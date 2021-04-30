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
# <a name="overview-of-azure-rtos-filex"></a>Información general sobre Azure RTOS FileX

El sistema de archivos incrustados de Azure RTOS FileX es la solución avanzada de nivel industrial de Azure RTOS para los formatos de archivo FAT de Microsoft, diseñada específicamente para aplicaciones de IoT, en tiempo real e integradas. Azure RTOS FileX admite todos los formatos de archivo de Microsoft, incluidos FAT12, FAT16, FAT32 y exFAT. FileX también ofrece tolerancia a errores y redistribución de uso de FLASH opcional a través de un producto complementario llamado [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/). Todo esto, combinado con una pequeña superficie, una ejecución rápida y una facilidad de uso superior, hacen que Azure RTOS FileX sea la opción ideal para las aplicaciones IoT insertadas más exigentes.

## <a name="api-protocols"></a>Protocolos de API

### <a name="azure-rtos-filex-api"></a>API Azure RTOS FileX

- API intuitivas y coherentes
- Convención de nomenclatura sustantivo-verbo
- Todas las API tienen un *fx_* al inicio para identificarlas fácilmente como FileX
- Las API de bloqueo tienen un tiempo de espera de subprocesos opcional
- Devoluciones de llamada de notificación de usuario opcionales para operaciones de archivos y medios
- Consulte la [Guía de usuario de Azure RTOS FileX](about-this-guide.md) para obtener más información

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

## <a name="small-footprint"></a>Superficie pequeña

El sistema de archivos incrustados de Azure RTOS FileX tiene una superficie mínima considerablemente pequeña de 8,6 KB a 12 KB para la compatibilidad con lectura y escritura de archivos básicos. El uso mínimo de RAM de Azure RTOS FileX es del orden de 1,8 KB para una instancia de medios y con solo una caché de sector lógico de 512 bytes. Al igual que Azure RTOS ThreadX, el tamaño de Azure RTOS FileX se escala automáticamente en función de los servicios que usa la aplicación. Esto elimina prácticamente la necesidad de configuraciones y parámetros de compilación complicados, lo que facilita el trabajo del desarrollador.

## <a name="fast-execution"></a>Ejecución rápida

Azure RTOS FileX proporciona una caché del sector lógico, así como una caché de entrada de FAT. La aplicación controla directamente ambos tamaños. Además, Azure RTOS FileX permite la asignación de clústeres contiguos y la lectura y escritura directa de clústeres consecutivos. Las solicitudes de lectura y escritura de sectores completos se realizan directamente entre el búfer de la aplicación y los medios. Por tanto, no se realiza un almacenamiento en búfer intermedio. Todo esto y una filosofía general de diseño orientada al rendimiento ayudan a Azure RTOS FileX a lograr el rendimiento más rápido posible.

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

## <a name="fastest-time-to-market"></a>Tiempo de comercialización más rápido

Azure RTOS FileX es fácil de instalar, conocer, usar, depurar, comprobar, certificar y mantener. Por lo tanto, Azure RTOS FileX es uno de los sistemas de archivos FAT más populares para dispositivos IoT insertados. A continuación se indican algunas razones del ventajoso tiempo de comercialización:

- Documentación de calidad: consulte nuestra [Guía de usuario de Azure RTOS FileX](about-this-guide.md) y véalo usted mismo.
- Disponibilidad completa del código fuente
- API fáciles de usar
- Conjunto de características completo y avanzado

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>Certificado previamente por TUV y UL para varios estándares de seguridad

![SGS-TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

Azure RTOS FileX ha sido certificado por los SG-TUV Saar para su uso en sistemas críticos para la seguridad, según CEI-61508 SIL 4, CEI-62304 SW Clase de seguridad C, ISO 26262 ASIL D y EN 50128. La certificación confirma que FileX se puede usar en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de CEI-61508, CEI-62304, ISO 26262 y EN 50128 para la "seguridad funcional de sistemas relacionados con la seguridad electrónica de electricidad, electrónica y programable". SG-TUV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TUV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo. El estándar de seguridad industrial CEI 61508, y todos los estándares que se derivan de él, incluidos CEI-62304, ISO 26262 y EN 50128, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y programables relacionados con la seguridad electrónica, los sistemas de control de procesos, la maquinaria industrial, los automóviles y los sistemas de control de ferrocarriles.

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="Certificación UL CRU":::

Azure RTOS FileX ha sido reconocido por UL por su conformidad con los estándares de seguridad para software de componentes programables UL 60730-1 anexo H, CSA E60730-1 anexo H, CEI 60730-1 anexo H, UL 60335-1 anexo R, CEI 60335-1 anexo R y UL 1998. UL es una empresa global e independiente especializada en la seguridad en la ciencia con más de un siglo de experiencia aportando innovaciones en soluciones de seguridad que abarcan desde la adopción pública de electricidad hasta los avances en sostenibilidad, energías renovables y nanotecnología.

Los artefactos (certificado, manual de seguridad, informe de pruebas, etc.) asociados a las certificaciones TUV y UL están disponibles para su venta.

En los casos en los que la aplicación necesite certificación adicional, hay un servicio de certificación disponible con Microsoft para proporcionar una certificación llave en mano para varios estándares con la plataforma de hardware real e incluso abarcando el código de la aplicación.

## <a name="one-simple-license"></a>Una licencia sencilla

No hay ningún costo asociado al uso y las pruebas del código fuente ni a las licencias de producción si se implementa en dispositivos con licencia previa; todos los demás dispositivos necesitan una licencia anual sencilla.

## <a name="full-highest-quality-source-code"></a>Código fuente completo y de máxima calidad

A lo largo de los años, el código fuente de FileX ha establecido el estándar de calidad y facilidad de comprensión. Además, la convención de tener una función por archivo facilita la navegación por el origen.

## <a name="supports-most-popular-architectures"></a>Compatible con las arquitecturas más populares

Azure RTOS FileX se ejecuta en los microprocesadores de 32 o 64 bits más populares, de serie, totalmente probado y totalmente compatible, lo que incluye lo siguiente:

**Dispositivos analógicos**: SHARC, Blackfin, CM4xx

**Andes Core**: RISC-V

**Ambiqmicro**: Apollo MCU

**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Cadence**: Xtensa, Diamond

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

**Cypress**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10

**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Synergy

**Silicon** Labs: EFM32

**Synopsys**: ARC 600, 700, ARC EM, ARC HS

**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Todas las cifras de tiempos y tamaños enumeradas son estimaciones y pueden ser diferentes en su plataforma de desarrollo.*
