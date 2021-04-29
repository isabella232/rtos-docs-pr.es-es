---
title: 'Capítulo 1: Introducción al servidor DHCPv6 de Azure RTOS NetX Duo'
description: En este documento se explica con detalle cómo el servidor DHCPv6 de NetX Duo asigna direcciones IPv6 a clientes DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6cf7baa91b1804876b97b1d75d1872d1120ad028
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814749"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-server"></a>Capítulo 1: Introducción al servidor DHCPv6 de Azure RTOS NetX Duo

En redes IPv6, DHCPv6 es necesario para que los clientes obtengan direcciones IPv6. No sustituye al DHCP, que está limitado a IPv4, ya que no ofrece direcciones IPv4. DHCPv6 tiene características similares a DHCP y muchas mejoras. Un cliente que no puede usar la configuración automática de direcciones sin estado IPv6 puede usar DHCPv6 para que se le asigne una dirección IPv6 global única desde un servidor DHCPv6.

NetX Duo se desarrolló para admitir aplicaciones basadas en red IPv6 y protocolos de red como DHCPv6. En este documento se explica con detalle cómo el servidor DHCPv6 de NetX Duo asigna direcciones IPv6 a clientes DHCPv6.

## <a name="dhcpv6-communication"></a>Comunicación de DHCPv6

**Estructura de los mensajes DHCPv6**

El contenido de los mensajes es básicamente un encabezado seguido de uno o varios (normalmente más) bloques de opciones. A continuación se muestra la estructura básica donde cada bloque representa un byte:

![Diagrama que muestra la estructura de bloques de opciones y mensajes DHCPv6.](media/image2.jpg)

**Figura 1. Estructura de bloques de opciones y mensajes DHCPv6**

El campo Msg-Type de 1 byte indica el tipo de mensaje DHCPv6. El campo Transaction-ID de 3 bytes lo establece el cliente. Puede ser cualquier secuencia de caracteres, pero debe ser única para cada mensaje del cliente al servidor (se conserva en los mensajes duplicados enviados por el cliente). El servidor utiliza ese campo Transaction-ID para cada respuesta al cliente con el fin de permitir que el cliente coteje los mensajes del servidor en caso de que se retrasen o quiten paquetes de la red. Después del campo Transaction-ID, se usan una o varias opciones de DHCPv6 para indicar lo que el cliente está solicitando.

La estructura de la opción DHCPv6 está formada por un código de opción, un campo de longitud de opción, que no incluye los campos de longitud o de código y, por último, los datos de opciones, que son uno o más campos de códigos de opción de 2 bytes correspondientes a los datos que el cliente solicita.

Algunos bloques de opciones tienen opciones anidadas. Por ejemplo, una opción de *asociación de identidades de direcciones no temporales (IANA)* contiene una o más opciones de *asociación de identidades (IA)* para solicitar direcciones IPv6. La opción de *IANA* devuelta en el mensaje de respuesta del servidor contiene las mismas opciones de *IA* con la dirección IPv6 y los tiempos de concesión concedidos por el servidor, así como una opción *Status* (Estado) que indica si hay un error en la solicitud de la dirección del cliente.

En el **Apéndice A** se proporciona una lista de todos los bloques de opciones con su descripción.

**Tipos de mensajes DHCPv6**

Aunque DHCPv6 mejora en gran medida la funcionalidad de DHCP, usa el mismo número de mensajes que DHCP y admite las mismas opciones de proveedor que DHCP. La lista de mensajes DHCPv6 es la siguiente:

- SOLICIT (1) (enviado por el cliente)
- ADVERTISE (2) (enviado por el servidor)
- REQUEST (3) (enviada por el cliente)
- REPLY (7) (enviada por el servidor)
- CONFIRM (4) (enviado por el cliente)
- RENEW (5) (enviado por el cliente)
- REBIND (6) (enviado por el cliente)
- RELEASE (8) (enviada por el cliente)
- DECLINE (9) (enviado por el cliente)
- INFORM_REQUEST (11) (enviado por el cliente)
- RECONFIGURE* (10) (enviado por el servidor)

