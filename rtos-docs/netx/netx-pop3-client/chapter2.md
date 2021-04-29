---
title: 'Capítulo 2: Instalación y uso del cliente POP3 de Azure RTOS NetX'
description: El cliente POP3 de NetX incluye un archivo de origen, un archivo de encabezado y un archivo de demostración. Hay dos archivos adicionales para los servicios de síntesis MD5.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24de396c69d458866f9423fd995bcb8d905f29c8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815162"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a>Capítulo 2: Instalación y uso del cliente POP3 de Azure RTOS NetX

El cliente POP3 de NetX incluye un archivo de origen, un archivo de encabezado y un archivo de demostración. Hay dos archivos adicionales para los servicios de síntesis MD5. También hay un archivo PDF de guía de usuario (este documento).

- **nx_pop3_client.c**: archivo de código fuente de C para la API del cliente POP3 de NetX.
- **nx_pop3_client.h**: archivo de encabezado de C para la API del cliente POP3 de NetX.
- **demo_netxduo_pop3_client.c**: archivo de demostración para la creación de clientes POP3 e inicio de sesión.
- **nx_md5.c**: archivo de código fuente de C que define los servicios de síntesis MD5.
- **nx_md5.h**: archivo de encabezado de C que define los servicios de síntesis MD5.
- **nx_pop3_client.pdf**: guía de usuario del cliente POP3 de NetX.

Para usar el cliente de POP3 de NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX. Por ejemplo, si NetX está instalado en el directorio " *\threadx\mcf5272\green*", los archivos *nx_md5.h*, *nx_md5.c*, *nx_pop3_client.h, and nx_pop3_client.c* deben copiarse en este directorio.

## <a name="using-netx-pop3-client"></a>Uso del cliente POP3 de NetX

Para usar el servicio del cliente POP3 de NetX, la aplicación debe agregar *nx_pop3_client.c* a su proyecto de compilación. El código de la aplicación debe incluir *nx_md5.h, nx_pop3. h y nx_pop3_client.h* después de *tx_api.h* y *nx_api. h*, con el fin de usar ThreadX y NetX.

Estos archivos deben compilarse de la misma manera que otros archivos de aplicación y el código del objeto debe vincularse junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar el cliente de POP3 de NetX.

## <a name="small-example-of-the-netx-pop3-client"></a>Pequeño ejemplo del cliente POP3 de NetX

En la figura 1 que aparece a continuación se muestra un ejemplo de cómo usar los servicios del cliente de POP3 de NetX. En esta demostración se configuran las dos devoluciones de llamada para notificar la descarga de correo y la finalización de la sesión en las líneas 37 y 38. El grupo de paquetes del cliente de POP3 se crea en la línea 76. La tarea de subprocesos de IP se crea en la línea 88. Tenga en cuenta que este grupo de paquetes también se usa para el grupo de paquetes del cliente de POP3. TCP está habilitado en la tarea IP en la línea 107.

El cliente POP3 se crea en la línea 133 dentro de la función de entrada de subproceso de aplicación, *demo_thread_entry*. Esto se debe a que el servicio *nx_pop3_client_create* también intenta establecer una conexión TCP con el servidor de POP3. Si se realiza correctamente, la aplicación consulta al servidor de POP3 el número de elementos en su maildrop en la línea 149 utilizando el servicio *nx_pop3_client_mail_items_get*.

Si hay uno o más elementos, la aplicación recorre en iteración el bucle while de cada elemento de correo para descargar el mensaje de correo. La solicitud RETR se realiza en la línea 149 en la llamada *nx_pop3_client_mail_item_get*. Si se realiza correctamente, la aplicación descarga paquetes mediante el servicio *nx_pop3_client_mail_item_message_get* en la línea 177 hasta que detecta que se ha recibido el último paquete del mensaje en la línea 196. Por último, la aplicación elimina el elemento de correo, suponiendo que se ha producido una descarga correcta en la línea 199 de la llamada *nx_pop3_client_mail_item_delete*. RFC 1939 recomienda que los clientes de POP3 indiquen al servidor que elimine los elementos de correo descargados para evitar que el correo se acumule en el maildrop del cliente. De todos modos, el servidor puede hacerlo automáticamente.

