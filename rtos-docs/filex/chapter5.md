---
title: 'Capítulo 5: Controladores de E/S para Azure RTOS FileX'
description: Este capítulo contiene una descripción de los controladores de E/S de Azure RTOS FileX y está diseñado para ayudar a los desarrolladores a escribir controladores específicos de la aplicación.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8f2ef697f68a269b24a34147a4bc076b8a2b1660
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550089"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a><span data-ttu-id="99bbb-103">Capítulo 5: Controladores de E/S para Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="99bbb-103">Chapter 5 - I/O Drivers for Azure RTOS FileX</span></span>

<span data-ttu-id="99bbb-104">Este capítulo contiene una descripción de los controladores de E/S de Azure RTOS FileX y está diseñado para ayudar a los desarrolladores a escribir controladores específicos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="99bbb-104">This chapter contains a description of I/O drivers for Azure RTOS FileX and is designed to help developers write application-specific drivers.</span></span>

## <a name="io-driver-introduction"></a><span data-ttu-id="99bbb-105">Introducción a los controladores de E/S</span><span class="sxs-lookup"><span data-stu-id="99bbb-105">I/O Driver Introduction</span></span>

<span data-ttu-id="99bbb-106">FileX admite varios dispositivos multimedia.</span><span class="sxs-lookup"><span data-stu-id="99bbb-106">FileX supports multiple media devices.</span></span> <span data-ttu-id="99bbb-107">La estructura FX_MEDIA define todo lo necesario para administrar un dispositivo multimedia.</span><span class="sxs-lookup"><span data-stu-id="99bbb-107">The FX_MEDIA structure defines everything required to manage a media device.</span></span> <span data-ttu-id="99bbb-108">Esta estructura contiene toda la información multimedia, incluido el controlador de E/S específico del elemento multimedia y los parámetros asociados para pasar información, y el estado entre el controlador y FileX.</span><span class="sxs-lookup"><span data-stu-id="99bbb-108">This structure contains all media information, including the media-specific I/O driver and associated parameters for passing information and status between the driver and FileX.</span></span> <span data-ttu-id="99bbb-109">En la mayoría de los sistemas, hay un controlador de E/S único para cada instancia de elemento multimedia de FileX.</span><span class="sxs-lookup"><span data-stu-id="99bbb-109">In most systems, there is a unique I/O driver for each FileX media instance.</span></span>

## <a name="io-driver-entry"></a><span data-ttu-id="99bbb-110">Entrada de controlador de E/S</span><span class="sxs-lookup"><span data-stu-id="99bbb-110">I/O Driver Entry</span></span>

<span data-ttu-id="99bbb-111">Cada controlador de E/S de FileX tiene una sola función de entrada definida por la llamada de servicio ***fx_media_open***.</span><span class="sxs-lookup"><span data-stu-id="99bbb-111">Each FileX I/O driver has a single entry function that is defined by the ***fx_media_open*** service call.</span></span> <span data-ttu-id="99bbb-112">La función de entrada del controlador tiene el formato siguiente:</span><span class="sxs-lookup"><span data-stu-id="99bbb-112">The driver entry function has the following format:</span></span>

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

<span data-ttu-id="99bbb-113">FileX llama a la función de entrada del controlador de E/S para solicitar todo el acceso a los medios físicos, incluida la inicialización y la lectura del sector de arranque.</span><span class="sxs-lookup"><span data-stu-id="99bbb-113">FileX calls the I/O driver entry function to request all physical media access, including initialization and boot sector reading.</span></span> <span data-ttu-id="99bbb-114">Las solicitudes al controlador se realizan de forma secuencial, es decir, FileX espera a que se complete la solicitud actual antes de enviar una nueva.</span><span class="sxs-lookup"><span data-stu-id="99bbb-114">Requests made to the driver are done sequentially; i.e., FileX waits for the current request to complete before another request is sent.</span></span>

## <a name="io-driver-requests"></a><span data-ttu-id="99bbb-115">Solicitudes de controlador de E/S</span><span class="sxs-lookup"><span data-stu-id="99bbb-115">I/O Driver Requests</span></span>

