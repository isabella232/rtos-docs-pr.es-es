---
title: 'Capítulo 2: Instalación y uso de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la pila de red de alto rendimiento de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 457eca2144bb0cba7cae63aa007e9cb658bbcd96
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815406"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo"></a>Capítulo 2: Instalación y uso de Azure RTOS NetX Duo

Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso de la pila de red de alto rendimiento de Azure RTOS NetX Duo, entre los que se incluyen: 

## <a name="host-considerations"></a>Consideraciones sobre el host

El desarrollo insertado normalmente se realiza en equipos host Windows o Linux (Unix). Después de que la aplicación se compila y se vincula, y de que el archivo ejecutable se genera en el host, se descarga en el hardware de destino para su ejecución.

Normalmente, la descarga del destino se realiza desde el depurador de la herramienta de desarrollo. Después de la descarga, el depurador es responsable de proporcionar el control de ejecución de destino (ir, detener, punto de interrupción, etc.), así como del acceso a los registros de memoria y del procesador.

La mayor parte de los depuradores de herramientas de desarrollo se comunican con el hardware de destino mediante conexiones de depuración en chip (OCD), como JTAG (IEEE 1149.1) y el modo de depuración en segundo plano (BDM). Los depuradores también se comunican con el hardware de destino mediante conexiones de emulación en el circuito (ICE). Las conexiones OCD e ICE proporcionan soluciones sólidas con una intrusión mínima en el software residente de destino.

En cuanto a los recursos utilizados en el host, el código fuente de NetX Duo se entrega en formato ASCII y requiere aproximadamente 1 MB de espacio en el disco duro del equipo host.

## <a name="target-considerations"></a>Consideraciones sobre el destino

NetX Duo requiere entre 5 y 45 KB de memoria de solo lectura (ROM) en el destino. Se requieren de 1 a 5 KB adicionales de memoria de acceso aleatorio (RAM) del destino para la pila de subprocesos de NetX Duo y otras estructuras de datos globales.

Además, NetX Duo requiere el uso tanto de dos objetos de temporizador de ThreadX como de un objeto de exclusión mutua de ThreadX. Estas funciones se utilizan para las necesidades periódicas de procesamiento y la protección de subprocesos en la pila del protocolo NetX Duo.

## <a name="product-distribution"></a>Distribución del producto

Azure RTOS NetX Duo se puede obtener en nuestro repositorio de código fuente público, en <https://github.com/azure-rtos/netxduo/>.

A continuación se muestra una lista de varios archivos importantes del repositorio:

**nx_api.h**  
Archivo de encabezado de C que contiene todas las equivalencias del sistema, las estructuras de datos y los prototipos del servicio.

**nx_port.h** Archivo de encabezado de C que contiene todas las definiciones y estructuras de datos específicos de la herramienta de desarrollo y del destino. 

**demo_netx.c** Archivo de C que contiene una pequeña aplicación de demostración.

**nx.a (onx.lib)**  
Versión binaria de la biblioteca de C de NetX que se distribuye con el paquete estándar.

## <a name="netx-duo-installation"></a>Instalación de NetX Duo

NetX Duo se instala mediante la clonación del repositorio de GitHub en el equipo local. La siguiente es la sintaxis típica para la creación de un clon del repositorio de NetX Duo en un equipo:

```c
    git clone https://github.com/azure-rtos/netxduo
```

También se puede descargar una copia del repositorio mediante el botón Descargar de la página principal de GitHub.

Además, hay instrucciones para compilar la biblioteca de NetX Duo en la página principal del repositorio en línea.

> [!IMPORTANT]
> *El software de aplicación necesita acceso al archivo de biblioteca de NetX Duo (normalmente, **nx.a** o **nx.lib**) y a los archivos de inclusión de C **nx_api. h y nx_port. h**, y para ello hay que establecer la ruta de acceso adecuada para las herramientas de desarrollo o copiar estos archivos en el área desarrollo de aplicaciones.*

## <a name="using-netx-duo"></a>Uso de NetX Duo

NetX Duo es fácil de usar. Para usar NetX, el código de la aplicación debe incluir ***nx_api. h** _ durante la compilación y vincular con la biblioteca de NetX Duo _*_nx.a_*_ (o _ *_nx.lib_*)*.

A continuación, se muestran los cuatro sencillos pasos necesarios para compilar una aplicación de NetX Duo:

[!div class="mx-tdCol2BreakAll"]
| Paso  | Descripción  |
|---|---|
|Paso&nbsp;1: |Incluya el archivo ***nx_api.h*** en todos los archivos de la aplicación que usen servicios o estructuras de datos de NetX Duo.|
|Paso&nbsp;2: |Inicialice el sistema NetX, para lo que debe llamar a ***nx_system_initialize** _ desde la función _ *_tx_application_define_** o desde un subproceso de la aplicación.|
|Paso&nbsp;3: |Cree una instancia de IP, habilite el protocolo de resolución de direcciones (ARP), si fuera, y los sockets después de que se llame a ***nx_system_initialize***.|
|Paso&nbsp;4: |Compile el origen de la aplicación y vincúlelo con la biblioteca en tiempo de ejecución de NetX Duo ***nx.a** _ (o _*_nx.lib_**). La imagen resultante puede descargarse en el destino y ejecutarse.|

## <a name="troubleshooting"></a>Solución de problemas

Cada distribución de NetX Duo se entrega con una o varias demostraciones que se ejecutan en una red real o a través de un controlador de red simulado. Habitualmente es conveniente que primero se ejecute el sistema de demostración.

Si el sistema de demostración no se ejecuta correctamente, realice las siguientes operaciones para reducir el problema:

1. Determine qué parte de la demostración se está ejecutando.
2. Aumente los tamaños de la pila en los subproceso de la aplicación nuevos.
3. Vuelva a compilar la biblioteca NetX Duo con las opciones de depuración apropiadas enumeradas en la sección de la opción de configuración.
4. Examine la estructura de NX_IP para ver si se envían o reciben paquetes.
5. Examine el grupo de paquetes predeterminado para ver si hay paquetes disponibles.
6. Asegúrese de que el controlador de red está suministrando paquetes ARP e IP con sus encabezados en los límites de 4 bytes para aplicaciones que requieren conectividad IPv4 o IPv6.
7. Omita temporalmente los cambios recientes para ver si el problema desaparece o cambia. Esta información debería resultar útil para los ingenieros de soporte técnico de Microsoft.

Siga los procedimientos descritos en la sección "Qué necesitamos de usted", en la página 12, para enviar la información recopilada en los pasos de solución de problemas.

## <a name="configuration-options"></a>Opciones de configuración

Cuando se compila la biblioteca de NetX Duo y la aplicación que usa NetX Duo hay varias opciones de configuración. Las opciones de configuración se pueden definir en el origen de la aplicación, en la línea de comandos, o en el archivo de inclusión ***nx_user.h***, salvo que se especifique lo contrario.

> [!NOTE]
> *Las opciones definidas en **nx_user.h** solo se aplican si la aplicación y la biblioteca de NetX Duo se compilan con el elemento* **_NX_INCLUDE_USER_DEFINE_FILE** definido.*

En las siguientes secciones se enumeran las opciones de configuración disponibles en NetX Duo. En primer lugar aparecen las opciones generales aplicables a IPv4 e IPv6 y, después, las opciones específicas de IPv6.

### <a name="system-configuration-options"></a>Opciones de configuración del sistema

| Opción  | Descripción  |
|---|---|
| NX_ASSERT_FAIL    | Símbolo que define la instrucción de depuración que se va a utilizar cuando se produce un error en una aserción.                               |
| NX_DEBUG           | Si se define, habilita la información de depuración de impresión opcional disponible en el controlador de red Ethernet de RAM. |
| NX_DEBUG_PACKET   | Si se define, habilita el volcado de paquetes de depuración opcional disponible en el controlador de red Ethernet de RAM.      |
| NX_DISABLE_ASSERT | Si se define, deshabilita las comprobaciones de ASSERT en el código fuente. De manera predeterminada, esta opción no se define.            |
|NX_DISABLE_ERROR_CHECKING | Si se define, quita la API de comprobación de errores básica de NetX Duo y mejora el rendimiento. Los códigos de retorno de API que no resultan afectados al deshabilitar la comprobación de errores se muestran en negrita en la definición de la API. Esta definición se utiliza normalmente después de que la aplicación se haya depurado suficientemente y su uso mejora el rendimiento y reduce el tamaño del código.|
|NX_DRIVER_DEFERRED_PROCESSING | Si se define, habilita el control diferido de paquetes de controladores de red. Esto permite que el controlador de red coloque un paquete en la instancia de IP y que se llame a la rutina de procesamiento real desde el subproceso de aplicación auxiliar de IP interna de NetX Duo.|
|NX_DUAL_PACKET_POOL_ENABLE | Se ha cambiado el nombre a ***NX_ENABLE_DUAL_PACKET_POOL** _. Aunque todavía se admite, se recomienda que los nuevos diseños utilicen _*_NX_ENABLE_DUAL_PACKET_POOL_**.|
|NX_ENABLE_DUAL_PACKET_POOL | Si se define, permite que la pila use dos grupos de paquetes, uno con tamaño de carga grande y otro con un tamaño de carga más pequeño. De forma predeterminada, esta opción no está habilitada.|
|NX_ENABLE_EXTENDED_NOTIFY_SUPPORT| Si se define, habilita más enlaces de devolución de llamada en la pila. Estas funciones de devolución de llamada las utiliza la capa del contenedor de BSD. De manera predeterminada, esta opción no se define.|
|NX_ENABLE_INTERFACE_CAPABILITY| Si se define, permite al controlador de dispositivo de la interfaz especificar información adicional acerca de la funcionalidad, como la descarga de la suma de comprobación. De manera predeterminada, esta opción no se define.|
|NX_ENABLE_SOURCE_ADDRESS_CHECK| Si se define, habilita la dirección de origen del paquete entrante que se va a comprobar. Esta opción está deshabilitada de manera predeterminada.|
| NX_IPSEC_ENABLE  | Si se define, habilita la biblioteca de NetX Duo para que admita operaciones de IPsec. Esta característica requiere el módulo IPsec de NetX Duo opcional. De forma predeterminada, esta característica no está habilitada.            |
| NX_LITTLE_ENDIAN | Si se define, realiza el intercambio de bytes necesario en los entornos de little endian para asegurarse de que los encabezados de protocolo se encuentran en el formato de big endian adecuado. Tenga en cuenta que el valor predeterminado normalmente se configura en ***nx_port.h***.|
|NX_MAX_PHYSICAL_INTERFACES | Especifica el número total de interfaces de red físicas que hay en el dispositivo. El valor predeterminado es 1 y se define en ***nx_api.h***; un dispositivo debe tener al menos una interfaz física. Tenga en cuenta que aquí no se incluye la interfaz de bucle invertido.|
| NX_NAT_ENABLE | Si se define, NetX Duo se crea con el proceso de NAT. De manera predeterminada, esta opción no se define.|
| NX_PHYSICAL_HEADER  | Especifica el tamaño, en bytes, del encabezado físico del marco. El valor predeterminado es 16 (basado en un marco Ethernet típico de 14 bytes alineado con un límite de 32 bits) y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _*_nx_api.h_*_, como en _ *_nx_user.h_*.* |
| NX_PHYSICAL_TRAILER | Especifica el tamaño, en bytes, del finalizador de paquetes físico y normalmente se utiliza para reservar almacenamiento para elementos como CRC de Ethernet, etc. El valor predeterminado es 4 y se define en ***nx_api.h***.|

