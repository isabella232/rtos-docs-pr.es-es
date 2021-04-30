---
title: 'Capítulo 2: Instalación y uso de Azure RTOS TraceX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la herramienta de análisis del sistema de Azure RTOS TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815769"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a>Capítulo 2: Instalación y uso de Azure RTOS TraceX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la herramienta de análisis del sistema de Azure RTOS TraceX. 

## <a name="product-distribution"></a>Distribución del producto

Para obtener la aplicación TraceX desde [Microsoft App Store](https://microsoft.com/store/apps), busque TraceX o vaya directamente a la [página de TraceX](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab). Después, haga lo siguiente.

1. En la página de TraceX de App Store, haga clic en el botón **Obtener** o **Instalar** para instalar TraceX.

1. Puede que el explorador le muestre un mensaje preguntándole si quiere abrir Microsoft Store, como se muestra en la siguiente figura. Si es así, seleccione el botón **Abrir**.
![Seleccione Abrir para instalar TraceX](../guix/media/guix-studio/open-ms-store.png).

1. Cuando finalice la instalación, seleccione el botón **Iniciar**. 

## <a name="using-tracex"></a>Uso de TraceX

Usar TraceX es tan sencillo como abrir un archivo de seguimiento dentro de TraceX. Ejecute TraceX mediante el botón ***Iniciar** _. En este punto, observará la interfaz gráfica de usuario (GUI) de TraceX. Ahora está listo para usar TraceX para ver gráficamente un búfer de seguimiento de destino existente. Es sencillo; para ello, haga clic en _ *_Archivo -> Abrir_** y, después, escriba el archivo de seguimiento binario.

>[!IMPORTANT]
>*También puede hacer doble clic en cualquier archivo de seguimiento con una extensión de **trx**, que iniciará automáticamente TraceX*.

![Captura de pantalla de la GUI de TraceX](./media/user-guide/screen_shot_8.png)

**FIGURA 1**

>[!IMPORTANT]
>*Consulte el **capítulo 5** para obtener instrucciones sobre cómo generar búferes de seguimiento en el destino mediante ThreadX*.

## <a name="tracex-examples"></a>Ejemplos de TraceX

La primera vez que ejecute la aplicación TraceX, o cuando se actualice la aplicación TraceX, se le pedirá que instale los archivos de seguimiento de ejemplo de TraceX y el archivo custom_events.trxc en un directorio definido por el usuario en el equipo local.

Después de completar este paso de instalación, los archivos de seguimiento de ejemplo con la extensión **trx** se encuentran en el subdirectorio **TraceFiles** de la carpeta de instalación. Estos ejemplos creados previamente le ayudarán a familiarizarse con el uso de TraceX en los búferes de seguimiento generados por ThreadX que se ejecutan con la aplicación.

Un archivo de seguimiento de ejemplo siempre está presente es el archivo ***demo_threadx.trx** _. Este archivo de seguimiento de ejemplo muestra la ejecución de la demostración de ThreadX estándar, como se describe en el capítulo 6 del manual del usuario de _ThreadX*.

![Captura de pantalla del cuadro de diálogo Abrir en TraceX](./media/user-guide/screen_shot_9.png)

**FIGURA 2**
