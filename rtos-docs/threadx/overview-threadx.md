---
title: Información general sobre Azure RTOS ThreadX
description: Obtenga más información sobre Azure ThreadX, un sistema operativo en tiempo real (RTOS) avanzado diseñado específicamente para aplicaciones profundamente insertadas.
author: philmea
ms.author: philmea
ms.date: 6/9/2021
ms.service: rtos
ms.topic: overview
ms.custom: contperf-fy21q4
ms.openlocfilehash: 4b6c8df5133f16cf3ed4006c12433ac426453cb5
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178211"
---
# <a name="overview-of-azure-rtos-threadx"></a>Información general sobre Azure RTOS ThreadX

Azure RTOS ThreadX es un sistema operativo en tiempo real avanzado de nivel industrial de Microsoft. Está diseñado específicamente para aplicaciones profundamente insertadas, en tiempo real y de IoT. Azure RTOS ThreadX proporciona recursos avanzados de programación, comunicación, sincronización, temporización, administración de memoria y administración de interrupciones. Además, Azure RTOS ThreadX tiene muchas características avanzadas, como su arquitectura picokernel™, la programación preemption-threshold™, event-chaining™, la generación de perfiles de ejecución, las métricas de rendimiento y el seguimiento de eventos del sistema. En combinación con su excelente facilidad de uso, Azure RTOS ThreadX es la opción ideal para las aplicaciones insertadas más exigentes. Azure RTOS ThreadX presenta miles de millones de implementaciones en una amplia gama de productos, incluidos dispositivos de consumo, electrónica médica y equipos de control industrial.

## <a name="threadx-footprint"></a>Superficie de memoria de ThreadX

Azure RTOS ThreadX posee un área de instrucciones notablemente pequeña de 2 KB y 1 KB de superficie mínima de memoria RAM. Este pequeño tamaño se debe en gran medida a su arquitectura picokernel™ sin superposición y al escalado automático. El escalado automático significa que solo los servicios (y la infraestructura de apoyo) que usa la aplicación se incluyen en la imagen final en tiempo de vínculo.

Estas son algunas de las características de tamaño típicas de Azure RTOS ThreadX.

|Servicio de Azure RTOS ThreadX  |Tamaño típico en bytes  |
|---------|---------|
|Servicios principales (requeridos) |2\.000  |
|Servicios de colas  |900  |
|Servicios de marcas de eventos  |900  |
|Servicios de semáforos  |450  |
|Servicios de exclusiones mutuas  |1,200  |
|Servicios de memoria de bloques  |550  |
|Servicios de memoria de bytes  |900  |

## <a name="threadx-execution-speed"></a>Velocidad de ejecución de ThreadX

Azure RTOS ThreadX logra un cambio de contexto submicrosegundo en los procesadores más populares y, en general, es más rápido que otros RTOS comerciales. Además de ser rápido, Azure RTOS ThreadX también es muy determinista. Consigue el mismo rendimiento rápido tanto si hay 200 subprocesos listos como si hay solo uno.

Estas son algunas características de rendimiento típicas de Azure RTOS ThreadX:

* Arranque rápido: Azure RTOS ThreadX arranca en menos de 120 ciclos.
* Eliminación opcional de comprobación de errores básica: la comprobación de errores básica de Azure RTOS ThreadX se puede omitir en tiempo de compilación. Esto puede ser útil cuando se ha verificado el código de la aplicación y ya no se requiere la comprobación de errores en cada parámetro. Omitir la comprobación de errores se puede hacer en una unidad de compilación en lugar de en todo el sistema.
* Diseño picokernel: los servicios no se superponen entre sí, con lo que se elimina la sobrecarga de llamadas a funciones innecesarias.
* Procesamiento de interrupciones optimizado: solo se guardan o restauran registros desde cero tras la entrada o salida del ISR, a menos que se necesite prevención.
* Procesamiento de API optimizado:

    |Servicio de Azure RTOS ThreadX  |Tiempo de servicio en microsegundos*  |
    |---------|---------|
    |Suspensión de subproceso  |0.6  |
    |Reanudación de subproceso  |0.6  |
    |Envío a la cola  |0,3  |
    |Recepción en la cola  |0,3  |
    |Obtención de semáforo  |0,2  |
    |Colocación de semáforo  |0,2  |
    |Cambio de contexto  |0,4  |
    |Respuesta de interrupción  |0,0 – 0,6  |

    **Cifras de rendimiento basadas en un procesador típico que se ejecuta a 200 MHz*.

## <a name="advanced-technology"></a>Tecnología avanzada

