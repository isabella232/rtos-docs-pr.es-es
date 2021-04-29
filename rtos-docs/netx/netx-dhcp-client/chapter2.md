---
title: 'Capítulo 2: Instalación y uso del cliente DHCP para NetX de Azure RTOS'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente de cliente DHCP para NetX de Azure RTOS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9224a4df70b8199032066e30108250a3baeb65f5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815253"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a><span data-ttu-id="65553-103">Capítulo 2: Instalación y uso del cliente DHCP para NetX de Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="65553-103">Chapter 2 - Installation and use of Azure RTOS NetX DHCP Client</span></span>

<span data-ttu-id="65553-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente DHCP para NetX de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="65553-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="65553-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="65553-105">Product Distribution</span></span>

<span data-ttu-id="65553-106">DHCP para NetX está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="65553-106">DHCP for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="65553-107">El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="65553-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="65553-108">**nx_dhcp.h** Archivo de encabezado de DHCP para NetX</span><span class="sxs-lookup"><span data-stu-id="65553-108">**nx_dhcp.h** Header file for DHCP for NetX</span></span>

- <span data-ttu-id="65553-109">**nx_dhcp.c** Archivo de código fuente C de DHCP para NetX</span><span class="sxs-lookup"><span data-stu-id="65553-109">**nx_dhcp.c** C Source file for DHCP for NetX</span></span>

- <span data-ttu-id="65553-110">**nx_dhcp.pdf** Descripción en PDF de DHCP para NetX</span><span class="sxs-lookup"><span data-stu-id="65553-110">**nx_dhcp.pdf** PDF description of DHCP for NetX</span></span>

- <span data-ttu-id="65553-111">**demo_netx_dhcp.c** Demostración de DHCP para NetX</span><span class="sxs-lookup"><span data-stu-id="65553-111">**demo_netx_dhcp.c** NetX DHCP demonstration</span></span>

- <span data-ttu-id="65553-112">**demo_netx_multihome_dhcp_client.c** Demostración del cliente DHCP de NetX en varias interfaces</span><span class="sxs-lookup"><span data-stu-id="65553-112">**demo_netx_multihome_dhcp_client.c** NetX DHCP Client demonstration of DHCP on multiple interfaces</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="65553-113">Instalación de DHCP</span><span class="sxs-lookup"><span data-stu-id="65553-113">DHCP Installation</span></span>

<span data-ttu-id="65553-114">Para usar DHCP para NetX, toda la distribución que se menciona anteriormente debe copiarse en el mismo directorio en el que se ha instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="65553-114">To use DHCP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="65553-115">Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_dhcp.h* y *nx_dhcp.c* deben copiarse en este directorio.</span><span class="sxs-lookup"><span data-stu-id="65553-115">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_dhcp.h* and *nx_dhcp.c* files should be copied into this directory.</span></span>

## <a name="using-dhcp"></a><span data-ttu-id="65553-116">Uso de DHCP</span><span class="sxs-lookup"><span data-stu-id="65553-116">Using DHCP</span></span>

<span data-ttu-id="65553-117">DHCP para NetX es fácil de utilizar.</span><span class="sxs-lookup"><span data-stu-id="65553-117">Using DHCP for NetX is easy.</span></span> <span data-ttu-id="65553-118">Básicamente, el código de la aplicación debe incluir *nx_dhcp.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="65553-118">Basically, the application code must include *nx_dhcp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="65553-119">Después de incluir *nx_dhcp.h*, el código de la aplicación puede realizar las llamadas de función DHCP especificadas más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="65553-119">Once *nx_dhcp.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="65553-120">La aplicación también debe incluir *nx_dhcp.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="65553-120">The application must also include *nx_dhcp.c* in the build process.</span></span> <span data-ttu-id="65553-121">Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="65553-121">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="65553-122">Esto es todo lo que se necesita para usar DHCP para NetX.</span><span class="sxs-lookup"><span data-stu-id="65553-122">This is all that is required to use NetX DHCP.</span></span>

<span data-ttu-id="65553-123">Tenga en cuenta que, como DHCP usa los servicios de UDP de NetX, debe habilitarse UDP con la llamada a *nx_udp_enable* antes de utilizar DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-123">Note that since DHCP utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

<span data-ttu-id="65553-124">Para obtener una dirección IP asignada previamente, el cliente DHCP puede iniciar el proceso de DHCP con el mensaje Request y la opción 50 "Requested IP Address" (Dirección IP solicitada) en el servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-124">To obtain a previously assigned IP address, the DHCP Client can initiate the DHCP process with the Request message and Option 50 “Requested IP Address” to the DHCP Server.</span></span> <span data-ttu-id="65553-125">El servidor DHCP responderá con un mensaje ACK si concede la dirección IP al cliente o un mensaje NACK si la rechaza.</span><span class="sxs-lookup"><span data-stu-id="65553-125">The DHCP Server will respond with either an ACK message if it grants the IP address to the Client or a NACK if it refuses.</span></span> <span data-ttu-id="65553-126">En el último caso, el cliente DHCP reinicia el proceso de DHCP en el estado Init con un mensaje Discover y ninguna dirección IP solicitada.</span><span class="sxs-lookup"><span data-stu-id="65553-126">In the latter case, the DHCP Client restarts the DHCP process at the Init state with a Discover message and no requested IP address.</span></span> <span data-ttu-id="65553-127">La aplicación host crea primero el cliente DHCP y, a continuación, llama al servicio de API *nx_dhcp_request_client_ip* para establecer la dirección IP solicitada antes de iniciar el proceso de DHCP con *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="65553-127">The host application first creates the DHCP Client, then calls the *nx_dhcp_request_client_ip* API service to set the requested IP address before starting the DHCP process with *nx_dhcp_start*.</span></span> <span data-ttu-id="65553-128">Se proporciona una aplicación DHCP de ejemplo en este documento para ofrecer más detalles.</span><span class="sxs-lookup"><span data-stu-id="65553-128">An example DHCP application is provided elsewhere in this document for more details.</span></span>

## <a name="in-the-bound-state"></a><span data-ttu-id="65553-129">En estado enlazado</span><span class="sxs-lookup"><span data-stu-id="65553-129">In the Bound State</span></span>