\* El servidor DHCPv6 de NetX Duo no admite RECONFIGURE.

La secuencia de solicitud DHCPv6 básica, con el tipo de mensaje DHCPv4 equivalente entre paréntesis, es la siguiente:

Client ***Solicit** _ (_Discovery *) Server **Advertisement** (* Offer *) Client **Request** (* Request *) Server **Reply** (* DHCPAck*)

Client **Renew**(same) Server **Reply** (*DHCPAck*)

## <a name="dhcpv6-message-validation"></a>Validación de mensajes DHCPv6

Identificador de transacción: el cliente debe generar un identificador de transacción para cada mensaje que envía al servidor. El servidor DHCPv6 rechazará cualquier mensaje del cliente que no coincida con este identificador de transacción. A su vez, el servidor debe usar el mismo identificador de transacción en sus respuestas al cliente.

**Identificadores únicos DHCPv6 (DUID)**

Todos los mensajes del servidor también deben incluir un identificador único de DHCPv6 (DUID) en cada mensaje, o el cliente DHCPv6 no debería aceptar el mensaje. Un DUID de nivel de vínculo (LL) es un bloque de control que contiene la dirección MAC del cliente, el tipo de hardware y el tipo de DUID. Un DUID de tiempo de nivel de vínculo (LLT) también contiene un campo de tiempo que reduce las probabilidades de que el DUID no sea único en la red del host. Por ese motivo, RFC 3315 recomienda LLT DUID en lugar de LL DUID. Si la aplicación host no crea su propio valor de tiempo único, el servidor DHCPv6 de NetX Duo proporcionará uno predeterminado. El tercer tipo de DUID es el DUID de empresa (asignado por el proveedor) que contiene un identificador de empresa registrado (como el registrado en IANA) y datos privados que son variables de tipo y longitud; por ejemplo, según el tamaño de la memoria o el tipo de sistema operativo de otra configuración de hardware. Consulte la lista de opciones de configuración en otra sección de este documento para configurar los valores de identificador privado y asignado por el proveedor del servidor.

El cliente también debe incluir su DUID en sus mensajes al servidor, excepto INFORM_REQUEST; de lo contrario, el servidor los rechazará.

**Sesiones de clientes y servidores DHCPv6**

Los clientes y servidores DHCPv6 intercambian mensajes a través de UDP. El cliente utiliza el puerto 546 para enviar y recibir mensajes DHCPv6, mientras que el servidor usa el puerto 547. El cliente usa inicialmente su dirección local de vínculo para transmitir y recibir mensajes DHCPv6. Este envía todos los mensajes a los servidores DHCPv6 con una dirección de multidifusión reservada de ámbito de vínculo conocida como *dirección de multidifusión* *All_DHCP_Relay_Agents_and_Servers* (FF02::01:02).

Para las solicitudes de asignación de direcciones IPv6, el servidor DHCPv6 escucha los mensajes *Solicit* enviados a la dirección *All_DHCP_Relay_Agents_and_Servers*. En la solicitud *Solicit*, el cliente puede solicitar la asignación de una dirección IPv6 específica o dejar que el servidor elija una. También puede solicitar otra información de configuración de red del servidor.

Si el servidor DHCPv6 extrae un mensaje *Solicit* válido y puede asignar una dirección IPv6 al cliente, responde con un mensaje *Advertise* que contiene la dirección IPv6 que se va a conceder al cliente, el tiempo de concesión de la dirección IPv6 y cualquier información adicional solicitada por el cliente. Si el cliente acepta la oferta del servidor, responde con un mensaje *Request* que permite al servidor saber que aceptará la dirección IPv6. El servidor confirma que el cliente está enlazado a la dirección IPv6 con un mensaje *Reply*.

Si el mensaje DHCPv6 del cliente no es válido, el servidor descartará el mensaje de forma silenciosa. Si el servidor no puede conceder la solicitud, enviará un mensaje *Reply* con una indicación del problema en el campo Status (Estado) de la opción de IANA de la dirección IP. Si se reciben solicitudes de cliente duplicadas, el servidor vuelve a enviar su respuesta DHCPv6 anterior, dando por hecho que el cliente no haya recibido el paquete.

