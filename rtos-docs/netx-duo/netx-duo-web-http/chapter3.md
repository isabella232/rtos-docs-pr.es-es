---
title: 'Capítulo 3: Descripción de los servicios HTTP'
description: Este capítulo contiene una descripción de todos los servicios Web HTTP de NetX (se enumeran a continuación) por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0357afe7f997c84a5d031ca71dc524e381734b4a
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178194"
---
# <a name="chapter-3---description-of-http-services"></a>Capítulo 3: Descripción de los servicios HTTP

Este capítulo contiene una descripción de todos los servicios Web HTTP de NetX (se enumeran a continuación) por orden alfabético.

> [!NOTE]
> En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.

## <a name="http-and-https-client-api"></a>API de cliente HTTP y HTTPS

## <a name="nx_web_http_client_connect"></a>nx_web_http_client_connect

Abre un socket de texto simple en un servidor HTTP para las solicitudes personalizadas

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio abre un socket TCP de texto no cifrado en un servidor HTTP, pero no envía ninguna solicitud. Las solicitudes se crean con n *x_web_http_client_request_initialize()* y se envían mediante *nx_web_http_client_request_send()* . Se pueden agregar encabezados HTTP personalizados a la solicitud mediante *nx_web_http_client_request_header_add()* .

El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud. **Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.**

> [!NOTE]
> Los métodos nx_web_http_client_*_start se proporcionan por comodidad (por ejemplo, *nx_web_http_client_get_start*()) y controlan la generación de solicitudes y la conexión de socket. Puede usar esos servicios en lugar de *nx_web_http_client_connect()* y las rutinas relacionadas si no necesita encabezados HTTP personalizados en sus solicitudes.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **server_ip** Dirección IP del servidor HTTP remoto.
- **server_port** Puerto en el servidor HTTP remoto (por ejemplo, 80 para HTTP).
- **wait_option** Define cuánto tiempo esperará el servicio para las operaciones de red subyacentes. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) conexión correcta del socket TCP.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_WEB_HTTP_NOT_READY (0x3000A) Ya hay otra solicitud en curso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a>nx_web_http_client_create

Crea una instancia de cliente HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente HTTP en la instancia de IP especificada. La instancia de cliente se puede usar para HTTP o HTTPS. Consulte los servicios *nx_web_http_client_connect()* y *nx_web_http_client_secure_connect()* para obtener más información sobre cómo iniciar una instancia HTTP o HTTPS. Consulte también la API de *nx_web_http_client_get_**, *nx_web_http_client_put_**, *nx_web_http_client_post_** para invocaciones simples de los métodos GET, PUT y POST.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **client_name** Nombre de la instancia de cliente HTTP.
- **ip_ptr** Puntero a la instancia de IP.
- **pool_ptr** Puntero al grupo de paquetes predeterminado. Tenga en cuenta que los paquetes de este grupo deben tener una carga útil lo suficientemente grande como para controlar el encabezado de respuesta completo. Esto lo define *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* en *nx_web_http_client.h*.
- **window_size** Tamaño de la ventana de recepción del socket TCP del cliente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Cliente HTTP creado correctamente.
- NX_PTR_ERROR (0x16) Puntero HTTP, ip_ptr o de grupo de paquetes no válido.
- NX_WEB_HTTP_POOL_ERROR (0x30009) Tamaño de carga no válido en el grupo de paquetes.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a>nx_web_http_client_delete

Elimina una instancia de cliente HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente HTTP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Cliente HTTP eliminado correctamente.
- NX_PTR_ERROR (0x16) El puntero HTTP no es válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a>nx_web_http_client_delete_start

Inicia una solicitud DELETE de HTTP de texto no cifrado

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta enviar una solicitud DELETE para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Esta API está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_delete_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud DELETE de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a>nx_web_http_client_delete_start_extended

Inicia una solicitud DELETE de HTTP de texto no cifrado

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta enviar una solicitud DELETE para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_delete_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud DELETE de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a>nx_web_http_client_delete_secure_start

Inicia una solicitud DELETE de HTTPS cifrada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta enviar una solicitud DELETE para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_delete_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado. El recurso debe terminar en NULL.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud DELETE de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a>nx_web_http_client_delete_secure_start_extended

Inicia una solicitud DELETE de HTTPS cifrada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta enviar una solicitud DELETE para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_delete_secure_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado. El recurso debe terminar en NULL.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud DELETE de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.


### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a>nx_web_http_client_get_start

Inicia una solicitud GET de HTTP de texto no cifrado

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_web_http_client_response_body_get()* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_delete_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a>nx_web_http_client_get_start_extended

Inicia una solicitud GET de HTTP de texto no cifrado

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_web_http_client_response_body_get()* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_delete_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a>nx_web_http_client_get_secure_start

Inicia una solicitud GET cifrada de HTTPS

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_web_http_client_response_body_get()* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_get_secure_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a>nx_web_http_client_get_secure_start_extended

Inicia una solicitud GET cifrada de HTTPS

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_web_http_client_response_body_get()* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_secure_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a>nx_web_http_client_head_start

Inicia una solicitud HEAD de HTTP de texto no cifrado

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta recuperar los metadatos HEAD para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_head_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud HEAD de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a>nx_web_http_client_head_start_extended

Inicia una solicitud HEAD de HTTP de texto no cifrado

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta recuperar los metadatos HEAD para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_head_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud HEAD de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a>nx_web_http_client_head_secure_start

Inicia una solicitud HEAD cifrada de HTTPS

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta recuperar los metadatos HEAD para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor correspondiente al contenido del recurso solicitado.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_head_secure_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud HEAD de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a>nx_web_http_client_head_secure_start_extended

Inicia una solicitud HEAD cifrada de HTTPS

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta recuperar los metadatos HEAD para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor correspondiente al contenido del recurso solicitado.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_head_secure_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud HEAD de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a>nx_web_http_client_request_packet_allocate

Asigna un paquete HTTP(S)

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta asignar un paquete para HTTP(S) de cliente.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **packet_ptr** Puntero al paquete asignado.
- **wait_option** Define el tiempo de espera en tics si no hay paquetes disponibles en el grupo de paquetes. Las opciones de espera se definen de la siguiente forma:
  - **NX_NO_WAIT**: (0x00000000)
  - **NX_WAIT_FOREVER** (0xFFFFFFFF)
  - **TIMEOUT_IN_TICKS** (de 0x00000001 a 0xFFFFFFFE)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Asignación correcta de paquetes.
