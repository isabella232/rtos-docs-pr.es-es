---
title: 'Capítulo 2: Instalación de la pila de host de Azure RTOS USBX'
description: Obtenga información sobre cómo instalar la pila de host de USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 77df2c4e4bf4ef38403fe78eb98f18820de4325aadb941fc69275e4c77754212
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790973"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a>Capítulo 2: Instalación de la pila de host de Azure RTOS USBX

## <a name="host-considerations"></a>Consideraciones sobre el host

### <a name="computer-type"></a>Tipo de equipo

El desarrollo insertado se suele realizar en equipos host Windows o Unix. Una vez que la aplicación está compilada, vinculada y colocada en el host, se descarga en el hardware de destino para su ejecución.

### <a name="download-interfaces"></a>Interfaces de descarga

Normalmente, la descarga de destino se realiza por medio de una interfaz serie RS-232, aunque las interfaces paralelas, USB y Ethernet se están volviendo más populares. Revise la documentación de la herramienta de desarrollo para ver las opciones disponibles.

### <a name="debugging-tools"></a>Herramientas de depuración

La depuración se suele realizar con el mismo vínculo que la descarga de la imagen del programa. Existen diversos depuradores, que abarcan desde pequeños programas de supervisión que se ejecutan en el destino, hasta herramientas de supervisión de depuración en segundo plano (BDM) y de emulación en circuito (ICE). La herramienta ICE proporciona la depuración más sólida del hardware de destino real.

### <a name="required-hard-disk-space"></a>Espacio en disco duro requerido

El código fuente de USBX se entrega en formato ASCII y requiere aproximadamente 500 KB de espacio en el disco duro del equipo host.

## <a name="target-considerations"></a>Consideraciones sobre el destino

USBX requiere entre 24 KB y 64 KB de memoria de solo lectura (ROM) en el destino en modo de host. La cantidad de memoria necesaria depende del tipo de controlador utilizado y de las clases USB vinculadas a USBX. Se requieren otros 32 KB de memoria de acceso aleatorio (RAM) del destino para las estructuras de datos globales de USBX y el bloque de memoria. Este bloque de memoria también se puede ajustar en función del número esperado de dispositivos en el USB y el tipo de controlador USB. El lado del dispositivo USBX requiere aproximadamente entre 10 y 12 KB de ROM según el tipo de controlador de dispositivo. El uso de memoria RAM depende del tipo de clase emulada por el dispositivo.

USBX también se basa en semáforos, exclusiones mutuas y subprocesos de ThreadX para la protección de varios subprocesos, y en la suspensión de E/S y el procesamiento periódico para la supervisión de la topología del bus USB.

### <a name="product-distribution"></a>Distribución del producto

Azure RTOS USBX se puede obtener desde el repositorio de código fuente público en <https://github.com/azure-rtos/usbx/>.

A continuación se muestra una lista de varios archivos importantes del repositorio:

- ***ux_api.h***: este archivo de encabezado de C contiene todas las equivalencias del sistema, estructuras de datos y prototipos del servicio.
- ***ux_port.h***: este archivo de encabezado de C contiene todas las definiciones de datos y estructuras específicas de la herramienta de desarrollo.
- ***ux.lib***: se trata de la versión binaria de la biblioteca de C de USBX. Se distribuye con el paquete estándar.
- ***demo_usbx.c***: archivo de C que contiene una demostración de USBX simple.

Todos los nombres de archivo están en minúsculas. Esta convención de nomenclatura facilita la conversión de los comandos en plataformas de desarrollo de Unix.

## <a name="usbx-installation"></a>Instalación de USBX

USBX se instala mediante la clonación del repositorio de GitHub en el equipo local. La siguiente es la sintaxis típica para la creación de un clon del repositorio de USBX en el equipo:

```powershell
    git clone https://github.com/azure-rtos/usbx
```

También se puede descargar una copia del repositorio mediante el botón Descargar de la página principal de GitHub.

Además, hay instrucciones para compilar la biblioteca de USBX en la página principal del repositorio en línea.

