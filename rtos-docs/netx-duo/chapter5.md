---
title: 'Capítulo 5: Controladores de red de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de los controladores de red para Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a0d18929f33f15a342e8fb8b3d01d4ce934d6ec7dc287707f960adb36fb4f44b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788854"
---
# <a name="chapter-5---azure-rtos-netx-duo-network-drivers"></a>Capítulo 5: Controladores de red de Azure RTOS NetX Duo

Este capítulo contiene una descripción de los controladores de red para Azure RTOS NetX Duo. La información presentada está diseñada para ayudar a los desarrolladores a escribir controladores de red específicos de la aplicación para NetX Duo.

## <a name="driver-introduction"></a>Introducción a los controladores

La estructura NX_IP contiene todo lo necesario para administrar una única instancia de IP. Aquí se incluye información general sobre el protocolo TCP/IP, así como la rutina de entrada del controlador de red física específico de la aplicación. La rutina de entrada del controlador se define durante el servicio de ***nx_ip_create** _. Para agregar dispositivos adicionales a la instancia de IP, se usa el servicio _ *_nx_ip_interface_attach_**.

La comunicación entre NetX Duo y el controlador de red de la aplicación se realiza a través de la estructura de la solicitud de **NX_IP_DRIVER**. Normalmente, esta estructura se define localmente en la pila del autor de la llamada y, por tanto, se libera después de que se devuelvan tanto el controlador como la función de llamada. La estructura se define como se ve a continuación.

```c
typedef struct NX_IP_DRIVER_STRUCT
{
      UINT           nx_ip_driver_command;
      UINT           nx_ip_driver_status;
      ULONG          nx_ip_driver_physical_address_msw;
      ULONG          nx_ip_driver_physical_address_lsw;
      NX_PACKET      *nx_ip_driver_packet;
      ULONG          *nx_ip_driver_return_ptr;
      NX_IP          *nx_ip_driver_ptr;
      NX_INTERFACE   *nx_ip_driver_interface;01
} NX_IP_DRIVER;
```
## <a name="driver-entry"></a>Entrada de controlador 

NetX Duo invoca la función de entrada del controlador de red no solo para la inicialización del controlador, sino también para enviar paquetes y para diversas operaciones de control y estado, entre las que se incluyen la inicialización y habilitación del dispositivo de red. NetX Duo emite comandos para el controlador de red mediante el establecimiento del campo ***nx_ip_driver_command** _ en la estructura de solicitud _ *NX_IP_DRIVER**. La función de entrada del controlador tiene el formato siguiente:

```c
VOID my_driver_entry(NX_IP_DRIVER *request);
```
## <a name="driver-requests"></a>Solicitudes de controlador

NetX Duo crea la solicitud de controlador con un comando específico e invoca la función de entrada del controlador para ejecutar el comando. Dado que cada controlador de red tiene una sola función de entrada, NetX Duo realiza todas las solicitudes a través de la estructura de datos de la solicitud del controlador. El miembro ***nx_ip_driver_command** _ de la estructura de datos de solicitud de controlador ( _*NX_IP_DRIVER**) define la solicitud. La información de estado se devuelve al autor de la llamada en el miembro **_nx_ip_driver_status_*_. Si el valor de este campo es _*NX_SUCCESS**, la solicitud del controlador se completó correctamente.

NetX Duo serializa todo el acceso al controlador. Por consiguiente, el controlador no necesita controlar varios subprocesos mediante la llamada asincrónica a la función de entrada. Tenga en cuenta que la función de controlador de dispositivo se ejecuta con la exclusión mutua de IP bloqueada. Por consiguiente, la función interna del controlador de dispositivo no se bloqueará automáticamente.

Normalmente, el controlador de dispositivo también controla las interrupciones. Por lo tanto, todas las funciones del controlador deben ser seguras en caso de interrupción.

### <a name="driver-initialization"></a>Inicialización del controlador   
Aunque el procesamiento real de la inicialización del controlador es específico de la aplicación, normalmente consiste en la inicialización de la estructura de datos y el hardware físico. La información necesaria de NetX Duo para la inicialización del controlador es la unidad de transmisión máxima (MTU) de IP, que es el número de bytes disponibles para la carga del nivel de IP, incluido el encabezado IPv4 o IPv6, y si la interfaz física necesita una asignación de nombres lógicos a físicos. El controlador configura el valor de MTU de la interfaz mediante una llamada a ***nx_ip_interface_mtu_set***.

El controlador de dispositivo debe llamar a ***nx_ip_interface_address_mapping_configure** _ para indicar a NetX Duo si se requiere o no la asignación de direcciones de interfaz. Si es necesaria la asignación de direcciones, el controlador es responsable de configurar la interfaz con una dirección MAC válida y de proporcionar la dirección MAC a NetX mediante _*_nx_ip_interface_physical_address_set_**.

Cuando el controlador de red recibe la solicitud NX_LINK INITIALIZE de NetX Duo, recibe un puntero al bloque de control de IP como parte del bloque de control de la solicitud NX_IP_DRIVER mostrado anteriormente.

Una vez que la aplicación llama a ***nx_ip_create***, el subproceso auxiliar de IP envía una solicitud de controlador con el comando establecido en NX_LINK_INITIALIZE al controlador para inicializar su interfaz de red física. Se utilizan los siguientes miembros de NX_IP_DRIVER para la solicitud de inicialización.