- **NX_NO_PACKET** (0X01) No hay ningún paquete disponible.
- **NX_WAIT_ABORTED** (0x1A) Una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.
- **NX_INVALID_PARAMETERS** (0x4D) El tamaño de paquete no admite el protocolo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a>nx_web_http_client_post_start

Envía una solicitud POST de HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta enviar una solicitud POST con el recurso especificado al servidor HTTP en la dirección IP y el puerto proporcionados. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet* para enviar el contenido del recurso al servidor HTTP.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_post_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto TCP en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud POST enviado correctamente.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a>nx_web_http_client_post_start_extended

Envía una solicitud POST de HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta enviar una solicitud POST con el recurso especificado al servidor HTTP en la dirección IP y el puerto proporcionados. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet* para enviar el contenido del recurso al servidor HTTP.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_post_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto TCP en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud POST enviado correctamente.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a>nx_web_http_client_post_secure_start

Inicia una solicitud POST cifrada de HTTPS

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta enviar una solicitud POST con el recurso especificado al servidor HTTPS en la dirección IP y el puerto proporcionados. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_post_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto TCP en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud POST enviado correctamente.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a>nx_web_http_client_post_secure_start_extended

Inicia una solicitud POST cifrada de HTTPS

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta enviar una solicitud POST con el recurso especificado al servidor HTTPS en la dirección IP y el puerto proporcionados. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_post_secure_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto TCP en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de solicitud POST enviado correctamente.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a>nx_web_http_client_put_start

Inicia una solicitud PUT de HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP y el puerto proporcionados. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_put_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto TCP en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a>nx_web_http_client_post_start_extended

Inicia una solicitud PUT de HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTP de **texto no cifrado**.

Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP y el puerto proporcionados. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_post_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto TCP en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a>nx_web_http_client_put_secure_start

Inicia una solicitud PUT cifrada de HTTPS

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTPS en la dirección IP y el puerto proporcionados. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_put_secure_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto TCP en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a>nx_web_http_client_put_secure_start_extended

Inicia una solicitud PUT cifrada de HTTPS

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTPS en la dirección IP y el puerto proporcionados. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.

Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_put_secure_start*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **ip_address** Dirección IP del servidor HTTP.
- **server_port** Puerto TCP en el servidor HTTP remoto.
- **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a>nx_web_http_client_put_packet

Envía el siguiente paquete de datos de recursos

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta enviar el siguiente paquete de contenido de recursos al servidor HTTP para las operaciones PUT y POST. Tenga en cuenta que se debe llamar a esta rutina repetidamente hasta que la longitud combinada de los paquetes enviados sea igual al objeto “total_bytes” especificado en la llamada anterior a *nx_web_http_client_put_start()* o *nx_web_http_client_post_start()* (o sus correspondientes versiones seguras).

Este servicio también busca una respuesta del servidor en caso de que se haya producido un problema al establecer la conexión HTTP (o HTTPS).

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **packet_ptr** Puntero al siguiente contenido del recurso que se va a enviar al servidor HTTP.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Paquete de cliente HTTP enviado correctamente.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.
- **NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Código de error del servidor recibido.**
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Longitud de paquete no válida.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) El servidor responde antes de que PUT finalice.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_INVALID_PACKET (0x12) El paquete es demasiado pequeño para el encabezado TCP.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a>nx_web_http_client_request_chunked_set

Establece una transferencia fragmentada para la solicitud HTTP(S)

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio utiliza codificación de transferencia fragmentada para enviar una solicitud HTTP(S) personalizada al servidor especificado en la llamada *nx_web_http_client_connect()* o *nx_web_http_client_secure_connect()* que previamente ha establecido la conexión de socket al host remoto.

> [!NOTE]
> Si la aplicación utiliza codificación de transferencia fragmentada para enviar un paquete de datos de solicitud, debe llamar a este servicio después de llamar a *nx_web_http_client_request_packet_allocate*() y antes de llamar a *nx_web_http_client_reqeust_packet_send*().

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **chunk_size** Tamaño de los datos de fragmentos en octetos.
- **packet_ptr** El puntero de paquete de datos de solicitud HTTP(S).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Fragmento establecido correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a>nx_web_http_client_request_header_add

Agrega un encabezado personalizado a una solicitud HTTP personalizada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a>Descripción

Este servicio agrega un encabezado personalizado (en forma de nombre y valor de campo) a una solicitud HTTP personalizada creada con n *x_web_http_client_request_initialize()* .

El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud. **Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.**

> [!NOTE]
> Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad. Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_initialize())* para crear y enviar solicitudes HTTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **field_name** Cadena de nombre de campo (por ejemplo, “Content-Type”).
- **name_length** Longitud de la cadena de nombre de campo en bytes.
- **field_value** Cadena de valor de campo (por ejemplo, “application/octet-stream”).
- **value_length** Longitud de la cadena de valor en bytes.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se ha agregado correctamente el encabezado a la solicitud.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a>nx_web_http_client_request_initialize

Inicializa una solicitud HTTP personalizada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>Descripción

Este servicio crea una solicitud HTTP personalizada y la asocia a la instancia de cliente HTTP. A diferencia del servicio más sencillo *nx_web_http_client_get_start()* (junto con los métodos para PUT, POST y las versiones seguras asociadas de esas API), la solicitud personalizada no se envía hasta que se llama al servicio *nx_web_http_client_request_send()* .

El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud mediante el servicio ***nx_web_http_client_request_header_add()***. Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.

> [!NOTE]
> Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad. Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_send())* para crear y enviar solicitudes HTTP.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_client_request_initialize_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **method** Método de solicitud HTTP que se va a usar. Las opciones se definen de la siguiente forma:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resource** Nombre del recurso que se va a transferir.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **input_size** Tamaño de los datos de entrada para PUT y POST. Pase 0 para otras operaciones.
- **transfer_encoding_trunked** Parámetro reservado para la compatibilidad futura con transferencias troncales.
- **username** Nombre de usuario para los recursos protegidos.
- **password** Contraseña para los recursos protegidos.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) La solicitud se ha inicializado correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_WEB_HTTP_METHOD_ERROR (0x30014) Faltaba información necesaria (por ejemplo, input_size para PUT o POST).

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a>nx_web_http_client_request_initialize_extended

Inicializa una solicitud HTTP personalizada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a>Descripción

