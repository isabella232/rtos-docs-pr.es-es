---
title: Manual del usuario de la pila del host Azure RTOS USBX
description: En esta guía se proporciona información completa sobre Azure RTOS USBX, el software de base USB de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 243b12c4757ee945def8fea01c0d4114e39312ce
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815606"
---
# <a name="azure-rtos-usbx-host-stack-user-guide"></a>Manual del usuario de la pila del host Azure RTOS USBX

En esta guía se proporciona información completa sobre Azure RTOS USBX, el software de base USB de alto rendimiento de Microsoft.

Está diseñada para el desarrollador de software insertado en tiempo real. El desarrollador debe estar familiarizado con las funciones estándar del sistema operativo en tiempo real, la especificación USB y el lenguaje de programación C.

Para obtener información técnica relacionada con USB, consulte la especificación USB y las especificaciones de clase USB que se pueden descargar en [https://www.USB.org/developers](https://www.USB.org/developers).

## <a name="organization"></a>Organización

- [**Capítulo 1**](usbx-host-stack-1.md): contiene una introducción a Azure RTOS USBX.

- [**Capítulo 2**](usbx-host-stack-2.md): proporciona los pasos básicos para instalar y usar Azure RTOS USBX con su aplicación de Azure RTOS ThreadX.

- [**Capítulo 3**](usbx-host-stack-3.md): proporciona una visión general funcional de Azure RTOS USBX e información básica sobre USB.

- [**Capítulo 4**](usbx-host-stack-4.md): información detallada de la interfaz de la aplicación para Azure RTOS USBX en modo host.

- [**Capítulo 5**](usbx-host-stack-5.md): describe las API de las clases de host de Azure RTOS USBX.

- [**Capítulo 6**](usbx-host-stack-6.md): descripción de la clase CDC-ECM de Azure RTOS USBX.

## <a name="customer-support-center"></a>Centro de soporte al cliente

Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos. Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:

1. Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.
2. Una descripción detallada de los cambios en la aplicación o en Azure RTOS ThreadX que han precedido al problema.
3. Contenido de la cadena *_tx_version_id* que se encuentra en el archivo *tx_port.h* de la distribución. Esta cadena nos proporciona información valiosa sobre el entorno en tiempo de ejecución.
4. El contenido en la RAM de la variable *_tx_build_options* ULONG. Esta variable nos proporciona información sobre cómo se ha compilado la biblioteca de Azure RTOS ThreadX.
