---
title: 'Capítulo 2: Instalación de la pila de host de Azure RTOS USBX'
description: Obtenga información sobre cómo instalar la pila de host de USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377091"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a><span data-ttu-id="c4a2b-103">Capítulo 2: Instalación de la pila de host de Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="c4a2b-103">Chapter 2 - Azure RTOS USBX Host Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="c4a2b-104">Consideraciones sobre el host</span><span class="sxs-lookup"><span data-stu-id="c4a2b-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="c4a2b-105">Tipo de equipo</span><span class="sxs-lookup"><span data-stu-id="c4a2b-105">Computer Type</span></span>

<span data-ttu-id="c4a2b-106">El desarrollo insertado se suele realizar en equipos host Windows o Unix.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="c4a2b-107">Una vez que la aplicación está compilada, vinculada y colocada en el host, se descarga en el hardware de destino para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="c4a2b-108">Interfaces de descarga</span><span class="sxs-lookup"><span data-stu-id="c4a2b-108">Download Interfaces</span></span>

<span data-ttu-id="c4a2b-109">Normalmente, la descarga de destino se realiza por medio de una interfaz serie RS-232, aunque las interfaces paralelas, USB y Ethernet se están volviendo más populares.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-109">Usually, the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="c4a2b-110">Revise la documentación de la herramienta de desarrollo para ver las opciones disponibles.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="c4a2b-111">Herramientas de depuración</span><span class="sxs-lookup"><span data-stu-id="c4a2b-111">Debugging Tools</span></span>

<span data-ttu-id="c4a2b-112">La depuración se suele realizar con el mismo vínculo que la descarga de la imagen del programa.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="c4a2b-113">Existen diversos depuradores, que abarcan desde pequeños programas de supervisión que se ejecutan en el destino, hasta herramientas de supervisión de depuración en segundo plano (BDM) y de emulación en circuito (ICE).</span><span class="sxs-lookup"><span data-stu-id="c4a2b-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="c4a2b-114">La herramienta ICE proporciona la depuración más sólida del hardware de destino real.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="c4a2b-115">Espacio en disco duro requerido</span><span class="sxs-lookup"><span data-stu-id="c4a2b-115">Required Hard Disk Space</span></span>

<span data-ttu-id="c4a2b-116">El código fuente de USBX se entrega en formato ASCII y requiere aproximadamente 500 KB de espacio en el disco duro del equipo host.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="c4a2b-117">Consideraciones sobre el destino</span><span class="sxs-lookup"><span data-stu-id="c4a2b-117">Target Considerations</span></span>

<span data-ttu-id="c4a2b-118">USBX requiere entre 24 KB y 64 KB de memoria de solo lectura (ROM) en el destino en modo de host.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="c4a2b-119">La cantidad de memoria necesaria depende del tipo de controlador utilizado y de las clases USB vinculadas a USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="c4a2b-120">Se requieren otros 32 KB de memoria de acceso aleatorio (RAM) del destino para las estructuras de datos globales de USBX y el bloque de memoria.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="c4a2b-121">Este bloque de memoria también se puede ajustar en función del número esperado de dispositivos en el USB y el tipo de controlador USB.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="c4a2b-122">El lado del dispositivo USBX requiere aproximadamente entre 10 y 12 KB de ROM según el tipo de controlador de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="c4a2b-123">El uso de memoria RAM depende del tipo de clase emulada por el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="c4a2b-124">USBX también se basa en semáforos, exclusiones mutuas y subprocesos de ThreadX para la protección de varios subprocesos, y en la suspensión de E/S y el procesamiento periódico para la supervisión de la topología del bus USB.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="c4a2b-125">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="c4a2b-125">Product Distribution</span></span>

<span data-ttu-id="c4a2b-126">Azure RTOS USBX se puede obtener desde el repositorio de código fuente público en <https://github.com/azure-rtos/usbx/>.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="c4a2b-127">A continuación se muestra una lista de varios archivos importantes del repositorio:</span><span class="sxs-lookup"><span data-stu-id="c4a2b-127">The following is a list of several important files in the repository:</span></span>

