---
title: 'Capítulo 3: Componentes funcionales de la pila del host USBX'
description: Este capítulo contiene una descripción de la pila de host USB insertada de USBX de alto rendimiento desde una perspectiva funcional.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a3cbbb2e26d66d3db26144a47a1b6cbb11387c7b5b2ba5e19d35df026e5e3598
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790932"
---
# <a name="chapter-3---functional-components-of-usbx-host-stack"></a>Capítulo 3: Componentes funcionales de la pila del host USBX

Este capítulo contiene una descripción de la pila de host USB insertada de USBX de alto rendimiento desde una perspectiva funcional.

## <a name="execution-overview"></a>Información general sobre la ejecución

USBX se compone de varios componentes:

- Inicialización
- Llamadas a la interfaz de la aplicación
- Concentrador raíz
- Clase de concentrador
- Clases de host
- Pila de host USB
- Controladora de host

En el siguiente diagrama se ilustra la pila de host de USBX:

![Pila de host de USBX](./media/usbx-host-stack/usbx-host-stack.png)

### <a name="initialization"></a>Inicialización

Para activar USBX, se debe llamar a la función ***ux_system_initialize***. Esta función inicializa los recursos de memoria de USBX.

Para activar las instalaciones del host de USBX, se debe llamar a la función ***ux_host_stack_initialize***. Esta función, a su vez, inicializará todos los recursos usados por la pila de host de USBX, como subprocesos de ThreadX, exclusiones mutuas y semáforos.

Depende de la inicialización de la aplicación activar al menos un controladora de host USB y una o varias clases USB. Cuando las clases se han registrado en la pila y se ha llamado a la función de inicialización de controladora de host, el bus está activo y se puede iniciar la detección de dispositivos. Si el concentrador raíz del controladora de host detecta un dispositivo conectado, el subproceso de enumeración USB a cargo de la topología USB se reactivará y continuará con la enumeración de los dispositivos.

Debido a la naturaleza de los concentradores raíz y de nivel inferior, es posible que no todos los dispositivos USB conectados se hayan configurado completamente cuando se devuelva la función de inicialización del controlador host. La enumeración de todos los dispositivos USB puede tardar varios segundos, especialmente si hay uno o más concentradores entre el concentrador raíz y los dispositivos USB.

### <a name="application-interface-calls"></a>Llamadas a la interfaz de la aplicación

Hay dos niveles de API en USBX:

- API de pila de host USB
- API de clase de host USB

Normalmente, una aplicación de USBX no debe tener que llamar a ninguna de las funciones de la API de pila de host USB. La mayoría de las aplicaciones solo tendrán acceso a las funciones de la API de clase USB.

### <a name="usb-host-stack-apis"></a>API de pila de host USB

Las funciones de la API de pila de host son las responsables del registro de los componentes de USBX (clases de host y controladores de host), la configuración de los dispositivos y las solicitudes de transferencia para los puntos de conexión de dispositivo disponibles.

### <a name="usb-host-class-api"></a>API de clase de host USB

Las API de clase son muy específicas de cada clase USB. La mayoría de las funciones de API comunes para las clases USB proporcionan servicios como apertura y cierre de un dispositivo, y lectura y escritura en un dispositivo.

### <a name="root-hub"></a>Concentrador raíz

Cada instancia del controladora de host tiene uno o varios concentradores raíz USB. El número de concentradores raíz viene determinado por la naturaleza del controlador o se puede recuperar mediante la lectura de registros específicos del controlador.

### <a name="hub-class"></a>Clase de concentrador

La clase de concentrador se encarga de controlar los concentradores USB. Un concentrador USB puede ser un concentrador independiente o formar parte de un dispositivo compuesto, como un teclado o un monitor. Un concentrador puede tener autoalimentación o alimentarse por bus. Los concentradores alimentados por bus tienen un máximo de cuatro puertos de bajada y solo pueden permitir la conexión de dispositivos autoalimentados o alimentados por bus que usen menos de 100 mA de energía. Los concentradores pueden estar en cascada. Se pueden conectar hasta cinco concentradores entre sí.

### <a name="usb-host-stack"></a>Pila de host USB

La pila de host USB es la pieza central de USBX. Tiene tres funciones principales:

- Administrar la topología del USB
- Enlazar un dispositivo USB a una o más clases
- Proporcionar una API a las clases para realizar interrogaciones de descriptor de dispositivo y transferencias USB

### <a name="topology-manager"></a>Administrador de topología

El subproceso de topología de la pila USB se activa al conectar un dispositivo nuevo o al desconectar un dispositivo. El concentrador raíz o un concentrador normal pueden aceptar conexiones de dispositivos. Cuando se ha conectado un dispositivo al USB, el administrador de topología recuperará el descriptor del dispositivo, el cual contendrá el número de configuraciones posibles disponibles para dicho dispositivo. La mayoría de los dispositivos solo tienen una configuración. Algunos dispositivos pueden funcionar de manera diferente según la energía disponible del puerto al que está conectado. En este caso, el dispositivo tendrá varias configuraciones que se pueden seleccionar en función de la energía disponible. Cuando el administrador de topología configura el dispositivo, se permite que extraiga la cantidad de energía especificada en su descriptor de configuración.

