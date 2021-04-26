---
title: 'Capítulo 2: instalación y uso de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la pila de red de alto rendimiento de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80d6ba18f47ad2b017dfa32260c83ba074a6dbac
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814478"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx"></a>Capítulo 2: instalación y uso de Azure RTOS NetX

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la pila de red de alto rendimiento de Azure RTOS NetX.

## <a name="host-considerations"></a>Consideraciones sobre el host

El desarrollo integrado se realiza normalmente en equipos host Windows o Linux (Unix). Una vez que la aplicación se compila, se vincula y se genera el archivo ejecutable en el host, se descarga en el hardware de destino para su ejecución.

Normalmente, la descarga de destino se realiza desde el depurador de la herramienta de desarrollo. Después de la descarga, el depurador es responsable de proporcionar el control de ejecución de destino (ir, detener, punto de interrupción, etc.), así como el acceso a los registros de memoria y del procesador.

La mayoría de los depuradores de herramientas de desarrollo se comunican con el hardware de destino mediante conexiones de depuración en chip (OCD), como JTAG (IEEE 1149.1) y el modo de depuración en segundo plano (BDM). Los depuradores también se comunican con el hardware de destino mediante conexiones de emulación en el circuito (ICE). Las conexiones OCD e ICE proporcionan soluciones sólidas con una intrusión mínima en el software residente de destino.

En cuanto a los recursos utilizados en el host, el código fuente de NetX se entrega en formato ASCII y requiere aproximadamente 1 MB de espacio en el disco duro del equipo host.

## <a name="target-considerations"></a>Consideraciones sobre el destino

NetX requiere entre 5 KB y 45 KB de memoria de solo lectura (ROM) en el destino. Se requieren de 1 a 5 KB adicionales de memoria de acceso aleatorio (RAM) del destino para la pila de subprocesos de NetX y otras estructuras de datos globales.

Además, NetX requiere el uso de dos objetos de temporizador y un objeto de exclusión mutua de ThreadX. Estas funciones se utilizan para las necesidades de procesamiento periódico y la protección de subprocesos dentro de la pila del protocolo NetX.

## <a name="product-distribution"></a>Distribución del producto

Azure RTOS NetX se puede obtener desde el repositorio de código fuente público en <https://github.com/azure-rtos/netx/>.

A continuación se muestra una lista de varios archivos importantes del repositorio:

- ***nx_api.h***: archivo de encabezado de C que contiene todas las equivalencias del sistema, las estructuras de datos y los prototipos del servicio.
- ***nx_port.h***: archivo de encabezado de C que contiene todas las definiciones y estructuras de datos específicas de la herramienta de desarrollo y del destino.  
- ***demo_netx.c***: archivo de C que contiene una pequeña aplicación de demostración.
- ***nx.a (o nx.lib)** _: versión binaria de la biblioteca de C de NetX que se distribuye con el _paquete estándar*.             |

## <a name="netx-installation"></a>Instalación de NetX

Puede instalar NetX mediante la clonación del repositorio de GitHub en el equipo local. La siguiente es la sintaxis típica para la creación de un clon del repositorio de NetX en el equipo:

```c
    git clone https://github.com/azure-rtos/netx
```

También puede descargar una copia del repositorio mediante el botón **Descargar** de la página principal de GitHub.

Además, hay instrucciones para compilar la biblioteca de NetX en la página principal del repositorio en línea.

> [!IMPORTANT]
> El software de la aplicación necesita acceso al archivo de biblioteca de NetX (normalmente ***nx.a** _ o _*_nx.lib_*_) y los archivos de inclusión de C _*_nx_api.h y nx_port.h_**. Esto se logra estableciendo la ruta de acceso adecuada para las herramientas de desarrollo o copiando estos archivos en el área de desarrollo de la aplicación.

## <a name="using-netx"></a>Usar NetX

Para usar NetX, el código de la aplicación debe incluir ***nx_api.h** _ durante la compilación y vincular con la biblioteca NetX _*_nx.a_*_ (o _ *_nx.lib_*) *.

Estos son los cuatro pasos necesarios para crear una aplicación de NetX:

1. Incluya el archivo ***nx_api.h*** en todos los archivos de la aplicación que usen servicios o estructuras de datos de NetX.
1. Inicialice el sistema NetX llamando a ***nx_system_initialize** _ desde la función _ *_tx_application_define_** o un subproceso de aplicación.  
1. Cree una instancia de IP, habilite el protocolo de resolución de direcciones (ARP), si es necesario, y los sockets después de que se llame a ***nx_system_initialize***.  
1. Compile el origen de la aplicación y vincúlelo con la biblioteca en tiempo de ejecución de NetX ***nx.a** _ (o _*_nx.lib_**). La imagen resultante se puede descargar en el destino y ejecutarse.

## <a name="troubleshooting"></a>Solución de problemas

Cada puerto de NetX se entrega con uno o varios ejemplos que se ejecutan en una red real o a través de un controlador de red simulado. Siempre es una buena idea conseguir que el sistema de ejemplo se ejecute en primer lugar.

Si el sistema de ejemplo no se ejecuta correctamente, realice las siguientes operaciones para reducir el problema:

1. Determine qué parte del ejemplo se está ejecutando.
2. Aumente los tamaños de pila en cualquier subproceso de aplicación nuevo.
3. Vuelva a compilar la biblioteca NetX con las opciones de depuración apropiadas enumeradas en la sección de la opción de configuración.
4. Examine la estructura de **NX_IP** para ver si los paquetes se envían o se reciben.
5. Examine el grupo de paquetes predeterminado para ver si hay paquetes disponibles.
6. Asegúrese de que el controlador de red está suministrando paquetes ARP e IP con sus encabezados en límites de 4 bytes para aplicaciones que requieren conectividad IP.
7. Omita temporalmente los cambios recientes para ver si el problema desaparece o cambia. Esta información debería resultar útil para los ingenieros de soporte técnico.

Siga los procedimientos descritos en [Centro de atención al cliente](about-this-guide.md) para enviar la información recopilada en los pasos de solución de problemas.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración al compilar la biblioteca de NetX y la aplicación mediante NetX. Las opciones de configuración pueden definirse en el origen de la aplicación, en la línea de comandos, o en el archivo de inclusión ***nx_user.h***, a menos que se especifique lo contrario.

> [!IMPORTANT]
> Las opciones definidas en ***nx_user.h** _ solo se aplican si la aplicación y la biblioteca de NetX se compilan con el elemento _ *NX_INCLUDE_USER_DEFINE_FILE** definido.

En las siguientes secciones se enumeran las opciones de configuración disponibles en NetX.

### <a name="system-configuration-options"></a>Opciones de configuración del sistema  

| Opción  | Descripción  |
|---|---|
| X_DEBUG | Si se define, habilita la información de depuración de impresión opcional disponible en el controlador de red Ethernet de RAM. |
| NX_DISABLE_ERROR_CHECKING | Si se define, quita la API de comprobación de errores básica de NetX y mejora el rendimiento. Los códigos de retorno de API no afectados al deshabilitar la comprobación de errores se muestran en negrita en la definición de la API. Esta definición se utiliza normalmente después de depurar la aplicación y cuando su uso mejora el rendimiento y reduce el tamaño del código. |
| NX_DRIVER_DEFERRED_PROCESSING | Si se define, habilita el control diferido de paquetes de controladores de red. Esto permite que el controlador de red coloque un paquete en la instancia de IP y que se llame a la rutina de procesamiento real desde el subproceso de aplicación auxiliar de IP interna de NetX. |
| NX_ENABLE_EXTENDED_NOTIFY_SUPPORT | Habilita más enlaces de devolución de llamada en la pila. Estas funciones de devolución de llamada las utiliza la capa de contenedor de BSD. De manera predeterminada, esta opción no está definida. |
| NX_ENABLE_SOURCE_ADDRESS_CHECK | Si se define, habilita la dirección de origen del paquete entrante que se va a comprobar. Esta opción está deshabilitada de manera predeterminada. |
| NX_LITTLE_ENDIAN | Si se define, realiza el intercambio de bytes necesario en los entornos de little endian para asegurarse de que los encabezados de protocolo se encuentran en un formato de big endian adecuado. Tenga en cuenta que el valor predeterminado normalmente se configura en ***nx_port.h***. |
| NX_MAX_PHYSICAL_INTERFACES | Especifica el número total de interfaces de red físicas en el dispositivo. El valor predeterminado es 1 y se define en ***nx_api.h***. Un dispositivo debe tener al menos una interfaz física. Tenga en cuenta que no incluye la interfaz de bucle invertido. |
| NX_PHYSICAL_HEADER | Especifica el tamaño en bytes del encabezado físico del marco. El valor predeterminado es 16 (basado en un marco Ethernet típico de 14 bytes alineado con el límite de 32 bits) y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _*_nx_api.h_*_, como en _ *_nx_user.h_*.* |

