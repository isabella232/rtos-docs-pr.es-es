---
title: 'Capítulo 5: Soporte técnico de Azure RTOS LevelX NOR'
description: La memoria flash NOR se compone de bloques que normalmente se pueden dividir de forma uniforme por 512 bytes. Azure RTOS LevelX divide cada bloque flash NOR en bloques lógicos de 512 bytes.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3a0c73c2b45c32bf3f1ef56de684fa83c334b59e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814893"
---
# <a name="chapter-5---azure-rtos-levelx-nor-support"></a>Capítulo 5: Soporte técnico de Azure RTOS LevelX NOR

La memoria flash NOR se compone de *bloques* que normalmente se pueden dividir de forma uniforme por 512 bytes. No existe el concepto de una *página* flash en la memoria flash NOR. Además, no hay bytes de *reserva* en la memoria flash NOR, por lo que Azure RTOS LevelX debe usar la propia memoria flash NOR para toda la información de administración. El acceso de lectura directo es posible en la memoria flash NOR. Normalmente, el acceso de escritura requiere una secuencia especial de operaciones. La memoria flash NOR se puede escribir varias veces, siempre que se borren los bits. Los bits en la memoria flash NOR solo se pueden establecer una vez, a través de la operación de borrado de bloque.

LevelX divide cada bloque flash NOR en *sectores* lógicos de 512 bytes. Además, LevelX usa los primeros sectores "n" de cada bloque flash NOR para almacenar información de administración. El formato de la información de administración de la memoria flash NOR LevelX es:

**Formato de bloque NOR LevelX**

| Desplazamiento de byte  | Contenido                     |
| ------------ | ---------------------------- |
| 0            | [Recuento de borrado de bloques]          |
| 4            | [Minimum Mapped Sector]      |
| 8            | [Maximum Mapped Sector]      |
| 12           | [Mapa de bits del sector libre]        |
| m            | [Entrada de asignación de sector 0]     |
|              | …                            |
| m+4*(n-1)    | [Entrada de asignación de sector "n"]   |
|              | …                            |
| s            | [Contenido del sector 0]          |
|              | …                            |
| s+512*(n-1) | [Contenido del sector "n"]         |

El *recuento de borrado de bloques* de 32 bits contiene el número de veces que se ha borrado el bloque. El objetivo principal de LevelX es mantener el número de borrado de todos los bloques relativamente cerca para ayudar a evitar que un bloque no se conserve prematuramente. Los campos de 32 bits del *sector asignado mínimo* y del *sector asignado máximo* solo se escriben cuando se han asignado y escrito todos los sectores lógicos del bloque. Estos campos son útiles para la optimización de la operación de lectura del sector. La entrada de *mapa de bits del sector libre* es un mapa de bits en el que cada bit establecido corresponde a un sector sin asignar del bloque. Este campo se usa para hacer que la búsqueda del sector libre sea más eficiente. Se trata de un campo de longitud variable que requiere una palabra por cada 32 sectores del bloque. La matriz de la *entrada de asignación de sectores* contiene información de asignación para cada sector del bloque. Cada entrada tiene los siguientes datos:

**Entrada de asignación de sectores**

| Bit(s) | Significado  |
| ------ | -------- |
| 31     | Marca válida. Cuando se establece un sector lógico, no todos indican que la asignación es válida |
| 30     | Marca obsoleta. Cuando está desactivada, esta asignación es obsoleta o está en proceso de ser obsoleta. |
| 29     | La escritura de entradas de asignación se completa cuando este bit es 0 |
| 0-28   | Sector lógico asignado a este sector físico: no todos. |

El bit superior del campo de 32 bits (bit 31) se usa para indicar que la asignación del sector lógico es válida. Si este bit es 0, la información de esta entrada (y el contenido del sector correspondiente) ya no es válida. El siguiente bit (bit 30) se usa para indicar que este sector está en proceso de ser obsoleto y se está escribiendo un nuevo sector. El bit 29 se usa para indicar cuándo se ha completado la escritura de la entrada de asignación. Si el bit 29 es 0, se completa la escritura de la entrada de asignación. Si se establece el bit 29, la entrada de asignación estaba en proceso de escritura. Los bits 30 y 29 se usan para recuperarse de una posible pérdida de energía mientras se actualiza una nueva asignación de sectores. Por último, los 29 bits inferiores (28-0) contienen el número de sector lógico del sector. Si un sector no se ha asignado, se establecerán todos los bits, es decir, tendrá un valor de 0xFFFFFFFF.

