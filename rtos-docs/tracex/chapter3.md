---
title: 'Capítulo 3: Descripción de TraceX de Azure RTOS'
description: En este capítulo se describe la funcionalidad general de la herramienta de análisis del sistema TraceX de Azure RTOS, incluida la funcionalidad general de su interfaz gráfica de usuario.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1c974b353c92e0a3cf51c92818794197cf999582
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815802"
---
# <a name="chapter-3---description-of-azure-rtos-tracex"></a>Capítulo 3: Descripción de TraceX de Azure RTOS

En este capítulo se describe la funcionalidad general de la herramienta de análisis del sistema TraceX de Azure RTOS, incluida la funcionalidad general de su interfaz gráfica de usuario. 

## <a name="display-overview"></a>Introducción a las presentaciones

En la **figura 4** se muestra la ventana de presentación principal de la herramienta de análisis del sistema TraceX. El diseño es sencillo: los contextos de ejecución se representan mediante los elementos verticales en el lado izquierdo; por ejemplo, inicialización, interrupción, inactividad y las distintas entradas de subproceso. Los eventos que tienen lugar en cada contexto se muestran horizontalmente en la misma línea de contexto. Por ejemplo, los eventos de **QR** que aparecen a continuación muestran que el **_subproceso 2_*está realizando llamadas sucesivas a*_tx_queue_receive_**.

![Captura de pantalla de la ventana de presentación principal de la herramienta de análisis del sistema TraceX.](./media/user-guide/screen_shot_10.png)


**FIGURA 5**

Los cambios de contexto se representan mediante las líneas negras verticales que conectan las líneas de contexto. El evento seleccionado actualmente se representa con una línea vertical roja continua. En este ejemplo, se selecciona el evento 494.

## <a name="title-bar"></a>Barra de título

La barra de título de TraceX proporciona varios fragmentos de información útil. El primero es la versión actual de TraceX. El segundo es la ruta de acceso completa del archivo de seguimiento actualmente abierto. En el ejemplo de la **figura 6** se muestra  **_TraceX_ *, versión* _6.0.0_ *, con el archivo de seguimiento* _demo_threadx.trx_**.

![Captura de pantalla de la barra de título de TraceX.](./media/user-guide/screen_shot_11.png)

**FIGURA 6**

## <a name="tool-bar"></a>Tool Bar

La barra de herramientas de TraceX proporciona varios botones para abrir los archivos de seguimiento y los elementos de control de su presentación.

![Captura de pantalla de la barra de herramientas de TraceX.](./media/user-guide/screen_shot_12.png)


**FIGURA 7**

Los botones de la barra de herramientas de TraceX, de izquierda a derecha, se definen de la siguiente manera:
                                             
| **Botón**                         | **Function** |
| ---------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![Botón para abrir archivo de seguimiento](./media/user-guide/screen_shot_13.png)      | Abrir un archivo de seguimiento |
| ![Botón para abrir una guía de usuario](./media/user-guide/screen_shot_14.png)      | Abrir esta guía de usuario |
| ![Botón para generar informe del perfil de ejecución](./media/user-guide/screen_shot_15.png)       | Generar informe del perfil de ejecución |
| ![ Botón para generar estadísticas de rendimiento](./media/user-guide/screen_shot_16.png)       | Generar estadísticas de rendimiento |
| ![Botón para generar el uso de la pila de subprocesos](./media/user-guide/screen_shot_17.png)       | Generar uso de la pila de subprocesos |
| ![Botón para mostrar el evento seleccionado](./media/user-guide/screen_shot_18.png)       | Mostrar evento seleccionado actualmente |
| ![Botón Buscar](./media/user-guide/screen_shot_19.png)      | Buscar eventos |
| ![Botón para acercar](./media/user-guide/screen_shot_20.png)      | Acercar |
| ![Botón para mostrar zoom](./media/user-guide/screen_shot_21.png)      | Seleccione el porcentaje de zoom de la presentación, donde 100 % significa que el archivo de seguimiento completo se muestra en la vista actual. |
| ![Botón para alejar](./media/user-guide/screen_shot_22.png)      | Alejar |
| ![Botón para seleccionar el primer evento](./media/user-guide/screen_shot_23.png)      | Seleccionar el primer evento |
| ![Botón para mostrar la página de evento anterior](./media/user-guide/screen_shot_24.png)      | Mostrar página de evento anterior |
| ![Botón para mostrar el evento anterior](./media/user-guide/screen_shot_25.png)      | Mostrar evento anterior |
| ![Botón de navegación siguiente/anterior](./media/user-guide/screen_shot_26.png)      | Determine el funcionamiento de los botones de navegación siguiente o anterior. Si se selecciona **Event** (Evento), la navegación se realiza en el evento siguiente o anterior. Si se selecciona _*_Context_*_ (Contexto), la navegación se realiza en el evento siguiente o anterior en el contexto especificado. Si se selecciona _*_Object_*_ (Objeto), la navegación se realiza en el evento siguiente o anterior del objeto especificado, por ejemplo, los eventos asociados a una cola específica. Si se selecciona _*_Switches_*_ (Modificadores), la navegación se realiza en el cambio de contexto siguiente o anterior. Si se selecciona *_ID_* (Id.), la navegación se realiza en el evento siguiente o anterior del identificador de evento especificado. |
| ![Botón para mostrar el evento siguiente](./media/user-guide/screen_shot_27.png)      | Mostrar evento siguiente |
| ![Botón para mostrar la página de evento siguiente](./media/user-guide/screen_shot_28.png)      | Mostrar página de evento siguiente |
| ![Botón para seleccionar el último evento](./media/user-guide/screen_shot_29.png)      | Seleccionar último evento |

