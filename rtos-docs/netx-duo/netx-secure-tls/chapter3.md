---
title: 'Capítulo 3: Descripción funcional de Azure RTOS NetX Secure'
description: Este capítulo contiene una descripción funcional del servicio TLS de NetX Secure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c28ad0255f99986a4ddfe5faefad81e70840e5e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814510"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-secure"></a>Capítulo 3: Descripción funcional de Azure RTOS NetX Secure

## <a name="execution-overview"></a>Información general sobre la ejecución

Este capítulo contiene una descripción funcional del servicio TLS de Azure RTOS NetX Secure. Hay dos tipos principales de ejecución de programa en una aplicación TLS de NetX Secure: inicialización y llamadas a la interfaz de la aplicación. 

*NetX Secure presupone la existencia de ThreadX y NetX/NetXDuo. En ThreadX, se requiere la ejecución de subprocesos, la suspensión, temporizadores periódicos y las instalaciones de exclusión mutua. En NetX/NetXDuo, se necesitan los controladores y los dispositivos de red TCP/IP.*

## <a name="transport-layer-security-tls-and-secure-sockets-layer-ssl"></a>Seguridad de la capa de transporte (TLS) y Capa de sockets seguros (SSL)

El componente de protocolo de red seguro de NetX Secure es una implementación del protocolo de seguridad de la capa de transporte (TLS), tal como se describe en la RFC 2246 (versión 1.0), 4346 (versión 1.1), 5246 (versión 1.2) y 8446 (versión 1.3). También se incluyen rutinas de soporte técnico para X.509 básico (RFC 5280).

El servicio TLS de NetX Secure es compatible con las versiones TLS 1.2 y 1.3. Se proporcionan implementaciones para TLS 1.0 y TLS 1.1 en desuso, pero se deben inicializar explícitamente y no se recomienda su uso en nuevos productos.

*Capa de sockets seguros* (SSL) era el nombre original de TLS antes de que se convirtiera en un estándar en la RFC 2246 y “SSL” se utiliza a menudo como nombre genérico para los protocolos TLS. La última versión de SSL era 3.0 y TLS 1.0 a veces se denomina SSL 3.1. Todas las versiones del protocolo “SSL” oficial se consideran obsoletas y no seguras; actualmente NetX Secure no ofrece una implementación de SSL.

TLS especifica un protocolo para generar *claves de sesión* que se crean durante *el protocolo de enlace* de TLS entre un cliente y un servidor de TLS, y dichas claves se utilizan para cifrar los datos enviados por la aplicación durante la *sesión* de TLS.

Los datos de TLS se dividen en *registros* que, conceptualmente, son equivalentes a un paquete TCP. Cada registro TLS tiene un encabezado y los registros cifrados TLS también tienen un pie de página (hash de suma de comprobación). Los registros de protocolo de enlace TLS tienen un encabezado adicional encapsulado en el registro TLS más grande. El registro TLS está encapsulado por el protocolo de red de la capa de transporte de la misma manera que un paquete TCP está encapsulado por un paquete IP.

### <a name="tls-13"></a>TLS 1.3

En agosto de 2018 finalizó la especificación TLS 1.3. La nueva versión del protocolo es una actualización bastante significativa que cambia algunos aspectos fundamentales de la seguridad y el rendimiento subyacentes de TLS. Sin embargo, estos cambios son en gran medida invisibles para el usuario típico de TLS, ya que se aplican principalmente a la máquina de estados del protocolo de enlace TLS y a la generación de claves de sesión. También se agregaron varias características y extensiones opcionales. A continuación puede ver un resumen de los cambios y cómo afectan a la funcionalidad de TLS.

- La máquina de estados del protocolo de enlace se optimizó eliminando un intercambio completo de mensajes por parte del servidor.
- La generación de claves se actualizó para usar una rutina normalizada denominada HKDF (función de derivación de claves basada en HMAC) y vincula las claves de sesión a todos los mensajes de protocolo de enlace (en lugar de algunos parámetros de selección).
- Todos los conjuntos de cifrado de TLS 1.2 y anteriores están en desuso y son incompatibles con TLS 1.3. Del mismo modo, ningún conjunto de cifrado de TLS 1.3 se puede usar con versiones anteriores.
- Todos los conjuntos de cifrado de TLS 1.3 proporcionan confidencialidad directa total (PFS) mediante claves efímeras<sup>6</sup>. 
- TLS 1.3 quita el “código de autenticación de mensajes” (MAC) de cada registro en favor del uso de cifrados de AEAD<sup>7</sup>.
- Se han agregado algunas características opcionales adicionales, incluido 0-RTT (tiempo de ida y vuelta cero), lo que permite que los datos de la aplicación se envíen durante el protocolo de enlace. 0: RTT es puramente opcional y no se admite actualmente en Azure RTOS TLS.

TLS 1.3 no afecta significativamente a las aplicaciones del usuario. La API se mantiene exactamente igual entre las distintas versiones y los conjuntos de cifrado se marcan para que se pueda usar una sola tabla de conjuntos de cifrado.

Para usar TLS 1.3, la macro NX_SECURE_TLS_ENABLE_TLS_1_3 debe estar definida globalmente. TLS 1.3 está deshabilitado de forma predeterminada en Azure RTOS TLS.

6. Las claves “efímeras” son pares de claves asimétricas que se generan durante el protocolo de enlace TLS y que se usan para el intercambio de secretos solo para esa sesión. Estos pares de claves se descartan después de su uso. Esto impide que un atacante pueda acceder a los datos cifrados en una sesión TLS registrada, incluso si una clave privada de certificado se ve comprometida en cualquier momento en el futuro (de ahí el nombre “confidencialidad directa total”).

7. Cifrado autenticado con datos asociados: modo de cifrado como AES que combina el cifrado y la comprobación de la integridad en una sola operación, lo que elimina la necesidad de un hash independiente de los datos para la comprobación de la integridad.

### <a name="tls-record-header"></a>Encabezado de registro TLS

Un registros TLS válido debe tener un encabezado TLS, como se muestra en Error! Reference source not found.

![Diagrama de un encabezado de registro TLS.](media/image2.png)

Figura 1: Encabezado de registro TLS

Los campos del encabezado de registro TLS se definen de la siguiente manera:

| Campo de encabezado TLS | Propósito     |
| ---------------- | ------------- |
| **Tipo de mensaje de 8 bits** | Este campo contiene el tipo de registro TLS que se está enviando. Los tipos válidos son los siguientes:<br />- ChangeCipherSpec<sup>8</sup>: 0x14<br />- Alert: 0x15<br />- Handshake: 0x16<br />- ApplicationData: 0x17 |
| **Versión del protocolo de 16 bits** | Este campo contiene la versión del protocolo TLS. Los valores válidos son los siguientes:<br />- SSL 3.0: 0x0300<br />- TLS 1.0: 0x0301<br />- TLS 1.1: 0x0302<br />- TLS 1.2: 0x0303<br />- **TLS 1.3 <sup>9</sup>** : **0x0303** |
| **Longitud de 16 bits** | Este campo contiene la longitud de los datos encapsulados en el registro TLS. |

8. En TLS 1.3 ya no se utiliza el mensaje ChangeCipherSpec, aunque se puede enviar por motivos de compatibilidad (en cuyo caso se omite el mensaje).

9. Técnicamente, TLS 1.3 tendría un valor de 0x0304 si este esquema continuase, pero el protocolo se cambió para tener la versión de protocolo real en una extensión, por lo que todos los registros de TLS 1.3 usan 0x0303 en los campos de versión de protocolo para ser compatibles con versiones anteriores.

### <a name="tls-handshake-record-header"></a>Encabezado de registro de protocolo de enlace TLS

Cualquier registro de protocolo de enlace TLS válido debe tener un encabezado de protocolo de enlace TLS, como se muestra en la figura 2.

![Diagrama de un encabezado de registro de protocolo de enlace TLS.](media/image3.png)

Figura 2: Encabezado de registro de protocolo de enlace TLS

Los campos del encabezado de registro de protocolo de enlace TLS se definen de la siguiente manera:

| Campo de encabezado TLS | Propósito |
| ---------------- |----------------------- |
| **Tipo de mensaje de 8 bits** | Este campo contiene el tipo de registro TLS que se está enviando. Los tipos válidos son los siguientes:<br />- ChangeCipherSpec<sup>10</sup>: 0x14<br />- Alert: 0x15<br />- Handshake: 0x16<br />- ApplicationData: 0x17 |
| **Versión del protocolo de 16 bits** | Este campo contiene la versión del protocolo TLS. Los valores válidos son los siguientes:<br />- SSL 3.0: 0x0300<br />- TLS 1.0: 0x0301<br />- TLS 1.1: 0x0302<br />- TLS 1.2: 0x0303<br />- **TLS 1.3 <sup>11</sup>** : **0x0303** |
| **Longitud de 16 bits**    | Este campo contiene la longitud de los datos encapsulados en el registro TLS. |
| **Tipo de protocolo de enlace de 8 bits** | Este campo contiene el tipo de mensaje del protocolo de enlace. Los valores válidos son los siguientes (*los mensajes en **negrita** se han agregado en TLS 1.3):<br />- HelloRequest: 0x00<br />- ClientHello: 0x01<br />- ServerHello: 0x02<br />- **HelloVerifyRequest**: **0x03**<br />- **NewSessionTicket**: **0x04**<br />- **EndOfEarlyData**: **0x05**<br />- **EncryptedExtensions**: **0x08**<br />- Certificate: 0x0B<br />- ServerKeyExchange: 0x0C<br />- CertificateRequest: 0x0D<br />- ServerHelloDone: 0x0E<br />- CertificateVerify: 0x0F<br />- ClientKeyExchange: 0x10<br />- Finished: 0x14<br />- **KeyUpdate**: **0x18**<br />- **MessageHash**: **0xFE** |
| **Longitud de 24 bits**    | Este campo contiene la longitud de los datos del mensaje del protocolo de enlace. |

10. En TLS 1.3 ya no se utiliza el mensaje ChangeCipherSpec, aunque se puede enviar por motivos de compatibilidad (en cuyo caso se omite el mensaje).

11. Técnicamente, TLS 1.3 tendría un valor de 0x0304 si este esquema continuase, pero el protocolo se cambió para tener la versión de protocolo real en una extensión, por lo que todos los registros de TLS 1.3 usan 0x0303 en los campos de versión de protocolo para ser compatibles con versiones anteriores.

### <a name="the-tls-handshake-and-tls-session"></a>El protocolo de enlace TLS y la sesión TLS

En la figura 3 se muestra un protocolo de enlace TLS típico (versiones 1.0-1.2). Un protocolo de enlace TLS comienza cuando el cliente envía un mensaje *ClientHello* a un servidor TLS e indica su deseo de iniciar una sesión de TLS. El mensaje contiene información sobre el cifrado que el cliente desea utilizar para la sesión, junto con la información utilizada para generar las claves de sesión más adelante en el protocolo de enlace. Hasta que no se generen las claves de sesión, no se cifrarán todos los mensajes del protocolo de enlace TLS. TLS 1.3 cambia el protocolo de enlace: los detalles se muestran en la sección siguiente.

El servidor TLS responde a ClientHello con un mensaje ServerHello, lo que indica una selección de las opciones de cifrado proporcionadas por el cliente. ServerHello va seguido de un mensaje de certificado en el que el servidor proporciona un certificado digital para autenticar su identidad en el cliente. Por último, el servidor envía un mensaje ServerHelloDone para indicar que no tiene más mensajes para enviar. Opcionalmente, el servidor puede enviar otros mensajes después de ServerHello y, en algunos casos, puede no enviar un mensaje de certificado, de ahí que el mensaje ServerHelloDone sea necesario.

Una vez que el cliente ha recibido todos los mensajes del servidor, tiene suficiente información para generar las claves de sesión. TLS lo hace mediante la creación de un bit compartido de datos aleatorios denominado *secreto premaestro*, que tiene un tamaño fijo y se utiliza como un valor de inicialización para generar todas las claves necesarias una vez habilitado el cifrado. El secreto premaestro se cifra mediante el algoritmo de clave pública (por ejemplo, RSA) especificado en los mensajes Hello (consulte más abajo para obtener información sobre los algoritmos de clave pública) y la clave pública proporcionada por el servidor en su certificado. Una característica opcional de TLS denominada claves precompartidas (PSK) admite conjuntos de cifrado que no usan un certificado, sino un valor de secreto compartido entre los hosts (normalmente a través de transferencia física u otro método protegido). El secreto compartido se usa para generar el secreto premaestro en lugar de usar un mensaje cifrado para enviarlo. Consulte a continuación la sección sobre claves precompartidas.

El secreto premaestro cifrado se envía al servidor en el mensaje ClientKeyExchange. El servidor, al recibir el mensaje ClientKeyExchange, descifra el secreto premaestro mediante su clave privada y continúa generando las claves de sesión en paralelo con el cliente TLS.

Una vez generadas las claves de sesión, todos los mensajes posteriores se pueden cifrar mediante el algoritmo de clave privada (por ejemplo, AES) seleccionado en los mensajes Hello. El cliente y el servidor envían un mensaje no cifrado final denominado ChangeCipherSpec para indicar que se cifrarán todos los mensajes posteriores.

El primer mensaje cifrado enviado por el cliente y el servidor también es el mensaje de protocolo de enlace TLS final, denominado Finished. Este mensaje contiene un hash de todos los mensajes de protocolo de enlace recibidos y enviados. Este hash se utiliza para comprobar que ninguno de los mensajes del protocolo de enlace se ha manipulado o dañado (lo que indica una posible infracción de seguridad).

Una vez recibidos los mensajes Finished y comprobados los hashes del protocolo de enlace, se inicia la sesión de TLS y la aplicación comienza a enviar y recibir datos. En primer lugar, se aplica un algoritmo hash a todos los datos enviados desde cualquier lado durante la sesión de TLS con el algoritmo hash elegido en los mensajes Hello (para proporcionar integridad del mensaje) y se cifran mediante el algoritmo de clave privada elegido con las claves de sesión generadas.

Por último, una sesión de TLS solo se puede finalizar correctamente si el cliente o el servidor decide hacerlo. Una sesión truncada se considera una infracción de seguridad (ya que un atacante puede estar intentando impedir que se reciban todos los datos que se envían), por lo que se envía una notificación especial cuando uno de los lados desea finalizar la sesión (denominada alerta CloseNotify). Tanto el cliente como el servidor deben enviar y procesar una alerta CloseNotify para que se cierre correctamente la sesión.

![Diagrama de un protocolo de enlace TLS típico.](media/image4.png)

Figura 3: Protocolo de enlace TLS típico

### <a name="tls-13-handshake"></a>Protocolo de enlace TLS 1.3

TLS 1.3 es una revisión bastante importante del protocolo TLS. La gran mayoría de los cambios se han realizado en el protocolo de enlace para aumentar la seguridad y el rendimiento. En la figura 4 se muestra un protocolo de enlace TLS 1.3 típico. La diferencia principal puede verse en el número de intercambios entre el servidor y el cliente.

En TLS 1.2 y versiones anteriores, el servidor enviaba los mensajes en dos paquetes<sup>12</sup> de mensajes: en primer lugar, ServerHello y, después, un mensaje de ChangeCipherSpec antes de enviar el mensaje cifrado Finished que finaliza el protocolo de enlace. En TLS 1.3, el servidor envía todo en el primer paquete: ServerHello, las extensiones, el certificado y el mensaje Finished. Se ha eliminado el mensaje ChangeCipherSpec y el servidor genera sus claves de sesión y comienza a cifrar los mensajes de protocolo de enlace inmediatamente después de ServerHello.

La nueva disposición significa que una mayor parte del protocolo de enlace TLS está protegido por el cifrado, lo que limita la cantidad de datos de texto no cifrado a los que puede tener acceso un atacante. Además, la eliminación del segundo paquete del servidor (que era simplemente un ChangeCipherSpec seguido de Finished) significa que un cliente TLS ya no necesita esperar para iniciar la transmisión de datos de la aplicación: tan pronto como el cliente envía su propio mensaje Finished, la sesión se inicia.

12. En este contexto, un paquete es simplemente una colección de mensajes TLS que se envían simultáneamente en un grupo.

![Diagrama de un protocolo de enlace TLS 1.3.](media/image5.png)

Figura 4: Protocolo de enlace TLS 1.3

> [!NOTE]
> *TLS 1.3 también introducía la noción de “datos tempranos” y 0-RTT (tiempo de ida y vuelta cero), lo que significa que algunos datos de la aplicación se pueden enviar en el primer paquete de mensajes. Esta característica opcional se agregó principalmente como una optimización de la capacidad de respuesta del explorador Web (por ejemplo, para enviar encabezados HTTP iniciales para empezar a representar una página). A partir de Azure RTOS 6.0, no se admite esta característica.*

### <a name="initialization"></a>Inicialización

