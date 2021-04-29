---
title: 'Capítulo 2: Instalación y uso del cliente SMTP de NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del cliente SMTP de NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86f324935ba32aab010b81f825be0a6564983a2e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814577"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a>Capítulo 2: Instalación y uso del cliente SMTP de NetX Duo

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del cliente SMTP de NetX Duo.

## <a name="netx-duo-smtp-client-installation"></a>Instalación del cliente SMTP de NetX Duo

El cliente SMTP de NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). El paquete incluye los siguientes archivos:

- **nxd_smtp_client.c**: archivo de código fuente en C para la API de cliente SMTP de NetX Duo
- **nxd_smtp_client.h**: archivo de encabezado en C para la API de cliente SMTP de NetX Duo
- **demo_netxduo_smtp_client.c**: demostración del cliente SMTP de NetX Duo
- **nxd_smtp_client.pdf** Guía del usuario para la API de cliente SMTP de NetX Duo

Para usar la API del cliente SMTP de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo. Por ejemplo, si NetX Duo se ha instalado en el directorio “c: *\myproject*”, los archivos *nxd_smtp_client.h y nxd_smtp_client.c* deben copiarse en este directorio.

## <a name="using-netx-duo-smtp-client"></a>Uso del cliente SMTP de NetX Duo

Para crear la aplicación cliente SMTP de NetX Duo, primero esta debe compilar las bibliotecas ThreadX y NetX Duo e incluirlas en el proyecto de compilación. A continuación, la aplicación debe incluir tx *_api.h* y *nx_api.h en el código fuente de la aplicación*. De este modo, se habilitarán los servicios ThreadX y NetX Duo. También debe incluir *nxd_smtp_client.c* y *nxd_smtp_client.h* después de *tx_api.h* y *nx_api.h para utilizar los servicios del cliente SMTP.*

Estos archivos deben compilarse de la misma manera que otros archivos de aplicación y el código del objeto debe vincularse junto con los archivos de la aplicación. Esto es todo lo que se necesita para crear una aplicación cliente SMTP de NetX Duo.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

En la figura 1 que aparece a continuación, se describe un ejemplo del uso del cliente SMTP de NetX Duo. El grupo de paquetes de la instancia de IP se crea con el servicio nx_packet_pool_create en la línea 68 y tiene una carga de paquetes muy pequeña. Esto se debe a que la instancia de IP solo envía paquetes de control que no requieren mucha carga. El grupo de paquetes de cliente SMTP creado en la línea 84 se utiliza para transmitir mensajes de cliente SMTP al servidor y los datos del mensaje. La carga de los paquetes es mucho mayor. La instancia de IP se crea en la línea 118 con el mismo grupo de paquetes. TCP, que es necesario para el protocolo SMTP, está habilitado en la instancia de IP en la línea 130.

En el subproceso de la aplicación, el cliente SMTP se crea con el servicio *nxd_smtp_client_create* en la línea 170. El servicio *nxd_smtp_client_create* admite conexiones de servidor SMTP IPv4 e IPv6, aunque este ejemplo está limitado a IPv4. A continuación, el mensaje de correo se envía al cliente SMTP para su transmisión en la línea 184 mediante el servicio *nx_smtp_mail_send*. Tenga en cuenta que la línea de asunto con el encabezado del contenido de correo se crea de forma independiente al cuerpo del mensaje. Tenga en cuenta también que la solicitud de envío de correo solo acepta una dirección de correo de destinatario que se supone que es sintácticamente correcta.

A continuación, la aplicación finaliza el cliente SMTP en la línea 200. El servicio *nx_smtp_client_delete* comprueba que la conexión del socket está cerrada y el puerto está desenlazado. Tenga en cuenta que la eliminación del grupo de paquetes depende de la aplicación cliente SMTP, en el caso de que esta ya no lo use.

