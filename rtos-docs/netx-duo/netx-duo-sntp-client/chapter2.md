---
title: 'Capítulo 2: Instalación y uso del cliente SNTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del cliente SNTP de NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd917e7e70ce21dbff6c8081c2ff115c0acad8a8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814553"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-sntp-client"></a><span data-ttu-id="1ac64-103">Capítulo 2: Instalación y uso del cliente SNTP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="1ac64-103">Chapter 2 - Installation and Use of Azure RTOS NetX Duo SNTP Client</span></span>

<span data-ttu-id="1ac64-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del cliente SNTP de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo SNTP Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="1ac64-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="1ac64-105">Product Distribution</span></span>

<span data-ttu-id="1ac64-106">SNTP para NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="1ac64-106">SNTP for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="1ac64-107">El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="1ac64-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="1ac64-108">**nxd_sntp_client.c**: archivo de código fuente de C del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-108">**nxd_sntp_client.c** SNTP Client C source file</span></span>  
- <span data-ttu-id="1ac64-109">**nxd_sntp_client.h**: archivo de encabezado del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-109">**nxd_sntp_client.h** SNTP Client Header file</span></span>  
- <span data-ttu-id="1ac64-110">**demo_netxduo_sntp_client.c**: aplicación de demostración del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-110">**demo_netxduo_sntp_client.c** Demonstration SNTP Client application</span></span>  
- <span data-ttu-id="1ac64-111">**nxd_sntp_client.pdf**: manual del usuario del cliente SNTP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-111">**nxd_sntp_client.pdf** NetX Duo SNTP Client User Guide</span></span>  

## <a name="netx-duo-sntp-client-installation"></a><span data-ttu-id="1ac64-112">Instalación del cliente SNTP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="1ac64-112">NetX Duo SNTP Client Installation</span></span>

<span data-ttu-id="1ac64-113">Para usar SNTP para NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-113">In order to use SNTP for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="1ac64-114">Por ejemplo, si NetX Duo está instalado en el directorio " *\threadx\arm7\green*", deben copiarse en este directorio los archivos del cliente SNTP de NetX Duo *nxd_sntp_client.c* y *nxd_sntp_client.h* (*nx_sntp_client.c* y *nx_sntp_client.h* en NetX).</span><span class="sxs-lookup"><span data-stu-id="1ac64-114">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the NetX Duo SNTP Client files *nxd_sntp_client.c* and *nxd_sntp_client.h* (*nx_sntp_client.c* and *nx_sntp_client.h* in NetX) should be copied into this directory.</span></span>

## <a name="using-netx-duo-sntp-client"></a><span data-ttu-id="1ac64-115">Uso del cliente SNTP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="1ac64-115">Using NetX Duo SNTP Client</span></span>

<span data-ttu-id="1ac64-116">Resulta fácil usar el cliente SNTP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-116">Using NetX Duo SNTP Client is easy.</span></span> <span data-ttu-id="1ac64-117">Básicamente, el código de la aplicación debe incluir *nxd_sntp_client.h* después de incluir *tx_api.h, fx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX Duo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1ac64-117">Basically, the application code must include *nxd_sntp_client.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="1ac64-118">Después de incluir *nxd_sntp_client.h*, el código de la aplicación puede realizar las llamadas a las funciones SNTP que se especifican más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="1ac64-118">Once *nxd_sntp_client.h* is included, the application code is then able to make the SNTP function calls specified later in this guide.</span></span> <span data-ttu-id="1ac64-119">La aplicación también debe incluir *nxd_sntp_client.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="1ac64-119">The application must also include *nxd_sntp_client.c* in the build process.</span></span> <span data-ttu-id="1ac64-120">Estos archivos deben compilarse de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1ac64-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="1ac64-121">Esto es todo lo que se necesita para usar el cliente SNTP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-121">This is all that is required to use NetX Duo SNTP Client.</span></span>

> [!NOTE]
> <span data-ttu-id="1ac64-122">Dado que el cliente SNTP de NetX Duo utiliza los servicios de UDP de NetX Duo, UDP debe habilitarse con una llamada a *nx_udp_enable* antes de usar los servicios SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-122">Since the NetX Duo SNTP Client utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using SNTP services.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="1ac64-123">Pequeño sistema de ejemplo</span><span class="sxs-lookup"><span data-stu-id="1ac64-123">Small Example System</span></span>

<span data-ttu-id="1ac64-124">A continuación se muestra un ejemplo de cómo usar SNTP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-124">An example of how to use NetX Duo SNTP is shown below.</span></span> <span data-ttu-id="1ac64-125">Tenga en cuenta que **no** se garantiza que este ejemplo funcione tal cual está en su sistema.</span><span class="sxs-lookup"><span data-stu-id="1ac64-125">Note that this example is **not** guaranteed to work as is on your system.</span></span> <span data-ttu-id="1ac64-126">Es posible que deba realizar ajustes para su sistema y hardware concretos.</span><span class="sxs-lookup"><span data-stu-id="1ac64-126">You may need to make adjustments for your particular system and hardware.</span></span> <span data-ttu-id="1ac64-127">Por ejemplo, tendrá que reemplazar el controlador de RAM de NetX con su función de controlador real.</span><span class="sxs-lookup"><span data-stu-id="1ac64-127">For example you will have to replace the NetX ram driver with your actual driver function.</span></span> <span data-ttu-id="1ac64-128">Este ejemplo está diseñado con el único fin de servir de demostración.</span><span class="sxs-lookup"><span data-stu-id="1ac64-128">This example is intended strictly for demonstration purposes.</span></span>

<span data-ttu-id="1ac64-129">En este ejemplo, se incluye el archivo de encabezado SNTP *nxd_sntp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="1ac64-129">In this example, the SNTP header file *nxd_sntp_client.h* is included.</span></span> <span data-ttu-id="1ac64-130">El cliente SNTP se crea en "*tx_application_define*".</span><span class="sxs-lookup"><span data-stu-id="1ac64-130">The SNTP Client is created in “*tx_application_define*”.</span></span> <span data-ttu-id="1ac64-131">A la hora de crearlo, tenga en cuenta que las funciones del beso de la muerte y el controlador del segundo intercalar son opcionales.</span><span class="sxs-lookup"><span data-stu-id="1ac64-131">Note that the kiss of death and leap second handler functions are optional when creating the SNTP Client.</span></span>