La pila TCP/IP de NetX o NetXDuo debe inicializarse antes de usar el servicio TLS de NetX Secure. Consulte la guía de usuario de NetX o NetXDuo para obtener información sobre cómo inicializar correctamente la pila TCP/IP.

Una vez inicializada la pila TCP/IP de NetX, se puede habilitar TLS. Internamente, todo el tráfico de red y el procesamiento de TLS se controla mediante la pila de NetX/NetXDuo sin necesidad de la intervención del usuario. Sin embargo, TLS tiene algunos requisitos específicos que se deben controlar de forma independiente de la pila de red subyacente. Estos parámetros se asignan al bloque de control de TLS llamado ***NX_SECURE_TLS_SESSION** _ mediante el servicio _ *_nx_secure_tls_session_create_**.

TLS tiene dos modos, servidor y cliente, y ambos pueden esta habilitados en una aplicación (pero solo un modo por socket NetX). Cada uno tiene sus propios requisitos específicos y se detallan a continuación.

En los dos modos, el servicio TLS de NetX Secure requiere la creación y configuración de un socket TCP (***NX_TCP_SOCKET** _) para las comunicaciones TCP con el host remoto. El socket TCP se asigna a una instancia de sesión TLS con el servicio _ *_nx_secure_tls_session_start_**, que se detalla a continuación.

### <a name="initialization--tls-server"></a>Inicialización – Servidor TLS

Además de un socket TCP, el modo de servidor TLS de NetX Secure requiere un *certificado digital* (que es un documento que se usa para identificar el servidor TLS en el cliente TLS de conexión) y los certificados de *clave privada* correspondientes (normalmente para el algoritmo de cifrado RSA). La norma International Telecommunications Union X.509 especifica el formato de certificado que usa TLS y hay numerosas utilidades para crear certificados digitales X.509.

En el caso del servicio TLS de NetX Secure, el certificado X.509 debe estar codificado de forma binaria con el formato de reglas de codificación distinguida (DER) de ASN.1. DER es el formato binario estándar TLS durante la conexión para los certificados.

La clave privada asociada con el certificado proporcionado debe estar en formato PKCS#1 codificado mediante DER. La clave privada solo se usa en el dispositivo y nunca se transmitirá a través de la conexión. ¡Mantenga las claves privadas seguras, ya que proporcionan la seguridad de las comunicaciones TLS!

Para inicializar el certificado de servidor TLS, la aplicación debe proporcionar un puntero a un búfer que contenga el certificado X.509 codificado mediante DER y datos opcionales de clave privada RSA PKCS#1 codificados mediante DER con el servicio ***nx_secure_x509_certificate_intialize** _ (que rellena la estructura _ *NX_SECURE_X509_CERT** con los datos de certificado adecuados para su uso por parte de TLS).

Una vez inicializado el certificado de servidor, debe agregarse al bloque de control de TLS mediante el servicio ***nx_secure_tls_local_certificate_add***.

Una vez que se ha agregado el certificado del servidor al bloque de control de TLS, se puede usar el socket para establecer una conexión segura del servidor TLS.

### <a name="initialization--tls-client"></a>Inicialización – Cliente TLS

El modo de cliente TLS de NetX Secure necesita un *almacén de certificados de confianza*, que es una colección de certificados digitales con codificación X.509 de las entidades de certificación de confianza (CA). El protocolo TLS da por supuesto que estos certificados son “de confianza” y sirven como base para autenticar los certificados proporcionados por las entidades de servidor TLS en el cliente TLS de NetX Secure.

Un certificado de CA de confianza puede ser *autofirmado* o firmado por otra CA, en cuyo caso el certificado se denomina de *CA intermedia* (ICA). En una aplicación TLS típica, el servidor proporciona los certificados ICA junto con su certificado de servidor, pero el único requisito para la autenticación correcta es que se pueda realizar un seguimiento de una cadena de emisores (certificados usados para firmar otros certificados) desde el certificado de servidor a un certificado de CA de confianza en el almacén de certificados de confianza. Esta cadena se conoce como *cadena de confianza* o *cadena de certificados*.

Para inicializar un certificado de CA o ICA de confianza, la aplicación debe proporcionar un puntero a un búfer que contenga el certificado X.509 codificado mediante DER con el servicio **nx_secure_x509_certificate_intialize** (que rellena la estructura *NX_SECURE_X509_CERT** con los datos de certificado adecuados para su uso por parte de TLS).

Los certificados de confianza que se han inicializado se agregan a continuación al bloque de control de TLS creado mediante el servicio ***nx_secure_tls_trusted_certificate_add***. Si no se agrega un certificado, se producirá un error en la sesión de cliente TLS, ya que no habrá forma de que el protocolo TLS autentique los hosts de servidor TLS remotos.

El cliente TLS también necesita espacio para asignar el certificado de servidor entrante (suponiendo que no se esté usando el modo de clave precompartida). A partir de la versión 5.12 de TLS en NetX Secure, ya no es necesario que la aplicación asigne espacio para el certificado remoto. Sin embargo, la opción heredada para asignar espacio para un certificado de servidor sigue estando disponible y los certificados asignados por el usuario se usarán antes de la optimización de búfer de certificado interno <sup>13</sup>; consulte el servicio ***nx_secure_tls_remote_certificate_allocate*** para obtener más información.

Una vez creado el almacén de certificados de confianza y tras haber asignado espacio para el certificado de servidor, el socket se puede usar para establecer una conexión de cliente TLS segura.

13. La optimización usa el “búfer de paquetes” proporcionado por la aplicación de usuario a la sesión de TLS mediante *nx_secure_tls_session_packet_buffer_set* para asignar las estructuras de análisis de X.509 en lugar de usar las estructuras proporcionadas por el usuario que se usan en versiones anteriores del servicio TLS de NetX Secure. No es probable que se detecte una cadena de certificados que supere el tamaño del búfer de paquetes, en cuyo caso se puede aumentar el tamaño del búfer de paquetes o usar *nx_secure_tls _remote_certificate_allocate* para asignar más espacio para la cadena de certificados.

### <a name="application-interface-calls"></a>Llamadas a la interfaz de la aplicación

Las aplicaciones TLS de NetX Secure normalmente realizarán llamadas de función desde subprocesos de la aplicación que se ejecutan en ThreadX RTOS. Se puede llamar a cierta inicialización, especialmente para los protocolos de comunicaciones de red subyacentes (por ejemplo, TCP e IP), desde ***tx_application_define*.** Consulte la guía de usuario de NetX/NetXDuo para obtener más información sobre cómo inicializar las comunicaciones de red.

TLS hace un uso intensivo de las rutinas de cifrado que son operaciones de uso intensivo del procesador. Por lo general, estas operaciones se realizarán en el contexto del subproceso que realiza la llamada.

### <a name="tls-session-start"></a>Inicio de sesión de TLS

TLS requiere un protocolo de red de capa de transporte subyacente para poder funcionar. El protocolo que se usa normalmente es TCP. Para establecer una sesión TLS de NetX Secure, se debe establecer una conexión TCP mediante la API de TCP de NetX/NetXDuo. Se debe crear un objeto **NX_TCP_SOCKET** y una conexión establecida con los servicios **_nx_tcp_server_socket_listen_ *_ y _* _nx_tcp_server_socket_accept_ *_ (para el servidor TLS) o con el servicio _* _nx_tcp_client_socket_connect_** (para el cliente TLS).

Una vez establecida una conexión TCP, el socket TCP se pasa al servicio ***nx_secure_tls_session_start***.

### <a name="tls-packet-allocation"></a>Asignación de paquetes TLS

El servicio TLS de NetX Secure usa la misma estructura de paquetes que el protocolo TCP de NetX/NetXDuo (***NX_PACKET** _), salvo que, en lugar de llamar al servicio _*_nx_packet_allocate_*_, se debe llamar al servicio _ *_nx_secure_tls_packet_allocate_** para que se pueda asignar correctamente el espacio para el encabezado TLS.

### <a name="tls-session-send"></a>Envío de sesión de TLS

Una vez iniciada la sesión TLS, la aplicación puede enviar datos mediante el servicio ***nx_secure_tls_session_send**. El uso del servicio de envío es idéntico para el servicio _*_nx_tcp_socket_send_*_ y toma una estructura de datos _*_NX_PACKET_*_ con los datos que se envían. La diferencia es que los datos se cifrarán mediante la pila TLS de NX Secure antes de que se envíen y el paquete debe asignarse mediante _ *_nx_secure_tls_packet_allocate_* *.

### <a name="tls-session-receive"></a>Recepción de sesión de TLS

Una vez iniciada la sesión de TLS, la aplicación puede empezar a recibir datos mediante el servicio ***nx_secure_tls_session_receive** _. Al igual que el envío de la sesión de TLS, este servicio se usa exactamente igual que _*_nx_udp_socket_receive_**, con la salvedad de que la pila TLS descifra y comprueba los datos entrantes antes de que se devuelvan en la estructura de paquetes.

### <a name="tls-session-close"></a>Cierre de sesión de TLS

Una vez completada una sesión de TLS, tanto el cliente como el servidor TLS deben enviar una alerta CloseNotify al otro lado para cerrar la sesión. Ambos lados deben recibir y procesar la alerta para asegurarse de que el cierre de sesión se ha realizado correctamente.

Si el host remoto envía una alerta CloseNotify, todas las llamadas al servicio ***nx_secure_tls_session_receive** _ procesarán la alerta, enviarán de nuevo la alerta correspondiente al host remoto y devolverán un valor de _*_NX_SECURE_TLS_SESSION_CLOSED_**. Una vez cerrada la sesión, se producirá un error en cualquier intento adicional de enviar o recibir datos con esa sesión de TLS.

Si la aplicación desea cerrar la sesión de TLS, se debe llamar al servicio ***nx_secure_tls_session_end** _. El servicio enviará la alerta CloseNotify y procesará la respuesta CloseNotify. Si no se recibe la respuesta, se devolverá un valor de error de _ *_NX_SECURE_TLS_SESSION_CLOSE_FAIL_**, lo que indica que la sesión de TLS no se apagó correctamente y puede indicar una posible infracción de seguridad.

### <a name="tls-alerts"></a>Alertas TLS

TLS está diseñado para proporcionar la máxima seguridad, por lo que cualquier comportamiento errante en el protocolo se considera una posible infracción de seguridad. Por esta razón, los errores en el procesamiento de mensajes o el cifrado y descifrado se consideran errores irrecuperables que finalizan la sesión o el protocolo de enlace inmediatamente.

Aunque el control de errores en una aplicación local es relativamente sencillo, el host remoto debe saber que se ha producido un error con el fin de controlar correctamente la situación y evitar posibles infracciones de seguridad. Por esta razón, DTLS enviará un mensaje de *alerta* al host remoto en caso de error.

Las alertas se tratan de la misma manera que cualquier otro mensaje de TLS y se cifran durante la sesión para impedir que un atacante recopile información del tipo de alerta proporcionado. Durante el protocolo de enlace, el ámbito de las alertas enviadas está limitado para controlar la cantidad de información que podría obtener un atacante potencial.

La alerta CloseNotify, que se usa para cerrar la sesión de TLS, es la única alerta no grave. Aunque se considera una alerta y se envía como un mensaje de alerta, CloseNotify es diferente de otras alertas, ya que no indica que se ha producido un error.

El valor y el “nivel” de la alerta (los niveles son “advertencia” y “irrecuperable”; la mayoría de las alertas de TLS de nivel “irrecuperable”) se definen en las RFC de TLS e indican el tipo de error que se ha producido. La mayoría de las alertas de TLS distintas de CloseNotify se pueden considerar como la indicación de un posible problema de seguridad y dará como resultado la anulación de la sesión o del protocolo de enlace TLS. Si alguna llamada a la API de TLS devuelve **NX_SECURE_TLS_ALERT_RECEIVED** (0x114), se puede usar el servicio **_nx_secure_tls_session_alert_value_get_** de la API (nuevo en la versión 5.12 de TLS en NetX Secure) para recuperar el valor de alerta de TLS y el nivel de la aplicación que se va a usar para cualquier decisión relativa a las respuestas a los problemas de seguridad. En la mayoría de los casos, cualquier alerta recibida desde el host remoto que no sea CloseNotify debe considerarse un error irrecuperable, aunque hay algunas excepciones (consulte las RFC de TLS para obtener más información).

### <a name="tls-session-renegotiation"></a>Renegociación de sesión TLS

TLS admite la noción de “renegociación”, que es simplemente una renegociación de los parámetros de sesión de TLS en el contexto de una sesión de TLS existente. Esto significa que, en la práctica, los nuevos mensajes de protocolo de enlace se cifran y se autentican mediante la sesión existente. La renegociación se usa cuando un host de TLS desea generar nuevos parámetros de sesión (por ejemplo, generar nuevas claves de sesión de TLS) sin tener que completar la sesión existente. Por ejemplo, la renegociación puede ser deseable cuando las directivas de seguridad de una aplicación dictan que las claves de sesión solo se usan durante un tiempo limitado, pero una sesión de TLS permanece activa más allá de ese tiempo.

Un problema con la renegociación de la sesión es que hace que TLS sea vulnerable a un ataque específico de tipo “Man in the Middle”, en el que un atacante puede convencer a un servidor para que inicie una renegociación con nuevos parámetros, lo que permite al atacante secuestrar la sesión de TLS. Para mitigar este problema, se ha introducido la extensión de indicación de renegociación segura (consulte la sección **Error! Reference source not found.** ).

El servicio TLS de NetX Secure admite por completo la renegociación de la sesión y la extensión de indicación de renegociación segura.

Al recibir datos de un host remoto, las renegociaciones (y su extensión) se administran automáticamente sin la interacción de la aplicación. Si se desea recibir notificaciones sobre renegociaciones de sesión, se puede proporcionar una devolución de llamada de renegociación con el servicio *nx_secure_tls_session_renegotiate_callback_set*. La devolución de llamada se invocará siempre que el host remoto solicite una renegociación, lo que permite que la aplicación tome medidas si se desea.

Para iniciar una renegociación desde una sesión de TLS activa, basta con invocar el servicio *nx_secure_tls_session_renegotiate* en la sesión de TLS deseada.

### <a name="tls-session-resumption"></a>Reanudación de la sesión TLS

A pesar de tener ciertas similitudes, la reanudación de la sesión TLS no se debe confundir con la renegociación de la sesión. En los casos en que la *renegociación* de la sesión implica iniciar un nuevo protocolo de enlace dentro de una sesión de TLS existente, la *reanudación* de la sesión es una característica puramente opcional que implica el reinicio de una sesión de TLS cerrada sin necesidad de realizar un protocolo de enlace TLS completo. Para ello, una implementación de TLS puede almacenar en caché los parámetros y las claves de la sesión, asociarlos con un *identificador de sesión* (un identificador único proporcionado en el protocolo de enlace original). Al proporcionar un identificador de sesión a un servidor TLS, un cliente indica que existía una sesión de TLS anterior entre los hosts y finalizó en el pasado, y que el cliente todavía posee el estado para volver a establecer la sesión con un protocolo de enlace reducido. Puesto que las claves de sesión en teoría son secretas y solo las conocen los dos hosts que se comunican, el servidor puede iniciar una nueva sesión de TLS y omitir la mayor parte del protocolo de enlace normal.

La reanudación de la sesión puede ser útil para evitar las operaciones de clave pública potencialmente costosas utilizadas para compartir el secreto maestro de generación de claves y comprobar las firmas de certificado, pero también requiere que el estado de los parámetros de sesión, las claves y el conjunto de cifrado se conserven en la memoria para todas las sesiones posibles (al menos para una ventana de tiempo configurable).

La versión actual del servicio TLS de NetX Secure no admite la reanudación de la sesión: los servidores TLS simplemente omiten el identificador de sesión y los clientes TLS siempre proporcionan un identificador de sesión NULL que solicita al servidor que realice un protocolo de enlace completo. La falta de reanudación de la sesión no debe provocar problemas de interoperabilidad, ya que es una característica completamente opcional y todas las implementaciones de TLS deben tener como valor predeterminado un protocolo de enlace completo si el identificador de sesión es NULL o no se reconoce.

### <a name="protocol-layering"></a>Capas de protocolo

El protocolo TLS encaja en la pila de red entre la capa de transporte (por ejemplo, TCP) y la capa de aplicación. TLS se considera a veces un protocolo de capa de transporte (de ahí su nombre: seguridad de la *capa de transporte*), pero dado que actúa como una aplicación con respecto a los protocolos de red subyacentes (como TCP), a veces se agrupa en la capa de aplicación.

TLS requiere un protocolo de capa de transporte que admita la entrega en orden y sin pérdidas, como TCP. Debido a este requisito, no se puede ejecutar TLS sobre UDP, ya que UDP no garantiza la entrega de datagramas. *DTLS* (versión modificada de TLS) es un protocolo independiente que se utiliza para las aplicaciones que necesitan la seguridad de TLS a través de un protocolo de datagramas como UDP. NetX Secure es compatible con DTLS, pero la documentación de DTLS se proporciona en otro documento, no en este.

