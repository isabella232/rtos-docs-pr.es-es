---
title: 'Capítulo 2: Instalación y uso del servidor de PPPoE de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del servidor de PPPoE de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5b52164911676b68c67da01d698e41c02730e45a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814445"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a><span data-ttu-id="de6aa-103">Capítulo 2: Instalación y uso del servidor de PPPoE de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="de6aa-103">Chapter 2 - Installation and use of Azure RTOS NetX PPPoE Server</span></span>

<span data-ttu-id="de6aa-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del servidor de PPPoE de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="de6aa-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX PPPoE Server component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="de6aa-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="de6aa-105">Product Distribution</span></span>

<span data-ttu-id="de6aa-106">El servidor de PPPoE para NetX está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="de6aa-106">PPPoE Server for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="de6aa-107">El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="de6aa-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="de6aa-108">**nx_pppoe_server. h**: Archivo de encabezado para el servidor de PPPoE para NetX</span><span class="sxs-lookup"><span data-stu-id="de6aa-108">**nx_pppoe_server.h**: Header file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="de6aa-109">**nx_pppoe_server. h**: Archivo de origen de C para el servidor de PPPoE para NetX</span><span class="sxs-lookup"><span data-stu-id="de6aa-109">**nx_pppoe_server.c**: C Source file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="de6aa-110">**nx_pppoe_server.pdf**: Descripción en PDF del servidor de PPPoE para NetX</span><span class="sxs-lookup"><span data-stu-id="de6aa-110">**nx_pppoe_server.pdf**: PDF description of PPPoE Server for NetX</span></span>
- <span data-ttu-id="de6aa-111">**demo_netx_pppoe_server.c**: Demostración del servidor de PPPoE de NetX</span><span class="sxs-lookup"><span data-stu-id="de6aa-111">**demo_netx_pppoe_server.c**: NetX PPPoE Server demonstration</span></span>

## <a name="pppoe-server-installation"></a><span data-ttu-id="de6aa-112">Instalación del servidor de PPPoE</span><span class="sxs-lookup"><span data-stu-id="de6aa-112">PPPoE Server Installation</span></span>

<span data-ttu-id="de6aa-113">Para usar el servidor de PPPoE para NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="de6aa-113">In order to use PPPoE Server for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="de6aa-114">Por ejemplo, si NetX está instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_pppoe_server.h* y *nx_pppoe_server.c* deben copiarse en este directorio.</span><span class="sxs-lookup"><span data-stu-id="de6aa-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_pppoe_server.h* and *nx_pppoe_server.c* files should be copied into this directory.</span></span>

## <a name="using-pppoe-server"></a><span data-ttu-id="de6aa-115">Usar el servidor de PPPoE</span><span class="sxs-lookup"><span data-stu-id="de6aa-115">Using PPPoE Server</span></span>

<span data-ttu-id="de6aa-116">Es fácil usar el servidor de PPPoE para NetX.</span><span class="sxs-lookup"><span data-stu-id="de6aa-116">Using PPPoE Server for NetX is easy.</span></span> <span data-ttu-id="de6aa-117">Básicamente, el código de la aplicación debe incluir *nx_pppoe_server. h* después de que incluya *tx_api. h* y *nx_api. h*, con el fin de usar ThreadX y NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="de6aa-117">Basically, the application code must include *nx_pppoe_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="de6aa-118">Una vez que se incluye *nx_pppoe_server.h*, el código de aplicación puede hacer que las llamadas de función del servidor de PPPoE se especifiquen más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="de6aa-118">Once *nx_pppoe_server.h* is included, the application code is then able to make the PPPoE Server function calls specified later in this guide.</span></span> <span data-ttu-id="de6aa-119">La aplicación también debe incluir *nx_pppoe_server.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="de6aa-119">The application must also include *nx_pppoe_server.c* in the build process.</span></span> <span data-ttu-id="de6aa-120">Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="de6aa-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="de6aa-121">Esto es todo lo que se necesita para usar el servidor de PPPoE de NetX.</span><span class="sxs-lookup"><span data-stu-id="de6aa-121">This is all that is required to use NetX PPPoE Server.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="de6aa-122">Pequeño sistema de ejemplo</span><span class="sxs-lookup"><span data-stu-id="de6aa-122">Small Example System</span></span>