### <a name="arp-configuration-options"></a>Opciones de configuración de ARP

| Opción  | Descripción  |
|---|---|
|NX_ARP_DEFEND_BY_REPLY | Si se define, permite a NetX Duo defender su dirección IP mediante el envío de una respuesta ARP.|
|NX_ARP_DEFEND_INTERVAL| Define el intervalo, en segundos, en que el módulo ARP envía el siguiente paquete de defensa en respuesta a un mensaje ARP entrante que indica que hay una dirección en conflicto.|
|NX_ARP_DISABLE_AUTO_ARP_ENTRY|  Se ha cambiado el nombre a ***NX_DISABLE_ARP_AUTO_ENTRY** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_ARP_AUTO_ENTRY_**.|
|NX_ARP_EXPIRATION_RATE| Especifica el número de segundos durante los que las entradas ARP son válidas. El valor predeterminado es cero y deshabilita la expiración o el vencimiento de las entradas ARP y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de incluir *_nx_api.h_**.|
|NX_ARP_MAC_CHANGE_NOTIFICATION_ENABLE | Se ha cambiado el nombre a ***NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION_**.|
|NX_ARP_MAX_QUEUE_DEPTH | Especifica el número máximo de paquetes que se pueden poner en cola mientras se espera una respuesta ARP. El valor predeterminado es 4 y se define en ***nx_api.h***.|
|NX_ARP_MAXIMUM_RETRIES | Especifica el número máximo de reintentos de ARP que se pueden realizar sin una respuesta ARP. El valor predeterminado es 18 y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de incluir *_nx_api.h_**.|
|NX_ARP_UPDATE_RATE | Especifica el número de segundos que pueden transcurrir entre reintentos de ARP. El valor predeterminado es 10, que representa 10 segundos, y se define en ***nx_api. h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_DISABLE_ARP_AUTO_ENTRY | Si se define, deshabilita la entrada de información de solicitud ARP en la caché de ARP.|
|NX_DISABLE_ARP_INFO | Si se define, deshabilita la recopilación de información de ARP.|
|NX_ENABLE_ARP_MAC_CHANGE_NOTIFICATION| Si se define, permite que ARP invoque una función de notificación de devolución de llamada al detectar que la dirección MAC se ha actualizado.|

### <a name="icmp-configuration-options"></a>Opciones de configuración de ICMP

| Opción  | Descripción  |
|---|---|
|NX_DISABLE_ICMP_INFO| Si se define, deshabilita la recopilación de información de ICMP.|
|NX_DISABLE_ICMP_RX_CHECKSUM| Si se define, deshabilita el cálculo de la suma de comprobación de ICMPv4 e ICMPv6 en los paquetes ICMP recibidos. Esta opción es útil cuando el controlador de la interfaz de red puede comprobar la suma de comprobación de ICMPv4 e ICMPv6, y la aplicación no usa la característica de fragmentación de IP ni la característica de IPsec. De manera predeterminada, esta opción no se define.|
|NX_DISABLE_ICMP_TX_CHECKSUM | Si se define, deshabilita el cálculo de la suma de comprobación de ICMPv4 e ICMPv6 en los paquetes ICMP transmitidos. Esta opción es útil cuando el controlador de la interfaz de red puede calcular la suma de comprobación de ICMPv4 y ICMPv6,
y la aplicación no utiliza la característica de fragmentación de IP ni la característica de IPsec. De manera predeterminada, esta opción no se define.|
|NX_DISABLE_ICMPV4_ERROR_MESSAGE | Si se define, NetX Duo no envía mensajes de error de ICMPv4 en respuesta a condiciones de error como el encabezado IPv4 con formato incorrecto. De manera predeterminada, esta opción no se define.|
|NX_DISABLE_ICMPV4_RX_CHECKSUM | Si se define, deshabilita el cálculo de la suma de comprobación de ICMPv4 en los paquetes ICMP recibidos. Esta opción se define automáticamente si se define ***NX_DISABLE_ICMP_RX_CHECKSUM***. De manera predeterminada, esta opción no se define.|
|NX_DISABLE_ICMPv4_RX_CHECKSUM | Se ha cambiado el nombre a ***NX_DISABLE_ICMPV4_RX_CHECKSUM** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_ICMPV4_RX_CHECKSUM_**.|
|NX_DISABLE_ICMPV4_TX_CHECKSUM | Si se define, deshabilita el cálculo de la suma de comprobación de ICMPv4 en los paquetes ICMP transmitidos. Esta opción se define automáticamente si se define ***NX_DISABLE_ICMP_TX_CHECKSUM***. De manera predeterminada, esta opción no se define.|
|NX_DISABLE_ICMPv4_TX_CHECKSUM | Se ha cambiado el nombre a ***NX_DISABLE_ICMPV4_TX_CHECKSUM** _.</br>Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_ICMPV4_TX_CHECKSUM_**.|
|NX_ENABLE_ICMP_ADDRESS_CHECK | Si se define, se comprueba la dirección de destino del paquete ICMP. El valor predeterminado es deshabilitado. Una solicitud de eco ICMP destinada a una dirección de difusión IP o de multidifusión IP se descartará de forma silenciosa.|

### <a name="igmp-configuration-options"></a>Opciones de configuración de IGMP

| Opción  | Descripción  |
|---|---|
|NX_DISABLE_IGMP_INFO | Si se define, deshabilita la recopilación de información de IGMP.|
|NX_DISABLE_IGMPV2 | Si se define, deshabilita la compatibilidad con IGMPv2 y NetX Duo solo admite IGMPv1. De forma predeterminada, esta opción no está establecida y se define en ***nx_api.h***.|
|NX_MAX_MULTICAST_GROUPS | Especifica el número máximo de grupos de multidifusión que se pueden combinar. El valor predeterminado es 7 y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|

### <a name="ip-configuration-options"></a>Opciones de configuración de IP

