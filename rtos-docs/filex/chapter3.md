---
title: 'Capítulo 3: Componentes funcionales de Azure RTOS FileX'
description: En este capítulo, se incluye una descripción del sistema de archivos incrustados de Azure RTOS FileX de alto rendimiento desde una perspectiva funcional
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1e1e1a1dbd844d811c7ee3122113f28162639fb4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814409"
---
# <a name="chapter-3---functional-components-of-azure-rtos-filex"></a>Capítulo 3: Componentes funcionales de Azure RTOS FileX

En este capítulo, se incluye una descripción del sistema de archivos incrustados de Azure RTOS FileX de alto rendimiento desde una perspectiva funcional.

## <a name="media-description"></a>Descripción del medio

FileX es un sistema de archivos incrustados de alto rendimiento que se ajusta al formato del sistema de archivos FAT. FileX ve el medio físico como una matriz de sectores lógicos. La forma en que estos sectores están asignados al medio físico subyacente viene determinada por el controlador de E/S conectado al medio de FileX durante la llamada ***fx_media_open***.

### <a name="fat121632-logical-sectors"></a>Sectores lógicos FAT12/16/32

La organización exacta de los sectores lógicos del medio viene determinada por el contenido del registro de arranque del medio físico. En la ilustración 1 se muestra el diseño general de los sectores lógicos del medio.

Los sectores lógicos de FileX se inician en el sector 1 lógico, que apunta al primer sector reservado del medio. Los sectores reservados son opcionales, pero cuando están en uso, normalmente contienen información del sistema, como el código de arranque.

### <a name="fat121632-media-boot-record"></a>Registro de arranque del medio FAT12/16/32

El desplazamiento exacto del sector de las demás áreas de la vista del sector lógico del medio se deriva del contenido del *registro de arranque del medio*. La ubicación del registro de arranque suele estar en el sector 0. Sin embargo, si el medio tiene *sectores ocultos*, el desplazamiento al sector de arranque debe tener en cuenta estos (se encuentran inmediatamente ANTES del sector de arranque). En la tabla 1 se enumeran los componentes de registro de arranque del medio y los componentes se describen en los párrafos.

- **Instrucción de salto** El campo de *instrucción de salto* es un campo de tres bytes que representa una instrucción de máquina Intel x86 para un salto de procesador. Se trata de un campo heredado en la mayoría de las situaciones.

  ![Vista del sector lógico del medio de FileX](./media/user-guide/filex-media-logical-sector-view.png)

  **ILUSTRACIÓN 1. Vista del sector lógico del medio de FileX**

- **Nombre de OEM** El campo de *nombre de OEM* se reserva para que los fabricantes incluyan su nombre o un nombre para el dispositivo.
- **Bytes por sector** El campo de *bytes por sector* en el registro de arranque del medio define cuántos bytes hay en casa sector (el elemento fundamental del medio).
- **Sectores por clúster** El campo de *sectores por clúster* del registro de arranque del medio define el número de sectores asignados a un clúster. El clúster es el elemento de asignación fundamental de un sistema de archivos compatible con FAT. Toda la información de los archivos y los subdirectorios se asignan desde los clústeres disponibles del medio según determina la tabla de asignación de archivos (FAT).

    **TABLA 1. Registro de arranque del medio de FileX**
    |Offset  |Campo  |Número de bytes|
    |----------|-----------|------------|
    |0x00|Instrucción de salto (e9,xx,xx or eb,xx,90)|3|
    |0x03|Nombre de OEM|8|
    |0x0B|Bytes por sector|2|
    |0x0D|Sectores por clúster|1|
    |0x0E|Número de sectores reservados|2|
    |0x10|Número de FAT|1|
    |0x11|Tamaño del directorio raíz|2|
    |0x13|Número de sectores FAT-12 &amp; FAT-16|2|
    |0x15|Tipo de soporte|1|
    |0x16|Número de sectores por FAT|2|
    |0x18|Sectores por pista|2|
    |0x1A|Número de encabezados|2|
    |0x1C|Número de sectores ocultos|4|
    |0x20|Número de sectores: FAT-32|4|
    |0x24|Sectores por FAT (FAT-32)|4|
    |0x2C|Clúster de directorio raíz|4|
    |0x3E|Código de arranque del sistema|448
    |0x1FE|0x55AA|2|