<span data-ttu-id="65553-130">Mientras el cliente DHCP se encuentra en estado enlazado, el subproceso de cliente DHCP procesa el estado del cliente una vez por intervalo (según se especifica en NX_DHCP_TIME_INTERVAL) y reduce el tiempo restante de la concesión de IP asignada al cliente.</span><span class="sxs-lookup"><span data-stu-id="65553-130">While the DHCP Client is in the bound state, the DHCP Client thread processes the Client state once per interval (as specified by NX_DHCP_TIME_INTERVAL) and decrements the time remaining on the IP lease assigned to the Client.</span></span> <span data-ttu-id="65553-131">Cuando el tiempo de renovación ha transcurrido, el estado del cliente DHCP se actualiza al estado RENEW, en el que el cliente solicitará una renovación del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-131">When the renewal time has elapsed the DHCP Client state is updated to the RENEW state where the Client will request a renewal from the DHCP Server.</span></span>


## <a name="sending-dhcp-messages-to-the-server"></a><span data-ttu-id="65553-132">Envío de mensajes DHCP al servidor</span><span class="sxs-lookup"><span data-stu-id="65553-132">Sending DHCP Messages To The Server</span></span>

<span data-ttu-id="65553-133">El cliente DHCP dispone de servicios de API que permiten que la aplicación host envíe un mensaje al servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-133">The DHCP Client has API services that allow the host application to send a message to the DHCP Server.</span></span> <span data-ttu-id="65553-134">Tenga en cuenta que estos servicios no están diseñados para que la aplicación host ejecute manualmente el protocolo de cliente DHCP ya que envían el mensaje, sin actualizar necesariamente el estado interno del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-134">Note these services are NOT intended for the host application to manually run the DHCP Client protocol as they primarily send the message without necessarily updating the DHCP Client internal state.</span></span>

  - <span data-ttu-id="65553-135">*nx_dhcp_release*: envía un mensaje RELEASE al servidor cuando la aplicación host abandona la red o necesita ceder su dirección IP.</span><span class="sxs-lookup"><span data-stu-id="65553-135">*nx_dhcp_release*: this sends a RELEASE message to the Server when the host application is either leaving the network or needs relinquish its IP address.</span></span>

  - <span data-ttu-id="65553-136">*nx_dhcp_decline*: envía un mensaje DECLINE al servidor si la aplicación host determina independientemente del cliente DHCP que su dirección IP ya está en uso.</span><span class="sxs-lookup"><span data-stu-id="65553-136">*nx_dhcp_decline*: this sends a DECLINE message to the Server if the host application determines independently of the DHCP Client that its IP address is already in use.</span></span>

  - <span data-ttu-id="65553-137">*nx_dhcp_forcerenew*: envía un mensaje FORCERENEW al servidor.</span><span class="sxs-lookup"><span data-stu-id="65553-137">*nx_dhcp_forcerenew*: this sends a FORCERENEW message to the Server</span></span>

  - <span data-ttu-id="65553-138">*nx_dhcp_send_request*: toma como argumento un tipo de mensaje de DHCP, como se especifica en *nx_dhcp.h*, y envía el mensaje al servidor.</span><span class="sxs-lookup"><span data-stu-id="65553-138">*nx_dhcp_send_request*: This takes as an argument a DHCP message type, as specified in *nx_dhcp.h*, and sends the message to the Server.</span></span> <span data-ttu-id="65553-139">Está pensado principalmente para enviar el mensaje DHCP INFORM.</span><span class="sxs-lookup"><span data-stu-id="65553-139">This is intended primarily for sending the DHCP INFORM message.</span></span>

<span data-ttu-id="65553-140">Vea la sección "*Descripción de los servicios DHCP*" en este documento para más información sobre estos servicios.</span><span class="sxs-lookup"><span data-stu-id="65553-140">See “*Description of DHCP Services*” for more information about these services elsewhere in this document.</span></span>

## <a name="starting-and-stopping-the-dhcp-client"></a><span data-ttu-id="65553-141">Inicio y detención del cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="65553-141">Starting and Stopping the DHCP Client</span></span>

<span data-ttu-id="65553-142">Para detener el cliente DHCP, independientemente de si ha logrado un estado enlazado, la aplicación host llama a *nx_dhcp_stop*.</span><span class="sxs-lookup"><span data-stu-id="65553-142">To stop the DHCP Client, regardless if it has achieved a bound state, the host application calls *nx_dhcp_stop*.</span></span>

<span data-ttu-id="65553-143">Para reiniciar un cliente DHCP, la aplicación host debe detener primero el cliente DHCP mediante el servicio *nx_dhcp_stop* descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="65553-143">To restart a DHCP client, the host application must first stop the DHCP Client using the *nx_dhcp_stop* service described above.</span></span> <span data-ttu-id="65553-144">A continuación, el host puede llamar a *nx_dhcp_start* para reanudar el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-144">Then the host can call *nx_dhcp_start* to resume the DHCP Client.</span></span> <span data-ttu-id="65553-145">Si la aplicación host desea borrar un perfil de cliente DHCP anterior, por ejemplo, uno obtenido de un servidor DHCP anterior de otra red, la aplicación host debe llamar a *nx_dhcp_reinitialize* para realizar esta tarea internamente antes de llamar a nx_dhcp_start.</span><span class="sxs-lookup"><span data-stu-id="65553-145">If the host application wishes to clear a previous DHCP Client profile, for example, one obtained from a previous DHCP Server on another network, the host application should call *nx_dhcp_reinitialize* to perform this task internally before calling nx_dhcp_start.</span></span>

<span data-ttu-id="65553-146">Una secuencia típica podría ser:</span><span class="sxs-lookup"><span data-stu-id="65553-146">A typical sequence might be:</span></span>

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="65553-147">En el caso de las aplicaciones DHCP que se ejecutan en una sola interfaz DHCP, la detención del cliente DHCP también desactiva el temporizador del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-147">For DHCP applications running on only a single DHCP interface, stopping the DHCP Client also inactivates the DHCP CLIENT timer.</span></span> <span data-ttu-id="65553-148">Por lo tanto, ya no realiza un seguimiento del tiempo restante de la concesión de IP.</span><span class="sxs-lookup"><span data-stu-id="65553-148">Thus it is no longer keeping track of the time remaining on the IP lease.</span></span> <span data-ttu-id="65553-149">Al detener el cliente DHCP en una interfaz determinada, no se desactivará el temporizador del cliente DHCP, pero se detendrán las actualizaciones del temporizador del tiempo restante de la concesión de IP en esa interfaz.</span><span class="sxs-lookup"><span data-stu-id="65553-149">Stopping DHCP Client on a particular interface will not inactivate the DHCP Client timer but will stop timer updates to the time remaining on the IP lease on that interface.</span></span>

