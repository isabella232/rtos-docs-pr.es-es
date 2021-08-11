---
title: 'Capítulo 5: API de clases de host de USBX'
description: Obtenga información sobre la API de clases de host de USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 2e9e2e0286300b3f79f7f9e6ad2d7fab96ba7337
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115177752"
---
# <a name="chapter-5---usbx-host-classes-api"></a>Capítulo 5: API de clases de host de USBX

En este capítulo se tratan todas las API expuestas de las clases de host de USBX. Se describen en detalle las siguientes API de cada clase.

- Clase HID
- Clase CDC/ACM
- Clase CDC/ECM
- Clase de almacenamiento

## <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

Registra un cliente HID en la clase HID.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a>Descripción

Esta función se usa para registrar un cliente HID en la clase HID. La clase HID debe encontrar una coincidencia entre un dispositivo HID y el cliente HID antes de solicitar datos de este dispositivo.

> [!NOTE]
> La cadena de C de hid_client_name debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.

### <a name="parameters"></a>Parámetros

- **hid_client_name**: puntero al nombre del cliente HID.
- **hid_client_handler**: puntero al controlador del cliente HID.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.
- **UX_MEMORY_INSUFFICIENT** (0X12): error de asignación de memoria para el cliente.
- **UX_MEMORY_ARRAY_FULL** (0X1a): ya se ha registrado el número máximo de clientes.
- **UX_HOST_CLASS_ALREADY_INSTALLED** (0X58): esta clase ya existe.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a>ux_host_class_hid_report_callback_register

Registra una devolución de llamada de la clase HID.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a>Descripción

Esta función se usa para registrar una devolución de llamada de la clase HID al cliente HID cuando se recibe un informe.

### <a name="parameters"></a>Parámetros

- **HID**: puntero a la instancia de la clase HID.
- **call_back**: puntero a la estructura de devolución de llamada.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): instancia de HID no válida.
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0x79): error en el registro de devolución de llamada del informe.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a>ux_host_class_hid_periodic_report_start

Inicia el punto de conexión periódico para una instancia de clase HID.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a>Descripción

Esta función se usa para iniciar el punto de conexión (interrupción) periódico de la instancia de la clase HID enlazada a este cliente HID. La clase HID no puede iniciar el punto de conexión periódico hasta que se active el cliente HID y, por lo tanto, es el cliente HID quien tiene que iniciar este punto de conexión para recibir informes.

### <a name="input-parameter"></a>Parámetro de entrada

- **HID** Puntero a la instancia de la clase HID.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): los informes periódicos se han iniciado correctamente.
- **ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A): error en el informe periódico.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a>ux_host_class_hid_periodic_report_stop

Detiene el punto de conexión periódico para una instancia de clase HID.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a>Descripción

Esta función se usa para detener el punto de conexión (interrupción) periódico de la instancia de la clase HID enlazada a este cliente HID. La clase HID no puede detener el punto de conexión periódico hasta que se desactive el cliente HID y se liberen todos sus recursos, por lo tanto, es el cliente HID quien tiene que detener este punto de conexión.

### <a name="input-parameter"></a>Parámetro de entrada

- **HID** Puntero a la instancia de la clase HID.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): los informes periódicos se detuvieron correctamente.
- **ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A): error en el informe periódico.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

Obtiene un informe de una instancia de la clase HID.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a>Descripción

Esta función se usa para recibir un informe directamente del dispositivo sin depender del punto de conexión periódico. Este informe procede del punto de conexión de control, pero su tratamiento es el mismo que si estuviera en el punto de conexión periódico.

### <a name="parameters"></a>Parámetros

- **HID**: puntero a la instancia de la clase HID.
- **client_report**: puntero al informe de cliente HID.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): el informe se ha recibido correctamente.
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0X70): el informe de cliente no era válido o se produjo un error durante la transferencia.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.
- **UX_BUFFER_OVERFLOW** (0X5d): el búfer proporcionado no es suficientemente grande para alojar el informe sin comprimir.

### <a name="example"></a>Ejemplo

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

Envía un informe.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a>Descripción

Esta función se usa para enviar un informe directamente al dispositivo.

### <a name="parameters"></a>Parámetros

