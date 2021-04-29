---
title: 'Capítulo 1: Introducción a Azure RTOS NetX BSD'
description: El contenedor de cumplimiento de la API de sockets de Azure RTOS NetX BSD es compatible con algunas de las llamadas API de sockets de BSD básicas, con algunas limitaciones, y usan primitivas de NetX debajo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814458"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a><span data-ttu-id="26c9c-103">Capítulo 1: Introducción a Azure RTOS NetX BSD</span><span class="sxs-lookup"><span data-stu-id="26c9c-103">Chapter 1 - Introduction to Azure RTOS NetX BSD</span></span>

<span data-ttu-id="26c9c-104">El contenedor de cumplimiento de la API de sockets de NetX BSD es compatible con algunas de las llamadas API de sockets de BSD básicas, con algunas limitaciones, y usan primitivas de NetX debajo.</span><span class="sxs-lookup"><span data-stu-id="26c9c-104">The NetX BSD Sockets API Compliancy Wrapper supports some of the basic BSD Sockets API calls with some limitations and utilizes NetX primitives underneath.</span></span> <span data-ttu-id="26c9c-105">Esta capa de API de sockets de BSD debe funcionar igual de rápido o ligeramente más rápido que las implementaciones de BSD típicas, ya que este contenedor emplea primitivas de NetX internas y omite la comprobación básica de errores de NetX.</span><span class="sxs-lookup"><span data-stu-id="26c9c-105">This BSD Sockets API compatibility layer should perform as fast or slightly faster than typical BSD implementations, since this Wrapper utilizes internal NetX primitives and bypasses basic NetX error checking.</span></span>

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a><span data-ttu-id="26c9c-106">Origen del contenedor de cumplimiento de la API de sockets de BSD</span><span class="sxs-lookup"><span data-stu-id="26c9c-106">BSD Sockets API Compliancy Wrapper Source</span></span>

<span data-ttu-id="26c9c-107">El código fuente del contenedor de está diseñado pensando en la sencillez y solo consta de dos archivos, *nx_bsd.c* y *nx_bsd.c*.</span><span class="sxs-lookup"><span data-stu-id="26c9c-107">The BSD Wrapper source code is designed for simplicity and is comprised of only two files, *nx_bsd.h* and *nx_bsd.c*.</span></span> <span data-ttu-id="26c9c-108">El archivo *nx_bsd.h* define todas las constantes del contenedor de la API de sockets de BSD y los prototipos de subrutinas necesarios, mientras que *nx_bsd.c* contiene el código fuente de compatibilidad de la API de sockets de BSD real.</span><span class="sxs-lookup"><span data-stu-id="26c9c-108">The *nx_bsd.h* file defines all the necessary BSD Sockets API Wrapper constants and subroutine prototypes, while *nx_bsd.c* contains the actual BSD Sockets API compatibility source code.</span></span> <span data-ttu-id="26c9c-109">Estos archivos de origen del contenedor de BSD son comunes a todos los paquetes de soporte de NetX.</span><span class="sxs-lookup"><span data-stu-id="26c9c-109">These BSD Wrapper source files are common to all NetX support packages.</span></span>

<span data-ttu-id="26c9c-110">El paquete consta de:</span><span class="sxs-lookup"><span data-stu-id="26c9c-110">The package consists of:</span></span>

- <span data-ttu-id="26c9c-111">**nxd_bsd.c**: código fuente del contenedor</span><span class="sxs-lookup"><span data-stu-id="26c9c-111">**nx_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="26c9c-112">**nxd_bsd.h**: archivo de encabezado principal</span><span class="sxs-lookup"><span data-stu-id="26c9c-112">**nx_bsd.h**: Main header file</span></span>

<span data-ttu-id="26c9c-113">Programas de demostración de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="26c9c-113">Sample demo programs:</span></span>

- <span data-ttu-id="26c9c-114">**bsd_demo_tcp.c**: *demo con un solo cliente y servidor TCP*</span><span class="sxs-lookup"><span data-stu-id="26c9c-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="26c9c-115">**bsd_demo_udp. c**: *demo con dos clientes UDP y un servidor UDP*</span><span class="sxs-lookup"><span data-stu-id="26c9c-115">**bsd_demo_udp.c**: *Demo with two UDP clients and a UDP server*</span></span>
