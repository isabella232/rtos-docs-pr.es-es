---
title: 'Capítulo 3: Componentes funcionales de Azure RTOS ThreadX'
description: Este capítulo contiene una descripción del kernel de alto rendimiento de Azure RTOS ThreadX desde una perspectiva funcional.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 906ccb4fb69925f5244192f06521bf508bd15ced2076fb03031649fea638171c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789985"
---
# <a name="chapter-3---functional-components-of-azure-rtos-threadx"></a>Capítulo 3: Componentes funcionales de Azure RTOS ThreadX

Este capítulo contiene una descripción del kernel de alto rendimiento de Azure RTOS ThreadX desde una perspectiva funcional. Cada componente funcional se presenta de una forma fácil de entender.

## <a name="execution-overview"></a>Información general sobre la ejecución

En una aplicación de ThreadX hay cuatro tipos de ejecución de programa: inicialización, ejecución de subprocesos, rutinas de servicio de interrupción (ISR) y temporizadores de aplicación.

En la figura 2 se muestra cada tipo de ejecución de programa. En las secciones siguientes de este capítulo se ofrece información más detallada sobre cada uno de estos tipos.

### <a name="initialization"></a>Inicialización

Como su nombre indica, este es el primer tipo de ejecución de programa de una aplicación de ThreadX. La inicialización incluye toda la ejecución de programa entre el restablecimiento del procesador y el punto de entrada del *bucle de programación de subprocesos*.

### <a name="thread-execution"></a>Ejecución de subprocesos

Una vez que se ha completado la inicialización, ThreadX entra en su bucle de programación de subprocesos. El bucle de programación busca un subproceso de aplicación listo para ejecutarse. Cuando se encuentra un subproceso listo, ThreadX le transfiere el control. Cuando termina el subproceso (o hay otro de mayor prioridad listo), la ejecución se vuelve a transferir al bucle de programación de subprocesos a fin de encontrar el siguiente subproceso listo de mayor prioridad.

Este proceso continuo de ejecución y programación de subprocesos es el tipo más común de ejecución de programa en las aplicaciones de ThreadX.

### <a name="interrupt-service-routines-isr"></a>Rutinas de servicio de interrupción (ISR)

Las interrupciones son la piedra angular de los sistemas en tiempo real. Sin interrupciones, sería extremadamente difícil responder a los cambios en el mundo exterior de manera oportuna. Al detectar una interrupción, el procesador guarda información clave sobre la ejecución de programas actual (normalmente en la pila) y transfiere el control a un área de programas predefinida. Esta área de programas predefinida suele recibir el nombre de rutina de servicio de interrupción. En la mayoría de los casos, las interrupciones se producen durante la ejecución de subprocesos (o en el bucle de programación de subprocesos). Pero también se pueden producir dentro de una ISR en ejecución o un temporizador de aplicación.

![Tipos de ejecución de programa](./media/user-guide/types-program-execution.png)

**FIGURA 2. Tipos de ejecución de programa**

### <a name="application-timers"></a>Temporizadores de aplicación

Los temporizadores de aplicación son similares a las ISR, aunque la implementación de hardware (normalmente se usa una sola interrupción de hardware periódica) se oculta a la aplicación. Las aplicaciones emplean estos temporizadores para ejecutar tiempos de espera, servicios periódicos o de guardián. Al igual que las ISR, los temporizadores de aplicación suelen interrumpir la ejecución de subprocesos. Pero a diferencia de las ISR, los temporizadores de aplicación no se pueden interrumpir entre sí.

## <a name="memory-usage"></a>Uso de la memoria

ThreadX reside junto al programa de la aplicación. Por eso, el uso de memoria estática (o memoria fija) de ThreadX viene determinado por las herramientas de desarrollo, por ejemplo, el compilador, el enlazador y el localizador. El uso de memoria dinámica (o memoria en tiempo de ejecución) está bajo el control directo de la aplicación.

### <a name="static-memory-usage"></a>Uso de memoria estática

La mayoría de las herramientas de desarrollo dividen la imagen del programa de la aplicación en cinco áreas básicas: *instrucciones*, *constantes*, *datos inicializados*, *datos sin inicializar* y *pila del sistema*. En la figura 3 se muestra un ejemplo de estas áreas de memoria.

Es importante entender que se trata solo de un ejemplo. El diseño de memoria estática real es específico del procesador, las herramientas de desarrollo y el hardware subyacente.

El área de instrucciones contiene todas las instrucciones del procesador del programa. Normalmente es el área más grande y suele encontrarse en la ROM.

El área de constantes contiene varias constantes compiladas, incluidas las cadenas definidas o a las que se hace referencia en el programa. Además, esta área contiene la "copia inicial" del área de datos inicializados. Durante el proceso de inicialización del compilador de *uso de memoria*, esta parte del área de constantes se usa para configurar el área de datos inicializados en la RAM. El área de constantes suele seguir al área de instrucciones y encontrarse en la ROM.

Las áreas de datos inicializados y sin inicializar contienen todas las variables globales y estáticas. Estas áreas siempre se encuentran en la RAM.

La pila del sistema se suele configurar inmediatamente después de las áreas de datos inicializados y sin inicializar.

El compilador usa la pila del sistema durante la inicialización, luego la utiliza ThreadX también durante la inicialización y, posteriormente, durante el procesamiento de ISR.

![Ejemplo de área de memoria](./media/user-guide/memory-area-example.png)

**FIGURA 3. Ejemplo de área de memoria**

### <a name="dynamic-memory-usage"></a>Uso de memoria dinámica

Como se ha mencionado antes, el uso de memoria dinámica está bajo el control directo de la aplicación. Los bloques de control y las áreas de memoria asociados a pilas, colas y bloques de memoria se pueden colocar en cualquier ubicación del espacio de memoria del destino. Se trata de una característica importante, ya que facilita el uso de diferentes tipos de memoria física.

Por ejemplo, imagine que un entorno de hardware de destino tiene memoria rápida y memoria lenta. Si la aplicación necesita rendimiento adicional para un subproceso de alta prioridad, su bloque de control (TX_THREAD) y la pila se pueden colocar en el área de memoria rápida, lo que puede mejorar considerablemente el rendimiento.

## <a name="initialization"></a>Inicialización

Es importante entender el proceso de inicialización. Aquí se configura el entorno de hardware inicial. Además, aquí es donde se proporciona la personalidad inicial a la aplicación.

> [!NOTE]
> *ThreadX intentará usar (siempre que sea posible) el proceso de inicialización completo de la herramienta de desarrollo. Esto permite que en el futuro sea más fácil hacer la actualización a nuevas versiones de las herramientas de desarrollo.*

### <a name="system-reset-vector"></a>Vector de restablecimiento del sistema

Todos los microprocesadores tienen lógica de restablecimiento. Cuando se produce un restablecimiento (ya sea de hardware o software), la dirección del punto de entrada de la aplicación se recupera de una ubicación de memoria concreta. Una vez que se ha recuperado el punto de entrada, el procesador transfiere el control a esa ubicación. El punto de entrada de la aplicación se escribe con mucha frecuencia en el lenguaje de ensamblado nativo y normalmente lo suministran las herramientas de desarrollo (al menos en formato de plantilla). En algunos casos, se proporciona una versión especial del programa de entrada con ThreadX.

### <a name="development-tool-initialization"></a>Inicialización de la herramienta de desarrollo

Una vez que se completa la inicialización de bajo nivel, el control se transfiere a la inicialización de alto nivel de la herramienta de desarrollo. Normalmente, es el lugar donde se configuran las variables globales y estáticas de C. Recuerde que sus valores iniciales se recuperan del área de constantes. El procesamiento de inicialización exacto es específico de la herramienta de desarrollo.

### <a name="main-function"></a>main (función)

Una vez que se completa la inicialización de la herramienta de desarrollo, el control se transfiere a la función *main* proporcionada por el usuario. En este punto, la aplicación controla lo que ocurre a continuación. Para la mayoría de las aplicaciones, la función "main" simplemente llama a *tx_kernel_enter*, que es la entrada a ThreadX. Pero las aplicaciones pueden realizar el procesamiento preliminar (normalmente para la inicialización de hardware) antes de entrar en ThreadX.

> [!IMPORTANT]
> *La llamada a tx_kernel_enter no devuelve valores, por lo no debe colocar ningún procesamiento después.*

### <a name="tx_kernel_enter"></a>tx_kernel_enter

La función de entrada coordina la inicialización de varias estructuras de datos internas de ThreadX y, después, llama a la función de definición ***tx_application_define*** de la aplicación.

Cuando ***tx_application_define*** devuelve un valor, el control se transfiere al bucle de programación de subprocesos. Esto marca el final de la inicialización.

### <a name="application-definition-function"></a>Función de definición de aplicación

La función ***tx_application_define*** define todos los subprocesos, las colas, los semáforos, las exclusiones mutuas, las marcas de eventos, los grupos de memoria y los temporizadores iniciales de la aplicación. También es posible crear y eliminar recursos del sistema desde subprocesos durante el funcionamiento normal de la aplicación. Pero aquí se definen todos los recursos iniciales de la aplicación.

La función ***tx_application_define** _ tiene un único parámetro de entrada que merece la pena mencionar. La dirección RAM _first-available* es el único parámetro de entrada de esta función. Normalmente se usa como punto de partida para las asignaciones de memoria iniciales en tiempo de ejecución de pilas de subprocesos, colas y grupos de memoria.

> [!NOTE]
> *Una vez que se ha completado la inicialización, solo un subproceso en ejecución puede crear y eliminar recursos del sistema, incluidos otros subprocesos. Por tanto, durante la inicialización se debe crear al menos un subproceso.*

### <a name="interrupts"></a>Interrupciones

Las interrupciones se dejan deshabilitadas durante todo el proceso de inicialización. Si la aplicación habilita alguna interrupción, se puede producir un comportamiento impredecible. En la figura 4 se muestra el proceso de inicialización completo, desde el restablecimiento del sistema hasta la inicialización específica de la aplicación.

## <a name="thread-execution"></a>Ejecución de subprocesos

La programación y ejecución de subprocesos de aplicación es la actividad más importante de ThreadX. Un subproceso se define normalmente como un segmento de programa semiindependiente con un propósito dedicado. El procesamiento combinado de todos los subprocesos crea una aplicación.

Los subprocesos se crean de forma dinámica mediante una llamada a ***tx_thread_create** _ durante la inicialización o durante la ejecución del subproceso. Los subprocesos se crean en un estado _listo* o *suspendido*.

![Proceso de inicialización](./media/user-guide/initialization-process.png)

**FIGURA 4. Proceso de inicialización**

### <a name="thread-execution-states"></a>Estados de ejecución de subprocesos

Comprender los distintos estados de procesamiento de los subprocesos es un factor clave para entender todo el entorno multiproceso. En ThreadX hay cinco estados de subproceso distintos: *listo*, *suspendido*, *en ejecución*, *finalizado* y *completado*. En la figura 5 se muestra el diagrama de transición de estado de subprocesos de ThreadX.

![Transición de estado de subprocesos](./media/user-guide/thread-state-transition.png)

**FIGURA 5. Transición de estado de subprocesos**

Un subproceso está en un estado *listo* cuando está listo para su ejecución. Un subproceso listo no se ejecuta hasta que es el subproceso de prioridad más alta en estado listo. Cuando esto sucede, ThreadX ejecuta el subproceso, que cambia su estado a *en ejecución*.

