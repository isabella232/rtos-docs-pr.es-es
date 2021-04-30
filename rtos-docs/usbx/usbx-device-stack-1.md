---
title: 'Capítulo 1: Introducción a pila de dispositivos de Azure RTOS USBX'
description: USBX es una pila USB que incorpora todas las características para aplicaciones con alto grado de inserción. En este capítulo se presenta USBX y se describen sus aplicaciones y ventajas.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6965303f1fbf19212b9f7ff20f811a71fb207f54
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816469"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a>Capítulo 1: Introducción a pila de dispositivos de Azure RTOS USBX

USBX es una pila USB que incorpora todas las características para aplicaciones con alto grado de inserción. En este capítulo se presenta USBX y se describen sus aplicaciones y ventajas. 

## <a name="usbx-features"></a>Características de USBX

USBX admite las tres especificaciones USB existentes: 1.1, 2.0 y OTG. Está diseñado para ser escalable y se adapta a las topologías USB simples con un solo dispositivo conectado, así como topologías complejas con varios dispositivos y concentradores en cascada. USBX admite todos los tipos de transferencia de datos de los protocolos USB: control, masivo, interrupción e isocrónico.

USBX admite tanto el lado del host como el del dispositivo. Cada lado se compone de tres capas.

- Capa de controlador
- Capa de pila
- Capa de clase

La relación entre las capas USB es la siguiente:

![Capas USB](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>Aspectos destacados del producto

- Soporte completo del procesador ThreadX
- Sin regalías
- Código fuente ANSI C completo
- Rendimiento en tiempo real
- Soporte técnico con capacidad de respuesta
- Compatibilidad con varias clases
- Varias instancias de clase
- Integración de clases con ThreadX, FileX y NetX
- Compatibilidad con dispositivos USB con varias configuraciones
- Compatibilidad con dispositivos compuestos USB
- Compatibilidad con la administración de energía USB
- Compatibilidad con el OTG USB
- Exportación de eventos de seguimiento para TraceX

## <a name="powerful-services-of-usbx"></a>Servicios eficaces de USBX

### <a name="complete-usb-device-framework-support"></a>Compatibilidad completa con el marco de dispositivos USB

USBX puede admitir los dispositivos USB más exigentes, incluidas varias configuraciones, varias interfaces y varias configuraciones alternativas.

### <a name="easy-to-use-apis"></a>API fáciles de usar

USBX proporciona la mejor pila USB con alto grado de inserción de una manera fácil de comprender y usar. La API de USBX hace que los servicios sean intuitivos y coherentes. Mediante el uso de las API de clase USBX proporcionadas, la aplicación de usuario no necesita comprender la complejidad de los protocolos USB.