- **Sectores reservados** El campo de *sectores reservados* del registro de arranque del medio define el número de sectores reservados entre el registro de arranque y el primer sector del área de FAT. Esta entrada es cero en la mayoría de los casos.
- **Número de FAT** La entrada de *número de FAT* del registro de arranque del medio define el número de FAT en el medio. Siempre debe haber al menos una FAT en un medio. Las FAT adicionales son simplemente copias duplicadas de la FAT principal (primera) y suele usarlas software de recuperación o diagnóstico.
- **Tamaño del directorio raíz** La entrada de *tamaño del directorio raíz* del registro de arranque del medio define el número fijo de entradas en el directorio raíz del medio. Este campo no se puede aplicar a los subdirectorios y al directorio raíz FAT-32, ya que ambos se asignan desde los clústeres del medio.
- **Número de sectores FAT-12 & FAT-16** El campo de *número de sectores* del registro de arranque del medio contiene el número total de sectores en el medio. Si este campo es cero, el número total de sectores se incluye en el campo de *número de sectores FAT-32* que se encuentra más adelante en el registro de arranque.
- **Tipo de medio** El campo de *tipo de medio* se usa para identificar el tipo de medio presente en el controlador de dispositivo. Se trata de un campo heredado.
- **Sectores por FAT** En el campo de *sectores por FAT* del registro de arranque del medio se incluye el número de sectores asociados a cada FAT del área de FAT. El número de sectores de FAT debe ser lo suficientemente grande como para tener en cuenta el número máximo posible de clústeres que se pueden asignar en el medio.
- **Sectores por pista** El campo de *sectores por pista* del registro de arranque del medio define el número de sectores por pista. Normalmente, esto solo es pertinente para el medio de tipo de disco real. Los dispositivos FLASH no usan esta asignación.
- **Número de encabezados** El campo de *número de encabezados* del registro de arranque del medio define el número de encabezados del medio. Normalmente, esto solo es pertinente para el medio de tipo de disco real. Los dispositivos FLASH no usan esta asignación.
- **Sectores ocultos** El campo de *sectores ocultos* del registro de arranque del medio define el número de sectores antes del registro de arranque. Este campo se mantiene en el bloque de control **FX_MEDIA** y se debe tener en cuenta en los controladores de E/S de FileX en todas las solicitudes de lectura y escritura realizadas por FileX.
- **Número de sectores FAT-32** El campo de *número de sectores* del registro raíz del medio solo es válido si el campo de *número de sectores* de dos bytes es cero. En tal caso, en este campo de cuatro bytes se incluye el número de sectores del medio.
- **Sectores por FAT (FAT-32)** El campo de *sectores por FAT (FAT-32)* solo es válido en formato FAT-32 y en él se incluye el número de sectores asignados para cada FAT del medio.
- **Clúster de directorio raíz** El campo de *clúster de directorio raíz* solo es válido en formato FAT-32 y en él se incluye el número inicial de clústeres del directorio raíz.
- **Código raíz del sistema** El campo de *código de arranque del sistema* es un área para almacenar una pequeña parte del código de arranque. Actualmente, en la mayoría de los dispositivos, se trata de un campo heredado.
- **Firma 0x55AA** El campo de *firma* es un patrón de datos usado para identificar el registro de arranque. Si este campo no está presente, el registro de arranque no es válido.

### <a name="exfat"></a>exFAT

El tamaño máximo de archivo en FAT32 es 4 GB, lo que limita la amplia adopción de archivos multimedia de alta definición. De forma predeterminada, FAT32 admite un medio de almacenamiento de hasta 32 GB. Con el aumento de la capacidad de la tarjeta SD y flash, FAT32 se vuelve menos eficaz al administrar grandes volúmenes. exFAT está diseñado para superar estas limitaciones. exFAT admite un tamaño de archivo hasta un exabyte (EB), que es aproximadamente de mil millones de GB. Otra diferencia significativa entre exFAT y FAT32 es que exFAT usa un mapa de bits para administrar el espacio disponible en el volumen, lo que hace que exFAT sea más eficaz al buscar espacio disponible al escribir datos en el archivo. En el caso de los archivos almacenados en clústeres contiguos, exFAT elimina la cadena que recorre la FAT, lo que aumenta su eficacia al acceder a archivos de gran tamaño. exFAT es necesario para el almacenamiento flash y las tarjetas SD de más de 32 GB.

### <a name="exfat-logical-sectors"></a>Sectores lógicos exFAT

El diseño general de los sectores lógicos del medio en exFAT se muestra en la ilustración 2. En exFAT, el bloque de arranque y el área de FAT pertenecen al área del sistema. El resto de los clústeres son áreas de usuario. Aunque no es necesario, el estándar exFAT recomienda que el mapa de bits de asignación esté al principio del área de usuario, seguido de la tabla de casos superior y el directorio raíz.

### <a name="exfat-media-boot-record"></a>Registro de arranque del medio de exFAT

El contenido del registro de arranque del medio de exFAT es diferente de los de FAT12/16/32. Aparecen en la tabla 2. Para evitar confusiones, el área entre 0x0B y 0x40, que contiene diversos parámetros del medio en FAT12/16/32, se marca como *Reservada* en exFAT. Esta área reservada debe programarse con ceros, evitando que se interprete erróneamente el registro de arranque del medio.

![Sectores lógicos exFAT](./media/user-guide/exfat-logical-sectors.png)

**ILUSTRACIÓN 2. Sectores lógicos exFAT**

- **Instrucción de salto** El campo de *instrucción de salto* es un campo de tres bytes que representa una instrucción de máquina Intel x86 para un salto de procesador. Se trata de un campo heredado en la mayoría de las situaciones.

    **TABLA 2. Registro de arranque del medio exFAT**

    |Offset  |Campo  |Número de bytes|
    |----------|-----------|------------|
    |0x00|Instrucción de salto|3|
    |0x03|Nombre del sistema de archivos|8|
    |0x0B|Reservado|53|
    |0x40|Desplazamiento de partición|8|
    |0x48|Longitud de volumen|8|
    |0x50|Desplazamiento de FAT|4|
    |0x54|Longitud de FAT|4|
    |0x58|Desplazamiento de montón de clúster|4|
    |0x5C|Recuento de clústeres|4|
    |0x60|Primer clúster del directorio raíz|4|
    |0x64|Número de serie de volumen|4|
    |0x68|Revisión del sistema de archivos|2|
    |0x6A|Marcas de volumen|2|
    |0x6c|Cambio de bytes por sector|1|
    |0x6D|Cambio de sector por clúster|1|
    |0x6E|Número de FAT|1|
    |0x6F|Selección de unidad|1|
    |0x70|Porcentaje en uso|7|
    |0x71|Reservado|1|
    |0x78|Código de arranque|390|
    |0x1FE|Firma de arranque|2|