- <span data-ttu-id="c4a2b-128">***ux_api.h***: este archivo de encabezado de C contiene todas las equivalencias del sistema, estructuras de datos y prototipos del servicio.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
- <span data-ttu-id="c4a2b-129">***ux_port.h***: este archivo de encabezado de C contiene todas las definiciones de datos y estructuras específicas de la herramienta de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
- <span data-ttu-id="c4a2b-130">***ux.lib***: se trata de la versión binaria de la biblioteca de C de USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-130">***ux.lib***: This is the binary version of the USBX C library.</span></span> <span data-ttu-id="c4a2b-131">Se distribuye con el paquete estándar.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-131">It is distributed with the standard package.</span></span>
- <span data-ttu-id="c4a2b-132">***demo_usbx.c***: archivo de C que contiene una demostración de USBX simple.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="c4a2b-133">Todos los nombres de archivo están en minúsculas.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-133">All filenames are in lower-case.</span></span> <span data-ttu-id="c4a2b-134">Esta convención de nomenclatura facilita la conversión de los comandos en plataformas de desarrollo de Unix.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="c4a2b-135">Instalación de USBX</span><span class="sxs-lookup"><span data-stu-id="c4a2b-135">USBX Installation</span></span>

<span data-ttu-id="c4a2b-136">USBX se instala mediante la clonación del repositorio de GitHub en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="c4a2b-137">La siguiente es la sintaxis típica para la creación de un clon del repositorio de USBX en el equipo:</span><span class="sxs-lookup"><span data-stu-id="c4a2b-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```powershell
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="c4a2b-138">También se puede descargar una copia del repositorio mediante el botón Descargar de la página principal de GitHub.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="c4a2b-139">Además, hay instrucciones para compilar la biblioteca de USBX en la página principal del repositorio en línea.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="c4a2b-140">Las siguientes instrucciones generales se aplican prácticamente a cualquier instalación:</span><span class="sxs-lookup"><span data-stu-id="c4a2b-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="c4a2b-141">Use el mismo directorio en el que antes ha instalado ThreadX en la unidad de disco duro del host.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="c4a2b-142">Todos los nombres de USBX son únicos y no interfieren con la instalación previa de USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
2. <span data-ttu-id="c4a2b-143">Agregue una llamada a \***ux_system_initialize** _ al principio o cerca del principio de _ *_tx_application_define_.* \* Aquí es donde se inicializan los recursos de USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _ *_tx_application_define_.** This is where the USBX resources are initialized.</span></span>
3. <span data-ttu-id="c4a2b-144">Agregue una llamada a \***ux_host_stack_initialize\*.**</span><span class="sxs-lookup"><span data-stu-id="c4a2b-144">Add a call to \***ux_host_stack_initialize\*.**</span></span>
4. <span data-ttu-id="c4a2b-145">Agregue una o más llamadas para inicializar la instancia requerida de USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-145">Add one or more calls to initialize the required USBX.</span></span>
5. <span data-ttu-id="c4a2b-146">Agregue una o más llamadas para inicializar los controladores de host disponibles en el sistema.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-146">Add one or more calls to initialize the host controllers available in the system.</span></span>
6. <span data-ttu-id="c4a2b-147">Puede que sea necesario modificar el archivo tx_low_level_initialize.c para agregar inicialización de hardware de bajo nivel e interrumpir el enrutamiento de vectores.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-147">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="c4a2b-148">Al tratarse de algo específico de la plataforma de hardware, no se va a tratar aquí.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-148">This is specific to the hardware platform and will not be discussed here.</span></span>
7. <span data-ttu-id="c4a2b-149">También puede ser necesario compilar el código fuente de la aplicación y vincular a las bibliotecas en tiempo de ejecución de USBX y ThreadX (también se pueden necesitar FileX o Netx si se van a compilar la clase de almacenamiento USB o las clases de red USB), ux.a (o ux.lib) y tx.a (o tx.lib).</span><span class="sxs-lookup"><span data-stu-id="c4a2b-149">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="c4a2b-150">El resultado se puede descargar en el destino y ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-150">The resulting can be downloaded to the target and executed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="c4a2b-151">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="c4a2b-151">Configuration Options</span></span>

