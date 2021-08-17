---
title: 'Capítulo 2: Instalación y uso de FTP de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente FTP de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9da2761ed9483a920ab6f735b8a3a6bd82936c867ece8047b622788d5fb99804
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799496"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-ftp"></a>Capítulo 2: Instalación y uso de FTP de Azure RTOS NetX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente FTP de Azure RTOS NetX.

## <a name="product-distribution"></a>Distribución del producto

Azure RTOS NetX se puede obtener desde el repositorio de código fuente público en [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/]). El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:

- **nx_ftp.h**: archivo de encabezado para FTP para NetX
- **nx_ftp_client.c**: archivo de código fuente C para el cliente FTP para NetX
- **nx_ftp_server.c**: archivo de código fuente C para el servidor FTP para NetX
- **filex_stub.h**: archivo de código auxiliar si FileX no está presente
- **nx_ftp.pdf**: descripción en PDF de FTP para NetX
- **demo_netx_ftp.c**: sistema de demostración de FTP

## <a name="ftp-installation"></a>Instalación de FTP

Para usar FTP para NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX. Por ejemplo, si NetX está instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_ftp.h*, *nx_ftp_client.c* y *nx_ftp_server.c* deben copiarse en ese mismo directorio.

## <a name="using-ftp"></a>Mediante FTP

El uso de FTP para NetX es sencillo. Básicamente, el código de la aplicación debe incluir *nx_ftp.h* después de incluir *tx_api.h, fx_api.h* y *nx_api.h*, con el fin de usar ThreadX, FileX y NetX, respectivamente. Después de incluir *nx_ftp.h*, el código de la aplicación puede realizar las llamadas de función FTP especificadas más adelante en este manual. La aplicación también debe incluir *nx_ftp_client.c* y *nx_ftp_server.c* en el proceso de compilación. Estos archivos se deben compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar NetX FTP.

> [!NOTE]
> Puesto que FTP usa los servicios de NetX TCP, TCP debe estar habilitado con la llamada a *nx_tcp_enable* antes de utilizar FTP.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

Un ejemplo de lo fácil que es usar NetX FTP se describe en la figura 1.1 que aparece a continuación.

> [!NOTE]
> Esto es para un dispositivo host con una sola interfaz de red.

En este ejemplo, el archivo de inclusión de FTP *nx_ftp_client.h* y *nx_ftp_server.h* se incluyen en las líneas 10 y 11. A continuación, el servidor FTP se crea en "*tx_application_define*" en la línea 134. Observe que el bloque de control de servidor FTP "*Server*" se definió anteriormente como una variable global en la línea 31. Después de la creación correcta, se inicia un servidor FTP en la línea 363. En la línea 183 se crea el cliente FTP. Y, por último, el cliente escribe el archivo en la línea 229 y vuelve a leer el archivo en la línea 318.

```c
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack. This demo
relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
and then back to the server. */

#include     "tx_api.h"
#include     "fx_api.h"
#include     "nx_api.h"
#include     "nx_ftp_client.h"
#include     "nx_ftp_server.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD          server_thread;
TX_THREAD          client_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_PACKET_POOL     client_pool;
NX_IP              client_ip;
FX_MEDIA           ram_disk;

/* Define the NetX FTP object control blocks. */

NX_FTP_CLIENT     ftp_client;
NX_FTP_SERVER     ftp_server;

/* Define the counters used in the demo application... */

ULONG     error_counter = 0;

/* Define the memory area for the FileX RAM disk. */

UCHAR     ram_disk_memory[32000];
UCHAR     ram_disk_sector_cache[512];

#define FTP_SERVER_ADDRESS IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS IP_ADDRESS(1,2,3,5)

extern UINT _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                    VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                    CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                    UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                    UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions. */
VOID     _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

void     client_thread_entry(ULONG thread_input);
void     thread_server_entry(ULONG thread_input);

/* Define server login/logout functions. These are stubs for functions that would
validate a client login request. */

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port, CHAR *name,
                CHAR *password, CHAR *extra_info);

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port, CHAR *name,
                    CHAR *password, CHAR *extra_info);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry,
                    0, pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize NetX. */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server. */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance",
                        FTP_SERVER_ADDRESS, 0xFFFFFF00UL, &server_pool,
                        _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance. */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP. */
    nx_tcp_enable(&server_ip);

    /* Create the FTP server. */
    status = nx_ftp_server_create(&ftp_server, "FTP Server Instance",
                    &server_ip, &ram_disk, pointer, DEMO_STACK_SIZE,
                    &server_pool, server_login, server_logout);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread. */
    status = tx_thread_create(&client_thread, "FTP Client thread ",
                            client_thread_entry, 0,
                            pointer, DEMO_STACK_SIZE,
                            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client. */
    status = nx_packet_pool_create(&client_pool, "NetX Client Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance for the FTP client. */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS,
            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP. */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance. */
    nx_tcp_enable(&client_ip);

    return;
}

/* Define the FTP client thread. */
void     client_thread_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = _fx_media_format(&ram_disk,
            _fx_ram_driver, /* Driver entry */
            ram_disk_memory, /* RAM disk memory pointer */
            ram_disk_sector_cache, /* Media buffer pointer */
            sizeof(ram_disk_sector_cache), /* Media buffer size */
            "MY_RAM_DISK", /* Volume Name */
            1, /* Number of FATs */
            32, /* Directory Entries */
            0, /* Hidden sectors */
            256, /* Total sectors */
            128, /* Sector size */
            1, /* Sectors per cluster */
            1, /* Heads */
            1); /* Sectors per track */

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                            ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

     /* Let the IP threads and driver initialize the system. */
    tx_thread_sleep(100);

    /* Create an FTP client. */
    status = nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Created the FTP Client\n");

    /* Now connect with the NetX FTP (IPv4) server. */
    status = nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS,
                                    "name", "password", 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet. */
    status = nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Write ABCs into the packet payload! */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length = 28;
    my_packet -> nx_packet_append_ptr = my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt. */
    status = nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");

    /* Close the file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");

    /* Now open the same file for reading. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file. */
    status = nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
        printf("Reread the FTP client test.txt file\n");
        nx_packet_release(my_packet);
    }

    /* Close this file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server. */
    status = nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    /* Delete the FTP client. */
    status = nx_ftp_client_delete(&ftp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
}

/* Define the helper FTP server thread. */
void     thread_server_entry(ULONG thread_input)
{

UINT     status;

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

    /* OK to start the FTP Server. */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute. */
    tx_thread_relinquish();

    return;
}

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port,
                CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success. */
    return(NX_SUCCESS);
}

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success. */
    return(NX_SUCCESS);
}
```

