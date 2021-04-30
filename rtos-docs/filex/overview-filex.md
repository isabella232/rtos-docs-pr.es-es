---
title: Información general sobre Azure RTOS FileX
description: Azure RTOS FileX es un sistema de archivos de alto rendimiento compatible con la tabla de asignación de archivos (FAT) que está totalmente integrado con Azure RTO ThreadX y está disponible para todos los procesadores compatibles. Al igual que Azure RTO ThreadX, Azure RTOS FileX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las actuales aplicaciones profundamente insertadas, que requieren operaciones de administración de archivos. FileX admite la mayoría de los soportes físicos, como la memoria RAM, Azure RTOS USBX, tarjeta SD y memorias Flash NAND/NOR a través de Azure RTO LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815601"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="ace37-105">Información general sobre Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="ace37-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="ace37-106">El sistema de archivos incrustados de Azure RTOS FileX es la solución avanzada de nivel industrial de Azure RTOS para los formatos de archivo FAT de Microsoft, diseñada específicamente para aplicaciones de IoT, en tiempo real e integradas.</span><span class="sxs-lookup"><span data-stu-id="ace37-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="ace37-107">Azure RTOS FileX admite todos los formatos de archivo de Microsoft, incluidos FAT12, FAT16, FAT32 y exFAT.</span><span class="sxs-lookup"><span data-stu-id="ace37-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="ace37-108">FileX también ofrece tolerancia a errores y redistribución de uso de FLASH opcional a través de un producto complementario llamado [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span><span class="sxs-lookup"><span data-stu-id="ace37-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="ace37-109">Todo esto, combinado con una pequeña superficie, una ejecución rápida y una facilidad de uso superior, hacen que Azure RTOS FileX sea la opción ideal para las aplicaciones IoT insertadas más exigentes.</span><span class="sxs-lookup"><span data-stu-id="ace37-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="ace37-110">Protocolos de API</span><span class="sxs-lookup"><span data-stu-id="ace37-110">API protocols</span></span>

### <a name="azure-rtos-filex-api"></a><span data-ttu-id="ace37-111">API Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="ace37-111">Azure RTOS FileX API</span></span>

- <span data-ttu-id="ace37-112">API intuitivas y coherentes</span><span class="sxs-lookup"><span data-stu-id="ace37-112">Intuitive and consistent API</span></span>
- <span data-ttu-id="ace37-113">Convención de nomenclatura sustantivo-verbo</span><span class="sxs-lookup"><span data-stu-id="ace37-113">Noun-verb naming convention</span></span>
- <span data-ttu-id="ace37-114">Todas las API tienen un *fx_* al inicio para identificarlas fácilmente como FileX</span><span class="sxs-lookup"><span data-stu-id="ace37-114">All APIs have leading *fx_* to easily identify as FileX</span></span>
- <span data-ttu-id="ace37-115">Las API de bloqueo tienen un tiempo de espera de subprocesos opcional</span><span class="sxs-lookup"><span data-stu-id="ace37-115">Blocking APIs have optional thread timeout</span></span>
- <span data-ttu-id="ace37-116">Devoluciones de llamada de notificación de usuario opcionales para operaciones de archivos y medios</span><span class="sxs-lookup"><span data-stu-id="ace37-116">Optional user-notification callbacks for media and file operations</span></span>
- <span data-ttu-id="ace37-117">Consulte la [Guía de usuario de Azure RTOS FileX](about-this-guide.md) para obtener más información</span><span class="sxs-lookup"><span data-stu-id="ace37-117">Please see [Azure RTOS FileX User Guide](about-this-guide.md) for more details</span></span>

### <a name="media-services"></a><span data-ttu-id="ace37-118">Media Services</span><span class="sxs-lookup"><span data-stu-id="ace37-118">Media Services</span></span>

- <span data-ttu-id="ace37-119">Compatibilidad con FAT 12/16/32 y exFAT</span><span class="sxs-lookup"><span data-stu-id="ace37-119">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="ace37-120">Memoria FLASH mínima de 6 KB y 2,5 KB de RAM</span><span class="sxs-lookup"><span data-stu-id="ace37-120">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="ace37-121">Servicios completos de acceso a medios</span><span class="sxs-lookup"><span data-stu-id="ace37-121">Complete media access services</span></span>
- <span data-ttu-id="ace37-122">Número ilimitado de instancias de medios</span><span class="sxs-lookup"><span data-stu-id="ace37-122">Unlimited number of media instance</span></span>
- <span data-ttu-id="ace37-123">Interfaz de controlador de sector lógico de lectura/escritura simple</span><span class="sxs-lookup"><span data-stu-id="ace37-123">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="ace37-124">Compatibilidad con varias particiones</span><span class="sxs-lookup"><span data-stu-id="ace37-124">Multiple partition support</span></span>
- <span data-ttu-id="ace37-125">Caché del sector lógico</span><span class="sxs-lookup"><span data-stu-id="ace37-125">Logical sector cache</span></span>
- <span data-ttu-id="ace37-126">Caché de entrada FAT</span><span class="sxs-lookup"><span data-stu-id="ace37-126">FAT entry cache</span></span>
- <span data-ttu-id="ace37-127">Compatibilidad con tolerancia a errores opcional</span><span class="sxs-lookup"><span data-stu-id="ace37-127">Optional fault tolerance support</span></span>
- <span data-ttu-id="ace37-128">Actualización diferida del sistema de archivos FAT secundario</span><span class="sxs-lookup"><span data-stu-id="ace37-128">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="ace37-129">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="ace37-129">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="ace37-130">API intuitivas de acceso a medios, que incluyen:</span><span class="sxs-lookup"><span data-stu-id="ace37-130">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="ace37-131">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ace37-131">fx_media_open</span></span>
  - <span data-ttu-id="ace37-132">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ace37-132">fx_media_close</span></span>
  - <span data-ttu-id="ace37-133">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ace37-133">fx_media_format</span></span>
  - <span data-ttu-id="ace37-134">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ace37-134">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="ace37-135">Servicios de directorio</span><span class="sxs-lookup"><span data-stu-id="ace37-135">Directory Services</span></span>

- <span data-ttu-id="ace37-136">Rutas de acceso de hasta 256 bytes</span><span class="sxs-lookup"><span data-stu-id="ace37-136">Up to 256 byte paths</span></span>
- <span data-ttu-id="ace37-137">Se admiten nombres largos y de directorio 8.3</span><span class="sxs-lookup"><span data-stu-id="ace37-137">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="ace37-138">Creación y eliminación de directorios</span><span class="sxs-lookup"><span data-stu-id="ace37-138">Directory create & delete</span></span>
- <span data-ttu-id="ace37-139">Navegación y recorrido de directorios</span><span class="sxs-lookup"><span data-stu-id="ace37-139">Directory navigation and traversal</span></span>
- <span data-ttu-id="ace37-140">Administración de atributos de directorios</span><span class="sxs-lookup"><span data-stu-id="ace37-140">Directory attributes management</span></span>
- <span data-ttu-id="ace37-141">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="ace37-141">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="ace37-142">API intuitivas de acceso a directorios, que incluyen:</span><span class="sxs-lookup"><span data-stu-id="ace37-142">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="ace37-143">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ace37-143">fx_directory_create</span></span>
  - <span data-ttu-id="ace37-144">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ace37-144">fx_directory_delete</span></span>
  - <span data-ttu-id="ace37-145">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ace37-145">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="ace37-146">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ace37-146">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="ace37-147">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ace37-147">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="ace37-148">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ace37-148">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="ace37-149">Servicios de archivos</span><span class="sxs-lookup"><span data-stu-id="ace37-149">File Services</span></span>

- <span data-ttu-id="ace37-150">Memoria FLASH mínima de 3,3 KB</span><span class="sxs-lookup"><span data-stu-id="ace37-150">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="ace37-151">Archivos abiertos ilimitados</span><span class="sxs-lookup"><span data-stu-id="ace37-151">Unlimited open files</span></span>
- <span data-ttu-id="ace37-152">Los archivos de solo lectura se pueden abrir varias veces</span><span class="sxs-lookup"><span data-stu-id="ace37-152">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="ace37-153">Se admiten nombres largos y de directorio 8.3</span><span class="sxs-lookup"><span data-stu-id="ace37-153">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="ace37-154">Compatibilidad con archivos contiguos</span><span class="sxs-lookup"><span data-stu-id="ace37-154">Contiguous file support</span></span>
- <span data-ttu-id="ace37-155">Lógica de búsqueda rápida</span><span class="sxs-lookup"><span data-stu-id="ace37-155">Fast seek logic</span></span>
- <span data-ttu-id="ace37-156">Asignación previa de clústeres</span><span class="sxs-lookup"><span data-stu-id="ace37-156">Pre-allocation of clusters</span></span>
- <span data-ttu-id="ace37-157">Creación, eliminación y cambio de nombre de archivos</span><span class="sxs-lookup"><span data-stu-id="ace37-157">File create, delete, and rename</span></span>
- <span data-ttu-id="ace37-158">Lectura, escritura y visualización de archivos</span><span class="sxs-lookup"><span data-stu-id="ace37-158">File read, write, and see</span></span>
- <span data-ttu-id="ace37-159">Administración de atributos de archivo</span><span class="sxs-lookup"><span data-stu-id="ace37-159">File attributes management</span></span>
- <span data-ttu-id="ace37-160">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="ace37-160">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="ace37-161">API intuitivas de acceso a archivos, que incluyen:</span><span class="sxs-lookup"><span data-stu-id="ace37-161">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="ace37-162">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ace37-162">fx_file_create</span></span>
  - <span data-ttu-id="ace37-163">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ace37-163">fx_file_delete</span></span>
  - <span data-ttu-id="ace37-164">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ace37-164">fx_file_attributes_set</span></span>
  - <span data-ttu-id="ace37-165">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ace37-165">fx_file_attributes_read</span></span>
  - <span data-ttu-id="ace37-166">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ace37-166">fx_file_read</span></span>
  - <span data-ttu-id="ace37-167">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ace37-167">fx_file_seek</span></span>
  - <span data-ttu-id="ace37-168">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ace37-168">fx_file_write</span></span>

## <a name="small-footprint"></a><span data-ttu-id="ace37-169">Superficie pequeña</span><span class="sxs-lookup"><span data-stu-id="ace37-169">Small-footprint</span></span>

<span data-ttu-id="ace37-170">El sistema de archivos incrustados de Azure RTOS FileX tiene una superficie mínima considerablemente pequeña de 8,6 KB a 12 KB para la compatibilidad con lectura y escritura de archivos básicos.</span><span class="sxs-lookup"><span data-stu-id="ace37-170">Azure RTOS FileX embedded file system has a remarkably small minimal footprint of 8.6 KB to 12 KB for basic file read/write support.</span></span> <span data-ttu-id="ace37-171">El uso mínimo de RAM de Azure RTOS FileX es del orden de 1,8 KB para una instancia de medios y con solo una caché de sector lógico de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="ace37-171">Minimal Azure RTOS FileX RAM usage is on the order of 1.8 KB for one media instance and with only a 512-byte logical sector cache.</span></span> <span data-ttu-id="ace37-172">Al igual que Azure RTOS ThreadX, el tamaño de Azure RTOS FileX se escala automáticamente en función de los servicios que usa la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ace37-172">Like Azure RTOS ThreadX, the size of Azure RTOS FileX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="ace37-173">Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="ace37-173">This virtually eliminates the need for complicated configuration and builds parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="ace37-174">Ejecución rápida</span><span class="sxs-lookup"><span data-stu-id="ace37-174">Fast execution</span></span>

<span data-ttu-id="ace37-175">Azure RTOS FileX proporciona una caché del sector lógico, así como una caché de entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="ace37-175">Azure RTOS FileX provides a logical sector cache as well as a FAT entry cache.</span></span> <span data-ttu-id="ace37-176">La aplicación controla directamente ambos tamaños.</span><span class="sxs-lookup"><span data-stu-id="ace37-176">The sizes of both are under direct control of the application.</span></span> <span data-ttu-id="ace37-177">Además, Azure RTOS FileX permite la asignación de clústeres contiguos y la lectura y escritura directa de clústeres consecutivos.</span><span class="sxs-lookup"><span data-stu-id="ace37-177">In addition, Azure RTOS FileX provides contiguous cluster allocation and direct consecutive cluster reading and writing.</span></span> <span data-ttu-id="ace37-178">Las solicitudes de lectura y escritura de sectores completos se realizan directamente entre el búfer de la aplicación y los medios. Por tanto, no se realiza un almacenamiento en búfer intermedio.</span><span class="sxs-lookup"><span data-stu-id="ace37-178">Read/write requests of whole sectors are done directly between the application buffer and the media – that is, no intermediate buffering is done.</span></span> <span data-ttu-id="ace37-179">Todo esto y una filosofía general de diseño orientada al rendimiento ayudan a Azure RTOS FileX a lograr el rendimiento más rápido posible.</span><span class="sxs-lookup"><span data-stu-id="ace37-179">All of this and a general performance-oriented design philosophy helps Azure RTOS FileX achieve the fastest possible performance.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="ace37-180">Tecnología avanzada</span><span class="sxs-lookup"><span data-stu-id="ace37-180">Advanced technology</span></span>

<span data-ttu-id="ace37-181">Azure RTOS FileX es tecnología avanzada que incluye lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="ace37-181">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="ace37-182">Compatibilidad con FAT 12/16/32 y exFAT</span><span class="sxs-lookup"><span data-stu-id="ace37-182">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="ace37-183">Compatibilidad con varias particiones</span><span class="sxs-lookup"><span data-stu-id="ace37-183">Multiple partition support</span></span>
- <span data-ttu-id="ace37-184">Escalado automático</span><span class="sxs-lookup"><span data-stu-id="ace37-184">Automatic scaling</span></span>
- <span data-ttu-id="ace37-185">Endian neutro</span><span class="sxs-lookup"><span data-stu-id="ace37-185">Endian neutral</span></span>
- <span data-ttu-id="ace37-186">Soporte para nombres de archivo largos y 8.3</span><span class="sxs-lookup"><span data-stu-id="ace37-186">Long file name and 8.3 support</span></span>
- <span data-ttu-id="ace37-187">Compatibilidad con tolerancia a errores opcional</span><span class="sxs-lookup"><span data-stu-id="ace37-187">Optional fault tolerance support</span></span>
- <span data-ttu-id="ace37-188">Caché del sector lógico</span><span class="sxs-lookup"><span data-stu-id="ace37-188">Logical sector cache</span></span>
- <span data-ttu-id="ace37-189">Caché de entrada FAT</span><span class="sxs-lookup"><span data-stu-id="ace37-189">FAT entry cache</span></span>
- <span data-ttu-id="ace37-190">Asignación previa de clústeres</span><span class="sxs-lookup"><span data-stu-id="ace37-190">Pre-allocation of clusters</span></span>
- <span data-ttu-id="ace37-191">Compatibilidad con archivos contiguos</span><span class="sxs-lookup"><span data-stu-id="ace37-191">Contiguous file support</span></span>
- <span data-ttu-id="ace37-192">Métricas de rendimiento opcionales</span><span class="sxs-lookup"><span data-stu-id="ace37-192">Optional performance metrics</span></span>
- <span data-ttu-id="ace37-193">Compatibilidad con el análisis del sistema de Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="ace37-193">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="ace37-194">Distribución del uso de la memoria NOR / NAND (Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="ace37-194">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="ace37-195">Azure RTOS LevelX es el producto de distribución del uso de memoria NOR / NAND FLASH de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ace37-195">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="ace37-196">Azure RTOS LevelX se puede usar con FileX o como una biblioteca independiente de sectores FLASH de lectura / escritura directa para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ace37-196">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="ace37-197">Tiempo de comercialización más rápido</span><span class="sxs-lookup"><span data-stu-id="ace37-197">Fastest time-to-market</span></span>

<span data-ttu-id="ace37-198">Azure RTOS FileX es fácil de instalar, conocer, usar, depurar, comprobar, certificar y mantener.</span><span class="sxs-lookup"><span data-stu-id="ace37-198">Azure RTOS FileX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="ace37-199">Por lo tanto, Azure RTOS FileX es uno de los sistemas de archivos FAT más populares para dispositivos IoT insertados.</span><span class="sxs-lookup"><span data-stu-id="ace37-199">As a result, Azure RTOS FileX is one of the most popular FAT file systems for embedded IoT devices.</span></span> <span data-ttu-id="ace37-200">A continuación se indican algunas razones del ventajoso tiempo de comercialización:</span><span class="sxs-lookup"><span data-stu-id="ace37-200">The following are some reasons for our consistent time-to-market advantage:</span></span>

- <span data-ttu-id="ace37-201">Documentación de calidad: consulte nuestra [Guía de usuario de Azure RTOS FileX](about-this-guide.md) y véalo usted mismo.</span><span class="sxs-lookup"><span data-stu-id="ace37-201">Quality Documentation – please review our [Azure RTOS FileX User Guide](about-this-guide.md) and see for yourself!</span></span>
- <span data-ttu-id="ace37-202">Disponibilidad completa del código fuente</span><span class="sxs-lookup"><span data-stu-id="ace37-202">Complete Source Code Availability</span></span>
- <span data-ttu-id="ace37-203">API fáciles de usar</span><span class="sxs-lookup"><span data-stu-id="ace37-203">Easy-to-use API</span></span>
- <span data-ttu-id="ace37-204">Conjunto de características completo y avanzado</span><span class="sxs-lookup"><span data-stu-id="ace37-204">Comprehensive and Advanced Feature Set</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="ace37-205">Certificado previamente por TUV y UL para varios estándares de seguridad</span><span class="sxs-lookup"><span data-stu-id="ace37-205">Pre-certified  by TUV and UL to many safety standards</span></span>

![SGS-TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

<span data-ttu-id="ace37-207">Azure RTOS FileX ha sido certificado por los SG-TUV Saar para su uso en sistemas críticos para la seguridad, según CEI-61508 SIL 4, CEI-62304 SW Clase de seguridad C, ISO 26262 ASIL D y EN 50128.</span><span class="sxs-lookup"><span data-stu-id="ace37-207">Azure RTOS FileX has been certified by SGS-TUV Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="ace37-208">La certificación confirma que FileX se puede usar en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de CEI-61508, CEI-62304, ISO 26262 y EN 50128 para la "seguridad funcional de sistemas relacionados con la seguridad electrónica de electricidad, electrónica y programable".</span><span class="sxs-lookup"><span data-stu-id="ace37-208">The certification confirms that FileX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="ace37-209">SG-TUV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TUV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="ace37-209">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="ace37-210">El estándar de seguridad industrial CEI 61508, y todos los estándares que se derivan de él, incluidos CEI-62304, ISO 26262 y EN 50128, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y programables relacionados con la seguridad electrónica, los sistemas de control de procesos, la maquinaria industrial, los automóviles y los sistemas de control de ferrocarriles.</span><span class="sxs-lookup"><span data-stu-id="ace37-210">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles, and railway control systems.</span></span>

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="Certificación UL CRU":::

<span data-ttu-id="ace37-212">Azure RTOS FileX ha sido reconocido por UL por su conformidad con los estándares de seguridad para software de componentes programables UL 60730-1 anexo H, CSA E60730-1 anexo H, CEI 60730-1 anexo H, UL 60335-1 anexo R, CEI 60335-1 anexo R y UL 1998.</span><span class="sxs-lookup"><span data-stu-id="ace37-212">Azure RTOS FileX has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="ace37-213">UL es una empresa global e independiente especializada en la seguridad en la ciencia con más de un siglo de experiencia aportando innovaciones en soluciones de seguridad que abarcan desde la adopción pública de electricidad hasta los avances en sostenibilidad, energías renovables y nanotecnología.</span><span class="sxs-lookup"><span data-stu-id="ace37-213">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

<span data-ttu-id="ace37-214">Los artefactos (certificado, manual de seguridad, informe de pruebas, etc.) asociados a las certificaciones TUV y UL están disponibles para su venta.</span><span class="sxs-lookup"><span data-stu-id="ace37-214">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="ace37-215">En los casos en los que la aplicación necesite certificación adicional, hay un servicio de certificación disponible con Microsoft para proporcionar una certificación llave en mano para varios estándares con la plataforma de hardware real e incluso abarcando el código de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ace37-215">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="ace37-216">Una licencia sencilla</span><span class="sxs-lookup"><span data-stu-id="ace37-216">One Simple License</span></span>

<span data-ttu-id="ace37-217">No hay ningún costo asociado al uso y las pruebas del código fuente ni a las licencias de producción si se implementa en dispositivos con licencia previa; todos los demás dispositivos necesitan una licencia anual sencilla.</span><span class="sxs-lookup"><span data-stu-id="ace37-217">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="ace37-218">Código fuente completo y de máxima calidad</span><span class="sxs-lookup"><span data-stu-id="ace37-218">Full, highest-quality source code</span></span>

<span data-ttu-id="ace37-219">A lo largo de los años, el código fuente de FileX ha establecido el estándar de calidad y facilidad de comprensión.</span><span class="sxs-lookup"><span data-stu-id="ace37-219">Throughout the years, FileX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="ace37-220">Además, la convención de tener una función por archivo facilita la navegación por el origen.</span><span class="sxs-lookup"><span data-stu-id="ace37-220">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="ace37-221">Compatible con las arquitecturas más populares</span><span class="sxs-lookup"><span data-stu-id="ace37-221">Supports most popular architectures</span></span>

<span data-ttu-id="ace37-222">Azure RTOS FileX se ejecuta en los microprocesadores de 32 o 64 bits más populares, de serie, totalmente probado y totalmente compatible, lo que incluye lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ace37-222">Azure RTOS FileX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="ace37-223">**Dispositivos analógicos**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="ace37-223">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="ace37-224">**Andes Core**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="ace37-224">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="ace37-225">**Ambiqmicro**: Apollo MCU</span><span class="sxs-lookup"><span data-stu-id="ace37-225">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="ace37-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="ace37-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="ace37-227">**Cadence**: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="ace37-227">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="ace37-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="ace37-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="ace37-229">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="ace37-229">**Cypress**: RISC-V</span></span>

<span data-ttu-id="ace37-230">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="ace37-230">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="ace37-231">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="ace37-231">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="ace37-232">**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="ace37-232">**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="ace37-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="ace37-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="ace37-234">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="ace37-234">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="ace37-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="ace37-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="ace37-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span><span class="sxs-lookup"><span data-stu-id="ace37-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="ace37-237">**Silicon** Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="ace37-237">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="ace37-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="ace37-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="ace37-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="ace37-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="ace37-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="ace37-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="ace37-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="ace37-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="ace37-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="ace37-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="ace37-243">*Todas las cifras de tiempos y tamaños enumeradas son estimaciones y pueden ser diferentes en su plataforma de desarrollo.*</span><span class="sxs-lookup"><span data-stu-id="ace37-243">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
