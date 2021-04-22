---
title: 'Capítulo 3: Descripción funcional del servicio DTLS de Azure RTOS NetX Secure'
description: Este capítulo contiene una descripción funcional del servicio DTLS de Azure RTOS NetX Secure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 468f1dc8a8334dc89064594b29dc8cfabd7d8fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815373"
---
# <a name="chapter-3-functional-description-of-azure-rtos-netx-secure-dtls"></a>Capítulo 3: Descripción funcional del servicio DTLS de Azure RTOS NetX Secure

## <a name="execution-overview"></a>Información general sobre la ejecución

Este capítulo contiene una descripción funcional del servicio DTLS de Azure RTOS NetX Secure. Hay dos tipos principales de ejecución de programa en una aplicación DTLS de NetX Secure: inicialización y llamadas a la interfaz de la aplicación. 

NetX Secure presupone la existencia de ThreadX y NetX/NetXDuo. En ThreadX, se requiere la ejecución de subprocesos, la suspensión, temporizadores periódicos e instalaciones de exclusión mutua. En NetX/NetXDuo, se necesitan los controladores y los dispositivos de red de IP y UDP.

## <a name="datagram-transport-layer-security-dtls-and-transport-layer-security-tls"></a>Seguridad de la capa de transporte de datagramas (DTLS) y Seguridad de la capa de transporte (TLS)

El servicio DTLS de NetX Secure implementa la versión 1.2 del protocolo DTLS (Seguridad de la capa de transporte de datagramas) definido en la RFC 6347. La versión 1.0 de DTLS se definió en la RFC 4347 y correspondía a la versión de 1.1 de TLS. Dado que DTLS es esencialmente una extensión de TLS, se decidió que la versión siguiente usaría el mismo número de versión que la versión de TLS correspondiente. Por lo tanto, no hay ninguna versión de 1.1 de DTLS porque la versión 1.2 de DTLS corresponde a la versión de 1.2 de TLS.

> [!NOTE]
> NetX Secure admite la versión 1.2 de DTLS. DTLS 1.0 (RFC 4347) **no** se admite actualmente.

*Capa de sockets seguros* (SSL) era el nombre original de TLS antes de que se convirtiera en un estándar en la RFC 2246 y “SSL” se utiliza a menudo como nombre genérico para los protocolos TLS. La última versión de SSL era 3.0 y TLS 1.0 a veces se denomina SSL 3.1. Todas las versiones del protocolo “SSL” oficial se consideran obsoletas y no seguras; actualmente NetX Secure no ofrece una implementación de SSL.

TLS especifica un protocolo para generar *claves de sesión* que se crean durante *el protocolo de enlace* de TLS entre un cliente y un servidor de TLS, y dichas claves se utilizan para cifrar los datos enviados por la aplicación durante la *sesión* de TLS.

DTLS está estrechamente relacionado con TLS, ya que ambos protocolos comparten mecanismos de seguridad subyacentes. Sin embargo, TLS está diseñado para funcionar a través de un protocolo de capa de transporte que proporciona garantías sobre la entrega y el orden de paquetes (casi siempre TCP en la práctica) y no funcionará a través de un protocolo no confiable como UDP. DTLS se incorporó precisamente debido a UDP: DTLS se diseñó para tratar la naturaleza no confiable de UDP y de protocolos similares. Para ello, incluye la lógica de ordenación y confiabilidad (por ejemplo, la retransmisión de datos anulados) de manera similar a protocolos confiables como TCP.

En el capítulo 3 de la guía de usuario del servicio TLS de NetX Secure se incluye un análisis completo de TLS, por lo que este documento se centrará en las diferencias entre TLS y DTLS.

### <a name="dtls-record-header"></a>Encabezado de registro DTLS

Cualquier registro DTLS válido debe tener un encabezado DTLS, como se muestra en la figura 1. El encabezado es igual que el TLS pero incluye dos nuevos campos: la *época* de 16 bits y el *número de secuencia* de 48 bits (se describen a continuación).

![Diagrama de un encabezado de registro DTLS.](media/image2.png)

**Figura 1: Encabezado de registro DTLS**

Los campos del encabezado de registro TLS se definen de la siguiente manera:

| Campo de encabezado TLS | Propósito  |
| ---------------- | --------- |
| **Tipo de mensaje de 8 bits** | Este campo contiene el tipo de registro DTLS que se está enviando. Los tipos válidos son los siguientes:<br />- ChangeCipherSpec: 0x14<br />- Alert: 0x15<br />- Handshake: 0x16<br />- ApplicationData: 0x17<br /> |
| **Versión del protocolo de 16 bits** | Este campo contiene la versión del protocolo DTLS. Los valores válidos son los siguientes:<br />- DTLS 1.1: 0xFEFD |
|  **Época de 16 bits** |  Este campo contiene la “época” de DTLS, que es un contador que se incrementa cada vez que se cambia el estado de cifrado (por ejemplo, al generar nuevas claves de sesión).  |
|  **Número de secuencia de 48 bits** |  Este campo contiene un número de secuencia que identifica este registro en particular. Lo usa DTLS para mantener el orden de los registros y comprobar la necesidad de retransmisión. |
|  **Longitud de 16 bits** |  Este campo contiene la longitud de los datos encapsulados en el registro DTLS.  |

### <a name="dtls-handshake-record-header"></a>Encabezado de registro de protocolo de enlace DTLS

Cualquier registro de protocolo de enlace DTLS válido debe tener un encabezado de protocolo de enlace DTLS, como se muestra en la figura 2.

![Diagrama de un encabezado de registro de protocolo de enlace DTLS.](media/image3.png)

**Figura 2: Encabezado de registro de protocolo de enlace DTLS**

Los campos del encabezado de registro de protocolo de enlace DTLS se definen de la siguiente manera:

| Campo de encabezado TLS | Propósito |
| ---------------- | ------------------------------------------------ |
| **Tipo de mensaje de 8 bits** | Este campo contiene el tipo de registro DTLS que se está enviando. Los tipos válidos son los siguientes:<br />- ChangeCipherSpec: 0x14<br />- Alert: 0x15<br />- Handshake: 0x16<br />- ApplicationData: 0x17 |
|  **Época de 16 bits** | Este campo contiene la “época” de DTLS, que es un contador que se incrementa cada vez que se cambia el estado de cifrado (por ejemplo, al generar nuevas claves de sesión). |
|  **Número de secuencia de 48 bits** | Este campo contiene un número de secuencia que identifica este registro en particular. Lo usa DTLS para mantener el orden de los registros y comprobar la necesidad de retransmisión. |
|  **Versión del protocolo de 16 bits** | Este campo contiene la versión del protocolo DTLS. Los valores válidos son los siguientes:<br />- DTLS 1.1: 0xFEFD |
| **Longitud de 16 bits** | Este campo contiene la longitud de los datos encapsulados en el registro DTLS. |
| **Tipo de protocolo de enlace de 8 bits** | Este campo contiene el tipo de mensaje del protocolo de enlace. Los valores válidos son los siguientes:<br />- HelloRequest: 0x00<br />- ClientHello: 0x01<br />- ServerHello: 0x02<br />- Certificate: 0x0B<br />- ServerKeyExchange: 0x0C<br />- CertificateRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificateVerify: 0x0F<br />- ClientKeyExchange: 0x10<br />- Finalizado | 0x14 |
| **Longitud de 24 bits** | Este campo contiene la longitud de los datos del mensaje del protocolo de enlace. |
| **Número de secuencia de 16 bits** | Este campo contiene un número de secuencia. |

### <a name="the-dtls-handshake-and-dtls-session"></a>El protocolo de enlace DTLS y la sesión de DTLS

En la figura 3 se muestra un protocolo de enlace DTLS típico. Es casi idéntico al protocolo de enlace TLS típico con una diferencia importante: cuando el mensaje ClientHello se envía por primera vez, el servidor responde con un nuevo mensaje específico de DTLS, *HelloVerifyRequest* que contiene una “cookie”. El cliente DTLS debe responder con un segundo mensaje ClientHello que contenga esa cookie antes de que el protocolo de enlace pueda continuar. Este mecanismo se ha agregado a DTLS para evitar determinados ataques de denegación de servicio (DoS), ya que UDP es un protocolo sin conexión (TCP requiere una conexión o un puerto dedicados para que TLS no sufra el mismo problema).

Un protocolo de enlace DTLS comienza cuando el cliente envía un mensaje *ClientHello* a un servidor DTLS e indica su deseo de iniciar una sesión de DTLS. El mensaje contiene información sobre el cifrado que el cliente desea utilizar para la sesión, junto con la información utilizada para generar las claves de sesión más adelante en el protocolo de enlace. Hasta que no se generen las claves de sesión, no se cifrarán todos los mensajes del protocolo de enlace DTLS. Como se mencionó anteriormente, el servidor DTLS puede enviar un valor HelloVerifyRequest en la respuesta a ClientHello, lo que obliga al cliente a responder con un segundo ClientHello actualizado.

Tras recibir el segundo mensaje ClientHello, el servidor DTLS comprobará la cookie y, si la respuesta es correcta, responderá con un mensaje ServerHello que indica una selección de las opciones de cifrado proporcionadas por el cliente. ServerHello va seguido de un mensaje de certificado en el que el servidor proporciona un certificado digital para autenticar su identidad en el cliente (si se usa la comprobación X.509). Por último, el servidor envía un mensaje ServerHelloDone para indicar que no tiene más mensajes para enviar. Opcionalmente, el servidor puede enviar otros mensajes después de ServerHello y, en algunos casos, puede no enviar un mensaje de certificado (por ejemplo, cuando se usan claves previamente compartidas), de ahí que el mensaje ServerHelloDone sea necesario.

Una vez que el cliente ha recibido todos los mensajes del servidor, tiene suficiente información para generar las claves de sesión. TLS/DTLS lo hace mediante la creación de un bit compartido de datos aleatorios denominado *secreto premaestro*, que tiene un tamaño fijo y se utiliza como un valor de inicialización para generar todas las claves necesarias una vez habilitado el cifrado. El secreto premaestro se cifra mediante el algoritmo de clave pública (por ejemplo, RSA) especificado en los mensajes Hello (consulte más abajo para obtener información sobre los algoritmos de clave pública) y la clave pública proporcionada por el servidor en su certificado. Una característica opcional de TLS/DTLS denominada claves precompartidas (PSK) admite conjuntos de cifrado que no usan un certificado, sino un valor de secreto compartido entre los hosts (normalmente a través de transferencia física u otro método protegido). Cuando se habilita PSK, se usa la clave secreta precompartida para generar el secreto premaestro. Consulte la sección sobre las claves precompartidas en “Métodos de autenticación” a continuación.

En un protocolo de enlace TLS/DTLS habitual, el secreto premaestro cifrado se envía al servidor en el mensaje ClientKeyExchange. El servidor, al recibir el mensaje ClientKeyExchange, descifra el secreto premaestro mediante su clave privada y continúa generando las claves de sesión en paralelo con el cliente TLS/DTLS.

Una vez generadas las claves de sesión, todos los mensajes posteriores se pueden cifrar mediante el algoritmo de clave privada (por ejemplo, AES) seleccionado en los mensajes Hello. El cliente y el servidor envían un mensaje no cifrado final denominado ChangeCipherSpec para indicar que se cifrarán todos los mensajes posteriores.

El primer mensaje cifrado enviado por el cliente y el servidor también es el mensaje de protocolo de enlace TLS final, denominado Finished. Este mensaje contiene un hash de todos los mensajes de protocolo de enlace recibidos y enviados. Este hash se utiliza para comprobar que ninguno de los mensajes del protocolo de enlace se ha manipulado o dañado (lo que indica una posible infracción de seguridad).

Una vez recibidos los mensajes Finished y comprobados los hashes del protocolo de enlace, se inicia la sesión de TLS/DTLS y la aplicación comienza a enviar y recibir datos. En primer lugar, se aplica un algoritmo hash a todos los datos enviados desde cualquier lado durante la sesión de TLS/DTLS con el algoritmo hash elegido en los mensajes Hello (para proporcionar integridad del mensaje) y se cifran mediante el algoritmo de clave privada elegido con las claves de sesión generadas.

