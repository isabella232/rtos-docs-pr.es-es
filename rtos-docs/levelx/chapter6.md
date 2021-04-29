---
title: 'Capítulo 6: API NOR de Azure RTOS LevelX'
description: Información sobre las API NOR de Azure RTOS LevelX disponibles para la aplicación.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815421"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a>Capítulo 6: API NOR de Azure RTOS LevelX

Las funciones de las API NOR de Azure RTOS LevelX disponibles para la aplicación son las siguientes.

- ***lx_nor_flash_close** _: _cerrar la instancia de memoria flash NOR*
- ***lx_nor_flash_defragment** _: _desfragmentar la instancia de memoria flash NOR*
- ***lx_nor_flash_extended_cache_enable** _: _habilitar o deshabilitar la memoria caché NOR extendida*
- ***lx_nor_flash_initialize** _: _inicializar la compatibilidad con memoria flash NOR*
- ***lx_nor_flash_open** _: _abrir la instancia de memoria flash NOR*
- ***lx_nor_flash_partial_defragment** _: _desfragmentar parcialmente la instancia de memoria flash NOR*
- ***lx_nor_flash_sector_read** _: _leer un sector de memoria flash NOR*
- ***lx_nor_flash_sector_release** _: _liberar un sector de memoria flash NOR*
- ***lx_nor_flash_sector_write** _: _escribir un sector de memoria flash NOR*

## <a name="lx_nor_flash_close"></a>lx_nor_flash_close

Cerrar la instancia de memoria flash NOR

### <a name="prototype"></a>Prototipo

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Descripción

Este servicio cierra la instancia de memoria flash NOR abierta previamente.

### <a name="input-parameters"></a>Parámetros de entrada

- *nor_flash*: puntero a la instancia de memoria flash NOR.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al cerrar la instancia de memoria flash.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_defragment"></a>lx_nor_flash_defragment

Desfragmentar la instancia de flash NOR

### <a name="prototype"></a>Prototipo

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Descripción

Este servicio desfragmenta la instancia de memoria flash NOR abierta previamente. El proceso de desfragmentación maximiza el número de sectores y bloques libres.

### <a name="input-parameters"></a>Parámetros de entrada

- *nor_flash*: puntero a la instancia de memoria flash NOR.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al desfragmentar la instancia de memoria flash.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nor_flash_close
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_extended_cache_enable"></a>lx_nor_flash_extended_cache_enable

Habilitar o deshabilitar la memoria caché NOR extendida

### <a name="prototype"></a>Prototipo

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Descripción

Este servicio implementa una capa de memoria caché de sectores NOR en RAM mediante la memoria proporcionada por la aplicación. Cada 512 bytes de memoria proporcionados se traduce en un sector NOR que se puede almacenar en caché. Los sectores almacenados en caché son los que contienen la información de control de bloques, por ejemplo, recuento de borrados, mapa de sectores libres e información de asignación de sectores. Los sectores de datos no se almacenan en esta memoria caché.

### <a name="input-parameters"></a>Parámetros de entrada

- **nor_flash**: puntero a la instancia de memoria flash NOR.  
- **memory**: dirección de inicio de la memoria caché, alineada para el acceso ULONG. Un valor LX_NULL deshabilita la memoria caché.  
- **size**: tamaño en bytes de la memoria suministrada (debe ser múltiplo de 512 bytes).

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) No hay suficiente memoria para un sector NOR.
- **LX_DISABLED**: (0x09) memoria caché NOR extendida deshabilitada mediante la opción de configuración.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_initialize"></a>lx_nor_flash_initialize

Inicializar la compatibilidad con memoria flash NOR

### <a name="prototype"></a>Prototipo

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a>Descripción

Este servicio inicializa la compatibilidad con memoria flash NOR. Se debe llamar al servicio antes que a cualquier otra API NOR de LevelX.

### <a name="input-parameters"></a>Parámetros de entrada

