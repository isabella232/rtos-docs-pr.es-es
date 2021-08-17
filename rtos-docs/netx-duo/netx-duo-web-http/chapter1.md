---
title: 'Capítulo 1: Introducción a HTTP y HTTPS'
description: En este capítulo se presenta el módulo de HTTP/HTTPS de Azure RTOS NetX Duo para web.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5f50419be3171d3df8544d1b34d603822f339785923f8a8199dc5b5ddcac281
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801764"
---
# <a name="chapter-1---introduction-to-http-and-https"></a>Capítulo 1: Introducción a HTTP y HTTPS

El Protocolo de transferencia de hipertexto (HTTP) es un protocolo diseñado para transferir contenido en la web. HTTP es un protocolo simple que emplea servicios del protocolo de control de transmisión (TCP) confiables para realizar su función de transferencia de contenido. Por este motivo, HTTP es un protocolo de transferencia de contenido de gran confiabilidad. HTTP es uno de los protocolos de aplicación más usados. Todas las operaciones en la web usan el protocolo HTTP.

HTTPS es la versión segura del protocolo HTTP, que implementa HTTP mediante seguridad de la capa de transporte (TLS) para proteger la conexión TCP subyacente. Aparte de la configuración adicional necesaria para configurar TLS, HTTPS es básicamente idéntico a HTTP en su uso.

## <a name="general-http-requirements"></a>Requisitos HTTP generales

Para que funcione correctamente, el paquete HTTP de NetX Web requiere que esté instalado NetX Duo (versión 5.10 o posterior). Además, se debe crear una instancia de IP y TCP debe estar habilitado en la misma instancia de IP. Para la compatibilidad con HTTPS, también se debe instalar NetX Secure TLS (versión 5.11 o posterior) (consulte la sección siguiente). El archivo de demostración de la sección "Sistema de ejemplo pequeño" del **Capítulo 2** mostrará cómo se hace esto.

La parte del cliente HTTP del paquete NetX Web HTTP no tiene ningún requisito adicional.

La parte del servidor HTTP del paquete NetX Web HTTP tiene varios requisitos adicionales. En primer lugar, requiere acceso completo al *puerto 80 conocido* de TCP para controlar todas las solicitudes HTTP de cliente (la aplicación puede cambiarlo a cualquier otro puerto TCP válido). El servidor HTTP también está diseñado para su uso con el sistema de archivos incrustado FileX. Si FileX no está disponible, el usuario puede migrar las partes de FileX usadas a su propio entorno. Esto se describe en secciones posteriores de esta guía.

## <a name="https-requirements"></a>Requisitos de HTTPS

Para que HTTPS funcione correctamente, el paquete HTTP de NetX Web requiere que se instalen NetX Duo (versión 5.10 o posterior) y NetX Secure TLS (versión 5.11 o posterior). Además, se debe crear una instancia de IP y TCP debe estar habilitado en la misma instancia de IP para su uso con TLS. La sesión de TLS deberá inicializarse con las rutinas criptográficas adecuadas, un certificado de CA de confianza y debe asignarse espacio para los certificados que los hosts de servidor remoto proporcionarán durante el protocolo de enlace de TLS. El archivo de demostración de la sección "Sistema HTTPS de ejemplo pequeño" del **Capítulo 2** mostrará cómo se hace esto.

La parte del cliente HTTPS del paquete NetX Web HTTP no tiene ningún requisito adicional.

La parte del servidor HTTPS del paquete NetX Web HTTP tiene varios requisitos adicionales. En primer lugar, requiere acceso completo al *puerto 443 conocido* de TCP para controlar todas las solicitudes HTTPS de cliente (al igual que para el HTTP de texto no cifrado, la aplicación puede modificarlo). En segundo lugar, la sesión de TLS deberá inicializarse con las rutinas criptográficas adecuadas y un certificado de identidad de servidor (o una clave previamente compartida). El servidor HTTPS también está diseñado para su uso con el sistema de archivos incrustado FileX. Si FileX no está disponible, el usuario puede migrar las partes de FileX usadas a su propio entorno. El uso de FileX se describe en secciones posteriores de esta guía.

Consulte la documentación de NetX Secure para obtener más información sobre las opciones de configuración para TLS.

