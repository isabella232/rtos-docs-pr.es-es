---
title: 'Capítulo 2: Instalación y uso del servidor DHCP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente DHCP de NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: aed0b61e595666e834a269911a261b36d10f46069d587ee1be1ec64e143360e9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790333"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-dhcp-server"></a>Capítulo 2: Instalación y uso del servidor DHCP de Azure RTOS NetX Duo

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente DHCP de NetX Duo.

## <a name="product-distribution"></a>Distribución del producto

El servidor DHCP de NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:

- **nxd_dhcp_server.h**: archivo de encabezado del servidor DHCP de NetX Duo.
- **nx_dhcp_server.c**: archivo de código fuente de C del servidor DHCP de NetX Duo.
- **nxd_dhcp_server.pdf**: guía del usuario del servidor DHCP de NetX Duo.
- **demo_netxduo_dhcp.c**: demostración del servidor DHCP de NetX Duo.

## <a name="dhcp-installation"></a>Instalación de DHCP

Para usar el servidor DHCP de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo. Por ejemplo, si NetX Duo está instalado en el directorio “ *\threadx\arm7\green*”, los archivos *nxd_dhcp_server.h* y *nxd_dhpc_server.c* deben copiarse en este directorio.

## <a name="using-netx-duo-dhcp-server"></a>Uso del servidor DHCP de NetX Duo

Es fácil usar el servidor DHCP de NetX. Básicamente, el código de la aplicación debe incluir *nx_dhcp_server.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX, respectivamente. Después de incluir *nxd_dhcp_server.h*, el código de la aplicación puede realizar las llamadas de función DHCP especificadas más adelante en esta guía. La aplicación también debe incluir *nxd_dhcp_server.c* en el proceso de compilación. Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación. Para obtener más información sobre el uso del servidor DHCP de NetX Duo, consulte los siguientes apartados: **Requisitos del **servidor** DHCP de NetX Duo** y **Restricciones del servidor DHCP de NetX Duo**.

Tenga en cuenta que como DHCP usa los servicios de UDP de NetX Duo, debe habilitarse UDP con la llamada *nx_udp_enable* antes de utilizar DHCP.

## <a name="requirements-of-the-netx-duo-dhcp-server"></a>Requisitos del servidor DHCP de NetX Duo

El servidor DHCP de NetX Duo requiere un puerto de socket UDP asignado al puerto DHCP 67 conocido. Para crear el servidor DHCP, la aplicación debe crear un grupo de paquetes con una carga de paquetes de al menos 548 bytes más los encabezados IP, UDP y Ethernet (que tienen un total de 44 bytes con una alineación de 4 bytes).

Se supone que el servidor y el cliente usan la configuración de la dirección de hardware Ethernet:

- Tipo de hardware: 1
- Longitud de hardware: 6
- Saltos: 0

### <a name="multiple-client-sessions"></a>Varias sesiones de cliente

El servidor DHCP de NetX Duo puede controlar varias sesiones de cliente manteniendo una tabla de clientes DHCP activos y el "estado" en el que se encuentra el cliente, por ejemplo, los estados DHCP INIT, BOOT, SELECTING, REQUESTING, RENEWING, etc. Si el tiempo de espera de la sesión expira antes de recibir el siguiente mensaje de cliente, a menos que el cliente esté enlazado a una concesión de IP, el servidor borrará los datos de la sesión de cliente y devolverá la dirección IP asignada al grupo disponible. Si el servidor recibe varios mensajes DISCOVER del mismo cliente, el servidor restablece el tiempo de espera de la sesión y mantiene la dirección IP reservada para que el cliente acepte en un mensaje REQUEST posterior.

El servidor DHCP de NetX Duo también acepta la solicitud DHCP de cliente de un solo estado; por ejemplo, el cliente solo envía un mensaje REQUEST. Se supone que al cliente se le ha asignado previamente una concesión de IP del servidor DHCP.

### <a name="setting-interface-specific-network-parameters-server-responses"></a>Configuración de las respuestas del servidor de parámetros de red específicos de la interfaz

La aplicación puede configurar el enrutador, la máscara de subred y los parámetros del servidor DNS para cada interfaz que administra las solicitudes de cliente DHCP mediante el servicio *nx_dhcp_set_interface_network_parameters*. De lo contrario, estos parámetros se configuran de forma predeterminada para la puerta de enlace IP en la interfaz principal del servidor, la subred de red DHCP y la dirección IP del servidor DHCP, respectivamente.

El servidor DHCP incluye estos parámetros en la opción datos de los mensajes DHCP que envía a los clientes DHCP.

