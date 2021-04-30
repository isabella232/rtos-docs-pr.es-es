---
title: 'Capítulo 2: Instalación de la pila de dispositivos de Azure RTOS USBX'
description: Obtenga información sobre cómo instalar la pila de dispositivos de Azure RTOS USBX, así como las consideraciones de host importantes que debe tener en cuenta antes de la instalación.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd58f77130fa252be9163bd70c29f7deee400d30
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549783"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a><span data-ttu-id="1aba6-103">Capítulo 2: Instalación de la pila de dispositivos de Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="1aba6-103">Chapter 2 - Azure RTOS USBX Device Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="1aba6-104">Consideraciones sobre el host</span><span class="sxs-lookup"><span data-stu-id="1aba6-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="1aba6-105">Tipo de equipo</span><span class="sxs-lookup"><span data-stu-id="1aba6-105">Computer Type</span></span>

<span data-ttu-id="1aba6-106">El desarrollo insertado se suele realizar en equipos host Windows o Unix.</span><span class="sxs-lookup"><span data-stu-id="1aba6-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="1aba6-107">Una vez que la aplicación está compilada, vinculada y colocada en el host, se descarga en el hardware de destino para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="1aba6-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="1aba6-108">Interfaces de descarga</span><span class="sxs-lookup"><span data-stu-id="1aba6-108">Download Interfaces</span></span>

<span data-ttu-id="1aba6-109">Normalmente, la descarga de destino se realiza por medio de una interfaz serie RS-232, aunque las interfaces paralelas, USB y Ethernet se están volviendo más populares.</span><span class="sxs-lookup"><span data-stu-id="1aba6-109">Usually the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="1aba6-110">Revise la documentación de la herramienta de desarrollo para ver las opciones disponibles.</span><span class="sxs-lookup"><span data-stu-id="1aba6-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="1aba6-111">Herramientas de depuración</span><span class="sxs-lookup"><span data-stu-id="1aba6-111">Debugging Tools</span></span>

<span data-ttu-id="1aba6-112">La depuración se suele realizar con el mismo vínculo que la descarga de la imagen del programa.</span><span class="sxs-lookup"><span data-stu-id="1aba6-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="1aba6-113">Existen diversos depuradores, que abarcan desde pequeños programas de supervisión que se ejecutan en el destino, hasta herramientas de supervisión de depuración en segundo plano (BDM) y de emulación en circuito (ICE).</span><span class="sxs-lookup"><span data-stu-id="1aba6-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="1aba6-114">La herramienta ICE proporciona la depuración más sólida del hardware de destino real.</span><span class="sxs-lookup"><span data-stu-id="1aba6-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="1aba6-115">Espacio en disco duro requerido</span><span class="sxs-lookup"><span data-stu-id="1aba6-115">Required Hard Disk Space</span></span>

<span data-ttu-id="1aba6-116">El código fuente de USBX se entrega en formato ASCII y requiere aproximadamente 500 KB de espacio en el disco duro del equipo host.</span><span class="sxs-lookup"><span data-stu-id="1aba6-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

### <a name="target-considerations"></a><span data-ttu-id="1aba6-117">Consideraciones sobre el destino</span><span class="sxs-lookup"><span data-stu-id="1aba6-117">Target Considerations</span></span>