## <a name="display-mode-tabs"></a>Pestañas del modo de presentación

TraceX muestra los eventos del sistema de dos maneras diferentes: *secuencial* y *relativos al tiempo*. El modo predeterminado es secuencial y es el modo que se muestra en la **figura 8**.

Cambiar de modo es tan sencillo como seleccionar las pestañas ***Sequential View** (Vista secuencial) o _*_Time View_*_ (Vista de tiempo) en la ventana de TraceX. La _*figura 8* muestra las pestañas *_Sequential View_*_ (Vista secuencial) y *_Time View_* (Vista de tiempo).

![Captura de pantalla de las pestañas Sequential View (Vista secuencial) y Time View (Vista de tiempo).](./media/user-guide/screen_shot_30.png)

**FIGURA 8**

## <a name="sequential-view-mode"></a>Modo de vista secuencial

El modo de vista secuencial se selecciona mediante la pestaña **Sequential View** (Vista secuencial) que se muestra en la figura 8. Este es el modo predeterminado. En este modo, los eventos se muestran inmediatamente unos detrás de otros, con independencia del tiempo transcurrido entre ellos. Tenga en cuenta también la regla que aparece encima del área de presentación de la **figura 8**. Muestra el número de eventos relativo desde el principio del seguimiento.

Este modo es el predeterminado y es especialmente útil para obtener una buena visión general sobre lo que ocurre en el sistema.

## <a name="time-view-mode"></a>Modo de vista de tiempo

El modo de vista de tiempo se selecciona con el botón ***Time View** (Vista de tiempo). En la *figura 9* se muestra el mismo seguimiento de eventos que en la **figura 8**, excepto en el modo de vista de tiempo. En este modo, los eventos se muestran relativos al tiempo, con una barra verde continua que se usa para representar la ejecución entre eventos. Este modo resulta especialmente útil para ver dónde se está llevando a cabo la mayor parte del procesamiento en el sistema, lo que puede ayudar a los desarrolladores a ajustar su sistema para obtener un mayor rendimiento o capacidad de respuesta.

![Captura de pantalla de la pestaña Time View (Vista de tiempo).](./media/user-guide/screen_shot_31.png)

**FIGURA 9**

Tenga en cuenta también la regla que aparece encima de la presentación de eventos de la **figura 9**. Esta regla muestra los tics relativos desde el principio del seguimiento, según se derivan de la marca de tiempo instrumentada en el registro de seguimiento de eventos dentro de TraceX. Si las marcas de tiempo están demasiado próximas (temporizador de baja frecuencia), los eventos se ejecutarán juntos. Por el contrario, si las marcas de tiempo están demasiado alejadas (temporizador de alta frecuencia), los eventos estarán demasiado alejados. La elección de la marca de tiempo de frecuencia correcta es una consideración importante a la hora de hacer que la vista relativa al tiempo sea significativa.

## <a name="system-summary-line"></a>Línea de resumen del sistema

TraceX también proporciona una sola línea de resumen (el contexto superior de la **figura 10**) que incluye todos los eventos en la misma línea. Esto hace que resulte fácil tener una visión general de un sistema complejo. La barra de resumen resulta especialmente útil en los sistemas que tienen un gran número de subprocesos. Sin esta línea de resumen, tendría que seguir las interacciones complejas del sistema mediante la barra de desplazamiento vertical para seguir el contexto de ejecución.

![Captura de pantalla de las pestañas Sequential View (Vista secuencial) y Time View (Vista de tiempo).](./media/user-guide/screen_shot_32.png)