Si un subproceso de prioridad más alta está listo, el subproceso en ejecución vuelve a un estado *listo*. Después se ejecuta el subproceso de alta prioridad recién preparado, que cambia su estado lógico a *en ejecución*. Esta transición entre los estados *listo* y *en ejecución* se produce cada vez que tiene lugar el adelantamiento de subprocesos.

En cualquier momento dado solo hay un subproceso en estado *en ejecución*. Esto se debe a que un subproceso en el estado *en ejecución* tiene el control del procesador subyacente.

Los subprocesos en estado *suspendido* no son aptos para ejecutarse. Entre los motivos para estar en estado *suspendido* se incluyen la suspensión por tiempo, mensajes de cola, semáforos, exclusiones mutuas, marcas de eventos, memoria y suspensión básica de subprocesos. Una vez que se elimina la causa de la suspensión, el subproceso se vuelve a colocar en estado *listo*.

Un subproceso en estado *completado* es el que ha completado su procesamiento y se ha devuelto desde su función de entrada. La función de entrada se especifica durante la creación del subproceso. No se puede volver a ejecutar un subproceso en estado *completado*.

Un subproceso está en estado *terminado* porque él mismo u otro subproceso ha llamado al servicio *tx_thread_terminate*. Un subproceso en un estado *completado* no se puede volver a ejecutar.

> [!IMPORTANT]
> *Si se quiere volver a iniciar un subproceso completado o finalizado, la aplicación debe eliminar primero el subproceso. Después, se podrá volver a crear y reiniciar.*

### <a name="thread-entryexit-notification"></a>Entrada de subprocesos/Notificación de salida

Es posible que para algunas aplicaciones sea una ventaja recibir notificaciones cuando se entra por primera vez en un subproceso concreto, cuando se completa o cuando se finaliza. ThreadX proporciona esta función por medio del servicio ***tx_thread_entry_exit_notify***. Este servicio registra una función de notificación de aplicación para un subproceso concreto, al que llama ThreadX cada vez que el subproceso empieza a ejecutarse, se completa o finaliza. Después de invocarse, la función de notificación de la aplicación puede realizar el procesamiento específico de la aplicación. Normalmente, esto implica informar a otro subproceso de aplicación del evento por medio de una primitiva de sincronización de ThreadX.

### <a name="thread-priorities"></a>Prioridades de subprocesos

Como se ha mencionado antes, un subproceso es un segmento de programa semiindependiente con un fin concreto. Pero no todos los subprocesos se crean de la misma forma. El fin concreto de algunos subprocesos es mucho más importante que el de otros. Este tipo heterogéneo de importancia del subproceso es un sello de las aplicaciones en tiempo real insertadas.

ThreadX determina la importancia de un subproceso al crearlo asignándole un valor numérico que representa su *prioridad*. El número máximo de prioridades de ThreadX se puede configurar de 32 a 1024 en incrementos de 32. El número máximo real de prioridades viene determinado por la constante **TX_MAX_PRIORITIES** durante la compilación de la biblioteca de ThreadX. Tener un número mayor de prioridades no aumenta significativamente la sobrecarga de procesamiento. Pero para cada grupo de 32 niveles de prioridad se necesitan 128 bytes de RAM adicionales a fin de administrarlos. Por ejemplo, los niveles de prioridad 32 necesitan 128 bytes de RAM, los de prioridad 64 necesitan 256 bytes de RAM y los de prioridad 96, 384 bytes de RAM.

De forma predeterminada, ThreadX tiene 32 niveles de prioridad, que van desde 0 hasta 31. Los valores numéricamente más pequeños implican una mayor prioridad. Por tanto, la prioridad 0 representa la prioridad más alta, mientras que la prioridad (**TX_MAX_PRIORITIES**-1) representa la más baja.

Varios subprocesos pueden tener la misma prioridad, que se basa en la programación cooperativa o la segmentación temporal. Además, las prioridades de los subprocesos se pueden cambiar durante el tiempo de ejecución.

### <a name="thread-scheduling"></a>Programación de subprocesos

ThreadX programa los subprocesos según su prioridad. Primero se ejecuta el subproceso listo con la prioridad más alta. Si hay varios subprocesos listos con la misma prioridad, se ejecutan de forma FIFO (*el primero en entrar es el primero en salir* ).

### <a name="round-robin-scheduling"></a>Programación round robin

ThreadX admite la programación *round robin* de varios subprocesos que tienen la misma prioridad. Esto se logra mediante llamadas cooperativas a ***tx_thread_relinquish** _. Este servicio proporciona a todos los demás subprocesos listos de la misma prioridad una oportunidad de ejecutarse antes de que el autor de la llamada a _ *_tx_thread_relinquish_** se vuelva a ejecutar.

### <a name="time-slicing"></a>Segmentación temporal

La *segmentación temporal* es otra forma de programación round robin. Un segmento temporal especifica el número máximo de tics de temporizador (interrupciones del temporizador) que un subproceso puede ejecutar sin renunciar al procesador. En ThreadX, la segmentación temporal está disponible en cada subproceso. El segmento temporal del subproceso se asigna durante la creación y se puede modificar en tiempo de ejecución. Cuando expira un segmento temporal, todos los demás subprocesos listos del mismo nivel de prioridad tienen la oportunidad de ejecutarse antes de que se vuelva a ejecutar el subproceso con segmentación temporal.

Se asigna un nuevo segmento temporal de subproceso a un subproceso después de que se suspenda, se interrumpa, realice una llamada de servicio de ThreadX que cause el adelantamiento o que se segmente temporalmente.

Cuando se adelante un subproceso con segmentación temporal, se reanudará antes que otros subprocesos listos de la misma prioridad para el resto de su segmento temporal.

> [!NOTE]
> *El uso de segmentos temporales provoca una ligera sobrecarga del sistema. Como la segmentación temporal solo es útil cuando varios subprocesos comparten la misma prioridad, no se debe asignar un segmento temporal a los subprocesos que tienen una prioridad única.*

### <a name="preemption"></a>Adelantamiento

El adelantamiento es el proceso de interrumpir temporalmente un subproceso en ejecución en favor de uno con mayor prioridad. Este proceso no es visible para el subproceso en ejecución. Cuando finaliza el subproceso de mayor prioridad, el control se transfiere de nuevo a la ubicación exacta donde se produjo el adelantamiento. Se trata de una característica muy importante de los sistemas en tiempo real porque facilita la respuesta rápida a eventos de aplicación importantes. Aunque sea una característica muy importante, el adelantamiento también puede ser una fuente de diversos problemas, como colapsos, sobrecargas excesivas e inversión de prioridades.

### <a name="preemption-thresholdtrade"></a>Umbral de adelantamiento&trade;

Para aliviar algunos de los problemas inherentes del adelantamiento, ThreadX proporciona una característica única y avanzada denominada *umbral de adelantamiento*.

Un umbral de adelantamiento permite que un subproceso especifique un *límite* de prioridad para deshabilitar el adelantamiento. Los subprocesos con prioridades más altas que el techo pueden seguir adelantándose, mientras que aquellos con prioridades inferiores no pueden hacerlo.

Por ejemplo, imagine que un subproceso de prioridad 20 solo interactúa con un grupo de subprocesos con prioridades entre 15 y 20. Durante sus secciones críticas, el subproceso de prioridad 20 puede establecer su umbral de adelantamiento en 15, con lo que se evita el adelantamiento de todos los subprocesos con los que interactúa. Esto sigue permitiendo que los subprocesos realmente importantes (con prioridades entre 0 y 14) adelanten a este durante su procesamiento de secciones críticas, lo que da lugar a un procesamiento mucho más dinámico.

Por supuesto, sigue siendo posible que un subproceso deshabilite todo adelantamiento si establece su umbral de adelantamiento en 0. Además, el umbral de adelantamiento se puede cambiar durante el tiempo de ejecución.

> [!NOTE]
> *El uso del umbral de adelantamiento deshabilita la segmentación temporal para el subproceso especificado.*

### <a name="priority-inheritance"></a>Herencia de prioridades

ThreadX también admite la herencia de prioridades opcional dentro de sus servicios de exclusión mutua descritos más adelante en este capítulo. La herencia de prioridades permite que un subproceso de prioridad inferior asuma temporalmente la de un subproceso de prioridad alta que espera una exclusión mutua propiedad del subproceso de prioridad inferior. Esta capacidad ayuda a la aplicación a evitar la inversión de prioridades no determinista al eliminar el adelantamiento de prioridades de subprocesos intermedias. Por supuesto, se puede usar el *umbral de adelantamiento* para lograr un resultado similar.

### <a name="thread-creation"></a>Creación de subprocesos

Los subprocesos de aplicación se crean durante la inicialización o durante la ejecución de otros subprocesos de aplicación. No existe límite en cuanto al número de subprocesos que puede crear una aplicación.

### <a name="thread-control-block-tx_thread"></a>Bloque de control de subprocesos TX_THREAD

Las características de cada subproceso se encuentran en su bloque de control. Esta estructura se define en el archivo ***tx_api.h***.

Los bloques de control de subproceso se pueden ubicar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global definiéndolo fuera del ámbito de cualquier función.

Para colocar el bloque de control en otras áreas se necesita más cuidado, como sucede con la memoria asignada de forma dinámica. Si se asigna un bloque de control dentro de una función de C, la memoria asociada al mismo formará parte de la pila del subproceso que realiza la llamada. En general, evite usar el almacenamiento local para los bloques de control, ya que, una vez devuelta la función, se libera todo su espacio de la pila de variables local, independientemente de si otro subproceso la usa para un bloque de control.

En la mayoría de los casos, la aplicación desconoce el contenido del bloque de control del subproceso. Pero en algunas situaciones, especialmente durante la depuración, resulta útil examinar determinados miembros. A continuación se muestran algunos de los miembros de bloque de control más útiles.

**tx_thread_run_count** contiene un contador del número de veces que se ha programado el subproceso. Un contador creciente indica que el subproceso se está programando y ejecutando.

**tx_thread_state** contiene el estado del subproceso asociado. A continuación se enumeran los estados de subproceso posibles.

|  Estado de subproceso   | Value |
| --------------- | ------ |
| TX_READY       | (0x00) |
| TX_COMPLETED   | (0x01) |
| TX_TERMINATED  | (0x02) |
| TX_SUSPENDED   | (0x03) |
| TX_SLEEP       | (0x04) |
| TX_QUEUE_SUSP | (0x05) |
| TX_SEMAPHORE_SUSP | (0x06) |
| TX_EVENT_FLAG   | (0x07) |
| TX_BLOCK_MEMORY | (0x08) |
| TX_BYTE_MEMORY  | (0x09) |
| TX_MUTEX_SUSP   | (0x0D) |

> [!NOTE]
> *Evidentemente, hay otros muchos campos interesantes en el bloque de control de subprocesos, entre los que se incluyen el puntero de pila, el valor del segmento temporal, las prioridades, etc. Los usuarios pueden revisar los miembros del bloque de control, pero las modificaciones están totalmente prohibidas.*

> [!IMPORTANT]
> *No hay ninguna equivalencia con el estado "en ejecución" mencionado antes en esta sección. No es necesario porque, en un momento dado, solo hay un subproceso en ejecución. El estado de un subproceso en ejecución también es* **TX_READY**.

