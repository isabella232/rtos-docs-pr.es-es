---
title: 'Capítulo 3: Descripción de los servicios HTTP de NetX Duo para Azure RTOS'
description: Este capítulo contiene una descripción de todos los servicios HTTP de NetX Duo para Azure RTOS (enumerados a continuación) en orden alfabético, excepto el equivalente a "NetX" (solo IPv4) del mismo servicio, que se emparejan juntos.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 09add7bb20a8e104ba41583c0dbf4d574b8e6c9e6b3a3deed71d8fa8c8942ce2
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796487"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a>Capítulo 3: Descripción de los servicios HTTP de NetX Duo para Azure RTOS

Este capítulo contiene una descripción de todos los servicios HTTP de NetX Duo para Azure RTOS (enumerados a continuación) en orden alfabético, excepto el equivalente a "NetX" (solo IPv4) del mismo servicio, que se emparejan juntos.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en NEGRITA no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

**Servicios de cliente HTTP:**

- **nx_http_client_create** *Crear una instancia de cliente HTTP*
- **nx_http_client_delete** *Eliminar una instancia de cliente HTTP*
- **nx_http_client_get_start** *Iniciar una solicitud HTTP GET (solo IPv4)*
- **nx_http_client_get_start_extended** *Iniciar una solicitud HTTP GET (solo IPv4)*
- **nxd_http_client_get_start** *Iniciar una solicitud HTTP GET (IPv4 o IPv6)*
- **nxd_http_client_get_start_extended** *Iniciar una solicitud HTTP GET (IPv4 o IPv6)*
- **nx_http_client_get_packet** *Obtener el siguiente paquete de datos de recursos*
- **nx_http_client_put_start** *Iniciar una solicitud HTTP PUT (solo IPv4)*
- **nx_http_client_put_start_extended** *Iniciar una solicitud HTTP PUT (solo IPv4)*
- **nxd_http_client_put_start** *Iniciar una solicitud HTTP PUT (IPv4 o IPv6)*
- **nxd_http_client_put_start_extended** *Iniciar una solicitud HTTP PUT (IPv4 o IPv6)*
- **nx_http_client_put_packet** *Enviar el siguiente paquete de datos de recursos*
- **nx_http_client_set_connect_port** *Cambiar el puerto para conectarse al servidor HTTP*

**Servicios de servidor HTTP:**

- **nx_http_server_cache_info_callback_set** *Establecer la devolución de llamada para recuperar la fecha de vencimiento y última modificación de la dirección URL especificada*
- **nx_http_server_callback_data_send** *Enviar datos HTTP desde la función de devolución de llamada*
- **nx_http_server_callback_generate_response_header** *Crear un encabezado de respuesta en funciones de devolución de llamada*
- **nx_http_server_callback_generate_response_header_extended** *Crear un encabezado de respuesta en funciones de devolución de llamada*
- **nx_http_server_callback_packet_send** *Enviar un paquete HTTP desde una devolución de llamada HTTP*
- **nx_http_server_callback_response_send** *Enviar una respuesta desde la función de devolución de llamada*
- **nx_http_server_callback_response_send_extended** *Enviar una respuesta desde la función de devolución de llamada*
- **nx_http_server_content_get** *Obtener contenido de la solicitud*
- **nx_http_server_content_get_extended** *Obtener contenido de la solicitud; admite solicitudes vacías (longitud de contenido cero)*
- **nx_http_server_content_length_get** *Obtener longitud de contenido de la solicitud*
- **nx_http_server_content_length_get_extended** *Obtener longitud de contenido de la solicitud; admite solicitudes vacías (longitud de contenido cero)*
- **nx_http_server_create** *Crear una instancia de servidor HTTP*
- **nx_http_server_delete** Eliminar una instancia de servidor HTTP
- **nx_http_server_get_entity_content** *Devolver tamaño y ubicación del contenido de la entidad en la dirección URL*
- **nx_http_server_get_entity_header** *Extraer encabezado de entidad URL en el búfer especificado*
- **nx_http_server_gmt_callback_set** *Establecer devolución de llamada para recuperar la fecha y hora GMT*
- **nx_http_server_invalid_userpassword_notify_set** *Establecer devolución de llamada para cuando se recibe un nombre de usuario y una contraseña no válidos en una solicitud de cliente*
- **nx_http_server_mime_maps_additional_set** *Definir asignaciones MIME adicionales para HTML*
- **nx_http_server_packet_content_find** *Extraer longitud de contenido en el encabezado HTTP y establecer puntero en el inicio de los datos de contenido*
- **nx_http_server_packet_get** *Recibir paquete de cliente directamente*
- **nx_http_server_param_get** *Obtener parámetro de la solicitud*
- **nx_http_server_query_get** *Obtener consulta de la solicitud*
- **nx_http_server_start** *Iniciar el servidor HTTP*
- **nx_http_server_stop** *Detener el servidor HTTP*
- **nx_http_server_type_get (en desuso)** *Extraer tipo HTTP, por ejemplo, texto/sin formato*
- **nx_http_server_type_get_extended** *Extraer tipo HTTP, por ejemplo, texto/sin formato*
- **nx_http_server_digest_authenticate_notify_set** *Establecer función de devolución de llamada de autenticación implícita*
- **nx_http_server_authentication_check_set** *Establecer función de devolución de llamada de comprobación de autenticación*

## <a name="nx_http_client_create"></a>nx_http_client_create

