---
title: 'Capítulo 2: Instalación y uso de Azure RTOS ThreadX SMP'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del kernel de alto rendimiento de Azure RTOS ThreadX SMP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d0a63f3798adbc634a43cdda7e9d44941de655d9333f9ae0fb4181f1a6c0566e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801910"
---
# <a name="chapter-2---installation--use-of-azure-rtos-threadx-smp"></a>Capítulo 2: Instalación y uso de Azure RTOS ThreadX SMP

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del kernel de alto rendimiento de Azure RTOS ThreadX SMP.

## <a name="host-considerations"></a>Consideraciones sobre el host

El software insertado se suele desarrollar en equipos host con Windows o Linux (Unix). Una vez que la aplicación está compilada, vinculada y colocada en el host, se descarga en el hardware de destino para su ejecución.

Normalmente, la descarga en el destino se realiza desde el depurador de la herramienta de desarrollo. Después de la descarga, el depurador es responsable de proporcionar el control de ejecución de destino (ir, detener, punto de interrupción, etc.), así como el acceso a los registros de memoria y del procesador.

La mayoría de los depuradores de herramientas de desarrollo se comunican con el hardware de destino mediante conexiones de depuración en chip (OCD), como JTAG (IEEE 1149.1) y el modo de depuración en segundo plano (BDM). Los depuradores también se comunican con el hardware de destino mediante conexiones de emulación en el circuito (ICE). Las conexiones OCD e ICE proporcionan soluciones sólidas con una intrusión mínima en el software residente de destino.

En cuanto a los recursos utilizados en el host, el código fuente de ThreadX SMP se entrega en formato ASCII y requiere aproximadamente 1 MByte de espacio en el disco duro del equipo host.

> [!IMPORTANT]
> Revise el archivo **readme_threadx.txt** proporcionado para ver las consideraciones y opciones adicionales del sistema host.

## <a name="target-considerations"></a>Consideraciones sobre el destino

ThreadX SMP requiere entre 2 y 20 KBytes de memoria de solo lectura (ROM) en el destino. Se requieren de 1 a 2 KBytes adicionales de memoria de acceso aleatorio (RAM) del destino para la pila del sistema de ThreadX SMP y otras estructuras de datos globales.

Para que las funciones relacionadas con el temporizador, como los tiempos de espera de las llamadas de servicio, la segmentación del tiempo y los temporizadores de la aplicación funcionen, el hardware de destino subyacente debe proporcionar un origen de interrupciones periódico. Si el procesador dispone de esta capacidad, ThreadX SMP la usará. De lo contrario, si el procesador de destino no tiene la capacidad de generar una interrupción periódica, el hardware del usuario debe proporcionarla. La instalación y configuración de la interrupción del temporizador se encuentra normalmente en el archivo de ensamblado ***tx_initialize_low_level*** de la distribución de ThreadX SMP.

> [!IMPORTANT]
> ThreadX SMP sigue funcionando, incluso si no hay disponible ningún origen de interrupción de temporizador periódico. Sin embargo, ninguno de los servicios relacionados con el temporizador está operativo. Revise el archivo **readme_threadx.txt** proporcionado para ver las consideraciones y opciones adicionales del sistema host.

## <a name="product-distribution"></a>Distribución del producto

El contenido exacto del disco de distribución depende del procesador de destino, las herramientas de desarrollo y el paquete de ThreadX SMP adquirido. Sin embargo, a continuación se muestra una lista de varios archivos importantes que son comunes a la mayoría de las distribuciones de productos:

### <a name="threadx_express_startuppdf"></a>ThreadX_Express_Startup.pdf

En este PDF se proporciona un sencillo procedimiento de cuatro pasos para empezar a ejecutar ThreadX SMP en una placa o procesador de destino específico y en herramientas de desarrollo específicas.

### <a name="readme_threadxtxt"></a>readme_threadx.txt

Archivo de texto que contiene información específica sobre el puerto ThreadX SMP, incluida la información sobre el procesador de destino y las herramientas de desarrollo.

| Herramienta | Descripción |
| -------------- | ------------------------------------------------------------------------------------------------- |
| **tx_api.h**  | Archivo de encabezado de C que contiene todas las equivalencias del sistema, las estructuras de datos y los prototipos del servicio.             |
| **tx_port.h** | Archivo de encabezado de C que contiene todas las definiciones y estructuras de datos específicos de la herramienta de desarrollo y del destino. |
|**demo_threadx.c**| Archivo de C que contiene una pequeña aplicación de demostración.|
|**tx.a (o tx.lib)**| Versión binaria de la biblioteca de C de ThreadX SMP que se distribuye con el paquete *estándar*.|