### <a name="currently-executing-thread"></a>Subproceso en ejecución

Como se ha mencionado antes, en un momento dado solo hay un subproceso en ejecución. Hay varias maneras de identificar el subproceso en ejecución, en función del subproceso que realiza la solicitud.
Un segmento de programa puede obtener la dirección del bloque de control del subproceso en ejecución mediante una llamada a ***tx_thread_identify***. Esto resulta útil en partes compartidas del código de la aplicación que se ejecutan desde varios subprocesos.

En las sesiones de depuración, los usuarios pueden examinar el puntero de ThreadX interno ***_tx_thread_current_ptr***. Contiene la dirección del bloque de control del subproceso actualmente en ejecución. Si este puntero es NULL, no hay ningún subproceso de aplicación en ejecución; es decir, ThreadX espera en su bucle de programación a que un subproceso esté listo.

### <a name="thread-stack-area"></a>Área de pila de subprocesos

Cada subproceso debe tener su propia pila para guardar el contexto de su última ejecución y uso del compilador. La mayoría de los compiladores de C usan la pila para realizar llamadas de función y para asignar variables locales de forma temporal. En la figura 6 se muestra la pila de un subproceso típico.

La ubicación de la pila de un subproceso en memoria depende de la aplicación. El área de pila se especifica durante la creación del subproceso y se puede ubicar en cualquier parte del espacio de direcciones del destino. Se trata de una característica importante porque permite a las aplicaciones mejorar el rendimiento de los subprocesos importantes colocando su pila en memoria RAM de alta velocidad.

**Área de memoria de la pila** (ejemplo)

![Pila de subprocesos típica](./media/user-guide/typical-thread-stack.png)

**FIGURA 6. Pila de subprocesos típica**

El tamaño de una pila es una de las preguntas más frecuentes sobre los subprocesos. El área de pila de un subproceso debe ser lo suficientemente grande como para acomodar el anidamiento de llamadas de función en el peor de los casos, la asignación de variables locales y el guardado de su último contexto de ejecución.

ThreadX define el tamaño mínimo de la pila, **TX_MINIMUM_STACK**. Una pila de este tamaño permite guardar el contexto de un subproceso y una cantidad mínima de llamadas de función y asignación de variables locales.

Pero para la mayoría de los subprocesos, el tamaño mínimo de la pila es demasiado pequeño y el usuario debe determinar el requisito de tamaño en el peor de los casos examinando el anidamiento de las llamadas de función y la asignación de variables locales. Por supuesto, siempre es mejor empezar con un área de pila más grande.

Después de depurar la aplicación, se pueden ajustar los tamaños de la pila de subprocesos si la memoria es escasa. Un buen truco es preestablecer todas las áreas de pila con un patrón de datos fácilmente identificable, como (0xEFEF), antes de crear los subprocesos. Una vez que la aplicación se ha probado en profundidad, se pueden examinar las áreas de pila para ver la cantidad que se ha usado realmente; para ello, se busca el área de la pila en la que el patrón de datos sigue intacto. En la figura 7 se muestra un valor de pila preestablecido en 0xEFEF después de la ejecución exhaustiva de subprocesos.

**Área de memoria de la pila** (otro ejemplo)

![Valor de la pila preestablecido en 0xEFEF*](./media/user-guide/stack-preset.png)

**FIGURA 7. Valor de la pila preestablecido en 0xEFEF**

> [!IMPORTANT]
> *De forma predeterminada, ThreadX inicializa todos los bytes de cada pila de subprocesos con un valor de 0xEF.*

### <a name="memory-pitfalls"></a>Errores de memoria

Los requisitos de la pila para los subprocesos pueden ser considerables. Por tanto, es importante diseñar la aplicación para que tenga un número razonable de subprocesos. Además, se debe tener cuidado para evitar un uso excesivo de la pila dentro de los subprocesos. Se deben evitar los algoritmos recursivos y las estructuras de datos locales de gran tamaño.

En la mayoría de los casos, una pila desbordada hace que la ejecución de los subprocesos afecte a la memoria adyacente (normalmente antes) de su área de pila. Los resultados son imprevisibles, pero la mayoría de las veces provocan un cambio no natural en el contador de programas. Esto se suele denominar "analizar los pormenores". Por supuesto, la única manera de evitarlo es asegurarse de que todas las pilas de subproceso son lo suficientemente grandes.

### <a name="optional-run-time-stack-checking"></a>Comprobación de pila en tiempo de ejecución opcional

ThreadX proporciona la capacidad de comprobar en tiempo de ejecución la existencia de daños en la pila de cada subproceso. De forma predeterminada, ThreadX rellena cada byte de las pilas de subproceso con un patrón de datos 0xEF durante la creación. Si la aplicación compila la biblioteca de ThreadX con **TX_ENABLE_STACK_CHECKING** definido, ThreadX examinará la pila de cada subproceso en busca de daños mientras se suspende o se reanuda. Si se detectan daños en la pila, ThreadX llamará a la rutina de control de errores de pila de la aplicación como se especifica en la llamada a **_tx_thread_stack_error_notify_ *_. De lo contrario, si no se ha especificado ningún controlador de errores de pila, ThreadX llamará a la rutina interna _* _ _tx_thread_stack_error_handler_**.

### <a name="reentrancy"></a>Reentrada

Uno de los atractivos reales de multithreading es que se puede llamar a la misma función de C desde varios subprocesos. Esto proporciona una gran eficacia y también ayuda a reducir el espacio de código. Pero es necesario que las funciones de C a las que se llama desde varios subprocesos sean *reentrantes*.

Básicamente, una función reentrante almacena en la pila actual la dirección de devolución del autor de la llamada y no se basa en las variables de C globales o estáticas que ha configurado antes. La mayoría de los compiladores colocan la dirección de devolución en la pila. Por tanto, los desarrolladores de aplicaciones solo deben preocuparse por el uso de las variables *globales* y *estáticas*.

Un ejemplo de una función no reentrante es la función de token de cadena ***strtok*** de la biblioteca estándar de C. Esta función "recuerda" el puntero de cadena anterior en las llamadas siguientes. Y lo hace con un puntero de cadena estático. Si se llama a esta función desde varios subprocesos, lo más probable es que devuelva un puntero no válido.

### <a name="thread-priority-pitfalls"></a>Problemas de prioridad de subprocesos

La selección de la prioridad de los subprocesos es uno de los aspectos más importantes de multithreading. En ocasiones, es muy tentador asignar prioridades en función de una noción percibida de la importancia del subproceso, en lugar de determinar lo que es exactamente necesario durante el tiempo de ejecución. El uso incorrecto de las prioridades de subproceso puede colapsar a otros subprocesos, crear la inversión de prioridades, reducir el ancho de banda de procesamiento y dificultar la comprensión del comportamiento en tiempo de ejecución de la aplicación.

Como se ha mencionado antes, ThreadX proporciona un algoritmo de programación de adelantamiento basado en la prioridad. Los subprocesos de menor prioridad no se ejecutan hasta que no hay subprocesos de prioridad más alta listos para ejecutarse. Si siempre hay un subproceso de prioridad más alta listo, los subprocesos de prioridad baja nunca se ejecutan. Esta condición se denomina *colapso de subprocesos*.

La mayoría de los problemas de colapso de subprocesos se detectan pronto en la depuración y se pueden resolver asegurándose de que los subprocesos de prioridad más alta no se ejecutan de forma continuada. Como alternativa, se puede agregar lógica a la aplicación que genere gradualmente la prioridad de los subprocesos colapsados hasta que tengan la oportunidad de ejecutarse.

Otro problema asociado a las prioridades de los subprocesos es la *inversión de prioridades*. La inversión de prioridades tiene lugar cuando se suspende un subproceso de prioridad superior porque otro de prioridad baja tiene un recurso necesario. Evidentemente, en algunos casos es necesario que dos subprocesos de prioridad diferente compartan un recurso común. Si estos subprocesos son los únicos activos, el tiempo de inversión de prioridades está limitado por el tiempo que el subproceso de prioridad baja mantiene el recurso. Esta condición es determinista y bastante normal. Pero si durante esta condición de inversión de prioridades se activan subprocesos de prioridad intermedia, el tiempo de inversión de prioridades deja de ser determinista y podría provocar un error en la aplicación.

Existen principalmente tres métodos distintos para evitar la inversión de prioridades no determinista en ThreadX. En primer lugar, las selecciones de prioridad de la aplicación y el comportamiento en tiempo de ejecución se pueden diseñar de forma que se impida el problema de inversión de prioridades. En segundo lugar, los subprocesos de menor prioridad pueden usar el *umbral de adelantamiento* para bloquear el adelantamiento de los subprocesos intermedios mientras comparten recursos con subprocesos de mayor prioridad. Por último, los subprocesos que usan objetos de exclusión mutua de ThreadX para proteger los recursos del sistema pueden usar la *herencia de prioridades* de exclusión mutua opcional para eliminar la inversión de prioridades no determinista.

### <a name="priority-overhead"></a>Sobrecarga de prioridades

Una de las formas más infravaloradas para disminuir la sobrecarga en multithreading es reducir el número de cambios de contexto. Como se ha mencionado antes, un cambio de contexto se produce cuando se favorece la ejecución de un subproceso de prioridad más alta sobre la del subproceso en ejecución. Merece la pena mencionar que los subprocesos de mayor prioridad pueden pasar a estar listos como resultado de eventos externos (por ejemplo, interrupciones) y de llamadas a servicios realizadas por el subproceso en ejecución.

Para ilustrar los efectos que tienen las prioridades de los subprocesos en la sobrecarga de cambios de contexto, imagine un entorno de tres subprocesos: *subproceso_1*, *subproceso_2* y *subproceso_3*. Imagine además que todos los subprocesos están en estado de suspensión en espera de un mensaje. Cuando subproceso_1 recibe un mensaje, lo reenvía inmediatamente a subproceso_2. Después, subproceso_2 reenvía el mensaje a subproceso_3. Subproceso_3 simplemente descarta el mensaje. Una vez que cada subproceso procesa su mensaje, retrocede y espera otro mensaje.

El procesamiento necesario para ejecutar estos tres subprocesos varía considerablemente en función de sus prioridades. Si todos los subprocesos tienen la misma prioridad, solo se produce un cambio de contexto antes de la ejecución de cada uno. El cambio de contexto se produce cuando cada subproceso se suspende en una cola de mensajes vacía.

Pero si subproceso_2 tiene mayor prioridad que subproceso_1, y subproceso_3 tiene mayor prioridad que subproceso_2, se duplica el número de cambios de contexto. Esto se debe a que se produce otro cambio de contexto dentro del servicio *tx_queue_send* cuando este detecta que un subproceso de prioridad más alta ya está listo.

El mecanismo de umbral de adelantamiento de ThreadX puede evitar estos modificadores de contexto adicionales y seguir permitiendo las selecciones de prioridad mencionadas anteriormente. Se trata de una característica importante porque permite varias prioridades de subproceso durante la programación, al tiempo que elimina algunos de los cambios de contexto no deseados entre ellos durante la ejecución de los subprocesos.

### <a name="run-time-thread-performance-information"></a>Información sobre el rendimiento de subprocesos en tiempo de ejecución

