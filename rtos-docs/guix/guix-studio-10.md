---
title: Proyecto de ejemplo simple
description: En este capítulo se describe cómo crear un proyecto de ejemplo en GUIX Studio y cómo ejecutar el ejemplo en GUIX.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3661396f097e0ed7bd872fae01a7bec9212001b9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815005"
---
# <a name="chapter-10-example-project"></a><span data-ttu-id="67728-103">Capítulo 10: Proyecto de ejemplo</span><span class="sxs-lookup"><span data-stu-id="67728-103">Chapter 10: Example Project</span></span>

<span data-ttu-id="67728-104">En este capítulo se describe cómo crear un proyecto de ejemplo en GUIX Studio y cómo ejecutar el ejemplo en GUIX.</span><span class="sxs-lookup"><span data-stu-id="67728-104">This chapter describes how to create an example project in GUIX Studio and execute the example on GUIX.</span></span>

## <a name="create-new-project"></a><span data-ttu-id="67728-105">Creación de un proyecto</span><span class="sxs-lookup"><span data-stu-id="67728-105">Create New Project</span></span>

<span data-ttu-id="67728-106">El primer paso es crear un nuevo proyecto y configurar las pantallas y los idiomas que el proyecto admitirá.</span><span class="sxs-lookup"><span data-stu-id="67728-106">The first step is creating a new project and configuring the displays and languages that the project will support.</span></span> <span data-ttu-id="67728-107">La primera vez que inicie GUIX Studio, verá la pantalla ***Proyectos recientes***:</span><span class="sxs-lookup"><span data-stu-id="67728-107">When you first start GUIX Studio, you will see the ***Recent Projects*** screen:</span></span>

![Captura de pantalla del cuadro de diálogo Proyectos recientes de GUIX Studio.](./media/guix-studio/recent_projects.png)

<span data-ttu-id="67728-109">**Figura 10.1**</span><span class="sxs-lookup"><span data-stu-id="67728-109">**Figure 10.1**</span></span>

<span data-ttu-id="67728-110">Haga clic en el botón \***Crear proyecto** _…</span><span class="sxs-lookup"><span data-stu-id="67728-110">Click on the \***Create New Project** _…</span></span> <span data-ttu-id="67728-111">para iniciar un nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-111">button to begin a new project.</span></span> <span data-ttu-id="67728-112">Aparecerá el cuadro de diálogo _ \*_Nuevo proyecto de GUIX_\*\*, que se muestra aquí:</span><span class="sxs-lookup"><span data-stu-id="67728-112">You will be presented with the _ *_New GUIX Project_*\* dialog, shown here:</span></span>

![Captura de pantalla del cuadro de diálogo Crear proyecto de GUIX Studio.](./media/guix-studio/create_new_project.png)

<span data-ttu-id="67728-114">**Figura 10.2**</span><span class="sxs-lookup"><span data-stu-id="67728-114">**Figure 10.2**</span></span>

<span data-ttu-id="67728-115">Escriba el nombre "***new_example***" como nombre del proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-115">Type the name "***new_example***" as the project name.</span></span> <span data-ttu-id="67728-116">Los nombres de proyecto deben usar reglas de nomenclatura de variables estándar de C; es decir, sin caracteres especiales ni reservados.</span><span class="sxs-lookup"><span data-stu-id="67728-116">Project names should use standard C variable naming rules, that is, no special or reserved characters.</span></span> <span data-ttu-id="67728-117">Escriba la ruta de acceso a la ubicación donde se debe guardar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-117">Type the path to the location where the project should be saved.</span></span> <span data-ttu-id="67728-118">La ruta de acceso debe ser un directorio del sistema de archivos válido; es decir, GUIX Studio no creará el directorio si no existe.</span><span class="sxs-lookup"><span data-stu-id="67728-118">The path must be a valid file system directory, that is, GUIX Studio will not create the directory if it does not exist.</span></span> <span data-ttu-id="67728-119">Haga clic en "Aceptar" para crear el proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-119">Click "OK" to create the project.</span></span>

