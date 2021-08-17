---
title: 'Capítulo 1: Introducción a Azure RTOS ThreadX'
description: Este capítulo contiene una introducción a Azure RTOS ThreadX y una descripción de sus aplicaciones y ventajas.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 536b2d59bf9f2cf15d320b91277f0efc7bf96097329f690b0849b2145c5a3abc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802074"
---
# <a name="chapter-1---introduction-to-azure-rtos-threadx"></a>Capítulo 1: Introducción a Azure RTOS ThreadX

Azure RTOS ThreadX es un kernel en tiempo real de alto rendimiento diseñado específicamente para aplicaciones insertadas. Este capítulo contiene una introducción al producto y una descripción de sus aplicaciones y ventajas.

## <a name="threadx-unique-features"></a>Características únicas de ThreadX

A diferencia de otros kernels en tiempo real, ThreadX se ha diseñado para ser versátil y permitir escalar fácilmente entre pequeñas aplicaciones basadas en microcontroladores y aquellas que usan potentes procesadores CISC, RISC y DSP.

ThreadX es escalable en función de su arquitectura subyacente. Dado que los servicios de ThreadX se implementan como una biblioteca de C, solo se incorporan a la imagen en tiempo de ejecución aquellos que realmente se usan en la aplicación. Por lo tanto, la aplicación es la única que determina el tamaño real de ThreadX. En la mayoría de las aplicaciones, el tamaño de la imagen de instrucción de ThreadX se sitúa entre los 2 y los 15 KB.

### <a name="picokerneltrade-architecture"></a>Arquitectura de *picokernel&trade;*

En lugar de disponer las funciones de kernel en capas, unas encima de otras, como las arquitecturas de *microkernel* tradicionales, los servicios de ThreadX se conectan directamente a su núcleo. Así se consigue el máximo rendimiento posible del cambio de contexto y la llamada a los servicios. Llamamos a este diseño sin capas arquitectura de *picokernel*.

### <a name="ansi-c-source-code"></a>Código fuente ANSI C

ThreadX se escribe principalmente en ANSI C. Se necesita una pequeña parte de lenguaje de ensamblado para adaptar el kernel al procesador de destino subyacente. Este diseño permite distribuir ThreadX a una nueva familia de procesadores en un tiempo muy breve, normalmente en un plazo de semanas.

### <a name="advanced-technology"></a>Tecnología avanzada

A continuación se indican los aspectos destacados de la avanzada tecnología de ThreadX.
- Arquitectura de *picokernel* simple
- Escalado automático (pequeña superficie)
- Procesamiento determinista
- Rendimiento rápido en tiempo real
- Programación preferente y cooperativa
- Compatibilidad con la prioridad flexible de subprocesos
- Creación dinámica de objetos del sistema
- Número ilimitado de objetos del sistema
- Control optimizado de interrupciones
- Preemption-Threshold&trade;
- Herencia de prioridad
- Event-Chaining&trade;
- Temporizadores rápidos de software
- Administración de memoria en tiempo de ejecución
- Supervisión del rendimiento en tiempo de ejecución
- Análisis de la pila en tiempo de ejecución
- Seguimiento del sistema integrado
- Amplia compatibilidad con el procesador
- Amplia compatibilidad con herramientas de desarrollo
- Completamente independiente de endian

### <a name="not-a-black-box"></a>No es una caja negra

La mayoría de las distribuciones de ThreadX incluyen el código fuente de C completo, así como el lenguaje de ensamblado específico del procesador. Esto elimina los problemas de "caja negra" que se producen con muchos kernels comerciales. Con ThreadX, los desarrolladores de aplicaciones pueden ver exactamente lo que hace el kernel; no hay misterio.

Gracias a disponer del código fuente, también se pueden hacer modificaciones específicas de la aplicación. Aunque no se recomienda, es ciertamente útil contar con la posibilidad de modificar el kernel si es absolutamente necesario.

Estas características son especialmente idóneas para los desarrolladores acostumbrados a trabajar con sus propios *kernels internos*, ya que cuentan con tener el código fuente y la posibilidad de modificar el kernel. ThreadX es el kernel definitivo para estos desarrolladores.

### <a name="the-rtos-standard"></a>El estándar RTOS

Debido a su versatilidad, a la arquitectura de *picokernel* de alto rendimiento, a la tecnología avanzada y a la portabilidad demostrada, ThreadX ya se implementa en más de dos mil millones de dispositivos a día de hoy. Esto hace que ThreadX sea el estándar de RTOS para aplicaciones profundamente insertadas.