<span data-ttu-id="1aba6-118">USBX requiere entre 24 KB y 64 KB de memoria de solo lectura (ROM) en el destino en modo de host.</span><span class="sxs-lookup"><span data-stu-id="1aba6-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="1aba6-119">La cantidad de memoria necesaria depende del tipo de controlador utilizado y de las clases USB vinculadas a USBX.</span><span class="sxs-lookup"><span data-stu-id="1aba6-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="1aba6-120">Se requieren otros 32 KB de memoria de acceso aleatorio (RAM) del destino para las estructuras de datos globales de USBX y el bloque de memoria.</span><span class="sxs-lookup"><span data-stu-id="1aba6-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="1aba6-121">Este bloque de memoria también se puede ajustar en función del número esperado de dispositivos en el USB y el tipo de controlador USB.</span><span class="sxs-lookup"><span data-stu-id="1aba6-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="1aba6-122">El lado del dispositivo USBX requiere aproximadamente entre 10 y 12 KB de ROM según el tipo de controlador de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1aba6-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="1aba6-123">El uso de memoria RAM depende del tipo de clase emulada por el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1aba6-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="1aba6-124">USBX también se basa en semáforos, exclusiones mutuas y subprocesos de ThreadX para la protección de varios subprocesos, y en la suspensión de E/S y el procesamiento periódico para la supervisión de la topología del bus USB.</span><span class="sxs-lookup"><span data-stu-id="1aba6-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="1aba6-125">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="1aba6-125">Product Distribution</span></span>

<span data-ttu-id="1aba6-126">Azure RTOS USBX se puede obtener desde el repositorio de código fuente público en <https://github.com/azure-rtos/usbx/>.</span><span class="sxs-lookup"><span data-stu-id="1aba6-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="1aba6-127">A continuación, se muestra una lista de varios archivos importantes del repositorio.</span><span class="sxs-lookup"><span data-stu-id="1aba6-127">The following is a list of several important files in the repository.</span></span>

* <span data-ttu-id="1aba6-128">***ux_api.h***: este archivo de encabezado de C contiene todas las equivalencias del sistema, estructuras de datos y prototipos del servicio.</span><span class="sxs-lookup"><span data-stu-id="1aba6-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
* <span data-ttu-id="1aba6-129">***ux_port.h***: este archivo de encabezado de C contiene todas las definiciones de datos y estructuras específicas de la herramienta de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="1aba6-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
* <span data-ttu-id="1aba6-130">***ux.lib***: se trata de la versión binaria de la biblioteca de C de USBX.</span><span class="sxs-lookup"><span data-stu-id="1aba6-130">***ux.lib***:  This is the binary version of the USBX C library.</span></span> <span data-ttu-id="1aba6-131">Se distribuye con el paquete estándar.</span><span class="sxs-lookup"><span data-stu-id="1aba6-131">It is distributed with the standard package.</span></span>
* <span data-ttu-id="1aba6-132">***demo_usbx.c***: archivo de C que contiene una demostración de USBX simple.</span><span class="sxs-lookup"><span data-stu-id="1aba6-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="1aba6-133">Todos los nombres de archivo están en minúsculas.</span><span class="sxs-lookup"><span data-stu-id="1aba6-133">All filenames are in lower-case.</span></span> <span data-ttu-id="1aba6-134">Esta convención de nomenclatura facilita la conversión de los comandos en plataformas de desarrollo de Unix.</span><span class="sxs-lookup"><span data-stu-id="1aba6-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="1aba6-135">Instalación de USBX</span><span class="sxs-lookup"><span data-stu-id="1aba6-135">USBX Installation</span></span>