<span data-ttu-id="1ac64-132">Esta demostración se puede usar con IPv6 o IPv4.</span><span class="sxs-lookup"><span data-stu-id="1ac64-132">This demo can be used with IPv6 or IPv4.</span></span> <span data-ttu-id="1ac64-133">Para ejecutar el cliente SNTP en IPv6, defina USE_IPV6.</span><span class="sxs-lookup"><span data-stu-id="1ac64-133">To run the SNTP Client over IPv6, define USE_IPV6.</span></span> <span data-ttu-id="1ac64-134">IPv6 también debe estar habilitado en NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-134">IPv6 must be enabled in NetX Duo as well.</span></span> <span data-ttu-id="1ac64-135">El host del cliente SNTP está configurado para la validación de direcciones IPv6 y los servicios ICMPv6 e IPv6 en NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-135">The SNTP Client host is set up for IPv6 address validation and ICMPv6 and IPv6 services in NetX Duo.</span></span> <span data-ttu-id="1ac64-136">Consulte el manual del usuario de NetX Duo para obtener más detalles sobre la compatibilidad con IPv6 en NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-136">See the NetX Duo User Guide for more details on IPv6 support in NetX Duo.</span></span>

<span data-ttu-id="1ac64-137">A continuación, se debe inicializar el cliente SNTP para el modo de unidifusión o difusión.</span><span class="sxs-lookup"><span data-stu-id="1ac64-137">Then the SNTP Client must be initialized for either unicast or broadcast mode.</span></span>

<span data-ttu-id="1ac64-138">El cliente SNTP escribe inicialmente las actualizaciones de hora del servidor en su propia estructura de datos interna.</span><span class="sxs-lookup"><span data-stu-id="1ac64-138">SNTP Client initially writes Server time updates to its own internal data structure.</span></span> <span data-ttu-id="1ac64-139">Esto no es lo mismo que la hora local del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-139">This is not the same as the device local time.</span></span> <span data-ttu-id="1ac64-140">Esta última se puede establecer como una hora de base de referencia en el cliente SNTP antes de iniciar el subproceso del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-140">The device local time can be set as a baseline time in the SNTP Client before starting the SNTP Client thread.</span></span> <span data-ttu-id="1ac64-141">Esto resulta útil si se configura el cliente SNTP (NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP establecido en NX_FALSE) para comparar la primera actualización del servidor con NX_SNTP_CLIENT_MAX_ADJUSTMENT (valor predeterminado de 180 milisegundos).</span><span class="sxs-lookup"><span data-stu-id="1ac64-141">This is useful if the SNTP Client is configured (NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP set to NX_FALSE) to compare the first Server update to the NX_SNTP_CLIENT_MAX_ADJUSTMENT (default value 180 milliseconds).</span></span> <span data-ttu-id="1ac64-142">De lo contrario, el cliente SNTP establecerá la hora local inicial directamente cuando obtenga la primera actualización del servidor.</span><span class="sxs-lookup"><span data-stu-id="1ac64-142">Otherwise the SNTP Client will set the initial local time directly when it gets the first update from the Server.</span></span>

<span data-ttu-id="1ac64-143">La hora base de referencia se aplica al cliente SNTP mediante el servicio *nx_sntp_client_set_local_time*.</span><span class="sxs-lookup"><span data-stu-id="1ac64-143">A baseline time is applied to the SNTP Client using the *nx_sntp_client_set_local_time* service.</span></span>

<span data-ttu-id="1ac64-144">El cliente SNTP se inicia para el modo de unidifusión y difusión, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1ac64-144">The SNTP Client is started on for unicast and broadcast mode respectively.</span></span> <span data-ttu-id="1ac64-145">Durante un intervalo determinado (ligeramente menor que el intervalo de sondeo de unidifusión), la aplicación actualiza la hora local del cliente SNTP, mediante el servicio *nx_sntp_client_set_local_time*, a partir del "reloj en tiempo real" que simulamos incrementando simplemente los segundos y los milisegundos de la hora actual.</span><span class="sxs-lookup"><span data-stu-id="1ac64-145">For a certain interval (slightly less than the unicast polling interval) the application updates the SNTP Client local time, using the *nx_sntp_client_set_local_time*, from the “real time clock” which we simulate by just incrementing the seconds and milliseconds of the current time.</span></span> <span data-ttu-id="1ac64-146">Después de cada intervalo, la aplicación comprueba periódicamente si hay actualizaciones del servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-146">After each interval, the application then periodically checks for updates from the SNTP server.</span></span> <span data-ttu-id="1ac64-147">El servicio *nx_sntp_client_receiving_updates* comprueba que el cliente SNTP está recibiendo actualizaciones válidas.</span><span class="sxs-lookup"><span data-stu-id="1ac64-147">The *nx_sntp_client_receiving _updates* service verifies that the SNTP Client is currently receiving valid updates.</span></span> <span data-ttu-id="1ac64-148">Si es así, recuperará la hora de actualización más reciente mediante el servicio *nx_sntp_client_get_local_time_extended*.</span><span class="sxs-lookup"><span data-stu-id="1ac64-148">If so, it will retrieve the latest update time using the *nx_sntp_client_get_local_time_extended* service.</span></span>

<span data-ttu-id="1ac64-149">El cliente SNTP se puede detener en cualquier momento mediante el servicio *nx_sntp_client_stop* si, por ejemplo, se detecta que ya no recibe actualizaciones válidas.</span><span class="sxs-lookup"><span data-stu-id="1ac64-149">The SNTP Client can be stopped at any time using the *nx_sntp_client_stop* service if for example it detects the SNTP Client is no longer receiving valid updates..</span></span> <span data-ttu-id="1ac64-150">Para reiniciar el cliente, la aplicación debe llamar al servicio de inicialización de unidifusión o de difusión y, a continuación, llamar a los servicios de ejecución de unidifusión o difusión.</span><span class="sxs-lookup"><span data-stu-id="1ac64-150">To restart the Client, the application must call either the unicast or broadcast initialize service and then call either unicast or broadcast run services.</span></span> <span data-ttu-id="1ac64-151">Mientras la tarea de subproceso del cliente SNTP está detenida, el cliente SNTP puede cambiar los servidores SNTP y los modos (unidifusión o difusión) si es necesario; por ejemplo, si el servidor SNTP anterior parece estar inactivo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-151">While the SNTP Client thread task is stopped, the SNTP Client can switch SNTP servers and modes (unicast or broadcast) if needed e.g. the previous SNTP server appears to be down.</span></span>