## <a name="safety-certifications"></a>Certificaciones de seguridad

### <a name="tv-certification"></a>Certificación TÜV

ThreadX está certificado por SG-TÜV Saar para su uso en sistemas críticos para la seguridad, según CEI-61508 y CEI-62304. La certificación confirma que se puede usar ThreadX en el desarrollo de software relacionado con la seguridad para los niveles de integridad de seguridad más altos de la Comisión electrotécnica internacional (CEI) 61508 y CEI 62304 para la "Seguridad funcional de los sistemas eléctricos, electrónicos y electrónicos programables relacionados con la seguridad". SGS-TÜV Saar, que es una sociedad conjunta entre las empresas alemanas SGS-Group y TÜV Saarland, se ha convertido en la empresa líder independiente acreditada para probar, auditar, comprobar y certificar software insertado para sistemas relacionados con la seguridad en todo el mundo. El estándar de seguridad industrial CEI 61508 y todos los estándares que se derivan de él, incluido CEI 62304, se usan para garantizar la seguridad funcional de los dispositivos médicos eléctricos, electrónicos y electrónicos programables relacionados con la seguridad, los sistemas de control de procesos, la maquinaria industrial y los sistemas de control de ferrocarriles.

SGS-TÜV Saar ha certificado ThreadX para su uso en sistemas de automóviles críticos para la seguridad, según el estándar ISO 26262. Además, ThreadX está certificado para el nivel D de integridad de la seguridad del automóvil (ASIL), que representa el nivel más alto de la certificación ISO 26262.

SGS-TÜV Saar también ha certificado ThreadX para su uso en aplicaciones ferroviarias críticas para la seguridad, cumpliendo el estándar EN 50128 hasta SW-SIL 4.

![Certificación TÜV](./media/overview-threadx/partener-logo-sgs-tuv-saar-2.png)

* CEI 61508 hasta SIL 4

* CEI 62304 hasta seguridad de software clase C

* ISO 26262 ASIL nivel D

* EN 50128 SW-SIL 4

> [!NOTE]
> *Póngase en contacto con nosotros para obtener más información sobre qué versiones de ThreadX están certificadas por TÜV o para disponer de informes de las pruebas, certificados y documentación asociada.*

### <a name="misra-c-compliant"></a>Compatibilidad con MISRA C

MISRA-C es un conjunto de instrucciones de programación para sistemas críticos que usan el lenguaje de programación C. Las instrucciones de MISRA-C originales se destinaban principalmente a aplicaciones de automoción; sin embargo, en la actualidad, MISRA-C se considera una herramienta aplicable a cualquier aplicación crítica para la seguridad. ThreadX es conforme con todas las normas requeridas y obligatorias de MISRA-C:2004 y MISRA-C:2012. ThreadX también es compatible con todas las reglas recomendadas excepto tres. Consulte el documento ***ThreadX_MISRA_Compliance.pdf*** para obtener más detalles.

### <a name="ul-certification"></a>Certificación UL

ThreadX ha sido certificado por UL por su conformidad con los estándares de seguridad para software de componentes programables UL 60730-1 anexo H, CSA E60730-1 anexo H, CEI 1 60730-1 anexo H, UL 60335-1 anexo R, CEI 60335-1 anexo R y UL 1998. Junto con CEI/UL 60730-1, que tiene requisitos para "Controles que usan software" en el anexo H, el estándar CEI 60335-1 describe los requisitos para "circuitos electrónicos programables" en el anexo R. CEI 60730 en su anexo H y CEI 60335-1 en su anexo R abordan la seguridad del hardware y el software MCU que se usa en dispositivos como lavadoras, lavavajillas, secadoras, frigoríficos, congeladores y hornos.

![Certificación UL](./media/overview-threadx/partener-logo-c-ru-us-2.png)

*UL/CEI 60730, UL/CEI 60335, UL 1998*

> [!NOTE]
> *Póngase en contacto con Microsoft para obtener más información sobre qué versiones de ThreadX están certificadas por TÜV o para disponer de informes de las pruebas, certificados y documentación asociada.*

### <a name="certification-pack"></a>Paquete de certificación

