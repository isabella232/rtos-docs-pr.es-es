---
title: 'Capítulo 3: Descripción de los servicios del cliente PTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del cliente PTP de NetX Duo por orden alfabético.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814589"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a>Capítulo 3: Descripción de los servicios del cliente PTP de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios del cliente PTP de NetX Duo (se enumeran a continuación) por orden alfabético.

[!NOTE]
> *En la sección **Valores devueltos** de las siguientes descripciones de funciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.*

## <a name="nx_ptp_client_create"></a>nx_ptp_client_create

Cree una instancia de cliente PTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente PTP.

Tenga en cuenta que la aplicación debe crear primero una instancia de IP y un grupo de paquetes para que el cliente PTP transmita paquetes. En el caso del grupo de paquetes, la aplicación puede usar el mismo grupo de paquetes en la instancia de IP; o bien, puede crear un grupo de paquetes dedicado para el cliente PTP.  La estrategia de usar un grupo de paquetes dedicado tiene la ventaja de usar paquetes pequeños (paquetes de 128 bytes si se usa IPv6, o 108 bytes para IPv4 solamente).

### <a name="input-parameters"></a>Parámetros de entrada
* **client_ptr** Puntero al cliente PTP que se va a crear
* **ip_ptr** Puntero a la instancia de IP
* **interface_index** Índice de la interfaz de red PTP
* **packet_pool_ptr** Puntero al grupo de paquetes del cliente
* **thread_priority** Prioridad del subproceso PTP
* **thread_stack** Puntero a la pila de subprocesos
* **stack_size** Tamaño de la pila de subprocesos
* **clock_callback** Devolución de llamada del reloj PTP
* **clock_callback_data** Datos de la devolución de llamada del reloj

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0x00) El cliente se creó correctamente
* **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) La carga útil del paquete es demasiado pequeña
* **NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Error de devolución de llamada del reloj
* **status** Finalización del estado de las llamadas al servicio NetX Duo y ThreadX
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada
* NX_INVALID_INTERFACE (0x4C) Interfaz no válida

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a>nx_ptp_client_delete

Elimina una instancia de cliente PTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente PTP.

### <a name="input-parameters"></a>Parámetros de entrada
* **client_ptr** Puntero al cliente PTP que se va a eliminar

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0x00) Cliente eliminado correctamente
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a>nx_ptp_client_master_info_get

Obtenga la información del reloj principal.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a>Descripción
Este servicio obtiene información del reloj principal. El bloque de control principal se pasa a la aplicación de usuario a través de la función de devolución de llamada del evento.

### <a name="input-parameters"></a>Parámetros de entrada
* **master_ptr** Puntero al reloj PTP principal
* **address** Dirección del reloj principal
* **port_identity** Identidad y puerto principal PTP
* **port_identity_length** Longitud de la identidad y el puerto principal PTP
* **priority1** Prioridad 1 del reloj PTP principal
* **priority2** Prioridad 2 del reloj PTP principal
* **clock_class** Clase del reloj PTP principal
* **clock_accuracy** Precisión del reloj PTP principal
* **clock_variance** Varianza del reloj PTP principal
* **grandmaster_identity** Identidad del reloj Grandmaster
* **grandmaster_identity_length** Longitud de la identidad de Grandmaster
* **steps_removed** Etapas eliminadas del encabezado PTP
* **time_source** El origen del que usa el reloj Grandmaster

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0X00) Información del reloj principal obtenida correctamente
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a>nx_ptp_client_packet_timestamp_notify

Notifique al cliente PTP la marca de tiempo del paquete.

### <a name="prototype"></a>Prototipo

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a>Descripción
Este servicio notifica al cliente PTP que el paquete se transmitió con una marca de tiempo. Este servicio está diseñado para el controlador de red y se invoca cuando se transmite el paquete. Normalmente, la marca de tiempo se genera mediante hardware.

### <a name="input-parameters"></a>Parámetros de entrada
* **client_ptr** Puntero al cliente PTP que se va a crear
* **packet_ptr** Puntero al paquete PTP que se transmitirá
* **timestamp_ptr** Puntero a la marca de tiempo del paquete PTP

### <a name="return-values"></a>Valores devueltos
Ninguno

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a>nx_ptp_client_soft_clock_callback

Implementación de software de un reloj PTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a>Descripción
Esta función de devolución de llamada sirve como un origen de reloj simulado de baja resolución para PTP. Esta rutina se proporciona como referencia y no se puede usar para producción.

