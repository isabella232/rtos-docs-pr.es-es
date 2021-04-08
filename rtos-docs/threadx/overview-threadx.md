---
title: Información general sobre Azure RTOS ThreadX
description: Azure ThreadX es un sistema operativo en tiempo real (RTOS) avanzado diseñado específicamente para aplicaciones profundamente insertadas.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: acee58d9c48cb7a66993aaa5dc4a565dfe96234d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815617"
---
# <a name="overview-of-azure-rtos-threadx"></a>Información general sobre Azure RTOS ThreadX

Azure RTOS ThreadX es el sistema operativo en tiempo real (RTOS) avanzado de nivel industrial de Microsoft diseñado específicamente para aplicaciones profundamente insertadas en tiempo real de IoT. Azure RTOS ThreadX proporciona recursos avanzados de programación, comunicación, sincronización, temporización, administración de memoria y administración de interrupciones. Además, Azure RTOS ThreadX tiene muchas características avanzadas, como su arquitectura picokernel™, la programación preemption-threshold™, event-chaining™, la generación de perfiles de ejecución, las métricas de rendimiento y el seguimiento de eventos del sistema. En combinación con su excelente facilidad de uso, Azure RTOS ThreadX es la opción ideal para las aplicaciones insertadas más exigentes. En 2017, Azure RTOS ThreadX presumía de más de 6200 millones de implementaciones en una amplia gama de productos, incluidos dispositivos de consumo, electrónica médica y equipos de control industrial.

## <a name="api-protocols"></a>Protocolos de API

### <a name="azure-rtos-threadx-api"></a>API de Azure RTOS ThreadX

* API intuitivas y coherentes
* Convención de nomenclatura sustantivo-verbo
* Todas las API tienen *tx_* al inicio para identificarlas fácilmente como pertenecientes a Azure RTOS ThreadX
* Las API de bloqueo tienen un tiempo de espera de subprocesos opcional
* Muchas API están directamente disponibles desde los ISR de la aplicación

### <a name="azure-rtos-threadx-services"></a>Servicios de Azure RTOS ThreadX

* Creación de subprocesos dinámica
* Sin límites en el número de subprocesos
* Las API de subprocesos principales incluyen:
  * tx_thread_create
  * tx_thread_delete
  * tx_thread_preemption_change
  * tx_thread_priority_change
  * tx_thread_relinquish
  * tx_thread_reset
  * tx_thread_resume
  * tx_thread_sleep
  * tx_thread_suspend
  * tx_thread_terminate
  * tx_thread_wait_abort
* API de información adicional y rendimiento

### <a name="message-queues"></a>Colas de mensajes

* Creación de colas dinámica
* Sin límites en el número de colas
* Mensajes copiados por valor (o por referencia mediante puntero)
* Tamaños de mensaje de 1 a 16 palabras de 32 bits
* Suspensión de subprocesos opcional en bloques vacíos o llenos
* Tiempo de espera opcional en todas las suspensiones
* Las principales API de colas de mensajes incluyen:
  * tx_queue_create
  * tx_queue_delete
  * tx_queue_flush
  * tx_queue_front_send
  * tx_queue_receive
  * tx_queue_send_notify
* API de información adicional y rendimiento

### <a name="counting-semaphores"></a>Semáforos de recuento

* Creación dinámica de semáforos
* Sin límites en el número de semáforos
* Semáforos de recuento de 32 bits (de 0 a 4 294 967 295)
* Compatibilidad con la protección de recursos o consumidor-productor
* Suspensión de subprocesos opcional si no hay semáforos disponibles
* Tiempo de espera opcional en todas las suspensiones
* Las API de semáforos principales incluyen:
  * tx_semaphore_create
  * tx_semaphore_delete
  * tx_semaphore_get
  * tx_semaphore_put
  * tx_semaphore_put_notify
* API de información adicional y rendimiento

### <a name="mutexes"></a>Mutexes

* Creación de exclusiones mutuas dinámica
* Sin límites en el número de exclusiones mutuas
* Compatibilidad con la protección de recursos anidados
* Compatibilidad con la herencia de prioridad opcional
* Suspensión de subprocesos opcional si no hay exclusiones mutuas disponibles
* Tiempo de espera opcional en todas las suspensiones
* Las principales API de exclusiones mutuas incluyen:
  * tx_mutex_create
  * tx_mutex_delete
  * tx_mutex_get
  * tx_mutex_put
* API de información adicional y rendimiento

