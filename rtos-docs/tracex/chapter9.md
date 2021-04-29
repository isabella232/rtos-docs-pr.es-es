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
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a>Capítulo 9: Eventos de seguimiento de USBX de Azure RTOS

En este capítulo se incluye una descripción de los eventos de USBX de Azure RTOS que muestra TraceX. 

## <a name="list-of-events-and-icons"></a>Lista de eventos e iconos

A continuación se incluye una lista de los eventos de USBX que muestra TraceX.

| Icono                             | Significado                               |
| -------------------------------- | ------------------------------------- |
| ![Icono de activación de clase C D C de dispositivo](./media/user-guide/usbx-events/image1.png)    | **Activación de clase CDC de dispositivo** *(ux_device_class_cdc_activate)* |
| ![Icono de desactivación de clase C D C de dispositivo](./media/user-guide/usbx-events/image2.png)    | **Desactivación de clase CDC de dispositivo** *(ux_device_class_cdc_deactivate)* |
| ![Icono de lectura de clase C D C de dispositivo](./media/user-guide/usbx-events/image3.png)    | **Lectura de clase CDC de dispositivo** *(ux_device_class_cdc_read)* |
| ![Icono de escritura de clase C D C de dispositivo](./media/user-guide/usbx-events/image4.png)    | **Escritura de clase CDC de dispositivo** *(ux_device_class_cdc_write)* |
| ![Icono de activación de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image5.png)    | **Activación de clase DPUMP de dispositivo** *(ux_device_class_dpump_activate)* |
| ![Icono de desactivación de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image6.png)    | **Desactivación de clase DPUMP de dispositivo** *(ux_device_class_dpump_deactivate)* |
| ![Icono de lectura de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image7.png)    | **Lectura de clase DPUMP de dispositivo** *(ux_device_class_dpump_read)* |
| ![Icono de escritura de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image8.png)    | **Escritura de clase DPUMP de dispositivo** *(ux_device_class_dpump_write)* |
| ![Icono de activación de clase H I D de dispositivo](./media/user-guide/usbx-events/image9.png)    | **Activación de clase HID de dispositivo** *(ux_device_class_hid_activate)* |
| ![Icono de desactivación de clase H I D de dispositivo](./media/user-guide/usbx-events/image10.png)    | **Desactivación de clase HID de dispositivo** *(ux_device_class_hid_deactivate)* |
| ![Icono de envío de descriptor de clase H I D de dispositivo](./media/user-guide/usbx-events/image11.png)    | **Envío de descriptor de clase HID de dispositivo** *(ux_device_class_hid_descriptor_send)* |
| ![Icono de obtención de evento de clase H I D de dispositivo](./media/user-guide/usbx-events/image12.png)    | **Obtención de evento de clase HID de dispositivo** *(ux_device_class_hid_event_get)* |
| ![Icono de establecimiento de evento de clase H I D de dispositivo](./media/user-guide/usbx-events/image13.png)    | **Establecimiento de evento de clase HID de dispositivo** *(ux_device_class_hid_event_set)* |
| ![Icono de obtención de informe de clase H I D de dispositivo](./media/user-guide/usbx-events/image14.png)    | **Obtención de informe de clase HID de dispositivo** *(ux_device_class_hid_report_get)* |
| ![Icono de establecimiento de informe de clase H I D de dispositivo](./media/user-guide/usbx-events/image15.png)    | **Establecimiento de informe de clase HID de dispositivo** *(ux_device_class_hid_report_set)* |
| ![Icono de activación de clase PIMA de dispositivo](./media/user-guide/usbx-events/image16.png)    | **Activación de clase PIMA de dispositivo** *(ux_device_class_pima_activate)* |
| ![Icono de desactivación de clase PIMA de dispositivo](./media/user-guide/usbx-events/image17.png)    | **Desactivación de clase PIMA de dispositivo** *(ux_device_class_pima_deactivate)* |
| ![Icono de envío de información de dispositivo de clase PIMA de dispositivo](./media/user-guide/usbx-events/image18.png)    | **Envío de información de dispositivo de clase PIMA de dispositivo** *(ux_device_class_pima_device_info_send)* |
| ![Icono de obtención de evento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image19.png)    | **Obtención de evento de clase PIMA de dispositivo** *(ux_device_class_pima_event_get)* |
| ![Icono de establecimiento de evento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image20.png)    | **Establecimiento de evento de clase PIMA de dispositivo** *(ux_device_class_pima_event_set)* |
| ![Icono de adición de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image21.png)    | **Adición de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_add)* |
| ![Icono de obtención de datos de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image22.png)    | **Obtención de datos de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_data_get)* |
| ![Icono de envío de datos de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image23.png)    | **Envío de datos de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_data_send)* |
| ![Icono de eliminación de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image24.png)    | **Eliminación de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_delete)* |
| ![Icono de envío de identificadores de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image25.png)    | **Envío de identificadores de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_handles_send)* |
| ![Icono de obtención de información de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image26.png)    | **Obtención de información de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_info_get)* |
| ![Icono de envío de información de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image27.png)    | **Envío de información de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_object_info_send)* |
| ![Icono de envío de número de objetos de clase PIMA de dispositivo](./media/user-guide/usbx-events/image28.png)    | **Envío de número de objetos de clase PIMA de dispositivo** *(ux_device_class_pima_objects_number_send)* |
| ![Icono de obtención de datos parciales de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image29.png)    | **Obtención de datos parciales de objeto de clase PIMA de dispositivo** *(ux_device_class_pima_partial_object_data_get)* |
| ![Icono de envío de respuesta de clase PIMA de dispositivo](./media/user-guide/usbx-events/image30.png)    | **Envío de respuesta de clase PIMA de dispositivo** *(ux_device_class_pima_response_send)*|
| ![Icono de envío de identificador de almacenamiento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image31.png)    | **Envío de ID de almacenamiento de clase PIMA de dispositivo** *(ux_device_class_pima_storage_id_send)* |
| ![Icono de envío de información de almacenamiento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image32.png)    | **Envío de información de almacenamiento de clase PIMA de dispositivo** *(ux_device_class_pima_storage_info_send)* |
| ![Icono de activación de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image33.png)    | **Activación de clase RNDIS de dispositivo** *(ux_device_class_rndis_activate)* |
| ![Icono de desactivación de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image34.png)    | **Desactivación de clase RNDIS de dispositivo** *(ux_device_class_rndis_deactivate)* |
| ![Icono de mantenimiento de conexión de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image35.png)    | **Mantenimiento de conexión de mensaje de clase RNDIS de dispositivo** *(ux_device_class_rndis_msg_keep_alive)* |
| ![Icono de consulta de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image36.png)    | **Consulta de mensaje de clase RNDIS de dispositivo** *(ux_device_class_rndis_msg_query)* |
| ![Icono de restablecimiento de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image37.png)    | **Restablecimiento de mensaje de clase RNDIS de dispositivo** *(ux_device_class_rndis_msg_reset)* |
| ![Icono de establecimiento de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image38.png)    | **Establecimiento de mensaje de clase RNDIS de dispositivo** *(ux_device_class_rndis_msg_set)* |
| ![Icono de recepción de paquete de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image39.png)    | **Recepción de paquetes de clase RNDIS de dispositivo** *(ux_device_class_rndis_packet_receive)* |
| ![Icono de transmisión de paquete de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image40.png)    | **Transmisión de paquetes de clase RNDIS de dispositivo** *(ux_device_class_rndis_packet_transmit)* |
| ![Icono de activación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image41.png)    | **Activación de clase STORAGE de dispositivo** *(ux_device_class_storage_activate)* |
| ![Icono de desactivación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image42.png)    | **Desactivación de clase STORAGE de dispositivo** *(ux_device_class_storage_deactivate)* |
| ![Icono de formato de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image43.png)    | **Formato de clase STORAGE de dispositivo** *(ux_device_class_storage_format)* |
| ![Icono de consulta de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image44.png)    | **Consulta de clase STORAGE de dispositivo** *(ux_device_class_storage_inquiry)* |
| ![Icono de selección de modo de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image45.png)    | **Selección de modo de clase STORAGE de dispositivo** *(ux_device_class_storage_mode_select)* |
| ![Icono de detección de modo de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image46.png)    | **Detección de modo de clase STORAGE de dispositivo** *(ux_device_class_storage_mode_sense)* |
| ![Icono de impedir/permitir extracción de soporte físico de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image47.png)    | **Impedir/permitir extracción de soporte físico de clase STORAGE de dispositivo** *(ux_device_class_storage_prevent_allow_media_removal)* |
| ![Icono de lectura de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image48.png)    | **Lectura de clase STORAGE de dispositivo** *(ux_device_class_storage_read)* |
| ![Icono de lectura de capacidad de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image49.png)    | **Lectura de capacidad de clase STORAGE de dispositivo** *(ux_device_class_storage_read_capacity)* |
| ![Icono de lectura de capacidad de formato de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image50.png)    | **Lectura de capacidad de formato de clase STORAGE de dispositivo** *(ux_device_class_storage_read_format_capacity)* |
| ![Icono de lectura de tabla de contenido de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image51.png)    | **Lectura de tabla de contenido de clase STORAGE de dispositivo** *(ux_device_class_storage_read_toc)* |
| ![Icono de detección de solicitud de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image52.png)    | **Detección de solicitud de clase STORAGE de dispositivo** *(ux_device_class_storage_request_sense)* |
| ![Icono de inicio/parada de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image53.png)    | **Inicio/parada de clase STORAGE de dispositivo** *(ux_device_class_storage_start_stop)* |
| ![Icono de prueba de unidad preparada de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image54.png)    | **Prueba de unidad preparada de clase STORAGE de dispositivo** *(ux_device_class_storage_test_ready)* |
| ![Icono de comprobación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image55.png)    | **Comprobación de clase STORAGE de dispositivo** *(ux_device_class_storage_verify)* |
| ![Icono de escritura de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image56.png)    | **Escritura de clase STORAGE de dispositivo** *(ux_device_class_storage_write)* |
| ![Icono de obtención de configuración alternativa de pila de dispositivos](./media/user-guide/usbx-events/image57.png)    | **Obtención de configuración alternativa de pila de dispositivos** *(ux_device_stack_alternate_setting_get)* |
| ![Icono de establecimiento de configuración alternativa de pila de dispositivos](./media/user-guide/usbx-events/image58.png)    | **Establecimiento de configuración alternativa de pila de dispositivos** *(ux_device_stack_alternate_setting_set)* |
| ![Icono de registro de clase de pila de dispositivos](./media/user-guide/usbx-events/image59.png)    | **Registro de clase de pila de dispositivos** *(ux_device_stack_class_register)* |
| ![Icono de borrado de característica de pila de dispositivos](./media/user-guide/usbx-events/image60.png)    | **Borrado de característica de pila de dispositivos** *(ux_device_stack_clear_feature)* |
| ![Icono de obtención de configuración de pila de dispositivos](./media/user-guide/usbx-events/image61.png)    | **Obtención de configuración de pila de dispositivos** *(ux_device_stack_configuration_get)* |
| ![Icono de establecimiento de configuración de pila de dispositivos](./media/user-guide/usbx-events/image62.png)    | **Establecimiento de configuración de pila de dispositivos** *(ux_device_stack_configuration_set)* |
| ![Icono de conexión de pila de dispositivos](./media/user-guide/usbx-events/image63.png)    | **Conexión de pila de dispositivos** *(ux_device_stack_connect)* |
| ![Icono de envío de descriptor de pila de dispositivos](./media/user-guide/usbx-events/image64.png)    | **Envío de descriptor de pila de dispositivos** *(ux_device_stack_descriptor_send)* |
| ![Icono de desconexión de pila de dispositivos](./media/user-guide/usbx-events/image65.png)    | **Desconexión de pila de dispositivos** *(ux_device_stack_disconnect)* |
| ![Icono de detención de punto de conexión de pila de dispositivos](./media/user-guide/usbx-events/image66.png)    | **Detención de punto de conexión de pila de dispositivo** *(ux_device_stack_endpoint_stall)* |
| ![Icono de obtención de estado de pila de dispositivos](./media/user-guide/usbx-events/image67.png)    | **Obtención de estado de pila de dispositivos** *(ux_device_stack_get_status)* |
| ![Icono de reactivación de host de pila de dispositivos](./media/user-guide/usbx-events/image68.png)    | **Reactivación de host de pila de dispositivos** *(ux_device_stack_host_wakeup)* |
| ![Icono de inicialización de pila de dispositivos](./media/user-guide/usbx-events/image69.png)    | **Inicialización de pila de dispositivos** *(ux_device_stack_initialize)* |
| ![Icono de eliminación de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image70.png)    | **Eliminación de interfaz de pila de dispositivos** *(ux_device_stack_interface_delete)* |
| ![Icono de obtención de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image71.png)    | **Obtención de interfaz de pila de dispositivos** *(ux_device_stack_interface_get)* |
| ![Icono de establecimiento de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image72.png)    | **Establecimiento de interfaz de pila de dispositivos** *(ux_device_stack_interface_set)* |
| ![Icono de establecimiento de característica de pila de dispositivos](./media/user-guide/usbx-events/image73.png)    | **Establecimiento de característica de pila de dispositivos** *(ux_device_stack_set_feature)* |
| ![Icono de anulación de transferencia de pila de dispositivos](./media/user-guide/usbx-events/image74.png)    | **Anulación de transferencia de pila de dispositivos** *(ux_device_stack_transfer_abort)* |
| ![*Icono de anulación de todas las solicitudes de transferencia de la pila de dispositivos](./media/user-guide/usbx-events/image75.png)    | **Anulación de todas las solicitudes de transferencia de la pila de dispositivos** *(ux_device_stack_transfer_all_request_abort)* |
| ![Icono de solicitud de transferencia de pila de dispositivos](./media/user-guide/usbx-events/image76.png)    | **Solicitud de transferencia de pila de dispositivos** *(ux_device_stack_transfer_request)* |
| ![Icono de activación de clase ASIX de host](./media/user-guide/usbx-events/image77.png)    | **Activación de clase ASIX de host** *(ux_host_class_asix_activate)* |
| ![Icono de desactivación de clase ASIX de host](./media/user-guide/usbx-events/image78.png)    | **Desactivación de clase ASIX de host** *(ux_host_class_asix_deactivate)* |
| ![Icono de notificación de interrupción de clase ASIX de host](./media/user-guide/usbx-events/image79.png)    | **Notificación de interrupción de clase ASIX de host** *(ux_host_class_asix_interrupt_notification)* |
| ![Icono de lectura de clase ASIX de host](./media/user-guide/usbx-events/image80.png)    | **Lectura de clase ASIX de host** *(ux_host_class_asix_read)* |
| ![Icono de escritura de clase ASIX de host](./media/user-guide/usbx-events/image81.png)    | **Escritura de clase ASIX de host** *(ux_host_class_asix_write)* |
| ![Icono de activación de clase AUDIO de host](./media/user-guide/usbx-events/image82.png)    | **Activación de clase AUDIO de host** *(ux_host_class_audio_activate)* |
| ![Icono de obtención de valor de control de clase AUDIO de host](./media/user-guide/usbx-events/image83.png)    | **Obtención de valor de control de clase AUDIO de host** *(ux_host_class_audio_control_value_get)* |
| ![Icono de establecimiento de valor de control de clase AUDIO de host](./media/user-guide/usbx-events/image84.png)    | **Establecimiento de valor de control de clase AUDIO de host** *(ux_host_class_audio_control_value_set)* |
| ![Icono de desactivación de clase AUDIO de host](./media/user-guide/usbx-events/image85.png)    | **Desactivación de clase AUDIO de host** *(ux_host_class_audio_deactivate)* |
| ![Icono de lectura de clase AUDIO de host](./media/user-guide/usbx-events/image86.png)    | **Lectura de clase AUDIO de host** *(ux_host_class_audio_read)* |
| ![Icono de obtención de muestreo de streaming de clase AUDIO de host](./media/user-guide/usbx-events/image87.png)    | **Obtención de muestreo de streaming de clase AUDIO de host** *(ux_host_class_audio_streaming_sampling_get)* |
| ![Icono de establecimiento de muestreo de streaming de clase AUDIO de host](./media/user-guide/usbx-events/image88.png)    | **Establecimiento de muestreo de streaming de clase AUDIO de host** *(ux_host_class_audio_streaming_sampling_set)* |
| ![Icono de escritura de clase AUDIO de host](./media/user-guide/usbx-events/image89.png)    | **Escritura de clase AUDIO de host** *(ux_host_class_audio_write)* |
| ![Icono de activación de clase C D C A C M de host](./media/user-guide/usbx-events/image90.png)    | **Activación de clase CDC ACM de host** *(ux_host_class_cdc_acm_activate)* |
| ![Icono de desactivación de clase C D C A C M de host](./media/user-guide/usbx-events/image91.png)    | **Desactivación de clase CDC ACM de host** *(ux_host_class_cdc_acm_deactivate)* |
| ![Icono de función I O C T L de canalización de entrada de clase C D C A C M de host](./media/user-guide/usbx-events/image92.png)    | **Función IOCTL de anulación de canalización de entrada de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)* |
| ![Icono de función I O C T L de anulación de canalización de salida de clase C D C A C M de host](./media/user-guide/usbx-events/image93.png)    | **Función IOCTL de anulación de canalización de salida de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)* |
| ![Icono de función I O C T L de obtención de estado de dispositivo de clase C D C A C M de host](./media/user-guide/usbx-events/image94.png)    | **Función IOCTL de obtención de estado de dispositivo de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_get_device_status)* |
| ![Icono de función I O C T L de obtención de codificación de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image95.png)    | **Función IOCTL de obtención de codificación de línea de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_get_line_coding)* |
| ![Icono de función I O C T L de devolución de llamada de notificación de clase C D C A C M de host](./media/user-guide/usbx-events/image96.png)    | **Función IOCTL de devolución de llamada de notificación de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_notification_callback)* |
| ![Icono de función I O C T L de interrupción de envío de clase C D C A C M de host](./media/user-guide/usbx-events/image97.png)    | **Función IOCTL de interrupción de envío de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_send_break)* |
| ![Icono de función I O C T L de establecimiento de codificación de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image98.png)    | **Función IOCTL de establecimiento de codificación de línea de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_set_line_coding)* |
| ![Icono de función I O C T L de establecimiento de estado de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image99.png)    | **Función IOCTL de establecimiento de estado de línea de clase CDC ACM de host** *(ux_host_class_cdc_acm_ioctl_set_line_state)* |
| ![Icono de lectura de clase C D C A C M de host](./media/user-guide/usbx-events/image100.png)    | **Lectura de clase C D C A C M de host** *(ux_host_class_cdc_acm_read)* |
| ![Icono de inicio de recepción de clase C D C A C M de host](./media/user-guide/usbx-events/image101.png)    | **Inicio de recepción de clase C D C A C M de host** *(ux_host_class_cdc_acm_reception_start)* |
| ![Icono de parada de recepción de clase C D C A C M de host](./media/user-guide/usbx-events/image102.png)    | **Parada de recepción de clase C D C A C M de host** *(ux_host_class_cdc_acm_reception_stop)* |
| ![Icono de escritura de clase C D C A C M de host](./media/user-guide/usbx-events/image103.png)    | **Escritura de clase C D C A C M de host** *(ux_host_class_cdc_acm_write)* |
| ![Icono de activación de clase DPUMP de host](./media/user-guide/usbx-events/image104.png)    | **Activación de clase DPUMP de host** *(ux_host_class_dpump_activate)* |
| ![Icono de desactivación de clase DPUMP de host](./media/user-guide/usbx-events/image105.png)    | **Desactivación de clase DPUMP de host** *(ux_host_class_dpump_deactivate)* |
| ![Icono de lectura de clase DPUMP de host](./media/user-guide/usbx-events/image106.png)    | **Lectura de clase DPUMP de host** *(ux_host_class_dpump_read)* |
| ![Icono de escritura de clase DPUMP de host](./media/user-guide/usbx-events/image107.png)    | **Escritura de clase DPUMP de host** *(ux_host_class_dpump_write)* |
| ![Icono de activación de clase HID de host](./media/user-guide/usbx-events/image108.png)    | **Activación de clase HID de host** *(ux_host_class_hid_activate)* |
| ![Icono de registro de cliente de clase HID de host](./media/user-guide/usbx-events/image109.png)    | **Registro de cliente de clase HID de host** *(ux_host_class_hid_client_register)* |
| ![Icono de desactivación de clase HID de host](./media/user-guide/usbx-events/image110.png)    | **Desactivación de clase HID de host** *(ux_host_class_hid_deactivate)* |
| ![Icono de obtención de inactividad de clase HID de host](./media/user-guide/usbx-events/image111.png)    | **Obtención de inactividad de clase HID de host** *(ux_host_class_hid_idle_get)* |
| ![Icono de establecimiento de inactividad de clase HID de host](./media/user-guide/usbx-events/image112.png)    | **Establecimiento de inactividad de clase HID de host** *(ux_host_class_hid_idle_set)* |
| ![Icono de activación de teclado de clase HID de host](./media/user-guide/usbx-events/image113.png)    | **Activación de teclado de clase HID de host** *(ux_host_class_hid_keyboard_activate)* |
| ![Icono de desactivación de teclado de clase HID de host](./media/user-guide/usbx-events/image114.png)    | **Desactivación de teclado de clase HID de host** *(ux_host_class_hid_keyboard_deactivate)* |
| ![Icono de activación de mouse de clase HID de host](./media/user-guide/usbx-events/image115.png)    | **Activación de mouse de clase HID de host** *(ux_host_class_hid_mouse_activate)* |
| ![Icono de desactivación de mouse de clase HID de host](./media/user-guide/usbx-events/image116.png)    | **Desactivación de mouse de clase HID de host** *(ux_host_class_hid_mouse_deactivate)* |
| ![Icono de activación de control remoto de clase HID de host](./media/user-guide/usbx-events/image117.png)    | **Activación de control remoto de clase HID de host** *(ux_host_class_hid_remote_control_activate)* |
| ![Icono de desactivación de control remoto de clase HID de host](./media/user-guide/usbx-events/image118.png)    | **Desactivación de control remoto de clase HID de host** *(ux_host_class_hid_remote_control_deactivate)* |
| ![Icono de obtención de informe de clase HID de host](./media/user-guide/usbx-events/image119.png)    | **Obtención de informe de clase HID de host** *(ux_host_class_hid_report_get)* |
| ![Icono de establecimiento de informe de clase HID de host](./media/user-guide/usbx-events/image120.png)    | **Establecimiento de informe de clase HID de host** *(ux_host_class_hid_report_set)* |
| ![Icono de activación de clase HUB de host](./media/user-guide/usbx-events/image121.png)    | **Activación de clase HUB de host** *(ux_host_class_hub_activate)* |
| ![Icono de detección de cambio de clase HUB de host](./media/user-guide/usbx-events/image122.png)    | **Detección de cambio de clase HUB de host** *(ux_host_class_hub_change_detect)* |
| ![*Icono de desactivación de clase HUB de host](./media/user-guide/usbx-events/image123.png)    | **Desactivación de clase HUB de host** *(ux_host_class_hub_deactivate)* |
| ![Icono de proceso de cambio de puerto de conexión de clase HUB de host](./media/user-guide/usbx-events/image124.png)    | **Proceso de cambio de puerto de conexión de clase HUB de host** *(ux_host_class_hub_port_change_connection_process)* |
| ![Icono de habilitación de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image125.png)    | **Habilitación de proceso de cambio de puerto de clase HUB de host** *(ux_host_class_hub_port_change_enable_process)* |
| ![Icono de proceso actual finalizado de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image126.png)    | **Proceso actual finalizado de cambio de puerto de clase HUB de host** *(ux_host_class_hub_port_change_over_current_process)* |
| ![Icono de restablecimiento de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image127.png)    | **Restablecimiento de proceso de cambio de puerto de clase HUB de host** *(ux_host_class_hub_port_change_reset_process)* |
| ![Icono de suspensión de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image128.png)    | **Suspensión de proceso de cambio de puerto de clase HUB de host** *(ux_host_class_hub_port_change_suspend_process)* |
| ![Icono de activación de clase PIMA de host](./media/user-guide/usbx-events/image129.png)    | **Activación de clase PIMA de host** *(ux_host_class_prima_activate)* |
| ![Icono de desactivación de clase PIMA de host](./media/user-guide/usbx-events/image130.png)    | **Desactivación de clase PIMA de host** *(ux_host_class_pima_deactivate)* |
| ![Icono de obtención de información de dispositivo de clase PIMA de host](./media/user-guide/usbx-events/image131.png)    | **Obtención de información de dispositivo de clase PIMA de host** *(ux_host_class_pima_device_info_get)* |
| ![Icono de restablecimiento de dispositivo de clase PIMA de host](./media/user-guide/usbx-events/image132.png)    | **Restablecimiento de dispositivo de clase PIMA de host** *(ux_host_class_pima_device_reset)* |
| ![Icono de notificación de clase PIMA de host](./media/user-guide/usbx-events/image133.png)    | **Notificación de clase PIMA de host** *(ux_host_class_pima_notification)* |
| ![Icono de obtención de objetos de clase PIMA de host](./media/user-guide/usbx-events/image134.png)    | **Obtención de número de objetos de clase PIMA de host** *(ux_host_class_pima_num_objects_get)* |
| ![Icono de cierre de objeto de clase PIMA de host](./media/user-guide/usbx-events/image135.png)    | **Cierre de objeto de clase PIMA de host** *(ux_host_class_pima_object_close)* |
| ![Icono de copia de objeto de clase PIMA de host](./media/user-guide/usbx-events/image136.png)    | **Copia de objeto de clase PIMA de host** *(ux_host_class_pima_object_copy)* |
| ![Icono de eliminación de objeto de clase PIMA de host](./media/user-guide/usbx-events/image137.png)    | **Eliminación de objeto de clase PIMA de host** *(ux_host_class_pima_object_delete)* |
| ![Icono de obtención de objeto de clase PIMA de host](./media/user-guide/usbx-events/image138.png)    | **Obtención de objeto de clase PIMA de host** *(ux_host_class_pima_object_get)* |
| ![Icono de obtención de información de objeto de clase PIMA de host](./media/user-guide/usbx-events/image139.png)    | **Obtención de información de objeto de clase PIMA de host** *(ux_host_class_pima_object_info_get)* |
| ![Icono de envío de información de objeto de clase PIMA de host](./media/user-guide/usbx-events/image140.png)    | **Envío de información de objeto de clase PIMA de host** *(ux_host_class_pima_object_info_send)* |
| ![Icono de movimiento de objeto de clase PIMA de host](./media/user-guide/usbx-events/image141.png)    | **Movimiento de objeto de clase PIMA de host** *(ux_host_class_pima_object_move)* |
| ![Icono de envío de objeto de clase PIMA de host](./media/user-guide/usbx-events/image142.png)    | **Envío de objeto de clase PIMA de host** *(ux_host_class_pima_object_send)* |
| ![Icono de anulación de transferencia de objeto de clase PIMA de host](./media/user-guide/usbx-events/image143.png)    | **Anulación de transferencia de objeto de clase PIMA de host** *(ux_host_class_object_transfer_abort)* |
| ![Icono de lectura de clase PIMA de host](./media/user-guide/usbx-events/image144.png)    | **Lectura de clase PIMA de host** *(ux_host_class_pima_read)* |
| ![Icono de cancelación de solicitud de clase PIMA de host](./media/user-guide/usbx-events/image145.png)    | **Cancelación de solicitud de clase PIMA de host** *(ux_host_class_pima_request_cancel)* |
| ![Icono de cierre de sesión de clase PIMA de host](./media/user-guide/usbx-events/image146.png)    | **Cierre de sesión de clase PIMA de host** *(ux_host_class_pima_session_close)* |
| ![Icono de apertura de sesión de clase PIMA de host](./media/user-guide/usbx-events/image147.png)    | **Apertura de sesión de clase PIMA de host** *(ux_host_class_pima_session_open)* |
| ![Icono de obtención de identificadores de almacenamiento de clase PIMA de host](./media/user-guide/usbx-events/image148.png)    | **Obtención de identificadores de almacenamiento de clase PIMA de host** *(ux_host_class_pima_storage_ids_get)* |
| ![Icono de obtención de información de almacenamiento de clase PIMA de host](./media/user-guide/usbx-events/image149.png)    | **Obtención de información de almacenamiento de clase PIMA de host** *(ux_host_class_pima_storage_info_get)* |
| ![Icono de obtención de miniatura de clase PIMA de host](./media/user-guide/usbx-events/image150.png)    | **Obtención de miniatura de clase PIMA de host** *(ux_host_class_pima_thumb_get)* |
| ![Icono de escritura de clase PIMA de host](./media/user-guide/usbx-events/image151.png)    | **Escritura de clase PIMA de host** *(ux_host_class_pima_write)* |
| ![Icono de activación de clase PRINTER de host](./media/user-guide/usbx-events/image152.png)    | **Activación de clase PRINTER de host** *(ux_host_class_printer_activate)* |
| ![Icono de desactivación de clase PRINTER de host](./media/user-guide/usbx-events/image153.png)    | **Desactivación de clase PRINTER de host** *(ux_host_class_printer_deactivate)* |
| ![Icono de obtención de nombre de clase PRINTER de host](./media/user-guide/usbx-events/image154.png)    | **Obtención de nombre de clase PRINTER de host** *(ux_host_class_printer_name_get)* |
| ![Icono de lectura de clase PRINTER de host](./media/user-guide/usbx-events/image155.png)    |  **Lectura de clase PRINTER de host** *(ux_host_class_printer_read)* |
| ![Icono de restablecimiento parcial de clase PRINTER de host](./media/user-guide/usbx-events/image156.png)    | **Restablecimiento parcial de clase PRINTER de host** *(ux_host_class_printer_soft_reset)* |
| ![Icono de obtención de estado de clase PRINTER de host](./media/user-guide/usbx-events/image157.png)    | **Obtención de estado de clase PRINTER de host** *(ux_host_class_printer_status_get)* |
| ![Icono de escritura de clase PRINTER de host](./media/user-guide/usbx-events/image158.png)    | **Escritura de clase PRINTER de host** *(ux_host_class_printer_write)* |
| ![Icono de activación de clase PROLIFIC de host](./media/user-guide/usbx-events/image159.png)    | **Activación de clase PROLIFIC de host** *(ux_host_class_prolific_activate)* |
| ![Icono de desactivación de clase PROLIFIC de host](./media/user-guide/usbx-events/image160.png)    | **Desactivación de clase PROLIFIC de host** *(ux_host_class_prolific_deactivate)* |
| ![Icono de función I O C T L de anulación de canalización de entrada de clase PROLIFIC de host](./media/user-guide/usbx-events/image161.png)    | **Función IOCTL de anulación de canalización de entrada de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_abort_in_pipe)* |
| ![Icono de función I O C T L de anulación de canalización de salida de clase PROLIFIC de host](./media/user-guide/usbx-events/image162.png)    | **Función IOCTL de anulación de canalización de salida de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_abort_out_pipe)* |
| ![Icono de función I O C T L de obtención de estado de dispositivo de clase PROLIFIC de host](./media/user-guide/usbx-events/image163.png)    | **Función IOCTL de obtención de estado de dispositivo de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_get_device_status)* |
| ![Icono de función I O C T L de obtención de codificación de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image164.png)    | **Función IOCTL de obtención de codificación de línea de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_get_line_coding)* |
| ![Icono de función I O C T L de depuración de clase PROLIFIC de host](./media/user-guide/usbx-events/image165.png)    | **Función IOCTL de depuración de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_purge)* |
| ![Icono de función I O C T L de informe de cambio de estado de dispositivo de clase PROLIFIC de host](./media/user-guide/usbx-events/image166.png)    | **Función IOCTL de informe de cambio de estado de dispositivo de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_report_device_status_change)* |
| ![Icono de función I O C T L de interrupción de envío de clase PROLIFIC de host](./media/user-guide/usbx-events/image167.png)    | **Función IOCTL de interrupción de envío de clase PROLIFIC de host** *(ux_host_class_prolific_send_break)* |
| ![Icono de función I O C T L de establecimiento de codificación de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image168.png)    | **Función IOCTL de establecimiento de codificación de línea de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_set_line_coding)* |
| ![Icono de función I O C T L de establecimiento de estado de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image169.png)    | **Función IOCTL de establecimiento de estado de línea de clase PROLIFIC de host** *(ux_host_class_prolific_ioctl_set_line_state)* |
| ![Icono de lectura de clase PROLIFIC de host](./media/user-guide/usbx-events/image170.png)    | **Lectura de clase PROLIFIC de host** *(ux_host_class_prolific_read)* |
| ![Icono de inicio de recepción de clase PROLIFIC de host](./media/user-guide/usbx-events/image171.png)    | **Inicio de recepción de clase PROLIFIC de host** *(ux_host_class_prolific_reception_start)* |
| ![Icono de parada de recepción de clase PROLIFIC de host](./media/user-guide/usbx-events/image172.png)    | **Parada de recepción de clase PROLIFIC de host** *(ux_host_class_prolific_reception_stop)* |
| ![Icono de escritura de clase PROLIFIC de host](./media/user-guide/usbx-events/image173.png)    | **Escritura de clase PROLIFIC de host** *(ux_host_class_prolific_write)* |
| ![Icono de activación de clase STORAGE de host](./media/user-guide/usbx-events/image174.png)    | **Activación de clase STORAGE de host** *(ux_host_class_storage_activate)* |
| ![Icono de desactivación de clase STORAGE de host](./media/user-guide/usbx-events/image175.png)    | **Desactivación de clase STORAGE de host** (*ux_host_class_storage_deactivate)* |
| ![Icono de obtención de capacidad de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image176.png)    | **Obtención de capacidad de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_capacity_get)* |
| ![Icono de obtención de capacidad de formato de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image177.png)    | **Obtención de capacidad de formato de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_format_capacity_get)* |
| ![Icono de montaje de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image178.png)    | **Montaje de soporte físico de clase STORAGE de host** (ux_host_class_storage_media_mount)* |
| ![Icono de apertura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image179.png)    | **Apertura de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_open)* |
| ![Icono de lectura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image180.png)    | **Lectura de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_read)* |
| ![Icono de escritura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image181.png)    | **Escritura de soporte físico de clase STORAGE de host** *(ux_host_class_storage_media_write)* |
| ![Icono de detección de solicitud de clase STORAGE de host](./media/user-guide/usbx-events/image182.png)    | **Detección de solicitud de clase STORAGE de host** *(ux_host_class_storage_request_sense)* |
| ![Icono de inicio/parada inicio de clase STORAGE de host](./media/user-guide/usbx-events/image183.png)    | **Inicio/parada inicio de clase STORAGE de host** *(ux_host_class_storage_start_stop)* |
| ![Icono de prueba de unidad preparada de clase STORAGE de host](./media/user-guide/usbx-events/image184.png)    | **Prueba de unidad preparada de clase STORAGE de host** *(ux_host_class_storage_activate)* |
| ![Icono de creación de instancia de clase de pila de hosts](./media/user-guide/usbx-events/image185.png)    | **Creación de instancia de clase de pila de hosts** *(ux_host_stack_class_instance_create)* |
| ![Icono de destrucción de instancia de clase de pila de hosts](./media/user-guide/usbx-events/image186.png)    | **Destrucción de instancia de clase de pila de hosts** *(ux_host_stack_class_instance_destroy)* |
| ![Icono de eliminación de configuración de pila de hosts](./media/user-guide/usbx-events/image187.png)    | **Eliminación de configuración de pila de hosts** *(ux_host_stack_configuration_delete)* |
| ![Icono de enumeración de configuración de pila de hosts](./media/user-guide/usbx-events/image188.png)    | **Enumeración de configuración de pila de hosts** *(ux_host_stack_configuration_enumerate)* |
| ![Icono de creación de instancia de configuración de pila de hosts](./media/user-guide/usbx-events/image189.png)    | **Creación de instancia de configuración de pila de hosts** *(ux_host_stack_configuration_instance_create)* |
| ![Icono de eliminación de instancia de configuración de pila de hosts](./media/user-guide/usbx-events/image190.png)    | **Eliminación de instancia de configuración de pila de hosts** *(ux_host_stack_configuration_instance_delete)* |
| ![Icono de establecimiento de configuración de pila de hosts](./media/user-guide/usbx-events/image191.png)    | **Establecimiento de configuración de pila de hosts** *(ux_host_stack_configuration_set)* |
| ![Icono de establecimiento de dirección de dispositivo de pila de hosts](./media/user-guide/usbx-events/image192.png)    | **Establecimiento de dirección de dispositivo de pila de hosts** *(ux_host_stack_device_set)* |
| ![Icono de obtención de configuración de dispositivo de pila de hosts](./media/user-guide/usbx-events/image193.png)    | **Obtención de configuración de dispositivo de pila de hosts** *(ux_host_stack_device_configuration_get)* |
| ![Icono de selección de configuración de dispositivo de pila de hosts](./media/user-guide/usbx-events/image194.png)    | **Selección de configuración de dispositivo de pila de hosts** *(ux_host_stack_device_configuration_select)* |
| ![Icono de lectura de descriptor de dispositivo de pila de hosts](./media/user-guide/usbx-events/image195.png)    | **Lectura de descriptor de dispositivo de pila de hosts** *(ux_host_stack_device_descriptor_read)* |
| ![Icono de obtención de dispositivo de pila de hosts](./media/user-guide/usbx-events/image196.png)    | **Obtención de dispositivo de pila de hosts** (ux_host_stack_device_get) |
| ![Icono de eliminación de dispositivo de pila de hosts](./media/user-guide/usbx-events/image197.png)    | **Eliminación de dispositivo de pila de hosts** (ux_host_stack_device_get) |
| ![Icono de recurso libre de dispositivo de pila de hosts](./media/user-guide/usbx-events/image198.png)    | **Recurso libre de dispositivo de pila de hosts** (ux_host_stack_device_resource_free) |
| ![Icono de creación de instancia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image199.png)    | **Creación de instancia de punto de conexión de pila de hosts** (ux_host_stack_endpoint_instance_create) |
| ![Icono de eliminación de instancia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image200.png)    | **Eliminación de instancia de punto de conexión de pila de hosts** (ux_host_stack_endpoint_instance_delete) |
| ![Icono de restablecimiento de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image201.png)    | **Restablecimiento de punto de conexión de pila de hosts** (ux_host_stack_endpoint_reset) |
| ![Icono de anulación de transferencia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image202.png)    | **Anulación de transferencia de punto de conexión de pila de hosts** (ux_host_stack_endpoint_transfer_abort) |
| ![Icono de registro de controlador de host de pila de hosts](./media/user-guide/usbx-events/image203.png)    | **Registro de controlador de host de pila de hosts** *(ux_host_stack_hcd_register)* |
| ![Icono de inicialización de pila de hosts](./media/user-guide/usbx-events/image204.png)    | **Inicialización de pila de hosts** *(ux_host_stack_initialize)* |
| ![Icono de obtención de punto de conexión de interfaz de pila de hosts](./media/user-guide/usbx-events/image205.png)    | **Obtención de punto de conexión de interfaz de pila de hosts** *(ux_host_stack_interface_endpoint_get)* |
| ![Icono de creación de instancia de interfaz de pila de hosts](./media/user-guide/usbx-events/image206.png)    | **Creación de instancia de interfaz de pila de hosts** *(ux_host_stack_interface_instance_create)* |
| ![Icono de eliminación de instancia de interfaz de pila de hosts](./media/user-guide/usbx-events/image207.png)    | **Eliminación de instancia de interfaz de pila de hosts** *(ux_host_stack_interface_instance_delete)* |
| ![Icono de establecimiento de interfaz de pila de hosts](./media/user-guide/usbx-events/image208.png)    | **Establecimiento de interfaz de pila de hosts** *(ux_host_stack_interface_set)* |
| ![Icono de selección de configuración de interfaz de pila de hosts](./media/user-guide/usbx-events/image209.png)    | **Selección de configuración de interfaz de pila de hosts** *(ux_host_stack_interface_setting_select)* |
| ![Icono de creación de nueva configuración de pila de hosts](./media/user-guide/usbx-events/image210.png)    | **Creación de nueva configuración de pila de hosts** *(ux_host_stack_new_configuration_create)* |
| ![Icono de creación de nuevo dispositivo de pila de hosts](./media/user-guide/usbx-events/image211.png)    | **Creación de nuevo dispositivo de pila de hosts** *(ux_host_stack_new_device_create)* |
| ![Icono de creación de nuevo punto de conexión de pila de hosts](./media/user-guide/usbx-events/image212.png)    | **Creación de nuevo punto de conexión de pila de hosts** *(ux_host_stack_new_endpoint_create)* |
| ![Icono de proceso de cambio de centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image213.png)    | **Proceso de cambio de centro de conectividad raíz de pila de hosts** *(ux_host_stack_rh_change_process)* |
| ![Icono de extracción de dispositivo de centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image214.png)    | **Extracción de dispositivo de centro de conectividad raíz de pila de hosts** *(ux_host_stack_rh_device_extraction)* |
| ![Icono de inserción de dispositivo en centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image215.png)    | **Inserción de dispositivo en centro de conectividad raíz de pila de hosts** *(ux_host_stack_rh_device_insertion)* |
| ![Icono de solicitud de transferencia de pila de hosts](./media/user-guide/usbx-events/image216.png)    | **Solicitud de transferencia de pila de hosts** *(ux_host_stack_transfer_request)* |
| ![Icono de anulación de solicitud de transferencia de pila de hosts](./media/user-guide/usbx-events/image217.png)    | **Anulación de solicitud de transferencia de pila de hosts** *(ux_host_stack_transfer_request_abort)* |
| ![Icono de error de U S B X](./media/user-guide/usbx-events/image218.png)    | **Error de USBX** *(ux_error)* |

