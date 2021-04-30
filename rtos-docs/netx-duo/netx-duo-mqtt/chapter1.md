---
title: 'Capítulo 1: Introducción a MQTT de NetX Duo para Azure RTOS'
description: El paquete de cliente MQTT de NetX Duo requiere que NetX Duo (versión 5.10 o posterior) esté instalado y configurado correctamente y que se haya creado la instancia de IP.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e13b997f987e2fd82569bcb1904218908313d70
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814661"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mqtt"></a>Capítulo 1: Introducción a MQTT de NetX Duo para Azure RTOS

## <a name="netx-duo-mqtt-requirements"></a>Requisitos de MQTT de NetX Duo

El paquete de cliente MQTT de NetX Duo Azure RTOS requiere que NetX Duo (versión 5.10 o posterior) esté instalado y configurado correctamente y que se haya creado la instancia de IP. El módulo TCP debe estar habilitado en el sistema. Además, si se requiere seguridad de TLS, el módulo NetX Secure TLS debe configurarse según el parámetro de seguridad requerido por el agente.

## <a name="netx-duo-mqtt-specification"></a>Especificación de MQTT de NetX Duo

La implementación del cliente MQTT de NetX Duo es compatible con la versión 3.1.1 de MQTT de OASIS del <sup>29 de octubre de 2014</sup>. La especificación se puede encontrar en:

- [http://mqtt.org/](http://mqtt.org/)

## <a name="netx-duo-mqtt-basic-operation"></a>Operación básica de MQTT de NetX Duo

MQTT (transporte de telemetría de cola de mensajes) se basa en el modelo de publicador-suscriptor. Un cliente puede publicar información en otros clientes mediante un agente. Un cliente, si está interesado en un tema, puede suscribirse al tema por medio del agente. Un agente es responsable de entregar los mensajes publicados a sus clientes que se suscriben al tema. En este modelo de publicador-suscriptor, varios clientes pueden publicar datos con el mismo tema. Un cliente recibirá un mensaje que publica si el cliente se suscribe al mismo tema.

En función del caso de uso, un cliente puede elegir uno de los tres niveles de QoS al publicar un mensaje:

- **QoS 0**: el mensaje se entrega como máximo una vez. Los mensajes enviados con QoS 0 se pueden perder.
- **QoS 1**: el mensaje se entrega al menos una vez. Los mensajes enviados con QoS 1 se pueden entregar más de una vez.
- **QoS 2**: el mensaje se entrega exactamente una vez. Se garantiza la entrega de los mensajes enviados con QoS 2, sin duplicación.

> [!NOTE]
> Esta implementación de cliente MQTT no admite mensajes de nivel 2 de QoS.

Dado que se garantiza la entrega con QoS 1 y QoS 2, el agente realiza un seguimiento del estado de los mensajes de QoS 1 y QoS 2 enviados a cada cliente. Esto es especialmente importante para los clientes que esperan mensajes de QoS 1 o QoS 2. Es posible que el cliente esté desconectado del agente (por ejemplo, cuando se reinicie el cliente o se pierda temporalmente el vínculo de comunicación). El agente debe almacenar los mensajes de QoS 1 y QoS 2 para que los mensajes se puedan entregar posteriormente una vez que el cliente vuelva a conectarse al agente. Sin embargo, el cliente puede optar por no recibir ningún mensaje obsoleto del agente después de la reconexión. Para ello, puede iniciar la conexión con la marca *clean_session* establecida en ***NX_TRUE**. En este caso, al recibir el mensaje MQTT CONNECT, el agente descartará toda información de sesión asociada a este cliente, incluidos los mensajes de QoS 1 o QoS 2 no entregados o no confirmados. Si la _marca clean_session* está establecida en ***NX_FALSE**_, el servidor reenviará los mensajes de QoS 1 y QoS 2. El cliente MQTT también vuelve a enviar los mensajes no confirmados si clean_session* está establecido en ***NX_TRUE*.** Esta confirmación es diferente de la confirmación de la capa TCP, aunque también sucede. El cliente MQTT envía una confirmación al agente.

Una aplicación crea una instancia del cliente MQTT mediante una llamada a ***nxd_mqtt_client_create()** . Una vez creado el cliente, la aplicación puede conectarse al agente mediante una llamada a _*_nxd_mqtt_client_connect()_*_. Después de conectarse al agente, el cliente puede suscribirse a un tema llamando a _*_nxd_mqtt_client_subscribe()_*_ o publicar un tema llamando a *_nxd_mqtt_client_publish()_ **.

Los mensajes MQTT entrantes se almacenan en la cola de recepción de la instancia del cliente MQTT. La aplicación recupera estos mensajes mediante la llamada a ***nxd_mqtt_client_message_get()***. Si hay mensajes en la cola de recepción, el primer mensaje (por ejemplo, el más antiguo) se devuelve al autor de la llamada. También se devuelve la cadena de tema del mensaje.

> [!NOTE]
> La función ***nxd_mqtt_client_message_get()** no se bloquea si la cola de recepción del cliente MQTT está vacía. La función se devuelve inmediatamente con el código de retorno _*_NXD_MQTT_NO_MESSAGE_**. La aplicación tratará este valor devuelto como una indicación de que la cola de recepción está vacía, y no como un error.

Para evitar el sondeo de mensajes entrantes en la cola de recepción, la aplicación puede registrar una función de devolución de llamada con el cliente MQTT mediante una llamada a ***nxd_mqtt_client_recieve_notify_set()***. La función de devolución de llamada se declara como:

```c
VOID (*receive_notify_callback)(NXD_MQTT_CLIENT *client_ptr, 
    UINT message_count);
```

Cuando el cliente MQTT recibe mensajes del agente, invoca la función de devolución de llamada si la función está establecida. La función de devolución de llamada pasa el puntero al bloque de control del cliente y un valor de recuento de mensajes. El valor de recuento de mensajes indica el número de mensajes MQTT en la cola de recepción. Tenga en cuenta que esta función de devolución de llamada se ejecuta en el contexto del subproceso de cliente MQTT. Por consiguiente, la función de devolución de llamada no debe ejecutar ningún procedimiento que pueda bloquear el subproceso de cliente MQTT. La función de devolución de llamada debe desencadenar el subproceso de la aplicación para llamar a ***nxd_mqtt_client_message_get()*** y recuperar los mensajes.

Para desconectar y finalizar el servicio del cliente MQTT, la aplicación debe usar el servicio ***nxd_mqtt_client_disconnect()** y _*_nxd_mqtt_client_delete()._*_ La llamada a _*_nxd_mqtt_client_disconnect()_*_ simplemente desconecta la conexión TCP al agente. Los mensajes ya recibidos y almacenados en la cola de recepción se liberan. Sin embargo, no se publican mensajes de nivel 1 de QoS en la cola de transmisión. Los mensajes de QoS de nivel 1 se retransmiten tras la conexión, suponiendo que la marca _*_clean_session_*_ está establecida en _ *_NX_FALSE._**

El agente también puede desconectarse del cliente. Cuando finaliza la conexión TCP entre el cliente y el agente, se puede notificar a la aplicación mediante la función de notificación de desconexión. Para usar el mecanismo de notificación, la aplicación instala la función de notificación de desconexión mediante una llamada a ***nxd_mqtt_client_disconnect_notify_set*.** Una vez que se observa una desconexión TCP y se crea la sesión MQTT, se invoca la función de notificación.

La llamada a ***nxd_mqtt_client_delete()*** libera todos los bloques de mensajes de la cola de transmisión y la cola de recepción. También se eliminan los mensajes de nivel 1 de QoS no confirmados.

## <a name="secure-mqtt-connection"></a>Conexión MQTT segura

El cliente MQTT establece una conexión segura con el agente mediante el módulo NetX Secure TLS. El número de puerto predeterminado de MQTT con seguridad TLS es 8883, definido en ***NXD_MQTT_TLS_PORT***.

Para crear una conexión MQTT segura con el agente, es necesario negociar una sesión TLS después de establecer una conexión TCP para que se puedan enviar mensajes MQTT CONNECT al agente. La configuración de la sesión TLS se realiza llamando a ***nxd_mqtt_client_secure_connect()*** y pasando una función de devolución de llamada de configuración TLS definida por el usuario. Durante la fase de conexión de MQTT, una vez establecida la conexión TCP, el cliente invoca la función de devolución de llamada de configuración de TLS para iniciar un proceso de enlace de TLS adecuado. Una vez establecida la sesión TLS, el cliente continúa el mensaje MQTT CONNECT a través del canal seguro.

La función de devolución de llamada definida por el usuario toma cinco valores de entrada y se declara como:

```c
UINT tls_Setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_cerfiticate);
```

A continuación, se muestra una descripción de los parámetros de entrada:

- **client_ptr** Puntero al bloque de control del cliente MQTT.
- **session_ptr** Puntero al bloque de control de sesión de TLS.
- **certificate_ptr** Puntero al bloque de control de certificado. La función de instalación configura este certificado antes de enviarlo al agente.
- **trusted_certificate_ptr** Puntero al certificado de confianza. La función de configuración de TLS configura el certificado de confianza para autenticar el servidor.

En la función de configuración de TLS, la aplicación es responsable de crear una sesión TLS y de configurar la sesión con un certificado adecuado. En el siguiente pseudocódigo se describe un procedimiento de inicio de sesión TLS típico. Para más información sobre el uso de las API de TLS, se hace referencia al lector en la guía de usuario de NetX Secure TLS.

A continuación, se muestra un ejemplo de devolución de llamada de configuración de TLS:

```c
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_pt
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certrifcate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate_ptr)
{
    /* Initialize TLS module */
    nx_secure_tls_initialize();

    /* Create a TLS session */
    nx_secure_tls_session_create(session_ptr, …);

    /* Need to allocate space for the certificate coming in from the broker. */
    memset(certificate_ptr), 0, sizeof(NX_SECURE_TLS_CERTIFICATE));

    nx_secure_tls_remote_certificate_allocate(session_ptr, certificate_ptr);

    /* Add a CA Certificate to our trusted store for verifying incomingserver certificates. */
    nx_secure_tls_certificate_initialize(
        trusted_certificate_ptr,
        ca_cert_der,
        ca_cert_der_len, NULL, 0);
    nx_secure_tls_trusted_certificate_add(session_ptr,
        trusted_certificate));
}
```

## <a name="known-limitations-of-the-netx-duo-mqtt-client"></a>Limitaciones conocidas del cliente MQTT de NetX Duo

- MQTT de NetX Duo no admite el envío ni la recepción de mensajes de nivel 2 de QoS.
- NetX Duo MQTT no admite paquetes encadenados.
