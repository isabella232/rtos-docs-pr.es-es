---
title: 'Capítulo 1: Introducción a Azure RTOS NetX Secure'
description: Este capítulo contiene una introducción a Azure RTOS NetX Secure y una descripción de sus aplicaciones y ventajas.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8f4c7a97564cd2f702f9887181b36297b42fa492
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814509"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-secure"></a>Capítulo 1: Introducción a Azure RTOS NetX Secure

Azure RTOS NetX Secure es una implementación en tiempo real de alto rendimiento de estándares de seguridad de red de cifrado, como TLS/SSL, diseñada exclusivamente para aplicaciones incrustadas basadas en ThreadX. Este capítulo contiene una introducción a NetX Secure y una descripción de sus aplicaciones y ventajas.

## <a name="netx-secure-unique-features"></a>Características exclusivas de NetX Secure

A diferencia de la mayoría de las implementaciones de TLS, NetX Secure se ha diseñado desde el principio para admitir una amplia variedad de plataformas de hardware incrustadas y para escalar fácilmente desde pequeñas aplicaciones de microcontroladores hasta los procesadores incrustados más eficaces disponibles. El código se escribe teniendo en cuenta los recursos limitados de los sistemas incrustados y proporciona varias opciones de configuración para reducir la superficie de memoria necesaria para proporcionar comunicaciones de red seguras a través de TLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFC compatibles con NetX Secure 

NetX Secure admite los siguientes protocolos relacionados con TLS. La lista no es necesariamente exhaustiva ya que hay numerosas RFC que pertenecen a TLS y criptografía. NetX Secure sigue todas las recomendaciones generales y los requisitos básicos dentro de las restricciones de un sistema operativo en tiempo real con una superficie de memoria pequeña y una ejecución eficiente.

| RFC      | Descripción                                                                                                 | Página |
|----------|-------------------------------------------------------------------------------------------------------------|------|
| RFC 2104 | HMAC: código hash con clave para la autenticación de mensajes                                                              | 33   |
| RFC 2246 | Versión 1.0 del protocolo TLS                                                                                | 19   |
| RFC 3268 | Conjuntos estándar de cifrado avanzado (AES) para la seguridad de la capa de transporte (TLS)                          | 31   |
| RFC 3447 | Estándares de criptografía de clave pública (PKCS) n.º 1: versión 2.1 de especificaciones de criptografía RSA                    | 32   |
| RFC 4279 | Conjuntos de cifrado de clave previamente compartida para TLS                                                                         | 39   |
| RFC 4346 | Versión 1.1 del protocolo de seguridad de la capa de transporte (TLS)                                                     | 19   |
| RFC 5246 | Versión 1.2 del protocolo de seguridad de la capa de transporte (TLS)                                                     | 19   |
| RFC 5280 | Certificados PKI X.509 (v3)                                                                                 | 41   |
| RFC 5746 | Extensión de indicación de renegociación de seguridad de la capa de transporte (TLS)                                           |      |
| RFC 5869 | Función de derivación de claves de extracción y expansión basada en HMAC (HKDF)                                                | 19   |
| RFC 6066<sup>1</sup> | Extensiones de seguridad de la capa de transporte (TLS): definiciones de extensión                                            | 19   |
| RFC 6234 | Algoritmos hash seguros de EE. UU. (HMAC y HKDF SHA y basados en SHA)                                                 | 33   |
| RFC 8443 | Conjuntos de cifrado de criptografía de curva elíptica (ECC) para las versiones 1.2 y anteriores de la seguridad de la capa de transporte (TLS) |      |
| RFC 8446 | Versión 1.3 del protocolo de seguridad de la capa de transporte (TLS)                                                     | 19   |

1. A partir de la versión 6.0 solo se admite totalmente la extensión de indicación de nombre de servidor (SNI) de RFC 6066.

## <a name="netx-secure-requirements"></a>Requisitos de NetX Secure

Para que funcione correctamente, la biblioteca en tiempo de ejecución de NetX Secure requiere que ya se haya creado una instancia IP de NetX. Además, y en función de la aplicación, se necesitarán uno o más certificados digitales X.509 codificados mediante DER, ya sea para identificar una instancia de TLS o para comprobar los certificados procedentes de un host remoto. El paquete NetX Secure no tiene ningún requisito adicional.

## <a name="netx-secure-constraints"></a>Restricciones de NetX Secure