| Opción  | Descripción  |
|---|---|
|NX_DISABLE_FRAGMENTATION | Si se define, deshabilita la fragmentación tanto de IPv4 como IPv6 y la lógica de reensamblado.|
| NX_DISABLE_IPV4     | Si se define, deshabilita la funcionalidad de IPv4. Esta opción se puede usar para que NetX Duo solo admita IPv6. De manera predeterminada, esta opción no se define. |
| NX_DISABLE_IP_INFO | Si se define, deshabilita la recopilación de información de IGMP.|
|NX_DISABLE_IP_RX_CHECKSUM | Si se define, deshabilita la lógica de la suma de comprobación en los paquetes IPv4 recibidos. Esto resulta útil si el dispositivo de red puede comprobar la suma de comprobación de IPv4 y la aplicación no espera usar la fragmentación de IP o IPsec.|
|NX_DISABLE_IP_TX_CHECKSUM | Si se define, deshabilita la lógica de la suma de comprobación en los paquetes IPv4 enviados. Esto resulta útil en aquellas situaciones en que el dispositivo de red subyacente es capaz de generar la suma de comprobación del encabezado IPv4 y la aplicación no espera usar la fragmentación de IP ni IPsec.|
|NX_DISABLE_LOOPBACK_INTERFACE | Si se define, deshabilita la compatibilidad de NetX Duo con la interfaz de bucle invertido.|
|NX_DISABLE_RX_SIZE_CHECKING | Si se define, deshabilita la comprobación del tamaño de los paquetes recibidos.|
|NX_ENABLE_IP_RAW_PACKET_FILTER | Si se define, habilita la funcionalidad de filtro de recepción de paquetes IP sin procesar. Esta característica la pueden usar las aplicaciones que requieren más control sobre el tipo de paquetes IP sin procesar que se van a recibir. La característica de filtro de paquetes IP sin procesar también admite la operación de socket sin procesar en el nivel de compatibilidad de BSD. De manera predeterminada, esta opción no se define.|
|NX_ENABLE_IP_STATIC_ROUTING | Si se define, habilita el enrutamiento estático de IPv4 en el que a una dirección de destino se le puede asignar una dirección de próximo salto específica. De forma predeterminada, el enrutamiento estático de IPv4 está deshabilitado.|
|NX_FRAGMENT_IMMEDIATE_ASSEMBLY | Si se define, permite que la lógica de reensamblado de IPv4 e IPv6 se ejecute inmediatamente después de recibir un fragmento de IP. De manera predeterminada, esta opción no se define.|
|NX_IP_MAX_REASSEMBLY_TIME | Símbolo que controla el tiempo máximo permitido para volver a ensamblar fragmentos IPv4 e IPv6. Tenga en cuenta que el valor que se define aquí sobrescribe los valores ***NX_IPV4_MAX_REASSEMBLY_TIME** _ y _*_NX_IPV6_MAX_REASSEMBLY_TIME_* *.|
|NX_IP_PERIODIC_RATE | Si se define, especifica el número de tics del temporizador de ThreadX en un segundo. El valor predeterminado se deriva del símbolo de ThreadX ***TX_TIMER_TICKS_PER_SECOND,** _ que de forma predeterminada se establece en 100 (temporizador de 10 ms). Las aplicaciones deben tener cuidado al modificar este valor, ya que el resto de los módulos de NetX Duo derivan información de tiempo de _ *_NX_IP_PERIODIC_RATE_.* *|
|NX_IP_RAW_MAX_QUEUE_DEPTH | Símbolo que controla el número de paquetes IP sin procesar que se pueden poner en la cola de recepción de paquetes sin procesar. De manera predeterminada, el valor se establece en 20.| 
|NX_IP_ROUTING_TABLE_SIZE | Si se define, establece el número máximo de entradas que puede haber en la tabla de enrutamiento estático IPv4, que es una lista de una interfaz de salida y las direcciones de próximo salto de una dirección de destino determinada. El valor predeterminado es 8 y se define en ***nx_api.h.** _. Este símbolo solo se usa si se define _ *_NX_ENABLE_IP_STATIC_ROUTING_**.|
|NX_IPV4_MAX_REASSEMBLY_TIME | Símbolo que controla el tiempo máximo permitido para volver a ensamblar un fragmento IPv4. Tenga en cuenta que el valor definido en NX_IP_MAX_REASSEMBLY_TIME sobrescribe este valor.|

### <a name="packet-configuration-options"></a>Opciones de configuración de paquetes

| Opción  | Descripción  |
|---|---|
|NX_DISABLE_PACKET_CHAIN | Si se define, deshabilita la lógica de la cadena de paquetes. De manera predeterminada, no está definido.|
|NX_DISABLE_PACKET_INFO | Si se define, deshabilita la recopilación de información del grupo de paquetes.|
|NX_ENABLE_LOW_WATERMARK | Si se define, habilita la característica de referencia inferior del grupo de paquetes de NetX Duo. La aplicación establece un valor de referencia bajo. En la recepción de paquetes TCP, si se alcanza una referencia inferior del grupo de paquetes, NetX Duo descarta el paquete de forma silenciosa liberándolo, lo que evita que el grupo de paquetes se colapse. De forma predeterminada, esta característica no está habilitada.|
|NX_ENABLE_PACKET_DEBUG_INFO | Si se define, registra información de depuración de paquetes.|
|NX_PACKET_ALIGNMENT | Si se define, especifica el requisito de alineación, en bytes, para la dirección de inicio del área de carga de paquetes. Esta opción deja de usar ***NX_PACKET_HEADER_PAD** _ y _*_NX_PACKET_HEADER_PAD_SIZE_**. De forma predeterminada, esta opción se define como 4, lo que hace que la dirección de inicio del área de carga útil esté alineada en 4 bytes.|
|NX_PACKET_HEADER_PAD | Si se define, habilita el relleno hacia el final del bloque de control de NX_PACKET. El número de palabras ULONG lo define ***NX_PACKET_HEADER_PAD_SIZE** _. Tenga en cuenta que _*_NX_PACKET_ALIGNMENT_** deja esta opción en desuso.|
|NX_PACKET_HEADER_PAD_SIZE | Establece el número de palabras ULONG que se van a rellenar en la estructura de NX_PACKET, lo que permite que el área de carga de paquetes se inicie con la alineación deseada. Esta característica resulta útil cuando los descriptores del búfer de recepción apuntan directamente al área de carga de NX_PACKET y la lógica de recepción de la interfaz de red o la lógica de la operación de caché esperan que la dirección de inicio del búfer cumpla ciertos requisitos de alineación. Este valor solo es válido cuando se define ***NX_PACKET_HEADER_PAD** _. Tenga en cuenta que _*_NX_PACKET_ALIGNMENT_** deja esta opción en desuso.|

