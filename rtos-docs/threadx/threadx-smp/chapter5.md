---
title: 'Capítulo 5: Controladores de dispositivo para Azure RTOS ThreadX SMP'
description: Este capítulo contiene una descripción de los controladores de dispositivo de Azure RTOS ThreadX SMP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 706ad47b2c3e7b2979da7262a4de8d681f4fbc53cb1af59a798b34094734060b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792350"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a>Capítulo 5: Controladores de dispositivo para Azure RTOS ThreadX SMP

Este capítulo contiene una descripción de los controladores de dispositivo de Azure RTOS ThreadX SMP. La información que se presenta en este capítulo está diseñada para ayudar a los desarrolladores a escribir controladores específicos de la aplicación. 

## <a name="device-driver-introduction"></a>Introducción al controlador de dispositivo

La comunicación con el entorno externo es un componente importante de la mayoría de las aplicaciones insertadas. Esta comunicación se realiza a través de dispositivos de hardware que son accesibles para el software de la aplicación insertada. Los componentes de software responsables de administrar dichos dispositivos se denominan normalmente *controladores de dispositivo*.

Los controladores de dispositivo de los sistemas en tiempo real integrados dependen de las aplicaciones de forma inherente. Esto es así por dos motivos principales: la gran diversidad del hardware de destino y los requisitos de rendimiento igualmente amplios que afectan a las aplicaciones en tiempo real. Por esta razón, es prácticamente imposible proporcionar un conjunto común de controladores que cumplan los requisitos de cada aplicación. La información de este capítulo, por tanto, se ha diseñado para ayudar a los usuarios a personalizar los controladores de dispositivo de ThreadX SMP *comerciales* y a escribir sus propios controladores específicos.

## <a name="driver-functions"></a>Funciones de controlador

Los controladores de dispositivo de ThreadX SMP se componen de ocho áreas funcionales básicas, como se indica a continuación:

- **Inicialización del controlador**
- **Control del controlador**
- **Acceso al controlador**
- **Entrada al controlador**
- **Salida del controlador**
- **Interrupciones del controlador**
- **Estado del controlador**
- **Finalización del controlador**

Con la excepción de la inicialización, las demás áreas funcionales del controlador son opcionales. Además, el procesamiento exacto de cada área es específico del controlador de dispositivo.

### <a name="driver-initialization"></a>Inicialización del controlador 
Esta área funcional es responsable de la inicialización del dispositivo real de hardware y de las estructuras de datos internas del controlador. No se puede llamar a otros servicios del controlador mientras no se complete la inicialización.

> [!IMPORTANT]
> Normalmente, se llama al componente de la función de inicialización del controlador desde la función **tx_application_define** o desde un subproceso de inicialización.

### <a name="driver-control"></a>Control del controlador 
Una vez que el controlador se inicializa y está listo para su funcionamiento, esta área funcional es responsable del control en tiempo de ejecución. Normalmente, este control consiste en realizar cambios en el dispositivo de hardware subyacente. Entre los ejemplos se incluyen el cambio de la velocidad en baudios de un dispositivo serie o la búsqueda de un nuevo sector en un disco.

### <a name="driver-access"></a>Acceso al controlador 
A algunos controladores de dispositivo solo se les llama desde un único subproceso de aplicación. En tales casos, no es necesaria esta área funcional. Sin embargo, en las aplicaciones en las que varios subprocesos necesitan acceso simultáneo al controlador, su interacción debe controlarse mediante la adición de recursos de asignación y liberación en el controlador de dispositivo. Como alternativa, la aplicación puede usar un semáforo para administrar el acceso al controlador y evitar una sobrecarga y una complicación adicionales dentro del controlador. 

### <a name="driver-input"></a>Entrada al controlador 
Esta área funcional es responsable de todas las entradas al dispositivo. Los principales problemas asociados a la entrada al controlador suelen tener que ver con el modo en que la entrada se almacena en el búfer y cómo esperan los subprocesos esa entrada. 

### <a name="driver-output"></a>Salida del controlador 
Esta área funcional es responsable de todas las salidas del dispositivo. Los principales problemas asociados con la salida del controlador suelen tener que ver con el modo en que la salida se almacena en el búfer y cómo esperan los subprocesos para realizar la salida. 