<span data-ttu-id="99bbb-116">Dado que cada controlador de E/S tiene una sola función de entrada, FileX realiza solicitudes específicas a través del bloque de control del medio.</span><span class="sxs-lookup"><span data-stu-id="99bbb-116">Because each I/O driver has a single entry function, FileX makes specific requests through the media control block.</span></span> <span data-ttu-id="99bbb-117">Específicamente, el miembro **fx_media_driver_request** de **FX_MEDIA** se utiliza para especificar la solicitud de controlador exacta.</span><span class="sxs-lookup"><span data-stu-id="99bbb-117">Specifically, the  **fx_media_driver_request** member of **FX_MEDIA** is used to specify the exact driver request.</span></span> <span data-ttu-id="99bbb-118">El controlador de E/S comunica si la solicitud se ha realizado correctamente a través del miembro **fx_media_driver_status** de **FX_MEDIA**.</span><span class="sxs-lookup"><span data-stu-id="99bbb-118">The I/O driver communicates the success or failure of the request through the **fx_media_driver_status** member of **FX_MEDIA**.</span></span> <span data-ttu-id="99bbb-119">Si la solicitud del controlador se ha realizado correctamente, **FX_SUCCESS** se coloca en este campo antes de que el controlador vuelva.</span><span class="sxs-lookup"><span data-stu-id="99bbb-119">If the driver request was successful, **FX_SUCCESS** is placed in this field before the driver returns.</span></span> <span data-ttu-id="99bbb-120">De lo contrario, si se detecta un error, FX_IO_ERROR se coloca en este campo.</span><span class="sxs-lookup"><span data-stu-id="99bbb-120">Otherwise, if an error is detected, FX_IO_ERROR is placed in this field.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="99bbb-121">Inicialización del controlador</span><span class="sxs-lookup"><span data-stu-id="99bbb-121">Driver Initialization</span></span>

<span data-ttu-id="99bbb-122">Aunque el procesamiento real de inicialización del controlador es específico de la aplicación, normalmente se compone de la inicialización de la estructura de datos y, posiblemente, de una inicialización de hardware preliminar.</span><span class="sxs-lookup"><span data-stu-id="99bbb-122">Although the actual driver initialization processing is application specific, it usually consists of data structure initialization and possibly some preliminary hardware initialization.</span></span> <span data-ttu-id="99bbb-123">Esta solicitud es la primera realizada por FileX y se realiza desde dentro del servicio fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="99bbb-123">This request is the first made by FileX and is done from within the fx_media_open service.</span></span>

<span data-ttu-id="99bbb-124">Si se detecta protección contra escritura de medios, el miembro del controlador fx_media_driver_write_protect de FX_MEDIA debe establecerse en FX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="99bbb-124">If media write protection is detected, the driver fx_media_driver_write_protect member of FX_MEDIA should be set to FX_TRUE.</span></span>

<span data-ttu-id="99bbb-125">Se usan los siguientes miembros de FX_MEDIA para la solicitud de inicialización del controlador de E/S:</span><span class="sxs-lookup"><span data-stu-id="99bbb-125">The following FX_MEDIA members are used for the I/O driver initialization request:</span></span>

|<span data-ttu-id="99bbb-126">Miembro de FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="99bbb-126">FX_MEDIA member</span></span>|<span data-ttu-id="99bbb-127">Significado</span><span class="sxs-lookup"><span data-stu-id="99bbb-127">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="99bbb-128">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="99bbb-128">fx_media_driver_request</span></span>|<span data-ttu-id="99bbb-129">FX_DRIVER_INIT</span><span class="sxs-lookup"><span data-stu-id="99bbb-129">FX_DRIVER_INIT</span></span>|

<span data-ttu-id="99bbb-130">FileX proporciona un mecanismo para informar al controlador de la aplicación cuando los sectores ya no están en uso.</span><span class="sxs-lookup"><span data-stu-id="99bbb-130">FileX provides a mechanism to inform the application driver when sectors are no longer being used.</span></span> <span data-ttu-id="99bbb-131">Esto es especialmente útil para los administradores de memoria flash que deben administrar todos los sectores lógicos en uso asignados a la memoria flash.</span><span class="sxs-lookup"><span data-stu-id="99bbb-131">This is especially useful for FLASH memory managers that must manage all in-use logical sectors mapped to the FLASH.</span></span>

