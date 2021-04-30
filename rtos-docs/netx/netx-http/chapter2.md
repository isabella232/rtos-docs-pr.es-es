---
title: 'Capítulo 2: Instalación y uso de NetX HTTP'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX HTTP.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db621e38e9d2324ca3ce2398aee9f729b05886ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815197"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a><span data-ttu-id="7e547-103">Capítulo 2: Instalación y uso de NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="7e547-103">Chapter 2 - Installation and use of NetX HTTP</span></span>

<span data-ttu-id="7e547-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="7e547-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="7e547-105">Product Distribution</span></span>

<span data-ttu-id="7e547-106">Azure RTOS NetX se puede obtener desde el repositorio de código fuente público en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="7e547-106">Azure RTOS NetX can be obtained from our public source code repository at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span>

- <span data-ttu-id="7e547-107">**nx_http_client.h** Archivo de encabezado del cliente HTTP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7e547-107">**nx_http_client.h** Header file for HTTP Client for NetX</span></span>
- <span data-ttu-id="7e547-108">**nx_http_server.h** Archivo de encabezado del servidor HTTP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7e547-108">**nx_http_server.h** Header file for HTTP Server for NetX</span></span>
- <span data-ttu-id="7e547-109">**nx_http_client.c** Archivo de código fuente de C del cliente HTTP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7e547-109">**nx_http_client.c** C Source file for HTTP Client for NetX</span></span>
- <span data-ttu-id="7e547-110">**nx_http_server.c** Archivo de código fuente de C del servidor HTTP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7e547-110">**nx_http_server.c** C Source file for HTTP Server for NetX</span></span>
- <span data-ttu-id="7e547-111">**nx_md5.c** Algoritmos de síntesis MD5.</span><span class="sxs-lookup"><span data-stu-id="7e547-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="7e547-112">**filex_stub.h** Archivo de código auxiliar si FileX no existe.</span><span class="sxs-lookup"><span data-stu-id="7e547-112">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="7e547-113">**nx_http.pdf** Descripción de HTTP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7e547-113">**nx_http.pdf** Description of HTTP for NetX</span></span>
- <span data-ttu-id="7e547-114">**demo_netx_http.c** Demostración de HTTP de NetX.</span><span class="sxs-lookup"><span data-stu-id="7e547-114">**demo_netx_http.c** NetX HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="7e547-115">Instalación de HTTP</span><span class="sxs-lookup"><span data-stu-id="7e547-115">HTTP Installation</span></span>

<span data-ttu-id="7e547-116">Para usar HTTP para NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="7e547-116">In order to use HTTP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="7e547-117">Por ejemplo, si NetX está instalado en el directorio " *\threadx\arm7\green*", entonces *nx_http_client.h* y *nx_http_client.c* en el caso de aplicaciones cliente HTTP de NetX y *nx_http_server.h* y *nx_http_server.c* en el caso de aplicaciones de servidor HTTP de NetX.</span><span class="sxs-lookup"><span data-stu-id="7e547-117">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_http_client.h* and *nx_http_client.c* for NetX HTTP Client applications, and *nx_http_server.h* and *nx_http_server.c* for NetX HTTP Server applications.</span></span> <span data-ttu-id="7e547-118">*nx_md5.c* debe copiarse en este directorio.</span><span class="sxs-lookup"><span data-stu-id="7e547-118">*nx_md5.c* should be copied into this directory.</span></span> <span data-ttu-id="7e547-119">En la demostración de "controlador RAM", los archivos de servidor y cliente HTTP de NetX de la aplicación deben copiarse en el mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="7e547-119">For the demo ‘ram driver’ application NetX HTTP Client and Server files should be copied into the same directory.</span></span>

## <a name="using-http"></a><span data-ttu-id="7e547-120">Uso de HTTP</span><span class="sxs-lookup"><span data-stu-id="7e547-120">Using HTTP</span></span>

