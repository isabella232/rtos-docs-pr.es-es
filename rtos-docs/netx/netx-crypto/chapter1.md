---
title: 'Capítulo 1: Introducción a Azure RTOS NetX Crypto'
description: NetX Crypto es una implementación en tiempo real de alto rendimiento de algoritmos criptográficos diseñados para proporcionar cifrado de datos y servicios de autenticación.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0bde9be472584308894cfd702ccd014578afe753
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814450"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-crypto"></a>Capítulo 1: Introducción a Azure RTOS NetX Crypto

Azure RTOS NetX Crypto es una implementación en tiempo real de alto rendimiento de algoritmos criptográficos diseñados para proporcionar cifrado de datos y servicios de autenticación. NetX Crypto está diseñado para conectarse a los módulos de IPsec, DTLS y TLS seguros. Las aplicaciones también pueden usar NetX Crypto como módulo independiente fuera de la seguridad de la red.

## <a name="netx-crypto-unique-features"></a>Características únicas de NetX Crypto

NetX Crypto se implementa en el lenguaje C estándar (C99), compatible con casi todos los compiladores de C/C++. Su diseño modular permite que una aplicación solo vincule los algoritmos criptográficos que necesita utilizar, logrando así un tamaño de código mínimo. La implementación está diseñada para funcionar con la mayoría de los microprocesadores de 32 bits y solo usa las operaciones matemáticas básicas (suma, resta, multiplicación, división, operador lógico AND, OR, NOR y desplazamiento de bits). Todas estas operaciones se utilizan con cantidades de 32 bits, lo que permite que NetX Crypto sea portable en la mayoría de los microprocesadores de 32 bits. La implementación está optimizada específicamente para ejecutarse en microprocesadores con recursos limitados, orientados a aplicaciones profundamente integradas.

## <a name="algorithms-supported-by-netx-crypto"></a>Algoritmos admitidos por NetX Crypto

NetX Crypto es compatible con los siguientes algoritmos criptográficos. NetX Crypto sigue todas las recomendaciones generales y los requisitos básicos dentro de las restricciones de un sistema operativo en tiempo real y las plataformas que requieren una superficie de memoria pequeña y una ejecución eficiente.

| Algoritmo       | Longitud de clave (bits)      |
| --------------- | ---------------------- |
| AES(CBC, CTR)   | 128, 192, 256          |
| AES(XCBC)       | 128                    |
| AES-CCM 8       | 128                    |
| 3DES(CBC)       | 192                    |
| HMAC-SHA1       | Cualquier longitud             |
| HMAC-SHA224     | Cualquier longitud             |
| HMAC-SHA256     | Cualquier longitud             |
| HMAC-SHA384     | Cualquier longitud             |
| HMAC-SHA512     | Cualquier longitud             |
| HMAC-SHA512/224 | Cualquier longitud             |
| HMAC-SHA512/256 | Cualquier longitud             |
| HMAC-MD5        | Cualquier longitud             |
| RSA             | 1024, 2048, 3072, 4096 |

| Algoritmo       | Longitud de síntesis (bits) | Tamaño de bloque (bits) |
| --------------- | -------------------- | ----------------- |
| SHA1            | 160                  | 512               |
| SHA224          | 224                  | 512               |
| SHA256          | 256                  | 512               |
| SHA384          | 384                  | 1024              |
| SHA512          | 512                  | 1024              |
| MD5             | 128                  | 512               |
| HMAC-SHA1       | 160                  | 512               |
| HMAC-SHA224     | 224                  | 512               |
| HMAC-SHA256     | 256                  | 512               |
| HMAC-SHA384     | 384                  | 1024              |
| HMAC-SHA512     | 512                  | 1024              |
| HMAC-SHA512/224 | 224                  | 1024              |
| HMAC-SHA512/256 | 256                  | 1024              |
| HMAC-MD5        | 128                  | 512               |
| Curva elíptica  | P192/224/256/384/521 |                   |

## <a name="netx-crypto-requirements"></a>Requisitos de NetX Crypto

TBD: Requisito de memoria... ¿Seguridad de interrupción/reentrada? Necesita debate

## <a name="netx-crypto-constraints"></a>Restricciones de NetX Crypto

Ninguno.