<span data-ttu-id="67728-120">La siguiente pantalla que se muestra es Configuración del proyecto, que se muestra aquí:</span><span class="sxs-lookup"><span data-stu-id="67728-120">The next screen shown is the Project Configuration screen, shown here:</span></span>

![Captura de pantalla del cuadro de diálogo Configurar proyecto de GUIX Studio.](./media/guix-studio/config_new_project.png)

<span data-ttu-id="67728-122">**Figura 10.3**</span><span class="sxs-lookup"><span data-stu-id="67728-122">**Figure 10.3**</span></span>

<span data-ttu-id="67728-123">Este cuadro de diálogo permite especificar el número de pantallas que admitirá el proyecto y asignar un nombre a cada pantalla.</span><span class="sxs-lookup"><span data-stu-id="67728-123">This dialog allows you to specify how many displays your project will support, and give a name to each display.</span></span> <span data-ttu-id="67728-124">Debe especificar el formato de color admitido por cada pantalla y, opcionalmente, escribir un nombre de ruta de acceso para los archivos de salida generados por Studio para cada pantalla.</span><span class="sxs-lookup"><span data-stu-id="67728-124">You must specify the color format supported by each display, and optionally type a pathname for the output files generated by Studio for each display.</span></span> <span data-ttu-id="67728-125">El directorio predeterminado para los archivos de salida es " ***\\***", lo que significa que los archivos de salida de C se escriben en el mismo directorio que el propio proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-125">The default directory for the output files is "***.\\***", meaning the C output files are written to the same directory as the project itself.</span></span>

<span data-ttu-id="67728-126">En este ejemplo, deje el valor de ***Number of Displays** _ (Número de pantallas) establecido en "1", escriba el nombre "_*_main_display_*_" en el campo de nombre para pantalla y active "_*_allocate canvas memory_\*_" (asignar memoria de lienzo).</span><span class="sxs-lookup"><span data-stu-id="67728-126">For this example, leave the ***Number of Displays** _ set to "1", type the name "_*_main_display_*_" in the display name field, and check "_*_allocate canvas memory_\*_".</span></span> <span data-ttu-id="67728-127">Deje los campos resolución, formato de color y directorio con sus valores predeterminados y haga clic en _\*_Aceptar_\*\*.</span><span class="sxs-lookup"><span data-stu-id="67728-127">Leave the resolution, color format, and directory fields at their default values, and click _\*_OK_\*\*.</span></span>

<span data-ttu-id="67728-128">Ahora debería ver el proyecto abierto con el IDE de Studio, como se muestra en la figura 10.4:</span><span class="sxs-lookup"><span data-stu-id="67728-128">You should now see your project open with the Studio IDE, as shown in figure 10.4:</span></span>

![Captura de pantalla de un proyecto abierto con el IDE de Studio.](./media/guix-studio/initial_screen.png)

<span data-ttu-id="67728-130">**Figura 10.4**</span><span class="sxs-lookup"><span data-stu-id="67728-130">**Figure 10.4**</span></span>

<span data-ttu-id="67728-131">Al crear un nuevo proyecto, GUIX Studio crea automáticamente una ventana predeterminada como punto de partida para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-131">When you create a new project, GUIX Studio automatically creates a default window as the starting point for your project.</span></span> <span data-ttu-id="67728-132">Este cuadro gris es la ventana predeterminada que se crea automáticamente centrada en la *vista de destino*.</span><span class="sxs-lookup"><span data-stu-id="67728-132">This gray box is the default window created for you, centered within the *Target View*.</span></span>

