---
title: 'Capítulo 2: Instalación y uso de Crypto de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3323af5eaf31ac9c167966522df6477c82e99fdc
ms.sourcegitcommit: c98e5360c9cedbe773af5a44f5163f563c85b570
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2021
ms.locfileid: "110337013"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a>Capítulo 2: Instalación y uso de Crypto de Azure RTOS NetX

En este capítulo se describen la instalación, la configuración y el uso del componente Crypto de Azure RTOS NetX.

## <a name="product-distribution"></a>Distribución del producto

Crypto, de Azure RTOS NetX, está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). El paquete incluye archivos de código fuente, archivos de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:

- **nx_crypto.h**: archivo de encabezado de la API pública del módulo NetX Crypto
- **nx_crypto_*.c/h**: archivos de código fuente de C/H para NetX Crypto
- **nx_crypto_port.h**: archivo de encabezado de C que contiene todas las definiciones y estructuras de datos específicos de la herramienta de desarrollo y de destino.
- **NetX_Crypto_User_Guide.pdf**: descripción en PDF del módulo NetX Crypto.

## <a name="netx-crypto-installation"></a>Instalación de NetX Crypto

Toda la distribución mencionada anteriormente está disponible en el directorio **crypto_libraries**, presente en el nivel raíz del repositorio NetX Duo.

Para usar NetX Crypto, toda la distribución que se menciona anteriormente debe copiarse en el mismo directorio en el que se ha instalado NetX. Por ejemplo, si NetX se ha instalado en el directorio "\threadx\arm7\NetX", los directorios nx_crypto *.* deben copiarse en "\threadx\arm7\NetXCrypto".

Para que la criptografía de NetX se use en modo independiente, la distribución completa que se ha mencionado anteriormente debe copiarse en el proyecto de la aplicación. Por ejemplo, el directorio **crypto_libraries** debe copiarse en el proyecto de la aplicación o en un proyecto de biblioteca con directorio **crypto_libraries** que se debe crear y vincular al proyecto de la aplicación. 

## <a name="using-netx-crypto"></a>Uso de NetX Crypto

El código de la aplicación debe incluir *nx_crypto.h*.  Después de incluir *nx_crypto.h*, el código de la aplicación puede realizar las llamadas de función NetX Crypto especificadas más adelante en este manual.

## <a name="configuration-options"></a>Opciones de configuración

Hay varias opciones de configuración para compilar NetX Crypto. A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas:

- **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: si se define, esta opción proporciona el módulo de RSA máximo esperado, en bits. El valor predeterminado es 4096 para un módulo de 4096 bits. Otros valores pueden ser 3072, 2048 o 1024 (no recomendado).
- **NX_CRYPTO_SELF_TEST**: si se define, habilita las pruebas automáticas del módulo Crypto de NetX. El símbolo **NX_CRYPTO_FIPS** ahora está en desuso y se ha cambiado el nombre a **NX_CRYPTO_SELF_TEST**.
- **NX_CRYPTO_STANDALONE_ENABLE**: si se define, permite usar NetX Crypto en modo independiente (sin Azure RTOS). De forma predeterminada, este símbolo no está definido.
