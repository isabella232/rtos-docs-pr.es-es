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
# <a name="chapter-3-usbx-dpump-class-considerations"></a>Capítulo 3: Consideraciones acerca de la clase DPUMP de USBX

USBX contiene una clase DPUMP para el lado del host y del dispositivo. Esta clase no es una clase estándar en sí misma, sino un ejemplo en el que se muestra cómo crear un dispositivo simple mediante dos canalizaciones masivas y el envío de datos de ida y vuelta en estas dos canalizaciones. La clase DPUMP se puede usar para iniciar una clase personalizada o para dispositivos RS232 heredados.

Diagrama de flujo de DPUMP para USB:

![Diagrama de flujo de DPUMP para USB](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a>Clase de host DPUMP de USBX

El lado del host de la clase DPUMP tiene dos funciones, una para enviar datos y otra para recibir datos:

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

Ambas funciones se bloquean para facilitar la aplicación DPUMP. Si es necesario que ambas canalizaciones (ENTRADA y SALIDA) se ejecuten al mismo tiempo, la aplicación debe crear un subproceso de transmisión y un subproceso de recepción.

El prototipo de la función de escritura es el siguiente.

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

Donde:

- dpump es la instancia de la clase.
- data_pointer es el puntero al búfer que se va a enviar.
- requested_length es la longitud que se va a enviar.
- actual_length es la longitud enviada una vez finalizada la transferencia, ya sea completa o parcialmente.

El prototipo de la función receptora es similar.

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

A continuación, se presenta un ejemplo de la clase de host DPUMP donde una aplicación escribe un paquete en el lado del dispositivo y recibe el mismo paquete en la recepción:

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

## <a name="usbx-dpump-device-class"></a>Clase de dispositivo DPUMP de USBX

La clase de dispositivo DPUMP usa un subproceso, que se inicia al conectarse al host USB. El subproceso espera a que llegue un paquete al punto de conexión de salida masiva. Una vez recibido el paquete, copia el contenido en el búfer del punto de conexión de entrada masiva y expone una transacción en este punto de conexión, a la espera de que el host emita una solicitud de lectura desde este punto de conexión. Esto proporciona un mecanismo de bucle invertido entre los puntos de conexión de entrada masiva y salida masiva.
