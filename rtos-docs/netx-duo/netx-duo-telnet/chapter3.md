---
title: 'Capítulo 3: Descripción de los servicios de Telnet de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios de Telnet de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814529"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a>Capítulo 3: Descripción de los servicios de Telnet de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios de Telnet de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están deshabilitados por completo.

- **nx_telnet_client_connect**: *conecta un cliente Telnet con una dirección IPv4.*
- **nxd_telnet_client_connect**: *conecta un cliente Telnet IPv6 con una dirección IPv6.*
- **nx_telnet_client_create**: *crea un cliente Telnet.*
- **nx_telnet_client_delete**: *elimina un cliente Telnet.*
- **nx_telnet_client_disconnect**: *desconecta un cliente Telnet.*
- **nx_telnet_client_packet_receive**: *recibe un paquete mediante el cliente Telnet.*
- **nx_telnet_client_packet_send**: *envía un paquete mediante el cliente Telnet.*
- **nx_telnet_server_create**: *crea un servidor Telnet.*
- **nx_telnet_server_delete**: *elimina un servidor Telnet.*
- **nx_telnet_server_disconnect**: *desconecta un cliente Telnet.*
- **nx_telnet_server_get_open_connection_count**: *recupera el número de conexiones abiertas.*
- **nx_telnet_server_packet_send**: *envía un paquete a través de una conexión de cliente.*
- **nx_telnet_server_packet_pool_set**: *establece el grupo de paquetes como grupo de paquetes del servidor Telnet.*
- **nx_telnet_server_start**: *inicia un servidor Telnet*
- **nx_telnet_server_stop**: *detiene un servidor Telnet*

## <a name="nx_telnet_client_connect"></a>nx_telnet_client_connect

Conecta un cliente Telnet con una dirección IPv4.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta conectar la instancia de cliente Telnet creada anteriormente con el servidor de la dirección IP y el puerto especificados mediante una dirección IPv4 para el servidor Telnet. En realidad, este servicio inserta la dirección IP del servidor ULONG en un bloque de control NXD_ADDRESS y establece la versión de IP en 4 antes de llamar al servicio *nxd_telnet_client_connect* que se describe a continuación.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente Telnet.
- **server_ip**: dirección IPv4 del servidor Telnet.
- **server_port**: puerto TCP del servidor (el servidor Telnet es el puerto 23).
- **wait_option**: define cuánto tiempo va a esperar el servicio para la conexión del cliente Telnet. Las opciones de espera se definen de la siguiente forma:

    - **timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) conexión correcta del cliente.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) el cliente ya está conectado.
- NX_PTR_ERROR: (0x07) el puntero de cliente no es válido.
- NX_IP_ADDRESS_ERROR (0x21): la dirección IP no es válida.
- NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a>nxd_telnet_client_connect

Conecta un cliente Telnet con una dirección IPv4 o IPv6.

### <a name="prototype"></a>Prototipo

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta conectar la instancia de cliente Telnet creada anteriormente al servidor de la dirección IP y el puerto especificados mediante una dirección IPv6 del servidor Telnet. Este servicio puede tomar una dirección IPv4 o IPv6, pero debe incluirse en la variable *server_ip_address* de NXD_ADDRESS.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente Telnet.
- **server_ip_address**: dirección IP del servidor.
- **server_port**: puerto TCP del servidor (el servidor Telnet es el puerto 23).
- **wait_option**: define cuánto tiempo va a esperar el servicio para la conexión del cliente Telnet. Las opciones de espera se definen de la siguiente forma:

    - **timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) conexión correcta del cliente.
- **NX_TELNET_ERROR**: (0xF0) error de conexión del cliente.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) el cliente ya está conectado.
- NX_PTR_ERROR: (0x07) el puntero de cliente no es válido.
- NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.
- NX_TELNET_INVALID_PARAMETER: (0xF5) entrada que no es de puntero no válida

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a>nx_telnet_client_create