## <a name="event-descriptions"></a>Descripciones de eventos

En las páginas siguientes se describen los eventos de seguimiento de USBX.

### <a name="device-class-cdc-activate"></a>Activación de clase CDC de dispositivo 

#### <a name="ux_device_class_cdc_activate"></a>ux_device_class_cdc_activate

**Icono** ![Icono de activación de clase C D C de dispositivo](./media/user-guide/usbx-events/image1.png)

**Descripción**

Este evento representa un evento de activación de la clase CDC del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-cdc-deactivate"></a>Desactivación de clase CDC de dispositivo 

#### <a name="ux_device_class_cdc_deactivate"></a>ux_device_class_cdc_deactivate

**Icono** ![Icono de desactivación de clase C D C de dispositivo](./media/user-guide/usbx-events/image2.png)

**Descripción**

Este evento representa una desactivación de la clase CDC del dispositivo USBX.

Campos de información 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-cdc-read"></a>Lectura de clase CDC de dispositivo 

#### <a name="ux_device_class_cdc_read"></a>ux_device_class_cdc_read

**Icono** ![Icono de lectura de clase C D C de dispositivo](./media/user-guide/usbx-events/image3.png)

**Descripción**

Este evento representa un evento de lectura de la clase CDC del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="device-class-cdc-write"></a>Escritura de clase CDC de dispositivo 