<span data-ttu-id="99bbb-132">Si se requiere esta notificación de sectores disponibles, el controlador de la aplicación simplemente establece en **FX_TRUE** el campo *fx_media_driver_free_sector_update* en la estructura **FX_MEDIA** asociada.</span><span class="sxs-lookup"><span data-stu-id="99bbb-132">If such notification of free sectors is required, the application driver simply sets the *fx_media_driver_free_sector_update* field in the associated **FX_MEDIA** structure to **FX_TRUE**.</span></span> <span data-ttu-id="99bbb-133">Una vez establecido, FileX realiza una llamada de controlador de E/S **_FX_DRIVER_RELEASE_SECTORS_** que indica la disponibilidad de uno o más sectores consecutivos.</span><span class="sxs-lookup"><span data-stu-id="99bbb-133">After set, FileX makes a **_FX_DRIVER_RELEASE_SECTORS_** I/O driver call indicating when one or more consecutive sectors becomes free.</span></span>

### <a name="boot-sector-read"></a><span data-ttu-id="99bbb-134">Lectura del sector de arranque</span><span class="sxs-lookup"><span data-stu-id="99bbb-134">Boot Sector Read</span></span>

<span data-ttu-id="99bbb-135">En lugar de usar una solicitud de lectura estándar, FileX realiza una solicitud específica para leer el sector de arranque del medio.</span><span class="sxs-lookup"><span data-stu-id="99bbb-135">Instead of using a standard read request, FileX makes a specific request to read the media's boot sector.</span></span> <span data-ttu-id="99bbb-136">Se usan los siguientes miembros de **FX_MEDIA** para la solicitud de lectura del sector de arranque del controlador de E/S:</span><span class="sxs-lookup"><span data-stu-id="99bbb-136">The following **FX_MEDIA** members are used for the I/O driver boot sector read request:</span></span>

|<span data-ttu-id="99bbb-137">Miembro de FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="99bbb-137">FX_MEDIA member</span></span>|<span data-ttu-id="99bbb-138">Significado</span><span class="sxs-lookup"><span data-stu-id="99bbb-138">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="99bbb-139">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="99bbb-139">fx_media_driver_request</span></span>| <span data-ttu-id="99bbb-140">FX_DRIVER_BOOT_READ</span><span class="sxs-lookup"><span data-stu-id="99bbb-140">FX_DRIVER_BOOT_READ</span></span>|
|<span data-ttu-id="99bbb-141">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="99bbb-141">fx_media_driver_buffer</span></span>| <span data-ttu-id="99bbb-142">Dirección de destino del sector de arranque.</span><span class="sxs-lookup"><span data-stu-id="99bbb-142">Address of destination for boot sector.</span></span>|

### <a name="boot-sector-write"></a><span data-ttu-id="99bbb-143">Escritura del sector de arranque</span><span class="sxs-lookup"><span data-stu-id="99bbb-143">Boot Sector Write</span></span>

<span data-ttu-id="99bbb-144">En lugar de usar una solicitud de escritura estándar, FileX realiza una solicitud específica para escribir el sector de arranque del medio.</span><span class="sxs-lookup"><span data-stu-id="99bbb-144">Instead of using a standard write request, FileX makes a specific request to write the media's boot sector.</span></span> <span data-ttu-id="99bbb-145">Se usan los siguientes miembros de **FX_MEDIA** para la solicitud de escritura del sector de arranque del controlador de E/S:</span><span class="sxs-lookup"><span data-stu-id="99bbb-145">The following **FX_MEDIA** members are used for the I/O driver boot sector write request:</span></span>