### <a name="assigning-ip-addresses-to-the-client"></a>Asignación de direcciones IP al cliente

Si el mensaje DISCOVER de cliente no especifica una dirección IP solicitada, el servidor DHCP puede usar una de su propio grupo. Si el servidor no tiene ninguna dirección IP disponible, enviará al cliente un mensaje NACK.

El servidor DHCP de NetX Duo concederá la dirección IP solicitada en el mensaje REQUEST de cliente siempre que la dirección IP esté disponible y se encuentre en la base de datos de direcciones IP del servidor. La aplicación crea la lista de direcciones IP disponibles del servidor para asignar a los clientes DHCP mediante el servicio *nx_dhcp_create_server_ip_address_list*. Si el servidor no tiene las direcciones IP solicitadas o se asigna a otro host, enviará al cliente un mensaje NACK.

Cuando el servidor DHCP recibe una solicitud de cliente, identifica a ese cliente de forma exclusiva mediante la dirección MAC del cliente en el campo dirección MAC del cliente en el mensaje de DHCP. Si el cliente cambia su dirección MAC o se mueve a otra subred, debe enviar un mensaje RELEASE al servidor para devolver la dirección IP al grupo disponible y solicitar una nueva dirección IP en el estado INIT.

Vea la figura 1.1 de la sección **Sistema de ejemplo pequeño** para obtener más información. El número de direcciones IP guardadas en la instancia del servidor DHCP se limita al tamaño de la matriz de direcciones del servidor en el bloque de control del servidor DHCP y se define mediante la opción configurable NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.

### <a name="ip-address-lease-times"></a>Tiempos de concesión de dirección IP

El servidor DHCP también aceptará el tiempo de concesión del cliente de la solicitud si dicho tiempo de concesión es menor que el tiempo de concesión predeterminado del servidor, que se define en la opción configurable NX_DHCP_DEFAULT_LEASE_TIME. Los tiempos de renovación y reenlace asignados al cliente son del 50 % y del 85 % del tiempo de concesión, respectivamente, a menos que el tiempo de concesión sea infinito (0xFFFFFFFF), en cuyo caso los tiempos de renovación y reenlace también se establecen en infinito.

### <a name="dhcp-server-timeouts"></a>Tiempos de expiración del servidor DHCP

El servidor DHCP tiene un tiempo de espera de sesión configurable de usuario, NX_DHCP_CLIENT_SESSION_TIMEOUT, para esperar al siguiente mensaje de cliente DHCP, a menos que se complete la sesión. El tiempo de espera se restablece cuando el servidor recibe el mensaje siguiente del cliente, independientemente de si es el mismo mensaje enviado anteriormente.

### <a name="internal-error-handling"></a>Control de errores interno

El servidor DHCP recibe y procesa los paquetes de cliente DHCP en la función *nx_dhcp_listen_for_messages*. Esta función interrumpirá el procesamiento del paquete de cliente DHCP actual si el paquete no es válido o el servidor DHCP encuentra un error interno. n *x_dhcp_listen_for_messages* devuelve un estado de error. El subproceso del servidor DHCP cede el control brevemente del programador de ThreadX antes de llamar a esta función para recibir el siguiente mensaje de cliente DHCP. En la versión actual no hay compatibilidad de registro para el estado de error devuelto desde *nx_dhcp_listen_for_messages.*

### <a name="option-55-parameter-request-list"></a>Opción 55: lista de solicitudes de parámetros

El servidor DHCP de NetX Duo debe estar configurado con un conjunto de opciones para cargar en la lista de la opción de solicitud de parámetros (55) en los mensajes OFFER y DHCPACK que se transmiten de vuelta al cliente. Estas opciones deben incluir datos de configuración críticos de red para la red de cliente y, de forma predeterminada, se define como dirección IP del enrutador, máscara de subred y servidor DNS. La lista de opciones es una lista delimitada por espacios y se define en la NX_DHCP_DEFAULT_SERVER_OPTION_LIST configurable por el usuario. Tenga en cuenta que el número de opciones especificado en esta lista debe ser igual que NX_DHCP_DEFAULT_OPTION_LIST_SIZE, que también está definido por el usuario.

## <a name="constraints-of-the-netx-duo-dhcp-server"></a>Restricciones del servidor DHCP de NetX Duo

### <a name="dhcp-messages"></a>Mensajes DHCP

El servidor DHCP de NetX Duo no comprueba si no se ha asignado una dirección IP en otra parte de la red antes de conceder la dirección IP al cliente. Si hay varios servidores DHCP, este podría ser el caso. *Según RFC 2131, es responsabilidad del cliente comprobar que la dirección IP es única en su red* (por ejemplo, haciendo ping a la dirección). Si no es así, el servidor debería recibir un mensaje DECLINE con la dirección IP para actualizar su base de datos desde el cliente.

