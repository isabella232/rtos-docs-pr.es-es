---
title: 'Capítulo 4: API NAND de Azure RTOS LevelX'
description: Las API NAND de Azure RTOS LevelX disponibles para la aplicación.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d92b6c10921b4d04345610e139101e93c7a439ff695a89a79245894ad9ef1fec
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790293"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a>Capítulo 4: API NAND de Azure RTOS LevelX

Las API NAND de Azure RTOS LevelX disponibles para la aplicación son:

- ***lx_nand_flash_close** _: _cerrar la instancia de memoria flash NAND*
- ***lx_nand_flash_defragment** _: _desfragmentar la instancia de memoria flash NAND*
- ***lx_nand_flash_extended_cache_enable** _: _habilitar o deshabilitar la memoria caché NAND extendida*
- ***lx_nand_flash_initialize** _: _inicializar la compatibilidad con memoria flash NAND*
- ***lx_nand_flash_open** _: _abrir instancia de memoria flash NAND*
- ***lx_nand_flash_page_ecc_check** _: _comprobar página de errores ECC con corrección*
- ***lx_nand_flash_page_ecc_compute** _: _calcular ECC de la página*
- ***lx_nand_flash_partial_defragment** _: _desfragmentar parcialmente la instancia de memoria flash NAND*
- ***lx_nand_flash_sector_read** _: _leer sector de memoria flash NAND*
- ***lx_nand_flash_sector_release** _: _liberar sector de memoria flash NAND*
- ***lx_nand_flash_sector_write** _: _escribir sector de memoria flash NAND*

## <a name="lx_nand_flash_close"></a>lx_nand_flash_close

Cerrar instancia de memoria flash NAND

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Descripción

Este servicio cierra la instancia de memoria flash NAND abierta previamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al cerrar la instancia de memoria flash.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_defragment"></a>lx_nand_flash_defragment

Desfragmentar instancia de memoria flash NAND

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Descripción

Este servicio desfragmenta la instancia de memoria flash NAND abierta previamente. El proceso de desfragmentación maximiza el número de páginas y bloques libres.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al desfragmentar la instancia de memoria flash.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_extended_cache_enable"></a>lx_nand_flash_extended_cache_enable

Habilitar o deshabilitar la memoria caché NAND extendida

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Descripción

Este servicio implementa una capa de memoria caché en RAM mediante la memoria proporcionada por la aplicación. La cantidad total de memoria necesaria para la operación de caché completa se puede calcular de la manera siguiente:

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

Si la memoria proporcionada no es lo suficientemente grande como para dar cabida a toda la memoria caché NAND, esta rutina habilitará la mayor parte posible de la memoria caché flash NAND en función de la memoria suministrada.

La memoria caché NAND se deshabilita si la dirección de memoria especificada es NULL. Por lo tanto, la caché NAND podría usarse de manera temporal.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.  
- **memory**: dirección de inicio de la memoria caché, alineada para el acceso ULONG. Un valor LX_NULL deshabilita la memoria caché.  
- **size**: el tamaño en bytes de la memoria suministrada.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) No hay suficiente memoria para un elemento de la memoria caché NAND.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_initialize"></a>lx_nand_flash_initialize

Inicializar la compatibilidad con la memoria flash NAND

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a>Descripción

Este servicio inicializa la compatibilidad con la memoria flash NAND de LevelX. Se debe antes que a cualquier otra API NAND de LevelX.

### <a name="input-parameters"></a>Parámetros de entrada

- **None**

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al inicializar o a la compatibilidad con flash.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_open"></a>lx_nand_flash_open

Abrir instancia de memoria flash NAND

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a>Descripción

Este servicio abre una instancia de memoria flash NAND con la función de inicialización del controlador y el bloque de control de memoria flash NAND especificados. Tenga en cuenta que la función de inicialización del controlador es responsable de la instalación de varios punteros de función para la lectura, escritura y borrado de bloques o páginas del hardware NAND asociado a esta instancia de memoria flash NAND.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.
- **name**: nombre de la instancia de memoria flash NAND.
- **nand_driver_initialize**: puntero de función a la función de inicialización del controlador de memoria flash NAND. Consulte el capítulo 3 de esta guía para más información sobre las responsabilidades del controlador de memoria flash NAND.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al abrir la instancia de memoria flash NAND.
- **LX_NO_MEMORY**: (0x08) El controlador no proporcionó ningún búfer para leer una página en RAM.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_check"></a>lx_nand_flash_page_ecc_check

Comprobar página de errores ECC con corrección

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Descripción

