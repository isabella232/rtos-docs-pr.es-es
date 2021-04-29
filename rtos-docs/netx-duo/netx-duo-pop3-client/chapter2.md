---
title: 'Capítulo 2: Instalación y uso del cliente POP3 de NetX Duo'
description: El cliente POP3 de NetX Duo incluye un archivo de origen, un archivo de encabezado y un archivo de demostración.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6ef4b6ba7aadf77ab95a4a12235eda847f32f3d5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814617"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-pop3-client"></a><span data-ttu-id="54ed5-103">Capítulo 2: Instalación y uso del cliente POP3 de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="54ed5-103">Chapter 2 - Installation and Use of NetX Duo POP3 Client</span></span>

<span data-ttu-id="54ed5-104">El cliente POP3 de NetX incluye un archivo de origen, un archivo de encabezado y un archivo de demostración.</span><span class="sxs-lookup"><span data-stu-id="54ed5-104">NetX POP3 Client includes one source file, one header file, and a demo file.</span></span> <span data-ttu-id="54ed5-105">Hay dos archivos adicionales para los servicios de síntesis de MD5.</span><span class="sxs-lookup"><span data-stu-id="54ed5-105">There are two additional files for MD5 digest services.</span></span> <span data-ttu-id="54ed5-106">También hay un archivo PDF de guía de usuario (este documento).</span><span class="sxs-lookup"><span data-stu-id="54ed5-106">There is also a User Guide PDF file (this document).</span></span>

- <span data-ttu-id="54ed5-107">**nxd_pop3_client. c** Archivo de código fuente de C para la API de cliente POP3 de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="54ed5-107">**nxd_pop3_client.c** C Source file for NetX Duo POP3 Client API</span></span>
- <span data-ttu-id="54ed5-108">**nxd_pop3_client. h** Archivo de encabezado de C para la API de cliente POP3 de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="54ed5-108">**nxd_pop3_client.h** C Header file for NetX Duo POP3 Client API</span></span>
- <span data-ttu-id="54ed5-109">**demo_netxduo_pop3_client.c** Archivo de demostración para la creación del cliente POP3 y el inicio de la sesión</span><span class="sxs-lookup"><span data-stu-id="54ed5-109">**demo_netxduo_pop3_client.c** Demo file for POP3 Client creation and session initiation</span></span>
- <span data-ttu-id="54ed5-110">**nx_md5. c** Archivo de origen de C que define los servicios de síntesis de MD5</span><span class="sxs-lookup"><span data-stu-id="54ed5-110">**nx_md5.c** C Source file defining MD5 digest services</span></span>
- <span data-ttu-id="54ed5-111">**nx_md5. h** Archivo de encabezado de C que define los servicios de síntesis de MD5</span><span class="sxs-lookup"><span data-stu-id="54ed5-111">**nx_md5.h** C Header file defining MD5 digest services</span></span>
- <span data-ttu-id="54ed5-112">**nxd_pop3_client.pdf** Guía de usuario del cliente POP3 de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="54ed5-112">**nxd_pop3_client.pdf** NetX Duo POP3 Client User Guide</span></span>

<span data-ttu-id="54ed5-113">Para usar el cliente POP3 de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="54ed5-113">To use NetX Duo POP3 Client, the entire distribution mentioned previously can be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="54ed5-114">Por ejemplo, si NetX Duo está instalado en el directorio " *\threadx\mcf5272\green*", los archivos *nx_md5.h*, *nx_md5.c,* *nxd_pop3_client.h y nxd_pop3_client.c* deben copiarse en este directorio.</span><span class="sxs-lookup"><span data-stu-id="54ed5-114">For example, if NetX Duo is installed in the directory “*\threadx\mcf5272\green*” then the *nx_md5.h*, *nx_md5.c,* *nxd_pop3_client.h, and nxd_pop3_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-pop3-client"></a><span data-ttu-id="54ed5-115">Uso del cliente POP3 de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="54ed5-115">Using NetX Duo POP3 Client</span></span>

