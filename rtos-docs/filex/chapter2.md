---
title: 'Capítulo 2: Instalación y uso de Azure RTOS FileX'
description: Este capítulo contiene una introducción a Azure RTOS FileX y una descripción de las condiciones de instalación, los procedimientos y el uso, incluidos los siguientes
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6703b10d8e0895984bb92d74d5dff809dca1a7f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814393"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-filex"></a>Capítulo 2: Instalación y uso de Azure RTOS FileX

Este capítulo contiene una introducción a Azure RTOS FileX y una descripción de las condiciones de instalación, los procedimientos y el uso. 

## <a name="host-considerations"></a>Consideraciones sobre el host

### <a name="computer-type"></a>Tipo de equipo

El desarrollo insertado normalmente se realiza en equipos host Windows o Linux (Unix). Una vez que la aplicación está compilada, vinculada y colocada en el host, se descarga en el hardware de destino para su ejecución.

### <a name="download-interfaces"></a>Interfaces de descarga

Normalmente, la descarga del destino se realiza desde el depurador de la herramienta de desarrollo. Después de la descarga, el depurador es responsable de proporcionar el control de ejecución de destino (ir, detener, punto de interrupción, etc.), así como el acceso a los registros de memoria y del procesador.

### <a name="debugging-tools"></a>Herramientas de depuración

La mayoría de los depuradores de herramientas de desarrollo se comunican con el hardware de destino mediante conexiones de depuración en chip (OCD), como JTAG (IEEE 1149.1) y el modo de depuración en segundo plano (BDM). Los depuradores también se comunican con el hardware de destino mediante conexiones de emulación en el circuito (ICE). Las conexiones OCD e ICE proporcionan soluciones sólidas con una intrusión mínima en el software residente de destino.

### <a name="required-hard-disk-space"></a>Espacio en disco duro requerido

El código fuente de FileX se distribuye en formato ASCII y requiere aproximadamente 500 KB de espacio en el disco duro del equipo host.

## <a name="target-considerations"></a>Consideraciones sobre el destino

FileX requiere entre 6 KB y 30 KB de memoria de solo lectura (ROM) en el destino. Se requieren otros 100 bytes de memoria de acceso aleatorio (RAM) del destino para las estructuras de datos globales de FileX. Cada medio abierto también requiere 1,5 KBytes de RAM para el bloque de control además de la memoria RAM para almacenar los datos de un sector (normalmente 512 bytes).

Para que la marca de fecha y hora funcione correctamente, FileX se basa en las instalaciones del temporizador de ThreadX. Esto se implementa mediante la creación de un temporizador específico de FileX durante la inicialización de FileX. FileX también se basa en semáforos de ThreadX para la protección de varios subprocesos y la suspensión de E/S.

## <a name="product-distribution"></a>Distribución del producto

Azure RTOS FileX se puede obtener desde el repositorio de código fuente público en <https://github.com/azure-rtos/filex/>.

A continuación se muestra una lista de varios archivos importantes del repositorio:

- ***fx_api.h***: Este archivo de encabezado de C contiene todas las equivalencias del sistema, estructuras de datos y prototipos del servicio.
- ***fx_port.h***: Este archivo de encabezado de C contiene todas las definiciones de datos y estructuras específicas de la herramienta de desarrollo.
- ***demo_filex.c***: Este archivo de C contiene una pequeña aplicación de demostración.
- ***fx.a (o fx.lib)***: Se trata de la versión binaria de la biblioteca de C de FileX. Se distribuye con el paquete estándar.

> [!IMPORTANT]
> *Todos los nombres de archivo están en minúsculas. Esta convención de nomenclatura facilita la conversión de los comandos para plataformas de desarrollo Linux (Unix).*

## <a name="filex-installation"></a>Instalación de FileX

FileX se instala mediante la clonación del repositorio de GitHub en el equipo local. La siguiente es la sintaxis típica para la creación de un clon del repositorio de FileX en el equipo:

```c
    git clone https://github.com/azure-rtos/filex
```

También se puede descargar una copia del repositorio mediante el botón Descargar de la página principal de GitHub.

Además, hay instrucciones para compilar la biblioteca de FileX en la página principal del repositorio en línea.

> [!IMPORTANT]
> El software de aplicación necesita acceso al archivo de biblioteca FileX (normalmente denominado ***fx.a** _ o _*_fx.lib_*_)_ y los archivos de inclusión de C **fx_api.h** y **fx_port.h**. Esto se logra estableciendo la ruta de acceso adecuada para las herramientas de desarrollo o copiando estos archivos en el área de desarrollo de la aplicación.

## <a name="using-filex"></a>Uso de FileX

El uso de FileX es sencillo. Básicamente, el código de la aplicación debe incluir ***fx_api.h** _ durante la compilación y vincularse con la biblioteca en tiempo de ejecución de FileX _*_fx.a_*_ (o _*_fx.lib_*_). Por supuesto, los archivos ThreadX, es decir, _*_tx_api.h_*_ y _*_tx.a_*_ (o _*_tx.lib_*_)_,* también son obligatorios.