<span data-ttu-id="de6aa-123">El siguiente es un ejemplo que muestra cómo usar el servidor de PPPoE de NetX descrito en la figura 1.1.</span><span class="sxs-lookup"><span data-stu-id="de6aa-123">The following is an example that illustrates how to use NetX PPPoE Server is described in Figure 1.1.</span></span> <span data-ttu-id="de6aa-124">En este ejemplo, el archivo de inclusión del servidor de PPPoE *nx_pppoe_server.h* se incluye en la línea 50.</span><span class="sxs-lookup"><span data-stu-id="de6aa-124">In this example, the PPPoE Server include file *nx_pppoe_server.h* is brought in at line 50.</span></span> <span data-ttu-id="de6aa-125">A continuación, se crea el servidor de PPPoE en *"thread_0_entry*" en la línea 248.</span><span class="sxs-lookup"><span data-stu-id="de6aa-125">Next, PPPoE Server is created in *"thread_0_entry*" at line 248.</span></span> <span data-ttu-id="de6aa-126">Tenga en cuenta que el servidor de PPPoE debe crearse después de crear la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="de6aa-126">Note that PPPoE Server should be created after create the IP instance.</span></span> <span data-ttu-id="de6aa-127">La instancia de IP se crea y se inicializa en la línea 165.</span><span class="sxs-lookup"><span data-stu-id="de6aa-127">The IP instance is created and initialized line165.</span></span> <span data-ttu-id="de6aa-128">El bloque de control del servidor de PPPoE "*pppoe_server*" se definió anteriormente como una variable global en la línea 79.</span><span class="sxs-lookup"><span data-stu-id="de6aa-128">The PPPoE Server control block "*pppoe_server*" was defined as a global variable at line 79 previously.</span></span> <span data-ttu-id="de6aa-129">Las funciones de notificación se establecen en la línea 257.</span><span class="sxs-lookup"><span data-stu-id="de6aa-129">The notify functions are set at line 257.</span></span> <span data-ttu-id="de6aa-130">Tenga en cuenta que la función de notificación pppoe_session_data_receive debe estar configurada.</span><span class="sxs-lookup"><span data-stu-id="de6aa-130">Note that pppoe_session_data_receive notify function must be set.</span></span> <span data-ttu-id="de6aa-131">Después de la creación correcta de la IP y el servidor de PPPoE, se ejecuta el proceso del servidor de PPPoE de establecer una sesión de PPPoE en la llamada a nx_pppoe_server_enable en la línea 272.</span><span class="sxs-lookup"><span data-stu-id="de6aa-131">After successful creation of IP and PPPoE Server, the PPPoE Server process of establishing a PPPoE session at the call to nx_pppoe_server_enable at line 272.</span></span>

<span data-ttu-id="de6aa-132">En general, el módulo de PPPoE se debe usar con el módulo de PPP.</span><span class="sxs-lookup"><span data-stu-id="de6aa-132">In general, PPPoE module should be used with PPP module.</span></span> <span data-ttu-id="de6aa-133">En este ejemplo, el archivo de inclusión del servidor de PPP *nx_ppp.h* se incluye en la línea 49.</span><span class="sxs-lookup"><span data-stu-id="de6aa-133">In this example, the PPP Server include file *nx_ppp.h* is brought in at line 49.</span></span> <span data-ttu-id="de6aa-134">A continuación, se crea el servidor de PPP en la línea 174.</span><span class="sxs-lookup"><span data-stu-id="de6aa-134">Next, PPP Server is created at line 174.</span></span> <span data-ttu-id="de6aa-135">La línea 182 configura la función para enviar el paquete de PPP.</span><span class="sxs-lookup"><span data-stu-id="de6aa-135">Line 182 setup the function to send PPP packet.</span></span> <span data-ttu-id="de6aa-136">La línea 188-200 configura las direcciones IP y define el protocolo PAP.</span><span class="sxs-lookup"><span data-stu-id="de6aa-136">Line 188-200 setup the IP addresses and define the pap protocol.</span></span> <span data-ttu-id="de6aa-137">En la línea 115-139 se configura el nombre de usuario y la contraseña para el protocolo PAP.</span><span class="sxs-lookup"><span data-stu-id="de6aa-137">Line 115-139 setup the user name and password for pap protocol.</span></span>

<span data-ttu-id="de6aa-138">Una vez establecida la sesión PPPoE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-138">After the PPPoE session established.</span></span> <span data-ttu-id="de6aa-139">La aplicación puede llamar a nx_pppoe_server_session_get para obtener la información de la sesión (dirección MAC del cliente e identificador de sesión) en la línea 281.</span><span class="sxs-lookup"><span data-stu-id="de6aa-139">The application can call nx_pppoe_server_session_get to get the session information (client MAC address and session id) at line 281.</span></span>