Azure RTOS ThreadX es notable por su programación del umbral de adelantamiento. Esta característica es exclusiva de Azure RTOS ThreadX y ha sido objeto de una extensa investigación académica. Puede conocer más información en el documento [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://ieeexplore.ieee.org/document/811269), de Yun Wang, Universidad Concordia, y Manas Saksena, Universidad de Pittsburgh.

Principales funcionalidades de Azure RTOS ThreadX:

* Recursos multitarea completos y generales
  * Subprocesos, temporizadores de aplicación, colas de mensajes, semáforos de recuento, exclusiones mutuas, marcas de eventos, bloques de memoria de bloques y de bytes
* Programación preventiva basada en prioridad
* Flexibilidad de prioridad: hasta 1024 niveles de prioridad
* Programación cooperativa
* Preemption-Threshold: exclusivo de Azure RTOS ThreadX, ayuda a reducir los cambios de contexto y a garantizar la programación (según la investigación académica)
* Protección de memoria por medio de Azure RTOS ThreadX MODULES
* Totalmente determinista
* Seguimiento de eventos: capture los últimos *n* eventos del sistema o la aplicación
* Event Chaining: registre una función de devolución de llamada "notify" específica de la aplicación para cada objeto de comunicación o sincronización de Azure RTOS ThreadX
* Azure RTOS ThreadX MODULES con protección de memoria opcional
* Métricas de rendimiento en tiempo de ejecución
  * Número de reanudaciones de subprocesos
  * Número de suspensiones de subprocesos
  * Número de prevenciones de subprocesos solicitadas
  * Número de prevenciones de interrupción de subprocesos asincrónicos
  * Número de inversiones de prioridad de subprocesos
  * Número de cesiones de subprocesos
* Kit de perfil de ejecución (EPK)
* Pila de interrupciones independiente
* Análisis de la pila en tiempo de ejecución
* Procesamiento de interrupciones del temporizador optimizado

## <a name="multicore-support-amp--smp"></a>Compatibilidad con varios núcleos (AMP y SMP)

Azure RTOS ThreadX estándar se suele usar en modo de multiproceso asimétrico (AMP), en el que una copia independiente de Azure RTOS ThreadX y la aplicación (o Linux) se ejecutan en cada núcleo y se comunican entre sí por medio de la memoria compartida o un mecanismo de comunicación entre procesadores, como OpenAMP (Azure RTOS ThreadX es compatible con OpenAMP).

En los entornos en los que la carga de los procesadores es muy dinámica, el multiproceso simétrico (SMP) de Azure RTOS ThreadX está disponible para las siguientes familias de procesadores:

* ARM Cortex-Ax
* ARM Cortex-Rx
* ARM Cortex-A5x 64-bit
* MIPS 34 K, 1004 K e interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP realiza el equilibrio de carga dinámico entre *n* procesadores. Permite que cualquier subproceso de cualquier núcleo acceda a todos los recursos de Azure RTOS ThreadX (colas, semáforos, marcas de eventos, bloques de memoria, etc.). Azure RTOS ThreadX SMP habilita todas las API de Azure RTOS ThreadX en todos los núcleos e incorpora las siguientes API nuevas aplicables a la actividad de SMP:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Protección de memoria por medio de Azure RTOS ThreadX MODULES

Un producto complementario denominado Azure RTOS ThreadX Modules permite que uno o más subprocesos de la aplicación se agrupen en un "módulo" que se puede cargar y ejecutar dinámicamente (o ejecutarse en contexto) en el destino.

Los módulos habilitan la actualización de campos, la corrección de errores y la creación de particiones de programa para permitir que las aplicaciones grandes ocupen solo la memoria que necesitan los subprocesos activos.

Los módulos también tienen un espacio de direcciones independiente de Azure RTOS ThreadX. De esta manera, Azure RTOS ThreadX puede colocar la protección de memoria (mediante MPU o MMU) en torno al módulo, de forma que el acceso accidental fuera del módulo no pueda dañar ningún otro componente de software.

## <a name="misra-compliant"></a>Conforme con MISRA

El código fuente de Azure RTOS ThreadX y Azure RTOS ThreadX SMP es compatible con MISRA-C:2004 y MISRA-C:2012. MISRA-C es un conjunto de instrucciones de programación para sistemas críticos que usan el lenguaje de programación C. Las instrucciones de MISRA-C originales se destinaban principalmente a aplicaciones de automoción; sin embargo, en la actualidad, MISRA-C se considera una herramienta aplicable a cualquier aplicación crítica para la seguridad. Azure RTOS ThreadX es conforme con todas las normas requeridas y obligatorias de MISRA-C:2004 y MISRA-C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certificación Misra":::

## <a name="supports-most-popular-tools"></a>Compatible con las herramientas más populares

Azure RTOS ThreadX es compatible con las herramientas de desarrollo insertadas más populares, incluido Embedded Workbench de IAR, que también tiene disponible el reconocimiento del kernel de Azure RTOS ThreadX más completo. La integración de herramientas adicionales incluye GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench, Imagination Codescape, Renesas e2studio, Metaware SeeCode, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore y todos los dispositivos análogos.

## <a name="adaptation-layer-for-threadx"></a>Capa de adaptación de ThreadX

Puede aliviar los problemas de migración de aplicaciones a Azure RTOS mediante [capas de adaptación](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) de ThreadX para varias API de RTOS heredadas (FreeRTOS, POSIX, OSEK, etc.).

> [!div class="nextstepaction"]
> [Introducción a Azure RTOS ThreadX](chapter1.md)