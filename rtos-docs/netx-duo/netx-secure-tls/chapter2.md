---
title: 'Capítulo 2: Instalación y uso de Azure RTOS NetX Secure'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX Secure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d11e50b2ab74ee147f682567d142768de6108fc18264e9d8bc69bbfc8a32cc0a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801876"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a>Capítulo 2: Instalación y uso de Azure RTOS NetX Secure

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente Azure RTOS NetX Secure.

## <a name="product-version-number"></a>Número de versión del producto

El usuario puede comprobar el número de versión del producto mediante la búsqueda de los siguientes símbolos en nx_secure_tls.h:

***NETX_SECURE_MAJOR_VERSION***

***NETX_SECURE_MINOR_VERSION***

Las versiones de Service Pack tienen el siguiente símbolo definido para indicar el número de Service Pack:

***NETX_SECURE_SERVICE_PACK_VERSION***

## <a name="product-distribution"></a>Distribución del producto

NetX Secure está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx). El paquete incluye archivos de código fuente, archivos de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:

- **nx_secure_tls_api.h** Archivo de encabezado de API pública para TLS de NetX Secure
- **nx_secure_tls_user.h** Archivo de encabezado definido por el usuario para TLS de NetX Secure
- **nx_secure_tls_port.h** Definiciones específicas de la plataforma para NetX Secure
- **nx_secure_tls.h** Archivo de encabezado para TLS de NetX Secure
- **nx_secure_tls&#42;.c/h** Archivos de código fuente C/H para TLS de NetX Secure
- **nx_crypto&#42;.c/h** Archivos de código fuente C/H para la criptografía de NetX Secure
- **nx_secure_x509&#42;.c/h** Archivos de código fuente C/H para certificados digitales X.509
- **demo_netx_secure_tls.c** Archivo de código fuente C para la demostración de TLS de NetX Secure
- **NetX_Secure_User_Guide.pdf** Descripción en PDF del producto NetX Secure

> [!NOTE]
> Los archivos nx_crypto* se proporcionan para distintas plataformas de hardware en un subdirectorio del directorio primario de NetX Secure.

## <a name="netx-secure-installation"></a>Instalación de NetX Secure

Para usar NetX Secure, toda la distribución que se menciona anteriormente debe copiarse en el mismo directorio en el que se ha instalado NetX. Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\NetX*", los directorios *nx_secure **.* deben copiarse en " *\threadx\arm7\NetXSecure*".

## <a name="using-netx-secure"></a>Uso de NetX Secure

Usar TLS de NetX Secure es sencillo. Básicamente, el código de la aplicación debe incluir *nx_secure_tls_api.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX. Después de incluir *nx_secure_tls_api.h*, el código de la aplicación puede realizar las llamadas de función DHCP especificadas más adelante en esta guía. La aplicación también debe importar los archivos *nx_secure**.* a una biblioteca de NetXSecure y los archivos específicos de la plataforma *nx_crypto**.* a una biblioteca de NetXCrypto.

## <a name="small-example-system-tls-client"></a>Sistema de ejemplo pequeño (cliente TLS)

Un ejemplo de lo fácil que es usar NetX Secure se describe en la figura 1.1, que aparece a continuación. Muestra un cliente TLS simple, que usa módulos criptográficos de software (no específicos de hardware) para el cifrado. Está diseñado para funcionar con el servidor de eco inverso OpenSSL (openssl s_server -rev).

Tenga en cuenta que, para poder ejecutar este ejemplo, necesitará un certificado de CA X.509 para autenticar el certificado del servidor de destino. En el ejemplo de OpenSSL, bastará con un PKI simple de 2 niveles (certificado de CA raíz-> >certificado de servidor). Tendrá que rellenar la matriz "trusted_ca_data" con una versión binaria codificada en DER de su certificado de CA y actualizar la variable "trusted_ca_length" para reflejar la longitud real del certificado.

También necesitará el controlador de red para el hardware (reemplace el parámetro "nx_driver_xx" en la llamada a nx_ip_create).

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

/* Define the size of our application stack. */
#define     DEMO_STACK_SIZE             4096

