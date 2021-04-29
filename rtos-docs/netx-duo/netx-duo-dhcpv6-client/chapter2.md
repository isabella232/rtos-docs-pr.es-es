---
title: 'Capítulo 2: Instalación y uso del cliente DHCPv6 de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente de cliente Azure RTOS NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a154dbeb91b46a2c8bd5f4585e168a6b62d042ff
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814782"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcpv6-client"></a>Capítulo 2: Instalación y uso del cliente DHCPv6 de Azure RTOS NetX Duo

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente de cliente Azure RTOS NetX Duo DHCPv6.

## <a name="product-distribution"></a>Distribución del producto

El cliente DHCPv6 de NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:

- **nxd_dhcpv6_client.h**: archivo de encabezado del cliente DHCPv6 de NetX Duo.

- **nxd_dhcpv6_client.c**: archivo de código fuente del cliente DHCPv6 de NetX Duo.

- **demo_netxduo_dhcpv6_client.c**: programa de ejemplo que muestra la configuración del cliente DHCPv6 de NetX Duo.

- **nxd_dhcpv6_client.pdf**: descripción en PDF del cliente DHCPv6 de NetX Duo.

## <a name="netx-duo-dhcpv6-client-installation"></a>Instalación del cliente DHCPv6 de NetX Duo

Para usar la API del cliente DHCPv6 de NetX Duo, la distribución completa que se ha mencionado arriba puede copiarse en el mismo directorio en el que está instalado NetX Duo. Por ejemplo, si NetX Duo se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nxd_dhcpv6_client.h* y *nxd_dhpcv6_client.c* pueden copiarse en este directorio.

## <a name="using-the-netx-duo-dhcpv6-client"></a>Uso del cliente DHCPv6 de NetX Duo

El código de la aplicación debe incluir *nxd_dhcpv6_client.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar el cliente DHCPv6, ThreadX y los servicios de NetX Duo, respectivamente. *nxd_dhcpv6_client.c* se debe compilar en el proyecto de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación.

### <a name="span-classunderlineclient-dhcp-unique-identifier-duidspan"></a><span class="underline">Identificador único de DHCP de cliente (DUID)</span>

El DUID de cliente define de forma única cada cliente en una red. Una aplicación debe crear un DUID de cliente antes de solicitar una dirección IPv6 de un servidor. El DUID de cliente se incluye automáticamente en todos los mensajes del servidor. Para crear un DUID, la aplicación llama al servicio *nx_dhcpv6_create_client_duid*:
```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT duid_type, 
                                  UINT hardware_type, ULONG time);
```

La aplicación llama a este servicio y especifica el tipo de DUID (solo nivel de vínculo, o nivel de vínculo más tiempo). Para los DUID de nivel de vínculo más tiempo, este servicio proporcionará el campo de tiempo si no se especifica la entrada de tiempo.

Para los dispositivos que se reinician y quieren usar una concesión de dirección IPv6 asignada previamente, la aplicación debe crear el DUID del cliente como el que se usó cuando se asignó la dirección IPv6. La dirección de nivel de vínculo es todo lo que se necesita para crear un DUID del cliente de nivel de vínculo. No se requiere almacenamiento de memoria no volátil previo si el dispositivo tiene acceso a la dirección de nivel de vínculo. En el caso de los DUID de tiempo, la aplicación debe tener acceso a los mismos datos que se usaron en la creación anterior de DUID, y para esto sí se requiere memoria no volátil. Los clientes que no tienen almacenamiento estable no deben usar DUID de tiempo.

### <a name="span-classunderlineclient-identity-association-for-non-temporary-addresses-ianaspan"></a><span class="underline">Asociación de identidades de direcciones no temporales (IANA) del cliente</span>

La aplicación debe crear una IANA y, opcionalmente, una o más direcciones IA antes de solicitar una dirección IPv6. Para ello, la aplicación llama al servicio *nx_dhcpv6_create_client_iana*. Para crear una opción de dirección IA, la aplicación llama al servicio *nx_dhcpv6_add_client_ia* con una dirección IPv6 y los valores de duración solicitados como una sugerencia para el servidor.

