---
title: ¿Qué es Microsoft Azure RTOS?
description: Azure RTOS es un sistema operativo en tiempo real (RTOS) para dispositivos IoT y perimetrales con tecnología de microcontroladores (MCU).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3b1c63135f6069652d7f66fc976b9d770a4dfeb2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815118"
---
# <a name="what-is-microsoft-azure-rtos"></a><span data-ttu-id="10ff5-103">¿Qué es Microsoft Azure RTOS?</span><span class="sxs-lookup"><span data-stu-id="10ff5-103">What is Microsoft Azure RTOS</span></span>

<span data-ttu-id="10ff5-104">Azure RTOS es un sistema operativo en tiempo real (RTOS) para dispositivos IoT y perimetrales con tecnología de microcontroladores (MCU).</span><span class="sxs-lookup"><span data-stu-id="10ff5-104">Azure RTOS is a real time operating system (RTOS) for IoT and edge devices powered by microcontroller units (MCUs).</span></span> <span data-ttu-id="10ff5-105">Azure RTOS está diseñado para admitir la mayoría de los dispositivos altamente restringidos (con batería y con menos de 64 kB de memoria flash).</span><span class="sxs-lookup"><span data-stu-id="10ff5-105">Azure RTOS is designed to support most highly constrained devices (battery powered and having less than 64 KB of flash memory).</span></span>
 
<span data-ttu-id="10ff5-106">Azure RTOS está certificado previamente para una amplia variedad de estándares de seguridad.</span><span class="sxs-lookup"><span data-stu-id="10ff5-106">Azure RTOS is pre-certified for a variety of safety standards.</span></span> <span data-ttu-id="10ff5-107">Entre ellas se incluyen las certificaciones IEC 61508 SIL 4, IEC 62304 clase C e ISO 26262 ASIL D.</span><span class="sxs-lookup"><span data-stu-id="10ff5-107">These include the IEC 61508 SIL 4, IEC 62304 Class C, and ISO 26262 ASIL D certifications.</span></span> <span data-ttu-id="10ff5-108">Azure RTOS ThreadX también tiene la certificación DO-178.</span><span class="sxs-lookup"><span data-stu-id="10ff5-108">Azure RTOS ThreadX is also DO-178 certified.</span></span>

<span data-ttu-id="10ff5-109">Azure RTOS proporciona un entorno certificado de seguridad de criterios comunes de EAL4 +, incluida la seguridad de la capa de IP completa a través de IPsec y la seguridad de la capa de socket a través de TLS y DTLS.</span><span class="sxs-lookup"><span data-stu-id="10ff5-109">Azure RTOS provides an EAL4+ Common Criteria security certified environment, including full IP layer security via IPsec and socket layer security via TLS and DTLS.</span></span> <span data-ttu-id="10ff5-110">Nuestra biblioteca de criptografía de software ha logrado la certificación FIPS 140-2.</span><span class="sxs-lookup"><span data-stu-id="10ff5-110">Our software crypto library has achieved FIPS 140-2 certification.</span></span> <span data-ttu-id="10ff5-111">También aprovechamos las funcionalidades criptográficas de hardware, la protección de memoria a través de módulos de ThreadX y la compatibilidad con las características de seguridad de TrustZone ARMv8-M de ARM.</span><span class="sxs-lookup"><span data-stu-id="10ff5-111">We also leverage hardware cryptographic capabilities, memory protection via ThreadX MODULES, and support for ARM's TrustZone ARMv8-M security features.</span></span>

## <a name="components-of-azure-rtos"></a><span data-ttu-id="10ff5-112">Componentes de Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="10ff5-112">Components of Azure RTOS</span></span>

<span data-ttu-id="10ff5-113">La plataforma Azure RTOS es la colección de soluciones en tiempo de ejecución, entre las que se incluyen Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo y Azure RTOS USBX.</span><span class="sxs-lookup"><span data-stu-id="10ff5-113">The Azure RTOS platform is the collection of run-time solutions including Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo, and Azure RTOS USBX.</span></span>

### <a name="azure-rtos-threadx"></a><span data-ttu-id="10ff5-114">Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="10ff5-114">Azure RTOS ThreadX</span></span>