## <a name="usb-class-binding"></a>Enlace de clase USB

Cuando se configura el dispositivo, el administrador de topología permitirá que el administrador de clases continúe la detección de dispositivos examinando los descriptores de la interfaz del dispositivo. Un dispositivo puede tener uno o varios descriptores de interfaz.

Una interfaz representa una función de un dispositivo. Por ejemplo, un altavoz USB tiene tres interfaces, una para el streaming de audio, otra para el control de audio y otra para administrar los diversos botones del altavoz.

El administrador de clases tiene dos mecanismos para unir las interfaces de dispositivo a una o más clases. Puede usar la combinación de un PID/VID (ID. de producto e ID. de proveedor) que se encuentra en el descriptor de la interfaz o la combinación de clase/subclase/protocolo.

La combinación de PID/VID es válida para las interfaces que no se pueden controlar mediante una clase genérica. La combinación de clase/subclase/protocolo la usan las interfaces que pertenecen a una clase certificada USB-IF, como printer, hub, storage, audio o HID.

El administrador de clases contiene una lista de clases registradas de la inicialización de USBX. El administrador de clases llamará a cada clase de una en una hasta que una clase acepte administrar la interfaz para ese dispositivo. Una clase solo puede administrar una interfaz. En el ejemplo del altavoz de audio USB, el administrador de clases llamará a todas las clases para cada una de las interfaces.

Cuando una clase acepte una interfaz, se crea una nueva instancia de esa clase. Después, el administrador de clases buscará la configuración alternativa predeterminada para la interfaz. Un dispositivo puede tener una o varias configuraciones alternativas para cada interfaz. La configuración alternativa 0 será la que se use de forma predeterminada hasta que una clase decida cambiarla.

En el caso de la configuración alternativa predeterminada, el administrador de clases montará todos los puntos de conexión contenidos en la configuración alternativa. Si el montaje de cada punto de conexión se realiza correctamente, el administrador de clases completará su trabajo volviendo a la clase que finalizará la inicialización de la interfaz.

### <a name="usbx-apis"></a>API de USBX

La pila USB exporta un número determinado de API para que las clases USB realicen la interrogación en el dispositivo y las transferencias USB en puntos de conexión específicos. Estas funciones de API se describen en detalle en este manual de referencia.

### <a name="host-controller"></a>Controladora de host

El controlador de controladora de host es el responsable de impulsar un tipo específico de controlador USB. Un controladora de host USB puede contener varios controladores. Por ejemplo, ciertos conjuntos de chips de PC Intel contienen dos controladores UHCI. Algunos controladores USB 2.0 contienen varias instancias de un controlador OHCI además de una instancia del controlador EHCI.

El controladora de host solo administrará varias instancias del mismo controlador. Con el fin de controlar la mayoría de los controladores de host USB 2.0, será necesario inicializar el controlador OCHI y el controlador EHCI durante la inicialización de USBX.

El controladora de host es responsable de administrar lo siguiente:

- Concentrador raíz
- Administración de energía
- Puntos de conexión
- Transferencias

### <a name="root-hub"></a>Concentrador raíz

La administración del concentrador raíz es responsable de iniciar cada puerto del controlador y de determinar si hay un dispositivo insertado o no. Esta funcionalidad la usa el concentrador de raíz USBX genérico para interrogar los puertos de bajada del controlador.

### <a name="power-management"></a>Administración de energía

El procesamiento de administración de energía proporciona el control de las señales de suspensión o reanudación en el modo de asociación, lo que afecta a todos los puertos de bajada del controlador al mismo tiempo, o individualmente si el controlador ofrece esta funcionalidad.

### <a name="endpoints"></a>Puntos de conexión

La administración de puntos de conexión proporciona al controlador la posibilidad de crear o destruir puntos de conexión físicos. Los puntos de conexión físicos son entidades de memoria que analiza el controlador si este es compatible con DMA principal o que están escritos en el controlador. Los puntos de conexión físicos contienen información de transacciones que debe realizar el controlador.

### <a name="transfers"></a>Transferencias

La administración de transferencias permite que una clase realice una transacción en cada uno de los puntos de conexión que se han creado. Cada punto de conexión lógico contiene un componente denominado "solicitud de transferencia" para solicitudes de transferencia USB. La pila usa la solicitud de transferencia para describir la transacción y, después, esta solicitud de transferencia se pasa a la pila y al controlador, que puede dividirla en varias subtransacciones en función de las capacidades del controlador.

## <a name="usb-device-framework"></a>Marco de dispositivos USB

Un dispositivo USB se representa mediante un árbol de descriptores. Hay seis tipos principales de descriptores:

- Descriptores de dispositivo
- Descriptores de configuración
- Descriptores de interfaz
- Descriptores de punto de conexión
- Descriptores de cadena
- Descriptores funcionales

Un dispositivo USB puede tener una descripción muy sencilla y su aspecto es el siguiente:
![Dispositivo USB simple](./media/usbx-host-stack/usb-device-simple.png)