Las siguientes instrucciones generales se aplican prácticamente a cualquier instalación:

1. Use el mismo directorio en el que antes ha instalado ThreadX en la unidad de disco duro del host. Todos los nombres de USBX son únicos y no interfieren con la instalación previa de USBX.
2. Agregue una llamada a ***ux_system_initialize** _ al principio o cerca del principio de _ *_tx_application_define_.* * Aquí es donde se inicializan los recursos de USBX.
3. Agregue una llamada a ***ux_host_stack_initialize*.**
4. Agregue una o más llamadas para inicializar la instancia requerida de USBX.
5. Agregue una o más llamadas para inicializar los controladores de host disponibles en el sistema.
6. Puede que sea necesario modificar el archivo tx_low_level_initialize.c para agregar inicialización de hardware de bajo nivel e interrumpir el enrutamiento de vectores. Al tratarse de algo específico de la plataforma de hardware, no se va a tratar aquí.
7. También puede ser necesario compilar el código fuente de la aplicación y vincular a las bibliotecas en tiempo de ejecución de USBX y ThreadX (también se pueden necesitar FileX o Netx si se van a compilar la clase de almacenamiento USB o las clases de red USB), ux.a (o ux.lib) y tx.a (o tx.lib). El resultado se puede descargar en el destino y ejecutarse.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar la biblioteca de USBX. Todas las opciones se encuentran en ***ux_user.h***.

En la lista siguiente se detalla cada opción de configuración.


- **UX_PERIODIC_RATE**: este valor representa el número de tics por segundo de una plataforma de hardware específica. El valor predeterminado es 1000, que indica un tic por milisegundo.
- **UX_MAX_CLASS_DRIVER**: este valor es el número máximo de clases que USBX puede cargar. Este valor representa el contenedor de clases y no el número de instancias de una clase. Por ejemplo, si una implementación concreta de USBX necesita la clase hub, la clase de impresora y la clase de almacenamiento, el valor de UX_MAX_CLASS_DRIVER se puede establecer en 3, independientemente del número de dispositivos que pertenezcan a estas clases.
- **UX_MAX_HCD**: este valor representa el número de controladores de host diferentes que están disponibles en el sistema. Para la compatibilidad con USB 1.1, este valor en general será 1. Para la compatibilidad con USB 2.0, este valor puede ser superior a 1. Este valor representa el número de controladores de host simultáneos que se ejecutan a la vez. Si, por ejemplo, hay dos instancias de OHCI o un controlador EHCI y otro OHCI en ejecución, UX_MAX_HCD debe establecerse en 2. 
- **UX_MAX_DEVICES**: este valor representa el número máximo de dispositivos que se pueden conectar al USB. Normalmente, el número máximo teórico en un solo USB es 127 dispositivos. Este valor se puede reducir verticalmente para conservar memoria. Debe tenerse en consideración que este valor representa el número total de dispositivos, independientemente del número de buses USB del sistema.
- **UX_MAX_ED**: este valor representa el número máximo de ED del grupo de controladores. Este número solo se asigna a un controlador. Si hay varias instancias de controladores presentes, cada controlador individual usa este valor.
- **UX_MAX_TD y UX_MAX_ISO_TD**: este valor representa el número máximo de TD normales e isocrónicos del grupo de controladores. Este número solo se asigna a un controlador. Si hay varias instancias de controladores presentes, cada controlador individual usa este valor.
- **UX_THREAD_STACK_SIZE**: este valor es el tamaño de la pila en bytes para los subprocesos de USBX. Normalmente puede ser de 1024 bytes o de 2048 bytes, según el procesador usado y el controlador de host.
- **UX_HOST_ENUM_THREAD_STACK_SIZE**: este valor es el tamaño de la pila del subproceso de enumeración del host USB. Si no se establece este símbolo, el tamaño de la pila del subproceso de enumeración del host de USBX se establece en **UX_THREAD_STACK_SIZE**. 
- **UX_HOST_ENUM_THREAD_STACK_SIZE**: este valor es el tamaño de la pila del subproceso de HCD del host USB. Si no se establece este símbolo, el tamaño de la pila del subproceso de HCD del host de USBX se establece en **UX_THREAD_STACK_SIZE**.
- **UX_THREAD_PRIORITY_ENUM**: este es el valor de prioridad de ThreadX para los subprocesos de enumeración de USBX que supervisa la topología de bus.
- **UX_THREAD_PRIORITY_CLASS**: este es el valor de prioridad de ThreadX para los subprocesos de USBX estándar.
- **UX_THREAD_PRIORITY_KEYBOARD**: este es el valor de prioridad de ThreadX para la clase de teclado HID de USBX.
- **UX_THREAD_PRIORITY_HCD**: este es el valor de prioridad de ThreadX para el subproceso del controlador de host.
- **UX_NO_TIME_SLICE**: este valor define realmente la porción de tiempo que se va a usar para los subprocesos. Por ejemplo, si se ha definido en 0, el puerto de destino de ThreadX no utiliza porciones de tiempo.
- **UX_MAX_HOST_LUN**: este valor representa el número máximo de unidades lógicas de SCSI representadas en el controlador de la clase de almacenamiento del host.
- **UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: si se ha definido, este valor incluye código para controlar los dispositivos de almacenamiento que utilizan el protocolo CB o CBI (por ejemplo, disquetes). Está desactivado de manera predeterminada porque estos protocolos están obsoletos y han sido reemplazados por el protocolo BOT, que prácticamente usan todos los dispositivos de almacenamiento modernos.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: si se ha definido, este valor hace que ux_host_class_hid_keyboard_key_get solo comunique cambios en las teclas, es decir, pulsaciones y liberaciones. De manera predeterminada, solo comunica cuando se pulsa una tecla.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: solo se utiliza si se ha definido **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**. Si se ha definido, hace que ux_host_class_hid_keyboard_key_get solo comunique cambios de pulsación de tecla; los cambios de liberación de tecla no se notifican.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: solo se utiliza si se ha definido **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**. Si se ha definido, hace que ux_host_class_hid_keyboard_key_get comunique los cambios en las teclas de bloqueo (BloqMayús/BloqNum/BloqDespl).
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: solo se utiliza si se ha definido **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**. Si se ha definido, hace que ux_host_class_hid_keyboard_key_get comunique los cambios en las teclas modificadoras (Ctrl/Alt/Mayús/GUI).
- **UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: si se ha definido, este valor representa el número de paquetes de la clase de host CDC-ECM. El valor predeterminado es 16.

