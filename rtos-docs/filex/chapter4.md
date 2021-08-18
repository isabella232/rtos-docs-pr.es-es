---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS FileX'
description: Este capítulo contiene una descripción de todos los servicios de Azure RTOS FileX en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 87b278c9b8642976fdab098636c518a3960f73cb906b4f1b28136a9a597a7a78
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783839"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a>Capítulo 4: Descripción de los servicios de Azure RTOS FileX

Este capítulo contiene una descripción de todos los servicios de Azure RTOS FileX en orden alfabético. Los nombres de los servicios están diseñados de modo que todos los servicios similares están agrupados.

## <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read

Lee los atributos de directorio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a>Descripción

Este servicio lee los atributos del directorio del medio especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **directory_name**: puntero al nombre del directorio solicitado (la ruta de acceso del directorio es opcional).
- **attributes** _ptr: puntero al destino de los atributos del directorio que se va a colocar. Los atributos de directorio se devuelven en un formato de mapa de bits con los siguientes valores posibles:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Lectura correcta de atributos de directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX _NOT FOUND** (0x04) El directorio especificado no se ha encontrado en el medio.
- **FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set

Establece los atributos de directorio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a>Descripción

Este servicio establece los atributos del directorio en los especificados por el autor de la llamada.

> [!WARNING]
> *Esta aplicación solo puede modificar un subconjunto de los atributos del directorio con este servicio. Cualquier intento de establecer atributos adicionales producirá un error.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **directory_name**: puntero al nombre del directorio solicitado (la ruta de acceso del directorio es opcional).
- **attributes**: los nuevos atributos de este directorio. Los atributos válidos de directorio se definen de la manera siguiente:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Establecimiento correcto de atributos de directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT FOUND** (0x04) El directorio especificado no se ha encontrado en el medio.
- **FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_INVALID_ATTR** (0x19) Se han seleccionado atributos no válidos.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_create"></a>fx_directory_create

Crea un subdirectorio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a>Descripción

Este servicio crea un subdirectorio en el directorio predeterminado actual o en la ruta de acceso proporcionada en el nombre de directorio. A diferencia del directorio raíz, los subdirectorios no tienen un límite en cuanto al número de archivos que pueden contener. El directorio raíz solo puede contener el número de entradas determinado por el registro de arranque.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **directory_name**: puntero al nombre del directorio que se va a crear (la ruta de acceso del directorio es opcional).

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Creación correcta de directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT FOUND** (0x04) El directorio especificado no se ha encontrado en el medio.
- **FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_INVALID_ATTR** (0x19) Se han seleccionado atributos no válidos.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_get"></a>fx_directory_default_get

Obtiene el último directorio predeterminado.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Descripción

Este servicio devuelve el puntero a la última ruta de acceso establecida por ***fx_directory_default_set***. Si no se ha establecido el directorio predeterminado o si el directorio predeterminado actual es el directorio raíz, se devuelve un valor de FX_NULL.

> [!IMPORTANT]
> *El tamaño predeterminado de la cadena de ruta de acceso interna es de 256 caracteres. Se puede cambiar modificando **FX_MAXIMUM_PATH** en **fx_api.h** y volviendo a generar toda la biblioteca FileX. Se mantiene la ruta de acceso de la cadena de caracteres para la aplicación y FileX no la usa internamente.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **return_path_name**: puntero al destino de la última cadena de directorio predeterminada. Se devuelve un valor de FX_NULL si la configuración actual del directorio predeterminado es la raíz. Cuando se abre el medio, la raíz es el valor predeterminado.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Obtención correcta del directorio predeterminado.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o destino.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_set"></a>fx_directory_default_set

Establece el directorio predeterminado.

### <a name="prototype"></a>Prototipo

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Descripción

Este servicio establece el directorio predeterminado del medio. Si se proporciona un valor de FX_NULL, el directorio predeterminado se establece en el directorio raíz del medio. Todas las operaciones de archivo posteriores que no especifiquen explícitamente una ruta de acceso tendrán este directorio como valor predeterminado.

> [!IMPORTANT]
> *El tamaño predeterminado de la cadena de ruta de acceso interna es de 256 caracteres. Se puede cambiar modificando **FX_MAXIMUM_PATH** en **fx_api.h** y volviendo a generar toda la biblioteca FileX. Se mantiene la ruta de acceso de la cadena de caracteres para la aplicación y FileX no la usa internamente.*

> [!IMPORTANT]
> *En el caso de los nombres proporcionados por la aplicación, FileX admite tanto los caracteres de barra diagonal inversa (\\) como los de barra diagonal (/) para separar los directorios, los subdirectorios y los nombres de archivo. Sin embargo, FileX solo usa el carácter de barra diagonal inversa en las rutas de acceso devueltas a la aplicación.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **new_path_name**: puntero al nuevo nombre de directorio predeterminado. Si se proporciona un valor de FX_NULL, el directorio predeterminado del medio se establece en el directorio raíz del medio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Establecimiento correcto del directorio predeterminado.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_INVALID_PATH** (0x0D) No se encontró el nuevo directorio.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_delete"></a>fx_directory_delete

Elimina el subdirectorio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Descripción

Este servicio elimina el directorio especificado. Tenga en cuenta que el directorio debe estar vacío para eliminarlo.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **directory_name**: puntero al nombre del directorio que se va a eliminar (la ruta de acceso del directorio es opcional).

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Eliminación correcta de directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT FOUND** (0x04) No se ha encontrado el directorio especificado.
- **FX_DIR_NOT_EMPTY** (0x10) El directorio especificado no está vacío.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.
- **FX_NOT_DIRECTORY** (0x0E) No es una entrada de directorio.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

Obtiene la primera entrada de directorio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Descripción

Este servicio recupera el nombre de la primera entrada en el directorio predeterminado y lo copia en el destino especificado.

> [!WARNING]
> *El destino especificado debe ser lo suficientemente grande como para contener el nombre de FileX de tamaño máximo, tal como se define en **FX_MAX_LONG_NAME_LEN.***

> [!WARNING]
> *Si usa una ruta de acceso no local, es importante para evitar (con un semáforo ThreadX, una exclusión mutua o un cambio de nivel de prioridad) que otros subprocesos de la aplicación cambien este directorio mientras se está llevando a cabo un cruce de directorio. De lo contrario, se pueden obtener resultados no válidos.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **return_entry_name**: puntero al destino del nombre de la primera entrada en el directorio predeterminado.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Búsqueda correcta de primera entrada de directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o destino.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

Obtiene la primera entrada de directorio con información completa.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **directory_name**: puntero al destino del nombre de una entrada de directorio. Debe ser al menos tan grande como FX_MAX_LONG_NAME_LEN.
- **attributes**: si no es nulo, puntero al destino de los atributos de la entrada que se va a colocar. Los atributos se devuelven en un formato de mapa de bits con los siguientes valores posibles:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **size**: si no es nulo, puntero al destino para el tamaño de la entrada en bytes.
- **year**: si no es nulo, puntero al destino del año de modificación de la entrada.
- **month**: si no es nulo, puntero al destino del mes de modificación de la entrada.
- **day**: si no es nulo, puntero al destino del día de modificación de la entrada.
- **hour**: si no es nulo, puntero al destino de la hora de modificación de la entrada.
- **minute**: si no es nulo, puntero al destino del minuto de modificación de la entrada.
- **second**: si no es nulo, puntero al destino del segundo de modificación de la entrada.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Búsqueda correcta de primera entrada de directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o destino.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_information_get"></a>fx_directory_information_get:

Obtiene la información de entrada de directorio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **directory_name**: puntero al nombre de la entrada de directorio.
- **attributes**: puntero al destino de los atributos.
- **size**: puntero al destino del tamaño.
- **year**: puntero al destino del año.
- **month**: puntero al destino del mes.
- **day**: puntero al destino del día.
- **hour**: puntero al destino de la hora.
- **minute**: puntero al destino del minuto.
- **second**: puntero al destino del segundo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Búsqueda correcta de primera entrada de directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT FOUND** (0x04) El directorio especificado no se ha encontrado en el medio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o destino.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear:

Borra la ruta de acceso local predeterminada.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Descripción

Este servicio borra la ruta de acceso local anterior configurada para el subproceso que realiza la llamada.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un medio abierto previamente.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Se ha borrado correctamente la ruta de acceso local.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto actualmente.
- **FX_NOT_IMPLEMENTED** (0x22) Se define FX_NO_LCOAL_PATH.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get:

Obtiene la cadena de ruta de acceso local actual.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Descripción

Este servicio devuelve el puntero de la ruta de acceso local del medio especificado. Si no hay ninguna ruta de acceso local establecida, se devuelve un valor NULL al autor de la llamada.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **return_path_name**: puntero al puntero de la cadena de destino para la cadena de ruta de acceso local que se va a almacenar.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Se ha obtenido correctamente la ruta de acceso local.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto actualmente.
- **FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.


### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore:

Restaura la ruta de acceso local anterior.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a>Descripción

Este servicio restaura una ruta de acceso local establecida previamente. También se restaura la posición de búsqueda de directorio realizada en esta ruta de acceso local, lo que hace que esta rutina resulte útil cuando la aplicación realiza cruces de directorio recursivos.