<span data-ttu-id="7e547-121">El uso de HTTP para NetX es sencillo.</span><span class="sxs-lookup"><span data-stu-id="7e547-121">Using HTTP for NetX is easy.</span></span> <span data-ttu-id="7e547-122">Básicamente, el código de la aplicación debe incluir *nx_http_client.h* o *nx_http_server.h* después de incluir *tx_api.h, fx_api.h* y *nx_api.h*, para usar ThreadX, FileX y NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7e547-122">Basically, the application code must include *nx_http_client.h* and/or *nx_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX, respectively.</span></span> <span data-ttu-id="7e547-123">Una vez incluidos los archivos de encabezado HTTP, el código de aplicación puede realizar las llamadas de función HTTP especificadas más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="7e547-123">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="7e547-124">La aplicación también debe incluir *nx_http_client.c*, *nx_http_server.c* y *md5.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="7e547-124">The application must also include *nx_http_client.c*, *nx_http_server.c*, and *md5.c* in the build process.</span></span> <span data-ttu-id="7e547-125">Estos archivos se deben compilar de la misma manera que otros archivos de aplicación, y su formulario de objetos se debe vincular junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e547-125">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="7e547-126">Esto es todo lo que se necesita para usar NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-126">This is all that is required to use NetX HTTP.</span></span>

>[!NOTE] 
> <span data-ttu-id="7e547-127">Si no se especifica NX_HTTP_DIGEST_ENABLE en el proceso de compilación, no es necesario agregar el archivo *md5.c* a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e547-127">If NX_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="7e547-128">Del mismo modo, si no se requiere ninguna funcionalidad de cliente HTTP, se puede omitir el archivo *nx_http_client.c*.</span><span class="sxs-lookup"><span data-stu-id="7e547-128">Similarly, if no HTTP Client capabilities are required, the *nx_http_client.c* file may be omitted.</span></span>

>[!NOTE] 
> <span data-ttu-id="7e547-129">Puesto que HTTP usa los servicios de NetX TCP, TCP debe estar habilitado con la llamada *nx_tcp_enable* antes de utilizar HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-129">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using HTTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="7e547-130">Sistema pequeño de ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e547-130">Small Example System</span></span>

<span data-ttu-id="7e547-131">Un ejemplo de lo fácil que es usar NetX HTTP se describe en la figura 1.1 que aparece a continuación.</span><span class="sxs-lookup"><span data-stu-id="7e547-131">An example of how easy it is to use NetX HTTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="7e547-132">En este ejemplo, los archivos de inclusión HTTP *nx_http_client.h y nx_http_server.h se* proporcionan en la línea 8.</span><span class="sxs-lookup"><span data-stu-id="7e547-132">In this example, the HTTP include file *nx_http_client.h and nx_http_server.h are* brought in at line 8.</span></span> <span data-ttu-id="7e547-133">A continuación, el servidor HTTP se crea en "*tx_application_define*" en la línea 131.</span><span class="sxs-lookup"><span data-stu-id="7e547-133">Next, the HTTP Server is created in “*tx_application_define*” at line 131.</span></span>

>[!NOTE] 
> <span data-ttu-id="7e547-134">El bloque de control de servidor HTTP "*server*" se definió anteriormente como una variable global en la línea 25.</span><span class="sxs-lookup"><span data-stu-id="7e547-134">The HTTP Server control block “*Server*” was defined as a global variable at line 25 previously.</span></span>

<span data-ttu-id="7e547-135">Después de la creación correcta, se inicia un servidor HTTP en la línea 136.</span><span class="sxs-lookup"><span data-stu-id="7e547-135">After successful creation, an HTTP Server is started at line 136.</span></span> <span data-ttu-id="7e547-136">En la línea 149 se crea el cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-136">At line 149 the HTTP Client is created.</span></span> <span data-ttu-id="7e547-137">Y, por último, el cliente escribe el archivo en la línea 157 y vuelve a leer el archivo en la línea 195.</span><span class="sxs-lookup"><span data-stu-id="7e547-137">And finally, the Client writes the file at line 157 and reads the file back at line 195.</span></span>