IANA y sus IA definen de manera acumulativa los parámetros de asignación de direcciones IPv6 del cliente:

Antes de iniciar el cliente DHCPv6, la aplicación cliente DHCPv6 crea una IANA mediante el servicio *nx_dhcpv6_create_client_iana*:

```C
UINT    nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                     UINT IA_ident, ULONG T1, ULONG T2);
```

También debe crear una o más IA mediante el servicio *nx_dhcpv6_create_client_ia* y las direcciones IPv6 solicitadas antes de iniciar el cliente DHCPv6.

```C
UINT    nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                                NXD_ADDRESS *ipv6_address, 
                                ULONG preferred_lifetime, 
                                ULONG valid_lifetime);
```

> [!NOTE]
> El número de direcciones IA que crea la aplicación no puede superar al del parámetro NX_DHCPV6_MAX_IA_ADDRESS, cuyo valor predeterminado es 1.

El cliente DHCPv6 de NetX Duo admite *nx_dhcpv6_create_client_ia* para las aplicaciones cliente DHCPv6 heredadas, y es idéntico a *nx_dhcpv6_add_client_ia*, pero se recomienda a los desarrolladores usar el servicio *nx_dhcpv6_add_client_ia*.

Estos servicios se muestran en el "sistema de ejemplo pequeño" en otro lugar de este capítulo.

### <a name="span-classunderlinenon-volatile-memory-considerations-to-reuse-ianas-and-iasspan"></a><span class="underline">Consideraciones de memoria no volátil para reutilizar IANA e IA</span>

La aplicación debe guardar los parámetros de IANA T1 y T2, así como el identificador de IANA en la memoria no volátil, si desea utilizar las mismas direcciones durante el reinicio. La aplicación también debe guardar su IA, que incluye su dirección IPv6 en la memoria no volátil.

La aplicación también debe almacenar el tiempo transcurrido que se ha enlazado a sus concesiones de direcciones IPv6 asignadas a la memoria no volátil, en caso de que se cierre. Esto se hace llamando al servicio *nx_dhcpv6_get_time_accrued* antes de detener el cliente DHCPv6.

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, 
                                ULONG *time_accrued);
```

Suponiendo que la aplicación tiene un reloj independiente para realizar el seguimiento del intervalo de tiempo desde que se detuvo y reinició el cliente DHCPv6 tras un reinicio, se agrega a ese tiempo transcurrido el tiempo acumulado en la concesión de IPv6 antes de detenerse. Ahora inicia la tarea de subproceso del cliente con el tiempo total transcurrido enlazado a la concesión de IPv6 como la entrada nv_time siguiente:

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr, ULONG nv_time);
```

A partir de este punto, la tarea de subproceso del cliente DHCPv6 se encargará de supervisar el tiempo acumulado en la concesión de IPv6 para saber cuándo renovar la concesión.

### <a name="span-classunderlinesetting-dhcpv6-option-dataspan"></a><span class="underline">Configuración de los datos de opciones de DHCPv6</span>

Antes de solicitar una concesión de IPv6, la aplicación puede solicitar otros datos de parámetros de red, como el servidor DNS y el servidor horario. Algunos de estos parámetros tienen servicios específicos. A continuación se muestran algunos:

```C
UINT  nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT enable)

UINT  nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr, 
                                           UINT enable);
```

### <a name="span-classunderlineinitiating-the-ipv6-address-requestspan"></a><span class="underline">Inicio de la solicitud de la dirección IPv6</span>

La aplicación inicia el subproceso del cliente DHCPv6 llamando al servicio *nx_dhcpv6_start* con una entrada de tiempo cero. Para iniciar el protocolo DHCPv6 con el fin de solicitar una dirección IPv6, la aplicación llama a *nx_dhcpv6_request_solicit*.

Si la aplicación desea utilizar una concesión IPv6 asignada previamente asignada, llama a *nx_dhcpv6_start* con una entrada de tiempo distinta de cero. No debe llamar a *nx_dhcpv6_request_solicit*.

