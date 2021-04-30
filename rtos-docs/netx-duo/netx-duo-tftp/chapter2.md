---
title: 'Capítulo 2: Instalación y uso de TFTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente TFTP de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ffb0c433bf1a5665e07da3cc6c240f1d0d8c87d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815385"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-tftp"></a>Capítulo 2: Instalación y uso de TFTP de Azure RTOS NetX Duo

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente TFTP de Azure RTOS NetX Duo.

## <a name="product-distribution"></a>Distribución del producto

Azure RTOS NetX Duo se puede obtener desde nuestro repositorio de código fuente público en https://github.com/azure-rtos/netxduo/. El paquete incluye los siguientes archivos:


- **nxd_tftp_client.h**: archivo de encabezado del cliente TFTP de NetX Duo

- **nxd_tftp_client.c**: archivo de código fuente C del cliente TFTP de NetX Duo

- **nxd_tftp_server.h**: archivo de encabezado del servidor TFTP de NetX Duo

- **nxd_tftp_server.c**: archivo de código fuente C del servidor TFTP de NetX Duo

- **filex_stub.h**: archivo de código auxiliar si FileX no está presente

- **nxd_tftp.pdf**: descripción en PDF de NetX Duo TFTP

- **demo_netxduo_tftp.c**: demostración de NetX Duo TFTP

## <a name="tftp-installation"></a>Instalación de TFTP

Para usar el cliente NetX Duo TFTP, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo. Por ejemplo, si NetX Duo está instalado en el directorio “ *\threadx\arm7\green*”, los archivos *nxd_tftp_client.h*, *nxd_tftp_client.c*, *nxd_tftp_server.h* y *nxd_tftp_server.c* podrían copiarse en ese mismo directorio.

## <a name="using-tftp"></a>Uso de TFTP

Para ejecutar una aplicación TFTP, el código de la aplicación debe incluir *nxd_tftp_client.h* o nxd_tftp_server.h después de incluir *tx_api.h, fx_api.h* y *nx_api.h*, con el fin de usar ThreadX, FileX y NetX Duo, respectivamente. El proyecto de aplicación también debe incluir *nxd_tftp_client.c* o *nxd_tftp_server.c* en el proceso de compilación. Estos archivos se deben compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar NetX Duo TFTP. Una vez incluidos *los archivos de encabezado*, el código de aplicación puede usar los servicios TFTP.

> [!NOTE]
> Como TFTP usa los servicios de UDP de NetX Duo, debe habilitarse UDP con la llamada a *nx_udp_enable* antes de utilizar TFTP.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

Un ejemplo de lo fácil que es usar NetX Duo TFTP se describe en la figura 1.1 que aparece a continuación. En este ejemplo, los archivos de inclusión de TFTP *nxd_tftp_client.h* y *nxd_tftp_server.h* se incluyen en las líneas 19 y 20. A continuación, el servidor TFTP se crea en "*tx_application_define*" en la línea 179. 

> [!NOTE]
> El bloque de control de servidor TFTP "*server*" se definió anteriormente como una variable global en la línea 45. En esta demostración se elige el uso de IPv4 para su comunicación de TFTP en la línea 14. Después de la creación correcta, se inicia un servidor TFTP en la línea 304. En la línea 411 se crea el cliente TFTP. Y, por último, el cliente escribe el archivo en la línea 450 y vuelve a leer el archivo en la línea 485.

La tarea de subproceso de servidor TFTP se detiene y el servidor TFTP se elimina en la línea 324. La aplicación debe llamar a fx_media_close (línea 331) para cerrar todos los archivos y actualizar los datos de archivos y directorios en el medio USB.

