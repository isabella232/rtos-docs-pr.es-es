---
title: Compatibilidad con Azure RTOS LevelX NAND
description: La memoria flash NAND se utiliza normalmente dentro de LevelX para el almacenamiento de datos de gran tamaño, que es habitual en los sistemas de archivos.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3286e4ea7f16b28ff55fc95a87a1e0c313ec4240
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814898"
---
# <a name="chapter-3---azure-rtos-levelx-nand-support"></a>Capítulo 3: Compatibilidad con Azure RTOS LevelX NAND

La memoria flash NAND se utiliza normalmente para el almacenamiento de datos de gran tamaño, que es habitual en los sistemas de archivos. La memoria NAND consta de *bloques*. Dentro de cada bloque NAND hay una serie de *páginas*. Los bloques NAND se pueden borrar, lo que significa que todas las páginas del bloque NAND se borran (se establecen en todas). Cada página de bloque NAND tiene un conjunto de *bytes de reserva* que usa Azure RTOS LevelX para la contabilidad, la administración de bloques defectuosa y la detección de errores. Las páginas de bloque NAND están disponibles en varios tamaños. Los tamaños de página más comunes son: 

| **Tamaño de página** | **Bytes de reserva** |
| ------------- | --------------- |
| 256           | 8               |
| 512           | 16              |
| 2048          | 64              |

La memoria NAND se diferencia de la memoria NOR en que no hay acceso directo, es decir, la memoria NAND no se puede leer directamente desde el procesador como la memoria NOR. La memoria NAND solo se puede escribir después de un borrado un número limitado de veces. Nuevamente, esto difiere de la memoria NOR que se puede escribir un número ilimitado de veces siempre que la solicitud de escritura borre los bits establecidos. Por último, los bytes de reserva asociados a cada página son únicos en flash NAND. Las configuraciones de bytes de reserva típicas son como se muestra en la tabla siguiente.

| **Bytes de reserva** | **Números de bytes** | **Configuración**     |
| ------------------------- | -------------- | --------------------- |
| 8                         | Bytes 0-2:     | Bytes ECC             |
|                           | Bytes 3,4,6,7: | Asignación del sector LevelX |
|                           | Byte 5:        | Marca de bloque incorrecto        |
| 16                        | Bytes 0-3,6-7: | Bytes ECC             |
|                           | Bytes 8-11:    | Asignación del sector LevelX |
|                           | Bytes 12-15:   | No utilizado                |
|                           | Byte 5:        | Marca de bloque incorrecto        |
| 64                        | Byte 0:        | Marca de bloque incorrecto        |
|                           | Bytes 2-5:     | Asignación del sector LevelX |
|                           | Bytes 6-39:    | No utilizado                |
|                           | Bytes 40-63:   | Bytes ECC             |

LevelX emplea 4 de los bytes de reserva de cada página NAND para realizar un seguimiento del sector lógico asignado a la página física NAND. Estos 4 bytes se utilizan para implementar un entero sin signo de 32 bits con un formato de propietario LevelX. El bit superior del campo de 32 bits (bit 31) se usa para indicar que la asignación de sector a página lógica es válida. Si este bit es 0, la información de esta página ya no es válida. El siguiente bit (bit 30) se usa para indicar que esta página está en proceso de ser obsoleta y se está escribiendo un nuevo sector. El bit 29 se usa para indicar cuándo se ha completado la escritura de la entrada de asignación. Si el bit 29 es 0, se completa la escritura de la entrada de asignación. Si se establece el bit 29, la entrada de asignación estaba en proceso de escritura. Los bits 30 y 29 se usan para recuperarse de una posible pérdida de energía mientras se actualiza una nueva página Flash. Por último, los 29 bits inferiores (28-0) contienen el número de sector lógico de la página.

**Entrada de asignación LevelX**

| Bit(s) | Significado |
| ------ | ------- |
| 31     | Marca válida. Cuando se establece y el sector lógico no son todos, indica que la asignación es válida |
| 30     | Marca obsoleta. Cuando está desactivada, esta asignación es obsoleta o está en proceso de ser obsoleta. |
| 29     | La escritura de entradas de asignación se completa cuando este bit es 0 |
| 0-28   | Sector lógico asignado a esta página física: no todos. |

LevelX también emplea la primera página de cada bloque NAND para el recuento de borrado de bloques, así como la lista de páginas asignadas cuando el bloque está lleno. A continuación se muestra el formato de la primera página de un bloque NAND en LevelX:

| LevelX formato de página 0 de bloque |
|:--------------------------:|
| [Recuento de borrado de bloques]        |
| [Asignación del sector de la página 1]    |
| ...                        |
| [Asignación del sector de la página "n"]  |
| [0xF0F0F0F0]               |

> [!NOTE]
> La información de asignación de páginas solo se escribe cuando el bloque está lleno, es decir, se han escrito todas las páginas del bloque. Esto permite una búsqueda más rápida de páginas gratuitas y la asignación de sectores lógicos durante el tiempo de ejecución.

## <a name="nand-bad-block-support"></a>Compatibilidad con bloques erróneos NAND

La memoria NAND tiene también más probabilidades de tener bloques no válidos que la memoria NOR. Esto se debe en gran medida a que los fabricantes de la NAND pueden aumentar la suspensión, ya que permiten bloques incorrectos y requieren software para solucionar estos bloques incorrectos. LevelX manipula la administración de bloques erróneos NAND simplemente mediante la asignación de bloques no válidos.

LevelX también proporciona API para códigos de corrección de errores de Hamming (ECC) de 256 bytes para que el controlador LevelX subyacente los utilice para calcular nuevos códigos ECC o para realizar una corrección de errores de 1 bit en la lectura de la página dentro de cada sección de 256 bytes de la página.

## <a name="nand-driver-requirements"></a>Requisitos para controladores NAND

LevelX requiere un controlador flash NAND subyacente que sea específico de la parte Flash subyacente y de la implementación de hardware. El controlador se especifica en LevelX durante la inicialización a través de la API ***lx_nand_flash_open***. El prototipo del controlador LevelX es el siguiente.

```c
INT nand_driver_initialize(LX_NAND_FLASH *instance);
```

El parámetro *instancia* especifica el bloque de control de LevelX NAND. La función de inicialización de controladores es responsable de configurar todos los demás servicios de nivel de controlador para la instancia de LevelX asociada. Los servicios necesarios para cada instancia de LevelX NAND se muestran en la lista siguiente.

- Leer página
- Escribir página
- Borrado de bloque
- Comprobación de bloque borrado
- Comprobación de página borrada
- Estado de bloque get
- Estado de bloque set
- Bytes adicionales del bloque get
- Bytes adicionales del bloque set
- Controlador de errores del sistema

## <a name="driver-initialization"></a>Inicialización del controlador

Estos servicios se configuran mediante el establecimiento de punteros de función en la instancia de **LX_NAND_FLASH** dentro de la función de inicialización del controlador. La función de inicialización del controlador también especifica el número total de bloques, páginas por bloque, bytes por página y un área de RAM lo suficientemente grande como para leer una página en la memoria. La función de inicialización del controlador también realiza tareas adicionales de inicialización específicas del dispositivo o de la implementación antes de devolver **LX_SUCCESS**.

## <a name="driver-read-page"></a>Página de lectura del controlador

El servicio "página de lectura" del controlador NAND LevelX es responsable de leer una página específica en un bloque específico del flash NAND. Todas las comprobaciones de errores y la lógica de corrección son responsabilidad del servicio de controlador. Si se realiza correctamente, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NAND devuelve **LX_ERROR**. A continuación se proporciona el prototipo del servicio "leer página" del controlador LevelX NAND.

```c
INT nand_driver_read_page(
    ULONG block,
    ULONG page,
    ULONG *destination, 
    ULONG words);
```

Donde el *bloque* y la *página* identifican la página que se va a leer y el *destino*, y las *palabras* especifican dónde se debe colocar el contenido de la página y cuántas palabras de 32 bits se van a leer.

## <a name="driver-write-page"></a>Página de escritura del controlador

El servicio "página de escritura" del controlador NAND LevelX es responsable de escribir una página específica en el bloque especificado del flash NAND. La comprobación de errores y el cálculo ECC son responsabilidad del servicio de controlador. Si se realiza correctamente, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NAND devuelve **LX_ERROR**. A continuación se muestra el prototipo del servicio "página de escritura" del controlador LevelX NAND.

```c
INT nand_driver_write_page(
    ULONG block, 
    ULONG page,
    ULONG *source, 
    ULONG words);
```

Donde el *bloque* y la *página* identifican la página que se va a escribir y el *origen* y las *palabras* especifican el origen de la escritura y el número de palabras de 32 bits que se van a escribir.