```c
/* 
   This is a small demo of the NetX SNTP Client on the high-performance NetX
   TCP/IP stack. This demo relies on Thread, NetX and NetX SNTP Client API to
   execute the Simple Network Time Protocol in unicast and broadcast modes.  
 */

#include <stdio.h>
#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_sntp_client.h"
                
/* Define SNTP packet size. */
#define NX_SNTP_CLIENT_PACKET_SIZE      (NX_UDP_PACKET + 100)

/* Define SNTP packet pool size. */
#define NX_SNTP_CLIENT_PACKET_POOL_SIZE      (4 * (NX_SNTP_CLIENT_PACKET_SIZE + 
                                                            sizeof(NX_PACKET)))

/* Define how often the demo checks for SNTP updates. */
#define DEMO_PERIODIC_CHECK_INTERVAL      (1 * NX_IP_PERIODIC_RATE) 

/* Define how often we check on SNTP server status. 
   We expect updates from the SNTP server about every hour using 
   the SNTP Client defaults. For testing
   make this (much) shorter. */
#define CHECK_SNTP_UPDATES_TIMEOUT       (180 * NX_IP_PERIODIC_RATE) 

/* Set up generic network driver for demo program. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Application defined services of the NetX SNTP Client. */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator);
UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, 
                                        UINT KOD_code);
VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time);


/* Set up client thread and network resources. */

NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;
TX_THREAD           demo_client_thread;
NX_SNTP_CLIENT      demo_sntp_client;
TX_EVENT_FLAGS_GROUP sntp_flags;

#define DEMO_SNTP_UPDATE_EVENT  1

/* Configure the SNTP Client to use IPv6. If not enabled, the 
   Client will use IPv4.  Note: IPv6 must be enabled in NetX Duo
   for the Client to communicate over IPv6.    */
#ifdef FEATURE_NX_IPV6
/* #define USE_IPV6 */
#endif /* FEATURE_NX_IPV6 */


/* Configure the SNTP Client to use unicast SNTP. */
#define USE_UNICAST


#define CLIENT_IP_ADDRESS       IP_ADDRESS(192,2,2,66)
#define SERVER_IP_ADDRESS       IP_ADDRESS(192,2,2,92)
#define SERVER_IP_ADDRESS_2     SERVER_IP_ADDRESS

/* Set up the SNTP network and address index; */
UINT     iface_index =0;
UINT     prefix = 64;   
UINT     address_index;

/* Set up client thread entry point. */
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return 0;
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT     status;
UCHAR    *free_memory_pointer;


    free_memory_pointer = (UCHAR *)first_unused_memory;

    /* Create client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool, 
                                "SNTP Client Packet Pool",
                                NX_SNTP_CLIENT_PACKET_SIZE, 
                                free_memory_pointer, 
                                NX_SNTP_CLIENT_PACKET_POOL_SIZE);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + NX_SNTP_CLIENT_PACKET_POOL_SIZE;

    /* Create Client IP instances */
    status = nx_ip_create(&client_ip, "SNTP IP Instance", 
                                        CLIENT_IP_ADDRESS, 
                                        0xFFFFFF00UL, 
                                        &client_packet_pool, 
                                       _nx_ram_network_driver, 
                                       free_memory_pointer, 2048, 1);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    free_memory_pointer =  free_memory_pointer + 2048;

#ifndef NX_DISABLE_IPV4
    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 2048);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;
    
    /* Enable UDP for client. */
    status =  nx_udp_enable(&client_ip);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

#ifndef NX_DISABLE_IPV4
    status = nx_icmp_enable(&client_ip);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "SNTP Client Thread", 
                                                demo_client_thread_entry, 
                                              (ULONG)(&demo_sntp_client), 
                                                free_memory_pointer, 2048, 
                                                  4, 4, TX_NO_TIME_SLICE, 
                                                        TX_DONT_START);

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Create the event flags. */
    status = tx_event_flags_create(&sntp_flags, "SNTP event flags");

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* set the SNTP network interface to the primary interface. */
    iface_index = 0;

    /* Create the SNTP Client to run in broadcast mode.. */
status =  nx_sntp_client_create(&demo_sntp_client, &client_ip,
                           iface_index, &client_packet_pool,  
                               leap_second_handler, 
                               kiss_of_death_handler, 
                               NULL /* no random_number_generator callback */);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        /* Bail out!*/
        return;
    }

    tx_thread_resume(&demo_client_thread);

    return;
}

/* Define size of buffer to display client's local time. */
#define BUFSIZE 50

/* Define the client thread.  */
void    demo_client_thread_entry(ULONG info)
{

UINT   status;
UINT   spin;
UINT   server_status;
ULONG  base_seconds;
ULONG  base_fraction;
ULONG  seconds, milliseconds, microseconds, fraction;
UINT   wait = 0;
UINT   error_counter = 0;
ULONG  events = 0;
#ifdef USE_IPV6
NXD_ADDRESS sntp_server_address;
NXD_ADDRESS client_ip_address;
#endif

    NX_PARAMETER_NOT_USED(info);

    /* Give other threads (IP instance) initialize first. */
    tx_thread_sleep(NX_IP_PERIODIC_RATE); 

#ifdef USE_IPV6
    /* Set up IPv6 services. */
    status = nxd_ipv6_enable(&client_ip);

    status += nxd_icmp_enable(&client_ip);

    if (status  != NX_SUCCESS)
        return;

    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Set the IPv6 server address. */
    sntp_server_address.nxd_ip_address.v6[0] = 0x20010db8;  
    sntp_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    sntp_server_address.nxd_ip_address.v6[2] = 0x0;
    sntp_server_address.nxd_ip_address.v6[3] = 0x00000106;
    sntp_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address. */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, NULL);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

     /* Set the host global IP address. We are assuming a 64 
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, 
                                        &client_ip_address, 
                                    prefix, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

    /* Wait while NetX Duo validates the global and link local addresses. */
    tx_thread_sleep(5 * NX_IP_PERIODIC_RATE);

#endif

    /* Setup time update callback function. */
    nx_sntp_client_set_time_update_notify(&demo_sntp_client, 
                                        time_update_callback);

    /* Set up client time updates depending on mode. */
#ifdef USE_UNICAST

    /* Initialize the Client for unicast mode to 
       poll the SNTP server once an hour. */
#ifdef USE_IPV6
/* Use the duo service to set up the Client and set the IPv6 SNTP server.
   Note: this can take either an IPv4 or IPv6 address. */
    status = nxd_sntp_client_initialize_unicast(&demo_sntp_client, 
                                            &sntp_server_address);
#else
    /* Use the IPv4 service to set up the Client and set the IPv4 SNTP server. */
    status = nx_sntp_client_initialize_unicast(&demo_sntp_client, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */


#else   /* Broadcast mode */

/* Initialize the Client for broadcast mode, no roundtrip calculation
   required and a broadcast SNTP service. */
#ifdef USE_IPV6
    /* Use the duo service to initialize the Client 
       and set IPv6 SNTP all hosts multicast address. 
       (Note: This can take either an IPv4 or IPv6 address.)*/
    status = nxd_sntp_client_initialize_broadcast(&demo_sntp_client, 
                                                &sntp_server_address, 
                                                            NX_NULL);
#else

    /* Use the IPv4 service to initialize the Client and set 
       IPv4 SNTP broadcast address. */
    status = nx_sntp_client_initialize_broadcast(&demo_sntp_client,  
                                                NX_NULL, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */
#endif  /* USE_UNICAST */

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the base time which is approximately the number of seconds since
       the turn of the last century. If this is not available in SNTP format,
       the nx_sntp_client_utility_add_msecs_to_ntp_time service can convert
       milliseconds to fraction.  For how to compute NTP seconds from real
   time, read the NetX SNTP User Guide. Otherwise set the base time to 
   zero and set NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP to NX_TRUE for
       the SNTP CLient to accept the first time update without applying a
       minimum or maximum adjustment parameters
      (NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT and
       NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT). */

    base_seconds =  0xd2c96b90;  /* Jan 24, 2012 UTC */
    base_fraction = 0xa132db1e;

    /* Apply to the SNTP Client local time.  */
status = nx_sntp_client_set_local_time(&demo_sntp_client, base_seconds,
                                base_fraction);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Run whichever service the client is configured for. */
#ifdef USE_UNICAST
    status = nx_sntp_client_run_unicast(&demo_sntp_client);
#else
    status = nx_sntp_client_run_broadcast(&demo_sntp_client);
#endif  /* USE_UNICAST */

    if (status != NX_SUCCESS)
    {
        return;
    }

    spin = NX_TRUE;

    /* Now check periodically for time changes. */
    while(spin)
    {
        /* Wait for a server update event. */
        tx_event_flags_get(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, 
                                          TX_OR_CLEAR, &events, 
                                 DEMO_PERIODIC_CHECK_INTERVAL);

        if (events == DEMO_SNTP_UPDATE_EVENT)
        {

            /* Check for valid SNTP server status. */
            status = nx_sntp_client_receiving_updates(&demo_sntp_client,
                                               &server_status);

            if ((status != NX_SUCCESS) || (server_status == NX_FALSE))
            {

                /* We do not have a valid update. Skip processing any time
                   data. If this happens repeatedly, consider stopping the
                   SNTP Client thread, picking another SNTP server and
                   resuming the SNTP Client thread task (more details about
                   that in the comments at the end of this function).
                 
                   If SNTP Client configurable parameters are too restrictive,
                   such as Max Adjustment, that may also cause valid server
                   updates to be rejected. Configurable parameters, however,
                   cannot be changed at run time.
                 */
                 
                continue;
            }

            /* We have a valid update.  Get the SNTP Client time.  */
            status = nx_sntp_client_get_local_time_extended(&demo_sntp_client, 
                                                    &seconds, &fraction,  
                                                    NX_NULL, 0); 

            /* Convert fraction to microseconds. */
            nx_sntp_client_utility_fraction_to_usecs(fraction, &microseconds);

            milliseconds = ((microseconds + 500) / 1000);

            if (status != NX_SUCCESS)
            {
                printf("Internal error with getting local time 0x%x\n", 
                       status);
                error_counter++;
            }
            else
            {
                printf("\nSNTP updated\n");
                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }

            /* Clear all events in our event flag. */
            events = 0;
        }
        else
        {

            /* No SNTP update event.             
               In the meantime, if we have an RTC we might want to check
               its notion of time. In this demo, we simulate the passage of 
               time on our 'RTC' really just the CPU counter, assuming that 
               seconds and milliseconds have previously been set to a base 
              (starting) time (as was the SNTP Client before running it) 
             */

            seconds += 1;
            milliseconds += 1;

            /* Update our timer. */
            wait += DEMO_PERIODIC_CHECK_INTERVAL;

            /* Check if it is time to display the local 'RTC' time. */
            if (wait >= CHECK_SNTP_UPDATES_TIMEOUT)
            {
                /* It is. Reset the timeout and print local time. */
                wait = 0;

                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }           
        }
    }

/* We can stop the SNTP service if for example we think the SNTP server 
   has stopped sending updates.
     
       To restart the SNTP Client, simply call the
       nx_sntp_client_initialize_unicast or
       nx_sntp_client_initialize_broadcast using another SNTP server IP
       address as input, and resume the SNTP Client by calling
       nx_sntp_client_run_unicast or
       nx_sntp_client_run_braodcast. */
    status = nx_sntp_client_stop(&demo_sntp_client);

    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* When done with the SNTP Client, we delete it */
    status = nx_sntp_client_delete(&demo_sntp_client);

    return;
}


/* This application defined handler for handling an 
   impending leap second is not required by 
   the SNTP Client. The default handler below only logs the
   event for every time stamp received with the 
   leap indicator set.  */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator)
{
    NX_PARAMETER_NOT_USED(client_ptr);
    NX_PARAMETER_NOT_USED(leap_indicator);

    /* Handle the leap second handler... */

    return NX_SUCCESS;
}

/* This application defined handler for handling 
   a Kiss of Death packet is not required by the SNTP Client. 
   A KOD handler should determine if the Client task should continue vs. 
   abort sending/receiving time data from its current time server, 
   and if aborting if it should remove
   the server from its active server list. 

   Note that the KOD list of codes is subject to change. The list
   below is current at the time of this software release. */

UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, UINT KOD_code)
{

UINT    remove_server_from_list = NX_FALSE;
UINT    status = NX_SUCCESS;

    NX_PARAMETER_NOT_USED(client_ptr);

    /* Handle kiss of death by code group. */
    switch (KOD_code)
    {

        case NX_SNTP_KOD_RATE:
        case NX_SNTP_KOD_NOT_INIT:
        case NX_SNTP_KOD_STEP:

            /* Find another server while this one 
               is temporarily out of service.  */
            status =  NX_SNTP_KOD_SERVER_NOT_AVAILABLE;

        break;

        case NX_SNTP_KOD_AUTH_FAIL:
        case NX_SNTP_KOD_NO_KEY:
        case NX_SNTP_KOD_CRYP_FAIL:

            /* These indicate the server will not 
               service client with time updates
               without successful authentication. */


            remove_server_from_list =  NX_TRUE;

        break;


        default:

            /* All other codes. Remove server 
               before resuming time updates. */

            remove_server_from_list =  NX_TRUE;
        break;
    }

    /* Removing the server from the active server list? */
    if (remove_server_from_list)
    {

        /* Let the caller know it has to bail on 
           this server before resuming service. */
        status = NX_SNTP_KOD_REMOVE_SERVER;
    }

    return status;
}


/* This application defined handler for notifying SNTP time update event.  */

VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time)
{
    tx_event_flags_set(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, TX_OR);
}

```