Este servicio crea una solicitud HTTP personalizada y la asocia a la instancia de cliente HTTP. A diferencia del servicio más sencillo *nx_web_http_client_get_start()* (junto con los métodos para PUT, POST y las versiones seguras asociadas de esas API), la solicitud personalizada no se envía hasta que se llama al servicio *nx_web_http_client_request_send()* .

El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud mediante el servicio ***nx_web_http_client_request_header_add()***. Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.

> [!NOTE]
> Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad. Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_send())* para crear y enviar solicitudes HTTP.

Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_client_request_initialize*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **method** Método de solicitud HTTP que se va a usar. Las opciones se definen de la siguiente forma:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resource** Nombre del recurso que se va a transferir.
- **resource_length** Longitud de cadena del recurso solicitado.
- **host** Cadena terminada en NULL del nombre de dominio del servidor. Esta cadena se transmite en el campo de encabezado del host HTTP. La cadena de host no puede ser NULL.
- **host_length** Longitud de cadena del host.
- **input_size** Tamaño de los datos de entrada para PUT y POST. Pase 0 para otras operaciones.
- **transfer_encoding_trunked** Parámetro reservado para la compatibilidad futura con transferencias troncales.
- **username** Puntero al nombre de usuario opcional para la autenticación.
- **username_length** Longitud de cadena del nombre de usuario para la autenticación.
- **password** Puntero a la contraseña opcional para la autenticación.
- **password_length** Longitud de cadena de la contraseña para la autenticación.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) La solicitud se ha inicializado correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_WEB_HTTP_METHOD_ERROR (0x30014) Faltaba información necesaria (por ejemplo, input_size para PUT o POST).

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a>nx_web_http_client_request_packet_send

Envía un paquete de datos de solicitud HTTP(S) al servidor remoto

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía un paquete de datos de solicitud HTTP(S) personalizado creado con *nx_web_http_client_request_packet_allocate*() al servidor especificado en la llamada *nx_web_http_client_connect()* o *nx_web_http_client_secure_connect(* ) que previamente ha establecido la conexión de socket al host remoto.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **packet_ptr** El puntero de paquete de datos de solicitud HTTP(S).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Paquete de datos de la solicitud enviado correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a>nx_web_http_client_request_send

Envía una solicitud HTTP personalizada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a>Descripción

Este servicio envía una solicitud HTTP personalizada creada con *nx_web_http_client_request_initialize*() al servidor especificado en la llamada *nx_web_http_client_connect()* o *nx_web_http_client_secure_connect(* ) (ambos previamente han establecido la conexión de socket al host remoto).

El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud mediante el servicio ***nx_web_http_client_request_header_add()***. Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.

> [!NOTE]
> Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad. Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_initialize())* para crear y enviar solicitudes HTTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Solicitud enviada correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a>nx_web_http_client_response_body_get

Obtiene el siguiente paquete de datos de recursos

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a>Descripción

Este servicio recupera el siguiente paquete de contenido del recurso solicitado por la solicitud anterior. Deben realizarse llamadas sucesivas a esta rutina hasta que se reciba el estado de devolución de NX_WEB_HTTP_GET_DONE.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **packet_ptr** Destino del puntero de paquete que contiene el contenido parcial del recurso.
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Paquete de cliente HTTP obtenido correctamente.
- **NX_WEB_HTTP_GET_DONE** (0x3000C) Obtención del paquete de cliente HTTP completada.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está en modo GET.
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Longitud de paquete no válida.
- **NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) Código de estado HTTP 100 - Continuar.
- **NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) Código de estado HTTP 101 - Cambiando protocolos.
- **NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) Código de estado HTTP 201 - Creado.
- **NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) Código de estado HTTP 202 - Aceptado.
- **NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) Código de estado HTTP 203 - Información no autoritativa.
- **NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) Código de estado HTTP 204 - Sin contenido.
- **NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) Código de estado HTTP 205 - Restablecer contenido.
- **NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) Código de estado HTTP 206 - Contenido parcial.
- **NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) Código de estado HTTP 300 - Varias opciones.
- **NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) Código de estado HTTP 301 - Trasladado permanentemente.
- **NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) Código de estado HTTP 302 - Encontrado.
- **NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) Código de estado HTTP 303 - Ver otro.
- **NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) Código de estado HTTP 304 - Sin modificar.
- **NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) Código de estado HTTP 305 - Usar proxy.
- **NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) Código de estado HTTP 307 - Redirección temporal.
- **NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) Código de estado HTTP 400 - Solicitud incorrecta.
- **NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) Código de estado HTTP 401 - No autorizado.
- **NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x3002B) Código de estado HTTP 402 - Solicitud incorrecta.
- **NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) Código de estado HTTP 403 - Prohibido.
- **NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) Código de estado HTTP 404 - No encontrado.
- **NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) Código de estado HTTP 405 - Método no permitido.
- **NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) Código de estado HTTP 406 - No aceptable.
- **NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) Código de estado HTTP 407 - Autenticación de proxy necesaria.
- **NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) Código de estado HTTP 408 - Tiempo de espera de solicitud agotado.
- **NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) Código de estado HTTP 409 - Conflicto.
- **NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) Código de estado HTTP 410 - Desaparecido.
- **NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) Código de estado HTTP 411 - Longitud requerida.
- **NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) Código de estado HTTP 412 - Error de condición previa.
- **NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) Código de estado HTTP 413 - Entidad de solicitud demasiado grande.
- **NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) Código de estado HTTP 414 - Dirección URL de solicitud demasiado grande.
- **NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) Código de estado HTTP 415 - Tipo de medio no admitido.
- **NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) Código de estado HTTP 416 - No se puede satisfacer el rango solicitado.
- **NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) Código de estado HTTP 417 - Error de expectativa.
- **NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) Código de estado HTTP 500 - Error interno del servidor.
- **NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) Código de estado HTTP 501 - No implementado.
- **NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) Código de estado HTTP 502 - Puerta de enlace incorrecta.
- **NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) Código de estado HTTP 503 - Servicio no disponible.
- **NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) Código de estado HTTP 504 - Tiempo de espera de puerta de enlace.
- **NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) Código de estado HTTP 505 - Versión no admitida.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a>nx_web_http_client_response_header_callback_set

Establece la devolución de llamada para invocar al procesar encabezados HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a>Descripción

