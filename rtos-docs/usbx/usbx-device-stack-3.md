---
title: 'Capítulo 3: Componentes funcionales de la pila del dispositivo USBX'
description: Este capítulo contiene una descripción de la pila de dispositivos USB insertada de USBX de alto rendimiento desde una perspectiva funcional.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a20fed71cbee8c50519be4a971eb191e0cc93915
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815670"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a>Capítulo 3: Componentes funcionales de la pila del dispositivo USBX

Este capítulo contiene una descripción de la pila de dispositivos USB insertada de USBX de alto rendimiento desde una perspectiva funcional.

## <a name="execution-overview"></a>Información general sobre la ejecución

USBX para el dispositivo se compone de varios componentes.

- Inicialización
- Llamadas a la interfaz de la aplicación
- Clases de dispositivo
- Pila de dispositivos USB
- Controladora de dispositivos
- Administrador de VBUS

En el siguiente diagrama se ilustra la pila de dispositivos USBX.

![Pila de dispositivos USBX](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a>Inicialización

Para activar USBX, se debe llamar a la función ***ux_system_initialize***. Esta función inicializa los recursos de memoria de USBX.

Para activar las instalaciones del dispositivo USBX, se debe llamar a la función ***ux_device_stack_initialize***. Esta función, a su vez, inicializará todos los recursos usados por la pila de dispositivos USBX, como subprocesos de ThreadX, exclusiones mutuas y semáforos.

Depende de la inicialización de la aplicación activar la controladora de dispositivos USB y una o varias clases USB. Al contrario que el lado del host USB, el lado del dispositivo solo puede tener un controlador para la controladora USB en ejecución en un momento dado. Cuando las clases se han registrado en la pila y se ha llamado a la función de inicialización de la controladora de dispositivos, el bus está activo y la pila responderá a los comandos de enumeración de host y restablecimiento de bus.

### <a name="application-interface-calls"></a>Llamadas a la interfaz de la aplicación

Hay dos niveles de API en USBX.

- API de la pila de dispositivos USB
- API de la clase de dispositivos USB

Normalmente, una aplicación de USBX no debe tener que llamar a ninguna de las API de la pila de dispositivos USB. La mayoría de las aplicaciones solo tendrán acceso a las API de clase USB.

### <a name="usb-device-stack-apis"></a>API de la pila de dispositivos USB

Las API de la pila de dispositivos son responsables del registro de los componentes de los dispositivos USBX, como las clases y el marco del dispositivo.

### <a name="usb-device-class-apis"></a>API de la clase de dispositivos USB

Las API de clase son muy específicas de cada clase USB. La mayoría de las API comunes para las clases USB proporcionaban servicios como apertura y cierre de un dispositivo, y lectura y escritura en un dispositivo. La naturaleza de las API es similar a la del lado del host.

## <a name="device-framework"></a>Marco de dispositivos

El lado del dispositivo USB es responsable de la definición del marco del dispositivo. El marco del dispositivo se divide en tres categorías, tal y como se describe en las secciones siguientes.

### <a name="definition-of-the-components-of-the-device-framework"></a>Definición de los componentes del marco del dispositivo

La definición de cada componente del marco del dispositivo está relacionada con la naturaleza del dispositivo y con los recursos utilizados por el dispositivo. A continuación se detallan las categorías principales.

- Descriptor del dispositivo
- Descriptor de configuración
- Descriptor de la interfaz
- Descriptor del punto de conexión

USBX admite la definición de los componentes del dispositivo para la velocidad alta y máxima (la velocidad baja se trata de la misma forma que la velocidad máxima). Esto permite que el dispositivo funcione de forma diferente cuando se conecta a un host de velocidad alta o máxima. Las diferencias típicas son el tamaño de cada punto de conexión y la potencia consumida por el dispositivo.

La definición del componente del dispositivo adopta la forma de una cadena de bytes que sigue la especificación USB. La definición es contigua y el orden en el que se representa el marco en la memoria será el mismo que se devuelve al host durante la enumeración.

A continuación, se muestra un ejemplo de un marco de dispositivo para un disco flash USB de alta velocidad.

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a>Definición de las cadenas del marco del dispositivo

Las cadenas son opcionales en un dispositivo. Su finalidad es dejar que el host USB conozca el fabricante del dispositivo, el nombre del producto y el número de revisión mediante cadenas Unicode.

Las cadenas principales son índices insertados en los descriptores del dispositivo. Se pueden insertar índices de cadenas adicionales en interfaces individuales.

Suponiendo que el marco del dispositivo anterior tiene tres índices de cadena insertados en el descriptor del dispositivo, la definición del marco de cadena podría ser similar a la de este código de ejemplo.

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

Si hay que usar cadenas diferentes para cada velocidad, se deben usar índices diferentes, ya que los índices son independientes de la velocidad.

La codificación de la cadena está basada en UNICODE. Para obtener más información sobre el estándar de codificación UNICODE, consulte la siguiente publicación:

*Estándar Unicode, codificación de caracteres mundial, versión 1, volúmenes 1 y 2, Consorcio Unicode, empresa Addison-Wesley Publishing y Reading MA*

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a>Definición de los idiomas compatibles con el dispositivo para cada cadena

USBX tiene la capacidad de admitir varios idiomas, aunque el predeterminado es el inglés. La definición de cada idioma para los descriptores de cadena presenta la forma de una matriz de definición de idiomas definida como se indica a continuación.

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

Para admitir otros idiomas, basta con agregar la definición de doble byte del código de idioma después del código de inglés predeterminado. Microsoft ha definido el código de idioma en el documento.

*Desarrollo de software internacional para Windows 95 y Windows NT, Nadine Kano, Microsoft Press, Redmond WA*

## <a name="vbus-manager"></a>Administrador de VBUS

En la mayoría de los diseños de dispositivos USB, VBUS no forma parte del núcleo del dispositivo USB, sino que se conecta a un GPIO externo, que supervisa la señal de la línea.

Como resultado, VBUS debe administrarse de forma independiente con respecto al controlador de la controladora de dispositivos.

Es la aplicación la que debe proporcionar la dirección de E/S de VBUS a la controladora de dispositivos. VBUS debe inicializarse antes de inicializar la controladora de dispositivos.

En función de la especificación de la plataforma para la supervisión de VBUS, es posible admitir las señales de VBUS del identificador del controlador de la controladora después de inicializar la E/S de VBUS o, si no es posible, la aplicación debe proporcionar el código para controlar VBUS.

Si la aplicación desea controlar VBUS por sí sola, su único requisito es llamar a la función ***ux_device_stack_disconnect*** cuando detecta que se ha extraído un dispositivo. No es necesario informar a la controladora cuando se inserte un dispositivo, ya que la controladora se activará cuando se detecte la señal de aserción/desaserción de RESTABLECIMIENTO DEL BUS.