<span data-ttu-id="de6aa-140">Cuando la aplicación ya no procesa el tráfico de PPP, la aplicación puede llamar a PppCloseInd o nx_pppoe_server_session_terminate para finalizar la sesión de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-140">When the application no longer process PPP traffic, the application PppCloseInd or nx_pppoe_server_session_terminate to terminate the PPPoE session.</span></span>

> [!NOTE]
> <span data-ttu-id="de6aa-141">En este ejemplo, el servidor de PPPoE funciona con la pila IP normal al mismo tiempo y comparte un controlador Ethernet.</span><span class="sxs-lookup"><span data-stu-id="de6aa-141">In this example, PPPoE Server work with normal IP stack at the same time, and share one Ethernet driver.</span></span> <span data-ttu-id="de6aa-142">Pase el mismo controlador Ethernet para la instancia de IP normal en la línea 165 y la instancia del servidor de PPPoE en la línea 248.</span><span class="sxs-lookup"><span data-stu-id="de6aa-142">Pass the same Ethernet driver for normal IP instance at line 165 and PPPoE Server instance at line 248.</span></span>

> [!NOTE]
> <span data-ttu-id="de6aa-143">Las funciones se proporcionan por la implementación de PPPoE para que las llame el software bajo la definición NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-143">The functions are provided by the PPPoE implementation for calling by the software under defined NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.</span></span>

<span data-ttu-id="de6aa-144">Si se define, habilita la característica que controla la sesión de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-144">If defined, enables the feature that controls the PPPoE session.</span></span>

<span data-ttu-id="de6aa-145">El servidor de PPPoE no responde automáticamente a la solicitud hasta que la aplicación llama a la API específica; si no se define, el servidor de PPPoE responde automáticamente a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="de6aa-145">PPPoE server does not automatically response to the request until application call specific API, if not defined, PPPoE Server automatically responses to the request.</span></span> <span data-ttu-id="de6aa-146">Se habilita de forma predeterminada en nx_pppoe_server.h.</span><span class="sxs-lookup"><span data-stu-id="de6aa-146">It enables by default in nx_pppoe_server.h.</span></span>

<span data-ttu-id="de6aa-147">Observe que debe volver a definir **NX_PHYSICAL_HEADER** en 24 para asegurarse de que hay suficiente espacio para rellenar el encabezado físico.</span><span class="sxs-lookup"><span data-stu-id="de6aa-147">Note, redefine **NX_PHYSICAL_HEADER** to 24 to ensure enough space for filling in physical header.</span></span> <span data-ttu-id="de6aa-148">Encabezado físico: 14 (encabezado de Ethernet) + 6 (encabezado de PPPoE) + 2 (encabezado de PPP) + 2 (alineación de cuatro bytes).</span><span class="sxs-lookup"><span data-stu-id="de6aa-148">Physical header:14(Ethernet header) + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment).</span></span>

