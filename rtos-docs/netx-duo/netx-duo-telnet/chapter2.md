---
title: 'Capítulo 2: Instalación y uso de Telnet de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente Telnet de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5b24690db6ccbc582387dd9dba5b0471e6f278d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814537"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-telnet"></a><span data-ttu-id="dbd3c-103">Capítulo 2: Instalación y uso de Telnet de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dbd3c-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo Telnet</span></span>

<span data-ttu-id="dbd3c-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente Telnet de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo Telnet component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="dbd3c-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="dbd3c-105">Product Distribution</span></span>

<span data-ttu-id="dbd3c-106">El paquete Telnet de Azure RTOS NetX Duo está disponible en <https://github.com/azure-rtos/netxduo>.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-106">The Azure RTOS NetX Duo Telnet package is available at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="dbd3c-107">El paquete incluye los siguientes archivos:</span><span class="sxs-lookup"><span data-stu-id="dbd3c-107">The package includes the following files:</span></span>

- <span data-ttu-id="dbd3c-108">**nxd_telnet_client.h**: archivo de encabezado del cliente Telnet para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dbd3c-108">**nxd_telnet_client.h**: Header file for Telnet Client for NetX Duo</span></span>
- <span data-ttu-id="dbd3c-109">**nxd_telnet_client.c**: archivo de origen del cliente Telnet para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dbd3c-109">**nxd_telnet_client.c**: C Source file for Telnet Client for NetX Duo</span></span>
- <span data-ttu-id="dbd3c-110">**nxd_telnet_server.h**: archivo de encabezado del servidor Telnet para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dbd3c-110">**nxd_telnet_server.h**: Header file for Telnet Server for NetX Duo</span></span>
- <span data-ttu-id="dbd3c-111">**nxd_telnet_server.c**: archivo de código fuente C del servidor Telnet para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dbd3c-111">**nxd_telnet_server.c**: C Source file for Telnet Server for NetX Duo</span></span>
- <span data-ttu-id="dbd3c-112">**nxd_telnet.pdf**: descripción en PDF de Telnet para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dbd3c-112">**nxd_telnet.pdf**: PDF description of Telnet for NetX Duo</span></span>
- <span data-ttu-id="dbd3c-113">**demo_netxduo_telnet.c**: demostración de Telnet de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dbd3c-113">**demo_netxduo_telnet.c**: NetX Duo Telnet demonstration</span></span>

## <a name="telnet-installation"></a><span data-ttu-id="dbd3c-114">Instalación de Telnet</span><span class="sxs-lookup"><span data-stu-id="dbd3c-114">Telnet Installation</span></span>

<span data-ttu-id="dbd3c-115">Para usar Telnet para NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-115">In order to use Telnet for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="dbd3c-116">Por ejemplo, si NetX Duo está instalado en el directorio “ *\threadx\arm7\green*”, los archivos *nxd_telnet_client.h*, *nxd_telnet_client.c*, *nxd_telnet_server.c y nxd_telnet_server.h* deben copiarse en este directorio.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-116">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_telnet_client.h*, *nxd_telnet_client.c*, *nxd_telnet_server.c and nxd_telnet_server.h* files should be copied into this directory.</span></span>

## <a name="using-telnet"></a><span data-ttu-id="dbd3c-117">Uso de Telnet</span><span class="sxs-lookup"><span data-stu-id="dbd3c-117">Using Telnet</span></span>