<span data-ttu-id="c4a2b-152">Hay varias opciones de configuración para compilar la biblioteca de USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-152">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="c4a2b-153">Todas las opciones se encuentran en ***ux_user.h***.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-153">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="c4a2b-154">En la lista siguiente se detalla cada opción de configuración.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-154">The list below details each configuration option.</span></span>


- <span data-ttu-id="c4a2b-155">**UX_PERIODIC_RATE**: este valor representa el número de tics por segundo de una plataforma de hardware específica.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-155">**UX_PERIODIC_RATE**: This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="c4a2b-156">El valor predeterminado es 1000, que indica un tic por milisegundo.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-156">The default is 1000 indicating one tick per millisecond.</span></span>
- <span data-ttu-id="c4a2b-157">**UX_MAX_CLASS_DRIVER**: este valor es el número máximo de clases que USBX puede cargar.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-157">**UX_MAX_CLASS_DRIVER**: This value is the maximum number of classes that can be loaded by USBX.</span></span> <span data-ttu-id="c4a2b-158">Este valor representa el contenedor de clases y no el número de instancias de una clase.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-158">This value represents the class container and not the number of instances of a class.</span></span> <span data-ttu-id="c4a2b-159">Por ejemplo, si una implementación concreta de USBX necesita la clase hub, la clase de impresora y la clase de almacenamiento, el valor de UX_MAX_CLASS_DRIVER se puede establecer en 3, independientemente del número de dispositivos que pertenezcan a estas clases.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-159">For instance, if a particular implementation of USBX needs the hub class, the printer class, and the storage class, then the UX_MAX_CLASS_DRIVER value can be set to 3 regardless of the number of devices that belong to these classes.</span></span>
- <span data-ttu-id="c4a2b-160">**UX_MAX_HCD**: este valor representa el número de controladores de host diferentes que están disponibles en el sistema.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-160">**UX_MAX_HCD**: This value represents the number of different host controllers that are available in the system.</span></span> <span data-ttu-id="c4a2b-161">Para la compatibilidad con USB 1.1, este valor en general será 1.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-161">For USB 1.1 support, this value will mostly be 1.</span></span> <span data-ttu-id="c4a2b-162">Para la compatibilidad con USB 2.0, este valor puede ser superior a 1.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-162">For USB 2.0 support this value can be more than 1.</span></span> <span data-ttu-id="c4a2b-163">Este valor representa el número de controladores de host simultáneos que se ejecutan a la vez.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-163">This value represents the number of concurrent host controllers running at the same time.</span></span> <span data-ttu-id="c4a2b-164">Si, por ejemplo, hay dos instancias de OHCI o un controlador EHCI y otro OHCI en ejecución, UX_MAX_HCD debe establecerse en 2.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-164">If for instance, there are two instances of OHCI running or one EHCI and one OHCI controllers running, the UX_MAX_HCD should be set to 2.</span></span> 
- <span data-ttu-id="c4a2b-165">**UX_MAX_DEVICES**: este valor representa el número máximo de dispositivos que se pueden conectar al USB.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-165">**UX_MAX_DEVICES**: This value represents the maximum number of devices that can be attached to the USB.</span></span> <span data-ttu-id="c4a2b-166">Normalmente, el número máximo teórico en un solo USB es 127 dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-166">Normally, the theoretical maximum number on a single USB is 127 devices.</span></span> <span data-ttu-id="c4a2b-167">Este valor se puede reducir verticalmente para conservar memoria.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-167">This value can be scaled down to conserve memory.</span></span> <span data-ttu-id="c4a2b-168">Debe tenerse en consideración que este valor representa el número total de dispositivos, independientemente del número de buses USB del sistema.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-168">It should be noted that this value represents the total number of devices regardless of the number of USB buses in the system.</span></span>
- <span data-ttu-id="c4a2b-169">**UX_MAX_ED**: este valor representa el número máximo de ED del grupo de controladores.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-169">**UX_MAX_ED**: This value represents the maximum number of EDs in the controller pool.</span></span> <span data-ttu-id="c4a2b-170">Este número solo se asigna a un controlador.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-170">This number is assigned to one controller only.</span></span> <span data-ttu-id="c4a2b-171">Si hay varias instancias de controladores presentes, cada controlador individual usa este valor.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-171">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="c4a2b-172">**UX_MAX_TD y UX_MAX_ISO_TD**: este valor representa el número máximo de TD normales e isocrónicos del grupo de controladores.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-172">**UX_MAX_TD and UX_MAX_ISO_TD**: This value represents the maximum number of regular and isochronous TDs in the controller pool.</span></span> <span data-ttu-id="c4a2b-173">Este número solo se asigna a un controlador.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-173">This number is assigned to one controller only.</span></span> <span data-ttu-id="c4a2b-174">Si hay varias instancias de controladores presentes, cada controlador individual usa este valor.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-174">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="c4a2b-175">**UX_THREAD_STACK_SIZE**: este valor es el tamaño de la pila en bytes para los subprocesos de USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-175">**UX_THREAD_STACK_SIZE**: This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="c4a2b-176">Normalmente puede ser de 1024 bytes o de 2048 bytes, según el procesador usado y el controlador de host.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-176">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span>
- <span data-ttu-id="c4a2b-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: este valor es el tamaño de la pila del subproceso de enumeración del host USB.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: This value is the stack size of the USB host enumeration thread.</span></span> <span data-ttu-id="c4a2b-178">Si no se establece este símbolo, el tamaño de la pila del subproceso de enumeración del host de USBX se establece en **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-178">If this symbol I not set, the USBX host enumeration thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span> 
- <span data-ttu-id="c4a2b-179">**UX_HOST_ENUM_THREAD_STACK_SIZE**: este valor es el tamaño de la pila del subproceso de HCD del host USB.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: This value is the stack size of the USB host HCD thread.</span></span> <span data-ttu-id="c4a2b-180">Si no se establece este símbolo, el tamaño de la pila del subproceso de HCD del host de USBX se establece en **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-180">If this symbol I not set, the USBX host HCD thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span>
- <span data-ttu-id="c4a2b-181">**UX_THREAD_PRIORITY_ENUM**: este es el valor de prioridad de ThreadX para los subprocesos de enumeración de USBX que supervisa la topología de bus.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-181">**UX_THREAD_PRIORITY_ENUM**: This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span>
- <span data-ttu-id="c4a2b-182">**UX_THREAD_PRIORITY_CLASS**: este es el valor de prioridad de ThreadX para los subprocesos de USBX estándar.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-182">**UX_THREAD_PRIORITY_CLASS**: This is the ThreadX priority value for the standard USBX threads.</span></span>
- <span data-ttu-id="c4a2b-183">**UX_THREAD_PRIORITY_KEYBOARD**: este es el valor de prioridad de ThreadX para la clase de teclado HID de USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-183">**UX_THREAD_PRIORITY_KEYBOARD**: This is the ThreadX priority value for the USBX HID keyboard class.</span></span>
- <span data-ttu-id="c4a2b-184">**UX_THREAD_PRIORITY_HCD**: este es el valor de prioridad de ThreadX para el subproceso del controlador de host.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-184">**UX_THREAD_PRIORITY_HCD**: This is the ThreadX priority value for the host controller thread.</span></span>
- <span data-ttu-id="c4a2b-185">**UX_NO_TIME_SLICE**: este valor define realmente la porción de tiempo que se va a usar para los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-185">**UX_NO_TIME_SLICE**: This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="c4a2b-186">Por ejemplo, si se ha definido en 0, el puerto de destino de ThreadX no utiliza porciones de tiempo.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-186">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span>
- <span data-ttu-id="c4a2b-187">**UX_MAX_HOST_LUN**: este valor representa el número máximo de unidades lógicas de SCSI representadas en el controlador de la clase de almacenamiento del host.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-187">**UX_MAX_HOST_LUN**: This value represents the maximum number of SCSI logical units represented in the host storage class driver.</span></span>
- <span data-ttu-id="c4a2b-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: si se ha definido, este valor incluye código para controlar los dispositivos de almacenamiento que utilizan el protocolo CB o CBI (por ejemplo, disquetes).</span><span class="sxs-lookup"><span data-stu-id="c4a2b-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: If defined, this value includes code to handle storage devices that use the CB or CBI protocol (such as floppy disks).</span></span> <span data-ttu-id="c4a2b-189">Está desactivado de manera predeterminada porque estos protocolos están obsoletos y han sido reemplazados por el protocolo BOT, que prácticamente usan todos los dispositivos de almacenamiento modernos.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-189">It is off by default because these protocols are obsolete, being superseded by the Bulk Only Transport (BOT protocol, which virtually all modern storage devices use.</span></span>
- <span data-ttu-id="c4a2b-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: si se ha definido, este valor hace que ux_host_class_hid_keyboard_key_get solo comunique cambios en las teclas, es decir, pulsaciones y liberaciones.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: If defined, this value causes ux_host_class_hid_keyboard_key_get to only report key changes that is, key presses and key releases.</span></span> <span data-ttu-id="c4a2b-191">De manera predeterminada, solo comunica cuando se pulsa una tecla.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-191">By default, it only reports when a key is down.</span></span>
- <span data-ttu-id="c4a2b-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: solo se utiliza si se ha definido **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="c4a2b-193">Si se ha definido, hace que ux_host_class_hid_keyboard_key_get solo comunique cambios de pulsación de tecla; los cambios de liberación de tecla no se notifican.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-193">If defined, causes ux_host_class_hid_keyboard_key_get to only report key pressed/down changes; key released/up changes are not reported.</span></span>
- <span data-ttu-id="c4a2b-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: solo se utiliza si se ha definido **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="c4a2b-195">Si se ha definido, hace que ux_host_class_hid_keyboard_key_get comunique los cambios en las teclas de bloqueo (BloqMayús/BloqNum/BloqDespl).</span><span class="sxs-lookup"><span data-stu-id="c4a2b-195">If defined, causes ux_host_class_hid_keyboard_key_get to report lock key (CapsLock/NumLock/ScrollLock) changes.</span></span>
- <span data-ttu-id="c4a2b-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: solo se utiliza si se ha definido **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="c4a2b-197">Si se ha definido, hace que ux_host_class_hid_keyboard_key_get comunique los cambios en las teclas modificadoras (Ctrl/Alt/Mayús/GUI).</span><span class="sxs-lookup"><span data-stu-id="c4a2b-197">If defined, causes ux_host_class_hid_keyboard_key_get to report modifier key (Ctrl/Alt/Shift/GUI) changes.</span></span>
- <span data-ttu-id="c4a2b-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: si se ha definido, este valor representa el número de paquetes de la clase de host CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: If defined, this value represents the number of packets in the CDC-ECM host class.</span></span> <span data-ttu-id="c4a2b-199">El valor predeterminado es 16.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-199">The default is 16.</span></span>