```c
/**************************************************************************/
/**************************************************************************/
/**                                                                       */
/** NetX PPPoE Server stack Component                                     */
/**                                                                       */
/** This is a small demo of the high-performance NetX PPPoE Server        */
/** stack. This demo includes IP instance, PPPoE Server and PPP Server    */
/** stack. Create one IP instance includes two interfaces to support      */
/** for normal IP stack and PPPoE Server, PPPoE Server can use the        */
/** mutex of IP instance to send PPPoE message when share one Ethernet    */
/** driver. PPPoE Server work with normal IP instance at the same time.   */
/**                                                                       */
/** Note1: Substitute your Ethernet driver instead of                     */
/** _nx_ram_network_driver before run this demo                           */
/**                                                                       */
/** Note2: Prerequisite for using PPPoE.                                  */
/** Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling  */
/** in physical header. Physical header:14(Ethernet header)               */
/** + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)             */
/**                                                                       */
/**************************************************************************/
/**************************************************************************/


/*****************************************************************/
/*                            NetX Stack                         */
/*****************************************************************/

                                      /***************************/
                                      /* PPP Server              */
                                      /***************************/

                                      /***************************/
                                      /* PPPoE Server            */
                                      /***************************/
/***************************/         /***************************/
/* Normal Ethernet Type    */         /* PPPoE Ethernet Type     */
/***************************/         /***************************/
/***************************/         /***************************/
/* Interface 0             */         /* Interface 1             */
/***************************/         /***************************/

/*****************************************************************/
/*                     Ethernet Dirver                           */
/*****************************************************************/

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_ppp.h"
#include     "nx_pppoe_server.h"

/* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified to match PPPoE moduler under this definition. */
#ifdef NX_PPP_PPPOE_ENABLE

/*   If the driver is not initialized in other module, define */
/*   NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE to initialize the driver in PPPoE module. */
/*   In this demo, the driver has been initialized in IP module. */

#ifdef NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE

/*   NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE: If defined, enables the feature that */
/*   controls the PPPoE session. PPPoE server does not automatically response to the */
/*   request until application call specific API. */

/* Define the block size. */
#define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
#define     DEMO_STACK_SIZE         2048
#define     PPPOE_THREAD_SIZE       2048

/* Define the ThreadX and NetX object control blocks... */
TX_THREAD           thread_0;

/* Define the packet pool and IP instance for normal IP instnace. */
NX_PACKET_POOL      pool_0;
NX_IP               ip_0;

/* Define the PPP Server instance. */
NX_PPP              ppp_server;

/* Define the PPPoE Server instance. */
NX_PPPOE_SERVER     pppoe_server;

/* Define the counters. */
CHAR                *pointer;
ULONG               error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);

/***** Substitute your PPP driver entry function here *********/
extern void     _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);

/***** Substitute your Ethernet driver entry function here *********/
extern void     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define the callback functions. */
void     PppDiscoverReq(UINT interfaceHandle);
void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data);
void     PppCloseRsp(UINT interfaceHandle);
void     PppCloseReq(UINT interfaceHandle);
void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id);
void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data);

/* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP. */
/* Functions to be provided by PPP for calling by the PPPoE Stack. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

UINT verify_login(CHAR *name, CHAR *password)
{

    if ((name[0] == 'm') &&
        (name[1] == 'y') &&
        (name[2] == 'n') &&
        (name[3] == 'a') &&
        (name[4] == 'm') &&
        (name[5] == 'e') &&
        (name[6] == (CHAR) 0) &&
        (password[0] == 'm') &&
        (password[1] == 'y') &&
        (password[2] == 'p') &&
        (password[3] == 'a') &&
        (password[4] == 's') &&
        (password[5] == 's') &&
        (password[6] == 'w') &&
        (password[7] == 'o') &&
        (password[8] == 'r') &&
        (password[9] == 'd') &&
        (password[10] == (CHAR) 0))
            return(NX_SUCCESS);
    else
        return(NX_PPP_ERROR);
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{

    UINT status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool for normal IP instance. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
                                    (1536 + sizeof(NX_PACKET)),
                                    pointer, NX_PACKET_POOL_SIZE);
                                    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create an normal IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 43),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create the PPP instance. */
    status = nx_ppp_create(&ppp_server, "PPP Instance", &ip_0, pointer, 2048, 1,
                            &pool_0, NX_NULL, NX_NULL);
    pointer = pointer + 2048;

    /* Check for PPP create error. */
    if (status)
        error_counter++;

    /* Set the PPP packet send function. */
    status = nx_ppp_packet_send_set(&ppp_server, ppp_server_packet_send);

    /* Check for PPP packet send function set error. */
    if (status)
        error_counter++;

    /* Define IP address. This PPP instance is effectively the server since it has both IP addresses. */
    status = nx_ppp_ip_address_assign(&ppp_server, IP_ADDRESS(192, 168, 10, 43),                                         IP_ADDRESS(192, 168, 10, 44));

    /* Check for PPP IP address assign error. */
    if (status)
        error_counter++;

    /* Setup PAP, this PPP instance is effectively the server since it will verify the name and password. */
    status = nx_ppp_pap_enable(&ppp_server, NX_NULL, verify_login);

    /* Check for PPP PAP enable error. */
    if (status)
        error_counter++;

    /* Attach an interface for PPP. */
    status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", 
                            IP_ADDRESS(0, 0, 0, 0), 0, nx_ppp_driver);

    /* Check for error. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for Normal IP Instance. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
        error_counter++;

    /* Enable ICMP */
    status = nx_icmp_enable(&ip_0);
    if(status)
        error_counter++;

    /* Enable UDP traffic. */
    status = nx_udp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Enable TCP traffic. */
    status = nx_tcp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;
}

/* Define the test threads. */

void     thread_0_entry(ULONG thread_input)
{
UINT     status;
ULONG    ip_status;

    /* Create the PPPoE instance. */
    status = nx_pppoe_server_create(&pppoe_server, (UCHAR *)"PPPoE Server", &ip_0, 0,
                    _nx_ram_network_driver, &pool_0, pointer, PPPOE_THREAD_SIZE, 4);
    pointer = pointer + PPPOE_THREAD_SIZE;
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the callback notify function. */
    status = nx_pppoe_server_callback_notify_set(&pppoe_server, PppDiscoverReq,
        PppOpenReq, PppCloseRsp, PppCloseReq, PppTransmitDataReq, PppReceiveDataRsp);

    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call function function to set the default service Name. */
        /* PppInitInd(length, aData); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

    /* Enable PPPoE Server. */
    status = nx_pppoe_server_enable(&pppoe_server);
    if (status)
    {
        error_counter++;
        return;
    }

    /* Get the PPPoE Client physical address and Session ID after establish PPPoE Session. */
    /*
        status = nx_pppoe_server_session_get(&pppoe_server, interfaceHandle, &client_mac_msw, &client_mac_lsw, &session_id);
        if (status)
            error_counter++;
    */

    /* Wait for the link to come up. */
    status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                            &ip_status, NX_WAIT_FOREVER);
    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to terminate the PPPoE Session. */
        /* PppCloseInd(interfaceHandle, causeCode); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

}

void     PppDiscoverReq(UINT interfaceHandle)
{

    /* Receive the PPPoE Discovery Initiation Message. */
    
    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to define the Service Name field of the PADO packet. */
        PppDiscoverCnf(0, NX_NULL, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data)
{

    /* Get the notify that receive the PPPoE Discovery Request Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to accept the PPPoE session. */
        PppOpenCnf(NX_TRUE, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseRsp(UINT interfaceHandle)
{

    /* Get the notify that receive the PPPoE Discovery Terminate Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to confirm that the handle has been freed. */
        PppCloseCnf(interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseReq(UINT interfaceHandle)
{

    /* Get the notify that PPPoE Discovery Terminate Message has been sent. */

}

void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id)
{

    NX_PACKET *packet_ptr;

    /* Get the notify that receive the PPPoE Session data. */

    /* Call PPP Server to receive the PPP data fame. */
    packet_ptr = (NX_PACKET *)(packet_id);
    nx_ppp_packet_receive(&ppp_server, packet_ptr);

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to confirm that the data has been processed. */
        PppTransmitDataCnf(interfaceHandle, data, packet_id);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data)
{

    /* Get the notify that the PPPoE Session data has been sent. */

}

/* PPP Server send function. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr)
{

    /* For Express Logic's PPP test, the session should be the first session, so set interfaceHandle as 0. */
    UINT interfaceHandle = 0;

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        while(packet_ptr)
        {

            /* Call functions to be provided by PPPoE for TTP. */
            PppReceiveDataInd(interfaceHandle, (packet_ptr -> nx_packet_append_ptr -
            packet_ptr -> nx_packet_prepend_ptr), packet_ptr -> nx_packet_prepend_ptr);

            /* Move to the next packet structure. */
            packet_ptr = packet_ptr -> nx_packet_next;
        }
    #else
        /* Directly Call PPPoE send function to send out the data through PPPoE module. */
        nx_pppoe_server_session_packet_send(&pppoe_server, interfaceHandle, packet_ptr);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}
#endif /* NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE */

#endif /* NX_PPP_PPPOE_ENABLE */
```