> [!IMPORTANT]
> Todos los nombres de archivo están en minúsculas. Esta convención de nomenclatura facilita la conversión de los comandos en plataformas de desarrollo de Linux (Unix).

## <a name="threadx-smp-installation"></a>Instalación de ThreadX SMP

La instalación de ThreadX SMP es sencilla. Consulte el archivo ***ThreadX_Express_Startup.pdf** _ y el archivo _ *_readme_threadx.txt_** para obtener información específica sobre la instalación de ThreadX SMP para su entorno específico.

> [!IMPORTANT]
> Asegúrese de hacer una copia de seguridad del disco de distribución de ThreadX SMP y guárdelo en un lugar seguro.

> [!IMPORTANT]
> El software de la aplicación necesita acceso al archivo de biblioteca de ThreadX SMP (normalmente **tx.a** o **tx.lib**) y los archivos de inclusión de C **tx_api.h** y **tx_port.h**. Esto se logra estableciendo la ruta de acceso adecuada para las herramientas de desarrollo o copiando estos archivos en el área de desarrollo de la aplicación.

## <a name="using-threadx-smp"></a>Uso de ThreadX SMP

El uso de ThreadX SMP es fácil. Básicamente, el código de la aplicación debe incluir el archivo ***tx_api.h** _ durante la compilación y vincular con la biblioteca en tiempo de ejecución de ThreadX SMP _*_tx.a_*_ (o _*_tx.lib)_ **.

Hay cuatro pasos necesarios para compilar una aplicación de ThreadX SMP:

Incluya el archivo ***tx_api.h*** en todos los archivos de la aplicación que usen servicios o estructuras de datos de ThreadX SMP.

Cree la función estándar de C ***main** _. Esta función debe llamar finalmente a _ *_tx_kernel_enter_** para iniciar ThreadX SMP. La inicialización específica de la aplicación que no implique a ThreadX SMP se puede agregar antes de entrar en el kernel.

> [!IMPORTANT]
> La función de entrada de ThreadX SMP ***tx_kernel_enter** nunca vuelve. Por tanto, asegúrese de no colocar ninguna llamada de función o procesamiento después de ella.

Cree la función ***tx_application_define***. Aquí es donde se crean los recursos iniciales del sistema. Algunos ejemplos de recursos del sistema son los subprocesos, las colas, los bloques de memoria, los grupos de marcas de eventos, las exclusiones mutuas y los semáforos.

Compile el código fuente de la aplicación y vincúlelo con la biblioteca en tiempo de ejecución de ThreadX SMP ***tx.lib***. La imagen resultante se puede descargar en el destino y ejecutarse.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

En el sistema de ejemplo pequeño de la figura 1 de la página 28 se muestra la creación de un único subproceso con prioridad 3. El subproceso se ejecuta, incrementa un contador y, a continuación, entra en suspensión durante un tic del reloj. Este proceso continúa indefinidamente.

```c
#include              "tx_api.h"

unsigned long         my_thread_counter = 0;
TX_THREAD             my_thread;

main( )
{
      /* Enter the ThreadX SMP kernel. */
      tx_kernel_enter( );
}

void tx_application_define(void *first_unused_memory)
{

      /* Create my_thread! */
      tx_thread_create(&my_thread, "My Thread",
          my_thread_entry, 0x1234, first_unused_memory, 1024,
             3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}

void my_thread_entry(ULONG thread_input)
{
      /* Enter into a forever loop. */
      while(1)
      {

            /* Increment thread counter. */
            my_thread_counter++;

            /* Sleep for 1 tick. */
            tx_thread_sleep(1);
      }
}
```
**FIGURA 1. Plantilla para el desarrollo de aplicaciones**

Aunque este es un ejemplo sencillo, proporciona una buena plantilla para el desarrollo de aplicaciones reales. Una vez más, vea el archivo de ***readme_threadx.txt*** para obtener más detalles.

## <a name="troubleshooting"></a>Solución de problemas

Cada puerto de ThreadX SMP se entrega con una aplicación de demostración. Siempre es una buena idea iniciar en primer lugar la ejecución del sistema de demostración, ya sea en el hardware de destino real o en un entorno simulado.

> [!IMPORTANT]
> Vea el archivo **readme_threadx.txt** proporcionado con la distribución para obtener detalles más específicos sobre el sistema de demostración.