> [!IMPORTANT]
> *Cada ruta de acceso local contiene una cadena de ruta de acceso local del tamaño máximo de **FX_MAXIMUM_PATH**, que de forma predeterminada es de 256 caracteres. FileX no usa esta cadena de ruta de acceso interna y solo se proporciona para su uso por la aplicación. Si **FX_LOCAL_PATH** se va a declarar como una variable local, los usuarios deben tener cuidado del crecimiento de la pila por el tamaño de esta estructura. Los usuarios pueden reducir el tamaño de **FX_MAXIMUM_PATH** y volver a generar el origen de la biblioteca FileX.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **local_path_ptr**: puntero a la ruta de acceso local establecida previamente. Es muy importante asegurarse de que este puntero apunta a una ruta de acceso local que se ha usado anteriormente y que todavía está intacta.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Se ha restaurado correctamente la ruta de acceso local.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto actualmente.
- **FX_NOT_IMPLEMENTED** (0x22) Se define FX_NO_LCOAL_PATH.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o ruta de acceso local.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

Configura una ruta de acceso local específica de subproceso.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Descripción

Este servicio configura una ruta de acceso específica de subproceso según lo especificado por ***new_path_string** _. Después de completar esta rutina correctamente, la información de la ruta de acceso local almacenada en _ *_local_path_ptr_** tendrá prioridad sobre la ruta de acceso de medio global para todas las operaciones de archivos y directorios realizadas por este subproceso. Esto no tendrá ningún impacto en ningún otro subproceso del sistema. 
> [!IMPORTANT]
> *El tamaño predeterminado de la cadena de ruta de acceso local es de 256 caracteres. Se puede cambiar modificando **FX_MAXIMUM_PATH** en **fx_api.h** y volviendo a generar toda la biblioteca FileX. Se mantiene la ruta de acceso de la cadena de caracteres para la aplicación y FileX no la usa internamente.*

> [!IMPORTANT]
> *En el caso de los nombres proporcionados por la aplicación, FileX admite tanto los caracteres de barra diagonal inversa (\\) como los de barra diagonal (/) para separar los directorios, los subdirectorios y los nombres de archivo. Sin embargo, FileX solo usa el carácter de barra diagonal inversa en las rutas de acceso devueltas a la aplicación.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al medio abierto previamente.
- **local_path_ptr**: destino para retener la información de la ruta de acceso local específica de subproceso. La dirección de esta estructura se podrá proporcionar a la función de restauración de la ruta de acceso local en el futuro.
- **new_path_name**: especifica la ruta de acceso local para el programa de instalación.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Establecimiento correcto del directorio predeterminado.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_IMPLEMENTED** (0x22) **FX_NO_LCOAL_PATH
- **FX_INVALID_PATH** (0x0D) No se encontró el nuevo directorio.
- **FX_NOT_IMPLEMENTED** (0x22) Se define **FX_NO_LCOAL_PATH.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o ruta de acceso local.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get:

Obtiene el nombre largo del nombre corto.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a>Descripción

Este servicio recupera el nombre largo (si existe) asociado al nombre corto (formato 8.3) proporcionado. El nombre corto puede ser un nombre de archivo o un nombre de directorio.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **short_name**: puntero al nombre corto de origen (formato 8.3).
- **long_name**: puntero al destino del nombre largo. Si no hay ningún nombre largo, se devuelve el nombre corto. Tenga en cuenta que el destino del nombre largo debe ser lo suficientemente grande como para contener el número de caracteres de FX_MAX_LONG_NAME_LEN.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Obtención correcta de nombre largo.
- **FX_NOT_FOUND** (0x04) No se ha encontrado el nombre corto.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get_extended"></a>fx_directory_long_name_get_extended

Obtiene el nombre largo del nombre corto.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a>Descripción

Este servicio recupera el nombre largo (si existe) asociado al nombre corto (formato 8.3) proporcionado. El nombre corto puede ser un nombre de archivo o un nombre de directorio.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **short_name**: puntero al nombre corto de origen (formato 8.3).
- **long_name**: puntero al destino del nombre largo. Si no hay ningún nombre largo, se devuelve el nombre corto. Nota: El destino del nombre largo debe ser lo suficientemente grande como para contener el número de caracteres de **FX_MAX_LONG_NAME_LEN**.
- **long_file_name_buffer_length**: longitud del búfer de nombres largos.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Obtención correcta de nombre largo.
- **FX_NOT_FOUND** (0x04) No se ha encontrado el nombre corto.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name, sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_name_test"></a>fx_directory_name_test

Pruebas de directorio

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Descripción

Este servicio comprueba si el nombre proporcionado es un directorio o no. Si lo es, se devuelve FX_SUCCESS.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **directory_name**: puntero al nombre de la entrada de directorio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) El nombre proporcionado es un directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_FOUND** (0x04) La entrada de directorio no se ha podido encontrar.
- **FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find:

Recoge la siguiente entrada de directorio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Descripción

Este servicio devuelve el siguiente nombre de entrada del directorio predeterminado actual.

> [!WARNING]
> *Si usa una ruta de acceso no local, también es importante para evitar (con un semáforo ThreadX o un nivel de prioridad de subproceso) que otros subprocesos de la aplicación cambien este directorio mientras se está llevando a cabo un cruce de directorio. De lo contrario, se pueden obtener resultados no válidos.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **return_entry_name**: puntero al destino del nombre de la siguiente entrada en el directorio predeterminado. El búfer al que apunta este puntero debe ser lo suficientemente grande como para contener el tamaño máximo del nombre de FileX, definido por **_FX_MAX_LONG_NAME_LEN_**.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Búsqueda correcta de siguiente entrada.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find:

Obtiene la siguiente entrada de directorio con información completa.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a>Descripción

Este servicio recupera el nombre de la siguiente entrada del directorio predeterminado y lo copia en el destino especificado. También devuelve información completa sobre la entrada tal y como se especifica en los parámetros de entrada adicionales.

> [!WARNING]
> *El destino especificado debe ser lo suficientemente grande como para contener el nombre de FileX de tamaño máximo, tal como se define en ***FX_MAX_LONG_NAME_LEN****.

> [!WARNING]
> *Si usa una ruta de acceso no local, es importante para evitar (con un semáforo ThreadX, una exclusión mutua o un cambio de nivel de prioridad) que otros subprocesos de la aplicación cambien este directorio mientras se está llevando a cabo un cruce de directorio. De lo contrario, se pueden obtener resultados no válidos.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **directory_name**: puntero al destino del nombre de una entrada de directorio. Debe ser al menos tan grande como **FX_MAX_LONG_NAME_LEN**.
- **attributes**: si no es nulo, puntero al destino para los atributos de la entrada que se va a colocar. Los atributos se devuelven en un formato de mapa de bits con los siguientes valores posibles:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **size**: si no es nulo, puntero al destino para el tamaño de la entrada en bytes.
- **month**: si no es nulo, puntero al destino del mes de modificación de la entrada.
- **year**: si no es nulo, puntero al destino del año de modificación de la entrada.
- **day**: si no es nulo, puntero al destino del día de modificación de la entrada.
- **hour**: si no es nulo, puntero al destino de la hora de modificación de la entrada.
- **minute**: si no es nulo, puntero al destino del minuto de modificación de la entrada.
- **second**: si no es nulo, puntero al destino del segundo de modificación de la entrada.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Búsqueda correcta de siguiente directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o todos los parámetros de entrada son NULL.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_rename"></a>fx_directory_rename

Cambia el nombre del directorio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a>Descripción

Este servicio cambia el nombre del directorio por el nuevo nombre de directorio especificado. El cambio de nombre también se realiza en relación con la ruta de acceso especificada o la ruta de acceso predeterminada. Si se especifica una ruta de acceso en el nuevo nombre de directorio, el directorio cuyo nombre ha cambiado se mueve realmente a la ruta de acceso especificada. Si no se especifica ninguna ruta de acceso, el directorio cuyo nombre ha cambiado se coloca en la ruta de acceso predeterminada actual.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **old_directory_name**: puntero al nombre de directorio actual.
- **new_directory_name**: puntero al nuevo nombre de directorio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Cambio correcto de nombre de directorio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_FOUND** (0x04) La entrada de directorio no se ha podido encontrar.
- **FX_NOT_DIRECTORY** (0x0E) La entrada no es un directorio.
- **FX_INVALID_NAME** (0x0C) El nuevo nombre de directorio no es válido.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en este directorio.
- **FX_INVALID_PATH** (0x0D) Ruta de acceso no válida proporcionada con el nombre de directorio.
- **FX_ALREADY_CREATED** (0x0B) El directorio especificado ya se había creado.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get:

Obtiene el nombre corto de un nombre largo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a>Descripción

Este servicio recupera el nombre corto (formato 8.3) asociado al nombre largo proporcionado. El nombre largo puede ser un nombre de archivo o un nombre de directorio.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **long_name**: puntero al nombre largo de origen.
- **short_name**: puntero al nombre corto de destino (formato 8.3). Tenga en cuenta que el destino del nombre corto debe ser lo suficientemente grande como para contener 14 caracteres.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Obtención correcta de nombre corto.
- **FX_NOT_FOUND** (0x04) No se ha encontrado el nombre largo.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get_extended"></a>fx_directory_short_name_get_extended

Obtiene el nombre corto de un nombre largo.

### <a name="prototype"></a>Prototipo

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a>Descripción