> [!NOTE]
> En este ejemplo se usa FileX para el control de servidor TFTP de recepción y descarga de solicitudes de archivos de cliente TFTP. Sin embargo, si se define NX_TFTP_NO_FILEX, la aplicación puede incluir file_stub.h en lugar de fx_api.h.
>
> Además, observe que las aplicaciones de servidor y cliente TFTP de NetX existentes funcionarán con NetX Duo TFTP. Sin embargo, se recomienda que el desarrollador de la aplicación porte sus aplicaciones TFTP de NetX a NetX Duo. Los servicios equivalentes de TFTP de NetX son:

- *nxd_tftp_server_start*

- *nxd_tftp_server_stop*

- *nxd_tftp_client_file_read*

- *nxd_tftp_client_file_write*

- *nxd_tftp_client_file_open*

```C
/* This is a small demo of TFTP on the high-performance NetX TCP/IP stack. This demo
   relies on ThreadX and NetX Duo, to show a simple file transfer from the client
   and then back to the server. */



/* Indicate if using IPv6. */
#define USE_DUO

/* If the host application is using NetX Duo, determine which IP version to use.
   Make sure IPv6 in NetX Duo is enabled if planning to use TFTP over IPv6 */
#ifdef USE_DUO
#define     IP_TYPE     6
#endif /* USE_DUO        */

#include    "tx_api.h"
#include    "nx_api.h"
#include    "nxd_tftp_client.h"
#include    "nxd_tftp_server.h"
#ifndef     NX_TFTP_NO_FILEX
#include    "fx_api.h"
#endif


#define     DEMO_STACK_SIZE         4096

/* To use another file storage utility define this symbol:
#define NX_TFTP_NO_FILEX
*/

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;

/* Define the NetX TFTP object control blocks. */

NX_TFTP_CLIENT          client;
NX_TFTP_SERVER          server;

/* Define the application global variables */

#define                 CLIENT_ADDRESS  IP_ADDRESS(1, 2, 3, 5)
#define                 SERVER_ADDRESS  IP_ADDRESS(1, 2, 3, 4)

NXD_ADDRESS             server_ip_address;
NXD_ADDRESS             client_ip_address;

UINT                    error_counter = 0;

/* Define buffer used in the demo application. */
UCHAR                   buffer[255];
ULONG                   data_length;


/* Define the memory area for the FileX RAM disk. */
#ifndef NX_TFTP_NO_FILEX
UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];
#endif


/* Define function prototypes. */

VOID    _fx_ram_driver(FX_MEDIA *media_ptr);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
void    client_thread_entry(ULONG thread_input);
void    server_thread_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;
UCHAR   *pointer;


    /* Setup the working pointer. */
    pointer =  (UCHAR *) first_unused_memory;


    /* Create the main TFTP server thread. */
    status = tx_thread_create(&server_thread, "TFTP Server Thread", server_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              4,4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the main TFTP client thread at a slightly lower priority. */
    status = tx_thread_create(&client_thread, "TFTP Client Thread", client_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              5, 5, TX_NO_TIME_SLICE, TX_DONT_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&server_pool, "TFTP Server Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the TFTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&server_ip);

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the TFTP server. */
#ifdef USE_DUO
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
    /* Specify the tftp server global address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x102;
#endif
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_ADDRESS;

#endif

    status =  nxd_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#else
    status =  nx_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#endif

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for errors for the server. */
    if (status)
        error_counter++;

    /* Create a packet pool for the TFTP client. */

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&client_pool, "TFTP Client Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the TFTP client. */
    status = nx_ip_create(&client_ip, "TFTP Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable UDP for client IP instance. */
    status |=  nx_udp_enable(&client_ip);
    status |= nx_icmp_enable(&client_ip);

    tx_thread_resume(&client_thread);
}

void server_thread_entry(ULONG thread_input)
{

UINT        status, running;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#ifndef  NX_TFTP_NO_FILEX

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry             */
                            ram_disk_memory,                 /* RAM disk memory pointer  */
                            ram_disk_sector_cache,           /* Media buffer pointer     */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size        */
                            "MY_RAM_DISK",                   /* Volume Name              */
                            1,                               /* Number of FATs           */
                            32,                              /* Directory Entries        */
                            0,                               /* Hidden sectors           */
                            256,                            /* Total sectors            */
                            128,                             /* Sector size              */
                            1,                               /* Sectors per cluster      */
                            1,                               /* Heads                    */
                            1);                              /* Sectors per track        */

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory, ram_disk_sector_cache,
                               sizeof(ram_disk_sector_cache));

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

#endif /*  NX_TFTP_NO_FILEX */

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ICMPv6 services. */
    status |= nxd_icmp_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the server. */
    status = nxd_ipv6_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for DAD to validate the address. */
    tx_thread_sleep(500);
#endif

#endif /* IP_TYPE == 6 */

    /* Start the NetX TFTP server. */
#ifdef USE_DUO
    status =  nxd_tftp_server_start(&server);
#else
    status =  nx_tftp_server_start(&server);
#endif

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Run for a while */
    running = NX_TRUE;
    while(running)
        tx_thread_sleep(200);


    /* Stop and delete the TFTP server. */
#ifdef USE_DUO
    nxd_tftp_server_delete(&server);
#else
    nx_tftp_server_delete(&server);
#endif

    /* Close all open files and ensure directory information is also written out to the media.
    This will also flush the file data to USB media*/
    status = fx_media_close(&ram_disk);

    if (status)
    {
        error_counter++;
    }

    return;

}


/* Define the TFTP client thread. */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
UINT        all_done = NX_FALSE;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ECMPv6 services for the client. */
    status = nxd_icmp_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the client. */
    status = nxd_ipv6_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the Client IPv6 address */
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_address.v6[1] = 0xf101;
    client_ip_address.nxd_ip_address.v6[2] = 0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for the link local and global addresses to be validated. */
    tx_thread_sleep(500);
#endif
#endif /*(IP_TYPE == 6) */


    /* The TFTP services used below include the NetX equivalent service which will work with
       NetX Duo TFTP. However, it is recommended for developers to port their applications
       to the newer services that take the NXD_ADDRESS type and support both IPv4 and IPv6
       communication.
    */

    /* Create a TFTP client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool, IP_TYPE);
#else
    status =  nx_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool);
#endif

    /* Check status. */
    if (status)
        return;

    /* Open a TFTP file for writing. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_WRITE, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_WRITE, 100);
#endif

    /* Check status. */
    if (status)
        return;

    /* Allocate a TFTP packet. */
#ifdef USE_DUO
    status =  nxd_tftp_client_packet_allocate(&client_pool, &my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_packet_allocate(&client_pool, &my_packet, 100);
#endif
    /* Check status. */
    if (status)
        error_counter++;

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write this packet to the file via TFTP. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_write(&client, my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_write(&client, my_packet, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Close this file. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Open the same file for reading. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_READ, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_READ, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;
    do
    {

    /* Read the file back. */
#ifdef USE_DUO
        status =  nxd_tftp_client_file_read(&client, &my_packet, 100, IP_TYPE);
#else
        status =  nx_tftp_client_file_read(&client, &my_packet, 100);
#endif
        /* Check for retranmission/dropped packet error. Benign. Try again... */
        if (status == NX_TFTP_INVALID_BLOCK_NUMBER)
        {

            continue;
        }
        else if (status == NX_TFTP_END_OF_FILE)
        {

            /* All done. */
            all_done = NX_TRUE;
        }
        else if (status != NX_SUCCESS)
        {

            /* Internal error, invalid packet or error on read. */
            break;
        }


        /* Do something with the packet data and release when done. */
        nx_packet_data_retrieve(my_packet, buffer, &data_length);
        buffer[data_length] = 0;
        printf("Receive data: %s\n", buffer);

        printf("release packet in demo.\n");

        nx_packet_release(my_packet);

    } while (all_done == NX_FALSE);

    /* Close the file again. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Delete the client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_delete(&client);
#else
    status =  nx_tftp_client_delete(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    return;
}
```

