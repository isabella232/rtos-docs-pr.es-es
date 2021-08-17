---
title: 'Capítulo 6: Módulo de tolerancia a errores de Azure RTOS FileX'
description: Este capítulo contiene una descripción del módulo de tolerancia a errores de Azure RTOS FileX que está diseñado para mantener la integridad del sistema de archivos si el soporte físico pierde energía o se expulsa en mitad de una operación de escritura de archivo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 66bffa2dbf52bc458bfaf124aa006a79e810100ac2e926c17444daf090519e66
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783792"
---
# <a name="chapter-6---azure-rtos-filex-fault-tolerant-module"></a>Capítulo 6: Módulo de tolerancia a errores de Azure RTOS FileX

Este capítulo contiene una descripción del módulo de tolerancia a errores de Azure RTOS FileX que está diseñado para mantener la integridad del sistema de archivos si el soporte físico pierde energía o se expulsa en mitad de una operación de escritura de archivo.

## <a name="filex-fault-tolerant-module-overview"></a>Información general del módulo de tolerancia a errores de FileX

Cuando una aplicación escribe datos en un archivo, FileX actualiza los clústeres de datos y la información del sistema. Estas actualizaciones se deben completar como una operación atómica para mantener coherente la información en el sistema de archivos. Por ejemplo, al anexar datos a un archivo, FileX necesita encontrar un clúster disponible en el soporte físico, actualizar la cadena FAT, actualizar la longitud presentada en la entrada de directorio y, posiblemente, actualizar el número de clúster de inicio en la entrada del directorio. Un error de potencia o una extracción del soporte físico pueden interrumpir la secuencia de actualizaciones, lo que dejará el sistema de archivos en un estado incoherente. Si no se corrige el estado incoherente, se pueden perder los datos que se están actualizando y, debido a los daños en la información del sistema, la operación posterior del sistema de archivos puede dañar otros archivos o directorios del soporte físico.

El módulo de tolerancia a errores de FileX funciona con los pasos de registro en diario necesarios para actualizar un archivo *antes* de que estos pasos se apliquen en el sistema de archivos. Si la actualización del archivo se realiza correctamente, se quitan las entradas de registro. Sin embargo, si se interrumpe la actualización del archivo, las entradas de registro se almacenan en el soporte físico. La próxima vez que se monte el soporte físico, FileX detectará estas entradas de registro de la operación de escritura anterior (sin terminar). En tales casos, FileX puede recuperarse de un error revirtiendo los cambios ya realizados en el sistema de archivos o volviendo a aplicar los cambios necesarios para completar la operación anterior. De esta manera, el módulo de tolerancia a errores de FileX mantiene la integridad del sistema de archivos si el soporte físico pierde energía durante una operación de actualización.

> [!IMPORTANT]
> *El módulo de tolerancia a errores de FileX no está diseñado para evitar daños en el sistema de archivos causados por daños en soportes físicos con datos válidos.*

> [!IMPORTANT]
> *Después de que el módulo de tolerancia a errores de FileX proteja un soporte físico, este soporte físico solo debe montarse con FileX con la tolerancia a errores habilitada. Si no, las entradas de registro del sistema de archivos pueden no ser coherentes con la información del sistema en el soporte físico. Si el módulo de tolerancia a errores de FileX intenta procesar las entradas de registro después de que otro sistema de archivos actualice el soporte físico, el procedimiento de recuperación puede producir un error, lo que dejaría todo el sistema de archivos en un estado impredecible.*

## <a name="use-of-the-fault-tolerant-module"></a>Uso del módulo de tolerancia a errores

La característica de tolerancia a errores de FileX está disponible para todos los sistemas de archivos FAT soportados por FileX, como FAT12, FAT16, FAT32 y exFAT. Para habilitar la característica de tolerancia a errores, FileX se debe crear con el símbolo **FX_ENABLE_FAULT_TOLERANT** definido. En el tiempo de ejecución, la aplicación inicia el servicio de tolerancia a errores mediante una llamada a **_fx_fault_tolerant_enable_ *_ inmediatamente después de la llamada a _* _fx_media_open_**. Una vez habilitada la tolerancia a errores, se protegen todas las operaciones de escritura de archivos en los soportes físicos designados. De forma predeterminada, el módulo de tolerancia a errores no está habilitado.

> [!IMPORTANT]
> *La aplicación debe asegurarse de que no se tiene acceso al sistema de archivos antes de la llamada a ***fx_fault_tolerant_enable** _. Si la aplicación escribe datos en el sistema de archivos antes de la habilitación de tolerancia a errores, la operación de escritura podría dañar el soporte físico si no se completaron las operaciones de escritura anteriores y el sistema de archivos no se restauró mediante las entradas de registro de tolerancia a errores._

