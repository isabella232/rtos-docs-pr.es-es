---
title: 'Capítulo 1: Introducción a pila de host de Azure RTOS USBX'
description: En este capítulo se presenta la pila de host de USBX y se describen sus aplicaciones y ventajas.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a9fdd86d47bd4680409cc550c87bc6f456d146a9
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377057"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a><span data-ttu-id="113e3-103">Capítulo 1: Introducción a pila de host de Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="113e3-103">Chapter 1 - Introduction to Azure RTOS USBX Host Stack</span></span>

<span data-ttu-id="113e3-104">USBX es una pila USB que incorpora todas las características para aplicaciones con alto grado de inserción.</span><span class="sxs-lookup"><span data-stu-id="113e3-104">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="113e3-105">En este capítulo se presenta USBX y se describen sus aplicaciones y ventajas.</span><span class="sxs-lookup"><span data-stu-id="113e3-105">This chapter introduces USBX, describing its applications and benefits.</span></span>

## <a name="usbx-features"></a><span data-ttu-id="113e3-106">Características de USBX</span><span class="sxs-lookup"><span data-stu-id="113e3-106">USBX features</span></span>

<span data-ttu-id="113e3-107">USBX admite las tres especificaciones USB existentes: 1.1, 2.0 y OTG.</span><span class="sxs-lookup"><span data-stu-id="113e3-107">USBX support the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="113e3-108">Está diseñado para ser escalable y se adapta a las topologías USB simples con un solo dispositivo conectado, así como topologías complejas con varios dispositivos y concentradores en cascada.</span><span class="sxs-lookup"><span data-stu-id="113e3-108">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="113e3-109">USBX admite todos los tipos de transferencia de datos de los protocolos USB: control, masivo, interrupción e isocrónico.</span><span class="sxs-lookup"><span data-stu-id="113e3-109">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="113e3-110">USBX admite tanto el lado del host como el del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="113e3-110">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="113e3-111">Cada lado se compone de tres capas.</span><span class="sxs-lookup"><span data-stu-id="113e3-111">Each side is comprised of three layers.</span></span>

- <span data-ttu-id="113e3-112">Capa de controlador</span><span class="sxs-lookup"><span data-stu-id="113e3-112">Controller layer</span></span>
- <span data-ttu-id="113e3-113">Capa de pila</span><span class="sxs-lookup"><span data-stu-id="113e3-113">Stack layer</span></span>
- <span data-ttu-id="113e3-114">Capa de clase</span><span class="sxs-lookup"><span data-stu-id="113e3-114">Class layer</span></span>

<span data-ttu-id="113e3-115">La relación entre las capas USB es la siguiente.</span><span class="sxs-lookup"><span data-stu-id="113e3-115">The relationship between the USB layers is as follows.</span></span>