| Miembro de&nbsp;NX_IP_DRIVER | Significado    |
| ------------------------- | ----------------------------- |
| nx_ip_driver_command   | NX_LINK_INITIALIZE    |
| nx_ip_driver_ptr       | Puntero a la instancia de IP. El controlador debe guardar este valor para que la función de controlador pueda encontrar la instancia de IP en la que se va a operar.    |
| nx_ip_driver_interface | Puntero a la estructura de la interfaz de red dentro de la instancia de IP. El controlador debe guardar esta información. Al recibir paquetes, el controlador utilizará la información de la estructura de la interfaz al enviar el paquete hacia arriba en la pila. El índice de interfaz (índice de dispositivo) se puede obtener mediante la lectura de nx_interface_index del miembro en esta estructura de datos. |
| nx_ip_driver_status    | Estado de finalización. Si el controlador no puede inicializar la interfaz especificada en la instancia de IP, devolverá un estado de error distinto de cero. |


> [!NOTE]  
> *Se llama al controlador desde el subproceso auxiliar de IP que se creó para la instancia de IP. Por consiguiente, la rutina del controlador debe evitar realizar operaciones de bloqueo, ya que el subproceso auxiliar de IP podría detenerse y causar retrasos ilimitados en las aplicaciones que se basan en el subproceso de IP.*

### <a name="enable-link"></a>Habilitar vínculo   
A continuación, el subproceso de la aplicación auxiliar IP habilita la red física mediante el establecimiento del comando driver en NX_LINK_ENABLE en la solicitud del controlador y el envío de la solicitud al controlador de red. Esto sucede poco después de que el subproceso auxiliar de IP complete la solicitud de inicialización. Habilitar el vínculo puede ser tan sencillo como establecer el campo *nx_interface_link_up* en la instancia de la interfaz. Pero también puede implicar la manipulación del hardware físico. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de habilitación del vínculo.

| Miembro de&nbsp;NX_IP_DRIVER       | Significado                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_ENABLE   |
| nx_ip_driver_ptr       | Puntero a la instancia de IP.  |
| nx_ip_driver_interface | Puntero a la instancia de interfaz |
| nx_ip_driver_status    | Estado de finalización. Si el controlador no puede habilitar la interfaz especificada, devolverá un estado de error distinto de cero. |

### <a name="disable-link"></a>Deshabilitar vínculo   
NetX Duo realiza esta solicitud cuando el servicio ***nx_ip_delete** elimina una instancia de IP. O bien, una aplicación puede emitir este comando para deshabilitar temporalmente el vínculo a fin de ahorrar energía. Este servicio deshabilita la interfaz de red física en la instancia de IP. El procesamiento para deshabilitar el vínculo puede ser tan sencillo como borrar la marca _nx_interface_link_up * en la instancia de la interfaz. Pero también puede implicar la manipulación del hardware físico. Normalmente es una operación inversa de la operación ***Enable Link**_. Una vez que se deshabilita el vínculo, la aplicación solicita la operación _ *_Enable Link_** para habilitar la interfaz.

Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de deshabilitación del vínculo.

| Miembro de&nbsp;NX_IP_DRIVER     | Significado                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_DISABLE    |
| nx_ip_driver_ptr       | Puntero a la instancia de IP.   |
| nx_ip_driver_interface | Puntero a la instancia de interfaz   |
| nx_ip_driver_status    | Estado de finalización. Si el controlador no puede deshabilitar la interfaz especificada en la instancia de IP, devolverá un estado de error distinto de cero. |

### <a name="uninitialize-link"></a>Anular inicialización de vínculo   
NetX Duo realiza esta solicitud cuando el servicio ***nx_ip_delete** elimina una instancia de IP. Esta solicitud anula la inicialización de la interfaz y libera los recursos creados durante la fase de inicialización. Normalmente es la operación inversa de la operación de _ *_inicialización de vínculo_**. Una vez que se anula la inicialización de la interfaz, el dispositivo no se puede usar hasta que la interfaz se vuelve a inicializar.

Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de deshabilitación del vínculo.

| Miembro de&nbsp;NX_IP_DRIVER    | Significado                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_UNINITIALZE      |
| nx_ip_driver_ptr       | Puntero a la instancia de IP.   |
| nx_ip_driver_interface | Puntero a la instancia de interfaz |
| nx_ip_driver_status    | Estado de finalización. Si el controlador no puede anular la inicialización de la interfaz especificada en la instancia de IP, devolverá un estado de error distinto de cero. |

### <a name="packet-send"></a>Envío de paquetes   
Esta solicitud se realiza durante el procesamiento de envío de IPv4 o IPv6 interno, que todos los protocolos de NetX Duo usan para transmitir paquetes (excepto ARP y RARP). Al recibir el comando de envío de paquetes, *nx_packet_prepend_ptr* apunta al principio del paquete que se va a enviar, que es el principio del encabezado de IPv4 o IPv6. *nx_packet_length* indica el tamaño total (en bytes) de los datos que se transmiten. Si *nx_packet_next* es válido, el datagrama de IP saliente se almacena en varios paquetes, es necesario que el controlador siga el paquete encadenado y transmita todo el marco. Tenga en cuenta que el área de datos válida en cada paquete encadenado se almacena entre *nx_packet_prepend_ptr* y *nx_packet_append_ptr*.

El controlador es responsable de construir un encabezado físico. Si se requiere la asignación de una dirección física a una dirección IP (como Ethernet), el nivel de IP ya resolvió la dirección MAC. La dirección MAC de destino se pasa desde la instancia de IP, almacenada en *nx_ip_driver_physical_address_msw y nx_ip_driver_physical_address_lsw*.

Después de agregar el encabezado físico, el procesamiento de envío de paquetes llama a la función de salida del controlador para transmitir el paquete.

Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de envío del paquete.

