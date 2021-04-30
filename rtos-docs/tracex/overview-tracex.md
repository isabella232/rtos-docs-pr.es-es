---
title: Información general sobre Azure RTOS TraceX
description: Azure RTOS TraceX es la herramienta de análisis basada en host de Microsoft que proporciona a los desarrolladores una vista gráfica de los eventos del sistema en tiempo real y les permite visualizar y comprender mejor el comportamiento de sus sistemas en tiempo real.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 9fd33eec6da69e6dda421a125a2dde5eae93b46d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816470"
---
# <a name="overview-of-azure-rtos-tracex"></a>Información general sobre Azure RTOS TraceX

Azure RTOS TraceX es la herramienta de análisis basada en host de Microsoft que proporciona a los desarrolladores una vista gráfica de los eventos del sistema en tiempo real y les permite visualizar y comprender mejor el comportamiento de sus sistemas en tiempo real. Con Azure RTOS TraceX, los desarrolladores pueden ver claramente la aparición de eventos del sistema, como interrupciones y cambios de contexto, que se encuentran fuera de la vista de las herramientas de depuración estándar. La capacidad de detectar y estudiar estos eventos y de identificar el momento de su ocurrencia en el contexto de la operación del sistema global permite a los desarrolladores resolver problemas de programación buscando un comportamiento inesperado para permitirles investigar áreas específicas. La información de seguimiento se almacena en un búfer del sistema de destino, con la ubicación y el tamaño del búfer determinados por la aplicación en tiempo de ejecución. Azure RTOS TraceX puede procesar cualquier búfer construido de la manera adecuada, no solo desde Azure RTOS ThreadX, sino también desde cualquier aplicación o RTOS. La información de seguimiento se puede cargar en el host para analizarla en cualquier momento, ya sea al final o después de un punto de interrupción. Azure RTOS ThreadX implementa un búfer circular, que permite que los eventos "N" más recientes estén disponibles para su inspección en caso de que se produzca un error de funcionamiento del sistema u otro evento significativo.

![Pantalla Single-Core de Azure RTOS TraceX](./media/user-guide/screen_shot_33.png)

**Pantalla Single-Core de TraceX**

## <a name="key-capabilites"></a>Funcionalidades clave

### <a name="azure-rtos-tracex-built-in-system-analysis"></a>Análisis de sistema integrados de Azure RTOS TraceX

Azure RTOS TraceX proporciona informes de análisis de sistema integrados que están disponibles con un solo clic en la barra de herramientas de TraceX. Estos botones e informes incluyen los siguientes:

![Generar informe del perfil de ejecución](./media/overview-tracex/execution-profile-report-button.jpg) Generar informe del perfil de ejecución

![Generar informe de estadísticas de rendimiento](./media/overview-tracex/performance-statistics-report-button.jpg) Generar informe de estadísticas de rendimiento

![Generar informe de uso de la pila de subprocesos](./media/overview-tracex/thread-stack-usage-report-button.jpg) Generar informe de uso de la pila de subprocesos

### <a name="trace-data-collected-by-azure-rtos-threadx"></a>Datos de seguimiento recopilados por Azure RTOS ThreadX

Azure RTOS TraceX está diseñado para funcionar con Azure RTOS ThreadX, que construye una base de datos de "eventos" del sistema y de la aplicación en el sistema de destino durante el tiempo de ejecución. Estos eventos incluyen los siguientes:

* cambios de contexto de subprocesos
* prioridades
* suspensiones
* finalizaciones
* interrupciones del sistema
* eventos específicos de una aplicación
* todas las llamadas API de Azure RTOS ThreadX
* todas las llamadas API de Azure RTOS NetX
* todas las llamadas API de Azure RTOS FileX
* todas las llamadas API de Azure RTOS USBX
* iconos e información definidos por la aplicación

Los eventos se registran bajo el control del programa, con la marca de tiempo y la identificación de subprocesos activa, para que se puedan mostrar más adelante en la secuencia de tiempo adecuada, y asociados al subproceso adecuado. Es posible que el programa de aplicación detenga y reinicie el registro de eventos de forma dinámica, por ejemplo, cuando se encuentre un área de interés. Esto evita saturar la base de datos y usar la memoria de destino cuando el sistema funciona correctamente.

