---
title: 'Capítulo 1: Introducción al cliente Azure RTOS NetX POP3'
description: La API de cliente POP3 de Azure RTOS NetX proporciona un sistema de transporte de correo que permite que las estaciones de trabajo pequeñas accedan a los maildrops de los clientes en los servidores POP3 para recuperar el correo de los clientes.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 135530f11f8f54acd6d093a05332056dbdc32be3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815166"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a>Capítulo 1: Introducción al cliente Azure RTOS NetX POP3

El Protocolo de oficina de correo versión 3 (POP3) está diseñado para proporcionar un sistema de transporte de correo que permite que las estaciones de trabajo pequeñas accedan a los maildrops de los clientes en los servidores POP3 para recuperar el correo de los clientes. POP3 emplea servicios de protocolo de control de transmisión (TCP) para realizar la transferencia de archivos. Por este motivo, POP3 es un protocolo de transferencia de contenido de gran confiabilidad.

Sin embargo, POP3 no proporciona operaciones extensas en el control de correo. Por lo general, el cliente descarga el correo y, a continuación, se elimina del maildrop del servidor.

## <a name="netx-pop3-client-requirements"></a>Requisitos del cliente POP3 de NetX

### <a name="client-requirements"></a>Requisitos de cliente

La API de cliente POP3 de Azure RTOS NetX requiere una instancia de IP de NetX creada anteriormente mediante *nx_ip_create* y un grupo de paquetes NetX creado previamente mediante *nx_packet_pool_create*. Como el cliente POP3 de NetX usa servicios TCP, se debe habilitar TCP con la llamada *nx_tcp_enable* antes de usar los servicios del cliente POP3 de NetX en esa misma instancia de IP. El cliente POP3 usa un socket TCP para conectarse a un servidor POP3 en el puerto POP3 del servidor. Por lo general, se establece en el *puerto 110 conocido, aunque no se requiere ningún servidor ni cliente POP3 para usar este puerto.*

El usuario puede configurar el tamaño del grupo de paquetes utilizado al crear el cliente POP3 en términos de carga de paquetes y cantidad de paquetes disponibles. Si el paquete solo se usa en el servicio de creación del cliente POP3, la carga del paquete no necesita más de 100 a 120 bytes en función de la longitud del nombre de usuario y la contraseña, o la síntesis APOP. El comando USER con el nombre de usuario del host local es probablemente el mensaje más grande enviado por el cliente POP3. Es posible compartir el mismo grupo de paquetes en nx_ip_create (grupo de paquetes IP predeterminado), ya que las operaciones internas de IP no requieren una carga de paquetes muy grande para enviar y recibir datos de control de TCP.

Sin embargo, es posible que el controlador de red no sea ventajoso para usar el mismo grupo de paquetes que el grupo de paquetes del cliente POP3. Normalmente, la carga del grupo de paquetes de recepción se establece en la instancia de IP MTU (por lo general, 1500 bytes) de la interfaz de red, que es mucho más grande que los mensajes del cliente POP3. Los mensajes POP3 entrantes suelen ser datos mucho más grandes que los mensajes del cliente POP3 salientes.

## <a name="netx-pop3-client-creation"></a>Creación del cliente POP3 de NetX

El servicio de creación del cliente POP3, *nx_pop3_client_create*, crea el socket TCP y se conecta con el servidor POP3.

Después de conectar con el servidor POP3, la aplicación cliente POP3 puede llamar a *nx_pop3_client _mail_items_get* para obtener el número de elementos de correo que se encuentran en el cuadro maildrop:

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

Si uno o más elementos están en el maildrop del cliente, la aplicación puede obtener el tamaño de un elemento de correo específico mediante el servicio *nx_pop3_client_get_mail_item*:

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

El primer elemento de correo del maildrop se encuentra en el índice 1.

Para obtener el mensaje de correo real, la aplicación puede llamar al servicio *nx_pop3_client_mail_item_get_message_data* a fin de recuperar los paquetes de mensajes de correo hasta que el servicio indique que el argumento de entrada final_packet recibe el último paquete:

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

Para eliminar un elemento de correo específico, la aplicación llama a *nx_pop3_client_mail_item_delete* con el mismo índice que se utilizó en la llamada a *nx_pop3_client_get_mail_item* anterior.

Se puede eliminar el cliente mediante el servicio *nx_pop3_client_delete*. Tenga en cuenta que depende de la aplicación eliminar el grupo de paquetes del cliente POP3 mediante el servicio *nx_packet_pool_delete* si ya no es necesario.

## <a name="netx-pop3-client-constraints"></a>Restricciones del cliente POP3 de NetX

Existen algunas restricciones en la implementación del cliente POP3 de NetX:

1. El cliente POP3 de NetX no admite el comando AUTH, aunque implementa la autenticación APOP mediante DIGEST-MD5 para el intercambio de autenticación cliente-servidor.

1. El cliente POP3 de NetX no implementa todos los comandos de POP3 (por ejemplo, los comandos TOP o UIDL). A continuación se muestra una lista de los comandos que admite:
   - NOOP
   - RSET

## <a name="netx-pop3-client-login"></a>Inicio de sesión del cliente POP3 de NetX

Un cliente POP3 de NetX debe autenticarse (iniciar sesión) en un servidor POP3 para tener acceso a un maildrop. Para ello, puede usar los comandos USER/PASS y proporcionar un nombre de usuario y una contraseña conocidos para el servidor POP3, o bien mediante el comando APOP y la síntesis MD5 que se describe a continuación.

El nombre de usuario suele ser un nombre de dominio completo (contiene una parte local y un nombre de dominio, separados por un carácter "@"). Al usar los comandos USER y PASS de POP3, el cliente envía su nombre de usuario y contraseña sin cifrar a través de Internet.

Para evitar el riesgo de seguridad de ingresar el nombre de usuario y la contraseña en texto sin formato, el cliente POP3 de NetX se puede configurar para usar la autenticación APOP configurando el parámetro *APOP_authentication* en el servicio *nx_pop3_client_create*:

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

O bien, solo para las aplicaciones IPv4, el servicio *nx_pop3_client_create*:

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

Cuando el cliente envía el comando APOP, toma una síntesis MD5 que contiene el dominio del servidor, la hora local y el id. de proceso extraídos del saludo del servidor, además de la contraseña del cliente. El servidor POP3 creará una síntesis MD5 que contiene la misma información y, si su síntesis MD5 coincide con el resumen MD5 del cliente, el cliente se autentica.

Si se produce un error en la autenticación de APOP, el cliente POP3 de NetX intentará la autenticación con USER/PASS.

## <a name="the-pop3-client-maildrop"></a>Maildrop de cliente POP3

El correo del cliente se almacena en un servidor POP3 en un buzón o "maildrop". Un maildrop de cliente en un servidor POP3 se representa como una lista de elementos de correo electrónico basada en 1. Es decir, para hacer referencia a cada correo, se hace mediante su índice en la lista del maildrop con el primer elemento de correo en el índice 1 (no cero). Los comandos de POP3 hacen referencia a elementos de correo específicos según su índice en esta lista.

## <a name="the-pop3-protocol-state-machine"></a>Máquina de estados del protocolo POP3

El protocolo POP3 requiere que tanto el cliente como el servidor mantengan el estado de la sesión POP3. En primer lugar, el cliente intenta conectarse al servidor POP3. Si se ejecuta correctamente, entra en el protocolo POP3 que tiene tres estados distintos que se definen en RFC 1939. El estado inicial es el estado de autorización con el que debe identificarse en el servidor. En el estado de autorización, el cliente POP3 solo puede emitir los comandos USER y PASS, y en ese orden, o el comando APOP.

Una vez que se autentica el cliente POP3, la sesión del cliente entra en el estado de transacción. En este estado, el cliente puede descargar correo y solicitar su eliminación. Los comandos que permite el estado de transacción son LIST, STAT, RETR, DELE, RSET y QUIT. Por lo general, el cliente POP3 envía un comando STAT seguido de una serie de comandos RETR (uno para cada elemento de correo en su maildrop).

Una vez que el cliente emite el comando QUIT, la sesión POP3 entra en el estado de actualización en el que se inicia la desconexión TCP del servidor. Para descargar correo más tarde, la aplicación cliente POP3 puede llamar a `nx_pop3_client_mail_items_get` en cualquier momento para comprobar si hay correo nuevo en el maildrop.

### <a name="pop3-server-reply-codes"></a>Códigos de respuesta del servidor POP3

- **+OK**: el servidor utiliza esta respuesta para aceptar un comando de cliente. El servidor puede incluir información adicional después de "+OK", pero no puede suponer que el cliente procesará esta información, salvo en el caso de la descarga de datos de mensajes de correo o de los comandos LIST o DELE. En el último caso, el "argumento" después del comando hace referencia al índice del elemento de correo en el maildrop del cliente.

- **+ERR**: el servidor utiliza esta respuesta para rechazar un comando de cliente. El servidor puede enviar información adicional después de "-ERR", pero no puede suponer que el cliente procesará esta información.

### <a name="sample-pop3-client---server-session"></a>Sesión de cliente-servidor POP3 de ejemplo

**Ejemplo básico de POP3 con USER/PASS:**

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

**Ejemplo básico de POP3 con APOP (y LIST en lugar de STAT):**

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-pop3-client"></a>RFC admitidos por el cliente POP3 de NetX

El cliente POP3 de NetX es compatible con RFC 1939.
