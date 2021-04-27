---
title: 'Capítulo 1: Introducción a BSD de Azure RTOS NetX Duo'
description: El contenedor de cumplimiento de la API de socket BSD es compatible con algunas de las llamadas API de socket BSD básicas, con algunas limitaciones, y usan primitivas de Azure RTOS NetX Duo debajo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814826"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="e8fa5-103">Capítulo 1: Introducción a BSD de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e8fa5-103">Chapter 1 - Introduction to Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="e8fa5-104">El contenedor de cumplimiento de la API de socket BSD es compatible con algunas de las llamadas API de socket BSD básicas, con algunas limitaciones, y usan primitivas de Azure RTOS NetX Duo debajo.</span><span class="sxs-lookup"><span data-stu-id="e8fa5-104">The BSD Socket API Compliancy Wrapper supports some of the basic BSD Socket API calls, with some limitations and utilizes Azure RTOS NetX Duo primitives underneath.</span></span>

## <a name="bsd-socket-api-compliancy-wrapper-source"></a><span data-ttu-id="e8fa5-105">Origen del contenedor de cumplimiento de la API de socket BSD</span><span class="sxs-lookup"><span data-stu-id="e8fa5-105">BSD Socket API Compliancy Wrapper Source</span></span>

<span data-ttu-id="e8fa5-106">El código fuente del contenedor está diseñado pensando en la sencillez y se compone de dos archivos, *nxd_bsd.h* y *nxd_bsd.c*.</span><span class="sxs-lookup"><span data-stu-id="e8fa5-106">The Wrapper source code is designed for simplicity and is comprised of two files, namely *nxd_bsd.h* and *nxd_bsd.c*.</span></span> <span data-ttu-id="e8fa5-107">El archivo *nxd_bsd.h* define todas las constantes y los prototipos de subrutinas del contenedor de la API de socket BSD necesarios, mientras que *nxd_bsd.c* contiene el código fuente de compatibilidad de la API de socket BSD real.</span><span class="sxs-lookup"><span data-stu-id="e8fa5-107">The *nxd_bsd.h* file defines all the necessary BSD Socket API wrapper constants and subroutine prototypes, while *nxd_bsd.c* contains the actual BSD Socket API compatibility source code.</span></span> <span data-ttu-id="e8fa5-108">Estos archivos de código fuente del contenedor son comunes a todos los paquetes de soporte de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="e8fa5-108">These Wrapper source files are common to all NetX Duo support packages.</span></span>

<span data-ttu-id="e8fa5-109">El paquete consta de:</span><span class="sxs-lookup"><span data-stu-id="e8fa5-109">The package consists of:</span></span>

- <span data-ttu-id="e8fa5-110">**nxd_bsd.c**: código fuente del contenedor</span><span class="sxs-lookup"><span data-stu-id="e8fa5-110">**nxd_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="e8fa5-111">**nxd_bsd.h**: archivo de encabezado principal</span><span class="sxs-lookup"><span data-stu-id="e8fa5-111">**nxd_bsd.h**: Main header file</span></span>

<span data-ttu-id="e8fa5-112">Programas de demostración de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e8fa5-112">Sample demo programs:</span></span>

- <span data-ttu-id="e8fa5-113">**bsd_demo_udp.c**: *demo con dos nodos UDP del mismo nivel (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="e8fa5-113">**bsd_demo_udp.c**: *Demo with two UDP peers (IPv4 only)*</span></span>
- <span data-ttu-id="e8fa5-114">**bsd_demo_tcp.c**: *demo con un solo cliente y servidor TCP*</span><span class="sxs-lookup"><span data-stu-id="e8fa5-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="e8fa5-115">**bsd_demo_raw.c**: *demo con dos nodos del mismo nivel sin procesar*</span><span class="sxs-lookup"><span data-stu-id="e8fa5-115">**bsd_demo_raw.c**: *Demo with two RAW peers*</span></span>