- **Nombre del sistema de archivos** En el caso de exFAT, el campo de *nombre del sistema de archivos* debe ser "EXFAT", seguido de tres espacios en blanco finales.
- **Reservado** El contenido del campo *reservado* debe ser cero. Esta región se superpone con los registros de arranque en FAT12/16/32. Al dejar esta área en cero se evita que los sistemas de archivos malinterpreten este volumen.
- **Desplazamiento de partición** El campo de *desplazamiento de partición* indica el inicio de esta partición.
- **Longitud de volumen** El campo de *longitud de volumen* define el tamaño, en número de sectores, de esta partición.
- **Desplazamiento de FAT** El campo de *desplazamiento de FAT* define el número inicial de sectores, con relación al principio de esta partición, de la tabla FAT para esta partición.
- **Longitud de FAT** El campo de *longitud de FAT* define el tamaño de la tabla FAT, en número de sectores.
- **Desplazamiento de montón de clúster** El campo de *desplazamiento de montón de clúster* define el número inicial de sectores, con relación al principio de la partición, del montón de clúster. El montón del clúster es el área donde se almacenan la información de los directorios y los datos de archivo.
- **Recuento de clústeres** El campo de *recuento de clústeres* define el número de clúster que tiene esta partición.
- **Primer clúster del directorio raíz** El campo de *primer clúster del directorio raíz* define la ubicación inicial del directorio raíz, que se aconseja que esté justo después del mapa de bits de asignación y la tabla de casos superior.
- **Número de serie de volumen** El campo de *número de serie de volumen* define el número de serie de esta partición.
- **Revisión del sistema de archivos** El campo de *revisión del sistema de archivos* define la versión principal y secundaria de exFAT.
- **Marcas de volumen** El campo de *marcas de volumen* contiene marcas que indican el estado de este volumen.
- **Cambio de bytes por sector** El campo de *cambio de bytes por sector* define el número de bytes por sector, en log2(n), donde n es el número de bytes por sector. Por ejemplo, en la tarjeta SD, el tamaño del sector es de 512 bytes. Por lo tanto, este campo debe ser 9 (log2(512) = 9).
- **Cambio de sectores por clúster** El campo de *cambio de sectores por clúster* define el número de sectores de un clúster, en log2(n), donde n es el número de sectores por clúster.
- **Número de FAT** El campo de *número de FAT* define el número de tablas FAT de esta partición. En el caso de exFAT, se recomienda que el valor sea 1, para una tabla FAT.
- **Selección de unidad** El campo de *selección de unidad* define el número de unidad INT 13h extendido.
- **Porcentaje en uso** El campo de *porcentaje en uso* define el porcentaje de los clústeres en el montón de clúster que se asigna. Los valores válidos oscilan entre 0 y 100, ambos inclusive.
- **Reservado** Este campo se reserva para un futuro uso.
- **Código de arranque** El campo de *código de arranque* es un área para almacenar una pequeña parte del código de arranque. Actualmente, en la mayoría de los dispositivos, se trata de un campo heredado.
- **Firma 0x55AA** El campo de *firma de arranque* es un patrón de datos usado para identificar el registro de arranque. Si este campo no está presente, el registro de arranque no es válido.

### <a name="file-allocation-table-fat"></a>Tabla de asignación de archivos (FAT)

La *Tabla de asignación de archivos (FAT)* se inicia después de los sectores reservados del medio. El área de FAT es básicamente una matriz de entradas de 12 bits, 16 bits o 32 bits que determinan si ese clúster está asignado o forma parte de una cadena de clústeres que incluye un subdirectorio o un archivo. El tamaño de cada entrada de FAT viene determinado por el número de clústeres que se deben representar. Si el número de clústeres (derivado de los sectores totales divididos por los sectores por clúster) es menor o igual que 4086, se usan entradas de FAT de 12 bits. Si el número total de clústeres es mayor que 4086 y menor que 65 525, se usan entradas de FAT de 16 bits. De lo contrario, si el número total de clústeres es mayor o igual que 65 525, se usan FAT o exFAT de 32 bits.

En el caso de FAT12/16/32, la tabla FAT no solo mantiene la cadena de clúster, sino que también proporciona información sobre la asignación de clústeres: si un clúster está disponible o no. En exFAT, una entrada de directorio de mapa de bits de asignación conserva la información de asignación de clústeres. Cada partición tiene su propio mapa de bits de asignación. El tamaño del mapa de bits es lo suficientemente grande como para abarcar todos los clústeres disponibles. Si un clúster está disponible para la asignación, el bit correspondiente en el mapa de bits de asignación se establece en 0. De lo contrario, el bit se establece en 1. En el caso de un archivo que ocupa clústeres consecutivos, exFAT no requiere una cadena FAT para realizar un seguimiento de todos los clústeres. Sin embargo, en el caso de un archivo que no ocupa clústeres consecutivos, sigue siendo necesario el mantenimiento de una cadena FAT.

### <a name="fat-entry-contents"></a>Contenido de las entrada de FAT

Las dos primeras entradas de la tabla FAT no se usan y normalmente tienen el siguiente contenido.

|Entrada de FAT |FAT de 12 bits|FAT de 16 bits|FAT de 32 bits| exFAT|
|----------|-----------|------------|-------|------|
|Entrada 0|0x0F0|0x00F0|0x000000F0|0xF8FFFFFF|
|Entrada 1|0xFFF|0xFFFF|0x0FFFFFFF|0xFFFFFFFF|

La entrada FAT número 2 representa el primer clúster del área de datos del medio. El contenido de cada entrada del clúster determina si está o no disponible, o forma parte de una lista vinculada de clústeres asignados para un archivo o un subdirectorio. Si la entrada del clúster contiene otra entrada del clúster válida, el clúster se asigna y su valor señala al siguiente clúster asignado en la cadena de clúster.

Las entradas del clúster posibles se definen como se indica a continuación.
|Significado|FAT de 12 bits|FAT de 16 bits|FAT de 32 bits| exFAT|
|----------|-----------|------------|-------|------|
|Clúster disponible|0x000|0x0000|0x00000000|0x00000000|
|No se utiliza|0x001|0x0001|0x00000001|0x00000001|
|Reservado|0xFF0-FF6|0xFFF0-FFF6|0x0FFFFFF0-6|ClusterCounter +2 a 0xFFFFFFF6|
|Clúster incorrecto|0xFF7|0xFFF7|0x0FFFFFF7|0xFFFFFFF7|
|Reservado| - | - | - | 0xFFFFFFF8-E|
|Último clúster| 0xFF8-FFF| 0xFFF8-FFFF| 0x0FFFFFF8-F| 0xFFFFFFFF|
|Vínculo de clúster| 0x002-0xFEF| 0x0002-FFEF| 0x2-0x0FFFFFEF | 0x2 - ClusterCount + 1|

