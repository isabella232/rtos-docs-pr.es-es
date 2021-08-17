---
title: 'Capítulo 2: Instalación y uso de Azure RTOS ThreadX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del kernel de alto rendimiento de Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a88dc75c3b01e8054f72b3e1475791f064eac0ded02b22ccd18dd46da8c7200a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785046"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a>Capítulo 2: Instalación y uso de Azure RTOS ThreadX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del kernel de alto rendimiento de Azure RTOS ThreadX.

## <a name="host-considerations"></a>Consideraciones sobre el host

El software insertado se suele desarrollar en equipos host con Windows o Linux (Unix). Una vez que la aplicación está compilada, vinculada y colocada en el host, se descarga en el hardware de destino para su ejecución.

Normalmente, la descarga en el destino se realiza desde el depurador de la herramienta de desarrollo. Después de finalizar la descarga, el depurador es responsable de proporcionar el control de ejecución de destino (ir, detener, punto de interrupción, etc.), así como el acceso a la memoria y a los registros del procesador.

La mayoría de los depuradores de las herramientas de desarrollo se comunican con el hardware de destino mediante conexiones de depuración en el chip (OCD), como JTAG (IEEE 1149.1) y el modo de depuración en segundo plano (BDM). Los depuradores también se comunican con el hardware de destino mediante conexiones de emulación en el circuito (ICE). Las conexiones OCD e ICE proporcionan soluciones sólidas con una intrusión mínima en el software residente de destino.

En cuanto a los recursos utilizados en el host, el código fuente de ThreadX se entrega en formato ASCII y requiere aproximadamente 1 MByte de espacio en el disco duro del equipo host.

## <a name="target-considerations"></a>Consideraciones sobre el destino

ThreadX requiere entre 2 KBytes y 20 KBytes de memoria de solo lectura (ROM) en el destino. También requiere de 1 a 2 KBytes adicionales de memoria de acceso aleatorio (RAM) del destino para la pila del sistema de ThreadX y otras estructuras de datos globales.

Para que las funciones relacionadas con el temporizador, como los tiempos de espera de las llamadas de servicio, la segmentación del tiempo y los temporizadores de la aplicación funcionen, el hardware de destino subyacente debe proporcionar un origen de interrupciones periódico. Si el procesador dispone de esta funcionalidad, ThreadX la usará. De lo contrario, si el procesador de destino no tiene la capacidad de generar una interrupción periódica, el hardware del usuario debe proporcionarla. La instalación y configuración de la interrupción del temporizador se encuentra normalmente en el archivo de ensamblado ***tx_initialize_low_level*** de la distribución de ThreadX.

> [!NOTE]
> *ThreadX sigue siendo funcional incluso si no hay disponible ningún origen de interrupciones de temporizador periódico. Sin embargo, ninguno de los servicios relacionados con el temporizador son funcionales.*

## <a name="product-distribution"></a>Distribución del producto

Azure RTOS ThreadX se puede obtener desde el repositorio de código fuente público en <https://github.com/azure-rtos/threadx/>.

A continuación se muestra una lista de varios archivos importantes del repositorio.

| Nombre de archivo | Descripción |
|------------------- | ----------- |
| **tx_api.h**                      | Archivo de encabezado de C que contiene todas las equivalencias del sistema, las estructuras de datos y los prototipos del servicio.                                                             |
| **tx_port.h**                     | Archivo de encabezado de C que contiene todas las definiciones y estructuras de datos específicos de la herramienta de desarrollo y del destino.                                                 |
| **demo_threadx.c**                | Archivo de C que contiene una pequeña aplicación de demostración.                                                                                                       |
| **tx.a (o tx.lib)**              | Versión binaria de la biblioteca de C de ThreadX que se distribuye con el paquete *estándar*.                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
>*Todos los nombres de archivo están en minúsculas. Esta convención de nomenclatura facilita la conversión de los comandos para plataformas de desarrollo Linux (Unix).*

## <a name="threadx-installation"></a>Instalación de ThreadX

ThreadX se instala mediante la clonación del repositorio de GitHub en el equipo local. La siguiente es la sintaxis típica para la creación de un clon del repositorio de ThreadX en el equipo.

```c
    git clone https://github.com/azure-rtos/threadx
```

También se puede descargar una copia del repositorio mediante el botón de descarga de la página principal de GitHub.

Además, hay instrucciones para compilar la biblioteca de ThreadX en la página principal del repositorio en línea.

