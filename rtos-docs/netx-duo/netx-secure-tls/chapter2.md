---
title: 'Capítulo 2: Instalación y uso de Azure RTOS NetX Secure'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX Secure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b3ef82bd113518b35105fb2eefe23bd3e755ca06
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815354"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a><span data-ttu-id="08067-103">Capítulo 2: Instalación y uso de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-103">Chapter 2 - Installation and use of Azure RTOS NetX Secure</span></span>

<span data-ttu-id="08067-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente Azure RTOS NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="08067-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Secure component.</span></span>

## <a name="product-version-number"></a><span data-ttu-id="08067-105">Número de versión del producto</span><span class="sxs-lookup"><span data-stu-id="08067-105">Product Version Number</span></span>

<span data-ttu-id="08067-106">El usuario puede comprobar el número de versión del producto mediante la búsqueda de los siguientes símbolos en nx_secure_tls.h:</span><span class="sxs-lookup"><span data-stu-id="08067-106">User may verify the product version number by finding the following symbols in nx_secure_tls.h:</span></span>

<span data-ttu-id="08067-107">***NETX_SECURE_MAJOR_VERSION***</span><span class="sxs-lookup"><span data-stu-id="08067-107">***NETX_SECURE_MAJOR_VERSION***</span></span>

<span data-ttu-id="08067-108">***NETX_SECURE_MINOR_VERSION***</span><span class="sxs-lookup"><span data-stu-id="08067-108">***NETX_SECURE_MINOR_VERSION***</span></span>

<span data-ttu-id="08067-109">Las versiones de Service Pack tienen el siguiente símbolo definido para indicar el número de Service Pack:</span><span class="sxs-lookup"><span data-stu-id="08067-109">Service Pack releases has the following symbol defined to indicate the service pack number:</span></span>

<span data-ttu-id="08067-110">***NETX_SECURE_SERVICE_PACK_VERSION***</span><span class="sxs-lookup"><span data-stu-id="08067-110">***NETX_SECURE_SERVICE_PACK_VERSION***</span></span>

## <a name="product-distribution"></a><span data-ttu-id="08067-111">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="08067-111">Product Distribution</span></span>

<span data-ttu-id="08067-112">NetX Secure está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="08067-112">NetX Secure is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="08067-113">El paquete incluye archivos de código fuente, archivos de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="08067-113">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="08067-114">**nx_secure_tls_api.h** Archivo de encabezado de API pública para TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-114">**nx_secure_tls_api.h** Public API header file for NetX Secure TLS</span></span>
- <span data-ttu-id="08067-115">**nx_secure_tls_user.h** Archivo de encabezado definido por el usuario para TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-115">**nx_secure_tls_user.h** User defines header file for NetX Secure TLS</span></span>
- <span data-ttu-id="08067-116">**nx_secure_tls_port.h** Definiciones específicas de la plataforma para NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-116">**nx_secure_tls_port.h** Platform-specific definitions for NetX Secure</span></span>
- <span data-ttu-id="08067-117">**nx_secure_tls.h** Archivo de encabezado para TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-117">**nx_secure_tls.h** Header file for NetX Secure TLS</span></span>
- <span data-ttu-id="08067-118">**nx_secure_tls&#42;.c/h** Archivos de código fuente C/H para TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-118">**nx_secure_tls&#42;.c/h** C/H Source files for NetX Secure TLS</span></span>
- <span data-ttu-id="08067-119">**nx_crypto&#42;.c/h** Archivos de código fuente C/H para la criptografía de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-119">**nx_crypto&#42;.c/h** C/H Source files for NetX Secure Cryptography</span></span>
- <span data-ttu-id="08067-120">**nx_secure_x509&#42;.c/h** Archivos de código fuente C/H para certificados digitales X.509</span><span class="sxs-lookup"><span data-stu-id="08067-120">**nx_secure_x509&#42;.c/h** C/H Source files for X.509 digital certificates.</span></span>
- <span data-ttu-id="08067-121">**demo_netx_secure_tls.c** Archivo de código fuente C para la demostración de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-121">**demo_netx_secure_tls.c** C Source file for NetX Secure TLS Demo</span></span>
- <span data-ttu-id="08067-122">**NetX_Secure_User_Guide.pdf** Descripción en PDF del producto NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-122">**NetX_Secure_User_Guide.pdf** PDF description of NetX Secure product</span></span>