<span data-ttu-id="67728-133">Si esta ventana no está seleccionada, haga clic en la ventana para que el cuadro de selección discontinuo se dibuje en torno a la ventana.</span><span class="sxs-lookup"><span data-stu-id="67728-133">If this window is not selected, click on the window so that the dashed selection box is drawn around the window.</span></span> <span data-ttu-id="67728-134">Ahora, en el cuadro **Ver propiedades** _*, cambie los valores de _*_Widget Name_*_ (Nombre del widget), _*_Widget Id_*_ (Id. del widget), _*_Izquierda_*_, _*_Parte superior_*_ , _*_Ancho_*_ , _*_Alto_\*_ y *_Borde_* \* para que coincidan con los valores que se muestran a continuación.</span><span class="sxs-lookup"><span data-stu-id="67728-134">Now in the ***Properties View** _, change the _*_Widget Name_*_, _*_Widget Id_*_, _*_Left_*_, _*_Top_*_, _*_Width_*_, _*_Height_*_, and _ *_Border_** to match those settings shown below.</span></span> <span data-ttu-id="67728-135">Cuando realice estos cambios, debería verlos inmediatamente en la vista de destino.</span><span class="sxs-lookup"><span data-stu-id="67728-135">As you make these changes, you should see your changes immediately taking effect within the Target View.</span></span>

![Captura de pantalla del cuadro de diálogo Ver propiedades.](./media/guix-studio/initial_window_properties.png)

<span data-ttu-id="67728-137">**Figura 10.5**</span><span class="sxs-lookup"><span data-stu-id="67728-137">**Figure 10.5**</span></span>

<span data-ttu-id="67728-138">A continuación, agregaremos un recurso de mapa de píxeles que se usará en un widget \***GX_ICON** _.</span><span class="sxs-lookup"><span data-stu-id="67728-138">Next we will add a pixelmap resource to be used within a \***GX_ICON** _ widget.</span></span> <span data-ttu-id="67728-139">Se proporcionan varios iconos con la distribución de GUIX Studio que funcionarán correctamente en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="67728-139">Several icons are provided with your GUIX Studio distribution that will work fine for this example.</span></span> <span data-ttu-id="67728-140">Expanda la vista de recursos _*_Pixelmaps_*_ (Mapas de píxeles) y haga clic en el botón _ *_Add New Pixelmap_*\* (Agregar nuevo mapa de píxeles):</span><span class="sxs-lookup"><span data-stu-id="67728-140">Expand your _*_Pixelmaps_*_ Resource View and click the _ *_Add New Pixelmap_*\* button:</span></span>

![Captura de pantalla del botón Add New Pixelmap (Agregar nuevo mapa de píxeles).](./media/guix-studio/image74.jpg)

<span data-ttu-id="67728-142">Vaya a la carpeta de instalación de GUIX Studio y, dentro de la carpeta \* **./graphics/icons** _, seleccione el archivo denominado _*_i_history_lg.png_*_.</span><span class="sxs-lookup"><span data-stu-id="67728-142">Browse to your GUIX Studio installation folder, and within the ***./graphics/icons** _ folder select the file named _*_i_history_lg.png_\*_.</span></span> <span data-ttu-id="67728-143">Haga clic en _*_Abrir_*_ para agregar este recurso al proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-143">Click _*_Open_*_ to add this resource to your project.</span></span> <span data-ttu-id="67728-144">La vista de recursos _ *_Pixelmaps_*\* (Mapas de píxeles) debería mostrar ahora una vista previa de la imagen de icono recién agregada:</span><span class="sxs-lookup"><span data-stu-id="67728-144">Your _ *_Pixelmaps_*\* Resource View should now show a preview of the newly added icon image:</span></span>

![Captura de pantalla de la vista de recursos Pixelmaps (Mapas de píxeles).](./media/guix-studio/example_add_pixelmap.png)

<span data-ttu-id="67728-146">**Figura 10.6**</span><span class="sxs-lookup"><span data-stu-id="67728-146">**Figure 10.6**</span></span>

<span data-ttu-id="67728-147">Usaremos este nuevo recurso de imagen más adelante como parte del diseño de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="67728-147">We will use this new image resource later as part of our UI design.</span></span>

