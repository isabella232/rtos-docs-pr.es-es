---
title: 'Capítulo 7: Eventos de seguimiento de Azure RTOS FileX'
description: Este capítulo contiene una descripción de los eventos de Azure RTOS FileX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8668f0867e205afdeab112dfedd257998a5f5b7ff256f27298072dde3e9019b0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116803301"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a>Capítulo 7: Eventos de seguimiento de Azure RTOS FileX

Este capítulo contiene una descripción de los eventos de Azure RTOS FileX. 

## <a name="list-of-events-and-icons"></a>Lista de eventos e iconos

**En la siguiente lista se enumeran eventos de FileX mostrados por TraceX.**

En la siguiente lista se describe cada uno de ellos:

| **Icono**                         | **Significado**                               |
| -------------------------------- | ----------------------------------------- |
| ![Icono de error de caché del sector lógico interno](./media/user-guide/fx-events/image1.png)    | Error de caché del sector lógico interno |
| ![Icono de error de caché del directorio interno](./media/user-guide/fx-events/image2.png)    | Error de caché del directorio interno |
| ![Icono de vaciado de elementos multimedia internos](./media/user-guide/fx-events/image3.png)    | Vaciado de elementos multimedia internos |
| ![Icono de lectura de entrada de directorio interno](./media/user-guide/fx-events/image4.png)    | Lectura de entrada de directorio interno |
| ![Icono de escritura de entrada de directorio interno](./media/user-guide/fx-events/image5.png)    | Escritura de entrada de directorio interno |
| ![Icono de lectura del controlador de E/S interno](./media/user-guide/fx-events/image6.png)    | Lectura del controlador de E/S interno |
| ![Icono de escritura del controlador de E/S interno](./media/user-guide/fx-events/image7.png)    | Escritura del controlador de E/S interno |
| ![Icono de vaciado de controlador de E/S interno](./media/user-guide/fx-events/image8.png)    | Vaciado de controlador de E/S interno |
| ![Icono de anulación de controlador de E/S interno](./media/user-guide/fx-events/image9.png)    | Anulación de controlador de E/S interno |
| ![Icono de inicialización de controlador de E/S interno](./media/user-guide/fx-events/image10.png)    | Inicialización de controlador de E/S interno |
| ![Icono de lectura de controlador de E/S interno](./media/user-guide/fx-events/image11.png)    | Lectura de controlador de E/S interno |
| ![Icono de sectores de versión de controlador de E/S interno](./media/user-guide/fx-events/image12.png)    | Sectores de versión de controlador de E/S interno |
| ![Icono de escritura de controlador de E/S interno](./media/user-guide/fx-events/image13.png)    | Escritura de controlador de E/S interno |
| ![Icono de anulación de inicialización de controlador de E/S interno](./media/user-guide/fx-events/image14.png)    | Anulación de inicialización de controlador de E/S interno |
| ![Icono de lectura de atributos de directorio](./media/user-guide/fx-events/image15.png)    | **Lectura de atributos de directorio** (*fx_directory_attributes_read*) |
| ![Icono de definición de atributos de directorio](./media/user-guide/fx-events/image16.png)    | **Definición de atributos de directorio** (*fx_directory_attributes_read*) |
| ![Icono de creación de directorio](./media/user-guide/fx-events/image17.png)    | **Creación de directorio** (*fx_directory_create*) |
| ![Icono de obtención predeterminada de directorio](./media/user-guide/fx-events/image18.png)    | **Obtención predeterminada de directorio** (*fx_directory_default_get*) |
| ![Icono de definición predeterminada de directorio](./media/user-guide/fx-events/image19.png)    | **Definición predeterminada de directorio** (*fx_directory_default_get*) |
| ![Icono de eliminación de directorio](./media/user-guide/fx-events/image20.png)    | **Eliminación de directorio** (*fx_directory_delete*) |
| ![Icono de búsqueda de primera entrada de directorio](./media/user-guide/fx-events/image21.png)    | **Búsqueda de primera entrada de directorio** (*fx_directory_first_entry_find*) |
| ![Icono de búsqueda de primera entrada completa de directorio](./media/user-guide/fx-events/image22.png)    | **Búsqueda de primera entrada completa de directorio** (*fx_directory_first_entry_find*) |
| ![Icono de obtención de información de directorio](./media/user-guide/fx-events/image23.png)    | **Obtención de información de directorio** (*fx_directory_information_get*) |
| ![Icono de borrado de ruta local de directorio](./media/user-guide/fx-events/image24.png)    | **Borrado de ruta local de directorio** (*fx_directory_local_path_clear*) |
| ![Icono de obtención de ruta de acceso local de directorio](./media/user-guide/fx-events/image25.png)    | **Obtención de ruta de acceso local de directorio** (*fx_directory_local_path_get*) |
| ![Icono de restauración de ruta de acceso local de directorio](./media/user-guide/fx-events/image26.png)    | **Restauración de ruta de acceso local de directorio** (*fx_directory_local_path_restore*) |
| ![Icono de definición de ruta de acceso local de directorio](./media/user-guide/fx-events/image27.png)    | **Definición de ruta de acceso local de directorio** (*fx_directory_local_path_set*) |
| ![Icono de obtención de nombre largo de directorio](./media/user-guide/fx-events/image28.png)    | **Obtención de nombre largo de directorio** (*fx_directory_long_name_get*) |
| ![Icono de prueba de nombre de directorio](./media/user-guide/fx-events/image29.png)    | **Prueba de nombre de directorio** (*fx_directory_name_test*) |
| ![Icono de búsqueda de siguiente entrada de directorio](./media/user-guide/fx-events/image30.png)    | **Búsqueda de siguiente entrada de directorio** (*fx_directory_next_entry_find*) |
| ![Icono de búsqueda de siguiente entrada completa de directorio](./media/user-guide/fx-events/image31.png)    | **Búsqueda de siguiente entrada completa de directorio** (*fx_directory_next_full_entry_find*) |
| ![Icono de cambio de nombre de directorio](./media/user-guide/fx-events/image32.png)    | **Cambio de nombre de directorio** (*fx_directory_rename*) |
| ![Icono de obtención de nombre corto de directorio](./media/user-guide/fx-events/image33.png)    | **Obtención de nombre corto de directorio** (*fx_directory_short_name_get*) |
| ![Icono de asignación de archivos](./media/user-guide/fx-events/image34.png)    | **Asignación de archivos** (*fx_file_allocate*) |
| ![Icono de lectura de atributos de archivos](./media/user-guide/fx-events/image35.png)    | **Lectura de atributos de archivos** (*fx_file_attributes_read*) |
| ![Icono de definición de atributos de archivos](./media/user-guide/fx-events/image36.png)    | **Definición de atributos de archivos** (*fx_file_attributes_set*) |
| ![Icono de asignación de mejor esfuerzo de archivo](./media/user-guide/fx-events/image37.png)    | **Asignación de mejor esfuerzo de archivo** (*fx_file_best_effort_allocate*) |
| ![Icono de cierre de archivo](./media/user-guide/fx-events/image38.png)    | **Cierre de archivo** (*fx_file_close*) |
| ![Icono de creación de archivo](./media/user-guide/fx-events/image39.png)    | **Creación de archivo** (*fx_file_create*) |
| ![Icono de definición de fecha y hora de archivo](./media/user-guide/fx-events/image40.png)    | **Definición de fecha y hora de archivo** (*fx_file_date_time_set*) |
| ![Icono de eliminación de archivo](./media/user-guide/fx-events/image41.png)    | **Eliminación de archivo** (*fx_file_delete*) |
| ![Icono de apertura de archivo](./media/user-guide/fx-events/image42.png)    | **Apertura de archivo** (*fx_file_open*) |
| ![Icono de lectura de archivo](./media/user-guide/fx-events/image43.png)    | **Lectura de archivo** (*fx_file_read*) |
| ![Icono de búsqueda relativa de archivo](./media/user-guide/fx-events/image44.png)    | **Búsqueda relativa de archivo** (*fx_file_relative_seek*) |
| ![Icono de cambio de nombre de archivo](./media/user-guide/fx-events/image45.png)    | **Cambio de nombre de archivo** (*fx_file_rename*) |
| ![Icono de búsqueda de archivo](./media/user-guide/fx-events/image46.png)    | **Búsqueda de archivo** (*fx_file_seek*) |
| ![Icono de truncamiento de archivo](./media/user-guide/fx-events/image47.png)    | **Truncamiento de archivo** (*fx_file_truncate*) |
| ![Icono de versión de truncamiento de archivo](./media/user-guide/fx-events/image48.png)    | **Versión de truncamiento de archivo** (*fx_file_truncate_release*) |
| ![Icono de escritura de archivo](./media/user-guide/fx-events/image49.png)    | **Escritura de archivo** (*fx_file_write*) |
| ![Icono de anulación de elementos multimedia](./media/user-guide/fx-events/image50.png)    | **Anulación de elementos multimedia** (*fx_media_abort*) |
| ![Icono de invalidación de caché de elementos multimedia](./media/user-guide/fx-events/image51.png)    | **Invalidación de caché de elementos multimedia** (*fx_media_cache_invalidate*) |
| ![Icono de comprobación de elementos multimedia](./media/user-guide/fx-events/image52.png)    | **Comprobación de elementos multimedia** (*fx_media_check*) |
| ![*Icono de cierre de elementos multimedia](./media/user-guide/fx-events/image53.png)    | **Cierre de elementos multimedia** (*fx_media_close*) |
| ![Icono de vaciado de elementos multimedia](./media/user-guide/fx-events/image54.png)    | **Vaciado de elementos multimedia** (*fx_media_flush*) |
| ![Icono de formato de elementos multimedia](./media/user-guide/fx-events/image55.png)    | **Formato de elementos multimedia** (*fx_media_format*) |
| ![Icono de apertura de elementos multimedia](./media/user-guide/fx-events/image56.png)    | **Apertura de elementos multimedia** (*fx_media_open*) |
| ![Icono de lectura de elementos multimedia](./media/user-guide/fx-events/image57.png)    | **Lectura de elementos multimedia** (*fx_media_read*) |
| ![Icono de espacio de elementos multimedia disponible](./media/user-guide/fx-events/image58.png)    | **Espacio de elementos multimedia disponible** (*fx_media_space_available*) |
| ![Icono de obtención de volumen de elementos multimedia](./media/user-guide/fx-events/image59.png)    | **Obtención de volumen de elementos multimedia** (*fx_media_volume_get*) |
| ![Icono de definición de volúmenes de elementos multimedia](./media/user-guide/fx-events/image60.png)    | **Definición de volúmenes de elementos multimedia** (*fx_media_volume_set*) |
| ![Icono de escritura de elementos multimedia](./media/user-guide/fx-events/image61.png)    | **Escritura de medios multimedia** (*fx_media_write*) |
| ![Icono de obtención de fecha del sistema](./media/user-guide/fx-events/image62.png)    | **Obtención de fecha del sistema** (*fx_system_date_get*) |
| ![Icono de definición de fecha del sistema](./media/user-guide/fx-events/image63.png)    | **Definición de fecha del sistema** (*fx_system_date_get*) |
| ![Icono de inicialización del sistema](./media/user-guide/fx-events/image64.png)    | **Inicialización del sistema** (*fx_system_initialize*) |
| ![Icono de obtención de hora del sistema](./media/user-guide/fx-events/image65.png)    | **Obtención de hora del sistema** (*fx_system_time_get*) |
| ![Icono de definición de hora del sistema](./media/user-guide/fx-events/image66.png)    | **Definición de hora del sistema** (*fx_system_time_get*) |
| ![Icono de creación de directorio Unicode](./media/user-guide/fx-events/image67.png)    | **Creación de directorio Unicode** (*fx_unicode_directory_create*) |
| ![Icono de cambio de nombre de directorio Unicode](./media/user-guide/fx-events/image68.png)    | **Cambio de nombre de directorio Unicode** (*fx_unicode_directory_rename*) |
| ![Icono de creación de archivo Unicode](./media/user-guide/fx-events/image69.png)    | **Creación de archivo Unicode** (*fx_unicode_file_create*) |
| ![Icono de cambio de nombre de archivo Unicode](./media/user-guide/fx-events/image70.png)    | **Cambio de nombre de archivo Unicode** (*fx_unicode_file_rename*) |
| ![Icono de obtención de longitud Unicode](./media/user-guide/fx-events/image71.png)    | **Obtención de longitud Unicode** (*fx_unicode_length_get*) |
| ![Icono de obtención de nombre Unicode](./media/user-guide/fx-events/image72.png)    | **Obtención de nombre Unicode** (*fx_unicode_name_get*) |
| ![Icono de obtención de nombre corto Unicode](./media/user-guide/fx-events/image73.png)    | **Obtención de nombre corto Unicode** (*fx_unicode_short_name_get*) |