> [!NOTE]
> <span data-ttu-id="08067-123">Los archivos nx_crypto\* se proporcionan para distintas plataformas de hardware en un subdirectorio del directorio primario de NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="08067-123">The nx_crypto\* files are provided for different hardware platforms in a subdirectory of the NetX Secure parent directory.</span></span>

## <a name="netx-secure-installation"></a><span data-ttu-id="08067-124">Instalación de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-124">NetX Secure Installation</span></span>

<span data-ttu-id="08067-125">Para usar NetX Secure, toda la distribución que se menciona anteriormente debe copiarse en el mismo directorio en el que se ha instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="08067-125">In order to use NetX Secure, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="08067-126">Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\NetX*", los directorios \*nx_secure \**.*</span><span class="sxs-lookup"><span data-stu-id="08067-126">For example, if NetX is installed in the directory "*\threadx\arm7\NetX*" then the *nx_secure\*\*.*</span></span> <span data-ttu-id="08067-127">deben copiarse en " *\threadx\arm7\NetXSecure*".</span><span class="sxs-lookup"><span data-stu-id="08067-127">directories should be copied into "*\threadx\arm7\NetXSecure*".</span></span>

## <a name="using-netx-secure"></a><span data-ttu-id="08067-128">Uso de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="08067-128">Using NetX Secure</span></span>

<span data-ttu-id="08067-129">Usar TLS de NetX Secure es sencillo.</span><span class="sxs-lookup"><span data-stu-id="08067-129">Using NetX Secure TLS is straightforward.</span></span> <span data-ttu-id="08067-130">Básicamente, el código de la aplicación debe incluir *nx_secure_tls_api.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX.</span><span class="sxs-lookup"><span data-stu-id="08067-130">Basically, the application code must include *nx_secure_tls_api.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="08067-131">Después de incluir *nx_secure_tls_api.h*, el código de la aplicación puede realizar las llamadas de función DHCP especificadas más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="08067-131">Once *nx_secure_tls_api.h* is included, the application code is then able to make the NetX Secure function calls specified later in this guide.</span></span> <span data-ttu-id="08067-132">La aplicación también debe importar los archivos *nx_secure\*\*.*</span><span class="sxs-lookup"><span data-stu-id="08067-132">The application must also import the *nx_secure\*\*.*</span></span> <span data-ttu-id="08067-133">a una biblioteca de NetXSecure y los archivos específicos de la plataforma *nx_crypto\*\*.*</span><span class="sxs-lookup"><span data-stu-id="08067-133">files into a NetXSecure library, and the platform-specific *nx_crypto\*\*.*</span></span> <span data-ttu-id="08067-134">a una biblioteca de NetXCrypto.</span><span class="sxs-lookup"><span data-stu-id="08067-134">files into a NetXCrypto library.</span></span>

## <a name="small-example-system-tls-client"></a><span data-ttu-id="08067-135">Sistema de ejemplo pequeño (cliente TLS)</span><span class="sxs-lookup"><span data-stu-id="08067-135">Small Example System (TLS Client)</span></span>

<span data-ttu-id="08067-136">Un ejemplo de lo fácil que es usar NetX Secure se describe en la figura 1.1, que aparece a continuación.</span><span class="sxs-lookup"><span data-stu-id="08067-136">An example of how easy it is to use NetX Secure is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="08067-137">Muestra un cliente TLS simple, que usa módulos criptográficos de software (no específicos de hardware) para el cifrado.</span><span class="sxs-lookup"><span data-stu-id="08067-137">This demonstrates a simple TLS Client, using software crypto modules (not hardware specific) for encryption.</span></span> <span data-ttu-id="08067-138">Está diseñado para funcionar con el servidor de eco inverso OpenSSL (openssl s_server -rev).</span><span class="sxs-lookup"><span data-stu-id="08067-138">It is designed to work with the OpenSSL reverse-echo server (openssl s_server -rev).</span></span>