### <a name="arp-configuration-options"></a>Opciones de configuración de ARP  

| Opción  | Descripción  |
|---|---|
| NX_ARP_DEFEND_BY_REPLY | Si se define, permite a NetX defender su dirección IP mediante el envío de una respuesta ARP. |
| NX_ARP_DEFEND_INTERVAL | Define el intervalo, en segundos, el módulo ARP envía el siguiente paquete de defensa en respuesta a un mensaje ARP entrante que indica una dirección en conflicto. |
| NX_ARP_DISABLE_AUTO_ARP_ENTRY | Se ha cambiado el nombre a **NX_DISABLE_ARP_AUTO_ENTRY**. Aunque todavía se admite, se recomienda que los nuevos diseños utilicen **NX_DISABLE_ARP_AUTO_ENTRY**.
| NX_ARP_EXPIRATION_RATE | Especifica el número de segundos durante los que las entradas ARP siguen siendo válidas. El valor predeterminado cero deshabilita la expiración o el vencimiento de las entradas ARP y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir *_nx_api.h_**.
| NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Se ha cambiado el nombre a **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. Aunque todavía se admite, se recomienda que los nuevos diseños utilicen **NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION**. |
| NX_ARP_MAX_QUEUE_DEPTH | Especifica el número máximo de paquetes que se pueden poner en cola mientras se espera una respuesta ARP. El valor predeterminado es 4 y se define en ***nx_api.h***. |
| NX_ARP_MAXIMUM_RETRIES | Especifica el número máximo de reintentos de ARP realizados sin una respuesta ARP. El valor predeterminado es 18 y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _*_nx_api.h_**. |
| NX_ARP_UPDATE_RATE | Especifica el número de segundos entre los reintentos de ARP. El valor predeterminado es 10, que representa 10 segundos, y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _*_nx_api.h_**. |
| NX_DISABLE_ARP_AUTO_ENTRY | Si se define, deshabilita la entrada de información de solicitud ARP en la caché ARP. |
| NX_DISABLE_ARP_INFO | Si se define, deshabilita la recopilación de información ARP. |
| NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION | Si se define, permite que ARP invoque una función de notificación de devolución de llamada al detectar que se ha actualizado la dirección MAC. |

### <a name="icmp-configuration-options"></a>Opciones de configuración de ICMP  

| Opción  | Descripción  |
|---|---|
| NX_DISABLE_ICMP_INFO | Si se define, deshabilita la recopilación de información ICMP. |
| NX_DISABLE_ICMP_RX_CHECKSUM | Deshabilita el cálculo de la suma de comprobación ICMP en los paquetes ICMP recibidos. Esta opción es útil cuando el controlador de interfaz de red puede comprobar la suma de comprobación de ICMP y la aplicación no usa la característica de fragmentación de IP. De manera predeterminada, esta opción no está definida. |
| NX_DISABLE_ICMP_TX_CHECKSUM | Deshabilita el cálculo de suma de comprobación ICMP en los paquetes ICMP transmitidos. Esta opción es útil donde el controlador de interfaz de red puede calcular la suma de comprobación de ICMP y la aplicación no usa la característica de fragmentación de IP. De manera predeterminada, esta opción no está definida. |

### <a name="igmp-configuration-options"></a>Opciones de configuración de IGMP  

| Opción  | Descripción  |
|---|---| 
| NX_DISABLE_IGMP_INFO | Si se define, deshabilita la recopilación de información IGMP. |
| NX_DISABLE_IGMPV2 | Si se define, deshabilita la compatibilidad con IGMPv2 y NetX solo admite IGMPv1. De forma predeterminada, esta opción no está establecida y se define en ***nx_api.h***. |
| NX_MAX_MULTICAST_GROUPS | Especifica el número máximo de grupos de multidifusión que se pueden combinar. El valor predeterminado es 7 y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir *_nx_api.h_**. |

### <a name="ip-configuration-options"></a>Opciones de configuración de IP