## <a name="event-descriptions"></a>Descripciones de eventos

A continuación se describe cada evento individual.

### <a name="internal-logical-sector-cache-miss"></a>Error de caché del sector lógico interno 

#### <a name="internal-logical-sector-cache-miss"></a>Error de caché del sector lógico interno

**Icono** ![Icono de error de caché del sector lógico interno](./media/user-guide/fx-events/image1.png)

**Descripción**

Este evento representa un error de caché del sector lógico FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sector.
- Campo de información 3: total de líneas no ejecutadas.
- Campo de información 4: tamaño de caché.

### <a name="internal-directory-cache-miss"></a>Error de caché del directorio interno

#### <a name="internal-directory-cache-miss"></a>Error de caché del directorio interno

**Icono** ![Icono de error de caché del directorio interno](./media/user-guide/fx-events/image2.png)

**Descripción** 

Este evento representa un error de caché del directorio FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: total de líneas no ejecutadas.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="internal-media-flush"></a>Vaciado de elementos multimedia internos 

#### <a name="internal-media-flush"></a>Vaciado de elementos multimedia internos

**Icono** ![Icono de vaciado interno de elementos multimedia](./media/user-guide/fx-events/image3.png)

**Descripción**

Este evento representa un vaciado interno de elementos multimedia FileX.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: número de sectores sucios.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.