<span data-ttu-id="1aba6-136">USBX se instala mediante la clonación del repositorio de GitHub en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="1aba6-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="1aba6-137">La siguiente es la sintaxis típica para la creación de un clon del repositorio de USBX en el equipo:</span><span class="sxs-lookup"><span data-stu-id="1aba6-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="1aba6-138">También se puede descargar una copia del repositorio mediante el botón Descargar de la página principal de GitHub.</span><span class="sxs-lookup"><span data-stu-id="1aba6-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="1aba6-139">Además, hay instrucciones para compilar la biblioteca de USBX en la página principal del repositorio en línea.</span><span class="sxs-lookup"><span data-stu-id="1aba6-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="1aba6-140">Las siguientes instrucciones generales se aplican prácticamente a cualquier instalación:</span><span class="sxs-lookup"><span data-stu-id="1aba6-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="1aba6-141">Use el mismo directorio en el que antes ha instalado ThreadX en la unidad de disco duro del host.</span><span class="sxs-lookup"><span data-stu-id="1aba6-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="1aba6-142">Todos los nombres de USBX son únicos y no interfieren con la instalación previa de USBX.</span><span class="sxs-lookup"><span data-stu-id="1aba6-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
1. <span data-ttu-id="1aba6-143">Agregue una llamada a ***ux_system_initialize** _ en o cerca del principio de _*_tx_application_define_\*\*.</span><span class="sxs-lookup"><span data-stu-id="1aba6-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _*_tx_application_define_\*\*.</span></span> <span data-ttu-id="1aba6-144">Aquí es donde se inicializan los recursos de USBX.</span><span class="sxs-lookup"><span data-stu-id="1aba6-144">This is where the USBX resources are initialized.</span></span>
1. <span data-ttu-id="1aba6-145">Agregue una llamada a ***ux_device_stack_initialize*** .</span><span class="sxs-lookup"><span data-stu-id="1aba6-145">Add a call to \***ux_device_stack_initialize\*.**</span></span>
1. <span data-ttu-id="1aba6-146">Agregue una o varias llamadas para inicializar las clases USBX requeridas (ya sean clases de host o de dispositivos).</span><span class="sxs-lookup"><span data-stu-id="1aba6-146">Add one or more calls to initialize the required USBX classes (either host and/or devices classes)</span></span>
1. <span data-ttu-id="1aba6-147">Agregue una o varias llamadas para inicializar la controladoras de dispositivos disponibles en el sistema.</span><span class="sxs-lookup"><span data-stu-id="1aba6-147">Add one or more calls to initialize the device controller available in the system.</span></span>
1. <span data-ttu-id="1aba6-148">Puede que sea necesario modificar el archivo tx_low_level_initialize.c para agregar inicialización de hardware de bajo nivel e interrumpir el enrutamiento de vectores.</span><span class="sxs-lookup"><span data-stu-id="1aba6-148">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="1aba6-149">Al tratarse de algo específico de la plataforma de hardware, no se va a tratar aquí.</span><span class="sxs-lookup"><span data-stu-id="1aba6-149">This is specific to the hardware platform and will not be discussed here.|</span></span>
1. <span data-ttu-id="1aba6-150">También puede ser necesario compilar el código fuente de la aplicación y vincular a las bibliotecas en tiempo de ejecución de USBX y ThreadX (también se pueden necesitar FileX o Netx si se van a compilar la clase de almacenamiento USB o las clases de red USB), ux.a (o ux.lib) y tx.a (o tx.lib).</span><span class="sxs-lookup"><span data-stu-id="1aba6-150">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="1aba6-151">El resultado se puede descargar en el destino y ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="1aba6-151">The resulting can be downloaded to the target and executed!</span></span>

## <a name="configuration-options"></a><span data-ttu-id="1aba6-152">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="1aba6-152">Configuration Options</span></span>

<span data-ttu-id="1aba6-153">Hay varias opciones de configuración para compilar la biblioteca de USBX.</span><span class="sxs-lookup"><span data-stu-id="1aba6-153">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="1aba6-154">Todas las opciones se encuentran en ***ux_user.h***.</span><span class="sxs-lookup"><span data-stu-id="1aba6-154">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="1aba6-155">En la lista siguiente se detalla cada opción de configuración.</span><span class="sxs-lookup"><span data-stu-id="1aba6-155">The list below details each configuration option.</span></span>