```c
/* This is a small demo of HTTP on the high-performance NetX TCP/IP stack.
This demo relies on ThreadX, NetX, and FileX to show a simple HTML
transfer from the client and then back from the server. */

#include "tx_api.h"
#include "fx_api.h"
#include "nx_api.h"
#include "nx_http_client.h"
#include "nx_http_server.h"
#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_0;
TX_THREAD         thread_1;
NX_PACKET_POOL    pool_0;
NX_PACKET_POOL    pool_1;
NX_IP             ip_0;
NX_IP             ip_1;
FX_MEDIA          ram_disk;

/* Define HTTP objects. */

NX_HTTP_SERVER    my_server;
NX_HTTP_CLIENT    my_client;

/* Define the counters used in the demo application... */

ULONG             error_counter;

/* Define the RAM disk memory. */

UCHAR             ram_disk_memory[32000];

/* Define function prototypes. */

void     thread_0_entry(ULONG thread_input);
VOID     _fx_ram_driver(FX_MEDIA *media_ptr) ;
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT     authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, CHAR **name, CHAR **password, 
                              CHAR **realm);

/* Define the application's authentication check. This is called by
the HTTP server whenever a new request is received. */
UINT authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, CHAR **name, CHAR **password, 
                         CHAR **realm);
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */
    *name = "name";
    *password = "password";
    *realm = "NetX HTTP demo";

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create packet pool. */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
                         600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create an IP instance. */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
                0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create another IP instance. */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
                0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances. */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk. */
                 _fx_ram_driver, ram_disk_memory, pointer, 4096) ;
                 pointer += 4096;

    /* Create the NetX HTTP Server. */
    nx_http_server_create(&my_server, "My HTTP Server", &ip_1, &ram_disk,
                         pointer, 4096, &pool_1, authentication_check, NX_NULL);
                         pointer = pointer + 4096;

    /* Start the HTTP Server. */
    nx_http_server_start(&my_server);
}

/* Define the test thread. */
void     thread_0_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Create an HTTP client instance. */
    status = nx_http_client_create(&my_client, "My Client", &ip_0,
                                  &pool_0, 600);

    /* Check status. */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server. */
    status = nx_http_client_put_start(&my_client, IP_ADDRESS(1,2,3,5),
                                      "/test.htm", "name", "password", 103, 50);
    /* Check status. */
    if (status)
        error_counter++;

    /* Allocate a packet. */
    status = nx_packet_allocate(&pool_0, &my_packet, NX_TCP_PACKET,
                               NX_WAIT_FOREVER);
    /* Check status. */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page. */
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

    /* Complete the PUT by writing the total length. */
    status = **nx_http_client_put_packet**(&my_client, my_packet, 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Now GET the file back! */
    status = nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
                                     "/test.htm", NX_NULL, 0, "name", 
                                     "password", 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Get a packet. */
    status = nx_http_client_get_packet(&my_client, &my_packet, 20);

    /* Check for an error. */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet. */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it! */
        nx_packet_release(my_packet);
    }

    /* Flush the media. */
     fx_media_flush(&ram_disk);
 }
```

<span data-ttu-id="7e547-138">Figura 1.1 Ejemplo de uso de HTTP con NetX</span><span class="sxs-lookup"><span data-stu-id="7e547-138">Figure 1.1 Example of HTTP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="7e547-139">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="7e547-139">Configuration Options</span></span>

<span data-ttu-id="7e547-140">Hay varias opciones de configuración para compilar HTTP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7e547-140">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="7e547-141">A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas.</span><span class="sxs-lookup"><span data-stu-id="7e547-141">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="7e547-142">Los valores predeterminados se enumeran, pero se pueden redefinir antes de incluir *nx_http_client.h y nx_http_server.h*:</span><span class="sxs-lookup"><span data-stu-id="7e547-142">The default values are listed, but can be redefined prior to inclusion of *nx_http_client.h and nx_http_server.h*:</span></span>

