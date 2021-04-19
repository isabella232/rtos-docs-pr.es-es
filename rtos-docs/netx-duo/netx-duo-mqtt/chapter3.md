---
title: 'Capítulo 3: Descripción de los servicios del cliente MQTT de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del cliente MQTT de NetX Duo (se enumeran a continuación) por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814650"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a>Capítulo 3: Descripción de los servicios del cliente MQTT de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios del cliente MQTT de Azure RTOS NetX Duo (se enumeran a continuación) por orden alfabético.

En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nxd_mqtt_client_create** *Crear la instancia de cliente MQTT*
- **nxd_mqtt_client_will_message_set** *Establecer el mensaje Will*
- **nxd_mqtt_client_client_login_set** *Establecer el nombre de usuario y contraseña de inicio de sesión del cliente MQTT*
- **nxd_mqtt_client_connect** *Conectar el cliente MQTT al agente*
- **nxd_mqtt_client_secure_connect** *Conectar el cliente MQTT al agente con seguridad TLS*
- **nxd_mqtt_client_publish** *Publicar un mensaje a través del agente.*
- **nxd_mqtt_client_subscribe** *Suscribirse a un tema*
- **nxd_mqtt_client_unsubscribe** *Cancelar la suscripción a un tema*
- **nxd_mqtt_client_receive_notify_set** *Establecer la función de devolución de llamada de la notificación que indica la recepción de un mensaje de MQTT*
- **nxd_mqtt_client_message_get** *Recuperar un mensaje del agente*
- **nxd_mqtt_client_disconnect_notify_set** *Establecer la función de devolución de llamada de la notificación que indica la desconexión de MQTT*
- **nxd_mqtt_client_disconnect** *Desconectar el cliente MQTT del agente*
- **nxd_mqtt_client_delete** *Eliminar la instancia de cliente MQTT*

## <a name="nxd_mqtt_client_create"></a>nxd_mqtt_client_create

Crear instancia de cliente MQTT

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente MQTT en la instancia de IP especificada. La cadena *client_id* se pasa al servidor durante la fase de conexión de MQTT como *Identificador de cliente (ClientId)* . También crea los recursos ThreadX necesarios (subproceso de la tarea cliente MQTT, exclusión mutua, grupo de marcas de evento y socket TCP).

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **client_name** Cadena de nombre de cliente.
- **client_id** Cadena de identificador de cliente que se usa durante la fase de conexión. El agente MQTT usa este client_id para identificar de forma única a un cliente.
- **client_id_length** Longitud de la cadena de identificador de cliente, en bytes.
- **ip_ptr** Puntero a la instancia de IP.
- **pool_ptr** Puntero al grupo de paquetes que el cliente MQTT usa para su funcionamiento.
- **stack_ptr** Área de pila para el subproceso del cliente MQTT.
- **stack_size** Tamaño del área de la pila, en bytes.
- **mqtt_thread_priority** Prioridad del subproceso MQTT.
- **memory_ptr** En desuso. Ya no se usa.
- **memory_size** En desuso. Ya no se usa.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) El cliente MQTT se creó correctamente.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna
- NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Cadena de tema Will, will_retrain_flag o will_QoS no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a>nxd_mqtt_client_will_message_set

Establece el mensaje Will.

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a>Descripción

Este servicio establece el tema Will opcional y el mensaje Will antes de que el cliente se conecte al servidor. El tema Will debe ser una cadena con codificación UTF-8.

Si se establece, el mensaje Will se transmite al agente como parte del mensaje CONNECT. Por lo tanto, las aplicaciones que quieran usar el mensaje Will deben usar este servicio antes de que se realice la conexión MQTT.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **will_topic** Cadena de tema Will con codificación UTF-8. El tema Will debe estar presente. El autor de la llamada debe hacer que la cadena will_topic siga siendo válida hasta que se realice la llamada a *nx_mqtt_client_connect*.
- **will_topic_length** Número de bytes en la cadena de tema Will.
- **will_message** Mensaje Will definido por la aplicación. Si no se requiere el mensaje Will, la aplicación puede establecer este campo en *NX_NULL*.
- **will_message_length** Número de bytes en la cadena de mensaje Will. Si will_message se establece en NULL, will_message_length debe establecerse en 0.
- **will_retain_flag** Define si el servidor publicará el mensaje Will como un mensaje retenido. Los valores válidos son *NX_TRUE* o *NX_FALSE*.
- **will_QoS** Valor de QoS que usa el servidor cuando se envía el mensaje Will. Los valores válidos son 0 ó 1.  

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) (0x00) El mensaje Will se configuró correctamente.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) No se admiten los mensajes de QoS nivel 2.
- NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Cadena de tema Will, will_retrain_flag o will_QoS no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a>nxd_mqtt_client_login_set