### <a name="input-parameters"></a>Parámetros de entrada
* **client_ptr** Puntero al cliente PTP que se va a crear
* **operation** Operación de devolución de llamada, los valores válidos se definen como:
  * **NX_PTP_CLIENT_CLOCK_INIT** Inicializa el reloj.
  * **NX_PTP_CLIENT_CLOCK_SET** Establece la marca de tiempo actual especificada por `time_ptr`.
  * **NX_PTP_CLIENT_CLOCK_GET** Devuelve la marca de tiempo actual a `time_ptr`.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrae la marca de tiempo de `packet_ptr` en `time_ptr`.
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Ajusta la marca de tiempo actual menos de *1* segundo.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Marque el `packet_ptr` que necesita para notificar al cliente PTP la marca de tiempo cuando se transmita.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Actualiza el temporizador de software. El reloj de hardware puede pasarlo por alto.
* **time_ptr** Puntero a la marca de tiempo.
* **packet_ptr** Puntero al paquete.
* **callback_data** Puntero a los datos de devolución de llamada opacos.

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0x00) Operación correcta
* **NX_PTP_PARAM_ERROR** (0xD03) Parámetro no válido

### <a name="allowed-from"></a>Permitido desde
PTP interno

### <a name="example"></a>Ejemplo
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a>nx_ptp_client_start

Inicie el cliente PTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a>Descripción
Este servicio inicia una instancia de cliente PTP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada
* **client_ptr** Puntero al cliente PTP que se va a crear
* **client_port_identity_ptr** Puntero a la identidad y al puerto de cliente; puede ser NULL.
* **client_port_identity_length** Longitud del puerto y la identidad del cliente. Debe ser 0 si client_port_identity_ptr es NULL o NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)
* **domain** Dominio del reloj PTP
* **transport_specific** 4 bits de la dirección de transporte específico
* **event_callback** Función de devolución de llamada invocada en el evento
* **event_callback_data** Datos para la devolución de llamada del evento

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0x00) El cliente se inició correctamente
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) El cliente PTP ya se ha iniciado
* **status** Finalización del estado de las llamadas al servicio NetX Duo y ThreadX
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a>nx_ptp_client_stop

Detenga el cliente PTP.  Una vez detenido el cliente PTP, no procesará los paquetes PTP ni transmitirá los paquetes PTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción
Este servicio detiene una instancia de cliente PTP iniciada y creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada
* **client_ptr** Puntero al cliente PTP que se va a detener

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0x00) El cliente se detuvo correctamente
* **NX_PTP_CLIENT_NOT_STARTED** (0xD01) El cliente no se inició
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a>nx_ptp_client_sync_info_get

Obtenga la información de sincronización.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a>Descripción
Este servicio obtiene información del mensaje de sincronización. El bloque de control de sincronización se pasa a la aplicación de usuario a través de la función de devolución de llamada del evento.

### <a name="input-parameters"></a>Parámetros de entrada
* **client_ptr** Puntero al cliente PTP que se va a crear
* **flags** Marcas en el mensaje de sincronización
* **utc_offset** Desplazamiento entre TAI y UTC

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0X00) La información de sincronización se obtuvo correctamente
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a>nx_ptp_client_time_get

Obtenga la hora actual.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Descripción
Este servicio obtiene el valor actual del reloj PTP. Está disponible, independientemente de si el cliente PTP está sincronizado con el reloj principal o no.

### <a name="input-parameters"></a>Parámetros de entrada
* **client_ptr** Puntero al cliente PTP que se va a crear
* **time_ptr** Puntero a la hora PTP

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0x00) El cliente se creó correctamente
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a>nx_ptp_client_time_set

Establezca la hora actual.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Descripción
Este servicio establece el valor actual del reloj PTP. Se debe invocar antes de que se inicie el cliente PTP.

### <a name="input-parameters"></a>Parámetros de entrada
* **client_ptr** Puntero al cliente PTP que se va a crear
* **time_ptr** Puntero a la hora PTP

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0x00) El cliente se creó correctamente
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) El cliente PTP ya se ha iniciado
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a>nx_ptp_client_utility_convert_time_to_date

Convierta la hora PTP en una fecha y hora UTC.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a>Descripción
Este servicio convierte la hora PTP en una fecha y hora UTC.

### <a name="input-parameters"></a>Parámetros de entrada
* **time_ptr** Puntero a la hora PTP
* **offset** Desplazamiento en segundos con signo para agregar a la hora PTP
* **date_time_ptr** Puntero a la fecha resultante

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0x00) El cliente se creó correctamente
* **Puntero a la fecha resultante** (0xD03) Parámetro de entrada no válido
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a>nx_ptp_client_utility_time_diff

Diferencia entre dos horas PTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a>Descripción
Este servicio calcula la diferencia entre dos horas PTP.

### <a name="input-parameters"></a>Parámetros de entrada
* **time1_ptr** Puntero a la primera hora PTP
* **time2_ptr** Puntero a la segunda hora PTP
* **result_ptr** Puntero al resultado de la operación time1-time2

### <a name="return-values"></a>Valores devueltos
* **NX_SUCCESS** (0x00) El cliente se creó correctamente
* NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde
Subprocesos

### <a name="example"></a>Ejemplo
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```