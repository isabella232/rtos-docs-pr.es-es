---
title: 'Capítulo 3: Descripción de los servicios del cliente SNTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del cliente SNTP de NetX Duo incluidos a continuación por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814550"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a>Capítulo 3: Descripción de los servicios del cliente SNTP de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios del cliente SNTP de Azure RTOS NetX Duo incluidos a continuación por orden alfabético.

En la sección “Valores devueltos” de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición de **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_sntp_client_create**: *crea el cliente SNTP.*
- **nx_sntp_client_delete**: *elimina el cliente SNTP.*
- **nx_sntp_client_get_local_time**: *obtiene la hora local del cliente SNTP.*
- **nx_sntp_client_get_local_time_extended**: *obtiene la hora local del cliente SNTP.*
- **nx_sntp_client_initialize_broadcast**: *inicializa el cliente para la operación de difusión en IPv4.*
- **nxd_sntp_client_initialize_broadcast**: *inicializa el cliente para la operación de difusión en IPv6 o IPv4.*
- **nx_sntp_client_initialize_unicast**: *inicializa el cliente para la operación de unidifusión en IPv4.*
- **nxd_sntp_client_initialize_unicast**: *inicializa el cliente para la operación de unidifusión en IPv4 o IPv6.*
- **nx_sntp_client_receiving_udpates**: *el cliente está recibiendo actualmente actualizaciones válidas de SNTP.*
- **nx_sntp_client_request_unicast_time**: *envía una solicitud de unidifusión directamente al servidor NTP.*
- **nx_sntp_client_run_broadcast**: *ejecuta el cliente en modo de difusión.*
- **nx_sntp_client_run_unicast**: *ejecuta el cliente en modo de unidifusión.*
- **nx_sntp_client_set_local_time**: *establece la hora local inicial del cliente SNTP.*
- **nx_sntp_client_set_time_update_notify**: *establece la devolución de llamada de actualización de SNTP.*
- **nx_sntp_client_stop**: *detiene el subproceso del cliente SNTP.*
- **nx_sntp_client_utility_display_date_and_time**: *muestra la hora de NTP en segundos.*
- **nx_sntp_client_utility_msecs_to_fraction**: *convierte milisegundos a un componente de fracción de NTP.*
- **nx_sntp_client_utility_usecs_to_fraction**: *convierte microsegundos a un componente de fracción de NTP.*
- **nx_sntp_client_utility_fraction_to_usecs**: *convierte un componente de fracción de NTP a microsegundos.*


## <a name="nx_sntp_client_create"></a>nx_sntp_client_create

Crea un cliente SNTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a>Descripción

Este servicio crea una instancia del cliente SNTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **ip_ptr**: puntero a la instancia de IP del cliente.

- **iface_index**: índice de la interfaz de red de SNTP.

- **packet_pool_ptr**: puntero al grupo de paquetes del cliente.

- **leap_second_handler**: devolución de llamada para la respuesta de la aplicación al segundo intercalar inminente.

- **kiss_of_death_handler**: devolución de llamada para la respuesta de la aplicación a la recepción de un paquete de beso de la muerte.

- **random_number_generator**: devolución de llamada al servicio generador de números aleatorios.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) creación correcta del cliente.

- **NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD**: (0xD2A) entrada que no es de puntero no válida.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a>nx_sntp_client_delete

Elimina un cliente SNTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia del cliente SNTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) creación correcta del cliente.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a>nx_sntp_client_get_local_time

Obtiene la hora local del cliente SNTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a>Descripción

Este servicio obtiene la hora local del cliente SNTP con una entrada de puntero al búfer opcional para recibir los datos en formato de mensaje de cadena.

Este servicio está en desuso. Se recomienda a los desarrolladores que migren a *nx_sntp_client_get_local_time_extended*().

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **seconds**: puntero a los segundos de la hora local.

- **fraction**: componente de fracción de la hora local.

- **buffer**: puntero al búfer para escribir datos de hora.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) creación correcta del cliente.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a>nx_sntp_client_get_local_time_extended

Obtiene la hora local extendida del cliente SNTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a>Descripción

Este servicio obtiene la hora local extendida del cliente SNTP con una entrada de puntero al búfer opcional para recibir los datos en formato de mensaje de cadena.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **seconds**: puntero a los segundos de la hora local.

- **fraction**: puntero al componente de fracción.

- **buffer**: puntero al búfer para escribir datos de hora.