Este servicio asigna una devolución de llamada que se invocará cuando el cliente Web HTTP de NetX procese un encabezado HTTP en una respuesta entrante desde un servidor HTTP remoto. La devolución de llamada se invoca una vez para cada encabezado de la respuesta cuando se procesa. La devolución de llamada permite a una aplicación cliente HTTP tener acceso a cada uno de los encabezados de la respuesta del servidor HTTP para realizar cualquier acción deseada más allá del procesamiento básico que el cliente Web HTTP de NetX.

### <a name="input-parameters"></a>Parámetros de entrada

**client_ptr** Puntero al bloque de control del cliente HTTP.

**callback_function** Devolución de llamada invocada durante el procesamiento de encabezados de respuesta. La devolución de llamada se invoca con el nombre y el valor del campo como cadenas (y sus longitudes). Por ejemplo, el encabezado “Content-Length: 100” haría que la función se invocara con “Content-Length” para *field_name* y la cadena “100” para *field_value*.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Asignación correcta de devolución de llamada.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a>nx_web_http_client_secure_connect

Abre una sesión de TLS en un servidor HTTPS para las solicitudes personalizadas

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este método es para HTTPS **protegido por TLS**.

Este servicio abre una sesión de TLS protegida en un servidor HTTPS, pero no envía ninguna solicitud. Las solicitudes se crean con n *x_web_http_client_request_initialize()* y se envían mediante *nx_web_http_client_request_send()* . Se pueden agregar encabezados HTTP personalizados a la solicitud mediante *nx_web_http_client_request_header_add()* .

El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud. **Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.**

> [!NOTE]
> Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad. Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_initialize())* para crear y enviar solicitudes HTTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **server_ip** Dirección IP del servidor HTTPS remoto.
- **server_port** Puerto en el servidor HTTPS remoto (por ejemplo, 443 para HTTPS).
- **tls_setup** Devolución de llamada que se usa para la configuración de TLS. La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).
- **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Conexión correcta de la sesión de TLS.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_WEB_HTTP_NOT_READY (0x3000A) Ya hay otra solicitud en curso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a>API de servidor HTTP y HTTPS

## <a name="nx_web_http_server_cache_info_callback_set"></a>nx_web_http_server_cache_info_callback_set

Establece la devolución de llamada para recuperar la antigüedad máxima y la fecha de la dirección URL

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a>Descripción

Este servicio establece el servicio de devolución de llamada invocado para obtener la antigüedad máxima y la fecha de última modificación del recurso especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **cache_info_get** Puntero a la devolución de llamada.
- **max_age** Puntero a la antigüedad máxima de un recurso.
- **data** Puntero a la fecha de última modificación devuelta.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización

### <a name="example"></a>Ejemplo

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a>nx_web_http_server_callback_data_send

Envía datos desde la función de devolución de llamada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a>Descripción

Este servicio envía los datos del paquete proporcionado desde la rutina de devolución de llamada de la aplicación. Normalmente se usa para enviar datos dinámicos asociados a solicitudes GET/POST. Tenga en cuenta que si se usa esta función, la rutina de devolución de llamada es responsable de enviar la respuesta completa en el formato correcto. Además, la rutina de devolución de llamada debe devolver el estado de NX_WEB_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **data_ptr** Puntero a los datos que se van a enviar.
- **data_length** Número de bytes que se van a enviar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a>nx_web_http_server_callback_generate_response_header

Crea un encabezado de respuesta en una función de devolución de llamada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Descripción

Este servicio se usa en la rutina de devolución de llamada del servidor HTTP(S) (definida por la aplicación) para generar un encabezado de respuesta HTTP. La rutina de devolución de llamada del servidor se invoca cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE de cliente que requieren una respuesta HTTP. Esta función toma la información de la respuesta de la aplicación y genera el encabezado de respuesta adecuado. Consulte el servicio *nx_web_http_server_create()* para obtener más información sobre la rutina de devolución de llamada de solicitud del servidor.

Esta API está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_server_callback_generate_response_header_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.
- **status_code** Indica el estado del recurso. Ejemplos:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **content_length** Tamaño del contenido en bytes.
- **content_type** Tipo de HTTP, por ejemplo, “texto/sin formato”.
- **additional_header** Puntero a texto de encabezado adicional.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Encabezado HTML creado correctamente.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a>nx_web_http_server_callback_generate_response_header_extended

Crea un encabezado de respuesta en una función de devolución de llamada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a>Descripción

Este servicio se usa en la rutina de devolución de llamada del servidor HTTP(S) (definida por la aplicación) para generar un encabezado de respuesta HTTP. La rutina de devolución de llamada del servidor se invoca cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE de cliente que requieren una respuesta HTTP. Esta función toma la información de la respuesta de la aplicación y genera el encabezado de respuesta adecuado. Consulte el servicio *nx_web_http_server_create()* para obtener más información sobre la rutina de devolución de llamada de solicitud del servidor.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.
- **status_code** Indica el estado del recurso. Ejemplos:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **status_code_length** Longitud de cadena del código de estado.
- **content_length** Tamaño del contenido en bytes.
- **content_type** Tipo de HTTP, por ejemplo, “texto/sin formato”.
- **content_type_length** Longitud de cadena del tipo de contenido.
- **additional_header** Puntero a texto de encabezado adicional.
- **additional_header_length** Longitud del texto de encabezado adicional.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Encabezado HTML creado correctamente.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a>nx_web_http_server_callback_packet_send

Envía un paquete HTTP desde la función de devolución de llamada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía una respuesta completa del servidor HTTP desde una devolución de llamada HTTP. El servidor HTTP enviará el paquete con NX_WEB_HTTP_SERVER _TIMEOUT_SEND. El encabezado y los datos HTTP deben anexarse al paquete. Si el estado devuelto indica un error, la aplicación HTTP debe liberar el paquete.

La devolución de llamada debe devolver NX_WEB_HTTP_CALLBACK_COMPLETED.

Consulte *nx_web_http_server_callback_generate_response_header()* para ver un ejemplo más detallado.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **packet_ptr** Puntero al paquete que se va a enviar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Paquete de servidor HTTP enviado correctamente.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a>nx_web_http_server_callback_response_send

Envía una respuesta desde la función de devolución de llamada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a>Descripción

Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación. Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST. Tenga en cuenta que si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_WEB_HTTP_CALLBACK_COMPLETED.

Este servicio está en desuso. Se recomienda a los desarrolladores que utilicen *nx_web_http_server_callback_response_send_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **header** Puntero a la cadena de encabezado de respuesta.
- **information** Puntero a la cadena de información.
- **additional_info** Puntero a la cadena de información adicional.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Respuesta de servidor HTTP enviada correctamente.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a>nx_web_http_server_callback_response_send_extended

