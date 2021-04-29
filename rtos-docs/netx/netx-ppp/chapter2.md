---
title: 'Capítulo 2: Instalación y uso del protocolo punto a punto (PPP) de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del protocolo punto a punto (PPP) de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40f09da31f5541208c3b2cc0eeb54850b3d71f7c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815157"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-point-to-point-protocol-ppp"></a><span data-ttu-id="7a770-103">Capítulo 2: Instalación y uso del protocolo punto a punto (PPP) de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="7a770-103">Chapter 2 - Installation and use of Azure RTOS NetX Point-to-Point Protocol (PPP)</span></span>

<span data-ttu-id="7a770-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del protocolo punto a punto (PPP) de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="7a770-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Point-to-Point Protocol (PPP) component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="7a770-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="7a770-105">Product Distribution</span></span>

<span data-ttu-id="7a770-106">El paquete del protocolo punto a punto (PPP) de Azure RTOS NetX está disponible en <https://github.com/azure-rtos/netx>.</span><span class="sxs-lookup"><span data-stu-id="7a770-106">The Azure RTOS NetX Point-to-Point Protocol (PPP) package is available at <https://github.com/azure-rtos/netx>.</span></span> <span data-ttu-id="7a770-107">El paquete incluye los siguientes archivos:</span><span class="sxs-lookup"><span data-stu-id="7a770-107">The package includes the following files:</span></span>

- <span data-ttu-id="7a770-108">**nx_ppp.h**: archivo de encabezado de PPP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-108">**nx_ppp.h**: Header file for PPP for NetX</span></span>
- <span data-ttu-id="7a770-109">**nx_ppp.c**: archivo de código fuente de C de PPP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-109">**nx_ppp.c**: C Source file for PPP for NetX</span></span>
- <span data-ttu-id="7a770-110">**nx_ppp.pdf**: archivo PDF de descripción de PPP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-110">**nx_ppp.pdf**: PDF description of PPP for NetX</span></span>
- <span data-ttu-id="7a770-111">**demo_netx_ppp.c**: demostración de PPP de NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-111">**demo_netx_ppp.c**: NetX PPP demonstration</span></span>

## <a name="ppp-installation"></a><span data-ttu-id="7a770-112">Instalación de PPP</span><span class="sxs-lookup"><span data-stu-id="7a770-112">PPP Installation</span></span>

<span data-ttu-id="7a770-113">Para usar PPP para NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-113">In order to use PPP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="7a770-114">Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_ppp.h* y *nx_ppp.c* deben copiarse en este directorio.</span><span class="sxs-lookup"><span data-stu-id="7a770-114">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_ppp.h* and *nx_ppp.c* files should be copied into this directory.</span></span>

## <a name="using-ppp"></a><span data-ttu-id="7a770-115">Uso de PPP</span><span class="sxs-lookup"><span data-stu-id="7a770-115">Using PPP</span></span>

<span data-ttu-id="7a770-116">El uso de PPP para NetX es sencillo.</span><span class="sxs-lookup"><span data-stu-id="7a770-116">Using PPP for NetX is easy.</span></span> <span data-ttu-id="7a770-117">Básicamente, el código de la aplicación debe incluir *nx_ppp.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7a770-117">Basically, the application code must include *nx_ppp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="7a770-118">Después de incluir *nx_ppp.h*, el código de la aplicación puede realizar las llamadas de función PPP especificadas más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="7a770-118">Once *nx_ppp.h* is included, the application code is then able to make the PPP function calls specified later in this guide.</span></span> <span data-ttu-id="7a770-119">La aplicación también debe incluir *nx_ppp.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="7a770-119">The application must also include *nx_ppp.c* in the build process.</span></span> <span data-ttu-id="7a770-120">Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7a770-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="7a770-121">Esto es todo lo que se necesita para usar el protocolo PPP de NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-121">This is all that is required to use NetX PPP.</span></span>

## <a name="using-modems"></a><span data-ttu-id="7a770-122">Uso de módems</span><span class="sxs-lookup"><span data-stu-id="7a770-122">Using Modems</span></span>