El protocolo NetX Secure implementa los requisitos de los estándares RFC 5246 para TLS 1.2 y RFC 8446 para TLS 1.3, así como para proporcionar compatibilidad con versiones anteriores (deshabilitada de forma predeterminada) con la RFC 4346 (TLS 1.1) y 2246 (TLS 1.0). Sin embargo, se aplican las restricciones siguientes:

- Solo se admiten conjuntos con SHA-256 para TLS 1.2 y TLS 1.3. En las versiones anteriores a TLS 1.2, el protocolo de enlace de TLS utiliza una rutina de hash fija para comprobar que los mensajes de protocolo de enlace TLS no se han alterado. A partir de la versión 1.2, el protocolo de enlace utiliza la rutina hash que se proporciona con el conjunto de cifrado. TLS no es consciente de antemano de qué rutina hash se usará y debe almacenar en caché los mensajes de protocolo de enlace. Al corregir el hash en SHA-256, el TLS de NetX Secure puede funcionar con una superficie de RAM menor que otras implementaciones de TLS. Esta limitación se quitará en una versión futura una vez que el uso de memoria se pueda resolver correctamente. *NOTA IMPORTANTE: esta limitación **solo** se aplica a la opción de conjunto de cifrado. Las firmas del certificado X.509 no están sujetas a la misma limitación y se puede usar cualquiera de las rutinas hash admitidas.
- Debido a la naturaleza de los dispositivos incrustados, es posible que algunas aplicaciones no tengan los recursos necesarios para admitir el tamaño máximo de registro de TLS de 16 KB. NetX Secure puede administrar registros de 16 KB en dispositivos con recursos suficientes. El búfer de reensamblado TLS (consulte referencia de API para *nx_secure_tls_session_packet_buffer_set*) **se puede** establecer en un tamaño inferior a 16 KB, con el riesgo de problemas de interoperabilidad. Si se recibe un registro de TLS válido que es mayor que el búfer de reensamblado, el TLS de NetX Secure anulará la sesión de TLS con un error. En general, el búfer siempre debe establecerse en al menos 18KB (tamaño de registro de TLS de 16KB + 2 KB para el relleno de cifrado) y solo se ha reducido en la configuración controlada (por ejemplo, el host remoto garantiza un tamaño máximo de registro de TLS).
  > [!NOTE]
  > En general, el búfer de reensamblado de paquetes nunca debe ser menor que el tamaño máximo de registro de TLS. Sin embargo, si las características del host remoto son conocidas (por ejemplo, en un sistema completamente cerrado), el tamaño se puede reducir para volver a obtener espacio en RAM.
- Comprobación de certificado mínima. NetX Secure realizará una comprobación básica de la cadena X.509 en un certificado para asegurarse de que el certificado sea válido y esté firmado por una entidad de certificación de confianza, y puede proporcionar el nombre común del certificado para que la aplicación lo compare con el nombre de dominio de nivel superior del host remoto. Si hay un reloj en tiempo real disponible, se puede usar para comprobar la fecha de expiración del certificado (consulte la API nx_secure_tls_session_time_function_set). Sin embargo, la comprobación de las extensiones de certificado y otros datos es responsabilidad del implementador de la aplicación.
- La criptografía basada en software requiere un uso intensivo del procesador. Las rutinas criptográficas basadas en software de NetX Secure se han optimizado para favorecer el rendimiento, pero en función de la eficacia del procesador de destino, dicho rendimiento puede dar lugar a operaciones muy largas. Cuando la criptografía basada en hardware está disponible, se debe usar para un rendimiento óptimo de NetX Secure TLS.
- No se admite la fragmentación del registro de protocolo de enlace de TLS. Si ciertos mensajes de registro de protocolo de enlace TLS son demasiado grandes, pueden dividirse en varios registros TLS. En este momento, NetX Secure TLS se comporta como si fuera un error. Los requisitos de memoria para sistemas incrustados significan que el mensaje de registro de protocolo de enlace más grande probablemente no se puede controlar, pero la limitación podría producir errores al comunicarse con determinados hosts de TLS que usan cadenas de certificados excesivamente grandes.
- El servidor TLS no admite la selección de certificados dinámicos cuando hay varios certificados en el almacén local. 
- No se observa el certificado X509 KeyUsage. 
- No se admiten los conjuntos de cifrado basados en ECDH. En su lugar, use ECDHE.