| <span data-ttu-id="1aba6-156">Opción de&nbsp;configuración</span><span class="sxs-lookup"><span data-stu-id="1aba6-156">Configuration&nbsp;Option</span></span> | <span data-ttu-id="1aba6-157">Descripción</span><span class="sxs-lookup"><span data-stu-id="1aba6-157">Description</span></span> |
| --- | --- |
| <span data-ttu-id="1aba6-158">**UX_PERIODIC_RATE**</span><span class="sxs-lookup"><span data-stu-id="1aba6-158">**UX_PERIODIC_RATE**</span></span> | <span data-ttu-id="1aba6-159">Este valor representa el número de tics por segundo de una plataforma de hardware específica.</span><span class="sxs-lookup"><span data-stu-id="1aba6-159">This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="1aba6-160">El valor predeterminado es 1000, que indica un tic por milisegundo.</span><span class="sxs-lookup"><span data-stu-id="1aba6-160">The default is 1000 indicating 1 tick per millisecond.</span></span> |
| <span data-ttu-id="1aba6-161">**UX_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="1aba6-161">**UX_THREAD_STACK_SIZE**</span></span> | <span data-ttu-id="1aba6-162">Este valor es el tamaño de la pila en bytes para los subprocesos de USBX.</span><span class="sxs-lookup"><span data-stu-id="1aba6-162">This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="1aba6-163">Normalmente puede ser de 1024 bytes o de 2048 bytes, según el procesador usado y el controlador de host.</span><span class="sxs-lookup"><span data-stu-id="1aba6-163">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span> |
| <span data-ttu-id="1aba6-164">**UX_THREAD_PRIORITY_ENUM**</span><span class="sxs-lookup"><span data-stu-id="1aba6-164">**UX_THREAD_PRIORITY_ENUM**</span></span> | <span data-ttu-id="1aba6-165">Este es el valor de prioridad de ThreadX para los subprocesos de enumeración de USBX que supervisa la topología de bus.</span><span class="sxs-lookup"><span data-stu-id="1aba6-165">This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span> |
| <span data-ttu-id="1aba6-166">**UX_THREAD_PRIORITY_CLASS**</span><span class="sxs-lookup"><span data-stu-id="1aba6-166">**UX_THREAD_PRIORITY_CLASS**</span></span> | <span data-ttu-id="1aba6-167">Este es el valor de prioridad de ThreadX para los subprocesos de USBX estándar.</span><span class="sxs-lookup"><span data-stu-id="1aba6-167">This is the ThreadX priority value for the standard USBX threads.</span></span> |
| <span data-ttu-id="1aba6-168">**UX_THREAD_PRIORITY_KEYBOARD**</span><span class="sxs-lookup"><span data-stu-id="1aba6-168">**UX_THREAD_PRIORITY_KEYBOARD**</span></span> | <span data-ttu-id="1aba6-169">Este es el valor de prioridad de ThreadX para la clase de teclado HID de USBX.</span><span class="sxs-lookup"><span data-stu-id="1aba6-169">This is the ThreadX priority value for the USBX HID keyboard class.</span></span> |
| <span data-ttu-id="1aba6-170">**UX_THREAD_PRIORITY_DCD**</span><span class="sxs-lookup"><span data-stu-id="1aba6-170">**UX_THREAD_PRIORITY_DCD**</span></span> | <span data-ttu-id="1aba6-171">Este es el valor de prioridad de ThreadX para el subproceso de la controladora de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1aba6-171">This is the ThreadX priority value for the device controller thread.</span></span> |
| <span data-ttu-id="1aba6-172">**UX_NO_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="1aba6-172">**UX_NO_TIME_SLICE**</span></span> | <span data-ttu-id="1aba6-173">Este valor define realmente la porción de tiempo que se va a usar para los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="1aba6-173">This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="1aba6-174">Por ejemplo, si se ha definido en 0, el puerto de destino de ThreadX no utiliza porciones de tiempo.</span><span class="sxs-lookup"><span data-stu-id="1aba6-174">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span> |
| <span data-ttu-id="1aba6-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span><span class="sxs-lookup"><span data-stu-id="1aba6-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span></span> | <span data-ttu-id="1aba6-176">Este es el número máximo de clases USBX que se pueden registrar mediante ux_device_stack_class_register.</span><span class="sxs-lookup"><span data-stu-id="1aba6-176">This is the maximum number of USBX classes that can be registered via ux_device_stack_class_register.</span></span> |
| <span data-ttu-id="1aba6-177">**UX_MAX_SLAVE_LUN**</span><span class="sxs-lookup"><span data-stu-id="1aba6-177">**UX_MAX_SLAVE_LUN**</span></span> | <span data-ttu-id="1aba6-178">Este valor representa el número actual de unidades lógicas SCSI representadas en el controlador de la clase de almacenamiento de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1aba6-178">This value represents the current number of SCSI logical units represented in the device storage class driver.</span></span> |
| <span data-ttu-id="1aba6-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span><span class="sxs-lookup"><span data-stu-id="1aba6-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span></span> | <span data-ttu-id="1aba6-180">Si se define, la clase de almacenamiento administrará los comandos multimedia (MMC), es decir, DVD-ROM.</span><span class="sxs-lookup"><span data-stu-id="1aba6-180">If defined, the storage class will handle Multi-Media Commands (MMC) that is, DVD-ROM.</span></span> |
| <span data-ttu-id="1aba6-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span><span class="sxs-lookup"><span data-stu-id="1aba6-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span></span> | <span data-ttu-id="1aba6-182">Este valor representa el número de paquetes de NetX en el grupo de paquetes de la clase CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="1aba6-182">This value represents the number of NetX packets in the CDC-ECM class' packet pool.</span></span> <span data-ttu-id="1aba6-183">El valor predeterminado es 16.</span><span class="sxs-lookup"><span data-stu-id="1aba6-183">The default is 16.</span></span> |
| <span data-ttu-id="1aba6-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="1aba6-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span></span> | <span data-ttu-id="1aba6-185">Este valor representa el número máximo de bytes recibidos en un punto de conexión de control de la pila de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1aba6-185">This value represents the maximum number of bytes received on a control endpoint in the device stack.</span></span> <span data-ttu-id="1aba6-186">El valor predeterminado es 256 bytes, pero se puede reducir en entornos con restricción de memoria.</span><span class="sxs-lookup"><span data-stu-id="1aba6-186">The default is 256 bytes but can be reduced in memory constraint environments.</span></span> |
| <span data-ttu-id="1aba6-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="1aba6-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span></span> | <span data-ttu-id="1aba6-188">Este valor representa la longitud máxima en bytes de un informe de HID.</span><span class="sxs-lookup"><span data-stu-id="1aba6-188">This value represents the maximum length in bytes of a HID report.</span></span> |
| <span data-ttu-id="1aba6-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span><span class="sxs-lookup"><span data-stu-id="1aba6-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span></span> | <span data-ttu-id="1aba6-190">Este valor representa el número máximo de informes de HID que se pueden poner en cola a la vez.</span><span class="sxs-lookup"><span data-stu-id="1aba6-190">This value represents the maximum number of HID reports that can be queued at once.</span></span> |
| <span data-ttu-id="1aba6-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="1aba6-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span></span> | <span data-ttu-id="1aba6-192">Este valor representa el número máximo de bytes recibidos en un punto de conexión masivo de la pila de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1aba6-192">This value represents the maximum number of bytes received on a bulk endpoint in the device stack.</span></span> <span data-ttu-id="1aba6-193">El valor predeterminado es 4096 bytes, pero se puede reducir en entornos con restricción de memoria.</span><span class="sxs-lookup"><span data-stu-id="1aba6-193">The default is 4096 bytes but can be reduced in memory constraint environments.</span></span> |