Es el cliente quien comprueba que su dirección IPv6 asignada desde el servidor no está asignada a otro host del sistema mediante el uso de varios protocolos IPv6, como el de detección de direcciones duplicadas. Si la dirección no es única, el cliente enviará un mensaje *Decline* al servidor. El servidor actualiza su tabla de concesión de direcciones IP con esta información, registrando que la dirección ya está asignada. Mientras tanto, el cliente debe reiniciar el proceso de solicitud DHCPv6 con otro mensaje *Solicit*.

Además de una dirección IPv6, es probable que un cliente también tenga que conocer el servidor DNS y, posiblemente, otra información de red, como el nombre de dominio de red. DHCPv6 proporciona los medios para solicitar esta información mediante el uso de solicitudes de opciones en los mensajes *Solicit* y *Request*, o bien por separado en mensajes *INFORM_REQUEST*. Las opciones de DHCPv6 se explican más adelante en este capítulo.

**Duración de la concesión de IPv6**

Cuando el servidor concede una dirección IPv6 a un cliente, también asigna la duración de la concesión (vigencia) en la opción de IANA para cuando recomiende al cliente que empiece a renovar (T1) o reenlazar (T2) su dirección IPv6 utilizando los mensajes *Renew* y *Rebind*. La diferencia entre los dos es que el cliente dirige el mensaje *Renew* al servidor incluyendo el DUID del servidor en la solicitud *Renew*. Sin embargo, no especifica ningún servidor y, por lo tanto, no incluye un DUID de servidor, en el mensaje *Rebind* a la dirección *All_DHCP_Relay_Agents_and_Servers*. La opción de IA que contiene la dirección IPv6 real que el servidor concede al cliente también contiene las duraciones preferida y válida cuando la dirección IPv6 concedida está en desuso u obsoleta (no válida), respectivamente.

El servidor DHCPv6 de NetX Duo mantiene un tiempo de espera de la sesión para cada cliente con el fin de hacer un seguimiento del tiempo entre los mensajes del cliente. Esto es necesario en caso de que un host de cliente pierda conectividad o la red esté desactivada. Cuando expira el tiempo de espera de la sesión, se supone que el cliente ya no está interesado o puede realizar solicitudes DHCPv6 del servidor. El servidor elimina el registro del cliente y devuelve cualquier dirección IPv6 asignada provisionalmente al grupo disponible. El tiempo de espera de la sesión es una opción configurable por el usuario.

Si el cliente desea liberar su dirección IPv6 o detecta que la dirección IPv6 asignada por el servidor DHCPv6 ya está en uso, envía un mensaje *Release* o *Decline*, respectivamente. En el caso de un mensaje *Release*, el servidor devuelve el estado de la dirección IPv6 al grupo disponible. En el caso del mensaje *Decline*, actualiza su tabla de concesión de direcciones IP para indicar que esta dirección IPv6 no está disponible (es propiedad de otra entidad en otra parte de la red).

**Concesión de direcciones IPv6 y datos de registros del cliente**

Cuando el servidor DHCPv6 comienza a aceptar solicitudes del cliente, mantiene una lista de clientes activos que envían solicitudes o a los que se les ha asignado direcciones IPv6. El servidor comprueba la expiración de la concesión de dirección IP por medio de un temporizador de concesión que actualiza periódicamente la duración de la concesión del cliente. Cuando la duración supera la duración válida, el servidor borra el registro del cliente y devuelve su dirección IPv6 al grupo disponible. El cliente debe iniciar el proceso de renovación y reenlace antes de que esto suceda.

La tabla de registros de clientes y servidores DHCPv6 de NetX Duo contiene información para identificar a los clientes e información de "estado" para validar las solicitudes del cliente DHCPv6 y asignar o volver a asignar las direcciones IPv6. Esta información incluye lo siguiente:

- El identificador único de DHCPv6 del cliente (DUID) que define de forma única cada host de cliente en una red. El cliente siempre debe usar este mismo DUID para todos sus mensajes DHCPv6.

- Las direcciones IPv6 acumulativas de la asociación de identidades de direcciones no temporales (IANA) y la asociación de identidades (IA) del cliente, que definen los parámetros de asignación de direcciones IPv6 del cliente.

- Solicitudes de opciones del cliente (servidor DNS, nombre de dominio, etc.).

- La dirección de origen IPv6 del cliente (si se establece) y la dirección de destino (si no es de multidifusión) de la solicitud DHCPv6 más reciente.

- El tipo de mensaje más reciente del cliente y el "estado" de DHCPv6.

## <a name="netx-duo-dhcpv6-server-requirements-and-constraints"></a>Requisitos y restricciones del servidor DHCPv6 de NetX Duo

La API del servidor DHCPv6 de NetX Duo requiere ThreadX 5.1 o posterior y NetX Duo 5.5 o posterior.

**Requisitos**

***Configuración de tareas de subprocesos de direcciones IP***

El servidor DHCPv6 de NetX Duo requiere la creación de una instancia de IP para enviar y recibir mensajes a DHCPv6 en su vínculo de red. Esto se hace mediante el servicio *nx_ip_create*. El servidor DHCPv6 de NetX Duo se debe crear. Esto se hace mediante el servicio *nx_dhcpv6_server_create*.

DHCPv6 emplea NetX Duo, ICMPv6 y UDP. Por lo tanto, IPv6 primero debe estar habilitado antes de usar el servidor DHCPv6 mediante una llamada a los siguientes servicios de NetX Duo:

- *nx_udp_enable*
- *nxd_ipv6_enable*
- *nxd_icmp_enable*

Además, antes de que se pueda iniciar el servidor DHCPv6, tiene varias tareas de configuración que realizar:

- Crear y validar sus direcciones globales IPv6 y locales de vínculo. La validación de direcciones se realiza automáticamente mediante NetX Duo, que emplea el protocolo de detección de direcciones duplicadas si está habilitado. Vea el *manual del usuario de NetX Duo* para obtener más información sobre la validación de direcciones IP globales y locales de vínculo.

- Establecer el índice de la interfaz de red para su interfaz DHCPv6.

- Crear un intervalo de direcciones IP para direcciones IPv6 asignables. O, si hay datos de una sesión anterior DHCPv6 del servidor, los registros de clientes y la tabla de concesión de IPv6 de esa sesión se deben cargar desde la memoria no volátil al servidor DHCPv6. En el sistema de ejemplo pequeño de este documento se mostrarán los servicios del servidor DHCPv6 para cumplir este requisito.

- Establecer el DUID del servidor. Si el servidor ha creado su DUID en una sesión anterior, debe usar los mismos datos para crear el mismo DUID para los mensajes a sus clientes. En el sistema de ejemplo pequeño de este documento se muestra cómo se cumple este requisito.

En este punto, el servidor DHCPv6 está listo para ejecutarse. Internamente, el servidor DHCPv6 de NetX Duo creará un socket UDP enlazado al puerto 547 y comenzará a escuchar las solicitudes del cliente.

***Requisitos de grupos de paquetes***

El servidor DHCPv6 de NetX Duo requiere un grupo de paquetes para enviar mensajes DHCPv6. El tamaño del grupo de paquetes en términos de carga de paquetes y el número de paquetes disponibles es configurable por el usuario, y depende del volumen previsto de mensajes DHCPv6 y otras transmisiones que va a enviar la aplicación host.

Un mensaje DHCPv6 típico tiene aproximadamente 200-300 bytes, según el número de opciones adicionales que solicite el cliente, y de la información disponible en el servidor.

***Configuración de la interfaz del servidor DHCPv6***

