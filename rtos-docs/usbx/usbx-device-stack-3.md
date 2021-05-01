---
title: 'Capítulo 3: Componentes funcionales de la pila del dispositivo USBX'
description: Este capítulo contiene una descripción de la pila de dispositivos USB insertada de USBX de alto rendimiento desde una perspectiva funcional.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dc57f3e0f6aa6731f4aaedee8169313ca7276cff
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082207"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a><span data-ttu-id="21861-103">Capítulo 3: Componentes funcionales de la pila del dispositivo USBX</span><span class="sxs-lookup"><span data-stu-id="21861-103">Chapter 3 - Functional Components of USBX Device Stack</span></span>

<span data-ttu-id="21861-104">Este capítulo contiene una descripción de la pila de dispositivos USB insertada de USBX de alto rendimiento desde una perspectiva funcional.</span><span class="sxs-lookup"><span data-stu-id="21861-104">This chapter contains a description of the high performance USBX embedded USB device stack from a functional perspective.</span></span>

## <a name="execution-overview"></a><span data-ttu-id="21861-105">Información general sobre la ejecución</span><span class="sxs-lookup"><span data-stu-id="21861-105">Execution Overview</span></span>

<span data-ttu-id="21861-106">USBX para el dispositivo se compone de varios componentes.</span><span class="sxs-lookup"><span data-stu-id="21861-106">USBX for the device is composed of several components.</span></span>

- <span data-ttu-id="21861-107">Inicialización</span><span class="sxs-lookup"><span data-stu-id="21861-107">Initialization</span></span>
- <span data-ttu-id="21861-108">Llamadas a la interfaz de la aplicación</span><span class="sxs-lookup"><span data-stu-id="21861-108">Application interface calls</span></span>
- <span data-ttu-id="21861-109">Clases de dispositivo</span><span class="sxs-lookup"><span data-stu-id="21861-109">Device Classes</span></span>
- <span data-ttu-id="21861-110">Pila de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="21861-110">USB Device Stack</span></span>
- <span data-ttu-id="21861-111">Controladora de dispositivos</span><span class="sxs-lookup"><span data-stu-id="21861-111">Device controller</span></span>
- <span data-ttu-id="21861-112">Administrador de VBUS</span><span class="sxs-lookup"><span data-stu-id="21861-112">VBUS manager</span></span>

<span data-ttu-id="21861-113">En el siguiente diagrama se ilustra la pila de dispositivos USBX.</span><span class="sxs-lookup"><span data-stu-id="21861-113">The following diagram illustrates the USBX Device stack.</span></span>

