---
title: 'Apéndice H: marcas de configuración de tiempo de compilación de GUIX'
description: Obtenga información sobre las marcas de configuración de tiempo de compilación de GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 65095e326bc6809eba6e9472e2d74325351354ca
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814997"
---
# <a name="appendix-h---guix-build-time-configuration-flags"></a>Apéndice H: marcas de configuración de tiempo de compilación de GUIX

GUIX admite varias opciones de compilación condicional y valores de configuración. La configuración predeterminada para estos valores de configuración y condicionales se puede reemplazar si se define previamente el valor, ya sea en el archivo de encabezado gx_user.h o en la línea de comandos del compilador.

**GX_DISABLE_THREADX_BINDING**
- Valor predeterminado: sin definir
- Descripción: este condicional se puede usar para deshabilitar el enlace de RTOS de ThreadX predeterminado. Si desea ejecutar GUIX con sistemas RTOS diferentes de ThreadX, debe usar #define GX_DISABLE_THREADX_BINDING y proporcionar sus propios servicios de enlace de RTOS.

GX_SYSTEM_TIMER_MS
- Valor predeterminado: 20
- Descripción: este valor define la precisión o el intervalo del temporizador de GUIX deseado.

TX_TIMER_TICKS_PER_SECOND
- Valor predeterminado: 100
- Descripción: este valor define el número de frecuencias de interrupción del temporizador de TX. Dado que el temporizador de intervalo de ThreadX predeterminado es de 10 ms, el valor predeterminado se establece en una frecuencia de 100 Hz.

GX_SYSTEM_TIMER_TICKS
- Valor predeterminado: ((GX_SYSTEM_TIMER_MS * TX_TIMER_TICKS_PER_SECOND)/1000)
- Descripción: este valor define el número de tics de temporizador de los sistemas RTOS subyacentes por tic del temporizador de GUIX. El valor predeterminado es 2, lo que significa que el intervalo del temporizador de GUIX es 2 intervalos de interrupción del temporizador de ThreadX o 20 ms de forma predeterminada.

GX_DISABLE_MULTITHREAD_SUPPORT
- Valor predeterminado: no definido
- Descripción: este condicional de tiempo de compilación se puede usar para deshabilitar la compatibilidad de la API de GUIX para varios subprocesos que invoquen la API de GUIX simultáneamente. Si solo un subproceso de aplicación utilizará la API de GUIX, debe definir esta marca para reducir la sobrecarga del sistema asociada a la protección de las secciones de código críticas.

GX_DISABLE_UTF8_SUPPORT
- Valor predeterminado: no definido.
- Descripción: este condicional de tiempo de compilación se puede usar para quitar la compatibilidad interna de GUIX para la codificación de cadenas de formato UTF8. Si solo usa los valores de caracteres M-0xFF en la aplicación, al activar #define se reducirá el tamaño del código y la sobrecarga asociada con la compatibilidad de la codificación de cadenas de formato UTF8.

GX_DISABLE_ARC_DRAWING_SUPPORT
- Valor predeterminado: no definido.
- Descripción: este condicional se puede usar para reducir el tamaño del código de la biblioteca de GUIX y el tamaño de la estructura de GX_DISPLAY. Para ello, se debe quitar la compatibilidad con las funciones de dibujo de arco: arco, círculo y elipse. Estas funciones no son necesarias para el conjunto de widgets predeterminados de GUIX.

GX_DISABLE_SOFTWARE_DECODER_SUPPORT
- Valor predeterminado: no definido.
- Descripción: este condicional se puede definir para quitar la compatibilidad con el descodificador de software JPEG y PNG en tiempo de ejecución de la biblioteca de GUIX. Si la aplicación no requiere descodificación en tiempo de ejecución de archivos JPG o PNG, lo que significa que la aplicación no usa los mapas de píxeles en formato RAW que genera Studio ni lee los archivos de imagen de un sistema de archivos externo, puede activar #define para reducir la superficie de la biblioteca de GUIX.

GX_DISABLE_BINARY_RESOURCE_SUPPORT
- Valor predeterminado: no definido
- Descripción: este condicional se puede usar para quitar la compatibilidad de la biblioteca de GUIX para la carga de datos de recursos binarios. Los recursos binarios se pueden usar para realizar el enlace en tiempo de ejecución de los datos de recursos con la aplicación GUIX. Si solo usa archivos de recursos de formato de código fuente de C, puede definir este condicional para reducir la superficie de la biblioteca de GUIX.

