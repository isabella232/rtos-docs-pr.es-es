---
title: 'Capítulo 2: Consideraciones acerca de la clase del dispositivo USBX'
description: La clase RNDIS del dispositivo USB permite que un sistema host de USB se comunique con el dispositivo como un dispositivo Ethernet. Esta clase se basa en la implementación de propiedad de Microsoft y es específica de las plataformas de Windows.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 035492644a911eba3b1c62a79572bc7d4c55f6dd
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082224"
---
# <a name="chapter-2---usbx-device-class-considerations"></a><span data-ttu-id="4d466-104">Capítulo 2: Consideraciones acerca de la clase del dispositivo USBX</span><span class="sxs-lookup"><span data-stu-id="4d466-104">Chapter 2 - USBX Device Class Considerations</span></span>

## <a name="usb-device-rndis-class"></a><span data-ttu-id="4d466-105">Clase RNDIS del dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="4d466-105">USB Device RNDIS Class</span></span>

<span data-ttu-id="4d466-106">La clase RNDIS del dispositivo USB permite que un sistema host de USB se comunique con el dispositivo como un dispositivo Ethernet.</span><span class="sxs-lookup"><span data-stu-id="4d466-106">The USB device RNDIS class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="4d466-107">Esta clase se basa en la implementación de propiedad de Microsoft y es específica de las plataformas de Windows.</span><span class="sxs-lookup"><span data-stu-id="4d466-107">This class is based on the Microsoft proprietary implementation and is specific to Windows platforms.</span></span>

<span data-ttu-id="4d466-108">Un marco de dispositivos compatible con RNDIS debe declararse en la pila de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4d466-108">A RNDIS compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="4d466-109">A continuación se muestra un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="4d466-109">An example is found below.</span></span>

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

<span data-ttu-id="4d466-110">La clase RNDIS usa un enfoque de descriptor de dispositivos muy similar para CDC-ACM y CDC-ECM, y también requiere un descriptor IAD.</span><span class="sxs-lookup"><span data-stu-id="4d466-110">The RNDIS class uses a very similar device descriptor approach to the CDC-ACM and CDC-ECM and also requires a IAD descriptor.</span></span> <span data-ttu-id="4d466-111">Consulte la clase CDC-ACM para obtener la definición y los requisitos del descriptor de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4d466-111">See the CDC-ACM class for definition and requirements for the device descriptor.</span></span>

<span data-ttu-id="4d466-112">La activación de la clase RNDIS se realiza tal como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="4d466-112">The activation of the RNDIS class is as follows.</span></span>

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

<span data-ttu-id="4d466-113">Como en el caso de CDC-ECM, la clase RNDIS requiere 2 nodos, uno local y otro remoto, pero no hay ningún requisito para obtener un descriptor de cadena que describa el nodo remoto.</span><span class="sxs-lookup"><span data-stu-id="4d466-113">As for the CDC-ECM, the RNDIS class requires 2 nodes, one local and one remote but there is no requirement to have a string descriptor describing the remote node.</span></span>

<span data-ttu-id="4d466-114">Sin embargo, debido al mecanismo de mensajería de propiedad de Microsoft, se necesitan algunos parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="4d466-114">However due to Microsoft proprietary messaging mechanism, some extra parameters are required.</span></span> <span data-ttu-id="4d466-115">En primer lugar, debe pasar el id. de proveedor.</span><span class="sxs-lookup"><span data-stu-id="4d466-115">First the vendor ID has to be passed.</span></span> <span data-ttu-id="4d466-116">Lo mismo sucede con la versión del controlador de RNDIS.</span><span class="sxs-lookup"><span data-stu-id="4d466-116">Likewise, the driver version of the RNDIS.</span></span> <span data-ttu-id="4d466-117">También se debe proporcionar una cadena de proveedor.</span><span class="sxs-lookup"><span data-stu-id="4d466-117">A vendor string must also be given.</span></span>

<span data-ttu-id="4d466-118">La clase RNDIS tiene API integradas para transferir datos de ambas maneras, pero están ocultas en la aplicación, ya que la aplicación de usuario se comunicará con el dispositivo USB Ethernet a través de NetX.</span><span class="sxs-lookup"><span data-stu-id="4d466-118">The RNDIS class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="4d466-119">La clase USBX RNDIS está estrechamente relacionada con la pila de red NetX de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="4d466-119">The USBX RNDIS class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="4d466-120">Una aplicación que use las clases NetX y USBX RNDIS activará la pila de red de NetX de la manera habitual, pero además necesitará activar la pila de red USB tal como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="4d466-120">An application using both NetX and USBX RNDIS class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="4d466-121">La pila de red USB debe activarse una sola vez y no es específica de RNDIS, pero es necesaria para cualquier clase USB que requiera los servicios de NetX.</span><span class="sxs-lookup"><span data-stu-id="4d466-121">The USB network stack needs to be activated only once and is not specific to RNDIS but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="4d466-122">Tenga en cuenta que los hosts de MAC OS y Linux no reconocerán la clase RNDIS, ya que es específica de los sistemas operativos de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4d466-122">The RNDIS class will not be recognized by MAC OS and Linux hosts as it is specific to Microsoft operating systems.</span></span> <span data-ttu-id="4d466-123">En las plataformas de Windows, un archivo .inf debe estar presente en el host que coincide con el descriptor del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-123">On windows platforms a .inf file needs to be present on the host that matches the device descriptor.</span></span> <span data-ttu-id="4d466-124">Asimismo, Microsoft proporciona una plantilla para la clase RNDIS que se puede encontrar en el directorio usbx_windows_host_files.</span><span class="sxs-lookup"><span data-stu-id="4d466-124">Microsoft supplies a template for the RNDIS class and it can be found in the usbx_windows_host_files directory.</span></span> <span data-ttu-id="4d466-125">Para obtener una versión más reciente de Windows, debe usar el archivo RNDIS_Template.inf.</span><span class="sxs-lookup"><span data-stu-id="4d466-125">For more recent version of Windows the file RNDIS_Template.inf should be used.</span></span> <span data-ttu-id="4d466-126">Este archivo debe modificarse para reflejar el valor de PID/VID que usa el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-126">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="4d466-127">El valor PID/VID será específico para el cliente final cuando la empresa y el producto se registren mediante el valor USB-IF.</span><span class="sxs-lookup"><span data-stu-id="4d466-127">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="4d466-128">En el archivo .inf, los campos que se van a modificar se encuentran aquí.</span><span class="sxs-lookup"><span data-stu-id="4d466-128">In the inf file, the fields to modify are located here.</span></span>

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

<span data-ttu-id="4d466-129">En el marco del dispositivo RNDIS, el valor PID/VID se almacena en el descriptor del dispositivo (consulte el descriptor de dispositivo que se declaró anteriormente).</span><span class="sxs-lookup"><span data-stu-id="4d466-129">In the device framework of the RNDIS device, the PID/VID are stored in the device descriptor (see the device descriptor declared above)</span></span>

<span data-ttu-id="4d466-130">Cuando un sistema host de USB detecta el dispositivo USB RNDIS, monta una interfaz de red, y el dispositivo se puede usar con la pila del protocolo de red.</span><span class="sxs-lookup"><span data-stu-id="4d466-130">When a USB host systems discovers the USB RNDIS device, it will mount a network interface and the device can be used with network protocol stack.</span></span> <span data-ttu-id="4d466-131">Consulte el sistema operativo host como referencia.</span><span class="sxs-lookup"><span data-stu-id="4d466-131">See the host Operating System for reference.</span></span>

## <a name="usb-device-dfu-class"></a><span data-ttu-id="4d466-132">Clase DFU del dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="4d466-132">USB Device DFU Class</span></span>

<span data-ttu-id="4d466-133">La clase DFU del dispositivo USB permite que un sistema host USB actualice el firmware del dispositivo en función de una aplicación host.</span><span class="sxs-lookup"><span data-stu-id="4d466-133">The USB device DFU class allows for a USB host system to update the device firmware based on a host application.</span></span> <span data-ttu-id="4d466-134">La clase DFU es una clase estándar de tipo USB-IF.</span><span class="sxs-lookup"><span data-stu-id="4d466-134">The DFU class is a USB-IF standard class.</span></span>

<span data-ttu-id="4d466-135">La clase USBX DFU es relativamente sencilla.</span><span class="sxs-lookup"><span data-stu-id="4d466-135">USBX DFU class is relatively simple.</span></span> <span data-ttu-id="4d466-136">El descriptor de dispositivos de TI no requiere ningún punto de conexión de control.</span><span class="sxs-lookup"><span data-stu-id="4d466-136">It device descriptor does not require anything but a control endpoint.</span></span> <span data-ttu-id="4d466-137">La mayoría de las veces, esta clase se insertará en un dispositivo compuesto USB.</span><span class="sxs-lookup"><span data-stu-id="4d466-137">Most of the time, this class will be embedded into a USB composite device.</span></span> <span data-ttu-id="4d466-138">El dispositivo puede ser cualquier cosa, como un dispositivo de almacenamiento o un dispositivo COMM, y la interfaz DFU agregada puede informar al host de que el dispositivo puede actualizar su firmware sobre la marcha.</span><span class="sxs-lookup"><span data-stu-id="4d466-138">The device can be anything such as a storage device or a comm device and the added DFU interface can inform the host that the device can have its firmware updated on the fly.</span></span>

<span data-ttu-id="4d466-139">La clase DFU funciona en tres pasos.</span><span class="sxs-lookup"><span data-stu-id="4d466-139">The DFU class works in 3 steps.</span></span> <span data-ttu-id="4d466-140">En primer lugar, el dispositivo se monta de forma normal mediante la clase exportada.</span><span class="sxs-lookup"><span data-stu-id="4d466-140">First the device mounts as normal using the class exported.</span></span> <span data-ttu-id="4d466-141">Una aplicación en el host (Windows o Linux) ejecutará la clase DFU y enviará una solicitud para restablecer el dispositivo en el modo DFU.</span><span class="sxs-lookup"><span data-stu-id="4d466-141">An application on the host (Windows or Linux) will exercise the DFU class and send a request to reset the device into DFU mode.</span></span> <span data-ttu-id="4d466-142">El dispositivo desaparecerá del bus durante un breve período de tiempo (el suficiente para que el host y el dispositivo detecten una secuencia de restablecimiento) y, al reiniciarse, el dispositivo estará exclusivamente en modo DFU, en espera de que la aplicación host envíe una actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="4d466-142">The device will disappear from the bus for a short time (enough for the host and the device to detect a RESET sequence) and upon restarting, the device will be exclusively in DFU mode, waiting for the host application to send a firmware upgrade.</span></span> <span data-ttu-id="4d466-143">Una vez completada la actualización del firmware, la aplicación host restablece el dispositivo y, tras la reenumeración, el dispositivo volverá a su funcionamiento normal con el nuevo firmware.</span><span class="sxs-lookup"><span data-stu-id="4d466-143">When the firmware upgrade has been completed, the host application resets the device and upon re-enumeration the device will revert to its normal operation with the new firmware.</span></span>