|<span data-ttu-id="99bbb-146">Miembro de FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="99bbb-146">FX_MEDIA member</span></span>|<span data-ttu-id="99bbb-147">Significado</span><span class="sxs-lookup"><span data-stu-id="99bbb-147">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="99bbb-148">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="99bbb-148">fx_media_driver_request</span></span>| <span data-ttu-id="99bbb-149">FX_DRIVER_BOOT_WRITE</span><span class="sxs-lookup"><span data-stu-id="99bbb-149">FX_DRIVER_BOOT_WRITE</span></span>|
|<span data-ttu-id="99bbb-150">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="99bbb-150">fx_media_driver_buffer</span></span>| <span data-ttu-id="99bbb-151">Dirección de origen del sector de arranque.</span><span class="sxs-lookup"><span data-stu-id="99bbb-151">Address of source for boot sector.</span></span>|

### <a name="sector-read"></a><span data-ttu-id="99bbb-152">Lectura del sector</span><span class="sxs-lookup"><span data-stu-id="99bbb-152">Sector Read</span></span>

<span data-ttu-id="99bbb-153">FileX lee uno o más sectores en la memoria emitiendo una solicitud de lectura al controlador de E/S.</span><span class="sxs-lookup"><span data-stu-id="99bbb-153">FileX reads one or more sectors into memory by issuing a read request to the I/O driver.</span></span> <span data-ttu-id="99bbb-154">Se usan los siguientes miembros de **FX_MEDIA** para la solicitud de lectura del controlador de E/S:</span><span class="sxs-lookup"><span data-stu-id="99bbb-154">The following **FX_MEDIA** members are used for the I/O driver read request:</span></span>

|<span data-ttu-id="99bbb-155">Miembro de FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="99bbb-155">FX_MEDIA member</span></span>|<span data-ttu-id="99bbb-156">Significado</span><span class="sxs-lookup"><span data-stu-id="99bbb-156">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="99bbb-157">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="99bbb-157">fx_media_driver_request</span></span>| <span data-ttu-id="99bbb-158">FX_DRIVER_READ</span><span class="sxs-lookup"><span data-stu-id="99bbb-158">FX_DRIVER_READ</span></span>|
|<span data-ttu-id="99bbb-159">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="99bbb-159">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="99bbb-160">Sector lógico que se va a leer</span><span class="sxs-lookup"><span data-stu-id="99bbb-160">Logical sector to read</span></span>|
|<span data-ttu-id="99bbb-161">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="99bbb-161">fx_media_driver_sectors</span></span>|<span data-ttu-id="99bbb-162">Número de sectores que se van a leer</span><span class="sxs-lookup"><span data-stu-id="99bbb-162">Number of sectors to read</span></span>|
|<span data-ttu-id="99bbb-163">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="99bbb-163">fx_media_driver_buffer</span></span>|<span data-ttu-id="99bbb-164">Búfer de destino para los sectores leídos</span><span class="sxs-lookup"><span data-stu-id="99bbb-164">Destination buffer for sector(s) read</span></span>|
|<span data-ttu-id="99bbb-165">fx_media_driver_data_sector_read</span><span class="sxs-lookup"><span data-stu-id="99bbb-165">fx_media_driver_data_sector_read</span></span>|<span data-ttu-id="99bbb-166">Se establece en FX_TRUE si se solicita un sector de datos de archivo;</span><span class="sxs-lookup"><span data-stu-id="99bbb-166">Set to FX_TRUE if a file data sector is requested.</span></span> <span data-ttu-id="99bbb-167">de lo contrario, en FX_FALSE si se solicita un sector del sistema (FAT o sector de directorio).</span><span class="sxs-lookup"><span data-stu-id="99bbb-167">Otherwise, FX_FALSE if a system sector (FAT or directory sector) is requested.</span></span>|
|<span data-ttu-id="99bbb-168">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="99bbb-168">fx_media_driver_sector_type</span></span>|<span data-ttu-id="99bbb-169">Define el tipo explícito de sector solicitado, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="99bbb-169">Defines the explicit type of sector requested, as follows:</span></span><br /><span data-ttu-id="99bbb-170">FX_FAT_SECTOR (2)</span><span class="sxs-lookup"><span data-stu-id="99bbb-170">FX_FAT_SECTOR (2)</span></span><br /><span data-ttu-id="99bbb-171">FX_DIRECTORY_SECTOR (3)</span><span class="sxs-lookup"><span data-stu-id="99bbb-171">FX_DIRECTORY_SECTOR (3)</span></span><br /><span data-ttu-id="99bbb-172">FX_DATA_SECTOR (4)</span><span class="sxs-lookup"><span data-stu-id="99bbb-172">FX_DATA_SECTOR (4)</span></span>|