## <a name="source-code-tree"></a><span data-ttu-id="c4a2b-200">Árbol de código fuente</span><span class="sxs-lookup"><span data-stu-id="c4a2b-200">Source Code Tree</span></span>

<span data-ttu-id="c4a2b-201">Los archivos de USBX se proporcionan en varios directorios.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-201">The USBX files are provided in several directories.</span></span>

![Árbol de código fuente](media/usbx-host-stack/source-code-tree.png)

<span data-ttu-id="c4a2b-203">Para que los archivos sean reconocibles por sus nombres, se ha adoptado la siguiente convención:</span><span class="sxs-lookup"><span data-stu-id="c4a2b-203">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="c4a2b-204">Nombre de sufijo de archivo</span><span class="sxs-lookup"><span data-stu-id="c4a2b-204">File Suffix Name</span></span> | <span data-ttu-id="c4a2b-205">Descripción del archivo</span><span class="sxs-lookup"><span data-stu-id="c4a2b-205">File description</span></span>                          |
| ---------------- | ----------------------------------------- |
| <span data-ttu-id="c4a2b-206">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="c4a2b-206">ux_host_stack</span></span>    | <span data-ttu-id="c4a2b-207">archivos principales de pila de host de usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-207">usbx host stack core files</span></span>                |
| <span data-ttu-id="c4a2b-208">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="c4a2b-208">ux_host_class</span></span>    | <span data-ttu-id="c4a2b-209">archivos de clases de pila de host de usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-209">usbx host stack classes files</span></span>             |
| <span data-ttu-id="c4a2b-210">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="c4a2b-210">ux_hcd</span></span>           | <span data-ttu-id="c4a2b-211">archivos de controlador de pila de host de usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-211">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="c4a2b-212">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="c4a2b-212">ux_device_stack</span></span>  | <span data-ttu-id="c4a2b-213">archivos principales de pila de dispositivo de usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-213">usbx device stack core files</span></span>              |
| <span data-ttu-id="c4a2b-214">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="c4a2b-214">ux_device_class</span></span>  | <span data-ttu-id="c4a2b-215">archivos de clases de pila de dispositivo de usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-215">usbx device stack classes files</span></span>           |
| <span data-ttu-id="c4a2b-216">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="c4a2b-216">ux_dcd</span></span>           | <span data-ttu-id="c4a2b-217">archivos de controlador de pila de host de usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-217">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="c4a2b-218">ux_otg</span><span class="sxs-lookup"><span data-stu-id="c4a2b-218">ux_otg</span></span>           | <span data-ttu-id="c4a2b-219">archivos relacionados con el controlador de otg de usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-219">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="c4a2b-220">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="c4a2b-220">ux_pictbridge</span></span>    | <span data-ttu-id="c4a2b-221">archivos de pictbridge de usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-221">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="c4a2b-222">ux_utility</span><span class="sxs-lookup"><span data-stu-id="c4a2b-222">ux_utility</span></span>       | <span data-ttu-id="c4a2b-223">funciones de utilidad de usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-223">usbx utility functions</span></span>                    |
| <span data-ttu-id="c4a2b-224">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="c4a2b-224">demo_usbx</span></span>        | <span data-ttu-id="c4a2b-225">archivos de demostración de USBX</span><span class="sxs-lookup"><span data-stu-id="c4a2b-225">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="c4a2b-226">Inicialización de recursos de USBX</span><span class="sxs-lookup"><span data-stu-id="c4a2b-226">Initialization of USBX resources</span></span>