> [!NOTE]
> LevelX se basa en el controlador para la detección de errores de bajo nivel al escribir en la página Flash, lo que normalmente implica volver a leer la página y compararla con el búfer de escritura para asegurarse de que la escritura se realizó correctamente.

## <a name="driver-block-erase"></a>Borrado de bloque de controlador

El servicio "eliminación de bloques" del controlador NAND LevelX es responsable de borrar el bloque especificado del flash NAND. Si se realiza correctamente, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NAND devuelve **LX_ERROR**. El prototipo del servicio "borrado de bloque" de LevelX NAND es el siguiente.

```c
INT nand_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Donde *bloque* identifica el bloque que se va a borrar. El parámetro *erase_count* se proporciona con fines de diagnóstico. Por ejemplo, el controlador puede querer alertar a otra parte del software de la aplicación cuando el recuento de borrado supera un umbral específico.

> [!NOTE]
> LevelX se basa en el controlador para la detección de errores de bajo nivel cuando se borra el bloque, lo que normalmente implica asegurarse de que todas las páginas del bloque son todas.

## <a name="driver-block-erased-verify"></a>Comprobación de borrado de bloque de controlador

El servicio "comprobación de borrado de bloque" del controlador LevelX es responsable de comprobar que se borra el bloque especificado del flash NAND. Si se borra, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si no se borra el bloque, el controlador LevelX NAND devuelve **LX_ERROR**. El prototipo del servicio "comprobación de borrado de bloque" del controlador LevelX NAND es el siguiente:

```c
INT nand_driver_block_erased_verify(ULONG block);
```

Donde *bloque* especifica el bloque que se va a comprobar que se ha borrado.

> [!NOTE]
> LevelX se basa en el controlador para examinar todas las páginas y todos los bytes de cada página, incluidos los bytes de reserva y de datos, para asegurarse de que se borran (contienen todos ellos).

## <a name="driver-page-erased-verify"></a>Comprobación de borrado de la página del controlador

El servicio LevelX NAND "comprobación de borrado de página" es responsable de comprobar que la página especificada del bloque especificado del flash NAND está borrada. Si se borra, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si la página no se borra, el controlador LevelX NAND devuelve **LX_ERROR**. El prototipo del servicio LevelX NAND "comprobación de borrado de página" es:

```c
INT nand_driver_page_erased_verify(
    ULONG block,  
    ULONG page);
```
Donde *bloque* especifica qué bloque y *página* especifica la página para comprobar que se ha borrado.

> [!NOTE]
> LevelX se basa en el controlador para examinar todos los bytes de la página especificada, incluidos los bytes de reserva y de datos, para asegurarse de que se borran (contienen todos ellos).

## <a name="driver-block-status-get"></a>Estado del bloque de controlador get

El servicio "estado del bloque get" del controlador NAND LevelX es responsable de recuperar la marca de bloque incorrecto del bloque especificado del flash NAND. Si se realiza correctamente, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NAND devuelve **LX_ERROR**. El prototipo del servicio "estado del bloque get" del controlador LevelX NAND es: se muestra a continuación.

```c
INT nand_driver_block_status_get(
    ULONG block,  
    UCHAR *bad_block_byte);
```

Donde *bloque* especifica qué bloque y *bad_block_byte* especifican el destino de la marca de bloque erróneo.

## <a name="driver-block-status-set"></a>Estado de bloque del controlador set

El servicio "estado de bloque set" del controlador NAND LevelX es responsable de establecer la marca de bloque erróneo del bloque especificado del flash NAND. Si se realiza correctamente, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NAND devuelve **LX_ERROR**. El prototipo del servicio "estado de bloque set" del controlador LevelX NAND es:

```c
INT nand_driver_block_status_set(
    ULONG block,
    UCHAR bad_block_byte);
```

Donde *bloque* especifica qué bloque y *bad_block_byte* especifican el valor de la marca de bloque erróneo.

## <a name="driver-block-extra-bytes-get"></a>Bytes adicionales del bloque de controlador get

El servicio del controlador LevelX NAND "bytes adicionales del bloque get" es responsable de recuperar los bytes adicionales asociados a una página específica de un bloque específico del flash NAND. Si se realiza correctamente, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NAND devuelve **LX_ERROR**. El prototipo del servicio "bytes adicionales del bloque get" del controlador LevelX NAND es:

```c
INT nand_driver_block_extra_bytes_get(
    ULONG block,  
    ULONG page, 
    UCHAR *destination, 
    UINT size);