<span data-ttu-id="65553-150">Por lo tanto, no se recomienda detener el cliente DHCP a menos que la aplicación host requiera un reinicio o conmutación de redes.</span><span class="sxs-lookup"><span data-stu-id="65553-150">Therefore, stopping the DHCP Client is not advised unless the host application requires rebooting or switching networks.</span></span>

## <a name="using-the-dhcp-client-with-auto-ip"></a><span data-ttu-id="65553-151">Uso del cliente DHCP con IP automática</span><span class="sxs-lookup"><span data-stu-id="65553-151">Using the DHCP Client with Auto IP</span></span>

<span data-ttu-id="65553-152">El cliente DHCP para NetX funciona simultáneamente con el protocolo de IP automática en las aplicaciones en las que DHCP y la IP automática garantizan una dirección cuando no se garantiza que un servidor DHCP esté disponible o responda.</span><span class="sxs-lookup"><span data-stu-id="65553-152">The NetX DHCP Client works concurrently with the Auto IP protocol in applications where DHCP and Auto IP guarantee an address where a DHCP Server is not guaranteed to be available or responding.</span></span> <span data-ttu-id="65553-153">Sin embargo, si el host no puede detectar un servidor u obtener una dirección IP asignada, puede cambiar al protocolo de IP automática para una dirección IP local.</span><span class="sxs-lookup"><span data-stu-id="65553-153">However, If the host is unable to detect a Server or get an IP address assigned, it can switch to the Auto IP protocol for a local IP address.</span></span> <span data-ttu-id="65553-154">Aunque, antes de hacerlo, es aconsejable detener temporalmente el cliente DHCP mientras la IP automática pasa por las fases de "sondeo" y "defensa".</span><span class="sxs-lookup"><span data-stu-id="65553-154">However before doing so, it is advisable to stop the DHCP Client temporarily while Auto IP goes through the “probe” and “defense” stages.</span></span> <span data-ttu-id="65553-155">Una vez asignada una dirección IP automática al host, se puede reiniciar el cliente DHCP y, si está disponible un servidor DHCP, la dirección IP del host puede aceptar la dirección IP que ofrece el servidor DHCP mientras la aplicación se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="65553-155">Once an Auto IP address is assigned to the host, the DHCP Client can be restarted and if a DHCP Server does become available, the host IP address can accept the IP address offered by the DHCP Server while the application is running.</span></span>

<span data-ttu-id="65553-156">La IP automática de NetX dispone de una notificación de cambio de dirección para que el host supervise sus actividades en caso de un cambio de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="65553-156">The NetX Auto IP has an address change notification for the host to monitor its activities in the event of an IP address change.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="65553-157">Sistema de ejemplo pequeño</span><span class="sxs-lookup"><span data-stu-id="65553-157">Small Example System</span></span>

<span data-ttu-id="65553-158">En la figura 1.1 siguiente, se describe un ejemplo de cómo usar NetX.</span><span class="sxs-lookup"><span data-stu-id="65553-158">An example of how use NetX is described in Figure 1.1 below.</span></span> <span data-ttu-id="65553-159">El cliente DHCP "*my_thread_entry*" se crea en la línea 101.</span><span class="sxs-lookup"><span data-stu-id="65553-159">The DHCP Client is created “*my_thread_entry*” at line 101.</span></span> <span data-ttu-id="65553-160">Después de que se cree correctamente, el proceso DHCP se inicia en la llamada a *nx_dhcp_start* en la línea 108.</span><span class="sxs-lookup"><span data-stu-id="65553-160">After successful creation, the DHCP process is initiated at the call to *nx_dhcp_start* at line 108.</span></span> <span data-ttu-id="65553-161">En este momento, se inician los intentos del cliente DHCP para ponerse en contacto con el servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-161">At this point the DHCP Client attempts are initiated to contact the DHCP server.</span></span> <span data-ttu-id="65553-162">Durante este proceso, el código de aplicación espera a que se registre una dirección IP válida en la instancia de IP mediante el servicio de *nx_ip_status_check* (o *nx_ip_interface_status_check* para una interfaz secundaria) a partir de la línea 95.</span><span class="sxs-lookup"><span data-stu-id="65553-162">During this process, the application code waits for a valid IP address to be registered with the IP instance using the *nx_ip_status_check* service (or *nx_ip_interface_status_check* for a secondary interface) starting at line 95.</span></span> <span data-ttu-id="65553-163">Esto se hace más habitualmente en un bucle con una opción de espera más corta.</span><span class="sxs-lookup"><span data-stu-id="65553-163">This is more commonly done in a loop with a shorter wait option.</span></span>

<span data-ttu-id="65553-164">Después de la línea 127, DHCP ha recibido una dirección IP válida y la aplicación puede continuar usando los servicios TCP/IP de NetX como se desee.</span><span class="sxs-lookup"><span data-stu-id="65553-164">After line 127, DHCP has received a valid IP address and the application can then proceed, utilizing NetX TCP/IP services as desired.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
      0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
      DEMO_STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


/* Define my thread. */

void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    actual_status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                            &actual_status, 100);

  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="65553-165">Figura 1.1 Ejemplo de uso de DHCP con NetX</span><span class="sxs-lookup"><span data-stu-id="65553-165">Figure 1.1 Example of DHCP use with NetX</span></span>

## <a name="multi-server-environments"></a><span data-ttu-id="65553-166">Entornos de varios servidores</span><span class="sxs-lookup"><span data-stu-id="65553-166">Multi-Server Environments</span></span>

<span data-ttu-id="65553-167">En las redes en las que hay más de un servidor DHCP, el cliente DHCP acepta el primer mensaje Offer recibido del servidor DHCP, avanza hasta el estado Request y omite cualquier otra oferta recibida.</span><span class="sxs-lookup"><span data-stu-id="65553-167">On networks where there is more than one DHCP Server, the DHCP Client accepts the first received DHCP Server Offer message, advances to the Request state, and ignores any other received offers.</span></span>

## <a name="arp-probes"></a><span data-ttu-id="65553-168">Sondeos ARP</span><span class="sxs-lookup"><span data-stu-id="65553-168">ARP Probes</span></span>

