---
title: API de clases de host de USBX
description: En este capítulo se tratan todas las API expuestas de las clases de host de USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28e733e37b06da7053f238e23e2b8b8046df2dd9940e50cd0321ccf15c27ec47
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802114"
---
# <a name="chapter-2-usbx-host-classes-api"></a>Capítulo 2: API de clases de host de USBX

En este capítulo se tratan todas las API expuestas de las clases de host de USBX. Se describen en detalle las siguientes API de cada clase.

- Clase Printer
- Clase Audio
- Clase Asix
- Clase Pima/PTP
- Clase Prolific
- Clase Generic Serial

## <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

Lectura desde la interfaz de la impresora.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Descripción

Esta función lee desde la interfaz de la impresora. La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia. Solo se permite la lectura en impresoras bidireccionales.

### <a name="parameters"></a>Parámetros

- **printer**: puntero que señala a la instancia de la clase printer.
- **data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.
- **requested_length**: longitud que se va a recibir.
- **actual_length**: longitud recibida realmente.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54): no se admite la función porque la impresora no es bidireccional.
- **UX_TRANSFER_TIMEOUT**: (0x5c): se agotó el tiempo de espera de la transferencia, lectura incompleta.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

Escritura en la interfaz de la impresora.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Descripción

Esta función escribe en la interfaz de la impresora. La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia.

### <a name="parameters"></a>Parámetros

- **printer**: puntero que señala a la instancia de la clase printer.
- **data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.
- **requested_length**: longitud que se va a enviar.
- **actual_length**: longitud enviada realmente.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, escritura incompleta.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

Realización de un restablecimiento parcial de la impresora.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a>Descripción

Realiza un restablecimiento parcial de la impresora.

### <a name="input-parameter"></a>Parámetro de entrada

- **printer**: puntero que señala a la instancia de la clase printer.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): se ha completado el restablecimiento.
- **UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, restablecimiento incompleto.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

Obtención del estado de la impresora.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a>Descripción

Esta función obtiene el estado de la impresora. El estado de la impresora es similar al estado LPT (estándar 1284).

### <a name="parameters"></a>Parámetros

- **printer**: puntero que señala a la instancia de la clase printer.
- **printer_status**: dirección del estado que se va a devolver.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): se ha completado el restablecimiento.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para realizar la operación.
- **UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, restablecimiento incompleto.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a>ux_host_class_printer_device_id_get

Obtención del identificador de dispositivo de la impresora.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a>Descripción

Esta función obtiene la cadena de identidad del dispositivo IEEE 1284 de la impresora (incluida la longitud de los dos primeros bytes en formato big endian).

### <a name="parameters"></a>Parámetros

- **printer**: puntero que señala a la instancia de la clase printer.
- **descriptor_buffer**: puntero que señala a un búfer para llenar la cadena de identidad del dispositivo IEEE 1284 (incluida la longitud de los dos primeros bytes en formato BE). 
- **length**: longitud del búfer en bytes.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): la operación se ha realizado correctamente.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para realizar la operación.
- **UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, solicitud incompleta.
- **UX_TRANSFER_NOT_READY**: (0x25): el dispositivo estaba en un estado no válido; debe estar en los estados ATTACHED, ADDRESSED o CONFIGURED.
- **UX_TRANSFER_STALL**: (0x21): se ha detenido la transferencia.
- **TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.
- **TX_SEMAPHORE_ERROR** (0x0C): puntero del semáforo de recuento no válido.
- **TX_WAIT_ERROR** (0x04): se ha especificado una opción de espera distinta de TX_NO_WAIT en una llamada de un no subproceso.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

Lectura desde la interfaz de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a>Descripción

Esta función lee desde la interfaz de audio. La llamada no es de bloqueo. La aplicación debe asegurarse de que se ha seleccionado la configuración alternativa adecuada para la interfaz de transmisión de audio.

### <a name="parameters"></a>Parámetros

- **audio**: puntero que señala a la instancia de clase de audio.
- **audio_transfer_request**: puntero que señala a la estructura de transferencia de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_FUNCTION_NOT_SUPPORTED**" (0x54): función no admitida.

### <a name="example"></a>Ejemplo

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

Escritura en la interfaz de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a>Descripción

Esta función escribe en la interfaz de audio. La llamada no es de bloqueo. La aplicación debe asegurarse de que se ha seleccionado la configuración alternativa adecuada para la interfaz de transmisión de audio.

### <a name="parameters"></a>Parámetros

- **audio**: puntero que señala a la instancia de clase de audio.
- **audio_transfer_request**: puntero que señala a la estructura de transferencia de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.
- **ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a>ux_host_class_audio_control_get