#### <a name="ux_device_class_cdc_write"></a>ux_device_class_cdc_write

**Icono** ![Icono de escritura de clase C D C de dispositivo](./media/user-guide/usbx-events/image4.png)

**Descripción**

Este evento representa un evento de escritura de la clase CDC del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="device-class-dpump-activate"></a>Activación de clase DPUMP de dispositivo 

#### <a name="ux_device_class_dpump_activate"></a>ux_device_class_dpump_activate

**Icono** ![Icono de activación de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image5.png)

**Descripción**

Este evento representa un evento de activación de la clase DPUMP del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-dpump-deactivate"></a>Desactivación de clase DPUMP de dispositivo 

#### <a name="ux_device_class_dpump_deactivate"></a>ux_device_class_dpump_deactivate

**Icono** ![Icono de desactivación de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image6.png)

**Descripción**

Este evento representa un evento de desactivación de la clase DPUMP del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-dpump-read"></a>Lectura de clase DPUMP de dispositivo 

#### <a name="ux_device_class_dpump_read"></a>ux_device_class_dpump_read

**Icono** ![Icono de lectura de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image7.png)

**Descripción**

Este evento representa un evento de lectura de la clase DPUMP del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: búfer
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="device-class-dpump-write"></a>Escritura de clase DPUMP de dispositivo 

#### <a name="ux_device_class_dpump_write"></a>ux_device_class_dpump_write

**Icono** ![Icono de escritura de clase DPUMP de dispositivo](./media/user-guide/usbx-events/image8.png)

**Descripción**

Este evento representa un evento de escritura de la clase DPUMP del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="device-class-hid-activate"></a>Activación de clase HID de dispositivo 