## <a name="source-code-tree"></a><span data-ttu-id="1aba6-194">Árbol de código fuente</span><span class="sxs-lookup"><span data-stu-id="1aba6-194">Source Code Tree</span></span>

<span data-ttu-id="1aba6-195">Los archivos de USBX se proporcionan en varios directorios.</span><span class="sxs-lookup"><span data-stu-id="1aba6-195">The USBX files are provided in several directories.</span></span>

![Árbol de código fuente](media/usbx-device-stack/source-code-tree.png)

<span data-ttu-id="1aba6-197">Para que los archivos sean reconocibles por sus nombres, se ha adoptado la siguiente convención:</span><span class="sxs-lookup"><span data-stu-id="1aba6-197">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="1aba6-198">Nombre de sufijo de archivo</span><span class="sxs-lookup"><span data-stu-id="1aba6-198">File Suffix Name</span></span>  | <span data-ttu-id="1aba6-199">Descripción del archivo</span><span class="sxs-lookup"><span data-stu-id="1aba6-199">File description</span></span>                          |
| ----------------- | ----------------------------------------- |
| <span data-ttu-id="1aba6-200">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="1aba6-200">ux_host_stack</span></span>   | <span data-ttu-id="1aba6-201">archivos principales de pila de host de usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-201">usbx host stack core files</span></span>                |
| <span data-ttu-id="1aba6-202">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="1aba6-202">ux_host_class</span></span>   | <span data-ttu-id="1aba6-203">archivos de clases de pila de host de usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-203">usbx host stack classes files</span></span>             |
| <span data-ttu-id="1aba6-204">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="1aba6-204">ux_hcd</span></span>           | <span data-ttu-id="1aba6-205">archivos de controlador de pila de host de usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-205">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="1aba6-206">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="1aba6-206">ux_device_stack</span></span> | <span data-ttu-id="1aba6-207">archivos principales de pila de dispositivo de usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-207">usbx device stack core files</span></span>              |
| <span data-ttu-id="1aba6-208">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="1aba6-208">ux_device_class</span></span> | <span data-ttu-id="1aba6-209">archivos de clases de pila de dispositivo de usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-209">usbx device stack classes files</span></span>           |
| <span data-ttu-id="1aba6-210">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="1aba6-210">ux_dcd</span></span>           | <span data-ttu-id="1aba6-211">archivos de controlador de pila de host de usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-211">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="1aba6-212">ux_otg</span><span class="sxs-lookup"><span data-stu-id="1aba6-212">ux_otg</span></span>           | <span data-ttu-id="1aba6-213">archivos relacionados con el controlador de otg de usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-213">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="1aba6-214">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="1aba6-214">ux_pictbridge</span></span>    | <span data-ttu-id="1aba6-215">archivos de pictbridge de usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-215">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="1aba6-216">ux_utility</span><span class="sxs-lookup"><span data-stu-id="1aba6-216">ux_utility</span></span>       | <span data-ttu-id="1aba6-217">funciones de utilidad de usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-217">usbx utility functions</span></span>                    |
| <span data-ttu-id="1aba6-218">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="1aba6-218">demo_usbx</span></span>        | <span data-ttu-id="1aba6-219">archivos de demostración de USBX</span><span class="sxs-lookup"><span data-stu-id="1aba6-219">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="1aba6-220">Inicialización de recursos de USBX</span><span class="sxs-lookup"><span data-stu-id="1aba6-220">Initialization of USBX resources</span></span>

