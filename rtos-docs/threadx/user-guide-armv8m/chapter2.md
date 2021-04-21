---
title: 'Capítulo 2: Instalación de la compatibilidad de ThreadX con ARMv8-M'
description: En este capítulo se explica cómo instalar y usar el código fuente de ThreadX para la arquitectura ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377536"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a><span data-ttu-id="b819a-103">Capítulo 2: Instalación de la compatibilidad de ThreadX con ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="b819a-103">Chapter 2  Installing ThreadX support for ARMv8-M</span></span>

<span data-ttu-id="b819a-104">Hay archivos de código fuente de ThreadX adicionales que admiten la arquitectura ARMv8-M.</span><span class="sxs-lookup"><span data-stu-id="b819a-104">There are additional ThreadX source code files to support the ARMv8-M architecture.</span></span>

<span data-ttu-id="b819a-105">Si ThreadX se va a ejecutar en modo seguro, no se necesitan estos archivos y API adicionales.</span><span class="sxs-lookup"><span data-stu-id="b819a-105">If ThreadX is to be run in secure mode, these additional files and APIs are not needed.</span></span> <span data-ttu-id="b819a-106">Para ejecutar ThreadX en modo seguro, defina el símbolo **TX_SECURE_EXECUTION** en la parte superior de **_tx_port.h_ *_ o en la línea de comandos o la configuración del proyecto. Asegúrese de definir* _TX_SECURE_EXECUTION** para todos los archivos de ensamblado y de c.</span><span class="sxs-lookup"><span data-stu-id="b819a-106">To run ThreadX in secure mode, define the symbol **TX_SECURE_EXECUTION** at the top of **_tx_port.h_*_ or on the command line or project settings. Ensure _\* TX_SECURE_EXECUTION*\* is defined for all c and assembly files.</span></span> <span data-ttu-id="b819a-107">ThreadX y la aplicación de usuario se ejecutarán en modo seguro.</span><span class="sxs-lookup"><span data-stu-id="b819a-107">ThreadX and the user application will execute in secure mode.</span></span>

<span data-ttu-id="b819a-108">Para ejecutar ThreadX y la aplicación de usuario en modo no seguro y admitir funciones seguras invocables no seguras, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b819a-108">To run ThreadX and the user application in non-secure mode and support non-secure callable secure functions, please do the following.</span></span>

<span data-ttu-id="b819a-109">Se debe agregar el archivo ***tx_thread_secure_stack.c*** a la aplicación segura.</span><span class="sxs-lookup"><span data-stu-id="b819a-109">The file ***tx_thread_secure_stack.c*** must be added to the secure application.</span></span>

<span data-ttu-id="b819a-110">Se deben agregar los siguientes archivos a la biblioteca ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b819a-110">The following files must be added to the ThreadX library.</span></span>

- <span data-ttu-id="b819a-111">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="b819a-111">***tx_secure_interface.h***</span></span>
- <span data-ttu-id="b819a-112">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="b819a-112">***txe_thread_secure_stack_allocate.c***</span></span>
- <span data-ttu-id="b819a-113">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="b819a-113">***txe_thread_secure_stack_free.c***</span></span>
- <span data-ttu-id="b819a-114">***tx_thread_secure_stack_allocate.s***</span><span class="sxs-lookup"><span data-stu-id="b819a-114">***tx_thread_secure_stack_allocate.s***</span></span>
- <span data-ttu-id="b819a-115">***tx_thread_secure_stack_free.s***</span><span class="sxs-lookup"><span data-stu-id="b819a-115">***tx_thread_secure_stack_free.s***</span></span>

<span data-ttu-id="b819a-116">Los dos archivos siguientes reemplazan a los archivos genéricos de la biblioteca ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b819a-116">The following two files replace the generic files in the ThreadX library.</span></span>

- <span data-ttu-id="b819a-117">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="b819a-117">***tx_thread_stack_error_handler.c***</span></span>
- <span data-ttu-id="b819a-118">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="b819a-118">***tx_thread_stack_error_notify.c***</span></span>

## <a name="additional-threadx-sources-for-armv8-m"></a><span data-ttu-id="b819a-119">Orígenes de ThreadX adicionales para ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="b819a-119">Additional ThreadX Sources for ARMv8-M</span></span>

<span data-ttu-id="b819a-120">A continuación se describen los archivos de ThreadX adicionales para la arquitectura TrustZone para ARMv8-M.</span><span class="sxs-lookup"><span data-stu-id="b819a-120">The additional ThreadX files for the ARMv8-M TrustZone architecture are described below.</span></span>

  | <span data-ttu-id="b819a-121">**Nombre de archivo**</span><span class="sxs-lookup"><span data-stu-id="b819a-121">**File Name**</span></span>                            | <span data-ttu-id="b819a-122">**Contents**</span><span class="sxs-lookup"><span data-stu-id="b819a-122">**Contents**</span></span>                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | <span data-ttu-id="b819a-123">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="b819a-123">***tx_secure_interface.h***</span></span>              | <span data-ttu-id="b819a-124">Archivo de inclusión que define las funciones ThreadX invocables no seguras.</span><span class="sxs-lookup"><span data-stu-id="b819a-124">Include file that defines the ThreadX non-secure callable functions.</span></span> |
  | <span data-ttu-id="b819a-125">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="b819a-125">***txe_thread_secure_stack_allocate.c***</span></span> |  <span data-ttu-id="b819a-126">Archivo de comprobación de errores de la API de asignación de pila segura.</span><span class="sxs-lookup"><span data-stu-id="b819a-126">Error-checking file for the secure stack allocate API.</span></span> |
  | <span data-ttu-id="b819a-127">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="b819a-127">***txe_thread_secure_stack_free.c***</span></span>     |  <span data-ttu-id="b819a-128">Archivo de comprobación de errores de la API gratuita de pila segura.</span><span class="sxs-lookup"><span data-stu-id="b819a-128">Error-checking file for the secure stack free API.</span></span> |
  | <span data-ttu-id="b819a-129">***tx_thread_secure_stack_allocate.s***</span><span class="sxs-lookup"><span data-stu-id="b819a-129">***tx_thread_secure_stack_allocate.s***</span></span>  |  <span data-ttu-id="b819a-130">Capa no segura para el servicio de asignación de pila segura.</span><span class="sxs-lookup"><span data-stu-id="b819a-130">Non-secure veneer for the secure stack allocate service.</span></span> |
  | <span data-ttu-id="b819a-131">***tx_thread_secure_stack_free.s***</span><span class="sxs-lookup"><span data-stu-id="b819a-131">***tx_thread_secure_stack_free.s***</span></span>      |  <span data-ttu-id="b819a-132">Capa no segura para el servicio gratuito de pila segura.</span><span class="sxs-lookup"><span data-stu-id="b819a-132">Non-secure veneer for the secure stack free service.</span></span> |
  | <span data-ttu-id="b819a-133">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="b819a-133">***tx_thread_stack_error_handler.c***</span></span>    |  <span data-ttu-id="b819a-134">Controlador de errores de pila de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="b819a-134">Handler for thread stack errors.</span></span> |
  | <span data-ttu-id="b819a-135">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="b819a-135">***tx_thread_stack_error_notify.c***</span></span>     |  <span data-ttu-id="b819a-136">Registra la devolución de llamada de notificación para controlar los errores de pila de subprocesos.</span><span class="sxs-lookup"><span data-stu-id="b819a-136">Register notification callback for handling thread stack errors.</span></span> |