ThreadX Certification Pack&trade; es un paquete independiente, específico del sector, totalmente listo y completo que proporciona toda la evidencia de ThreadX necesaria para certificar o llevar con éxito al producto basado en ThreadX a los niveles de confiabilidad e importancia crítica más altos, necesarios para los sistemas de aviación, médicos e industriales críticos para la seguridad. Entre las certificaciones compatibles se incluyen DO-178B, ED-12B, DO-278, FDA510(k), CEI-62304, CEI-60601, ISO-14971, UL-1998, CEI-61508, CENELEC EN50128, BS50128 y 49CFR236. Póngase en contacto con Microsoft para obtener más información sobre el paquete de certificación.

## <a name="embedded-applications"></a>Aplicaciones insertadas

Las aplicaciones insertadas se ejecutan en microprocesadores escondidos dentro de productos como dispositivos de comunicación inalámbrica, motores de automóviles, impresoras láser, dispositivos médicos, etc. Otra característica de las aplicaciones insertadas es que su software y hardware tienen un fin concreto.

### <a name="real-time-software"></a>Software en tiempo real

Cuando se imponen restricciones de tiempo en el software de la aplicación, se denomina software en *tiempo real*. Las aplicaciones insertadas casi siempre son en tiempo real debido a su interacción inherente con eventos externos.

### <a name="multitasking"></a>Multitarea

Como se mencionó, las aplicaciones insertadas tienen un fin concreto. Para cumplir este fin, el software debe realizar una serie de *tareas*. Una tarea es una parte semiindependiente de la aplicación que lleva a cabo un servicio específico. También se da el caso de que algunas tareas son más importantes que otras. Una de las principales dificultades en una aplicación insertada es la asignación del procesador entre las distintas tareas de la aplicación. Esta asignación del procesamiento entre las diversas tareas que compiten entre sí es el propósito principal de ThreadX.

### <a name="tasks-vs-threads"></a>Tareas frente a subprocesos

Otra distinción acerca las tareas es que el término *tarea* se utiliza de diversas maneras. A veces hace referencia a un programa que se carga por separado. En otros casos, puede referirse a un segmento de programa interno. Por tanto, en los sistemas operativos modernos, hay dos términos que en cierta medida han reemplazado el uso del término tarea: *proceso* y *subproceso*. Un *proceso* es un programa completamente independiente que tiene su propio espacio de direcciones, en tanto que un *subproceso* es un segmento de programa semiindependiente que se ejecuta dentro de un proceso. Los subprocesos comparten el mismo espacio de direcciones del proceso. La sobrecarga asociada a la administración de subprocesos es mínima.

La mayoría de las aplicaciones insertadas no pueden permitirse la sobrecarga (tanto de memoria como de capacidad de proceso) asociada a un sistema operativo orientado a los procesos completos. Además, los microprocesadores más pequeños no tienen la arquitectura de hardware necesaria para utilizar un sistema operativo verdaderamente orientado a procesos. Por estos motivos, ThreadX implementa un modelo de subprocesos, que resulta extremadamente eficaz y práctico para la mayoría de aplicaciones insertadas en tiempo real.

Para evitar confusiones, ThreadX no usa el término *tarea*. En su lugar, se usa el término *subproceso* moderno, que es más descriptivo.

## <a name="threadx-benefits"></a>Ventajas de ThreadX

El uso de ThreadX ofrece muchas ventajas a las aplicaciones insertadas. Por supuesto, la principal ventaja reside en el modo en que se asigna el tiempo de procesamiento a los subprocesos de la aplicación insertada.

### <a name="improved-responsiveness"></a>Capacidad de respuesta mejorada

Antes de los kernels en tiempo real como ThreadX, la mayoría de las aplicaciones insertadas asignaban el tiempo de procesamiento con un bucle de control simple, normalmente desde la función *main* de C. Este enfoque se sigue usando en aplicaciones muy pequeñas o sencillas. Sin embargo, en aplicaciones grandes o complejas, no resulta práctico, porque el tiempo de respuesta a cualquier evento es una función del tiempo de procesamiento del peor caso de un paso a través del bucle de control. 

Para empeorarlo todavía más, las características de tiempo de la aplicación cambian cada vez que se realizan modificaciones en el bucle de control. Esto hace que la aplicación sea intrínsecamente inestable y difícil de mantener y mejorar.