Establece el nombre de usuario y contraseña de inicio de sesión del cliente MQTT

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a>Descripción

Este servicio establece el nombre de usuario y la contraseña, que se usan durante la fase de conexión de MQTT para el inicio de sesión en la autenticación.

Iniciar sesión en el cliente MQTT con el nombre de usuario y la contraseña es opcional. En situaciones en las que el servidor requiere un nombre de usuario y una contraseña, ambos valores se deben establecer antes de establecer la conexión.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **username** Cadena de nombre de usuario con codificación UTF-8. El autor de la llamada debe hacer que la cadena username siga siendo válida hasta que se realice la llamada a *nx_mqtt_client_connect*.
- **username_length** Número de bytes en la cadena de nombre de usuario.
- **password** Cadena de contraseña. Si no se requiere una contraseña, este campo se puede establecer en NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) (0x00) El mensaje Will se configuró correctamente.
- NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Cadena de nombre de usuario o contraseña no válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a>nxd_mqtt_client_connect

Conecta el cliente MQTT al agente

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Descripción

Este servicio inicia una conexión al agente. En primer lugar, se enlaza a un socket TCP y, a continuación, realiza una conexión TCP. Suponiendo que se realiza correctamente, crea un temporizador si está habilitada la característica Mantener conexión de MQTT. A continuación, se conecta con el servidor MQTT (agente).

Tenga en cuenta que este servicio crea una conexión MQTT sin protección TLS. Para crear una conexión MQTT segura, la aplicación debe usar el servicio ***nxd_mqtt_client_secure_connect().***

Una vez establecida la conexión, si el cliente establece *clean_session* en NX_FALSE, el cliente volverá a transmitir los mensajes almacenados que todavía no se hayan confirmado.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **server_IP** Dirección IP del agente.
- **server_port** Número de puerto del agente. El puerto predeterminado para MQTT está definido como **_NXD_MQTT_PORT_** (1883).
- **keep_alive** Valor de Mantener conexión, en segundos, que se va a usar durante la sesión. El valor indica el tiempo máximo entre dos mensajes de control de MQTT que se envían al agente antes de que este agote el tiempo de espera del cliente. El valor 0 desactiva la característica keep-alive.
- **clean_session** Si el servidor debe iniciar la limpieza de esta sesión. Las opciones válidas son **_NX_TRUE_ *_ o _* _NX_FALSE._**
- **wait_option** Tiempo de espera de la conexión.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) Conexión a MQTT correcta.
- **NXD_MQTT_ALREADY_CONNECTED** (0X10001) El cliente ya está conectado al agente.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT. 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.
- **NXD_MQTT_CONNECT_FAILURE** (0X10005) No se pudo conectar al agente.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No pueden enviar mensajes al agente.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) El servidor respondió con un error.
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Código de respuesta del servidor.
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Código de respuesta del servidor.
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Código de respuesta del servidor.
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Código de respuesta del servidor.
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Código de respuesta del servidor.
- NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a>nxd_mqtt_client_secure_connect

Conecta el cliente MQTT al agente con seguridad TLS

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Descripción

Este servicio es idéntico a ***nxd_mqtt_client_connect***, salvo que la conexión pasa a través de la capa TLS en lugar de TCP. Por lo tanto, se protege la comunicación entre el cliente y el agente.

El elemento *tls_setup* definido por el usuario es una función de devolución de llamada que usa el cliente MQTT antes de realizar una conexión de cliente MQTT. La aplicación inicializará NetX Secure TLS, configurará los parámetros de seguridad y cargará los certificados pertinentes que se usarán durante el protocolo de enlace TLS. El protocolo de enlace TLS real se produce después de establecer una conexión TCP en el puerto TLS MQTT del agente (puerto TCP predeterminado 8883). Una vez que el protocolo de enlace de TLS se ha realizado correctamente, el paquete de control CONNECT de MQTT se envía a través de TLS.