El servidor DHCPv6 utiliza de forma predeterminada la interfaz de red principal como la interfaz en la que aceptará las solicitudes del cliente. Sin embargo, la aplicación host todavía debe establecer el índice de direcciones globales que se usó para crear la dirección global del servidor. El índice de la interfaz DHCPv6 y el índice de direcciones globales se establecen mediante el servicio *nx_dhcpv6_server_interface_set*. Esto también se muestra en el "sistema de ejemplo pequeño" de este documento.

***Guardado de los DUID de DHCPv6 en los reinicios del servidor***

El protocolo DHCPv6 requiere que el servidor use el mismo DUID en varios reinicios. Por tanto, los datos usados para crear el DUID deben almacenarse y recuperarse de la memoria no volátil para cumplir este requisito. Para hosts que usan el nivel de vínculo y el DUID de tiempo que requiere acceso a un reloj en tiempo real, la aplicación host DHCPv6 de NetX Duo debe incluir el acceso a datos en tiempo real con el fin de generar un valor de tiempo para la creación inicial de DUID del servidor y almacenar esos datos para su reutilización en sesiones posteriores del servidor. A continuación, *nx_dhcpv6_set_server_duid* toma los datos de DUID como argumentos, así como las opciones de configuración en función del tipo de DUID, para generar (o reproducir) su propio DUID.

***Creación de listas de direcciones IPv6 asignables***

Después de crear el servidor DHCPv6, la aplicación host del servidor debe crear un intervalo de direcciones globales IPv6 asignables si no hay datos de listas de direcciones IP previamente almacenados. Esto se hace mediante el servicio *nx_dhcpv6_create_ip_address_range* que toma como entrada una dirección IPv6 inicial y final.

***Guardado de los datos del cliente y las direcciones DHCPv6 asignables***

El protocolo DHCPv6 requiere que el servidor DHCPv6 guarde los datos del cliente y de las direcciones IPv6 en un almacenamiento no volátil en caso de que se reinicie el servidor. El servidor DHCPv6 de NetX Duo tiene varias API para cargar y descargar datos del cliente y de las direcciones IPv6 con origen y destino en el servidor DHCPv6, respectivamente:

*nx_dhcpv6_add_client_record*

*nx_dhcpv6_add_ip_address_lease*

*nx_dhcpv6_retrieve_client_record*

*nx_dhcpv6_retrieve_ip_address_lease*

La carga de datos en el servidor debe realizarse antes de reiniciar el servidor. La descarga de los datos debe realizarse solo después de que el servidor DHCPv6 se detenga (o se suspenda). Los servicios para hacerlo se describen con detalle más adelante en este documento. Sin embargo, el servidor DHCPv6 de NetX Duo no define ningún acceso al almacenamiento no volátil. Este debe controlarse mediante la aplicación host. En el sistema de ejemplo pequeño se muestra cómo la aplicación host lo hace.

***Identificador único de DHCP (DUID) del servidor***

El DUID del servidor define de forma única el host del servidor DHCPv6 en la red. Si un servidor no ha creado previamente su DUID, puede usar *nx_dhcpv6_server_set_duid* para crear uno. Según RFC 3315, el servidor DHCPv6 debe guardar este DUID en la memoria no volátil para poder recuperarlo después de que se reinicie el servidor. El servidor DHCPv6 es compatible con los tipos de DUID de nivel de vínculo, de tiempo de nivel de vínculo y de empresa (asignado por el proveedor). Tenga en cuenta que el cliente debe enviar directamente el DUID de tipo de proveedor. La opción para los DUID (17) de tipo de proveedor no es compatible directamente con el servidor DHPv6 de NetX Duo.

La aplicación host del servidor DHCPv6 tiene valores predeterminados para la asignación de direcciones IPv6 que incluye el tiempo de espera de la concesión. Consulte la sección de opciones configurables más adelante en este documento para obtener más información sobre cómo establecer estas opciones. :

El bloque de control de *IANA* contiene los campos T1 y T2. El bloque *IA* del bloque de control de *IANA* contiene los campos de las duraciones preferida y válida. La aplicación host tiene opciones configurables definidas en otro lugar de este documento para establecer estas opciones. Estas se asignan a todas las solicitudes de direcciones IPv6 del cliente.