Este servicio recupera el nombre corto (formato 8.3) asociado al nombre largo proporcionado. El nombre largo puede ser un nombre de archivo o un nombre de directorio.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **long_name**: puntero al nombre largo de origen.
- **short_name**: puntero al nombre corto de destino (formato 8.3). Nota: El destino del nombre corto debe ser lo suficientemente grande como para contener 14 caracteres.
- **short_file_name_length**: longitud del búfer de nombre corto.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Obtención correcta de nombre corto.
- **FX_NOT_FOUND** (0x04) No se ha encontrado el nombre largo.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_fault_tolerant_enable"></a>fx_fault_tolerant_enable

Habilita el servicio de tolerancia a errores.

### <a name="prototype"></a>Prototipo

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a>Descripción

Este servicio habilita el módulo de tolerancia a errores. Al iniciarse, el módulo de tolerancia a errores detecta si el sistema de archivos está bajo la protección de la tolerancia a errores de FileX. Si no es así, el servicio busca los sectores disponibles en el sistema de archivos para almacenar los registros en las transacciones del sistema de archivos. Si el sistema de archivos se encuentra bajo la protección de la tolerancia a errores de FileX, aplica los registros al sistema de archivos para mantener su integridad.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **memory_ptr**: puntero a un bloque de memoria utilizado por el módulo de tolerancia a errores como memoria temporal.
- **memory_size**: tamaño de la memoria temporal. Para que la tolerancia a errores funcione correctamente, el tamaño de la memoria temporal debe ser de al menos 3072 bytes, y debe ser un múltiplo del tamaño del sector.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Habilitación correcta de la tolerancia a errores.
- **FX_NOT_ENOUGH_MEMORY** (0x91) Tamaño de memoria demasiado pequeño.
- **FX_BOOT_ERROR** (0x01) Error del sector de arranque.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más clústeres libres disponibles.
- **FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.
- **FX_SECTOR_INVALID** (0x89) El sector no es válido.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a>Consulte también

- fx_system_initialize
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write

## <a name="fx_file_allocate"></a>fx_file_allocate

Asigna espacio para un archivo.

### <a name="prototype"></a>Prototipo

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a>Descripción

Este servicio asigna y vincula uno o más clústeres contiguos al final del archivo especificado. FileX determina el número de clústeres necesarios dividiendo el tamaño solicitado por el número de bytes por clúster. Después, el resultado se redondea al siguiente clúster completo.

Para asignar espacio más allá de 4 GB, la aplicación debe usar el servicio *fx_file_extended_allocate*.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero a un archivo abierto previamente.
- **size**: número de bytes que se asignan al archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Asignación correcta de archivo.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.
- **FX_FAT_READ_ERROR** (0x03) No se ha podido leer la entrada FAT.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más clústeres libres disponibles.
- **FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.
- **FX_SECTOR_INVALID** (0x89) El sector no es válido.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a>Consulte también

- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open- fx_file_read
- fx_file_relative_seek
- fx_file_rename- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_read"></a>fx_file_attributes_read

Lee atributos de archivo.

### <a name="prototype"></a>Prototipo

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a>Descripción

Este servicio lee los atributos del archivo del medio especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **file_name**: puntero al nombre del archivo solicitado (la ruta de acceso del directorio es opcional).
- **attributes_ptr**: puntero al destino de los atributos del archivo que se va a colocar. Los atributos del archivo se devuelven en un formato de mapa de bits con los siguientes valores posibles:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Lectura correcta del atributo.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT FOUND** (0x04) El archivo especificado no se ha encontrado en el medio.
- **FX_NOT_A_FILE** (0x05) El archivo especificado es un directorio.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o atributos.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_set"></a>fx_file_attributes_set

Establece atributos de archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a>Descripción

Este servicio establece los atributos del archivo en los especificados por el autor de la llamada.

> [!WARNING]
> *La aplicación solo puede modificar un subconjunto de los atributos del archivo con este servicio. Cualquier intento de establecer atributos adicionales producirá un error.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **file_name**: puntero al nombre del archivo solicitado** (la ruta de acceso del directorio es opcional).
- **attributes**: nuevos atributos del archivo. Los atributos de archivo válidos se definen de la manera siguiente:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Establecimiento correcto del atributo.
- **FX_ACCESS_ERROR** (0x06) El archivo está abierto y sus atributos no se pueden establecer.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas en la tabla FAT o en la asignación de clúster de exFAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_NOT FOUND** (0x04) El archivo especificado no se ha encontrado en el medio.
- **FX_NOT_A_FILE** (0x05) El archivo especificado es un directorio.
- **FX_SECTOR_INVALID** (0x89) El sector no es válido.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_INVALID_ATTR** (0x19) Se han seleccionado atributos no válidos.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

Mejor esfuerzo para asignar espacio para un archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a>Descripción

Este servicio asigna y vincula uno o más clústeres contiguos al final del archivo especificado. FileX determina el número de clústeres necesarios dividiendo el tamaño solicitado por el número de bytes por clúster. Después, el resultado se redondea al siguiente clúster completo. Si no hay suficientes clústeres consecutivos disponibles en el medio, este servicio vincula el bloque más grande disponible de clústeres consecutivos al archivo. La cantidad de espacio realmente asignado al archivo se devuelve al autor de la llamada.

Para asignar espacio más allá de 4 GB, la aplicación debe usar el servicio *fx_file_extended_best_effort_allocate*.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero a un archivo abierto previamente.
- **size**: número de bytes que se asignan al archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Asignación correcta de mejor esfuerzo de archivo.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.
- **FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero o destino no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_close"></a>fx_file_close

Cierra el archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a>Descripción

Este servicio cierra el archivo especificado. Si el archivo estaba abierto para escritura y se ha modificado, este servicio completa el proceso de modificación del archivo actualizando su entrada de directorio con el nuevo tamaño y la fecha y hora actuales del sistema.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero a un archivo abierto previamente.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Cierre correcto de archivo.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o atributos.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_create"></a>fx_file_create

Crea un archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a>Descripción

Este servicio crea el archivo especificado en el directorio predeterminado o en la ruta de acceso al directorio suministrada con el nombre de archivo.

> [!WARNING]
> *Este servicio crea un archivo de longitud cero, es decir, sin clústeres asignados. La asignación se realizará automáticamente en las escrituras de archivos posteriores o se puede realizar por adelantado con el servicio fx_file_allocate o fx_file_extended_allocate para un espacio más allá de 4 GB).*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **file_name**: puntero al nombre del archivo que se va a crear (la ruta de acceso del directorio es opcional).

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Creación correcta de archivo.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_ALREADY_CREATED** (0x0B) El archivo especificado ya se había creado.
- **FX_NO_MORE_SPACE** (0x0A) No hay más entradas en el directorio raíz o no hay más clústeres disponibles.
- **FX_INVALID_PATH** (0x0D) Ruta de acceso no válida proporcionada con el nombre de archivo.
- **FX_INVALID_NAME** (0x0C) El nombre de archivo no es válido.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio subyacente está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a>Consulte también
- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_date_time_set"></a>fx_file_date_time_set

### <a name="sets-file-date-and-time"></a>Establece la fecha y la hora del archivo

Establecimiento de la fecha y la hora del archivo

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a>Descripción

Este servicio establece la fecha y hora del archivo especificado.

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **file_name**: puntero al nombre del archivo.
- **year**: valor del año (de 1980 a 2107 inclusive).
- **month**: valor del mes (de 1 a 12 inclusive).
- **day**: valor del día (de 1 a 31 inclusive).
- **hour**: valor de la hora (de 0 a 23 inclusive).
- **minute**: valor del minuto (de 0 a 59 inclusive).
- **second**: valor del segundo (de 0 a 59 inclusive).

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Establecimiento correcto de fecha y hora.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_FOUND** (0x04) No se ha encontrado el archivo.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.
- **FX_INVALID_YEAR** (0x12) El año no es válido.
- **FX_INVALID_MONTH** (0x13) El mes no es válido.
- **FX_INVALID_DAY** (0x14) El día no es válido.
- **FX_INVALID_HOUR** (0x15) La hora no es válida.
- **FX_INVALID_MINUTE** (0x16) El minuto no es válido.
- **FX_INVALID_SECOND** (0x17) El segundo no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_delete"></a>fx_file_delete

### <a name="deletes-file"></a>Elimina el archivo

Eliminación de un archivo

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a>Descripción

Este servicio elimina el archivo especificado.


### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **file_name**: puntero al nombre del archivo que se va a eliminar (la ruta de acceso del directorio es opcional).

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Eliminación correcta de archivo.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT FOUND** (0x04) No se ha encontrado el archivo especificado.
- **FX_NOT_A_FILE** (0x05) El nombre de archivo especificado era un directorio o un volumen.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado está abierto actualmente.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_allocate"></a>fx_file_extended_allocate

Asigna espacio para un archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a>Descripción

Este servicio asigna y vincula uno o más clústeres contiguos al final del archivo especificado. FileX determina el número de clústeres necesarios dividiendo el tamaño solicitado por el número de bytes por clúster. Después, el resultado se redondea al siguiente clúster completo.

Este servicio está diseñado para exFAT. El parámetro *size* toma un valor entero de 64 bits, lo que permite que el autor de la llamada preasigne espacio más allá del intervalo de 4 GB.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero a un archivo abierto previamente.
- **size**: número de bytes que se asignan al archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Asignación correcta de archivo.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.
- **FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_best_effort_allocate"></a>fx_file_extended_best_effort_allocate