<span data-ttu-id="54ed5-116">Para usar el servicio de cliente POP3 de NetX Duo, la aplicación debe agregar *nxd_pop3_client.c* a su proyecto de compilación.</span><span class="sxs-lookup"><span data-stu-id="54ed5-116">To use the NetX Duo POP3 Client service, the application must add *nxd_pop3_client.c* to its build project.</span></span> <span data-ttu-id="54ed5-117">El código de aplicación debe incluir *nx_md5.h, and nxd_pop3_client.h* después de *tx_api.h* y *nx_api.h* con el fin de usar ThreadX y NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="54ed5-117">The application code must include *nx_md5.h, and nxd_pop3_client.h* after *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo.</span></span>

<span data-ttu-id="54ed5-118">Estos archivos deben compilarse de la misma manera que otros archivos de aplicación y el código de objeto debe vincularse junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="54ed5-118">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="54ed5-119">Esto es todo lo que se necesita para usar el cliente POP3 de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="54ed5-119">This is all that is required to use the NetX Duo POP3 Client.</span></span>

## <a name="small-example-of-the-netx-duo-pop3-client"></a><span data-ttu-id="54ed5-120">Pequeño ejemplo del cliente POP3 de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="54ed5-120">Small Example of the NetX Duo POP3 Client</span></span>

<span data-ttu-id="54ed5-121">En la figura 1 que aparece a continuación se muestra un ejemplo de cómo usar los servicios del cliente POP3 de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="54ed5-121">An example of how to use NetX Duo POP3 Client services is described in Figure 1 that appears below.</span></span> <span data-ttu-id="54ed5-122">En esta demostración se configuran las dos devoluciones de llamada para notificar la descarga de correo y la finalización de la sesión en las líneas 37 y 38.</span><span class="sxs-lookup"><span data-stu-id="54ed5-122">This demo sets up the two callbacks for notification of mail download and session completion on lines 37 and 38.</span></span> <span data-ttu-id="54ed5-123">El grupo de paquetes del cliente POP3 se crea en la línea 76.</span><span class="sxs-lookup"><span data-stu-id="54ed5-123">The POP3 Client packet pool is created on line 76.</span></span> <span data-ttu-id="54ed5-124">La tarea de subprocesos de IP se crea en la línea 88.</span><span class="sxs-lookup"><span data-stu-id="54ed5-124">The IP thread task is created on line 88.</span></span> <span data-ttu-id="54ed5-125">Tenga en cuenta que este grupo de paquetes también se usa para el grupo de paquetes del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="54ed5-125">Note that this packet pool is also used for the POP3 Client packet pool.</span></span> <span data-ttu-id="54ed5-126">TCP está habilitado en la tarea IP en la línea 107.</span><span class="sxs-lookup"><span data-stu-id="54ed5-126">TCP is enabled on the IP task in line 107.</span></span>

<span data-ttu-id="54ed5-127">El cliente POP3 se crea en la línea 133 dentro de la función de entrada del subproceso de la aplicación, *demo_thread_entry*.</span><span class="sxs-lookup"><span data-stu-id="54ed5-127">The POP3 Client is created on line 133 inside the application thread entry function, *demo_thread_entry*.</span></span> <span data-ttu-id="54ed5-128">Esto se debe a que el servicio *nx_pop3_client_create* también intenta establecer una conexión TCP con el servidor de POP3.</span><span class="sxs-lookup"><span data-stu-id="54ed5-128">This is because the *nx_pop3_client_create* service also attempts to make a TCP connection with the POP3 server.</span></span> <span data-ttu-id="54ed5-129">Si se realiza correctamente, la aplicación consulta al servidor de POP3 el número de elementos en su maildrop en la línea 149 utilizando el servicio *nx_pop3_client_mail_items_get*.</span><span class="sxs-lookup"><span data-stu-id="54ed5-129">If successful, the application queries the POP3 server for the number of items in its maildrop on line 149 using the *nx_pop3_client_mail_items_get* service.</span></span>