El último clúster de una cadena de clústeres asignada contiene el último valor de clúster (definido anteriormente). El primer número de clúster se encuentra en el archivo o en la entrada de directorio del subdirectorio.

### <a name="internal-logical-cache"></a>Caché lógica interna

FileX mantiene una caché del sector lógico *most-recently-used* para cada medio abierto. La constante **FX_MAX_SECTOR_CACHE** define el tamaño máximo de la caché del sector lógico y se encuentra en **_fx_api.h_**. Este es el primer factor que determina el tamaño de la caché del sector lógico interna.

El otro factor que determina el tamaño de la caché del sector lógico es la cantidad de memoria que la aplicación proporciona a la llamada ***fx_media_open** _ . Debe haber memoria suficiente para un sector lógico como mínimo. Si se requieren más de _ *FX_MAX_SECTOR_CACHE** sectores lógicos, se debe cambiar la constante en **_fx_api.h_** y se debe recompilar toda la biblioteca FileX.

> [!IMPORTANT]
> *Cada medio abierto en FileX debe tener un tamaño de caché distinto según la memoria proporcionada durante la llamada abierta.*

### <a name="write-protect"></a>Protección contra escritura

FileX proporciona al controlador de la aplicación la capacidad de establecer de forma dinámica la protección contra escritura en el medio. Si se requiere protección contra escritura, el controlador establece en FX_TRUE el campo *fx_media_driver_write_protect* en la estructura FX_MEDIA asociada. Cuando se establece, se rechazan todos los intentos de la aplicación para modificar el medio, así como los intentos de abrir archivos para escritura. El controlador también puede deshabilitar la protección contra escritura desactivando este campo.

### <a name="free-sector-update"></a>Actualización del sector disponible

FileX proporciona un mecanismo para informar al controlador de la aplicación cuando los sectores ya no están en uso. Esto es especialmente útil para los administradores de memoria FLASH que administran todos los sectores lógicos que usa FileX.

Si se requiere la notificación de sectores disponibles, el controlador de la aplicación establece en FX_TRUE el campo *fx_media_driver_free_sector_update* en la estructura FX_MEDIA asociada. Esta asignación se realiza normalmente durante la inicialización del controlador.

Al establecer este campo, FileX realiza una llamada de controlador **FX_DRIVER_RELEASE_SECTORS** que indica la disponibilidad de uno o más sectores consecutivos.

### <a name="media-control-block-fx_media"></a>Bloque de control del medio FX_MEDIA

Las características de cada medio abierto en FileX se encuentran en el bloque de control del medio. Esta estructura se define en el archivo ***fx_api.h***.

El bloque de control del medio se puede ubicar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global mediante su definición fuera del ámbito de cualquier función.

Buscar el bloque de control en otras áreas requiere un poco más de cuidado, exactamente igual que toda la memoria asignada de forma dinámica. Si se asigna un bloque de control dentro de una función de C, la memoria asociada al mismo forma parte de la pila del subproceso que realiza la llamada.

> [!WARNING]
>*En general, evite usar almacenamiento local para los bloques de control, ya que, una vez devuelta la función, se libera todo su espacio de pila de variables local, independientemente de si se sigue usando.*

## <a name="fat121632-directory-description"></a>**Descripción de directorio FAT12/16/32**

FileX admite formatos de nombre de archivo largos (LFN) de Windows y 8.3. Además del nombre, cada entrada de directorio contiene los atributos de la entrada, la fecha y hora modificadas por última vez, el índice de clúster inicial y el tamaño en bytes de la entrada. En la tabla 3 se muestra el contenido y tamaño de una entrada de directorio FileX 8.3.

- **Nombre de directorio**

    FileX admite nombres de archivo con un tamaño comprendido entre 1 y 255 caracteres. Los nombres de archivo de ocho caracteres estándar se representan en una única entrada de directorio en el medio. Se alinean a la izquierda en el campo de nombre de directorio y se rellenan en blanco. Además, los caracteres ASCII que componen el nombre siempre se escriben en mayúsculas.

    Los nombres de archivo largos (LFN) se representan mediante entradas de directorio consecutivas, en orden inverso, seguidas inmediatamente de un nombre de archivo estándar 8.3. El nombre 8.3 creado contiene toda la información significativa del directorio asociada al nombre. En la tabla 4 se muestra el contenido de las entradas de directorio usadas para incluir la información de los nombres de archivo largos y en la tabla 5 se muestra un ejemplo de un LFN de 39 caracteres que requiere un total de cuatro entradas de directorio.

> [!IMPORTANT]
> *La constante **FX_MAX_LONG_NAME_LEN**, definida en **fx_api.h**, contiene la longitud máxima que admite FileX.*

- **Extensión de nombre de archivo del directorio**

    En el caso de los nombres de archivo 8.3, FileX también admite la *extensión de nombre de archivo* de tres caracteres opcional. Al igual que el nombre de archivo de ocho caracteres, las extensiones de nombre de archivo se justifican a la izquierda en el campo de extensión de nombre de archivo del directorio, se rellenan en blanco y siempre se escriben en mayúsculas.

    **TABLA 3. Entrada de directorio FileX 8.3**

    |Offset|Campo|Número de bytes|
    |------------|-----------|------------|
    |0x00|Nombre de entrada de directorio|8|
    |0x08|Extensión de directorio|3|
    |0x0B|Atributos|1|
    |0x0C|NT (introducido por el formato de nombre de archivo largo y se reserva para NT [siempre 0])|1|
    |0x0D|Tiempo de creación en milisegundos (introducido por el formato de nombre de archivo largo y representa el número de milisegundos correspondientes al momento de la creación del archivo).|1|
    |0x0E|Tiempo de creación en horas &amp; minutos (introducido por el formato de nombre de archivo largo y representa la hora y el minuto en que se creó el archivo)|2|
    |0x10|Fecha de creación (introducida por el formato de nombre de archivo largo y representa la fecha en que se creó el archivo).|2|
    |0x12|Fecha de creación (introducida por el formato de nombre de archivo largo y representa la fecha en que se creó el archivo).|2|
    |0x14|Clúster inicial (solo FAT-32 de más de 16 bits)|2|
    |0x16|Hora de modificación|2|
    |0x18|Fecha de modificación|2|
    |0x1A|Clúster inicial (FAT-12, FAT-16 o FAT-32 de menos de 16 bits)|2|
    |0x1C|Tamaño de archivo|4|