| Opción  | Descripción  |
|---|---|
| NX_DISABLE_FRAGMENTATION | Si se define, deshabilita la lógica de fragmentación y reensamblado de IP. |
| NX_DISABLE_IP_INFO | Si se define, deshabilita la recopilación de información de IP. |
| NX_DISABLE_IP_RX_CHECKSUM | Si se define, deshabilita la lógica de la suma de comprobación en los paquetes IP recibidos. Esto resulta útil si el dispositivo de red puede comprobar la suma de comprobación del encabezado IP y la aplicación no utiliza la fragmentación de IP. |
| NX_DISABLE_IP_TX_CHECKSUM | Si se define, deshabilita la lógica de la suma de comprobación en los paquetes IP enviados. Esto resulta útil en situaciones en las que el dispositivo de red subyacente es capaz de generar la suma de comprobación del encabezado IP y la aplicación no utiliza la fragmentación de IP. |
| NX_DISABLE_LOOPBACK_INTERFACE | Si se define, deshabilita la compatibilidad de NetX con la interfaz de bucle invertido. |
| NX_DISABLE_RX_SIZE_CHECKING | Si se define, deshabilita la comprobación de tamaño de los paquetes recibidos. |
| NX_ENABLE_IP_STATIC_ROUTING | Si se define, habilita el enrutamiento estático IP en el que una dirección de destino puede tener asignada una dirección de próximo salto específica. De forma predeterminada, el enrutamiento estático IP está deshabilitado. |
| NX_IP_PERIODIC_RATE | Si se define, especifica el número de tics de temporizador de ThreadX en un segundo. El valor predeterminado se deriva del símbolo de ThreadX **TX_TIMER_TICKS_PER_SECOND,** que de forma predeterminada se establece en 100 (temporizador de 10 ms). Las aplicaciones deben tener cuidado al modificar este valor, ya que el resto de los módulos de NetX derivan información de tiempo de **NX_IP_PERIODIC_RATE*.** |
| NX_IP_ROUTING_TABLE_SIZE | Si se define, establece el número máximo de entradas en la tabla de enrutamiento estático de IP, que es una lista de una interfaz de salida y el próximo salto
direcciones para una dirección de destino determinada. El valor predeterminado es 8 y se define en ***nx_api.h.** _ Este símbolo se usa solo si se define _ *NX_ENABLE_IP_STATIC_ROUTING**. |

### <a name="packet-configuration-options"></a>Opciones de configuración de paquetes  

| Opción  | Descripción  |
|---|---|
| NX_DISABLE_PACKET_INFO | Si se define, deshabilita la recopilación de información del grupo de paquetes. | 
| NX_PACKET_HEADER_PAD | Si se define, habilita el relleno hacia el final del bloque de control NX_PACKET. El número de palabras de **ULONG** que se van a rellenar se define mediante **NX_PACKET_HEADER_PAD_SIZE**. |
| NX_PACKET_HEADER_PAD_SIZE | Establece el número de palabras de **ULONG** que se van a rellenar en la estructura de NX_PACKET, lo que permite que el área de carga de paquetes se inicie en la
alineación deseada. Esta característica es útil cuando los descriptores de búfer de recepción apuntan directamente al área de carga útil de NX_PACKET y la lógica de recepción de la interfaz de red o la lógica de la operación de caché espera que la dirección de inicio del búfer cumpla ciertos requisitos de alineación. Este valor solo es válido cuando se define **NX_PACKET_HEADER_PAD**. |

### <a name="rarp-configuration-options"></a>Opciones de configuración de RARP  

| Opción  | Descripción  |
|---|---|
| NX_DISABLE_RARP_INFO | Si se define, deshabilita la recopilación de información RARP. |

### <a name="tcp-configuration-options"></a>Opciones de configuración de TCP

