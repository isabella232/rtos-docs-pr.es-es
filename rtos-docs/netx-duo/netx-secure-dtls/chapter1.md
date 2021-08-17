---
title: 'Capítulo 1: Introducción a DTLS de Azure RTOS NetX Secure'
description: El protocolo DTLS de Azure RTOS NetX Secure es una implementación en tiempo real del protocolo de seguridad de la capa de transporte de datagramas diseñado para aplicaciones incrustadas basadas en ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a7fe51fd1e141c0c525a98986ca3058732b61843f8bd79bf24fc5ac986147501
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797048"
---
# <a name="chapter-1-introduction-to-azure-rtos-netx-secure-dtls"></a>Capítulo 1: Introducción al protocolo DTLS de Azure RTOS NetX Secure

El protocolo DTLS de Azure RTOS NetX Secure es una implementación en tiempo real de alto rendimiento del protocolo de seguridad de la capa de transporte de datagramas diseñado exclusivamente para aplicaciones incrustadas basadas en ThreadX. Este capítulo contiene una introducción a NetX Secure DTLS y una descripción de sus aplicaciones y ventajas.

## <a name="netx-secure-unique-features"></a>Características exclusivas seguras de NetX

A diferencia de la mayoría de las implementaciones de TLS/DTLS, NetX Secure se ha diseñado desde el principio para admitir una amplia variedad de plataformas de hardware incrustadas y para escalar fácilmente desde pequeñas aplicaciones de microcontroladores hasta los procesadores incrustados más eficaces disponibles. El código se escribe teniendo en cuenta los recursos limitados de los sistemas incrustados y proporciona varias opciones de configuración para reducir la superficie de memoria necesaria para proporcionar comunicaciones de red seguras a través de TLS o DTLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFC compatibles con NetX Secure

NetX Secure admite los siguientes protocolos relacionados con TLS y DTLS. La lista no es necesariamente exhaustiva ya que hay numerosas RFC que pertenecen a TLS/DTLS y criptografía. NetX Secure sigue todas las recomendaciones generales y los requisitos básicos dentro de las restricciones de un sistema operativo en tiempo real con una superficie de memoria pequeña y una ejecución eficiente.


| RFC | Descripción |
| --- | ----------- |
| RFC 6347 | Versión 1.2 de seguridad de la capa de transporte de datagramas |
| RFC 2246 | Versión 1.0 del protocolo TLS|
| RFC 4346 | Versión 1.1 del protocolo de seguridad de la capa de transporte (TLS) |
| RFC 5246 | Versión 1.2 del protocolo de seguridad de la capa de transporte (TLS) |
| RFC 5280 | Certificados PKI X.509 (v3) |
| RFC 3268 | Conjuntos estándar de cifrado avanzado (AES) para la seguridad de la capa de transporte (TLS) |
| RFC 3447 | Estándares de criptografía de clave pública (PKCS) n.º 1: versión 2.1 de especificaciones de criptografía RSA |
| RFC 2104 | HMAC: código hash con clave para la autenticación de mensajes |
| RFC 6234 | Algoritmos hash seguros de EE. UU. (HMAC y HKDF SHA y basados en SHA) |
| RFC 4279 | Conjuntos de cifrado de clave previamente compartida para TLS |

## <a name="netx-secure-dtls-requirements"></a>Requisitos de NetX Secure DTLS

Para que funcione correctamente, la biblioteca en tiempo de ejecución de NetX Secure requiere que ya se haya creado una instancia IP de NetX. Además, y en función de la aplicación, se necesitarán uno o más certificados digitales X.509 codificados mediante DER, ya sea para identificar una instancia de TLS/DTLS o para comprobar los certificados procedentes de un host remoto. El paquete NetX Secure no tiene ningún requisito adicional.

## <a name="netx-secure-dtls-constraints"></a>Restricciones de NetX Secure DTLS

El protocolo NetX Secure DTLS implementa los requisitos de los estándares RFC 6347 para DTLS 1.2. Sin embargo, se aplican las restricciones siguientes:

1. Debido a la naturaleza de los dispositivos incrustados, es posible que algunas aplicaciones no tengan los recursos necesarios para admitir el tamaño máximo de registro de TLS/DTLS de 16 KB. NetX Secure puede administrar registros de 16 KB en dispositivos con recursos suficientes.
2. Comprobación de certificado mínima. NetX Secure realizará una comprobación básica de la cadena X.509 en un certificado para asegurarse de que el certificado sea válido y esté firmado por una entidad de certificación de confianza, y puede proporcionar el nombre común del certificado para que la aplicación lo compare con el nombre de dominio de nivel superior del host remoto. Sin embargo, la comprobación de las extensiones de certificado y otros datos es responsabilidad del implementador de la aplicación.
3. La criptografía basada en software requiere un uso intensivo del procesador. Las rutinas criptográficas basadas en software de NetX Secure se han optimizado para favorecer el rendimiento, pero en función de la eficacia del procesador de destino, dicho rendimiento puede dar lugar a operaciones muy largas. Cuando la criptografía basada en hardware está disponible, se debe usar para un rendimiento óptimo de NetX Secure DTLS.