En la ilustración anterior, el dispositivo solo tiene una configuración. Esta configuración solo tiene una interfaz asociada, lo que indica que el dispositivo solo tiene una función y un punto de conexión. Conectado al descriptor de dispositivo hay un descriptor de cadena que proporciona una identificación visible del dispositivo.

Pero un dispositivo puede ser más complejo y puede tener el siguiente aspecto:

![Dispositivo USB complejo](./media/usbx-host-stack/usb-device-complex.png)

En la ilustración anterior, el dispositivo tiene dos descriptores de configuración asociados al descriptor del dispositivo. Este dispositivo podría indicar que tiene dos modos de energía o que se puede controlar mediante clases estándar o clases de propiedad.

La primera configuración tiene dos interfaces asociadas que indican que el dispositivo tiene dos funciones lógicas. La primera función tiene tres descriptores de punto de conexión y un descriptor funcional. La clase responsable de controlar la interfaz puede usar el descriptor funcional para obtener información adicional sobre esta interfaz que normalmente un descriptor genérico no encuentra.

### <a name="device-descriptors"></a>Descriptores de dispositivo

Cada dispositivo USB tiene un único descriptor de dispositivo. Este descriptor contiene la identificación del dispositivo, el número de configuraciones admitidas y las características del punto de conexión de control predeterminado que se usa para configurar el dispositivo.

| Offset | Campo              | Size | Value    | Descripción                             |
| ------ | ------------------ | ---- | -------- | --------------------------------------- |
| 0      | BLength            | 1    | Number   | Tamaño de este descriptor en bytes. |
| 1      | bDescriptorType    | 1    | Constante | Tipo de descriptor de dispositivo. |
| 2      | bcdUSB             | 2    | BCD      | Número de versión de especificación USB en Binary-Coded Decimal.<br />Ejemplo: 2.10 es equivalente a 0x210. Este campo identifica la versión de la especificación USB con la que son compatibles el dispositivo y sus descriptores. |
| 4      | bDeviceClass       | 1    | Clase    | Código de clase (asignado por USB-IF).<br />Si este campo se restablece en 0, cada interfaz de una configuración especifica su propia información de clase y las distintas interfaces funcionan de manera independiente.<br />Si este campo se establece en un valor entre 1 y 0xFE, el dispositivo admite distintas especificaciones de clase en distintas interfaces y es posible que las interfaces no funcionen de forma independiente. Este valor identifica la definición de clase utilizada para las interfaces de agregado.<br />Si este campo se establece en 0xFF, la clase de dispositivo es específica del proveedor. |
| 5      | bDeviceSubClass    | 1    | Subclase | Código de subclase (asignado por USB-IF).<br />Estos códigos se califican mediante el valor del campo bDeviceClass. Si el campo bDeviceClass se restablece a 0, este campo también debe restablecerse a 0. Si el campo bDeviceClass no se establece en 0xFF, se reservan todos los valores para la asignación mediante USB. |
| 6      | bDeviceProtocol    | 1    | Protocolo | Código de protocolo (asignado por USB-IF).<br />Estos códigos se cualifican con el valor de los campos bDeviceClass y bDeviceSubClass. Si un dispositivo admite protocolos específicos de clase en un dispositivo en lugar de una interfaz, este código identifica los protocolos que el dispositivo usa tal y como se define en la especificación de la clase de dispositivo. Si este campo se restablece a 0, el dispositivo no usa protocolos específicos de clase en un dispositivo,<br />pero puede usar protocolos específicos de clase en una interfaz.<br />Si este campo se restablece a 0xFF, el dispositivo usa un protocolo específico de proveedor en un dispositivo. |
| 7      | bMaxPacketSize0    | 1    | Number   | Tamaño máximo de paquete para el punto de conexión cero (solo con válidos los tamaños de bytes de 8, 16, 32 o 64). |
| 8      | idVendor           | 2    | ID       | Identificador de proveedor (asignado por USB-IF). |
| 10     | idProduct          | 2    | ID       | Identificador del producto (asignado por el fabricante). |
| 12     | bcdDevice          | 2    | BCD      | Número de versión del dispositivo en binary-coded decimal. |
| 14     | iManufacturer      | 1    | Índice    | Índice de descriptor de cadena que describe el fabricante. |
| 15     | iProduct           | 1    | Índice    | Índice de descriptor de cadena que describe el producto. |
| 16     | iSerialNumber       | 1    | Índice    | Índice de descriptor de cadena que describe el número de serie del dispositivo. |
| 17     | bNumConfigurations | 1    | Number   | Número de configuraciones posibles. |

USBX define un descriptor de dispositivo USB de la siguiente manera:

```c
typedef struct UX_DEVICE_DESCRIPTOR_STRUCT
{
    UINT      bLength;
    UINT      bDescriptorType;
    USHORT    bcdUSB;
    UINT      bDeviceClass;
    UINT      bDeviceSubClass;
    UINT      bDeviceProtocol;
    UINT      bMaxPacketSize0;
    USHORT    idVendor;
    USHORT    idProduct;
    USHORT    bcdDevice;
    UINT      iManufacturer;
    UINT      iProduct;
    UINT      iSerialNumber;
    UINT      bNumConfigurations;
} UX_DEVICE_DESCRIPTOR;
```

