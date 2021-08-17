---
title: 'Capítulo 1: Introducción al cliente SMTP de Azure RTOS NetX Duo'
description: El Protocolo simple de transferencia de correo (SMTP) es un protocolo para transferir correo entre redes e Internet.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: df8c6b6920577ebfc18ed9252761401c30822c034e30d7ae95b25778707f53d5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797830"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-smtp-client"></a>Capítulo 1: Introducción al cliente SMTP de Azure RTOS NetX Duo

El Protocolo simple de transferencia de correo (SMTP) es un protocolo para transferir correo entre redes e Internet. Emplea servicios de Protocolo de control de transmisión (TCP) de confianza para realizar su función de transferencia de contenido.

## <a name="netx-duo-smtp-client-requirements"></a>Requisitos del cliente SMTP de NetX Duo

El cliente SMTP de NetX Duo requiere la creación de una instancia de IP de NetX Duo y un grupo de paquetes de NetX Duo. El cliente SMTP utiliza un socket de TCP para conectarse a un servidor SMTP en el *puerto 25 conocido. Por lo tanto*, TCP se debe habilitar primero llamando al servicio *nx_tcp_enable* en una instancia de IP creada anteriormente.

La llamada de creación del cliente SMTP (nxd_smtp_client_create) requiere un grupo de paquetes creado previamente para transmitir comandos SMTP al servidor, así como para enviar el mensaje de correo real. La carga de paquetes depende del tamaño previsto del contenido del correo y debe permitir TCP, el encabezado IP y el encabezado MAC. (Tenga en cuenta que el encabezado IPv6 es de 40 bytes, mientras que el encabezado IPv4 tiene 20 bytes).

Si el mensaje de correo completo no cabe en un paquete, el cliente SMTP asigna paquetes adicionales para que contengan el resto del mensaje.

## <a name="netx-duo-smtp-client-constraints"></a>Restricciones del cliente SMTP de NetX Duo

Aunque el protocolo de SMTP de NetX Duo implementa los estándares RFC 2821 y 2554, existen algunas restricciones:

1. El cliente SMTP de NetX Duo solo admite la autenticación LOGIN y PLAIN, pero no la autenticación implícita CRAM-MD5.
2. Los mensajes del cliente SMTP de NetX Duo se limitan a un destinatario por cada elemento de correo y solo un mensaje de correo por cada conexión TCP con el servidor SMTP.
3. No se admiten las opciones VRFY, SEND, SOML, EXPN, SAML, ETRN, TURN y SIZE de SMTP.
4. El cliente SMTP no es el explorador de correo ("agente de usuario de correo") que se utiliza normalmente para crear el mensaje de correo. Solo es un "agente de transferencia de correo". Proporcionará el procesamiento necesario del cuerpo del mensaje de correo para el transporte SMTP, como se especifica en la RFC 2821. No comprueba el contenido de la sintaxis correcta, por ejemplo, el destinatario y la ruta inversa. No hay ninguna restricción en cuanto al contenido del búfer de correo, por ejemplo, datos MIME o mensajes de texto no cifrado. El formato del mensaje de correo electrónico, especificado en la RFC 2822 para incluir encabezados y el cuerpo del mensaje, está fuera del ámbito de la API del cliente SMTP.

## <a name="commands-supported-by-netx-duo-smtp-client"></a>Comandos admitidos por el cliente SMTP de NetX Duo

El cliente SMTP de NetX Duo usa los siguientes comandos durante una sesión de correo con un servidor SMTP.

- **EHLO** El cliente desea iniciar una sesión que incluye algunos servicios SMTP del protocolo de extensión disponibles en el servidor SMTP (o todos ellos). Este es el valor predeterminado.
- **HELO** El cliente desea iniciar una sesión limitada a los servicios básicos de SMTP.
- **MAIL** El cliente desea que el servidor reciba el correo del cliente.
- **AUTH** El cliente desea iniciar la autenticación por el servidor.
- **RCPT** El cliente desea enviar un buzón de otro host al que desea que se entregue el correo.
- **DATA** El cliente desea iniciar el envío de datos del mensaje de correo al servidor.
- **QUIT** El cliente desea finalizar la sesión.

## <a name="getting-started"></a>Introducción

La aplicación cliente SMTP crea una instancia de IP y habilita TCP en esa instancia de IP. A continuación, crea el cliente SMTP con el siguiente servicio:

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type,
    NXD_ADDRESS *server_address, UINT port);
```

*client_packet_pool_ptr* es un puntero a un grupo de paquetes creado previamente que el cliente SMTP usará para enviar mensajes al servidor SMTP.

Tenga en cuenta que una aplicación debe proporcionar un valor *from_address* para el dispositivo local y una dirección IP de servidor. Todas las direcciones deben ser nombres de dominio completos. Un nombre de dominio completo contiene una parte local y un nombre de dominio, separados por un carácter "@". Tenga en cuenta que el cliente SMTP no comprueba la sintaxis de *from_address* o *recipient_address* en el servicio de nx_smtp_mail_send que se muestra a continuación.

Una vez creado el cliente SMTP, la aplicación cliente SMTP crea un elemento de correo con un mensaje de correo SMTP con formato correcto y realiza la solicitud de envío del elemento de correo al cliente SMTP mediante la siguiente API:

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address, UINT priority,
    CHAR *subject, CHAR *mail_body,
    UINT mail_body_length);
```