| Miembro de&nbsp;NX_IP_DRIVER              | Significado                               |
| -----------------------------------| --------------------------------------|
| nx_ip_driver_command            | NX_LINK_PACKET_SEND                |
| nx_ip_driver_ptr                | Puntero a la instancia de IP                |
| nx_ip_driver_packet             | Puntero al paquete que se va a enviar.         |
| nx_ip_driver_interface          | Puntero a la instancia de interfaz.    |
| nx_ip_driver_physical_address_msw | 32 bits de dirección física más significativos (solo si se requiere asignación física) |
| nx_ip_driver_physical_address_lsw | Los 32 bits de dirección física más significativos (solo si se necesita asignación física) |
| nx_ip_driver_status             | Estado de finalización. Si el controlador no puede enviar el paquete, devolverá un estado de error distinto de cero. |

### <a name="packet-broadcastipv4-packets-only"></a>Difusión de paquetes (solo paquetes IPv4)  
Esta solicitud es casi idéntica a la solicitud de envío de paquetes. La única diferencia es que los campos de dirección física de destino se establecen en la dirección MAC de difusión Ethernet. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de difusión de paquetes.

| Miembro de&nbsp;NX_IP_DRIVER                | Significado                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST                                                                                 |
| nx_ip_driver_ptr                   | Puntero a la instancia de IP                                                                                   |
| nx_ip_driver_packet                | Puntero al paquete que se va a enviar                                                                            |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (difusión)                                                                                   |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (difusión)                                                                                   |
| nx_ip_driver_interface             | Puntero a la instancia de interfaz.                                                                       |
| nx_ip_driver_status                | Estado de finalización. Si el controlador no puede enviar el paquete, devolverá un estado de error distinto de cero. |

### <a name="arp-send"></a>Envío de ARP  
Esta solicitud también es similar a la solicitud de envío de paquetes IP. La única diferencia es que el encabezado Ethernet especifica un paquete ARP, en lugar de un paquete IP, y los campos de dirección física de destino se establecen en dirección de difusión MAC. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de envío de ARP.

| Miembro de&nbsp;NX_IP_DRIVER                | Significado                                                                                                      |
|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_ARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Puntero a la instancia de IP                                                                                       |
| nx_ip_driver_packet                | Puntero al paquete que se va a enviar                                                                                |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (difusión)                                                                                       |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (difusión)                                                                                       |
| nx_ip_driver_interface             | Puntero a la instancia de interfaz.                                                                           |
| nx_ip_driver_status                | Estado de finalización. Si el controlador no puede enviar el paquete ARP, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]  
> *Si no se necesita la asignación física, no es preciso implementar esta solicitud.*

*Aunque ARP se reemplazó por el protocolo de detección de equipos cercanos y el protocolo de detección de enrutadores en IPv6, los controladores de red Ethernet deben seguir siendo compatibles con los enrutadores y los nodos del mismo nivel de IPv4. Por lo tanto, los controladores deben seguir controlando los paquetes ARP*.

### <a name="arp-response-send"></a>Envío de respuesta ARP  
Esta solicitud es casi idéntica a la solicitud de paquetes ARP. La única diferencia es que los campos de dirección física de destino se pasan desde la instancia de IP. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de envío de respuesta ARP.

| Miembro de&nbsp;NX_IP_DRIVER                  | Significado                                  |
| -------------------------------------- | -----------------------------------------|
| nx_ip_driver_command                | NX_LINK_ARP_RESPONSE_SEND            |
| nx_ip_driver_ptr                    | Puntero a la instancia de IP   |
| nx_ip_driver_packet                 | Puntero al paquete que se va a enviar.          |
| nx_ip_driver_physical_address_msw | 32 bits de dirección física más significativos |
| nx_ip_driver_physical_address_lsw | 32 bits de dirección física menos significativos |
| nx_ip_driver_interface              | Puntero a la instancia de interfaz |
| nx_ip_driver_status                 | Estado de finalización. Si el controlador no puede enviar el paquete ARP, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]  
> *Si no se necesita la asignación física, no es preciso implementar esta solicitud.*

### <a name="rarp-send"></a>Envío de RARP   
Esta solicitud es casi idéntica a la solicitud de paquetes ARP. Las únicas diferencias son el tipo de encabezado de paquete y los campos de dirección física no son necesarios, ya que el destino físico es siempre una dirección de difusión.

Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de envío de RARP.

| Miembro de&nbsp;NX_IP_DRIVER                | Significado                                                                                                       |
|------------------------------------|---------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_RARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | Puntero a la instancia de IP                                                                                        |
| nx_ip_driver_packet                | Puntero al paquete que se va a enviar                                                                                 |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (difusión)                                                                                        |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (difusión)                                                                                        |
| nx_ip_driver_interface             | Puntero a la instancia de interfaz.                                                                            |
| nx_ip_driver_status                | Estado de finalización. Si el controlador no puede enviar el paquete RARP, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]  
> *Las aplicaciones que requieren el servicio RARP deben implementar este comando*.

### <a name="multicast-group-join"></a>Unión a un grupo de multidifusión   
Esta solicitud se realiza con los servicios ***nx_igmp_multicast_interface join** _ y _*_nx_ipv4_multicast_interface_join_*_ en IPv4, y con el servicio _ *_nxd_ipv6_multicast_interface_join_** en IPv6, así como con las distintas operaciones que requiere IPv6. El controlador de red toma la dirección del grupo de multidifusión suministrada y configura el soporte físico para aceptar los paquetes entrantes de dicha dirección. Tenga en cuenta que en el caso de los controladores que no admiten un filtro multidifusión, es posible que la lógica de recepción del controlador esté en modo promiscuo. En este caso, es posible que el controlador tenga que filtrar los marcos entrantes en función de la dirección MAC de destino, lo que reduce la cantidad de tráfico que se pasa a la instancia de IP. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de unión al grupo de multidifusión.

