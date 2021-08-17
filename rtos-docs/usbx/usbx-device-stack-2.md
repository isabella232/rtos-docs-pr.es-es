---
title: 'Capítulo 2: Instalación de la pila de dispositivos de Azure RTOS USBX'
description: Obtenga información sobre cómo instalar la pila de dispositivos de Azure RTOS USBX, así como las consideraciones de host importantes que debe tener en cuenta antes de la instalación.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: abe3e43e090890a5e51700fc2f587c59619fcdad5b71681fd4071c614dab5ce6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791415"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a>Capítulo 2: Instalación de la pila de dispositivos de Azure RTOS USBX

## <a name="host-considerations"></a>Consideraciones sobre el host

### <a name="computer-type"></a>Tipo de equipo

El desarrollo insertado se suele realizar en equipos host Windows o Unix. Una vez que la aplicación está compilada, vinculada y colocada en el host, se descarga en el hardware de destino para su ejecución.

### <a name="download-interfaces"></a>Interfaces de descarga

Normalmente, la descarga de destino se realiza por medio de una interfaz serie RS-232, aunque las interfaces paralelas, USB y Ethernet se están volviendo más populares. Revise la documentación de la herramienta de desarrollo para ver las opciones disponibles.

### <a name="debugging-tools"></a>Herramientas de depuración

La depuración se suele realizar con el mismo vínculo que la descarga de la imagen del programa. Existen diversos depuradores, que abarcan desde pequeños programas de supervisión que se ejecutan en el destino, hasta herramientas de supervisión de depuración en segundo plano (BDM) y de emulación en circuito (ICE). La herramienta ICE proporciona la depuración más sólida del hardware de destino real.

### <a name="required-hard-disk-space"></a>Espacio en disco duro requerido

El código fuente de USBX se entrega en formato ASCII y requiere aproximadamente 500 KB de espacio en el disco duro del equipo host.

### <a name="target-considerations"></a>Consideraciones sobre el destino

USBX requiere entre 24 KB y 64 KB de memoria de solo lectura (ROM) en el destino en modo de host. La cantidad de memoria necesaria depende del tipo de controlador utilizado y de las clases USB vinculadas a USBX. Se requieren otros 32 KB de memoria de acceso aleatorio (RAM) del destino para las estructuras de datos globales de USBX y el bloque de memoria. Este bloque de memoria también se puede ajustar en función del número esperado de dispositivos en el USB y el tipo de controlador USB. El lado del dispositivo USBX requiere aproximadamente entre 10 y 12 KB de ROM según el tipo de controlador de dispositivo. El uso de memoria RAM depende del tipo de clase emulada por el dispositivo.

USBX también se basa en semáforos, exclusiones mutuas y subprocesos de ThreadX para la protección de varios subprocesos, y en la suspensión de E/S y el procesamiento periódico para la supervisión de la topología del bus USB.

### <a name="product-distribution"></a>Distribución del producto

Azure RTOS USBX se puede obtener desde el repositorio de código fuente público en <https://github.com/azure-rtos/usbx/>.

A continuación, se muestra una lista de varios archivos importantes del repositorio.

* ***ux_api.h***: este archivo de encabezado de C contiene todas las equivalencias del sistema, estructuras de datos y prototipos del servicio.
* ***ux_port.h***: este archivo de encabezado de C contiene todas las definiciones de datos y estructuras específicas de la herramienta de desarrollo.
* ***ux.lib***: se trata de la versión binaria de la biblioteca de C de USBX. Se distribuye con el paquete estándar.
* ***demo_usbx.c***: archivo de C que contiene una demostración de USBX simple.

Todos los nombres de archivo están en minúsculas. Esta convención de nomenclatura facilita la conversión de los comandos en plataformas de desarrollo de Unix.

## <a name="usbx-installation"></a>Instalación de USBX

USBX se instala mediante la clonación del repositorio de GitHub en el equipo local. La siguiente es la sintaxis típica para la creación de un clon del repositorio de USBX en el equipo:

```c
    git clone https://github.com/azure-rtos/usbx
```