<span data-ttu-id="7a770-123">Si se necesita un módem para la conexión a Internet, hay que tener en cuenta algunas consideraciones especiales para poder usar el producto de PPP de NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-123">If a modem is required for connection to the internet, some special considerations are required in order to use the NetX PPP product.</span></span> <span data-ttu-id="7a770-124">Básicamente, el uso de un módem introduce lógica adicional de inicialización y lógica para la pérdida de comunicación.</span><span class="sxs-lookup"><span data-stu-id="7a770-124">Basically, using a modem introduces additional initialization logic and logic for loss of communication.</span></span> <span data-ttu-id="7a770-125">Además, la mayor parte de la lógica de módem adicional se realiza fuera del contexto del protocolo PPP de NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-125">In addition, most of the additional modem logic is done outside the context of NetX PPP.</span></span> <span data-ttu-id="7a770-126">El flujo básico del uso de PPP de NetX con un módem es similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="7a770-126">The basic flow of using the NetX PPP with a modem goes something like this:</span></span>

1. <span data-ttu-id="7a770-127">Inicializar módem</span><span class="sxs-lookup"><span data-stu-id="7a770-127">Initialize Modem</span></span>

1. <span data-ttu-id="7a770-128">Marcar al proveedor de servicios de Internet (ISP)</span><span class="sxs-lookup"><span data-stu-id="7a770-128">Dial Internet Service Provider (ISP)</span></span>

1. <span data-ttu-id="7a770-129">Esperar a la conexión</span><span class="sxs-lookup"><span data-stu-id="7a770-129">Wait for Connection</span></span>

1. <span data-ttu-id="7a770-130">Esperar a la solicitud de UserID</span><span class="sxs-lookup"><span data-stu-id="7a770-130">Wait for UserID Prompt</span></span>

1. <span data-ttu-id="7a770-131">Iniciar PPP de NetX [PPP en operación]</span><span class="sxs-lookup"><span data-stu-id="7a770-131">Start NetX PPP [PPP in operation]</span></span>

1. <span data-ttu-id="7a770-132">Pérdida de comunicación</span><span class="sxs-lookup"><span data-stu-id="7a770-132">Loss of Communication</span></span>

1. <span data-ttu-id="7a770-133">Detener PPP de NetX (o reiniciar mediante nx_ppp_restart)</span><span class="sxs-lookup"><span data-stu-id="7a770-133">Stop NetX PPP (or restart via nx_ppp_restart)</span></span>

### <a name="initialize-modem"></a><span data-ttu-id="7a770-134">Inicializar módem</span><span class="sxs-lookup"><span data-stu-id="7a770-134">Initialize Modem</span></span>

<span data-ttu-id="7a770-135">Utilizando la rutina de salida en serie de bajo nivel de la aplicación, el módem se inicializa a través de una serie de comandos de caracteres ASCII (consulte la documentación del módem para obtener más detalles).</span><span class="sxs-lookup"><span data-stu-id="7a770-135">Using the application’s low-level serial output routine, the modem is initialized via a series of ASCII character commands (see modem’s documentation for more details).</span></span>

### <a name="dial-internet-service-provider"></a><span data-ttu-id="7a770-136">Marcar al proveedor de servicios de Internet</span><span class="sxs-lookup"><span data-stu-id="7a770-136">Dial Internet Service Provider</span></span>

<span data-ttu-id="7a770-137">Con la rutina de salida en serie de bajo nivel de la aplicación, se indica al módem que marque al ISP.</span><span class="sxs-lookup"><span data-stu-id="7a770-137">Using the application’s low-level serial output routine, the modem is instructed to dial the ISP.</span></span> <span data-ttu-id="7a770-138">Por ejemplo, lo siguiente es típico de una cadena ASCII que se usa para marcar a un ISP en el número 123-4567:</span><span class="sxs-lookup"><span data-stu-id="7a770-138">For example, the following is typical of an ASCII string used to dial an ISP at the number 123-4567:</span></span>

<span data-ttu-id="7a770-139">“ATDT123456\r”</span><span class="sxs-lookup"><span data-stu-id="7a770-139">“ATDT123456\r”</span></span>