### <a name="sector-write"></a><span data-ttu-id="99bbb-173">Escritura de sectores</span><span class="sxs-lookup"><span data-stu-id="99bbb-173">Sector Write</span></span>

<span data-ttu-id="99bbb-174">FileX escribe uno o más sectores en el medio físico emitiendo una solicitud de escritura en el controlador de E/S.</span><span class="sxs-lookup"><span data-stu-id="99bbb-174">FileX writes one or more sectors to the physical media by issuing a write request to the I/O driver.</span></span> <span data-ttu-id="99bbb-175">Se usan los siguientes miembros de FX_MEDIA para la solicitud de escritura del controlador de E/S:</span><span class="sxs-lookup"><span data-stu-id="99bbb-175">The following FX_MEDIA members are used for the I/O driver write request:</span></span>

|<span data-ttu-id="99bbb-176">Miembro de FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="99bbb-176">FX_MEDIA member</span></span>| <span data-ttu-id="99bbb-177">Significado</span><span class="sxs-lookup"><span data-stu-id="99bbb-177">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="99bbb-178">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="99bbb-178">fx_media_driver_request</span></span>|<span data-ttu-id="99bbb-179">FX_DRIVER_WRITE</span><span class="sxs-lookup"><span data-stu-id="99bbb-179">FX_DRIVER_WRITE</span></span>|
|<span data-ttu-id="99bbb-180">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="99bbb-180">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="99bbb-181">Sector lógico que se va a escribir</span><span class="sxs-lookup"><span data-stu-id="99bbb-181">Logical sector to write</span></span>|
|<span data-ttu-id="99bbb-182">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="99bbb-182">fx_media_driver_sectors</span></span>|<span data-ttu-id="99bbb-183">Número de sectores que se van a escribir</span><span class="sxs-lookup"><span data-stu-id="99bbb-183">Number of sectors to write</span></span>|
|<span data-ttu-id="99bbb-184">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="99bbb-184">fx_media_driver_buffer</span></span>|<span data-ttu-id="99bbb-185">Búfer de origen de los sectores que se van a escribir</span><span class="sxs-lookup"><span data-stu-id="99bbb-185">Source buffer for sector(s) to write</span></span>|
|<span data-ttu-id="99bbb-186">fx_media_driver_system_write</span><span class="sxs-lookup"><span data-stu-id="99bbb-186">fx_media_driver_system_write</span></span>| <span data-ttu-id="99bbb-187">Se establece en FX_TRUE si se solicita un sector del sistema (FAT o sector del directorio);</span><span class="sxs-lookup"><span data-stu-id="99bbb-187">Set to FX_TRUE if a system sector is requested (FAT or directory sector).</span></span> <span data-ttu-id="99bbb-188">de lo contrario, en FX_FALSE si se solicita un sector de datos de archivo.</span><span class="sxs-lookup"><span data-stu-id="99bbb-188">Otherwise, FX_FALSE if a file data sector is requested.</span></span>|
|<span data-ttu-id="99bbb-189">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="99bbb-189">fx_media_driver_sector_type</span></span>|<span data-ttu-id="99bbb-190">Define el tipo explícito de sector solicitado, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="99bbb-190">Defines the explicit type of sector requested, as follows:</span></span><br> <br><span data-ttu-id="99bbb-191">FX_FAT_SECTOR (2)</span><span class="sxs-lookup"><span data-stu-id="99bbb-191">FX_FAT_SECTOR (2)</span></span> <br> <span data-ttu-id="99bbb-192">FX_DIRECTORY_SECTOR (3)</span><span class="sxs-lookup"><span data-stu-id="99bbb-192">FX_DIRECTORY_SECTOR (3)</span></span> <br><span data-ttu-id="99bbb-193">FX_DATA_SECTOR (4)</span><span class="sxs-lookup"><span data-stu-id="99bbb-193">FX_DATA_SECTOR (4).</span></span>|