<span data-ttu-id="dbd3c-118">Usar Telnet para NetX Duo es fácil.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-118">Using Telnet for NetX Duo is easy.</span></span> <span data-ttu-id="dbd3c-119">Básicamente, el código de la aplicación debe incluir *nxd_telnet_server.h* para las aplicaciones del servidor Telnet y *nxd_telnet_client.h* para las aplicaciones cliente Telnet después de incluir *tx_api.h* y *nx_api.h*, para poder usar ThreadX y NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-119">Basically, the application code must include *nxd_telnet_server.h* for Telnet Server applications and *nxd_telnet_client.h* for Telnet Client applications after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo.</span></span> <span data-ttu-id="dbd3c-120">Una vez que se incluye *el encabezado*, el código de la aplicación puede realizar las llamadas de función de Telnet que se especifican más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-120">Once *the header* is included, the application code is then able to make the Telnet function calls specified later in this guide.</span></span> <span data-ttu-id="dbd3c-121">La aplicación también debe incluir *nxd_telnet_client.c* y *nxd_telnet_server.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-121">The application must also include *nxd_telnet_client.c* and *nxd_telnet_server.c* in the build process.</span></span> <span data-ttu-id="dbd3c-122">Estos archivos deben compilarse de la misma manera que otros archivos de aplicación, y su forma de objeto debe vincularse junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-122">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="dbd3c-123">Esto es todo lo que se necesita para usar NetX Duo Telnet.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-123">This is all that is required to use NetX Duo Telnet.</span></span>

<span data-ttu-id="dbd3c-124">Si no se requiere ninguna funcionalidad del cliente Telnet, es posible que se omita el archivo *nxd_telnet_client.c*.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-124">If no Telnet Client capabilities are required, the *nxd_telnet_client.c* file may be omitted.</span></span>

<span data-ttu-id="dbd3c-125">Tenga en cuenta que, puesto que Telnet usa los servicios TCP de NetX Duo, TCP debe estar habilitado con la llamada *nx_tcp_enable* para poder utilizar Telnet.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-125">Note also that because Telnet utilizes NetX Duo TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using Telnet.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="dbd3c-126">Sistema de ejemplo pequeño</span><span class="sxs-lookup"><span data-stu-id="dbd3c-126">Small Example System</span></span>

<span data-ttu-id="dbd3c-127">A continuación se muestra un ejemplo de cómo usar Telnet de NetX Duo en la figura 1.1.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-127">An example of how to use NetX Duo Telnet is shown in Figure 1.1 below.</span></span> <span data-ttu-id="dbd3c-128">En este ejemplo, los archivos de inclusión de Telnet *se* incluyen en las líneas 7 y 8.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-128">In this example, the Telnet include files *are* brought in at line 7 and 8.</span></span> <span data-ttu-id="dbd3c-129">A continuación, el servidor Telnet se crea en "*tx_application_define*" en la línea 146.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-129">Next, the Telnet Server is created in “*tx_application_define*” at line 146.</span></span> <span data-ttu-id="dbd3c-130">Tenga en cuenta que los bloques de control del servidor y el cliente Telnet se definen como variables globales en las líneas 23 y 24 previamente.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-130">Note that the Telnet Server and Client control blocks are defined as global variables at line 23-24 previously.</span></span>