**FIGURA 10**

La línea de resumen contiene un resumen del contexto, y debajo aparece el resumen de eventos correspondiente. En el ejemplo que se muestra en la **figura 10**, es fácil ver que el **_subproceso 2_*se está ejecutando y se ha interrumpido. La interrupción da como resultado el adelantamiento por parte del*_subproceso 3_**, ***subproceso 6**, _*_subproceso 4_*_ y _*_subproceso 7_*_ , después del cual el *_subproceso 2_* * reanuda la ejecución.

## <a name="system-contexts"></a>Contextos del sistema

TraceX muestra los contextos del sistema en el lado izquierdo de la pantalla, como se ilustra en la **figura 11**. Los eventos que se producen en un contexto determinado se muestran en la línea horizontal a la derecha de ese contexto. De esta manera, puede determinar fácilmente el contexto en el que se produjo el evento y seguir esa línea de contexto para ver todos los eventos que se produjeron en un contexto determinado.

Las dos primeras entradas de contexto siempre se corresponden con los contextos de **interrupción** e _*_inicialización o inactividad_*_. El contexto de _*_interrupción_*_ representa todos los eventos del sistema ocurridos a partir de rutinas de servicio de interrupción (IRS). El contexto de _*_inicialización o inactividad_*_ representa dos contextos en TraceX. Los eventos que se producen durante _*_tx_application_define_*_ son el contexto de _*_inicialización o inactividad_*_. Si el sistema está inactivo y, por lo tanto, no se produce ningún evento, la barra verde que representa el estado _*_en ejecución_*_ en la vista de tiempo se dibuja en el contexto de *_inicialización o inactividad_**.

![Captura de pantalla de los contextos del sistema en el lado izquierdo de la pantalla.](./media/user-guide/screen_shot_33.png)

**FIGURA 11**

En el ejemplo de la **figura 11**, hay nueve contextos de subproceso, empezando por el contexto de **_subproceso del temporizador del sistema_ *. Si necesita más información sobre un contexto, sitúe el mouse sobre él. La información adicional incluye la dirección de pila inicial del subproceso, la dirección de pila final, el tamaño total, el porcentaje usado, el porcentaje de ejecución relativa, el número de suspensiones, las reanudaciones y su prioridad máxima y mínima durante el seguimiento. La* figura 12** muestra información del **_subproceso 0_**.

![Captura de pantalla de la información del subproceso 0.](./media/user-guide/screen_shot_34.png)


**FIGURA 12**

Los contextos también se pueden mover al grupo de mayor interés. Para ello, se arrastra y coloca el contexto o se hace clic con el botón derecho en él. Al hacer clic con el botón derecho en el contexto, se genera un cuadro de diálogo para mover el contexto arriba o abajo. 

Al seleccionar ***Move to top** (Mover al principio), el contexto del _*_subproceso 3_*_ se mueve arriba de la lista de contextos, como se muestra en la figura 13.

![Captura de pantalla del contexto que se mueve arriba de la lista de contextos.](./media/user-guide/screen_shot_35.png)


**FIGURA 13**

## <a name="thread-status-information"></a>Información de estado del subproceso

Cuando está habilitada esta opción, TraceX muestra el estado de cada subproceso mediante una línea de color en el contexto del subproceso. Una línea verde indica que el subproceso está en estado "listo", mientras que una línea de cualquier otro color indica que el subproceso está suspendido. En el caso de los subprocesos suspendidos, el color de la línea indica el tipo de objeto de TraceX en el que se suspende el subproceso. Por ejemplo, en la **figura 13**, la línea verde del contexto del **_subproceso de temporizador del sistema_ *, que empieza en el evento 147, muestra que el* _subproceso de temporizador del sistema_*está listo. Antes del evento 147 y después del evento 154, la ausencia de la línea verde indica que el*_subproceso de temporizador del sistema_*está listo. Antes del evento 147 y después del evento 154, la ausencia de la línea verde indica que el*_subproceso del temporizador del sistema_** está suspendido.

![Captura de pantalla del estado de cada subproceso con una línea de color en el contexto del subproceso.](./media/user-guide/screen_shot_36.png)

**FIGURA 14**

Hay tres modos de presentación del estado del subproceso, disponibles a través del menú **Options -> Status Lines** (Opciones > Líneas de estado). La opción _*_Ready Only_*_ (Solo preparado) únicamente muestra las líneas con estado preparado (verdes), pero no muestra ninguna línea con estado de suspensión. Esta es la opción predeterminada en TraceX. La opción *_All On_** (Todo activado) permite la presentación de todas las líneas de estado (preparadas y en suspensión).