ThreadX proporciona información opcional sobre el rendimiento de los subprocesos en tiempo de ejecución. Si la biblioteca y la aplicación de ThreadX se compilan con **TX_THREAD_ENABLE_PERFORMANCE_INFO** definido, ThreadX acumula la información siguiente.

Número total del sistema general:

  - reanudaciones de subprocesos

  - suspensiones de subprocesos

  - adelantamientos de llamadas a servicios

  - adelantamientos de interrupciones

  - inversiones de prioridades

  - segmentos temporales

  - renuncias

  - tiempos de espera de subprocesos

  - anulaciones de suspensiones

  - devoluciones de sistema inactivo

  - devoluciones de sistema no inactivo

Número total en cada subproceso:

  - reanudaciones

  - suspensiones

  - adelantamientos de llamadas a servicios

  - adelantamientos de interrupciones

  - inversiones de prioridades

  - segmentos temporales

  - renuncias de subprocesos

  - tiempos de espera de subprocesos

  - anulaciones de suspensión

Esta información está disponible en tiempo de ejecución mediante los servicios ***tx_thread_performance_info_get** _ y _*_tx_thread_performance_system_info_get_**. La información de rendimiento de los subprocesos resulta útil para determinar si la aplicación se comporta de manera correcta. También es útil para optimizar la aplicación. Por ejemplo, es posible que un número relativamente alto de adelantos de llamada de servicio sugiera que la prioridad o el umbral de adelantamiento del subproceso son demasiado bajos. Además, un número relativamente bajo de devoluciones del sistema inactivas podría sugerir que los subprocesos de menor prioridad no se suspenden lo suficiente.

### <a name="debugging-pitfalls"></a>Problemas de depuración

La depuración de aplicaciones multiproceso es algo más difícil, ya que el mismo código de programa se puede ejecutar desde varios subprocesos. En esos casos, es posible que no sea suficiente con un punto de interrupción. El depurador también debe ver el puntero del subproceso actual **_tx_thread_current_ptr** con un punto de interrupción condicional para comprobar si el subproceso que realiza la llamada es el que se va a depurar.

Gran parte de esta operación se controla en los paquetes de soporte de multithreading que ofrecen distintos proveedores de herramientas de desarrollo. Debido a su diseño sencillo, la integración de ThreadX con diferentes herramientas de desarrollo es relativamente sencilla.

El tamaño de la pila es siempre un tema de depuración importante en el multithreading. Siempre que se observa un comportamiento inexplicable, una buena solución inicial suele consistir en aumentar los tamaños de pila de todos los subprocesos, especialmente el del último que se va a ejecutar.

> [!TIP]
> *También es aconsejable crear la biblioteca de ThreadX con **TX_ENABLE_STACK_CHECKING** definido. Esto ayudará a aislar los problemas de daños en la pila tan pronto como sea posible en el procesamiento.*

## <a name="message-queues"></a>Colas de mensajes

Las colas de mensajes son el medio principal de la comunicación entre subprocesos en ThreadX. En una cola de mensajes puede haber uno o varios mensajes. Una cola de mensajes que contiene un solo mensaje normalmente se denomina *buzón*.

Los mensajes se copian en una cola por medio de ***tx_queue_send** _ y desde una cola con _*_tx_queue_receive_**. La única excepción es cuando se suspende un subproceso mientras se espera un mensaje en una cola vacía. En este caso, el siguiente mensaje que se envía a la cola se coloca directamente en el área de destino del subproceso.

Cada cola de mensajes es un recurso público. ThreadX no aplica restricciones al modo de usar las colas de mensajes.

### <a name="creating-message-queues"></a>Creación de colas de mensajes

Las colas de mensajes se crean durante la inicialización o durante el tiempo de ejecución por medio de subprocesos de aplicación. No hay ningún límite en cuanto al número de colas de mensajes de una aplicación.

### <a name="message-size"></a>Tamaño de los mensajes

Cada cola de mensajes admite una serie de mensajes de tamaño fijo. Los tamaños de mensaje disponibles son de 1 a 16 palabras de 32 bits. El tamaño del mensaje se especifica cuando se crea la cola. Los mensajes de aplicación de más de 16 palabras se deben pasar mediante un puntero. Esto se logra mediante la creación de una cola con un tamaño de mensaje de 1 palabra (suficiente para contener un puntero) y, después, el envío y la recepción de punteros de mensaje en lugar del mensaje completo.

### <a name="message-queue-capacity"></a>Capacidad de la cola de mensajes

El número de mensajes que puede contener una cola es una función de su tamaño de mensaje y el tamaño del área de memoria suministrada durante la creación. Para calcular la capacidad total de mensajes de la cola, se divide el número de bytes de cada mensaje entre el número total de bytes del área de memoria proporcionada.

Por ejemplo, si se crea una cola de mensajes que admite un tamaño de mensaje de una palabra de 32 bits (4 bytes) con un área de memoria de 100 bytes, su capacidad es de 25 mensajes.

### <a name="queue-memory-area"></a>Área de memoria de cola

Como se ha mencionado anteriormente, el área de memoria para almacenar en búfer los mensajes se especifica durante la creación de la cola. Como sucede con otras áreas de memoria de ThreadX, se puede ubicar en cualquier parte del espacio de direcciones del destino.

Se trata de una característica importante porque ofrece a la aplicación una gran flexibilidad. Por ejemplo, una aplicación puede colocar el área de memoria de una cola importante en la memoria RAM de alta velocidad para mejorar el rendimiento.

### <a name="thread-suspension"></a>Suspensión de subprocesos

Los subprocesos de aplicación se pueden suspender mientras se intenta enviar o recibir un mensaje de una cola. Normalmente, la suspensión de subprocesos implica esperar un mensaje de una cola vacía. Pero también es posible que un subproceso se suspenda al intentar enviar un mensaje a una cola completa.

Una vez que se resuelve la condición de la suspensión, el servicio solicitado se completa y se reanuda el subproceso en espera. Si se suspenden varios subprocesos en la misma cola, se reanudan en el orden en el que se suspendieron (FIFO).

Pero la reanudación por prioridad también es posible si la aplicación llama a ***tx_queue_prioritize*** antes que al servicio de cola que anula la suspensión de subprocesos. El servicio de clasificación por orden de prioridad de la cola coloca el subproceso de mayor prioridad al principio de la lista de suspensión y deja a todos los demás subprocesos suspendidos en el mismo orden FIFO.

También hay tiempos de espera disponibles para todas las suspensiones de cola. Básicamente, un tiempo de espera especifica el número máximo de tics de temporizador que el subproceso permanece suspendido. Si se agota el tiempo de espera, el subproceso se reanuda y el servicio devuelve el código de error adecuado.

### <a name="queue-send-notification"></a>Notificación de envío a cola

Es posible que algunas aplicaciones se beneficien de recibir una notificación cada vez que un mensaje se coloca en una cola. ThreadX proporciona esta función por medio del servicio ***tx_queue_send_notify***. Este servicio registra la función de notificación de aplicación proporcionada con la cola especificada. Después, ThreadX invocará esta función de notificación de aplicación cada vez que se envíe un mensaje a la cola. El procesamiento exacto dentro de la función de notificación de aplicación viene determinado por la aplicación; pero normalmente consiste en reanudar el subproceso adecuado para procesar el nuevo mensaje.

### <a name="queue-event-chainingtrade"></a>Encadenamiento de eventos de cola&trade;

Las funciones de notificación de ThreadX se pueden usar para encadenar varios eventos de sincronización. Esto suele ser útil cuando un único subproceso debe procesar varios eventos de sincronización.

Por ejemplo, imagine que un único subproceso es responsable de procesar los mensajes de cinco colas diferentes y que también se debe suspender cuando no haya mensajes disponibles. Esto se consigue fácilmente mediante el registro de una función de notificación de aplicación para cada cola y la adición de un semáforo de recuento adicional. En concreto, la función de notificación de aplicación ejecuta *tx_semaphore_put* cada vez que se la llama (el recuento del semáforo representa el número total de mensajes de las cinco colas). El subproceso de procesamiento se suspende en este semáforo por medio del servicio *tx_semaphore_get*. Cuando el semáforo está disponible (en este caso, cuando hay un mensaje disponible), se reanuda el subproceso de procesamiento. Después, solicita un mensaje a cada cola, procesa el mensaje encontrado y vuelve a ejecutar ***tx_semaphore_get*** para esperar al siguiente mensaje. La realización de esta tarea sin el encadenamiento de eventos es bastante difícil, y es probable que se necesiten más subprocesos o código de aplicación adicional.

En general, el *encadenamiento de eventos* genera menos subprocesos, menos sobrecarga y menos requisitos de RAM. También proporciona un mecanismo muy flexible para controlar los requisitos de sincronización de sistemas más complejos.

### <a name="run-time-queue-performance-information"></a>Información de rendimiento de colas en tiempo de ejecución
ThreadX proporciona información opcional sobre el rendimiento de las colas en tiempo de ejecución. Si la biblioteca y la aplicación de ThreadX se compilan con ***TX_QUEUE_ENABLE_PERFORMANCE_INFO*** definido, ThreadX acumula la información siguiente.

Número total del sistema general:

  - mensajes enviados

  - mensajes recibidos

  - suspensiones de cola vacía

  - suspensiones llenas de cola

  - devoluciones de errores completos de cola (suspensión sin especificar)

  - tiempos de espera de cola

Número total en cada cola:

  - mensajes enviados

  - mensajes recibidos

  - suspensiones de cola vacía

  - suspensiones llenas de cola

  - devoluciones de errores completos de cola (suspensión sin especificar)

  - tiempos de espera de cola

Esta información está disponible en tiempo de ejecución por medio de los servicios ***tx_queue_performance_info_get** _ y _*_tx_queue_performance_system_info_get_**. La información de rendimiento de las colas resulta útil para determinar si la aplicación se comporta de manera correcta. También es útil para optimizar la aplicación. Por ejemplo, un número relativamente alto de "suspensiones completas de cola" sugiere que un aumento en el tamaño de la cola podría ser beneficioso.

### <a name="queue-control-block-tx_queue"></a>TX_QUEUE: bloque de control de cola

Las características de cada cola de mensajes se encuentran en su bloque de control. Contiene información interesante, como el número de mensajes de la cola. Esta estructura se define en el archivo ***tx_api.h***.

Los bloques de control de cola de mensajes también se pueden colocar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global mediante su definición fuera del ámbito de cualquier función.

### <a name="message-destination-pitfall"></a>Problema de destino de mensajes

Como se ha mencionado antes, los mensajes se copian entre el área de cola y las áreas de datos de la aplicación. Es importante asegurarse de que el destino de un mensaje recibido sea lo suficientemente grande como para contener todo el mensaje. De lo contrario, es probable que la memoria que sigue al destino del mensaje resulte dañada.

> [!NOTE]
> *Esto es especialmente grave cuando un destino de mensaje demasiado pequeño está en la pila; no hay nada peor que los daños en la dirección de devolución de una función.*

## <a name="counting-semaphores"></a>Semáforos de recuento

ThreadX proporciona semáforos de recuento de 32 bits con un valor que oscila entre 0 y 4 294 967 295. Hay dos operaciones para el recuento de semáforos: *tx_semaphore_get* y *tx_semaphore_put*. La operación Get reduce el semáforo en uno. Si el semáforo es 0, la operación Get no se realiza correctamente. La operación Put es la inversa de la operación Get.
Aumenta el semáforo en uno.