A partir de ese momento, la aplicación no tiene que hacer nada más y el cliente DHCPv6 supervisará automáticamente cuando sea el momento de renovar o volver a enlazar una dirección IPv6.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

A continuación se describe un pequeño ejemplo de lo fácil que es usar el servidor DHCPv6 de NetX Duo con un cliente DHCPv6 que se ejecuta a través de un controlador “RAM” virtual. En esta demostración se presupone que un dispositivo solo tiene una interfaz de red física.

*tx_application_define* crea un grupo de paquetes para que el cliente DHCPv6 envíe mensajes DHCPv6. También crea un subproceso de aplicación y una instancia de IP. A continuación, habilita UDP e ICMP en IP en las líneas 130-148. Después, el cliente DHCPv6 se crea con funciones de devolución de llamada de cambio de estado (*dhcpv6_state_change_notify* ) y de error del servidor (*dhcpv6_server_error_handler*) en la línea 151.

En la función de entrada de subproceso de cliente, *thread_client_entry*, la IP de cliente se configura con una dirección local de vínculo y se habilita para los servicios IPv6 e ICMPv6 en las líneas 202-217. Antes de iniciar el cliente DHCPv6, la aplicación crea un DUID de cliente, una opción de IANA y una opción de dirección IA en las líneas 219-303. La opción de dirección IA es opcional si el cliente desea solicitar una dirección IPv6 y las duraciones preferida y válida del servidor. El servidor puede o no conceder los tiempos de concesión o la dirección IPv6 solicitada. La aplicación puede agregar más opciones del IA (hasta NX_DHCPV6_MAX_IA_ADDRESS) para asignarles varias direcciones globales.

Por último, la aplicación establece diversas opciones para solicitar parámetros de red en sus mensajes al servidor DHCPv6. La tarea del cliente DHCPv6 se inicia llamando a *nx_dhcpv6_start* en la línea 306 y el protocolo DHCPv6 real se inicia con el estado SOLICIT con la llamada a *nx_dhcpv6_request_solicit* en la línea 317. A continuación, el cliente DHCPv6 controla automáticamente la promoción del estado del cliente a través del protocolo DHCPv6 hasta que se enlaza a una dirección o se produce un error. Durante este tiempo, la aplicación espera a que se complete el protocolo, así como a que se complete la detección de direcciones duplicadas (DAD) si la instancia IP está configurada para DAD (que es la configuración predeterminada).

Después de la llamada a tx_thread_sleep, la aplicación comprueba el conjunto de parámetros globales de la devolución de llamada de cambio de estado para determinar el éxito de la tarea del cliente DHCPv6 para obtener una concesión de Pv6 y, en caso afirmativo, que la comprobación de unicidad de DAD se haya realizado correctamente. Esto se hace mediante los contadores configurados en las funciones de devolución de llamada de cambio de estado y del servidor. La aplicación sondea si hay recuentos distintos de cero de address_not_assigned, address_expired y server_errors para la asignación de direcciones erróneas. Si el recuento de bound_addresses es distinto de cero (al menos una dirección se asigna correctamente), comprueba si hay un servicio address_failed_dad distinto de cero para comprobar si se la DAD se ha realizado con errores. A continuación se ofrece una explicación de las devoluciones de llamada de error del servidor y el cambio de estado:

La devolución de llamada de cambio de estado, *dhcpv6_state_change_notify*, el estado del cliente DHCPv6 anterior y actual para determinar si el cliente recibió respuestas de servidor válidas:

  - *dhcpv6_state_change_notify* comprueba las transiciones directamente desde SOLICIT hasta INIT y, si es así, incrementa un contador para que el cliente DHCPv6 no reciba ninguna respuesta del servidor.

A continuación, *dhcpv6_state_change_notify* comprueba si el cliente se ha asignado (enlazado) a una o más direcciones IPv6:

  - Si el nuevo estado es BOUND, incrementa un contador de direcciones enlazadas al cliente.
    
*dhcpv6_state_change_notify* también comprueba si la DAD se ha realizado con errores.

  - Si el estado pasa de DECLINE a INIT, significa que el cliente DHCPv6 no ha superado la comprobación de DAD en una de sus direcciones asignadas e incrementa el recuento de asignaciones de direcciones con errores.
    
