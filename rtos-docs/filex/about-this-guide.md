---
title: Manual del usuario de Azure RTOS FileX
description: Esta guía contiene información exhaustiva sobre Azure RTOS FileX, el sistema de archivos en tiempo real de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48fe70fc3cff6e656328d38b2583116e58a6c98510d5f0554f81a7b728f95457
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782411"
---
# <a name="about-this-filex-user-guide"></a>Acerca de esta guía del usuario de FileX

Esta guía contiene información exhaustiva sobre Azure RTOS FileX, el sistema de archivos incrustado en tiempo real de alto rendimiento de Microsoft. Para sacar el máximo partido de esta guía, debe estar familiarizado con las funciones estándar del sistema operativo en tiempo real, los servicios del sistema de archivos FAT y el lenguaje de programación C.

## <a name="organization"></a>Organización

[Capítulo 1](chapter1.md) Presenta Azure RTOS FileX.

[Capítulo 2](chapter2.md) Proporciona los pasos básicos para instalar y usar Azure RTOS FileX con su aplicación de Azure RTOS ThreadX.

[Capítulo 3](chapter3.md) Proporciona una visión general funcional del sistema de Azure RTOS FileX y la información básica sobre los formatos del sistema de archivos FAT.

[Capítulo 4](chapter4.md) : detalla la interfaz de la aplicación para Azure RTOS FileX.

[Capítulo 5](chapter5.md) Describe el controlador de RAM de Azure RTOS FileX proporcionado y cómo escribir sus propios controladores personalizados de Azure RTOS FileX.

[Capítulo 6](chapter6.md) Describe del módulo de tolerancia a errores de Azure RTOS FileX.

[Apéndice A](appendix-a.md) Servicios de Azure RTOS FileX

[Apéndice B](appendix-b.md) Constantes de Azure RTOS FileX

[Apéndice C](appendix-c.md) Tipos de datos de Azure RTOS FileX

[Apéndice D](appendix-d.md) Gráficos ASCII

## <a name="guide-conventions"></a>Convenciones de la guía

*Cursiva*: el tipo de letra denota títulos de libros, destaca palabras importantes e indica variables.

**Negrita**: el tipo de letra indica nombres de archivo, palabras clave y, además, destaca palabras importantes y variables.

> [!NOTE]
> Los símbolos de información llaman la atención sobre información importante o adicional que podría afectar al rendimiento o al funcionamiento.

> [!IMPORTANT]
> Los símbolos de advertencia llaman la atención sobre situaciones que los desarrolladores deben intentar evitar, ya que podrían dar lugar a errores irrecuperables.

## <a name="filex-data-types"></a>Tipos de datos FileX

Además de los tipos de datos personalizados de la estructura de control de Azure RTOS FileX, hay varios tipos de datos especiales que se usan en las interfaces de llamada a servicios de Azure RTOS FileX. Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente. De esta manera, se garantiza la portabilidad entre diferentes compiladores de C. La implementación exacta se hereda de Azure RTOS ThreadX y se puede encontrar en el archivo tx_port.h incluido en la distribución de Azure RTOS ThreadX.

A continuación se muestra una lista de los tipos de datos de llamada a servicios de Azure RTOS FileX y sus significados asociados.

| Tipo  | Descripción  |
|---|---|
| **UINT** | Entero sin signo básico. Este tipo debe admitir datos sin signo de 8 bits, pero se asigna al tipo de datos sin signo más conveniente. |
| **ULONG** | Tipo largo sin signo. Este tipo debe admitir datos sin signo de 32 bits. |
| **VOID** | Casi siempre equivale al tipo void del compilador. |
| **CHAR** | Suele ser un tipo de carácter de 8 bits estándar. |
| **ULONG64** | Tipo de datos entero sin signo de 64 bits. |

Se usan tipos de datos adicionales en el origen de FileX. Se encuentran en los archivos ***tx_port.h** _ o _ *_fx_port.h_**.

## <a name="customer-support-center"></a>Centro de soporte al cliente

Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos. Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:

1. Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.
2. Una descripción detallada de los cambios en la aplicación o en FileX que precedieron al problema.
3. El contenido de las cadenas_tx_version_id y _fx_version_id que se encuentran en los archivos **tx_port.h**_ y _ *_fx_port.h_** de la distribución. Estas cadenas nos proporcionan información valiosa sobre el entorno en tiempo de ejecución.
4. El contenido en la RAM de las siguientes variables **ULONG**. Estas variables nos proporcionarán información sobre cómo se compilaron las bibliotecas de ThreadX y FileX:

    **_tx_build_options**

    **_fx_system_build_options1**

    **_fx_system_build_options2**

    **_fx_system_build_options3**
