---
title: 'Apéndice D: Volcado y búfer de seguimiento'
description: El volcado del búfer de seguimiento creado por Azure RTOS ThreadX en un archivo del equipo host se realiza mediante comandos y/o utilidades proporcionados por la herramienta de desarrollo específica que se va a utilizar.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815869"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a><span data-ttu-id="0b4d4-103">Apéndice D: Volcado y búfer de seguimiento</span><span class="sxs-lookup"><span data-stu-id="0b4d4-103">Appendix D - Dumping and trace buffer</span></span>

<span data-ttu-id="0b4d4-104">El volcado del búfer de seguimiento creado por Azure RTOS ThreadX en un archivo del equipo host se realiza mediante comandos y/o utilidades proporcionados por la herramienta de desarrollo específica que se va a utilizar.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-104">Dumping the trace buffer created by Azure RTOS ThreadX to a file on the host computer is done via commands and/or utilities provided by the specific development tool being used.</span></span> <span data-ttu-id="0b4d4-105">Este apéndice contiene ejemplos de cómo volcar un búfer de seguimiento en un archivo de host en algunas de las herramientas de desarrollo más populares que se usan con ThreadX.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-105">This appendix contains examples of dumping a trace buffer to a host file in some of the more popular development tools used with ThreadX.</span></span> 

## <a name="benchx-tools"></a><span data-ttu-id="0b4d4-106">Herramientas de BenchX</span><span class="sxs-lookup"><span data-stu-id="0b4d4-106">BenchX Tools</span></span>

<span data-ttu-id="0b4d4-107">El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de BenchX; para ello, seleccione el botón ***Store Memory To File** _ (Almacenar memoria en archivo) en _*_Memory View_\*\* (Vista de memoria), como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="0b4d4-107">The trace buffer can be dumped to a host file easily with the BenchX tools by selecting the ***Store Memory To File** _ button within the _*_Memory View_\*\*, as shown below:</span></span>

![Captura de pantalla de la vista de memoria en las herramientas de BenchX](./media/user-guide/image642.jpg)

<span data-ttu-id="0b4d4-109">En este punto, especifique la dirección del búfer de seguimiento, el tamaño, el nombre del archivo de destino (incluida la ruta de acceso) y seleccione el botón ***Save*** (Guardar) como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-109">At this point, specify the trace buffer address, size, destination file name (including path), and select the ***Save*** button as shown below.</span></span> <span data-ttu-id="0b4d4-110">Se creará el archivo de seguimiento binario para verlo dentro de TraceX.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-110">This will create the binary trace file for viewing within TraceX.</span></span>