### <a name="rarp-configuration-options"></a>Opciones de configuración de RARP

| Opción  | Descripción  |
|---|---|
|NX_DISABLE_RARP_INFO | Si se define, deshabilita la recopilación de información de RARP.|

### <a name="tcp-configuration-options"></a>Opciones de configuración de TCP

| Opción | Descripción |
|---|---|
|NX_DISABLE_RESET_DISCONNECT | Si se define, deshabilita el procesamiento de restablecimiento durante la desconexión cuando el valor de tiempo de espera proporcionado se especifica como ***NX_NO_WAIT***.|
|NX_DISABLE_TCP_INFO | Si se define, deshabilita la recopilación de información de TCP.|
|NX_DISABLE_TCP_RX_CHECKSUM | Si se define, deshabilita la lógica de la suma de comprobación en los paquetes de TCP recibidos. Solo es útil en aquellas situaciones en que la capa de vínculo tiene un procesamiento de suma de comprobación o CRC confiables, o cuando el controlador de interfaz puede comprobar la suma de comprobación TCP en el hardware y la aplicación no usa IPsec.|
|NX_DISABLE_TCP_TX_CHECKSUM | Si se define, deshabilita la lógica de suma de comprobación para enviar paquetes de TCP. Solo resulta útil en aquellas situaciones en que el nodo de red receptor tiene deshabilitada la lógica de suma de comprobación TCP recibida o el controlador de red subyacente es capaz de generar la suma de comprobación TCP y la aplicación no usa IPsec.|
|NX_ENABLE_TCP_KEEPALIVE | Si se define, habilita el temporizador de Keepalive TCP opcional. La configuración predeterminada es no habilitado.|
|NX_ENABLE_TCP_MSS_CHECK | Si se define, habilita la comprobación del MSS del mismo nivel mínima antes de aceptar una conexión TCP. Para usar esta característica, debe definirse el símbolo ***NX_ENABLE_TCP_MSS_MINIMUM***. De forma predeterminada, esta opción está activada.|
|NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY| Si se define, permite a la aplicación instalar una función de devolución de llamada que se invoca cuando la profundidad de la cola de transmisión de TCP deja de estar en el valor máximo. Esta devolución de llamada sirve como indicación de que el socket TCP está listo para transmitir más datos. De forma predeterminada, esta opción no está habilitada.|
|NX_ENABLE_TCP_WINDOW_SCALING | Habilita la opción de escalado de ventana para las aplicaciones TCP. Si se define, la opción de escalado de ventana se negocia durante la fase de conexión de TCP y la aplicación puede especificar un tamaño de ventana superior a 64 k. La configuración predeterminada es no habilitada (no está definida).|
|NX_MAX_LISTEN_REQUESTS | Especifica el número máximo de solicitudes de escucha del servidor. El valor predeterminado es 10 y se define en ***nx_api.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_TCP_ACK_EVERY_N_PACKETS | Especifica el número de paquetes TCP que se reciben antes de enviar un ACK. Tenga en cuente que si ***NX_TCP_IMMEDIATE_ACK** _ está habilitado, pero *_NX_TCP_ACK_EVERY_N_PACKETS_** no lo está, este valor se establece automáticamente en 1 para obtener compatibilidad con versiones anteriores.|
|NX_TCP_ACK_TIMER_RATE | Especifica cómo se divide el número de tics del sistema (NX_IP_PERIODIC_RATE) para calcular la velocidad del temporizador para el procesamiento de confirmación diferida de TCP. El valor predeterminado es 5, que representa 200 ms, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_TCP_ENABLE_KEEPALIVE | Se ha cambiado el nombre a ***NX_ENABLE_TCP_KEEPALIVE** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_ENABLE_TCP_KEEPALIVE_**.|
|NX_TCP_ENABLE_MSS_CHECK | Se ha cambiado el nombre a ***NX_ENABLE_TCP_MSS_CHECK** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _ *_NX_ENABLE_TCP_MSS_CHECK._**|
|NX_TCP_ENABLE_WINDOW_SCALING | Se ha cambiado el nombre a ***NX_ENABLE_TCP_WINDOW_SCALING** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_ENABLE_TCP_WINDOW_SCALING_**.|
|NX_TCP_FAST_TIMER_RATE | Especifica cómo se divide el número de tics internos de NetX Duo (NX_IP_PERIODIC_RATE) para calcular la velocidad del temporizador de TCP rápido. El temporizador de TCP rápido se utiliza para controlar los distintos temporizadores de TCP, incluido el temporizador de confirmación retrasada. El valor predeterminado es 10, que representa 100 ms, suponiendo que el temporizador de ThreadX se ejecute a 10 ms. Este valor se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_TCP_IMMEDIATE_ACK| Si se define, habilita el procesamiento de respuesta de confirmación inmediata de TCP opcional. Definir de este símbolo equivale a definir ***NX_TCP_ACK_EVERY_N_PACKETS*** como 1.|
|NX_TCP_KEEPALIVE_INITIAL | Especifica el número de segundos de inactividad antes de que se active el temporizador de Keepalive. El valor predeterminado es 7200, que representa 2 horas, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_TCP_KEEPALIVE_RETRIES | Especifica el número de reintentos de Keepalive que se permiten antes de que la conexión se considere interrumpida. El valor predeterminado es 10, que representa 10 reintentos, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_TCP_KEEPALIVE_RETRY | Especifica el número de segundos entre los reintentos del temporizador de Keepalive, suponiendo que el otro lado de la conexión no responda. El valor predeterminado es 75, que representa 75 segundos entre reintentos, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_TCP_MAX_OUT_OF_ORDER_PACKETS | Símbolo que define el número máximo de paquetes TCP desordenados que se pueden mantener en la cola de recepción de sockets TCP. Este símbolo se puede usar para limitar el número de paquetes en cola en el socket de recepción TCP, lo que impide que se agote el grupo de paquetes. De forma predeterminada, este símbolo no se define, por lo que no hay límite en el número de paquetes desordenados que se ponen en la cola del socket TCP.|
|NX_TCP_MAXIMUM_RETRIES | Especifica el número de reintentos de transmisión de datos que se permiten antes de que la conexión se considere interrumpida. El valor predeterminado es 10, que representa 10 reintentos, y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_TCP_MAXIMUM_RX_QUEUE | Símbolo que define la cola de recepción máxima para sockets TCP. Esta característica la habilita ***NX_ENABLE_LOW_WATERMARK***.|
|NX_TCP_MAXIMUM_TX_QUEUE | Especifica la profundidad máxima de la cola de transmisión de TCP antes de que se suspendan o se rechacen las solicitudes de envío TCP. El valor predeterminado es 20, lo que significa que el número máximo de paquetes que puede haber en la cola de transmisión en un momento dado es 20. Tenga en cuenta que los paquetes permanecen en la cola de transmisión hasta que se reciba una confirmación que abarque algunos o todos los datos de los paquetes desde el otro lado de la conexión. Esta constante se define en ***nx_tcp. h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_TCP_MSS_MINIMUM | Símbolo que define el valor mínimo de MSS que el módulo TCP de NetX Duo acepta. Esta característica la habilita ***NX_ENABLE_TCP_MSS_CHECK***.|
|NX_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_ENABLE | Se ha cambiado el nombre a ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY_**.|
|NX_TCP_RETRY_SHIFT | Especifica cómo cambia el tiempo de espera de retransmisión entre los reintentos. Si este valor es 0, el tiempo de espera de retransmisión inicial es el mismo los posteriores. Si este valor es 1, se duplica el tiempo de espera en cada retransmisión posterior. Si este valor es 2, el tiempo de espera de retransmisión de cada retransmisión posterior es cuatro veces mayor. El valor predeterminado es 0 y se define en ***nx_tcp.h** _. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|
|NX_TCP_TRANSMIT_TIMER_RATE | Especifica cómo se divide el número de tics del sistema (***NX_IP_PERIODIC_RATE** _) para calcular la velocidad del temporizador para el procesamiento de reintentos de transmisión de TCP. El valor predeterminado es 1, que representa 1 segundo, y se define en _*_nx_tcp.h_*_. La aplicación puede invalidar el valor predeterminado. Para ello, debe definir el valor antes de que se incluya _ *_nx_api.h_**.|

