---
title: 'Capítulo 1: Información general de Azure RTOS LevelX'
description: Azure RTOS LevelX proporciona instalaciones de redistribución del uso de flash NAND y NOR en aplicaciones insertadas.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 045446fec74164f125bc0ad27e8b7a904be14ab2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814902"
---
# <a name="chapter-1---overview-of-azure-rtos-levelx"></a>Capítulo 1: Información general de Azure RTOS LevelX

Azure RTOS LevelX proporciona instalaciones de redistribución del uso de flash NAND y NOR en aplicaciones insertadas. Dado que la memoria flash NAND y NOR solo se puede borrar un número finito de veces, es fundamental distribuir el uso de la memoria flash uniformemente. Esto se suele denominar "desgaste de la nivelación" y es el objetivo de LevelX.

El algoritmo que elige el bloque flash que se va a reutilizar se basa principalmente en el recuento de borrado, pero no en su totalidad. No se puede elegir el bloque con el menor número de borrado si hay otro bloque con un recuento de borrado dentro de un delta aceptable del recuento mínimo de borrados y tiene un número mayor de asignaciones obsoletas. En tales casos, el bloque con el mayor número de asignaciones obsoletas se borrará y reutilizará, con lo que se ahorrará la sobrecarga de mover entradas de asignación válidas.

LevelX admite varias instancias de las partes NAND o NOR, es decir, la aplicación puede usar instancias independientes de LevelX en la misma aplicación. Cada instancia requiere su propio bloque de control proporcionado por la aplicación, así como su propio controlador flash.

LevelX presenta al usuario una matriz de sectores lógicos que se asignan a la memoria flash física dentro de LevelX. Para mejorar el rendimiento, LevelX también proporciona una memoria caché de las asignaciones de sectores lógicos más recientes. El programador define el tamaño de esta memoria caché. Las aplicaciones pueden usar LevelX junto con FileX o pueden leer o escribir sectores lógicos directamente. LevelX no tiene ninguna dependencia en FileX y muy poca dependencia en ThreadX (solo se usan tipos de datos ThreadX primitivos).

LevelX está diseñado para la tolerancia a errores. Las actualizaciones de flash se realizan en un proceso de varios pasos que se puede interrumpir en cada paso. LevelX recupera automáticamente el estado óptimo durante la siguiente operación.

LevelX requiere un controlador flash para el acceso físico a la memoria Flash subyacente. Se proporcionan los controladores de ejemplo simulados NAND y NOR, y se pueden usar como un buen punto de partida para implementar los controladores de LevelX reales. Además, los requisitos de los controladores se detallan más adelante en esta documentación.

En los siguientes capítulos se describe la operación funcional para la compatibilidad de LevelX con NAND y NOR.
