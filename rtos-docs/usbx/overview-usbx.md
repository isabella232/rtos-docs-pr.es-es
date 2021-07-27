---
title: Información general sobre Azure RTOS USBX
description: Azure RTO USBX es un host USB, un dispositivo y una pila insertada "on-the-go" (OTG) de alto rendimiento; Azure RTO USBX está totalmente integrado con Azure RTO ThreadX y está disponible para todos los procesadores compatibles con Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3c214a49f7dd1af20c20f07412fb072dd785b16f
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754835"
---
# <a name="overview-of-azure-rtos-usbx"></a>Información general sobre Azure RTOS USBX

Azure RTOS USBX es un host USB de alto rendimiento, un dispositivo y una pila insertada "on-the-go" (OTG). Azure RTOS USBX está totalmente integrado con Azure RTOS ThreadX y está disponible para todos los procesadores compatibles con ThreadX. Al igual que ThreadX, Azure RTOS USBX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las aplicaciones profundamente insertadas, que requieren una interfaz con dispositivos USB.

## <a name="host-device-otg--extensive-class-support"></a>Compatibilidad con host, dispositivo, OTG y amplia compatibilidad de clases

La pila de protocolos USB insertados en el dispositivo o del host de Azure RTOS USBX es una solución USB insertada de nivel industrial diseñada específicamente para aplicaciones de IoT, en tiempo real profundamente insertadas. Azure RTOS USBX proporciona compatibilidad con host, dispositivo y OTG, así como una amplia compatibilidad de clases. Azure RTO USBX está totalmente integrado con el sistema operativo en tiempo real ThreadX, el sistema de archivos compatible con FAT insertado Azure RTO FileX, Azure RTOS NetX y las pilas TCP/IP insertadas de Azure RTO NetX Duo. Todo esto, combinado con una superficie realmente pequeña, una ejecución rápida y una facilidad de uso superior, hacen que Azure RTOS USBX sea la opción ideal para las aplicaciones IoT insertadas más exigentes que requieren conectividad USB.

### <a name="usbx-memory-footprint"></a>Superficie de memoria de USBX

Azure RTOS USBX tiene una superficie increíblemente pequeña de 10,5 KB de memoria FLASH y 5,1 KB de RAM para la compatibilidad de CDC y ACM del dispositivo Azure RTOS USBX. El host de Azure RTOS USBX requiere un mínimo de 18 KB de memoria FLASH y 25 KB de RAM para admitir CDC y ACM.

Se necesita una memoria de área de instrucciones adicional de 10 KB a 13 KB para la funcionalidad de TCP. El uso de RAM de Azure RTOS USBX suele oscilar entre 2,6 KB y 3,6 KB más la memoria del grupo de paquetes, definida por la aplicación.

Al igual que ThreadX, el tamaño de Azure RTOS USBX se escala automáticamente en función de los servicios que realmente usa la aplicación. Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.

### <a name="usb-interoperability-verification"></a>Comprobación de interoperabilidad USB

La pila de dispositivos de Azure RTOS USBX se ha probado rigurosamente con USBCV, la herramienta de prueba estándar de USB IF, para garantizar el cumplimiento completo de las especificaciones USB y la interoperabilidad con distintos sistemas host.
Además, el laboratorio de pruebas independiente Allion, de Taiwán, ha comprobado y certificado la pila OTG de Azure RTOS USBX.

### <a name="usb-host-controller-support"></a>Compatibilidad con el controlador de host USB

Azure RTOS USBX admite los principales estándares USB, como OHCI y EHCI. Además, Azure RTOS USBX admite controladores propietarios de host USB discretos de Atmel, Microchip, Philips, Renesas, ST y TI, entre otros proveedores. Azure RTOS USBX también admite varios controladores de host en la misma aplicación.
Compatibilidad con controladores de dispositivos USB Azure RTOS USBX admite controladores de dispositivos USB populares de Analog Devices, Atmel, Microchip, NXP, Philips, Renesas, ST y TI, entre otros proveedores.

