---
title: 'Capítulo 2: Instalación y uso de NetX HTTP'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX HTTP.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db621e38e9d2324ca3ce2398aee9f729b05886ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815197"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a>Capítulo 2: Instalación y uso de NetX HTTP

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX HTTP.

## <a name="product-distribution"></a>Distribución del producto

Azure RTOS NetX se puede obtener desde el repositorio de código fuente público en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).

- **nx_http_client.h** Archivo de encabezado del cliente HTTP para NetX.
- **nx_http_server.h** Archivo de encabezado del servidor HTTP para NetX.
- **nx_http_client.c** Archivo de código fuente de C del cliente HTTP para NetX.
- **nx_http_server.c** Archivo de código fuente de C del servidor HTTP para NetX.
- **nx_md5.c** Algoritmos de síntesis MD5.
- **filex_stub.h** Archivo de código auxiliar si FileX no existe.
- **nx_http.pdf** Descripción de HTTP para NetX.
- **demo_netx_http.c** Demostración de HTTP de NetX.

## <a name="http-installation"></a>Instalación de HTTP

Para usar HTTP para NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX. Por ejemplo, si NetX está instalado en el directorio " *\threadx\arm7\green*", entonces *nx_http_client.h* y *nx_http_client.c* en el caso de aplicaciones cliente HTTP de NetX y *nx_http_server.h* y *nx_http_server.c* en el caso de aplicaciones de servidor HTTP de NetX. *nx_md5.c* debe copiarse en este directorio. En la demostración de "controlador RAM", los archivos de servidor y cliente HTTP de NetX de la aplicación deben copiarse en el mismo directorio.

## <a name="using-http"></a>Uso de HTTP

El uso de HTTP para NetX es sencillo. Básicamente, el código de la aplicación debe incluir *nx_http_client.h* o *nx_http_server.h* después de incluir *tx_api.h, fx_api.h* y *nx_api.h*, para usar ThreadX, FileX y NetX, respectivamente. Una vez incluidos los archivos de encabezado HTTP, el código de aplicación puede realizar las llamadas de función HTTP especificadas más adelante en esta guía. La aplicación también debe incluir *nx_http_client.c*, *nx_http_server.c* y *md5.c* en el proceso de compilación. Estos archivos se deben compilar de la misma manera que otros archivos de aplicación, y su formulario de objetos se debe vincular junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar NetX HTTP.

>[!NOTE] 
> Si no se especifica NX_HTTP_DIGEST_ENABLE en el proceso de compilación, no es necesario agregar el archivo *md5.c* a la aplicación. Del mismo modo, si no se requiere ninguna funcionalidad de cliente HTTP, se puede omitir el archivo *nx_http_client.c*.

>[!NOTE] 
> Puesto que HTTP usa los servicios de NetX TCP, TCP debe estar habilitado con la llamada *nx_tcp_enable* antes de utilizar HTTP.

## <a name="small-example-system"></a>Sistema pequeño de ejemplo

Un ejemplo de lo fácil que es usar NetX HTTP se describe en la figura 1.1 que aparece a continuación. En este ejemplo, los archivos de inclusión HTTP *nx_http_client.h y nx_http_server.h se* proporcionan en la línea 8. A continuación, el servidor HTTP se crea en "*tx_application_define*" en la línea 131.

>[!NOTE] 
> El bloque de control de servidor HTTP "*server*" se definió anteriormente como una variable global en la línea 25.

Después de la creación correcta, se inicia un servidor HTTP en la línea 136. En la línea 149 se crea el cliente HTTP. Y, por último, el cliente escribe el archivo en la línea 157 y vuelve a leer el archivo en la línea 195.