#### <a name="ux_device_class_hid_activate"></a>ux_device_class_hid_activate

**Icono** ![Icono de activación de clase H I D de dispositivo](./media/user-guide/usbx-events/image9.png)

**Descripción**

Este evento representa un evento de activación de la clase HID del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-hid-deactivate"></a>Desactivación de clase HID de dispositivo 

#### <a name="ux_device_class_hid_deactivate"></a>ux_device_class_hid_deactivate

**Icono** ![Icono de desactivación de clase H I D de dispositivo](./media/user-guide/usbx-events/image10.png)

**Descripción**

Este evento representa un evento de desactivación de la clase HID del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-hid-descriptor-send"></a>Envío de descriptor de clase HID de dispositivo 

#### <a name="ux_device_class_hid_descritpor_send"></a>ux_device_class_hid_descritpor_send

**Icono** ![Icono de envío de descriptor de clase H I D de dispositivo](./media/user-guide/usbx-events/image11.png)

**Descripción**

Este evento representa un evento de envío de descriptor de la clase HID del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: tipo de descriptor
- Campo de información 3: índice de la solicitud
- Campo de información 4: no se usa

### <a name="device-class-hid-event-get"></a>Obtención de evento de clase HID de dispositivo 

#### <a name="ux_device_class_hid_event_get"></a>ux_device_class_hid_event_get

**Icono** ![Icono de obtención de evento de clase H I D de dispositivo](./media/user-guide/usbx-events/image12.png)

**Descripción**

Este evento representa un evento de obtención de evento de la clase HID del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-hid-event-set"></a>Establecimiento de evento de clase HID de dispositivo 

#### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

**Icono** ![Icono de establecimiento de evento de clase H I D de dispositivo](./media/user-guide/usbx-events/image13.png)

**Descripción**

Este evento representa un evento de establecimiento de evento de la clase HID del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-hid-report-get"></a>Obtención de informe de clase HID de dispositivo 

#### <a name="ux_device_class_hid_report_get"></a>ux_device_class_hid_report_get

**Icono** ![Icono de obtención de informe de clase H I D de dispositivo](./media/user-guide/usbx-events/image14.png)

**Descripción**

Este evento representa un evento de obtención de informe de la clase HID del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: tipo de descriptor
- Campo de información 3: índice de la solicitud
- Campo de información 4: no se usa

### <a name="device-class-hid-report-set"></a>Establecimiento de informe de clase HID de dispositivo 

#### <a name="ux_device_class_hid_report_set"></a>ux_device_class_hid_report_set

**Icono** ![Icono de establecimiento de informe de clase H I D de dispositivo](./media/user-guide/usbx-events/image15.png)

**Descripción**

Este evento representa un evento de establecimiento de informe de la clase HID del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: tipo de descriptor
- Campo de información 3: índice de la solicitud
- Campo de información 4: no se usa

### <a name="device-class-pima-activate"></a>Activación de clase PIMA de dispositivo

#### <a name="ux_device_class_pima_activate"></a>ux_device_class_pima_activate

**Icono** ![Icono de activación de clase PIMA de dispositivo](./media/user-guide/usbx-events/image16.png)

**Descripción**

Este evento representa un evento de activación de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-deactivate"></a>Desactivación de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_deactivate"></a>ux_device_class_pima_deactivate

**Icono** ![Icono de desactivación de clase PIMA de dispositivo](./media/user-guide/usbx-events/image17.png)

**Descripción**

Este evento representa un evento de desactivación de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-device-info-send"></a>Envío de información de dispositivo de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_device_info_send"></a>ux_device_class_pima_device_info_send

**Icono** ![Icono de envío de información de dispositivo de clase PIMA de dispositivo](./media/user-guide/usbx-events/image18.png)

**Descripción**

Este evento representa un evento de envío de información de dispositivo de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa

### <a name="device-class-pima-event-get"></a>Obtención de evento de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_event_get"></a>ux_device_class_pima_event_get

**Icono** ![Icono de obtención de evento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image19.png)

**Descripción**

Este evento representa un evento de obtención de evento de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: evento de PIMA
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-event-set"></a>Establecimiento de evento de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_event_set"></a>ux_device_class_pima_event_set

**Icono** ![Icono de establecimiento de evento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image20.png)

**Descripción**

Este evento representa un evento de establecimiento de evento de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: evento de PIMA
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-object-add"></a>Adición de objeto de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

**Icono** ![Icono de adición de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image21.png)

**Descripción**

Este evento representa un evento de adición de objeto de la clase PIMA del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-object-data-get"></a>Obtención de datos de objeto de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

**Icono** ![Icono de obtención de datos de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image22.png)

**Descripción**

Este evento representa un evento de obtención de datos de objeto de la clase PIMA del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-object-data-send"></a>Envío de datos de objeto de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

**Icono** ![Icono de envío de datos de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image23.png)

**Descripción**

Este evento representa un evento de envío de datos de objeto de la clase PIMA del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-object-delete"></a>Eliminación de objeto de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

**Icono** ![Icono de eliminación de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image24.png)

**Descripción**

Este evento representa un evento de eliminación de objeto de la clase PIMA del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-object-handles-send"></a>Envío de identificadores de objeto de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_object_handles_send"></a>ux_device_class_pima_object_handles_send

**Icono** ![Icono de envío de identificadores de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image25.png)

**Descripción**

Este evento representa un evento de envío de identificadores de objeto de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador de almacenamiento
- Campo de información 3: código de formato de objeto
- Campo de información 4: asociación de objetos

### <a name="device-class-pima-object-info-get"></a>Obtención de información de objeto de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Icono** ![Icono de obtención de información de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image26.png)

**Descripción**

Este evento representa un evento de obtención de información de objeto de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-object-info-send"></a>Envío de información de objeto de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Icono** ![Icono de envío de información de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image27.png)

**Descripción**

Este evento representa un evento de envío de información de objeto de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-objects-number-send"></a>Envío de número de objetos de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_object_number_send"></a>ux_device_class_pima_object_number_send

**Icono** ![Icono de envío de número de objetos de clase PIMA de dispositivo](./media/user-guide/usbx-events/image28.png)

**Descripción**

Este evento representa un evento de envío de número de objetos de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador de almacenamiento
- Campo de información 3: código de formato de objeto
- Campo de información 4: asociación de objetos

### <a name="device-class-pima-partial-object-data-get"></a>Obtención de datos parciales de objeto de clase PIMA de dispositivo

#### <a name="ux_device_class_pima_partial_object_data_get"></a>ux_device_class_pima_partial_object_data_get

**Icono** ![Icono de obtención de datos parciales de objeto de clase PIMA de dispositivo](./media/user-guide/usbx-events/image29.png)

**Descripción**

Este evento representa un evento de obtención de datos parciales de objeto de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: desplazamiento solicitado
- Campo de información 4: longitud solicitada

### <a name="device-class-pima-response-send"></a>Envío de respuesta de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_response_send"></a>ux_device_class_pima_response_send

**Icono** ![Icono de envío de respuesta de clase PIMA de dispositivo](./media/user-guide/usbx-events/image30.png)

**Descripción**

Este evento representa un evento de envío de respuesta de la clase PIMA del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: código de respuesta
- Campo de información 3: parámetro de número
- Campo de información 4: parámetro de PIMA 1

### <a name="device-class-pima-storage-id-send"></a>Envío de identificador de almacenamiento de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_storage_id_send"></a>ux_device_class_pima_storage_id_send

**Icono** ![Icono de envío de identificador de almacenamiento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image31.png)

**Descripción**

Este evento representa un evento de envío de identificador de almacenamiento de la clase PIMA del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-pima-storage-info-send"></a>Envío de información de almacenamiento de clase PIMA de dispositivo 

#### <a name="ux_device_class_pima_storage_info_send"></a>ux_device_class_pima_storage_info_send

**Icono** ![Icono de envío de información de almacenamiento de clase PIMA de dispositivo](./media/user-guide/usbx-events/image32.png)

**Descripción**

Este evento representa un evento de envío de información de almacenamiento de la clase PIMA del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-rndis-activate"></a>Activación de clase RNDIS de dispositivo 

#### <a name="ux_device_class_rndis_activate"></a>ux_device_class_rndis_activate

**Icono** ![Icono de activación de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image33.png)

**Descripción**

Este evento representa un evento de activación de la clase RNDIS del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-rndis-deactivate"></a>Desactivación de clase RNDIS de dispositivo 

#### <a name="ux_device_class_rndis_deactivate"></a>ux_device_class_rndis_deactivate

**Icono** ![Icono de desactivación de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image34.png)

**Descripción**

Este evento representa un evento de desactivación de la clase RNDIS del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-rndis-message-keep-alive"></a>Mantenimiento de conexión de mensaje de clase RNDIS de dispositivo 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a>ux_device_class_rndis_msg_keep_alive

**Icono** ![Icono de mantenimiento de conexión de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image35.png)

**Descripción**

Este evento representa un evento de mantenimiento de conexión de mensaje de la clase RNDIS del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-rndis-message-query"></a>Consulta de mensaje de clase RNDIS de dispositivo 

#### <a name="ux_device_class_rndis_msg_keep_query"></a>ux_device_class_rndis_msg_keep_query

**Icono** ![Icono de consulta de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image36.png)

**Descripción**

Este evento representa un evento de consulta de mensaje de la clase RNDIS del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: OID de RNDIS
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-rndis-message-reset"></a>Restablecimiento de mensaje de clase RNDIS de dispositivo 

#### <a name="ux_device_class_rndis_msg_reset"></a>ux_device_class_rndis_msg_reset

**Icono** ![Icono de restablecimiento de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image37.png)

**Descripción**

Este evento representa un evento de restablecimiento de mensaje de la clase RNDIS del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa

### <a name="device-class-rndis-message-set"></a>Establecimiento de mensaje de clase RNDIS de dispositivo 

#### <a name="ux_device_class_rndis_msg_set"></a>ux_device_class_rndis_msg_set

**Icono** ![Icono de establecimiento de mensaje de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image38.png)

**Descripción**

Este evento representa un evento de establecimiento de mensaje de la clase RNDIS del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: OID de RNDIS
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-rndis-packet-receive"></a>Recepción de paquete de clase RNDIS de dispositivo 

#### <a name="ux_device_class_rndis_packet_receive"></a>ux_device_class_rndis_packet_receive

**Icono** ![Icono de recepción de paquete de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image39.png)

**Descripción**

Este evento representa un evento de recepción de paquete de la clase RNDIS del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-rndis-packet-transmit"></a>Transmisión de paquete de clase RNDIS de dispositivo 

#### <a name="ux_device_class_rndis_packet_transmit"></a>ux_device_class_rndis_packet_transmit

**Icono** ![Icono de transmisión de paquete de clase R N D I S de dispositivo](./media/user-guide/usbx-events/image40.png)

**Descripción**

Este evento representa un evento de transmisión de paquete de la clase RNDIS del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-activate"></a>Activación de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_activate"></a>ux_device_class_storage_activate

**Icono** ![Icono de activación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image41.png)

**Descripción**

Este evento representa un evento de activación de la clase STORAGE del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-deactivate"></a>Desactivación de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_deactivate"></a>ux_device_class_storage_deactivate

**Icono** ![Icono de desactivación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image42.png)

**Descripción**

Este evento representa un evento de desactivación de la clase STORAGE del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-format"></a>Formato de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_format"></a>ux_device_class_storage_format

**Icono** ![Icono de formato de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image43.png)

**Descripción**

Este evento representa un evento de formato de la clase STORAGE del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-inquiry"></a>Consulta de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_inquiry"></a>ux_device_class_storage_inquiry

**Icono** ![Icono de consulta de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image44.png)

**Descripción**

Este evento representa un evento de consulta de la clase STORAGE del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-mode-select"></a>Selección de modo de clase STORAGE de dispositivo

#### <a name="ux_device_class_storage_mode_select"></a>ux_device_class_storage_mode_select

**Icono** ![Icono de selección de modo de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image45.png)

**Descripción**

Este evento representa un evento de selección de modo de la clase STORAGE del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-mode-sense"></a>Detección del modo de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_mode_sense"></a>ux_device_class_storage_mode_sense

**Icono** ![Icono de detección de modo de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image46.png)

**Descripción**

Este evento representa un evento de detección de modo de la clase STORAGE del dispositivo USBX.

Campos de información 

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-prevent-allow-media-removal"></a>Impedir/permitir extracción de soporte físico de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a>ux_device_class_storage_prevent_allow_media_removal

**Icono** ![Icono de impedir/permitir extracción de soporte físico de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image47.png)

**Descripción**

Este evento representa un evento para impedir o permitir la extracción del soporte físico de la clase STORAGE del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-read"></a>Lectura de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_read"></a>ux_device_class_storage_read

**Icono** ![Icono de lectura de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image48.png)

**Descripción**

Este evento representa un evento de lectura de la clase STORAGE del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: sector
- Campo de información 4: sectores numéricos

### <a name="device-class-storage-read-capacity"></a>Lectura de capacidad de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_read_capacity"></a>ux_device_class_storage_read_capacity

**Icono** ![Icono de lectura de capacidad de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image49.png)

**Descripción**

Este evento representa un evento de lectura de capacidad de la clase STORAGE del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-read-format-capacity"></a>Lectura de capacidad de formato de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_read_format_capacity"></a>ux_device_class_storage_read_format_capacity

**Icono** ![Icono de lectura de capacidad de formato de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image50.png)

**Descripción**

Este evento representa un evento de lectura de capacidad de formato de la clase STORAGE del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-read-toc"></a>Lectura de tabla de contenido de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_read_toc"></a>ux_device_class_storage_read_toc

**Icono** ![Icono de lectura de tabla de contenido de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image51.png)

**Descripción**

Este evento representa un evento de lectura de tabla de contenido de la clase STORAGE del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-request-sense"></a>Detección de solicitud de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_request_sense"></a>ux_device_class_storage_request_sense

**Icono** ![Icono de detección de solicitud de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image52.png)

**Descripción**

Este evento representa un evento de detección de solicitud de la clase STORAGE del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: clave de detección
- Campo de información 4: código

### <a name="device-class-storage-start-stop"></a>Inicio/parada de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_start_stop"></a>ux_device_class_storage_start_stop

**Icono** ![Icono de inicio/parada de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image53.png)

**Descripción**

Este evento representa un evento de inicio/parada de la clase STORAGE del dispositivo USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-test-ready"></a>Prueba de unidad preparada de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_test_ready"></a>ux_device_class_storage_test_ready

**Icono** ![Icono de prueba de unidad preparada de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image54.png)

**Descripción**

Este evento representa un evento de prueba de unidad preparada de la clase STORAGE del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-verify"></a>Comprobación de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_verify"></a>ux_device_class_storage_verify

**Icono** ![Icono de comprobación de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image55.png)

**Descripción**

Este evento representa un evento de comprobación de la clase STORAGE del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-class-storage-write"></a>Escritura de clase STORAGE de dispositivo 

#### <a name="ux_device_class_storage_write"></a>ux_device_class_storage_write

