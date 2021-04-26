---
title: Acerca de la guía del usuario de Azure RTOS NetX Duo
description: Esta guía contiene información completa acerca de Azure RTOS NetX Duo, la pila de red dual IPv4/IPv6 de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814878"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a>Acerca de la guía del usuario de Azure RTOS NetX Duo

Esta guía contiene información completa acerca de Azure RTOS NetX Duo, la pila de red dual IPv4/IPv6 de alto rendimiento de Microsoft. 

Está destinada a desarrolladores de software insertado en tiempo real familiarizados con los conceptos básicos de redes, Azure RTOS ThreadX y el lenguaje de programación C.

## <a name="organization"></a>Organización

[Capítulo 1](chapter1.md): presenta Azure RTOS NetX Duo.

[Capítulo 2](chapter2.md): proporciona los pasos básicos para instalar y usar Azure RTOS NetX Duo con la aplicación ThreadX.

[Capítulo 3](chapter3.md): proporciona una visión general funcional del sistema Azure RTOS NetX Duo e información básica sobre los estándares de redes TCP/IP.

[Capítulo 4](chapter4.md): ofrece información detallada de la interfaz de la aplicación para Azure RTOS NetX Duo.

[Capítulo 5](chapter5.md): describe los controladores de red para Azure RTOS NetX Duo.

[Apéndice A](appendix-a.md): servicios de Azure RTOS NetX Duo.

[Apéndice B](appendix-b.md): constantes de Azure RTOS NetX Duo.

[Apéndice C](appendix-c.md): tipos de datos de Azure RTOS NetX Duo.

[Apéndice D](appendix-d.md): API de socket compatible con BSD.

[Apéndice E](appendix-e.md): gráfico ASCII.

## <a name="guide-conventions"></a>Convenciones de la guía

Cursiva: el tipo de letra denota títulos de libros, destaca palabras importantes e indica variables.

**Negrita**: el tipo de letra indica nombres de archivo, palabras clave y, además, destaca palabras importantes y variables.

> [!IMPORTANT]
> Los símbolos de información llaman la atención sobre información importante o adicional que podría afectar al rendimiento o al funcionamiento.
 
> [!WARNING]
> Los símbolos de advertencia llaman la atención sobre situaciones que los desarrolladores deben intentar evitar, ya que podrían dar lugar a errores irrecuperables.

## <a name="azure-rtos-netx-duo-data-types"></a>Tipos de datos de Azure RTOS NetX Duo

Además de los tipos de datos de estructura de control personalizados de Azure RTOS NetX Duo, hay varios tipos de datos especiales que se usan en las interfaces de llamada de servicio de Azure RTOS NetX Duo. Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente. De esta manera, se garantiza la portabilidad entre diferentes compiladores de C. La implementación exacta se hereda de ThreadX y se puede encontrar en el archivo ***tx_port.h*** incluido en la distribución de ThreadX.

A continuación se muestra una lista de los tipos de datos de llamada de servicio de Azure RTOS NetX Duo y sus significados asociados:

**UINT**: entero sin signo básico. Este tipo debe admitir datos sin signo de 32 bits, pero se asigna al tipo de datos sin signo más conveniente.  
**ULONG**: tipo largo sin signo. Este tipo debe admitir datos sin signo de 32 bits.
**VOID**: casi siempre equivale al tipo void del compilador.  
**CHAR**: suele ser un tipo de carácter de 8 bits estándar.  

Se usan tipos de datos adicionales en el origen de datos de Azure RTOS NetX Duo. Se encuentran en los archivos ***tx_port.h** _ o _ *_nx_port.h_**.

## <a name="customer-support-center"></a>Centro de soporte al cliente

Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos. Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:

1. Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.
2. Una descripción detallada de los cambios en la aplicación o en Azure RTOS NetX Duo que precedieron al problema.
3. El contenido de las cadenas _tx_version_id y _nx_version_id que se encuentran en los archivos tx_port.h y nx_port.h de la distribución. Estas cadenas nos proporcionan información valiosa sobre el entorno en tiempo de ejecución.
4. El contenido en la RAM de las siguientes variables ULONG:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Estas variables nos proporcionarán información sobre cómo se compilaron las bibliotecas de Azure RTOS ThreadX y de Azure RTOS NetX Duo.

5. Un búfer de seguimiento capturado inmediatamente después de que se haya detectado el problema. Esto se consigue mediante la compilación de las bibliotecas de Azure RTOS ThreadX y Azure RTOS NetX Duo con TX_ENABLE_EVENT_TRACE y una llamada a tx_trace_enable con la información del búfer de seguimiento.