<span data-ttu-id="1ac64-152">Figura 1 Ejemplo del uso del cliente SNTP con NetX Duo</span><span class="sxs-lookup"><span data-stu-id="1ac64-152">Figure 1 Example of using SNTP Client with NetX Duo</span></span>

## <a name="configuration-options"></a><span data-ttu-id="1ac64-153">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="1ac64-153">Configuration Options</span></span>

<span data-ttu-id="1ac64-154">Hay varias opciones de configuración para definir el cliente SNTP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-154">There are several configuration options for defining the NetX Duo SNTP Client.</span></span> <span data-ttu-id="1ac64-155">En la lista siguiente se describe cada una de forma detallada:</span><span class="sxs-lookup"><span data-stu-id="1ac64-155">The following list describes each in detail:</span></span>  
  

<span data-ttu-id="1ac64-156">**NX_SNTP_CLIENT_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="1ac64-156">**NX_SNTP_CLIENT_THREAD_STACK_SIZE**</span></span>  
<span data-ttu-id="1ac64-157">Esta opción establece el tamaño de la pila de subprocesos del cliente.</span><span class="sxs-lookup"><span data-stu-id="1ac64-157">This option sets the size of the Client thread stack.</span></span> <span data-ttu-id="1ac64-158">El tamaño del cliente SNTP de NetX Duo predeterminado es 2048.</span><span class="sxs-lookup"><span data-stu-id="1ac64-158">The default NetX Duo SNTP Client size is 2048.</span></span>