<span data-ttu-id="c4a2b-227">USBX tiene su propio administrador de memoria.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-227">USBX has its own memory manager.</span></span> <span data-ttu-id="c4a2b-228">La memoria debe asignarse a USBX antes de que se inicialice el lado de host o dispositivo de USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-228">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="c4a2b-229">El administrador de memoria de USBX puede hospedar sistemas en los que la memoria se puede almacenar en caché.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-229">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="c4a2b-230">La siguiente función inicializa los recursos de memoria de USBX con 128 K de memoria normal y sin bloque independiente para la memoria segura en caché:</span><span class="sxs-lookup"><span data-stu-id="c4a2b-230">The following function initializes USBX memory resources with 128K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="c4a2b-231">El prototipo de ux_system_initialize es como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-231">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a><span data-ttu-id="c4a2b-232">Parámetros de entrada:</span><span class="sxs-lookup"><span data-stu-id="c4a2b-232">Input parameters:</span></span>

- <span data-ttu-id="c4a2b-233">**regular_memory_pool_start** Inicio del bloque de memoria normal.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-233">**regular_memory_pool_start** Beginning of the regular memory pool.</span></span>
- <span data-ttu-id="c4a2b-234">**regular_memory_size** Tamaño del bloque de memoria normal.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-234">**regular_memory_size** Size of the regular memory pool.</span></span>
- <span data-ttu-id="c4a2b-235">**cache_safe_memory_pool_start** Inicio del bloque de memoria segura en caché.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-235">**cache_safe_memory_pool_start** Beginning of the cache safe memory pool.</span></span>
- <span data-ttu-id="c4a2b-236">**cache_safe_memory_size** Tamaño del bloque de memoria segura en caché.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-236">**cache_safe_memory_size** Size of the cache safe memory pool.</span></span>    |

