---
title: Acerca de esta guía
description: En esta guía se proporciona información completa sobre Azure RTOS ThreadX SMP, el kernel en tiempo real insertado de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2399666b5b4d7c34db50d539e200c90f06f7235f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814350"
---
# <a name="about-this-guide"></a>Acerca de esta guía

En esta guía se proporciona información completa sobre Azure RTOS ThreadX SMP, el kernel en tiempo real insertado de alto rendimiento de Microsoft.

Está diseñado para el desarrollador de software en tiempo real insertado. El desarrollador debe estar familiarizado con las funciones estándar del sistema operativo en tiempo real y el lenguaje de programación C.

## <a name="organization"></a>Organización

| Capítulo       | Información general                    |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| **Capítulo 1** | Proporciona información general básica de ThreadX SMP y su relación con el desarrollo insertado en tiempo real.           |
| **Capítulo 2** | Proporciona los pasos básicos para instalar y usar ThreadX SMP en la aplicación *directamente*.           |
| **Capítulo 3** | Describe en detalle el funcionamiento funcional de ThreadX SMP, el kernel SMP en tiempo real de alto rendimiento.    |
| **Capítulo 4** | Ofrece información detallada de la interfaz de la aplicación para ThreadX SMP.                                                        |
| **Capítulo 5** | Describe la escritura de controladores de E/S para aplicaciones de ThreadX SMP.                                                |
| **Capítulo 6** | Describe la aplicación de demostración que se proporciona con cada paquete de soporte del procesador de ThreadX SMP. |
| **Apéndice A** | API de Thread SMP        |
| **Apéndice B** | Constantes de ThreadX SMP  |
| **Apéndice C** | Tipos de datos de ThreadX SMP |
| **Apéndice D** | Gráfico de ASCII            |

## <a name="guide-conventions"></a>Convenciones de la guía

- *Cursiva* - *el tipo de letra denota títulos de libros, destaca palabras importantes e indica variables.*
- **Negrita** - **el tipo de letra denota nombres de archivo y palabras clave, y además destaca palabras y variables importantes.**

> [!IMPORTANT]
> Los símbolos de información destacan información importante o adicional que podría afectar al rendimiento o a la funcionalidad.

> [!WARNING]
> Los símbolos de advertencia se refieren a situaciones en las que los desarrolladores deben tener cuidado de evitar, ya que podrían provocar errores irrecuperables.

## <a name="threadx-smp-data-types"></a>Tipos de datos de ThreadX SMP

Además de los tipos de datos de estructura de control personalizados de ThreadX SMP, hay una serie de tipos de datos especiales que se usan en las interfaces de llamada de servicio de ThreadX SMP. Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente. De esta manera, se garantiza la portabilidad entre diferentes compiladores de C. La implementación exacta se puede encontrar en el archivo ***tx_port.h*** incluido en el disco de distribución.

A continuación se muestra una lista de los tipos de datos de llamada de servicio de ThreadX SMP y sus significados asociados:

| Tipo de datos          | Significado                                                          |
| --------- | --------------------------------------------------------- |
| **UINT**  | Entero sin signo básico. Este tipo debe admitir datos sin signo de 8 bits, pero se asigna al tipo de datos sin signo más conveniente. |
| **ULONG** | Tipo largo sin signo. Este tipo debe admitir datos sin signo de 32 bits.                                                                     |
| **VOID**  | Casi siempre equivale al tipo void del compilador.                                                                                |
| **CHAR**  | Suele ser un tipo de carácter de 8 bits estándar.                                                                                          |

Se usan tipos de datos adicionales en el origen de ThreadX SMP. También se encuentran en el archivo ***tx_port.h***.

## <a name="customer-support-center"></a>Centro de soporte al cliente

Correo electrónico de soporte técnico: [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Página web: azure.com/rtos

### <a name="latest-product-information"></a>Información del producto más reciente

Visite el sitio web azure.com/rtos y seleccione la opción de menú "Soporte técnico" para encontrar la información de soporte técnico en línea más reciente, incluida información sobre las versiones de producto de ThreadX SMP más recientes.

### <a name="what-we-need-from-you"></a>Qué necesitamos de usted

Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de forma más eficaz:

1. Una descripción detallada del problema, incluida la frecuencia de repetición y si se puede reproducir de forma fiable.
2. Una descripción detallada de los cambios en la aplicación o en ThreadX SMP que precedieron al problema.
3. Contenido de la cadena de * **_tx_version_id** que se encuentra en el archivo _ *_tx_port.h_** de la distribución. Esta cadena nos proporcionará información de valor sobre el entorno en tiempo de ejecución.
4. El contenido de la RAM de la variable ***_tx_build_options*** ULONG. Esta variable nos proporcionará información sobre cómo se compiló la biblioteca de ThreadX SMP.

### <a name="where-to-send-comments-about-this-guide"></a>Dónde enviar comentarios acerca de esta guía

Envíe por correo electrónico cualquier comentario y sugerencia al Centro de soporte al cliente en [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Escriba "Guía de usuario de ThreadX SMP" en la línea de asunto.