/* Define the remote server IP address using NetX IP_ADDRESS macro. */
#define     REMOTE_SERVER_IP_ADDRESS    IP_ADDRESS(192, 168, 1, 1)

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS           IP_ADDRESS(192, 168, 1, 2)

/* Define the remote server port. 443 is the HTTPS default. */
#define     REMOTE_SERVER_PORT          443

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define an HTTP request to be sent to the HTTPS web server not defined here but
  represented by the ellipsis. */
UCHAR http_request[] = { "GET /example.html HTTP/1.1"  };

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];

/* Define the TLS Client thread.  */
ULONG             tls_client_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_client_thread;
void              client_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Client X.509 trusted root CA certificate, ASN.1 DER-
   encoded. A trusted certificate must be provided for TLS Client applications
   (unless X.509 authentication is disabled) or TLS will treat all certificates as
   untrusted and the handshake will fail.
*/

/* DER-encoded binary certificate, not defined here but represented by the ellipsis,
   for the sake of brevity. */
const UCHAR trusted_ca_data[] = { … };
const UINT trusted_ca_length = 0x574;

/* Define the application – initialize drivers and TCP/IP setup.
   NOTE: the variable “status” should be checked after every API call. Most error
         checking has been omitted for clarity. */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;

   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create a packet pool. Check status for errors. */
   status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                   NX_PACKET_POOL_SIZE);

   /* Create an IP instance for the specific target. Check status for errors. This
      call is not completely defined. Please see other demo files for proper usage
      of the nx_ip_create call. */
   status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                         DEVICE_IP_ADDRESS ,
                         0xFFFFFF00UL,
                         &pool_0, nx_driver_xx,
                         (UCHAR*)ip_thread_stack,
                         sizeof(ip_thread_stack),
                         1);

   /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
       errors. */
   status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

   /* Enable TCP traffic. Check status for errors. */
   status =  nx_tcp_enable(&ip_0);

   status =  nx_ip_fragment_enable(&ip_0);

   /* Initialize the NetX Secure TLS system.  */
   nx_secure_tls_initialize();

    /* Create the TLS client thread to start handling incoming requests. */
   tx_thread_create(&tls_client_thread, "TLS Client thread", client_thread_entry, 0,
                     tls_client_thread_stack, sizeof(tls_client_thread_stack),
                     16, 16, 4, TX_AUTO_START);
   return;
}