<span data-ttu-id="65553-169">El cliente DHCP puede configurarse para enviar uno o más sondeos ARP después de la asignación de direcciones IP del servidor DHCP para comprobar que la dirección IP aún no está en uso.</span><span class="sxs-lookup"><span data-stu-id="65553-169">The DHCP Client can be configured to send one or more ARP probes after IP address assignment from the DHCP Server to verify the IP address is not already in use.</span></span> <span data-ttu-id="65553-170">En el RFC 2131 se recomienda el paso de sondeo ARP y es especialmente importante en entornos con más de un servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-170">The ARP probe step is recommended by RFC 2131 and is particularly important in environments with more than one DHCP Server.</span></span> <span data-ttu-id="65553-171">Si la aplicación host habilita la opción NX_DHCP_CLIENT_SEND_ARP_PROBE (consulte **Opciones de configuración** en el capítulo dos de las opciones adicionales de sondeo ARP), el cliente DHCP enviará un sondeo ARP "autodireccionado" y esperará durante el tiempo especificado para recibir una respuesta.</span><span class="sxs-lookup"><span data-stu-id="65553-171">If the host application enables the NX_DHCP_CLIENT_SEND_ARP_PROBE option (see **Configuration Options** in Chapter Two for additional ARP probe options), the DHCP Client will send a ‘self addressed’ ARP probe and wait for the specified time for a response.</span></span> <span data-ttu-id="65553-172">Si no se recibe ninguna, el cliente DHCP avanza al estado Bound.</span><span class="sxs-lookup"><span data-stu-id="65553-172">If none is received, the DHCP Client advances to the Bound state.</span></span> <span data-ttu-id="65553-173">Si se recibe una respuesta, el cliente DHCP supone que la dirección ya está en uso.</span><span class="sxs-lookup"><span data-stu-id="65553-173">If a response is received, the DHCP Client assumes the address is already in use.</span></span> <span data-ttu-id="65553-174">Envía automáticamente un mensaje DECLINE al servidor y reinicializa el cliente para reiniciar los sondeos DHCP de nuevo desde el estado INIT.</span><span class="sxs-lookup"><span data-stu-id="65553-174">It automatically sends a DECLINE message to the Server, and reinitializes the Client to restart the DHCP probes again from the INIT state.</span></span> <span data-ttu-id="65553-175">Así se reinicia la máquina de estado DHCP y el cliente envía otro mensaje DISCOVER al servidor.</span><span class="sxs-lookup"><span data-stu-id="65553-175">This restarts the DHCP state machine and the Client sends another DISCOVER message to the Server.</span></span>

## <a name="bootp-protocol"></a><span data-ttu-id="65553-176">Protocolo BOOTP</span><span class="sxs-lookup"><span data-stu-id="65553-176">BOOTP Protocol</span></span>

<span data-ttu-id="65553-177">El cliente DHCP también admite el protocolo BOOTP además del protocolo DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-177">The DHCP Client also supports the BOOTP protocol as well the DHCP protocol.</span></span> <span data-ttu-id="65553-178">Para habilitar esta opción y usar BOOTP en lugar de DHCP, la aplicación host debe establecer la opción de configuración NX_DHCP_BOOTP_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="65553-178">To enable this option and use BOOTP instead of DHCP, the host application must set the NX_DHCP_BOOTP_ENABLE configuration option.</span></span> <span data-ttu-id="65553-179">La aplicación host también puede solicitar direcciones IP específicas en el protocolo BOOTP.</span><span class="sxs-lookup"><span data-stu-id="65553-179">The host application can still request specific IP addresses in the BOOTP protocol.</span></span> <span data-ttu-id="65553-180">Sin embargo, el cliente DHCP no admite la carga del sistema operativo host, ya que a veces se usa BOOTP para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="65553-180">However, the DHCP Client does not support loading the host operating system as BOOTP is sometimes used to do.</span></span>

## <a name="dhcp-on-a-secondary-interface"></a><span data-ttu-id="65553-181">DHCP en una interfaz secundaria</span><span class="sxs-lookup"><span data-stu-id="65553-181">DHCP on a Secondary Interface</span></span>

<span data-ttu-id="65553-182">El cliente DHCP de NetX puede ejecutarse en interfaces secundarias en lugar de en la interfaz principal predeterminada.</span><span class="sxs-lookup"><span data-stu-id="65553-182">The NetX DHCP Client can run on secondary interfaces rather than the default primary interface.</span></span>

<span data-ttu-id="65553-183">Para ejecutar el cliente DHCP de NetX en una interfaz de red secundaria, la aplicación host debe establecer el índice de interfaz del cliente DHCP en la interfaz secundaria mediante el servicio de API *nx_dhcp_set_interface_index*.</span><span class="sxs-lookup"><span data-stu-id="65553-183">To run NetX DHCP Client on a secondary network interface, the host application must set the interface index of the DHCP Client to the secondary interface using the *nx_dhcp_set_interface_index* API service.</span></span> <span data-ttu-id="65553-184">La interfaz ya debe estar conectada a la interfaz de red principal mediante el servicio *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="65553-184">The interface must already be attached to the primary network interface using the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="65553-185">Consulte la guía del usuario de NetX para obtener más detalles sobre cómo conectar interfaces secundarias.</span><span class="sxs-lookup"><span data-stu-id="65553-185">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="65553-186">En la figura 1.2 siguiente, se muestra un sistema de ejemplo en el que la aplicación host se conecta al servidor DHCP en su interfaz secundaria.</span><span class="sxs-lookup"><span data-stu-id="65553-186">Below in Figure 1.2 is an example system on which the host application connects to the DHCP server on its secondary interface.</span></span> <span data-ttu-id="65553-187">En la línea 65, la interfaz secundaria se conecta a la tarea de IP con una dirección IP nula.</span><span class="sxs-lookup"><span data-stu-id="65553-187">On line 65, the secondary interface is attached to the IP task with a null IP address.</span></span> <span data-ttu-id="65553-188">En la línea 104, una vez creada la instancia de cliente DHCP, el índice de la interfaz de cliente DHCP se establece en 1 (por ejemplo, el desplazamiento desde la interfaz principal que es el índice 0) mediante una llamada a *nx_dhcp_set_interface_index*.</span><span class="sxs-lookup"><span data-stu-id="65553-188">On line 104, after the DHCP Client instance is created, the DHCP Client interface index is set to 1 (e.g. the offset from the primary interface which itself is index 0) by calling *nx_dhcp_set_interface_index*.</span></span> <span data-ttu-id="65553-189">Después, el cliente DHCP está listo para iniciarse en la línea 108.</span><span class="sxs-lookup"><span data-stu-id="65553-189">Then the DHCP Client is ready to be started in line 108.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
       0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  status = _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                            0xFFFFFF00UL, my_netx_driver);
                            
  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Set the DHCP client interface to the secondary interface. 
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="65553-190">Figura 1.2 Ejemplo de DHCP para NetX con compatibilidad de varios orígenes</span><span class="sxs-lookup"><span data-stu-id="65553-190">Figure 1.2 Example of DHCP for NetX with multihome support</span></span>

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a><span data-ttu-id="65553-191">Cliente DHCP en varias interfaces simultáneamente</span><span class="sxs-lookup"><span data-stu-id="65553-191">DHCP Client on Multiple Interfaces Simultaneously</span></span>

