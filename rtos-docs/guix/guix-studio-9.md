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
# <a name="chapter-9-guix-studio-command-line"></a>Capítulo 9: Línea de comandos de GUIX Studio

GUIX Studio es compatible con la invocación de línea de comandos, que es útil para las canalizaciones de compilación necesarias para actualizar los archivos de salida generados por Studio.

## <a name="command-line-usage"></a>Uso de la línea de comandos

**Uso:** guix_studio \[OPCIÓN\] \[ARGUMENTO\]

Abre el proyecto *.gxp*.

Abre el proyecto de Studio y genera los archivos de salida deseados.


**Ejemplos:**

`guix_studio demo.gxp`  
Abre el proyecto "demo.gxp"


`guix_studio.exe –p demo.gxp`  
Abre el proyecto "demo.gxp"


`guix_studio.exe –n –p demo.gxp`  
Genera todos los archivos de salida del proyecto demo.gxp

`guix_studio.exe –n –r –p demo.gxp`  
Genera los archivo de recursos del proyecto demo.gxp


## <a name="command-line-options"></a>Opciones de la línea de comandos

```C
***-n --nogui***  
```

La opción "nogui" indica a GUIX Studio que se ejecute sin iniciar la interfaz de usuario basada en ventanas.

```C
***-o pathname***  
***--log***  
```

La opción log especifica un archivo de registro.

```C
***-b***  
***--binary***  
```

La opción binary genera un archivo de recursos binario en lugar de un archivo de C.

```C
***-d display1, display2***  
***--display***  
```

Opción de nombres para pantalla. Si se usa esta opción, solo los nombres de pantalla especificados se incluyen en los archivos de especificaciones o recursos generados. Si no se usa esta opción, se incluyen todos.

```C
***-t theme1, theme2***  
***--theme***  
```

Opción de nombres de tema. Si se usa esta opción, solo los nombres de tema especificados se incluyen en los archivos de especificaciones o recursos generados. Si no se usa esta opción, se incluyen todos los temas.

```C
***-l langage1, language2***  
***--language***  
```

Opción de nombres de lenguaje. Si se usa esta opción, los nombres de lenguaje especificados se incluyen en los archivos de especificaciones o recursos generados. En caso contrario, se incluyen todos los nombres de lenguaje.

```C
***-r [filename]***  
***--resource***  
```

La opción resource especifica que Studio debe generar un archivo de recursos de las pantallas, los temas y los lenguajes designados anteriormente.

```C
***-s [filename]***  
***--specification***  
```

La opción specification especifica que Studio debe generar un archivo de especificaciones de las pantallas, los temas y los lenguajes designados.

```C
***-p project_pathname***  
***--project***  
```

La opción de nombre de ruta de proyecto especifica el proyecto de ejemplo que se va a cargar.

```C
***-i [pathname]***  
***--import***  
```

Importa la cadena del archivo de formato xliff o csv.

***--big_endian***  
Genera datos de recursos en formato big-endian.