### <a name="event-flags"></a>Marcas de eventos

* Creación de grupos de marcas de eventos dinámica
* Sin límites en el número de grupos de marcas de eventos
* Sincronización de un subproceso o de varios
* Compatibilidad con la obtención y eliminación atómicas
* Suspensión de subprocesos opcional en conjunto de eventos AND/OR
* Tiempo de espera opcional en todas las suspensiones
* Las API de marcas de eventos principales incluyen:
  * tx_event_flags_create
  * tx_event_flags_delete
  * tx_event_flags_get
  * tx_event_flags_set
  * tx_event_flags_set_notify
* API de información adicional y rendimiento

### <a name="block-memory-pools"></a>Bloques de memoria de bloques

* Creación de bloques dinámica
* Sin límites en el número de bloques
* Sin límites en cuanto al tamaño de los bloques de tamaño fijo ni el tamaño del bloque
* Asignación o desasignación de memoria lo más rápida posible
* Suspensión de subprocesos opcional en bloques vacíos
* Tiempo de espera opcional en todas las suspensiones
* Las API de bloques principales incluyen:
  * tx_block_pool_create
  * tx_block_pool_delete
  * tx_block_allocate
  * tx_block_release
* API de información adicional y rendimiento

### <a name="byte-memory-pools"></a>Bloques de memoria de bytes

* Creación de bloques de bytes dinámica
* Sin límites en el número de bloques de bytes
* Sin límites en el tamaño del bloque de bytes
* Asignación o desasignación de memoria de longitud variable más flexible
* Situación de tamaño de asignación compatible
* Suspensión de subprocesos opcional en bloques vacíos
* Tiempo de espera opcional en todas las suspensiones
* Las API de bloques de bytes principales incluyen:
  * tx_byte_pool_create
  * tx_byte_pool_delete
  * tx_byte_allocate
  * tx_byte_release
* API de información adicional y rendimiento

### <a name="application-timers"></a>Temporizadores de aplicación

* Creación dinámica de temporizadores
* Sin límites en el número de temporizadores
* Compatibilidad con temporizadores periódicos o monoestables
* Los temporizadores periódicos pueden tener un valor de expiración inicial diferente
* Sin búsqueda durante la activación o desactivación del temporizador
* Todos los temporizadores se controlan desde una interrupción de temporizador de hardware
* Las API de temporizadores principales incluyen:
  * tx_timer_create
  * tx_timer_delete
  * tx_timer_activate
  * tx_timer_change
  * tx_timer_deactivate
* API de información adicional y rendimiento

### <a name="azure-rtos-threadx-core-scheduler"></a>Programador principal de Azure RTOS ThreadX

* Superficie mínima de 2 KB FLASH y 1 KB RAM
* Cambio de contexto rápido submicrosegundo
* Totalmente determinista independientemente del número de subprocesos
* Programación totalmente preventiva basada en prioridad
* 32 niveles de prioridad predeterminados, opcionalmente hasta 1024 niveles
* Programación cooperativa en nivel de prioridad (FIFO)
* Tecnología de umbral de prevención
* Servicios de temporizador opcionales, incluidos:
  * Porción de tiempo opcional por subproceso
  * Tiempo de espera opcional en todos los bloqueos
  * Las API requieren interrupción de temporizador de hardware
* Generación de perfiles de ejecución
* Seguimiento de nivel de sistema
* Seguridad certificada para muchos estándares

## <a name="most-deployed-rtos"></a>RTOS más implementado

Azure RTOS ThreadX presume de más de 6200 millones de implementaciones en todo el mundo, de acuerdo con la principal empresa de inteligencia de mercado de M2M, VDC Research. La popularidad de Azure RTOS ThreadX se debe a sus ventajas de confiabilidad, calidad, tamaño, rendimiento, características avanzadas, facilidad de uso y tiempo de comercialización general.

> *"Hemos seguido la trayectoria de crecimiento de THREADX en los mercados inalámbricos y de IoT desde la fundación de la empresa y estamos cada vez más impresionados de la adopción de THREADX por parte del sector".* – Chris Rommel, Vicepresidente Ejecutivo, VDC Research.

## <a name="small-footprint"></a>Superficie pequeña

Azure RTOS ThreadX requiere un área de instrucciones increíblemente pequeña de 2 KB y 1 KB de RAM para su superficie mínima. Esto se debe en gran medida a su arquitectura picokernel™ sin superposición y al escalado automático. El escalado automático significa que solo los servicios (y la infraestructura de apoyo) que usa la aplicación se incluyen en la imagen final en tiempo de vínculo.