![Diagrama de capas de protocolo TCP/IP y TLS.](media/image6.png)

Figura 5: Diagrama de capas de protocolo TCP/IP y TLS

## <a name="network-communications-security"></a>Seguridad de las comunicaciones de red

La protección de las comunicaciones a través de redes públicas e Internet es un tema muy importante y es protagonista de una gran cantidad de libros, artículos y soluciones. El tema es el increíblemente complejo, pero se puede reducir a una idea sencilla: enviar información a través de una red para que solo el destinatario previsto pueda acceder a la información o cambiarla. Esto se divide en tres conceptos importantes: confidencialidad, integridad y autenticación. El protocolo TLS proporciona soluciones para los tres.

### <a name="secrecy"></a>Confidencialidad

Cuando se envían datos a través de una red, a menudo es importante que una entidad malintencionada no pueda obtenerlos. Si los datos se envían a través de una conexión TCP/IP, cualquier usuario con acceso a la red podrá leer esos datos mediante herramientas de red fácilmente disponibles. Para evitar que se obtengan datos, se debe codificar de forma que únicamente se puedan leer en el destino previsto; se debe garantizar la *confidencialidad.* En TLS, los algoritmos de cifrado, como RSA y AES, proporcionan confidencialidad.

### <a name="integrity"></a>Integridad

A veces, la confidencialidad no es suficiente para proteger los datos que viajan a través de una red. En algunos casos, una entidad malintencionada puede llegar a modificar el contenido de un paquete TCP sin necesidad de saber lo que contiene el paquete. Es posible modificar los datos cifrados anulando el descifrado o cambiando los parámetros del mensaje para que el atacante pueda conseguir lo que le interesa. En la red, no podemos evitar que un atacante cambie los datos en tránsito, pero podemos proporcionar un mecanismo para saber si los datos han cambiado o no. Si se cambian los datos en tránsito, lo sabremos y podremos rechazar los datos. Este concepto se denomina *integridad*. En TLS, la integridad se proporciona mediante una clase de rutinas criptográficas conocidas como *funciones hash*. Algunos ejemplos de funciones hash son MD5 y SHA-1.

### <a name="authentication"></a>Authentication

El tercer concepto importante en la seguridad de las comunicaciones de red es la idea de que los datos solo deben comunicarse con el destino previsto. Un atacante puede intentar hacerse pasar por una entidad legítima para recibir los datos destinados a otro host. Incluso si los datos se envían con mecanismos de confidencialidad e integridad implementados, es posible que el atacante siga pudiendo conseguir el resultado deseado (poner en riesgo las comunicaciones seguras) a través de este proceso. Para evitarlo, es necesario un mecanismo para demostrar la identidad de un host remoto antes de que se envíen datos confidenciales. El proceso de comprobación de la identidad de un host remoto recibe el nombre de *autenticación.* En TLS, la autenticación se proporciona mediante certificados digitales, funciones hash y un mecanismo denominado *firmas digitales* que utiliza una propiedad de cifrado de clave pública (se describe a continuación). También se puede proporcionar una forma limitada pero útil de autenticación con una *clave precompartida* (PSK).

## <a name="tls-encryption"></a>Cifrado TLS

El protocolo TLS es un marco para proporcionar comunicaciones de red seguras a través de Internet con cifrado. Normalmente, el cifrado se define como el proceso de codificación de datos de tal forma que la obtención de los datos originales (o la información sobre esos datos) resulte excesivamente difícil sin una *clave*. En, el cifrado de sistemas se basa en cálculos matemáticos complejos, como campos finitos, y se puede clasificar en dos tipos: *clave privada* (o *cifrado simétrico*) y *clave pública* (o *cifrado asimétrico*). Los ejemplos de cifrado de clave privada son AES (Estándar de cifrado avanzado) y RC4 (Cifrado de Rivest 4). Los cifrados RSA (Rivest, Shamir, Adleson) y Diffie-Hellman son ejemplos de cifrado de clave pública.

El protocolo TLS usa las rutinas de cifrado de clave privada y de clave pública para proporcionar un equilibrio entre rendimiento, seguridad y flexibilidad.

### <a name="private-key-encryption"></a>Cifrado de clave privada

El cifrado de clave privada se lleva usando miles de años. Los cifrados de sustitución básicos (donde una letra o una palabra se sustituye por otra letra o palabra no relacionada) son los ejemplos más antiguos conocidos de cifrado, pero con la llegada de la era de la información, el cifrado de claves privadas ha mejorado considerablemente.

Un cifrado de clave privada usa una “clave”, que es simplemente un valor (podría ser una palabra, una frase o un número en el caso general) que se usa para codificar de alguna manera ciertos datos de modo que solo una entidad que tenga acceso a esa clave pueda descodificarlos para obtener su significado. La clave se usa para el cifrado y descifrado de los datos, de ahí que también reciba el nombre de *cifrado simétrico*.

Los cifrados de clave privada suelen ser rápidos y fáciles de implementar, incluso si los cálculos matemáticos implicados son demasiado complejos. Por esta razón, TLS utiliza cifrados de clave privada para la mayor parte de las comunicaciones seguras.

Sin embargo, el cifrado de clave privada tiene un problema cuando se intenta aplicar a las comunicaciones de red de equipos generales: la clave debe compartirse entre los equipos que intentan comunicarse. En general, esto no resulta práctico y a menudo no es posible comunicar una clave privada de forma segura entre dos equipos en Internet, ya que se puede suponer que el tráfico de la red puede ser obtenido por cualquier número de entidades en los diversos saltos que toman los datos al ser enrutados a través de Internet. Si una entidad malintencionada obtiene la clave, se pone en peligro todos los datos cifrados con esa clave. Como la mayoría de los equipos en Internet solo tienen una conexión de red y no otro canal seguro para las comunicaciones, el envío de claves a través de la red equivale a enviar los datos sin cifrar: no proporciona seguridad.

Por esta razón, el cifrado de clave privada no basta para implementar un protocolo de seguridad de comunicaciones de red de uso general. Aquí es donde el cifrado de clave pública es de ayuda.

El servicio TLS de NetX Secure es compatible con el cifrado de clave privada AES.

### <a name="public-key-encryption"></a>Cifrado de clave pública

A diferencia del cifrado de clave privada, el cifrado de clave pública es un concepto bastante nuevo que se desarrolló en los de 1970. Mediante el uso de un concepto matemático conocido como “funciones de trampilla”, se descubrió que había una manera de compartir una clave a través de una red sin poner en peligro la seguridad de los datos cifrados.

El cifrado de clave pública funciona de la siguiente manera: la clave (en el sentido de cifrado de clave privada descrito anteriormente) se divide en dos partes, una *clave privada* y una *clave pública* (de aquí viene el nombre de cifrado de clave pública). El concepto se basa en que una de estas claves (normalmente, la clave pública) se usa para el cifrado, mientras que la otra se usa para el descifrado. Esta asimetría de claves es el motivo por el que el cifrado de clave pública recibe el nombre de *cifrado asimétrico*.

Los cálculos matemáticos detrás del cifrado de clave pública son bastante complejos, pero la idea es que la clave pública *solo* se puede usar para el cifrado y la obtención de esa clave no permite obtener datos cifrados. La clave privada, a su vez, es la única manera de descifrar los datos cifrados con la clave pública. Por lo tanto, al mantener el secreto de la clave privada, cualquier persona que quiera comunicarse de forma segura con el propietario de esa clave privada solo necesita cifrar sus datos con la clave pública correspondiente y sabrá que solo alguien en posesión de la clave privada podrá obtener los datos seguros.

El servicio TLS de NetX Secure admite el cifrado de clave pública RSA.

> [!IMPORTANT] 
> *RSA es una operación que requiere un uso intensivo del procesador si se usa la implementación RSA de software. Los tamaños de clave más grandes aumentan por cuatro la potencia de procesamiento necesaria (4 veces más lento para un aumento del doble en el tamaño de la clave).*

### <a name="public-key-authentication"></a>Autenticación de la clave pública

Un efecto secundario interesante del concepto de cifrado de clave pública es que se puede usar para proporcionar autenticación y cifrado mediante la operación inversa: cifrado con la clave *privada* y descifrado mediante la clave *pública*. El mecanismo real para hacerlo depende del algoritmo de clave pública que se use, pero el concepto es el mismo.

Para autenticar mediante la autenticación de clave pública, el propietario de una clave privada cifra parte de los datos (normalmente un hash criptográfico de los datos que se van a autenticar) con esa clave privada. A continuación, alguien que quiera verificar que los datos provienen del propietario de la clave privada usa la clave pública asociada para descifrar los datos: si el descifrado se realiza correctamente y se asume que el usuario confía en la validez de la clave pública, el usuario puede estar seguro de que los datos proceden del propietario de la clave privada.

En TLS se usa la autenticación de clave pública para comprobar la validez de un certificado digital proporcionado por un servidor TLS (y, opcionalmente, el cliente TLS) mediante claves públicas del almacén de certificados de confianza. El certificado se comprueba con una clave pública en el almacén y los datos del certificado se usan para comprobar la identidad del servidor.

El servicio TLS de NetX Secure es compatible con la autenticación RSA.

### <a name="cryptographic-hashing"></a>Hash criptográfico

El cifrado no es la única operación criptográfica que se usa en TLS. Para proporcionar integridad del mensaje durante una sesión de TLS, se necesita una suma de comprobación para garantizar que el contenido del mensaje no se ha alterado. Sin embargo, una suma de comprobación simple (como se usa en TCP) no es suficiente para garantizar un nivel de integridad aceptable, ya que un atacante experto puede subvertirla fácilmente. El mecanismo que usa TLS para proporcionar la integridad del mensaje se conoce como *hash criptográfico*.

El cifrado es una codificación 1:1, es decir, la totalidad de los datos originales se puede obtener a partir de los datos cifrados. Sin embargo, un hash asigna una cantidad arbitraria de datos a un valor de tamaño fijo, como una suma de comprobación. A diferencia de una suma de comprobación simple, un hash se ha diseñado específicamente para reducir las *colisiones*, donde distintos datos de entrada producen el mismo resultado. En una suma de comprobación simple, si un bit se voltea de 1 a 0 y otro bit de 0 a 1, la suma de comprobación es la misma. Con un hash criptográfico, el resultado sería bastante distinto, y esto haría que para un atacante fuese más difícil cambiar los datos con hash y conseguir que la operación hash de los datos cambiados generase el mismo valor (y, por lo tanto, lograr comprobar la integridad de los datos de forma falsa).

TLS usa varios algoritmos hash distintos para proporcionar integridad a los mensajes, tanto a los de la aplicación como a los de control TLS. Entre ellos se incluyen MD5, SHA-1 y SHA-256.

El servicio TLS de NetX Secure admite hash MD5, SHA-1 y SHA-256.

## <a name="tls-extensions"></a>Extensiones TLS

TLS incluye una serie de extensiones que ofrecen funcionalidad adicional para ciertas aplicaciones. Normalmente, estas extensiones se envían como parte de los mensajes ClientHello o ServerHello, lo que indica a un host remoto el deseo de usar una extensión o proporciona detalles adicionales para su uso en el establecimiento de la sesión de TLS segura.

En general, las extensiones proporcionan parámetros opcionales a TLS al principio del protocolo de enlace que guían las operaciones siguientes. Algunas extensiones requieren la toma de decisiones o la entrada de la aplicación, mientras que otras se administran automáticamente.

En la tabla siguiente se describen las extensiones TLS compatibles actualmente con el servicio TLS de NetX Secure:

| **Extension Name**              | **Descripción**              |
| ------------------------------- |----------------------------- |
| Indicación de renegociación segura | Esta extensión mitiga una vulnerabilidad de ataque de tipo “man in the middle” que podría producirse durante un protocolo de enlace de renegociación.|
| Indicación de nombre de servidor          | Esta extensión permite que un cliente TLS proporcione un nombre DNS específico a un servidor TLS, lo que permite al servidor seleccionar las credenciales correctas (supone que el servidor tiene varios certificados de identidad y puntos de entrada de red). |
| Algoritmos de firma            | Esta extensión permite a un cliente TLS proporcionar a un servidor TLS una lista de algoritmos de firma y hash aceptables. |

Información general de las extensiones TLS admitidas

### <a name="secure-renegotiation-indication"></a>Indicación de renegociación segura

TLS admite la noción de realizar un protocolo de enlace en una sesión de TLS existente y usa la sesión establecida para cifrar los mensajes de protocolo de enlace. Este proceso permite que se vuelvan a establecer las claves de sesión criptográfica sin terminar la sesión de TLS (consulte la sección “Renegociación de sesión TLS”).

Lamentablemente, cuando TLS ya llevaba usando la renegociación durante algún tiempo, se descubrió que existía una vulnerabilidad en un ataque de tipo “man in the middle” que aprovechaba la característica de renegociación. Para cerrar la vulnerabilidad, se introdujo la extensión de indicación de renegociación segura. Esencialmente, la extensión de renegociación segura usa el hash del mensaje Finished de la conexión establecida para comprobar que los hosts originales participan en el protocolo de enlace de renegociación; básicamente, el hash se usa como un token de comprobación bajo el supuesto de que un atacante no podría falsificar el hash (lo que requeriría acceso a las claves de sesión).

El servicio TLS de NetX Secure controla la renegociación automática y usa la extensión de renegociación segura de forma predeterminada. No se requiere ninguna interacción con la aplicación.

### <a name="server-name-indication"></a>Indicación de nombre de servidor

Durante el protocolo de enlace TLS, un cliente TLS espera que un servidor remoto proporcione un certificado de identidad para que el cliente pueda autenticar el servidor. Sin embargo, puede haber algunos casos en los que un servidor ofrezca varios servicios diferentes con servidores “virtuales”, cada uno con identidades únicas. En el caso de un solo servidor con varias identidades, un cliente TLS puede proporcionar un nombre DNS específico que el servidor usará para seleccionar las credenciales adecuadas; el mecanismo para proporcionar este nombre es la extensión de indicación de nombre de servidor (SNI).

En las aplicaciones que usan la extensión SNI sí se requiere cierta interacción. En el caso de los clientes TLS, la aplicación debe proporcionar un nombre DNS que se enviará al servidor remoto. En el caso de los servidores TLS, la aplicación debe leer el nombre DNS de la extensión y seleccionar un certificado adecuado para devolverlo al cliente.

En las secciones siguientes se proporcionan más detalles sobre cómo usar la extensión SNI en el servicio TLS de NetX Secure.

### <a name="sni-extension--tls-client"></a>Extensión SNI – Cliente TLS

Un cliente TLS de NetX Secure que quiera usar la extensión SNI debe suministrar un nombre DNS a TLS para que se proporcione durante el protocolo de enlace. Este nombre se debe inicializar y proporcionar antes de iniciar una sesión de TLS, ya que la extensión se envía en el mensaje ClientHello que inicia el proceso de protocolo de enlace.

En el fragmento de código siguiente se muestra el uso de la extensión. En primer lugar, se inicializa un objeto NX_SECURE_X509_DNS_NAME con el nombre de servidor deseado. Después, antes de iniciar la sesión de TLS, se proporciona el nombre a TLS mediante la API de extensión SNI. Una vez establecido el nombre, no es necesario realizar ninguna otra acción. Consulte la referencia de la API en el capítulo 4.  
  
Descripción de los servicios de NetX Secure para obtener más información sobre las funciones individuales.

```C
/* The dns_name variable will contain our desired server name. */
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize the server DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, "www.example.com", 
                                            strlen("www.example.com"));


/* Initialize SNI extension in previously-initialized TLS Session. */
status = nx_secure_tls_session_sni_extension_set(&client_tls_session, &dns_name);

/* Now start the TLS session, starting with establishing the TCP connection – if 
   TLS is started before initializing the SNI extension, the extension will not be 
   sent in the ClientHello message! */
status = nx_tcp_client_socket_connect(&client_socket, IP_ADDRESS(1, 2, 3, 4), 443, 
                                      5 * NX_IP_PERIODIC_RATE);

status = nx_secure_tls_session_start(&client_tls_session, &client_socket, 
                                     NX_WAIT_FOREVER);
```
### <a name="sni-extension--tls-server"></a>Extensión SNI – Servidor TLS

En el lado del servidor TLS, la aplicación puede procesar la extensión SNI para seleccionar las credenciales correctas (por ejemplo, el certificado) que se proporcionarán al cliente remoto durante el protocolo de enlace. Para ello, la aplicación debe proporcionar una devolución de llamada de sesión que se invoca después de la recepción de un mensaje ClientHello.

El código de ejemplo de la API de nx_secure_tls_session_server_callback_set (consulte la página 122) muestra el análisis de una extensión SNI entrante mediante una devolución de llamada de servidor. Esencialmente, el servidor TLS recibe un mensaje ClientHello e invoca la devolución de llamada. A continuación, la aplicación usa la API de *nx_secure_tls_session_sni_extension_parse* para analizar los datos de la extensión proporcionada a la devolución de llamada para buscar la extensión SNI y devolver el nombre DNS proporcionado (tenga en cuenta que la extensión solo admite un nombre DNS único). Una vez que se obtiene el nombre, la aplicación lo usa para buscar y enviar el certificado de identidad de servidor adecuado (y la cadena de emisores, si procede).