- **Atributos de directorio**

    La entrada de campo de *atributo de directorio* de un byte contiene una serie de bits que especifican diversas propiedades de la entrada de directorio. Las definiciones de atributos de directorio son las siguientes:

    |Bit de atributo|Significado|
    |------------|-----------|
    |0x01|La entrada es de solo lectura.|
    |0x02|La entrada está oculta.|
    |0x04|La entrada es una entrada del sistema.|
    |0x08|La entrada es una etiqueta de volumen|
    |0x10|La entrada es un directorio.|
    |0x20|La entrada se ha modificado.|

    Dado que todos los bits de atributo se excluyen mutuamente, puede haber más de un conjunto de bits de atributo a la vez.

- **Tiempo del directorio**

    El campo de *tiempo del directorio* de dos bytes contiene las horas, minutos y segundos del último cambio en la entrada de directorio especificada. En cuanto a los bits, del 15 al 11 contienen las horas, del 10 al 5 contienen los minutos y del 4 al 0 contienen los medios segundos. Los segundos reales se dividen entre dos antes de escribirse en este campo.

- **Fecha del directorio**

    El campo de *fecha del directorio* de dos bytes contiene el año (desplazamiento desde 1980), mes y día del último cambio en la entrada de directorio especificada. En cuanto a los bits, del 15 al 9 contienen el desplazamiento anual, del 8 al 5 contienen el desplazamiento mensual y del 4 al 0 contienen el día.

- **Clúster inicial del directorio**

    Este campo ocupa 2 bytes para los FAT-12 y FAT-16. En el caso de FAT-32, este campo ocupa 4 bytes. Este campo contiene el primer número de clúster asignado a la entrada (subdirectorio o archivo).

    > [!NOTE]
    > *Tenga en cuenta que FileX crea archivos nuevos sin un clúster inicial (el campo de clúster inicial es igual a cero) para permitir a los usuarios asignar opcionalmente un número contiguo de clústeres para un archivo recién creado. *

- **Tamaño de archivo del directorio**

    El campo de *tamaño de archivo* del *directorio* contiene el número de bytes del archivo. Si la entrada es en realidad un subdirectorio, el campo de tamaño es cero.

### <a name="long-file-name-directory"></a>Directorio de nombre de archivo largo

- **Ordinal**

    El campo *ordinal* de un byte que especifica el número de la entrada de LFN. Dado que las entradas de LFN se colocan en orden inverso, los valores ordinales de las entradas de directorio LFN que componen un solo LFN disminuyen en uno. Además, el valor ordinal del LFN directamente antes del nombre del archivo 8.3 debe ser uno.

    **TABLA 4. Entrada de directorio de nombre de archivo largo**

    |Offset|Campo|Número de bytes|
    |------------|-----------|------------|
    0x00|Campo ordinal|1|
    0x01|Carácter Unicode 1|2|
    0x03|Carácter Unicode 2|2|
    0x05|Carácter Unicode 3|2|
    0x07|Carácter Unicode 4|2|
    0x09|Carácter Unicode 5|2|
    0x0B|Atributos de LFN|1|
    0x0C|Tipo de LFN (reservado siempre 0)|1|
    0x0D|Suma de comprobación de LFN|1|
    0x0E|Carácter Unicode 6|2|
    0x10|Carácter Unicode 7|2|
    0x12|Carácter Unicode 8|2|
    0x14|Carácter Unicode 9|2|
    0x16|Carácter Unicode 10|2|
    0x18|Carácter Unicode 11|2|
    0x1A|Clúster de LFN (no utilizado siempre 0)|2|
    0x1C|Carácter Unicode 12|2|
    0x1E|Carácter Unicode |13|2|

- **Carácter Unicode**

    Los campos de *carácter Unicode* de dos bytes están diseñados para admitir caracteres de muchos lenguajes diferentes. Los caracteres ASCII estándar se representan con el carácter ASCII almacenado en el primer byte del carácter Unicode seguido de un carácter de espacio.

- **Atributos de LFN**

    El campo de *atributos de LFN* de un byte contiene atributos que identifican la entrada de directorio como una entrada de directorio LFN. Para ello, se han establecido todos los atributos de solo lectura, del sistema, ocultos y de volumen.

- **Tipo de LFN**

    El campo de *tipo de LFN* de un byte está reservado y siempre es 0.

- **Suma de comprobación de LFN**

    El campo de *suma de comprobación* de un byte representa una suma de comprobación de los 11 caracteres del nombre de archivo MSDOS 8.3 asociado. Esta suma de comprobación se almacena en cada entrada de LFN para ayudar a garantizar que la entrada de LFN se corresponda con el nombre del archivo 8.3 adecuado.

- **Clúster de LFN**

    El campo de *clúster de LFN* de dos bytes no se utiliza y siempre es 0.

    **TABLA 5. Entradas de directorio que componen un LFN de 39 caracteres**

    |Entrada|Significado|
    |------------|-----------|
    |1|Entrada de directorio LFN 3|
    |2|Entrada de directorio LFN 2|
    |3|Entrada de directorio LFN 1|
    |4|Entrada de directorio 8.3 (ttttt~n.xx)|

### <a name="exfat-directory-description"></a>Descripción de directorio exFAT