Figura 1.1 Ejemplo de uso de TFTP con NetX Duo

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar NetX Duo TFTP. En la lista siguiente se describe cada una de forma detallada. A menos que se especifique lo contrario, estas opciones se encuentran en *nxd_tftp_client.h* y *nxd_tftp_server.h*.


- **NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica de TFTP. Normalmente se utiliza después de depurar la aplicación.

- **NX_TFTP_SERVER_PRIORITY**: prioridad del subproceso del servidor TFTP. De forma predeterminada, este valor se define como 16 para especificar la prioridad 16.

- **NX_TFTP_SERVER_TIME_SLICE**: la porción de tiempo para que el servidor TFTP se ejecute antes de suspender otros subprocesos con la misma prioridad. El valor predeterminado es 2.

- **NX_TFTP_MAX_CLIENTS**: número máximo de clientes que el servidor puede controlar al mismo tiempo. De forma predeterminada, este valor es 10 para admitir 10 clientes a la vez.

- **NX_TFTP_ERROR_STRING_MAX**: número máximo de caracteres de la cadena de error. De manera predeterminada, este valor es 64.

- **NX_TFTP_NO_FILEX**: si está definida, esta opción proporciona un código auxiliar para las dependencias de FileX. El cliente TFTP funcionará sin ningún cambio si se define esta opción. El servidor TFTP tendrá que modificarse o el usuario tendrá que crear unos cuantos servicios de FileX para que funcionen correctamente.