Mejor esfuerzo para asignar espacio para un archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a>Descripción

Este servicio asigna y vincula uno o más clústeres contiguos al final del archivo especificado. FileX determina el número de clústeres necesarios dividiendo el tamaño solicitado por el número de bytes por clúster. Después, el resultado se redondea al siguiente clúster completo. Si no hay suficientes clústeres consecutivos disponibles en el medio, este servicio vincula el bloque más grande disponible de clústeres consecutivos al archivo. La cantidad de espacio realmente asignado al archivo se devuelve al autor de la llamada.

Este servicio está diseñado para exFAT. El parámetro *size* toma un valor entero de 64 bits, lo que permite que el autor de la llamada preasigne espacio más allá del intervalo de 4 GB.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero a un archivo abierto previamente.
- **size**: número de bytes que se asignan al archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Asignación correcta de archivo.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.
- **FX_NO_MORE_SPACE** (0x0A) El medio asociado con este archivo no tiene suficientes clústeres disponibles.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_relative_seek"></a>fx_file_extended_relative_seek

Posiciona en un desplazamiento de bytes relativo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Descripción

Este servicio posiciona el puntero de lectura y escritura de archivo interno en el desplazamiento de bytes relativo especificado. Cualquier solicitud de lectura o escritura de archivo subsiguiente comenzará en esta ubicación del archivo.

Este servicio está diseñado para exFAT. El parámetro *byte_offset* toma un valor entero de 64 bits, lo que permite al autor de la llamada volver a posicionar el puntero de lectura y escritura más allá del intervalo de 4 GB.

> [!IMPORTANT]
> *Si la operación de búsqueda intenta buscar más allá del final del archivo, el puntero de lectura y escritura del archivo se posiciona al final del archivo. Por el contrario, si la operación de búsqueda intenta posicionarse antes del principio del archivo, el puntero de lectura y escritura del archivo se posiciona al principio del archivo.*

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero a un archivo abierto previamente.
- **byte_offset**: desplazamiento de bytes relativo deseado en el archivo.
- **seek_from**: la dirección y la ubicación desde donde se realizará la búsqueda relativa. Las opciones de búsqueda válidas son las siguientes:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03) Si se especifica FX_SEEK_BEGIN, la operación de búsqueda se realiza desde el principio del archivo. Si se especifica FX_SEEK_END, la operación de búsqueda se realiza hacia atrás desde el final del archivo. Si se especifica FX_SEEK_FORWARD, la operación de búsqueda se realiza hacia delante desde la posición actual del archivo. Si se especifica FX_SEEK_BACK, la operación de búsqueda se realiza hacia atrás desde la posición actual del archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Búsqueda relativa de archivo correcta.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_seek"></a>fx_file_extended_seek

Posiciona en el desplazamiento de bytes.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a>Descripción

Este servicio posiciona el puntero de lectura y escritura de archivo interno en el desplazamiento de bytes especificado. Cualquier solicitud de lectura o escritura de archivo subsiguiente comenzará en esta ubicación del archivo.

Este servicio está diseñado para exFAT. El parámetro *byte_offset* toma un valor entero de 64 bits, lo que permite al autor de la llamada volver a posicionar el puntero de lectura y escritura más allá del intervalo de 4 GB.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero al bloque de control de archivo.
- **byte_offset**: desplazamiento de bytes deseado en el archivo. Un valor cero posicionará el puntero de lectura y escritura al principio del archivo, mientras que un valor mayor que el tamaño del archivo posicionará el puntero de lectura y escritura al final del archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Búsqueda correcta de archivo.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate"></a>fx_file_extended_truncate

Trunca el archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a>Descripción

Este servicio trunca el tamaño del archivo al tamaño especificado. Si el tamaño proporcionado es mayor que el tamaño real del archivo, este servicio no hace nada. No se libera ninguno de los clústeres de medios asociados con el archivo.

> [!WARNING]
> *Tenga cuidado al truncar archivos que también pueden estar abiertos para lectura al mismo tiempo. El truncamiento de un archivo abierto también para lectura puede dar lugar a lectura de datos no válidos.*

Este servicio está diseñado para exFAT. El parámetro *size* toma un valor entero de 64 bits, lo que permite que el autor de la llamada opere más allá del intervalo de 4 GB.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero al bloque de control de archivo.
- **size**: nuevo tamaño de archivo. Se descartan los bytes más allá de este nuevo tamaño de archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Truncamiento correcto de archivo.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio subyacente está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate_release"></a>fx_file_extended_truncate_release

Trunca el archivo y libera los clústeres.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a>Descripción

Este servicio trunca el tamaño del archivo al tamaño especificado. Si el tamaño proporcionado es mayor que el tamaño real del archivo, este servicio no hace nada. A diferencia del servicio ***fx_file_extended_truncate***, este servicio libera todos los clústeres no utilizados.

> [!WARNING]
> *Tenga cuidado al truncar archivos que también pueden estar abiertos para lectura al mismo tiempo. El truncamiento de un archivo abierto también para lectura puede dar lugar a lectura de datos no válidos.*

Este servicio está diseñado para exFAT. El parámetro *size* toma un valor entero de 64 bits, lo que permite que el autor de la llamada opere más allá del intervalo de 4 GB.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero a un archivo abierto previamente.
- **size**: nuevo tamaño de archivo. Se descartan los bytes más allá de este nuevo tamaño de archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Truncamiento correcto de archivo.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_open"></a>fx_file_open

Abre el archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a>Descripción

Este servicio abre el archivo especificado para lectura o escritura. Se puede abrir un archivo para lectura varias veces, mientras que un archivo solo se puede abrir para escritura una vez hasta que el escritor cierre el archivo.

> [!IMPORTANT]
> *Se debe tener cuidado si un archivo se abre simultáneamente para lectura y escritura. Puede que el lector no vea la escritura de archivo realizada cuando un archivo se abre al mismo tiempo para la lectura, a menos que el lector cierre y vuelva a abrir el archivo. Del mismo modo, el escritor del archivo debe tener cuidado al usar los servicios de truncamiento de archivo. Si el escritor trunca un archivo, los lectores del mismo archivo podrían devolver datos no válidos.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **file_ptr**: puntero al bloque de control de archivo.
- **file_name**: puntero al nombre del archivo que se va a abrir (la ruta de acceso del directorio es opcional).
- **open_type**: tipo de archivo abierto. Las opciones válidas de tipo de apertura son:
  - FX_OPEN_FOR_READ (0x00)
  - FX_OPEN_FOR_WRITE (0x01)
  - FX_OPEN_FOR_READ_FAST (0x02)

Abrir archivos con FX_OPEN_FOR_READ y FX_OPEN_FOR_READ_FAST es similar:

- FX_OPEN_FOR_READ incluye la comprobación de que la lista vinculada de clústeres que componen el archivo está intacta y FX_OPEN_FOR_READ_FAST no realiza esta comprobación, lo que hace que sea más rápida.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Apertura correcta de archivo.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT FOUND** (0x04) No se ha encontrado el archivo especificado.
- **FX_NOT_A_FILE** (0x05) El nombre de archivo especificado era un directorio o un volumen.
- **FX_FILE_CORRUPT** (0x08) El archivo especificado está dañado y la apertura generó un error.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado ya está abierto o el tipo de apertura no es válido.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_MEDIA_INVALID** (0x02) Medio no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio subyacente está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_read"></a>fx_file_read

Lee bytes del archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a>Descripción

Este servicio lee bytes del archivo y los almacena en el búfer proporcionado. Una vez completada la lectura, el puntero de lectura interno del archivo se ajusta para que apunte al siguiente byte del archivo. Si quedan menos bytes en la solicitud, solo los bytes restantes se almacenan en el búfer. En cualquier caso, el número total de bytes colocados en el búfer se devuelve al autor de la llamada.

> [!WARNING]
> *La aplicación debe asegurarse de que el búfer proporcionado pueda almacenar el número especificado de bytes solicitados.*

> [!WARNING]
> *Se consigue un rendimiento más rápido si el búfer de destino se encuentra en un límite de palabra larga y el tamaño solicitado es divisible en partes iguales por sizeof(**ULONG**).*

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero al bloque de control de archivo.
- **buffer_ptr**: puntero al búfer de destino para la lectura.
- **request_size**: número máximo de bytes que se van a leer.
- **actual_size**: puntero a la variable que va a contener el número real de bytes leídos en el búfer proporcionado.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Lectura correcta de archivo.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.
- **FX_FILE_CORRUPT** (0x08) El archivo especificado está dañado y la lectura generó un error.
- **FX_END_OF_FILE** (0x09) Se ha alcanzado el final del archivo.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de búfer o archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a>Consulte también

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_relative_seek"></a>fx_file_relative_seek

Posiciona en un desplazamiento de bytes relativo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Descripción

Este servicio posiciona el puntero de lectura y escritura de archivo interno en el desplazamiento de bytes relativo especificado. Cualquier solicitud de lectura o escritura de archivo subsiguiente comenzará en esta ubicación del archivo.

> [!IMPORTANT]
> *Si la operación de búsqueda intenta buscar más allá del final del archivo, el puntero de lectura y escritura del archivo se posiciona al final del archivo. Por el contrario, si la operación de búsqueda intenta posicionarse antes del principio del archivo, el puntero de lectura y escritura del archivo se posiciona al principio del archivo.*