Si el sistema de demostración no se ejecuta correctamente, estas son algunas sugerencias para la solución de problemas:

  - Determine qué parte de la demostración se está ejecutando.

  - Aumente los tamaños de pila (esto es más importante en el código de aplicación real que en el de demostración).

  - Vuelva a compilar la biblioteca de ThreadX SMP con TX_ENABLE_STACK_CHECKING definido. Así se habilitará la comprobación de pila de ThreadX SMP integrada.

  - Omita temporalmente los cambios recientes para ver si el problema desaparece o cambia. Esta información debería resultar útil para los ingenieros de soporte técnico.

Siga los procedimientos descritos en "Qué necesitamos de usted" de la página 12 para enviar la información recopilada en los pasos de solución de problemas.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración al compilar la biblioteca de ThreadX SMP y la aplicación con ThreadX SMP. Las opciones siguientes se pueden definir en el código fuente de la aplicación, en la línea de comandos o en el archivo de inclusión ***tx_user.h***.

> [!IMPORTANT]
> Las opciones definidas en **tx_user.h** solo se aplican si la aplicación y la biblioteca de ThreadX SMP se compilan con el elemento **TX_INCLUDE_USER_DEFINE_FILE** definido.

### <a name="smallest-configuration"></a>Configuración más pequeña
Para obtener el tamaño de código más pequeño, se deben tener en cuenta las siguientes opciones de configuración de ThreadX SMP (en ausencia de todas las demás opciones):

- TX_DISABLE_ERROR_CHECKING
- TX_DISABLE_PREEMPTION_THRESHOLD
- TX_DISABLE_NOTIFY_CALLBACKS 
- TX_DISABLE_REDUNDANT_CLEARING 
- TX_DISABLE_STACK_FILLING 
- TX_NOT_INTERRUPTABLE 
- TX_TIMER_PROCESS_IN_ISR

### <a name="fastest-configuration"></a>Configuración más rápida 
Para lograr la ejecución más rápida, se han usado las mismas opciones de configuración que para la configuración más pequeña anterior, pero también se ha tenido en cuenta esta opción:

- TX_REACTIVATE_INLINE

Revise el archivo ***readme_threadx.txt*** para ver las opciones adicionales de su versión específica de ThreadX SMP. Las opciones de configuración detalladas se describen a partir de la página 28.

### <a name="global-time-source"></a>Origen de hora global  
Para otros productos de Azure RTOS (FileX, NetX, GUIX, USBX, etc.), ThreadX SMP define el número de tics del temporizador de ThreadX SMP que representa un segundo. El resto deriva sus requisitos de hora en función de esta constante. De manera predeterminada, el valor es 100, suponiendo una interrupción periódica de 10 ms. El usuario puede invalidar este valor mediante la definición de TX_TIMER_TICKS_PER_SECOND con el valor deseado en ***tx_port.h*** o en el IDE o en la línea de comandos.

### <a name="detailed-configuration-options"></a>Opciones de configuración detalladas

- **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO**: cuando se define, habilita la recopilación de información de rendimiento en grupos de bloques. De manera predeterminada, esta opción no está definida.
- **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**: cuando se define, habilita la recopilación de información de rendimiento en grupos de bytes. De manera predeterminada, esta opción no está definida.
- **TX_DISABLE_ERROR_CHECKING**: omite la comprobación básica de errores de llamadas de servicio. Cuando se define en el código fuente de la aplicación, todas las comprobaciones básicas de errores de parámetros están deshabilitadas. Esto puede mejorar el rendimiento hasta un 30 % y también puede reducir el tamaño de la imagen.

> [!NOTE]
> *Solo es seguro deshabilitar la comprobación de errores si la aplicación puede garantizar absolutamente que todos los parámetros de entrada siempre son válidos en todas las circunstancias, incluidos los parámetros de entrada derivados de la entrada externa. Si se proporciona una entrada no válida a la API con la comprobación de errores deshabilitada, el comportamiento resultante es indefinido y podría provocar datos dañados en la memoria o el bloqueo del sistema.*

