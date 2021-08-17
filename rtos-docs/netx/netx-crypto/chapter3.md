---
title: 'Capítulo 3: Descripción funcional de Azure RTOS NetX Crypto'
description: Este capítulo contiene una descripción funcional de NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8aa49c130dc2802e95620ccdd4f4d9398c3fd2e55f5896d004e47baa72829848
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796764"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a>Capítulo 3: Descripción funcional de Azure RTOS NetX Crypto

## <a name="execution-overview"></a>Información general sobre la ejecución

Este capítulo contiene una descripción funcional de Azure RTOS NetX Crypto. Hay dos tipos principales de ejecución del programa en una aplicación de NetX Crypto: inicialización y llamadas a la interfaz de la aplicación.

*NetX Crypto se puede usar como una biblioteca criptográfica independiente o bien con ThreadX, NetX o NetX Secure.*

## <a name="aes"></a>AES

- **Algoritmo estándar:** : NetX Crypto implementa AES según el FIPS 197 de NIST, que se puede encontrar en: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)
- **Longitudes de clave admitidas**: 128, 192, 256
- **Modos compatibles**:
  - CBC, CTR (longitud de clave 128, 192, 256 bits)
  - XCBC (solo 128 bits de longitud de clave)
  - CCM8 (solo 128 bits de longitud de clave)
- **Requisitos de memoria**: la aplicación especifica el búfer de entrada y de salida y una estructura de control de AES. La estructura de control de AES mantiene el estado del algoritmo de AES entre las llamadas a la API. El búfer de entrada contiene datos que se van a cifrar o descifrar, y puede tener un tamaño arbitrario. AES usa el búfer de salida para almacenar los datos que se procesan mediante AES. El tamaño del búfer de salida no debe ser menor que el tamaño del búfer de entrada, y debe ser un múltiplo de 16 bytes, el tamaño de bloque de AES. Los búferes de entrada y salida deben ser de memoria contigua y no pueden superponerse, excepto en el caso especial del cifrado en contexto (con la misma memoria para la entrada y la salida). Al cifrar en contexto, el búfer de salida se inicia exactamente en la misma ubicación que el búfer de entrada, y no debe ser menor que el búfer de entrada. Cuando el cifrado AES funciona en contexto, no se requiere memoria temporal adicional.

## <a name="3des"></a>3DES

- **Algoritmo estándar**: NetX Crypto implementa Tripple DES (TDES, también conocido como 3DES) de acuerdo con la publicación especial de NIST 800-67, rev. 2: *"Recomendación para el cifrado de bloques del algoritmo de cifrado de datos triple (TDES)* , que puede consultarse en inglés en [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final).
- **Longitud de clave admitida**: 64 * 3 = 192
- **Requisito de memoria**: ninguno

En NetX Crypto, el término "3DES" se usa indistintamente con "TDES".

## <a name="md5"></a>MD5

- **Algoritmo estándar**: NetX Crypto implementa MD5 según la RFC 1321: *"Algoritmo de síntesis del mensaje de MD5"* .
- **Requisito de memoria**: la aplicación debe proporcionar una estructura de bloques de control DE MD5, que se usa para mantener el estado entre las operaciones de MD5.

## <a name="sha1-sha256512"></a>SHA1, SHA256/512

- **Algoritmo estándar:** NetX Crypto implementa SHA1/256/512 según la publicación del FIPS 180-4 de NIST: "*Estándar de hash seguro*", que puede consultarse en inglés en [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf).
- **Tamaño de bloque de hash**:
  - SHA1: valor hash de 160 bits
  - SHA 224: valor hash de 224 bits
  - SHA 256: valor hash de 256 bits
  - SHA 384: valor hash de 384 bits
  - SHA 512: valor hash de 512 bits
  - SHA 512/224: valor hash de 224 bits
  - SHA 512/256: valor hash de 256 bits

  En NetX Crypto, las rutinas de SHA256 se usan para entregar SHA256 y SHA224. Las rutinas de SHA512 se utilizan para entregar SHA512, SHA384, SHA512/224 y SHA512/256.
- **Requisito de memoria:** la aplicación debe proporcionar una estructura de bloques de control de SHA para mantener el estado entre las operaciones.

## <a name="rsa"></a>RSA

- **Estándar:** NetX Crypto implementa RSA según el estándar *PKCS #1 v2.2: Estándar de criptografía de RSA*", que se publica como RFC 8017 y también puede consultarse en inglés en [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf).
- **Requisito de memoria:** la aplicación debe proporcionar una estructura de bloques de control de RSA para mantener el estado entre las operaciones y proporcionar el espacio de búfer "temporal" necesario para los cálculos intermedios.

## <a name="hmac"></a>HMAC

- **Estándar:** NetX Crypto implementa HMAC según el FIPS PUB 198-1: "*El código de autenticación de mensajes basado en hash (HMAC) con clave*", que puede consultarse en inglés en [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf).
- **Requisito de memoria:** la aplicación debe proporcionar una estructura de bloques de control de HMAC para mantener el estado entre las operaciones. El bloque de control real proporcionado depende de la operación de hash subyacente deseada (por ejemplo, SHA1, MD5).

## <a name="elliptic-curve"></a>Curva elíptica

- **Estándar:** NetX Crypto implementa una curva elíptica. Las curvas con nombre admitidas son (solo campo primario):
  - P-192
  - P-224
  - P-256
  - P-384
  - P-521

   > [!TIP]
   > El formato sin comprimir se admite. Vea la sección 2.3.3 y 2.3.4 de SEC1-v1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)

- **Requisito de memoria:** ninguno

## <a name="ecdsa"></a>ECDSA

- **Estándar:** NetX Crypto implementa ECDSA según el FIPS PUB 186-4: "*Estándar de firma digital (DSS)* ", que puede consultarse en inglés en: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf).
- **Requisito de memoria:** la aplicación debe proporcionar una estructura de bloques de control de ECDSA para mantener el estado entre las operaciones.

## <a name="ecdh"></a>ECDH

> [!IMPORTANT]
> En Azure RTOS 6.0, las rutinas ECDH solo deben utilizarse para la criptografía ECDHE, ya que ECDH con una clave privada estática requiere que la validación del punto de entrada sea segura.

- **Estándar:** NetX Crypto implementa ECDH según el FIPS PUB 800-56Ar2: "Recomendación de esquemas de establecimiento de claves por pares mediante criptografía de logaritmos discretos", que puede consultarse en inglés en [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf).
- **Requisito de memoria:** la aplicación debe proporcionar una estructura de bloques de control de ECDH para mantener el estado entre las operaciones.

## <a name="drbg"></a>DRBG

- **Estándar:** NetX Crypto implementa DRBG de acuerdo con el FIPS PUB 800-90Ar1: "Recomendación para la generación de números aleatorios mediante generadores de bits aleatorios deterministas", que puede consultarse en inglés en [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf).
- **Requisito de memoria:** la aplicación debe proporcionar una estructura de bloques de control de DRBG para mantener el estado entre las operaciones.

## <a name="fips-compliant"></a>Compatible con FIPS

FIPS 140-2 de NetX Crypto