<span data-ttu-id="1ac64-159">**NX_SNTP_CLIENT_THREAD_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="1ac64-159">**NX_SNTP_CLIENT_THREAD_TIME_SLICE**</span></span>  
<span data-ttu-id="1ac64-160">Esta opción establece la porción de tiempo del programador que permite la ejecución de subprocesos del cliente.</span><span class="sxs-lookup"><span data-stu-id="1ac64-160">This option sets the time slice of the scheduler allows for Client thread execution.</span></span> <span data-ttu-id="1ac64-161">El tamaño predeterminado para el cliente SNTP de NetX Duo es TX_NO_TIME_SLICE.</span><span class="sxs-lookup"><span data-stu-id="1ac64-161">The default NetX Duo SNTP Client size is TX_NO_TIME_SLICE.</span></span>

<span data-ttu-id="1ac64-162">**NX_SNTP_CLIENT_ THREAD_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="1ac64-162">**NX_SNTP_CLIENT_ THREAD_PRIORITY**</span></span>  
<span data-ttu-id="1ac64-163">Esta opción establece la prioridad del subproceso del cliente.</span><span class="sxs-lookup"><span data-stu-id="1ac64-163">This option sets the Client thread priority.</span></span> <span data-ttu-id="1ac64-164">El valor predeterminado para el cliente SNTP de NetX Duo es 2.</span><span class="sxs-lookup"><span data-stu-id="1ac64-164">The NetX Duo SNTP Client default value is 2.</span></span>

<span data-ttu-id="1ac64-165">**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**</span><span class="sxs-lookup"><span data-stu-id="1ac64-165">**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**</span></span>  
<span data-ttu-id="1ac64-166">Esta opción establece el nivel de prioridad en el que el subproceso del cliente permite el adelantamiento.</span><span class="sxs-lookup"><span data-stu-id="1ac64-166">This option sets the sets the level of priority at which the Client thread allows preemption.</span></span> <span data-ttu-id="1ac64-167">El valor predeterminado para el cliente SNTP de NetX Duo se establece en `NX_SNTP_CLIENT_ THREAD_PRIORITY`.</span><span class="sxs-lookup"><span data-stu-id="1ac64-167">The default NetX Duo SNTP Client value is set to `NX_SNTP_CLIENT_ THREAD_PRIORITY`.</span></span>

<span data-ttu-id="1ac64-168">**NX_SNTP_CLIENT_UDP_SOCKET_NAME**</span><span class="sxs-lookup"><span data-stu-id="1ac64-168">**NX_SNTP_CLIENT_UDP_SOCKET_NAME**</span></span>  
<span data-ttu-id="1ac64-169">Esta opción establece el nombre del socket UDP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-169">This option sets the UDP socket name.</span></span> <span data-ttu-id="1ac64-170">El valor predeterminado del nombre de socket UDP para el cliente SNTP de NetX Duo es "SNTP Client socket".</span><span class="sxs-lookup"><span data-stu-id="1ac64-170">The NetX Duo SNTP Client UDP socket name default is “SNTP Client socket.”</span></span>

<span data-ttu-id="1ac64-171">**NX_SNTP_CLIENT_UDP_PORT**</span><span class="sxs-lookup"><span data-stu-id="1ac64-171">**NX_SNTP_CLIENT_UDP_PORT**</span></span>  
<span data-ttu-id="1ac64-172">Esta opción establece el puerto al que está enlazado el socket del cliente.</span><span class="sxs-lookup"><span data-stu-id="1ac64-172">This sets the port which the Client socket is bound to.</span></span> <span data-ttu-id="1ac64-173">El puerto predeterminado para el cliente SNTP de NetX Duo es el puerto 123.</span><span class="sxs-lookup"><span data-stu-id="1ac64-173">The default NetX Duo SNTP Client port is 123.</span></span>

