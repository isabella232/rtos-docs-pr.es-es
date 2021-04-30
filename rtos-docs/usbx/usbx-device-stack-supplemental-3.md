---
title: 'Capítulo 3: Consideraciones acerca de la clase DPUMP de USBX'
description: USBX contiene una clase DPUMP para el lado del host y del dispositivo. Esta clase no es una clase estándar en sí misma, sino un ejemplo en el que se muestra cómo crear un dispositivo simple mediante dos canalizaciones masivas y el envío de datos de ida y vuelta en estas dos canalizaciones.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c7870f1984fe3104d30e3b9efd82010218acbe27
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816462"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a><span data-ttu-id="f36d8-104">Capítulo 3: Consideraciones acerca de la clase DPUMP de USBX</span><span class="sxs-lookup"><span data-stu-id="f36d8-104">Chapter 3 - USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="f36d8-105">USBX contiene una clase **DPUMP** para el lado del host y del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f36d8-105">USBX contains a **DPUMP** class for the host and device side.</span></span> <span data-ttu-id="f36d8-106">Esta clase no es una clase estándar en sí misma, sino un ejemplo en el que se muestra cómo crear un dispositivo simple mediante dos canalizaciones masivas y el envío de datos de ida y vuelta en estas dos canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="f36d8-106">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="f36d8-107">La clase **DPUMP** se puede usar para iniciar una clase personalizada o para dispositivos RS232 heredados.</span><span class="sxs-lookup"><span data-stu-id="f36d8-107">The **DPUMP** class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="f36d8-108">Diagrama de flujo de DPUMP para USB:</span><span class="sxs-lookup"><span data-stu-id="f36d8-108">USB DPUMP flow chart:</span></span>

![Diagrama de flujo de DPUMP para USB](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="f36d8-110">Clase de dispositivo DPUMP de USBX</span><span class="sxs-lookup"><span data-stu-id="f36d8-110">USBX DPUMP Device Class</span></span>

<span data-ttu-id="f36d8-111">La clase de dispositivo **DPUMP** usa un subproceso, que se inicia al conectarse al host USB.</span><span class="sxs-lookup"><span data-stu-id="f36d8-111">The device **DPUMP** class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="f36d8-112">El subproceso espera a que llegue un paquete al punto de conexión de salida masiva.</span><span class="sxs-lookup"><span data-stu-id="f36d8-112">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="f36d8-113">Una vez recibido el paquete, copia el contenido en el búfer del punto de conexión de entrada masiva y expone una transacción en este punto de conexión, a la espera de que el host emita una solicitud de lectura desde este punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="f36d8-113">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="f36d8-114">Esto proporciona un mecanismo de bucle invertido entre los puntos de conexión de entrada masiva y salida masiva.</span><span class="sxs-lookup"><span data-stu-id="f36d8-114">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
