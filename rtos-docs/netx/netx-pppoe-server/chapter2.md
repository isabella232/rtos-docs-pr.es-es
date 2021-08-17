---
title: 'Capítulo 2: Instalación y uso del servidor de PPPoE de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del servidor de PPPoE de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5e93d783299448301c4e79a324ccec01473dbcce3fb96d25d7be352384d4fa53
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796334"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a>Capítulo 2: Instalación y uso del servidor de PPPoE de Azure RTOS NetX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del servidor de PPPoE de Azure RTOS NetX.

## <a name="product-distribution"></a>Distribución del producto

El servidor de PPPoE para NetX está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx). El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:

- **nx_pppoe_server. h**: Archivo de encabezado para el servidor de PPPoE para NetX
- **nx_pppoe_server. h**: Archivo de origen de C para el servidor de PPPoE para NetX
- **nx_pppoe_server.pdf**: Descripción en PDF del servidor de PPPoE para NetX
- **demo_netx_pppoe_server.c**: Demostración del servidor de PPPoE de NetX

## <a name="pppoe-server-installation"></a>Instalación del servidor de PPPoE

Para usar el servidor de PPPoE para NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX. Por ejemplo, si NetX está instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_pppoe_server.h* y *nx_pppoe_server.c* deben copiarse en este directorio.

## <a name="using-pppoe-server"></a>Usar el servidor de PPPoE

Es fácil usar el servidor de PPPoE para NetX. Básicamente, el código de la aplicación debe incluir *nx_pppoe_server. h* después de que incluya *tx_api. h* y *nx_api. h*, con el fin de usar ThreadX y NetX, respectivamente. Una vez que se incluye *nx_pppoe_server.h*, el código de aplicación puede hacer que las llamadas de función del servidor de PPPoE se especifiquen más adelante en esta guía. La aplicación también debe incluir *nx_pppoe_server.c* en el proceso de compilación. Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar el servidor de PPPoE de NetX.

## <a name="small-example-system"></a>Pequeño sistema de ejemplo

El siguiente es un ejemplo que muestra cómo usar el servidor de PPPoE de NetX descrito en la figura 1.1. En este ejemplo, el archivo de inclusión del servidor de PPPoE *nx_pppoe_server.h* se incluye en la línea 50. A continuación, se crea el servidor de PPPoE en *"thread_0_entry*" en la línea 248. Tenga en cuenta que el servidor de PPPoE debe crearse después de crear la instancia de IP. La instancia de IP se crea y se inicializa en la línea 165. El bloque de control del servidor de PPPoE "*pppoe_server*" se definió anteriormente como una variable global en la línea 79. Las funciones de notificación se establecen en la línea 257. Tenga en cuenta que la función de notificación pppoe_session_data_receive debe estar configurada. Después de la creación correcta de la IP y el servidor de PPPoE, se ejecuta el proceso del servidor de PPPoE de establecer una sesión de PPPoE en la llamada a nx_pppoe_server_enable en la línea 272.

En general, el módulo de PPPoE se debe usar con el módulo de PPP. En este ejemplo, el archivo de inclusión del servidor de PPP *nx_ppp.h* se incluye en la línea 49. A continuación, se crea el servidor de PPP en la línea 174. La línea 182 configura la función para enviar el paquete de PPP. La línea 188-200 configura las direcciones IP y define el protocolo PAP. En la línea 115-139 se configura el nombre de usuario y la contraseña para el protocolo PAP.

Una vez establecida la sesión PPPoE. La aplicación puede llamar a nx_pppoe_server_session_get para obtener la información de la sesión (dirección MAC del cliente e identificador de sesión) en la línea 281.

Cuando la aplicación ya no procesa el tráfico de PPP, la aplicación puede llamar a PppCloseInd o nx_pppoe_server_session_terminate para finalizar la sesión de PPPoE.

> [!NOTE]
> En este ejemplo, el servidor de PPPoE funciona con la pila IP normal al mismo tiempo y comparte un controlador Ethernet. Pase el mismo controlador Ethernet para la instancia de IP normal en la línea 165 y la instancia del servidor de PPPoE en la línea 248.

> [!NOTE]
> Las funciones se proporcionan por la implementación de PPPoE para que las llame el software bajo la definición NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.

Si se define, habilita la característica que controla la sesión de PPPoE.

El servidor de PPPoE no responde automáticamente a la solicitud hasta que la aplicación llama a la API específica; si no se define, el servidor de PPPoE responde automáticamente a la solicitud. Se habilita de forma predeterminada en nx_pppoe_server.h.

Observe que debe volver a definir **NX_PHYSICAL_HEADER** en 24 para asegurarse de que hay suficiente espacio para rellenar el encabezado físico. Encabezado físico: 14 (encabezado de Ethernet) + 6 (encabezado de PPPoE) + 2 (encabezado de PPP) + 2 (alineación de cuatro bytes).

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

Figura 1.1 Ejemplo de uso del servidor de PPPoE con NetX

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para crear el servidor de PPPoE para NetX. En la lista siguiente se describe cada una de forma detallada:

- **NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica del servidor de PPPoE. Normalmente se utiliza después de depurar la aplicación.

- **NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: si está definida, esta opción habilita la característica que controla la sesión de PPPoE. El servidor de PPPoE no responde automáticamente a la solicitud hasta que la aplicación llama a la API específica.

- **NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: si está definida, esta opción habilita la característica para inicializar el controlador de Ethernet en el módulo de PPPoE. Se deshabilita de forma predeterminada.

- **NX_PPPOE_SERVER_THREAD_TIME_SLICE**: opción de segmento de tiempo para el subproceso del servidor de PPPoE. Este valor es TX_NO_TIME_SLICE de forma predeterminada.

- **NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: define el número máximo de sesiones de cliente simultáneas. De manera predeterminada, este valor es 10.

- **NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: define el tamaño máximo de Host-Uniq. De manera predeterminada, este valor es 32.

- **NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: define el tamaño máximo del identificador de sesión de retransmisión. De forma predeterminada, este valor es 12.

- **NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: especifica el tamaño mínimo de carga de paquetes para el servidor de PPPoE. Si el tamaño de la carga del paquete es mayor que este valor, puede evitar un encadenamiento de paquetes. De forma predeterminada, este valor es 1520 (tamaño máximo de carga de Ethernet 1500, encabezado de Ethernet 14, CRC 2 y alineación de cuatro bytes 4).

- **NX_PPPOE_SERVER_PACKET_TIMEOUT**: Define la porción de espera (en tics de temporizador) para asignar paquetes o agregar datos a los paquetes. De forma predeterminada, este valor es **NX_IP_PERIODIC_RATE** (100 tics).

- **NX_PPPOE_SERVER_START_SESSION_ID**: define el identificador de la sesión de inicio para asignarlo a la sesión de PPPoE. De forma predeterminada, este valor es 0X4944 (valor ASCII para el identificador).