### <a name="internal-directory-entry-read"></a>Lectura de entrada de directorio interno 

#### <a name="internal-directory-entry-read"></a>Lectura de entrada de directorio interno

**Icono** ![Icono de lectura de entrada de directorio interno](./media/user-guide/fx-events/image4.png)

**Descripción**

Este evento representa un evento de lectura de entrada del directorio FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="internal-directory-entry-write"></a>Escritura de entrada de directorio interno

#### <a name="internal-directory-entry-write"></a>Escritura de entrada de directorio interno

**Icono** ![Icono de escritura de entrada de directorio interno](./media/user-guide/fx-events/image5.png)

**Descripción**

Este evento representa un evento de escritura de entrada de directorio de FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="internal-io-driver-read"></a>Lectura del controlador de E/S interno 

#### <a name="internal-io-driver-read"></a>Lectura del controlador de E/S interno 

**Icono** ![Icono de lectura del controlador de E/S interno](./media/user-guide/fx-events/image6.png)

**Descripción** 

Este evento representa un evento de lectura del controlador de E/S de FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sector.
- Campo de información 3: número de sectores.
- Campo de información 4: puntero de búfer.

### <a name="internal-io-driver-write"></a>Escritura del controlador de E/S interno 

#### <a name="internal-io-driver-write"></a>Escritura del controlador de E/S interno 

**Icono** ![Icono de escritura del controlador de E/S interno](./media/user-guide/fx-events/image7.png)

**Descripción** 

Este evento representa un evento de escritura del controlador de E/S de FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sector.
- Campo de información 3: número de sectores.
- Campo de información 4: puntero de búfer.

### <a name="internal-io-driver-flush"></a>Vaciado de controlador de E/S interno 

#### <a name="internal-io-driver-flush"></a>Vaciado de controlador de E/S interno 

**Icono** ![Icono de vaciado de controlador de E/S interno](./media/user-guide/fx-events/image8.png)

**Descripción** 

Este evento representa un evento de vaciado de controlador de E/S FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="internal-io-driver-abort"></a>Anulación de controlador de E/S interno 

#### <a name="internal-io-dirver-abort"></a>Anulación de controlador de E/S interno

**Icono** ![Icono de anulación de controlador de E/S interno](./media/user-guide/fx-events/image9.png)

**Descripción**

Este evento representa un evento de anulación de controlador de E/S de FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="internal-io-driver-initialize"></a>Inicialización de controlador de E/S interno 

#### <a name="internal-io-driver-initialize"></a>Inicialización de controlador de E/S interna 