Cada semáforo de recuento es un recurso público. ThreadX no aplica restricciones al modo de usar los semáforos de recuento.

Los semáforos de recuento se usan normalmente para la *exclusión mutua*. Pero también se pueden usar como un método para la notificación de eventos.

### <a name="mutual-exclusion"></a>Exclusión mutua

 La exclusión mutua corresponde a controlar el acceso de los subprocesos a determinadas áreas de la aplicación (también denominadas *secciones críticas* o *recursos de aplicación*). Cuando se usa para la exclusión mutua, el "recuento actual" de un semáforo representa el número total de subprocesos a los que se permite el acceso. En la mayoría de los casos, el recuento de semáforos usados para la exclusión mutua tendrá un valor inicial de 1, lo que significa que solo un subproceso puede acceder al recurso asociado a la vez. Los semáforos de recuento que solo tienen los valores 0 o 1 se denominan normalmente *semáforos binarios*.

> [!IMPORTANT]
> *Si se usa un semáforo binario, el usuario debe evitar que el mismo subproceso realice una operación Get en un semáforo que ya posee. Una segunda operación Get no sería correcta y podría provocar una suspensión indefinida del subproceso que realiza la llamada y la falta de disponibilidad permanente del recurso.*

### <a name="event-notification"></a>Notificación de evento

También es posible usar semáforos de recuento como notificación de eventos, a modo productor-consumidor. El consumidor intenta obtener el semáforo de recuento mientras el productor lo aumenta siempre que hay algo disponible. Estos semáforos suelen tener un valor inicial de 0 y no aumentan hasta que el productor tiene algo preparado para el consumidor. Los semáforos que se usan para la notificación de eventos también se pueden beneficiar del uso de la llamada al servicio ***tx_semaphore_ceiling_put***. Este servicio garantiza que el recuento del semáforo nunca supere el valor proporcionado en la llamada.

### <a name="creating-counting-semaphores"></a>Creación de semáforos de recuento

Los semáforos de recuento se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de aplicación. El recuento inicial del semáforo se especifica durante la creación. No hay ningún límite en cuanto al número de semáforos de recuento de una aplicación.

### <a name="thread-suspension"></a>Suspensión de subprocesos

Los subprocesos de aplicación se pueden suspender mientras se intenta realizar una operación Get en un semáforo con un recuento actual de 0.

Después de realizar una operación Put, se realiza la operación Get del subproceso suspendido y se reanuda. Si se suspenden varios subprocesos en el mismo semáforo de recuento, se reanudan en el orden en el que se hayan suspendido (FIFO).

Pero la reanudación por prioridad también es posible si la aplicación llama a ***tx_semaphore_prioritize*** antes de la llamada a Put del semáforo que anula la suspensión de subprocesos. El servicio de clasificación por orden de prioridad del semáforo coloca al subproceso de mayor prioridad al principio de la lista de suspensión y deja a todos los demás subprocesos suspendidos en el mismo orden FIFO.

### <a name="semaphore-put-notification"></a>Notificación Put de semáforo

Es posible que algunas aplicaciones se beneficien de recibir una notificación cada vez que se agrega un semáforo. ThreadX proporciona esta función por medio del servicio ***tx_semaphore_put_notify***. Este servicio registra la función de notificación de aplicación proporcionada con el semáforo especificado. Después, ThreadX invocará esta función de notificación de aplicación cada vez que se coloque el semáforo. El procesamiento exacto dentro de la función de notificación de aplicación viene determinado por la aplicación; pero normalmente consiste en reanudar el subproceso adecuado para procesar el nuevo evento Put del semáforo.

### <a name="semaphore-event-chainingtrade"></a>Encadenamiento de eventos de semáforo&trade;

Las funciones de notificación de ThreadX se pueden usar para encadenar varios eventos de sincronización. Esto suele ser útil cuando un único subproceso debe procesar varios eventos de sincronización.

Por ejemplo, en lugar de suspender subprocesos independientes para un mensaje de cola, marcas de evento y un semáforo, la aplicación puede registrar una rutina de notificación para cada objeto. Cuando se invoca, la rutina de notificación de aplicación puede reanudar un solo subproceso, que puede solicitar a cada objeto que busque y procese el nuevo evento.

En general, el *encadenamiento de eventos* genera menos subprocesos, menos sobrecarga y menos requisitos de RAM. También proporciona un mecanismo muy flexible para controlar los requisitos de sincronización de sistemas más complejos.

### <a name="run-time-semaphore-performance-information"></a>Información de rendimiento de semáforos en tiempo de ejecución

ThreadX proporciona información opcional sobre el rendimiento de los semáforos en tiempo de ejecución. Si la biblioteca y la aplicación de ThreadX se compilan con **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** definido, ThreadX acumula la información siguiente.

Número total del sistema general:

  - operaciones Put de semáforo

  - operaciones Get de semáforo

  - suspensiones de operaciones Get de semáforo

  - tiempos de espera de operaciones Get de semáforo

Número total en cada semáforo:

  - operaciones Put de semáforo

  - operaciones Get de semáforo

  - suspensiones de operaciones Get de semáforo

  - tiempo de espera de operaciones Get de semáforo

Esta información está disponible en tiempo de ejecución por medio de los servicios ***tx_semaphore_performance_info_get** _ y _*_tx_semaphore_performance_system_info_get_**. La información de rendimiento de los semáforos resulta útil para determinar si la aplicación se comporta de manera correcta. También es útil para optimizar la aplicación. Por ejemplo, un número relativamente alto de "tiempos de espera de operaciones Get de semáforo" podría sugerir que otros subprocesos conservan los recursos durante demasiado tiempo.

### <a name="semaphore-control-block-tx_semaphore"></a>TX_SEMAPHORE: bloque de control de semáforo

Las características de cada semáforo de recuento se encuentran en su bloque de control. Contiene información como el recuento de semáforos actual. Esta estructura se define en el archivo ***tx_api.h***.

Los bloques de control de semáforos se pueden colocar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global mediante su definición fuera del ámbito de cualquier función.

### <a name="deadly-embrace"></a>Adopción letal

Uno de los problemas más interesantes y peligrosos asociados a los semáforos que se usan para la exclusión mutua es la *adopción letal*. Una adopción letal, o *interbloqueo*, es una condición en la que dos o más subprocesos se suspenden indefinidamente mientras intentan obtener semáforos que ya son propiedad de cada uno.

Esta condición se ilustra mejor con un ejemplo de dos subprocesos y dos semáforos. Imagine que el primer subproceso posee el primer semáforo y el segundo subproceso posee el segundo semáforo. Si el primer subproceso intenta obtener el segundo semáforo y, al mismo tiempo, el segundo subproceso intenta obtener el primer semáforo, los dos subprocesos entran en una condición de interbloqueo. Además, si estos subprocesos permanecen suspendidos de manera indefinida, sus recursos asociados también se bloquean de forma permanente. En la figura 8 se ilustra este ejemplo.

**Adopción letal** (ejemplo)

![Ejemplo de subprocesos suspendidos](./media/user-guide/example-suspended-threads.png)

**FIGURA 8. Ejemplo de subprocesos suspendidos**

En el caso de los sistemas en tiempo real, los interbloqueos se pueden evitar si se aplican determinadas restricciones al modo en que los subprocesos obtienen los semáforos. Los subprocesos solo pueden tener un semáforo a la vez. Como alternativa, los subprocesos pueden poseer varios semáforos si los obtienen en el mismo orden. En el ejemplo anterior, si el primer y el segundo subproceso obtienen el primero y el segundo semáforo en orden, se evita el interbloqueo.

> [!TIP]
> *También es posible usar el tiempo de espera de suspensión asociado a la operación Get para recuperarse de un interbloqueo.*

### <a name="priority-inversion"></a>Inversión de prioridades

Otra dificultad asociada a los semáforos de exclusión mutua es la inversión de prioridades. Este tema se describe con más detalle en "[Problemas de prioridad de subprocesos](#thread-priority-pitfalls)".

El problema básico se debe a una situación en la que un subproceso de prioridad baja tiene un semáforo que necesita un subproceso de prioridad superior. En sí mismo, esto es normal. Pero los subprocesos con prioridades intermedias pueden provocar que la inversión de prioridades dure una cantidad de tiempo no determinista. Esto se puede controlar mediante la selección cuidadosa de las prioridades de los subprocesos, con el umbral de adelantamiento y la elevación temporal de la prioridad del subproceso que posee el recurso a la del subproceso de mayor prioridad.

## <a name="mutexes"></a>Mutexes

Además de los semáforos, ThreadX también proporciona un objeto de exclusión mutua. Una exclusión mutua es básicamente un semáforo binario, lo que significa que solo un subproceso puede poseer una exclusión mutua a la vez. Además, el mismo subproceso puede realizar varias veces una operación Get de exclusión mutua correcta en una exclusión mutua en propiedad, 4 294 967 295 para ser exactos. En el objeto de exclusión mutua hay dos operaciones: ***tx_mutex_get** _ y _*_tx_mutex_put_**. La operación Get obtiene una exclusión mutua que no pertenece a otro subproceso, mientras que la operación Put libera una exclusión mutua obtenida previamente. Para que un subproceso libere una exclusión mutua, el número de operaciones Put debe ser igual al número de operaciones Get anteriores.

Cada exclusión mutua es un recurso público. ThreadX no aplica restricciones al modo de usar las exclusiones mutuas.

Las exclusiones mutuas de ThreadX se usan únicamente para la *exclusión mutua*. A diferencia de los semáforos de recuento, las exclusiones mutuas no se usan como método para la notificación de eventos.

### <a name="mutex-mutual-exclusion"></a>Exclusión mutua de exclusiones mutuas

De forma similar a la descripción de la sección sobre semáforos de recuento, la exclusión mutua se corresponde al control del acceso de los subprocesos a determinadas áreas de la aplicación (también denominadas *secciones críticas* o *recursos de aplicación*). Cuando está disponible, una exclusión mutua de ThreadX tendrá un recuento de propiedad de 0. Una vez que un subproceso obtiene la exclusión mutua, el recuento de propiedad se incrementa una vez por cada operación Get correcta realizada en la exclusión mutua y se reduce por cada operación Put correcta.

### <a name="creating-mutexes"></a>Creación de exclusiones mutuas

Las exclusiones mutuas de ThreadX se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de aplicación. La condición inicial de una exclusión mutua siempre es "disponible". También se puede crear una exclusión mutua con la *herencia de prioridades* seleccionada.

### <a name="thread-suspension"></a>Suspensión de subprocesos

Los subprocesos de aplicación se pueden suspender mientras se intenta realizar una operación Get en una exclusión mutua que ya pertenece a otro subproceso.

Una vez que el subproceso propietario realiza el mismo número de operaciones Put, se realiza la operación Get del subproceso suspendido, se le asigna la propiedad de la exclusión mutua y se reanuda el subproceso. Si se suspenden varios subprocesos en la exclusión mutua, se reanudan en el mismo orden en el que se hayan suspendido (FIFO).

