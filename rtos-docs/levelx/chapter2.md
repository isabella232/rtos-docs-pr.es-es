---
title: 'Capítulo 2: Instalación y uso de Azure RTOS LevelX'
description: La instalación y el uso de LevelX son sencillos y se describen en las siguientes secciones de este capítulo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223322"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a>Capítulo 2: Instalación y uso de Azure RTOS LevelX

La instalación y el uso de Azure RTOS LevelX son sencillos y se describen en las siguientes secciones de este capítulo.

## <a name="distribution"></a>Distribución

LevelX se distribuye en ANSI C, donde cada función se encuentra en su propio archivo de C independiente. Los archivos de la distribución de LevelX son los siguientes.
- lx_api.h
- lx_nand_flash_256byte_ecc_check.c
- lx_nand_flash_256byte_ecc_compute.c
- lx_nand_flash_block_full_update.c
- lx_nand_flash_block_reclaim.c
- lx_nand_flash_close.c
- lx_nand_flash_defragment.c  
- lx_nand_flash_extended_cache_enable.c
- lx_nand_flash_initialize.c
- lx_nand_flash_logical_sector_find.c
- lx_nand_flash_next_block_to_erase_find.c
- lx_nand_flash_open.c
- lx_nand_flash_page_ecc_check.c
- lx_nand_flash_page_ecc_compute.c  
- lx_nand_flash_partial_defragment.c
- lx_nand_flash_physical_page_allocate.c
- lx_nand_flash_sector_mapping_cache_invalidate.c
- lx_nand_flash_sector_read.c
- lx_nand_flash_sector_release.c
- lx_nand_flash_sector_write.c
- lx_nand_flash_system_error.c
- lx_nor_flash_block_reclaim.c
- lx_nor_flash_close.c
- lx_nor_flash_defragment.c  
- lx_nor_flash_extended_cache_enable.c
- lx_nor_flash_initialize.c
- lx_nor_flash_logical_sector_find.c
- lx_nor_flash_next_block_to_erase_find.c
- lx_nor_flash_open.c
- lx_nor_flash_partial_defragment.c
- lx_nor_flash_physical_sector_allocate.c
- lx_nor_flash_sector_mapping_cache_invalidate.c
- lx_nor_flash_sector_read.c
- lx_nor_flash_sector_release.c
- lx_nor_flash_sector_write.c
- lx_nor_flash_system_error.c

También hay ejemplos de controladores de simulador y FileX, tanto para instancias de NAND de LevelX como para instancias de NOR, como se indica a continuación.

- demo_filex_nand_flash.c  
- fx_nand_flash_simulated_driver.c
- lx_nand_flash_simulator.c
- demo_filex_nor_flash.c  
- fx_nor_flash_simulated_driver.c
- lx_nor_flash_simulator.c

Por supuesto, si solo se requiere memoria flash NAND, solo se necesitan los archivos para memoria flash NAND de LevelX (***lx_nand_\*.c***). Del mismo modo, si solo se requiere memoria flash NOR, solo se necesitan los archivos para memoria flash NOR (**_lx_nor_\_.c***).

## <a name="configuration-options"></a>Opciones de configuración

LevelX se puede configurar en tiempo de compilación mediante las definiciones condicionales que se describen a continuación. Basta con agregar la definición deseada a la compilación de cada código fuente de LevelX para utilizar la opción.

- **LX_DIRECT_READ**: definido, esta opción omite la rutina de lectura del controlador de memoria flash NOR para favorecer o leer directamente la memoria NOR, lo que da lugar a un aumento significativo del rendimiento.
- **LX_FREE_SECTOR_DATA_VERIFY**: definido, esto hace que la lógica de apertura de la instancia de NOR de LevelX compruebe que los sectores NOR libres son todos unos.
- **LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: de forma predeterminada, este valor es 16 y define el tamaño de la memoria caché de asignación de sectores lógicos. Los valores grandes mejoran el rendimiento, pero tienen un costo de memoria. El tamaño mínimo es 8 y todos los valores deben ser una potencia de 2.
- **LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: definido, esto crea una memoria caché de asignación directa, de modo que no hay errores de caché. También requiere que LX_NAND_SECTOR_MAPPING_CACHE_SIZE represente el número exacto de páginas totales del dispositivo flash.
- **LX_NOR_DISABLE_EXTENDED_CACHE**: definido, esto deshabilita la memoria caché NOR extendida.
- **LX_NOR_EXTENDED_CACHE_SIZE**: de forma predeterminada, este valor es 8, que representa un máximo de 8 sectores que se pueden almacenar en memoria caché en una instancia de NOR.
- **LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: de forma predeterminada, este valor es 16 y define el tamaño de la memoria caché de asignación de sectores lógicos. Los valores grandes mejoran el rendimiento, pero tienen un costo de memoria. El tamaño mínimo es 8 y todos los valores deben ser una potencia de 2.
- **LX_THREAD_SAFE_ENABLE**: definido, esto hace que LevelX sea seguro para subprocesos mediante un objeto de exclusión mutua de ThreadX en toda la API.
- **LX_STANDALONE_ENABLE**: si se define, permite usar LevelX en modo independiente (sin Azure RTOS). De forma predeterminada, este símbolo no está definido.

> [!IMPORTANT]
> Cuando se usa LevelX en modo independiente (se debe definir **LX_STANDALONE_ENABLE**), no se necesitan archivos ni bibliotecas de ThreadX. La característica Seguro para subprocesos de LevelX está deshabilitada en este modo.

## <a name="using-levelx"></a>Uso de LevelX

Para usar LevelX, ya sea por sí mismo o con FileX, incluya el archivo ***lx_api.h** _ en el código que hace referencia a la API de LevelX. Asegúrese también de que el código del objeto de LevelX esté disponible en tiempo de vínculo. Examine los archivos _*_demo_filex_nand_flash.c_*_ y _ *_demo_filex_nor_flash.c_** para obtener ejemplos de cómo usar LevelX.
