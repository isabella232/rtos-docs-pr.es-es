---
title: 'Apéndice D: Volcado y búfer de seguimiento'
description: El volcado del búfer de seguimiento creado por Azure RTOS ThreadX en un archivo del equipo host se realiza mediante comandos y/o utilidades proporcionados por la herramienta de desarrollo específica que se va a utilizar.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: afbbabbd04ac4c33a747bb0cce4a9f36ca2d197a819cb48d834429e29fe5572c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802402"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a>Apéndice D: Volcado y búfer de seguimiento

El volcado del búfer de seguimiento creado por Azure RTOS ThreadX en un archivo del equipo host se realiza mediante comandos y/o utilidades proporcionados por la herramienta de desarrollo específica que se va a utilizar. Este apéndice contiene ejemplos de cómo volcar un búfer de seguimiento en un archivo de host en algunas de las herramientas de desarrollo más populares que se usan con ThreadX. 

## <a name="benchx-tools"></a>Herramientas de BenchX

El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de BenchX; para ello, seleccione el botón ***Store Memory To File** _ (Almacenar memoria en archivo) en _*_Memory View_** (Vista de memoria), como se muestra a continuación:

![Captura de pantalla de la vista de memoria en las herramientas de BenchX](./media/user-guide/image642.jpg)

En este punto, especifique la dirección del búfer de seguimiento, el tamaño, el nombre del archivo de destino (incluida la ruta de acceso) y seleccione el botón ***Save*** (Guardar) como se muestra a continuación. Se creará el archivo de seguimiento binario para verlo dentro de TraceX.