El sistema de archivos exFAT almacena la entrada de directorio y el nombre de archivo de manera diferente. La entrada de directorio contiene los atributos de la entrada, diversas marcas de tiempo del momento en que se creó, modificó y tuvo acceso a la entrada. Otra información, como el tamaño de archivo y el clúster inicial, se almacena en la entrada de directorio de extensión de flujo que sigue inmediatamente a la entrada de directorio principal. exFAT solo admite el formato de nombre de archivo largo (LFN). que se almacena en la entrada de directorio de nombres de archivo que sigue inmediatamente a la entrada de directorio de extensión de flujo, como se muestra en la tabla 2.

### <a name="exfat-file-directory-entry"></a>Entrada de directorio de archivos exFAT

En la tabla y los párrafos siguientes se incluye una descripción de la entrada de directorio de archivos exFAT y su contenido.

- **Tipo de entrada**

    El campo de tipo de entrada indica el tipo de esta entrada. Para la entrada de directorio de archivos, este campo debe ser 0x85.

- **Recuento de entradas secundarias**

    El campo de *recuento de entradas secundarias* indica el número de entradas secundarias que sigue inmediatamente a esta entrada principal. Las entradas secundarias asociadas a la entrada de directorio de archivos incluyen una entrada de directorio de extensión de flujo y una o varias entradas de directorio de nombres de archivo.

    **TABLA 6. Entrada de directorio de archivos exFAT**

    |Offset|Campo|Número de bytes|
    |----|-----------|-|
    |0x00|Tipo de entrada|1|
    |0x01|Entrada secundaria|1|
    |0x02|Suma de comprobación|2|
    |0x04|Atributos de archivo|2|
    |0x06|Reservado 1|2|
    |0x08|Marca de tiempo de creación|4|
    |0x0C|Última marca de tiempo modificada|4|
    |0x10|Última marca de tiempo de acceso|4|
    |0x14|Creación de incremento de 10 ms|1|
    |0x15|Último incremento de 10 ms modificado|1|
    |0x16|Creación de diferencia horaria con UTC|1|
    |0 x 17|Última diferencia horaria con UTC modificada|1|
    |0x18|Última diferencia horaria con UTC de acceso|1|
    |0x19|Reservado 2|7|

- **Checksum**

    El campo de *suma de comprobación* contiene el valor de la suma de comprobación de todas las entradas del conjunto de entradas de directorio (la entrada de directorio de archivos y sus entradas secundarias).

- **Atributos de archivo**

    La entrada de campo de atributos de un byte contiene una serie de bits que especifican diversas propiedades de la entrada de directorio. La definición de la mayoría de los bits de atributos es idéntica a FAT 12/16/32. Las definiciones de atributos de directorio son las siguientes:

    |Bit de atributo|Significado|
    |------------|-----------|
    |0x01| La entrada es de solo lectura|
    |0x02|La entrada está oculta|
    |0x04|La entrada es una entrada del sistema|
    |0x08|La entrada está reservada|
    |0x10|La entrada es un directorio|
    |0x20|La entrada se ha modificado|
    |Todos los demás bits|Reservado|

- **Reserved1**

    Este campo debe ser cero.

- **Marca de tiempo de creación**

    El campo de *creación de marca de tiempo*, que combina información del campo de *creación de incremento de 10 ms*, describe la fecha y hora local en que se creó el archivo o el directorio.

- **Última marca de tiempo modificada**

    El campo de *última marca de tiempo modificada*, que combina información del campo de *último incremento de 10 ms modificado*, describe la fecha y hora local en que se modificó por última vez el archivo o el directorio. Consulte las notas siguientes sobre marcas de tiempo.

- **Última marca de tiempo de acceso**

    El campo de *última marca de tiempo de acceso* describe la fecha y hora local en que se accedió por última vez al archivo o al directorio. Consulte las notas siguientes sobre marcas de tiempo.

- **Creación de incremento de 10 ms**

    El campo de *creación de incremento de 10 ms*, que combina información del campo de *creación de marca de tiempo*, describe la fecha y hora local en que se creó el archivo o el directorio. Consulte las notas siguientes sobre marcas de tiempo.

- **Último incremento de 10 ms modificado**

    El campo de *último incremento de 10 ms modificado*, que combina información del campo de *última marca de tiempo modificada*, describe la fecha y hora local en que se modificó por última vez el archivo o el directorio. Consulte las notas siguientes sobre marcas de tiempo.

- **Creación de diferencia horaria con UTC**

    El campo de *creación de diferencia horaria con UTC* describe la diferencia entre la hora local y la hora UTC, momento de creación del archivo o el directorio. Consulte las notas siguientes sobre marcas de tiempo.

- **Última diferencia horaria con UTC modificada**

    El campo de *última diferencia horaria con UTC modificada* describe la diferencia entre la hora local y la hora UTC, momento en que se modificó por última vez el archivo o el directorio. Consulte las notas siguientes sobre marcas de tiempo.

- **Última diferencia horaria con UTC de acceso**

    El campo de *última diferencia horaria con UTC de acceso* describe la diferencia entre la hora local y la hora UTC, momento en que se accedió por última vez el archivo o el directorio. Consulte las notas siguientes sobre marcas de tiempo.

- **Reserved2**

    Este campo debe ser cero.

### <a name="notes-on-timestamps"></a>Notas sobre marcas de tiempo

- **Entrada de marca de tiempo** Los campos de marca de tiempo se interpretan de la manera siguiente:

- **Campos de incremento de 10 ms** El valor del campo de incremento de 10 ms proporciona una granularidad más fina al valor de marca de tiempo. Los valores válidos están comprendidos entre 0 (0 ms) y 199 (1990 ms).

     ![Campos de incremento de 10 ms](./media/user-guide/10ms-increment-fields.png)

- **Campo de diferencia horaria con UTC**

     ![Campo de diferencia horaria con UTC](./media/user-guide/utc-offset-field.png)