### <a name="driver-interrupts"></a>Interrupciones del controlador 
La mayoría de los sistemas en tiempo real se basan en interrupciones de hardware para notificar al controlador los eventos de entrada, salida, control y error del dispositivo. Las interrupciones proporcionan un tiempo de respuesta garantizado para estos eventos externos. En lugar de las interrupciones, el software del controlador puede comprobar periódicamente el hardware externo para detectar esos eventos. Esta técnica se conoce como *sondeo*. El sondeo no está tan próximo al tiempo real como las interrupciones, pero puede tener sentido en algunas aplicaciones que tampoco lo están. 

### <a name="driver-status"></a>Estado del controlador 
Esta área funcional es responsable de proporcionar el estado en tiempo de ejecución y las estadísticas asociadas al funcionamiento del controlador. Por lo general, la información administrada por esta área funcional incluye lo siguiente: 
- Estado actual del dispositivo
- Bytes de entrada
- Bytes de salida
- Recuentos de errores de dispositivos

### <a name="driver-termination"></a>Finalización del controlador 
Esta área funcional es opcional. Solo se precisa si es necesario apagar el controlador o el dispositivo de hardware físico. Una vez finalizado el controlador, no se debe volver a llamar hasta que se vuelva a inicializar. 

## <a name="simple-driver-example"></a>Ejemplo de un controlador simple

Un ejemplo es la mejor manera de describir un controlador de dispositivo. En este ejemplo, el controlador supone que existe un dispositivo de hardware serie simple con un registro de configuración, un registro de entrada y un registro de salida. En este ejemplo de controlador simple se muestran las áreas funcionales de inicialización, entrada, salida e interrupción.

### <a name="simple-driver-initialization"></a>Inicialización del controlador simple 
La función ***tx_sdriver_initialize*** del controlador simple crea dos semáforos de recuento que se usan para administrar las operaciones de entrada y salida del controlador. La ISR de entrada establece el semáforo de entrada cuando el dispositivo de hardware serie recibe un carácter. Por este motivo, el semáforo de entrada se crea con un recuento inicial de cero.

A su vez, el semáforo de salida indica la disponibilidad del registro de transmisión del dispositivo de hardware serie. Se crea con un valor de uno para indicar que el registro de transmisión está inicialmente disponible.

La función de inicialización también es responsable de instalar los controladores de vector de interrupción de bajo nivel para las notificaciones de entrada y salida. Al igual que otras rutinas de servicio de interrupción de ThreadX SMP, el controlador de bajo nivel debe llamar a * **_tx_thread_context_save** _ antes de llamar a la ISR del controlador simple. Cuando vuelve la ISR del controlador, el controlador de bajo nivel debe llamar a _*_ _tx_thread_context_restore_**.

> [!IMPORTANT]
> Es importante que se llame a la inicialización antes que a cualquier otra función del controlador. Normalmente, se llama a la inicialización del controlador desde **tx_application_define**.

Consulte la figura 9 para ver el código fuente de inicialización del controlador simple.

```C
VOID     tx_sdriver_initialize(VOID)
{

    /* Initialize the two counting semaphores used to control
       the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                       "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                       "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
       The initial vector handling should call the ISRs
       defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
       generation, baud rate, stop bits, etc. */
}
```
**FIGURA 9. Inicialización de un controlador simple**

### <a name="simple-driver-input"></a>Entrada al controlador simple 
La entrada al controlador simple se centra en el semáforo de entrada. Cuando se recibe una interrupción de entrada del dispositivo serie, se establece el semáforo de entrada. Si hay varios subprocesos esperando un carácter del controlador, se reanuda el subproceso que lleva esperando más tiempo. Si no hay ningún subproceso en espera, el semáforo simplemente permanece establecido hasta que un subproceso llama a la función de entrada al controlador.

Existen varias limitaciones en el control de entradas al controlador simple. La más importante es la posibilidad de que se quiten caracteres de la entrada. Esto se debe a que no hay ninguna opción para almacenar en búfer los caracteres de entrada que llegan antes de que se haya procesado el carácter anterior. Se puede solucionar fácilmente agregando un búfer de caracteres de entrada.

> [!IMPORTANT]
> Solo los subprocesos pueden llamar a la función **tx_sdriver_input**.

En la figura 10 se muestra el código fuente asociado a la entrada al controlador simple.