**Icono** ![Icono de inicialización de controlador de E/S interna](./media/user-guide/fx-events/image10.png)

**Descripción** 

Este evento representa un evento de inicialización del controlador de E/S de FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="internal-io-driver-boot-sector-read"></a>Lectura del sector de arranque del controlador de E/S interno 

#### <a name="internal-io-driver-boot-sector-read"></a>Lectura del sector de arranque del controlador de E/S interno 

**Icono** ![Icono de lectura del sector de arranque del controlador de E/S interno](./media/user-guide/fx-events/image11.png)

**Descripción** 

Este evento representa un evento de lectura del sector de arranque del controlador de E/S FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero de búfer.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="internal-io-driver-release-sectors"></a>Sectores de versión de controlador de E/S interno 

#### <a name="internal-io-driver-release-sectors"></a>Sectores de versión de controlador de E/S interno 

**Icono** ![Icono de sectores de versión de controlador de E/S interno](./media/user-guide/fx-events/image12.png)

**Descripción** 

Este evento representa un evento de sectores de la versión del controlador de E/S de FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sector.
- Campo de información 3: número de sectores.
- Campo de información 4: sin usar.

### <a name="internal-io-driver-boot-sector-write"></a>Escritura del sector de arranque del controlador de E/S interno

#### <a name="internal-io-driver-boot-sector-write"></a>Escritura del sector de arranque del controlador de E/S interno 

**Icono** ![Escritura del sector de arranque del controlador de E/S interno](./media/user-guide/fx-events/image13.png)

**Descripción** 

Este evento representa un evento de escritura del sector de arranque del controlador de E/S de FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero de búfer.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="internal-io-driver-un-initialize"></a>Anulación de inicialización de controlador de E/S interno 

#### <a name="internal-io-driver-un-initialize"></a>Anulación de inicialización del controlador de E/S interna 

**Icono** ![Icono de anulación de inicialización del controlador de E/S interna](./media/user-guide/fx-events/image14.png)

**Descripción** 

Este evento representa un evento de anulación de inicialización del controlador de E/S de FileX interno.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.
</blockquote></td>

### <a name="directory-attributes-read"></a>Lectura de atributos de directorio 

#### <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read 

**Icono** ![Icono de lectura de atributos de directorio](./media/user-guide/fx-events/image15.png)

**Descripción** 

Este evento representa un evento de lectura de atributos de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3; asignación de bits de atributos:

  | Atributo                         | Value        |
  |---------------------------------- | --------|
  |  Solo lectura                        | (0x01)  |
  |  Hidden                           | (0x02)  |
  |  Sistema                           | (0x04)  |
  |  Volumen                           | (0x08)  |
  |  Directorio                        | (0x10)  |
  |  Archivo                          | (0x20)  |
- Campo de información 4: sin usar.

### <a name="directory-attributes-set"></a>Definición de atributos de directorio 

#### <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set 

**Icono** ![Icono de definición de atributos](./media/user-guide/fx-events/image16.png)

**Descripción** 

Este evento representa un evento de definición de atributos de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3; asignación de bits de atributos:

  |  Atributo                        | Value        |
  |---------------------------------- | --------|
  |  Solo lectura                        | (0x01)  |
  |  Hidden                           | (0x02)  |
  |  Sistema                           | (0x04)  |
  |  Archivo                          | (0x20)  |
- Campo de información 4: sin usar.

### <a name="directory-create"></a>Creación de directorio 

#### <a name="fx_directory_create"></a>fx_directory_create

**Icono** ![Icono de creación de directorio](./media/user-guide/fx-events/image17.png)

**Descripción** 

Este evento representa un evento de creación de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-default-get"></a>Obtención predeterminada de directorio 

#### <a name="fx_directory_default_get"></a>fx_directory_default_get 

**Icono** ![Icono de obtención predeterminada de directorio](./media/user-guide/fx-events/image18.png)

**Descripción** 

Este evento representa un evento de definición predeterminada de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero a nombre de ruta de acceso de retorno.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-default-set"></a>Definición predeterminada de directorio 

#### <a name="fx_directory_default_set"></a>fx_directory_default_set 

**Icono** ![Icono de definición predeterminada de directorio](./media/user-guide/fx-events/image19.png)

**Descripción** 

Este evento representa un evento de definición predeterminada de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nuevo nombre de ruta de acceso predeterminado.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-delete"></a>Eliminación de directorio 

#### <a name="fx_directory_delete"></a>fx_directory_delete

**Icono** ![Icono de eliminación de directorio](./media/user-guide/fx-events/image20.png)

**Descripción** 

Este evento representa un evento de eliminación de directorio.

**Campos de información**
- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-first-entry-find"></a>Búsqueda de primera entrada de directorio 

#### <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

**Icono** ![Icono de búsqueda de primera entrada de directorio](./media/user-guide/fx-events/image21.png)

**Descripción** 

Este evento representa un evento de búsqueda de primera entrada de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-first-full-entry-find"></a>Búsqueda de primera entrada completa de directorio 

#### <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

**Icono** ![Icono de búsqueda de primera entrada completa de directorio](./media/user-guide/fx-events/image22.png)

**Descripción** 

Este evento representa un evento de búsqueda de primera entrada completa de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-information-get"></a>Obtención de información de directorio 

#### <a name="fx_directory_information_get"></a>fx_directory_information_get

**Icono** ![Icono de obtención de información de directorio](./media/user-guide/fx-events/image23.png)

**Descripción** 

Este evento representa un evento de obtención de información de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-local-path-clear"></a>Borrado de ruta de acceso local de directorio 