## <a name="nor-driver-requirements"></a>Requisitos para controladores NOR

LevelX requiere un controlador flash NOR subyacente que sea específico de la parte flash subyacente y de la implementación de hardware. El controlador se especifica en LevelX durante la inicialización a través de la API ***lx_nor_flash_open***. El prototipo del controlador LevelX es:

```c
INT nor_driver_initialize(LX_NOR_FLASH *instance);
```

El parámetro "*instancia*" el bloque de control LevelX NOR. La función de inicialización de controladores es responsable de configurar todos los demás servicios de nivel de controlador para la instancia de LevelX asociada. Los servicios necesarios para cada instancia LevelX NOR son:

- Leer sector
- Escribir sector
- Borrado de bloque
- Comprobación de bloque borrado
- Controlador de errores del sistema

## <a name="driver-initialization"></a>Inicialización del controlador

Estos servicios se configuran mediante el establecimiento de punteros de función en la instancia de **LX_NOR_FLASH** dentro de la función de inicialización del controlador. La función de inicialización del controlador también es responsable de:

1. Especificar la dirección base del flash.
1. Especificar el número total de bloques y el número de palabras por bloque.
1. Un búfer de RAM para leer un sector de flash (512 bytes) y alineado para el acceso ULONG.

La función de inicialización del controlador también realiza tareas adicionales de inicialización específicas del dispositivo o de la implementación antes de devolver **LX_SUCCESS**.

## <a name="driver-read-sector"></a>Sector de lectura del controlador

El servicio de "sector de lectura" del controlador LevelX NOR es responsable de leer un sector específico en un bloque específico de la memoria flash NOR. Todas las comprobaciones de errores y la lógica de corrección son responsabilidad del servicio de controlador. Si se realiza correctamente, el controlador LevelX NOR devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NOR devuelve *LX_ERROR*. El prototipo del servicio de "sector de lectura" del controlador LevelX NOR es:

```c
INT nor_driver_read_sector(
    ULONG *flash_address,
    ULONG *destination, 
    ULONG words);
```

Donde "*flash_address*" especifica la dirección de un sector lógico dentro de un bloque de memoria flash NOR y "*destino*" y "*palabras*" especifican dónde colocar el contenido del sector y cuántas palabras de 32 bits se van a leer.

## <a name="driver-write-sector"></a>Sector de escritura de controladores

El servicio de "sector de escritura" del controlador LevelX NOR es responsable de escribir un sector específico en un bloque de la memoria flash NOR. La comprobación de errores es responsabilidad del servicio de controlador. Si se realiza correctamente, el controlador LevelX NOR devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NOR devuelve **LX_ERROR**. El prototipo del servicio de "sector de escritura" del controlador LevelX NOR es:

```c
INT nor_driver_write_sector(
    ULONG *flash_address,
    ULONG *source, 
    ULONG words);
```

Donde "*flash_address*" especifica la dirección de un sector lógico dentro de un bloque de memoria flash NOR y "*origen*" y "*palabras*" especifican el origen de la escritura y el número de palabras de 32 bits que se van a escribir.

> [!NOTE]
> LevelX se basa en el controlador para comprobar que el sector de escritura se ha realizado correctamente. Normalmente, esto se realiza leyendo el valor programado para asegurarse de que coincida con el valor solicitado que se va a escribir.

## <a name="driver-block-erase"></a>Borrado de bloque de controlador

El servicio de "borrado de bloques" del controlador LevelX NOR es responsable de borrar el bloque especificado de la memoria flash NOR. Si se realiza correctamente, el controlador LevelX NOR devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NOR devuelve **LX_ERROR**. El prototipo del servicio de "borrado de bloques" del controlador LevelX NOR es:

```c
INT nor_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Donde "*bloque*" identifica el bloque NOR que se va a borrar. El parámetro "*erase_count*" se proporciona con fines de diagnóstico. Por ejemplo, el controlador puede querer alertar a otra parte del software de la aplicación cuando el recuento de borrado supera un umbral específico.

> [!NOTE]
> LevelX se basa en el controlador para examinar todos los bytes del bloque con el fin de asegurarse de que se borran (contienen todos).

## <a name="driver-block-erased-verify"></a>Comprobación de borrado de bloque de controlador

El servicio de "comprobación de borrado de bloque" del controlador LevelX NOR es responsable de verificar que se borre el bloque especificado de la memoria flash NOR. Si se borra, el controlador LevelX NOR devuelve **LX_SUCCESS**. Si no se borra el bloque, el controlador LevelX NOR devuelve **LX_ERROR**. El prototipo del servicio de "comprobación de borrado de bloque" del controlador LevelX NOR es:

```c
INT nor_driver_block_erased_verify(ULONG block);
```

Donde "*bloque*" especifica el bloque que se va a comprobar que se ha borrado.

> [!NOTE]
> LevelX se basa en el controlador para examinar todos los bytes del especificado para asegurarse de que se borran (contienen todos).

## <a name="driver-system-error"></a>Error del sistema de controladores

El servicio "controlador de errores del sistema" del controlador LevelX NOR es responsable de configurar el manejo de errores del sistema detectados por LevelX. El procesamiento en esta rutina depende de la aplicación. Si se realiza correctamente, el controlador LevelX NOR devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NOR devuelve **LX_ERROR**. El prototipo del servicio de "error del sistema" del controlador LevelX NOR es:

```c
INT nor_driver_system_error(UINT error_code);
```

Donde "*error_code*" representa el error que se ha producido.

## <a name="nor-simulated-driver"></a>Controlador simulado NOR

LevelX proporciona un controlador flash NOR simulado que simplemente usa RAM para simular el funcionamiento de una parte flash NOR. De manera predeterminada, el controlador simulado NOR proporciona 8 bloques flash NOR con 16 sectores de 512 bytes por bloque.

La función de inicialización del controlador flash NOR simulado es ***lx_nor_flash_simulator_initialize** _ y está definida en _ *_lx_nor_flash_simulator.c_**. Este controlador también proporciona una buena plantilla para escribir controladores de flash NOR específicos.

## <a name="nor-filex-integration"></a>Integración de FileX NOR

Como se mencionó anteriormente, LevelX no se basa en FileX para su funcionamiento. El software de la aplicación puede llamar directamente a todas las API de LevelX para almacenar o recuperar datos sin procesar en los sectores lógicos proporcionados por LevelX. Sin embargo, LevelX también admite FileX.

El archivo ***fx_nor_flash_simulated_driver. c*** contiene un controlador de FileX de ejemplo para su uso con la simulación flash NOR. El controlador NOR flash FileX para LevelX proporciona un buen punto de partida para escribir controladores FileX personalizados.

> [!NOTE]
> El formato flash FileX NOR debe tener un tamaño de bloque completo de sectores menos de lo que proporciona el flash NOR. Esto le ayudará a garantizar el mejor rendimiento durante el procesamiento de nivel de desgaste. Las técnicas adicionales para mejorar el rendimiento de escritura en el algoritmo de nivelación de desgaste de LevelX incluyen:
> 1. Asegúrese de que todas las escrituras tienen exactamente uno o más clústeres de tamaño y comience en los límites exactos del clúster.
> 2. Asigne previamente los clústeres antes de realizar operaciones de escritura de archivos grandes a través de la clase de FileX ***fx_file_allocate*** de las API.
> 3.  Uso periódico de ***lx_nor_flash_defragment*** para liberar tantos como bloques NOR como sea posible y mejorar el rendimiento de escritura.
> 4. Asegúrese de que el controlador FileX está habilitado para recibir información del sector de la versión y que las solicitudes realizadas al controlador para liberar sectores se controlen en el controlador mediante una llamada a ***lx_nor_flash_sector_release***.