![Captura de pantalla del cuadro de diálogo para guardar de las herramientas de BenchX](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a><span data-ttu-id="0b4d4-112">Herramientas de RealView</span><span class="sxs-lookup"><span data-stu-id="0b4d4-112">RealView Tools</span></span>

<span data-ttu-id="0b4d4-113">El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de RealView de ARM; para ello, escriba el siguiente comando en el símbolo de la línea de comandos en RealView:</span><span class="sxs-lookup"><span data-stu-id="0b4d4-113">The trace buffer can be dumped to a host file easily with the ARM RealView tools by entering the following command at the command-line prompt in RealView:</span></span>

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

<span data-ttu-id="0b4d4-114">Al finalizar, el archivo ***trace_file.trx*** contendrá el búfer de seguimiento que se encuentra a partir de la dirección 0x6860 y que se dirige a 0xE560.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-114">Upon completion, the file ***trace_file.trx*** will contain the trace buffer that is located starting at the address 0x6860 and goes up to address 0xE560.</span></span> <span data-ttu-id="0b4d4-115">Este archivo está listo para que lo vea TraceX.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-115">This file is ready for viewing by TraceX.</span></span>

## <a name="iar-tools"></a><span data-ttu-id="0b4d4-116">Herramientas de IAR</span><span class="sxs-lookup"><span data-stu-id="0b4d4-116">IAR Tools</span></span>

<span data-ttu-id="0b4d4-117">El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de IAR; para ello, solo tiene que hacer clic con el botón derecho en la vista de memoria y seleccionar la opción ***Memory Save…*** (Almacenamiento en memoria),</span><span class="sxs-lookup"><span data-stu-id="0b4d4-117">The trace buffer can be dumped to a host file easily with the IAR tools by simply right-clicking in the memory view and selecting the ***Memory Save…***</span></span> <span data-ttu-id="0b4d4-118">como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-118">option, as shown below.</span></span>

![Captura de pantalla de la opción de almacenamiento en memoria en las herramientas de IAR](./media/user-guide/image0_311.jpg)

<span data-ttu-id="0b4d4-120">A continuación, se abre el cuadro de diálogo \***Memory Save** _ (Almacenamiento en memoria).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-120">This results in the \***Memory Save** _ dialog to be displayed.</span></span> <span data-ttu-id="0b4d4-121">Escriba la dirección inicial y final y el nombre del archivo de seguimiento y, a continuación, seleccione el botón _*_Save_*_ (Guardar).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-121">Enter the starting and ending address and the trace file name, then select the _*_Save_*_ button.</span></span> <span data-ttu-id="0b4d4-122">En el ejemplo que se muestra a continuación, las herramientas de IAR guardan el búfer de seguimiento especificado en registros HEX de Intel en el archivo _\*_trace_file.hex_\*\*.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-122">In the example shown below, the IAR tools save the specified trace buffer into Intel HEX records in the file _\*_trace_file.hex_\*\*.</span></span>

![Captura de pantalla del cuadro de diálogo de almacenamiento en memoria de las herramientas de IAR](./media/user-guide/image648.jpg)

<span data-ttu-id="0b4d4-124">En este punto, tenemos el búfer de seguimiento guardado en el archivo ***trace_file.hex*** en el host y está listo para verlo con TraceX.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-124">At this point, we have the trace buffer saved in the ***trace_file.hex*** file on the host and is ready for viewing with TraceX.</span></span>

## <a name="codewarrior-tools"></a><span data-ttu-id="0b4d4-125">Herramientas de CodeWarrior</span><span class="sxs-lookup"><span data-stu-id="0b4d4-125">CodeWarrior Tools</span></span>

<span data-ttu-id="0b4d4-126">El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de CodeWarrior; para ello, escriba el comando \***save** _ en la ventana de comandos.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-126">The trace buffer can be dumped to a host file easily with the CodeWarrior tools by entering the \***save** _ command in the Command Window.</span></span> <span data-ttu-id="0b4d4-127">En el ejemplo siguiente, el comando _ *_save_*\* supone que el búfer de seguimiento se inicia en 0x102200 y finaliza en 0x109F00:</span><span class="sxs-lookup"><span data-stu-id="0b4d4-127">The following example _ *_save_*\* command assumes the trace buffer starts at 0x102200 and ends at 0x109F00:</span></span>

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

<span data-ttu-id="0b4d4-128">Esto hace que el búfer de seguimiento se guarde en el archivo ***trace_file.trx*** en el host.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-128">This results in the trace buffer being saved in the file ***trace_file.trx*** on the host.</span></span>

## <a name="mplab-tools"></a><span data-ttu-id="0b4d4-129">Herramientas de MPLAB</span><span class="sxs-lookup"><span data-stu-id="0b4d4-129">MPLAB Tools</span></span>

<span data-ttu-id="0b4d4-130">MPLAB puede crear un archivo de seguimiento compatible con TraceX con la utilidad de exportación de tablas, que permite exportar cualquier intervalo de memoria a un archivo de host.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-130">MPLAB can create a TraceX-compatible trace file through its Export Table utility, which allows the export of any range of memory to a host file.</span></span> <span data-ttu-id="0b4d4-131">Para usar esta utilidad con el fin de crear un archivo de seguimiento para TraceX, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="0b4d4-131">To use this utility to create a trace file for TraceX, proceed as follows:</span></span>

<span data-ttu-id="0b4d4-132">**Paso 1**: abra una ventana Memory (Memoria); para ello, seleccione View -> Memory (Ver -> Memoria).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-132">**Step 1** Open a memory window by selecting View -> Memory.</span></span>

![Captura de pantalla con la opción Memory (Memoria) seleccionada en el menú View (Ver)](./media/user-guide/image0_316.jpg)

<span data-ttu-id="0b4d4-134">**Paso 2**: haga clic con el botón derecho en la **vista Memory** (Memoria) para mostrar una lista de opciones.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-134">**Step 2** Right-click within the **Memory View** to display a list of options.</span></span> <span data-ttu-id="0b4d4-135">Especifique **Display Format -1 Byte** (Formato de presentación: 1 byte) para seleccionar la presentación de bytes.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-135">Specify **Display Format -1 Byte** to select byte display..</span></span>

![Captura de pantalla de la vista de memoria con la opción Display Format (Formato de presentación) seleccionada](./media/user-guide/image650.png)

![Captura de pantalla del cuadro de diálogo Go To (Ir a)](./media/user-guide/image651.jpg)

<span data-ttu-id="0b4d4-138">**Paso 3**: vuelva a hacer clic con el botón derecho en la ventana de la **vista Memory** (Memoria) y seleccione **Go To** (Ir a); a continuación, se abre un cuadro de diálogo que le permite especificar la dirección del búfer de eventos.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-138">**Step 3** Right-click again within the **Memory View** Window and select **Go To**, which opens a dialog box that enables you to specify the address of the event buffer.</span></span> <span data-ttu-id="0b4d4-139">En este ejemplo se muestra **_event_buffer_**.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-139">This example shows **_event_buffer_** being displayed.</span></span>

![Captura de pantalla de la vista de memoria con la opción Ir a seleccionada](./media/user-guide/image0_312.jpg)

![Captura de pantalla de un ejemplo en el que se muestra event_buffer](./media/user-guide/image653.png)

<span data-ttu-id="0b4d4-142">**Paso 4**: esto resalta el contenido de la primera ubicación del búfer de seguimiento, que siempre es la cadena BTXT...</span><span class="sxs-lookup"><span data-stu-id="0b4d4-142">**Step 4** This highlights the contents of the first location of the trace buffer, which is always the string BTXT….</span></span>

![Captura de pantalla de la primera ubicación del búfer de seguimiento](./media/user-guide/image0_313.jpg)

<span data-ttu-id="0b4d4-144">**Paso 5**: ahora, vuelva a hacer clic con el botón derecho para abrir el menú opciones y seleccione **Export Table** (Exportar tabla).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-144">**Step 5** Now, right-click again to bring up the options menu, and select **Export Table**.</span></span>

![Captura de pantalla de la vista de memoria con la opción de exportación de tabla seleccionada](./media/user-guide/image0_314.jpg)

<span data-ttu-id="0b4d4-146">**Paso 6**: se abrirá el cuadro de diálogo **Export Table** (Exportar tabla), como se muestra.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-146">**Step 6** This brings up the **Export Table** dialog, as shown.</span></span> <span data-ttu-id="0b4d4-147">Especifique el intervalo de direcciones que se va a exportar.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-147">Specify the range of addresses to export.</span></span> <span data-ttu-id="0b4d4-148">En el caso de un búfer de seguimiento de 8 K, como en este ejemplo, especifique el intervalo 0xA00006AC a 0xA00026AC y escriba un nombre para el archivo de host que se va a crear (demo_threadx.trx en este ejemplo).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-148">For an 8K trace buffer, as is the case in this example, specify the range 0xA00006AC to 0xA00026AC, and enter a name for the host file to be created (demo_threadx.trx in this example).</span></span>

<span data-ttu-id="0b4d4-149">![[Captura de pantalla de la ventana Export As (Exportar como)](./media/user-guide/image656.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b4d4-149">![[Screenshot of the Export As dialog.](./media/user-guide/image656.jpg)</span></span>

<span data-ttu-id="0b4d4-150">**Paso 7**: se creará un archivo denominado **demo_threadx.trx** en el host, y este archivo se puede abrir mediante TraceX.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-150">**Step 7** A file named **demo_threadx.trx** will be created on the host, and this file can be opened by TraceX.</span></span>

## <a name="ghs-tools"></a><span data-ttu-id="0b4d4-151">Herramientas de GHS</span><span class="sxs-lookup"><span data-stu-id="0b4d4-151">GHS Tools</span></span>

<span data-ttu-id="0b4d4-152">El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de GHS; para ello, escriba el siguiente comando en el símbolo de la línea de comandos en la ventana de comandos de depuración:</span><span class="sxs-lookup"><span data-stu-id="0b4d4-152">The trace buffer can be dumped to a host file easily with the GHS tools by entering the following command at the command-line prompt in the debug command window:</span></span>

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

<span data-ttu-id="0b4d4-153">Al finalizar, el archivo **demo_threadx.trx** contendrá el búfer de seguimiento que se encuentra en event_buffer con un tamaño de 32 768 bytes y está listo para que lo vea TraceX.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-153">Upon completion, the file **demo_threadx.trx** will contain the trace buffer that is located in the event_buffer with a size of 32,768 bytes and is ready for viewing by TraceX.</span></span>

## <a name="renesas-hew"></a><span data-ttu-id="0b4d4-154">Renesas HEW</span><span class="sxs-lookup"><span data-stu-id="0b4d4-154">Renesas HEW</span></span>

<span data-ttu-id="0b4d4-155">El búfer de seguimiento se puede volcar en un archivo de host fácilmente con las herramientas de Renasas HEW; para ello, siga los tres pasos y los subpasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="0b4d4-155">The trace buffer can be dumped to a host file easily with the Renasas HEW tools by following the three steps (and substeps) below:</span></span>

<span data-ttu-id="0b4d4-156">**Paso 1**: abra la ventana Memory (Memoria).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-156">**Step 1** Open Memory Window.</span></span>

<span data-ttu-id="0b4d4-157">![[Captura de pantalla de la ventana Memory (Memoria)](./media/user-guide/image657.jpg)</span><span class="sxs-lookup"><span data-stu-id="0b4d4-157">![[Screenshot of the Memory Window.](./media/user-guide/image657.jpg)</span></span>

<span data-ttu-id="0b4d4-158">**Paso 2**: coloque el cursor dentro de la ventana Memory (Memoria) y haga clic con el botón derecho.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-158">**Step 2** Place cursor within memory window and right click.</span></span>

![Captura de pantalla de la ventana Memory (Memoria) con la opción Save (Guardar) seleccionada](./media/user-guide/image0_315.jpg)

<span data-ttu-id="0b4d4-160">**Paso 3**: seleccione Save (Guardar) y, a continuación, en la ventana Save Memory As (Guardar memoria como), haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0b4d4-160">**Step 3** Select Save, then in the Save Memory As window do the following:</span></span>

- <span data-ttu-id="0b4d4-161">Seleccione File format: Binary (Formato de archivo: Binario).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-161">Select File format: Binary.</span></span>
- <span data-ttu-id="0b4d4-162">Especifique Filename (Nombre de archivo): (como desee).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-162">Specify Filename: As Desired</span></span>
- <span data-ttu-id="0b4d4-163">Especifique Start address (Dirección de inicio): trace_buffer.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-163">Specify Start address: trace_buffer</span></span>
- <span data-ttu-id="0b4d4-164">Especifique End address (Dirección final): (trace_buffer+tamaño).</span><span class="sxs-lookup"><span data-stu-id="0b4d4-164">Specify End address: (trace_buffer+size)</span></span>
- <span data-ttu-id="0b4d4-165">Especifique Access size (Tamaño de acceso): 1.</span><span class="sxs-lookup"><span data-stu-id="0b4d4-165">Specify Access size: 1</span></span>
- <span data-ttu-id="0b4d4-166">Haga clic en Guardar</span><span class="sxs-lookup"><span data-stu-id="0b4d4-166">Click Save</span></span>

![Captura de pantalla del cuadro de diálogo para guardar la memoria como](./media/user-guide/image659.jpg)