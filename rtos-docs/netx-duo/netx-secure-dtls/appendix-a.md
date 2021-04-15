---
title: 'Apéndice A: Códigos de error o retorno de Azure RTOS NetX Secure DTLS'
description: Aquí se enumeran los posibles códigos de error que pueden devolver los servicios de Azure RTOS NetX Secure DTLS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: reference
ms.service: rtos
ms.openlocfilehash: f14f27167a95a1b9d3ebbdf0d903be7b043ccb28
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814518"
---
# <a name="appendix-a-azure-rtos-netx-secure-dtls-returnerror-codes"></a>Apéndice A: Códigos de error o retorno de Azure RTOS NetX Secure DTLS

## <a name="netx-secure-tlsdtls-return-codes"></a>Códigos de retorno de NetX Secure TLS/DTLS

En la tabla 1 que figura a continuación se enumeran los posibles códigos de error que pueden devolver los servicios de Azure RTOS NetX Secure DTLS. Tenga en cuenta que los servicios también pueden devolver códigos de error de UDP o IP: los valores de TLS empiezan a partir de 0x101, mientras que los de TCP/IP/UDP son inferiores a 0x100. Los valores devueltos de X.509 empiezan a partir de 0x181. Vea la documentación de NetX TCP/IP/UDP para obtener información sobre los valores devueltos de IP y UDP. A continuación encontrará los valores de X.509.