/* Thread to handle the TLS Client instance. */
void client_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG       actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;
ULONG server_ipv4_address;

    /* We are not using the thread input parameter so suppress compiler warning. */
    NX_PARAMETER_NOT_USED(thread_input);

   /* Ensure the IP instance has been initialized.  */
   status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

   /* Create a TCP socket to use for our TLS session.  */
   status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Client Socket",
                                  NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                  NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

   /* Create a TLS session for our socket. This sets up the TLS session object for
          later use */
   status =  nx_secure_tls_session_create(&tls_session,
                                          &nx_crypto_tls_ciphers_ecc,
                                          tls_crypto_metadata,
                                          sizeof(tls_crypto_metadata));

   /* Initialize ECC parameters for this session. */
   status = nx_secure_tls_ecc_initialize(&tls_session,
                                             nx_crypto_ecc_supported_groups,
                                             nx_crypto_ecc_supported_groups_size,
                                             nx_crypto_ecc_curves);

   /* Set the packet reassembly buffer for this TLS session. */
   status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                    sizeof(tls_packet_buffer));

   /* Initialize an X.509 certificate with our CA root certificate data. */
   nx_secure_x509_certificate_initialize(&certificate, trusted_ca_data,
                                         trusted_ca_length, NX_NULL, 0, NX_NULL, 0,
                                         NX_SECURE_X509_KEY_TYPE_NONE);

   /* Add the initialized certificate as a trusted root certificate. */
   nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);

   /* Setup this thread to open a connection on the TCP socket to a remote server.
      The IP address can be used directly or it can be obtained via DNS or other
      means.*/
   server_ipv4_address = REMOTE_SERVER_IP_ADDRESS;
   status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
                                         REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

   /* Start the TLS Session using the connected TCP socket. This function will
      ascertain from the TCP socket state that this is a TLS Client session. */
   status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                         NX_WAIT_FOREVER);

    /* Allocate a TLS packet to send an HTTP request over TLS (HTTPS). */
    status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                          NX_WAIT_FOREVER);

    /* Populate the packet with our HTTP request. */
    nx_packet_data_append(send_packet, http_request, sizeof(http_request), &pool_0,
                          NX_WAIT_FOREVER);


   /* Send the HTTP request over the TLS Session, turning it into HTTPS. */
   status = nx_secure_tls_session_send(&tls_session, send_packet, NX_WAIT_FOREVER);

   /* If the send fails, you must release the packet.  */
   if (status != NX_SUCCESS)
   {
         /* Release the packet since the packet was not sent.  */
         nx_packet_release(send_packet);
   }

   /* Receive the HTTP response and any data from the server. */
   status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
   NX_WAIT_FOREVER);
   if (status == NX_SUCCESS)
   {
       /* Extract the data we received from the remote server. */
       status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                             100,  &bytes);
        /* Display the response data. */
       receive_buffer[bytes] = 0;
       printf("Received data: %s\n", receive_buffer);

        /* Release the packet when done with it. */
       nx_packet_release(receive_packet);
   }

   /* End the TLS session now that we have received our HTTPS/HTML response. */
   status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

   /* Check for errors to make sure the session ended cleanly. */

   /* Disconnect the TCP socket. */
   status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

}
```

**Figura 1.1 Ejemplo de uso de NetX Secure con NetX**

## <a name="small-example-system-tls-web-server"></a>Sistema de ejemplo pequeño (servidor web TLS)

Un ejemplo de lo fácil que es usar NetX Secure se describe en la figura 1.1, que aparece a continuación y muestra un servidor web TLS sencillo (HTTPS).

Tenga en cuenta que, para ejecutar este ejemplo, necesitará un certificado X.509 para identificar el servidor en los clientes TLS. Para la mayoría de los exploradores web, un certificado autofirmado simple será suficiente. El explorador objetará que no puede autenticar el servidor y, en algunos casos, es posible que no pueda establecer una conexión TLS/HTTPS con el servidor<sup>3</sup>. Tendrá que rellenar la matriz "certificate_data" con una versión binaria codificada en DER de su certificado de servidor y actualizar la variable "certificate_length" para reflejar la longitud real del certificado. También debe rellenar la matriz "private_key" con una versión codificada en DER de la clave privada del certificado, con el formato PKCS#1 para la clave RSA y el RFC 5915 para las claves ECC. Rellene la variable "private_key_length" con la longitud real de los datos de la clave.

> [!IMPORTANT]
> Algunos exploradores (especialmente algunas versiones del explorador Chrome) pueden rechazar los certificados autofirmados. En este caso, puede crear un PKI de 2 niveles con un certificado de CA raíz que se usa para firmar el certificado de servidor. En esta situación, el certificado de CA raíz se instala como un certificado raíz de confianza en el explorador. !!! IMPORTANTE: Quite el certificado de CA raíz del explorador cuando haya terminado y no lo use para las aplicaciones de producción.

También necesitará el controlador de red para el hardware (reemplace el parámetro "nx_driver_xx" en la llamada a nx_ip_create).

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

#define     DEMO_STACK_SIZE         4096

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS             IP_ADDRESS(192, 168, 1, 2)

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];


/* Define the TLS Server thread.  */
ULONG             tls_server_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_server_thread;
void              server_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Server X.509 certificate, ASN.1 DER-encoded. Note that the
   certificate data and private key data is represented by an ellipsis for the sake
   of brevity.
*/
const UCHAR certificate_data[] = { … }; /* DER-encoded binary certificate. */
const UINT certificate_length = 0x574;

/* Binary data for the TLS Server Private Key, from private key
   file generated at the time of the X.509 certificate creation. ASN.1 DER-encoded. */
const UCHAR private_key[] = { … }; /* DER-encoded private key file (PKCS#1 RSA or ECC) */
const UINT private_key_length = 0x40;

/* Define some HTML data (web page) with an HTTPS header to serve to connecting
   clients. */
UCHAR html_data[] = { "HTTP/1.1 200 OK\r\n" \
        "Date: Tue, 19 May 2020 23:59:59 GMT\r\n" \
        "Content-Type: text/html\r\n" \
        "Content-Length: 200\r\n\r\n" \
        "<html>\r\n"\
        "<body>\r\n"\
        "<b>Hello NetX Secure User!</b>\r\n"\
        "This is a simple webpage\r\n"\
        "served up using NetX Secure!\r\n"\
        "</body>\r\n"\
        "</html>\r\n" };

/* Define the application – initialize drivers and TCP/IP setup.  */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;


    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool. Check status for errors. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                    (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                    NX_PACKET_POOL_SIZE);

    /* Create an IP instance for the specific target. Check status for errors. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                          DEVICE_IP_ADDRESS,
                          0xFFFFFF00UL,
                          &pool_0, nx_driver_xx,
                          (UCHAR*)ip_thread_stack,
                          sizeof(ip_thread_stack),
                          1);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable TCP traffic. Check status for errors. */
    status =  nx_tcp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS system.  */
    nx_secure_tls_initialize();

    /* Create the TLS server thread to start handling incoming requests. */
    tx_thread_create(&tls_server_thread, "TLS Server thread", server_thread_entry, 0,
                   tls_server_thread_stack, sizeof(tls_server_thread_stack),
                   16, 16, 4, TX_AUTO_START);
    return;
}

/* Thread to handle the TLS Server instance. */
void server_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG      actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;

    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

    /* Create a TCP socket to use for our TLS session.  */
    status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket",
                                   NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                   NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

    /* Create a TLS session for our socket.  */
    status =  nx_secure_tls_session_create(&tls_session,
                                        &nx_crypto_tls_ciphers_ecc,
                                        tls_crypto_metadata,
                                        sizeof(tls_crypto_metadata));

    status = nx_secure_tls_ecc_initialize(&tls_session,
                                          nx_crypto_ecc_supported_groups,
                                          nx_crypto_ecc_supported_groups_size,
                                          nx_crypto_ecc_curves);

     /* Set the packet reassembly buffer for this TLS session. */
     status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                      sizeof(tls_packet_buffer));

    /* Initialize an X.509 certificate and private ECC key for our TLS Session. */
    nx_secure_x509_certificate_initialize(&certificate, certificate_data, NX_NULL, 0,
                                          certificate_length, private_key,
                                          private_key_length,
                                          NX_SECURE_X509_KEY_TYPE_EC_DER);

    /* Add the initialized certificate as a local identity certificate. */
    nx_secure_tls_local_certificate_add(&tls_session, &certificate);


    /* Setup this thread to listen on the TCP socket.
       Port 443 is standard for HTTPS. */
    status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

    while(1)
     {
         /* Accept a client TCP socket connection.  */
         status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

         /* Start the TLS Session using the connected TCP socket. */
         status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                              NX_WAIT_FOREVER);

         /* Receive the HTTPS request. */
         status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
                                                NX_WAIT_FOREVER);

if (status == NX_SUCCESS)
      {
         /* Extract the HTTP request information from the HTTPS request. */
            status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                                  100, &bytes);
         /* Display the HTTP request data. */
            receive_buffer[bytes] = 0;
            printf("Received data: %s\n", receive_buffer);

         /* Release the packet when done with it */
            nx_packet_release(receive_packet);
      }

         /* Allocate a TLS packet to send HTML data back to client. */
         status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                                NX_WAIT_FOREVER);

         /* Populate the packet with our HTTP response and HTML web page data. */
         nx_packet_data_append(send_packet, html_data, sizeof(html_data), &pool_0,
                               NX_WAIT_FOREVER);

         /* Send the HTTP response over the TLS Session, turning it into HTTPS. */
         status = nx_secure_tls_session_send(&tls_session, send_packet,
                                                 NX_WAIT_FOREVER);

         /* If the send fails, you must release the packet.  */
         if (status != NX_SUCCESS)
         {
              /* Release the packet since it was not sent.  */
              nx_packet_release(send_packet);
         }

         /* End the TLS session now that we have sent our HTTPS/HTML response. */
         status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

         /* Check for errors to make sure the session ended cleanly! */

         /* Disconnect the TCP socket so we can be ready for the next request. */
         status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

         /* Unaccept the server socket.  */
         status =  nx_tcp_server_socket_unaccept(&tcp_socket);

         /* Setup server socket for listening again.  */
         status =  nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
     }
}
```