Esencialmente, no hay ninguna diferencia en la ejecución del cliente SMTP a través de IPv4 o IPv6 desde la perspectiva del usuario. Las diferencias entre los dos protocolos IP se tratan en la capa de NetX Duo subyacente.

Tenga en cuenta que una aplicación que desea enviar correo debe proporcionar una dirección de destinatario en la llamada *nx_smtp_client_mail*.

Para la autenticación, los nombres de usuario pueden ser nombres de dominio completos o nombres de usuario para mostrar. Esto depende de la forma en que el servidor realiza la autenticación.

En la demostración de la sección Pequeño ejemplo que figura más adelante en este manual de usuario se muestra cómo se debe dar formato al mensaje. El estado si el elemento de correo se envió correctamente será NX_SUCCESS. Si se produce un error, ya sea un error interno, una conexión TCP interrumpida o la recepción de un código de error de respuesta del servidor, *nx_smtp_mail_send* devolverá un estado de error distinto de cero.

Al enviar un elemento de correo, el cliente SMTP de NetX Duo crea una nueva conexión TCP con el servidor SMTP y comienza una sesión SMTP. En esta sesión, el cliente envía una serie de comandos al servidor SMTP como parte del protocolo SMTP, que culmina en el envío del mensaje de correo real. A continuación, se finaliza la conexión TCP, independientemente del resultado de la sesión SMTP.

Después de la transmisión de correo, independientemente de si se ha realizado correctamente o no, el cliente SMTP vuelve al estado "inicial" y se puede usar para otra sesión de transferencia de correo.

## <a name="netx-duo-smtp-authentication"></a>Autenticación SMTP de NetX Duo

La autenticación es una manera de que los clientes SMTP demuestren su identidad en el servidor SMTP y su correo se entregue como usuarios de confianza. La mayoría de los servidores SMTP comerciales requieren que los clientes se autentiquen.

Normalmente, los datos de autenticación se componen del nombre de usuario y la contraseña del remitente. Durante un desafío de autenticación, el servidor solicita esta información y el cliente responde mediante el envío de los datos solicitados en formato codificado. El servidor descodifica los datos e intenta encontrar una coincidencia en su base de datos de usuario. Si se encuentra, el servidor indica que la autenticación se ha realizado correctamente. La autenticación SMTP se define en [RFC 2554](http://www.ietf.org/rfc/rfc2554.txt).

Hay dos tipos de autenticación, a saber: *básica* e *implícita*. La implícita no se admite en el cliente SMTP de NetX Duo actual y no se tratará aquí. La autenticación básica es equivalente a la autenticación con *nombre* y *contraseña* que se ha descrito anteriormente. En la autenticación básica SMTP, el nombre y las contraseñas están codificados en Base64. La ventaja de la autenticación básica es su facilidad de implementación y uso generalizado. La principal desventaja de la autenticación básica es que los datos del nombre y la contraseña se transmiten abiertamente en la solicitud.

### <a name="plain-authentication"></a>Autenticación sin formato

El cliente SMTP de NetX Duo envía un comando AUTH con el parámetro PLAIN. Si el servidor SMTP de NetX Duo es compatible con este tipo de autenticación, responderá con un código de respuesta 334. El cliente responde con un único mensaje de nombre de usuario y contraseña codificados en base64 al servidor. Si el servidor determina que la autenticación del cliente se realiza correctamente, responde con el código 235.

### <a name="login-authentication"></a>Autenticación del inicio de sesión

El cliente SMTP de NetX Duo envía un comando AUTH con el parámetro LOGIN. Si el servidor SMTP de NetX Duo es compatible con este tipo de autenticación, responderá con un código de respuesta 334 como inicio del "desafío" de autenticación. Envía una solicitud codificada en Base64 al cliente, que suele ser "Username". El cliente descodifica la solicitud y responde con un nombre de usuario codificado en base64. Si el servidor acepta el nombre de usuario del cliente, envía una solicitud codificada en base64 para la contraseña del cliente. El cliente responde con una contraseña codificada en base64. Si el servidor determina que la autenticación del cliente se realiza correctamente, responde con el código 235.

### <a name="no-authentication"></a>Sin autenticación

Algunos servidores SMTP están configurados sin autenticación. En ese caso, la respuesta 250 al mensaje EHLO del cliente no mostrará ningún tipo de autenticación. Sin embargo, la ausencia de tipos de autenticación en la lista no significa necesariamente que el servidor no requiera o admita la autenticación. Si el cliente está configurado para la autenticación PLAIN o LOGIN en esta situación, la tarea del subproceso de cliente NetX Duo tendrá como valor predeterminado PLAIN. Si el cliente está configurado para NONE, se omite el paso de autenticación y el estado SMTP avanza al estado MAIL.

Tenga en cuenta que si el cliente está configurado sin autenticación y el servidor SMTP admite la autenticación, el tipo de autenticación del cliente se cambia a PLAIN.

## <a name="rfcs-supported-by-netx-duo-smtp-client"></a>RFC admitidas por el cliente SMTP de NetX Duo

La API del cliente SMTP de NetX Duo es compatible con la RFC 2821 "Protocolo simple de transferencia de correo" y la RFC 2554 "Extensión de servicio SMTP para autenticación". “