| Miembro de&nbsp;NX_IP_DRIVER                  | Significado                                 |
| -------------------------------------- | --------------------------------------- |
| nx_ip_driver_command                | NX_LINK_MULTICAST_JOIN               |
| nx_ip_driver_ptr                    | Puntero a la instancia de IP  |
| nx_ip_driver_physical_address_msw | 32 bits de dirección multidifusión física más significativos |
| nx_ip_driver_physical_address_lsw | 32 bits de dirección multidifusión física menos significativos |
| nx_ip_driver_interface              | Puntero a la instancia de interfaz |
| nx_ip_driver_status                 | Estado de finalización. Si el controlador no puede unirse al grupo de multidifusión, devolverá un estado de error distinto de cero. |

> [!NOTE]  
> *Las aplicaciones IPv6 requerirán que se implemente la multidifusión en el controlador para protocolos basados en ICMPv6, como la configuración de direcciones. Sin embargo, para las aplicaciones IPv4, la implementación de esta solicitud no es necesaria si no se requieren funcionalidades de multidifusión*.

> [!IMPORTANT]  
> *Si IPv6 no está habilitado y IPv4 no requiere las funcionalidades de multidifusión, la implementación de esta solicitud no es necesaria*.

### <a name="multicast-group-leave"></a>Salida de un grupo de multidifusión  
Esta solicitud se invoca mediante una llamada explícita a los servicios ***nx_igmp_multicast_interface_leave** _ o _*_nx_ipv4_multicast_interface_leave_*_ en IPv4, al servicio _ *_nxd_ipv6_multicast_interface_leave_** en IPv6 o mediante las distintas operaciones internas de NetX Duo que requiere IPv6. El controlador quita la dirección de multidifusión Ethernet suministrada de la lista de multidifusión. Una vez que un host ha dejado un grupo de multidifusión, esta instancia de IP deja de recibir los paquetes de la red con esta dirección de multidifusión Ethernet. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de abandono del grupo de multidifusión.

| Miembro de&nbsp;NX_IP_DRIVER              | Significado                              |
| -----------------------------------| -------------------------------------|
| nx_ip_driver_command            | NX_LINK_MULTICAST_LEAVE           |
| nx_ip_driver_ptr                | Puntero a la instancia de IP   |
| nx_ip_driver_physical_address_msw | 32 bits de la dirección multidifusión física más significativos |
| nx_ip_driver_physical_address_lsw | 32 bits de dirección multidifusión física menos significativos |
| nx_ip_driver_interface              | Puntero a la instancia de interfaz |
| nx_ip_driver_status                 | Estado de finalización. Si el controlador no puede dejar el grupo de multidifusión, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]  
> *Si IPv4 o IPv6 no requieren las funcionalidades de multidifusión, la implementación de esta solicitud no es necesaria*.

### <a name="attach-interface"></a>Asociar interfaz  
Esta solicitud se invoca desde NetX Duo para el controlador de dispositivo, lo que permite al controlador asociar la instancia del controlador a la instancia de IP correspondiente y a la instancia de la interfaz física dentro de la dirección IP. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de asociación de interfaz.

| Miembro de&nbsp;NX_IP_DRIVER    | Significado                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | Puntero a la instancia de IP.   |
| nx_ip_driver_interface | Puntero a la instancia de interfaz.|
| nx_ip_driver_status    | Estado de finalización. Si el controlador no puede desasociar la interfaz especificada en la instancia de IP, devolverá un estado de error distinto de cero. |

### <a name="detach-interface"></a>Desasociar interfaz    
Esta solicitud la invoca NetX Duo para el controlador de dispositivo, lo que permite al controlador desasociar la instancia del controlador de la instancia de IP correspondiente y de la instancia de la interfaz física dentro de la dirección IP. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de asociación de interfaz.

| Miembro de&nbsp;NX_IP_DRIVER    | Significado                                                                                                                                    |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH                                                                                                                   |
| nx_ip_driver_ptr       | Puntero a la instancia de IP.                                                                                                                     |
| nx_ip_driver_interface | Puntero a la instancia de interfaz.                                                                                                         |
| nx_ip_driver_status    | Estado de finalización. Si el controlador no puede asociar la interfaz especificada en la instancia de IP, devolverá un estado de error distinto de cero. |

### <a name="get-link-status"></a>Obtener estado del vínculo    
La aplicación puede consultar el estado del vínculo de la interfaz de red mediante el servicio ***nx_ip_interface_status_check*** de NetX Duo para cualquier interfaz del host. Para más información sobre estos servicios, consulte el capítulo 4, "Descripción de los servicios de NetX Duo" en la página 149.

El estado del vínculo se encuentra en el campo *nx_interface_link_up* de la estructura de NX_INTERFACE a la que apunta el puntero *nx_ip_driver_interface*. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de estado del vínculo.

| Miembro de&nbsp;NX_IP_DRIVER       | Significado                  |
| --------------------------- | -------------------------|
| nx_ip_driver_command     | NX_LINK_GET_STATUS    |
| nx_ip_driver_ptr         | Puntero a la instancia de IP.   |
| nx_ip_driver_return_ptr | Puntero al destino en el que se va a colocar el estado. |
| nx_ip_driver_interface   | Puntero a la instancia de interfaz   |
| nx_ip_driver_status      | Estado de finalización. Si el controlador no puede obtener un estado concreto, devolverá un estado de error distinto de cero. |