## <a name="source-code-tree"></a>Árbol de código fuente

Los archivos de USBX se proporcionan en varios directorios.

![Árbol de código fuente](media/usbx-host-stack/source-code-tree.png)

Para que los archivos sean reconocibles por sus nombres, se ha adoptado la siguiente convención:

| Nombre de sufijo de archivo | Descripción del archivo                          |
| ---------------- | ----------------------------------------- |
| ux_host_stack    | archivos principales de pila de host de usbx                |
| ux_host_class    | archivos de clases de pila de host de usbx             |
| ux_hcd           | archivos de controlador de pila de host de usbx   |
| ux_device_stack  | archivos principales de pila de dispositivo de usbx              |
| ux_device_class  | archivos de clases de pila de dispositivo de usbx           |
| ux_dcd           | archivos de controlador de pila de host de usbx |
| ux_otg           | archivos relacionados con el controlador de otg de usbx  |
| ux_pictbridge    | archivos de pictbridge de usbx                     |
| ux_utility       | funciones de utilidad de usbx                    |
| demo_usbx        | archivos de demostración de USBX              |

## <a name="initialization-of-usbx-resources"></a>Inicialización de recursos de USBX

USBX tiene su propio administrador de memoria. La memoria debe asignarse a USBX antes de que se inicialice el lado de host o dispositivo de USBX. El administrador de memoria de USBX puede hospedar sistemas en los que la memoria se puede almacenar en caché.

La siguiente función inicializa los recursos de memoria de USBX con 128 K de memoria normal y sin bloque independiente para la memoria segura en caché:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