Crear una instancia de cliente de PPPoE

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente HTTP en la instancia de IP especificada.

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **client_name** Nombre de la instancia de cliente HTTP.
 - **ip_ptr** Puntero a la instancia de IP.
 - **pool_ptr** Puntero al grupo de paquetes predeterminado. Tenga en cuenta que los paquetes de este grupo deben tener una carga útil lo suficientemente grande como para controlar el encabezado de respuesta completo. Se define mediante NX_HTTP_CLIENT_MIN_PACKET_SIZE en *nx_http. h*.
 - **window_size** Tamaño de la ventana de recepción del socket TCP del cliente.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Se creó correctamente el cliente HTTP.
 - NX_PTR_ERROR (0x07) Puntero HTTP, ip_ptr o de grupo de paquetes no válido
 - NX_HTTP_POOL_ERROR (0xE9) Tamaño de carga no válido en el grupo de paquetes

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a>nx_http_client_delete

Eliminar una instancia de cliente HTTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente HTTP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Se eliminó correctamente el cliente HTTP.
 - NX_PTR_ERROR (0x07) Puntero HTTP no válido
 - NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a>nx_http_client_get_start

Iniciar una solicitud HTTP GET mediante IPv4

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta crear y enviar una solicitud GET con el recurso especificado por el puntero "resource" en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.

> [!NOTE]
> La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes GET de referencia.

Este servicio solo funciona a través de la red IPv4. En el caso de las aplicaciones que necesitan conectarse a la red IPv6, se debe usar *nxd_http_client_get_start_extended()* .

Este servicio está en desuso. Se recomienda a los desarrolladores migrar a *nx_http_client_get_start_extended()* o *nxd_http_client_get_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **ip_address** Dirección IP del servidor HTTP.
 - **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
 - **input_ptr** Puntero a datos adicionales para la solicitud GET. Esto es opcional. Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.
 - **input_size** Número de bytes en la entrada adicional opcional a la que apunta ```input_ptr```.
 - **username** Puntero al nombre de usuario opcional para la autenticación.
 - **password** Puntero a la contraseña opcional para la autenticación.
 - **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:

    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Cliente HTTP enviado correctamente. Mensaje de inicio GET.
 - **NX_HTTP_ERROR** (0xE0) Error interno del cliente HTTP.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.
 - **NX_HTTP_FAILED** (0xE2) Error de cliente HTTP al comunicarse con el servidor HTTP.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a>nx_http_client_get_start_extended

Iniciar una solicitud HTTP GET mediante IPv4

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta crear y enviar una solicitud GET con el recurso especificado por el puntero "resource" en la instancia de cliente HTTP creada anteriormente. Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.

> [!NOTE]
> La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes GET de referencia.

Este servicio solo funciona a través de la red IPv4. En el caso de las aplicaciones que necesitan conectarse a la red IPv6, se debe usar *nxd_http_client_get_start_extended()* .

Este servicio reemplaza a *nx_http_client_get_start()* . Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **ip_address** Dirección IP del servidor HTTP.
 - **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
 - **resource_length** Longitud de la cadena de dirección URL para el recurso solicitado.
 - **input_ptr** Puntero a datos adicionales para la solicitud GET. Esto es opcional. Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.
 - **input_size** Número de bytes en la entrada adicional opcional a la que apunta ```input_ptr```.
 - **username** Puntero al nombre de usuario opcional para la autenticación.
 - **username_length** Longitud de cadena del nombre de usuario para la autenticación.
 - **password** Puntero a la contraseña opcional para la autenticación.
 - **password_length** Longitud de la contraseña opcional para la autenticación.
 - **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Cliente HTTP enviado correctamente. Mensaje de inicio GET.
 - **NX_HTTP_ERROR** (0xE0) Error interno del cliente HTTP.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.
 - **NX_HTTP_FAILED** (0xE2) Error de cliente HTTP al comunicarse con el servidor HTTP.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a>nxd_http_client_get_start

Enviar una solicitud HTTP GET (IPv4 o IPv6)

### <a name="prototype"></a>Prototipo

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta crear y enviar una solicitud GET con el recurso especificado por el puntero "resource" en la instancia de cliente HTTP creada anteriormente. Se puede usar para conectarse a una red IPv4 o IPv6. Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.

> [!NOTE]
>La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes GET de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores migrar a *nxd_http_client_get_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **Server_ip** Dirección IP del servidor HTTP.
 - **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
 - **input_ptr** Puntero a datos adicionales para la solicitud GET. Esto es opcional. Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.
 - **input_size** Número de bytes en la entrada adicional opcional a la que apunta ```input_ptr```.
 - **username** Puntero al nombre de usuario opcional para la autenticación.
 - **username_length** Longitud de cadena del nombre de usuario para la autenticación.
 - **password** Puntero a la contraseña opcional para la autenticación.
 - **password_length** Longitud de la contraseña opcional para la autenticación.
 - **wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Solicitud GET enviada correctamente
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) La contraseña supera el tamaño del búfer.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.
 - **NX_HTTP_FAILED** (0xE2) Parámetros de paquete no válidos.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a>nxd_http_client_get_start_extended

Enviar una solicitud HTTP GET (IPv4 o IPv6)

### <a name="prototype"></a>Prototipo

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta crear y enviar una solicitud GET con el recurso especificado por el puntero "resource" en la instancia de cliente HTTP creada anteriormente. Se puede usar para conectarse a una red IPv4 o IPv6. Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.

> [!NOTE]
> La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes GET de referencia.