Obtención de un control específico de la interfaz de control de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a>Descripción

Esta función lee un control específico de la interfaz de control de audio.

### <a name="parameters"></a>Parámetros

- **audio**: puntero que señala a la instancia de clase de audio.
- **audio_control**: puntero que señala a la estructura de control de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

Establecimiento de un control específico en la interfaz de control de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

**Descripción**

Esta función establece un control específico en la interfaz de control de audio.

### <a name="parameters"></a>Parámetros

- **audio**: puntero que señala a la instancia de clase de audio.
- **audio_control**: puntero que señala a la estructura de control de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.

### <a name="example"></a>Ejemplo

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

Establecimiento de una interfaz de configuración alternativa de la interfaz de transmisión de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a>Descripción

Esta función establece la interfaz de configuración alternativa adecuada de la interfaz de transmisión de audio según una estructura de muestreo específica.

### <a name="parameters"></a>Parámetros

- **audio**: puntero que señala a la instancia de clase de audio.
- **audio_sampling**: puntero que señala a la estructura de muestreo de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.
- **UX_NO_ALTERNATE_SETTING**: (0x5e): no hay valores alternativos para los valores de muestreo.

### <a name="example"></a>Ejemplo

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

Obtención de los ajustes de muestreo posibles de la interfaz de transmisión de audio.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a>Descripción

Esta función obtiene, de uno en uno, todos los ajustes de muestreo posibles disponibles en cada una de las configuraciones alternativas de la interfaz de transmisión de audio. La primera vez que se usa la función, se deben restablecer todos los campos del puntero de la estructura de llamada. La función devolverá un conjunto específico de valores de transmisión por secuencias a menos que se haya alcanzado el final de la configuración alternativa. Cuando se vuelva a usar esta función, se usarán los valores de muestreo anteriores para buscar los siguientes valores de muestreo.

### <a name="parameters"></a>Parámetros

- **audio**: puntero que señala a la instancia de clase de audio.
- **audio_sampling**: puntero que señala a la estructura de muestreo de audio.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.
- **UX_NO_ALTERNATE_SETTING**: (0x5e): no hay valores alternativos para los valores de muestreo.

### <a name="example"></a>Ejemplo

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

Lectura desde la interfaz ASIX.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Descripción

Esta función lee desde la interfaz ASIX. La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia.

### <a name="parameters"></a>Parámetros

- **ASIX**: puntero que señala a la instancia de la clase ASIX.
- **data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.
- **requested_length**: longitud que se va a recibir.
- **actual_length**: longitud recibida realmente.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, lectura incompleta.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

Escritura en la interfaz ASIX.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a>Descripción

Esta función escribe en la interfaz ASIX. La llamada no es de bloqueo.

### <a name="parameters"></a>Parámetros

- **ASIX**: puntero que señala a la instancia de la clase ASIX.
- **packet**: paquete de datos NetX

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_ERROR**: (0xFF): no se pudo solicitar la transferencia.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

Apertura de una sesión entre el iniciador y el respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Descripción

Esta función abre una sesión entre un iniciador PIMA y un respondedor PIMA. Una vez que se abre una sesión correctamente, la mayoría de los comandos PIMA se pueden ejecutar.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la sesión se ha abierto correctamente.
- **UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E): la sesión ya está abierta.

### <a name="example"></a>Ejemplo

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

Cierre de una sesión entre el iniciador y el respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Descripción

Esta función cierra una sesión que se abrió previamente entre un iniciador PIMA y un respondedor PIMA. Una vez que se cierra una sesión, la mayoría de los comandos PIMA ya no se pueden ejecutar.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la sesión se ha cerrado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.

### <a name="example"></a>Ejemplo

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a>ux_host_class_pima_storage_ids_get

Obtención de la matriz del identificador de almacenamiento del respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a>Descripción

Esta función obtiene la matriz de identificación de almacenamiento del respondedor.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **storage_ids_array**: matriz en la que se devolverán los identificadores de almacenamiento.
- **storage_id_length**: longitud de la matriz de almacenamiento.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): se ha rellenado la matriz de identificación del almacenamiento.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.

### <a name="example"></a>Ejemplo

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

Obtención de la información de almacenamiento del respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a>Descripción

Esta función obtiene la información de almacenamiento de un contenedor de almacenamiento con el valor *storage_id*.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **storage_id**: identificador del contenedor de almacenamiento.
- **storage**: puntero que señala a un contenedor de información de almacenamiento.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): se ha recuperado la información de almacenamiento.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_MEMORY_INSUFFICIENT** (0x12): no hay suficiente memoria para crear el comando PIMA.