<span data-ttu-id="1aba6-221">USBX tiene su propio administrador de memoria.</span><span class="sxs-lookup"><span data-stu-id="1aba6-221">USBX has its own memory manager.</span></span> <span data-ttu-id="1aba6-222">La memoria debe asignarse a USBX antes de que se inicialice el lado de host o dispositivo de USBX.</span><span class="sxs-lookup"><span data-stu-id="1aba6-222">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="1aba6-223">El administrador de memoria de USBX puede hospedar sistemas en los que la memoria se puede almacenar en caché.</span><span class="sxs-lookup"><span data-stu-id="1aba6-223">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="1aba6-224">La siguiente función inicializa los recursos de memoria de USBX con 128 K de memoria normal y sin bloque independiente para la memoria segura en caché:</span><span class="sxs-lookup"><span data-stu-id="1aba6-224">The following function initializes USBX memory resources with 128 K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="1aba6-225">El prototipo de ux_system_initialize es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="1aba6-225">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

<span data-ttu-id="1aba6-226">Parámetros de entrada:</span><span class="sxs-lookup"><span data-stu-id="1aba6-226">Input parameters:</span></span>

| <span data-ttu-id="1aba6-227">Parámetro</span><span class="sxs-lookup"><span data-stu-id="1aba6-227">Parameter</span></span>                          | <span data-ttu-id="1aba6-228">Descripción</span><span class="sxs-lookup"><span data-stu-id="1aba6-228">Description</span></span>                             |
| ---------------------------------- | --------------------------------------- |
| <span data-ttu-id="1aba6-229">VOID \*regular_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="1aba6-229">VOID \*regular_memory_pool_start</span></span>    | <span data-ttu-id="1aba6-230">Inicio del bloque de memoria normal</span><span class="sxs-lookup"><span data-stu-id="1aba6-230">Beginning of the regular memory pool</span></span>    |
| <span data-ttu-id="1aba6-231">ULONG regular_memory_size</span><span class="sxs-lookup"><span data-stu-id="1aba6-231">ULONG regular_memory_size</span></span>          | <span data-ttu-id="1aba6-232">Tamaño del bloque de memoria normal</span><span class="sxs-lookup"><span data-stu-id="1aba6-232">Size of the regular memory pool</span></span>         |
| <span data-ttu-id="1aba6-233">VOID \*cache_safe_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="1aba6-233">VOID \*cache_safe_memory_pool_start</span></span> | <span data-ttu-id="1aba6-234">Inicio del bloque de memoria segura en caché</span><span class="sxs-lookup"><span data-stu-id="1aba6-234">Beginning of the cache safe memory pool</span></span> |
| <span data-ttu-id="1aba6-235">ULONG cache_safe_memory_size</span><span class="sxs-lookup"><span data-stu-id="1aba6-235">ULONG cache_safe_memory_size</span></span>       | <span data-ttu-id="1aba6-236">Tamaño del bloque de memoria segura en caché</span><span class="sxs-lookup"><span data-stu-id="1aba6-236">Size of the cache safe memory pool</span></span>      |