**Figura 1.2 Ejemplo de uso de NetX Secure con NetX**

## <a name="a-note-on-tls-session-error-recovery"></a>Nota sobre la recuperación de errores de la sesión de TLS

En los sistemas de ejemplo descritos anteriormente se muestran los esquemas básicos para un cliente y un servidor TLS, respectivamente, pero para mayor claridad, se omite el control de errores. Sin embargo, parte de la seguridad que proporciona TLS depende de la administración adecuada de las condiciones de error. Por lo general, los problemas más graves posibles se tratarán dentro de la propia pila de TLS, pero es importante que la aplicación TLS responda de manera adecuada a los errores de TLS que no se controlan dentro de la implementación de TLS y se recupere.

Con el fin de ilustrar la lógica necesaria para el control de errores adecuado, la siguiente función muestra una colección típica de servicios de API que se pueden usar para controlar correctamente los errores de TLS y restablecer de forma limpia el estado de TLS después de encontrar una condición de error. Aparte de la sección donde se indicó, la lógica se aplica a las instancias de cliente TLS y de servidor TLS.

Tenga en cuenta que las llamadas API más importantes de la función son a los servicios *nx_secure_tls_session_end*, lo que cierra limpiamente la sesión TLS o el protocolo de enlace, y *nx_secure_tls_session_reset*, que borra el estado de la sesión TLS para que se pueda reutilizar la instancia de la estructura de control tls_session para una nueva sesión TLS. Tenga en cuenta también que *nx_secure_tls_session_reset* no borra el estado configurado por el usuario, como los certificados o los búferes asignados, lo que permite que la sesión se vuelva a usar sin llamar a *nx_secure_tls_session_create* de nuevo. Para borrar completamente todo el estado de sesión TLS, se puede usar el servicio *nx_secure_tls_session_delete* en su lugar.

