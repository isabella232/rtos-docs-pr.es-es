---
title: Guía de usuario de GUIX Studio
description: En esta guía se proporciona información exhaustiva sobre GUIX Studio, el entorno de desarrollo rápido de interfaz de usuario basado en Microsoft Windows diseñado específicamente para la biblioteca en tiempo de ejecución de GUIX de Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6a5d628581d4c6b44ff093bac45790d6e2755349
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815501"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a><span data-ttu-id="d47e0-103">Capítulo 1: Introducción a Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="d47e0-103">Chapter 1: Introduction to Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="d47e0-104">Azure RTOS GUIX Studio es un entorno de desarrollo de interfaz de usuario rápido basado en Microsoft Windows diseñado específicamente para la biblioteca en tiempo de ejecución de GUIX de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d47e0-104">Azure RTOS GUIX Studio is a Microsoft Windows-based rapid UI development environment specifically designed for the GUIX runtime library from Microsoft.</span></span>

<span data-ttu-id="d47e0-105">Los desarrolladores de UI integradas pueden usar el diseñador de pantalla WYSIWYG de GUIX Studio para crear y actualizar rápidamente interfaces de usuario integradas utilizando el entorno de ejecución de GUIX.</span><span class="sxs-lookup"><span data-stu-id="d47e0-105">Embedded UI Developers can utilize the GUIX Studio WYSIWYG screen designer to quickly create and update their embedded UI using the GUIX run-time environment.</span></span> <span data-ttu-id="d47e0-106">Los diseños de GUIX Studio se guardan y mantienen en un archivo del proyecto de GUIX Studio, que tiene la extensión .gxp.</span><span class="sxs-lookup"><span data-stu-id="d47e0-106">GUIX Studio designs are saved and maintained in a GUIX Studio project file, which has the extension .gxp.</span></span> <span data-ttu-id="d47e0-107">Cuando el diseño está listo para su ejecución en el destino, Guix Studio genera código de C que contiene toda la información y el código de la interfaz de usuario que se necesitan.</span><span class="sxs-lookup"><span data-stu-id="d47e0-107">When your design is ready for execution on the target, GUIX Studio generates C code that contains all the necessary UI information and code.</span></span>

## <a name="guix-studio-requirements"></a><span data-ttu-id="d47e0-108">Requisitos de GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="d47e0-108">GUIX Studio Requirements</span></span>

<span data-ttu-id="d47e0-109">Para funcionar correctamente, GUIX Studio de Microsoft requiere *Windows XP* (o superior).</span><span class="sxs-lookup"><span data-stu-id="d47e0-109">In order to function properly, Microsoft's GUIX Studio requires *Windows XP* (or above).</span></span> <span data-ttu-id="d47e0-110">El sistema debe tener un mínimo de 200 de RAM, 2 B de espacio disponible en el disco duro y una pantalla de 1024 x 768 con 256 colores como mínimo.</span><span class="sxs-lookup"><span data-stu-id="d47e0-110">The system should have a minimum of 200MB of RAM, 2GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="d47e0-111">Además, la aplicación insertada se debe ejecutar en *ThreadX/GUIX v6.0* o posterior.</span><span class="sxs-lookup"><span data-stu-id="d47e0-111">In addition, the embedded application must be running on *ThreadX/GUIX V6.0* or later.</span></span>

<span data-ttu-id="d47e0-112">Si desea poder compilar y ejecutar la aplicación de UI integrada como un ejecutable independiente de Microsoft Windows, también necesita un compilador o un entorno de compilación que pueda compilar el código fuente de C para convertirse en un producto ejecutable de Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="d47e0-112">If you would like to be able to build and run the embedded UI application as a stand-alone Microsoft Windows executable, you will also need a compiler or build environment capable of compiling C source code to produce a Microsoft Windows executable.</span></span> <span data-ttu-id="d47e0-113">El paquete de evaluación incluido con GUIX Studio también incluye archivos de proyecto y soluciones compatibles con Visual Studio 2019 para cada una de las aplicaciones de ejemplo proporcionadas.</span><span class="sxs-lookup"><span data-stu-id="d47e0-113">The evaluation package included with GUIX Studio also includes Visual Studio 2019 compatible project files and solutions for each of the provided example applications.</span></span> <span data-ttu-id="d47e0-114">Si usa un compilador diferente, deberá crear sus propios archivos de proyecto, generar archivos para crear sus aplicaciones de ejemplo o ponerse en contacto con el soporte técnico en https://aka.ms/azrtos-support.</span><span class="sxs-lookup"><span data-stu-id="d47e0-114">If you are using a different compiler, you will need to create your own project files or make files for the purposes of building your example applications, or contact support at https://aka.ms/azrtos-support.</span></span>

## <a name="guix-studio-constraints"></a><span data-ttu-id="d47e0-115">Restricciones de GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="d47e0-115">GUIX Studio Constraints</span></span>

<span data-ttu-id="d47e0-116">La herramienta de diseño de UI de GUIX Studio tiene varias restricciones, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="d47e0-116">The GUIX Studio UI design tool has several constraints, as follows:</span></span>

- <span data-ttu-id="d47e0-117">Un máximo de 4 publicaciones por proyecto.</span><span class="sxs-lookup"><span data-stu-id="d47e0-117">A maximum of 4 displays per project.</span></span>
- <span data-ttu-id="d47e0-118">Un máximo de 100 000 widgets por proyecto de GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="d47e0-118">A maximum of 100,000 widgets per GUIX Studio project.</span></span>
- <span data-ttu-id="d47e0-119">Un máximo de 100 000 recursos distintos, por ejemplo, colores, fuentes, mapas de píxeles, cadenas, etc.</span><span class="sxs-lookup"><span data-stu-id="d47e0-119">A maximum of 100,000 distinct resources, e.g., colors, fonts, pixelmaps, strings, etc.</span></span>