Este servicio reemplaza a *nxd_http_client_get_start()* . Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **Server_ip** Dirección IP del servidor HTTP.
 - **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
 - **resource_length** Longitud de la cadena de dirección URL para el recurso solicitado.
 - **input_ptr** Puntero a datos adicionales para la solicitud GET. Esto es opcional. Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.
 - **input_size** Número de bytes en la entrada adicional opcional a la que apunta ```input_ptr```.
 - **username** Puntero al nombre de usuario opcional para la autenticación.
 - **username_length** Longitud de cadena del nombre de usuario para la autenticación.
 - **password** Puntero a la contraseña opcional para la autenticación.
 - **password_length** Longitud de la contraseña opcional para la autenticación.
 - **wait_option** Define cuánto tiempo esperará el servicio internamente para procesar el inicio del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Solicitud GET enviada correctamente
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) La contraseña supera el tamaño del búfer.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.
 - **NX_HTTP_FAILED** (0xE2) Parámetros de paquete no válidos.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a>nx_http_client_get_packet

Obtener el siguiente paquete de datos de recursos

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a>Descripción

Este servicio recupera el siguiente paquete de contenido del recurso solicitado por la llamada a *nx_http_client_get_start* anterior. Deben realizarse llamadas sucesivas a esta rutina hasta que se reciba el estado de devolución de NX_HTTP_GET_DONE.

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **packet_ptr** Destino del puntero de paquete que contiene el contenido parcial del recurso.
 - **wait_option** Define cuánto tiempo esperará el servicio a que se obtenga el paquete del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Se ha obtenido correctamente el paquete del cliente HTTP.
 - **NX_HTTP_GET_DONE** (0xEC) Se ha realizado la obtención del paquete del cliente HTTP.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está en modo de obtención.
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) Longitud de paquete no válida.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a>nx_http_client_put_start

Iniciar una solicitud HTTP PUT a través de IPv4

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP proporcionada. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet ()* para enviar realmente el contenido del recurso al servidor HTTP.

> [!NOTE]
> La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o puede hacer referencia a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores migrar a *nx_web_http_client_put_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **ip_address** Dirección IP del servidor HTTP.
 - **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
 - **username** Puntero al nombre de usuario opcional para la autenticación.
 - **password** Puntero a la contraseña opcional para la autenticación.
 - **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet* debe ser igual a este valor.
 - **wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) El nombre de usuario es demasiado grande para el búfer.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a>nx_http_client_put_start_extended

Iniciar una solicitud HTTP PUT a través de IPv4

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP proporcionada. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet ()* para enviar realmente el contenido del recurso al servidor HTTP.

> [!NOTE]
> La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o puede hacer referencia a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Este servicio reemplaza a *nx_http_client_put_start()* . Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **ip_address** Dirección IP del servidor HTTP.
 - **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
 - **resource_length** Longitud de la cadena de dirección URL para el recurso que se va a enviar al servidor.
 - **username** Puntero al nombre de usuario opcional para la autenticación.
 - **username_length** Longitud de cadena del nombre de usuario para la autenticación.
 - **password** Puntero a la contraseña opcional para la autenticación.
 - **password_length** Longitud de la contraseña opcional para la autenticación.
 - **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet* debe ser igual a este valor.
 - **wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) El nombre de usuario es demasiado grande para el búfer.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a>nxd_http_client_put_start

Iniciar una solicitud HTTP PUT (IPv4 o IPv6)

### <a name="prototype"></a>Prototipo

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta colocar (enviar) el recurso especificado en el servidor HTTP en la dirección IP proporcionada a través de IPv6. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet ()* para enviar realmente el contenido del recurso al servidor HTTP.

> [!NOTE]
> La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o puede hacer referencia a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Este servicio está en desuso. Se recomienda a los desarrolladores migrar a *nx_web_http_client_put_start_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **server_IP** Dirección IP del servidor HTTP.
 - **resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.
 - **username** Puntero al nombre de usuario opcional para la autenticación.
 - **password** Puntero a la contraseña opcional para la autenticación.
 - **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet* debe ser igual a este valor.
 - **wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Solicitud PUT del cliente HTTP enviada correctamente.
 - **NX_HTTP_ERROR** (0xE0) Error interno del cliente HTTP.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.
 - **NX_HTTP_FAILED** (0xE2) Error de cliente HTTP al comunicarse con el servidor HTTP.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a>nxd_http_client_put_start_extended

Iniciar una solicitud HTTP PUT (IPv4 o IPv6)

### <a name="prototype"></a>Prototipo

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta colocar (enviar) el recurso especificado en el servidor HTTP en la dirección IP proporcionada a través de IPv6. Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet ()* para enviar realmente el contenido del recurso al servidor HTTP.

> [!NOTE]
> La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o puede hacer referencia a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes PUT de referencia.

Este servicio reemplaza a *nxd_http_client_put_start()* . Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **ip_address** Dirección IP del servidor HTTP.
 - **resource** Puntero a la cadena de dirección URL para el recurso solicitado.
 - **resource_length** Longitud de la cadena de dirección URL para el recurso que se va a enviar al servidor.
 - **username** Puntero al nombre de usuario opcional para la autenticación.
 - **username_length** Longitud de cadena del nombre de usuario para la autenticación.
 - **password** Puntero a la contraseña opcional para la autenticación.
 - **password_length** Longitud de la contraseña opcional para la autenticación.
 - **total_bytes** Bytes totales del recurso que se está enviando. Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet* debe ser igual a este valor.
 - **wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Solicitud PUT del cliente HTTP enviada correctamente.
 - **NX_HTTP_ERROR** (0xE0) Error interno del cliente HTTP.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.
 - NX_HTTP_FAILED (0xE2) Error del cliente HTTP al comunicarse con el servidor HTTP.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a>nx_http_client_put_packet

