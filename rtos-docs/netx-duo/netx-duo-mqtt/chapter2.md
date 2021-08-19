---
title: 'Capítulo 2: Instalación y uso del cliente MQTT de NetX Duo para Azure RTOS'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del cliente MQTT de NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: faf9d84b8b2bce12a99a72198a396b121055a8eef975349f53833a180092e0a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797541"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a>Capítulo 2: Instalación y uso del cliente MQTT de NetX Duo para Azure RTOS

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del cliente MQTT de NetX Duo para Azure RTOS.

## <a name="product-distribution"></a>Distribución del producto

El cliente MQTT para NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). El paquete incluye dos archivos de código fuente: un archivo de inclusión y un archivo que contiene este documento, como se indica a continuación:

- **nxd_mqtt_client.h** Archivo de encabezado del cliente MQTT de NetX Duo.
- **nxd_mqtt_client.c** Archivo de código fuente de C del cliente MQTT de NetX Duo.
- **nxd_mqtt_client.pdf** Descripción del cliente MQTT de NetX Duo.
- **demo_mqtt_client.c** Demostración de MQTT de NetX Duo.

## <a name="mqtt-client-installation"></a>Instalación del cliente MQTT

Para usar el cliente MQTT de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo. Por ejemplo, si NetX Duo está instalado en el directorio " *\threadx\arm7\green*", se deben copiar *nxd_mqtt_client.h* y *nxd_mqtt_client.c* para el cliente MQTT de NetX Duo en este directorio.

## <a name="using-mqtt-client"></a>Uso del cliente MQTT

Es fácil usar el cliente MQTT de NetX Duo. Básicamente, el código de la aplicación debe incluir *nxd_dhcp_client.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX Duo, respectivamente. Una vez incluidos los archivos de encabezado de cliente MQTT, el código de aplicación puede usar los servicios MQTT que se describen más adelante en esta guía. La aplicación también debe incluir *nxd_mqtt_client.c* en el proceso de compilación. Estos archivos se deben compilar de la misma manera que otros archivos de aplicación, y su formulario de objetos se debe vincular junto con los archivos de la aplicación. Esto es todo lo que se necesita para usar el cliente MQTT de NetX Duo.

## <a name="using-mqtt-client-with-netx-secure-tls"></a>Uso del cliente MQTT con NetX Secure TLS

Para usar el cliente MQTT con el módulo NetX Secure TLS, la aplicación debe tener instalado dicho módulo e incluir *nx_secure_tls_api.h* y *nx_crypto.h*. La biblioteca MQTT se debe compilar con el símbolo ***NX_SECURE_ENABLE*** definido.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar el cliente MQTT de NetX Duo. A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas. Los valores predeterminados se muestran, pero se pueden redefinir antes de incluir *nxd_mqtt_client.h.*

- **NX_DISABLE_ERROR_CHECKING** Cuando se define, esta opción quita la comprobación básica de errores del cliente MQTT. Normalmente se utiliza después de depurar la aplicación.
- **NX_SECURE_ENABLE** Cuando se define, el cliente MQTT se crea con compatibilidad con TLS.
La definición de este símbolo requiere la instalación del módulo NetX Secure TLS.
*NX_SECURE_ENABLE* no está habilitado de forma predeterminada.
- **NXD_MQTT_REQUIRE_TLS** Cuando se define, la aplicación debe usar TLS para conectarse al agente MQTT. Esta característica requiere que se defina *NX_SECURE_ENABLE*. De forma predeterminada, este símbolo no se define.
- **NXD_MQTT_MAXIMUM_TRANSMIT_QUEUE_DEPTH**: cuando se define, la profundidad de la cola de transmisión de MQTT está habilitada. Debe ser un número entero positivo.
- **NXD_MQTT_MAX_TOPIC_NAME_LENGTH** En desuso.
- **NXD_MQTT_MAX_MESSAGE_LENGTH** En desuso.
- **NXD_MQTT_KEEPALIVE_TIMER_RATE** Define la velocidad del temporizador de MQTT, en tics del temporizador de ThreadX. Este temporizador se usa para realizar un seguimiento del tiempo transcurrido desde que se envió el último mensaje de control MQTT y envía un mensaje MQTT PINGREQ antes de que expire el tiempo de mantenimiento de conexión. Este temporizador se activa si el cliente se conecta al agente con un valor de temporizador de mantenimiento de la conexión establecido. El valor predeterminado es TX_TIMER_TICKS_PER_SECOND, que es un temporizador de un segundo.
- **NXD_MQTT_PING_TIMEOUT_DELAY** Define el tiempo que el cliente MQTT espera a PINGRESP desde el agente después de enviar MQTT PINGREQ. Si, transcurrido este tiempo de espera, no se recibe PINGRESP, el cliente trata al agente como que no responde y se desconecta de él. El retraso predeterminado del tiempo de espera de PING es TX_TIMER_TICKS_PER_SECOND, que es un segundo.
- **NXD_MQTT_SOCKET_TIMEOUT** Define el tiempo de espera de la llamada de desconexión del socket TCP al desconectarse del servidor MQTT, en tics del temporizador. El valor predeterminado es NX_WAIT_FOREVER.

## <a name="sample-mqtt-program"></a>Programa MQTT de ejemplo

El programa siguiente muestra una aplicación MQTT sencilla. Por motivos de simplicidad, se supone que los códigos de retorno son correctos, por lo que no se realiza ninguna otra comprobación de errores.

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
