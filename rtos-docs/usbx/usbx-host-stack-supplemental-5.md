---
title: USBX OTG
description: USBX admite las funcionalidades OTG de USB cuando hay una controladora USB compatible con OTG disponible en el diseño del hardware.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3349059f168b145629ca9bf030ddb141350ca760
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816070"
---
# <a name="chapter-5-usbx-otg"></a>Capítulo 5: USBX OTG

USBX admite las funcionalidades OTG de USB cuando hay una controladora USB compatible con OTG disponible en el diseño del hardware.

USBX admite OTG en la pila USB principal, pero para que OTG funcione, requiere una controladora USB específica. Puede encontrar las funciones de la controladora de USBX OTG en el directorio ***usbx_otg***. La versión actual de USBX solo admite NXP LPC3131 con funcionalidad de OTG completa.

Puede encontrar las funciones del controlador de la controladora habituales (host o dispositivo) en los directorios usbx_device_controllers y usbx_host_controllers de USBX estándar, pero el directorio ***usbx_otg*** contiene las funciones del OTG específicas asociadas con la controladora USB.

Hay cuatro categorías de funciones para una controladora de OTG, además de las funciones habituales de host o de dispositivo.

- Funciones específicas de VBUS
- Inicio y detención de la controladora
- Administrador de roles USB
- Controladores de interrupciones

## <a name="vbus-functions"></a>Funciones de VBUS

Cada controladora debe tener un administrador de VBUS para cambiar el estado de VBUS en función de los requisitos de administración de energía. Normalmente, esta función solo realiza la activación o desactivación de VBUS.

## <a name="start-and-stop-the-controller"></a>Inicio y detención de la controladora

A diferencia de una implementación USB normal, OTG requiere que la pila de hosts o de dispositivos se activen y desactiven al cambiar el rol.

## <a name="usb-role-manager"></a>Administrador de roles USB

El administrador de roles USB recibe comandos para cambiar el estado del USB. Hay varios estados que necesitan transiciones hacia y desde los estados que se indican en la tabla siguiente.

| Estado                    | Value | Descripción                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| UX_OTG_IDLE            | 0     | El dispositivo está inactivo. No está conectado a nada. |
| UX_OTG_IDLE_TO_HOST  | 1     | El dispositivo está conectado a un conector de tipo A.             |
| UX_OTG_IDLE_TO_SLAVE | 2     | El dispositivo está conectado a un conector de tipo B.             |
| UX_OTG_HOST_TO_IDLE  | 3     | El dispositivo host se ha desconectado.                          |
| UX_OTG_HOST_TO_SLAVE | 4     | Intercambio de roles de Host a Subordinado.                          |
| UX_OTG_SLAVE_TO_IDLE | 5     | El dispositivo subordinado está desconectado.                          |
| UX_OTG_SLAVE_TO_HOST | 6     | Intercambio de roles de Subordinado a Host.                          |

## <a name="interrupt-handlers"></a>Controladores de interrupciones

Tanto los controladores de controladora de dispositivo como de host para OTG necesitan diferentes controladores de interrupción para supervisar señales además de las interrupciones USB tradicionales; en particular, las señales debidas a SRP y VBUS.

Veamos cómo se inicializa una controladora USB OTG. Aquí se usa NXP LPC3131 como ejemplo.

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

En este ejemplo, se inicializa LPC3131 en el modo OTG pasando una función VBUS y una devolución de llamada para el cambio de modo (de host a subordinado o viceversa).

La función de devolución de llamada simplemente debe registrar el nuevo modo y reactivar un subproceso pendiente para que actúe en función del nuevo estado.

```C
void tx_demo_change_mode_callback(ULONG mode)
{
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

El modo que se pasa puede tener los valores siguientes.

- UX_OTG_MODE_IDLE
- UX_OTG_MODE_SLAVE
- UX_OTG_MODE_HOST

La aplicación siempre puede comprobar qué dispositivo es examinando la variable.

```C
ux_system_otg ->ux_system_otg_device_type
```

Su valor puede ser uno de los siguientes:

- UX_OTG_DEVICE_A
- UX_OTG_DEVICE_B
- UX_OTG_DEVICE_IDLE

Un dispositivo host de USB OTG siempre puede solicitar un intercambio de roles emitiendo el comando correspondiente.

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */

ux_host_stack_role_swap(storage ->ux_host_class_storage_device);
```

En el caso de un dispositivo subordinado, no hay ningún comando que pueda emitir, pero puede establecer un estado para cambiar el rol; el host recogerá este estado el host cuando emita GET_STATUS y, después, se iniciará el intercambio.

```C
/* We are a B device, ask for role swap. The next GET_STATUS from the host will get the status change and do the HNP. */

ux_system_otg ->ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
