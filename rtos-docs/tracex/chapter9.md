---
title: 'Capítulo 9: Eventos de seguimiento de USBX de Azure RTOS'
description: En este capítulo se incluye una descripción de los eventos de USBX de Azure RTOS que muestra TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 98561fe1d131e1d1b0893b7d89eb720881a82ac8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816286"
---
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a><span data-ttu-id="5ddac-103">Capítulo 9: Eventos de seguimiento de USBX de Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="5ddac-103">Chapter 9 - Azure RTOS USBX trace events</span></span>

<span data-ttu-id="5ddac-104">En este capítulo se incluye una descripción de los eventos de USBX de Azure RTOS que muestra TraceX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-104">This chapter contains a description of the Azure RTOS USBX events displayed by TraceX.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="5ddac-105">Lista de eventos e iconos</span><span class="sxs-lookup"><span data-stu-id="5ddac-105">List of Events and Icons</span></span>

<span data-ttu-id="5ddac-106">A continuación se incluye una lista de los eventos de USBX que muestra TraceX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-106">The following is a list of USBX events displayed by TraceX.</span></span>

| <span data-ttu-id="5ddac-107">Icono</span><span class="sxs-lookup"><span data-stu-id="5ddac-107">Icon</span></span>                             | <span data-ttu-id="5ddac-108">Significado</span><span class="sxs-lookup"><span data-stu-id="5ddac-108">Meaning</span></span>                               |
| -------------------------------- | ------------------------------------- |
| ![Icono de activación de clase C D C de dispositivo](./media/user-guide/usbx-events/image1.png)    | <span data-ttu-id="5ddac-110">**Activación de clase CDC de dispositivo** *(ux_device_class_cdc_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-110">**Device Class Cdc Activate** *(ux_device_class_cdc_activate)*</span></span> |
| ![Icono de desactivación de clase C D C de dispositivo](./media/user-guide/usbx-events/image2.png)    | <span data-ttu-id="5ddac-112">**Desactivación de clase CDC de dispositivo** *(ux_device_class_cdc_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-112">**Device Class Cdc Deactivate** *(ux_device_class_cdc_deactivate)*</span></span> |
| ![Icono de lectura de clase C D C de dispositivo](./media/user-guide/usbx-events/image3.png)    | <span data-ttu-id="5ddac-114">**Lectura de clase CDC de dispositivo** *(ux_device_class_cdc_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-114">**Device Class Cdc Read** *(ux_device_class_cdc_read)*</span></span> |
| ![Icono de escritura de clase C D C de dispositivo](./media/user-guide/usbx-events/image4.png)    | <span data-ttu-id="5ddac-116">**Escritura de clase CDC de dispositivo** *(ux_device_class_cdc_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-116">**Device Class Cdc Write** *(ux_device_class_cdc_write)*</span></span> |
| ![Icono de activación de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image5.png)    | <span data-ttu-id="5ddac-118">**Activación de clase DPUMP de dispositivo** *(ux_device_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-118">**Device Class Dpump Activate** *(ux_device_class_dpump_activate)*</span></span> |
| ![Icono de desactivación de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image6.png)    | <span data-ttu-id="5ddac-120">**Desactivación de clase DPUMP de dispositivo** *(ux_device_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-120">**Device Class Dpump Deactivate** *(ux_device_class_dpump_deactivate)*</span></span> |
| ![Icono de lectura de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image7.png)    | <span data-ttu-id="5ddac-122">**Lectura de clase DPUMP de dispositivo** *(ux_device_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-122">**Device Class Dpump Read** *(ux_device_class_dpump_read)*</span></span> |
| ![Icono de escritura de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image8.png)    | <span data-ttu-id="5ddac-124">**Escritura de clase DPUMP de dispositivo** *(ux_device_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-124">**Device Class Dpump Write** *(ux_device_class_dpump_write)*</span></span> |
| ![Icono de activación de clase H I D de dispositivo](./media/user-guide/usbx-events/image9.png)    | <span data-ttu-id="5ddac-126">**Activación de clase HID de dispositivo** *(ux_device_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-126">**Device Class Hid Activate** *(ux_device_class_hid_activate)*</span></span> |
| ![Icono de desactivación de clase H I D de dispositivo](./media/user-guide/usbx-events/image10.png)    | <span data-ttu-id="5ddac-128">**Desactivación de clase HID de dispositivo** *(ux_device_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-128">**Device Class Hid Deactivate** *(ux_device_class_hid_deactivate)*</span></span> |
| ![Icono de envío de descriptor de clase H I D de dispositivo](./media/user-guide/usbx-events/image11.png)    | <span data-ttu-id="5ddac-130">**Envío de descriptor de clase HID de dispositivo** *(ux_device_class_hid_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-130">**Device Class Hid Descriptor Send** *(ux_device_class_hid_descriptor_send)*</span></span> |
| ![Icono de obtención de evento de clase H I D de dispositivo](./media/user-guide/usbx-events/image12.png)    | <span data-ttu-id="5ddac-132">**Obtención de evento de clase HID de dispositivo** *(ux_device_class_hid_event_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-132">**Device Class Hid Event Get** *(ux_device_class_hid_event_get)*</span></span> |
| ![Icono de establecimiento de evento de clase H I D de dispositivo](./media/user-guide/usbx-events/image13.png)    | <span data-ttu-id="5ddac-134">**Establecimiento de evento de clase HID de dispositivo** *(ux_device_class_hid_event_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-134">**Device Class Hid Event Set** *(ux_device_class_hid_event_set)*</span></span> |
| ![Icono de obtención de informe de clase H I D de dispositivo](./media/user-guide/usbx-events/image14.png)    | <span data-ttu-id="5ddac-136">**Obtención de informe de clase HID de dispositivo** *(ux_device_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-136">**Device Class Hid Report Get** *(ux_device_class_hid_report_get)*</span></span> |
| ![Icono de establecimiento de informe de clase H I D de dispositivo](./media/user-guide/usbx-events/image15.png)    | <span data-ttu-id="5ddac-138">**Establecimiento de informe de clase HID de dispositivo** *(ux_device_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-138">**Device Class Hid Report Set** *(ux_device_class_hid_report_set)*</span></span> |
| ![Icono de activación de clase PIMA de dispositivo](./media/user-guide/usbx-events/image16.png)    | <span data-ttu-id="5ddac-140">**Activación de clase PIMA de dispositivo** *(ux_device_class_pima_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-140">**Device Class Pima Activate** *(ux_device_class_pima_activate)*</span></span> |
| ![Icono de desactivación de clase PIMA de dispositivo](./media/user-guide/usbx-events/image17.png)    | <span data-ttu-id="5ddac-142">**Desactivación de clase PIMA de dispositivo** *(ux_device_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-142">**Device Class Pima Deactivate** *(ux_device_class_pima_deactivate)*</span></span> |
| ![Icono de envío de información de dispositivo de clase PIMA de dispositivo](./media/user-guide/usbx-events/image18.png)    | <span data-ttu-id="5ddac-144">**Envío de información de dispositivo de clase PIMA de dispositivo** *(ux_device_class_pima_device_info_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-144">**Device Class Pima Device Info Send** *(ux_device_class_pima_device_info_send)*</span></span> |
| ![Icono de obtención de evento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image19.png)    | <span data-ttu-id="5ddac-146">**Obtención de evento de clase PIMA de dispositivo** *(ux_device_class_pima_event_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-146">**Device Class Pima Event Get** *(ux_device_class_pima_event_get)*</span></span> |
| ![Icono de establecimiento de evento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image20.png)    | <span data-ttu-id="5ddac-148">**Establecimiento de evento de clase PIMA de dispositivo** *(ux_device_class_pima_event_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-148">**Device Class Pima Event Set** *(ux_device_class_pima_event_set)*</span></span> |
| ![Icono de adición de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image21.png)    | <span data-ttu-id="5ddac-150">**Adición de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_add)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-150">**Device Class Pima Object Add** *(ux_device_class_pima_object_add)*</span></span> |
| ![Icono de obtención de datos de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image22.png)    | <span data-ttu-id="5ddac-152">**Obtención de datos de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-152">**Device Class Pima Object Data Get** *(ux_device_class_pima_object_data_get)*</span></span> |
| ![Icono de envío de datos de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image23.png)    | <span data-ttu-id="5ddac-154">**Envío de datos de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_data_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-154">**Device Class Pima Object Data Send** *(ux_device_class_pima_object_data_send)*</span></span> |
| ![Icono de eliminación de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image24.png)    | <span data-ttu-id="5ddac-156">**Eliminación de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-156">**Device Class Pima Object Delete** *(ux_device_class_pima_object_delete)*</span></span> |
| ![Icono de envío de identificadores de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image25.png)    | <span data-ttu-id="5ddac-158">**Envío de identificadores de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_handles_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-158">**Device Class Pima Object Handles Send** *(ux_device_class_pima_object_handles_send)*</span></span> |
| ![Icono de obtención de información de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image26.png)    | <span data-ttu-id="5ddac-160">**Obtención de información de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-160">**Device Class Pima Object Info Get** *(ux_device_class_pima_object_info_get)*</span></span> |
| ![Icono de envío de información de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image27.png)    | <span data-ttu-id="5ddac-162">**Envío de información de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-162">**Device Class Pima Object Info Send** *(ux_device_class_pima_object_info_send)*</span></span> |
| ![Icono de envío de número de objetos de clase PIMA de dispositivo](./media/user-guide/usbx-events/image28.png)    | <span data-ttu-id="5ddac-164">**Envío de número de objetos de clase PIMA de dispositivo** *(ux_device_class_pima_objects_number_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-164">**Device Class Pima Objects Number Send** *(ux_device_class_pima_objects_number_send)*</span></span> |
| ![Icono de obtención de datos parciales de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image29.png)    | <span data-ttu-id="5ddac-166">**Obtención de datos parciales de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_partial_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-166">**Device Class Pima Partial Object Data Get** *(ux_device_class_pima_partial_object_data_get)*</span></span> |
| ![Icono de envío de respuesta de clase PIMA de dispositivo](./media/user-guide/usbx-events/image30.png)    | <span data-ttu-id="5ddac-168">**Envío de respuesta de clase PIMA de dispositivo** *(ux_device_class_pima_response_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-168">**Device Class Pima Response Send** *(ux_device_class_pima_response_send)*</span></span>|
| ![Icono de envío de identificador de almacenamiento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image31.png)    | <span data-ttu-id="5ddac-170">**Envío de ID de almacenamiento de clase PIMA de dispositivo** *(ux_device_class_pima_storage_id_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-170">**Device Class Pima Storage Id Send** *(ux_device_class_pima_storage_id_send)*</span></span> |
| ![Icono de envío de información de almacenamiento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image32.png)    | <span data-ttu-id="5ddac-172">**Envío de información de almacenamiento de clase PIMA de dispositivo** *(ux_device_class_pima_storage_info_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-172">**Device Class Pima Storage Info Send** *(ux_device_class_pima_storage_info_send)*</span></span> |
| ![Icono de activación de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image33.png)    | <span data-ttu-id="5ddac-174">**Activación de clase RNDIS de dispositivo** *(ux_device_class_rndis_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-174">**Device Class Rndis Activate** *(ux_device_class_rndis_activate)*</span></span> |
| ![Icono de desactivación de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image34.png)    | <span data-ttu-id="5ddac-176">**Desactivación de clase RNDIS de dispositivo** *(ux_device_class_rndis_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-176">**Device Class Rndis Deactivate** *(ux_device_class_rndis_deactivate)*</span></span> |
| ![Icono de mantenimiento de conexión de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image35.png)    | <span data-ttu-id="5ddac-178">**Mantenimiento de conexión de mensaje de clase RNDIS de dispositivo** *(ux_device_class_rndis_msg_keep_alive)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-178">**Device Class Rndis Message Keep Alive** *(ux_device_class_rndis_msg_keep_alive)*</span></span> |
| ![Icono de consulta de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image36.png)    | <span data-ttu-id="5ddac-180">**Consulta de mensaje de clase RNDIS de dispositivo** *(ux_device_class_rndis_msg_query)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-180">**Device Class Rndis Message Query** *(ux_device_class_rndis_msg_query)*</span></span> |
| ![Icono de restablecimiento de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image37.png)    | <span data-ttu-id="5ddac-182">**Restablecimiento de mensaje de clase RNDIS de dispositivo** *(ux_device_class_rndis_msg_reset)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-182">**Device Class Rndis Message Reset** *(ux_device_class_rndis_msg_reset)*</span></span> |
| ![Icono de establecimiento de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image38.png)    | <span data-ttu-id="5ddac-184">**Establecimiento de mensaje de clase RNDIS de dispositivo** *(ux_device_class_rndis_msg_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-184">**Device Class Rndis Message Set** *(ux_device_class_rndis_msg_set)*</span></span> |
| ![Icono de recepción de paquete de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image39.png)    | <span data-ttu-id="5ddac-186">**Recepción de paquetes de clase RNDIS de dispositivo** *(ux_device_class_rndis_packet_receive)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-186">**Device Class Rndis Packet Receive** *(ux_device_class_rndis_packet_receive)*</span></span> |
| ![Icono de transmisión de paquete de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image40.png)    | <span data-ttu-id="5ddac-188">**Transmisión de paquetes de clase RNDIS de dispositivo** *(ux_device_class_rndis_packet_transmit)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-188">**Device Class Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)*</span></span> |
| ![Icono de activación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image41.png)    | <span data-ttu-id="5ddac-190">**Activación de clase STORAGE de dispositivo** *(ux_device_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-190">**Device Class Storage Activate** *(ux_device_class_storage_activate)*</span></span> |
| ![Icono de desactivación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image42.png)    | <span data-ttu-id="5ddac-192">**Desactivación de clase STORAGE de dispositivo** *(ux_device_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-192">**Device Class Storage Deactivate** *(ux_device_class_storage_deactivate)*</span></span> |
| ![Icono de formato de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image43.png)    | <span data-ttu-id="5ddac-194">**Formato de clase STORAGE de dispositivo** *(ux_device_class_storage_format)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-194">**Device Class Storage Format** *(ux_device_class_storage_format)*</span></span> |
| ![Icono de consulta de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image44.png)    | <span data-ttu-id="5ddac-196">**Consulta de clase STORAGE de dispositivo** *(ux_device_class_storage_inquiry)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-196">**Device Class Storage Inquiry** *(ux_device_class_storage_inquiry)*</span></span> |
| ![Icono de selección de modo de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image45.png)    | <span data-ttu-id="5ddac-198">**Selección de modo de clase STORAGE de dispositivo** *(ux_device_class_storage_mode_select)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-198">**Device Class Storage Mode Select** *(ux_device_class_storage_mode_select)*</span></span> |
| ![Icono de detección de modo de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image46.png)    | <span data-ttu-id="5ddac-200">**Detección de modo de clase STORAGE de dispositivo** *(ux_device_class_storage_mode_sense)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-200">**Device Class Storage Mode Sense** *(ux_device_class_storage_mode_sense)*</span></span> |
| ![Icono de impedir/permitir extracción de soporte físico de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image47.png)    | <span data-ttu-id="5ddac-202">**Impedir/permitir extracción de soporte físico de clase STORAGE de dispositivo** *(ux_device_class_storage_prevent_allow_media_removal)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-202">**Device Class Storage Prevent Allow Media Removal** *(ux_device_class_storage_prevent_allow_media_removal)*</span></span> |
| ![Icono de lectura de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image48.png)    | <span data-ttu-id="5ddac-204">**Lectura de clase STORAGE de dispositivo** *(ux_device_class_storage_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-204">**Device Class Storage Read** *(ux_device_class_storage_read)*</span></span> |
| ![Icono de lectura de capacidad de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image49.png)    | <span data-ttu-id="5ddac-206">**Lectura de capacidad de clase STORAGE de dispositivo** *(ux_device_class_storage_read_capacity)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-206">**Device Class Storage Read Capacity** *(ux_device_class_storage_read_capacity)*</span></span> |
| ![Icono de lectura de capacidad de formato de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image50.png)    | <span data-ttu-id="5ddac-208">**Lectura de capacidad de formato de clase STORAGE de dispositivo** *(ux_device_class_storage_read_format_capacity)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-208">**Device Class Storage Read Format Capacity** *(ux_device_class_storage_read_format_capacity)*</span></span> |
| ![Icono de lectura de tabla de contenido de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image51.png)    | <span data-ttu-id="5ddac-210">**Lectura de tabla de contenido de clase STORAGE de dispositivo** *(ux_device_class_storage_read_toc)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-210">**Device Class Storage Read TOC** *(ux_device_class_storage_read_toc)*</span></span> |
| ![Icono de detección de solicitud de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image52.png)    | <span data-ttu-id="5ddac-212">**Detección de solicitud de clase STORAGE de dispositivo** *(ux_device_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-212">**Device Class Storage Request Sense** *(ux_device_class_storage_request_sense)*</span></span> |
| ![Icono de inicio/parada de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image53.png)    | <span data-ttu-id="5ddac-214">**Inicio/parada de clase STORAGE de dispositivo** *(ux_device_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-214">**Device Class Storage Start Stop** *(ux_device_class_storage_start_stop)*</span></span> |
| ![Icono de prueba de unidad preparada de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image54.png)    | <span data-ttu-id="5ddac-216">**Prueba de unidad preparada de clase STORAGE de dispositivo** *(ux_device_class_storage_test_ready)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-216">**Device Class Storage Test Ready** *(ux_device_class_storage_test_ready)*</span></span> |
| ![Icono de comprobación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image55.png)    | <span data-ttu-id="5ddac-218">**Comprobación de clase STORAGE de dispositivo** *(ux_device_class_storage_verify)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-218">**Device Class Storage Verify** *(ux_device_class_storage_verify)*</span></span> |
| ![Icono de escritura de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image56.png)    | <span data-ttu-id="5ddac-220">**Escritura de clase STORAGE de dispositivo** *(ux_device_class_storage_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-220">**Device Class Storage Write** *(ux_device_class_storage_write)*</span></span> |
| ![Icono de obtención de configuración alternativa de pila de dispositivos](./media/user-guide/usbx-events/image57.png)    | <span data-ttu-id="5ddac-222">**Obtención de configuración alternativa de pila de dispositivos** *(ux_device_stack_alternate_setting_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-222">**Device Stack Alternate Setting Get** *(ux_device_stack_alternate_setting_get)*</span></span> |
| ![Icono de establecimiento de configuración alternativa de pila de dispositivos](./media/user-guide/usbx-events/image58.png)    | <span data-ttu-id="5ddac-224">**Establecimiento de configuración alternativa de pila de dispositivos** *(ux_device_stack_alternate_setting_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-224">**Device Stack Alternate Setting Set** *(ux_device_stack_alternate_setting_set)*</span></span> |
| ![Icono de registro de clase de pila de dispositivos](./media/user-guide/usbx-events/image59.png)    | <span data-ttu-id="5ddac-226">**Registro de clase de pila de dispositivos** *(ux_device_stack_class_register)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-226">**Device Stack Class Register** *(ux_device_stack_class_register)*</span></span> |
| ![Icono de borrado de característica de pila de dispositivos](./media/user-guide/usbx-events/image60.png)    | <span data-ttu-id="5ddac-228">**Borrado de característica de pila de dispositivos** *(ux_device_stack_clear_feature)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-228">**Device Stack Clear Feature** *(ux_device_stack_clear_feature)*</span></span> |
| ![Icono de obtención de configuración de pila de dispositivos](./media/user-guide/usbx-events/image61.png)    | <span data-ttu-id="5ddac-230">**Obtención de configuración de pila de dispositivos** *(ux_device_stack_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-230">**Device Stack Configuration Get** *(ux_device_stack_configuration_get)*</span></span> |
| ![Icono de establecimiento de configuración de pila de dispositivos](./media/user-guide/usbx-events/image62.png)    | <span data-ttu-id="5ddac-232">**Establecimiento de configuración de pila de dispositivos** *(ux_device_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-232">**Device Stack Configuration Set** *(ux_device_stack_configuration_set)*</span></span> |
| ![Icono de conexión de pila de dispositivos](./media/user-guide/usbx-events/image63.png)    | <span data-ttu-id="5ddac-234">**Conexión de pila de dispositivos** *(ux_device_stack_connect)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-234">**Device Stack Connect** *(ux_device_stack_connect)*</span></span> |
| ![Icono de envío de descriptor de pila de dispositivos](./media/user-guide/usbx-events/image64.png)    | <span data-ttu-id="5ddac-236">**Envío de descriptor de pila de dispositivos** *(ux_device_stack_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-236">**Device Stack Descriptor Send** *(ux_device_stack_descriptor_send)*</span></span> |
| ![Icono de desconexión de pila de dispositivos](./media/user-guide/usbx-events/image65.png)    | <span data-ttu-id="5ddac-238">**Desconexión de pila de dispositivos** *(ux_device_stack_disconnect)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-238">**Device Stack Disconnect** *(ux_device_stack_disconnect)*</span></span> |
| ![Icono de detención de punto de conexión de pila de dispositivos](./media/user-guide/usbx-events/image66.png)    | <span data-ttu-id="5ddac-240">**Detención de punto de conexión de pila de dispositivo** *(ux_device_stack_endpoint_stall)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-240">**Device Stack Endpoint Stall** *(ux_device_stack_endpoint_stall)*</span></span> |
| ![Icono de obtención de estado de pila de dispositivos](./media/user-guide/usbx-events/image67.png)    | <span data-ttu-id="5ddac-242">**Obtención de estado de pila de dispositivos** *(ux_device_stack_get_status)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-242">**Device Stack Get Status** *(ux_device_stack_get_status)*</span></span> |
| ![Icono de reactivación de host de pila de dispositivos](./media/user-guide/usbx-events/image68.png)    | <span data-ttu-id="5ddac-244">**Reactivación de host de pila de dispositivos** *(ux_device_stack_host_wakeup)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-244">**Device Stack Host Wakeup** *(ux_device_stack_host_wakeup)*</span></span> |
| ![Icono de inicialización de pila de dispositivos](./media/user-guide/usbx-events/image69.png)    | <span data-ttu-id="5ddac-246">**Inicialización de pila de dispositivos** *(ux_device_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-246">**Device Stack Initialize** *(ux_device_stack_initialize)*</span></span> |
| ![Icono de eliminación de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image70.png)    | <span data-ttu-id="5ddac-248">**Eliminación de interfaz de pila de dispositivos** *(ux_device_stack_interface_delete)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-248">**Device Stack Interface Delete** *(ux_device_stack_interface_delete)*</span></span> |
| ![Icono de obtención de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image71.png)    | <span data-ttu-id="5ddac-250">**Obtención de interfaz de pila de dispositivos** *(ux_device_stack_interface_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-250">**Device Stack Interface Get** *(ux_device_stack_interface_get)*</span></span> |
| ![Icono de establecimiento de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image72.png)    | <span data-ttu-id="5ddac-252">**Establecimiento de interfaz de pila de dispositivos** *(ux_device_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-252">**Device Stack Interface Set** *(ux_device_stack_interface_set)*</span></span> |
| ![Icono de establecimiento de característica de pila de dispositivos](./media/user-guide/usbx-events/image73.png)    | <span data-ttu-id="5ddac-254">**Establecimiento de característica de pila de dispositivos** *(ux_device_stack_set_feature)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-254">**Device Stack Set Feature** *(ux_device_stack_set_feature)*</span></span> |
| ![Icono de anulación de transferencia de pila de dispositivos](./media/user-guide/usbx-events/image74.png)    | <span data-ttu-id="5ddac-256">**Anulación de transferencia de pila de dispositivos** *(ux_device_stack_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-256">**Device Stack Transfer Abort** *(ux_device_stack_transfer_abort)*</span></span> |
| ![\*Icono de anulación de todas las solicitudes de transferencia de la pila de dispositivos](./media/user-guide/usbx-events/image75.png)    | <span data-ttu-id="5ddac-258">**Anulación de todas las solicitudes de transferencia de la pila de dispositivos** *(ux_device_stack_transfer_all_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-258">**Device Stack Transfer All Request Abort** *(ux_device_stack_transfer_all_request_abort)*</span></span> |
| ![Icono de solicitud de transferencia de pila de dispositivos](./media/user-guide/usbx-events/image76.png)    | <span data-ttu-id="5ddac-260">**Solicitud de transferencia de pila de dispositivos** *(ux_device_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-260">**Device Stack Transfer Request** *(ux_device_stack_transfer_request)*</span></span> |
| ![Icono de activación de clase ASIX de host](./media/user-guide/usbx-events/image77.png)    | <span data-ttu-id="5ddac-262">**Activación de clase ASIX de host** *(ux_host_class_asix_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-262">**Host Class Asix Activate** *(ux_host_class_asix_activate)*</span></span> |
| ![Icono de desactivación de clase ASIX de host](./media/user-guide/usbx-events/image78.png)    | <span data-ttu-id="5ddac-264">**Desactivación de clase ASIX de host** *(ux_host_class_asix_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-264">**Host Class Asix Deactivate** *(ux_host_class_asix_deactivate)*</span></span> |
| ![Icono de notificación de interrupción de clase ASIX de host](./media/user-guide/usbx-events/image79.png)    | <span data-ttu-id="5ddac-266">**Notificación de interrupción de clase ASIX de host** *(ux_host_class_asix_interrupt_notification)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-266">**Host Class Asix Interrupt Notification** *(ux_host_class_asix_interrupt_notification)*</span></span> |
| ![Icono de lectura de clase ASIX de host](./media/user-guide/usbx-events/image80.png)    | <span data-ttu-id="5ddac-268">**Lectura de clase ASIX de host** *(ux_host_class_asix_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-268">**Host Class Asix Read** *(ux_host_class_asix_read)*</span></span> |
| ![Icono de escritura de clase ASIX de host](./media/user-guide/usbx-events/image81.png)    | <span data-ttu-id="5ddac-270">**Escritura de clase ASIX de host** *(ux_host_class_asix_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-270">**Host Class Asix Write** *(ux_host_class_asix_write)*</span></span> |
| ![Icono de activación de clase AUDIO de host](./media/user-guide/usbx-events/image82.png)    | <span data-ttu-id="5ddac-272">**Activación de clase AUDIO de host** *(ux_host_class_audio_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-272">**Host Class Audio Activate** *(ux_host_class_audio_activate)*</span></span> |
| ![Icono de obtención de valor de control de clase AUDIO de host](./media/user-guide/usbx-events/image83.png)    | <span data-ttu-id="5ddac-274">**Obtención de valor de control de clase AUDIO de host** *(ux_host_class_audio_control_value_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-274">**Host Class Audio Control Value Get** *(ux_host_class_audio_control_value_get)*</span></span> |
| ![Icono de establecimiento de valor de control de clase AUDIO de host](./media/user-guide/usbx-events/image84.png)    | <span data-ttu-id="5ddac-276">**Establecimiento de valor de control de clase AUDIO de host** *(ux_host_class_audio_control_value_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-276">**Host Class Audio Control Value Set** *(ux_host_class_audio_control_value_set)*</span></span> |
| ![Icono de desactivación de clase AUDIO de host](./media/user-guide/usbx-events/image85.png)    | <span data-ttu-id="5ddac-278">**Desactivación de clase AUDIO de host** *(ux_host_class_audio_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-278">**Host Class Audio Deactivate** *(ux_host_class_audio_deactivate)*</span></span> |
| ![Icono de lectura de clase AUDIO de host](./media/user-guide/usbx-events/image86.png)    | <span data-ttu-id="5ddac-280">**Lectura de clase AUDIO de host** *(ux_host_class_audio_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-280">**Host Class Audio Read** *(ux_host_class_audio_read)*</span></span> |
| ![Icono de obtención de muestreo de streaming de clase AUDIO de host](./media/user-guide/usbx-events/image87.png)    | <span data-ttu-id="5ddac-282">**Obtención de muestreo de streaming de clase AUDIO de host** *(ux_host_class_audio_streaming_sampling_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-282">**Host Class Audio Streaming Sampling Get** *(ux_host_class_audio_streaming_sampling_get)*</span></span> |
| ![Icono de establecimiento de muestreo de streaming de clase AUDIO de host](./media/user-guide/usbx-events/image88.png)    | <span data-ttu-id="5ddac-284">**Establecimiento de muestreo de streaming de clase AUDIO de host** *(ux_host_class_audio_streaming_sampling_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-284">**Host Class Audio Streaming Sampling Set** *(ux_host_class_audio_streaming_sampling_set)*</span></span> |
| ![Icono de escritura de clase AUDIO de host](./media/user-guide/usbx-events/image89.png)    | <span data-ttu-id="5ddac-286">**Escritura de clase AUDIO de host** *(ux_host_class_audio_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-286">**Host Class Audio Write** *(ux_host_class_audio_write)*</span></span> |
| ![Icono de activación de clase C D C A C M de host](./media/user-guide/usbx-events/image90.png)    | <span data-ttu-id="5ddac-288">**Activación de clase CDC ACM de host** *(ux_host_class_cdc_acm_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-288">**Host Class Cdc Acm Activate** *(ux_host_class_cdc_acm_activate)*</span></span> |
| ![Icono de desactivación de clase C D C A C M de host](./media/user-guide/usbx-events/image91.png)    | <span data-ttu-id="5ddac-290">**Desactivación de clase CDC ACM de host** *(ux_host_class_cdc_acm_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-290">**Host Class Cdc Acm Deactivate** *(ux_host_class_cdc_acm_deactivate)*</span></span> |
| ![Icono de función I O C T L de canalización de entrada de clase C D C A C M de host](./media/user-guide/usbx-events/image92.png)    | <span data-ttu-id="5ddac-292">**Función IOCTL de anulación de canalización de entrada de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-292">**Host Class Cdc Acm Ioctl Abort In Pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span></span> |
| ![Icono de función I O C T L de anulación de canalización de salida de clase C D C A C M de host](./media/user-guide/usbx-events/image93.png)    | <span data-ttu-id="5ddac-294">**Función IOCTL de anulación de canalización de salida de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-294">**Host Class Cdc Acm Ioctl Abort Out Pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span></span> |
| ![Icono de función I O C T L de obtención de estado de dispositivo de clase C D C A C M de host](./media/user-guide/usbx-events/image94.png)    | <span data-ttu-id="5ddac-296">**Función IOCTL de obtención de estado de dispositivo de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-296">**Host Class Cdc Acm Ioctl Get Device Status** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span></span> |
| ![Icono de función I O C T L de obtención de codificación de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image95.png)    | <span data-ttu-id="5ddac-298">**Función IOCTL de obtención de codificación de línea de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-298">**Host Class Cdc Acm Ioctl Get Line Coding** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span></span> |
| ![Icono de función I O C T L de devolución de llamada de notificación de clase C D C A C M de host](./media/user-guide/usbx-events/image96.png)    | <span data-ttu-id="5ddac-300">**Función IOCTL de devolución de llamada de notificación de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-300">**Host Class Cdc Acm Ioctl Notification Callback** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span></span> |
| ![Icono de función I O C T L de interrupción de envío de clase C D C A C M de host](./media/user-guide/usbx-events/image97.png)    | <span data-ttu-id="5ddac-302">**Función IOCTL de interrupción de envío de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-302">**Host Class Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)*</span></span> |
| ![Icono de función I O C T L de establecimiento de codificación de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image98.png)    | <span data-ttu-id="5ddac-304">**Función IOCTL de establecimiento de codificación de línea de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-304">**Host Class Cdc Acm Ioctl Set Line Coding** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span></span> |
| ![Icono de función I O C T L de establecimiento de estado de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image99.png)    | <span data-ttu-id="5ddac-306">**Función IOCTL de establecimiento de estado de línea de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-306">**Host Class Cdc Acm Ioctl Set Line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span></span> |
| ![Icono de lectura de clase C D C A C M de host](./media/user-guide/usbx-events/image100.png)    | <span data-ttu-id="5ddac-308">**Lectura de clase C D C A C M de host** *(ux_host_class_cdc_acm_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-308">**Host Class Cdc Acm Read** *(ux_host_class_cdc_acm_read)*</span></span> |
| ![Icono de inicio de recepción de clase C D C A C M de host](./media/user-guide/usbx-events/image101.png)    | <span data-ttu-id="5ddac-310">**Inicio de recepción de clase C D C A C M de host** *(ux_host_class_cdc_acm_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-310">**Host Class Cdc Acm Reception Start** *(ux_host_class_cdc_acm_reception_start)*</span></span> |
| ![Icono de parada de recepción de clase C D C A C M de host](./media/user-guide/usbx-events/image102.png)    | <span data-ttu-id="5ddac-312">**Parada de recepción de clase C D C A C M de host** *(ux_host_class_cdc_acm_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-312">**Host Class Cdc Acm Reception Stop** *(ux_host_class_cdc_acm_reception_stop)*</span></span> |
| ![Icono de escritura de clase C D C A C M de host](./media/user-guide/usbx-events/image103.png)    | <span data-ttu-id="5ddac-314">**Escritura de clase C D C A C M de host** *(ux_host_class_cdc_acm_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-314">**Host Class Cdc Acm Write** *(ux_host_class_cdc_acm_write)*</span></span> |
| ![Icono de activación de clase DPUMP de host](./media/user-guide/usbx-events/image104.png)    | <span data-ttu-id="5ddac-316">**Activación de clase DPUMP de host** *(ux_host_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-316">**Host Class Dpump Activate** *(ux_host_class_dpump_activate)*</span></span> |
| ![Icono de desactivación de clase DPUMP de host](./media/user-guide/usbx-events/image105.png)    | <span data-ttu-id="5ddac-318">**Desactivación de clase DPUMP de host** *(ux_host_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-318">**Host Class Dpump Deactivate** *(ux_host_class_dpump_deactivate)*</span></span> |
| ![Icono de lectura de clase DPUMP de host](./media/user-guide/usbx-events/image106.png)    | <span data-ttu-id="5ddac-320">**Lectura de clase DPUMP de host** *(ux_host_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-320">**Host Class Dpump Read** *(ux_host_class_dpump_read)*</span></span> |
| ![Icono de escritura de clase DPUMP de host](./media/user-guide/usbx-events/image107.png)    | <span data-ttu-id="5ddac-322">**Escritura de clase DPUMP de host** *(ux_host_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-322">**Host Class Dpump Write** *(ux_host_class_dpump_write)*</span></span> |
| ![Icono de activación de clase HID de host](./media/user-guide/usbx-events/image108.png)    | <span data-ttu-id="5ddac-324">**Activación de clase HID de host** *(ux_host_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-324">**Host Class Hid Activate** *(ux_host_class_hid_activate)*</span></span> |
| ![Icono de registro de cliente de clase HID de host](./media/user-guide/usbx-events/image109.png)    | <span data-ttu-id="5ddac-326">**Registro de cliente de clase HID de host** *(ux_host_class_hid_client_register)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-326">**Host Class Hid Client Register** *(ux_host_class_hid_client_register)*</span></span> |
| ![Icono de desactivación de clase HID de host](./media/user-guide/usbx-events/image110.png)    | <span data-ttu-id="5ddac-328">**Desactivación de clase HID de host** *(ux_host_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-328">**Host Class Hid Deactivate** *(ux_host_class_hid_deactivate)*</span></span> |
| ![Icono de obtención de inactividad de clase HID de host](./media/user-guide/usbx-events/image111.png)    | <span data-ttu-id="5ddac-330">**Obtención de inactividad de clase HID de host** *(ux_host_class_hid_idle_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-330">**Host Class Hid Idle Get** *(ux_host_class_hid_idle_get)*</span></span> |
| ![Icono de establecimiento de inactividad de clase HID de host](./media/user-guide/usbx-events/image112.png)    | <span data-ttu-id="5ddac-332">**Establecimiento de inactividad de clase HID de host** *(ux_host_class_hid_idle_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-332">**Host Class Hid Idle Set** *(ux_host_class_hid_idle_set)*</span></span> |
| ![Icono de activación de teclado de clase HID de host](./media/user-guide/usbx-events/image113.png)    | <span data-ttu-id="5ddac-334">**Activación de teclado de clase HID de host** *(ux_host_class_hid_keyboard_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-334">**Host Class Hid Keyboard Activate** *(ux_host_class_hid_keyboard_activate)*</span></span> |
| ![Icono de desactivación de teclado de clase HID de host](./media/user-guide/usbx-events/image114.png)    | <span data-ttu-id="5ddac-336">**Desactivación de teclado de clase HID de host** *(ux_host_class_hid_keyboard_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-336">**Host Class Hid Keyboard Deactivate** *(ux_host_class_hid_keyboard_deactivate)*</span></span> |
| ![Icono de activación de mouse de clase HID de host](./media/user-guide/usbx-events/image115.png)    | <span data-ttu-id="5ddac-338">**Activación de mouse de clase HID de host** *(ux_host_class_hid_mouse_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-338">**Host Class Hid Mouse Activate** *(ux_host_class_hid_mouse_activate)*</span></span> |
| ![Icono de desactivación de mouse de clase HID de host](./media/user-guide/usbx-events/image116.png)    | <span data-ttu-id="5ddac-340">**Desactivación de mouse de clase HID de host** *(ux_host_class_hid_mouse_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-340">**Host Class Hid Mouse Deactivate** *(ux_host_class_hid_mouse_deactivate)*</span></span> |
| ![Icono de activación de control remoto de clase HID de host](./media/user-guide/usbx-events/image117.png)    | <span data-ttu-id="5ddac-342">**Activación de control remoto de clase HID de host** *(ux_host_class_hid_remote_control_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-342">**Host Class Hid Remote Control Activate** *(ux_host_class_hid_remote_control_activate)*</span></span> |
| ![Icono de desactivación de control remoto de clase HID de host](./media/user-guide/usbx-events/image118.png)    | <span data-ttu-id="5ddac-344">**Desactivación de control remoto de clase HID de host** *(ux_host_class_hid_remote_control_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-344">**Host Class Hid Remote Control Deactivate** *(ux_host_class_hid_remote_control_deactivate)*</span></span> |
| ![Icono de obtención de informe de clase HID de host](./media/user-guide/usbx-events/image119.png)    | <span data-ttu-id="5ddac-346">**Obtención de informe de clase HID de host** *(ux_host_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-346">**Host Class Hid Report Get** *(ux_host_class_hid_report_get)*</span></span> |
| ![Icono de establecimiento de informe de clase HID de host](./media/user-guide/usbx-events/image120.png)    | <span data-ttu-id="5ddac-348">**Establecimiento de informe de clase HID de host** *(ux_host_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-348">**Host Class Hid Report Set** *(ux_host_class_hid_report_set)*</span></span> |
| ![Icono de activación de clase HUB de host](./media/user-guide/usbx-events/image121.png)    | <span data-ttu-id="5ddac-350">**Activación de clase HUB de host** *(ux_host_class_hub_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-350">**Host Class Hub Activate** *(ux_host_class_hub_activate)*</span></span> |
| ![Icono de detección de cambio de clase HUB de host](./media/user-guide/usbx-events/image122.png)    | <span data-ttu-id="5ddac-352">**Detección de cambio de clase HUB de host** *(ux_host_class_hub_change_detect)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-352">**Host Class Hub Change Detect** *(ux_host_class_hub_change_detect)*</span></span> |
| ![\*Icono de desactivación de clase HUB de host](./media/user-guide/usbx-events/image123.png)    | <span data-ttu-id="5ddac-354">**Desactivación de clase HUB de host** *(ux_host_class_hub_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-354">**Host Class Hub Deactivate** *(ux_host_class_hub_deactivate)*</span></span> |
| ![Icono de proceso de cambio de puerto de conexión de clase HUB de host](./media/user-guide/usbx-events/image124.png)    | <span data-ttu-id="5ddac-356">**Proceso de cambio de puerto de conexión de clase HUB de host** *(ux_host_class_hub_port_change_connection_process)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-356">**Host Class Hub Port Change Connection Process** *(ux_host_class_hub_port_change_connection_process)*</span></span> |
| ![Icono de habilitación de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image125.png)    | <span data-ttu-id="5ddac-358">**Habilitación de proceso de cambio de puerto de clase HUB de host** *(ux_host_class_hub_port_change_enable_process)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-358">**Host Class Hub Port Change Enable Process** *(ux_host_class_hub_port_change_enable_process)*</span></span> |
| ![Icono de proceso actual finalizado de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image126.png)    | <span data-ttu-id="5ddac-360">**Proceso actual finalizado de cambio de puerto de clase HUB de host** *(ux_host_class_hub_port_change_over_current_process)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-360">**Host Class Hub Port Change Over Current Process** *(ux_host_class_hub_port_change_over_current_process)*</span></span> |
| ![Icono de restablecimiento de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image127.png)    | <span data-ttu-id="5ddac-362">**Restablecimiento de proceso de cambio de puerto de clase HUB de host** *(ux_host_class_hub_port_change_reset_process)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-362">**Host Class Hub Port Change Reset Process** *(ux_host_class_hub_port_change_reset_process)*</span></span> |
| ![Icono de suspensión de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image128.png)    | <span data-ttu-id="5ddac-364">**Suspensión de proceso de cambio de puerto de clase HUB de host** *(ux_host_class_hub_port_change_suspend_process)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-364">**Host Class Hub Port Change Suspend Process** *(ux_host_class_hub_port_change_suspend_process)*</span></span> |
| ![Icono de activación de clase PIMA de host](./media/user-guide/usbx-events/image129.png)    | <span data-ttu-id="5ddac-366">**Activación de clase PIMA de host** *(ux_host_class_prima_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-366">**Host Class Pima Activate** *(ux_host_class_prima_activate)*</span></span> |
| ![Icono de desactivación de clase PIMA de host](./media/user-guide/usbx-events/image130.png)    | <span data-ttu-id="5ddac-368">**Desactivación de clase PIMA de host** *(ux_host_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-368">**Host Class Pima Deactivate** *(ux_host_class_pima_deactivate)*</span></span> |
| ![Icono de obtención de información de dispositivo de clase PIMA de host](./media/user-guide/usbx-events/image131.png)    | <span data-ttu-id="5ddac-370">**Obtención de información de dispositivo de clase PIMA de host** *(ux_host_class_pima_device_info_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-370">**Host Class Pima Device Info Get** *(ux_host_class_pima_device_info_get)*</span></span> |
| ![Icono de restablecimiento de dispositivo de clase PIMA de host](./media/user-guide/usbx-events/image132.png)    | <span data-ttu-id="5ddac-372">**Restablecimiento de dispositivo de clase PIMA de host** *(ux_host_class_pima_device_reset)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-372">**Host Class Pima Device Reset** *(ux_host_class_pima_device_reset)*</span></span> |
| ![Icono de notificación de clase PIMA de host](./media/user-guide/usbx-events/image133.png)    | <span data-ttu-id="5ddac-374">**Notificación de clase PIMA de host** *(ux_host_class_pima_notification)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-374">**Host Class Pima Notification** *(ux_host_class_pima_notification)*</span></span> |
| ![Icono de obtención de objetos de clase PIMA de host](./media/user-guide/usbx-events/image134.png)    | <span data-ttu-id="5ddac-376">**Obtención de número de objetos de clase PIMA de host** *(ux_host_class_pima_num_objects_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-376">**Host Class Pima Number Objects Get** *(ux_host_class_pima_num_objects_get)*</span></span> |
| ![Icono de cierre de objeto de clase PIMA de host](./media/user-guide/usbx-events/image135.png)    | <span data-ttu-id="5ddac-378">**Cierre de objeto de clase PIMA de host** *(ux_host_class_pima_object_close)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-378">**Host Class Pima Object Close** *(ux_host_class_pima_object_close)*</span></span> |
| ![Icono de copia de objeto de clase PIMA de host](./media/user-guide/usbx-events/image136.png)    | <span data-ttu-id="5ddac-380">**Copia de objeto de clase PIMA de host** *(ux_host_class_pima_object_copy)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-380">**Host Class Pima Object Copy** *(ux_host_class_pima_object_copy)*</span></span> |
| ![Icono de eliminación de objeto de clase PIMA de host](./media/user-guide/usbx-events/image137.png)    | <span data-ttu-id="5ddac-382">**Eliminación de objeto de clase PIMA de host** *(ux_host_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-382">**Host Class Pima Object Delete** *(ux_host_class_pima_object_delete)*</span></span> |
| ![Icono de obtención de objeto de clase PIMA de host](./media/user-guide/usbx-events/image138.png)    | <span data-ttu-id="5ddac-384">**Obtención de objeto de clase PIMA de host** *(ux_host_class_pima_object_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-384">**Host Class Pima Object Get** *(ux_host_class_pima_object_get)*</span></span> |
| ![Icono de obtención de información de objeto de clase PIMA de host](./media/user-guide/usbx-events/image139.png)    | <span data-ttu-id="5ddac-386">**Obtención de información de objeto de clase PIMA de host** *(ux_host_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-386">**Host Class Pima Object Info Get** *(ux_host_class_pima_object_info_get)*</span></span> |
| ![Icono de envío de información de objeto de clase PIMA de host](./media/user-guide/usbx-events/image140.png)    | <span data-ttu-id="5ddac-388">**Envío de información de objeto de clase PIMA de host** *(ux_host_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-388">**Host Class Pima Object Info Send** *(ux_host_class_pima_object_info_send)*</span></span> |
| ![Icono de movimiento de objeto de clase PIMA de host](./media/user-guide/usbx-events/image141.png)    | <span data-ttu-id="5ddac-390">**Movimiento de objeto de clase PIMA de host** *(ux_host_class_pima_object_move)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-390">**Host Class Pima Object Move** *(ux_host_class_pima_object_move)*</span></span> |
| ![Icono de envío de objeto de clase PIMA de host](./media/user-guide/usbx-events/image142.png)    | <span data-ttu-id="5ddac-392">**Envío de objeto de clase PIMA de host** *(ux_host_class_pima_object_send)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-392">**Host Class Pima Object Send** *(ux_host_class_pima_object_send)*</span></span> |
| ![Icono de anulación de transferencia de objeto de clase PIMA de host](./media/user-guide/usbx-events/image143.png)    | <span data-ttu-id="5ddac-394">**Anulación de transferencia de objeto de clase PIMA de host** *(ux_host_class_object_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-394">**Host Class Pima Object Transfer Abort** *(ux_host_class_object_transfer_abort)*</span></span> |
| ![Icono de lectura de clase PIMA de host](./media/user-guide/usbx-events/image144.png)    | <span data-ttu-id="5ddac-396">**Lectura de clase PIMA de host** *(ux_host_class_pima_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-396">**Host Class Pima Read** *(ux_host_class_pima_read)*</span></span> |
| ![Icono de cancelación de solicitud de clase PIMA de host](./media/user-guide/usbx-events/image145.png)    | <span data-ttu-id="5ddac-398">**Cancelación de solicitud de clase PIMA de host** *(ux_host_class_pima_request_cancel)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-398">**Host Class Pima Request Cancel** *(ux_host_class_pima_request_cancel)*</span></span> |
| ![Icono de cierre de sesión de clase PIMA de host](./media/user-guide/usbx-events/image146.png)    | <span data-ttu-id="5ddac-400">**Cierre de sesión de clase PIMA de host** *(ux_host_class_pima_session_close)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-400">**Host Class Pima Session Close** *(ux_host_class_pima_session_close)*</span></span> |
| ![Icono de apertura de sesión de clase PIMA de host](./media/user-guide/usbx-events/image147.png)    | <span data-ttu-id="5ddac-402">**Apertura de sesión de clase PIMA de host** *(ux_host_class_pima_session_open)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-402">**Host Class Pima Session Open** *(ux_host_class_pima_session_open)*</span></span> |
| ![Icono de obtención de identificadores de almacenamiento de clase PIMA de host](./media/user-guide/usbx-events/image148.png)    | <span data-ttu-id="5ddac-404">**Obtención de identificadores de almacenamiento de clase PIMA de host** *(ux_host_class_pima_storage_ids_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-404">**Host Class Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)*</span></span> |
| ![Icono de obtención de información de almacenamiento de clase PIMA de host](./media/user-guide/usbx-events/image149.png)    | <span data-ttu-id="5ddac-406">**Obtención de información de almacenamiento de clase PIMA de host** *(ux_host_class_pima_storage_info_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-406">**Host Class Pima Storage Info Get** *(ux_host_class_pima_storage_info_get)*</span></span> |
| ![Icono de obtención de miniatura de clase PIMA de host](./media/user-guide/usbx-events/image150.png)    | <span data-ttu-id="5ddac-408">**Obtención de miniatura de clase PIMA de host** *(ux_host_class_pima_thumb_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-408">**Host Class Pima Thumb Get** *(ux_host_class_pima_thumb_get)*</span></span> |
| ![Icono de escritura de clase PIMA de host](./media/user-guide/usbx-events/image151.png)    | <span data-ttu-id="5ddac-410">**Escritura de clase PIMA de host** *(ux_host_class_pima_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-410">**Host Class Pima Write** *(ux_host_class_pima_write)*</span></span> |
| ![Icono de activación de clase PRINTER de host](./media/user-guide/usbx-events/image152.png)    | <span data-ttu-id="5ddac-412">**Activación de clase PRINTER de host** *(ux_host_class_printer_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-412">**Host Class Printer Activate** *(ux_host_class_printer_activate)*</span></span> |
| ![Icono de desactivación de clase PRINTER de host](./media/user-guide/usbx-events/image153.png)    | <span data-ttu-id="5ddac-414">**Desactivación de clase PRINTER de host** *(ux_host_class_printer_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-414">**Host Class Printer Deactivate** *(ux_host_class_printer_deactivate)*</span></span> |
| ![Icono de obtención de nombre de clase PRINTER de host](./media/user-guide/usbx-events/image154.png)    | <span data-ttu-id="5ddac-416">**Obtención de nombre de clase PRINTER de host** *(ux_host_class_printer_name_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-416">**Host Class Printer Name Get** *(ux_host_class_printer_name_get)*</span></span> |
| ![Icono de lectura de clase PRINTER de host](./media/user-guide/usbx-events/image155.png)    |  <span data-ttu-id="5ddac-418">**Lectura de clase PRINTER de host** *(ux_host_class_printer_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-418">**Host Class Printer Read** *(ux_host_class_printer_read)*</span></span> |
| ![Icono de restablecimiento parcial de clase PRINTER de host](./media/user-guide/usbx-events/image156.png)    | <span data-ttu-id="5ddac-420">**Restablecimiento parcial de clase PRINTER de host** *(ux_host_class_printer_soft_reset)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-420">**Host Class Printer Soft Reset** *(ux_host_class_printer_soft_reset)*</span></span> |
| ![Icono de obtención de estado de clase PRINTER de host](./media/user-guide/usbx-events/image157.png)    | <span data-ttu-id="5ddac-422">**Obtención de estado de clase PRINTER de host** *(ux_host_class_printer_status_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-422">**Host Class Printer Status Get** *(ux_host_class_printer_status_get)*</span></span> |
| ![Icono de escritura de clase PRINTER de host](./media/user-guide/usbx-events/image158.png)    | <span data-ttu-id="5ddac-424">**Escritura de clase PRINTER de host** *(ux_host_class_printer_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-424">**Host Class Printer Write** *(ux_host_class_printer_write)*</span></span> |
| ![Icono de activación de clase PROLIFIC de host](./media/user-guide/usbx-events/image159.png)    | <span data-ttu-id="5ddac-426">**Activación de clase PROLIFIC de host** *(ux_host_class_prolific_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-426">**Host Class Prolific Activate** *(ux_host_class_prolific_activate)*</span></span> |
| ![Icono de desactivación de clase PROLIFIC de host](./media/user-guide/usbx-events/image160.png)    | <span data-ttu-id="5ddac-428">**Desactivación de clase PROLIFIC de host** *(ux_host_class_prolific_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-428">**Host Class Prolific Deactivate** *(ux_host_class_prolific_deactivate)*</span></span> |
| ![Icono de función I O C T L de anulación de canalización de entrada de clase PROLIFIC de host](./media/user-guide/usbx-events/image161.png)    | <span data-ttu-id="5ddac-430">**Función IOCTL de anulación de canalización de entrada de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-430">**Host Class Prolific Ioctl Abort In Pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span></span> |
| ![Icono de función I O C T L de anulación de canalización de salida de clase PROLIFIC de host](./media/user-guide/usbx-events/image162.png)    | <span data-ttu-id="5ddac-432">**Función IOCTL de anulación de canalización de salida de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-432">**Host Class Prolific Ioctl Abort Out Pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span></span> |
| ![Icono de función I O C T L de obtención de estado de dispositivo de clase PROLIFIC de host](./media/user-guide/usbx-events/image163.png)    | <span data-ttu-id="5ddac-434">**Función IOCTL de obtención de estado de dispositivo de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-434">**Host Class Prolific Ioctl Get Device Status** *(ux_host_class_prolific_ioctl_get_device_status)*</span></span> |
| ![Icono de función I O C T L de obtención de codificación de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image164.png)    | <span data-ttu-id="5ddac-436">**Función IOCTL de obtención de codificación de línea de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-436">**Host Class Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)*</span></span> |
| ![Icono de función I O C T L de depuración de clase PROLIFIC de host](./media/user-guide/usbx-events/image165.png)    | <span data-ttu-id="5ddac-438">**Función IOCTL de depuración de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_purge)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-438">**Host Class Prolific Ioctl Purge** *(ux_host_class_prolific_ioctl_purge)*</span></span> |
| ![Icono de función I O C T L de informe de cambio de estado de dispositivo de clase PROLIFIC de host](./media/user-guide/usbx-events/image166.png)    | <span data-ttu-id="5ddac-440">**Función IOCTL de informe de cambio de estado de dispositivo de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-440">**Host Class Prolific Ioctl Report Device Status Change** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span></span> |
| ![Icono de función I O C T L de interrupción de envío de clase PROLIFIC de host](./media/user-guide/usbx-events/image167.png)    | <span data-ttu-id="5ddac-442">**Función IOCTL de interrupción de envío de clase PROLIFIC de host** *(ux_host_class_prolific_send_break)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-442">**Host Class Prolific Ioctl Send Break** *(ux_host_class_prolific_ioctl_send_break)*</span></span> |
| ![Icono de función I O C T L de establecimiento de codificación de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image168.png)    | <span data-ttu-id="5ddac-444">**Función IOCTL de establecimiento de codificación de línea de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-444">**Host Class Prolific Ioctl Set Line Coding** *(ux_host_class_prolific_ioctl_set_line_coding)*</span></span> |
| ![Icono de función I O C T L de establecimiento de estado de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image169.png)    | <span data-ttu-id="5ddac-446">**Función IOCTL de establecimiento de estado de línea de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-446">**Host Class Prolific Ioctl Set Line State** *(ux_host_class_prolific_ioctl_set_line_state)*</span></span> |
| ![Icono de lectura de clase PROLIFIC de host](./media/user-guide/usbx-events/image170.png)    | <span data-ttu-id="5ddac-448">**Lectura de clase PROLIFIC de host** *(ux_host_class_prolific_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-448">**Host Class Prolific Read** *(ux_host_class_prolific_read)*</span></span> |
| ![Icono de inicio de recepción de clase PROLIFIC de host](./media/user-guide/usbx-events/image171.png)    | <span data-ttu-id="5ddac-450">**Inicio de recepción de clase PROLIFIC de host** *(ux_host_class_prolific_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-450">**Host Class Prolific Reception Start** *(ux_host_class_prolific_reception_start)*</span></span> |
| ![Icono de parada de recepción de clase PROLIFIC de host](./media/user-guide/usbx-events/image172.png)    | <span data-ttu-id="5ddac-452">**Parada de recepción de clase PROLIFIC de host** *(ux_host_class_prolific_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-452">**Host Class Prolific Reception Stop** *(ux_host_class_prolific_reception_stop)*</span></span> |
| ![Icono de escritura de clase PROLIFIC de host](./media/user-guide/usbx-events/image173.png)    | <span data-ttu-id="5ddac-454">**Escritura de clase PROLIFIC de host** *(ux_host_class_prolific_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-454">**Host Class Prolific Write** *(ux_host_class_prolific_write)*</span></span> |
| ![Icono de activación de clase STORAGE de host](./media/user-guide/usbx-events/image174.png)    | <span data-ttu-id="5ddac-456">**Activación de clase STORAGE de host** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-456">**Host Class Storage Activate** *(ux_host_class_storage_activate)*</span></span> |
| ![Icono de desactivación de clase STORAGE de host](./media/user-guide/usbx-events/image175.png)    | <span data-ttu-id="5ddac-458">**Desactivación de clase STORAGE de host** (*ux_host_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-458">**Host Class Storage Deactivate** (*ux_host_class_storage_deactivate)*</span></span> |
| ![Icono de obtención de capacidad de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image176.png)    | <span data-ttu-id="5ddac-460">**Obtención de capacidad de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-460">**Host Class Storage Media Capacity Get** *(ux_host_class_storage_media_capacity_get)*</span></span> |
| ![Icono de obtención de capacidad de formato de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image177.png)    | <span data-ttu-id="5ddac-462">**Obtención de capacidad de formato de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_format_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-462">**Host Class Storage Media Format Capacity Get** *(ux_host_class_storage_media_format_capacity_get)*</span></span> |
| ![Icono de montaje de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image178.png)    | <span data-ttu-id="5ddac-464">**Montaje de soporte físico de clase STORAGE de host** (ux_host_class_storage_media_mount)\*</span><span class="sxs-lookup"><span data-stu-id="5ddac-464">**Host Class Storage Media Mount** (ux_host_class_storage_media_mount)\*</span></span> |
| ![Icono de apertura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image179.png)    | <span data-ttu-id="5ddac-466">**Apertura de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_open)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-466">**Host Class Storage Media Open** *(ux_host_class_storage_media_open)*</span></span> |
| ![Icono de lectura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image180.png)    | <span data-ttu-id="5ddac-468">**Lectura de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-468">**Host Class Storage Media Read** *(ux_host_class_storage_media_read)*</span></span> |
| ![Icono de escritura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image181.png)    | <span data-ttu-id="5ddac-470">**Escritura de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_write)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-470">**Host Class Storage Media Write** *(ux_host_class_storage_media_write)*</span></span> |
| ![Icono de detección de solicitud de clase STORAGE de host](./media/user-guide/usbx-events/image182.png)    | <span data-ttu-id="5ddac-472">**Detección de solicitud de clase STORAGE de host** *(ux_host_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-472">**Host Class Storage Request Sense** *(ux_host_class_storage_request_sense)*</span></span> |
| ![Icono de inicio/parada inicio de clase STORAGE de host](./media/user-guide/usbx-events/image183.png)    | <span data-ttu-id="5ddac-474">**Inicio/parada inicio de clase STORAGE de host** *(ux_host_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-474">**Host Class Storage Start Stop** *(ux_host_class_storage_start_stop)*</span></span> |
| ![Icono de prueba de unidad preparada de clase STORAGE de host](./media/user-guide/usbx-events/image184.png)    | <span data-ttu-id="5ddac-476">**Prueba de unidad preparada de clase STORAGE de host** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-476">**Host Class Storage Unit Ready Test** *(ux_host_class_storage_activate)*</span></span> |
| ![Icono de creación de instancia de clase de pila de hosts](./media/user-guide/usbx-events/image185.png)    | <span data-ttu-id="5ddac-478">**Creación de instancia de clase de pila de hosts** *(ux_host_stack_class_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-478">**Host Stack Class Instance Create** *(ux_host_stack_class_instance_create)*</span></span> |
| ![Icono de destrucción de instancia de clase de pila de hosts](./media/user-guide/usbx-events/image186.png)    | <span data-ttu-id="5ddac-480">**Destrucción de instancia de clase de pila de hosts** *(ux_host_stack_class_instance_destroy)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-480">**Host Stack Class Instance Destroy** *(ux_host_stack_class_instance_destroy)*</span></span> |
| ![Icono de eliminación de configuración de pila de hosts](./media/user-guide/usbx-events/image187.png)    | <span data-ttu-id="5ddac-482">**Eliminación de configuración de pila de hosts** *(ux_host_stack_configuration_delete)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-482">**Host Stack Configuration Delete** *(ux_host_stack_configuration_delete)*</span></span> |
| ![Icono de enumeración de configuración de pila de hosts](./media/user-guide/usbx-events/image188.png)    | <span data-ttu-id="5ddac-484">**Enumeración de configuración de pila de hosts** *(ux_host_stack_configuration_enumerate)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-484">**Host Stack Configuration Enumerate** *(ux_host_stack_configuration_enumerate)*</span></span> |
| ![Icono de creación de instancia de configuración de pila de hosts](./media/user-guide/usbx-events/image189.png)    | <span data-ttu-id="5ddac-486">**Creación de instancia de configuración de pila de hosts** *(ux_host_stack_configuration_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-486">**Host Stack Configuration Instance Create** *(ux_host_stack_configuration_instance_create)*</span></span> |
| ![Icono de eliminación de instancia de configuración de pila de hosts](./media/user-guide/usbx-events/image190.png)    | <span data-ttu-id="5ddac-488">**Eliminación de instancia de configuración de pila de hosts** *(ux_host_stack_configuration_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-488">**Host Stack Configuration Instance Delete** *(ux_host_stack_configuration_instance_delete)*</span></span> |
| ![Icono de establecimiento de configuración de pila de hosts](./media/user-guide/usbx-events/image191.png)    | <span data-ttu-id="5ddac-490">**Establecimiento de configuración de pila de hosts** *(ux_host_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-490">**Host Stack Configuration Set** *(ux_host_stack_configuration_set)*</span></span> |
| ![Icono de establecimiento de dirección de dispositivo de pila de hosts](./media/user-guide/usbx-events/image192.png)    | <span data-ttu-id="5ddac-492">**Establecimiento de dirección de dispositivo de pila de hosts** *(ux_host_stack_device_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-492">**Host Stack Device Address Set** *(ux_host_stack_device_set)*</span></span> |
| ![Icono de obtención de configuración de dispositivo de pila de hosts](./media/user-guide/usbx-events/image193.png)    | <span data-ttu-id="5ddac-494">**Obtención de configuración de dispositivo de pila de hosts** *(ux_host_stack_device_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-494">**Host Stack Device Configuration Get** *(ux_host_stack_device_configuration_get)*</span></span> |
| ![Icono de selección de configuración de dispositivo de pila de hosts](./media/user-guide/usbx-events/image194.png)    | <span data-ttu-id="5ddac-496">**Selección de configuración de dispositivo de pila de hosts** *(ux_host_stack_device_configuration_select)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-496">**Host Stack Device Configuration Select** *(ux_host_stack_device_configuration_select)*</span></span> |
| ![Icono de lectura de descriptor de dispositivo de pila de hosts](./media/user-guide/usbx-events/image195.png)    | <span data-ttu-id="5ddac-498">**Lectura de descriptor de dispositivo de pila de hosts** *(ux_host_stack_device_descriptor_read)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-498">**Host Stack Device Descriptor Read** *(ux_host_stack_device_descriptor_read)*</span></span> |
| ![Icono de obtención de dispositivo de pila de hosts](./media/user-guide/usbx-events/image196.png)    | <span data-ttu-id="5ddac-500">**Obtención de dispositivo de pila de hosts** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="5ddac-500">**Host Stack Device Get** (ux_host_stack_device_get)</span></span> |
| ![Icono de eliminación de dispositivo de pila de hosts](./media/user-guide/usbx-events/image197.png)    | <span data-ttu-id="5ddac-502">**Eliminación de dispositivo de pila de hosts** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="5ddac-502">**Host Stack Device Remove** (ux_host_stack_device_get)</span></span> |
| ![Icono de recurso libre de dispositivo de pila de hosts](./media/user-guide/usbx-events/image198.png)    | <span data-ttu-id="5ddac-504">**Recurso libre de dispositivo de pila de hosts** (ux_host_stack_device_resource_free)</span><span class="sxs-lookup"><span data-stu-id="5ddac-504">**Host Stack Device Resource Free** (ux_host_stack_device_resource_free)</span></span> |
| ![Icono de creación de instancia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image199.png)    | <span data-ttu-id="5ddac-506">**Creación de instancia de punto de conexión de pila de hosts** (ux_host_stack_endpoint_instance_create)</span><span class="sxs-lookup"><span data-stu-id="5ddac-506">**Host Stack Endpoint Instance Create** (ux_host_stack_endpoint_instance_create)</span></span> |
| ![Icono de eliminación de instancia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image200.png)    | <span data-ttu-id="5ddac-508">**Eliminación de instancia de punto de conexión de pila de hosts** (ux_host_stack_endpoint_instance_delete)</span><span class="sxs-lookup"><span data-stu-id="5ddac-508">**Host Stack Endpoint Instance Delete** (ux_host_stack_endpoint_instance_delete)</span></span> |
| ![Icono de restablecimiento de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image201.png)    | <span data-ttu-id="5ddac-510">**Restablecimiento de punto de conexión de pila de hosts** (ux_host_stack_endpoint_reset)</span><span class="sxs-lookup"><span data-stu-id="5ddac-510">**Host Stack Endpoint Reset** (ux_host_stack_endpoint_reset)</span></span> |
| ![Icono de anulación de transferencia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image202.png)    | <span data-ttu-id="5ddac-512">**Anulación de transferencia de punto de conexión de pila de hosts** (ux_host_stack_endpoint_transfer_abort)</span><span class="sxs-lookup"><span data-stu-id="5ddac-512">**Host Stack Endpoint Transfer Abort** (ux_host_stack_endpoint_transfer_abort)</span></span> |
| ![Icono de registro de controlador de host de pila de hosts](./media/user-guide/usbx-events/image203.png)    | <span data-ttu-id="5ddac-514">**Registro de controlador de host de pila de hosts** *(ux_host_stack_hcd_register)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-514">**Host Stack Host Controller Register** *(ux_host_stack_hcd_register)*</span></span> |
| ![Icono de inicialización de pila de hosts](./media/user-guide/usbx-events/image204.png)    | <span data-ttu-id="5ddac-516">**Inicialización de pila de hosts** *(ux_host_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-516">**Host Stack Initialize** *(ux_host_stack_initialize)*</span></span> |
| ![Icono de obtención de punto de conexión de interfaz de pila de hosts](./media/user-guide/usbx-events/image205.png)    | <span data-ttu-id="5ddac-518">**Obtención de punto de conexión de interfaz de pila de hosts** *(ux_host_stack_interface_endpoint_get)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-518">**Host Stack Interface Endpoint Get** *(ux_host_stack_interface_endpoint_get)*</span></span> |
| ![Icono de creación de instancia de interfaz de pila de hosts](./media/user-guide/usbx-events/image206.png)    | <span data-ttu-id="5ddac-520">**Creación de instancia de interfaz de pila de hosts** *(ux_host_stack_interface_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-520">**Host Stack Interface Instance Create** *(ux_host_stack_interface_instance_create)*</span></span> |
| ![Icono de eliminación de instancia de interfaz de pila de hosts](./media/user-guide/usbx-events/image207.png)    | <span data-ttu-id="5ddac-522">**Eliminación de instancia de interfaz de pila de hosts** *(ux_host_stack_interface_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-522">**Host Stack Interface Instance Delete** *(ux_host_stack_interface_instance_delete)*</span></span> |
| ![Icono de establecimiento de interfaz de pila de hosts](./media/user-guide/usbx-events/image208.png)    | <span data-ttu-id="5ddac-524">**Establecimiento de interfaz de pila de hosts** *(ux_host_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-524">**Host Stack Interface Set** *(ux_host_stack_interface_set)*</span></span> |
| ![Icono de selección de configuración de interfaz de pila de hosts](./media/user-guide/usbx-events/image209.png)    | <span data-ttu-id="5ddac-526">**Selección de configuración de interfaz de pila de hosts** *(ux_host_stack_interface_setting_select)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-526">**Host Stack Interface Setting Select** *(ux_host_stack_interface_setting_select)*</span></span> |
| ![Icono de creación de nueva configuración de pila de hosts](./media/user-guide/usbx-events/image210.png)    | <span data-ttu-id="5ddac-528">**Creación de nueva configuración de pila de hosts** *(ux_host_stack_new_configuration_create)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-528">**Host Stack New Configuration Create** *(ux_host_stack_new_configuration_create)*</span></span> |
| ![Icono de creación de nuevo dispositivo de pila de hosts](./media/user-guide/usbx-events/image211.png)    | <span data-ttu-id="5ddac-530">**Creación de nuevo dispositivo de pila de hosts** *(ux_host_stack_new_device_create)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-530">**Host Stack New Device Create** *(ux_host_stack_new_device_create)*</span></span> |
| ![Icono de creación de nuevo punto de conexión de pila de hosts](./media/user-guide/usbx-events/image212.png)    | <span data-ttu-id="5ddac-532">**Creación de nuevo punto de conexión de pila de hosts** *(ux_host_stack_new_endpoint_create)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-532">**Host Stack New Endpoint Create** *(ux_host_stack_new_endpoint_create)*</span></span> |
| ![Icono de proceso de cambio de centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image213.png)    | <span data-ttu-id="5ddac-534">**Proceso de cambio de centro de conectividad raíz de pila de hosts** *(ux_host_stack_rh_change_process)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-534">**Host Stack Root Hub Change Process** *(ux_host_stack_rh_change_process)*</span></span> |
| ![Icono de extracción de dispositivo de centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image214.png)    | <span data-ttu-id="5ddac-536">**Extracción de dispositivo de centro de conectividad raíz de pila de hosts** *(ux_host_stack_rh_device_extraction)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-536">**Host Stack Root Hub Device Extraction** *(ux_host_stack_rh_device_extraction)*</span></span> |
| ![Icono de inserción de dispositivo en centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image215.png)    | <span data-ttu-id="5ddac-538">**Inserción de dispositivo en centro de conectividad raíz de pila de hosts** *(ux_host_stack_rh_device_insertion)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-538">**Host Stack Root Hub Device Insertion** *(ux_host_stack_rh_device_insertion)*</span></span> |
| ![Icono de solicitud de transferencia de pila de hosts](./media/user-guide/usbx-events/image216.png)    | <span data-ttu-id="5ddac-540">**Solicitud de transferencia de pila de hosts** *(ux_host_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-540">**Host Stack Transfer Request** *(ux_host_stack_transfer_request)*</span></span> |
| ![Icono de anulación de solicitud de transferencia de pila de hosts](./media/user-guide/usbx-events/image217.png)    | <span data-ttu-id="5ddac-542">**Anulación de solicitud de transferencia de pila de hosts** *(ux_host_stack_transfer_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-542">**Host Stack Transfer Request Abort** *(ux_host_stack_transfer_request_abort)*</span></span> |
| ![Icono de error de U S B X](./media/user-guide/usbx-events/image218.png)    | <span data-ttu-id="5ddac-544">**Error de USBX** *(ux_error)*</span><span class="sxs-lookup"><span data-stu-id="5ddac-544">**USBX Error** *(ux_error)*</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="5ddac-545">Descripciones de eventos</span><span class="sxs-lookup"><span data-stu-id="5ddac-545">Event Descriptions</span></span>

<span data-ttu-id="5ddac-546">En las páginas siguientes se describen los eventos de seguimiento de USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-546">The following pages describe the USBX Trace Events.</span></span>

### <a name="device-class-cdc-activate"></a><span data-ttu-id="5ddac-547">Activación de clase CDC de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-547">Device Class Cdc Activate</span></span> 

#### <a name="ux_device_class_cdc_activate"></a><span data-ttu-id="5ddac-548">ux_device_class_cdc_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-548">ux_device_class_cdc_activate</span></span>

<span data-ttu-id="5ddac-549">**Icono** ![Icono de activación de clase C D C de dispositivo](./media/user-guide/usbx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-549">**Icon** ![Device Class C D C Activate icon](./media/user-guide/usbx-events/image1.png)</span></span>

<span data-ttu-id="5ddac-550">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-550">**Description**</span></span>

<span data-ttu-id="5ddac-551">Este evento representa un evento de activación de la clase CDC del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-551">This event represents a USBX Device Class Cdc Activate Event.</span></span>

<span data-ttu-id="5ddac-552">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-552">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-553">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-553">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-554">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-554">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-555">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-555">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-556">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-556">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-deactivate"></a><span data-ttu-id="5ddac-557">Desactivación de clase CDC de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-557">Device Class Cdc Deactivate</span></span> 

#### <a name="ux_device_class_cdc_deactivate"></a><span data-ttu-id="5ddac-558">ux_device_class_cdc_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-558">ux_device_class_cdc_deactivate</span></span>

<span data-ttu-id="5ddac-559">**Icono** ![Icono de desactivación de clase C D C de dispositivo](./media/user-guide/usbx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-559">**Icon** ![Device Class C D C Deactivate icon](./media/user-guide/usbx-events/image2.png)</span></span>

<span data-ttu-id="5ddac-560">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-560">**Description**</span></span>

<span data-ttu-id="5ddac-561">Este evento representa una desactivación de la clase CDC del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-561">This event represents a USBX Device Class Cdc Deactivate.</span></span>

<span data-ttu-id="5ddac-562">Campos de información</span><span class="sxs-lookup"><span data-stu-id="5ddac-562">Information Fields</span></span> 

- <span data-ttu-id="5ddac-563">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-563">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-564">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-564">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-565">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-565">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-566">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-566">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-read"></a><span data-ttu-id="5ddac-567">Lectura de clase CDC de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-567">Device Class Cdc Read</span></span> 

#### <a name="ux_device_class_cdc_read"></a><span data-ttu-id="5ddac-568">ux_device_class_cdc_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-568">ux_device_class_cdc_read</span></span>

<span data-ttu-id="5ddac-569">**Icono** ![Icono de lectura de clase C D C de dispositivo](./media/user-guide/usbx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-569">**Icon** ![Device Class C D C Read icon](./media/user-guide/usbx-events/image3.png)</span></span>

<span data-ttu-id="5ddac-570">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-570">**Description**</span></span>

<span data-ttu-id="5ddac-571">Este evento representa un evento de lectura de la clase CDC del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-571">This event represents a USBX Device Class Cdc Read Event.</span></span>

<span data-ttu-id="5ddac-572">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-572">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-573">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-573">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-574">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-574">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-575">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-575">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-576">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-576">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-write"></a><span data-ttu-id="5ddac-577">Escritura de clase CDC de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-577">Device Class Cdc Write</span></span> 

#### <a name="ux_device_class_cdc_write"></a><span data-ttu-id="5ddac-578">ux_device_class_cdc_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-578">ux_device_class_cdc_write</span></span>

<span data-ttu-id="5ddac-579">**Icono** ![Icono de escritura de clase C D C de dispositivo](./media/user-guide/usbx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-579">**Icon** ![Device Class C D C Write icon](./media/user-guide/usbx-events/image4.png)</span></span>

<span data-ttu-id="5ddac-580">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-580">**Description**</span></span>

<span data-ttu-id="5ddac-581">Este evento representa un evento de escritura de la clase CDC del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-581">This event represents a USBX Device Class Cdc Write Event.</span></span>

<span data-ttu-id="5ddac-582">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-582">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-583">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-583">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-584">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-584">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-585">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-585">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-586">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-586">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-activate"></a><span data-ttu-id="5ddac-587">Activación de clase DPUMP de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-587">Device Class Dpump Activate</span></span> 

#### <a name="ux_device_class_dpump_activate"></a><span data-ttu-id="5ddac-588">ux_device_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-588">ux_device_class_dpump_activate</span></span>

<span data-ttu-id="5ddac-589">**Icono** ![Icono de activación de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-589">**Icon** ![Device Class Dpump Activate icon](./media/user-guide/usbx-events/image5.png)</span></span>

<span data-ttu-id="5ddac-590">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-590">**Description**</span></span>

<span data-ttu-id="5ddac-591">Este evento representa un evento de activación de la clase DPUMP del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-591">This event represents a USBX Device Class Dpump Activate Event.</span></span>

<span data-ttu-id="5ddac-592">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-592">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-593">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-593">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-594">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-594">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-595">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-595">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-596">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-596">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-deactivate"></a><span data-ttu-id="5ddac-597">Desactivación de clase DPUMP de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-597">Device Class Dpump Deactivate</span></span> 

#### <a name="ux_device_class_dpump_deactivate"></a><span data-ttu-id="5ddac-598">ux_device_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-598">ux_device_class_dpump_deactivate</span></span>

<span data-ttu-id="5ddac-599">**Icono** ![Icono de desactivación de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-599">**Icon** ![Device Class Dpump Deactivate icon](./media/user-guide/usbx-events/image6.png)</span></span>

<span data-ttu-id="5ddac-600">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-600">**Description**</span></span>

<span data-ttu-id="5ddac-601">Este evento representa un evento de desactivación de la clase DPUMP del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-601">This event represents a USBX Device Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="5ddac-602">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-602">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-603">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-603">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-604">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-604">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-605">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-605">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-606">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-606">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-read"></a><span data-ttu-id="5ddac-607">Lectura de clase DPUMP de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-607">Device Class Dpump Read</span></span> 

#### <a name="ux_device_class_dpump_read"></a><span data-ttu-id="5ddac-608">ux_device_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-608">ux_device_class_dpump_read</span></span>

<span data-ttu-id="5ddac-609">**Icono** ![Icono de lectura de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-609">**Icon** ![Device Class Dpump Read icon](./media/user-guide/usbx-events/image7.png)</span></span>

<span data-ttu-id="5ddac-610">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-610">**Description**</span></span>

<span data-ttu-id="5ddac-611">Este evento representa un evento de lectura de la clase DPUMP del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-611">This event represents a USBX Device Class Dpump Read Event.</span></span>

<span data-ttu-id="5ddac-612">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-612">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-613">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-613">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-614">Campo de información 2: búfer</span><span class="sxs-lookup"><span data-stu-id="5ddac-614">Info Field 2: Buffer.</span></span>
- <span data-ttu-id="5ddac-615">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-615">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-616">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-616">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-write"></a><span data-ttu-id="5ddac-617">Escritura de clase DPUMP de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-617">Device Class Dpump Write</span></span> 

#### <a name="ux_device_class_dpump_write"></a><span data-ttu-id="5ddac-618">ux_device_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-618">ux_device_class_dpump_write</span></span>

<span data-ttu-id="5ddac-619">**Icono** ![Icono de escritura de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-619">**Icon** ![Device Class Dpump Write icon](./media/user-guide/usbx-events/image8.png)</span></span>

<span data-ttu-id="5ddac-620">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-620">**Description**</span></span>

<span data-ttu-id="5ddac-621">Este evento representa un evento de escritura de la clase DPUMP del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-621">This event represents a USBX Device Class Dpump Write Event.</span></span>

<span data-ttu-id="5ddac-622">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-622">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-623">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-623">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-624">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-624">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-625">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-625">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-626">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-626">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-activate"></a><span data-ttu-id="5ddac-627">Activación de clase HID de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-627">Device Class Hid Activate</span></span> 

#### <a name="ux_device_class_hid_activate"></a><span data-ttu-id="5ddac-628">ux_device_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-628">ux_device_class_hid_activate</span></span>

<span data-ttu-id="5ddac-629">**Icono** ![Icono de activación de clase H I D de dispositivo](./media/user-guide/usbx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-629">**Icon** ![Device Class Hid Activate icon](./media/user-guide/usbx-events/image9.png)</span></span>

<span data-ttu-id="5ddac-630">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-630">**Description**</span></span>

<span data-ttu-id="5ddac-631">Este evento representa un evento de activación de la clase HID del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-631">This event represents a USBX Device Class Hid Activate Event.</span></span>

<span data-ttu-id="5ddac-632">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-632">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-633">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-633">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-634">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-634">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-635">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-635">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-636">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-636">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-deactivate"></a><span data-ttu-id="5ddac-637">Desactivación de clase HID de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-637">Device Class Hid Deactivate</span></span> 

#### <a name="ux_device_class_hid_deactivate"></a><span data-ttu-id="5ddac-638">ux_device_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-638">ux_device_class_hid_deactivate</span></span>

<span data-ttu-id="5ddac-639">**Icono** ![Icono de desactivación de clase H I D de dispositivo](./media/user-guide/usbx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-639">**Icon** ![Device Class Hid Deactivate icon](./media/user-guide/usbx-events/image10.png)</span></span>

<span data-ttu-id="5ddac-640">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-640">**Description**</span></span>

<span data-ttu-id="5ddac-641">Este evento representa un evento de desactivación de la clase HID del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-641">This event represents a USBX Device Class Hid Deactivate Event.</span></span>

<span data-ttu-id="5ddac-642">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-642">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-643">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-643">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-644">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-644">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-645">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-645">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-646">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-646">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-descriptor-send"></a><span data-ttu-id="5ddac-647">Envío de descriptor de clase HID de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-647">Device Class Hid Descriptor Send</span></span> 

#### <a name="ux_device_class_hid_descritpor_send"></a><span data-ttu-id="5ddac-648">ux_device_class_hid_descritpor_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-648">ux_device_class_hid_descritpor_send</span></span>

<span data-ttu-id="5ddac-649">**Icono** ![Icono de envío de descriptor de clase H I D de dispositivo](./media/user-guide/usbx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-649">**Icon** ![Device Class Hid Descriptor Send icon](./media/user-guide/usbx-events/image11.png)</span></span>

<span data-ttu-id="5ddac-650">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-650">**Description**</span></span>

<span data-ttu-id="5ddac-651">Este evento representa un evento de envío de descriptor de la clase HID del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-651">This event represents a USBX Device Class Hid Descriptor Send Event.</span></span>

<span data-ttu-id="5ddac-652">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-652">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-653">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-653">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-654">Campo de información 2: tipo de descriptor</span><span class="sxs-lookup"><span data-stu-id="5ddac-654">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="5ddac-655">Campo de información 3: índice de la solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-655">Info Field 3: Request index.</span></span>
- <span data-ttu-id="5ddac-656">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-656">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-get"></a><span data-ttu-id="5ddac-657">Obtención de evento de clase HID de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-657">Device Class Hid Event Get</span></span> 

#### <a name="ux_device_class_hid_event_get"></a><span data-ttu-id="5ddac-658">ux_device_class_hid_event_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-658">ux_device_class_hid_event_get</span></span>

<span data-ttu-id="5ddac-659">**Icono** ![Icono de obtención de evento de clase H I D de dispositivo](./media/user-guide/usbx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-659">**Icon** ![Device Class Hid Event Get icon](./media/user-guide/usbx-events/image12.png)</span></span>

<span data-ttu-id="5ddac-660">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-660">**Description**</span></span>

<span data-ttu-id="5ddac-661">Este evento representa un evento de obtención de evento de la clase HID del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-661">This event represents a USBX Device Class Hid Event Get Event.</span></span>

<span data-ttu-id="5ddac-662">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-662">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-663">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-663">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-664">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-664">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-665">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-665">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-666">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-666">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-set"></a><span data-ttu-id="5ddac-667">Establecimiento de evento de clase HID de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-667">Device Class Hid Event Set</span></span> 

#### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="5ddac-668">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-668">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="5ddac-669">**Icono** ![Icono de establecimiento de evento de clase H I D de dispositivo](./media/user-guide/usbx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-669">**Icon** ![Device Class Hid Event Set icon](./media/user-guide/usbx-events/image13.png)</span></span>

<span data-ttu-id="5ddac-670">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-670">**Description**</span></span>

<span data-ttu-id="5ddac-671">Este evento representa un evento de establecimiento de evento de la clase HID del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-671">This event represents a USBX Device Class Hid Event Set.</span></span>

<span data-ttu-id="5ddac-672">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-672">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-673">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-673">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-674">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-674">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-675">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-675">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-676">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-676">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-get"></a><span data-ttu-id="5ddac-677">Obtención de informe de clase HID de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-677">Device Class Hid Report Get</span></span> 

#### <a name="ux_device_class_hid_report_get"></a><span data-ttu-id="5ddac-678">ux_device_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-678">ux_device_class_hid_report_get</span></span>

<span data-ttu-id="5ddac-679">**Icono** ![Icono de obtención de informe de clase H I D de dispositivo](./media/user-guide/usbx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-679">**Icon** ![Device Class Hid Report Get icon](./media/user-guide/usbx-events/image14.png)</span></span>

<span data-ttu-id="5ddac-680">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-680">**Description**</span></span>

<span data-ttu-id="5ddac-681">Este evento representa un evento de obtención de informe de la clase HID del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-681">This event represents a USBX Device Class Hid Report Get Event.</span></span>

<span data-ttu-id="5ddac-682">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-682">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-683">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-683">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-684">Campo de información 2: tipo de descriptor</span><span class="sxs-lookup"><span data-stu-id="5ddac-684">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="5ddac-685">Campo de información 3: índice de la solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-685">Info Field 3: Request index.</span></span>
- <span data-ttu-id="5ddac-686">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-686">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-set"></a><span data-ttu-id="5ddac-687">Establecimiento de informe de clase HID de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-687">Device Class Hid Report Set</span></span> 

#### <a name="ux_device_class_hid_report_set"></a><span data-ttu-id="5ddac-688">ux_device_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-688">ux_device_class_hid_report_set</span></span>

<span data-ttu-id="5ddac-689">**Icono** ![Icono de establecimiento de informe de clase H I D de dispositivo](./media/user-guide/usbx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-689">**Icon** ![Device Class Hid Report Set icon](./media/user-guide/usbx-events/image15.png)</span></span>

<span data-ttu-id="5ddac-690">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-690">**Description**</span></span>

<span data-ttu-id="5ddac-691">Este evento representa un evento de establecimiento de informe de la clase HID del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-691">This event represents a USBX Device Class Hid Report Set Event.</span></span>

<span data-ttu-id="5ddac-692">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-692">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-693">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-693">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-694">Campo de información 2: tipo de descriptor</span><span class="sxs-lookup"><span data-stu-id="5ddac-694">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="5ddac-695">Campo de información 3: índice de la solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-695">Info Field 3: Request index.</span></span>
- <span data-ttu-id="5ddac-696">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-696">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-activate"></a><span data-ttu-id="5ddac-697">Activación de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-697">Device Class Pima Activate</span></span>

#### <a name="ux_device_class_pima_activate"></a><span data-ttu-id="5ddac-698">ux_device_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-698">ux_device_class_pima_activate</span></span>

<span data-ttu-id="5ddac-699">**Icono** ![Icono de activación de clase PIMA de dispositivo](./media/user-guide/usbx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-699">**Icon** ![Device Class Pima Activate icon](./media/user-guide/usbx-events/image16.png)</span></span>

<span data-ttu-id="5ddac-700">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-700">**Description**</span></span>

<span data-ttu-id="5ddac-701">Este evento representa un evento de activación de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-701">This event represents a USBX Device Class Pima Activate Event.</span></span>

<span data-ttu-id="5ddac-702">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-702">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-703">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-703">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-704">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-704">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-705">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-705">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-706">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-706">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-deactivate"></a><span data-ttu-id="5ddac-707">Desactivación de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-707">Device Class Pima Deactivate</span></span> 

#### <a name="ux_device_class_pima_deactivate"></a><span data-ttu-id="5ddac-708">ux_device_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-708">ux_device_class_pima_deactivate</span></span>

<span data-ttu-id="5ddac-709">**Icono** ![Icono de desactivación de clase PIMA de dispositivo](./media/user-guide/usbx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-709">**Icon** ![Device Class Pima Deactivate icon](./media/user-guide/usbx-events/image17.png)</span></span>

<span data-ttu-id="5ddac-710">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-710">**Description**</span></span>

<span data-ttu-id="5ddac-711">Este evento representa un evento de desactivación de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-711">This event represents a USBX Device Class Pima Deactivate Event.</span></span>

<span data-ttu-id="5ddac-712">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-712">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-713">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-713">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-714">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-714">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-715">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-715">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-716">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-716">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-device-info-send"></a><span data-ttu-id="5ddac-717">Envío de información de dispositivo de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-717">Device Class Pima Device Info Send</span></span> 

#### <a name="ux_device_class_pima_device_info_send"></a><span data-ttu-id="5ddac-718">ux_device_class_pima_device_info_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-718">ux_device_class_pima_device_info_send</span></span>

<span data-ttu-id="5ddac-719">**Icono** ![Icono de envío de información de dispositivo de clase PIMA de dispositivo](./media/user-guide/usbx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-719">**Icon** ![Device Class Pima Device Info Send icon](./media/user-guide/usbx-events/image18.png)</span></span>

<span data-ttu-id="5ddac-720">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-720">**Description**</span></span>

<span data-ttu-id="5ddac-721">Este evento representa un evento de envío de información de dispositivo de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-721">This event represents a USBX Device Class Pima Device Info Send Event.</span></span>

<span data-ttu-id="5ddac-722">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-722">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-723">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-723">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-724">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-724">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-725">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-725">Info Field 3: Not used.</span></span>

### <a name="device-class-pima-event-get"></a><span data-ttu-id="5ddac-726">Obtención de evento de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-726">Device Class Pima Event Get</span></span> 

#### <a name="ux_device_class_pima_event_get"></a><span data-ttu-id="5ddac-727">ux_device_class_pima_event_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-727">ux_device_class_pima_event_get</span></span>

<span data-ttu-id="5ddac-728">**Icono** ![Icono de obtención de evento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-728">**Icon** ![Device Class Pima Event Get icon](./media/user-guide/usbx-events/image19.png)</span></span>

<span data-ttu-id="5ddac-729">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-729">**Description**</span></span>

<span data-ttu-id="5ddac-730">Este evento representa un evento de obtención de evento de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-730">This event represents a USBX Device Class Pima Event Get Event.</span></span>

<span data-ttu-id="5ddac-731">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-731">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-732">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-732">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-733">Campo de información 2: evento de PIMA</span><span class="sxs-lookup"><span data-stu-id="5ddac-733">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="5ddac-734">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-734">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-735">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-735">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-event-set"></a><span data-ttu-id="5ddac-736">Establecimiento de evento de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-736">Device Class Pima Event Set</span></span> 

#### <a name="ux_device_class_pima_event_set"></a><span data-ttu-id="5ddac-737">ux_device_class_pima_event_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-737">ux_device_class_pima_event_set</span></span>

<span data-ttu-id="5ddac-738">**Icono** ![Icono de establecimiento de evento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-738">**Icon** ![Device Class Pima Event Set icon](./media/user-guide/usbx-events/image20.png)</span></span>

<span data-ttu-id="5ddac-739">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-739">**Description**</span></span>

<span data-ttu-id="5ddac-740">Este evento representa un evento de establecimiento de evento de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-740">This event represents a USBX Device Class Pima Event Set Event.</span></span>

<span data-ttu-id="5ddac-741">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-741">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-742">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-742">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-743">Campo de información 2: evento de PIMA</span><span class="sxs-lookup"><span data-stu-id="5ddac-743">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="5ddac-744">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-744">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-745">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-745">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-add"></a><span data-ttu-id="5ddac-746">Adición de objeto de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-746">Device Class Pima Object Add</span></span> 

#### <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="5ddac-747">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="5ddac-747">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="5ddac-748">**Icono** ![Icono de adición de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-748">**Icon** ![Device Class Pima Object Add icon](./media/user-guide/usbx-events/image21.png)</span></span>

<span data-ttu-id="5ddac-749">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-749">**Description**</span></span>

<span data-ttu-id="5ddac-750">Este evento representa un evento de adición de objeto de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-750">This event represents a USBX Device Class Pima Object Add Event.</span></span>

<span data-ttu-id="5ddac-751">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-751">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-752">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-752">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-753">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-753">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-754">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-754">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-755">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-755">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-get"></a><span data-ttu-id="5ddac-756">Obtención de datos de objeto de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-756">Device Class Pima Object Data Get</span></span> 

#### <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="5ddac-757">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-757">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="5ddac-758">**Icono** ![Icono de obtención de datos de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-758">**Icon** ![Device Class Pima Object Data Get icon](./media/user-guide/usbx-events/image22.png)</span></span>

<span data-ttu-id="5ddac-759">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-759">**Description**</span></span>

<span data-ttu-id="5ddac-760">Este evento representa un evento de obtención de datos de objeto de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-760">This event represents a USBX Device Class Pima Object Data Get Event.</span></span>

<span data-ttu-id="5ddac-761">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-761">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-762">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-762">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-763">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-763">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-764">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-764">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-765">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-765">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-send"></a><span data-ttu-id="5ddac-766">Envío de datos de objeto de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-766">Device Class Pima Object Data Send</span></span> 

#### <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="5ddac-767">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-767">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="5ddac-768">**Icono** ![Icono de envío de datos de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-768">**Icon** ![Device Class Pima Object Data Send icon](./media/user-guide/usbx-events/image23.png)</span></span>

<span data-ttu-id="5ddac-769">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-769">**Description**</span></span>

<span data-ttu-id="5ddac-770">Este evento representa un evento de envío de datos de objeto de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-770">This event represents a USBX Device Class Pima Object Data Send Event.</span></span>

<span data-ttu-id="5ddac-771">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-771">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-772">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-772">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-773">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-773">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-774">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-774">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-775">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-775">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-delete"></a><span data-ttu-id="5ddac-776">Eliminación de objeto de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-776">Device Class Pima Object Delete</span></span> 

#### <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="5ddac-777">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="5ddac-777">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="5ddac-778">**Icono** ![Icono de eliminación de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-778">**Icon** ![Device Class Pima Object Delete icon](./media/user-guide/usbx-events/image24.png)</span></span>

<span data-ttu-id="5ddac-779">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-779">**Description**</span></span>

<span data-ttu-id="5ddac-780">Este evento representa un evento de eliminación de objeto de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-780">This event represents a USBX Device Class Pima Object Delete Event.</span></span>

<span data-ttu-id="5ddac-781">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-781">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-782">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-782">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-783">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-783">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-784">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-784">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-785">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-785">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-handles-send"></a><span data-ttu-id="5ddac-786">Envío de identificadores de objeto de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-786">Device Class Pima Object Handles Send</span></span> 

#### <a name="ux_device_class_pima_object_handles_send"></a><span data-ttu-id="5ddac-787">ux_device_class_pima_object_handles_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-787">ux_device_class_pima_object_handles_send</span></span>

<span data-ttu-id="5ddac-788">**Icono** ![Icono de envío de identificadores de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-788">**Icon** ![Device Class Pima Object Handles Send icon](./media/user-guide/usbx-events/image25.png)</span></span>

<span data-ttu-id="5ddac-789">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-789">**Description**</span></span>

<span data-ttu-id="5ddac-790">Este evento representa un evento de envío de identificadores de objeto de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-790">This event represents a USBX Device Class Pima Object Handles Send Event.</span></span>

<span data-ttu-id="5ddac-791">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-791">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-792">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-792">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-793">Campo de información 2: identificador de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="5ddac-793">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="5ddac-794">Campo de información 3: código de formato de objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-794">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="5ddac-795">Campo de información 4: asociación de objetos</span><span class="sxs-lookup"><span data-stu-id="5ddac-795">Info Field 4: Object association.</span></span>

### <a name="device-class-pima-object-info-get"></a><span data-ttu-id="5ddac-796">Obtención de información de objeto de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-796">Device Class Pima Object Info Get</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="5ddac-797">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-797">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="5ddac-798">**Icono** ![Icono de obtención de información de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-798">**Icon** ![Device Class Pima Object Info Get icon](./media/user-guide/usbx-events/image26.png)</span></span>

<span data-ttu-id="5ddac-799">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-799">**Description**</span></span>

<span data-ttu-id="5ddac-800">Este evento representa un evento de obtención de información de objeto de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-800">This event represents a USBX Device Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="5ddac-801">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-801">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-802">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-802">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-803">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-803">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-804">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-804">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-805">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-805">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-info-send"></a><span data-ttu-id="5ddac-806">Envío de información de objeto de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-806">Device Class Pima Object Info Send</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="5ddac-807">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-807">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="5ddac-808">**Icono** ![Icono de envío de información de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-808">**Icon** ![Device Class Pima Object Info Send icon](./media/user-guide/usbx-events/image27.png)</span></span>

<span data-ttu-id="5ddac-809">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-809">**Description**</span></span>

<span data-ttu-id="5ddac-810">Este evento representa un evento de envío de información de objeto de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-810">This event represents a USBX Device Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="5ddac-811">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-811">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-812">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-812">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-813">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-813">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-814">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-814">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-815">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-815">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-objects-number-send"></a><span data-ttu-id="5ddac-816">Envío de número de objetos de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-816">Device Class Pima Objects Number Send</span></span> 

#### <a name="ux_device_class_pima_object_number_send"></a><span data-ttu-id="5ddac-817">ux_device_class_pima_object_number_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-817">ux_device_class_pima_object_number_send</span></span>

<span data-ttu-id="5ddac-818">**Icono** ![Icono de envío de número de objetos de clase PIMA de dispositivo](./media/user-guide/usbx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-818">**Icon** ![Device Class Pima Objects Number Send icon](./media/user-guide/usbx-events/image28.png)</span></span>

<span data-ttu-id="5ddac-819">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-819">**Description**</span></span>

<span data-ttu-id="5ddac-820">Este evento representa un evento de envío de número de objetos de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-820">This event represents a USBX Device Class Pima Object Number Send event.</span></span>

<span data-ttu-id="5ddac-821">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-821">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-822">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-822">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-823">Campo de información 2: identificador de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="5ddac-823">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="5ddac-824">Campo de información 3: código de formato de objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-824">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="5ddac-825">Campo de información 4: asociación de objetos</span><span class="sxs-lookup"><span data-stu-id="5ddac-825">Info Field 4: Object associate.</span></span>

### <a name="device-class-pima-partial-object-data-get"></a><span data-ttu-id="5ddac-826">Obtención de datos parciales de objeto de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-826">Device Class Pima Partial Object Data Get</span></span>

#### <a name="ux_device_class_pima_partial_object_data_get"></a><span data-ttu-id="5ddac-827">ux_device_class_pima_partial_object_data_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-827">ux_device_class_pima_partial_object_data_get</span></span>

<span data-ttu-id="5ddac-828">**Icono** ![Icono de obtención de datos parciales de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-828">**Icon** ![Device Class Pima Partial Object Data Get icon](./media/user-guide/usbx-events/image29.png)</span></span>

<span data-ttu-id="5ddac-829">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-829">**Description**</span></span>

<span data-ttu-id="5ddac-830">Este evento representa un evento de obtención de datos parciales de objeto de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-830">This event represents a USBX Device Class Pima Partial Object Data Get Event.</span></span>

<span data-ttu-id="5ddac-831">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-831">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-832">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-832">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-833">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-833">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-834">Campo de información 3: desplazamiento solicitado</span><span class="sxs-lookup"><span data-stu-id="5ddac-834">Info Field 3: Offset requested.</span></span>
- <span data-ttu-id="5ddac-835">Campo de información 4: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-835">Info Field 4: Length requested.</span></span>

### <a name="device-class-pima-response-send"></a><span data-ttu-id="5ddac-836">Envío de respuesta de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-836">Device Class Pima Response Send</span></span> 

#### <a name="ux_device_class_pima_response_send"></a><span data-ttu-id="5ddac-837">ux_device_class_pima_response_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-837">ux_device_class_pima_response_send</span></span>

<span data-ttu-id="5ddac-838">**Icono** ![Icono de envío de respuesta de clase PIMA de dispositivo](./media/user-guide/usbx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-838">**Icon** ![Device Class Pima Response Send icon](./media/user-guide/usbx-events/image30.png)</span></span>

<span data-ttu-id="5ddac-839">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-839">**Description**</span></span>

<span data-ttu-id="5ddac-840">Este evento representa un evento de envío de respuesta de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-840">This event represents a USBX Device Class Pima Response Send Event.</span></span>

<span data-ttu-id="5ddac-841">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-841">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-842">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-842">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-843">Campo de información 2: código de respuesta</span><span class="sxs-lookup"><span data-stu-id="5ddac-843">Info Field 2: Response code.</span></span>
- <span data-ttu-id="5ddac-844">Campo de información 3: parámetro de número</span><span class="sxs-lookup"><span data-stu-id="5ddac-844">Info Field 3: Number parameter.</span></span>
- <span data-ttu-id="5ddac-845">Campo de información 4: parámetro de PIMA 1</span><span class="sxs-lookup"><span data-stu-id="5ddac-845">Info Field 4: Pima parameter 1.</span></span>

### <a name="device-class-pima-storage-id-send"></a><span data-ttu-id="5ddac-846">Envío de identificador de almacenamiento de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-846">Device Class Pima Storage Id Send</span></span> 

#### <a name="ux_device_class_pima_storage_id_send"></a><span data-ttu-id="5ddac-847">ux_device_class_pima_storage_id_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-847">ux_device_class_pima_storage_id_send</span></span>

<span data-ttu-id="5ddac-848">**Icono** ![Icono de envío de identificador de almacenamiento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-848">**Icon** ![Device Class Pima Storage Id Send icon](./media/user-guide/usbx-events/image31.png)</span></span>

<span data-ttu-id="5ddac-849">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-849">**Description**</span></span>

<span data-ttu-id="5ddac-850">Este evento representa un evento de envío de identificador de almacenamiento de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-850">This event represents a USBX Device Class Pima Storage Id Send Event.</span></span>

<span data-ttu-id="5ddac-851">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-851">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-852">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-852">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-853">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-853">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-854">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-854">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-855">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-855">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-storage-info-send"></a><span data-ttu-id="5ddac-856">Envío de información de almacenamiento de clase PIMA de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-856">Device Class Pima Storage Info Send</span></span> 

#### <a name="ux_device_class_pima_storage_info_send"></a><span data-ttu-id="5ddac-857">ux_device_class_pima_storage_info_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-857">ux_device_class_pima_storage_info_send</span></span>

<span data-ttu-id="5ddac-858">**Icono** ![Icono de envío de información de almacenamiento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-858">**Icon** ![Device Class Pima Storage Info Send icon](./media/user-guide/usbx-events/image32.png)</span></span>

<span data-ttu-id="5ddac-859">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-859">**Description**</span></span>

<span data-ttu-id="5ddac-860">Este evento representa un evento de envío de información de almacenamiento de la clase PIMA del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-860">This event represents a USBX Device Class Pima Storage Info Send Event.</span></span>

<span data-ttu-id="5ddac-861">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-861">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-862">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-862">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-863">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-863">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-864">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-864">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-865">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-865">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-activate"></a><span data-ttu-id="5ddac-866">Activación de clase RNDIS de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-866">Device Class Rndis Activate</span></span> 

#### <a name="ux_device_class_rndis_activate"></a><span data-ttu-id="5ddac-867">ux_device_class_rndis_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-867">ux_device_class_rndis_activate</span></span>

<span data-ttu-id="5ddac-868">**Icono** ![Icono de activación de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-868">**Icon** ![Device Class Rndis Activate icon](./media/user-guide/usbx-events/image33.png)</span></span>

<span data-ttu-id="5ddac-869">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-869">**Description**</span></span>

<span data-ttu-id="5ddac-870">Este evento representa un evento de activación de la clase RNDIS del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-870">This event represents a USBX Device Class Rndis Activate Event.</span></span>

<span data-ttu-id="5ddac-871">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-871">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-872">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-872">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-873">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-873">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-874">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-874">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-875">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-875">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-deactivate"></a><span data-ttu-id="5ddac-876">Desactivación de clase RNDIS de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-876">Device Class Rndis Deactivate</span></span> 

#### <a name="ux_device_class_rndis_deactivate"></a><span data-ttu-id="5ddac-877">ux_device_class_rndis_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-877">ux_device_class_rndis_deactivate</span></span>

<span data-ttu-id="5ddac-878">**Icono** ![Icono de desactivación de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-878">**Icon** ![Device Class Rndis Deactivate icon](./media/user-guide/usbx-events/image34.png)</span></span>

<span data-ttu-id="5ddac-879">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-879">**Description**</span></span>

<span data-ttu-id="5ddac-880">Este evento representa un evento de desactivación de la clase RNDIS del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-880">This event represents a USBX Device Class Rndis Deactivate Event.</span></span>

<span data-ttu-id="5ddac-881">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-881">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-882">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-882">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-883">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-883">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-884">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-884">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-885">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-885">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-keep-alive"></a><span data-ttu-id="5ddac-886">Mantenimiento de conexión de mensaje de clase RNDIS de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-886">Device Class Rndis Message Keep Alive</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a><span data-ttu-id="5ddac-887">ux_device_class_rndis_msg_keep_alive</span><span class="sxs-lookup"><span data-stu-id="5ddac-887">ux_device_class_rndis_msg_keep_alive</span></span>

<span data-ttu-id="5ddac-888">**Icono** ![Icono de mantenimiento de conexión de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-888">**Icon** ![Device Class Rndis Message Keep Alive icon](./media/user-guide/usbx-events/image35.png)</span></span>

<span data-ttu-id="5ddac-889">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-889">**Description**</span></span>

<span data-ttu-id="5ddac-890">Este evento representa un evento de mantenimiento de conexión de mensaje de la clase RNDIS del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-890">This event represents a USBX Device Class Rndis Message Keep Alive Event.</span></span>

<span data-ttu-id="5ddac-891">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-891">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-892">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-892">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-893">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-893">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-894">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-894">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-895">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-895">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-query"></a><span data-ttu-id="5ddac-896">Consulta de mensaje de clase RNDIS de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-896">Device Class Rndis Message Query</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_query"></a><span data-ttu-id="5ddac-897">ux_device_class_rndis_msg_keep_query</span><span class="sxs-lookup"><span data-stu-id="5ddac-897">ux_device_class_rndis_msg_keep_query</span></span>

<span data-ttu-id="5ddac-898">**Icono** ![Icono de consulta de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-898">**Icon** ![Device Class Rndis Message Query icon](./media/user-guide/usbx-events/image36.png)</span></span>

<span data-ttu-id="5ddac-899">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-899">**Description**</span></span>

<span data-ttu-id="5ddac-900">Este evento representa un evento de consulta de mensaje de la clase RNDIS del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-900">This event represents a USBX Device Class Rndis Message Query Event.</span></span>

<span data-ttu-id="5ddac-901">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-901">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-902">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-902">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-903">Campo de información 2: OID de RNDIS</span><span class="sxs-lookup"><span data-stu-id="5ddac-903">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="5ddac-904">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-904">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-905">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-905">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-reset"></a><span data-ttu-id="5ddac-906">Restablecimiento de mensaje de clase RNDIS de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-906">Device Class Rndis Message Reset</span></span> 

#### <a name="ux_device_class_rndis_msg_reset"></a><span data-ttu-id="5ddac-907">ux_device_class_rndis_msg_reset</span><span class="sxs-lookup"><span data-stu-id="5ddac-907">ux_device_class_rndis_msg_reset</span></span>

<span data-ttu-id="5ddac-908">**Icono** ![Icono de restablecimiento de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-908">**Icon** ![Device Class Rndis Message Reset icon](./media/user-guide/usbx-events/image37.png)</span></span>

<span data-ttu-id="5ddac-909">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-909">**Description**</span></span>

<span data-ttu-id="5ddac-910">Este evento representa un evento de restablecimiento de mensaje de la clase RNDIS del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-910">This event represents a USBX Device Class Rndis Message Reset Event.</span></span>

<span data-ttu-id="5ddac-911">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-911">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-912">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-912">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-913">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-913">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-914">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-914">Info Field 3: Not used.</span></span>

### <a name="device-class-rndis-message-set"></a><span data-ttu-id="5ddac-915">Establecimiento de mensaje de clase RNDIS de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-915">Device Class Rndis Message Set</span></span> 

#### <a name="ux_device_class_rndis_msg_set"></a><span data-ttu-id="5ddac-916">ux_device_class_rndis_msg_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-916">ux_device_class_rndis_msg_set</span></span>

<span data-ttu-id="5ddac-917">**Icono** ![Icono de establecimiento de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-917">**Icon** ![Device Class Rndis Message Set icon](./media/user-guide/usbx-events/image38.png)</span></span>

<span data-ttu-id="5ddac-918">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-918">**Description**</span></span>

<span data-ttu-id="5ddac-919">Este evento representa un evento de establecimiento de mensaje de la clase RNDIS del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-919">This event represents a USBX Device Class Rndis Message Set Event.</span></span>

<span data-ttu-id="5ddac-920">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-920">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-921">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-921">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-922">Campo de información 2: OID de RNDIS</span><span class="sxs-lookup"><span data-stu-id="5ddac-922">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="5ddac-923">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-923">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-924">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-924">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-receive"></a><span data-ttu-id="5ddac-925">Recepción de paquete de clase RNDIS de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-925">Device Class Rndis Packet Receive</span></span> 

#### <a name="ux_device_class_rndis_packet_receive"></a><span data-ttu-id="5ddac-926">ux_device_class_rndis_packet_receive</span><span class="sxs-lookup"><span data-stu-id="5ddac-926">ux_device_class_rndis_packet_receive</span></span>

<span data-ttu-id="5ddac-927">**Icono** ![Icono de recepción de paquete de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-927">**Icon** ![Device Class Rndis Packet Receive icon](./media/user-guide/usbx-events/image39.png)</span></span>

<span data-ttu-id="5ddac-928">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-928">**Description**</span></span>

<span data-ttu-id="5ddac-929">Este evento representa un evento de recepción de paquete de la clase RNDIS del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-929">This event represents a USBX Device Class Rndis Packet Receive Event.</span></span>

<span data-ttu-id="5ddac-930">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-930">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-931">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-931">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-932">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-932">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-933">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-933">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-934">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-934">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-transmit"></a><span data-ttu-id="5ddac-935">Transmisión de paquete de clase RNDIS de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-935">Device Class Rndis Packet Transmit</span></span> 

#### <a name="ux_device_class_rndis_packet_transmit"></a><span data-ttu-id="5ddac-936">ux_device_class_rndis_packet_transmit</span><span class="sxs-lookup"><span data-stu-id="5ddac-936">ux_device_class_rndis_packet_transmit</span></span>

<span data-ttu-id="5ddac-937">**Icono** ![Icono de transmisión de paquete de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-937">**Icon** ![Device Class Rndis Packet Transmit icon](./media/user-guide/usbx-events/image40.png)</span></span>

<span data-ttu-id="5ddac-938">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-938">**Description**</span></span>

<span data-ttu-id="5ddac-939">Este evento representa un evento de transmisión de paquete de la clase RNDIS del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-939">This event represents a USBX Device Class Rndis Packet Transmit Event.</span></span>

<span data-ttu-id="5ddac-940">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-940">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-941">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-941">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-942">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-942">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-943">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-943">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-944">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-944">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-activate"></a><span data-ttu-id="5ddac-945">Activación de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-945">Device Class Storage Activate</span></span> 

#### <a name="ux_device_class_storage_activate"></a><span data-ttu-id="5ddac-946">ux_device_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-946">ux_device_class_storage_activate</span></span>

<span data-ttu-id="5ddac-947">**Icono** ![Icono de activación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-947">**Icon** ![Device Class Storage Activate icon](./media/user-guide/usbx-events/image41.png)</span></span>

<span data-ttu-id="5ddac-948">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-948">**Description**</span></span>

<span data-ttu-id="5ddac-949">Este evento representa un evento de activación de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-949">This event represents a USBX Device Class Storage Activate Event.</span></span>

<span data-ttu-id="5ddac-950">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-950">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-951">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-951">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-952">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-952">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-953">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-953">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-954">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-954">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-deactivate"></a><span data-ttu-id="5ddac-955">Desactivación de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-955">Device Class Storage Deactivate</span></span> 

#### <a name="ux_device_class_storage_deactivate"></a><span data-ttu-id="5ddac-956">ux_device_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-956">ux_device_class_storage_deactivate</span></span>

<span data-ttu-id="5ddac-957">**Icono** ![Icono de desactivación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-957">**Icon** ![Device Class Storage Deactivate icon](./media/user-guide/usbx-events/image42.png)</span></span>

<span data-ttu-id="5ddac-958">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-958">**Description**</span></span>

<span data-ttu-id="5ddac-959">Este evento representa un evento de desactivación de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-959">This event represents a USBX Device Class Storage Deactivate Event.</span></span>

<span data-ttu-id="5ddac-960">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-960">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-961">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-961">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-962">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-962">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-963">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-963">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-964">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-964">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-format"></a><span data-ttu-id="5ddac-965">Formato de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-965">Device Class Storage Format</span></span> 

#### <a name="ux_device_class_storage_format"></a><span data-ttu-id="5ddac-966">ux_device_class_storage_format</span><span class="sxs-lookup"><span data-stu-id="5ddac-966">ux_device_class_storage_format</span></span>

<span data-ttu-id="5ddac-967">**Icono** ![Icono de formato de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-967">**Icon** ![Device Class Storage Format icon](./media/user-guide/usbx-events/image43.png)</span></span>

<span data-ttu-id="5ddac-968">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-968">**Description**</span></span>

<span data-ttu-id="5ddac-969">Este evento representa un evento de formato de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-969">This event represents a USBX Device Class Storage Format Event.</span></span>

<span data-ttu-id="5ddac-970">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-970">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-971">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-971">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-972">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-972">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-973">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-973">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-974">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-974">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-inquiry"></a><span data-ttu-id="5ddac-975">Consulta de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-975">Device Class Storage Inquiry</span></span> 

#### <a name="ux_device_class_storage_inquiry"></a><span data-ttu-id="5ddac-976">ux_device_class_storage_inquiry</span><span class="sxs-lookup"><span data-stu-id="5ddac-976">ux_device_class_storage_inquiry</span></span>

<span data-ttu-id="5ddac-977">**Icono** ![Icono de consulta de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-977">**Icon** ![Device Class Storage Inquiry icon](./media/user-guide/usbx-events/image44.png)</span></span>

<span data-ttu-id="5ddac-978">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-978">**Description**</span></span>

<span data-ttu-id="5ddac-979">Este evento representa un evento de consulta de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-979">This event represents a USBX Device Class Storage Inquiry Event.</span></span>

<span data-ttu-id="5ddac-980">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-980">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-981">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-981">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-982">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-982">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-983">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-983">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-984">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-984">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-select"></a><span data-ttu-id="5ddac-985">Selección de modo de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-985">Device Class Storage Mode Select</span></span>

#### <a name="ux_device_class_storage_mode_select"></a><span data-ttu-id="5ddac-986">ux_device_class_storage_mode_select</span><span class="sxs-lookup"><span data-stu-id="5ddac-986">ux_device_class_storage_mode_select</span></span>

<span data-ttu-id="5ddac-987">**Icono** ![Icono de selección de modo de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-987">**Icon** ![Device Class Storage Mode Select icon](./media/user-guide/usbx-events/image45.png)</span></span>

<span data-ttu-id="5ddac-988">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-988">**Description**</span></span>

<span data-ttu-id="5ddac-989">Este evento representa un evento de selección de modo de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-989">This event represents a USBX Device Class Storage Mode Select Event.</span></span>

<span data-ttu-id="5ddac-990">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-990">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-991">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-991">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-992">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-992">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-993">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-993">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-994">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-994">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-sense"></a><span data-ttu-id="5ddac-995">Detección del modo de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-995">Device Class Storage Mode Sense</span></span> 

#### <a name="ux_device_class_storage_mode_sense"></a><span data-ttu-id="5ddac-996">ux_device_class_storage_mode_sense</span><span class="sxs-lookup"><span data-stu-id="5ddac-996">ux_device_class_storage_mode_sense</span></span>

<span data-ttu-id="5ddac-997">**Icono** ![Icono de detección de modo de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-997">**Icon** ![Device Class Storage Mode Sense icon](./media/user-guide/usbx-events/image46.png)</span></span>

<span data-ttu-id="5ddac-998">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-998">**Description**</span></span>

<span data-ttu-id="5ddac-999">Este evento representa un evento de detección de modo de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-999">This event represents a USBX Device Class Storage Mode Sense Event.</span></span>

<span data-ttu-id="5ddac-1000">Campos de información</span><span class="sxs-lookup"><span data-stu-id="5ddac-1000">Information Fields</span></span> 

- <span data-ttu-id="5ddac-1001">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1001">nfo Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1002">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1002">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1003">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1003">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1004">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1004">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-prevent-allow-media-removal"></a><span data-ttu-id="5ddac-1005">Impedir/permitir extracción de soporte físico de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1005">Device Class Storage Prevent Allow Media Removal</span></span> 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a><span data-ttu-id="5ddac-1006">ux_device_class_storage_prevent_allow_media_removal</span><span class="sxs-lookup"><span data-stu-id="5ddac-1006">ux_device_class_storage_prevent_allow_media_removal</span></span>

<span data-ttu-id="5ddac-1007">**Icono** ![Icono de impedir/permitir extracción de soporte físico de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1007">**Icon** ![Device Class Storage Prevent Allow Media Removal icon](./media/user-guide/usbx-events/image47.png)</span></span>

<span data-ttu-id="5ddac-1008">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1008">**Description**</span></span>

<span data-ttu-id="5ddac-1009">Este evento representa un evento para impedir o permitir la extracción del soporte físico de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1009">This event represents a USBX Device Class Storage Prevent Allow Media Removal Event.</span></span>

<span data-ttu-id="5ddac-1010">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1010">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1011">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1011">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1012">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1012">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1013">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1013">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1014">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1014">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read"></a><span data-ttu-id="5ddac-1015">Lectura de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1015">Device Class Storage Read</span></span> 

#### <a name="ux_device_class_storage_read"></a><span data-ttu-id="5ddac-1016">ux_device_class_storage_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-1016">ux_device_class_storage_read</span></span>

<span data-ttu-id="5ddac-1017">**Icono** ![Icono de lectura de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1017">**Icon** ![Device Class Storage Read icon](./media/user-guide/usbx-events/image48.png)</span></span>

<span data-ttu-id="5ddac-1018">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1018">**Description**</span></span>

<span data-ttu-id="5ddac-1019">Este evento representa un evento de lectura de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1019">This event represents a USBX Device Class Storage Read Event.</span></span>

<span data-ttu-id="5ddac-1020">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1020">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1021">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1021">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1022">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1022">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1023">Campo de información 3: sector</span><span class="sxs-lookup"><span data-stu-id="5ddac-1023">Info Field 3: Sector.</span></span>
- <span data-ttu-id="5ddac-1024">Campo de información 4: sectores numéricos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1024">Info Field 4: Number sectors.</span></span>

### <a name="device-class-storage-read-capacity"></a><span data-ttu-id="5ddac-1025">Lectura de capacidad de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1025">Device Class Storage Read Capacity</span></span> 

#### <a name="ux_device_class_storage_read_capacity"></a><span data-ttu-id="5ddac-1026">ux_device_class_storage_read_capacity</span><span class="sxs-lookup"><span data-stu-id="5ddac-1026">ux_device_class_storage_read_capacity</span></span>

<span data-ttu-id="5ddac-1027">**Icono** ![Icono de lectura de capacidad de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1027">**Icon** ![Device Class Storage Read Capacity icon](./media/user-guide/usbx-events/image49.png)</span></span>

<span data-ttu-id="5ddac-1028">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1028">**Description**</span></span>

<span data-ttu-id="5ddac-1029">Este evento representa un evento de lectura de capacidad de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1029">This event represents a USBX Device Class Storage Read Capacity Event.</span></span>

<span data-ttu-id="5ddac-1030">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1030">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1031">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1031">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1032">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1032">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1033">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1033">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1034">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1034">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-format-capacity"></a><span data-ttu-id="5ddac-1035">Lectura de capacidad de formato de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1035">Device Class Storage Read Format Capacity</span></span> 

#### <a name="ux_device_class_storage_read_format_capacity"></a><span data-ttu-id="5ddac-1036">ux_device_class_storage_read_format_capacity</span><span class="sxs-lookup"><span data-stu-id="5ddac-1036">ux_device_class_storage_read_format_capacity</span></span>

<span data-ttu-id="5ddac-1037">**Icono** ![Icono de lectura de capacidad de formato de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1037">**Icon** ![Device Class Storage Read Format Capacity icon](./media/user-guide/usbx-events/image50.png)</span></span>

<span data-ttu-id="5ddac-1038">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1038">**Description**</span></span>

<span data-ttu-id="5ddac-1039">Este evento representa un evento de lectura de capacidad de formato de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1039">This event represents a USBX Device Class Storage Read Format Capacity Event.</span></span>

<span data-ttu-id="5ddac-1040">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1040">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1041">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1041">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1042">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1042">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1043">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1043">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1044">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1044">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-toc"></a><span data-ttu-id="5ddac-1045">Lectura de tabla de contenido de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1045">Device Class Storage Read TOC</span></span> 

#### <a name="ux_device_class_storage_read_toc"></a><span data-ttu-id="5ddac-1046">ux_device_class_storage_read_toc</span><span class="sxs-lookup"><span data-stu-id="5ddac-1046">ux_device_class_storage_read_toc</span></span>

<span data-ttu-id="5ddac-1047">**Icono** ![Icono de lectura de tabla de contenido de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1047">**Icon** ![Device Class Storage Read TOC icon](./media/user-guide/usbx-events/image51.png)</span></span>

<span data-ttu-id="5ddac-1048">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1048">**Description**</span></span>

<span data-ttu-id="5ddac-1049">Este evento representa un evento de lectura de tabla de contenido de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1049">This event represents a USBX Device Class Storage Read TOC Event.</span></span>

<span data-ttu-id="5ddac-1050">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1050">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1051">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1051">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1052">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1052">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1053">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1053">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1054">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1054">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-request-sense"></a><span data-ttu-id="5ddac-1055">Detección de solicitud de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1055">Device Class Storage Request Sense</span></span> 

#### <a name="ux_device_class_storage_request_sense"></a><span data-ttu-id="5ddac-1056">ux_device_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="5ddac-1056">ux_device_class_storage_request_sense</span></span>

<span data-ttu-id="5ddac-1057">**Icono** ![Icono de detección de solicitud de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1057">**Icon** ![Device Class Storage Request Sense icon](./media/user-guide/usbx-events/image52.png)</span></span>

<span data-ttu-id="5ddac-1058">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1058">**Description**</span></span>

<span data-ttu-id="5ddac-1059">Este evento representa un evento de detección de solicitud de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1059">This event represents a USBX Device Class Storage Request Sense Event.</span></span>

<span data-ttu-id="5ddac-1060">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1060">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1061">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1061">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1062">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1062">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1063">Campo de información 3: clave de detección</span><span class="sxs-lookup"><span data-stu-id="5ddac-1063">Info Field 3: Sense key.</span></span>
- <span data-ttu-id="5ddac-1064">Campo de información 4: código</span><span class="sxs-lookup"><span data-stu-id="5ddac-1064">Info Field 4: Code.</span></span>

### <a name="device-class-storage-start-stop"></a><span data-ttu-id="5ddac-1065">Inicio/parada de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1065">Device Class Storage Start Stop</span></span> 

#### <a name="ux_device_class_storage_start_stop"></a><span data-ttu-id="5ddac-1066">ux_device_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="5ddac-1066">ux_device_class_storage_start_stop</span></span>

<span data-ttu-id="5ddac-1067">**Icono** ![Icono de inicio/parada de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1067">**Icon** ![Device Class Storage Start Stop icon](./media/user-guide/usbx-events/image53.png)</span></span>

<span data-ttu-id="5ddac-1068">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1068">**Description**</span></span>

<span data-ttu-id="5ddac-1069">Este evento representa un evento de inicio/parada de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1069">This event represents a USBX Device Class Storage Start Stop Event.</span></span>

<span data-ttu-id="5ddac-1070">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1070">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1071">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1071">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1072">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1072">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1073">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1073">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1074">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1074">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-test-ready"></a><span data-ttu-id="5ddac-1075">Prueba de unidad preparada de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1075">Device Class Storage Test Ready</span></span> 

#### <a name="ux_device_class_storage_test_ready"></a><span data-ttu-id="5ddac-1076">ux_device_class_storage_test_ready</span><span class="sxs-lookup"><span data-stu-id="5ddac-1076">ux_device_class_storage_test_ready</span></span>

<span data-ttu-id="5ddac-1077">**Icono** ![Icono de prueba de unidad preparada de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1077">**Icon** ![Device Class Storage Test Ready icon](./media/user-guide/usbx-events/image54.png)</span></span>

<span data-ttu-id="5ddac-1078">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1078">**Description**</span></span>

<span data-ttu-id="5ddac-1079">Este evento representa un evento de prueba de unidad preparada de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1079">This event represents a USBX Device Class Storage Test Ready Event.</span></span>

<span data-ttu-id="5ddac-1080">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1080">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1081">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1081">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1082">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1082">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1083">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1083">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1084">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1084">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-verify"></a><span data-ttu-id="5ddac-1085">Comprobación de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1085">Device Class Storage Verify</span></span> 

#### <a name="ux_device_class_storage_verify"></a><span data-ttu-id="5ddac-1086">ux_device_class_storage_verify</span><span class="sxs-lookup"><span data-stu-id="5ddac-1086">ux_device_class_storage_verify</span></span>

<span data-ttu-id="5ddac-1087">**Icono** ![Icono de comprobación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1087">**Icon** ![Device Class Storage Verify icon](./media/user-guide/usbx-events/image55.png)</span></span>

<span data-ttu-id="5ddac-1088">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1088">**Description**</span></span>

<span data-ttu-id="5ddac-1089">Este evento representa un evento de comprobación de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1089">This event represents a USBX Device Class Storage Verify Event.</span></span>

<span data-ttu-id="5ddac-1090">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1090">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1091">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1091">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1092">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1092">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1093">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1093">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1094">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1094">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-write"></a><span data-ttu-id="5ddac-1095">Escritura de clase STORAGE de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1095">Device Class Storage Write</span></span> 

#### <a name="ux_device_class_storage_write"></a><span data-ttu-id="5ddac-1096">ux_device_class_storage_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-1096">ux_device_class_storage_write</span></span>

<span data-ttu-id="5ddac-1097">**Icono** ![Icono de escritura de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1097">**Icon** ![Device Class Storage Write icon](./media/user-guide/usbx-events/image56.png)</span></span>

<span data-ttu-id="5ddac-1098">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1098">**Description**</span></span>

<span data-ttu-id="5ddac-1099">Este evento representa un evento de escritura de la clase STORAGE del dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1099">This event represents a USBX Device Class Storage Write Event.</span></span>

<span data-ttu-id="5ddac-1100">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1100">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1101">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1101">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1102">Campo de información 2: LUN</span><span class="sxs-lookup"><span data-stu-id="5ddac-1102">Info Field 2: Lun.</span></span>
- <span data-ttu-id="5ddac-1103">Campo de información 3: sector</span><span class="sxs-lookup"><span data-stu-id="5ddac-1103">Info Field 3: Sector.</span></span>
- <span data-ttu-id="5ddac-1104">Campo de información 4: sectores numéricos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1104">Info Field 4: Number sectors.</span></span>

### <a name="device-stack-alternate-setting-get"></a><span data-ttu-id="5ddac-1105">Obtención de configuración alternativa de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1105">Device Stack Alternate Setting Get</span></span> 

#### <a name="ux_device_class_alternate_setting_get"></a><span data-ttu-id="5ddac-1106">ux_device_class_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1106">ux_device_class_alternate_setting_get</span></span>

<span data-ttu-id="5ddac-1107">**Icono** ![Icono de obtención de configuración alternativa de pila de dispositivos](./media/user-guide/usbx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1107">**Icon** ![Device Stack Alternate Setting Get icon](./media/user-guide/usbx-events/image57.png)</span></span>

<span data-ttu-id="5ddac-1108">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1108">**Description**</span></span>

<span data-ttu-id="5ddac-1109">Este evento representa un evento de obtención de configuración alternativa de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1109">This event represents a USBX Device Stack Alternate Setting Get Event.</span></span>

<span data-ttu-id="5ddac-1110">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1110">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1111">Campo de información 1: valor de la interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-1111">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="5ddac-1112">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1112">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1113">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1113">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1114">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1114">Info Field 4: Not used.</span></span>

### <a name="device-stack-alternate-setting-set"></a><span data-ttu-id="5ddac-1115">Establecimiento de configuración alternativa de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1115">Device Stack Alternate Setting Set</span></span> 

#### <a name="ux_device_class_alternate_setting_set"></a><span data-ttu-id="5ddac-1116">ux_device_class_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-1116">ux_device_class_alternate_setting_set</span></span>

<span data-ttu-id="5ddac-1117">**Icono** ![Icono de establecimiento de configuración alternativa de pila de dispositivos](./media/user-guide/usbx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1117">**Icon** ![Device Stack Alternate Setting Set icon](./media/user-guide/usbx-events/image58.png)</span></span>

<span data-ttu-id="5ddac-1118">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1118">**Description**</span></span>

<span data-ttu-id="5ddac-1119">Este evento representa un evento de establecimiento de configuración alternativa de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1119">This event represents a USBX Device Stack Alternate Setting Set Event.</span></span>

<span data-ttu-id="5ddac-1120">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1120">**Information Fields**</span></span>
- <span data-ttu-id="5ddac-1121">Campo de información 1: valor de la interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-1121">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="5ddac-1122">Campo de información 2: valor de configuración alternativo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1122">Info Field 2: Alternate setting value.</span></span>
- <span data-ttu-id="5ddac-1123">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1123">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1124">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1124">Info Field 4: Not used.</span></span>

### <a name="device-stack-class-register"></a><span data-ttu-id="5ddac-1125">Registro de clase de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1125">Device Stack Class Register</span></span> 

#### <a name="ux_device_stack_class_register"></a><span data-ttu-id="5ddac-1126">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="5ddac-1126">ux_device_stack_class_register</span></span>

<span data-ttu-id="5ddac-1127">**Icono** ![Icono de registro de clase de pila de dispositivos](./media/user-guide/usbx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1127">**Icon** ![Device Stack Class Register icon](./media/user-guide/usbx-events/image59.png)</span></span>

<span data-ttu-id="5ddac-1128">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1128">**Description**</span></span>

<span data-ttu-id="5ddac-1129">Este evento representa un evento de registro de la clase de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1129">This event represents a USBX Device Stack Class Register Event.</span></span>

<span data-ttu-id="5ddac-1130">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1130">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1131">Campo de información 1: nombre de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1131">Info Field 1: Class name.</span></span>
- <span data-ttu-id="5ddac-1132">Campo de información 2: número de interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-1132">Info Field 2: Interface number.</span></span>
- <span data-ttu-id="5ddac-1133">Campo de información 3: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-1133">Info Field 3: Parameter.</span></span>
- <span data-ttu-id="5ddac-1134">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1134">Info Field 4: Not used.</span></span>

### <a name="device-stack-clear-feature"></a><span data-ttu-id="5ddac-1135">Borrado de característica de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1135">Device Stack Clear Feature</span></span> 

#### <a name="ux_device_stack_clear_feature"></a><span data-ttu-id="5ddac-1136">ux_device_stack_clear_feature</span><span class="sxs-lookup"><span data-stu-id="5ddac-1136">ux_device_stack_clear_feature</span></span>

<span data-ttu-id="5ddac-1137">**Icono** ![Icono de borrado de característica de pila de dispositivos](./media/user-guide/usbx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1137">**Icon** ![Device Stack Clear Feature icon](./media/user-guide/usbx-events/image60.png)</span></span>

<span data-ttu-id="5ddac-1138">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1138">**Description**</span></span>

<span data-ttu-id="5ddac-1139">Este evento representa un evento de borrado de característica de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1139">This event represents a USBX Device Stack Clear Feature Event.</span></span>

<span data-ttu-id="5ddac-1140">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1140">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1141">Campo de información 1: tipo de solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-1141">Info Field 1: Request type.</span></span>
- <span data-ttu-id="5ddac-1142">Campo de información 2: valor de la solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-1142">Info Field 2: Request value.</span></span> <span data-ttu-id="5ddac-1143">Campo de información 3: índice de la solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-1143">Info Field 3: Request index.</span></span>
- <span data-ttu-id="5ddac-1144">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1144">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-get"></a><span data-ttu-id="5ddac-1145">Obtención de configuración de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1145">Device Stack Configuration Get</span></span> 

#### <a name="ux_device_stack_configuration_get-t"></a><span data-ttu-id="5ddac-1146">ux_device_stack_configuration_get t</span><span class="sxs-lookup"><span data-stu-id="5ddac-1146">ux_device_stack_configuration_get t</span></span>

<span data-ttu-id="5ddac-1147">**Icono** ![Icono de obtención de configuración de pila de dispositivos](./media/user-guide/usbx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1147">**Icon** ![Device Stack Configuration Get icon](./media/user-guide/usbx-events/image61.png)</span></span>

<span data-ttu-id="5ddac-1148">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1148">**Description**</span></span>

<span data-ttu-id="5ddac-1149">Este evento representa un evento de obtención de configuración de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1149">This event represents a USBX Device Stack Configuration Get Event.</span></span>

<span data-ttu-id="5ddac-1150">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1150">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1151">Campo de información 1: valor de configuración</span><span class="sxs-lookup"><span data-stu-id="5ddac-1151">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="5ddac-1152">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1152">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1153">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1153">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1154">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1154">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-set"></a><span data-ttu-id="5ddac-1155">Establecimiento de configuración de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1155">Device Stack Configuration Set</span></span> 

#### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="5ddac-1156">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-1156">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="5ddac-1157">**Icono** ![Icono de establecimiento de configuración de pila de dispositivos](./media/user-guide/usbx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1157">**Icon** ![Device Stack Configuration Set icon](./media/user-guide/usbx-events/image62.png)</span></span>

<span data-ttu-id="5ddac-1158">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1158">**Description**</span></span>

<span data-ttu-id="5ddac-1159">Este evento representa un evento de establecimiento de configuración de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1159">This event represents a USBX Device Stack Configuration Set Event.</span></span>

<span data-ttu-id="5ddac-1160">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1160">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1161">Campo de información 1: valor de configuración</span><span class="sxs-lookup"><span data-stu-id="5ddac-1161">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="5ddac-1162">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1162">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1163">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1163">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1164">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1164">Info Field 4: Not used.</span></span>

### <a name="device-stack-connect"></a><span data-ttu-id="5ddac-1165">Conexión de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1165">Device Stack Connect</span></span> 

#### <a name="ux_device_stack_connect"></a><span data-ttu-id="5ddac-1166">ux_device_stack_connect</span><span class="sxs-lookup"><span data-stu-id="5ddac-1166">ux_device_stack_connect</span></span>

<span data-ttu-id="5ddac-1167">**Icono** ![Icono de conexión de pila de dispositivos](./media/user-guide/usbx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1167">**Icon** ![Device Stack Connect icon](./media/user-guide/usbx-events/image63.png)</span></span>

<span data-ttu-id="5ddac-1168">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1168">**Description**</span></span>

<span data-ttu-id="5ddac-1169">Este evento representa un evento de envío de descriptor de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1169">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="5ddac-1170">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1170">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1171">Campo de información 1: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1171">Info Field 1: Not used.</span></span>
- <span data-ttu-id="5ddac-1172">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1172">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1173">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1173">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1174">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1174">Info Field 4: Not used.</span></span>

### <a name="device-stack-descriptor-send"></a><span data-ttu-id="5ddac-1175">Envío de descriptor de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1175">Device Stack Descriptor Send</span></span> 

#### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="5ddac-1176">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-1176">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="5ddac-1177">**Icono** ![Icono de envío de descriptor de pila de dispositivos](./media/user-guide/usbx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1177">**Icon** ![Device Stack Descriptor Send icon](./media/user-guide/usbx-events/image64.png)</span></span>

<span data-ttu-id="5ddac-1178">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1178">**Description**</span></span>

<span data-ttu-id="5ddac-1179">Este evento representa un evento de envío de descriptor de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1179">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="5ddac-1180">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1180">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1181">Campo de información 1: tipo de descriptor</span><span class="sxs-lookup"><span data-stu-id="5ddac-1181">Info Field 1: Descriptor type.</span></span>
- <span data-ttu-id="5ddac-1182">Campo de información 2: índice de solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-1182">Info Field 2: Request index.</span></span>
- <span data-ttu-id="5ddac-1183">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1183">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1184">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1184">Info Field 4: Not used.</span></span>

### <a name="device-stack-disconnect"></a><span data-ttu-id="5ddac-1185">Desconexión de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1185">Device Stack Disconnect</span></span> 

#### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="5ddac-1186">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="5ddac-1186">ux_device_stack_disconnect</span></span>

<span data-ttu-id="5ddac-1187">**Icono** ![Icono de desconexión de pila de dispositivos](./media/user-guide/usbx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1187">**Icon** ![Device Stack Disconnect icon](./media/user-guide/usbx-events/image65.png)</span></span>

<span data-ttu-id="5ddac-1188">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1188">**Description**</span></span>

<span data-ttu-id="5ddac-1189">Este evento representa un evento de desconexión de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1189">This event represents a USBX Device Stack Disconnect Event.</span></span>

<span data-ttu-id="5ddac-1190">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1190">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1191">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1191">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-1192">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1192">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1193">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1193">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1194">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1194">Info Field 4: Not used.</span></span>

### <a name="device-stack-endpoint-stall"></a><span data-ttu-id="5ddac-1195">Detención de punto de conexión de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1195">Device Stack Endpoint Stall</span></span> 

#### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="5ddac-1196">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="5ddac-1196">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="5ddac-1197">**Icono** ![Icono de detención de punto de conexión de pila de dispositivos](./media/user-guide/usbx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1197">**Icon** ![Device Stack Endpoint Stall icon](./media/user-guide/usbx-events/image66.png)</span></span>

<span data-ttu-id="5ddac-1198">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1198">**Description**</span></span>

<span data-ttu-id="5ddac-1199">Este evento representa un evento de detención del punto de conexión de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1199">This event represents a USBX Device Stack Endpoint Stall Event.</span></span>

<span data-ttu-id="5ddac-1200">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1200">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1201">Campo de información 1: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-1201">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="5ddac-1202">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1202">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1203">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1203">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1204">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1204">Info Field 4: Not used.</span></span>

### <a name="device-stack-get-status"></a><span data-ttu-id="5ddac-1205">Obtención de estado de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1205">Device Stack Get Status</span></span> 

#### <a name="ux_device_stack_get_status"></a><span data-ttu-id="5ddac-1206">ux_device_stack_get_status</span><span class="sxs-lookup"><span data-stu-id="5ddac-1206">ux_device_stack_get_status</span></span>

<span data-ttu-id="5ddac-1207">**Icono** ![Icono de obtención de estado de pila de dispositivos](./media/user-guide/usbx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1207">**Icon** ![Device Stack Get Status icon](./media/user-guide/usbx-events/image67.png)</span></span>

<span data-ttu-id="5ddac-1208">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1208">**Description**</span></span>

<span data-ttu-id="5ddac-1209">Este evento representa un evento de obtención de estado de la pila de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1209">This event represents a USBX Device Stack Get Status Event.</span></span>

<span data-ttu-id="5ddac-1210">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1210">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1211">Campo de información 1: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1211">Info Field 1: Not used.</span></span>
- <span data-ttu-id="5ddac-1212">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1212">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1213">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1213">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1214">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1214">Info Field 4: Not used.</span></span>

### <a name="device-stack-host-wakeup"></a><span data-ttu-id="5ddac-1215">Reactivación de host de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1215">Device Stack Host Wakeup</span></span> 

#### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="5ddac-1216">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="5ddac-1216">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="5ddac-1217">**Icono** ![Icono de reactivación de host de pila de dispositivos](./media/user-guide/usbx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1217">**Icon** ![Device Stack Host Wakeup icon](./media/user-guide/usbx-events/image68.png)</span></span>

<span data-ttu-id="5ddac-1218">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1218">**Description**</span></span>

<span data-ttu-id="5ddac-1219">Este evento representa un evento de reactivación del host de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1219">This event represents a USBX Device Stack Host Wakeup Event.</span></span>

<span data-ttu-id="5ddac-1220">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1220">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1221">Campo de información 1: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1221">Info Field 1: Not used.</span></span>
- <span data-ttu-id="5ddac-1222">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1222">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1223">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1223">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1224">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1224">Info Field 4: Not used.</span></span>

### <a name="device-stack-initialize"></a><span data-ttu-id="5ddac-1225">Inicialización de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1225">Device Stack Initialize</span></span> 

#### <a name="ux_device_stack_initialize"></a><span data-ttu-id="5ddac-1226">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="5ddac-1226">ux_device_stack_initialize</span></span>

<span data-ttu-id="5ddac-1227">**Icono** ![Icono de inicialización de pila de dispositivos](./media/user-guide/usbx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1227">**Icon** ![Device Stack Initialize icon](./media/user-guide/usbx-events/image69.png)</span></span>

<span data-ttu-id="5ddac-1228">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1228">**Description**</span></span>

<span data-ttu-id="5ddac-1229">Este evento representa un evento de inicialización de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1229">This event represents a USBX Device Stack Initialize Event.</span></span>

<span data-ttu-id="5ddac-1230">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1230">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1231">Campo de información 1: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1231">Info Field 1: Not used.</span></span>
- <span data-ttu-id="5ddac-1232">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1232">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1233">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1233">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1234">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1234">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-delete"></a><span data-ttu-id="5ddac-1235">Eliminación de interfaz de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1235">Device Stack Interface Delete</span></span> 

#### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="5ddac-1236">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="5ddac-1236">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="5ddac-1237">**Icono** ![Icono de eliminación de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1237">**Icon** ![Device Stack Interface Delete icon](./media/user-guide/usbx-events/image70.png)</span></span>

<span data-ttu-id="5ddac-1238">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1238">**Description**</span></span>

<span data-ttu-id="5ddac-1239">Este evento representa un evento de eliminación de la interfaz de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1239">This event represents a USBX Device Stack Interface Delete Event.</span></span>

<span data-ttu-id="5ddac-1240">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1240">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1241">Campo de información 1: interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-1241">Info Field 1: Interface.</span></span>
- <span data-ttu-id="5ddac-1242">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1242">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1243">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1243">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1244">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1244">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-get"></a><span data-ttu-id="5ddac-1245">Obtención de interfaz de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1245">Device Stack Interface Get</span></span> 

#### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="5ddac-1246">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1246">ux_device_stack_interface_get</span></span>

<span data-ttu-id="5ddac-1247">**Icono** ![Icono de obtención de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1247">**Icon** ![Device Stack Interface Get icon](./media/user-guide/usbx-events/image71.png)</span></span>

<span data-ttu-id="5ddac-1248">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1248">**Description**</span></span>

<span data-ttu-id="5ddac-1249">Este evento representa un evento de obtención de la interfaz de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1249">This event represents a USBX Device Stack Interface Get Event.</span></span>

<span data-ttu-id="5ddac-1250">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1250">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1251">Campo de información 1: valor de la interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-1251">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="5ddac-1252">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1252">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1253">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1253">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1254">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1254">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-set"></a><span data-ttu-id="5ddac-1255">Establecimiento de interfaz de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1255">Device Stack Interface Set</span></span> 

#### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="5ddac-1256">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-1256">ux_device_stack_interface_set</span></span>

<span data-ttu-id="5ddac-1257">**Icono** ![Icono de establecimiento de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1257">**Icon** ![Device Stack Interface Set icon](./media/user-guide/usbx-events/image72.png)</span></span>

<span data-ttu-id="5ddac-1258">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1258">**Description**</span></span>

<span data-ttu-id="5ddac-1259">Este evento representa un evento de establecimiento de la interfaz de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1259">This event represents a USBX Device Stack Interface Set Event.</span></span>

<span data-ttu-id="5ddac-1260">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1260">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1261">Campo de información 1: valor de la solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-1261">Info Field 1: Request value.</span></span> <span data-ttu-id="5ddac-1262">Campo de información 2: índice de solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-1262">Info Field 2: Request index.</span></span>
- <span data-ttu-id="5ddac-1263">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1263">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1264">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1264">Info Field 4: Not used.</span></span>

### <a name="device-stack-set-feature"></a><span data-ttu-id="5ddac-1265">Establecimiento de característica de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1265">Device Stack Set Feature</span></span> 

#### <a name="ux_device_stack_set_feature"></a><span data-ttu-id="5ddac-1266">ux_device_stack_set_feature</span><span class="sxs-lookup"><span data-stu-id="5ddac-1266">ux_device_stack_set_feature</span></span>

<span data-ttu-id="5ddac-1267">**Icono** ![Icono de establecimiento de característica de pila de dispositivos](./media/user-guide/usbx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1267">**Icon** ![Device Stack Set Feature icon](./media/user-guide/usbx-events/image73.png)</span></span>

<span data-ttu-id="5ddac-1268">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1268">**Description**</span></span>

<span data-ttu-id="5ddac-1269">Este evento representa un evento de establecimiento de característica de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1269">This event represents a USBX Device Stack Set Feature Event.</span></span>

<span data-ttu-id="5ddac-1270">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1270">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1271">Campo de información 1: valor de la solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-1271">Info Field 1: Request value.</span></span> <span data-ttu-id="5ddac-1272">Campo de información 2: índice de solicitud</span><span class="sxs-lookup"><span data-stu-id="5ddac-1272">Info Field 2: Request index.</span></span>
- <span data-ttu-id="5ddac-1273">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1273">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1274">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1274">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-abort"></a><span data-ttu-id="5ddac-1275">Anulación de transferencia de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1275">Device Stack Transfer Abort</span></span> 

#### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="5ddac-1276">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="5ddac-1276">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="5ddac-1277">**Icono** ![Icono de anulación de transferencia de pila de dispositivos](./media/user-guide/usbx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1277">**Icon** ![Device Stack Transfer Abort icon](./media/user-guide/usbx-events/image74.png)</span></span>

<span data-ttu-id="5ddac-1278">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1278">**Description**</span></span>

<span data-ttu-id="5ddac-1279">Este evento representa un evento de anulación de transferencia de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1279">This event represents a USBX Device Stack Transfer Abort Event.</span></span>

<span data-ttu-id="5ddac-1280">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1280">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1281">Campo de información 1: solicitud de transferencia</span><span class="sxs-lookup"><span data-stu-id="5ddac-1281">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="5ddac-1282">Campo de información 2: código de finalización</span><span class="sxs-lookup"><span data-stu-id="5ddac-1282">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="5ddac-1283">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1283">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1284">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1284">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-all-request-abort"></a><span data-ttu-id="5ddac-1285">Anulación de todas las solicitudes de transferencia de la pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1285">Device Stack Transfer All Request Abort</span></span> 

#### <a name="ux_device_stack_transfer_all_request_abort"></a><span data-ttu-id="5ddac-1286">ux_device_stack_transfer_all_request_abort</span><span class="sxs-lookup"><span data-stu-id="5ddac-1286">ux_device_stack_transfer_all_request_abort</span></span>

<span data-ttu-id="5ddac-1287">**Icono** ![Icono de anulación de todas las solicitudes de transferencia de la pila de dispositivos](./media/user-guide/usbx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1287">**Icon** ![Device Stack Transfer All Request Abort icon](./media/user-guide/usbx-events/image75.png)</span></span>

<span data-ttu-id="5ddac-1288">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1288">**Description**</span></span>

<span data-ttu-id="5ddac-1289">Este evento representa un evento de anulación de todas las solicitudes de transferencia de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1289">This event represents a USBX Device Stack Transfer All Request Abort Event.</span></span>

<span data-ttu-id="5ddac-1290">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1290">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1291">Campo de información 1: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-1291">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="5ddac-1292">Campo de información 2: código de finalización</span><span class="sxs-lookup"><span data-stu-id="5ddac-1292">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="5ddac-1293">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1293">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1294">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1294">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-request"></a><span data-ttu-id="5ddac-1295">Solicitud de transferencia de pila de dispositivos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1295">Device Stack Transfer Request</span></span> 

#### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="5ddac-1296">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="5ddac-1296">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="5ddac-1297">**Icono** ![Icono de solicitud de transferencia de pila de dispositivos](./media/user-guide/usbx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1297">**Icon** ![Device Stack Transfer Request icon](./media/user-guide/usbx-events/image76.png)</span></span>

<span data-ttu-id="5ddac-1298">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1298">**Description**</span></span>

<span data-ttu-id="5ddac-1299">Este evento representa un evento de solicitud de transferencia de la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1299">This event represents a USBX Device Stack Transfer Request Event.</span></span>

<span data-ttu-id="5ddac-1300">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1300">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1301">Campo de información 1: solicitud de transferencia</span><span class="sxs-lookup"><span data-stu-id="5ddac-1301">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="5ddac-1302">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1302">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1303">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1303">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1304">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1304">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-activate"></a><span data-ttu-id="5ddac-1305">Activación de clase ASIX de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1305">Host Class Asix Activate</span></span> 

#### <a name="ux_host_class_asix_activate"></a><span data-ttu-id="5ddac-1306">ux_host_class_asix_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1306">ux_host_class_asix_activate</span></span>

<span data-ttu-id="5ddac-1307">**Icono** ![Icono de activación de clase ASIX de host](./media/user-guide/usbx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1307">**Icon** ![Host Class Asix Activate icon](./media/user-guide/usbx-events/image77.png)</span></span>

<span data-ttu-id="5ddac-1308">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1308">**Description**</span></span>

<span data-ttu-id="5ddac-1309">Este evento representa una activación de la clase ASIX del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1309">This event represents a USBX Host Class Asix Activate.</span></span>

<span data-ttu-id="5ddac-1310">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1310">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1311">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1311">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1312">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1312">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1313">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1313">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1314">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1314">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-deactivate"></a><span data-ttu-id="5ddac-1315">Desactivación de clase ASIX de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1315">Host Class Asix Deactivate</span></span> 

#### <a name="ux_host_class_asix_deactivate"></a><span data-ttu-id="5ddac-1316">ux_host_class_asix_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1316">ux_host_class_asix_deactivate</span></span>

<span data-ttu-id="5ddac-1317">**Icono** ![Icono de desactivación de clase ASIX de host](./media/user-guide/usbx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1317">**Icon** ![Host Class Asix Deactivate icon](./media/user-guide/usbx-events/image78.png)</span></span>

<span data-ttu-id="5ddac-1318">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1318">**Description**</span></span>

<span data-ttu-id="5ddac-1319">Este evento representa un evento de desactivación de la clase ASIX del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1319">This event represents a USBX Host Class Asix Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1320">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1320">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1321">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1321">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1322">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1322">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1323">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1323">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1324">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1324">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-interrupt-notification"></a><span data-ttu-id="5ddac-1325">Notificación de interrupción de clase ASIX de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1325">Host Class Asix Interrupt Notification</span></span> 

#### <a name="ux_host_class_asix_interrupt_notification"></a><span data-ttu-id="5ddac-1326">ux_host_class_asix_interrupt_notification</span><span class="sxs-lookup"><span data-stu-id="5ddac-1326">ux_host_class_asix_interrupt_notification</span></span>

<span data-ttu-id="5ddac-1327">**Icono** ![Icono de notificación de interrupción de clase ASIX de host](./media/user-guide/usbx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1327">**Icon** ![Host Class Asix Interrupt Notification icon](./media/user-guide/usbx-events/image79.png)</span></span>

<span data-ttu-id="5ddac-1328">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1328">**Description**</span></span>

<span data-ttu-id="5ddac-1329">Este evento representa un evento de notificación de interrupción de la clase ASIX del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1329">This event represents a USBX Host Class Asix Interrupt Notification Event.</span></span>

<span data-ttu-id="5ddac-1330">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1330">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1331">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1331">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-1332">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1332">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1333">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1333">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1334">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1334">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-read"></a><span data-ttu-id="5ddac-1335">Lectura de clase ASIX de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1335">Host Class Asix Read</span></span> 

#### <a name="ux_host_class_asix_read"></a><span data-ttu-id="5ddac-1336">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-1336">ux_host_class_asix_read</span></span>

<span data-ttu-id="5ddac-1337">**Icono** ![Icono de lectura de clase ASIX de host](./media/user-guide/usbx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1337">**Icon** ![Host Class Asix Read icon](./media/user-guide/usbx-events/image80.png)</span></span>

<span data-ttu-id="5ddac-1338">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1338">**Description**</span></span>

<span data-ttu-id="5ddac-1339">Este evento representa un evento de lectura de la clase ASIX del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1339">This event represents a USBX Host Class Asix Read Event.</span></span>

<span data-ttu-id="5ddac-1340">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1340">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1341">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1341">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1342">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1342">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-1343">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-1343">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-1344">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1344">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-write"></a><span data-ttu-id="5ddac-1345">Escritura de clase ASIX de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1345">Host Class Asix Write</span></span> 

#### <a name="ux_host_class_asix_write"></a><span data-ttu-id="5ddac-1346">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-1346">ux_host_class_asix_write</span></span>

<span data-ttu-id="5ddac-1347">**Icono** ![Icono de escritura de clase ASIX de host](./media/user-guide/usbx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1347">**Icon** ![Host Class Asix Write icon](./media/user-guide/usbx-events/image81.png)</span></span>

<span data-ttu-id="5ddac-1348">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1348">**Description**</span></span>

<span data-ttu-id="5ddac-1349">Este evento representa un evento de escritura de la clase ASIX del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1349">This event represents a USBX Host Class Asix Write Event.</span></span>

<span data-ttu-id="5ddac-1350">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1350">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1351">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1351">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1352">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1352">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-1353">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-1353">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-1354">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1354">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-activate"></a><span data-ttu-id="5ddac-1355">Activación de clase AUDIO de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1355">Host Class Audio Activate</span></span> 

#### <a name="ux_host_class_audio_activate"></a><span data-ttu-id="5ddac-1356">ux_host_class_audio_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1356">ux_host_class_audio_activate</span></span>

<span data-ttu-id="5ddac-1357">**Icono** ![Icono de activación de clase AUDIO de host](./media/user-guide/usbx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1357">**Icon** ![Host Class Audio Activate icon](./media/user-guide/usbx-events/image82.png)</span></span>

<span data-ttu-id="5ddac-1358">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1358">**Description**</span></span>

<span data-ttu-id="5ddac-1359">Este evento representa un evento de activación de la clase AUDIO del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1359">This event represents a USBX Host Class Audio Activate Event.</span></span>

<span data-ttu-id="5ddac-1360">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1360">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1361">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1361">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1362">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1362">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1363">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1363">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1364">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1364">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-get"></a><span data-ttu-id="5ddac-1365">Obtención de valor de control de clase AUDIO de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1365">Host Class Audio Control Value Get</span></span> 

#### <a name="ux_host_class_audio_control_value_get"></a><span data-ttu-id="5ddac-1366">ux_host_class_audio_control_value_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1366">ux_host_class_audio_control_value_get</span></span>

<span data-ttu-id="5ddac-1367">**Icono** ![Icono de obtención de valor de control de clase AUDIO de host](./media/user-guide/usbx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1367">**Icon** ![Host Class Audio Control Value Get icon](./media/user-guide/usbx-events/image83.png)</span></span>

<span data-ttu-id="5ddac-1368">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1368">**Description**</span></span>

<span data-ttu-id="5ddac-1369">Este evento representa un evento de obtención del valor de control de la clase AUDIO del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1369">This event represents a USBX Host Class Audio Control Value Get Event.</span></span>

<span data-ttu-id="5ddac-1370">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1370">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1371">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1371">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1372">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1372">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1373">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1373">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1374">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1374">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-set"></a><span data-ttu-id="5ddac-1375">Establecimiento de valor de control de clase AUDIO de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1375">Host Class Audio Control Value Set</span></span> 

#### <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="5ddac-1376">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-1376">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="5ddac-1377">**Icono** ![Icono de establecimiento de valor de control de clase AUDIO de host](./media/user-guide/usbx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1377">**Icon** ![Host Class Audio Control Value Set icon](./media/user-guide/usbx-events/image84.png)</span></span>

<span data-ttu-id="5ddac-1378">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1378">**Description**</span></span>

<span data-ttu-id="5ddac-1379">Este evento representa un evento interno de procesamiento diferido del controlador de E/S de NetX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1379">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="5ddac-1380">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1380">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1381">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1381">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1382">Campo de información 2: control de audio</span><span class="sxs-lookup"><span data-stu-id="5ddac-1382">Info Field 2: Audio control.</span></span>
- <span data-ttu-id="5ddac-1383">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1383">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1384">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1384">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-deactivate"></a><span data-ttu-id="5ddac-1385">Desactivación de clase AUDIO de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1385">Host Class Audio Deactivate</span></span> 

#### <a name="ux_host_class_audio_deactivate"></a><span data-ttu-id="5ddac-1386">ux_host_class_audio_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1386">ux_host_class_audio_deactivate</span></span>

<span data-ttu-id="5ddac-1387">**Icono** ![Icono de desactivación de clase AUDIO de host](./media/user-guide/usbx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1387">**Icon** ![Host Class Audio Deactivate icon](./media/user-guide/usbx-events/image85.png)</span></span>

<span data-ttu-id="5ddac-1388">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1388">**Description**</span></span>

<span data-ttu-id="5ddac-1389">Este evento representa un evento de desactivación de la clase AUDIO del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1389">This event represents a USBX Host Class Audio Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1390">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1390">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1391">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1391">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1392">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1392">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1393">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1393">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1394">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1394">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-read"></a><span data-ttu-id="5ddac-1395">Lectura de clase AUDIO de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1395">Host Class Audio Read</span></span> 

#### <a name="ux_host_class_audio_read"></a><span data-ttu-id="5ddac-1396">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-1396">ux_host_class_audio_read</span></span>

<span data-ttu-id="5ddac-1397">**Icono** ![Icono de lectura de clase AUDIO de host](./media/user-guide/usbx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1397">**Icon** ![Host Class Audio Read icon](./media/user-guide/usbx-events/image86.png)</span></span>

<span data-ttu-id="5ddac-1398">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1398">**Description**</span></span>

<span data-ttu-id="5ddac-1399">Este evento representa un evento de lectura de la clase AUDIO del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1399">This event represents a USBX Host Class Audio Read Event.</span></span>

- <span data-ttu-id="5ddac-1400">Campos de información</span><span class="sxs-lookup"><span data-stu-id="5ddac-1400">Information Fields</span></span> 
- <span data-ttu-id="5ddac-1401">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1401">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1402">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1402">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-1403">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-1403">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-1404">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1404">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-get"></a><span data-ttu-id="5ddac-1405">Obtención de muestreo de streaming de clase AUDIO de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1405">Host Class Audio Streaming Sampling Get</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="5ddac-1406">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1406">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="5ddac-1407">**Icono** ![Icono de obtención de muestreo de streaming de clase AUDIO de host](./media/user-guide/usbx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1407">**Icon** ![Host Class Audio Streaming Sampling Get icon](./media/user-guide/usbx-events/image87.png)</span></span>

<span data-ttu-id="5ddac-1408">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1408">**Description**</span></span>

<span data-ttu-id="5ddac-1409">Este evento representa un evento de obtención de muestreo de streaming de la clase AUDIO del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1409">This event represents a USBX Host Class Audio Streaming Sampling Get Event.</span></span>

<span data-ttu-id="5ddac-1410">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1410">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1411">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1411">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1412">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1412">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1413">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1413">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1414">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1414">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-set"></a><span data-ttu-id="5ddac-1415">Establecimiento de muestreo de streaming de clase AUDIO de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1415">Host Class Audio Streaming Sampling Set</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="5ddac-1416">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-1416">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="5ddac-1417">**Icono** ![Icono de establecimiento de muestreo de streaming de clase AUDIO de host](./media/user-guide/usbx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1417">**Icon** ![Host Class Audio Streaming Sampling Set icon](./media/user-guide/usbx-events/image88.png)</span></span>

<span data-ttu-id="5ddac-1418">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1418">**Description**</span></span>

<span data-ttu-id="5ddac-1419">Este evento representa un evento de establecimiento de muestreo de streaming de la clase AUDIO del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1419">This event represents a USBX Host Class Audio Streaming Sampling Set Event.</span></span>

<span data-ttu-id="5ddac-1420">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1420">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1421">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1421">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1422">Campo de información 2: muestreo de audio</span><span class="sxs-lookup"><span data-stu-id="5ddac-1422">Info Field 2: Audio Sampling.</span></span>
- <span data-ttu-id="5ddac-1423">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1423">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1424">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1424">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-write"></a><span data-ttu-id="5ddac-1425">Escritura de clase AUDIO de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1425">Host Class Audio Write</span></span> 

#### <a name="ux_host_class_audio_write"></a><span data-ttu-id="5ddac-1426">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-1426">ux_host_class_audio_write</span></span>

<span data-ttu-id="5ddac-1427">**Icono** ![Icono de escritura de clase AUDIO de host](./media/user-guide/usbx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1427">**Icon** ![Host Class Audio Write icon](./media/user-guide/usbx-events/image89.png)</span></span>

<span data-ttu-id="5ddac-1428">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1428">**Description**</span></span>

<span data-ttu-id="5ddac-1429">Este evento representa un evento de escritura de la clase AUDIO del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1429">This event represents a USBX Host Class Audio Write Event.</span></span>

<span data-ttu-id="5ddac-1430">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1430">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1431">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1431">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1432">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1432">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-1433">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-1433">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-1434">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1434">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-activate"></a><span data-ttu-id="5ddac-1435">Activación de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1435">Host Class Cdc Acm Activate</span></span> 

#### <a name="ux_host_class_cdc_acm_activate"></a><span data-ttu-id="5ddac-1436">ux_host_class_cdc_acm_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1436">ux_host_class_cdc_acm_activate</span></span>

<span data-ttu-id="5ddac-1437">**Icono** ![Icono de activación de clase C D C A C M de host](./media/user-guide/usbx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1437">**Icon** ![Host Class C D C A C M Activate icon](./media/user-guide/usbx-events/image90.png)</span></span>

<span data-ttu-id="5ddac-1438">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1438">**Description**</span></span>

<span data-ttu-id="5ddac-1439">Este evento representa un evento de activación de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1439">This event represents a USBX Host Class Cdc Acm Activate Event.</span></span>

<span data-ttu-id="5ddac-1440">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1440">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1441">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1441">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1442">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1442">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1443">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1443">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1444">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1444">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-deactivate"></a><span data-ttu-id="5ddac-1445">Desactivación de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1445">Host Class Cdc Acm Deactivate</span></span> 

#### <a name="ux_host_class_cdc_acm_deactivate"></a><span data-ttu-id="5ddac-1446">ux_host_class_cdc_acm_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1446">ux_host_class_cdc_acm_deactivate</span></span>

<span data-ttu-id="5ddac-1447">**Icono** ![Icono de desactivación de clase C D C A C M de host](./media/user-guide/usbx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1447">**Icon** ![Host Class C D C A C M Deactivate icon](./media/user-guide/usbx-events/image91.png)</span></span>

<span data-ttu-id="5ddac-1448">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1448">**Description**</span></span>

<span data-ttu-id="5ddac-1449">Este evento representa un evento de desactivación de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1449">This event represents a USBX Host Class Cdc Acm Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1450">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1450">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1451">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1451">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1452">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1452">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1453">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1453">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1454">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1454">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a><span data-ttu-id="5ddac-1455">Función IOCTL de anulación de canalización de entrada de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1455">Host Class Cdc Acm Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a><span data-ttu-id="5ddac-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="5ddac-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="5ddac-1457">**Icono** ![Icono de función I O C T L de anulación de canalización de entrada de clase C D C A C M de host](./media/user-guide/usbx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1457">**Icon** ![Host Class C D C A C M I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image92.png)</span></span>

<span data-ttu-id="5ddac-1458">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1458">**Description**</span></span>

<span data-ttu-id="5ddac-1459">Este evento representa un evento de una función IOCTL de anulación de canalización de entrada de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1459">This event represents a USBX Host Class Cdc Acm Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="5ddac-1460">Campos de información</span><span class="sxs-lookup"><span data-stu-id="5ddac-1460">Information Fields</span></span> 

- <span data-ttu-id="5ddac-1461">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1461">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1462">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-1462">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-1463">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1463">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1464">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1464">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a><span data-ttu-id="5ddac-1465">Función IOCTL de anulación de canalización de salida de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1465">Host Class Cdc Acm Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a><span data-ttu-id="5ddac-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="5ddac-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span></span>

<span data-ttu-id="5ddac-1467">**Icono** [Icono de función I O C T L de anulación de canalización de salida de clase C D C A C M de host](./media/user-guide/usbx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1467">**Icon** ![[Host Class C D C A C M I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image93.png)</span></span>

<span data-ttu-id="5ddac-1468">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1468">**Description**</span></span>

<span data-ttu-id="5ddac-1469">Este evento representa un evento de una función IOCTL de anulación de canalización de salida de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1469">This event represents a USBX Host Class Cdc Acm Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="5ddac-1470">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1470">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1471">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1471">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1472">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-1472">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-1473">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1473">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1474">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1474">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a><span data-ttu-id="5ddac-1475">Función IOCTL de obtención de estado de dispositivo de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1475">Host Class Cdc Acm Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a><span data-ttu-id="5ddac-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="5ddac-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span></span>

<span data-ttu-id="5ddac-1477">**Icono** ![Icono de función I O C T L de obtención de estado de dispositivo de clase C D C A C M de host](./media/user-guide/usbx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1477">**Icon** ![Host Class C D C A C M I O C T L Get Device Status icon](./media/user-guide/usbx-events/image94.png)</span></span>

<span data-ttu-id="5ddac-1478">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1478">**Description**</span></span>

<span data-ttu-id="5ddac-1479">Este evento representa un evento de una función IOCTL de obtención de estado de dispositivo de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1479">This event represents a USBX Host Class Cdc Acm Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="5ddac-1480">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1480">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1481">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1481">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1482">Campo de información 2: estado del dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-1482">Info Field 2: Device status.</span></span>
- <span data-ttu-id="5ddac-1483">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1483">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1484">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1484">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a><span data-ttu-id="5ddac-1485">Función IOCTL de obtención de codificación de línea de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1485">Host Class Cdc Acm Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="5ddac-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="5ddac-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span></span>

<span data-ttu-id="5ddac-1487">**Icono** ![Icono de función I O C T L de obtención de codificación de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1487">**Icon** ![Host Class C D C A C M I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image95.png)</span></span>

<span data-ttu-id="5ddac-1488">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1488">**Description**</span></span>

<span data-ttu-id="5ddac-1489">Este evento representa un evento de una función IOCTL de obtención de codificación de línea de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1489">This event represents a USBX Host Class Cdc Acm Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="5ddac-1490">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1490">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1491">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1491">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1492">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-1492">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-1493">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1493">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1494">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1494">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a><span data-ttu-id="5ddac-1495">Función IOCTL de devolución de llamada de notificación de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1495">Host Class Cdc Acm Ioctl Notification Callback</span></span>

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a><span data-ttu-id="5ddac-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span><span class="sxs-lookup"><span data-stu-id="5ddac-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span></span>

<span data-ttu-id="5ddac-1497">**Icono** ![Icono de función I O C T L de devolución de llamada de notificación de clase C D C A C M de host](./media/user-guide/usbx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1497">**Icon** ![Host Class C D C A C M I O C T L Notification Callback icon](./media/user-guide/usbx-events/image96.png)</span></span>

<span data-ttu-id="5ddac-1498">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1498">**Description**</span></span>

<span data-ttu-id="5ddac-1499">Este evento representa un evento de una función IOCTL de devolución de llamada de notificación de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1499">This event represents a USBX Host Class Cdc Acm Ioctl Notification Callback Event.</span></span>

<span data-ttu-id="5ddac-1500">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1500">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1501">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1501">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1502">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-1502">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-1503">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1503">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1504">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1504">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-send-break"></a><span data-ttu-id="5ddac-1505">Función IOCTL de interrupción de envío de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1505">Host Class Cdc Acm Ioctl Send Break</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a><span data-ttu-id="5ddac-1506">ux_host_class_cdc_acm_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="5ddac-1506">ux_host_class_cdc_acm_ioctl_send_break</span></span>

<span data-ttu-id="5ddac-1507">**Icono** ![Icono de función I O C T L de interrupción de envío de clase C D C A C M de host](./media/user-guide/usbx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1507">**Icon** ![Host Class C D C A C M I O C T L Send Break icon](./media/user-guide/usbx-events/image97.png)</span></span>

<span data-ttu-id="5ddac-1508">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1508">**Description**</span></span>

<span data-ttu-id="5ddac-1509">Este evento representa un evento de una función IOCTL de interrupción de envío de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1509">This event represents a USBX Host Class Cdc Acm Ioctl Send Break Event.</span></span>

<span data-ttu-id="5ddac-1510">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1510">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1511">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1511">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1512">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-1512">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-1513">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1513">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1514">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1514">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a><span data-ttu-id="5ddac-1515">Función IOCTL de establecimiento de codificación de línea de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1515">Host Class Cdc Acm Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="5ddac-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="5ddac-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span></span>

<span data-ttu-id="5ddac-1517">**Icono** ![Icono de función I O C T L de establecimiento de codificación de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1517">**Icon** ![The Host Class C D C A C M I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)</span></span>

<span data-ttu-id="5ddac-1518">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1518">**Description**</span></span>

<span data-ttu-id="5ddac-1519">Este evento representa un evento de una función IOCTL de establecimiento de codificación de línea de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1519">This event represents a USBX Host Class Cdc Acm Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="5ddac-1520">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1520">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1521">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1521">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1522">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-1522">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-1523">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1523">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1524">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1524">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a><span data-ttu-id="5ddac-1525">Función IOCTL de establecimiento de estado de línea de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1525">Host Class Cdc Acm Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="5ddac-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="5ddac-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span></span>

<span data-ttu-id="5ddac-1527">**Icono** ![Icono de función I O C T L de establecimiento de estado de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1527">**Icon** ![Host Class C D C A C M I O C T L Set Line State icon](./media/user-guide/usbx-events/image99.png)</span></span>

<span data-ttu-id="5ddac-1528">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1528">**Description**</span></span>

<span data-ttu-id="5ddac-1529">Este evento representa un evento de establecimiento de estado de línea de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1529">This event represents a USBX Host Class Cdc Acm Ioctl Set Line State Event.</span></span>

<span data-ttu-id="5ddac-1530">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1530">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1531">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1531">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1532">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-1532">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-1533">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1533">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1534">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1534">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-read"></a><span data-ttu-id="5ddac-1535">Lectura de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1535">Host Class Cdc Acm Read</span></span> 

#### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="5ddac-1536">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-1536">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="5ddac-1537">**Icono** ![Icono de lectura de clase C D C A C M de host](./media/user-guide/usbx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1537">**Icon** ![Host Class C D C A C M Read icon](./media/user-guide/usbx-events/image100.png)</span></span>

<span data-ttu-id="5ddac-1538">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1538">**Description**</span></span>

<span data-ttu-id="5ddac-1539">Este evento representa un evento de lectura de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1539">This event represents a USBX Host Class Cdc Acm Read Event.</span></span>

<span data-ttu-id="5ddac-1540">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1540">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1541">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1541">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1542">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1542">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-1543">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-1543">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="5ddac-1544">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1544">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-start"></a><span data-ttu-id="5ddac-1545">Inicio de recepción de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1545">Host Class Cdc Acm Reception Start</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="5ddac-1546">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="5ddac-1546">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="5ddac-1547">**Icono** ![Icono de inicio de recepción de clase C D C A C M de host](./media/user-guide/usbx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1547">**Icon** ![Host Class C D C A C M Reception Start icon](./media/user-guide/usbx-events/image101.png)</span></span>

<span data-ttu-id="5ddac-1548">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1548">**Description**</span></span>

<span data-ttu-id="5ddac-1549">Este evento representa un evento de inicio de recepción de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1549">This event represents a USBX Host Class Cdc Acm Reception Start Event.</span></span>

<span data-ttu-id="5ddac-1550">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1550">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1551">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1551">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1552">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1552">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1553">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1553">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1554">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1554">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-stop"></a><span data-ttu-id="5ddac-1555">Parada de recepción de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1555">Host Class Cdc Acm Reception Stop</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="5ddac-1556">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="5ddac-1556">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="5ddac-1557">**Icono** ![Icono de parada de recepción de clase C D C A C M de host](./media/user-guide/usbx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1557">**Icon** ![Host Class C D C A C M Reception Stop icon](./media/user-guide/usbx-events/image102.png)</span></span>

<span data-ttu-id="5ddac-1558">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1558">**Description**</span></span>

<span data-ttu-id="5ddac-1559">Este evento representa un evento de parada de recepción de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1559">This event represents a USBX Host Class Cdc Acm Reception Stop Event.</span></span>

<span data-ttu-id="5ddac-1560">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1560">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1561">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1561">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1562">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1562">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1563">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1563">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-write"></a><span data-ttu-id="5ddac-1564">Escritura de clase CDC ACM de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1564">Host Class Cdc Acm Write</span></span> 

#### <a name="ux_host_class_acm_write"></a><span data-ttu-id="5ddac-1565">ux_host_class_acm_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-1565">ux_host_class_acm_write</span></span>

<span data-ttu-id="5ddac-1566">**Icono** ![Icono de escritura de clase C D C A C M de host](./media/user-guide/usbx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1566">**Icon** ![Host Class C D C A C M Write icon](./media/user-guide/usbx-events/image103.png)</span></span>

<span data-ttu-id="5ddac-1567">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1567">**Description**</span></span>

<span data-ttu-id="5ddac-1568">Este evento representa un evento de escritura de la clase CDC ACM del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1568">This event represents a USBX Host Class Cdc Acm Write Event.</span></span>

<span data-ttu-id="5ddac-1569">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1569">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1570">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1570">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1571">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1571">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-1572">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-1572">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="5ddac-1573">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1573">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-activate"></a><span data-ttu-id="5ddac-1574">Activación de clase DPUMP de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1574">Host Class Dpump Activate</span></span> 

#### <a name="ux_host_class_dpump_activate"></a><span data-ttu-id="5ddac-1575">ux_host_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1575">ux_host_class_dpump_activate</span></span>

<span data-ttu-id="5ddac-1576">**Icono** ![Icono de activación de clase DPUMP de host](./media/user-guide/usbx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1576">**Icon** ![Host Class Dpump Activate icon](./media/user-guide/usbx-events/image104.png)</span></span>

<span data-ttu-id="5ddac-1577">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1577">**Description**</span></span>

<span data-ttu-id="5ddac-1578">Este evento representa un evento de activación de la clase DPUMP del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1578">This event represents a USBX Host Class Dpump Activate Event.</span></span>

<span data-ttu-id="5ddac-1579">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1579">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1580">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1580">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1581">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1581">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1582">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1582">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1583">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1583">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-deactivate"></a><span data-ttu-id="5ddac-1584">Desactivación de clase DPUMP de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1584">Host Class Dpump Deactivate</span></span> 

#### <a name="ux_host_class_dpump_deactivate"></a><span data-ttu-id="5ddac-1585">ux_host_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1585">ux_host_class_dpump_deactivate</span></span>

<span data-ttu-id="5ddac-1586">**Icono** ![Icono de desactivación de clase DPUMP de host](./media/user-guide/usbx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1586">**Icon** ![Host Class Dpump Deactivate icon](./media/user-guide/usbx-events/image105.png)</span></span>

<span data-ttu-id="5ddac-1587">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1587">**Description**</span></span>

<span data-ttu-id="5ddac-1588">Este evento representa un evento de desactivación de la clase DPUMP del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1588">This event represents a USBX Host Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1589">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1589">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1590">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1590">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1591">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1591">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1592">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1592">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1593">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1593">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-read"></a><span data-ttu-id="5ddac-1594">Lectura de clase DPUMP de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1594">Host Class Dpump Read</span></span> 

#### <a name="ux_host_class_dpump_read"></a><span data-ttu-id="5ddac-1595">ux_host_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-1595">ux_host_class_dpump_read</span></span>

<span data-ttu-id="5ddac-1596">**Icono** ![Icono de lectura de clase DPUMP de host](./media/user-guide/usbx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1596">**Icon** ![Host Class Dpump Read icon](./media/user-guide/usbx-events/image106.png)</span></span>

<span data-ttu-id="5ddac-1597">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1597">**Description**</span></span>

<span data-ttu-id="5ddac-1598">Este evento representa un evento de lectura de la clase DPUMP del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1598">This event represents a USBX Host Class Dpump Read Event.</span></span>

<span data-ttu-id="5ddac-1599">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1599">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1600">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1600">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1601">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1601">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-1602">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-1602">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-1603">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1603">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-write"></a><span data-ttu-id="5ddac-1604">Escritura de clase DPUMP de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1604">Host Class Dpump Write</span></span> 

#### <a name="ux_host_class_dpump_write"></a><span data-ttu-id="5ddac-1605">ux_host_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-1605">ux_host_class_dpump_write</span></span>

<span data-ttu-id="5ddac-1606">**Icono** ![Icono de escritura de clase DPUMP de host](./media/user-guide/usbx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1606">**Icon** ![Host Class Dpump Write icon](./media/user-guide/usbx-events/image107.png)</span></span>

<span data-ttu-id="5ddac-1607">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1607">**Description**</span></span>

<span data-ttu-id="5ddac-1608">Este evento representa un evento de escritura de la clase DPUMP del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1608">This event represents a USBX Host Class Dpump Write Event.</span></span>

<span data-ttu-id="5ddac-1609">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1609">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1610">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1610">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1611">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1611">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-1612">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-1612">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-1613">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1613">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-activate"></a><span data-ttu-id="5ddac-1614">Activación de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1614">Host Class Hid Activate</span></span> 

#### <a name="ux_host_class_hid_activate"></a><span data-ttu-id="5ddac-1615">ux_host_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1615">ux_host_class_hid_activate</span></span>

<span data-ttu-id="5ddac-1616">**Icono** ![Icono de activación de clase HID de host](./media/user-guide/usbx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1616">**Icon** ![Host Class Hid Activate icon](./media/user-guide/usbx-events/image108.png)</span></span>

<span data-ttu-id="5ddac-1617">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1617">**Description**</span></span>

<span data-ttu-id="5ddac-1618">Este evento representa un evento de activación de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1618">This event represents a USBX Host Class Hid Activate Event.</span></span>

<span data-ttu-id="5ddac-1619">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1619">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1620">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1620">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1621">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1621">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1622">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1622">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1623">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1623">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-client-register"></a><span data-ttu-id="5ddac-1624">Registro de cliente de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1624">Host Class Hid Client Register</span></span> 

#### <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="5ddac-1625">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="5ddac-1625">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="5ddac-1626">**Icono** ![Icono de registro de cliente de clase HID de host](./media/user-guide/usbx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1626">**Icon** ![Host Class Hid Client Register icon](./media/user-guide/usbx-events/image109.png)</span></span>

<span data-ttu-id="5ddac-1627">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1627">**Description**</span></span>

<span data-ttu-id="5ddac-1628">Este evento representa un evento de registro de cliente de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1628">This event represents a USBX Host Class Hid Client Register Event.</span></span>

<span data-ttu-id="5ddac-1629">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1629">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1630">Campo de información 1: nombre de cliente de HID</span><span class="sxs-lookup"><span data-stu-id="5ddac-1630">Info Field 1: Hid client name.</span></span>
- <span data-ttu-id="5ddac-1631">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1631">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1632">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1632">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1633">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1633">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-deactivate"></a><span data-ttu-id="5ddac-1634">Desactivación de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1634">Host Class Hid Deactivate</span></span> 

#### <a name="ux_host_class_hid_deactivate"></a><span data-ttu-id="5ddac-1635">ux_host_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1635">ux_host_class_hid_deactivate</span></span>

<span data-ttu-id="5ddac-1636">**Icono** ![Icono de desactivación de clase HID de host](./media/user-guide/usbx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1636">**Icon** ![Host Class Hid Deactivate icon](./media/user-guide/usbx-events/image110.png)</span></span>

<span data-ttu-id="5ddac-1637">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1637">**Description**</span></span>

<span data-ttu-id="5ddac-1638">Este evento representa un evento de desactivación de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1638">This event represents a USBX Host Class Hid Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1639">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1639">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1640">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1640">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1641">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1641">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1642">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1642">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1643">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1643">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-get"></a><span data-ttu-id="5ddac-1644">Obtención de inactividad de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1644">Host Class Hid Idle Get</span></span> 

#### <a name="ux_host_class_hid_idle_get"></a><span data-ttu-id="5ddac-1645">ux_host_class_hid_idle_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1645">ux_host_class_hid_idle_get</span></span>

<span data-ttu-id="5ddac-1646">**Icono** ![Icono de obtención de inactividad de clase HID de host](./media/user-guide/usbx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1646">**Icon** ![Host Class Hid Idle Get icon](./media/user-guide/usbx-events/image111.png)</span></span>

<span data-ttu-id="5ddac-1647">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1647">**Description**</span></span>

<span data-ttu-id="5ddac-1648">Este evento representa un evento de obtención de inactividad de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1648">This event represents a USBX Host Class Hid Idle Get Event.</span></span>

<span data-ttu-id="5ddac-1649">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1649">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1650">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1650">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1651">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1651">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1652">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1652">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1653">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1653">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-set"></a><span data-ttu-id="5ddac-1654">Establecimiento de inactividad de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1654">Host Class Hid Idle Set</span></span> 

#### <a name="ux_host_class_hid_idle_set"></a><span data-ttu-id="5ddac-1655">ux_host_class_hid_idle_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-1655">ux_host_class_hid_idle_set</span></span>

<span data-ttu-id="5ddac-1656">**Icono** ![Icono de establecimiento de inactividad de clase HID de host](./media/user-guide/usbx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1656">**Icon** ![Host Class Hid Idle Set icon](./media/user-guide/usbx-events/image112.png)</span></span>

<span data-ttu-id="5ddac-1657">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1657">**Description**</span></span>

<span data-ttu-id="5ddac-1658">Este evento representa un evento de establecimiento de inactividad de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1658">This event represents a USBX Host Class Hid Idle Set Event.</span></span>

<span data-ttu-id="5ddac-1659">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1659">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1660">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1660">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1661">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1661">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1662">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1662">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1663">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1663">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-activate"></a><span data-ttu-id="5ddac-1664">Activación de teclado de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1664">Host Class Hid Keyboard Activate</span></span> 

#### <a name="ux_host_class_hid_keyboard_activate"></a><span data-ttu-id="5ddac-1665">ux_host_class_hid_keyboard_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1665">ux_host_class_hid_keyboard_activate</span></span>

<span data-ttu-id="5ddac-1666">**Icono** ![Icono de activación de teclado de clase HID de host](./media/user-guide/usbx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1666">**Icon** ![Host Class Hid Keyboard Activate icon](./media/user-guide/usbx-events/image113.png)</span></span>

<span data-ttu-id="5ddac-1667">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1667">**Description**</span></span>

<span data-ttu-id="5ddac-1668">Este evento representa un evento de activación de teclado de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1668">This event represents a USBX Host Class Hid Keyboard Activate Event.</span></span>

<span data-ttu-id="5ddac-1669">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1669">**Information Fields**</span></span>
<p><span data-ttu-id="5ddac-1670">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1670">Info Field 1: Class instance.</span></span>
<p><span data-ttu-id="5ddac-1671">Campo de información 2: instancia de cliente de HID</span><span class="sxs-lookup"><span data-stu-id="5ddac-1671">Info Field 2: Hid client instance.</span></span>
<p><span data-ttu-id="5ddac-1672">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1672">Info Field 3: Not used.</span></span>
<p><span data-ttu-id="5ddac-1673">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1673">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-deactivate"></a><span data-ttu-id="5ddac-1674">Desactivación de teclado de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1674">Host Class Hid Keyboard Deactivate</span></span> 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a><span data-ttu-id="5ddac-1675">ux_host_class_hid_keyboard_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1675">ux_host_class_hid_keyboard_deactivate</span></span>

<span data-ttu-id="5ddac-1676">**Icono** ![Icono de desactivación de teclado de clase HID de host](./media/user-guide/usbx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1676">**Icon** ![Host Class Hid Keyboard Deactivate icon](./media/user-guide/usbx-events/image114.png)</span></span>

<span data-ttu-id="5ddac-1677">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1677">**Description**</span></span>

<span data-ttu-id="5ddac-1678">Este evento representa un evento de desactivación de teclado de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1678">This event represents a USBX Host Class Hid Keyboard Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1679">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1679">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1680">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1680">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1681">Campo de información 2: instancia de cliente de HID</span><span class="sxs-lookup"><span data-stu-id="5ddac-1681">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="5ddac-1682">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1682">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1683">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1683">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-activate"></a><span data-ttu-id="5ddac-1684">Activación de mouse de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1684">Host Class Hid Mouse Activate</span></span> 

#### <a name="ux_host_class_hid_mouse_activate"></a><span data-ttu-id="5ddac-1685">ux_host_class_hid_mouse_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1685">ux_host_class_hid_mouse_activate</span></span>

<span data-ttu-id="5ddac-1686">**Icono** ![Icono de activación de mouse de clase HID de host](./media/user-guide/usbx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1686">**Icon** ![Host Class Hid Mouse Activate icon](./media/user-guide/usbx-events/image115.png)</span></span>

<span data-ttu-id="5ddac-1687">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1687">**Description**</span></span>

<span data-ttu-id="5ddac-1688">Este evento representa un evento de activación de mouse de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1688">This event represents a USBX Host Class Hid Mouse Activate Event.</span></span>

<span data-ttu-id="5ddac-1689">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1689">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1690">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1690">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1691">Campo de información 2: instancia de cliente de HID</span><span class="sxs-lookup"><span data-stu-id="5ddac-1691">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="5ddac-1692">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1692">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1693">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1693">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-deactivate"></a><span data-ttu-id="5ddac-1694">Desactivación de mouse de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1694">Host Class Hid Mouse Deactivate</span></span> 

#### <a name="ux_host_class_hid_mouse_deactivate"></a><span data-ttu-id="5ddac-1695">ux_host_class_hid_mouse_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1695">ux_host_class_hid_mouse_deactivate</span></span>

<span data-ttu-id="5ddac-1696">**Icono** ![Icono de desactivación de mouse de clase HID de host](./media/user-guide/usbx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1696">**Icon** ![Host Class Hid Mouse Deactivate icon](./media/user-guide/usbx-events/image116.png)</span></span>

<span data-ttu-id="5ddac-1697">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1697">**Description**</span></span>

- <span data-ttu-id="5ddac-1698">Este evento representa un evento de desactivación de mouse de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1698">This event represents a USBX Host Class Hid Mouse Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1699">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1699">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1700">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1700">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1701">Campo de información 2: instancia de cliente de HID</span><span class="sxs-lookup"><span data-stu-id="5ddac-1701">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="5ddac-1702">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1702">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1703">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1703">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-activate"></a><span data-ttu-id="5ddac-1704">Activación de control remoto de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1704">Host Class Hid Remote Control Activate</span></span> 

#### <a name="ux_host_class_hid_remote_control_activate"></a><span data-ttu-id="5ddac-1705">ux_host_class_hid_remote_control_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1705">ux_host_class_hid_remote_control_activate</span></span>

<span data-ttu-id="5ddac-1706">**Icono** ![Icono de activación de control remoto de clase HID de host](./media/user-guide/usbx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1706">**Icon** ![Host Class Hid Remote Control Activate icon](./media/user-guide/usbx-events/image117.png)</span></span>

<span data-ttu-id="5ddac-1707">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1707">**Description**</span></span>

<span data-ttu-id="5ddac-1708">Este evento representa un evento de activación de control remoto de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1708">This event represents a USBX Host Class Hid Remote Control Activate Event.</span></span>

<span data-ttu-id="5ddac-1709">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1709">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1710">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1710">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1711">Campo de información 2: instancia de cliente de HID</span><span class="sxs-lookup"><span data-stu-id="5ddac-1711">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="5ddac-1712">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1712">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1713">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1713">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-deactivate"></a><span data-ttu-id="5ddac-1714">Desactivación de control remoto de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1714">Host Class Hid Remote Control Deactivate</span></span> 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a><span data-ttu-id="5ddac-1715">ux_host_class_hid_remote_control_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1715">ux_host_class_hid_remote_control_deactivate</span></span>

<span data-ttu-id="5ddac-1716">**Icono** ![Icono de desactivación de control remoto de clase HID de host](./media/user-guide/usbx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1716">**Icon** ![Host Class Hid Remote Control Deactivate icon](./media/user-guide/usbx-events/image118.png)</span></span>

<span data-ttu-id="5ddac-1717">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1717">**Description**</span></span>

<span data-ttu-id="5ddac-1718">Este evento representa un evento de desactivación de control remoto de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1718">This event represents a USBX Host Class Hid Remote Control Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1719">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1719">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1720">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1720">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1721">Campo de información 2: instancia de cliente de HID</span><span class="sxs-lookup"><span data-stu-id="5ddac-1721">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="5ddac-1722">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1722">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1723">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1723">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-get"></a><span data-ttu-id="5ddac-1724">Obtención de informe de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1724">Host Class Hid Report Get</span></span> 

#### <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="5ddac-1725">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1725">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="5ddac-1726">**Icono** ![Icono de obtención de informe de clase HID de host](./media/user-guide/usbx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1726">**Icon** ![Host Class Hid Report Get icon](./media/user-guide/usbx-events/image119.png)</span></span>

<span data-ttu-id="5ddac-1727">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1727">**Description**</span></span>

<span data-ttu-id="5ddac-1728">Este evento representa una obtención de informe de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1728">This event represents a USBX Host Class Hid Report Get.</span></span>

<span data-ttu-id="5ddac-1729">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1729">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1730">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1730">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1731">Campo de información 2: informe de cliente</span><span class="sxs-lookup"><span data-stu-id="5ddac-1731">Info Field 2: Client report.</span></span>
- <span data-ttu-id="5ddac-1732">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1732">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1733">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1733">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-set"></a><span data-ttu-id="5ddac-1734">Establecimiento de informe de clase HID de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1734">Host Class Hid Report Set</span></span> 

#### <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="5ddac-1735">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-1735">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="5ddac-1736">**Icono** ![Icono de establecimiento de informe de clase HID de host](./media/user-guide/usbx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1736">**Icon** ![Host Class Hid Report Set icon](./media/user-guide/usbx-events/image120.png)</span></span>

<span data-ttu-id="5ddac-1737">**Descripción** Este evento representa un establecimiento de informe de la clase HID del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1737">**Description** This event represents a USBX Host Class Hid Report Set.</span></span>

<span data-ttu-id="5ddac-1738">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1738">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1739">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1739">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1740">Campo de información 2: informe de cliente</span><span class="sxs-lookup"><span data-stu-id="5ddac-1740">Info Field 2: Client report.</span></span>
- <span data-ttu-id="5ddac-1741">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1741">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1742">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1742">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-activate"></a><span data-ttu-id="5ddac-1743">Activación de clase HUB de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1743">Host Class Hub Activate</span></span> 

#### <a name="ux_host_class_hub_activate"></a><span data-ttu-id="5ddac-1744">ux_host_class_hub_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1744">ux_host_class_hub_activate</span></span>

<span data-ttu-id="5ddac-1745">**Icono** ![Icono de activación de clase HUB de host](./media/user-guide/usbx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1745">**Icon** ![Host Class Hub Activate icon](./media/user-guide/usbx-events/image121.png)</span></span>

<span data-ttu-id="5ddac-1746">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1746">**Description**</span></span>

<span data-ttu-id="5ddac-1747">Este evento representa un evento de activación de la clase HUB del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1747">This event represents a USBX Host Class Hub Activate Event.</span></span>

<span data-ttu-id="5ddac-1748">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1748">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-1749">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1749">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1750">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1750">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1751">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1751">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1752">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1752">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-change-detect"></a><span data-ttu-id="5ddac-1753">Detección de cambio de clase HUB de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1753">Host Class Hub Change Detect</span></span> 

#### <a name="ux_host_class_hub_change_detect"></a><span data-ttu-id="5ddac-1754">ux_host_class_hub_change_detect</span><span class="sxs-lookup"><span data-stu-id="5ddac-1754">ux_host_class_hub_change_detect</span></span>

<span data-ttu-id="5ddac-1755">**Icono** ![Icono de detección de cambio de clase HUB de host](./media/user-guide/usbx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1755">**Icon** ![Host Class Hub Change Detect icon](./media/user-guide/usbx-events/image122.png)</span></span>

<span data-ttu-id="5ddac-1756">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1756">**Description**</span></span>

<span data-ttu-id="5ddac-1757">Este evento representa un evento de detección de cambio de la clase HUB del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1757">This event represents a USBX Host Class Hub Change Detect Event.</span></span>

<span data-ttu-id="5ddac-1758">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1758">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1759">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1759">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1760">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1760">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1761">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1761">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1762">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1762">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-deactivate"></a><span data-ttu-id="5ddac-1763">Desactivación de clase HUB de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1763">Host Class Hub Deactivate</span></span> 

#### <a name="ux_host_class_hub_deactivate"></a><span data-ttu-id="5ddac-1764">ux_host_class_hub_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1764">ux_host_class_hub_deactivate</span></span>

<span data-ttu-id="5ddac-1765">**Icono** ![Icono de desactivación de clase HUB de host](./media/user-guide/usbx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1765">**Icon** ![Host Class Hub Deactivate icon](./media/user-guide/usbx-events/image123.png)</span></span>

<span data-ttu-id="5ddac-1766">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1766">**Description**</span></span>

<span data-ttu-id="5ddac-1767">Este evento representa un evento de desactivación de la clase HUB del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1767">This event represents a USBX Host Class Hub Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1768">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1768">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1769">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1769">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1770">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1770">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1771">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1771">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1772">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1772">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-connection-process"></a><span data-ttu-id="5ddac-1773">Proceso de cambio de puerto de conexión de clase HUB de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1773">Host Class Hub Port Change Connection Process</span></span> 

#### <a name="ux_host_class_hub_change_connection_process"></a><span data-ttu-id="5ddac-1774">ux_host_class_hub_change_connection_process</span><span class="sxs-lookup"><span data-stu-id="5ddac-1774">ux_host_class_hub_change_connection_process</span></span>

<span data-ttu-id="5ddac-1775">**Icono** ![Icono de proceso de cambio de puerto de conexión de clase HUB de host](./media/user-guide/usbx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1775">**Icon** ![Host Class Hub Port Change Connection Process icon](./media/user-guide/usbx-events/image124.png)</span></span>

<span data-ttu-id="5ddac-1776">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1776">**Description**</span></span>

<span data-ttu-id="5ddac-1777">Este evento representa un evento de proceso de cambio del puerto de conexión de la clase HUB del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1777">This event represents a USBX Host Class Hub Port Change Connection Process Event.</span></span>

<span data-ttu-id="5ddac-1778">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1778">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1779">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1779">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1780">Campo de información 2: puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1780">Info Field 2: Port.</span></span>
- <span data-ttu-id="5ddac-1781">Campo de información 3: estado de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1781">Info Field 3: Port status.</span></span>
- <span data-ttu-id="5ddac-1782">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1782">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-enable-process"></a><span data-ttu-id="5ddac-1783">Habilitación de proceso de cambio de puerto de clase HUB de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1783">Host Class Hub Port Change Enable Process</span></span> 

#### <a name="ux_host_class_hub_port_change_enable_process"></a><span data-ttu-id="5ddac-1784">ux_host_class_hub_port_change_enable_process</span><span class="sxs-lookup"><span data-stu-id="5ddac-1784">ux_host_class_hub_port_change_enable_process</span></span>

<span data-ttu-id="5ddac-1785">**Icono** ![Icono de habilitación de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1785">**Icon** ![Host Class Hub Port Change Enable Process icon](./media/user-guide/usbx-events/image125.png)</span></span>

<span data-ttu-id="5ddac-1786">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1786">**Description**</span></span>

<span data-ttu-id="5ddac-1787">Este evento representa un evento de habilitación del proceso de cambio de puerto de la clase HUB del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1787">This event represents a USBX Host Class Hub Port Change Enable Process Event.</span></span>

<span data-ttu-id="5ddac-1788">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1788">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1789">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1789">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1790">Campo de información 2: puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1790">Info Field 2: Port.</span></span>
- <span data-ttu-id="5ddac-1791">Campo de información 3: estado de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1791">Info Field 3: Port status.</span></span>
- <span data-ttu-id="5ddac-1792">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1792">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-over-current-process"></a><span data-ttu-id="5ddac-1793">Proceso actual finalizado de cambio de puerto de clase HUB de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1793">Host Class Hub Port Change Over Current Process</span></span> 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a><span data-ttu-id="5ddac-1794">ux_host_class_hub_port_change_over_current_process</span><span class="sxs-lookup"><span data-stu-id="5ddac-1794">ux_host_class_hub_port_change_over_current_process</span></span>

<span data-ttu-id="5ddac-1795">**Icono** ![Icono de proceso actual finalizado de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1795">**Icon** ![Host Class Hub Port Change Over Current Process icon](./media/user-guide/usbx-events/image126.png)</span></span>

<span data-ttu-id="5ddac-1796">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1796">**Description**</span></span>

<span data-ttu-id="5ddac-1797">Este evento representa la asignación de un paquete por medio de nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1797">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="5ddac-1798">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1798">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1799">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1799">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1800">Campo de información 2: puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1800">Info Field 2: Port.</span></span>
- <span data-ttu-id="5ddac-1801">Campo de información 3: estado de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1801">Info Field 3: Port status.</span></span>
- <span data-ttu-id="5ddac-1802">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1802">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-reset-process"></a><span data-ttu-id="5ddac-1803">Restablecimiento de proceso de cambio de puerto de clase HUB de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1803">Host Class Hub Port Change Reset Process</span></span> 

#### <a name="ux_host_class_hub_port_change_reset_process"></a><span data-ttu-id="5ddac-1804">ux_host_class_hub_port_change_reset_process</span><span class="sxs-lookup"><span data-stu-id="5ddac-1804">ux_host_class_hub_port_change_reset_process</span></span>

<span data-ttu-id="5ddac-1805">**Icono** ![Icono de restablecimiento de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1805">**Icon** ![Host Class Hub Port Change Reset Process icon](./media/user-guide/usbx-events/image127.png)</span></span>

<span data-ttu-id="5ddac-1806">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1806">**Description**</span></span>

<span data-ttu-id="5ddac-1807">Este evento representa un evento de restablecimiento del proceso de cambio de puerto de la clase HUB del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1807">This event represents a USBX Host Class Hub Port Change Reset Process Event.</span></span>

<span data-ttu-id="5ddac-1808">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1808">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1809">Campo de información 1: centro de conectividad</span><span class="sxs-lookup"><span data-stu-id="5ddac-1809">Info Field 1: Hub.</span></span> <span data-ttu-id="5ddac-1810">Campo de información 2: puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1810">Info Field 2: Port.</span></span>
- <span data-ttu-id="5ddac-1811">Campo de información 3: estado de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1811">Info Field 3: Port status.</span></span>
- <span data-ttu-id="5ddac-1812">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1812">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-suspend-process"></a><span data-ttu-id="5ddac-1813">Suspensión de proceso de cambio de puerto de clase HUB de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1813">Host Class Hub Port Change Suspend Process</span></span> 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a><span data-ttu-id="5ddac-1814">ux_host_class_hub_port_change_suspend_process</span><span class="sxs-lookup"><span data-stu-id="5ddac-1814">ux_host_class_hub_port_change_suspend_process</span></span>

<span data-ttu-id="5ddac-1815">**Icono** ![Icono de suspensión de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1815">**Icon** ![Host Class Hub Port Change Suspend Process icon](./media/user-guide/usbx-events/image128.png)</span></span>

<span data-ttu-id="5ddac-1816">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1816">**Description**</span></span>

<span data-ttu-id="5ddac-1817">Este evento representa un evento de suspensión del proceso de cambio de puerto de la clase HUB del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1817">This event represents a USBX Host Class Hub Port Change Suspend Process Event.</span></span>

<span data-ttu-id="5ddac-1818">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1818">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1819">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1819">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1820">Campo de información 2: puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1820">Info Field 2: Port.</span></span>
- <span data-ttu-id="5ddac-1821">Campo de información 3: estado de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1821">Info Field 3: Port status.</span></span>
- <span data-ttu-id="5ddac-1822">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1822">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-activate"></a><span data-ttu-id="5ddac-1823">Activación de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1823">Host Class Pima Activate</span></span> 

#### <a name="ux_host_class_pima_activate"></a><span data-ttu-id="5ddac-1824">ux_host_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1824">ux_host_class_pima_activate</span></span>

<span data-ttu-id="5ddac-1825">**Icono** ![Icono de activación de clase PIMA de host](./media/user-guide/usbx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1825">**Icon** ![Host Class Pima Activate icon](./media/user-guide/usbx-events/image129.png)</span></span>

<span data-ttu-id="5ddac-1826">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1826">**Description**</span></span>

<span data-ttu-id="5ddac-1827">Este evento representa un evento de activación de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1827">This event represents a USBX Host Class Pima Activate Event.</span></span>

<span data-ttu-id="5ddac-1828">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1828">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1829">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1829">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1830">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1830">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1831">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1831">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1832">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1832">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-deactivate"></a><span data-ttu-id="5ddac-1833">Desactivación de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1833">Host Class Pima Deactivate</span></span> 

#### <a name="ux_host_class_pima_deactivate"></a><span data-ttu-id="5ddac-1834">ux_host_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-1834">ux_host_class_pima_deactivate</span></span>

<span data-ttu-id="5ddac-1835">**Icono** ![Icono de desactivación de clase PIMA de host](./media/user-guide/usbx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1835">**Icon** ![Host Class Pima Deactivate icon](./media/user-guide/usbx-events/image130.png)</span></span>

<span data-ttu-id="5ddac-1836">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1836">**Description**</span></span>

<span data-ttu-id="5ddac-1837">Este evento representa un evento de desactivación de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1837">This event represents a USBX Host Class Pima Deactivate Event.</span></span>

<span data-ttu-id="5ddac-1838">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1838">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1839">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1839">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1840">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1840">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1841">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1841">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1842">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1842">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-info-get"></a><span data-ttu-id="5ddac-1843">Obtención de información de dispositivo de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1843">Host Class Pima Device Info Get</span></span> 

#### <a name="ux_host_class_pima_device_info_get"></a><span data-ttu-id="5ddac-1844">ux_host_class_pima_device_info_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1844">ux_host_class_pima_device_info_get</span></span>

<span data-ttu-id="5ddac-1845">**Icono** ![Icono de obtención de información de dispositivo de clase PIMA de host](./media/user-guide/usbx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1845">**Icon** ![Host Class Pima Device Info Get icon](./media/user-guide/usbx-events/image131.png)</span></span>

<span data-ttu-id="5ddac-1846">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1846">**Description**</span></span>

<span data-ttu-id="5ddac-1847">Este evento representa un evento de obtención de información del dispositivo de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1847">This event represents a USBX Host Class Pima Device Info Get Event.</span></span>

<span data-ttu-id="5ddac-1848">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1848">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1849">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1849">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1850">Campo de información 2: dispositivo PIMA</span><span class="sxs-lookup"><span data-stu-id="5ddac-1850">Info Field 2: Pima device.</span></span>
- <span data-ttu-id="5ddac-1851">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1851">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1852">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1852">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-reset"></a><span data-ttu-id="5ddac-1853">Restablecimiento de dispositivo de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1853">Host Class Pima Device Reset</span></span> 

#### <a name="ux_host_class_pima_device_reset"></a><span data-ttu-id="5ddac-1854">ux_host_class_pima_device_reset</span><span class="sxs-lookup"><span data-stu-id="5ddac-1854">ux_host_class_pima_device_reset</span></span>

<span data-ttu-id="5ddac-1855">**Icono** ![Icono de restablecimiento de dispositivo de clase PIMA de host](./media/user-guide/usbx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1855">**Icon** ![Host Class Pima Device Reset icon](./media/user-guide/usbx-events/image132.png)</span></span>

<span data-ttu-id="5ddac-1856">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1856">**Description**</span></span>

<span data-ttu-id="5ddac-1857">Este evento representa un evento de restablecimiento de dispositivo de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1857">This event represents a USBX Host Class Pima Device Reset Event.</span></span>

<span data-ttu-id="5ddac-1858">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1858">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1859">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1859">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1860">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1860">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1861">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1861">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1862">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1862">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-notification"></a><span data-ttu-id="5ddac-1863">Notificación de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1863">Host Class Pima Notification</span></span> 

#### <a name="ux_host_class_pima_notification"></a><span data-ttu-id="5ddac-1864">ux_host_class_pima_notification</span><span class="sxs-lookup"><span data-stu-id="5ddac-1864">ux_host_class_pima_notification</span></span>

<span data-ttu-id="5ddac-1865">**Icono** ![Icono de notificación de clase PIMA de host](./media/user-guide/usbx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1865">**Icon** ![Host Class Pima Notification icon](./media/user-guide/usbx-events/image133.png)</span></span>

<span data-ttu-id="5ddac-1866">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1866">**Description**</span></span>

<span data-ttu-id="5ddac-1867">Este evento representa un evento de notificación de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1867">This event represents a USBX Host Class Pima Notification Event.</span></span>

<span data-ttu-id="5ddac-1868">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1868">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1869">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1869">Info Field 1: Class instance.</span></span> <span data-ttu-id="5ddac-1870">Campo de información 2: código de evento</span><span class="sxs-lookup"><span data-stu-id="5ddac-1870">Info Field 2: Event code.</span></span>
- <span data-ttu-id="5ddac-1871">Campo de información 3: identificador de la transacción</span><span class="sxs-lookup"><span data-stu-id="5ddac-1871">Info Field 3: Transaction ID.</span></span>
- <span data-ttu-id="5ddac-1872">Campo de información 4: parámetro 1</span><span class="sxs-lookup"><span data-stu-id="5ddac-1872">Info Field 4: Parameter1.</span></span>

### <a name="host-class-pima-number-objects-get"></a><span data-ttu-id="5ddac-1873">Obtención de número de objetos de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1873">Host Class Pima Number Objects Get</span></span> 

#### <a name="ux_host_class_pima_number_objects_get"></a><span data-ttu-id="5ddac-1874">ux_host_class_pima_number_objects_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1874">ux_host_class_pima_number_objects_get</span></span>

<span data-ttu-id="5ddac-1875">**Icono** ![Icono de obtención de número de objetos de clase PIMA de host](./media/user-guide/usbx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1875">**Icon** ![Host Class Pima Number Objects Get icon](./media/user-guide/usbx-events/image134.png)</span></span>

<span data-ttu-id="5ddac-1876">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1876">**Description**</span></span>

<span data-ttu-id="5ddac-1877">Este evento representa un evento de obtención de número de objetos de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1877">This event represents a USBX Host Class Pima Number Objects Get Event.</span></span>

<span data-ttu-id="5ddac-1878">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1878">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1879">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1879">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1880">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1880">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1881">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1881">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1882">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1882">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-close"></a><span data-ttu-id="5ddac-1883">Cierre de objeto de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1883">Host Class Pima Object Close</span></span> 

#### <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="5ddac-1884">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="5ddac-1884">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="5ddac-1885">**Icono** ![Icono de cierre de objeto de clase PIMA de host](./media/user-guide/usbx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1885">**Icon** ![Host Class Pima Object Close icon](./media/user-guide/usbx-events/image135.png)</span></span>

<span data-ttu-id="5ddac-1886">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1886">**Description**</span></span>

<span data-ttu-id="5ddac-1887">Este evento representa un evento de cierre de objeto de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1887">This event represents a USBX Host Class Pima Object Close Event.</span></span>

<span data-ttu-id="5ddac-1888">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1888">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1889">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1889">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1890">Campo de información 2: objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1890">Info Field 2: Object.</span></span>
- <span data-ttu-id="5ddac-1891">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1891">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1892">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1892">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-copy"></a><span data-ttu-id="5ddac-1893">Copia de objeto de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1893">Host Class Pima Object Copy</span></span> 

#### <a name="ux_host_class_pima_object_copy"></a><span data-ttu-id="5ddac-1894">ux_host_class_pima_object_copy</span><span class="sxs-lookup"><span data-stu-id="5ddac-1894">ux_host_class_pima_object_copy</span></span>

<span data-ttu-id="5ddac-1895">**Icono** ![Icono de copia de objeto de clase PIMA de host](./media/user-guide/usbx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1895">**Icon** ![Host Class Pima Object Copy icon](./media/user-guide/usbx-events/image136.png)</span></span>

<span data-ttu-id="5ddac-1896">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1896">**Description**</span></span>

<span data-ttu-id="5ddac-1897">Este evento representa un evento de copia de objeto de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1897">This event represents a USBX Host Class Pima Object Copy Event.</span></span>

<span data-ttu-id="5ddac-1898">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1898">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1899">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1899">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1900">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1900">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-1901">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1901">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1902">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1902">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-delete"></a><span data-ttu-id="5ddac-1903">Eliminación de objeto de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1903">Host Class Pima Object Delete</span></span> 

#### <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="5ddac-1904">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="5ddac-1904">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="5ddac-1905">**Icono** ![Icono de eliminación de objeto de clase PIMA de host](./media/user-guide/usbx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1905">**Icon** ![Host Class Pima Object Delete icon](./media/user-guide/usbx-events/image137.png)</span></span>

<span data-ttu-id="5ddac-1906">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1906">**Description**</span></span>

<span data-ttu-id="5ddac-1907">Este evento representa un evento de eliminación de objeto de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1907">This event represents a USBX Host Class Pima Object Delete Event.</span></span>

<span data-ttu-id="5ddac-1908">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1908">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1909">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1909">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1910">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1910">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-1911">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1911">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1912">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1912">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-get"></a><span data-ttu-id="5ddac-1913">Obtención de objeto de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1913">Host Class Pima Object Get</span></span> 

#### <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="5ddac-1914">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1914">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="5ddac-1915">**Icono** ![Icono de obtención de objeto de clase PIMA de host](./media/user-guide/usbx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1915">**Icon** ![Host Class Pima Object Get icon](./media/user-guide/usbx-events/image138.png)</span></span>

<span data-ttu-id="5ddac-1916">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1916">**Description**</span></span>

<span data-ttu-id="5ddac-1917">Este evento representa la obtención de información de RARP por medio de nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1917">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="5ddac-1918">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1918">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1919">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1919">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1920">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1920">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-1921">Campo de información 3: objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1921">Info Field 3: Object.</span></span>
- <span data-ttu-id="5ddac-1922">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1922">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-get"></a><span data-ttu-id="5ddac-1923">Obtención de información de objeto de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1923">Host Class Pima Object Info Get</span></span> 

#### <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="5ddac-1924">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-1924">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="5ddac-1925">**Icono** ![Icono de obtención de información de objeto de clase PIMA de host](./media/user-guide/usbx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1925">**Icon** ![Host Class Pima Object Info Get icon](./media/user-guide/usbx-events/image139.png)</span></span>

<span data-ttu-id="5ddac-1926">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1926">**Description**</span></span>

<span data-ttu-id="5ddac-1927">Este evento representa un evento de obtención de información de objeto de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1927">This event represents a USBX Host Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="5ddac-1928">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1928">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1929">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1929">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1930">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1930">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-1931">Campo de información 3: objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1931">Info Field 3: Object.</span></span>
- <span data-ttu-id="5ddac-1932">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1932">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-send"></a><span data-ttu-id="5ddac-1933">Envío de información de objeto de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1933">Host Class Pima Object Info Send</span></span> 

#### <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="5ddac-1934">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="5ddac-1934">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="5ddac-1935">**Icono** ![Icono de envío de información de objeto de clase PIMA de host](./media/user-guide/usbx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1935">**Icon** ![Host Class Pima Object Info Send icon](./media/user-guide/usbx-events/image140.png)</span></span>

<span data-ttu-id="5ddac-1936">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1936">**Description**</span></span>

<span data-ttu-id="5ddac-1937">Este evento representa un evento de envío de información de objeto de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1937">This event represents a USBX Host Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="5ddac-1938">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1938">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1939">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1939">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1940">Campo de información 2: objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1940">Info Field 2: Object.</span></span>
- <span data-ttu-id="5ddac-1941">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1941">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1942">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1942">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-move"></a><span data-ttu-id="5ddac-1943">Movimiento de objeto de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1943">Host Class Pima Object Move</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="5ddac-1944">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="5ddac-1944">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="5ddac-1945">**Icono** ![Icono de movimiento de objeto de clase PIMA de host](./media/user-guide/usbx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1945">**Icon** ![Host Class Pima Object Move icon](./media/user-guide/usbx-events/image141.png)</span></span>

<span data-ttu-id="5ddac-1946">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1946">**Description**</span></span>

<span data-ttu-id="5ddac-1947">Este evento representa un evento de movimiento de objeto de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1947">This event reprThis event represents a USBX Host Class Pima Object Move Event.</span></span>

<span data-ttu-id="5ddac-1948">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1948">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1949">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1949">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1950">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1950">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-1951">Campo de información 3: objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1951">Info Field 3: Object.</span></span>
- <span data-ttu-id="5ddac-1952">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1952">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-send"></a><span data-ttu-id="5ddac-1953">Envío de objeto de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1953">Host Class Pima Object Send</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="5ddac-1954">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="5ddac-1954">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="5ddac-1955">**Icono** ![Icono de envío de objeto de clase PIMA de host](./media/user-guide/usbx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1955">**Icon** ![Host Class Pima Object Send icon](./media/user-guide/usbx-events/image142.png)</span></span>

<span data-ttu-id="5ddac-1956">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1956">**Description**</span></span>

<span data-ttu-id="5ddac-1957">Este evento representa un evento de envío de objeto de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1957">This event represents a USBX Host Class Pima Object Send Event.</span></span>

<span data-ttu-id="5ddac-1958">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1958">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1959">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1959">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1960">Campo de información 2: objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1960">Info Field 2: Object.</span></span>
- <span data-ttu-id="5ddac-1961">Campo de información 3: búfer de objetos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1961">Info Field 3: Object buffer.</span></span>
- <span data-ttu-id="5ddac-1962">Campo de información 4: longitud del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1962">Info Field 4: Object length.</span></span>

### <a name="host-class-pima-object-transfer-abort"></a><span data-ttu-id="5ddac-1963">Anulación de transferencia de objeto de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1963">Host Class Pima Object Transfer Abort</span></span> 

#### <a name="ux_host_class_pima_object_transfer_abort"></a><span data-ttu-id="5ddac-1964">ux_host_class_pima_object_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="5ddac-1964">ux_host_class_pima_object_transfer_abort</span></span>

<span data-ttu-id="5ddac-1965">**Icono** ![Icono de anulación de transferencia de objeto de clase PIMA de host](./media/user-guide/usbx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1965">**Icon** ![Host Class Pima Object Transfer Abort icon](./media/user-guide/usbx-events/image143.png)</span></span>

<span data-ttu-id="5ddac-1966">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1966">**Description**</span></span>

<span data-ttu-id="5ddac-1967">Este evento representa un evento de anulación de transferencia de objeto de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1967">This event represents a USBX Host Class Pima Object Transfer Abort Event.</span></span>

<span data-ttu-id="5ddac-1968">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1968">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1969">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1969">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1970">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1970">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-1971">Campo de información 3: objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-1971">Info Field 3: Object.</span></span>
- <span data-ttu-id="5ddac-1972">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1972">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-read"></a><span data-ttu-id="5ddac-1973">Lectura de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1973">Host Class Pima Read</span></span> 

#### <a name="ux_host_class_pima_read"></a><span data-ttu-id="5ddac-1974">ux_host_class_pima_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-1974">ux_host_class_pima_read</span></span>

<span data-ttu-id="5ddac-1975">**Icono** ![Icono de lectura de clase PIMA de host](./media/user-guide/usbx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1975">**Icon** ![Host Class Pima Read icon](./media/user-guide/usbx-events/image144.png)</span></span>

<span data-ttu-id="5ddac-1976">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1976">**Description**</span></span>

<span data-ttu-id="5ddac-1977">Este evento representa un evento de lectura de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1977">This event represents a USBX Host Class Pima Read Event.</span></span>

<span data-ttu-id="5ddac-1978">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1978">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1979">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1979">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1980">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1980">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-1981">Campo de información 3: longitud de los datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-1981">Info Field 3: Data length.</span></span>
- <span data-ttu-id="5ddac-1982">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1982">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-request-cancel"></a><span data-ttu-id="5ddac-1983">Cancelación de solicitud de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1983">Host Class Pima Request Cancel</span></span> 

#### <a name="ux_host_class_pima_request_cancel"></a><span data-ttu-id="5ddac-1984">ux_host_class_pima_request_cancel</span><span class="sxs-lookup"><span data-stu-id="5ddac-1984">ux_host_class_pima_request_cancel</span></span>

<span data-ttu-id="5ddac-1985">**Icono** ![Icono de cancelación de solicitud de clase PIMA de host](./media/user-guide/usbx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1985">**Icon** ![Host Class Pima Request Cancel icon](./media/user-guide/usbx-events/image145.png)</span></span>

<span data-ttu-id="5ddac-1986">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1986">**Description**</span></span>

<span data-ttu-id="5ddac-1987">Este evento representa un evento de cancelación de solicitud de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1987">This event represents a USBX Host Class Pima Request Cancel Event.</span></span>

<span data-ttu-id="5ddac-1988">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1988">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1989">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1989">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-1990">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1990">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-1991">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1991">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-1992">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-1992">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-close"></a><span data-ttu-id="5ddac-1993">Cierre de sesión de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-1993">Host Class Pima Session Close</span></span> 

#### <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="5ddac-1994">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="5ddac-1994">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="5ddac-1995">**Icono** ![Icono de cierre de sesión de clase PIMA de host](./media/user-guide/usbx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-1995">**Icon** ![Host Class Pima Session Close icon](./media/user-guide/usbx-events/image146.png)</span></span>

<span data-ttu-id="5ddac-1996">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1996">**Description**</span></span>

<span data-ttu-id="5ddac-1997">Este evento representa un evento de cierre de sesión de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-1997">This event represents a USBX Host Class Pima Session Close Event.</span></span>

<span data-ttu-id="5ddac-1998">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-1998">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-1999">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-1999">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2000">Campo de información 2: sesión de PIMA</span><span class="sxs-lookup"><span data-stu-id="5ddac-2000">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="5ddac-2001">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2001">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2002">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2002">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-open"></a><span data-ttu-id="5ddac-2003">Apertura de sesión de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2003">Host Class Pima Session Open</span></span> 

#### <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="5ddac-2004">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="5ddac-2004">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="5ddac-2005">**Icono** ![Icono de apertura de sesión de clase PIMA de host](./media/user-guide/usbx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2005">**Icon** ![Host Class Pima Session Open icon](./media/user-guide/usbx-events/image147.png)</span></span>

<span data-ttu-id="5ddac-2006">**Descripción** Este evento representa un evento de apertura de sesión de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2006">**Description** This event represents a USBX Host Class Pima Session Open Event.</span></span>

<span data-ttu-id="5ddac-2007">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2007">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2008">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2008">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2009">Campo de información 2: sesión de PIMA</span><span class="sxs-lookup"><span data-stu-id="5ddac-2009">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="5ddac-2010">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2010">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2011">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2011">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-ids-get"></a><span data-ttu-id="5ddac-2012">Obtención de identificadores de almacenamiento de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2012">Host Class Pima Storage Ids Get</span></span> 

#### <a name="ux_host_class_pima_session_ids_get"></a><span data-ttu-id="5ddac-2013">ux_host_class_pima_session_ids_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2013">ux_host_class_pima_session_ids_get</span></span>

<span data-ttu-id="5ddac-2014">**Icono** ![Icono de obtención de identificadores de almacenamiento de clase PIMA de host](./media/user-guide/usbx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2014">**Icon** ![Host Class Pima Storage Ids Get icon](./media/user-guide/usbx-events/image148.png)</span></span>

<span data-ttu-id="5ddac-2015">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2015">**Description**</span></span>

<span data-ttu-id="5ddac-2016">Este evento representa un evento de obtención de identificadores de almacenamiento de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2016">This event represents a USBX Host Class Pima Storage Ids Get Event.</span></span>

<span data-ttu-id="5ddac-2017">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2017">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2018">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2018">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2019">Campo de información 2: matriz de identificadores de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="5ddac-2019">nfo Field 2: Storage ID array.</span></span>
- <span data-ttu-id="5ddac-2020">Campo de información 3: longitud de identificador de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="5ddac-2020">Info Field 3: Storage ID length.</span></span>
<span data-ttu-id="5ddac-2021">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2021">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-info-get"></a><span data-ttu-id="5ddac-2022">Obtención de información de almacenamiento de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2022">Host Class Pima Storage Info Get</span></span> 

#### <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="5ddac-2023">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2023">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="5ddac-2024">**Icono** ![Icono de obtención de información de almacenamiento de clase PIMA de host](./media/user-guide/usbx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2024">**Icon** ![Host Class Pima Storage Info Get icon](./media/user-guide/usbx-events/image149.png)</span></span>

<span data-ttu-id="5ddac-2025">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2025">**Description**</span></span>

<span data-ttu-id="5ddac-2026">Este evento representa un evento de obtención de información de almacenamiento de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2026">This event represents a USBX Host Class Pima Storage Info Get Event.</span></span>

<span data-ttu-id="5ddac-2027">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2027">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2028">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2028">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2029">Campo de información 2: identificador de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="5ddac-2029">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="5ddac-2030">Campo de información 3: almacenamiento</span><span class="sxs-lookup"><span data-stu-id="5ddac-2030">Info Field 3: Storage.</span></span>
- <span data-ttu-id="5ddac-2031">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2031">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-thumb-get"></a><span data-ttu-id="5ddac-2032">Obtención de miniatura de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2032">Host Class Pima Thumb Get</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="5ddac-2033">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2033">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="5ddac-2034">**Icono** ![Icono de obtención de miniatura de clase PIMA de host](./media/user-guide/usbx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2034">**Icon** ![Host Class Pima Thumb Get icon](./media/user-guide/usbx-events/image150.png)</span></span>

<span data-ttu-id="5ddac-2035">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2035">**Description**</span></span>

<span data-ttu-id="5ddac-2036">Este evento representa la desaceptación de una conexión de servidor TCP por medio de nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2036">This event represents unaccepting a TCP server connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="5ddac-2037">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2037">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-2038">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2038">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2039">Campo de información 2: identificador del objeto</span><span class="sxs-lookup"><span data-stu-id="5ddac-2039">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="5ddac-2040">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2040">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2041">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2041">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-write"></a><span data-ttu-id="5ddac-2042">Escritura de clase PIMA de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2042">Host Class Pima Write</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="5ddac-2043">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2043">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="5ddac-2044">**Icono** ![Icono de escritura de clase PIMA de host](./media/user-guide/usbx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2044">**Icon** ![Host Class Pima Write icon](./media/user-guide/usbx-events/image151.png)</span></span>

<span data-ttu-id="5ddac-2045">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2045">**Description**</span></span>

<span data-ttu-id="5ddac-2046">Este evento representa un evento de escritura de la clase PIMA del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2046">This event represents a USBX Host Class Pima Write.</span></span>

<span data-ttu-id="5ddac-2047">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2047">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2048">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2048">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="5ddac-2049">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-2049">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-2050">Campo de información 3: longitud de los datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-2050">Info Field 3: Data length.</span></span>
- <span data-ttu-id="5ddac-2051">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2051">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-activate"></a><span data-ttu-id="5ddac-2052">Activación de clase PRINTER de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2052">Host Class Printer Activate</span></span> 

#### <a name="ux_host_class_printer_activate"></a><span data-ttu-id="5ddac-2053">ux_host_class_printer_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-2053">ux_host_class_printer_activate</span></span>

<span data-ttu-id="5ddac-2054">**Icono** ![Icono de activación de clase PRINTER de host](./media/user-guide/usbx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2054">**Icon** ![Host Class Printer Activate icon](./media/user-guide/usbx-events/image152.png)</span></span>

<span data-ttu-id="5ddac-2055">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2055">**Description**</span></span>

<span data-ttu-id="5ddac-2056">Este evento representa un evento de activación de la clase PRINTER del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2056">This event represents a USBX Host Class Printer Activate Event.</span></span>

<span data-ttu-id="5ddac-2057">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2057">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2058">Campo de información 1: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="5ddac-2058">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="5ddac-2059">Campo de información 2: puntero al socket</span><span class="sxs-lookup"><span data-stu-id="5ddac-2059">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="5ddac-2060">Campo de información 3: tipo de servicio</span><span class="sxs-lookup"><span data-stu-id="5ddac-2060">Info Field 3: Type of service.</span></span>
- <span data-ttu-id="5ddac-2061">Campo de información 4: tamaño de la ventana de recepción</span><span class="sxs-lookup"><span data-stu-id="5ddac-2061">Info Field 4: Receive window size.</span></span>

### <a name="host-class-printer-deactivate"></a><span data-ttu-id="5ddac-2062">Desactivación de clase PRINTER de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2062">Host Class Printer Deactivate</span></span> 

#### <a name="ux_host_class_printer_deactivate"></a><span data-ttu-id="5ddac-2063">ux_host_class_printer_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-2063">ux_host_class_printer_deactivate</span></span>

<span data-ttu-id="5ddac-2064">**Icono** ![Icono de desactivación de clase PRINTER de host](./media/user-guide/usbx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2064">**Icon** ![Host Class Printer Deactivate icon](./media/user-guide/usbx-events/image153.png)</span></span>

<span data-ttu-id="5ddac-2065">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2065">**Description**</span></span>

<span data-ttu-id="5ddac-2066">Este evento representa un evento de desactivación de la clase PRINTER del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2066">This event represents a USBX Host Class Printer Deactivate Event.</span></span>

<span data-ttu-id="5ddac-2067">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2067">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2068">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2068">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2069">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2069">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2070">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2070">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2071">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2071">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-name-get"></a><span data-ttu-id="5ddac-2072">Obtención de nombre de clase PRINTER de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2072">Host Class Printer Name Get</span></span> 

#### <a name="ux_host_class_printer_name_get"></a><span data-ttu-id="5ddac-2073">ux_host_class_printer_name_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2073">ux_host_class_printer_name_get</span></span>

<span data-ttu-id="5ddac-2074">**Icono** ![Icono de obtención de nombre de clase PRINTER de host](./media/user-guide/usbx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2074">**Icon** ![Host Class Printer Name Get icon](./media/user-guide/usbx-events/image154.png)</span></span>

<span data-ttu-id="5ddac-2075">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2075">**Description**</span></span>

<span data-ttu-id="5ddac-2076">Este evento representa un evento de obtención de nombre de la clase PRINTER del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2076">This event represents a USBX Host Class Printer Name Get Event.</span></span>

<span data-ttu-id="5ddac-2077">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2077">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-2078">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2078">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2079">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2079">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2080">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2080">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2081">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2081">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-read"></a><span data-ttu-id="5ddac-2082">Lectura de clase PRINTER de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2082">Host Class Printer Read</span></span> 

#### <a name="ux_host_class_printer_read"></a><span data-ttu-id="5ddac-2083">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-2083">ux_host_class_printer_read</span></span>

<span data-ttu-id="5ddac-2084">**Icono** ![Icono de lectura de clase PRINTER de host](./media/user-guide/usbx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2084">**Icon** ![Host Class Printer Read icon](./media/user-guide/usbx-events/image155.png)</span></span>

<span data-ttu-id="5ddac-2085">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2085">**Description**</span></span>

<span data-ttu-id="5ddac-2086">Este evento representa un evento de lectura de la clase PRINTER del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2086">This event represents a USBX Host Class Printer Read Event.</span></span>

<span data-ttu-id="5ddac-2087">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2087">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2088">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2088">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2089">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-2089">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-2090">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-2090">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-2091">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2091">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-soft-reset"></a><span data-ttu-id="5ddac-2092">Restablecimiento parcial de clase PRINTER de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2092">Host Class Printer Soft Reset</span></span> 

#### <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="5ddac-2093">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="5ddac-2093">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="5ddac-2094">**Icono** ![Icono de restablecimiento parcial de clase PRINTER de host](./media/user-guide/usbx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2094">**Icon** ![Host Class Printer Soft Reset icon](./media/user-guide/usbx-events/image156.png)</span></span>

<span data-ttu-id="5ddac-2095">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2095">**Description**</span></span>

<span data-ttu-id="5ddac-2096">Este evento representa un evento de restablecimiento parcial de la clase PRINTER del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2096">This event represents a USBX Host Class Printer Soft Reset Event.</span></span>

<span data-ttu-id="5ddac-2097">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2097">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2098">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2098">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2099">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2099">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2100">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2100">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2101">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2101">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-status-get"></a><span data-ttu-id="5ddac-2102">Obtención de estado de clase PRINTER de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2102">Host Class Printer Status Get</span></span> 

#### <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="5ddac-2103">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2103">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="5ddac-2104">**Icono** ![Icono de obtención de estado de clase PRINTER de host](./media/user-guide/usbx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2104">**Icon** ![Host Class Printer Status Get icon](./media/user-guide/usbx-events/image157.png)</span></span>

<span data-ttu-id="5ddac-2105">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2105">**Description**</span></span>

<span data-ttu-id="5ddac-2106">Este evento representa un evento de obtención de estado de la clase PRINTER del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2106">This event represents a USBX Host Class Printer Status Get Event.</span></span>

<span data-ttu-id="5ddac-2107">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2107">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2108">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2108">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2109">Campo de información 2: estado de la impresora</span><span class="sxs-lookup"><span data-stu-id="5ddac-2109">Info Field 2: Printer status.</span></span>
- <span data-ttu-id="5ddac-2110">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2110">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2111">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2111">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-write"></a><span data-ttu-id="5ddac-2112">Escritura de clase PRINTER de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2112">Host Class Printer Write</span></span> 

#### <a name="ux_host_class_printer_write"></a><span data-ttu-id="5ddac-2113">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-2113">ux_host_class_printer_write</span></span>

<span data-ttu-id="5ddac-2114">**Icono** ![Icono de escritura de clase PRINTER de host](./media/user-guide/usbx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2114">**Icon** ![Host Class Printer Write icon](./media/user-guide/usbx-events/image158.png)</span></span>

<span data-ttu-id="5ddac-2115">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2115">**Description**</span></span>

<span data-ttu-id="5ddac-2116">Este evento representa un evento de escritura de la clase PRINTER del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2116">This event represents a USBX Host Class Printer Write.</span></span>

<span data-ttu-id="5ddac-2117">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2117">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-2118">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2118">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2119">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-2119">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-2120">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-2120">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-2121">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2121">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-activate"></a><span data-ttu-id="5ddac-2122">Activación de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2122">Host Class Prolific Activate</span></span> 

#### <a name="ux_host_class_prolific_activate"></a><span data-ttu-id="5ddac-2123">ux_host_class_prolific_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-2123">ux_host_class_prolific_activate</span></span> 

<span data-ttu-id="5ddac-2124">**Icono** ![Icono de activación de clase PROLIFIC de host](./media/user-guide/usbx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2124">**Icon** ![Host Class Prolific Activate icon](./media/user-guide/usbx-events/image159.png)</span></span>

<span data-ttu-id="5ddac-2125">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2125">**Description**</span></span>

<span data-ttu-id="5ddac-2126">Este evento representa un evento de activación de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2126">This event represents a USBX Host Class Prolific Activate Event.</span></span>

<span data-ttu-id="5ddac-2127">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2127">**Information Fields**</span></span> 

- <span data-ttu-id="5ddac-2128">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2128">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2129">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2129">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2130">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2130">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2131">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2131">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-deactivate"></a><span data-ttu-id="5ddac-2132">Desactivación de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2132">Host Class Prolific Deactivate</span></span> 

#### <a name="ux_host_class_prolific_deactivate"></a><span data-ttu-id="5ddac-2133">ux_host_class_prolific_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-2133">ux_host_class_prolific_deactivate</span></span> 

<span data-ttu-id="5ddac-2134">**Icono** ![Icono de desactivación de clase PROLIFIC de host](./media/user-guide/usbx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2134">**Icon** ![Host Class Prolific Deactivate icon](./media/user-guide/usbx-events/image160.png)</span></span>

<span data-ttu-id="5ddac-2135">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2135">**Description**</span></span>

<span data-ttu-id="5ddac-2136">Este evento representa un evento de desactivación de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2136">This event represents a USBX Host Class Prolific Deactivate Event.</span></span>

<span data-ttu-id="5ddac-2137">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2137">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2138">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2138">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2139">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2139">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2140">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2140">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2141">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2141">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a><span data-ttu-id="5ddac-2142">Función IOCTL de anulación de canalización de entrada de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2142">Host Class Prolific Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a><span data-ttu-id="5ddac-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="5ddac-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="5ddac-2144">**Icono** ![Icono de función I O C T L de anulación de canalización de entrada de clase PROLIFIC de host](./media/user-guide/usbx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2144">**Icon** ![Host Class Prolific I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image161.png)</span></span>

<span data-ttu-id="5ddac-2145">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2145">**Description**</span></span>

<span data-ttu-id="5ddac-2146">Este evento representa un evento de una función IOCTL de anulación de canalización de entrada de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2146">This event represents a USBX Host Class Prolific Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="5ddac-2147">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2147">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2148">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2148">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2149">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2149">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-2150">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2150">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2151">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2151">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a><span data-ttu-id="5ddac-2152">Función IOCTL de anulación de canalización de salida de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2152">Host Class Prolific Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a><span data-ttu-id="5ddac-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="5ddac-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span></span>

<span data-ttu-id="5ddac-2154">**Icono** ![Icono de función I O C T L de anulación de canalización de salida de clase PROLIFIC de host](./media/user-guide/usbx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2154">**Icon** ![Host Class Prolific I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image162.png)</span></span>

<span data-ttu-id="5ddac-2155">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2155">**Description**</span></span>

<span data-ttu-id="5ddac-2156">Este evento representa un evento de una función IOCTL de anulación de canalización de salida de la clase PROLIFIC de host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2156">This event represents a USBX Host Class Prolific Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="5ddac-2157">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2157">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2158">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2158">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2159">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2159">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-2160">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2160">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2161">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2161">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-device-status"></a><span data-ttu-id="5ddac-2162">Función IOCTL de obtención de estado de dispositivo de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2162">Host Class Prolific Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a><span data-ttu-id="5ddac-2163">ux_host_class_prolific_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="5ddac-2163">ux_host_class_prolific_ioctl_get_device_status</span></span>

<span data-ttu-id="5ddac-2164">**Icono** ![Icono de función I O C T L de obtención de estado de dispositivo de clase PROLIFIC de host](./media/user-guide/usbx-events/image163.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2164">**Icon** ![Host Class Prolific I O C T L Get Device Status icon](./media/user-guide/usbx-events/image163.png)</span></span>

<span data-ttu-id="5ddac-2165">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2165">**Description**</span></span>

<span data-ttu-id="5ddac-2166">Este evento representa un evento de una función IOCTL de obtención de estado de dispositivo de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2166">This event represents a USBX Host Class Prolific Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="5ddac-2167">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2167">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2168">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2168">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2169">Campo de información 2: estado del dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2169">Info Field 2: Device status.</span></span>
- <span data-ttu-id="5ddac-2170">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2170">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2171">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2171">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-line-coding"></a><span data-ttu-id="5ddac-2172">Función IOCTL de obtención de codificación de línea de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2172">Host Class Prolific Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a><span data-ttu-id="5ddac-2173">ux_host_class_prolific_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="5ddac-2173">ux_host_class_prolific_ioctl_get_line_coding</span></span>

<span data-ttu-id="5ddac-2174">**Icono** ![Icono de función I O C T L de obtención de codificación de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2174">**Icon** ![Host Class Prolific I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image164.png)</span></span>

<span data-ttu-id="5ddac-2175">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2175">**Description**</span></span>

<span data-ttu-id="5ddac-2176">Este evento representa un evento de una función IOCTL de obtención de codificación de línea de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2176">This event represents a USBX Host Class Prolific Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="5ddac-2177">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2177">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2178">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2178">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2179">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-2179">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-2180">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2180">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2181">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2181">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-purge"></a><span data-ttu-id="5ddac-2182">Función IOCTL de depuración de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2182">Host Class Prolific Ioctl Purge</span></span> 

#### <a name="ux_host_class_prolific_ioctl_purge"></a><span data-ttu-id="5ddac-2183">ux_host_class_prolific_ioctl_purge</span><span class="sxs-lookup"><span data-stu-id="5ddac-2183">ux_host_class_prolific_ioctl_purge</span></span>

<span data-ttu-id="5ddac-2184">**Icono** ![Icono de función I O C T L de depuración de clase PROLIFIC de host](./media/user-guide/usbx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2184">**Icon** ![Host Class Prolific Ioctl Purge icon](./media/user-guide/usbx-events/image165.png)</span></span>

<span data-ttu-id="5ddac-2185">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2185">**Description**</span></span>

<span data-ttu-id="5ddac-2186">Este evento representa un evento de una función IOCTL de depuración de la clase PROLIFIC de host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2186">This event represents a USBX Host Class Prolific Ioctl Purge Event.</span></span>

<span data-ttu-id="5ddac-2187">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2187">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2188">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2188">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2189">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-2189">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-2190">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2190">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2191">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2191">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-report-device"></a><span data-ttu-id="5ddac-2192">Función IOCTL de informe de dispositivo de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2192">Host Class Prolific Ioctl Report Device</span></span> 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a><span data-ttu-id="5ddac-2193">ux_host_class_prolific_ioctl_report_device</span><span class="sxs-lookup"><span data-stu-id="5ddac-2193">ux_host_class_prolific_ioctl_report_device</span></span>

<span data-ttu-id="5ddac-2194">**Icono** ![Icono de función I O C T L de informe de cambio de estado de dispositivo de clase PROLIFIC de host](./media/user-guide/usbx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2194">**Icon** ![Host Class Prolific I O C T L Report Device icon](./media/user-guide/usbx-events/image166.png)</span></span>

<span data-ttu-id="5ddac-2195">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2195">**Description**</span></span>

<span data-ttu-id="5ddac-2196">Este evento representa un evento de una función IOCTL de informe del cambio de estado del dispositivo de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2196">This event represents a USBX Host Class Prolific Ioctl Report Device Status Change Event.</span></span>

<span data-ttu-id="5ddac-2197">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2197">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2198">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2198">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2199">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-2199">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-2200">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2200">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2201">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2201">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-send-break"></a><span data-ttu-id="5ddac-2202">Función IOCTL de interrupción de envío de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2202">Host Class Prolific Ioctl Send Break</span></span> 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a><span data-ttu-id="5ddac-2203">ux_host_class_prolific_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="5ddac-2203">ux_host_class_prolific_ioctl_send_break</span></span>

<span data-ttu-id="5ddac-2204">**Icono** ![Icono de función I O C T L de interrupción de envío de clase PROLIFIC de host](./media/user-guide/usbx-events/image167.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2204">**Icon** ![Host Class Prolific I O C T L Send Break icon](./media/user-guide/usbx-events/image167.png)</span></span>

<span data-ttu-id="5ddac-2205">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2205">**Description**</span></span>

<span data-ttu-id="5ddac-2206">Este evento representa un evento de una función IOCTL de interrupción de envío de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2206">This event represents a USBX Host Class Prolific Ioctl Send Break Event.</span></span>

<span data-ttu-id="5ddac-2207">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2207">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2208">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2208">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2209">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2209">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2210">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2210">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2211">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2211">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-coding"></a><span data-ttu-id="5ddac-2212">Función IOCTL de establecimiento de codificación de línea de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2212">Host Class Prolific Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a><span data-ttu-id="5ddac-2213">ux_host_class_prolific_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="5ddac-2213">ux_host_class_prolific_ioctl_set_line_coding</span></span>

<span data-ttu-id="5ddac-2214">**Icono** ![Icono de función I O C T L de establecimiento de codificación de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image168.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2214">**Icon** ![Host Class Prolific I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image168.png)</span></span>

<span data-ttu-id="5ddac-2215">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2215">**Description**</span></span>

<span data-ttu-id="5ddac-2216">Este evento representa un evento de una función IOCTL de establecimiento de codificación de línea de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2216">This event represents a USBX Host Class Prolific Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="5ddac-2217">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2217">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2218">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2218">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2219">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-2219">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-2220">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2220">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2221">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2221">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-state"></a><span data-ttu-id="5ddac-2222">Función IOCTL de establecimiento de estado de línea de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2222">Host Class Prolific Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a><span data-ttu-id="5ddac-2223">ux_host_class_prolific_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="5ddac-2223">ux_host_class_prolific_ioctl_set_line_state</span></span>

<span data-ttu-id="5ddac-2224">**Icono** ![Icono de función I O C T L de establecimiento de estado de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image169.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2224">**Icon** ![Host Class Prolific I O C T L Set Line State icon](./media/user-guide/usbx-events/image169.png)</span></span>

<span data-ttu-id="5ddac-2225">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2225">**Description**</span></span>

<span data-ttu-id="5ddac-2226">Este evento representa un evento de una función IOCTL de establecimiento de estado de línea de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2226">This event represents a USBX Host Class Prolific Ioctl Set Line State Event.</span></span>

<span data-ttu-id="5ddac-2227">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2227">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2228">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2228">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2229">Campo de información 2: parámetro</span><span class="sxs-lookup"><span data-stu-id="5ddac-2229">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="5ddac-2230">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2230">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2231">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2231">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-read"></a><span data-ttu-id="5ddac-2232">Lectura de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2232">Host Class Prolific Read</span></span> 

#### <a name="ux_host_class_prolific_read"></a><span data-ttu-id="5ddac-2233">ux_host_class_prolific_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-2233">ux_host_class_prolific_read</span></span>

<span data-ttu-id="5ddac-2234">**Icono** ![Icono de lectura de clase PROLIFIC de host](./media/user-guide/usbx-events/image170.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2234">**Icon** ![Host Class Prolific Read icon](./media/user-guide/usbx-events/image170.png)</span></span>

<span data-ttu-id="5ddac-2235">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2235">**Description**</span></span>

<span data-ttu-id="5ddac-2236">Este evento representa un evento de lectura de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2236">This event represents a USBX Host Class Prolific Read Event.</span></span>

<span data-ttu-id="5ddac-2237">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2237">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2238">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2238">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2239">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-2239">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-2240">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-2240">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-2241">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2241">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-start"></a><span data-ttu-id="5ddac-2242">Inicio de recepción de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2242">Host Class Prolific Reception Start</span></span> 

#### <a name="ux_host_class_prolific_reception_start"></a><span data-ttu-id="5ddac-2243">ux_host_class_prolific_reception_start</span><span class="sxs-lookup"><span data-stu-id="5ddac-2243">ux_host_class_prolific_reception_start</span></span>

<span data-ttu-id="5ddac-2244">**Icono** ![Icono de inicio de recepción de clase PROLIFIC de host](./media/user-guide/usbx-events/image171.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2244">**Icon** ![Host Class Prolific Reception Start icon](./media/user-guide/usbx-events/image171.png)</span></span>

<span data-ttu-id="5ddac-2245">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2245">**Description**</span></span>

<span data-ttu-id="5ddac-2246">Este evento representa un evento de inicio de recepción de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2246">This event represents a USBX Host Class Prolific Reception Start Event.</span></span>

<span data-ttu-id="5ddac-2247">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2247">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2248">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2248">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2249">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2249">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2250">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2250">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2251">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2251">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-stop"></a><span data-ttu-id="5ddac-2252">Parada de recepción de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2252">Host Class Prolific Reception Stop</span></span> 

#### <a name="ux_host_class_prolific_reception_stop"></a><span data-ttu-id="5ddac-2253">ux_host_class_prolific_reception_stop</span><span class="sxs-lookup"><span data-stu-id="5ddac-2253">ux_host_class_prolific_reception_stop</span></span>

<span data-ttu-id="5ddac-2254">**Icono** ![Icono de parada de recepción de clase PROLIFIC de host](./media/user-guide/usbx-events/image172.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2254">**Icon** ![Host Class Prolific Reception Stop icon](./media/user-guide/usbx-events/image172.png)</span></span>

<span data-ttu-id="5ddac-2255">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2255">**Description**</span></span>

<span data-ttu-id="5ddac-2256">Este evento representa un evento de parada de recepción de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2256">This event represents a USBX Host Class Prolific Reception Stop Event.</span></span>

<span data-ttu-id="5ddac-2257">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2257">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2258">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2258">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2259">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2259">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2260">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2260">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2261">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2261">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-write"></a><span data-ttu-id="5ddac-2262">Escritura de clase PROLIFIC de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2262">Host Class Prolific Write</span></span> 

#### <a name="ux_host_class_prolific_write"></a><span data-ttu-id="5ddac-2263">ux_host_class_prolific_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-2263">ux_host_class_prolific_write</span></span>

<span data-ttu-id="5ddac-2264">**Icono** ![Icono de escritura de clase PROLIFIC de host](./media/user-guide/usbx-events/image173.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2264">**Icon** ![Host Class Prolific Write icon](./media/user-guide/usbx-events/image173.png)</span></span>

<span data-ttu-id="5ddac-2265">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2265">**Description**</span></span>

<span data-ttu-id="5ddac-2266">Este evento representa un evento de escritura de la clase PROLIFIC del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2266">This event represents a USBX Host Class Prolific Write Event.</span></span>

<span data-ttu-id="5ddac-2267">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2267">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2268">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2268">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2269">Campo de información 2: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-2269">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="5ddac-2270">Campo de información 3: longitud solicitada</span><span class="sxs-lookup"><span data-stu-id="5ddac-2270">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="5ddac-2271">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2271">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-activate"></a><span data-ttu-id="5ddac-2272">Activación de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2272">Host Class Storage Activate</span></span> 

#### <a name="ux_host_class_storage_activate"></a><span data-ttu-id="5ddac-2273">ux_host_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="5ddac-2273">ux_host_class_storage_activate</span></span>

<span data-ttu-id="5ddac-2274">**Icono** ![Icono de activación de clase STORAGE de host](./media/user-guide/usbx-events/image174.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2274">**Icon** ![Host Class Storage Activate icon](./media/user-guide/usbx-events/image174.png)</span></span>

<span data-ttu-id="5ddac-2275">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2275">**Description**</span></span>

<span data-ttu-id="5ddac-2276">Este evento representa un evento de activación de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2276">This event represents a USBX Host Class Storage Activate Event.</span></span>

<span data-ttu-id="5ddac-2277">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2277">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2278">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2278">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2279">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2279">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2280">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2280">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2281">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2281">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-deactivate"></a><span data-ttu-id="5ddac-2282">Desactivación de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2282">Host Class Storage Deactivate</span></span> 

#### <a name="ux_host_class_storage_deactivate"></a><span data-ttu-id="5ddac-2283">ux_host_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="5ddac-2283">ux_host_class_storage_deactivate</span></span>

<span data-ttu-id="5ddac-2284">**Icono** ![Icono de desactivación de clase STORAGE de host](./media/user-guide/usbx-events/image175.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2284">**Icon** ![Host Class Storage Deactivate icon](./media/user-guide/usbx-events/image175.png)</span></span>

<span data-ttu-id="5ddac-2285">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2285">**Description**</span></span>

<span data-ttu-id="5ddac-2286">Este evento representa un evento de desactivación de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2286">This event represents a USBX Host Class Storage Deactivate Event.</span></span>

<span data-ttu-id="5ddac-2287">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2287">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2288">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2288">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2289">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2289">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2290">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2290">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2291">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2291">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-capacity-get"></a><span data-ttu-id="5ddac-2292">Obtención de capacidad de soporte físico de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2292">Host Class Storage Media Capacity Get</span></span> 

#### <a name="ux_host_class_storage_media_capacity_get"></a><span data-ttu-id="5ddac-2293">ux_host_class_storage_media_capacity_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2293">ux_host_class_storage_media_capacity_get</span></span>

<span data-ttu-id="5ddac-2294">**Icono** ![Icono de obtención de capacidad de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image176.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2294">**Icon** ![Host Class Storage Media Capacity Get icon](./media/user-guide/usbx-events/image176.png)</span></span>

<span data-ttu-id="5ddac-2295">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2295">**Description**</span></span>

<span data-ttu-id="5ddac-2296">Este evento representa un evento de obtención de capacidad de soporte físico de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2296">This event represents a USBX Host Class Storage Media Capacity Get Event.</span></span>

<span data-ttu-id="5ddac-2297">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2297">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2298">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2298">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2299">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2299">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2300">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2300">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2301">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2301">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-format-capacity-get"></a><span data-ttu-id="5ddac-2302">Obtención de capacidad de formato de soporte físico de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2302">Host Class Storage Media Format Capacity Get</span></span>

#### <a name="ux_host_class_storage_media_format_capacity_get"></a><span data-ttu-id="5ddac-2303">ux_host_class_storage_media_format_capacity_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2303">ux_host_class_storage_media_format_capacity_get</span></span>

<span data-ttu-id="5ddac-2304">**Icono** ![Icono de obtención de capacidad de formato de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image177.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2304">**Icon** ![Host Class Storage Media Format Capacity Get icon](./media/user-guide/usbx-events/image177.png)</span></span>

<span data-ttu-id="5ddac-2305">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2305">**Description**</span></span>

<span data-ttu-id="5ddac-2306">Este evento representa un evento de obtención de capacidad de formato de soporte físico de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2306">This event represents a USBX Host Class Storage Media Format Capacity Get Event.</span></span>

<span data-ttu-id="5ddac-2307">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2307">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2308">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2308">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2309">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2309">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2310">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2310">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2311">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2311">Info Field 4: Not used.</span></span>

#### <a name="host-class-storage-media-mount"></a><span data-ttu-id="5ddac-2312">Montaje de soporte físico de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2312">Host Class Storage Media Mount</span></span> 

#### <a name="ux_host_class_storage_media_mount"></a><span data-ttu-id="5ddac-2313">ux_host_class_storage_media_mount</span><span class="sxs-lookup"><span data-stu-id="5ddac-2313">ux_host_class_storage_media_mount</span></span>

<span data-ttu-id="5ddac-2314">**Icono** ![Icono de montaje de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image178.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2314">**Icon** ![Host Class Storage Media Mount icon](./media/user-guide/usbx-events/image178.png)</span></span>

<span data-ttu-id="5ddac-2315">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2315">**Description**</span></span>

<span data-ttu-id="5ddac-2316">Este evento representa un evento de montaje de soporte físico de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2316">This event represents a USBX Host Class Storage Media Mount Event.</span></span>

<span data-ttu-id="5ddac-2317">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2317">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2318">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2318">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2319">Campo de información 2: sector</span><span class="sxs-lookup"><span data-stu-id="5ddac-2319">Info Field 2: Sector.</span></span>
- <span data-ttu-id="5ddac-2320">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2320">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2321">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2321">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-open"></a><span data-ttu-id="5ddac-2322">Apertura de soporte físico de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2322">Host Class Storage Media Open</span></span> 

#### <a name="ux_host_class_storage_media_open"></a><span data-ttu-id="5ddac-2323">ux_host_class_storage_media_open</span><span class="sxs-lookup"><span data-stu-id="5ddac-2323">ux_host_class_storage_media_open</span></span>

<span data-ttu-id="5ddac-2324">**Icono** ![Icono de apertura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image179.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2324">**Icon** ![Host Class Storage Media Open icon](./media/user-guide/usbx-events/image179.png)</span></span>

<span data-ttu-id="5ddac-2325">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2325">**Description**</span></span>

<span data-ttu-id="5ddac-2326">Este evento representa un evento de apertura de soporte físico de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2326">This event represents a USBX Host Class Storage Media Open Event.</span></span>

<span data-ttu-id="5ddac-2327">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2327">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2328">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2328">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2329">Campo de información 2: soporte físico</span><span class="sxs-lookup"><span data-stu-id="5ddac-2329">Info Field 2: Media.</span></span>
- <span data-ttu-id="5ddac-2330">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2330">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2331">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2331">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-read"></a><span data-ttu-id="5ddac-2332">Lectura de soporte físico de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2332">Host Class Storage Media Read</span></span> 

#### <a name="ux_host_class_storage_media_read"></a><span data-ttu-id="5ddac-2333">ux_host_class_storage_media_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-2333">ux_host_class_storage_media_read</span></span>

<span data-ttu-id="5ddac-2334">**Icono** ![Icono de lectura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image180.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2334">**Icon** ![Host Class Storage Media Read icon](./media/user-guide/usbx-events/image180.png)</span></span>

<span data-ttu-id="5ddac-2335">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2335">**Description**</span></span>

<span data-ttu-id="5ddac-2336">Este evento representa un evento de lectura de soporte físico de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2336">This event represents a USBX Host Class Storage Media Read Event.</span></span>

<span data-ttu-id="5ddac-2337">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2337">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2338">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2338">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2339">Campo de información 2: Inicio del sector</span><span class="sxs-lookup"><span data-stu-id="5ddac-2339">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="5ddac-2340">Campo de información 3: recuento de sectores</span><span class="sxs-lookup"><span data-stu-id="5ddac-2340">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="5ddac-2341">Campo de información 4: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-2341">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-media-write"></a><span data-ttu-id="5ddac-2342">Escritura de soporte físico de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2342">Host Class Storage Media Write</span></span> 

#### <a name="ux_host_class_storage_media_write"></a><span data-ttu-id="5ddac-2343">ux_host_class_storage_media_write</span><span class="sxs-lookup"><span data-stu-id="5ddac-2343">ux_host_class_storage_media_write</span></span>

<span data-ttu-id="5ddac-2344">**Icono** ![Icono de escritura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image181.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2344">**Icon** ![Host Class Storage Media Write icon](./media/user-guide/usbx-events/image181.png)</span></span>

<span data-ttu-id="5ddac-2345">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2345">**Description**</span></span>

<span data-ttu-id="5ddac-2346">Este evento representa un evento de escritura de soporte físico de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2346">This event represents a USBX Host Class Storage Media Write Event.</span></span>

<span data-ttu-id="5ddac-2347">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2347">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2348">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2348">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2349">Campo de información 2: Inicio del sector</span><span class="sxs-lookup"><span data-stu-id="5ddac-2349">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="5ddac-2350">Campo de información 3: recuento de sectores</span><span class="sxs-lookup"><span data-stu-id="5ddac-2350">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="5ddac-2351">Campo de información 4: puntero de datos</span><span class="sxs-lookup"><span data-stu-id="5ddac-2351">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-request-sense"></a><span data-ttu-id="5ddac-2352">Detección de solicitud de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2352">Host Class Storage Request Sense</span></span> 

#### <a name="ux_host_class_storage_request_sense"></a><span data-ttu-id="5ddac-2353">ux_host_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="5ddac-2353">ux_host_class_storage_request_sense</span></span>

<span data-ttu-id="5ddac-2354">**Icono** ![Icono de detección de solicitud de clase STORAGE de host](./media/user-guide/usbx-events/image182.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2354">**Icon** ![Host Class Storage Request Sense icon](./media/user-guide/usbx-events/image182.png)</span></span>

<span data-ttu-id="5ddac-2355">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2355">**Description**</span></span>

<span data-ttu-id="5ddac-2356">Este evento representa un evento de detección de solicitud de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2356">This event represents a USBX Host Class Storage Request Sense Event.</span></span>

<span data-ttu-id="5ddac-2357">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2357">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2358">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2358">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2359">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2359">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2360">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2360">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2361">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2361">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-start-stop"></a><span data-ttu-id="5ddac-2362">Inicio/parada de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2362">Host Class Storage Start Stop</span></span> 

#### <a name="ux_host_class_storage_start_stop"></a><span data-ttu-id="5ddac-2363">ux_host_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="5ddac-2363">ux_host_class_storage_start_stop</span></span>

<span data-ttu-id="5ddac-2364">**Icono** ![Icono de inicio/parada inicio de clase STORAGE de host](./media/user-guide/usbx-events/image183.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2364">**Icon** ![Host Class Storage Start Stop icon](./media/user-guide/usbx-events/image183.png)</span></span>

<span data-ttu-id="5ddac-2365">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2365">**Description**</span></span>

<span data-ttu-id="5ddac-2366">Este evento representa un evento de inicio/parada de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2366">This event represents a USBX Host Class Storage Start Stop Event.</span></span>

<span data-ttu-id="5ddac-2367">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2367">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2368">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2368">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2369">Campo de información 2: señal de inicio/parada</span><span class="sxs-lookup"><span data-stu-id="5ddac-2369">Info Field 2: Start stop signal.</span></span>
- <span data-ttu-id="5ddac-2370">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2370">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2371">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2371">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-unit-ready-test"></a><span data-ttu-id="5ddac-2372">Prueba de unidad preparada de clase STORAGE de host</span><span class="sxs-lookup"><span data-stu-id="5ddac-2372">Host Class Storage Unit Ready Test</span></span> 

#### <a name="ux_host_class_storage_unit_ready_test"></a><span data-ttu-id="5ddac-2373">ux_host_class_storage_unit_ready_test</span><span class="sxs-lookup"><span data-stu-id="5ddac-2373">ux_host_class_storage_unit_ready_test</span></span>

<span data-ttu-id="5ddac-2374">**Icono** ![Icono de prueba de unidad preparada de clase STORAGE de host](./media/user-guide/usbx-events/image184.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2374">**Icon** ![Host Class Storage Unit Ready Test icon](./media/user-guide/usbx-events/image184.png)</span></span>

<span data-ttu-id="5ddac-2375">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2375">**Description**</span></span>

<span data-ttu-id="5ddac-2376">Este evento representa un evento de prueba de unidad preparada de la clase STORAGE del host USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2376">This event represents a USBX Host Class Storage Unit Ready Test Event.</span></span>

<span data-ttu-id="5ddac-2377">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2377">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2378">Campo de información 1: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2378">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="5ddac-2379">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2379">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2380">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2380">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2381">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2381">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-create"></a><span data-ttu-id="5ddac-2382">Creación de instancia de clase de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2382">Host Stack Class Instance Create</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="5ddac-2383">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="5ddac-2383">ux_host_class_instance_create</span></span>

<span data-ttu-id="5ddac-2384">**Icono** ![Icono de creación de instancia de clase de pila de hosts](./media/user-guide/usbx-events/image185.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2384">**Icon** ![Host Stack Class Instance Create icon](./media/user-guide/usbx-events/image185.png)</span></span>

<span data-ttu-id="5ddac-2385">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2385">**Description**</span></span>

<span data-ttu-id="5ddac-2386">Este evento representa un evento de creación de instancia de la clase de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2386">This event represents a USBX Host Stack Class Instance Create Event.</span></span>

<span data-ttu-id="5ddac-2387">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2387">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2388">Campo de información 1: clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2388">Info Field 1: Class.</span></span>
- <span data-ttu-id="5ddac-2389">Campo de información 2: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2389">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="5ddac-2390">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2390">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2391">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2391">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-destroy"></a><span data-ttu-id="5ddac-2392">Destrucción de instancia de clase de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2392">Host Stack Class Instance Destroy</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="5ddac-2393">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="5ddac-2393">ux_host_class_instance_create</span></span>

<span data-ttu-id="5ddac-2394">**Icono** ![Icono de destrucción de instancia de clase de pila de hosts](./media/user-guide/usbx-events/image186.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2394">**Icon** ![Host Stack Class Instance Destroy icon](./media/user-guide/usbx-events/image186.png)</span></span>

<span data-ttu-id="5ddac-2395">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2395">**Description**</span></span>

<span data-ttu-id="5ddac-2396">Este evento representa un evento de destrucción de instancia de la clase de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2396">This event represents a USBX Host Stack Class Instance Destroy Event.</span></span>

<span data-ttu-id="5ddac-2397">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2397">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2398">Campo de información 1: clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2398">Info Field 1: Class.</span></span>
- <span data-ttu-id="5ddac-2399">Campo de información 2: instancia de clase</span><span class="sxs-lookup"><span data-stu-id="5ddac-2399">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="5ddac-2400">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2400">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2401">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2401">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-delete"></a><span data-ttu-id="5ddac-2402">Eliminación de configuración de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2402">Host Stack Configuration Delete</span></span> 

#### <a name="ux_host_class_configuration_delete"></a><span data-ttu-id="5ddac-2403">ux_host_class_configuration_delete</span><span class="sxs-lookup"><span data-stu-id="5ddac-2403">ux_host_class_configuration_delete</span></span>

<span data-ttu-id="5ddac-2404">**Icono** ![Icono de eliminación de configuración de pila de hosts](./media/user-guide/usbx-events/image187.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2404">**Icon** ![Host Stack Configuration Delete icon](./media/user-guide/usbx-events/image187.png)</span></span>

<span data-ttu-id="5ddac-2405">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2405">**Description**</span></span>

<span data-ttu-id="5ddac-2406">Este evento representa un evento de eliminación de configuración de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2406">This event represents a USBX Host Stack Configuration Delete Event.</span></span>

<span data-ttu-id="5ddac-2407">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2407">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2408">Campo de información 1: configuración</span><span class="sxs-lookup"><span data-stu-id="5ddac-2408">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="5ddac-2409">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2409">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2410">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2410">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2411">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2411">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-enumerate"></a><span data-ttu-id="5ddac-2412">Enumeración de configuración de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2412">Host Stack Configuration Enumerate</span></span> 

#### <a name="ux_host_stack_configuration_enumerate"></a><span data-ttu-id="5ddac-2413">ux_host_stack_configuration_enumerate</span><span class="sxs-lookup"><span data-stu-id="5ddac-2413">ux_host_stack_configuration_enumerate</span></span>

<span data-ttu-id="5ddac-2414">**Icono** ![Icono de enumeración de configuración de pila de hosts](./media/user-guide/usbx-events/image188.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2414">**Icon** ![Host Stack Configuration Enumerate icon](./media/user-guide/usbx-events/image188.png)</span></span>

<span data-ttu-id="5ddac-2415">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2415">**Description**</span></span>

<span data-ttu-id="5ddac-2416">Este evento representa un evento de enumeración de configuración de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2416">This event represents a USBX Host Stack Configuration Enumerate Event.</span></span>

<span data-ttu-id="5ddac-2417">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2417">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2418">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2418">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2419">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2419">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2420">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2420">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2421">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2421">Info Field 4: Not used.</span></span>

### <a name="stack-configuration-instance-create"></a><span data-ttu-id="5ddac-2422">Creación de instancia de configuración de pila</span><span class="sxs-lookup"><span data-stu-id="5ddac-2422">Stack Configuration Instance Create</span></span> 

#### <a name="ux_host_stack_configuration_instance_create"></a><span data-ttu-id="5ddac-2423">ux_host_stack_configuration_instance_create</span><span class="sxs-lookup"><span data-stu-id="5ddac-2423">ux_host_stack_configuration_instance_create</span></span>

<span data-ttu-id="5ddac-2424">**Icono** ![Icono de creación de instancia de configuración de pila de hosts](./media/user-guide/usbx-events/image189.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2424">**Icon** ![Stack Configuration Instance Create icon](./media/user-guide/usbx-events/image189.png)</span></span>

<span data-ttu-id="5ddac-2425">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2425">**Description**</span></span>

<span data-ttu-id="5ddac-2426">Este evento representa un evento de creación de instancia de configuración de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2426">This event represents a USBX Host Stack Configuration Instance Create Event.</span></span>

<span data-ttu-id="5ddac-2427">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2427">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2428">Campo de información 1: configuración</span><span class="sxs-lookup"><span data-stu-id="5ddac-2428">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="5ddac-2429">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2429">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2430">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2430">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2431">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2431">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-instance-delete"></a><span data-ttu-id="5ddac-2432">Eliminación de instancia de configuración de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2432">Host Stack Configuration Instance Delete</span></span> 

#### <a name="ux_host_stack_configuration_instance_delete"></a><span data-ttu-id="5ddac-2433">ux_host_stack_configuration_instance_delete</span><span class="sxs-lookup"><span data-stu-id="5ddac-2433">ux_host_stack_configuration_instance_delete</span></span>

<span data-ttu-id="5ddac-2434">**Icono** ![Icono de eliminación de instancia de configuración de pila de hosts](./media/user-guide/usbx-events/image190.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2434">**Icon** ![Host Stack Configuration Instance Delete icon](./media/user-guide/usbx-events/image190.png)</span></span>

<span data-ttu-id="5ddac-2435">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2435">**Description**</span></span>

<span data-ttu-id="5ddac-2436">Este evento representa un evento de eliminación de instancia de configuración de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2436">This event represents a USBX Host Stack Configuration Instance Delete Event.</span></span>

<span data-ttu-id="5ddac-2437">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2437">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2438">Campo de información 1: configuración</span><span class="sxs-lookup"><span data-stu-id="5ddac-2438">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="5ddac-2439">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2439">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2440">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2440">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2441">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2441">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-set"></a><span data-ttu-id="5ddac-2442">Establecimiento de configuración de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2442">Host Stack Configuration Set</span></span> 

#### <a name="ux_host_stack_configuration_set"></a><span data-ttu-id="5ddac-2443">ux_host_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-2443">ux_host_stack_configuration_set</span></span>

<span data-ttu-id="5ddac-2444">**Icono** ![Icono de establecimiento de configuración de pila de hosts](./media/user-guide/usbx-events/image191.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2444">**Icon** ![Host Stack Configuration Set icon](./media/user-guide/usbx-events/image191.png)</span></span>

<span data-ttu-id="5ddac-2445">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2445">**Description**</span></span>

<span data-ttu-id="5ddac-2446">Este evento representa un evento de establecimiento de configuración de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2446">This event represents a USBX Host Stack Configuration Set Event.</span></span>

<span data-ttu-id="5ddac-2447">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2447">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2448">Campo de información 1: configuración</span><span class="sxs-lookup"><span data-stu-id="5ddac-2448">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="5ddac-2449">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2449">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2450">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2451">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2451">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-address-set"></a><span data-ttu-id="5ddac-2452">Establecimiento de dirección de dispositivo de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2452">Host Stack Device Address Set</span></span> 

#### <a name="ux_host_stack_device_address_set"></a><span data-ttu-id="5ddac-2453">ux_host_stack_device_address_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-2453">ux_host_stack_device_address_set</span></span>

<span data-ttu-id="5ddac-2454">**Icono** ![Icono de establecimiento de dirección de dispositivo de pila de hosts](./media/user-guide/usbx-events/image192.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2454">**Icon** ![Host Stack Device Address Set icon](./media/user-guide/usbx-events/image192.png)</span></span>

<span data-ttu-id="5ddac-2455">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2455">**Description**</span></span>

<span data-ttu-id="5ddac-2456">Este evento representa un evento de establecimiento de dirección de dispositivo de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2456">This event represents a USBX Host Stack Device Address Set Event.</span></span>

<span data-ttu-id="5ddac-2457">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2457">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2458">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2458">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2459">Campo de información 2: dirección del dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2459">Info Field 2: Device Address.</span></span>
- <span data-ttu-id="5ddac-2460">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2461">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2461">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-get"></a><span data-ttu-id="5ddac-2462">Obtención de configuración de dispositivo de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2462">Host Stack Device Configuration Get</span></span> 

#### <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="5ddac-2463">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2463">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="5ddac-2464">**Icono** ![Icono de obtención de configuración de dispositivo de pila de hosts](./media/user-guide/usbx-events/image193.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2464">**Icon** ![Host Stack Device Configuration Get icon](./media/user-guide/usbx-events/image193.png)</span></span>

<span data-ttu-id="5ddac-2465">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2465">**Description**</span></span>

<span data-ttu-id="5ddac-2466">Este evento representa un evento de obtención de configuración de dispositivo de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2466">This event represents a USBX Host Stack Device Configuration Get Event.</span></span>

<span data-ttu-id="5ddac-2467">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2467">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2468">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2468">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2469">Campo de información 2: configuración</span><span class="sxs-lookup"><span data-stu-id="5ddac-2469">nfo Field 2: Configuration.</span></span>
- <span data-ttu-id="5ddac-2470">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2471">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2471">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-select"></a><span data-ttu-id="5ddac-2472">Selección de configuración de dispositivo de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2472">Host Stack Device Configuration Select</span></span> 

#### <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="5ddac-2473">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="5ddac-2473">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="5ddac-2474">**Icono** ![Icono de selección de configuración de dispositivo de pila de hosts](./media/user-guide/usbx-events/image194.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2474">**Icon** ![Host Stack Device Configuration Select icon](./media/user-guide/usbx-events/image194.png)</span></span>

<span data-ttu-id="5ddac-2475">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2475">**Description**</span></span>

<span data-ttu-id="5ddac-2476">Este evento representa un evento de selección de configuración de dispositivo de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2476">This event represents a USBX Host Stack Device Configuration Select Event.</span></span>

<span data-ttu-id="5ddac-2477">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2477">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2478">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2478">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2479">Campo de información 2: configuración</span><span class="sxs-lookup"><span data-stu-id="5ddac-2479">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="5ddac-2480">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2481">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2481">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-descriptor-read"></a><span data-ttu-id="5ddac-2482">Lectura de descriptor de dispositivo de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2482">Host Stack Device Descriptor Read</span></span> 

#### <a name="ux_host_stack_device_descriptor_read"></a><span data-ttu-id="5ddac-2483">ux_host_stack_device_descriptor_read</span><span class="sxs-lookup"><span data-stu-id="5ddac-2483">ux_host_stack_device_descriptor_read</span></span>

<span data-ttu-id="5ddac-2484">**Icono** ![Icono de lectura de descriptor de dispositivo de pila de hosts](./media/user-guide/usbx-events/image195.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2484">**Icon** ![Host Stack Device Descriptor Read icon](./media/user-guide/usbx-events/image195.png)</span></span>

<span data-ttu-id="5ddac-2485">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2485">**Description**</span></span>

<span data-ttu-id="5ddac-2486">Este evento representa un evento de lectura del descriptor de dispositivo de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2486">This event represents a USBX Host Stack Device Descriptor Read Event.</span></span>

<span data-ttu-id="5ddac-2487">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2487">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2488">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2488">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2489">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2489">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2490">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2491">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2491">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-get"></a><span data-ttu-id="5ddac-2492">Obtención de dispositivo de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2492">Host Stack Device Get</span></span> 

#### <a name="ux_host_stack_device_get"></a><span data-ttu-id="5ddac-2493">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="5ddac-2493">ux_host_stack_device_get</span></span>

<span data-ttu-id="5ddac-2494">**Icono** ![Icono de obtención de dispositivo de pila de hosts](./media/user-guide/usbx-events/image196.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2494">**Icon** ![Host Stack Device Get icon](./media/user-guide/usbx-events/image196.png)</span></span>

<span data-ttu-id="5ddac-2495">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2495">**Description**</span></span>

<span data-ttu-id="5ddac-2496">Este evento representa un evento de obtención de dispositivo de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2496">This event represents a USBX Host Stack Device Get Event.</span></span>

<span data-ttu-id="5ddac-2497">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2497">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2498">Campo de información 1: índice de dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2498">Info Field 1: Device index.</span></span>
- <span data-ttu-id="5ddac-2499">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2499">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2500">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2501">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2501">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-remove"></a><span data-ttu-id="5ddac-2502">Eliminación de dispositivo de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2502">Host Stack Device Remove</span></span> 

#### <a name="ux_host_stack_device_remove"></a><span data-ttu-id="5ddac-2503">ux_host_stack_device_remove</span><span class="sxs-lookup"><span data-stu-id="5ddac-2503">ux_host_stack_device_remove</span></span>

<span data-ttu-id="5ddac-2504">**Icono** ![Icono de eliminación de dispositivo de pila de hosts](./media/user-guide/usbx-events/image197.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2504">**Icon** ![Host Stack Device Remove icon](./media/user-guide/usbx-events/image197.png)</span></span>

<span data-ttu-id="5ddac-2505">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2505">**Description**</span></span>

<span data-ttu-id="5ddac-2506">Este evento representa un evento de eliminación de dispositivo de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2506">This event represents a USBX Host Stack Device Remove Event.</span></span>

<span data-ttu-id="5ddac-2507">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2507">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2508">Campo de información 1: HCD</span><span class="sxs-lookup"><span data-stu-id="5ddac-2508">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="5ddac-2509">Campo de información 2: elemento principal</span><span class="sxs-lookup"><span data-stu-id="5ddac-2509">Info Field 2: Parent.</span></span>
- <span data-ttu-id="5ddac-2510">Campo de información 3: índice de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-2510">Info Field 3: Port Index.</span></span>
- <span data-ttu-id="5ddac-2511">Campo de información 4: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2511">Info Field 4: Device.</span></span>

### <a name="host-stack-device-resource-free"></a><span data-ttu-id="5ddac-2512">Recurso libre de dispositivo de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2512">Host Stack Device Resource Free</span></span> 

#### <a name="ux_host_stack_device_resource_free"></a><span data-ttu-id="5ddac-2513">ux_host_stack_device_resource_free</span><span class="sxs-lookup"><span data-stu-id="5ddac-2513">ux_host_stack_device_resource_free</span></span>

<span data-ttu-id="5ddac-2514">**Icono** ![Icono de recurso libre de dispositivo de pila de hosts](./media/user-guide/usbx-events/image198.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2514">**Icon** ![Host Stack Device Resource Free icon](./media/user-guide/usbx-events/image198.png)</span></span>

<span data-ttu-id="5ddac-2515">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2515">**Description**</span></span>

<span data-ttu-id="5ddac-2516">Este evento representa un evento de recurso libre de dispositivo de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2516">This event represents a USBX Host Stack Device Resource Free Event.</span></span>

<span data-ttu-id="5ddac-2517">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2517">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2518">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2518">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2519">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2520">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2521">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2521">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-create"></a><span data-ttu-id="5ddac-2522">Creación de instancia de punto de conexión de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2522">Host Stack Endpoint Instance Create</span></span> 

#### <a name="ux_host_stack_endpoint_instance_create"></a><span data-ttu-id="5ddac-2523">ux_host_stack_endpoint_instance_create</span><span class="sxs-lookup"><span data-stu-id="5ddac-2523">ux_host_stack_endpoint_instance_create</span></span>

<span data-ttu-id="5ddac-2524">**Icono** ![Icono de creación de instancia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image199.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2524">**Icon** ![Host Stack Endpoint Instance Create icon](./media/user-guide/usbx-events/image199.png)</span></span>

<span data-ttu-id="5ddac-2525">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2525">**Description**</span></span>

<span data-ttu-id="5ddac-2526">Este evento representa un evento de creación de instancia de punto de conexión de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2526">This event represents a USBX Host Stack Endpoint Instance Create Event.</span></span>

<span data-ttu-id="5ddac-2527">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2527">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2528">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2528">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2529">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2529">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-2530">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2531">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2531">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-delete"></a><span data-ttu-id="5ddac-2532">Eliminación de instancia de punto de conexión de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2532">Host Stack Endpoint Instance Delete</span></span> 

#### <a name="ux_host_stack_endpoint_instance_delete"></a><span data-ttu-id="5ddac-2533">ux_host_stack_endpoint_instance_delete</span><span class="sxs-lookup"><span data-stu-id="5ddac-2533">ux_host_stack_endpoint_instance_delete</span></span>

<span data-ttu-id="5ddac-2534">**Icono** ![Icono de eliminación de instancia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image200.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2534">**Icon** ![Host Stack Endpoint Instance Delete icon](./media/user-guide/usbx-events/image200.png)</span></span>

<span data-ttu-id="5ddac-2535">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2535">**Description**</span></span>

<span data-ttu-id="5ddac-2536">Este evento representa un evento de eliminación de instancia de punto de conexión de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2536">This event represents a USBX Host Stack Endpoint Instance Delete Event.</span></span>

<span data-ttu-id="5ddac-2537">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2537">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2538">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2538">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-2539">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2539">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2540">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2540">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-reset"></a><span data-ttu-id="5ddac-2541">Restablecimiento de punto de conexión de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2541">Host Stack Endpoint Reset</span></span> 

#### <a name="ux_host_stack_endpoint_reset"></a><span data-ttu-id="5ddac-2542">ux_host_stack_endpoint_reset</span><span class="sxs-lookup"><span data-stu-id="5ddac-2542">ux_host_stack_endpoint_reset</span></span>

<span data-ttu-id="5ddac-2543">**Icono** ![Icono de restablecimiento de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image201.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2543">**Icon** ![Host Stack Endpoint Reset icon](./media/user-guide/usbx-events/image201.png)</span></span>

<span data-ttu-id="5ddac-2544">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2544">**Description**</span></span>

<span data-ttu-id="5ddac-2545">Este evento representa un evento de restablecimiento de punto de conexión de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2545">This event represents a USBX Host Stack Endpoint Reset Event.</span></span>

<span data-ttu-id="5ddac-2546">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2546">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2547">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2547">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2548">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2548">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-2549">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2549">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2550">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2550">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-transfer-abort"></a><span data-ttu-id="5ddac-2551">Anulación de transferencia de punto de conexión de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2551">Host Stack Endpoint Transfer Abort</span></span> 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="5ddac-2552">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="5ddac-2552">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="5ddac-2553">**Icono** ![Icono de anulación de transferencia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image202.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2553">**Icon** ![Host Stack Endpoint Transfer Abort icon](./media/user-guide/usbx-events/image202.png)</span></span>

<span data-ttu-id="5ddac-2554">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2554">**Description**</span></span>

<span data-ttu-id="5ddac-2555">Este evento representa un evento de anulación de transferencia de punto de conexión de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2555">This event represents a USBX Host Stack Endpoint Transfer Abort Event.</span></span>

<span data-ttu-id="5ddac-2556">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2556">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2557">Campo de información 1: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2557">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="5ddac-2558">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2558">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2559">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2559">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2560">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2560">Info Field 4: Not used.</span></span>

### <a name="host-stack-host-controller-register"></a><span data-ttu-id="5ddac-2561">Registro de controlador de host de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2561">Host Stack Host Controller Register</span></span> 

#### <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="5ddac-2562">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="5ddac-2562">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="5ddac-2563">**Icono** ![Icono de registro de controlador de host de pila de hosts](./media/user-guide/usbx-events/image203.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2563">**Icon** ![Host Stack Host Controller Register icon](./media/user-guide/usbx-events/image203.png)</span></span>

<span data-ttu-id="5ddac-2564">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2564">**Description**</span></span>

<span data-ttu-id="5ddac-2565">Este evento representa un registro de controlador de host de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2565">This event represents a USBX Host Stack Host Controller Register.</span></span>

<span data-ttu-id="5ddac-2566">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2566">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2567">Campo de información 1: nombre de HCD</span><span class="sxs-lookup"><span data-stu-id="5ddac-2567">Info Field 1: Hcd Name.</span></span>
- <span data-ttu-id="5ddac-2568">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2568">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2569">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2569">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2570">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2570">Info Field 4: Not used.</span></span>

### <a name="host-stack-initialize"></a><span data-ttu-id="5ddac-2571">Inicialización de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2571">Host Stack Initialize</span></span> 

#### <a name="ux_host_stack_initialize"></a><span data-ttu-id="5ddac-2572">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="5ddac-2572">ux_host_stack_initialize</span></span>

<span data-ttu-id="5ddac-2573">**Icono** ![Icono de inicialización de pila de hosts](./media/user-guide/usbx-events/image204.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2573">**Icon** ![Host Stack Initialize icon](./media/user-guide/usbx-events/image204.png)</span></span>

<span data-ttu-id="5ddac-2574">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2574">**Description**</span></span>

<span data-ttu-id="5ddac-2575">Este evento representa un evento de inicialización de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2575">This event represents a USBX Host Stack Initialize Event.</span></span>

<span data-ttu-id="5ddac-2576">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2576">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2577">Campo de información 1: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2577">Info Field 1: Not used.</span></span>
- <span data-ttu-id="5ddac-2578">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2578">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2579">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2579">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2580">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2580">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-endpoint-get"></a><span data-ttu-id="5ddac-2581">Obtención de punto de conexión de interfaz de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2581">Host Stack Interface Endpoint Get</span></span> 

#### <a name="interface_-tcp-retry-entry"></a><span data-ttu-id="5ddac-2582">Entrada de reintento de interfaz TCP</span><span class="sxs-lookup"><span data-stu-id="5ddac-2582">Interface_ TCP retry entry</span></span>

<span data-ttu-id="5ddac-2583">**Icono** ![Icono de obtención de punto de conexión de interfaz de pila de hosts](./media/user-guide/usbx-events/image205.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2583">**Icon** ![Host Stack Interface Endpoint Get icon](./media/user-guide/usbx-events/image205.png)</span></span>

<span data-ttu-id="5ddac-2584">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2584">**Description**</span></span>

<span data-ttu-id="5ddac-2585">Este evento representa un evento interno de reintento de TCP de NetX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2585">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="5ddac-2586">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2586">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2587">Campo de información 1: interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-2587">Info Field 1: Interface.</span></span>
- <span data-ttu-id="5ddac-2588">Campo de información 2: índice de punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2588">Info Field 2: Endpoint index.</span></span>
- <span data-ttu-id="5ddac-2589">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2589">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2590">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2590">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-create"></a><span data-ttu-id="5ddac-2591">Creación de instancia de interfaz de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2591">Host Stack Interface Instance Create</span></span> 

#### <a name="ux_host_stack_interface_instance_create"></a><span data-ttu-id="5ddac-2592">ux_host_stack_interface_instance_create</span><span class="sxs-lookup"><span data-stu-id="5ddac-2592">ux_host_stack_interface_instance_create</span></span>

<span data-ttu-id="5ddac-2593">**Icono** ![Icono de creación de instancia de interfaz de pila de hosts](./media/user-guide/usbx-events/image206.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2593">**Icon** ![Host Stack Interface Instance Create icon](./media/user-guide/usbx-events/image206.png)</span></span>

<span data-ttu-id="5ddac-2594">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2594">**Description**</span></span>

<span data-ttu-id="5ddac-2595">Este evento representa un evento de creación de instancia de interfaz de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2595">This event represents a USBX Host Stack Interface Instance Create Event.</span></span>

<span data-ttu-id="5ddac-2596">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2596">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2597">Campo de información 1: interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-2597">Info Field 1: Interface.</span></span>
- <span data-ttu-id="5ddac-2598">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2598">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2599">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2599">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2600">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2600">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-delete"></a><span data-ttu-id="5ddac-2601">Eliminación de instancia de interfaz de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2601">Host Stack Interface Instance Delete</span></span> 

#### <a name="ux_host_stack_interface_instance_delete"></a><span data-ttu-id="5ddac-2602">ux_host_stack_interface_instance_delete</span><span class="sxs-lookup"><span data-stu-id="5ddac-2602">ux_host_stack_interface_instance_delete</span></span>

<span data-ttu-id="5ddac-2603">**Icono** ![Icono de eliminación de instancia de interfaz de pila de hosts](./media/user-guide/usbx-events/image207.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2603">**Icon** ![Host Stack Interface Instance Delete icon](./media/user-guide/usbx-events/image207.png)</span></span>

<span data-ttu-id="5ddac-2604">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2604">**Description**</span></span>

<span data-ttu-id="5ddac-2605">Este evento representa un evento de eliminación de instancia de interfaz de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2605">This event represents a USBX Host Stack Interface Instance Delete Event.</span></span>

<span data-ttu-id="5ddac-2606">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2606">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2607">Campo de información 1: interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-2607">Info Field 1: Interface.</span></span>
- <span data-ttu-id="5ddac-2608">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2608">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2609">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2609">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2610">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2610">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-set"></a><span data-ttu-id="5ddac-2611">Establecimiento de interfaz de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2611">Host Stack Interface Set</span></span> 

#### <a name="ux_host_stack_interface_set"></a><span data-ttu-id="5ddac-2612">ux_host_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="5ddac-2612">ux_host_stack_interface_set</span></span>

<span data-ttu-id="5ddac-2613">**Icono** ![Icono de establecimiento de interfaz de pila de hosts](./media/user-guide/usbx-events/image208.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2613">**Icon** ![Host Stack Interface Set icon](./media/user-guide/usbx-events/image208.png)</span></span>

<span data-ttu-id="5ddac-2614">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2614">**Description**</span></span>

<span data-ttu-id="5ddac-2615">Este evento representa un evento de establecimiento de la interfaz de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2615">This event represents a USBX Host Stack Interface Set Event.</span></span>

<span data-ttu-id="5ddac-2616">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2616">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2617">Campo de información 1: interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-2617">Info Field 1: Interface.</span></span>
- <span data-ttu-id="5ddac-2618">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2618">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2619">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2619">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2620">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2620">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-setting-select"></a><span data-ttu-id="5ddac-2621">Selección de configuración de interfaz de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2621">Host Stack Interface Setting Select</span></span> 

#### <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="5ddac-2622">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="5ddac-2622">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="5ddac-2623">**Icono** ![Icono de selección de configuración de interfaz de pila de hosts](./media/user-guide/usbx-events/image209.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2623">**Icon** ![Host Stack Interface Setting Select icon](./media/user-guide/usbx-events/image209.png)</span></span>

<span data-ttu-id="5ddac-2624">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2624">**Description**</span></span>

<span data-ttu-id="5ddac-2625">Este evento representa un evento de selección de la configuración de interfaz de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2625">This event represents a USBX Host Stack Interface Setting Select Event.</span></span>

<span data-ttu-id="5ddac-2626">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2626">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2627">Campo de información 1: interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-2627">Info Field 1: Interface.</span></span>
- <span data-ttu-id="5ddac-2628">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2628">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2629">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2629">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2630">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2630">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-configuration-create"></a><span data-ttu-id="5ddac-2631">Creación de nueva configuración de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2631">Host Stack New Configuration Create</span></span> 

#### <a name="ux_host_stack_new_configuration_create"></a><span data-ttu-id="5ddac-2632">ux_host_stack_new_configuration_create</span><span class="sxs-lookup"><span data-stu-id="5ddac-2632">ux_host_stack_new_configuration_create</span></span>

<span data-ttu-id="5ddac-2633">**Icono** ![Icono de creación de nueva configuración de pila de hosts](./media/user-guide/usbx-events/image210.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2633">**Icon** ![Host Stack New Configuration Create icon](./media/user-guide/usbx-events/image210.png)</span></span>

<span data-ttu-id="5ddac-2634">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2634">**Description**</span></span>
 
<span data-ttu-id="5ddac-2635">Este evento representa un evento de creación de nueva configuración de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2635">This event represents a USBX Host Stack New Configuration Create Event.</span></span>

<span data-ttu-id="5ddac-2636">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2636">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2637">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2637">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2638">Campo de información 2: configuración</span><span class="sxs-lookup"><span data-stu-id="5ddac-2638">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="5ddac-2639">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2639">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2640">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2640">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-device-create"></a><span data-ttu-id="5ddac-2641">Creación de nuevo dispositivo de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2641">Host Stack New Device Create</span></span> 

#### <a name="ux_host_stack_new_device_create"></a><span data-ttu-id="5ddac-2642">ux_host_stack_new_device_create</span><span class="sxs-lookup"><span data-stu-id="5ddac-2642">ux_host_stack_new_device_create</span></span>

<span data-ttu-id="5ddac-2643">**Icono** ![Icono de creación de nuevo dispositivo de pila de hosts](./media/user-guide/usbx-events/image211.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2643">**Icon** ![Host Stack New Device Create icon](./media/user-guide/usbx-events/image211.png)</span></span>

<span data-ttu-id="5ddac-2644">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2644">**Description**</span></span>
 
 <span data-ttu-id="5ddac-2645">Este evento representa un evento de creación de un nuevo dispositivo de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2645">This event represents a USBX Host Stack New Device Create Event.</span></span>

<span data-ttu-id="5ddac-2646">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2646">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2647">Campo de información 1: HCD</span><span class="sxs-lookup"><span data-stu-id="5ddac-2647">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="5ddac-2648">Campo de información 2: propietario del dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2648">Info Field 2: Device owner.</span></span>
- <span data-ttu-id="5ddac-2649">Campo de información 3: índice de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-2649">Info Field 3: Port index.</span></span>
- <span data-ttu-id="5ddac-2650">Campo de información 4: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2650">Info Field 4: Device.</span></span>

### <a name="host-stack-new-endpoint-create"></a><span data-ttu-id="5ddac-2651">Creación de nuevo punto de conexión de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2651">Host Stack New Endpoint Create</span></span> 

#### <a name="ux_host_stack_new_endpoint_create"></a><span data-ttu-id="5ddac-2652">ux_host_stack_new_endpoint_create</span><span class="sxs-lookup"><span data-stu-id="5ddac-2652">ux_host_stack_new_endpoint_create</span></span>

<span data-ttu-id="5ddac-2653">**Icono** ![Icono de creación de nuevo punto de conexión de pila de hosts](./media/user-guide/usbx-events/image212.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2653">**Icon** ![Host Stack New Endpoint Create icon](./media/user-guide/usbx-events/image212.png)</span></span>

<span data-ttu-id="5ddac-2654">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2654">**Description**</span></span>
 
<span data-ttu-id="5ddac-2655">Este evento representa un evento de creación de un nuevo punto de conexión de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2655">This event represents a USBX Host Stack New Endpoint Create Event.</span></span>

<span data-ttu-id="5ddac-2656">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2656">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2657">Campo de información 1: interfaz</span><span class="sxs-lookup"><span data-stu-id="5ddac-2657">Info Field 1: Interface.</span></span>
- <span data-ttu-id="5ddac-2658">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2658">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-2659">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2659">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2660">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2660">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-change-process"></a><span data-ttu-id="5ddac-2661">Proceso de cambio de centro de conectividad raíz de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2661">Host Stack Root Hub Change Process</span></span> 

#### <a name="ux_host_stack_rh_change_process"></a><span data-ttu-id="5ddac-2662">ux_host_stack_rh_change_process</span><span class="sxs-lookup"><span data-stu-id="5ddac-2662">ux_host_stack_rh_change_process</span></span>

<span data-ttu-id="5ddac-2663">**Icono** ![Icono de proceso de cambio de centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image213.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2663">**Icon** ![Host Stack Root Hub Change Process icon](./media/user-guide/usbx-events/image213.png)</span></span>

<span data-ttu-id="5ddac-2664">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2664">**Description**</span></span>
 
<span data-ttu-id="5ddac-2665">Este evento representa un proceso de cambio del centro de conectividad raíz de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2665">This event represents a USBX Host Stack Root Hub Change Process.</span></span>

<span data-ttu-id="5ddac-2666">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2666">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2667">Campo de información 1: índice de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-2667">Info Field 1: Port index.</span></span>
- <span data-ttu-id="5ddac-2668">Campo de información 2: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2668">Info Field 2: Not used.</span></span>
- <span data-ttu-id="5ddac-2669">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2669">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2670">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2670">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-extraction"></a><span data-ttu-id="5ddac-2671">Extracción de dispositivo de centro de conectividad raíz de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2671">Host Stack Root Hub Device Extraction</span></span> 

#### <a name="ux_host_stack_rh_device_extraction"></a><span data-ttu-id="5ddac-2672">ux_host_stack_rh_device_extraction</span><span class="sxs-lookup"><span data-stu-id="5ddac-2672">ux_host_stack_rh_device_extraction</span></span>

<span data-ttu-id="5ddac-2673">**Icono** ![Icono de extracción de dispositivo de centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image214.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2673">**Icon** ![Host Stack Root Hub Device Extraction icon](./media/user-guide/usbx-events/image214.png)</span></span>

<span data-ttu-id="5ddac-2674">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2674">**Description**</span></span>

<span data-ttu-id="5ddac-2675">Este evento representa un evento de extracción de dispositivo del centro de conectividad raíz de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2675">This event represents a USBX Host Stack Root Hub Device Extraction Event.</span></span>

<span data-ttu-id="5ddac-2676">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2676">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2677">Campo de información 1: HCD</span><span class="sxs-lookup"><span data-stu-id="5ddac-2677">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="5ddac-2678">Campo de información 2: índice de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-2678">Info Field 2: Port index.</span></span>
- <span data-ttu-id="5ddac-2679">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2679">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2680">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2680">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-insertion"></a><span data-ttu-id="5ddac-2681">Inserción de dispositivo en centro de conectividad raíz de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2681">Host Stack Root Hub Device Insertion</span></span> 

#### <a name="ux_host_stack_rh_device_insertion"></a><span data-ttu-id="5ddac-2682">ux_host_stack_rh_device_insertion</span><span class="sxs-lookup"><span data-stu-id="5ddac-2682">ux_host_stack_rh_device_insertion</span></span>

<span data-ttu-id="5ddac-2683">**Icono** ![Icono de inserción de dispositivo en centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image215.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2683">**Icon** ![Host Stack Root Hub Device Insertion icon](./media/user-guide/usbx-events/image215.png)</span></span>

<span data-ttu-id="5ddac-2684">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2684">**Description**</span></span>

<span data-ttu-id="5ddac-2685">Este evento representa una inserción de dispositivo en el centro de conectividad raíz de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2685">This event represents a USBX Host Stack Root Hub Device Insertion.</span></span>

<span data-ttu-id="5ddac-2686">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2686">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2687">Campo de información 1: HCD</span><span class="sxs-lookup"><span data-stu-id="5ddac-2687">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="5ddac-2688">Campo de información 2: índice de puerto</span><span class="sxs-lookup"><span data-stu-id="5ddac-2688">Info Field 2: Port index.</span></span>
- <span data-ttu-id="5ddac-2689">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2689">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2690">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2690">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request"></a><span data-ttu-id="5ddac-2691">Solicitud de transferencia de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2691">Host Stack Transfer Request</span></span> 

#### <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="5ddac-2692">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="5ddac-2692">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="5ddac-2693">**Icono** ![Icono de solicitud de transferencia de pila de hosts](./media/user-guide/usbx-events/image216.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2693">**Icon** ![Host Stack Transfer Request icon](./media/user-guide/usbx-events/image216.png)</span></span>

<span data-ttu-id="5ddac-2694">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2694">**Description**</span></span>

<span data-ttu-id="5ddac-2695">Este evento representa una solicitud de transferencia de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2695">This event represents a USBX Host Stack Transfer Request.</span></span>

<span data-ttu-id="5ddac-2696">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2696">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2697">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2697">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2698">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2698">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-2699">Campo de información 3: solicitud de transferencia</span><span class="sxs-lookup"><span data-stu-id="5ddac-2699">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="5ddac-2700">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2700">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request-abort"></a><span data-ttu-id="5ddac-2701">Anulación de solicitud de transferencia de pila de hosts</span><span class="sxs-lookup"><span data-stu-id="5ddac-2701">Host Stack Transfer Request Abort</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="5ddac-2702">Obtención de estado del controlador de E/S interna</span><span class="sxs-lookup"><span data-stu-id="5ddac-2702">Internal I/O driver get status</span></span>

<span data-ttu-id="5ddac-2703">**Icono** ![Icono de anulación de solicitud de transferencia de pila de hosts](./media/user-guide/usbx-events/image217.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2703">**Icon** ![Host Stack Transfer Request Abort icon](./media/user-guide/usbx-events/image217.png)</span></span>

<span data-ttu-id="5ddac-2704">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2704">**Description**</span></span>

<span data-ttu-id="5ddac-2705">Este evento representa una anulación de la solicitud de transferencia de la pila de hosts USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2705">This event represents a USBX Host Stack Transfer Request Abort.</span></span>

<span data-ttu-id="5ddac-2706">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2706">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2707">Campo de información 1: dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ddac-2707">Info Field 1: Device.</span></span>
- <span data-ttu-id="5ddac-2708">Campo de información 2: punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5ddac-2708">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="5ddac-2709">Campo de información 3: solicitud de transferencia</span><span class="sxs-lookup"><span data-stu-id="5ddac-2709">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="5ddac-2710">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2710">Info Field 4: Not used.</span></span>

### <a name="usbx-error"></a><span data-ttu-id="5ddac-2711">Error de USBX</span><span class="sxs-lookup"><span data-stu-id="5ddac-2711">USBX Error</span></span> 

#### <a name="ux_error"></a><span data-ttu-id="5ddac-2712">ux_error</span><span class="sxs-lookup"><span data-stu-id="5ddac-2712">ux_error</span></span>

<span data-ttu-id="5ddac-2713">**Icono** ![Icono de error de U S B X](./media/user-guide/usbx-events/image218.png)</span><span class="sxs-lookup"><span data-stu-id="5ddac-2713">**Icon** ![U S B X Error icon](./media/user-guide/usbx-events/image218.png)</span></span>

<span data-ttu-id="5ddac-2714">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2714">**Description**</span></span>

<span data-ttu-id="5ddac-2715">Este evento representa un evento de error de USBX.</span><span class="sxs-lookup"><span data-stu-id="5ddac-2715">This event represents a USBX Error Event.</span></span>

<span data-ttu-id="5ddac-2716">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="5ddac-2716">**Information Fields**</span></span>

- <span data-ttu-id="5ddac-2717">Campo de información 1: error de USBX</span><span class="sxs-lookup"><span data-stu-id="5ddac-2717">Info Field 1: USBX error.</span></span>
- <span data-ttu-id="5ddac-2718">Campo de información 2: nombre del error</span><span class="sxs-lookup"><span data-stu-id="5ddac-2718">Info Field 2: Error Name.</span></span>
- <span data-ttu-id="5ddac-2719">Campo de información 3: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2719">Info Field 3: Not used.</span></span>
- <span data-ttu-id="5ddac-2720">Campo de información 4: no se usa</span><span class="sxs-lookup"><span data-stu-id="5ddac-2720">Info Field 4: Not used.</span></span>