#### <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear

**Icono** ![Icono de borrado de ruta de acceso local de directorio](./media/user-guide/fx-events/image24.png)

**Descripción** 

Este evento representa un evento de borrado de ruta de acceso local de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="directory-local-path-get"></a>Obtención de ruta de acceso local de directorio 

#### <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get

**Icono** ![Icono de obtención de ruta de acceso local de directorio](./media/user-guide/fx-events/image25.png)

**Descripción** 

Este evento representa un evento de obtención de ruta de acceso local de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero a nombre de ruta de acceso de retorno.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-local-path-restore"></a>Restauración de ruta de acceso local de directorio 

#### <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore

**Icono** ![Icono de obtención de restauración de acceso local de directorio](./media/user-guide/fx-events/image26.png)

**Descripción** 

Este evento representa un evento de restauración de ruta de acceso local de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero a la estructura de ruta de acceso local.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-local-path-set"></a>Definición de ruta de acceso local de directorio 

#### <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

**Icono** ![Icono de definición de ruta de acceso local de directorio](./media/user-guide/fx-events/image27.png)

**Descripción** 

Este evento representa un evento de definición de ruta de acceso local de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero a la estructura de ruta de acceso local.
- Campo de información 3: puntero al nuevo nombre de ruta de acceso.
- Campo de información 4: sin usar.

### <a name="directory-long-name-get"></a>Obtención de nombre largo de directorio 

#### <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get

**Icono** ![Icono de obtención de nombre largo de directorio](./media/user-guide/fx-events/image28.png)

**Descripción** 

Este evento representa un evento de obtención de nombre largo de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre corto de archivo.
- Campo de información 3: puntero al nombre largo de archivo.
- Campo de información 4: sin usar.

### <a name="directory-name-test"></a>Prueba de nombre de directorio 

#### <a name="fx_directory_name_test"></a>fx_directory_name_test

**Icono** ![Icono de prueba de nombre de directorio](./media/user-guide/fx-events/image29.png)

**Descripción** 

Este evento representa un evento de prueba de nombre de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-next-entry-find"></a>Búsqueda de siguiente entrada de directorio 

#### <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find

**Icono** ![Icono de búsqueda de siguiente entrada de directorio](./media/user-guide/fx-events/image30.png)

**Descripción** 

Este evento representa un evento de búsqueda de siguiente entrada de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-next-full-entry-find"></a>Búsqueda de siguiente entrada completa de directorio 

#### <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find

**Icono** ![Icono de búsqueda de siguiente entrada completa de directorio](./media/user-guide/fx-events/image31.png)

**Descripción**

Este evento representa un evento de búsqueda de siguiente entrada completa de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del directorio.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="directory-rename"></a>Cambio de nombre de directorio 

#### <a name="fx_directory_rename-event"></a>fx_directory_rename_event

**Icono** ![Icono de cambio de nombre de directorio](./media/user-guide/fx-events/image32.png)

**Descripción**

Este evento representa un evento de cambio de nombre de directorio.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre antiguo de directorio.
- Campo de información 3: puntero al nombre nuevo de directorio.
- Campo de información 4: sin usar.

### <a name="directory-short-name-get"></a>Obtención de nombre corto de directorio 

#### <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get

**Icono** ![Icono de obtención de nombre corto de directorio](./media/user-guide/fx-events/image33.png)

**Descripción**

Este evento representa un evento de obtención de nombre corto de directorio.

**Campos de información** 

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre largo de archivo.
- Campo de información 3: puntero al nombre corto de archivo.
- Campo de información 4: sin usar.

### <a name="file-allocate"></a>Asignación de archivos 

#### <a name="fx_file_allocate"></a>fx_file_allocate

**Icono** ![Icono de asignación de archivos](./media/user-guide/fx-events/image34.png)

**Descripción**

Este evento representa un evento de asignación de archivos.

**Campos de información**

- Campo de información 1: puntero al archivo.
- Campo de información 2: tamaño solicitado.
- Campo de información 3: tamaño actual.
- Campo de información 4: nuevo tamaño.

### <a name="file-attributes-read"></a>Lectura de atributos de archivos 

#### <a name="fx_file_attributes_read"></a>fx_file_attributes_read

**Icono** ![Icono de lectura de atributos de archivo](./media/user-guide/fx-events/image35.png)

**Descripción**

Este evento representa un evento de lectura de atributos de archivo.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia. 
- Campo de información 2: asignación de bits de atributos:

  |  Atributo                         | Value        |
  |---------------------------------- | --------|
  |  Solo lectura                        | (0x01)  |
  |  Hidden                           | (0x02)  |
  |  Sistema                           | (0x04)  |
  |  Volumen                           | (0x08)  |
  |  Directorio                        | (0x10)  |
  |  Archivo                          | (0x20)  |
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="file-attributes-set"></a>Definición de atributos de archivo 

#### <a name="fx_file_attributes_set"></a>fx_file_attributes_set

**Icono** ![Icono de definición de atributos de archivo](./media/user-guide/fx-events/image36.png)

**Descripción** 

Este evento representa un evento de definición de atributos de archivo.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre de archivo. 
- Campo de información 3; asignación de bits de atributos:

  | Atributo                         | Value        |
  |---------------------------------- | --------|
  |  Solo lectura                        | (0x01)  |
  |  Hidden                           | (0x02)  |
  |  Sistema                           | (0x04)  |
  |  Archivo                          | (0x20)  |
- Campo de información 4: sin usar.

### <a name="file-best-effort-allocate"></a>Asignación de mejor esfuerzo de archivo 

#### <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