### <a name="azure-rtos-tracex-is-like-a-software-logic-analyzer"></a>Azure RTOS TraceX es como un analizador de lógica de software

Una vez que el registro de eventos se ha cargado desde la memoria de destino al host, Azure RTOS TraceX muestra los eventos gráficamente en un eje horizontal que representa el tiempo, con los distintos subprocesos de aplicación y rutinas del sistema con los que se relacionan los eventos que aparecen en el eje vertical. Azure RTOS TraceX crea un "analizador de lógica de software" en el host, lo que permite que los eventos del sistema sean visibles de forma sencilla. Los eventos se representan mediante iconos codificados por colores, ubicados en el punto de ocurrencia a lo largo de la escala de tiempo horizontal, a la derecha de la rutina de subproceso o sistema pertinente. Cuando se selecciona el icono de un evento, se muestra la información correspondiente para ese evento, así como la información de los dos eventos anteriores y posteriores. Esto proporciona acceso rápido con un solo clic a la información más inmediata sobre el evento y sus eventos conexos inmediatos. Azure RTOS TraceX proporciona una pantalla "Summary" (Resumen) que muestra todos los eventos del sistema en una sola línea horizontal para simplificar el análisis de sistemas con muchos subprocesos.

### <a name="sequential-view-mode"></a>Modo de vista secuencial

Para seleccionar el modo de vista secuencial, haga clic en la pestaña "Sequential View" (Vista secuencial). Este es el modo predeterminado. En este modo, los eventos se muestran inmediatamente unos detrás de otros, independientemente del tiempo transcurrido entre ellos. Tenga en cuenta también la regla que aparece encima del área de visualización. Muestra el número de evento relativo desde el principio del seguimiento. Este modo es el predeterminado y es especialmente útil para obtener información general apropiada sobre lo que ocurre en el sistema.

![Modo de vista secuencial](./media/user-guide/screen_shot_10.png)

**Modo de vista secuencial**

### <a name="time-view-mode"></a>Modo de vista de tiempo

En este modo, los eventos se muestran según el tiempo, con una barra verde sólida que se usa para representar la ejecución entre eventos. Este modo resulta especialmente útil para ver dónde se está llevando a cabo la mayor parte del procesamiento en el sistema, lo que puede ayudar a los desarrolladores a ajustar su sistema para obtener un mayor rendimiento o capacidad de respuesta.

Tenga en cuenta también la regla que aparece encima de la pantalla de eventos. Esta regla muestra los tics relativos desde el principio del seguimiento, como se derivan de la marca de tiempo instrumentada en el registro de seguimiento de eventos dentro de Azure RTOS ThreadX. Si las marcas de tiempo están demasiado próximas (temporizador de baja frecuencia), los eventos se ejecutarán juntos. Por el contrario, si las marcas de tiempo están demasiado alejadas (temporizador de alta frecuencia), los eventos estarán demasiado alejados. La elección de la marca de tiempo de frecuencia correcta es una consideración importante a la hora de hacer que la vista relativa al tiempo sea significativa.

![Modo de vista de tiempo](./media/user-guide/screen_shot_31.png)

### <a name="system-summary-line"></a>Línea de resumen del sistema

Azure RTOS TraceX también proporciona una sola línea de resumen que incluye todos los eventos en la misma línea. La línea de resumen contiene un resumen del contexto, y debajo aparece el resumen de evento correspondiente. Esto hace que resulte fácil ver información general de un sistema complejo. La barra de resumen resulta especialmente útil en los sistemas que tienen un gran número de subprocesos. Sin esta línea de resumen, el usuario tendría que seguir las interacciones complejas del sistema mediante la barra de desplazamiento vertical para seguir el contexto de ejecución.

Azure RTOS TraceX muestra los contextos del sistema en el lado izquierdo de la pantalla.
Los eventos que se producen en un contexto determinado se muestran en la línea horizontal a la derecha de ese contexto. De esta manera, el usuario puede determinar fácilmente el contexto en el que se produjo el evento y seguir esa línea de contexto para ver todos los eventos que se produjeron en un contexto determinado.

![Línea de resumen del sistema](./media/user-guide/screen_shot_32.png)

**Línea de resumen del sistema**