Pero la reanudación por prioridad se realiza de forma automática si durante la creación se ha seleccionado la herencia de prioridad de exclusión mutua. La reanudación por prioridad también es posible si la aplicación llama a ***tx_mutex_prioritize*** antes de la llamada a Put de la exclusión mutua que anula la suspensión de subprocesos. El servicio de clasificación por orden de prioridad de las exclusiones mutuas coloca al subproceso de mayor prioridad al principio de la lista de suspensión y deja a todos los demás subprocesos suspendidos en el mismo orden FIFO.

### <a name="run-time-mutex-performance-information"></a>Información de rendimiento de exclusiones mutuas en tiempo de ejecución

ThreadX proporciona información opcional sobre el rendimiento de las exclusiones mutuas en tiempo de ejecución. Si la biblioteca y la aplicación de ThreadX se compilan con **TX_MUTEX_ENABLE_PERFORMANCE_INFO** definido, ThreadX acumula la información siguiente.

Número total del sistema general:

- operaciones Put de exclusión mutua

- operaciones Get de exclusión mutua

- suspensiones de operaciones Get de exclusión mutua

- tiempos de espera de operaciones Get de exclusión mutua

- inversiones de prioridades de exclusión mutua

- herencia de prioridad de exclusión mutua

Número total en cada exclusión mutua:

  - operaciones Put de exclusión mutua

  - operaciones Get de exclusión mutua

  - suspensiones de operaciones Get de exclusión mutua

  - tiempos de espera de operaciones Get de exclusión mutua

  - inversiones de prioridades de exclusión mutua

  - herencia de prioridades de exclusión mutua

Esta información está disponible en tiempo de ejecución por medio de los servicios ***tx_mutex_performance_info_get** _ y _*_tx_mutex_performance_system_info_get_**. La información de rendimiento de las exclusiones mutuas resulta útil para determinar si la aplicación se comporta de manera correcta. También es útil para optimizar la aplicación. Por ejemplo, un número relativamente alto de "tiempos de espera de operaciones Get de exclusiones mutuas" podría sugerir que otros subprocesos conservan los recursos durante demasiado tiempo.

### <a name="mutex-control-block-tx_mutex"></a>TX_MUTEX: bloque de control de exclusión mutua

Las características de cada exclusión mutua se encuentran en su bloque de control. Contiene información como el recuento de propiedad de la exclusión mutua actual junto con el puntero del subproceso propietario de la exclusión mutua. Esta estructura se define en el archivo ***tx_api.h***. Los bloques de control de exclusiones mutuas se pueden colocar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global mediante su definición fuera del ámbito de cualquier función.

### <a name="deadly-embrace"></a>Adopción letal

Uno de los problemas más interesantes y peligrosos asociados a la propiedad de la exclusión mutua es la *adopción letal*. Una adopción letal, o *interbloqueo*, es una condición en la que dos o más subprocesos se suspenden indefinidamente mientras intentan obtener una exclusión mutua que ya pertenece a los otros subprocesos. La descripción de los *interbloqueos* y sus correcciones también es totalmente válida para el objeto de exclusión mutua.

### <a name="priority-inversion"></a>Inversión de prioridades

Como se ha mencionado antes, un problema importante asociado a la exclusión mutua es el de la inversión de prioridades. Este tema se describe con más detalle en "[Problemas de prioridad de subprocesos](#thread-priority-pitfalls)".

El problema básico se debe a una situación en la que un subproceso de prioridad baja tiene un semáforo que necesita un subproceso de prioridad superior. En sí mismo, esto es normal. Pero los subprocesos con prioridades entre ellos pueden provocar que la inversión de prioridades dure una cantidad de tiempo no determinista. A diferencia de los semáforos descritos anteriormente, el objeto de exclusión mutua de ThreadX tiene una *herencia de prioridades* opcional. La idea básica detrás de la herencia de prioridades es que, en un subproceso de prioridad inferior, su prioridad se aumenta temporalmente hasta que coincide con la de un subproceso de prioridad alta que quiere la misma exclusión mutua propiedad del subproceso de prioridad inferior. Cuando el subproceso de prioridad baja libera la exclusión mutua, se restaura su prioridad original y la propiedad de la exclusión mutua se asigna al subproceso de mayor prioridad. Esta característica elimina la inversión de prioridades no determinista mediante el enlace de la cantidad de inversión al tiempo en que el subproceso de prioridad baja conserva la exclusión mutua. Por supuesto, las técnicas descritas anteriormente en este capítulo para controlar la inversión de prioridades no determinista también son válidas con las exclusiones mutuas.

## <a name="event-flags"></a>Marcas de eventos

Las marcas de eventos proporcionan una herramienta eficaz para la sincronización de subprocesos. Cada marca de evento se representa con un solo bit. Las marcas de eventos se organizan en grupos de 32. Los subprocesos pueden operar en las 32 marcas de eventos de un grupo al mismo tiempo. Los eventos se establecen mediante ***tx_event_flags_set** _ y se recuperan con _*_tx_event_flags_get_**.

Para establecer las marcas de eventos se realiza una operación AND/OR lógica entre las marcas de evento actuales y las nuevas. El tipo de operación lógica (OR o AND) se especifica en la llamada a ***tx_event_flags_set***.

Existen opciones lógicas similares para la recuperación de marcas de eventos. Una solicitud Get puede especificar que todas las marcas de eventos especificadas sean obligatorias (una operación AND lógica).

Como alternativa, una solicitud Get puede especificar que cualquiera de las marcas de eventos especificadas satisfaga la solicitud (una operación OR lógica). El tipo de operación lógica asociada a la recuperación de marcas de eventos se especifica en la llamada a ***tx_event_flags_get***.

> [!IMPORTANT]
> *Las marcas de evento que satisfacen una solicitud GET se consumen, es decir, se establecen en cero si* *la solicitud especifica **TX_OR_CLEAR** *o* **TX_AND_CLEAR*** .

Cada grupo de marcas de evento es un recurso público. ThreadX no aplica restricciones al modo de usar los grupos de marcas de evento.

### <a name="creating-event-flags-groups"></a>Creación de grupos de marcas de eventos

Los grupos de marcas de eventos se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de aplicación. En el momento de su creación, todas las marcas de eventos del grupo se establecen en cero. No hay ningún límite en cuanto al número de grupos de marcas de eventos de una aplicación.

### <a name="thread-suspension"></a>Suspensión de subprocesos

Los subprocesos de aplicación se pueden suspender mientras se intenta obtener una combinación lógica de marcas de eventos de un grupo. Después de establecer una marca de evento, se revisan las solicitudes Get de todos los subprocesos suspendidos. Se reanudan todos los subprocesos que ahora tienen las marcas de evento necesarias.

> [!NOTE]
> *Todos los subprocesos suspendidos de un grupo de marcas de evento se revisan cuando se establecen sus marcas de evento. Esto, por supuesto, presenta una sobrecarga adicional. Por tanto, se recomienda limitar el número de subprocesos que usan el mismo grupo de marcas de evento a un número razonable.*

### <a name="event-flags-set-notification"></a>Notificación de establecimiento de marcas de evento

Es posible que algunas aplicaciones se beneficien de recibir una notificación cada vez que se establezca una marca de eventos. ThreadX proporciona esta función por medio del servicio ***tx_event_flags_set_notify***. Este servicio registra la función de notificación de aplicación proporcionada con el grupo de marcas de evento especificado. Después, ThreadX invocará esta función de notificación de aplicación cada vez que se establece una marca de evento en el grupo. El procesamiento exacto dentro de la función de notificación de aplicación viene determinado por la aplicación, pero normalmente consiste en reanudar el subproceso adecuado para procesar la nueva marca de evento.

### <a name="event-flags-event-chainingtrade"></a>Encadenamiento de eventos de marcas de evento&trade;

Las funciones de notificación de ThreadX se pueden usar para "encadenar" varios eventos de sincronización. Esto suele ser útil cuando un único subproceso debe procesar varios eventos de sincronización.

Por ejemplo, en lugar de suspender subprocesos independientes para un mensaje de cola, marcas de evento y un semáforo, la aplicación puede registrar una rutina de notificación para cada objeto. Cuando se invoca, la rutina de notificación de aplicación puede reanudar un solo subproceso, que puede solicitar a cada objeto que busque y procese el nuevo evento.

En general, el *encadenamiento de eventos* genera menos subprocesos, menos sobrecarga y menos requisitos de RAM. También proporciona un mecanismo muy flexible para controlar los requisitos de sincronización de sistemas más complejos.

### <a name="run-time-event-flags-performance-information"></a>Información de rendimiento de marcas de eventos en tiempo de ejecución

ThreadX proporciona información opcional sobre el rendimiento de las marcas de evento en tiempo de ejecución. Si la biblioteca y la aplicación de ThreadX se compilan con **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** definido, ThreadX acumula la información siguiente.

Número total del sistema general:

  - operaciones Set de marcas de eventos

  - operaciones Get de marcas de eventos

  - suspensiones de operaciones Get de marcas de eventos

  - tiempos de espera de operaciones Get de marcas de eventos

Número total en cada grupo de marcas de eventos:

  - operaciones Set de marcas de eventos

  - operaciones Get de marcas de eventos

  - suspensiones de operaciones Get de marcas de eventos

  - tiempo de espera GET de marcas de evento

Esta información está disponible en tiempo de ejecución por medio de los servicios ***tx_event_flags_performance_info_get** _ y _*_tx_event_flags_performance_system_info_get_*_. La información de rendimiento de las marcas de evento resulta útil para determinar si la aplicación se comporta de manera correcta. También es útil para optimizar la aplicación. Por ejemplo, un número relativamente alto de tiempos de espera en el servicio _ *_tx_event_flags_get_** podría sugerir que el tiempo de espera de la suspensión de las marcas de evento es demasiado corto.

### <a name="event-flags-group-control-block-tx_event_flags_group"></a>TX_EVENT_FLAGS_GROUP: bloque de control de grupos de marcas de evento

Las características de cada grupo de marcas de eventos se encuentran en su bloque de control. Contiene información como la configuración actual de las marcas de eventos y el número de subprocesos suspendidos para eventos. Esta estructura se define en el archivo ***tx_api.h***.

Los bloques de control de grupos de eventos se pueden colocar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global mediante su definición fuera del ámbito de cualquier función.

### <a name="memory-block-pools"></a>Grupos de bloques de memoria

En las aplicaciones en tiempo real, la asignación de memoria de una manera rápida y determinista siempre es un desafío. Con esto en mente, ThreadX proporciona la capacidad de crear y administrar varios grupos de bloques de memoria de tamaño fijo.

Como los grupos de bloques de memoria se componen de bloques de tamaño fijo, nunca hay problemas de fragmentación. Por supuesto, la fragmentación provoca un comportamiento que es inherentemente no determinista. Además, el tiempo necesario para asignar y liberar un bloque de memoria de tamaño fijo es comparable al de la manipulación de la lista de vínculo simple. Además, la asignación y desasignación de bloques de memoria se realiza al inicio de la lista disponible. Esto proporciona el procesamiento de la lista de vínculo más rápido posible y puede ayudar a mantener el bloque de memoria real en caché.

La falta de flexibilidad es el principal inconveniente de los grupos de memoria de tamaño fijo. El tamaño de bloque de un grupo debe ser lo suficientemente grande como para controlar los requisitos de memoria de peor caso de sus usuarios. Por supuesto, es posible que se desperdicie memoria si se realizan muchas solicitudes de memoria de tamaño diferente al mismo grupo. Una posible solución es crear varios grupos de bloques de memoria diferentes que contengan bloques de memoria de diferente tamaño.