<span data-ttu-id="08067-139">Tenga en cuenta que, para poder ejecutar este ejemplo, necesitará un certificado de CA X.509 para autenticar el certificado del servidor de destino.</span><span class="sxs-lookup"><span data-stu-id="08067-139">Note that in order to run this example, you will need an X.509 CA certificate to authenticate your target server's certificate.</span></span> <span data-ttu-id="08067-140">En el ejemplo de OpenSSL, bastará con un PKI simple de 2 niveles (certificado de CA raíz-> >certificado de servidor).</span><span class="sxs-lookup"><span data-stu-id="08067-140">For the OpenSSL example, a simple 2-level PKI (root CA certificate-> >server certificate) will suffice.</span></span> <span data-ttu-id="08067-141">Tendrá que rellenar la matriz "trusted_ca_data" con una versión binaria codificada en DER de su certificado de CA y actualizar la variable "trusted_ca_length" para reflejar la longitud real del certificado.</span><span class="sxs-lookup"><span data-stu-id="08067-141">You will need to fill in the "trusted_ca_data" array with a DER-encoded binary version of your CA certificate and update the "trusted_ca_length" variable to reflect your certificate's actual length.</span></span>

<span data-ttu-id="08067-142">También necesitará el controlador de red para el hardware (reemplace el parámetro "nx_driver_xx" en la llamada a nx_ip_create).</span><span class="sxs-lookup"><span data-stu-id="08067-142">You will also need the network driver for your hardware (replace "nx_driver_xx" parameter in nx_ip_create call).</span></span>

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

<span data-ttu-id="08067-143">**Figura 1.1 Ejemplo de uso de NetX Secure con NetX**</span><span class="sxs-lookup"><span data-stu-id="08067-143">**Figure 1.1 Example of NetX Secure use with NetX**</span></span>

## <a name="small-example-system-tls-web-server"></a><span data-ttu-id="08067-144">Sistema de ejemplo pequeño (servidor web TLS)</span><span class="sxs-lookup"><span data-stu-id="08067-144">Small Example System (TLS Web Server)</span></span>