<span data-ttu-id="dbd3c-131">Antes de que se pueda iniciar el servidor o cliente Telnet, deben validar su dirección IP con NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-131">Before the Telnet Server or Client can be started they must validate their IP address with NetX Duo.</span></span> <span data-ttu-id="dbd3c-132">En el caso de las conexiones IPv4, esto se logra simplemente esperando a que el controlador NetX inicialice el sistema en la línea 166.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-132">For IPv4 connections this is accomplished by simply waiting briefly to let the NetX driver initialize the system on line 166.</span></span> <span data-ttu-id="dbd3c-133">En el caso de las conexiones IPv6, es necesario habilitar IPv6 e ICMPv6 (se hace en las líneas 171 y 172).</span><span class="sxs-lookup"><span data-stu-id="dbd3c-133">For IPv6 connections, this requires enabling IPv6 and ICMPv6 which it does in lines 171-172.</span></span> <span data-ttu-id="dbd3c-134">El cliente establece sus direcciones IPv6 locales de vínculo y globales en la interfaz principal entre las líneas 181 y 186 y espera a que se complete la validación de NetX Duo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-134">The Client sets its global and link local IPv6 addresses on the primary interface on lines 181-186 and waits for NetX Duo validation to complete in the background.</span></span> <span data-ttu-id="dbd3c-135">El servidor también establece sus direcciones locales de vínculo y globales en su interfaz principal, entre las líneas 192 y 198.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-135">The Server also sets its global and link local addresses on its primary interface in lines 192 – 198.</span></span> <span data-ttu-id="dbd3c-136">Tenga en cuenta que los dos servicios (*nxd_ipv6_global_address_set* y *nxd_ipv6_linklocal_address_set*) se reemplazan por el *servicio nxd_ipv6_address_set*.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-136">Note that the two services, *nxd_ipv6_global_address_set* and *nxd_ipv6_linklocal_address_set* are replaced with *nxd_ipv6_address_set service*.</span></span> <span data-ttu-id="dbd3c-137">Los dos servicios anteriores siguen estando disponibles para las aplicaciones de NetX Duo heredadas, pero finalmente quedarán en desuso.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-137">The former two services are still available for legacy NetX Duo applications but are eventually deprecated.</span></span> <span data-ttu-id="dbd3c-138">Se recomienda a los desarrolladores que utilicen *nxd_ipv6_address_set* en su lugar.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-138">Developers are encouraged to use *nxd_ipv6_address_set* instead.</span></span>

<span data-ttu-id="dbd3c-139">Una vez que la dirección IP se valida correctamente con NetX Duo, el servidor Telnet se inicia en la línea 215 con el servicio *nxd_telnet_server_start*.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-139">After successful IP address validation with NetX Duo, the Telnet Server is started at line 215 using the *nxd_telnet_server_start* service.</span></span> <span data-ttu-id="dbd3c-140">En la línea 226, el cliente Telnet se crea con el servicio *nx_telnet_client_create*.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-140">At line 226 the Telnet Client is created using the *nx_telnet_client_create* service.</span></span> <span data-ttu-id="dbd3c-141">Después, se conecta con el servidor Telnet en la línea 242 para las aplicaciones IPv4 y la línea 238 para las aplicaciones IPv6 que usan los servicios *nxd_telnet_client_connect* y *nx_telnet_client_connect*, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-141">It then connects with the Telnet Server on line 242 for IPv4 applications and line 238 for IPv6 applications using the *nxd_telnet_client_connect* and *nx_telnet_client_connect* services respectively.</span></span> <span data-ttu-id="dbd3c-142">Una vez que se realiza la validación y se establece la conexión con el servidor correctamente, realiza algunos intercambios antes de la desconexión.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-142">After successful validation and connection with the server, it makes a few exchanges before disconnecting.</span></span>

