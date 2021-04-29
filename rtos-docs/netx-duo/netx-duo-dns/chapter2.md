---
title: 'Capítulo 2: Instalación y uso del cliente DNS de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del cliente DNS de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b85829f80462015d66e1623b880d5139349ce0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815386"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dns-client"></a><span data-ttu-id="06f06-103">Capítulo 2: Instalación y uso del cliente DNS de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="06f06-103">Chapter 2 - Installation and Use of Azure RTOS NetX Duo DNS Client</span></span>

<span data-ttu-id="06f06-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del cliente DNS de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="06f06-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo DNS Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="06f06-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="06f06-105">Product Distribution</span></span>

<span data-ttu-id="06f06-106">El cliente DNS de NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="06f06-106">NetX Duo DNS Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="06f06-107">El paquete incluye dos archivos de origen y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="06f06-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="06f06-108">**nxd_dns.h** Archivo de encabezado para el cliente DNS de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="06f06-108">**nxd_dns.h** Header file for NetX Duo DNS Client</span></span>
- <span data-ttu-id="06f06-109">**nxd_dns.c** Archivo de código fuente C para el cliente DNS de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="06f06-109">**nxd_dns.c** C Source file for NetX Duo DNS Client</span></span>
- <span data-ttu-id="06f06-110">**nxd_dns.pdf** Descripción en PDF del cliente DNS de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="06f06-110">**nxd_dns.pdf** PDF description of NetX Duo DNS Client</span></span>

## <a name="dns-client-installation"></a><span data-ttu-id="06f06-111">Instalación del cliente DNS</span><span class="sxs-lookup"><span data-stu-id="06f06-111">DNS Client Installation</span></span>

<span data-ttu-id="06f06-112">Para usar el cliente DNS de NetX Duo, copie los archivos de código fuente *nxd_dns.c* y *nxd_dns.h* en el mismo directorio en el que se ha instalado NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="06f06-112">To use NetX Duo DNS Client, copy the source code files *nxd_dns.c* and *nxd_dns.h* to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="06f06-113">Por ejemplo, si NetX Duo se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nxd_dns.h* y *nxd_dns.c* deben copiarse en este directorio.</span><span class="sxs-lookup"><span data-stu-id="06f06-113">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dns.h* and *nxd_dns.c* files should be copied into this directory.</span></span>

## <a name="using-the-dns-client"></a><span data-ttu-id="06f06-114">Uso del cliente DNS</span><span class="sxs-lookup"><span data-stu-id="06f06-114">Using the DNS Client</span></span>

<span data-ttu-id="06f06-115">Es fácil usar el cliente DNS de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="06f06-115">Using NetX Duo DNS Client is easy.</span></span> <span data-ttu-id="06f06-116">Básicamente, el código de la aplicación debe incluir *nxd_dns.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX Duo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="06f06-116">Basically, the application code must include *nxd_dns.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="06f06-117">Después de incluir *nxd_dns.h*, el código de la aplicación puede realizar las llamadas de función DNS especificadas más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="06f06-117">Once *nxd_dns.h* is included, the application code is then able to make the DNS function calls specified later in this guide.</span></span> <span data-ttu-id="06f06-118">La aplicación también debe agregar *nxd_dns.c* al proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="06f06-118">The application must also add *nxd_dns.c* to the build process.</span></span> <span data-ttu-id="06f06-119">Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="06f06-119">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="06f06-120">Esto es todo lo que se necesita para usar DNS de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="06f06-120">This is all that is required to use NetX Duo DNS.</span></span>

> [!NOTE]
> <span data-ttu-id="06f06-121">Como DNS usa los servicios de UDP de NetX Duo, debe habilitarse UDP con la llamada a *nx_udp_enable* antes de utilizar DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-121">Since DNS utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DNS.</span></span>

## <a name="small-example-system-for-netx-duo-dns-client"></a><span data-ttu-id="06f06-122">Sistema de ejemplo pequeño para el cliente DNS de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="06f06-122">Small Example System for NetX Duo DNS Client</span></span> 

<span data-ttu-id="06f06-123">El cliente DNS de NetX Duo es compatible con las aplicaciones DNS de NetX existentes.</span><span class="sxs-lookup"><span data-stu-id="06f06-123">NetX Duo DNS Client is compatible with existing NetX DNS applications.</span></span> <span data-ttu-id="06f06-124">A continuación, se muestra la lista de servicios heredados y su equivalente de NetX Duo:</span><span class="sxs-lookup"><span data-stu-id="06f06-124">The list of legacy services and their NetX Duo equivalent is shown below:</span></span>