A menos que se indique, todas las funciones HTTP descritas en este documento también se aplican a HTTPS.

## <a name="http-and-https-constraints"></a>Restricciones de HTTPS y HTTP

NetX Web HTTP implementa el estándar HTTP 1.1. Sin embargo, se aplican las restricciones siguientes:

1. No se admite la canalización de solicitudes.
1. El servidor HTTP es compatible con la autenticación implícita básica y MD5, pero no con MD5-sess. En la actualidad, el cliente HTTP solo admite la autenticación básica. Al usar TLS para HTTPS, todavía se puede usar la autenticación HTTP.
1. No se admite la compresión de contenido.
1. No se admiten las solicitudes TRACE, OPTIONS y CONNECT.
1. El grupo de paquetes asociado al servidor o cliente HTTP debe ser lo suficientemente grande como para contener el encabezado HTTP completo.
1. Los servicios de cliente HTTP son solo para la transferencia de contenido: no se proporciona ninguna utilidad de presentación en este paquete.

## <a name="http-url-resource-names"></a>URL HTTP (nombres de recursos)

El protocolo HTTP está diseñado para transferir contenido en la web. El contenido solicitado se especifica mediante el localizador uniforme de recursos (URL). Este es el componente principal de cada solicitud HTTP. Las direcciones URL siempre comienzan con un carácter "/" y suelen corresponderse con archivos del servidor HTTP. A continuación se muestran extensiones de archivo HTTP comunes:

- **.htm** (o **.html**) Lenguaje de marcado de hipertexto (HTML)
- **.txt** Texto ASCII sin formato
- **.gif** Imagen GIF binaria
- **.xbm** Imagen Xbitmap binaria

## <a name="http-client-requests"></a>Solicitudes de cliente HTTP

HTTP posee un mecanismo sencillo para solicitar contenido web. Hay un conjunto de comandos HTTP estándar que emite el cliente después de que una conexión se haya establecido correctamente en el *puerto conocido 80 (puerto 443 para HTTPS)* de TCP. A continuación se muestran algunos de los comandos HTTP básicos:

- **GET *resource* HTTP/1.1** Obtener el recurso especificado
- **POST *resource* HTTP/1.1** Obtener el recurso especificado y pasar la entrada adjunta al servidor HTTP
- **HEAD *resource* HTTP/1.1** Se trata como un GET pero el servidor HTTP no devuelve ningún contenido
- **PUT *resource* HTTP/1.1** Colocar recurso en servidor HTTP
- **DELETE *resource* HTTP/1.1** Eliminar recursos en el servidor

Estos comandos ASCII los generan internamente los exploradores web y los servicios de cliente NetX Web HTTP para realizar operaciones HTTP con un servidor HTTP.

Observe que la aplicación cliente HTTP debe usar el puerto 80, o el puerto 443 si se usa HTTPS. Las API HTTP de cliente y servidor toman el puerto como parámetro: las macros NX_WEB_HTTP_SERVER_PORT (puerto 80) y NX_WEB_HTTPS_SERVER_PORT (puerto 443) se definen por comodidad. El puerto del servidor HTTP también se puede cambiar en tiempo de ejecución mediante el servicio *nx_web_http_client_set_connect_port ()* . Consulte el capítulo 4 para obtener más detalles de este servicio.

## <a name="http-server-responses"></a>Respuestas del servidor HTTP

El servidor HTTP emplea el mismo *puerto 80 conocido de TCP (443 para HTTPS)* para enviar respuestas de comando de cliente. Una vez que el servidor HTTP procesa el comando de cliente, devuelve una cadena de respuesta ASCII que incluye un código de estado numérico de 3 dígitos. El software cliente HTTP usa la respuesta numérica para determinar si la operación se ha realizado correctamente o no. A continuación se muestra una lista de las distintas respuestas del servidor HTTP a los comandos de cliente:

- **200** La solicitud se ha realizado correctamente
- **400** La solicitud no tiene el formato correcto
- **401** Solicitud no autorizada, el cliente debe enviar la autenticación
- **404** No se ha encontrado el recurso especificado en la solicitud
- **500** Error interno del servidor HTTP
- **501** Solicitud no implementada por el servidor HTTP
- **502** El servicio no está disponible