<span data-ttu-id="54ed5-130">Si hay uno o más elementos, la aplicación recorre en iteración el bucle while de cada elemento de correo para descargar el mensaje de correo.</span><span class="sxs-lookup"><span data-stu-id="54ed5-130">If there are one or more items, the application iterates through the while loop for each mail item to download the mail message.</span></span> <span data-ttu-id="54ed5-131">La solicitud RETR se realiza en la línea 149 en la llamada *nx_pop3_client_mail_item_get*.</span><span class="sxs-lookup"><span data-stu-id="54ed5-131">The RETR request is made on line 149 in the *nx_pop3_client_mail_item_get* call.</span></span> <span data-ttu-id="54ed5-132">Si se realiza correctamente, la aplicación descarga paquetes mediante el servicio *nx_pop3_client_mail_item_message_get* en la línea 177 hasta que detecta que se ha recibido el último paquete del mensaje en la línea 196.</span><span class="sxs-lookup"><span data-stu-id="54ed5-132">If successful, the application downloads packets using the *nx_pop3_client_mail_item_message_get* service on line 177 till it detects the last packet in the message has been received on line 196.</span></span> <span data-ttu-id="54ed5-133">Por último, la aplicación elimina el elemento de correo, suponiendo que se ha producido una descarga correcta en la línea 199 de la llamada *nx_pop3_client_mail_item_delete*.</span><span class="sxs-lookup"><span data-stu-id="54ed5-133">Lastly, the application deletes the mail item, assuming a successful download has occurred on line 199 in *the nx_pop3_client_mail_item_delete* call.</span></span> <span data-ttu-id="54ed5-134">La RFC 1939 recomienda que los clientes de POP3 indiquen al servidor que elimine los elementos de correo descargados para evitar que el correo se acumule en el maildrop del cliente.</span><span class="sxs-lookup"><span data-stu-id="54ed5-134">The RFC 1939 recommends that POP3 Clients instruct the Server to delete downloaded mail items to prevent mail accumulating in the Client’s maildrop.</span></span> <span data-ttu-id="54ed5-135">De todos modos, el servidor puede hacerlo automáticamente.</span><span class="sxs-lookup"><span data-stu-id="54ed5-135">The Server may automatically do so anyway.</span></span>

<span data-ttu-id="54ed5-136">Una vez que se descargan todos los elementos de correo, o si se produce un error en una llamada de servicio del cliente POP3, la aplicación sale del bucle y elimina el cliente POP3 en la línea 217 mediante el servicio *nx_pop3_client_delete*.</span><span class="sxs-lookup"><span data-stu-id="54ed5-136">Once all the mail items are downloaded, or if a POP3 Client service call fails, the application exits of the loop and deletes the POP3 Client on line 217 using the *nx_pop3_client_delete* service.</span></span>