Envía una respuesta desde la función de devolución de llamada

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a>Descripción

Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación. Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST. Tenga en cuenta que si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_WEB_HTTP_CALLBACK_COMPLETED.

Las cadenas “header”, “information” y “additional_info” deben terminar en NULL y la longitud de cada cadena coincide con la longitud especificada en la lista de argumentos.

Este servicio reemplaza a *nx_web_http_server_callback_response_send*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **header** Puntero a la cadena de encabezado de respuesta.
- **header_length** Longitud de la cadena de encabezado de respuesta.
- **information** Puntero a la cadena de información.
- **Information_length** Longitud de la cadena de información.
- **additional_info** Puntero a la cadena de información adicional.
- **additional_info_length** Longitud de la cadena de información adicional.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Respuesta de servidor HTTP enviada correctamente.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a>nx_web_http_server_content_get

Obtiene contenido de la solicitud

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Descripción

Este servicio intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST o PUT. Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.
- **byte_offset** Número de bytes que se van a desplazar en el área de contenido.
- **destination_ptr** Puntero al área de destino para el contenido.
- **destination_size** Número máximo de bytes disponibles en el área de destino.
- **actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) Error interno del servidor HTTP.
- **NX_WEB_HTTP_DATA_END** (0x30007) Fin de la solicitud de contenido.
- **NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo de espera del servidor HTTP para obtener el siguiente paquete de contenido.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a>nx_web_http_server_content_get_extended

Obtiene contenido de la solicitud/admite la longitud del contenido de longitud cero

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Descripción

Este servicio es casi idéntico a *nx_web_http_server_content_get()* ; intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST o PUT. Sin embargo, administra las solicitudes con longitud de contenido de valor cero (“solicitud vacía”) como solicitud válida. Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).

Este servicio reemplaza a *nx_web_http_server_content_get*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.
- **byte_offset** Número de bytes que se van a desplazar en el área de contenido.
- **destination_ptr** Puntero al área de destino para el contenido.
- **destination_size** Número máximo de bytes disponibles en el área de destino.
- **actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.
- **NX_WEB_HTTP_ERROR** (0x30000) Error interno del servidor HTTP.
- **NX_WEB_HTTP_DATA_END** (0x30007) Fin de la solicitud de contenido.
- **NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo de espera del servidor HTTP para obtener el siguiente paquete.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a>nx_web_http_server_content_length_get

Obtiene la longitud del contenido de la solicitud/admite la longitud del contenido de cero.

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Descripción

Este servicio intenta recuperar la longitud del contenido HTTP en el paquete proporcionado. El valor devuelto indica el estado de finalización correcta y el valor de longitud real se devuelve en el puntero de entrada content_length. Si no hay contenido HTTP/longitud de contenido = 0, esta rutina sigue devolviendo un estado de finalización correcta y el puntero de entrada content_length apunta a una longitud válida (cero). Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).

### <a name="input-parameters"></a>Parámetros de entrada

- **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.
- **CONTENT_LENGTH** Puntero al valor recuperado del campo de longitud de contenido.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Longitud del contenido del servidor HTTP obtenida correctamente.
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Formato de encabezado HTTP incorrecto.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a>nx_web_http_server_create

Crea una instancia de servidor HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de servidor HTTP que se ejecuta en el contexto de su propio subproceso ThreadX. Las rutinas de devolución de llamada de aplicación *authentication_check* y *request_notify* opcionales proporcionan al software de aplicación control sobre las operaciones básicas del servidor HTTP.

Este servicio se utiliza para crear servidores HTTP de texto no cifrado y servidores HTTPS protegidos por TLS. Para habilitar HTTPS mediante TLS, consulte el servicio *nx_web_http_server_secure_configure()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **http_server_ptr** Puntero al bloque de control del servidor HTTP.
- **http_server_name** Puntero al nombre del servidor HTTP.
- **ip_ptr** Puntero a la instancia de IP creada anteriormente.
- **server_port** Puerto de escucha de TCP para la instancia de servidor.
- **media_ptr** Puntero a la instancia de medios FileX creada anteriormente.
- **stack_ptr** Puntero al área de la pila de subprocesos del servidor HTTP.
- **stack_size** Puntero al tamaño de la pila de subprocesos del servidor HTTP.
- **authentication_check** Puntero de función a la rutina de comprobación de autenticación de la aplicación. Si se especifica, se llama a esta rutina para cada solicitud de cliente HTTP. Si este parámetro es NULL, no se realizará ninguna autenticación. Este parámetro está en desuso. Llame a *nx_web_http_server_authenticate_check_set*() en su lugar.
- **request_notify** Puntero de función a la rutina de notificación de solicitud de la aplicación. Si se especifica, se llama a esta rutina antes de que se procese el servidor HTTP de la solicitud. Esto permite que se redirija el nombre del recurso o que los campos de un recurso se actualicen antes de completar la solicitud de cliente HTTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor HTTP creado correctamente.
- NX_PTR_ERROR (0x07) El puntero de servidor HTTP, dirección IP, medio, pila o grupo de paquetes no es válido.
- NX_WEB_HTTP_POOL_ERROR (0x30009) La carga de paquetes del grupo no es lo suficientemente grande como para contener una solicitud HTTP completa.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a>nx_web_http_server_delete

Elimina una instancia de servidor HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente HTTP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **http_server_ptr** Puntero al bloque de control del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor HTTP eliminado correctamente.
- NX_PTR_ERROR (0x07) Puntero de servidor HTTP no válido.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a>nx_web_http_server_get_entity_content

Recupera la ubicación y la longitud de los datos de entidad

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a>Descripción

Este servicio determina la ubicación del inicio de los datos dentro de la entidad actual de varias partes en los mensajes de cliente recibidos y la longitud de los datos que no incluyen la cadena de límite. Internamente, el servidor HTTP actualiza sus propios desplazamientos para que se pueda volver a llamar a esta función en el mismo datagrama de cliente para mensajes con varias entidades. El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.

Tenga en cuenta que NX_WEB_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio. Tenga en cuenta también que la aplicación no debe liberar el paquete al que apunta packet_pptr. Esto lo realiza internamente el servidor HTTP.