### <a name="wait-for-connection"></a><span data-ttu-id="7a770-140">Esperar a la conexión</span><span class="sxs-lookup"><span data-stu-id="7a770-140">Wait for Connection</span></span>

<span data-ttu-id="7a770-141">En este momento, la aplicación espera a recibir la indicación del módem de que se ha establecido una conexión.</span><span class="sxs-lookup"><span data-stu-id="7a770-141">At this point, the application waits to receive indication from the modem that a connection has been established.</span></span> <span data-ttu-id="7a770-142">Esto se consigue buscando los caracteres de la rutina de entrada en serie de bajo nivel de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7a770-142">This is accomplished by looking for characters from the application’s low-level serial input routine.</span></span> <span data-ttu-id="7a770-143">Normalmente, los módems devuelven una cadena ASCII "CONNECT" cuando se ha establecido una conexión.</span><span class="sxs-lookup"><span data-stu-id="7a770-143">Typically, modems return an ASCII string “CONNECT” when a connection has been established.</span></span>

### <a name="wait-for-user-id-prompt"></a><span data-ttu-id="7a770-144">Esperar a la solicitud de UserID</span><span class="sxs-lookup"><span data-stu-id="7a770-144">Wait for User ID Prompt</span></span>

<span data-ttu-id="7a770-145">Una vez establecida la conexión, la aplicación debe esperar una solicitud de inicio de sesión inicial del ISP.</span><span class="sxs-lookup"><span data-stu-id="7a770-145">Once the connection has been established, the application must now wait for an initial login request from the ISP.</span></span> <span data-ttu-id="7a770-146">Normalmente, suele tomar la forma de una cadena ASCII como "Inicio de sesión".</span><span class="sxs-lookup"><span data-stu-id="7a770-146">This typically takes the form of an ASCII string like “Login?”</span></span>

### <a name="start-netx-ppp"></a><span data-ttu-id="7a770-147">Iniciar PPP de NetX</span><span class="sxs-lookup"><span data-stu-id="7a770-147">Start NetX PPP</span></span>

<span data-ttu-id="7a770-148">En este punto, se puede iniciar el protocolo PPP de NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-148">At this point, the NetX PPP can be started.</span></span> <span data-ttu-id="7a770-149">Esto se logra mediante una llamada al servicio *nx_ppp_create* seguido del servicio *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="7a770-149">This is accomplished by calling the *nx_ppp_create* service followed by the *nx_ip_create* service.</span></span> <span data-ttu-id="7a770-150">También es posible que se requieran servicios adicionales para habilitar PAP y configurar las direcciones IP de PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-150">Additional services to enable PAP and to setup the PPP IP addresses might also be required.</span></span> <span data-ttu-id="7a770-151">Consulte las siguientes secciones de esta guía para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="7a770-151">Please review the following sections of this guide for more information.</span></span>

### <a name="loss-of-communication"></a><span data-ttu-id="7a770-152">Pérdida de comunicación</span><span class="sxs-lookup"><span data-stu-id="7a770-152">Loss of Communication</span></span>

<span data-ttu-id="7a770-153">Una vez que se inicia PPP, cualquier información que no sea de PPP se pasa a la rutina de "control de paquetes no válidos" que la aplicación especificó para el servicio *nx_ppp_create*.</span><span class="sxs-lookup"><span data-stu-id="7a770-153">Once PPP is started, any non-PPP information is passed to the “invalid packet handling” routine the application specified to the *nx_ppp_create* service.</span></span> <span data-ttu-id="7a770-154">Normalmente, los módems envían una cadena ASCII, como "SIN OPERADOR", cuando se pierde la comunicación con el ISP.</span><span class="sxs-lookup"><span data-stu-id="7a770-154">Typically, modems send an ASCII string such as “NO CARRIER” when communication is lost with the ISP.</span></span> <span data-ttu-id="7a770-155">Cuando la aplicación recibe un paquete que no es PPP con dicha información, debe continuar para detener la instancia de PPP de NetX o reiniciar la máquina de estados de PPP a través de la API de *nx_ppp_restart*.</span><span class="sxs-lookup"><span data-stu-id="7a770-155">When the application receives a non-PPP packet with such information, it should proceed to either stop the NetX PPP instance or to restart the PPP state machine via the *nx_ppp_restart* API.</span></span>

