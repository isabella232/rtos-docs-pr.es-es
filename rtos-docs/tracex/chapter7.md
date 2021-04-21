---
title: 'Capítulo 7: Eventos de seguimiento de Azure RTOS FileX'
description: Este capítulo contiene una descripción de los eventos de Azure RTOS FileX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: c3cbc945e33b87b6759c56ec1429d6bf57259bd9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815714"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a><span data-ttu-id="de49c-103">Capítulo 7: Eventos de seguimiento de Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="de49c-103">Chapter 7 - Azure RTOS FileX trace events</span></span>

<span data-ttu-id="de49c-104">Este capítulo contiene una descripción de los eventos de Azure RTOS FileX.</span><span class="sxs-lookup"><span data-stu-id="de49c-104">This chapter contains a description of the Azure RTOS FileX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="de49c-105">Lista de eventos e iconos</span><span class="sxs-lookup"><span data-stu-id="de49c-105">List of Events and Icons</span></span>

<span data-ttu-id="de49c-106">**En la siguiente lista se enumeran eventos de FileX mostrados por TraceX.**</span><span class="sxs-lookup"><span data-stu-id="de49c-106">**The following is a list of FileX events displayed by TraceX.**</span></span>

<span data-ttu-id="de49c-107">En la siguiente lista se describe cada uno de ellos:</span><span class="sxs-lookup"><span data-stu-id="de49c-107">The following describes each event:</span></span>