## <a name="filex-fault-tolerant-module-log"></a>Módulo de tolerancia a errores de FileX

El registro de tolerancia a errores de FileX usa un clúster lógico en flash. El índice para el número de clústeres de inicio de ese clúster se registra en el sector de arranque del soporte físico, con un desplazamiento especificado por el símbolo **FX_FAULT_TOLERANT_BOOT_INDEX**. De forma predeterminada, este símbolo está definido como 116. Esta ubicación se elige porque está marcada como reservada en las especificaciones FAT12/16/32 y exFAT.

En la figura 5, "diseño de la estructura del registro", se muestra el diseño general de la estructura del registro. La estructura del registro contiene tres secciones: encabezado del registro, cadena FAT y entradas de registro.

> [!IMPORTANT]
> *Todos los valores multibyte almacenados en las entradas de registro están en formato Little Endian.*

![Diseño de la estructura del registro](./media/user-guide/log-structure-layout.png)

**Figura 5. Diseño de la estructura del registro**

El área de encabezado del registro contiene información que describe la estructura del registro completa y explica detalladamente cada campo.

**TABLA 8. Área de encabezado del registro**

|Campo|Tamaño (en bytes)|Descripción|
|-----|--------------|-----------|
|ID|4|Identifica una estructura del registro de tolerancia a errores de FileX. La estructura del registro no se considera válida si el valor de id. no es 0x46544C52.|
|Tamaño total|2|Indica el tamaño total (en bytes) de toda la estructura del registro.|
|Suma de comprobación del encabezado|2|Suma de comprobación que convierte el área del encabezado del registro. La estructura del registro no se considera válida si los campos del encabezado no coinciden con la comprobación de la suma de comprobación.|
|Número de versión|2|Números de versión principales y secundarios de tolerancia a errores de FileX.|
|Reservado|2|Para una futura expansión.|

El área de encabezado del registro va seguida del área del registro de la cadena FAT. La figura 9 contiene información que describe cómo se debe modificar la cadena FAT. Esta área del registro contiene información sobre los clústeres que se van a asignar a un archivo, los clústeres que se van a quitar de un archivo y dónde debe estar la inserción/eliminación y describe cada campo del área del registro de la cadena FAT.

**TABLA 9. Área del registro de la cadena FAT**

|Campo|Tamaño (en bytes)|Descripción|
|-----|--------------|-----------|
|Suma de comprobación del registro de la cadena FAT|2|Suma de comprobación del área del registro de la cadena FAT completa. El área del registro de la cadena FAT no se considera válida si se produce un error en la comprobación de la suma de comprobación.|
|Marcar|1|Los valores de marca válidos son:<br/>0x01 cadena FAT válida<br />0x02 se está utilizando el mapa de bits|
|Reservado|1|Reservado para uso futuro|
|Punto de inserción: Frontal|4|El clúster (que pertenece a la cadena FAT original) a la que se va a adjuntar la cadena recién creada.|
|Clúster principal de la nueva cadena FAT|4|Primer clúster de la cadena FAT recién creada|
|Clúster principal de la cadena FAT original|4|Primer clúster de la parte de la cadena FAT original que se va a quitar.|
|Punto de inserción: Trasero|4|El clúster original en el que se combina la cadena FAT recién creada.|
|Siguiente punto de eliminación|4|Este campo ayuda al procedimiento de limpieza de la cadena FAT.|

El área de las entradas de registro contiene entradas de registro que describen los cambios necesarios para recuperarse de un error. Se admiten tres tipos de entradas de registro en el módulo de tolerancia a errores de FileX: entrada de registro FAT; entrada de registro de directorio; y entrada de registro de mapa de bits.

En las tres figuras y tres tablas siguientes se describen detalladamente estas entradas de registro.

![Entrada de registro FAT](./media/user-guide/fat-log-entry.png)

**Figura 6. Entrada de registro FAT**

**TABLA 10. Entrada de registro FAT**

|Campo|Tamaño (en bytes)|Descripción|
|-----|--------------|-----------|
Tipo|2|Tipo de entrada, debe ser FX_FAULT_TOLERANT_FAT_LOG_TYPE|
|Size|2|Tamaño de esta entrada|
|Número de clúster|4|Número de clúster|
|Value|4|Valor que se va a escribir en la entrada FAT|

![Entrada de registro de directorio](./media/user-guide/directory-log-entry.png)

