---
title: Manual del usuario de la pila del dispositivo Azure RTOS USBX
description: En esta guía se proporciona información completa sobre Azure RTOS USBX, el software de base USB de alto rendimiento de Microsoft
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 042398377766a3e73f72d4dbba0478ba707d378a379fd33de7808675eb96f257
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788769"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a>Manual del usuario de la pila del dispositivo Azure RTOS USBX

En esta guía se proporciona información completa sobre Azure RTOS USBX, el software de base USB de alto rendimiento de Microsoft.

Está diseñado para el desarrollador de software en tiempo real insertado. El desarrollador debe estar familiarizado con las funciones estándar del sistema operativo en tiempo real, la especificación USB y el lenguaje de programación C.

Para obtener información técnica relacionada con USB, consulte la especificación USB y las especificaciones de clase USB que se pueden descargar en https://www.USB.org/developers

## <a name="organization"></a>Organización

- [**Capítulo 1**](usbx-device-stack-1.md): contiene una introducción a Azure RTOS USBX

- [**Capítulo 2**](usbx-device-stack-2.md) : proporciona los pasos básicos para instalar y usar Azure RTOS USBX con su aplicación ThreadX

- [**Capítulo 3**](usbx-device-stack-3.md): describe los componentes funcionales de la pila de dispositivos Azure RTOS USBX

- [**Capítulo 4**](usbx-device-stack-4.md): describe los servicios de pila de dispositivos Azure RTOS USBX

- [**Capítulo 5**](usbx-device-stack-5.md): describe cada clase de dispositivo Azure RTOS USBX, incluidas sus API

## <a name="customer-support-center"></a>Centro de soporte al cliente

Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos. Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:

1. Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.
2. Una descripción detallada de los cambios en la aplicación o en Azure RTOS ThreadX que precedieron al problema.
3. Contenido de la cadena de **_tx_version_id** que se encuentra en el archivo **_tx_port.h_** de la distribución. Esta cadena nos proporcionará información de valor sobre el entorno en tiempo de ejecución.
4. El contenido de la RAM de la variable *_tx_build_options* **ULONG**. Esta variable nos proporciona información sobre cómo se ha compilado la biblioteca de Azure RTOS ThreadX.