ThreadX proporciona tiempos de respuesta rápidos y deterministas a eventos externos importantes. Esto se consigue gracias a su algoritmo de programación basado en prioridad y preferencia, que permite que un subproceso de prioridad más alta tenga preferencia sobre un subproceso en ejecución de menor prioridad. Como resultado, el tiempo de respuesta en el peor de los casos se aproxima al tiempo necesario para realizar un cambio de contexto. Esto no solo es determinista, sino también muy rápido.

### <a name="software-maintenance"></a>Mantenimiento de software

El kernel de ThreadX permite a los desarrolladores de aplicaciones concentrarse en requisitos específicos de los subprocesos de sus aplicaciones sin tener que preocuparse por cambiar los tiempos de otras áreas de la aplicación. Esta característica también hace que sea mucho más fácil reparar o mejorar una aplicación que utiliza ThreadX.

### <a name="increased-throughput"></a>Mayor capacidad de proceso

Una posible solución al problema del tiempo de respuesta del bucle de control es agregar más sondeos. Esto mejora la capacidad de respuesta, pero sigue sin garantizar un tiempo de respuesta constante en el peor caso y no hace nada para mejorar las modificaciones futuras de la aplicación. Además, ahora el procesador está llevando a cabo aún más procesamiento innecesario debido al sondeo adicional. Todo este procesamiento innecesario reduce la capacidad global de proceso del sistema.

Un punto interesante con respecto a la sobrecarga es que muchos desarrolladores suponen que los entornos multiproceso como ThreadX aumentan la sobrecarga y tienen un impacto negativo en la capacidad total de proceso del sistema. En algunos casos, sin embargo, el multithreading de hecho reduce la sobrecarga debido a la eliminación de todos los sondeos redundantes que se producen en entornos de bucle de control. La sobrecarga asociada a los kernels multiproceso suele ser una función del tiempo necesario para el cambio de contexto. Si el tiempo del cambio de contexto es menor que el proceso de sondeo, ThreadX proporciona una solución con el potencial de ofrecer menos sobrecarga y más capacidad de proceso. Esto hace que ThreadX sea una opción obvia para las aplicaciones con cualquier grado de complejidad o tamaño.

### <a name="processor-isolation"></a>Aislamiento del procesador

ThreadX proporciona una interfaz sólida e independiente del procesador entre la aplicación y el procesador subyacente. Esto permite que los desarrolladores se puedan concentrar en la aplicación, en lugar de dedicar una cantidad considerable de tiempo a conocer los detalles del hardware.

### <a name="dividing-the-application"></a>División de la aplicación

En las aplicaciones basadas en bucles de control, cada desarrollador debe tener un profundo conocimiento de los requisitos y el comportamiento en tiempo de ejecución de toda la aplicación. Esto se debe a que la lógica de asignación del procesador se dispersa por toda la aplicación. A medida que aumenta el tamaño o la complejidad de una aplicación, se hace cada vez más imposible que todos los desarrolladores recuerden los requisitos de procesamiento precisos de toda la aplicación.

ThreadX libera a cada desarrollador de las preocupaciones asociadas a la asignación del procesador y les permite concentrarse en su parte específica de la aplicación insertada. Además, ThreadX fuerza a la aplicación a dividirse en subprocesos claramente definidos. Esta división de la aplicación en subprocesos por sí sola ya hace que el desarrollo sea mucho más sencillo.

### <a name="ease-of-use"></a>Facilidad de uso

ThreadX se ha diseñado pensando en el desarrollador de aplicaciones. La arquitectura y la interfaz de llamada a los servicios de ThreadX están diseñadas para entenderse fácilmente. Como resultado, los desarrolladores de ThreadX pueden usar rápidamente sus características avanzadas.

### <a name="improve-time-to-market"></a>Mejor tiempo de comercialización

Todas las ventajas de ThreadX aceleran el proceso de desarrollo de software. ThreadX se encarga de la mayoría de los problemas de procesador y de las certificaciones de seguridad más comunes, eliminando esta labor de la programación de desarrollo. Todo esto se traduce en un tiempo de comercialización más rápido.

### <a name="protecting-the-software-investment"></a>Protección de la inversión en software

Debido a su arquitectura, ThreadX se distribuye fácilmente a nuevos entornos de procesador o de herramientas de desarrollo. Esto, junto con el hecho de que ThreadX aísla las aplicaciones de los detalles de los procesadores subyacentes, hace que las aplicaciones de ThreadX sean altamente portátiles. Como resultado, se garantiza la ruta de migración de la aplicación y se protege la inversión de desarrollo original.
