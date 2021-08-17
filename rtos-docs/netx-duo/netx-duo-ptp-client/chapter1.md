---
title: 'Capítulo 1: Introducción al cliente PTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una introducción al cliente PTP de Azure RTOS NetX Duo.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf7210529121c8e49ff3cabbb7c673288b803f24760096396f32f33d4a9fb7e6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798051"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a>Capítulo 1: Introducción al cliente PTP de Azure RTOS NetX Duo

El componente PTP de Azure RTOS NetX Duo implementa la parte de cliente de la versión 2 del Protocolo de tiempo de precisión (PTP), IEEE 1588-2008. Se usa para sincronizar los relojes entre los MCU de la red local al comunicarse entre sí a través de paquetes de multidifusión IPv4 o IPv6.

## <a name="netx-duo-ptp-client-setup"></a>Configuración del cliente PTP de NetX Duo

Para que funcione correctamente, el paquete del cliente PTP requiere que ya se haya creado una instancia de IP de NetX DUO.

De forma predeterminada, el cliente PTP se une al grupo de multidifusión de IPv4. Para ejecutar el cliente PTP en una red IPv6, `NX_ENABLE_IPV6_MULTICAST` debe definirse al compilar la biblioteca de NetX Duo.

Al crear el cliente PTP, la aplicación debe proporcionar una función de devolución de llamada para controlar las marcas de tiempo de los paquetes entrantes y salientes. Para lograr una alta resolución, recomendamos que las aplicaciones generen marcas de tiempo mediante un temporizador de alta resolución. Para ejecutar PTP en el simulador, se proporciona una implementación basada en software `nx_ptp_client_soft_clock_callback`.

