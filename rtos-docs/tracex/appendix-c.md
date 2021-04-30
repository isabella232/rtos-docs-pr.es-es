---
title: 'Apéndice C: Utilidades de línea de comandos de DOS'
description: La instalación de Azure RTOS TraceX incluye tres utilidades de línea de comandos de DOS en el subdirectorio Utilities.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: e1ec852a97a6735a4a055706f55283950d3f8d6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815934"
---
# <a name="appendix-c---dos-command-line-utilities"></a>Apéndice C: Utilidades de línea de comandos de DOS

La instalación de Azure RTOS TraceX incluye tres utilidades de línea de comandos de DOS en el subdirectorio ***Utilities***.

A continuación se enumeran las utilidades suministradas:

| **Utilidad**                              | **Propósito**                               | **Definiciones de línea de comandos** |
| -------------------------------- | ----------------------------------------- | ---------------------------- |
| **ea2tracex.exe**                | Convierte al formato de archivo de seguimiento de TraceX el archivo de seguimiento ea2tracex generado por ThreadX en la asociación del archivo original con el archivo convertido de las herramientas GHS. La solución ThreadX para herramientas GHS produce un formato de seguimiento diferente al de la solución para herramientas no sujetas a GHS, motivo por el que es necesaria una utilidad de conversión. | ``` > eatracex original_file converted_file <cr> ``` | 
**hex2tracex.exe** | Convierte un archivo de seguimiento generado por ThreadX, pero volcado de la herramienta de desarrollo en formato HEX de Intel, al formato de archivo de seguimiento binario de TraceX. TraceX V5 y versiones posteriores pueden abrir archivos HEX sin convertirlos. | ``` hex2tracex hex_file converted_file <cr> ``` | 
**mot2tracex.exe** | Convierte un archivo de seguimiento generado por ThreadX, pero volcado de la herramienta de desarrollo en formato S-Record de Motorola, al formato de archivo de seguimiento binario de TraceX. TraceX V5 y versiones posteriores pueden abrir archivos S-Record sin convertirlos. | ``` > mot2tracex mot_file converted_file <cr> ```|