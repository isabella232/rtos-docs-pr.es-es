---
title: 'Capítulo 1: Introducción a Azure RTOS FileX'
description: Azure RTOS FileX es un sistema de administración de archivos y soportes físicos de formato FAT completo para las aplicaciones con alto grado de inserción.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48fab21d78ede88e84db11a4f30574ce2061d145820b819ec7846203e297f42a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782975"
---
# <a name="chapter-1---introduction-to-azure-rtos-filex"></a>Capítulo 1: Introducción a Azure RTOS FileX

Azure RTOS FileX es un sistema de administración de archivos y soportes físicos de formato FAT completo para las aplicaciones con alto grado de inserción. En este capítulo se presenta FileX y se describen sus aplicaciones y ventajas.

## <a name="filex-unique-features"></a>Características únicas de FileX

Azure RTOS FileX admite un número ilimitado de soportes físicos al mismo tiempo, incluidos los discos RAM, los administradores de unidades flash y los dispositivos físicos reales. Admite formatos de tabla de asignación de archivos (FAT) de 12, 16 y 32 bits, y también admite la tabla de asignación de archivos extendida (exFAT), la asignación de archivos contigua y está altamente optimizado para el tamaño y el rendimiento. FileX también incluye compatibilidad con tolerancia a errores, apertura/cierre de soportes físicos y funciones de devolución de llamada por escritura de archivo.

Está diseñado para satisfacer la creciente necesidad de unidades flash, por lo que FileX usa los mismos métodos de diseño y codificación que ThreadX. Al igual que todos los productos de Microsoft, FileX se distribuye con código fuente ANSI C completo y no cobra regalías por entorno de ejecución.

### <a name="product-highlights"></a>Aspectos destacados del producto

- Soporte completo del procesador ThreadX
- Sin regalías
- Código fuente ANSI C completo
- Rendimiento en tiempo real
- Soporte técnico con capacidad de respuesta
- Objetos FileX ilimitados (soportes físicos, directorios y archivos)
- Creación/eliminación dinámica de objetos FileX
- Uso de memoria flexible
- Escala automática de tamaño
- Tamaño del área de instrucciones con una superficie de memoria pequeña (hasta 6 KB): 6 a 30 KB
- Integración completa con ThreadX
- Endian neutro
- Controladores de E/S de FileX de fácil implementación
- Compatibilidad con FAT de 12, 16 y 32 bits
- Compatibilidad con exFAT
- Compatibilidad con nombres de archivo largos
- Caché de entrada FAT interna
- Compatibilidad con nombres Unicode
- Asignación de archivos contigua
- Lectura y escritura de clústeres y sectores consecutivos
- Caché del sector lógico interno
- Ejecuciones de la demostración de disco RAM listas para usar
- Capacidad de soporte físico
- Detección de errores y recuperación
- Opciones de tolerancia a errores
- Estadísticas de rendimiento integradas
- Compatibilidad independiente (sin Azure RTOS)

## <a name="safety-certifications"></a>Certificaciones de seguridad

### <a name="tv-certification"></a>Certificación TÜV

FileX está certificado por SG-TÜV Saar para su uso en sistemas críticos para la seguridad, según CEI-61508 y CEI-62304. La certificación confirma que se puede usar FileX en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de la Comisión electrotécnica internacional (CEI) 61508 e CEI 62304 para la "Seguridad funcional de los sistemas eléctricos, electrónicos y electrónicos programables relacionados con la seguridad". SGS-TÜV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TÜV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo. El estándar de seguridad industrial CEI 61508 y todos los estándares que se derivan de él, incluido CEI 62304, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y electrónicos programables relacionados con la seguridad, los sistemas de control de procesos, la maquinaria industrial y los sistemas de control de ferrocarriles.

SGS-TÜV Saar ha certificado FileX para su uso en sistemas de automóviles críticos para la seguridad, según el estándar ISO 26262. Además, FileX está certificado para el nivel D de integridad de la seguridad del automóvil (ASIL), que representa el nivel más alto de la certificación ISO 26262.

Además, SGS-TÜV Saar ha certificado FileX para su uso en aplicaciones ferroviarias críticas para la seguridad, cumpliendo el estándar EN 50128 hasta SW-SIL 4.

![Logotipo de SGS-TÜV Saar](./media/user-guide/sgs-tuv-saar-logo.png)

- CEI 61508 hasta SIL 4
- CEI 62304 hasta seguridad de software clase C
- ISO 26262 ASIL nivel D
- EN 50128 SW-SIL 4

> [!IMPORTANT]
> Póngase en contacto con nosotros para más información sobre qué versiones de FileX están certificadas por TÜV o para la disponibilidad de informes de las pruebas, certificados y documentación asociada.*