```

Donde *bloque* especifica qué bloque, *página* especifica la página y el *destino* específicos especifican el destino de los bytes adicionales. El *tamaño* del parámetro especifica el número de bytes adicionales que se van a obtener.

## <a name="driver-block-extra-bytes-set"></a>Bytes adicionales del bloque de controlador set

El servicio del controlador LevelX NAND "bytes adicionales de bloque set" es responsable de establecer bytes adicionales en una página específica de un bloque específico del flash NAND. Si se realiza correctamente, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NAND devuelve **LX_ERROR**. El prototipo del servicio del controlador LevelX NAND "bytes adicionales de bloque set" es:

```c
INT nand_driver_block_extra_bytes_set(
    ULONG block,  
    ULONG page, 
    UCHAR *source, 
    UINT size);
```

Donde *bloque* especifica qué bloque, *página* especifica la página y el *origen* específicos especifican el origen de los bytes adicionales. El *tamaño* del parámetro especifica el número de bytes adicionales que se van a establecer.

## <a name="driver-system-error"></a>Error del sistema de controladores

El servicio "errores del sistema" del controlador NAND LevelX es responsable de establecer el control de los errores del sistema detectados por LevelX. El procesamiento en esta rutina depende de la aplicación. Si se realiza correctamente, el controlador LevelX NAND devuelve **LX_SUCCESS**. Si no se realiza correctamente, el controlador LevelX NAND devuelve **LX_ERROR**. El prototipo del servicio "error del sistema" del controlador NAND LevelX es:

```c
INT nand_driver_system_error(
    UINT error_code,  
    ULONG block, 
    ULONG page);
```

Donde *bloque* especifica el bloque y la *página* especifican la página específica en que se produjo el error representada por *error_code*.

## <a name="nand-simulated-driver"></a>Controlador simulado NAND

LevelX proporciona un controlador flash NAND simulado que simplemente usa RAM para simular el funcionamiento de una parte flash NAND. De manera predeterminada, el controlador simulado NAND proporciona 8 bloques flash NAND con 16 páginas por bloque y 2048 bytes por página.

La función de inicialización del controlador flash NAND simulado es ***lx_nand_flash_simulator_initialize** _ y se define en _ *_lx_nand_flash_simulator.c_**. Este controlador también proporciona una buena plantilla para escribir controladores flash NAND específicos.

## <a name="nand-filex-integration"></a>Integración de FileX NAND

Como se mencionó anteriormente, LevelX no se basa en FileX para su funcionamiento. El software de la aplicación puede llamar directamente a todas las API de LevelX para almacenar o recuperar datos sin procesar en los sectores lógicos proporcionados por LevelX. Sin embargo, LevelX también admite FileX.

El archivo ***fx_nand_flash_simulated_driver.c*** contiene un controlador FileX de ejemplo para su uso con la simulación flash NAND. Un aspecto interesante de este controlador es que combina los sectores lógicos de 512 bytes que usa normalmente FileX en las solicitudes de lectura y escritura de un solo sector lógico en el simulador LevelX mediante páginas de 2048 bytes. Esto da como resultado un uso más eficaz de la memoria flash NAND. El controlador FileX flash NAND para LevelX proporciona un buen punto de partida para escribir controladores FileX personalizados.  
  
> [!NOTE]
> El formato Flash FileX NAND debe ser un tamaño de bloque completo de sectores inferior al que proporciona flash NAND. Esto le ayudará a garantizar el mejor rendimiento durante el procesamiento de nivel de desgaste. Las técnicas adicionales para mejorar el rendimiento de escritura en el algoritmo de nivelación de desgaste de LevelX son las siguientes.

1. Asegúrese de que todas las escrituras tienen exactamente uno o más clústeres de tamaño y comience en los límites exactos del clúster.
1. Asigne previamente los clústeres antes de realizar operaciones de escritura de archivos grandes a través de la clase de FileX ***fx_file_allocate*** de las API.
1. Asegúrese de que el controlador FileX está habilitado para recibir información del sector de la versión y que las solicitudes realizadas al controlador para liberar sectores se controlen en el controlador mediante una llamada a ***lx_nor_flash_sector_release***.
1. Uso periódico de ***lx_nand_flash_defragment*** para liberar tantos bloques NAND como sea posible y, por tanto, mejorar el rendimiento de escritura.
1. Use la API de ***lx_nand_flash_extended_cache_enable*** para proporcionar una memoria caché de RAM de varios recursos de bloque NAND para obtener un rendimiento más rápido.