**Icono** ![Icono de escritura de clase STORAGE de dispositivo](./media/user-guide/usbx-events/image56.png)

**Descripción**

Este evento representa un evento de escritura de la clase STORAGE del dispositivo USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: LUN
- Campo de información 3: sector
- Campo de información 4: sectores numéricos

### <a name="device-stack-alternate-setting-get"></a>Obtención de configuración alternativa de pila de dispositivos 

#### <a name="ux_device_class_alternate_setting_get"></a>ux_device_class_alternate_setting_get

**Icono** ![Icono de obtención de configuración alternativa de pila de dispositivos](./media/user-guide/usbx-events/image57.png)

**Descripción**

Este evento representa un evento de obtención de configuración alternativa de la pila de dispositivos USBX.

**Campos de información**

- Campo de información 1: valor de la interfaz
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-alternate-setting-set"></a>Establecimiento de configuración alternativa de pila de dispositivos 

#### <a name="ux_device_class_alternate_setting_set"></a>ux_device_class_alternate_setting_set

**Icono** ![Icono de establecimiento de configuración alternativa de pila de dispositivos](./media/user-guide/usbx-events/image58.png)

**Descripción**

Este evento representa un evento de establecimiento de configuración alternativa de la pila de dispositivos USBX.

**Campos de información**
- Campo de información 1: valor de la interfaz
- Campo de información 2: valor de configuración alternativo
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-class-register"></a>Registro de clase de pila de dispositivos 

#### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

**Icono** ![Icono de registro de clase de pila de dispositivos](./media/user-guide/usbx-events/image59.png)

**Descripción**

Este evento representa un evento de registro de la clase de la pila de dispositivos USBX.

**Campos de información**

- Campo de información 1: nombre de clase
- Campo de información 2: número de interfaz
- Campo de información 3: parámetro
- Campo de información 4: no se usa

### <a name="device-stack-clear-feature"></a>Borrado de característica de pila de dispositivos 

#### <a name="ux_device_stack_clear_feature"></a>ux_device_stack_clear_feature

**Icono** ![Icono de borrado de característica de pila de dispositivos](./media/user-guide/usbx-events/image60.png)

**Descripción**

Este evento representa un evento de borrado de característica de la pila de dispositivos USBX.

**Campos de información**

- Campo de información 1: tipo de solicitud
- Campo de información 2: valor de la solicitud Campo de información 3: índice de la solicitud
- Campo de información 4: no se usa

### <a name="device-stack-configuration-get"></a>Obtención de configuración de pila de dispositivos 

#### <a name="ux_device_stack_configuration_get-t"></a>ux_device_stack_configuration_get t

**Icono** ![Icono de obtención de configuración de pila de dispositivos](./media/user-guide/usbx-events/image61.png)

**Descripción**

Este evento representa un evento de obtención de configuración de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: valor de configuración
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-configuration-set"></a>Establecimiento de configuración de pila de dispositivos 

#### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

**Icono** ![Icono de establecimiento de configuración de pila de dispositivos](./media/user-guide/usbx-events/image62.png)

**Descripción**

Este evento representa un evento de establecimiento de configuración de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: valor de configuración
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-connect"></a>Conexión de pila de dispositivos 

#### <a name="ux_device_stack_connect"></a>ux_device_stack_connect

**Icono** ![Icono de conexión de pila de dispositivos](./media/user-guide/usbx-events/image63.png)

**Descripción**

Este evento representa un evento de envío de descriptor de la pila de dispositivos USBX.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-descriptor-send"></a>Envío de descriptor de pila de dispositivos 

#### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

**Icono** ![Icono de envío de descriptor de pila de dispositivos](./media/user-guide/usbx-events/image64.png)

**Descripción**

Este evento representa un evento de envío de descriptor de la pila de dispositivos USBX.

**Campos de información**

- Campo de información 1: tipo de descriptor
- Campo de información 2: índice de solicitud
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-disconnect"></a>Desconexión de pila de dispositivos 

#### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

**Icono** ![Icono de desconexión de pila de dispositivos](./media/user-guide/usbx-events/image65.png)

**Descripción**

Este evento representa un evento de desconexión de la pila de dispositivos USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-endpoint-stall"></a>Detención de punto de conexión de pila de dispositivos 

#### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

**Icono** ![Icono de detención de punto de conexión de pila de dispositivos](./media/user-guide/usbx-events/image66.png)

**Descripción**

Este evento representa un evento de detención del punto de conexión de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: punto de conexión
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-get-status"></a>Obtención de estado de pila de dispositivos 

#### <a name="ux_device_stack_get_status"></a>ux_device_stack_get_status

**Icono** ![Icono de obtención de estado de pila de dispositivos](./media/user-guide/usbx-events/image67.png)

**Descripción**

Este evento representa un evento de obtención de estado de la pila de dispositivo USBX.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-host-wakeup"></a>Reactivación de host de pila de dispositivos 

#### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

**Icono** ![Icono de reactivación de host de pila de dispositivos](./media/user-guide/usbx-events/image68.png)

**Descripción**

Este evento representa un evento de reactivación del host de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-initialize"></a>Inicialización de pila de dispositivos 

#### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

**Icono** ![Icono de inicialización de pila de dispositivos](./media/user-guide/usbx-events/image69.png)

**Descripción**

Este evento representa un evento de inicialización de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-interface-delete"></a>Eliminación de interfaz de pila de dispositivos 

#### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

**Icono** ![Icono de eliminación de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image70.png)

**Descripción**

Este evento representa un evento de eliminación de la interfaz de la pila de dispositivos USBX.

**Campos de información**

- Campo de información 1: interfaz
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-interface-get"></a>Obtención de interfaz de pila de dispositivos 

#### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

**Icono** ![Icono de obtención de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image71.png)

**Descripción**

Este evento representa un evento de obtención de la interfaz de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: valor de la interfaz
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-interface-set"></a>Establecimiento de interfaz de pila de dispositivos 

#### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

**Icono** ![Icono de establecimiento de interfaz de pila de dispositivos](./media/user-guide/usbx-events/image72.png)

**Descripción**

Este evento representa un evento de establecimiento de la interfaz de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: valor de la solicitud Campo de información 2: índice de solicitud
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-set-feature"></a>Establecimiento de característica de pila de dispositivos 

#### <a name="ux_device_stack_set_feature"></a>ux_device_stack_set_feature

**Icono** ![Icono de establecimiento de característica de pila de dispositivos](./media/user-guide/usbx-events/image73.png)

**Descripción**

Este evento representa un evento de establecimiento de característica de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: valor de la solicitud Campo de información 2: índice de solicitud
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-transfer-abort"></a>Anulación de transferencia de pila de dispositivos 

#### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

**Icono** ![Icono de anulación de transferencia de pila de dispositivos](./media/user-guide/usbx-events/image74.png)

**Descripción**

Este evento representa un evento de anulación de transferencia de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: solicitud de transferencia
- Campo de información 2: código de finalización
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-transfer-all-request-abort"></a>Anulación de todas las solicitudes de transferencia de la pila de dispositivos 

#### <a name="ux_device_stack_transfer_all_request_abort"></a>ux_device_stack_transfer_all_request_abort

**Icono** ![Icono de anulación de todas las solicitudes de transferencia de la pila de dispositivos](./media/user-guide/usbx-events/image75.png)

**Descripción**

Este evento representa un evento de anulación de todas las solicitudes de transferencia de la pila de dispositivos USBX.

**Campos de información** 

- Campo de información 1: punto de conexión
- Campo de información 2: código de finalización
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="device-stack-transfer-request"></a>Solicitud de transferencia de pila de dispositivos 

#### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

**Icono** ![Icono de solicitud de transferencia de pila de dispositivos](./media/user-guide/usbx-events/image76.png)

**Descripción**

Este evento representa un evento de solicitud de transferencia de la pila de dispositivos USBX.

**Campos de información**

- Campo de información 1: solicitud de transferencia
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-asix-activate"></a>Activación de clase ASIX de host 

#### <a name="ux_host_class_asix_activate"></a>ux_host_class_asix_activate

**Icono** ![Icono de activación de clase ASIX de host](./media/user-guide/usbx-events/image77.png)

**Descripción**

Este evento representa una activación de la clase ASIX del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-asix-deactivate"></a>Desactivación de clase ASIX de host 

#### <a name="ux_host_class_asix_deactivate"></a>ux_host_class_asix_deactivate

**Icono** ![Icono de desactivación de clase ASIX de host](./media/user-guide/usbx-events/image78.png)

**Descripción**

Este evento representa un evento de desactivación de la clase ASIX del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-asix-interrupt-notification"></a>Notificación de interrupción de clase ASIX de host 

#### <a name="ux_host_class_asix_interrupt_notification"></a>ux_host_class_asix_interrupt_notification

**Icono** ![Icono de notificación de interrupción de clase ASIX de host](./media/user-guide/usbx-events/image79.png)

**Descripción**

Este evento representa un evento de notificación de interrupción de la clase ASIX del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-asix-read"></a>Lectura de clase ASIX de host 

#### <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

**Icono** ![Icono de lectura de clase ASIX de host](./media/user-guide/usbx-events/image80.png)

**Descripción**

Este evento representa un evento de lectura de la clase ASIX del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-asix-write"></a>Escritura de clase ASIX de host 

#### <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

**Icono** ![Icono de escritura de clase ASIX de host](./media/user-guide/usbx-events/image81.png)

**Descripción**

Este evento representa un evento de escritura de la clase ASIX del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-audio-activate"></a>Activación de clase AUDIO de host 

#### <a name="ux_host_class_audio_activate"></a>ux_host_class_audio_activate

**Icono** ![Icono de activación de clase AUDIO de host](./media/user-guide/usbx-events/image82.png)

**Descripción**

Este evento representa un evento de activación de la clase AUDIO del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-audio-control-value-get"></a>Obtención de valor de control de clase AUDIO de host 

#### <a name="ux_host_class_audio_control_value_get"></a>ux_host_class_audio_control_value_get

**Icono** ![Icono de obtención de valor de control de clase AUDIO de host](./media/user-guide/usbx-events/image83.png)

**Descripción**

Este evento representa un evento de obtención del valor de control de la clase AUDIO del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-audio-control-value-set"></a>Establecimiento de valor de control de clase AUDIO de host 

#### <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

**Icono** ![Icono de establecimiento de valor de control de clase AUDIO de host](./media/user-guide/usbx-events/image84.png)

**Descripción**

Este evento representa un evento interno de procesamiento diferido del controlador de E/S de NetX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: control de audio
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-audio-deactivate"></a>Desactivación de clase AUDIO de host 

#### <a name="ux_host_class_audio_deactivate"></a>ux_host_class_audio_deactivate

**Icono** ![Icono de desactivación de clase AUDIO de host](./media/user-guide/usbx-events/image85.png)

**Descripción**

Este evento representa un evento de desactivación de la clase AUDIO del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-audio-read"></a>Lectura de clase AUDIO de host 

#### <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

**Icono** ![Icono de lectura de clase AUDIO de host](./media/user-guide/usbx-events/image86.png)

**Descripción**

Este evento representa un evento de lectura de la clase AUDIO del host USBX.

- Campos de información 
- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-audio-streaming-sampling-get"></a>Obtención de muestreo de streaming de clase AUDIO de host 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

**Icono** ![Icono de obtención de muestreo de streaming de clase AUDIO de host](./media/user-guide/usbx-events/image87.png)

**Descripción**

Este evento representa un evento de obtención de muestreo de streaming de la clase AUDIO del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-audio-streaming-sampling-set"></a>Establecimiento de muestreo de streaming de clase AUDIO de host 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

**Icono** ![Icono de establecimiento de muestreo de streaming de clase AUDIO de host](./media/user-guide/usbx-events/image88.png)

**Descripción**

Este evento representa un evento de establecimiento de muestreo de streaming de la clase AUDIO del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: muestreo de audio
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-audio-write"></a>Escritura de clase AUDIO de host 

#### <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

**Icono** ![Icono de escritura de clase AUDIO de host](./media/user-guide/usbx-events/image89.png)

**Descripción**

Este evento representa un evento de escritura de la clase AUDIO del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-activate"></a>Activación de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_activate"></a>ux_host_class_cdc_acm_activate

**Icono** ![Icono de activación de clase C D C A C M de host](./media/user-guide/usbx-events/image90.png)

**Descripción**

Este evento representa un evento de activación de la clase CDC ACM del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-deactivate"></a>Desactivación de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_deactivate"></a>ux_host_class_cdc_acm_deactivate

**Icono** ![Icono de desactivación de clase C D C A C M de host](./media/user-guide/usbx-events/image91.png)

**Descripción**

Este evento representa un evento de desactivación de la clase CDC ACM del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a>Función IOCTL de anulación de canalización de entrada de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a>ux_host_class_cdc_acm_ioctl_abort_in_pipe

**Icono** ![Icono de función I O C T L de anulación de canalización de entrada de clase C D C A C M de host](./media/user-guide/usbx-events/image92.png)

**Descripción**

Este evento representa un evento de una función IOCTL de anulación de canalización de entrada de la clase CDC ACM del host USBX.

Campos de información 

- Campo de información 1: instancia de clase
- Campo de información 2: punto de conexión
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a>Función IOCTL de anulación de canalización de salida de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a>ux_host_class_cdc_acm_ioct_abort_out_pipe

**Icono** [Icono de función I O C T L de anulación de canalización de salida de clase C D C A C M de host](./media/user-guide/usbx-events/image93.png)

**Descripción**

Este evento representa un evento de una función IOCTL de anulación de canalización de salida de la clase CDC ACM del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: punto de conexión
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a>Función IOCTL de obtención de estado de dispositivo de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a>ux_host_class_cdc_acm_ioctl_get_device_status

**Icono** ![Icono de función I O C T L de obtención de estado de dispositivo de clase C D C A C M de host](./media/user-guide/usbx-events/image94.png)

**Descripción**

Este evento representa un evento de una función IOCTL de obtención de estado de dispositivo de la clase CDC ACM del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: estado del dispositivo
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a>Función IOCTL de obtención de codificación de línea de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a>ux_host_class_cdc_acm_ioctl_get_line_coding

**Icono** ![Icono de función I O C T L de obtención de codificación de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image95.png)

**Descripción**

Este evento representa un evento de una función IOCTL de obtención de codificación de línea de la clase CDC ACM del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a>Función IOCTL de devolución de llamada de notificación de clase CDC ACM de host

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a>ux_host_class_cdc_acm_ioctl_notification_callback

**Icono** ![Icono de función I O C T L de devolución de llamada de notificación de clase C D C A C M de host](./media/user-guide/usbx-events/image96.png)

**Descripción**

Este evento representa un evento de una función IOCTL de devolución de llamada de notificación de la clase CDC ACM del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-ioctl-send-break"></a>Función IOCTL de interrupción de envío de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a>ux_host_class_cdc_acm_ioctl_send_break

**Icono** ![Icono de función I O C T L de interrupción de envío de clase C D C A C M de host](./media/user-guide/usbx-events/image97.png)

**Descripción**