<span data-ttu-id="4d466-144">Una plataforma de dispositivos DFU tendrá el siguiente aspecto.</span><span class="sxs-lookup"><span data-stu-id="4d466-144">A DFU device framework will look like this.</span></span>

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

<span data-ttu-id="4d466-145">En este ejemplo, el descriptor DFU no está asociado a ninguna otra clase.</span><span class="sxs-lookup"><span data-stu-id="4d466-145">In this example, the DFU descriptor is not associated with any other classes.</span></span> <span data-ttu-id="4d466-146">Tiene un descriptor de interfaz simple y no hay ningún otro punto de conexión asociado a él.</span><span class="sxs-lookup"><span data-stu-id="4d466-146">It has a simple interface descriptor and no other endpoints attached to it.</span></span> <span data-ttu-id="4d466-147">Hay un descriptor funcional que describe los detalles de las capacidades de DFU del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-147">There is a Functional descriptor that describes the specifics of the DFU capabilities of the device.</span></span>

<span data-ttu-id="4d466-148">La descripción de las capacidades de DFU es la siguiente.</span><span class="sxs-lookup"><span data-stu-id="4d466-148">The description of the DFU capabilities are as follows.</span></span>

| <span data-ttu-id="4d466-149">Nombre</span><span class="sxs-lookup"><span data-stu-id="4d466-149">Name</span></span>             | <span data-ttu-id="4d466-150">Offset</span><span class="sxs-lookup"><span data-stu-id="4d466-150">Offset</span></span>  | <span data-ttu-id="4d466-151">Size</span><span class="sxs-lookup"><span data-stu-id="4d466-151">Size</span></span> | <span data-ttu-id="4d466-152">type</span><span class="sxs-lookup"><span data-stu-id="4d466-152">type</span></span>      | <span data-ttu-id="4d466-153">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-153">Description</span></span> |
|------------------|----------|------|-----------|------------|
| <span data-ttu-id="4d466-154">bmAttributes</span><span class="sxs-lookup"><span data-stu-id="4d466-154">bmAttributes</span></span>  | <span data-ttu-id="4d466-155">2</span><span class="sxs-lookup"><span data-stu-id="4d466-155">2</span></span>     | <span data-ttu-id="4d466-156">1</span><span class="sxs-lookup"><span data-stu-id="4d466-156">1</span></span>   | <span data-ttu-id="4d466-157">Campo de bit</span><span class="sxs-lookup"><span data-stu-id="4d466-157">Bit field</span></span> | <span data-ttu-id="4d466-158">Bit 3: el dispositivo realizará una secuencia de asociación y desasociación del bus al recibir una solicitud de DFU_DETACH.</span><span class="sxs-lookup"><span data-stu-id="4d466-158">Bit 3: device will perform a bus detach-attach sequence when it receives a DFU_DETACH request.</span></span> <span data-ttu-id="4d466-159">El host no debe emitir un restablecimiento de USB.</span><span class="sxs-lookup"><span data-stu-id="4d466-159">The host must not issue a USB Reset.</span></span> <span data-ttu-id="4d466-160">(bitWillDetach) 0 = no 1 = sí; bit 2: el dispositivo puede comunicarse a través de USB después de realizar la fase de manifiesto.</span><span class="sxs-lookup"><span data-stu-id="4d466-160">(bitWillDetach) 0 = no 1 = yes Bit 2: device is able to communicate via USB after Manifestation phase.</span></span> <span data-ttu-id="4d466-161">(bitManifestationTolerant) 0 = no, debe ver el reinicio del bus 1 = sí bit 1: carga compatible (bitCanUpload) 0 = no 1 = sí; bit 0: descarga compatible (bitCanDnload) 0 = no 1 = sí</span><span class="sxs-lookup"><span data-stu-id="4d466-161">(bitManifestationTolerant) 0 = no, must see bus reset 1 = yes Bit 1: upload capable (bitCanUpload) 0 = no 1 = yes Bit 0: download capable (bitCanDnload) 0 = no 1 = yes</span></span>  |
| <span data-ttu-id="4d466-162">wDetachTimeOut</span><span class="sxs-lookup"><span data-stu-id="4d466-162">wDetachTimeOut</span></span>  | <span data-ttu-id="4d466-163">3</span><span class="sxs-lookup"><span data-stu-id="4d466-163">3</span></span>      | <span data-ttu-id="4d466-164">2</span><span class="sxs-lookup"><span data-stu-id="4d466-164">2</span></span>  | <span data-ttu-id="4d466-165">number</span><span class="sxs-lookup"><span data-stu-id="4d466-165">number</span></span>    | <span data-ttu-id="4d466-166">Es el tiempo, en milisegundos, que el dispositivo esperará después de la recepción de la solicitud de DFU_DETACH.</span><span class="sxs-lookup"><span data-stu-id="4d466-166">Time, in milliseconds, that the device will wait after receipt of the DFU_DETACH request.</span></span> <span data-ttu-id="4d466-167">Si este tiempo transcurre sin un restablecimiento de USB, el dispositivo finalizará la fase de reconfiguración y volverá al funcionamiento normal.</span><span class="sxs-lookup"><span data-stu-id="4d466-167">If this time elapses without a USB reset, then the device will terminate the Reconfiguration phase and revert back to normal operation.</span></span> <span data-ttu-id="4d466-168">Representa el tiempo máximo que el dispositivo puede esperar (dependiendo de sus temporizadores, etc.).</span><span class="sxs-lookup"><span data-stu-id="4d466-168">This represents the maximum time that the device can wait (depending on its timers, etc.).</span></span> <span data-ttu-id="4d466-169">USBX establece este valor en 1000 ms.</span><span class="sxs-lookup"><span data-stu-id="4d466-169">USBX sets this value to 1000 ms.</span></span>  |
| <span data-ttu-id="4d466-170">wTransferSize</span><span class="sxs-lookup"><span data-stu-id="4d466-170">wTransferSize</span></span>  | <span data-ttu-id="4d466-171">5</span><span class="sxs-lookup"><span data-stu-id="4d466-171">5</span></span>      | <span data-ttu-id="4d466-172">2</span><span class="sxs-lookup"><span data-stu-id="4d466-172">2</span></span>  | <span data-ttu-id="4d466-173">number</span><span class="sxs-lookup"><span data-stu-id="4d466-173">number</span></span>    | <span data-ttu-id="4d466-174">Número máximo de bytes que el dispositivo puede aceptar por operación de escritura de control \-.</span><span class="sxs-lookup"><span data-stu-id="4d466-174">Maximum number of bytes that the device can accept per control\-write operation.</span></span> <span data-ttu-id="4d466-175">USBX establece este valor en 64 bytes.</span><span class="sxs-lookup"><span data-stu-id="4d466-175">USBX sets this value to 64 bytes.</span></span> |

<span data-ttu-id="4d466-176">La declaración de la clase DFU es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="4d466-176">The declaration of the DFU class is as follows:</span></span>

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

<span data-ttu-id="4d466-177">La clase DFU debe trabajar con una aplicación de firmware de dispositivo específica del destino.</span><span class="sxs-lookup"><span data-stu-id="4d466-177">The DFU class needs to work with a device firmware application specific to the target.</span></span> <span data-ttu-id="4d466-178">Por lo tanto, define varias devoluciones de llamada para leer y escribir en bloques de firmware y para obtener el estado de la aplicación de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="4d466-178">Therefore it defines several call back to read and write blocks of firmware and to get status from the firmware update application.</span></span> <span data-ttu-id="4d466-179">La clase DFU también tiene una función de devolución de llamadas de notificaciones para informar a la aplicación cuando se produce un inicio y un final de la transferencia del firmware.</span><span class="sxs-lookup"><span data-stu-id="4d466-179">The DFU class also has a notify callback function to inform the application when a begin and end of transfer of the firmware occur.</span></span>

<span data-ttu-id="4d466-180">A continuación se proporciona la descripción de un flujo de la aplicación del DFU típico.</span><span class="sxs-lookup"><span data-stu-id="4d466-180">Following is the description of a typical DFU application flow.</span></span>

![Flujo de la aplicación DFU](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

<span data-ttu-id="4d466-182">El principal desafío de la clase DFU es obtener la aplicación correcta en el host para realizar la descarga del firmware.</span><span class="sxs-lookup"><span data-stu-id="4d466-182">The major challenge of the DFU class is getting the right application on the host to perform the download the firmware.</span></span> <span data-ttu-id="4d466-183">No hay ninguna aplicación que haya proporcionado Microsoft o USB-IF.</span><span class="sxs-lookup"><span data-stu-id="4d466-183">There is no application supplied by Microsoft or the USB-IF.</span></span> <span data-ttu-id="4d466-184">Existen algunas opciones de shareware y funcionan razonablemente bien en Linux, pero en un menor grado en Windows.</span><span class="sxs-lookup"><span data-stu-id="4d466-184">Some shareware exist and they work reasonably well on Linux and to a lesser extent on Windows.</span></span>

<span data-ttu-id="4d466-185">En Linux, puede usar las utilidades DFU para encontrarlas aquí: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util); también se puede encontrar mucha información sobre las utilidades DFU en este vínculo: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend).</span><span class="sxs-lookup"><span data-stu-id="4d466-185">On Linux, one can use dfu-utils to be found here: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) A lot of information on dfu utils can also be found on this link: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span></span>

<span data-ttu-id="4d466-186">La implementación de Linux de DFU realiza correctamente la secuencia de restablecimiento entre el host y el dispositivo, por lo que no es necesario que el dispositivo lo haga.</span><span class="sxs-lookup"><span data-stu-id="4d466-186">The Linux implementation of DFU performs correctly the reset sequence between the host and the device and therefore the device does not need to do it.</span></span> <span data-ttu-id="4d466-187">Linux puede aceptar que el elemento bmAttributes *bitWillDetach* sea 0.</span><span class="sxs-lookup"><span data-stu-id="4d466-187">Linux can accept for the bmAttributes *bitWillDetach* to be 0.</span></span> <span data-ttu-id="4d466-188">Por otro lado, Windows requiere que el dispositivo realice el restablecimiento.</span><span class="sxs-lookup"><span data-stu-id="4d466-188">Windows on the other side requires the device to perform the reset.</span></span>