Una vez que se descargan todos los elementos de correo, o si se produce un error en una llamada de servicio del cliente de POP3, la aplicación sale del bucle y elimina el cliente de POP3 en la línea 217 mediante el servicio *nx_pop3_client_delete*.

```c
/*
    demo_netxduo_pop3.c

    This is a small demo of POP3 Client on the NetX TCP/IP stack.
    This demo relies on Thread, NetX and POP3 Client API to conduct
    a POP3 mail session.
*/

#include "tx_api.h"
#include "nx_api.h"
#include "nx_pop3_client.h"

#define DEMO_STACK_SIZE        4096
#define CLIENT_ADDRESS         IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS         IP_ADDRESS(192,2,2,89)
#define SERVER_PORT            110

/* Replace the 'ram' driver with your own Ethernet driver. */
void _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client. */

TX_THREAD          demo_client_thread;
NX_POP3_CLIENT     demo_client;
NX_PACKET_POOL     client_packet_pool;
NX_IP              client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void     demo_thread_entry(ULONG info);

/* Shared secret is the same as password. */

#define LOCALHOST              "recipient@domain.com"
#define LOCALHOST_PASSWORD     "testpwd"

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *free_memory_pointer;

    /* Setup the working pointer. */
    free_memory_pointer = first_unused_memory;

    /* Create a client thread. */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                    free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer = free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* The demo client username and password is the authentication
    data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status = nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                        PAYLOAD_SIZE, free_memory_pointer, (PAYLOAD_SIZE * 10));
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
    free_memory_pointer = free_memory_pointer + 2048;

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

void demo_thread_entry(ULONG info)
{

UINT          status;
UINT          mail_item, number_mail_items;
UINT          bytes_downloaded = 0;
UINT          final_packet = NX_FALSE;
ULONG         total_size, mail_item_size, bytes_retrieved;
NX_PACKET     *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);

    /* Create a NetX POP3 Client instance with no byte or block memory pools.
    Note that it uses its password for its APOP shared secret. */
    status = nx_pop3_client_create(&demo_client,
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

    /* Find out how many items are in our mailbox. */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items, &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {
        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items. */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {

        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item, &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely downloaded. */

        while((final_packet == NX_FALSE) && (status == NX_SUCCESS))
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

    /* Delete the POP3 Client. This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

Figura 1. Ejemplo de una aplicación cliente POP3 de NetX

## <a name="pop3-client-configuration-options"></a>Opciones de configuración del cliente POP3

Hay varias opciones de configuración con el cliente de POP3 de NetX. A continuación, se muestra una lista de todas las opciones descritas de manera detallada:

- **NX_POP3_CLIENT_PACKET_TIMEOUT** Esto define la opción de espera en segundos para que el cliente de POP3 asigne un paquete. El valor predeterminado es 1 segundo.

- **NX_POP3_CLIENT_CONNECTION_TIMEOUT** Esto define la opción de espera en segundos para que el cliente de POP3 se conecte con el servidor de POP3. El valor predeterminado es 30 segundos.

- **NX_POP3_CLIENT_DISCONNECT_TIMEOUT** Esto define la opción de espera en segundos para que el cliente de POP3 se desconecte del servidor de POP3. El valor predeterminado es 2 segundos.

- **NX_POP3_TCP_SOCKET_SEND_WAIT** Esta opción establece la opción de espera en segundos en las llamadas al servicio *nx_tcp_socket_send*. El valor predeterminado es 2 segundos.

- **NX_POP3_SERVER_REPLY_TIMEOUT** Esta opción establece la opción de espera en las llamadas de servicio *nx_tcp_socket_receive* para la respuesta del servidor a una solicitud del cliente. El valor predeterminado es 10 segundos.

- **NX_POP3_CLIENT_TCP_WINDOW_SIZE** Esta opción establece el tamaño de la ventana de recepción de TCP del cliente. Debe establecerse el tamaño de MTU de la instancia IP menos el encabezado IP y TCP. El valor predeterminado es 1460.

- **NX_POP3_MAX_USERNAME** Esta opción establece el tamaño del búfer del nombre de usuario del cliente de POP3. El valor predeterminado es 40 bytes.

- **NX_POP3_MAX_PASSWORD** Esta opción establece el tamaño del búfer de la contraseña del cliente de POP3. El valor predeterminado es 20 bytes.