> [!IMPORTANT]
> Cuando se usa FileX en modo independiente (se debe definir **FX_STANDALONE_ENABLE**), no se necesitan archivos ni bibliotecas de ThreadX.

Suponiendo que ya usa ThreadX, hay cuatro pasos necesarios para compilar una aplicación de FileX:

1. Incluya el archivo ***fx_api.h*** en todos los archivos de la aplicación que usen servicios o estructuras de datos de FileX.
1. Inicialice el sistema FileX llamando a ***fx_system_initialize** _ desde la función _ *_tx_application_define_** o un subproceso de aplicación.

    > [!IMPORTANT]
    > Al usar FileX en modo independiente, se debe llamar a ***fx_system_initialize*** directamente desde el código de la aplicación.

1. Agregue una o varias llamadas a ***fx_media_open*** para configurar el medio FileX. Esta llamada debe realizarse desde el contexto de un subproceso de aplicación.

    > [!IMPORTANT]
    > *Recuerde que la llamada a **fx_media_open** requiere suficiente RAM para almacenar los datos de un sector.*

1. Compile el origen de la aplicación y vincúlelo con las bibliotecas en tiempo de ejecución de FileX y ThreadX, ***fx.a** _ (o _*_fx.lib_*_) y _*_tx.a_*_ (o _*_tx.lib_**). La imagen resultante se puede descargar en el destino y ejecutarse.

## <a name="troubleshooting"></a>Solución de problemas

Cada puerto de FileX se entrega con una aplicación de demostración. Siempre es conveniente que el sistema de demostración se ejecute en primer lugar, ya sea en el hardware de destino o en un entorno de demostración específico.

Si el sistema de demostración no funciona, pruebe los siguientes pasos para delimitar el problema:

1. Determine qué parte de la demostración se está ejecutando.
1. Aumente los tamaños de pila (esto es más importante en el código de aplicación real que en el de demostración).
1. Asegúrese de que haya suficiente memoria RAM para el tamaño de disco de RAM predeterminado de 32 KBytes. El sistema básico funcionará con mucha menos RAM; sin embargo, a medida que se use más el disco RAM, aparecerán problemas si no hay suficiente memoria.
1. Omita temporalmente los cambios recientes para ver si el problema desaparece o cambia. Esta información debería resultar útil para los ingenieros de soporte técnico de Microsoft. Siga los procedimientos descritos en "Centro de atención al cliente" para enviar la información recopilada en los pasos de solución de problemas.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración al compilar la biblioteca de FileX y la aplicación mediante FileX. Las opciones siguientes se pueden definir en el código fuente de la aplicación, en la línea de comandos o en el archivo de inclusión ***fx_user.h***.

> [!IMPORTANT]
> *Las opciones definidas en **fx_user.h** solo se aplican si la aplicación y la biblioteca de ThreadX se compilan con **_FX_INCLUDE_USER_DEFINE_FILE_*_ definido._ Cuando se usa FileX en modo independiente (debe estar definido** FX_STANDALONE_ENABLE*), no se necesitan archivos ni bibliotecas de ThreadX.

En la lista siguiente se describen detalladamente las opciones de configuración:

|Definir|Significado|
|----------    |-----------|
|FX_MAX_LAST_NAME_LEN        |Este valor define la longitud máxima del nombre de archivo, que incluye el nombre de la ruta de acceso completa. De forma predeterminada, este valor es 256.|
|FX_DONT_UPDATE_OPEN_FILES    |Si se define, FileX no actualiza los archivos ya abiertos.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Si se define, la optimización de la caché de búsqueda de archivos está deshabilitada.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Si se define, la optimización de la caché de búsqueda de archivos está deshabilitada.|
|FX_DISABLE_DIRECT_DATA_READ_CACHE_FILL |Si se define, la actualización directa del sector de lectura de la memoria caché está deshabilitada.|
|FX_MEDIA_STATISTICS_DISABLE |Si se define, la recopilación de estadísticas multimedia está deshabilitada.|
|FX_SINGLE_OPEN_LEGACY |Si se define, la lógica de apertura única heredada para el mismo archivo está habilitada.|
|FX_RENAME_PATH_INHERIT    |Si se define, el cambio de nombre hereda la información de la ruta de acceso.|
|FX_DISABLE_ERROR_CHECKING    |Quita la API de comprobación de errores de FileX básica y da como resultado un rendimiento mejorado (hasta un 30 %) y un tamaño de código más pequeño.|
|FX_MAX_LONG_NAME_LEN    |Especifica el tamaño máximo del nombre de archivo de FileX. El valor predeterminado es 256, pero se puede invalidar con una definición de línea de comandos. Los valores válidos oscilan entre 13 y 256.|
|FX_MAX_SECTOR_CACHE|Especifica el número máximo de sectores lógicos que se pueden almacenar en caché por FileX. El número real de sectores que se pueden almacenar en la caché es el menor de esta constante y de cuántos sectores pueden caber en la cantidad de memoria suministrada en fx_media_open. El valor predeterminado es 256. Todos los valores deben ser una potencia de 2.|
|FX_FAT_MAP_SIZE    |Especifica el número de sectores que se pueden representar en la asignación de actualización de FAT. El valor predeterminado es 256, pero se puede invalidar con una definición de línea de comandos. Los valores más grandes ayudan a reducir las actualizaciones innecesarias de los sectores FAT secundarios.|
|FX_MAX_FAT_CACHE    |Especifica el número de entradas en la memoria caché de FAT interna. El valor predeterminado es 16, pero se puede invalidar con una definición de línea de comandos. Todos los valores deben ser una potencia de 2.|
|FX_FAULT_TOLERANT    |Si se define, FileX pasa inmediatamente las solicitudes de escritura de todos los sectores del sistema (sectores de arranque, FAT y de directorio) al controlador del medio. Esto puede disminuir el rendimiento, pero ayuda a limitar los daños a los clústeres perdidos. Tenga en cuenta que la habilitación de esta característica no habilita automáticamente el módulo de tolerancia a errores de FileX, que se habilita mediante la definición de|
|FX_FAULT_TOLERANT_DATA    |Si se define, FileX pasa inmediatamente todas las solicitudes de escritura de datos de archivos al controlador del medio. Esto puede disminuir el rendimiento, pero ayuda a limitar los datos de archivos perdidos. Tenga en cuenta que la habilitación de esta característica no habilita automáticamente el módulo de tolerancia a errores de FileX, que se habilita mediante la definición de ***FX_ENABLE_FAULT_TOLERANT***.|
|FX_NO_LOCAL_PATH|Quita la lógica de la ruta de acceso local de FileX, lo que da lugar a un tamaño de código más pequeño.|
|FX_NO_TIMER|Elimina la configuración del temporizador de ThreadX para actualizar la fecha y hora del sistema de FileX. Si lo hace, la fecha y la hora predeterminadas se colocarán en todas las operaciones de archivo.|
|FX_UPDATE_RATE_IN_SECONDS    |Especifica la frecuencia a la que se ajusta la hora del sistema en FileX. De forma predeterminada, el valor es 10, lo que especifica que la hora del sistema FileX se actualiza cada 10 segundos.|
|FX_ENABLE_EXFAT| Cuando se define, la lógica para controlar el sistema de archivos de exFAT se habilita en FileX. De forma predeterminada, este símbolo no está definido.| 
|FX_UPDATE_RATE_IN_TICKS| Especifica la misma frecuencia que ***FX_UPDATE_RATE_IN_SECONDS*** (vea más arriba), excepto en lo que se refiere a la frecuencia del temporizador de ThreadX subyacente. El valor predeterminado es 1000, que supone una tasa de temporizador de ThreadX de 10 ms y un intervalo de 10 segundos.|
|FX_SINGLE_THREAD|Elimina la lógica de protección de ThreadX del origen de FileX. Se debe usar si FileX solo se usa desde un subproceso o si FileX se usa sin ThreadX.|
|FX_DRIVER_USE_64BIT_LBA|Si se define, habilita las direcciones del sector de 64 bits usadas en el controlador de E/S. De manera predeterminada, esta opción no está definida.|
|FX_ENABLE_FAULT_TOLERANT| Si se define, habilita el módulo de tolerancia a errores de FileX. Al habilitar la tolerancia a errores se define automáticamente el símbolo ***FX_FAULT_TOLERANT** _ y _*_FX_FAULT_TOLERANT_DATA_**. De manera predeterminada, esta opción no está definida.|
|FX_FAULT_TOLERANT_BOOT_INDEX|Define el desplazamiento de bytes en el sector de arranque en el que se encuentra el clúster para el registro de tolerancia a errores. De manera predeterminada, este valor es 116. Este campo toma 4 bytes. Los bytes 116 a 119 se eligen porque están marcados como reservados por la especificación 12/16/32/exFAT de FAT.|
|FX_FAULT_TOLERANT_MINIMAL_CLUSTER|Este símbolo está en desuso. La tolerancia a errores de FileX ya no lo utiliza.|
|FX_STANDALONE_ENABLE|Si se define, permite usar FileX en modo independiente (sin Azure RTOS). De forma predeterminada, este símbolo no está definido.|

> [!IMPORTANT]
> Si se define **FX_STANDALONE_ENABLE**, la lógica de la ruta de acceso local y la configuración del temporizador de ThreadX están deshabilitadas.

## <a name="filex-version-id"></a>Id. de la versión de FileX

La versión actual de FileX está disponible tanto para el software de usuario como para el de aplicación durante el tiempo de ejecución. El programador puede obtener la versión de FileX si examina el archivo **fx_port.h**. Además, este archivo también contiene un historial de versiones del puerto correspondiente. El software de la aplicación puede obtener la versión de FileX mediante el examen de la cadena global **_ _fx_version_id_**.