Por ejemplo, a una solicitud de cliente PUT correcta para el archivo "test.htm" se responde con el mensaje "HTTP/1.1 200 OK".

## <a name="http-communication"></a>Comunicación HTTP

Como se ha mencionado anteriormente, el servidor HTTP emplea el *puerto 80 conocido (443 para HTTPS) de TCP* para las solicitudes de cliente de campo. Los clientes HTTP pueden utilizar cualquier puerto TCP disponible para las conexiones salientes. La secuencia general de eventos HTTP es la siguiente:

**Solicitud HTTP GET**:

1. El cliente emite TCP Connect al puerto 80 del servidor (o 443 para HTTPS).
1. Si se usa HTTPS, la conexión TCP va seguida de un protocolo de enlace TLS para autenticar el servidor y establecer un canal seguro.
1. El cliente envía la solicitud "**GET *resource* HTTP/1.1**" (junto con otra información de encabezado).
1. El servidor genera un mensaje "**HTTP/1.1 200 OK**" con información adicional seguida inmediatamente del contenido del recurso (si existe).
1. El servidor se desconecta del cliente (TLS se apaga si se usa HTTPS).
1. El cliente se desconecta del socket (TLS se apaga después de la alerta de desconexión del servidor).

**Solicitud HTTP PUT**:

1. El cliente emite una conexión TCP al puerto del servidor 80 (o 443).
1. Si se usa HTTPS, la conexión TCP va seguida de un protocolo de enlace TLS para autenticar el servidor y establecer un canal seguro.
1. El cliente envía la solicitud "PUT resource HTTP/1.1", junto con otra información de encabezado, seguida del contenido del recurso.
1. El servidor genera un mensaje "HTTP/1.1 200 OK" con información adicional seguida inmediatamente del contenido del recurso.
1. El servidor realiza una desconexión.
1. El cliente realiza una desconexión.

> [!NOTE]
> Como se ha mencionado anteriormente, el servidor HTTP puede cambiar el puerto de conexión predeterminado (80 o 443) en el tiempo de ejecución a otro puerto mediante *nx_web_http_client_set_connect_port()* para servidores web que usan puertos alternativos para conectarse a los clientes.

## <a name="http-authentication"></a>Autenticación HTTP

La autenticación HTTP es opcional y no es necesaria para todas las solicitudes web. Hay dos tipos de autenticación, a saber: *básica* e *implícita*. La autenticación básica es equivalente a la autenticación de *nombre* y *contraseña* que se encuentra en muchos protocolos. En la autenticación HTTP básica, el nombre y las contraseñas se concatenan y se codifican en formato base64. El principal inconveniente de la autenticación básica es que el nombre y la contraseña se transmiten abiertamente en la solicitud. Esto hace que resulte muy fácil que el nombre y la contraseña se roben. La autenticación implícita soluciona este problema, ya que nunca transmite el nombre y la contraseña en la solicitud. En su lugar, se utiliza un algoritmo para derivar una síntesis de 128 bits del nombre, la contraseña y otra información. El servidor NetX Web HTTP es compatible con el algoritmo de síntesis MD5 estándar.

¿Cuándo se requiere autenticación? El servidor HTTP decide si un recurso solicitado requiere autenticación. Si se requiere autenticación y la solicitud de cliente no incluía la autenticación correcta, se envía al cliente una respuesta "HTTP/1.1 401 No autorizado" con el tipo de autenticación necesario. A continuación, se espera que el cliente formule una nueva solicitud con la autenticación adecuada.

Cuando se usa HTTPS, el servidor HTTPS puede seguir usando la autenticación HTTP. En este caso, se usa TLS para cifrar todo el tráfico HTTP, por lo que el uso de la autenticación HTTP *básica* no supone un riesgo para la seguridad. También se permite la autenticación *implícita*, pero no proporciona una mejora de la seguridad significativa sobre la autenticación básica a través de TLS.

## <a name="http-authentication-callback"></a>Devolución de llamada de autenticación HTTP

Como se ha mencionado anteriormente, la autenticación HTTP es opcional y no es necesaria en todas las transferencias web. Además, la autenticación suele depender del recurso. El acceso a algunos recursos del servidor requiere autenticación, mientras que otros, no. El paquete de servidor NetX Web HTTP permite que la aplicación especifique (a través de la llamada a ***nx_web_http_server_create***) una rutina de devolución de llamada de autenticación a la que se llama al comenzar a administrar cada solicitud de cliente HTTP.