### <a name="udp-configuration-options"></a>Opciones de configuración de UDP

| Opción  | Descripción  |
|---|---|
|NX_DISABLE_UDP_INFO | Si se define, deshabilita la recopilación de información de UDP.|
|NX_DISABLE_UDP_RX_CHECKSUM | Si se define, deshabilita el cálculo de la suma de comprobación de UDP en los paquetes UDP entrantes. Esto resulta útil si el controlador de la interfaz de red puede comprobar la suma de comprobación del encabezado UDP en el hardware y la aplicación no habilita la lógica de fragmentación de IP o IPsec.|
|NX_DISABLE_UDP_TX_CHECKSUM | Si se define, deshabilita el cálculo de la suma de comprobación de UDP en los paquetes UDP salientes. Esto resulta útil si el controlador de la interfaz de red puede calcular la suma de comprobación del encabezado UDP e insertar el valor en el encabezado IP antes de transmitir los datos y la aplicación no habilita la lógica de fragmentación de IP o IPsec.|

### <a name="ipv6-options"></a>Opciones de IPv6  

| Opción  | Descripción  |
|---|---|
| NX_DISABLE_IPV6 | Deshabilita la funcionalidad IPv6 cuando se crea la biblioteca de NetX Duo. En el caso de las aplicaciones que no necesitan IPv6, así se evita la extracción de código y el espacio de almacenamiento adicional necesario para admitir IPv6.|
|NX_DISABLE_IPV6_PATH_MTU_DISCOVERY | Si se define, deshabilita la detección de la MTU de la ruta de acceso, que se usa para determinar la MTU máxima en la ruta de acceso a un destino en la tabla de destinos de host de NetX Duo. Permite que el host NetX Duo envíe el paquete más grande posible que no requiera fragmentación. De forma predeterminada, esta opción está definida (la MTU de la ruta de acceso está deshabilitada).|
|NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY | Si se define, permite invocar una función de devolución de llamada cuando se cambia la dirección IPv6. De forma predeterminada, esta opción no está habilitada.|
|NX_ENABLE_IPV6_MULTICAST | Si se define, habilita la función de combinación/salida de multidifusión IPv6. De forma predeterminada, esta opción no está habilitada.|
|NX_ENABLE_IPV6_PATH_MTU_DISCOVERY | Si se define, habilita la característica de detección de MTU de la ruta de acceso de IPv6. De forma predeterminada, esta opción no está habilitada.|
|NX_IPV6_ADDRESS_CHANGE_NOTIFY_ENABLE | Se ha cambiado el nombre a ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY_**.|
|NX_IPV6_DEFAULT_ROUTER_TABLE_SIZE | Especifica el número de entradas que hay en la tabla de enrutamiento de IPv6. Se necesita al menos una entrada para el enrutador predeterminado. Definido en ***nx_api. h***, el valor predeterminado es 8.|
|NX_IPV6_DESTINATION_TABLE_SIZE | Especifica el número de entradas que hay en la tabla de destino de IPv6. Almacena información sobre las direcciones de próximo salto para las direcciones IPv6. Definido en ***nx_api. h***, el valor predeterminado es 8.|
|NX_IPV6_MAX_REASSEMBLY_TIME | Símbolo que controla el tiempo máximo que se permite para volver a ensamblar un fragmento de IPv6.|
|NX_IPV6_MULTICAST_ENABLE | Se ha cambiado el nombre a ***NX_ENABLE_IPV6_MULTICAST** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_ENABLE_IPV6_MULTICAST_**.|
|NX_IPV6_PREFIX_LIST_TABLE_SIZE | Especifica el tamaño de la tabla de prefijos. La información del prefijo se obtiene de los anuncios del enrutador y forma parte de la configuración de la dirección IPv6. Definido en ***nx_api. h***, el valor predeterminado es 8.|
|NX_IPV6_STATELESS_AUTOCONFIG_CONTROL | Si se define, permite que NetX Duo deshabilite la característica de configuración automática de direcciones sin estado. De forma predeterminada, esta opción no está habilitada.|
|NX_MAX_IPV6_ADDRESSES | Especifica el número de entradas que hay en el grupo de direcciones de IPv6. Durante la configuración de la interfaz, NetX Duo utiliza entradas IPv6 del grupo. Su valor predeterminado es (NX_MAX_PHYSICAL_INTERFACES \* 3), lo que permite que cada interfaz tenga al menos una dirección local de vínculo y dos direcciones globales. Tenga en cuenta que todas las interfaces comparten el grupo de direcciones IPv6.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Especifica el intervalo de espera, en tics de temporizador, para restablecer la MTU de la ruta de acceso de un destino específico de la tabla de destino. Si se define ***NX_DISABLE_IPV6_PATH_MTU_DISCOVERY***, la definición de este símbolo no tiene ningún efecto.|
|NX_PATH_MTU_INCREASE_WAIT_INTERVAL | Símbolo que especifica el intervalo de espera (en segundos) para restablecer el valor de la MTU de la ruta de acceso en una entrada de la tabla de destino. Solo es válido si se define ***NX_ENABLE_IPV6_PATH_MTU_DISCOVERY***. De forma predeterminada, este valor se establece en 600 (segundos).|