![Capas USB](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="113e3-117">Aspectos destacados del producto</span><span class="sxs-lookup"><span data-stu-id="113e3-117">Product Highlights</span></span>

- <span data-ttu-id="113e3-118">Soporte completo del procesador ThreadX</span><span class="sxs-lookup"><span data-stu-id="113e3-118">Complete ThreadX processor support</span></span>
- <span data-ttu-id="113e3-119">Sin regalías</span><span class="sxs-lookup"><span data-stu-id="113e3-119">No royalties</span></span>
- <span data-ttu-id="113e3-120">Código fuente ANSI C completo</span><span class="sxs-lookup"><span data-stu-id="113e3-120">Complete ANSI C source code</span></span>
- <span data-ttu-id="113e3-121">Rendimiento en tiempo real</span><span class="sxs-lookup"><span data-stu-id="113e3-121">Real-time performance</span></span>
- <span data-ttu-id="113e3-122">Soporte técnico con capacidad de respuesta</span><span class="sxs-lookup"><span data-stu-id="113e3-122">Responsive technical support</span></span>
- <span data-ttu-id="113e3-123">Compatibilidad con varios controladores de host</span><span class="sxs-lookup"><span data-stu-id="113e3-123">Multiple host controller support</span></span>
- <span data-ttu-id="113e3-124">Compatibilidad con varias clases</span><span class="sxs-lookup"><span data-stu-id="113e3-124">Multiple class support</span></span>
- <span data-ttu-id="113e3-125">Varias instancias de clase</span><span class="sxs-lookup"><span data-stu-id="113e3-125">Multiple class instances</span></span>
- <span data-ttu-id="113e3-126">Integración de clases con ThreadX, FileX y NetX</span><span class="sxs-lookup"><span data-stu-id="113e3-126">Integration of classes with ThreadX, FileX and NetX</span></span>
- <span data-ttu-id="113e3-127">Compatibilidad con dispositivos USB con varias configuraciones</span><span class="sxs-lookup"><span data-stu-id="113e3-127">Support for USB devices with multiple configuration</span></span>
- <span data-ttu-id="113e3-128">Compatibilidad con dispositivos compuestos USB</span><span class="sxs-lookup"><span data-stu-id="113e3-128">Support for USB composite devices</span></span>
- <span data-ttu-id="113e3-129">Compatibilidad con concentradores en cascada</span><span class="sxs-lookup"><span data-stu-id="113e3-129">Support for cascading hubs</span></span>
- <span data-ttu-id="113e3-130">Compatibilidad con la administración de energía USB</span><span class="sxs-lookup"><span data-stu-id="113e3-130">Support for USB power management</span></span>
- <span data-ttu-id="113e3-131">Compatibilidad con el OTG USB</span><span class="sxs-lookup"><span data-stu-id="113e3-131">Support for USB OTG</span></span>
- <span data-ttu-id="113e3-132">Exportación de eventos de seguimiento para TraceX</span><span class="sxs-lookup"><span data-stu-id="113e3-132">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="113e3-133">Servicios eficaces de USBX</span><span class="sxs-lookup"><span data-stu-id="113e3-133">Powerful Services of USBX</span></span>

### <a name="multiple-host-controller-support"></a><span data-ttu-id="113e3-134">Compatibilidad con varios controladores de host</span><span class="sxs-lookup"><span data-stu-id="113e3-134">Multiple Host Controller Support</span></span>

<span data-ttu-id="113e3-135">USBX puede admitir varios controladores de host USB que se ejecutan simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="113e3-135">USBX can support multiple USB host controllers running concurrently.</span></span> <span data-ttu-id="113e3-136">Esta característica permite a USBX admitir el estándar USB 2.0 con el esquema de compatibilidad con versiones anteriores asociado a la mayoría de los controladores de host USB 2.0 del mercado actual.</span><span class="sxs-lookup"><span data-stu-id="113e3-136">This feature allows USBX to support the USB 2.0 standard using the backward compatibility scheme associated with most USB 2.0 host controllers on the market today.</span></span>

### <a name="usb-software-scheduler"></a><span data-ttu-id="113e3-137">Programador de software USB</span><span class="sxs-lookup"><span data-stu-id="113e3-137">USB Software Scheduler</span></span>

<span data-ttu-id="113e3-138">USBX contiene un programador de software USB necesario para admitir controladores USB que no tienen procesamiento de la lista de hardware.</span><span class="sxs-lookup"><span data-stu-id="113e3-138">USBX contains a USB software scheduler necessary to support USB controllers that do not have hardware list processing.</span></span> <span data-ttu-id="113e3-139">El programador de software USBX organizará las transferencias USB con la frecuencia correcta de servicio y prioridad, y le indicará al controlador USB que ejecute cada transferencia.</span><span class="sxs-lookup"><span data-stu-id="113e3-139">The USBX software scheduler will organize USB transfers with the correct frequency of service and priority, and will instruct the USB controller to execute each transfer.</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="113e3-140">Compatibilidad completa con el marco de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="113e3-140">Complete USB Device Framework Support</span></span>

<span data-ttu-id="113e3-141">USBX puede admitir los dispositivos USB más exigentes, incluidas varias configuraciones, varias interfaces y varias configuraciones alternativas.</span><span class="sxs-lookup"><span data-stu-id="113e3-141">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="113e3-142">API fáciles de usar</span><span class="sxs-lookup"><span data-stu-id="113e3-142">Easy-To-Use APIs</span></span>

<span data-ttu-id="113e3-143">USBX proporciona la mejor pila USB con alto grado de inserción de una manera fácil de comprender y usar.</span><span class="sxs-lookup"><span data-stu-id="113e3-143">USBX provides the very best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="113e3-144">La API de USBX hace que los servicios sean intuitivos y coherentes.</span><span class="sxs-lookup"><span data-stu-id="113e3-144">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="113e3-145">Mediante el uso de las API de clase USBX proporcionadas, la aplicación de usuario no necesita comprender la complejidad de los protocolos USB.</span><span class="sxs-lookup"><span data-stu-id="113e3-145">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