```c
/*
   demo_netxduo_smtp_client.c

   This is a small demo of the NetX Duo SMTP Client on the high-performance NetX
   Duo TCP/IP stack.  This demo relies on Thread, NetX Duo and SMTP Client API to
   perform simple SMTP mail transfers in an SMTP client application to an SMTP mail
   server.   */

#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_smtp_client.h"


/* Define the host user name and mail box parameters */
#define USERNAME               "myusername"
#define PASSWORD               "mypassword"
#define FROM_ADDRESS           "my@mycompany.com"
#define RECIPIENT_ADDRESS      "your@yourcompany.com"
#define LOCAL_DOMAIN           "mycompany.com"

#define SUBJECT_LINE           "NetX Duo SMTP Client Demo"
#define MAIL_BODY              "NetX Duo SMTP client is an SMTP client \r\n" \
                               “implementation for embedded devices to send  \r\n" \
                               "email to SMTP servers. This feature is \r\n" \
                               "intended to allow a device to send simple \r\n " \
                               "status reports using the most universal \r\n " \
                               “Internet application, email.\r\n"

/* See the NetX Duo SMTP Client User Guide for how to set the authentication type.
   The most common authentication type is PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE 3


#define CLIENT_IP_ADDRESS  IP_ADDRESS(1,2,3,5)
#define SERVER_IP_ADDRESS  IP_ADDRESS(1,2,3,4)
#define SERVER_PORT        25


/* Define the NetX Duo and ThreadX structures for the SMTP client appliciation. */
NX_PACKET_POOL                  ip_packet_pool;
NX_PACKET_POOL                  client_packet_pool;
NX_IP                           client_ip;
TX_THREAD                       demo_client_thread;
static NX_SMTP_CLIENT           demo_client;


void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
void    demo_client_thread_entry(ULONG info);

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
    CHAR    *free_memory_pointer;


    /* Setup the pointer to unallocated memory.  */
    free_memory_pointer =  (CHAR *) first_unused_memory;

    /* Create IP default packet pool. */
    status =  nx_packet_pool_create(&ip_packet_pool, "Default IP Packet Pool",
                                    128, free_memory_pointer, 2048);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Create SMTP Client packet pool. This is only for transmitting packets to the
       server. It need not be a separate packet pool than the IP default packet pool
       but for more efficient resource use, we use two different packet pools
       because the CLient SMTP messages generally require more payload than IP
       control packets.

       Packet payload depends on the SMTP Client application requirements.  Size of
       packet payload must include IP and TCP headers. For IPv6 connections, IP and
       TCP header data is 60 bytes. For IPv4 IP and TCP header data is 40 bytes (not
       including TCP options). */
    status |=  nx_packet_pool_create(&client_packet_pool, "SMTP Client Packet Pool",
                                     800, free_memory_pointer, (10*800));

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (10*800);

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "client_thread",
                              demo_client_thread_entry, 0, free_memory_pointer,
                              2048, 16, 16,
                              TX_NO_TIME_SLICE, TX_DONT_START);

    if (status != NX_SUCCESS)
    {

        printf("Error creating Client thread. Status 0x%x\r\n", status);
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 4096;


    /* Create Client IP instance. Remember to replace the generic driver
       with a real ethernet driver to actually run this demo! */

    status = nx_ip_create(&client_ip, "SMTP Client IP Instance", CLIENT_IP_ADDRESS,
                          0xFFFFFF00UL, &ip_packet_pool, _nx_ram_network_driver,
                          free_memory_pointer, 2048, 1);


    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1040);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1040;

    /* Enable TCP for client. */
    status =  nx_tcp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable ICMP for client. */
    status =  nx_icmp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Start the client thread. */
    tx_thread_resume(&demo_client_thread);

    return;
}


/* Define the smtp application thread task.   */
void    demo_client_thread_entry(ULONG info)
{

    UINT        status;
    UINT        error_counter = 0;
    NXD_ADDRESS server_ip_address;


    tx_thread_sleep(100);

    /* Set up the server IP address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    status =  nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
                                     USERNAME,
                                     PASSWORD,
                                     FROM_ADDRESS,
                                     LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
                                     &server_ip_address, SERVER_PORT);

    if (status != NX_SUCCESS)
    {
        printf("Error creating the client. Status: 0x%x.\n\r", status);
        return;
    }

    /* Create a mail instance with the above text message and recipient info. */
    status =  nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
                                TP_MAIL_PRIORITY_NORMAL,
                                SUBJECT_LINE, MAIL_BODY, sizeof(MAIL_BODY) - 1);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        /* Mail item was not sent. Note that we need not delete the client. The
           error status may be a failed authentication check or a broken connection.
           We can simply call nx_smtp_mail_send again.  */
        error_counter++;
    }

    /* Release resources used by client. Note that the transmit packet
       pool must be deleted by the application if it no longer has use for it.*/
    status = nx_smtp_client_delete(&demo_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    return;
}
```