### <a name="extensive-host-class-support"></a>Amplia compatibilidad con la clase de host

El host de Azure RTOS USBX proporciona compatibilidad con las clases más populares, como ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID (teclado, mouse y control remoto), HUB, PIMA (PTP/MTP), PRINTER, PROLIFIC y STORAGE.

### <a name="extensive-usb-device-class-support"></a>Amplia compatibilidad con la clase de dispositivos USB

El dispositivo Azure RTOS USBX proporciona compatibilidad con las clases más populares, como CDC/ACM, CDC/ECM, DFU, HID, PIMA (PTP/MTP) (w/MTP), RNDIS y STORAGE. También está disponible la compatibilidad con las clases personalizadas.

### <a name="pictbridge-support"></a>Compatibilidad con PictBridge

Azure RTOS USBX admite la implementación completa de PictBridge tanto en el host como en el dispositivo. PictBridge se encuentra en la parte superior de la clase PIMA (PTP/MTP) de Azure RTOS USBX, en ambos lados. El estándar de PictBridge permite la conexión de una cámara fija digital o un smartphone directamente a una impresora sin un PC, lo que permite la impresión directa en algunas impresoras compatibles con PictBridge. Cuando se conecta una cámara o un teléfono a una impresora, esta es el host USB y la cámara es el dispositivo USB. Pero, con PictBridge, la cámara aparecerá como el host y esta controlará los comandos. La cámara es el servidor de almacenamiento y la impresora, el cliente de almacenamiento. La cámara es el cliente de impresión y la impresora es el servidor de impresión. PictBridge usa USB como capa de transporte, pero se basa en PTP (Protocolo de transferencia de imágenes) para el protocolo de comunicación.

### <a name="custom-class-support"></a>Compatibilidad con clases personalizadas

El host y el dispositivo de Azure RTOS USBX admiten clases personalizadas. En la distribución de Azure RTOS USBX se proporciona una clase personalizada de ejemplo. Esta clase de bombeo de datos simple se denomina DPUMP y se puede usar como modelo para las clases de aplicación personalizadas.
Tecnología avanzada El host y el dispositivo de Azure RTOS USBX admiten clases personalizadas. En la distribución de Azure RTOS USBX se proporciona una clase personalizada de ejemplo. Azure RTOS USBX es una tecnología avanzada que incluye:

* Compatibilidad con host, dispositivo y OTG
* Compatibilidad con velocidad USB baja, completa y alta
* Escalado automático
* Totalmente integrado con ThreadX, Azure RTOS FileX y Azure RTOS NetX
* Métricas de rendimiento opcionales
* Compatibilidad con el análisis del sistema de Azure RTOS TraceX

## <a name="azure-rtos-usbx-apis"></a>API de Azure RTOS USBX

### <a name="azure-rtos-usbx-host-api"></a>API de host de Azure RTOS USBX

La API de host de Azure RTOS USBX es una API intuitiva y coherente, siguiendo una convención de nomenclatura sustantivo-verbo. Todas las API tienen ux_host_* al inicio para identificarlas fácilmente como USBX. Las API de bloqueo tienen un tiempo de espera de subproceso opcional.

* ASIX
    - Memoria flash mínima de 0,3 KB y de 4 KB de RAM
    - Escalado automático Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_class_asix_* *
* AUDIO
    - Memoria flash mínima de 1,2 KB y de 4 KB de RAM
    - Escalado automático
    - API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_class_audio_* *
* CDC/ACM
    - Memoria flash mínima de1,4 KB y de 4 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_class_cdc_acm_* *
* HID
    - Memoria flash mínima de 0,3 KB y de 4 KB de RAM
    - Teclado, mouse y compatibilidad remota
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_class_hid_* * 
* CONCENTRADOR
    - Memoria flash mínima de 1,7 KB y de 2 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_class_hub_* *
* PIMA (PTP/MTP)
    - Memoria flash mínima de 0,9 KB y de 8 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_class_pima_* *