> [!NOTE]  
> ***nx_ip_status_check** _ todavía está disponible para comprobar el estado de la interfaz principal. Sin embargo, se recomienda a los desarrolladores de aplicaciones que usen el servicio específico de la interfaz: _ *_nx_ip_interface_status_check._**

### <a name="get-link-speed"></a>Obtener velocidad del vínculo  
Esta solicitud se realiza desde el servicio ***nx_ip_driver_direct_command***. El controlador almacena la velocidad de línea del vínculo en el destino suministrado. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de velocidad de línea del vínculo.

| Miembro de&nbsp;NX_IP_DRIVER   | Significado                   |
| ------------------------| ------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_SPEED          |
| nx_ip_driver_ptr         | Puntero a la instancia de IP.                                                                                         |
| nx_ip_driver_return_ptr | Puntero al destino en el que se va a colocar la velocidad de la línea.                                                             |
| nx_ip_driver_interface   | Puntero a la instancia de interfaz                                                                              |
| nx_ip_driver_status      | Estado de finalización. Si el controlador no puede obtener información sobre la velocidad, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]  
> *NetX Duo no usa internamente esta solicitud, por lo que su implementación es opcional*.

### <a name="get-duplex-type"></a>Obtener tipo dúplex   
Esta solicitud se realiza desde el servicio ***nx_ip_driver_direct_command***. El controlador almacena el tipo dúplex del vínculo en el destino suministrado. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de tipo dúplex.

| Miembro de&nbsp;NX_IP_DRIVER   | Significado                                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_DUPLEX_TYPE                                                                                    |
| nx_ip_driver_ptr         | Puntero a la instancia de IP.                                                                                         |
| nx_ip_driver_return_ptr | Puntero al destino en el que se va a colocar el tipo dúplex.                                                            |
| nx_ip_driver_interface   | Puntero a la instancia de interfaz                                                                              |
| nx_ip_driver_status      | Estado de finalización. Si el controlador no puede obtener información sobre el dúplex, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]  
> *NetX Duo no usa internamente esta solicitud, por lo que su implementación es opcional*.

### <a name="get-error-count"></a>Obtener número de errores   
Esta solicitud se realiza desde el servicio ***nx_ip_driver_direct_command***. El controlador almacena el número de errores del vínculo en el destino suministrado. Para admitir esta característica, el controlador debe realizar un seguimiento de los errores en las operaciones. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud del número de errores del vínculo.

| Miembro de&nbsp;NX_IP_DRIVER   | Significado                   |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_ERROR_COUNT   |
| nx_ip_driver_ptr         | Puntero a la instancia de IP.   |
| nx_ip_driver_return_ptr | Puntero al destino en el que se va a colocar el número de errores. |
| nx_ip_driver_interface   | Puntero a la instancia de interfaz|
| nx_ip_driver_status      | Estado de finalización. Si el controlador no puede obtener el número de errores, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]
> *NetX Duo no usa internamente esta solicitud, por lo que su implementación es opcional*.

### <a name="get-receive-packet-count"></a>Obtener número de paquetes recibidos    
Esta solicitud se realiza desde el servicio ***nx_ip_driver_direct_command***. El controlador almacena el número de paquetes recibidos del vínculo en el destino suministrado. Para admitir esta característica, el controlador debe realizar un seguimiento del número de paquetes recibidos. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud del número de paquetes recibidos del vínculo.

| Miembro de&nbsp;NX_IP_DRIVER       | Significado                        |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_RX_COUNT      |
| nx_ip_driver_ptr         | Puntero a la instancia de IP.  |
| nx_ip_driver_return_ptr | Puntero al destino en el que se va a colocar el número de paquetes recibidos.   |
| nx_ip_driver_interface   | Puntero a la interfaz de red física.  |
| nx_ip_driver_status      | Estado de finalización. Si el controlador no puede obtener el número de paquetes recibidos, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]  
> *NetX Duo no usa internamente esta solicitud, por lo que su implementación es opcional*.

### <a name="get-transmit-packet-count"></a>Obtener recuento de paquetes transmitidos   
Esta solicitud se realiza desde el servicio ***nx_ip_driver_direct_command***. El controlador almacena el número de paquetes transmitidos del vínculo en el destino suministrado. Para admitir esta característica, el controlador debe realizar un seguimiento de todos los paquetes que se transmiten en cada interfaz. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud del número de paquetes transmitidos del vínculo.

| Miembro de&nbsp;NX_IP_DRIVER   | Significado                   |
| ----------------------- | ------------------------- |
| nx_ip_driver_command | NX_LINK_GET_TX_COUNT  |
| nx_ip_driver_ptr     | Puntero a la instancia de IP.    |
| nx_ip_driver_return_ptr | Puntero al destino en el que se va a colocar el número de paquetes transmitidos  |
| nx_ip_driver_interface   | Puntero a la instancia de interfaz   |
| nx_ip_driver_status      | Estado de finalización. Si el controlador no puede obtener el número de paquetes transmitidos, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]  
> *NetX Duo no usa internamente esta solicitud, por lo que su implementación es opcional*.

### <a name="get-allocation-errors"></a>Obtener errores de asignación   
Esta solicitud se realiza desde el servicio ***nx_ip_driver_direct_command***. El controlador almacena el número de errores de asignación del grupo de paquetes del vínculo en el destino proporcionado. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud del número de errores de asignación del vínculo.

| Miembro de&nbsp;NX_IP_DRIVER       | Significado                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_ALLOC_ERRORS  |
| nx_ip_driver_ptr         | Puntero a la instancia de IP.     |
| nx_ip_driver_return_ptr | Puntero al destino en el que se va a colocar el número de errores de asignación.  |
| nx_ip_driver_interface   | Puntero a la instancia de interfaz  |
| nx_ip_driver_status      | Estado de finalización. Si el controlador no puede obtener los errores de asignación, devolverá un estado de error distinto de cero. |