<span data-ttu-id="1ac64-174">**NX_SNTP_SERVER_UDP_PORT**</span><span class="sxs-lookup"><span data-stu-id="1ac64-174">**NX_SNTP_SERVER_UDP_PORT**</span></span>  
<span data-ttu-id="1ac64-175">Esta opción establece el puerto por el que el cliente envía mensajes SNTP al servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-175">This is port which the Client sends SNTP messages to the SNTP Server on.</span></span> <span data-ttu-id="1ac64-176">El puerto predeterminado para el servidor SNTP de NetX es el puerto 123.</span><span class="sxs-lookup"><span data-stu-id="1ac64-176">The default NetX SNTP Server port is 123.</span></span>

<span data-ttu-id="1ac64-177">**NX_SNTP_CLIENT_TIME_TO_LIVE**</span><span class="sxs-lookup"><span data-stu-id="1ac64-177">**NX_SNTP_CLIENT_TIME_TO_LIVE**</span></span>  
<span data-ttu-id="1ac64-178">Especifica el número de enrutadores que puede pasar un paquete de cliente antes de que se descarte.</span><span class="sxs-lookup"><span data-stu-id="1ac64-178">Specifies the number of routers a Client packet can pass before it is discarded.</span></span> <span data-ttu-id="1ac64-179">El valor predeterminado para el cliente SNTP de NetX Duo se establece en 0x80 *.* .</span><span class="sxs-lookup"><span data-stu-id="1ac64-179">The default NetX Duo SNTP Client is set to 0x80 *.*</span></span>

<span data-ttu-id="1ac64-180">**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**</span><span class="sxs-lookup"><span data-stu-id="1ac64-180">**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**</span></span>  
<span data-ttu-id="1ac64-181">Número máximo de paquetes UDP (datagramas) que se pueden poner en cola en el socket del cliente SNTP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-181">Maximum number of UDP packets (datagrams) that can be queued in the NetX Duo SNTP Client socket.</span></span> <span data-ttu-id="1ac64-182">Si se reciben paquetes adicionales, se liberan los paquetes más antiguos.</span><span class="sxs-lookup"><span data-stu-id="1ac64-182">Additional packets received mean the oldest packets are released.</span></span> <span data-ttu-id="1ac64-183">El valor predeterminado para el cliente SNTP de NetX Duo se establece en 5.</span><span class="sxs-lookup"><span data-stu-id="1ac64-183">The default NetX Duo SNTP Client is set to 5.</span></span>

<span data-ttu-id="1ac64-184">**NX_SNTP_CLIENT_PACKET_TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="1ac64-184">**NX_SNTP_CLIENT_PACKET_TIMEOUT**</span></span>  
<span data-ttu-id="1ac64-185">Tiempo de espera para la asignación de paquetes de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-185">Time out for NetX Duo packet allocation.</span></span> <span data-ttu-id="1ac64-186">El tiempo de espera predeterminado para los paquetes del cliente SNTP de NetX Duo es 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-186">The default NetX Duo SNTP Client packet timeout is 1 second.</span></span>

<span data-ttu-id="1ac64-187">**NX_SNTP_CLIENT_NTP_VERSION**</span><span class="sxs-lookup"><span data-stu-id="1ac64-187">**NX_SNTP_CLIENT_NTP_VERSION**</span></span>  
<span data-ttu-id="1ac64-188">Versión de SNTP usada por el cliente. La API del cliente SNTP de NetX Duo se ha basado en la versión 4.</span><span class="sxs-lookup"><span data-stu-id="1ac64-188">SNTP version used by the Client The NetX Duo SNTP Client API was based on Version 4.</span></span> <span data-ttu-id="1ac64-189">El valor predeterminado es 3.</span><span class="sxs-lookup"><span data-stu-id="1ac64-189">The default value is 3.</span></span>

<span data-ttu-id="1ac64-190">**NX_SNTP_CLIENT_MIN_NTP_VERSION**</span><span class="sxs-lookup"><span data-stu-id="1ac64-190">**NX_SNTP_CLIENT_MIN_NTP_VERSION**</span></span>  
<span data-ttu-id="1ac64-191">Versión de SNTP más antigua con la que el cliente podrá trabajar.</span><span class="sxs-lookup"><span data-stu-id="1ac64-191">Oldest SNTP version the Client will be able to work with.</span></span> <span data-ttu-id="1ac64-192">El valor predeterminado para el cliente SNTP de NetX Duo es la versión 3.</span><span class="sxs-lookup"><span data-stu-id="1ac64-192">The NetX Duo SNTP Client default is Version 3.</span></span>

<span data-ttu-id="1ac64-193">**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**</span><span class="sxs-lookup"><span data-stu-id="1ac64-193">**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**</span></span>  
<span data-ttu-id="1ac64-194">Establece la capa del servidor SNTP de nivel más bajo (nivel numérico de capa más alto) que el cliente aceptará.</span><span class="sxs-lookup"><span data-stu-id="1ac64-194">The lowest level (highest numeric stratum level) SNTP Server stratum the Client will accept.</span></span> <span data-ttu-id="1ac64-195">El valor predeterminado para el cliente SNTP de NetX Duo es 2.</span><span class="sxs-lookup"><span data-stu-id="1ac64-195">The NetX Duo SNTP Client default is 2.</span></span>

<span data-ttu-id="1ac64-196">**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**</span><span class="sxs-lookup"><span data-stu-id="1ac64-196">**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**</span></span>  
<span data-ttu-id="1ac64-197">El ajuste mínimo de hora, en milisegundos, que el cliente realizará en su hora de reloj local.</span><span class="sxs-lookup"><span data-stu-id="1ac64-197">The minimum time adjustment in milliseconds the Client will make to its local clock time.</span></span> <span data-ttu-id="1ac64-198">Se omitirán los ajustes menores a este valor.</span><span class="sxs-lookup"><span data-stu-id="1ac64-198">Time adjustments below this will be ignored.</span></span> <span data-ttu-id="1ac64-199">El valor predeterminado para el cliente SNTP de NetX Duo es 10.</span><span class="sxs-lookup"><span data-stu-id="1ac64-199">The NetX Duo SNTP Client default is 10.</span></span>