<span data-ttu-id="67728-148">Al igual que cuando se agrega un recurso mapa de píxeles, se agregará un nuevo recurso de fuente a nuestro cuadro de herramientas para que podamos usar esta fuente más adelante en nuestro diseño.</span><span class="sxs-lookup"><span data-stu-id="67728-148">Similar to adding a pixelmap resource, we will add a new font resource to our toolbox so that we can use this font later in our design.</span></span> <span data-ttu-id="67728-149">Expanda la vista de recursos ***Fuentes** _ y haga clic en el botón _*_Add New Font_\*_ (Agregar nueva fuente).</span><span class="sxs-lookup"><span data-stu-id="67728-149">Expand the ***Fonts** _ Resource View and click on the _*_Add New Font_\*_ button.</span></span> <span data-ttu-id="67728-150">Esta acción invocará al cuadro de diálogo _*_Agregar/Editar_*_ fuente.</span><span class="sxs-lookup"><span data-stu-id="67728-150">This action will invoke the _*_Add/Edit_*_ font dialog.</span></span> <span data-ttu-id="67728-151">A continuación, vaya a las fuentes GUIX proporcionadas en la carpeta de instalación de GUIX Studio, _\*_ .\\fonts\\verasans_ *_ y seleccione el archivo de fuentes TrueType denominado _* _VeraIt.ttf_*_. Escriba el nombre de fuente "_*_MEDIUM_ITALIC_*_" en el campo de nombre de fuente y escriba "_*_30_\*\*" en el campo de altura.</span><span class="sxs-lookup"><span data-stu-id="67728-151">Next, browse to the supplied GUIX fonts in the GUIX Studio installation folder, _\*_.\\fonts\\verasans_ *_, and select the TrueType font file named _*_VeraIt.ttf_*_. Type font the font name "_*_MEDIUM_ITALIC_*_" in the font name field, and type "_*_30_\*\*" in the height field.</span></span> <span data-ttu-id="67728-152">Ahora el cuadro de diálogo debería tener el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="67728-152">Your dialog should now look like this:</span></span>

![Captura de pantalla del cuadro de diálogo Edit Font (Editar fuente).](./media/guix-studio/example_add_font.png)

<span data-ttu-id="67728-154">**Figura 10.7**</span><span class="sxs-lookup"><span data-stu-id="67728-154">**Figure 10.7**</span></span>

<span data-ttu-id="67728-155">Haga clic en ***Aceptar*** para agregar esta fuente al proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-155">Click ***OK*** to add this font to your project.</span></span> <span data-ttu-id="67728-156">Ahora debería ver la fuente en la vista de recursos:</span><span class="sxs-lookup"><span data-stu-id="67728-156">You should now see the font in your Resource View:</span></span>

![Captura de pantalla de la sección Fuentes de la vista de recursos.](./media/guix-studio/example_font_added.png)

<span data-ttu-id="67728-158">**Figura 10.8**</span><span class="sxs-lookup"><span data-stu-id="67728-158">**Figure 10.8**</span></span>

<span data-ttu-id="67728-159">Usaremos esta nueva fuente más adelante en el diseño de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="67728-159">We will use this new font later in our UI design.</span></span>

<span data-ttu-id="67728-160">Ahora que tenemos nuevos recursos disponibles, es necesario agregar algunos widgets secundarios a la pantalla que puedan usar estos recursos.</span><span class="sxs-lookup"><span data-stu-id="67728-160">Now that we have some new resources available, we need to add some child widgets to our screen that can utilize these resources.</span></span> <span data-ttu-id="67728-161">Seleccione la ventana creada anteriormente denominada "\***hello_world** _"; para ello, haga clic con el botón derecho en la ventana de la vista de destino.</span><span class="sxs-lookup"><span data-stu-id="67728-161">Select the previously created window named "\***hello_world** _" by right-clicking on the window in the Target View.</span></span> <span data-ttu-id="67728-162">En el menú emergente que aparece ahora, seleccione el comando de menú _*_Insertar, Texto, Solicitud_*_ para insertar un nuevo widget _ *_GX_PROMPT_*\* y adjunte el widget a la ventana en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="67728-162">In the pop-up menu that is now displayed, select the menu command _*_Insert, Text, Prompt_*_ to insert a new _ *_GX_PROMPT_*\* widget and attach the widget to the background window.</span></span> <span data-ttu-id="67728-163">Ahora la ventana debería tener el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="67728-163">Your window should now look like this:</span></span>