Crear un cliente Telnet

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia del cliente Telnet.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente Telnet.
- **client_name**: nombre de la instancia del cliente.
- **ip_ptr**: puntero a la instancia de IP.
- **window_size**: tamaño de la ventana de recepción TCP para este cliente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) creación correcta del cliente.
- **NX_TELNET_ERROR**: (0xF0) error de creación del socket.
- NX_PTR_ERROR: (0x07) el puntero de IP o el cliente no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a>nx_telnet_client_delete

Elimina un cliente Telnet.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente Telnet creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente Telnet.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) eliminación correcta del cliente.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) el cliente aún está conectado.
- NX_PTR_ERROR: (0x07) el puntero de cliente no es válido.
- NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a>nx_telnet_client_disconnect

Desconecta un cliente Telnet.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio desconecta una instancia de cliente Telnet conectada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente Telnet.
- **wait_option**: define cuánto tiempo va a esperar el servicio la desconexión del cliente Telnet. Las opciones de espera se definen de la siguiente forma:

    - **timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) desconexión correcta del cliente.
- **NX_TELNET_NOT_CONNECTED**: (0xF3) el cliente no está conectado.
- NX_PTR_ERROR: (0x07) el puntero de cliente no es válido.
- NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.


### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a>nx_telnet_client_packet_receive

Recibe un paquete mediante el cliente Telnet.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio recibe un paquete de la instancia de cliente Telnet conectada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente Telnet.
- **packet_ptr**: puntero al destino del paquete recibido.
- **wait_option**: define cuánto tiempo va a esperar el servicio para recibir un paquete del cliente Telnet. Las opciones de espera se definen de la siguiente forma:
    - **timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) recepción correcta de paquetes del cliente.
- NX_PTR_ERROR: (0x07) la entrada del puntero no es válida.
- NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a>nx_telnet_client_packet_send

Envía un paquete mediante el cliente Telnet.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía un paquete mediante la instancia de cliente Telnet conectada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: puntero al bloque de control del cliente Telnet.
- **packet_ptr**: puntero al paquete que se va a enviar.
- **wait_option**: define cuánto tiempo va a esperar el servicio para enviar un paquete del cliente Telnet. Las opciones de espera se definen de la siguiente forma:
    - **timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) envío correcto de paquetes.
- **NX_TELNET_ERROR**: (0xF0) error de envío de paquete; el autor de la llamada es responsable de liberar el paquete.
- NX_PTR_ERROR: (0x07) la entrada del puntero no es válida.
- NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a>nx_telnet_server_create

Crea un servidor Telnet.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a>Descripción

Este servicio crea una instancia de un servidor Telnet en la instancia de IP especificada.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al bloque de control del servidor Telnet.
- **server_name**: nombre de la instancia del servidor Telnet.
- **ip_ptr**: puntero a la instancia de IP asociada.
- **stack_ptr**: puntero a la pila del subproceso del servidor interno.
- **stack_size**: tamaño de la pila, en bytes.
- **new_connection**: puntero de función de rutina de la devolución de llamada de la aplicación. Se llama a esta rutina siempre que el servidor detecta una nueva solicitud de conexión del cliente Telnet.
- **receive_data**: puntero de función de rutina de la devolución de llamada de la aplicación. Se llama a esta rutina siempre que haya nuevos datos del cliente Telnet en la conexión. Esta rutina es responsable de liberar el paquete.
- **end_connection**: puntero de función de rutina de la devolución de llamada de la aplicación. Se llama a esta rutina cuando el cliente desconecta una conexión de cliente Telnet o se agota el tiempo de espera de la conexión de cliente ("tiempo de espera de la actividad"). El servidor también se puede desconectar mediante el servicio *nx_telnet_server_disconnect* que se describe a continuación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el servidor se creó correctamente.
- NX_PTR_ERROR: (0x07) el servidor, la dirección IP, la pila o los punteros de devolución de llamada de aplicación no son válidos.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a>nx_telnet_server_delete