```c
/* This is a small demo of HTTP on the high-performance NetX TCP/IP stack.
This demo relies on ThreadX, NetX, and FileX to show a simple HTML
transfer from the client and then back from the server. */

#include "tx_api.h"
#include "fx_api.h"
#include "nx_api.h"
#include "nx_http_client.h"
#include "nx_http_server.h"
#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_0;
TX_THREAD         thread_1;
NX_PACKET_POOL    pool_0;
NX_PACKET_POOL    pool_1;
NX_IP             ip_0;
NX_IP             ip_1;
FX_MEDIA          ram_disk;

/* Define HTTP objects. */

NX_HTTP_SERVER    my_server;
NX_HTTP_CLIENT    my_client;

/* Define the counters used in the demo application... */

ULONG             error_counter;

/* Define the RAM disk memory. */

UCHAR             ram_disk_memory[32000];

/* Define function prototypes. */

void     thread_0_entry(ULONG thread_input);
VOID     _fx_ram_driver(FX_MEDIA *media_ptr) ;
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT     authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, CHAR **name, CHAR **password, 
                              CHAR **realm);

/* Define the application's authentication check. This is called by
the HTTP server whenever a new request is received. */
UINT authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, CHAR **name, CHAR **password, 
                         CHAR **realm);
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */
    *name = "name";
    *password = "password";
    *realm = "NetX HTTP demo";

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create packet pool. */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
                         600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create an IP instance. */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
                0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create another IP instance. */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
                0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances. */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk. */
                 _fx_ram_driver, ram_disk_memory, pointer, 4096) ;
                 pointer += 4096;

    /* Create the NetX HTTP Server. */
    nx_http_server_create(&my_server, "My HTTP Server", &ip_1, &ram_disk,
                         pointer, 4096, &pool_1, authentication_check, NX_NULL);
                         pointer = pointer + 4096;

    /* Start the HTTP Server. */
    nx_http_server_start(&my_server);
}

/* Define the test thread. */
void     thread_0_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Create an HTTP client instance. */
    status = nx_http_client_create(&my_client, "My Client", &ip_0,
                                  &pool_0, 600);

    /* Check status. */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server. */
    status = nx_http_client_put_start(&my_client, IP_ADDRESS(1,2,3,5),
                                      "/test.htm", "name", "password", 103, 50);
    /* Check status. */
    if (status)
        error_counter++;

    /* Allocate a packet. */
    status = nx_packet_allocate(&pool_0, &my_packet, NX_TCP_PACKET,
                               NX_WAIT_FOREVER);
    /* Check status. */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page. */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
                         "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length. */
    status = **nx_http_client_put_packet**(&my_client, my_packet, 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Now GET the file back! */
    status = nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
                                     "/test.htm", NX_NULL, 0, "name", 
                                     "password", 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Get a packet. */
    status = nx_http_client_get_packet(&my_client, &my_packet, 20);

    /* Check for an error. */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet. */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it! */
        nx_packet_release(my_packet);
    }

    /* Flush the media. */
     fx_media_flush(&ram_disk);
 }
```

Figura 1.1 Ejemplo de uso de HTTP con NetX

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar HTTP para NetX. A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas. Los valores predeterminados se enumeran, pero se pueden redefinir antes de incluir *nx_http_client.h y nx_http_server.h*:

- **NX_DISABLE_ERROR_CHECKING** Si está definida, esta opción quita la comprobación de errores básica de HTTP. Por lo general, se utiliza después de depurar la aplicación.
- **NX_HTTP_SERVER_PRIORITY** Prioridad del subproceso de servidor HTTP. De manera predeterminada, este valor se define como 16 para especificar la prioridad 16.
- **NX_TFTP_NO_FILEX** Si está definida, esta opción proporciona un código auxiliar para las dependencias de FileX. Si esta opción está definida, el cliente HTTP funcionará sin ningún cambio. El servidor HTTP tendrá que modificarse o el usuario tendrá que crear unos cuantos servicios de FileX para que funcione correctamente.
- **NX_HTTP_TYPE_OF_SERVICE** Tipo de servicio necesario para las solicitudes HTTP TCP. De manera predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal.
- **NX_HTTP_SERVER_THREAD_TIME_SLICE** El número de tics de temporizador que el subproceso de servidor puede ejecutar antes de producir subprocesos con la misma prioridad. El valor predeterminado es 2.
- **NX_HTTP_FRAGMENT_OPTION** Permite habilitar la fragmentación de solicitudes TCP de HTTP. De manera predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de TCP de HTTP.
- **NX_HTTP_SERVER_WINDOW_SIZE** Tamaño de la ventana del socket de servidor. De manera predeterminada, este valor es 2048 bytes.
- **NX_TFTP_TIME_TO_LIVE** Especifica el número de enrutadores que este paquete puede pasar antes de que se descarte. El valor predeterminado se define en 0x80.
- **NX_HTTP_SERVER_TIMEOUT** Especifica el número de tics de ThreadX para los que se suspenderán los servicios internos. El valor predeterminado se establece en 10 segundos (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_ACCEPT** Especifica el número de tics de ThreadX para los que los servicios internos se suspenderán en las llamadas internas *nx_tcp_server_socket_accept*. El valor predeterminado se establece en (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Especifica el número de tics de ThreadX con los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_disconnect*. El valor predeterminado se establece en 10 segundos (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_RECEIVE** Especifica el número de tics de ThreadX con los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_receive*. El valor predeterminado se establece en 10 segundos (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_SEND** Especifica el número de tics de ThreadX con los que los servicios internos se suspenderán en las llamadas internas a *nx_tcp_socket_send*. El valor predeterminado se establece en 10 segundos (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_MAX_HEADER_FIELD** Especifica el tamaño máximo del campo de encabezado HTTP. El valor predeterminado es 256.
- **NX_HTTP_MULTIPART_ENABLE** Si se define, permite que el servidor HTTP admita solicitudes HTTP de varias partes.
- **NX_HTTP_SERVER_MAX_PENDING** Especifica el número de conexiones que se pueden poner en cola para el servidor HTTP. El valor predeterminado se establece en 5.
- **NX_HTTP_MAX_RESOURCE** Especifica el número de bytes permitido en un *nombre de recurso* proporcionado por el cliente. El valor predeterminado se establece en 40.
- **NX_HTTP_MAX_NAME** Especifica el número de bytes permitido en un *nombre de usuario* proporcionado por el cliente. El valor predeterminado se establece en 20.
- **NX_HTTP_MAX_PASSWORD** Especifica el número de bytes permitido en una *contraseña* proporcionada por el cliente. El valor predeterminado se establece en 20.
- **NX_HTTP_SERVER_MIN_PACKET_SIZE** Especifica el tamaño mínimo de los paquetes en el grupo especificado al crear el servidor. El tamaño mínimo es necesario para asegurarse de que el encabezado HTTP completo puede estar incluido en un paquete. El valor predeterminado se establece en 600.
- **NX_HTTP_CLIENT_MIN_PACKET_SIZE** Especifica el tamaño mínimo de los paquetes en el grupo especificado al crear el cliente. El tamaño mínimo es necesario para asegurarse de que el encabezado HTTP completo puede estar incluido en un paquete. El valor predeterminado se establece en 300.
- **NX_HTTP_SERVER_RETRY_SECONDS** *Establece el tiempo de espera de retransmisión de sockets del servidor en segundos. El* valor predeterminado se establece en 2.
- **NX_HTTP_SERVER_ RETRY_MAX** Establece el número máximo de retransmisiones en el socket de servidor. El valor predeterminado se establece en 10.
- **NX_HTTP_SERVER_ RETRY_SHIFT** Este valor se usa para establecer el siguiente tiempo de espera de retransmisión. El tiempo de espera actual se multiplica por el número de retransmisiones hasta el momento, desplazado por el valor del desplazamiento de tiempo de espera del socket. El valor predeterminado se establece en 1 para duplicar el tiempo de espera.
- **NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH** Especifica el número máximo de paquetes que se pueden poner en la cola de retransmisión de sockets de servidor. Si el número de paquetes puestos en cola alcanza este número, no se podrán enviar más paquetes hasta que se liberen uno o varios paquetes en cola. El valor predeterminado se establece en 20.