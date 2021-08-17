---
title: Información general sobre Azure RTOS FileX
description: Azure RTOS FileX es un sistema de archivos de alto rendimiento compatible con la tabla de asignación de archivos (FAT) que está totalmente integrado con Azure RTO ThreadX y está disponible para todos los procesadores compatibles. Al igual que Azure RTO ThreadX, Azure RTOS FileX está diseñado para ocupar poca superficie de memoria y proporcionar un alto rendimiento, lo que lo convierte en una opción ideal para las actuales aplicaciones profundamente insertadas, que requieren operaciones de administración de archivos. FileX admite la mayoría de los soportes físicos, como la memoria RAM, Azure RTOS USBX, tarjeta SD y memorias Flash NAND/NOR a través de Azure RTO LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 399586eca18ef9345b94cc577bdacbf3c3a591bcd22b474b4e3d4ca4eefb4432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782860"
---
# <a name="overview-of-azure-rtos-filex"></a>Información general sobre Azure RTOS FileX

El sistema de archivos incrustados de Azure RTOS FileX es la solución avanzada de nivel industrial de Azure RTOS para los formatos de archivo FAT de Microsoft, diseñada específicamente para aplicaciones de IoT, en tiempo real e integradas. Azure RTOS FileX admite todos los formatos de archivo de Microsoft, incluidos FAT12, FAT16, FAT32 y exFAT. FileX también ofrece tolerancia a errores y redistribución de uso de FLASH opcional a través de un producto complementario llamado [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/). Todo esto, combinado con una pequeña superficie, una ejecución rápida y una facilidad de uso superior, hacen que Azure RTOS FileX sea la opción ideal para las aplicaciones IoT insertadas más exigentes.

## <a name="api-protocols"></a>Protocolos de API

### <a name="media-services"></a>Media Services

- Compatibilidad con FAT 12/16/32 y exFAT
- Memoria FLASH mínima de 6 KB y 2,5 KB de RAM
- Servicios completos de acceso a medios
- Número ilimitado de instancias de medios
- Interfaz de controlador de sector lógico de lectura/escritura simple
- Compatibilidad con varias particiones
- Caché del sector lógico
- Caché de entrada FAT
- Compatibilidad con tolerancia a errores opcional
- Actualización diferida del sistema de archivos FAT secundario
- Seguimiento de nivel de sistema mediante Azure RTOS TraceX
- API intuitivas de acceso a medios, que incluyen:
  - fx_media_open
  - fx_media_close
  - fx_media_format
  - fx_media_space_available

### <a name="directory-services"></a>Servicios de directorio

- Rutas de acceso de hasta 256 bytes
- Se admiten nombres largos y de directorio 8.3
- Creación y eliminación de directorios
- Navegación y recorrido de directorios
- Administración de atributos de directorios
- Seguimiento de nivel de sistema mediante Azure RTOS TraceX
- API intuitivas de acceso a directorios, que incluyen:
  - fx_directory_create
  - fx_directory_delete
  - fx_directory_attributes_set
  - fx_directory_attributes_read
  - fx_directory_first_entry_find
  - fx_directory_next_entry_find

### <a name="file-services"></a>Servicios de archivos

- Memoria FLASH mínima de 3,3 KB
- Archivos abiertos ilimitados
- Los archivos de solo lectura se pueden abrir varias veces
- Se admiten nombres largos y de directorio 8.3
- Compatibilidad con archivos contiguos
- Lógica de búsqueda rápida
- Asignación previa de clústeres
- Creación, eliminación y cambio de nombre de archivos
- Lectura, escritura y visualización de archivos
- Administración de atributos de archivo
- Seguimiento de nivel de sistema mediante Azure RTOS TraceX
- API intuitivas de acceso a archivos, que incluyen:
  - fx_file_create
  - fx_file_delete
  - fx_file_attributes_set
  - fx_file_attributes_read
  - fx_file_read
  - fx_file_seek
  - fx_file_write

## <a name="advanced-technology"></a>Tecnología avanzada

Azure RTOS FileX es tecnología avanzada que incluye lo siguiente.

- Compatibilidad con FAT 12/16/32 y exFAT
- Compatibilidad con varias particiones
- Escalado automático
- Endian neutro
- Soporte para nombres de archivo largos y 8.3
- Compatibilidad con tolerancia a errores opcional
- Caché del sector lógico
- Caché de entrada FAT
- Asignación previa de clústeres
- Compatibilidad con archivos contiguos
- Métricas de rendimiento opcionales
- Compatibilidad con el análisis del sistema de Azure RTOS TraceX

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a>Distribución del uso de la memoria NOR / NAND (Azure RTOS LevelX)

Azure RTOS LevelX es el producto de distribución del uso de memoria NOR / NAND FLASH de Microsoft. Azure RTOS LevelX se puede usar con FileX o como una biblioteca independiente de sectores FLASH de lectura / escritura directa para la aplicación.