Elimina un servidor Telnet.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de servidor Telnet creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al bloque de control del servidor Telnet.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el servidor se eliminó correctamente.
- NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.
- NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a>nx_telnet_server_disconnect

Desconecta un cliente Telnet.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a>Descripción

Este servicio desconecta un cliente conectado previamente en esta instancia del servidor Telnet. Normalmente, se llama a esta rutina desde la función de devolución de llamada de recepción de datos de la aplicación en respuesta a una condición detectada en los datos recibidos.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al bloque de control del servidor Telnet.
- **logical_connection**: conexión lógica correspondiente a la conexión de cliente en este servidor. El intervalo de valores válidos es de 0 a NX_TELENET_MAX_CLIENTS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el servidor se desconectó correctamente.
- **NX_TELNET_ERROR**: (0xF0) error al desconectar el servidor.
- NX_OPTION_ERROR: (0x0A) la conexión lógica no es válida.
- NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.
- NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a>nx_telnet_server_get_open_connection_count

Devuelve el número de conexiones abiertas actualmente.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a>Descripción

Este servicio devuelve el número de clientes de Telnet conectados actualmente.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al bloque de control del servidor Telnet.
- **Connection_count**: puntero a la memoria para almacenar el número de conexiones

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) la operación finalizó correctamente.
- NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.
- NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a>nx_telnet_server_packet_send

Envía un paquete a través de la conexión de cliente.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía un paquete a la conexión de cliente en esta instancia del servidor Telnet. Normalmente, se llama a esta rutina desde la función de devolución de llamada de recepción de datos de la aplicación en respuesta a una condición detectada en los datos recibidos.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al bloque de control del servidor Telnet.
- **logical_connection**: conexión lógica correspondiente a la conexión de cliente en este servidor. El intervalo de valores válidos es de 0 a NX_TELENET_MAX_CLIENTS.
- **packet_ptr**: puntero al paquete recibido.
- **wait_option**: define cuánto tiempo va a esperar el servicio para enviar un paquete del servidor Telnet. Las opciones de espera se definen de la siguiente forma:
    - **timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud. 

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el paquete se envió correctamente.
- **NX_TELNET_FAILED**: (0xF2) error al enviar el socket TCP.
- NX_OPTION_ERROR: (0x0A) la conexión lógica no es válida.
- NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.
- NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a>nx_telnet_server_packet_pool_set

Establece el grupo de paquetes creado anteriormente como grupo de servidores Telnet

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a>Descripción

Este servicio establece un grupo de paquetes creado anteriormente como el grupo de paquetes del servidor Telnet si se define NX_TELNET_SERVER_USER_CREATE_PACKET_POOL. También requiere que NX_TELNET_SERVER_OPTION_DISABLE no se defina de modo que el servidor Telnet necesite un grupo de paquetes para transmitir opciones de Telnet a los clientes Telnet.

Esto permite que las aplicaciones creen el grupo de paquetes en una memoria distinta (por ejemplo, sin memoria caché) a la pila del servidor Telnet. Tenga en cuenta que esta función no comprueba si el grupo de paquetes del servidor Telnet ya está establecido. Si se llama en un puntero del grupo de paquetes del servidor Telnet que no tenga un valor null, lo sobrescribirá y reemplazará el grupo de paquetes existente al que señala el puntero de entrada.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al bloque de control del servidor Telnet
- **packet_pool_ptr**: puntero al grupo de paquetes creado previamente

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) el grupo se estableció correctamente.
- NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a>nx_telnet_server_start

Inicia un servidor Telnet.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a>Descripción

Este servicio inicia una instancia de servidor Telnet creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al bloque de control del servidor Telnet.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) iniciado correctamente.
- **NX_TELNET_NO_PACKET_POOL**: (0XF6) no hay ningún grupo de paquetes establecido.
- NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a>nx_telnet_server_stop

Detiene un servidor Telnet.

### <a name="prototype"></a>Prototipo

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene una instancia de servidor Telnet iniciada y creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr**: puntero al bloque de control del servidor Telnet.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) se detuvo correctamente.
- NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.
- NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```