### <a name="ul-certification"></a>Certificación UL

FileX ha sido certificado por UL por su conformidad con los estándares de seguridad para software de componentes programables UL 60730-1 anexo H, CSA E60730-1 anexo H, CEI 60730-1 anexo H, UL 60335-1 anexo R, CEI 603351 anexo R y UL 1998. Junto con CEI/UL 60730-1, que tiene requisitos para "Controles que usan software" en el anexo H, el estándar CEI 60335-1 describe los requisitos para "circuitos electrónicos programables" en el anexo R. CEI 60730 en su anexo H y CEI 60335-1 en su anexo R abordan la seguridad del hardware y el software MCU que se usa en dispositivos como lavadoras, lavavajillas, secadoras, frigoríficos, congeladores y hornos.

![Certificación RU US 2](./media/user-guide/c-ru-us-logo.png)

*UL/CEI 60730, UL/CEI 60335, UL 1998*

> [!IMPORTANT]
>*Póngase en contacto con nosotros para más información sobre qué versiones de FileX están certificadas por UL o para la disponibilidad de informes de las pruebas, certificados y documentación asociada.*

## <a name="powerful-services-of-filex"></a>Servicios eficaces de FileX

### <a name="multiple-media-management"></a>Administración de varios soportes físicos

FileX puede admitir un número ilimitado de soportes físicos. Cada instancia de soporte físico tiene su propia área de memoria independiente y el controlador asociado especificado en la llamada ***fx_media_open***. La distribución predeterminada de FileX incluye un controlador de soportes físicos de RAM simple y un sistema de demostración que usa este disco RAM.

### <a name="logical-sector-cache"></a>Caché del sector lógico

Al reducir el número de transferencias del sector completo, tanto recibidas como emitidas por el soporte físico, la memoria caché del sector lógico de FileX mejora significativamente el rendimiento. FileX mantiene una caché de sector lógico para cada soporte físico abierto. La profundidad de la caché del sector lógico viene determinada por la cantidad de memoria proporcionada a FileX con la llamada de API ***fx_media_open***.

### <a name="contiguous-file-support"></a>Compatibilidad con archivos contiguos

FileX ofrece compatibilidad con archivos contiguos a través del servicio de API ***fx_file_allocate*** para que el tiempo de acceso a los archivos sea determinista y mejor. Esta rutina toma la cantidad de memoria solicitada y busca una serie de clústeres adyacentes para cumplir los requisitos de la solicitud. Si se encuentran clústeres de estas características, se asignan previamente al incluirlos en le cadena de clústeres asignados del archivo. En el traslado de soportes físicos, la compatibilidad con archivos contiguos de FileX tiene como resultado una mejora significativa del rendimiento y hace que el tiempo de acceso sea determinista.

### <a name="dynamic-creation"></a>Creación dinámica

FileX permite crear recursos del sistema de manera dinámica. Esto es particularmente importante si la aplicación tiene varios requisitos de configuración o son dinámicos. Además, no hay ningún límite predeterminado para el número de recursos de FileX que puede usar (soportes físicos o archivos). Además, el número de objetos del sistema no afecta al rendimiento.

## <a name="easy-to-use-api"></a>API fáciles de usar

FileX ofrece la mejor tecnología de sistema de archivos con alto grado de inserción de una manera fácil de entender y de usar. La interfaz de programación de aplicaciones (API) de FileX hace que los servicios sean intuitivos y coherentes. No tendrá que descifrar los servicios de "sopa de letras" que son tan comunes con otros sistemas de archivos.

Para obtener una lista completa de los servicios de FileX versión 5, consulte el [Apéndice A](appendix-a.md).

## <a name="exfat-support"></a>Compatibilidad con exFAT

exFAT (tabla de asignación de archivos extendida) es un sistema de archivos diseñado por Microsoft para que el tamaño de los archivos pueda superar los 2 GB, que es el límite impuesto por los sistemas de archivos FAT32. Es el sistema de archivos predeterminado para las tarjetas SD con una capacidad superior a 32 GB. Las tarjetas SD o unidades flash USB con el formato exFAT de FileX son compatibles con Windows. exFAT admite un tamaño de archivo de hasta un exabyte (EB), que es aproximadamente de mil millones de GB.

Los usuarios que quieran usar exFAT deben volver a compilar la biblioteca de FileX con el símbolo ***FX_ENABLE_EXFAT** _ definido. Al abrir un soporte físico, FileX detecta su tipo. Si el soporte físico se formatea con exFAT, FileX lee y escribe el sistema de archivos según el estándar exFAT. Para dar formato a soportes físicos nuevos con exFAT, use el servicio _*_fx_media_exFAT_format_**. De manera predeterminada, exFAT no está habilitado.