- **HID**: puntero a la instancia de la clase HID.
- **client_report**: puntero al informe de cliente HID.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): el informe se ha enviado correctamente.
- **UX_HOST_CLASS_HID_REPORT_ERROR** (0X70): el informe de cliente no era válido o se produjo un error durante la transferencia.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.
- **UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0X5d): el búfer proporcionado no es suficientemente grande para alojar el informe sin comprimir.

### <a name="example"></a>Ejemplo

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a>ux_host_class_hid_mouse_buttons_get

Obtiene los botones del mouse.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a>Descripción

Esta función se usa para obtener los botones del mouse.

### <a name="parameters"></a>Parámetros

- **mouse_instance**: puntero a la instancia del mouse HID.
- **mouse_buttons**: puntero a los botones devueltos.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): se recuperó correctamente el botón del mouse.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.

### <a name="example"></a>Ejemplo

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a>ux_host_class_hid_mouse_position_get

Obtiene la posición del mouse.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a>Descripción

Esta función se usa para obtener la posición del mouse en coordenadas X e Y.

### <a name="parameters"></a>Parámetros

- **mouse_instance**: puntero a la instancia del mouse HID.
- **mouse_x_position**: puntero a la coordenada X.
- **mouse_y_position**: puntero a la coordenada Y.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): se han recuperado correctamente las coordenadas X e Y.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.

### <a name="example"></a>Ejemplo

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a>ux_host_class_hid_keyboard_key_get

Obtiene la tecla y el estado del teclado.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a>Descripción

Esta función se usa para obtener la tecla y el estado del teclado.

### <a name="parameters"></a>Parámetros

- **keyboard_instance**: puntero a la instancia del teclado HID.
- **keyboard_key**: puntero al contenedor de claves del teclado.
- **keyboard_state**: puntero al contenedor de estados del teclado.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0x00): se han recuperado correctamente la clave y el estado.
- **UX_ERROR** (0Xff): no hay nada que notificar.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.

El estado del teclado puede tener los siguientes valores:

- **UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000
- **UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001
- **UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002
- **UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004
- **UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007
- **UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100
- **UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200
- **UX_HID_KEYBOARD_STATE_SHIFT** 0x0300
- **UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400
- **UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800
- **UX_HID_KEYBOARD_STATE_ALT** 0x0a00
- **UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000
- **UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000
- **UX_HID_KEYBOARD_STATE_CTRL** 0x3000
- **UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000
- **UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000
- **UX_HID_KEYBOARD_STATE_GUI** 0xa000

### <a name="example"></a>Ejemplo

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a>ux_host_class_hid_keyboard_ioctl

Realiza una función IOCTL en el teclado HID.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a>Descripción

Esta función realiza una función IOCTL específica en el teclado HID. La llamada produce un bloqueo, y solo devuelve un resultado cuando hay un error o cuando se completa el comando.

### <a name="parameters"></a>Parámetros

- **keyboard_instance**: puntero a la instancia del teclado HID.
- **ioctl_function**: función IOCTL que se va a realizar. Vea la tabla siguiente para ver una de las funciones IOCTL permitidas.
- **parameter**: puntero a un parámetro específico de IOCTL.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): la función IOCTL se ha completado correctamente.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54): función IOCTL desconocida.

### <a name="ioctl-functions"></a>Funciones IOCTL

- UX_HID_KEYBOARD_IOCTL_SET_LAYOUT
- UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE
- UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE

### <a name="example--change-keyboard-layout"></a>Ejemplo: cambio de la distribución del teclado

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a>Ejemplo: deshabilitación de la descodificación de teclas del teclado

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a>ux_host_class_hid_remote_control_usage_get

Obtención del uso del control remoto

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a>Descripción

Esta función se usa para obtener los usos del control remoto.

### <a name="parameters"></a>Parámetros

- **remote_control_instance**: puntero a la instancia del control remoto HID.
- **usage**: puntero al uso.
- **value**: puntero al valor del uso.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.
- **UX_ERROR** (0Xff): no hay nada que notificar.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.

La lista de todos los usos posibles es demasiado larga para caber en esta guía de usuario. Si quiere obtener una descripción completa, ux_host_class_hid.h tiene el conjunto completo de valores posibles.