<span data-ttu-id="c4a2b-237">No todos los sistemas requieren la definición de memoria segura en caché.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="c4a2b-238">En este tipo de sistema, los valores que se pasan durante la inicialización del puntero de memoria se establecerán en UX_NULL y el tamaño del bloque en 0.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="c4a2b-239">A continuación, USBX usará el bloque de memoria normal en lugar del bloque seguro en caché.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="c4a2b-240">En un sistema en el que la memoria normal no es segura en caché y un controlador necesita hacer uso de la memoria DMA (como los controladores OHCI y EHCI, entre otros), es necesario definir un bloque de memoria en una zona segura en caché.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory (like OHCI, EHCI controllers amongst others) it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="c4a2b-241">Anulación de inicialización de recursos de USBX</span><span class="sxs-lookup"><span data-stu-id="c4a2b-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="c4a2b-242">USBX se puede finalizar mediante la liberación de sus recursos.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="c4a2b-243">Antes de finalizar USBX, todas las clases y los recursos del controlador deben finalizarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="c4a2b-244">La siguiente función anula la inicialización de los recursos de memoria de USBX:</span><span class="sxs-lookup"><span data-stu-id="c4a2b-244">The following function uninitializes USBX memory resources :</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="c4a2b-245">El prototipo de ux_system_initialize es como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-245">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a><span data-ttu-id="c4a2b-246">Definición de controladores de host USB</span><span class="sxs-lookup"><span data-stu-id="c4a2b-246">Definition of USB Host Controllers</span></span>

