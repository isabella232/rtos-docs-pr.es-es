---
title: 'Capítulo 1: Introducción a HTTP de NetX Duo para Azure RTOS'
description: En este capítulo se presenta el módulo HTTP de NetX Duo para Azure RTOS.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 45f35f2c1bec142e10d29eedb6e5a88a8eb74771e5d4adf1d85b04a87ad59ab7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796215"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-http"></a>Capítulo 1: Introducción a HTTP de NetX Duo para Azure RTOS

El protocolo de transferencia de hipertexto (HTTP) es un protocolo diseñado para transferir contenido en la web. HTTP es un protocolo simple que emplea servicios del protocolo de control de transmisión (TCP) confiables para realizar su función de transferencia de contenido. Por este motivo, HTTP es un protocolo de transferencia de contenido de gran confiabilidad. HTTP es uno de los protocolos de aplicación más usados. Todas las operaciones en la web usan el protocolo HTTP. HTTP de NetX Duo para Azure RTOS admite redes IPv4 e IPv6. IPv6 no cambia directamente el protocolo HTTP, aunque algunos cambios en la API HTTP de NetX para Azure RTOS original son necesarios para admitir IPv6 y se describen en este documento.

## <a name="http-requirements"></a>Requisitos de HTTP

Para que funcione correctamente, el paquete HTTP de NetX Duo requiere la instalación de NetX Duo (versión 5.2 o posterior). Además, se debe haber creado ya una instancia de IP y TCP debe estar habilitado en esa misma instancia de IP. Una aplicación host IPv6 debe establecer su dirección IPv6 local y global de vínculo mediante la API de IPv6 o DHCPv6. El archivo de demostración de la sección "Sistema de ejemplo pequeño" del **Capítulo 2** mostrará cómo se hace esto.

La parte del cliente HTTP del paquete HTTP de NetX Duo no tiene ningún requisito adicional.

La parte del servidor HTTP del paquete HTTP de NetX Duo tiene varios requisitos adicionales. En primer lugar, se necesita acceso completo al puerto 80 conocido de TCP para controlar todas las solicitudes HTTP de cliente. El servidor HTTP también está diseñado para su uso con el sistema de archivos incrustado FileX. Si FileX no está disponible, el usuario puede migrar las partes de FileX usadas a su propio entorno. Este proceso se describe en secciones posteriores de esta guía.

## <a name="http-constraints"></a>Restricciones de HTTP

El protocolo HTTP de NetX Duo implementa el estándar HTTP 1.0. Sin embargo, se aplican las restricciones siguientes:

1.  No se admiten conexiones persistentes
2.  No se admite la canalización de solicitudes
3.  El servidor HTTP es compatible con la autenticación implícita básica y MD5, pero no con MD5-sess. En la actualidad, el cliente HTTP solo admite la autenticación básica.
4.  No se admite la compresión de contenido.
5.  No se admiten las solicitudes TRACE, OPTIONS y CONNECT.
6.  El grupo de paquetes asociado al servidor o cliente HTTP debe ser lo suficientemente grande como para contener el encabezado HTTP completo.
7.  Los servicios de cliente HTTP son solo para la transferencia de contenido: no se proporciona ninguna utilidad de presentación en este paquete.

## <a name="http-url-resource-names"></a>URL HTTP (nombres de recursos)

El protocolo HTTP está diseñado para transferir contenido en la web. El contenido solicitado se especifica mediante el localizador uniforme de recursos (URL). Este es el componente principal de cada solicitud HTTP. Las direcciones URL siempre comienzan con un carácter *"/"* y suelen corresponderse con archivos del servidor HTTP. A continuación, se muestran extensiones de archivo HTTP comunes:

| Extensión | Significado |
| --------- | ------- |
| .htm (o .html) | Lenguaje de marcado de hipertexto (HTML) |
| .txt | Texto ASCII sin formato |
| .gif | Imagen GIF binaria |
| .xbm | Imagen Xbitmap binaria |

## <a name="http-client-requests"></a>Solicitudes de cliente HTTP

HTTP posee un mecanismo sencillo para solicitar contenido web. Básicamente, hay un conjunto de comandos HTTP estándar que emite el cliente después de que una conexión se haya establecido correctamente en el *puerto conocido 80* de TCP. A continuación, se muestran algunos de los comandos HTTP básicos:

| Comando HTTP | Significado |
| ------------ | ------- |
| GET resource HTTP/1.0 | *Obtener el recurso especificado* |
| POST resource HTTP/1.0 | *Obtener el recurso especificado y pasar la entrada asociada al servidor HTTP* |
| HEAD resource HTTP/1.0 | *Se trata como GET, pero el servidor HTTP no devuelve contenido* |
| PUT resource HTTP/1.0 | *Colocar recurso en el servidor HTTP* |
| DELETE resource HTTP/1.0 | *Eliminar recurso del servidor* |

Estos comandos ASCII los generan internamente los exploradores web y los servicios de cliente NetX HTTP para realizar operaciones HTTP con un servidor HTTP.

> [!NOTE]
> La aplicación de cliente HTTP tiene como valor predeterminado el puerto de conexión 80. Sin embargo, puede cambiar el puerto de conexión al servidor HTTP en tiempo de ejecución mediante el servicio nx_http_client_set_connect_port. Consulte el capítulo 4 para obtener más detalles de este servicio. La finalidad es alojar servidores web que utilizan ocasionalmente puertos alternativos para las conexiones de cliente.

## <a name="http-server-responses"></a>Respuestas del servidor HTTP

El servidor HTTP emplea el mismo *puerto 80 conocido de TCP* para enviar respuestas de comando de cliente. Una vez que el servidor HTTP procesa el comando de cliente, devuelve una cadena de respuesta ASCII que incluye un código de estado numérico de 3 dígitos. El software cliente HTTP usa la respuesta numérica para determinar si la operación se ha realizado correctamente o no. A continuación, se muestra una lista de las distintas respuestas del servidor HTTP a los comandos de cliente:

| Campo numérico | Significado |
| ------------- | ------- |
| *200* | *La solicitud se realizó correctamente.* |
| *400* |   *La solicitud no tiene el formato correcto* |
| *401* | *Solicitud no autorizada, el cliente debe enviar la autenticación* |
| *404* | *No se ha encontrado el recurso especificado en la solicitud* |
| *500* | *Error interno del servidor HTTP* |
| *501* | *Solicitud no implementada por el servidor HTTP* |
| *502* | *El servicio no está disponible* |

Por ejemplo, a una solicitud de cliente PUT correcta para el archivo "test.htm" se responde con el mensaje "HTTP/1.0 200 OK".

## <a name="http-communication"></a>Comunicación HTTP

Como se ha mencionado anteriormente, el servidor HTTP emplea el puerto 80 conocido de TCP para las solicitudes de cliente de campo. Los clientes HTTP pueden utilizar cualquier puerto TCP disponible. La secuencia general de eventos HTTP es la siguiente:

### <a name="http-get-request"></a>Solicitud HTTP GET:

1.  el cliente emite una conexión TCP al puerto de servidor 80.
2.  El cliente envía la solicitud "**GET resource HTTP/1.0**" (junto con otra información de encabezado).
3.  El servidor genera un mensaje "**HTTP/1.0 200 OK**" con información adicional seguida inmediatamente del contenido del recurso (si existe).
4.  El servidor realiza una desconexión.
5.  El cliente realiza una desconexión.

### <a name="http-put-request"></a>Solicitud HTTP PUT:

1.  el cliente emite una conexión TCP al puerto de servidor 80.
2.  El cliente envía la solicitud "**PUT resource HTTP/1.0**", junto con otra información de encabezado, seguida del contenido del recurso.
3.  El servidor genera un mensaje "**HTTP/1.0 200 OK**" con información adicional seguida inmediatamente del contenido del recurso.
4.  El servidor realiza una desconexión.
5.  El cliente realiza una desconexión.

> [!NOTE]
>Como se ha mencionado anteriormente, el cliente HTTP puede cambiar el puerto de conexión predeterminado 80 por otro puerto mediante *nx_http_client_set_connect_port* para servidores web que usan puertos alternativos para conectarse a los clientes.

## <a name="http-authentication"></a>Autenticación HTTP

La autenticación HTTP es opcional y no es necesaria en todas las solicitudes web. Hay dos tipos de autenticación, a saber: básica e implícita. La autenticación básica es equivalente a la autenticación de nombre y contraseña que se encuentra en muchos protocolos. En la autenticación HTTP básica, el nombre y las contraseñas se concatenan y se codifican en formato base64. El principal inconveniente de la autenticación básica es que el nombre y la contraseña se transmiten abiertamente en la solicitud. Esto hace que resulte muy fácil que el nombre y la contraseña se roben. La autenticación implícita soluciona este problema, ya que nunca transmite el nombre y la contraseña en la solicitud. En su lugar, se utiliza un algoritmo para derivar una clave de 128 bits o una síntesis del nombre, la contraseña y otra información. El servidor HTTP de NetX admite el algoritmo de síntesis estándar MD5.