### <a name="stop-netx-ppp"></a><span data-ttu-id="7a770-156">Detener PPP de NetX</span><span class="sxs-lookup"><span data-stu-id="7a770-156">Stop NetX PPP</span></span>

<span data-ttu-id="7a770-157">Detener el protocolo PPP de NetX es bastante sencillo.</span><span class="sxs-lookup"><span data-stu-id="7a770-157">Stopping the NetX PPP is fairly straightforward.</span></span> <span data-ttu-id="7a770-158">Básicamente, todos los sockets creados deben desenlazarse y eliminarse.</span><span class="sxs-lookup"><span data-stu-id="7a770-158">Basically, all created sockets must be unbound and deleted.</span></span> <span data-ttu-id="7a770-159">A continuación, elimine la instancia de IP a través del servicio *nx_ip_delete*.</span><span class="sxs-lookup"><span data-stu-id="7a770-159">Next, delete the IP instance via the *nx_ip_delete* service.</span></span> <span data-ttu-id="7a770-160">Una vez eliminada la instancia de IP, se debe llamar al servicio *nx_ppp_delete* para finalizar el proceso de detención de PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-160">Once the IP instance is deleted, the *nx_ppp_delete* service should be called to finish the process of stopping PPP.</span></span> <span data-ttu-id="7a770-161">En este momento, la aplicación puede intentar restablecer la comunicación con el ISP.</span><span class="sxs-lookup"><span data-stu-id="7a770-161">At this point, the application is now able to attempt to reestablish communication with the ISP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="7a770-162">Sistema de ejemplo pequeño</span><span class="sxs-lookup"><span data-stu-id="7a770-162">Small Example System</span></span>

<span data-ttu-id="7a770-163">En la figura 1.1 a continuación se describe un ejemplo que muestra lo fácil que es usar el protocolo PPP de NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-163">An example that illustrates how easy it is to use NetX PPP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="7a770-164">En este ejemplo, el archivo de inclusión de PPP *nx_ppp.h* se incluye en la línea 3.</span><span class="sxs-lookup"><span data-stu-id="7a770-164">In this example, the PPP include file *nx_ppp.h* is brought in at line 3.</span></span> <span data-ttu-id="7a770-165">A continuación, se crea el protocolo PPP en *"tx_application_define*" en la línea 56.</span><span class="sxs-lookup"><span data-stu-id="7a770-165">Next, PPP is created in *”tx_application_define*” at line 56.</span></span> <span data-ttu-id="7a770-166">El bloque de control de PPP "*my_ppp*" se definió anteriormente como una variable global en la línea 9.</span><span class="sxs-lookup"><span data-stu-id="7a770-166">The PPP control block “*my_ppp*” was defined as a global variable at line 9 previously.</span></span> 

>[!NOTE]
><span data-ttu-id="7a770-167">El protocolo PPP debe crearse antes de crear la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="7a770-167">PPP should be created prior to creating the IP instance.</span></span> <span data-ttu-id="7a770-168">Después de crear correctamente PPP e IP, el subproceso "*my_thread*" espera a que el vínculo de PPP esté activo en la línea 98.</span><span class="sxs-lookup"><span data-stu-id="7a770-168">After successful creation of PPP and IP, the thread “*my_thread*” waits for the PPP link to come alive at line 98.</span></span> <span data-ttu-id="7a770-169">En la línea 104, tanto PPP como NetX están totalmente operativos.</span><span class="sxs-lookup"><span data-stu-id="7a770-169">At line 104, both PPP and NetX are fully operational.</span></span>

<span data-ttu-id="7a770-170">El único elemento que no se muestra en este ejemplo es el ISR de recepción de bytes en serie de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7a770-170">The one item not shown in this example is the application’s serial byte receive ISR.</span></span> <span data-ttu-id="7a770-171">Deberá llamar a *nx_ppp_byte_receive* con "*my_ppp*" y el byte recibido como parámetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="7a770-171">It will need to call *nx_ppp_byte_receive* with “*my_ppp*” and the byte received as input parameters.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_ppp.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a><span data-ttu-id="7a770-172">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="7a770-172">Configuration Options</span></span>