El prototipo de ux_system_initialize es como se indica a continuación.

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a>Parámetros de entrada:

- **regular_memory_pool_start** Inicio del bloque de memoria normal.
- **regular_memory_size** Tamaño del bloque de memoria normal.
- **cache_safe_memory_pool_start** Inicio del bloque de memoria segura en caché.
- **cache_safe_memory_size** Tamaño del bloque de memoria segura en caché.    |

No todos los sistemas requieren la definición de memoria segura en caché. En este tipo de sistema, los valores que se pasan durante la inicialización del puntero de memoria se establecerán en UX_NULL y el tamaño del bloque en 0. A continuación, USBX usará el bloque de memoria normal en lugar del bloque seguro en caché.

En un sistema en el que la memoria normal no es segura en caché y un controlador necesita hacer uso de la memoria DMA (como los controladores OHCI y EHCI, entre otros), es necesario definir un bloque de memoria en una zona segura en caché.

## <a name="uninitialization-of-usbx-resources"></a>Anulación de inicialización de recursos de USBX

USBX se puede finalizar mediante la liberación de sus recursos. Antes de finalizar USBX, todas las clases y los recursos del controlador deben finalizarse correctamente. La siguiente función anula la inicialización de los recursos de memoria de USBX:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

El prototipo de ux_system_initialize es como se indica a continuación.

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a>Definición de controladores de host USB

Es necesario definir al menos un controlador de host USB para que USBX funcione en modo de host. El archivo de inicialización de la aplicación debe contener esta definición. La línea siguiente realiza la definición de un controlador de host genérico.

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

ux_host_stack_hcd_register tiene el siguiente prototipo.

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

La función ux_host_stack_hcd_register tiene los parámetros siguientes.

- **hcd_name**: cadena del nombre del controlador
- **hcd_initialize_function**: función de inicialización del controlador
- **hcd_param1**: normalmente el valor de E/S o la memoria usada por el controlador
- **hcd_param2**: normalmente la IRQ usada por el controlador

En el ejemplo anterior:

- "ux_hcd_controller" es el nombre del controlador
- "ux_hcd_controller_initialize" es la rutina de inicialización del controlador de host
- 0xd0000 es la dirección en la que los registros del controlador de host están visibles en la memoria
- y 0x0A es la IRQ usada por el controlador de host.

A continuación se proporciona un ejemplo de la inicialización de USBX en modo de host con un controlador de host y varias clases.

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a>Definición de clases de host

Es necesario definir una o varias clases de host con USBX. Se necesita una clase USB para activar un dispositivo USB después de que la pila USB haya configurado el dispositivo USB. Una clase USB es específica del dispositivo. Pueden ser necesarias una o más clases para activar un dispositivo USB en función del número de interfaces que contengan los descriptores del dispositivo USB.

Este es un ejemplo del registro de la clase hub.

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

La función ux_host_class_register tiene el siguiente prototipo.

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- **class_name** es el nombre de la clase
- **class_entry_address** es el punto de entrada de la clase

En el ejemplo de la inicialización de la clase hub:

- "ux_host_class_hub" es el nombre de la clase hub
- ux_host_class_hub_entry es el punto de entrada de la clase hub

## <a name="troubleshooting"></a>Solución de problemas

USBX se entrega con un archivo de demostración y un entorno de simulación. Siempre es conveniente que la plataforma de demostración se ejecute en primer lugar, ya sea en el hardware de destino o en una plataforma de demostración específica.

Si el sistema de demostración no funciona, pruebe los siguientes pasos para delimitar el problema.

## <a name="usbx-version-id"></a>Id. de la versión de USBX

La versión actual de USBX está disponible tanto para el software de usuario como para el de aplicación durante el tiempo de ejecución. El programador puede obtener la versión de USBX si examina el archivo ***ux_port.h** _. Además, este archivo también contiene un historial de versiones del puerto correspondiente. El software de aplicación puede obtener la versión de USBX si examina la cadena global _ *_ _ux_version_id_* _, que se define en _*_ux_port.h_**.