Enviar el siguiente paquete de datos de recursos

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta enviar el siguiente paquete de contenido de recursos al servidor HTTP.

> [!NOTE]
> Se debe llamar a esta rutina repetidamente hasta que la longitud combinada de los paquetes enviados sea igual al valor de "total_bytes" especificado en la llamada a *nx_http_client_put_start* anterior.

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **packet_ptr** Puntero al siguiente contenido del recurso que se va a enviar al servidor HTTP.
 - **WAIT_OPTION** Define cuánto tiempo esperará el servicio internamente para procesar el paquete PUT del cliente HTTP. Las opciones de espera se definen de la siguiente forma:
    - **time out value** (de 0x00000001 a 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.

    Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Paquete de cliente HTTP enviado correctamente.
 - **NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.
 - **NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Código de error del servidor recibido.
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) Longitud de paquete no válida.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos.
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) El servidor responde antes de que finalice PUT.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_INVALID_PACKET (0x12) El paquete es demasiado pequeño para el encabezado TCP.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a>nx_http_client_set_connect_port

Establecer el puerto de conexión al servidor

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a>Descripción

Este servicio cambia el puerto de conexión al conectarse al servidor HTTP en el puerto especificado en tiempo de ejecución. De lo contrario, el puerto de conexión tiene como valor predeterminado 80. Se debe llamar a este método antes de *nx_http_client_get_start()* y *nx_http_client_put_start()* , por ejemplo, cuando el cliente HTTP conecta con el servidor.

### <a name="input-parameters"></a>Parámetros de entrada

 - **client_ptr** Puntero al bloque de control del cliente HTTP.
 - **port** Puerto para la conexión al servidor.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Puerto cambiado correctamente.
 - NX_INVALID_PORT (0x46) El puerto supera el valor máximo (0xFFFF) o es cero.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, inicialización

### <a name="example"></a>Ejemplo

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a>nx_http_server_cache_info_callback_set

Establece la devolución de llamada para recuperar la antigüedad máxima y la fecha de la dirección URL

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
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
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización

### <a name="example"></a>Ejemplo

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a>nx_http_server_callback_data_send

Enviar datos desde la función de devolución de llamada

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a>Descripción

Este servicio envía los datos del paquete proporcionado desde la rutina de devolución de llamada de la aplicación. Normalmente se usa para enviar datos dinámicos asociados a solicitudes GET/POST.

> [!NOTE]
> Si se usa esta función, la rutina de devolución de llamada es responsable de enviar la respuesta completa en el formato correcto. Además, la rutina de devolución de llamada debe devolver el estado de NX_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al bloque de control del servidor HTTP.
 - **data_ptr** Puntero a los datos que se van a enviar.
 - **data_length** Número de bytes que se van a enviar.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a>nx_http_server_callback_generate_response_header

Crear un encabezado de respuesta en una función de devolución de llamada

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Descripción

Este servicio llama a la función interna *_nx_http_server_generate_response_header* cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE del cliente. Su uso está previsto en funciones de devolución de llamada de servidor HTTP cuando la aplicación de servidor HTTP está diseñando su respuesta al cliente.

Este servicio está en desuso. Se recomienda a los desarrolladores migrar a *nxd_http_server_callback_generate_response_header_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al bloque de control del servidor HTTP.
 - **packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.
 - **status_code** Indica el estado del recurso. Ejemplos:
    - **NX_HTTP_STATUS_OK**
    - **NX_HTTP_STATUS_MODIFIED**
    - **NX_HTTP_STATUS_INTERNAL_ERROR**
 - **content_length** Tamaño del contenido en bytes.
 - **content_type** Tipo de HTTP, por ejemplo, "texto/sin formato".
 - **additional_header** Puntero a texto de encabezado adicional.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Encabezado creado correctamente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a>nx_http_server_callback_generate_response_header_extended

Crear un encabezado de respuesta en una función de devolución de llamada

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_callback_generate_response_header_extended(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT status_code_length,
                        UINT content_length,
                        CHAR *content_type, UINT content_type_length,
                        CHAR *additional_header,
                        UINT additional_header_length);