![Captura de pantalla de un menú emergente con la selección de Solicitud](./media/guix-studio/image78.jpg)

<span data-ttu-id="67728-165">**Figura 10.9**</span><span class="sxs-lookup"><span data-stu-id="67728-165">**Figure 10.9**</span></span>

<span data-ttu-id="67728-166">Haga clic en la fuente denominada "\***MEDIUM_ITALIC** _" en el vista de recursos _ \*_Fuentes_\*\*, y arrastre y coloque la fuente en el widget de solicitud.</span><span class="sxs-lookup"><span data-stu-id="67728-166">Click on the font named "***MEDIUM_ITALIC** _" in the _ *_Fonts_** Resource View, and drag and drop the font on the prompt widget.</span></span> <span data-ttu-id="67728-167">A continuación, edite las propiedades de la solicitud como se muestra en la figura 10.10 para cambiar el tamaño de la solicitud, establezca la transparencia, y cambie el texto y el estilo de la solicitud:</span><span class="sxs-lookup"><span data-stu-id="67728-167">Next, edit the prompt properties as shown in figure 10.10 to resize the prompt, set the prompt transparency, and change the prompt text and style:</span></span>

![Captura de pantalla de la vista de propiedades de la solicitud.](./media/guix-studio/image79.jpg)

<span data-ttu-id="67728-169">**Figura 10.10**</span><span class="sxs-lookup"><span data-stu-id="67728-169">**Figure 10.10**</span></span>

<span data-ttu-id="67728-170">Es posible que tenga que desplazarse verticalmente en la vista de propiedades para ver cada una de estas opciones en función de la resolución de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="67728-170">You may need to scroll vertically in the Properties View to see each of these settings depending on your screen resolution.</span></span> <span data-ttu-id="67728-171">Después de realizar estos cambios, la vista de destino debería tener el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="67728-171">After making these changes, your Target View should now look like this:</span></span>

![Captura de pantalla de un menú emergente con la selección de Hola mundo.](./media/guix-studio/image80.jpg)

<span data-ttu-id="67728-173">**Figura 10.11**</span><span class="sxs-lookup"><span data-stu-id="67728-173">**Figure 10.11**</span></span>

<span data-ttu-id="67728-174">A continuación, colocaremos un widget de estilo de botón de icono en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="67728-174">Next we will place an Icon Button style widget on the screen.</span></span> <span data-ttu-id="67728-175">Haga clic en la ventana en segundo plano para seleccionarla y use el menú de nivel superior o el menú emergente que aparece al hacer clic con el botón derecho para seleccionar ***Insertar, Botón, Botón de icono** _ para agregar un nuevo recurso _*_GX_ICON_BUTTON_\*_ a la ventana.</span><span class="sxs-lookup"><span data-stu-id="67728-175">Select the background window by clicking on it, and use either the top-level menu or the right-click pop-up menu to select ***Insert, Button, Icon Button** _ to add a new _*_GX_ICON_BUTTON_\*_ to the window.</span></span> <span data-ttu-id="67728-176">Haga clic en el icono denominado _ *_I_HISTORY_LG_*\* que agregamos anteriormente y arrástrelo hasta el botón de icono.</span><span class="sxs-lookup"><span data-stu-id="67728-176">Click on the Icon named _ *_I_HISTORY_LG_*\* that we added earlier and drag it to the icon button.</span></span> <span data-ttu-id="67728-177">Con la vista de propiedades, ajuste la posición y el tamaño del icono como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="67728-177">Using the properties view, adjust the icon position and size as show below:</span></span>

![Captura de pantalla de la vista de propiedades del widget de estilo de botón de icono.](./media/guix-studio/image81.jpg)

<span data-ttu-id="67728-179">**Figura 10.12**</span><span class="sxs-lookup"><span data-stu-id="67728-179">**Figure 10.12**</span></span>