- <span data-ttu-id="7e547-143">**NX_DISABLE_ERROR_CHECKING** Si está definida, esta opción quita la comprobación de errores básica de HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-143">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="7e547-144">Por lo general, se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e547-144">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="7e547-145">**NX_HTTP_SERVER_PRIORITY** Prioridad del subproceso de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-145">**NX_HTTP_SERVER_PRIORITY** The priority of the HTTP Server thread.</span></span> <span data-ttu-id="7e547-146">De manera predeterminada, este valor se define como 16 para especificar la prioridad 16.</span><span class="sxs-lookup"><span data-stu-id="7e547-146">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="7e547-147">**NX_TFTP_NO_FILEX** Si está definida, esta opción proporciona un código auxiliar para las dependencias de FileX.</span><span class="sxs-lookup"><span data-stu-id="7e547-147">**NX_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="7e547-148">Si esta opción está definida, el cliente HTTP funcionará sin ningún cambio.</span><span class="sxs-lookup"><span data-stu-id="7e547-148">The HTTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="7e547-149">El servidor HTTP tendrá que modificarse o el usuario tendrá que crear unos cuantos servicios de FileX para que funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="7e547-149">The HTTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="7e547-150">**NX_HTTP_TYPE_OF_SERVICE** Tipo de servicio necesario para las solicitudes HTTP TCP.</span><span class="sxs-lookup"><span data-stu-id="7e547-150">**NX_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTP TCP requests.</span></span> <span data-ttu-id="7e547-151">De manera predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal.</span><span class="sxs-lookup"><span data-stu-id="7e547-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="7e547-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** El número de tics de temporizador que el subproceso de servidor puede ejecutar antes de producir subprocesos con la misma prioridad.</span><span class="sxs-lookup"><span data-stu-id="7e547-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="7e547-153">El valor predeterminado es 2.</span><span class="sxs-lookup"><span data-stu-id="7e547-153">The default value is 2.</span></span>
- <span data-ttu-id="7e547-154">**NX_HTTP_FRAGMENT_OPTION** Permite habilitar la fragmentación de solicitudes TCP de HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-154">**NX_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="7e547-155">De manera predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de TCP de HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-155">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="7e547-156">**NX_HTTP_SERVER_WINDOW_SIZE** Tamaño de la ventana del socket de servidor.</span><span class="sxs-lookup"><span data-stu-id="7e547-156">**NX_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="7e547-157">De manera predeterminada, este valor es 2048 bytes.</span><span class="sxs-lookup"><span data-stu-id="7e547-157">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="7e547-158">**NX_TFTP_TIME_TO_LIVE** Especifica el número de enrutadores que este paquete puede pasar antes de que se descarte.</span><span class="sxs-lookup"><span data-stu-id="7e547-158">**NX_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="7e547-159">El valor predeterminado se define en 0x80.</span><span class="sxs-lookup"><span data-stu-id="7e547-159">The default value is set to 0x80.</span></span>
- <span data-ttu-id="7e547-160">**NX_HTTP_SERVER_TIMEOUT** Especifica el número de tics de ThreadX para los que se suspenderán los servicios internos.</span><span class="sxs-lookup"><span data-stu-id="7e547-160">**NX_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="7e547-161">El valor predeterminado se establece en 10 segundos (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7e547-161">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="7e547-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Especifica el número de tics de ThreadX para los que los servicios internos se suspenderán en las llamadas internas *nx_tcp_server_socket_accept*.</span><span class="sxs-lookup"><span data-stu-id="7e547-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept* calls.</span></span> <span data-ttu-id="7e547-163">El valor predeterminado se establece en (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7e547-163">The default value is set to (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="7e547-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Especifica el número de tics de ThreadX con los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_disconnect*.</span><span class="sxs-lookup"><span data-stu-id="7e547-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect* calls.</span></span> <span data-ttu-id="7e547-165">El valor predeterminado se establece en 10 segundos (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7e547-165">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="7e547-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Especifica el número de tics de ThreadX con los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_receive*.</span><span class="sxs-lookup"><span data-stu-id="7e547-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive* calls.</span></span> <span data-ttu-id="7e547-167">El valor predeterminado se establece en 10 segundos (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7e547-167">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="7e547-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Especifica el número de tics de ThreadX con los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_send*.</span><span class="sxs-lookup"><span data-stu-id="7e547-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send* calls.</span></span> <span data-ttu-id="7e547-169">El valor predeterminado se establece en 10 segundos (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="7e547-169">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="7e547-170">**NX_HTTP_MAX_HEADER_FIELD** Especifica el tamaño máximo del campo de encabezado HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-170">**NX_HTTP_MAX_HEADER_FIELD** Specifies the maximum size of the HTTP header field.</span></span> <span data-ttu-id="7e547-171">El valor predeterminado es 256.</span><span class="sxs-lookup"><span data-stu-id="7e547-171">The default value is 256.</span></span>
- <span data-ttu-id="7e547-172">**NX_HTTP_MULTIPART_ENABLE** Si se define, permite que el servidor HTTP admita solicitudes HTTP de varias partes.</span><span class="sxs-lookup"><span data-stu-id="7e547-172">**NX_HTTP_MULTIPART_ENABLE** If defined, enables HTTP Server to support multipart HTTP requests.</span></span>
- <span data-ttu-id="7e547-173">**NX_HTTP_SERVER_MAX_PENDING** Especifica el número de conexiones que se pueden poner en cola para el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e547-173">**NX_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTP Server.</span></span> <span data-ttu-id="7e547-174">El valor predeterminado se establece en 5.</span><span class="sxs-lookup"><span data-stu-id="7e547-174">The default value is set to 5.</span></span>
- <span data-ttu-id="7e547-175">**NX_HTTP_MAX_RESOURCE** Especifica el número de bytes permitido en un *nombre de recurso* proporcionado por el cliente.</span><span class="sxs-lookup"><span data-stu-id="7e547-175">**NX_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="7e547-176">El valor predeterminado se establece en 40.</span><span class="sxs-lookup"><span data-stu-id="7e547-176">The default value is set to 40.</span></span>
- <span data-ttu-id="7e547-177">**NX_HTTP_MAX_NAME** Especifica el número de bytes permitido en un *nombre de usuario* proporcionado por el cliente.</span><span class="sxs-lookup"><span data-stu-id="7e547-177">**NX_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="7e547-178">El valor predeterminado se establece en 20.</span><span class="sxs-lookup"><span data-stu-id="7e547-178">The default value is set to 20.</span></span>
- <span data-ttu-id="7e547-179">**NX_HTTP_MAX_PASSWORD** Especifica el número de bytes permitido en una *contraseña* proporcionada por el cliente.</span><span class="sxs-lookup"><span data-stu-id="7e547-179">**NX_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="7e547-180">El valor predeterminado se establece en 20.</span><span class="sxs-lookup"><span data-stu-id="7e547-180">The default value is set to 20.</span></span>
- <span data-ttu-id="7e547-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Especifica el tamaño mínimo de los paquetes en el grupo especificado al crear el servidor.</span><span class="sxs-lookup"><span data-stu-id="7e547-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Server creation.</span></span> <span data-ttu-id="7e547-182">El tamaño mínimo es necesario para asegurarse de que el encabezado HTTP completo puede estar incluido en un paquete.</span><span class="sxs-lookup"><span data-stu-id="7e547-182">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="7e547-183">El valor predeterminado se establece en 600.</span><span class="sxs-lookup"><span data-stu-id="7e547-183">The default value is set to 600.</span></span>
- <span data-ttu-id="7e547-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Especifica el tamaño mínimo de los paquetes en el grupo especificado al crear el cliente.</span><span class="sxs-lookup"><span data-stu-id="7e547-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="7e547-185">El tamaño mínimo es necesario para asegurarse de que el encabezado HTTP completo puede estar incluido en un paquete.</span><span class="sxs-lookup"><span data-stu-id="7e547-185">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="7e547-186">El valor predeterminado se establece en 300.</span><span class="sxs-lookup"><span data-stu-id="7e547-186">The default value is set to 300.</span></span>
- <span data-ttu-id="7e547-187">**NX_HTTP_SERVER_RETRY_SECONDS** *Establece el tiempo de espera de retransmisión de sockets del servidor en segundos. El* valor predeterminado se establece en 2.</span><span class="sxs-lookup"><span data-stu-id="7e547-187">**NX_HTTP_SERVER_RETRY_SECONDS** *Set the Server socket retransmission timeout in seconds. The* default value is set to 2.</span></span>
- <span data-ttu-id="7e547-188">**NX_HTTP_SERVER_ RETRY_MAX** Establece el número máximo de retransmisiones en el socket de servidor.</span><span class="sxs-lookup"><span data-stu-id="7e547-188">**NX_HTTP_SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="7e547-189">El valor predeterminado se establece en 10.</span><span class="sxs-lookup"><span data-stu-id="7e547-189">The default value is set to 10.</span></span>
- <span data-ttu-id="7e547-190">**NX_HTTP_SERVER_ RETRY_SHIFT** Este valor se usa para establecer el siguiente tiempo de espera de retransmisión.</span><span class="sxs-lookup"><span data-stu-id="7e547-190">**NX_HTTP_SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="7e547-191">El tiempo de espera actual se multiplica por el número de retransmisiones hasta el momento, desplazado por el valor del desplazamiento de tiempo de espera del socket.</span><span class="sxs-lookup"><span data-stu-id="7e547-191">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="7e547-192">El valor predeterminado se establece en 1 para duplicar el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="7e547-192">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="7e547-193">**NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH** Especifica el número máximo de paquetes que se pueden poner en la cola de retransmisión de sockets de servidor.</span><span class="sxs-lookup"><span data-stu-id="7e547-193">**NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="7e547-194">Si el número de paquetes puestos en cola alcanza este número, no se podrán enviar más paquetes hasta que se liberen uno o varios paquetes en cola.</span><span class="sxs-lookup"><span data-stu-id="7e547-194">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="7e547-195">El valor predeterminado se establece en 20.</span><span class="sxs-lookup"><span data-stu-id="7e547-195">The default value is set to 20.</span></span>