**Icono** ![Icono de asignación de mejor esfuerzo de archivo](./media/user-guide/fx-events/image37.png)

**Descripción** 

Este evento representa un evento de asignación de mejor esfuerzo de archivo.

**Campos de información**

- Campo de información 1: puntero al archivo.
- Campo de información 2: tamaño solicitado.
- Campo de información 3: tamaño real asignado.
- Campo de información 4: sin usar.

### <a name="file-close"></a>Cierre de archivo 

#### <a name="fx_file_close"></a>fx_file_close

**Icono** ![Icono de cierre de archivo](./media/user-guide/fx-events/image38.png)

**Descripción** 

Este evento representa un evento de cierre de archivo.

**Campos de información**

- Campo de información 1: puntero al archivo.
- Campo de información 2: tamaño del archivo.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="file-create"></a>Creación de archivo

#### <a name="fx_file_create"></a>fx_file_create

**Icono** ![Icono de creación de archivo](./media/user-guide/fx-events/image39.png)

**Descripción**

Este evento representa un evento de creación de archivo.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre de archivo.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="file-date-time-set"></a>Definición de fecha y hora de archivo 

#### <a name="fx_file_date_time_set"></a>fx_file_date_time_set

**Icono** ![Icono de definición de fecha y hora de archivo](./media/user-guide/fx-events/image40.png)

**Descripción**

Este evento representa un evento de definición de fecha y hora de archivo.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre de archivo.
- Campo de información 3: año.
- Campo de información 4: mes.

### <a name="file-delete"></a>Eliminación de archivo 

#### <a name="fx_file_delete"></a>fx_file_delete

**Icono** ![Icono de eliminación de archivo](./media/user-guide/fx-events/image41.png)

**Descripción**

Este evento representa un evento de eliminación de archivo.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre de archivo.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="file-open"></a>Apertura de archivo 

#### <a name="fx_file_open"></a>fx_file_open

**Icono** ![Icono de apertura de archivo](./media/user-guide/fx-events/image42.png)

**Descripción**

Este evento representa un evento de apertura de archivo.

**Campos de información** 

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al bloque de control de archivo.
- Campo de información 3: puntero al nombre de archivo.
- Campo de información 4; tipo abierto:

  |  Tipo de apertura                        | Value        |
  |---------------------------------- | --------|
  |  Apertura para lectura                    | (0x00)  |
  |  Apertura para escritura                   | (0x01)  |
  |  Apertura rápida para lectura               | (0x02)  |

### <a name="file-read"></a>Lectura de archivo 

#### <a name="fx_file_read"></a>fx_file_read

**Icono** ![Icono de lectura de archivo](./media/user-guide/fx-events/image43.png)

**Descripción**

Este evento representa un evento de lectura de archivo.

**Campos de información**

- Campo de información 1: puntero al archivo.
- Campo de información 2: puntero de búfer.
- Campo de información 3: tamaño de la solicitud.
- Campo de información 4: tamaño real leído.

### <a name="file-relative-seek"></a>Búsqueda relativa de archivo 

#### <a name="fx_file_relative_seek"></a>fx_file_relative_seek

**Icono** ![Icono de búsqueda relativa de archivo](./media/user-guide/fx-events/image44.png)

**Descripción**

Este evento representa un evento de búsqueda relativa de archivo.

**Campos de información**

- Campo de información 1: puntero al archivo.
- Campo de información 2: desplazamiento de bytes.
- Campo de información 3: buscar desde:

  | Evento                             | Value        |
  |---------------------------------- | --------|
  |  Desde el principio                   | (0x00)  |
  |  Desde el final                         | (0x01)  | 
  |  Adelante                          | (0x02)  |
  |  atrás                         | (0x03)  |
- Campo de información 4: desplazamiento anterior.

### <a name="file-rename"></a>Cambio de nombre de archivo 

#### <a name="fx_file_rename"></a>fx_file_rename

**Icono** ![Icono de cambio de nombre de archivo](./media/user-guide/fx-events/image45.png)

**Descripción**

Este evento representa un evento de cambio de nombre de archivo.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre de archivo antiguo.
- Campo de información 3: puntero al nombre de archivo nuevo.
- Campo de información 4: sin usar.

### <a name="file-seek"></a>Búsqueda de archivo 

#### <a name="fx_file_seek"></a>fx_file_seek

**Icono** ![Icono de búsqueda de archivo](./media/user-guide/fx-events/image46.png)

**Descripción**

Este evento representa un evento de búsqueda de archivo.

**Campos de información** 

- Campo de información 1: puntero al archivo.
- Campo de información 2: desplazamiento de bytes.
- Campo de información 3: desplazamiento anterior.
- Campo de información 4: sin usar.

### <a name="file-truncate"></a>Truncamiento de archivo 

#### <a name="fx_file_truncate"></a>fx_file_truncate

**Icono** ![Icono de truncamiento de archivo](./media/user-guide/fx-events/image47.png)

**Descripción**

Este evento representa un evento de truncamiento de archivo.

**Campos de información**

- Campo de información 1: puntero al archivo.
- Campo de información 2: tamaño solicitado.
- Campo de información 3: tamaño anterior.
- Campo de información 4: nuevo tamaño.

### <a name="file-truncate-release"></a>Versión de truncamiento de archivo 

#### <a name="fx_file_truncate_release"></a>fx_file_truncate_release 

**Icono** ![Icono de versión de truncamiento de archivo](./media/user-guide/fx-events/image48.png)

**Descripción**

Este evento representa un evento de versión de truncamiento de archivo.

**Campos de información**

- Campo de información 1: puntero al archivo.
- Campo de información 2: tamaño solicitado.
- Campo de información 3: tamaño anterior.
- Campo de información 4: nuevo tamaño.