<span data-ttu-id="4d466-189">En Windows, el registro USB debe ser capaz de asociar el dispositivo USB al PID/VID y a la biblioteca USB que, a su vez, usará la aplicación DFU.</span><span class="sxs-lookup"><span data-stu-id="4d466-189">On Windows, the USB registry must be able to associate the USB device with its PID/VID and the USB library which will in turn be used by the DFU application.</span></span> <span data-ttu-id="4d466-190">Esto puede hacerse fácilmente con la utilidad gratuita Zadig, que se puede encontrar aquí: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).</span><span class="sxs-lookup"><span data-stu-id="4d466-190">This can be easily done with the free utility Zadig which can be found here: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).</span></span>

<span data-ttu-id="4d466-191">Al ejecutar Zadig por primera vez, se mostrará esta pantalla:</span><span class="sxs-lookup"><span data-stu-id="4d466-191">Running Zadig for the first time will show this screen:</span></span>

![Ejecución de Zadig por primera vez](./media/usbx-device-stack-supplemental/zadig.png)

<span data-ttu-id="4d466-193">En la lista de dispositivos, busque el dispositivo y asócielo al controlador libusb de Windows.</span><span class="sxs-lookup"><span data-stu-id="4d466-193">From the device list, find your device and associate it with the libusb windows driver.</span></span> <span data-ttu-id="4d466-194">Esto enlazará el PID/VID del dispositivo con la biblioteca USB de Windows que usan las utilidades DFU.</span><span class="sxs-lookup"><span data-stu-id="4d466-194">This will bind the PID/VID of the device with the Windows USB library used by the DFU utilities.</span></span>

<span data-ttu-id="4d466-195">Para usar el comando DFU, simplemente desempaquete las utilidades DFU comprimidas en un directorio, y asegúrese de que el archivo dll de libusb también está presente en el mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="4d466-195">To operate the DFU command, simply unpack the zipped dfu utilities into a directory, making sure the libusb dll is also present in the same directory.</span></span> <span data-ttu-id="4d466-196">Las utilidades DFU se deben ejecutar desde un cuadro de DOS en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="4d466-196">The DFU utilities must be run from a DOS box at the command line.</span></span>

<span data-ttu-id="4d466-197">En primer lugar, escriba el comando **dfu-util –l** para determinar si el dispositivo aparece en la lista.</span><span class="sxs-lookup"><span data-stu-id="4d466-197">First, type the command **dfu-util –l** to determine whether the device is listed.</span></span> <span data-ttu-id="4d466-198">Si no es así, ejecute Zadig para asegurarse de que el dispositivo aparece y está asociado a la biblioteca USB.</span><span class="sxs-lookup"><span data-stu-id="4d466-198">If not, run Zadig to make sure the device is listed and associated with the USB library.</span></span> <span data-ttu-id="4d466-199">Debería ver una pantalla como la que se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="4d466-199">You should see a screen as follows:</span></span>

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

<span data-ttu-id="4d466-200">El siguiente paso será preparar el archivo que se va a descargar.</span><span class="sxs-lookup"><span data-stu-id="4d466-200">The next step will be to prepare the file to be downloaded.</span></span> <span data-ttu-id="4d466-201">La clase USBX DFU no realiza ninguna comprobación en este archivo y es independiente de su formato interno.</span><span class="sxs-lookup"><span data-stu-id="4d466-201">The USBX DFU class does not perform any verification on this file and is agnostic of its internal format.</span></span> <span data-ttu-id="4d466-202">Este archivo de firmware es específico del destino, pero no de DFU ni de USBX.</span><span class="sxs-lookup"><span data-stu-id="4d466-202">This firmware file is very specific to the target but not to DFU nor to USBX.</span></span>

<span data-ttu-id="4d466-203">A continuación, se puede indicar a la utilidad DFU que envíe el archivo; para ello escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="4d466-203">Then the dfu-util can be instructed to send the file by typing the following command:</span></span>

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

<span data-ttu-id="4d466-204">Asimismo, la utilidad DFU debe mostrar el proceso de descarga del archivo hasta que el firmware se haya descargado por completo.</span><span class="sxs-lookup"><span data-stu-id="4d466-204">The dfu-util should display the file download process until the firmware has been completely downloaded.</span></span>

## <a name="usb-device-pima-class-ptp-responder"></a><span data-ttu-id="4d466-205">Clase PIMA del dispositivo USB (respondedor PTP)</span><span class="sxs-lookup"><span data-stu-id="4d466-205">USB Device PIMA Class (PTP Responder)</span></span>

<span data-ttu-id="4d466-206">La clase PIMA del dispositivo USB permite que un sistema host USB (iniciador) se conecte a un:</span><span class="sxs-lookup"><span data-stu-id="4d466-206">The USB device PIMA class allows for a USB host system (Initiator) to connect to a</span></span>

<span data-ttu-id="4d466-207">Dispositivo PIMA (respondedor) para transferir archivos multimedia.</span><span class="sxs-lookup"><span data-stu-id="4d466-207">PIMA device (Resonder) to transfer media files.</span></span> <span data-ttu-id="4d466-208">La clase USBX PIMA se ajusta a la clase USB-IF PIMA 15740, también conocida como clase PTP (para el protocolo de transferencia de imágenes).</span><span class="sxs-lookup"><span data-stu-id="4d466-208">USBX Pima Class is conforming to the USB-IF PIMA 15740 class also known as PTP class (for Picture Transfer Protocol).</span></span>

<span data-ttu-id="4d466-209">La clase PIMA del lado del dispositivo USBX admite las siguientes operaciones.</span><span class="sxs-lookup"><span data-stu-id="4d466-209">USBX device side PIMA class supports the following operations.</span></span>

| <span data-ttu-id="4d466-210">Código de operación</span><span class="sxs-lookup"><span data-stu-id="4d466-210">Operation code</span></span>                                    | <span data-ttu-id="4d466-211">Value</span><span class="sxs-lookup"><span data-stu-id="4d466-211">Value</span></span> | <span data-ttu-id="4d466-212">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-212">Description</span></span>                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| <span data-ttu-id="4d466-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span><span class="sxs-lookup"><span data-stu-id="4d466-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span></span>    | <span data-ttu-id="4d466-214">0x1001</span><span class="sxs-lookup"><span data-stu-id="4d466-214">0x1001</span></span>  | <span data-ttu-id="4d466-215">Permite obtener las operaciones y los eventos que admite el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-215">Obtain the device supported operations and events</span></span>                                                         |
| <span data-ttu-id="4d466-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span><span class="sxs-lookup"><span data-stu-id="4d466-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span></span>        | <span data-ttu-id="4d466-217">0x1002</span><span class="sxs-lookup"><span data-stu-id="4d466-217">0x1002</span></span>  | <span data-ttu-id="4d466-218">Permite abrir una sesión entre el host y el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-218">Open a session between the host and the device</span></span>                                                            |
| <span data-ttu-id="4d466-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span><span class="sxs-lookup"><span data-stu-id="4d466-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span></span>       | <span data-ttu-id="4d466-220">0x1003</span><span class="sxs-lookup"><span data-stu-id="4d466-220">0x1003</span></span>  | <span data-ttu-id="4d466-221">Permite cerrar una sesión entre el host y el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-221">Close a session between the host and the device</span></span>                                                           |
| <span data-ttu-id="4d466-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span><span class="sxs-lookup"><span data-stu-id="4d466-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span></span>    | <span data-ttu-id="4d466-223">0x1004</span><span class="sxs-lookup"><span data-stu-id="4d466-223">0x1004</span></span>  | <span data-ttu-id="4d466-224">Permite devolver el id. de almacenamiento del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-224">Returns the storage ID for the device.</span></span> <span data-ttu-id="4d466-225">USBX PIMA solo usa un id. de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="4d466-225">USBX PIMA uses one storage ID only</span></span> |
| <span data-ttu-id="4d466-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span><span class="sxs-lookup"><span data-stu-id="4d466-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span></span>   | <span data-ttu-id="4d466-227">0x1005</span><span class="sxs-lookup"><span data-stu-id="4d466-227">0x1005</span></span>  | <span data-ttu-id="4d466-228">Permite devolver información sobre el objeto de almacenamiento, como la capacidad máxima y el espacio disponible.</span><span class="sxs-lookup"><span data-stu-id="4d466-228">Return information about the storage object such as max capacity and free space</span></span>                           |
| <span data-ttu-id="4d466-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="4d466-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span></span>    | <span data-ttu-id="4d466-230">0x1006</span><span class="sxs-lookup"><span data-stu-id="4d466-230">0x1006</span></span>  | <span data-ttu-id="4d466-231">Permite devolver el número de objetos contenidos en el dispositivo de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="4d466-231">Return the number of objects contained in the storage device</span></span>                                              |
| <span data-ttu-id="4d466-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span><span class="sxs-lookup"><span data-stu-id="4d466-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span></span> | <span data-ttu-id="4d466-233">0x1007</span><span class="sxs-lookup"><span data-stu-id="4d466-233">0x1007</span></span>  | <span data-ttu-id="4d466-234">Permite devolver una matriz de manipuladores de los objetos en el dispositivo de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="4d466-234">Return an array of handles of the objects on the storage device</span></span>                                           |
| <span data-ttu-id="4d466-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="4d466-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span></span>    | <span data-ttu-id="4d466-236">0x1008</span><span class="sxs-lookup"><span data-stu-id="4d466-236">0x1008</span></span>  | <span data-ttu-id="4d466-237">Permite devolver información acerca de un objeto, como el nombre de este, la fecha de creación y la fecha de modificación.</span><span class="sxs-lookup"><span data-stu-id="4d466-237">Return information about an object such as the name of the object, its creation date, modification date</span></span> |
| <span data-ttu-id="4d466-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="4d466-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span></span>          | <span data-ttu-id="4d466-239">0x1009</span><span class="sxs-lookup"><span data-stu-id="4d466-239">0x1009</span></span>  | <span data-ttu-id="4d466-240">Permite devolver los datos que pertenecen a un objeto específico.</span><span class="sxs-lookup"><span data-stu-id="4d466-240">Return the data pertaining to a specific object</span></span>                                                         |
| <span data-ttu-id="4d466-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span><span class="sxs-lookup"><span data-stu-id="4d466-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span></span>           | <span data-ttu-id="4d466-242">0x100a</span><span class="sxs-lookup"><span data-stu-id="4d466-242">0x100A</span></span>  | <span data-ttu-id="4d466-243">Permite enviar la miniatura si está disponible sobre un objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-243">Send the thumbnail if available about an object</span></span>                                                           |
| <span data-ttu-id="4d466-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="4d466-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span></span>       | <span data-ttu-id="4d466-245">0x100B</span><span class="sxs-lookup"><span data-stu-id="4d466-245">0x100B</span></span>  | <span data-ttu-id="4d466-246">Permite eliminar un objeto en el contenido multimedia.</span><span class="sxs-lookup"><span data-stu-id="4d466-246">Delete an object on the media</span></span>                                                                             |
| <span data-ttu-id="4d466-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="4d466-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span></span>   | <span data-ttu-id="4d466-248">0x100C</span><span class="sxs-lookup"><span data-stu-id="4d466-248">0x100C</span></span>  | <span data-ttu-id="4d466-249">Permite enviar al dispositivo la información sobre un objeto para su creación en el contenido multimedia.</span><span class="sxs-lookup"><span data-stu-id="4d466-249">Send to the device information about an object for its creation on the media</span></span>                              |
| <span data-ttu-id="4d466-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span><span class="sxs-lookup"><span data-stu-id="4d466-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span></span>         | <span data-ttu-id="4d466-251">0x100D</span><span class="sxs-lookup"><span data-stu-id="4d466-251">0x100D</span></span>  | <span data-ttu-id="4d466-252">Permite enviar los datos de un objeto al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-252">Send data for an object to the device</span></span>                                                                     |
| <span data-ttu-id="4d466-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span><span class="sxs-lookup"><span data-stu-id="4d466-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span></span>        | <span data-ttu-id="4d466-254">0x100F</span><span class="sxs-lookup"><span data-stu-id="4d466-254">0x100F</span></span>  | <span data-ttu-id="4d466-255">Permite limpiar los elementos multimedia del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-255">Clean the device media</span></span>                                                                                    |
| <span data-ttu-id="4d466-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span><span class="sxs-lookup"><span data-stu-id="4d466-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span></span>        | <span data-ttu-id="4d466-257">0x0110</span><span class="sxs-lookup"><span data-stu-id="4d466-257">0x0110</span></span>  | <span data-ttu-id="4d466-258">Permite restablecer el dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="4d466-258">Reset the target device</span></span>                                                                                   |