<span data-ttu-id="65553-192">Para ejecutar el cliente DHCP en varias interfaces, se debe establecer NX_MAX_PHYSICAL_INTERFACES de *nx_api.h* en el número de interfaces físicas conectadas al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="65553-192">To run DHCP Client on multiple interfaces, NX_MAX_PHYSICAL_INTERFACES in *nx_api.h* must be set to the number of physical interfaces connected to the device.</span></span> <span data-ttu-id="65553-193">De forma predeterminada, este valor es 1 (es decir, la interfaz principal).</span><span class="sxs-lookup"><span data-stu-id="65553-193">By default, this value is 1 (e.g. the primary interface).</span></span> <span data-ttu-id="65553-194">Para registrar una interfaz adicional en la instancia de IP, use el servicio *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="65553-194">To register an additional interface to the IP instance use the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="65553-195">Consulte la guía del usuario de NetX para obtener más detalles sobre cómo conectar interfaces secundarias.</span><span class="sxs-lookup"><span data-stu-id="65553-195">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="65553-196">El siguiente paso consiste en establecer NX_DHCP_CLIENT_MAX_RECORDS de *nx_dhcp.h* en el número máximo de interfaces que se espera que ejecuten DHCP simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="65553-196">The next step is to set the NX_DHCP_CLIENT_MAX_RECORDS in *nx_dhcp.h* to the maximum number of interfaces expected to run DHCP simultaneously.</span></span> <span data-ttu-id="65553-197">Tenga en cuenta que NX_DHCP_CLIENT_MAX_RECORDS no tiene que ser igual a NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="65553-197">Note that NX_DHCP_CLIENT_MAX_RECORDS does not have to equal NX_MAX_PHYSICAL_INTERFACES.</span></span> <span data-ttu-id="65553-198">Por ejemplo, NX_MAX_PHYSICAL_INTERFACES puede ser 3 y NX_DHCP_CLIENT_MAX_RECORDS puede ser 2.</span><span class="sxs-lookup"><span data-stu-id="65553-198">For example, NX_MAX_PHYSICAL_INTERFACES can be 3 and NX_DHCP_CLIENT_MAX_RECORDS equal to 2.</span></span> <span data-ttu-id="65553-199">En esta configuración, solo dos interfaces (pueden ser cualquiera de las tres interfaces físicas en cualquier momento) de las tres interfaces físicas pueden ejecutar DHCP al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="65553-199">In this configuration, only two interfaces (and they can be any two of the three physical interfaces at any time) of the three physical interfaces can run DHCP at any one time.</span></span> <span data-ttu-id="65553-200">Los registros de cliente DHCP no tienen una asignación de uno a uno con las interfaces de red, por ejemplo, el registro del cliente 1 no se correlaciona automáticamente con el índice de interfaz física 1.</span><span class="sxs-lookup"><span data-stu-id="65553-200">DHCP Client Records do not have a one to one mapping to network interfaces e.g. Client Record 1 does not automatically correlate to physical interface index 1.</span></span>

<span data-ttu-id="65553-201">NX_DHCP_CLIENT_MAX_RECORDS también se puede establecer en un valor mayor que NX_MAX_PHYSICAL_INTERFACES, pero esto crearía registros de cliente no usados y sería un uso ineficaz de la memoria.</span><span class="sxs-lookup"><span data-stu-id="65553-201">NX_DHCP_CLIENT_MAX_RECORDS can also be set to greater than NX_MAX_PHYSICAL_INTERFACES but this would create unused client records and be an inefficient use of memory.</span></span>

<span data-ttu-id="65553-202">Antes de poder iniciar DHCP en cualquier interfaz, la aplicación debe habilitar las interfaces mediante una llamada a *nx_dhcp_interface_enable*.</span><span class="sxs-lookup"><span data-stu-id="65553-202">Before it can start DHCP on any interface, the application must enable those interfaces by calling *nx_dhcp_interface_enable*.</span></span> <span data-ttu-id="65553-203">Tenga en cuenta que la excepción es la interfaz principal que se habilita automáticamente en la llamada a *nx_dhcp_create* (y que se puede deshabilitar mediante el servicio *nx_dhcp_interface_disable* que se describe a continuación).</span><span class="sxs-lookup"><span data-stu-id="65553-203">Note that the exception is the primary interface which is automatically enabled in the *nx_dhcp_create* call (and which can be disabled using the *nx_dhcp_interface_disable* service discussed below).</span></span>

<span data-ttu-id="65553-204">En cualquier momento, se puede deshabilitar una interfaz para DHCP o se puede detener DHCP en esa interfaz independientemente de otras interfaces que ejecuten DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-204">At any time, an interface can be disabled for DHCP or DHCP can be stopped on that interface independently of other interfaces running DHCP.</span></span>

<span data-ttu-id="65553-205">Como se mencionó anteriormente, para habilitar una interfaz específica para DHCP, use el servicio *nx_dhcp_interface_enable* y especifique el índice de interfaz física en el argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="65553-205">As mentioned above, to enable a specific interface for DHCP, use the *nx_dhcp_interface_enable* service and specify the physical interface index in the input argument.</span></span> <span data-ttu-id="65553-206">El número máximo de interfaces que se pueden habilitar es el valor de NX_DHCP_CLIENT_MAX_RECORDS con la única limitación de que el argumento de entrada del índice de interfaz sea menor que NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="65553-206">Up to NX_DHCP_CLIENT_MAX_RECORDS interfaces can be enabled with the only limitation that the interface index input argument be less than NX_MAX_PHYSICAL_INTERFACES.</span></span>

<span data-ttu-id="65553-207">Para iniciar DHCP en una interfaz específica, utilice el servicio *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="65553-207">To start DHCP on a specific interface, use the *nx_dhcp_interface_start* service.</span></span> <span data-ttu-id="65553-208">Para iniciar DHCP en todas las interfaces habilitadas, use el servicio *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="65553-208">To start DHCP on all enabled interfaces, use the *nx_dhcp_start* service.</span></span> <span data-ttu-id="65553-209">(Las interfaces que ya han iniciado DHCP no se verán afectadas por *nx_dhcp_start*).</span><span class="sxs-lookup"><span data-stu-id="65553-209">(Interfaces that have already started DHCP will not be affected by *nx_dhcp_start*.)</span></span>