<span data-ttu-id="08067-145">Un ejemplo de lo fácil que es usar NetX Secure se describe en la figura 1.1, que aparece a continuación y muestra un servidor web TLS sencillo (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="08067-145">An example of how easy it is to use NetX Secure is described in Figure 1.1, which appears below and demonstrates a simple TLS Web Server (HTTPS).</span></span>

<span data-ttu-id="08067-146">Tenga en cuenta que, para ejecutar este ejemplo, necesitará un certificado X.509 para identificar el servidor en los clientes TLS.</span><span class="sxs-lookup"><span data-stu-id="08067-146">Note that in order to run this example, you will need an X.509 certificate to identify your server to TLS clients.</span></span> <span data-ttu-id="08067-147">Para la mayoría de los exploradores web, un certificado autofirmado simple será suficiente.</span><span class="sxs-lookup"><span data-stu-id="08067-147">For most web browers a simple self-signed certificate should be sufficient.</span></span> <span data-ttu-id="08067-148">El explorador objetará que no puede autenticar el servidor y, en algunos casos, es posible que no pueda establecer una conexión TLS/HTTPS con el servidor<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="08067-148">Your browser will complain about not being able to authenticate the server and in some cases may be unable to establish a TLS/HTTPS connection to your server<sup>3</sup>.</span></span> <span data-ttu-id="08067-149">Tendrá que rellenar la matriz "certificate_data" con una versión binaria codificada en DER de su certificado de servidor y actualizar la variable "certificate_length" para reflejar la longitud real del certificado.</span><span class="sxs-lookup"><span data-stu-id="08067-149">You will need to fill in the "certificate_data" array with a DER-encoded binary version of your server certificate and update the "certificate_length" variable to reflect your certificate's actual length.</span></span> <span data-ttu-id="08067-150">También debe rellenar la matriz "private_key" con una versión codificada en DER de la clave privada del certificado, con el formato PKCS#1 para la clave RSA y el RFC 5915 para las claves ECC.</span><span class="sxs-lookup"><span data-stu-id="08067-150">You also need to fill in the "private_key" array with a DER-encoded version of your certificate's private key, formatted using PKCS#1 for RSA key and RFC 5915 for ECC keys.</span></span> <span data-ttu-id="08067-151">Rellene la variable "private_key_length" con la longitud real de los datos de la clave.</span><span class="sxs-lookup"><span data-stu-id="08067-151">Fill in the "private_key_length" variable with the actual length of your key data.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08067-152">Algunos exploradores (especialmente algunas versiones del explorador Chrome) pueden rechazar los certificados autofirmados.</span><span class="sxs-lookup"><span data-stu-id="08067-152">Some browsers (particularly some versions of the Chrome browser) may reject self-signed certificates.</span></span> <span data-ttu-id="08067-153">En este caso, puede crear un PKI de 2 niveles con un certificado de CA raíz que se usa para firmar el certificado de servidor.</span><span class="sxs-lookup"><span data-stu-id="08067-153">In this case you can create a 2-level PKI with a root CA certificate that is used to sign your server certificate.</span></span> <span data-ttu-id="08067-154">En esta situación, el certificado de CA raíz se instala como un certificado raíz de confianza en el explorador.</span><span class="sxs-lookup"><span data-stu-id="08067-154">In this situation, the root CA certificate is installed as a trusted root certificate in your browser.</span></span> <span data-ttu-id="08067-155">!!!</span><span class="sxs-lookup"><span data-stu-id="08067-155">!!!</span></span> <span data-ttu-id="08067-156">IMPORTANTE: Quite el certificado de CA raíz del explorador cuando haya terminado y no lo use para las aplicaciones de producción.</span><span class="sxs-lookup"><span data-stu-id="08067-156">IMPORTANT – remove your root CA certificate from your browser when done and do not use it for any production applications !!!</span></span>

<span data-ttu-id="08067-157">También necesitará el controlador de red para el hardware (reemplace el parámetro "nx_driver_xx" en la llamada a nx_ip_create).</span><span class="sxs-lookup"><span data-stu-id="08067-157">You will also need the network driver for your hardware (replace "nx_driver_xx" parameter in nx_ip_create call).</span></span>

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

<span data-ttu-id="08067-158">**Figura 1.2 Ejemplo de uso de NetX Secure con NetX**</span><span class="sxs-lookup"><span data-stu-id="08067-158">**Figure 1.2 Example of NetX Secure use with NetX**</span></span>

## <a name="a-note-on-tls-session-error-recovery"></a><span data-ttu-id="08067-159">Nota sobre la recuperación de errores de la sesión de TLS</span><span class="sxs-lookup"><span data-stu-id="08067-159">A Note on TLS Session Error Recovery</span></span>

<span data-ttu-id="08067-160">En los sistemas de ejemplo descritos anteriormente se muestran los esquemas básicos para un cliente y un servidor TLS, respectivamente, pero para mayor claridad, se omite el control de errores.</span><span class="sxs-lookup"><span data-stu-id="08067-160">The example systems described above show the basic outlines for a TLS Client and Server, respectively, but for clarity the error handling is omitted.</span></span> <span data-ttu-id="08067-161">Sin embargo, parte de la seguridad que proporciona TLS depende de la administración adecuada de las condiciones de error.</span><span class="sxs-lookup"><span data-stu-id="08067-161">However, part of the security TLS provides is dependent on the proper handling of error conditions.</span></span> <span data-ttu-id="08067-162">Por lo general, los problemas más graves posibles se tratarán dentro de la propia pila de TLS, pero es importante que la aplicación TLS responda de manera adecuada a los errores de TLS que no se controlan dentro de la implementación de TLS y se recupere.</span><span class="sxs-lookup"><span data-stu-id="08067-162">Generally, the most serious potential problems will be handled within the TLS stack itself, but it is important for the TLS application to properly respond to and recover from TLS errors that are not handled within the TLS implementation.</span></span>

<span data-ttu-id="08067-163">Con el fin de ilustrar la lógica necesaria para el control de errores adecuado, la siguiente función muestra una colección típica de servicios de API que se pueden usar para controlar correctamente los errores de TLS y restablecer de forma limpia el estado de TLS después de encontrar una condición de error.</span><span class="sxs-lookup"><span data-stu-id="08067-163">In order to illustrate the necessary logic for proper error handling, the following function demonstrates a typical collection of API services that can be used to properly handle TLS errors and cleanly reset the TLS state after an error condition is encountered.</span></span> <span data-ttu-id="08067-164">Aparte de la sección donde se indicó, la lógica se aplica a las instancias de cliente TLS y de servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="08067-164">Other than the section where noted, the logic applies to both TLS Client and TLS Server instances.</span></span>

<span data-ttu-id="08067-165">Tenga en cuenta que las llamadas API más importantes de la función son a los servicios *nx_secure_tls_session_end*, lo que cierra limpiamente la sesión TLS o el protocolo de enlace, y *nx_secure_tls_session_reset*, que borra el estado de la sesión TLS para que se pueda reutilizar la instancia de la estructura de control tls_session para una nueva sesión TLS.</span><span class="sxs-lookup"><span data-stu-id="08067-165">Note that the most important API calls in the function are to the services *nx_secure_tls_session_end*, which cleanly closes the TLS session or handshake, and *nx_secure_tls_session_reset*, which clears the TLS session state so the tls_session control structure instance can be reused for a new TLS session.</span></span> <span data-ttu-id="08067-166">Tenga en cuenta también que *nx_secure_tls_session_reset* no borra el estado configurado por el usuario, como los certificados o los búferes asignados, lo que permite que la sesión se vuelva a usar sin llamar a *nx_secure_tls_session_create* de nuevo.</span><span class="sxs-lookup"><span data-stu-id="08067-166">Also note that *nx_secure_tls_session_reset* does not clear the user-configured state such as certificates or assigned buffers, allowing the session to be reused without calling *nx_secure_tls_session_create* again.</span></span> <span data-ttu-id="08067-167">Para borrar completamente todo el estado de sesión TLS, se puede usar el servicio *nx_secure_tls_session_delete* en su lugar.</span><span class="sxs-lookup"><span data-stu-id="08067-167">To completely clear all TLS session state, the service *nx_secure_tls_session_delete* may be used instead.</span></span>

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

## <a name="configuration-options"></a><span data-ttu-id="08067-168">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="08067-168">Configuration Options</span></span>

<span data-ttu-id="08067-169">Hay varias opciones de configuración para compilar NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="08067-169">There are several configuration options for building NetX Secure.</span></span> <span data-ttu-id="08067-170">A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas:</span><span class="sxs-lookup"><span data-stu-id="08067-170">Following is a list of all options, where each is described in detail:</span></span>

| <span data-ttu-id="08067-171">Definir</span><span class="sxs-lookup"><span data-stu-id="08067-171">Define</span></span> | <span data-ttu-id="08067-172">Significado</span><span class="sxs-lookup"><span data-stu-id="08067-172">Meaning</span></span> |
|----------------------|------------------------------------------------|
| <span data-ttu-id="08067-173">**NX_SECURE_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="08067-173">**NX_SECURE_DISABLE_ERROR_CHECKING**</span></span>                | <span data-ttu-id="08067-174">Si se define, esta opción quita la comprobación básica de errores de NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="08067-174">Defined, this option removes the basic NetX Secure error checking.</span></span> <span data-ttu-id="08067-175">Normalmente se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="08067-175">It is typically used after the application has been debugged.</span></span> |
| <span data-ttu-id="08067-176">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span><span class="sxs-lookup"><span data-stu-id="08067-176">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**</span></span>                  | <span data-ttu-id="08067-177">Si se define, esta opción proporciona el módulo RSA máximo esperado, en bits.</span><span class="sxs-lookup"><span data-stu-id="08067-177">Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="08067-178">El valor predeterminado es 4096 para un módulo de 4096 bits.</span><span class="sxs-lookup"><span data-stu-id="08067-178">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="08067-179">Otros valores pueden ser 3072, 2048 o 1024 (no recomendado).</span><span class="sxs-lookup"><span data-stu-id="08067-179">Other values can be 3072, 2048, or 1024 (not recommended).</span></span> |
| <span data-ttu-id="08067-180">**NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**</span><span class="sxs-lookup"><span data-stu-id="08067-180">**NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**</span></span>        | <span data-ttu-id="08067-181">Si se define, esta opción permite que TLS acepte certificados autofirmados de un host remoto.</span><span class="sxs-lookup"><span data-stu-id="08067-181">Defined, this option allows TLS to accept self-signed certificates from a remote host.</span></span> <span data-ttu-id="08067-182">De forma predeterminada, TLS rechazará los certificados de servidor autofirmados como precaución de seguridad.</span><span class="sxs-lookup"><span data-stu-id="08067-182">By default, TLS will reject self-signed server certificates as a security precaution.</span></span> <span data-ttu-id="08067-183">Si se define esta macro, los certificados autofirmados se deben agregar al almacén de confianza para que se acepten.</span><span class="sxs-lookup"><span data-stu-id="08067-183">If this macro is defined, self-signed certificates must still be added to the trusted store to be accepted.</span></span> |
| <span data-ttu-id="08067-184">**NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**</span><span class="sxs-lookup"><span data-stu-id="08067-184">**NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**</span></span>      | <span data-ttu-id="08067-185">Si se define, esta opción habilita la comprobación opcional de certificados de cliente X.509 para los servidores TLS<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="08067-185">Defined, this option enables the optional X.509 Client Certificate Verification for TLS Servers<sup>4</sup>.</span></span>  |
| <span data-ttu-id="08067-186">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span><span class="sxs-lookup"><span data-stu-id="08067-186">**NX_SECURE_ENABLE_PSK_CIPHERSUITES**</span></span>               | <span data-ttu-id="08067-187">Si se define, esta opción habilita la funcionalidad de clave previamente compartida (PSK).</span><span class="sxs-lookup"><span data-stu-id="08067-187">Defined, this option enables Pre-Shared Key (PSK) functionality.</span></span> <span data-ttu-id="08067-188">No deshabilita los certificados digitales.</span><span class="sxs-lookup"><span data-stu-id="08067-188">It does not disable digital certificates.</span></span> |
| <span data-ttu-id="08067-189">**NX_SECURE_TLS_CLIENT_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="08067-189">**NX_SECURE_TLS_CLIENT_DISABLED**</span></span>                   | <span data-ttu-id="08067-190">Si se define, esta opción quita todo el código de pila TLS relacionado con el modo de cliente TLS, lo que reduce el uso de código y datos.</span><span class="sxs-lookup"><span data-stu-id="08067-190">Defined, this option removes all TLS stack code related to TLS Client mode, reducing code and data usage.</span></span> |
| <span data-ttu-id="08067-191">**NX_SECURE_TLS_SERVER_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="08067-191">**NX_SECURE_TLS_SERVER_DISABLED**</span></span>                   | <span data-ttu-id="08067-192">Si se define, esta opción quita todo el código de pila TLS relacionado con el modo de servidor TLS, lo que reduce el uso de código y datos.</span><span class="sxs-lookup"><span data-stu-id="08067-192">Defined, this option removes all TLS stack code related to TLS Server mode, reducing code and data usage.</span></span>  |
| <span data-ttu-id="08067-193">**NX_SECURE_DISABLE_ECC_CIPHERSUITE**</span><span class="sxs-lookup"><span data-stu-id="08067-193">**NX_SECURE_DISABLE_ECC_CIPHERSUITE**</span></span>               | <span data-ttu-id="08067-194">Si se define, esta opción quita toda la lógica TLS para los conjuntos de cifrado de la criptografía de curva elíptica (ECC).</span><span class="sxs-lookup"><span data-stu-id="08067-194">Defined, this option removes all TLS logic for Elliptic Curve Cryptography (ECC) ciphersuites.</span></span> <span data-ttu-id="08067-195">Estos conjuntos de cifrado son opcionales en TLS 1.2 y versiones anteriores y, si se deshabilitan, se puede producir una reducción significativa del tamaño de los datos y el código.</span><span class="sxs-lookup"><span data-stu-id="08067-195">These ciphersuites are optional in TLS 1.2 and earlier and disabling them can result in significant code and data size reduction.</span></span>|
| <span data-ttu-id="08067-196">**NX_SECURE_TLS_ENABLE_TLS_1_3**</span><span class="sxs-lookup"><span data-stu-id="08067-196">**NX_SECURE_TLS_ENABLE_TLS_1_3**</span></span>                    | <span data-ttu-id="08067-197">Si se define, esta opción habilita el modo TLSv1.3.</span><span class="sxs-lookup"><span data-stu-id="08067-197">Defined, this option enables TLSv1.3 mode.</span></span> <span data-ttu-id="08067-198">TLS 1.3 es la versión más reciente de TLS y está deshabilitada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="08067-198">TLS 1.3 is the newest version of TLS and is disabled by default.</span></span> |
| <span data-ttu-id="08067-199">**NX_SECURE_TLS_ENABLE_TLS_1_0**</span><span class="sxs-lookup"><span data-stu-id="08067-199">**NX_SECURE_TLS_ENABLE_TLS_1_0**</span></span>                    | <span data-ttu-id="08067-200">Si se define, esta opción habilita el modo heredado de TLSv1.0.</span><span class="sxs-lookup"><span data-stu-id="08067-200">Defined, this option enables the legacy TLSv1.0 mode.</span></span> <span data-ttu-id="08067-201">TLSv1.0 se considera obsoleto, por lo que solo se debe habilitar para la compatibilidad con versiones anteriores de aplicaciones antiguas.</span><span class="sxs-lookup"><span data-stu-id="08067-201">TLSv1.0 is considered obsolete so it should only be enabled for backward-compatibility with older applications.</span></span> |
| <span data-ttu-id="08067-202">**NX_SECURE_TLS_ENABLE_TLS_1_1**</span><span class="sxs-lookup"><span data-stu-id="08067-202">**NX_SECURE_TLS_ENABLE_TLS_1_1**</span></span>                    | <span data-ttu-id="08067-203">Si se define, esta opción habilita el modo heredado de TLSv1.1.</span><span class="sxs-lookup"><span data-stu-id="08067-203">Defined, this option enables the legacy TLSv1.1 mode.</span></span> <span data-ttu-id="08067-204">TLSv1.1 se considera obsoleto, por lo que solo se debe habilitar para la compatibilidad con versiones anteriores de aplicaciones antiguas.</span><span class="sxs-lookup"><span data-stu-id="08067-204">TLSv1.1 is considered obsolete so it should only be enabled for backward-compatibility with older applications.</span></span> |
| <span data-ttu-id="08067-205">**NX_SECURE_TLS_DISABLE_TLS_1_1**</span><span class="sxs-lookup"><span data-stu-id="08067-205">**NX_SECURE_TLS_DISABLE_TLS_1_1**</span></span>                   | <span data-ttu-id="08067-206">Si se define, esta opción deshabilita el modo TLSv1.1.</span><span class="sxs-lookup"><span data-stu-id="08067-206">Defined, this option disables TLSv1.1 mode.</span></span> <span data-ttu-id="08067-207">Está definida de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="08067-207">It is defined by default.</span></span> <span data-ttu-id="08067-208">TLSv1.1 se deshabilita para usar solo TLSv1.2<sup>5</sup> que es más seguro.</span><span class="sxs-lookup"><span data-stu-id="08067-208">TLSv1.1 is disabled in favor of using only the more-secure TLSv1.2<sup>5</sup>.</span></span>  |
| <span data-ttu-id="08067-209">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span><span class="sxs-lookup"><span data-stu-id="08067-209">**NX_SECURE_X509_STRICT_NAME_COMPARE**</span></span>              | <span data-ttu-id="08067-210">Si se define, esta opción habilita la comparación estricta de nombres distintivos para los certificados X.509 en la búsqueda y comprobación de certificados.</span><span class="sxs-lookup"><span data-stu-id="08067-210">Defined, this option enables strict distinguished name comparison for X.509 certificates for certificate searching and verification.</span></span> <span data-ttu-id="08067-211">De forma predeterminada, solo se comparan los campos de nombre común de los nombres distintivos.</span><span class="sxs-lookup"><span data-stu-id="08067-211">The default is to only compare the Common Name fields of the Distinguished Names.</span></span>|
| <span data-ttu-id="08067-212">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span><span class="sxs-lookup"><span data-stu-id="08067-212">**NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES**</span></span> | <span data-ttu-id="08067-213">Si se define, esta opción habilita los campos opcionales de nombre distintivo de X.509, a costa del uso de memoria adicional para los certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="08067-213">Defined, this option enables the optional X.509 Distinguished Name fields, at the expense of extra memory use for X.509 certificates.</span></span> |

4. <span data-ttu-id="08067-214">Tenga en cuenta que esta opción solo permite que el código se vincule a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="08067-214">Note that this option only enables the code to be linked into the application.</span></span> <span data-ttu-id="08067-215">La característica deberá habilitarse con el servicio de API nx_secure_tls_session_client_verify_enable o configurarse con nx_secure_tls_session_x509_client_verify_configure para poder usar la comprobación de certificados de cliente.</span><span class="sxs-lookup"><span data-stu-id="08067-215">The feature will need to be enabled with the API service nx_secure_tls_session_client_verify_enable or configured using nx_secure_tls_session_x509_client_verify_configure in order to use Client Certificate Verification.</span></span>

5. <span data-ttu-id="08067-216">Tenga en cuenta que también es posible deshabilitar TLSv1.2 si solo se usa TLS 1.0 o TLS 1.1.</span><span class="sxs-lookup"><span data-stu-id="08067-216">Note that it is also possible to disable TLSv1.2 if using TLS 1.0 or TLS 1.1 only.</span></span> <span data-ttu-id="08067-217">Sin embargo, no es recomendable y no se admite directamente.</span><span class="sxs-lookup"><span data-stu-id="08067-217">However, this is not recommended and not directly supported.</span></span>