| <span data-ttu-id="06f06-125">Servicio de API de DNS de NetX (solo IPv4)</span><span class="sxs-lookup"><span data-stu-id="06f06-125">NetX DNS API service (IPv4 only)</span></span> | <span data-ttu-id="06f06-126">Servicio de API de DNS de NetX Duo (compatible con IPv4 e IPv6)</span><span class="sxs-lookup"><span data-stu-id="06f06-126">NetX Duo DNS API service (IPv4 and IPv6 supported)</span></span> |
|----------------------------------|----------------------------------------------------|
| <span data-ttu-id="06f06-127">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="06f06-127">nx_dns_host_by_name_get</span></span>          | <span data-ttu-id="06f06-128">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="06f06-128">nxd_dns_host_by_name_get</span></span>                           |
| <span data-ttu-id="06f06-129">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="06f06-129">nx_dns_host_by_address_get</span></span>       | <span data-ttu-id="06f06-130">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="06f06-130">nxd_dns_host_by_address_get</span></span>                        |
| <span data-ttu-id="06f06-131">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="06f06-131">nx_dns_server_get</span></span>                | <span data-ttu-id="06f06-132">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="06f06-132">nxd_dns_server_get</span></span>                                 |
| <span data-ttu-id="06f06-133">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="06f06-133">nx_dns_server_add</span></span>                | <span data-ttu-id="06f06-134">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="06f06-134">nxd_dns_server_add</span></span>                                 |
| <span data-ttu-id="06f06-135">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="06f06-135">nx_dns_server_remove</span></span>             | <span data-ttu-id="06f06-136">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="06f06-136">nxd_dns_server_remove</span></span>                              |

<span data-ttu-id="06f06-137">Consulte la descripción de los servicios de API de cliente DNS de NetX Duo en el capítulo 3 para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="06f06-137">See the description of NetX Duo DNS Client API services in Chapter 3 for more details.</span></span>

<span data-ttu-id="06f06-138">En el programa de aplicación DNS de ejemplo que se proporciona en esta sección, *nxd_dns.h* se incluye en la línea 6.</span><span class="sxs-lookup"><span data-stu-id="06f06-138">In the example DNS application program provided in this section, *nxd_dns.h* is included at line 6.</span></span> <span data-ttu-id="06f06-139">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, que permite que la aplicación de cliente DNS cree el grupo de paquetes para el cliente DNS, se declara en las líneas 24 a 26.</span><span class="sxs-lookup"><span data-stu-id="06f06-139">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, which allows the DNS Client application to create the packet pool for the DNS Client, is declared on lines 24-26.</span></span> <span data-ttu-id="06f06-140">Este grupo de paquetes se utiliza para asignar paquetes para enviar mensajes DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-140">This packet pool is used for allocating packets for sending DNS messages.</span></span> <span data-ttu-id="06f06-141">Si se define NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, se crea un grupo de paquetes en las líneas 78 a 98.</span><span class="sxs-lookup"><span data-stu-id="06f06-141">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined, a packet pool is created in lines 78-98.</span></span> <span data-ttu-id="06f06-142">Si esta opción no está habilitada, el cliente DNS crea su propio grupo de paquetes según la carga del paquete y el tamaño del grupo establecido por los parámetros de configuración en *nxd_dns.h* y descritos en otro lugar de este capítulo.</span><span class="sxs-lookup"><span data-stu-id="06f06-142">If this option is not enabled, the DNS Client creates its own packet pool as per the packet payload and pool size set by configuration parameters in *nxd_dns.h* and described elsewhere in this chapter.</span></span>

<span data-ttu-id="06f06-143">En las líneas 100 a 112, se crea otro grupo de paquetes para la instancia de IP de cliente que se usa para las operaciones internas de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="06f06-143">Another packet pool is created in lines 100-112 for the Client IP instance which is used for internal NetX Duo operations.</span></span> <span data-ttu-id="06f06-144">A continuación, se crea la instancia de IP mediante la llamada a *nx_ip_create* en la línea 115.</span><span class="sxs-lookup"><span data-stu-id="06f06-144">Next the IP instance is created using the *nx_ip_create* call in line 115.</span></span> <span data-ttu-id="06f06-145">Es posible que la tarea de IP y el cliente DNS compartan el mismo grupo de paquetes, pero como el cliente DNS suele enviar mensajes más grandes que los paquetes de control enviados por la tarea de IP, si se emplean grupos de paquetes independientes, se usa la memoria de manera más eficaz.</span><span class="sxs-lookup"><span data-stu-id="06f06-145">It is possible for the IP task and the DNS Client to share the same packet pool, but since the DNS Client typically sends out larger messages than the control packets sent by the IP task, using separate packet pools makes more efficient use of memory.</span></span>

<span data-ttu-id="06f06-146">ARP y UDP (que se usa por las redes IPv4) se habilitan en las líneas 129 y 141, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="06f06-146">ARP and UDP (which is used by IPv4 networks) are enabled in lines 129 and 141 respectively.</span></span>

>[!NOTE]
> <span data-ttu-id="06f06-147">En esta demostración se usa el controlador "ram" declarado en la línea 44 y utilizado en la llamada a *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="06f06-147">This demo uses the ‘ram’ driver declared on line 44 and used in the *nx_ip_create* call.</span></span> <span data-ttu-id="06f06-148">Este controlador de RAM se distribuye con el código fuente de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="06f06-148">This ram driver is distributed with the NetX Duo source code.</span></span> <span data-ttu-id="06f06-149">Para ejecutar realmente el cliente DNS, la aplicación debe proporcionar un controlador de red físico real para transmitir y recibir paquetes del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-149">To actually run the DNS Client the application must supply an actual physical network driver to transmit and receive packets from the DNS server.</span></span>