Por último, la opción ***All Off*** (Todo desactivado) deshabilita la presentación de todas las líneas de estado.

## <a name="event-information-display"></a>Presentación de la información de eventos

TraceX proporciona información detallada sobre unos 600 eventos en tiempo de ejecución, como llamadas a la API de ThreadX, FileX, NetX, NetX Duo y USBX y eventos internos. TraceX también admite hasta 61 439 eventos adicionales únicos definidos por el usuario.

Con independencia de que se seleccione el modo de vista secuencial o de tiempo, al pasar el mouse sobre cualquier evento en el área de presentación se muestra información detallada sobre él. En la figura 15 se muestra la acción de pasar el mouse por el evento 143 en el archivo de seguimiento **demo_threadx.trx** de la demostración:

![Captura de pantalla de la acción de pasar el mouse sobre el evento 143 en un archivo de seguimiento de ejemplo](./media/user-guide/screen_shot_37.png)

**FIGURA 15**

Cada evento mostrado contiene información estándar sobre el **contexto**, así como el _*_tiempo relativo_*_ y la _*_marca de tiempo_*_. El campo de contexto muestra el contexto en el que tuvo lugar el evento. Hay exactamente cuatro contextos: subproceso, inactividad, ISR e inicialización. Cuando un evento tiene lugar en un contexto de subproceso, el nombre del subproceso y su prioridad en ese momento se recopilan y se muestran como se mostró anteriormente. El _*_tiempo relativo_*_ muestra el número relativo de tics del temporizador desde el principio del seguimiento. La *_marca de tiempo sin formato_* muestra el origen de tiempo sin formato del evento. Por último, se muestra toda la información específica del evento. Esta información se detalla en el resto de este capítulo.

La información detallada del evento también está disponible al hacer doble clic en cualquier evento. En la **figura 16** se muestra la acción de hacer doble clic en el evento 143:

![Captura de pantalla de la información detallada del evento cuando se hace doble clic en un evento.](./media/user-guide/screen_shot_38.png)

**FIGURA 16**

La posibilidad de ver varios eventos a la vez ofrece al usuario una vista mucho más completa de lo que ha sucedido. Verlos en paralelo es bastante útil porque muchos eventos están interrelacionados. Esto se consigue haciendo doble clic en varios eventos.

## <a name="current-event-display"></a>Presentación del evento actual

TraceX muestra el evento actual, en una ventana aparte, cuando el usuario lo selecciona mediante ***View -> Current Event*** (Ver > Evento actual) o al hacer clic en el botón de evento actual de la barra de herramientas. A continuación, TraceX muestra el evento seleccionado actualmente en una ventana independiente y actualiza esta ventana cada vez que se selecciona otro evento.

## <a name="event-searching"></a>Búsqueda de eventos

TraceX proporciona una extensa funcionalidad de búsqueda de eventos. Los campos de identificador de evento e información de cada evento son los principales parámetros de búsqueda. No especificar un valor para un parámetro de búsqueda indica que el parámetro quita realmente ese parámetro de la búsqueda. Además, se puede realizar la búsqueda de modo que los parámetros que se encuentren la satisfagan o que se tengan que encontrar todos los parámetros para satisfacerla. La búsqueda también se puede restringir a un contexto determinado o abarcar todos los contextos del seguimiento. La invocación de la búsqueda de eventos se realiza seleccionando el botón **Search by Value** (Buscar por valor) en la barra de herramientas, como se muestra en la _figura 17. Cuando se selecciona, se muestra el cuadro de diálogo de búsqueda, que especifica todos los parámetros de la búsqueda. Los botones **_Next_*_  (Siguiente) y _*_Previous_*_ (Anterior) del cuadro de diálogo de búsqueda se pueden usar para buscar los eventos siguiente y anterior que coinciden con los criterios de búsqueda especificados. La *figura 17* muestra el cuadro de diálogo de búsqueda.

![Captura de pantalla de la búsqueda de eventos.](./media/user-guide/screen_shot_39.png)

**FIGURA 17**

![Captura de pantalla del cuadro de diálogo de eventos.](./media/user-guide/screen_shot_40.png)

**FIGURA 18**

## <a name="zooming-in-and-out"></a>Acercar y alejar

De forma predeterminada, TraceX muestra los eventos a tamaño completo. El usuario puede acercarlos o alejarlos según sea necesario. Alejar es útil para ver los eventos globales capturados en el seguimiento, mientras que acercar resulta conveniente en condiciones en las que los eventos se superponen debido a la resolución del origen de la marca de tiempo. En la **figura 19** se ilustra el archivo **_demo_threadx.trx_** alejado para mostrar el 100 % del archivo de seguimiento.

