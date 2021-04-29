---
title: Definición de flujo de pantalla
description: GUIX Studio admite la generación y ejecución automáticas de la lógica de transición de pantalla.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 1c590725281c785181bcb4c5852346bc973c24d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814918"
---
# <a name="chapter-7-defining-screen-flow"></a>Capítulo 7: Definición de flujo de pantalla

GUIX Studio admite la generación y ejecución automáticas de la lógica de transición de pantalla. El usuario define la lógica de transición de pantalla mediante la creación y edición de un diagrama de gráfico de flujo de pantalla. Cuando se agrega un diagrama de flujo de pantalla al proyecto, se habilitan dos características importantes: 1) la aplicación se puede ejecutar desde el entorno de Studio y 2) Studio genera automáticamente controladores de eventos y lógica de transición de pantalla para implementar el flujo de pantalla designado dentro del archivo specifications.c generado, lo que elimina esta carga al programa de la aplicación. 

Ejecutar la aplicación en el escritorio desde el entorno de Studio es una característica útil que ahorra tiempo, ya que no es necesario pasar por un ciclo de compilación/vinculación para ejecutar la aplicación. Por supuesto, hay limitaciones a lo que se puede hacer sin compilar la aplicación. Las funciones de dibujo personalizadas, los controladores de eventos personalizados y el control de eventos complejos no están disponibles cuando se ejecuta la aplicación desde el entorno de GUIX Studio. Aun así, esta funcionalidad permite generar automáticamente la lógica de transición de pantalla y las animaciones de programa que se ejecutarán para pasar de una pantalla a otra. Estos efectos y animaciones se pueden observar directamente desde el entorno de GUIX Studio.

Tenga en cuenta que, al definir el flujo de pantalla, los desencadenadores y las acciones que describiremos en los párrafos siguientes, no solo se está habilitando la ejecución de la interfaz de usuario desde el entorno de Studio, sino que también se permite que GUIX Studio genere lógica dentro del archivo de especificaciones que controlará los eventos y realizará acciones basadas en esos eventos, como la transición de una pantalla a otra.

## <a name="configuring-screen-flow"></a>Configuración del flujo de pantalla

Para poder ejecutar una aplicación desde el entorno de Studio, deben definirse algunas cosas. En primer lugar, las pantallas de nivel superior que deben mostrarse al inicio del programa deben indicarse seleccionando la propiedad "Visible at Startup" (Visible al iniciar) en la vista de propiedades de Studio. Esta marca indica que esta pantalla debe mostrarse inicialmente cuando se inicia el programa. Si lo desea, más de una pantalla puede tener esta designación.

Después de definir las pantallas que son visibles en el inicio, el usuario puede definir cómo la aplicación de la interfaz de usuario pasará de una pantalla a otra. GUIX Studio proporciona un diagrama de flujo de pantalla gráfico para definir la lógica de transición de pantalla. Simplemente seleccione la selección de menú ***Configure, Screen Flow** _ (Configurar, Flujo de pantalla) para abrir el cuadro de diálogo de edición de flujo de pantalla; vea la captura de pantalla en la _ *_figura 30_* *.

![Captura de pantalla del cuadro de diálogo del flujo de pantalla de GUIX Studio.](./media/guix-studio/config_screen_flow.png)

**Figura 30**

Cada pantalla de nivel superior definida en el proyecto se mostrará como un cuadro que muestra el nombre de la pantalla. Este cuadro es un marcador de posición que representa cada pantalla de nivel superior definida en el proyecto. Estos cuadros se pueden quitar y cambiar de tamaño según sea necesario. Cuando se ha definido una transición de una pantalla de nivel superior a otra, se muestra una línea de conexión con un encabezado de flecha entre dos pantallas para indicar las transiciones de una pantalla a otra.

La vista de árbol en el lado izquierdo del diagrama de flujo de pantalla muestra cada pantalla de nivel superior y puede seleccionar qué pantallas de nivel superior deben dibujarse en el diagrama de flujo de pantalla.

El diagrama de flujo de pantalla es desplazable. Puede arrastrar cualquier bloque de pantalla hacia abajo y a la derecha fuera del área visible para ampliar la ventana desplazable. Una vez que se amplía la ventana desplazable, puede alejarla para ajustarla al área visible desplazando la rueda del mouse hacia abajo. Si la ventana desplazable está alejada, puede hacerla lo suficientemente grande como para contener todos los bloques desplazando la rueda del mouse hacia arriba.