### <a name="file-write"></a>Escritura de archivo 

#### <a name="fx_file_write"></a>fx_file_write 

**Icono** ![Icono de escritura de archivo](./media/user-guide/fx-events/image49.png)

**Descripción**

Este evento representa un evento de escritura de archivo.

**Campos de información**

- Campo de información 1: puntero al archivo.
- Campo de información 2: puntero de búfer.
- Campo de información 3: tamaño de la solicitud.
- Campo de información 4: tamaño real escrito.

### <a name="media-abort"></a>Anulación de elementos multimedia 

#### <a name="fx_media_abort"></a>fx_media_abort 

**Icono** ![Icono de anulación de elementos multimedia](./media/user-guide/fx-events/image50.png)

**Descripción**

Este evento representa un evento de anulación de elementos multimedia.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="media-cache-invalidate"></a>Invalidación de caché de elementos multimedia

#### <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

**Icono** ![Icono de invalidación de caché de elementos multimedia](./media/user-guide/fx-events/image51.png)

**Descripción**

Este evento representa un evento de invalidación de caché de elementos multimedia.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="media-check"></a>Comprobación de elementos multimedia 

#### <a name="fx_media_check"></a>fx_media_check

**Icono** ![Icono de comprobación de elementos multimedia](./media/user-guide/fx-events/image52.png)

**Descripción**

Este evento representa un evento de comprobación de elementos multimedia.

**Campos de información** 

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero de memoria de tachado.
- Campo de información 3: puntero de memoria de tachado.
- Campo de información 4: asignación de bits de errores:

  | Tipo de error                        | Value        |
  |---------------------------------- | --------|
  |  Error de cadena FAT                  | (0x01)  |
  |  Error de directorio                  | (0x02)  |
  |  Error de clúster perdido               | (0x04)  |
  |  Error de tamaño de archivo                  | (0x08)  |

### <a name="media-close"></a>Cierre de elementos multimedia 

#### <a name="fx_media_close"></a>fx_media_close

**Icono** ![Icono de cierre de elementos multimedia](./media/user-guide/fx-events/image53.png)

**Descripción**

Este evento representa un evento de cierre de elementos multimedia.

**Campos de información** 

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="media-flush"></a>Vaciado de elementos multimedia 

#### <a name="fx_media_flush"></a>fx_media_flush

**Icono** ![Icono de vaciado de elementos multimedia](./media/user-guide/fx-events/image54.png)

**Descripción**

Este evento representa un evento de vaciado de elementos multimedia.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sin usar.
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="media-format"></a>Formato de elementos multimedia 

#### <a name="fx_media_format"></a>fx_media_format

**Icono** ![Icono formato de elementos multimedia](./media/user-guide/fx-events/image55.png)

**Descripción**

Este evento representa un evento de formato de elementos multimedia.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: número de entradas raíz.
- Campo de información 3: sectores.
- Campo de información 4: sectores por clúster.

### <a name="media-open"></a>Elementos multimedia abiertos 

#### <a name="fx_media_open"></a>fx_media_open

**Icono** ![Icono de elementos multimedia abiertos](./media/user-guide/fx-events/image56.png)

**Descripción**

Este evento representa un evento de apertura de elementos multimedia.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero a la entrada del controlador de elementos multimedia.
- Campo de información 3: puntero de memoria.
- Campo de información 4: tamaño de memoria.

### <a name="media-read-media-read"></a>Lectura de elementos multimedia 

#### <a name="fx_media_read"></a>fx_media_read

**Icono** ![Icono de lectura de elementos multimedia](./media/user-guide/fx-events/image57.png)

**Descripción**

Este evento representa un evento de lectura de elementos multimedia.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sector lógico.
- Campo de información 3: puntero de búfer.
- Campo de información 4: bytes leídos.

### <a name="media-space-available"></a>Espacio de elementos multimedia disponible 

#### <a name="fx_media_space_available"></a>fx_media_space_available

**Icono** ![Icono de espacio de elementos multimedia disponible](./media/user-guide/fx-events/image58.png)

**Descripción**

Este evento representa un evento de espacio de elementos multimedia disponible.

**Campos de información** 

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero de bytes disponibles.
- Campo de información 3: número de clústeres libres.
- Campo de información 4: sin usar.

### <a name="media-volume-get"></a>Obtención de volumen de elementos multimedia 

#### <a name="fx_media_volume_get"></a>fx_media_volume_get

**Icono** ![Icono de obtención de volumen de elementos multimedia](./media/user-guide/fx-events/image59.png)

**Descripción**

Este evento representa un evento de obtención de volumen de elementos multimedia.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del volumen.
- Campo de información 3: origen de volumen.
- Campo de información 4: sin usar.

### <a name="media-volume-set"></a>Definición de volumen de elementos multimedia 

#### <a name="fx_media_volume_set"></a>fx_media_volume_set

**Icono** ![Icono de obtención de definición de volumen de elementos multimedia](./media/user-guide/fx-events/image60.png)

**Descripción**

Este evento representa un evento de definición de volumen de elementos multimedia.

**Campos de información** 
- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre del volumen.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="media-write"></a>Escritura de elementos multimedia 

#### <a name="fx_media_write"></a>fx_media_write

**Icono** ![Icono de escritura de elementos multimedia](./media/user-guide/fx-events/image61.png)

**Descripción**

Este evento representa un evento de escritura de elementos multimedia.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: sector lógico.
- Campo de información 3: puntero de búfer.
- Campo de información 4: bytes escritos.

### <a name="system-date-get"></a>Obtención de fecha del sistema 