Por último, una sesión de TLS/DTLS solo se puede finalizar correctamente si el cliente o el servidor decide hacerlo. Una sesión truncada se considera una infracción de seguridad (ya que un atacante puede estar intentando impedir que se reciban todos los datos que se envían), por lo que se envía una notificación especial cuando uno de los lados desea finalizar la sesión (denominada alerta CloseNotify). Tanto el cliente como el servidor deben enviar y procesar una alerta CloseNotify para que se cierre correctamente la sesión.

![Diagrama de una sesión de protocolo de enlace DTLS típica.](media/image4.png)

**Figura 3: Protocolo de enlace DTLS típico**

### <a name="initialization"></a>Inicialización

La pila de NetX o NetXDuo debe inicializarse antes de usar el servicio DTLS de NetX Secure. Consulte la guía de usuario de NetX o NetXDuo para obtener información sobre cómo inicializar correctamente la pila TCP/IP para el funcionamiento de UDP.

Una vez inicializado UDP en NetX, se puede habilitar DTLS. Internamente, todo el tráfico de red y el procesamiento de DTLS se controla mediante la pila de NetX/NetXDuo sin necesidad de la intervención del usuario. Sin embargo, DTLS tiene algunos requisitos específicos que se deben controlar de forma independiente de la pila de red subyacente. En el cliente DTLS, estos parámetros se asignan al bloque de control de DTLS llamado ***NX_SECURE_DTLS_SESSION** _. En el servidor DTLS, el bloque de control se denomina _ *_NX_SECURE_DTLS_SERVER_** y contiene la infraestructura necesaria para controlar varias sesiones DTLS en un único puerto UDP; tenga en cuenta que esto es diferente en TLS, donde cada sesión de TLS está enlazada a un único puerto TCP.

Los dos modos de DTLS, servidor y cliente, pueden estar habilitados en una aplicación (pero solo un modo por socket NetX). Cada uno tiene sus propios requisitos específicos y se detallan a continuación.

### <a name="initialization--dtls-server"></a>Inicialización: Servidor DTLS

El modo de servidor del servicio DTLS de NetX Secure difiere del modo de servidor TLS debido al uso de UDP para el protocolo de transporte de red subyacente. Con TCP, el puerto se enlaza a un único host remoto mientras dure la sesión de TLS. UDP no tiene ninguna noción de estado con respecto al host remoto, por lo que todas las solicitudes de DTLS de distintos hosts se recibirán en la misma interfaz de UDP. Por lo tanto, DTLS debe mantener el estado de la sesión en lugar de confiar en el socket (como sucede con TLS y TCP). Por esta razón, el bloque de control del servidor DTLS (NX_SECURE_DTLS_SERVER) mantiene una asignación de información de host remoto (dirección IP y puerto) con las sesiones DTLS. Todos los datos entrantes en el socket UDP asignado a un servidor DTLS se asignarán a una sesión de DTLS existente o nueva basada en el host remoto. Por esta razón, la creación del servidor de DTLS requiere varios parámetros adicionales más allá de lo que los clientes de TLS y DTLS necesitan.

Además del bloque de control del servidor DTLS, los conjuntos de cifrado de TLS y el búfer de cifrado de ScratchSpace/metadatos, los servidores DTLS necesitan un búfer para mantener las sesiones de DTLS y un búfer de reensamblado de paquetes que se usa para descifrar los registros DTLS entrantes.

Además de los búferes de la sesión, los servidores DTLS requieren un *certificado digital* (que es un documento que se usa para identificar el servidor TLS en el cliente TLS de conexión) y los certificados de *clave privada* correspondientes (normalmente para el algoritmo de cifrado RSA). La norma International Telecommunications Union X.509 especifica el formato de certificado que usa TLS/DTLS y hay numerosas utilidades para crear certificados digitales X.509.

En el caso del servicio DTLS de NetX Secure, el certificado X.509 debe estar codificado de forma binaria con el formato de reglas de codificación distinguida (DER) de ASN.1. DER es el formato binario estándar TLS por cable para los certificados.

La clave privada asociada con el certificado proporcionado debe estar en formato PKCS#1 codificado mediante DER. La clave privada solo se usa en el dispositivo y nunca se transmitirá a través de la conexión. ¡Mantenga las claves privadas seguras, ya que proporcionan la seguridad de las comunicaciones TLS/DTLS!

Para inicializar el certificado de servidor DTLS, la aplicación debe proporcionar un puntero a un búfer que contenga el certificado X.509 codificado mediante DER y datos opcionales de clave privada RSA PKCS#1 codificados mediante DER con el servicio ***nx_secure_x509_certificate_intialize*** (que rellena la estructura de **NX_SECURE_X509_CERT** con los datos de certificado adecuados para su uso por parte de TLS).

Una vez inicializado el certificado de servidor, debe agregarse al bloque de control de TLS mediante el servicio ***nx_secure_dtls_server_local_certificate_add***.

Una vez agregado el certificado del servidor al bloque de control del servidor DTLS, el servidor se puede usar para proteger las comunicaciones de DTLS (consulte el ejemplo anterior).

### <a name="initialization--dtls-client"></a>Inicialización: Cliente DTLS

El modo de cliente DTLS de NetX Secure es sencillo en comparación con el del servidor DTLS, ya que solo hay una conexión saliente al host remoto a través del socket UDP.

Para configurar un cliente DTLS, se necesita un *almacén de certificados de confianza*, que es una colección de certificados digitales con codificación X.509 de las entidades de certificación de confianza (CA). El protocolo DTLS da por supuesto que estos certificados son “de confianza” y sirven como base para autenticar los certificados proporcionados por las entidades de servidor DTLS en la aplicación cliente de DTLS de NetX Secure.

Un certificado de CA de confianza puede ser *autofirmado* o firmado por otra CA, en cuyo caso el certificado se denomina de *CA intermedia* (ICA). En una aplicación TLS/DTLS típica, el servidor proporciona los certificados ICA junto con su certificado de servidor, pero el único requisito para la autenticación correcta es que se pueda realizar un seguimiento de una cadena de emisores (certificados usados para firmar otros certificados) desde el certificado de servidor a un certificado de CA de confianza en el almacén de certificados de confianza. Esta cadena se conoce como *cadena de confianza* o *cadena de certificados*.