- **buffer_size**: longitud del búfer.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) creación correcta del cliente.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.

- NX_SIZE_ERROR: (0x09) error de comprobación de buffer_size.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a>nx_sntp_client_initialize_broadcast

Inicializa el cliente para la operación de difusión.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a>Descripción

Este servicio inicializa el cliente para la operación de difusión estableciendo la dirección IP del servidor SNTP e inicializando los parámetros de inicio y los tiempos de espera de SNTP. Si ni la dirección de multidifusión ni la de difusión son NULL, se selecciona la dirección de multidifusión. Si ambas direcciones son NULL, se devuelve un error. Tenga en cuenta que solo es compatible con las direcciones de servidor IPv4.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **multicast_server_address**: dirección de multidifusión de SNTP.

- **broadcast_time_server**: dirección de difusión del servidor SNTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) creación correcta del cliente.

- **NX_INVALID_PARAMETERS**: (0x4D) entrada que no es de puntero no válida:

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a>nxd_sntp_client_initialize_broadcast

Inicializa el cliente para la operación de difusión en IPv4 o IPv6.

### <a name="prototype"></a>Prototipo

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a>Descripción

Este servicio inicializa el cliente para la operación de difusión configurando la dirección IP del servidor SNTP e inicializando los parámetros de inicio y los tiempos de espera de SNTP. Si ni el puntero a la dirección de multidifusión ni a la de difusión son NULL, se selecciona la dirección de multidifusión. Si ambos punteros de dirección son NULL, se devuelve un error. Es compatible con los tipos de dirección IPv4 e IPv6. Tenga en cuenta que IPv6 no admite la difusión, por lo que si el puntero de dirección de difusión se establece en IPv6, se devuelve un error.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **multicast_server_address**: dirección de multidifusión del servidor SNTP.

- **broadcast_server_address**: dirección de difusión del servidor SNTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) cliente inicializado correctamente.

- NX_SNTP_PARAM_ERROR: (0xD0D) entrada que no es de puntero no válida.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.


### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a>nx_sntp_client_initialize_unicast

Configura el cliente SNTP para que se ejecute en unidifusión.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a>Descripción

Este servicio inicializa el cliente para la operación de unidifusión estableciendo la dirección IP del servidor SNTP e inicializando los parámetros de inicio y los tiempos de espera de SNTP. Tenga en cuenta que solo es compatible con las direcciones de servidor IPv4.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **unicast_time_server**: dirección IP del servidor SNTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) cliente inicializado correctamente.

- NX_INVALID_PARAMETERS: (0x4D) entrada que no es de puntero no válida.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a>nxd_sntp_client_initialize_unicast

Configura el cliente SNTP para que se ejecute en unidifusión en IPv4 o IPv6.

### <a name="prototype"></a>Prototipo

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a>Descripción

Este servicio inicializa el cliente para la operación de unidifusión configurando la dirección IP del servidor SNTP e inicializando los parámetros de inicio y los tiempos de espera de SNTP. Es compatible con los tipos de dirección IPv4 e IPv6.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **unicast_time_server**: dirección IP del servidor SNTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) cliente inicializado correctamente.

- NX_INVALID_PARAMETERS: (0x4D) entrada que no es de puntero no válida.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a>nx_sntp_client_receiving_updates

Indica si el cliente está recibiendo actualizaciones válidas.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a>Descripción

Este servicio indica si el cliente está recibiendo actualizaciones SNTP válidas. Si se supera el intervalo máximo de tiempo sin una actualización o se supera el límite de actualizaciones no válidas consecutivas, el estado de recepción se devuelve como false. Tenga en cuenta que el cliente SNTP se sigue ejecutando y, si la aplicación desea reiniciarlo con otro servidor de unidifusión o de difusión/multidifusión, debe detenerlo mediante el servicio *nx_sntp_client_stop* y después reinicializarlo mediante uno de los servicios de inicialización con otro servidor.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **receive_status**: puntero al indicador que señala si el cliente está recibiendo actualizaciones válidas.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el cliente ha recibido correctamente el estado de actualización.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a>nx_sntp_client_request_unicast_time

Envía una solicitud de unidifusión directamente al servidor NTP.


### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a>Descripción