### <a name="driver-flush"></a><span data-ttu-id="99bbb-194">Vaciado de controladores</span><span class="sxs-lookup"><span data-stu-id="99bbb-194">Driver Flush</span></span>

<span data-ttu-id="99bbb-195">FileX vacía todos los sectores que se encuentran actualmente en la memoria caché del sector del controlador en el medio físico emitiendo una solicitud de vaciado al controlador de E/S.</span><span class="sxs-lookup"><span data-stu-id="99bbb-195">FileX flushes all sectors currently in the driver's sector cache to the physical media by issuing a flush request to the I/O driver.</span></span> <span data-ttu-id="99bbb-196">Obviamente, si el controlador no almacena en caché los sectores, esta solicitud no requiere ningún procesamiento del controlador.</span><span class="sxs-lookup"><span data-stu-id="99bbb-196">Of course, if the driver is not caching sectors, this request requires no driver processing.</span></span> <span data-ttu-id="99bbb-197">Se usan los siguientes miembros de FX_MEDIA para la solicitud de vaciado del controlador de E/S:</span><span class="sxs-lookup"><span data-stu-id="99bbb-197">The following FX_MEDIA members are used for the I/O driver flush request:</span></span>

|<span data-ttu-id="99bbb-198">Miembro de FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="99bbb-198">FX_MEDIA member</span></span>| <span data-ttu-id="99bbb-199">Significado</span><span class="sxs-lookup"><span data-stu-id="99bbb-199">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="99bbb-200">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="99bbb-200">fx_media_driver_request</span></span>|<span data-ttu-id="99bbb-201">FX_DRIVER_FLUSH</span><span class="sxs-lookup"><span data-stu-id="99bbb-201">FX_DRIVER_FLUSH</span></span>|

### <a name="driver-abort"></a><span data-ttu-id="99bbb-202">Anulación del controlador</span><span class="sxs-lookup"><span data-stu-id="99bbb-202">Driver Abort</span></span>

<span data-ttu-id="99bbb-203">FileX informa al controlador de que debe anular toda la actividad física de E/S con el medio físico emitiendo una solicitud de anulación al controlador de E/S.</span><span class="sxs-lookup"><span data-stu-id="99bbb-203">FileX informs the driver to abort all further physical I/O activity with the physical media by issuing an abort request to the I/O driver.</span></span> <span data-ttu-id="99bbb-204">El controlador no debe realizar ninguna E/S de nuevo hasta que se vuelva a inicializar.</span><span class="sxs-lookup"><span data-stu-id="99bbb-204">The driver should not perform any I/O again until it is re-initialized.</span></span> <span data-ttu-id="99bbb-205">Se usan los siguientes miembros de FX_MEDIA para la solicitud de anulación del controlador de E/S:</span><span class="sxs-lookup"><span data-stu-id="99bbb-205">The following FX_MEDIA members are used for the I/O driver abort request:</span></span>

|<span data-ttu-id="99bbb-206">Miembro de FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="99bbb-206">FX_MEDIA member</span></span>| <span data-ttu-id="99bbb-207">Significado</span><span class="sxs-lookup"><span data-stu-id="99bbb-207">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="99bbb-208">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="99bbb-208">fx_media_driver_request</span></span>| <span data-ttu-id="99bbb-209">FX_DRIVER_ABORT</span><span class="sxs-lookup"><span data-stu-id="99bbb-209">FX_DRIVER_ABORT</span></span>|

### <a name="release-sectors"></a><span data-ttu-id="99bbb-210">Disponibilidad de sectores</span><span class="sxs-lookup"><span data-stu-id="99bbb-210">Release Sectors</span></span>

<span data-ttu-id="99bbb-211">Si el controlador lo seleccionó anteriormente durante la inicialización, FileX informa al controlador cuando uno o más sectores consecutivos están disponibles.</span><span class="sxs-lookup"><span data-stu-id="99bbb-211">If previously selected by the driver during initialization, FileX informs the driver whenever one or more consecutive sectors become free.</span></span> <span data-ttu-id="99bbb-212">Si el controlador es en realidad un administrador de memoria flash, se puede usar esta información para indicarle que ya no se necesitan estos sectores.</span><span class="sxs-lookup"><span data-stu-id="99bbb-212">If the driver is actually a FLASH manager, this information can be used to tell the FLASH manager that these sectors are no longer needed.</span></span> <span data-ttu-id="99bbb-213">Se usan los siguientes miembros de **FX_MEDIA** para la solicitud de disponibilidad de sectores de E/S:</span><span class="sxs-lookup"><span data-stu-id="99bbb-213">The following **FX_MEDIA** members are used for the I/O release sectors request:</span></span>