<span data-ttu-id="1ac64-200">**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**</span><span class="sxs-lookup"><span data-stu-id="1ac64-200">**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**</span></span>  
<span data-ttu-id="1ac64-201">El ajuste máximo de hora, en milisegundos, que el cliente realizará en su hora de reloj local.</span><span class="sxs-lookup"><span data-stu-id="1ac64-201">The maximum time adjustment in milliseconds the Client will make to its local clock time.</span></span> <span data-ttu-id="1ac64-202">Si hay ajustes con valores superiores a este número, el reloj local se limitará al ajuste máximo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-202">For time adjustments above this amount, the local clock adjustment is limited to the maximum time adjustment.</span></span> <span data-ttu-id="1ac64-203">El valor predeterminado para el cliente SNTP de NetX Duo es 180000 (3 minutos).</span><span class="sxs-lookup"><span data-stu-id="1ac64-203">The NetX Duo SNTP Client default is 180000 (3 minutes).</span></span>

<span data-ttu-id="1ac64-204">**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**</span><span class="sxs-lookup"><span data-stu-id="1ac64-204">**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**</span></span>  
<span data-ttu-id="1ac64-205">Esta opción permite que se omita el ajuste máximo de hora cuando el cliente recibe la primera actualización de su servidor horario.</span><span class="sxs-lookup"><span data-stu-id="1ac64-205">This enables the maximum time adjustment to be waived when the Client receives the first update from its time server.</span></span> <span data-ttu-id="1ac64-206">A partir de ese momento, se aplica el ajuste máximo de hora.</span><span class="sxs-lookup"><span data-stu-id="1ac64-206">Thereafter, the maximum time adjustment is enforced.</span></span> <span data-ttu-id="1ac64-207">De este modo se pretende que el cliente se sincronice con el reloj del servidor lo antes posible.</span><span class="sxs-lookup"><span data-stu-id="1ac64-207">The intention is to get the Client in synch with the server clock as soon as possible.</span></span> <span data-ttu-id="1ac64-208">El valor predeterminado para el cliente SNTP de NetX Duo es NX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="1ac64-208">The NetX Duo SNTP Client default is NX_TRUE.</span></span>

<span data-ttu-id="1ac64-209">**NX_SNTP_CLIENT_MAX_TIME_LAPSE**</span><span class="sxs-lookup"><span data-stu-id="1ac64-209">**NX_SNTP_CLIENT_MAX_TIME_LAPSE**</span></span>  
<span data-ttu-id="1ac64-210">Tiempo máximo permitido (en segundos) que puede transcurrir sin una actualización de hora válida recibida por el cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-210">Maximum allowable amount of time (seconds) elapsed without a valid time update received by the SNTP Client.</span></span> <span data-ttu-id="1ac64-211">El cliente SNTP seguirá funcionando, pero el estado del servidor SNTP se establecerá en NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="1ac64-211">The SNTP Client will continue in operation but the SNTP Server status is set to NX_FALSE.</span></span> <span data-ttu-id="1ac64-212">El valor predeterminado es 7200.</span><span class="sxs-lookup"><span data-stu-id="1ac64-212">The default value is 7200.</span></span>


<span data-ttu-id="1ac64-213">**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="1ac64-213">**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**</span></span>  
<span data-ttu-id="1ac64-214">El intervalo (en segundos) con el que el temporizador del cliente SNTP actualiza el tiempo restante del cliente SNTP desde la última actualización válida recibida y con el que el cliente de unidifusión actualiza el tiempo restante del intervalo de sondeo antes de enviar la siguiente solicitud de actualización de SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-214">The interval (seconds) at which the SNTP Client timer updates the SNTP Client time remaining since the last valid update received, and the unicast Client updates the poll interval time remaining before sending the next SNTP update request.</span></span> <span data-ttu-id="1ac64-215">El valor predeterminado es 1.</span><span class="sxs-lookup"><span data-stu-id="1ac64-215">The default value is 1.</span></span>

<span data-ttu-id="1ac64-216">**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="1ac64-216">**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**</span></span>  
<span data-ttu-id="1ac64-217">El intervalo de sondeo inicial (en segundos) con el que el cliente envía una solicitud de unidifusión a su servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-217">The starting poll interval (seconds) on which the Client sends a unicast request to its SNTP server.</span></span> <span data-ttu-id="1ac64-218">El valor predeterminado para el cliente SNTP de NetX Duo es 3600.</span><span class="sxs-lookup"><span data-stu-id="1ac64-218">The NetX Duo SNTP Client default is 3600.</span></span>

<span data-ttu-id="1ac64-219">**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**</span><span class="sxs-lookup"><span data-stu-id="1ac64-219">**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**</span></span>  
<span data-ttu-id="1ac64-220">Factor por el que aumenta el intervalo de sondeo de unidifusión del cliente actual.</span><span class="sxs-lookup"><span data-stu-id="1ac64-220">The factor by which the current Client unicast poll interval is increased.</span></span> <span data-ttu-id="1ac64-221">Cuando el cliente no recibe una actualización de hora del servidor, o recibe indicaciones del servidor de que no está disponible temporalmente (por ejemplo, todavía no se ha sincronizado) para el servicio de actualización de hora, aumentará el intervalo de sondeo actual según este valor hasta alcanzar el valor de NX_SNTP_CLIENT_MAX_TIME_LAPSE, sin superarlo.</span><span class="sxs-lookup"><span data-stu-id="1ac64-221">When the Client fails to receive a server time update, or receiving indications from the server that it is temporarily unavailable (e.g. not synchronized yet) for time update service, it will increase the current poll interval by this rate up to but not exceeding NX_SNTP_CLIENT_MAX_TIME_LAPSE.</span></span> <span data-ttu-id="1ac64-222">El valor predeterminado es 2.</span><span class="sxs-lookup"><span data-stu-id="1ac64-222">The default is 2.</span></span>