```C
/* Define a helper function to clean up a broken TLS session (to be called on any
   error from nx_secure_tls_session_start onwards). Note that the variables
   tls_session, tcp_socket, and ip_0 are global in the above examples. */
VOID tls_session_error_cleanup(VOID)
{
UINT status;
UINT alert_level, alert_value;

      /* If we got an error back from a TLS API call, there may be an alert from the
         remote host. Extract the alert level and value to print out. Note that the TLS
         API will return NX_SECURE_TLS_ALERT_RECEIVED (0x114) if an alert was received.
         For other error codes the alert value and level are not valid. */
      status = nx_secure_tls_session_alert_value_get(&tls_session, &alert_level,
                                                     &alert_value);
      if(status)
      {
         printf("Pointer error in getting alert value.\n");
      }
      else
      {
         printf("Alert recieved. Value: %d, Level: %d\n", alert_value, alert_level);
      }

      /* End the TLS session. This is required to properly shut down the TLS
         connection. */
      status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

      /* If the session did not shut down cleanly, this is a possible security issue. */
      if (status)
      {
         printf("Error in TLS session end: %x\n", status);
      }

      /* Reset the TLS session to re-use the control structure for the next connection.
         This API service resets the TLS session state but does not remove user-
         configured options such as certificates, PSKs, buffers, and cipher routines. */
      nx_secure_tls_session_reset(&tls_session);

      /* Disconnect the TCP socket, closing the connection. */
      status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket close: %x\n", status);
      }

   /* The following code applies only to a TLS server instance. */
   #if NX_SECURE_TLS_SERVER
      /* Unaccept the server socket.  */
      status =  nx_tcp_server_socket_unaccept(&tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket unaccept: %x\n", status);
      }

      /* Setup server socket for listening again.  */
      status =  nx_tcp_server_socket_relisten(&ip_0, DEVICE_SERVER_PORT, &tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket relisten: %x\n", status);
      }
#endif
} /* End function. */
```

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar NetX Secure. A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas:

