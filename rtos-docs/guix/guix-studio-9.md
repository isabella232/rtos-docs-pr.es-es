---
title: Línea de comandos de GUIX Studio
description: GUIX Studio proporciona una invocación de línea de comandos que es útil para las canalizaciones de compilación necesarias para actualizar los archivos de salida generados por Studio.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9f9bfc67c524a77b5bf736407bf2ca372ce98308
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814914"
---
# <a name="chapter-9-guix-studio-command-line"></a><span data-ttu-id="f993d-103">Capítulo 9: Línea de comandos de GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="f993d-103">Chapter 9: GUIX Studio Command Line</span></span>

<span data-ttu-id="f993d-104">GUIX Studio es compatible con la invocación de línea de comandos, que es útil para las canalizaciones de compilación necesarias para actualizar los archivos de salida generados por Studio.</span><span class="sxs-lookup"><span data-stu-id="f993d-104">GUIX Studio supports command-line invocation,  which is useful for build pipelines that are required to update of the Studio-generated output files.</span></span>

## <a name="command-line-usage"></a><span data-ttu-id="f993d-105">Uso de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="f993d-105">Command-Line Usage</span></span>

<span data-ttu-id="f993d-106">**Uso:** guix_studio \[OPCIÓN\] \[ARGUMENTO\]</span><span class="sxs-lookup"><span data-stu-id="f993d-106">**Usage:** guix_studio \[OPTION\] \[ARGUMENT\]</span></span>

<span data-ttu-id="f993d-107">Abre el proyecto *.gxp*.</span><span class="sxs-lookup"><span data-stu-id="f993d-107">Open the *.gxp* project.</span></span>

<span data-ttu-id="f993d-108">Abre el proyecto de Studio y genera los archivos de salida deseados.</span><span class="sxs-lookup"><span data-stu-id="f993d-108">Open the Studio project and generate desired output files.</span></span>


<span data-ttu-id="f993d-109">**Ejemplos:**</span><span class="sxs-lookup"><span data-stu-id="f993d-109">**Examples:**</span></span>

`guix_studio demo.gxp`  
<span data-ttu-id="f993d-110">Abre el proyecto "demo.gxp"</span><span class="sxs-lookup"><span data-stu-id="f993d-110">Open "demo.gxp" project</span></span>


`guix_studio.exe –p demo.gxp`  
<span data-ttu-id="f993d-111">Abre el proyecto "demo.gxp"</span><span class="sxs-lookup"><span data-stu-id="f993d-111">Open "demo.gxp" project</span></span>


`guix_studio.exe –n –p demo.gxp`  
<span data-ttu-id="f993d-112">Genera todos los archivos de salida del proyecto demo.gxp</span><span class="sxs-lookup"><span data-stu-id="f993d-112">Generate all output files of demo.gxp project.</span></span>

`guix_studio.exe –n –r –p demo.gxp`  
<span data-ttu-id="f993d-113">Genera los archivo de recursos del proyecto demo.gxp</span><span class="sxs-lookup"><span data-stu-id="f993d-113">Generate resource files of demo.gxp project</span></span>


## <a name="command-line-options"></a><span data-ttu-id="f993d-114">Opciones de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="f993d-114">Command-Line Options</span></span>

```C
***-n --nogui***  
```

<span data-ttu-id="f993d-115">La opción "nogui"</span><span class="sxs-lookup"><span data-stu-id="f993d-115">The "nogui" option.</span></span> <span data-ttu-id="f993d-116">indica a GUIX Studio que se ejecute sin iniciar la interfaz de usuario basada en ventanas.</span><span class="sxs-lookup"><span data-stu-id="f993d-116">Tell GUIX Studio to run without starting the windowing UI interface.</span></span>

```C
***-o pathname***  
***--log***  
```

<span data-ttu-id="f993d-117">La opción log especifica un archivo de registro.</span><span class="sxs-lookup"><span data-stu-id="f993d-117">Log option, specify a log file.</span></span>

```C
***-b***  
***--binary***  
```