- **Valor de desplazamiento**

    Un entero con signo de 7 bits representa el desplazamiento de la hora UTC, en incrementos de 15 minutos.

- **Válido**

    Si el valor del campo de desplazamiento es válido o no. 0 indica que el valor del campo de valor de desplazamiento no es válido. 1 indica que el valor es válido.

### <a name="stream-extension-directory-entry"></a>Entrada de directorio de extensión de flujo

En la tabla siguiente se incluye una descripción de la entrada de directorio de extensión de flujo y su contenido.

**TABLA 7. Entrada de directorio de extensión de flujo**

|Offset|Campo| Número de bytes|
|------------|-----------|-------|
|0x00|Tipo de entrada|1|
|0x01|Marcas|1|
|0x02|Reservado 1|1|
|0x03|Longitud del nombre|1|
|0x04|Hash del nombre|2|
|0x06|Reservado 2|2|
|0x08|Longitud de datos válida|8|
|0x10|Reservado 3|4|
|0x14|Primer clúster|4|
|0x18|Longitud de los datos|8|

- **Tipo de entrada**

    El campo de *tipo de entrada* indica el tipo de esta entrada. En el caso de la entrada de directorio de extensión de streaming, este campo debe ser 0xC0.

- **Marcas**

    Este campo contiene una serie de bits que especifican diversas propiedades:
    |Bit de marca|Significado    |
    |-----------------|-----------|
    |0x01            |Este campo indica si es posible o no la asignación de clústeres. Este campo debe ser 1.|
    |0x02            |Este campo indica si los clústeres asociados son contiguos o no. Un valor 0 significa que la entrada de FAT es válida y FileX debe seguir a la cadena FAT. Un valor 1 significa que la entrada de FAT no es válida y los clústeres son contiguos.|
    |Todos los demás bits    |Reservado.|

- **Reservado 1**

    Este campo debe ser 0.

- **Longitud del nombre**

    El campo de *longitud del nombre* contiene la longitud de la cadena Unicode en el directorio de nombres de archivo que contienen las entradas de forma colectiva. Las entradas de directorio de nombres de archivo seguirán inmediatamente a esta entrada de directorio de extensión de flujo.

- **Hash del nombre**

    El campo de *hash del nombre* es una entrada de 2 bytes que contiene el valor hash del nombre de archivo incluido en la tabla de casos superior. El valor hash permite una búsqueda de nombres de archivos o directorios más rápida: si los valores hash no coinciden, el nombre de archivo asociado a esta entrada no es una coincidencia.

- **Reservado 2**

    Este campo debe ser 0.

- **Longitud de datos válida**

    El campo de *longitud de datos válida* indica la cantidad de datos válidos del archivo.

- **Reservado 3**

    Este archivado debe ser 0.

- **Primer clúster**

    El campo de *primer clúster* contiene el índice del primer clúster del flujo de datos.

- **Longitud de datos**

    El campo de *longitud de datos* contiene el número total de bytes de los clústeres asignados. Este valor puede ser mayor que la *longitud de datos válidos*, ya que exFAT permite la asignación previa de los clústeres de datos.

### <a name="root-directory"></a>Directorio raíz

En los formatos de 12 y 16 bits de FAT, el *directorio raíz* se encuentra inmediatamente después de todos los sectores de FAT del medio y se puede buscar examinando ***fx_media_root_sector_start** _ en un bloque de control _ *FX_MEDIA** abierto. El tamaño del directorio raíz, en términos de número de entradas de directorio (cada una con un tamaño de 32 bytes), viene determinado por la entrada correspondiente en el registro de arranque del medio.

El directorio raíz de FAT-32 y exFAT puede ubicarse en cualquier lugar de los clústeres disponibles. Su ubicación y tamaño se determinan a partir del registro de arranque al abrirse el medio. Una vez abierto el medio, se puede usar el campo ***fx_media_root_sector_start*** para buscar el clúster inicial del directorio raíz FAT-32 o exFAT.

### <a name="subdirectories"></a>Subdirectorios

Hay una cantidad de subdirectorios en un sistema FAT. El nombre del subdirectorio reside en una entrada de directorio de la misma forma que un nombre de archivo. Sin embargo, la especificación de atributo de directorio (0x10) se establece para indicar que la entrada es un subdirectorio y el tamaño de archivo siempre es cero.
En la ilustración 3 se muestra el aspecto de una estructura de subdirectorio típica para un nuevo subdirectorio de clúster único llamado ***SAMPLE.DIR** _ con un archivo denominado _*_FILE.TXT_**.
En la mayoría de los aspectos, los subdirectorios son muy similares a las entradas de archivo. El primer campo de clúster apunta al primer clúster de una lista vinculada de clústeres. Cuando se crea un subdirectorio, las dos primeras entradas de directorio contienen directorios predeterminados, concretamente el directorio "." y el directorio "..". El directorio "." apunta al propio subdirectorio, mientras que el directorio ".." apunta al directorio anterior o primario.

### <a name="global-default-path"></a>Ruta de acceso predeterminada global

FileX proporciona una ruta de acceso predeterminada global para el medio. La ruta de acceso predeterminada se usa en cualquier servicio de directorio o archivo que no especifique una ruta de acceso completa de forma explícita.

Inicialmente, el directorio predeterminado global se establece en el directorio raíz del medio. La aplicación puede cambiar esto mediante una llamada a ***fx_directory_default_set***.

La ruta de acceso predeterminada actual para el medio se puede examinar llamando a ***fx_directory_default_get** _. Esta rutina proporciona un puntero de cadena a la cadena de ruta de acceso predeterminada que se mantiene dentro del bloque de control _ *FX_MEDIA**.

### <a name="local-default-path"></a>Ruta de acceso predeterminada local