¿Cuándo se requiere autenticación? Básicamente, el servidor HTTP decide si un recurso solicitado requiere autenticación. Si se requiere autenticación y la solicitud de cliente no incluía la autenticación correcta, se envía al cliente una respuesta "HTTP/1.0 401 No autorizado" con el tipo de autenticación necesario. A continuación, se espera que el cliente formule una nueva solicitud con la autenticación adecuada.

## <a name="http-authentication-callback"></a>Devolución de llamada de autenticación HTTP

Como se ha mencionado anteriormente, la autenticación HTTP es opcional y no es necesaria en todas las transferencias web. Además, la autenticación suele depender del recurso. El acceso a algunos recursos del servidor requiere autenticación, mientras que otros, no. El paquete de servidor HTTP de NetX permite que la aplicación especifique (a través de la llamada a *nx_http_server_create*) una rutina de devolución de llamada de autenticación a la que se llama al comenzar a administrar cada solicitud de cliente HTTP.

La rutina de devolución de llamada proporciona al servidor HTTP de NetX las cadenas de nombre de usuario, contraseña y dominio asociadas al recurso y devuelven el tipo de autenticación necesaria. Si el recurso no necesita autenticación, la devolución de llamada de autenticación debe devolver el valor de **NX_HTTP_DONT_AUTHENTICATE**. De lo contrario, si el recurso especificado requiere la autenticación básica, la rutina debe devolver **NX_HTTP_BASIC_AUTHENTICATE**. Y, por último, si se requiere autenticación implícita MD5, la rutina de devolución de llamada debe devolver **NX_HTTP_DIGEST_AUTHENTICATE**. Si ningún recurso proporcionado por el servidor HTTP requiere autenticación, la devolución de llamada no es necesaria y se puede proporcionar un puntero NULL a la llamada de creación del servidor HTTP.

El formato de la rutina de devolución de llamada de autenticación de la aplicación es muy simple y se define a continuación:

```c
UINT nx_http_server_authentication_check(NX_HTTP_SERVER *server_ptr,
                                          UINT request_type, CHAR *resource,
                                          CHAR **name, CHAR **password,
                                          CHAR **realm);
```
Los parámetros de entrada se definen a continuación:

| Parámetro | Significado |
| --------- | --------|
| *request_type* | Especifica la solicitud de cliente HTTP; las solicitudes válidas se definen como: <br/> **NX_HTTP_SERVER_GET_REQUEST**<br/>**NX_HTTP_SERVER_POST_REQUEST**<br/>**NX_HTTP_SERVER_HEAD_REQUEST**<br/>**NX_HTTP_SERVER_PUT_REQUEST**<br/>**NX_HTTP_SERVER_DELETE_REQUEST** |
| *resource* | Recurso específico solicitado. |
| *name* | Destino del puntero al nombre de usuario necesario. |
| *password* | Destino del puntero a la contraseña solicitada. |
| *realm* | Destino del puntero al dominio de esta autenticación. |

El valor devuelto de la rutina de autenticación especifica si se requiere autenticación. Los punteros ```name, password, and realm``` no se usan si la rutina de devolución de llamada de autenticación devuelve **NX_HTTP_DONT_AUTHENTICATE**. De lo contrario, el desarrollador del servidor HTTP debe asegurarse de que **NX_HTTP_MAX_USERNAME** y **NX_HTTP_MAX_PASSWORD** definidos en *nx_http_server.h* sean lo suficientemente grandes para el nombre de usuario y la contraseña especificados en la devolución de llamada de autenticación. Ambos tienen como tamaño predeterminado 20 caracteres.

## <a name="http-invalid-usernamepassword-callback"></a>Devolución de llamada de nombre de usuario/contraseña no válida HTTP

La devolución de llamada de nombre de usuario/contraseña no válida en el servidor HTTP de NetX se invoca si el servidor HTTP recibe una combinación de nombre de usuario y contraseña no válida en una solicitud de cliente. Si la aplicación de servidor HTTP registra una devolución de llamada con el servidor HTTP, se invocará si se produce un error en la autenticación básica o implícita en *nx_http_server_get_process*, en *nx_http_server_put_process* o en *nx_http_server_delete_process*.

Para registrar una devolución de llamada con el servidor HTTP, el siguiente servicio se define en el servidor HTTP de NetX Duo.