Para inicializar un certificado de CA o ICA de confianza, la aplicación debe proporcionar un puntero a un búfer que contenga el certificado X.509 codificado mediante DER con el servicio **nx_secure_x509_certificate_intialize** (que rellena la estructura de *NX_SECURE_X509_CERT** con los datos de certificado adecuados para su uso por parte de TLS).

El cliente DTLS también necesita espacio para asignar el certificado de servidor entrante (suponiendo que no se use un modo de clave precompartida) y un búfer para ensamblar paquetes en registros de DTLS para descifrarlos. Estos búferes se pasan como parámetros al servicio ***nx_secure_dtls_session_create*** (consulte la referencia de la API para obtener más información).

Los certificados de confianza que se han inicializado se agregan a continuación al bloque de control de sesión de DTLS creado mediante el servicio ***nx_secure_dtls_session_trusted_certificate_add***. Si no se agrega un certificado, se producirá un error en la sesión de cliente DTLS, ya que no habrá forma de que el protocolo DTLS autentique los hosts de servidor remotos.

Una vez creado el almacén de certificados de confianza, la sesión se puede usar para establecer una conexión de cliente TLS segura.

### <a name="application-interface-calls"></a>Llamadas a la interfaz de la aplicación

Las aplicaciones DTLS de NetX Secure normalmente realizarán llamadas de función desde subprocesos de la aplicación que se ejecutan en ThreadX RTOS. Se puede llamar a cierta inicialización, especialmente para los protocolos de comunicaciones de red subyacentes (por ejemplo, UDP y IP), desde ***tx_application_define*.** Consulte la guía de usuario de NetX/NetXDuo para obtener más información sobre cómo inicializar las comunicaciones de red.

DTLS hace un uso intensivo de las rutinas de cifrado que son operaciones de uso intensivo del procesador. Por lo general, estas operaciones se realizarán en el contexto del subproceso que realiza la llamada.

### <a name="dtls-session-start"></a>Inicio de sesión de DTLS

DTLS requiere un protocolo de red de capa de transporte subyacente para poder funcionar. El protocolo que se usa normalmente es TCP. Para establecer una sesión de TLS de NetX Secure, se debe crear **NX_UDP_SOCKET** y pasarlo al servicio **_nx_secure_dtls_client_session_start_** para los clientes DTLS.

Los servidores DTLS funcionan de manera diferente. El socket UDP usado para las solicitudes entrantes de cliente DTLS se encuentra dentro del bloque de control NX_SECURE_DTLS_SERVER y se inicializa en la llamada a ***nx_secure_dtls_server_create** _, que toma el puerto UDP local como parámetro. El servicio _*_nx_secure_dtls_server_start_*_ se utiliza para iniciar el servidor DTLS con el fin de controlar las solicitudes entrantes. Todas las solicitudes entrantes se administran en rutinas de devolución de llamada proporcionadas a _nx_secure_dtls_server_create*: una para las conexiones y otra para las notificaciones de recepción. Depende de la aplicación controlar el inicio de la sesión de DTLS cuando se recibe una notificación de conexión (se invoca la devolución de llamada de notificación de conexión a través de DTLS) mediante una llamada a ***nx_secure_dtls_server_session_start**_. La aplicación también debe controlar los datos entrantes cuando se invoca la devolución de llamada de notificación de recepción (que sigue a un protocolo de enlace DTLS completado) mediante una llamada a _*_nx_secure_dtls_session_receive_**. Los detalles se proporcionan en el ejemplo anterior y en la referencia de la API para cada uno de los servicios mencionados anteriormente.

### <a name="dtls-packet-allocation"></a>Asignación de paquetes DTLS

El servicio DTLS de NetX Secure usa la misma estructura de paquetes que el protocolo TCP de NetX/NetXDuo (***NX_PACKET** _), salvo que, en lugar de llamar al servicio _*_nx_packet_allocate_*_, se debe llamar al servicio _ *_nx_secure_dtls_packet_allocate_** para que se pueda asignar correctamente el espacio para el encabezado DTLS.

### <a name="dtls-session-send"></a>Envío de sesión de DTLS

Una vez iniciada la sesión TLS, la aplicación puede enviar datos mediante el servicio ***nx_secure_dtls_session_send***. El uso del servicio de envío es idéntico para el servicio ***nx_udp_socket_send** _, que toma una estructura de datos _ *_NX_PACKET_** con los datos que se envían, una dirección IP de destino y un puerto UDP de destino.

> [!IMPORTANT]
> Al enviar datos mediante nx_secure_dtls_session_send, es importante usar la misma dirección IP y el mismo puerto que se usaron para establecer la sesión de DTLS, a menos que haya un mecanismo para pasar la sesión a una nueva dirección y puerto UDP sobre la marcha (esto no es habitual).

Los datos enviados a través de DTLS se cifrarán mediante la pila DTLS de NX Secure y las rutinas de cifrado configuradas antes de enviarse.

### <a name="dtls-session-receive"></a>Recepción de sesión de DTLS

Una vez iniciada la sesión de DTLS, la aplicación puede empezar a recibir datos mediante el servicio ***nx_secure_Dtls_session_receive** _. Al igual que el envío de la sesión de DTLS, este servicio se usa exactamente igual que _*_nx_udp_socket_receive_**, con la salvedad de que la pila DTLS descifra y comprueba los datos entrantes antes de que se devuelvan en la estructura de paquetes.

### <a name="tls-session-close"></a>Cierre de sesión de TLS

Una vez completada una sesión de DTLS, tanto el cliente como el servidor DTLS deben enviar una alerta CloseNotify al otro lado para cerrar la sesión. Ambos lados deben recibir y procesar la alerta para asegurarse de que el cierre de sesión se ha realizado correctamente.

Si el host remoto envía una alerta CloseNotify, todas las llamadas al servicio ***nx_secure_dtls_session_receive** _ procesarán la alerta, enviarán de nuevo la alerta correspondiente al host remoto y devolverán un valor de _*_NX_SECURE_TLS_SESSION_CLOSED_**. Una vez cerrada la sesión, se producirá un error en cualquier intento adicional de enviar o recibir datos con esa sesión de DTLS.