<span data-ttu-id="65553-210">Para detener DHCP en una interfaz, use el servicio *nx_dhcp_interface_stop*.</span><span class="sxs-lookup"><span data-stu-id="65553-210">To stop DHCP on an interface, use the *nx_dhcp_interface_stop* service.</span></span> <span data-ttu-id="65553-211">DHCP debe haberse iniciado ya en esa interfaz o se devolverá un estado de error.</span><span class="sxs-lookup"><span data-stu-id="65553-211">DHCP must already have started on that interface or an error status is returned.</span></span> <span data-ttu-id="65553-212">Para detener DHCP en todas las interfaces habilitadas, use el servicio *nx_dhcp_stop*.</span><span class="sxs-lookup"><span data-stu-id="65553-212">To stop DHCP on all enabled interfaces, use the *nx_dhcp_stop* service.</span></span> <span data-ttu-id="65553-213">DHCP se puede detener independientemente de otras interfaces en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="65553-213">DHCP can be stopped independently of other interfaces at any time.</span></span>

<span data-ttu-id="65553-214">La mayoría de los servicios de cliente DHCP existentes tienen un equivalente de "interfaz"; por ejemplo, *nx_dhcp_interface_release* es el equivalente específico de la interfaz de *nx_dhcp_release.*</span><span class="sxs-lookup"><span data-stu-id="65553-214">Most of the existing DHCP Client services have an ‘interface’ equivalent e.g. *nx_dhcp_interface_release* is the interface specific equivalent of *nx_dhcp_release.*</span></span> <span data-ttu-id="65553-215">Si el cliente DHCP está configurado para una sola interfaz, realizan la misma acción.</span><span class="sxs-lookup"><span data-stu-id="65553-215">If DHCP Client is configured for a single interface, they perform the same action.</span></span>

<span data-ttu-id="65553-216">Tenga en cuenta que los servicios de cliente DHCP que no son específicos de interfaz suelen aplicarse a todas las interfaces, pero no a todas.</span><span class="sxs-lookup"><span data-stu-id="65553-216">Note that non-interface specific DHCP Client services typically apply to all interfaces but not all.</span></span> <span data-ttu-id="65553-217">En el último caso, el servicio que no es específico de interfaz se aplica a la primera interfaz habilitada para DHCP que se encuentra en la búsqueda en la lista de registros de interfaz del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-217">In the latter case, the non-interface specific service applies to the first DHCP enabled interface found in searching the DHCP Client list of interface records.</span></span> <span data-ttu-id="65553-218">Vea **Descripción de los servicios** en el capítulo tres sobre cómo funciona un servicio que no es específico de interfaz cuando se habilitan varias interfaces para DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-218">See **Description of Services** in Chapter Three for how a non-interface specific service performs when multiple interfaces are enabled for DHCP.</span></span>

<span data-ttu-id="65553-219">En la secuencia de ejemplo siguiente, la instancia de IP tiene dos interfaces de red y primero se ejecuta DHCP en la interfaz secundaria.</span><span class="sxs-lookup"><span data-stu-id="65553-219">In the example sequence below, the IP instance has two network interfaces and first runs DHCP on the secondary interface.</span></span> <span data-ttu-id="65553-220">En algún momento posterior, inicia DHCP en la interfaz principal.</span><span class="sxs-lookup"><span data-stu-id="65553-220">At some time later, it starts DHCP on the primary interface.</span></span> <span data-ttu-id="65553-221">A continuación, libera la dirección IP en la interfaz principal y reinicia DHCP en la interfaz principal:</span><span class="sxs-lookup"><span data-stu-id="65553-221">Then it releases the IP address on the primary interface and restarts DHCP on the primary interface:</span></span>

```C
nx_dhcp_create(&my_dhcp_client);
/* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); 
/* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); 
/* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); 

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is restarted on primary interface. */
```

<span data-ttu-id="65553-222">Para obtener una lista completa de los servicios específicos de interfaz, vea **Descripción de los servicios** en el capítulo tres.</span><span class="sxs-lookup"><span data-stu-id="65553-222">For a complete list of interface specific services see **Description of Services** in Chapter Three.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="65553-223">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="65553-223">Configuration Options</span></span>

<span data-ttu-id="65553-224">Las opciones DHCP configurables por el usuario en *nx_dhcp.h* permiten a la aplicación host ajustar correctamente el cliente DHCP para sus requisitos particulares.</span><span class="sxs-lookup"><span data-stu-id="65553-224">User configurable DHCP options in *nx_dhcp.h* allow the host application to fine tune DHCP Client for its particular requirements.</span></span> <span data-ttu-id="65553-225">A continuación, se muestra una lista de estos parámetros:</span><span class="sxs-lookup"><span data-stu-id="65553-225">The following is a list of these parameters:</span></span>  
  
- <span data-ttu-id="65553-226">**NX_DHCP_ENABLE_BOOTP** Si se define, esta opción habilita el protocolo BOOTP en lugar de DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-226">**NX_DHCP_ENABLE_BOOTP** Defined, this option enables the BOOTP protocol instead of DHCP.</span></span> <span data-ttu-id="65553-227">Esta opción está deshabilitada de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="65553-227">By default this option is disabled.</span></span>

- <span data-ttu-id="65553-228">**NX_DHCP_CLIENT_RESTORE_STATE** Si se define, permite que el cliente DHCP guarde el "estado" actual de la licencia de cliente DHCP, incluido el tiempo restante de la concesión, y restaure este estado entre los reinicios de la aplicación de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-228">**NX_DHCP_CLIENT_RESTORE_STATE** If defined, this enables the DHCP Client to save its current DHCP Client license ‘state’ including time remaining on the lease, and restore this state between DHCP Client application reboots.</span></span> <span data-ttu-id="65553-229">El valor predeterminado está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="65553-229">The default value is disabled.</span></span>

- <span data-ttu-id="65553-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** Si se establece, el cliente DHCP no creará su propio grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="65553-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** If set, the DHCP Client will not create its own packet pool.</span></span> <span data-ttu-id="65553-231">La aplicación host debe usar el servicio nx_dhcp_packet_pool_set para establecer el grupo de paquetes del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-231">The host application must use the nx_dhcp_packet_pool_set service to set the DHCP Client packet pool.</span></span> <span data-ttu-id="65553-232">El valor predeterminado está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="65553-232">The default value is disabled.</span></span>