<span data-ttu-id="f993d-118">La opción binary</span><span class="sxs-lookup"><span data-stu-id="f993d-118">Binary resource option.</span></span> <span data-ttu-id="f993d-119">genera un archivo de recursos binario en lugar de un archivo de C.</span><span class="sxs-lookup"><span data-stu-id="f993d-119">Produces a binary resource file rather than a C file.</span></span>

```C
***-d display1, display2***  
***--display***  
```

<span data-ttu-id="f993d-120">Opción de nombres para pantalla.</span><span class="sxs-lookup"><span data-stu-id="f993d-120">Display names option.</span></span> <span data-ttu-id="f993d-121">Si se usa esta opción, solo los nombres de pantalla especificados se incluyen en los archivos de especificaciones o recursos generados.</span><span class="sxs-lookup"><span data-stu-id="f993d-121">If this option is used, then only the specified display names are included in any generated resource or specification files.</span></span> <span data-ttu-id="f993d-122">Si no se usa esta opción, se incluyen todos.</span><span class="sxs-lookup"><span data-stu-id="f993d-122">If this option is not used,  all displays are included.</span></span>

```C
***-t theme1, theme2***  
***--theme***  
```

<span data-ttu-id="f993d-123">Opción de nombres de tema.</span><span class="sxs-lookup"><span data-stu-id="f993d-123">Theme name(s) option.</span></span> <span data-ttu-id="f993d-124">Si se usa esta opción, solo los nombres de tema especificados se incluyen en los archivos de especificaciones o recursos generados.</span><span class="sxs-lookup"><span data-stu-id="f993d-124">If this option is used, then only the specified theme names are included in any generated resource or specification files.</span></span> <span data-ttu-id="f993d-125">Si no se usa esta opción, se incluyen todos los temas.</span><span class="sxs-lookup"><span data-stu-id="f993d-125">If this option is not used, all themes are included.</span></span>

```C
***-l langage1, language2***  
***--language***  
```

<span data-ttu-id="f993d-126">Opción de nombres de lenguaje.</span><span class="sxs-lookup"><span data-stu-id="f993d-126">Language name(s) option.</span></span> <span data-ttu-id="f993d-127">Si se usa esta opción, los nombres de lenguaje especificados se incluyen en los archivos de especificaciones o recursos generados.</span><span class="sxs-lookup"><span data-stu-id="f993d-127">If this option is used,  the specified language names are included in the generated resource or specification files.</span></span> <span data-ttu-id="f993d-128">En caso contrario, se incluyen todos los nombres de lenguaje.</span><span class="sxs-lookup"><span data-stu-id="f993d-128">Otherwise all language names are included.</span></span>

```C
***-r [filename]***  
***--resource***  
```

<span data-ttu-id="f993d-129">La opción resource especifica que Studio debe generar un archivo de recursos de las pantallas, los temas y los lenguajes designados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f993d-129">The resource option, specifies that Studio should produce a resource file for previously designated display(s), theme(s), and language(s).</span></span>

```C
***-s [filename]***  
***--specification***  
```

<span data-ttu-id="f993d-130">La opción specification especifica que Studio debe generar un archivo de especificaciones de las pantallas, los temas y los lenguajes designados.</span><span class="sxs-lookup"><span data-stu-id="f993d-130">The specification option, specify that studio should produce a specification file for designated display(s), theme(s), and language(s).</span></span>

```C
***-p project_pathname***  
***--project***  
```

<span data-ttu-id="f993d-131">La opción de nombre de ruta de proyecto especifica el proyecto de ejemplo que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="f993d-131">Project pathname option, specify the example project to be loaded.</span></span>

```C
***-i [pathname]***  
***--import***  
```

<span data-ttu-id="f993d-132">Importa la cadena del archivo de formato xliff o csv.</span><span class="sxs-lookup"><span data-stu-id="f993d-132">Import string from xliff or csv format file.</span></span>

<span data-ttu-id="f993d-133">***--big_endian***</span><span class="sxs-lookup"><span data-stu-id="f993d-133">***--big_endian***</span></span>  
<span data-ttu-id="f993d-134">Genera datos de recursos en formato big-endian.</span><span class="sxs-lookup"><span data-stu-id="f993d-134">Generate resource data in big-endian format.</span></span>