Para buscar con un valor de desplazamiento más allá de 4 GB, la aplicación debe usar el servicio *fx_file_extended_relative_seek*.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero a un archivo abierto previamente.
- **byte_offset**: desplazamiento de bytes relativo deseado en el archivo.
- **seek_from**: la dirección y la ubicación desde donde se realizará la búsqueda relativa. Las opciones de búsqueda válidas son las siguientes:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03)

Si se especifica FX_SEEK_BEGIN, la operación de búsqueda se realiza desde el principio del archivo. Si se especifica FX_SEEK_END, la operación de búsqueda se realiza hacia atrás desde el final del archivo. Si se especifica FX_SEEK_FORWARD, la operación de búsqueda se realiza hacia delante desde la posición actual del archivo. Si se especifica FX_SEEK_BACK, la operación de búsqueda se realiza hacia atrás desde la posición actual del archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Búsqueda relativa de archivo correcta.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_rename"></a>fx_file_rename

Cambia el nombre de archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a>Descripción

Este servicio cambia el nombre del archivo especificado por *old_file_name*. El cambio de nombre también se realiza en relación con la ruta de acceso especificada o la ruta de acceso predeterminada. Si se especifica una ruta de acceso en el nuevo nombre de archivo, el archivo cuyo nombre ha cambiado se mueve realmente a la ruta de acceso especificada. Si no se especifica ninguna ruta de acceso, el archivo cuyo nombre ha cambiado se coloca en la ruta de acceso predeterminada actual.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un bloque de control de medio.
- **old_file_name**: puntero al nombre del archivo cuyo nombre se va a cambiar (la ruta de acceso del directorio es opcional).
- **new_file_name**: puntero al nuevo nombre de archivo. No se permite la ruta de acceso al directorio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Cambio correcto de nombre de archivo.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT FOUND** (0x04) No se ha encontrado el archivo especificado.
- **FX_NOT_A_FILE** (0x05) El archivo especificado es un directorio.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado ya está abierto.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_INVALID_NAME** (0x0C) El nuevo nombre de archivo especificado no es un nombre de archivo válido.
- **FX_INVALID_PATH** (0x0D) La ruta de acceso no es válida.
- **FX_ALREADY_CREATED** (0x0B) Se utiliza el nuevo nombre de archivo.
- **FX_MEDIA_INVALID** (0x02) El medio no es válido.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_seek"></a>fx_file_seek

Posiciona en el desplazamiento de bytes.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a>Descripción

Este servicio posiciona el puntero de lectura y escritura de archivo interno en el desplazamiento de bytes especificado. Cualquier solicitud de lectura o escritura de archivo subsiguiente comenzará en esta ubicación del archivo.

Para buscar con un valor de desplazamiento más allá de 4 GB, la aplicación debe usar el servicio *fx_file_extended_seek*.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero al bloque de control de archivo.
- **byte_offset**: desplazamiento de bytes deseado en el archivo. Un valor cero posicionará el puntero de lectura y escritura al principio del archivo, mientras que un valor mayor que el tamaño del archivo posicionará el puntero de lectura y escritura al final del archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Búsqueda correcta de archivo.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate"></a>fx_file_truncate

Trunca el archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a>Descripción

Este servicio trunca el tamaño del archivo al tamaño especificado. Si el tamaño proporcionado es mayor que el tamaño real del archivo, este servicio no hace nada. No se libera ninguno de los clústeres de medios asociados con el archivo.

> [!WARNING]
> *Tenga cuidado al truncar archivos que también pueden estar abiertos para lectura al mismo tiempo. El truncamiento de un archivo abierto también para lectura puede dar lugar a lectura de datos no válidos.*

Para operar más allá de los 4 GB, la aplicación debe usar el servicio *fx_file_extended_truncate*.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero al bloque de control de archivo.
- **size**: nuevo tamaño de archivo. Se descartan los bytes más allá de este nuevo tamaño de archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Truncamiento correcto de archivo.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate_release"></a>fx_file_truncate_release

Trunca el archivo y libera los clústeres.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a>Descripción

Este servicio trunca el tamaño del archivo al tamaño especificado. Si el tamaño proporcionado es mayor que el tamaño real del archivo, este servicio no hace nada. A diferencia del servicio ***fx_file_truncate***, este servicio libera todos los clústeres no utilizados.

> [!WARNING]
> *Tenga cuidado al truncar archivos que también pueden estar abiertos para lectura al mismo tiempo. El truncamiento de un archivo abierto también para lectura puede dar lugar a lectura de datos no válidos.*

Para operar más allá de los 4 GB, la aplicación debe usar el servicio *fx_file_extended_release*.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero a un archivo abierto previamente.
- **size**: nuevo tamaño de archivo. Se descartan los bytes más allá de este nuevo tamaño de archivo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Truncamiento correcto de archivo.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto actualmente.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio subyacente está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio para completar la operación.
- **FX_PTR_ERROR** (0x18) Puntero no válido de archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_write"></a>fx_file_write

Escribe bytes en el archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a>Descripción

Este servicio escribe bytes del búfer especificado a partir de la posición actual del archivo. Una vez completada la escritura, el puntero de lectura interno del archivo se ajusta para que apunte al siguiente byte del archivo.

> [!WARNING]
> *Se consigue un rendimiento más rápido si el búfer de origen se encuentra en un límite de palabra larga y el tamaño solicitado es divisible en partes iguales por sizeof(**ULONG**).*

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero al bloque de control de archivo.
- **buffer_ptr**: puntero al búfer de origen para la escritura.
- **size**: número de bytes para escribir.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Escritura correcta de archivo.
- **FX_NOT_OPEN** (0x07) El archivo especificado no está abierto.
- **FX_ACCESS_ERROR** (0x06) El archivo especificado no está abierto para escritura.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio disponible en los medios para realizar esta escritura.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la entrada FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) No hay más entradas FAT.
- **FX_PTR_ERROR** (0x18) Puntero no válido de búfer o archivo.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_read,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_write_notify_set"></a>fx_file_write_notify_set

Establece la función de notificación de escritura de archivo.

### <a name="prototype"></a>Prototipo

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a>Descripción

Este servicio instala la función de devolución de llamada que se invoca después de una operación de escritura de archivo correcta.

### <a name="input-parameters"></a>Parámetros de entrada

- **file_ptr**: puntero al bloque de control de archivo.
- **file_write_notify**: función de devolución de llamada de escritura de archivo que se va a instalar. Establezca la función de devolución de llamada en NULL para deshabilitarla.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) La función de devolución de llamada se ha instalado correctamente.
- **FX_PTR_ERROR** (0x18) file_ptr es NULL.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_media_abort"></a>fx_media_abort

Anula las actividades de los medios.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Descripción

Este servicio anula todas las actividades actuales asociadas a los medios, incluido el cierre de todos los archivos abiertos, el envío de una solicitud de anulación al controlador asociado y la colocación de los medios en un estado anulado. Normalmente, se llama a este servicio cuando se detectan errores de E/S.

> [!WARNING]
> *El medio debe volverse a abrir para poder usarlo de nuevo después de realizar una operación de anulación.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Anulación correcta del medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

Invalida la caché del sector lógico.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Descripción

Este servicio vacía todos los sectores sucios de la memoria caché y, a continuación, invalida toda la caché del sector lógico.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Invalidación correcta de caché de medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o memoria temporal.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_check"></a>fx_media_check

Comprueba si hay errores en los medios.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a>Descripción

Este servicio comprueba los medios especificados en busca de errores estructurales básicos, como la vinculación cruzada de archivos o directorios, cadenas FAT no válidas y clústeres perdidos. Este servicio también proporciona la capacidad de corregir los errores detectados.

El servicio fx_media_check requiere memoria temporal para el análisis del equilibrio de carga en profundidad de los directorios y archivos del medio. En concreto, la memoria temporal que se proporciona al servicio de comprobación de medios debe ser lo suficientemente grande como para contener varias entradas de directorio, una estructura de datos para "apilar" la posición de la entrada de directorio actual antes de entrar en los subdirectorios y, por último, el mapa de bits de FAT lógica. La memoria temporal debe ser al menos de 512 a 1024 bytes más la memoria para el mapa de bits de FAT lógica, que requiere tantos bits como clústeres haya en el medio. Por ejemplo, un dispositivo con 8000 clústeres requiere 1000 bytes para representarse y, por tanto, requiere un área temporal total del orden de los 2048 bytes.

> [!WARNING]
> *Solo se debe llamar a este servicio inmediatamente después de fx_media_open y sin ninguna otra actividad del sistema de archivos.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **scratch_memory_ptr**: puntero al principio de la memoria temporal.
- **scratch_memory_size**: tamaño de la memoria temporal en bytes.
- **error_correction_option**: bits de opción de corrección de errores, cuando se establece el bit, se realiza la corrección de errores. Los bits de la opción de corrección de errores se definen de la siguiente manera:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02)
  - FX_LOST_CLUSTER_ERROR (0x04) Simplemente se combinan mediante OR las opciones de corrección de errores necesarias. Si no se requiere ninguna corrección de errores, se debe proporcionar el valor 0.
