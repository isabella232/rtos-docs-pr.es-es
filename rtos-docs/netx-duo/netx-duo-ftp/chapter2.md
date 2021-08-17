---
title: 'Capítulo 2: Instalación y uso de FTP'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de los servicios FTP de NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bef7dcce9354e6653dd92c5a47a29d120268faeb4a30b4d146c9e10d2d69084e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790231"
---
# <a name="chapter-2---installation-and-use-of-ftp"></a>Capítulo 2: Instalación y uso de FTP

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de los servicios FTP de NetX Duo.

## <a name="product-distribution"></a>Distribución del producto

FTP de NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:

- **nxd_tftp_client.h**: archivo de encabezado del cliente FTP de NetX Duo
- **nxd_ftp_client.c**: archivo de código fuente de C del cliente FTP de NetX Duo
- **nxd_ftp_server.h**: archivo de encabezado del servidor FTP de NetX Duo
- **nxd_ftp_server.c**: archivo de código fuente de C del servidor FTP de NetX Duo
- **filex_stub.h**: archivo de código auxiliar si FileX no está presente
- **nxd_ftp.pdf**: descripción en PDF de FTP para NetX
- **demo_netxduo_ftp.c**: sistema de demostración de FTP

## <a name="netx-duo-ftp-installation"></a>Instalación de FTP de NetX Duo

Para usar la API de FTP de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo. Por ejemplo, si NetX Duo se instala en el directorio “ *\threadx\arm7\green*”, entonces los archivos *nxd_ftp_client.h* y *nxd_ftp_client.c* se deben copiar en este directorio para las aplicaciones de cliente FTP, y los archivos *nxd_ftp_server.h* y *nxd_ftp_server.c* se deben copiar en este directorio para las aplicaciones de servidor FTP.

## <a name="using-netx-duo-ftp"></a>Uso de FTP de NetX Duo

El uso de la API de FTP de NetX Duo es fácil. Básicamente, el código de aplicación debe incluir el archivo *nxd_ftp_client.h* para las aplicaciones de cliente FTP o el archivo *nxd_ftp_server* para las aplicaciones de servidor FTP, después de incluir *tx_api.h, fx_api.h* y *nx_api.h*, con el fin de usar ThreadX, FileX y NetX Duo, respectivamente. El proyecto de compilación debe incluir el código fuente FTP y el archivo de aplicación host y, por supuesto, los archivos de biblioteca de ThreadX y NetX. Esto es todo lo que se necesita para usar FTP de NetX Duo.

Puesto que FTP usa los servicios TCP de NetX Duo, TCP debe estar habilitado con la llamada *nx_tcp_enable* antes de utilizar FTP.

Tenga en cuenta que la biblioteca de NetX Duo se puede habilitar para IPv6 y seguir admitiendo redes IPv4. Sin embargo, NetX Duo no admite IPv6 a menos que esté habilitado. Para deshabilitar el procesamiento de IPv6 en NetX Duo, **NX_DISABLE_IPV6** debe definirse en el archivo *nx_user.h* y dicho archivo debe incluirse en la compilación de la biblioteca de NetX Duo definiendo **NX_INCLUDE_USER_DEFINE_FILE** en el archivo *nx_port.h*. De forma predeterminada, **NX_DISABLE_IPV6** no está definido (IPv6 está habilitado). Esto es diferente del servicio *nxd_ipv6_enable* que configura los protocolos y servicios IPv6 en la tarea IP y requiere que **NX_DISABLE_IPV6** no se defina.

## <a name="small-example-system-of-netx-duo-ftp"></a>Sistema de ejemplo pequeño de FTP de NetX Duo

En la figura 1.1 que aparece a continuación se describe un ejemplo de lo fácil que es usar FTP de NetX Duo. En este ejemplo, se crea tanto un servidor FTP como un cliente FTP. Por tanto, ambos archivos de inclusión de FTP *nxd_ftp_client.h y nxd_ftp_server.h* se incluyen en las líneas 10 y 11. A continuación, el servidor FTP se crea en “*tx_application_define*” en la línea 99. Tenga en cuenta que los bloques de control del servidor y el cliente FTP se definen como variables globales en la línea 26 previamente.

En esta demostración se muestra cómo usar las funciones dobles disponibles en el FTP de NetX Duo, así como los servicios de FTP limitados de IPv4 heredados. Para usar las funciones de IPv6, la demostración define USE_IPV6 en la línea 16.

En la línea 162, el servidor FTP se crea con ***nxd_ftp_server_create** _ si la aplicación host define USE_IPV6, que admite tanto IPv4 como IPv6. Si no, el servidor FTP se crea con _ *_nx_ftp_server_create_** en la línea 166 con el servicio limitado de IPv4. Tenga en cuenta que la función "doble" usa argumentos de función de inicio de sesión y cierre de sesión diferentes al servicio IPv4, ambos definidos en la parte inferior del archivo en las líneas 534-568.