Consulte *nx_web_http_server_get_entity_header()* para obtener más información.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al servidor HTTP.
- **packet_pptr** Puntero a la ubicación del puntero de paquete. Tenga en cuenta que la aplicación no debe liberar este paquete
- **available_offset** Puntero para desplazar los datos de entidad desde el puntero antepuesto de paquete.
- **available_length** Puntero a la longitud de los datos de entidad.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Tamaño y ubicación del contenido de la entidad recuperados correctamente.
- **NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Contenido para los marcadores de varias partes internos del servidor HTTP ya encontrado.
- NX_WEB_HTTP_ERROR (0x30000) Error interno del servidor HTTP.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a>nx_web_http_server_get_entity_header

Recupera el contenido del encabezado de entidad.

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a>Descripción

Este servicio recupera el encabezado de entidad en el búfer especificado. Internamente, el servidor HTTP actualiza sus propios punteros para localizar la siguiente entidad de varias partes en un datagrama de cliente con varios encabezados de entidad. El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.

Tenga en cuenta que NX_WEB_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio. Tenga en cuenta también que la aplicación no debe liberar el paquete al que apunta packet_pptr.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al servidor HTTP.
- **packet_pptr** Puntero a la ubicación del puntero de paquete. Tenga en cuenta que la aplicación no debe liberar este paquete
- **entity_header_buffer** Puntero a la ubicación donde se va a almacenar el encabezado de entidad.
- **buffer_size** Tamaño del búfer de entrada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Encabezado de entidad recuperado correctamente.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) Campo de encabezado de identidad no encontrado.
- **NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo agotado para recibir el siguiente paquete para el mensaje de cliente con varios paquetes.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.
- NX_WEB_HTTP_ERROR (0x30000) Error de cliente HTTP interno.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
                NX_SUCCESS)
            {
                nx_packet_release(response_pkt);
            }
        }
    }
    else
    {
        /* Indicate we have not processed the response to client yet.*/
        return(NX_SUCCESS);
    }

    /* Indicate the response to client is transmitted. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a>nx_web_http_server_gmt_callback_set

Establece la devolución de llamada para obtener la fecha y hora GMT.

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Descripción

Este servicio establece la devolución de llamada para obtener la fecha y hora GMT con un servidor HTTP creado previamente. Este servicio se invoca con el servidor HTTP y crea un encabezado en las respuestas del servidor HTTP al cliente.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al servidor HTTP.
- **gmt_get** Puntero a la devolución de llamada GMT.
- **date** Puntero a la fecha de recuperación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.
- NX_PTR_ERROR (0x07) Puntero de paquete o parámetro no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a>nx_web_http_server_invalid_userpassword_notify_set

Establece la devolución de llamada para controlar la contraseña o el usuario no válidos

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a>Descripción

Este servicio establece la devolución de llamada invocada cuando se recibe un nombre de usuario y una contraseña no válidos en una solicitud GET, PUT o DELETE de cliente, ya sea mediante autenticación implícita o básica. El servidor HTTP se debe crear previamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al servidor HTTP.
- **invalid_username_password_callback** Puntero a una devolución de llamada de aprobado/usuario no válido.
- **resource** Puntero al recurso especificado por el cliente.
- **client_address** Dirección de cliente.
- **request_type** Indica el tipo de solicitud de cliente. Puede ser:
  - *NX_WEB_HTTP_SERVER_GET_REQUEST*
  - *NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*
  - *NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a>nx_web_http_server_mime_maps_additional_set

Establece asignaciones MIME adicionales para HTML

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a>Descripción

Este servicio permite al desarrollador de aplicaciones HTTP agregar tipos MIME adicionales a partir de los tipos MIME predeterminados proporcionados por el servidor Web HTTP de NetX. Consulte *nx_web_http_server_get_type()* para obtener una lista de tipos definidos.

Cuando se recibe una solicitud de cliente, por ejemplo, una solicitud GET, el servidor HTTP analiza el tipo de archivo solicitado del encabezado HTTP mediante el conjunto de asignaciones MIME adicional y, si no se encuentra ninguna coincidencia, busca una coincidencia en la asignación MIME predeterminada del servidor HTTP. Si no se encuentra ninguna coincidencia, el tipo MIME tiene como valor predeterminado “texto/sin formato”.

Si la función de notificación de solicitud se registra con el servidor HTTP, la devolución de llamada de solicitud de notificación puede llamar a *nx_web_http_server_type_get_extended()* para analizar el tipo de archivo.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero a la instancia de servidor HTTP.
- **mime_maps** Puntero a una matriz de asignaciones MIME.
- **mime_map_num** Número de asignaciones MIME en la matriz.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Asignación MIME del servidor HTTP establecida correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a>nx_web_http_server_response_packet_allocate

Asigna un paquete HTTP(S)

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta asignar un paquete para el servidor HTTP(S).

Tenga en cuenta que si **se produce un error en** una API de servidor NetX o HTTP posterior que usa este paquete como entrada, como nx_packet_data_append o **nx_web_http_server_callback_packet_send, la aplicación es responsable de liberar el paquete. **

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero al bloque de control del servidor HTTP.
- **packet_ptr** Puntero al paquete asignado.
- **wait_option** Define el tiempo de espera en tics si no hay paquetes disponibles en el grupo de paquetes. Las opciones de espera se definen de la siguiente forma:
  - **NX_NO_WAIT** (0X00000000) Si se selecciona NX_NO_WAIT, el subproceso que realiza la llamada se devuelve inmediatamente si no se puede cumplir la solicitud.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.
  - **timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Asignación correcta de paquetes.
- **NX_NO_PACKET** (0X01) No hay ningún paquete disponible.
- **NX_WAIT_ABORTED** (0x1A) Una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.
- **NX_INVALID_PARAMETERS** (0x4D) El tamaño de paquete no admite el protocolo.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a>nx_web_http_server_packet_content_find

Extrae la longitud del contenido y establece el puntero en el inicio de los datos

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Descripción

Este servicio extrae la longitud del contenido del encabezado HTTP. También actualiza el paquete proporcionado de la siguiente manera: el puntero antepuesto de paquete (inicio de la ubicación del búfer de paquetes en el que se va a escribir) se establece en el contenido HTTP (datos) que se acaba de pasar al encabezado HTTP.

Si no se encuentra el principio del contenido en el paquete actual, la función espera a que se reciba el siguiente paquete mediante la opción de espera NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Tenga en cuenta que no se debe llamar a este método antes de llamar a *nx_web_http_server_get_entity_header()* porque modifica el puntero antepuesto de paquete más allá del encabezado de entidad.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero a la instancia de servidor HTTP.
- **packet_ptr** Puntero al puntero de paquete para devolver el paquete con el puntero antepuesto actualizado.
- **CONTENT_LENGTH** Puntero al valor content_length extraído.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se encontró la longitud del contenido HTTP y el paquete se actualizó correctamente.
- **NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo agotado esperando al siguiente paquete.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a>nx_web_http_server_packet_get

Recibe el siguiente paquete HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve el siguiente paquete recibido en el socket de servidor HTTP. La opción de espera para recibir un paquete es NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Tenga en cuenta que si se ejecuta correctamente, la aplicación es responsable de liberar el paquete.

### <a name="input-parameters"></a>Parámetros de entrada

- **server_ptr** Puntero a la instancia de servidor HTTP.
- **packet_ptr** Puntero al paquete recibido.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Siguiente paquete HTTP recibido correctamente.
- **NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo agotado esperando al siguiente paquete.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a>nx_web_http_server_param_get

Obtiene el parámetro de la solicitud

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a>Descripción

Este servicio intenta recuperar el parámetro de dirección URL HTTP especificado en el paquete de solicitud proporcionado. Si el parámetro HTTP solicitado no está presente, esta rutina devuelve un estado de NX_WEB_HTTP_NOT_FOUND. Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).

### <a name="input-parameters"></a>Parámetros de entrada

- **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que la aplicación no debe liberar este paquete.
- **param_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de parámetros.
- **param_ptr** Área de destino para copiar el parámetro.
- **param_size** Devuelve la longitud total de los datos del parámetro (en bytes).
- **max_param_size** Tamaño máximo del área de destino del parámetro.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Parámetro del servidor HTTP obtenido correctamente.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) No se encontró el parámetro especificado.
- **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Parámetro de solicitud no terminado correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a>nx_web_http_server_query_get

Obtiene la consulta de la solicitud

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a>Descripción

Este servicio intenta recuperar la consulta de dirección URL HTTP especificada en el paquete de solicitud proporcionado. Si la consulta HTTP solicitada no está presente, esta rutina devuelve un estado de NX_WEB_HTTP_NOT_FOUND. Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).

### <a name="input-parameters"></a>Parámetros de entrada

- **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que la aplicación no debe liberar este paquete.
- **query_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de consultas.
- **query_ptr** Área de destino en la que se va a copiar la consulta.
- **query_size** Devuelve el tamaño de los datos de consulta (en bytes).
- **max_query_size** Tamaño máximo del destino de la consulta.

zona.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Consulta del servidor HTTP obtenida correctamente.
- **NX_WEB_HTTP_FAILED** (0x30002) Tamaño de consulta demasiado pequeño.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) No se encontró la consulta especificada.
- **NX_WEB_HTTP_NO_QUERY_PARSED** (0X30013) No hay ninguna consulta en la solicitud de cliente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a>nx_web_http_server_response_chunked_set

Establece una transferencia fragmentada para la respuesta HTTP(S)

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio utiliza codificación de transferencia fragmentada para enviar un paquete de datos de respuesta HTTP(S) personalizado creado con *nx_web_http_server_response_packet_allocate*() al cliente.

> [!NOTE]
> Si la aplicación utiliza codificación de transferencia fragmentada para enviar un paquete de datos de respuesta, debe llamar a este servicio después de llamar a *nx_web_http_client_response_packet_allocate*() y antes de llamar a *nx_web_http_server_callback_packet_send*().

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr** Puntero al bloque de control del cliente HTTP.
- **chunk_size** Tamaño de los datos de fragmentos en octetos.
- **packet_ptr** El puntero de paquete de datos de solicitud HTTP(S).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Fragmento establecido correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a>nx_web_http_server_secure_configure

Configura un servidor HTTP para usar TLS para HTTPS seguro

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a>Descripción

Este servicio configura una instancia de servidor Web HTTP de NetX creada previamente para usar TLS en las comunicaciones HTTPS seguras. Los parámetros se usan para configurar todas las sesiones TLS posibles con un estado idéntico, de modo que cada cliente HTTPS entrante experimente un comportamiento coherente. El número de sesiones TLS se controla mediante la macro NX_WEB_HTTP_SESSION_MAX.

La tabla de rutinas criptográficas (tabla de conjuntos de cifrado) se comparte entre todas las sesiones TLS, ya que solo contiene punteros de función.

Los metadatos y los búferes de reensamblado de paquetes se dividen equitativamente entre todas las sesiones TLS. Si el tamaño del búfer no es divisible por el número de sesiones, el resto no se usará.

Todas las sesiones usan el certificado de identidad que se ha pasado. Durante la operación TLS, el certificado de identidad de servidor solo se lee para que no se necesiten copias para cada sesión.

Los certificados de confianza se agregan a cada sesión de TLS en el servidor HTTPS. Se usan para la autenticación de certificados de cliente que se habilita automáticamente cuando se proporciona un espacio de certificados remoto.

La matriz de certificados y el búfer remotos se comparten de forma predeterminada entre todas las sesiones de TLS. Los certificados remotos se utilizan para la autenticación de certificados de cliente que se habilita automáticamente cuando el número de certificados remotos es distinto de cero. Debido al uso compartido del búfer, algunas sesiones pueden bloquearse durante la validación del certificado.

Para deshabilitar la autenticación de certificados de cliente, pase NX_NULL al parámetro remote_certificates y un valor de 0 para el parámetro remote_certs_num.

Los valores devueltos incluirán cualquier código de error de TLS que resulte de problemas en la configuración de las sesiones de TLS.

### <a name="input-parameters"></a>Parámetros de entrada

- **http_server_ptr** Puntero a la instancia de servidor HTTP.
- **crypto_table** Puntero a la tabla de conjuntos de cifrado de TLS.
- **metadata_buffer** Puntero al búfer de metadatos criptográficos.
- **metadata_size** Tamaño del búfer de metadatos criptográficos.
- **packet_buffer** Búfer del reensamblado de paquetes TLS.
- **packet_buffer** Tamaño del búfer de paquetes TLS: debe ser igual a (<tamaño de búfer de TLS deseado* NX_WEB_HTTP_SESSION_MAX).
- **identity_certificate** Certificado de identidad del servidor TLS: se usará para todas las sesiones HTTPS del servidor.
- **trusted_certificates** Puntero a la matriz de objetos NX_SECURE_X509_CERT, que se usa para validar los certificados de cliente entrantes si se habilita la autenticación de certificados de cliente pasando un valor distinto de cero para el parámetro *remote_certs_num*.
- **trusted_certs_num** Número de certificados de confianza en la matriz de *trusted_certificates*.
- **remote_certificates** Puntero a la matriz de objetos NX_SECURE_X509_CERT, que se usa para los certificados de cliente entrantes.
- **remote_certs_num** Número de certificados remotos. Debe ser el número máximo de certificados esperados de los clientes. La autenticación de certificados de cliente se habilita automáticamente cuando no es cero.
- **remote_certificate_buffer** Búfer que contiene los certificados remotos entrantes de los clientes si está habilitada la autenticación de certificados de cliente. remote_cert_buffer_size Tamaño del búfer de certificados remotos. Debe ser igual a (<tamaño máximo de certificado esperado \* remote_certs_num).


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.
- **NX_NOT_CONNECTED**: (0x38) El socket TCP subyacente ya no está conectado.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**: (0x102) Un tipo de mensaje TLS recibido es incorrecto.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER**: (0x106) No se admite el cifrado proporcionado por el host remoto.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Error al procesar el mensaje durante el protocolo de enlace de TLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Un mensaje entrante no pudo realizar una comprobación hash de MAC.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Error al enviar un socket TCP subyacente.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Un mensaje entrante tenía un campo de longitud no válido.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0X10B) Un mensaje ChangeCipherSpec entrante era incorrecto.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Un certificado TLS entrante no se puede usar para identificar el servidor DTLS remoto.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) No se admite el cifrado de clave pública proporcionado por el host remoto.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS**: (0x10E) El host remoto ha indicado que no hay conjuntos de cifrado admitidos por la pila de TLS de NetX Secure.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION**: (0x10F) Un mensaje TLS recibido tenía una versión de TLS desconocida en el encabezado.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION**: (0x110) Un mensaje TLS recibido tenía una versión de TLS conocida pero no admitida en el encabezado.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**: (0x111) Error en la asignación interna del paquete TLS.
- **NX_SECURE_TLS_INVALID_CERTIFICATE**: (0x112) El host remoto proporcionó un certificado no válido.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) El host remoto envió una alerta que indica un error y finaliza la sesión de TLS.
- **NX_PTR_ERROR** (0x07) Se ha intentado usar un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a>nx_web_http_server_start

Inicia el servidor HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia una instancia de servidor HTTP o HTTPS creada anteriormente.

Los servidores HTTPS comparten la misma API que los HTTP. Para habilitar HTTPS mediante TLS, consulte el servicio *nx_web_http_server_secure_configure()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **http_server_ptr** Puntero a la instancia de servidor HTTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor HTTP iniciado correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a>nx_web_http_server_stop

Detiene el servidor HTTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene la instancia de servidor HTTP creada anteriormente. Se debe llamar a esta rutina antes de eliminar una instancia del servidor HTTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **http_server_ptr** Puntero a la instancia de servidor HTTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor HTTP detenido correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a>nx_web_http_server_type_get

Extrae el tipo de archivo de la solicitud HTTP del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a>Descripción

> [!NOTE]
> Este servicio está en desuso. Se recomienda a los usuarios que usen el servicio *nx_web_http_server_type_get_extended()* .

Este servicio extrae el tipo de solicitud HTTP en el búfer *http_type_string* y su longitud en *string_size* desde el *nombre* del búfer de entrada, normalmente la dirección URL. Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo “texto/sin formato”. En caso contrario, compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias. Los mapas MIME predeterminados del servidor Web HTTP de NetX son:

- texto html/html
- texto htm/html
- texto txt/plain
- imagen gif/gif
- imagen jpg/jpeg
- imagen ico/x-icon

Si se proporciona, también buscará un conjunto definido por el usuario de asignaciones MIME adicionales. Consulte *nx_web_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.

### <a name="input-parameters"></a>Parámetros de entrada

- **http_server_ptr** Puntero a la instancia de servidor HTTP.
- **name** Puntero al búfer para buscar.
- **http_type_string** Puntero a la cadena de tipo HTML extraída.
- **string_size** Puntero para devolver la longitud de cadena de tipo HTML extraída.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Tipo extraído correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Se devuelve el valor predeterminado “texto/sin formato”.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a>nx_web_http_server_type_get_extended

Extrae el tipo de archivo de la solicitud HTTP del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a>Descripción

Este servicio extrae el tipo de solicitud HTTP en el búfer *http_type_string* y su longitud en *string_size* desde el *nombre* del búfer de entrada, normalmente la dirección URL. Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo “texto/sin formato”. En caso contrario, compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias. Los mapas MIME predeterminados del servidor Web HTTP de NetX son:

- texto html/html
- texto htm/html
- texto txt/plain
- imagen gif/gif
- imagen jpg/jpeg
- imagen ico/x-icon

Si se proporciona, también buscará un conjunto definido por el usuario de asignaciones MIME adicionales. Consulte *nx_web_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.

Este servicio reemplaza a *nx_web_http_server_type_get*(). Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.

### <a name="input-parameters"></a>Parámetros de entrada

- **http_server_ptr** Puntero a la instancia de servidor HTTP.
- **name** Puntero al búfer para buscar.
- **name_length** Longitud del nombre.
- **http_type_string** Puntero a la cadena de tipo HTML extraída.
- **http_type_string_max_size** Tamaño del búfer de http_type_string.
- **string_size** Puntero para devolver la longitud de cadena de tipo HTML

extraída.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Tipo extraído correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Se devuelve el valor predeterminado “texto/sin formato”.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a>nx_web_http_server_digest_authenticate_notify_set

Establece la función de devolución de llamada de autenticación implícita

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a>Descripción

Este servicio establece la devolución de llamada invocada cuando se realiza la autenticación implícita.

### <a name="input-parameters"></a>Parámetros de entrada

- **http_server_ptr** Puntero a la instancia de servidor HTTP.
- **digest_authenticate_callback** Puntero a la devolución de llamada de autenticación implícita.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_NOT_SUPPORTED (0x4B) Autenticación implícita no habilitada.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a>nx_web_http_server_authenticate_check_set

Establece la función de devolución de llamada de autenticación implícita

### <a name="prototype"></a>Prototipo

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a>Descripción

Este servicio establece la devolución de llamada invocada cuando se realiza la comprobación de autenticación.

### <a name="input-parameters"></a>Parámetros de entrada

- **http_server_ptr** Puntero a la instancia de servidor HTTP.
- **authenticate_check_externded** Puntero para autenticar la devolución de llamada de comprobación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