<span data-ttu-id="de6aa-149">Figura 1.1 Ejemplo de uso del servidor de PPPoE con NetX</span><span class="sxs-lookup"><span data-stu-id="de6aa-149">Figure 1.1 Example of PPPoE Server use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="de6aa-150">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="de6aa-150">Configuration Options</span></span>

<span data-ttu-id="de6aa-151">Hay varias opciones de configuración para crear el servidor de PPPoE para NetX.</span><span class="sxs-lookup"><span data-stu-id="de6aa-151">There are several configuration options for building PPPoE Server for NetX.</span></span> <span data-ttu-id="de6aa-152">En la lista siguiente se describe cada una de forma detallada:</span><span class="sxs-lookup"><span data-stu-id="de6aa-152">The following list describes each in detail:</span></span>

- <span data-ttu-id="de6aa-153">**NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica del servidor de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-153">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPPoE Server error checking.</span></span> <span data-ttu-id="de6aa-154">Normalmente se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="de6aa-154">It is typically used after the application has been debugged.</span></span>

- <span data-ttu-id="de6aa-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: si está definida, esta opción habilita la característica que controla la sesión de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: If defined, enables the feature that controls the PPPoE session.</span></span> <span data-ttu-id="de6aa-156">El servidor de PPPoE no responde automáticamente a la solicitud hasta que la aplicación llama a la API específica.</span><span class="sxs-lookup"><span data-stu-id="de6aa-156">PPPoE server does not automatically response to the request until application call specific API.</span></span>