Estas son algunas de las características de tamaño típicas de Azure RTOS ThreadX:

|Servicio de Azure RTOS ThreadX  |Tamaño típico en bytes  |
|---------|---------|
|Servicios principales (requeridos) |2\.000  |
|Servicios de colas  |900  |
|Servicios de marcas de eventos  |900  |
|Servicios de semáforos  |450  |
|Servicios de exclusiones mutuas  |1,200  |
|Servicios de memoria de bloques  |550  |
|Servicios de memoria de bytes  |900  |

## <a name="fast-execution"></a>Ejecución rápida

Azure RTOS ThreadX logra un cambio de contexto submicrosegundo en los procesadores más populares y, en general, es considerablemente más rápido que otros RTOS comerciales. Además de ser rápido, Azure RTOS ThreadX también es muy determinista. Consigue el mismo rendimiento rápido tanto si hay 200 subprocesos listos como si hay solo uno.

Estas son algunas características de rendimiento típicas de Azure RTOS ThreadX:

* Arranque rápido: Azure RTOS ThreadX arranca en menos de 120 ciclos.
* Eliminación opcional de comprobación de errores básica: la comprobación de errores básica de Azure RTOS ThreadX se puede omitir en tiempo de compilación. Esto puede ser útil cuando se ha verificado el código de la aplicación y ya no se requiere la comprobación de errores en cada parámetro. Tenga en cuenta que esto puede hacerse en una unidad de compilación y no en todo el sistema.
* Diseño picokernel™: los servicios no se superponen entre sí, con lo que se elimina la sobrecarga de llamadas a funciones innecesarias.
* *Procesamiento de interrupciones optimizado: solo se guardan o restauran registros desde cero tras la entrada o salida del ISR, a menos que se necesite prevención.
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

    **Cifras de rendimiento basadas en procesador típico que se ejecuta a 200 MHz*.

## <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>Certificado previamente por TUV y UL para varios estándares de seguridad

Azure RTOS ThreadX y Azure RTOS ThreadX SMP han sido certificados por SGS-TUV Saar para su uso en sistemas críticos para la seguridad, de acuerdo con IEC-61508 SIL 4, IEC-62304 clase de seguridad de SW C, ISO 26262 SIL D y EN 50128. La certificación confirma que Azure RTOS ThreadX y Azure RTOS ThreadX SMP se pueden usar en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de IEC-61508, IEC-62304, ISO 26262 y EN 50128 para la "Seguridad funcional de los sistemas eléctricos, electrónicos y electrónicos programables relacionados con la seguridad". SG-TUV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TUV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo. El estándar de seguridad industrial IEC 61508 y todos los estándares que se derivan de él, incluidos IEC-62304, ISO 26262 y EN 50128, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y electrónicos programables relacionados con la seguridad, los sistemas de control de procesos, la maquinaria industrial, los automóviles y los sistemas de control de ferrocarriles.

:::image type="content" source="media/overview-threadx/partener-logo-sgs-tuv-saar-2.png" alt-text="Certificación SG TUV SAAR":::

Azure RTOS ThreadX y Azure RTOS ThreadX SMP han sido reconocidos por UR por su conformidad con los estándares de seguridad para software de componentes programables UL 60730-1 anexo H, CSA E60730-1 anexo H, IEC 60730-1 anexo H, UL 60335-1 anexo R, IEC 60335-1 anexo R y UL 1998. UL es una empresa global e independiente especializada en la seguridad en la ciencia con más de un siglo de experiencia aportando innovaciones en soluciones de seguridad que abarcan desde la adopción pública de electricidad hasta los avances en sostenibilidad, energías renovables y nanotecnología.

:::image type="content" source="media/overview-threadx/cru-logo-certification.png" alt-text="Certificación UL":::

Los artefactos (certificado, manual de seguridad, informe de pruebas, etc.) asociados a las certificaciones TUV y UL están disponibles para su venta.

## <a name="eal4-common-criteria-security-certification"></a>Certificación de seguridad EAL4 + Common Criteria

Azure RTOS ha logrado la certificación de seguridad EAL4 + Common Criteria. El objetivo de la evaluación (TOE) cubre Azure RTOS ThreadX, Azure RTOS NetX-Duo, Azure RTOS NetX Secure TLS y Azure RTOS NetX MQTT. Representa los protocolos de IoT más habituales que requieren sensores, dispositivos, enrutadores perimetrales y puertas de enlace profundamente insertados.

