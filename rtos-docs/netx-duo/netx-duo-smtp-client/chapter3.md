---
title: 'Capítulo 3: Descripción de los servicios de cliente SMTP'
description: Este capítulo contiene una descripción de todos los servicios de cliente SMTP de NetX Duo (que se enumeran a continuación) en orden de uso en una aplicación cliente SMTP típica.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814578"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a>Capítulo 3: Descripción de los servicios de cliente SMTP

Este capítulo contiene una descripción de todos los servicios de cliente SMTP de NetX Duo (que se enumeran a continuación) en orden de uso en una aplicación cliente SMTP típica.

> [!NOTE]
> En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **_NX_DISABLE_ERROR_CHECKING_** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.

## <a name="nxd_smtp_client_create"></a>nxd_smtp_client_create

Crea una instancia de cliente SMTP

### <a name="prototype"></a>Prototipo

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente SMTP en la instancia de IP especificada.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente SMTP.
- **ip_ptr** Puntero a la instancia de IP.
- **packet_pool_ptr** Puntero al grupo de paquetes de cliente.
- **username** Nombre de usuario terminado en NULL** para la autenticación.
- **password** Contraseña terminada en NULL para la autenticación.
- **from_address** Dirección del remitente terminada en NULL.
- **client_domain** Nombre de dominio terminado en NULL.
- **authentication_type** Tipo de autenticación de cliente. Estos son los tipos que se admiten:
  - NX_SMTP_CLIENT_AUTH_LOGIN
  - NX_SMTP_CLIENT_AUTH_PLAIN
  - NX_SMTP_CLIENT_AUTH_NONE
- **server_address** Puntero a la dirección IP del servidor SMTP.
- **server_port** Puerto TCP del servidor SMTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Cliente SMTP creado correctamente. Estado de creación de sockets TCP
- NX_SMTP_INVALID_PARAM (0xA5) Entrada no válida que no es de puntero.
- NX_IP_ADDRESS_ERROR (0x21) Tipo de dirección IP no válida.
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a>nx_smtp_client_delete

Elimina una instancia de cliente SMTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente SMTP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero a la instancia de cliente SMTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Cliente eliminado correctamente.
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a>nx_smtp_mail_send

Crea y envía un elemento de correo SMTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a>Descripción

Este servicio crea y envía un elemento de correo SMTP. El cliente SMTP establece una conexión TCP con el servidor SMTP y envía una serie de comandos SMTP. Si no se encuentra ningún error, transmitirá el mensaje de correo al servidor. Independientemente de si el correo se envía correctamente, finalizará la conexión TCP y devolverá un estado que indica el resultado de la transmisión del correo. La aplicación puede llamar a este servicio para tantos mensajes de correo como necesite enviar (sin límite).

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al cliente SMTP.
- **recipient_address** Dirección de destinatario terminada en NULL.
- **subject** Texto de la línea de asunto terminado en NULL.
- **priority** Nivel de prioridad con el que se entrega el correo.
- **mail_body** Puntero al mensaje de correo.
- **mail_body_length** Tamaño del mensaje de correo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Correo enviado correctamente.
- **NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) Instancia de cliente SMTP no inicializada para el resultado de la sesión SMTP.
- NX_PTR_ERROR (0x07) Parámetro de puntero no válido.
- NX_SMTP_INVALID_PARAM (0xA5) Entrada no válida que no es de puntero.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