|<span data-ttu-id="99bbb-214">Miembro de FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="99bbb-214">FX_MEDIA member</span></span>| <span data-ttu-id="99bbb-215">Significado</span><span class="sxs-lookup"><span data-stu-id="99bbb-215">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="99bbb-216">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="99bbb-216">fx_media_driver_request</span></span>|<span data-ttu-id="99bbb-217">FX_DRIVER_RELEASE_SECTORS</span><span class="sxs-lookup"><span data-stu-id="99bbb-217">FX_DRIVER_RELEASE_SECTORS</span></span>|
|<span data-ttu-id="99bbb-218">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="99bbb-218">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="99bbb-219">Inicio del sector disponible</span><span class="sxs-lookup"><span data-stu-id="99bbb-219">Start of free sector</span></span>|
|<span data-ttu-id="99bbb-220">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="99bbb-220">fx_media_driver_sectors</span></span>|<span data-ttu-id="99bbb-221">Número de sectores disponibles</span><span class="sxs-lookup"><span data-stu-id="99bbb-221">Number of free sectors</span></span>|

### <a name="driver-suspension"></a><span data-ttu-id="99bbb-222">Suspensión del controlador</span><span class="sxs-lookup"><span data-stu-id="99bbb-222">Driver Suspension</span></span>

<span data-ttu-id="99bbb-223">Dado que la E/S con medios físicos puede tardar algún tiempo, suele ser recomendable suspender el subproceso de llamada.</span><span class="sxs-lookup"><span data-stu-id="99bbb-223">Because I/O with physical media may take some time, suspending the calling thread is often desirable.</span></span> <span data-ttu-id="99bbb-224">Con ello, se da por sentado que la finalización de la operación de E/S subyacente está controlada por interrupciones.</span><span class="sxs-lookup"><span data-stu-id="99bbb-224">Of course, this assumes completion of the underlying I/O operation is interrupt driven.</span></span> <span data-ttu-id="99bbb-225">Si es así, la suspensión de subprocesos se implementa fácilmente con un semáforo ThreadX.</span><span class="sxs-lookup"><span data-stu-id="99bbb-225">If so, thread suspension is easily implemented with a ThreadX semaphore.</span></span> <span data-ttu-id="99bbb-226">Después de iniciar la operación de entrada o de salida, el controlador de E/S se suspende en su propio semáforo de E/S interno (creado con un recuento inicial de cero durante la inicialización del controlador).</span><span class="sxs-lookup"><span data-stu-id="99bbb-226">After starting the input or output operation, the I/O driver suspends on its own internal I/O semaphore (created with an initial count of zero during driver initialization).</span></span> <span data-ttu-id="99bbb-227">Como parte del procesamiento de interrupciones de finalización de E/S del controlador, se establece el mismo semáforo de E/S, que a su vez activa el subproceso suspendido.</span><span class="sxs-lookup"><span data-stu-id="99bbb-227">As part of the driver I/O completion interrupt processing, the same I/O semaphore is set, which in turn wakes up the suspended thread.</span></span>

### <a name="sector-translation"></a><span data-ttu-id="99bbb-228">Traducción de sectores</span><span class="sxs-lookup"><span data-stu-id="99bbb-228">Sector Translation</span></span>