```C
UCHAR     tx_sdriver_input(VOID)
{

    /* Determine if there is a character waiting. If not,
        suspend. */
    tx_semaphore_get(&tx_sdriver_input_semaphore,
                                             TX_WAIT_FOREVER;
    /* Return character from serial RX hardware register. */
    return(*serial_hardware_input_ptr);
}

VOID     tx_sdriver_input_ISR(VOID)
{
    /* See if an input character notification is pending. */
    if (!tx_sdriver_input_semaphore.tx_semaphore_count)
    {
        /* If not, notify thread of an input character. */
        tx_semaphore_put(&tx_sdriver_input_semaphore);
    }
}
```
**FIGURA 10. Entrada al controlador simple**

### <a name="simple-driver-output"></a>Salida del controlador simple 
El procesamiento de la salida emplea el semáforo de salida para indicar si el registro de transmisión del dispositivo serie está libre. Antes de que un carácter de salida se escriba realmente en el dispositivo, se obtiene el semáforo de salida. Si no está disponible, significa que la transmisión anterior no ha finalizado todavía.

La ISR de salida es responsable de controlar la interrupción de transmisión completa. El procesamiento de la ISR de salida equivale a establecer el semáforo de salida, lo que permite la salida de otro carácter.

> [!IMPORTANT]
> Solo los subprocesos pueden llamar a la función **tx_sdriver_output**.

En la figura 11 se muestra el código fuente asociado con la salida del controlador simple.

```C
VOID     tx_sdriver_output(UCHAR alpha)
{

    /* Determine if the hardware is ready to transmit a
       character. If not, suspend until the previous output
        completes. */
    tx_semaphore_get(&tx_sdriver_output_semaphore,
                                            TX_WAIT_FOREVER);
    /* Send the character through the hardware. */
    *serial_hardware_output_ptr = alpha;
}

VOID     tx_sdriver_output_ISR(VOID)
{
    /* Notify thread last character transmit is
        complete. */
    tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
**FIGURA 11. Salida del controlador simple**

### <a name="simple-driver-shortcomings"></a>Limitaciones del controlador simple 
Este ejemplo de un controlador de dispositivo simple refleja la idea básica de un controlador de dispositivo de ThreadX SMP. Sin embargo, dado que el controlador de dispositivo simple no se ocupa del almacenamiento en búfer de datos ni de ningún problema de sobrecarga, no acaba de representar los controladores de ThreadX SMP del mundo real. En la sección siguiente se describen algunas de las cuestiones más avanzadas asociadas a los controladores de dispositivo.

## <a name="advanced-driver-issues"></a>Cuestiones de controladores avanzados

Como se mencionó anteriormente, los controladores de dispositivo tienen requisitos tan únicos como sus aplicaciones. Es posible que algunas aplicaciones requieran una cantidad enorme de almacenamiento en el búfer de datos, mientras que otra aplicación puede requerir una ISR de controlador optimizada debido a una gran frecuencia de las interrupciones de dispositivo.

### <a name="io-buffering"></a>Almacenamiento en búfer de E/S 
El almacenamiento en el búfer de datos de las aplicaciones insertadas en tiempo real requiere un planeamiento considerable. Parte del diseño viene determinado por el dispositivo de hardware subyacente. Si el dispositivo proporciona E/S de bytes básica, es probable que resulte conveniente un búfer circular simple. Sin embargo, si el dispositivo proporciona E/S en bloque, de DMA o de paquetes, es probable que esté justificado un esquema de administración de búferes. 

### <a name="circular-byte-buffers"></a>Búferes de bytes circulares 
Los búferes de bytes circulares se usan normalmente en controladores que administran un dispositivo de hardware serie simple como un UART. En estas situaciones, se suelen usan dos búferes circulares: uno para la entrada y otro para la salida.

Cada búfer de bytes circular está formado por un área de memoria de bytes (normalmente una matriz de UCHAR), un puntero de lectura y un puntero de escritura. Un búfer se considera vacío cuando el puntero de lectura y el puntero de escritura hacen referencia a la misma ubicación de memoria en el búfer. La inicialización del controlador establece los punteros de lectura y escritura del búfer en la dirección inicial del búfer.

### <a name="circular-buffer-input"></a>Entrada de búfer circular 
El búfer de entrada se usa para contener los caracteres que llegan antes de que la aplicación esté lista para recibirlos. Cuando se recibe un carácter de entrada (normalmente en una rutina de servicio de interrupción), el nuevo carácter se recupera del dispositivo de hardware y se coloca en el búfer de entrada en la ubicación a la que señala el puntero de escritura. A continuación, el puntero de escritura avanza a la siguiente posición en el búfer. Si la siguiente posición está más allá del final del búfer, el puntero de escritura se establece en el principio del búfer. La condición de cola llena se controla cancelando el avance del puntero de escritura si el nuevo puntero de escritura es el mismo que el puntero de lectura.

Las solicitudes de bytes de entrada de la aplicación al controlador examinan primero los punteros de lectura y escritura del búfer de entrada. Si ambos punteros son idénticos, significa que el búfer está vacío. De lo contrario, si el puntero de lectura no es el mismo, el byte al que apunta el puntero de lectura se copia desde el búfer de entrada y el puntero de lectura avanza a la siguiente ubicación de búfer. Si el nuevo puntero de lectura está más allá del final del búfer, se restablece al principio. En la figura 12 se muestra la lógica del búfer de entrada circular.

```C
UCHAR     tx_input_buffer[MAX_SIZE];
UCHAR     tx_input_write_ptr;
UCHAR     tx_input_read_ptr;

