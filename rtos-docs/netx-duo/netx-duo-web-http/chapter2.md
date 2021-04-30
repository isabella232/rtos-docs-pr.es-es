---
title: 'Capítulo 2: Instalación y uso de HTTP y HTTPS'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX Web HTTP.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99e649781588b56e72b509c2aa077c38423379d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814522"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a><span data-ttu-id="a3a6d-103">Capítulo 2: Instalación y uso de HTTP y HTTPS</span><span class="sxs-lookup"><span data-stu-id="a3a6d-103">Chapter 2 - Installation and use of HTTP and HTTPS</span></span>

<span data-ttu-id="a3a6d-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Web HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="a3a6d-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="a3a6d-105">Product Distribution</span></span>

<span data-ttu-id="a3a6d-106">HTTP para NetX está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="a3a6d-106">HTTP for NetX is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="a3a6d-107">El paquete incluye tres archivos de código fuente, dos archivos de inclusión y un archivo que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="a3a6d-107">The package includes three source files, two include files, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="a3a6d-108">**nx_web_http_common.h** Archivo de encabezado común para NetX Web HTTP</span><span class="sxs-lookup"><span data-stu-id="a3a6d-108">**nx_web_http_common.h** Common header file for NetX Web HTTP</span></span>
- <span data-ttu-id="a3a6d-109">**nx_web_http_client.h** Archivo de encabezado para el cliente HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="a3a6d-109">**nx_web_http_client.h** Header file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="a3a6d-110">**nx_web_http_server.h** Archivo de encabezado para el servidor HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="a3a6d-110">**nx_web_http_server.h** Header file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="a3a6d-111">**nx_web_http_client.c** Archivo de código fuente C para el cliente HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="a3a6d-111">**nx_web_http_client.c** C Source file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="a3a6d-112">**nx_web_http_server.** Archivo de código fuente C para el servidor HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="a3a6d-112">**nx_web_http_server.c** C Source file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="a3a6d-113">**nx_tcpserver. c** Archivo de código fuente C para varios sockets TCP</span><span class="sxs-lookup"><span data-stu-id="a3a6d-113">**nx_tcpserver.c** C Source file for multiple TCP sockets</span></span>
- <span data-ttu-id="a3a6d-114">**nx_tcpserver.h** Archivo de encabezado para definir símbolos de servidor HTTPS</span><span class="sxs-lookup"><span data-stu-id="a3a6d-114">**nx_tcpserver.h** Header file for defining HTTPS Server symbols</span></span>
- <span data-ttu-id="a3a6d-115">**nx_md5.c** Algoritmos de síntesis MD5</span><span class="sxs-lookup"><span data-stu-id="a3a6d-115">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="a3a6d-116">**filex_stub.h** Archivo de código auxiliar si FileX no está presente</span><span class="sxs-lookup"><span data-stu-id="a3a6d-116">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="a3a6d-117">**nx_web_http.pdf** Descripción de HTTP para NetX Web</span><span class="sxs-lookup"><span data-stu-id="a3a6d-117">**nx_web_http.pdf** Description of HTTP for NetX Web</span></span>
- <span data-ttu-id="a3a6d-118">**demo_netx_web_http.c** Demostración de NetX Web HTTP</span><span class="sxs-lookup"><span data-stu-id="a3a6d-118">**demo_netx_web_http.c** NetX Web HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="a3a6d-119">instalación de HTTP</span><span class="sxs-lookup"><span data-stu-id="a3a6d-119">HTTP Installation</span></span>