La última comprobación de *dhcpv6_state_change_notify* en este ejemplo es para una dirección asignada correctamente que pasó la comprobación de DAD con errores para renovarse o volverse a enlazar:

  - Si el estado cambia de REBIND a INIT, significa que el cliente no ha recibido ninguna respuesta a las solicitudes RENEW o REBIND y *dhcpv6_state_change_notify* incrementa su recuento de direcciones expiradas.

*dhcpv6_server_error_handler*, si la tarea de cliente DHCPv6 notifica un estado de error recibido del servidor, incrementa el recuento de errores del servidor.

Suponiendo que todo sea correcto, la aplicación consulta el cliente DHCPv6 en busca de datos de direcciones, incluidos los tiempos de la concesión. Obtiene un recuento de direcciones válidas (asignadas correctamente) mediante una llamada al servicio *nx_dhcpv6_get_valid_ip_address_count* y el tiempo de renovación en la IANA (se aplica a todas las direcciones IA asignadas) llamando a *nx_dhcpv6_get_iana_lease_time* en las líneas 372-392. A continuación, consulta el cliente DHCPv6 cada una de sus opciones de IA para la dirección IPv6 y los tiempos de la concesión por índice de dirección.

Algunos servicios de cliente DHCPv6 (*nx_dhcpv6_get_lease_time_data, nx_dhcpv6_get_IP_address*) no requieren un índice de dirección como entrada y devuelven los parámetros DHCPv6 para la dirección global del cliente principal. Esto es adecuado para los clientes con una única dirección IPv6 global cuando llama a *nx_dhcpv6_get_valid_ip_address_lease_time* en la línea 384.

La configuración del cliente DHCPv6, NX_DHCPV6_CLIENT_RESTORE_STATE, permite que un sistema restaure un cliente DHCPv6 creado previamente con el estado BOUND entre reinicios del sistema. Llamando a *nx_dhcpv6_client_get_record* para obtener el registro de cliente DHCPv6 entre los reinicios del sistema en la línea 434, o bien llamando a *nx_dhcpv6_client_restore_record* para almacenar el registro de cliente DHCPv6 después de encender el sistema en la línea 525.

A continuación, la aplicación libera las direcciones asignadas mediante el servicio *nx_dhcpv6_request_release* en la línea 552. Para reiniciar la aplicación, se detiene el cliente DHCPv6 con el servicio *nx_dhcpv6_client_stop* en la línea 567 y se borran todas las direcciones IPv6 registradas con la instancia de IP que se configuraron mediante el cliente DHCPv6. Para ello, llama a *nx_dhcpv6_reinitialize* en la línea 578. A continuación, reinicia la tarea del cliente DHCPv6 con los servicios *nx_dhcpv6_start* y *nx_dhcpv6_request_solicit* como antes.

El cliente DHCPv6 se elimina llamando a *nx_dhcpv6_delete* en la línea 626. Tenga en cuenta que no se elimina *e* l grupo de paquetes que creó para el cliente DHCPv6 porque la instancia de IP también usa este grupo de paquetes. En caso contrario, debe eliminar el grupo de paquetes si no se usa para usar el servicio *nx_packet_pool_delete* de NetX Duo.