> [!NOTE]
> *El software de la aplicación necesita acceso al archivo de biblioteca de ThreadX (normalmente **tx.a** o **tx.lib**) y los archivos de inclusión de C **_tx_api.h_* _ y _*_tx_port.h_*_. Esto se logra estableciendo la ruta de acceso adecuada para las herramientas de desarrollo o copiando estos archivos en el área de desarrollo de la aplicación._

## <a name="using-threadx"></a>Uso de ThreadX

Para usar ThreadX, el código de la aplicación debe incluir el archivo ***tx_api.h** _ durante la compilación y vincular con la biblioteca en tiempo de ejecución de ThreadX _*_tx.a_*_ (o _*_tx.lib_**).

Hay cuatro pasos necesarios para compilar una aplicación de ThreadX.

1. Incluya el archivo ***tx_api.h*** en todos los archivos de la aplicación que usen servicios o estructuras de datos de ThreadX.

1. Cree la función estándar de C ***main** _. Esta función debe llamar finalmente a _ *_tx_kernel_enter_** para iniciar ThreadX. La inicialización específica de la aplicación que no implique a ThreadX se puede agregar antes de entrar en el kernel.

      > [!IMPORTANT]
      > *La función de entrada de ThreadX ***tx_kernel_enter** _ nunca vuelve. Por tanto, asegúrese de no colocar ninguna llamada de función o procesamiento después de ella._

1. Cree la función ***tx_application_define***. Aquí es donde se crean los recursos iniciales del sistema. Algunos ejemplos de recursos del sistema son los subprocesos, las colas, los bloques de memoria, los grupos de marcas de eventos, las exclusiones mutuas y los semáforos.

1. Compile el código fuente de la aplicación y vincúlelo con la biblioteca en tiempo de ejecución de ThreadX ***tx.lib***. La imagen resultante se puede descargar en el destino y ejecutarse.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

En el sistema de ejemplo pequeño de la figura 1 se muestra la creación de un único subproceso con prioridad 3. El subproceso se ejecuta, incrementa un contador y, a continuación, entra en suspensión durante un tic del reloj.
Este proceso continúa indefinidamente.

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
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

Aunque este es un ejemplo sencillo, proporciona una buena plantilla para el desarrollo de aplicaciones reales.

## <a name="troubleshooting"></a>Solución de problemas

Cada distribución de ThreadX se entrega con una aplicación de demostración. Siempre es una buena idea poner en primer lugar el sistema de demostración en ejecución, ya sea en el hardware de destino real o en un entorno simulado.

Si el sistema de demostración no se ejecuta correctamente, estas son algunas sugerencias para la solución de problemas.

1. Determine qué parte de la demostración se está ejecutando.
1. Aumente los tamaños de la pila (esto es más importante en el código real de la aplicación que en la demostración).
1. Vuelva a compilar la biblioteca de ThreadX con TX_ENABLE_STACK_CHECKING definido. Esto habilita la comprobación de la pila de ThreadX integrada.
1. Omita temporalmente los cambios recientes para ver si el problema desaparece o cambia. Esta información debería resultar útil para los ingenieros de soporte técnico.

Siga los procedimientos descritos en "[Centro de atención al cliente](about-this-guide.md#customer-support-center)" para enviar la información recopilada en los pasos de solución de problemas.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración al compilar la biblioteca de ThreadX y la aplicación con ThreadX. Las opciones siguientes se pueden definir en el código fuente de la aplicación, en la línea de comandos o en el archivo de inclusión ***tx_user.h***.

> [!IMPORTANT]
> *Las opciones definidas en ***tx_user.h** _ solo se aplican si la aplicación y la biblioteca de ThreadX se compilan con el elemento _ *TX_INCLUDE_USER_DEFINE_FILE** definido.*

### <a name="smallest-configuration"></a>Configuración más pequeña

Para obtener el tamaño de código más pequeño, se deben tener en cuenta las siguientes opciones de configuración de ThreadX (en ausencia de todas las demás opciones).

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a>Configuración más rápida

Para lograr la ejecución más rápida, se han utilizado las mismas opciones de configuración que para la configuración más pequeña anterior, pero también se han tenido en cuenta estas opciones.

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

