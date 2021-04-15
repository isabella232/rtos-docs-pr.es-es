---
title: Guía del usuario de Azure RTOS GUIX
description: Esta guía contiene información exhaustiva sobre Azure RTOS GUIX, el producto de GUI de alto rendimiento de Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b7af0fba59b599c9c8db3ab80a3271eacfd11992
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815581"
---
# <a name="about-guix-user-guide"></a>Acerca de la guía del usuario de GUIX

Esta guía contiene información exhaustiva sobre Azure RTOS GUIX, el producto de GUI de alto rendimiento de Microsoft. Está destinada a los desarrolladores de software insertado en tiempo real que están familiarizados con los conceptos básicos de GUI, Azure RTOS ThreadX y el lenguaje de programación C.

## <a name="organization"></a>Organización

[Capítulo 1: Introducción a Azure RTOS GUIX](chapter-1.md)

[Capítulo 2: Instalación y uso de Azure RTOS GUIX](chapter-2.md)

[Capítulo 3: Introducción funcional a Azure RTOS GUIX](chapter-3.md)

[Capítulo 4: Descripción de los servicios de Azure RTOS GUIX](chapter-4.md)

[Capítulo 5: Controladores de pantalla de Azure RTOS GUIX](chapter-5.md)  

[Ejemplo de Azure RTOS GUIX](guix-example.md)

[Apéndice A: Definiciones de color de Azure RTOS GUIX](appendix-a.md)

[Apéndice B: Formatos de color de Azure RTOS GUIX](appendix-b.md)

[Apéndice C: Estilos de widget de Azure RTOS GUIX](appendix-c.md)

[Apéndice D: Atributos de pincel, lienzo y degradado de Azure RTOS GUIX](appendix-d.md)

[Apéndice E: Descripción de eventos de Azure RTOS GUIX](appendix-e.md)

[Apéndice F: Servicios de enlace de RTOS de Azure RTOS GUIX](appendix-f.md)

[Apéndice G: Estructura de fuente de Azure RTOS GUIX](appendix-g.md)

[Apéndice H: Marcas de configuración de tiempo de compilación de Azure RTOS GUIX](appendix-h.md)

[Apéndice I: Estructuras de información de Azure RTOS GUIX](appendix-i.md)

## <a name="guide-conventions"></a>Convenciones de la guía

*Cursiva*: el tipo de letra denota títulos de libros, destaca palabras importantes e indica variables.

**Negrita**: el tipo de letra indica nombres de archivo, palabras clave y, además, destaca palabras importantes y variables.

> [!IMPORTANT]
> Los símbolos de información llaman la atención sobre información importante o adicional que podría afectar al rendimiento o al funcionamiento.

## <a name="azure-rtos-guix-data-types"></a>Tipos de datos de Azure RTOS GUIX

Además de los tipos de datos personalizados de la estructura de control de Azure RTOS GUIX, hay varios tipos de datos especiales que se usan en las interfaces de llamada a servicios de Azure RTOS GUIX. Estos tipos de datos especiales se asignan directamente a los tipos de datos del compilador de C subyacente. De esta manera, se garantiza la portabilidad entre diferentes compiladores de C. La implementación exacta se hereda de ThreadX y se puede encontrar en el archivo ***tx_port.h*** incluido en la distribución de ThreadX.

A continuación se muestra una lista de los tipos de datos de llamada a servicios de Azure RTOS GUIX y sus significados asociados:

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **UINT**             | Entero sin signo básico. Este tipo se asigna al tipo de datos sin signo más conveniente.                                |
| **INT**              | Entero con signo básico. Este tipo se asigna al tipo de datos con signo más conveniente.                                    |
| **ULONG**            | Tipo largo sin signo. Este tipo debe admitir datos sin signo de 32 bits.                                                      |
| **VOID**             | Casi siempre equivale al tipo void del compilador.                                                                 |
| **GX_CHAR**         | La mayoría de las veces se usa typedef como tipo de carácter definido por el compilador.                                                               |
| **GX_BYTE**          | Tipo con signo de 8 bits.                                                                                                    |
| **GX_UBYTE**         | Tipo sin signo de 8 bits.                                                                                                  |
| **GX_VALUE**        | Tipo con signo de 16 o 32 bits. Se define según sea necesario para obtener el mejor rendimiento en el sistema de destino.                                |
| **GX_FIXED_VAL**   | Tipo de datos numérico de punto fijo.                                                                                        |
| **GX_RESOURCE_ID** | Tipo largo sin signo.                                                                                                   |
| **GX_COLOR**        | Tipo largo sin signo.                                                                                                   |
| **GX_STRING**       | Estructura que contiene GX_CHAR \*gx_string_ptr y UINT gx_string_length.                                          |
| **GX_POINT**        | Estructura que contiene gx_point_x y gx_point_y.                                                                   |
| **GX_RECTANGLE**    | Estructura que contiene los campos gx_rectangle_left, gx_rectangle_top, gx_rectangle_right y gx_rectangle_bottom. |
| **GX_GLYPH**        | Estructura que contiene métricas de glifo.                                                                                   |
| **GX_FONT**         | Estructura que contiene métricas de fuente.                                                                                    |
| **GX_BRUSH**        | Estructura que contiene métricas de pincel.                                                                               |
**GX_PIXELMAP**       | Estructura que contiene métricas de mapa de píxeles.

En el origen de Azure RTOS GUIX se usan tipos de datos adicionales. Se encuentran en los archivos ***tx_port.h** _ o _ *_gx_port.h_**.

## <a name="customer-support-center"></a>Centro de soporte al cliente

Envíe una incidencia de soporte técnico por medio de Azure Portal si tiene alguna pregunta o necesita ayuda con estos pasos. Proporcione la siguiente información en un mensaje de correo electrónico para que podamos resolver la solicitud de soporte técnico de la forma más eficaz posible:

1. Una descripción detallada del problema, incluida la frecuencia con que se produce y si se puede reproducir de forma confiable.

2. Una descripción detallada de los cambios en la aplicación o en Azure RTOS GUIX que han precedido al problema.

3. El contenido de las cadenas _tx_version_id y _gx_version_id que se encuentran en los archivos ***tx_port.h**_ y _ *_gx_port.h_** de la distribución. Estas cadenas nos proporcionan información valiosa sobre el entorno en tiempo de ejecución.

4. El contenido en la RAM de las siguientes variables ULONG:

    **_tx_build_options** **_gx_system_build_options**

    Estas variables nos proporcionan información sobre cómo se han compilado las bibliotecas de Azure RTOS ThreadX y Azure RTOS GUIX.

5. El contenido en la RAM de las siguientes variables ULONG:

    **_gx_system_last_error** **_gx_system_error_count**

    Estas variables hacen un seguimiento de los errores internos del sistema en Azure RTOS GUIX. Si _gx_system_error_count es mayor que uno, establezca un punto de interrupción en el valor devuelto de la función _gx_system_error_process y proporcione el valor de _gx_system_last_error en este punto. Esto suspende el primer error interno del sistema de Azure RTOS GUIX.

6. Un búfer de seguimiento capturado inmediatamente después de que se haya detectado el problema. Puede hacerse si se compilan las bibliotecas de Azure RTOS ThreadX y Azure RTOS GUIX con TX_ENABLE_EVENT_TRACE y se llama a tx_trace_enable con la información del búfer de seguimiento.

7. El proyecto de Azure RTOS GUIX Studio que usa, si procede, o, al menos, un pequeño proyecto suficiente para mostrar la deficiencia que está notificando.