### <a name="example"></a>Ejemplo

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a>ux_host_class_pima_num_objects_get

Obtención del número de objetos de un contenedor de almacenamiento del respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a>Descripción

Esta función obtiene el número de objetos almacenados en un contenedor de almacenamiento específico con el valor storage_id que coincide con un código de formato específico. El número de objetos se devuelve en el campo ux_host_class_pima_session_nb_objects de la estructura pima_session.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **storage_id**: identificador del contenedor de almacenamiento.
- **object_format_code**: filtro del código de formato de los objetos.

Los códigos de formato de los objetos pueden tener uno de estos valores.

| Código de formato de objeto               | Descripción   |     Código de USBX                          |
|----------------------------------|---------------|------------------------------------------|
| 0x3000                           | Objeto no definido que no es una imagen | UX_HOST_CLASS_PIMA_OFC_UNDEFINED   |
| 0x3001                           | Asociación (por ejemplo, carpeta) | UX_HOST_CLASS_PIMA_OFC_ASSOCIATION |
| 0x3002                           | Script específico del modelo de dispositivo | UX_HOST_CLASS_PIMA_OFC_SCRIPT      |
| 0x3003                           | Archivo ejecutable binario específico del modelo de dispositivo | UX_HOST_CLASS_PIMA_OFC_EXECUTABLE  |
| 0x3004                           | Archivo de texto  |   UX_HOST_CLASS_PIMA_OFC_TEXT        |
| 0x3005                           | Archivo de lenguaje de marcado de hipertexto, HTML (texto) | UX_HOST_CLASS_PIMA_OFC_HTML        |
| 0x3006                           | Archivo de formato de orden de impresión digital, DPOF (texto) | UX_HOST_CLASS_PIMA_OFC_DPOF        |
| 0x3007                           | Clip de audio AIFF  |  UX_HOST_CLASS_PIMA_OFC_AIFF        |
| 0x3008                           | Clip de audio WAV   |  UX_HOST_CLASS_PIMA_OFC_WAV         |
| 0x3009                           | Clip de audio MP3   |  UX_HOST_CLASS_PIMA_OFC_MP3         |
| 0x300A                           | Clip de vídeo AVI   |  UX_HOST_CLASS_PIMA_OFC_AVI         |
| 0x300B                           | Clip de vídeo MPEG  |  UX_HOST_CLASS_PIMA_OFC_MPEG        |
| 0x300C                           | Advanced Streaming Format de Microsoft, ASF (vídeo) | UX_HOST_CLASS_PIMA_OFC_ASF         |
| 0x3800                           | Objeto de imagen desconocido sin definir | UX_HOST_CLASS_PIMA_OFC_QT          |
| 0x3801                           | Exchangeable Image File Format (EXIF/JPEG), estándar JEIDA | UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG   |
| 0x3802                           | Tagged Image File Format para fotografía electrónica (TIFF/EP) | UX_HOST_CLASS_PIMA_OFC_TIFF_EP     |
| 0x3803                           | Formato de imagen de almacenamiento estructurado FlashPix | UX_HOST_CLASS_PIMA_OFC_FLASHPIX    |
| 0x3804                           | Archivo de mapa de bits de Microsoft Windows (BMP) | UX_HOST_CLASS_PIMA_OFC_BMP         |
| 0x3805                           | Formato de archivo de imagen de cámara Canon (CIFF) | UX_HOST_CLASS_PIMA_OFC_CIFF        |
| 0x3806                           | Reservado sin definir |  |
| 0x3807                           | Formato de intercambio de gráficos (GIF) | UX_HOST_CLASS_PIMA_OFC_GIF         |
| 0x3808                           | Formato de intercambio de archivos (JPEG/JFIF) | UX_HOST_CLASS_PIMA_OFC_JFIF        |
| 0x3809                           | PhotoCD Image Pac (PCD) | UX_HOST_CLASS_PIMA_OFC_PCD         |
| 0x380A                           | Formato de imagen de Quickdraw (PICT) | UX_HOST_CLASS_PIMA_OFC_PICT        |
| 0x380B                           | Portable Network Graphics (PNG) | UX_HOST_CLASS_PIMA_OFC_PNG         |
| 0x380C                           | Reservado sin definir |   |
| 0x380D                           | Tag Image File Format (TIFF) | UX_HOST_CLASS_PIMA_OFC_TIFF        |
| 0x380E                           | Tag Image File Format para tecnologías de la información, TIFF/IT (artes gráficas) | UX_HOST_CLASS_PIMA_OFC_TIFF_IT     |
| 0x380F                           | Formato de archivo de base de referencia JPEG2000 (JP2) | UX_HOST_CLASS_PIMA_OFC_JP2         |
| 0x3810                           | Formato de archivo extendido JPEG2000 (JPX) | UX_HOST_CLASS_PIMA_OFC_JPX         |
| Resto de códigos con un MSN de 0011 | Cualquier reservado sin definir para uso futuro |                                    |
| Resto de códigos con un MSN de 1011 | Cualquier tipo definido por el fabricante: imagen |                                    |

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.

