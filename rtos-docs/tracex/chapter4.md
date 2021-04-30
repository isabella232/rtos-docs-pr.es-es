---
title: 'Capítulo 4: Análisis de rendimiento de Azure RTOS TraceX'
description: En este capítulo se describe la herramienta de análisis de rendimiento de Azure RTOS TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 6cf1b5bd5349efd97c3afc8a9e7f57f477f06f8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815745"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a>Capítulo 4: Análisis de rendimiento de Azure RTOS TraceX

En este capítulo se describe la herramienta de análisis de rendimiento de Azure RTOS TraceX:

## <a name="performance-analysis"></a>Análisis de rendimiento

TraceX proporciona un análisis de rendimiento integrado de los archivos de seguimiento. Se puede acceder fácilmente a la información, como el *perfil de ejecución*, los *servicios populares*, el *uso de la pila de subprocesos* y diversas *estadísticas de rendimiento*, incluidas las estadísticas de FileX y NetX *,* . Esta información está disponible en el elemento de menú ***Ver***. 


## <a name="execution-profile"></a>Perfil de ejecución

Al seleccionar el botón ***Generate Execution Profile** _ (Generar perfil de ejecución) o _*_View -Execution Profile_*_ (Ver - Perfil de ejecución), se presenta el perfil de ejecución de TraceX para el archivo de seguimiento cargado actualmente. El perfil de ejecución asociado al seguimiento de la demostración de ThreadX de ejemplo se muestra en la _* figura 19**.

![Captura de pantalla del perfil de ejecución asociado al seguimiento de la demostración de ThreadX de ejemplo.](./media/user-guide/execution_profile.png)

**FIGURA 19**

El ejemplo que se muestra en la **figura 19** indica que casi el 45 % del tiempo de procesamiento transcurre dentro de **_thread 2_ *_ (subproceso 2) y casi el 51 % del tiempo de procesamiento transcurre dentro de _* _thread 1_** (subproceso 1). Esto es lógico, ya que la mayor parte del seguimiento muestra que estos subprocesos envían y reciben mensajes. En los demás contextos de ejecución transcurre solo una pequeña parte del tiempo de ejecución en este ejemplo.

## <a name="popular-services"></a>Servicios populares

Al seleccionar ***View ->Popular Services** _ (Ver->Servicios populares) se presentan los servicios populares del archivo de seguimiento cargado actualmente. De forma predeterminada, esta información se muestra para todo el sistema. Sin embargo, también están disponibles los servicios populares para subprocesos específicos. Los servicios populares del seguimiento de demostración de ThreadX de ejemplo se muestran en la _*figura 20**.

![Captura de pantalla de los servicios populares en el seguimiento de demostración de ThreadX de ejemplo.](./media/user-guide/popular_services.png)

**FIGURA 20**

El ejemplo que se muestra en la **figura 20** indica que **_tx_queue_send_ *_ y _* _tx_queue_receive_** son los dos servicios más populares de este seguimiento. Esto es coherente con el comportamiento de la demostración de ThreadX estándar en la que se capturó este seguimiento.

Los subprocesos específicos se pueden seleccionar para este análisis mediante la lista desplegable de selección de la parte superior de esta ventana. En la **figura 21** se muestra este análisis para **_thread 3_** (subproceso 3).

![Captura de pantalla del análisis de los servicios populares de TraceX](./media/user-guide/popular_services_thread3.png)

**FIGURA 21**

## <a name="thread-stack-usage-analysis-for-thread-3"></a>Uso de la pila de subprocesos ![Análisis del subproceso 3.](./media/user-guide/screen_shot_17.png)

Al seleccionar el botón ***Generate Thread Stack Usage** _ (Generar uso de la pila de subprocesos) o _*_View -> Thread Stack Usage_*_ (Ver -> Uso de la pila de subprocesos), se muestra el uso de la pila para cada subproceso del archivo de seguimiento. Esto se logra mediante ThreadX, incluido el puntero de la pila de subprocesos actual en muchas de las entradas de seguimiento del archivo. Un uso de la pila del 100 % indica que la pila se ha desbordado y que debe corregirse en la aplicación. Si no hay ninguna ejecución de subprocesos dentro de este archivo de seguimiento, el uso de la pila de ese subproceso se muestra como 0 %. El uso de la pila de subprocesos del seguimiento de demostración de ThreadX de ejemplo se muestra en la _*figura 22**.

![Captura de pantalla del uso de la pila de subprocesos de TraceX](./media/user-guide/thread_stack_usage.png)

**FIGURA 22**

El ejemplo que se muestra en la **figura 22** indica que la mayoría de los subprocesos de este seguimiento consumen un uso de la pila de entre el 9 % y el 12 %.