/* Initialization.  */
tx_input_write_ptr =  &tx_input_buffer[0];
tx_input_read_ptr =    &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr =  tx_input_write_ptr;
*tx_input_write_ptr++ =  alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr =  &tx_input_buffer[0];  /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr =  save_ptr;  /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
    alpha =  *tx_input_read_ptr++;
    if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
        tx_input_read_ptr =  &tx_input_buffer[0];
}
```
**FIGURA 12. Lógica del búfer de entrada circular**

> [!IMPORTANT]
> Para conseguir un funcionamiento confiable, puede ser necesario bloquear las interrupciones cuando se manipulan los punteros de lectura y escritura de los búferes circulares de entrada y salida.

### <a name="circular-output-buffer"></a>Búfer de salida circular 
El búfer de salida se usa para contener los caracteres que han llegado para su salida antes de que el dispositivo de hardware haya terminado de enviar el byte anterior. El procesamiento del búfer de salida es similar al procesamiento del búfer de entrada, excepto en que el procesamiento de la interrupción de transmisión completa manipula el puntero de lectura de salida, en tanto que la solicitud de salida de la aplicación emplea el puntero de escritura de salida. Por lo demás, el procesamiento del búfer de salida es el mismo. En la figura 13 se muestra la lógica del búfer de salida circular.

```C
UCHAR     tx_output_buffer[MAX_SIZE];
UCHAR     tx_output_write_ptr;
UCHAR     tx_output_read_ptr;

/* Initialization.  */
tx_output_write_ptr =  &tx_output_buffer[0];
tx_output_read_ptr =   &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
    *device_reg =  *tx_output_read_ptr++;
    if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
    tx_output_read_ptr =  &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr =  tx_output_write_ptr;