<span data-ttu-id="67728-180">Ahora la pantalla debería tener el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="67728-180">Your screen should now look like this:</span></span>

![Captura de pantalla de un menú emergente con el texto Hola mundo y el icono del portapapeles.](./media/guix-studio/image82.jpg)

<span data-ttu-id="67728-182">**Figura 10.13**</span><span class="sxs-lookup"><span data-stu-id="67728-182">**Figure 10.13**</span></span>

<span data-ttu-id="67728-183">Lo llamaremos completo para el diseño sencillo de la pantalla de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="67728-183">We will call this complete for the simple example screen design.</span></span> <span data-ttu-id="67728-184">Las pantallas de aplicación reales probablemente serán mucho más sofisticadas, pero esto es suficiente para mostrar cómo usar GUIX Studio para crear sus propias pantallas de aplicación.</span><span class="sxs-lookup"><span data-stu-id="67728-184">Your actual application screens will likely be much more sophisticated, but this is enough to show you how to use GUIX Studio to create your own application screens.</span></span>

## <a name="generate-resource-and-application-code"></a><span data-ttu-id="67728-185">Generación de código de recurso y aplicación</span><span class="sxs-lookup"><span data-stu-id="67728-185">Generate Resource and Application Code</span></span>

<span data-ttu-id="67728-186">El siguiente paso es generar el archivo de recursos y el archivo de especificación que define la interfaz de usuario de tiempo de ejecución de GUIX insertada.</span><span class="sxs-lookup"><span data-stu-id="67728-186">The next step is to generate the resource file and specification file that define the embedded GUIX run-time UI.</span></span> <span data-ttu-id="67728-187">Para generar los archivos de salida, tendrá que hacer clic con el botón derecho en el nodo ***main_display** _ en la vista del proyecto y seleccionar el comando _ *_Generate Resource Files_** (Generar archivos de recursos).</span><span class="sxs-lookup"><span data-stu-id="67728-187">To generate your output files you will need right-click on the ***main_display** _ node in the Project View, and select the _ *_Generate Resource Files_** command.</span></span> <span data-ttu-id="67728-188">Observará una ventana de información que indica que se han generado los archivos de recursos, como se muestra en la figura 10.14:</span><span class="sxs-lookup"><span data-stu-id="67728-188">You will observe an information window that indicates your resource files have been generated, as shown in figure 10.14:</span></span>

![Captura de pantalla de un cuadro de diálogo de notificación.](./media/guix-studio/image83.jpg)

<span data-ttu-id="67728-190">**Figura 10.14**</span><span class="sxs-lookup"><span data-stu-id="67728-190">**Figure 10.14**</span></span>

<span data-ttu-id="67728-191">Haga clic en ***Aceptar** _ para descartar esta notificación y use el mismo procedimiento para hacer clic con el botón derecho en el nodo _*_main_display_*_ y seleccione el comando _ *_Generate Specification Files_** (Generar archivos de especificación).</span><span class="sxs-lookup"><span data-stu-id="67728-191">Click ***OK** _ to dismiss this notification, and use the same procedure to right-click on the _*_main_display_*_ node and select the _ *_Generate Specification Files_** command.</span></span> <span data-ttu-id="67728-192">Debe observar una ventana de notificación similar.</span><span class="sxs-lookup"><span data-stu-id="67728-192">You should observe a similar notification window.</span></span> <span data-ttu-id="67728-193">Ahora ya ha generado los archivos de aplicación de interfaz de usuario simples.</span><span class="sxs-lookup"><span data-stu-id="67728-193">You have now generated your simple UI application files.</span></span>

## <a name="create-user-supplied-code"></a><span data-ttu-id="67728-194">Creación de código proporcionado por el usuario</span><span class="sxs-lookup"><span data-stu-id="67728-194">Create User Supplied Code</span></span>

