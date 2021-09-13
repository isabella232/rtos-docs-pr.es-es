---
title: 'Capítulo 3: Componentes funcionales de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de la pila TCP/IP de alto rendimiento de Azure RTOS NetX Duo desde una perspectiva funcional.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c96e6e422ea570085f5d7c6aeaaaa697a2393b5e
ms.sourcegitcommit: 20a136b06a25e31bbde718b4d12a03ddd8db9051
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2021
ms.locfileid: "123552388"
---
# <a name="chapter-3---functional-components-of-azure-rtos-netx-duo"></a>Capítulo 3: Componentes funcionales de Azure RTOS NetX Duo

Este capítulo contiene una descripción de la pila TCP/IP de alto rendimiento de Azure RTOS NetX Duo desde una perspectiva funcional. 

## <a name="execution-overview"></a>Información general sobre la ejecución

Hay cinco tipos de ejecución de programa en una aplicación NetX Duo: inicialización, llamadas a la interfaz de la aplicación, subproceso de IP interno, temporizadores periódicos de IP y el controlador de red.

> [!NOTE]
> *NetX Duo da por hecha la existencia de ThreadX y depende de la ejecución de subprocesos, la suspensión, los temporizadores periódicos y los recursos de exclusión mutua.*

### <a name="initialization"></a>Inicialización

Se debe llamar al servicio ***nx_system_initialize** _ antes de llamar a ningún otro servicio de NetX Duo. Se puede llamar a la inicialización del sistema desde la función _ *_tx_application_define_** de ThreadX o desde los subprocesos de la aplicación.

Después de volver de ***nx_system_initialize** _, el sistema está listo para crear grupos de paquetes e instancias de IP. Dado que la creación de una instancia de IP requiere un grupo de paquetes predeterminado, debe existir al menos un grupo de paquetes de NetX Duo antes de crear una instancia de IP. Se permite crear grupos de paquetes e instancias de IP desde la función de inicialización de ThreadX _ *_tx_application_define_** y desde los subprocesos de la aplicación.

Internamente, la creación de una instancia de IP se realiza en dos partes: la primera parte se realiza en el contexto del autor de llamada, ya sea desde ***tx_application_define*** o desde el contexto de un subproceso de la aplicación. Esto incluye la configuración de la estructura de datos de IP y la creación de varios recursos de IP, incluido el subproceso de IP interno. La segunda parte se realiza durante la ejecución inicial desde el subproceso de IP interno. Aquí es donde se llama primero al controlador de red, proporcionado durante la primera parte de la creación de IP. La llamada al controlador de red desde el subproceso de IP interno permite que el controlador realice la E/S y la suspensión durante su procesamiento de inicialización.

Cuando el controlador de red vuelve de su procesamiento de inicialización, se completa la creación de la instancia de IP.