Para establecer conexiones seguras, la biblioteca de NetX Secure TLS debe estar disponible y el cliente MQTT de NetX Duo debe compilarse con el valor ***NX_SECURE_ENABLE*** definido.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **server_IP** Dirección IP del agente.
- **server_port** Número de puerto del agente. El puerto predeterminado para MQTT está definido como **_NXD_MQTT_TLS_PORT_** (8883).
- **tls_setup** Función de devolución de llamada de configuración de TLS proporcionada por el usuario. Esta función de devolución de llamada se invoca para establecer los parámetros de conexión del cliente TLS.
- **keep_alive** Valor de Mantener conexión que se va a usar durante la sesión. El valor 0 desactiva la característica keep-alive.
- **clean_session** Si el servidor debe o no iniciar la limpieza de esta sesión. Las opciones válidas son **_NX_TRUE_ *_ o _* _NX_FALSE._**
- **wait_option** Tiempo de espera de la conexión.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) Se estableció correctamente una conexión de cliente MQTT a través de TLS.
- **NXD_MQTT_ALREADY_CONNECTED** (0X10001) El cliente ya está conectado al agente.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT. 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.
- **NXD_MQTT_CONNECT_FAILURE** (0X10005) No se pudo conectar al agente.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No pueden enviar mensajes al agente.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) El servidor respondió con un mensaje de error.
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Código de respuesta del servidor.
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Código de respuesta del servidor.
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Código de respuesta del servidor.
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Código de respuesta del servidor.
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Código de respuesta del servidor.
- NX_PTR_ERROR (0x07) Bloque de control o estructura de dirección de servidor MQTT no válidos.
- NX_INVALID_PORT (0x46) El puerto del servidor no puede ser 0.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Error de entrada del parámetro.
- NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) El subproceso MQTT aún no ha comenzado a ejecutarse.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a>nxd_mqtt_client_publish

Publica un mensaje a través del agente

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a>Descripción

Este servicio publica un mensaje a través del agente. Todavía no se admite la publicación de mensajes de QoS de nivel 2.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **topic_name** Tema en el que se va a publicar.
- **topic_name_length** Longitud del tema, en bytes.
- **message** Puntero al búfer de mensajes.
- **message_length** Tamaño del mensaje, en bytes
- **retain** Determina si el agente debe conservar el mensaje.
- **QoS** Valor de QoS deseado: 0 ó 1.
- **timeout** Valor de tiempo de espera.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) Creación de cliente MQTT correcta.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.
- **NXD_MQTT_PACKET_POOL_FAILURE** (0X10006) No se pudo obtener el paquete del grupo de paquetes.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No se pudo comunicar con el agente.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) No se admiten los mensajes de QoS nivel 2.
- NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.
- NXD_MQTT_INVALID_PARAMETER (0x10009) Error de entrada del parámetro.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a>nxd_mqtt_client_subscribe

Suscripción a un tema

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a>Descripción

Este servicio se suscribe a un tema específico. Todavía no se admite la suscripción a mensajes de QoS de nivel 2.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **topic_name** Tema en el que se va a publicar.
- **topic_name_length** Longitud del tema, en bytes.
- **QoS Nivel de QoS deseado:** 0 ó 1.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) Se ha suscrito correctamente al tema.
- **NXD_MQTT_NOT_CONNECTED** (0X10002) El cliente no está conectado al agente.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No pueden enviar mensajes al agente.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) No se admiten los mensajes de QoS nivel 2.
- NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.
- NXD_MQTT_INVALID_PARAMETER (0x10009) El valor de topic_name no está establecido, o topic_name_length es cero, o el valor de QoS no es válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a>nxd_mqtt_client_unsubscribe

Cancela la suscripción a un tema

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a>Descripción

Este servicio cancela la suscripción de un tema.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **topic_name** Tema del que se cancelará la suscripción.
- **topic_name_length** Longitud del tema, en bytes.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) Se ha cancelado correctamente la suscripción al tema.
- **NXD_MQTT_NOT_CONNECTED** (0X10002) El cliente no está conectado al agente.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No pueden enviar mensajes al agente.
- NX_PTR_ERROR (0x07) Puntero de bloque de control MQTT no válido.
- NXD_MQTT_INVALID_PARAMETER (0x10009) El valor de topic_name no está establecido, o topic_name_length es cero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a>nxd_mqtt_client_receive_notify_set

Establece la función de devolución de llamada de la notificación de recepción de un mensaje MQTT

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada con el cliente MQTT. Al recibir un mensaje publicado por el agente, el cliente MQTT almacena el mensaje en la cola de recepción. Si está establecida la función de devolución de llamada, se invoca para notificar a la aplicación que un mensaje está listo para recuperarse. La función de notificación de recepción toma un puntero al bloque de control de cliente MQTT y un *message_count* que indica el número de mensajes disponibles en la cola de recepción. Tenga en cuenta que el número puede cambiar entre la notificación de recepción y el momento en que la aplicación recupera estos mensajes, ya que es posible que los mensajes nuevos hayan llegado durante el intervalo.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **receive_notify** Función de devolución de llamada proporcionada por el usuario que se invocará cuando se reciba un mensaje.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) La función de notificación de recepción se configuró correctamente.
- NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a>nxd_mqtt_client_message_get