<span data-ttu-id="06f06-150">La función de entrada de subproceso de cliente *thread_client_entry* se define debajo de la función *tx_application_define*.</span><span class="sxs-lookup"><span data-stu-id="06f06-150">The Client thread entry function *thread_client_entry* is defined below the *tx_application_define* function.</span></span> <span data-ttu-id="06f06-151">Cede inicialmente el control al sistema para permitir que el controlador de red inicialice el subproceso de la tarea de IP.</span><span class="sxs-lookup"><span data-stu-id="06f06-151">It initially relinquishes control to the system to allow the IP task thread to be initialized by the network driver.</span></span>

<span data-ttu-id="06f06-152">A continuación, crea el cliente DNS en la línea 257, inicializa la caché de DNS en las líneas 267 a 278 y establece el grupo de paquetes creado previamente en la instancia del cliente DNS en las líneas 281 a 295.</span><span class="sxs-lookup"><span data-stu-id="06f06-152">It then creates the DNS Client in line 257, initializes the DNS cache on lines 267- 278, and sets the packet pool previously created to the DNS Client instance on lines 281-295.</span></span> <span data-ttu-id="06f06-153">Después agrega el servidor DNS en las líneas 297 a 341.</span><span class="sxs-lookup"><span data-stu-id="06f06-153">It then adds DNS server on lines 297-341.</span></span>

<span data-ttu-id="06f06-154">El resto del programa de ejemplo usa los servicios de cliente DNS para realizar consultas de DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-154">The remainder of the example program uses the DNS Client services to make DNS queries.</span></span> <span data-ttu-id="06f06-155">Las búsquedas de direcciones IP de host se realizan en las líneas 193 y 207.</span><span class="sxs-lookup"><span data-stu-id="06f06-155">Host IP address lookups are performed on lines 193 and 207.</span></span> <span data-ttu-id="06f06-156">La diferencia entre estos dos servicios, *nxd_dns_host_by_name_get* y *nx_dns_host_by_name_get*, es que el primero guarda los datos de dirección en un tipo de datos NXD_ADDRESS, mientras que el segundo guarda los datos en un tipo de datos ULONG.</span><span class="sxs-lookup"><span data-stu-id="06f06-156">The difference between these two services, *nxd_dns_host_by_name_get* and *nx_dns_host_by_name_get*, is that the former saves the address data in an NXD_ADDRESS data type, while the latter saves the data in a ULONG data type.</span></span> <span data-ttu-id="06f06-157">Además, este último está limitado a las redes IPv4, mientras que el primero se puede usar con redes IPv6 o IPv4.</span><span class="sxs-lookup"><span data-stu-id="06f06-157">Further the latter is limited to IPv4 networks, while the former can be used with IPv6 or IPv4 networks.</span></span> <span data-ttu-id="06f06-158">Esto solo es posible si la instancia de IP está habilitada para IPv6.</span><span class="sxs-lookup"><span data-stu-id="06f06-158">This is only possible if the IP instance is enabled for IPv6.</span></span> <span data-ttu-id="06f06-159">Consulte la guía del usuario de NetX Duo para obtener más detalles sobre cómo habilitar la instancia de IP para la red IPv6.</span><span class="sxs-lookup"><span data-stu-id="06f06-159">See the NetX Duo User Guide for more details on enabling the IP instance for IPv6 networking.</span></span>

<span data-ttu-id="06f06-160">Otro servicio para las búsquedas de IP de host se muestra en la línea 464, *nx_dns_ipv4_address_by_name_get*.</span><span class="sxs-lookup"><span data-stu-id="06f06-160">Another service for host IP address lookups is shown on line 464, *nx_dns_ipv4_address_by_name_get*.</span></span> <span data-ttu-id="06f06-161">Este servicio difiere de *nx_dns_host_by_name_get* en que devuelve todas las direcciones IPv4 detectadas para el nombre de dominio (o el número máximo que cabe en el búfer proporcionado), no solo la primera dirección recibida en la respuesta del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-161">This service differs from *nx_dns_host_by_name_get* in that it returns all (or as many will fit in the supplied buffer) of the IPv4 addresses discovered for the domain name, not just the first address received in the DNS Server reply.</span></span>

<span data-ttu-id="06f06-162">Del mismo modo, el servicio *nxd_dns_ipv6_address_by_name_get*, llamado en la línea 380, devuelve todas las direcciones IPv6 detectadas por el cliente DNS, no solo la primera.</span><span class="sxs-lookup"><span data-stu-id="06f06-162">Similarly, the *nxd_dns_ipv6_address_by_name_get* service, called on line 380, returns all the IPv6 addresses discovered by the DNS Client, not just the first one.</span></span>