```c
UINT nx_http_server_invalid_userpassword_notify_set(
                   NX_HTTP_SERVER *http_server_ptr,
                   UINT *invalid_username_password_callback)
                            (CHAR *resource,
                             NXD_ADDRESS *client_nxd_address,
                             UINT request_type))
```

Los tipos de solicitud se definen de la manera siguiente:
 - **NX_HTTP_SERVER_GET_REQUEST**
 - **NX_HTTP_SERVER_POST_REQUEST**
 - **NX_HTTP_SERVER_HEAD_REQUEST**
 - **NX_HTTP_SERVER_PUT_REQUEST**
 - **NX_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>Devolución de llamada de encabezado de fecha GMT de inserción HTTP

Hay una devolución de llamada opcional en el servidor HTTP de NetX Duo para insertar un encabezado de fecha en sus mensajes de respuesta. Esta devolución de llamada se invoca cuando el servidor HTTP responde a una solicitud PUT o GET.

Hay una devolución de llamada opcional en el servidor HTTP de NetX Duo para insertar un encabezado de fecha en sus mensajes de respuesta. Esta devolución de llamada se invoca cuando el servidor HTTP responde a una solicitud PUT o GET.

Para registrar una devolución de llamada de fecha GMT con el servidor HTTP, el siguiente servicio se define en el servidor HTTP de NetX Duo.

```c
UINT  _nx_http_server_gmt_callback_set(
                    NX_HTTP_SERVER *server_ptr,
                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date)
```

El tipo de datos NX_HTTP_SERVER_DATE se define de la siguiente manera:

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT          nx_http_server_year;           /* Year                 */
    UCHAR           nx_http_server_month;          /* Month                */
    UCHAR           nx_http_server_day;            /* Day                  */
    UCHAR           nx_http_server_hour;           /* Hour              */
    UCHAR           nx_http_server_minute;         /* Minute               */
    UCHAR           nx_http_server_second;         /* Second               */
    UCHAR           nx_http_server_weekday;        /* Weekday              */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>Devolución de llamada GET de información de caché HTTP

El servidor HTTP tiene una devolución de llamada para solicitar la antigüedad y la fecha máximas de la aplicación HTTP de un recurso específico. Esta información se usa para determinar si el servidor HTTP envía toda la página como respuesta a una solicitud GET de cliente. Si no se encuentra "if modified since" en la solicitud de cliente o no coincide con la fecha de "last modified" devuelta por la devolución de llamada de caché GET, se envía toda la página.

Para registrar una devolución de llamada con el servidor HTTP, se define el siguiente servicio:

```c
UINT  _nx_http_server_cache_info_callback_set(
                              NX_HTTP_SERVER *server_ptr,
                              UINT (*cache_info_get)
                                    (CHAR *, UINT *, NX_HTTP_SERVER_DATE *))
```

## <a name="http-multipart-support"></a>Compatibilidad con varias partes HTTP

Las extensiones multipropósito de correo Internet (MIME) estaban pensadas originalmente para el protocolo SMTP, pero su uso se ha extendido a HTTP. MIME permite que los mensajes contengan tipos de mensajes mixtos (por ejemplo, imagen/jpg y texto/sin formato) dentro del mismo mensaje. El servidor HTTP de NetX Duo ha agregado servicios para determinar el tipo de contenido en los mensajes HTTP que contienen MIME del cliente. Para permitir la compatibilidad con varias partes HTTP y usar estos servicios, debe definirse la opción de configuración **NX_HTTP_MULTIPART_ENABLE**.

```c
UINT  nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       UCHAR *entity_header_buffer,
                                       ULONG buffer_size);

UINT  nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_pptr,
                                        ULONG *available_offset,
                                        ULONG *available_length)
```

Para más detalles sobre el uso de estos servicios, vea su descripción en el capítulo 3 "Descripción de los servicios HTTP".

## <a name="http-multi-thread-support"></a>Compatibilidad con varios subprocesos HTTP

Se puede llamar a los servicios de cliente HTTP de NetX desde varios subprocesos simultáneamente. Sin embargo, las solicitudes de lectura o escritura de una determinada instancia de cliente HTTP deben realizarse en secuencia desde el mismo subproceso.

## <a name="http-rfcs"></a>Documentos RFC de HTTP

HTTP de NetX es compatible con los documentos RFC1945 "Protocolo de transferencia de hipertexto/1.0", RFC 2581 "Control de congestión de TCP", RFC 1122 "Requisitos para hosts de Internet" y RFC relacionados.