<span data-ttu-id="1aba6-237">No todos los sistemas requieren la definición de memoria segura en caché.</span><span class="sxs-lookup"><span data-stu-id="1aba6-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="1aba6-238">En este tipo de sistema, los valores que se pasan durante la inicialización del puntero de memoria se establecerán en UX_NULL y el tamaño del bloque en 0.</span><span class="sxs-lookup"><span data-stu-id="1aba6-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="1aba6-239">A continuación, USBX usará el bloque de memoria normal en lugar del bloque seguro en caché.</span><span class="sxs-lookup"><span data-stu-id="1aba6-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="1aba6-240">En un sistema en el que la memoria normal no es segura en caché y una controladora necesita hacer uso de la memoria DMA, es necesario definir un bloque de memoria en una zona segura en caché.</span><span class="sxs-lookup"><span data-stu-id="1aba6-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="1aba6-241">Anulación de inicialización de recursos de USBX</span><span class="sxs-lookup"><span data-stu-id="1aba6-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="1aba6-242">USBX se puede finalizar mediante la liberación de sus recursos.</span><span class="sxs-lookup"><span data-stu-id="1aba6-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="1aba6-243">Antes de finalizar USBX, todas las clases y los recursos del controlador deben finalizarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="1aba6-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="1aba6-244">La siguiente función anula la inicialización de los recursos de memoria de USBX:</span><span class="sxs-lookup"><span data-stu-id="1aba6-244">The following function uninitializes USBX memory resources:</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="1aba6-245">El prototipo de ux_system_initialize es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="1aba6-245">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a><span data-ttu-id="1aba6-246">Definición de la controladora de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="1aba6-246">Definition of USB Device Controller</span></span>

<span data-ttu-id="1aba6-247">Solo se puede definir una controladora de dispositivos USB en un momento dado para que funcione en modo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1aba6-247">Only one USB device controller can be defined at any time to operate in device mode.</span></span> <span data-ttu-id="1aba6-248">El archivo de inicialización de la aplicación debe contener esta definición.</span><span class="sxs-lookup"><span data-stu-id="1aba6-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="1aba6-249">La línea siguiente realiza la definición de una controladora USB genérica:</span><span class="sxs-lookup"><span data-stu-id="1aba6-249">The following line performs the definition of a generic usb controller:</span></span>

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