<span data-ttu-id="06f06-163">Las búsquedas inversas (el nombre de host de la dirección IP) se realizan en la línea 606 (*nx_dns_host_by_address_get*) y de nuevo en las líneas 564 y 588 (*nxd_dns_host_by_address_get*).</span><span class="sxs-lookup"><span data-stu-id="06f06-163">Reverse lookups (host name from IP address) are performed on lines 606 (*nx_dns_host_by_address_get*) and again on line 564 and 588 (*nxd_dns_host_by_address_get*).</span></span> <span data-ttu-id="06f06-164">*nx_dns_host_by_address_get* solo funcionará en redes IPv4, mientras que *nxd_dns_host_by_address_get* funcionará en redes IPv4 o IPv6 (por ejemplo, la instancia de IP está habilitada para redes IPv6 y IPv4).</span><span class="sxs-lookup"><span data-stu-id="06f06-164">*nx_dns_host_by_address_get* will only work on IPv4 networks, while *nxd_dns_host_by_address_get* will work on either IPv4 or IPv6 networks (e.g. the IP instance is enabled for IPv6 as well as IPv4 networks).</span></span>

<span data-ttu-id="06f06-165">Dos servicios más para las búsquedas DNS, CNAME y TXT, se muestran en las líneas 627 y 649, respectivamente, para detectar los datos de nombre de dominio y CNAME para el nombre de dominio de entrada.</span><span class="sxs-lookup"><span data-stu-id="06f06-165">Two more services for DNS lookups, CNAME and TXT, are demonstrated on lines 627 and 649 respectively, to discover CNAME and domain name data for the input domain name.</span></span> <span data-ttu-id="06f06-166">El cliente DNS de NetX Duo es similar a servicios para otros tipos de registro, por ejemplo, MX, NS, SRV y SOA.</span><span class="sxs-lookup"><span data-stu-id="06f06-166">NetX Duo DNS Client as similar services for other record types, e.g. MX, NS, SRV and SOA.</span></span> <span data-ttu-id="06f06-167">Consulte el capítulo 3 para obtener descripciones detalladas de todas las búsquedas de tipo de registro disponibles en el cliente DNS de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="06f06-167">See Chapter 3 for detailed descriptions of all record type lookups available in NetX Duo DNS Client.</span></span>

<span data-ttu-id="06f06-168">Cuando el cliente DNS se elimina en la línea 846 con el servicio *nx_dns_delete*, el grupo de paquetes para el cliente DNS no se elimina, a menos que el cliente DNS haya creado su propio grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="06f06-168">When the DNS Client is deleted on line 846, using the *nx_dns_delete* service, the packet pool for the DNS Client is not deleted unless the DNS Client created its own packet pool.</span></span> <span data-ttu-id="06f06-169">De lo contrario, dependerá de la aplicación la eliminación del grupo de paquetes que ya no se usa.</span><span class="sxs-lookup"><span data-stu-id="06f06-169">Otherwise, it is up to the application to delete the packet pool if it has no further use for it.</span></span>