```C
/*
   demo_netxduo_pop3.c

   This is a small demo of POP3 Client on the NetX Duo TCP/IP stack.
   This demo relies on Thread, NetX Duo and POP3 Client API to conduct
   a POP3 mail session.
 */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_pop3_client.h"

#define DEMO_STACK_SIZE             4096
#define CLIENT_ADDRESS              IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS              IP_ADDRESS(192,2,2,89)
#define SERVER_PORT                 110

/* Replace the 'ram' driver with your own Ethernet driver. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client.  */

TX_THREAD           demo_client_thread;
NX_POP3_CLIENT      demo_client;
NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void    demo_thread_entry(ULONG info);


  /* Shared secret is the same as password. */

#define LOCALHOST                               "recipient@domain.com"
#define LOCALHOST_PASSWORD                      "testpwd"

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    UINT     status;
    UCHAR    *free_memory_pointer;


    /* Setup the working pointer.  */
    free_memory_pointer =  first_unused_memory;

    /* Create a client thread.  */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                     free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                     TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer =  free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                                    PAYLOAD_SIZE, free_memory_pointer,
                                    (PAYLOAD_SIZE * 10));
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (PAYLOAD_SIZE * 10);


    /* Create IP instance for demo Client */
    status = nx_ip_create(&client_ip, "POP3 Client IP Instance",
                          CLIENT_ADDRESS, 0xFFFFFF00UL, &client_packet_pool,
                          _nx_ram_network_driver, free_memory_pointer,
                          2048, 1);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1024);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1024;

    /* Enable TCP and ICMP for Client IP. */
    nx_tcp_enable(&client_ip);
    nx_icmp_enable(&client_ip);

    return;
}



/* Define the application thread entry function. */

void    demo_thread_entry(ULONG info)
{

    UINT        status;
    UINT        mail_item, number_mail_items;
    UINT        bytes_downloaded = 0;
    UINT        final_packet = NX_FALSE;
    ULONG       total_size, mail_item_size, bytes_retrieved;
    NX_PACKET   *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);


    /* Create a NetX POP3 Client instance with no byte or block memory pools.
       Note that it uses its password for its APOP shared secret. */
    status =  nx_pop3_client_create(&demo_client,
                                    NX_TRUE,
                                    &client_ip, &client_packet_pool, SERVER_ADDRESS,
                                    SERVER_PORT, LOCALHOST, LOCALHOST_PASSWORD);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        status = nx_pop3_client_delete(&demo_client);

        /* Abort. */
        return;
    }

    /* Find out how many items are in our mailbox.  */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items,
                                            &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {

        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items.  */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {


        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item,
                                               &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely
           downloaded. */
        while((final_packet ==  NX_FALSE) && (status == NX_SUCCESS))
        {

            status = nx_pop3_client_mail_item_message_get(&demo_client, &packet_ptr,
                                                        &bytes_retrieved,
                                                        &final_packet);

            if (status != NX_SUCCESS)
            {

                break;
            }

            if (bytes_retrieved != 0)
            {

                printf("Received %d bytes of data for item %d: %s\n",
                        packet_ptr -> nx_packet_length,
                        mail_item, packet_ptr -> nx_packet_prepend_ptr);
            }

            nx_packet_release(packet_ptr);

            /* Determine if this is the last data packet. */
            if (final_packet)
            {
                /* It is. Let the server know it can delete this mail item. */
                status = nx_pop3_client_mail_item_delete(&demo_client, mail_item);
            }

            /* Keep track of how much mail message data is left. */
            bytes_downloaded += bytes_retrieved;
        }

        /* Get the next mail item. */
        mail_item++;

        tx_thread_sleep(100);

    }

    /* Disconnect from the POP3 server. */
    status = nx_pop3_client_quit(&demo_client);

    /* Delete the POP3 Client.  This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

<span data-ttu-id="54ed5-137">**Figura 1. Ejemplo de una aplicación cliente POP3 de NetX Duo**</span><span class="sxs-lookup"><span data-stu-id="54ed5-137">**Figure 1. Example of a NetX Duo POP3 Client application**</span></span>

## <a name="pop3-client-configuration-options"></a><span data-ttu-id="54ed5-138">Opciones de configuración del cliente POP3</span><span class="sxs-lookup"><span data-stu-id="54ed5-138">POP3 Client Configuration Options</span></span>

<span data-ttu-id="54ed5-139">Hay varias opciones de configuración con el cliente POP3 de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="54ed5-139">There are several configuration options with the NetX Duo POP3 Client.</span></span> <span data-ttu-id="54ed5-140">A continuación, se muestra una lista de todas las opciones descritas de manera detallada:</span><span class="sxs-lookup"><span data-stu-id="54ed5-140">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="54ed5-141">**NX_POP3_CLIENT_PACKET_TIMEOUT** Esto define la opción de espera en segundos para que el cliente POP3 asigne un paquete.</span><span class="sxs-lookup"><span data-stu-id="54ed5-141">**NX_POP3_CLIENT_PACKET_TIMEOUT** This defines the wait option in seconds for the POP3 Client to allocate a packet.</span></span> <span data-ttu-id="54ed5-142">El valor predeterminado es 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="54ed5-142">The default value is 1 second.</span></span>
- <span data-ttu-id="54ed5-143">**NX_POP3_CLIENT_CONNECTION_TIMEOUT** Esto define la opción de espera en segundos para que el cliente POP3 se conecte con el servidor de POP3.</span><span class="sxs-lookup"><span data-stu-id="54ed5-143">**NX_POP3_CLIENT_CONNECTION_TIMEOUT** This defines the wait option in seconds for the POP3 Client to connect with the POP3 Server.</span></span> <span data-ttu-id="54ed5-144">El valor predeterminado es 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="54ed5-144">The default value is 30 seconds.</span></span>
- <span data-ttu-id="54ed5-145">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT** Esto define la opción de espera en segundos para que el cliente POP3 se desconecte del servidor de POP3.</span><span class="sxs-lookup"><span data-stu-id="54ed5-145">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT** This defines the wait option in seconds for the POP3 Client to disconnect from the POP3 Server.</span></span> <span data-ttu-id="54ed5-146">El valor predeterminado es 2 segundos.</span><span class="sxs-lookup"><span data-stu-id="54ed5-146">The default value is 2 seconds.</span></span>
- <span data-ttu-id="54ed5-147">**NX_POP3_TCP_SOCKET_SEND_WAIT** Esta opción establece la opción de espera en segundos en las llamadas al servicio *nx_tcp_socket_send*.</span><span class="sxs-lookup"><span data-stu-id="54ed5-147">**NX_POP3_TCP_SOCKET_SEND_WAIT** This option sets the wait option in seconds in *nx_tcp_socket_send* service calls.</span></span> <span data-ttu-id="54ed5-148">El valor predeterminado es 2 segundos.</span><span class="sxs-lookup"><span data-stu-id="54ed5-148">The default value is 2 seconds.</span></span>
- <span data-ttu-id="54ed5-149">**NX_POP3_SERVER_REPLY_TIMEOUT** Esta opción establece la opción de espera en las llamadas de servicio *nx_tcp_socket_receive* para la respuesta del servidor a una solicitud del cliente.</span><span class="sxs-lookup"><span data-stu-id="54ed5-149">**NX_POP3_SERVER_REPLY_TIMEOUT** This option sets the wait option in *nx_tcp_socket_receive* service calls for the Server reply to a Client request.</span></span> <span data-ttu-id="54ed5-150">El valor predeterminado es 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="54ed5-150">The default value is 10 seconds.</span></span>
- <span data-ttu-id="54ed5-151">**NX_POP3_CLIENT_TCP_WINDOW_SIZE** Esta opción establece el tamaño de la ventana de recepción de TCP del cliente.</span><span class="sxs-lookup"><span data-stu-id="54ed5-151">**NX_POP3_CLIENT_TCP_WINDOW_SIZE** This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="54ed5-152">Debe establecerse el tamaño de MTU de la instancia IP menos el encabezado IP y TCP.</span><span class="sxs-lookup"><span data-stu-id="54ed5-152">This should be set to the IP instance MTU size minus the IP and TCP header.</span></span> <span data-ttu-id="54ed5-153">El valor predeterminado es 1460.</span><span class="sxs-lookup"><span data-stu-id="54ed5-153">The default value is 1460.</span></span> <span data-ttu-id="54ed5-154">Debe ser menor si la aplicación envía paquetes de POP3 a través de IPv6 (1440 bytes) para tener en cuenta el encabezado IPv6 más grande.</span><span class="sxs-lookup"><span data-stu-id="54ed5-154">This should be less if the application is sending POP3 packets over IPv6 (1440 bytes) to account for the larger IPv6 header.</span></span>
- <span data-ttu-id="54ed5-155">**NX_POP3_MAX_USERNAME** Esta opción establece el tamaño del búfer del nombre de usuario del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="54ed5-155">**NX_POP3_MAX_USERNAME** This option sets the size of the buffer of the POP3 Client user name.</span></span> <span data-ttu-id="54ed5-156">El valor predeterminado es 40 bytes.</span><span class="sxs-lookup"><span data-stu-id="54ed5-156">The default value is 40 bytes.</span></span>
- <span data-ttu-id="54ed5-157">**NX_POP3_MAX_PASSWORD** Esta opción establece el tamaño del búfer de la contraseña del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="54ed5-157">**NX_POP3_MAX_PASSWORD** This option sets the size of the buffer of the POP3 Client password.</span></span> <span data-ttu-id="54ed5-158">El valor predeterminado es 20 bytes.</span><span class="sxs-lookup"><span data-stu-id="54ed5-158">The default value is 20 bytes.</span></span>
