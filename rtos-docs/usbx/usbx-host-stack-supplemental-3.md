---
title: Consideraciones acerca de la clase DPUMP de USBX
description: USBX contiene una clase DPUMP para el lado del host y del dispositivo.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9960b391418fa2f9203e761115bcba71cc3619e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816102"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a><span data-ttu-id="df823-103">Capítulo 3: Consideraciones acerca de la clase DPUMP de USBX</span><span class="sxs-lookup"><span data-stu-id="df823-103">Chapter 3: USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="df823-104">USBX contiene una clase DPUMP para el lado del host y del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="df823-104">USBX contains a DPUMP class for the host and device side.</span></span> <span data-ttu-id="df823-105">Esta clase no es una clase estándar en sí misma, sino un ejemplo en el que se muestra cómo crear un dispositivo simple mediante dos canalizaciones masivas y el envío de datos de ida y vuelta en estas dos canalizaciones.</span><span class="sxs-lookup"><span data-stu-id="df823-105">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="df823-106">La clase DPUMP se puede usar para iniciar una clase personalizada o para dispositivos RS232 heredados.</span><span class="sxs-lookup"><span data-stu-id="df823-106">The DPUMP class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="df823-107">Diagrama de flujo de DPUMP para USB:</span><span class="sxs-lookup"><span data-stu-id="df823-107">USB DPUMP flow chart:</span></span>

![Diagrama de flujo de DPUMP para USB](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a><span data-ttu-id="df823-109">Clase de host DPUMP de USBX</span><span class="sxs-lookup"><span data-stu-id="df823-109">USBX DPUMP Host Class</span></span>

<span data-ttu-id="df823-110">El lado del host de la clase DPUMP tiene dos funciones, una para enviar datos y otra para recibir datos:</span><span class="sxs-lookup"><span data-stu-id="df823-110">The host side of the DPUMP Class has two functions, one for sending data and one for receiving data:</span></span>

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

<span data-ttu-id="df823-111">Ambas funciones se bloquean para facilitar la aplicación DPUMP.</span><span class="sxs-lookup"><span data-stu-id="df823-111">Both functions are blocking to make the DPUMP application easier.</span></span> <span data-ttu-id="df823-112">Si es necesario que ambas canalizaciones (ENTRADA y SALIDA) se ejecuten al mismo tiempo, la aplicación debe crear un subproceso de transmisión y un subproceso de recepción.</span><span class="sxs-lookup"><span data-stu-id="df823-112">If it is necessary to have both pipes (IN and OUT) running at the same time, the application will be required to create a transmit thread and a receive thread.</span></span>

<span data-ttu-id="df823-113">El prototipo de la función de escritura es el siguiente.</span><span class="sxs-lookup"><span data-stu-id="df823-113">The prototype for the writing function is as follows.</span></span>

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

<span data-ttu-id="df823-114">Donde:</span><span class="sxs-lookup"><span data-stu-id="df823-114">Where:</span></span>

- <span data-ttu-id="df823-115">dpump es la instancia de la clase.</span><span class="sxs-lookup"><span data-stu-id="df823-115">dpump is the instance of the class</span></span>
- <span data-ttu-id="df823-116">data_pointer es el puntero al búfer que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="df823-116">data_pointer is the pointer to the buffer to be sent</span></span>
- <span data-ttu-id="df823-117">requested_length es la longitud que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="df823-117">requested_length is the length to send</span></span>
- <span data-ttu-id="df823-118">actual_length es la longitud enviada una vez finalizada la transferencia, ya sea completa o parcialmente.</span><span class="sxs-lookup"><span data-stu-id="df823-118">actual_length is the length sent after completion of the transfer, either successfully or partially.</span></span>

<span data-ttu-id="df823-119">El prototipo de la función receptora es similar.</span><span class="sxs-lookup"><span data-stu-id="df823-119">The prototype for the receiving function is similar.</span></span>

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

<span data-ttu-id="df823-120">A continuación, se presenta un ejemplo de la clase de host DPUMP donde una aplicación escribe un paquete en el lado del dispositivo y recibe el mismo paquete en la recepción:</span><span class="sxs-lookup"><span data-stu-id="df823-120">Here is an example of the host DPUMP class where an application writes a packet to the device side and receives the same packet on the reception:</span></span>

```C
/* We start with a 'A' in buffer. */
current_char = 'A';

while(1)
{
    /* Initialize the write buffer. */
    ux_utility_memory_set(out_buffer, current_char,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE);

    /* Increment the character in buffer. */
    current_char++;

    /* Check for upper alphabet limit. */
    if (current_char > 'Z')
        current_char = 'A';

    /* Write to the Data Pump Bulk out endpoint. */
    status = ux_host_class_dpump_write (dpump, out_buffer,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE,
        &actual_length);

    /* Verify that the status and the amount of data is correct. */
    if ((status == UX_SUCCESS) && actual_length == UX_HOST_CLASS_DPUMP_PACKET_SIZE)
    {
        /* Read to the Data Pump Bulk out endpoint. */
        status = ux_host_class_dpump_read (dpump, in_buffer,
            UX_HOST_CLASS_DPUMP_PACKET_SIZE, &actual_length);
    }
}
```

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="df823-121">Clase de dispositivo DPUMP de USBX</span><span class="sxs-lookup"><span data-stu-id="df823-121">USBX DPUMP Device Class</span></span>

<span data-ttu-id="df823-122">La clase de dispositivo DPUMP usa un subproceso, que se inicia al conectarse al host USB.</span><span class="sxs-lookup"><span data-stu-id="df823-122">The device DPUMP class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="df823-123">El subproceso espera a que llegue un paquete al punto de conexión de salida masiva.</span><span class="sxs-lookup"><span data-stu-id="df823-123">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="df823-124">Una vez recibido el paquete, copia el contenido en el búfer del punto de conexión de entrada masiva y expone una transacción en este punto de conexión, a la espera de que el host emita una solicitud de lectura desde este punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="df823-124">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="df823-125">Esto proporciona un mecanismo de bucle invertido entre los puntos de conexión de entrada masiva y salida masiva.</span><span class="sxs-lookup"><span data-stu-id="df823-125">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
