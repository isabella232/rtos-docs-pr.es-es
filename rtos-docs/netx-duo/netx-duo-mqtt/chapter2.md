---
title: 'Capítulo 2: Instalación y uso del cliente MQTT de NetX Duo para Azure RTOS'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del cliente MQTT de NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cde19a0e84f369f1199ea4027fa09e6bd038e837
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814658"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a><span data-ttu-id="8fa89-103">Capítulo 2: Instalación y uso del cliente MQTT de NetX Duo para Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="8fa89-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo MQTT client</span></span>

<span data-ttu-id="8fa89-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del cliente MQTT de NetX Duo para Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="8fa89-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo MQTT client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="8fa89-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="8fa89-105">Product Distribution</span></span>

<span data-ttu-id="8fa89-106">El cliente MQTT para NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="8fa89-106">MQTT Client for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="8fa89-107">El paquete incluye dos archivos de código fuente: un archivo de inclusión y un archivo que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="8fa89-107">The package includes two source files, one include file, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="8fa89-108">**nxd_mqtt_client.h** Archivo de encabezado del cliente MQTT de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-108">**nxd_mqtt_client.h** Header file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="8fa89-109">**nxd_mqtt_client.c** Archivo de código fuente de C del cliente MQTT de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-109">**nxd_mqtt_client.c** C Source file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="8fa89-110">**nxd_mqtt_client.pdf** Descripción del cliente MQTT de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-110">**nxd_mqtt_client.pdf** Description of MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="8fa89-111">**demo_mqtt_client.c** Demostración de MQTT de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-111">**demo_mqtt_client.c** NetX Duo MQTT demonstration</span></span>

## <a name="mqtt-client-installation"></a><span data-ttu-id="8fa89-112">Instalación del cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="8fa89-112">MQTT Client Installation</span></span>

<span data-ttu-id="8fa89-113">Para usar el cliente MQTT de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-113">In order to use MQTT Client for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="8fa89-114">Por ejemplo, si NetX Duo está instalado en el directorio " *\threadx\arm7\green*", se deben copiar *nxd_mqtt_client.h* y *nxd_mqtt_client.c* para el cliente MQTT de NetX Duo en este directorio.</span><span class="sxs-lookup"><span data-stu-id="8fa89-114">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_mqtt_client.h* and *nxd_mqtt_client.c* for NetX Duo MQTT Client need to be copied into this directory.</span></span>

## <a name="using-mqtt-client"></a><span data-ttu-id="8fa89-115">Uso del cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="8fa89-115">Using MQTT Client</span></span>

<span data-ttu-id="8fa89-116">Es fácil usar el cliente MQTT de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-116">Using MQTT Client for NetX Duo is easy.</span></span> <span data-ttu-id="8fa89-117">Básicamente, el código de la aplicación debe incluir *nxd_dhcp_client.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX Duo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8fa89-117">Basically, the application code must include *nxd_mqtt_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX, and NetX Duo, respectively.</span></span> <span data-ttu-id="8fa89-118">Una vez incluidos los archivos de encabezado de cliente MQTT, el código de aplicación puede usar los servicios MQTT que se describen más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="8fa89-118">Once the MQTT Client header files are included, the application code is then able to use the MQTT services described later in this guide.</span></span> <span data-ttu-id="8fa89-119">La aplicación también debe incluir *nxd_mqtt_client.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="8fa89-119">The application must also include *nxd_mqtt_client.c* in the build process.</span></span> <span data-ttu-id="8fa89-120">Estos archivos se deben compilar de la misma manera que otros archivos de aplicación, y su formulario de objetos se debe vincular junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8fa89-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="8fa89-121">Esto es todo lo que se necesita para usar el cliente MQTT de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-121">This is all that is required to use NetX Duo MQTT Client.</span></span>

## <a name="using-mqtt-client-with-netx-secure-tls"></a><span data-ttu-id="8fa89-122">Uso del cliente MQTT con NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="8fa89-122">Using MQTT Client with NetX Secure TLS</span></span>