### <a name="example"></a>Ejemplo

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a>ux_host_class_pima_object_handles_get

Obtención de identificadores de objeto del respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a>Descripción

Devuelve una matriz de identificadores de objetos presentes en el contenedor de almacenamiento indicado por el parámetro storage_id. Si quiere una lista agregada en todos los almacenes, este valor se establecerá en 0xFFFFFFFF.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **object_handes_array**: matriz en la que se devuelven los identificadores.
- **object_handles_length**: longitud de la matriz.
- **storage_id**: identificador del contenedor de almacenamiento.
- **object_format_code**: código de formato del objeto (consulte la tabla para la función ux_host_class_pima_num_objects_get).
- **object_handle_association**: valor de asociación de objeto opcional.

La asociación del identificador de objeto puede ser uno de los valores de la tabla siguiente:

| AssociationCode                        | AssociationType      | Interpretación       |
|----------------------------------------|----------------------|----------------------|
| 0x0000                                 | No definido            | No definido            |
| 0x0001                                 | GenericFolder        | No utilizado               |
| 0x0002                                 | Álbum                | Reservado             |
| 0x0003                                 | TimeSequence         | DefaultPlaybackDelta |
| 0x0004                                 | HorizontalPanoramic  | No utilizado               |
| 0x0005                                 | VerticalPanoramic    | No utilizado               |
| 0x0006                                 | 2DPanoramic          | ImagesPerRow         |
| 0x0007                                 | AncillaryData        | No definido            |
| Resto de valores con el bit 15 establecido en 0  | Reservado             | No definido            |
| Resto de valores con el bit 15 establecido en 1        | Vendor-Defined       | Vendor-Defined       |

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.

### <a name="example"></a>Ejemplo

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

Obtención de la información del objeto del respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Descripción

Esta función obtiene la información de objeto de un identificador de objeto.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **object_handle**: identificador del objeto.
- **object**: puntero que señala al contenedor de información del objeto.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.

### <a name="example"></a>Ejemplo

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

Envío de la información del objeto al respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Descripción

Esta función envía la información de almacenamiento de un contenedor de almacenamiento con el valor storage_id. El iniciador debe usar este comando antes de enviar un objeto al respondedor.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **storage_id**: identificador del almacenamiento de destino.
- **parent_object_id**: ObjectHandle primario en el respondedor donde debe colocarse el objeto.
- **object**: puntero que señala al contenedor de información del objeto.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.

### <a name="example"></a>Ejemplo

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a>ux_host_class_pima_object_open

Apertura de un objeto almacenado en el respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Descripción

Esta función abre un objeto en el respondedor antes de la lectura o escritura.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **object_handle**: identificador del objeto.
- **object**: puntero que señala al contenedor de información del objeto.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) El objeto ya se ha abierto.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.

### <a name="example"></a>Ejemplo

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

Obtención de un objeto almacenado en el respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a>Descripción

Esta función obtiene un objeto del respondedor.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **object_handle**: identificador del objeto.
- **object**: puntero que señala al contenedor de información del objeto.
- **object_buffer**: dirección de los datos del objeto.
- **object_buffer_length**: longitud solicitada del objeto.
- **object_actual_length**: longitud del objeto devuelto.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): se ha transferido el objeto.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023): el objeto no está abierto.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f): acceso al objeto denegado.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007): la transferencia no está completa.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.
- **UX_TRANSFER_ERROR**: (0x23): error de transferencia al leer el objeto.

### <a name="example"></a>Ejemplo

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a>ux_host_class_pima_object_send

Envío de un objeto almacenado en el respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a>Descripción

Esta función envía un objeto al respondedor.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **object_handle**: identificador del objeto.
- **object**: puntero que señala al contenedor de información del objeto.
- **object_buffer**: dirección de los datos del objeto.
- **object_buffer_length**: longitud solicitada del objeto.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023): el objeto no está abierto.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f): acceso al objeto denegado.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007): la transferencia no está completa.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.
- **UX_TRANSFER_ERROR**: (0x23): error de transferencia durante la escritura del objeto.

### <a name="example"></a>Ejemplo

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