![Pila de dispositivos USBX](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a><span data-ttu-id="21861-115">Inicialización</span><span class="sxs-lookup"><span data-stu-id="21861-115">Initialization</span></span>

<span data-ttu-id="21861-116">Para activar USBX, se debe llamar a la función ***ux_system_initialize***.</span><span class="sxs-lookup"><span data-stu-id="21861-116">In order to activate USBX, the function ***ux_system_initialize*** must be called.</span></span> <span data-ttu-id="21861-117">Esta función inicializa los recursos de memoria de USBX.</span><span class="sxs-lookup"><span data-stu-id="21861-117">This function initializes the memory resources of USBX.</span></span>

<span data-ttu-id="21861-118">Para activar las instalaciones del dispositivo USBX, se debe llamar a la función ***ux_device_stack_initialize***.</span><span class="sxs-lookup"><span data-stu-id="21861-118">In order to activate USBX device facilities, the function ***ux_device_stack_initialize*** must be called.</span></span> <span data-ttu-id="21861-119">Esta función, a su vez, inicializará todos los recursos usados por la pila de dispositivos USBX, como subprocesos de ThreadX, exclusiones mutuas y semáforos.</span><span class="sxs-lookup"><span data-stu-id="21861-119">This function will in turn initialize all the resources used by the USBX device stack such as ThreadX threads, mutexes, and semaphores.</span></span>

<span data-ttu-id="21861-120">Depende de la inicialización de la aplicación activar la controladora de dispositivos USB y una o varias clases USB.</span><span class="sxs-lookup"><span data-stu-id="21861-120">It is up to the application initialization to activate the USB device controller and one or more USB classes.</span></span> <span data-ttu-id="21861-121">Al contrario que el lado del host USB, el lado del dispositivo solo puede tener un controlador para la controladora USB en ejecución en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="21861-121">Contrary to the USB host side, the device side can have only one USB controller driver running at any time.</span></span> <span data-ttu-id="21861-122">Cuando las clases se han registrado en la pila y se ha llamado a la función de inicialización de la controladora de dispositivos, el bus está activo y la pila responderá a los comandos de enumeración de host y restablecimiento de bus.</span><span class="sxs-lookup"><span data-stu-id="21861-122">When the classes have been registered to the stack and the device controller(s) initialization function has been called, the bus is active and the stack will reply to bus reset and host enumeration commands.</span></span>

### <a name="application-interface-calls"></a><span data-ttu-id="21861-123">Llamadas a la interfaz de la aplicación</span><span class="sxs-lookup"><span data-stu-id="21861-123">Application Interface Calls</span></span>

<span data-ttu-id="21861-124">Hay dos niveles de API en USBX.</span><span class="sxs-lookup"><span data-stu-id="21861-124">There are two levels of APIs in USBX.</span></span>

- <span data-ttu-id="21861-125">API de la pila de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="21861-125">USB Device Stack APIs</span></span>
- <span data-ttu-id="21861-126">API de la clase de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="21861-126">USB Device Class APIs</span></span>

<span data-ttu-id="21861-127">Normalmente, una aplicación de USBX no debe tener que llamar a ninguna de las API de la pila de dispositivos USB.</span><span class="sxs-lookup"><span data-stu-id="21861-127">Normally, a USBX application should not have to call any of the USB device stack APIs.</span></span> <span data-ttu-id="21861-128">La mayoría de las aplicaciones solo tendrán acceso a las API de clase USB.</span><span class="sxs-lookup"><span data-stu-id="21861-128">Most applications will only access the USB Class APIs.</span></span>

### <a name="usb-device-stack-apis"></a><span data-ttu-id="21861-129">API de la pila de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="21861-129">USB Device Stack APIs</span></span>

<span data-ttu-id="21861-130">Las API de la pila de dispositivos son responsables del registro de los componentes de los dispositivos USBX, como las clases y el marco del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21861-130">The device stack APIs are responsible for the registration of USBX device components such as classes and the device framework.</span></span>

### <a name="usb-device-class-apis"></a><span data-ttu-id="21861-131">API de la clase de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="21861-131">USB Device Class APIs</span></span>

<span data-ttu-id="21861-132">Las API de clase son muy específicas de cada clase USB.</span><span class="sxs-lookup"><span data-stu-id="21861-132">The Class APIs are very specific to each USB class.</span></span> <span data-ttu-id="21861-133">La mayoría de las API comunes para las clases USB proporcionaban servicios como apertura y cierre de un dispositivo, y lectura y escritura en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21861-133">Most of the common APIs for USB classes provided services such as opening/closing a device and reading from and writing to a device.</span></span> <span data-ttu-id="21861-134">La naturaleza de las API es similar a la del lado del host.</span><span class="sxs-lookup"><span data-stu-id="21861-134">The APIs are similar in nature to the host side.</span></span>

## <a name="device-framework"></a><span data-ttu-id="21861-135">Marco de dispositivos</span><span class="sxs-lookup"><span data-stu-id="21861-135">Device Framework</span></span>

<span data-ttu-id="21861-136">El lado del dispositivo USB es responsable de la definición del marco del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21861-136">The USB device side is responsible for the definition of the device framework.</span></span> <span data-ttu-id="21861-137">El marco del dispositivo se divide en tres categorías, tal y como se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="21861-137">The device framework is divided into three categories, as described in the following sections.</span></span>

### <a name="definition-of-the-components-of-the-device-framework"></a><span data-ttu-id="21861-138">Definición de los componentes del marco del dispositivo</span><span class="sxs-lookup"><span data-stu-id="21861-138">Definition of the Components of the Device Framework</span></span>

<span data-ttu-id="21861-139">La definición de cada componente del marco del dispositivo está relacionada con la naturaleza del dispositivo y con los recursos utilizados por el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21861-139">The definition of each component of the device framework is related to the nature of the device and the resources utilized by the device.</span></span> <span data-ttu-id="21861-140">A continuación se detallan las categorías principales.</span><span class="sxs-lookup"><span data-stu-id="21861-140">Following are the main categories.</span></span>

- <span data-ttu-id="21861-141">Descriptor del dispositivo</span><span class="sxs-lookup"><span data-stu-id="21861-141">Device Descriptor</span></span>
- <span data-ttu-id="21861-142">Descriptor de configuración</span><span class="sxs-lookup"><span data-stu-id="21861-142">Configuration Descriptor</span></span>
- <span data-ttu-id="21861-143">Descriptor de la interfaz</span><span class="sxs-lookup"><span data-stu-id="21861-143">Interface Descriptor</span></span>
- <span data-ttu-id="21861-144">Descriptor del punto de conexión</span><span class="sxs-lookup"><span data-stu-id="21861-144">Endpoint Descriptor</span></span>

<span data-ttu-id="21861-145">USBX admite la definición de los componentes del dispositivo para la velocidad alta y máxima (la velocidad baja se trata de la misma forma que la velocidad máxima).</span><span class="sxs-lookup"><span data-stu-id="21861-145">USBX supports device component definition for both high and full speed (low speed being treated the same way as full speed).</span></span> <span data-ttu-id="21861-146">Esto permite que el dispositivo funcione de forma diferente cuando se conecta a un host de velocidad alta o máxima.</span><span class="sxs-lookup"><span data-stu-id="21861-146">This allows the device to operate differently when connected to a high speed or full speed host.</span></span> <span data-ttu-id="21861-147">Las diferencias típicas son el tamaño de cada punto de conexión y la potencia consumida por el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21861-147">The typical differences are the size of each endpoint and the power consumed by the device.</span></span>

<span data-ttu-id="21861-148">La definición del componente del dispositivo adopta la forma de una cadena de bytes que sigue la especificación USB.</span><span class="sxs-lookup"><span data-stu-id="21861-148">The definition of the device component takes the form of a byte string that follows the USB specification.</span></span> <span data-ttu-id="21861-149">La definición es contigua y el orden en el que se representa el marco en la memoria será el mismo que se devuelve al host durante la enumeración.</span><span class="sxs-lookup"><span data-stu-id="21861-149">The definition is contiguous and the order in which the framework is represented in memory will be the same as the one returned to the host during enumeration.</span></span>

<span data-ttu-id="21861-150">A continuación, se muestra un ejemplo de un marco de dispositivo para un disco flash USB de alta velocidad.</span><span class="sxs-lookup"><span data-stu-id="21861-150">Following is an example of a device framework for a high speed USB Flash Disk.</span></span>

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a><span data-ttu-id="21861-151">Definición de las cadenas del marco del dispositivo</span><span class="sxs-lookup"><span data-stu-id="21861-151">Definition of the Strings of the Device Framework</span></span>

<span data-ttu-id="21861-152">Las cadenas son opcionales en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21861-152">Strings are optional in a device.</span></span> <span data-ttu-id="21861-153">Su finalidad es dejar que el host USB conozca el fabricante del dispositivo, el nombre del producto y el número de revisión mediante cadenas Unicode.</span><span class="sxs-lookup"><span data-stu-id="21861-153">Their purpose is to let the USB host know about the manufacturer of the device, the product name, and the revision number through Unicode strings.</span></span>

<span data-ttu-id="21861-154">Las cadenas principales son índices insertados en los descriptores del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21861-154">The main strings are indexes embedded in the device descriptors.</span></span> <span data-ttu-id="21861-155">Se pueden insertar índices de cadenas adicionales en interfaces individuales.</span><span class="sxs-lookup"><span data-stu-id="21861-155">Additional strings indexes can be embedded into individual interfaces.</span></span>

<span data-ttu-id="21861-156">Suponiendo que el marco del dispositivo anterior tiene tres índices de cadena insertados en el descriptor del dispositivo, la definición del marco de cadena podría ser similar a la de este código de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="21861-156">Assuming the device framework above has three string indexes embedded into the device descriptor, the string framework definition could look like this example code.</span></span>

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38
UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

<span data-ttu-id="21861-157">Si hay que usar cadenas diferentes para cada velocidad, se deben usar índices diferentes, ya que los índices son independientes de la velocidad.</span><span class="sxs-lookup"><span data-stu-id="21861-157">If different strings have to be used for each speed, different indexes must be used as the indexes are speed agnostic.</span></span>

<span data-ttu-id="21861-158">La codificación de la cadena está basada en UNICODE.</span><span class="sxs-lookup"><span data-stu-id="21861-158">The encoding of the string is UNICODE-based.</span></span> <span data-ttu-id="21861-159">Para obtener más información sobre el estándar de codificación UNICODE, consulte la siguiente publicación:</span><span class="sxs-lookup"><span data-stu-id="21861-159">For more information on the UNICODE encoding standard refer to the following publication:</span></span>

<span data-ttu-id="21861-160">*Estándar Unicode, codificación de caracteres mundial, versión 1, volúmenes 1 y 2, Consorcio Unicode, empresa Addison-Wesley Publishing y Reading MA*</span><span class="sxs-lookup"><span data-stu-id="21861-160">*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*</span></span>

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a><span data-ttu-id="21861-161">Definición de los idiomas compatibles con el dispositivo para cada cadena</span><span class="sxs-lookup"><span data-stu-id="21861-161">Definition of the Languages Supported by the Device for each String</span></span>

<span data-ttu-id="21861-162">USBX tiene la capacidad de admitir varios idiomas, aunque el predeterminado es el inglés.</span><span class="sxs-lookup"><span data-stu-id="21861-162">USBX has the ability to support multiple languages although English is the default.</span></span> <span data-ttu-id="21861-163">La definición de cada idioma para los descriptores de cadena presenta la forma de una matriz de definición de idiomas definida como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="21861-163">The definition of each language for the string descriptors is in the form of an array of languages definition defined as follows.</span></span>

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="21861-164">Para admitir otros idiomas, basta con agregar la definición de doble byte del código de idioma después del código de inglés predeterminado.</span><span class="sxs-lookup"><span data-stu-id="21861-164">To support additional languages, simply add the language code double-byte definition after the default English code.</span></span> <span data-ttu-id="21861-165">Microsoft ha definido el código de idioma en el documento.</span><span class="sxs-lookup"><span data-stu-id="21861-165">The language code has been defined by Microsoft in the document.</span></span>

<span data-ttu-id="21861-166">*Desarrollo de software internacional para Windows 95 y Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span><span class="sxs-lookup"><span data-stu-id="21861-166">*Developing International Software for Windows 95 and Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span></span>

## <a name="vbus-manager"></a><span data-ttu-id="21861-167">Administrador de VBUS</span><span class="sxs-lookup"><span data-stu-id="21861-167">VBUS Manager</span></span>

<span data-ttu-id="21861-168">En la mayoría de los diseños de dispositivos USB, VBUS no forma parte del núcleo del dispositivo USB, sino que se conecta a un GPIO externo, que supervisa la señal de la línea.</span><span class="sxs-lookup"><span data-stu-id="21861-168">In most USB device designs, VBUS is not part of the USB Device core but rather connected to an external GPIO, which monitors the line signal.</span></span>

<span data-ttu-id="21861-169">Como resultado, VBUS debe administrarse de forma independiente con respecto al controlador de la controladora de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="21861-169">As a result, VBUS has to be managed separately from the device controller driver.</span></span>

<span data-ttu-id="21861-170">Es la aplicación la que debe proporcionar la dirección de E/S de VBUS a la controladora de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="21861-170">It is up to the application to provide the device controller with the address of the VBUS IO.</span></span> <span data-ttu-id="21861-171">VBUS debe inicializarse antes de inicializar la controladora de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="21861-171">VBUS must be initialized prior to the device controller initialization.</span></span>

<span data-ttu-id="21861-172">En función de la especificación de la plataforma para la supervisión de VBUS, es posible admitir las señales de VBUS del identificador del controlador de la controladora después de inicializar la E/S de VBUS o, si no es posible, la aplicación debe proporcionar el código para controlar VBUS.</span><span class="sxs-lookup"><span data-stu-id="21861-172">Depending on the platform specification for monitoring VBUS, it is possible to let the controller driver handle VBUS signals after the VBUS IO is initialized or if this is not possible, the application has to provide the code for handling VBUS.</span></span>

<span data-ttu-id="21861-173">Si la aplicación desea controlar VBUS por sí sola, su único requisito es llamar a la función ***ux_device_stack_disconnect*** cuando detecta que se ha extraído un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21861-173">If the application wishes to handle VBUS by itself, its only requirement is to call the function ***ux_device_stack_disconnect*** when it detects that a device has been extracted.</span></span> <span data-ttu-id="21861-174">No es necesario informar a la controladora cuando se inserte un dispositivo, ya que la controladora se activará cuando se detecte la señal de aserción/desaserción de RESTABLECIMIENTO DEL BUS.</span><span class="sxs-lookup"><span data-stu-id="21861-174">It is not necessary to inform the controller when a device is inserted because the controller will wake up when the BUS RESET assert/deassert signal is detected.</span></span>
