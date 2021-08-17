---
title: 'Capítulo 2: Instalación y uso de HTTP y HTTPS'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX Web HTTP.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fd8ab093d15c5413b0d5dac6d35b080674c3a332ec7a028fc462237135880d34
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783431"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a>Capítulo 2: Instalación y uso de HTTP y HTTPS

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX Web HTTP.

## <a name="product-distribution"></a>Distribución del producto

HTTP para NetX está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). El paquete incluye tres archivos de código fuente, dos archivos de inclusión y un archivo que contiene este documento, como se indica a continuación:

- **nx_web_http_common.h** Archivo de encabezado común para NetX Web HTTP
- **nx_web_http_client.h** Archivo de encabezado para el cliente HTTP para NetX Web
- **nx_web_http_server.h** Archivo de encabezado para el servidor HTTP para NetX Web
- **nx_web_http_client.c** Archivo de código fuente C para el cliente HTTP para NetX Web
- **nx_web_http_server.** Archivo de código fuente C para el servidor HTTP para NetX Web
- **nx_tcpserver. c** Archivo de código fuente C para varios sockets TCP
- **nx_tcpserver.h** Archivo de encabezado para definir símbolos de servidor HTTPS
- **nx_md5.c** Algoritmos de síntesis MD5
- **filex_stub.h** Archivo de código auxiliar si FileX no está presente
- **nx_web_http.pdf** Descripción de HTTP para NetX Web
- **demo_netx_web_http.c** Demostración de NetX Web HTTP

## <a name="http-installation"></a>instalación de HTTP

Para usar NetX Web HTTP, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo. Por ejemplo, si NetX Duo está instalado en el directorio “ *\threadx\arm7\green*”, *nx_web_http_client.h* y *nx_web_http_client.c para aplicaciones de cliente HTTP de NetX Web, y nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c y nx_tcpserver.h para aplicaciones de servidor HTTP de NetX Web. nx_web_http_common.h debe estar en ese mismo directorio tanto para las aplicaciones de servidor como cliente. nx_md5.c* también debe copiarse en ese mismo directorio si se está usando la autenticación implícita. Para la demostración, los archivos del servidor y cliente HTTP de la aplicación “controlador de RAM” deben copiarse en el mismo directorio.

Si se está usando TLS, es necesario contar con un directorio NetX Secure independiente que contenga los archivos de código fuente de TLS.

## <a name="using-http"></a>Uso de HTTP

El uso de NetX Web HTTP es sencillo. Básicamente, el código de aplicación debe incluir *nx_web_http_client.h* o *nx_web_http_server.h* después de incluir *tx_api.h, fx_api.h* y *nx_api.h* (*nx_web_http_common.h* se incluye automáticamente). Esos encabezados permiten que la aplicación use ThreadX, FileX y NetX Duo, respectivamente. Para la compatibilidad con HTTPS, se deben incluir los encabezados después de incluir el archivo *nx_secure_tls.h* para proporcionar compatibilidad con TLS.

Una vez incluidos los archivos de encabezado HTTP, el código de aplicación puede realizar las llamadas de función HTTP especificadas más adelante en este manual. La aplicación también debe vincularse con *nx_web_http_client.c para los clientes HTTP(S)* , *nx_web_http_server.c y nx_tcpserver.c para los servidores HTTP(S)* y *nx_md5.c (para la autenticación implícita)* en el proceso de compilación. Estos archivos se deben compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar NetX Web HTTP.

> [!NOTE]
> Si no se especifica NX_WEB_HTTP_DIGEST_ENABLE en el proceso de compilación, no es necesario agregar el archivo *MD5.c* a la aplicación. Del mismo modo, si no se requiere ninguna funcionalidad de cliente HTTP, se puede omitir el archivo *nx_web_http_client.c* y, si no se requiere ninguna funcionalidad de servidor HTTP, se puede omitir *nx_web_http_server.c*.
>
> A menos que se defina NX_WEB_HTTPS_ENABLE para habilitar HTTPS (en lugar de usar solo HTTP de texto no cifrado), no es necesario que el protocolo TLS seguro esté en la compilación.
>
> Puesto que HTTP usa los servicios de NetX TCP, TCP debe estar habilitado con la llamada a *nx_tcp_enable()* antes de utilizar HTTP.
>
> Cuando se usa HTTPS con NetX Secure TLS, TLS se debe inicializar con *nx_secure_tls_initialize()* antes de llamar a las rutinas HTTPS.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

En la figura 1.1 siguiente se describe un ejemplo de cómo usar NetX Web HTTP.