FileX también proporciona una ruta de acceso predeterminada específica del subproceso que permite que distintos subprocesos tengan rutas de acceso únicas sin conflicto. La aplicación proporciona la estructura **FX_LOCAL_PATH** durante las llamadas a **_fx_directory_local_path_set_ *_ y _* _fx_directory_local_path_restore_** para modificar la ruta de acceso local para el subproceso que realiza la llamada.

Si hay una ruta de acceso local, la ruta de acceso local tiene prioridad sobre la ruta de acceso del medio predeterminado global. Si no se configura la ruta de acceso local o si se borra con el servicio ***fx_directory_local_path_clear***, la ruta de acceso predeterminada global del medio se usará una vez más.

## <a name="file-description"></a>Descripción del archivo

FileX admite nombres de archivo largos y de caracteres 8.3 estándar con extensiones de tres caracteres. Además del nombre ASCII, cada entrada de archivo contiene los atributos de la entrada, la última fecha y hora modificada, el índice de clúster inicial y el tamaño en bytes de la entrada.

### <a name="file-allocation"></a>Asignación de archivos

FileX admite el esquema de asignación de clústeres estándar del formato FAT. Además, FileX admite la asignación de clústeres previa de clústeres contiguos. Para adaptar esto, cada archivo FileX se crea sin ningún clúster asignado. Los clústeres se asignan en solicitudes de escritura subsiguientes o en solicitudes ***fx_file_allocate*** para la asignación de clústeres contiguos previa.

En la ilustración 4, "Ejemplo de archivo FileX FAT-16", se muestra un archivo denominado ***FILE.TXT*** con dos clústeres secuenciales asignados a partir del clúster 101, un tamaño de 26 y el alfabeto como los datos del primer clúster de datos del archivo, 101.

### <a name="file-access"></a>Acceso a archivos

Un archivo FileX se puede abrir varias veces simultáneamente para el acceso de lectura. Sin embargo, un archivo solo puede abrirse una vez para la escritura. La información que se usa para admitir el acceso a archivos se incluye en el bloque de control de archivos ***FX_FILE***.

> [!NOTE]
> *Tenga en cuenta que el controlador del medio puede establecer dinámicamente la protección de escritura. Si ocurre esto, todas las solicitudes de escritura se rechazarán, así como los intentos de abrir un archivo para escritura.*

### <a name="file-layout-in-exfat"></a>Diseño de archivo en exFAT

El diseño de exFAT no requiere que se mantenga la cadena FAT para un archivo si los datos se almacenan en clústeres contiguos. El bit *NoFATChain* de la entrada de directorio de extensión de flujo indica si se debe usar o no la cadena FAT al leer datos del archivo. Si se establece *NoFATChain*, FileX lee secuencialmente del clúster indicado en el campo de *primer clúster* de la entrada de directorio de extensión de flujo.

Por otro lado, si *NoFATChain* está claro, FileX seguirá la cadena FAT para recorrer todo el archivo, de forma similar a la cadena FAT de FAT12/16/32.

En la ilustración 3 se muestran dos archivos de ejemplo, uno que no requiere cadena FAT y otro que sí.

## <a name="system-information"></a>Información del sistema

La información del sistema FileX consiste en realizar un seguimiento de las instancias del medio abiertas y mantener la fecha y hora del sistema global.

![Archivo con clústeres contiguos frente a un archivo que requiere un vínculo de FAT](./media/user-guide/system-information.png)

**ILUSTRACIÓN 3. Archivo con clústeres contiguos frente a un archivo que requiere un vínculo de FAT**

De forma predeterminada, la fecha y hora del sistema se establecen en la fecha de la última versión de FileX. Para tener una fecha y hora del sistema precisa, la aplicación debe llamar a ***fx_system_time_set** _ y _ *_fx_system_date_set_** durante la inicialización.

### <a name="system-date"></a>Fecha del sistema

La fecha del sistema FileX se mantiene en la variable ***_fx_system_date*** global. En cuanto a los bits, del 15 al 9 contienen el desplazamiento anual desde 1980, del 8 al 5 contienen el desplazamiento mensual y del 4 al 0 contienen el día. |

### <a name="system-time"></a>Hora del sistema

La hora del sistema FileX se mantiene en la variable ***_fx_system_time*** global. En cuanto a los bits, del 15 al 11 contienen las horas, del 10 al 5 contienen los minutos y del 4 al 0 contienen los medios segundos.

### <a name="periodic-time-update"></a>Actualización de hora periódica

Durante la inicialización del sistema, FileX crea un temporizador de aplicación ThreadX para actualizar periódicamente la fecha y hora del sistema. La velocidad a la que se actualiza la fecha y hora del sistema viene determinada por dos constantes utilizadas por la función ***_fx_system_initialize***.

Las constantes **FX_UPDATE_RATE_IN_SECONDS** y **FX_UPDATE_RATE_IN_TICKS** representan el mismo período de tiempo. La constante **FX_UPDATE_RATE_IN_TICKS** es el número de tics del temporizador ThreadX que representa el número de segundos especificado por la constante **FX_UPDATE_RATE_IN_SECONDS**. La constante **FX_UPDATE_RATE_IN_SECONDS** especifica el número de segundos existente entre cada actualización de hora de FileX. Por lo tanto, el tiempo de FileX interno se incrementa en intervalos de **FX_UPDATE_RATE_IN_SECONDS**. Estas constantes se pueden proporcionar durante la compilación de **_fx_system_initialize_ *_, o el desarrollador puede modificar los valores predeterminados encontrados en el archivo _* _fx_port.h_** de la versión FileX.

El temporizador de FileX periódico solo se utiliza para actualizar la fecha y hora del sistema global, que se usa únicamente para la marca de tiempo de archivo. Si la marca de tiempo no es necesaria, basta con definir **FX_NO_TIMER** al compilar **_fx_system_initialize.c_** para eliminar la creación del temporizador periódico de FileX.

![Ejemplo de archivo FileX FAT-16](./media/user-guide/fat-16-file-example.png)

**ILUSTRACIÓN 4. Ejemplo de archivo FileX FAT-16**