![Captura de pantalla del cuadro de diálogo para guardar de las herramientas de BenchX](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a>Herramientas de RealView

El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de RealView de ARM; para ello, escriba el siguiente comando en el símbolo de la línea de comandos en RealView:

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

Al finalizar, el archivo ***trace_file.trx*** contendrá el búfer de seguimiento que se encuentra a partir de la dirección 0x6860 y que se dirige a 0xE560. Este archivo está listo para que lo vea TraceX.

## <a name="iar-tools"></a>Herramientas de IAR

El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de IAR; para ello, solo tiene que hacer clic con el botón derecho en la vista de memoria y seleccionar la opción ***Memory Save…*** (Almacenamiento en memoria), como se muestra a continuación.

![Captura de pantalla de la opción de almacenamiento en memoria en las herramientas de IAR](./media/user-guide/image0_311.jpg)

A continuación, se abre el cuadro de diálogo ***Memory Save** _ (Almacenamiento en memoria). Escriba la dirección inicial y final y el nombre del archivo de seguimiento y, a continuación, seleccione el botón _*_Save_*_ (Guardar). En el ejemplo que se muestra a continuación, las herramientas de IAR guardan el búfer de seguimiento especificado en registros HEX de Intel en el archivo _*_trace_file.hex_**.

![Captura de pantalla del cuadro de diálogo de almacenamiento en memoria de las herramientas de IAR](./media/user-guide/image648.jpg)

En este punto, tenemos el búfer de seguimiento guardado en el archivo ***trace_file.hex*** en el host y está listo para verlo con TraceX.

## <a name="codewarrior-tools"></a>Herramientas de CodeWarrior

El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de CodeWarrior; para ello, escriba el comando ***save** _ en la ventana de comandos. En el ejemplo siguiente, el comando _ *_save_** supone que el búfer de seguimiento se inicia en 0x102200 y finaliza en 0x109F00:

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

Esto hace que el búfer de seguimiento se guarde en el archivo ***trace_file.trx*** en el host.

## <a name="mplab-tools"></a>Herramientas de MPLAB

MPLAB puede crear un archivo de seguimiento compatible con TraceX con la utilidad de exportación de tablas, que permite exportar cualquier intervalo de memoria a un archivo de host. Para usar esta utilidad con el fin de crear un archivo de seguimiento para TraceX, siga estos pasos:

**Paso 1**: abra una ventana Memory (Memoria); para ello, seleccione View -> Memory (Ver -> Memoria).

![Captura de pantalla con la opción Memory (Memoria) seleccionada en el menú View (Ver)](./media/user-guide/image0_316.jpg)

**Paso 2**: haga clic con el botón derecho en la **vista Memory** (Memoria) para mostrar una lista de opciones. Especifique **Display Format -1 Byte** (Formato de presentación: 1 byte) para seleccionar la presentación de bytes.

![Captura de pantalla de la vista de memoria con la opción Display Format (Formato de presentación) seleccionada](./media/user-guide/image650.png)

![Captura de pantalla del cuadro de diálogo Go To (Ir a)](./media/user-guide/image651.jpg)

**Paso 3**: vuelva a hacer clic con el botón derecho en la ventana de la **vista Memory** (Memoria) y seleccione **Go To** (Ir a); a continuación, se abre un cuadro de diálogo que le permite especificar la dirección del búfer de eventos. En este ejemplo se muestra **_event_buffer_**.

![Captura de pantalla de la vista de memoria con la opción Ir a seleccionada](./media/user-guide/image0_312.jpg)

![Captura de pantalla de un ejemplo en el que se muestra event_buffer](./media/user-guide/image653.png)

**Paso 4**: esto resalta el contenido de la primera ubicación del búfer de seguimiento, que siempre es la cadena BTXT...

![Captura de pantalla de la primera ubicación del búfer de seguimiento](./media/user-guide/image0_313.jpg)

**Paso 5**: ahora, vuelva a hacer clic con el botón derecho para abrir el menú opciones y seleccione **Export Table** (Exportar tabla).

![Captura de pantalla de la vista de memoria con la opción de exportación de tabla seleccionada](./media/user-guide/image0_314.jpg)

**Paso 6**: se abrirá el cuadro de diálogo **Export Table** (Exportar tabla), como se muestra. Especifique el intervalo de direcciones que se va a exportar. En el caso de un búfer de seguimiento de 8 K, como en este ejemplo, especifique el intervalo 0xA00006AC a 0xA00026AC y escriba un nombre para el archivo de host que se va a crear (demo_threadx.trx en este ejemplo).

![[Captura de pantalla de la ventana Export As (Exportar como)](./media/user-guide/image656.jpg)

**Paso 7**: se creará un archivo denominado **demo_threadx.trx** en el host, y este archivo se puede abrir mediante TraceX.

## <a name="ghs-tools"></a>Herramientas de GHS

El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de GHS; para ello, escriba el siguiente comando en el símbolo de la línea de comandos en la ventana de comandos de depuración:

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

Al finalizar, el archivo **demo_threadx.trx** contendrá el búfer de seguimiento que se encuentra en event_buffer con un tamaño de 32 768 bytes y está listo para que lo vea TraceX.

## <a name="renesas-hew"></a>Renesas HEW

El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de Renasas HEW; para ello, siga los tres pasos y los subpasos siguientes:

**Paso 1**: abra la ventana Memory (Memoria).

![[Captura de pantalla de la ventana Memory (Memoria)](./media/user-guide/image657.jpg)

**Paso 2**: coloque el cursor dentro de la ventana Memory (Memoria) y haga clic con el botón derecho.

![Captura de pantalla de la ventana Memory (Memoria) con la opción Save (Guardar) seleccionada](./media/user-guide/image0_315.jpg)

**Paso 3**: seleccione Save (Guardar) y, a continuación, en la ventana Save Memory As (Guardar memoria como), haga lo siguiente:

- Seleccione File format: Binary (Formato de archivo: Binario).
- Especifique Filename (Nombre de archivo): (como desee).
- Especifique Start address (Dirección de inicio): trace_buffer.
- Especifique End address (Dirección final): (trace_buffer+tamaño).
- Especifique Access size (Tamaño de acceso): 1.
- Haga clic en Guardar

![Captura de pantalla del cuadro de diálogo para guardar la memoria como](./media/user-guide/image659.jpg)