El descriptor de dispositivo USB forma parte de un contenedor de dispositivos descrito como sigue:

```c
typedef struct UX_DEVICE_STRUCT
{
    ULONG ux_device_handle;
    ULONG ux_device_type;
    ULONG ux_device_state;
    ULONG ux_device_address;
    ULONG ux_device_speed;
    ULONG ux_device_port_location;
    ULONG ux_device_max_power;
    ULONG ux_device_power_source;
    UINT ux_device_current_configuration;

    TX_SEMAPHORE ux_device_protection_semaphore;
    struct UX_DEVICE_STRUCT *ux_device_parent; 
    struct UX_HOST_CLASS_STRUCT *ux_device_class; 
    VOID *ux_device_class_instance;
    struct UX_HCD_STRUCT *ux_device_hcd;
    struct UX_CONFIGURATION_STRUCT *ux_device_first_configuration; 
    struct UX_DEVICE_STRUCT *ux_device_next_device;
    struct UX_DEVICE_DESCRIPTOR_STRUCT ux_device_descriptor;
    struct UX_ENDPOINT_STRUCT ux_device_control_endpoint;
    struct UX_HUB_TT_STRUCT ux_device_hub_tt[UX_MAX_TT];
} UX_DEVICE;
```

- **ux_device_handle**: identificador del dispositivo. Normalmente, es la dirección de la instancia de esta estructura para el dispositivo.
- **ux_device_type**: valor obsoleto. Sin usar.
- **ux_device_state**: estado del dispositivo, que puede tener uno de los valores siguientes:
    - **UX_DEVICE_RESET** 0
    - **UX_DEVICE_ATTACHED** 1
    - **UX_DEVICE_ADDRESSED** 2
    - **UX_DEVICE_CONFIGURED** 3
    - **UX_DEVICE_SUSPENDED** 4
    - **UX_DEVICE_RESUMED** 5
    - **UX_DEVICE_SELF_POWERED_STATE** 6
    - **UX_DEVICE_SELF_POWERED_STATE** 7
    - **UX_DEVICE_REMOTE_WAKEUP** 8
    - **UX_DEVICE_BUS_RESET_COMPLETED** 9
    - **UX_DEVICE_REMOVED** 10
    - **UX_DEVICE_FORCE_DISCONNECT** 11
- **ux_device_address**: dirección del dispositivo después de que se haya aceptado el comando de **SET_ADDRESS** (de 1 a 127).
- **ux_device_speed**: velocidad del dispositivo:
    - **UX_LOW_SPEED_DEVICE** 0
    - **UX_FULL_SPEED_DEVICE** 1
    - **UX_HIGH_SPEED_DEVICE** 2
- **ux_device_port_location**: índice del puerto del dispositivo primario (concentrador raíz o concentrador).
- **ux_device_max_power**: potencia máxima en mA que el dispositivo puede recibir en la configuración seleccionada.
- **ux_device_power_source**: puede ser uno de los dos valores siguientes:
    - **UX_DEVICE_BUS_POWERED** 1
    - **UX_DEVICE_SELF_POWERED** 2
- **ux_device_current_configuration**: índice de la configuración actual usada por este dispositivo.
- **ux_device_parent**: puntero de contenedor de dispositivo del elemento primario de este dispositivo. Si el puntero es null, el elemento primario es el concentrador raíz del controlador.
- **ux_device_class**: puntero al tipo de clase que posee este dispositivo.
- **ux_device_class_instance**: puntero a la instancia de la clase a la que pertenece este dispositivo.
- **ux_device_hcd**: instancia del controladora de host USB donde está conectado este dispositivo.
- **ux_device_first_configuration**: puntero al primer contenedor de configuración para este dispositivo.
- **ux_device_next_device**: puntero al siguiente dispositivo de la lista de dispositivos en cualquiera de los buses detectados por USBX.
- **ux_device_descriptor**: descriptor de dispositivo USB.
- **ux_device_control_endpoint**: descriptor del punto de conexión de control predeterminado que usa este dispositivo.
- **ux_device_hub_tt**: matriz de TTS del concentrador para el dispositivo

### <a name="configuration-descriptors"></a>Descriptores de configuración

El descriptor de configuración describe información sobre una configuración específica del dispositivo. Un dispositivo USB puede contener uno o varios descriptores de configuración. El campo **bNumConfigurations** del descriptor de dispositivo indica el número de descriptores de configuración. El descriptor contiene un campo **bConfigurationValue** con un valor que, cuando se usa como parámetro para la solicitud Set Configuration (Establecer la configuración), hace que el dispositivo asuma la configuración descrita.

El descriptor describe el número de interfaces proporcionadas por la configuración. Cada interfaz representa una función lógica dentro del dispositivo y puede funcionar de forma independiente. Por ejemplo, un altavoz de audio USB puede tener tres interfaces, una para el streaming de audio, otra para el control de audio y otra interfaz HID para controlar los botones del altavoz.

Cuando el host emite una solicitud GET_DESCRIPTOR para el descriptor de configuración, se devuelven todos los descriptores de interfaz y de punto de conexión relacionados.