El servidor DHCP de NetX Duo no emite mensajes de FORCE_RENEW. Es el cliente DHCP el que renueva su concesión de dirección IP. Sin embargo, el servidor DHCP supervisa el tiempo restante en todas las direcciones IP asignadas en su base de datos. Cuando expira una concesión de dirección IP, se devuelve la dirección IP al grupo de direcciones IP disponibles. Por lo tanto, es el cliente quien debe renovar o volver a enlazar activamente su concesión de dirección IP.

Los datos de la sesión se borran en cuanto el cliente se le concede ("se enlaza") a una concesión de IP (o se renueva una existente). Si un paquete de cliente demuestra ser ficticio o el cliente agota el tiempo de espera entre respuestas, se borran los datos de la sesión.

### <a name="saving-data-between-reboots"></a>Guardado de datos entre reinicios

El servidor DHCP de NetX Duo guarda los datos de cliente, incluidos los parámetros de solicitud DHCP, en una tabla de registros de cliente. Esta tabla no se almacena en memoria no volátil, por lo que, si el host del servidor DHCP debe reiniciar esa información, no se guarda entre reinicios.

El servidor DHCP de NetX Duo guarda los datos de concesión de direcciones IP en una tabla de direcciones IP. Esta tabla no se almacena en memoria no volátil, por lo que, si el host del servidor DHCP debe reiniciar esa información, no se guarda entre reinicios.

### <a name="relay-agents"></a>Agentes de retransmisión

El servidor DHCP de NetX Duo está configurado con una dirección IP cero para el campo "Agente de retransmisión" porque no es compatible con las solicitudes DHCP de la red.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

Un ejemplo de lo fácil que es usar el servidor DHCP Duo de NetX se describe en la figura 1.1 que aparece a continuación. En este ejemplo, el archivo de inclusión DHCP *nxd_dhcp_server.h* se incluye en la línea 5. El tamaño de la pila del subproceso del servidor DHCP, el tamaño de la pila del subproceso IP y el tamaño de la pila del subproceso de prueba se definen en las líneas 7-13.

En primer lugar, se crea una tarea de subproceso de prueba opcional para detener, reiniciar y eliminar el servidor DHCP con la función "*test_thread_entry*" en la línea 57. Un bloque de control de servidor DHCP "*dhcp_server*" se define como una variable global en la línea 20. Tenga en cuenta que el grupo de paquetes de servidor se crea con paquetes que tienen una carga al menos tan grande como el mensaje DHCP estándar (548 bytes más bytes de encabezado UDP e IP). Después de crear correctamente una instancia de IP para el servidor DHCP, la aplicación crea el servidor DHCP en la línea 96. A continuación, la aplicación permite que la instancia de IP del servidor esté habilitada para UDP. Antes de iniciar el servidor DHCP, se crea la lista de direcciones IP disponibles en la línea 137 mediante el servicio **nx_dhcp_create_server_ip_address_list**. Los parámetros de configuración de red se establecen en la siguiente línea 138 con el servicio **nx_dhcp_set_interface_network_parameters**, los servicios de servidor DHCP están disponibles cuando la aplicación llama a *nx_dhcp_server_start* en la línea 141. La tarea de subproceso de prueba muestra el uso de la detención y el reinicio del servidor DHCP.

```C
/* This is a small demo of NetX Duo DHCP Server for the high-performance NetX Duo TCP/IP stack.  */

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE         2048
#define     DEMO_SERVER_STACK_SIZE  2048
#define     SERVER_IP_ADDRESS_LIST  "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD          1000
#define     PACKET_POOL_SIZE        (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK    2048


/* Define the ThreadX and NetX Duo Duo object control blocks...  */

TX_THREAD test_thread;
NX_PACKET_POOL server_pool;
NX_IP server_ip;
NX_DHCP_SERVER dhcp_server;


/* Define the counters used in the demo application...  */

ULONG state_changes;


/* Define thread prototypes.  */

void test_thread_entry(ULONG thread_input);
void nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define main entry point.  */

int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{
    CHAR    *pointer;
    UINT    status;


    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the test thread.  */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
            pointer, TEST_STACK_SIZE,  1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duosystem.  */
    nx_system_initialize();

    /* Create the DHCP Server packet pool.  */
    status =  nx_packet_pool_create(&server_pool, "NetX Main Packet Pool", PACKET_PAYLOAD,
        pointer, PACKET_POOL_SIZE);
    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error.  */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance.  */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
        0xFFFFFF00UL,  &server_pool, nx_etherDriver_mcf5485, pointer,
        R_IP_THREAD_STACK, 1);

    pointer =  pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors.  */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance.  */
    status =  nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                                     DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic.  */
    status =  nx_udp_enable(&server_ip);

    /* Check for UDP enable errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility.  */
    status =  nx_icmp_enable(&server_ip);

    /* Check for errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

   status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                                 START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

   status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                               NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                               IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server.  */
   status =  nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread.  */
void    test_thread_entry(ULONG thread_input)
{
    UINT status;
    UINT keep_spinning;


    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }


    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);


    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}

```