Este servicio comprueba la integridad del búfer de páginas NAND proporcionado con el ECC suministrado. Se supone que el tamaño de página (definido en el puntero de instancia de memoria flash NAND) es un múltiplo de 256 bytes y el código ECC proporcionado es capaz de corregir un error de 1 bit en cada fragmento de 256 bytes de la página.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.
- **page_buffer**: puntero al búfer de página de memoria flash NAND.
- **ecc_buffer**: puntero a ECC para la página de memoria flash NAND. Tenga en cuenta que hay 3 bytes de ECC por fragmento de 256 bytes de la página.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) La página NAND no contiene errores.
- **LX_NAND_ERROR_CORRECTED**: (0x06) Se corrigieron uno o más errores de 1 bit en la página NAND, las correcciones están en el búfer de páginas.
- **LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Demasiados errores para corregir en la página NAND.

### <a name="allowed-from"></a>Permitido desde

Controlador LevelX

### <a name="example"></a>Ejemplo

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_compute"></a>lx_nand_flash_page_ecc_compute

Calcular ECC para la página

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Descripción

Este servicio calcula el ECC del búfer de página NAND proporcionado y devuelve el ECC en el búfer de ECC suministrado. Se supone que el tamaño de página es un múltiplo de 256 bytes (definido en el puntero de instancia de memoria flash NAND). El código ECC se usa para comprobar la integridad de la página cuando se lea en un momento posterior.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.
- **page_buffer**: puntero al búfer de página de memoria flash NAND.
- **ecc_buffer**: puntero al destino de ECC de la página de memoria flash NAND. Tenga en cuenta que debe tener 3 bytes de almacenamiento de ECC por fragmento de 256 bytes de la página. Por ejemplo, una página de 2048 bytes requeriría 24 bytes para el ECC.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) El ECC se calculó correctamente.
- **LX_ERROR**: (0x01) Error al calcular el ECC.

### <a name="allowed-from"></a>Permitido desde

Controlador LevelX

### <a name="example"></a>Ejemplo

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_partial_defragment"></a>lx_nand_flash_partial_defragment

Desfragmentar parcialmente la instancia de memoria flash NAND

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a>Descripción

Este servicio desfragmenta la instancia de memoria flash NAND abierta anteriormente hasta el número máximo de bloques especificado. El proceso de desfragmentación maximiza el número de páginas y bloques libres.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.
- **max_blocks**: número máximo de bloques.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al desfragmentar la instancia de memoria flash.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_read"></a>lx_nand_flash_sector_read

Leer sector de memoria flash NAND

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Descripción

Este servicio lee el sector lógico de la instancia de memoria flash NAND y, si la operación se realiza correctamente, devuelve el contenido en el búfer proporcionado. Tenga en cuenta que el tamaño del sector NAND siempre es el tamaño de página del hardware NAND subyacente.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.
- **logical_sector**: sector lógico que se va a leer.
- **buffer**: puntero al destino del contenido del sector lógico. Tenga en cuenta que se supone que el búfer tiene el tamaño de la página de memoria flash NAND y está alineado para el acceso ULONG.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al leer el sector de memoria flash NAND.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_release"></a>lx_nand_flash_sector_release

Liberar sector de memoria flash NAND

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Descripción

Este servicio libera la asignación del sector lógico en la instancia de memoria flash NAND. La liberación de un sector lógico cuando no se usa hace que la nivelación de la utilización de LevelX sea más eficaz.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.
- **logical_sector**: sector lógico que se va a liberar.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_ERROR**: (0x01) Error al escribir sector de memoria flash NAND.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_write"></a>lx_nand_flash_sector_write

Escribir sector de memoria flash NAND

### <a name="prototype"></a>Prototipo

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Descripción

Este servicio escribe el sector lógico especificado en la instancia de memoria flash NAND.

### <a name="input-parameters"></a>Parámetros de entrada

- **nand_flash**: puntero de la instancia de memoria flash NAND.
- **logical_sector**: sector lógico que se va a escribir.
- **buffer**: puntero al contenido del sector lógico. Tenga en cuenta que se supone que el búfer tiene el tamaño de la página de memoria flash NAND y está alineado para el acceso ULONG.

### <a name="return-values"></a>Valores devueltos

- **LX_SUCCESS**: (0x00) Solicitud correcta.
- **LX_NO_SECTORS**: (0x02) No hay más sectores libres disponibles para realizar la escritura.
- **LX_ERROR**: (0x01) Error al liberar el sector de memoria flash NAND.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>Consulte también

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