> [!IMPORTANT]  
> *NetX Duo no usa internamente esta solicitud, por lo que su implementación es opcional*.

### <a name="driver-deferred-processing"></a>Procesamiento diferido del controlador    
Esta solicitud se realiza desde el subproceso auxiliar de IP en respuesta a la llamada del controlador a la rutina _ _***nx_ip_driver_deferred_processing**_ desde un ISR de transmisión o recepción. Esto permite que el ISR del controlador difiera el procesamiento de la recepción y transmisión del paquete hasta el subproceso auxiliar de IP y, por tanto, reduzca la cantidad que se va a procesar en el ISR. El controlador puede usar el campo _nx_interface_additional_link_info* de la estructura de NX_INTERFACE a la que apunta *nx_ip_driver_interface* para almacenar información sobre el evento de procesamiento diferido desde el contexto del subproceso auxiliar de IP. Los siguientes miembros de NX_IP_DRIVER se usan para el evento de procesamiento diferido.

| Miembro de&nbsp;NX_IP_DRIVER     | Significado                           |
| ------------------------- | --------------------------------- |
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING    |
| nx_ip_driver_ptr       | Puntero a la instancia de IP.            |
| nx_ip_driver_interface | Puntero a la instancia de interfaz |

### <a name="set-physical-address"></a>Establecer la dirección física  
Esta solicitud se realiza desde el servicio ***nx_ip_interface_physical_address_set** _. Este servicio permite a una aplicación cambiar la dirección física de la interfaz en tiempo de ejecución. Al recibir este comando, el controlador debe volver a configurar la dirección de hardware de la interfaz de red para la dirección física proporcionada. Dado que la instancia de IP ya tiene la nueva dirección, no es necesario llamar al servicio _ *_nx_ip_interface_address_set_** desde este comando.

Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de comandos de usuario.

| Miembro de&nbsp;NX_IP_DRIVER      | Significado                      |
| -------------------------- | ---------------------------- |
| nx_ip_driver_command    | NX_LINK_SET_PHYSICAL_ADDRESS  |
| nx_ip_driver_ptr        | Puntero a la instancia de IP.  |
| nx_ip_driver_interface  | Puntero a la instancia de interfaz   |
| nx_ip_driver_physical_ad dress_msw | 32 bits de la nueva dirección física más significativos  |
| nx_ip_driver_physical_ad dress_lsw | 32 bits de la nueva dirección física menos significativos  |
| nx_ip_driver_status                  | Estado de finalización. Si el controlador no puede volver a configurar la dirección física, devolverá un estado de error distinto de cero. |

### <a name="user-commands"></a>Comandos de usuario    
Esta solicitud se realiza desde el servicio ***nx_ip_driver_direct_command***. El controlador procesa los comandos de usuario específicos de la aplicación. Los siguientes miembros de NX_IP_DRIVER se usan para la solicitud de comandos de usuario.

| Miembro de&nbsp;NX_IP_DRIVER       | Significado                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_USER_COMMAND       |
| nx_ip_driver_ptr         | Puntero a la instancia de IP.        |
| nx_ip_driver_return_ptr | Definidas por el usuario       |
| nx_ip_driver_interface   | Puntero a la instancia de interfaz    |
| nx_ip_driver_status      | Estado de finalización. Si el controlador no puede ejecutar comandos de usuario, devolverá un estado de error distinto de cero. |

> [!IMPORTANT] 
> *NetX Duo no usa internamente esta solicitud, por lo que su implementación es opcional*.

### <a name="unimplemented-commands"></a>Comandos no implementados  
Los comandos no implementados por el controlador de red deben tener el campo estado devuelto establecido en NX_UNHANDLED_COMMAND.

## <a name="driver-capability"></a>Funcionalidad del controlador

Algunas interfaces de red ofrecen características de descarga de suma de comprobación. Los controladores de dispositivo pueden aprovechar las aceleraciones de hardware para liberar tiempo de CPU de la ejecución de varios cálculos de suma de comprobación.

Dependiendo del nivel de compatibilidad de la suma de comprobación del hardware, el controlador de dispositivo debe indicar a la instancia de IP qué característica de hardware está habilitada. De este modo, la instancia de IP es consciente de la característica de hardware y descarga la máxima cantidad de cálculo posible en el hardware. El controlador debe usar la API ***nx_ip_interface_capability_set*** para establecer todas las características que la interfaz física puede controlar.

Se pueden usar las siguientes características:

- NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_RX_CHECKSUM

En el caso de un cálculo de suma de comprobación que se puede realizar en el hardware, el controlador debe configurar el hardware o los descriptores de búfer correctamente para que el hardware pueda generar e insertar en el encabezado la suma de comprobación de un paquete saliente. Al recibir un paquete, la lógica de la suma de comprobación de hardware debe poder comprobar el valor de la suma de comprobación. Si el valor de la suma de comprobación es incorrecto, se debe descartar el fotograma recibido.

Incluso con la capacidad de realizar el cálculo de la suma de comprobación en el hardware, la instancia de IP sigue manteniendo la capacidad de suma de comprobación. En ciertos escenarios, por ejemplo, para un datagrama UDP que atraviesa la protección de IPsec, la suma de comprobación de UDP debe calcularse en el software antes de legar el marco de UDP a la pila. La mayoría de las características de la suma de comprobación de hardware no admite el cálculo de suma de comprobación para un segmento de datos protegido por IPsec. En el caso de un marco UDP o ICMP que deba fragmentarse, la suma de comprobación de UDP o ICMP debe calcularse en el software. La mayoría de la lógica de suma de comprobación de hardware no controla el caso en que los datos se dividen en varios marcos.