*tx_output_write_ptr++ =  alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr =  &tx_output_buffer[0];  /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr =  save_ptr;  /* Buffer full!  */
```
**FIGURA 13. Lógica del búfer de salida circular**

### <a name="buffer-io-management"></a>Administración de búferes de E/S 
Para mejorar el rendimiento de los microprocesadores insertados, muchos dispositivos periféricos transmiten y reciben datos con búferes suministrados por el software. En algunas implementaciones, se pueden usar varios búferes para transmitir o recibir paquetes de datos individuales. 

El tamaño y la ubicación de los búferes de E/S viene determinado por la aplicación o el software del controlador. Normalmente, los búferes tienen un tamaño fijo y se administran dentro de un grupo de bloques de memoria de ThreadX SMP. En la figura 14 se describe un búfer de E/S típico y un grupo de bloques de memoria de ThreadX SMP que administra su asignación.

```C
typedef struct TX_IO_BUFFER_STRUCT
{

      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
    struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR  tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
   "free_memory_ptr"points to an available memory area that
   is 64 KBytes in size. */

tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```
**FIGURA 14. Búfer de E/S**

### <a name="tx_io_buffer"></a>TX_IO_BUFFER 
La definición de tipo TX_IO_BUFFER consta de dos punteros. El puntero ***tx_next_packet** _ se usa para vincular varios paquetes de la lista de entrada o de salida. El puntero _ *_tx_next_buffer_** se usa para vincular los búferes que componen un paquete individual de datos del dispositivo. Ambos punteros se establecen en NULL cuando el búfer se asigna desde el grupo. Además, algunos dispositivos pueden requerir otro campo para indicar cuánta proporción del área de búfer contiene realmente datos.

### <a name="buffered-io-advantage"></a>Ventaja de la entrada/salida almacenada en búfer 
¿Cuáles son las ventajas de un esquema de E/S en búfer? La mayor ventaja es que los datos no se copian entre los registros del dispositivo y la memoria de la aplicación. En vez de esto, el controlador proporciona al dispositivo una serie de punteros de búfer. La E/S del dispositivo físico emplea directamente la memoria de búfer suministrada.

El uso del procesador para copiar paquetes de entrada o salida de información es extremadamente costoso y debe evitarse en cualquier situación de E/S de alto rendimiento.

Otra ventaja del enfoque de E/S almacenada en búfer es que las listas de entrada y salida no tienen condiciones de elemento completo. Todos los búferes disponibles pueden estar en cualquiera de las dos listas en un momento dado. Esto lo distingue de los búferes circulares de bytes simples presentados antes en el capítulo. Cada uno tenía un tamaño fijo que se determinaba en la compilación.

### <a name="buffered-driver-responsibilities"></a>Responsabilidades del controlador con almacenamiento en búfer 
Los controladores de dispositivo con almacenamiento en búfer solo se ocupan de administrar listas vinculadas de búferes de E/S. Se mantiene una lista de búferes de entrada para los paquetes que se reciben antes de que el software de la aplicación esté listo. También se mantiene una lista de búferes de salida para los paquetes que se envían más rápido de lo que el dispositivo de hardware puede gestionar. En la figura 15 se muestran listas vinculadas de entrada y salida simples de paquetes de datos y los búferes que componen cada paquete.

![Responsabilidades del controlador con almacenamiento en búfer](media/image11.png)

**FIGURA 15. Listas de entrada y salida**

Las aplicaciones interactúan con controladores con almacenamiento en búfer que tienen los mismos búferes de E/S. En la transmisión, el software de la aplicación proporciona al controlador uno o varios búferes para transmitir. Cuando el software de la aplicación solicita una entrada, el controlador devuelve los datos de entrada en búferes de E/S.

> [!IMPORTANT]
> En algunas aplicaciones, puede ser útil crear una interfaz de entrada al controlador que requiera que la aplicación intercambie un búfer libre por un búfer de entrada del controlador. Esto podría aliviar parte del procesamiento de la asignación de búferes dentro del controlador.

### <a name="interrupt-management"></a>Administración de interrupciones 
En algunas aplicaciones, la frecuencia de interrupción del dispositivo puede prohibir escribir la ISR en C o interactuar con ThreadX SMP en cada interrupción. Por ejemplo, si se tardan 25 μs en guardar y restaurar el contexto interrumpido, no sería aconsejable realizar un guardado de contexto completo con una frecuencia de interrupción de 50 μs. En tales casos, se usa una ISR de lenguaje de ensamblado pequeña para controlar la mayoría de las interrupciones del dispositivo. Esta ISR de carga baja solo interactuará con ThreadX SMP cuando sea necesario.

Se trata una cuestión similar en la explicación sobre la administración de interrupciones al final del capítulo 3.

> [!NOTE]
> Si se va a usar el bloqueo de interrupciones para proteger secciones críticas del código de controlador ante el código de la ISR del controlador, el código del controlador en el nivel de subproceso debe ejecutarse siempre en el mismo núcleo en el que se procesa la ISR. Si no, se deben usar primitivas internas de ThreadX SMP como TX_DISABLE y TX_RESTORE, que también tienen integrada la protección entre núcleos.

### <a name="thread-suspension"></a>Suspensión de subprocesos 
En el ejemplo de controlador simple presentado anteriormente en este capítulo, se suspende el autor de la llamada del servicio de entrada si un carácter no está disponible. En algunas aplicaciones, puede que esto no resulte viable.

Por ejemplo, si el subproceso responsable de procesar la entrada de un controlador también tiene otras tareas, probablemente no se podrá suspender solo la entrada del controlador. En su lugar, debe personalizarse el controlador para solicitar el procesamiento de forma similar a la manera en que se realizan otras solicitudes de procesamiento al subproceso.

En la mayoría de los casos, se coloca el búfer de entrada en una lista vinculada y se envía un mensaje de evento de entrada a la cola de entrada del subproceso.