<span data-ttu-id="67728-195">El siguiente paso consiste en crear su propio archivo de aplicación que invocará el diseño de pantalla generado por GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="67728-195">The next step is to create your own application file that will invoke the GUIX Studio-generated screen design.</span></span> <span data-ttu-id="67728-196">Con el editor que prefiera, cree un archivo de código fuente denominado ***new_example.c*** y escriba el siguiente código fuente en este archivo:</span><span class="sxs-lookup"><span data-stu-id="67728-196">Using your preferred editor, create a source file named ***new_example.c***, and enter the following source code into this file:</span></span>

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

<span data-ttu-id="67728-197">El código fuente anterior crea un subproceso de ThreadX típico denominado `GUIX New Example Thread` con un tamaño de pila de 4000 bytes.</span><span class="sxs-lookup"><span data-stu-id="67728-197">The source code above creates a typical ThreadX thread named `GUIX New Example Thread` with a stack size of 4K bytes.</span></span> <span data-ttu-id="67728-198">El trabajo interesante comienza en la función denominada ***new_example_thread_entry***.</span><span class="sxs-lookup"><span data-stu-id="67728-198">The interesting work begins in the function named ***new_example_thread_entry***.</span></span> <span data-ttu-id="67728-199">Esta función es el lugar en el que comienza a ejecutarse el subproceso específico de GUIX.</span><span class="sxs-lookup"><span data-stu-id="67728-199">This function is where the GUIX specific thread begins to run.</span></span>

<span data-ttu-id="67728-200">La primera llamada es a la función denominada ***gx_system_initialize***.</span><span class="sxs-lookup"><span data-stu-id="67728-200">The first call is to the function named ***gx_system_initialize***.</span></span> <span data-ttu-id="67728-201">Esta llamada siempre es necesaria antes de invocar otras API de GUIX para preparar la biblioteca de GUIX para su primer uso.</span><span class="sxs-lookup"><span data-stu-id="67728-201">This call is always required before any other GUIX APIs are invoked to prepare the GUIX library for first use.</span></span>

<span data-ttu-id="67728-202">A continuación, el ejemplo llama a la función ***gx_studio_display_configure***.</span><span class="sxs-lookup"><span data-stu-id="67728-202">Next, the example calls the function ***gx_studio_display_configure***.</span></span> <span data-ttu-id="67728-203">Esta función crea la instancia de visualización de GUIX, instala el lenguaje solicitado de la tabla de cadenas de aplicación, instala el tema solicitado desde los recursos de pantalla y devuelve un puntero a la ventana raíz que se creó para esta pantalla.</span><span class="sxs-lookup"><span data-stu-id="67728-203">This function creates the GUIX display instance, installs the requested language of the application string table, installs the requested theme from the display resources, and returns a pointer to the root window that has been created for this display.</span></span> <span data-ttu-id="67728-204">La ventana raíz se usa como elemento primario de todas las pantallas de nivel superior que mostrará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="67728-204">The root window is used as the parent of all top-level screens that our application will display.</span></span>

<span data-ttu-id="67728-205">A continuación, el ejemplo llama a \***gx_studio_named_widget_create** _ para crear una instancia de la pantalla _ \*_hello_world_\*\*.</span><span class="sxs-lookup"><span data-stu-id="67728-205">Next the example calls ***gx_studio_named_widget_create** _ to create an instance of our _ *_hello_world_** screen.</span></span> <span data-ttu-id="67728-206">Esta función usa las estructuras de datos y los recursos generados por GUIX Studio para crear una instancia de la pantalla, tal como se ha definido.</span><span class="sxs-lookup"><span data-stu-id="67728-206">This function uses the data structures and resource produces by GUIX Studio to create an instance of the screen as we have defined it.</span></span> <span data-ttu-id="67728-207">Pasamos el puntero de la ventana raíz como el segundo parámetro a esta llamada de función, lo que indica que queremos que la pantalla se conecte inmediatamente a la ventana raíz.</span><span class="sxs-lookup"><span data-stu-id="67728-207">We pass the root window pointer as the second parameter to this function call, meaning we want the screen to be immediately attached to the root window.</span></span> <span data-ttu-id="67728-208">El último parámetro es un puntero de retorno opcional que se puede usar si se desea mantener un puntero a la pantalla creada.</span><span class="sxs-lookup"><span data-stu-id="67728-208">The last parameter is an optional return pointer that can be used if we want to keep a pointer to the created screen.</span></span>