También se puede descargar una copia del repositorio mediante el botón Descargar de la página principal de GitHub.

Además, hay instrucciones para compilar la biblioteca de USBX en la página principal del repositorio en línea.

Las siguientes instrucciones generales se aplican prácticamente a cualquier instalación:

1. Use el mismo directorio en el que antes ha instalado ThreadX en la unidad de disco duro del host. Todos los nombres de USBX son únicos y no interfieren con la instalación previa de USBX.
1. Agregue una llamada a ***ux_system_initialize** _ en o cerca del principio de _*_tx_application_define_**. Aquí es donde se inicializan los recursos de USBX.
1. Agregue una llamada a ***ux_device_stack_initialize*** .
1. Agregue una o varias llamadas para inicializar las clases USBX requeridas (ya sean clases de host o de dispositivos).
1. Agregue una o varias llamadas para inicializar la controladoras de dispositivos disponibles en el sistema.
1. Puede que sea necesario modificar el archivo tx_low_level_initialize.c para agregar inicialización de hardware de bajo nivel e interrumpir el enrutamiento de vectores. Al tratarse de algo específico de la plataforma de hardware, no se va a tratar aquí.
1. También puede ser necesario compilar el código fuente de la aplicación y vincular a las bibliotecas en tiempo de ejecución de USBX y ThreadX (también se pueden necesitar FileX o Netx si se van a compilar la clase de almacenamiento USB o las clases de red USB), ux.a (o ux.lib) y tx.a (o tx.lib). El resultado se puede descargar en el destino y ejecutarse.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar la biblioteca de USBX. Todas las opciones se encuentran en ***ux_user.h***.

En la lista siguiente se detalla cada opción de configuración.

| Opción de&nbsp;configuración | Descripción |
| --- | --- |
| **UX_PERIODIC_RATE** | Este valor representa el número de tics por segundo de una plataforma de hardware específica. El valor predeterminado es 1000, que indica un tic por milisegundo. |
| **UX_THREAD_STACK_SIZE** | Este valor es el tamaño de la pila en bytes para los subprocesos de USBX. Normalmente puede ser de 1024 bytes o de 2048 bytes, según el procesador usado y el controlador de host. |
| **UX_THREAD_PRIORITY_ENUM** | Este es el valor de prioridad de ThreadX para los subprocesos de enumeración de USBX que supervisa la topología de bus. |
| **UX_THREAD_PRIORITY_CLASS** | Este es el valor de prioridad de ThreadX para los subprocesos de USBX estándar. |
| **UX_THREAD_PRIORITY_KEYBOARD** | Este es el valor de prioridad de ThreadX para la clase de teclado HID de USBX. |
| **UX_THREAD_PRIORITY_DCD** | Este es el valor de prioridad de ThreadX para el subproceso de la controladora de dispositivos. |
| **UX_NO_TIME_SLICE** | Este valor define realmente la porción de tiempo que se va a usar para los subprocesos. Por ejemplo, si se ha definido en 0, el puerto de destino de ThreadX no utiliza porciones de tiempo. |
| **UX_MAX_SLAVE_CLASS_DRIVER** | Este es el número máximo de clases USBX que se pueden registrar mediante ux_device_stack_class_register. |
| **UX_MAX_SLAVE_LUN** | Este valor representa el número actual de unidades lógicas SCSI representadas en el controlador de la clase de almacenamiento de dispositivo. |
| **UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC** | Si se define, la clase de almacenamiento administrará los comandos multimedia (MMC), es decir, DVD-ROM. |
| **UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES** | Este valor representa el número de paquetes de NetX en el grupo de paquetes de la clase CDC-ECM. El valor predeterminado es 16. |
| **UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH** | Este valor representa el número máximo de bytes recibidos en un punto de conexión de control de la pila de dispositivos. El valor predeterminado es 256 bytes, pero se puede reducir en entornos con restricción de memoria. |
| **UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH** | Este valor representa la longitud máxima en bytes de un informe de HID. |
| **UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE** | Este valor representa el número máximo de informes de HID que se pueden poner en cola a la vez. |
| **UX_SLAVE_REQUEST_DATA_MAX_LENGTH** | Este valor representa el número máximo de bytes recibidos en un punto de conexión masivo de la pila de dispositivos. El valor predeterminado es 4096 bytes, pero se puede reducir en entornos con restricción de memoria. |