<span data-ttu-id="a3a6d-120">Para usar NetX Web HTTP, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-120">In order to use NetX Web HTTP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="a3a6d-121">Por ejemplo, si NetX Duo está instalado en el directorio “ *\threadx\arm7\green*”, *nx_web_http_client.h* y *nx_web_http_client.c para aplicaciones de cliente HTTP de NetX Web, y nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c y nx_tcpserver.h para aplicaciones de servidor HTTP de NetX Web. nx_web_http_common.h debe estar en ese mismo directorio tanto para las aplicaciones de servidor como cliente. nx_md5.c* también debe copiarse en ese mismo directorio si se está usando la autenticación implícita.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-121">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nx_web_http_client.h* and *nx_web_http_client.c for NetX Web HTTP Client applications, and nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c and nx_tcpserver.h for NetX Web HTTP Server applications. For both client and server applications, nx_web_http_common.h must be in this directory as well. nx_md5.c* should also be copied into this directory if digest authentication is being used.</span></span> <span data-ttu-id="a3a6d-122">Para la demostración, los archivos del servidor y cliente HTTP de la aplicación “controlador de RAM” deben copiarse en el mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-122">For the demo ‘ram driver’ application HTTP Client and Server files should be copied into the same directory.</span></span>

<span data-ttu-id="a3a6d-123">Si se está usando TLS, es necesario contar con un directorio NetX Secure independiente que contenga los archivos de código fuente de TLS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-123">If using TLS, you should have a separate NetX Secure directory containing the TLS source files.</span></span>

## <a name="using-http"></a><span data-ttu-id="a3a6d-124">Uso de HTTP</span><span class="sxs-lookup"><span data-stu-id="a3a6d-124">Using HTTP</span></span>

<span data-ttu-id="a3a6d-125">El uso de NetX Web HTTP es sencillo.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-125">Using NetX Web HTTP is easy.</span></span> <span data-ttu-id="a3a6d-126">Básicamente, el código de aplicación debe incluir *nx_web_http_client.h* o *nx_web_http_server.h* después de incluir *tx_api.h, fx_api.h* y *nx_api.h* (*nx_web_http_common.h* se incluye automáticamente).</span><span class="sxs-lookup"><span data-stu-id="a3a6d-126">Basically, the application code must include *nx_web_http_client.h* and/or *nx_web_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h* (*nx_web_http_common.h* is automatically included).</span></span> <span data-ttu-id="a3a6d-127">Esos encabezados permiten que la aplicación use ThreadX, FileX y NetX Duo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-127">Those headers enable the application to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="a3a6d-128">Para la compatibilidad con HTTPS, se deben incluir los encabezados después de incluir el archivo *nx_secure_tls.h* para proporcionar compatibilidad con TLS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-128">For HTTPS support, the headers must be included after the *nx_secure_tls.h* file is included to bring in TLS support.</span></span>

<span data-ttu-id="a3a6d-129">Una vez incluidos los archivos de encabezado HTTP, el código de aplicación puede realizar las llamadas de función HTTP especificadas más adelante en este manual.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-129">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="a3a6d-130">La aplicación también debe vincularse con *nx_web_http_client.c para los clientes HTTP(S)* , *nx_web_http_server.c y nx_tcpserver.c para los servidores HTTP(S)* y *nx_md5.c (para la autenticación implícita)* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-130">The application must also link with *nx_web_http_client.c for HTTP(S) clients*, *nx_web_http_server.c and nx_tcpserver.c for HTTP(S) servers*, and *nx_md5.c (for digest authentication)* in the build process.</span></span> <span data-ttu-id="a3a6d-131">Estos archivos se deben compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-131">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="a3a6d-132">Esto es todo lo que se necesita para usar NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-132">This is all that is required to use NetX Web HTTP.</span></span>