* PRINTER
    - Memoria flash mínima de 0,8 KB y de 8 KB de RAM
    - Escalado automático
    -  Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    -  API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_class_printer_* *
* PROLIFIC
    - Memoria flash mínima de 1,5 KB y de 4 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_class_prolific_* *
* STORAGE
    - Memoria flash mínima de 5,6 KB y de 4 KB de RAM
    - Escalado automático<br> Integrado con Azure RTOS FileX
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_class_storage_* *
* Pila de host de USB
    - Admite muchos controladores de host
    - Memoria flash mínima de 18 KB y de 25 KB de RAM
    - Escalado automático
    - Compatibilidad con varios controladores de host en la misma plataforma
    -  Compatibilidad con velocidad USB baja, completa y alta
    -  Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    -  API de host de Azure RTOS USBX intuitivas con el siguiente formato: *ux_host_stack_*  * 
* Controladores de host propietarios, OHCI y EHCI 

### <a name="azure-rtos-usbx-device-api"></a>API de dispositivo de Azure RTOS USBX

La API de dispositivo de Azure RTOS USBX es una API intuitiva y coherente, siguiendo una convención de nomenclatura sustantivo-verbo. Todas las API tienen ux_device_* al inicio para identificarlas fácilmente como USBX. Las API de bloqueo tienen un tiempo de espera de subprocesos opcional. Consulte la [Guía de usuario de host de Azure RTOS USBX](usbx-host-stack-about.md) para obtener más información.

* CDC/ACM
    - Memoria flash mínima de 0.8 KB y de 2 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de dispositivo de Azure RTOS USBX intuitivas con el siguiente formato: *ux_device_class_cdc_acm_**
* CDC/ECM
    - Memoria flash mínima de 1,5 KB y de 4 KB a 8 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX<br> API de dispositivo de Azure RTOS USBX intuitivas con el siguiente formato: *ux_device_class_cdc_ecm_**
* DFU
    - Memoria flash mínima de 1,1 KB y de 2 KB de RAM
    -  Escalado automático
    -  Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de dispositivo de Azure RTOS USBX intuitivas con el siguiente formato: *ux_device_class_dfu_* * 
* GSER
    - Memoria flash mínima de 0,6 KB y de 4 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de dispositivo de Azure RTOS USBX intuitivas con el siguiente formato: *ux_device_class_gser_* *
* HID
    - Memoria flash mínima de 0,9 KB y de 2 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de dispositivo de Azure RTOS USBX intuitivas con el siguiente formato: *ux_device_class_hid_* * PIMA (PTP/MTP)
    - Memoria flash mínima de 5,2 KB y de 8 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de dispositivo de Azure RTOS USBX intuitivas con el siguiente formato: *ux_device_class_pima_* * 
* STORAGE
    - Memoria flash mínima de 2,3 KB y de 4 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de dispositivo de Azure RTOS USBX intuitivas con el siguiente formato: *ux_device_class_storage_* *
* RNDIS
    - Memoria flash mínima de 2,3 KB y de 4 KB a 8 KB de RAM
    - Escalado automático
    - Integrado con Azure RTOS NetX y Azure RTOS NetX DUO
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de dispositivo de Azure RTOS USBX intuitivas con el siguiente formato: *ux_device_class_rndls_* *
* Pila de dispositivo de Azure RTOS USBX
    - Memoria flash mínima de 2,3 KB y de 4 KB de RAM
    - Escalado automático
    - Seguimiento de nivel de sistema mediante Azure RTOS TraceX
    - API de dispositivo de Azure RTOS USBX intuitivas con el siguiente formato: *ux_device_class_storage_* *
* Controladores de host propietarios

## <a name="next-steps"></a>Pasos siguientes

Para empezar a trabajar con el host y la pila de dispositivos de Azure RTOS USBX, siga nuestra [Guía de usuario de host de Azure RTOS USBX](usbx-host-stack-about.md)o la [Guía de usuario del dispositivo de Azure RTOS USBX](usbx-device-stack-about.md).