Cada grupo de bloques de memoria es un recurso público. ThreadX no aplica restricciones al modo de usar los grupos.

### <a name="creating-memory-block-pools"></a>Creación de grupos de bloques de memoria

Los grupos de bloques de memoria se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de aplicación. No hay ningún límite en cuanto al número de grupos de bloques de memoria de una aplicación.

### <a name="memory-block-size"></a>Tamaño de bloques de memoria

Como se ha mencionado antes, los grupos de bloques de memoria contienen una serie de bloques de tamaño fijo. El tamaño del bloque, en bytes, se especifica durante la creación del grupo.

> [!NOTE]
> *ThreadX agrega una pequeña cantidad de sobrecarga (del tamaño de un puntero de C) a cada bloque de memoria del grupo. Además, es posible que ThreadX tenga que rellenar el tamaño de bloque para mantener el principio de cada bloque de memoria en la alineación adecuada.*

### <a name="pool-capacity"></a>Capacidad del grupo

El número de bloques de memoria de un grupo es una función del tamaño de bloque y el número total de bytes del área de memoria proporcionada durante la creación. Para calcular la capacidad de un grupo, se divide el tamaño de bloque (incluido el relleno y los bytes de sobrecarga del puntero) entre el número total de bytes en el área de memoria proporcionada.

### <a name="pools-memory-area"></a>Área de memoria del grupo

Como se ha mencionado antes, el área de memoria del grupo de bloques se especifica durante la creación. Como sucede con otras áreas de memoria de ThreadX, se puede ubicar en cualquier parte del espacio de direcciones del destino.

Esta es una característica importante debido a la gran flexibilidad que proporciona. Por ejemplo, imagine que un producto de comunicación tiene un área de memoria de alta velocidad para E/S. Esta área de memoria se administra fácilmente si se convierte en un grupo de bloques de memoria de ThreadX.

### <a name="thread-suspension"></a>Suspensión de subprocesos

Los subprocesos de aplicación se pueden suspender mientras se espera un bloque de memoria de un grupo vacío. Cuando se devuelve un bloque al grupo, el subproceso suspendido lo recibe y se reanuda.

Si se suspenden varios subprocesos en el mismo grupo de bloques de memoria, se reanudan en el orden en el que se suspendieron (FIFO).

Pero la reanudación por prioridad también es posible si la aplicación llama a ***tx_block_pool_prioritize*** antes de la llamada de liberación del bloque que anula la suspensión de subprocesos. El servicio de clasificación por orden de prioridad de los grupos de bloques coloca el subproceso de mayor prioridad al principio de la lista de suspensión y deja a todos los demás subprocesos suspendidos en el mismo orden FIFO.

### <a name="run-time-block-pool-performance-information"></a>Información de rendimiento de un grupo de bloques en tiempo de ejecución

ThreadX proporciona información opcional sobre el rendimiento de los grupos de bloques en tiempo de ejecución. Si la biblioteca y la aplicación de ThreadX se compilan con **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** definido, ThreadX acumula la información siguiente.

Número total del sistema general:

  - bloques asignados

  - bloques liberados

  - suspensiones de asignación

  - tiempos de espera de asignación

Número total en cada grupo de bloques:

  - bloques asignados

  - bloques liberados

  - suspensiones de asignación

  - tiempos de espera de asignación

Esta información está disponible en tiempo de ejecución por medio de los servicios ***tx_block_pool_performance_info_get** _ y _*_tx_block_pool_performance_system_info_get_**. La información de rendimiento de los grupos de bloques resulta útil para determinar si la aplicación se comporta de manera correcta. También es útil para optimizar la aplicación. Por ejemplo, un número relativamente alto de "suspensiones de asignación" podría sugerir que el grupo de bloques es demasiado pequeño.

### <a name="memory-block-pool-control-block-tx_block_pool"></a>TX_BLOCK_POOL: bloque de control de grupos de bloques de memoria

Las características de cada grupo de bloques de memoria se encuentran en su bloque de control. Contiene información como el número de bloques de memoria disponibles y el tamaño de bloque de memoria. Esta estructura se define en el archivo ***tx_api.h***.

Los bloques de control de grupos también se pueden colocar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global mediante su definición fuera del ámbito de cualquier función.

### <a name="overwriting-memory-blocks"></a>Sobrescritura de bloques de memoria

Es importante asegurarse de que el usuario de un bloque de memoria asignado no escriba fuera de sus límites. Si esto ocurre, los daños se producen en un área de memoria adyacente (normalmente posterior). Los resultados son imprevisibles y a menudo graves para la aplicación.

## <a name="memory-byte-pools"></a>Bloques de bytes de memoria

Los grupos de bytes de memoria de ThreadX son similares a un montón de C estándar. A diferencia del montón de C estándar, es posible tener varios grupos de bytes de memoria. Además, los subprocesos se pueden suspender en un grupo hasta que la memoria solicitada esté disponible.

Las asignaciones desde los bloques de bytes de memoria son similares a las llamadas a ***malloc** _ tradicionales, que incluyen la cantidad de memoria deseada (en bytes). La asignación de memoria desde el grupo usa un formato "el primero que sea válido", es decir, se usa el primer bloque de memoria libre que satisfaga la solicitud. El exceso de memoria de este bloque se convierte en un nuevo bloque y se vuelve a colocar en la lista de memoria libre. Este proceso se denomina *fragmentación*.

Los bloques de memoria libre adyacentes se *combinan* durante una búsqueda de asignación posterior de un bloque de memoria libre suficientemente grande. Este proceso se denomina *desfragmentación*.

Cada grupo de bytes de memoria es un recurso público. ThreadX no aplica restricciones al modo de usar los grupos, a excepción de que no se puede llamar a los servicios de bytes de memoria desde las ISR.

### <a name="creating-memory-byte-pools"></a>Creación de grupos de bytes de memoria

Los grupos de bytes de memoria se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de aplicación. No hay ningún límite en cuanto al número de grupos de bytes de memoria de una aplicación.

### <a name="pool-capacity"></a>Capacidad del grupo

El número de bytes que se pueden asignar en un grupo de bytes de memoria es ligeramente inferior al especificado durante la creación. Esto se debe a que la administración del área de memoria libre genera cierta sobrecarga. Cada bloque de memoria libre del grupo necesita el equivalente a dos punteros de C de sobrecarga. Además, el grupo se crea con dos bloques, un bloque libre grande y uno pequeño asignado de forma permanente al final del área de memoria. Este bloque asignado se usa para mejorar el rendimiento del algoritmo de asignación. Elimina la necesidad de comprobar continuamente el final del área del grupo durante la combinación.

Durante el tiempo de ejecución, la cantidad de sobrecarga del grupo suele aumentar. Las asignaciones de un número impar de bytes se rellenan para garantizar la alineación adecuada del bloque de memoria siguiente. Además, la sobrecarga aumenta a medida que el grupo se vuelve más fragmentado.

### <a name="pools-memory-area"></a>Área de memoria del grupo

El área de memoria de un grupo de bytes de memoria se especifica durante la creación. Como sucede con otras áreas de memoria de ThreadX, se puede ubicar en cualquier parte del espacio de direcciones del destino. Esta es una característica importante debido a la gran flexibilidad que proporciona. Por ejemplo, si el hardware de destino tiene un área de memoria de alta velocidad y otra de baja velocidad, el usuario puede administrar la asignación de memoria de las dos áreas si crea un grupo en cada una de ellas.

### <a name="thread-suspension"></a>Suspensión de subprocesos

Los subprocesos de aplicación se pueden suspender mientras se esperan bytes de memoria de un grupo. Cuando hay suficiente memoria contigua disponible, los subprocesos suspendidos reciben la memoria solicitada y se reanudan.

Si se suspenden varios subprocesos en el mismo grupo de bytes de memoria, se les asigna memoria (se reanudan) en el orden en el que se suspendieron (FIFO).

Pero la reanudación por prioridad también es posible si la aplicación llama a ***tx_byte_pool_prioritize*** antes de la llamada de liberación de bytes que anula la suspensión de subprocesos. El servicio de clasificación por orden de prioridad de los grupos de bytes coloca el subproceso de mayor prioridad al principio de la lista de suspensión y deja a todos los demás subprocesos suspendidos en el mismo orden FIFO.

### <a name="run-time-byte-pool-performance-information"></a>Información de rendimiento de un grupo de bytes en tiempo de ejecución

ThreadX proporciona información opcional sobre el rendimiento de los grupos de bytes en tiempo de ejecución. Si la biblioteca y la aplicación de ThreadX se compilan con ***TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO*** definido, ThreadX acumula la información siguiente.

Número total del sistema general:

  - asignaciones

  - versiones

  - fragmentos buscados

  - fragmentos combinados

  - fragmentos creados

  - suspensiones de asignación

  - tiempos de espera de asignación

Número total en cada grupo de bytes:

  - asignaciones

  - versiones

  - fragmentos buscados

  - fragmentos combinados

  - fragmentos creados

  - suspensiones de asignación

  - tiempos de espera de asignación

Esta información está disponible en tiempo de ejecución por medio de los servicios ***tx_byte_pool_performance_info_get** _ y _*_tx_byte_pool_performance_system_info_get_**. La información de rendimiento de los grupos de bytes resulta útil para determinar si la aplicación se comporta de manera correcta. También es útil para optimizar la aplicación. Por ejemplo, un número relativamente alto de "suspensiones de asignación" podría sugerir que el grupo de bytes es demasiado pequeño.

### <a name="memory-byte-pool-control-block-tx_byte_pool"></a>TX_BYTE_POOL: bloque de control de grupos de bytes de memoria

Las características de cada grupo de bytes de memoria se encuentran en su bloque de control. Contiene información útil, como el número de bytes disponibles en el grupo. Esta estructura se define en el archivo ***tx_api.h***.

Los bloques de control de grupos también se pueden colocar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global mediante su definición fuera del ámbito de cualquier función.

### <a name="nondeterministic-behavior"></a>Comportamiento no determinista

Aunque los grupos de bytes de memoria proporcionan la asignación de memoria más flexible, también sufren un comportamiento no determinista. Por ejemplo, un grupo de bytes de memoria puede tener 2000 bytes de memoria disponibles, pero es posible que no pueda satisfacer una solicitud de asignación de 1000 bytes. Esto se debe a que no hay ninguna garantía sobre cuántos de los bytes libres son contiguos. Incluso si existe un bloque libre de 1000 bytes, no hay ninguna garantía sobre el tiempo que se puede tardar en encontrar el bloque. Es totalmente posible que sea necesario buscar en todo el grupo de memoria para encontrar el bloque de 1000 bytes.

> [!TIP]
> *Como resultado del comportamiento no determinista de los grupos de bytes de memoria, por lo general se recomienda evitar el uso de servicios de bytes de memoria en áreas donde se necesita un comportamiento determinista y en tiempo real. Muchas aplicaciones realizan una asignación previa de su memoria necesaria durante la configuración de inicialización o en tiempo de ejecución.*

### <a name="overwriting-memory-blocks"></a>Sobrescritura de bloques de memoria