### <a name="example"></a>Ejemplo

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

Lee desde la interfaz cdc_acm.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a>Descripción

Esta función lee desde la interfaz cdc_acm. La llamada produce un bloqueo, y solo devuelve un resultado cuando hay un error o cuando se completa la transferencia.

> [!Note]
> Esta función lee datos masivos sin procesar del dispositivo, por lo que se mantiene en estado pendiente hasta que el búfer está lleno o el dispositivo finaliza la transferencia mediante un paquete corto (incluido el paquete de longitud cero). Para más información, consulte [**Consideraciones generales sobre la transferencia masiva**](usbx-device-stack-5.md#general-considerations-for-bulk-transfer).

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase cdc_acm.
- **data_pointer**: puntero a la dirección del búfer de la carga de datos.
- **requested_length**: longitud que se va a recibir.
- **actual_length**: longitud recibida realmente.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b): la instancia de cdc_acm no es válida.
- **UX_TRANSFER_TIMEOUT** (0x5c): se ha agotado el tiempo de espera de la transferencia, lectura incompleta.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a>ux_host_class_cdc_acm_write

Escribe en la interfaz cdc_acm.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a>Descripción

Esta función escribe en la interfaz cdc_acm. La llamada produce un bloqueo, y solo devuelve un resultado cuando hay un error o cuando se completa la transferencia.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase cdc_acm.
- **data_pointer**: puntero a la dirección del búfer de la carga de datos.
- **requested_length**: longitud que se va a enviar.
- **actual_length**: longitud enviada realmente.

### <a name="return-values"></a>Valores devueltos

- **UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b): la instancia de cdc_acm no es válida.
- **UX_TRANSFER_TIMEOUT** (0x5c): se ha agotado el tiempo de espera de la transferencia, escritura incompleta.

### <a name="example"></a>Ejemplo

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a>ux_host_class_cdc_acm_ioctl

Realiza una función IOCTL en la interfaz cdc_acm.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a>Descripción

Esta función realiza una función IOCTL específica en la interfaz cdc_acm. La llamada produce un bloqueo, y solo devuelve un resultado cuando hay un error o cuando se completa el comando.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase cdc_acm.
- **ioctl_function**: función IOCTL que se va a realizar. Vea la tabla siguiente para ver una de las funciones IOCTL permitidas.
- **parameter**: puntero a un parámetro específico de IOCTL.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.
- **UX_MEMORY_INSUFFICIENT** (0X12): no tiene suficiente memoria.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b): la instancia de CDC_ACM no tiene un estado válido.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54): función IOCTL desconocida.

### <a name="ioctl-functions"></a>Funciones IOCTL:

- UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK
- UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

Comienza la recepción en segundo plano de los datos del dispositivo.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a>Descripción

Esta función hace que USBX lea continuamente los datos del dispositivo en segundo plano. Tras la finalización de cada transacción, se invoca la devolución de llamada especificada en **cdc_acm_reception** para que la aplicación pueda realizar un procesamiento posterior de los datos de la transacción.

> [!NOTE]
> No se debe usar **ux_host_class_cdc_acm_read** mientras la recepción en segundo plano esté en uso.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase cdc_acm.
- **cdc_acm_reception**: puntero al parámetro que contiene valores que definen el comportamiento de la recepción en segundo plano. El diseño de este parámetro es el siguiente:

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): se ha iniciado correctamente la recepción en segundo plano.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): instancia de clase no válida.

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

Detiene la recepción en segundo plano de los paquetes.

### <a name="prototype"></a>Prototipo

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a>Descripción

Esta función hace que USBX detenga la recepción en segundo plano iniciada previamente por **ux_host_class_cdc_acm_reception_start**.

### <a name="parameters"></a>Parámetros

- **cdc_acm**: puntero a la instancia de la clase cdc_acm.
- **cdc_acm_reception**: puntero al mismo parámetro que se usó para iniciar la recepción en segundo plano. El diseño de este parámetro es el siguiente:

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): se ha detenido correctamente la recepción en segundo plano.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): instancia de clase no válida.

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