| Offset | Campo               | Size | Value    | Descripción                       |
| ------ | ------------------- | ---- | -------- | --------------------------------- |
| 0      | BLength             | 1    | Number   | Tamaño de este descriptor en bytes. |
| 1      | bDescriptorType     | 1    | Constante | CONFIGURATION                     |
| 2      | wTotalLength        | 2    | Number   | Longitud total de los datos devueltos para esta configuración. Incluye la longitud combinada de todos los descriptores (de configuración, interfaz, punto de conexión y de clase o específico del proveedor) devueltos para esta configuración. |
| 4      | bNumInterfaces      | 1    | Number   | Número de interfaces admitidas por esta configuración. |
| 5      | bConfigurationValue | 1    | Number   | Valor que se va a usar como argumento que se va a establecer.<br/>Configuración para seleccionar esta configuración. |
| 6      | iConfiguration      | 1    | Índice    | Índice de descriptor de cadena que describe esta configuración. |
| 7      | bMAttributes        | 1    | Bitmap   | Características de configuración D7 Alimentado por bus<br />D6 Autoalimentado<br />D5 Activación remota<br />D4 0 reservado (restablecer a cero)<br />Una configuración de dispositivo que usa la energía del bus y de un origen local establece tanto D7 como D6. La fuente de alimentación real en tiempo de ejecución se puede determinar mediante la solicitud de dispositivo Get Status (Obtener estado).<br />Si una configuración de dispositivo admite la activación remota, D5 se establece en 1. |
| 8      | MaxPower            | 1    | mA       | Consumo de energía máximo del dispositivo USB desde el bus en esta configuración específica cuando el dispositivo está totalmente operativo.<br />Expresado en dos unidades de mA (por ejemplo, 50 = 100 mA).<br />Nota: Una configuración de dispositivo informa de si la configuración se alimenta por bus tiene autoalimentación.<br />El estado del dispositivo informa de si el dispositivo tiene autoalimentación. Si un dispositivo está desconectado de su fuente de alimentación externa, actualiza el estado del dispositivo para indicar que ya no tiene autoalimentación. |

USBX define un descriptor de configuración USB como se indica a continuación.

```c
typedef struct UX_CONFIGURATION_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT wTotalLength;
    UINT bNumInterfaces;
    UINT bConfigurationValue;
    UINT iConfiguration;
    UINT bmAttributes;
    UINT MaxPower;
} UX_CONFIGURATION_DESCRIPTOR;
```

El descriptor de configuración de USB forma parte de un contenedor de configuración descrito como sigue.

```c
typedef struct UX_CONFIGURATION_STRUCT
{
    ULONG ux_configuration_handle;
    ULONG ux_configuration_state;
    struct UX_CONFIGURATION_DESCRIPTOR_STRUCT ux_configuration_descriptor;
    struct UX_INTERFACE_STRUCT *ux_configuration_first_interface;
    struct UX_CONFIGURATION_STRUCT *ux_configuration_next_configuration;
    struct UX_DEVICE_STRUCT *ux_configuration_device;
} UX_CONFIGURATION;
```

- **ux_configuration_handle**: identificador de la configuración. Normalmente, es la dirección de la instancia de esta estructura para la configuración.
- **ux_configuration_state**: estado de la configuración.
- **ux_configuration_descriptor**: descriptor de dispositivo USB.
- **ux_configuration_first_interface**: puntero a la primera interfaz para esta configuración.
- **ux_configuration_next_configuration**: puntero a la siguiente configuración para el mismo dispositivo.
- **ux_configuration_device**: puntero al propietario del dispositivo de esta configuración.

### <a name="interface-descriptors"></a>Descriptores de interfaz

El descriptor de interfaz describe una interfaz específica dentro de una configuración. Una interfaz es una función lógica dentro de un dispositivo USB. Una configuración proporciona una o más interfaces, cada una con cero o más descriptores de punto de conexión que describen un conjunto único de puntos de conexión en la configuración. Cuando una configuración admite más de una interfaz, los descriptores de punto de conexión para una interfaz determinada siguen el descriptor de la interfaz de los datos devueltos por la solicitud de **GET_DESCRIPTOR** para la configuración especificada.

Un descriptor de interfaz siempre se devuelve como parte de un descriptor de configuración. Una solicitud GET_DESCRIPTOR no puede acceder directamente a un descriptor de interfaz.

Una interfaz puede incluir configuraciones alternativas que permiten variar los puntos de conexión y sus características una vez configurado el dispositivo. La configuración predeterminada de una interfaz siempre es el valor alternativo cero. Una clase puede seleccionar cambiar la configuración alternativa actual para cambiar el comportamiento de la interfaz y las características de los puntos de conexión asociados. La solicitud SET_INTERFACE se usa para seleccionar una configuración alternativa o para volver a la configuración predeterminada.

La configuración alternativa permite variar una parte de la configuración del dispositivo mientras otras interfaces se mantienen en funcionamiento. Si una configuración tiene un valor alternativo para una o varias de sus interfaces, se incluyen un descriptor de interfaz independiente y sus puntos de conexión asociados para cada valor.