Es importante asegurarse de que el usuario de la memoria asignada no escriba fuera de sus límites. Si esto ocurre, los daños se producen en un área de memoria adyacente (normalmente posterior). Los resultados son imprevisibles y a menudo catastróficos para la ejecución del programa.

## <a name="application-timers"></a>Temporizadores de aplicación

La respuesta rápida a los eventos externos asincrónicos es la función más importante de las aplicaciones insertadas en tiempo real. Pero muchas de estas aplicaciones también deben realizar ciertas actividades en intervalos de tiempo predeterminados.

Los temporizadores de aplicación de ThreadX proporcionan a las aplicaciones la capacidad de ejecutar funciones de aplicación de C a intervalos de tiempo concretos. También es posible que un temporizador de aplicación expire una sola vez. Este tipo de temporizador se denomina *temporizador único*, mientras que los temporizadores con intervalos repetidos se denominan *temporizadores periódicos*.

Cada temporizador de aplicación es un recurso público. ThreadX no aplica restricciones al modo de usar los temporizadores de aplicación.

### <a name="timer-intervals"></a>Intervalos de temporizador

En ThreadX, los intervalos de tiempo se miden por interrupciones periódicas del temporizador. Cada interrupción del temporizador se denomina *tic* del temporizador. La aplicación especifica el tiempo real entre tics de temporizador, pero 10 ms es la norma en la mayoría de las implementaciones. La configuración del temporizador periódico normalmente se encuentra en el archivo de ensamblado ***tx_initialize_low_level***.

Merece la pena mencionar que el hardware subyacente debe tener la capacidad de generar interrupciones periódicas para que los temporizadores de aplicación funcionen. En algunos casos, el procesador tiene una capacidad de interrupción periódica integrada. Si el procesador no tiene esta capacidad, el panel del usuario debe tener un dispositivo periférico que pueda generar interrupciones periódicas.

> [!IMPORTANT]
> *ThreadX todavía puede funcionar incluso sin un origen de interrupción periódico, pero se deshabilita todo el procesamiento relacionado con el temporizador. Esto incluye la segmentación temporal, los tiempos de espera de suspensión y los servicios de temporizador.*

### <a name="timer-accuracy"></a>Precisión del temporizador

Las expiraciones del temporizador se especifican en tics. El valor de expiración especificado se reduce en uno en cada tic del temporizador. Como un temporizador de aplicación se puede habilitar justo antes de una interrupción del temporizador (o tic), el tiempo de expiración real puede ser hasta un tic anterior.

Si la tasa de tics del temporizador es de 10 ms, los temporizadores de aplicación pueden expirar hasta 10 ms antes. Esto es más importante para temporizadores de 10 ms que para los de 1 segundo. Evidentemente, el aumento de la frecuencia de interrupción del temporizador reduce este margen de error.

### <a name="timer-execution"></a>Ejecución del temporizador

Los temporizadores de aplicación se ejecutan en el orden en que se activan. Por ejemplo, si se crean tres temporizadores con el mismo valor de expiración y se activan, se garantiza que sus funciones de expiración correspondientes se ejecuten en el orden en el que se han activado.

### <a name="creating-application-timers"></a>Creación de temporizadores de aplicación

Los temporizadores de aplicación se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de aplicación. No hay ningún límite en cuanto al número de temporizadores de aplicación en una aplicación.

### <a name="run-time-application-timer-performance-information"></a>Información de rendimiento del temporizador de aplicación en tiempo de ejecución

ThreadX proporciona información opcional sobre el rendimiento de los temporizadores de aplicación en tiempo de ejecución. Si la biblioteca y la aplicación de ThreadX se compilan con **TX_TIMER_ENABLE_PERFORMANCE_INFO** definido, ThreadX acumula la información siguiente.

Número total del sistema general:

- activaciones

- desactivaciones

- reactivaciones (temporizadores periódicos)

- expirations

- ajustes de expiración

Número total en cada temporizador de aplicación:

- activaciones

- desactivaciones

- reactivaciones (temporizadores periódicos)

- expirations

- ajustes de expiración

Esta información está disponible en tiempo de ejecución por medio de los servicios ***tx_timer_performance_info_get** _ y _*_tx_timer_performance_system_info_get_**. La información de rendimiento de los temporizadores de aplicación resulta útil para determinar si la aplicación se comporta de manera correcta. También es útil para optimizar la aplicación.

### <a name="application-timer-control-block-tx_timer"></a>Bloque de control de temporizador de aplicación TX_TIMER

Las características de cada temporizador de aplicación se encuentran en su bloque de control. Contiene información útil, como el valor de identificación de expiración de 32 bits. Esta estructura se define en el archivo ***tx_api.h***.

Los bloques de control de temporizador de aplicación se pueden colocar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global definiéndolo fuera del ámbito de cualquier función.

### <a name="excessive-timers"></a>Temporizadores excesivos

De manera predeterminada, los temporizadores de aplicación se ejecutan desde dentro de un subproceso del sistema oculto que se ejecuta con prioridad cero, que suele ser mayor que cualquier subproceso de aplicación. Por este motivo, el procesamiento dentro de los temporizadores de aplicación debe ser mínimo.

También es importante evitar, siempre que sea posible, temporizadores que expiren en cada tic del temporizador. Esa situación podría inducir una sobrecarga excesiva en la aplicación.

> [!IMPORTANT]
> *Como se ha mencionado antes, los temporizadores de aplicación se ejecutan desde un subproceso del sistema oculto. Por tanto, es importante no seleccionar la suspensión en ninguna llamada de servicio de ThreadX realizada desde la función de expiración del temporizador de aplicación.*

## <a name="relative-time"></a>Tiempo relativo

Además de los temporizadores de aplicación mencionados antes, ThreadX proporciona un único contador de tics de 32 bits que aumenta continuamente. El contador de tics o *tiempo* se incrementa en uno en cada interrupción del temporizador.

La aplicación puede leer o establecer este contador de 32 bits mediante llamadas a ***tx_time_get** _ y _*_tx_time_set_**, respectivamente. La aplicación determina el uso de este contador de tics. ThreadX no lo usa de forma interna.

## <a name="interrupts"></a>Interrupciones

La respuesta rápida a los eventos asincrónicos es la función principal de las aplicaciones insertadas en tiempo real. La aplicación sabe que hay un evento de ese tipo presente por medio de interrupciones de hardware.

Una interrupción es un cambio asincrónico en la ejecución del procesador. Normalmente, cuando se produce una interrupción, el procesador de *interrupciones* guarda una pequeña parte de la ejecución actual en la pila y transfiere el control al vector de interrupción adecuado. El vector de interrupción es básicamente la dirección de la rutina responsable de controlar la interrupción de tipo específica. El procedimiento exacto de control de la interrupción es específico del procesador.

### <a name="interrupt-control"></a>Control de interrupción

El servicio ***tx_interrupt_control*** permite a las aplicaciones habilitar y deshabilitar las interrupciones. Este servicio devuelve la posición de habilitación o deshabilitación de la interrupción anterior. Es importante mencionar que el control de interrupción solo afecta al segmento del programa en ejecución. Por ejemplo, si un subproceso deshabilita las interrupciones, solo permanecerán deshabilitadas durante la ejecución de ese subproceso.

> [!NOTE]
> *Una interrupción no enmascarable (NMI) es una interrupción que el hardware no puede deshabilitar. Estas interrupciones se pueden usar en las aplicaciones de ThreadX; pero no se permite que la rutina de control de NMI de la aplicación use la administración de contextos de ThreadX ni ningún servicio de API.*

### <a name="threadx-managed-interrupts"></a>Interrupciones administradas de ThreadX

ThreadX proporciona a las aplicaciones la administración completa de las interrupciones. Esta administración incluye el guardado y la restauración del contexto de la ejecución interrumpida. Además, ThreadX permite que se llame a determinados servicios desde rutinas de servicio de interrupción (ISR). A continuación se muestra una lista de los servicios de ThreadX permitidos desde ISR de aplicación.

```c
tx_block_allocate
tx_block_pool_info_get tx_block_pool_prioritize
tx_block_pool_performance_info_get
tx_block_pool_performance_system_info_get tx_block_release
tx_byte_pool_info_get tx_byte_pool_performance_info_get
tx_byte_pool_performance_system_info_get
tx_byte_pool_prioritize tx_event_flags_info_get
tx_event_flags_get tx_event_flags_set
tx_event_flags_performance_info_get
tx_event_flags_performance_system_info_get
tx_event_flags_set_notify tx_interrupt_control
tx_mutex_performance_info_get
tx_mutex_performance_system_info_get tx_queue_front_send
tx_queue_info_get tx_queue_performance_info_get
tx_queue_performance_system_info_get tx_queue_prioritize
tx_queue_receive tx_queue_send tx_semaphore_get
tx_queue_send_notify tx_semaphore_ceiling_put
tx_semaphore_info_get tx_semaphore_performance_info_get
tx_semaphore_performance_system_info_get
tx_semaphore_prioritize tx_semaphore_put tx_thread_identify
tx_semaphore_put_notify tx_thread_entry_exit_notify
tx_thread_info_get tx_thread_resume
tx_thread_performance_info_get
tx_thread_performance_system_info_get
tx_thread_stack_error_notify tx_thread_wait_abort tx_time_get
tx_time_set tx_timer_activate tx_timer_change
tx_timer_deactivate tx_timer_info_get
tx_timer_performance_info_get
tx_timer_performance_system_info_get
```

> [!IMPORTANT]
> *No se permite la suspensión desde ISR. Por tanto, el parámetro **wait_option** para todas las llamadas de servicio de ThreadX realizadas desde una ISR se deben establecer en **TX_NO_WAIT**.*

### <a name="isr-template"></a>Plantilla de ISR

Para administrar las interrupciones de la aplicación, se debe llamar a varias utilidades de ThreadX al principio y al final de las ISR de aplicación. El formato exacto para el control de interrupciones varía entre puertos.

El siguiente segmento de código pequeño es típico de la mayoría de las ISR administradas de ThreadX. En la mayoría de los casos, este procesamiento está en lenguaje de ensamblado.

```c
_application_ISR_vector_entry:

; Save context and prepare for

; ThreadX use by calling the ISR

; entry function.

CALL _tx_thread_context_save

; The ISR can now call ThreadX

; services and its own C functions

; When the ISR is finished, context

; is restored (or thread preemption)

; by calling the context restore ; function. Control does not return!

JUMP _tx_thread_context_restore
```

### <a name="high-frequency-interrupts"></a>Interrupciones de alta frecuencia

Algunas interrupciones se producen con una frecuencia tan alta que al guardar y restaurar el contexto completo en cada interrupción se consumirá un ancho de banda de procesamiento excesivo. En esos casos, es habitual que la aplicación tenga una ISR de lenguaje de ensamblado pequeña que realiza una cantidad limitada de procesamiento para una mayoría de estas interrupciones de alta frecuencia.

Después de un momento determinado, es posible que la ISR pequeña tenga que interactuar con ThreadX. Esto se logra mediante una llamada a las funciones de entrada y salida descritas en la plantilla anterior.

### <a name="interrupt-latency"></a>Latencia de interrupción

ThreadX bloquea las interrupciones durante breves periodos de tiempo. La cantidad máxima de tiempo que las interrupciones se deshabilitan es el orden del tiempo necesario para guardar o restaurar el contexto de un subproceso.