La inicialización de IPv6 en NetX Duo requiere algunos servicios adicionales de NetX Duo. Estos se describen con más detalle en la sección [IPv6 en NetX Duo](#ipv6-in-netx-duo) más adelante en este capítulo.

> [!NOTE]
> *El servicio **nx_ip_status_check** de NetX Duo está disponible para obtener información sobre la instancia de IP y el estado de su interfaz principal. Esta información de estado incluye si el vínculo está inicializado y habilitado y si se ha resuelto la dirección IP. Esta información se usa para sincronizar los subprocesos de la aplicación que necesitan usar una instancia de IP recién creada. En el caso de los sistemas de host múltiple, consulte [Compatibilidad con host múltiple](#multihome-support). **nx_ip_interface_status_check** está disponible para obtener información sobre la interfaz especificada.*

### <a name="application-interface-calls"></a>Llamadas a la interfaz de la aplicación

Las llamadas desde la aplicación se realizan en gran medida desde los subprocesos de la aplicación que se ejecutan en RTOS ThreadX. Sin embargo, se puede llamar a algunos servicios de inicialización, creación y habilitación desde ***tx_application_define***. Las secciones "Permitido desde" del [Capítulo 4: Descripción de los servicios de Azure RTOS NetX Duo](chapter4.md) indican la ubicación desde la que se puede llamar a cada servicio de NETX Duo.

En su mayor parte, el procesamiento de actividades intensivas como el cálculo de sumas de comprobación se realiza en el contexto del subproceso de llamada, sin impedir a otros subprocesos el acceso a la instancia de IP. Por ejemplo, en la transmisión, el cálculo de la suma de comprobación de UDP se realiza en el servicio ***nx_udp_socket_send** _, antes de llamar a la función de envío de IP subyacente. En un paquete recibido, la suma de comprobación de UDP se calcula en el servicio _ *_nx_udp_socket_receive_**, que se ejecuta en el subproceso de la aplicación. Esto ayuda a evitar la detención de solicitudes de red de subprocesos de mayor prioridad debido al procesamiento intensivo de sumas de comprobación en subprocesos de menor prioridad.

Los valores, como las direcciones IP y los números de puerto, se pasan a las API en el orden de bytes del host. Internamente, estos valores también se almacenan en el orden de bytes del host. Esto permite a los desarrolladores ver fácilmente los valores mediante un depurador. Cuando estos valores se programan en un marco para la transmisión, se convierten al orden de bytes de la red.

### <a name="internal-ip-thread"></a>Subproceso de IP interno

Como se ha mencionado, cada instancia de IP en NetX Duo tiene su propio subproceso. La prioridad y el tamaño de la pila del subproceso de IP interno se define en el servicio ***nx_ip_create***. El subproceso de IP interno se crea en un modo listo para ejecutarse. Si el subproceso de IP tiene una prioridad más alta que el subproceso que realiza la llamada, se puede producir un adelantamiento dentro de la llamada de creación de IP.

El punto de entrada del subproceso de IP interno está en la función interna ***_nx_ip_thread_entry***. Cuando se inicia, el subproceso de IP interno completa primero la inicialización del controlador de red, que consiste en realizar tres llamadas al controlador de red específico de la aplicación. La primera llamada es para conectar el controlador de red a la instancia de IP, seguida de una llamada de inicialización, que permite al controlador de red pasar por el proceso de inicialización. Cuando el controlador de red vuelve de la inicialización (se puede suspender mientras espera a que el hardware se configure correctamente), el subproceso de IP interno vuelve a llamar al controlador de red para habilitar el vínculo. Después de que el controlador de red vuelva de la llamada para habilitar el vínculo, el subproceso de IP interno entra en una comprobación de bucle eterna de varios eventos que necesitan procesamiento para esta instancia de IP. Entre los eventos procesados en este bucle se incluyen la recepción de paquetes IP diferida, el ensamblado de fragmentos de paquetes IP, el procesamiento de ping de ICMP, el procesamiento de IGMP, el procesamiento de la cola de paquetes TCP, el procesamiento periódico de TCP, los tiempos de espera de ensamblado de fragmentos IP y el procesamiento periódico de IGMP. Los eventos también incluyen actividades de resolución de direcciones: procesamiento de paquetes ARP y procesamiento periódico de ARP en IPv4, detección de direcciones duplicadas, solicitudes de enrutador y detección de equipos cercanos en IPv6.

> [!CAUTION]
> *Las funciones de devolución de llamada de NetX Duo, incluidas las devoluciones de llamada de escucha y desconexión, se llaman desde el subproceso de IP interno, no desde el subproceso de llamada original. La aplicación debe tener cuidado de no entrar en suspensión dentro de cualquier función de devolución de llamada de NetX Duo.*

### <a name="ip-periodic-timers"></a>Temporizadores periódicos de IP

Se utilizan dos temporizadores periódicos de ThreadX para cada instancia de IP. El primero es un temporizador de un segundo para el tiempo de espera de TCP, ARP e IGMP, que también controla el procesamiento del reensamblado de fragmentos IP. El segundo es un temporizador de 100 ms para controlar el tiempo de espera de la retransmisión TCP y las operaciones relacionadas con IPv6.

### <a name="network-driver"></a>Controlador de red

Cada instancia de IP en NetX Duo tiene una interfaz principal, que se identifica mediante el controlador de dispositivo especificado en el servicio ***nx_ip_create***. El controlador de red es responsable de controlar varias solicitudes de NetX Duo, como la transmisión de paquetes, la recepción de paquetes y las solicitudes de estado y control. 

En el caso de un sistema de host múltiple, la instancia de IP tiene varias interfaces, cada una con un controlador de red asociado que realiza estas tareas para la interfaz correspondiente.

El controlador de red también debe controlar los eventos asincrónicos que se producen en el soporte físico. Los eventos asincrónicos del soporte físico incluyen la recepción de paquetes, la finalización de la transmisión de paquetes y los cambios de estado. NetX Duo proporciona al controlador de red varias funciones de acceso para controlar varios eventos. Estas funciones están diseñadas para ser llamadas desde la parte de rutina del servicio de interrupciones del controlador de red. En el caso de las redes IPv4, el controlador de red debe reenviar todos los paquetes ARP recibidos a la función interna ***_nx_arp_packet_deferred_receive***. Todos los paquetes RARP se deben reenviar a la función interna * **_nx_rarp_packet_deferred_receive** _. Hay dos opciones para los paquetes IP. Si se requiere el envío rápido de paquetes IP, los paquetes IP entrantes se deben reenviar a _ *_ _nx_ip_packet_receive_* _ para su procesamiento inmediato. Esto mejora considerablemente el rendimiento de NetX Duo en el control de paquetes IP. De lo contrario, debe reenviar los paquetes IP a _ *_ _nx_ip_packet_deferred_receive_**. Este servicio coloca el paquete IP en la cola de procesamiento diferido, donde posteriormente lo controla el subproceso de IP interno, lo que da lugar a la mínima cantidad de tiempo de procesamiento de ISR.

El controlador de red también puede diferir el procesamiento de interrupciones para quedarse fuera del contexto del subproceso de IP. En este modo, el ISR debe guardar la información necesaria, llamar a la función interna ***_nx_ip_driver_deferred_processing*** y confirmar el controlador de interrupciones. Este servicio notifica al subproceso de IP que programe una devolución de llamada al controlador del dispositivo para completar el proceso del evento que provoca la interrupción.

Algunos controladores de red pueden realizar el cálculo y la validación de la suma de comprobación de encabezados TCP/IP en hardware, sin ocupar recursos de CPU valiosos. Para aprovechar la ventaja de la característica de capacidad de hardware, NetX Duo proporciona opciones para habilitar o deshabilitar el cálculo de la suma de comprobación de software en el momento de la compilación, así como para activar o desactivar el cálculo de suma de comprobación en tiempo de ejecución, si el controlador de dispositivo es capaz de comunicarse con el nivel de IP acerca de las capacidades de hardware. Consulte [Capítulo 5: Controladores de red de Azure RTOS NetX Duo](chapter5.md) para obtener información más detallada sobre la escritura de controladores de red de NetX Duo.

### <a name="multihome-support"></a>Compatibilidad con host múltiple

NetX Duo admite sistemas conectados a varios dispositivos físicos mediante una única instancia de IP. Cada interfaz física se asigna a un bloque de control de interfaz en la instancia de IP. Las aplicaciones que deseen usar un sistema de host múltiple deben definir el valor de ***NX_MAX_PHSYCIAL_INTERFACES** _ en el número de dispositivos físicos conectados al sistema y volver a compilar la biblioteca de NetX Duo. De manera predeterminada, _ *_NX_MAX_PHYSICAL_INTERFACES_** está establecido en uno, de forma que se crea un bloque de control de interfaz en la instancia de IP.

La aplicación NetX Duo crea una única instancia de IP para el dispositivo primario mediante el servicio ***nx_ip_create** _. Para cada dispositivo de red adicional, la aplicación conecta el dispositivo a la instancia de IP mediante el servicio _ *_nx_ip_interface_attach_**.

Cada estructura de la interfaz de red contiene un subconjunto de información de red sobre la interfaz de red que se encuentra en el bloque de control IP, incluida la dirección IPv4 de la interfaz, la máscara de subred, el tamaño de MTU de IP y la información de dirección de capa MAC.

> [!NOTE]
> *NetX Duo con compatibilidad con host múltiple es compatible con versiones anteriores de NetX Duo. Los servicios que no toman información explícita de la interfaz tienen como valor predeterminado el dispositivo de red primario.*

La interfaz principal tiene el índice cero en la lista de instancias de IP. A cada dispositivo subsiguiente conectado a la instancia de IP se le asigna el siguiente índice.

Todos los servicios de protocolo de capa superior para los que la instancia de IP está habilitada, incluidos TCP, UDP, ICMP e IGMP, están disponibles para todos los dispositivos conectados.

En la mayoría de los casos, NetX Duo puede determinar la mejor dirección de origen que se va a usar al transmitir un paquete. La selección de la dirección de origen se basa en la dirección de destino. Se han agregado servicios de NetX Duo para permitir que las aplicaciones especifiquen la dirección de origen específica que se usará, en los casos en los que no se puede determinar la más adecuada en función de la dirección de destino. Un ejemplo sería en un sistema de host múltiple, una aplicación debe enviar un paquete a una difusión IPv4 o a direcciones de destino de multidifusión.

Entre los servicios específicos para desarrollar aplicaciones de host múltiple se incluyen los siguientes:

- *nx_igmp_multicast_interface_join*
- *nx_igmp_multicast_interface_leave*
- *nx_ip_driver_interface_direct_command*
- *nx_ip_interface_address_get*
- *nx_ip_interface_address_mapping_configure*
- *nx_ip_interface_address_set*  
- *nx_ip_interface_attach*
- *nx_ip_interface_capability_get* 
- *nx_ip_interface_capability_set*
- *nx_ip_interface_detach*
- *nx_ip_interface_info_get*
- *nx_ip_interface_mtu_set*
- *nx_ip_interface_physical_address_get*
- *nx_ip_interface_physical_address_set*
- *nx_ip_interface_status_check*
- *nx_ip_raw_packet_source_send*
- *nx_ipv4_multicast_interface_join*
- *nx_ipv4_multicast_interface_leave*
- *nx_udp_socket_source_send*
- *nxd_ipv6_multicast_interface_join*
- *nxd_ipv6_multicast_interface_leave* 
- *nxd_udp_socket_source_send*
- *nxd_icmp_source_ping*
- *nxd_ip_raw_packet_source_send*
- *nxd_udp_socket_source_send*

Estos servicios se explican con mayor detalle en la [Descripción de los servicios de NetX Duo](chapter4.md).

### <a name="loopback-interface"></a>Interfaz de bucle invertido

La interfaz de bucle invertido es una interfaz de red especial sin un vínculo físico conectado a ella. La interfaz de bucle invertido permite que las aplicaciones se comuniquen mediante la dirección de bucle invertido IPv4 127.0.0.1. Para usar una interfaz de bucle invertido lógico, asegúrese de que la opción configurable ***NX_DISABLE_LOOPBACK_INTERFACE*** no esté establecida.

### <a name="interface-control-blocks"></a>Bloques de control de interfaz

El número de bloques de control de interfaz de la instancia de IP es el número de interfaces físicas (definidas por ***NX_MAX_PHYSICAL_INTERFACES** _) más la interfaz de bucle invertido, si está habilitada. El número total de interfaces se define en _*_NX_MAX_IP_INTERFACES_**.

## <a name="protocol-layering"></a>Capas de protocolos

El protocolo TCP/IP implementado por NetX Duo es un protocolo en capas, lo que significa que los protocolos más complejos se crean a partir de protocolos subyacentes más simples. En TCP/IP, el protocolo de la capa más baja está en el *nivel de vínculo* y lo controla el controlador de red. Normalmente, este nivel se dirige hacia Ethernet, pero también podría ser fibra, serie o prácticamente cualquier medio físico.

Sobre el nivel de vínculo está la *capa de red*. En TCP/IP se trata del protocolo IP, que básicamente es responsable de enviar y recibir paquetes simples de la mejor forma posible a través de la red. Los protocolos de tipo de administración como ICMP e IGMP normalmente también se clasifican como capas de red, aunque se basan en IP para el envío y la recepción.

La *capa de transporte* se sitúa sobre la capa de red. Esta capa es responsable de administrar el flujo de datos entre los hosts de la red. Hay dos tipos de servicios de transporte admitidos por NetX Duo: UDP y TCP. Los servicios de UDP proporcionan la mejor opción para enviar y recibir datos entre dos hosts de una manera sin conexión, mientras que TCP proporciona un servicio orientado a la conexión confiable entre dos entidades host.

Esta estructura en capas se refleja en los paquetes de datos de red reales. Cada capa de TCP/IP contiene un bloque de información llamado encabezado. Esta técnica de rodear los datos (y posiblemente la información de protocolo) con un encabezado se llama normalmente encapsulación de datos. La figura 1 muestra un ejemplo de la disposición en capas de NetX Duo y la figura 2 muestra la encapsulación de datos resultante para los datos de UDP que se envían.

![Capas de protocolos](./media/user-guide/image12.jpg)

**FIGURA 1. Capas de protocolos**

## <a name="packet-pools"></a>Grupos de paquetes

En las aplicaciones de redes en tiempo real, la asignación de paquetes de una manera rápida y determinista siempre es un desafío. Con esto en mente, NetX Duo proporciona la capacidad de crear y administrar varios grupos de paquetes de red de tamaño fijo.

Dado que los grupos de paquetes de NetX Duo se componen de bloques de memoria de tamaño fijo, nunca hay problemas de fragmentación interna. Por supuesto, la fragmentación provoca un comportamiento que es inherentemente no determinista. Además, el tiempo necesario para asignar y liberar un paquete de NetX Duo equivale a la manipulación de una lista vinculada simple. Además, la asignación y desasignación de paquetes se realiza al inicio de la lista disponible. Esto proporciona el procesamiento de la lista vinculada más rápido posible.

![Encapsulación de datos de UDP](./media/user-guide/image13.png)

**FIGURA 2. Encapsulación de datos de UDP**

La falta de flexibilidad suele ser el principal inconveniente de los grupos de paquetes de tamaño fijo. La determinación del tamaño óptimo de la carga del paquete, que también controla el paquete entrante en el peor de los casos, es una tarea difícil. Los paquetes de NetX Duo solucionan este problema con una característica opcional llamada "encadenamiento de paquetes". Un paquete de red real puede constar de uno o varios paquetes de NetX Duo vinculados entre sí. Además, el encabezado del paquete mantiene un puntero a la parte superior del paquete. A medida que se agregan protocolos adicionales, este puntero simplemente se mueve hacia atrás y el nuevo encabezado se escribe directamente delante de los datos. Sin una tecnología de paquetes flexible, la pila tendría que asignar otro búfer y copiar los datos en un nuevo búfer con el nuevo encabezado, lo que es intensivo en procesamiento.

Dado que el tamaño de la carga de cada paquete es fijo para un grupo de paquetes determinado, los datos de la aplicación mayores que el tamaño de la carga requerirían varios paquetes encadenados juntos. Al rellenar un paquete con datos del usuario, la aplicación deberá usar el servicio ***nx_packet_data_append***. Este servicio mueve los datos de la aplicación a un paquete. En situaciones en las que un paquete no es suficiente para contener los datos del usuario, se asignan paquetes adicionales para almacenar los datos de usuario. Para usar el encadenamiento de paquetes, el controlador debe ser capaz de recibir o transmitir paquetes encadenados.

En el caso de los sistemas insertados que no necesitan usar la característica de encadenamiento de paquetes, la biblioteca de NetX Duo se puede compilar con ***NX_DISABLE_PACKET_CHAIN** _ para quitar la lógica de encadenamiento de paquetes. Tenga en cuenta que la característica de fragmentación y reensamblado de IP puede necesitar usar la característica de paquetes encadenados. Por lo tanto, la definición de _*_NX_DISABLE_PACKET_CHAIN_*_ requiere que también se defina _ *_NX_DISABLE_FRAGMENTATION_**. 

Cada grupo de memoria de paquetes de NetX Duo es un recurso público. NetX Duo no aplica restricciones sobre cómo se usan los grupos. 

### <a name="packet-pool-memory-area"></a>Área de memoria del grupo de paquetes

El área de memoria del grupo de paquetes se especifica durante la creación. Como sucede con otras áreas de memoria de objetos de ThreadX y NetX Duo, se puede ubicar en cualquier parte del espacio de direcciones del destino. 

Se trata de una característica importante porque ofrece a la aplicación una flexibilidad considerable. Por ejemplo, imagine que un producto de comunicación tiene un área de memoria de alta velocidad para los búferes de red. Este área de memoria se emplea fácilmente convirtiéndola en un grupo de memoria de paquetes de NetX Duo.

### <a name="creating-packet-pools"></a>Creación de grupos de paquetes

Los grupos de paquetes se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de la aplicación. No hay ningún límite en el número de grupos de memoria de paquetes en una aplicación de NetX Duo.

### <a name="dual-packet-pool"></a>Grupo de paquetes dual

Normalmente, el tamaño de carga del grupo de paquetes IP predeterminado es lo suficientemente grande como para acomodar el tamaño del marco hasta la MTU de la interfaz de red. Durante el funcionamiento normal, el subproceso de IP necesita enviar mensajes como ARP, mensajes de control TCP, mensajes de IGMP o mensajes de ICMPv6. Estos mensajes usan los paquetes asignados del grupo de paquetes predeterminado en la instancia de IP. En un sistema con memoria restringida donde la cantidad de memoria disponible para el grupo de paquetes es limitada, es posible que el uso de un único grupo de paquetes (con el tamaño de carga grande para que coincida con el tamaño de la MTU) no sea una solución óptima. NetX Duo permite a la aplicación instalar un grupo de paquetes auxiliar, donde el tamaño de carga es menor. Una vez instalado el grupo de paquetes auxiliar, el subproceso auxiliar de IP asignaría los paquetes del grupo de paquetes predeterminado o del grupo auxiliar, dependiendo del tamaño del mensaje que transmita. Para un grupo de paquetes auxiliar, un tamaño de carga de 200 bytes funcionaría con la mayoría de los mensajes que el subproceso auxiliar de IP transmite.

De forma predeterminada, la biblioteca de NetX Duo se crea sin habilitar el grupo de paquetes dual. Para habilitar la característica, compile la biblioteca con ***NX_DUAL_PACKET_POOL_ENABLE** _ definido. A continuación, se puede establecer el grupo de paquetes auxiliar mediante una llamada a _*_nx_ip_auxiliary_packet_pool_set_**.

También existe la opción de crear más de un grupo de paquetes. Por ejemplo, un grupo de paquetes de transmisión se crea con un tamaño de carga óptimo para los tamaños de mensaje esperados. Se crea un grupo de paquetes de recepción en el controlador con un tamaño de carga establecido en la MTU del controlador, ya que no se puede predecir el tamaño de los paquetes recibidos.

### <a name="packet-header-nx_packet"></a>Encabezado de paquete NX_PACKET   
De manera predeterminada, NetX Duo coloca el encabezado del paquete inmediatamente antes del área de la carga del paquete. El grupo de memoria de paquetes es básicamente una serie de paquetes: encabezados seguidos inmediatamente por la carga del paquete. El encabezado del paquete (***NX_PACKET***) y el diseño del grupo de paquetes se muestran en la figura 3.

En el caso de los controladores de dispositivos de red que pueden realizar operaciones sin copia, normalmente la dirección inicial del área de la carga del paquete se programa en la lógica de DMA. Algunos motores de DMA tienen un requisito de alineación en el área de la carga. Para que la dirección inicial del área de carga se alinee correctamente con el motor DMA o la operación de caché, el usuario puede definir el símbolo ***NX_PACKET_ALIGNMENT***.

> [!WARNING]
> *Es importante que el controlador de red use la función **nx_packet_transmit_release** cuando se complete la transmisión de un paquete. Esta función realiza una comprobación para asegurarse de que el paquete no forma parte de una cola de salida TCP antes de que se vuelva a colocar en el grupo disponible.*

![Diseño del encabezado del paquete y del grupo de paquetes](./media/user-guide/image14.jpg)

**FIGURA 3. Diseño del encabezado del paquete y del grupo de paquetes**

Los campos del encabezado del paquete se definen de la siguiente manera. Tenga en cuenta que esta tabla no es una lista exhaustiva de todos los miembros de la estructura *NX_PACKET*.

|Encabezado de paquete | Propósito |
|---|---|
|***nx_packet_pool_owner***|Este campo apunta al grupo de paquetes que posee este paquete en particular. Cuando se libera el paquete, se libera a este grupo en particular. Con la propiedad del grupo dentro de cada paquete, es posible que un datagrama abarque varios paquetes de varios grupos de paquetes.|
|***nx_packet_next** _|Este campo apunta al siguiente paquete dentro del mismo marco. Si es NULL, no hay paquetes adicionales que formen parte del marco. Este campo se usa para mantener los paquetes fragmentados hasta que se pueda volver a ensamblar todo el paquete. Se quita si se define _*_NX_DISABLE_PACKET_CHAIN_**.|
|***nx_packet_last** _|Este campo apunta al último paquete que se encuentra en el mismo paquete de red. Si es NULL, este paquete representa todo el paquete de red. Este campo se quita si se define _*_NX_DISABLE_PACKET_CHAIN_**.|
|***nx_packet_length** _| Este campo contiene el número total de bytes de todo el paquete de red, incluido el total de todos los bytes de todos los paquetes encadenados mediante el miembro _nx_packet_next*.|
|***nx_packet_ip_interface***| Este campo es el bloque de control de la interfaz, que se asigna al paquete cuando lo recibe el controlador de interfaz y por NetX Duo para los paquetes salientes. Un bloque de control de interfaz describe la interfaz, por ejemplo, la dirección de red, la dirección MAC, la dirección IP y el estado de la interfaz, como el vínculo habilitado y la asignación física necesaria.|
|***nx_packet_data_start** _| Este campo apunta al inicio del área de la carga física de este paquete. No tiene que estar inmediatamente después del encabezado NX_PACKET, pero ese es el valor predeterminado para el servicio _ *_nx_packet_pool_create_**.|
|***nx_packet_data_end** _|Este campo apunta al final del área de la carga física de este paquete. La diferencia entre este campo y el campo _nx_packet_data_start* representa el tamaño de la carga.|
|***nx_packet_prepend_ptr** _|Este campo apunta a la ubicación donde se agregan los datos de los paquetes, ya sea el encabezado de protocolo o los datos reales, delante de los datos de los paquetes existentes (si existen) en el área de carga de paquetes. Debe ser mayor o igual que la ubicación del puntero _nx_packet_data_start* y menor o igual que el puntero *nx_packet_append_ptr*.|
> [!CAUTION]
> *Por motivos de rendimiento, NetX Duo supone que cuando el paquete se pasa a los servicios de NetX Duo para su transmisión, el puntero antepuesto apunta a una dirección alineada para palabra larga.*

| Encabezado de paquete | Fin |
|---|---|
|***nx_packet_append_ptr** _|Este campo apunta al final de los datos que se encuentran actualmente en el área de carga de paquetes. Debe encontrarse entre la ubicación de memoria a la que apuntan _nx_packet_prepend_ptr* y *nx_packet_data_end.* La diferencia entre este campo y el campo *nx_packet_prepend_ptr* representa la cantidad de datos de este paquete.|
|***nx_packet_packet_pad** _|Este campo define la longitud del relleno en palabras de 4 bytes para lograr el requisito de alineación deseado. Este campo se quita si no se define _*_NX_PACKET_HEADER_PAD_*_. Como alternativa, se puede usar _*_NX_PACKET_ALIGNMENT_*_ en lugar de definir _nx_packet_header_pad.*|

### <a name="packet-header-offsets"></a>Desplazamientos de encabezados de paquetes

El tamaño del encabezado del paquete se define para dejar espacio suficiente para acomodar el tamaño del encabezado. El servicio ***nx_packet_allocate*** se utiliza para asignar un paquete y ajusta el puntero antepuesto del paquete según el tipo de paquete especificado. El tipo de paquete indica a NetX Duo el desplazamiento necesario para insertar el encabezado de protocolo (por ejemplo, UDP, TCP o ICMP) delante de los datos del protocolo.

Los siguientes tipos se definen en NetX Duo para tener en cuenta el encabezado IP y el encabezado de capa física (Ethernet) del paquete. En el último caso, se supone que tiene 16 bytes para tener en cuenta la alineación de 4 bytes necesaria. Los paquetes IPv4 siguen definidos en NetX Duo para que las aplicaciones asignen paquetes para redes IPv4. Tenga en cuenta que si la biblioteca de NetX Duo se compila con IPv6 habilitado, los tipos de paquetes genéricos (como NX_IP_PACKET) se asignan a la versión de IPv6. Si la biblioteca de NetX Duo se compila sin habilitar IPv6, estos tipos de paquetes genéricos se asignan a la versión IPv4.

En la tabla siguiente se muestran los símbolos definidos con IPv6 habilitado:

|**Tipo de paquete** |**Valor** |
|---|---|
|NX_IPv6_PACKET (NX_IP_PACKET) | 0x38 |
|NX_UDPv6_PACKET (NX_UDP_PACKET) |0x40 |
|NX_TCPv6_PACKET (NX_TCP_PACKET) |0x4c |
|NX_IPv4_PACKET |0x24 |
|NX_IPv4_UDP_PACKET |0x2c |
|NX_IPv4_TCP_PACKET |0x38 |

En la tabla siguiente se muestran los símbolos definidos con IPv6 deshabilitado:

|**Tipo de paquete** |**Valor** |
|---|---|
|NX_IPv4_PACKET (NX_IP_PACKET) |0x24 |
|NX_IPv4_UDP_PACKET (NX_UDP_PACKET) |0x2c |
|NX_IPv4_TCP_PACKET (NX_TCP_PACKET) |0x38 |

Tenga en cuenta que estos valores cambiarán si se define *NX_IPSEC_ENABLE*. Para obtener más información sobre la aplicación que usa IPsec, consulte la guía de usuario de NetX Duo IPsec.

### <a name="pool-capacity"></a>Capacidad del grupo

El número de paquetes de un grupo de paquetes es una función del tamaño de la carga y el número total de bytes del área de memoria proporcionado al servicio de creación del grupo de paquetes. La capacidad del grupo se calcula dividiendo el tamaño del paquete (incluido el tamaño del encabezado NX_PACKET, el tamaño de carga útil y la alineación adecuada) en el número total de bytes del área de memoria proporcionada.

### <a name="payload-area-alignment"></a>Alineación del área de carga

El diseño del grupo de paquetes de NetX Duo admite la operación sin copia. En el nivel de controlador de dispositivo, el controlador puede asignar el área de carga directamente a los descriptores del búfer para la recepción de datos. A veces, el motor DMA o el mecanismo de sincronización de caché requieren que la dirección inicial del área de carga tenga un determinado requisito de alineación. Esto puede lograrse mediante la definición del requisito de alineación deseado (en bytes) en ***NX_PACKET_ALIGNMENT***. Al crear un grupo de paquetes, la dirección inicial del área de carga se alineará con este valor. De forma predeterminada, la dirección de inicio tiene una alineación de 4 bytes.

### <a name="thread-suspension"></a>Suspensión de subprocesos

Los subprocesos de la aplicación se pueden suspender mientras se espera un paquete de un grupo vacío. Cuando se devuelve un paquete al grupo, el subproceso suspendido recibe este paquete y se reanuda.

Si se suspenden varios subprocesos en el mismo grupo de paquetes, se reanudan en el orden en que se suspendieron (FIFO).

### <a name="pool-statistics-and-errors"></a>Estadísticas y errores del grupo

Si está habilitado, el software de administración de paquetes de NetX Duo realiza el seguimiento de varias estadísticas y errores que pueden ser útiles para la aplicación. Se mantienen las estadísticas y los informes de errores siguientes para los grupos de paquetes:

- Número total de paquetes en el grupo
- Paquetes libres en el grupo
- Total de asignaciones de paquetes
- Solicitudes de asignación de grupos vacíos
- Suspensiones de asignación de grupos vacíos
- Liberaciones de paquetes no válidas

Todos estos informes de errores y estadísticas, excepto el total y el número de paquetes libres del grupo, están integrados en la biblioteca de NetX Duo a menos que se defina ***NX_DISABLE_PACKET_INFO** _. Estos datos están disponibles para la aplicación con el servicio _ *_nx_packet_pool_info_get_**.

### <a name="packet-pool-control-block-nx_packet_pool"></a>Bloque de control del grupo de paquetes NX_PACKET_POOL

Las características de cada grupo de memoria de paquetes se encuentran en su bloque de control. Contiene información útil, como la lista vinculada de paquetes libres, el número de paquetes libres y el tamaño de la carga de los paquetes de este grupo. Esta estructura se define en el archivo ***tx_api.h***.

Los bloques de control del grupo de paquetes se pueden ubicar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global mediante su definición fuera del ámbito de cualquier función.

## <a name="ipv4-protocol"></a>Protocolo IPv4

El componente del protocolo de Internet (IP) de NetX Duo es responsable de enviar y recibir paquetes IPv4 en Internet. En NetX Duo, es el componente responsable en última instancia de enviar y recibir mensajes TCP, UDP, ICMP e IGMP, mediante el controlador de red subyacente.

NetX Duo es compatible con el protocolo IPv4 (RFC 791) y el protocolo IPv6 (RFC 2460). En esta sección se describe IPv4. IPv6 se describe en la sección siguiente.

### <a name="ipv4-addresses"></a>Direcciones IPv4

Cada host de Internet tiene un identificador único de 32 bits que se conoce como una dirección IP. Hay cinco clases de direcciones IPv4, como se describe en la figura 4. Los intervalos de las cinco clases de direcciones IPv4 son los siguientes:

|Clase|Intervalo|
|---|---|
|A |De 0.0.0.0 a 127.255.255.255|
|B |De 128.0.0.0 a 191.255.255.255|
|C |De 192.0.0.0 a 223.255.255.255|
|D |De 224.0.0.0 a 239.255.255.255|
|E |240.0.0.0 a 247.255.255.255|

![Diagrama de la estructura de direcciones IPv4.](./media/user-guide/ipv4-address-structure.png)

### <a name="figure-4-ipv4-address-structure"></a>FIGURA 4. Estructura de una dirección IPv4

También hay tres tipos de especificaciones de dirección: *unidifusión*, *difusión* y *multidifusión*. Las direcciones de unidifusión son aquellas direcciones IPv4 que identifican un host específico en Internet. Las direcciones de unidifusión pueden ser una dirección IPv4 de origen o de destino. Las direcciones de difusión identifican todos los hosts de una red o subred específicas y solo se pueden usar como direcciones de destino. Las direcciones de difusión se especifican con la parte del identificador de host de la dirección establecida en unos. Las direcciones de multidifusión (clase D) especifican un grupo dinámico de hosts en Internet. Los miembros del grupo de multidifusión pueden unirse y salir siempre que lo deseen.

> [!IMPORTANT]
> *Solo los protocolos sin conexión como UDP sobre IPv4 pueden emplear la difusión y la funcionalidad de difusión limitada del grupo de multidifusión.*

> [!IMPORTANT]
> *La macro *IP_ADDRESS*  se define en el archivo ***nx_api.h** _. Permite una especificación sencilla de direcciones IPv4 mediante comas en lugar de puntos. Por ejemplo, _IP_ADDRESS(128, 0, 0, 0)* especifica la primera dirección de clase B que se muestra en la figura 4.*

### <a name="ipv4-gateway-address"></a>Dirección de puerta de enlace IPv4

Las puertas de enlace de red ayudan a los hosts de sus redes a retransmitir paquetes destinados a destinos fuera del dominio local. Cada nodo tiene cierto conocimiento del próximo salto al que se va hacer el envío, ya sea el destino de uno de sus equipos cercanos o mediante una tabla de enrutamiento estático programada previamente. Sin embargo, si se produce un error en estos enfoques, el nodo debe reenviar el paquete a su puerta de enlace predeterminada, que conoce mejor cómo enrutar el paquete a su destino. Tenga en cuenta que la puerta de enlace predeterminada debe ser accesible directamente mediante una de las interfaces físicas asociadas a la instancia de IP. La aplicación llama a ***nx_ip_gateway_address_set** _ para configurar la dirección de la puerta de enlace predeterminada de IPv4. Use el servicio _*_nx_ip_gateway_address_get_*_ para recuperar la configuración actual de la puerta de enlace de IPv4. La aplicación usará el servicio _ *_nx_ip_gateway_address_clear_** para borrar la configuración de la puerta de enlace.

### <a name="ipv4-header"></a>Encabezado IPv4

Para que cualquier paquete IPv4 se envíe a Internet, debe tener un encabezado IPv4. Cuando los protocolos de nivel superior (UDP, TCP, ICMP o IGMP) llaman al componente IP para enviar un paquete, el módulo de transmisión IPv4 coloca un encabezado IPv4 delante de los datos. Por el contrario, cuando se reciben paquetes IP de la red, el componente IP quita el encabezado IPv4 del paquete antes de entregarlo a los protocolos de nivel superior. En la figura 5 se muestra el formato del encabezado IP.

![Formato del encabezado IPv4](./media/user-guide/ipv4-header-format.png)

### <a name="figure-5-ipv4-header-format"></a>FIGURA 5. Formato del encabezado IPv4

> [!IMPORTANT]
> *Se espera que todos los encabezados de la implementación de TCP/IP estén en formato **big endian**. En este formato, el byte más significativo de la palabra reside en la dirección de bytes más baja. Por ejemplo, la versión de 4 bits y la longitud del encabezado de 4 bits del encabezado IP deben estar ubicadas en el primer byte del encabezado.*

Los campos del encabezado IPv4 se definen de la siguiente manera:

|Campo&nbsp;de encabezado&nbsp;IPv4 |Propósito |
|---|---|
|***4-bit version*** |Este campo contiene la versión de IP que representa este encabezado. En el caso de IP versión 4, que es lo que admite NetX Duo, el valor de este campo es 4. |
|***Longitud del encabezado de 4 bits*** |Este campo especifica el número de palabras de 32 bits del encabezado IP. Si no hay palabras de opción presentes, el valor de este campo es 5. |
|***Tipo de servicio (TOS) de 8 bits*** |Este campo especifica el tipo de servicio solicitado para este paquete IP. Las solicitudes válidas son las siguientes:<br />- Normal: 0x00 <br />- Retraso mínimo: 0x00<br />- Datos máximos: 0x08<br />- Confiabilidad máxima: 0x04<br />- Costo mínimo: 0x02 |
|***Longitud total de 16 bits*** |Este campo contiene la longitud total del datagrama IP en bytes, incluido el encabezado IP. Un datagrama IP es la unidad básica de información que se encuentra en una red de Internet con TCP/IP. Contiene una dirección de origen y de destino, además de los datos. Dado que es un campo de 16 bits, el tamaño máximo de un datagrama IP es de 65 535 bytes.|
|***identificación de 16 bits*** |El campo es un número que se usa para identificar de forma única cada datagrama IP enviado desde un host. Normalmente, este número se incrementa después de enviar un datagrama IP. Es especialmente útil para ensamblar fragmentos de paquetes IP recibidos.|
|***Marcas de 3 bits*** |Este campo contiene información de fragmentación de IP. El bit 14 es el bit "no fragmentar". Si se establece este bit, el datagrama IP saliente no se fragmentará. El bit 13 es el bit "más fragmentos". Si se establece este bit, hay más fragmentos. Si este bit está a cero, se trata del último fragmento del paquete IP.|
|***Desplazamiento de fragmento de 13 bits*** |Este campo contiene los 13 bits superiores del desplazamiento del fragmento. Por este motivo, los desplazamientos de fragmentos solo se permiten en límites de 8 bytes. El primer fragmento de un datagrama IP fragmentado tendrá el bit "más fragmentos" establecido y tendrá un desplazamiento de 0.|
|***Período de vida (TTL) de 8 bits*** |Este campo contiene el número de enrutadores que puede pasar este datagrama, lo que básicamente limita la vigencia del datagrama.|
|***Protocolo de 8 bits***|Este campo especifica el protocolo que usa el datagrama IP. A continuación se muestra una lista de protocolos válidos y sus valores:<br />- ICMP: 0x01 <br />- IGMP: 0x02<br />- TCP: 0X06<br />- UDP: 0X11 |
|***Suma de comprobación de 16 bits*** |Este campo contiene la suma de comprobación de 16 bits solo para el encabezado IP. Hay sumas de comprobación adicionales en los protocolos de nivel superior para la carga de IP. |
|***Dirección IP de origen de 32 bits*** |Este campo contiene la dirección IP del remitente y siempre es una dirección de host. |
|***Dirección IP de destino de 32 bits*** |Este campo contiene la dirección IP del receptor o los receptores, si la dirección es una dirección de difusión o multidifusión. |

### <a name="creating-ip-instances"></a>Creación de instancias de IP

Las instancias de IP se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de la aplicación. La dirección IPv4 inicial, la máscara de red, el grupo de paquetes predeterminado, el controlador multimedia, y la memoria y la prioridad del subproceso IP interno se definen mediante el servicio de ***nx_ip_create***, aunque la aplicación tenga previsto usar solo redes IPv6. Si la aplicación inicializa la instancia de IP con su dirección IPv4 establecida en una dirección no válida (0.0.0.0), se supone que la dirección de la interfaz se resolverá con una configuración manual más adelante, mediante RARP, DHCP o protocolos similares.

En sistemas con varias interfaces de red, la interfaz principal se designa al llamar a ***nx_ip_create** _. Cada interfaz adicional se puede conectar a la misma instancia de IP mediante una llamada a _*_nx_ip_interface_attach_**. Este servicio almacena información sobre la interfaz de red (como la dirección IP o la máscara de red) en el bloque de control de la interfaz y asocia la instancia del controlador con el bloque de control de la interfaz en la instancia de IP. Cuando el controlador recibe un paquete de datos, debe almacenar la información de la interfaz en la estructura NX_PACKET antes de reenviarlo a la lógica de recepción de IP. Tenga en cuenta que se debe haber creado una instancia de IP antes de conectar cualquier interfaz.

Los servicios IPv6 no se inician después de llamar a ***nx_ip_create** _. Las aplicaciones que deseen usar servicios IPv6 deben llamar al servicio _ *_nx_ipv6_enable_** para iniciar IPv6.

En la red IPv6, cada interfaz de una instancia de IP puede tener varias direcciones globales de IPv6. Además de usar DHCPv6 para la asignación de direcciones IPv6, un dispositivo también puede usar la configuración automática de direcciones sin estado. Puede encontrar más información en las secciones "Bloque de control de IP" y "Resolución de direcciones IPv6" más adelante en este capítulo.

### <a name="ip-send"></a>Envío de IP

El procesamiento del envío de IP en NetX Duo está muy optimizado. El puntero antepuesto del paquete se mueve hacia atrás para acomodar el encabezado IP. Se completa el encabezado IP (con todas las opciones especificadas por la capa de protocolo de llamada), se calcula en línea la suma de comprobación de IP (solo para paquetes IPv4) y se envía el paquete al controlador de red asociado. Además, la fragmentación de salida también se coordina desde el procesamiento de envío de IP.

En el caso de IPv4, NetX Duo inicia solicitudes ARP si se necesita asignación física para la dirección IP de destino. IPv6 usa la detección de equipos cercanos para la asignación de la dirección IPv6 a una dirección física.

> [!NOTE]
> *En cuanto a la conectividad IPv4, los paquetes que requieren la resolución de direcciones IP (por ejemplo, la asignación física) se ponen en la cola de ARP hasta que el número de paquetes de la cola supera la profundidad de la cola de ARP (definida por el símbolo **NX_ARP_MAX_QUEUE_DEPTH**). Si se alcanza la profundidad de la cola, NetX Duo quitará el paquete más antiguo de la cola y seguirá esperando a la resolución de direcciones para el resto de paquetes en cola. Por otro lado, si no se resuelve una entrada de ARP, los paquetes pendientes en la entrada de ARP se liberan tras el tiempo de espera de entrada de ARP.*

En el caso de sistemas con varias interfaces de red, NetX Duo elige una interfaz en función de la dirección IP de destino. El siguiente procedimiento se aplica al proceso de selección:

1. Si el remitente especifica una interfaz de salida que es válida, úsela.
2. Si una dirección de destino es de difusión o multidifusión IPv4, se usa la primera interfaz física habilitada.
3. Si la dirección de destino se encuentra en la tabla de enrutamiento estático, se usa la interfaz asociada a la puerta de enlace.
4. Si el destino es en vínculo, se usa la interfaz en vínculo.
5. Si la dirección de destino es una dirección local de vínculo (169.254.0.0/16), se usa la primera interfaz válida.
6. Si la puerta de enlace predeterminada está configurada correctamente, se usa la interfaz asociada a la puerta de enlace predeterminada para transmitir el paquete.
7. Por último, si una de las direcciones IP de interfaz válida es una dirección local de vínculo (169.254.0.0/16), esta interfaz se utiliza como dirección de origen para la transmisión.
8. El paquete de salida se elimina si fracasa todo lo anterior.

### <a name="ip-receive"></a>Recepción de IP

El procesamiento de recepción de IP se llama desde el controlador de red o desde el subproceso de IP interno (para procesar los paquetes de la cola de paquetes recibidos diferida). El procesamiento de recepción de IP examina el campo de protocolo e intenta enviar el paquete al componente de protocolo adecuado. Antes de que el paquete se envíe realmente, el encabezado IP se quita adelantando el puntero antepuesto después del encabezado IP.

El procesamiento de recepción de IP también detecta paquetes IP fragmentados y realiza los pasos necesarios para volver a ensamblarlos si está habilitada la fragmentación. Si la fragmentación es necesaria pero no está habilitada, se elimina el paquete.

NetX Duo determina la interfaz de red adecuada en función de la interfaz especificada en el paquete. Si la interfaz del paquete es NULL, el valor predeterminado de NetX Duo es la interfaz principal. Esto se hace para garantizar la compatibilidad con controladores Ethernet de NetX Duo heredados.

### <a name="raw-ip-send"></a>Envío de Raw IP

Un paquete Raw IP es un marco IP que contiene una carga de protocolo de nivel superior no admitida directamente (ni procesada) por NetX Duo. Un paquete sin formato permite a los desarrolladores definir sus propias aplicaciones basadas en IP. Una aplicación puede enviar paquetes Raw IP directamente mediante el servicio ***nxd_ip_raw_packet_send** _ si se ha habilitado el procesamiento de paquetes Raw IP con el servicio _*_nx_ip_raw_packet_enabled_*_. Cuando se transmite un paquete de unidifusión en una red IPv6, NetX Duo determina automáticamente la mejor dirección IPv6 de origen que se debe usar para enviar los paquetes en función de la dirección de destino. Sin embargo, si la dirección de destino es una dirección de multidifusión (o de difusión para IPv4), el valor predeterminado de NetX Duo es la primera interfaz (principal). Por lo tanto, para enviar estos paquetes mediante las interfaces secundarias, la aplicación debe usar el servicio _ *_nx_ip_raw_packet_source_send_** para especificar la dirección de origen que se va a utilizar para el paquete saliente.

### <a name="raw-ip-receive"></a>Recepción de IP sin formato

Si está habilitado el procesamiento de paquetes IP sin formato, la aplicación puede recibir paquetes IP sin formato mediante el servicio ***nx_ip_raw_packet_receive** _. Todos los paquetes entrantes se procesan según el protocolo especificado en el encabezado IP. Si el protocolo especifica UDP, TCP, IGMP o ICMP, NetX Duo procesará el paquete con el controlador adecuado para el tipo de protocolo del paquete. Si el protocolo no es uno de los indicados y la recepción de Raw IP está habilitada, el paquete entrante se colocará en la cola de paquetes sin procesar en espera de que la aplicación lo reciba a través del servicio _*_nx_ip_raw_packet_receive_**. Además, los subprocesos de aplicación se pueden suspender con un tiempo de espera opcional mientras esperan un paquete Raw IP. El número de paquetes que se pueden poner en cola en la cola de paquetes sin procesar es limitado. El valor máximo se define en ***NX_IP_RAW_MAX_QUEUE_DEPTH**_, cuyo valor predeterminado es 20. Una aplicación puede cambiar el valor máximo mediante una llamada al servicio _ *_nx_ip_raw_receive_queue_max_set_**.

Como alternativa, la biblioteca de NetX Duo puede compilarse con ***NX_ENABLE_IP_RAW_PACKET_FILTER*.** En este modo de funcionamiento, la aplicación proporciona una función de devolución de llamada que se invoca cada vez que se recibe un paquete con un tipo de protocolo no controlado. La lógica de recepción de IP reenvía el paquete a la rutina de filtro de recepción de paquetes sin procesar definida por el usuario. La rutina de filtro decide si se debe mantener el paquete sin procesar para futuros procesos. El valor devuelto de la rutina de devolución de llamada indica si el paquete se ha procesado mediante el filtro de recepción de paquetes sin procesar. Si la función de devolución de llamada procesa el paquete, el paquete debe liberarse cuando la aplicación termine de utilizarlo. De lo contrario, NetX Duo es responsable de liberar el paquete. Consulte **_nx_ip_raw_packet_filter_set_** para obtener más información sobre cómo usar la función de filtro de paquetes sin procesar.

> [!NOTE]
> *La función de contenedor BSD para NetX Duo se basa en la función de filtro de paquetes sin procesar para controlar los sockets sin procesar de BSD. Por lo tanto, para admitir sockets sin procesar en el contenedor BSD, la biblioteca de NetX Duo debe compilarse con ***NX_ENABLE_IP_RAW_PACKET_FILTER** _ definido, y la aplicación no debe usar _*_nx_ip_raw_packet_filter_set_*_ para instalar sus propias funciones de filtro de paquetes sin procesar._

### <a name="default-packet-pool"></a>Grupo de paquetes predeterminado

A cada instancia de IP se le asigna un grupo de paquetes predeterminado durante la creación. Este grupo de paquetes se usa para asignar paquetes para ARP, RARP, ICMP, IGMP, distintos paquetes de control TCP (SYN, ACK, etc.), detección de equipos cercanos, detección de enrutadores y detección de direcciones duplicadas. Si el grupo de paquetes predeterminado está vacío cuando NetX Duo necesita asignar un paquete, es posible que NetX Duo deba cancelar esa operación específica y devolverá un mensaje de error si es posible.

### <a name="ip-helper-thread"></a>Subproceso auxiliar de IP

Cada instancia de IP tiene un subproceso auxiliar. Este subproceso es responsable de controlar todo el procesamiento de paquetes diferido y todo el procesamiento periódico. El subproceso auxiliar de IP se crea en ***nx_ip_create***.Aquí es donde el subproceso tiene su pila y prioridad. Tenga en cuenta que el primer procesamiento del subproceso auxiliar de IP es para finalizar la inicialización del controlador de red asociado con el servicio de creación de IP. Una vez completada la inicialización del controlador de red, el subproceso auxiliar inicia un bucle sin fin para procesar paquetes y solicitudes periódicas.

> [!IMPORTANT]
> *Si se observa un comportamiento no explicado en el subproceso auxiliar de IP, el primer paso de depuración es el aumento del tamaño de la pila durante el servicio de creación de IP. Si la pila es demasiado pequeña, es posible que el subproceso auxiliar de IP sobrescriba la memoria, lo que puede causar problemas inusuales.*

### <a name="thread-suspension"></a>Suspensión de subprocesos

Los subprocesos de la aplicación se pueden suspender al intentar recibir paquetes IP sin formato. Después de recibir un paquete sin formato, se asigna el nuevo paquete al primer subproceso suspendido y se reanuda dicho subproceso. Todos los servicios de NetX Duo para la recepción de paquetes tienen un tiempo de espera de suspensión opcional. Cuando se recibe un paquete o se agota el tiempo de espera, el subproceso de la aplicación se reanuda con el estado de finalización adecuado.

### <a name="ip-statistics-and-errors"></a>Estadísticas y errores de IP

Si se habilita, NetX Duo realiza un seguimiento de varias estadísticas y errores que pueden ser útiles para la aplicación. Se mantienen las estadísticas y los informes de errores siguientes para cada instancia de IP:

- Número total de paquetes IP enviados
- Número total de bytes IP enviados
- Número total de paquetes IP recibidos
- Número total de bytes IP recibidos
- Número total de paquetes IP no válidos
- Número total de paquetes de recepción de IP eliminados
- Número total de errores de suma de comprobación de recepción de IP
- Número total de paquetes de envío de IP eliminados
- Número total de fragmentos IP enviados
- Número total de fragmentos IP recibidos

Todos estos informes de errores y estadísticas están disponibles para la aplicación con el servicio ***nx_ip_info_get***.

### <a name="ip-control-block-nx_ip"></a>Bloque de control de IP NX_IP

Las características de cada instancia de IP se encuentran en su bloque de control. Contiene información útil, como las direcciones IP y las máscaras de red de cada dispositivo de red, y una tabla de asignación de direcciones IP de equipos cercanos y hardware físico. Esta estructura se define en el archivo ***nx_api.h**. Si IPv6 está habilitado, también contiene una matriz de direcciones IPv6, cuyo número se especifica mediante la opción configurable por el usuario _*_NX_MAX_IPV6_ADDRESSES_**. El valor predeterminado permite que cada interfaz de red física tenga tres direcciones IPv6.

Los bloques de control de instancias de IP se pueden ubicar en cualquier parte de la memoria, pero es más común convertir el bloque de control en una estructura global definiéndolo fuera del ámbito de cualquier función.

### <a name="static-ipv4-routing"></a>Enrutamiento IPv4 estático

La característica de enrutamiento estático permite que una aplicación especifique una red IPv4 y una dirección de próximo salto para direcciones IP de destino específicas fuera de la red. Si está habilitado el enrutamiento estático, NetX Duo busca en la tabla de enrutamiento estática una entrada que coincida con la dirección de destino del paquete que se va a enviar. Si no se encuentra ninguna coincidencia, NetX Duo busca en la lista de interfaces físicas y elige una dirección IP de origen y una dirección del próximo salto en función de la dirección IP de destino y la máscara de red. Si el destino no coincide con ninguna de las direcciones IP de los controladores de red conectados a la instancia de IP, NetX Duo elige una interfaz que esté conectada directamente a la puerta de enlace predeterminada y usa la dirección IP de la interfaz como dirección de origen y la puerta de enlace predeterminada como el próximo salto.

Se pueden agregar y quitar entradas de la tabla de enrutamiento estático mediante los servicios ***nx_ip_static_route_add** _ y _ *_nx_ip_static_route_delete_**, respectivamente. Para usar el enrutamiento estático, la aplicación host debe habilitar esta característica mediante la definición de ***NX_ENABLE_IP_STATIC_ROUTING.***

> [!NOTE]
> *Cuando se agrega una entrada a la tabla de enrutamiento estático, NetX Duo comprueba si ya hay una entrada coincidente para la dirección de destino especificada en la tabla. Si existe una, da preferencia a la entrada con la red más pequeña (prefijo más largo) de la máscara de red.*

### <a name="ipv4-forwarding"></a>Reenvío IPv4

Si el paquete IPv4 entrante no está destinado a este nodo y la característica de reenvío IPv4 está habilitada, NetX Duo intenta reenviar el paquete a través de las otras interfaces.  

### <a name="ip-fragmentation"></a>Fragmentación de IP

El dispositivo de red puede tener límites en cuanto al tamaño de los paquetes salientes. Este límite se llama unidad de transmisión máxima (MTU). La MTU de IP es el tamaño de marco de IP más grande que un controlador de capa de vínculo puede transmitir sin fragmentar el paquete IP. Durante la fase de inicialización de un controlador de dispositivo, el módulo del controlador debe configurar su tamaño de MTU de IP mediante el servicio ***nx_ip_interface_mtu_set.***

Aunque no se recomienda, la aplicación puede generar datagramas mayores que la MTU de IP subyacente admitida por el dispositivo. Antes de transmitir este tipo de datagrama IP, la capa de IP debe fragmentar estos paquetes. Al recibir marcos IP fragmentados, el extremo receptor debe almacenar todos los marcos IP fragmentados con el mismo identificador de fragmentación y volver a ensamblarlos en orden. Si la lógica de recepción de IP no puede recopilar todos los fragmentos para restaurar el marco de IP original a tiempo, se liberan todos los fragmentos. El protocolo de la capa superior debe detectar esta pérdida de paquetes y realizar la recuperación pertinente.

La fragmentación de IP se aplica a los paquetes IPv4 e IPv6.

Con el fin de admitir la fragmentación de IP y la operación de reensamblado, el diseñador del sistema debe habilitar la característica de fragmentación de IP en NetX Duo mediante el servicio ***nx_ip_fragment_enable***. Si esta característica no está habilitada, se descartan los paquetes IP fragmentados entrantes, así como los paquetes que superan la MTU del controlador de red.

> [!NOTE]
> *La lógica de fragmentación de IP se puede quitar por completo mediante la definición de ***NX_DISABLE_FRAGMENTATION** _ al compilar la biblioteca de NetX Duo. Esto ayuda a reducir el tamaño del código de NetX Duo. Tenga en cuenta que, en esta situación, las funciones de fragmentación y reensamblado de IPv4 e IPv6 se deshabilitan._

> [!NOTE]
> *Si se define **NX_DISABLE_CHAINED_PACKET**, se debe deshabilitar la fragmentación de IP.*

> [!NOTE]
> *En una red IPv6, los enrutadores no fragmentan un datagrama si su tamaño supera el tamaño mínimo de la MTU. Por lo tanto, el dispositivo de envío debe determinar la MTU mínima entre el origen y el destino, y asegurarse de que el tamaño del datagrama IP no supera la MTU de la ruta de acceso. En NetX Duo, la detección de MTU de la ruta de acceso IPv6 se puede habilitar mediante la compilación de la biblioteca de NetX Duo con el símbolo **NX_ENABLE_IPV6_PATH_MTU_DISCOVERY** definido.*

## <a name="address-resolution-protocol-arp-in-ipv4"></a>Protocolo de resolución de direcciones (ARP) en IPv4

El protocolo de resolución de direcciones (ARP) es responsable de asignar de forma dinámica las direcciones IPv4 de 32 bits a las de los soportes físicos subyacentes (RFC 826). Ethernet es el soporte físico más típico y admite direcciones de 48 bits. La necesidad de ARP viene determinada por el controlador de red proporcionado al servicio ***nx_ip_create** _. Si se requiere la asignación física, el controlador de red debe usar el servicio _ *_nx_interface_address_mapping_needed_** para configurar la interfaz del controlador correctamente.

### <a name="arp-enable"></a>Habilitación de ARP

Para que ARP funcione correctamente, primero se debe habilitar desde la aplicación con el servicio ***nx_arp_enable***. Este servicio configura varias estructuras de datos para el procesamiento de ARP, incluida la creación de un área de memoria caché de ARP desde la memoria suministrada al servicio de habilitación de ARP.

### <a name="arp-cache"></a>Memoria caché de ARP

La memoria caché de ARP se puede ver como una matriz de estructuras de datos de asignaciones de ARP internas. Cada estructura interna es capaz de mantener la relación entre una dirección IP y una dirección de hardware físico. Además, cada estructura de datos tiene punteros de vínculo para que pueda formar parte de varias listas vinculadas.

La aplicación puede buscar una dirección IP desde la memoria caché de ARP proporcionando una dirección MAC de hardware mediante el servicio ***nx_arp_ip_address_find** _ si la asignación existe en la tabla de ARP. De forma similar, el servicio _ *_nx_arp_hardware_address_find_** devuelve la dirección MAC correspondiente a una dirección IP determinada.

### <a name="arp-dynamic-entries"></a>Entradas dinámicas de ARP

De manera predeterminada, el servicio de habilitación de ARP coloca todas las entradas de la memoria caché de ARP en la lista de entradas de ARP dinámicas disponibles. NetX Duo asigna una entrada de ARP dinámica de esta lista cuando se detecta una solicitud de envío a una dirección IP no asignada. Después de la asignación, se configura la entrada de ARP y se envía una solicitud ARP al soporte físico.

También se puede crear una entrada dinámica mediante el servicio ***nx_arp_dynamic_entry_set***.

> [!IMPORTANT]
> *Si todas las entradas de ARP dinámicas están en uso, la entrada de ARP usada menos recientemente se reemplaza por una nueva asignación.*

### <a name="arp-static-entries"></a>Entradas estáticas de ARP

La aplicación también puede configurar una asignación de ARP estática mediante el servicio ***nx_arp_static_entry_create** _. Este servicio asigna una entrada de ARP de la lista de entradas de ARP dinámicas y la coloca en la lista estática con la información de asignación proporcionada por la aplicación. Las entradas de ARP estáticas no están sujetas a reutilización o caducidad. La aplicación puede eliminar una entrada estática mediante el servicio _*_nx_arp_static_entry_delete_*_. Para quitar todas las entradas estáticas de la tabla de ARP, la aplicación puede utilizar el servicio _*_nx_arp_static_entries_delete_**.

### <a name="automatic-arp-entry"></a>Entrada de ARP automática

NetX Duo registra la asignación entre IP y MAC del nodo del mismo nivel después de las respuestas del nodo del mismo nivel a la solicitud ARP. NetX Duo también implementa la característica de entrada de ARP automática, con la que se registra la asignación de direcciones IP y MAC del nodo del mismo nivel en función de solicitudes ARP no realizadas desde la red. Esta característica permite que la tabla de ARP se rellene con información de los nodos del mismo nivel, lo que reduce el retraso necesario para pasar por el ciclo de solicitud y respuesta de ARP. Sin embargo, el inconveniente de habilitar ARP automático es que la tabla de ARP tiende a llenarse rápidamente en una red ocupada con muchos nodos en el vínculo local, lo que finalmente provocaría el reemplazo de las entradas de ARP.

Esta característica está habilitada de forma predeterminada. Para deshabilitarla, se debe compilar la biblioteca de NetX Duo con el símbolo ***NX_DISABLE_ARP_AUTO_ENTRY*** definido.</p>

### <a name="arp-messages"></a>Mensajes de ARP

Como se ha mencionado anteriormente, se envía un mensaje de solicitud ARP cuando la tarea de IP detecta que es necesaria una asignación para una dirección IP. Las solicitudes ARP se envían periódicamente (cada ***NX_ARP_UPDATE_RATE** _ segundos) hasta que se recibe una respuesta de ARP correspondiente. Se realiza un total de _ *_NX_ARP_MAXIMUM_RETRIES_** solicitudes ARP antes de que se abandone el intento de ARP. Cuando se recibe una respuesta de ARP, la información de la dirección física asociada se almacena en la entrada de ARP que se encuentra en la memoria caché.

En el caso de los sistemas de host múltiple, NetX Duo determina la interfaz que va a enviar las solicitudes y respuestas de ARP en función de la dirección de destino especificada.

> [!NOTE]
> *Los paquetes IP salientes se ponen en cola mientras que NetX Duo espera la respuesta de ARP. El número de paquetes IP salientes en cola se define mediante la constante **NX_ARP_MAX_QUEUE_DEPTH**.*

NetX Duo también responde a las solicitudes ARP de otros nodos de la red IPv4 local. Cuando se realiza una solicitud ARP externa que coincide con la dirección IP actual de la interfaz que recibe la solicitud ARP, NetX Duo crea un mensaje de respuesta de ARP que contiene la dirección física actual.

Los formatos de las solicitudes y respuestas de ARP para Ethernet se muestran en la figura 6 y se describen a continuación.

| **Campo de&nbsp;solicitud/respuesta**         | **Propósito**            |
| ---------------------------------- | ---------------------- |
| ***Dirección Ethernet de destino*** | Este campo de 6 bytes contiene la dirección de destino de la respuesta de ARP y es de tipo difusión (todo unos) para las solicitudes ARP. Este campo lo configura el controlador de red. 
| ***Dirección Ethernet de origen***      | Este campo de 6 bytes contiene la dirección del remitente de la solicitud o respuesta de ARP y lo configura el controlador de red. |
| ***Tipo de marco*** | Este campo de 2 bytes contiene el tipo de marco Ethernet presente y, para las solicitudes y respuestas de ARP, es igual a 0x0806. Este es el último campo que el controlador de red tiene la responsabilidad de configurar. |
| ***Tipo de hardware*** | Este campo de 2 bytes contiene el tipo de hardware, que es 0x0001 para Ethernet. |
| ***Tipo de protocolo*** | Este campo de 2 bytes contiene el tipo de protocolo, que es 0x0800 para las direcciones IP. |
| ***Tamaño de hardware*** | Este campo de 1 byte contiene el tamaño de la dirección de hardware, que es 6 para las direcciones Ethernet. |

![Diagrama del formato de paquetes ARP.](./media/user-guide/arp-packet-format.png)

**FIGURA 6. Formato de paquetes ARP**

| Campo de&nbsp;solicitud/respuesta | Propósito |
|---|---|
| ***Tamaño de protocolo*** | Este campo de 1 byte contiene el tamaño de la dirección IP, que es 4 para las direcciones IP. |
| ***Código de la operación*** | Este campo de 2 bytes contiene la operación para este paquete ARP. Una solicitud ARP se especifica con el valor 0x0001, mientras que una respuesta de ARP se representa con el valor 0x0002. |
| ***Dirección Ethernet del remitente*** | Este campo de 6 bytes contiene la dirección Ethernet del remitente. |
| ***Dirección IP del remitente*** | Este campo de 4 bytes contiene la dirección IP del remitente. |
| ***Dirección Ethernet de destino*** | Este campo de 6 bytes contiene la dirección Ethernet de destino. |
| ***Dirección IP de destino*** | Este campo de 4 bytes contiene la dirección IP de destino. |

> [!NOTE]
> *Las solicitudes y respuestas de ARP son paquetes de nivel Ethernet. Todos los demás paquetes TCP/IP se encapsulan con un encabezado de paquete IP.*

> [!NOTE]
> *Se espera que todos los mensajes de ARP de la implementación de TCP/IP estén en formato **big endian**. En este formato, el byte más significativo de la palabra reside en la dirección de bytes más baja.*

### <a name="arp-aging"></a>Caducidad de ARP

NetX admite la invalidación automática de las entradas de ARP dinámicas. ***NX_ARP_EXPIRATION_RATE** _ especifica el número de segundos que una dirección IP establecida en una asignación física sigue siendo válida. Después de la expiración, la entrada de ARP se quita de la memoria caché de ARP. El siguiente intento de envío a la dirección IP correspondiente dará como resultado una nueva solicitud ARP. Si se establece _ *_NX_ARP_EXPIRATION_RATE_** en cero, se deshabilita la caducidad de ARP, que es la configuración predeterminada.

### <a name="arp-defend"></a>Protección de ARP

Cuando se recibe una solicitud ARP o un paquete de respuesta de ARP y el remitente tiene la misma dirección IP, que entra en conflicto con la dirección IP de este nodo, NetX Duo envía una solicitud ARP para esa dirección como protección. Si el paquete ARP en conflicto se recibe más de una vez en 10 segundos, NetX no envía más paquetes de protección. El intervalo predeterminado de 10 segundos se puede redefinir mediante ***NX_ARP_DEFEND_INTERVAL** _. Este comportamiento sigue la directiva especificada en el punto 2.4(c) de RFC5227. Dado que Windows XP omite el anuncio de ARP como respuesta para su sondeo de ARP, el usuario puede definir _ *_NX_ARP_DEFEND_BY_REPLY_** para enviar la respuesta de ARP como protección adicional.

### <a name="arp-statistics-and-errors"></a>Estadísticas y errores de ARP

Si se habilita, el software de ARP de NetX Duo realiza un seguimiento de varias estadísticas y errores que pueden ser útiles para la aplicación. Se mantienen las estadísticas y los informes de errores siguientes para cada procesamiento de ARP de IP:

- Número total de solicitudes ARP enviadas
- Número total de solicitudes ARP recibidas
- Número total de respuestas de ARP enviadas 
- Número total de respuestas de ARP recibidas 
- Número total de entradas dinámicas de ARP 
- Número total de entradas estáticas de ARP 
- Número total de entradas caducadas de ARP 
- Número total de mensajes no válidos de ARP 

Todos estos informes de errores y estadísticas están disponibles para la aplicación con el servicio ***nx_arp_info_get***.

## <a name="reverse-address-resolution-protocol-rarp-in-ipv4"></a>Protocolo de resolución inversa de direcciones (RARP) en IPv4

El protocolo de resolución inversa de direcciones (RARP) es el protocolo para solicitar la asignación de red de las direcciones IP de 32 bits del host (RFC 903). Esto se realiza mediante una solicitud RARP y continúa periódicamente hasta que un miembro de la red asigna una dirección IP a la interfaz de red del host en una respuesta de RARP. La aplicación crea una instancia de IP mediante el servicio ***nx_ip_create*** con una dirección IP establecida en cero. Si la aplicación habilita RARP, puede usar el protocolo RARP para solicitar una dirección IP del servidor de red accesible mediante la interfaz que tiene una dirección IP establecida en cero.

### <a name="rarp-enable"></a>Habilitación de RARP

Para usar RARP, la aplicación debe crear la instancia de IP con una dirección IP establecida en cero y, a continuación, habilitar RARP con el servicio ***nx_rarp_enable***. En el caso de los sistemas de host múltiple, al menos un dispositivo de red asociado a la instancia de IP debe tener una dirección IP establecida en cero. El procesamiento de RARP envía periódicamente mensajes de solicitud RARP al sistema de NetX Duo en el que requiere una dirección IP hasta que se recibe una respuesta de RARP válida con la dirección IP designada por la red. En este momento, se ha completado el procesamiento de RARP.

Una vez habilitado RARP, se deshabilitará automáticamente una vez que se resuelvan todas las direcciones de las interfaces. La aplicación puede forzar la finalización de RARP con el servicio ***nx_rarp_disable***.

### <a name="rarp-request"></a>Solicitud RARP

El formato de un paquete de solicitud RARP es casi idéntico al paquete ARP que se muestra en la [figura 6](#arp-messages). La única diferencia es que el campo de tipo de marco es 0x8035 y el valor del campo *Código de la operación* es 3, lo que designa una solicitud RARP. Como se ha mencionado anteriormente, las solicitudes RARP se enviarán periódicamente (cada ***NX_RARP_UPDATE_RATE*** segundos) hasta que se reciba una respuesta de RARP con la dirección IP asignada por la red.

> [!NOTE]
> *Se espera que todos los mensajes de RARP de la implementación de TCP/IP estén en formato **big endian**. En este formato, el byte más significativo de la palabra reside en la dirección de bytes más baja.*

### <a name="rarp-reply"></a>Respuesta de RARP

Los mensajes de respuesta de RARP se reciben desde la red y contienen la dirección IP asignada por la red para este host. El formato de un paquete de respuesta de RARP es casi idéntico al paquete ARP que se muestra en la figura 6. La única diferencia es que el campo de tipo de marco es 0x8035 y el campo del *código de operación* es 4, lo que designa una respuesta de RARP. Después de la recepción, se configura la dirección IP en la instancia de IP, se deshabilita la solicitud RARP periódica y la instancia de IP ahora está lista para la operación de red normal.

En el caso de hosts múltiples, la dirección IP se aplica a la interfaz de red que lo solicita. Si hay otras interfaces de red que aún solicitan una asignación de dirección IP, el servicio RARP periódico continúa hasta que se resuelven todas las solicitudes de direcciones IP de las interfaces.

> [!NOTE]
> *La aplicación no debe utilizar la instancia de IP hasta que se complete el procesamiento de RARP. Las aplicaciones pueden usar **nx_ip_status_check** para esperar la finalización de RARP. En el caso de sistemas de host múltiple, la aplicación no debe usar la interfaz de la solicitud hasta que se complete el procesamiento de RARP en esa interfaz. El estado de la dirección IP del dispositivo secundario se puede comprobar con el servicio **nx_ip_interface_status_check**.*

### <a name="rarp-statistics-and-errors"></a>Estadísticas y errores de RARP

Si se habilita, el software de RARP de NetX Duo realiza un seguimiento de varios errores y estadísticas que pueden ser útiles para la aplicación. Se mantienen las estadísticas y los informes de errores siguientes para cada procesamiento de RARP de IP:

- Número total de solicitudes RARP enviadas
- Número total de respuestas de RARP recibidas
- Número total de mensajes no válidos de RARP

Todas estas estadísticas e informes de errores están disponibles para la aplicación con el servicio ***nx_rarp_info_get***.

## <a name="internet-control-message-protocol-icmp"></a>Protocolo de mensajes de control de Internet (ICMP)

El protocolo de mensajes de control de Internet (ICMP) para IPv4 se limita a pasar información de errores y de control entre los miembros de la red IP. El protocolo de mensajes de control de Internet para IPv6 (ICMPv6) también controla la información de errores y de control, y es necesario para los protocolos de resolución de direcciones, como la detección de direcciones duplicadas (DAD) y la configuración automática de direcciones sin estado.

Como la mayoría de los mensajes de la capa de aplicación (por ejemplo, TCP/IP), los mensajes de ICMP e ICMPv6 se encapsulan con un encabezado IP con la designación del protocolo ICMP (o ICMPv6).

### <a name="icmp-statistics-and-errors"></a>Estadísticas y errores de ICMP

Si se habilita, NetX Duo realiza un seguimiento de varios errores y estadísticas de ICMP que pueden ser útiles para la aplicación. Se mantienen las estadísticas y los informes de errores siguientes para cada procesamiento de ICMP de IP: 

- Número total de pings de ICMP enviados  
- Número total de tiempos de expiración de pings de ICMP 
- Número total de subprocesos de ping de ICMP suspendidos 
- Número total de respuestas de ping de ICMP recibidas 
- Número total de errores de suma de comprobación de ICMP 
- Número total de mensajes de ICMP no controlados 

Todos estos informes de errores y estadísticas están disponibles para la aplicación con el servicio ***nx_icmp_info_get***.

## <a name="icmpv4-services-in-netx-duo"></a>Servicios ICMPv4 en NetX Duo

### <a name="icmpv4-enable"></a>Habilitación de ICMPv4

Para que NetX Duo pueda procesar los mensajes de ICMPv4, la aplicación debe llamar al servicio ***nx_icmp_enable*** para habilitar el procesamiento de ICMPv4. Una vez hecho esto, la aplicación puede emitir solicitudes de ping y paquetes de ping entrantes de campo.  

### <a name="icmpv4-echo-request"></a>Solicitud de eco de ICMPv4

Una solicitud de eco es un tipo de mensaje de ICMPv4 que se suele usar para comprobar la existencia de un nodo específico en la red, como se identifica por su dirección IP del host. El popular comando ping se implementa mediante mensajes de solicitud y respuesta de eco de ICMP. Si el host específico está presente, su pila de red procesa la solicitud de ping y responde con una respuesta de ping. En la figura 7 se detalla el formato del mensaje de ping de ICMPv4.

![Mensaje de ping de ICMPv4](./media/user-guide/icmpv4-ping-message.png)  

**FIGURA 7. Mensaje de ping de ICMPv4**

> [!NOTE]
> *Se espera que todos los mensajes ICMPv4 de la implementación de TCP/IP estén en formato **big endian**. En este formato, el byte más significativo de la palabra reside en la dirección de bytes más baja.*

A continuación se describe el formato de encabezado de ICMPv4:

|Campo del encabezado |Propósito |
|---|---|
|**Tipo** |Este campo especifica el mensaje de ICMPv4 (bits del 31 al 24). Los más comunes son:<br />- 0: respuesta de eco<br />- 3: destino no accesible<br />- 8: solicitud de eco<br />- 11: tiempo superado<br />- 12: problema de parámetro |
|**Código** |Este campo es específico del contexto del campo de tipo (bits del 23 al 16). En el caso de una solicitud o respuesta de eco, el código se establece en cero.|
|**Checksum** |Este campo contiene la suma de comprobación de 16 bits de la suma del complemento a uno del mensaje de ICMPv4, incluido el encabezado ICMPv4 completo a partir del campo de tipo. Antes de generar la suma de comprobación, se borra el campo de la suma de comprobación.|
|**Identificación** | Este campo contiene un valor de identificador que identifica al host; un host debe utilizar el identificador extraído de una solicitud de eco en la respuesta de eco (bits del 31 al 16).|
|**Número de secuencia** |Este campo contiene un valor de identificador; un host debe utilizar el identificador extraído de una solicitud de eco en la respuesta de eco (bits del 31 al 16). A diferencia del campo de identificador, este valor cambiará en una solicitud de eco subsiguiente del mismo host (bits del 15 al 0).|

### <a name="icmpv4-echo-response"></a>Respuesta de eco de ICMPv4    
Una respuesta de ping es otro tipo de mensaje de ICMP que el componente de ICMP genera internamente en respuesta a una solicitud de ping externa. Además de la confirmación, la respuesta de ping también contiene una copia de los datos de usuario proporcionados en la solicitud de ping.

### <a name="icmpv4-error-messages"></a>Mensajes de error de ICMPv4   
Se admiten los siguientes mensajes de error de ICMPv4 en NetX Duo: 
- Destino no accesible 
- Tiempo superado 
- Problema de parámetro

## <a name="internet-group-management-protocol-igmp"></a>Protocolo de administración de grupos de Internet (IGMP)

El protocolo de administración de grupos de Internet (IGMP) proporciona un dispositivo para comunicarse con sus equipos cercanos y sus enrutadores que pretenden recibir, o unirse, a un grupo de multidifusión IPv4 (RFC 1112 y RFC 2236). Un grupo de multidifusión es básicamente una colección dinámica de miembros de la red y se representa mediante una dirección IP de clase D. Los miembros del grupo de multidifusión pueden salir en cualquier momento y los nuevos miembros pueden unirse en cualquier momento. La coordinación implicada en la unión y la salida del grupo es responsabilidad de IGMP.

> [!NOTE]
> *IGMP está diseñado únicamente para grupos de multidifusión IPv4. No se puede usar en la red IPv6.*

### <a name="igmp-enable"></a>Habilitación de IGMP     
Para que se pueda llevar a cabo cualquier actividad de multidifusión en NetX Duo, la aplicación debe llamar al servicio ***nx_igmp_enable***. Este servicio realiza la inicialización básica de IGMP como preparación para las solicitudes de multidifusión.

### <a name="multicast-ipv4-addressing"></a>Direccionamiento IPv4 de multidifusión  
Como se ha mencionado anteriormente, las direcciones de multidifusión son realmente direcciones IP de clase D, tal como se muestra en la [figura 4](#ipv4-addresses). Los 28 bits inferiores de la dirección de clase D se corresponden con el identificador del grupo de multidifusión. Hay una serie de direcciones de multidifusión predefinidas; sin embargo, la *dirección de todos los hosts* (244.0.0.1) es especialmente importante para el procesamiento de IGMP. Los enrutadores usan la *dirección de todos los hosts* para consultar a todos los miembros de multidifusión sobre los grupos de multidifusión a los que pertenecen.  

### <a name="physical-address-mapping-in-ipv4"></a>Asignación de dirección física en IPv4
Las direcciones de multidifusión de clase D se asignan directamente a direcciones Ethernet físicas que van de la 01.00.5e.00.00.00 a la 01.00.5e.7f.ff.ff. Los 23 bits inferiores de la dirección de multidifusión IP se asignan directamente a los 23 bits inferiores de la dirección Ethernet.

### <a name="multicast-group-join"></a>Unión a un grupo de multidifusión
Las aplicaciones que necesiten unirse a un grupo de multidifusión determinado pueden hacerlo mediante una llamada al servicio ***nx_igmp_multicast_join***. Este servicio realiza un seguimiento del número de solicitudes para unirse a este grupo de multidifusión. Si esta es la primera solicitud de la aplicación para unirse al grupo de multidifusión, se envía un informe de IGMP a la red principal que indica la intención de este host de unirse al grupo. A continuación, se llama al controlador de red para realizar escuchas de paquetes con la dirección Ethernet de este grupo de multidifusión.

En un sistema de host múltiple, si el grupo de multidifusión es accesible mediante una interfaz específica, la aplicación debe usar el servicio ***nx_igmp_multicast_interface_join** _ en lugar de _*_nx_igmp_multicast_join_**, que está limitado a los grupos de multidifusión de la red principal.

### <a name="multicast-group-leave"></a>Salida de un grupo de multidifusión   
Las aplicaciones que necesiten salir de un grupo de multidifusión al que se han unido anteriormente pueden hacerlo llamando al servicio ***nx_igmp_multicast_leave***. Este servicio reduce el recuento interno asociado con el número de veces que se han realizado uniones al grupo. Si no hay ninguna solicitud de unión pendiente para un grupo, se llama al controlador de red para deshabilitar la escucha de paquetes con la dirección Ethernet de este grupo de multidifusión.

### <a name="multicast-loopback"></a>Bucle invertido de multidifusión    
Es posible que una aplicación desee recibir tráfico de multidifusión originado en uno de los orígenes del mismo nodo. Esto requiere que el componente de multidifusión de IP tenga habilitado el bucle invertido mediante el servicio ***nx_igmp_loopback_enable***.

### <a name="igmp-report-message"></a>Mensaje de informe de IGMP      
Cuando la aplicación se une a un grupo de multidifusión, se envía un mensaje de informe de IGMP mediante la red para indicar la intención del host de unirse a un grupo de multidifusión determinado. En la figura 8 se muestra el formato del mensaje de informe de IGMP. La dirección del grupo de multidifusión se usa para el mensaje de grupo en el mensaje de informe de IGMP y para la dirección IP de destino.

En la figura 8 siguiente, el encabezado IGMP contiene un campo de versión/tipo, respuesta máxima

![Diagrama de un mensaje de informe de IGMP.](./media/user-guide/image17.jpg)

**FIGURA 8. Mensaje de informe de IGMP**

Un campo de tiempo, uno de suma de comprobación y otro de dirección de grupo de multidifusión. En el caso de los mensajes de IGMPv1, el campo de tiempo de respuesta máximo siempre se establece en cero, ya que no forma parte del protocolo IGMPv1. El campo de tiempo de respuesta máximo se establece cuando el host recibe un mensaje de IGMP de tipo consulta y se borra cuando un host recibe el mensaje de tipo informe de otro host, tal como se define en el protocolo IGMPv2.

A continuación se describe el formato de encabezado IGMP:

|Campo del encabezado|Propósito|
|---|---|
|**Versión** |Este campo especifica la versión de IGMP (bits del 31 al 28).|
|**Tipo** |Este campo especifica el tipo de mensaje de IGMP (bits del 27 al 24).|
|**Tiempo de respuesta máximo** |No se utiliza en IGMP v1. En IGMP v2, este campo actúa como el tiempo de respuesta máximo.|
|**Checksum** |Este campo contiene la suma de comprobación de 16 bits de la suma del complemento a uno del mensaje de IGMP a partir de la versión de IGMP (bits del 0 al 15).|
|**Dirección del grupo** |Dirección IP del grupo de clase D de 32 bits|

Los mensajes de informe de IGMP también se envían en respuesta a los mensajes de consulta de IGMP enviados por un enrutador de multidifusión. Los enrutadores de multidifusión envían periódicamente mensajes de consulta para ver qué hosts siguen requiriendo pertenencia a grupos. Los mensajes de consulta tienen el mismo formato que el mensaje de informe de IGMP que se muestra en la figura 8. Las únicas diferencias son que el tipo de IGMP es igual a 1 y que el campo de dirección del grupo se establece en 0. El enrutador de multidifusión envía los mensajes de consulta de IGMP a la dirección IP de *todos los hosts*. Un host que aún desea mantener la pertenencia a grupos responde mediante el envío de otro mensaje de informe de IGMP.

> [!NOTE]
> *Se espera que todos los mensajes de la implementación de TCP/IP estén en formato **big endian**. En este formato, el byte más significativo de la palabra reside en la dirección de bytes más baja.*

### <a name="igmp-statistics-and-errors"></a>Estadísticas y errores de IGMP    
<th><p>Si se habilita, el software de IGMP de NetX Duo realiza un seguimiento de varios errores y estadísticas que pueden ser útiles para la aplicación. Se mantienen las estadísticas y los informes de errores siguientes para cada procesamiento de IGMP de IP: 

- Número total de informes de IGMP enviados 
- Número total de consultas de IGMP recibidas 
- Número total de errores de suma de comprobación de IGMP 
- Número total de grupos unidos actualmente a IGMP 

Todos estos informes de errores y estadísticas están disponibles para la aplicación con el servicio ***nx_igmp_info_get***. 

### <a name="multicast-without-igmp"></a>Multidifusión sin IGMP  
La aplicación que espera el tráfico de multidifusión IPv4 puede unirse a una dirección de grupo de multidifusión sin invocar mensajes de IGMP mediante el servicio ***nx_ipv4_multicast_interface_join***. Este servicio indica a la capa IPv4 y al controlador de interfaz subyacente que acepte paquetes de la dirección IPv4 de multidifusión designada. Sin embargo, no se está enviando o procesando mensajes de administración de grupo de IGMP para este grupo.

La aplicación que ya no quiere recibir tráfico del grupo puede usar el servicio ***nx_ipv4_multicast_interface_leave.***

## <a name="ipv6-in-netx-duo"></a>IPv6 en NetX Duo

### <a name="ipv6-addresses"></a>Direcciones IPv6   
Las direcciones IPv6 son de 128 bits. La arquitectura de la dirección IPv6 se describe en RFC 4291. La dirección se divide en un prefijo que contiene los bits más significativos y una dirección de host que contiene los bits inferiores. El prefijo indica el tipo de dirección y equivale aproximadamente a la dirección de red de la red IPv4.

IPv6 tiene tres tipos de especificaciones de direcciones: unidifusión, difusión por proximidad (no se admite en NetX Duo) y multidifusión. Las direcciones de unidifusión son aquellas direcciones IP que identifican un host específico en Internet. Las direcciones de unidifusión pueden ser una dirección IP de origen o de destino. Las direcciones de multidifusión especifican un grupo dinámico de hosts en Internet. Los miembros del grupo de multidifusión pueden unirse y salir siempre que lo deseen.

IPv6 no tiene el equivalente del mecanismo de difusión de IPv4. La capacidad de enviar un paquete a todos los hosts se puede lograr mediante el envío de un paquete al grupo de multidifusión local de vínculo de todos los hosts.

IPv6 emplea direcciones de multidifusión para realizar los procedimientos de detección de equipos cercanos, detección de enrutadores y configuración automática de direcciones sin estado.

Hay dos tipos de direcciones IPv6 de unidifusión: las direcciones locales de vínculo, que normalmente se crean mediante la combinación del prefijo local de vínculo conocido con la dirección MAC de la interfaz, y las direcciones IP globales, que también tienen la parte del prefijo y la parte del identificador de host. Una dirección global puede configurarse manualmente o a través de la configuración automática de direcciones sin estado o DHCPv6. NetX Duo admite la dirección local de vínculo y la dirección global.

Para dar cabida a los formatos IPv4 e IPv6, NetX Duo proporciona un nuevo tipo de datos, NXD_ADDRESS, para almacenar direcciones IPv4 e IPv6. A continuación se muestra la definición de esta estructura. El campo de dirección es una unión de direcciones IPv4 e IPv6.

```c
typedef struct NXD_ADDRESS_STRUCT
{
    ULONG nxd_ip_version;
    union
    {
        ULONG v4;
        ULONG v6[4];
    } nxd_ip_address;
} NXD_ADDRESS;
```

En la estructura de NXD_ADDRESS, el primer elemento, *nxd_ip_version*, indica la versión IPv4 o IPv6. Los valores admitidos son NX_IP_VERSION_V4 o NX_IP_VERSION_V6. *nxd_ip_version* indica el campo de la unión de *nxd_ip_address* que se usará como dirección IP. Los servicios de API de NetX Duo suelen tomar un puntero a la estructura NXD_ADDRESS como argumento de entrada en lugar de la dirección IP de ULONG (32 bits).

### <a name="link-local-addresses"></a>Direcciones locales de vínculo     
Una dirección local de vínculo solo es válida en la red local. Un dispositivo puede enviar y recibir paquetes a otro dispositivo en la misma red después de que se le asigne una dirección local de vínculo válida. Una aplicación asigna una dirección local de vínculo mediante una llamada al servicio ***nxd_ipv6_address_set*** de NetX Duo, con el parámetro de longitud de prefijo establecido en 10. La aplicación puede proporcionar una dirección local de vínculo al servicio o simplemente usar NX_NULL como dirección local de vínculo y permitir que NetX Duo cree una dirección local de vínculo basada en la dirección MAC del dispositivo.

En el ejemplo siguiente se indica a NetX Duo que configure la dirección local de vínculo con una longitud de prefijo de 10 en el dispositivo principal (índice 0) mediante su dirección MAC:

```c
nxd_ipv6_address_set(ip_ptr, 0, NX_NULL, 10, NX_NULL);
```
En el ejemplo anterior, si la dirección MAC de la interfaz es 54:32:10:1A:BC:67, la dirección local de vínculo correspondiente sería:

```c
FE80::5632:10FF:FE1A:BC67
```
Tenga en cuenta que la parte del identificador de host de la dirección IPv6 (**5632:10FF:FE1A:BC67**) se compone de la dirección Mac de 6 bytes, con las siguientes modificaciones:

- **0xFFFE** insertado entre el byte 3 y el byte 4 de la dirección MAC.
- El segundo bit más bajo del primer byte de la dirección MAC (bit U/L) se establece en 1.

Consulte RFC 2464 (transmisión de paquetes IPv6 a través de la red Ethernet) para obtener más información sobre cómo crear la parte del host de una dirección IPv6 a partir de la dirección MAC de la interfaz.

Hay algunas direcciones de multidifusión especiales para enviar mensajes de multidifusión a uno o varios hosts en IPv6:

| Grupo  | Dirección   | Descripción  |
|---|---|---|
|Grupo de todos los nodos |**FF02::1** |Todos los hosts de la red local|
|Grupo de todos los enrutadores |**FF02::2** |Todos los enrutadores de la red local|
|Nodo solicitado |**FF02::1:FF00:0/104** |Se explica a continuación|

Una dirección de multidifusión de nodo solicitado se dirige a hosts específicos en el vínculo local en lugar de a todos los hosts IPv6. Consta del prefijo **FF02::1:FF00:0/104**, que tiene 104 bits y los últimos 24 bits de la dirección IPv6 de destino. Por ejemplo, una dirección IPv6 **205B:209D:D028::F058:D1C8:1024** tiene una dirección de multidifusión de nodo solicitado **FF02::1:FFC8:1024**.

> [!IMPORTANT]
> *La notación de dos puntos dobles indica que los bits intermedios son ceros. **FF02::1:FF00:0/104** totalmente expandido sería* **FF02:0000:0000:0000:0000:0001:FF00:0000**.

### <a name="global-addresses"></a>Direcciones globales    
Un ejemplo de una dirección global IPv6 es **2001:0123:4567:89AB:CDEF::1**. NetX Duo almacena direcciones IPv6 en la estructura NXD_ADDRESS. En el ejemplo siguiente, la variable de NXD_ADDRESS **global_ipv6_address** contiene una dirección IPv6 de unidifusión. En el ejemplo siguiente se muestra un dispositivo NetX Duo que crea una dirección IPv6 global específica para su dispositivo primario:

```c
NXD_ADDRESS global_ipv6_address;
UINT        primary_interface_index = 0;

global_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
global_ipv6_address.nxd_ip_address.v6[0] = 0x20010123;
global_ipv6_address.nxd_ip_address.v6[1] = 0x456789AB;
global_ipv6_address.nxd_ip_address.v6[2] = 0xCDEF0000;
global_ipv6_address.nxd_ip_address.v6[3] = 0x00000001;

status = nxd_ipv6_address_set(
            &ip_0,
            primary_interface_index,
            &global_ipv6_address,
            64,
            NX_NULL);
```
Tenga en cuenta que el prefijo de esta dirección IPv6 es **2001:0123:4567:89AB**, que tiene 64 bits de longitud y es una longitud de prefijo común para las direcciones IPv6 de unidifusión globales en Ethernet.

La estructura de NXD_ADDRESS también contiene direcciones IPv4. Una dirección IP de **192.1.168.10** (**0xC001A80A**) almacenada en global_ipv4_address tendría el siguiente diseño de memoria:

|Campo |Value |
|---|---|
|global_ipv4_address.nxd_ip_version |NX_IP_VERSION_V4|
|global_ipv4_address.nxd_ip_address.v4 |0xC001A80A|

Cuando una aplicación pasa una dirección a los servicios de NetX Duo, el campo *nxd_ip_version* debe especificar la versión de IP correcta para el control de paquetes adecuado.

Para ser compatible con versiones anteriores de las aplicaciones de NetX existentes, NetX Duo admite todos los servicios de NetX. Internamente, NetX Duo convierte el tipo de dirección IPv4 ULONG en un tipo de datos NXD_ADDRESS antes de reenviarlo al servicio de NetX Duo real.

En el ejemplo siguiente se muestran la similitud y las diferencias entre los servicios de NetX y NetX Duo.

```c
/* Make a connection to the destination IPv4 address
   192.1.168.12 through an already created TCP socket bound
   to the well known HTTP port number 80. */

global_ipv4_address.nxd_ip_version = NX_IP_VERSION_V4;
global_ipv4_address.nxd_ip_address.v4 = 0xC001A80C;

nxd_tcp_client_socket_connect(&tcp_socket,
                              &global_ipv4_address,
                              port_number,
                              NX_WAIT_FOREVER);
```

A continuación se muestra la API de NetX equivalente:

```c
ULONG         server_ip = 0xC001A80C;
NX_TCP_SOCKET tcp_socket;
UINT          port_number = 80;

nx_tcp_client_socket_connect(&tcp_socket,
                             server_ip,
                             port_number,
                             NX_WAIT_FOREVER); 
```

> [!IMPORTANT]
> *Se recomienda a los desarrolladores de aplicaciones que usen la versión nxd de estas API*.

### <a name="ipv6-default-routers"></a>Enrutadores IPv6 predeterminados    
IPv6 usa un enrutador predeterminado para reenviar paquetes a destinos fuera del enlace. El servicio ***nxd_ipv6_default_router_add*** de NetX Duo permite que una aplicación agregue un enrutador IPv6 a la tabla de enrutadores predeterminados. Consulte el capítulo 4 "Descripción de los servicios" para conocer los demás servicios de enrutador predeterminados que ofrece NetX Duo.  

Al reenviar paquetes IPv6, NetX Duo comprueba primero si el destino del paquete está en el vínculo. Si no es así, NetX Duo busca en la tabla de enrutamiento predeterminada un enrutador válido al que reenviar el paquete fuera de vínculo.  

Para quitar un enrutador de la tabla de enrutadores predeterminados IPv6, la aplicación debe usar el servicio ***nxd_ipv6_default_router_delete** _. Para obtener las entradas de la tabla de enrutadores predeterminados IPv6, use el servicio _*_nxd_ipv6_default_router_entry_get_**.

### <a name="ipv6-header"></a>Encabezado IPv6    
El encabezado IPv6 se ha modificado a partir del encabezado IPv4. Al asignar un paquete, el autor de la llamada especifica el protocolo de la aplicación (por ejemplo, UDP, TCP), el tamaño del búfer en bytes y el límite de saltos.   

En la ilustración 9 se muestra el formato del encabezado IPv6 y en la tabla se enumeran los componentes de encabezado.

![Diagrama del formato de encabezado IPv6.](./media/user-guide/image18.png)

**FIGURA 9. Formato del encabezado IPv6**

|Encabezado IP | Propósito |
|---|---|
|Versión |Campo de 4 bits para la versión de IP. En el caso de las redes IPv6, el valor de este campo debe ser 6; en el caso de las redes IPv4, debe ser 4.|
|Clase de tráfico |Campo de 8 bits que almacena la información de la clase de tráfico. NetX Duo no usa este campo.|
|Etiqueta de flujo |Campo de 20 bits para identificar de forma única el flujo, si existe, al que está asociado un paquete. Un valor de cero indica que el paquete no pertenece a ningún flujo concreto. Este campo reemplaza el campo *TOS* de IPv4.|
|Longitud de carga útil |Campo de 16 bits que indica la cantidad de datos en bytes del paquete IPv6 después del encabezado base de IPv6. Incluye todos los datos y el encabezado del protocolo encapsulado.|
|Encabezado siguiente | Campo de 8 bits que indica el tipo del encabezado de extensión después del encabezado base de IPv6. Este campo reemplaza el campo *Protocolo* de IPv4.|
|Límite de saltos |Campo de 8 bits que limita el número de enrutadores que puede pasar el paquete. Este campo reemplaza el campo *TTL* de IPv4.|
|Dirección de origen |Campo de 128 bits que almacena la dirección IPv6 del remitente.|
|Dirección de destino |Campo de 128 bits que almacena la dirección IPv6 del destino.|

### <a name="enabling-ipv6-in-netx-duo"></a>Habilitación de IPv6 en NetX Duo    
IPv6 está habilitado de forma predeterminada en NetX Duo. Los servicios IPv6 están habilitados en NetX Duo si la opción configurable ***NX_DISABLE_IPV6** _ de _nx_user.h* no está definida. Si ***NX_DISABLE_IPV6*** está definido, NetX Duo solo ofrecerá servicios IPv4, y ninguno de los módulos y servicios relacionados con IPv6 no estarán integrados en la biblioteca de NetX Duo.

El siguiente servicio se proporciona para que las aplicaciones configuren la dirección IPv6 del dispositivo: ***nxd_ipv6_address_set***.

Además de establecer manualmente las direcciones IPv6 del dispositivo, el sistema también puede usar la configuración automática de direcciones sin estado. Para usar esta opción, la aplicación debe llamar a ***nxd_ipv6_enable** _ para iniciar los servicios IPv6 en el dispositivo. Además, los servicios ICMPv6 deben iniciarse mediante una llamada a _*_nxd_icmp_enable_*_, que permite que NetX Duo realice servicios como la solicitud de enrutador, la detección de equipos cercanos y la detección de direcciones duplicadas. Tenga en cuenta que _*_nx_icmp_enable_*_ solo inicia ICMP para servicios IPv4. _*_nxd_icmp_enable_*_ inicia servicios ICMP para IPv4 e IPv6. Si el sistema no necesita los servicios ICMPv6, se puede usar _ *_nx_icmp_enable_** para que el módulo ICMPv6 no esté vinculado al sistema.

En el ejemplo siguiente se muestra un procedimiento de inicialización de IPv6 típico de NetX Duo.

```c
/* Assume ip_0 has been created and IPv4 services (such as ARP,
   ICMP, have been enabled. */
#define SECONDARY_INTERFACE 1

/* Enable IPv6 */
status = nxd_ipv6_enable(&ip_0);

if(status != NX_SUCCESS)
{
    /* nxd_ipv6_enable failed. */
}

/* Enable ICMPv6 */
status = nxd_icmp_enable(&ip_0);
if(status != NX_SUCCESS)
{
    /* nxd_icmp_enable failed. */
}

/* Configure the link local address on the primary interface. */
status = nxd_ipv6_address_set(&ip_0, 0, NX_NULL, 10, NX_NULL);

/* Configure ip_0 primary interface global address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6
ip_address.nxd_ip_address.v6[0] = 0x20010db8;
ip_address.nxd_ip_address.v6[1] = 0x0000f101;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 0x202;

/* Configure global address of the primary interface. */
status = nxd_ipv6_address_set(&ip_0, SECONDARY_INTERFACE,
                              &ip_address, 64, NX_NULL);
```                              

Los protocolos de nivel superior (como TCP y UDP) pueden habilitarse antes o después de que se inicie IPv6.

> [!IMPORTANT]  
> *Los servicios de IPv6 solo están disponibles después de inicializar el subproceso de IP y de habilitar el dispositivo.*

Una vez que la interfaz está habilitada (es decir, el controlador de dispositivo de la interfaz está listo para enviar y recibir datos, y se ha obtenido una dirección local de vínculo válida), el dispositivo puede obtener direcciones IPv6 globales mediante uno de estos métodos:

- Configuración automática de direcciones sin estado.  
- Configuración manual de direcciones IPv6.  
- Configuración de direcciones a través de DHCPv6 (con un paquete DHCPv6 opcional)

Los dos primeros métodos se describen a continuación. El tercer método (DHCPv6) se describe en el paquete DHCP.

### <a name="stateless-address-autoconfiguration-using-router-solicitation"></a>Configuración automática de direcciones sin estado mediante la solicitud de enrutador      
Los dispositivos NetX Duo pueden configurar sus interfaces automáticamente cuando se conectan a una red IPv6 con un enrutador que proporciona información de prefijo. Los dispositivos que requieren la configuración automática de direcciones sin estado envían mensajes de solicitud de enrutador (RS). Los enrutadores de la red responden con mensajes de anuncios de enrutador solicitados (RA). Los mensajes de RA anuncian prefijos que identifican las direcciones de red asociadas a un vínculo. A continuación, los dispositivos generan un identificador único para la red a la que está conectado el dispositivo. La dirección se forma combinando el prefijo y su identificador único. De esta manera, al recibir los mensajes de RA, los hosts generan su dirección IP. Los enrutadores también pueden enviar mensajes de RA no solicitados periódicos. 

> [!WARNING]
> *NetX Duo permite a una aplicación habilitar o deshabilitar la configuración automática de direcciones sin estado en tiempo de ejecución. Para habilitar esta característica, la biblioteca de NetX Duo se debe compilar con **NX_IPV6_STATELESS_AUTOCONFIG_CONTROL** definido. Una vez habilitada esta característica, las aplicaciones pueden usar **nxd_ipv6_stateless_address_autoconfigure_enable** y **nxd_ipv6_stateless_address_autocofigure_disable** para habilitar o deshabilitar la configuración automática de direcciones IPv6 sin estado*.

### <a name="manual-ipv6-address-configuration"></a>Configuración manual de la dirección IPv6     
Si se necesita una dirección IPv6 específica, la aplicación puede usar ***nxd_ipv6_address_set*** para configurar manualmente una dirección IPv6. Una interfaz de red puede tener varias direcciones IPv6. Sin embargo, tenga en cuenta que el número total de direcciones IPv6 de un sistema, ya sea obtenido a través de la configuración automática de direcciones sin estado o a través de la configuración manual, no puede superar el valor de ***NX_MAX_IPV6_ADDRESSES***.

En el ejemplo siguiente se muestra cómo configurar manualmente una dirección global en la interfaz principal (dispositivo 0) en ip_0:

```c
NXD_ADDRESS global_address;
global_address.nxd_ip_version = NX_IP_VERSION_V6;
global_address.nxd_ip_address.v6[0] = 0x20010000;
global_address.nxd_ip_address.v6[1] = 0x00000000;
global_address.nxd_ip_address.v6[2] = 0x00000000;
global_address.nxd_ip_address.v6[3] = 0x0000ABCD;
```

A continuación, el host llama al siguiente servicio de NetX Duo para asignar esta dirección como su dirección IP global:

```c
status = nxd_ipv6_address_set(&ip_0, 0,  
                              &global_address, 64
                              NX_NULL);
```

### <a name="duplicate-address-detection-dad"></a>Detección de direcciones duplicadas (DAD)    
Cuando un sistema configura su dirección IPv6, la dirección se marca como provisional (*TENTATIVE*). Si la detección de direcciones duplicadas (DAD), que se describe en RFC 4862, está habilitada, NetX Duo envía automáticamente mensajes de solicitud de equipos cercanos (NS) con esta dirección provisional como destino. Si ningún host de la red responde a estos mensajes de NS dentro de un período de tiempo determinado, se supone que la dirección es única en el vínculo local y su estado pasa al estado VALID. Llegados a este punto, la aplicación puede empezar a usar esta dirección IP para la comunicación.  

La funcionalidad DAD forma parte del módulo ICMPv6. Por lo tanto, la aplicación debe habilitar los servicios ICMPv6 para que una dirección configurada recientemente pueda someterse al proceso DAD. Como alternativa, para desactivar el proceso DAD se puede definir la opción ***NX_DISABLE_IPV6_DAD** _ en el entorno de compilación de la biblioteca de NetX Duo (definido como _*_nx_user.h_*_). Durante el proceso DAD, el parámetro _*_NX_IPV6_DAD_TRANSMITS_*_ determina el número de mensajes de NS que envía NetX Duo sin recibir una respuesta para determinar que la dirección es única. De forma predeterminada y de acuerdo con la recomendación de RFC 4862, _ *_NX_IPV6_DAD_TRANSMITS_** se establece en 3. Si se establece este símbolo en cero, DAD se deshabilita de forma efectiva.

Si ICMPv6 o DAD no están habilitados en el momento en que la aplicación asigna una dirección IPv6, no se realiza el proceso DAD y NetX Duo establece el estado de la dirección IPv6 en VALID inmediatamente.

NetX Duo no puede comunicarse en la red IPv6 hasta que la dirección global o local de vínculo es válida. Después de obtener una dirección válida, NetX Duo intenta hacer coincidir la dirección de destino de un paquete entrante con una de sus direcciones IPv6 configuradas o con una dirección de multidifusión habilitada. Si no se encuentra ninguna coincidencia, se quita el paquete. 

> [!WARNING]  
> *Durante el proceso DAD, el número de paquetes NS de DAD que se van a transmitir se define mediante ***NX_IPV6_DAD_TRANSMITS** _, cuyo valor predeterminado es 3 y, de forma predeterminada, se envía un retraso de un segundo entre cada mensaje de NS de DAD. Por lo tanto, en un sistema con DAD habilitado, después de que se asigne una dirección IPv6 (y suponiendo que no sea una dirección duplicada), hay aproximadamente 3 segundos de retraso antes de que la dirección IP esté en estado VALID y lista para la comunicación._

Es posible que las aplicaciones deseen recibir notificaciones cuando se cambien las direcciones IPv6 en el sistema. Para habilitar la característica de notificación de cambio de dirección IPv6, la biblioteca de NetX Duo debe compilarse con el símbolo **NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** definido. Una vez habilitada la característica, las aplicaciones pueden instalar la función de devolución de llamada mediante el servicio **_nxd_ipv6_address_change_notify_**.

Cuando una dirección IPv6 se cambia o deja de ser válida, se invoca la función de devolución de llamada proporcionada por el usuario con la siguiente información:

| Función  | Descripción  |
|---|---|
|ip_ptr |Puntero a la instancia de IP.|
|interface_index |Índice de la interfaz de red a la que está asociada esta dirección IPv6.
|ipv6_addr_index |Índice para la tabla de direcciones IPv6.|
|ipv6_address |Puntero a la dirección IPv6, en forma de matriz de cuatro enteros de tipo ULONG. Las direcciones Pv6 se presentan en el orden de bytes del host.|

### <a name="ipv6-multicast-support-in-netx-duo"></a>Compatibilidad con multidifusión IPv6 en NetX Duo      
Las direcciones de multidifusión especifican un grupo dinámico de hosts en Internet. Los miembros del grupo de multidifusión pueden unirse y salir siempre que lo deseen. NetX Duo implementa varios protocolos ICMPv6, como la detección de direcciones duplicadas, la detección de equipos cercanos y la detección de enrutadores, que requieren la capacidad de multidifusión IP. Por lo tanto, NetX Duo espera que el controlador de dispositivo subyacente admita las operaciones de multidifusión.

Cuando NetX Duo necesita unirse o abandonar un grupo de multidifusión (por ejemplo, la dirección de multidifusión de todos los nodos y la dirección de multidifusión de *nodo solicitado*), emite un comando de controlador al controlador de dispositivo para unirse a una dirección MAC de multidifusión o abandonarla. El comando de controlador para unirse a la dirección de multidifusión es ***NX_LINK_MULTICAST_JOIN** _. Para abandonar una dirección de multidifusión, NetX Duo emite el comando de controlador _*_NX_LINK_MULTICAST_LEAVE_**. El controlador de dispositivo debe implementar estos dos comandos para que los protocolos ICMPv6 funcionen correctamente.

Las aplicaciones pueden unirse a un grupo de multidifusión IPv6 mediante el servicio ***nxd_ipv6_multicast_interface_join*.** Este servicio registra la dirección de multidifusión con la pila IP y, a continuación, notifica al controlador de dispositivo especificado la dirección de multidifusión IPv6. Para dejar un grupo de multidifusión, las aplicaciones usan el servicio ***nxd_ipv6_multicast_interface_leave.***

### <a name="neighbor-discovery-nd"></a>Detección de equipos cercanos (ND)    
La detección de equipos cercanos es un protocolo de redes IPv6 para asignar direcciones físicas a las direcciones IPv6 (dirección global o dirección local de vínculo). Esta asignación se mantiene en la caché de detección de equipos cercanos (caché de ND). El proceso de ND es el equivalente al proceso de ARP de IPv4, y la caché de ND es similar a la tabla de ARP. Un nodo IPv6 puede obtener la dirección MAC de su equipo cercano mediante el protocolo de detección de equipos cercanos (ND). Envía un mensaje de solicitud de equipo cercano (NS) a la dirección de multidifusión de nodo solicitado de todos los nodos y espera un mensaje de anuncio de vecino (NA) correspondiente. La dirección MAC obtenida a través de este proceso se almacena en la memoria caché de ND.

Cada instancia de IP tiene una caché de ND. La caché de ND se mantiene como una matriz de entradas. El tamaño de la matriz se define en el momento de la compilación. Para ello, se establece la opción ***NX_IPV6_NEIGHBOR_CACHE_SIZE** _ en _*_nx_user.h_**. Tenga en cuenta que todas las interfaces asociadas a una instancia de IP comparten la misma caché de ND.

La caché de ND completa está vacía cuando se inicia NetX Duo. A medida que se ejecuta el sistema, NetX Duo actualiza automáticamente la caché de ND, y agrega y elimina entradas según el protocolo ND. Sin embargo, una aplicación también puede actualizar la caché de ND mediante la adición y eliminación de entradas de caché manualmente con los siguientes servicios de NetX Duo:

- ***nxd_nd_cache_entry_delete***  
- ***nxd_nd_cache_entry_set***   
- ***nxd_nd_cache_invalidate***

Al enviar y recibir paquetes IPv6, NetX Duo actualiza automáticamente la tabla de la caché de ND.

## <a name="internet-control-message-protocol-in-ipv6-icmpv6"></a>Protocolo de mensajes de control de Internet en IPv6 (ICMPv6)  

El rol de ICMPv6 en IPv6 se ha expandido en gran medida para admitir la asignación de direcciones IPv6 y la detección de enrutadores. Además, NetX Duo ICMPv6 admite solicitudes y respuestas de eco, informes de errores de ICMPv6 y mensajes de redireccionamiento de ICMPv6.

### <a name="icmpv6-enable"></a>Habilitación de ICMPv6    
Antes de que NetX Duo pueda procesar los mensajes ICMPv6, la aplicación debe llamar al servicio ***nxd_icmp_enable*** para habilitar el procesamiento de ICMPv6 como se explicó anteriormente. 

### <a name="icmpv6-messages"></a>Mensajes de ICMPv6     
La estructura de encabezado de ICMPv6 es similar a la estructura de encabezado de ICMPv4. Como se muestra a continuación, el encabezado de ICMPv6 básico contiene tres campos de tipo, código y suma de comprobación, además de la longitud variable de los datos opcionales de ICMPv6. 

![Diagrama de un encabezado de ICMPv6 básico.](./media/user-guide/image19.png)

**FIGURA 10. Encabezado ICMPv6 básico**

|Campo |Tamaño (bytes) |Descripción |
|-----|-----|-----|
|     | 1   |Identifica el tipo de mensaje de ICMPv6 |
|     |     |1 Destino no accesible |
|     |     |2 Paquete demasiado grande |
|     |     |3 Tiempo superado |
|     |     |4 Problema de parámetro |
|     |     |128 Solicitud de eco |
|     |     |129 Respuesta de eco |
|     |     |133 Solicitud de enrutador |
|     |     |134 Anuncio de enrutador |
|     |     |135 Solicitud de equipo cercano |
|     |     |136 Anuncio de equipo cercano |
|     |     |137 Mensaje de redireccionamiento |
|Código | 1   |Califica aún más el tipo de mensaje de ICMPv6. Se suele usar con los mensajes de error. Si no se usa, se establece en cero. La solicitud/respuesta de eco y los mensajes de NS no los usan.|
|Suma de comprobación | 2 |Campo de suma de comprobación de 16 bits para el encabezado de ICMP. Se trata de un complemento de 16 bits del mensaje de ICMPv6 completo, incluido el encabezado de ICMPv6. También incluye un pseudoencabezado de la dirección de origen IPv6, la dirección de destino y la longitud de carga del paquete. |

A continuación se muestra un encabezado de solicitud de equipo cercano de ejemplo.

![Diagrama de un encabezado de solicitud de equipo cercano de ejemplo.](./media/user-guide/image20.jpg)

**FIGURA 11. Encabezado de ICMPv6 para un mensaje de solicitud de equipo cercano**

|Campo |Tamaño (bytes) |Descripción |
|-----|-----|-----|
|Tipo | 1   |Identifica el tipo de mensaje de ICMPv6 para mensajes de solicitud de equipos cercano. El valor es 135. |
|Código | 1   |No se utiliza. Establecer en 0. |
|Suma de comprobación | 2  |Campo de suma de comprobación de 16 bits para el encabezado de ICMPv6. |
|Reservada | 4  |4 bytes reservados establecidos en 0. |
|Dirección de destino | 16  |Dirección IPv6 de destino de la solicitud. Para la resolución de direcciones IPv6, se trata de la dirección IP de unidifusión real del dispositivo cuya dirección de nivel de vínculo debe resolverse. |
|Opciones | Variable |Información opcional especificada por el protocolo de detección de equipos cercanos. |

### <a name="icmpv6-ping-request"></a>Solicitud de ping de ICMPv6
En las aplicaciones de NetX Duo, use ***nxd_icmp_ping*** para emitir solicitudes de ping de IPv6 o IPv4, en función de la dirección IP de destino especificada en los parámetros.  

### <a name="icmpv6-ping-response"></a>Respuesta de ping de ICMPv6
Una respuesta de ping de ICMPv6 es otro tipo de mensaje de ICMPv6 que el componente de ICMPv6 genera internamente en respuesta a una solicitud de ping de ICMPv6 externa. Además de la confirmación, la respuesta de ping de ICMPv6 también contiene una copia de los datos de usuario proporcionados en la solicitud de ping de ICMPv6.  

### <a name="thread-suspension"></a>Suspensión de subprocesos
Los subprocesos de aplicación se pueden suspender mientras intentan hacer ping en otro miembro de la red. Después de recibir una respuesta de ping, se proporciona el mensaje de respuesta de ping al primer subproceso suspendido y se reanuda el subproceso. Al igual que todos los servicios de NetX Duo, la suspensión de una solicitud de ping tiene un tiempo de espera opcional.  

### <a name="other-icmpv6-messages"></a>Otros mensajes de ICMPv6
Los mensajes de ICMPv6 son necesarios para las siguientes características:  

- Detección de equipos cercanos  
- Configuración automática de direcciones sin estado 
- Detección de enrutador 
- Detección de inaccesibilidad de equipos cercanos  

### <a name="neighbor-unreachability-router-and-prefix-discovery"></a>Detección de inaccesibilidad de equipos cercanos, enrutador y prefijo    
La detección de inaccesibilidad de equipos cercanos, de enrutador y de prefijo se basa en el protocolo de detección de equipos cercanos y se describe a continuación. 

***Detección de inaccesibilidad de equipos cercanos:*** un dispositivo IPv6 busca en la memoria caché de detección de equipos cercanos (ND) la dirección del nivel de vínculo de destino cuando quiere enviar un paquete. El destino inmediato, que a veces se denomina "próximo salto", puede ser el destino real en el mismo vínculo o puede ser un enrutador si el destino se encuentra fuera del vínculo. Una entrada de caché de ND contiene el estado sobre la inaccesibilidad de un equipo cercano.

Un estado REACHABLE indica que el equipo cercano se considera accesible. Un equipo cercano es accesible si ha recibido recientemente una confirmación de recepción de los paquetes enviados al equipo cercano. La confirmación en NetX Duo adopta la forma de recepción de un mensaje de NA del equipo cercano en respuesta a un mensaje de NS enviado por el dispositivo NetX Duo. NetX Duo también cambiará el estado del equipo cercano a REACHABLE si la aplicación llama al servicio ***nxd_nd_cache_entry_set*** de NetX Duo para introducir manualmente un registro de caché.

***Detección de enrutadores:*** un dispositivo IPv6 usa un enrutador para reenviar todos los paquetes previstos para los destinos fuera del vínculo. También puede usar la información enviada por el enrutador, como mensajes de anuncio de enrutador (RA), para configurar sus direcciones IPv6 globales.

Un dispositivo en la red puede iniciar el proceso de detección del enrutador mediante el envío de un mensaje de solicitud de enrutador (RS) a la dirección de multidifusión de todos los enrutadores (FF01::2). O bien, puede esperar en la dirección de multidifusión de todos los nodos (FF::1) un RA periódico de los enrutadores.

Un mensaje de RA contiene la información del prefijo para configurar una dirección IPv6 para esa red. En NetX Duo, la solicitud de enrutador está habilitada de forma predeterminada y se puede deshabilitar estableciendo la opción de configuración ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _ en _*_nx_user.h_**. Consulte Opciones de configuración en el capítulo "Instalación y uso de NetX Duo" para obtener más detalles sobre cómo establecer los parámetros de solicitud de enrutador. 

***Detección de prefijos***: un dispositivo IPv6 usa la detección de prefijos para saber qué hosts de destino son accesibles directamente sin pasar por un enrutador. Esta información se pone a disposición del dispositivo IPv6 desde los mensajes de RA del enrutador. El dispositivo IPv6 almacena la información de prefijo en una tabla de prefijos. La detección de prefijos hace coincidir un prefijo de la tabla de prefijos de dispositivos IPv6 con una dirección de destino. Un prefijo coincide con una dirección de destino si todos los bits del prefijo coinciden con los bits más significativos de la dirección de destino. Si hay más de un prefijo que cubre una dirección, se selecciona el prefijo más largo.

### <a name="icmpv6-error-messages"></a>Mensajes de error de ICMPv6    
Se admiten los siguientes mensajes de error de ICMPv6 en NetX Duo:  

- Destino no accesible  
- Paquete demasiado grande  
- Tiempo superado  
- Problema de parámetro  

## <a name="user-datagram-protocol-udp"></a>Protocolo de datagramas de usuario (UDP)

El protocolo de datagramas de usuario (UDP) proporciona la forma más sencilla de transferencia de datos entre los miembros de la red (RFC 768). Los paquetes de datos de UDP se envían de un miembro de red a otro de la mejor forma posible; es decir, no hay ningún mecanismo integrado para la confirmación por parte del destinatario del paquete. Además, el envío de un paquete UDP no requiere que se establezca una conexión de antemano. Debido a esto, la transmisión de paquetes UDP es muy eficaz.

Para los desarrolladores que migran sus aplicaciones de NetX a NetX Duo solo hay algunos cambios básicos en la funcionalidad de UDP entre NetX y NetX Duo. Esto se debe a que IPv6 se ocupa principalmente del nivel de IP subyacente. Todos los servicios de UDP de NetX Duo se pueden usar para la conectividad IPv4 o IPv6.

### <a name="udp-header"></a>Encabezado UDP       
UDP coloca un encabezado de paquete simple delante de los datos de la aplicación en la transmisión y quita un encabezado UDP similar del paquete en la recepción antes de entregar un paquete UDP recibido a la aplicación. UDP emplea el protocolo IP para enviar y recibir paquetes, lo que significa que hay un encabezado IP delante del encabezado UDP cuando el paquete está en la red. En la figura 12 se muestra el formato del encabezado UDP.

![Diagrama del formato de encabezado UDP.](./media/user-guide/image21.png)

### <a name="figure-12-udp-header"></a>FIGURA 12. Encabezado UDP

> [!NOTE]
> *Se espera que todos los encabezados de la implementación de UDP/IP estén en formato **big endian**. En este formato, el byte más significativo de la palabra reside en la dirección de bytes más baja.*

A continuación se describe el formato de encabezado UDP:

|Campo del encabezado |Propósito |
|---|---|
|**Número de puerto de origen de 16 bits** |Este campo contiene el puerto desde el que se envía el paquete UDP. El intervalo de puertos UDP válidos va del 1 al 0xFFFF. |
|**Número de puerto de destino de 16 bits** |Este campo contiene el puerto UDP al que se envía el paquete. El intervalo de puertos UDP válidos va del 1 al 0xFFFF. |
|**Longitud de UDP de 16 bits** |Este campo contiene el número de bytes del paquete UDP, incluido el tamaño del encabezado UDP. |
|**Suma de comprobación de UDP de 16 bits** |Este campo contiene la suma de comprobación de 16 bits del paquete, incluidos el encabezado UDP, el área de datos del paquete y el pseudoencabezado IP. |

### <a name="udp-enable"></a>Habilitación de UDP   
Antes de que sea posible la transmisión de paquetes UDP, la aplicación debe habilitar primero UDP mediante una llamada al servicio ***nx_udp_enable***. Una vez habilitado, la aplicación puede enviar y recibir paquetes UDP.  

### <a name="udp-socket-create"></a>Creación de sockets UDP    
Los sockets UDP se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de la aplicación. En el servicio ***nx_udp_socket_create*** se definen el tipo inicial de servicio, el período de vida y la profundidad de la cola de recepción. No hay ningún límite en el número de sockets UDP de una aplicación.

### <a name="udp-checksum"></a>Suma de comprobación de UDP   
El protocolo IPv6 requiere un cálculo de suma de comprobación de encabezado UDP en los datos de paquetes, mientras que en el protocolo IPv4 es opcional.  

UDP especifica una suma de comprobación de 16 bits del complemento a uno que incluye el pseudoencabezado IP (que consta de la dirección IP de origen, la dirección IP de destino, el protocolo y la longitud de palabra de IP), el encabezado UDP y los datos del paquete UDP. Las únicas diferencias entre las sumas de comprobación de encabezado de paquetes UDP de IPv4 e IPv6 son que las direcciones IP de origen y de destino son de 32 bits en IPv4, mientras que en IPv6 son de 128 bits. Si la suma de comprobación de UDP calculada es 0, se almacena como todo unos (0xFFFF). Si el socket de envío tiene deshabilitada la lógica de la suma de comprobación de UDP, se coloca un cero en el campo de suma de comprobación de UDP para indicar que no se ha calculado la suma de comprobación.

Si la suma de comprobación de UDP no coincide con la suma de comprobación calculada por el receptor, simplemente se descarta el paquete UDP.

En la red IPv4, la suma de comprobación de UDP es opcional. NetX Duo permite a una aplicación habilitar o deshabilitar el cálculo de la suma de comprobación de UDP por cada socket. De manera predeterminada, la lógica de la suma de comprobación del socket UDP está habilitada. La aplicación puede deshabilitar la lógica de la suma de comprobación para un socket UDP determinado mediante una llamada al servicio ***nx_udp_socket_checksum_disable** _. En la red IPv6, sin embargo, la suma de comprobación de UDP es obligatoria. Por lo tanto, el servicio _ *_nx_udp_socket_checksum_disable_** no deshabilitaría la lógica de suma de comprobación de UDP al enviar un paquete a través de la red IPv6.

Algunos controladores Ethernet pueden generar la suma de comprobación de UDP sobre la marcha. Si el sistema puede usar la característica de cálculo de la suma de comprobación por hardware, la biblioteca de NetX Duo se puede compilar sin la lógica de la suma de comprobación. Para deshabilitar la suma de comprobación del software UDP, la biblioteca de NetX Duo debe compilarse con los siguientes símbolos definidos: ***NX_DISABLE_UDP_TX_CHECKSUM** _ y _*_NX_DISABLE_UDP_RX_CHECKSUM_*_ (se describen en el segundo capítulo). Las opciones de configuración quitan completamente la lógica de suma de comprobación de UDP de NetX Duo, mientras que la llamada al servicio _ *_nx_udp_socket_checksum_disable_** permite a la aplicación deshabilitar el procesamiento de suma de comprobación de UDP de IPv4 por socket.

### <a name="udp-ports-and-binding"></a>Enlaces y puertos UDP      
Un puerto UDP es un punto de conexión lógico en el protocolo UDP. Hay 65 535 puertos válidos en el componente de UDP de NetX Duo, que van del 1 al 0xFFFF. Para enviar o recibir datos UDP, la aplicación debe crear primero un socket UDP y, a continuación, enlazarlo al puerto deseado. Después de enlazar un socket UDP a un puerto, la aplicación puede enviar y recibir datos en ese socket.

### <a name="udp-fast-pathtrade"></a>UDP Fast Path&trade;   
UDP Fast Path&trade; es el nombre de una ruta de baja sobrecarga de paquetes mediante la implementación de UDP de NetX Duo. El envío de un paquete UDP requiere solo algunas llamadas de función: ***nx_udp_socket_send** _, _*_nx_ip_packet_send_*_ y la llamada eventual al controlador de red. _*_nx_udp_socket_send_*_ está disponible en NetX Duo para las aplicaciones de NETX existentes y solo es aplicable a los paquetes IPv4. Sin embargo, el método preferido es usar el servicio _ *_nxd_udp_socket_send_** que se describe a continuación. En la recepción de paquetes UDP, el paquete UDP se coloca en la cola de recepción del socket UDP adecuado o se entrega a un subproceso de la aplicación en suspensión en una única llamada de función desde el procesamiento de interrupciones de recepción del controlador de red. Esta lógica altamente optimizada para enviar y recibir paquetes UDP es la esencia de la tecnología UDP Fast Path.  

### <a name="udp-packet-send"></a>Envío de paquetes UDP    
El envío de datos UDP mediante redes IPv6 o IPv4 se realiza fácilmente mediante una llamada a la función ***nxd_udp_socket_send** _. El autor de la llamada debe establecer la versión de IP en el campo _nx_ip_version* del parámetro de puntero NXD_ADDRESS. NetX Duo determinará la mejor dirección de origen para los paquetes UDP transmitidos en función de la dirección IPv4/IPv6 de destino. Este servicio coloca un encabezado UDP delante de los datos del paquete y lo envía a la red mediante una rutina interna de envío IP. No hay ninguna suspensión de subprocesos en el envío de paquetes UDP porque todas las transmisiones de paquetes UDP se procesan inmediatamente. 

En el caso de los destinos de multidifusión o de difusión, la aplicación debe especificar la dirección IP de origen que se usará si el dispositivo con NetX Duo tiene varias direcciones IP para elegir. Esto se puede realizar con el servicio ***nxd_udp_socket_source_send.***

> [!IMPORTANT]    
> *Si se usa **nx_udp_socket_send** para transmitir paquetes de multidifusión o de difusión, se utiliza la dirección IP de la primera interfaz habilitada como dirección de origen*.

> [!NOTE] 
> *Si la lógica de la suma de comprobación de UDP está habilitada para este socket, la operación de suma de comprobación se realiza en el contexto del subproceso de llamada, sin bloquear el acceso a las estructuras de datos de UDP o IP.* 

> [!WARNING]    
> *Los datos de la carga UDP que residen en la estructura NX_PACKET deben residir en un límite de palabra larga. La aplicación debe dejar espacio suficiente entre el puntero antepuesto y el puntero de inicio de datos de NetX Duo para colocar los encabezados del soporte físico, IP y UDP*.

### <a name="udp-packet-receive"></a>Recepción de paquetes UDP    
Los subprocesos de la aplicación pueden recibir paquetes UDP desde un socket determinado mediante una llamada a ***nx_udp_socket_receive***. La función de recepción del socket entrega el paquete más antiguo de la cola de recepción del socket. Si no hay paquetes en la cola de recepción, el subproceso que realiza la llamada se puede suspender (con un tiempo de espera opcional) hasta que llegue un paquete.

El procesamiento de paquetes de recepción de UDP (normalmente llamado desde el controlador de interrupciones de recepción del controlador de red) es responsable de colocar el paquete en la cola de recepción del socket UDP o de entregarlo al primer subproceso suspendido en espera de un paquete. Si el paquete está en cola, el procesamiento de recepción también comprueba la profundidad máxima de la cola de recepción asociada al socket. Si este paquete recién puesto en cola supera la profundidad de la cola, se descarta el paquete más antiguo de la cola.

### <a name="udp-receive-notify"></a>Notificación de recepción de UDP   
Si el subproceso de la aplicación debe procesar los datos recibidos desde más de un socket, se debe usar la función ***nx_udp_socket_receive_notify***. Esta función registra una función de devolución de llamada de paquetes de recepción para el socket. Cada vez que se recibe un paquete en el socket, se ejecuta la función de devolución de llamada.

El contenido de la función de devolución de llamada es específico de la aplicación; sin embargo, lo más probable es que contenga lógica para notificar al subproceso de procesamiento que un paquete ahora está disponible en el socket correspondiente.

### <a name="peer-address-and-port"></a>Dirección y puerto del mismo nivel   
Al recibir un paquete UDP, la aplicación puede encontrar el número de puerto y la dirección IP del remitente mediante el servicio ***nx_udp_packet_info_extract***. Si la devolución es correcta, este servicio proporciona información sobre la dirección IP del remitente, el número de puerto del remitente y la interfaz local a través de la cual se recibió el paquete.  

### <a name="thread-suspension"></a>Suspensión de subprocesos   
Como se ha mencionado anteriormente, los subprocesos de la aplicación se pueden suspender al intentar recibir un paquete UDP en un puerto UDP determinado. Una vez que se recibe un paquete en ese puerto, se asigna al primer subproceso suspendido y, a continuación, se reanuda el subproceso. Existe un tiempo de espera opcional disponible cuando hay una suspensión en la recepción de un paquete UDP, una característica disponible para la mayoría de los servicios de NetX Duo.  

### <a name="udp-socket-statistics-and-errors"></a>Estadísticas y errores del socket UDP     
Si se habilita, el software de socket UDP de NetX Duo realiza un seguimiento de varios errores y estadísticas que pueden ser útiles para la aplicación. Se mantienen las estadísticas y los informes de errores siguientes para cada instancia de IP/UDP:

- Número total de paquetes UDP enviados  
- Número total de bytes UDP enviados  
- Número total de paquetes UDP recibidos   
- Número total de bytes UDP recibidos  
- Número total de paquetes UDP no válidos  
- Número total de paquetes UDP recibidos eliminados  
- Número total de errores de suma de comprobación de recepción de UDP  
- Paquetes de socket UDP enviados  
- Bytes de socket UDP enviados  
- Paquetes de socket UDP recibidos   
- Bytes de socket UDP recibidos  
- Paquetes de socket UDP puestos en cola  
- Paquetes de socket UDP recibidos eliminados  
- Errores de suma de comprobación de socket UDP  

Todos estos informes de errores y estadísticas están disponibles para la aplicación con el servicio ***nx_udp_info_get** _ para las estadísticas acumuladas de UDP en todos los sockets UDP y el servicio _ *_nx_udp_socket_info_get_** para las estadísticas de UDP en el socket UDP especificado.

### <a name="udp-socket-control-block-nx_udp_socket"></a>Bloque de control de socket UDP NX_UDP_SOCKET
Las características de cada socket UDP se encuentran en el bloque de control NX_UDP_SOCKET asociado. Contiene información útil, como el vínculo a la estructura de datos IP, la interfaz de red para las rutas de acceso de envío y recepción, el puerto enlazado y la cola de paquetes de recepción. Esta estructura se define en el archivo ***tx_api.h***.

## <a name="transmission-control-protocol-tcp"></a>Protocolo de control de transmisión (TCP)

El protocolo de control de transmisión (TCP) proporciona transferencia de datos de secuencia confiable entre dos miembros de la red (RFC 793). El miembro receptor comprueba y confirma todos los datos enviados desde un miembro de la red. Además, los dos miembros deben haber establecido una conexión antes de cualquier transferencia de datos. Todo esto produce una transferencia de datos confiable; sin embargo, requiere bastante más sobrecarga que la transferencia de datos UDP descrita previamente.

Excepto en los casos en los que se indique, no hay ningún cambio en los servicios de API del protocolo TCP entre NetX y NetX Duo, ya que IPv6 se preocupa principalmente del nivel de IP subyacente. Todos los servicios de TCP de NetX Duo se pueden usar para conexiones IPv4 o IPv6.

### <a name="tcp-header"></a>Encabezado TCP   
En la transmisión, el encabezado TCP se coloca delante de los datos del usuario. En la recepción, el encabezado TCP se quita del paquete entrante y solo están disponibles para la aplicación los datos del usuario. TCP emplea el protocolo IP para enviar y recibir paquetes, lo que significa que hay un encabezado IP delante del encabezado TCP cuando el paquete está en la red. En la figura 13 se muestra el formato del encabezado TCP.

![Diagrama del formato de encabezado TCP.](./media/user-guide/image22.png)

### <a name="figure-13-tcp-header"></a>FIGURA 13. Encabezado TCP

A continuación se describe el formato de encabezado TCP:

|Campo de&nbsp;encabezado |Propósito |
|------|------|
| **Número de puerto de origen de 16 bits** | Este campo contiene el puerto por el que se envía el paquete TCP. El intervalo de puertos TCP válidos va del 1 al 0xFFFF. |
| **Puerto de destino de 16 bits** | Este campo contiene el puerto al que se envía el paquete TCP. El intervalo de puertos TCP válidos va del 1 al 0xFFFF. |
| **Número de secuencia de 32 bits** | Este campo contiene el número de secuencia de los datos enviados desde este extremo de la conexión. La secuencia original se establece durante la secuencia de conexión inicial entre dos nodos TCP. Cada transferencia de datos desde ese punto da lugar a un incremento del número de secuencia en la cantidad de bytes enviados. |
| **Número de confirmación de 32 bits** | Este campo contiene el número de secuencia correspondiente al último byte recibido por este lado de la conexión. Se utiliza para determinar si el otro extremo de la conexión ha recibido correctamente o no los datos que se han enviado anteriormente. |
| **Longitud del encabezado de 4 bits** | Este campo contiene el número de palabras de 32 bits que hay en el encabezado TCP. Si no hay opciones en el encabezado TCP, el valor de este campo es 5. |
| **Bits de código de 6 bits** |Este campo contiene los seis bits de código diferentes que se usan para indicar diversa información de control asociada a la conexión. Los bits de control se definen de la siguiente manera: <br \> - URG (21): datos de urgencia<br \> - ACK (20): el número de confirmación es válido<br \> - PSH (19): controlar estos datos inmediatamente<br \> - RST (18): restablecer la conexión<br \> - SYN (17): sincronizar los números de secuencia (se usa para establecer la conexión) <br \> - FIN (16): el remitente ha finalizado con la transmisión (se usa para la conexión) |
|**Ventana de 16 bits** |Este campo se usa para el control de flujo. Contiene la cantidad de bytes que el socket puede recibir actualmente. Básicamente se usa para el control de flujo. El remitente es responsable de asegurarse de que los datos que se van a enviar se ajustan a la ventana anunciada del receptor. |
|**Suma de comprobación de TCP de 16 bits** |Este campo contiene la suma de comprobación de 16 bits del paquete, incluidos el encabezado TCP, el área de datos del paquete y el encabezado pseudo IP. |
|**Puntero urgente de 16 bits** |Este campo contiene el desplazamiento positivo del último byte de los datos urgentes. Este campo solo es válido si se establece en el encabezado el bit de código URG. |

> [!NOTE]  
> *Se espera que todos los encabezados de la implementación de TCP/IP estén en formato **big endian**. En este formato, el byte más significativo de la palabra reside en la dirección de bytes más baja.*

### <a name="tcp-enable"></a>Habilitación de TCP       
Antes de que las conexiones TCP y las transmisiones de paquetes sean posibles, la aplicación debe habilitar primero TCP mediante una llamada al servicio ***nx_tcp_enable***. Una vez habilitada, la aplicación puede acceder a todos los servicios de TCP.  

### <a name="tcp-socket-create"></a>Creación de sockets TCP    
Los sockets TCP se crean durante la inicialización o en tiempo de ejecución mediante subprocesos de la aplicación. En el servicio ***nx_tcp_socket_create*** se definen el tipo inicial de servicio, el período de vida y el tamaño de la ventana. No hay ningún límite en el número de sockets TCP de una aplicación.  

### <a name="tcp-checksum"></a>Suma de comprobación de TCP     
TCP especifica una suma de comprobación de 16 bits del complemento a uno que incluye el pseudoencabezado IP (que consta de la dirección IP de origen, la dirección IP de destino, el protocolo y la longitud de palabra de IP), el encabezado TCP y los datos del paquete TCP. La única diferencia entre las sumas de comprobación de encabezado de paquete TCP IPv4 e IPv6 es que las direcciones IP de origen y destino son de 32 bits en IPv4 y 128 bits en IPv6. 

Algunos controladores de red pueden realizar el cálculo y la validación de la suma de comprobación de TCP por hardware. En estos sistemas, es posible que las aplicaciones deseen usar la lógica de la suma de comprobación por hardware tanto como sea posible para reducir la sobrecarga en tiempo de ejecución. Las aplicaciones pueden deshabilitar por completo la lógica del cálculo de la suma de comprobación de TCP de la biblioteca de NetX en tiempo de compilación mediante la definición de ***NX_DISABLE_TCP_TX_CHECKSUM** _ y _*_NX_DISABLE_TCP_RX_CHECKSUM_**. De esta manera, el código de la suma de comprobación de TCP no se compila. Sin embargo, hay que tener cuidado si se instala el paquete IPsec de NetX Duo opcional y la conexión TCP puede necesitar atravesar un canal seguro. En este caso, los datos de los paquetes que pertenecen a la conexión TCP ya están cifrados y la mayoría de los módulos de suma de comprobación de TCP de hardware presentes en el controlador de red no pueden generar un valor de suma de comprobación correcto a partir de la carga de TCP cifrada.

Para solucionar este problema, la aplicación debe mantener la lógica de la suma de comprobación de TCP disponible en la biblioteca y usar la característica de funcionalidad de interfaz. Con la característica de funcionalidad de interfaz habilitada, el módulo de TCP sabe cómo administrar correctamente la suma de comprobación de TCP si el controlador también puede calcular el valor de la suma de comprobación:

1) Si el paquete TCP no está sujeto a un proceso IPsec, el hardware de la interfaz de red puede calcular la suma de comprobación. Por lo tanto, el módulo de TCP no intenta calcular la suma de comprobación.

2) Si se instala el paquete IPsec y el paquete TCP está sujeto a un proceso IPsec, el módulo de TCP calcula la suma de comprobación en el software antes de enviar el paquete a la capa IPsec.

### <a name="tcp-port"></a>Puerto TCP     
Un puerto TCP es un punto de conexión lógico en el protocolo TCP. Hay 65 535 puertos válidos en el componente de TCP de NetX Duo, que van del 1 al 0xFFFF. A diferencia de UDP, en que los datos de un puerto se pueden enviar a cualquier otro puerto de destino, un puerto TCP se conecta a otro puerto TCP específico, y solo cuando se establece esta conexión se puede realizar cualquier transferencia de datos (solo entre los dos puertos que conforman la conexión).

> [!IMPORTANT]
> *Los puertos TCP son completamente independientes de los puertos UDP; es decir, el puerto UDP número 1 no tiene relación con el puerto TCP número 1*.

### <a name="client-server-model"></a>Modelo cliente-servidor     
Para usar TCP para la transferencia de datos, primero se debe establecer una conexión entre los dos sockets TCP. El establecimiento de la conexión se realiza en modo cliente-servidor. El lado cliente de la conexión es el lado que inicia la conexión, mientras que el lado servidor simplemente espera las solicitudes de conexión de cliente antes de ejecutar cualquier procesamiento.

> [!IMPORTANT]
> *En el caso de los dispositivos de host múltiple, NetX Duo determina automáticamente la dirección de origen que se usará para la conexión y la dirección del próximo salto en función de la dirección IP de destino de la conexión. Dado que TCP está limitado a enviar paquetes a direcciones de destino de unidifusión (por ejemplo, sin difusión), NetX Duo no requiere una "sugerencia" para elegir la dirección IPv6 de origen*.

### <a name="tcp-socket-state-machine"></a>Máquina de estados del socket TCP      
La conexión entre dos sockets TCP (un cliente y un servidor) es compleja y se administra en modo de máquina de estados. Cada socket TCP se inicia en estado CLOSED. Mediante los eventos de conexión, la máquina de estados de cada socket cambia al estado ESTABLISHED, que es donde tiene lugar la mayor parte de la transferencia de datos en TCP. Cuando un lado de la conexión ya no quiere enviar más datos, se desconecta. Una vez que el otro lado se desconecta, el socket TCP vuelve al estado CLOSED. Este proceso se repite cada vez que un cliente y un servidor TCP establecen y cierran una conexión. En la figura 14 se muestran los distintos estados de la máquina de estados de TCP.

### <a name="tcp-client-connection"></a>Conexión del cliente TCP       
Como se mencionó anteriormente, el lado cliente de la conexión TCP inicia una solicitud de conexión a un servidor TCP. Para poder realizar una solicitud de conexión, TCP debe estar habilitado en la instancia de IP del cliente. Además, el socket TCP del cliente debe crearse con el servicio ***nx_tcp_socket_create** _ y enlazarse a un puerto mediante el servicio _ *_nx_tcp_client_socket_bind_***.

Una vez enlazado el socket de cliente, se utiliza el servicio ***nxd_tcp_client_socket_connect*** se usa para establecer una conexión con un servidor TCP. Tenga en cuenta que el socket debe estar en estado CLOSED para iniciar un intento de conexión. Para establecer la conexión, primero se emite un paquete SYN y, a continuación, se espera a que el servidor devuelva un paquete SYN ACK, lo que significa que se acepta la solicitud de conexión. Una vez recibido el paquete SYN ACK, NetX Duo responde con un paquete ACK y promueve el socket de cliente al estado ESTABLISHED.

![Diagrama de los estados de la máquina de estados de TCP.](./media/user-guide/image24.png)   

**FIGURA 14. Estados de la máquina de estados de TCP**


> [!WARNING]
> *Las aplicaciones deben usar **nxd_tcp_client_socket_connect** para las conexiones TCP IPv4 e IPv6. Las aplicaciones pueden seguir usando **nx_tcp_client_socket_connect** para las conexiones TCP IPv4, pero se recomienda a los desarrolladores que utilicen **nxd_tcp_client_socket_connect**, ya que **nx_tcp_client_socket_connect** se dejará de usar*.

*De modo parecido, **nxd_tcp_socket_peer_info_get** funciona con conexiones TCP IPv4 o IPv6. Sin embargo, **nx_tcp_socket_peer_info_get** sigue estando disponible para las aplicaciones heredadas. Se recomienda a los desarrolladores que utilicen **nxd_tcp_socket_peer_info_get** en adelante*.

### <a name="tcp-client-disconnection"></a>Desconexión del cliente TCP    
El cierre de la conexión se realiza mediante una llamada a ***nx_tcp_socket_disconnect***. Si no se especifica ninguna suspensión, el socket de cliente envía un paquete RST al socket de servidor y coloca el socket en estado CLOSED. De lo contrario, si se solicita una suspensión, se realiza el protocolo de desconexión TCP completo, como se indica a continuación: 

- Si el servidor inició previamente una solicitud de desconexión (el socket de cliente ya recibió un paquete FIN, respondió con un paquete ACK y está en estado CLOSE WAIT), NetX Duo promueve el estado del socket TCP de cliente al estado LAST ACK y envía un paquete FIN. Después, espera un paquete ACK del servidor antes de completar la desconexión y de entrar en estado CLOSED.

- Por otro lado, si el cliente es el primero en iniciar una solicitud de desconexión (el servidor no se desconectó y el socket todavía está en estado ESTABLISHED), NetX Duo envía un paquete FIN para iniciar la desconexión y espera a recibir un paquete FIN y un paquete ACK del servidor antes de completar la desconexión y colocar el socket en estado CLOSED.

Si todavía hay paquetes en la cola de transmisión del socket, NetX Duo realiza una suspensión durante el tiempo de espera especificado para permitir que se confirmen los paquetes. Si se agota el tiempo de espera, NetX Duo vacía la cola de transmisión del socket de cliente. 

Para desenlazar el puerto del socket de cliente, la aplicación llama a ***nx_tcp_client_socket_unbind***. El socket se debe encontrar en estado CLOSED o en el proceso de desconexión (por ejemplo, TIMED WAIT) antes de que se libere el puerto; de lo contrario, se devuelve un error.

Por último, si la aplicación ya no necesita el socket de cliente, llama a ***nx_tcp_socket_delete*** para eliminar el socket.

### <a name="tcp-server-connection"></a>Conexión del servidor TCP      
El lado servidor de una conexión TCP es pasivo; es decir, el servidor espera a que un cliente inicie la solicitud de conexión. Para aceptar una conexión de cliente, TCP debe estar habilitado antes en la instancia de IP mediante una llamada al servicio ***nx_tcp_enable** _. A continuación, la aplicación debe crear un socket TCP mediante el servicio _ *_nx_tcp_socket_create_**.  

También se debe configurar el socket de servidor para la escucha de solicitudes de conexión. Esto se realiza mediante el servicio ***nx_tcp_server_socket_listen***. Este servicio coloca el socket de servidor en estado LISTEN y enlaza el puerto especificado del servidor al socket.

> [!NOTE] 
> *Para establecer una rutina de devolución de llamada de escucha de sockets, la aplicación especifica la función de devolución de llamada adecuada para el argumento tcp_listen_callback del servicio **nx_tcp_server_socket_listen**. En este momento, NetX Duo ejecutará la función de devolución de llamada de la aplicación siempre que se solicite una nueva conexión en este puerto del servidor. El procesamiento de la devolución de llamada está bajo el control de la aplicación.*

Para aceptar solicitudes de conexión de cliente, la aplicación llama al servicio ***nx_tcp_server_socket_accept** _. El socket de servidor debe estar en estado LISTEN o en estado SYN RECEIVED (es decir, el servidor está en estado LISTEN y ha recibido un paquete SYN de un cliente que solicita una conexión) para llamar al servicio de aceptación. Un estado de devolución correcto desde _ *_nx_tcp_server_socket_accept_** indica que se ha configurado la conexión y el socket de servidor está en estado ESTABLISHED.

Una vez que el socket de servidor tenga una conexión válida, las solicitudes de conexión de cliente adicionales se ponen en cola hasta la profundidad especificada por el parámetro *listen_queue_size, que se pasa al servicio* ***nx_tcp_server_socket_listen** _. Para procesar las conexiones posteriores en un puerto del servidor, la aplicación debe llamar a _ *_nx_tcp_server_socket_relisten_** con un socket disponible (es decir, un socket en estado CLOSED). Tenga en cuenta que se puede usar el mismo socket de servidor si ya ha finalizado la conexión anterior asociada con el socket y el socket está en estado CLOSED.

### <a name="tcp-server-disconnection"></a>Desconexión del servidor TCP     
El cierre de la conexión se realiza mediante una llamada a ***nx_tcp_socket_disconnect***. Si no se especifica ninguna suspensión, el socket de servidor envía un paquete RST al socket de cliente y coloca el socket en estado CLOSED. De lo contrario, si se solicita una suspensión, se realiza el protocolo de desconexión TCP completo, como se indica a continuación:

- Si el cliente inició previamente una solicitud de desconexión (el socket de servidor ya recibió un paquete FIN, respondió con un paquete ACK y está en estado CLOSE WAIT), NetX Duo promueve el estado del socket TCP al estado LAST ACK y envía un paquete FIN. Después, espera un paquete ACK del cliente antes de completar la desconexión y de entrar en estado CLOSED.

- Por otro lado, si el servidor es el primero en iniciar una solicitud de desconexión (el cliente no se desconectó y el socket todavía está en estado ESTABLISHED), NetX Duo envía un paquete FIN para iniciar la desconexión y espera a recibir un paquete FIN y un paquete ACK del cliente antes de completar la desconexión y colocar el socket en estado CLOSED.

Si todavía hay paquetes en la cola de transmisión del socket, NetX Duo realiza una suspensión durante el tiempo de espera especificado para permitir que se confirmen esos paquetes. Si se agota el tiempo de espera, NetX Duo vacía la cola de transmisión del socket de servidor.

Cuando el procesamiento de la desconexión se completa y el socket de servidor se encuentra en estado CLOSED, la aplicación debe llamar al servicio ***nx_tcp_server_socket_unaccept** _ para finalizar la asociación de este socket con el puerto del servidor. Tenga en cuenta que la aplicación debe llamar a este servicio aunque _*_nx_tcp_socket_disconnect_*_ o _*_nx_tcp_server_socket_accept_*_ devuelvan un estado de error. Después de la devolución de _*_nx_tcp_server_socket_unaccept_*_, el socket se puede usar como un socket de cliente o de servidor, o incluso eliminarse si ya no se necesita. Si se desea aceptar otra conexión de cliente en el mismo puerto de servidor, se debe llamar al servicio _ *_nx_tcp_server_socket_relisten_** en este socket.

En el segmento de código siguiente se muestra la secuencia de llamadas que usa un servidor TCP típico:

```c
/* Set up a previously created TCP socket to
   listen on port 12 */
nx_tcp_server_socket_listen()

/* Loop to make a (another) connection. */
while(1)
{
    /* Wait for a client socket connection request
       for 100 ticks. */
    nx_tcp_server_socket_accept();

    /* (Send and receive TCP messages with the TCP
       client) */

    /* Disconnect the server socket. */
    nx_tcp_socket_disconnect();

    /* Remove this server socket from listening on
       the port. */
    nx_tcp_server_socket_unaccept(&server_socket);
    /* Set up server socket to relisten on the
       same port for the next client. */
    nx_tcp_server_socket_relisten();
}
```

### <a name="mss-validation"></a>Validación de MSS      
El tamaño máximo de segmento (MSS) es la cantidad máxima de bytes que puede recibir un host TCP sin que la capa IP subyacente los fragmente. Durante la fase de establecimiento de la conexión TCP, ambos extremos intercambian su propio valor de MSS de TCP, por lo que el remitente no envía un segmento de datos TCP mayor que el valor de MSS del receptor. El módulo TCP de NetX Duo validará opcionalmente el valor de MSS anunciado de su nodo del mismo nivel antes de establecer una conexión. De forma predeterminada, NetX Duo no habilita este tipo de comprobación. Las aplicaciones que deseen realizar la validación de MSS definirán ***NX_ENABLE_TCP_MSS_CHECK** _ al compilar la biblioteca de NetX Duo y el valor mínimo se definirá en _*_NX_TCP_MSS_MINIMUM_*_. Las conexiones TCP entrantes con valores de MSS inferiores a _ *_NX_TCP_MSS_MINIMUM_** se anulan.

### <a name="stop-listening-on-a-server-port"></a>Detención de la escucha en un puerto del servidor    
Si la aplicación ya no desea escuchar las solicitudes de conexión de cliente en un puerto del servidor que se especificó anteriormente mediante una llamada al servicio ***nx_tcp_server_socket_listen** _, la aplicación simplemente llamará al servicio _ *_nx_tcp_server_socket_unlisten_**. Este servicio coloca cualquier socket en espera de una conexión en estado CLOSED y libera los paquetes de solicitud de conexión de cliente en cola. 

### <a name="tcp-window-size"></a>Tamaño de la ventana de TCP   
Durante las fases de configuración y transferencia de datos de la conexión, cada puerto informa de la cantidad de datos que puede controlar, llamada tamaño de la ventana. A medida que se reciben y procesan los datos, el tamaño de esta ventana se ajusta dinámicamente. En TCP, un remitente solo puede enviar una cantidad de datos que quepan en la ventana del receptor. En esencia, el tamaño de la ventana proporciona el control de flujo para la transferencia de datos en cada dirección de la conexión.   

### <a name="tcp-packet-send"></a>Envío de paquetes TCP     
El envío de datos TCP se realiza fácilmente mediante una llamada a la función ***nx_tcp_socket_send***. Si el tamaño de los datos que se van a transmitir es mayor que el valor de MSS del socket o que el tamaño actual de la ventana de recepción del nodo del mismo nivel, lo que sea menor, la lógica interna de TCP divide los datos que caben en min(MSS, ventana de recepción del nodo del mismo nivel) para la transmisión. A continuación, este servicio crea un encabezado TCP delante del paquete (incluido el cálculo de la suma de comprobación). Si el tamaño de la ventana del receptor no es cero, el autor de llamada enviará tantos datos como pueda para llenar el tamaño de la ventana del receptor. Si el tamaño de la ventana de recepción se convierte en cero, el autor de llamada puede suspender y esperar a que el tamaño de la ventana del receptor aumente lo suficiente para que se envíe este paquete. En un momento dado, se pueden suspender varios subprocesos mientras intentan enviar datos mediante el mismo socket. 

> [!WARNING]  
> *Los datos de TCP que residen en la estructura NX_PACKET deben residir en un límite de palabra larga. Además, debe haber espacio suficiente entre el puntero antepuesto y el puntero de inicio de datos para colocar los encabezados del soporte físico, IP y TCP.*

### <a name="tcp-packet-retransmit"></a>Retransmisión de paquetes TCP      
Los paquetes TCP transmitidos previamente enviados realmente se almacenan internamente hasta que se devuelva un mensaje ACK desde el otro lado de la conexión. Si los datos transmitidos no se confirman dentro del período de tiempo de espera, el paquete almacenado se vuelve a enviar y se establece el período de tiempo de espera siguiente. Cuando se recibe un mensaje ACK, finalmente se liberan todos los paquetes que están incluidos en el número de confirmación de la cola de transmisión interna.  

> [!WARNING]   
> *La aplicación no reutilizará el paquete ni modificará su contenido después de que nx_tcp_socket_send() vuelva con NX_SUCCESS. Finalmente, el procesamiento interno de NetX Duo libera el paquete transmitido después de que el otro extremo confirme los datos*.

### <a name="tcp-keepalive"></a>TCP Keepalive     
La característica KeepAlive de TCP permite a un socket detectar si su nodo del mismo nivel se desconecta sin la terminación adecuada (por ejemplo, un nodo bloqueado) o impedir que determinadas funciones de supervisión de red finalicen una conexión durante períodos prolongados de inactividad. KeepAlive de TCP funciona enviando periódicamente un marco TCP sin datos y con el número de secuencia establecido en uno menos que el número de secuencia actual. Al recibir este marco de KeepAlive de TCP, el destinatario, si sigue activo, responde con un mensaje ACK para su número de secuencia actual. Esto completa la transacción de KeepAlive.  

De forma predeterminada, la característica Keepalive no está habilitada. Para usar esta característica, la biblioteca de NetX Duo debe compilarse con ***NX_ENABLE_TCP_KEEPALIVE** _ definido. El símbolo _ *_NX_TCP_KEEPALIVE_INITIAL_** especifica el número de segundos de inactividad antes de que se inicie el marco Keepalive.  

### <a name="tcp-packet-receive"></a>Recepción de paquetes TCP   
El procesamiento de paquetes de recepción TCP (llamado desde el subproceso auxiliar de IP) es responsable de administrar varias acciones de conexión y desconexión, así como de transmitir el procesamiento de confirmación. Además, el procesamiento de paquetes de recepción TCP es responsable de colocar los paquetes con los datos recibidos en la cola de recepción del socket TCP correspondiente o de entregar el paquete al primer subproceso suspendido a la espera de un paquete.

### <a name="tcp-receive-notify"></a>Notificación de recepción de TCP     
Si el subproceso de la aplicación debe procesar los datos recibidos desde más de un socket, se debe usar la función ***nx_tcp_socket_receive_notify***. Esta función registra una función de devolución de llamada de paquetes de recepción para el socket. Cada vez que se recibe un paquete en el socket, se ejecuta la función de devolución de llamada.  

El contenido de la función de devolución de llamada es específico de la aplicación; sin embargo, la función probablemente contendría lógica para informar al subproceso de procesamiento de que está disponible un paquete en el socket correspondiente. 

### <a name="thread-suspension"></a>Suspensión de subprocesos      
Como se ha mencionado anteriormente, los subprocesos de la aplicación se pueden suspender al intentar recibir datos desde un puerto TCP determinado. Una vez que se recibe un paquete en ese puerto, se asigna al primer subproceso suspendido y, a continuación, se reanuda el subproceso. Existe un tiempo de espera opcional disponible cuando hay una suspensión en la recepción de un paquete TCP, una característica disponible para la mayoría de los servicios de NetX Duo.  

La suspensión de subprocesos también está disponible para los servicios de conexión (cliente y servidor), enlace de cliente y desconexión.  

### <a name="tcp-socket-statistics-and-errors"></a>Estadísticas y errores del socket TCP     
Si se habilita, el software de socket TCP de NetX Duo realiza un seguimiento de varios errores y estadísticas que pueden ser útiles para la aplicación. Se mantienen las estadísticas y los informes de errores siguientes para cada instancia de IP/TCP:   

- Número total de paquetes TCP enviados  
- Número total de bytes TCP enviados  
- Número total de paquetes TCP recibidos   
- Número total de bytes TCP recibidos   
- Número total de paquetes TCP no válidos   
- Número total de paquetes de recepción de TCP eliminados    
- Número total de errores de suma de comprobación de recepción de TCP   
- Número total de conexiones TCP   
- Número total de desconexiones TCP   
- Número total de conexiones TCP eliminadas    
- Número total de retransmisiones de paquetes TCP   
- Paquetes de socket TCP enviados   
- Bytes de socket TCP enviados   
- Paquetes de socket TCP recibidos   
- Bytes de socket TCP recibidos   
- Retransmisiones de paquetes de socket TCP    
- Paquetes de socket TCP puestos en cola    
- Errores de suma de comprobación del socket TCP    
- Estado del socket TCP    
- Profundidad de la cola de transmisión del socket TCP    
- Tamaño de la ventana de transmisión del socket TCP    
- Tamaño de la ventana de recepción del socket TCP    

Todas estas estadísticas e informes de errores están disponibles para la aplicación con el servicio ***nx_tcp_info_get** _ para las estadísticas totales de TCP y con el servicio _ *_nx_tcp_socket_info_get_** para las estadísticas de TCP de cada socket.

### <a name="tcp-socket-control-block-nx_tcp_socket"></a>Bloque de control de socket TCP NX_TCP_SOCKET      
Las características de cada socket TCP se encuentran en el bloque de control *NX_TCP_SOCKET* asociado, que contiene información útil, como el vínculo a la estructura de datos IP, la interfaz de la conexión de red, el puerto enlazado y la cola de paquetes de recepción. Esta estructura se define en el archivo ***tx_api.h***.

## <a name="tcpip-offload"></a>Descarga de TCP/IP
Esta característica permite a NetX Duo admitir tarjetas de interfaz de red que ofrecen el servicio TCP/IP en el hardware. Algunos módulos Wi-Fi ofrecen procesamiento TCP/IP en el módulo y las aplicaciones del MCU envían y reciben paquetes mediante las API para acceder a su pila TCP/IP. Con esta característica habilitada, los desarrolladores pueden ejecutar aplicaciones nativas de NetX Duo directamente.

Para habilitar la característica de descarga de TCP/IP, NetX Duo se debe compilar con `NX_ENABLE_TCPIP_OFFLOAD` y `NX_ENABLE_INTERFACE_CAPABILITY` definidos.

### <a name="tcpip-offload-handler"></a>Manipulador de descarga de TCP/IP
NetX Duo se comunica con el controlador de red mediante una función de devolución de llamada para controlar las operaciones de los sockets TCP y UDP. La función de devolución de llamada se define en `NX_INTERFACE_STRUCT`. El controlador de red debe establecer la función de devolución de llamada de TCP/IP durante el comando `NX_LINK_ENABLE` del controlador. El prototipo de función de devolución de llamada de TCP/IP es el siguiente.

``` C
UINT (*nx_interface_tcpip_offload_handler)(struct NX_IP_STRUCT *ip_ptr,
                                           struct NX_INTERFACE_STRUCT *interface_ptr,
                                           VOID *socket_ptr, UINT operation, NX_PACKET *packet_ptr,
                                           NXD_ADDRESS *local_ip, NXD_ADDRESS *remote_ip,
                                           UINT local_port, UINT *remote_port, UINT wait_option);
```
Descripción de los parámetros.
* `ip_ptr`: puntero a la instancia de IP
* `interface_ptr`: puntero a la interfaz
* `socket_ptr`: puntero a `NX_TCP_SOCKET` o `NX_UDP_SOCKET`, en función del valor de `operation`
* `operation`: operación de la llamada de función actual. Los valores se definen como se indica a continuación.
``` C
#define NX_TCPIP_OFFLOAD_TCP_CLIENT_SOCKET_CONNECT  0
#define NX_TCPIP_OFFLOAD_TCP_SERVER_SOCKET_LISTEN   1
#define NX_TCPIP_OFFLOAD_TCP_SERVER_SOCKET_ACCEPT   2
#define NX_TCPIP_OFFLOAD_TCP_SERVER_SOCKET_UNLISTEN 3
#define NX_TCPIP_OFFLOAD_TCP_SOCKET_DISCONNECT      4
#define NX_TCPIP_OFFLOAD_TCP_SOCKET_SEND            5
#define NX_TCPIP_OFFLOAD_UDP_SOCKET_BIND            6
#define NX_TCPIP_OFFLOAD_UDP_SOCKET_UNBIND          7
#define NX_TCPIP_OFFLOAD_UDP_SOCKET_SEND            8
```
* `packet_ptr`: puntero al paquete. El valor se establece cuando `operation` es `TCP_SOCKET_SEND` o `UDP_SOCKET_SEND`.
* `local_ip`: puntero a la dirección IP local. El valor se establece cuando `operation` es `UDP_SOCKET_SEND`.
* `remote_ip`: puntero a la dirección IP remota. El valor se establece cuando `operation` es `TCP_CLIENT_SOCKET_CONNECT` o `UDP_SOCKET_SEND`. Cuando la operación es `TCP_SERVER_SOCKET_ACCEPT`, este valor se debe devolver mediante la función de devolución de llamada.
* `local_port`: puerto local. El valor se establece cuando `operation` es `TCP_CLIENT_SOCKET_CONNECT`, `TCP_SERVER_SOCKET_LISTEN`, `TCP_SERVER_SOCKET_ACCEPT`, `TCP_SERVER_SOCKET_UNLISTEN` o UDP.
* `remote_port`: puerto remoto. El valor se establece cuando `operation` es `TCP_CLIENT_SOCKET_CONNECT` o `UDP_SOCKET_SEND`. Cuando la operación es `TCP_SERVER_SOCKET_ACCEPT`, este valor se debe devolver mediante la función de devolución de llamada.
* `wait_option`: opción de espera expresada en tics. El valor se establece para todas las operaciones.

### <a name="tcpip-offload-context"></a>Contexto de descarga de TCP/IP
Se agrega un puntero a la estructura `NX_TCP_SOCKET` que usará el controlador de descarga de TCP/IP.
```
typedef struct NX_TCP_SOCKET_STRUCT
{
    // ...

    /* This pointer is designed to be accessed by TCP/IP offload directly.  */
    VOID *nx_tcp_socket_tcpip_offload_context;
} NX_TCP_SOCKET;
```

Se agrega un puntero a la estructura `NX_UDP_SOCKET` que usará el controlador de descarga de TCP/IP.
```
typedef struct NX_UDP_SOCKET_STRUCT
{
    // ...

    /* This pointer is designed to be accessed by TCP/IP offload directly.  */
    VOID *nx_udp_socket_tcpip_offload_context;
} NX_UDP_SOCKET;
```

### <a name="apis-for-tcpip-offload-network-driver"></a>API del controlador de red de descarga de TCP/IP
``` C
/* Invoked when TCP packet is receive or connection error.  */
VOID _nx_tcp_socket_driver_packet_receive(NX_TCP_SOCKET *socket_ptr, NX_PACKET *packet_ptr);

/* Invoked when TCP connection is establish.  */
UINT _nx_tcp_socket_driver_establish(NX_TCP_SOCKET *socket_ptr, NX_INTERFACE *interface_ptr, UINT remote_port);

/* Invoked when UDP packet is receive.  */
VOID _nx_udp_socket_driver_packet_receive(NX_UDP_SOCKET *socket_ptr, NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *local_ip, NXD_ADDRESS *remote_ip, UINT remote_port);
```
### <a name="tcpip-offload-driver"></a>Controlador de descarga de TCP/IP
Se necesita una función del controlador para cada interfaz IP. Consulte el [Capítulo 5](chapter5.md#tcpip-offload-driver-guidance) para más detalles sobre cómo desarrollar funciones del controlador de NetX Duo.

### <a name="tcpip-offload-known-limitations"></a>Limitaciones conocidas de la descarga de TCP/IP
- Solo se admiten sockets TCP y UDP.
- Las operaciones de DHCP normalmente se realizan mediante la pila TCP/IP de la capa inferior, no mediante NetX Duo.
- Otras limitaciones de la pila TCP/IP de la capa inferior