- **errors_detected_ptr**: destino de los bits de detección de errores, tal y como se define a continuación:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)
  - FX_FILE_SIZE_ERROR (0x08)

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Comprobación correcta del medio, vea el destino de los errores detectados para obtener más información.
- **FX_ACCESS_ERROR** (0x06) No puede realizar una comprobación con archivos abiertos.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NO_MORE_SPACE** (0x0A) No hay más espacio en el medio.
- **FX_NOT_ENOUGH_MEMORY** (0x91) La memoria temporal proporcionada no es lo suficientemente grande.
- **FX_ERROR_NOT_FIXED** (0x93) Daños en el directorio raíz FAT32 que no se pudieron corregir.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_SECTOR_INVALID** (0x89) El sector no es válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o memoria temporal.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.


### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close"></a>fx_media_close

Cierra el medio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Descripción

Este servicio cierra el medio especificado. En el proceso de cierre del medio, todos los archivos abiertos se cierran y el resto de los búferes se vacían en los medios físicos.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Cierre correcto del medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close_notify_set"></a>fx_media_close_notify_set

Establece la función de notificación de cierre de medio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a>Descripción

Este servicio establece una función de devolución de llamada de notificación que se invocará después de que un medio se cierre correctamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **media_close_notify**: función de devolución de llamada de notificación de cierre del medio que se va a instalar. Pasar NULL como la función de devolución de llamada deshabilita la devolución de llamada de cierre del medio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) La función de devolución de llamada se ha instalado correctamente.
- **FX_PTR_ERROR** (0x18) media_ptr es NULL.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_exfat_format"></a>fx_media_exFAT_format

Formatea el medio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a>Descripción

Este servicio da formato al medio proporcionado en un modo compatible con exFAT basado en los parámetros proporcionados. Se debe llamar a este servicio antes de abrir el medio.

> [!WARNING]
> *El formato a un medio ya formateado borra eficazmente todos los archivos y directorios del medio.*

> [!IMPORTANT]
> *El tamaño del volumen exFAT debe coincidir con el tamaño de la partición (si hay un diseño MBR o GPT) o con el tamaño de todo el dispositivo si no hay diseño de partición (sin MBR o GPT). En Windows existe la limitación de que el disco exFAT si se formatea con algunos valores de sectores totales que sean inferiores a los sectores disponibles.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio. Solo se utiliza para proporcionar un poco de información básica necesaria para que el controlador funcione.
- **driver**: puntero al controlador de E/S para este medio. Normalmente será el mismo controlador proporcionado a la siguiente llamada de fx_media_open.
- **driver_info_ptr**: puntero a información opcional que el controlador de E/S puede utilizar.
- **memory_ptr**: puntero a la memoria de trabajo del medio. memory_size Especifica el tamaño de la memoria de medios de trabajo. El tamaño debe ser al menos tan grande como el tamaño del sector del medio.
- **volume_name**: puntero a la cadena de nombre de volumen, que tiene un máximo de 11 caracteres.
- **number_of_fats**: número de FAT en el medio. La implementación actual admite una FAT en el medio.
- **hidden_sectors**: número de sectores ocultos antes del sector de arranque del medio. Esto es típico cuando hay varias particiones presentes.
- **total_sectors**: número total de sectores en el medio.
- **bytes_per_sector**: número de bytes por sector, que suele ser 512. FileX requiere que sea un múltiplo de 32.
> [!IMPORTANT]
> *Con referencia a la especificación, los bytes por sector solo pueden tomar los siguientes valores: 512, 1024, 2048 o 4096.*

- **sectors_per_cluster**: número de sectores en cada clúster. El clúster es la unidad de asignación mínima en un sistema de archivos FAT.
- **volumne_serial_number**: número de serie que se va a usar para este volumen.
- **boundary_unit**: tamaño de alineación del área de datos física, en número de sectores.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Formato correcto del medio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18): Puntero no válido de medio, controlador o memoria.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_extended_space_available"></a>fx_media_extended_space_available

Devuelve el espacio disponible en el medio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a>Descripción

Este servicio devuelve el número de bytes disponibles en el medio.

Este servicio está diseñado para exFAT. El puntero al parámetro *available_bytes* toma un valor entero de 64 bits, lo que permite al autor de la llamada trabajar con medios más allá del intervalo de 4 GB.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un medio abierto previamente.
- **available_bytes_ptr**: bytes disponibles que quedan en el medio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Se ha recuperado correctamente el espacio disponible en el medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_PTR_ERROR** (0x18) Puntero de medio no válido o el puntero de bytes disponibles es NULL.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_flush"></a>fx_media_flush

Vacía los datos en medios físicos.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Descripción

Este servicio vacía todos los sectores almacenados en caché y las entradas de directorio de los archivos modificados en los medios físicos.

> [!WARNING]
> *La aplicación puede llamar periódicamente a esta rutina para reducir el riesgo de daños en los archivos o la pérdida de datos en caso de una interrupción repentina de energía en el destino.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Vaciado correcto del medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_format"></a>fx_media_format

Formatea el medio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a>Descripción

Este servicio da formato al medio proporcionado en un modo compatible con FAT 12/16/32 basado en los parámetros proporcionados. Se debe llamar a este servicio antes de abrir el medio.

> [!WARNING]
> *El formato a un medio ya formateado borra eficazmente todos los archivos y directorios del medio.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio. Solo se utiliza para proporcionar un poco de información básica necesaria para que el controlador funcione.
- **driver**: puntero al controlador de E/S para este medio. Normalmente será el mismo controlador proporcionado a la siguiente llamada de fx_media_open.
- **driver_info_ptr**: puntero a información opcional que el controlador de E/S puede utilizar.
- **memory_ptr**: puntero a la memoria de trabajo del medio.
- **memory_size** Especifica el tamaño de la memoria de medios de trabajo. El tamaño debe ser al menos tan grande como el tamaño del sector del medio.
- **volume_name**: puntero a la cadena de nombre de volumen, que tiene un máximo de 11 caracteres.
- **number_of_fats**: número de FAT en el medio. El valor mínimo es 1 para la FAT principal. Los valores mayores que 1 hacen que se mantengan copias de FAT adicionales en tiempo de ejecución.
- **directory_entries**: el número de entradas de directorio en el directorio raíz.
- **hidden_sectors**: número de sectores ocultos antes del sector de arranque del medio. Esto es típico cuando hay varias particiones presentes.
- **total_sectors**: número total de sectores en el medio.
- **bytes_per_sector**: número de bytes por sector, que suele ser 512. FileX requiere que sea un múltiplo de 32.
> [!IMPORTANT]
> *Con referencia a la especificación, los bytes por sector solo pueden tomar los siguientes valores: 512, 1024, 2048 o 4096.*

- **sectors_per_cluster**: número de sectores en cada clúster. El clúster es la unidad de asignación mínima en un sistema de archivos FAT.
- **heads**: número de encabezados físicos.
- **sectors_per_track**: número de sectores por pista.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Formato correcto del medio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18): Puntero no válido de medio, controlador o memoria.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open"></a>fx_media_open

Abre el medio para el acceso a archivos.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a>Descripción

Este servicio abre un medio para el acceso a archivos mediante el controlador de E/S proporcionado.

> [!WARNING]
> *La memoria suministrada a este servicio se usa para implementar una caché de sectores lógicos interna; por lo tanto, cuanto más memoria se suministra más se reduce la E/S física. FileX requiere una memoria caché de al menos un sector lógico (bytes por sector del medio).*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **media_name**: puntero al nombre del medio.
- **media_driver**: puntero al controlador de E/S para este medio. El controlador de E/S debe cumplir los requisitos del controlador FileX definidos en el capítulo 5.
- **driver_info_ptr**: puntero a información opcional que el controlador de E/S proporcionado puede utilizar.
- **memory_ptr**: puntero a la memoria de trabajo del medio.
- **memory_size** Especifica el tamaño de la memoria de medios de trabajo. El tamaño debe ser tan grande como el tamaño de sector del medio (normalmente 512 bytes).

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Apertura correcta del medio.
- **FX_BOOT_ERROR** (0x01) Error al leer el sector de arranque del medio.
- **FX_MEDIA_INVALID** (0x02) El sector de arranque del medio especificado está dañado o no es válido. Además, este código de retorno se usa para indicar que el tamaño de la caché del sector lógico o el tamaño de la entrada de FAT no es una potencia de 2.
- **FX_FAT_READ_ERROR** (0x03) Error al leer la FAT del medio.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Uno o más punteros son NULL.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open_notify_set"></a>fx_media_open_notify_set

Establece la función de notificación de apertura del medio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a>Descripción

Este servicio establece una función de devolución de llamada de notificación que se invocará después de que un medio se abra correctamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **media_open_notify**: Función de devolución de llamada de notificación de apertura de medio que se va a instalar. Pasar NULL como la función de devolución de llamada deshabilita la devolución de llamada de apertura del medio.

### <a name="return-values"></a>Valores devueltos


- **FX_SUCCESS** (0x00) La función de devolución de llamada se ha instalado correctamente.
- **FX_PTR_ERROR** (0x18) media_ptr es NULL.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_read"></a>fx_media_read

Lee el sector lógico del medio

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a>Descripción

Este servicio lee un sector lógico del medio y lo coloca en el búfer proporcionado.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un medio abierto previamente.
- **logical_sector**: sector lógico que se va a leer.
- **buffer_ptr**: puntero al destino del sector lógico leído.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Lectura correcta del medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o búfer.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_space_available"></a>fx_media_space_available

Devuelve el espacio disponible en el medio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve el número de bytes disponibles en el medio.