A continuación, el servidor FTP debe establecer su dirección IPv6 (local y global de vínculo) con NetX Duo, a partir de la línea 466 en la función de entrada de subprocesos del servidor FTP. Después, el servidor FTP se inicia en la línea 518 y está listo para las solicitudes de cliente FTP.

El cliente FTP se crea en la línea 316 y pasa por el mismo proceso que el servidor FTP para habilitar IPv6 para la tarea IP del cliente FTP y sus direcciones IPv6 se validan a partir de las líneas 263-313.

A continuación, el cliente se conecta al servidor FTP mediante ***nxd_ftp_client_connect** _ en la línea 334 si ha definido USE_IPV6, o en la línea 340 si usa el servicio limitado IPv4 _ *_nx_ftp_client_connect_**. En el transcurso de la función de subproceso del cliente FTP, se escribe un archivo en el servidor FTP y se lee de nuevo antes de la desconexión.

```C
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack.  This demo
   relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
   and then back to the server.  */



#include    "tx_api.h"
#include    "fx_api.h"
#include    "nx_api.h"
#include    "nxd_ftp_client.h"
#include    "nxd_ftp_server.h"

#define     DEMO_STACK_SIZE         4096

#ifdef FEATURE_NX_IPV6
#define USE_IPV6
#endif /* FEATURE_NX_IPV6 */


/* Define the ThreadX, NetX, and FileX object control blocks...  */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;


/* Define the NetX FTP object control blocks.  */

NX_FTP_CLIENT           ftp_client;
NX_FTP_SERVER           ftp_server;


/* Define the counters used in the demo application...  */

ULONG                   error_counter = 0;


/* Define the memory area for the FileX RAM disk.  */

UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];


#define FTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)

extern UINT  _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                        VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                        CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                        UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                        UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions.  */
VOID    _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);


void    client_thread_entry(ULONG thread_input);
void    thread_server_entry(ULONG thread_input);


#ifdef USE_IPV6
/* Define NetX Duo IP address for the NetX Duo FTP Server and Client. */
NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;
endif


/* Define server login/logout functions.  These are stubs for functions that would
   validate a client login request.   */

#ifdef USE_IPV6
UINT    server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
#else
UINT    server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
#endif


/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return(0);
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    UCHAR   *pointer;


    /* Setup the working pointer.  */
    pointer =  (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry, 0,
                     pointer, DEMO_STACK_SIZE,
                     4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize NetX.  */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server.  */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool", 256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors.  */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server.  */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", FTP_SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance.  */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP.  */
    nx_tcp_enable(&server_ip);

#ifdef USE_IPV6

    /* Next set the NetX Duo FTP Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Create the FTP server.  */
    status =  nxd_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login6, server_logout6);
#else
    /* Create the FTP server.  */
    status =  nx_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login, server_logout);
#endif
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread.  */
    status = tx_thread_create(&client_thread, "FTP Client thread ", client_thread_entry, 0,
            pointer, DEMO_STACK_SIZE,
            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE ;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client.  */
    status =  nx_packet_pool_create(&client_pool, "NetX Client Packet Pool", 256, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the FTP client.  */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP.  */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance.  */
    nx_tcp_enable(&client_ip);

    return;

}

/* Define the FTP client thread.  */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;

#ifdef USE_IPV6
UINT        iface_index, address_index;
#endif


    /* Format the RAM disk - the memory for the RAM disk was defined above.  */
    status = _fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry                */
                            ram_disk_memory,                 /* RAM disk memory pointer     */
                            ram_disk_sector_cache,           /* Media buffer pointer        */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size           */
                            "MY_RAM_DISK",                   /* Volume Name                 */
                            1,                               /* Number of FATs              */
                            32,                              /* Directory Entries           */
                            0,                               /* Hidden sectors              */
                            256,                             /* Total sectors               */
                            128,                             /* Sector size                 */
                            1,                               /* Sectors per cluster         */
                            1,                               /* Heads                       */
                            1);                              /* Sectors per track           */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk.  */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
        ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Let the IP threads and driver initialize the system.    */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    status = nxd_icmp_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Set the Client link local and global addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Let NetX Duo validate the addresses. */
    tx_thread_sleep(400);

#endif  /* USE_IPV6 */

    /* Create an FTP client.  */
    status =  nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Created the FTP Client\n");

#ifdef USE_IPV6

    do
    {

        /* Now connect with the NetX Duo FTP (IPv6) server. */
        status =  nxd_ftp_client_connect(&ftp_client, &server_ip_address, "name", "password", 100);
    } while (status != NX_SUCCESS);

#else

    /* Now connect with the NetX FTP (IPv4) server. */
    status =  nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS, "name", "password", 100);

#endif  /* USE_IPV6 */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet.  */
    status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer.  */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt.  */
    status =  nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");


    /* Close the file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");


    /* Now open the same file for reading.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file.  */
    status =  nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
            printf("Reread the FTP client test.txt file\n");
            nx_packet_release(my_packet);
    }

    /* Close this file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server.  */
    status =  nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;


    /* Delete the FTP client.  */
    status =  nx_ftp_client_delete(&ftp_client);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
}


/* Define the helper FTP server thread.  */
void    thread_server_entry(ULONG thread_input)
{

    UINT            status;
#ifdef  USE_IPV6
    UINT            iface_index, address_index;
#endif

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP server IPv6 enabled. */
    status = nxd_ipv6_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    status = nxd_icmp_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);

#endif /* USE_IPV6 */

    /* OK to start the FTP Server.   */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute.    */
    tx_thread_relinquish();

    return;
}


#ifdef USE_IPV6
UINT  server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    NXD_ADDRESS *client_ipduo_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged in6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
                     UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#else
UINT  server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#endif  /* USE_IPV6 */
```