## <a name="driver-output"></a>Salida del controlador  

Todas las solicitudes de transmisión de paquetes mencionadas anteriormente requieren una función de salida implementada en el controlador. La lógica de transmisión concreta es específica del hardware, pero normalmente consiste en comprobar la capacidad del hardware para enviar el paquete inmediatamente. Si es posible, la carga de paquetes (y las cargas adicionales en la cadena de paquetes) se carga en uno o varios de los búferes de transmisión de hardware y se inicia una operación de transmisión. Si el paquete no cabe en los búferes de transmisión disponibles, el paquete debe ponerse en cola y transmitirse cuando los búferes de transmisión estén disponibles.

La cola de transmisión recomendada es una lista vinculada individualmente que tiene punteros de encabezado y de cola. Los paquetes nuevos se agregan al final de la cola y el paquete más antiguo es siempre el primero. El campo *nx_packet_queue_next* se usa como el siguiente vínculo del paquete en la cola. El controlador define los punteros del encabezado y la cola de la transmisión.

> [!CAUTION]  
> *Dado que se accede a esta cola desde las partes de subproceso e interrupción del controlador, la protección de la interrupción debe colocarse alrededor de las manipulaciones de la cola*.

La mayoría de las implementaciones de hardware físico generan una interrupción tras la finalización de la transmisión de paquetes. Cuando el controlador recibe una interrupción de este tipo, normalmente libera los recursos asociados al paquete que se está transmitiendo. Si la lógica de transmisión lee los datos directamente del búfer de NX_PACKET, el controlador debe usar el servicio de ***nx_packet_transmit_release*** para devolver el paquete asociado a la interrupción de retransmisión completada al grupo de paquetes disponible. Después, el controlador examina la cola de transmisión para buscar otros paquetes que están esperando a ser enviados. Como muchos de los paquetes de transmisión en cola que caben en los búferes de transmisión del hardware se quitan de la cola y se cargan en los búferes. Esto va seguido del inicio de otra operación de envío.

En cuanto los datos de NX_PACKET se hayan movido al patrón FIFO del transmisor (o en caso de que un controlador admita la operación sin copia, se hayan transmitido los datos de NX_PACKET), el controlador debe mover el campo *nx_packet_prepend_ptr* al principio del encabezado IP antes de llamar a ***nx_packet_transmit_release** _. Recuerde ajustar el campo _nx_packet_length* en consecuencia. Si un marco de IP se compone de varios paquetes, solo es necesario liberar el principio de la cadena de paquetes.

## <a name="driver-input"></a>Entrada del controlador

Tras la recepción de una interrupción de paquetes recibida, el controlador de red recupera el paquete de los búferes de recepción de hardware físico y crea un paquete de NetX Duo válido. La creación de un paquete de NetX Duo válido implica configurar el campo de longitud adecuado y el encadenamiento de varios paquetes si el tamaño del paquete entrante es mayor que una sola carga de paquete. Una vez creado correctamente, *prepend_ptr* se mueve después del encabezado de la capa física y el paquete de recepción se envía a NetX Duo.

NetX Duo supone que los encabezados IP (IPv4 e IPv6) y ARP están alineados en un límite **ULONG**. Por consiguiente, el controlador de NetX Duo debe garantizar esta alineación. En entornos Ethernet, esto se logra iniciando el encabezado de Ethernet a dos bytes del principio del paquete. Cuando *nx_packet_prepend_ptr* se mueve más allá del encabezado de Ethernet, el encabezado IP (IPv4 e IPv6) o ARP subyacente tiene una alineación de 4 bytes.

> [!WARNING] 
> *Consulte la sección "Encabezados Ethernet" a continuación para conocer las diferencias importantes entre los encabezados Ethernet IPv4 e IPv6*.

Hay varias funciones del paquete de recepción disponibles en NetX Duo. Si el paquete recibido es un paquete ARP, se llama a _***nx_arp_packet_deferred_receive**_. Si el paquete recibido es un paquete RARP, se llama a _ _*_nx_rarp_packet_deferred_receive_*_. Hay varias opciones para controlar los paquetes IP entrantes. Si lo que se desea es lograr el control más rápido posible de los paquetes IP, se llama a _*_nx_ip_packet_receive_*_. Este enfoque es el que tiene la menor sobrecarga, pero requiere más procesamiento en el controlador de servicio de interrupción de recepción (ISR) del controlador. Si lo que se necesita es que el procesamiento de ISR sea mínimo, se llama a __ *_nx_ip_packet_deferred_receive_**.

Una vez que el nuevo paquete de recepción se ha creado correctamente, los búferes de recepción del hardware físico se configuran para recibir más datos. Esto podría requerir la asignación de paquetes de NetX Duo y la colocación de la dirección de la carga en el búfer de recepción de hardware, o puede que se limite a cambiar una configuración del búfer de recepción de hardware. Para minimizar las posibilidades de saturación, es importante que los búferes de recepción del hardware tengan búferes disponibles lo antes posible después de recibir un paquete.

> [!IMPORTANT] 
> *Los búferes de recepción iniciales se configuran durante la inicialización del controlador*.

### <a name="deferred-receive-packet-handling"></a>Control de paquetes de recepción diferidos  
El controlador puede diferir el procesamiento de paquetes de recepción en el subproceso auxiliar de IP de NetX Duo. En algunas aplicaciones, es posible que esto sea necesario para minimizar tanto el procesamiento de ISR como el número de paquetes descartados. 