```c
/* This is a small demo of TELNET on the high-performance NetX Duo TCP/IP stack.  
       This demo relies on ThreadX and NetX Duo to show a simple TELNET connection,
       send, server echo, and then disconnection from the TELNET server.  */
    
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_telnet_client.h"
#include  "nxd_telnet_server.h"
#define     DEMO_STACK_SIZE         4096    
   
/* Define the ThreadX and NetX object control blocks...  */
TX_THREAD               test_thread;
NX_PACKET_POOL          pool_server;
NX_PACKET_POOL          pool_client;
NX_IP                   ip_server;
NX_IP                   ip_client;
   
/* Define TELNET objects.  */

NX_TELNET_SERVER        my_server;
NX_TELNET_CLIENT        my_client;


#ifdef FEATURE_NX_IPV6

/* Define NetX Duo IP address for the NetX Duo Telnet Server and Client. */

NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;

#endif

#define         SERVER_ADDRESS          IP_ADDRESS(1,2,3,4)
#define         CLIENT_ADDRESS          IP_ADDRESS(1,2,3,5)

/* Define the counters used in the demo application...  */
ULONG                   error_counter;

/* Define timeout in ticks for connecting and sending/receiving data. */

#define                 TELNET_TIMEOUT  200

/* Define function prototypes.  */

void    thread_test_entry(ULONG thread_input);
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define the application's TELNET Server callback routines.  */

void    telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection); 
void    telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection, 
                            NX_PACKET *packet_ptr);
void    telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection);

/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT    status;
CHAR    *pointer;
UINT    iface_index, address_index;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;
    
    /* Create the main thread.  */
    tx_thread_create(&test_thread, "test thread", thread_test_entry, 0,  
                     pointer, DEMO_STACK_SIZE, 
                     2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;
    
    /* Initialize the NetX system.  */
    nx_system_initialize();
    
    /* Create packet pool.  */
    nx_packet_pool_create(&pool_server, "Server NetX Packet Pool", 600, pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create an IP instance.  */
    nx_ip_create(&ip_server, "Server NetX IP Instance", SERVER_ADDRESS, 
                 0xFFFFFF00UL, &pool_server, _nx_ram_network_driver,
                 pointer, 4096, 1);
    
    pointer =  pointer + 4096;
    
    /* Create another packet pool. */
    nx_packet_pool_create(&pool_client, "Client NetX Packet Pool", 600, 
                          pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create another IP instance.  */
    nx_ip_create(&ip_client, "Client NetX IP Instance", CLIENT_ADDRESS, 
                 0xFFFFFF00UL, &pool_client, _nx_ram_network_driver, 
                 pointer, 4096, 1);
    
    pointer = pointer + 4096;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_server, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_client, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_server);
    nx_tcp_enable(&ip_client);

#ifdef FEATURE_NX_IPV6

    /* Next set the NetX Duo Telnet Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

#endif

    /* Create the NetX Duo TELNET Server.  */
    status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_server, 
                                      pointer, 2048, telnet_new_connection, telnet_receive_data, 
                                      telnet_connection_end);
    
    /* Check for errors.  */
    if (status)
        error_counter++;
    
    return;
}

/* Define the test thread.  */
void    thread_test_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
    
    /* Allow other threads (e.g. IP thread task) to run first. */
    tx_thread_sleep(100);
    
    #ifdef FEATURE_NX_IPV6
    /* Here's where we make the Telnet Client IPv6 enabled. */
    nxd_ipv6_enable(&ip_client);
    nxd_icmp_enable(&ip_client);     
    
    /* Wait till the IP task thread initializes the system. */
    tx_thread_sleep(100);
        
    /* Set up the Client addresses on the Client IP for the primary interface. */
    if_index = 0;
    
    status = nxd_ipv6_address_set(&ip_ client, iface_index, NX_NULL, 10, 
                                  &address_index);
    status = nxd_ipv6_address_set(&ip_ client, iface_index, & client _ip_address, 
                                   64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */
    tx_thread_sleep(400);
    
    /* Set up the Server addresses on the Client IP. */
    iface_index = 0;
    status = nxd_ipv6_address_set (&ip_server, iface_index, NX_NULL, 10, 
                                   &address_index);
    
    status = nxd_ ipv6_address _set(&ip_server, iface_index, & server _ip_address, 
                                     64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */     
    tx_thread_sleep(400);
    
    #endif
    
    /* Start the TELNET Server.  */
    status =  nx_telnet_server_start(&my_server);
    
    /* Check for errors.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Create a TELENT client instance.  */
    status =  nx_telnet_client_create(&my_client, "My TELNET Client", 
                                      &ip_client, 600);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    #ifdef FEATURE_NX_IPV6
    
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 
                                             TELNET_TIMEOUT);
    
    #else
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nx_telnet_client_connect(&my_client, SERVER_ADDRESS, 23,
                                            TELNET_TIMEOUT);
    #endif
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Allocate a packet.  */
    status =  nx_packet_allocate(&pool_client, &my_packet, NX_TCP_PACKET, 
                                  NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Build a simple 1-byte message.  */
    nx_packet_data_append(my_packet, "a", 1, &pool_client, NX_WAIT_FOREVER);
    
    /* Send the packet to the TELNET Server.  */
    status =  nx_telnet_client_packet_send(&my_client, my_packet, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Pickup the Server header.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the Server's banner
        message sent by the Server callback function below.  Just
        release it for this demo.  */
    nx_packet_release(my_packet);
    
    /* Pickup the Server echo of the character.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the character 'a' that
        we sent earlier.  Just release the packet for now.  */
    nx_packet_release(my_packet);
    
    /* Now disconnect form the TELNET Server.  */
    status =  nx_telnet_client_disconnect(&my_client, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Delete the TELNET Client.  */
    status =  nx_telnet_client_delete(&my_client);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
}

/* This routine is called by the NetX Telnet Server whenever a new Telnet client 
    connection is established.  */
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{

UINT        status;
NX_PACKET   *packet_ptr;

    /* Allocate a packet for client greeting. */
    status =  nx_packet_allocate(&pool_server, &packet_ptr, NX_TCP_PACKET, 
                                  NX_NO_WAIT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Build a banner message and a prompt.  */
    nx_packet_data_append(packet_ptr,"**** Welcome to NetX TELNET Server ****\r\n\r\n\r\n", 45,                            
                         &pool_server, NX_NO_WAIT);

    nx_packet_data_append(packet_ptr, "NETX> ", 6, &pool_server, NX_NO_WAIT);
    
    /* Send the packet to the client.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }
    return;
}

/* This routine is called by the NetX Telnet Server whenever data is present on a 
    Telnet client connection.  */          
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection,
                          NX_PACKET *packet_ptr)
{

UINT    status;
UCHAR   alpha;

    /* This demo echoes the character back; on <cr,lf> sends a new prompt back to 
        the client.  A real system would likely buffer the character(s) received in a 
        buffer associated with the supplied logical connection and process it.  */

    /* Just throw away carriage returns.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\r') && (packet_ptr -> nx_packet_length == 1))
    {
        printf("telnet server received just a CRLF\n");

        nx_packet_release(packet_ptr);
        return;
    }

    /* Setup new line on line feed.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\n') || (packet_ptr -> nx_packet_prepend_ptr[1] == '\n'))
    {
        /* Clean up the packet.  */
        packet_ptr -> nx_packet_length =  0;
        packet_ptr -> nx_packet_prepend_ptr =  packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;
        packet_ptr -> nx_packet_append_ptr =   packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;

        /* Build the next prompt.  */
        nx_packet_data_append(packet_ptr, "\r\nNETX> ", 8, &pool_server, 
                              NX_NO_WAIT);

        /* Send the packet to the client.  */
        status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                               packet_ptr, TELNET_TIMEOUT);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            nx_packet_release(packet_ptr);
        }
        return;
    }

    /* Pickup first character (usually only one from client).  */
    alpha =  packet_ptr -> nx_packet_prepend_ptr[0];

    /* Echo character.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }

    /* Check for a disconnection.  */
    if (alpha == 'q')
    {
        /* Initiate server disconnection.  */
        nx_telnet_server_disconnect(server_ptr, logical_connection);
    }
}


/* This routine is called by the NetX Telnet Server when the client disconnects.  */
void  telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{
    /* Cleanup any application specific connection or buffer information.  */
    return;
}
```