Para definir las transiciones de una pantalla, haga clic con el botón derecho en el marcador de posición de la pantalla para abrir el cuadro de diálogo Edit Trigger List (Editar lista de desencadenadores); vea la ***figura 31***.

![Captura de pantalla del cuadro de diálogo Editar lista de desencadenadores de GUIX Studio.](./media/guix-studio/edit_trigger_list.png)

**Figura 31**

En el cuadro de diálogo de edición de desencadenador se muestran los eventos definidos por el usuario que desencadenarán una transición de pantalla, que es el motivo por el que llamamos a estos "desencadenadores de eventos". Los desencadenadores suelen ser señales generadas por uno o más widgets secundarios de la pantalla seleccionada.

Para definir un nuevo desencadenador, seleccione el botón ***Add New Trigger** (Agregar nuevo desencadenador) en el cuadro de diálogo Edit Trigger List (Editar lista de desencadenadores) para abrir el cuadro de diálogo  Add Trigger (Agregar desencadenador) que se muestra en _*_Figura 32_**.

![Captura de pantalla del cuadro de diálogo Add Trigger (Agregar desencadenador) de GUIX Studio.](./media/guix-studio/add_trigger_for.png)

**Figura 32**

Puede definir el tipo de evento que desencadenará un nuevo conjunto de acciones y definir las acciones que se ejecutarán cuando se reciba ese evento desencadenador.

Una vez que defina el tipo de evento que desea usar para desencadenar una nueva transición de pantalla de animación, guarde este nuevo desencadenador y se mostrará en el cuadro de diálogo Edit Trigger List (Editar lista de desencadenadores).

Puede modificar este evento (sin modificar las acciones relacionadas que se van a realizar) seleccionando el evento en el cuadro de diálogo Edit Trigger List (Editar lista de desencadenadores) y el botón ***Edit Trigger Event*** (Editar evento de desencadenador).

Del mismo modo, puede quitar cualquier evento desencadenador de la lista; para ello, seleccione el evento y haga clic en el botón ***Delete Selected Trigger*** (Eliminar desencadenador seleccionado).

Para especificar la animación o la transición de la pantalla que debe producirse en función de un evento de desencadenador determinado, seleccione ese evento desencadenador y haga clic en el botón ***Edit Action(s)*** (Editar acciones). Tenga en cuenta que puede activar más de una acción en función de cada desencadenador definido.

El botón **Edit Action(s)** (Editar acciones) muestra el cuadro de diálogo Edit Actions for Trigger (Editar acciones para desencadenador), que se muestra en la figura 33: 

![Captura de pantalla del cuadro de diálogo Edit Actions for Trigger (Editar acciones para desencadenador) de GUIX Studio.](./media/guix-studio/edit_actions_for_trigger.png)

**Figura 33**

Este cuadro de diálogo permite definir el número de acciones que se van a implementar en función de este evento desencadenador. Puede asignar a cada acción un nombre descriptivo para ayudarle a asociar cada definición de acción con una animación o transición visual. En el ejemplo anterior, hemos definido dos acciones denominadas "fade_in_text_screen" y "fade_out_button_screen".

Para definir una nueva acción que se va a implementar, haga clic en el botón Add New Action (Agregar nueva acción), que muestra el cuadro de diálogo Select Action (Seleccionar acción); vea la figura 34:

![Captura de pantalla del cuadro de diálogo Select Action (Seleccionar acción) de GUIX Studio.](./media/guix-studio/select_action.png)

**Figura 34**

Estos son algunos de los tipos de acciones disponibles:

- **Animation** (Animación): inicia una animación con la información especificada.
- **Attach** (Asociar): asocie la pantalla de destino a la pantalla primaria; si no se especifica la pantalla primaria, la pantalla de destino se asociará a la ventana raíz.
- **Detach** (Desasociar): desasocie la pantalla de destino de su elemento primario.
- **Hide** (Ocultar): oculte la pantalla de destino.
- **Screen Stack Pop** (Extracción de la pila de pantalla): extrae una pantalla de la pila de pantalla interna.
- **Screen Stack Pus** (Inserción en la pila de pantalla): inserte un puntero de pantalla en la pila de pantalla interna.
- **Screen Stack Reset** (Restablecimiento de la pila de pantalla): quite todos los punteros de pantalla de la pila de pantalla interna.
- **Show** (Mostrar): muestra la pantalla de destino.
- **Toggle** (Alternar): asocie la pantalla de destino al elemento primario de la pantalla actual y suelte la pantalla actual de su elemento primario.
- **Ventana Execute (Ejecutar)** : ejecute de forma modal la pantalla de destino.
- **Ventana Execute Stop (Ejecutar parada)** : salga de la ejecución de forma modal de la pantalla actual.

Una vez que haya definido la acción que se debe realizar en función del evento desencadenador seleccionado, esa acción se mostrará en el cuadro de diálogo Edit Actions for Trigger (Editar acciones para desencadenador). Puede seleccionar esta acción para modificar los parámetros de la acción, tal como se muestra en la figura 35.

![Captura de pantalla del cuadro de diálogo Edit Actions for Trigger (Editar acciones para desencadenador) de GUIX Studio.](./media/guix-studio/edit_actions_for_trigger.png)

**Figura 35**

Si el tipo de acción es una animación, se muestra un conjunto de parámetros de animación a la derecha para que pueda definir una animación de tipo deslizante o de transición para ejecutar. Cuando se completa una acción de animación, también puede determinar si la animación debe desasociarse automáticamente de su elemento primario o insertarse en la pila de pantalla interna, lo que a menudo resulta útil al definir sistemas de menús de varias capas.

En el caso de animaciones de deslizamiento y de atenuación, también puede definir la función de aceleración que se va a usar seleccionando el botón Easing Func Select (Selección de función de aceleración). Las funciones de aceleración son diversas curvas diseñadas para imitar mejor los eventos de movimiento de la vida real. Al seleccionar este botón se muestra el cuadro de diálogo **Select Easing Function** (Seleccionar función de aceleración); vea la figura 36:

![Captura de pantalla del cuadro de diálogo Select Easing Function (Seleccionar función de aceleración) de GUIX Studio](./media/guix-studio/easing_function_select.png)

**Figura 36**

Si está definiendo varias acciones para asociar a un evento de desencadenador, puede ser útil asignar un nombre descriptivo a cada acción. Los nombres de acción deben seguir las reglas de nomenclatura de la sintaxis de C, ya que estos nombres se utilizarán en el archivo de especificaciones generadas para definir tablas de eventos y de acciones.

Al definir acciones y eventos de desencadenador en GUIX Studio, se generan controladores de eventos automatizados en el archivo de especificaciones del proyecto para controlar estos eventos y ejecutar las acciones especificadas. Esto significa que no es necesario controlar estos eventos en el código de la aplicación, aunque los eventos del desencadenador todavía se pasan a los controladores de eventos personalizados que haya definido. En otras palabras, los controladores de eventos generados por Studio aumentan, en lugar de reemplazar, sus propios controladores de eventos personalizados.

## <a name="running-the-application"></a>Ejecutar la aplicación

Una vez que se han creado las pantallas de inicio y un diagrama de flujo de pantalla, puede ejecutar la aplicación en Studio seleccionando el botón "Run Application" (Ejecutar aplicación)

![Captura de pantalla del botón Run Application (Ejecutar aplicación)](./media/guix-studio/image68.jpg)

en la barra de herramientas, seleccionando Edit | Run Application (Editar | Ejecutar aplicación) en el menú del proyecto o seleccionando el botón Run (Ejecutar) situado en la parte inferior del cuadro de diálogo Edit Screen Flow (Editar flujo de pantalla).

Cuando ejecute la aplicación, verá que en una nueva ventana se muestran las pantallas que ha designado como "visible al iniciar". Los widgets secundarios de esta pantalla están totalmente operativos. Puede hacer clic en los botones, usar controles deslizantes y ruedas de desplazamiento, etc. Si ha definido funciones de dibujo personalizadas o el control de eventos de cliente para cualquiera de estos widgets, no los verá al ejecutar la aplicación en este modo. Pero si ha definido un diagrama de flujo de pantalla con eventos y acciones de desencadenador, dichos desencadenadores estarán operativos y las pantallas cambiarán según se haya definido, incluidas las animaciones que haya definido.