<span data-ttu-id="1aba6-250">La inicialización del dispositivo USB tiene el siguiente prototipo:</span><span class="sxs-lookup"><span data-stu-id="1aba6-250">The USB device initialization has the following prototype:</span></span>

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

<span data-ttu-id="1aba6-251">con los parámetros siguientes:</span><span class="sxs-lookup"><span data-stu-id="1aba6-251">with the following parameters:</span></span>

| <span data-ttu-id="1aba6-252">Parámetro</span><span class="sxs-lookup"><span data-stu-id="1aba6-252">Pararmeter</span></span>               | <span data-ttu-id="1aba6-253">Descripción</span><span class="sxs-lookup"><span data-stu-id="1aba6-253">Description</span></span>                      |
| ------------------------ | -------------------------------- |
| <span data-ttu-id="1aba6-254">ULONG dcd_io</span><span class="sxs-lookup"><span data-stu-id="1aba6-254">ULONG dcd_io</span></span>            | <span data-ttu-id="1aba6-255">Dirección de la E/S de la controladora</span><span class="sxs-lookup"><span data-stu-id="1aba6-255">Address of the controller IO</span></span>     |
| <span data-ttu-id="1aba6-256">ULONG dcd_irq</span><span class="sxs-lookup"><span data-stu-id="1aba6-256">ULONG dcd_irq</span></span>           | <span data-ttu-id="1aba6-257">Interrupción usada por la controladora</span><span class="sxs-lookup"><span data-stu-id="1aba6-257">Interrupt used by the controller</span></span> |
| <span data-ttu-id="1aba6-258">ULONG dcd_vbus_address</span><span class="sxs-lookup"><span data-stu-id="1aba6-258">ULONG dcd_vbus_address</span></span> | <span data-ttu-id="1aba6-259">Dirección del GPIO de VBUS</span><span class="sxs-lookup"><span data-stu-id="1aba6-259">Address of the VBUS GPIO</span></span>         |

<span data-ttu-id="1aba6-260">El ejemplo siguiente se corresponde con la inicialización de USBX en modo de dispositivo con la clase de dispositivo de almacenamiento y una controladora genérica:</span><span class="sxs-lookup"><span data-stu-id="1aba6-260">The following example is the initialization of USBX in device mode with the storage device class and a generic controller:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a><span data-ttu-id="1aba6-261">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="1aba6-261">Troubleshooting</span></span>

<span data-ttu-id="1aba6-262">USBX se entrega con un archivo de demostración y un entorno de simulación.</span><span class="sxs-lookup"><span data-stu-id="1aba6-262">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="1aba6-263">Siempre es conveniente que la plataforma de demostración se ejecute en primer lugar, ya sea en el hardware de destino o en una plataforma de demostración específica.</span><span class="sxs-lookup"><span data-stu-id="1aba6-263">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="1aba6-264">Id. de la versión de USBX</span><span class="sxs-lookup"><span data-stu-id="1aba6-264">USBX Version ID</span></span>

<span data-ttu-id="1aba6-265">La versión actual de USBX está disponible tanto para el software de usuario como para el de aplicación durante el tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="1aba6-265">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="1aba6-266">El programador puede obtener la versión de USBX si examina el archivo \***ux_port.h** _.</span><span class="sxs-lookup"><span data-stu-id="1aba6-266">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="1aba6-267">Además, este archivo también contiene un historial de versiones del puerto correspondiente.</span><span class="sxs-lookup"><span data-stu-id="1aba6-267">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="1aba6-268">El software de aplicación puede obtener la versión de USBX si examina la cadena global _ *_ _ux_version_id_* _, que se define en _\*_ux_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="1aba6-268">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