<span data-ttu-id="8fa89-123">Para usar el cliente MQTT con el módulo NetX Secure TLS, la aplicación debe tener instalado dicho módulo e incluir *nx_secure_tls_api.h* y *nx_crypto.h*.</span><span class="sxs-lookup"><span data-stu-id="8fa89-123">To use MQTT client with NetX Secure TLS module, application must have NetX Secure TLS module installed, and include *nx_secure_tls_api.h* and *nx_crypto.h*.</span></span> <span data-ttu-id="8fa89-124">La biblioteca MQTT se debe compilar con el símbolo ***NX_SECURE_ENABLE*** definido.</span><span class="sxs-lookup"><span data-stu-id="8fa89-124">The MQTT library must be built with the symbol ***NX_SECURE_ENABLE*** defined.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="8fa89-125">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="8fa89-125">Configuration Options</span></span>

<span data-ttu-id="8fa89-126">Hay varias opciones de configuración para compilar el cliente MQTT de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-126">There are several configuration options for building MQTT client for NetX Duo.</span></span> <span data-ttu-id="8fa89-127">A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas.</span><span class="sxs-lookup"><span data-stu-id="8fa89-127">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="8fa89-128">Los valores predeterminados se muestran, pero se pueden redefinir antes de incluir *nxd_mqtt_client.h.*</span><span class="sxs-lookup"><span data-stu-id="8fa89-128">The default values are listed, but can be redefined prior to inclusion of *nxd_mqtt_client.h.*</span></span>

- <span data-ttu-id="8fa89-129">**NX_DISABLE_ERROR_CHECKING** Cuando se define, esta opción quita la comprobación básica de errores del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="8fa89-129">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic MQTT client error checking.</span></span> <span data-ttu-id="8fa89-130">Normalmente se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8fa89-130">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="8fa89-131">**NX_SECURE_ENABLE** Cuando se define, el cliente MQTT se crea con compatibilidad con TLS.</span><span class="sxs-lookup"><span data-stu-id="8fa89-131">**NX_SECURE_ENABLE**: Defined, MQTT Client is built with TLS support.</span></span>
<span data-ttu-id="8fa89-132">La definición de este símbolo requiere la instalación del módulo NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="8fa89-132">Defining this symbol requires NetX Secure TLS module to be installed.</span></span>
<span data-ttu-id="8fa89-133">*NX_SECURE_ENABLE* no está habilitado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="8fa89-133">*NX_SECURE_ENABLE* is not enabled by default.\*\*</span></span>
- <span data-ttu-id="8fa89-134">**NXD_MQTT_REQUIRE_TLS** Cuando se define, la aplicación debe usar TLS para conectarse al agente MQTT.</span><span class="sxs-lookup"><span data-stu-id="8fa89-134">**NXD_MQTT_REQUIRE_TLS**: Defined, application must use TLS to connect to MQTT broker.</span></span> <span data-ttu-id="8fa89-135">Esta característica requiere que se defina *NX_SECURE_ENABLE*.</span><span class="sxs-lookup"><span data-stu-id="8fa89-135">This feature requires *NX_SECURE_ENABLE* defined.</span></span> <span data-ttu-id="8fa89-136">De forma predeterminada, este símbolo no se define.</span><span class="sxs-lookup"><span data-stu-id="8fa89-136">By default, this symbol is not defined.</span></span>
- <span data-ttu-id="8fa89-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH** En desuso.</span><span class="sxs-lookup"><span data-stu-id="8fa89-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="8fa89-138">**NXD_MQTT_MAX_MESSAGE_LENGTH** En desuso.</span><span class="sxs-lookup"><span data-stu-id="8fa89-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="8fa89-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE** Define la velocidad del temporizador de MQTT, en tics del temporizador de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8fa89-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: Defines the MQTT timer rate, in ThreadX timer ticks.</span></span> <span data-ttu-id="8fa89-140">Este temporizador se usa para realizar un seguimiento del tiempo transcurrido desde que se envió el último mensaje de control MQTT y envía un mensaje MQTT PINGREQ antes de que expire el tiempo de mantenimiento de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fa89-140">This timer is used to keep track of the time since last MQTT control message was sent, and sends out an MQTT PINGREQ message before the keep-alive time expires.</span></span> <span data-ttu-id="8fa89-141">Este temporizador se activa si el cliente se conecta al agente con un valor de temporizador de mantenimiento de la conexión establecido.</span><span class="sxs-lookup"><span data-stu-id="8fa89-141">This timer is activated if the client connects to the broker with a keep-alive timer value set.</span></span> <span data-ttu-id="8fa89-142">El valor predeterminado es TX_TIMER_TICKS_PER_SECOND, que es un temporizador de un segundo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-142">The default value is TX_TIMER_TICKS_PER_SECOND, which is a one-second timer.</span></span>
- <span data-ttu-id="8fa89-143">**NXD_MQTT_PING_TIMEOUT_DELAY** Define el tiempo que el cliente MQTT espera a PINGRESP desde el agente después de enviar MQTT PINGREQ.</span><span class="sxs-lookup"><span data-stu-id="8fa89-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: Defines the time the MQTT client waits for PINGRESP from the broker after it sends out MQTT PINGREQ.</span></span> <span data-ttu-id="8fa89-144">Si, transcurrido este tiempo de espera, no se recibe PINGRESP, el cliente trata al agente como que no responde y se desconecta de él.</span><span class="sxs-lookup"><span data-stu-id="8fa89-144">If no PINGRESP is received after this timeout delay, the client treats the broker as non-responsive and disconnects itself from the broker.</span></span> <span data-ttu-id="8fa89-145">El retraso predeterminado del tiempo de espera de PING es TX_TIMER_TICKS_PER_SECOND, que es un segundo.</span><span class="sxs-lookup"><span data-stu-id="8fa89-145">The default PING timeout delay is TX_TIMER_TICKS_PER_SECOND, which is one second.</span></span>
- <span data-ttu-id="8fa89-146">**NXD_MQTT_SOCKET_TIMEOUT** Define el tiempo de espera de la llamada de desconexión del socket TCP al desconectarse del servidor MQTT, en tics del temporizador.</span><span class="sxs-lookup"><span data-stu-id="8fa89-146">**NXD_MQTT_SOCKET_TIMEOUT**: Defines the time out in the TCP socket disconnect call when disconnecting from the MQTT server in timer ticks.</span></span> <span data-ttu-id="8fa89-147">El valor predeterminado es NX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="8fa89-147">The default value is NX_WAIT_FOREVER.</span></span>