## <a name="configuration-options"></a><span data-ttu-id="dbd3c-143">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="dbd3c-143">Configuration Options</span></span>

<span data-ttu-id="dbd3c-144">Hay varias opciones de configuración para compilar Telnet para NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-144">There are several configuration options for building Telnet for NetX Duo.</span></span> <span data-ttu-id="dbd3c-145">La aplicación puede establecer estos elementos #defines antes de la inclusión de *nxd_telnet_server.h* y *nxd_telnet_client.h.*</span><span class="sxs-lookup"><span data-stu-id="dbd3c-145">These #defines can be set by the application prior to inclusion of *nxd_telnet_server.h*.and *nxd_telnet_client.h.*</span></span>

<span data-ttu-id="dbd3c-146">A continuación, se muestra una lista de todas las opciones, en que se describe con detalle cada una de ellas:</span><span class="sxs-lookup"><span data-stu-id="dbd3c-146">Following is a list of all options, where each is described in detail:</span></span>  
  
- <span data-ttu-id="dbd3c-147">**NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica de Telnet.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-147">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic Telnet error checking.</span></span> <span data-ttu-id="dbd3c-148">Normalmente se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-148">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="dbd3c-149">**NX_TELNET_MAX_CLIENTS**: número máximo de clientes de Telnet admitidos por el subproceso de servidor.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-149">**NX_TELNET_MAX_CLIENTS**: The maximum number of Telnet Clients supported by the Server thread.</span></span> <span data-ttu-id="dbd3c-150">De forma predeterminada, este valor se define como 4 para especificar un máximo de 4 clientes a la vez.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-150">By default, this value is defined as 4 to specify a maximum of 4 clients at a time.</span></span>
- <span data-ttu-id="dbd3c-151">**NX_TELNET_SERVER_PRIORITY**: prioridad del subproceso del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-151">**NX_TELNET_SERVER_PRIORITY**: The priority of the Telnet Server thread.</span></span> <span data-ttu-id="dbd3c-152">De forma predeterminada, este valor se define como 16 para especificar la prioridad 16.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-152">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="dbd3c-153">**NX_TELNET_TOS**: tipo de servicio necesario para las solicitudes TCP de Telnet.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-153">**NX_TELNET_TOS**: Type of service required for the Telnet TCP requests.</span></span> <span data-ttu-id="dbd3c-154">De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar</span><span class="sxs-lookup"><span data-stu-id="dbd3c-154">By default, this value is defined as NX_IP_NORMAL to indicate</span></span>  
<span data-ttu-id="dbd3c-155">el servicio de paquetes IP normal.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-155">normal IP packet service.</span></span>
- <span data-ttu-id="dbd3c-156">**NX_TELNET_FRAGMENT_OPTION**: habilitación del fragmento para solicitudes TCP de Telnet.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-156">**NX_TELNET_FRAGMENT_OPTION**: Fragment enable for Telnet TCP requests.</span></span> <span data-ttu-id="dbd3c-157">De forma predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de TCP de Telnet.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-157">By default, this value is NX_DONT_FRAGMENT to disable Telnet TCP fragmenting.</span></span>
- <span data-ttu-id="dbd3c-158">**NX_TELNET_SERVER_WINDOW_SIZE**: tamaño de la ventana de socket del servidor.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-158">**NX_TELNET_SERVER_WINDOW_SIZE**: Server socket window size.</span></span> <span data-ttu-id="dbd3c-159">De forma predeterminada, este valor es 2048 bytes.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-159">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="dbd3c-160">**NX_TELNET_TIME_TO_LIVE**: especifica el número de enrutadores que este paquete puede pasar antes de que se descarte.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-160">**NX_TELNET_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="dbd3c-161">El valor predeterminado se establece en 0x80.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-161">The default value is set to 0x80.</span></span>
- <span data-ttu-id="dbd3c-162">**NX_TELNET_SERVER_TIMEOUT**: especifica el número de tics de ThreadX durante los que se suspenderán los servicios internos.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-162">**NX_TELNET_SERVER_TIMEOUT**: Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="dbd3c-163">El valor predeterminado se establece en 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-163">The default value is set to 10 seconds.</span></span>
- <span data-ttu-id="dbd3c-164">**NX_TELNET_ACTIVITY_TIMEOUT**: especifica el número de segundos que pueden transcurrir sin ninguna actividad antes de que el servidor desconecte la conexión del cliente.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-164">**NX_TELNET_ACTIVITY_TIMEOUT**: Specifies the number of seconds that can elapse without any activity before the Server disconnects the Client connection.</span></span> <span data-ttu-id="dbd3c-165">El valor predeterminado se establece en 600 segundos.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-165">The default value is set to 600 seconds.</span></span>
- <span data-ttu-id="dbd3c-166">**NX_TELNET_TIMEOUT_PERIOD**: especifica el número de segundos entre comprobaciones del tiempo de espera de la actividad del cliente.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-166">**NX_TELNET_TIMEOUT_PERIOD**: Specifies the number of seconds between checking for Client activity timeouts.</span></span> <span data-ttu-id="dbd3c-167">El valor predeterminado se establece en 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-167">The default value is set to 60 seconds.</span></span>
- <span data-ttu-id="dbd3c-168">**NX_TELNET_SERVER_OPTION_DISABLE**: si se define, la negociación de la opción de Telnet se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-168">**NX_TELNET_SERVER_OPTION_DISABLE**: Defined, Telnet option negotiation is disabled.</span></span> <span data-ttu-id="dbd3c-169">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-169">By default this option is not defined.</span></span>
- <span data-ttu-id="dbd3c-170">**NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: si se define, el grupo de paquetes del servidor Telnet se debe crear externamente.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-170">**NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: If defined, the Telnet Server packet pool must be created externally.</span></span> <span data-ttu-id="dbd3c-171">Esta opción solo es significativa si no se define NX_TELNET_SERVER_OPTION_DISABLE.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-171">This is only meaningful if NX_TELNET_SERVER_OPTION_DISABLE is not defined.</span></span> <span data-ttu-id="dbd3c-172">De forma predeterminada, esta opción no está definida y el subproceso del servidor Telnet crea su propio grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-172">By default this option is not defined and the Telnet Server thread creates its own packet pool.</span></span>
- <span data-ttu-id="dbd3c-173">**NX_TELNET_SERVER_PACKET_PAYLOAD**: define el tamaño de la carga de paquetes creada por el servidor Telnet para la negociación de la opción.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-173">**NX_TELNET_SERVER_PACKET_PAYLOAD**: Defines the size of the packet payload created by the Telnet Server for option negotiation.</span></span> <span data-ttu-id="dbd3c-174">Tenga en cuenta que el servidor Telnet solo crea este grupo de paquetes si no se ha definido NX_TELNET_SERVER _OPTION_DISABLE (las opciones de Telnet están habilitadas).</span><span class="sxs-lookup"><span data-stu-id="dbd3c-174">Note that the Telnet Server only creates this packet pool if NX_TELNET_SERVER _OPTION_DISABLE is not defined (Telnet options are enabled).</span></span> <span data-ttu-id="dbd3c-175">El valor predeterminado de esta opción es 300.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-175">The default value of this option is 300.</span></span>
- <span data-ttu-id="dbd3c-176">**NX_TELNET_SERVER_PACKET_POOL_SIZE**: define el tamaño del grupo de paquetes del servidor Telnet usado para las negociaciones de Telnet.</span><span class="sxs-lookup"><span data-stu-id="dbd3c-176">**NX_TELNET_SERVER_PACKET_POOL_SIZE**: Defines the size of the Telnet Server packet pool used for Telnet negotiations.</span></span> <span data-ttu-id="dbd3c-177">Tenga en cuenta que el servidor Telnet solo crea este grupo de paquetes si no se ha definido NX_TELNET_SERVER _OPTION_DISABLE (las opciones de Telnet están habilitadas).</span><span class="sxs-lookup"><span data-stu-id="dbd3c-177">Note that the Telnet Server only creates this packet pool if NX_TELNET_SERVER _OPTION_DISABLE is not defined (Telnet options are enabled).</span></span> <span data-ttu-id="dbd3c-178">El valor predeterminado de esta opción es 2048 (\~5-6 paquetes).</span><span class="sxs-lookup"><span data-stu-id="dbd3c-178">The default value of this option is 2048 (\~5-6 packets).</span></span>