La rutina de devolución de llamada proporciona el servidor NetX Web HTTP con las cadenas de nombre de usuario, contraseña y dominio kerberos asociadas al recurso y devuelven el tipo de autenticación necesaria. Si no es necesaria ninguna autenticación para el recurso, la devolución de llamada de autenticación debe devolver el valor de **NX_WEB_HTTP_DONT_AUTHENTICATE**. De lo contrario, si se requiere la autenticación básica para el recurso especificado, la rutina debe devolver **NX_WEB_HTTP_BASIC_AUTHENTICATE**. Y, por último, si se requiere autenticación implícita MD5, la rutina de devolución de llamada debe devolver **NX_WEB_HTTP_DIGEST_AUTHENTICATE**. Si no se requiere autenticación para ningún recurso proporcionado por el servidor HTTP, la devolución de llamada no es necesaria y se puede proporcionar un puntero NULL a la llamada de creación del servidor HTTP.

El formato de la rutina de devolución de llamada de autenticación de la aplicación es muy simple y se define a continuación:

```C
UINT nx_web_http_server_authentication_check(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type, CHAR *resource,
    CHAR **name, CHAR **password,
    CHAR **realm);
```

Los parámetros de entrada se definen a continuación:

- **request_type**: especifica la solicitud de cliente HTTP; las solicitudes válidas se definen como:
  - **NX_WEB_HTTP_SERVER_GET_REQUEST**
  - **NX_WEB_HTTP_SERVER_POST_REQUEST**
  - **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
  - **NX_WEB_HTTP_SERVER_PUT_REQUEST**
  - **NX_WEB_HTTP_SERVER_DELETE_REQUEST**
- **resource** Recurso específico solicitado.
- **name** Destino del puntero al nombre de usuario solicitado.
- **password** Destino del puntero a la contraseña solicitada.
- **realm** Destino del puntero al dominio kerberos para esta autenticación.

El valor devuelto de la rutina de autenticación especifica si se requiere autenticación. Los punteros name, password y realm no se usan si la rutina de devolución de llamada de autenticación devuelve **NX_WEB_HTTP_DONT_AUTHENTICATE**. De lo contrario, el programador del servidor HTTP debe asegurarse de que **NX_WEB_HTTP_MAX_USERNAME** y **NX_WEB_HTTP_MAX_PASSWORD** definidos en *nx_web_http_server.h* sean lo suficientemente grandes para el nombre de usuario y la contraseña especificados en la devolución de llamada de autenticación. Ambos tienen un tamaño predeterminado de 20 caracteres.

## <a name="http-invalid-usernamepassword-callback"></a>Devolución de llamada de nombre de usuario/contraseña no válida HTTP

La devolución de llamada de nombre de usuario/contraseña no válida en el servidor NetX Web HTTP se invoca si el servidor HTTP recibe una combinación de nombre de usuario y contraseña no válida en una solicitud de cliente. Si la aplicación de servidor HTTP registra una devolución de llamada con el servidor HTTP, se invocará si se produce un error en la autenticación básica o implícita *en nx_web_http_server_get_process()* , en *nx_web_http_server_put_process()* o *en nx_web_http_server_delete_process().*

Para registrar una devolución de llamada con el servidor HTTP, el siguiente servicio se define en el servidor NetX Web HTTP.

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource, ULONG *client_nx_address,
        UINT request_type));
