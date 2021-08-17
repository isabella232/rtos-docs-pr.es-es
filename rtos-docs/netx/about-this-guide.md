---
title: Acerca de la guía del usuario de Azure RTOS NetX
description: Esta guía contiene información completa acerca de Azure RTOS NetX, la pila de red de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d77997e8c5bac598f382e1169a56727af09ab108f57c90cc6265df0691b5926
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796419"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a>Acerca de la guía del usuario de Azure RTOS NetX

Esta guía contiene información completa acerca de Azure RTOS NetX, la pila de red de alto rendimiento de Microsoft.

Está destinado a desarrolladores de software insertado en tiempo real familiarizados con los conceptos básicos de redes, Azure RTOS ThreadX y el lenguaje de programación C.

## <a name="organization"></a>Organización

[Capítulo 1](chapter1.md): presenta Azure RTOS NetX.

[Capítulo 2](chapter2.md): proporciona los pasos básicos para instalar y usar Azure RTOS NetX con la aplicación ThreadX.

[Capítulo 3](chapter3.md): proporciona una visión general funcional del sistema Azure RTOS NetX e información básica sobre los estándares de redes TCP/IP.

[Capítulo 4](chapter4.md): ofrece información detallada de la interfaz de la aplicación para Azure RTOS NetX.

[Capítulo 5](chapter5.md): describe los controladores de red para Azure RTOS NetX.

[Apéndice A](appendix-a.md): servicios de Azure RTOS NetX

[Apéndice B](appendix-b.md): constantes de Azure RTOS NetX

[Apéndice C](appendix-c.md): tipos de datos de Azure RTOS NetX

[Apéndice D](appendix-d.md): API de socket compatible con BSD

[Apéndice E](appendix-e.md): tabla ASCII

## <a name="azure-rtos-netx-data-types"></a>Tipos de datos de Azure RTOS NetX

Además de los tipos de datos de estructura de control personalizados de Azure RTOS NetX, hay varios tipos de datos especiales que se usan en las interfaces de llamada de servicio de Azure RTOS NetX. Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente. De esta manera, se garantiza la portabilidad entre diferentes compiladores de C. La implementación exacta se hereda de ThreadX y se puede encontrar en el archivo ***tx_port.h*** incluido en la distribución de ThreadX.

A continuación se muestra una lista de los tipos de datos de llamada de servicio de Azure RTOS NetX y sus significados asociados:

| Tipo de datos | Descripción  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **UINT**  | Entero sin signo básico. Este tipo debe admitir datos sin signo de 32 bits, pero se asigna al tipo de datos sin signo más conveniente. |
| **ULONG** | Tipo largo sin signo. Este tipo debe admitir datos sin signo de 32 bits.                                                                      |
| **VOID**  | Casi siempre equivale al tipo void del compilador.                                                                                 |
| **CHAR**  | Suele ser un tipo de carácter de 8 bits estándar.                                                                                           |

Se usan tipos de datos adicionales en el código fuente de Azure RTOS NetX. Se encuentran en los archivos ***tx_port.h** _ o _ *_nx_port.h_**.

## <a name="customer-support-center"></a>Centro de soporte al cliente

Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos. Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:

1. Una descripción detallada del problema, incluida la frecuencia de repetición y si se puede reproducir de forma fiable.

2. Una descripción detallada de los cambios en la aplicación o en Azure RTOS NetX que precedieron al problema.

3. El contenido de las cadenas **_tx_version_id** y **_nx_version_id** que se encuentran en los archivos **_tx_port.h_ *_ y _* _nx_port.h_** de la distribución. Estas cadenas nos proporcionarán información valiosa sobre el entorno en tiempo de ejecución.

4. El contenido de la memoria RAM de las siguientes variables **ULONG**:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Estas variables nos proporcionarán información sobre cómo se compilaron las bibliotecas de Azure RTOS ThreadX y de Azure RTOS NetX.

5. Un búfer de seguimiento capturado inmediatamente después de que se haya detectado el problema. Esto se consigue mediante la compilación de las bibliotecas de Azure RTOS ThreadX y Azure RTOS NetX con **TX_ENABLE_EVENT_TRACE** y una llamada a **tx_trace_enable** con la información del búfer de seguimiento. Consulte la guía del usuario de Azure RTOS TraceX para más información.