> [!NOTE]
> <span data-ttu-id="a3a6d-133">Si no se especifica NX_WEB_HTTP_DIGEST_ENABLE en el proceso de compilación, no es necesario agregar el archivo *MD5.c* a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-133">If NX_WEB_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="a3a6d-134">Del mismo modo, si no se requiere ninguna funcionalidad de cliente HTTP, se puede omitir el archivo *nx_web_http_client.c* y, si no se requiere ninguna funcionalidad de servidor HTTP, se puede omitir *nx_web_http_server.c*.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-134">Similarly, if no HTTP Client capabilities are required, the *nx_web_http_client.c* file may be omitted and if no HTTP Server capabilities are required, *nx_web_http_server.c* may be omitted.</span></span>
>
> <span data-ttu-id="a3a6d-135">A menos que se defina NX_WEB_HTTPS_ENABLE para habilitar HTTPS (en lugar de usar solo HTTP de texto no cifrado), no es necesario que el protocolo TLS seguro esté en la compilación.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-135">Unless NX_WEB_HTTPS_ENABLE is defined in order to enable HTTPS (instead of using only plaintext HTTP) then NetX Secure TLS does not need to be in the build.</span></span>
>
> <span data-ttu-id="a3a6d-136">Puesto que HTTP usa los servicios de NetX TCP, TCP debe estar habilitado con la llamada a *nx_tcp_enable()* antes de utilizar HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-136">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable()* call prior to using HTTP.</span></span>
>
> <span data-ttu-id="a3a6d-137">Cuando se usa HTTPS con NetX Secure TLS, TLS se debe inicializar con *nx_secure_tls_initialize()* antes de llamar a las rutinas HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-137">When using HTTPS with NetX Secure TLS, TLS must be initialized with *nx_secure_tls_initialize()* prior to calling HTTPS routines.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="a3a6d-138">Sistema de ejemplo pequeño</span><span class="sxs-lookup"><span data-stu-id="a3a6d-138">Small Example System</span></span>

<span data-ttu-id="a3a6d-139">En la figura 1.1 siguiente se describe un ejemplo de cómo usar NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-139">An example of how to use NetX Web HTTP is described in Figure 1.1 below.</span></span>

> [!CAUTION]
> <span data-ttu-id="a3a6d-140">Esto se proporciona solo con fines demostrativos y no hay garantía de que se compile y se ejecute tal cual.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-140">This is provided for demonstration purposes only and is not guaranteed to compile and run as is.</span></span>
>
> <span data-ttu-id="a3a6d-141">Consulte la distribución del código de la versión HTTPS de NetX Duo para ver los archivos de código fuente de demostración que se compilarán correctamente en el entorno de Express Logic nativo.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-141">Please refer to the NetX Duo HTTPS release code distribution for  demo source code file(s) that will properly build in the native Express Logic environment.</span></span>  <span data-ttu-id="a3a6d-142">Observe también que estas demostraciones son muy simples de forma intencionada, ya que están diseñadas para dar a conocer la aplicación NetX Duo HTTPS o HTTPS a los nuevos usuarios.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-142">Also be aware that these demos are intentionally kept very simple as they are intended to introduce HTTPS and/or NetX Duo HTTPS application to new users.</span></span>

<span data-ttu-id="a3a6d-143">En este ejemplo se incluyen el archivo de inclusión HTTP *nx_web_http_client.h y nx_web_http_server.h* (*netx_web_http_common.h* se incluye automáticamente).</span><span class="sxs-lookup"><span data-stu-id="a3a6d-143">In this example, the HTTP include file *nx_web_http_client.h and nx_web_http_server.h are* brought in (*netx_web_http_common.h* is included automatically).</span></span> <span data-ttu-id="a3a6d-144">A continuación, el servidor HTTP se crea en "*tx_application_define*".</span><span class="sxs-lookup"><span data-stu-id="a3a6d-144">Next, the HTTP Server is created in “*tx_application_define*”.</span></span> <span data-ttu-id="a3a6d-145">Observe que el bloque de control de servidor HTTP "*Server*" se definió anteriormente como una variable global.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-145">Note that the HTTP Server control block “*Server*” was defined as a global variable previously.</span></span> <span data-ttu-id="a3a6d-146">Después de crearse correctamente, se inicia el servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-146">After successful creation, the HTTPS Server is started.</span></span> <span data-ttu-id="a3a6d-147">A continuación, se crea el cliente HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-147">The HTTPS Client is then created.</span></span> <span data-ttu-id="a3a6d-148">Escribe el archivo y vuelve a leer el archivo.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-148">It writes the file and reads the file back.</span></span>