| <span data-ttu-id="4d466-259">Código de la operación</span><span class="sxs-lookup"><span data-stu-id="4d466-259">Operation Code</span></span>                                         | <span data-ttu-id="4d466-260">Value</span><span class="sxs-lookup"><span data-stu-id="4d466-260">Value</span></span> | <span data-ttu-id="4d466-261">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-261">Description</span></span> |
|--------------------------------------------------------|-------|-----------------------------------------|
| <span data-ttu-id="4d466-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="4d466-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span></span>       | <span data-ttu-id="4d466-263">0x4001</span><span class="sxs-lookup"><span data-stu-id="4d466-263">0x4001</span></span>  | <span data-ttu-id="4d466-264">Permite cancelar la transacción actual.</span><span class="sxs-lookup"><span data-stu-id="4d466-264">Cancels the current transaction</span></span>                                                 |
| <span data-ttu-id="4d466-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span><span class="sxs-lookup"><span data-stu-id="4d466-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span></span>             | <span data-ttu-id="4d466-266">0x4002</span><span class="sxs-lookup"><span data-stu-id="4d466-266">0x4002</span></span>  | <span data-ttu-id="4d466-267">Se ha agregado un objeto a los elementos multimedia del dispositivo y el host puede recuperarlo.</span><span class="sxs-lookup"><span data-stu-id="4d466-267">An object has been added to the device media and can be retrieved by the host\.</span></span> |
| <span data-ttu-id="4d466-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span><span class="sxs-lookup"><span data-stu-id="4d466-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span></span>           | <span data-ttu-id="4d466-269">0x4003</span><span class="sxs-lookup"><span data-stu-id="4d466-269">0x4003</span></span>  | <span data-ttu-id="4d466-270">Se ha eliminado un objeto de los elementos multimedia del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-270">An object has been deleted from the device media</span></span>                                |
| <span data-ttu-id="4d466-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span><span class="sxs-lookup"><span data-stu-id="4d466-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span></span>              | <span data-ttu-id="4d466-272">0x4004</span><span class="sxs-lookup"><span data-stu-id="4d466-272">0x4004</span></span>  | <span data-ttu-id="4d466-273">Se ha agregado un elemento multimedia al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-273">A media has been added to the device</span></span>                                            |
| <span data-ttu-id="4d466-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span><span class="sxs-lookup"><span data-stu-id="4d466-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span></span>            | <span data-ttu-id="4d466-275">0x4005</span><span class="sxs-lookup"><span data-stu-id="4d466-275">0x4005</span></span>  | <span data-ttu-id="4d466-276">Se ha eliminado un elemento multimedia del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-276">A media has been deleted from the device</span></span>                                        |
| <span data-ttu-id="4d466-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span><span class="sxs-lookup"><span data-stu-id="4d466-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span></span>     | <span data-ttu-id="4d466-278">0x4006</span><span class="sxs-lookup"><span data-stu-id="4d466-278">0x4006</span></span>  | <span data-ttu-id="4d466-279">Las propiedades del elemento han cambiado.</span><span class="sxs-lookup"><span data-stu-id="4d466-279">Device properties have changed</span></span>                                                  |
| <span data-ttu-id="4d466-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="4d466-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span></span>     | <span data-ttu-id="4d466-281">0x4007</span><span class="sxs-lookup"><span data-stu-id="4d466-281">0x4007</span></span>  | <span data-ttu-id="4d466-282">Ha cambiado la información de un objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-282">An object information has changed</span></span>                                               |
| <span data-ttu-id="4d466-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span><span class="sxs-lookup"><span data-stu-id="4d466-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span></span>      | <span data-ttu-id="4d466-284">0x4008</span><span class="sxs-lookup"><span data-stu-id="4d466-284">0x4008</span></span>  | <span data-ttu-id="4d466-285">Un dispositivo ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="4d466-285">A device has changed</span></span>                                                            |
| <span data-ttu-id="4d466-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span><span class="sxs-lookup"><span data-stu-id="4d466-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span></span> | <span data-ttu-id="4d466-287">0x4009</span><span class="sxs-lookup"><span data-stu-id="4d466-287">0x4009</span></span>  | <span data-ttu-id="4d466-288">El dispositivo solicita la transferencia de un objeto desde el host.</span><span class="sxs-lookup"><span data-stu-id="4d466-288">The device requests the transfer of an object from the host</span></span>                     |
| <span data-ttu-id="4d466-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span><span class="sxs-lookup"><span data-stu-id="4d466-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span></span>               | <span data-ttu-id="4d466-290">0x400A</span><span class="sxs-lookup"><span data-stu-id="4d466-290">0x400A</span></span>  | <span data-ttu-id="4d466-291">El dispositivo indica que está al completo de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="4d466-291">Device reports the media is full</span></span>                                                |
| <span data-ttu-id="4d466-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span><span class="sxs-lookup"><span data-stu-id="4d466-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span></span>             | <span data-ttu-id="4d466-293">0x400B</span><span class="sxs-lookup"><span data-stu-id="4d466-293">0x400B</span></span>  | <span data-ttu-id="4d466-294">El dispositivo indica que se ha restablecido.</span><span class="sxs-lookup"><span data-stu-id="4d466-294">Device reports it was reset</span></span>                                                     |
| <span data-ttu-id="4d466-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="4d466-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span></span>    | <span data-ttu-id="4d466-296">0x400C</span><span class="sxs-lookup"><span data-stu-id="4d466-296">0x400C</span></span>  | <span data-ttu-id="4d466-297">La información de almacenamiento ha cambiado en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-297">Storage information has changed on the device</span></span>                                   |
| <span data-ttu-id="4d466-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="4d466-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span></span>         | <span data-ttu-id="4d466-299">0x400D</span><span class="sxs-lookup"><span data-stu-id="4d466-299">0x400D</span></span>  | <span data-ttu-id="4d466-300">La captura se ha completado.</span><span class="sxs-lookup"><span data-stu-id="4d466-300">Capture is completed</span></span>                                                            |

<span data-ttu-id="4d466-301">La clase de dispositivo USBX PIMA usa un subproceso TX para escuchar los comandos PIMA del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-301">The USBX PIMA device class uses a TX Thread to listen to PIMA commands from the host.</span></span>

<span data-ttu-id="4d466-302">Un comando PIMA se compone de un bloque de comandos, un bloque de datos y una fase de estado.</span><span class="sxs-lookup"><span data-stu-id="4d466-302">A PIMA command is composed of a command block, a data block and a status phase.</span></span>

<span data-ttu-id="4d466-303">La función ux_device_class_pima_thread envía una solicitud a la pila para recibir un comando PIMA del lado del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-303">The function ux_device_class_pima_thread posts a request to the stack to receive a PIMA command from the host side.</span></span> <span data-ttu-id="4d466-304">El comando PIMA se descodifica y se comprueba su contenido.</span><span class="sxs-lookup"><span data-stu-id="4d466-304">The PIMA command is decoded and verified for content.</span></span> <span data-ttu-id="4d466-305">Si el bloque de comandos es válido, este se bifurca en el controlador de comandos adecuado.</span><span class="sxs-lookup"><span data-stu-id="4d466-305">If the command block is valid, it branches to the appropriate command handler.</span></span>

<span data-ttu-id="4d466-306">La mayoría de comandos PIMA solo se pueden ejecutar cuando el host ha abierto una sesión.</span><span class="sxs-lookup"><span data-stu-id="4d466-306">Most PIMA commands can only be executed when a session has been opened by the host.</span></span> <span data-ttu-id="4d466-307">La única excepción es el comando **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span><span class="sxs-lookup"><span data-stu-id="4d466-307">The only exception is the command **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span></span> <span data-ttu-id="4d466-308">Con la implementación USBX PIMA, solo se puede abrir una sesión entre un iniciador y un respondedor en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="4d466-308">With USBX PIMA implementation, only one session can be opened between an Initiator and Responder at any time.</span></span> <span data-ttu-id="4d466-309">Todas las transacciones de la sesión única están bloqueadas y no se puede iniciar una nueva transacción antes de que se complete la anterior.</span><span class="sxs-lookup"><span data-stu-id="4d466-309">All transactions within the single session are blocking and no new transaction can begin before the previous one completed.</span></span>

<span data-ttu-id="4d466-310">Las transacciones PIMA se componen de tres fases: una fase de comandos, una fase de datos opcional y una fase de respuesta.</span><span class="sxs-lookup"><span data-stu-id="4d466-310">PIMA transactions are composed of 3 phases, a command phase, an optional data phase and a response phase.</span></span> <span data-ttu-id="4d466-311">Si hay una fase de datos, solo puede estar en una dirección.</span><span class="sxs-lookup"><span data-stu-id="4d466-311">If a data phase is present, it can only be in one direction.</span></span>