| Opción  | Descripción  |
|---|---|
| NX_DISABLE_RESET_DISCONNECT | Si se define, deshabilita el procesamiento de restablecimiento durante la desconexión cuando el valor de tiempo de espera proporcionado se especifica como **NX_NO_WAIT**. |
| NX_DISABLE_TCP_INFO | Si se define, deshabilita la recopilación de información TCP. |
| NX_DISABLE_TCP_RX_CHECKSUM | Si se define, deshabilita la lógica de la suma de comprobación en los paquetes TCP recibidos. Esto solo es útil en situaciones en las que la capa de vínculo tiene un procesamiento de suma de comprobación o CRC confiables o el controlador de interfaz puede comprobar la suma de comprobación TCP en el hardware. |
| NX_DISABLE_TCP_TX_CHECKSUM | Si se define, deshabilita la lógica de suma de comprobación para enviar paquetes TCP. Esto solo es útil en situaciones en las que el nodo de red receptor tiene deshabilitada la lógica de suma de comprobación TCP recibida o el controlador de red subyacente es capaz de generar la suma de comprobación TCP. |
| NX_ENABLE_TCP_KEEPALIVE | Si se define, habilita el temporizador de Keepalive TCP opcional. La configuración predeterminada no está habilitada. |
| NX_ENABLE_TCP_MSS_CHECKING | Si se define, habilita la comprobación del MSS del mismo nivel mínima antes de aceptar una conexión TCP. Para usar esta característica, debe definirse el símbolo **NX_ENABLE_TCP_MSS_MINIMUM**. De forma predeterminada, esta opción está activada. |
NX_ENABLE_TCP_WINDOW_SCALING | Habilita la opción de escalado de ventana para las aplicaciones TCP. Si se define, la opción de escalado de la ventana se negocia durante la fase de conexión TCP y la aplicación puede especificar un tamaño de ventana superior a 64 K. La configuración predeterminada no está habilitada (no está definida). |
| NX_MAX_LISTEN_REQUESTS | Especifica el número máximo de solicitudes de escucha del servidor. El valor predeterminado es 10 y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir *_nx_api.h_**. |
| NX_TCP_ACK_EVERY_N_PACKETS | Especifica el número de paquetes TCP que se van a recibir antes de enviar una confirmación. Nota: Si **NX_TCP_IMMEDIATE_ACK** está habilitado, pero **NX_TCP_ACK_EVERY_N_PACKETS** no, este valor se establece automáticamente en 1 para la compatibilidad con versiones anteriores. |
| NX_TCP_ACK_TIMER_RATE | Especifica cómo se divide el número de tics del sistema (NX_IP_PERIODIC_RATE) para calcular la velocidad del temporizador para el procesamiento de confirmación diferida de TCP. El valor predeterminado es 5, que representa 200 ms, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _*_nx_api.h_**. |
| NX_TCP_ENABLE_KEEPALIVE | Se ha cambiado el nombre a **NX_ENABLE_TCP_KEEPALIVE**. Aunque todavía se admite, se recomienda que los nuevos diseños usen **NX_ENABLE_TCP_KEEPALIVE**. |
| NX_TCP_ENABLE_WINDOW_SCALING | Se ha cambiado el nombre a **NX_ENABLE_TCP_WINDOW_SCALING**. Aunque todavía se admite, se recomienda que los nuevos diseños usen **NX_ENABLE_TCP_WINDOW_SCALING**. |
| NX_TCP_FAST_TIMER_RATE | Especifica cómo se divide el número de tics internos de NetX (NX_IP_PERIODIC_RATE) para calcular la velocidad del temporizador de TCP rápido. El temporizador de TCP rápido se utiliza para controlar los distintos temporizadores de TCP, incluido el temporizador de confirmación retrasada. El valor predeterminado es 10, que representa 100 ms suponiendo que el temporizador de ThreadX se esté ejecutando a 10 ms. Este valor se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _*_nx_api.h_**. |
| NX_TCP_IMMEDIATE_ACK | Si se define, habilita el procesamiento de respuesta de confirmación inmediata de TCP opcional. Definir de este símbolo equivale a definir **NX_TCP_ACK_EVERY_N_PACKETS** como 1. |
| NX_TCP_KEEPALIVE_INITIAL | Especifica el número de segundos de inactividad antes de que se active el temporizador de Keepalive. El valor predeterminado es 7200, que representa 2 horas, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _*_nx_api.h_**. |
| NX_TCP_KEEPALIVE_RETRIES | Especifica cuántos reintentos Keepalive se permiten antes de que la conexión se considere interrumpida. El valor predeterminado es 10, que representa 10 reintentos, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir *_nx_api.h_**. |
| NX_TCP_KEEPALIVE_RETRY | Especifica el número de segundos entre los reintentos del temporizador de Keepalive, suponiendo que el otro lado de la conexión no responde. El valor predeterminado es 75, que representa 75 segundos entre reintentos, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir *_nx_api.h_**. |
| NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Símbolo que define el número máximo de paquetes TCP no disponibles que se pueden mantener en la cola de recepción de sockets TCP. Este símbolo se puede usar para limitar el número de paquetes en cola en el socket de recepción TCP, lo que impide que se agote el grupo de paquetes. De forma predeterminada, este símbolo no está definido, por lo que no hay ningún límite en el número de paquetes no disponibles en cola en el socket TCP. |
| NX_TCP_MAXIMUM_RETRIES | Especifica cuántos reintentos de transmisión de datos se permiten antes de que la conexión se considere interrumpida. El valor predeterminado es 10, que representa 10 reintentos, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _*_nx_api.h_**. |
| NX_TCP_MAXIMUM_TX_QUEUE | Especifica la profundidad máxima de la cola de transmisión de TCP antes de que se suspendan o se rechacen las solicitudes de envío TCP. El valor predeterminado es 20, lo que significa que puede haber un máximo de 20 paquetes en la cola de transmisión en un momento dado. Nota: Los paquetes permanecen en la cola de transmisión hasta que se reciba una confirmación que abarque algunos o todos los datos del paquete desde el otro lado de la conexión. Esta constante se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _*_nx_api.h_**. |
| X_TCP_MSS_CHECKING_ENABLED | Se ha cambiado el nombre a **NX_ENABLE_TCP_MSS_CHECKING**. Aunque todavía se admite, se recomienda que los nuevos diseños utilicen **NX_ENABLE_TCP_MSS_CHECKING**. |
| NX_TCP_MSS_MINIMUM | Símbolo que define el valor mínimo de MSS que el módulo TCP de NetX acepta. Esta característica está habilitada por **NX_ENABLE_TCP_MSS_CHECK** |
| NX_TCP_RETRY_SHIFT | Especifica cómo cambia el período de tiempo de espera de retransmisión entre los reintentos. Si este valor es 0, el tiempo de espera de retransmisión inicial es el mismo que el de los tiempos de espera de retransmisión subsiguientes. Si este valor es 1, cada retransmisión sucesiva es dos veces más larga. Si este valor es 2, cada tiempo de espera de retransmisión subsiguiente es cuatro veces mayor. El valor predeterminado es 0 y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _*_nx_api.h_**. |
| NX_TCP_TRANSMIT_TIMER_RATE| Especifica cómo se divide el número de tics del sistema (**NX_IP_PERIODIC_RATE**) para calcular la velocidad del temporizador para el procesamiento de reintentos de transmisión de TCP. El valor predeterminado es 1, que representa un segundo, y se define en **_nx_tcp.h_ *_. La aplicación puede invalidar el valor predeterminado definiendo el valor antes de incluir _* _nx_api.h_**. |