- **NX_TFTP_TYPE_OF_SERVICE**: tipo de servicio necesario para las solicitudes UDP de TFTP. De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal.

- **NX_TFTP_FRAGMENT_OPTION**: habilita los fragmentos para solicitudes UDP de TFTP. De forma predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de UDP de TFTP.

- **NX_TFTP_TIME_TO_LIVE**: especifica el número de enrutadores que un paquete puede pasar antes de que se descarte. El valor predeterminado se define en 0x80.

- **NX_TFTP_SOURCE_PORT**: esta opción permite a una aplicación cliente de TFTP especificar el puerto de socket UDP del cliente TFTP. Su valor predeterminado es NX_ANY_PORT.

- ***NX_TFTP_SERVER_RETRANSMIT_ENABLE***: permite que el temporizador del servidor TFTP compruebe cada sesión de cliente TFTP para verificar las actividades recientes (ya sea ACK o un paquete de datos). Cuando el tiempo de espera de la sesión expira después del número máximo de veces, se supone que se ha perdido la conexión. El servidor borra la solicitud de cliente, cierra todos los archivos abiertos y hace que la solicitud de conexión esté disponible para el siguiente cliente. De forma predeterminada está deshabilitado.

- **NX_TFTP_SERVER_TIMEOUT_PERIOD**: especifica el intervalo en el que la función de entrada del temporizador del servidor TFTP comprueba las conexiones de cliente para recibir los paquetes. El valor predeterminado es 20 (tics del temporizador).

- **NX_TFTP_SERVER_RETRANSMIT_TIMEOUT**: este es el tiempo de espera para recibir un paquete de datos o ACK válido del cliente. El valor predeterminado es 200 (tics del temporizador) *.*

- **NX_TFTP_SERVER_MAX_RETRIES**: especifica el número máximo de veces que se renueva el tiempo de espera de retransmisión de la sesión de cliente. A partir de ese momento, el servidor cierra la sesión.

- **NX_TFTP_MAX_CLIENT_RETRANSMITS**: especifica el número máximo de veces que el servidor recibe un paquete de datos o un ACK duplicado del cliente (que se anula) sin enviar un mensaje de error al cliente y cerrando la sesión. No tiene ningún efecto si se define NX_TFTP_SERVER_RETRANSMIT_ENABLE.