<span data-ttu-id="7a770-173">Hay varias opciones de configuración para crear el protocolo PPP para NetX.</span><span class="sxs-lookup"><span data-stu-id="7a770-173">There are several configuration options for building PPP for NetX.</span></span> <span data-ttu-id="7a770-174">En la lista siguiente se describe cada una de forma detallada:</span><span class="sxs-lookup"><span data-stu-id="7a770-174">The following list describes each in detail:</span></span>

- <span data-ttu-id="7a770-175">**NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica de PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-175">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPP error checking.</span></span> <span data-ttu-id="7a770-176">Normalmente se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7a770-176">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="7a770-177">**NX_PPP_PPPOE_ENABLE**: si está definida, PPP puede transmitir paquetes a través de Ethernet.</span><span class="sxs-lookup"><span data-stu-id="7a770-177">**NX_PPP_PPPOE_ENABLE**: If defined, PPP can transmit packet over Ethernet</span></span>
- <span data-ttu-id="7a770-178">**NX_PPP_BASE_TIMEOUT**: define la frecuencia del periodo (en tics del temporizador) con el que se reactiva la tarea del subproceso de PPP para comprobar los eventos de PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-178">**NX_PPP_BASE_TIMEOUT**: This defines the period rate (in timer ticks) that the PPP thread task is woken to check for PPP events.</span></span> <span data-ttu-id="7a770-179">El valor predeterminado es 1\*NX_IP_PERIODIC_RATE (100 tics).</span><span class="sxs-lookup"><span data-stu-id="7a770-179">The default value is 1\*NX_IP_PERIODIC_RATE (100 ticks).</span></span>
- <span data-ttu-id="7a770-180">**NX_PPP_DISABLE_INFO**: si está definida, la recopilación de información interna de PPP está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="7a770-180">**NX_PPP_DISABLE_INFO**: If defined, internal PPP information gathering is disabled.</span></span>
- <span data-ttu-id="7a770-181">**NX_PPP_DEBUG_LOG_ENABLE**: si está definida, se habilita el registro de depuración interno de PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-181">**NX_PPP_DEBUG_LOG_ENABLE**: If defined, internal PPP debug log is enabled.</span></span>
- <span data-ttu-id="7a770-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**: si está definida, se habilita el registro de depuración de PPP interno *printf* en *stdio*.</span><span class="sxs-lookup"><span data-stu-id="7a770-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**:If defined, internal PPP debug log *printf* to *stdio* is enabled.</span></span> <span data-ttu-id="7a770-183">Esto solo es válido si el registro de depuración también está habilitado.</span><span class="sxs-lookup"><span data-stu-id="7a770-183">This is only valid if the debug log is also enabled.</span></span>
- <span data-ttu-id="7a770-184">**NX_PPP_DEBUG_LOG_SIZE**: tamaño del registro de depuración (número de entradas del registro de depuración).</span><span class="sxs-lookup"><span data-stu-id="7a770-184">**NX_PPP_DEBUG_LOG_SIZE**: Size of debug log (number of entries in the debug log).</span></span> <span data-ttu-id="7a770-185">Al llegar a la última entrada, la captura de depuración vuelve a la primera entrada y sobrescribe cualquier dato capturado previamente.</span><span class="sxs-lookup"><span data-stu-id="7a770-185">On reaching the last entry, the debug capture wraps to the first entry and overwrites any data previously captured.</span></span> <span data-ttu-id="7a770-186">El valor predeterminado es 50.</span><span class="sxs-lookup"><span data-stu-id="7a770-186">The default value is 50.</span></span>
- <span data-ttu-id="7a770-187">**NX_PPP_DEBUG_FRAME_SIZE**: cantidad máxima de datos capturados de una carga de paquetes recibida y guardados en la salida de depuración.</span><span class="sxs-lookup"><span data-stu-id="7a770-187">**NX_PPP_DEBUG_FRAME_SIZE**: Maximum amount of data captured from a received packet payload and saved to debug output.</span></span> <span data-ttu-id="7a770-188">El valor predeterminado es 50.</span><span class="sxs-lookup"><span data-stu-id="7a770-188">The default value is 50.</span></span>
- <span data-ttu-id="7a770-189">**NX_PPP_DISABLE_CHAP**: si está definida, se quita la lógica interna de CHAP de PPP, incluida la lógica de síntesis de MD5.</span><span class="sxs-lookup"><span data-stu-id="7a770-189">**NX_PPP_DISABLE_CHAP**: If defined, internal PPP CHAP logic is removed, including the MD5 digest logic.</span></span>
- <span data-ttu-id="7a770-190">**NX_PPP_DISABLE_PAP**: si está definida, se quita la lógica interna de PAP de PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-190">**NX_PPP_DISABLE_PAP**: If defined, internal PPP PAP logic is removed.</span></span>
- <span data-ttu-id="7a770-191">**NX_PPP_DNS_OPTION_DISABLE**: si está definida, la opción DNS se deshabilita en la respuesta IPCP.</span><span class="sxs-lookup"><span data-stu-id="7a770-191">**NX_PPP_DNS_OPTION_DISABLE**: If defined, DNS Option is disabled in the IPCP response.</span></span>  <span data-ttu-id="7a770-192">De forma predeterminada, esta opción no está definida (la opción de DNS está establecida).</span><span class="sxs-lookup"><span data-stu-id="7a770-192">By default this option is not defined (DNS option is set).</span></span>
- <span data-ttu-id="7a770-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: especifica el número de veces que el host de PPP solicitará una dirección de servidor DNS del homólogo en el estado de IPCP.</span><span class="sxs-lookup"><span data-stu-id="7a770-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: This specifies how many times the PPP host will request a DNS Server address from the peer in the IPCP state.</span></span> <span data-ttu-id="7a770-194">Esto no tiene ningún efecto si se define NX_PPP_DNS_OPTION_DISABLE.</span><span class="sxs-lookup"><span data-stu-id="7a770-194">This has no effect if NX_PPP_DNS_OPTION_DISABLE is defined.</span></span> <span data-ttu-id="7a770-195">El valor predeterminado es 2.</span><span class="sxs-lookup"><span data-stu-id="7a770-195">The default value is 2.</span></span>
- <span data-ttu-id="7a770-196">**NX_PPP_HASHED_VALUE_SIZE**: especifica el tamaño de las cadenas "hashed value" que se usan en la autenticación de CHAP.</span><span class="sxs-lookup"><span data-stu-id="7a770-196">**NX_PPP_HASHED_VALUE_SIZE**: Specifies the size of “hashed value” strings used in CHAP authentication.</span></span> <span data-ttu-id="7a770-197">El valor predeterminado se establece en 16 bytes, pero se puede redefinir antes de la inclusión de *nx_ftp.h*.</span><span class="sxs-lookup"><span data-stu-id="7a770-197">The default value is set to 16 bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="7a770-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: define el número máximo de reintentos si el protocolo PPP agota el tiempo de espera antes de enviar otro mensaje de solicitud de configuración de LCP.</span><span class="sxs-lookup"><span data-stu-id="7a770-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another LCP configure request message.</span></span> <span data-ttu-id="7a770-199">Cuando se alcanza este número, se anula el protocolo de enlace de PPP y el estado del vínculo se desactiva.</span><span class="sxs-lookup"><span data-stu-id="7a770-199">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="7a770-200">El valor predeterminado es 20.</span><span class="sxs-lookup"><span data-stu-id="7a770-200">The default value is 20.</span></span>
- <span data-ttu-id="7a770-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: define el número máximo de reintentos si el protocolo PPP agota el tiempo de espera antes de enviar otro mensaje de solicitud de autenticación de PAP.</span><span class="sxs-lookup"><span data-stu-id="7a770-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another PAP authentication request message.</span></span> <span data-ttu-id="7a770-202">Cuando se alcanza este número, se anula el protocolo de enlace de PPP y el estado del vínculo se desactiva.</span><span class="sxs-lookup"><span data-stu-id="7a770-202">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="7a770-203">El valor predeterminado es 20.</span><span class="sxs-lookup"><span data-stu-id="7a770-203">The default value is 20.</span></span>
- <span data-ttu-id="7a770-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: define el número máximo de reintentos si el protocolo PPP agota el tiempo de espera antes de enviar otro mensaje de desafío de CHAP.</span><span class="sxs-lookup"><span data-stu-id="7a770-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another CHAP challenge message.</span></span> <span data-ttu-id="7a770-205">Cuando se alcanza este número, se anula el protocolo de enlace de PPP y el estado del vínculo se desactiva.</span><span class="sxs-lookup"><span data-stu-id="7a770-205">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="7a770-206">El valor predeterminado es 20.</span><span class="sxs-lookup"><span data-stu-id="7a770-206">The default value is 20.</span></span>
- <span data-ttu-id="7a770-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: define el número máximo de reintentos si el protocolo PPP agota el tiempo de espera antes de enviar otro mensaje de solicitud de configuración de IPCP.</span><span class="sxs-lookup"><span data-stu-id="7a770-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another IPCP configure request message.</span></span> <span data-ttu-id="7a770-208">Cuando se alcanza este número, se anula el protocolo de enlace de PPP y el estado del vínculo se desactiva.</span><span class="sxs-lookup"><span data-stu-id="7a770-208">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="7a770-209">El valor predeterminado es 20.</span><span class="sxs-lookup"><span data-stu-id="7a770-209">The default value is 20.</span></span>
- <span data-ttu-id="7a770-210">**NX_PPP_MRU**: especifica la unidad de recepción máxima (MRU) para PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-210">**NX_PPP_MRU**: Specifies the Maximum Receive Unit (MRU) for PPP.</span></span> <span data-ttu-id="7a770-211">De forma predeterminada, este valor es 1500 bytes (el valor mínimo).</span><span class="sxs-lookup"><span data-stu-id="7a770-211">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="7a770-212">La aplicación puede establecer esta definición antes de la inclusión de *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="7a770-212">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="7a770-213">**NX_PPP_MINIMUM_MRU**: especifica el número mínimo de MRU recibido en un mensaje de solicitud de configuración de LCP.</span><span class="sxs-lookup"><span data-stu-id="7a770-213">**NX_PPP_MINIMUM_MRU**: Specifies the minimum MRU received in an LCP configure request message.</span></span> <span data-ttu-id="7a770-214">De forma predeterminada, este valor es 1500 bytes (el valor mínimo).</span><span class="sxs-lookup"><span data-stu-id="7a770-214">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="7a770-215">La aplicación puede establecer esta definición antes de la inclusión de *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="7a770-215">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="7a770-216">**NX_PPP_NAME_SIZE**: especifica el tamaño de las cadenas "name" usadas en la autenticación.</span><span class="sxs-lookup"><span data-stu-id="7a770-216">**NX_PPP_NAME_SIZE**: Specifies the size of “name” strings used in authentication.</span></span> <span data-ttu-id="7a770-217">El valor predeterminado se establece en 32 bytes, pero se puede redefinir antes de incluir \*nx_ppp.h.</span><span class="sxs-lookup"><span data-stu-id="7a770-217">The default value is set to 32bytes, but can be redefined prior to inclusion of \*nx_ppp.h.</span></span>
- <span data-ttu-id="7a770-218">**NX_PPP_PASSWORD_SIZE**: especifica el tamaño de las cadenas "password" usadas en la autenticación.</span><span class="sxs-lookup"><span data-stu-id="7a770-218">**NX_PPP_PASSWORD_SIZE**: Specifies the size of “password” strings used in authentication.</span></span> <span data-ttu-id="7a770-219">El valor predeterminado se establece en 32 bytes, pero se puede redefinir antes de la inclusión de *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="7a770-219">The default value is set to 32bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="7a770-220">**NX_PPP_PROTOCOL_TIMEOUT**: define la opción de espera (en segundos) para que la tarea PPP reciba una respuesta a un mensaje de solicitud de protocolo PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-220">**NX_PPP_PROTOCOL_TIMEOUT**: This defines the wait option (in seconds) for the PPP task to receive a response to a PPP protocol request message.</span></span> <span data-ttu-id="7a770-221">El valor predeterminado es 4 segundos.</span><span class="sxs-lookup"><span data-stu-id="7a770-221">The default value is 4 seconds.</span></span>
- <span data-ttu-id="7a770-222">**NX_PPP_RECEIVE_TIMEOUTS**: define el número de veces que la tarea de subprocesos PPP agota el tiempo de espera para recibir el siguiente carácter de una secuencia de mensajes de PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-222">**NX_PPP_RECEIVE_TIMEOUTS**: This defines the number of times the PPP thread task times out waiting to receive the next character in a PPP message stream.</span></span> <span data-ttu-id="7a770-223">Después, PPP libera el paquete y comienza a esperar para recibir el siguiente mensaje de PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-223">Thereafter, PPP releases the packet and begins waiting to receive the next PPP message.</span></span> <span data-ttu-id="7a770-224">El valor predeterminado es 4.</span><span class="sxs-lookup"><span data-stu-id="7a770-224">The default value is 4.</span></span>
- <span data-ttu-id="7a770-225">**NX_PPP_SERIAL_BUFFER_SIZE**: especifica el tamaño del búfer de serie de caracteres de recepción.</span><span class="sxs-lookup"><span data-stu-id="7a770-225">**NX_PPP_SERIAL_BUFFER_SIZE**: Specifies the size of the receive character serial buffer.</span></span> <span data-ttu-id="7a770-226">De forma predeterminada, este valor es 3000 bytes.</span><span class="sxs-lookup"><span data-stu-id="7a770-226">By default, this value is 3,000 bytes.</span></span> <span data-ttu-id="7a770-227">La aplicación puede establecer esta definición antes de la inclusión de *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="7a770-227">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="7a770-228">**NX_PPP_TIMEOUT**: define la opción de espera (en tics de temporizador) para asignar paquetes para transmitir datos, así como almacenar en búfer los datos de serie de PPP en paquetes para enviarlos a la capa de IP.</span><span class="sxs-lookup"><span data-stu-id="7a770-228">**NX_PPP_TIMEOUT**: This defines the wait option (in timer ticks) for allocating packets to transmit data as well as buffer PPP serial data into packets to send to the IP layer.</span></span> <span data-ttu-id="7a770-229">El valor predeterminado es 4\*NX_IP_PERIODIC_RATE (400 tics).</span><span class="sxs-lookup"><span data-stu-id="7a770-229">The default value is 4\*NX_IP_PERIODIC_RATE (400 ticks).</span></span>
- <span data-ttu-id="7a770-230">**NX_PPP_THREAD_TIME_SLICE**: opción de segmento de tiempo para los subprocesos de PPP.</span><span class="sxs-lookup"><span data-stu-id="7a770-230">**NX_PPP_THREAD_TIME_SLICE**: Time-slice option for PPP threads.</span></span> <span data-ttu-id="7a770-231">Este valor es TX_NO_TIME_SLICE de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="7a770-231">By default, this value is TX_NO_TIME_SLICE.</span></span> <span data-ttu-id="7a770-232">La aplicación puede establecer esta definición antes de la inclusión de *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="7a770-232">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="7a770-233">**NX_PPP_VALUE_SIZE**: especifica el tamaño de las cadenas "value" que se usan en la autenticación de CHAP.</span><span class="sxs-lookup"><span data-stu-id="7a770-233">**NX_PPP_VALUE_SIZE**: Specifies the size of “value” strings used in CHAP authentication.</span></span> <span data-ttu-id="7a770-234">El valor predeterminado se establece en 32 bytes, pero se puede redefinir antes de la inclusión de nx_ppp.h.</span><span class="sxs-lookup"><span data-stu-id="7a770-234">The default value is set to 32bytes, but can be redefined prior to inclusion of nx_ppp.h.</span></span>