**Figura 1.1 Ejemplo de aplicación del servidor DHCP de NetX Duo**

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar el servidor DHCP de NetX Duo. En la lista siguiente se describe cada una de forma detallada:

- **NX_DISABLE_ERROR_CHECKING**: esta opción quita la comprobación de errores DHCP básica. Normalmente se utiliza después de depurar la aplicación.
- **NX_DHCP_SERVER_THREAD_PRIORITY**: esta opción especifica la prioridad del subproceso del servidor DHCP. De forma predeterminada, este valor especifica que el subproceso DHCP se ejecuta con la prioridad 2.
- **NX_DHCP_TYPE_OF_SERVICE**: esta opción especifica el tipo de servicio necesario para las solicitudes UDP de DHCP. De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal.
- **NX_DHCP_FRAGMENT_OPTION**: habilita los fragmentos para solicitudes UDP de DHCP. De forma predeterminada, este valor se establece en NX_DONT_FRAGMENT para deshabilitar la fragmentación de UDP.
- **NX_DHCP_TIME_TO_LIVE**: especifica el número de enrutadores que un paquete puede pasar antes de que se descarte. El valor predeterminado es 0x80.
- **NX_DHCP_QUEUE_DEPTH**: especifica el número de paquetes que el socket del servidor DHCP conserva antes de vaciar la cola. El valor predeterminado es 5.
- **NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: especifica el tiempo de espera en tics del temporizador para que el servidor DHCP de NetX espere a que se asigne un paquete de su grupo de paquetes. El valor predeterminado está establecido en NX_IP_PERIODIC_RATE.
- **NX_DHCP_SUBNET_MASK**: se trata de la máscara de subred con la que se debe configurar el cliente DHCP. El valor predeterminado se define en 0xFFFFFF00.
- **NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: es el período de tiempo de espera en tics del temporizador para que el temporizador rápido del servidor DHCP compruebe el tiempo restante de la sesión y administre las sesiones que han agotado el tiempo de espera.
- **NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: es el período de tiempo de espera en tics del temporizador para que el temporizador lento del servidor DHCP compruebe el tiempo restante de la concesión de dirección IP y administre las concesiones que han agotado el tiempo de espera.
- **NX_DHCP_CLIENT_SESSION_TIMEOUT**: este es el período de tiempo de espera en tics del temporizador que el servidor DHCP esperará para recibir el siguiente mensaje de cliente DHCP.
- **NX_DHCP_DEFAULT_LEASE_TIME**: este es el tiempo de concesión de la dirección IP en segundos asignado al cliente DHCP y la base para calcular los tiempos de renovación y reenlace también asignados al cliente. El valor predeterminado se define en 0xFFFFFFFF (infinito).
- **NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: es el tamaño de la matriz de servidores DHCP que contiene las direcciones IP disponibles para asignar al cliente. El valor predeterminado es 20.
- **NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: es el tamaño de la matriz de servidor DHCP para contener los registros de cliente. El valor predeterminado es 50.
- **NX_DHCP_CLIENT_OPTIONS_MAX**: es el tamaño de la matriz en la instancia del cliente DHCP para contener todas las opciones solicitadas en la lista de solicitudes de parámetros en la sesión actual. El valor predeterminado es 12.
- **NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: este es el búfer que contiene la lista de opciones predeterminada del servidor DHCP que proporcionar al cliente DHCP actual en la lista de solicitudes de parámetros. El valor predeterminado es "1 3 6".
- **NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: es el tamaño de la matriz que contiene la lista de opciones predeterminada del servidor DHCP. El valor predeterminado es 3.
- **NX_DHCP_SERVER_HOSTNAME_MAX**: tamaño del búfer para contener el nombre de host del servidor. El valor predeterminado es 32.
- **NX_DHCP_CLIENT_HOSTNAME_MAX**: es el tamaño del búfer que contiene el nombre de host del cliente en la sesión de cliente del servidor DHCP actual. El valor predeterminado es 32.