### <a name="signature-algorithms-extension"></a>Extensión de algoritmos de firma

Esta extensión es específica de TLS 1.2 y permite a un cliente TLS proporcionar una lista de pares de algoritmo hash y firma aceptables que se pueden usar para generar y comprobar firmas digitales. La lista se genera automáticamente mediante el servicio TLS de NetX Secure para clientes TLS que usan la tabla de cifrado proporcionada para *nx_secure_tls_session_create*. No se requiere ninguna interacción con la aplicación.

## <a name="authentication-methods"></a>Métodos de autenticación

TLS proporciona el marco para establecer una conexión segura entre dos dispositivos a través de una red no segura, pero parte del problema es conocer la identidad del dispositivo en el otro extremo de la conexión. Sin un mecanismo para autenticar la identidad de los hosts remotos, un atacante podría hacerse pasar por un dispositivo de confianza sin el más mínimo esfuerzo.

Inicialmente, puede parecer que el uso de direcciones IP, direcciones MAC de hardware o DNS, proporcionarán un nivel relativamente alto de confianza para identificar hosts en una red, pero dada la naturaleza de la tecnología TCP/IP, la facilidad con la que se pueden suplantar las direcciones y dañarse las entradas DNS (por ejemplo, a través de la infección de la caché DNS), queda claro que TLS necesita una capa adicional de protección.

Hay varios mecanismos que pueden proporcionar esta capa adicional de autenticación para TLS, pero el *certificado digital* es el más común. Otros mecanismos incluyen las claves precompartidas (PSK) y los esquemas de contraseña.

### <a name="digital-cerificates"></a>Certificados digitales

Los certificados digitales son el método más común para autenticar un host remoto en TLS. Esencialmente, un certificado digital es un documento con un formato específico que proporciona información de identidad para un dispositivo en una red de equipos.

TLS normalmente usa un formato denominado X.509, un estándar desarrollado por la International Telecommunication Union, aunque se pueden usar otros formatos de certificados si los hosts de TLS acuerdan el formato usado. X.509 define un formato específico para los certificados y diversas codificaciones que se pueden utilizar para generar un documento digital. La mayoría de los certificados X.509 que se usan con TLS se codifican mediante una variante de ASN.1, otro estándar de telecomunicaciones. En ASN.1 hay varias codificaciones digitales, pero la codificación más común de los certificados TLS es el estándar de reglas de codificación distinguida (DER). DER es un subconjunto simplificado de las reglas de codificación básicas (BER) de ASN.1 que están diseñadas para ser inequívocas, lo que facilita el análisis. A través de la conexión, los certificados TLS normalmente están codificados en DER binario y este es el formato que NetX Secure espera para los certificados X.509.

Aunque los certificados binarios con formato DER se usan en el protocolo TLS real, se pueden generar y almacenar en varias codificaciones diferentes, con extensiones de archivo como. pem, .crt y .p12. Las distintas variantes las usan diferentes aplicaciones de distintos fabricantes, pero generalmente todas se pueden convertir en DER mediante herramientas ampliamente disponibles.

La más común de las codificaciones alternativas de certificados es PEM. El formato PEM (Privacy-Enhanced Mail, correo con privacidad mejorada) es una versión codificada en base 64 de la codificación DER que se usa a menudo porque la codificación da como resultado texto imprimible que se puede enviar fácilmente mediante correo electrónico o protocolos basados en Web.