Recupera de un mensaje del agente

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a>Descripción

Este servicio recupera un mensaje publicado por el agente. Todos los mensajes entrantes se almacenan en la cola de recepción. La aplicación usa este servicio para recuperar estos mensajes. Esta llamada no es de bloqueo. Si la cola de recepción está vacía, este servicio devuelve ***NXD_MQTT_NO_MESSAGE** _. Una aplicación que quiera recibir notificaciones acerca del mensaje entrante puede llamar al servicio _ *_nxd_mqtt_client_receive_notify_set_** para registrar una función de devolución de llamada de recepción.

El autor de la llamada debe proporcionar espacio de memoria para la cadena de tema y para el cuerpo del mensaje. Los tamaños de estos dos búferes se pasan mediante los parámetros *topic_buffer_size* y *message_buffer_size*. El número real de bytes de la cadena de tema y el cuerpo del mensaje se devuelven en los parámetros *actual_topic_length* y *actual_message_length*. Si la longitud del tema o del mensaje es mayor que el espacio en búfer proporcionado, este servicio devuelve el código de error *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.

La aplicación asignará un búfer de mayor tamaño y volverá a intentarlo.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **topic_buffer** Puntero a la ubicación de memoria en la que se copia la cadena de tema.
- **topic_buffer_size** Tamaño del búfer de tema.
- **actual_topic_length** Puntero a la ubicación de memoria en la que se devuelve la longitud real del tema.
- **message_buffer** Puntero a la ubicación de memoria en la que se copia la cadena de mensaje.
- **message_buffer_size** Tamaño del búfer de mensajes.
- **actual_message_length** Puntero a la ubicación de memoria en la que se devuelve la longitud del mensaje.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) Se recuperó correctamente el mensaje.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.
- **NXD_MQTT_NO_MESSAGE** (0x1000A) La cola de recepción está vacía.
- **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) El búfer de tema o mensaje es demasiado pequeño para el tema o mensaje.
- NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.
- NXD_MQTT_INVALID_PARAMETER (0x10009) El puntero de message_buffer o topic_buffer es NULL.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a>nxd_mqtt_client_disconnect_notify_set

Establece la función de devolución de llamada de notificación de desconexión del mensaje de MQTT

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a>Descripción

Este servicio registra una función de devolución de llamada con el cliente MQTT. Cuando MQTT detecta que se pierde la conexión con el agente, llama a esta función de notificación para avisar a la aplicación. Por lo tanto, la aplicación puede usar esta función de devolución de llamada para detectar una conexión perdida y restablecer la conexión con el agente.

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **disconnect_notify** Función de devolución de llamada proporcionada por el usuario que se va a invocar cuando MQTT detecte que se ha perdido la conexión con el agente.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) La función de notificación de desconexión se configuró correctamente.
- NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a>nxd_mqtt_client_disconnect

Desconecta el cliente MQTT del agente

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio desconecta el cliente del agente. Tenga en cuenta que se liberan los mensajes en la cola de recepción. No se liberan los mensajes con QoS 1 en la cola de transmisión. Una vez que el cliente se vuelve a conectar al servidor, se pueden procesar los mensajes con QoS 1, a menos que el cliente vuelva a conectarse al servidor con la marca *clean_session* establecida en ***NX_TRUE***.

Si la conexión se realizó con protección de seguridad de TLS, este servicio cerrará la sesión de TLS antes de desconectar la conexión TCP.

La llamada de desconexión del socket TCP real tiene una opción de espera que define el parámetro NXD_MQTT_SOCKET_TIMEOUT (tics del temporizador). El valor predeterminado es NX_WAIT_FOREVER. Para evitar la suspensión indefinida en caso de que se pierda la conexión de red o de que el servidor no responda, establezca esta opción en un valor finito.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) Se desconectó correctamente del agente.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT.
- NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a>nxd_mqtt_client_delete

Elimine la instancia de cliente MQTT

### <a name="prototype"></a>Prototipo

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina la instancia de cliente MQTT y libera los recursos internos. Este servicio desconecta automáticamente el cliente del agente si aún está conectado. Se liberan los mensajes que todavía no se han transmitido o no se han confirmado. También se liberan los mensajes que se han recibido pero que la aplicación no ha recuperado.

Si la conexión se realizó con protección de seguridad de TLS, este servicio cierra la sesión de TLS antes de desconectar la conexión TCP.

Una vez eliminado el cliente, una aplicación que quiera usar el servicio MQTT deberá crear una nueva instancia.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente MQTT.

### <a name="return-values"></a>Valores devueltos

- **NXD_MQTT_SUCCESS** (0x00) Se eliminó correctamente el cliente MQTT.
- NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