![Captura de pantalla de un archivo de ejemplo alejado para mostrar el 100 % del archivo de seguimiento.](./media/user-guide/screen_shot_41.png)

**FIGURA 19**

Al alejar hasta el 100 % para mostrar el seguimiento completo dentro de la página de presentación actual, es fácil ver toda la ejecución de contexto capturada en el seguimiento, así como los eventos generales que se producen dentro de esos contextos. Observe que en la **figura 16** el **_subproceso 1_*y el*_subproceso 2_** se ejecutan más a menudo. El color azul de sus eventos también sugiere que estos subprocesos realizan llamadas al servicio Queue (los eventos de cola son de color azul).

La restauración a una vista de iconos completa es igual de fácil. Es posible seleccionar varias veces el botón de acercar o se puede escribir algún factor de 100.

## <a name="delta-ticks-between-events"></a>Tics diferenciales entre eventos

Determinar el número de tics entre varios eventos en TraceX es fácil: simplemente haga clic en el evento de inicio y arrastre el mouse hasta el evento de fin. El número diferencial de tics entre los eventos se muestra en la esquina superior derecha de la pantalla, como ilustra la **figura 17**.

![Captura de pantalla del número diferencial de tics entre los eventos.](./media/user-guide/screen_shot_42.png)

**FIGURA 17**

Las tics diferenciales que se ilustran en la **figura 17** muestran que han transcurrido 5032 tics entre los eventos 125 y 154. Aunque este cálculo se puede realizar manualmente examinando las marcas de tiempo relativo de cada evento y restándolas, con la interfaz gráfica de usuario es fácil e instantáneo.

## <a name="actual-time-display"></a>Presentación del tiempo real

Cuando está habilitada esta opción, TraceX muestra el tiempo real en microsegundos en la pestaña **Time View** (Vista de tiempo) y también para la diversa información de tiempo diferencial que se muestra en TraceX. De forma predeterminada, la presentación del tiempo real está deshabilitada. Para habilitar la presentación del tiempo real, se debe especificar el número de tics por microsegundo mediante la selección del menú *_Options -> Ticks per Microsecond_* (Opciones > Tics por microsegundo) (el valor que se va a especificar viene determinado por el origen del temporizador de hardware usado para el registro de eventos de TraceX en el destino).

## <a name="priority-inversions"></a>Inversiones de prioridad

TraceX muestra automáticamente las inversiones de prioridad detectadas en el archivo de seguimiento. Las inversiones de prioridad se definen como condiciones en las que se bloquea un subproceso de prioridad superior intentando obtener una exclusión mutua que actualmente es propiedad de un subproceso de prioridad más baja. Esta condición se denomina *determinista*, ya que el sistema se configuró para funcionar de esta manera. Con el fin de informar al usuario, TraceX muestra intervalos de inversión de prioridad *deterministas* en un color salmón claro.

TraceX también muestra las inversiones de prioridad *no deterministas*. Estas inversiones de prioridad difieren de las inversiones de prioridad *deterministas* en que otro subproceso de un nivel de prioridad diferente se ha ejecutado en medio de lo que ha sido una inversión de prioridad *determinista*, lo que hace que el tiempo dentro de la inversión de prioridad sea algo *no determinista*. El usuario suele desconocer esta condición, y puede ser muy grave. Para alertar al usuario de esta condición, TraceX muestra las inversiones de prioridad *no deterministas* en un color salmón más vivo. En la **figura 18** se muestran las inversiones de prioridad *deterministas* y *no deterministas*.

![Captura de pantalla de la inversión de prioridad en un archivo de seguimiento.](./media/user-guide/screen_shot_43.png)

**FIGURA 18**

En la **figura 18** se muestra una inversión de prioridad *determinista* del evento 398 al 402. En este intervalo, el **subproceso 0** de prioridad superior se bloquea en una exclusión mutua propiedad de un _*_subproceso 1_*_ de prioridad inferior. En el evento 402, el *_subproceso 1_* libera la exclusión mutua y, por tanto, finaliza la inversión de prioridad.

El área sombreada más brillante muestra una inversión de prioridad *no determinista* entre el evento 408 y 420. Lo que hace que sea *no determinista* es que mientras que el **subproceso 1** contiene la exclusión mutua en la que se bloquea el _*_subproceso 0_*_ de prioridad superior, se produce una interrupción que reanuda el _subproceso 2_, que luego se ejecuta y alarga el tiempo en que el sistema está en la inversión de prioridad. Esta condición puede ser bastante seria y difícil de identificar; sin embargo, con TraceX se identifica fácilmente.