| **Nombre del error**                                        | **Valor** | **Descripción**                                                                                                                                               |
| ----------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_TLS_SUCCESS                              | 0x00      | La función se ha devuelto correctamente. (Igual que NX_SUCCESS).                                                                                                        |
| NX_SECURE_TLS_SESSION_UNINITIALIZED               | 0x101     | Se ha llamado al bucle principal de TLS con un socket sin inicializar.                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE          | 0x102     | La capa de registro de TLS ha recibido un tipo de mensaje no reconocido.                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                       | 0x103     | Error interno: no se reconoce el estado.                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                      | 0x104     | Error interno: el paquete recibido no contiene datos de TLS.                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                 | 0x105     | El conjunto de cifrado elegido no es compatible: error interno del servidor; en el caso del cliente, significa que el host remoto ha enviado un conjunto de cifrado incorrecto (error o ataque).            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                  | 0x106     | Al realizar un cifrado o descifrado, el cifrado elegido está deshabilitado o no está disponible.                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                   | 0x107     | Se ha producido un error en el procesamiento de mensajes durante el protocolo de enlace.                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE           | 0x108     | Un registro entrante tenía un MAC que no coincidía con el que se había generado.                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                    | 0x109     | Por algún motivo, se ha producido un error en el envío de TCP saliente de un registro.                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH           | 0x10A     | Un mensaje entrante tenía una longitud incorrecta (normalmente una longitud distinta de la del encabezado, como en mensajes de certificado).                               |
| NX_SECURE_TLS_BAD_CIPHERSPEC                      | 0x10B     | Un mensaje ChangeCipherSpec entrante era incorrecto.                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                | 0x10C     | Un certificado de servidor entrante no se ha analizado correctamente.                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER          | 0x10D     | En un certificado proporcionado por un servidor se ha especificado una operación de clave pública que no se admite.                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS               | 0x10E     | Se ha recibido un mensaje ClientHello sin conjuntos de cifrado admitidos.                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                | 0x10F     | Un registro entrante tenía una versión de TLS que no se reconoce.                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION            | 0x110     | Un registro entrante tenía una versión de TLS válida, pero no admitida.                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED             | 0x111     | Se ha producido un error al asignar un paquete interno a un mensaje de TLS.                                                                                                       |
| NX_SECURE_TLS_INVALID_CERTIFICATE                 | 0x112     | Un certificado X.509 no se ha analizado correctamente.                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                  | 0x113     | Durante el cierre de una sesión de TLS, no se ha recibido una alerta CloseNotify del host remoto.                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                      | 0x114     | El host remoto ha enviado una alerta que indica un error y ha cerrado la conexión.                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE              | 0x115     | El hash de mensaje de finalización que se ha recibido no coincide con el hash generado localmente: daños en el protocolo de enlace.                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM        | 0x116     | Durante la comprobación, un certificado tenía un algoritmo de firma no admitido.                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED      | 0x117     | Se ha producido un error en la comprobación de la firma de un certificado: los datos del certificado no coincidían con la firma.                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD             | 0x118     | Se ha recibido un mensaje de saludo con un método de compresión no admitido.                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND              | 0x119     | En una operación con una lista de certificados, no se ha encontrado ningún certificado que coincidiera.                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT          | 0x11A     | El host remoto ha enviado un certificado autofirmado, pero no se ha definido NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES.                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND      | 0x11B     | Se ha recibido un certificado remoto con un emisor que no figura en el almacén de confianza local.                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE              | 0x11C     | Se ha recibido un mensaje de DTLS en el orden equivocado: es probable que el culpable sea un datagrama anulado.                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                | 0x11D     | Se ha recibido un paquete de un host remoto que no se reconoce.                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                       | 0x11E     | Se ha recibido un mensaje de DTLS que coincidía con una sesión de DTLS, pero tenía la época equivocada y se debe ignorar.                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED            | 0x11F     | Se ha recibido un mensaje de DTLS con un número de secuencia que ya se ha visto, por lo que se debe ignorar.                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                  | 0x120     | Se ha usado una sesión de TLS en una API de DTLS que no se ha inicializado para DTLS.                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                   | 0x121     | Se ha usado una sesión de TLS en una API de TLS que se ha inicializado para DTLS, no para TLS.                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH              | 0x122     | El autor de la llamada ha intentado enviar datos a través de una sesión de DTLS con una dirección IP o un puerto que no coincidían con los de la sesión.                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS             | 0x123     | Una nueva conexión ha intentado obtener una sesión de DTLS de la memoria caché, pero no había ninguna disponible.                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                 | 0x124     | El autor de la llamada ha buscado una sesión de DTLS, pero la dirección IP y el puerto especificados no coincidían con ninguna entrada de la caché.                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                 | 0x125     | El autor de la llamada ha intentado agregar una PSK a una sesión de TLS, pero no había más espacio en la sesión especificada.                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                    | 0x126     | Un host remoto ha proporcionado una sugerencia de identidad de PSK que no coincidía con ninguna del almacén local.                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED              | 0x127     | Una sesión de TLS ha recibido del host remoto una alerta CloseNotify en la que se indica que la sesión ha finalizado.                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS              | 0x128     | No hay disponibles sesiones de TLS en un objeto de TLS para controlar una conexión.                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED           | 0x129     | No se ha asignado espacio de certificado para los certificados remotos entrantes.                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED               | 0x12A     | El relleno de cifrado de un mensaje entrante no era correcto.                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE        | 0x12B     | Al procesar un mensaje CertificateVerifyRequest, el servidor remoto no ha proporcionado ningún tipo de certificado admitido.                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG         | 0x12C     | Al procesar un mensaje CertificateVerifyRequest, el servidor remoto no ha proporcionado ningún algoritmo de firma admitido.                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE            | 0x12D     | No se ha asignado suficiente espacio de búfer de certificado para un certificado.                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED           | 0x12E     | La versión de protocolo de un registro de TLS entrante no coincidía con la de la sesión establecida.                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR             | 0x12F     | Se ha recibido un mensaje HelloRequest, pero no se va a renegociar.                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                 | 0x130     | Se ha detectado una característica deshabilitada durante una sesión o un protocolo de enlace de TLS.                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE         | 0x131     | Un mensaje CertificateVerify de un cliente remoto no ha podido comprobar el certificado de cliente.                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED | 0x132     | El host remoto ha enviado un mensaje de certificado vacío.                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR      | 0x133     | Se ha producido un error al procesar o enviar una extensión de indicación de renegociación segura.                                                                     |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE     | 0x134     | Se estaba intentando realizar una renegociación de sesión con una sesión de TLS que no estaba activa.                                                                                |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL           | 0x135     | TLS ha recibido un registro demasiado grande para el búfer de paquete asignado. No se ha podido procesar el registro.                                                   |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                | 0x136     | No se ha recibido ninguna extensión especificada del host remoto durante el protocolo de enlace de TLS.                                                                         |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID              | 0x137     | TLS ha recibido una extensión de Indicación de nombre de servidor no válida.                                                                                                     |
| NX_SECURE_TLS_CERT_ID_INVALID                    | 0x138     | La aplicación ha intentado agregar un certificado de servidor con un valor de identificador de certificado no válido (probablemente 0).                                                                |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                  | 0x139     | La aplicación ha intentado agregar un certificado de servidor con un identificador de certificado que ya está en el almacén local.                                                       |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE               | 0x13A     | El host remoto no ha proporcionado la extensión de indicación de renegociación segura o el seudoconjunto de cifrado SCSV, por lo que no se puede realizar una renegociación segura.     |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE             | 0x13B     | Al intentar realizar una operación criptográfica, una de las entradas de la tabla de conjuntos de cifrado (o uno de sus punteros de función) se ha establecido incorrectamente en NULL. |