Este evento representa un evento de una función IOCTL de interrupción de envío de la clase CDC ACM del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a>Función IOCTL de establecimiento de codificación de línea de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a>ux_host_class_cdc_acm_ioctl_set_line_coding

**Icono** ![Icono de función I O C T L de establecimiento de codificación de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image97.png)

**Descripción**

Este evento representa un evento de una función IOCTL de establecimiento de codificación de línea de la clase CDC ACM del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a>Función IOCTL de establecimiento de estado de línea de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a>ux_host_class_cdc_acm_ioctl_set_line_state

**Icono** ![Icono de función I O C T L de establecimiento de estado de línea de clase C D C A C M de host](./media/user-guide/usbx-events/image99.png)

**Descripción**

Este evento representa un evento de establecimiento de estado de línea de la clase CDC ACM del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-read"></a>Lectura de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

**Icono** ![Icono de lectura de clase C D C A C M de host](./media/user-guide/usbx-events/image100.png)

**Descripción**

Este evento representa un evento de lectura de la clase CDC ACM del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-reception-start"></a>Inicio de recepción de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

**Icono** ![Icono de inicio de recepción de clase C D C A C M de host](./media/user-guide/usbx-events/image101.png)

**Descripción**

Este evento representa un evento de inicio de recepción de la clase CDC ACM del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-reception-stop"></a>Parada de recepción de clase CDC ACM de host 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

**Icono** ![Icono de parada de recepción de clase C D C A C M de host](./media/user-guide/usbx-events/image102.png)

**Descripción**

Este evento representa un evento de parada de recepción de la clase CDC ACM del host USBX.

**Campos de información**

- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-cdc-acm-write"></a>Escritura de clase CDC ACM de host 

#### <a name="ux_host_class_acm_write"></a>ux_host_class_acm_write

**Icono** ![Icono de escritura de clase C D C A C M de host](./media/user-guide/usbx-events/image103.png)

**Descripción**

Este evento representa un evento de escritura de la clase CDC ACM del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-dpump-activate"></a>Activación de clase DPUMP de host 

#### <a name="ux_host_class_dpump_activate"></a>ux_host_class_dpump_activate

**Icono** ![Icono de activación de clase DPUMP de host](./media/user-guide/usbx-events/image104.png)

**Descripción**

Este evento representa un evento de activación de la clase DPUMP del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-dpump-deactivate"></a>Desactivación de clase DPUMP de host 

#### <a name="ux_host_class_dpump_deactivate"></a>ux_host_class_dpump_deactivate

**Icono** ![Icono de desactivación de clase DPUMP de host](./media/user-guide/usbx-events/image105.png)

**Descripción**

Este evento representa un evento de desactivación de la clase DPUMP del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-dpump-read"></a>Lectura de clase DPUMP de host 

#### <a name="ux_host_class_dpump_read"></a>ux_host_class_dpump_read

**Icono** ![Icono de lectura de clase DPUMP de host](./media/user-guide/usbx-events/image106.png)

**Descripción**

Este evento representa un evento de lectura de la clase DPUMP del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-dpump-write"></a>Escritura de clase DPUMP de host 

#### <a name="ux_host_class_dpump_write"></a>ux_host_class_dpump_write

**Icono** ![Icono de escritura de clase DPUMP de host](./media/user-guide/usbx-events/image107.png)

**Descripción**

Este evento representa un evento de escritura de la clase DPUMP del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-hid-activate"></a>Activación de clase HID de host 

#### <a name="ux_host_class_hid_activate"></a>ux_host_class_hid_activate

**Icono** ![Icono de activación de clase HID de host](./media/user-guide/usbx-events/image108.png)

**Descripción**

Este evento representa un evento de activación de la clase HID del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-client-register"></a>Registro de cliente de clase HID de host 

#### <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

**Icono** ![Icono de registro de cliente de clase HID de host](./media/user-guide/usbx-events/image109.png)

**Descripción**

Este evento representa un evento de registro de cliente de la clase HID del host USBX.

**Campos de información** 

- Campo de información 1: nombre de cliente de HID
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-deactivate"></a>Desactivación de clase HID de host 

#### <a name="ux_host_class_hid_deactivate"></a>ux_host_class_hid_deactivate

**Icono** ![Icono de desactivación de clase HID de host](./media/user-guide/usbx-events/image110.png)

**Descripción**

Este evento representa un evento de desactivación de la clase HID del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-idle-get"></a>Obtención de inactividad de clase HID de host 

#### <a name="ux_host_class_hid_idle_get"></a>ux_host_class_hid_idle_get

**Icono** ![Icono de obtención de inactividad de clase HID de host](./media/user-guide/usbx-events/image111.png)

**Descripción**

Este evento representa un evento de obtención de inactividad de la clase HID del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-idle-set"></a>Establecimiento de inactividad de clase HID de host 

#### <a name="ux_host_class_hid_idle_set"></a>ux_host_class_hid_idle_set

**Icono** ![Icono de establecimiento de inactividad de clase HID de host](./media/user-guide/usbx-events/image112.png)

**Descripción**

Este evento representa un evento de establecimiento de inactividad de la clase HID del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-keyboard-activate"></a>Activación de teclado de clase HID de host 

#### <a name="ux_host_class_hid_keyboard_activate"></a>ux_host_class_hid_keyboard_activate

**Icono** ![Icono de activación de teclado de clase HID de host](./media/user-guide/usbx-events/image113.png)

**Descripción**

Este evento representa un evento de activación de teclado de la clase HID del host USBX.

**Campos de información**
<p>Campo de información 1: instancia de clase
<p>Campo de información 2: instancia de cliente de HID
<p>Campo de información 3: no se usa
<p>Campo de información 4: no se usa

### <a name="host-class-hid-keyboard-deactivate"></a>Desactivación de teclado de clase HID de host 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a>ux_host_class_hid_keyboard_deactivate

**Icono** ![Icono de desactivación de teclado de clase HID de host](./media/user-guide/usbx-events/image114.png)

**Descripción**

Este evento representa un evento de desactivación de teclado de la clase HID del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: instancia de cliente de HID
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-mouse-activate"></a>Activación de mouse de clase HID de host 

#### <a name="ux_host_class_hid_mouse_activate"></a>ux_host_class_hid_mouse_activate

**Icono** ![Icono de activación de mouse de clase HID de host](./media/user-guide/usbx-events/image115.png)

**Descripción**

Este evento representa un evento de activación de mouse de la clase HID del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: instancia de cliente de HID
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-mouse-deactivate"></a>Desactivación de mouse de clase HID de host 

#### <a name="ux_host_class_hid_mouse_deactivate"></a>ux_host_class_hid_mouse_deactivate

**Icono** ![Icono de desactivación de mouse de clase HID de host](./media/user-guide/usbx-events/image116.png)

**Descripción**

- Este evento representa un evento de desactivación de mouse de la clase HID del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: instancia de cliente de HID
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-remote-control-activate"></a>Activación de control remoto de clase HID de host 

#### <a name="ux_host_class_hid_remote_control_activate"></a>ux_host_class_hid_remote_control_activate

**Icono** ![Icono de activación de control remoto de clase HID de host](./media/user-guide/usbx-events/image117.png)

**Descripción**

Este evento representa un evento de activación de control remoto de la clase HID del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: instancia de cliente de HID
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-remote-control-deactivate"></a>Desactivación de control remoto de clase HID de host 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a>ux_host_class_hid_remote_control_deactivate

**Icono** ![Icono de desactivación de control remoto de clase HID de host](./media/user-guide/usbx-events/image118.png)

**Descripción**

Este evento representa un evento de desactivación de control remoto de la clase HID del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: instancia de cliente de HID
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-report-get"></a>Obtención de informe de clase HID de host 

#### <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

**Icono** ![Icono de obtención de informe de clase HID de host](./media/user-guide/usbx-events/image119.png)

**Descripción**

Este evento representa una obtención de informe de la clase HID del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: informe de cliente
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hid-report-set"></a>Establecimiento de informe de clase HID de host 

#### <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

**Icono** ![Icono de establecimiento de informe de clase HID de host](./media/user-guide/usbx-events/image120.png)

**Descripción** Este evento representa un establecimiento de informe de la clase HID del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: informe de cliente
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hub-activate"></a>Activación de clase HUB de host 

#### <a name="ux_host_class_hub_activate"></a>ux_host_class_hub_activate

**Icono** ![Icono de activación de clase HUB de host](./media/user-guide/usbx-events/image121.png)

**Descripción**

Este evento representa un evento de activación de la clase HUB del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hub-change-detect"></a>Detección de cambio de clase HUB de host 

#### <a name="ux_host_class_hub_change_detect"></a>ux_host_class_hub_change_detect

**Icono** ![Icono de detección de cambio de clase HUB de host](./media/user-guide/usbx-events/image122.png)

**Descripción**

Este evento representa un evento de detección de cambio de la clase HUB del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hub-deactivate"></a>Desactivación de clase HUB de host 

#### <a name="ux_host_class_hub_deactivate"></a>ux_host_class_hub_deactivate

**Icono** ![Icono de desactivación de clase HUB de host](./media/user-guide/usbx-events/image123.png)

**Descripción**

Este evento representa un evento de desactivación de la clase HUB del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-hub-port-change-connection-process"></a>Proceso de cambio de puerto de conexión de clase HUB de host 

#### <a name="ux_host_class_hub_change_connection_process"></a>ux_host_class_hub_change_connection_process

**Icono** ![Icono de proceso de cambio de puerto de conexión de clase HUB de host](./media/user-guide/usbx-events/image124.png)

**Descripción**

Este evento representa un evento de proceso de cambio del puerto de conexión de la clase HUB del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puerto
- Campo de información 3: estado de puerto
- Campo de información 4: no se usa

### <a name="host-class-hub-port-change-enable-process"></a>Habilitación de proceso de cambio de puerto de clase HUB de host 

#### <a name="ux_host_class_hub_port_change_enable_process"></a>ux_host_class_hub_port_change_enable_process

**Icono** ![Icono de habilitación de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image125.png)

**Descripción**

Este evento representa un evento de habilitación del proceso de cambio de puerto de la clase HUB del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puerto
- Campo de información 3: estado de puerto
- Campo de información 4: no se usa

### <a name="host-class-hub-port-change-over-current-process"></a>Proceso actual finalizado de cambio de puerto de clase HUB de host 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a>ux_host_class_hub_port_change_over_current_process

**Icono** ![Icono de proceso actual finalizado de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image126.png)

**Descripción**

Este evento representa la asignación de un paquete por medio de nx_packet_allocate.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puerto
- Campo de información 3: estado de puerto
- Campo de información 4: no se usa

### <a name="host-class-hub-port-change-reset-process"></a>Restablecimiento de proceso de cambio de puerto de clase HUB de host 

#### <a name="ux_host_class_hub_port_change_reset_process"></a>ux_host_class_hub_port_change_reset_process

**Icono** ![Icono de restablecimiento de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image127.png)

**Descripción**

Este evento representa un evento de restablecimiento del proceso de cambio de puerto de la clase HUB del host USBX.

**Campos de información**

- Campo de información 1: centro de conectividad Campo de información 2: puerto
- Campo de información 3: estado de puerto
- Campo de información 4: no se usa

### <a name="host-class-hub-port-change-suspend-process"></a>Suspensión de proceso de cambio de puerto de clase HUB de host 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a>ux_host_class_hub_port_change_suspend_process

**Icono** ![Icono de suspensión de proceso de cambio de puerto de clase HUB de host](./media/user-guide/usbx-events/image128.png)

**Descripción**

Este evento representa un evento de suspensión del proceso de cambio de puerto de la clase HUB del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puerto
- Campo de información 3: estado de puerto
- Campo de información 4: no se usa

### <a name="host-class-pima-activate"></a>Activación de clase PIMA de host 

#### <a name="ux_host_class_pima_activate"></a>ux_host_class_pima_activate

**Icono** ![Icono de activación de clase PIMA de host](./media/user-guide/usbx-events/image129.png)

**Descripción**

Este evento representa un evento de activación de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-deactivate"></a>Desactivación de clase PIMA de host 

#### <a name="ux_host_class_pima_deactivate"></a>ux_host_class_pima_deactivate

**Icono** ![Icono de desactivación de clase PIMA de host](./media/user-guide/usbx-events/image130.png)

**Descripción**

Este evento representa un evento de desactivación de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-device-info-get"></a>Obtención de información de dispositivo de clase PIMA de host 

#### <a name="ux_host_class_pima_device_info_get"></a>ux_host_class_pima_device_info_get

**Icono** ![Icono de obtención de información de dispositivo de clase PIMA de host](./media/user-guide/usbx-events/image131.png)

**Descripción**

Este evento representa un evento de obtención de información del dispositivo de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: dispositivo PIMA
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-device-reset"></a>Restablecimiento de dispositivo de clase PIMA de host 

#### <a name="ux_host_class_pima_device_reset"></a>ux_host_class_pima_device_reset

**Icono** ![Icono de restablecimiento de dispositivo de clase PIMA de host](./media/user-guide/usbx-events/image132.png)

**Descripción**

Este evento representa un evento de restablecimiento de dispositivo de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-notification"></a>Notificación de clase PIMA de host 

#### <a name="ux_host_class_pima_notification"></a>ux_host_class_pima_notification

**Icono** ![Icono de notificación de clase PIMA de host](./media/user-guide/usbx-events/image133.png)

**Descripción**

Este evento representa un evento de notificación de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase Campo de información 2: código de evento
- Campo de información 3: identificador de la transacción
- Campo de información 4: parámetro 1

### <a name="host-class-pima-number-objects-get"></a>Obtención de número de objetos de clase PIMA de host 

#### <a name="ux_host_class_pima_number_objects_get"></a>ux_host_class_pima_number_objects_get

**Icono** ![Icono de obtención de número de objetos de clase PIMA de host](./media/user-guide/usbx-events/image134.png)

**Descripción**

Este evento representa un evento de obtención de número de objetos de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-object-close"></a>Cierre de objeto de clase PIMA de host 

#### <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

**Icono** ![Icono de cierre de objeto de clase PIMA de host](./media/user-guide/usbx-events/image135.png)

**Descripción**

Este evento representa un evento de cierre de objeto de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-object-copy"></a>Copia de objeto de clase PIMA de host 

#### <a name="ux_host_class_pima_object_copy"></a>ux_host_class_pima_object_copy

**Icono** ![Icono de copia de objeto de clase PIMA de host](./media/user-guide/usbx-events/image136.png)

**Descripción**

Este evento representa un evento de copia de objeto de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-object-delete"></a>Eliminación de objeto de clase PIMA de host 

#### <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

**Icono** ![Icono de eliminación de objeto de clase PIMA de host](./media/user-guide/usbx-events/image137.png)

**Descripción**

Este evento representa un evento de eliminación de objeto de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-object-get"></a>Obtención de objeto de clase PIMA de host 

#### <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

**Icono** ![Icono de obtención de objeto de clase PIMA de host](./media/user-guide/usbx-events/image138.png)

**Descripción**

Este evento representa la obtención de información de RARP por medio de nx_rarp_info_get.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: objeto
- Campo de información 4: no se usa