<span data-ttu-id="c4a2b-247">Es necesario definir al menos un controlador de host USB para que USBX funcione en modo de host.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-247">It is required to define at least one USB host controller for USBX to operate in host mode.</span></span> <span data-ttu-id="c4a2b-248">El archivo de inicialización de la aplicación debe contener esta definición.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="c4a2b-249">La línea siguiente realiza la definición de un controlador de host genérico.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-249">The following line performs the definition of a generic host controller.</span></span>

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

<span data-ttu-id="c4a2b-250">ux_host_stack_hcd_register tiene el siguiente prototipo.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-250">The ux_host_stack_hcd_register has the following prototype.</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

<span data-ttu-id="c4a2b-251">La función ux_host_stack_hcd_register tiene los parámetros siguientes.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-251">The ux_host_stack_hcd_register function has the following parameters.</span></span>

- <span data-ttu-id="c4a2b-252">**hcd_name**: cadena del nombre del controlador</span><span class="sxs-lookup"><span data-stu-id="c4a2b-252">**hcd_name**: string of the controller name</span></span>
- <span data-ttu-id="c4a2b-253">**hcd_initialize_function**: función de inicialización del controlador</span><span class="sxs-lookup"><span data-stu-id="c4a2b-253">**hcd_initialize_function**: initialization function of the controller</span></span>
- <span data-ttu-id="c4a2b-254">**hcd_param1**: normalmente el valor de E/S o la memoria usada por el controlador</span><span class="sxs-lookup"><span data-stu-id="c4a2b-254">**hcd_param1**: usually the IO value or Memory used by the controller</span></span>
- <span data-ttu-id="c4a2b-255">**hcd_param2**: normalmente la IRQ usada por el controlador</span><span class="sxs-lookup"><span data-stu-id="c4a2b-255">**hcd_param2**: usually the IRQ used by the controller</span></span>

<span data-ttu-id="c4a2b-256">En el ejemplo anterior:</span><span class="sxs-lookup"><span data-stu-id="c4a2b-256">In our previous example:</span></span>

- <span data-ttu-id="c4a2b-257">"ux_hcd_controller" es el nombre del controlador</span><span class="sxs-lookup"><span data-stu-id="c4a2b-257">"ux_hcd_controller" is the name of the controller</span></span>
- <span data-ttu-id="c4a2b-258">"ux_hcd_controller_initialize" es la rutina de inicialización del controlador de host</span><span class="sxs-lookup"><span data-stu-id="c4a2b-258">"ux_hcd_controller_initialize" is the initialization routine for the host controller</span></span>
- <span data-ttu-id="c4a2b-259">0xd0000 es la dirección en la que los registros del controlador de host están visibles en la memoria</span><span class="sxs-lookup"><span data-stu-id="c4a2b-259">0xd0000 is the address at which the host controller registers are visible in memory</span></span>
- <span data-ttu-id="c4a2b-260">y 0x0A es la IRQ usada por el controlador de host.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-260">and 0x0a is the IRQ used by the host controller.</span></span>

