---
title: 'Capítulo 2: Instalación y uso de Iperf de Azure RTOS NetX Duo'
description: En este capítulo, se proporcionan instrucciones para instalar y usar el ejemplo de Iperf.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7e80d89a334ceec3467b23574ab5c231a15f68a1
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609858"
---
# <a name="chapter-2-installation-and-use"></a>Capítulo 2: Instalación y uso

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la demostración de Iperf de NetX Duo.

## <a name="installing-the-demonstration"></a>Instalación de la demostración

Siga las instrucciones de instalación específicas de la plataforma proporcionadas en la distribución.

## <a name="installing-iperf"></a>Instalación de Iperf

Hay una variedad de programas Iperf que puede usar. Sin embargo, los ejemplos de este documento se basan en ***Jperf 2.0.2*** basado en Java, que está disponible en varios orígenes en Internet.

> [Nota] *Jperf requiere que Java esté instalado en el equipo host.*

## <a name="setting-the-ip-address"></a>Establecimiento de la dirección IP

De manera predeterminada, la dirección IP de la demostración de Iperf de NetX Duo está establecida en **192.2.2.149**. Esto se configura en el archivo **_demo_netx_duo_iperf.c_ *_ como parámetro para la llamada a _* _nx_ip_create_**.

## <a name="network-assumptions"></a>Suposiciones de red

En esta demostración, se da por supuesto que el equipo host de Iperf y la placa de destino que ejecuta la demostración de Iperf de NetX Duo están conectadas a un conmutador Ethernet full-duplex de 100 Mbps. Para lograr el mejor rendimiento, no debe haber ningún otro tráfico en la red de prueba.

También es posible conectar el host de Iperf y la placa de destino de NetX Duo directamente con un cable Ethernet cruzado.

## <a name="running-the-demonstration"></a>Ejecución de la demostración

La ejecución de la demostración es fácil; simplemente cargue, compile y ejecute el proyecto de demostración de Iperf de NetX Duo, que normalmente se llama ***demo_netx_duo_iperf***.

## <a name="browse-to-the-demonstration"></a>Exploración de la demostración

Vaya a la placa de destino mediante un explorador en la plataforma del host de Iperf. Suponiendo que la dirección IP de la placa de destino es **192.2.2.149**, el siguiente es un ejemplo de la página web inicial de la demostración de Iperf de NetX Duo.

![Ejemplo de la página web inicial de Iperf](media/Picture1.jpg)

## <a name="running-jperf"></a>Ejecución de Jperf

Ejecutar Jperf es fácil, simplemente haga doble clic en el archivo por lotes ***jperf.bat** _ de Windows. Esto inicia el IDE de Jperf, como se muestra a continuación. Una vez que se muestre el IDE de Jperf, el campo _ *Server Address** (Dirección del servidor) se debe establecer en la dirección IP de la placa de destino de la demostración de Iperf de NetX Duo. En este ejemplo, la dirección IP de la placa de destino de NetX Duo es **192.2.2.149**. También merece la pena mencionar los campos **UDP Bandwidth** (Ancho de banda de UDP) y **UDP Packet Size** (Tamaño de paquete de UDP). Estos campos se deben configurar para obtener un rendimiento óptimo de la recepción de UDP, como se muestra a continuación.

![Optimización del rendimiento de UDP.](media/Picture2.jpg)