> [!CAUTION]
> Esto se proporciona solo con fines demostrativos y no hay garantía de que se compile y se ejecute tal cual.
>
> Consulte la distribución del código de la versión HTTPS de NetX Duo para ver los archivos de código fuente de demostración que se compilarán correctamente en el entorno de Express Logic nativo.  Observe también que estas demostraciones son muy simples de forma intencionada, ya que están diseñadas para dar a conocer la aplicación NetX Duo HTTPS o HTTPS a los nuevos usuarios.

En este ejemplo se incluyen el archivo de inclusión HTTP *nx_web_http_client.h y nx_web_http_server.h* (*netx_web_http_common.h* se incluye automáticamente). A continuación, el servidor HTTP se crea en "*tx_application_define*". Observe que el bloque de control de servidor HTTP "*Server*" se definió anteriormente como una variable global. Después de crearse correctamente, se inicia el servidor HTTPS. A continuación, se crea el cliente HTTPS. Escribe el archivo y vuelve a leer el archivo.

> [!NOTE]
> NX_WEB_HTTPS_ENABLE se define en este sistema.

```c
/* This is a small demo of HTTPS on the high-performance NetX Duo TCP/IP stack.
   This demo relies on ThreadX, NetX Duo, and FileX to show an HTML
   transfer from the client and then back from the server.  */

#include  "tx_api.h"
#include  "fx_api.h"
#include  "nx_api.h"
#include  “nx_crypto.h”
#include  “nx_secure_tls_api.h”
#include  “nx_secure_x509.h”
#include  "nx_web_http_client.h"
#include  "nx_web_http_server.h"
#define    DEMO_STACK_SIZE         4096


/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
TX_THREAD               thread_1;
NX_PACKET_POOL          pool_0;
NX_PACKET_POOL          pool_1;
NX_IP                   ip_0;
NX_IP                   ip_1;
FX_MEDIA                ram_disk;

/* Define HTTP objects.  */

NX_WEB_HTTP_SERVER      my_server;
NX_WEB_HTTP_CLIENT      my_client;

/* Define the counters used in the demo application...  */

ULONG                   error_counter;


/* Define the RAM disk memory.  */

UCHAR                   ram_disk_memory[32000];

/* Include cryptographic routines for TLS. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Define TLS data for HTTPS. */
CHAR crypto_metadata[8928 * NX_WEB_HTTP_SESSION_MAX];
UCHAR tls_packet_buffer[16500];

/* NX_WEB_HTTP_SERVER_SESSION_MAX defaults to 2 in nx_web_http_server.h */
UCHAR server_tls_packet_buffer[16500 * NX_WEB_HTTP_SERVER_SESSION_MAX];

/* Define certificate containers. The server certificate is used to identify the NetX
   Web HTTPS server and the trusted certificate is used by the client to verify the
   server’s identity certificate.  */
NX_SECURE_X509_CERT server_certificate;
NX_SECURE_X509_CERT trusted_certificate;

/* Remote certificates need both an NX_SECURE_X509_CERT container and an associated
   buffer. The number of certificates depends on the remote host, but usually at least
   two certificates will be sent – the identity certificate for the host and the
   certificate that issued the identity certificate. */
NX_SECURE_X509_CERT remote_certificate, remote_issuer;

UCHAR remote_cert_buffer[2000];
UCHAR remote_issuer_buffer[2000];

/* Certificate information for server and client (see NetX Secure TLS reference on X.509
    certificates for more information). Arrays are populated with binary versions Of
    certificates and keys and the corresponding “len” variables are assigned the lengths
    of that data. Trusted certificates do not need a private key. */
const UCHAR server_cert_der[] = { … };
const UINT  server_cert_derlen = … ;
const UCHAR server_cert_key_der[] = { … };
const UINT  server_cert_key_derlen = … ;

const UCHAR trusted_cert_der[] = { … };
const UINT  trusted_cert_derlen = … ;


/* Define function prototypes.  */

void    thread_0_entry(ULONG thread_input);
VOID    _fx_ram_driver(FX_MEDIA *media_ptr) ;
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT    authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
             CHAR *resource, CHAR **name, CHAR **password, CHAR **realm);
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
   NX_SECURE_TLS_SESSION *tls_session);

/* Define the application's authentication check.  This is called by
   the HTTP server whenever a new request is received.  */
UINT  authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
            CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
{
    /* Just use a simple name, password, and realm for all
       requests and resources.  */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Web HTTP demo";

    /* Request basic authentication.  */
    return(NX_WEB_HTTP_BASIC_AUTHENTICATE);
}

/* Define the TLS setup callback for HTTPS Client. This function is invoked when the
   HTTPS client is started – all TLS per-session initialization should go in here. */
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
  NX_SECURE_TLS_SESSION *tls_session)
{
    UINT status;

    /* Initialize and create TLS session. */
    nx_secure_tls_session_create(tls_session, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata));

    /* Allocate space for packet reassembly. */
    nx_secure_tls_session_packet_buffer_set(tls_session, tls_packet_buffer,
        sizeof(tls_packet_buffer));


    /* Add a CA Certificate to our trusted store for verifying incoming server
        certificates. */
    nx_secure_x509_certificate_initialize(&trusted_certificate, trusted_cert_der,
        trusted_cert_der_len, NX_NULL, 0, NULL, 0,
        NX_SECURE_X509_KEY_TYPE_NONE);
    nx_secure_tls_trusted_certificate_add(tls_session, &trusted_certificate);

    /* Need to allocate space for the certificate coming in from the remote host. */
    nx_secure_tls_remote_certificate_allocate(tls_session, &remote_certificate,
        remote_cert_buffer, sizeof(remote_cert_buffer));
    nx_secure_tls_remote_certificate_allocate(tls_session,
        &remote_issuer, remote_issuer_buffer,
        sizeof(remote_issuer_buffer));

    return(NX_SUCCESS);
 }

/* Define main entry point.  */

 int main()
 {
     /* Enter the ThreadX kernel.  */
     tx_kernel_enter();
 }

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    CHAR    *pointer;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create packet pool.  */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
        600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance.  */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer =  pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create another IP instance.  */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
        0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk.  */
    fx_media_open(&ram_disk, "RAM DISK",
        _fx_ram_driver, ram_disk_memory, pointer, 4096);
    pointer += 4096;

    /* Create the NetX Web HTTP Server.  */
    nx_web_http_server_create(&my_server, "My HTTP Server", &ip_1,
        NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
        pointer, 4096, &pool_1, authentication_check, NX_NULL);
    pointer = pointer + 4096;

    /* The TLS server needs an identity certificate which is imported as a binary DER-
        encoded X.509 certificate and its associated private key (e.g. DER-encoded PKCS#1
        RSA private key). */
    nx_secure_x509_certificate_initialize(&server_certificate, server_cert_der,
        server_cert_der_len, NX_NULL, 0,
        server_cert_key_der, server_cert_key_der_len,
        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Setup TLS session data for the TCP server.
        This enables TLS and HTTPS for the server.  */
    nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata), server_tls_packet_buffer,
        sizeof(server_tls_packet_buffer), &server_certificate, NX_NULL, 0,
        NX_NULL, 0, NX_NULL, 0);

    /* Start the HTTP Server.  */
    nx_web_http_server_start(&my_server);
}

/* Define the test thread.  */
void    thread_0_entry(ULONG thread_input)
{
    NX_PACKET   *my_packet;
    UINT        status;

    /* Create an HTTP client instance.  */
    status = nx_web_http_client_create(&my_client, "My Client", &ip_0, &pool_0, 600);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server over HTTPS.  */
    status = nx_web_http_client_put_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm", "name", "password", 103, tls_setup_callback, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Allocate a packet.  */
     tatus = nx_web_http_client_request_packet_allocate(&pool_0, &my_packet,
        NX_TCP_PACKET, NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page.  */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
        "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length.  */
    status =  nx_web_http_client_put_packet(&my_client, my_packet, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Now GET the file back!  */
    status =  nx_web_http_client_get_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm",
        "name", "password", tls_setup_callback, 50);
 
    /* Check status.  */
    if (status)
        error_counter++;

    /* Get a packet.  */
    status =  nx_web_http_client_response_body_get(&my_client, &my_packet, 20);

    /* Check for an error.  */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet.  */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it!  */
        nx_packet_release(my_packet);
    }

    /* Make sure TLS shuts down properly. */
    nx_web_http_client_delete(&my_client);

    /* Flush the media.  */
    fx_media_flush(&ram_disk);
}
```