Las dos primeras entradas de contexto siempre se corresponden con los contextos de "interrupción" e "inicialización/inactividad". El contexto de "interrupción" representa todos los eventos del sistema ocurridos a partir de rutinas de servicio de interrupción (ISR). El contexto de "inicialización/inactividad" representa dos contextos en Azure RTOS ThreadX. Los eventos que se producen durante tx_application_define son eventos de "inicialización" y se muestran en el contexto de "inicialización/inactividad". Si el sistema está inactivo y, por lo tanto, no se produce ningún evento, la barra verde que representa "en ejecución" en la vista de tiempo se dibuja en el contexto de "inicialización/inactividad".

## <a name="methods-of-navigation"></a>Métodos de navegación

Azure RTOS TraceX permite al desarrollador especificar cómo funcionan los botones de navegación "Siguiente" y "Anterior".

![Botones de navegación](./media/user-guide/event.png)

Si se selecciona "Event" (Evento), la navegación se realiza en el evento siguiente o anterior. Si se selecciona "Context" (Contexto), la navegación se realiza en el evento siguiente o anterior en el mismo contexto. Si se selecciona "Object" (Objeto), la navegación se realiza en el evento siguiente o anterior del objeto actual, por ejemplo, los eventos asociados a una cola específica. Si se selecciona "Switches" (Modificadores), la navegación se realiza en el modificador de contexto siguiente o anterior. Si se selecciona "Same ID" (Mismo id.), la navegación se realiza en el evento siguiente o anterior para el mismo identificador de evento.

### <a name="event-information-display"></a>Pantalla de información de eventos

Azure RTOS TraceX proporciona información detallada sobre unos 300 eventos. Entre ellos se incluyen seis eventos internos de Azure RTOS ThreadX, dos eventos de ISR (entrar y salir), 14 eventos internos de Azure RTOS FileX, 42 eventos internos de Azure RTOS NetX y un evento definido por el usuario. Los demás eventos se corresponden directamente con los servicios de API de Azure RTOS ThreadX, Azure RTOS FileX y Azure RTOS NetX.
Independientemente de que el modo de presentación secuencial o de tiempo esté seleccionado, al pasar el mouse sobre cualquier evento en el área de visualización se muestra información sobre el evento cerca del evento. A continuación, se muestra lo que aparece al pasar el mouse por el evento 494 en el archivo de seguimiento demo_threadx.trx de la demostración:

![Más información al pasar el mouse](./media/user-guide/screen_shot_37.png)

**Más información al pasar el mouse**

Cada evento mostrado contiene información estándar sobre el contexto y la marca de tiempo y la hora correspondientes. El campo de contexto muestra el contexto en el que tuvo lugar el evento. Hay exactamente cuatro contextos: subproceso, inactividad, ISR e inicialización. Cuando un evento tiene lugar en un contexto de subproceso, el nombre del subproceso y su prioridad en ese momento se recopilan y se muestran como se representó anteriormente. La hora relativa muestra el número relativo de tics del temporizador desde el principio del seguimiento. La marca de tiempo sin formato muestra el origen de hora sin formato del evento. Por último, se muestra toda la información específica del evento.

### <a name="zooming-in-and-out"></a>Acercar y alejar

De forma predeterminada, Azure RTOS TraceX muestra los eventos en un tamaño fácil de ver, con una asignación de píxel:tic 1:1. El usuario puede acercar o alejar según sea necesario. Alejar hasta el 100 % es útil para ver el seguimiento completo en la vista de presentación actual, mientras que acercar es útil en condiciones donde los eventos se superponen debido a la resolución del origen de la marca de tiempo.

![Alejar hasta el 100 % para visualizar o acercar para consultar los detalles](./media/user-guide/screen_shot_41.png)

**Alejar hasta el 100 % para visualizar o acercar para consultar los detalles**

Al alejar hasta el 100 %, para mostrar el seguimiento completo dentro de la página de presentación actual, es fácil ver toda la ejecución de contexto capturada en el seguimiento, así como los eventos generales que se producen dentro de esos contextos. Tenga en cuenta que "thread 1" (subproceso 1) y "thread 2" (subproceso 2) se ejecutan con más frecuencia. El color azul de sus eventos también sugiere que estos subprocesos realizan llamadas a Queue service (los eventos de cola son de color azul).