- <span data-ttu-id="65553-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE** Si se define, permite que el cliente DHCP envíe un sondeo ARP después de la asignación de la dirección IP para comprobar que la dirección DHCP asignada no pertenece a otro host.</span><span class="sxs-lookup"><span data-stu-id="65553-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE** Defined, this enables the DHCP Client to send an ARP probe after IP address assignment to verify the assigned DHCP address is not owned by another host.</span></span> <span data-ttu-id="65553-234">Esta opción está deshabilitada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="65553-234">By default, this option is disabled.</span></span>

- <span data-ttu-id="65553-235">**NX_DHCP_ARP_PROBE_WAIT** Define el período de tiempo que el cliente DHCP espera una respuesta después de enviar un sondeo ARP.</span><span class="sxs-lookup"><span data-stu-id="65553-235">**NX_DHCP_ARP_PROBE_WAIT** Defines the length of time the DHCP Client waits for a response after sending an ARP probe.</span></span> <span data-ttu-id="65553-236">El valor predeterminado es un segundo (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="65553-236">The default value is one second (1 \* NX_IP_PERIODIC_RATE)</span></span>

- <span data-ttu-id="65553-237">**NX_DHCP_ARP_PROBE_MIN** Define la variación mínima en el intervalo entre el envío de sondeos ARP.</span><span class="sxs-lookup"><span data-stu-id="65553-237">**NX_DHCP_ARP_PROBE_MIN** Defines the minimum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="65553-238">El valor predeterminado es 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="65553-238">The value is defaulted to 1 second.</span></span>

- <span data-ttu-id="65553-239">**NX_DHCP_ARP_PROBE_MAX** Define la variación máxima en el intervalo entre el envío de sondeos ARP.</span><span class="sxs-lookup"><span data-stu-id="65553-239">**NX_DHCP_ARP_PROBE_MAX** Defines the maximum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="65553-240">El valor predeterminado es 2 segundos.</span><span class="sxs-lookup"><span data-stu-id="65553-240">The value is defaulted to 2 seconds.</span></span>

- <span data-ttu-id="65553-241">**NX_DHCP_ARP_PROBE_NUM** Define el número de sondeos ARP enviados para determinar si la dirección IP asignada por el servidor DHCP ya está en uso.</span><span class="sxs-lookup"><span data-stu-id="65553-241">**NX_DHCP_ARP_PROBE_NUM** Defines the number of ARP probes sent for determining if the IP address assigned by the DHCP server is already in use.</span></span> <span data-ttu-id="65553-242">El valor predeterminado es 3 sondeos.</span><span class="sxs-lookup"><span data-stu-id="65553-242">The value is defaulted to 3 probes.</span></span>

- <span data-ttu-id="65553-243">**NX_DHCP_RESTART_WAIT** Define el período de tiempo que el cliente DHCP espera para reiniciar DHCP si la dirección IP asignada al cliente DHCP ya está en uso.</span><span class="sxs-lookup"><span data-stu-id="65553-243">**NX_DHCP_RESTART_WAIT** Defines the length of time the DHCP Client waits to restart DHCP if the IP address assigned to the DHCP Client is already in use.</span></span> <span data-ttu-id="65553-244">El valor predeterminado es 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="65553-244">The value is defaulted to 10 seconds.</span></span>

- <span data-ttu-id="65553-245">**NX_DHCP_CLIENT_MAX_RECORDS** Especifica el número máximo de registros de interfaz que se guardarán en la instancia del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-245">**NX_DHCP_CLIENT_MAX_RECORDS** Specifies the maximum number of interface records to save to the DHCP Client instance.</span></span> <span data-ttu-id="65553-246">Un registro de la interfaz de cliente DHCP es un registro del cliente DHCP que se ejecuta en una interfaz específica.</span><span class="sxs-lookup"><span data-stu-id="65553-246">A DHCP Client interface record is a record of the DHCP Client running on a specific interface.</span></span> <span data-ttu-id="65553-247">El valor predeterminado se establece en el recuento de interfaces físicas (NX_MAX_PHYSICAL_INTERFACES).</span><span class="sxs-lookup"><span data-stu-id="65553-247">The default value is set as physical interfaces count(NX_MAX_PHYSICAL_INTERFACES).</span></span>

- <span data-ttu-id="65553-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Si se define, permite que el cliente DHCP envíe la opción de tamaño máximo de mensaje DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Defined, this enables the DHCP Client to send maximum DHCP message size option.</span></span> <span data-ttu-id="65553-249">Esta opción está deshabilitada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="65553-249">By default, this option is disabled.</span></span>

- <span data-ttu-id="65553-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Si se define, permite que el cliente DHCP compruebe si los caracteres o la longitud son válidos en el nombre de host de entrada en la llamada a nx_dhcp_create.</span><span class="sxs-lookup"><span data-stu-id="65553-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Defined, this enables the DHCP Client to check the input host name in the nx_dhcp_create call for invalid characters or length.</span></span> <span data-ttu-id="65553-251">Esta opción está deshabilitada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="65553-251">By default, this option is disabled.</span></span>

- <span data-ttu-id="65553-252">**NX_DHCP_THREAD_PRIORITY** Prioridad del subproceso DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-252">**NX_DHCP_THREAD_PRIORITY** Priority of the DHCP thread.</span></span> <span data-ttu-id="65553-253">De forma predeterminada, este valor especifica que el subproceso DHCP se ejecuta con la prioridad 3.</span><span class="sxs-lookup"><span data-stu-id="65553-253">By default, this value specifies that the DHCP thread runs at priority 3.</span></span>

- <span data-ttu-id="65553-254">**NX_DHCP_THREAD_STACK_SIZE** Tamaño de la pila de subprocesos DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-254">**NX_DHCP_THREAD_STACK_SIZE** Size of the DHCP thread stack.</span></span> <span data-ttu-id="65553-255">De forma predeterminada, el tamaño es 2048 bytes.</span><span class="sxs-lookup"><span data-stu-id="65553-255">By default, the size is 2048 bytes.</span></span>

- <span data-ttu-id="65553-256">**NX_DHCP_TIME_INTERVAL** Intervalo en segundos en el que se ejecuta la función de expiración del temporizador del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-256">**NX_DHCP_TIME_INTERVAL** Interval in seconds when the DHCP Client timer expiration function executes.</span></span> <span data-ttu-id="65553-257">Esta función actualiza todos los tiempos de espera del proceso DHCP, por ejemplo, si se deben retransmitir los mensajes o se debe cambiar el estado del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-257">This function updates all the timeouts in the DHCP process e.g. if messages should be retransmitted or DHCP Client state changed.</span></span> <span data-ttu-id="65553-258">De manera predeterminada, este valor es 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="65553-258">By default, this value is 1 second.</span></span>

- <span data-ttu-id="65553-259">**NX_DHCP_OPTIONS_BUFFER_SIZE** Tamaño del búfer de opciones DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-259">**NX_DHCP_OPTIONS_BUFFER_SIZE** Size of DHCP options buffer.</span></span> <span data-ttu-id="65553-260">De manera predeterminada, este valor es 312.</span><span class="sxs-lookup"><span data-stu-id="65553-260">By default, this value is 312.</span></span>

- <span data-ttu-id="65553-261">**NX_DHCP_PACKET_PAYLOAD** Especifica el tamaño en bytes de la carga del paquete de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-261">**NX_DHCP_PACKET_PAYLOAD** Specifies the size in bytes of the DHCP Client packet payload.</span></span> <span data-ttu-id="65553-262">El valor predeterminado es NX_DHCP_MINIMUM_IP_DATAGRAM más el tamaño del encabezado físico.</span><span class="sxs-lookup"><span data-stu-id="65553-262">The default value is NX_DHCP_MINIMUM_IP_DATAGRAM + physical header size.</span></span> <span data-ttu-id="65553-263">Normalmente, el tamaño del encabezado físico en una red de conexión por cable es el tamaño del marco de Ethernet.</span><span class="sxs-lookup"><span data-stu-id="65553-263">The physical header size in a wireline network is usually the Ethernet frame size.</span></span>

- <span data-ttu-id="65553-264">**NX_DHCP_PACKET_POOL_SIZE** Especifica el tamaño del grupo de paquetes del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-264">**NX_DHCP_PACKET_POOL_SIZE** Specifies the size of the DHCP Client packet pool.</span></span> <span data-ttu-id="65553-265">El valor predeterminado es (5 \* NX_DHCP_PACKET_PAYLOAD) que proporcionará cuatro paquetes más espacio para la sobrecarga interna del grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="65553-265">The default value is (5 \*NX_DHCP_PACKET_PAYLOAD) which will provide four packets plus room for internal packet pool overhead.</span></span>

- <span data-ttu-id="65553-266">**NX_DHCP_MIN_RETRANS_TIMEOUT** Especifica la opción de espera mínima para recibir una respuesta del servidor DHCP al mensaje del cliente antes de retransmitir el mensaje.</span><span class="sxs-lookup"><span data-stu-id="65553-266">**NX_DHCP_MIN_RETRANS_TIMEOUT** Specifies the minimum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="65553-267">El valor predeterminado son los 4 segundos recomendados por el RFC 2131.</span><span class="sxs-lookup"><span data-stu-id="65553-267">The default value is the RFC 2131 recommended 4 seconds.</span></span>

- <span data-ttu-id="65553-268">**NX_DHCP_MAX_RETRANS_TIMEOUT** Especifica la opción de espera máxima para recibir una respuesta del servidor DHCP al mensaje del cliente antes de retransmitir el mensaje.</span><span class="sxs-lookup"><span data-stu-id="65553-268">**NX_DHCP_MAX_RETRANS_TIMEOUT** Specifies the maximum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="65553-269">El valor predeterminado son los 64 segundos recomendados por el RFC 2131.</span><span class="sxs-lookup"><span data-stu-id="65553-269">The default value is the RFC 2131 recommended 64 seconds.</span></span>

- <span data-ttu-id="65553-270">**NX_DHCP_MIN_RENEW_TIMEOUT** Especifica la opción de espera mínima para recibir un mensaje del servidor DHCP y enviar una solicitud de renovación una vez que el cliente DHCP esté enlazado a una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="65553-270">**NX_DHCP_MIN_RENEW_TIMEOUT** Specifies minimum wait option for receiving a DHCP Server message and sending a renewal request after the DHCP Client is bound to an IP address.</span></span> <span data-ttu-id="65553-271">El valor predeterminado es de 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="65553-271">The default value is 60 seconds.</span></span> <span data-ttu-id="65553-272">Sin embargo, el cliente DHCP utiliza los tiempos de expiración de renovación y reenlace del mensaje del servidor DHCP antes de tomar de manera predeterminada el tiempo de espera mínimo de renovación.</span><span class="sxs-lookup"><span data-stu-id="65553-272">However, the DHCP Client uses the Renew and Rebind expiration times from the DHCP server message before defaulting to the minimum renew timeout.</span></span>

- <span data-ttu-id="65553-273">**NX_DNS_TYPE_OF_SERVICE** Tipo de servicio necesario para las solicitudes UDP de DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-273">**NX_DHCP_TYPE_OF_SERVICE** Type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="65553-274">De forma predeterminada, este valor se define como NX_IP_NORMAL para el servicio de paquetes IP normal.</span><span class="sxs-lookup"><span data-stu-id="65553-274">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>

- <span data-ttu-id="65553-275">**NX_DHCP_FRAGMENT_OPTION** Habilitación de la fragmentación de solicitudes UDP de DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-275">**NX_DHCP_FRAGMENT_OPTION** Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="65553-276">De forma predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de UDP de DHCP.</span><span class="sxs-lookup"><span data-stu-id="65553-276">By default, this value is NX_DONT_FRAGMENT to disable DHCP UDP fragmenting.</span></span>

- <span data-ttu-id="65553-277">**NX_DNS_TIME_TO_LIVE** Especifica el número de enrutadores que un paquete puede pasar antes de que se descarte.</span><span class="sxs-lookup"><span data-stu-id="65553-277">**NX_DHCP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="65553-278">El valor predeterminado se define en 0x80.</span><span class="sxs-lookup"><span data-stu-id="65553-278">The default value is set to 0x80.</span></span>

- <span data-ttu-id="65553-279">**NX_DHCP_QUEUE_DEPTH** Especifica el número máximo de profundidad de la cola de recepción.</span><span class="sxs-lookup"><span data-stu-id="65553-279">**NX_DHCP_QUEUE_DEPTH** Specifies the number of maximum depth of receive queue.</span></span> <span data-ttu-id="65553-280">El valor predeterminado se establece en 4.</span><span class="sxs-lookup"><span data-stu-id="65553-280">The default value is set to 4.</span></span>