### <a name="udp-configuration-options"></a>Opciones de configuración de UDP
| Opción  | Descripción  |
|---|---|
| NX_DISABLE_UDP_INFO | Si se define, deshabilita la recopilación de información UCP. |
| NX_DISABLE_UDP_RX_CHECKSUM | Si se define, deshabilita el cálculo de la suma de comprobación UDP en los paquetes UDP entrantes. Esto resulta útil si el controlador de la interfaz de red puede comprobar la suma de comprobación del encabezado UDP en el hardware y la aplicación no habilita la lógica de fragmentación de IP. |
| NX_DISABLE_UDP_TX_CHECKSUM | Si se define, deshabilita el cálculo de la suma de comprobación UDP en los paquetes UDP salientes. Esto resulta útil si el controlador de la interfaz de red puede calcular la suma de comprobación del encabezado UDP e insertar el valor en el encabezado IP antes de transmitir los datos y la aplicación no habilita la lógica de fragmentación de IP. |

## <a name="netx-version-id"></a>Id. de la versión de NetX

La versión actual de NetX está disponible tanto para el software de usuario como para el de la aplicación durante el tiempo de ejecución. El programador puede obtener la versión de NetX del archivo **nx_port.h**. Además, este archivo contiene un historial de versiones del puerto correspondiente. El software de la aplicación puede obtener la versión de NetX mediante el examen de la cadena global **_nx_version_id** en **_nx_port.h_**.  

El software de la aplicación también puede obtener información de la versión de las constantes que se muestran a continuación, que se definen en ***nx_api.h***.

Estas constantes identifican la versión actual del producto por nombre y la versión principal y secundaria del producto.

```c
#define EL_PRODUCT_NETX

#define NETX_MAJOR_VERSION

#define NETX_MINOR_VERSION
```