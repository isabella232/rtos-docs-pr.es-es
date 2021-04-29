---
title: 'Capítulo 1: Introducción al Protocolo punto a punto (PPP) de Azure RTOS NetX Duo'
description: En este capítulo se presenta el módulo del Protocolo punto a punto (PPP) de Azure RTOS NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f439cf66e6619652ae8ab9097b2de5e584d78c59
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814613"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a>Capítulo 1: Introducción al Protocolo punto a punto (PPP) de Azure RTOS NetX Duo

Normalmente, las aplicaciones de NetX se conectan a la red física real a través de Ethernet. Esto proporciona un acceso a la red rápido y eficaz. Sin embargo, hay situaciones en las que la aplicación no tiene acceso Ethernet. En tales casos, la aplicación todavía puede conectarse a la red a través de una interfaz serie conectada directamente a otro miembro de la red. El protocolo de software más común que se usa para administrar este tipo de conexión es el Protocolo punto a punto (PPP).

Aunque la comunicación en serie es relativamente sencilla, el PPP es bastante complejo. El PPP se compone en realidad de varios protocolos, como el Protocolo de control de vínculos (LCP), el Protocolo de control de protocolo de Internet (IPCP), el Protocolo de autenticación de contraseña (PAP) y el Protocolo de autenticación por desafío mutuo (CHAP). El LCP es el protocolo principal de PPP. Aquí es donde los componentes básicos del vínculo se negocian dinámicamente en un modo de punto a punto. Una vez que las características básicas del vínculo se han negociado correctamente, se usa PAP o CHAP para asegurarse de que un homólogo conectado sea válido. Si ambos elementos homólogos son válidos, se usa IPCP para negociar las direcciones IP usadas por estos. Una vez que IPCP se completa, PPP puede enviar y recibir paquetes IP.

NetX considera a PPP principalmente como un controlador de dispositivo. La función *nx_ppp_driver* se proporciona a la función de creación de IP de NetX, *nx_ip_create*. De lo contrario, NetX no tiene ningún conocimiento directo de PPP.

## <a name="ppp-serial-communication"></a>Comunicación en serie de PPP

El paquete de PPP de NetX requiere que la aplicación proporcione un controlador de comunicación en serie. El controlador debe admitir caracteres de 8 bits y también puede emplear el control de flujo de software. Es responsabilidad de la aplicación inicializar el controlador, lo que debe hacerse antes de crear la instancia de PPP.

Para enviar paquetes de PPP, se debe proporcionar una rutina de bytes de salida del controlador serie a PPP (especificada en la función *nx_ppp_create*). Se llama repetidamente a esta rutina de bytes de salida del controlador serie para transmitir todo el paquete de PPP. Es responsabilidad del controlador de serie almacenar en búfer el resultado. En el lado de recepción, el controlador serie de la aplicación debe llamar a la función *nx_ppp_byte_receive* de PPP siempre que llegue un nuevo byte. Esto se suele hacer desde dentro del contexto de una rutina de servicio de interrupción (ISR). La función *nx_ppp_byte_receive* coloca el byte de entrada en un búfer circular y alerta al subproceso de recepción de PPP de su presencia.

## <a name="ppp-over-ethernet-communication"></a>Comunicación de PPP a través de Ethernet

El PPP de NetX también puede transmitir mensajes de PPP a través de Ethernet. En esta situación, el paquete de PPP de NetX requiere que la aplicación proporcione un controlador de comunicación de Ethernet.

Para enviar paquetes de PPP a través de Ethernet, se debe proporcionar una rutina de salida a PPP (especificada en la función *nx_ppp_packet_send_set*). Se llama repetidamente a esta rutina de salida para transmitir todo el paquete de PPP. En el lado de recepción, el receptor de la aplicación debe llamar a la función *nx_ppp_packet_receive* de PPP siempre que llegue un nuevo paquete.

## <a name="ppp-packet"></a>Paquete de PPP

PPP emplea tramas de AHDLC (un subconjunto de HDLC) para encapsular todos los datos de usuario y control del protocolo PPP. Un marco AHDLC tiene un aspecto similar al siguiente:

|**Marca**|**Addr**|**Ctrl**|**Información**|**CRC**|**Marca**|
|--------|--------|--------|---------------|-------|--------|
|7E |FF|03|[0-1502 bytes]|2 bytes.| 7E|