<span data-ttu-id="4d466-312">El iniciador siempre determina el flujo de las operaciones PIMA, pero el respondedor puede iniciar los eventos de vuelta al iniciador para informar de los cambios de estado que se produjeron durante una sesión.</span><span class="sxs-lookup"><span data-stu-id="4d466-312">The Initiator always determines the flow of the PIMA operations but the Responder can initiate events back to the Initiator to inform status changes that happened during a session.</span></span>

<span data-ttu-id="4d466-313">En el diagrama siguiente se muestra la transferencia de un objeto de datos entre el host y la clase de dispositivo PIMA.</span><span class="sxs-lookup"><span data-stu-id="4d466-313">The following diagram shows the transfer of a data object between the host and the PIMA device class.</span></span>

![Transacciones PIMA](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a><span data-ttu-id="4d466-315">Inicialización de la clase de dispositivo PIMA</span><span class="sxs-lookup"><span data-stu-id="4d466-315">Initialization of the PIMA device class</span></span>

<span data-ttu-id="4d466-316">La clase de dispositivo PIMA necesita algunos parámetros que proporciona la aplicación durante la inicialización.</span><span class="sxs-lookup"><span data-stu-id="4d466-316">The PIMA device class needs some parameters supplied by the application during the initialization.</span></span>

<span data-ttu-id="4d466-317">Los parámetros siguientes describen la información del dispositivo y del almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="4d466-317">The following parameters describe the device and storage information.</span></span>

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

<span data-ttu-id="4d466-318">La clase PIMA también requiere que realice el registro de la devolución de llamada en la aplicación para informar a la aplicación de determinados eventos o para recuperar o almacenar datos en el medio local.</span><span class="sxs-lookup"><span data-stu-id="4d466-318">The PIMA class also requires the registration of callback into the application to inform the application of certain events or retrieve/store data from/to the local media.</span></span> <span data-ttu-id="4d466-319">Las devoluciones de llamada son tal como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="4d466-319">The callbacks are as follows.</span></span>

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

<span data-ttu-id="4d466-320">En el ejemplo siguiente se muestra cómo inicializar el lado cliente de PIMA.</span><span class="sxs-lookup"><span data-stu-id="4d466-320">The following example shows how to initialize the client side of PIMA.</span></span> <span data-ttu-id="4d466-321">En este ejemplo se usa PictBridge como cliente para PIMA.</span><span class="sxs-lookup"><span data-stu-id="4d466-321">This example uses Pictbridge as a client for PIMA.</span></span>

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="4d466-322">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="4d466-322">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="4d466-323">Permite agregar un objeto y enviar el evento al host</span><span class="sxs-lookup"><span data-stu-id="4d466-323">Adding an object and sending the event to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-324">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-324">Prototype</span></span>

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="4d466-325">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-325">Description</span></span>

<span data-ttu-id="4d466-326">Se llama a esta función cuando la clase PIMA necesita agregar un objeto e informar al host.</span><span class="sxs-lookup"><span data-stu-id="4d466-326">This function is called when the PIMA class needs to add an object and inform the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-327">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-327">Parameters</span></span>

- <span data-ttu-id="4d466-328">**pima**: puntero a la instancia de la clase pima.</span><span class="sxs-lookup"><span data-stu-id="4d466-328">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="4d466-329">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-329">**object_handle**: Handle of the object.</span></span>

### <a name="example"></a><span data-ttu-id="4d466-330">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-330">Example</span></span>

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a><span data-ttu-id="4d466-331">ux_device_class_pima_object_number_get</span><span class="sxs-lookup"><span data-stu-id="4d466-331">ux_device_class_pima_object_number_get</span></span>

<span data-ttu-id="4d466-332">Permite obtener el número de objeto de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d466-332">Getting the object number from the application</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-333">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-333">Prototype</span></span>

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a><span data-ttu-id="4d466-334">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-334">Description</span></span>

<span data-ttu-id="4d466-335">Se llama a esta función cuando la clase PIMA necesita recuperar el número de objetos en el sistema local y enviarlo de nuevo al host.</span><span class="sxs-lookup"><span data-stu-id="4d466-335">This function is called when the PIMA class needs to retrieve the number of objects in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-336">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-336">Parameters</span></span>

- <span data-ttu-id="4d466-337">**pima**: puntero a la instancia de la clase pima.</span><span class="sxs-lookup"><span data-stu-id="4d466-337">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="4d466-338">**object_number**: dirección del número de objetos que se van a devolver.</span><span class="sxs-lookup"><span data-stu-id="4d466-338">**object_number**: Address of the number of objects to be returned</span></span>

### <a name="example"></a><span data-ttu-id="4d466-339">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-339">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a><span data-ttu-id="4d466-340">ux_device_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="4d466-340">ux_device_class_pima_object_handles_get</span></span>

<span data-ttu-id="4d466-341">Permite devolver la matriz de identificadores de objetos.</span><span class="sxs-lookup"><span data-stu-id="4d466-341">Return the object handle array</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-342">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-342">Prototype</span></span>

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a><span data-ttu-id="4d466-343">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-343">Description</span></span>

<span data-ttu-id="4d466-344">Se llama a esta función cuando la clase PIMA necesita recuperar el número de objetos en el sistema local y enviarlo de nuevo al host.</span><span class="sxs-lookup"><span data-stu-id="4d466-344">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-345">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-345">Parameters</span></span>

- <span data-ttu-id="4d466-346">**pima**: puntero a la instancia de la clase pima.</span><span class="sxs-lookup"><span data-stu-id="4d466-346">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="4d466-347">**object_handles_format_code**: código de formato para los identificadores.</span><span class="sxs-lookup"><span data-stu-id="4d466-347">**object_handles_format_code**: Format code for the handles</span></span>
- <span data-ttu-id="4d466-348">**object_handles_association**: código de asociación de objetos.</span><span class="sxs-lookup"><span data-stu-id="4d466-348">**object_handles_association**: Object association code</span></span>
- <span data-ttu-id="4d466-349">**object_handle_array**: dirección en la que se almacenan los identificadores.</span><span class="sxs-lookup"><span data-stu-id="4d466-349">**object_handle_array**: Address where to store the handles</span></span>
- <span data-ttu-id="4d466-350">**object_handles_max_number**: número máximo de identificadores de la matriz.</span><span class="sxs-lookup"><span data-stu-id="4d466-350">**object_handles_max_number**: Maximum number of handles in the array</span></span>

### <a name="example"></a><span data-ttu-id="4d466-351">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-351">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a><span data-ttu-id="4d466-352">ux_device_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="4d466-352">ux_device_class_pima_object_info_get</span></span>

<span data-ttu-id="4d466-353">Permite devolver la información del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-353">Return the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-354">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-354">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a><span data-ttu-id="4d466-355">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-355">Description</span></span>

<span data-ttu-id="4d466-356">Se llama a esta función cuando la clase PIMA necesita recuperar el número de objetos en el sistema local y enviarlo de nuevo al host.</span><span class="sxs-lookup"><span data-stu-id="4d466-356">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-357">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-357">Parameters</span></span>

- <span data-ttu-id="4d466-358">**pima**: puntero a la instancia de la clase pima.</span><span class="sxs-lookup"><span data-stu-id="4d466-358">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="4d466-359">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-359">**object_handles**: Handle of the object</span></span>
- <span data-ttu-id="4d466-360">**object**: dirección del puntero del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-360">**object**: Object pointer address</span></span>

### <a name="example"></a><span data-ttu-id="4d466-361">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-361">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="4d466-362">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="4d466-362">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="4d466-363">Permite devolver los datos del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-363">Return the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-364">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-364">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a><span data-ttu-id="4d466-365">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-365">Description</span></span>

<span data-ttu-id="4d466-366">Se llama a esta función cuando la clase PIMA necesita recuperar los datos de los objetos en el sistema local y enviarlo de nuevo al host.</span><span class="sxs-lookup"><span data-stu-id="4d466-366">This function is called when the PIMA class needs to retrieve the object data in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-367">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-367">Parameters</span></span>

- <span data-ttu-id="4d466-368">**pima**: puntero a la instancia de la clase pima.</span><span class="sxs-lookup"><span data-stu-id="4d466-368">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="4d466-369">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-369">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="4d466-370">**object_buffer**: dirección del búfer del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-370">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="4d466-371">**object_length_requested**: longitud de datos de objetos que ha solicitado el cliente a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d466-371">**object_length_requested**: Object data length requested by the client to the application</span></span>
- <span data-ttu-id="4d466-372">**object_actual_length**: longitud de datos de objeto de devuelve la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d466-372">**object_actual_length**: Object data length returned by the application</span></span>

### <a name="example"></a><span data-ttu-id="4d466-373">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-373">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="4d466-374">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="4d466-374">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="4d466-375">El host envía la información del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-375">Host sends the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-376">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-376">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a><span data-ttu-id="4d466-377">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-377">Description</span></span>

<span data-ttu-id="4d466-378">Se llama a esta función cuando la clase PIMA necesita recibir la información del objeto en el sistema local para el almacenamiento futuro.</span><span class="sxs-lookup"><span data-stu-id="4d466-378">This function is called when the PIMA class needs to receive the object information in the local system for future storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-379">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-379">Parameters</span></span>

- <span data-ttu-id="4d466-380">**pima**: puntero a la instancia de la clase pima.</span><span class="sxs-lookup"><span data-stu-id="4d466-380">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="4d466-381">**object**: puntero al objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-381">**object**:  Pointer to the object</span></span>
- <span data-ttu-id="4d466-382">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-382">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="4d466-383">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-383">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="4d466-384">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="4d466-384">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="4d466-385">El host envía los datos del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-385">Host sends the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-386">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-386">Prototype</span></span>

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a><span data-ttu-id="4d466-387">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-387">Description</span></span>

<span data-ttu-id="4d466-388">Se llama a esta función cuando la clase PIMA necesita recibir la información del objeto en el sistema local para el almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="4d466-388">This function is called when the PIMA class needs to receive the object data in the local system for storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-389">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-389">Parameters</span></span>

- <span data-ttu-id="4d466-390">**pima**: puntero a la instancia de la clase pima.</span><span class="sxs-lookup"><span data-stu-id="4d466-390">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="4d466-391">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-391">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="4d466-392">**phase**: fase de la transferencia (activa o completa).</span><span class="sxs-lookup"><span data-stu-id="4d466-392">**phase**: phase of the transfer (active or complete)</span></span>
- <span data-ttu-id="4d466-393">**object_buffer**: dirección del búfer del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-393">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="4d466-394">**object_offset**: dirección de los datos.</span><span class="sxs-lookup"><span data-stu-id="4d466-394">**object_offset**: Address of data</span></span>
- <span data-ttu-id="4d466-395">**object_length**: longitud de datos del objeto que ha enviado la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d466-395">**object_length**: Object data length sent by application</span></span>

### <a name="example"></a><span data-ttu-id="4d466-396">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-396">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="4d466-397">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="4d466-397">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="4d466-398">Permite eliminar un objeto local.</span><span class="sxs-lookup"><span data-stu-id="4d466-398">Delete a local object</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-399">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-399">Prototype</span></span>

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="4d466-400">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-400">Description</span></span>

<span data-ttu-id="4d466-401">Se llama a esta función cuando la clase PIMA necesita eliminar un objeto en el almacenamiento local.</span><span class="sxs-lookup"><span data-stu-id="4d466-401">This function is called when the PIMA class needs to delete an object on the local storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-402">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-402">Parameters</span></span>

- <span data-ttu-id="4d466-403">**pima**: puntero a la instancia de la clase pima.</span><span class="sxs-lookup"><span data-stu-id="4d466-403">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="4d466-404">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d466-404">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="4d466-405">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-405">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a><span data-ttu-id="4d466-406">Clase de audio del dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="4d466-406">USB Device Audio Class</span></span>

<span data-ttu-id="4d466-407">La clase de audio del dispositivo USB permite que un sistema host de USB se comunique con el dispositivo como un dispositivo de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-407">The USB device Audio class allows for a USB host system to communicate with the device as an audio device.</span></span> <span data-ttu-id="4d466-408">Esta clase se basa en el estándar USB y la clase de audio USB 1.0 o 2.0 estándar.</span><span class="sxs-lookup"><span data-stu-id="4d466-408">This class is based on the USB standard and USB Audio Class 1.0 or 2.0 standard.</span></span>

<span data-ttu-id="4d466-409">Un marco de dispositivos compatible con el audio USB debe declararse en la pila de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4d466-409">A USB audio compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="4d466-410">A continuación, se muestra un ejemplo de un altavoz de audio 2.0:</span><span class="sxs-lookup"><span data-stu-id="4d466-410">An example of an Audio 2.0 speaker follows:</span></span>

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

<span data-ttu-id="4d466-411">La clase de audio utiliza un marco de dispositivo compuesto para agrupar interfaces (control y streaming).</span><span class="sxs-lookup"><span data-stu-id="4d466-411">The Audio class uses a composite device framework to group interfaces (control and streaming).</span></span> <span data-ttu-id="4d466-412">Como resultado, debe tener cuidado al definir el descriptor de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-412">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="4d466-413">USBX se basa en el descriptor IAD para saber internamente cómo enlazar interfaces.</span><span class="sxs-lookup"><span data-stu-id="4d466-413">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="4d466-414">El descriptor IAD debe declararse antes que las interfaces (una interfaz de AudioControl seguida de una o varias interfaces de AudioStreaming) y contener la primera interfaz de la clase de audio (la interfaz de AudioControl) y el número de interfaces que están asociadas.</span><span class="sxs-lookup"><span data-stu-id="4d466-414">The IAD descriptor should be declared before the interfaces (an AudioControl interface followed by one or more AudioStreaming interfaces) and contain the first interface of the Audio class (the AudioControl interface) and how many interfaces are attached.</span></span>

<span data-ttu-id="4d466-415">La forma en que funciona la clase de audio depende de si el dispositivo está enviando o recibiendo audio, pero ambos casos usan un FIFO para almacenar búferes de tramas de audio: si el dispositivo está enviando audio al host, la aplicación agrega búferes de tramas de audio al FIFO que USBX envía posteriormente al host; si por el contrario el dispositivo está recibiendo audio desde el host, USBX agrega los búferes de tramas de audio recibidos del host al FIFO, que posteriormente lee la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d466-415">The way the audio class works depends on whether the device is sending or receiving audio, but both cases use a FIFO for storing audio frame buffers: if the device is sending audio to the host, then the application adds audio frame buffers to the FIFO which are later sent to the host by USBX; if the device is receiving audio from the host, then USBX adds the audio frame buffers received from the host to the FIFO which are later read by the application.</span></span> <span data-ttu-id="4d466-416">Cada flujo de audio tiene su propio FIFO y cada búfer de trama de audio consta de varios ejemplos.</span><span class="sxs-lookup"><span data-stu-id="4d466-416">Each audio stream has its own FIFO, and each audio frame buffer consists of multiple samples.</span></span>

<span data-ttu-id="4d466-417">La inicialización de la clase de audio espera las siguientes partes.</span><span class="sxs-lookup"><span data-stu-id="4d466-417">The initialization of the Audio class expects the following parts.</span></span>

1. <span data-ttu-id="4d466-418">La clase de audio espera los siguientes parámetros de streaming:</span><span class="sxs-lookup"><span data-stu-id="4d466-418">Audio class expects the following streaming parameters:</span></span>

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. <span data-ttu-id="4d466-419">La clase de audio espera los siguientes parámetros de función.</span><span class="sxs-lookup"><span data-stu-id="4d466-419">Audio class expects the following function parameters.</span></span>

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_audio_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   <span data-ttu-id="4d466-420">La devolución de llamada de la solicitud de control que define la aplicación (***ux_device_class_audio_control_process***; establecida en el ejemplo anterior) se invoca cuando la pila recibe una solicitud de control del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-420">The application-defined control request callback (***ux_device_class_audio_control_process***; set in the previous example) is invoked when the stack receives a control request from the host.</span></span> <span data-ttu-id="4d466-421">Si la solicitud se acepta y se controla (se confirma o se detiene), la devolución de llamada debe devolver un resultado correcto; de lo contrario, debe devolver un error.</span><span class="sxs-lookup"><span data-stu-id="4d466-421">If the request is accepted and handled (acknowledged or stalled) the callback must return success, otherwise error should be returned.</span></span>

   <span data-ttu-id="4d466-422">El proceso de solicitud de control específico de la clase se define como una devolución de llamada que define la aplicación porque las solicitudes de control son muy diferentes entre las versiones de audio USB, y una gran parte del proceso de solicitud se relaciona con el marco de trabajo del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d466-422">The class-specific control request process is defined as an application-defined callback because the control requests are very different between USB Audio versions and a large part of the request process relates to the device framework.</span></span> <span data-ttu-id="4d466-423">La aplicación debe controlar las solicitudes correctamente para que el dispositivo funcione.</span><span class="sxs-lookup"><span data-stu-id="4d466-423">The application should handle requests correctly to make the device functional.</span></span>

   <span data-ttu-id="4d466-424">Puesto que para un dispositivo de audio, el volumen, el silencio y la frecuencia de muestreo son solicitudes de control comunes, las devoluciones de llamada simples y definidas internamente para diferentes versiones de audio USB se introducen en secciones posteriores para que las usen las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="4d466-424">Since for an audio device, volume, mute and sampling frequency are common control requests, simple, internally-defined callbacks for different USB audio versions are introduced in later sections for applications to use.</span></span> <span data-ttu-id="4d466-425">Consulte ***ux_device_class_audio10_control_process** _ y _ *_ux_device_class_audio_control_request_** para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="4d466-425">Refer to ***ux_device_class_audio10_control_process** _ and _ *_ux_device_class_audio_control_request_** for more details.</span></span>

<span data-ttu-id="4d466-426">En el marco del dispositivo de audio, el valor PID/VID se almacena en el descriptor del dispositivo (consulte el descriptor de dispositivo que se declaró anteriormente).</span><span class="sxs-lookup"><span data-stu-id="4d466-426">In the device framework of the Audio device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="4d466-427">Cuando un sistema host USB detecta el dispositivo de audio USB y monta la clase de audio, el dispositivo puede usarse con cualquier reproductor o grabadora de audio (según el marco de trabajo).</span><span class="sxs-lookup"><span data-stu-id="4d466-427">When a USB host system discovers the USB Audio device and mounts the audio class, the device can be used with any audio player or recorder (depending on the framework).</span></span> <span data-ttu-id="4d466-428">Consulte el sistema operativo host como referencia.</span><span class="sxs-lookup"><span data-stu-id="4d466-428">See the host Operating System for reference.</span></span>

<span data-ttu-id="4d466-429">A continuación se definen las API de la clase de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-429">The Audio class APIs are defined below.</span></span>

## <a name="ux_device_class_audio_read_thread_entry"></a><span data-ttu-id="4d466-430">ux_device_class_audio_read_thread_entry</span><span class="sxs-lookup"><span data-stu-id="4d466-430">ux_device_class_audio_read_thread_entry</span></span>

<span data-ttu-id="4d466-431">Entrada de subproceso para leer los datos de la función de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-431">Thread entry for reading data for the Audio function.</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-432">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-432">Prototype</span></span>

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="4d466-433">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-433">Description</span></span>

<span data-ttu-id="4d466-434">Esta función se pasa al parámetro de inicialización de la secuencia de audio si quiere leer el audio del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-434">This function is passed to the audio stream initialization parameter if reading audio from the host is desired.</span></span> <span data-ttu-id="4d466-435">Internamente, se crea un subproceso con esta función como su función de entrada; el propio subproceso lee los datos de audio a través del punto de conexión isocróno OUT en la función Audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-435">Internally, a thread is created with this function as its entry function; the thread itself reads audio data through the isochronous OUT endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-436">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-436">Parameters</span></span>

- <span data-ttu-id="4d466-437">**audio_stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-437">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="4d466-438">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-438">Example</span></span>

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a><span data-ttu-id="4d466-439">ux_device_class_audio_write_thread_entry</span><span class="sxs-lookup"><span data-stu-id="4d466-439">ux_device_class_audio_write_thread_entry</span></span>

<span data-ttu-id="4d466-440">Entrada de subproceso para leer los datos de la función Audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-440">Thread entry for writing data for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-441">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-441">Prototype</span></span>

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="4d466-442">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-442">Description</span></span>

<span data-ttu-id="4d466-443">Esta función se pasa al parámetro de inicialización de la secuencia de audio si quiere escribir en el audio del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-443">This function is passed to the audio stream initialization parameter if writing audio to the host is desired.</span></span> <span data-ttu-id="4d466-444">Internamente, se crea un subproceso con esta función como su función de entrada; el propio subproceso escribe los datos de audio a través del punto de conexión isocróno IN en la función Audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-444">Internally, a thread is created with this function as its entry function; the thread itself writes audio data through the isochronous IN endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-445">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-445">Parameters</span></span>

- <span data-ttu-id="4d466-446">**audio_stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-446">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="4d466-447">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-447">Example</span></span>

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a><span data-ttu-id="4d466-448">ux_device_class_audio_stream_get</span><span class="sxs-lookup"><span data-stu-id="4d466-448">ux_device_class_audio_stream_get</span></span>

<span data-ttu-id="4d466-449">Permite obtener una instancia de flujo específica para la función Audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-449">Get specific stream instance for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-450">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-450">Prototype</span></span>

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a><span data-ttu-id="4d466-451">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-451">Description</span></span>

<span data-ttu-id="4d466-452">Esta función se usa para obtener una instancia de secuencia de la clase de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-452">This function is used to get a stream instance of audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-453">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-453">Parameters</span></span>

- <span data-ttu-id="4d466-454">**audio**: puntero a la instancia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-454">**audio**: Pointer to the audio instance</span></span>
- <span data-ttu-id="4d466-455">**stream_index**: índice de instancia de la secuencia basado en 0.</span><span class="sxs-lookup"><span data-stu-id="4d466-455">**stream_index**: Stream instance index based on 0</span></span>
- <span data-ttu-id="4d466-456">**stream**: puntero al búfer para almacenar el puntero de la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-456">**stream**: Pointer to buffer to store the audio stream instance pointer</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-457">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-457">Return Value</span></span>

- <span data-ttu-id="4d466-458">**UX_SUCCESS** (0X00) esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-458">**UX_SUCCESS** (0x00) This operation was successful</span></span>
- <span data-ttu-id="4d466-459">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-459">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-460">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-460">Example</span></span>

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a><span data-ttu-id="4d466-461">ux_device_class_audio_reception_start</span><span class="sxs-lookup"><span data-stu-id="4d466-461">ux_device_class_audio_reception_start</span></span>

<span data-ttu-id="4d466-462">Permite iniciar la recepción de datos de audio para la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-462">Start audio data reception for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-463">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-463">Prototype</span></span>

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="4d466-464">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-464">Description</span></span>

<span data-ttu-id="4d466-465">Esta función se usa para iniciar la lectura de datos de audio en secuencias de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-465">This function is used to start audio data reading in audio streams.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-466">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-466">Parameters</span></span>

- <span data-ttu-id="4d466-467">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-467">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-468">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-468">Return Value</span></span>

- <span data-ttu-id="4d466-469">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-469">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-471">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO está lleno.</span><span class="sxs-lookup"><span data-stu-id="4d466-471">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="4d466-472">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-472">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-473">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-473">Example</span></span>

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a><span data-ttu-id="4d466-474">ux_device_class_audio_sample_read8</span><span class="sxs-lookup"><span data-stu-id="4d466-474">ux_device_class_audio_sample_read8</span></span>

<span data-ttu-id="4d466-475">Permite leer la muestra de 8 bits de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-475">Read 8-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-476">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-476">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="4d466-477">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-477">Description</span></span>

<span data-ttu-id="4d466-478">Esta función lee los datos de la muestra de audio de 8 bits de la secuencia especificada.</span><span class="sxs-lookup"><span data-stu-id="4d466-478">This function reads 8-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="4d466-479">En concreto, lee los datos de muestra del búfer de la trama de audio actual en el FIFO.</span><span class="sxs-lookup"><span data-stu-id="4d466-479">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="4d466-480">Tras leer la última muestra en una trama de audio, esta se liberará automáticamente para que se pueda usar para aceptar más datos del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-480">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-481">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-481">Parameters</span></span>

- <span data-ttu-id="4d466-482">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-482">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="4d466-483">**buffer**: puntero al búfer para guardar la muestra de bytes.</span><span class="sxs-lookup"><span data-stu-id="4d466-483">**buffer**: Pointer to the buffer to save sample byte.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-484">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-484">Return Value</span></span>

- <span data-ttu-id="4d466-485">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-485">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-487">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.</span><span class="sxs-lookup"><span data-stu-id="4d466-487">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="4d466-488">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-488">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-489">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-489">Example</span></span>

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a><span data-ttu-id="4d466-490">ux_device_class_audio_sample_read16</span><span class="sxs-lookup"><span data-stu-id="4d466-490">ux_device_class_audio_sample_read16</span></span>

<span data-ttu-id="4d466-491">Permite leer la muestra de 16 bits de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-491">Read 16-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-492">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-492">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a><span data-ttu-id="4d466-493">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-493">Description</span></span>

<span data-ttu-id="4d466-494">Esta función lee los datos de la muestra de audio de 16 bits de la secuencia especificada.</span><span class="sxs-lookup"><span data-stu-id="4d466-494">This function reads 16-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="4d466-495">En concreto, lee los datos de muestra del búfer de la trama de audio actual en el FIFO.</span><span class="sxs-lookup"><span data-stu-id="4d466-495">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="4d466-496">Tras leer la última muestra en una trama de audio, esta se liberará automáticamente para que se pueda usar para aceptar más datos del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-496">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-497">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-497">Parameters</span></span>

- <span data-ttu-id="4d466-498">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-498">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="4d466-499">**buffer**: puntero al búfer para guardar la muestra de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="4d466-499">**buffer**: Pointer to the buffer to save the 16-bit sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-500">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-500">Return Value</span></span>

- <span data-ttu-id="4d466-501">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-501">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-503">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.</span><span class="sxs-lookup"><span data-stu-id="4d466-503">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="4d466-504">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-504">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-505">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-505">Example</span></span>

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a><span data-ttu-id="4d466-506">ux_device_class_audio_sample_read24</span><span class="sxs-lookup"><span data-stu-id="4d466-506">ux_device_class_audio_sample_read24</span></span>

<span data-ttu-id="4d466-507">Permite leer la muestra de 24 bits de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-507">Read 24-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-508">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-508">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="4d466-509">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-509">Description</span></span>

<span data-ttu-id="4d466-510">Esta función lee los datos de la muestra de audio de 24 bits de la secuencia especificada.</span><span class="sxs-lookup"><span data-stu-id="4d466-510">This function reads 24-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="4d466-511">En concreto, lee los datos de muestra del búfer de la trama de audio actual en el FIFO.</span><span class="sxs-lookup"><span data-stu-id="4d466-511">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="4d466-512">Tras leer la última muestra en una trama de audio, esta se liberará automáticamente para que se pueda usar para aceptar más datos del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-512">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-513">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-513">Parameters</span></span>

- <span data-ttu-id="4d466-514">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-514">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="4d466-515">**buffer**: puntero al búfer para guardar la muestra de 3 bytes.</span><span class="sxs-lookup"><span data-stu-id="4d466-515">**buffer**: Pointer to the buffer to save the 3-byte sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-516">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-516">Return Value</span></span>

- <span data-ttu-id="4d466-517">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-517">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-519">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.</span><span class="sxs-lookup"><span data-stu-id="4d466-519">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="4d466-520">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-520">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-521">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-521">Example</span></span>

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a><span data-ttu-id="4d466-522">ux_device_class_audio_sample_read32</span><span class="sxs-lookup"><span data-stu-id="4d466-522">ux_device_class_audio_sample_read32</span></span>

<span data-ttu-id="4d466-523">Permite leer la muestra de 32 bits de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-523">Read 32-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-524">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-524">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="4d466-525">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-525">Description</span></span>

<span data-ttu-id="4d466-526">Esta función lee los datos de la muestra de audio de 32 bits de la secuencia especificada.</span><span class="sxs-lookup"><span data-stu-id="4d466-526">This function reads 32-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="4d466-527">En concreto, lee los datos de muestra del búfer de la trama de audio actual en el FIFO.</span><span class="sxs-lookup"><span data-stu-id="4d466-527">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="4d466-528">Tras leer la última muestra en una trama de audio, esta se liberará automáticamente para que se pueda usar para aceptar más datos del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-528">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-529">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-529">Parameters</span></span>

- <span data-ttu-id="4d466-530">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-530">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="4d466-531">**buffer**: puntero al búfer para guardar la muestra de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="4d466-531">**buffer**: Pointer to the buffer to save the 4-byte data.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-532">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-532">Return Value</span></span>

- <span data-ttu-id="4d466-533">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-533">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-535">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.</span><span class="sxs-lookup"><span data-stu-id="4d466-535">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="4d466-536">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-536">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-537">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-537">Example</span></span>

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a><span data-ttu-id="4d466-538">ux_device_class_audio_read_frame_get</span><span class="sxs-lookup"><span data-stu-id="4d466-538">ux_device_class_audio_read_frame_get</span></span>

<span data-ttu-id="4d466-539">Permite obtener acceso a la trama de audio en la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-539">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-540">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-540">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="4d466-541">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-541">Description</span></span>

<span data-ttu-id="4d466-542">Esta función devuelve el primer búfer de la trama de audio y su longitud en el FIFO de la secuencia especificada.</span><span class="sxs-lookup"><span data-stu-id="4d466-542">This function returns the first audio frame buffer and its length in the specified stream's FIFO.</span></span> <span data-ttu-id="4d466-543">Cuando la aplicación termina de procesar los datos, se debe usar ux_device_class_audio_read_frame_free para liberar el búfer de la trama en el FIFO.</span><span class="sxs-lookup"><span data-stu-id="4d466-543">When the application is done processing the data, ux_device_class_audio_read_frame_free must be used to free the frame buffer in the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-544">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-544">Parameters</span></span>

- <span data-ttu-id="4d466-545">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-545">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="4d466-546">**frame_data**: puntero para el puntero de datos en el que se va a devolver el puntero de datos.</span><span class="sxs-lookup"><span data-stu-id="4d466-546">**frame_data**: Pointer to data pointer to return the data pointer in.</span></span>
- <span data-ttu-id="4d466-547">**frame_length**: puntero al búfer para guardar la longitud de la trama en número de bytes.</span><span class="sxs-lookup"><span data-stu-id="4d466-547">**frame_length**: Pointer to buffer to save the frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-548">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-548">Return Value</span></span>

- <span data-ttu-id="4d466-549">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-549">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-551">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.</span><span class="sxs-lookup"><span data-stu-id="4d466-551">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="4d466-552">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-552">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-553">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-553">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a><span data-ttu-id="4d466-554">ux_device_class_audio_read_frame_free</span><span class="sxs-lookup"><span data-stu-id="4d466-554">ux_device_class_audio_read_frame_free</span></span>

<span data-ttu-id="4d466-555">Permite liberar un búfer de la trama de audio en la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-555">Free an audio frame buffer in Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-556">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-556">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="4d466-557">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-557">Description</span></span>

<span data-ttu-id="4d466-558">Esta función libera el búfer de la trama de audio situado al principio del FIFO de la secuencia especificada para que pueda recibir datos del host.</span><span class="sxs-lookup"><span data-stu-id="4d466-558">This function frees the audio frame buffer at the front of the specified stream's FIFO so that it can receive data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-559">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-559">Parameters</span></span>

- <span data-ttu-id="4d466-560">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-560">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-561">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-561">Return Value</span></span>

- <span data-ttu-id="4d466-562">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-562">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-564">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.</span><span class="sxs-lookup"><span data-stu-id="4d466-564">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="4d466-565">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-565">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-566">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-566">Example</span></span>

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a><span data-ttu-id="4d466-567">ux_device_class_audio_transmission_start</span><span class="sxs-lookup"><span data-stu-id="4d466-567">ux_device_class_audio_transmission_start</span></span>

<span data-ttu-id="4d466-568">Permite iniciar la transmisión de datos de audio para la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-568">Start audio data transmission for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-569">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-569">Prototype</span></span>

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="4d466-570">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-570">Description</span></span>

<span data-ttu-id="4d466-571">Esta función se usa para empezar a enviar datos de audio escritos en el FIFO en la clase de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-571">This function is used to start sending audio data written to the FIFO in the audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-572">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-572">Parameters</span></span>

- <span data-ttu-id="4d466-573">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-573">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-574">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-574">Return Value</span></span>

- <span data-ttu-id="4d466-575">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-575">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-577">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO es NULL.</span><span class="sxs-lookup"><span data-stu-id="4d466-577">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="4d466-578">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-578">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-579">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-579">Example</span></span>

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a><span data-ttu-id="4d466-580">ux_device_class_audio_frame_write</span><span class="sxs-lookup"><span data-stu-id="4d466-580">ux_device_class_audio_frame_write</span></span>

<span data-ttu-id="4d466-581">Permite escribir una trama de audio en la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-581">Write an audio frame into the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-582">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-582">Prototype</span></span>

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a><span data-ttu-id="4d466-583">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-583">Description</span></span>

<span data-ttu-id="4d466-584">Esta función escribe una trama en el FIFO de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-584">This function writes a frame to the audio stream's FIFO.</span></span> <span data-ttu-id="4d466-585">Los datos de la trama se copian en el búfer disponible en el FIFO para que se pueda enviar al host.</span><span class="sxs-lookup"><span data-stu-id="4d466-585">The frame data is copied to the available buffer in the FIFO so that it can be sent to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-586">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-586">Parameters</span></span>

- <span data-ttu-id="4d466-587">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-587">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="4d466-588">**frame**: puntero a los datos de la trama.</span><span class="sxs-lookup"><span data-stu-id="4d466-588">**frame**: Pointer to frame data.</span></span>
- <span data-ttu-id="4d466-589">**frame_length**: longitud de la trama en número de bytes.</span><span class="sxs-lookup"><span data-stu-id="4d466-589">**frame_length** Frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-590">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-590">Return Value</span></span>

- <span data-ttu-id="4d466-591">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-591">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-593">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO está lleno.</span><span class="sxs-lookup"><span data-stu-id="4d466-593">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="4d466-594">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-594">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-595">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-595">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a><span data-ttu-id="4d466-596">ux_device_class_audio_write_frame_get</span><span class="sxs-lookup"><span data-stu-id="4d466-596">ux_device_class_audio_write_frame_get</span></span>

<span data-ttu-id="4d466-597">Permite obtener acceso a la trama de audio en la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-597">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-598">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-598">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="4d466-599">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-599">Description</span></span>

<span data-ttu-id="4d466-600">Esta función recupera la dirección del último búfer de trama de audio del FIFO; también recupera la longitud del búfer de la trama de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-600">This function retrieves the address of the last audio frame buffer of the FIFO; it also retrieves the length of the audio frame buffer.</span></span> <span data-ttu-id="4d466-601">Una vez que la aplicación rellena el búfer de la trama de audio con los datos deseados, ***ux_device_class_audio_write_frame_commit*** debe usarse para agregar o confirmar el búfer de la trama en el FIFO.</span><span class="sxs-lookup"><span data-stu-id="4d466-601">After the application fills the audio frame buffer with its desired data, ***ux_device_class_audio_write_frame_commit*** must be used to add/commit the frame buffer to the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-602">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-602">Parameters</span></span>

- <span data-ttu-id="4d466-603">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-603">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="4d466-604">**frame_data**: puntero para el puntero de datos de la trama en el que se va a devolver el puntero de datos de la trama.</span><span class="sxs-lookup"><span data-stu-id="4d466-604">**frame_data**: Pointer to frame data pointer to return the frame data pointer in.</span></span>
- <span data-ttu-id="4d466-605">**frame_length**: puntero al búfer para guardar la longitud de la trama en número de bytes.</span><span class="sxs-lookup"><span data-stu-id="4d466-605">**frame_length** Pointer to the buffer to save frame length in number of bytes .</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-606">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-606">Return Value</span></span>

- <span data-ttu-id="4d466-607">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-607">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-609">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO está lleno.</span><span class="sxs-lookup"><span data-stu-id="4d466-609">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="4d466-610">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-610">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-611">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-611">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a><span data-ttu-id="4d466-612">ux_device_class_audio_write_frame_get</span><span class="sxs-lookup"><span data-stu-id="4d466-612">ux_device_class_audio_write_frame_commit</span></span>

<span data-ttu-id="4d466-613">Permite liberar un búfer de la trama de audio en la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-613">Commit an audio frame buffer in Audio stream.</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-614">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-614">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="4d466-615">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-615">Description</span></span>

<span data-ttu-id="4d466-616">Esta función agrega o confirma el último búfer de la trama de audio en el FIFO, por lo que el búfer está listo para transferirse al host; tenga en cuenta que el último búfer de la trama de audio debe haberse rellenado a través de ux_device_class_write_frame_get.</span><span class="sxs-lookup"><span data-stu-id="4d466-616">This function adds/commits the last audio frame buffer to the FIFO so the buffer is ready to be transferred to host; note the last audio frame buffer should have been filled out via ux_device_class_write_frame_get.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-617">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-617">Parameters</span></span>

- <span data-ttu-id="4d466-618">**stream**: puntero a la instancia de la secuencia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-618">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="4d466-619">**length**: número de bytes listos en el búfer.</span><span class="sxs-lookup"><span data-stu-id="4d466-619">**length**: Number of bytes ready in the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-620">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-620">Return Value</span></span>

- <span data-ttu-id="4d466-621">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-621">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) La interfaz está inactiva.</span><span class="sxs-lookup"><span data-stu-id="4d466-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="4d466-623">**UX_BUFFER_OVERFLOW** (0x5d) El búfer FIFO está lleno.</span><span class="sxs-lookup"><span data-stu-id="4d466-623">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is fssull.</span></span>
- <span data-ttu-id="4d466-624">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-624">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-625">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-625">Example</span></span>

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a><span data-ttu-id="4d466-626">ux_device_class_audio10_control_process</span><span class="sxs-lookup"><span data-stu-id="4d466-626">ux_device_class_audio10_control_process</span></span>

<span data-ttu-id="4d466-627">Permite procesar solicitudes de control de audio USB 1.0</span><span class="sxs-lookup"><span data-stu-id="4d466-627">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-628">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-628">Prototype</span></span>

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="4d466-629">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-629">Description</span></span>

<span data-ttu-id="4d466-630">Esta función administra las solicitudes básicas que envían el host en el punto de conexión de control con un tipo específico 1.0 de audio USB.</span><span class="sxs-lookup"><span data-stu-id="4d466-630">This function manages basic requests sent by the host on the control endpoint with a USB Audio 1.0 specific type.</span></span>

<span data-ttu-id="4d466-631">Las características de audio 1.0 de las solicitudes de volumen y silenciar se procesan en la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-631">Audio 1.0 features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="4d466-632">Al procesar las solicitudes, los datos predefinidos que pasa el último parámetro (grupo) se usan para responder a las solicitudes y almacenar los cambios del control.</span><span class="sxs-lookup"><span data-stu-id="4d466-632">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-633">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-633">Parameters</span></span>

- <span data-ttu-id="4d466-634">**audio**: puntero a la instancia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-634">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="4d466-635">**transfer**: puntero a la instancia de la solicitud de transferencia.</span><span class="sxs-lookup"><span data-stu-id="4d466-635">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="4d466-636">**group**: grupo de datos para el proceso de solicitud.</span><span class="sxs-lookup"><span data-stu-id="4d466-636">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-637">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-637">Return Value</span></span>

- <span data-ttu-id="4d466-638">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-638">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-639">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-639">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-640">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-640">Example</span></span>

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a><span data-ttu-id="4d466-641">ux_device_class_audio20_control_process</span><span class="sxs-lookup"><span data-stu-id="4d466-641">ux_device_class_audio20_control_process</span></span>

<span data-ttu-id="4d466-642">Permite procesar solicitudes de control de audio USB 1.0</span><span class="sxs-lookup"><span data-stu-id="4d466-642">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="4d466-643">Prototipo</span><span class="sxs-lookup"><span data-stu-id="4d466-643">Prototype</span></span>
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="4d466-644">Descripción</span><span class="sxs-lookup"><span data-stu-id="4d466-644">Description</span></span>

<span data-ttu-id="4d466-645">Esta función administra las solicitudes básicas que envían el host en el punto de conexión de control con un tipo específico de audio USB 2.0.</span><span class="sxs-lookup"><span data-stu-id="4d466-645">This function manages basic requests sent by the host on the control endpoint with a USB Audio 2.0 specific type.</span></span>

<span data-ttu-id="4d466-646">La velocidad de muestreo de audio 2.0 (se supone una frecuencia de un solo fijo), las características de las solicitudes de volumen y silenciar se procesan en la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-646">Audio 2.0 sampling rate (assumed single fixed frequency), features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="4d466-647">Al procesar las solicitudes, los datos predefinidos que pasa el último parámetro (grupo) se usan para responder a las solicitudes y almacenar los cambios del control.</span><span class="sxs-lookup"><span data-stu-id="4d466-647">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="4d466-648">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4d466-648">Parameters</span></span>

- <span data-ttu-id="4d466-649">**audio**: puntero a la instancia de audio.</span><span class="sxs-lookup"><span data-stu-id="4d466-649">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="4d466-650">**transfer**: puntero a la instancia de la solicitud de transferencia.</span><span class="sxs-lookup"><span data-stu-id="4d466-650">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="4d466-651">**group**: grupo de datos para el proceso de solicitud.</span><span class="sxs-lookup"><span data-stu-id="4d466-651">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="4d466-652">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="4d466-652">Return Value</span></span>

- <span data-ttu-id="4d466-653">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="4d466-653">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="4d466-654">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="4d466-654">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="4d466-655">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4d466-655">Example</span></span>

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