```C
/* This is a small demo of the NetX Duo DHCPv6 Client for the high-performance NetX Duo stack. */

#include    <stdio.h>
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcpv6_client.h"

#ifdef FEATURE_NX_IPV6
#define     DEMO_STACK_SIZE         2048

/* Set the client address, and request these address from DHCPv6 Server. */
/*
#define     NX_DHCPV6_REQUEST_IA_ADDRESS
*/

/* Set the list of DHCPv6 option data (timezone, DNS server, timer server, domain name)to get from the DHCPv6 server. */

#define     NX_DHCPV6_REQUEST_OPTION


/* Add the fully qualified domain name to request whether the DHCPv6 server SHOULD or SHOULD NOT perform the AAAA RR or DNS updates. */

#define     NX_DHCPV6_REQUEST_FQDN_OPTION


/* Define the ThreadX and NetX object control blocks... */

NX_PACKET_POOL          pool_0;
TX_THREAD               thread_client;
NX_IP                   client_ip;

/* Define the Client and Server instances. */

NX_DHCPV6               dhcp_client;

/* Define the error counter used in the demo application... */
ULONG                   error_counter;
CHAR                    *pointer;

/* Define thread prototypes. */
void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Declare DHCPv6 Client callbacks */
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state);
VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type);

/* Set up globals for tracking changes to DHCPv6 Client from callback services. */
UINT state_changes = 0;
UINT address_expired = 0;
UINT address_failed_dad = 0;
UINT bound_addresses = 0;
UINT address_not_assigned = 0;
UINT server_errors = 0;

/* Define some DHCPv6 parameters. */

#define DHCPV6_IANA_ID      0xC0DEDBAD
#define DHCPV6_T1           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_T2           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_RENEW_TIME   NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_REBIND_TIME  NX_DHCPV6_INFINITE_LEASE
#define PACKET_PAYLOAD      500
#define PACKET_POOL_SIZE    (5*PACKET_PAYLOAD)

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

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the Client thread. */
    status = tx_thread_create(&thread_client, "Client thread", thread_client_entry, 0,
                              pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1024,  pointer, PACKET_POOL_SIZE);

    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create a Client IP instance. */
    status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                          0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                          pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable UDP traffic for sending DHCPv6 messages. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable ICMP. */
    status =  nx_icmp_enable(&client_ip);

    /* Check for ICMP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 Client. */
    status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                      &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                      dhcpv6_server_error_handler);

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update the stack pointer because we need it again. */
    pointer = pointer + 2048;

    /* Yield control to DHCPv6 threads and ThreadX. */
    return;
}


/* Define the Client host application thread. */

void    thread_client_entry(ULONG thread_input)
{

UINT        status;
ULONG       T1, T2;
UINT        address_count;
UINT        address_index = 0;
NXD_ADDRESS valid_ipv6_address;
ULONG       preferred_lifetime;
ULONG       valid_lifetime;
UINT        ia_count = 1;

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
NXD_ADDRESS ipv6_address;
#endif

#ifdef NX_DHCPV6_REQUEST_OPTION
UCHAR       buffer[200];
NXD_ADDRESS dns_server;
#endif

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE
ULONG       current_time;
ULONG       elapsed_time;
NX_DHCPV6_CLIENT_RECORD dhcpv6_client_record;
#endif


    state_changes = 0;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address of 0x1122334456. */
    status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

    if (status)
    {
        error_counter++;
        return;
    }

    /* Let NetX Duo get initialized. */
    tx_thread_sleep(50);

    /* Enable the Client IP for IPv6 and ICMPv6 services. */
    nxd_ipv6_enable(&client_ip);
    nxd_icmp_enable(&client_ip);

    /* Create a Link Layer Plus Time DUID for the DHCPv6 Client. Set time ID field
       to NULL; the DHCPv6 Client API will supply one. */
    status = nx_dhcpv6_create_client_duid(&dhcp_client, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                          NX_DHCPV6_HW_TYPE_IEEE_802, 0);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 client's Identity Association (IA-NA) now.

       Note that if this host had already been assigned in IPv6 lease, it
       would have to use the assigned T1 and T2 values in loading the DHCPv6
       client with an IANA block.
    */
    status = nx_dhcpv6_create_client_iana(&dhcp_client, DHCPV6_IANA_ID, DHCPV6_T1,  DHCPV6_T2);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
    memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
    ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
    ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
    ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
    ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
    ipv6_address.nxd_ip_address.v6[3] = 0x0000abcd;

    /* Create an IA address option.
        Note that if this host had already been assigned in IPv6 lease, it
        would have to use the assigned IPv6 address, preferred and valid lifetime
        values in loading the DHCPv6 Client with an IA block.
    */
    status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address,DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* If the DHCPv6 Client is configured for a maximum number of IA addresses
       greater than 1, we can add another IA address if the device requires
       multiple global IPv6 addresses. */
    if(NX_DHCPV6_MAX_IA_ADDRESS >= 2)
    {
        memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
        ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
        ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
        ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
        ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
        ipv6_address.nxd_ip_address.v6[3] = 0x00001234;

        /* Add another  IA address option. */
        status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address, DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            return;
        }
    }
#endif /* NX_DHCPV6_REQUEST_IA_ADDRESS  */

#ifdef NX_DHCPV6_REQUEST_OPTION
    /* Set the list of DHCPv6 option data to get from the DHCPv6 server if needed. */
    nx_dhcpv6_request_option_timezone(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_DNS_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_time_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_domain_name(&dhcp_client, NX_TRUE);
#endif /* NX_DHCPV6_REQUEST_OPTION */


#ifdef NX_DHCPV6_REQUEST_FQDN_OPTION
    /* Set the DHCPv6 Client FQDN option.
       operation: NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR         DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client.
                  NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE   DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client to the server.
                  NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE   DHCPv6 Client choose to request that the server perform no DNS updatest on its behalf. */
    nx_dhcpv6_request_option_FQDN(&dhcp_client, "DHCPv6-Client", NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR);
#endif /* NX_DHCPV6_REQUEST_FQDN_OPTION */

    /* Start up the NetX DHCPv6 Client thread task. */
    status =  nx_dhcpv6_start(&dhcp_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start the DHCPv6 by sending a Solicit message out on the network. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Is the DHCPv6 Client request for address assignment successfully started? */
    if (status == NX_SUCCESS)
    {

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Check the bound address. */
        if (bound_addresses != ia_count)
        {

            /* Attempt to find out why DHCPv6 failed, where...*/

            if (server_errors > 0)
            {
                /* Actually you would compare server_error count with number of IA's added
                   to determine if any addresses were assigned. */
                printf("Server error, not all address assigned\n");
            }

            if (address_not_assigned > 0)
            {
                /* Actually you would compare address not assigned count with number of IA's added
                   to determine if any addresses were assigned. */

                printf("No servers responded to some or all of our IAs\n");
            }

        }

        /* Regardless if the DHCPv6 Client achieved a bound state, check for DAD
           failures. */
        if (address_failed_dad > 0)
        {
            /* Actually you would compare failed dad count with number of IA's added
               to determine if any addresses were assigned. */

            printf("Some or all of our IAs failed DAD\n");

        }

        /* Successfully assigned IPv6 addresses! */

        /* Get the count of valid IPv6 address obtained by DHCPv6. */
        status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_client, &address_count);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IPv6 address and related lifetimes by address index. This index is the
           index into the DHCPv6 Client address table. Not to be confused with the IP
           instance address table! */
        status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_client, address_index,
                                                           &valid_ipv6_address, 
                                                               &preferred_lifetime,
                                                           &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IANA options for when to start renew/rebind requests. These time
           parameters are the same for all IPv6 addresses assigned in the Client
           e.g. IANA returned from Server. */
        status = nx_dhcpv6_get_iana_lease_time(&dhcp_client, &T1, &T2);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /*****************************************************************************/
        /* These are 'legacy' DHCPv6 services and are for the most part identical to the services
           above except they default to the primary global IPv6 address regardless if the
           Client was assigned more than one global IPv6 address. */

        /* Now check the assigned lease times. */
        status = nx_dhcpv6_get_lease_time_data(&dhcp_client, &T1, &T2,
                                               &preferred_lifetime, &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IP address. */
        status = nx_dhcpv6_get_IP_address(&dhcp_client, &valid_ipv6_address);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Bound state. */

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE

        /* Get the DHCPv6 Client record. */
        nx_dhcpv6_client_get_record(&dhcp_client, &dhcpv6_client_record);

        /* Delete DHCPv6 instance. */
        nx_dhcpv6_client_delete(&dhcp_client);

        /* Delete IP instance. */
        status = nx_ip_delete(&client_ip);

        /* Check for error. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Create a Client IP instance. */
        status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                              0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                              pointer, 2048, 1);

        pointer =  pointer + 2048;

        /* Check for IP create errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable UDP traffic for sending DHCPv6 messages. */
        status =  nx_udp_enable(&client_ip);

        /* Check for UDP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable ICMP. */
        status =  nx_icmp_enable(&client_ip);

        /* Check for ICMP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable the Client IP for IPv6 and ICMPv6 services. */
        status = nxd_ipv6_enable(&client_ip);
        status += nxd_icmp_enable(&client_ip);

        /* Check for IPv6 and ICMPv6 enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Establish the link local address for the host. The RAM driver creates
           a virtual MAC address of 0x1122334456. */
        status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

        if (status)
        {
            error_counter++;
            return;
        }

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Create the DHCPv6 Client. */
        status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                          &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                          dhcpv6_server_error_handler);

        /* Check for errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Update the stack pointer because we need it again. */
        pointer = pointer + 2048;

        /* Restore the DHCPv6 record. */
        nx_dhcpv6_client_restore_record(&dhcp_client, &dhcpv6_client_record, 5);

        /* Resume the DHCPv6 service. */
        nx_dhcpv6_resume(&dhcp_client);
#endif


#ifdef NX_DHCPV6_REQUEST_OPTION

        /* Get the DNS Server address. */
        nx_dhcpv6_get_DNS_server_address(&dhcp_client, 0, &dns_server);

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_DOMAIN_NAME_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        /* Get the time zone. */
        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_NEW_POSIX_TIMEZONE_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server
#endif

        /* At some point, we may wish to release the IPv6 address lease e.g. the device
           is leaving the network or powering down. In that case we inform the
           DHCPv6 Server that we are releasing the address lease. */
        status = nx_dhcpv6_request_release(&dhcp_client);

        /* Check status. */
        if (status != NX_SUCCESS)
        {

            error_counter++;
            return;
        }

        /* Send the release message. */
        tx_thread_sleep(100);
    }

    /* Stopping the Client task. */
    status = nx_dhcpv6_stop(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Clear the previously assigned IPv6 addresses from the Client and IP address table. */
    status = nx_dhcpv6_reinitialize(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start up the Client task again. */
    status = nx_dhcpv6_start(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Begin the request process by sending a Solicit message with the IA created above
       with our preferred IPv6 address. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);
    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Wait a bit before releasing the IP address and terminating the client. */
    tx_thread_sleep(500);

    /* Ok, lets stop the application. Again we DO NOT plan
       to keep the IPv6 address we were assigned and need to release it
       back to the DHCPv6 server. */
    status = nx_dhcpv6_request_release(&dhcp_client);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* Now delete the DHCPv6 client and release ThreadX and
       NetX Duo resources back to the system. */
    nx_dhcpv6_client_delete(&dhcp_client);


    return;

}


/* This is the notification from the DHCPv6 Client task that it has changed
   state in the DHCPv6 protocol, for example getting assigned an IPv6 lease and
   achieving the bound state or an IPv6 lease expires and being reset to
   the init state.
*/
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state)
{


    /* Increment state change counter. */
    state_changes++;

    /* Check if the Client attempted to request an IPv6 lease but no servers
       responded. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_SOLICIT) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that either DAD failed or IP lease expired. */
        address_not_assigned++;
    }

    /* Check if the Client has been assigned an IPv6 lease. */
    if (new_state == NX_DHCPV6_STATE_BOUND_TO_ADDRESS)
    {
        bound_addresses++;
    }

   /* Check if the Client was bound, but failed the uniqueness check
       (Duplicate Address Detection) and was reset to the INIT state. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_DECLINE) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that DAD failed on Client IA. */
        address_failed_dad++;
    }

    /* Check if the Client was bound, attempted renew the lease but the
       IPv6 address renewal/rebinding failed. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_REBIND) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that the IP lease expired. */
        address_expired++;
    }



    /* Other checks are possible. */

}

/* This is the notification from the DHCPv6 Client task that it received an error
   from the server (status code) in response to the Client's last DHCPv6 message.
*/

VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type)
{

    /* Increment the server error count. */
    server_errors++;

    /* This should distinguish between receiving a server error and no server
       available to assign the Client an IPv6 address if the Client fails
       to get assigned an address. */
}

#endif /* FEATURE_NX_IPV6 */
```