La generación de un certificado para la aplicación de NetX Secure suele estar fuera del ámbito de este manual, pero la herramienta de línea de comandos de OpenSSL ([www.openssl.org](http://www.openssl.org)) está ampliamente disponible y puede realizar la conversión entre la mayoría de los formatos.

En función de la aplicación, puede generar sus propios certificados, proporcionar certificados por un fabricante o una organización gubernamental, o adquirir certificados de una entidad de certificación comercial.

Para usar un certificado digital en la aplicación de NetX Secure, primero debe convertir el certificado a un formato binario DER y, opcionalmente, convertir la clave privada asociada (el “exponente privado” en RSA, por ejemplo) en formato binario, normalmente una clave RSA con formato PKCS#1 con codificación DER o una clave ECC con codificación DER. Una vez finalizada la conversión, depende de usted cargar el certificado y la clave privada en el dispositivo. Entre las opciones posibles se incluyen el uso de un sistema de archivos basado en Flash o la generación de una matriz C a partir de los datos (mediante una herramienta como “xxd” desde Linux) y la compilación del certificado y la clave en la aplicación como datos constantes.

Una vez que el certificado se carga en el dispositivo, se puede usar la API de TLS para asociar el certificado a una sesión de TLS.

Para obtener más información y ejemplos sobre cómo usar los certificados X.509 con el servicio TLS de NetX Secure, consulte la sección “Importación de certificados X.509 en NetX Secure”.

Consulte los siguientes servicios TLS en la referencia de la API para obtener más información:

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add
- nx_secure_trusted_certificate_remove

### <a name="tls-client-certificate-specifics"></a>Detalles de certificados de cliente TLS

Las implementaciones de cliente TLS generalmente no requieren la carga de un certificado “local”<sup>14</sup> en el dispositivo. Hay una excepción: cuando está habilitada la autenticación de certificados de cliente, pero este supuesto es mucho menos frecuente.

Un cliente TLS requiere que se cargue al menos un certificado “de confianza”<sup>15</sup> (es posible que se carguen más, si es necesario) y espacio para que se asigne un certificado “remoto”<sup>16</sup>.

Para obtener más información sobre cómo agregar certificados de confianza y asignar espacio para los certificados remotos, consulte la referencia de la API de TLS para los siguientes servicios: nx_secure_tls_remote_certificate_allocate, nx_secure_tls_trusted_certificate_add.

14. Un certificado “local” es un certificado que identifica el dispositivo local, es decir, proporciona información de identidad para el dispositivo en el que se carga la aplicación TLS.

15. Un certificado “de confianza” es un certificado que proporciona una base de confianza y autenticación del dispositivo remoto, ya sea directamente o a través de una infraestructura de clave pública (PKI). La raíz de la cadena de confianza se denomina normalmente “entidad de certificación” o certificado de CA.

16. Un certificado “remoto” hace referencia al certificado enviado por el host remoto durante el protocolo de enlace TLS. Proporciona identidad para ese host remoto y se autentica mediante su comparación con un certificado “de confianza” en el dispositivo local.

### <a name="tls-server-certificate-specifics"></a>Detalles de certificados de servidor TLS

Por lo general, las implementaciones de servidor TLS no requieren la carga de certificados de “confianza” en el dispositivo o los certificados remotos que se van a asignar. Hay una excepción: cuando está habilitada la autenticación de certificados de cliente (este supuesto es menos frecuente).

Un servidor TLS requiere la carga de un certificado “local” para que el servidor pueda proporcionarlo al cliente remoto durante el protocolo de enlace TLS para autenticar el servidor en el cliente.

Para obtener más información sobre la carga de certificados locales para su uso con aplicaciones de servidor TLS de NetX, consulte la referencia de la API para los siguientes servicios: 
- nx_secure_tls_local_certificate_add, 
- nx_secure_tls_local_certificate_remove.

### <a name="pre-shared-keys-psk"></a>Claves precompartidas (PSK)

Un mecanismo alternativo para proporcionar autenticación de identificación en TLS es la noción de claves precompartidas (PSK). Usar un conjunto de cifrado PSK elimina la necesidad de realizar las operaciones de cifrado de clave pública de uso intensivo del procesador, una ventaja para los dispositivos integrados con restricción de recursos. La PSK reemplaza el certificado en el protocolo de enlace DTLS y se usa en lugar del secreto premaestro cifrado para la generación de claves de sesión DTLS.

Las conjuntos de PSK están limitados en el sentido de que un secreto compartido debe estar presente en ambos dispositivos antes de que se pueda establecer una sesión de DTLS. Esto significa que los dispositivos se deben haber cargado con ese secreto mediante el uso de algunos medios seguros distintos, no solo mediante una conexión TLS con PSK. La PSK se puede actualizar a través de una conexión de TLS con PSK, pero el dispositivo debe comenzar con una PSK que se carga a través de otro mecanismo. Por ejemplo, se podría cargar un dispositivo de sensor y su dispositivo de puerta de enlace con PSK en la fábrica antes del envío, o bien se podría usar una conexión TLS estándar (con un certificado) para cargar la PSK.

Los conjuntos de cifrado PSK se presentan en un par de formatos, que se describe en la RFC 4279. El primero usa las claves RSA o Diffie-Hellman que se usan de la misma manera que las claves públicas transmitidas en el certificado en los protocolos de enlace TLS estándar. El segundo, que se usa más en un entorno con restricción de recursos, utiliza una PSK que se utiliza para generar directamente las claves de sesión (para su uso con AES, por ejemplo), evitando así las costosas operaciones de Diffie-Hellman o RSA.

NetX Secure admite el segundo formato de conjuntos de cifrado PSK, lo que permite que las aplicaciones quiten todo el código de criptografía de clave pública y el uso de memoria. La PSK no es una clave AES, pero se puede considerar como una contraseña de la que se generan las claves reales. Existen algunas restricciones en lo que puede ser el valor de PSK, aunque los valores más largos proporcionarán más seguridad (igual que con las contraseñas).

Para usar PSK con la aplicación de NetX Secure, primero debe definir la macro global **NX_SECURE_ENABLE_PSK_CIPHERSUITES**. Normalmente esto se realiza a través de la configuración del compilador, pero la definición también se puede colocar en el archivo de encabezado nx_secure_tls.h. Con la macro definida, la compatibilidad del conjunto de cifrado PSK se compilará en la aplicación TLS de NetX Secure.

Con la compatibilidad con PSK habilitada, puede usar la API de TLS para configurar PSK para la aplicación. Cada PSK requerirá un valor de PSK (la “clave” secreta real que debe mantener a salvo), un valor de “identidad” que se usa para identificar la PSK específica y una “sugerencia de identidad” que se usa en un servidor TLS para elegir un valor de PSK determinado.

La PSK puede ser cualquier valor binario, ya que nunca se envía a través de una conexión de red. La PSK puede tener cualquier valor de hasta 64 bytes de longitud.

La identidad y la sugerencia deben ser cadenas de caracteres imprimibles con formato UTF-8. Los valores de identidad y sugerencia pueden tener una longitud de hasta 128 bytes.

La identidad y la PSK forman un par único que se carga en todos los dispositivos de la red que necesitan comunicarse entre sí.

La “sugerencia” se usa principalmente para definir perfiles de aplicación específicos para agrupar PSK por función o servicio. Estos valores se deben acordar de antemano y dependen de la aplicación. Por ejemplo, la aplicación de servidor de línea de comandos de OpenSSL (con PSK habilitado) utiliza la cadena predeterminada “Client_identity” que debe proporcionar un cliente TLS para continuar con el protocolo de enlace TLS.

Para obtener más información sobre las PSK, consulte la referencia de la API de NetX Secure para los siguientes servicios: nx_secure_tls_client_psk_set, nx_secure_tls_psk_add.

## <a name="importing-x509-certificates-into-netx-secure"></a>Importación de certificados X.509 en NetX Secure

Los certificados digitales son necesarios para la mayoría de las conexiones TLS en Internet. Los certificados proporcionan un método para autenticar hosts desconocidos previamente a través de Internet mediante el uso de intermediarios de confianza, normalmente denominados *entidades de certificación* o CA. Para conectar el dispositivo NetX Seguro con un servicio en la nube comercial (por ejemplo, Amazon Web Services), deberá importar los certificados en la aplicación si los carga en el dispositivo.

Además de los certificados, también necesitará una *clave privada* que esté asociada con el certificado. En algunas aplicaciones (como el cliente TLS cuando no se utiliza la autenticación de certificados de cliente), bastará con el certificado, pero si el certificado se usa para identificar el dispositivo, necesitará una clave privada. Las claves privadas normalmente se generan al crear el certificado y se almacenan en un archivo independiente (que a menudo cifrado con una contraseña).

### <a name="certificate-types"></a>Tipos de certificado

Los certificados digitales se utilizan normalmente para identificar entidades en una red pero, en función de sus aplicaciones, tendrán propiedades ligeramente diferentes.

### <a name="local-certificates"></a>Certificados locales

Para los fines de esta documentación, “certificados locales” hace referencia a los certificados que proporcionan una identidad para el dispositivo local (otro nombre posible podría ser “certificado de dispositivo”). Estos certificados se proporcionarán a un host remoto cuando el host remoto desea autenticar el dispositivo local.

### <a name="remote-certificates"></a>Certificados remotos

En esta documentación, “certificados remotos” hace referencia a los certificados proporcionados por un host remoto durante el protocolo de enlace TLS cuando proceda. Si el espacio de estos certificados no está asignado, NetX Secure no podrá analizarlos ni completar el protocolo de enlace TLS.

### <a name="signing-certificates"></a>Certificados de firma

Un “certificado de firma” se usa para firmar digitalmente otros certificados o datos con fines de autenticación. Estos certificados pueden ser certificados intermedios o raíz dentro de una infraestructura de clave pública (PKI) y, por lo general, no se usan para identificar dispositivos o hosts individuales.

### <a name="root-ca-certificates"></a>Certificados de entidad de certificación raíz

Los “Certificados de entidad de certificación raíz” son certificados de firma que proporcionan la base de una PKI y son autofirmados, en lugar de estar firmados por otro certificado de firma. Normalmente, se requiere al menos un certificado de CA raíz para que un cliente de TLS compruebe los servidores remotos.

### <a name="certificate-formats"></a>Formatos de certificado

Los certificados digitales son simplemente archivos que contienen datos estructurados codificados mediante la sintaxis ASN.1. Sin embargo, hay varios formatos en los que se pueden almacenar los certificados y es importante tener el formato correcto antes de cargar un certificado en una aplicación de NetX Secure.

Los formatos más comunes para los certificados son DER y PEM. DER (*reglas de codificación distinguida*, un formato de ASN.1) es el formato binario que usa TLS al realizar el protocolo de enlace inicial. PEM (*correo con privacidad mejorada*) es una versión codificada en base 64 del formato DER adecuada para el correo electrónico o el envío a través de HTTP en la Web. Los distintos proveedores utilizan extensiones de nombre de archivo diferentes para los certificados, como “.pem” o “.CRT” para los certificados PEM y “.der” para los certificados DER. Si tiene un certificado y no está claro qué formato se usa, abrir el archivo en un editor de texto le permitirá determinar el tipo, ya que los archivos DER están codificados como binarios y los archivos PEM son texto ASCII normal que empieza con el encabezado “-----BEGIN CERTIFICATE-----”.

NetX Secure requiere que el certificado esté en formato binario DER, por lo que tendrá que convertir el certificado al formato DER antes de la importación. Esto puede hacerse con herramientas disponibles fácilmente, como OpenSSL.

Si necesita una clave privada para la aplicación, el archivo de clave se codificará con PEM o DER en un formato específico (PKCS#1 para RSA, RFC 5915 para ECC). El archivo de clave privada deberá convertirse en DER antes de importarse.

Los siguientes comandos de OpenSSL se proporcionan como ejemplo para la conversión de certificados y archivos de clave RSA en el formato DER requerido por NetX Secure (ECC es similar; consulte la documentación de OpenSSL).

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
### <a name="private-keys-and-certificates"></a>Claves privadas y certificados

En el caso de los certificados que identifican un dispositivo, se debe cargar la clave privada asociada junto con el certificado. Un servidor TLS usa la clave privada (que puede ser para uno de los algoritmos de clave pública, como RSA, Diffie-Hellman o criptografía de curva elíptica) para descifrar el material de clave entrante (el “secreto premaestro”) de un cliente TLS, con lo que se autentica a sí mismo en el cliente. Para un cliente TLS, si se proporciona un certificado de identidad (un certificado con su clave privada asociada) y un servidor solicita un certificado de cliente, la clave privada se usa para autenticar el cliente: en el caso de RSA, el cliente cifra un token mediante la clave privada que luego el servidor descifra mediante la clave pública del cliente que se proporciona en el certificado de cliente (la autenticación Diffie-Hellman y ECC se produce de manera similar; solo varían algunos detalles).

En NetX Secure, el servicio *nx_secure_x509_certificate_initialize* se usa para inicializar un certificado X.509 (consulte la sección “Carga de certificados en el dispositivo” para obtener más información) y asociar opcionalmente una clave privada a ese certificado.

Si se proporciona una clave privada, el certificado se marca como el certificado de “identidad” que se usa para identificar el dispositivo. La clave se pasa como un BLOB binario contiguo y una longitud, con un tipo de clave asociada. El tipo de clave depende del tipo de la clave (por ejemplo, RSA, ECC, etc.) y el formato (por ejemplo, PKCS#1 DER). Si no se proporciona ninguna clave, se puede pasar el valor NX_SECURE_X509_KEY_TYPE_NONE (valor 0X0) para indicar que no se proporciona ninguna clave (una longitud de 0 y un puntero NX_NULL para el parámetro de datos logrará el mismo efecto).

En la tabla siguiente se muestran los tipos de clave conocidos para NetX Secure y el identificador de tipo asociado que se va a pasar a *nx_secure_x509_certificate_initialize*. Se agregarán tipos de clave adicionales a medida que se agreguen más algoritmos de cifrado a NetX Secure.

| Identificador                              | Algoritmo | Formato   | Encoding | Value |
| --------------------------------------- | --------- | -------- | -------- | ----- |
| NX_SECURE_X509_KEY_TYPE_NONE            | None      | N/D      | N/D      | 0x0   |
| NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER   | RSA       | PKCS#1   | DER      | 0x1   |
| NX_SECURE_X509_KEY_TYPE_EC_DER          | ECDSA     | RFC 5915 | DER      | 0x2   |

### <a name="user-defined-private-key-types"></a>Tipos de clave privada definidos por el usuario

Los valores de los identificadores de tipo de clave para el servicio *nx_secure_x509_certificate_initialize* rigen las acciones que se realizan cuando se proporciona la clave privada. En el caso de los tipos conocidos, los valores están en el intervalo 0x0000 0000 – 0x0000 FFFF (16 bits inferiores de un entero sin signo de 32 bits). En el caso de las plataformas con tipos de clave personalizada<sup>17</sup> (como ocurre en algunos motores de cifrado basados en hardware), se puede pasar un tipo de clave definido por el usuario en el intervalo 0x0000 1000-0xFFFF FFFF (16 bits superiores distintos de cero) como tipo de clave. Si se establece cualquiera de los 16 bits superiores del tipo de clave, los datos de la clave privada se pasan directamente a la rutina criptográfica adecuada (por ejemplo, RSA) suministrada en la tabla de conjuntos de cifrado de TLS. Los tipos de clave definidos por el usuario no se analizan ni se procesan de otra manera antes de pasarse a la rutina criptográfica. Además, el tipo de clave definido por el usuario también se pasará a la rutina criptográfica para que se pueda controlar cualquier procesamiento adecuado en ese nivel.

Tenga en cuenta que los tipos de clave definidos por el usuario se suelen usar en plataformas de hardware específicas que utilizan datos de clave personalizados (posiblemente cifrados). Por lo general, esto implica que los datos clave se generan o se codifican con un mecanismo específico de dicho proveedor de hardware (o, en el caso de una norma como PKCS#11, un estándar específico). Consulte la documentación del proveedor de la plataforma de hardware para obtener más información.

17. Los tipos de clave definidos por el usuario requieren una rutina criptográfica personalizada correspondiente para controlar el formato de clave personalizada. La rutina criptográfica debe tener un algoritmo coincidente (por ejemplo, RSA) y pasarse a TLS en la tabla de conjuntos de cifrado. 

### <a name="loading-certificates-onto-your-device"></a>Carga de certificados en el dispositivo

Cualquier método para cargar un archivo en el dispositivo será suficiente para importar los certificados.

El método más sencillo para cargar un certificado es convertir los datos codificados en DER binarios en una matriz de C y compilarlos en la aplicación como una constante. Esto puede hacerse fácilmente con herramientas como “XXD” en Linux (con la opción “-i”).

Como alternativa, puede cargar el certificado en un sistema de archivos Flash u otras opciones de almacenamiento, siempre y cuando pueda pasar un puntero a los datos del certificado en la API de NetX Secure.

### <a name="certificate-files-needed-for-netx-secure"></a>Archivos de certificado necesarios para NetX Secure

Los archivos de certificado que necesitará importar dependen de la aplicación. En general, los servidores TLS requieren un certificado para identificar el dispositivo y los clientes TLS requieren uno o más *certificados de confianza* para autenticar los servidores remotos. En la tabla siguiente se muestran los certificados necesarios para algunas aplicaciones TLS diferentes.

| **Funcionalidad/opciones de TLS**                     | **Certificados/claves que se necesitan (mínimo)**              |
| ------------------------------------------------- | --------------------------------------------------- |
| Cliente TLS                                        | Certificado de entidad de certificación raíz                                 |
| Servidor TLS                                        | Certificado local, clave privada para ese certificado |
| Servidor TLS con autenticación de certificados de cliente | Certificado local, clave privada, CA raíz             |
| Cliente TLS con autenticación de certificados de cliente | Certificado local, clave privada, CA raíz             |
| Cliente o servidor TLS solo con claves precompartidas    | Ninguno (se usó PSK en lugar de certificados)             |

Los servicios relevantes para cargar certificados son los siguientes:

| **API Name** (Nombre de la API)                                   | **Propósito**                                            |
| ---------------------------------------------- |------------------------------------------------------- |
| nx_secure_x509_certificate_initialize      | Se debe llamar a todos los certificados con el fin de rellenar la estructura NX_SECURE_X509_CERT con los datos y la clave privada del certificado. |
| nx_secure_tls_local_certificate_add       | Agrega un certificado local a una sesión de TLS para identificar el dispositivo.                                                                |
| nx_secure_tls_local_certificate_remove    | Quita un certificado local de una sesión de TLS.                                                                                   |
| nx_secure_tls_remote_certificate_allocate | Asigna espacio para un certificado remoto (llamado con un objeto NX_SECURE_X509_CERT no inicializado).                                   |
| nx_secure_tls_trusted_certificate_add     | Agrega un certificado a una sesión de TLS como un certificado de confianza para autenticar hosts remotos.                                     |
| nx_secure_tls_trusted_certificate_remove  | Quita un certificado de confianza de una sesión de TLS.                                                                                 |

### <a name="working-with-aws-iot-certificates"></a>Trabajo con certificados IoT de AWS

En la interfaz de IoT Amazon Web Services, seleccione “Seguridad” en el menú de la barra lateral y seleccione “Certificados”. Cree un certificado nuevo y siga las instrucciones para descargar el nuevo certificado de dispositivo.

Una vez que haya descargado los certificados, tendrá que convertirlos al formato DER mediante OpenSSL o una utilidad similar.

NOTA: AWS también proporcionará un archivo de clave pública. La clave pública está incluida en el certificado del dispositivo local, por lo que no es necesario importarla a la aplicación.

Por ejemplo, estos son los comandos para convertir el certificado de dispositivo local y su clave privada en formato DER para su uso con NetX Secure:

```C
openssl x509 -inform PEM -in <certificate> -outform DER -out cert.der
openssl x509 -inform PEM -in <root CA cert> -outform DER -out CA_cert.der
openssl rsa -inform PEM -in <private key> -outform DER -out private.key
```
Los archivos convertidos se pueden importar en la aplicación siguiendo las instrucciones anteriores.

## <a name="x509-certificate-validation-in-netx-secure"></a>Validación del certificado X.509 en NetX Secure 

Cuando se usan TLS con certificados X.509 para la identificación y comprobación del host, es importante comprender cómo se validan realmente esos certificados. Aunque la especificación de TLS no proporciona instrucciones detalladas sobre cómo validar un certificado, hace referencia a la especificación X.509 (RFC 5280). En general, se espera que TLS realice al menos la validación básica en los certificados de entrada (los certificados proporcionados por el host remoto durante el protocolo de enlace TLS) y lo mismo sucede en el servicio TLS de NetX Secure.

### <a name="basic-x509-validation"></a>Validación básica de X.509

Para cualquier certificado entrante, el servicio TLS de NetX Secure realizará la validación básica de la ruta de acceso de X.509. El proceso implica comprobar la firma digital de cada certificado con su certificado de emisor, que puede ser proporcionado por el host remoto o ubicarse en el almacén de certificados de confianza (consulte la sección “Importación de certificados X.509 en NetX Secure” para obtener más información sobre la importación de certificados de confianza). El proceso de validación se repite de forma recursiva en los certificados de emisor hasta que se llega a un certificado de confianza o finaliza la cadena (con un certificado autofirmado o un certificado de emisor que falta). Si se llega a un certificado de confianza, se comprueba el certificado; en caso contrario, se rechaza. Además, en cada fase del proceso de comprobación, se comprueba la fecha de expiración de cada certificado con respecto a la hora proporcionada por la función de marca de tiempo de la aplicación (consulte el servicio “nx_secure_tls_session_time_function_set” para obtener más información).

La especificación X.509 también proporciona un algoritmo para admitir “directivas”, que son identificadores que se encuentran en una extensión X.509 que se puede comprobar durante la validación de la ruta de acceso. NetX Secure actualmente trata los certificados X.509 como si se hubiera definido la opción “anyPolicy”, es decir, todas las directivas son aceptables y no se lleva a cabo la comprobación opcional de directivas. La implementación de X.509 en NetX Secure puede aumentar con esta característica en una versión futura. Por ahora, la extensión de la directiva se puede obtener a partir de un certificado mediante la API *nx_secure_x509_extension_find*.

Una vez completada la validación básica de la ruta de acceso, TLS invocará la devolución de llamada de comprobación de certificado proporcionada por la aplicación mediante la API *nx_secure_tls_session_certificate_callback_set*. Si no se proporciona ninguna devolución de llamada, se considera que el certificado es de confianza después de validar la ruta de acceso correcta. Si se proporciona una devolución de llamada, esta llevará a cabo cualquier validación adicional del certificado requerido por la aplicación. El valor devuelto de la devolución de llamada se usa para determinar si se debe continuar con el protocolo de enlace TLS o anularlo debido a un error de validación.

La devolución de llamada se invoca con un puntero a la sesión de TLS pertinente y un puntero NX_SECURE_X509_CERT al certificado que se va a validar. Entre la sesión de TLS y el certificado, la aplicación tiene todos los datos que necesita de TLS para realizar comprobaciones de verificación adicional.

Para ayudar con la validación adicional, NetX Secure proporciona rutinas X.509 para algunas operaciones comunes de validación, incluidas la validación de DNS y la comprobación de la lista de revocación de certificados. Todas estas rutinas son aptas para su uso dentro de la devolución de llamada de comprobación de certificado, pero también se pueden usar para realizar una comprobación sin conexión de los certificados X.509.

En la tabla siguiente se resumen las funciones auxiliares disponibles para el procesamiento de certificados X.509. En las secciones siguientes y en el capítulo 4 de la referencia de la API encontrará explicaciones más detalladas sobre las operaciones.  
  
La descripción de los servicios de NetX Secure incluye detalles adicionales sobre las rutinas específicas.

| **API Name** (Nombre de la API)                             | **Descripción**                               |
| ---------------------------------------- | -------------------------------------- |
| nx_secure_x509_common_name_dns_check               | Compara el nombre común del sujeto X.509 y SubjectAltName con un nombre DNS esperado |
| nx_secure_x509_crl_revocation_check                 | Busca un certificado revocado en una lista de revocación de certificados X.509 (CRL)       |
| nx_secure_x509_extended_key_usage_extension_parse | Analiza y busca un OID específico de uso mejorado de clave en un certificado                   |
| nx_secure_x509_key_usage_extension_parse           | Analiza y devuelve el campo de bits de uso de clave en un certificado                            |
| nx_secure_x509_extension_find                        | Busca y devuelve los datos ASN.1 sin formato con codificación DER para una extensión específica.            |

Funciones auxiliares de X.509 para su uso en la devolución de llamada de comprobación de certificado

### <a name="x509-extensions"></a>Extensiones X.509

La especificación X.509 describe una serie de “extensiones” que se pueden usar para proporcionar información adicional que se puede utilizar en la comprobación de certificados. En su mayor parte, estas extensiones son opcionales y no son necesarias para la validación segura de un certificado digital con un certificado raíz de confianza. Sin embargo, NetX Secure admite algunas extensiones básicas. Tal vez se agregue compatibilidad con extensiones adicionales en versiones futuras.

Los valores que se admiten actualmente de forma nativa son los de la lista siguiente:

| Nombre de la extensión           | Descripción                                                                   | API relevante                                             |
| ------------------------ | ----------------------------------------------------------------------------- | -------------------------------------------------------- |
| Uso de claves                | Proporciona un uso aceptable para la clave pública de un certificado en un campo de bits         | nx_secure_x509_key_usage_extension_parse           |
| Uso mejorado de clave       | Proporciona un uso aceptable adicional para la clave pública de un certificado usando OID | nx_secure_x509_extended_key_usage_extension_parse |
| Nombre alternativo del sujeto | Proporciona nombres DNS alternativos que también están representados por el certificado   | nx_secure_x509_common_name_dns_check               |

### <a name="unsupported-x509-extensions"></a>Extensiones X.509 no admitidas

La implementación de X.509 en NetX Secure proporciona un servicio para extraer también las extensiones no compatibles: *nx_secure_x509_extension_find*. Esta API está destinada a usuarios avanzados, ya que requiere un conocimiento de ASN.1 con codificación DER para analizar los datos devueltos. Se usa internamente para extraer las extensiones admitidas, pero se proporciona por comodidad en el desarrollo de la compatibilidad personalizada para las extensiones X.509.

Para usar nx_secure_x509_extension_find, se pasa un objeto NX_SECURE_X509_EXTENSION, junto con el certificado y un identificador de extensión, que es una representación con enteros de la cadena OID de longitud variable para un tipo de extensión conocido. En la página 178 de la referencia de la API de nx_secure_x509_extension_find, se proporciona una lista completa de los OID admitidos para las extensiones X.509.

La estructura NX_SECURE_X509_EXTENSION se define de la siguiente manera:

```C
typedef struct NX_SECURE_X509_EXTENSION_STRUCT
{
    /* Identifier (maps to OID) for this extension. */
    USHORT nx_secure_x509_extension_id;

    /* Critical flag - boolean value. */
    USHORT nx_secure_x509_extension_critical;

    /* Pointer to DER-encoded extension data. */
    const UCHAR *nx_secure_x509_extension_data;
    ULONG        nx_secure_x509_extension_data_length;
} NX_SECURE_X509_EXTENSION;
```
Cuando el servicio se devuelve correctamente, la estructura se rellenará con los datos pertinentes del certificado. En general, el campo nx_secure_x509_extension_id se usa para fines internos, pero se rellenará con la representación con enteros correspondiente del OID. El campo nx_secure_x509_extension_critical expone el valor de la marca de extensión crítica de X.509 (booleano). Los campos nx_secure_x509_extension_data y nx_secure_x509_extension_data_length contienen un puntero a los datos ASN.1 con codificación DER para la extensión y la longitud de esos datos, respectivamente.

El análisis real de los datos de la extensión ASN.1 está fuera del ámbito de este documento, pero si tiene acceso al origen del servicio TLS de NetX Secure, puede ver cómo se realiza el análisis dondequiera que se llame a nx_secure_x509_extension_find para las extensiones admitidas.

### <a name="x509-dns-validation"></a>Validación de DNS de X.509

Una operación de validación de certificados común en TLS implica comprobar el nombre del dominio de primer nivel (TLD) de un host remoto con el certificado X.509 proporcionado por ese host durante el protocolo de enlace TLS. Esta operación ayuda a garantizar que el certificado coincida realmente con el servidor host que lo proporcionó, suponiendo que se pueda confiar en la búsqueda de DNS. En el servicio TLS de NetX Secure, esta funcionalidad la proporciona el servicio **nx_secure_x509_common_name_dns_check**, que toma el certificado y una cadena que contiene la parte TLD de la dirección URL usada para obtener acceso al host. El TLD se compara con el campo de nombre común del certificado y, si coincide, se devuelve NX_SUCCESS. Si el nombre común no coincide, la rutina también comprobará la existencia de la extensión de certificado X.509 *subjectAltName*. Si hay presente un parámetro subjectAltName, las entradas de DNSName de la extensión también se comprueban con el TLD proporcionado. De nuevo, si se encuentra alguna coincidencia, se devuelve NX_SUCCESS. Si no se encuentra ninguna coincidencia, se devuelve un error adecuado para devolver desde la devolución de llamada de validación de certificado.

### <a name="x509-key-usage-and-extended-key-usage-extensions"></a>Uso de claves X.509 y extensiones de uso mejorado de clave

Las extensiones de uso de clave y de uso mejorado de clave de X.509 proporcionan información sobre cómo se puede usar la clave pública de un certificado al autenticar el certificado. El emisor del certificado proporciona el uso de la clave cuando el certificado se firma y se emite. El uso de clave puede ser utilizado por un host TLS para comprobar que el certificado está autorizado a usarse para autenticar un host TLS remoto y realizar otras operaciones.

La extensión de uso de clave consta de un campo de bits simple en el que cada uno de los bits representa un uso de clave específico. En la página 183 de la referencia de la API de *nx_secure_x509_key_usage_extension_parse*, se proporciona una lista completa de estos valores. Para obtener una descripción más completa de los bits de uso de clave y sus significados, consulte la sección 4.2.1.3 de la RFC 5280.

La extensión de uso mejorado de clave, al igual que la extensión de uso de clave, proporciona información de uso aceptable de claves. Sin embargo, para admitir usos arbitrarios, la extensión de uso mejorado de clave usa OID en lugar de un campo de bits. Al analizar una extensión de uso mejorado de clave de X.509 en NetX Secure, la aplicación proporciona un entero que representa el OID: el servicio *nx_secure_x509_extended_key_usage_extension_parse* devolverá si ese OID está presente. En la página 175 de la referencia de la API de *nx_secure_x509_extended_key_usage_extension_parse*, se proporciona una lista completa de los OID admitidos para el uso mejorado de clave. Para obtener una descripción más completa de los OID y sus significados, consulte la sección 4.2.1.12 de la RFC 5280.

### <a name="x509-crl-revocation-status-checking"></a>Comprobación del estado de revocación CRL de X.509

X.509 proporciona un mecanismo denominado *lista de revocación de certificados* (CRL) que permite a una autoridad de firma de certificados digitales revocar la validez de los certificados que ha firmado. Cualquier aplicación que necesite comprobar certificados de una autoridad de firma puede obtener una CRL y comparar los certificados firmados por dicha autoridad (emisor) con la CRL para ver si se ha revocado su estado por algún motivo (por ejemplo, una clave privada en peligro). De esta manera, la aplicación puede evitar el uso de certificados potencialmente peligrosos que superen otras comprobaciones de validación de certificados.

La obtención de una CRL se realiza mediante una aplicación mediante la descarga de la lista con codificación DER desde un servidor predefinido o a través de otros medios. La configuración real varía según el emisor, de modo que NetX Secure no proporciona un mecanismo para obtener las CRL, sino una rutina para comprobar un certificado en una CRL, **nx_secure_x509_crl_revocation_check**.

La API toma una CRL codificada con DER, un almacén de certificados (como el de una sesión de TLS) con el que se va a realizar la comprobación y el certificado que se va a comprobar. La rutina valida primero la CRL en el almacén de confianza (parte del almacén de certificados proporcionado por la aplicación). Esto es importante para protegerse frente a las CRL fraudulentas que se usan para los ataques por denegación de servicio y establece que la CRL es realmente del emisor adecuado. Después de la validación de CRL, se comprueba el emisor: si el emisor de la CRL no coincide con el emisor del certificado, la CRL no es válida para ese certificado y se devuelve un error. Depende de la aplicación determinar si el protocolo de enlace TLS puede continuar en este momento. Si los emisores coinciden, se busca en la CRL el número de serie del certificado que se está validando. Si el número de serie está presente en la lista, se devuelve un error que indica que se ha revocado el certificado. Si no se encuentra alguna coincidencia, se devuelve NX_SUCCESS.

## <a name="client-certificate-authentication-in-netx-secure-tls"></a>Autenticación de certificados de cliente en el servicio TLS de NetX Secure

Al usar la autenticación de certificados X.509, el protocolo TLS requiere que la instancia del servidor TLS proporcione un certificado para la identificación. Sin embargo, de forma predeterminada, la instancia de cliente TLS no tiene que proporcionar un certificado para la autenticación y puede usar otra forma de autenticación (por ejemplo, una combinación de nombre de usuario/contraseña). Esto coincide con el uso más común de TLS para sitios Web en Internet. Por ejemplo, un sitio de venta directa en línea debe demostrar a un cliente potencial que use un explorador Web que el servidor es legítimo, pero el usuario empleará un inicio de sesión y una contraseña para tener acceso a una cuenta específica.

Sin embargo, el caso predeterminado no siempre es el aconsejable, por lo que DTLS permite a la instancia del servidor TLS solicitar un certificado del cliente remoto. Cuando esta característica está habilitada, el servidor TLS enviará un mensaje CertificateRequest al cliente TLS durante el protocolo de enlace. El cliente debe responder con un certificado propio y un mensaje CertificateVerify que contenga un token criptográfico que demuestre que el cliente posee la clave privada correspondiente asociada a ese certificado. Si se produce un error en la comprobación o el certificado no está conectado a un certificado de confianza en el servidor, se produce un error en el protocolo de enlace TLS.

Hay dos casos independientes para la autenticación de certificados de cliente en TLS: en las secciones siguientes se tratan ambos casos.

### <a name="client-certificate-authentication-for-tls-clients"></a>Autenticación de certificados de cliente para clientes TLS

Un cliente TLS puede intentar una conexión a un servidor que solicite un certificado para la autenticación del cliente. En este caso, el cliente debe proporcionar un certificado al servidor y comprobar que posee la clave privada correspondiente; si no, el servidor finalizará el protocolo de enlace TLS.

En el servicio TLS de NetX Secure, no hay ninguna configuración especial para admitir esta característica, pero la aplicación tendrá que proporcionar un certificado de identificación local para la instancia de cliente TLS mediante el servicio *nx_secure_tls_local_certificate_add*. Si la aplicación no proporciona ningún certificado pero el servidor remoto usa la autenticación de certificado de cliente y solicita un certificado, se producirá un error en el protocolo de enlace TLS. El servidor remoto debe reconocer el certificado proporcionado a la sesión TLS con *nx_secure_tls_local_certificate_add* para poder completar el protocolo de enlace TLS.

### <a name="client-certificate-authentication-for-tls-servers"></a>Autenticación de certificados de cliente para servidores TLS

El caso del servidor TLS para la autenticación de certificados de cliente es ligeramente más complejo que el caso del cliente TLS, ya que la característica es opcional. En este caso, el servidor TLS necesita solicitar específicamente un certificado de cliente TLS remoto y, seguidamente, procesar el mensaje CertificateVerify para comprobar que el cliente remoto es el propietario de la clave privada correspondiente. A continuación, el servidor debe comprobar que se puede realizar un seguimiento del certificado proporcionado por el cliente hasta un certificado del almacén local de certificados de confianza.

En las instancias del servidor TLS de NetX Secure, la autenticación de certificados de cliente se controla mediante <br>
los servicios *nx <span class="underline"> _</span>secure <span class="underline">_</span>tls <span class="underline"> _</span>session <span class="underline">_</span>client <span class="underline"> _</span>verify<span class="underline">_</span>enable* y<br>
*nx <span class="underline"> _</span>secure <span class="underline">_</span>tls <span class="underline"> _</span>session <span class="underline">_</span>client <span class="underline"> _</span>verify<span class="underline">_</span>disable*.

Para habilitar la autenticación de certificados de cliente, una aplicación debe llamar a<br>
*nx <span class="underline"> _</span>secure <span class="underline">_</span>tls <span class="underline"> _</span>session <span class="underline">_</span>client <span class="underline"> _</span>verify <span class="underline">_</span>enable* con la instancia de sesión del servidor TLS antes de llamar a *nx_secure_tls_session_start*. Tenga en cuenta que llamar a este servicio en una sesión de TLS que se usa para las conexiones de cliente TLS no tendrá ningún efecto.

Cuando se habilita la autenticación de certificados de cliente, el servidor TLS solicitará un certificado de cliente TLS remoto durante el protocolo de enlace TLS. En el servidor TLS de NetX Secure, el certificado de cliente se compara con el almacén de certificados de confianza creados con *nx <span class="underline"> _</span>secure_tls <span class="underline">_</span>trusted <span class="underline"> _</span>certificate<span class="underline">_</span>add* siguiendo la cadena de emisor X.509. El cliente remoto debe proporcionar una cadena que conecte su certificado de identidad con un certificado en el almacén de confianza; de lo contrario, se producirá un error en el protocolo de enlace TLS. Además, si se produce un error en el procesamiento del mensaje CertificateVerify, también se producirá un error en el protocolo de enlace TLS.

Los métodos de firma que se usan para el método CertificateVerify son fijos para la versión de TLS 1.0 y la versión TLS 1.1; se especifican mediante el servidor TLS en la versión TLS 1.2. En el caso de TLS 1.2, los métodos de firma admitidos generalmente siguen los métodos pertinentes suministrados en la tabla de métodos criptográficos, pero normalmente RSA con SHA-256 (consulte la sección “Criptografía el servicio TLS de NetX Secure” para obtener más información sobre cómo inicializar TLS con métodos criptográficos).

## <a name="cryptography-in-netx-secure-tls"></a>Criptografía en el servicio TLS de NetX Secure

TLS define un protocolo en el que se puede usar la criptografía para proteger las comunicaciones de red. Como tal, permite que los usuarios de TLS puedan usar el cifrado real de forma bastante amplia. La especificación solo requiere la implementación de un único conjunto de cifrado. En el caso de TLS 1.2, el conjunto es TLS_RSA_WITH_AES_128_CBC_SHA, que indica el uso de RSA para las operaciones de clave pública, AES en modo CBC con claves de 128 bits para el cifrado de sesión y SHA-1 para los hash de autenticación de mensajes.

Al ser compatible con TLS 1.2, NetX Secure habilita el conjunto de cifrado obligatorio TLS_RSA_WITH_AES_128_CBC_SHA de forma predeterminada, pero dado el número de implementaciones posibles para cada uno de los métodos criptográficos debido a las capacidades de hardware y otras consideraciones, NetX Secure proporciona una API criptográfica genérica que permite a los usuarios especificar qué métodos criptográficos usar con TLS.

NOTA: el mecanismo genérico de la API criptográfica también permite a los usuarios implementar sus propios conjuntos, pero esto solo se recomienda a los usuarios avanzados que están familiarizados con las extensiones y conjuntos de cifrado de TLS. Póngase en contacto con su representante de Logic Express si está interesado en usar sus propios conjuntos de cifrado.

### <a name="cryptographic-methods"></a>Métodos criptográficos

El servicio TLS de NetX Secure implementa DES, 3DES, AES, MD5, HMAC-MD5, SHA-1, HMAC-SHA1, SHA-256, HMAC-SHA256, RSA y ECC (curvas seleccionadas) en el software con controladores de hardware para determinadas plataformas de hardware. Una aplicación puede usar las rutinas criptográficas proporcionadas con NetX Secure o usar rutinas personalizadas proporcionadas por el usuario final o por terceros.

*NX_CRYPTO_METHOD* es un bloque de control diseñado para que una aplicación describa una implementación concreta de un algoritmo criptográfico que se va a usar con el servicio TLS de NetX Secure. Con *NX_CRYPTO_METHOD,* una aplicación puede integrar fácilmente su propia implementación de cifrado en NetX Secure. La estructura *NX_CRYPTO_METHOD* se declara como:

```C
typedef struct NX_CRYPTO_METHOD_STRUCT
{
    /* Symbolic name of the algorithm. */
    USHORT nx_crypto_algorithm;

    /* Size of the key, in bits. */
    USHORT nx_crypto_key_size_in_bits;

    /* Size of the IV block, in bits, used for encryption. */
    USHORT nx_crypto_IV_size_in_bits;

    /* Size of the ICV block, in bits, used for authentication. */
    USHORT nx_crypto_ICV_size_in_bits;

    /* Size of the crypto block, in bytes. */
    ULONG nx_crypto_block_size_in_bytes;

    /* Size of the metadata area. */
    ULONG nx_crypto_metadata_size;

    /* nx_crypto_init function initializes the crypto method with the
        "secret key" or other state  information. The initialization 
        routine should return a handle to the caller.  This handle is 
        used in subsequent crypto operations to identify the session.  
        */

    UINT (*nx_crypto_init) (NX_CRYPTO_METHOD     *method,
                            UCHAR               *key, 
                            NX_CRYPTO_KEY_SIZE   key_size_in_bits,
                            VOID               **handler,
                            VOID                *crypto_metadata,
                            VOID                 crypto_metadata_size);

    /* NetX Secure calls the nx_crypto_cleanup routine when a TLS
       session is to be deleted (or updated).  Resources allocated 
       during the crypto operation should be released in this routine.  
       */
    UINT (*nx_crypto_cleanup) (VOID *handler);

    /* nx_crypto_operation is the actual crypto or hash operation. Note 
       that both input and output buffers are prepared by the caller. 
       For encryption or decryption operations, the crypto operation 
       routine uses the output buffer for encrypted or decrypted data. 
       For authentication operations, the authentication routine shall 
       use the output buffer for the digest. */
    UINT (*nx_crypto_operation)(UINT  op, 
                  VOID              *handler, 
                  NX_CRYPTO_METHOD  *method,
                  UCHAR             *key,
                  NX_CRYPTO_KEY_SIZE key_size_in_bits,
                  UCHAR             *input,
                  ULONG              input_length_in_byte,
                  UCHAR             *iv_ptr,
                  UCHAR             *output,
                  ULONG              output_length_in_byte,
                  VOID              *crypto_metadata,
                  VOID               crypto_metadata_size,
                  NX_PACKET*         packet_ptr,
                  VOID (*nx_crypto_hw_process_callback(NX_PACKET 
                                                       *packet_ptr, 
                                                        UINT status);
} NX_CRYPTO_METHOD;
```

A continuación se muestra la descripción de cada elemento de la estructura *NX_CRYPTO_METHOD*:

- nx_crypto_algorithm: este campo identifica el algoritmo descrito en la variable *METHOD*. Algunos valores válidos para el servicio TLS de NetX Secure son los siguientes (consulte nx_crypto_const. h para ver los valores específicos):
    
  - NX_CRYPTO_NONE    
  - NX_CRYPTO_ENCRYPTION_NULL    
  - NX_CRYPTO_ENCRYPTION_AES_CBC    
  - NX_CRYPTO_AUTHENTICATION_NONE    
  - TLS_HASH_SHA_1    
  - TLS_HASH_SHA_256    
  - TLS_HASH_MD5    
  - TLS_CIPHER_RSA    
  - TLS_CIPHER_NULL

- nx_crypto_key_size_in_bits: este campo especifica el tamaño de la clave secreta utilizada por el método.

- nx_crypto_IV_size_in_bits: este campo especifica el tamaño del vector de inicialización (IV). Tenga en cuenta que en la mayoría de los casos el bloque IV solo se usa para los algoritmos de cifrado y descifrado. Los algoritmos de autenticación y comprobación suelen usar este campo.

- nx_crypto_ICV_size_in_bits: este campo especifica el tamaño del bloque de valor de comprobación de integridad (ICV). NOTA: este bloque es para uso de IPsec y no se usa en TLS. Para obtener más información, consulte el servicio IPsec de NetX Duo.

- nx_crypto_block_size_in_bytes: este campo especifica el tamaño del bloque de algoritmos criptográficos para los cifrados basados en bloques (en bytes). En la mayoría de los casos, lo usan las rutinas de cifrado y raramente las rutinas de autenticación.

- nx_crypto_metadata_area_size: este campo especifica el tamaño del área de metadatos que requiere este método. Cada implementación puede requerir cierta memoria para almacenar su información de estado, para almacenar datos intermedios (como material de transformación de claves) o para usarlos como un área de borrador. En este campo se especifica la cantidad de espacio necesario para una implementación. La aplicación proporciona el espacio de memoria al crear una sesión de TLS. La función criptográfica es responsable de administrar esta área de metadatos.

- nx_crypto_init: se trata de la función de inicialización para el algoritmo criptográfico. En una implementación que no necesita una rutina de inicialización, este campo se puede establecer en NX_NULL. Un uso típico de una función de inicialización es inicializar la estructura de datos interna para el algoritmo. El servicio TLS de NetX Secure administrará la inicialización de la rutina criptográfica llamando a esta función internamente.

El prototipo de la función de inicialización es:

```C
UINT crypto_init_function(NX_CRYPTO_METHOD *method, 
                          UCHAR *key, 
                          UINT  key_size_in_bits, 
                          VOID  **handle, 
                          VOID  *crypto_metadata_area, 
                          ULONG crypto_metadata_area_size);
```

  - “method” es un puntero al bloque de control del método criptográfico.

  - “key” es la cadena de clave secreta para procesar los paquetes de datos.

  - “key_size_in_bits” define el tamaño de la clave secreta en bits.

  - “handle” es un elemento definido por la implementación que identifica una sesión de cifrado determinada. El valor se genera mediante la rutina de inicialización y se devuelve al autor la llamada. La siguiente operación de cifrado o rutina de limpieza utiliza este identificador para identificar la sesión.

  - “crypto_metadata” es un puntero al área de metadatos que requiere la implementación de este algoritmo. En el caso de los algoritmos que no necesitan un área de metadatos, este campo se establece en NX_NULL y la rutina de inicialización no debe tener acceso al área de metadatos.

  - “crypto_metadata_size” especifica el tamaño del área de metadatos. En el caso de los algoritmos que no necesitan un área de metadatos, este campo se establece en NX_NULL y la rutina de inicialización no debe tener acceso al área de metadatos.

  - Esta rutina devolverá *NX_SUCCESS* si el proceso de inicialización se realiza correctamente. El autor de llamada trata cualquier otro valor devuelto como error.

- nx_crypto_cleanup: se trata de la rutina de limpieza definida para la implementación de un algoritmo criptográfico. Se invoca cuando se elimina o se reinicia una sesión de TLS.

El prototipo de la función de limpieza es:

```C
UINT crypto_cleanup_function(VOID *handle);
```
- El autor de llamada pasa “handle” a la función de limpieza. La rutina de inicialización de cifrado inicializa “handle” y se usa para identificar el estado del algoritmo criptográfico.

- Esta rutina devolverá *NX_SUCCESS* si el proceso de limpieza se realiza correctamente. El autor de llamada trata cualquier otro valor devuelto como error.

- nx_crypto_operation: se trata de la rutina que realiza los servicios de cifrado, descifrado y autenticación reales. El prototipo de función de la rutina de operación es:

```C
UINT crypto_operation_function(UINT   op,
          VOID  *handle,  
          NX_CRYPTO_METHOD* method,
          UCHAR *key,
          UCHAR  key_size_in_bits,
          UCHAR* input,
          ULONG  input_length_in_byte,
          UCHAR* iv_ptr,
          UCHAR* output,
          ULONG  output_length_in_byte,
          VOID *crypto_metadata,
          ULONG crypto_metadata_size,
          NX_PACKET *packet_ptr,
          VOID (*nx_crypto_hw_process_callback)(NX_PACKET 
                          *packet_ptr, UINT status));
```

- “op” indica el tipo de operación que se espera que lleve a cabo esta rutina. Los valores válidos son:
    
    - NX_CRYPTO_ENCRYPT
    - NX_CRYPTO_DECRYPT
    - NX_CRYPTO_AUTHENTICATE
    - NX_CRYPTO_VERIFY

- El autor de llamada pasa “handle” a la función de operación. Se genera mediante la rutina de inicialización de cifrado.
- “method” apunta al bloque de control del método criptográfico.
- “key” apunta a la clave secreta utilizada para esta operación.
- “key_size_in_bits” es el tamaño de la clave secreta en bits.
- “input” es un puntero al principio del mensaje en el que se va a operar.
- el autor de la llamada pasa input_length_in_byte para indicar el tamaño del mensaje en el que se van a realizar operaciones.
- El autor de llamada configura “iv_ptr” para que apunte al principio de un bloque IV. Tenga en cuenta que el autor de llamada proporciona la memoria para el bloque IV. En el cifrado, la función de operación debe escribir la información de IV en este bloque de memoria; en el descifrado, la función de operación debe recuperar la información de IV de este bloque de memoria. Normalmente, los algoritmos para la operación de autenticación y comprobación no usan el vector de inicialización.
- El autor de llamada configura “output” para que apunte a un búfer de salida. Tenga en cuenta que el autor de llamada proporciona la memoria para el búfer de salida. En el cifrado, la función de operación debe escribir el texto cifrado en el búfer de salida; en el descifrado, la operación debe escribir el texto descifrado (texto sin cifrar) en el búfer de salida; en la autenticación, el valor hash se escribirá en el búfer de salida. En la comprobación, el búfer de salida se usa para almacenar información de hash.
- “output_length_in_byte” indica el tamaño del búfer de salida.
- “crypto_metadata” apunta al área de metadatos que va a usar esta operación de cifrado. Normalmente, “crypto_init_function” inicializa el área de metadatos de cifrado.
- “crypto_metadata_size” indica el tamaño del área de metadatos.
- Esta rutina devolverá *NX_SUCCESS* si el proceso de operación se realiza correctamente. El autor de llamada trata cualquier otro valor devuelto como error.
- “packet_ptr”: el paquete que contiene los datos que se están procesando. NOTA: TLS no usa este parámetro y debe establecerse en NX_NULL.
- “nx_crypto_hw_process_callback”: una función de devolución de llamada proporcionada por el método de cifrado. Se usa si el hardware proporciona la función de cifrado y requiere una rutina de devolución de llamada.

El servicio TLS de NetX Secure proporciona los siguientes métodos de cifrado:

- *AES*  
- *RSA*  
- *NULL*

El servicio TLS de NetX Secure proporciona los siguientes métodos de autenticación:

- *HMAC-MD5*  
- *HMAC-SHA1*  
- *HMAC-SHA256*

En los siguientes ejemplos se muestra cómo configurar la estructura *NX_CRYPTO_METHOD* para usar los métodos de cifrado y de autenticación proporcionados por el servicio IPSec de NetX Duo.

***AES:***

```C
/* AES-CBC 128. */
NX_CRYPTO_METHOD crypto_method_aes_cbc_128 = 
{
    /* AES crypto algorithm                             */
    NX_CRYPTO_ENCRYPTION_AES_CBC,                       

    /* Key size in bits. For AES-128 this value is 128  */
    NX_CRYPTO_AES_128_KEY_LEN_IN_BITS,              
   
    /* IV size in bits.  For AES-128 this value is 128  */
    NX_CRYPTO_AES_IV_LEN_IN_BITS,

    /* ICV size in bits, not used.                      */
    0,                                              

    /* Block size in bytes.  For AES this value is 16   */
    (NX_CRYPTO_AES_BLOCK_SIZE_IN_BITS >> 3),        

    /* Metadata size in bytes, for AES this value is 262*/
    sizeof(NX_CRYPTO_AES),              

    /* AES-CBC initialization routine.                  */
    _nx_secure_crypto_method_aes_init,               

    /* AES-CBC cleanup routine, not used.               */
    NX_NULL,                                        

    /* AES-CBC operation                                */
    _nx_secure_crypto_method_aes_operation           
};

/* RSA. */
NX_CRYPTO_METHOD crypto_method_rsa = 
{
    /* RSA crypto algorithm                             */
    TLS_CIPHER_RSA,                       

    /* Key size. RSA key sizes vary, so set to 0.         */
    0,              
   
    /* IV size in bits.  RSA does not use an IV.         */
    0,

    /* ICV size in bits, not used.                      */
    0,                                              

    /* Block size in bytes.  RSA does not have a block size. */
    0,        

    /* Metadata size in bytes, for RSA use the control block. */
    sizeof(NX_CRYPTO_RSA),              

    /* RSA initialization routine.                  */
    _nx_secure_crypto_method_rsa_init,               

    /* Cleanup routine, not used.                    */
    NX_NULL,                                        

    /* RSA operation                                */
    _nx_secure_crypto_method_rsa_operation           

};
```
***NULL***

```C
/* NULL encryption method. */
NX_CRYPTO_METHOD crypto_method_null = 
{
    NX_CRYPTO_ENCRYPTION_NULL,/* Name of the crypto algorithm  */
    0,                        /* Key size in bits, not used    */
    0,                        /* IV size in bits, not used     */
    0,                        /* ICV size in bits, not used    */
    4,                        /* Block size in bytes           */
    0,                        /* Metadata size in bytes        */
    NX_NULL,                  /* Initialization routine,unused */
    NX_NULL,                  /* Cleanup routine, not used     */
    _nx_secure_crypto_method_null_operation  /* NULL operation  
*/
}; 
```
***HMAC-SHA1***
```C
NX_CRYPTO_METHOD crypto_method_hmac_sha1 = 
{
    /* HMAC SHA1 algorithm                               */
    TLS_HASH_SHA1,            


    /* Key size in bits. For HMAC-SHA1 this value is 160 */ 
    NX_CRYPTO_HMAC_SHA1_KEY_LEN_IN_BITS,              

    /* IV size in bits, not used                         */
    0,                                            

    /* Transmitted ICV size in bits. Unused.             */
    0, 

    /* Block size in bytes, not used                     */
    0,                                            

    /* Metadata size in bytes                            */
    sizeof(NX_SHA1_HMAC),                                            

    /* Initialization routine, not used                  */
    NX_NULL,                                      

    /* Cleanup routine, not used                         */
    NX_NULL,                                          

    /* HMAC SHA1 operation                               */
    _nx_secure_crypto_method_hmac_sha1_operation   
};
```
***NONE***

Se usa un método especial **NX_CRYPTO_NONE** para indicar al módulo IPsec que el cifrado o el servicio de autenticación no son necesarios. Se configura de la siguiente manera:

```C
/* NX_CRYPTO_NONE means encryption or authentication
   method is not needed.  */
NX_CRYPTO_METHOD crypto_method_none = 
{
    NX_CRYPTO_NONE,       /* Name of the crypto algorithm */
    0,                    /* Key size in bits, not used   */
    0,                    /* IV size in bits, not used    */
    0,                    /* ICV size in bits, not used   */
    0,                    /* Block size in bytes          */
    0,                    /* Metadata size in bytes       */
    NX_NULL,              /* Initialization routine, not used */
    NX_NULL,              /* Cleanup routine, not used    */
    NX_NULL               /* NULL operation               */
};                                               
```
### <a name="initializing-tls-with-cryptographic-methods"></a>Inicialización de TLS con métodos criptográficos

Una vez creadas las rutinas criptográficas conforme a las firmas de métodos criptográficos descritas en la sección anterior, tendrá que pasarlas a TLS al inicializar un bloque de control NX_SECURE_TLS_SESSION. Esto se hace en el servicio TLS nx_secure_tls_session_create:

```C
UINT  nx_secure_tls_session_create(
              NX_SECURE_TLS_SESSION*     session_ptr,
              const NX_SECURE_TLS_CRYPTO*    tls_cipher_table,
              VOID*                encryption_metadata_area,
              ULONG                 encryption_metadata_size
);
```
- “session_pointer” es un puntero al bloque de control NX_SECURE_TLS_SESSION.
- “tls_cipher_table” es un puntero a un bloque de control NX_SECURE_TLS_CRYPTO, que se describe a continuación.
- “encryption_metadata_area” apunta al espacio utilizado por las rutinas criptográficas en TLS.
- “encryption_metadata_size” es el tamaño del área de metadatos en bytes.

### <a name="elliptic-curve-cryptography-ecc-in-netx-secure-tls"></a>Criptografía de curva elíptica (ECC) en el servicio TLS de NetX Secure

La criptografía de curva elíptica (ECC) proporciona un esquema de criptografía de clave pública que se puede usar en lugar de RSA. ECC suele ser más rápido y usa claves más pequeñas que RSA, por lo que puede ser una opción valiosa para TLS integrado. En las versiones de X-Ware anteriores a Azure RTOS 6.0, ECC se distribuía como un complemento que requería la instalación del código fuente ECC en el proyecto. Azure RTOS 6.0 ha integrado ECC en el código base principal, por lo que ya no es necesario instalar los archivos ECC. Sin embargo, ECC todavía requiere la misma inicialización que las versiones anteriores.

### <a name="supported-ecc-curves"></a>Curvas ECC admitidas

NetX Secure implementa partes de las curvas según <http://www.secg.org/sec2-v2.pdf>. Se admiten las siguientes curvas<sup>18</sup>:

  - secp256r1 
  - secp384r1 
  - secp521r1 

Si se usan otras curvas ECC, la rutina *nx_secure_tls_session_start ()* devolverá el error NX_SECURE_TLS_NO_SUPPORTED_CIPHERS, que indica que se han usado curvas no compatibles.

Tenga en cuenta que la cadena de certificados de TLS también se puede cifrar mediante algoritmos ECC. Aunque se admiten las curvas proporcionadas por el cliente TLS, es posible que no se admita la curva ECC usada en la cadena de certificados. En este caso, la rutina *nx_secure_tls_session_start* devuelve NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER.

En nx_crypto_generic_ciphersuites. c se proporciona un ejemplo de tabla de conjuntos de cifrado predeterminados para ECC. Consulte la sección “Tabla de cifrado criptográfico de TLS” para obtener más información sobre las tablas de conjuntos de cifrado.

18. Tenga en cuenta que las implementaciones para las curvas secp192r1 y secp224r1are también se proporcionan para las aplicaciones heredadas. Sin embargo, estas curvas ahora se consideran débiles y no deben usarse para el desarrollo de nuevas aplicaciones.

### <a name="crypto-methods-for-ecc"></a>Métodos criptográficos para ECC

Métodos criptográficos para grupos de curva elíptica:

- NX_CRYPTO_METHOD crypto_method_ec_secp192<sup>15</sup>;  
- NX_CRYPTO_METHOD crypto_method_ec_secp224<sup>15</sup>;  
- NX_CRYPTO_METHOD crypto_method_ec_secp256;  
- NX_CRYPTO_METHOD crypto_method_ec_secp384;  
- NX_CRYPTO_METHOD crypto_method_ec_secp521;

Los métodos criptográficos para las curvas ECC se definen en nx_crypto_generic_ciphersuites.c.

Método criptográfico para ECDHE:

- NX_CRYPTO_METHOD crypto_method_ecdhe;

Crypto method for ECDSA:

- NX_CRYPTO_METHOD crypto_method_ecdsa;

Los métodos criptográficos ECDSA y ECDHE se definen en nx_crypto_generic_ciphersuites.c.

Combinado con otros métodos de cifrado, como RSA, SHA, AES, se pueden usar como bloques de creación para la tabla de búsqueda de conjuntos de cifrado.

### <a name="enabling-ecc-support-for-tls"></a>Habilitación de la compatibilidad con ECC para TLS

ECC está habilitado de forma predeterminada para TLS. Para deshabilitar la compatibilidad con ECC, se debe definir el símbolo NX_SECURE_DISABLE_ECC_CIPHERSUITE.

Para que el cambio surta efecto, debe volver a generar la biblioteca de NetX Secure y todas las aplicaciones que usen esa biblioteca.

En el código de la aplicación, se debe llamar a la API n *x_secure_tls_ecc_initialize ()* después de crear la sesión de TLS. Esta API notifica a la sesión de TLS el tipo de curvas que se va a usar para las operaciones de intercambio de claves TLS y la comprobación de certificados. Durante la fase de protocolo de enlace TLS, si se selecciona un algoritmo de ECC, los parámetros relacionados con la curva ECC de intercambio de cliente y servidor determinan la curva que se usará.

El siguiente fragmento de código muestra cómo se debe usar la API. Tenga en cuenta que todos los argumentos (*nx_crypto_ecc_supported_groups, nx_crypto_ecc_supported_groups_size, and nx_crypto_ecc_curves)* se definen en *nx_crypto_generic_ciphersuites.c*. Por lo tanto, estos símbolos se pueden usar directamente.

```C
status = nx_secure_tls_ecc_initialize(&tls_session,     
                    nx_crypto_ecc_supported_groups,      
                    nx_crypto_ecc_supported_groups_size,     
                    nx_crypto_ecc_curves);
```
La configuración de ejemplo de nx_crypto_generic_ciphersuites.c contiene una tabla de búsqueda de conjuntos de cifrado ECC que se utiliza cuando se habilita ECC. Para usar ECC, solo tiene que pasar nx_crypto_tls_ciphers_ecc como el parámetro de la tabla de conjuntos de cifrado al crear sesiones de TLS con nx_secure_tls_session_create. La tabla de ejemplo contiene ECC y no conjuntos de cifrado ECC.

### <a name="tls-cryptographic-cipher-table"></a>Tabla de cifrado criptográfico de TLS

La estructura NX_SECURE_TLS_CRYPTO se define como:

```C
typedef struct NX_SECURE_METHODS_STRUCT
{
    /* Table that maps ciphersuites to crypto methods. */
    NX_SECURE_TLS_CIPHERSUITE_INFO* nx_secure_tls_ciphersuite_lookup_table;
    USHORT nx_secure_tls_ciphersuite_lookup_table_size;

    /* Table that maps X.509 cipher identifiers to crypto methods. */
    NX_SECURE_X509_CRYPTO *nx_secure_tls_x509_cipher_table;
    USHORT nx_secure_tls_x509_cipher_table_size;

    /* Specific routines needed for specific TLS versions. */
#if (NX_SECURE_TLS_TLS_1_0_ENABLED || NX_SECURE_TLS_TLS_1_1_ENABLED)
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_md5_method;
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_sha1_method;
    NX_CRYPTO_METHOD *nx_secure_tls_prf_1_method;
#endif

#if (NX_SECURE_TLS_TLS_1_2_ENABLED)
    NX_CRYPTO_METHOD *nx_secure_tls_handshake_hash_sha256_method;
    NX_CRYPTO_METHOD *nx_secure_tls_prf_sha256_method;
#endif

#if (NX_SECURE_TLS_TLS_1_3_ENABLED)
    const NX_CRYPTO_METHOD *nx_secure_tls_hkdf_method;
    const NX_CRYPTO_METHOD *nx_secure_tls_hmac_method;
    const NX_CRYPTO_METHOD *nx_secure_tls_ecdhe_method;
#endif

} NX_SECURE_TLS_CRYPTO;
```
La tabla se crea rellenando las entradas de esta estructura en una constante estática ubicada en el proyecto TLS de NetX Secure, que normalmente se encuentra en las rutinas criptográficas y los módulos.

Por ejemplo, la biblioteca criptográfica de solo software (“genérica”) proporcionada con NetX Secure contiene la siguiente definición de tabla (para la compatibilidad con conjuntos de cifrado que no son ECC<sup>19</sup>):

```C
/* Define the cipher table object we can pass into TLS. */
const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers =
{
    /* TLS Ciphersuite lookup table and size. */
    _nx_crypto_ciphersuite_lookup_table,
    sizeof(_nx_crypto_ciphersuite_lookup_table) / 
    sizeof(NX_SECURE_TLS_CIPHERSUITE_INFO),

    /* X.509 certificate cipher table and size. */
    _nx_crypto_x509_cipher_lookup_table,
    sizeof(_nx_crypto_x509_cipher_lookup_table) / sizeof(NX_SECURE_X509_CRYPTO),

    /* TLS version-specific methods. */
#if (NX_SECURE_TLS_TLS_1_0_ENABLED || NX_SECURE_TLS_TLS_1_1_ENABLED)
    &crypto_method_md5,
    &crypto_method_sha1,
    &crypto_method_tls_prf_1,
#endif

#if (NX_SECURE_TLS_TLS_1_2_ENABLED)
    &crypto_method_sha256,
    &crypto_method_tls_prf_sha_256
#endif

#if (NX_SECURE_TLS_TLS_1_3_ENABLED)
    &crypto_method_hkdf,
    &crypto_method_hmac,
    &crypto_method_ecdhe,
#endif
};
```
En la estructura, la primera entrada es la tabla de conjuntos de cifrado de TLS. La estructura NX_SECURE_TLS_CIPHERSUITE_INFO asigna las rutinas criptográficas (en forma de punteros de NX_CRYPTO_METHOD) a conjuntos de cifrado específicos, tal como se define en las especificaciones de TLS. El segundo valor es el número de entradas de la tabla a las que apunta el primer campo.

El campo siguiente apunta a una tabla de rutinas que usa X.509 al procesar certificados digitales y el formato de la estructura NX_SECURE_X509_CRYPTO es similar a NX_SECURE_TLS_CIPHERSUITE_INFO. El siguiente campo es el número de entradas de la tabla.

Después de la tabla de búsqueda hay una serie de rutinas necesarias para las versiones específicas de TLS. Por ejemplo, antes de TLS 1.2, las rutinas de generación de claves y hash de protocolo de enlace se corrigieron para usar una combinación de SHA-1 y MD5; los métodos de estas rutinas se llaman específicamente en la estructura de cifrado, ya que no están vinculados a conjuntos de cifrado específicos. En TLS 1.2, las rutinas de generación de claves y hash se eligen mediante el conjunto de cifrado, pero para conjuntos de cifrado que no especifican las rutinas que se van a usar, se usa el método hash SHA-256 y la estructura de cifrado llama específicamente a esa rutina.

TLS 1.3 requiere algunos cifrados específicos adicionales para varias operaciones.

19. Tenga en cuenta que la compatibilidad con TLS 1.3 requiere ECC: el uso de nx_crypto_tls_ciphers_ecc si TLS 1,3 está habilitado.

### <a name="tls-ciphersuite-lookup-table"></a>Tabla de búsqueda de conjuntos de cifrado de TLS

Para rellenar la tabla de cifrado para TLS, también deberá crear una tabla de búsqueda de conjuntos de cifrado que asigne rutinas criptográficas a identificadores de conjuntos de cifrado específicos. Los identificadores son valores registrados por IANA que son universales. Consulte las RFC de TLS para obtener más información. Las rutinas representan los 5 métodos independientes usados en cada conjunto de cifrado (algunos conjuntos no pueden usar los 5): cifrado público, autenticación de clave pública, cifrado de sesión, rutina de hash de sesión y función de pseudoaleatoria de TLS (PRF). En la tabla siguiente se explica cada uno de los cinco métodos:

| **Categoría de rutina**      | **Descripción**                                                                                       | **Algoritmos de ejemplo**                                            |
| ------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Cifrado público             | Se usa para intercambiar claves durante el protocolo de enlace TLS                                                        | RSA, Diffie-Hellman, ECC                                          |
| Autenticación de clave pública | Se usa para autenticar o firmar datos durante el protocolo de enlace TLS                                            | RSA, DSS                                                          |
| Cifrado de sesión            | Algoritmo de clave simétrica que se usa para cifrar los datos de la aplicación durante la sesión de TLS                       | AES, RC4                                                          |
| Hash de sesión              | Se usa para conservar la integridad de los mensajes durante la sesión de TLS (garantiza que los datos no han cambiado) | SHA-1, SHA-256                                                    |
| PRF DE TLS                   | Se usa para generar material de clave y en el hash de protocolo de enlace del protocolo de enlace TLS.                          | La PRF se basa en rutinas hash (SHA-1 + MD5, SHA-256, SHA-512). |

La estructura NX_SECURE_TLS_CIPHERSUITE_INFO se define de la siguiente manera:

```C
typedef struct NX_SECURE_TLS_CIPHERSUITE_INFO_struct
{
    /* The IANA value of the ciphersuite as defined by the TLS spec.*/
    USHORT nx_secure_tls_ciphersuite;

    /* The Public Key operation in this suite - RSA or DH. */
    NX_CRYPTO_METHOD *nx_secure_tls_public_cipher;

    /* The Public Authentication method used for signing data. */
    NX_CRYPTO_METHOD *nx_secure_tls_public_auth;

    /* The session cipher being used - AES, RC4, etc. */
    NX_CRYPTO_METHOD *nx_secure_tls_session_cipher;

    /* The size of the initialization vectors for the session cipher (bytes).*/
    USHORT nx_secure_tls_iv_size;

    /* The key size for the session cipher (bytes). */
    UCHAR nx_secure_tls_session_key_size;

    /* The hash being used - MD5, SHA-1, SHA-256, etc. */
    NX_CRYPTO_METHOD *nx_secure_tls_hash;

    /* The size of the hash being used. SHA-1 is 20 bytes, MD5 is 16 bytes.*/
    USHORT nx_secure_tls_hash_size;

    /* The TLS PRF being used – this is only for TLSv1.2. */
    NX_CRYPTO_METHOD *nx_secure_tls_prf;

} NX_SECURE_TLS_CIPHERSUITE_INFO;
```
El campo nx_secure_tls_ciphersuite contiene el valor de conjunto de cifrado de IANA y los punteros de NX_CRYPTO_METHOD representan los 5 métodos usados por dicho conjunto. Los valores escalares (nx_secure_tls_iv_size, nx_secure_tls_key_size y nx_secure_tls_hash_size) son informativos y proporcionan información que podría no estar disponible en las entradas de NX_CRYPTO_METHOD.

Como ejemplo, veremos el valor predeterminado del conjunto de cifrado para TLS, TLS_RSA_WITH_AES_128_CBC_SHA, que especifica el uso de RSA, AES-CBC con claves de 128 bits y SHA-1 para el hash de sesión. No se ha especificado ninguna PRF de TLS para este conjunto de cifrado, por lo que en el modo TLSv 1.2 usará el valor predeterminado de PRF SHA-256. Tenga en cuenta que todos los conjuntos de cifrado usan la PRF SHA-1 + MD5 en TLS 1.0 y 1,1, independientemente de la PRF especificada en la tabla.

La entrada de la tabla NX_SECURE_TLS_CIPHERSUITE_INFO de la biblioteca de cifrado genérica se define de la siguiente manera:

```C
{ 
  TLS_RSA_WITH_AES_128_CBC_SHA,     /* Ciphersuite identifier */
  &crypto_method_rsa,               /* Public-key cipher (NX_CRYPTO_METHOD)*/
  &crypto_method_rsa,               /* Authentication method(NX_CRYPTO_METHOD)*/
  &crypto_method_aes_cbc_128,       /* Session cipher method(NX_CRYPTO_METHOD)*/
  16,                               /* Session cipher IV size in bytes */
  16,                               /* Session cipher key size in bytes */
  &crypto_method_hmac_sha1,         /* Session hash routine(NX_CRYPTO_METHOD) */
  20,                               /* Session hash output size in bytes */
  &crypto_method_tls_prf_sha_256    /* TLSv1.2 PRF */
},
```

Tenga en cuenta que para el cifrado de la sesión el tamaño de la clave viene determinado por el conjunto de cifrado, pero para los métodos de clave pública no se conoce el tamaño de la clave hasta que el protocolo de enlace TLS está en curso, ya que las claves públicas están contenidas en los certificados digitales intercambiados durante el protocolo de enlace.

### <a name="x509-cipher-lookup-table"></a>Tabla de búsqueda de cifrado de X.509

Al igual que la tabla NX_SECURE_TLS_CIPHERSUITE_INFO, la estructura NX_SECURE_X509_CRYPTO asigna rutinas criptográficas a valores conocidos. En el caso de X.509, los identificadores son, en realidad, los OID definidos por X.509 y se registran con los cuerpos de los estándares ISO e ITU. Los OID son valores multibyte de longitud variable diseñados para identificar de forma exclusiva diversa información en diversos estándares de telecomunicación, incluidas las rutinas criptográficas utilizadas en los certificados digitales. Debido al hecho de que los OID son de longitud variable, el servicio TLS de NetX Secure asigna los valores de OID oficiales a las constantes de longitud fija que se usan internamente (consulte nx_secure_x509.h). Estas constantes se utilizan en la estructura NX_SECURE_X509_CRYPTO, que se define de la siguiente manera:

```C
/* Structure to hold X.509 cryptographic routine information. */
typedef struct NX_SECURE_X509_CRYPTO_struct
{
    /* Internal NetX Secure identifier for certificate "ciphersuite" which consists
       of a hash and a public key operation. These can be mapped to OIDs in X.509.
        */
    USHORT nx_secure_x509_crypto_identifier;

    /* Public-Key Cryptographic method used by certificates. */
    NX_CRYPTO_METHOD *nx_secure_x509_public_cipher_method;

    /* Hash method used by certificates. */
    NX_CRYPTO_METHOD *nx_secure_x509_hash_method;
} NX_SECURE_X509_CRYPTO;
```

El primer campo, *nx_secure_x509_crypto_identifier*, es la representación interna de OID usada por NetX Secure.

Los campos segundo y tercero apuntan a objetos NX_CRYPTO_METHOD que representan los métodos criptográficos identificados por el OID, una operación de clave pública emparejada con una rutina hash. Tenga en cuenta que cada certificado digital puede tener más de un OID para las rutinas criptográficas.

La tabla de métodos de X.509 se construye de la misma manera que la tabla de búsqueda de conjuntos de cifrado. Como ejemplo, veremos el OID de RSA_SHA1. El OID real para RSA_SHA1 es el siguiente:

```C
{iso(1) member-body(2) us(840) rsadsi(113549) pkcs(1) pkcs-1(1) sha1-with-rsa-
signature(5)}
```
El OID se representa en la sintaxis ASN.1 y tiene un valor numérico de 1.2.840.113549.1.1.5. A continuación, este valor se codifica en formato binario y crea los siguientes bytes:

```C
UCHAR RSA_SHA1_OID = { 0x2A, 0x86, 0x48, 0x86, 0xF7, 0x0D, 0x01, 0x01, 0x05 };
```
La conversión real de ASN.1 al formato binario está fuera del ámbito de este documento. Busque las codificaciones ASN.1 de OID para obtener más información. La representación binaria de los OID admitidos por NetX Secure puede encontrarse en el archivo *nx_secure_x509.c*.

Una vez que tenemos una asignación del OID real a una constante reconocida internamente, podemos crear una entrada para RSA_SHA1 en la tabla NX_SECURE_X509_CRYPTO:

```C
{ 
    NX_SECURE_TLS_X509_TYPE_RSA_SHA_1,    /* Internal OID constant. */
    &crypto_method_rsa,                   /* RSA method (NX_CRYPTO_METHOD). */ 
    &crypto_method_sha1                   /* SHA-1 method (NX_CRYPTO_METHOD). */
}, 
```
### <a name="default-tls-routines"></a>Rutinas de TLS predeterminadas

Como se mencionó anteriormente, TLS requiere algunas rutinas predeterminadas para la generación de claves y la comprobación de mensajes durante el protocolo de enlace. La rutina principal es la función pseudoaleatoria de TLS o PRF. La PRF se basa en rutinas hash y se puede usar para generar una cantidad arbitraria de datos pseudoaleatorios<sup>20</sup> para la generación de claves u otros fines.

Además de la PRF, cada versión de TLS utiliza rutinas hash predeterminadas que también se deben proporcionar. En TLS 1.0 y 1.1, esas rutinas hash son MD5 y SHA-1. TLS 1.2 solo requiere SHA-256.

En la estructura NX_SECURE_TLS_CRYPTO, hay punteros NX_CRYPTO_METHOD para MD5, SHA-1, SHA-256, PRF de TLS 1.0/1.1 y PRF predeterminada de TLS 1.2.

La compatibilidad con TLS 1.3 agrega campos para HKDF (generación de claves), HMAC (para operaciones de hash específicas que se usan durante el protocolo de enlace) y ECDHE (necesario para la funcionalidad TLS 1.3).

En la biblioteca de criptografía de software genérico se incluyen las versiones de software de la PRF de TLS. Para TLS 1.0/1.1, esta función se denomina *nx_crypto_tls_prf_1*. Para TLS 1.2, la función se denomina *nx_secure_tls_prf_sha256*. El sufijo “1” representa la PRF de TLS 1.0 heredada y el sufijo “SHA256” hace referencia al hecho de que la PRF predeterminada de TLS 1.2 se basa en SHA-256. Cuando se necesita compatibilidad con otras rutinas PRF, el sufijo de dichas rutinas reflejará el método hash que se usa. Dado que las rutinas PRF se basan en métodos hash, las rutinas hash subyacentes pueden acelerar el hardware de forma independiente en distintas plataformas de destino.

Además de las tablas de búsqueda de conjuntos de cifrado de TLS y X.509, con las rutinas PRF y hash predeterminadas rellenadas se puede usar la estructura NX_SECURE_TLS_CRYPTO y usarla para inicializar una sesión de TLS.

20. “Pseudoaleatorio” hace referencia al hecho de que la PRF es determinista, lo que significa que siempre producirá la misma salida con la misma entrada; pero es aleatoria en el sentido de que la salida no es predecible. TLS usa esta propiedad de PRF para generar las claves de sesión a partir de varios datos públicos combinados con el secreto maestro intercambiado durante el protocolo de enlace mediante un cifrado de clave pública como RSA.

### <a name="cryptographic-metadata"></a>Metadatos criptográficos

Antes de que podamos inicializar la sesión de TLS con la tabla NX_SECURE_TLS_CRYPTO, necesitamos asignar espacio en el búfer para los metadatos de rutina criptográfica. Los metadatos se usan para almacenar todo el estado asociado a una rutina determinada, representada por su bloque de control. El campo *nx_crypto_metadata_area_size* de cada objeto NX_CRYPTO_METHOD debe establecerse en el tamaño de la estructura de control asociada a esa rutina. En caso contrario, la inicialización de TLS no podrá tener en cuenta correctamente el espacio necesario, lo que podría provocar problemas de saturación del búfer.

Antes de crear la sesión de TLS, se debe asignar el búfer de metadatos. El servicio nx_secure_tls_session_create divide automáticamente el búfer y el espacio se reserva para cada una de las rutinas que se proporcionan en la tabla de métodos criptográficos. Tenga en cuenta que, puesto que solo hay un conjunto de cifrado activo a la vez en una sesión de TLS, el número de conjuntos admitidos no afecta al espacio de metadatos necesario: el espacio se reserva para cada una de las 5 rutinas de conjunto de cifrado con el tamaño máximo de bloque de control de esa categoría en la tabla de búsqueda de conjuntos de cifrado.

Con el fin de facilitar el cálculo del tamaño del búfer de metadatos, el servicio *nx_secure_metadata_size_calculate* realiza los mismos cálculos que nx_secure_tls_session_create, pero simplemente devuelve el tamaño del búfer de metadatos total requerido en bytes.

### <a name="initializing-the-tls-session"></a>Inicialización de la sesión de TLS

Una vez creados los objetos NX_CRYPTO_METHOD y NX_SECURE_TLS_CRYPTO y reservada el área de metadatos, se puede inicializar una sesión de TLS como se indica a continuación (valores tomados de los ejemplos anteriores):

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Cryptographic routine metadata buffer. Size is determined by calling 
nx_secure_tls_metadata_size_calculate with the nx_crypto_tls_ciphers table referenced 
above. */
UCHAR crypto_metadata[4500];

/* Initialize our TLS session using our cipher table and metadata area. Note that we can 
use sizeof for the metadata array because the size parameter expects the size in bytes.*/

nx_secure_tls_session_create(
    &tls_session,            /* Pointer to TLS session.      */
    &nx_crypto_tls_ciphers,  /* Pointer to cipher table.     */
    crypto_metadata,         /* Cryptography metadata buffer.*/
    sizeof(crypto_metadata), /* Size of metadata buffer.     */
);
```