<span data-ttu-id="c4a2b-261">A continuación se proporciona un ejemplo de la inicialización de USBX en modo de host con un controlador de host y varias clases.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-261">Following is an example of the initialization of USBX in host mode with one host controller and several classes.</span></span>

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a><span data-ttu-id="c4a2b-262">Definición de clases de host</span><span class="sxs-lookup"><span data-stu-id="c4a2b-262">Definition of Host Classes</span></span>

<span data-ttu-id="c4a2b-263">Es necesario definir una o varias clases de host con USBX.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-263">It is required to define one or more host classes with USBX.</span></span> <span data-ttu-id="c4a2b-264">Se necesita una clase USB para activar un dispositivo USB después de que la pila USB haya configurado el dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-264">A USB class is required to drive a USB device after the USB stack has configured the USB device.</span></span> <span data-ttu-id="c4a2b-265">Una clase USB es específica del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-265">A USB class is specific to the device.</span></span> <span data-ttu-id="c4a2b-266">Pueden ser necesarias una o más clases para activar un dispositivo USB en función del número de interfaces que contengan los descriptores del dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-266">One or more classes may be required to drive a USB device depending on the number of interfaces contained in the USB device descriptors.</span></span>

<span data-ttu-id="c4a2b-267">Este es un ejemplo del registro de la clase hub.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-267">This is an example of the registration of the HUB class.</span></span>

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

<span data-ttu-id="c4a2b-268">La función ux_host_class_register tiene el siguiente prototipo.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-268">The function ux_host_class_register has the following prototype.</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- <span data-ttu-id="c4a2b-269">**class_name** es el nombre de la clase</span><span class="sxs-lookup"><span data-stu-id="c4a2b-269">**class_name** is the name of the class</span></span>
- <span data-ttu-id="c4a2b-270">**class_entry_address** es el punto de entrada de la clase</span><span class="sxs-lookup"><span data-stu-id="c4a2b-270">**class_entry_address** is the entry point of the class</span></span>

<span data-ttu-id="c4a2b-271">En el ejemplo de la inicialización de la clase hub:</span><span class="sxs-lookup"><span data-stu-id="c4a2b-271">In the example of the HUB class initialization:</span></span>

- <span data-ttu-id="c4a2b-272">"ux_host_class_hub" es el nombre de la clase hub</span><span class="sxs-lookup"><span data-stu-id="c4a2b-272">"ux_host_class_hub" is the name of the hub class</span></span>
- <span data-ttu-id="c4a2b-273">ux_host_class_hub_entry es el punto de entrada de la clase hub</span><span class="sxs-lookup"><span data-stu-id="c4a2b-273">ux_host_class_hub_entry is the entry point of the HUB class.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="c4a2b-274">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="c4a2b-274">Troubleshooting</span></span>

<span data-ttu-id="c4a2b-275">USBX se entrega con un archivo de demostración y un entorno de simulación.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-275">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="c4a2b-276">Siempre es conveniente que la plataforma de demostración se ejecute en primer lugar, ya sea en el hardware de destino o en una plataforma de demostración específica.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-276">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

<span data-ttu-id="c4a2b-277">Si el sistema de demostración no funciona, pruebe los siguientes pasos para delimitar el problema.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-277">If the demonstration system does not work, try the following things to narrow the problem.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="c4a2b-278">Id. de la versión de USBX</span><span class="sxs-lookup"><span data-stu-id="c4a2b-278">USBX Version ID</span></span>

<span data-ttu-id="c4a2b-279">La versión actual de USBX está disponible tanto para el software de usuario como para el de aplicación durante el tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-279">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="c4a2b-280">El programador puede obtener la versión de USBX si examina el archivo \***ux_port.h** _.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-280">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="c4a2b-281">Además, este archivo también contiene un historial de versiones del puerto correspondiente.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-281">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="c4a2b-282">El software de aplicación puede obtener la versión de USBX si examina la cadena global _ *_ _ux_version_id_* _, que se define en _\*_ux_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="c4a2b-282">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
