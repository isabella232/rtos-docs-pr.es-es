---
title: 'Capítulo 3: Ejecución de la prueba de transmisión de UDP'
description: En este capítulo, se proporcionan instrucciones para ejecutar el ejemplo de Iperf.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2a68ba3ddb71adc424002c815fd023f50b552997
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609859"
---
# <a name="chapter-3-running-the-demonstration"></a>Capítulo 3: Ejecución de la demostración

Suponiendo que el explorador del host muestra la página web de la demostración de Iperf de NetX Duo como se mostró anteriormente y que Jperf se ejecuta en el host, en este capítulo se describe cómo ejecutar cada prueba de Iperf.

## <a name="running-the-udp-transmit-test"></a>Ejecución de la prueba de transmisión de UDP

La prueba de transmisión de UDP determina el rendimiento de la transmisión de UDP de NetX Duo al host. En esta prueba, el destino de NetX Duo es el cliente y el host de Jperf es el servidor. En primer lugar, seleccione **Server** (Servidor) y **UDP** en el IDE de Jperf. A continuación, seleccione **Run IPerf!** (Ejecutar Iperf) para iniciar el servidor de Iperf, como se muestra a continuación.

![Ejecución de la prueba de transmisión de UDP.](media/picture3.jpg)

Ahora, en la página web de la demostración de Iperf de NetX Duo, seleccione el botón **Start UDP Transmit Test** (Iniciar prueba de transmisión de UDP) para iniciar la prueba. Ahora debería observar las estadísticas de rendimiento en el IDE de Jperf y la página web de NetX Duo actualizada, como se muestra a continuación.

![Estadísticas de la prueba de transmisión de UDP.](media/picture4.jpg)

Para completar la prueba, seleccione **este vínculo** en la página web de la demostración de Iperf de NetX Duo. Ahora debería observar los resultados de rendimiento de la prueba. En este ejemplo, el rendimiento de la transmisión de UDP desde el destino de NetX Duo al host de Iperf era de 94 Mbps en el destino de NetX Duo, como se muestra a continuación.

![Resultados de las pruebas de transmisión de UDP.](media/picture5.jpg)

## <a name="running-the-udp-receive-test"></a>Ejecución de la prueba de recepción de UDP

La prueba de recepción de UDP determina el rendimiento de la recepción de UDP de NetX Duo en el destino de NetX Duo. En esta prueba, el destino de NetX Duo es el servidor y el host de Jperf es el cliente. En primer lugar, seleccione **Client** (Cliente) y **UDP** en el IDE de Jperf. A continuación, seleccione **Start UDP Receive Test** (Iniciar prueba de recepción de UDP) en la página web de la demostración de Iperf de NetX Duo, como se muestra en la ilustración siguiente.

![Ejecución de la prueba de recepción de UDP.](media/picture6.jpg)

A continuación, seleccione **Run IPerf!** (Ejecutar Iperf) desde el IDE de Jperf y observe las estadísticas en el IDE de Jperf, como se muestra a continuación.

![Estadísticas de la prueba de recepción de UDP.](media/picture7.jpg)

Para completar la prueba, seleccione el vínculo **aquí** en la página web de la demostración de Iperf de NetX Duo. Ahora debería observar los resultados de rendimiento de la prueba. En este ejemplo, el rendimiento de la recepción de UDP en el destino de NetX Duo era de 95 Mbps, como se muestra a continuación.

![Resultado de la prueba de recepción de UDP](media/picture8.jpg)

## <a name="running-the-tcp-transmit-test"></a>Ejecución de la prueba de transmisión de TCP

La prueba de transmisión de TCP determina el rendimiento de la transmisión de TCP de NetX Duo al host. En esta prueba, el destino de NetX Duo es el cliente y el host de Jperf es el servidor. En primer lugar, seleccione **Server** (Servidor) y **TCP** en el IDE de Jperf. A continuación, seleccione **Run IPerf!** (Ejecutar Iperf) para iniciar el servidor de Iperf, como se muestra a continuación.

![Ejecución de la prueba de transmisión de TCP.](media/picture9.jpg)

Ahora, en la página web de la demostración de Iperf de NetX Duo, seleccione el botón **Start TCP Transmit Test** (Iniciar prueba de transmisión de TCP) para iniciar la prueba. Ahora debería observar las estadísticas de rendimiento en el IDE de Jperf y la página web de la demostración de Iperf de NetX Duo actualizada, como se muestra a continuación.

![Estadísticas de la prueba de transmisión de TCP.](media/picture10.jpg)

Para completar la prueba, seleccione el vínculo ***aquí*** en la página web de la demostración de Iperf de NetX Duo. Ahora debería observar los resultados de rendimiento de la prueba. En este ejemplo, el rendimiento de la transmisión de TCP en el destino de NetX Duo era de 91 Mbps, como se muestra a continuación.

![Resultados de la prueba de transmisión de TCP.](media/picture11.jpg)

## <a name="running-the-tcp-receive-test"></a>Ejecución de la prueba de recepción de TCP

La prueba de recepción de TCP determina el rendimiento de la recepción de TCP de NetX Duo en el destino de NetX Duo. En esta prueba, el destino de NetX Duo es el servidor y el host de Jperf es el cliente. En primer lugar, seleccione **Client** (Cliente) y **TCP** en el IDE de Jperf. A continuación, seleccione **Start TCP Receive Test** (Iniciar prueba de recepción de TCP) en la página web de NetX Duo, como se muestra.

![Ejecución de la prueba de recepción de TCP](media/picture12.jpg)

A continuación, seleccione **Run IPerf!** (Ejecutar Iperf) desde el IDE de Jperf y observe las estadísticas en el IDE de Jperf, como se muestra a continuación.

![Estadísticas de la prueba de recepción de TCP.](media/picture13.jpg)

Para completar la prueba, seleccione el vínculo ***aquí*** en la página web de la demostración de Iperf de NetX Duo. Ahora debería observar los resultados de rendimiento de la prueba. En este ejemplo, el rendimiento de la recepción de TCP en el destino de NetX Duo era de 71 Mbps, como se muestra a continuación.

![Resultados de la prueba de recepción de TCP.](media/picture14.jpg)