El cliente PTP requiere un grupo de paquetes para la transmisión de mensajes de PTP. El tamaño de carga del grupo de paquetes no debe ser inferior a `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, que es 108 bytes para IPv4 y 128 bytes si IPv6 está habilitado.

Después de crear el cliente PTP, la aplicación puede iniciarlo. La sincronización se realiza en el subproceso auxiliar de PTP. Se puede especificar una función de devolución de llamada del evento. Se invocará cuando se produzca cualquiera de los siguientes eventos.
* Se selecciona un maestro. 
* Se calibra la hora.
* Un maestro agota el tiempo de espera.

## <a name="netx-duo-ptp-client-messages"></a>Mensajes del cliente PTP de en NetX Duo

El cliente PTP de Next Duo implementa solo el mecanismo de retraso de solicitud-respuesta. El cliente PTP abre dos puertos UDP. *319* para el mensaje de **evento** y *320* para el mensaje **general**. Hay cinco tipos de mensajes para este mecanismo.

* **Announce**. Se trata de un mensaje de evento. Se utiliza para la selección del reloj principal.
* **Sync**. Se trata de un mensaje de evento. Se utiliza para enviar la marca de tiempo de origen y calcular el retraso de la ruta de maestro a cliente.
* **Follow_Up**. Se trata de un mensaje general. Es opcional y se usa para corregir la marca de tiempo de origen en el mensaje Sync relacionado. Solo se envía cuando el bit de dos pasos de la marca Sync está activado.
* **Delay_Req**. Se trata de un mensaje de evento. Se envía desde el cliente PTP para calcular el retraso de la ruta de cliente a maestro, al recibir Delay_Resp.
* **Delay_Resp**. Se trata de un mensaje de evento. Se envía desde el maestro al cliente para calcular el retraso de la ruta de cliente a maestro.

*Tenga en cuenta que el algoritmo de "mejor reloj maestro" no está implementado. Solo se acepta el primer reloj maestro cuando el cliente PTP está en estado de escucha.*

## <a name="netx-duo-ptp-client-clock-callback"></a>Devolución de llamada del reloj del cliente PTP de NetX Duo
Para sincronizar el reloj desde el maestro, el cliente PTP necesita un reloj local. Se pasa una función de devolución de llamada del reloj al cliente PTP durante la creación. El formato de la rutina de devolución de llamada del reloj se define a continuación.
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
Los parámetros de entrada se definen de la manera siguiente:
* *client_ptr* apunta al cliente PTP.
* *operation* especifica la operación de devolución de llamada. Los valores válidos se definen como se muestra en la lista siguiente.
  * **NX_PTP_CLIENT_CLOCK_INIT** Inicializa el reloj.
  * **NX_PTP_CLIENT_CLOCK_SET** Establece la marca de tiempo actual especificada por `time_ptr`.
  * **NX_PTP_CLIENT_CLOCK_GET** Devuelve la marca de tiempo actual a `time_ptr`.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrae la marca de tiempo de `packet_ptr` en `time_ptr`.
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Ajusta la marca de tiempo actual menos de *1* segundo.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Marque el `packet_ptr` que necesita para notificar al cliente PTP la marca de tiempo cuando se transmita.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Actualiza el temporizador de software. El reloj de hardware puede pasarlo por alto.
* *time_ptr* apunta a la marca de tiempo.
* *packet_ptr* apunta al paquete.
* *callback_data* apunta a los datos de devolución de llamada opacos.

El tipo de datos NX_PTP_TIME se define como se indica a continuación.
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a>Devolución de llamada de evento de cliente PTP de NetX Duo
La función de devolución de llamada de evento puede configurarse para notificar a la aplicación el estado del cliente PTP. El formato de la rutina de devolución de llamada de evento se define como se muestra a continuación.
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
Los parámetros de entrada son.
* *client_ptr* apunta al cliente PTP.
* *Event* especifica el evento de devolución de llamada. Los valores válidos se definen como:
  * **NX_PTP_CLIENT_EVENT_MASTER** Se selecciona un reloj maestro.
  * **NX_PTP_CLIENT_EVENT_SYNC** El cliente PTP está calibrado.
  * **NX_PTP_CLIENT_EVENT_TIMEOUT** El reloj maestro ha agotado el tiempo de espera.
* *event_data* especifica los datos relacionados con el evento. Cuando el evento es **NX_PTP_CLIENT_EVENT_MASTER**, los datos del evento apuntan a la instancia `NX_PTP_CLIENT_MASTER`. Cuando el evento es **NX_PTP_CLIENT_EVENT_SYNC**, los datos del evento apuntan a la instancia `NX_PTP_CLIENT_SYNC`.

## <a name="netx-duo-ptp-client-communication"></a>Comunicación de cliente PTP de NetX Duo
Como se mencionó anteriormente, el cliente PTP de NetX Duo solo admite el mecanismo de retraso de solicitud-respuesta. Este mecanismo mide el retraso de la ruta media entre el cliente y el reloj maestro como se indica a continuación:
1. El cliente recibe el mensaje *Announce* del maestro y lo selecciona como "mejor maestro".
1. El cliente recibe el mensaje *Sync* del maestro. La marca de tiempo *t1* es la marca de tiempo de origen en este mensaje. La marca de tiempo *t2* se lee desde el reloj local cuando se recibe este mensaje.
1. El cliente recibe el mensaje *Follow_Up* del maestro. Este mensaje es opcional y solo es válido cuando se establecen dos pasos en la marca *Sync*. A continuación, la marca de tiempo *t1* se actualiza a la marca de tiempo de origen en este mensaje.
1. El cliente envía el mensaje *Delay_Req* al maestro. La marca de tiempo *t3* se lee desde el reloj local cuando se transmite el mensaje.
1. El cliente recibe el mensaje *Delay_Resp* del maestro. La marca de tiempo *t4* es la marca de tiempo de recepción de este mensaje.

El retraso de la ruta media se calcula como se muestra a continuación.
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
El desplazamiento desde el maestro se calcula como se muestra a continuación.
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> ****correctionField** _ se omite durante el cálculo._