> [!NOTE]
> *Los valores devueltos por la API de ThreadX SMP que no se ven afectados por la deshabilitación de la comprobación de errores se muestran en negrita en la sección "Valores devueltos" de cada descripción de API del capítulo 4. Los valores devueltos que no están en negrita son nulos si la comprobación de errores se deshabilita mediante la opción TX_DISABLE_ERROR_CHECKING.*
- **TX_DISABLE_NOTIFY_CALLBACKS**: cuando se define, deshabilita las devoluciones de llamada de notificación para varios objetos de ThreadX SMP. El uso de esta opción reduce ligeramente el tamaño del código y mejora el rendimiento. De manera predeterminada, esta opción no está definida.
- **TX_DISABLE_PREEMPTION_THRESHOLD**: cuando se define, deshabilita la característica de umbral de prioridad, reduce ligeramente el tamaño del código y mejora el rendimiento. Por supuesto, las funcionalidades de umbral de prioridad ya no están disponibles. De manera predeterminada, esta opción no está definida.
- **TX_DISABLE_REDUNDANT_CLEARING**: cuando se define, quita la lógica para inicializar a cero las estructuras de datos de C globales de ThreadX SMP. Solo se debe usar si el código de inicialización del compilador establece todos los datos globales de C no inicializados en cero. El uso de esta opción reduce ligeramente el tamaño del código y mejora el rendimiento durante la inicialización. De manera predeterminada, esta opción no está definida.
- **TX_DISABLE_STACK_FILLING**: cuando se define, deshabilita el establecimiento del valor 0xEF en cada byte de la pila de cada subproceso cuando se crea. De manera predeterminada, esta opción no está definida.
- **TX_ENABLE_EVENT_TRACE**: cuando se define, ThreadX SMP habilita el código de recopilación de eventos para crear un búfer de seguimiento de TraceX. Consulte la guía del usuario de TraceX para obtener más información.
- **TX_ENABLE_STACK_CHECKING**: cuando se define, habilita la comprobación de la pila en tiempo de ejecución de ThreadX SMP, que incluye el análisis de qué cantidad de pila se ha usado y el examen de las "barreras" del patrón de datos antes y después del área de pila. Si se detecta un error en la pila, se llama al controlador registrado de errores de la pila de la aplicación. Esta opción da como resultado una sobrecarga y un tamaño de código ligeramente mayores. Consulte la API **_tx_- thread_stack_error_notify_** para más información. De manera predeterminada, esta opción no está definida.
- **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**: cuando se define, habilita la recopilación de información de rendimiento en grupos de marcas de eventos. De manera predeterminada, esta opción no está definida.
- **TX_INLINE_THREAD_RESUME_SUSPEND**: cuando se define, ThreadX SMP mejora las llamadas a la API **_tx_thread_resume_ *_ y _* _tx_thread_suspend_** a través de código en línea. Esto aumenta el tamaño del código, pero mejora el rendimiento de estas dos llamadas API.
- **TX_MAX_PRIORITIES**: define los niveles de prioridad para ThreadX SMP. Los valores válidos van de 32 a 1024 (inclusive) y deben ser divisibles por 32. El incremento del número de niveles de prioridad admitidos aumenta el uso de RAM en 128 bytes por cada grupo de 32 prioridades. Sin embargo, solo tiene un efecto insignificante en el rendimiento. De manera predeterminada, este valor se establece en 32 niveles de prioridad.
- **TX_MINIMUM_STACK**: define el tamaño mínimo de la pila (en bytes). Se utiliza para la comprobación de errores cuando se crean subprocesos. El valor predeterminado es específico del puerto y se encuentra en **_tx_port.h_**.
- **TX_MISRA_ENABLE**: cuando se define, ThreadX SMP emplea convenciones conformes a MISRA C. Consulte **_ThreadX_MISRA_Compliance.pdf_** para más información.
- **TX_MUTEX_ENABLE_PERFORMANCE_INFO**: cuando se define, habilita la recopilación de información de rendimiento en exclusiones mutuas. De manera predeterminada, esta opción no está definida.
- **TX_NO_TIMER**: cuando se define, la lógica del temporizador de ThreadX SMP está completamente deshabilitada. Esto resulta útil en los casos en los que no se usan las características de temporizador de ThreadX SMP (suspensión de subprocesos, tiempos de espera de API, segmentación de tiempo y temporizadores de aplicación).
- **TX_NOT_INTERRUPTABLE**: cuando se define, ThreadX SMP no intenta minimizar el tiempo de bloqueo de interrupción. Esto da como resultado una ejecución más rápida, pero aumenta ligeramente el tiempo de bloqueo de interrupción.
- **TX_QUEUE_ENABLE_PERFORMANCE_INFO**: cuando se define, habilita la recopilación de información de rendimiento en colas. De manera predeterminada, esta opción no está definida.
- **TX_REACTIVATE_INLINE**: cuando se define, realiza la reactivación de los temporizadores de ThreadX SMP en línea en lugar de usar una llamada de función. Esto mejora el rendimiento, pero aumenta ligeramente el tamaño del código. De manera predeterminada, esta opción no está definida.
- **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**: cuando se define, habilita la recopilación de información de rendimiento en semáforos. De manera predeterminada, esta opción no está definida.
- **TX_THREAD_ENABLE_PERFORMANCE_INFO**: cuando se define, habilita la recopilación de información de rendimiento en subprocesos. De manera predeterminada, esta opción no está definida.
- **TX_THREAD_SMP_CORE_MASK**: define la máscara de mapa de bits para la exclusión de núcleos. Por ejemplo, un entorno de 4 núcleos tiene un valor de 0xF definido.
- **TX_THREAD_SMP_DEBUG_ENABLE**: cuando se define, la información de depuración de ThreadX SMP se guarda en un búfer circular.
- **TX_THREAD_SMP_DYNAMIC_CORE_MAX**: cuando se define, habilita el número máximo dinámico de núcleos que se pueden ajustar en tiempo de ejecución.
- **TX_THREAD_SMP_EQUAL_PRIORITY**: cuando se define, ThreadX SMP solo programa los subprocesos de igual prioridad en paralelo. Debe definirse antes de compilar la biblioteca de ThreadX SMP.
- **TX_THREAD_SMP_INTER_CORE_INTERRUPT**: cuando se define, ThreadX SMP genera interrupciones entre núcleos.
- **TX_THREAD_SMP_MAX_CORES**: define el número máximo de núcleos.
- **TX_THREAD_SMP_ONLY_CORE_0_DEFAULT**: cuando se define, ThreadX SMP establece que de forma predeterminada todos los subprocesos y temporizadores se ejecuten solo en el núcleo 0. La aplicación puede invalidarlo llamando a las API de exclusión de núcleo. Debe definirse antes de compilar la biblioteca de ThreadX SMP.
- **TX_THREAD_SMP_WAKEUP_LOGIC**: cuando se define, se invoca la macro de aplicación para activar el núcleo "i". Debe definirse antes de la inclusión de  **_tx_port.h._**
- **TX_THREAD_SMP_WAKEUP (i)** : define una macro de aplicación para activar el núcleo "i". Debe definirse antes de la inclusión de  **_tx_port.h._**
- **TX_TIMER_ENABLE_PERFORMANCE_INFO**: cuando se define, habilita la recopilación de información de rendimiento en temporizadores. De manera predeterminada, esta opción no está definida.
- **TX_TIMER_PROCESS_IN_ISR**: cuando se define, elimina el subproceso interno del temporizador del sistema para ThreadX SMP. Esto da como resultado una mejora del rendimiento de los eventos del temporizador y menos requisitos de RAM porque ya no se necesitan la pila del temporizador y el bloque de control. Sin embargo, el uso de esta opción mueve todo el procesamiento de la expiración del temporizador al nivel de ISR del temporizador. De manera predeterminada, esta opción no está definida.

    > [!NOTE]
    > Es posible que los servicios permitidos desde los temporizadores no se permitan desde ISR y, por lo tanto, no se permitan al usar esta opción.

- **TX_TIMER_THREAD_PRIORITY**: define la prioridad del subproceso interno del temporizador del sistema ThreadX SMP. El valor predeterminado es la prioridad 0, la prioridad más alta en ThreadX SMP. El valor predeterminado se define en **_tx_port.h._**
- **TX_TIMER_THREAD_STACK_SIZE**: define el tamaño de la pila (en bytes) del subproceso interno del temporizador del sistema ThreadX SMP. Este subproceso procesa todas las solicitudes de suspensión de subprocesos, así como todos los tiempos de espera de las llamadas de servicio. Además, todas las rutinas de devolución de llamada del temporizador de la aplicación se invocan desde este contexto. El valor predeterminado es específico del puerto y se encuentra en **_tx_port.h_**.

## <a name="threadx-smp-version-id"></a>Id. de versión de ThreadX SMP

El id. de versión de ThreadX SMP se puede encontrar en el archivo ***readme_threadx.txt** _. Además, este archivo también contiene un historial de versiones del puerto correspondiente. El software de la aplicación puede obtener la versión de ThreadX SMP mediante el examen de la cadena global _ *_ _tx_version_id._**