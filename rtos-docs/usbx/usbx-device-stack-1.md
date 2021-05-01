---
title: 'Capítulo 1: Introducción a pila de dispositivos de Azure RTOS USBX'
description: USBX es una pila USB que incorpora todas las características para aplicaciones con alto grado de inserción. En este capítulo se presenta USBX y se describen sus ventajas y aplicación.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8b1e08130d4531fd82629378761cd5b1752f0a07
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550293"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a><span data-ttu-id="99f2e-104">Capítulo 1: Introducción a pila de dispositivos de Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="99f2e-104">Chapter 1 - Introduction to Azure RTOS USBX Device Stack</span></span>

<span data-ttu-id="99f2e-105">USBX es una pila USB que incorpora todas las características para aplicaciones con alto grado de inserción.</span><span class="sxs-lookup"><span data-stu-id="99f2e-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="99f2e-106">En este capítulo se presenta USBX y se describen sus aplicaciones y ventajas.</span><span class="sxs-lookup"><span data-stu-id="99f2e-106">This chapter introduces USBX, describing its applications and benefits</span></span> 

## <a name="usbx-features"></a><span data-ttu-id="99f2e-107">Características de USBX</span><span class="sxs-lookup"><span data-stu-id="99f2e-107">USBX features</span></span>

<span data-ttu-id="99f2e-108">USBX admite las tres especificaciones USB existentes: 1.1, 2.0 y OTG.</span><span class="sxs-lookup"><span data-stu-id="99f2e-108">USBX supports the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="99f2e-109">Está diseñado para ser escalable y se adapta a las topologías USB simples con un solo dispositivo conectado, así como topologías complejas con varios dispositivos y concentradores en cascada.</span><span class="sxs-lookup"><span data-stu-id="99f2e-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="99f2e-110">USBX admite todos los tipos de transferencia de datos de los protocolos USB: control, masivo, interrupción e isocrónico.</span><span class="sxs-lookup"><span data-stu-id="99f2e-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="99f2e-111">USBX admite tanto el lado del host como el del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="99f2e-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="99f2e-112">Cada lado se compone de tres capas.</span><span class="sxs-lookup"><span data-stu-id="99f2e-112">Each side is composed of three layers.</span></span>

- <span data-ttu-id="99f2e-113">Capa de controlador</span><span class="sxs-lookup"><span data-stu-id="99f2e-113">Controller layer</span></span>
- <span data-ttu-id="99f2e-114">Capa de pila</span><span class="sxs-lookup"><span data-stu-id="99f2e-114">Stack layer</span></span>
- <span data-ttu-id="99f2e-115">Capa de clase</span><span class="sxs-lookup"><span data-stu-id="99f2e-115">Class layer</span></span>

<span data-ttu-id="99f2e-116">La relación entre las capas USB es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="99f2e-116">The relationship between the USB layers is as follows:</span></span>

![Capas USB](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="99f2e-118">Aspectos destacados del producto</span><span class="sxs-lookup"><span data-stu-id="99f2e-118">Product Highlights</span></span>

- <span data-ttu-id="99f2e-119">Soporte completo del procesador ThreadX</span><span class="sxs-lookup"><span data-stu-id="99f2e-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="99f2e-120">Sin regalías</span><span class="sxs-lookup"><span data-stu-id="99f2e-120">No royalties</span></span>
- <span data-ttu-id="99f2e-121">Código fuente ANSI C completo</span><span class="sxs-lookup"><span data-stu-id="99f2e-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="99f2e-122">Rendimiento en tiempo real</span><span class="sxs-lookup"><span data-stu-id="99f2e-122">Real-time performance</span></span>
- <span data-ttu-id="99f2e-123">Soporte técnico con capacidad de respuesta</span><span class="sxs-lookup"><span data-stu-id="99f2e-123">Responsive technical support</span></span>
- <span data-ttu-id="99f2e-124">Compatibilidad con varias clases</span><span class="sxs-lookup"><span data-stu-id="99f2e-124">Multiple class support</span></span>
- <span data-ttu-id="99f2e-125">Varias instancias de clase</span><span class="sxs-lookup"><span data-stu-id="99f2e-125">Multiple class instances</span></span>
- <span data-ttu-id="99f2e-126">Integración de clases con ThreadX, FileX y NetX</span><span class="sxs-lookup"><span data-stu-id="99f2e-126">Integration of classes with ThreadX, FileX, and NetX</span></span>
- <span data-ttu-id="99f2e-127">Compatibilidad con dispositivos USB con varias configuraciones</span><span class="sxs-lookup"><span data-stu-id="99f2e-127">Support for USB devices with multiple configurations</span></span>
- <span data-ttu-id="99f2e-128">Compatibilidad con dispositivos compuestos USB</span><span class="sxs-lookup"><span data-stu-id="99f2e-128">Support for USB composite devices</span></span>
- <span data-ttu-id="99f2e-129">Compatibilidad con la administración de energía USB</span><span class="sxs-lookup"><span data-stu-id="99f2e-129">Support for USB power management</span></span>
- <span data-ttu-id="99f2e-130">Compatibilidad con el OTG USB</span><span class="sxs-lookup"><span data-stu-id="99f2e-130">Support for USB OTG</span></span>
- <span data-ttu-id="99f2e-131">Exportación de eventos de seguimiento para TraceX</span><span class="sxs-lookup"><span data-stu-id="99f2e-131">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="99f2e-132">Servicios eficaces de USBX</span><span class="sxs-lookup"><span data-stu-id="99f2e-132">Powerful Services of USBX</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="99f2e-133">Compatibilidad completa con el marco de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="99f2e-133">Complete USB Device Framework Support</span></span>

<span data-ttu-id="99f2e-134">USBX puede admitir los dispositivos USB más exigentes, incluidas varias configuraciones, varias interfaces y varias configuraciones alternativas.</span><span class="sxs-lookup"><span data-stu-id="99f2e-134">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="99f2e-135">API fáciles de usar</span><span class="sxs-lookup"><span data-stu-id="99f2e-135">Easy-To-Use APIs</span></span>

<span data-ttu-id="99f2e-136">USBX proporciona la mejor pila USB con alto grado de inserción de una manera fácil de comprender y usar.</span><span class="sxs-lookup"><span data-stu-id="99f2e-136">USBX provides the best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="99f2e-137">La API de USBX hace que los servicios sean intuitivos y coherentes.</span><span class="sxs-lookup"><span data-stu-id="99f2e-137">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="99f2e-138">Mediante el uso de las API de clase USBX proporcionadas, la aplicación de usuario no necesita comprender la complejidad de los protocolos USB.</span><span class="sxs-lookup"><span data-stu-id="99f2e-138">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