```C
/* This is a small demo of DNS Client for the high-performance NetX TCP/IP stack. */

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_udp.h"
#include   "nxd_dns.h"

#ifdef FEATURE_NX_IPV6
#include   "nx_ipv6.h"
#endif

#define     DEMO_STACK_SIZE         4096

#define     NX_PACKET_PAYLOAD       1536
#define     NX_PACKET_POOL_SIZE     30 * NX_PACKET_PAYLOAD
#define     LOCAL_CACHE_SIZE        2048

/* Define the ThreadX and NetX object control blocks... */

NX_DNS                  client_dns;
TX_THREAD               client_thread;
NX_IP                   client_ip;
NX_PACKET_POOL          main_pool;
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL
NX_PACKET_POOL          client_pool;
#endif
UCHAR                   local_cache[LOCAL_CACHE_SIZE];

UINT                    error_counter = 0;

#ifdef FEATURE_NX_IPV6
/* If IPv6 is enabled in NetX Duo, allow DNS Client to try using IPv6 */
//#define USE_IPV6
#endif

#define CLIENT_ADDRESS      IP_ADDRESS(192,168,0,11)
#define DNS_SERVER_ADDRESS  IP_ADDRESS(192,168,0,1)

/* Define thread prototypes. */

void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern  VOID _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&client_thread, "Client thread", thread_client_entry, 0,
            pointer, DEMO_STACK_SIZE, 4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Create the packet pool for the DNS Client to send packets.

        If the DNS Client is configured for letting the host application create
        the DNS packet pool, (see NX_DNS_CLIENT_USER_CREATE_PACKET_POOL option), see
       nx_dns_create() for guidelines on packet payload size and pool size.
       packet traffic for NetX processes.
    */
    status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", NX_DNS_PACKET_PAYLOAD, pointer, NX_DNS_PACKET_POOL_SIZE);

    pointer = pointer + NX_DNS_PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif
     /* Create the packet pool which the IP task will use to send packets. Also available to the host
       application to send packet. */
    status =  nx_packet_pool_create(&main_pool, "Main Packet Pool", NX_PACKET_PAYLOAD, pointer, NX_PACKET_POOL_SIZE);

    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Create an IP instance for the DNS Client. */
    status = nx_ip_create(&client_ip, "DNS Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                          &main_pool, _nx_ram_network_driver, pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Enable ARP and supply ARP cache memory for the DNS Client IP. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Enable UDP traffic because DNS is a UDP based protocol. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }
}

#define BUFFER_SIZE     200
#define RECORD_COUNT    10

/* Define the Client thread. */

void    thread_client_entry(ULONG thread_input)
{

UCHAR           record_buffer[200];
UINT            record_count;
UINT            status;
ULONG           host_ip_address;
#ifdef FEATURE_NX_IPV6
NXD_ADDRESS     host_ipduo_address;
NXD_ADDRESS     test_ipduo_server_address;
#ifdef USE_IPV6
NXD_ADDRESS     client_ipv6_address;
NXD_ADDRESS     dns_ipv6_server_address;
UINT            iface_index, address_index;
#endif
#endif
UINT            i;
ULONG           *ipv4_address_ptr[RECORD_COUNT];
NX_DNS_IPV6_ADDRESS
                *ipv6_address_ptr[RECORD_COUNT];
#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
NX_DNS_NS_ENTRY
                *nx_dns_ns_entry_ptr[RECORD_COUNT];
NX_DNS_MX_ENTRY
                *nx_dns_mx_entry_ptr[RECORD_COUNT];
NX_DNS_SRV_ENTRY
                *nx_dns_srv_entry_ptr[RECORD_COUNT];
NX_DNS_SOA_ENTRY
                *nx_dns_soa_entry_ptr;
ULONG           host_address;
USHORT          host_port;
#endif

    /* Give NetX IP task a chance to get initialized . */
    tx_thread_sleep(100);

#ifdef FEATURE_NX_IPV6
#ifdef USE_IPV6

    /* Make the DNS Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check for enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }
    status = nxd_icmp_enable(&client_ip);

    /* Check for enable errors. */
    if (status)
    {

        error_counter++;
        return;
    }

    client_ipv6_address.nxd_ip_address.v6[3] = 0x101;
    client_ipv6_address.nxd_ip_address.v6[2] = 0x0;
    client_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;


     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ipv6_address, 64, &address_index);

    /* Check for global address set error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);
#endif
#endif

    /* Create a DNS instance for the Client. Note this function will create
       the DNS Client packet pool for creating DNS message packets intended
       for querying its DNS server. */
    status =  nx_dns_create(&client_dns, &client_ip, (UCHAR *)"DNS Client");

    /* Check for DNS create error. */
    if (status)
    {

        error_counter++;
        return;
     }

#ifdef NX_DNS_CACHE_ENABLE
    /* Initialize the cache. */
    status = nx_dns_cache_initialize(&client_dns, local_cache, LOCAL_CACHE_SIZE);

    /* Check for DNS cache error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif

    /* Is the DNS client configured for the host application to create the pecket pool? */
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Yes, use the packet pool created above which has appropriate payload size
       for DNS messages. */
     status = nx_dns_packet_pool_set(&client_dns, &client_pool);

     /* Check for set DNS packet pool error. */
     if (status)
     {

         error_counter++;
         return;
      }

#endif /* NX_DNS_CLIENT_USER_CREATE_PACKET_POOL */

#ifdef FEATURE_NX_IPV6
#ifdef USE_IPV6

    /* Add an IPv6 DNS server to the DNS client. */
    dns_ipv6_server_address.nxd_ip_address.v6[3] = 0x106;
    dns_ipv6_server_address.nxd_ip_address.v6[2] = 0x0;
    dns_ipv6_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    dns_ipv6_server_address.nxd_ip_address.v6[0] = 0x20010db8;
    dns_ipv6_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    status = nxd_dns_server_add(&client_dns, &dns_ipv6_server_address);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#else

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif
#else

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif


/********************************************************************************/
/*                                  Type AAAA                                   */
/*     Send AAAA type DNS Query to its DNS server and get the IPv6 address. */
/********************************************************************************/
#ifdef FEATURE_NX_IPV6

    /* Send a DNS Client name query. Indicate the Client expects an IPv6 address (containing an AAAA record). The DNS
       Client will send AAAA type query to its DNS server. */
    status = nxd_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ipduo_address, 400, NX_IP_VERSION_V6);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test AAAA: \n");

        printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n",
            (UINT)host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
    }

#endif

    /* Look up IPv6 addresses(AAAA TYPE) to record multiple IPv6 addresses in record_buffer and return the IPv6 address count. */
    status = nxd_dns_ipv6_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS add server error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test AAAA: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv6_address_ptr[i] = (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS));

        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i,
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF));
    }


/********************************************************************************/
/*                                  Type A                                      */
/*       Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
#ifdef FEATURE_NX_IPV6
    /* Send a DNS Client name query. Indicate the Client expects an IPv4 address (containing an A record). If the DNS client
       is using an IPv6 DNS server it will send this query over IPv6; otherwise it will be sent over IPv4. */
    status = nxd_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ipduo_address, 400, NX_IP_VERSION_V4);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
              host_ipduo_address.nxd_ip_address.v4 >> 24,
              host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,
              host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
              host_ipduo_address.nxd_ip_address.v4 & 0xFF);
    }

#endif

    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }


    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }


/********************************************************************************/
/*                                  Type A + CNAME response                     */
/*       Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A + CNAME response: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }


    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test Test A + CNAME response: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }


/********************************************************************************/
/*                                  Type PTR                                    */
/*       Send PTR type DNS Query to its DNS server and get the host name. */
/********************************************************************************/

#ifdef FEATURE_NX_IPV6

    /* Look up a host name from an IPv6 address (reverse lookup). */

    /* Create an IPv6 address for a reverse lookup. */
    test_ipduo_server_address.nxd_ip_version = NX_IP_VERSION_V6;
    test_ipduo_server_address.nxd_ip_address.v6[0] = 0x24046800;
    test_ipduo_server_address.nxd_ip_address.v6[1] = 0x40050c00;
    test_ipduo_server_address.nxd_ip_address.v6[2] = 0x00000000;
    test_ipduo_server_address.nxd_ip_address.v6[3] = 0x00000065;

    /* This will be sent over IPv6 to the DNS server who should return a PTR record if it can find the information. */
    status = nxd_dns_host_by_address_get(&client_dns, &test_ipduo_server_address, &record_buffer[0], BUFFER_SIZE, 450);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }
#endif

#ifdef FEATURE_NX_IPV6

    /* Create an IPv4 address for the reverse lookup. If the DNS client is IPv6 enabled, it will send this over
       IPv6 to the DNS server; otherwise it will send it over IPv4. In either case the respective server will
       return a PTR record if it has the information. */
    test_ipduo_server_address.nxd_ip_version = NX_IP_VERSION_V4;
    test_ipduo_server_address.nxd_ip_address.v4 = IP_ADDRESS(74, 125, 71, 106);

    status = nxd_dns_host_by_address_get(&client_dns, &test_ipduo_server_address, &record_buffer[0], BUFFER_SIZE, 450);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }
#endif

     /* Look up host name over IPv4. */
     host_ip_address = IP_ADDRESS(74, 125, 71, 106);
     status = nx_dns_host_by_address_get(&client_dns, host_ip_address, &record_buffer[0], BUFFER_SIZE, 450);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {
        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
/********************************************************************************/
/*                                  Type CNAME                                  */
/*   Send CNAME type DNS Query to its DNS server and get the canonical name . */
/********************************************************************************/

     /* Send CNAME type to record the canonical name of host in record_buffer. */
     status = nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test CNAME: %s\n", record_buffer);
    }


/********************************************************************************/
/*                                  Type TXT                                    */
/*      Send TXT type DNS Query to its DNS server and get descriptive text. */
/********************************************************************************/

     /* Send TXT type to record the descriptive test of host in record_buffer. */
     status = nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test TXT: %s\n", record_buffer);
    }


/********************************************************************************/
/*                                  Type NS                                     */
/*   Send NS type DNS Query to its DNS server and get the domain name server. */
/********************************************************************************/

     /* Send NS type to record multiple name servers in record_buffer and return the name server count.
        If the DNS response includes the IPv4 addresses of name server, record it similarly in record_buffer. */
     status = nx_dns_domain_name_server_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test NS: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
            printf("hostname = %s\n", nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/*                                  Type MX                                     */
/*   Send MX type DNS Query to its DNS server and get the domain mail exchange. */
/********************************************************************************/

     /* Send MX DNS query type to record multiple mail exchanges in record_buffer and return the mail exchange count.
        If the DNS response includes the IPv4 addresses of mail exchange, record it similarly in record_buffer. */
     status = nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test MX: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);
        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);
        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/*                                  Type SRV                                    */
/*  Send SRV type DNS Query to its DNS server and get the location of services. */
/********************************************************************************/

     /* Send SRV DNS query type to record the location of services in record_buffer and return count.
        If the DNS response includes the IPv4 addresses of service name, record it similarly in record_buffer. */
     status = nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the location of services. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);
        printf("port number = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
        printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
        printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );
        if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
            printf("hostname = %s\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

    /* Get the service info, NetX old API.*/
    status = nx_dns_info_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_address, &host_port, 200);

    /* Check for DNS add server error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("IP address: %d.%d.%d.%d\n",
                host_address >> 24,
                host_address >> 16 & 0xFF,
                host_address >> 8 & 0xFF,
                host_address & 0xFF);
        printf("port number = %d\n", host_port);
    }

/********************************************************************************/
/*                                  Type SOA                                    */
/* Send SOA type DNS Query to its DNS server and get zone of start of authority.*/
/********************************************************************************/

     /* Send SOA DNS query type to record the zone of start of authority in record_buffer. */
     status = nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

     /* Get the loc*/
     nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
     printf("------------------------------------------------------\n");
     printf("Test SOA: \n");
     printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
     printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
     printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
     printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
     printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
     if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
         printf("host mname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
     else
         printf("host mame is not set\n");
     if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
         printf("host rname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
     else
         printf("host rname is not set\n");


#endif

    /* Shutting down...*/

    /* Terminate the DNS Client thread. */
    status = nx_dns_delete(&client_dns);

    return;
}
```
## <a name="configuration-options"></a><span data-ttu-id="06f06-170">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="06f06-170">Configuration Options</span></span>