Estos parámetros de concesión de direcciones IP DHCPv6 se definen a continuación.

T1: tiempo en segundos en que el cliente debe empezar a renovar su dirección IPv6 desde el servidor que la asignó.

T2: tiempo en segundos en el que el cliente debe iniciar el reenlace de la dirección IPv6, si se produce un error de renovación, con cualquier servidor en su vínculo.

Duración preferida: tiempo en segundos en que la dirección del cliente deja de estar en desuso si el cliente no la ha renovado ni reenlazado. El cliente puede seguir usando esta dirección.

Duración válida: tiempo en segundos en que la dirección IP del cliente expiró y no debe usar esta dirección en sus transmisiones de red.

RFC recomienda los tiempos T1 y T2 que son 0,5 y 0,8, respectivamente, de la duración preferida en la opción de *IANA* del cliente. Si el servidor no tiene ninguna preferencia, debe establecer estos tiempos en cero. Si una respuesta del servidor contiene los tiempos T1 y T2 establecidos en cero, se permite que el cliente establezca sus propios tiempos T1 y T2.

**Restricciones**

El servidor DHCPv6 de NetX Duo no es compatible con las siguientes opciones de DHCPv6:

  - Opción de confirmación rápida que optimiza el proceso de solicitud de direcciones DHCPv6 solo para el intercambio de mensajes de solicitud y respuesta.

  - Opción reconfigure que permite al servidor iniciar cambios en el estado de la dirección IP del cliente.

  - Opción de unidifusión: todos los mensajes del cliente deben enviarse a la dirección de multidifusión *All_DHCP_Relay_Agents_and_Servers* en lugar de directamente al servidor DHCPv6.

  - Opción de la asociación de identidades de direcciones temporales (IA_TA), que es una dirección IP temporal concedida a un cliente.

  - Varias opciones de IA (direcciones IPv6) por solicitud del cliente.

  - El host de retransmisión entre el cliente y el servidor DHCPv6; por ejemplo, el cliente y el servidor deben estar en la misma red.

  - IPSec y la autenticación no se admiten en la mensajería DHCPv6. Sin embargo, la instancia de IP puede estar habilitada para IPSec según la versión de NetX Duo en uso.

  - El servidor DHCPv6 de NetX Duo solo admite directamente la solicitud de opción de servidor DNS. Esto puede cambiar en versiones futuras.

  - No se admite la opción de delegación de prefijo.

  - Autenticación de mensajes DHCPv6, aunque IPSec se puede habilitar en el entorno de NetX Duo subyacente. Ninguno de los servidores DHCPv6 de NetX Duo admiten conexiones de retransmisión a los clientes. Se da por sentado que todas las solicitudes del cliente se originan en los hosts de la red del servidor.

## <a name="netx-duo-dhcpv6-server-callback-functions"></a>Funciones de devolución de llamada del servidor DHCPv6 de NetX Duo

*nx_dhcpv6_IP_address_declined_handler*

Cuando el cliente DHCPv6 envía un mensaje Decline, el servidor DHCPv6 de NetX Duo marca la dirección como no disponible en las tablas de direcciones IPv6. Para poder personalizar el servidor que controla este mensaje, se proporciona *nx_dhcpv6_IP_address_declined_handler* *.* Sin embargo, esta devolución de llamada no está implementada actualmente.

*nx_dhcpv6_server_option_request_handler*

Cuando el mensaje del cliente DHCPv6 contiene datos de solicitud de opción, el servidor DHCPv6 de NetX Duo reenvía cada código de opción de solicitud a esta devolución de llamada de usuario, si se ha definido. De esta forma, el servidor de NetX Duo puede permitir que la devolución de llamada definida por el usuario llene los datos. Sin embargo, esta funcionalidad no está implementada actualmente.

## <a name="supported-dhcpv6-rfcs"></a>RFC de DHCPv6 compatibles

El servidor DHCPv6 de NetX Duo es compatible con RFC3315, RFC3646 y RFC relacionados.