- **None**

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al inicializar la compatibilidad con memoria flash NOR.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_partial_defragment
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_open"></a>lx_nor_flash_open

Abrir la instancia de memoria flash NOR

### <a name="prototype"></a>Prototipo

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a>Descripción

Este servicio abre una instancia de memoria flash NOR con la función de inicialización del controlador y el bloque de control de memoria flash NOR especificados. Tenga en cuenta que la función de inicialización del controlador es responsable de la instalación de varios punteros de función para la lectura, escritura y borrado de bloques del hardware NOR asociado a esta instancia de memoria flash NOR.

### <a name="input-parameters"></a>Parámetros de entrada

- *nor_flash*: puntero a la instancia de memoria flash NOR.
- *name*: nombre de la instancia de memoria flash NOR.
- *nor_driver_initialize*: puntero de función a la función de inicialización del controlador de memoria flash NOR. Consulte el capítulo 5 de esta guía para más información sobre las responsabilidades del controlador de memoria flash NOR.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al abrir la instancia de memoria flash NOR.
- **LX_NO_MEMORY**: (0x08) El controlador no proporcionó ningún búfer para leer ningún sector en RAM.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_partial_defragment"></a>lx_nor_flash_partial_defragment

Desfragmentar parcialmente la instancia de memoria flash NOR

### <a name="prototype"></a>Prototipo

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a>Descripción

Este servicio desfragmenta la instancia de memoria flash NOR abierta anteriormente hasta el número máximo de bloques especificado. El proceso de desfragmentación maximiza el número de sectores y bloques libres.

### <a name="input-parameters"></a>Parámetros de entrada

- *nor_flash*: puntero a la instancia de memoria flash NOR.
- *max_blocks*: número máximo de bloques.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al desfragmentar la instancia de memoria flash.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_read"></a>lx_nor_flash_sector_read

Leer un sector de memoria flash NOR

### <a name="prototype"></a>Prototipo

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Descripción

Este servicio lee el sector lógico de la instancia de memoria flash NOR y, si la operación se realiza correctamente, devuelve el contenido en el búfer proporcionado. Tenga en cuenta que el tamaño de un sector NOR siempre de 512 bytes.

### <a name="input-parameters"></a>Parámetros de entrada

- *nor_flash*: puntero a la instancia de memoria flash NOR.
- *logical_sector*: sector lógico que se va a leer.
- *buffer*: puntero al destino del contenido del sector lógico. Tenga en cuenta que se supone que el búfer es de 512 bytes y está alineado para el acceso ULONG.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al leer el sector de memoria flash NOR.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a>Consulte también

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_release"></a>lx_nor_flash_sector_release

Liberar un sector de memoria flash NOR

### <a name="prototype"></a>Prototipo

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Descripción

Este servicio libera la asignación del sector lógico en la instancia de memoria flash NOR. La liberación de un sector lógico cuando no se usa hace que la nivelación del desgaste de LevelX sea más eficaz.

### <a name="input-parameters"></a>Parámetros de entrada

- *nor_flash*: puntero a la instancia de memoria flash NOR.
- *logical_sector*: sector lógico que se va a liberar.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) error al escribir el sector de memoria flash NOR.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>Consulte también

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_write"></a>lx_nor_flash_sector_write

Escribir un sector de memoria flash NOR

### <a name="prototype"></a>Prototipo

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Descripción

Este servicio escribe el sector lógico especificado en la instancia de memoria flash NOR.

### <a name="input-parameters"></a>Parámetros de entrada

- *nor_flash*: puntero a la instancia de memoria flash NOR.
- *logical_sector*: sector lógico que se va a escribir.
- *buffer*: puntero al contenido del sector lógico. Tenga en cuenta que se supone que el búfer es de 512 bytes y está alineado para el acceso ULONG.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_NO_SECTORS**: (0x02) No hay más sectores libres disponibles para realizar la escritura.
- **LX_ERROR**: (0x01) Error al liberar el sector de memoria flash NOR.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>Consulte también

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
