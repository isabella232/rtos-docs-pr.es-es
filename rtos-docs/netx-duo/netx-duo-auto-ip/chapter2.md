---
title: 'Capítulo 2: Instalación y uso de AutoIP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente AutoIP de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 42c58a4cdec34a03eda9f42315438e5fbe2ea594
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814833"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a>Capítulo 2: Instalación y uso de AutoIP de Azure RTOS NetX Duo

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente AutoIP de Azure RTOS NetX Duo.

## <a name="product-distribution"></a>Distribución del producto

El componente AutoIP de Azure RTOS NetX se puede obtener desde nuestro repositorio de código fuente público en [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/). El paquete incluye tres archivos de código fuente, un archivo de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:

- **nx_auto_ip.h**: archivo de encabezado para AutoIP de NetX
- **nx_auto_ip.c**: archivo de código fuente C para AutoIP de NetX
- **demo_netx_auto_ip.c**: demo de archivo de código fuente C para AutoIP de NetX
- **nx_auto_ip.pdf**: descripción en PDF de AutoIP de NetX

## <a name="autoip-installation"></a>Instalación de AutoIP

Para usar AutoIP de NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX. Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_auto_ip.h*, *nx_auto_ip.c* y *demo_netx_auto_ip.c* deben copiarse en ese mismo directorio.

## <a name="using-autoip"></a>Uso de AutoIP

El uso de AutoIP de NetX es sencillo. Básicamente, el código de la aplicación debe incluir *nx_auto_ip.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX. Después de incluir *nx_auto_ip.h*, el código de la aplicación puede realizar las llamadas de función AutoIP que se especifican más adelante en este manual. La aplicación también debe incluir *nx_auto_ip.c* en el proceso de compilación. Estos archivos se deben compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar AutoIP de NetX.

> [!NOTE]
> Dado que AutoIP usa servicios ARP de NetX, ARP debe estar habilitado con la llamada a *nx_arp_enable* antes de usar AutoIP.

## <a name="small-example-system"></a>Sistema de ejemplo pequeño

Un ejemplo de lo fácil que es usar AutoIP de NetX se describe en la figura 1.1, que aparece a continuación. En este ejemplo, el archivo de inclusión de AutoIP *nx_auto_ip.h* se agrega en la línea 002. A continuación, se crea la instancia de AutoIP de NetX en "*tx_application_define*" en la línea 090. Observe que el bloque de control de AutoIP de NetX "auto_ip_0" se definió anteriormente como una variable global en la línea 015. Después de la creación correcta, se inicia AutoIP de NetX en la línea 098. El procesamiento de la función de devolución de llamada de cambio de dirección IP comienza en la línea 105, que se usa para controlar los conflictos subsiguientes o la posible resolución de direcciones DHCP.

> [!NOTE]
> En el ejemplo siguiente se supone que el dispositivo host es un dispositivo de host único. En el caso de un dispositivo de host múltiple, la aplicación host puede usar el servicio AutoIP de NetX *nx_auto_ip_interface_* establecido para especificar una interfaz de red secundaria para sondear una dirección IP. Consulte el [Manual de usuario de NetX](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) para obtener más detalles sobre la configuración de aplicaciones de host múltiple. Observe que la aplicación host debe usar la API de NetX *nx_status_ip_interface_check* para comprobar que AutoIP haya obtenido una dirección IP.

```c
#include "tx_api.h"
#include "nx_api.h"
#include "nx_auto_ip.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD              thread_0;
NX_PACKET_POOL         pool_0;
NX_IP                  ip_0;

/* Define the AUTO IP structures for the IP instance. */

NX_AUTO_IP             auto_ip_0;

/* Define the counters used in the demo application... */

ULONG                 thread_0_counter;
ULONG                 address_changes;
ULONG                 error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);
void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

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
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    16, 16, 1, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
                                    pointer, 4096);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Create an IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
        error_counter++;

    /* Create the AutoIP instance for IP Instance 0. */
    status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Check AutoIP create status. */
    if (status)
        error_counter++;

    /* Start AutoIP instances. */
    status = **nx_auto_ip_start**(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);

    /* Check AutoIP start status. */
    if (status)
        error_counter++;

    /* Register an IP address change function for IP Instance 0. */
    status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
                                        (void *) &auto_ip_0);

    /* Check IP address change notify status. */
    if (status)
        error_counter++;
}

/* Define the test thread. */

void     thread_0_entry(ULONG thread_input)
{

UINT     status;
ULONG    actual_status;

    /* Wait for IP address to be resolved. */
    do
    {

        /* Call IP status check routine. */
        status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
            &actual_status, 10000);

    } while (status != NX_SUCCESS);

    /* Since the IP address is resolved at this point, the application can now fully utilize NetX! */

    while(1)
    {

        /* Increment thread 0's counter. */
        thread_0_counter++;

        /* Sleep... */
        tx_thread_sleep(10);
    }
}

void          ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
{

ULONG         ip_address;
ULONG         network_mask;
NX_AUTO_IP    *auto_ip_ptr;

    /* Setup pointer to auto IP instance. */
    auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;

    /* Pickup the current IP address. */
    nx_ip_address_get(ip_ptr, &ip_address, &network_mask);

    /* Determine if the IP address has changed back to zero. If so, make sure the AutoIP instance is started. */
    if (ip_address == 0)
    {

        /* Get the last AutoIP address for this node. */
        nx_auto_ip_get_address(auto_ip_ptr, &ip_address);

        /* Start this AutoIP instance. */
        nx_auto_ip_start(auto_ip_ptr, ip_address);
        }

    /* Determine if IP address has transitioned to a non local IP address. */
    else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
    {

        /* Stop the AutoIP processing. */
        nx_auto_ip_stop(auto_ip_ptr);
    }

    /* Increment a counter. */
    address_changes++;
}
```

Figura 1.1 Ejemplo de uso de AutoIP con NetX

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar AutoIP de NetX. A continuación se muestra una lista de todas las opciones, donde cada una de ellas se describe en detalle:

- **NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica de AutoIP. Normalmente se utiliza después de depurar la aplicación.
- **NX_AUTO_IP_PROBE_WAIT**: el número de segundos que hay que esperar antes de enviar el primer sondeo. De forma predeterminada, este valor es 1.
- **NX_AUTO_IP_PROBE_NUM**: el número de sondeos ARP que se van a enviar. De forma predeterminada, este valor es 3.
- **NX_AUTO_IP_PROBE_MIN**: el número mínimo de segundos que hay que esperar entre el envío de sondeos. De forma predeterminada, este valor es 1.
- **NX_AUTO_IP_PROBE_MAX**: el número máximo de segundos que hay que esperar entre el envío de sondeos. De forma predeterminada, este valor es 2.
- **NX_AUTO_IP_MAX_CONFLICTS**: el número de conflictos de AutoIP antes de aumentar los retrasos de procesamiento. De forma predeterminada, este valor es 10.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: el número de segundos que se debe extender el período de espera cuando se supera el número total de conflictos. De forma predeterminada, este valor es 60.
- **NX_AUTO_IP_ANNOUNCE_WAIT**: el número de segundos que hay que esperar antes de enviar el anuncio. De forma predeterminada, este valor es 2.
- **NX_AUTO_IP_ANNOUNCE_NUM**: el número de anuncios de ARP que se van a enviar. De forma predeterminada, este valor es 2.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: el número de segundos de espera entre el envío de anuncios. De forma predeterminada, este valor es 2.
- **NX_AUTO_IP_DEFEND_INTERVAL**: el número de segundos de espera entre anuncios de defensa. De forma predeterminada, este valor es 10.