<span data-ttu-id="06f06-171">Hay varias opciones de configuración para compilar el DNS de NetX.</span><span class="sxs-lookup"><span data-stu-id="06f06-171">There are several configuration options for building DNS for NetX.</span></span> <span data-ttu-id="06f06-172">Estas opciones se pueden redefinir en *nxd_dns.h.*</span><span class="sxs-lookup"><span data-stu-id="06f06-172">These options can be redefined in *nxd_dns.h.*</span></span> <span data-ttu-id="06f06-173">En la lista siguiente se describe cada una de forma pormenorizada:</span><span class="sxs-lookup"><span data-stu-id="06f06-173">The following list describes each in detail:</span></span>  

- <span data-ttu-id="06f06-174">**NX_DNS_TYPE_OF_SERVICE** Tipo de servicio necesario para las solicitudes UDP de DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-174">**NX_DNS_TYPE_OF_SERVICE** Type of service required for the DNS UDP requests.</span></span> <span data-ttu-id="06f06-175">De forma predeterminada, este valor se define como NX_IP_NORMAL para el servicio de paquetes IP normal.</span><span class="sxs-lookup"><span data-stu-id="06f06-175">By default, this value is defined as NX_IP_NORMAL for normal IP packet service.</span></span>

- <span data-ttu-id="06f06-176">**NX_DNS_TIME_TO_LIVE** Especifica el número máximo de enrutadores que un paquete puede pasar antes de que se descarte.</span><span class="sxs-lookup"><span data-stu-id="06f06-176">**NX_DNS_TIME_TO_LIVE** Specifies the maximum number of routers a packet can pass before it is discarded.</span></span> <span data-ttu-id="06f06-177">El valor predeterminado es 0x80.</span><span class="sxs-lookup"><span data-stu-id="06f06-177">The default value is 0x80.</span></span>