**Figura 7. Entrada de registro de directorio**

**TABLA 11. Entrada de registro de directorio**

|Campo|Tamaño (en bytes)|Descripción|
|-----|--------------|-----------|
|Tipo|2|Tipo de entrada, debe ser FX_FAULT_TOLERANT_DIRECTORY_LOG_TYPE|
|Size|2|Tamaño de esta entrada|
|Desplazamiento de sectores|4|Desplazamiento (en bytes) en el sector donde se encuentra este directorio.|
|Sector de registro|4|Sector en el que se encuentra la entrada de directorio|
|Datos de registro|Variable|Contenido de la entrada de directorio|

![Entrada de registro de mapa de bits](./media/user-guide/bitmap-log-entry.png)

**Figura 8. Entrada de registro de mapa de bits**

**TABLA 12. Entrada de registro de mapa de bits**

|Campo|Tamaño (en bytes)|Descripción|
|-----|--------------|-----------|
|Tipo|2|Tipo de entrada, debe ser FX_FAULT_TOLERANT_BITMAP_LOG_TYPE|
|Size|2|Tamaño de esta entrada|
|Número de clúster|4|Número de clúster|
|Value|4|Valor que se va a escribir en la entrada FAT|

## <a name="fault-tolerant-protection"></a>Protección de tolerancia a errores

Una vez que se inicia el módulo de tolerancia a errores de FileX, este busca primero un archivo de registro de tolerancia a errores existente en el soporte físico. Si no se encuentra un archivo de registro válido, FileX considera que el soporte físico no está protegido. En este caso, FileX creará un archivo de registro de tolerancia a errores en el soporte físico.

> [!IMPORTANT]
> *FileX no puede proteger un sistema de archivos si estaba dañado antes de que se inicie el módulo de tolerancia a errores de FileX. *

Si se encuentra un archivo de registro de tolerancia a errores, FileX comprueba las entradas de registro existentes. Un archivo de registro sin entradas de registro indica que la operación de archivo anterior se realizó correctamente y se quitaron todas las entradas de registro. En este caso, la aplicación puede empezar a usar el sistema de archivos con protección de tolerancia a errores.

Sin embargo, si se encuentran entradas de registro, FileX debe completar la operación de archivo anterior o revertir los cambios ya aplicados al sistema de archivos, deshacer los cambios de forma efectiva. En cualquier caso, después de que se apliquen las entradas de registro en el sistema de archivos, el sistema de archivos se restaura en un estado coherente y la aplicación puede empezar a usar el sistema de archivos de nuevo.

En el caso de los soportes físicos protegidos por FileX, durante la operación de actualización de archivos, la parte de datos se escribe directamente en el soporte físico. A medida que FileX escribe datos, también registra los cambios necesarios que se deben aplicar a las entradas de directorio, tabla FAT. Esta información se registra en las entradas de registro con tolerancia a archivos. Este enfoque garantiza que las actualizaciones del sistema de archivos se producen después de que los datos se escriban en el soporte físico. Si el soporte físico se expulsa durante la fase de escritura de datos, todavía no se ha cambiado la información crucial del sistema de archivos. Por lo tanto, el sistema de archivos no se ve afectado por la interrupción.

Una vez que todos los datos se han escrito correctamente en el soporte físico, FileX sigue la información de las entradas de registro para aplicar los cambios a la información del sistema, una entrada por una. Una vez confirmada toda la información del sistema en el soporte físico, las entradas de registro se quitan del registro de tolerancia a errores. En este momento, FileX completa la operación de actualización del archivo.

Durante la operación de actualización de archivos, los archivos no se actualizan en su lugar. El módulo de tolerancia a errores asigna un sector para los datos en los que se van a escribir los nuevos datos y, a continuación, quita el sector que contiene los datos que se van a sobrescribir, actualizando las entradas FAT relacionadas para vincular el nuevo sector a la cadena. En situaciones en las que es necesario modificar los datos parciales de un clúster, FileX siempre asigna nuevos clústeres, escribe todos los datos de los clústeres antiguos con datos actualizados en los nuevos clústeres y, a continuación, libera los clústeres antiguos. Esto garantiza que si se interrumpe la actualización del archivo, el archivo original permanece intacto. La aplicación debe tener en cuenta que en la protección de tolerancia a errores de FileX, la actualización de los datos en un archivo requiere que el soporte físico tenga suficiente espacio libre para almacenar datos nuevos antes de que se puedan liberar los sectores con datos antiguos. Si el soporte físico no tiene suficiente espacio para almacenar datos nuevos, se produce un error en la operación de actualización.