Si la aplicación desea cerrar la sesión de TLS, se debe llamar al servicio ***nx_secure_dtls_session_end** _. El servicio enviará la alerta CloseNotify y procesará la respuesta CloseNotify. Si no se recibe la respuesta, se devolverá un valor de error de _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_**, lo que indica que la sesión de DTLS no se apagó correctamente y puede indicar una posible infracción de seguridad.

### <a name="tlsdtls-alerts"></a>Alertas TLS/DTLS

TLS/DTLS está diseñado para proporcionar la máxima seguridad, por lo que cualquier comportamiento errante en el protocolo se considera una posible infracción de seguridad. Por esta razón, los errores en el procesamiento de mensajes o el cifrado y descifrado se consideran errores irrecuperables que finalizan la sesión o el protocolo de enlace inmediatamente.

Aunque el control de errores en una aplicación local es relativamente sencillo, el host remoto debe saber que se ha producido un error con el fin de controlar correctamente la situación y evitar posibles infracciones de seguridad. Por esta razón, TLS/DTLS enviará un mensaje de *alerta* al host remoto en caso de error.

Las alertas se tratan de la misma manera que cualquier otro mensaje de TLS/DTLS y se cifran durante la sesión para impedir que un atacante recopile información del tipo de alerta proporcionado. Durante el protocolo de enlace, el ámbito de las alertas enviadas está limitado para controlar la cantidad de información que podría obtener un atacante potencial.

La alerta CloseNotify, que se usa para cerrar la sesión de TLS/DTLS, es la única alerta no grave. Aunque se considera una alerta y se envía como un mensaje de alerta, CloseNotify es diferente de otras alertas, ya que no indica que se ha producido un error.

### <a name="tlsdtls-session-renegotiation-and-resumption"></a>Renegociación y reanudación de la sesión de TLS/DTLS

TLS admite la noción de “renegociación”, que es simplemente una renegociación de los parámetros de sesión de TLS en el contexto de una sesión de TLS existente.

A pesar de tener ciertas similitudes, la *reanudación* de la sesión TLS no se debe confundir con la *renegociación* de la sesión. En los casos en que la *renegociación* de la sesión implica iniciar un nuevo protocolo de enlace dentro de una sesión de TLS existente, la *reanudación* de la sesión es una característica puramente opcional que implica el reinicio de una sesión de TLS cerrada sin necesidad de realizar un protocolo de enlace TLS completo.

El servicio DTLS de NX Secure controla las solicitudes de renegociación entrantes de hosts remotos. **No** admite la reanudación de la sesión. Encontrará una explicación más completa de estas características en el capítulo 3 de la guía de usuario del servicio TLS de NetX Secure.

### <a name="protocol-layering"></a>Capas de protocolo

El protocolo TLS (y, por lo tanto, también DTLS) encaja en la pila de red entre la capa de transporte (por ejemplo, TCP o UDP) y la capa de aplicación. TLS se considera a veces un protocolo de capa de transporte (de ahí su nombre: seguridad de la *capa de transporte*), pero dado que actúa como una aplicación con respecto a los protocolos de red subyacentes, a veces se agrupa en la capa de aplicación.

TLS requiere un protocolo de capa de transporte que admita la entrega en orden y sin pérdidas, como TCP. Debido a este requisito, no se puede ejecutar TLS sobre UDP, ya que UDP no garantiza la entrega de datagramas. *DTLS* es una versión modificada de TLS que se utiliza para las aplicaciones que necesitan la seguridad de TLS a través de un protocolo de datagramas como UDP.

![Diagrama de las capas de un protocolo TLS.](media/image6.png)

**Figura 4: Capas de protocolo TCP/IP, UDP y TLS/DTLS**

## <a name="network-communications-security-and-encryption"></a>Seguridad y cifrado de las comunicaciones de red

La protección de las comunicaciones a través de redes públicas e Internet es un tema muy importante y es protagonista de una gran cantidad de libros, artículos y soluciones. El tema es el increíblemente complejo, pero se puede reducir a una idea sencilla: enviar información a través de una red para que solo el destinatario previsto pueda acceder a la información o cambiarla. Esto se divide en tres conceptos importantes: confidencialidad, integridad y autenticación. El protocolo TLS/DTLS proporciona soluciones para los tres.

El cifrado se usa de maneras diferentes para proporcionar confidencialidad, integridad y autenticación dentro de los protocolos TLS y DTLS. El cifrado debe proporcionarse a TLS o DTLS tras la creación de una sesión o una instancia del servidor, ya que TLS ofrece un marco flexible para usar el cifrado y no el propio cifrado. El servicio DTLS de NetX Secure proporciona las rutinas de cifrado necesarias para la mayoría de las aplicaciones, por lo que no tiene que preocuparse de encontrar el cifrado adecuado.

Puede encontrar una descripción más detallada de estos temas en el capítulo 3 de la guía de usuario del servicio TLS de NetX Secure.

## <a name="tls-and-dtls-extensions"></a>Extensiones de TLS y DTLS

TLS (y, por tanto, DTLS) incluyen una serie de extensiones que ofrecen funcionalidad adicional para ciertas aplicaciones. Normalmente, estas extensiones se envían como parte de los mensajes ClientHello o ServerHello, lo que indica a un host remoto el deseo de usar una extensión o proporciona detalles adicionales para su uso en el establecimiento de la sesión de TLS segura.

El servicio DTLS de NetX Secure admite todas las extensiones del servicio TLS de NetX Secure. Encontrará una descripción completa de las extensiones en el capítulo 3 de la guía de usuario del servicio TLS de NetX Secure.

## <a name="authentication-methods"></a>Métodos de autenticación

TLS y DTLS proporcionan el marco para establecer una conexión segura entre dos dispositivos a través de una red no segura, pero parte del problema es conocer la identidad del dispositivo en el otro extremo de la conexión. Sin un mecanismo para autenticar la identidad de los hosts remotos, un atacante podría hacerse pasar por un dispositivo de confianza sin el más mínimo esfuerzo.