La restauración a una vista de iconos completa es igual de fácil. Es posible seleccionar varias veces el botón de acercar o se puede escribir algún factor de 100.

### <a name="delta-ticks-between-events"></a>Tics delta entre eventos

Determinar el número de tics entre varios eventos en Azure RTOS TraceX es fácil: simplemente haga clic en el evento de inicio y arrastre el mouse hasta el evento final.
El número delta de tics entre los eventos se mostrará en la esquina superior derecha de la pantalla.

![Tics delta](./media/user-guide/screen_shot_42.png)

**Tics delta**

Las tics delta muestran que han transcurrido 5032 tics entre los eventos 494 y 496. Esto también se puede calcular manualmente; para ello, se deben examinar las marcas de tiempo relativas de cada evento y restarlas, pero el uso de la GUI es fácil e instantáneo.

### <a name="priority-inversions"></a>Inversiones de prioridades

Azure RTOS TraceX muestra automáticamente las inversiones de prioridades detectadas en el archivo de seguimiento. Las inversiones de prioridades se definen como condiciones en las que se bloquea un subproceso de prioridad superior intentando obtener una exclusión mutua que actualmente es propiedad de un subproceso de prioridad más baja. Esta condición se denomina "determinista", ya que el sistema se configuró para funcionar de esta manera. Con el fin de informar al usuario, Azure RTOS TraceX muestra intervalos de inversión de prioridades "deterministas" con un color salmón claro.

Azure RTOS TraceX también muestra las inversiones de prioridades "no deterministas". Estas inversiones de prioridades difieren de las inversiones de prioridades "deterministas" en que otro subproceso de un nivel de prioridad diferente se ha ejecutado en el medio de la inversión de prioridades "determinista", lo que hace que el tiempo dentro de la inversión de prioridades sea algo "no determinista". El usuario suele desconocer esta condición, y puede ser muy grave. Para alertar al usuario de esta condición, Azure RTOS TraceX muestra las inversiones de prioridades "no deterministas" con un color salmón más vivo.

![Inversión de prioridades determinista y no determinista](./media/user-guide/screen_shot_43.png)

**Inversión de prioridades determinista y no determinista**

### <a name="execution-profile"></a>Perfil de ejecución

Azure RTOS TraceX proporciona un informe de perfil de ejecución integrado para todos los contextos de ejecución dentro del archivo de seguimiento cargado actualmente.

![Perfil de ejecución](./media/user-guide/execution_profile.png)

### <a name="performance-statistics"></a>Performance statistics

Azure RTOS TraceX proporciona un informe de estadísticas de rendimiento integrado para el archivo de seguimiento cargado actualmente.

![Performance statistics](./media/user-guide/performance_statistics.png)

### <a name="thread-stack-usage"></a>Uso de la pila de subprocesos

Azure RTOS TraceX proporciona un informe de uso de pila integrado para todos los subprocesos que se ejecutan dentro del archivo de seguimiento cargado actualmente.

![Uso de la pila](./media/user-guide/thread_stack_usage.png)

Azure RTOS TraceX presenta las estadísticas de rendimiento de Azure RTOS FileX del archivo de seguimiento cargado actualmente. Esta información se muestra para todo el sistema: en todos los objetos multimedia abiertos.

![Estadísticas de FileX](./media/user-guide/filex_statistics.png)

### <a name="azure-rtos-netx-statistics"></a>Estadísticas de Azure RTOS NetX

Azure RTOS TraceX también presenta las estadísticas de rendimiento de NetX del archivo de seguimiento cargado actualmente. Esta información se muestra para todo el sistema.

![Estadísticas de NetX](./media/user-guide/netx_statistics.png)

### <a name="raw-trace-dump"></a>Volcado de seguimiento sin procesar

Azure RTOS TraceX puede generar un archivo de seguimiento sin procesar en formato de texto e iniciar el Bloc de notas para mostrarlo.

![Volcado de seguimiento sin procesar](./media/user-guide/raw_trace_dump.png)

Tenga en cuenta que todas las cifras de tiempos y tamaños enumeradas son estimaciones y pueden ser diferentes en su plataforma de desarrollo.