- <span data-ttu-id="06f06-178">**NX_DNS_FRAGMENT_OPTION** Establece la propiedad de socket para permitir o impedir la fragmentación de los paquetes de salida.</span><span class="sxs-lookup"><span data-stu-id="06f06-178">**NX_DNS_FRAGMENT_OPTION** Sets the socket property to allow or disallow fragmentation of outgoing packets.</span></span> <span data-ttu-id="06f06-179">El valor predeterminado es NX_DONT_FRAGMENT.</span><span class="sxs-lookup"><span data-stu-id="06f06-179">The default value is NX_DONT_FRAGMENT.</span></span>

- <span data-ttu-id="06f06-180">**NX_DNS_QUEUE_DEPTH** Establece el número máximo de paquetes que se almacenan en la cola de recepción del socket.</span><span class="sxs-lookup"><span data-stu-id="06f06-180">**NX_DNS_QUEUE_DEPTH** Sets the maximum number of packets to store on the socket receive queue.</span></span> <span data-ttu-id="06f06-181">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="06f06-181">The default value is 5.</span></span>

- <span data-ttu-id="06f06-182">**NX_DNS_MAX_SERVERS** Especifica el número máximo de servidores DNS en la lista de servidor cliente.</span><span class="sxs-lookup"><span data-stu-id="06f06-182">**NX_DNS_MAX_SERVERS** Specifies the maximum number of DNS Servers in the Client server list.</span></span> <span data-ttu-id="06f06-183">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="06f06-183">The default value is 5.</span></span>

- <span data-ttu-id="06f06-184">**NX_DNS_MESSAGE_MAX** Tamaño máximo del mensaje DNS para enviar consultas de DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-184">**NX_DNS_MESSAGE_MAX** The maximum DNS message size for sending DNS queries.</span></span> <span data-ttu-id="06f06-185">El valor predeterminado es 512, que también es el tamaño máximo especificado en el RFC 1035 sección 2.3.4.</span><span class="sxs-lookup"><span data-stu-id="06f06-185">The default value is 512, which is also the maximum size specified in RFC 1035 Section 2.3.4.</span></span>

- <span data-ttu-id="06f06-186">**NX_DNS_PACKET_PAYLOAD_UNALIGNED** Si no se define, el tamaño de la carga del paquete de cliente que incluye los encabezados Ethernet, IP (o IPv6) y UDP más el tamaño de mensaje DNS máximo especificado por NX_DNS_MESSAGE_MAX.</span><span class="sxs-lookup"><span data-stu-id="06f06-186">**NX_DNS_PACKET_PAYLOAD_UNALIGNED** If not defined, the size of the Client packet payload which includes the Ethernet, IP (or IPv6), and UDP headers plus the maximum DNS message size specified by NX_DNS_MESSAGE_MAX.</span></span> <span data-ttu-id="06f06-187">Independientemente de si está definido, la carga del paquete es los 4 bytes alineados y almacenados en NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="06f06-187">Regardless if defined, the packet payload is the 4-byte aligned and stored in NX_DNS_PACKET_PAYLOAD.</span></span>

