---
title: Guía de usuario de GUIX Studio
description: En esta guía se proporciona información exhaustiva sobre GUIX Studio, el entorno de desarrollo rápido de interfaz de usuario basado en Microsoft Windows diseñado específicamente para la biblioteca en tiempo de ejecución de GUIX de Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 2c36fb794816cb1acd51ec81f48c0dabe509336f27914050b6206f19bf8ceeff
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789840"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a>Capítulo 1: Introducción a Azure RTOS GUIX Studio

Azure RTOS GUIX Studio es un entorno de desarrollo de interfaz de usuario rápido basado en Microsoft Windows diseñado específicamente para la biblioteca en tiempo de ejecución de GUIX de Microsoft.

Los desarrolladores de UI integradas pueden usar el diseñador de pantalla WYSIWYG de GUIX Studio para crear y actualizar rápidamente interfaces de usuario integradas utilizando el entorno de ejecución de GUIX. Los diseños de GUIX Studio se guardan y mantienen en un archivo del proyecto de GUIX Studio, que tiene la extensión .gxp. Cuando el diseño está listo para su ejecución en el destino, Guix Studio genera código de C que contiene toda la información y el código de la interfaz de usuario que se necesitan.

## <a name="guix-studio-requirements"></a>Requisitos de GUIX Studio

Para funcionar correctamente, GUIX Studio de Microsoft requiere *Windows XP* (o superior). El sistema debe tener un mínimo de 200 de RAM, 2 B de espacio disponible en el disco duro y una pantalla de 1024 x 768 con 256 colores como mínimo. Además, la aplicación insertada se debe ejecutar en *ThreadX/GUIX v6.0* o posterior.

Si desea poder compilar y ejecutar la aplicación de UI integrada como un ejecutable independiente de Microsoft Windows, también necesita un compilador o un entorno de compilación que pueda compilar el código fuente de C para convertirse en un producto ejecutable de Microsoft Windows. El paquete de evaluación incluido con GUIX Studio también incluye archivos de proyecto y soluciones compatibles con Visual Studio 2019 para cada una de las aplicaciones de ejemplo proporcionadas. Si usa un compilador diferente, deberá crear sus propios archivos de proyecto, generar archivos para crear sus aplicaciones de ejemplo o ponerse en contacto con el soporte técnico en https://aka.ms/azrtos-support.

## <a name="guix-studio-constraints"></a>Restricciones de GUIX Studio

La herramienta de diseño de UI de GUIX Studio tiene varias restricciones, como se indica a continuación:

- Un máximo de 4 publicaciones por proyecto.
- Un máximo de 100 000 widgets por proyecto de GUIX Studio.
- Un máximo de 100 000 recursos distintos, por ejemplo, colores, fuentes, mapas de píxeles, cadenas, etc.