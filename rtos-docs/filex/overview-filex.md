---
title: Información general sobre Azure RTOS FileX
description: Azure RTOS FileX es un sistema de archivos de alto rendimiento compatible con la tabla de asignación de archivos (FAT) que está totalmente integrado con Azure RTO ThreadX y está disponible para todos los procesadores compatibles. Al igual que Azure RTO ThreadX, Azure RTOS FileX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las actuales aplicaciones profundamente insertadas, que requieren operaciones de administración de archivos. FileX admite la mayoría de los soportes físicos, como la memoria RAM, Azure RTOS USBX, tarjeta SD y memorias Flash NAND/NOR a través de Azure RTO LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a54f160c96fb3e90c2295ae72020c121d367a12
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171360"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="ea753-105">Información general sobre Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="ea753-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="ea753-106">El sistema de archivos incrustados de Azure RTOS FileX es la solución avanzada de nivel industrial de Azure RTOS para los formatos de archivo FAT de Microsoft, diseñada específicamente para aplicaciones de IoT, en tiempo real e integradas.</span><span class="sxs-lookup"><span data-stu-id="ea753-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="ea753-107">Azure RTOS FileX admite todos los formatos de archivo de Microsoft, incluidos FAT12, FAT16, FAT32 y exFAT.</span><span class="sxs-lookup"><span data-stu-id="ea753-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="ea753-108">FileX también ofrece tolerancia a errores y redistribución de uso de FLASH opcional a través de un producto complementario llamado [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span><span class="sxs-lookup"><span data-stu-id="ea753-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="ea753-109">Todo esto, combinado con una pequeña superficie, una ejecución rápida y una facilidad de uso superior, hacen que Azure RTOS FileX sea la opción ideal para las aplicaciones IoT insertadas más exigentes.</span><span class="sxs-lookup"><span data-stu-id="ea753-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="ea753-110">Protocolos de API</span><span class="sxs-lookup"><span data-stu-id="ea753-110">API protocols</span></span>

### <a name="media-services"></a><span data-ttu-id="ea753-111">Media Services</span><span class="sxs-lookup"><span data-stu-id="ea753-111">Media Services</span></span>

- <span data-ttu-id="ea753-112">Compatibilidad con FAT 12/16/32 y exFAT</span><span class="sxs-lookup"><span data-stu-id="ea753-112">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="ea753-113">Memoria FLASH mínima de 6 KB y 2,5 KB de RAM</span><span class="sxs-lookup"><span data-stu-id="ea753-113">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="ea753-114">Servicios completos de acceso a medios</span><span class="sxs-lookup"><span data-stu-id="ea753-114">Complete media access services</span></span>
- <span data-ttu-id="ea753-115">Número ilimitado de instancias de medios</span><span class="sxs-lookup"><span data-stu-id="ea753-115">Unlimited number of media instance</span></span>
- <span data-ttu-id="ea753-116">Interfaz de controlador de sector lógico de lectura/escritura simple</span><span class="sxs-lookup"><span data-stu-id="ea753-116">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="ea753-117">Compatibilidad con varias particiones</span><span class="sxs-lookup"><span data-stu-id="ea753-117">Multiple partition support</span></span>
- <span data-ttu-id="ea753-118">Caché del sector lógico</span><span class="sxs-lookup"><span data-stu-id="ea753-118">Logical sector cache</span></span>
- <span data-ttu-id="ea753-119">Caché de entrada FAT</span><span class="sxs-lookup"><span data-stu-id="ea753-119">FAT entry cache</span></span>
- <span data-ttu-id="ea753-120">Compatibilidad con tolerancia a errores opcional</span><span class="sxs-lookup"><span data-stu-id="ea753-120">Optional fault tolerance support</span></span>
- <span data-ttu-id="ea753-121">Actualización diferida del sistema de archivos FAT secundario</span><span class="sxs-lookup"><span data-stu-id="ea753-121">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="ea753-122">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="ea753-122">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="ea753-123">API intuitivas de acceso a medios, que incluyen:</span><span class="sxs-lookup"><span data-stu-id="ea753-123">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="ea753-124">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="ea753-124">fx_media_open</span></span>
  - <span data-ttu-id="ea753-125">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="ea753-125">fx_media_close</span></span>
  - <span data-ttu-id="ea753-126">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="ea753-126">fx_media_format</span></span>
  - <span data-ttu-id="ea753-127">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="ea753-127">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="ea753-128">Servicios de directorio</span><span class="sxs-lookup"><span data-stu-id="ea753-128">Directory Services</span></span>

- <span data-ttu-id="ea753-129">Rutas de acceso de hasta 256 bytes</span><span class="sxs-lookup"><span data-stu-id="ea753-129">Up to 256 byte paths</span></span>
- <span data-ttu-id="ea753-130">Se admiten nombres largos y de directorio 8.3</span><span class="sxs-lookup"><span data-stu-id="ea753-130">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="ea753-131">Creación y eliminación de directorios</span><span class="sxs-lookup"><span data-stu-id="ea753-131">Directory create & delete</span></span>
- <span data-ttu-id="ea753-132">Navegación y recorrido de directorios</span><span class="sxs-lookup"><span data-stu-id="ea753-132">Directory navigation and traversal</span></span>
- <span data-ttu-id="ea753-133">Administración de atributos de directorios</span><span class="sxs-lookup"><span data-stu-id="ea753-133">Directory attributes management</span></span>
- <span data-ttu-id="ea753-134">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="ea753-134">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="ea753-135">API intuitivas de acceso a directorios, que incluyen:</span><span class="sxs-lookup"><span data-stu-id="ea753-135">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="ea753-136">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="ea753-136">fx_directory_create</span></span>
  - <span data-ttu-id="ea753-137">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ea753-137">fx_directory_delete</span></span>
  - <span data-ttu-id="ea753-138">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ea753-138">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="ea753-139">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ea753-139">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="ea753-140">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="ea753-140">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="ea753-141">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="ea753-141">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="ea753-142">Servicios de archivos</span><span class="sxs-lookup"><span data-stu-id="ea753-142">File Services</span></span>

- <span data-ttu-id="ea753-143">Memoria FLASH mínima de 3,3 KB</span><span class="sxs-lookup"><span data-stu-id="ea753-143">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="ea753-144">Archivos abiertos ilimitados</span><span class="sxs-lookup"><span data-stu-id="ea753-144">Unlimited open files</span></span>
- <span data-ttu-id="ea753-145">Los archivos de solo lectura se pueden abrir varias veces</span><span class="sxs-lookup"><span data-stu-id="ea753-145">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="ea753-146">Se admiten nombres largos y de directorio 8.3</span><span class="sxs-lookup"><span data-stu-id="ea753-146">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="ea753-147">Compatibilidad con archivos contiguos</span><span class="sxs-lookup"><span data-stu-id="ea753-147">Contiguous file support</span></span>
- <span data-ttu-id="ea753-148">Lógica de búsqueda rápida</span><span class="sxs-lookup"><span data-stu-id="ea753-148">Fast seek logic</span></span>
- <span data-ttu-id="ea753-149">Asignación previa de clústeres</span><span class="sxs-lookup"><span data-stu-id="ea753-149">Pre-allocation of clusters</span></span>
- <span data-ttu-id="ea753-150">Creación, eliminación y cambio de nombre de archivos</span><span class="sxs-lookup"><span data-stu-id="ea753-150">File create, delete, and rename</span></span>
- <span data-ttu-id="ea753-151">Lectura, escritura y visualización de archivos</span><span class="sxs-lookup"><span data-stu-id="ea753-151">File read, write, and see</span></span>
- <span data-ttu-id="ea753-152">Administración de atributos de archivo</span><span class="sxs-lookup"><span data-stu-id="ea753-152">File attributes management</span></span>
- <span data-ttu-id="ea753-153">Seguimiento de nivel de sistema mediante Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="ea753-153">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="ea753-154">API intuitivas de acceso a archivos, que incluyen:</span><span class="sxs-lookup"><span data-stu-id="ea753-154">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="ea753-155">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="ea753-155">fx_file_create</span></span>
  - <span data-ttu-id="ea753-156">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="ea753-156">fx_file_delete</span></span>
  - <span data-ttu-id="ea753-157">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="ea753-157">fx_file_attributes_set</span></span>
  - <span data-ttu-id="ea753-158">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="ea753-158">fx_file_attributes_read</span></span>
  - <span data-ttu-id="ea753-159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="ea753-159">fx_file_read</span></span>
  - <span data-ttu-id="ea753-160">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="ea753-160">fx_file_seek</span></span>
  - <span data-ttu-id="ea753-161">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="ea753-161">fx_file_write</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="ea753-162">Tecnología avanzada</span><span class="sxs-lookup"><span data-stu-id="ea753-162">Advanced technology</span></span>

<span data-ttu-id="ea753-163">Azure RTOS FileX es tecnología avanzada que incluye lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="ea753-163">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="ea753-164">Compatibilidad con FAT 12/16/32 y exFAT</span><span class="sxs-lookup"><span data-stu-id="ea753-164">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="ea753-165">Compatibilidad con varias particiones</span><span class="sxs-lookup"><span data-stu-id="ea753-165">Multiple partition support</span></span>
- <span data-ttu-id="ea753-166">Escalado automático</span><span class="sxs-lookup"><span data-stu-id="ea753-166">Automatic scaling</span></span>
- <span data-ttu-id="ea753-167">Endian neutro</span><span class="sxs-lookup"><span data-stu-id="ea753-167">Endian neutral</span></span>
- <span data-ttu-id="ea753-168">Soporte para nombres de archivo largos y 8.3</span><span class="sxs-lookup"><span data-stu-id="ea753-168">Long file name and 8.3 support</span></span>
- <span data-ttu-id="ea753-169">Compatibilidad con tolerancia a errores opcional</span><span class="sxs-lookup"><span data-stu-id="ea753-169">Optional fault tolerance support</span></span>
- <span data-ttu-id="ea753-170">Caché del sector lógico</span><span class="sxs-lookup"><span data-stu-id="ea753-170">Logical sector cache</span></span>
- <span data-ttu-id="ea753-171">Caché de entrada FAT</span><span class="sxs-lookup"><span data-stu-id="ea753-171">FAT entry cache</span></span>
- <span data-ttu-id="ea753-172">Asignación previa de clústeres</span><span class="sxs-lookup"><span data-stu-id="ea753-172">Pre-allocation of clusters</span></span>
- <span data-ttu-id="ea753-173">Compatibilidad con archivos contiguos</span><span class="sxs-lookup"><span data-stu-id="ea753-173">Contiguous file support</span></span>
- <span data-ttu-id="ea753-174">Métricas de rendimiento opcionales</span><span class="sxs-lookup"><span data-stu-id="ea753-174">Optional performance metrics</span></span>
- <span data-ttu-id="ea753-175">Compatibilidad con el análisis del sistema de Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="ea753-175">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="ea753-176">Distribución del uso de la memoria NOR / NAND (Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="ea753-176">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="ea753-177">Azure RTOS LevelX es el producto de distribución del uso de memoria NOR / NAND FLASH de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ea753-177">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="ea753-178">Azure RTOS LevelX se puede usar con FileX o como una biblioteca independiente de sectores FLASH de lectura / escritura directa para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ea753-178">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>