```

### <a name="description"></a>Descripción

Este servicio llama a la función interna *_nx_http_server_generate_response_header* cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE del cliente. Su uso está previsto en funciones de devolución de llamada de servidor HTTP cuando la aplicación de servidor HTTP está diseñando su respuesta al cliente.

Este servicio reemplaza a *nx_http_server_callback_generate_response_header()* . Esta versión proporciona información de longitud adicional a la función de devolución de llamada.

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al bloque de control del servidor HTTP.
 - **packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.
 - **status_code** Indica el estado del recurso. Ejemplos:
    - **NX_HTTP_STATUS_OK**
    - **NX_HTTP_STATUS_MODIFIED**
    - **NX_HTTP_STATUS_INTERNAL_ERROR**
 - **status_code** Longitud del código de estado.
 - **content_length** Tamaño del contenido en bytes.
 - **content_type** Tipo de HTTP, por ejemplo, "texto/sin formato".
 - **content_type_length** Longitud del tipo HTTP.
 - **additional_header** Puntero a texto de encabezado adicional.
 - **additional_header_length** Longitud del texto de encabezado adicional.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Encabezado creado correctamente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header_extended(
                             http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
              sizeof(NX_HTTP_STATUS_OK) - 1, length,
              temp_string, string_length, NX_NULL, 0);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_packet_send"></a>nx_http_server_callback_packet_send

Enviar un paquete HTTP desde la función de devolución de llamada

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía una respuesta completa del servidor HTTP desde una devolución de llamada HTTP. El servidor HTTP enviará el paquete con NX_HTTP_SERVER_TIMEOUT_SEND. El encabezado y los datos HTTP deben anexarse al paquete. Si el estado devuelto indica un error, la aplicación HTTP debe liberar el paquete.

La devolución de llamada debe devolver NX_HTTP_CALLBACK_COMPLETED.

Consulte *nx_http_server_callback_generate_response_header()* para ver un ejemplo más detallado.

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al bloque de control del servidor HTTP.
 - **packet_ptr** Puntero al paquete que se va a enviar.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Paquete del servidor enviado correctamente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a>nx_http_server_callback_response_send

Enviar una respuesta desde la función de devolución de llamada

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a>Descripción

Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación. Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST.

> [!NOTE]
> Si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_HTTP_CALLBACK_COMPLETED.

Este servicio está en desuso. Se recomienda a los desarrolladores migrar a *nxd_http_server_callback_response_send_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al bloque de control del servidor HTTP.
 - **header** Puntero a la cadena de encabezado de respuesta.
 - **information** Puntero a la cadena de información.
 - **additional_info** Puntero a la cadena de información adicional.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send(server_ptr,
                      "HTTP/1.0 404 ",
                      "NetX HTTP Server unable to find  
                       file: ", resource);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a>nx_http_server_callback_response_send_extended

Enviar una respuesta desde la función de devolución de llamada

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a>Descripción

Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación. Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST.

> [!NOTE]
> Si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_HTTP_CALLBACK_COMPLETED.

Este servicio reemplaza a *nx_http_server_callback_response_send()* . Esta versión toma información de longitud adicional como argumentos.

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al bloque de control del servidor HTTP.
 - **header** Puntero a la cadena de encabezado de respuesta.
 - **header_length** Longitud de la cadena de encabezado de respuesta.
 - **information** Puntero a la cadena de información.
 - **information_length** Longitud de la cadena de información.
 - **additional_info** Puntero a la cadena de información adicional.
 - **additional_info_length** Longitud de la cadena de información adicional.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a>nx_http_server_content_get

Obtener contenido de la solicitud

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a>Descripción

Este servicio intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST o PUT. Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create*).

Este servicio está en desuso. Se recomienda a los desarrolladores migrar a *nx_http_server_content_get_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al bloque de control del servidor HTTP.
 - **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.
 - **byte_offset** Número de bytes que se van a desplazar en el área de contenido.
 - **destination_ptr** Puntero al área de destino para el contenido.
 - **destination_size** Número máximo de bytes disponibles en el área de destino.
 - **actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.
 - **NX_HTTP_ERROR** (0xE0) Error interno del servidor HTTP.
 - **NX_HTTP_DATA_END** (0xE7) Fin del contenido de la solicitud.
 - **NX_WEB_HTTP_TIMEOUT** (0xE1) Tiempo de espera del servidor HTTP para obtener el siguiente paquete de contenido.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a>nx_http_server_content_get_extended

Obtener contenido de la solicitud (admite la longitud de contenido cero)

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a>Descripción

Este servicio es casi idéntico a *nx_http_server_content_get();* intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST O PUT. Sin embargo, administra las solicitudes con una longitud de contenido de valor cero ("solicitud vacía") como solicitud válida. Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).

Este servicio reemplaza a *nx_http_server_content_get()* . Esta versión requiere que el autor de la llamada proporcione información de longitud adicional.

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al bloque de control del servidor HTTP.
 - **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.
 - **byte_offset** Número de bytes que se van a desplazar en el área de contenido.
 - **destination_ptr** Puntero al área de destino para el contenido.
 - **destination_size** Número máximo de bytes disponibles en el área de destino.
 - **actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.
 - **NX_HTTP_ERROR** (0xE0) Error interno del servidor HTTP.
 - **NX_HTTP_DATA_END** (0xE7) Fin del contenido de la solicitud.
 - **NX_WEB_HTTP_TIMEOUT** (0xE1) Tiempo de espera del servidor HTTP para obtener el siguiente paquete.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a>nx_http_server_content_length_get

Obtener la longitud del contenido de la solicitud

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio intenta recuperar la longitud del contenido HTTP en el paquete proporcionado. Si no hay contenido HTTP, esta rutina devuelve un valor de cero. Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).

Este servicio está en desuso. Se recomienda a los desarrolladores migrar a *nx_http_server_content_length_get_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.

### <a name="return-values"></a>Valores devueltos

 - **content length** Si hay error, se devuelve un valor de cero.  

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a>nx_http_server_content_length_get_extended

Obtener la longitud del contenido de la solicitud (admite la longitud de contenido de valor cero)

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a>Descripción

Este servicio es similar a *nx_http_server_content_length_get;* intenta recuperar la longitud del contenido HTTP en el paquete proporcionado. Sin embargo, el valor devuelto indica el estado de finalización correcta y el valor de longitud real se devuelve en el puntero de ```content_length```. Si no hay contenido HTTP/longitud de contenido = 0, esta rutina sigue devolviendo un estado de finalización correcta y el puntero de entrada content_length apunta a una longitud válida (cero). Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create*).

Este servicio reemplaza a *nx_http_server_content_length_get()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.
 - **CONTENT_LENGTH** Puntero al valor recuperado del campo de longitud de contenido.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Formato de encabezado HTTP incorrecto
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a>nx_http_server_create

Crear una instancia de servidor HTTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
      CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
      VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, CHAR **name,
            CHAR **password, CHAR **realm),
      UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de servidor HTTP que se ejecuta en el contexto de su propio subproceso ThreadX. Las rutinas de devolución de llamada de aplicación opcionales *authentication_check* y request_notify proporcionan al software de aplicación control sobre las operaciones básicas del servidor HTTP.

### <a name="input-parameters"></a>Parámetros de entrada

 - **http_server_ptr** Puntero al bloque de control del servidor HTTP.
 - **http_server_name** Puntero al nombre del servidor HTTP.
 - **ip_ptr** Puntero a la instancia de IP creada anteriormente.
 - **media_ptr** Puntero a la instancia de medios FileX creada anteriormente.
 - **stack_ptr** Puntero al área de la pila de subprocesos del servidor HTTP.
 - **stack_size** Puntero al tamaño de la pila de subprocesos del servidor HTTP.
 - **authentication_check** Puntero de función a la rutina de comprobación de autenticación de la aplicación. Si se especifica, se llama a esta rutina para cada solicitud de cliente HTTP. Si este parámetro es NULL, no se realizará ninguna autenticación.
 - **request_notify** Puntero de función a la rutina de notificación de solicitud de la aplicación. Si se especifica, se llama a esta rutina antes de que se procese el servidor HTTP de la solicitud. Esto permite que se redirija el nombre del recurso o que los campos de un recurso se actualicen antes de completar la solicitud de cliente HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS**: (0x00) Servidor HTTP creado correctamente.
 - NX_PTR_ERROR (0x07) El puntero de servidor HTTP, dirección IP, medio, pila o grupo de paquetes no es válido.
 - NX_HTTP_POOL_ERROR (0xE9) La carga de paquetes del grupo no es lo suficientemente grande como para contener una solicitud HTTP completa.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a>nx_http_server_delete

Eliminar una instancia de servidor HTTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
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

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a>nx_http_server_get_entity_content

Recuperar la ubicación y la longitud de los datos de entidad

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a>Descripción

Este servicio determina la ubicación del inicio de los datos dentro de la entidad actual de varias partes en los mensajes de cliente recibidos y la longitud de los datos que no incluyen la cadena de límite. Internamente, el servidor HTTP actualiza sus propios desplazamientos para que se pueda volver a llamar a esta función en el mismo datagrama de cliente para mensajes con varias entidades. El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.

> [!NOTE]
> NX_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio.

Para más información, consulte [*nx_web_http_server_get_entity_header*](#nx_http_server_get_entity_header).

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al servidor HTTP.
 - **packet_pptr** Puntero a la ubicación del puntero de paquete. Tenga en cuenta que la aplicación no debe liberar este paquete.
 - **available_offset** Puntero para desplazar los datos de entidad desde el puntero antepuesto de paquete.
 - **available_length** Puntero a la longitud de los datos de entidad.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Tamaño y ubicación del contenido de la entidad recuperados correctamente.
 - **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Ya se encontró el contenido interno de los marcadores de varias partes del servidor HTTP.
 - NX_HTTP_ERROR (0xE0) Error de HTTP interno.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a>nx_http_server_get_entity_header

Recuperar el contenido del encabezado de entidad

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a>Descripción

Este servicio recupera el encabezado de entidad en el búfer especificado. Internamente, el servidor HTTP actualiza sus propios punteros para localizar la siguiente entidad de varias partes en un datagrama de cliente con varios encabezados de entidad. El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.

> [!NOTE]
> NX_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio.

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al servidor HTTP.
 - **packet_pptr** Puntero a la ubicación del puntero de paquete. Tenga en cuenta que la aplicación no debe liberar este paquete.
 - **entity_header_buffer** Puntero a la ubicación donde se va a almacenar el encabezado de entidad.
 - **buffer_size** Tamaño del búfer de entrada.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Encabezado de entidad recuperado correctamente.
 - **NX_HTTP_NOT_FOUND** **(0xE6)** No se encontró el campo de encabezado de entidad.
 - **NX_HTTP_TIMEOUT** **(0xE1)** Se agotó el tiempo para recibir el siguiente paquete del mensaje de cliente de varios paquetes.
 - NX_HTTP_ERROR (0xE0) Error de HTTP interno.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

        /* Process multipart data. */
        if(request_type == NX_HTTP_SERVER_POST_REQUEST)
        {

       /* Get the content header. */
       while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                         sizeof(buffer)) == NX_SUCCESS)
   {

      /* Header obtained successfully. Get the content data location. */
      while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                              &length) == NX_SUCCESS)
      {
           /* Write content data to buffer. */
           nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
           buffer[length] = 0;
      }

    }

    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
                         &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a>nx_http_server_gmt_callback_set

Establecer la devolución de llamada para obtener la fecha y hora GMT.

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
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

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a>nx_http_server_invalid_userpassword_notify_set

Establecer la devolución de llamada para controlar la contraseña o el usuario no válidos

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a>Descripción

Este servicio establece la devolución de llamada invocada cuando se recibe un nombre de usuario y una contraseña no válidos en una solicitud GET, PUT o DELETE de cliente, ya sea mediante autenticación implícita o básica. El servidor HTTP se debe crear previamente.

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero al servidor HTTP.
 - **invalid_username_password_callback** Puntero a una devolución de llamada de aprobado/usuario no válido.
 - **resource** Puntero al recurso especificado por el cliente.
 - **client_address** Puntero a la dirección del cliente. Puede ser IPv4 o IPv6.
 - **request_type** Indica el tipo de solicitud de cliente. Puede ser:
    - NX_HTTP_SERVER_GET_REQUEST
    - NX_HTTP_SERVER_POST_REQUEST
    - NX_HTTP_SERVER_HEAD_REQUEST
    - NX_HTTP_SERVER_PUT_REQUEST
    - NX_HTTP_SERVER_DELETE_REQUEST

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a>nx_http_server_mime_maps_additional_set

Establecer asignaciones MIME adicionales para HTML

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a>Descripción

Este servicio permite al desarrollador de aplicaciones HTTP agregar tipos MIME adicionales de los tipos MIME predeterminados proporcionados por el servidor NetX Duo HTTP (consulte *nx_http_server_get_type* para ver una lista de tipos definidos).

Cuando se recibe una solicitud de cliente, por ejemplo, una solicitud GET, el servidor HTTP analiza el tipo de archivo solicitado del encabezado HTTP mediante el conjunto de asignaciones MIME adicional y, si no se encuentra ninguna coincidencia, busca una coincidencia en la asignación MIME predeterminada del servidor HTTP. Si no se encuentra ninguna coincidencia, el tipo MIME tiene como valor predeterminado "texto/sin formato".

Si la función de notificación de solicitud se registra con el servidor HTTP, la devolución de llamada de solicitud de notificación puede llamar a *nx_http_server_type_retrieve()* para analizar el tipo de archivo.

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

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a>nx_http_server_packet_content_find

Extraer la longitud del contenido y establecer el puntero en el inicio de los datos

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a>Descripción

Este servicio extrae la longitud del contenido del encabezado HTTP. También actualiza el paquete proporcionado de la siguiente manera: el puntero de anteposición del paquete (inicio de la ubicación del búfer de paquetes en el que se va a escribir) se establece en el contenido HTTP (datos) que se acaba de pasar al encabezado HTTP.

Si no se encuentra el principio del contenido en el paquete actual, la función espera a que se reciba el siguiente paquete mediante la opción de espera NX_HTTP_SERVER_TIMEOUT_RECEIVE.

> [!NOTE]
> No se debe llamar a esta función antes que a *nx_web_http_server_get_entity_header()* , ya que modifica el puntero de anteposición más allá del encabezado de entidad.

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero a la instancia de servidor HTTP.
 - **packet_ptr** Puntero al puntero de paquete para devolver el paquete con el puntero de anteposición actualizado.
 - **CONTENT_LENGTH** Puntero al valor de ```content_length``` extraído.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Se encontró la longitud del contenido HTTP y el paquete se actualizó correctamente.
 - **NX_HTTP_TIMEOUT** (0xE1) Tiempo agotado esperando al siguiente paquete.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a>nx_http_server_packet_get

Recibir el siguiente paquete HTTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a>Descripción

Este servicio devuelve el siguiente paquete recibido en el socket de servidor HTTP. La opción de espera para recibir un paquete es NX_HTTP_SERVER_TIMEOUT_RECEIVE.

### <a name="input-parameters"></a>Parámetros de entrada

 - **server_ptr** Puntero a la instancia de servidor HTTP.
 - **packet_ptr** Puntero al paquete recibido.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Siguiente paquete recibido correctamente.
 - **NX_HTTP_TIMEOUT** (0xE1) Tiempo agotado esperando al siguiente paquete.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a>nx_http_server_param_get

Obtener el parámetro de la solicitud

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a>Descripción

Este servicio intenta recuperar el parámetro de dirección URL HTTP especificado en el paquete de solicitud proporcionado. Si el parámetro HTTP solicitado no está presente, esta rutina devuelve un estado de NX_HTTP_NOT_FOUND. Se debe llamar a esta rutina desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create*).

### <a name="input-parameters"></a>Parámetros de entrada

 - **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que la aplicación no debe liberar este paquete.
 - **param_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de parámetros.
 - **param_ptr** Área de destino para copiar el parámetro.
 - **max_param_size** Tamaño máximo del área de destino del parámetro.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0X00) Parámetro del servidor HTTP obtenido correctamente.
 - **NX_WEB_HTTP_NOT_FOUND** (0xE6) Parámetro especificado no encontrado.
 - **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Parámetro de solicitud no terminado correctamente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a>nx_http_server_query_get

Obtiene la consulta de la solicitud

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a>Descripción

Este servicio intenta recuperar la consulta de dirección URL HTTP especificada en el paquete de solicitud proporcionado. Si la consulta HTTP solicitada no está presente, esta rutina devuelve un estado de NX_HTTP_NOT_FOUND. Se debe llamar a esta rutina desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create*).

### <a name="input-parameters"></a>Parámetros de entrada

 - **packet_ptr** Puntero al paquete de solicitud de cliente HTTP. Tenga en cuenta que la aplicación no debe liberar este paquete.
 - **query_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de consultas.
 - **query_ptr** Área de destino en la que se va a copiar la consulta.
 - **max_query_size** Tamaño máximo del área de destino de la consulta.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS**: (0x00) Consulta del servidor HTTP obtenida correctamente.
 - **NX_HTTP_FAILED** (0xE2) Tamaño de consulta demasiado pequeño.
 - **NX_HTTP_NOT_FOUND** (0xE6) No se encontró la consulta especificada.
 - **NX_HTTP_NO_QUERY_PARSED** (0xF2) No hay ninguna consulta en la solicitud de cliente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a>nx_http_server_start

Iniciar el servidor HTTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia la instancia de servidor HTTP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

 - **http_server_ptr** Puntero a la instancia de servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Servidor iniciado correctamente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a>nx_http_server_stop

Detener el servidor HTTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene la instancia de servidor HTTP creada anteriormente. Se debe llamar a esta rutina antes de eliminar una instancia del servidor HTTP.

### <a name="input-parameters"></a>Parámetros de entrada

 - **http_server_ptr** Puntero a la instancia de servidor HTTP.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Servidor detenido correctamente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.
 - NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a>nx_http_server_type_get

Extraer el tipo de archivo de la solicitud HTTP del cliente

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a>Descripción

> [!NOTE]
> Este servicio está en desuso. Se recomienda a los usuarios que usen el servicio *nx_http_server_type_get_extended()* .

Este servicio extrae el tipo de solicitud HTTP en el búfer http_type_string y su longitud en el valor devuelto del nombre del búfer de entrada, normalmente la dirección URL. Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo "texto/sin formato". En caso contrario, compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias. Los mapas MIME predeterminados del servidor HTTP de NetX Duo son:

 - **html** texto/html
 - **htm** texto/html
 - **txt** texto/sin formato
 - **gif** imagen/gif
 - **jpg** imagen/jpeg
 - **ico** imagen/x-icon

Si se proporciona, también se buscará un conjunto definido por el usuario de asignaciones MIME adicionales. Consulte *nx_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.

Este servicio está en desuso. Se recomienda a los desarrolladores migrar a *nx_http_server_type_get_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

 - **http_server_ptr** Puntero a la instancia de servidor HTTP.
 - **name** Puntero al búfer que se va a buscar.
 - **http_type_string** Puntero a la cadena de tipo HTML extraída.

### <a name="return-values"></a>Valores devueltos

 - **Longitud de la cadena en bytes** Un valor distinto de cero es correcto. Cero indica un error.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a>nx_http_server_type_get_extended

Extraer el tipo de archivo de la solicitud HTTP del cliente

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a>Descripción

Este servicio extrae el tipo de solicitud HTTP en el búfer *http_type_string* y su longitud en el valor devuelto por el *nombre* de búfer de entrada, normalmente la dirección URL. Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo "texto/sin formato". En caso contrario, compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias. Los mapas MIME predeterminados del servidor HTTP de NetX Duo son:

 - **html** texto/html
 - **htm** texto/html
 - **txt** texto/sin formato
 - **gif** imagen/gif
 - **jpg** imagen/jpeg
 - **ico** imagen/x-icon

Si se proporciona, también se buscará un conjunto definido por el usuario de asignaciones MIME adicionales. Consulte *nx_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.

Este servicio reemplaza a *nx_http_server_type_get()* . Esta versión proporciona información de longitud adicional.

### <a name="input-parameters"></a>Parámetros de entrada

 - **http_server_ptr** Puntero a la instancia de servidor HTTP.
 - **name** Puntero al búfer para buscar.
 - **name_length** Longitud del búfer que se va a buscar.
 - **http_type_string** Puntero a la cadena de tipo HTML extraída.
 - **http_type_string_max_size** Tamaño del búfer de http_type_string.

### <a name="return-values"></a>Valores devueltos

 - **Longitud de la cadena en bytes** Un valor distinto de cero es correcto. Cero indica un error.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
                    my_server.nx_http_server_request_resource, &resource_length,
                    sizeof(my_server.nx_http_server_request_resource) - 1))
           {
               return;
           }

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

Para ver un ejemplo más detallado, consulte la descripción de [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).

## <a name="nx_http_server_digest_authenticate_notify_set"></a>nx_http_server_digest_authenticate_notify_set

Establecer la función de devolución de llamada de autenticación implícita

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_digest_authenticate_notify_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                            CHAR *name_ptr,
                                            CHAR *realm_ptr,
                                            CHAR *password_ptr,
                                            CHAR *method,
                                            CHAR *authorization_uri,
                                            CHAR *authorization_nc,
                                            CHAR *authorization_cnonce
                                           ));
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

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a>nx_http_server_authentication_check_set

Establecer la función de devolución de llamada de comprobación de autenticación

### <a name="prototype"></a>Prototipo

```c
UINT nx_http_server_authentication_check_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*authentication_check_extended)(
                                            NX_HTTP_SERVER *server_ptr,
                                            UINT request_type,
                                            CHAR *resource,
                                            CHAR **name,
                                            UINT *name_length,
                                            CHAR **password,
                                            UINT *password_length,
                                            CHAR **realm,
                                            UINT *realm_length
                                            ));
```

### <a name="description"></a>Descripción

Este servicio establece la función de devolución de llamada de comprobación de autenticación.

### <a name="input-parameters"></a>Parámetros de entrada

 - **http_server_ptr** Puntero a la instancia de servidor HTTP.
 - **authentication_check** Puntero a la comprobación de autenticación de la aplicación.

### <a name="return-values"></a>Valores devueltos

 - **NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.
 - NX_PTR_ERROR (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