| <span data-ttu-id="de49c-108">**Icono**</span><span class="sxs-lookup"><span data-stu-id="de49c-108">**Icon**</span></span>                         | <span data-ttu-id="de49c-109">**Significado**</span><span class="sxs-lookup"><span data-stu-id="de49c-109">**Meaning**</span></span>                               |
| -------------------------------- | ----------------------------------------- |
| ![Icono de error de caché del sector lógico interno](./media/user-guide/fx-events/image1.png)    | <span data-ttu-id="de49c-111">Error de caché del sector lógico interno</span><span class="sxs-lookup"><span data-stu-id="de49c-111">Internal Logical Sector Cache Miss</span></span> |
| ![Icono de error de caché del directorio interno](./media/user-guide/fx-events/image2.png)    | <span data-ttu-id="de49c-113">Error de caché del directorio interno</span><span class="sxs-lookup"><span data-stu-id="de49c-113">Internal Directory Cache Miss</span></span> |
| ![Icono de vaciado de elementos multimedia internos](./media/user-guide/fx-events/image3.png)    | <span data-ttu-id="de49c-115">Vaciado de elementos multimedia internos</span><span class="sxs-lookup"><span data-stu-id="de49c-115">Internal Media Flush</span></span> |
| ![Icono de lectura de entrada de directorio interno](./media/user-guide/fx-events/image4.png)    | <span data-ttu-id="de49c-117">Lectura de entrada de directorio interno</span><span class="sxs-lookup"><span data-stu-id="de49c-117">Internal Directory Entry Read</span></span> |
| ![Icono de escritura de entrada de directorio interno](./media/user-guide/fx-events/image5.png)    | <span data-ttu-id="de49c-119">Escritura de entrada de directorio interno</span><span class="sxs-lookup"><span data-stu-id="de49c-119">Internal Directory Entry Write</span></span> |
| ![Icono de lectura del controlador de E/S interno](./media/user-guide/fx-events/image6.png)    | <span data-ttu-id="de49c-121">Lectura del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-121">Internal I/O Driver Read</span></span> |
| ![Icono de escritura del controlador de E/S interno](./media/user-guide/fx-events/image7.png)    | <span data-ttu-id="de49c-123">Escritura del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-123">Internal I/O Driver Write</span></span> |
| ![Icono de vaciado de controlador de E/S interno](./media/user-guide/fx-events/image8.png)    | <span data-ttu-id="de49c-125">Vaciado de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-125">Internal I/O Driver Flush</span></span> |
| ![Icono de anulación de controlador de E/S interno](./media/user-guide/fx-events/image9.png)    | <span data-ttu-id="de49c-127">Anulación de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-127">Internal I/O Driver Abort</span></span> |
| ![Icono de inicialización de controlador de E/S interno](./media/user-guide/fx-events/image10.png)    | <span data-ttu-id="de49c-129">Inicialización de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-129">Internal I/O Driver Initialize</span></span> |
| ![Icono de lectura de controlador de E/S interno](./media/user-guide/fx-events/image11.png)    | <span data-ttu-id="de49c-131">Lectura de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-131">Internal I/O Driver Boot Read</span></span> |
| ![Icono de sectores de versión de controlador de E/S interno](./media/user-guide/fx-events/image12.png)    | <span data-ttu-id="de49c-133">Sectores de versión de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-133">Internal I/O Driver Release Sectors</span></span> |
| ![Icono de escritura de controlador de E/S interno](./media/user-guide/fx-events/image13.png)    | <span data-ttu-id="de49c-135">Escritura de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-135">Internal I/O Driver Boot Write</span></span> |
| ![Icono de anulación de inicialización de controlador de E/S interno](./media/user-guide/fx-events/image14.png)    | <span data-ttu-id="de49c-137">Anulación de inicialización de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-137">Internal I / O Driver Driver Un-initialize</span></span> |
| ![Icono de lectura de atributos de directorio](./media/user-guide/fx-events/image15.png)    | <span data-ttu-id="de49c-139">**Lectura de atributos de directorio** (*fx_directory_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="de49c-139">**Directory Attributes Read** (*fx_directory_attributes_read*)</span></span> |
| ![Icono de definición de atributos de directorio](./media/user-guide/fx-events/image16.png)    | <span data-ttu-id="de49c-141">**Definición de atributos de directorio** (*fx_directory_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="de49c-141">**Directory Attributes Set** (*fx_directory_attributes_set*)</span></span> |
| ![Icono de creación de directorio](./media/user-guide/fx-events/image17.png)    | <span data-ttu-id="de49c-143">**Creación de directorio** (*fx_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="de49c-143">**Directory Create** (*fx_directory_create*)</span></span> |
| ![Icono de obtención predeterminada de directorio](./media/user-guide/fx-events/image18.png)    | <span data-ttu-id="de49c-145">**Obtención predeterminada de directorio** (*fx_directory_default_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-145">**Directory Default Get** (*fx_directory_default_get*)</span></span> |
| ![Icono de definición predeterminada de directorio](./media/user-guide/fx-events/image19.png)    | <span data-ttu-id="de49c-147">**Definición predeterminada de directorio** (*fx_directory_default_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-147">**Directory Default Set** (*fx_directory_default_set*)</span></span> |
| ![Icono de eliminación de directorio](./media/user-guide/fx-events/image20.png)    | <span data-ttu-id="de49c-149">**Eliminación de directorio** (*fx_directory_delete*)</span><span class="sxs-lookup"><span data-stu-id="de49c-149">**Directory Delete** (*fx_directory_delete*)</span></span> |
| ![Icono de búsqueda de primera entrada de directorio](./media/user-guide/fx-events/image21.png)    | <span data-ttu-id="de49c-151">**Búsqueda de primera entrada de directorio** (*fx_directory_first_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="de49c-151">**Directory First Entry Find** (*fx_directory_first_entry_find*)</span></span> |
| ![Icono de búsqueda de primera entrada completa de directorio](./media/user-guide/fx-events/image22.png)    | <span data-ttu-id="de49c-153">**Búsqueda de primera entrada completa de directorio** (*fx_directory_first_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="de49c-153">**Directory First Full Entry Find** (*fx_directory_first_full_entry_find*)</span></span> |
| ![Icono de obtención de información de directorio](./media/user-guide/fx-events/image23.png)    | <span data-ttu-id="de49c-155">**Obtención de información de directorio** (*fx_directory_information_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-155">**Directory Information Get** (*fx_directory_information_get*)</span></span> |
| ![Icono de borrado de ruta local de directorio](./media/user-guide/fx-events/image24.png)    | <span data-ttu-id="de49c-157">**Borrado de ruta local de directorio** (*fx_directory_local_path_clear*)</span><span class="sxs-lookup"><span data-stu-id="de49c-157">**Directory Local Path Clear** (*fx_directory_local_path_clear*)</span></span> |
| ![Icono de obtención de ruta de acceso local de directorio](./media/user-guide/fx-events/image25.png)    | <span data-ttu-id="de49c-159">**Obtención de ruta de acceso local de directorio** (*fx_directory_local_path_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-159">**Directory Local Path Get** (*fx_directory_local_path_get*)</span></span> |
| ![Icono de restauración de ruta de acceso local de directorio](./media/user-guide/fx-events/image26.png)    | <span data-ttu-id="de49c-161">**Restauración de ruta de acceso local de directorio** (*fx_directory_local_path_restore*)</span><span class="sxs-lookup"><span data-stu-id="de49c-161">**Directory Local Path Restore** (*fx_directory_local_path_restore*)</span></span> |
| ![Icono de definición de ruta de acceso local de directorio](./media/user-guide/fx-events/image27.png)    | <span data-ttu-id="de49c-163">**Definición de ruta de acceso local de directorio** (*fx_directory_local_path_set*)</span><span class="sxs-lookup"><span data-stu-id="de49c-163">**Directory Local Path Set** (*fx_directory_local_path_set*)</span></span> |
| ![Icono de obtención de nombre largo de directorio](./media/user-guide/fx-events/image28.png)    | <span data-ttu-id="de49c-165">**Obtención de nombre largo de directorio** (*fx_directory_long_name_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-165">**Directory Long Name Get** (*fx_directory_long_name_get*)</span></span> |
| ![Icono de prueba de nombre de directorio](./media/user-guide/fx-events/image29.png)    | <span data-ttu-id="de49c-167">**Prueba de nombre de directorio** (*fx_directory_name_test*)</span><span class="sxs-lookup"><span data-stu-id="de49c-167">**Directory Name Test** (*fx_directory_name_test*)</span></span> |
| ![Icono de búsqueda de siguiente entrada de directorio](./media/user-guide/fx-events/image30.png)    | <span data-ttu-id="de49c-169">**Búsqueda de siguiente entrada de directorio** (*fx_directory_next_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="de49c-169">**Directory Next Entry Find** (*fx_directory_next_entry_find*)</span></span> |
| ![Icono de búsqueda de siguiente entrada completa de directorio](./media/user-guide/fx-events/image31.png)    | <span data-ttu-id="de49c-171">**Búsqueda de siguiente entrada completa de directorio** (*fx_directory_next_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="de49c-171">**Directory Next Full Entry Find** (*fx_directory_next_full_entry_find*)</span></span> |
| ![Icono de cambio de nombre de directorio](./media/user-guide/fx-events/image32.png)    | <span data-ttu-id="de49c-173">**Cambio de nombre de directorio** (*fx_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="de49c-173">**Directory Rename** (*fx_directory_rename*)</span></span> |
| ![Icono de obtención de nombre corto de directorio](./media/user-guide/fx-events/image33.png)    | <span data-ttu-id="de49c-175">**Obtención de nombre corto de directorio** (*fx_directory_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-175">**Directory Short Name Get** (*fx_directory_short_name_get*)</span></span> |
| ![Icono de asignación de archivos](./media/user-guide/fx-events/image34.png)    | <span data-ttu-id="de49c-177">**Asignación de archivos** (*fx_file_allocate*)</span><span class="sxs-lookup"><span data-stu-id="de49c-177">**File Allocate** (*fx_file_allocate*)</span></span> |
| ![Icono de lectura de atributos de archivos](./media/user-guide/fx-events/image35.png)    | <span data-ttu-id="de49c-179">**Lectura de atributos de archivos** (*fx_file_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="de49c-179">**File Attributes Read** (*fx_file_attributes_read*)</span></span> |
| ![Icono de definición de atributos de archivos](./media/user-guide/fx-events/image36.png)    | <span data-ttu-id="de49c-181">**Definición de atributos de archivos** (*fx_file_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="de49c-181">**File Attributes Set** (*fx_file_attributes_set*)</span></span> |
| ![Icono de asignación de mejor esfuerzo de archivo](./media/user-guide/fx-events/image37.png)    | <span data-ttu-id="de49c-183">**Asignación de mejor esfuerzo de archivo** (*fx_file_best_effort_allocate*)</span><span class="sxs-lookup"><span data-stu-id="de49c-183">**File Best Effort Allocate** (*fx_file_best_effort_allocate*)</span></span> |
| ![Icono de cierre de archivo](./media/user-guide/fx-events/image38.png)    | <span data-ttu-id="de49c-185">**Cierre de archivo** (*fx_file_close*)</span><span class="sxs-lookup"><span data-stu-id="de49c-185">**File Close** (*fx_file_close*)</span></span> |
| ![Icono de creación de archivo](./media/user-guide/fx-events/image39.png)    | <span data-ttu-id="de49c-187">**Creación de archivo** (*fx_file_create*)</span><span class="sxs-lookup"><span data-stu-id="de49c-187">**File Create** (*fx_file_create*)</span></span> |
| ![Icono de definición de fecha y hora de archivo](./media/user-guide/fx-events/image40.png)    | <span data-ttu-id="de49c-189">**Definición de fecha y hora de archivo** (*fx_file_date_time_set*)</span><span class="sxs-lookup"><span data-stu-id="de49c-189">**File Date Time Set** (*fx_file_date_time_set*)</span></span> |
| ![Icono de eliminación de archivo](./media/user-guide/fx-events/image41.png)    | <span data-ttu-id="de49c-191">**Eliminación de archivo** (*fx_file_delete*)</span><span class="sxs-lookup"><span data-stu-id="de49c-191">**File Delete** (*fx_file_delete*)</span></span> |
| ![Icono de apertura de archivo](./media/user-guide/fx-events/image42.png)    | <span data-ttu-id="de49c-193">**Apertura de archivo** (*fx_file_open*)</span><span class="sxs-lookup"><span data-stu-id="de49c-193">**File Open** (*fx_file_open*)</span></span> |
| ![Icono de lectura de archivo](./media/user-guide/fx-events/image43.png)    | <span data-ttu-id="de49c-195">**Lectura de archivo** (*fx_file_read*)</span><span class="sxs-lookup"><span data-stu-id="de49c-195">**File Read** (*fx_file_read*)</span></span> |
| ![Icono de búsqueda relativa de archivo](./media/user-guide/fx-events/image44.png)    | <span data-ttu-id="de49c-197">**Búsqueda relativa de archivo** (*fx_file_relative_seek*)</span><span class="sxs-lookup"><span data-stu-id="de49c-197">**File Relative Seek** (*fx_file_relative_seek*)</span></span> |
| ![Icono de cambio de nombre de archivo](./media/user-guide/fx-events/image45.png)    | <span data-ttu-id="de49c-199">**Cambio de nombre de archivo** (*fx_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="de49c-199">**File Rename** (*fx_file_rename*)</span></span> |
| ![Icono de búsqueda de archivo](./media/user-guide/fx-events/image46.png)    | <span data-ttu-id="de49c-201">**Búsqueda de archivo** (*fx_file_seek*)</span><span class="sxs-lookup"><span data-stu-id="de49c-201">**File Seek** (*fx_file_seek*)</span></span> |
| ![Icono de truncamiento de archivo](./media/user-guide/fx-events/image47.png)    | <span data-ttu-id="de49c-203">**Truncamiento de archivo** (*fx_file_truncate*)</span><span class="sxs-lookup"><span data-stu-id="de49c-203">**File Truncate** (*fx_file_truncate*)</span></span> |
| ![Icono de versión de truncamiento de archivo](./media/user-guide/fx-events/image48.png)    | <span data-ttu-id="de49c-205">**Versión de truncamiento de archivo** (*fx_file_truncate_release*)</span><span class="sxs-lookup"><span data-stu-id="de49c-205">**File Truncate Release** (*fx_file_truncate_release*)</span></span> |
| ![Icono de escritura de archivo](./media/user-guide/fx-events/image49.png)    | <span data-ttu-id="de49c-207">**Escritura de archivo** (*fx_file_write*)</span><span class="sxs-lookup"><span data-stu-id="de49c-207">**File Write** (*fx_file_write*)</span></span> |
| ![Icono de anulación de elementos multimedia](./media/user-guide/fx-events/image50.png)    | <span data-ttu-id="de49c-209">**Anulación de elementos multimedia** (*fx_media_abort*)</span><span class="sxs-lookup"><span data-stu-id="de49c-209">**Media Abort** (*fx_media_abort*)</span></span> |
| ![Icono de invalidación de caché de elementos multimedia](./media/user-guide/fx-events/image51.png)    | <span data-ttu-id="de49c-211">**Invalidación de caché de elementos multimedia** (*fx_media_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="de49c-211">**Media Cache Invalidate** (*fx_media_cache_invalidate*)</span></span> |
| ![Icono de comprobación de elementos multimedia](./media/user-guide/fx-events/image52.png)    | <span data-ttu-id="de49c-213">**Comprobación de elementos multimedia** (*fx_media_check*)</span><span class="sxs-lookup"><span data-stu-id="de49c-213">**Media Check** (*fx_media_check*)</span></span> |
| ![\*Icono de cierre de elementos multimedia](./media/user-guide/fx-events/image53.png)    | <span data-ttu-id="de49c-215">**Cierre de elementos multimedia** (*fx_media_close*)</span><span class="sxs-lookup"><span data-stu-id="de49c-215">**Media Close** (*fx_media_close*)</span></span> |
| ![Icono de vaciado de elementos multimedia](./media/user-guide/fx-events/image54.png)    | <span data-ttu-id="de49c-217">**Vaciado de elementos multimedia** (*fx_media_flush*)</span><span class="sxs-lookup"><span data-stu-id="de49c-217">**Media Flush** (*fx_media_flush*)</span></span> |
| ![Icono de formato de elementos multimedia](./media/user-guide/fx-events/image55.png)    | <span data-ttu-id="de49c-219">**Formato de elementos multimedia** (*fx_media_format*)</span><span class="sxs-lookup"><span data-stu-id="de49c-219">**Media Format** (*fx_media_format*)</span></span> |
| ![Icono de apertura de elementos multimedia](./media/user-guide/fx-events/image56.png)    | <span data-ttu-id="de49c-221">**Apertura de elementos multimedia** (*fx_media_open*)</span><span class="sxs-lookup"><span data-stu-id="de49c-221">**Media Open** (*fx_media_open*)</span></span> |
| ![Icono de lectura de elementos multimedia](./media/user-guide/fx-events/image57.png)    | <span data-ttu-id="de49c-223">**Lectura de elementos multimedia** (*fx_media_read*)</span><span class="sxs-lookup"><span data-stu-id="de49c-223">**Media Read** (*fx_media_read*)</span></span> |
| ![Icono de espacio de elementos multimedia disponible](./media/user-guide/fx-events/image58.png)    | <span data-ttu-id="de49c-225">**Espacio de elementos multimedia disponible** (*fx_media_space_available*)</span><span class="sxs-lookup"><span data-stu-id="de49c-225">**Media Space Available** (*fx_media_space_available*)</span></span> |
| ![Icono de obtención de volumen de elementos multimedia](./media/user-guide/fx-events/image59.png)    | <span data-ttu-id="de49c-227">**Obtención de volumen de elementos multimedia** (*fx_media_volume_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-227">**Media Volume Get** (*fx_media_volume_get*)</span></span> |
| ![Icono de definición de volúmenes de elementos multimedia](./media/user-guide/fx-events/image60.png)    | <span data-ttu-id="de49c-229">**Definición de volúmenes de elementos multimedia** (*fx_media_volume_set*)</span><span class="sxs-lookup"><span data-stu-id="de49c-229">**Media Volume Set** (*fx_media_volume_set*)</span></span> |
| ![Icono de escritura de elementos multimedia](./media/user-guide/fx-events/image61.png)    | <span data-ttu-id="de49c-231">**Escritura de medios multimedia** (*fx_media_write*)</span><span class="sxs-lookup"><span data-stu-id="de49c-231">**Media Write** (*fx_media_write*)</span></span> |
| ![Icono de obtención de fecha del sistema](./media/user-guide/fx-events/image62.png)    | <span data-ttu-id="de49c-233">**Obtención de fecha del sistema** (*fx_system_date_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-233">**System Date Get** (*fx_system_date_get*)</span></span> |
| ![Icono de definición de fecha del sistema](./media/user-guide/fx-events/image63.png)    | <span data-ttu-id="de49c-235">**Definición de fecha del sistema** (*fx_system_date_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-235">**System Date Set** (*fx_system_date_set*)</span></span> |
| ![Icono de inicialización del sistema](./media/user-guide/fx-events/image64.png)    | <span data-ttu-id="de49c-237">**Inicialización del sistema** (*fx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="de49c-237">**System Initialize** (*fx_system_initialize*)</span></span> |
| ![Icono de obtención de hora del sistema](./media/user-guide/fx-events/image65.png)    | <span data-ttu-id="de49c-239">**Obtención de hora del sistema** (*fx_system_time_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-239">**System Time Get** (*fx_system_time_get*)</span></span> |
| ![Icono de definición de hora del sistema](./media/user-guide/fx-events/image66.png)    | <span data-ttu-id="de49c-241">**Definición de hora del sistema** (*fx_system_time_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-241">**System Time Set** (*fx_system_time_set*)</span></span> |
| ![Icono de creación de directorio Unicode](./media/user-guide/fx-events/image67.png)    | <span data-ttu-id="de49c-243">**Creación de directorio Unicode** (*fx_unicode_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="de49c-243">**Unicode Directory Create** (*fx_unicode_directory_create*)</span></span> |
| ![Icono de cambio de nombre de directorio Unicode](./media/user-guide/fx-events/image68.png)    | <span data-ttu-id="de49c-245">**Cambio de nombre de directorio Unicode** (*fx_unicode_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="de49c-245">**Unicode Directory Rename** (*fx_unicode_directory_rename*)</span></span> |
| ![Icono de creación de archivo Unicode](./media/user-guide/fx-events/image69.png)    | <span data-ttu-id="de49c-247">**Creación de archivo Unicode** (*fx_unicode_file_create*)</span><span class="sxs-lookup"><span data-stu-id="de49c-247">**Unicode File Create** (*fx_unicode_file_create*)</span></span> |
| ![Icono de cambio de nombre de archivo Unicode](./media/user-guide/fx-events/image70.png)    | <span data-ttu-id="de49c-249">**Cambio de nombre de archivo Unicode** (*fx_unicode_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="de49c-249">**Unicode File Rename** (*fx_unicode_file_rename*)</span></span> |
| ![Icono de obtención de longitud Unicode](./media/user-guide/fx-events/image71.png)    | <span data-ttu-id="de49c-251">**Obtención de longitud Unicode** (*fx_unicode_length_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-251">**Unicode Lenght Get** (*fx_unicode_length_get*)</span></span> |
| ![Icono de obtención de nombre Unicode](./media/user-guide/fx-events/image72.png)    | <span data-ttu-id="de49c-253">**Obtención de nombre Unicode** (*fx_unicode_name_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-253">**Unicode Name Get** (*fx_unicode_name_get*)</span></span> |
| ![Icono de obtención de nombre corto Unicode](./media/user-guide/fx-events/image73.png)    | <span data-ttu-id="de49c-255">**Obtención de nombre corto Unicode** (*fx_unicode_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="de49c-255">**Unicode Short Name Get** (*fx_unicode_short_name_get*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="de49c-256">Descripciones de eventos</span><span class="sxs-lookup"><span data-stu-id="de49c-256">Event Descriptions</span></span>

<span data-ttu-id="de49c-257">A continuación se describe cada evento individual.</span><span class="sxs-lookup"><span data-stu-id="de49c-257">The following describes each individual event.</span></span>

### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="de49c-258">Error de caché del sector lógico interno</span><span class="sxs-lookup"><span data-stu-id="de49c-258">Internal Logical Sector Cache Miss</span></span> 

#### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="de49c-259">Error de caché del sector lógico interno</span><span class="sxs-lookup"><span data-stu-id="de49c-259">Internal logical sector cache miss</span></span>

<span data-ttu-id="de49c-260">**Icono** ![Icono de error de caché del sector lógico interno](./media/user-guide/fx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-260">**Icon** ![Internal logical sector cache miss icon](./media/user-guide/fx-events/image1.png)</span></span>

<span data-ttu-id="de49c-261">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-261">**Description**</span></span>

<span data-ttu-id="de49c-262">Este evento representa un error de caché del sector lógico FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-262">This event represents an internal FileX logical sector cache miss.</span></span>

<span data-ttu-id="de49c-263">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-263">**Information Fields**</span></span>

- <span data-ttu-id="de49c-264">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-264">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-265">Campo de información 2: sector.</span><span class="sxs-lookup"><span data-stu-id="de49c-265">Info Field 2: Sector.</span></span>
- <span data-ttu-id="de49c-266">Campo de información 3: total de líneas no ejecutadas.</span><span class="sxs-lookup"><span data-stu-id="de49c-266">Info Field 3: Total misses.</span></span>
- <span data-ttu-id="de49c-267">Campo de información 4: tamaño de caché.</span><span class="sxs-lookup"><span data-stu-id="de49c-267">Info Field 4: Cache size.</span></span>

### <a name="internal-directory-cache-miss"></a><span data-ttu-id="de49c-268">Error de caché del directorio interno</span><span class="sxs-lookup"><span data-stu-id="de49c-268">Internal Directory Cache Miss</span></span>

#### <a name="internal-directory-cache-miss"></a><span data-ttu-id="de49c-269">Error de caché del directorio interno</span><span class="sxs-lookup"><span data-stu-id="de49c-269">Internal directory cache miss</span></span>

<span data-ttu-id="de49c-270">**Icono** ![Icono de error de caché del directorio interno](./media/user-guide/fx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-270">**Icon** ![Internal directory cache miss icon](./media/user-guide/fx-events/image2.png)</span></span>

<span data-ttu-id="de49c-271">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-271">**Description**</span></span> 

<span data-ttu-id="de49c-272">Este evento representa un error de caché del directorio FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-272">This event represents an internal FileX directory cache miss.</span></span>

<span data-ttu-id="de49c-273">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-273">**Information Fields**</span></span>

- <span data-ttu-id="de49c-274">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-274">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-275">Campo de información 2: total de líneas no ejecutadas.</span><span class="sxs-lookup"><span data-stu-id="de49c-275">Info Field 2: Total misses.</span></span>
- <span data-ttu-id="de49c-276">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-276">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-277">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-277">Info Field 4: Not used.</span></span>

### <a name="internal-media-flush"></a><span data-ttu-id="de49c-278">Vaciado de elementos multimedia internos</span><span class="sxs-lookup"><span data-stu-id="de49c-278">Internal Media Flush</span></span> 

#### <a name="internal-media-flush"></a><span data-ttu-id="de49c-279">Vaciado de elementos multimedia internos</span><span class="sxs-lookup"><span data-stu-id="de49c-279">Internal media flush</span></span>

<span data-ttu-id="de49c-280">**Icono** ![Icono de vaciado interno de elementos multimedia](./media/user-guide/fx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-280">**Icon** ![Internal media flush icon](./media/user-guide/fx-events/image3.png)</span></span>

<span data-ttu-id="de49c-281">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-281">**Description**</span></span>

<span data-ttu-id="de49c-282">Este evento representa un vaciado interno de elementos multimedia FileX.</span><span class="sxs-lookup"><span data-stu-id="de49c-282">This event represents an internal FileX media flush.</span></span>

<span data-ttu-id="de49c-283">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-283">**Information Fields**</span></span>

- <span data-ttu-id="de49c-284">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-284">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-285">Campo de información 2: número de sectores sucios.</span><span class="sxs-lookup"><span data-stu-id="de49c-285">Info Field 2: Number of dirty sectors.</span></span>
- <span data-ttu-id="de49c-286">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-286">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-287">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-287">Info Field 4: Not used.</span></span>


### <a name="internal-directory-entry-read"></a><span data-ttu-id="de49c-288">Lectura de entrada de directorio interno</span><span class="sxs-lookup"><span data-stu-id="de49c-288">Internal Directory Entry Read</span></span> 

#### <a name="internal-directory-entry-read"></a><span data-ttu-id="de49c-289">Lectura de entrada de directorio interno</span><span class="sxs-lookup"><span data-stu-id="de49c-289">Internal directory entry read</span></span>

<span data-ttu-id="de49c-290">**Icono** ![Icono de lectura de entrada de directorio interno](./media/user-guide/fx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-290">**Icon** ![Internal directory entry read icon](./media/user-guide/fx-events/image4.png)</span></span>

<span data-ttu-id="de49c-291">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-291">**Description**</span></span>

<span data-ttu-id="de49c-292">Este evento representa un evento de lectura de entrada del directorio FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-292">This event represents an internal FileX directory entry read event.</span></span>

<span data-ttu-id="de49c-293">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-293">**Information Fields**</span></span>

- <span data-ttu-id="de49c-294">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-294">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-295">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-295">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-296">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-296">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-297">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-297">Info Field 4: Not used.</span></span>

### <a name="internal-directory-entry-write"></a><span data-ttu-id="de49c-298">Escritura de entrada de directorio interno</span><span class="sxs-lookup"><span data-stu-id="de49c-298">Internal Directory Entry Write</span></span>

#### <a name="internal-directory-entry-write"></a><span data-ttu-id="de49c-299">Escritura de entrada de directorio interno</span><span class="sxs-lookup"><span data-stu-id="de49c-299">Internal directory entry write</span></span>

<span data-ttu-id="de49c-300">**Icono** ![Icono de escritura de entrada de directorio interno](./media/user-guide/fx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-300">**Icon** ![Internal directory entry write icon](./media/user-guide/fx-events/image5.png)</span></span>

<span data-ttu-id="de49c-301">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-301">**Description**</span></span>

<span data-ttu-id="de49c-302">Este evento representa un evento de escritura de entrada de directorio de FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-302">This event represents an internal FileX directory entry write event.</span></span>

<span data-ttu-id="de49c-303">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-303">**Information Fields**</span></span>

- <span data-ttu-id="de49c-304">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-304">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-305">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-305">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-306">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-306">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-307">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-307">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-read"></a><span data-ttu-id="de49c-308">Lectura del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-308">Internal I/O Driver Read</span></span> 

#### <a name="internal-io-driver-read"></a><span data-ttu-id="de49c-309">Lectura del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-309">Internal I/O driver read</span></span> 

<span data-ttu-id="de49c-310">**Icono** ![Icono de lectura del controlador de E/S interno](./media/user-guide/fx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-310">**Icon** ![Internal I / O driver read icon](./media/user-guide/fx-events/image6.png)</span></span>

<span data-ttu-id="de49c-311">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-311">**Description**</span></span> 

<span data-ttu-id="de49c-312">Este evento representa un evento de lectura del controlador de E/S de FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-312">This event represents an internal FileX I/O driver read event.</span></span>

<span data-ttu-id="de49c-313">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-313">**Information Fields**</span></span>

- <span data-ttu-id="de49c-314">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-314">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-315">Campo de información 2: sector.</span><span class="sxs-lookup"><span data-stu-id="de49c-315">Info Field 2: Sector.</span></span>
- <span data-ttu-id="de49c-316">Campo de información 3: número de sectores.</span><span class="sxs-lookup"><span data-stu-id="de49c-316">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="de49c-317">Campo de información 4: puntero de búfer.</span><span class="sxs-lookup"><span data-stu-id="de49c-317">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-write"></a><span data-ttu-id="de49c-318">Escritura del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-318">Internal I/O Driver Write</span></span> 

#### <a name="internal-io-driver-write"></a><span data-ttu-id="de49c-319">Escritura del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-319">Internal I/O driver write</span></span> 

<span data-ttu-id="de49c-320">**Icono** ![Icono de escritura del controlador de E/S interno](./media/user-guide/fx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-320">**Icon** ![Internal I / O driver write icon](./media/user-guide/fx-events/image7.png)</span></span>

<span data-ttu-id="de49c-321">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-321">**Description**</span></span> 

<span data-ttu-id="de49c-322">Este evento representa un evento de escritura del controlador de E/S de FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-322">This event represents an internal FileX I/O driver write event.</span></span>

<span data-ttu-id="de49c-323">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-323">**Information Fields**</span></span>

- <span data-ttu-id="de49c-324">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-324">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-325">Campo de información 2: sector.</span><span class="sxs-lookup"><span data-stu-id="de49c-325">Info Field 2: Sector.</span></span>
- <span data-ttu-id="de49c-326">Campo de información 3: número de sectores.</span><span class="sxs-lookup"><span data-stu-id="de49c-326">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="de49c-327">Campo de información 4: puntero de búfer.</span><span class="sxs-lookup"><span data-stu-id="de49c-327">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-flush"></a><span data-ttu-id="de49c-328">Vaciado de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-328">Internal I/O Driver Flush</span></span> 

#### <a name="internal-io-driver-flush"></a><span data-ttu-id="de49c-329">Vaciado de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-329">Internal I/O driver flush</span></span> 

<span data-ttu-id="de49c-330">**Icono** ![Icono de vaciado de controlador de E/S interno](./media/user-guide/fx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-330">**Icon** ![Internal I / O driver flush icon](./media/user-guide/fx-events/image8.png)</span></span>

<span data-ttu-id="de49c-331">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-331">**Description**</span></span> 

<span data-ttu-id="de49c-332">Este evento representa un evento de vaciado de controlador de E/S FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-332">This event represents an internal FileX I/O driver flush event.</span></span>

<span data-ttu-id="de49c-333">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-333">**Information Fields**</span></span>

- <span data-ttu-id="de49c-334">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-334">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-335">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-335">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-336">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-336">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-337">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-337">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-abort"></a><span data-ttu-id="de49c-338">Anulación de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-338">Internal I/O Driver Abort</span></span> 

#### <a name="internal-io-dirver-abort"></a><span data-ttu-id="de49c-339">Anulación de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-339">Internal I/O dirver abort</span></span>

<span data-ttu-id="de49c-340">**Icono** ![Icono de anulación de controlador de E/S interno](./media/user-guide/fx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-340">**Icon** ![Internal I / O driver abort icon](./media/user-guide/fx-events/image9.png)</span></span>

<span data-ttu-id="de49c-341">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-341">**Description**</span></span>

<span data-ttu-id="de49c-342">Este evento representa un evento de anulación de controlador de E/S de FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-342">This event represents an internal FileX I/O driver abort event.</span></span>

<span data-ttu-id="de49c-343">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-343">**Information Fields**</span></span>

- <span data-ttu-id="de49c-344">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-344">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-345">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-345">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-346">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-346">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-347">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-347">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="de49c-348">Inicialización de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-348">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="de49c-349">Inicialización de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-349">Internal I/O driver initialize</span></span> 

<span data-ttu-id="de49c-350">**Icono** ![Icono de inicialización de controlador de E/S interno](./media/user-guide/fx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-350">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/fx-events/image10.png)</span></span>

<span data-ttu-id="de49c-351">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-351">**Description**</span></span> 

<span data-ttu-id="de49c-352">Este evento representa un evento de inicialización del controlador de E/S de FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-352">This event represents an internal FileX I/O driver initialize event.</span></span>

<span data-ttu-id="de49c-353">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-353">**Information Fields**</span></span>

- <span data-ttu-id="de49c-354">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-354">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-355">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-355">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-356">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-356">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-357">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-357">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="de49c-358">Lectura del sector de arranque del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-358">Internal I/O Driver Boot Sector Read</span></span> 

#### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="de49c-359">Lectura del sector de arranque del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-359">Internal I/O driver boot sector read</span></span> 

<span data-ttu-id="de49c-360">**Icono** ![Icono de lectura del sector de arranque del controlador de E/S interno](./media/user-guide/fx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-360">**Icon** ![Internal I / O driver boot sector read icon](./media/user-guide/fx-events/image11.png)</span></span>

<span data-ttu-id="de49c-361">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-361">**Description**</span></span> 

<span data-ttu-id="de49c-362">Este evento representa un evento de lectura del sector de arranque del controlador de E/S FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-362">This event represents an internal FileX I/O driver boot sector read event.</span></span>

<span data-ttu-id="de49c-363">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-363">**Information Fields**</span></span>

- <span data-ttu-id="de49c-364">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-364">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-365">Campo de información 2: puntero de búfer.</span><span class="sxs-lookup"><span data-stu-id="de49c-365">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="de49c-366">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-366">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-367">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-367">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="de49c-368">Sectores de versión de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-368">Internal I/O Driver Release Sectors</span></span> 

#### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="de49c-369">Sectores de versión de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-369">Internal I/O driver release sectors</span></span> 

<span data-ttu-id="de49c-370">**Icono** ![Icono de sectores de versión de controlador de E/S interno](./media/user-guide/fx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-370">**Icon** ![Internal I / O driver release sectors icon](./media/user-guide/fx-events/image12.png)</span></span>

<span data-ttu-id="de49c-371">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-371">**Description**</span></span> 

<span data-ttu-id="de49c-372">Este evento representa un evento de sectores de la versión del controlador de E/S de FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-372">This event represents an internal FileX I/O driver release sectors event.</span></span>

<span data-ttu-id="de49c-373">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-373">**Information Fields**</span></span>

- <span data-ttu-id="de49c-374">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-374">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-375">Campo de información 2: sector.</span><span class="sxs-lookup"><span data-stu-id="de49c-375">Info Field 2: Sector.</span></span>
- <span data-ttu-id="de49c-376">Campo de información 3: número de sectores.</span><span class="sxs-lookup"><span data-stu-id="de49c-376">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="de49c-377">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-377">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="de49c-378">Escritura del sector de arranque del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-378">Internal I/O Driver Boot Sector Write</span></span>

#### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="de49c-379">Escritura del sector de arranque del controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-379">Internal I/O driver boot sector write</span></span> 

<span data-ttu-id="de49c-380">**Icono** ![Escritura del sector de arranque del controlador de E/S interno](./media/user-guide/fx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-380">**Icon** ![Internal I / O driver boot sector write icon](./media/user-guide/fx-events/image13.png)</span></span>

<span data-ttu-id="de49c-381">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-381">**Description**</span></span> 

<span data-ttu-id="de49c-382">Este evento representa un evento de escritura del sector de arranque del controlador de E/S de FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-382">This event represents an internal FileX I/O driver boot sector write event.</span></span>

<span data-ttu-id="de49c-383">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-383">**Information Fields**</span></span>

- <span data-ttu-id="de49c-384">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-384">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-385">Campo de información 2: puntero de búfer.</span><span class="sxs-lookup"><span data-stu-id="de49c-385">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="de49c-386">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-386">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-387">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-387">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="de49c-388">Anulación de inicialización de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-388">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="de49c-389">Anulación de inicialización de controlador de E/S interno</span><span class="sxs-lookup"><span data-stu-id="de49c-389">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="de49c-390">**Icono** ![Icono de anulación de inicialización de controlador de E/S interno](./media/user-guide/fx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-390">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/fx-events/image14.png)</span></span>

<span data-ttu-id="de49c-391">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-391">**Description**</span></span> 

<span data-ttu-id="de49c-392">Este evento representa un evento de anulación de inicialización del controlador de E/S de FileX interno.</span><span class="sxs-lookup"><span data-stu-id="de49c-392">This event represents an internal FileX I/O driver un-initialize event.</span></span>

<span data-ttu-id="de49c-393">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-393">**Information Fields**</span></span>

- <span data-ttu-id="de49c-394">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-394">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-395">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-395">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-396">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-396">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-397">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-397">Info Field 4: Not used.</span></span>
</blockquote></td>

### <a name="directory-attributes-read"></a><span data-ttu-id="de49c-398">Lectura de atributos de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-398">Directory Attributes Read</span></span> 

#### <a name="fx_directory_attributes_read"></a><span data-ttu-id="de49c-399">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="de49c-399">fx_directory_attributes_read</span></span> 

<span data-ttu-id="de49c-400">**Icono** ![Icono de lectura de atributos de directorio](./media/user-guide/fx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-400">**Icon** ![Directory attributes read icon](./media/user-guide/fx-events/image15.png)</span></span>

<span data-ttu-id="de49c-401">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-401">**Description**</span></span> 

<span data-ttu-id="de49c-402">Este evento representa un evento de lectura de atributos de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-402">This event represents a directory attributes read event.</span></span>

<span data-ttu-id="de49c-403">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-403">**Information Fields**</span></span>

- <span data-ttu-id="de49c-404">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-404">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-405">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-405">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-406">Campo de información 3; asignación de bits de atributos:</span><span class="sxs-lookup"><span data-stu-id="de49c-406">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="de49c-407">Atributo</span><span class="sxs-lookup"><span data-stu-id="de49c-407">Attribute</span></span>                         | <span data-ttu-id="de49c-408">Value</span><span class="sxs-lookup"><span data-stu-id="de49c-408">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="de49c-409">Solo lectura</span><span class="sxs-lookup"><span data-stu-id="de49c-409">Read Only</span></span>                        | <span data-ttu-id="de49c-410">(0x01)</span><span class="sxs-lookup"><span data-stu-id="de49c-410">(0x01)</span></span>  |
  |  <span data-ttu-id="de49c-411">Hidden</span><span class="sxs-lookup"><span data-stu-id="de49c-411">Hidden</span></span>                           | <span data-ttu-id="de49c-412">(0x02)</span><span class="sxs-lookup"><span data-stu-id="de49c-412">(0x02)</span></span>  |
  |  <span data-ttu-id="de49c-413">Sistema</span><span class="sxs-lookup"><span data-stu-id="de49c-413">System</span></span>                           | <span data-ttu-id="de49c-414">(0x04)</span><span class="sxs-lookup"><span data-stu-id="de49c-414">(0x04)</span></span>  |
  |  <span data-ttu-id="de49c-415">Volumen</span><span class="sxs-lookup"><span data-stu-id="de49c-415">Volume</span></span>                           | <span data-ttu-id="de49c-416">(0x08)</span><span class="sxs-lookup"><span data-stu-id="de49c-416">(0x08)</span></span>  |
  |  <span data-ttu-id="de49c-417">Directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-417">Directory</span></span>                        | <span data-ttu-id="de49c-418">(0x10)</span><span class="sxs-lookup"><span data-stu-id="de49c-418">(0x10)</span></span>  |
  |  <span data-ttu-id="de49c-419">Archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-419">Archive</span></span>                          | <span data-ttu-id="de49c-420">(0x20)</span><span class="sxs-lookup"><span data-stu-id="de49c-420">(0x20)</span></span>  |
- <span data-ttu-id="de49c-421">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-421">Info Field 4: Not used.</span></span>

### <a name="directory-attributes-set"></a><span data-ttu-id="de49c-422">Definición de atributos de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-422">Directory Attributes Set</span></span> 

#### <a name="fx_directory_attributes_set"></a><span data-ttu-id="de49c-423">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="de49c-423">fx_directory_attributes_set</span></span> 

<span data-ttu-id="de49c-424">**Icono** ![Icono de definición de atributos](./media/user-guide/fx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-424">**Icon** ![Attributes set icon](./media/user-guide/fx-events/image16.png)</span></span>

<span data-ttu-id="de49c-425">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-425">**Description**</span></span> 

<span data-ttu-id="de49c-426">Este evento representa un evento de definición de atributos de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-426">This event represents a directory a directory attributes set event.</span></span>

<span data-ttu-id="de49c-427">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-427">**Information Fields**</span></span>

- <span data-ttu-id="de49c-428">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-428">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-429">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-429">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-430">Campo de información 3; asignación de bits de atributos:</span><span class="sxs-lookup"><span data-stu-id="de49c-430">Info Field 3: Attributes bit map:</span></span>

  |  <span data-ttu-id="de49c-431">Atributo</span><span class="sxs-lookup"><span data-stu-id="de49c-431">Attribute</span></span>                        | <span data-ttu-id="de49c-432">Value</span><span class="sxs-lookup"><span data-stu-id="de49c-432">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="de49c-433">Solo lectura</span><span class="sxs-lookup"><span data-stu-id="de49c-433">Read Only</span></span>                        | <span data-ttu-id="de49c-434">(0x01)</span><span class="sxs-lookup"><span data-stu-id="de49c-434">(0x01)</span></span>  |
  |  <span data-ttu-id="de49c-435">Hidden</span><span class="sxs-lookup"><span data-stu-id="de49c-435">Hidden</span></span>                           | <span data-ttu-id="de49c-436">(0x02)</span><span class="sxs-lookup"><span data-stu-id="de49c-436">(0x02)</span></span>  |
  |  <span data-ttu-id="de49c-437">Sistema</span><span class="sxs-lookup"><span data-stu-id="de49c-437">System</span></span>                           | <span data-ttu-id="de49c-438">(0x04)</span><span class="sxs-lookup"><span data-stu-id="de49c-438">(0x04)</span></span>  |
  |  <span data-ttu-id="de49c-439">Archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-439">Archive</span></span>                          | <span data-ttu-id="de49c-440">(0x20)</span><span class="sxs-lookup"><span data-stu-id="de49c-440">(0x20)</span></span>  |
- <span data-ttu-id="de49c-441">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-441">Info Field 4: Not used.</span></span>

### <a name="directory-create"></a><span data-ttu-id="de49c-442">Creación de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-442">Directory Create</span></span> 

#### <a name="fx_directory_create"></a><span data-ttu-id="de49c-443">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="de49c-443">fx_directory_create</span></span>

<span data-ttu-id="de49c-444">**Icono** ![Icono de creación de directorio](./media/user-guide/fx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-444">**Icon** ![Directory create icon](./media/user-guide/fx-events/image17.png)</span></span>

<span data-ttu-id="de49c-445">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-445">**Description**</span></span> 

<span data-ttu-id="de49c-446">Este evento representa un evento de creación de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-446">This event represents a directory create event.</span></span>

<span data-ttu-id="de49c-447">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-447">**Information Fields**</span></span>

- <span data-ttu-id="de49c-448">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-448">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-449">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-449">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-450">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-451">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-451">Info Field 4: Not used.</span></span>

### <a name="directory-default-get"></a><span data-ttu-id="de49c-452">Obtención predeterminada de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-452">Directory Default Get</span></span> 

#### <a name="fx_directory_default_get"></a><span data-ttu-id="de49c-453">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="de49c-453">fx_directory_default_get</span></span> 

<span data-ttu-id="de49c-454">**Icono** ![Icono de obtención predeterminada de directorio](./media/user-guide/fx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-454">**Icon** ![Directory default get icon](./media/user-guide/fx-events/image18.png)</span></span>

<span data-ttu-id="de49c-455">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-455">**Description**</span></span> 

<span data-ttu-id="de49c-456">Este evento representa un evento de definición predeterminada de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-456">This event represents a directory default set event.</span></span>

<span data-ttu-id="de49c-457">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-457">**Information Fields**</span></span>

- <span data-ttu-id="de49c-458">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-458">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-459">Campo de información 2: puntero a nombre de ruta de acceso de retorno.</span><span class="sxs-lookup"><span data-stu-id="de49c-459">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="de49c-460">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-461">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-461">Info Field 4: Not used.</span></span>

### <a name="directory-default-set"></a><span data-ttu-id="de49c-462">Definición predeterminada de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-462">Directory Default Set</span></span> 

#### <a name="fx_directory_default_set"></a><span data-ttu-id="de49c-463">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="de49c-463">fx_directory_default_set</span></span> 

<span data-ttu-id="de49c-464">**Icono** ![Icono de definición predeterminada de directorio](./media/user-guide/fx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-464">**Icon** ![Directory default set icon](./media/user-guide/fx-events/image19.png)</span></span>

<span data-ttu-id="de49c-465">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-465">**Description**</span></span> 

<span data-ttu-id="de49c-466">Este evento representa un evento de definición predeterminada de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-466">This event represents a directory default set event.</span></span>

<span data-ttu-id="de49c-467">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-467">**Information Fields**</span></span>

- <span data-ttu-id="de49c-468">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-468">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-469">Campo de información 2: puntero al nuevo nombre de ruta de acceso predeterminado.</span><span class="sxs-lookup"><span data-stu-id="de49c-469">Info Field 2: Pointer to new default path name.</span></span>
- <span data-ttu-id="de49c-470">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-471">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-471">Info Field 4: Not used.</span></span>

### <a name="directory-delete"></a><span data-ttu-id="de49c-472">Eliminación de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-472">Directory Delete</span></span> 

#### <a name="fx_directory_delete"></a><span data-ttu-id="de49c-473">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="de49c-473">fx_directory_delete</span></span>

<span data-ttu-id="de49c-474">**Icono** ![Icono de eliminación de directorio](./media/user-guide/fx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-474">**Icon** ![Directory delete icon](./media/user-guide/fx-events/image20.png)</span></span>

<span data-ttu-id="de49c-475">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-475">**Description**</span></span> 

<span data-ttu-id="de49c-476">Este evento representa un evento de eliminación de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-476">This event represents a directory delete event.</span></span>

<span data-ttu-id="de49c-477">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-477">**Information Fields**</span></span>
- <span data-ttu-id="de49c-478">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-478">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-479">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-479">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-480">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-481">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-481">Info Field 4: Not used.</span></span>

### <a name="directory-first-entry-find"></a><span data-ttu-id="de49c-482">Búsqueda de primera entrada de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-482">Directory First Entry Find</span></span> 

#### <a name="fx_directory_first_entry_find"></a><span data-ttu-id="de49c-483">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="de49c-483">fx_directory_first_entry_find</span></span>

<span data-ttu-id="de49c-484">**Icono** ![Icono de búsqueda de primera entrada de directorio](./media/user-guide/fx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-484">**Icon** ![Directory first entry find icon](./media/user-guide/fx-events/image21.png)</span></span>

<span data-ttu-id="de49c-485">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-485">**Description**</span></span> 

<span data-ttu-id="de49c-486">Este evento representa un evento de búsqueda de primera entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-486">This event represents a directory first entry find event.</span></span>

<span data-ttu-id="de49c-487">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-487">**Information Fields**</span></span>

- <span data-ttu-id="de49c-488">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-488">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-489">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-489">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-490">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-491">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-491">Info Field 4: Not used.</span></span>

### <a name="directory-first-full-entry-find"></a><span data-ttu-id="de49c-492">Búsqueda de primera entrada completa de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-492">Directory First Full Entry Find</span></span> 

#### <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="de49c-493">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="de49c-493">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="de49c-494">**Icono** ![Icono de búsqueda de primera entrada completa de directorio](./media/user-guide/fx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-494">**Icon** ![Directory first full entry find icon](./media/user-guide/fx-events/image22.png)</span></span>

<span data-ttu-id="de49c-495">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-495">**Description**</span></span> 

<span data-ttu-id="de49c-496">Este evento representa un evento de búsqueda de primera entrada completa de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-496">This event represents a directory first full entry find event.</span></span>

<span data-ttu-id="de49c-497">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-497">**Information Fields**</span></span>

- <span data-ttu-id="de49c-498">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-498">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-499">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-499">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-500">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-501">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-501">Info Field 4: Not used.</span></span>

### <a name="directory-information-get"></a><span data-ttu-id="de49c-502">Obtención de información de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-502">Directory Information Get</span></span> 

#### <a name="fx_directory_information_get"></a><span data-ttu-id="de49c-503">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="de49c-503">fx_directory_information_get</span></span>

<span data-ttu-id="de49c-504">**Icono** ![Icono de obtención de información de directorio](./media/user-guide/fx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-504">**Icon** ![Directory information get icon](./media/user-guide/fx-events/image23.png)</span></span>

<span data-ttu-id="de49c-505">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-505">**Description**</span></span> 

<span data-ttu-id="de49c-506">Este evento representa un evento de obtención de información de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-506">This event represents a directory information get event.</span></span>

<span data-ttu-id="de49c-507">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-507">**Information Fields**</span></span>

- <span data-ttu-id="de49c-508">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-508">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-509">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-509">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-510">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-510">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-511">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-511">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-clear"></a><span data-ttu-id="de49c-512">Borrado de ruta de acceso local de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-512">Directory Local Path Clear</span></span> 

#### <a name="fx_directory_local_path_clear"></a><span data-ttu-id="de49c-513">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="de49c-513">fx_directory_local_path_clear</span></span>

<span data-ttu-id="de49c-514">**Icono** ![Icono de borrado de ruta de acceso local de directorio](./media/user-guide/fx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-514">**Icon** ![Directory local path clear icon](./media/user-guide/fx-events/image24.png)</span></span>

<span data-ttu-id="de49c-515">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-515">**Description**</span></span> 

<span data-ttu-id="de49c-516">Este evento representa un evento de borrado de ruta de acceso local de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-516">This event represents a directory local path clear event.</span></span>

<span data-ttu-id="de49c-517">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-517">**Information Fields**</span></span>

- <span data-ttu-id="de49c-518">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-518">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-519">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-520">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-521">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-521">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-get"></a><span data-ttu-id="de49c-522">Obtención de ruta de acceso local de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-522">Directory Local Path Get</span></span> 

#### <a name="fx_directory_local_path_get"></a><span data-ttu-id="de49c-523">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="de49c-523">fx_directory_local_path_get</span></span>

<span data-ttu-id="de49c-524">**Icono** ![Icono de obtención de ruta de acceso local de directorio](./media/user-guide/fx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-524">**Icon** ![Directory local path get icon](./media/user-guide/fx-events/image25.png)</span></span>

<span data-ttu-id="de49c-525">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-525">**Description**</span></span> 

<span data-ttu-id="de49c-526">Este evento representa un evento de obtención de ruta de acceso local de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-526">This event represents a directory local path get event.</span></span>

<span data-ttu-id="de49c-527">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-527">**Information Fields**</span></span>

- <span data-ttu-id="de49c-528">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-528">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-529">Campo de información 2: puntero a nombre de ruta de acceso de retorno.</span><span class="sxs-lookup"><span data-stu-id="de49c-529">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="de49c-530">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-531">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-531">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-restore"></a><span data-ttu-id="de49c-532">Restauración de ruta de acceso local de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-532">Directory Local Path Restore</span></span> 

#### <a name="fx_directory_local_path_restore"></a><span data-ttu-id="de49c-533">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="de49c-533">fx_directory_local_path_restore</span></span>

<span data-ttu-id="de49c-534">**Icono** ![Icono de obtención de restauración de acceso local de directorio](./media/user-guide/fx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-534">**Icon** ![Directory local path restore icon](./media/user-guide/fx-events/image26.png)</span></span>

<span data-ttu-id="de49c-535">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-535">**Description**</span></span> 

<span data-ttu-id="de49c-536">Este evento representa un evento de restauración de ruta de acceso local de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-536">This event represents a directory local path restore event.</span></span>

<span data-ttu-id="de49c-537">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-537">**Information Fields**</span></span>

- <span data-ttu-id="de49c-538">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-538">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-539">Campo de información 2: puntero a la estructura de ruta de acceso local.</span><span class="sxs-lookup"><span data-stu-id="de49c-539">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="de49c-540">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-540">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-541">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-541">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-set"></a><span data-ttu-id="de49c-542">Definición de ruta de acceso local de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-542">Directory Local Path Set</span></span> 

#### <a name="fx_directory_local_path_set"></a><span data-ttu-id="de49c-543">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="de49c-543">fx_directory_local_path_set</span></span>

<span data-ttu-id="de49c-544">**Icono** ![Icono de definición de ruta de acceso local de directorio](./media/user-guide/fx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-544">**Icon** ![Directory local path set icon](./media/user-guide/fx-events/image27.png)</span></span>

<span data-ttu-id="de49c-545">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-545">**Description**</span></span> 

<span data-ttu-id="de49c-546">Este evento representa un evento de definición de ruta de acceso local de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-546">This event represents a directory local path set event.</span></span>

<span data-ttu-id="de49c-547">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-547">**Information Fields**</span></span>

- <span data-ttu-id="de49c-548">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-548">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-549">Campo de información 2: puntero a la estructura de ruta de acceso local.</span><span class="sxs-lookup"><span data-stu-id="de49c-549">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="de49c-550">Campo de información 3: puntero al nuevo nombre de ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="de49c-550">Info Field 3: Pointer to new path name.</span></span>
- <span data-ttu-id="de49c-551">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-551">Info Field 4: Not used.</span></span>

### <a name="directory-long-name-get"></a><span data-ttu-id="de49c-552">Obtención de nombre largo de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-552">Directory Long Name Get</span></span> 

#### <a name="fx_directory_long_name_get"></a><span data-ttu-id="de49c-553">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="de49c-553">fx_directory_long_name_get</span></span>

<span data-ttu-id="de49c-554">**Icono** ![Icono de obtención de nombre largo de directorio](./media/user-guide/fx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-554">**Icon** ![Directory long name get icon](./media/user-guide/fx-events/image28.png)</span></span>

<span data-ttu-id="de49c-555">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-555">**Description**</span></span> 

<span data-ttu-id="de49c-556">Este evento representa un evento de obtención de nombre largo de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-556">This event represents a directory long name get event.</span></span>

<span data-ttu-id="de49c-557">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-557">**Information Fields**</span></span>

- <span data-ttu-id="de49c-558">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-558">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-559">Campo de información 2: puntero al nombre corto de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-559">Info Field 2: Pointer to short file name.</span></span>
- <span data-ttu-id="de49c-560">Campo de información 3: puntero al nombre largo de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-560">Info Field 3: Pointer to long file name.</span></span>
- <span data-ttu-id="de49c-561">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-561">Info Field 4: Not used.</span></span>

### <a name="directory-name-test"></a><span data-ttu-id="de49c-562">Prueba de nombre de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-562">Directory Name Test</span></span> 

#### <a name="fx_directory_name_test"></a><span data-ttu-id="de49c-563">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="de49c-563">fx_directory_name_test</span></span>

<span data-ttu-id="de49c-564">**Icono** ![Icono de prueba de nombre de directorio](./media/user-guide/fx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-564">**Icon** ![Directory name test icon](./media/user-guide/fx-events/image29.png)</span></span>

<span data-ttu-id="de49c-565">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-565">**Description**</span></span> 

<span data-ttu-id="de49c-566">Este evento representa un evento de prueba de nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-566">This event represents a directory name test event.</span></span>

<span data-ttu-id="de49c-567">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-567">**Information Fields**</span></span>

- <span data-ttu-id="de49c-568">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-568">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-569">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-569">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-570">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-570">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-571">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-571">Info Field 4: Not used.</span></span>

### <a name="directory-next-entry-find"></a><span data-ttu-id="de49c-572">Búsqueda de siguiente entrada de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-572">Directory Next Entry Find</span></span> 

#### <a name="fx_directory_next_entry_find"></a><span data-ttu-id="de49c-573">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="de49c-573">fx_directory_next_entry_find</span></span>

<span data-ttu-id="de49c-574">**Icono** ![Icono de búsqueda de siguiente entrada de directorio](./media/user-guide/fx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-574">**Icon** ![Directory next entry find icon](./media/user-guide/fx-events/image30.png)</span></span>

<span data-ttu-id="de49c-575">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-575">**Description**</span></span> 

<span data-ttu-id="de49c-576">Este evento representa un evento de búsqueda de siguiente entrada de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-576">This event represents a directory next entry find event.</span></span>

<span data-ttu-id="de49c-577">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-577">**Information Fields**</span></span>

- <span data-ttu-id="de49c-578">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-578">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-579">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-579">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-580">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-580">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-581">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-581">Info Field 4: Not used.</span></span>

### <a name="directory-next-full-entry-find"></a><span data-ttu-id="de49c-582">Búsqueda de siguiente entrada completa de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-582">Directory Next Full Entry Find</span></span> 

#### <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="de49c-583">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="de49c-583">fx_directory_next_full_entry_find</span></span>

<span data-ttu-id="de49c-584">**Icono** ![Icono de búsqueda de siguiente entrada completa de directorio](./media/user-guide/fx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-584">**Icon** ![Directory next full entry find icon](./media/user-guide/fx-events/image31.png)</span></span>

<span data-ttu-id="de49c-585">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-585">**Description**</span></span>

<span data-ttu-id="de49c-586">Este evento representa un evento de búsqueda de siguiente entrada completa de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-586">This event represents a directory next full entry find event.</span></span>

<span data-ttu-id="de49c-587">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-587">**Information Fields**</span></span>

- <span data-ttu-id="de49c-588">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-588">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-589">Campo de información 2: puntero al nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-589">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="de49c-590">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-590">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-591">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-591">Info Field 4: Not used.</span></span>

### <a name="directory-rename"></a><span data-ttu-id="de49c-592">Cambio de nombre de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-592">Directory Rename</span></span> 

#### <a name="fx_directory_rename-event"></a><span data-ttu-id="de49c-593">fx_directory_rename_event</span><span class="sxs-lookup"><span data-stu-id="de49c-593">fx_directory_rename event</span></span>

<span data-ttu-id="de49c-594">**Icono** ![Icono de cambio de nombre de directorio](./media/user-guide/fx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-594">**Icon** ![Directory rename icon](./media/user-guide/fx-events/image32.png)</span></span>

<span data-ttu-id="de49c-595">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-595">**Description**</span></span>

<span data-ttu-id="de49c-596">Este evento representa un evento de cambio de nombre de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-596">This event represents a directory rename event.</span></span>

<span data-ttu-id="de49c-597">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-597">**Information Fields**</span></span>

- <span data-ttu-id="de49c-598">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-598">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-599">Campo de información 2: puntero al nombre antiguo de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-599">Info Field 2: Pointer to old directory name.</span></span>
- <span data-ttu-id="de49c-600">Campo de información 3: puntero al nombre nuevo de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-600">Info Field 3: Pointer to new directory name.</span></span>
- <span data-ttu-id="de49c-601">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-601">Info Field 4: Not used.</span></span>

### <a name="directory-short-name-get"></a><span data-ttu-id="de49c-602">Obtención de nombre corto de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-602">Directory Short Name Get</span></span> 

#### <a name="fx_directory_short_name_get"></a><span data-ttu-id="de49c-603">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="de49c-603">fx_directory_short_name_get</span></span>

<span data-ttu-id="de49c-604">**Icono** ![Icono de obtención de nombre corto de directorio](./media/user-guide/fx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-604">**Icon** ![Directory short name get icon](./media/user-guide/fx-events/image33.png)</span></span>

<span data-ttu-id="de49c-605">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-605">**Description**</span></span>

<span data-ttu-id="de49c-606">Este evento representa un evento de obtención de nombre corto de directorio.</span><span class="sxs-lookup"><span data-stu-id="de49c-606">This event represents a directory short name get event.</span></span>

<span data-ttu-id="de49c-607">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-607">**Information Fields**</span></span> 

- <span data-ttu-id="de49c-608">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-608">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-609">Campo de información 2: puntero al nombre largo de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-609">Info Field 2: Pointer to long file name.</span></span>
- <span data-ttu-id="de49c-610">Campo de información 3: puntero al nombre corto de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-610">Info Field 3: Pointer to short file name.</span></span>
- <span data-ttu-id="de49c-611">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-611">Info Field 4: Not used.</span></span>

### <a name="file-allocate"></a><span data-ttu-id="de49c-612">Asignación de archivos</span><span class="sxs-lookup"><span data-stu-id="de49c-612">File Allocate</span></span> 

#### <a name="fx_file_allocate"></a><span data-ttu-id="de49c-613">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="de49c-613">fx_file_allocate</span></span>

<span data-ttu-id="de49c-614">**Icono** ![Icono de asignación de archivos](./media/user-guide/fx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-614">**Icon** ![File allocate icon](./media/user-guide/fx-events/image34.png)</span></span>

<span data-ttu-id="de49c-615">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-615">**Description**</span></span>

<span data-ttu-id="de49c-616">Este evento representa un evento de asignación de archivos.</span><span class="sxs-lookup"><span data-stu-id="de49c-616">This event represents a file allocate event.</span></span>

<span data-ttu-id="de49c-617">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-617">**Information Fields**</span></span>

- <span data-ttu-id="de49c-618">Campo de información 1: puntero al archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-618">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="de49c-619">Campo de información 2: tamaño solicitado.</span><span class="sxs-lookup"><span data-stu-id="de49c-619">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="de49c-620">Campo de información 3: tamaño actual.</span><span class="sxs-lookup"><span data-stu-id="de49c-620">Info Field 3: Current size.</span></span>
- <span data-ttu-id="de49c-621">Campo de información 4: nuevo tamaño.</span><span class="sxs-lookup"><span data-stu-id="de49c-621">Info Field 4: New size.</span></span>

### <a name="file-attributes-read"></a><span data-ttu-id="de49c-622">Lectura de atributos de archivos</span><span class="sxs-lookup"><span data-stu-id="de49c-622">File Attributes Read</span></span> 

#### <a name="fx_file_attributes_read"></a><span data-ttu-id="de49c-623">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="de49c-623">fx_file_attributes_read</span></span>

<span data-ttu-id="de49c-624">**Icono** ![Icono de lectura de atributos de archivo](./media/user-guide/fx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-624">**Icon** ![File attributes read icon](./media/user-guide/fx-events/image35.png)</span></span>

<span data-ttu-id="de49c-625">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-625">**Description**</span></span>

<span data-ttu-id="de49c-626">Este evento representa un evento de lectura de atributos de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-626">This event represents a file attributes read event.</span></span>

<span data-ttu-id="de49c-627">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-627">**Information Fields**</span></span>

- <span data-ttu-id="de49c-628">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-628">Info Field 1: Pointer to the media.</span></span> 
- <span data-ttu-id="de49c-629">Campo de información 2: asignación de bits de atributos:</span><span class="sxs-lookup"><span data-stu-id="de49c-629">Info Field 2: Attributes bit map:</span></span>

  |  <span data-ttu-id="de49c-630">Atributo</span><span class="sxs-lookup"><span data-stu-id="de49c-630">Attribut</span></span>                         | <span data-ttu-id="de49c-631">Value</span><span class="sxs-lookup"><span data-stu-id="de49c-631">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="de49c-632">Solo lectura</span><span class="sxs-lookup"><span data-stu-id="de49c-632">Read Only</span></span>                        | <span data-ttu-id="de49c-633">(0x01)</span><span class="sxs-lookup"><span data-stu-id="de49c-633">(0x01)</span></span>  |
  |  <span data-ttu-id="de49c-634">Hidden</span><span class="sxs-lookup"><span data-stu-id="de49c-634">Hidden</span></span>                           | <span data-ttu-id="de49c-635">(0x02)</span><span class="sxs-lookup"><span data-stu-id="de49c-635">(0x02)</span></span>  |
  |  <span data-ttu-id="de49c-636">Sistema</span><span class="sxs-lookup"><span data-stu-id="de49c-636">System</span></span>                           | <span data-ttu-id="de49c-637">(0x04)</span><span class="sxs-lookup"><span data-stu-id="de49c-637">(0x04)</span></span>  |
  |  <span data-ttu-id="de49c-638">Volumen</span><span class="sxs-lookup"><span data-stu-id="de49c-638">Volume</span></span>                           | <span data-ttu-id="de49c-639">(0x08)</span><span class="sxs-lookup"><span data-stu-id="de49c-639">(0x08)</span></span>  |
  |  <span data-ttu-id="de49c-640">Directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-640">Directory</span></span>                        | <span data-ttu-id="de49c-641">(0x10)</span><span class="sxs-lookup"><span data-stu-id="de49c-641">(0x10)</span></span>  |
  |  <span data-ttu-id="de49c-642">Archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-642">Archive</span></span>                          | <span data-ttu-id="de49c-643">(0x20)</span><span class="sxs-lookup"><span data-stu-id="de49c-643">(0x20)</span></span>  |
- <span data-ttu-id="de49c-644">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-644">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-645">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-645">Info Field 4: Not used.</span></span>

### <a name="file-attributes-set"></a><span data-ttu-id="de49c-646">Definición de atributos de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-646">File Attributes Set</span></span> 

#### <a name="fx_file_attributes_set"></a><span data-ttu-id="de49c-647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="de49c-647">fx_file_attributes_set</span></span>

<span data-ttu-id="de49c-648">**Icono** ![Icono de definición de atributos de archivo](./media/user-guide/fx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-648">**Icon** ![File attributes set icon](./media/user-guide/fx-events/image36.png)</span></span>

<span data-ttu-id="de49c-649">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-649">**Description**</span></span> 

<span data-ttu-id="de49c-650">Este evento representa un evento de definición de atributos de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-650">This event represents a file attributes set event.</span></span>

<span data-ttu-id="de49c-651">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-651">**Information Fields**</span></span>

- <span data-ttu-id="de49c-652">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-652">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-653">Campo de información 2: puntero al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-653">Info Field 2: Pointer to file name.</span></span> 
- <span data-ttu-id="de49c-654">Campo de información 3; asignación de bits de atributos:</span><span class="sxs-lookup"><span data-stu-id="de49c-654">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="de49c-655">Atributo</span><span class="sxs-lookup"><span data-stu-id="de49c-655">Attribute</span></span>                         | <span data-ttu-id="de49c-656">Value</span><span class="sxs-lookup"><span data-stu-id="de49c-656">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="de49c-657">Solo lectura</span><span class="sxs-lookup"><span data-stu-id="de49c-657">Read Only</span></span>                        | <span data-ttu-id="de49c-658">(0x01)</span><span class="sxs-lookup"><span data-stu-id="de49c-658">(0x01)</span></span>  |
  |  <span data-ttu-id="de49c-659">Hidden</span><span class="sxs-lookup"><span data-stu-id="de49c-659">Hidden</span></span>                           | <span data-ttu-id="de49c-660">(0x02)</span><span class="sxs-lookup"><span data-stu-id="de49c-660">(0x02)</span></span>  |
  |  <span data-ttu-id="de49c-661">Sistema</span><span class="sxs-lookup"><span data-stu-id="de49c-661">System</span></span>                           | <span data-ttu-id="de49c-662">(0x04)</span><span class="sxs-lookup"><span data-stu-id="de49c-662">(0x04)</span></span>  |
  |  <span data-ttu-id="de49c-663">Archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-663">Archive</span></span>                          | <span data-ttu-id="de49c-664">(0x20)</span><span class="sxs-lookup"><span data-stu-id="de49c-664">(0x20)</span></span>  |
- <span data-ttu-id="de49c-665">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-665">Info Field 4: Not used.</span></span>

### <a name="file-best-effort-allocate"></a><span data-ttu-id="de49c-666">Asignación de mejor esfuerzo de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-666">File Best Effort Allocate</span></span> 

#### <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="de49c-667">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="de49c-667">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="de49c-668">**Icono** ![Icono de asignación de mejor esfuerzo de archivo](./media/user-guide/fx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-668">**Icon** ![File best effort allocate icon](./media/user-guide/fx-events/image37.png)</span></span>

<span data-ttu-id="de49c-669">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-669">**Description**</span></span> 

<span data-ttu-id="de49c-670">Este evento representa un evento de asignación de mejor esfuerzo de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-670">This event represents a file best effort allocate event.</span></span>

<span data-ttu-id="de49c-671">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-671">**Information Fields**</span></span>

- <span data-ttu-id="de49c-672">Campo de información 1: puntero al archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-672">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="de49c-673">Campo de información 2: tamaño solicitado.</span><span class="sxs-lookup"><span data-stu-id="de49c-673">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="de49c-674">Campo de información 3: tamaño real asignado.</span><span class="sxs-lookup"><span data-stu-id="de49c-674">Info Field 3: Actual size allocated.</span></span>
- <span data-ttu-id="de49c-675">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-675">Info Field 4: Not used.</span></span>

### <a name="file-close"></a><span data-ttu-id="de49c-676">Cierre de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-676">File Close</span></span> 

#### <a name="fx_file_close"></a><span data-ttu-id="de49c-677">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="de49c-677">fx_file_close</span></span>

<span data-ttu-id="de49c-678">**Icono** ![Icono de cierre de archivo](./media/user-guide/fx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-678">**Icon** ![File close icon](./media/user-guide/fx-events/image38.png)</span></span>

<span data-ttu-id="de49c-679">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-679">**Description**</span></span> 

<span data-ttu-id="de49c-680">Este evento representa un evento de cierre de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-680">This event represents a file close event.</span></span>

<span data-ttu-id="de49c-681">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-681">**Information Fields**</span></span>

- <span data-ttu-id="de49c-682">Campo de información 1: puntero al archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-682">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="de49c-683">Campo de información 2: tamaño del archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-683">Info Field 2: File size.</span></span>
- <span data-ttu-id="de49c-684">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-684">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-685">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-685">Info Field 4: Not used.</span></span>

### <a name="file-create"></a><span data-ttu-id="de49c-686">Creación de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-686">File Create</span></span>

#### <a name="fx_file_create"></a><span data-ttu-id="de49c-687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="de49c-687">fx_file_create</span></span>

<span data-ttu-id="de49c-688">**Icono** ![Icono de creación de archivo](./media/user-guide/fx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-688">**Icon** ![File create icon](./media/user-guide/fx-events/image39.png)</span></span>

<span data-ttu-id="de49c-689">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-689">**Description**</span></span>

<span data-ttu-id="de49c-690">Este evento representa un evento de creación de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-690">This event represents a file create event.</span></span>

<span data-ttu-id="de49c-691">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-691">**Information Fields**</span></span>

- <span data-ttu-id="de49c-692">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-692">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-693">Campo de información 2: puntero al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-693">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="de49c-694">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-694">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-695">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-695">Info Field 4: Not used.</span></span>

### <a name="file-date-time-set"></a><span data-ttu-id="de49c-696">Definición de fecha y hora de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-696">File Date Time Set</span></span> 

#### <a name="fx_file_date_time_set"></a><span data-ttu-id="de49c-697">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="de49c-697">fx_file_date_time_set</span></span>

<span data-ttu-id="de49c-698">**Icono** ![Icono de definición de fecha y hora de archivo](./media/user-guide/fx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-698">**Icon** ![File date time set icon](./media/user-guide/fx-events/image40.png)</span></span>

<span data-ttu-id="de49c-699">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-699">**Description**</span></span>

<span data-ttu-id="de49c-700">Este evento representa un evento de definición de fecha y hora de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-700">This event represents a file date/time set event.</span></span>

<span data-ttu-id="de49c-701">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-701">**Information Fields**</span></span>

- <span data-ttu-id="de49c-702">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-702">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-703">Campo de información 2: puntero al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-703">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="de49c-704">Campo de información 3: año.</span><span class="sxs-lookup"><span data-stu-id="de49c-704">Info Field 3: Year.</span></span>
- <span data-ttu-id="de49c-705">Campo de información 4: mes.</span><span class="sxs-lookup"><span data-stu-id="de49c-705">Info Field 4: Month.</span></span>

### <a name="file-delete"></a><span data-ttu-id="de49c-706">Eliminación de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-706">File Delete</span></span> 

#### <a name="fx_file_delete"></a><span data-ttu-id="de49c-707">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="de49c-707">fx_file_delete</span></span>

<span data-ttu-id="de49c-708">**Icono** ![Icono de eliminación de archivo](./media/user-guide/fx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-708">**Icon** ![File delete icon](./media/user-guide/fx-events/image41.png)</span></span>

<span data-ttu-id="de49c-709">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-709">**Description**</span></span>

<span data-ttu-id="de49c-710">Este evento representa un evento de eliminación de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-710">This event represents a file delete event.</span></span>

<span data-ttu-id="de49c-711">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-711">**Information Fields**</span></span>

- <span data-ttu-id="de49c-712">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-712">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-713">Campo de información 2: puntero al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-713">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="de49c-714">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-714">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-715">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-715">Info Field 4: Not used.</span></span>

### <a name="file-open"></a><span data-ttu-id="de49c-716">Apertura de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-716">File Open</span></span> 

#### <a name="fx_file_open"></a><span data-ttu-id="de49c-717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="de49c-717">fx_file_open</span></span>

<span data-ttu-id="de49c-718">**Icono** ![Icono de apertura de archivo](./media/user-guide/fx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-718">**Icon** ![File open icon](./media/user-guide/fx-events/image42.png)</span></span>

<span data-ttu-id="de49c-719">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-719">**Description**</span></span>

<span data-ttu-id="de49c-720">Este evento representa un evento de apertura de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-720">This event represents a file open event.</span></span>

<span data-ttu-id="de49c-721">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-721">**Information Fields**</span></span> 

- <span data-ttu-id="de49c-722">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-722">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-723">Campo de información 2: puntero al bloque de control de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-723">Info Field 2: Pointer to the file control block.</span></span>
- <span data-ttu-id="de49c-724">Campo de información 3: puntero al nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-724">Info Field 3: Pointer to file name.</span></span>
- <span data-ttu-id="de49c-725">Campo de información 4; tipo abierto:</span><span class="sxs-lookup"><span data-stu-id="de49c-725">Info Field 4: Open type:</span></span>

  |  <span data-ttu-id="de49c-726">Tipo de apertura</span><span class="sxs-lookup"><span data-stu-id="de49c-726">Open Type</span></span>                        | <span data-ttu-id="de49c-727">Value</span><span class="sxs-lookup"><span data-stu-id="de49c-727">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="de49c-728">Apertura para lectura</span><span class="sxs-lookup"><span data-stu-id="de49c-728">Open for Read</span></span>                    | <span data-ttu-id="de49c-729">(0x00)</span><span class="sxs-lookup"><span data-stu-id="de49c-729">(0x00)</span></span>  |
  |  <span data-ttu-id="de49c-730">Apertura para escritura</span><span class="sxs-lookup"><span data-stu-id="de49c-730">Open for Write</span></span>                   | <span data-ttu-id="de49c-731">(0x01)</span><span class="sxs-lookup"><span data-stu-id="de49c-731">(0x01)</span></span>  |
  |  <span data-ttu-id="de49c-732">Apertura rápida para lectura</span><span class="sxs-lookup"><span data-stu-id="de49c-732">Fast Open for Read</span></span>               | <span data-ttu-id="de49c-733">(0x02)</span><span class="sxs-lookup"><span data-stu-id="de49c-733">(0x02)</span></span>  |

### <a name="file-read"></a><span data-ttu-id="de49c-734">Lectura de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-734">File Read</span></span> 

#### <a name="fx_file_read"></a><span data-ttu-id="de49c-735">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="de49c-735">fx_file_read</span></span>

<span data-ttu-id="de49c-736">**Icono** ![Icono de lectura de archivo](./media/user-guide/fx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-736">**Icon** ![File read icon](./media/user-guide/fx-events/image43.png)</span></span>

<span data-ttu-id="de49c-737">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-737">**Description**</span></span>

<span data-ttu-id="de49c-738">Este evento representa un evento de lectura de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-738">This event represents a file read event.</span></span>

<span data-ttu-id="de49c-739">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-739">**Information Fields**</span></span>

- <span data-ttu-id="de49c-740">Campo de información 1: puntero al archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-740">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="de49c-741">Campo de información 2: puntero de búfer.</span><span class="sxs-lookup"><span data-stu-id="de49c-741">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="de49c-742">Campo de información 3: tamaño de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="de49c-742">Info Field 3: Request size.</span></span>
- <span data-ttu-id="de49c-743">Campo de información 4: tamaño real leído.</span><span class="sxs-lookup"><span data-stu-id="de49c-743">Info Field 4: Actual size read.</span></span>

### <a name="file-relative-seek"></a><span data-ttu-id="de49c-744">Búsqueda relativa de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-744">File Relative Seek</span></span> 

#### <a name="fx_file_relative_seek"></a><span data-ttu-id="de49c-745">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="de49c-745">fx_file_relative_seek</span></span>

<span data-ttu-id="de49c-746">**Icono** ![Icono de búsqueda relativa de archivo](./media/user-guide/fx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-746">**Icon** ![File relative seek icon](./media/user-guide/fx-events/image44.png)</span></span>

<span data-ttu-id="de49c-747">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-747">**Description**</span></span>

<span data-ttu-id="de49c-748">Este evento representa un evento de búsqueda relativa de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-748">This event represents a file relative seek event.</span></span>

<span data-ttu-id="de49c-749">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-749">**Information Fields**</span></span>

- <span data-ttu-id="de49c-750">Campo de información 1: puntero al archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-750">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="de49c-751">Campo de información 2: desplazamiento de bytes.</span><span class="sxs-lookup"><span data-stu-id="de49c-751">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="de49c-752">Campo de información 3: buscar desde:</span><span class="sxs-lookup"><span data-stu-id="de49c-752">Info Field 3: Seek from:</span></span>

  | <span data-ttu-id="de49c-753">Evento</span><span class="sxs-lookup"><span data-stu-id="de49c-753">Event</span></span>                             | <span data-ttu-id="de49c-754">Value</span><span class="sxs-lookup"><span data-stu-id="de49c-754">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="de49c-755">Desde el principio</span><span class="sxs-lookup"><span data-stu-id="de49c-755">From Beginning</span></span>                   | <span data-ttu-id="de49c-756">(0x00)</span><span class="sxs-lookup"><span data-stu-id="de49c-756">(0x00)</span></span>  |
  |  <span data-ttu-id="de49c-757">Desde el final</span><span class="sxs-lookup"><span data-stu-id="de49c-757">From End</span></span>                         | <span data-ttu-id="de49c-758">(0x01)</span><span class="sxs-lookup"><span data-stu-id="de49c-758">(0x01)</span></span>  | 
  |  <span data-ttu-id="de49c-759">Adelante</span><span class="sxs-lookup"><span data-stu-id="de49c-759">Forward</span></span>                          | <span data-ttu-id="de49c-760">(0x02)</span><span class="sxs-lookup"><span data-stu-id="de49c-760">(0x02)</span></span>  |
  |  <span data-ttu-id="de49c-761">atrás</span><span class="sxs-lookup"><span data-stu-id="de49c-761">Backward</span></span>                         | <span data-ttu-id="de49c-762">(0x03)</span><span class="sxs-lookup"><span data-stu-id="de49c-762">(0x03)</span></span>  |
- <span data-ttu-id="de49c-763">Campo de información 4: desplazamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="de49c-763">Info Field 4: Previous offset.</span></span>

### <a name="file-rename"></a><span data-ttu-id="de49c-764">Cambio de nombre de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-764">File Rename</span></span> 

#### <a name="fx_file_rename"></a><span data-ttu-id="de49c-765">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="de49c-765">fx_file_rename</span></span>

<span data-ttu-id="de49c-766">**Icono** ![Icono de cambio de nombre de archivo](./media/user-guide/fx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-766">**Icon** ![File rename icon](./media/user-guide/fx-events/image45.png)</span></span>

<span data-ttu-id="de49c-767">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-767">**Description**</span></span>

<span data-ttu-id="de49c-768">Este evento representa un evento de cambio de nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-768">This event represents a file rename event.</span></span>

<span data-ttu-id="de49c-769">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-769">**Information Fields**</span></span>

- <span data-ttu-id="de49c-770">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-770">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-771">Campo de información 2: puntero al nombre de archivo antiguo.</span><span class="sxs-lookup"><span data-stu-id="de49c-771">Info Field 2: Pointer to old file name.</span></span>
- <span data-ttu-id="de49c-772">Campo de información 3: puntero al nombre de archivo nuevo.</span><span class="sxs-lookup"><span data-stu-id="de49c-772">Info Field 3: Pointer to new file name.</span></span>
- <span data-ttu-id="de49c-773">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-773">Info Field 4: Not used.</span></span>

### <a name="file-seek"></a><span data-ttu-id="de49c-774">Búsqueda de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-774">File Seek</span></span> 

#### <a name="fx_file_seek"></a><span data-ttu-id="de49c-775">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="de49c-775">fx_file_seek</span></span>

<span data-ttu-id="de49c-776">**Icono** ![Icono de búsqueda de archivo](./media/user-guide/fx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-776">**Icon** ![File seek icon](./media/user-guide/fx-events/image46.png)</span></span>

<span data-ttu-id="de49c-777">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-777">**Description**</span></span>

<span data-ttu-id="de49c-778">Este evento representa un evento de búsqueda de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-778">This event represents a file seek event.</span></span>

<span data-ttu-id="de49c-779">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-779">**Information Fields**</span></span> 

- <span data-ttu-id="de49c-780">Campo de información 1: puntero al archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-780">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="de49c-781">Campo de información 2: desplazamiento de bytes.</span><span class="sxs-lookup"><span data-stu-id="de49c-781">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="de49c-782">Campo de información 3: desplazamiento anterior.</span><span class="sxs-lookup"><span data-stu-id="de49c-782">Info Field 3: Previous offset.</span></span>
- <span data-ttu-id="de49c-783">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-783">Info Field 4: Not used.</span></span>

### <a name="file-truncate"></a><span data-ttu-id="de49c-784">Truncamiento de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-784">File Truncate</span></span> 

#### <a name="fx_file_truncate"></a><span data-ttu-id="de49c-785">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="de49c-785">fx_file_truncate</span></span>

<span data-ttu-id="de49c-786">**Icono** ![Icono de truncamiento de archivo](./media/user-guide/fx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-786">**Icon** ![File truncate icon](./media/user-guide/fx-events/image47.png)</span></span>

<span data-ttu-id="de49c-787">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-787">**Description**</span></span>

<span data-ttu-id="de49c-788">Este evento representa un evento de truncamiento de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-788">This event represents a file truncate event.</span></span>

<span data-ttu-id="de49c-789">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-789">**Information Fields**</span></span>

- <span data-ttu-id="de49c-790">Campo de información 1: puntero al archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-790">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="de49c-791">Campo de información 2: tamaño solicitado.</span><span class="sxs-lookup"><span data-stu-id="de49c-791">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="de49c-792">Campo de información 3: tamaño anterior.</span><span class="sxs-lookup"><span data-stu-id="de49c-792">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="de49c-793">Campo de información 4: nuevo tamaño.</span><span class="sxs-lookup"><span data-stu-id="de49c-793">Info Field 4: New size.</span></span>

### <a name="file-truncate-release"></a><span data-ttu-id="de49c-794">Versión de truncamiento de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-794">File Truncate Release</span></span> 

#### <a name="fx_file_truncate_release"></a><span data-ttu-id="de49c-795">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="de49c-795">fx_file_truncate_release</span></span> 

<span data-ttu-id="de49c-796">**Icono** ![Icono de versión de truncamiento de archivo](./media/user-guide/fx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-796">**Icon** ![File truncate release icon](./media/user-guide/fx-events/image48.png)</span></span>

<span data-ttu-id="de49c-797">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-797">**Description**</span></span>

<span data-ttu-id="de49c-798">Este evento representa un evento de versión de truncamiento de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-798">This event represents a file truncate release event.</span></span>

<span data-ttu-id="de49c-799">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-799">**Information Fields**</span></span>

- <span data-ttu-id="de49c-800">Campo de información 1: puntero al archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-800">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="de49c-801">Campo de información 2: tamaño solicitado.</span><span class="sxs-lookup"><span data-stu-id="de49c-801">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="de49c-802">Campo de información 3: tamaño anterior.</span><span class="sxs-lookup"><span data-stu-id="de49c-802">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="de49c-803">Campo de información 4: nuevo tamaño.</span><span class="sxs-lookup"><span data-stu-id="de49c-803">Info Field 4: New size.</span></span>

### <a name="file-write"></a><span data-ttu-id="de49c-804">Escritura de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-804">File Write</span></span> 

#### <a name="fx_file_write"></a><span data-ttu-id="de49c-805">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="de49c-805">fx_file_write</span></span> 

<span data-ttu-id="de49c-806">**Icono** ![Icono de escritura de archivo](./media/user-guide/fx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-806">**Icon** ![File write icon](./media/user-guide/fx-events/image49.png)</span></span>

<span data-ttu-id="de49c-807">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-807">**Description**</span></span>

<span data-ttu-id="de49c-808">Este evento representa un evento de escritura de archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-808">This event represents a file write event.</span></span>

<span data-ttu-id="de49c-809">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-809">**Information Fields**</span></span>

- <span data-ttu-id="de49c-810">Campo de información 1: puntero al archivo.</span><span class="sxs-lookup"><span data-stu-id="de49c-810">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="de49c-811">Campo de información 2: puntero de búfer.</span><span class="sxs-lookup"><span data-stu-id="de49c-811">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="de49c-812">Campo de información 3: tamaño de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="de49c-812">Info Field 3: Request size.</span></span>
- <span data-ttu-id="de49c-813">Campo de información 4: tamaño real escrito.</span><span class="sxs-lookup"><span data-stu-id="de49c-813">Info Field 4: Actual size written.</span></span>

### <a name="media-abort"></a><span data-ttu-id="de49c-814">Anulación de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-814">Media Abort</span></span> 

#### <a name="fx_media_abort"></a><span data-ttu-id="de49c-815">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="de49c-815">fx_media_abort</span></span> 

<span data-ttu-id="de49c-816">**Icono** ![Icono de anulación de elementos multimedia](./media/user-guide/fx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-816">**Icon** ![Media abort icon](./media/user-guide/fx-events/image50.png)</span></span>

<span data-ttu-id="de49c-817">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-817">**Description**</span></span>

<span data-ttu-id="de49c-818">Este evento representa un evento de anulación de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-818">This event represents a media abort event.</span></span>

<span data-ttu-id="de49c-819">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-819">**Information Fields**</span></span>

- <span data-ttu-id="de49c-820">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-820">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-821">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-821">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-822">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-822">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-823">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-823">Info Field 4: Not used.</span></span>

### <a name="media-cache-invalidate"></a><span data-ttu-id="de49c-824">Invalidación de caché de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-824">Media Cache Invalidate</span></span>

#### <a name="fx_media_cache_invalidate"></a><span data-ttu-id="de49c-825">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="de49c-825">fx_media_cache_invalidate</span></span>

<span data-ttu-id="de49c-826">**Icono** ![Icono de invalidación de caché de elementos multimedia](./media/user-guide/fx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-826">**Icon** ![Media cache invalidate icon](./media/user-guide/fx-events/image51.png)</span></span>

<span data-ttu-id="de49c-827">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-827">**Description**</span></span>

<span data-ttu-id="de49c-828">Este evento representa un evento de invalidación de caché de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-828">This event represents a media cache invalidate event.</span></span>

<span data-ttu-id="de49c-829">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-829">**Information Fields**</span></span>

- <span data-ttu-id="de49c-830">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-830">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-831">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-831">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-832">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-832">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-833">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-833">Info Field 4: Not used.</span></span>

### <a name="media-check"></a><span data-ttu-id="de49c-834">Comprobación de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-834">Media Check</span></span> 

#### <a name="fx_media_check"></a><span data-ttu-id="de49c-835">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="de49c-835">fx_media_check</span></span>

<span data-ttu-id="de49c-836">**Icono** ![Icono de comprobación de elementos multimedia](./media/user-guide/fx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-836">**Icon** ![Media check icon](./media/user-guide/fx-events/image52.png)</span></span>

<span data-ttu-id="de49c-837">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-837">**Description**</span></span>

<span data-ttu-id="de49c-838">Este evento representa un evento de comprobación de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-838">This event represents a media check event.</span></span>

<span data-ttu-id="de49c-839">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-839">**Information Fields**</span></span> 

- <span data-ttu-id="de49c-840">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-840">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-841">Campo de información 2: puntero de memoria de tachado.</span><span class="sxs-lookup"><span data-stu-id="de49c-841">Info Field 2: Scratch memory pointer.</span></span>
- <span data-ttu-id="de49c-842">Campo de información 3: puntero de memoria de tachado.</span><span class="sxs-lookup"><span data-stu-id="de49c-842">Info Field 3: Scratch memory size.</span></span>
- <span data-ttu-id="de49c-843">Campo de información 4: asignación de bits de errores:</span><span class="sxs-lookup"><span data-stu-id="de49c-843">Info Field 4: Errors bit map:</span></span>

  | <span data-ttu-id="de49c-844">Tipo de error</span><span class="sxs-lookup"><span data-stu-id="de49c-844">Error type</span></span>                        | <span data-ttu-id="de49c-845">Value</span><span class="sxs-lookup"><span data-stu-id="de49c-845">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="de49c-846">Error de cadena FAT</span><span class="sxs-lookup"><span data-stu-id="de49c-846">FAT Chain Error</span></span>                  | <span data-ttu-id="de49c-847">(0x01)</span><span class="sxs-lookup"><span data-stu-id="de49c-847">(0x01)</span></span>  |
  |  <span data-ttu-id="de49c-848">Error de directorio</span><span class="sxs-lookup"><span data-stu-id="de49c-848">Directory Error</span></span>                  | <span data-ttu-id="de49c-849">(0x02)</span><span class="sxs-lookup"><span data-stu-id="de49c-849">(0x02)</span></span>  |
  |  <span data-ttu-id="de49c-850">Error de clúster perdido</span><span class="sxs-lookup"><span data-stu-id="de49c-850">Lost Cluster Error</span></span>               | <span data-ttu-id="de49c-851">(0x04)</span><span class="sxs-lookup"><span data-stu-id="de49c-851">(0x04)</span></span>  |
  |  <span data-ttu-id="de49c-852">Error de tamaño de archivo</span><span class="sxs-lookup"><span data-stu-id="de49c-852">File Size Error</span></span>                  | <span data-ttu-id="de49c-853">(0x08)</span><span class="sxs-lookup"><span data-stu-id="de49c-853">(0x08)</span></span>  |

### <a name="media-close"></a><span data-ttu-id="de49c-854">Cierre de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-854">Media Close</span></span> 

#### <a name="fx_media_close"></a><span data-ttu-id="de49c-855">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="de49c-855">fx_media_close</span></span>

<span data-ttu-id="de49c-856">**Icono** ![Icono de cierre de elementos multimedia](./media/user-guide/fx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-856">**Icon** ![Media Close icon](./media/user-guide/fx-events/image53.png)</span></span>

<span data-ttu-id="de49c-857">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-857">**Description**</span></span>

<span data-ttu-id="de49c-858">Este evento representa un evento de cierre de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-858">This event represents a media close event.</span></span>

<span data-ttu-id="de49c-859">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-859">**Information Fields**</span></span> 

- <span data-ttu-id="de49c-860">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-860">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-861">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-861">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-862">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-862">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-863">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-863">Info Field 4: Not used.</span></span>

### <a name="media-flush"></a><span data-ttu-id="de49c-864">Vaciado de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-864">Media Flush</span></span> 

#### <a name="fx_media_flush"></a><span data-ttu-id="de49c-865">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="de49c-865">fx_media_flush</span></span>

<span data-ttu-id="de49c-866">**Icono** ![Icono de vaciado de elementos multimedia](./media/user-guide/fx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-866">**Icon** ![Media flush icon](./media/user-guide/fx-events/image54.png)</span></span>

<span data-ttu-id="de49c-867">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-867">**Description**</span></span>

<span data-ttu-id="de49c-868">Este evento representa un evento de vaciado de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-868">This event represents a media flush event.</span></span>

<span data-ttu-id="de49c-869">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-869">**Information Fields**</span></span>

- <span data-ttu-id="de49c-870">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-870">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-871">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-871">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-872">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-872">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-873">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-873">Info Field 4: Not used.</span></span>

### <a name="media-format"></a><span data-ttu-id="de49c-874">Formato de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-874">Media Format</span></span> 

#### <a name="fx_media_format"></a><span data-ttu-id="de49c-875">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="de49c-875">fx_media_format</span></span>

<span data-ttu-id="de49c-876">**Icono** ![Icono formato de elementos multimedia](./media/user-guide/fx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-876">**Icon** ![Media format icon](./media/user-guide/fx-events/image55.png)</span></span>

<span data-ttu-id="de49c-877">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-877">**Description**</span></span>

<span data-ttu-id="de49c-878">Este evento representa un evento de formato de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-878">This event represents a media format event.</span></span>

<span data-ttu-id="de49c-879">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-879">**Information Fields**</span></span>

- <span data-ttu-id="de49c-880">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-880">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-881">Campo de información 2: número de entradas raíz.</span><span class="sxs-lookup"><span data-stu-id="de49c-881">Info Field 2: Number of root entries.</span></span>
- <span data-ttu-id="de49c-882">Campo de información 3: sectores.</span><span class="sxs-lookup"><span data-stu-id="de49c-882">Info Field 3: Sectors.</span></span>
- <span data-ttu-id="de49c-883">Campo de información 4: sectores por clúster.</span><span class="sxs-lookup"><span data-stu-id="de49c-883">Info Field 4: Sectors per cluster.</span></span>

### <a name="media-open"></a><span data-ttu-id="de49c-884">Elementos multimedia abiertos</span><span class="sxs-lookup"><span data-stu-id="de49c-884">Media Open</span></span> 

#### <a name="fx_media_open"></a><span data-ttu-id="de49c-885">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="de49c-885">fx_media_open</span></span>

<span data-ttu-id="de49c-886">**Icono** ![Icono de elementos multimedia abiertos](./media/user-guide/fx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-886">**Icon** ![Media open icon](./media/user-guide/fx-events/image56.png)</span></span>

<span data-ttu-id="de49c-887">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-887">**Description**</span></span>

<span data-ttu-id="de49c-888">Este evento representa un evento de apertura de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-888">This event represents a media open event.</span></span>

<span data-ttu-id="de49c-889">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-889">**Information Fields**</span></span>

- <span data-ttu-id="de49c-890">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-890">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-891">Campo de información 2: puntero a la entrada del controlador de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-891">Info Field 2: Pointer to media driver entry.</span></span>
- <span data-ttu-id="de49c-892">Campo de información 3: puntero de memoria.</span><span class="sxs-lookup"><span data-stu-id="de49c-892">Info Field 3: Memory pointer.</span></span>
- <span data-ttu-id="de49c-893">Campo de información 4: tamaño de memoria.</span><span class="sxs-lookup"><span data-stu-id="de49c-893">Info Field 4: Memory size.</span></span>

### <a name="media-read-media-read"></a><span data-ttu-id="de49c-894">Lectura de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-894">Media Read Media Read</span></span> 

#### <a name="fx_media_read"></a><span data-ttu-id="de49c-895">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="de49c-895">fx_media_read</span></span>

<span data-ttu-id="de49c-896">**Icono** ![Icono de lectura de elementos multimedia](./media/user-guide/fx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-896">**Icon** ![Media read icon](./media/user-guide/fx-events/image57.png)</span></span>

<span data-ttu-id="de49c-897">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-897">**Description**</span></span>

<span data-ttu-id="de49c-898">Este evento representa un evento de lectura de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-898">This event represents a media read event.</span></span>

<span data-ttu-id="de49c-899">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-899">**Information Fields**</span></span>

- <span data-ttu-id="de49c-900">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-900">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-901">Campo de información 2: sector lógico.</span><span class="sxs-lookup"><span data-stu-id="de49c-901">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="de49c-902">Campo de información 3: puntero de búfer.</span><span class="sxs-lookup"><span data-stu-id="de49c-902">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="de49c-903">Campo de información 4: bytes leídos.</span><span class="sxs-lookup"><span data-stu-id="de49c-903">Info Field 4: Bytes read.</span></span>

### <a name="media-space-available"></a><span data-ttu-id="de49c-904">Espacio de elementos multimedia disponible</span><span class="sxs-lookup"><span data-stu-id="de49c-904">Media Space Available</span></span> 

#### <a name="fx_media_space_available"></a><span data-ttu-id="de49c-905">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="de49c-905">fx_media_space_available</span></span>

<span data-ttu-id="de49c-906">**Icono** ![Icono de espacio de elementos multimedia disponible](./media/user-guide/fx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-906">**Icon** ![Media space available icon](./media/user-guide/fx-events/image58.png)</span></span>

<span data-ttu-id="de49c-907">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-907">**Description**</span></span>

<span data-ttu-id="de49c-908">Este evento representa un evento de espacio de elementos multimedia disponible.</span><span class="sxs-lookup"><span data-stu-id="de49c-908">This event represents a media space available event.</span></span>

<span data-ttu-id="de49c-909">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-909">**Information Fields**</span></span> 

- <span data-ttu-id="de49c-910">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-910">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-911">Campo de información 2: puntero de bytes disponibles.</span><span class="sxs-lookup"><span data-stu-id="de49c-911">Info Field 2: Available bytes pointer.</span></span>
- <span data-ttu-id="de49c-912">Campo de información 3: número de clústeres libres.</span><span class="sxs-lookup"><span data-stu-id="de49c-912">Info Field 3: Number of free clusters.</span></span>
- <span data-ttu-id="de49c-913">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-913">Info Field 4: Not used.</span></span>

### <a name="media-volume-get"></a><span data-ttu-id="de49c-914">Obtención de volumen de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-914">Media Volume Get</span></span> 

#### <a name="fx_media_volume_get"></a><span data-ttu-id="de49c-915">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="de49c-915">fx_media_volume_get</span></span>

<span data-ttu-id="de49c-916">**Icono** ![Icono de obtención de volumen de elementos multimedia](./media/user-guide/fx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-916">**Icon** ![Media volume get icon](./media/user-guide/fx-events/image59.png)</span></span>

<span data-ttu-id="de49c-917">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-917">**Description**</span></span>

<span data-ttu-id="de49c-918">Este evento representa un evento de obtención de volumen de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-918">This event represents a media volume get event.</span></span>

<span data-ttu-id="de49c-919">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-919">**Information Fields**</span></span>

- <span data-ttu-id="de49c-920">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-920">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-921">Campo de información 2: puntero al nombre del volumen.</span><span class="sxs-lookup"><span data-stu-id="de49c-921">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="de49c-922">Campo de información 3: origen de volumen.</span><span class="sxs-lookup"><span data-stu-id="de49c-922">Info Field 3: Volume source.</span></span>
- <span data-ttu-id="de49c-923">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-923">Info Field 4: Not used.</span></span>

### <a name="media-volume-set"></a><span data-ttu-id="de49c-924">Definición de volumen de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-924">Media Volume Set</span></span> 

#### <a name="fx_media_volume_set"></a><span data-ttu-id="de49c-925">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="de49c-925">fx_media_volume_set</span></span>

<span data-ttu-id="de49c-926">**Icono** ![Icono de obtención de definición de volumen de elementos multimedia](./media/user-guide/fx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-926">**Icon** ![Media volume set icon](./media/user-guide/fx-events/image60.png)</span></span>

<span data-ttu-id="de49c-927">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-927">**Description**</span></span>

<span data-ttu-id="de49c-928">Este evento representa un evento de definición de volumen de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-928">This event represents a media volume set event.</span></span>

<span data-ttu-id="de49c-929">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-929">**Information Fields**</span></span> 
- <span data-ttu-id="de49c-930">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-930">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-931">Campo de información 2: puntero al nombre del volumen.</span><span class="sxs-lookup"><span data-stu-id="de49c-931">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="de49c-932">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-932">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-933">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-933">Info Field 4: Not used.</span></span>

### <a name="media-write"></a><span data-ttu-id="de49c-934">Escritura de elementos multimedia</span><span class="sxs-lookup"><span data-stu-id="de49c-934">Media Write</span></span> 

#### <a name="fx_media_write"></a><span data-ttu-id="de49c-935">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="de49c-935">fx_media_write</span></span>

<span data-ttu-id="de49c-936">**Icono** ![Icono de escritura de elementos multimedia](./media/user-guide/fx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-936">**Icon** ![Media write icon](./media/user-guide/fx-events/image61.png)</span></span>

<span data-ttu-id="de49c-937">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-937">**Description**</span></span>

<span data-ttu-id="de49c-938">Este evento representa un evento de escritura de elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-938">This event represents a media write event.</span></span>

<span data-ttu-id="de49c-939">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-939">**Information Fields**</span></span>

- <span data-ttu-id="de49c-940">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-940">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-941">Campo de información 2: sector lógico.</span><span class="sxs-lookup"><span data-stu-id="de49c-941">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="de49c-942">Campo de información 3: puntero de búfer.</span><span class="sxs-lookup"><span data-stu-id="de49c-942">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="de49c-943">Campo de información 4: bytes escritos.</span><span class="sxs-lookup"><span data-stu-id="de49c-943">Info Field 4: Bytes written.</span></span>

### <a name="system-date-get"></a><span data-ttu-id="de49c-944">Obtención de fecha del sistema</span><span class="sxs-lookup"><span data-stu-id="de49c-944">System Date Get</span></span> 

#### <a name="fx_system_date_get"></a><span data-ttu-id="de49c-945">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="de49c-945">fx_system_date_get</span></span> 

<span data-ttu-id="de49c-946">**Icono** ![Icono de obtención de fecha del sistema](./media/user-guide/fx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-946">**Icon** ![System date get icon](./media/user-guide/fx-events/image62.png)</span></span>

<span data-ttu-id="de49c-947">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-947">**Description**</span></span>

<span data-ttu-id="de49c-948">Este evento representa un evento de obtención de fecha del sistema.</span><span class="sxs-lookup"><span data-stu-id="de49c-948">This event represents a system date get event.</span></span>

<span data-ttu-id="de49c-949">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-949">**Information Fields**</span></span>

- <span data-ttu-id="de49c-950">Campo de información 1: año.</span><span class="sxs-lookup"><span data-stu-id="de49c-950">Info Field 1: Year.</span></span>
- <span data-ttu-id="de49c-951">Campo de información 2: mes.</span><span class="sxs-lookup"><span data-stu-id="de49c-951">Info Field 2: Month.</span></span>
- <span data-ttu-id="de49c-952">Campo de información 3: día.</span><span class="sxs-lookup"><span data-stu-id="de49c-952">Info Field 3: Day.</span></span>
- <span data-ttu-id="de49c-953">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-953">Info Field 4: Not used.</span></span>

### <a name="system-date-set"></a><span data-ttu-id="de49c-954">Definición de fecha del sistema</span><span class="sxs-lookup"><span data-stu-id="de49c-954">System Date Set</span></span> 

#### <a name="fx_system_date_set"></a><span data-ttu-id="de49c-955">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="de49c-955">fx_system_date_set</span></span> 

<span data-ttu-id="de49c-956">**Icono** ![Icono de definición de fecha del sistema](./media/user-guide/fx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-956">**Icon** ![System date set icon](./media/user-guide/fx-events/image63.png)</span></span>

<span data-ttu-id="de49c-957">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-957">**Description**</span></span>

<span data-ttu-id="de49c-958">Este evento representa un evento de definición de fecha del sistema.</span><span class="sxs-lookup"><span data-stu-id="de49c-958">This event represents a system date set event.</span></span>

<span data-ttu-id="de49c-959">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-959">**Information Fields**</span></span>

- <span data-ttu-id="de49c-960">Campo de información 1: año.</span><span class="sxs-lookup"><span data-stu-id="de49c-960">Info Field 1: Year.</span></span>
- <span data-ttu-id="de49c-961">Campo de información 2: mes.</span><span class="sxs-lookup"><span data-stu-id="de49c-961">Info Field 2: Month.</span></span>
- <span data-ttu-id="de49c-962">Campo de información 3: día.</span><span class="sxs-lookup"><span data-stu-id="de49c-962">Info Field 3: Day.</span></span>
- <span data-ttu-id="de49c-963">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-963">Info Field 4: Not used.</span></span>

### <a name="system-initialize"></a><span data-ttu-id="de49c-964">Inicialización del sistema</span><span class="sxs-lookup"><span data-stu-id="de49c-964">System Initialize</span></span> 

#### <a name="fx_system_initialize"></a><span data-ttu-id="de49c-965">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="de49c-965">fx_system_initialize</span></span> 

<span data-ttu-id="de49c-966">**Icono** ![Icono de inicialización del sistema](./media/user-guide/fx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-966">**Icon** ![System initialize icon](./media/user-guide/fx-events/image64.png)</span></span>

<span data-ttu-id="de49c-967">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-967">**Description**</span></span>

<span data-ttu-id="de49c-968">Este evento representa un evento de inicialización del sistema.</span><span class="sxs-lookup"><span data-stu-id="de49c-968">This event represents a system initialize event.</span></span>

<span data-ttu-id="de49c-969">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-969">**Information Fields**</span></span>

- <span data-ttu-id="de49c-970">Campo de información 1: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-970">Info Field 1: Not used.</span></span>
- <span data-ttu-id="de49c-971">Campo de información 2: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-971">Info Field 2: Not used.</span></span>
- <span data-ttu-id="de49c-972">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-972">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-973">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-973">Info Field 4: Not used.</span></span>

### <a name="system-time-get"></a><span data-ttu-id="de49c-974">Obtención de hora del sistema</span><span class="sxs-lookup"><span data-stu-id="de49c-974">System Time Get</span></span> 

#### <a name="fx_system_time_get"></a><span data-ttu-id="de49c-975">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="de49c-975">fx_system_time_get</span></span> 

<span data-ttu-id="de49c-976">**Icono** ![Icono de obtención de hora del sistema](./media/user-guide/fx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-976">**Icon** ![System time get icon](./media/user-guide/fx-events/image65.png)</span></span>

<span data-ttu-id="de49c-977">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-977">**Description**</span></span>

<span data-ttu-id="de49c-978">Este evento representa un evento de obtención de hora del sistema.</span><span class="sxs-lookup"><span data-stu-id="de49c-978">This event represents a system time get event.</span></span>

<span data-ttu-id="de49c-979">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-979">**Information Fields**</span></span> 

- <span data-ttu-id="de49c-980">Campo de información 1: hora.</span><span class="sxs-lookup"><span data-stu-id="de49c-980">Info Field 1: Hour.</span></span>
- <span data-ttu-id="de49c-981">Campo de información 2: minuto.</span><span class="sxs-lookup"><span data-stu-id="de49c-981">Info Field 2: Minute.</span></span>
- <span data-ttu-id="de49c-982">Campo de información 3: segundo.</span><span class="sxs-lookup"><span data-stu-id="de49c-982">Info Field 3: Second.</span></span>
- <span data-ttu-id="de49c-983">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-983">Info Field 4: Not used.</span></span>

### <a name="system-time-set"></a><span data-ttu-id="de49c-984">Definición de hora del sistema</span><span class="sxs-lookup"><span data-stu-id="de49c-984">System Time Set</span></span> 

#### <a name="fx_system_time_set"></a><span data-ttu-id="de49c-985">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="de49c-985">fx_system_time_set</span></span> 

<span data-ttu-id="de49c-986">**Icono** ![Icono de definición de hora del sistema](./media/user-guide/fx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-986">**Icon** ![System time set icon](./media/user-guide/fx-events/image66.png)</span></span>

<span data-ttu-id="de49c-987">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-987">**Description**</span></span>

<span data-ttu-id="de49c-988">Este evento representa un evento de definición de hora del sistema.</span><span class="sxs-lookup"><span data-stu-id="de49c-988">This event represents a system time set event.</span></span>

<span data-ttu-id="de49c-989">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-989">**Information Fields**</span></span>

- <span data-ttu-id="de49c-990">Campo de información 1: hora.</span><span class="sxs-lookup"><span data-stu-id="de49c-990">Info Field 1: Hour.</span></span>
- <span data-ttu-id="de49c-991">Campo de información 2: minuto.</span><span class="sxs-lookup"><span data-stu-id="de49c-991">Info Field 2: Minute.</span></span>
- <span data-ttu-id="de49c-992">Campo de información 3: segundo.</span><span class="sxs-lookup"><span data-stu-id="de49c-992">Info Field 3: Second.</span></span>
- <span data-ttu-id="de49c-993">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-993">Info Field 4: Not used.</span></span>

### <a name="unicode-directory-create"></a><span data-ttu-id="de49c-994">Creación de directorio Unicode</span><span class="sxs-lookup"><span data-stu-id="de49c-994">Unicode Directory Create</span></span> 

#### <a name="fx_unicode_directory_create"></a><span data-ttu-id="de49c-995">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="de49c-995">fx_unicode_directory_create</span></span> 

<span data-ttu-id="de49c-996">**Icono** ![Icono de creación de directorio Unicode](./media/user-guide/fx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-996">**Icon** ![Unicode directory create icon](./media/user-guide/fx-events/image67.png)</span></span>

<span data-ttu-id="de49c-997">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-997">**Description**</span></span>

<span data-ttu-id="de49c-998">Este evento representa un evento de creación de directorio Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-998">This event represents a Unicode directory create event.</span></span>

<span data-ttu-id="de49c-999">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-999">**Information Fields**</span></span> 

- <span data-ttu-id="de49c-1000">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-1000">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-1001">Campo de información 2: puntero a nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1001">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="de49c-1002">Campo de información 3: tamaño del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1002">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="de49c-1003">Campo de información 4: puntero al nombre corto.</span><span class="sxs-lookup"><span data-stu-id="de49c-1003">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-directory-rename"></a><span data-ttu-id="de49c-1004">Cambio de nombre de directorio Unicode</span><span class="sxs-lookup"><span data-stu-id="de49c-1004">Unicode Directory Rename</span></span> 

#### <a name="fx_unicode_directory_rename"></a><span data-ttu-id="de49c-1005">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="de49c-1005">fx_unicode_directory_rename</span></span>

<span data-ttu-id="de49c-1006">**Icono** ![Icono de cambio de nombre de directorio Unicode](./media/user-guide/fx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-1006">**Icon** ![Unicode directory rename icon](./media/user-guide/fx-events/image68.png)</span></span>

<span data-ttu-id="de49c-1007">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-1007">**Description**</span></span>

<span data-ttu-id="de49c-1008">Este evento representa un evento de cambio de nombre de directorio Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1008">This event represents a Unicode directory rename event.</span></span>

<span data-ttu-id="de49c-1009">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-1009">**Information Fields**</span></span> 

- <span data-ttu-id="de49c-1010">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-1010">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-1011">Campo de información 2: puntero a nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1011">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="de49c-1012">Campo de información 3: tamaño del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1012">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="de49c-1013">Campo de información 4: puntero al nombre corto.</span><span class="sxs-lookup"><span data-stu-id="de49c-1013">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-create"></a><span data-ttu-id="de49c-1014">Creación de archivo Unicode</span><span class="sxs-lookup"><span data-stu-id="de49c-1014">Unicode File Create</span></span> 

#### <a name="fx_unicode_file_create"></a><span data-ttu-id="de49c-1015">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="de49c-1015">fx_unicode_file_create</span></span>

<span data-ttu-id="de49c-1016">**Icono** ![Icono de creación de archivo Unicode](./media/user-guide/fx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-1016">**Icon** ![Unicode file create icon](./media/user-guide/fx-events/image69.png)</span></span>

<span data-ttu-id="de49c-1017">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-1017">**Description**</span></span>

<span data-ttu-id="de49c-1018">Este evento representa un evento de creación de archivo Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1018">This event represents a Unicode file create event.</span></span>

<span data-ttu-id="de49c-1019">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-1019">**Information Fields**</span></span>

- <span data-ttu-id="de49c-1020">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-1020">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-1021">Campo de información 2: puntero al nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1021">Info Field 2: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="de49c-1022">Campo de información 3: tamaño del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1022">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="de49c-1023">Campo de información 4: puntero al nombre corto.</span><span class="sxs-lookup"><span data-stu-id="de49c-1023">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-rename"></a><span data-ttu-id="de49c-1024">Cambio de nombre de archivo Unicode</span><span class="sxs-lookup"><span data-stu-id="de49c-1024">Unicode File Rename</span></span> 

#### <a name="fx_unicode_file_rename"></a><span data-ttu-id="de49c-1025">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="de49c-1025">fx_unicode_file_rename</span></span>

<span data-ttu-id="de49c-1026">**Icono** ![Icono de cambio de nombre de archivo Unicode](./media/user-guide/fx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-1026">**Icon** ![Unicode file rename icon](./media/user-guide/fx-events/image70.png)</span></span>

<span data-ttu-id="de49c-1027">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-1027">**Description**</span></span>

<span data-ttu-id="de49c-1028">Este evento representa un evento de cambio de nombre de archivo Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1028">This event represents a Unicode file rename event.</span></span>

<span data-ttu-id="de49c-1029">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-1029">**Information Fields**</span></span>

- <span data-ttu-id="de49c-1030">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-1030">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-1031">Campo de información 2: puntero a nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1031">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="de49c-1032">Campo de información 3: tamaño del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1032">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="de49c-1033">Campo de información 4: puntero al nombre corto.</span><span class="sxs-lookup"><span data-stu-id="de49c-1033">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-length-get"></a><span data-ttu-id="de49c-1034">Obtención de longitud Unicode</span><span class="sxs-lookup"><span data-stu-id="de49c-1034">Unicode Length Get</span></span> 

#### <a name="fx_unicode_length_get"></a><span data-ttu-id="de49c-1035">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="de49c-1035">fx_unicode_length_get</span></span>

<span data-ttu-id="de49c-1036">**Icono** ![Icono de obtención de longitud Unicode](./media/user-guide/fx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-1036">**Icon** ![Unicode length get icon](./media/user-guide/fx-events/image71.png)</span></span>

<span data-ttu-id="de49c-1037">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-1037">**Description**</span></span>

<span data-ttu-id="de49c-1038">Este evento representa un evento de obtención de longitud Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1038">This event represents a Unicode length get event.</span></span>

<span data-ttu-id="de49c-1039">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-1039">**Information Fields**</span></span>

- <span data-ttu-id="de49c-1040">Campo de información 1: puntero al nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1040">Info Field 1: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="de49c-1041">Campo de información 2: longitud.</span><span class="sxs-lookup"><span data-stu-id="de49c-1041">Info Field 2: Length.</span></span>
- <span data-ttu-id="de49c-1042">Campo de información 3: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-1042">Info Field 3: Not used.</span></span>
- <span data-ttu-id="de49c-1043">Campo de información 4: sin usar.</span><span class="sxs-lookup"><span data-stu-id="de49c-1043">Info Field 4: Not used.</span></span>

### <a name="unicode-name-get"></a><span data-ttu-id="de49c-1044">Obtención de nombre Unicode</span><span class="sxs-lookup"><span data-stu-id="de49c-1044">Unicode Name Get</span></span> 

#### <a name="fx_unicode_name_get"></a><span data-ttu-id="de49c-1045">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="de49c-1045">fx_unicode_name_get</span></span>

<span data-ttu-id="de49c-1046">**Icono** ![Icono de obtención de nombre Unicode](./media/user-guide/fx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-1046">**Icon** ![Unicode name get icon](./media/user-guide/fx-events/image72.png)</span></span>

<span data-ttu-id="de49c-1047">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-1047">**Description**</span></span>

<span data-ttu-id="de49c-1048">Este evento representa un evento de obtención de nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1048">This event represents a Unicode name get event.</span></span>

<span data-ttu-id="de49c-1049">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-1049">**Information Fields**</span></span>

- <span data-ttu-id="de49c-1050">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-1050">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-1051">Campo de información 2: nombre corto del origen.</span><span class="sxs-lookup"><span data-stu-id="de49c-1051">Info Field 2: Source short name.</span></span>
- <span data-ttu-id="de49c-1052">Campo de información 3: puntero de nombre Unicode de destino.</span><span class="sxs-lookup"><span data-stu-id="de49c-1052">Info Field 3: Destination Unicode name pointer.</span></span>
- <span data-ttu-id="de49c-1053">Campo de información 4: longitud del nombre Unicode de destino.</span><span class="sxs-lookup"><span data-stu-id="de49c-1053">Info Field 4: Destination Unicode name length.</span></span>

### <a name="unicode-short-name-get"></a><span data-ttu-id="de49c-1054">Obtención de nombre corto Unicode</span><span class="sxs-lookup"><span data-stu-id="de49c-1054">Unicode Short Name Get</span></span> 

#### <a name="fx_unicode_short_name_get"></a><span data-ttu-id="de49c-1055">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="de49c-1055">fx_unicode_short_name_get</span></span>

<span data-ttu-id="de49c-1056">**Icono** ![Icono de obtención de nombre corto Unicode](./media/user-guide/fx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="de49c-1056">**Icon** ![Unicode short name get icon](./media/user-guide/fx-events/image73.png)</span></span>

<span data-ttu-id="de49c-1057">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="de49c-1057">**Description**</span></span>

<span data-ttu-id="de49c-1058">Este evento representa un evento de obtención de nombre corto Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1058">This event represents a Unicode short name get event.</span></span>

<span data-ttu-id="de49c-1059">**Campos de información**</span><span class="sxs-lookup"><span data-stu-id="de49c-1059">**Information Fields**</span></span>

- <span data-ttu-id="de49c-1060">Campo de información 1: puntero a los elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="de49c-1060">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="de49c-1061">Campo de información 2: puntero al nombre Unicode de origen.</span><span class="sxs-lookup"><span data-stu-id="de49c-1061">Info Field 2: Pointer to source Unicode name.</span></span>
- <span data-ttu-id="de49c-1062">Campo de información 3: longitud del nombre Unicode.</span><span class="sxs-lookup"><span data-stu-id="de49c-1062">Info Field 3: Length of Unicode name.</span></span>
- <span data-ttu-id="de49c-1063">Campo de información 4: puntero al nombre corto.</span><span class="sxs-lookup"><span data-stu-id="de49c-1063">Info Field 4: Pointer to short name.</span></span>