## <a name="fault-tolerant-support"></a>Compatibilidad con tolerancia a errores

El módulo de tolerancia a errores de FileX está diseñado para evitar daños en el sistema de archivos que sean ocasionados por interrupciones durante la actualización de archivos o directorios. Por ejemplo, al anexar datos a un archivo, FileX necesita actualizar el contenido del archivo, la entrada del directorio y, posiblemente, las entradas FAT. Si se interrumpe esta secuencia de actualización (por ejemplo, se genera un problema de alimentación o se expulsa el soporte físico durante la actualización), el sistema de archivos se encuentra en un estado incoherente, lo que puede afectar a la integridad de todo el sistema de archivos y provocar daños en otros archivos.

El módulo de tolerancia a errores de FileX graba todos los pasos necesarios para actualizar un archivo o un directorio a lo largo del proceso. Esta entrada de registro se almacena en el soporte físico en sectores dedicados (bloques) que FileX puede buscar y acceder. Puede acceder a la ubicación de los datos de registro incluso si no hay un sistema de archivos adecuado. Por lo tanto, en caso de que el sistema de archivos esté dañado, FileX aún podrá buscar la entrada de registro y volver a restaurar el sistema de archivos a un estado correcto.

Cuando FileX actualiza el archivo o el directorio, se crean las entradas de registro. Una vez completada correctamente la operación de actualización, se quitan las entradas del registro. Si las entradas del registro no se quitaron correctamente después de una actualización correcta del archivo y el proceso de recuperación determina que el contenido de la entrada del registro coincide con el sistema de archivos, no es necesario hacer nada y se pueden limpiar las entradas del registro.

Si se interrumpiera la operación de actualización del sistema de archivos, la próxima vez que FileX monte el soporte físico, el módulo de tolerancia a errores analizará las entradas del registro. La información de las entradas del registro permite que FileX revierta los cambios parciales ya aplicados al sistema de archivos (en caso de que el error se produzca durante una fase temprana de la operación de actualización de archivos). Además, si las entradas del registro contienen información de repetición, FileX puede aplicar los cambios necesarios para finalizar la operación anterior.

La característica de tolerancia a errores de FileX está disponible para todos los sistemas de archivos FAT compatibles con FileX, como FAT12, FAT16, FAT32 y exFAT. De manera predeterminada, la tolerancia a errores no está habilitada en FileX. Para habilitar la característica de tolerancia a errores, FileX se debe crear con el símbolo **FX_ENABLE_FAULT_TOLERANT** y **FX_FAULT_TOLERANT** definido. En el tiempo de ejecución, la aplicación inicia el servicio de tolerancia a errores mediante una llamada a **_fx_fault_tolerant_enable_**.
Una vez iniciado el servicio, todas las operaciones de escritura de archivos y directorios pasan por el módulo de tolerancia a errores.

A medida que se inicia el servicio de tolerancia a errores, primero detecta si el soporte físico está protegido o no en el módulo de tolerancia a errores. Si no es así, FileX asume la integridad del sistema de archivos e inicia la protección mediante la asignación de bloques libres del sistema de archivos que se usarán para el registro y el almacenamiento en caché. Si los registros del módulo de tolerancia a errores se encuentran en el sistema de archivos, analiza las entradas del registro. FileX revierte la operación anterior o vuelve a realizar la operación anterior, según el contenido de las entradas del registro. El sistema de archivos está disponible una vez procesadas todas las entradas de registro anteriores. Esto garantiza que FIleX se inicia a partir de un estado correcto conocido.

Después de proteger un soporte físico en el módulo de tolerancia a errores de FileX, dicho soporte físico no se actualizará con otro sistema de archivos. Si lo actualiza de esta manera, las entradas de registro en el sistema de archivos no serán coherentes con el contenido de la tabla FAT, la entrada de directorio. Si el soporte físico se actualiza por otro sistema de archivos antes de trasladarlo de vuelta a FileX con el módulo de tolerancia a errores, el resultado es indefinido.

## <a name="callback-functions"></a>Funciones de devolución de llamada

Las tres funciones de devolución de llamada siguientes se agregaron a FileX:

- Devolución de llamada de apertura de soporte físico
- Devolución de llamada de cierre de soporte físico
- Devolución de llamada de escritura en archivo

Tras su registro, estas funciones notificarán a la aplicación cuando se produzcan dichos eventos.

## <a name="easy-integration"></a>Fácil integración

FileX se integra fácilmente con prácticamente cualquier unidad flash o soporte físico. La portabilidad de FileX es sencilla. En esta guía se describe el proceso de manera detallada y el controlador de RAM del sistema de demostración hace que sea un buen punto de partida.