Obtención de un objeto thumb almacenado en el respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a>Descripción

Esta función obtiene un objeto thumb del respondedor.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **object_handle**: identificador del objeto.
- **object**: puntero que señala al contenedor de información del objeto.
- **thumb_buffer**: dirección de los datos del objeto thumb.
- **thumb_buffer_length**: longitud solicitada del objeto thumb.
- **thumb_actual_length**: longitud del objeto thumb devuelto.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023): el objeto no está abierto.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Acceso al objeto denegado.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) La transferencia no está completa.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.
- **UX_TRANSFER_ERROR**: (0x23): error de transferencia al leer el objeto.

### <a name="example"></a>Ejemplo

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

Eliminación de un objeto almacenado en el respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a>Descripción

Esta función elimina un objeto en el respondedor.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **object_handle**: identificador del objeto.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): se ha eliminado el objeto.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f): no se puede eliminar el objeto.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.

### <a name="example"></a>Ejemplo

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

Cierre de un objeto almacenado en el respondedor.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Descripción

Esta función cierra un objeto en el respondedor.

### <a name="parameters"></a>Parámetros

- **pima**: puntero que señala a la instancia de clase PIMA.
- **pima_session**: puntero que señala a la sesión PIMA.
- **object_handle**: identificador del objeto.
- **object**: puntero que señala al objeto.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00) Se cerró el objeto.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023): el objeto no está abierto.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.

### <a name="example"></a>Ejemplo

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a>ux_host_class_gser_read

Lectura desde la interfaz serie genérica.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Descripción

Esta función lee desde la interfaz serie genérica. La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia.

### <a name="parameters"></a>Parámetros

- **gser**: puntero que señala a la instancia de la clase gser.
- **interface_index**: índice de interfaz desde el que se va a leer.
- **data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.
- **requested_length**: longitud que se va a recibir.
- **actual_length**: longitud recibida realmente.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, lectura incompleta.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a>ux_host_class_gser_write

Escritura desde la interfaz serie genérica.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Descripción

Esta función escribe desde la interfaz serie genérica. La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia.

### <a name="parameters"></a>Parámetros

- **gser**: puntero que señala a la instancia de la clase gser.
- **interface_index**: interfaz en la que se va a escribir.
- **data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.
- **requested_length**: longitud que se va a enviar.
- **actual_length**: longitud enviada realmente.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, escritura incompleta.

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a>ux_host_class_gser_ioctl

Realización de una función IOCTL en la interfaz serie genérica.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a>Descripción

Esta función realiza una función IOCTL específica en la interfaz gser. La llamada produce un bloqueo, y solo devuelve cuando hay un error o cuando se completa el comando.

### <a name="parameters"></a>Parámetros

- **gser**: puntero que señala a la instancia de la clase gser.
- **ioctl_function**: función IOCTL que se va a realizar. Vea la tabla siguiente para ver las funciones IOCTL permitidas.
- **parameter**: puntero que señala a un parámetro específico de IOCTL.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.
- **UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria.
- **UX_HOST_CLASS_UNKNOWN**: (0x59): la instancia de clase es incorrecta.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54): la función de IOCTL es desconocida.

### <a name="ioctl-functions"></a>Funciones IOCTL

- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK
- UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS

### <a name="example"></a>Ejemplo

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a>ux_host_class_gser_reception_start

Inicio de la recepción en la interfaz serie genérica.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Descripción

Esta función inicia la recepción en la interfaz de clase serie genérica. Esta función permite la recepción sin bloqueo. Cuando se recibe un búfer, se invoca una devolución de llamada en la aplicación.

### <a name="parameters"></a>Parámetros

- **gser**: puntero que señala a la instancia de la clase gser.
- **gser_reception**: estructura que contiene los parámetros de recepción.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.
- **UX_HOST_CLASS_UNKNOWN** (0x59): la instancia de clase es incorrecta.
- **UX_ERROR** (0x01): error

### <a name="example"></a>Ejemplo

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a>ux_host_class_gser_reception_stop

Detención de recepción en la interfaz serie genérica.

### <a name="prototype"></a>Prototipo

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Descripción

Esta función detiene la recepción en la interfaz de clase serie genérica.

### <a name="parameters"></a>Parámetros

- **gser**: puntero que señala a la instancia de la clase gser.
- **gser_reception**: estructura que contiene los parámetros de recepción.

### <a name="return-value"></a>Valor devuelto

- **UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.
- **UX_HOST_CLASS_UNKNOWN** (0x59): la instancia de clase es incorrecta.
- **UX_ERROR** (0x01): error

### <a name="example"></a>Ejemplo

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