Inicialmente, puede parecer que el uso de direcciones IP, direcciones MAC de hardware o DNS, proporcionarán un nivel relativamente alto de confianza para identificar hosts en una red, pero dada la naturaleza de la tecnología TCP/IP, la facilidad con la que se pueden suplantar las direcciones y dañarse las entradas DNS (por ejemplo, a través de la infección de la caché DNS), queda claro que TLS necesita una capa adicional de protección.

Hay varios mecanismos que pueden proporcionar esta capa adicional de autenticación para TLS, pero el *certificado digital* es el más común. Otros mecanismos incluyen las claves precompartidas (PSK) y los esquemas de contraseña.

### <a name="digital-cerificates"></a>Certificados digitales

Los certificados digitales son el método más común para autenticar un host remoto en TLS. Esencialmente, un certificado digital es un documento con un formato específico que proporciona información de identidad para un dispositivo en una red de equipos.

TLS normalmente usa un formato denominado X.509, un estándar desarrollado por la International Telecommunication Union, aunque se pueden usar otros formatos de certificados si los hosts de TLS acuerdan el formato usado. X.509 define un formato específico para los certificados y diversas codificaciones que se pueden utilizar para generar un documento digital. La mayoría de los certificados X.509 que se usan con TLS se codifican mediante una variante de ASN.1, otro estándar de telecomunicaciones. En ASN.1 hay varias codificaciones digitales, pero la codificación más común de los certificados TLS es el estándar de reglas de codificación distinguida (DER). DER es un subconjunto simplificado de las reglas de codificación básicas (BER) de ASN.1 que están diseñadas para ser inequívocas, lo que facilita el análisis. A través de la conexión, los certificados TLS normalmente están codificados en DER binario y este es el formato que NetX Secure espera para los certificados X.509.

Aunque los certificados binarios con formato DER se usan en el protocolo TLS real, se pueden generar y almacenar en varias codificaciones diferentes, con extensiones de archivo como. pem, .crt y .p12. Las distintas variantes las usan diferentes aplicaciones de distintos fabricantes, pero generalmente todas se pueden convertir en DER mediante herramientas ampliamente disponibles.

La más común de las codificaciones alternativas de certificados es PEM. El formato PEM (Privacy-Enhanced Mail, correo con privacidad mejorada) es una versión codificada en base 64 de la codificación DER que se usa a menudo porque la codificación da como resultado texto imprimible que se puede enviar fácilmente mediante correo electrónico o protocolos basados en Web.

