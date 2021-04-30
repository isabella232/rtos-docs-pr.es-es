---
title: 'Capítulo 1: Introducción a Azure RTOS TraceX'
description: Azure RTOS TraceX es una herramienta de análisis del sistema de Microsoft que muestra la información de eventos del sistema recopilada por ThreadX que se ejecuta en un destino insertado.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 3009d13388b3b7e8eca041dc6ede569a5caf5e9b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815842"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a>Capítulo 1: Introducción a Azure RTOS TraceX

Azure RTOS TraceX es una herramienta de análisis del sistema de Microsoft que muestra la información de eventos del sistema recopilada por ThreadX que se ejecuta en un destino insertado. El usuario es responsable de transferir el búfer de seguimiento almacenado en la RAM del destino insertado a un archivo binario en el equipo host. A continuación, el usuario puede abrir este archivo con TraceX y analizar gráficamente los eventos de destino, diagnosticar problemas del sistema y optimizar una aplicación operativa para mejorar el rendimiento y la administración de recursos.

## <a name="tracex-requirements"></a>Requisitos de TraceX

TraceX requiere Windows XP, o posterior. El sistema debe tener un mínimo de 192 de RAM, 2 GB de espacio disponible en el disco duro y una pantalla de 1024 x 768 con 256 colores como mínimo. Además, la aplicación debe ejecutarse en ThreadX V5.0 o posterior.

TraceX también requiere que esté instalado el marco de Microsoft .NET, una operación que el instalador de TraceX realiza automáticamente.

## <a name="tracex-constraints"></a>Restricciones de TraceX

TraceX tiene las siguientes restricciones:

- Los archivos de TraceX se limitan a un máximo de 32 768 eventos (aproximadamente 1 MB).
- El origen de la marca de tiempo debe tener una resolución razonable. Si la resolución es demasiado baja, los eventos se superponen. Si la resolución es demasiado alta, existe la posibilidad de que haya intervalos largos entre eventos.
- TraceX no puede medir con precisión los intervalos entre eventos mayores que el período del temporizador.
