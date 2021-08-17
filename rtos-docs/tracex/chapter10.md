---
title: 'Capítulo 10: Eventos de usuario de cliente'
description: En este capítulo se incluye una descripción de cómo crear eventos definidos por el usuario, iconos personalizados y campos de información para dichos eventos.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: b287436fb7f61df846bb0c84d910f5c095bc1f8f6635305e97c9e8b7aab64655
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790432"
---
# <a name="chapter-10---customer-user-events"></a>Capítulo 10: Eventos de usuario de cliente

En este capítulo se incluye una descripción de cómo crear eventos definidos por el usuario, iconos personalizados y campos de información para dichos eventos. En este capítulo se incluyen las secciones siguientes: 

## <a name="inserting-user-defined-events"></a>Inserción de eventos definidos por el usuario

ThreadX ofrece la posibilidad de que los desarrolladores registren sus propios eventos definidos por el usuario, proporcionando información aún más útil que se puede ver gráficamente mediante TraceX. Los números de eventos definidos por el usuario oscilan entre

**TX_TRACE_USER_EVENT_START** (4096) y **TX_TRACE_USER_EVENT_END** (65535), ambos incluidos. La colocación de los eventos en el búfer de seguimiento se realiza mediante ***tx_trace_user_event_insert***, que se define en el capítulo 5. Las llamadas de ejemplo siguientes insertan dos eventos definidos por el usuario en el búfer de seguimiento actual, en concreto el evento definido por el usuario 4096 y el evento definido por el usuario 4098:

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a>Visualización predeterminada de eventos definidos por el usuario

![Icono de evento definido por el usuario](./media/user-guide/tx-events/image0.png)

De forma predeterminada, TraceX muestra todos los eventos de usuario con un icono de evento definido por el usuario predeterminado, como se describe en el capítulo 6. La figura 28 muestra el icono de evento predeterminado definido por el usuario para los eventos 452 y 453, que se colocaron en el búfer de eventos mediante los ejemplos de ***tx_trace_user_event_insert*** anteriores.

![Captura de pantalla de la visualización predeterminada de eventos definidos por el usuario.](./media/user-guide/10.1.png)
**FIGURA 28**

También hay información detallada disponible para los eventos definidos por el usuario. La figura 28 muestra la información detallada de eventos del evento 452, que tiene el número de evento 4096 y muestra los cuatro campos de información especificados.

![Captura de pantalla de la visualización detallada de eventos definidos por el usuario.](./media/user-guide/10.2.png)
**FIGURA 29**

## <a name="defining-custom-user-defined-event-icons"></a>Definición de iconos de eventos definidos por el usuario personalizados

TraceX también proporciona al usuario la capacidad de crear iconos de eventos personalizados definidos por el usuario y etiquetas de campo de información personalizadas. Esta capacidad se consigue agregando especificaciones de icono de evento al archivo de configuración ***tracex_custom.trxc** _. Este archivo se encuentra en el subdirectorio _ *_CustomEvents_** del directorio de instalación de TraceX definido por el usuario, que por defecto es c:\Azure_RTOS\TraceX. En la figura 30 se muestra una ruta de acceso al directorio de ejemplo.

![Captura de pantalla de una ruta de acceso al directorio de ejemplo.](./media/user-guide/custom_events_folder.png)
**FIGURA 30**

El archivo de configuración de eventos personalizado ***tracex_custom.trxc*** es un simple archivo de texto ASCII que contiene cero o más definiciones de eventos personalizados. El formato del archivo es el siguiente:

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

Cada línea entre Start y End se usa para definir un único evento personalizado. TraceX proporciona una versión de plantilla de este archivo sin eventos personalizados definidos (nada entre las etiquetas "Start" y "End"). El formato de una definición de evento personalizado es el siguiente:

**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**

donde:

- number: define el número de evento definido por el usuario, entre 4096 y 65535, ambos incluidos.</th>
- name: define el nombre lógico para el evento definido por el usuario.</td>
- abbreviation: define la abreviatura de eventos definidos por el usuario de dos letras.</td>
- top_color: define el valor RGB de la mitad superior del icono, que es un número de tres dígitos entre paréntesis. Algunas definiciones RGB típicas son
  - NEGRO = (0,0,0)       
  - BLANCO = (255,255,255)
  - ROJO = (255,0,0)     
  - VERDE = (0,255,0)     
  - AZUL = (0,0,255)     
  - AMARILLO = (255,255,0)   
  - CIAN = (0,255,255)   
  - MAGENTA = (255,0,255)   
  El uso de la especificación RBG proporciona al usuario una amplia gama de colores para cada icono definido por el usuario. Para obtener más información sobre la definición de color RBG, consulte: https://en.wikipedia.org/wiki/RGB#Digital_representations
- bottom_color: define el valor RGB de la mitad inferior del icono, que es un número de tres dígitos entre paréntesis.
- label1: etiqueta para ***info_field_1** _, como se especifica en la llamada _ *_tx_trace_user_event_insert_**.
- label2: etiqueta para ***info_field_2** _, como se especifica en la llamada _ *_tx_trace_user_event_insert_**.
- label3: etiqueta para ***info_field_3** _, como se especifica en la llamada _ *_tx_trace_user_event_insert_**.
- label4: etiqueta para ***info_field_4** _, como se especifica en la llamada _ *_tx_trace_user_event_insert_**.

En la figura 10.4 se muestran definiciones de ejemplo para cada uno de los dos eventos definidos por el usuario que se usan en este capítulo. La primera definición es para el evento 4096 de la línea 5 del archivo ***tracex_custom.trxc** _. Esta definición proporciona al evento 4096 definido por el usuario el nombre _*First_User_Event**, especifica la abreviatura de dos letras **FE**, hace que la parte superior del icono sea roja, la parte inferior del icono verde y asigna a los campos de información los nombres **First_Info1**, **First_Info2**, **First_Info3** y **First_Info4**. El evento 4098 definido por el usuario se define de forma similar en la línea 6 de **_tracex_custom.trxc_**.

![Captura de pantalla de las definiciones de ejemplo para los eventos definidos por el usuario.](./media/user-guide/10.4.png)
**FIGURA 31**

Dado que TraceX lee el archivo ***tracex_custom.trxc** _ durante la inicialización, TraceX se debe cerrar y reiniciar para que las definiciones de iconos personalizados surtan efecto. En la figura 32 se muestra la pantalla de TraceX de los eventos definidos por el usuario 452 y 453 con los iconos de eventos personalizados definidos en _*_tracex_custom.trxc_**.

![Captura de pantalla de la pantalla de TraceX de loa eventos definidos por el usuario con los iconos de eventos personalizados.](./media/user-guide/10.5.png)
**FIGURA 32**

La información adicional en la definición de evento personalizado se muestra cuando se selecciona un evento con un doble clic, al pasar el puntero del mouse o al hacer clic en el botón del evento actual. En la figura 33 se muestra la selección de doble clic en el evento 452. Todos los campos de información y el nombre de evento coinciden con la definición de ejemplo que se agregó a ***tracex_custom.trxc***.

![Captura de pantalla de la selección de doble clic en un evento.](./media/user-guide/10.6.png)
**FIGURA 33**