<span data-ttu-id="10ff5-115">Azure RTOS ThreadX es un sistema operativo en tiempo real (RTOS) avanzado, diseñado específicamente para aplicaciones profundamente insertadas.</span><span class="sxs-lookup"><span data-stu-id="10ff5-115">Azure RTOS ThreadX is an advanced Real-Time Operating System (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="10ff5-116">Entre las múltiples ventajas que ofrece Azure RTOS ThreadX se encuentran las funciones avanzadas de programación, el envío de mensajes, la administración de interrupciones y los servicios de mensajería.</span><span class="sxs-lookup"><span data-stu-id="10ff5-116">Among the multiple benefits Azure RTOS ThreadX provides are advanced scheduling facilities, message passing, interrupt management, and messaging services.</span></span> <span data-ttu-id="10ff5-117">Azure RTOS ThreadX tiene muchas características avanzadas, entre las que se incluyen la arquitectura picokernel, la programación de umbral de prioridad, el encadenamiento de eventos y un conjunto completo de servicios del sistema.</span><span class="sxs-lookup"><span data-stu-id="10ff5-117">Azure RTOS ThreadX has many advanced features, including its picokernel architecture, preemption-threshold scheduling, event-chaining, and a rich set of system services.</span></span>

### <a name="azure-rtos-filex"></a><span data-ttu-id="10ff5-118">Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="10ff5-118">Azure RTOS FileX</span></span>

<span data-ttu-id="10ff5-119">Azure RTOS FileX es un sistema de archivos compatible con FAT de alto rendimiento.</span><span class="sxs-lookup"><span data-stu-id="10ff5-119">Azure RTOS FileX is a high-performance FAT-compatible file system.</span></span> <span data-ttu-id="10ff5-120">Está totalmente integrado con Azure RTOS ThreadX y está disponible para todos los procesadores compatibles.</span><span class="sxs-lookup"><span data-stu-id="10ff5-120">It is fully integrated with Azure RTOS ThreadX and is available for all supported processors.</span></span> <span data-ttu-id="10ff5-121">Al igual que Azure RTOS ThreadX, Azure RTOS FileX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las actuales aplicaciones profundamente insertadas, que requieren operaciones de archivos.</span><span class="sxs-lookup"><span data-stu-id="10ff5-121">Like Azure RTOS ThreadX, Azure RTOS FileX is designed to have a small footprint and high performance, making it ideal for today's deeply embedded applications that require file operations.</span></span> <span data-ttu-id="10ff5-122">Azure RTOS FileX admite la mayoría de los soportes físicos, como el disco RAM, Azure RTOS USBX, tarjeta SD y memorias Flash NAND/NOR a través de Azure RTO LevelX.</span><span class="sxs-lookup"><span data-stu-id="10ff5-122">Azure RTOS FileX supports most physical media, including RAM disk, USBX, SD CARD, and NAND/NOR flash memories via Azure RTOS LevelX.</span></span>

### <a name="azure-rtos-guix"></a><span data-ttu-id="10ff5-123">Azure RTO GUIX</span><span class="sxs-lookup"><span data-stu-id="10ff5-123">Azure RTOS GUIX</span></span>

<span data-ttu-id="10ff5-124">Azure RTOS GUIX es un paquete de interfaz gráfica de usuario de calidad profesional creado para satisfacer las necesidades de los desarrolladores de sistemas insertados.</span><span class="sxs-lookup"><span data-stu-id="10ff5-124">Azure RTOS GUIX is a professional quality graphical user interface package, created to meet the needs of embedded systems developers.</span></span> <span data-ttu-id="10ff5-125">A diferencia de las alternativas, Azure RTOS GUIX es pequeño, rápido y fácil de migrar a prácticamente cualquier configuración de hardware capaz de admitir la salida gráfica.</span><span class="sxs-lookup"><span data-stu-id="10ff5-125">Unlike the alternatives, Azure RTOS GUIX is small, fast, and easily ported to virtually any hardware configuration capable of supporting graphical output.</span></span> <span data-ttu-id="10ff5-126">Azure RTOS GUIX también ofrece un atractivo visual excepcional y una API intuitiva y potente para el desarrollo de interfaces de usuario a nivel de aplicación.</span><span class="sxs-lookup"><span data-stu-id="10ff5-126">Azure RTOS GUIX also delivers exceptional visual appeal and an intuitive and powerful API for application-level user interface development.</span></span>

### <a name="azure-rtos-netx"></a><span data-ttu-id="10ff5-127">Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="10ff5-127">Azure RTOS NetX</span></span>

<span data-ttu-id="10ff5-128">Azure RTOS NetX es una implementación de alto rendimiento de estándares de protocolos TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="10ff5-128">Azure RTOS NetX is a high-performance implementation of TCP/IP protocol standards.</span></span> <span data-ttu-id="10ff5-129">Está totalmente integrado con Azure RTOS ThreadX y está disponible para todos los procesadores compatibles.</span><span class="sxs-lookup"><span data-stu-id="10ff5-129">It is fully integrated with Azure RTOS ThreadX, and is available for all supported processors.</span></span> <span data-ttu-id="10ff5-130">Azure RTOS NetX tiene una arquitectura Piconet exclusiva.</span><span class="sxs-lookup"><span data-stu-id="10ff5-130">Azure RTOS NetX has a unique Piconet architecture.</span></span> <span data-ttu-id="10ff5-131">Combinado con una API de copia de cero, lo convierte en un ajuste perfecto para las aplicaciones profundamente incrustadas de hoy en día que requieren conectividad de red.</span><span class="sxs-lookup"><span data-stu-id="10ff5-131">Combined with a zero-copy API, it makes it a perfect fit for today's deeply embedded applications that require network connectivity.</span></span>

### <a name="azure-rtos-netx-duo"></a><span data-ttu-id="10ff5-132">Azure RTO NetX Duo</span><span class="sxs-lookup"><span data-stu-id="10ff5-132">Azure RTOS NetX Duo</span></span>

<span data-ttu-id="10ff5-133">Azure RTOS NetX Duo es una pila de red TCP/IP avanzada y de nivel industrial diseñada específicamente para aplicaciones de IoT y en tiempo real insertadas.</span><span class="sxs-lookup"><span data-stu-id="10ff5-133">Azure RTOS NetX Duo is an advanced, Industrial Grade TCP/IP network stacks designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="10ff5-134">Azure RTOS NetX Duo es una pila de red IPv4 e IPv6 dual, mientras que NetX es la pila de red IPv4 original, esencialmente un subconjunto de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="10ff5-134">Azure RTOS NetX Duo is a dual IPv4 and IPv6 network stack, while NetX is the original IPv4 network stack, essentially a subset of Azure RTOS NetX Duo.</span></span>

### <a name="azure-rtos-usbx"></a><span data-ttu-id="10ff5-135">Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="10ff5-135">Azure RTOS USBX</span></span>

<span data-ttu-id="10ff5-136">Azure RTOS USBX es un host USB de alto rendimiento, un dispositivo y una pila insertada "on-the-go" (OTG).</span><span class="sxs-lookup"><span data-stu-id="10ff5-136">Azure RTOS USBX is a high-performance USB host, device, and On-The-Go (OTG) embedded stack.</span></span> <span data-ttu-id="10ff5-137">Está totalmente integrado con ThreadX y está disponible para todos los procesadores compatibles con Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="10ff5-137">It is fully integrated with ThreadX and is available for all Azure RTOS ThreadX supported processors.</span></span> <span data-ttu-id="10ff5-138">Al igual que Azure RTOS ThreadX, Azure RTOS USBX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las aplicaciones profundamente insertadas, que requieren una interfaz con dispositivos USB.</span><span class="sxs-lookup"><span data-stu-id="10ff5-138">Like Azure RTOS ThreadX, Azure RTOS USBX is designed to have a small footprint and high performance, making it ideal for deeply embedded applications that require an interface with USB devices.</span></span>

### <a name="windows-tools"></a><span data-ttu-id="10ff5-139">Herramientas de Windows</span><span class="sxs-lookup"><span data-stu-id="10ff5-139">Windows tools</span></span>

<span data-ttu-id="10ff5-140">Azure RTOS GUIX Studio proporciona un entorno de diseño de aplicaciones GUI completo, lo que facilita la creación y el mantenimiento de todos los elementos gráficos de la GUI de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="10ff5-140">Azure RTOS GUIX Studio provides a complete GUI application design environment, facilitating the creation and maintenance of all graphical elements in the application's GUI.</span></span> <span data-ttu-id="10ff5-141">Azure RTOS GUIX Studio genera automáticamente un código de C compatible con la biblioteca de Azure RTOS GUIX, listo para compilarse y ejecutarse en el destino.</span><span class="sxs-lookup"><span data-stu-id="10ff5-141">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span>

<span data-ttu-id="10ff5-142">Azure RTOS TraceX es la herramienta de análisis basada en host que proporciona a los desarrolladores una vista gráfica de los eventos del sistema en tiempo real y les permite visualizar y comprender mejor el comportamiento de sus sistemas en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="10ff5-142">Azure RTOS TraceX is a host-based analysis tool that provides developers with a graphical view of real-time system events and enables them to visualize and better understand the behavior of their real-time systems.</span></span>

## <a name="in-the-context-of-azure-iot"></a><span data-ttu-id="10ff5-143">En el contexto de Azure IoT</span><span class="sxs-lookup"><span data-stu-id="10ff5-143">In the context of Azure IoT</span></span>

<span data-ttu-id="10ff5-144">Además de conectarse directamente a Azure IoT o conectarse indirectamente a través de Azure IoT Edge, Azure RTOS también está disponible en dispositivos Azure Sphere.</span><span class="sxs-lookup"><span data-stu-id="10ff5-144">In addition to directly connecting to Azure IoT or indirectly connecting through Azure IoT Edge, Azure RTOS is also available on Azure Sphere devices.</span></span> <span data-ttu-id="10ff5-145">La combinación de Azure RTOS y Azure Sphere reúne el mejor procesamiento en tiempo real y la mejor seguridad en un solo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="10ff5-145">The combination of Azure RTOS and Azure Sphere bring best-of-class real-time processing and security together in one device.</span></span>