## <a name="performance-statistics"></a>Estadísticas de rendimiento

Al seleccionar el botón **Generate Performance Statistics** _ (Generar estadísticas de rendimiento) o _ *_View -> Performance Statistics_** (Ver -> Estadísticas de rendimiento), se muestran las estadísticas de rendimiento del archivo de seguimiento cargado actualmente. De forma predeterminada, esta información se muestra para todo el sistema. Sin embargo, las estadísticas de rendimiento también están disponibles para cada subproceso específico.

Las estadísticas de rendimiento del seguimiento de demostración de ThreadX de ejemplo se muestran en la **figura 23**.

![Captura de pantalla de las estadísticas de rendimiento de TraceX](./media/user-guide/performance_statistics.png)

**FIGURA 23**

El ejemplo que se muestra en la **figura 23** indica que había 18 cambios de contexto en este archivo de seguimiento, así como 5 adelantamientos de subproceso, 16 suspensiones de subprocesos, 19 reanudaciones de subprocesos y 3 interrupciones. No se encontraron inversiones de prioridades en este archivo de seguimiento. Observe que hay dos categorías de inversiones de prioridades, es decir, *deterministas* y *no deterministas*. Las inversiones de prioridades deterministas son aquellas en las que un subproceso se bloquea en una exclusión mutua que es propiedad de un subproceso de prioridad más baja. Una inversión de prioridad no determinista es donde se ejecuta un subproceso de prioridad más baja diferente durante una inversión de prioridad determinista. Esta última puede provocar un comportamiento de temporización imprevisto en la aplicación y debe estudiarse detenidamente.

## <a name="filex-statistics"></a>Estadísticas de FileX

Al seleccionar ***View -> FileX Statistics** _ (Ver -> Estadísticas de FileX), se muestran las estadísticas de rendimiento de FileX del archivo de seguimiento cargado actualmente. Esta información se muestra para todo el sistema, en todos los objetos ../media abiertos. Las estadísticas de rendimiento del seguimiento de demostración de FileX de ejemplo se muestran en la _*figura 24**.

![Captura de pantalla de las estadísticas de FileX](./media/user-guide/filex_statistics.png)

**FIGURA 24**

El ejemplo que se muestra en la **figura 27** indica que había 19 elementos ../media abiertos, 19 elementos ../media cerrados, 19 elementos ../media vacíos, 18 lecturas de directorio, 19 escrituras de directorio y 18 errores en la caché del directorio. Para consultar información adicional, desplácese hacia abajo en la ventana de estadísticas.

## <a name="netx-statistics"></a>Estadísticas de NetX

Al seleccionar ***View -> NetX Statistics** _ (Ver -> Estadísticas de NetX), se muestran las estadísticas de rendimiento de NetX del archivo de seguimiento cargado actualmente. Esta información se muestra para todo el sistema. Las estadísticas de rendimiento del seguimiento de demostración de NetX de ejemplo se muestran en la _*figura 25**.

![Captura de pantalla de las estadísticas de NetX](./media/user-guide/netx_statistics.png)

**FIGURA 25**

El ejemplo que se muestra en la **figura 25** indica que no había eventos ARP, ping o UDP, pero que había 30 paquetes de IP enviados, 1368 bytes de IP enviados, 30 paquetes de IP recibidos y 1360 bytes de IP recibidos.

## <a name="trace-file-information"></a>Información del archivo de seguimiento

Al seleccionar ***View -> Trace File Information** _ (Ver -> Información del archivo de seguimiento), se muestra información básica sobre el archivo de seguimiento abierto. Esta información incluye el orden de bytes del archivo, el tamaño del origen de la hora, el número máximo de bytes para cada nombre de objeto y la dirección base de todos los punteros del archivo de seguimiento. En la _ *figura 26** se muestra la información del archivo de seguimiento estándar **_demo_threadx.trx_**.

![Captura de pantalla de la información del archivo de TraceX](./media/user-guide/trace_file_info.png)

**FIGURA 26**

## <a name="raw-trace-dump"></a>Volcado de seguimiento sin procesar

Al seleccionar ***View -> Raw Trace Dump** _ (Ver -> Volcado de seguimiento sin procesar), se presenta un cuadro de diálogo para asignar un nombre al archivo que contiene el volcado de seguimiento sin procesar. Después de escribir el nombre de archivo y la ruta de acceso, TraceX crea el archivo de seguimiento sin procesar en formato de texto e inicia _*_notepad.exe_*_ para mostrarlo. En la _ *figura 27** se muestra el volcado del archivo de seguimiento sin procesar del archivo de seguimiento estándar **_demo_threadx.trx_**.

![Captura de pantalla del volcado de seguimiento sin procesar](./media/user-guide/raw_trace_dump.png)

**FIGURA 27**