GX_DISABLE_BRUSH_ALPHA_SUPPORT
- Valor predeterminado: no definido.
- Descripción: cuando se ejecuta con profundidades de color de 16 BPP y más altas, GUIX admite de manera opcional el dibujo de gráficos que no son de arco, mapas de píxeles y fuentes con un valor alfa definido por el pincel del contexto de dibujo. La compatibilidad con este modo de dibujo introduce una pequeña sobrecarga en tiempo de ejecución y un aumento de la superficie de la biblioteca, que se puede eliminar definiendo esta marca si no se requiere compatibilidad con el dibujo de combinación alfa. Tenga en cuenta que todavía se admiten los mapas de píxeles con canal alfa, las fuentes con suavizado de contorno y otros modos de dibujo con suavizado de contorno, independientemente de esta configuración condicional.

GX_DISABLE_THREADX_TIMER_SOURCE
- Valor predeterminado: no definido.
- Descripción: este condicional se puede usar para deshabilitar el origen del temporizador de ThreadX. Debe definir GX_DISABLE_THREADX_TIMER_SOURCE si desea utilizar un origen de temporizador diferente.

GX_REPEAT_BUTTON_INITIAL_TICS
- Valor predeterminado: 10
- Descripción: si un botón tiene el estilo GX_STYLE_BUTTON_REPEAT, este valor define cuánto tiempo espera el botón antes de empezar a enviar eventos de GX_EVENT_CLICKED repetidos.

GX_MAX_QUEUE_EVENTS
- Valor predeterminado: 48.
- Descripción: define el tamaño de la cola de eventos GUIX en unidades de entradas de la estructura de eventos. Si la cola de eventos se desborda, se descartan los eventos que se están insertando en la cola y la función gx_system_event_send() devuelve GX_SYSTEM_ERROR.

GX_MAX_DIRTY_AREAS
- Valor predeterminado: 64.
- Descripción: define el número máximo de entradas de la lista desfasada únicas que puede mantener un lienzo. Si la lista desfasada se desborda, GUIX marcará de forma predeterminada la ventana raíz del lienzo como desfasada, lo que resulta menos eficaz que dibujar widgets secundarios individuales.

GX_MAX_CONTEXT_NESTING
- Valor predeterminado: 8.
- Descripción: define el anidamiento máximo de la pila del contexto de dibujo. Equivale al anidamiento máximo de widgets primarios/secundarios/secundarios/secundarios dentro de la definición de la interfaz de usuario.

GX_MAX_INPUT_CAPTURE_NESTING
- Valor predeterminado: 4.
- Descripción: define el tamaño de la pila que se usa para mantener la lista de widgets que tienen capturas de la entrada del usuario (mouse y teclado).

GX_SYSTEM_THREAD_PRIORITY
- Valor predeterminado: 16.
- Descripción: define la prioridad del subproceso GUIX creado durante la ejecución de gx_system_initialize().

GX_SYSTEM_THREAD_TIMESLICE
- Valor predeterminado: 10
- Descripción: define el período de tiempo del subproceso GUIX en términos de tics del temporizador de RTOS. Si se definen otros subprocesos con la misma prioridad que el subproceso GUIX, este valor determina la frecuencia con que se concede a esos subprocesos competitivos el control de la CPU.

GX_CURSOR_BLINK_INTERVAL
- Valor predeterminado: 20.
- Descripción: define la velocidad de parpadeo del cursor de entrada para los widgets de entrada de texto. Este valor se proporciona en términos de tics de temporizador de GUIX, que de forma predeterminada se define en 50 ms, por lo que un valor de 20 indica que el cursor de entrada parpadea una vez por segundo.

GX_MULTI_LINE_INDEX_CACHE_SIZE
- Valor predeterminado: 32.
- Descripción: define el tamaño de la memoria caché del índice de inicio de lista que mantienen los widgets de entrada y visualización de texto de varias líneas. Esta memoria caché se utiliza para realizar un desplazamiento vertical rápido de los widgets de texto de varias líneas. Para obtener el mejor rendimiento, el tamaño de la memoria caché debe ser mayor que el número de filas visibles del widget de texto de varias líneas más grande definido por la aplicación. Por ejemplo, si las filas más visibles de cualquier widget de texto son 20 filas, la aplicación puede definir un tamaño de caché de 32 (valor predeterminado), que permite que GUIX se desplace verticalmente sin tener que volver a calcular todos los índices de inicio de línea.

GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES
- Valor predeterminado: 4.
- Descripción: el bloque de control de botón de texto de varias líneas mantiene un puntero a cada una de las líneas de texto que mostrará el botón. Este valor determina el número de punteros de texto que necesita el botón de texto de varias líneas en el peor de los casos.

GX_POLYGON_MAX_EDGE_NUM
- Valor predeterminado: 10
- Descripción: este valor determina el polígono más complejo que puede dibujar GUIX. El algoritmo de dibujo de polígonos determina las líneas necesarias para definir las aristas del polígono, y esta definición determina el número máximo de aristas que se pueden admitir.

GX_NUMERIC_SCROLL_WHEEL_STRING_BUFFER_SIZE
- Valor predeterminado: 16.
- Descripción: para una rueda del mouse de número, el widget de la rueda convierte los valores enteros en cadenas ASCII. Este valor determina la longitud máxima de la cadena que se requiere para mostrar los valores enteros asignados.

GX_DEFAULT_CIRCULAR_GAUGE_ANIMATION_DELAY
- Valor predeterminado: 5.
- Descripción: define el número de tics de temporizador de GUIX (50 ms) entre las actualizaciones de un medidor circular configurado para animar el movimiento de la aguja entre la última posición angular y la actual.

GX_NUMERIC_PROMPT_BUFFER_SIZE
- Valor predeterminado: 16.
- Descripción: una solicitud numérica asigna un búfer para convertir un valor entero que tiene asignado en una cadena ASCII. Esta definición determina el tamaño del búfer de caracteres.

GX_ANIMATION_POOL_SIZE
- Valor predeterminado: 6.
- Descripción: GUIX define un grupo de animaciones desde el que se pueden asignar y devolver estructuras de información de animaciones de forma dinámica mediante las API de gx_system_animation_get y gx_system_animation_free(). Esta definición determina el tamaño de este grupo de bloques de control de animaciones.

GX_MOUSE_SUPPORT
- Valor predeterminado: no definido.
- Descripción: esta definición habilita la compatibilidad con la entrada del mouse. El mouse de software requiere que el controlador de pantalla dibuje y realice un seguimiento del cursor del mouse, lo que agrega sobrecarga adicional al controlador de pantalla. Esta definición solo debe establecerse cuando se deba admitir un mouse (no una pantalla táctil).

GX_HARDWARE_MOUSE_SUPPORT
- Valor predeterminado: no definido.
- Descripción: cuando se establece esta definición, el controlador de pantalla de GUIX emplea la compatibilidad con el dibujo del cursor del mouse de hardware. Esto reduce la memoria necesaria para capturar la memoria del lienzo debajo del cursor del mouse y mejora el rendimiento del sistema para los destinos de hardware que admiten una capa de gráficos de superposición del mouse.

GX_FONT_KERNING_SUPPORT
- Valor predeterminado: no definido.
- Descripción: esta definición se puede establecer para habilitar la compatibilidad con el interletraje de fuentes. El interletraje de fuentes mejora el espaciado de los glifos en determinadas combinaciones de glifos. Esta compatibilidad agrega una pequeña cantidad de sobrecarga a las funciones de dibujo de cadenas en tiempo de ejecución y también aumenta ligeramente el tamaño de las estructuras de datos de fuentes.

GX_WIDGET_USER_DATA
- Valor predeterminado: no definido.
- Descripción: si se define, se agrega un campo de datos definido por el usuario al bloque de control GX_WIDGET. Este campo de datos se puede asignar mediante la vista de propiedades de GUIX Studio. GUIX omite este campo de datos internamente, pero el software de la aplicación puede usarlo para muchos propósitos.

GUIX_5_4_0_COMPATIBILITY
- Valor predeterminado: no definido.
- Descripción: determinadas API de la GUI se modificaron después de la versión 5.4.0 para agregar compatibilidad con los colores de texto deshabilitados y para mejorar la precisión de ciertas funciones matemáticas mediante parámetros de coincidencia de punto fijo. Estos cambios hacen que las versiones de la biblioteca de GUIX posteriores a 5.4.0 sean incompatibles con versiones anteriores. Sin embargo, al activar #define, la biblioteca se puede compilar de tal forma que las API sean totalmente compatibles con la versión 5.4.0 o anteriores, lo que significa que no se necesita ningún cambio en las aplicaciones existentes para realizar la compilación con la versión más reciente de la biblioteca de GUIX.

GX_MAX_STRING_LENGTH
- Valor predeterminado: 102400
- Descripción: define la longitud máxima de una cadena, que se usa para probar cadenas no válidas. Si la cadena de entrada supera la longitud máxima de la cadena, se considerará no válida.