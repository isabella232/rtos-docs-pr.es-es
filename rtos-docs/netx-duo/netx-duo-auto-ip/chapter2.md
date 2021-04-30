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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a><span data-ttu-id="fb8d2-103">Capítulo 2: Instalación y uso de AutoIP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fb8d2-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo AutoIP</span></span>

<span data-ttu-id="fb8d2-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente AutoIP de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="fb8d2-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="fb8d2-105">Product Distribution</span></span>

<span data-ttu-id="fb8d2-106">El componente AutoIP de Azure RTOS NetX se puede obtener desde nuestro repositorio de código fuente público en [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span><span class="sxs-lookup"><span data-stu-id="fb8d2-106">Azure RTOS NetX AutoIP can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="fb8d2-107">El paquete incluye tres archivos de código fuente, un archivo de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="fb8d2-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="fb8d2-108">**nx_auto_ip.h**: archivo de encabezado para AutoIP de NetX</span><span class="sxs-lookup"><span data-stu-id="fb8d2-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="fb8d2-109">**nx_auto_ip.c**: archivo de código fuente C para AutoIP de NetX</span><span class="sxs-lookup"><span data-stu-id="fb8d2-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="fb8d2-110">**demo_netx_auto_ip.c**: demo de archivo de código fuente C para AutoIP de NetX</span><span class="sxs-lookup"><span data-stu-id="fb8d2-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="fb8d2-111">**nx_auto_ip.pdf**: descripción en PDF de AutoIP de NetX</span><span class="sxs-lookup"><span data-stu-id="fb8d2-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="fb8d2-112">Instalación de AutoIP</span><span class="sxs-lookup"><span data-stu-id="fb8d2-112">AutoIP Installation</span></span>

<span data-ttu-id="fb8d2-113">Para usar AutoIP de NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="fb8d2-114">Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_auto_ip.h*, *nx_auto_ip.c* y *demo_netx_auto_ip.c* deben copiarse en ese mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="fb8d2-115">Uso de AutoIP</span><span class="sxs-lookup"><span data-stu-id="fb8d2-115">Using AutoIP</span></span>

<span data-ttu-id="fb8d2-116">El uso de AutoIP de NetX es sencillo.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="fb8d2-117">Básicamente, el código de la aplicación debe incluir *nx_auto_ip.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="fb8d2-118">Después de incluir *nx_auto_ip.h*, el código de la aplicación puede realizar las llamadas de función AutoIP que se especifican más adelante en este manual.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="fb8d2-119">La aplicación también debe incluir *nx_auto_ip.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="fb8d2-120">Estos archivos se deben compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="fb8d2-121">Esto es todo lo que se necesita para usar AutoIP de NetX.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="fb8d2-122">Dado que AutoIP usa servicios ARP de NetX, ARP debe estar habilitado con la llamada a *nx_arp_enable* antes de usar AutoIP.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="fb8d2-123">Sistema de ejemplo pequeño</span><span class="sxs-lookup"><span data-stu-id="fb8d2-123">Small Example System</span></span>

<span data-ttu-id="fb8d2-124">Un ejemplo de lo fácil que es usar AutoIP de NetX se describe en la figura 1.1, que aparece a continuación.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="fb8d2-125">En este ejemplo, el archivo de inclusión de AutoIP *nx_auto_ip.h* se agrega en la línea 002.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="fb8d2-126">A continuación, se crea la instancia de AutoIP de NetX en "*tx_application_define*" en la línea 090.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="fb8d2-127">Observe que el bloque de control de AutoIP de NetX "auto_ip_0" se definió anteriormente como una variable global en la línea 015.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="fb8d2-128">Después de la creación correcta, se inicia AutoIP de NetX en la línea 098.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="fb8d2-129">El procesamiento de la función de devolución de llamada de cambio de dirección IP comienza en la línea 105, que se usa para controlar los conflictos subsiguientes o la posible resolución de direcciones DHCP.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="fb8d2-130">En el ejemplo siguiente se supone que el dispositivo host es un dispositivo de host único.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="fb8d2-131">En el caso de un dispositivo de host múltiple, la aplicación host puede usar el servicio AutoIP de NetX *nx_auto_ip_interface_* establecido para especificar una interfaz de red secundaria para sondear una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="fb8d2-132">Consulte el [Manual de usuario de NetX](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) para obtener más detalles sobre la configuración de aplicaciones de host múltiple.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-132">See the [NetX User Guide](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) for more details on setting up multihomed applications.</span></span> <span data-ttu-id="fb8d2-133">Observe que la aplicación host debe usar la API de NetX *nx_status_ip_interface_check* para comprobar que AutoIP haya obtenido una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

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

<span data-ttu-id="fb8d2-134">Figura 1.1 Ejemplo de uso de AutoIP con NetX</span><span class="sxs-lookup"><span data-stu-id="fb8d2-134">Figure 1.1 Example of AutoIP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="fb8d2-135">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="fb8d2-135">Configuration Options</span></span>

<span data-ttu-id="fb8d2-136">Hay varias opciones de configuración para compilar AutoIP de NetX.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="fb8d2-137">A continuación se muestra una lista de todas las opciones, donde cada una de ellas se describe en detalle:</span><span class="sxs-lookup"><span data-stu-id="fb8d2-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="fb8d2-138">**NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="fb8d2-139">Normalmente se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="fb8d2-140">**NX_AUTO_IP_PROBE_WAIT**: el número de segundos que hay que esperar antes de enviar el primer sondeo.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="fb8d2-141">De forma predeterminada, este valor es 1.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="fb8d2-142">**NX_AUTO_IP_PROBE_NUM**: el número de sondeos ARP que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="fb8d2-143">De forma predeterminada, este valor es 3.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="fb8d2-144">**NX_AUTO_IP_PROBE_MIN**: el número mínimo de segundos que hay que esperar entre el envío de sondeos.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="fb8d2-145">De forma predeterminada, este valor es 1.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="fb8d2-146">**NX_AUTO_IP_PROBE_MAX**: el número máximo de segundos que hay que esperar entre el envío de sondeos.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="fb8d2-147">De forma predeterminada, este valor es 2.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="fb8d2-148">**NX_AUTO_IP_MAX_CONFLICTS**: el número de conflictos de AutoIP antes de aumentar los retrasos de procesamiento.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="fb8d2-149">De forma predeterminada, este valor es 10.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="fb8d2-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: el número de segundos que se debe extender el período de espera cuando se supera el número total de conflictos.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="fb8d2-151">De forma predeterminada, este valor es 60.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="fb8d2-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: el número de segundos que hay que esperar antes de enviar el anuncio.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="fb8d2-153">De forma predeterminada, este valor es 2.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="fb8d2-154">**NX_AUTO_IP_ANNOUNCE_NUM**: el número de anuncios de ARP que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="fb8d2-155">De forma predeterminada, este valor es 2.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="fb8d2-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: el número de segundos de espera entre el envío de anuncios.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="fb8d2-157">De forma predeterminada, este valor es 2.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="fb8d2-158">**NX_AUTO_IP_DEFEND_INTERVAL**: el número de segundos de espera entre anuncios de defensa.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="fb8d2-159">De forma predeterminada, este valor es 10.</span><span class="sxs-lookup"><span data-stu-id="fb8d2-159">By default, this value is defined as 10.</span></span>
