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
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a><span data-ttu-id="a02c3-103">Capítulo 1: Introducción a Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="a02c3-103">Chapter 1 - Introduction to Azure RTOS TraceX</span></span>

<span data-ttu-id="a02c3-104">Azure RTOS TraceX es una herramienta de análisis del sistema de Microsoft que muestra la información de eventos del sistema recopilada por ThreadX que se ejecuta en un destino insertado.</span><span class="sxs-lookup"><span data-stu-id="a02c3-104">Azure RTOS TraceX is a Microsoft system analysis tool that displays system event information gathered by ThreadX running on an embedded target.</span></span> <span data-ttu-id="a02c3-105">El usuario es responsable de transferir el búfer de seguimiento almacenado en la RAM del destino insertado a un archivo binario en el equipo host.</span><span class="sxs-lookup"><span data-stu-id="a02c3-105">The user is responsible for transferring the trace buffer stored in RAM in the embedded target to a binary file on the host computer.</span></span> <span data-ttu-id="a02c3-106">A continuación, el usuario puede abrir este archivo con TraceX y analizar gráficamente los eventos de destino, diagnosticar problemas del sistema y optimizar una aplicación operativa para mejorar el rendimiento y la administración de recursos.</span><span class="sxs-lookup"><span data-stu-id="a02c3-106">The user can then open this file with TraceX and graphically analyze the target events, diagnosing system problems and tuning a working application to improve performance and resource management.</span></span>

## <a name="tracex-requirements"></a><span data-ttu-id="a02c3-107">Requisitos de TraceX</span><span class="sxs-lookup"><span data-stu-id="a02c3-107">TraceX Requirements</span></span>

<span data-ttu-id="a02c3-108">TraceX requiere Windows XP, o posterior.</span><span class="sxs-lookup"><span data-stu-id="a02c3-108">TraceX requires Windows XP (or above).</span></span> <span data-ttu-id="a02c3-109">El sistema debe tener un mínimo de 192 de RAM, 2 GB de espacio disponible en el disco duro y una pantalla de 1024 x 768 con 256 colores como mínimo.</span><span class="sxs-lookup"><span data-stu-id="a02c3-109">The system should have a minimum of 192 MB of RAM, 2 GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="a02c3-110">Además, la aplicación debe ejecutarse en ThreadX V5.0 o posterior.</span><span class="sxs-lookup"><span data-stu-id="a02c3-110">In addition, the application must be running on ThreadX V5.0 or later.</span></span>

<span data-ttu-id="a02c3-111">TraceX también requiere que esté instalado el marco de Microsoft .NET, una operación que el instalador de TraceX realiza automáticamente.</span><span class="sxs-lookup"><span data-stu-id="a02c3-111">TraceX also requires the Microsoft .NET framework be installed, which the TraceX installer does automatically.</span></span>

## <a name="tracex-constraints"></a><span data-ttu-id="a02c3-112">Restricciones de TraceX</span><span class="sxs-lookup"><span data-stu-id="a02c3-112">TraceX Constraints</span></span>

<span data-ttu-id="a02c3-113">TraceX tiene las siguientes restricciones:</span><span class="sxs-lookup"><span data-stu-id="a02c3-113">TraceX has the following constraints:</span></span>

- <span data-ttu-id="a02c3-114">Los archivos de TraceX se limitan a un máximo de 32 768 eventos (aproximadamente 1 MB).</span><span class="sxs-lookup"><span data-stu-id="a02c3-114">TraceX files are limited to a maximum of 32,768 events (roughly 1 MB ).</span></span>
- <span data-ttu-id="a02c3-115">El origen de la marca de tiempo debe tener una resolución razonable.</span><span class="sxs-lookup"><span data-stu-id="a02c3-115">The time-stamp source must have reasonable resolution.</span></span> <span data-ttu-id="a02c3-116">Si la resolución es demasiado baja, los eventos se superponen.</span><span class="sxs-lookup"><span data-stu-id="a02c3-116">If the resolution is too low, the events will overlap.</span></span> <span data-ttu-id="a02c3-117">Si la resolución es demasiado alta, existe la posibilidad de que haya intervalos largos entre eventos.</span><span class="sxs-lookup"><span data-stu-id="a02c3-117">If the resolution is too high, there is potential for long gaps between events.</span></span>
- <span data-ttu-id="a02c3-118">TraceX no puede medir con precisión los intervalos entre eventos mayores que el período del temporizador.</span><span class="sxs-lookup"><span data-stu-id="a02c3-118">TraceX cannot accurately measure intervals between events greater than the timer period.</span></span>