:::image type="content" border="false" source="media/overview-threadx/eal-logo-certification.png" alt-text="Certificación EAL":::

El recurso de evaluación de seguridad de TI usado para la certificación de seguridad de Azure RTOS es Brightsight BV y la entidad de certificación es SERTIT.

## <a name="simple-easy-to-use"></a>Simple y fácil de usar

Azure RTOS ThreadX es muy fácil de usar. Las API de Azure RTOS ThreadX son intuitivas y muy funcionales. Los nombres de API se componen de palabras reales y no de la sopa de letras de nombres muy abreviados que son tan comunes en otros productos RTOS. Todas las API de Azure RTOS ThreadX tienen `tx_` al inicio y siguen una convención de nomenclatura sustantivo-verbo. Además, existe una coherencia funcional en la API. Por ejemplo, todas las API que se suspenden tienen un tiempo de espera opcional que funciona de forma idéntica para las API.

Es fácil compilar una aplicación de Azure RTOS ThreadX. La aplicación debe incluir *tx_api.h*, llamar a `tx_kernel_enter` desde Main, definir la función `tx_application_define` y crear un subproceso, definir la función de punto de entrada de subproceso y vincularse a la biblioteca de Azure RTOS ThreadX (normalmente *tx.a*).

Azure RTOS ThreadX también presume del mayor volumen de documentación disponible. 

## <a name="advanced-technology"></a>Tecnología avanzada

Azure RTOS ThreadX es una tecnología avanzada cuya característica más notable es la programación de umbral de prevención. Esta característica es exclusiva de Azure RTOS ThreadX y ha sido objeto de una extensa investigación académica. Por ejemplo, vea [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), de Yun Wang, Universidad Concordia, y Manas Saksena, Universidad de Pittsburgh.

Tenga en cuenta las capacidades de Azure RTOS ThreadX:

* Recursos multitarea completos y generales
  * Subprocesos, temporizadores de aplicación, colas de mensajes, semáforos de recuento, exclusiones mutuas, marcas de eventos, bloques de memoria de bloques y de bytes
* Programación preventiva basada en prioridad
* Flexibilidad de prioridad: hasta 1024 niveles de prioridad
* Programación cooperativa
* Preemption-Threshold™: exclusivo de Azure RTOS ThreadX, ayuda a reducir los cambios de contexto y a garantizar la programación (según la investigación académica)
* Protección de memoria por medio de Azure RTOS ThreadX MODULES
* Totalmente determinista
* Seguimiento de eventos: capture los últimos *n* eventos del sistema o la aplicación
* Event Chaining™: registre una función de devolución de llamada "notify" específica de la aplicación para cada objeto de comunicación o sincronización de Azure RTOS ThreadX
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

Azure RTOS ThreadX estándar se suele usar en modo de multiproceso asimétrico (AMP), en el que una copia independiente de Azure RTOS ThreadX y la aplicación (o Linux) se ejecutan en cada núcleo y se comunican entre sí por medio de la memoria compartida o un mecanismo de comunicación entre procesadores, como OpenAMP (Azure RTOS ThreadX es compatible con OpenAMP). Esta es la configuración de varios núcleos más típica con Azure RTOS ThreadX y puede ser la más eficaz si la aplicación es capaz de cargar realmente los procesadores.

En los entornos en los que la carga de los procesadores es muy dinámica, el multiproceso simétrico (SMP) de Azure RTOS ThreadX está disponible para las siguientes familias de procesadores:

* ARM Cortex-Ax
* ARM Cortex-Rx
* ARM Cortex-A5x 64-bit
* MIPS 34K, 1004K e interAptiv
* PowerPC
* Synopsys ARC HS
* x86

Azure RTOS ThreadX SMP realiza el equilibrio de carga dinámico en *n* procesadores y permite que cualquier subproceso de cualquier núcleo acceda a todos los recursos de ThreadX (colas, semáforos, marcas de eventos, bloques de memoria, etc.). Azure RTOS ThreadX SMP habilita todas las API de Azure RTOS ThreadX en todos los núcleos e incorpora las siguientes API nuevas aplicables a la actividad de SMP:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Protección de memoria por medio de Azure RTOS ThreadX MODULES

