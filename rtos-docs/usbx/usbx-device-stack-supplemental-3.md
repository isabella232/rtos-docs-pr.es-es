---
title: 'Capítulo 3: Consideraciones acerca de la clase DPUMP de USBX'
description: USBX contiene una clase DPUMP para el lado del host y del dispositivo. Esta clase no es una clase estándar en sí misma, sino un ejemplo en el que se muestra cómo crear un dispositivo simple mediante dos canalizaciones masivas y el envío de datos de ida y vuelta en estas dos canalizaciones.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d453d9ee19b9bc7ca7809102f087f46fdde05dc62b756d9eb3f38f493805be4
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791160"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a>Capítulo 3: Consideraciones acerca de la clase DPUMP de USBX

USBX contiene una clase **DPUMP** para el lado del host y del dispositivo. Esta clase no es una clase estándar en sí misma, sino un ejemplo en el que se muestra cómo crear un dispositivo simple mediante dos canalizaciones masivas y el envío de datos de ida y vuelta en estas dos canalizaciones. La clase **DPUMP** se puede usar para iniciar una clase personalizada o para dispositivos RS232 heredados.

Diagrama de flujo de DPUMP para USB:

![Diagrama de flujo de DPUMP para USB](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a>Clase de dispositivo DPUMP de USBX

La clase de dispositivo **DPUMP** usa un subproceso, que se inicia al conectarse al host USB. El subproceso espera a que llegue un paquete al punto de conexión de salida masiva. Una vez recibido el paquete, copia el contenido en el búfer del punto de conexión de entrada masiva y expone una transacción en este punto de conexión, a la espera de que el host emita una solicitud de lectura desde este punto de conexión. Esto proporciona un mecanismo de bucle invertido entre los puntos de conexión de entrada masiva y salida masiva.