### <a name="neighbor-cache-configuration-options"></a>Opciones de configuración de la caché de vecinos

| Opción  | Descripción  |
|---|---|
|NX_DELAY_FIRST_PROBE_TIME | Especifica el retraso, en segundos, antes de que se envíe la primera solicitud de una entrada de la caché en estado STALE. Definido en ***nx_nd_cache.h***, el valor predeterminado es 5.|
|NX_DISABLE_IPV6_DAD | Si se define, esta opción deshabilita Detección de direcciones duplicadas (DAD) durante la asignación de direcciones IPv6. Las direcciones se establecen mediante configuración manual o a través de la configuración automática de direcciones sin estado.|
|NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES | Si se define, esta opción impide que NetX Duo quite las entradas antiguas de la tabla de caché antes de que expire su tiempo de espera para dejar espacio a las nuevas entradas cuando la tabla está llena. Las entradas estáticas y del enrutador nunca se purgan.|
|NX_IPV6_DAD_TRANSMITS | Especifica el número de mensajes de solicitud de vecino que se van a enviar antes de que NetX Duo marque una dirección de interfaz como válida. Si se define ***NX_DISABLE_IPV6_DAD** _ (DAD está deshabilitado), configurar esta opción no tiene efecto alguno. Como alternativa, si se asigna el valor cero (0), DAD se desactiva, pero su funcionalidad no desaparece. Definido en _*_nx_api.h_**, el valor predeterminado es 3.|
|NX_IPV6_DISABLE_PURGE_UNUSED_CACHE_ENTRIES | Se ha cambiado el nombre a ***NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_IPV6_PURGE_UNUSED_CACHE_ENTRIES_**.|
|NX_IPV6_NEIGHBOR_CACHE_SIZE | Especifica el número de entradas que puede haber en la tabla de la caché de vecinos IPv6. Definido en ***nx_nd_cache.h***, el valor predeterminado es 16.|
|NX_MAX_MULTICAST_SOLICIT | Especifica el número de mensajes de solicitud de vecino que NetX Duo transmite como parte del protocolo de detección de vecinos IPv6 cuando se requiere asignación entre la dirección IPv6 y la dirección MAC. Definido en ***nx_nd_cache.h***, el valor predeterminado es 3.|
|NX_MAX_UNICAST_SOLICIT | Especifica el número de mensajes de solicitud de vecino que NetX Duo transmite para determinar la disponibilidad de un vecino concreto. Definido en ***nx_nd_cache.h***, el valor predeterminado es 3.|
|NX_ARP_MAX_QUEUE_DEPTH | Símbolo que define el número máximo de paquetes que se ponen en cola para que se resuelva la caché de ND. De forma predeterminada, este símbolo se establece en 4.|
|NX_REACHABLE_TIME | Especifica el tiempo de espera, en segundos, para que una entrada de la memoria caché exista en el estado REACHABLE sin paquetes recibidos de la dirección IPv6 de destino de la caché. Definido en ***nx_nd_cache.h***, el valor predeterminado es 30.|
|NX_RETRANS_TIMER  | Especifica, en milisegundos, la duración del retraso entre los paquetes de convocatoria enviados por NetX Duo. Definido en ***nx_nd_cache.h***, el valor predeterminado es 1000.|
| NXDUO_DISABLE_DAD | Se ha cambiado el nombre a ***NX_DISABLE_IPV6_DAD** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_IPV6_DAD_**.|
|NXDUO_DUP_ADDR_DETECT_TRANSMITS | Se ha cambiado el nombre a ***NX_IPV6_DAD_TRANSMITS** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_IPV6_DAD_TRANSMITS_**.|