### <a name="host-class-pima-object-info-get"></a>Obtención de información de objeto de clase PIMA de host 

#### <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

**Icono** ![Icono de obtención de información de objeto de clase PIMA de host](./media/user-guide/usbx-events/image139.png)

**Descripción**

Este evento representa un evento de obtención de información de objeto de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: objeto
- Campo de información 4: no se usa

### <a name="host-class-pima-object-info-send"></a>Envío de información de objeto de clase PIMA de host 

#### <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

**Icono** ![Icono de envío de información de objeto de clase PIMA de host](./media/user-guide/usbx-events/image140.png)

**Descripción**

Este evento representa un evento de envío de información de objeto de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-object-move"></a>Movimiento de objeto de clase PIMA de host 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Icono** ![Icono de movimiento de objeto de clase PIMA de host](./media/user-guide/usbx-events/image141.png)

**Descripción**

Este evento representa un evento de movimiento de objeto de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: objeto
- Campo de información 4: no se usa

### <a name="host-class-pima-object-send"></a>Envío de objeto de clase PIMA de host 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Icono** ![Icono de envío de objeto de clase PIMA de host](./media/user-guide/usbx-events/image142.png)

**Descripción**

Este evento representa un evento de envío de objeto de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: objeto
- Campo de información 3: búfer de objetos
- Campo de información 4: longitud del objeto

### <a name="host-class-pima-object-transfer-abort"></a>Anulación de transferencia de objeto de clase PIMA de host 

#### <a name="ux_host_class_pima_object_transfer_abort"></a>ux_host_class_pima_object_transfer_abort

**Icono** ![Icono de anulación de transferencia de objeto de clase PIMA de host](./media/user-guide/usbx-events/image143.png)

**Descripción**

Este evento representa un evento de anulación de transferencia de objeto de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: objeto
- Campo de información 4: no se usa

### <a name="host-class-pima-read"></a>Lectura de clase PIMA de host 

#### <a name="ux_host_class_pima_read"></a>ux_host_class_pima_read

**Icono** ![Icono de lectura de clase PIMA de host](./media/user-guide/usbx-events/image144.png)

**Descripción**

Este evento representa un evento de lectura de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud de los datos
- Campo de información 4: no se usa

### <a name="host-class-pima-request-cancel"></a>Cancelación de solicitud de clase PIMA de host 

#### <a name="ux_host_class_pima_request_cancel"></a>ux_host_class_pima_request_cancel

**Icono** ![Icono de cancelación de solicitud de clase PIMA de host](./media/user-guide/usbx-events/image145.png)

**Descripción**

Este evento representa un evento de cancelación de solicitud de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-session-close"></a>Cierre de sesión de clase PIMA de host 

#### <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

**Icono** ![Icono de cierre de sesión de clase PIMA de host](./media/user-guide/usbx-events/image146.png)

**Descripción**

Este evento representa un evento de cierre de sesión de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: sesión de PIMA
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-session-open"></a>Apertura de sesión de clase PIMA de host 

#### <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

**Icono** ![Icono de apertura de sesión de clase PIMA de host](./media/user-guide/usbx-events/image147.png)

**Descripción** Este evento representa un evento de apertura de sesión de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: sesión de PIMA
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-storage-ids-get"></a>Obtención de identificadores de almacenamiento de clase PIMA de host 

#### <a name="ux_host_class_pima_session_ids_get"></a>ux_host_class_pima_session_ids_get

**Icono** ![Icono de obtención de identificadores de almacenamiento de clase PIMA de host](./media/user-guide/usbx-events/image148.png)

**Descripción**

Este evento representa un evento de obtención de identificadores de almacenamiento de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: matriz de identificadores de almacenamiento
- Campo de información 3: longitud de identificador de almacenamiento
Campo de información 4: no se usa

### <a name="host-class-pima-storage-info-get"></a>Obtención de información de almacenamiento de clase PIMA de host 

#### <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

**Icono** ![Icono de obtención de información de almacenamiento de clase PIMA de host](./media/user-guide/usbx-events/image149.png)

**Descripción**

Este evento representa un evento de obtención de información de almacenamiento de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: identificador de almacenamiento
- Campo de información 3: almacenamiento
- Campo de información 4: no se usa

### <a name="host-class-pima-thumb-get"></a>Obtención de miniatura de clase PIMA de host 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Icono** ![Icono de obtención de miniatura de clase PIMA de host](./media/user-guide/usbx-events/image150.png)

**Descripción**

Este evento representa la desaceptación de una conexión de servidor TCP por medio de nx_tcp_server_socket_unaccept.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: identificador del objeto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-pima-write"></a>Escritura de clase PIMA de host 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Icono** ![Icono de escritura de clase PIMA de host](./media/user-guide/usbx-events/image151.png)

**Descripción**

Este evento representa un evento de escritura de la clase PIMA del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud de los datos
- Campo de información 4: no se usa

### <a name="host-class-printer-activate"></a>Activación de clase PRINTER de host 

#### <a name="ux_host_class_printer_activate"></a>ux_host_class_printer_activate

**Icono** ![Icono de activación de clase PRINTER de host](./media/user-guide/usbx-events/image152.png)

**Descripción**

Este evento representa un evento de activación de la clase PRINTER del host USBX.

**Campos de información**

- Campo de información 1: puntero a la instancia de IP
- Campo de información 2: puntero al socket
- Campo de información 3: tipo de servicio
- Campo de información 4: tamaño de la ventana de recepción

### <a name="host-class-printer-deactivate"></a>Desactivación de clase PRINTER de host 

#### <a name="ux_host_class_printer_deactivate"></a>ux_host_class_printer_deactivate

**Icono** ![Icono de desactivación de clase PRINTER de host](./media/user-guide/usbx-events/image153.png)

**Descripción**

Este evento representa un evento de desactivación de la clase PRINTER del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-printer-name-get"></a>Obtención de nombre de clase PRINTER de host 

#### <a name="ux_host_class_printer_name_get"></a>ux_host_class_printer_name_get

**Icono** ![Icono de obtención de nombre de clase PRINTER de host](./media/user-guide/usbx-events/image154.png)

**Descripción**

Este evento representa un evento de obtención de nombre de la clase PRINTER del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-printer-read"></a>Lectura de clase PRINTER de host 

#### <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

**Icono** ![Icono de lectura de clase PRINTER de host](./media/user-guide/usbx-events/image155.png)

**Descripción**

Este evento representa un evento de lectura de la clase PRINTER del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-printer-soft-reset"></a>Restablecimiento parcial de clase PRINTER de host 

#### <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

**Icono** ![Icono de restablecimiento parcial de clase PRINTER de host](./media/user-guide/usbx-events/image156.png)

**Descripción**

Este evento representa un evento de restablecimiento parcial de la clase PRINTER del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-printer-status-get"></a>Obtención de estado de clase PRINTER de host 

#### <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

**Icono** ![Icono de obtención de estado de clase PRINTER de host](./media/user-guide/usbx-events/image157.png)

**Descripción**

Este evento representa un evento de obtención de estado de la clase PRINTER del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: estado de la impresora
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-printer-write"></a>Escritura de clase PRINTER de host 

#### <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

**Icono** ![Icono de escritura de clase PRINTER de host](./media/user-guide/usbx-events/image158.png)

**Descripción**

Este evento representa un evento de escritura de la clase PRINTER del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-prolific-activate"></a>Activación de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_activate"></a>ux_host_class_prolific_activate 

**Icono** ![Icono de activación de clase PROLIFIC de host](./media/user-guide/usbx-events/image159.png)

**Descripción**

Este evento representa un evento de activación de la clase PROLIFIC del host USBX.

**Campos de información** 

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-deactivate"></a>Desactivación de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_deactivate"></a>ux_host_class_prolific_deactivate 

**Icono** ![Icono de desactivación de clase PROLIFIC de host](./media/user-guide/usbx-events/image160.png)

**Descripción**

Este evento representa un evento de desactivación de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a>Función IOCTL de anulación de canalización de entrada de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a>ux_host_class_prolific_ioctl_abort_in_pipe

**Icono** ![Icono de función I O C T L de anulación de canalización de entrada de clase PROLIFIC de host](./media/user-guide/usbx-events/image161.png)

**Descripción**

Este evento representa un evento de una función IOCTL de anulación de canalización de entrada de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: punto de conexión
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a>Función IOCTL de anulación de canalización de salida de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a>ux_host_class_prolific_ioctl_abort_out_pipe

**Icono** ![Icono de función I O C T L de anulación de canalización de salida de clase PROLIFIC de host](./media/user-guide/usbx-events/image162.png)

**Descripción**

Este evento representa un evento de una función IOCTL de anulación de canalización de salida de la clase PROLIFIC de host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: punto de conexión
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-ioctl-get-device-status"></a>Función IOCTL de obtención de estado de dispositivo de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a>ux_host_class_prolific_ioctl_get_device_status

**Icono** ![Icono de función I O C T L de obtención de estado de dispositivo de clase PROLIFIC de host](./media/user-guide/usbx-events/image163.png)

**Descripción**

Este evento representa un evento de una función IOCTL de obtención de estado de dispositivo de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: estado del dispositivo
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-ioctl-get-line-coding"></a>Función IOCTL de obtención de codificación de línea de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a>ux_host_class_prolific_ioctl_get_line_coding

**Icono** ![Icono de función I O C T L de obtención de codificación de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image164.png)

**Descripción**

Este evento representa un evento de una función IOCTL de obtención de codificación de línea de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-ioctl-purge"></a>Función IOCTL de depuración de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_ioctl_purge"></a>ux_host_class_prolific_ioctl_purge

**Icono** ![Icono de función I O C T L de depuración de clase PROLIFIC de host](./media/user-guide/usbx-events/image165.png)

**Descripción**

Este evento representa un evento de una función IOCTL de depuración de la clase PROLIFIC de host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-ioctl-report-device"></a>Función IOCTL de informe de dispositivo de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a>ux_host_class_prolific_ioctl_report_device

**Icono** ![Icono de función I O C T L de informe de cambio de estado de dispositivo de clase PROLIFIC de host](./media/user-guide/usbx-events/image166.png)

**Descripción**

Este evento representa un evento de una función IOCTL de informe del cambio de estado del dispositivo de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-ioctl-send-break"></a>Función IOCTL de interrupción de envío de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a>ux_host_class_prolific_ioctl_send_break

**Icono** ![Icono de función I O C T L de interrupción de envío de clase PROLIFIC de host](./media/user-guide/usbx-events/image167.png)

**Descripción**

Este evento representa un evento de una función IOCTL de interrupción de envío de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-ioctl-set-line-coding"></a>Función IOCTL de establecimiento de codificación de línea de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a>ux_host_class_prolific_ioctl_set_line_coding

**Icono** ![Icono de función I O C T L de establecimiento de codificación de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image168.png)

**Descripción**

Este evento representa un evento de una función IOCTL de establecimiento de codificación de línea de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-ioctl-set-line-state"></a>Función IOCTL de establecimiento de estado de línea de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a>ux_host_class_prolific_ioctl_set_line_state

**Icono** ![Icono de función I O C T L de establecimiento de estado de línea de clase PROLIFIC de host](./media/user-guide/usbx-events/image169.png)

**Descripción**

Este evento representa un evento de una función IOCTL de establecimiento de estado de línea de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: parámetro
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-read"></a>Lectura de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_read"></a>ux_host_class_prolific_read

**Icono** ![Icono de lectura de clase PROLIFIC de host](./media/user-guide/usbx-events/image170.png)

**Descripción**

Este evento representa un evento de lectura de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-prolific-reception-start"></a>Inicio de recepción de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_reception_start"></a>ux_host_class_prolific_reception_start

**Icono** ![Icono de inicio de recepción de clase PROLIFIC de host](./media/user-guide/usbx-events/image171.png)

**Descripción**

Este evento representa un evento de inicio de recepción de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-reception-stop"></a>Parada de recepción de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_reception_stop"></a>ux_host_class_prolific_reception_stop

**Icono** ![Icono de parada de recepción de clase PROLIFIC de host](./media/user-guide/usbx-events/image172.png)

**Descripción**

Este evento representa un evento de parada de recepción de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-prolific-write"></a>Escritura de clase PROLIFIC de host 

#### <a name="ux_host_class_prolific_write"></a>ux_host_class_prolific_write

**Icono** ![Icono de escritura de clase PROLIFIC de host](./media/user-guide/usbx-events/image173.png)

**Descripción**

Este evento representa un evento de escritura de la clase PROLIFIC del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: puntero de datos
- Campo de información 3: longitud solicitada
- Campo de información 4: no se usa

### <a name="host-class-storage-activate"></a>Activación de clase STORAGE de host 

#### <a name="ux_host_class_storage_activate"></a>ux_host_class_storage_activate

**Icono** ![Icono de activación de clase STORAGE de host](./media/user-guide/usbx-events/image174.png)

**Descripción**

Este evento representa un evento de activación de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-storage-deactivate"></a>Desactivación de clase STORAGE de host 

#### <a name="ux_host_class_storage_deactivate"></a>ux_host_class_storage_deactivate

**Icono** ![Icono de desactivación de clase STORAGE de host](./media/user-guide/usbx-events/image175.png)

**Descripción**

Este evento representa un evento de desactivación de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-storage-media-capacity-get"></a>Obtención de capacidad de soporte físico de clase STORAGE de host 

#### <a name="ux_host_class_storage_media_capacity_get"></a>ux_host_class_storage_media_capacity_get

**Icono** ![Icono de obtención de capacidad de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image176.png)

**Descripción**

Este evento representa un evento de obtención de capacidad de soporte físico de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-storage-media-format-capacity-get"></a>Obtención de capacidad de formato de soporte físico de clase STORAGE de host

#### <a name="ux_host_class_storage_media_format_capacity_get"></a>ux_host_class_storage_media_format_capacity_get

**Icono** ![Icono de obtención de capacidad de formato de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image177.png)

**Descripción**

Este evento representa un evento de obtención de capacidad de formato de soporte físico de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

#### <a name="host-class-storage-media-mount"></a>Montaje de soporte físico de clase STORAGE de host 

#### <a name="ux_host_class_storage_media_mount"></a>ux_host_class_storage_media_mount

**Icono** ![Icono de montaje de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image178.png)

**Descripción**

Este evento representa un evento de montaje de soporte físico de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: sector
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-storage-media-open"></a>Apertura de soporte físico de clase STORAGE de host 

#### <a name="ux_host_class_storage_media_open"></a>ux_host_class_storage_media_open

**Icono** ![Icono de apertura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image179.png)

**Descripción**

Este evento representa un evento de apertura de soporte físico de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: soporte físico
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-storage-media-read"></a>Lectura de soporte físico de clase STORAGE de host 

#### <a name="ux_host_class_storage_media_read"></a>ux_host_class_storage_media_read

**Icono** ![Icono de lectura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image180.png)

**Descripción**

Este evento representa un evento de lectura de soporte físico de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: Inicio del sector
- Campo de información 3: recuento de sectores
- Campo de información 4: puntero de datos