Este servicio permite que la aplicación envíe directamente una solicitud de unidifusión al servidor NTP de forma asincrónica desde la tarea de subproceso del cliente SNTP. La opción de espera especifica cuánto tiempo se debe esperar por una respuesta. Si finaliza correctamente, la aplicación puede usar otros servicios del cliente SNTP para obtener la hora más reciente. Consulte la sección **Solicitudes asincrónicas de unidifusión de SNTP** para obtener más detalles.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **Wait_option**: opción de espera por la respuesta de NTP en tics de temporizador.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el cliente envía y recibe correctamente la actualización de unidifusión.

- **NX_SNTP_CLIENT_NOT_STARTED**: (0xD0B) no se ha iniciado el subproceso del cliente.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a>nx_sntp_client_run_broadcast

Ejecuta el cliente en modo de difusión.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia el cliente en modo de difusión, en el que esperará para recibir las difusiones del servidor SNTP. Si se recibe un mensaje SNTP de difusión válido, se restablecen el tiempo de espera del cliente SNTP del intervalo máximo sin actualizaciones y el número de mensajes no válidos consecutivos recibidos. Si se supera cualquiera de estos límites, el cliente SNTP establece el estado del servidor en no válido, aunque seguirá esperando recibir actualizaciones. La aplicación puede sondear la tarea de cliente SNTP para comprobar el estado del servidor y, si no es válido, detener el cliente SNTP y reinicializarlo con otra dirección de difusión SNTP. También puede cambiar a un servidor SNTP de unidifusión.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

### <a name="return-values"></a>Valores devueltos

- **status**: -------- estado de finalización real.

- **NX_SNTP_CLIENT_ALREADY_STARTED**: (0xD0C) el cliente ya se ha iniciado.

- **NX_SNTP_CLIENT_NOT_INITIALIZED**: (0xD01) el cliente no se ha inicializado.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a>nx_sntp_client_run_unicast

Ejecuta el cliente en modo de unidifusión.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia el cliente en modo de unidifusión, desde el que envía periódicamente una solicitud de unidifusión a su servidor SNTP para una actualización de hora. Si se recibe un mensaje SNTP válido, se restablecen el tiempo de espera del cliente SNTP del intervalo máximo sin actualizaciones, el intervalo inicial de sondeo y el número de mensajes no válidos consecutivos recibidos. Si se supera cualquiera de estos límites, el cliente SNTP establece el estado del servidor en no válido, aunque seguirá sondeando y esperando recibir actualizaciones. La aplicación puede sondear la tarea de cliente SNTP para comprobar el estado del servidor y, si no es válido, detener el cliente SNTP y reinicializarlo con otra dirección de unidifusión SNTP. También puede cambiar a un servidor SNTP de difusión.

.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el cliente se ha iniciado correctamente en modo de unidifusión.

- **NX_SNTP_CLIENT_ALREADY_STARTED**: (0xD0C) el cliente ya se ha iniciado.

- **NX_SNTP_CLIENT_NOT_INITIALIZED**: (0xD01) el cliente no se ha inicializado.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

- NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.


### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a>nx_sntp_client_set_local_time

Establece la hora local del cliente SNTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a>Descripción

Este servicio establece la hora local del cliente SNTP a partir de la hora de entrada, en formato SNTP; es decir, con segundos y una fracción, que es la forma de incluir fracciones de segundo en formato hexadecimal. Está diseñado para actualizar la hora local del cliente SNTP a partir de un cronometrador independiente; por ejemplo, un reloj en tiempo real. El protocolo SNTP está diseñado de modo que las actualizaciones de hora de SNTP impidan el desfase de la hora del reloj local. Las actualizaciones de hora del servidor SNTP pueden ser, aunque no está previsto que lo sean, la única entrada para la hora local del cliente SNTP si no hay ningún cronometrador independiente en el dispositivo de la aplicación.

Esta API también se puede usar para proporcionar al cliente SNTP una hora base antes de iniciar el subproceso del cliente SNTP. La hora local del cliente SNTP se compara con las actualizaciones recibidas para obtener datos de hora válidos. La primera vez que se recibe una actualización puede haber una discrepancia muy grande. Por lo tanto, existe una opción para que el cliente SNTP pase por alto la discrepancia de la primera actualización. Así, el cliente SNTP puede iniciarse sin una hora base. La hora de entrada puede obtenerse a partir de horas de época conocidas (normalmente disponibles en Internet) y se calcula como el número de segundos transcurridos desde el 1 de enero de 1900 (hasta 2036, año en que empezará una nueva "época").

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **seconds**: componente de segundos de la entrada de hora.

- **fraction**: componente de subsegundos en el formato de fracción de SNTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) hora local establecida correctamente.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización

### <a name="example"></a>Ejemplo

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a>nx_sntp_client_set_time_update_notify

Establece la devolución de llamada de la actualización de SNTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a>Descripción

Este servicio establece una devolución de llamada para notificar a la aplicación cuando el cliente SNTP reciba una actualización de hora válida. Proporciona la hora local del mensaje SNTP y del cliente SNTP (normalmente la misma) en formato NTP. La aplicación puede usar los datos NTP directamente o llamar al *servicio nx_sntp_client_utility_display_date_time* para convertir la hora a un formato en lenguaje natural.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

- **time_update_cb**: puntero a la función de devolución de llamada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) devolución de llamada establecida correctamente.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización

### <a name="example"></a>Ejemplo

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a>nx_sntp_client_stop

Detiene el subproceso del cliente SNTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene el subproceso del cliente SNTP. Las tareas de subproceso del cliente SNTP, que se ejecutan en un bucle infinito, se pausan en cada iteración para liberar el control del estado del cliente SNTP y permitir que las aplicaciones realicen llamadas API al cliente SNTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente SNTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) subproceso de cliente correctamente detenido.

- **NX_SNTP_CLIENT_NOT_STARTED**: (0xDB) no se ha iniciado el subproceso del cliente SNTP.

- NX_PTR_ERROR: (0x07) entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a>nx_sntp_client_utility_display_date_time

Convierte una hora NTP en una cadena de fecha y hora.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a>Descripción

Este servicio convierte la hora local del cliente SNTP al formato de año, mes y día, y devuelve la fecha en el búfer proporcionado. No es necesario que el valor de NX_SNTP_CURRENT_YEAR sea el mismo año que el de la hora actual del cliente, pero debe definirse.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al cliente SNTP.

- **buffer**: puntero al búfer para almacenar la fecha.

- **length**: tamaño del búfer de entrada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) conversión correcta.

- **NX_SNTP_ERROR_CONVERTING_DATETIME**: (0xD08) no se ha definido NX_SNTP_CURRENT_YEAR o no se ha establecido la hora del cliente local.

- **NX_SNTP_INVALID_DATETIME_BUFFER**: (0xD07) tamaño de búfer insuficiente.


### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a>nx_sntp_client_utility_msecs_to_fraction

Convierte milisegundos a un componente de fracción de NTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a>Descripción

Este servicio convierte los milisegundos de la entrada al componente de fracción de NTP. Está diseñado para usarse con aplicaciones que tienen una hora base de inicio para el cliente SNTP pero no en formato de segundos/fracción de NTP. El número de milisegundos debe ser inferior a 1000 para crear una fracción válida.

### <a name="input-parameters"></a>Parámetros de entrada

- **milliseconds**: milisegundos que se van a convertir.

- **fraction**: puntero a los milisegundos convertidos a fracción.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) conversión correcta.

- **NX_SNTP_OVERFLOW_ERROR**: (0xD32) error al convertir la hora a una fecha.

- NX_SNTP_INVALID_TIME: (0xD30) entrada de datos de SNTP no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a>nx_sntp_client_utility_usecs_to_fraction

Convierte microsegundos a un componente de fracción de NTP.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a>Descripción

Este servicio convierte los microsegundos de la entrada al componente de fracción de NTP. Está diseñado para usarse con aplicaciones que tienen una hora base de inicio para el cliente SNTP pero no en formato de segundos/fracción de NTP. El número de microsegundos debe ser inferior a 1 000 000 para crear una fracción válida.

### <a name="input-parameters"></a>Parámetros de entrada

- **microseconds**: microsegundos que se van a convertir.

- **fraction**: puntero a los microsegundos convertidos a fracción.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) conversión correcta.

- **NX_SNTP_OVERFLOW_ERROR**: (0xD32) error al convertir la hora a una fecha.

- NX_SNTP_INVALID_TIME: (0xD30) entrada de datos de SNTP no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a>nx_sntp_client_utility_fraction_to_usecs

Convierte un componente de fracción de NTP a microsegundos.

### <a name="prototype"></a>Prototipo

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a>Descripción

Este servicio convierte el componente de fracción de NTP de la entrada a microsegundos.

### <a name="input-parameters"></a>Parámetros de entrada

- **fraction**: fracción que se va a convertir.

- **microseconds**: puntero a la fracción convertida en microsegundos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) conversión correcta.

- NX_SNTP_INVALID_TIME: (0xD30) entrada de datos de SNTP no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```