Cada marco de PPP tiene este aspecto general. Los dos primeros bytes del campo de información contienen el tipo de protocolo de PPP. Los valores válidos se definen de la siguiente forma:

- C021:  LCP
- 8021: IPCP
- C023: PAP
- C223: CHAP
- 0021: Paquete de datos IP

Si el tipo de protocolo 0x0021 está presente, el paquete de IP sigue inmediatamente. De lo contrario, si uno de los otros protocolos está presente, los bytes siguientes corresponden a ese protocolo en particular.

Con el fin de garantizar que los marcadores de marcos iniciales/finales de 0x7E sean únicos y para admitir el control de flujo de software, AHDLC usa secuencias de escape para representar varios valores de byte. El valor 0x7D especifica que se codifica el carácter que aparece a continuación, que es básicamente el carácter original exclusivo ORed con 0x20. Por ejemplo, el valor 0x03 para el campo Ctrl en el encabezado se representa mediante la secuencia de dos bytes: 7D 23. De forma predeterminada, los valores menores que 0x20 se convierten en una secuencia de escape, así como los valores 0x7E y 0x7D que se encuentran en el campo de información. Tenga en cuenta que las secuencias de escape también se aplican al campo CRC.

## <a name="link-control-protocol-lcp"></a>Protocolo de control de vínculos (LCP)

LCP es el protocolo PPP principal y es el primer protocolo que se ejecuta. LCP es responsable de negociar varios parámetros de PPP, como la unidad de recepción máxima (MRU) y el protocolo de autenticación (PAP, CHAP o ninguno) que se va a usar. Una vez que ambos lados de LCP coinciden con los parámetros de PPP, los protocolos de autenticación, si los hay, empiezan a ejecutarse.

## <a name="password-authentication-protocol-pap"></a>Protocolo de autenticación de contraseña (PAP)

PAP es un protocolo relativamente sencillo que se basa en el suministro de un nombre y una contraseña por una de las partes de la conexión (como se negocia durante LCP). El otro lado comprueba esta información. Si es correcto, se devuelve un mensaje de aceptación al remitente y, a continuación, PPP puede continuar con la máquina de estados de IPCP. De lo contrario, si el nombre o la contraseña no son correctos, se rechazará la conexión.

>[!NOTE]
> Los dos lados de la interfaz pueden solicitar PAP, pero PAP se usa normalmente solo en una dirección.

## <a name="challenge-handshake-authentication-protocol-chap"></a>Protocolo de autenticación por desafío mutuo (CHAP)

CHAP es un protocolo de autenticación más complejo que PAP. El autenticador de CHAP proporciona a su homólogo un nombre y un valor. A continuación, el homólogo usa el nombre proporcionado para buscar un "secreto" compartido entre las dos entidades. Después, se realiza un cálculo sobre el identificador, el valor y el "secreto". El resultado de este cálculo se devuelve en la respuesta. Si es correcto, PPP puede continuar con la máquina de estados de IPCP. De lo contrario, si el resultado es incorrecto, se rechaza la conexión.

Otro aspecto interesante de CHAP es que puede producirse a intervalos aleatorios después de que se haya establecido una conexión. Se utiliza para evitar que una conexión sea secuestrada una vez autenticada. Si se produce un error en un desafío en una de estos momentos aleatorios, la conexión finaliza inmediatamente.

>[!NOTE]
> Los dos lados de la interfaz pueden solicitar CHAP, pero CHAP se usa normalmente solo en una dirección.

## <a name="internet-protocol-control-protocol-ipcp"></a>Protocolo de control de protocolo de Internet (IPCP)

IPCP es el último protocolo que se ejecuta antes de que la comunicación de PPP esté disponible para la transferencia de datos IP de NetX. El propósito principal de este protocolo es que homólogo informe al otro de su dirección IP. Una vez que se configura la dirección IP, se habilita la transferencia de datos de IP de NetX.

## <a name="data-transfer"></a>Transferencia de datos

Como se mencionó anteriormente, los paquetes de datos de IP de NetX residen en marcos de PPP con un identificador de protocolo 0x0021. Todos los paquetes de datos recibidos se colocan en una o varias estructuras de NX_PACKET y se transfieren al procesamiento de recepción de NetX. En la transmisión, el contenido del paquete de NetX se coloca en un marco de AHDLC y se transmite.

## <a name="ppp-rfcs"></a>RFC de PPP

PPP de NetX es compatible con las RFC1332, RFC1334, RFC1661, RFC1994 y RFC relacionadas.