Si una configuración de dispositivo contiene una sola interfaz con dos valores alternativos, la solicitud GET_DESCRIPTOR de la configuración devolvería el descriptor de configuración, el descriptor de la interfaz con los campos **bInterfaceNumber** y **bAlternateSetting** establecidos en cero y, después, los descriptores de punto de conexión para esa configuración, seguidos de otro descriptor de interfaz y sus descriptores de punto de conexión asociados. El campo **bInterfaceNumber** del segundo descriptor de la interfaz también se establecería en cero, pero el campo **bAlternateSetting** del segundo descriptor de interfaz se establecería en 1, lo que indica que esta configuración alternativa pertenece a la primera interfaz.

Una interfaz podría no tener ningún punto de conexión asociado, en cuyo caso solo sería válido para dicha interfaz el punto de conexión de control predeterminado.

Las configuraciones alternativas se usan principalmente para cambiar el ancho de banda solicitado para los puntos de conexión periódicos asociados a la interfaz. Por ejemplo, una interfaz de streaming de un altavoz USB debe tener el primer valor alternativo con una demanda de ancho de banda de 0 en su punto de conexión isocrónico. Otras configuraciones alternativas pueden seleccionar diferentes requisitos de ancho de banda en función de la frecuencia de streaming de audio.

El descriptor USB de la interfaz es el siguiente:

| Offset | Campo              | Size | Value     | Descriptor                              |
| ------ | ------------------ | ---- | --------- | --------------------------------------- |
| 0      | BLength            | 1    | Number    | Tamaño de este descriptor en bytes.       |
| 1      | bDescriptorType    | 1    | Constante  | Tipo de descriptor de interfaz.               |
| 2      | bInterfaceNumber   | 1    | Number    | Número de interfaz. Valor basado en cero que identifica el índice en la matriz de interfaces simultáneas admitidas por esta configuración. |
| 3      | bAltenateSetting   | 1    | Number    | Valor que se usa para seleccionar la configuración alternativa de la interfaz identificada en el campo anterior. |
| 4      | bNumEndpoints      | 1    | Number    | Número de puntos de conexión utilizados por esta interfaz (excluyendo el punto de conexión cero). Si este valor es 0, esta interfaz solo utiliza el punto de conexión cero. |
| 5      | bInterfaceClass    | 1    | Clase     | Código de clase (asignado por USB).<br />Si este campo se restablece a 0, la interfaz no pertenece a ninguna clase de dispositivo USB especificada.<br />Si este campo se establece en 0xFF, la clase de interfaz es específica del proveedor.<br />El resto de los valores están reservados para la asignación por USB. |
| 6      | bInterfaceSubClass | 1    | Subclase  | Código de subclase (asignado por USB).<br />Estos códigos se califican mediante el valor del campo bInterfaceClass. Si el campo bInterfaceClass se restablece a 0, este campo también debe restablecerse a 0. Si el campo bInterfaceClass no se establece en 0xFF, se reservan todos los valores para la asignación mediante USB. |
| 7      | bInterfaceProtocol | 1    | Protocolo  | Código de protocolo (asignado por USB). Estos códigos se cualifican con el valor de los campos bInterfaceClass y bInterfaceSubClass. Si una interfaz admite solicitudes específicas de la clase, este código identifica los protocolos que usa el dispositivo tal y como se define en la especificación de la clase de dispositivo.<br />Si este campo se restablece a 0, el dispositivo no usa un protocolo específico en esta interfaz. Si este campo se restablece a 0xFF, el dispositivo usa un protocolo específico de proveedor para esta interfaz. |
| 8      | iInterface         | 1    | Índice     | Índice de descriptor de cadena que describe esta interfaz. |

USBX define un descriptor de interfaz USB de la siguiente manera:

```c
typedef struct UX_INTERFACE_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bInterfaceNumber;
    UINT bAlternateSetting;
    UINT bNumEndpoints;
    UINT bInterfaceClass
    UINT bInterfaceSubClass;
    UINT bInterfaceProtocol;
    UINT iInterface;
} UX_INTERFACE_DESCRIPTOR;
```

El descriptor de interfaz USB forma parte de un contenedor de interfaz descrito como sigue:

```c
typedef struct UX_INTERFACE_STRUCT
{
    ULONG ux_interface_handle;
    ULONG ux_interface_state;
    ULONG ux_interface_current_alternate_setting;
    struct UX_INTERFACE_DESCRIPTOR_STRUCT ux_interface_descriptor;
    struct UX_HOST_CLASS_STRUCT    *ux_interface_class;
    VOID    *ux_interface_class_instance;
    struct UX_ENDPOINT_STRUCT    *ux_interface_first_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_interface_next_interface;
    struct UX_CONFIGURATION_STRUCT    *ux_interface_configuration;
} UX_INTERFACE;
```