## <a name="source-code-tree"></a>Árbol de código fuente

Los archivos de USBX se proporcionan en varios directorios.

![Árbol de código fuente](media/usbx-device-stack/source-code-tree.png)

Para que los archivos sean reconocibles por sus nombres, se ha adoptado la siguiente convención:

| Nombre de sufijo de archivo  | Descripción del archivo                          |
| ----------------- | ----------------------------------------- |
| ux_host_stack   | archivos principales de pila de host de usbx                |
| ux_host_class   | archivos de clases de pila de host de usbx             |
| ux_hcd           | archivos de controlador de pila de host de usbx   |
| ux_device_stack | archivos principales de pila de dispositivo de usbx              |
| ux_device_class | archivos de clases de pila de dispositivo de usbx           |
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

El prototipo de ux_system_initialize es el siguiente:

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

Parámetros de entrada:

| Parámetro                          | Descripción                             |
| ---------------------------------- | --------------------------------------- |
| VOID *regular_memory_pool_start    | Inicio del bloque de memoria normal    |
| ULONG regular_memory_size          | Tamaño del bloque de memoria normal         |
| VOID *cache_safe_memory_pool_start | Inicio del bloque de memoria segura en caché |
| ULONG cache_safe_memory_size       | Tamaño del bloque de memoria segura en caché      |

No todos los sistemas requieren la definición de memoria segura en caché. En este tipo de sistema, los valores que se pasan durante la inicialización del puntero de memoria se establecerán en UX_NULL y el tamaño del bloque en 0. A continuación, USBX usará el bloque de memoria normal en lugar del bloque seguro en caché.

En un sistema en el que la memoria normal no es segura en caché y una controladora necesita hacer uso de la memoria DMA, es necesario definir un bloque de memoria en una zona segura en caché.

## <a name="uninitialization-of-usbx-resources"></a>Anulación de inicialización de recursos de USBX

USBX se puede finalizar mediante la liberación de sus recursos. Antes de finalizar USBX, todas las clases y los recursos del controlador deben finalizarse correctamente. La siguiente función anula la inicialización de los recursos de memoria de USBX:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

El prototipo de ux_system_initialize es el siguiente:

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a>Definición de la controladora de dispositivos USB

Solo se puede definir una controladora de dispositivos USB en un momento dado para que funcione en modo de dispositivo. El archivo de inicialización de la aplicación debe contener esta definición. La línea siguiente realiza la definición de una controladora USB genérica:

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

La inicialización del dispositivo USB tiene el siguiente prototipo:

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

con los parámetros siguientes:

| Parámetro               | Descripción                      |
| ------------------------ | -------------------------------- |
| ULONG dcd_io            | Dirección de la E/S de la controladora     |
| ULONG dcd_irq           | Interrupción usada por la controladora |
| ULONG dcd_vbus_address | Dirección del GPIO de VBUS         |

El ejemplo siguiente se corresponde con la inicialización de USBX en modo de dispositivo con la clase de dispositivo de almacenamiento y una controladora genérica:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a>Solución de problemas

USBX se entrega con un archivo de demostración y un entorno de simulación. Siempre es conveniente que la plataforma de demostración se ejecute en primer lugar, ya sea en el hardware de destino o en una plataforma de demostración específica.

## <a name="usbx-version-id"></a>Id. de la versión de USBX

La versión actual de USBX está disponible tanto para el software de usuario como para el de aplicación durante el tiempo de ejecución. El programador puede obtener la versión de USBX si examina el archivo ***ux_port.h** _. Además, este archivo también contiene un historial de versiones del puerto correspondiente. El software de aplicación puede obtener la versión de USBX si examina la cadena global _ *_ _ux_version_id_* _, que se define en _*_ux_port.h_**.