```

Los tipos de solicitud se definen de la manera siguiente:

- **NX_WEB_HTTP_SERVER_GET_REQUEST**
- **NX_WEB_HTTP_SERVER_POST_REQUEST**
- **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
- **NX_WEB_HTTP_SERVER_PUT_REQUEST**
- **NX_WEB_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>Devolución de llamada de encabezado de fecha GMT de inserción HTTP

Hay una devolución de llamada opcional en el servidor NetX Web HTTP para insertar un encabezado de fecha en sus mensajes de respuesta. Esta devolución de llamada se invoca cuando el servidor HTTP responde a una solicitud put o get

Para registrar una devolución de llamada de fecha GMT con el servidor HTTP, se define el siguiente servicio.

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

El tipo de datos NX_WEB_HTTP_SERVER_DATE se define de la siguiente manera:

```C
typedef struct NX_WEB_HTTP_SERVER_DATE_STRUCT
{
    USHORT nx_web_http_server_year; /* Year */
    UCHAR nx_web_http_server_month; /* Month */
    UCHAR nx_web_http_server_day; /* Day */
    UCHAR nx_web_http_server_hour; /* Hour */
    UCHAR nx_web_http_server_minute; /* Minute */
    UCHAR nx_web_http_server_second; /* Second */
    UCHAR nx_web_http_server_weekday; /* Weekday */
} NX_WEB_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>Devolución de llamada GET de información de caché HTTP

El servidor HTTP tiene una devolución de llamada para solicitar la antigüedad y la fecha máximas de la aplicación HTTP para un recurso específico. Esta información se usa para determinar si el servidor HTTP envía toda una página como respuesta a una solicitud GET de cliente. Si no se encuentra "If modified since" en la solicitud de cliente o no coincide con la fecha de "Last modified" devuelta por la devolución de llamada de caché GET, se envía toda la página.

Para registrar una devolución de llamada con el servidor HTTP, se define el siguiente servicio:

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a>Compatibilidad con la codificación de transferencia fragmentada HTTP

Cuando no se puede determinar la longitud total del mensaje HTTP antes de enviarlo, la característica de codificación de transferencia fragmentada se puede usar para enviar mensajes como una serie de fragmentos sin el campo de encabezado "longitud de contenido". Esta característica se admite en todos los mensajes de solicitud y respuesta HTTP. Como receptor, se admite esta característica y la lógica interna procesa el encabezado de fragmentos de forma transparente. Como remitente, el cliente y el servidor deben invocar la API *nx_web_http_client_request_chunked_set* y *nx_web_http_server_response_chunked_set*, respectivamente.

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

Para obtener más detalles sobre estos servicios, consulte sus descripciones en el capítulo 3 "Descripción de los servicios HTTP".

## <a name="http-multipart-support"></a>Compatibilidad con varias partes HTTP

Las extensiones multipropósito de correo Internet (MIME) estaban pensadas originalmente para el protocolo SMTP, pero su uso se ha extendido a HTTP. MIME permite que los mensajes contengan tipos de mensajes mixtos (por ejemplo, imagen/jpg y texto/sin formato) dentro del mismo mensaje. El servidor NetX Web HTTP cuenta con servicios para determinar el tipo de contenido en los mensajes HTTP del cliente que contienen MIME. Para habilitar la compatibilidad con varias partes HTTP y usar estos servicios, debe definirse la opción de configuración **NX_WEB_HTTP_MULTIPART_ENABLE**.

```C
UINT nx_web_http_server_get_entity_header(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);

UINT nx_web_http_server_get_entity_content(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

Para obtener más detalles sobre el uso de estos servicios, consulte su descripción en el capítulo 3 "Descripción de los servicios HTTP".

## <a name="http-multi-thread-support"></a>Compatibilidad con varios subprocesos HTTP

Se puede llamar a los servicios de cliente NetX Web HTTP desde varios subprocesos simultáneamente. Sin embargo, las solicitudes de lectura o escritura de una determinada instancia de cliente HTTP deben realizarse en secuencia desde el mismo subproceso.

Si se está usando HTTPS, es posible que se llame a los servicios de cliente NetX Web HTTP desde varios subprocesos pero, debido a la complejidad agregada de la funcionalidad de TLS subyacente, cada subproceso debe tener una única instancia de cliente HTTP independiente (estructura de control NX_WEB_HTTP_CLIENT).

## <a name="http-rfcs"></a>RFC de HTTP

NetX Web HTTP es compatible con la RFC1945 “Protocolo de transferencia de hipertexto/1.0”, RFC 2616 “Protocolo de transferencia de hipertexto – HTTP/1.1”, RFC 2581 “Control de congestión de TCP”, RFC 1122 “Requisitos para hosts de Internet” y RFC relacionadas.

En HTTPS, NetX Web HTTP es compatible con la RFC 2818 "HTTP sobre TLS".