<span data-ttu-id="1ac64-223">**NX_SNTP_CLIENT_RTT_REQUIRED**</span><span class="sxs-lookup"><span data-stu-id="1ac64-223">**NX_SNTP_CLIENT_RTT_REQUIRED**</span></span>  
<span data-ttu-id="1ac64-224">Esta opción, si está habilitada, requiere que el cliente SNTP calcule el tiempo de ida y vuelta de los mensajes SNTP a la hora de aplicar actualizaciones del servidor al reloj local.</span><span class="sxs-lookup"><span data-stu-id="1ac64-224">This option if enabled requires that the SNTP Client calculate round trip time of SNTP messages when applying Server updates to the local clock.</span></span> <span data-ttu-id="1ac64-225">El valor predeterminado es NX_FALSE (deshabilitado).</span><span class="sxs-lookup"><span data-stu-id="1ac64-225">The default value is NX_FALSE (disabled).</span></span>

<span data-ttu-id="1ac64-226">**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**</span><span class="sxs-lookup"><span data-stu-id="1ac64-226">**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**</span></span>  
<span data-ttu-id="1ac64-227">Esta opción establece la dispersión máxima del reloj del servidor (en microsegundos), una medida de la precisión del reloj del servidor, que el cliente aceptará.</span><span class="sxs-lookup"><span data-stu-id="1ac64-227">The maximum server clock dispersion (microseconds), which is a measure of server clock precision, the Client will accept.</span></span> <span data-ttu-id="1ac64-228">Para deshabilitar este requisito, establezca la dispersión raíz máxima en 0x0.</span><span class="sxs-lookup"><span data-stu-id="1ac64-228">To disable this requirement, set the maximum root dispersion to 0x0.</span></span> <span data-ttu-id="1ac64-229">El valor predeterminado para el cliente SNTP de NetX Duo se establece en 50000.</span><span class="sxs-lookup"><span data-stu-id="1ac64-229">The NetX Duo SNTP Client default is set to 50000.</span></span>

<span data-ttu-id="1ac64-230">**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**</span><span class="sxs-lookup"><span data-stu-id="1ac64-230">**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**</span></span>  
<span data-ttu-id="1ac64-231">Límite en el número de actualizaciones no válidas consecutivas recibidas del servidor del cliente en modo de difusión o de unidifusión.</span><span class="sxs-lookup"><span data-stu-id="1ac64-231">The limit on the number of consecutive invalid updates received from the Client server in either broadcast or unicast mode.</span></span> <span data-ttu-id="1ac64-232">Cuando se alcanza este límite, el cliente establece el estado actual del servidor SNTP en no válido (NX_FALSE), aunque seguirá intentando recibir sus actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="1ac64-232">When this limit is reached, the Client sets the current SNTP Server status to invalid (NX_FALSE) although it will continue to try to receive updates from the Server.</span></span> <span data-ttu-id="1ac64-233">El valor predeterminado para el cliente SNTP de NetX Duo es 3.</span><span class="sxs-lookup"><span data-stu-id="1ac64-233">The NetX Duo SNTP Client default is 3.</span></span>

<span data-ttu-id="1ac64-234">**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**</span><span class="sxs-lookup"><span data-stu-id="1ac64-234">**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**</span></span>  
<span data-ttu-id="1ac64-235">Determina si el cliente SNTP en modo de unidifusión debe enviar su primera solicitud SNTP con el servidor SNTP actual después de un intervalo de espera aleatorio.</span><span class="sxs-lookup"><span data-stu-id="1ac64-235">This determines if the SNTP Client in unicast mode should send its first SNTP request with the current SNTP server after a random wait interval.</span></span> <span data-ttu-id="1ac64-236">Se utiliza en casos en los que se inicia simultáneamente un número significativo de clientes SNTP, con el fin de limitar la congestión del tráfico en el servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="1ac64-236">It is used in cases where significant numbers of SNTP Clients are starting up simultaneously to limit traffic congestion on the SNTP Server.</span></span> <span data-ttu-id="1ac64-237">El valor predeterminado es NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="1ac64-237">The default value is NX_FALSE.</span></span>

<span data-ttu-id="1ac64-238">**NX_SNTP_CLIENT_SLEEP_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="1ac64-238">**NX_SNTP_CLIENT_SLEEP_INTERVAL**</span></span>  
<span data-ttu-id="1ac64-239">El intervalo de tiempo durante el que la tarea del cliente SNTP se suspende.</span><span class="sxs-lookup"><span data-stu-id="1ac64-239">The time interval during which the SNTP Client task sleeps.</span></span> <span data-ttu-id="1ac64-240">Esto permite que el cliente SNTP ejecute las llamadas a la API de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1ac64-240">This allows the application API calls to be executed by the SNTP Client.</span></span> <span data-ttu-id="1ac64-241">El valor predeterminado es 1 tic del temporizador.</span><span class="sxs-lookup"><span data-stu-id="1ac64-241">The default value is 1 timer tick.</span></span>

<span data-ttu-id="1ac64-242">**NX_SNTP_CURRENT_YEAR**</span><span class="sxs-lookup"><span data-stu-id="1ac64-242">**NX_SNTP_CURRENT_YEAR**</span></span>  
<span data-ttu-id="1ac64-243">Para mostrar la fecha en formato de año/mes/día, establezca este valor en un número igual o menor que el año actual (no es necesario que sea el mismo año que el de la hora de NTP que se está evaluando).</span><span class="sxs-lookup"><span data-stu-id="1ac64-243">To display date in year/month/date format, set this value to equal or less than current year (need not be same year as in NTP time being evaluated).</span></span> <span data-ttu-id="1ac64-244">El valor predeterminado es 2015.</span><span class="sxs-lookup"><span data-stu-id="1ac64-244">The default value is 2015.</span></span>

<span data-ttu-id="1ac64-245">**NTP_SECONDS_AT_01011999**</span><span class="sxs-lookup"><span data-stu-id="1ac64-245">**NTP_SECONDS_AT_01011999**</span></span>  
<span data-ttu-id="1ac64-246">Es el número de segundos en la primera época NTP del reloj NTP maestro.</span><span class="sxs-lookup"><span data-stu-id="1ac64-246">This is the number of seconds into the first NTP Epoch on the master NTP clock.</span></span> <span data-ttu-id="1ac64-247">Se define como 0xBA368E80.</span><span class="sxs-lookup"><span data-stu-id="1ac64-247">It is defined as 0xBA368E80.</span></span> <span data-ttu-id="1ac64-248">Para deshabilitar la visualización de segundos NTP en día y hora, establezca esta opción en cero.</span><span class="sxs-lookup"><span data-stu-id="1ac64-248">To disable display of NTP seconds into date and time, set to zero.</span></span>