<span data-ttu-id="67728-209">A continuación, se llama a \***gx_widget_show** _, que hace que la ventana raíz y todos sus elementos secundarios, incluida la pantalla _ \*_hello_world_\*\*, sean visibles.</span><span class="sxs-lookup"><span data-stu-id="67728-209">Next ***gx_widget_show** _ is called, which makes the root window and all of its children, including the _ *_hello_world_** screen, visible.</span></span>

<span data-ttu-id="67728-210">Por último, el ejemplo llama a ***gx_system_start***.</span><span class="sxs-lookup"><span data-stu-id="67728-210">Finally, the example calls ***gx_system_start***.</span></span> <span data-ttu-id="67728-211">Esta función comienza a ejecutar el bucle de procesamiento de eventos del sistema GUIX.</span><span class="sxs-lookup"><span data-stu-id="67728-211">This function begins executing the GUIX system event processing loop.</span></span>

## <a name="build-and-run-the-example"></a><span data-ttu-id="67728-212">Creación y ejecución del ejemplo</span><span class="sxs-lookup"><span data-stu-id="67728-212">Build and Run the Example</span></span>

<span data-ttu-id="67728-213">Compilar y ejecutar el ejemplo son tareas específicas del entorno y las herramientas de compilación.</span><span class="sxs-lookup"><span data-stu-id="67728-213">Building and running the example is specific to your build tools and environment.</span></span> <span data-ttu-id="67728-214">Sin embargo, los pasos del proceso general se pueden definir de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="67728-214">However we can define the general process:</span></span>

1. <span data-ttu-id="67728-215">Crear un nuevo proyecto de directorio y aplicación.</span><span class="sxs-lookup"><span data-stu-id="67728-215">Create a new directory and application project</span></span>
1. <span data-ttu-id="67728-216">Agregar estos archivos al proyecto:</span><span class="sxs-lookup"><span data-stu-id="67728-216">Add these files to the project:</span></span>

    <span data-ttu-id="67728-217">**new_example_resources.c**</span><span class="sxs-lookup"><span data-stu-id="67728-217">**new_example_resources.c**</span></span>

    <span data-ttu-id="67728-218">**new_example_specification.c**</span><span class="sxs-lookup"><span data-stu-id="67728-218">**new_example_specification.c**</span></span>

    <span data-ttu-id="67728-219">**new_example.c**</span><span class="sxs-lookup"><span data-stu-id="67728-219">**new_example.c**</span></span>

1. <span data-ttu-id="67728-220">Agregar los archivos de compatibilidad en tiempo de ejecución de Win32 desde la ruta de instalación de GUIX Studio ***./win32_runtime***.</span><span class="sxs-lookup"><span data-stu-id="67728-220">Add the Win32 run-time support files from the GUIX Studio installation path ***./win32_runtime***.</span></span> <span data-ttu-id="67728-221">Incluye el encabezado Win32 de ThreadX y GUIX, así como los archivos de la biblioteca en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="67728-221">This includes the ThreadX and GUIX Win32 header and run-time library files.</span></span>
1. <span data-ttu-id="67728-222">Agregar la biblioteca Win32 de GUIX (***gx.lib***) al proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-222">Add the GUIX Win32 library (***gx.lib***) to the project</span></span>
1. <span data-ttu-id="67728-223">Agregar la biblioteca Win32 de ThreadX (***tx.lib***) al proyecto.</span><span class="sxs-lookup"><span data-stu-id="67728-223">Add the ThreadX Win32 library (***tx.lib***) to the project</span></span>
1. <span data-ttu-id="67728-224">Compilar, vincular y ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="67728-224">Compile, Link, and Run the application!</span></span>