**Figura 1.1 Ejemplo de uso de HTTPS con NetX y NetX Secure TLS**

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar HTTP para NetX. A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas. Los valores predeterminados se enumeran pero se pueden redefinir antes de incluir *nx_web_http_client.h y nx_web_http_server.h*:

- **NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica de HTTP. Normalmente se utiliza después de depurar la aplicación.
- **NX_WEB_HTTP_DIGEST_ENABLE**: si está definida, la autenticación con el resumen MD5 está habilitada en el servidor HTTPS. De forma predeterminada, no está definido.
- **NX_WEB_HTTP_SERVER_PRIORITY**: prioridad del subproceso de servidor HTTPS. De forma predeterminada, este valor se define como 16 para especificar la prioridad 16.
- **NX_WEB_HTTP_NO_FILEX**: si está definida, esta opción proporciona un código auxiliar para las dependencias de FileX. El cliente HTTPS funcionará sin ningún cambio si se define esta opción. El servidor HTTPS tendrá que modificarse o el usuario tendrá que crear unos cuantos servicios de FileX para que funcionen correctamente.
- **NX_WEB_HTTP_TYPE_OF_SERVICE**: tipo de servicio necesario para las solicitudes TCP de HTTPS. De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal.
- **NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE**: el número de tics de temporizador que el subproceso de servidor puede ejecutar antes de producir subprocesos con la misma prioridad. El valor predeterminado es 2. Observe que esta opción está en desuso.
- **NX_WEB_HTTP_FRAGMENT_OPTION**: fragmento habilitar para solicitudes TCP de HTTP. De forma predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de TCP de HTTP.
- **NX_WEB_HTTP_SERVER_WINDOW_SIZE**: tamaño de la ventana de socket de servidor. De manera predeterminada, este valor es 2048 bytes.
- **NX_WEB_HTTP_TIME_TO_LIVE**: especifica el número de enrutadores que un paquete puede pasar antes de que se descarte. El valor predeterminado se define en 0x80.
- **NX_WEB_HTTP_SERVER_TIMEOUT**: especifica el número de tics de ThreadX en los que se suspenderán los servicios internos. El valor predeterminado es 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT**: especifica el número de tics de ThreadX en los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_server_socket_accept()* . El valor predeterminado está establecido en (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT**: especifica el número de tics de ThreadX en los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_disconnect()* . El valor predeterminado es 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT**: especifica el número de tics de ThreadX en los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_disconnect()* . El valor predeterminado es 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_SEND**: especifica el número de tics de ThreadX en los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_disconnect()* . El valor predeterminado es 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_MAX_HEADER_FIELD** **: especifica el tamaño máximo del campo de encabezado HTTP. El valor predeterminado es 256.**
- **NX_WEB_HTTP_MULTIPART_ENABLE ** **: si está definido, permite que el servidor HTTPS admita solicitudes HTTP de varias partes. **
- **NX_WEB_HTTP_SERVER_MAX_PENDING**: especifica el número de conexiones que se pueden poner en cola para el servidor HTTPS. El valor predeterminado se establece en el doble del número máximo de sesiones de servidor.
- **NX_WEB_HTTP_MAX_RESOURCE**: especifica el número de bytes permitido en el *nombre de recurso* proporcionado por un cliente. El valor predeterminado se establece en 40.
- **NX_WEB_HTTP_MAX_NAME**: especifica el número de bytes permitido en el *nombre de usuario* proporcionado por un cliente. El valor predeterminado se establece en 20.
- **NX_WEB_HTTP_MAX_PASSWORD**: especifica el número de bytes permitido en la *contraseña* proporcionada por un cliente. El valor predeterminado se establece en 20.
- **NX_WEB_HTTP_SERVER_SESSION_MAX**: especifica el número de sesiones simultáneas para un servidor HTTP o HTTPS. Se asignan un socket TCP y una sesión TLS (si HTTPS está habilitado) para cada sesión. El valor predeterminado se establece en 2.
- **NX_WEB_HTTPS_ENABLE**: si se define, esta macro habilita TLS y HTTPS. Deje sin definir para liberar recursos si solo desea un HTTP de texto no cifrado. De forma predeterminada, esta macro no está definida.
- **NX_WEB_HTTPS_KEEPALIVE_DISABLE**: si se define, esta macro deshabilita la característica de conexión persistente de HTTP. De forma predeterminada, esta macro no está definida.
- **NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE**: especifica el tamaño mínimo de los paquetes en el grupo especificado al crear el servidor. El tamaño mínimo es necesario para asegurarse de que el encabezado HTTP completo puede estar incluido en un paquete. El valor predeterminado se establece en 600.
- **NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE**: especifica el tamaño mínimo de los paquetes en el grupo especificado al crear el cliente. El tamaño mínimo es necesario para asegurarse de que el encabezado HTTP completo puede estar incluido en un paquete. El valor predeterminado se establece en 600.
- **NX_WEB_HTTP_SERVER_RETRY_SECONDS**: establece el tiempo de espera de retransmisión de sockets de servidor en segundos. El valor predeterminado se establece en 2.
- **NX_WEB_HTTP_ SERVER_RETRY_MAX**: establece el número máximo de retransmisiones en el socket de servidor. El valor predeterminado se establece en 10.
- **NX_WEB_HTTP_ SERVER_RETRY_SHIFT**: este valor se usa para establecer el siguiente tiempo de espera de retransmisión. El tiempo de espera actual se multiplica por el número de retransmisiones hasta el momento, desplazado por el valor del desplazamiento de tiempo de espera del socket. El valor predeterminado se establece en 1 para duplicar el tiempo de espera.
- **NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH**: especifica el número máximo de paquetes que se pueden poner en cola en la cola de retransmisión de sockets de servidor. Si el número de paquetes puestos en cola alcanza este número, no se podrán enviar más paquetes hasta que se liberen uno o varios paquetes en cola. El valor predeterminado se establece en 20.