> [!NOTE]
> <span data-ttu-id="a3a6d-149">NX_WEB_HTTPS_ENABLE se define en este sistema.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-149">NX_WEB_HTTPS_ENABLE is defined on this system.</span></span>

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

<span data-ttu-id="a3a6d-150">**Figura 1.1 Ejemplo de uso de HTTPS con NetX y NetX Secure TLS**</span><span class="sxs-lookup"><span data-stu-id="a3a6d-150">**Figure 1.1 Example of HTTPS use with NetX and NetX Secure TLS**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="a3a6d-151">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="a3a6d-151">Configuration Options</span></span>

<span data-ttu-id="a3a6d-152">Hay varias opciones de configuración para compilar HTTP para NetX.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-152">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="a3a6d-153">A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-153">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="a3a6d-154">Los valores predeterminados se enumeran pero se pueden redefinir antes de incluir *nx_web_http_client.h y nx_web_http_server.h*:</span><span class="sxs-lookup"><span data-stu-id="a3a6d-154">The default values are listed but can be redefined prior to inclusion of *nx_web_http_client.h and nx_web_http_server.h*:</span></span>

- <span data-ttu-id="a3a6d-155">**NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica de HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-155">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="a3a6d-156">Normalmente se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-156">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="a3a6d-157">**NX_WEB_HTTP_DIGEST_ENABLE**: si está definida, la autenticación con el resumen MD5 está habilitada en el servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-157">**NX_WEB_HTTP_DIGEST_ENABLE** If defined, authentication using the MD5 digest is enabled on the HTTPS Server.</span></span> <span data-ttu-id="a3a6d-158">De forma predeterminada, no está definido.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-158">By default it is not defined.</span></span>
- <span data-ttu-id="a3a6d-159">**NX_WEB_HTTP_SERVER_PRIORITY**: prioridad del subproceso de servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-159">**NX_WEB_HTTP_SERVER_PRIORITY** The priority of the HTTPS Server thread.</span></span> <span data-ttu-id="a3a6d-160">De forma predeterminada, este valor se define como 16 para especificar la prioridad 16.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-160">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="a3a6d-161">**NX_WEB_HTTP_NO_FILEX**: si está definida, esta opción proporciona un código auxiliar para las dependencias de FileX.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-161">**NX_WEB_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="a3a6d-162">El cliente HTTPS funcionará sin ningún cambio si se define esta opción.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-162">The HTTPS Client will function without any change if this option is defined.</span></span> <span data-ttu-id="a3a6d-163">El servidor HTTPS tendrá que modificarse o el usuario tendrá que crear unos cuantos servicios de FileX para que funcionen correctamente.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-163">The HTTPS Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="a3a6d-164">**NX_WEB_HTTP_TYPE_OF_SERVICE**: tipo de servicio necesario para las solicitudes TCP de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTPS TCP requests.</span></span> <span data-ttu-id="a3a6d-165">De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-165">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="a3a6d-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE**: el número de tics de temporizador que el subproceso de servidor puede ejecutar antes de producir subprocesos con la misma prioridad.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="a3a6d-167">El valor predeterminado es 2.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-167">The default value is 2.</span></span> <span data-ttu-id="a3a6d-168">Observe que esta opción está en desuso.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-168">Note this option is deprecated.</span></span>
- <span data-ttu-id="a3a6d-169">**NX_WEB_HTTP_FRAGMENT_OPTION**: fragmento habilitar para solicitudes TCP de HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-169">**NX_WEB_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="a3a6d-170">De forma predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de TCP de HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-170">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="a3a6d-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE**: tamaño de la ventana de socket de servidor.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="a3a6d-172">De manera predeterminada, este valor es 2048 bytes.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-172">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="a3a6d-173">**NX_WEB_HTTP_TIME_TO_LIVE**: especifica el número de enrutadores que un paquete puede pasar antes de que se descarte.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-173">**NX_WEB_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="a3a6d-174">El valor predeterminado se define en 0x80.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-174">The default value is set to 0x80.</span></span>
- <span data-ttu-id="a3a6d-175">**NX_WEB_HTTP_SERVER_TIMEOUT**: especifica el número de tics de ThreadX en los que se suspenderán los servicios internos.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-175">**NX_WEB_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="a3a6d-176">El valor predeterminado es 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="a3a6d-176">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="a3a6d-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT**: especifica el número de tics de ThreadX en los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_server_socket_accept()* .</span><span class="sxs-lookup"><span data-stu-id="a3a6d-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept()* calls.</span></span> <span data-ttu-id="a3a6d-178">El valor predeterminado está establecido en (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="a3a6d-178">The default value is set to (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="a3a6d-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT**: especifica el número de tics de ThreadX en los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_disconnect()* .</span><span class="sxs-lookup"><span data-stu-id="a3a6d-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect()* calls.</span></span> <span data-ttu-id="a3a6d-180">El valor predeterminado es 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="a3a6d-180">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="a3a6d-181">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT**: especifica el número de tics de ThreadX en los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_disconnect()* .</span><span class="sxs-lookup"><span data-stu-id="a3a6d-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive()* calls.</span></span> <span data-ttu-id="a3a6d-182">El valor predeterminado es 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="a3a6d-182">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="a3a6d-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND**: especifica el número de tics de ThreadX en los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_disconnect()* .</span><span class="sxs-lookup"><span data-stu-id="a3a6d-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send()* calls.</span></span> <span data-ttu-id="a3a6d-184">El valor predeterminado es 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="a3a6d-184">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="a3a6d-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **: especifica el tamaño máximo del campo de encabezado HTTP. El valor predeterminado es 256.**</span><span class="sxs-lookup"><span data-stu-id="a3a6d-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **Specifies the maximum size of the HTTP header field. The default value is 256.**</span></span>
- <span data-ttu-id="a3a6d-186">\*\*NX_WEB_HTTP_MULTIPART_ENABLE \*\* \*\*: si está definido, permite que el servidor HTTPS admita solicitudes HTTP de varias partes.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-186">\*\*NX_WEB_HTTP_MULTIPART_ENABLE \*\* \*\*If defined, enables HTTPS Server to support multipart HTTP requests.</span></span> **
- <span data-ttu-id="a3a6d-187">**NX_WEB_HTTP_SERVER_MAX_PENDING**: especifica el número de conexiones que se pueden poner en cola para el servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTPS Server.</span></span> <span data-ttu-id="a3a6d-188">El valor predeterminado se establece en el doble del número máximo de sesiones de servidor.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-188">The default value is set to twice the maximum number of server sessions.</span></span>
- <span data-ttu-id="a3a6d-189">**NX_WEB_HTTP_MAX_RESOURCE**: especifica el número de bytes permitido en el *nombre de recurso* proporcionado por un cliente.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-189">**NX_WEB_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="a3a6d-190">El valor predeterminado se establece en 40.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-190">The default value is set to 40.</span></span>
- <span data-ttu-id="a3a6d-191">**NX_WEB_HTTP_MAX_NAME**: especifica el número de bytes permitido en el *nombre de usuario* proporcionado por un cliente.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-191">**NX_WEB_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="a3a6d-192">El valor predeterminado se establece en 20.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-192">The default value is set to 20.</span></span>
- <span data-ttu-id="a3a6d-193">**NX_WEB_HTTP_MAX_PASSWORD**: especifica el número de bytes permitido en la *contraseña* proporcionada por un cliente.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-193">**NX_WEB_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="a3a6d-194">El valor predeterminado se establece en 20.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-194">The default value is set to 20.</span></span>
- <span data-ttu-id="a3a6d-195">**NX_WEB_HTTP_SERVER_SESSION_MAX**: especifica el número de sesiones simultáneas para un servidor HTTP o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** Specifies the number of simultaneous sessions for an HTTP or HTTPS Server.</span></span> <span data-ttu-id="a3a6d-196">Se asignan un socket TCP y una sesión TLS (si HTTPS está habilitado) para cada sesión.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-196">A TCP socket and a TLS session (if HTTPS is enabled) are allocated for each session.</span></span> <span data-ttu-id="a3a6d-197">El valor predeterminado se establece en 2.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-197">The default value is set to 2.</span></span>
- <span data-ttu-id="a3a6d-198">**NX_WEB_HTTPS_ENABLE**: si se define, esta macro habilita TLS y HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-198">**NX_WEB_HTTPS_ENABLE** If defined, this macro enables TLS and HTTPS.</span></span> <span data-ttu-id="a3a6d-199">Deje sin definir para liberar recursos si solo desea un HTTP de texto no cifrado.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-199">Leave undefined to free up resources if only plaintext HTTP is desired.</span></span> <span data-ttu-id="a3a6d-200">De forma predeterminada, esta macro no está definida.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-200">By default, this macro is not defined.</span></span>
- <span data-ttu-id="a3a6d-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE**: si se define, esta macro deshabilita la característica de conexión persistente de HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** If defined, this macro disables HTTP keep-alive feature.</span></span> <span data-ttu-id="a3a6d-202">De forma predeterminada, esta macro no está definida.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-202">By default, this macro is not defined.</span></span>
- <span data-ttu-id="a3a6d-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE**: especifica el tamaño mínimo de los paquetes en el grupo especificado al crear el servidor.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at server creation.</span></span> <span data-ttu-id="a3a6d-204">El tamaño mínimo es necesario para asegurarse de que el encabezado HTTP completo puede estar incluido en un paquete.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-204">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="a3a6d-205">El valor predeterminado se establece en 600.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-205">The default value is set to 600.</span></span>
- <span data-ttu-id="a3a6d-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE**: especifica el tamaño mínimo de los paquetes en el grupo especificado al crear el cliente.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="a3a6d-207">El tamaño mínimo es necesario para asegurarse de que el encabezado HTTP completo puede estar incluido en un paquete.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-207">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="a3a6d-208">El valor predeterminado se establece en 600.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-208">The default value is set to 600.</span></span>
- <span data-ttu-id="a3a6d-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS**: establece el tiempo de espera de retransmisión de sockets de servidor en segundos.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** Set the Server socket retransmission timeout in seconds.</span></span> <span data-ttu-id="a3a6d-210">El valor predeterminado se establece en 2.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-210">The default value is set to 2.</span></span>
- <span data-ttu-id="a3a6d-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX**: establece el número máximo de retransmisiones en el socket de servidor.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="a3a6d-212">El valor predeterminado se establece en 10.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-212">The default value is set to 10.</span></span>
- <span data-ttu-id="a3a6d-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT**: este valor se usa para establecer el siguiente tiempo de espera de retransmisión.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="a3a6d-214">El tiempo de espera actual se multiplica por el número de retransmisiones hasta el momento, desplazado por el valor del desplazamiento de tiempo de espera del socket.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-214">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="a3a6d-215">El valor predeterminado se establece en 1 para duplicar el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-215">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="a3a6d-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH**: especifica el número máximo de paquetes que se pueden poner en cola en la cola de retransmisión de sockets de servidor.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="a3a6d-217">Si el número de paquetes puestos en cola alcanza este número, no se podrán enviar más paquetes hasta que se liberen uno o varios paquetes en cola.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-217">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="a3a6d-218">El valor predeterminado se establece en 20.</span><span class="sxs-lookup"><span data-stu-id="a3a6d-218">The default value is set to 20.</span></span>