### <a name="miscellaneous-icmpv6-configuration-options"></a>Opciones variadas de configuración de ICMPv6

| Opción  | Descripción  |
|---|---|
|NX_DISABLE_ICMPV6_ERROR_MESSAGE | Si se define, elimina la posibilidad de que NetX Duo envíe un mensaje de error ICMPv6 como respuesta a un paquete con problemas (por ejemplo, el formato del encabezado no es correcto o el tipo de encabezado del paquete está en desuso) recibido de otro host.|
|NX_DISABLE_ICMPV6_REDIRECT_PROCESS | Si se define, deshabilita el procesamiento de paquetes de redireccionamiento ICMPv6. NetX Duo procesa los mensajes de redireccionamiento de forma predeterminada y actualiza la tabla de destino con la información de dirección IP del próximo salto.|
|NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS | Si se define, deshabilita NetX Duo para procesar la información recibida en paquetes de anuncios de enrutadores IPv6.|
|NX_DISABLE_ICMPV6_ROUTER_SOLICITATION | Si se define, deshabilita NetX Duo para enviar al enrutador mensajes de convocatoria del enrutador IPv6 a intervalos regulares.|
|NX_DISABLE_ICMPV6_RX_CHECKSUM | Si se define, deshabilita el cálculo de la suma de comprobación de ICMPv6 en los paquetes ICMP recibidos.|
|NX_DISABLE_ICMPv6_RX_CHECKSUM | Se ha cambiado el nombre a ***NX_DISABLE_ICMPV6_RX_CHECKSUM** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_CMPV6_RX_CHECKSUM_**.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Si se define, deshabilita el cálculo de la suma de comprobación de ICMPv6 en los paquetes ICMP transmitidos.|
|NX_DISABLE_ICMPV6_TX_CHECKSUM | Se ha cambiado el nombre a ***NX_DISABLE_ICMPV6_TX_CHECKSUM** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_ICMPV6_TX_CHECKSUM_**.|
|NX_ICMPV6_MAX_RTR_SOLICITATIONS | Defina el número máximo de convocatorias de enrutador que envía un host hasta que se recibe una respuesta de este. Si no se recibe ninguna, el host concluye que no hay ningún enrutador presente. El valor predeterminado es 3.|
|NX_ICMPV6_RTR_SOLICITATION_DELAY | Especifica el retraso máximo, en segundos, de la solicitud de enrutador inicial.|
|NX_ICMPV6_RTR_SOLICITATION_INTERVAL | Especifica el intervalo entre dos mensajes de convocatoria del enrutador. El valor predeterminado es 4.|
|NXDUO_DESTINATION_TABLE_SIZE | Se ha cambiado el nombre a ***NX_IPV6_DESTINATION_TABLE_SIZE** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_IPV6_DESTINATION_TABLE_SIZE_**.|
|NXDUO_DISABLE_ICMPV6_ERROR_MESSAGE | Se ha cambiado el nombre a ***NX_DISABLE_ICMPV6_ERROR_MESSAGE** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_ICMPV6_ERROR_MESSAGE_**.|
|NXDUO_DISABLE_ICMPV6_REDIRECT_PROCESS | Se ha cambiado el nombre a ***NX_DISABLE_ICMPV6_REDIRECT_PROCESS** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _ *_NX_DISABLE_ICMPV6_REDIRECT_PROCESS_**|  
|NXDUO_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS| Se ha cambiado el nombre a ***NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_ICMPV6_ROUTER_ADVERTISEMENT_PROCESS_**.|
|NXDUO_DISABLE_ICMPV6_ROUTER_SOLICITATION | Se ha cambiado el nombre a ***NX_DISABLE_ICMPV6_ROUTER_SOLICITATION** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_DISABLE_ICMPV6_ROUTER_SOLICITATION_**.|
|NXDUO_ICMPV6_MAX_RTR_SOLICITATIONS | Se ha cambiado el nombre a ***NX_ICMPV6_MAX_RTR_SOLICITATIONS** _. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _*_NX_ICMPV6_MAX_RTR_SOLICITATIONS_**.|
|NXDUO_ICMPV6_RTR_SOLICITATION_INTERVAL | Se ha cambiado el nombre a ***NX_ICMPV6_RTR_SOLICITATION_INTERVAL** _. Este símbolo está en desuso. Aunque aún se admite, se recomienda que los nuevos diseños utilicen _ *_NX_ICMPV6_RTR_SOLICITATION_INTERVAL_**|

## <a name="netx-duo-version-id"></a>Identificador de la versión de NetX Duo

La versión actual de NetX Duo está disponible tanto para el software de usuario como para el de la aplicación durante el tiempo de ejecución. La versión de NetX Duo se puede obtener al examinar el archivo **nx_port.h**. Además, este archivo también contiene un historial de versiones de la distribución correspondiente. Para que el software de la aplicación obtenga la versión de NetX Duo, es preciso examinar la cadena global _**_nx_version_id_*_ en _*_nx_port.h_**.

El software de la aplicación también puede obtener información de la versión en las constantes que se muestran a continuación, definidas en ***nx_api. h***.

Estas constantes identifican la versión actual del producto por nombre y la versión principal y secundaria del producto.

\#define EL_PRODUCT_NETXDUO  
\#define NETXDUO_MAJOR_VERSION  
\#define NETXDUO_MINOR_VERSION