- **ux_interface_handle**: identificador de la interfaz. Normalmente, es la dirección de la instancia de esta estructura para la interfaz.
- **ux_interface_state**: estado de la interfaz.
- **ux_interface_descriptor**: descriptor de interfaz USB.
- **ux_interface_class**: puntero al tipo de clase que posee esta interfaz.
- **ux_interface_class_instance**: puntero a la instancia de la clase a la que pertenece esta interfaz.
- **ux_interface_first_endpoint**: puntero al primer punto de conexión registrado con esta interfaz.
- **ux_interface_next_interface**: puntero a la siguiente interfaz asociada a la configuración.
- **ux_interface_configuration**: puntero al propietario de la configuración de esta interfaz.

### <a name="endpoint-descriptors"></a>Descriptores de punto de conexión

Cada punto de conexión asociado con una interfaz tiene su propio descriptor de punto de conexión. Este descriptor contiene la información requerida por la pila de host para determinar los requisitos de ancho de banda de cada punto de conexión, la carga máxima asociada con el punto de conexión, su periodicidad y su dirección. Un descriptor de extremo siempre lo devuelve un comando GET_DESCRIPTOR para la configuración.

El punto de conexión de control predeterminado asociado al descriptor de dispositivo no se cuenta como parte de los puntos de conexión asociados a la interfaz y, por tanto, no se devuelve en este descriptor.

Cuando el software del host solicita un cambio de la configuración alternativa para una interfaz, todos los puntos de conexión asociados y sus recursos USB se modifican según la nueva configuración alternativa.

Los puntos de conexión no se pueden compartir entre las interfaces, a excepción de los puntos de conexión de control predeterminados.

| Offset | Campo            | Size | Value    | Descripción                       |
| ------ | ---------------- | ---- | -------- | --------------------------------- |
| 0      | BLength          | 1    | Number   | Tamaño de este descriptor en bytes. |
| 1      | bDescriptorType  | 1    | Constante | Tipo de descriptor de punto de conexión. |
| 2      | bEndpointAddress | 1    | Punto de conexión | La dirección del punto de conexión en el dispositivo USB descrito por este descriptor. La dirección se codifica de la siguiente manera:<br />Bit 3... 0: Número de punto de conexión<br />Bit 6... 4: Reservado, restablecer a cero<br />Bit 7: Dirección, omitido para puntos de conexión de control<br />0 = Punto de conexión de salida<br />1 = Punto de conexión de entrada |
| 3      | bmAttributes     | 1    | Bitmap   | Este campo describe los atributos del punto de conexión cuando se configura mediante el campo **bConfigurationValue**. Bits 1... 0: Tipo de transferencia<br />00 = Control<br />01 = Isocrónico<br />10 = Masivo<br />11 = Interrupción<br />Si no se trata de un punto de conexión isocrónico, los bits 5..2 están reservados y deben establecerse en cero. Si es isocrónico, se define de la siguiente manera:<br />Bits 3..2: Tipo de sincronización<br />00 = Sin sincronización<br />01 = Asincrónico<br />10 = Adaptable<br />11 = Sincrónico<br />Bits 5..4: Tipo de uso<br />00 = Punto de conexión de datos<br />01 = Punto de conexión de comentarios<br />10 = Punto de conexión de datos de comentarios implícitos<br />11 = Reservado |
| 4      | wMaxPacketSize   | 2    | Number   | Tamaño máximo de paquete que este punto de conexión puede enviar o recibir cuando se selecciona esta configuración.<br />En el caso de los puntos de conexión isocrónicos, este valor se usa para reservar la hora de bus en la programación, necesaria para las cargas de datos de (micro)fotogramas. La canalización puede usar, de manera continuada, menos ancho de banda que la reservada. El dispositivo notifica, si es necesario, el ancho de banda real usado a través de sus mecanismos normales no definidos por USB.<br />Para todos los puntos de conexión, los bits 10..0 especifican el tamaño máximo del paquete (en bytes).<br />En el caso de los puntos de conexión isocrónicos y de interrupción de alta velocidad:<br />Bits 12..11 especifican el número de oportunidades de transacciones adicionales por micrograma: 00 = ninguna (1 transacción por micrograma)<br />01 = 1 adicional (2 por micrograma)<br />10 = 2 adicionales (3 por micrograma)<br />11 = Reservado<br />Los bits 15..13 están reservados y deben establecerse en cero. |
| 6      | bInterval        | 1     | Number   | Intervalo de número para el punto de conexión de sondeo para las transferencias de datos.<br />Expresado en marcos o microgramas en función de la velocidad de funcionamiento del dispositivo (es decir, un milisegundo o 125 unidades de μs).<br />En el caso de los extremos isocrónicos de alta velocidad o velocidad máxima, este valor debe estar en el intervalo comprendido entre 1 y 16. **BInterval** se usa como exponente para un valor de 2bInterval-1; por ejemplo, un **bInterval** de 4 significa un período de 8 (24-1).<br />En el caso de los puntos de conexión de interrupción completos, el valor de este campo puede ser de 1 a 255.<br />Para puntos de conexión de interrupción de alta velocidad, **bInterval** se usa como exponente para un valor de 2bInterval-1; por ejemplo, un **bInterval** de 4 significa un período de 8 (24-1). Este valor debe estar comprendido entre 1 y 16.<br />En el caso de los puntos de conexión de salida de control o masivos de alta velocidad, **bInterval** especifica la tasa de NAK máxima del punto de conexión. Un valor de cero indica que el punto de conexión nunca envía NAK. Otros valores indican como máximo una señal NAK cada **bInterval** de microgramas.<br />Este valor debe estar comprendido entre 0 y 255. |

