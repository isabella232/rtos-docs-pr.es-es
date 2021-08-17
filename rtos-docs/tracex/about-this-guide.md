---
title: Manual del usuario de Azure RTOS TraceX
description: Este manual contiene información completa sobre Azure RTOS TraceX, la herramienta de análisis del sistema basada en Microsoft Windows de Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 89a39112d6fc6d231408179ebb3867c21f927326930a1610529b142aa71a1027
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784077"
---
# <a name="about-this-guide"></a>Acerca de esta guía

Este manual contiene información completa sobre Azure RTOS TraceX, la herramienta de análisis del sistema basada en Microsoft Windows para Microsoft Azure RTOS.

Está destinada al desarrollador de software insertado en tiempo real que usa los componentes de complemento y el sistema operativo en tiempo real (RTOS) de Azure RTOS ThreadX. El desarrollador debe estar familiarizado con los conceptos estándar de Azure RTOS ThreadX, Azure RTOS FileX y Azure RTOS NetX.

## <a name="organization"></a>Organización

- [Capítulo 1](chapter1.md): contiene una introducción básica de Azure RTOS TraceX y describe su relación con el desarrollo en tiempo real.
- [Capítulo 2](chapter2.md): proporciona los pasos básicos para instalar y utilizar Azure RTOS TraceX a fin de analizar la aplicación desde el primer momento.
- [Capítulo 3](chapter3.md): describe las principales características de Azure RTOS TraceX.
- [Capítulo 4](chapter4.md): proporciona los detalles de las características de análisis de rendimiento de Azure RTOS TraceX.
- [Capítulo 5](chapter5.md): describe cómo configurar Azure RTOS ThreadX, Azure RTOS FileX y Azure RTOS NetX para generar un búfer de seguimiento que sea visible para Azure RTOS TraceX.
- [Capítulo 6](chapter6.md): describe los eventos de Azure RTOS TraceX de forma detallada.
- [Capítulo 7](chapter7.md): describe los eventos de Azure RTOS FileX de forma detallada.
- [Capítulo 8](chapter8.md): describe los eventos de Azure RTOS NetX de forma detallada.
- [Capítulo 9](chapter9.md): describe los eventos de Azure RTOS USBX de forma detallada.
- [Capítulo 10](chapter10.md): describe cómo crear eventos de usuario personalizados de forma detallada.
- [Capítulo 11](chapter11.md): describe el búfer de seguimiento interno de forma detallada.
- [Apéndice A](appendix-a.md): archivo específico del puerto de Azure RTOS ThreadX con su origen de marca de tiempo para recopilar eventos de seguimiento.
- [Apéndice B](appendix-b.md): archivo *tx_trace.h* de Azure RTOS ThreadX que muestra los detalles de implementación relacionados con el búfer de seguimiento de eventos.
- [Apéndice C](appendix-c.md): se resumen las utilidades de línea de comandos para convertir varios formatos de archivo en archivos binarios de Azure RTOS TraceX adecuados.
- [Apéndice D](appendix-d.md): ejemplos de archivos de seguimiento de volcado de varias herramientas de desarrollo.

## <a name="guide-conventions"></a>Convenciones de la guía

*Cursiva*: el tipo de letra denota títulos de libros, destaca palabras importantes e indica variables.

**Negrita**: el tipo de letra indica nombres de archivo, palabras clave y, además, destaca palabras importantes y variables.

> [!NOTE]
> Indica la información de la nota.

## <a name="customer-support-center"></a>Centro de asistencia al cliente

Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos. Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:

1. Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.
2. Una descripción detallada de los cambios en la aplicación o en Azure RTOS ThreadX que han precedido al problema.
3. Contenido de la cadena *_tx_version_id* que se encuentra en el archivo *tx_port.h* de la distribución. Esta cadena nos proporciona información valiosa sobre el entorno en tiempo de ejecución.
4. El contenido en la RAM de la variable *_tx_build_options* ULONG. Esta variable nos proporciona información sobre cómo se ha compilado la biblioteca de Azure RTOS ThreadX.