Para trabajar con el medio mayor que 4 GB, la aplicación usará el servicio *fx_media_extended_space_available*.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un medio abierto previamente.
- **available_bytes_ptr**: bytes disponibles que quedan en el medio.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Se devolvió correctamente el espacio disponible en el medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_PTR_ERROR** (0x18) Puntero de medio no válido o el puntero de bytes disponibles es NULL.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get"></a>fx_media_volume_get

Obtiene el nombre del volumen del medio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a>Descripción

Este servicio recupera el nombre del volumen del medio abierto previamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **volume_name**: puntero al destino del nombre del volumen. Tenga en cuenta que el destino debe ser al menos lo suficientemente grande como para contener 12 caracteres.
- **volume_source**: designa dónde recuperar el nombre, ya sea desde el sector de arranque o desde el directorio raíz. Los valores válidos para este parámetro son:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Obtención correcta del volumen del medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_FOUND** (0x04) Volumen no encontrado.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de destino de volumen o medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get_extended"></a>fx_media_volume_get_extended

Obtiene el nombre del volumen de medio de los medios abiertos previamente.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a>Descripción

Este servicio recupera el nombre del volumen del medio abierto previamente.

> [!IMPORTANT]
> Este servicio es idéntico a ***fx_media_volume_get()** _ excepto en que el autor de la llamada pasa el tamaño del búfer _ *volume_name**.

### <a name="input-parameters"></a>Parámetros de entrada


- **media_ptr**: puntero al bloque de control de medio.
- **volume_name**: puntero al destino del nombre del volumen. Tenga en cuenta que el destino debe ser al menos lo suficientemente grande como para contener 12 caracteres.
- **volume_name_buffer_length**: tamaño del búfer volume_name.
- **volume_source**: designa dónde recuperar el nombre, ya sea desde el sector de arranque o desde el directorio raíz. Los valores válidos para este parámetro son:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Obtención correcta del volumen del medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_FOUND** (0x04) Volumen no encontrado.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Puntero no válido de destino de volumen o medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_set"></a>fx_media_volume_set

Establece el nombre del volumen del medio.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a>Descripción

Este servicio establece el nombre del volumen del medio abierto previamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **volume_name**: puntero al nombre del volumen.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Establecimiento correcto del volumen del medio.
- **FX_INVALID_NAME** (0x0C) Volume_name no es válido.
- **FX_MEDIA_INVALID** (0x02) No se puede establecer el nombre del volumen.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio o nombre de volumen.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_write
- fx_system_initialize

## <a name="fx_media_write"></a>fx_media_write

Escribe el sector lógico.

### <a name="prototype"></a>Prototipo

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a>Descripción

Este servicio escribe el búfer proporcionado en el sector lógico especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero a un medio abierto previamente.
- **logical_sector**: sector lógico que se va a escribir.
- **buffer_ptr**: puntero al origen de la escritura de sector lógico.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Escritura correcta del medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Puntero no válido de medio.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a>Consulte también

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_system_initialize

## <a name="fx_system_date_get"></a>fx_system_date_get

Obtiene la fecha del sistema de archivos.

### <a name="prototype"></a>Prototipo

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a>Descripción

Este servicio devuelve la fecha actual del sistema.

### <a name="input-parameters"></a>Parámetros de entrada

- **year**: puntero al destino del año.
- **month**: puntero al destino del mes.
- **day**: puntero al destino del día.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Recuperación correcta de la fecha.
- **FX_PTR_ERROR** (0x18) Uno o varios de los parámetros de entrada son NULL.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a>Consulte también

- fx_system_date_set
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_date_set"></a>fx_system_date_set

Establece la fecha del sistema.

### <a name="prototype"></a>Prototipo

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a>Descripción

Este servicio establece la fecha del sistema según se especifique.

> [!WARNING]
> *Se debe llamar a este servicio poco después de **fx_system_initialize** para establecer la fecha inicial del sistema. De forma predeterminada, la fecha del sistema es la de la versión genérica más reciente de FileX.*

### <a name="input-parameters"></a>Parámetros de entrada

- **year**: nuevo año. El intervalo válido es desde el año 1980 hasta 2107.
- **mes**: nuevo mes. El intervalo válido es de 1 a 12.
- **day**: nuevo día. El intervalo válido es entre 1 y 31, en función de las condiciones de año bisiesto y mes.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Establecimiento correcto de la fecha.
- **FX_INVALID_YEAR** (0x12) Se ha especificado un año no válido.
- **FX_INVALID_MONTH** (0x13) Se ha especificado un mes no válido.
- **FX_INVALID_DAY** (0x14) Se ha especificado un día no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a>Consulte también

- fx_system_date_get
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_initialize"></a>fx_system_initialize

Inicializa todo el sistema.

### <a name="prototype"></a>Prototipo

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a>Descripción

Este servicio inicializa todas las estructuras de datos principales de FileX. Se debe llamar en ***tx_application_define*** o tal vez desde un subproceso de inicialización y debe hacerse antes de usar cualquier otro servicio de FileX.

> [!WARNING]
> *Una vez inicializada mediante esta llamada, la aplicación debe llamar a ***fx_system_date_set** _ y _ *fx_system_time_set** para iniciar con una fecha y hora del sistema precisas.*

### <a name="input-parameters"></a>Parámetros de entrada

Ninguno

### <a name="return-values"></a>Valores devueltos

Ninguno.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a>Consulte también

- fx_system_date_get
- fx_system_date_set
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_time_get"></a>fx_system_time_get

Obtiene la hora actual del sistema.

### <a name="prototype"></a>Prototipo

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a>Descripción

Este servicio recupera la hora actual del sistema.

### <a name="input-parameters"></a>Parámetros de entrada

- **hour**: puntero al destino de la hora.
- **minute**: puntero al destino del minuto.
- **second**: puntero al destino del segundo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Recuperación correcta de la hora del sistema.
- **FX_PTR_ERROR** (0x18) Uno o varios de los parámetros de entrada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a>Consulte también

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_set

## <a name="fx_system_time_set"></a>fx_system_time_set

Establece la hora actual del sistema.

### <a name="prototype"></a>Prototipo

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a>Descripción

Este servicio establece la hora actual del sistema en la especificada por los parámetros de entrada.

> [!WARNING]
> *Se debe llamar a este servicio poco después de **fx_system_initialize** para establecer la hora inicial del sistema. De forma predeterminada, la hora del sistema es 0:0:0.*

### <a name="input-parameters"></a>Parámetros de entrada

- **hour**: nueva hora (de 0 a 23).
- **minute**: nuevo minuto (de 0 a 59).
- **second**: nuevo segundo (de 0 a 59).

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Recuperación correcta de la hora del sistema.
- **FX_INVALID_HOUR** (0x15) La nueva hora no es válida.
- **FX_INVALID_MINUTE** (0x16) El nuevo minuto no es válido.
- **FX_INVALID_SECOND** (0x17) El nuevo segundo no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a>Consulte también

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_get

## <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create

Crea un directorio Unicode.

### <a name="prototype"></a>Prototipo

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a>Descripción

Este servicio crea un subdirectorio con nombre Unicode en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre de origen Unicode). Si es correcto, el servicio devuelve el nombre corto (formato 8.3) del subdirectorio Unicode recién creado.

> [!WARNING]
> *Todas las operaciones en el subdirectorio Unicode (conversión en la ruta de acceso predeterminada, eliminación, etc.) deben realizarse proporcionando el nombre corto devuelto (formato 8.3) a los servicios de directorio de FileX estándar.*

> [!IMPORTANT]
> *Este servicio no es compatible con los medios exFAT.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **source_unicode_name**: puntero al nombre Unicode del nuevo subdirectorio.
- **source_unicode_length**: longitud del nombre Unicode.
- **short_name**: puntero al destino del nombre corto (formato 8.3) para el nuevo subdirectorio Unicode.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Creación correcta de directorio Unicode.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_ALREADY_CREATED** (0x0B) El directorio especificado ya existe.
- **FX_NO_MORE_SPACE** (0x0A) no hay más clústeres disponibles en los medios para la entrada del nuevo directorio.
- **FX_NOT_IMPLEMENTED** (0x22) No se ha implementado el servicio para el sistema de archivos exFAT.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_rename

## <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

Cambia el nombre del directorio mediante la cadena Unicode.

### <a name="prototype"></a>Prototipo

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a>Descripción

Este servicio cambia un subdirectorio con nombre Unicode al nuevo nombre Unicode especificado en el directorio de trabajo actual. Los parámetros de nombre Unicode no deben tener información de ruta de acceso.

> [!IMPORTANT]
> *Este servicio no es compatible con los medios exFAT.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **old_unicode_name**: puntero al nombre Unicode del archivo actual.
- **old_unicode_name_length**: longitud del nombre Unicode actual.
- **new_unicode_name**: puntero al nuevo nombre de archivo Unicode.
- **old_unicode_name_length**: Longitud del nombre Unicode nuevo.
- **new_short_name**: puntero al destino del nombre corto (formato 8.3) del archivo Unicode con el nombre cambiado. Cambie el nombre del directorio con Unicode.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Apertura correcta del medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_ALREADY_CREATED** (0x0B) El nombre de directorio especificado ya existe.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Uno o más punteros son NULL.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Consulte también

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_unicode_file_create"></a>fx_unicode_file_create

Crea un archivo Unicode.

### <a name="prototype"></a>Prototipo

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a>Descripción

