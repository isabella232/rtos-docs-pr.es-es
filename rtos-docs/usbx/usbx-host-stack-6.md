---
title: 'Capítulo 6: Uso de la clase CDC-ECM de USBX'
description: USBX contiene una clase CDC-ECM para el lado del host y del dispositivo. Esta clase está diseñada para usarse con NetX, en concreto, la clase CDC-ECM de USBX actúa como el controlador de NetX. Esta es la razón por la que no hay ninguna API de CDC-ECM enumerada en el capítulo 5.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 18e7e075788623916de36cf911597230295b56c5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816345"
---
# <a name="chapter-6---usbx-cdc-ecm-class-usage"></a>Capítulo 6: Uso de la clase CDC-ECM de USBX

USBX contiene una clase CDC-ECM para el lado del host y del dispositivo. Esta clase está diseñada para usarse con NetX, en concreto, la clase CDC-ECM de USBX actúa como el controlador de NetX. Esta es la razón por la que no hay ninguna API de CDC-ECM enumerada en el capítulo 5.

Una vez que se inicializan NetX y USBX y que USBX encuentra una instancia de un dispositivo CDC-ECM, la aplicación usa únicamente NetX para comunicarse con el dispositivo. La inicialización sigue el patrón que se muestra en el ejemplo siguiente.

```c
UINT status;

/* The USB controller should be the last component initialized so that
everything is ready when data starts being received. */

/* Initialize USBX. */

ux_system_initialize(memory_pointer, UX_USBX_MEMORY_SIZE, UX_NULL, 0);

/* The code below is required for installing the host portion of USBX */
status = ux_host_stack_initialize(UX_NULL);

/* Register cdc_ecm class. */

status = ux_host_stack_class_register(_ux_system_host_class_cdc_ecm_name,
    ux_host_class_cdc_ecm_entry);

/* Perform the initialization of the network driver. */

_ux_network_driver_init();

/* Initialize NetX. Refer to NetX user guide for details to add initialization code. */

/* Register the platform-specific USB controller. */

status = ux_host_stack_hcd_register("controller_name", controller_entry, param1, param2);

/* Find the CDC-ECM class. */
class_cdc_ecm_get();

/* Now wait for the link to be up. */

while (cdc_ecm -> ux_host_class_cdc_ecm_link_state != UX_HOST_CLASS_CDC_ECM_LINK_STATE_UP)
    tx_thread_sleep(10);

/* At this point, everything has been initialized, and we've found a CDC-ECM device.
    Now NetX can be used to communicate with the device. */
```