Un producto complementario denominado Azure RTOS ThreadX MODULES permite que uno o más subprocesos de la aplicación se agrupen en un "módulo" que se puede cargar y ejecutar dinámicamente (o ejecutarse en contexto) en el destino.

Los módulos habilitan la actualización de campos, la corrección de errores y la creación de particiones de programa para permitir que las aplicaciones grandes ocupen solo la memoria que necesitan los subprocesos activos.

Los módulos también tienen un espacio de direcciones completamente independiente de Azure RTOS ThreadX. De esta manera, Azure RTOS ThreadX puede colocar la protección de memoria (mediante MPU o MMU) en torno al módulo, de forma que el acceso accidental fuera del módulo no pueda dañar ningún otro componente de software.

## <a name="fastest-time-to-market"></a>Tiempo de comercialización más rápido

Azure RTOS ThreadX es fácil de instalar, conocer, usar, depurar, comprobar, certificar y mantener. Como resultado, Azure RTOS ThreadX ha sido el RTOS líder en cuanto a tiempo de comercialización durante los últimos siete años consecutivos, según las encuestas de Embedded Market Forecasters (EMF). Las encuestas muestran que el 70 % de los diseños que usan Azure RTOS ThreadX se comercializan a tiempo, lo que supera al resto de los RTOS.

A continuación se indica el porqué del ventajoso tiempo de comercialización:

* Documentación de calidad
* Disponibilidad completa del código fuente
* API fáciles de usar
* Conjunto de características completo y avanzado
* Amplia integración de herramientas de terceros: especialmente Embedded Workbench™ de IAR

## <a name="royalty-free"></a>Libre de regalías

No hay ningún costo asociado al uso y las pruebas del código fuente ni a las licencias de producción si se implementa en dispositivos con licencia previa; todos los demás dispositivos necesitan una licencia anual sencilla.

## <a name="full-highest-quality-source-code"></a>Código fuente completo y de máxima calidad

Desde el principio, Azure RTOS ThreadX se diseñó para ser un RTOS de nivel industrial distribuido con código fuente de C completo. El código fuente de Azure RTOS ThreadX ha establecido el estándar de calidad y facilidad de comprensión. Además, la convención de tener una función por archivo facilita la navegación por el origen.

Azure RTOS ThreadX se ajusta a estrictas convenciones de codificación, incluido el requisito de que cada línea de código de C tenga un comentario con sentido. Además, el origen de Azure RTOS ThreadX se ha certificado conforme a los estándares más altos.

## <a name="misra-compliant"></a>Conforme con MISRA

El código fuente de Azure RTOS ThreadX y Azure RTOS ThreadX SMP es conforme con MISRA-C:2004 y MISRA-C:2012. MISRA-C es un conjunto de instrucciones de programación para sistemas críticos que usan el lenguaje de programación C. Las instrucciones de MISRA-C originales se destinaban principalmente a aplicaciones de automoción; sin embargo, en la actualidad, MISRA-C se considera una herramienta aplicable a cualquier aplicación crítica para la seguridad. Azure RTOS ThreadX es conforme con todas las normas requeridas y obligatorias de MISRA-C:2004 y MISRA-C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certificación Misra":::

## <a name="supports-most-popular-architectures"></a>Compatible con las arquitecturas más populares

Azure RTOS ThreadX se ejecuta en los microprocesadores de 32 o 64 bits más populares, de serie, totalmente probado y totalmente compatible, lo que incluye lo siguiente:

* Dispositivos analógicos: SHARC, Blackfin, CM4xx
* Andes Core: RISC-V
* Ambiqmicro: Apollo MCUs
* ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-BI/A7x 64 bits/R4/R5, TrustZone ARMv8-M
* Cadence: Xtensa, Diamond
* CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi
* Cypress: RISC-V
* EnSilica: eSi-RISC
* Infineon: XMC1000, XMC4000, TriCore
* Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10
* Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32
* Microsemi: RISC-V
* NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4
* Renesas: SH, HS, V850, RX, RZ, Synergy
* Silicon Labs: EFM32
* Synopsys: ARC 600, 700, ARC EM, ARC HS
* ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7
* Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C
* Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class
* Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

## <a name="supports-most-popular-tools"></a>Compatible con las herramientas más populares

Azure RTOS ThreadX es compatible con las herramientas de desarrollo insertadas más populares, incluido Embedded Workbench™ de IAR, que también tiene disponible el reconocimiento del kernel de Azure RTOS ThreadX más completo. La integración de herramientas adicionales incluye GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore y todos los dispositivos análogos.