## <a name="sample-mqtt-program"></a><span data-ttu-id="8fa89-148">Programa MQTT de ejemplo</span><span class="sxs-lookup"><span data-stu-id="8fa89-148">Sample MQTT program</span></span>

<span data-ttu-id="8fa89-149">El programa siguiente muestra una aplicación MQTT sencilla.</span><span class="sxs-lookup"><span data-stu-id="8fa89-149">The following program illustrates a simple MQTT application.</span></span> <span data-ttu-id="8fa89-150">Por motivos de simplicidad, se supone que los códigos de retorno son correctos, por lo que no se realiza ninguna otra comprobación de errores.</span><span class="sxs-lookup"><span data-stu-id="8fa89-150">For simplicity, the return codes are assumed to be successful, therefore no further error checking is done.</span></span>

```c
#define LOCAL_SERVER_ADDRESS (IP_ADDRESS(192, 168, 1, 81))

/*******************************************************/
/* IOT MQTT Client Example                             */
/*******************************************************/
#define DEMO_STACK_SIZE 2048
#define CLIENT_ID_STRING "mytestclient"
#define MQTT_CLIENT_STACK_SIZE 4096
#define STRLEN(p) (sizeof(p) - 1)

/* Declare the MQTT thread stack space. */
static ULONG mqtt_client_stack[MQTT_CLIENT_STACK_SIZE / sizeof(ULONG)];

/* Declare the MQTT client control block. */
static NXD_MQTT_CLIENT mqtt_client;

/* Define the symbol for signaling a received message. */

/* Define the test threads. */

#define TOPIC_NAME "topic"

#define MESSAGE_STRING "This is a message. "

/* Define the priority of the MQTT internal thread. */
#define MQTT_THREAD_PRIORTY 2

/* Define the MQTT keep alive timer for 5 minutes */
#define MQTT_KEEP_ALIVE_TIMER 300
#define QOS0 0
#define QOS1 1

/* Declare event flag, which is used in this demo. */
TX_EVENT_FLAGS_GROUP mqtt_app_flag;
#define DEMO_MESSAGE_EVENT 1
#define DEMO_ALL_EVENTS 3

/* Declare buffers to hold message and topic. */
static UCHAR message_buffer[NXD_MQTT_MAX_MESSAGE_LENGTH];
static UCHAR topic_buffer[NXD_MQTT_MAX_TOPIC_NAME_LENGTH];

/* Declare the disconnect notify function. */
static VOID my_disconnect_func(NXD_MQTT_CLIENT *client_ptr)
{
    printf("client disconnected from server\n");
}

static VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr, UINT number_of_messages)
{
    tx_event_flags_set(&mqtt_app_flag, DEMO_MESSAGE_EVENT, TX_OR);
    return;
}

static ULONG error_counter;
void demo_mqtt_client_local(NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr)
{
    UINT status;
    NXD_ADDRESS server_ip;
    ULONG events;
    UINT topic_length, message_length;

    /* Create MQTT client instance. */
    nxd_mqtt_client_create(&mqtt_client, "my_client",
        CLIENT_ID_STRING, STRLEN(CLIENT_ID_STRING), ip_ptr, pool_ptr,
        (VOID*)mqtt_client_stack, sizeof(mqtt_client_stack),
        MQTT_THREAD_PRIORTY, NX_NULL, 0);

    /* Register the disconnect notification function. */
    nxd_mqtt_client_disconnect_notify_set(&mqtt_client, my_disconnect_func);

    /* Create an event flag for this demo. */
    status = tx_event_flags_create(&mqtt_app_flag, "my app event");
    server_ip.nxd_ip_version = 4;
    server_ip.nxd_ip_address.v4 = LOCAL_SERVER_ADDRESS;

    /* Start the connection to the server. */
    nxd_mqtt_client_connect(&mqtt_client, &server_ip, NXD_MQTT_PORT, 
        MQTT_KEEP_ALIVE_TIMER, 0, NX_WAIT_FOREVER);

    /* Subscribe to the topic with QoS level 0. */
    nxd_mqtt_client_subscribe(&mqtt_client, TOPIC_NAME, STRLEN(TOPIC_NAME),
        QOS0);

    /* Set the receive notify function. */
    nxd_mqtt_client_receive_notify_set(&mqtt_client, my_notify_func);

    /* Publish a message with QoS Level 1. */
    nxd_mqtt_client_publish(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME), (CHAR*)MESSAGE_STRING, 
        STRLEN(MESSAGE_STRING), 0, QOS1, NX_WAIT_FOREVER);

    /* Now wait for the broker to publish the message. */
    tx_event_flags_get(&mqtt_app_flag, DEMO_ALL_EVENTS,
        TX_OR_CLEAR, &events, TX_WAIT_FOREVER);

    if(events & DEMO_MESSAGE_EVENT)
    {
        nxd_mqtt_client_message_get(&mqtt_client, topic_buffer,
            sizeof(topic_buffer), &topic_length, message_buffer,
            sizeof(message_buffer), &message_length);

        topic_buffer[topic_length] = 0;

        message_buffer[message_length] = 0;

        printf("topic = %s, message = %s\n", topic_buffer, message_buffer);
    }

    /* Now unsubscribe the topic. */
    nxd_mqtt_client_unsubscribe(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME));

    /* Disconnect from the broker. */
    nxd_mqtt_client_disconnect(&mqtt_client);

    /* Delete the client instance, release all the resources. */
    nxd_mqtt_client_delete(&mqtt_client);
    return;
}
```