#### <a name="fx_system_date_get"></a>fx_system_date_get 

**Icono** ![Icono de obtención de fecha del sistema](./media/user-guide/fx-events/image62.png)

**Descripción**

Este evento representa un evento de obtención de fecha del sistema.

**Campos de información**

- Campo de información 1: año.
- Campo de información 2: mes.
- Campo de información 3: día.
- Campo de información 4: sin usar.

### <a name="system-date-set"></a>Definición de fecha del sistema 

#### <a name="fx_system_date_set"></a>fx_system_date_set 

**Icono** ![Icono de definición de fecha del sistema](./media/user-guide/fx-events/image63.png)

**Descripción**

Este evento representa un evento de definición de fecha del sistema.

**Campos de información**

- Campo de información 1: año.
- Campo de información 2: mes.
- Campo de información 3: día.
- Campo de información 4: sin usar.

### <a name="system-initialize"></a>Inicialización del sistema 

#### <a name="fx_system_initialize"></a>fx_system_initialize 

**Icono** ![Icono de inicialización del sistema](./media/user-guide/fx-events/image64.png)

**Descripción**

Este evento representa un evento de inicialización del sistema.

**Campos de información**

- Campo de información 1: no se usa
- Campo de información 2: no se usa
- Campo de información 3: no se usa
- Campo de información 4: sin usar.

### <a name="system-time-get"></a>Obtención de hora del sistema 

#### <a name="fx_system_time_get"></a>fx_system_time_get 

**Icono** ![Icono de obtención de hora del sistema](./media/user-guide/fx-events/image65.png)

**Descripción**

Este evento representa un evento de obtención de hora del sistema.

**Campos de información** 

- Campo de información 1: hora.
- Campo de información 2: minuto.
- Campo de información 3: segundo.
- Campo de información 4: sin usar.

### <a name="system-time-set"></a>Definición de hora del sistema 

#### <a name="fx_system_time_set"></a>fx_system_time_set 

**Icono** ![Icono de definición de hora del sistema](./media/user-guide/fx-events/image66.png)

**Descripción**

Este evento representa un evento de definición de hora del sistema.

**Campos de información**

- Campo de información 1: hora.
- Campo de información 2: minuto.
- Campo de información 3: segundo.
- Campo de información 4: sin usar.

### <a name="unicode-directory-create"></a>Creación de directorio Unicode 

#### <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create 

**Icono** ![Icono de creación de directorio Unicode](./media/user-guide/fx-events/image67.png)

**Descripción**

Este evento representa un evento de creación de directorio Unicode.

**Campos de información** 

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero a nombre Unicode.
- Campo de información 3: tamaño del nombre Unicode.
- Campo de información 4: puntero al nombre corto.

### <a name="unicode-directory-rename"></a>Cambio de nombre de directorio Unicode 

#### <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

**Icono** ![Icono de cambio de nombre de directorio Unicode](./media/user-guide/fx-events/image68.png)

**Descripción**

Este evento representa un evento de cambio de nombre de directorio Unicode.

**Campos de información** 

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero a nombre Unicode.
- Campo de información 3: tamaño del nombre Unicode.
- Campo de información 4: puntero al nombre corto.

### <a name="unicode-file-create"></a>Creación de archivo Unicode 

#### <a name="fx_unicode_file_create"></a>fx_unicode_file_create

**Icono** ![Icono de creación de archivo Unicode](./media/user-guide/fx-events/image69.png)

**Descripción**

Este evento representa un evento de creación de archivo Unicode.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre Unicode.
- Campo de información 3: tamaño del nombre Unicode.
- Campo de información 4: puntero al nombre corto.

### <a name="unicode-file-rename"></a>Cambio de nombre de archivo Unicode 

#### <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

**Icono** ![Icono de cambio de nombre de archivo Unicode](./media/user-guide/fx-events/image70.png)

**Descripción**

Este evento representa un evento de cambio de nombre de archivo Unicode.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero a nombre Unicode.
- Campo de información 3: tamaño del nombre Unicode.
- Campo de información 4: puntero al nombre corto.

### <a name="unicode-length-get"></a>Obtención de longitud Unicode 

#### <a name="fx_unicode_length_get"></a>fx_unicode_length_get

**Icono** ![Icono de obtención de longitud Unicode](./media/user-guide/fx-events/image71.png)

**Descripción**

Este evento representa un evento de obtención de longitud Unicode.

**Campos de información**

- Campo de información 1: puntero al nombre Unicode.
- Campo de información 2: longitud.
- Campo de información 3: sin usar.
- Campo de información 4: sin usar.

### <a name="unicode-name-get"></a>Obtención de nombre Unicode 

#### <a name="fx_unicode_name_get"></a>fx_unicode_name_get

**Icono** ![Icono de obtención de nombre Unicode](./media/user-guide/fx-events/image72.png)

**Descripción**

Este evento representa un evento de obtención de nombre Unicode.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: nombre corto del origen.
- Campo de información 3: puntero de nombre Unicode de destino.
- Campo de información 4: longitud del nombre Unicode de destino.

### <a name="unicode-short-name-get"></a>Obtención de nombre corto Unicode 

#### <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

**Icono** ![Icono de obtención de nombre corto Unicode](./media/user-guide/fx-events/image73.png)

**Descripción**

Este evento representa un evento de obtención de nombre corto Unicode.

**Campos de información**

- Campo de información 1: puntero a los elementos multimedia.
- Campo de información 2: puntero al nombre Unicode de origen.
- Campo de información 3: longitud del nombre Unicode.
- Campo de información 4: puntero al nombre corto.