**Figura 1. Ejemplo de uso del cliente SMTP con NetX Duo**

## <a name="client-configuration-options"></a>Opciones de configuración del cliente

Hay varias opciones de configuración con la API del cliente SMTP de NetX Duo. A continuación, se muestra una lista de todas las opciones descritas de manera detallada:

- **NX_SMTP_CLIENT_TCP_WINDOW_SIZE**: esta opción establece el tamaño de la ventana de recepción de TCP del cliente. Debe establecerse en el tamaño de MTU del hardware de Ethernet subyacente y dejar espacio para los encabezados IP y TCP. El tamaño predeterminado de la ventana TCP del cliente SMTP de NetX Duo es 1460.
- **NX_SMTP_CLIENT_PACKET_TIMEOUT**: esta opción establece el tiempo de espera para la asignación de paquetes de NetX. El tiempo de espera predeterminado para los paquetes del cliente SMTP de NetX Duo es de 2 segundos.
- **NX_SMTP_CLIENT_CONNECTION_TIMEOUT**: esta opción establece el tiempo de espera de conexión del socket TCP del cliente. El tiempo de espera predeterminado para conectar el cliente SMTP de NetX Duo es de 10 segundos.
- **NX_SMTP_CLIENT_DISCONNECT_TIMEOUT**: esta opción establece el tiempo de espera de desconexión del socket TCP del cliente. El tiempo de espera predeterminado para desconectar el cliente SMTP de NetX Duo es de 5 segundos*. Tenga en cuenta que, si el cliente SMTP encuentra un error interno, como una conexión interrumpida, puede finalizar la conexión con un tiempo de espera de cero segundos.
- **NX_SMTP_GREETING_TIMEOUT**: esta opción establece el tiempo de espera para que el cliente reciba la respuesta del servidor a su saludo. El valor predeterminado del cliente SMTP de NetX Duo es de 10 segundos.
- **NX_SMTP_ENVELOPE_TIMEOUT**: esta opción establece el tiempo de espera para que el cliente reciba la respuesta del servidor a un comando que emitió. El valor predeterminado del cliente SMTP de NetX Duo es de 10 segundos.
- **NX_SMTP_MESSAGE_TIMEOUT**: esta opción establece el tiempo de espera para que el cliente reciba la respuesta del servidor para recibir los datos del mensaje de correo. El valor predeterminado del cliente SMTP de NetX Duo es de 30 segundos.
- **NX_SMTP_CLIENT_SEND_TIMEOUT**: esta opción define la opción de espera del búfer para almacenar la contraseña de usuario durante la autenticación SMTP con el servidor. El valor predeterminado es de 20 bytes.
- **NX_SMTP_SERVER_CHALLENGE_MAX_STRING**: esta opción define el tamaño del búfer para extraer el desafío del servidor durante la autenticación SMTP. El valor predeterminado es de 200 bytes. Para el inicio de sesión y la autenticación sin formato, el cliente SMTP puede utilizar probablemente un búfer más pequeño.
- **NX_SMTP_CLIENT_MAX_PASSWORD**: esta opción define el tamaño del búfer para almacenar la contraseña de usuario durante la autenticación SMTP con el servidor. El valor predeterminado es de 20 bytes. 
- **NX_SMTP_CLIENT_MAX_USERNAME**: esta opción define el tamaño del búfer para almacenar el nombre de usuario del host durante la autenticación SMTP con el servidor. El valor predeterminado es de 40 bytes. 