Figura 1.1 Ejemplo de cliente FTP y servidor con NetX (host de interfaz de red única)

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar FTP para NetX. En la lista siguiente se describe cada una de forma detallada:  

- **NX_FTP_SERVER_PRIORITY**: prioridad del subproceso del servidor FTP. De forma predeterminada, este valor se define como 16 para especificar la prioridad 16.

- **NX_FTP_MAX_CLIENTS**: número máximo de clientes que el servidor puede controlar al mismo tiempo. De forma predeterminada, este valor es 4 para admitir 4 clientes a la vez.

- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: tamaño mínimo de la carga del grupo de paquetes de servidor en bytes, incluidos los encabezados TCP, IP y de trama de red, además de los datos HTTP. El valor predeterminado es 256 (longitud máxima del nombre de archivo en FileX) + 12 bytes para la información del archivo y NX_PHYSICAL_TRAILER.

- **NX_FTP_NO_FILEX**: si está definida, esta opción proporciona un código auxiliar para las dependencias de FileX. El cliente FTP funcionará sin ningún cambio si se define esta opción. El servidor FTP tendrá que modificarse o el usuario tendrá que crear unos cuantos servicios de FileX para que funcionen correctamente.

- **NX_FTP_CONTROL_TOS**: tipo de servicio necesario para las solicitudes de control TCP de FTP. De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal. La aplicación puede establecer esta definición antes de la inclusión de *nx_ftp.h*.

- **NX_FTP_DATA_TOS**: tipo de servicio necesario para las solicitudes de datos TCP de FTP. De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal. La aplicación puede establecer esta definición antes de la inclusión de *nx_ftp.h*.

- **NX_FTP_FRAGMENT_OPTION**: fragmento habilitar para solicitudes TCP de FTP. De forma predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de TCP de FTP. La aplicación puede establecer esta definición antes de la inclusión de *nx_ftp.h*.

- **NX_FTP_CONTROL_WINDOW_SIZE**: control del tamaño de la ventana del socket. De manera predeterminada, este valor es 400 bytes. La aplicación puede establecer esta definición antes de la inclusión de *nx_ftp.h*.

- **NX_FTP_DATA_WINDOW_SIZE**: tamaño de la ventana de socket de datos. De manera predeterminada, este valor es 2048 bytes. La aplicación puede establecer esta definición antes de la inclusión de *nx_ftp.h*.

- **NX_FTP_TIME_TO_LIVE**: especifica el número de enrutadores que un paquete puede pasar antes de que se descarte. El valor predeterminado se establece en 0x80, pero se puede redefinir antes de la inclusión de *nx_ftp.h.*

- **NX_FTP_SERVER_TIMEOUT**: especifica el número de tics de ThreadX en los que se suspenderán los servicios internos. El valor predeterminado se establece en 100, pero se puede redefinir antes de la inclusión de *nx_ftp.h.*

- **NX_FTP_USERNAME_SIZE**: especifica el número de bytes permitido en el *nombre de usuario* proporcionado por un cliente. El valor predeterminado se establece en 20, pero se puede redefinir antes de la inclusión de *nx_ftp.h.*

- **NX_FTP_PASSWORD_SIZE**: especifica el número de bytes permitido en la *contraseña* proporcionada por un cliente. El valor predeterminado se establece en 20, pero se puede redefinir antes de la inclusión de *nx_ftp.h.*

- **NX_FTP_ACTIVITY_TIMEOUT**: especifica el número de segundos que se mantiene una conexión de cliente si no hay ninguna actividad. El valor predeterminado se establece en 240, pero se puede redefinir antes de la inclusión de *nx_ftp.h.*

- **NX_FTP_TIMEOUT_PERIOD**: especifica el número de segundos entre la comprobación del servidor para la inactividad del cliente. El valor predeterminado se establece en 60, pero se puede redefinir antes de la inclusión de *nx_ftp.h.*