- <span data-ttu-id="de6aa-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: si está definida, esta opción habilita la característica para inicializar el controlador de Ethernet en el módulo de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: If defined, enables the feature to initialize the Ethernet driver in PPPoE module.</span></span> <span data-ttu-id="de6aa-158">Se deshabilita de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="de6aa-158">It disables by default.</span></span>

- <span data-ttu-id="de6aa-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE**: opción de segmento de tiempo para el subproceso del servidor de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE**: Time-slice option for PPPoE Server thread.</span></span> <span data-ttu-id="de6aa-160">Este valor es TX_NO_TIME_SLICE de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="de6aa-160">By default, this value is TX_NO_TIME_SLICE.</span></span>

- <span data-ttu-id="de6aa-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: define el número máximo de sesiones de cliente simultáneas.</span><span class="sxs-lookup"><span data-stu-id="de6aa-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: This defines the max number of concurrent client sessions.</span></span> <span data-ttu-id="de6aa-162">De manera predeterminada, este valor es 10.</span><span class="sxs-lookup"><span data-stu-id="de6aa-162">By default, this value is 10.</span></span>

- <span data-ttu-id="de6aa-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: define el tamaño máximo de Host-Uniq.</span><span class="sxs-lookup"><span data-stu-id="de6aa-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: This defines the max size of Host-Uniq.</span></span> <span data-ttu-id="de6aa-164">De manera predeterminada, este valor es 32.</span><span class="sxs-lookup"><span data-stu-id="de6aa-164">By default, this value is 32.</span></span>

- <span data-ttu-id="de6aa-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: define el tamaño máximo del identificador de sesión de retransmisión. De forma predeterminada, este valor es 12.</span><span class="sxs-lookup"><span data-stu-id="de6aa-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: This defines the max size of Relay-Session-Id. By default, this value is 12.</span></span>

- <span data-ttu-id="de6aa-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: especifica el tamaño mínimo de carga de paquetes para el servidor de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: Specifies the Minimum packet payload size for PPPoE Server.</span></span> <span data-ttu-id="de6aa-167">Si el tamaño de la carga del paquete es mayor que este valor, puede evitar un encadenamiento de paquetes.</span><span class="sxs-lookup"><span data-stu-id="de6aa-167">If the packet payload size is greater than this value, can avoid packet chained.</span></span> <span data-ttu-id="de6aa-168">De forma predeterminada, este valor es 1520 (tamaño máximo de carga de Ethernet 1500, encabezado de Ethernet 14, CRC 2 y alineación de cuatro bytes 4).</span><span class="sxs-lookup"><span data-stu-id="de6aa-168">By default, this value is 1520 (Maximum Payload Size of Ethernet 1500, Ethernet Header 14, CRC 2 and Four-byte alignment 4).</span></span>

- <span data-ttu-id="de6aa-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT**: Define la porción de espera (en tics de temporizador) para asignar paquetes o agregar datos a los paquetes.</span><span class="sxs-lookup"><span data-stu-id="de6aa-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT**: This defines the wait potion(in timer ticks) for allocating packets or appending data into packets.</span></span> <span data-ttu-id="de6aa-170">De forma predeterminada, este valor es **NX_IP_PERIODIC_RATE** (100 tics).</span><span class="sxs-lookup"><span data-stu-id="de6aa-170">By default, this value is **NX_IP_PERIODIC_RATE** (100 ticks).</span></span>

- <span data-ttu-id="de6aa-171">**NX_PPPOE_SERVER_START_SESSION_ID**: define el identificador de la sesión de inicio para asignarlo a la sesión de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="de6aa-171">**NX_PPPOE_SERVER_START_SESSION_ID**: This defines the start Session ID for assigning to the PPPoE Session.</span></span> <span data-ttu-id="de6aa-172">De forma predeterminada, este valor es 0X4944 (valor ASCII para el identificador).</span><span class="sxs-lookup"><span data-stu-id="de6aa-172">By default, this value is 0X4944(ASCII value for ID).</span></span>