Para usar el control de paquetes diferido, antes debe compilarse la biblioteca de NetX Duo con ***NX_DRIVER_DEFERRED_PROCESSING** _ definido. Esto agrega la lógica de paquetes diferida al subproceso auxiliar de IP de NetX Duo. Después, al recibir un paquete de datos, el controlador debe llamar a __nx_ip_packet_deferred_receive():*

```c
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```
La función de recepción diferida coloca el paquete de recepción representado por *packet_ptr* en una FIFO (lista vinculada) y notifica al subproceso auxiliar de IP. Después de ejecutarse, la aplicación auxiliar de IP llama repetidamente a la función de control diferida para procesar cada paquete diferido. Normalmente, el procesamiento de los controladores diferidos incluye la eliminación del encabezado de la capa física del paquete (normalmente Ethernet) y su envío a una de estas funciones de recepción de NetX Duo:

- ***_nx_ip_packet_receive***
- ***_nx_arp_packet_deferred_receive***
- ***_nx_rarp_packet_deferred_receive***

## <a name="ethernet-headers"></a>Encabezados Ethernet 

Una de las diferencias más importantes entre IPv6 e IPv4 para los encabezados Ethernet es la configuración del tipo de marco. Al enviar paquetes, el controlador Ethernet es responsable de establecer el tipo de marco Ethernet de los paquetes salientes. En el caso de los paquetes IPv6, el tipo de marco debe ser 0x86DD y en el caso de los paquetes IPv4, debe ser 0x0800.

El siguiente segmento de código muestra este proceso:

```c
NX_PACKET *packet_ptr;
packet_ptr = driver_req_ptr -> nx_ip_driver_packet;
if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V4)
{

   /* Set Ethernet frame type to IPv4 /*
   ethernet_frame_ptr -> frame_type = 0x0800;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V6)
{

   /* Set Ethernet frame type to IPv6. /*
   ethernet_frame_ptr -> frame_type = 0x86DD;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else
{

   /* Unknown IP version. Free the packet we will not send. */
   nx_packet_transmit_release(packet_ptr);
}
```
De forma similar, para los paquetes entrantes, el controlador Ethernet debe determinar el tipo de paquete del tipo de marco Ethernet. Debe implementarse para aceptar los tipos de marco IPv6 (0x86DD), IPv4 (0x0800), ARP (0x0806) y RARP (0x8035).

## <a name="example-ram-ethernet-network-driver"></a>Controlador de red Ethernet de RAM de ejemplo

El sistema de demostración de NetX Duo se entrega con un pequeño controlador de red basado en RAM, definido en el archivo ***nx_ram_network_driver.c.*** Este controlador da por hecho que todas las instancias de IP se encuentran en la misma red y simplemente asigna direcciones de hardware virtual (direcciones MAC) a cada instancia del dispositivo a medida que se crean. Este archivo es un buen ejemplo de la estructura básica de los controladores de red físicos de NetX Duo. Los usuarios pueden desarrollar sus propios controladores de red mediante el marco de controlador que se presenta en este ejemplo.

La función de entrada del controlador de red es * **_nx_ram_network_driver(),** _ que se pasa a la llamada de creación de una instancia de IP. Las funciones de entrada de las interfaces de red adicionales se pueden pasar al servicio _nx_ip_interface_attach()*. Una vez que se inicia la ejecución de la instancia de IP, se invoca la función de entrada del controlador para inicializar y habilitar el dispositivo (consulte el caso **NX_LINK_INITIALIZE** y **NX_LINK_ENABLE**). Después de la emisión del comando **NX_LINK_ENABLE**, el dispositivo debe estar preparado para transmitir y recibir paquetes. 

La instancia de IP transmite los paquetes de red a través de uno de estos comandos:

| Get-Help                         |  Descripción                                                   |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_PACKET_SEND***    | Se está transmitiendo un paquete IPv4 o IPv6.                   |
| ***NX_LINK_ARP_SEND***       | Se transmite un paquete de solicitudes ARP o respuestas ARP.    |
| ***NX_LINK_ARP_RARP_SEND*** | Se transmite un paquete de solicitudes o respuestas ARP inverso. |

Al procesar estos comandos, el controlador de red debe anteponer el encabezado del marco Ethernet adecuado y, después, enviarlo al hardware subyacente para su transmisión. Durante el proceso de transmisión, el controlador de red tiene la propiedad exclusiva del área del búfer de paquetes. Por consiguiente, una vez que se transmiten los datos (o una vez que los datos se han copiado en el búfer de transferencia interno del controlador), el controlador de red es responsable de liberar el búfer de paquetes, para lo cual en primer lugar mueve el puntero antepuesto más allá del encabezado Ethernet al encabezado de IP (y ajusta la longitud del paquete en consecuencia) y, después, llama al servicio ***nx_packet_transmit_release()*** para liberar el paquete. Si no se libera el paquete después de la transmisión de datos, se producirán pérdidas de paquetes.

El controlador de dispositivo de red también es responsable de administrar los paquetes de datos entrantes. En el ejemplo del controlador de RAM, la función ***_nx_ram_network_driver_receive()*** procesa el paquete recibido. Una vez que el dispositivo recibe un marco Ethernet, el controlador es responsable de almacenar los datos en la estructura NX_PACKET. Tenga en cuenta que NetX Duo supone que el encabezado IP comienza en una dirección alineada de 4 bytes. Dado que la longitud del encabezado de Ethernet es de 14 bytes, el controlador necesita almacenar el inicio del encabezado Ethernet en una dirección alineada de 2 bytes para garantizar que el encabezado IP se inicia en una dirección alineada de 4 bytes.