Más adelante se describen las [opciones de configuración detalladas](#detailed-configuration-options).

### <a name="global-time-source"></a>Origen de hora global

Para otros productos de Microsoft Azure RTOS (FileX, NetX, GUIX, USBX, etc.), ThreadX define el número de tics del temporizador de ThreadX que representa un segundo. El resto deriva sus requisitos de hora en función de esta constante. De manera predeterminada, el valor es 100, suponiendo una interrupción periódica de 10 ms. El usuario puede invalidar este valor mediante la definición de TX_TIMER_TICKS_PER_SECOND con el valor deseado en ***tx_port.h*** o en el IDE o en la línea de comandos.

### <a name="detailed-configuration-options"></a>Opciones de configuración detalladas

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

Cuando se define, esta opción habilita la recopilación de información de rendimiento sobre los grupos de bytes. De manera predeterminada, esta opción no está definida.

**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**

Cuando se define, esta opción habilita la recopilación de información de rendimiento sobre los grupos de bytes. De manera predeterminada, esta opción no está definida.

**TX_DISABLE_ERROR_CHECKING**

Omite la comprobación de errores de llamada de servicio básica. Cuando se define en el código fuente de la aplicación, todas las comprobaciones de errores de parámetros básicas están deshabilitadas. Esto puede mejorar el rendimiento hasta un 30 % y también puede reducir el tamaño de la imagen.

> [!NOTE]
> *Solo es seguro deshabilitar la comprobación de errores si la aplicación puede garantizar absolutamente que todos los parámetros de entrada siempre son válidos en todas las circunstancias, incluidos los parámetros de entrada derivados de la entrada externa. Si se proporciona una entrada no válida a la API con la comprobación de errores deshabilitada, el comportamiento resultante es indefinido y podría provocar datos dañados en la memoria o el bloqueo del sistema.*

> [!NOTE]
> *Los valores devueltos por la API de ThreadX que no se ven afectados por la deshabilitación de la comprobación de errores se muestran en negrita en la sección "Valores devueltos" de cada descripción de API en el capítulo 4. Los valores devueltos que no están en negrita son nulos si la comprobación de errores está deshabilitada mediante la opción TX_DISABLE_ERROR_CHECKING.*

**TX_DISABLE_NOTIFY_CALLBACKS**

Cuando se define, deshabilita las devoluciones de llamada de notificación para varios objetos de ThreadX. El uso de esta opción reduce ligeramente el tamaño del código y mejora el rendimiento. De manera predeterminada, esta opción no está definida.

**TX_DISABLE_PREEMPTION_THRESHOLD**

Cuando se define, deshabilita la característica de umbral de adelantamiento y reduce ligeramente el tamaño del código y mejora el rendimiento. Por supuesto, las funcionalidades de umbral de adelantamiento ya no están disponibles. De manera predeterminada, esta opción no está definida.

**TX_DISABLE_REDUNDANT_CLEARING**

Cuando se define, quita la lógica para inicializar con ceros las estructuras de datos globales de C de ThreadX. Solo se debe usar si el código de inicialización del compilador establece todos los datos globales de C no inicializados en cero. El uso de esta opción reduce ligeramente el tamaño del código y mejora el rendimiento durante la inicialización. De manera predeterminada, esta opción no está definida.

**TX_DISABLE_STACK_FILLING**

Cuando se define, deshabilita el establecimiento del valor 0xEF en cada byte de la pila de cada subproceso cuando se crea. De manera predeterminada, esta opción no está definida.

**TX_ENABLE_EVENT_TRACE**

Cuando se define, ThreadX habilita el código de recopilación de eventos para crear un búfer de seguimiento de TraceX.

**TX_ENABLE_STACK_CHECKING**

Cuando se define, habilita la comprobación de la pila en tiempo de ejecución de ThreadX, que incluye el análisis de la parte de la pila que se ha usado y el examen de las "barreras" del patrón de datos antes y después del área de pila. Si se detecta un error en la pila, se llama al controlador de errores de la pila de la aplicación registrado. Esta opción da como resultado una sobrecarga y un tamaño de código ligeramente mayores. Consulte la función de la API ***tx_thread_stack_error_notify*** para más información. De manera predeterminada, esta opción no está definida.

**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**

Cuando se define, habilita la recopilación de información de rendimiento sobre los grupos de marcas de eventos. De manera predeterminada, esta opción no está definida.

**TX_INLINE_THREAD_RESUME_SUSPEND**

Cuando se define, ThreadX mejora las llamadas a las API ***tx_thread_resume** _ y _ *_tx_thread_suspend_** mediante código en línea. Esto aumenta el tamaño del código, pero mejora el rendimiento de estas dos llamadas de API.

**TX_MAX_PRIORITIES**

Define los niveles de prioridad de ThreadX. Los valores válidos van de 32 a 1024 (ambos incluidos) y *deben* ser divisibles por 32. El incremento del número de niveles de prioridad admitidos aumenta el uso de RAM en 128 bytes por cada grupo de 32 prioridades. Sin embargo, solo tiene un efecto insignificante en el rendimiento. De manera predeterminada, este valor se establece en 32 niveles de prioridad.

**TX_MINIMUM_STACK**

Define el tamaño mínimo de la pila (en bytes). Se utiliza para la comprobación de errores cuando se crean subprocesos. El valor predeterminado es específico de la distribución y se encuentra en ***tx_port.h***.

**TX_MISRA_ENABLE**

Cuando se define, ThreadX emplea convenciones compatibles con MISRA C. Consulte ***ThreadX_MISRA_Compliance.pdf*** para más información.

**TX_MUTEX_ENABLE_PERFORMANCE_INFO**

Cuando se define, habilita la recopilación de información de rendimiento sobre las exclusiones mutuas. De manera predeterminada, esta opción no está definida.

**TX_NO_TIMER**

Cuando se define, la lógica del temporizador de ThreadX está completamente deshabilitada. Esto resulta útil en los casos en los que no se usan las características de temporizador de ThreadX (suspensión de un subproceso, tiempos de espera de API, segmentación de tiempo y temporizadores de aplicación). Si se especifica **TX_NO_TIMER**, también se debe definir la opción **TX_TIMER_PROCESS_IN_ISR**.

**TX_NOT_INTERRUPTABLE**

Cuando se define, ThreadX no intenta minimizar el tiempo de bloqueo de una interrupción. Esto da como resultado una ejecución más rápida, pero aumenta ligeramente el tiempo de bloqueo de las interrupciones.

**TX_QUEUE_ENABLE_PERFORMANCE_INFO**

Cuando se define, habilita la recopilación de información de rendimiento sobre las colas. De manera predeterminada, esta opción no está definida.

**TX_REACTIVATE_INLINE**

Cuando se define, realiza la reactivación de los temporizadores de ThreadX insertados en lugar de usar una llamada de función. Esto mejora el rendimiento, pero aumenta ligeramente el tamaño del código. De manera predeterminada, esta opción no está definida.

**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**

Cuando se define, habilita la recopilación de información de rendimiento sobre los semáforos. De manera predeterminada, esta opción no está definida.

**TX_THREAD_ENABLE_PERFORMANCE_INFO**

Cuando se define, habilita la recopilación de información de rendimiento sobre los subprocesos. De manera predeterminada, esta opción no está definida.

**TX_TIMER_ENABLE_PERFORMANCE_INFO**

Cuando se define, habilita la recopilación de información de rendimiento sobre los temporizadores. De manera predeterminada, esta opción no está definida.

**TX_TIMER_PROCESS_IN_ISR**

Cuando se define, elimina el subproceso interno del temporizador del sistema para ThreadX. Esto da como resultado un rendimiento mejorado en los eventos del temporizador y requisitos de RAM más pequeños porque ya no se necesitan la pila del temporizador y el bloque de control. Sin embargo, el uso de esta opción mueve todo el procesamiento de la expiración del temporizador al nivel de ISR del temporizador. De manera predeterminada, esta opción no está definida.

> [!NOTE]
> *Es posible que los servicios permitidos desde los temporizadores no se permitan desde ISR y, por lo tanto, no se permitan al usar esta opción.*

**TX_TIMER_THREAD_PRIORITY**

Define la prioridad del subproceso interno del temporizador del sistema de ThreadX. El valor predeterminado es prioridad 0, la prioridad más alta en ThreadX. El valor predeterminado se define en ***tx_port.h***.

**TX_TIMER_THREAD_STACK_SIZE**

Define el tamaño de la pila (en bytes) del subproceso interno del temporizador del sistema de ThreadX. Este subproceso procesa todas las solicitudes de suspensión de subprocesos, así como todos los tiempos de espera de las llamadas de servicio. Además, todas las rutinas de devolución de llamada del temporizador de la aplicación se invocan desde este contexto. El valor predeterminado es específico de la distribución y se encuentra en ***tx_port.h***.

## <a name="threadx-version-id"></a>Identificador de versión de ThreadX

El programador puede obtener la versión de ThreadX mediante el examen del archivo ***tx_port.h** _. Además, este archivo también contiene un historial de versiones de la distribución correspondiente. El software de la aplicación puede obtener la versión de ThreadX mediante el examen de la cadena global _*_tx_version_id**.