**Tabla 1: códigos de retorno de error de NetX Secure TLS**

## <a name="netx-secure-x509-return-codes"></a>Códigos de retorno de NetX Secure X.509

En la tabla 2 que figura a continuación se enumeran los posibles códigos de error que pueden devolver los servicios de NetX Secure X.509. Tenga en cuenta que los servicios también pueden devolver otros códigos de error. Los valores devueltos de X.509 empiezan a partir de 0x181 y los valores de TLS de 0x101. Los valores de TCP/IP son inferiores a 0x100. Vea la documentación de NetX TCP/IP para obtener información sobre los valores devueltos de TCP/IP. Arriba encontrará los valores devueltos de TLS.

| **Nombre del error**                                   | **Valor** | **Descripción**                                                                                                        |
| ------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_SUCCESS                        | 0x00      | Estado de devolución correcto. (Igual que NX_SUCCESS).                                                                        |
| NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED    | 0x181     | Se ha detectado una etiqueta ASN.1 de varios bytes que no se admite actualmente.                                                       |
| NX_SECURE_X509_ASN1_LENGTH_TOO_LONG        | 0x182     | Se ha detectado un valor de longitud mayor de lo que se puede controlar.                                                                  |
| NX_SECURE_X509_FOUND_NON_ZERO_PADDING      | 0x183     | Se esperaba un valor de relleno de 0 y se ha obtenido otro diferente.                                                               |
| NX_SECURE_X509_MISSING_PUBLIC_KEY           | 0x184     | X.509 esperaba una clave pública, pero no ha encontrado ninguna.                                                                        |
| NX_SECURE_X509_INVALID_PUBLIC_KEY           | 0x185     | Se ha encontrado una clave pública, pero no es válida o tiene un formato incorrecto.                                                      |
| NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE | 0x186     | El bloque ASN.1 de nivel superior no es una secuencia: el certificado X.509 no es válido.                                                |
| NX_SECURE_X509_MISSING_SIGNATURE_ALGORITHM  | 0x187     | Se esperaba un identificador de algoritmo de firma, pero no se ha encontrado.                                                           |
| NX_SECURE_X509_INVALID_CERTIFICATE_DATA     | 0x188     | Los datos de identidad del certificado no tienen un formato válido.                                                                     |
| NX_SECURE_X509_UNEXPECTED_ASN1_TAG          | 0x189     | Se esperaba una etiqueta ASN.1 específica para el formato X.509, pero se ha obtenido otra cosa.                                      |
| NX_SECURE_PKCS1_INVALID_PRIVATE_KEY         | 0x18A     | Se ha pasado un archivo de clave privada PKCS#1, pero el formato era incorrecto.                                            |
| NX_SECURE_X509_CHAIN_TOO_SHORT              | 0x18B     | Una cadena de certificados X.509 era demasiado corta para contener toda la cadena durante la compilación de esta.                                |
| NX_SECURE_X509_CHAIN_VERIFY_FAILURE         | 0x18C     | No se ha podido comprobar una cadena de certificados X.509 (error global).                                                 |
| NX_SECURE_X509_PKCS7_PARSING_FAILED         | 0x18D     | Se ha producido un error al analizar una firma con codificación PKCS#7 de X.509.                                                                     |
| NX_SECURE_X509_CERTIFICATE_NOT_FOUND        | 0x18E     | Al buscar un certificado, no se ha encontrado ninguna entrada que coincidiera.                                                              |
| NX_SECURE_X509_INVALID_VERSION               | 0x18F     | Un certificado incluía un campo que no es compatible con la versión especificada.                                           |
| NX_SECURE_X509_INVALID_TAG_CLASS            | 0x190     | Un certificado incluía una etiqueta ASN.1 con un valor de clase de etiqueta no válido.                                                   |
| NX_SECURE_X509_INVALID_EXTENSIONS            | 0x191     | Un certificado incluía un TLV de extensiones, pero no contenía ninguna secuencia.                                          |
| NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE   | 0x192     | Un certificado incluía una secuencia de extensión que era X.509 no válido.                                                   |
| NX_SECURE_X509_CERTIFICATE_EXPIRED           | 0x193     | Un certificado tenía un campo "no después de" que era anterior a la hora actual.                                             |
| NX_SECURE_X509_CERTIFICATE_NOT_YET_VALID   | 0x194     | Un certificado tenía un campo "no antes de" que era posterior a la hora actual.                                         |
| NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH     | 0x195     | Un nombre común del certificado o nombre alternativo del firmante no coincidía con un determinado TLD de DNS.                                           |
| NX_SECURE_X509_INVALID_DATE_FORMAT          | 0x196     | Un certificado contenía un campo de fecha con un formato no reconocido.                                               |
| NX_SECURE_X509_CRL_ISSUER_MISMATCH          | 0x197     | Una CRL y un certificado proporcionados no están emitidos por la misma entidad de certificación.                                      |
| NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED  | 0x198     | Se ha producido un error de comprobación de una firma de CRL en su emisor.                                                                       |
| NX_SECURE_X509_CRL_CERTIFICATE_REVOKED      | 0x199     | Se ha encontrado un certificado en una CRL válida, por lo que se ha revocado.                                                 |
| NX_SECURE_X509_WRONG_SIGNATURE_METHOD       | 0x19A     | Al intentar validar una firma, el método de firma no coincidía con el esperado.                          |
| NX_SECURE_X509_EXTENSION_NOT_FOUND          | 0x19B     | Al buscar una extensión, no se ha encontrado ninguna con un identificador que coincidiera.                                                |
| NX_SECURE_X509_ALT_NAME_NOT_FOUND          | 0x19C     | Se ha buscado un nombre en una extensión de nombre alternativo del firmante, pero no se ha encontrado.                                               |
| NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE    | 0x19D     | El tipo de clave privada especificado era desconocido o no era válido.                                                                         |
| NX_SECURE_X509_NAME_STRING_TOO_LONG        | 0x19E     | Se ha pasado una cadena de nombre demasiado larga para un búfer interno (nombre DNS, etc.).                                        |
| NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND    | 0x19F     | Al buscar una extensión de uso mejorado de clave, no se ha encontrado el OID de uso de clave especificado.                               |
| NX_SECURE_X509_KEY_USAGE_ERROR              | 0x1A0     | La devolución de llamada de la aplicación devuelve este código si se produce un error en el uso de la clave durante una comprobación de certificado. |

**Tabla 2: códigos de retorno de error de NetX Secure X.509**