| Definir | Significado |
|----------------------|------------------------------------------------|
| **NX_SECURE_DISABLE_ERROR_CHECKING**                | Si se define, esta opción quita la comprobación básica de errores de NetX Secure. Normalmente se utiliza después de depurar la aplicación. |
| **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**                  | Si se define, esta opción proporciona el módulo RSA máximo esperado, en bits. El valor predeterminado es 4096 para un módulo de 4096 bits. Otros valores pueden ser 3072, 2048 o 1024 (no recomendado). |
| **NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**        | Si se define, esta opción permite que TLS acepte certificados autofirmados de un host remoto. De forma predeterminada, TLS rechazará los certificados de servidor autofirmados como precaución de seguridad. Si se define esta macro, los certificados autofirmados se deben agregar al almacén de confianza para que se acepten. |
| **NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**      | Si se define, esta opción habilita la comprobación opcional de certificados de cliente X.509 para los servidores TLS<sup>4</sup>.  |
| **NX_SECURE_ENABLE_PSK_CIPHERSUITES**               | Si se define, esta opción habilita la funcionalidad de clave previamente compartida (PSK). No deshabilita los certificados digitales. |
| **NX_SECURE_TLS_CLIENT_DISABLED**                   | Si se define, esta opción quita todo el código de pila TLS relacionado con el modo de cliente TLS, lo que reduce el uso de código y datos. |
| **NX_SECURE_TLS_SERVER_DISABLED**                   | Si se define, esta opción quita todo el código de pila TLS relacionado con el modo de servidor TLS, lo que reduce el uso de código y datos.  |
| **NX_SECURE_DISABLE_ECC_CIPHERSUITE**               | Si se define, esta opción quita toda la lógica TLS para los conjuntos de cifrado de la criptografía de curva elíptica (ECC). Estos conjuntos de cifrado son opcionales en TLS 1.2 y versiones anteriores y, si se deshabilitan, se puede producir una reducción significativa del tamaño de los datos y el código.|
| **NX_SECURE_TLS_ENABLE_TLS_1_3**                    | Si se define, esta opción habilita el modo TLSv1.3. TLS 1.3 es la versión más reciente de TLS y está deshabilitada de forma predeterminada. |
| **NX_SECURE_TLS_ENABLE_TLS_1_0**                    | Si se define, esta opción habilita el modo heredado de TLSv1.0. TLSv1.0 se considera obsoleto, por lo que solo se debe habilitar para la compatibilidad con versiones anteriores de aplicaciones antiguas. |
| **NX_SECURE_TLS_ENABLE_TLS_1_1**                    | Si se define, esta opción habilita el modo heredado de TLSv1.1. TLSv1.1 se considera obsoleto, por lo que solo se debe habilitar para la compatibilidad con versiones anteriores de aplicaciones antiguas. |
| **NX_SECURE_TLS_DISABLE_TLS_1_1**                   | Si se define, esta opción deshabilita el modo TLSv1.1. Está definida de manera predeterminada. TLSv1.1 se deshabilita para usar solo TLSv1.2<sup>5</sup> que es más seguro.  |
| **NX_SECURE_X509_STRICT_NAME_COMPARE**              | Si se define, esta opción habilita la comparación estricta de nombres distintivos para los certificados X.509 en la búsqueda y comprobación de certificados. De forma predeterminada, solo se comparan los campos de nombre común de los nombres distintivos.|
| **NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES** | Si se define, esta opción habilita los campos opcionales de nombre distintivo de X.509, a costa del uso de memoria adicional para los certificados X.509. |

4. Tenga en cuenta que esta opción solo permite que el código se vincule a la aplicación. La característica deberá habilitarse con el servicio de API nx_secure_tls_session_client_verify_enable o configurarse con nx_secure_tls_session_x509_client_verify_configure para poder usar la comprobación de certificados de cliente.

5. Tenga en cuenta que también es posible deshabilitar TLSv1.2 si solo se usa TLS 1.0 o TLS 1.1. Sin embargo, no es recomendable y no se admite directamente.