USBX define un descriptor de punto de conexión USB de la siguiente manera:

```c
typedef struct UX_ENDPOINT_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bEndpointAddress;
    UINT bmAttributes;
    USHORT wMaxPacketSize;
    UINT bInterval;
} UX_ENDPOINT_DESCRIPTOR;
```

El descriptor de punto de conexión USB forma parte de un contenedor de puntos de conexión, que se describe como sigue:

```c
typedef struct UX_ENDPOINT_STRUCT {
    ULONG    ux_endpoint_handle;
    ULONG    ux_endpoint_state;
    VOID    *ux_endpoint_ed;
    struct UX_ENDPOINT_DESCRIPTOR_STRUCT    ux_endpoint_descriptor;
    struct UX_ENDPOINT_STRUCT    *ux_endpoint_next_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_endpoint_interface;
    struct UX_DEVICE_STRUCT    *ux_endpoint_device;
    struct UX_TRANSFER REQUEST_STRUCT    ux_endpoint_transfer request;
} UX_ENDPOINT;

```

- **ux_endpoint_handle**: identificador del punto de conexión. Normalmente, es la dirección de la instancia de esta estructura para el punto de conexión.
- **ux_endpoint_state**: estado del punto de conexión.
- **ux_endpoint_ed**: puntero al punto de conexión físico en la capa del controladora de host.
- **ux_endpoint_descriptor**: descriptor de punto de conexión USB.
- **ux_endpoint_next_endpoint**: puntero al siguiente punto de conexión que pertenece a la misma interfaz.
- **ux_endpoint_interface**: puntero a la interfaz que posee esta interfaz de punto de conexión.
- **ux_endpoint_device**: puntero al contenedor del dispositivo primario.
- **ux_endpoint_transfer solicitud**: solicitud de transferencia USB usada para enviar y recibir datos desde el dispositivo.

### <a name="string-descriptors"></a>Descriptores de cadena

Los descriptores de cadena son opcionales. Si un dispositivo no admite descriptores de cadena, todas las referencias a descriptores de cadena dentro del dispositivo, configuración y descriptores de interfaz deben restablecerse a cero.

Los descriptores de cadena utilizan codificación Unicode, lo que permite la compatibilidad con varios conjuntos de caracteres. Las cadenas de un dispositivo USB pueden admitir varios idiomas. Cuando se solicita un descriptor de cadena, el solicitante especifica el idioma deseado mediante un identificador de idioma definido por el USB. Puede encontrar la lista de LANGID USB definidos actualmente en el apéndice USBX ??
El índice de cadena cero para todos los lenguajes devuelve un descriptor de cadena que contiene una matriz de códigos LANGID de dos bytes admitidos por el dispositivo. Obsérvese que la cadena Unicode no finaliza en cero. En su lugar, el tamaño de la matriz de cadenas se calcula restando dos al tamaño de la matriz que se encuentra en el primer byte del descriptor.

El descriptor cero de cadena USB se codifica como se indica a continuación.

| Offset | Campo           | Size | Value    | Descripción                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | BLength         | 1    | N+2      | Tamaño de este descriptor en bytes. |
| 1      | bDescriptorType | 1    | Constante | Tipo de descriptor de cadena           |
| 2      | wLANGID[0]      | 2    | Number   | LANGID code 0                    |
| ...    | ...]            | ...  | ...      | ...                              |
| N      | wLANGID[n]      | 2    | Number   | LANGID code n                    |

Otros descriptores de cadena USB se codifican como se indica a continuación.

| Offset | Campo           | Size | Value    | Descripción                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | BLength         | 1    | Number   | Tamaño de este descriptor en bytes. |
| 1      | bDescriptorType | 1    | Constante | Tipo de descriptor de cadena           |
| 2      | bString         | n    | Number   | Cadena codificada de Unicode.           |

USBX define un descriptor de cadena USB de longitud distinta de cero como se indica a continuación:

```c
typedef struct UX_STRING_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT bString[1];
} UX_STRING_DESCRIPTOR;
```

### <a name="functional-descriptors"></a>Descriptores funcionales

Los descriptores funcionales también se conocen como descriptores específicos de clase. Normalmente usan las mismas estructuras básicas que los descriptores genéricos y permiten que haya información adicional disponible para la clase. Por ejemplo, en el caso del altavoz de audio USB, los descriptores específicos de la clase permiten que la clase de audio recupere para cada configuración alternativa el tipo de frecuencia de audio admitido.

### <a name="usbx-device-descriptor-framework-in-memory"></a>Marco de descriptor de dispositivo USBX en memoria

USBX mantiene la mayoría de los descriptores de dispositivo en memoria, es decir, todos los descriptores excepto la cadena y los descriptores funcionales. En el diagrama siguiente se muestra cómo se almacenan y se relacionan estos descriptores.

![Marco de descriptor de dispositivo USBX en memoria](./media/usbx-host-stack/usbx-device-descriptor-framework.png)