### <a name="host-class-storage-media-write"></a>Escritura de soporte físico de clase STORAGE de host 

#### <a name="ux_host_class_storage_media_write"></a>ux_host_class_storage_media_write

**Icono** ![Icono de escritura de soporte físico de clase STORAGE de host](./media/user-guide/usbx-events/image181.png)

**Descripción**

Este evento representa un evento de escritura de soporte físico de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: Inicio del sector
- Campo de información 3: recuento de sectores
- Campo de información 4: puntero de datos

### <a name="host-class-storage-request-sense"></a>Detección de solicitud de clase STORAGE de host 

#### <a name="ux_host_class_storage_request_sense"></a>ux_host_class_storage_request_sense

**Icono** ![Icono de detección de solicitud de clase STORAGE de host](./media/user-guide/usbx-events/image182.png)

**Descripción**

Este evento representa un evento de detección de solicitud de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-storage-start-stop"></a>Inicio/parada de clase STORAGE de host 

#### <a name="ux_host_class_storage_start_stop"></a>ux_host_class_storage_start_stop

**Icono** ![Icono de inicio/parada inicio de clase STORAGE de host](./media/user-guide/usbx-events/image183.png)

**Descripción**

Este evento representa un evento de inicio/parada de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: señal de inicio/parada
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-class-storage-unit-ready-test"></a>Prueba de unidad preparada de clase STORAGE de host 

#### <a name="ux_host_class_storage_unit_ready_test"></a>ux_host_class_storage_unit_ready_test

**Icono** ![Icono de prueba de unidad preparada de clase STORAGE de host](./media/user-guide/usbx-events/image184.png)

**Descripción**

Este evento representa un evento de prueba de unidad preparada de la clase STORAGE del host USBX.

**Campos de información**

- Campo de información 1: instancia de clase
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-class-instance-create"></a>Creación de instancia de clase de pila de hosts 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Icono** ![Icono de creación de instancia de clase de pila de hosts](./media/user-guide/usbx-events/image185.png)

**Descripción**

Este evento representa un evento de creación de instancia de la clase de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: clase
- Campo de información 2: instancia de clase
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-class-instance-destroy"></a>Destrucción de instancia de clase de pila de hosts 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Icono** ![Icono de destrucción de instancia de clase de pila de hosts](./media/user-guide/usbx-events/image186.png)

**Descripción**

Este evento representa un evento de destrucción de instancia de la clase de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: clase
- Campo de información 2: instancia de clase
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-configuration-delete"></a>Eliminación de configuración de pila de hosts 

#### <a name="ux_host_class_configuration_delete"></a>ux_host_class_configuration_delete

**Icono** ![Icono de eliminación de configuración de pila de hosts](./media/user-guide/usbx-events/image187.png)

**Descripción**

Este evento representa un evento de eliminación de configuración de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: configuración
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-configuration-enumerate"></a>Enumeración de configuración de pila de hosts 

#### <a name="ux_host_stack_configuration_enumerate"></a>ux_host_stack_configuration_enumerate

**Icono** ![Icono de enumeración de configuración de pila de hosts](./media/user-guide/usbx-events/image188.png)

**Descripción**

Este evento representa un evento de enumeración de configuración de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="stack-configuration-instance-create"></a>Creación de instancia de configuración de pila 

#### <a name="ux_host_stack_configuration_instance_create"></a>ux_host_stack_configuration_instance_create

**Icono** ![Icono de creación de instancia de configuración de pila de hosts](./media/user-guide/usbx-events/image189.png)

**Descripción**

Este evento representa un evento de creación de instancia de configuración de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: configuración
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-configuration-instance-delete"></a>Eliminación de instancia de configuración de pila de hosts 

#### <a name="ux_host_stack_configuration_instance_delete"></a>ux_host_stack_configuration_instance_delete

**Icono** ![Icono de eliminación de instancia de configuración de pila de hosts](./media/user-guide/usbx-events/image190.png)

**Descripción**

Este evento representa un evento de eliminación de instancia de configuración de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: configuración
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-configuration-set"></a>Establecimiento de configuración de pila de hosts 

#### <a name="ux_host_stack_configuration_set"></a>ux_host_stack_configuration_set

**Icono** ![Icono de establecimiento de configuración de pila de hosts](./media/user-guide/usbx-events/image191.png)

**Descripción**

Este evento representa un evento de establecimiento de configuración de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: configuración
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-device-address-set"></a>Establecimiento de dirección de dispositivo de pila de hosts 

#### <a name="ux_host_stack_device_address_set"></a>ux_host_stack_device_address_set

**Icono** ![Icono de establecimiento de dirección de dispositivo de pila de hosts](./media/user-guide/usbx-events/image192.png)

**Descripción**

Este evento representa un evento de establecimiento de dirección de dispositivo de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: dirección del dispositivo
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-device-configuration-get"></a>Obtención de configuración de dispositivo de pila de hosts 

#### <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

**Icono** ![Icono de obtención de configuración de dispositivo de pila de hosts](./media/user-guide/usbx-events/image193.png)

**Descripción**

Este evento representa un evento de obtención de configuración de dispositivo de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: configuración
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-device-configuration-select"></a>Selección de configuración de dispositivo de pila de hosts 

#### <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

**Icono** ![Icono de selección de configuración de dispositivo de pila de hosts](./media/user-guide/usbx-events/image194.png)

**Descripción**

Este evento representa un evento de selección de configuración de dispositivo de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: configuración
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-device-descriptor-read"></a>Lectura de descriptor de dispositivo de pila de hosts 

#### <a name="ux_host_stack_device_descriptor_read"></a>ux_host_stack_device_descriptor_read

**Icono** ![Icono de lectura de descriptor de dispositivo de pila de hosts](./media/user-guide/usbx-events/image195.png)

**Descripción**

Este evento representa un evento de lectura del descriptor de dispositivo de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-device-get"></a>Obtención de dispositivo de pila de hosts 

#### <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

**Icono** ![Icono de obtención de dispositivo de pila de hosts](./media/user-guide/usbx-events/image196.png)

**Descripción**

Este evento representa un evento de obtención de dispositivo de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: índice de dispositivo
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-device-remove"></a>Eliminación de dispositivo de pila de hosts 

#### <a name="ux_host_stack_device_remove"></a>ux_host_stack_device_remove

**Icono** ![Icono de eliminación de dispositivo de pila de hosts](./media/user-guide/usbx-events/image197.png)

**Descripción**

Este evento representa un evento de eliminación de dispositivo de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: HCD
- Campo de información 2: elemento principal
- Campo de información 3: índice de puerto
- Campo de información 4: dispositivo

### <a name="host-stack-device-resource-free"></a>Recurso libre de dispositivo de pila de hosts 

#### <a name="ux_host_stack_device_resource_free"></a>ux_host_stack_device_resource_free

**Icono** ![Icono de recurso libre de dispositivo de pila de hosts](./media/user-guide/usbx-events/image198.png)

**Descripción**

Este evento representa un evento de recurso libre de dispositivo de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-endpoint-instance-create"></a>Creación de instancia de punto de conexión de pila de hosts 

#### <a name="ux_host_stack_endpoint_instance_create"></a>ux_host_stack_endpoint_instance_create

**Icono** ![Icono de creación de instancia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image199.png)

**Descripción**

Este evento representa un evento de creación de instancia de punto de conexión de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: punto de conexión
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-endpoint-instance-delete"></a>Eliminación de instancia de punto de conexión de pila de hosts 

#### <a name="ux_host_stack_endpoint_instance_delete"></a>ux_host_stack_endpoint_instance_delete

**Icono** ![Icono de eliminación de instancia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image200.png)

**Descripción**

Este evento representa un evento de eliminación de instancia de punto de conexión de la pila de hosts USBX.

**Campos de información**

- Campo de información 2: punto de conexión
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-endpoint-reset"></a>Restablecimiento de punto de conexión de pila de hosts 

#### <a name="ux_host_stack_endpoint_reset"></a>ux_host_stack_endpoint_reset

**Icono** ![Icono de restablecimiento de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image201.png)

**Descripción**

Este evento representa un evento de restablecimiento de punto de conexión de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: punto de conexión
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-endpoint-transfer-abort"></a>Anulación de transferencia de punto de conexión de pila de hosts 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

**Icono** ![Icono de anulación de transferencia de punto de conexión de pila de hosts](./media/user-guide/usbx-events/image202.png)

**Descripción**

Este evento representa un evento de anulación de transferencia de punto de conexión de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: punto de conexión
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-host-controller-register"></a>Registro de controlador de host de pila de hosts 

#### <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

**Icono** ![Icono de registro de controlador de host de pila de hosts](./media/user-guide/usbx-events/image203.png)

**Descripción**

Este evento representa un registro de controlador de host de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: nombre de HCD
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-initialize"></a>Inicialización de pila de hosts 

#### <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

**Icono** ![Icono de inicialización de pila de hosts](./media/user-guide/usbx-events/image204.png)

**Descripción**

Este evento representa un evento de inicialización de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-interface-endpoint-get"></a>Obtención de punto de conexión de interfaz de pila de hosts 

#### <a name="interface_-tcp-retry-entry"></a>Entrada de reintento de interfaz TCP

**Icono** ![Icono de obtención de punto de conexión de interfaz de pila de hosts](./media/user-guide/usbx-events/image205.png)

**Descripción**

Este evento representa un evento interno de reintento de TCP de NetX.

**Campos de información**

- Campo de información 1: interfaz
- Campo de información 2: índice de punto de conexión
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-interface-instance-create"></a>Creación de instancia de interfaz de pila de hosts 

#### <a name="ux_host_stack_interface_instance_create"></a>ux_host_stack_interface_instance_create

**Icono** ![Icono de creación de instancia de interfaz de pila de hosts](./media/user-guide/usbx-events/image206.png)

**Descripción**

Este evento representa un evento de creación de instancia de interfaz de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: interfaz
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-interface-instance-delete"></a>Eliminación de instancia de interfaz de pila de hosts 

#### <a name="ux_host_stack_interface_instance_delete"></a>ux_host_stack_interface_instance_delete

**Icono** ![Icono de eliminación de instancia de interfaz de pila de hosts](./media/user-guide/usbx-events/image207.png)

**Descripción**

Este evento representa un evento de eliminación de instancia de interfaz de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: interfaz
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-interface-set"></a>Establecimiento de interfaz de pila de hosts 

#### <a name="ux_host_stack_interface_set"></a>ux_host_stack_interface_set

**Icono** ![Icono de establecimiento de interfaz de pila de hosts](./media/user-guide/usbx-events/image208.png)

**Descripción**

Este evento representa un evento de establecimiento de la interfaz de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: interfaz
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-interface-setting-select"></a>Selección de configuración de interfaz de pila de hosts 

#### <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

**Icono** ![Icono de selección de configuración de interfaz de pila de hosts](./media/user-guide/usbx-events/image209.png)

**Descripción**

Este evento representa un evento de selección de la configuración de interfaz de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: interfaz
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-new-configuration-create"></a>Creación de nueva configuración de pila de hosts 

#### <a name="ux_host_stack_new_configuration_create"></a>ux_host_stack_new_configuration_create

**Icono** ![Icono de creación de nueva configuración de pila de hosts](./media/user-guide/usbx-events/image210.png)

**Descripción**
 
Este evento representa un evento de creación de nueva configuración de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: configuración
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-new-device-create"></a>Creación de nuevo dispositivo de pila de hosts 

#### <a name="ux_host_stack_new_device_create"></a>ux_host_stack_new_device_create

**Icono** ![Icono de creación de nuevo dispositivo de pila de hosts](./media/user-guide/usbx-events/image211.png)

**Descripción**
 
 Este evento representa un evento de creación de un nuevo dispositivo de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: HCD
- Campo de información 2: propietario del dispositivo
- Campo de información 3: índice de puerto
- Campo de información 4: dispositivo

### <a name="host-stack-new-endpoint-create"></a>Creación de nuevo punto de conexión de pila de hosts 

#### <a name="ux_host_stack_new_endpoint_create"></a>ux_host_stack_new_endpoint_create

**Icono** ![Icono de creación de nuevo punto de conexión de pila de hosts](./media/user-guide/usbx-events/image212.png)

**Descripción**
 
Este evento representa un evento de creación de un nuevo punto de conexión de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: interfaz
- Campo de información 2: punto de conexión
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-root-hub-change-process"></a>Proceso de cambio de centro de conectividad raíz de pila de hosts 

#### <a name="ux_host_stack_rh_change_process"></a>ux_host_stack_rh_change_process

**Icono** ![Icono de proceso de cambio de centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image213.png)

**Descripción**
 
Este evento representa un proceso de cambio del centro de conectividad raíz de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: índice de puerto
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-root-hub-device-extraction"></a>Extracción de dispositivo de centro de conectividad raíz de pila de hosts 

#### <a name="ux_host_stack_rh_device_extraction"></a>ux_host_stack_rh_device_extraction

**Icono** ![Icono de extracción de dispositivo de centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image214.png)

**Descripción**

Este evento representa un evento de extracción de dispositivo del centro de conectividad raíz de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: HCD
- Campo de información 2: índice de puerto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-root-hub-device-insertion"></a>Inserción de dispositivo en centro de conectividad raíz de pila de hosts 

#### <a name="ux_host_stack_rh_device_insertion"></a>ux_host_stack_rh_device_insertion

**Icono** ![Icono de inserción de dispositivo en centro de conectividad raíz de pila de hosts](./media/user-guide/usbx-events/image215.png)

**Descripción**

Este evento representa una inserción de dispositivo en el centro de conectividad raíz de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: HCD
- Campo de información 2: índice de puerto
- Campo de información 3: no se usa
- Campo de información 4: no se usa

### <a name="host-stack-transfer-request"></a>Solicitud de transferencia de pila de hosts 

#### <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

**Icono** ![Icono de solicitud de transferencia de pila de hosts](./media/user-guide/usbx-events/image216.png)

**Descripción**

Este evento representa una solicitud de transferencia de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: punto de conexión
- Campo de información 3: solicitud de transferencia
- Campo de información 4: no se usa

### <a name="host-stack-transfer-request-abort"></a>Anulación de solicitud de transferencia de pila de hosts 

#### <a name="internal-io-driver-get-status"></a>Obtención de estado del controlador de E/S interna

**Icono** ![Icono de anulación de solicitud de transferencia de pila de hosts](./media/user-guide/usbx-events/image217.png)

**Descripción**

Este evento representa una anulación de la solicitud de transferencia de la pila de hosts USBX.

**Campos de información**

- Campo de información 1: dispositivo
- Campo de información 2: punto de conexión
- Campo de información 3: solicitud de transferencia
- Campo de información 4: no se usa

### <a name="usbx-error"></a>Error de USBX 

#### <a name="ux_error"></a>ux_error

**Icono** ![Icono de error de U S B X](./media/user-guide/usbx-events/image218.png)

**Descripción**

Este evento representa un evento de error de USBX.

**Campos de información**

- Campo de información 1: error de USBX
- Campo de información 2: nombre del error
- Campo de información 3: no se usa
- Campo de información 4: no se usa