**Figura 1.1 Ejemplo de FTP de NetX Duo**

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar FTP de NetX y FTP de NetX Duo. Se enumeran los valores predeterminados, pero la aplicación puede establecer cada definición

antes de la inclusión del archivo de encabezado de FTP de NetX Duo especificado. Si no se especifica ningún archivo de encabezado, la opción está disponible tanto en *nxd_ftp_client.h como en nxd_ftp_server.h*. En la lista siguiente se describe cada una de forma detallada:

- **NX_FTP_SERVER_PRIORITY**: prioridad del subproceso del servidor FTP. De forma predeterminada, este valor se define como 16 para especificar la prioridad 16.
- **NX_FTP_MAX_CLIENTS**: número máximo de clientes que el servidor puede controlar al mismo tiempo. De forma predeterminada, este valor es 4 para admitir 4 clientes a la vez.
- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: tamaño mínimo de la carga del grupo de paquetes de servidor en bytes, incluidos los encabezados TCP, IP y de trama de red, además de los datos HTTP. El valor predeterminado es 256 (longitud máxima del nombre de archivo en FileX) + 12 bytes para la información del archivo y NX_PHYSICAL_TRAILER.
- **NX_FTP_SERVER_TIMEOUT**: especifica el número de tics de ThreadX en los que se suspenderán los servicios internos. El valor predeterminado es 1 segundo (1 *  NX_IP_PERIODIC_RATE).
- **NX_FTP_ACTIVITY_TIMEOUT**: especifica el número de segundos que se mantiene una conexión de cliente si no hay ninguna actividad. El valor predeterminado se establece en 240.
- **NX_FTP_TIMEOUT_PERIOD**: especifica los intervalos en segundos en los que el servidor comprueba la actividad del cliente. El valor predeterminado se establece en 60.
- **NX_FTP_SERVER_RETRY_SECONDS**: especifica el tiempo de espera inicial en segundos antes de retransmitir la respuesta del servidor. El valor predeterminado es 2.
- **NX_FTP_SERVER_TRANSMIT_QUEUE_DEPTH**: especifica el máximo de profundidad de paquetes de transmisión en cola en el socket del servidor. El valor predeterminado es 20.
- **NX_FTP_SERVER_RETRY_MAX**: especifica el número máximo de reintentos por paquete. El valor predeterminado es 10.
- **NX_FTP_SERVER_RETRY_SHIFT**: especifica el número de bits que se va a desplazar al establecer el tiempo de espera de reintentos. El valor predeterminado es 2, por ejemplo, cada tiempo de espera de reintento es el doble que el reintento anterior.
- **NX_FTP_NO_FILEX**: si está definida, esta opción proporciona un código auxiliar para las dependencias de FileX. El cliente FTP funcionará sin ningún cambio si se define esta opción. El servidor FTP tendrá que modificarse o el usuario tendrá que crear unos cuantos servicios de FileX para que funcionen correctamente.
- **NX_FTP_CONTROL_TOS**: tipo de servicio necesario para las solicitudes de control de FTP. De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal.
- **NX_FTP_DATA_TOS**: tipo de servicio necesario para las solicitudes de datos de FTP. De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal.
- **NX_FTP_FRAGMENT_OPTION**: habilitación de fragmentación para solicitudes de FTP. De forma predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de TCP de FTP.
- **NX_FTP_CONTROL_WINDOW_SIZE**: tamaño de la ventana del socket de control de TCP. De forma predeterminada, este valor es 400 bytes.
- **NX_FTP_DATA_WINDOW_SIZE**: tamaño de la ventana de socket de datos de TCP. De forma predeterminada, este valor es 2048 bytes.
- **NX_FTP_TIME_TO_LIVE**: especifica el número de enrutadores que este paquete puede pasar antes de que se descarte. El valor predeterminado se establece en 0x80.
- **NX_FTP_USERNAME_SIZE**: especifica el número de bytes permitido en el *nombre de usuario* proporcionado por un cliente. El valor predeterminado se establece en 20 *.* .
- **NX_FTP_PASSWORD_SIZE**: especifica el número de bytes permitido en la *contraseña* proporcionada por un cliente. El valor predeterminado se establece en 20.
