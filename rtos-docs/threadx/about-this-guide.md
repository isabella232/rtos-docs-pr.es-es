---
title: Acerca de la guía de Azure RTOS ThreadX
description: En esta guía se proporciona información exhaustiva sobre Azure RTOS ThreadX, el kernel de alto rendimiento en tiempo real de Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28f088409fdd5e2c075cbf90b21d3d260c811806066e74bffc395207cde0239c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802131"
---
# <a name="about-the-azure-rtos-threadx-guide"></a>Acerca de la guía de Azure RTOS ThreadX

En esta guía se proporciona información exhaustiva sobre Azure RTOS ThreadX, el kernel de alto rendimiento en tiempo real de Microsoft. 

Está diseñada para el desarrollador de software insertado en tiempo real. El desarrollador debe estar familiarizado con las funciones estándar del sistema operativo en tiempo real y el lenguaje de programación C.

## <a name="organization"></a>Organización

[Capítulo 1](chapter1.md): ofrece una introducción básica a Azure RTOS ThreadX y su relación con el desarrollo insertado en tiempo real

[Capítulo 2](chapter2.md): proporciona los pasos básicos para instalar y usar Azure RTOS ThreadX en la aplicación *desde el primer momento*

[Capítulo 3](chapter3.md): describe en detalle el funcionamiento de Azure RTOS ThreadX, el kernel de alto rendimiento en tiempo real

[Capítulo 4](chapter4.md): detalla la interfaz de la aplicación para Azure RTOS ThreadX

[Capítulo 5](chapter5.md): describe los controladores de E/S de escritura para aplicaciones de Azure RTOS ThreadX

[Capítulo 6](chapter6.md): describe la aplicación de demostración que se proporciona con cada paquete de soporte técnico del procesador Azure RTOS ThreadX

[Apéndice A](appendix-a.md): API de Azure RTOS ThreadX

[Apéndice B](appendix-b.md): constantes de Azure RTOS ThreadX

[Apéndice C](appendix-c.md): tipos de datos de Azure RTOS ThreadX

[Apéndice D](appendix-d.md): gráficos ASCII

## <a name="guide-conventions"></a>Convenciones de la guía

*Cursiva*: el tipo de letra denota títulos de libros, destaca palabras importantes e indica parámetros.

**Negrita**: el tipo de letra denota palabras clave, constantes, nombres de tipos, elementos de la interfaz de usuario, nombres de variables y destaca palabras importantes.

***Cursiva y negrita***: el tipo de letra denota nombres de archivo y nombres de función.

> [!IMPORTANT]
> Los símbolos de información llaman la atención sobre información importante o adicional que podría afectar al rendimiento o al funcionamiento.

> [!WARNING]
> Los símbolos de advertencia llaman la atención sobre situaciones que los desarrolladores deben intentar evitar, ya que podrían dar lugar a errores irrecuperables.

## <a name="azure-rtos-threadx-data-types"></a>Tipos de datos de Azure RTOS ThreadX

Además de los tipos de datos personalizados de la estructura de control de Azure RTOS ThreadX, hay varios tipos de datos especiales que se usan en las interfaces de llamada a servicios de Azure RTOS ThreadX. Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente. De esta manera, se garantiza la portabilidad entre diferentes compiladores de C. La implementación exacta se puede encontrar en el archivo ***tx_port.h*** incluido en el origen.

A continuación se muestra una lista de los tipos de datos de llamada a servicios de Azure RTOS ThreadX y sus significados asociados:

| Tipo de datos  | Descripción |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **UINT** | Entero sin signo básico. Este tipo debe admitir datos sin signo de 8 bits, pero se asigna al tipo de datos sin signo más conveniente. |
| **ULONG** | Tipo largo sin signo. Este tipo debe admitir datos sin signo de 32 bits. |
| **VOID** | Casi siempre equivale al tipo void del compilador. |
| **CHAR** | Suele ser un tipo de carácter de 8 bits estándar. |
|  |  |

En el origen de Azure RTOS ThreadX se usan tipos de datos adicionales. También se encuentran en el archivo ***tx_port.h***.

## <a name="customer-support-center"></a>Centro de soporte al cliente

Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos. Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:

1. Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.
2. Una descripción detallada de los cambios en la aplicación o en Azure RTOS ThreadX que han precedido al problema.
3. Contenido de la cadena *_tx_version_id* que se encuentra en el archivo *tx_port.h* de la distribución. Esta cadena nos proporciona información valiosa sobre el entorno en tiempo de ejecución.
4. El contenido de la RAM de la variable **_tx_build_options** **ULONG**. Esta variable nos proporciona información sobre cómo se ha compilado la biblioteca de Azure RTOS ThreadX.