- <span data-ttu-id="06f06-188">**NX_DNS_PACKET_POOL_SIZE** Tamaño del grupo de paquetes de cliente para enviar consultas de DNS si no se define NX_DNS_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="06f06-188">**NX_DNS_PACKET_POOL_SIZE** Size of the Client packet pool for sending DNS queries if NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is not defined.</span></span> <span data-ttu-id="06f06-189">El valor predeterminado es lo suficientemente grande para 16 paquetes de tamaño de carga definido por NX_DNS_PACKET_PAYLOAD y es de 4 bytes alineados.</span><span class="sxs-lookup"><span data-stu-id="06f06-189">The default value is large enough for 16 packets of payload size defined by NX_DNS_PACKET_PAYLOAD, and is 4-byte aligned.</span></span>

- <span data-ttu-id="06f06-190">**NX_DNS_MAX_RETRIES** Número máximo de veces que el cliente DNS consultará el servidor DNS actual antes de intentar otro servidor o anular la consulta de DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-190">**NX_DNS_MAX_RETRIES** The maximum number of times the DNS Client will query the current DNS server before trying another server or aborting the DNS query.</span></span> <span data-ttu-id="06f06-191">El valor predeterminado es 3.</span><span class="sxs-lookup"><span data-stu-id="06f06-191">The default value is 3.</span></span>

- <span data-ttu-id="06f06-192">**NX_DNS_MAX_RETRANS_TIMEOUT** El tiempo de espera máximo de retransmisión en una consulta de DNS a un servidor DNS específico.</span><span class="sxs-lookup"><span data-stu-id="06f06-192">**NX_DNS_MAX_RETRANS_TIMEOUT** The maximum retransmission timeout on a DNS query to a specific DNS server.</span></span> <span data-ttu-id="06f06-193">El valor predeterminado es 64 segundos (64 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="06f06-193">The default value is 64 seconds (64 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="06f06-194">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER** Si se define y la dirección de puerta de enlace IPv4 del cliente es distinta de cero, el cliente DNS establece la puerta de enlace IPv4 como el servidor DNS principal del cliente.</span><span class="sxs-lookup"><span data-stu-id="06f06-194">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER** If defined and the Client IPv4 gateway address is non zero, the DNS Client sets the IPv4 gateway as the Client’s primary DNS server.</span></span> <span data-ttu-id="06f06-195">El valor predeterminado está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="06f06-195">The default value is disabled.</span></span>

- <span data-ttu-id="06f06-196">**NX_DNS_PACKET_ALLOCATE_TIMEOUT** Establece la opción de tiempo de espera para la asignación de un paquete desde el grupo de paquetes de cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-196">**NX_DNS_PACKET_ALLOCATE_TIMEOUT** This sets the timeout option for allocating a packet from the DNS client packet pool.</span></span> <span data-ttu-id="06f06-197">El valor predeterminado es 1 segundo (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="06f06-197">The default value is 1 second (1\*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="06f06-198">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** Posibilita que el cliente DNS permita a la aplicación crear y establecer el grupo de paquetes de cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-198">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** This enables the DNS Client to let the application create and set the DNS Client packet pool.</span></span> <span data-ttu-id="06f06-199">De forma predeterminada, esta opción está deshabilitada y el cliente DNS crea su propio grupo de paquetes en *nx_dns_create*.</span><span class="sxs-lookup"><span data-stu-id="06f06-199">By default this option is disabled, and the DNS Client creates its own packet pool in *nx_dns_create*.</span></span>

- <span data-ttu-id="06f06-200">**NX_DNS_CLIENT_CLEAR_QUEUE** Permite que el cliente DNS borre los mensajes DNS antiguos de la cola de recepción antes de enviar una nueva consulta.</span><span class="sxs-lookup"><span data-stu-id="06f06-200">**NX_DNS_CLIENT_CLEAR_QUEUE** This enables the DNS Client to clear old DNS messages off the receive queue before sending a new query.</span></span> <span data-ttu-id="06f06-201">La eliminación de estos paquetes de consultas de DNS anteriores impide que la cola del socket de cliente DNS se desborde y quite paquetes válidos.</span><span class="sxs-lookup"><span data-stu-id="06f06-201">Removing these packets from previous DNS queries prevents the DNS Client socket queue from overflowing and dropping valid packets.</span></span>

- <span data-ttu-id="06f06-202">**NX_DNS_ENABLE_EXTENDED_RR_TYPES** Permite que el cliente DNS consulte otros tipos de registro DNS (por ejemplo, CNAME, NS, MX, SOA, SRV y TXT).</span><span class="sxs-lookup"><span data-stu-id="06f06-202">**NX_DNS_ENABLE_EXTENDED_RR_TYPES** This enables the DNS Client to query on additional DNS record types in (e.g. CNAME, NS, MX, SOA, SRV and TXT).</span></span>

- <span data-ttu-id="06f06-203">**NX_DNS_CACHE_ENABLE** Permite que el cliente DNS almacene los registros de respuesta en la memoria caché de DNS.</span><span class="sxs-lookup"><span data-stu-id="06f06-203">**NX_DNS_CACHE_ENABLE** This enables the DNS Client to store the answer records into DNS cache.</span></span>