<span data-ttu-id="99bbb-229">Dado que FileX ve el medio como sectores lógicos lineales, las solicitudes de E/S realizadas al controlador de E/S se realizan con sectores lógicos.</span><span class="sxs-lookup"><span data-stu-id="99bbb-229">Because FileX views the media as linear logical sectors, I/O requests made to the I/O driver are made with logical sectors.</span></span> <span data-ttu-id="99bbb-230">Es responsabilidad del controlador traducir entre sectores lógicos y la geometría física del medio, que puede incluir encabezados, pistas y sectores físicos.</span><span class="sxs-lookup"><span data-stu-id="99bbb-230">It is the driver's responsibility to translate between logical sectors and the physical geometry of the media, which may include heads, tracks, and physical sectors.</span></span> <span data-ttu-id="99bbb-231">En el caso de los medios de disco RAM y Flash, los sectores lógicos suelen asignar el directorio a los sectores físicos.</span><span class="sxs-lookup"><span data-stu-id="99bbb-231">For FLASH and RAM disk media, the logical sectors typically map directory to physical sectors.</span></span> <span data-ttu-id="99bbb-232">En cualquier caso, estas son las fórmulas típicas para realizar la asignación de sectores lógicos a físicos en el controlador de E/S:</span><span class="sxs-lookup"><span data-stu-id="99bbb-232">In any case, here are the typical formulas to perform the logical to physical sector mapping in the I/O driver:</span></span>

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

<span data-ttu-id="99bbb-233">Tenga en cuenta que los sectores físicos comienzan por uno, mientras que los sectores lógicos comienzan por cero.</span><span class="sxs-lookup"><span data-stu-id="99bbb-233">Note that physical sectors start at one, while logical sectors start at zero.</span></span>

### <a name="hidden-sectors"></a><span data-ttu-id="99bbb-234">Sectores ocultos</span><span class="sxs-lookup"><span data-stu-id="99bbb-234">Hidden Sectors</span></span>

<span data-ttu-id="99bbb-235">Los sectores ocultos residían antes del registro de arranque en el medio.</span><span class="sxs-lookup"><span data-stu-id="99bbb-235">Hidden sectors resided prior to the boot record on the media.</span></span> <span data-ttu-id="99bbb-236">Dado que realmente se encuentran fuera del ámbito del diseño del sistema de archivos FAT, se deben tener en cuenta en cada operación de sector lógico que realiza el controlador.</span><span class="sxs-lookup"><span data-stu-id="99bbb-236">Because they are really outside the scope of the FAT file system layout, they must be accounted for in each logical sector operation the driver does.</span></span>

### <a name="media-write-protect"></a><span data-ttu-id="99bbb-237">Protección contra escritura de medios</span><span class="sxs-lookup"><span data-stu-id="99bbb-237">Media Write Protect</span></span>

<span data-ttu-id="99bbb-238">El controlador FileX puede activar la protección contra escritura estableciendo el campo fx_media_driver_write_protect en el bloque de control multimedia.</span><span class="sxs-lookup"><span data-stu-id="99bbb-238">The FileX driver can turn on write protect by setting the fx_media_driver_write_protect field in the media control block.</span></span> <span data-ttu-id="99bbb-239">De esta manera se devolverá un error si se realizan llamadas a FileX en un intento de escribir en el medio.</span><span class="sxs-lookup"><span data-stu-id="99bbb-239">This will cause an error to be returned if any FileX calls are made in an attempt to write to the media.</span></span>

## <a name="sample-ram-driver"></a><span data-ttu-id="99bbb-240">Controlador de RAM de ejemplo</span><span class="sxs-lookup"><span data-stu-id="99bbb-240">Sample RAM Driver</span></span>

<span data-ttu-id="99bbb-241">El sistema de demostración de FileX se entrega con un pequeño controlador de disco RAM, que se define en el archivo fx_ram_driver.c.</span><span class="sxs-lookup"><span data-stu-id="99bbb-241">The FileX demonstration system is delivered with a small RAM disk driver, which is defined in the file fx_ram_driver.c.</span></span> <span data-ttu-id="99bbb-242">El controlador supone un espacio de memoria de 32 KB y crea un registro de arranque para los sectores de 256 y 128 bytes.</span><span class="sxs-lookup"><span data-stu-id="99bbb-242">The driver assumes a 32K memory space and creates a boot record for 256 128-byte sectors.</span></span> <span data-ttu-id="99bbb-243">Este archivo proporciona un buen ejemplo de cómo implementar controladores de E/S de FileX específicos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="99bbb-243">This file provides a good example of how to implement application specific FileX I/O drivers.</span></span>

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