La generación de un certificado para la aplicación de NetX Secure suele estar fuera del ámbito de este manual, pero la herramienta de línea de comandos de OpenSSL ([www.openssl.org](http://www.openssl.org)) está ampliamente disponible y puede realizar la conversión entre la mayoría de los formatos.

En función de la aplicación, puede generar sus propios certificados, proporcionar certificados por un fabricante o una organización gubernamental, o adquirir certificados de una entidad de certificación comercial.

Para usar un certificado digital en la aplicación de NetX Secure, primero debe convertir el certificado a un formato binario DER y, opcionalmente, convertir la clave privada asociada (el “exponente privado” en RSA, por ejemplo) en formato binario, normalmente una clave RSA con formato PKCS#1 y con codificación DER. Una vez finalizada la conversión, depende de usted cargar el certificado y la clave privada en el dispositivo. Entre las opciones posibles se incluyen el uso de un sistema de archivos basado en Flash o la generación de una matriz C a partir de los datos (mediante una herramienta como “XXD” desde Linux) y la compilación del certificado y la clave en la aplicación como datos constantes.

Una vez que el certificado se carga en el dispositivo, se puede usar la API de DTLS para asociar el certificado a una sesión o un servidor DTLS.

Para obtener más información y ejemplos sobre cómo usar los certificados X.509 con el servicio DTLS de NetX Secure, consulte la sección “Importación de certificados X.509 en NetX Secure” en la guía de usuario del servicio TLS de NetX Secure.

Consulte los siguientes servicios DTLS en la referencia de la API para obtener más información:

- nx_secure_x509_certificate_initialize,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_dtls_server_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Detalles de certificados de cliente TLS

Las implementaciones de cliente DTLS generalmente no requieren la carga de un certificado local en el dispositivo. Un certificado local es un certificado que identifica el dispositivo local. En concreto, un certificado local proporciona información de identidad para el dispositivo en el que se carga la aplicación TLS/DTLS. Hay una excepción: cuando está habilitada la autenticación de certificados de cliente, pero este supuesto es menos frecuente.

Un cliente DTLS requiere que se cargue al menos un certificado de confianza (es posible que se carguen más, si es necesario) y espacio para que se asigne un certificado remoto. Un certificado de confianza es un certificado que proporciona una base de confianza y autenticación del dispositivo remoto, ya sea directamente o a través de una infraestructura de clave pública (PKI). La raíz de la cadena de confianza se denomina normalmente entidad de certificación o certificado de CA. Un certificado remoto hace referencia al certificado enviado por el host remoto durante el protocolo de enlace TLS. Proporciona identidad para ese host remoto y se autentica mediante su comparación con un certificado de confianza en el dispositivo local.

Para obtener más información sobre cómo agregar certificados de confianza y asignar espacio para los certificados remotos, consulte la referencia de la API de TLS para los siguientes servicios: nx_secure_dtls_session_create, nx_secure_dtls_session_trusted_certificate_add.

### <a name="tlsdtls-server-certificate-specifics"></a>Detalles de certificados de servidor TLS/DTLS

Por lo general, las implementaciones de servidor DTLS no requieren la carga de certificados de “confianza” en el dispositivo o los certificados remotos que se van a asignar. Hay una excepción: cuando está habilitada la autenticación de certificados de cliente.

Un servidor TLS requiere la carga de un certificado “local” (o “identidad”) para que el servidor pueda proporcionarlo al cliente remoto durante el protocolo de enlace TLS para autenticar el servidor en el cliente.

Para obtener más información sobre la carga de certificados locales para su uso con aplicaciones de servidor TLS de NetX, consulte la referencia de la API para los siguientes servicios: nx_secure_dtls_server_local_certificate_add, nx_secure_dtls_server_local_certificate_remove.


### <a name="pre-shared-keys-psk"></a>Claves precompartidas (PSK)

Un mecanismo alternativo para proporcionar autenticación de identificación en TLS es la noción de claves precompartidas (PSK). Usar un conjunto de cifrado PSK elimina la necesidad de realizar las operaciones de cifrado de clave pública de uso intensivo del procesador, una ventaja para los dispositivos integrados con restricción de recursos. La PSK reemplaza el certificado en el protocolo de enlace TLS/DTLS y se usa en lugar del secreto premaestro cifrado para la generación de claves de sesión TLS/DTLS.

Las conjuntos de PSK están limitados en el sentido de que un secreto compartido debe estar presente en ambos dispositivos antes de que se pueda establecer una sesión de TLS/DTLS. Esto significa que los dispositivos se deben haber cargado con ese secreto mediante el uso de algunos medios seguros distintos, no solo mediante una conexión TLS con PSK. La PSK se puede actualizar a través de una conexión de TLS con PSK, pero el dispositivo debe comenzar con una PSK que se carga a través de otro mecanismo. Por ejemplo, se podría cargar un dispositivo de sensor y su dispositivo de puerta de enlace con PSK en la fábrica antes del envío, o bien se podría usar una conexión TLS estándar (con un certificado) para cargar la PSK.

Los conjuntos de cifrado PSK se presentan en un par de formatos, que se describe en la RFC 4279. El primero usa las claves RSA o Diffie-Hellman que se usan de la misma manera que las claves públicas transmitidas en el certificado en los protocolos de enlace TLS estándar. El segundo, que se usa más en un entorno con restricción de recursos, utiliza una PSK que se utiliza para generar directamente las claves de sesión (para su uso con AES, por ejemplo), evitando así las costosas operaciones de Diffie-Hellman o RSA.

NetX Secure admite el segundo formato de conjuntos de cifrado PSK, lo que permite que las aplicaciones quiten todo el código de criptografía de clave pública y el uso de memoria. La PSK no es una clave AES, pero se puede considerar como una contraseña de la que se generan las claves reales. Existen algunas restricciones en lo que puede ser el valor de PSK, aunque los valores más largos proporcionarán más seguridad (igual que con las contraseñas).

Para usar PSK con la aplicación de NetX Secure, primero debe definir la macro global **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Normalmente esto se realiza a través de la configuración del compilador, pero la definición también se puede colocar en el archivo de encabezado nx_secure_tls.h. Con la macro definida, la compatibilidad del conjunto de cifrado PSK se compilará en la aplicación DTLS de NetX Secure.

Con la compatibilidad con PSK habilitada, puede usar la API de DTLS para configurar PSK para la aplicación. Cada PSK requerirá un valor de PSK (la “clave” secreta real que debe mantener a salvo), un valor de “identidad” que se usa para identificar la PSK específica y una “sugerencia de identidad” que se usa en un servidor TLS para elegir un valor de PSK determinado.

La PSK puede ser cualquier valor binario, ya que nunca se envía a través de una conexión de red. La PSK puede tener cualquier valor de hasta 64 bytes de longitud.

La identidad y la sugerencia deben ser cadenas de caracteres imprimibles con formato UTF-8. Los valores de identidad y sugerencia pueden tener una longitud de hasta 128 bytes.

La identidad y la PSK forman un par único que se carga en todos los dispositivos de la red que necesitan comunicarse entre sí.

La “sugerencia” se usa principalmente para definir perfiles de aplicación específicos para agrupar PSK por función o servicio. Estos valores se deben acordar de antemano y dependen de la aplicación. Por ejemplo, la aplicación de servidor de línea de comandos de OpenSSL (con PSK habilitado) utiliza la cadena predeterminada “Client_identity” que debe proporcionar un cliente TLS para continuar con el protocolo de enlace TLS.

Para obtener más información sobre las PSK, consulte la referencia de la API de NetX Secure para los siguientes servicios: nx_secure_dtls_psk_add, nx_secure_dtls_server_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importación de certificados X.509 en NetX Secure

Los certificados digitales son necesarios para la mayoría de las conexiones TLS en Internet. Los certificados proporcionan un método para autenticar hosts desconocidos previamente a través de Internet mediante el uso de intermediarios de confianza, normalmente denominados *entidades de certificación* o CA. Para conectar el dispositivo NetX Seguro con un servicio en la nube comercial (por ejemplo, Amazon Web Services), deberá importar los certificados en la aplicación si los carga en el dispositivo.

Además de los certificados, también necesitará una *clave privada* que esté asociada con el certificado. En algunas aplicaciones (como el cliente TLS cuando no se utiliza la autenticación de certificados de cliente), bastará con el certificado, pero si el certificado se usa para identificar el dispositivo, necesitará una clave privada. Las claves privadas normalmente se generan al crear el certificado y se almacenan en un archivo independiente (que a menudo cifrado con una contraseña).

Para obtener una descripción detallada de la importación de certificados a aplicaciones de NetX Secure, consulte el capítulo 3 de la guía de usuario del servicio TLS de NetX Secure.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Autenticación de certificados de cliente en el servicio TLS de NetX Secure

Al usar la autenticación de certificados X.509, el protocolo TLS/DTLS requiere que la instancia del servidor DTLS proporcione un certificado para la identificación. Sin embargo, de forma predeterminada, la instancia de cliente DTLS no tiene que proporcionar un certificado para la autenticación y puede usar otra forma de autenticación (por ejemplo, una combinación de nombre de usuario/contraseña). Esto coincide con el uso más común de TLS para sitios Web en Internet. Por ejemplo, un sitio de venta directa en línea debe demostrar a un cliente potencial que use un explorador Web que el servidor es legítimo, pero el usuario empleará un inicio de sesión y una contraseña para tener acceso a una cuenta específica.

Sin embargo, el caso predeterminado no siempre es el aconsejable, por lo que TLS/DTLS permite a la instancia del servidor DTLS solicitar un certificado del cliente remoto. Cuando esta característica está habilitada, el servidor DTLS enviará un mensaje CertificateRequest al cliente DTLS durante el protocolo de enlace. El cliente debe responder con un certificado propio y un mensaje CertificateVerify que contenga un token criptográfico que demuestre que el cliente posee la clave privada correspondiente asociada a ese certificado. Si se produce un error en la comprobación o el certificado no está conectado a un certificado de confianza en el servidor, se produce un error en el protocolo de enlace TLS.

Hay dos casos independientes para la autenticación de certificados de cliente en TLS: en las secciones siguientes se tratan ambos casos.

### <a name="client-certificate-authentication-for-dtls-clients"></a>Autenticación de certificados de cliente para clientes DTLS

Un cliente DTLS puede intentar una conexión a un servidor que solicite un certificado para la autenticación del cliente. En este caso, el cliente debe proporcionar un certificado al servidor y comprobar que posee la clave privada correspondiente; si no, el servidor finalizará el protocolo de enlace DTLS.

En el servicio DTLS de NetX Secure, no hay ninguna configuración especial para admitir esta característica, pero la aplicación tendrá que proporcionar un certificado de identificación local para la instancia de cliente TLS mediante el servicio *nx_secure_tls_session_local_certificate_add*. Si la aplicación no proporciona ningún certificado pero el servidor remoto usa la autenticación de certificado de cliente y solicita un certificado, se producirá un error en el protocolo de enlace DTLS. El servidor remoto debe reconocer el certificado proporcionado a la sesión DTLS con *nx_secure_dtls_session_local_certificate_add* para poder completar el protocolo de enlace DTLS.

### <a name="client-certificate-authentication-for-tls-servers"></a>Autenticación de certificados de cliente para servidores DTLS

El caso del servidor DTLS para la autenticación de certificados de cliente es ligeramente más complejo que el caso del cliente DTLS, ya que la característica es opcional. En este caso, el servidor TLS necesita solicitar específicamente un certificado de cliente TLS remoto y, seguidamente, procesar el mensaje CertificateVerify para comprobar que el cliente remoto es el propietario de la clave privada correspondiente. A continuación, el servidor debe comprobar que se puede realizar un seguimiento del certificado proporcionado por el cliente hasta un certificado del almacén local de certificados de confianza.

En las instancias del servidor TLS seguras, la autenticación de certificados de cliente se controla mediante los servicios *nx_secure_dtls_server_x509_client_verify_configure* y *nx_secure_dtls_server_x509_client_verify_disable*.

Para habilitar la autenticación de certificados de cliente, una aplicación debe llamar a *nx_secure_dtls_server_x509_client_verify_configure* con la instancia de sesión de servidor DTLS antes de llamar a *nx_secure_dtls_server_start*. La comprobación requiere que se asigne espacio para los certificados de cliente entrantes que se proporciona como parámetro para *nx_secure_dtls_server_x509_client_verify_configure.* Tenga en cuenta que el búfer debe ser lo suficientemente grande para contener la cadena de certificados de tamaño máximo proporcionada por un cliente *veces el número de sesiones del servidor de DTLS*. Cada sesión de servidor requiere espacio que se asignará desde el búfer proporcionado único. Asegúrese de que el búfer es suficientemente grande o se producirá un error si la cadena de certificados de cliente proporcionada es demasiado grande.

Cuando se habilita la autenticación de certificados de cliente, el servidor DTLS solicitará un certificado de cliente DTLS remoto durante el protocolo de enlace DTLS. En el servidor DTLS de NetX Secure, el certificado de cliente se compara con el almacén de certificados de confianza creados con *nx_secure_dtls_server_trusted_certificate_add* siguiendo la cadena de emisor X.509. El cliente remoto debe proporcionar una cadena que conecte su certificado de identidad con un certificado en el almacén de confianza; de lo contrario, se producirá un error en el protocolo de enlace DTLS. Además, si se produce un error en el procesamiento del mensaje CertificateVerify, también se producirá un error en el protocolo de enlace DTLS.

Los métodos de firma que se usan para el método CertificateVerify son fijos para la versión de TLS 1.0 y la versión TLS 1.1; se especifican mediante el servidor TLS en la versión TLS 1.2, en el que se basa el servicio DTLS de NetX Secure. En el caso de DTLS 1.2, los métodos de firma admitidos generalmente siguen los métodos pertinentes suministrados en la tabla de métodos criptográficos, pero normalmente RSA con SHA-256 (consulte la sección “Criptografía el servicio TLS de NetX Secure” para obtener más información sobre cómo inicializar TLS con métodos criptográficos).

## <a name="cryptography-in-netx-secure-tls"></a>Criptografía en el servicio TLS de NetX Secure

TLS define un protocolo en el que se puede usar la criptografía para proteger las comunicaciones de red. Como tal, permite que los usuarios de TLS puedan usar el cifrado real de forma bastante amplia. La especificación solo requiere la implementación de un único conjunto de cifrado. En el caso de TLS 1.2, el conjunto es TLS_RSA_WITH_AES_128_CBC_SHA, que indica el uso de RSA para las operaciones de clave pública, AES en modo CBC con claves de 128 bits para el cifrado de sesión y SHA-1 para los hash de autenticación de mensajes.

Al ser compatible con TLS 1.2, NetX Secure habilita el conjunto de cifrado obligatorio TLS_RSA_WITH_AES_128_CBC_SHA de forma predeterminada, pero dado el número de implementaciones posibles para cada uno de los métodos criptográficos debido a las capacidades de hardware y otras consideraciones, NetX Secure proporciona una API criptográfica genérica que permite a los usuarios especificar qué métodos criptográficos usar con TLS.

> [!NOTE]
> El mecanismo genérico de la API criptográfica también permite a los usuarios implementar sus propios conjuntos, pero esto solo se recomienda a los usuarios avanzados que están familiarizados con las extensiones y conjuntos de cifrado de TLS. Póngase en contacto con su representante de Logic Express si está interesado en usar sus propios conjuntos de cifrado.

Consulte el capítulo 3 de la guía de usuario del servicio TLS de NetX Secure para ver una explicación detallada sobre cómo configurar los métodos criptográficos para DTLS. El mismo proceso se aplica tanto a TLS como a DTLS.