Este servicio crea un archivo con nombre Unicode en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre de origen Unicode). Si es correcto, el servicio devuelve el nombre corto (formato 8.3) del archivo Unicode recién creado.

> [!WARNING]
> *Todas las operaciones en el archivo Unicode (abrir, escribir, leer, cerrar, etc.) deben realizarse proporcionando el nombre corto devuelto (formato 8.3) a los servicios de archivo de FileX estándar.*

### <a name="input-parameters"></a>Parámetros de entrada


- **media_ptr**: puntero al bloque de control de medio.
- **source_unicode_name**: puntero al nombre Unicode del nuevo archivo.
- **source_unicode_length**: longitud del nombre Unicode.
- **short_name**: puntero al destino del nombre corto (formato 8.3) para el nuevo archivo Unicode.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Creación correcta de archivo.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_ALREADY_CREATED** (0x0B) El archivo especificado ya existe.
- **FX_NO_MORE_SPACE** (0x0A) No hay más clústeres disponibles en los medios para la entrada del nuevo archivo.
- **FX_NOT_IMPLEMENTED** (0x22) No se ha implementado el servicio para el sistema de archivos exFAT.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.
- **FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

Cambia el nombre de un archivo mediante una cadena Unicode

### <a name="prototype"></a>Prototipo

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a>Descripción

Este servicio cambia un nombre de archivo con nombre Unicode al nuevo nombre Unicode especificado en el directorio predeterminado actual. Los parámetros de nombre Unicode no deben tener información de ruta de acceso.

> [!IMPORTANT]
> *Este servicio no es compatible con los medios exFAT.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **old_unicode_name**: puntero al nombre Unicode del archivo actual.
- **old_unicode_name_length**: longitud del nombre Unicode actual.
- **new_unicode_name**: puntero al nuevo nombre de archivo Unicode.
- **new_unicode_name_length**: longitud del nombre Unicode nuevo.
- **new_short_name**: puntero al destino del nombre corto (formato 8.3) del archivo Unicode con el nombre cambiado.

### <a name="return-values"></a>Valores devueltos


- **FX_SUCCESS** (0x00) Apertura correcta del medio.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_ALREADY_CREATED** (0x0B) El nombre de archivo especificado ya existe.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_PTR_ERROR** (0x18) Uno o más punteros son NULL.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.
- **FX_WRITE_PROTECT** (0x23) El medio especificado está protegido contra escritura.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get"></a>fx_unicode_length_get

Obtiene la longitud del nombre Unicode.

### <a name="prototype"></a>Prototipo

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a>Descripción

Este servicio determina la longitud del nombre Unicode proporcionado. Un carácter Unicode se representa mediante dos bytes. Un nombre Unicode es una serie de caracteres Unicode de dos bytes terminada en dos bytes NULL (dos bytes de valor 0).

### <a name="input-parameters"></a>Parámetros de entrada

**unicode_name**: puntero al nombre Unicode.

### <a name="return-values"></a>Valores devueltos

**length**: longitud del nombre Unicode (número de caracteres Unicode en el nombre).

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get_extended"></a>fx_unicode_length_get_extended

Obtiene la longitud del nombre Unicode.

### <a name="prototype"></a>Prototipo

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a>Descripción

Este servicio obtiene la longitud del nombre Unicode proporcionado. Un carácter Unicode se representa mediante dos bytes. Un nombre Unicode es una serie de caracteres Unicode de dos bytes terminada en dos bytes NULL (dos bytes de valor 0).

> [!IMPORTANT]
> *Este servicio es idéntico a **fx_unicode_length_get ()** , excepto en que el autor de la llamada pasa el tamaño del búfer de **unicode_name**, incluidos los dos caracteres NULL.*

### <a name="input-parameters"></a>Parámetros de entrada

- **unicode_name**: puntero al nombre Unicode.
- **buffer_length**: tamaño del búfer de nombre Unicode.

### <a name="return-values"></a>Valores devueltos

**length**: longitud del nombre Unicode (número de caracteres Unicode en el nombre).

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get"></a>fx_unicode_name_get

Obtiene el nombre Unicode del nombre corto.

### <a name="prototype"></a>Prototipo

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a>Descripción

Este servicio recupera el nombre Unicode asociado al nombre corto proporcionado (formato 8.3) en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre corto). Si es correcto, el servicio devuelve el nombre Unicode asociado al nombre corto.

> [!IMPORTANT]
> *Este servicio se puede usar para obtener nombres Unicode para archivos y subdirectorios.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **short_name**: puntero al nombre corto (formato 8.3).
- **destination_unicode_name**: puntero al destino para el nombre Unicode asociado al nombre corto proporcionado.
- **destination_unicode_length**: puntero a la longitud del nombre Unicode devuelto.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Recuperación correcta del nombre Unicode.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_FOUND** (0x04) No se encontró el nombre corto o el tamaño de destino Unicode es demasiado pequeño.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get_extended"></a>fx_unicode_name_get_extended

Obtiene el nombre Unicode del nombre corto.

### <a name="prototype"></a>Prototipo

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a>Descripción

Este servicio recupera el nombre Unicode asociado al nombre corto proporcionado (formato 8.3) en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre corto). Si es correcto, el servicio devuelve el nombre Unicode asociado al nombre corto.

> [!IMPORTANT]
> *Este servicio es idéntico a ***fx_unicode_name_get** _, salvo que el autor de la llamada proporciona el tamaño del búfer Unicode de destino como argumento de entrada. Esto permite al servicio garantizar que no sobrescribirá el búfer Unicode de destino_.

> [!IMPORTANT]
> *Este servicio se puede usar para obtener nombres Unicode para archivos y subdirectorios.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **short_name**: puntero al nombre corto (formato 8.3).
- **destination_unicode_name**: puntero al destino para el nombre Unicode asociado al nombre corto proporcionado.
- **destination_unicode_length**: puntero a la longitud del nombre Unicode devuelto.
- **unicode_name_buffer_length**: tamaño del búfer de nombre Unicode. Nota: Se requiere un terminador NULL, que es un byte adicional.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Recuperación correcta del nombre Unicode.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_FOUND** (0x04) No se encontró el nombre corto o el tamaño de destino Unicode es demasiado pequeño.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

Obtiene el nombre corto del nombre Unicode.

### <a name="prototype"></a>Prototipo

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

Este servicio recupera el nombre corto (formato 8.3) asociado al nombre Unicode en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre Unicode). Si es correcto, el servicio devuelve el nombre corto asociado al nombre Unicode.

> [!IMPORTANT]
> *Este servicio se puede usar para obtener nombres cortos para archivos y subdirectorios.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **source_unicode_name**: puntero al nombre Unicode.
- **source_unicode_length**: longitud del nombre Unicode.
- **destination_short_name**: puntero al destino del nombre corto (formato 8.3). Debe tener un tamaño mínimo de 13 bytes.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Recuperación correcta de nombre corto.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_FOUND** (0x04) No se ha encontrado el nombre Unicode.
- **FX_NOT_IMPLEMENTED** (0x22) No se ha implementado el servicio para el sistema de archivos exFAT.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get

## <a name="fx_unicode_short_name_get_extended"></a>fx_unicode_short_name_get_extended

Obtiene el nombre corto del nombre Unicode.

### <a name="prototype"></a>Prototipo

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a>Descripción

Este servicio recupera el nombre corto (formato 8.3) asociado al nombre Unicode en el directorio predeterminado actual (no se permite ninguna información de ruta de acceso en el parámetro de nombre Unicode). Si es correcto, el servicio devuelve el nombre corto asociado al nombre Unicode.

> [!IMPORTANT]
> *Este servicio es idéntico a **fx_unicode_name_get()** , salvo que el autor de la llamada proporciona el tamaño del búfer de destino como argumento de entrada. Esto permite al servicio garantizar que el nombre corto no supera el búfer de destino.*

*Este servicio se puede usar para obtener nombres cortos para archivos y subdirectorios.*

### <a name="input-parameters"></a>Parámetros de entrada

- **media_ptr**: puntero al bloque de control de medio.
- **source_unicode_name**: puntero al nombre Unicode.
- **source_unicode_length**: longitud del nombre Unicode.
- **destination_short_name**: puntero al destino del nombre corto (formato 8.3). Debe tener un tamaño mínimo de 13 bytes.
- **short_name_buffer_length**: tamaño del búfer de destino. El tamaño del búfer debe ser de 14 bytes como mínimo.

### <a name="return-values"></a>Valores devueltos

- **FX_SUCCESS** (0x00) Recuperación correcta de nombre corto.
- **FX_FAT_READ_ERROR** (0x03) No se puede leer la tabla FAT.
- **FX_FILE_CORRUPT** (0x08) El archivo está dañado.
- **FX_IO_ERROR** (0x90) Error de E/S del controlador.
- **FX_MEDIA_NOT_OPEN** (0x11) El medio especificado no está abierto.
- **FX_NOT_FOUND** (0x04) No se ha encontrado el nombre Unicode.
- **FX_NOT_IMPLEMENTED** (0x22) No se ha implementado el servicio para el sistema de archivos exFAT.
- **FX_SECTOR_INVALID** (0x89) Sector no válido.
- **FX_PTR_ERROR** (0x18) Punteros no válidos de medio o nombre.
- **FX_CALLER_ERROR** (0x20) El autor de la llamada no es un subproceso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>Consulte también

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get
