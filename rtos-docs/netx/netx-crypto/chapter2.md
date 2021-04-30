---
title: 'Capítulo 2: Instalación y uso de Crypto de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1616667c5efd73229ed69bcd4e5de5f80e5826f9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815265"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="482c2-103">Capítulo 2: Instalación y uso de Crypto de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="482c2-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="482c2-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente Crypto de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="482c2-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="482c2-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="482c2-105">Product Distribution</span></span>

<span data-ttu-id="482c2-106">Crypto, de Azure RTOS NetX, está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="482c2-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="482c2-107">El paquete incluye archivos de código fuente, archivos de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="482c2-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="482c2-108">**nx_crypto.h**: archivo de encabezado de la API pública del módulo NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="482c2-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="482c2-109">**nx_crypto_\*.c/h**: archivos de código fuente de C/H para NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="482c2-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="482c2-110">**nx_crypto_port.h**: archivo de encabezado de C que contiene todas las definiciones y estructuras de datos específicos de la herramienta de desarrollo y de destino.</span><span class="sxs-lookup"><span data-stu-id="482c2-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="482c2-111">**NetX_Crypto_User_Guide.pdf**: descripción en PDF del módulo NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="482c2-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="482c2-112">Instalación de NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="482c2-112">NetX Crypto Installation</span></span>

<span data-ttu-id="482c2-113">Toda la distribución mencionada anteriormente está disponible en el directorio **crypto_libraries**, presente en el nivel raíz del repositorio NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="482c2-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="482c2-114">Para usar NetX Crypto, toda la distribución que se menciona anteriormente debe copiarse en el mismo directorio en el que se ha instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="482c2-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="482c2-115">Por ejemplo, si NetX se ha instalado en el directorio "\threadx\arm7\NetX", los directorios nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="482c2-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="482c2-116">deben copiarse en "\threadx\arm7\NetXCrypto".</span><span class="sxs-lookup"><span data-stu-id="482c2-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="482c2-117">Para que la criptografía de NetX se use en modo independiente, la distribución completa que se ha mencionado anteriormente debe copiarse en el proyecto de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="482c2-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="482c2-118">Por ejemplo, el directorio **crypto_libraries** debe copiarse en el proyecto de la aplicación o en un proyecto de biblioteca con directorio **crypto_libraries** que se debe crear y vincular al proyecto de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="482c2-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="482c2-119">Uso de NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="482c2-119">Using NetX Crypto</span></span>

<span data-ttu-id="482c2-120">El uso de NetX Crypto es fácil.</span><span class="sxs-lookup"><span data-stu-id="482c2-120">Using NetX Crypto is easy.</span></span> <span data-ttu-id="482c2-121">Básicamente, el código de la aplicación debe incluir el *nx_crypto.h*.</span><span class="sxs-lookup"><span data-stu-id="482c2-121">Basically, the application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="482c2-122">Después de incluir *nx_crypto.h*, el código de la aplicación puede realizar las llamadas de función NetX Crypto especificadas más adelante en este manual.</span><span class="sxs-lookup"><span data-stu-id="482c2-122">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="482c2-123">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="482c2-123">Configuration Options</span></span>

<span data-ttu-id="482c2-124">Hay varias opciones de configuración para compilar NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="482c2-124">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="482c2-125">A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas:</span><span class="sxs-lookup"><span data-stu-id="482c2-125">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="482c2-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: si se define, esta opción proporciona el módulo de RSA máximo esperado, en bits.</span><span class="sxs-lookup"><span data-stu-id="482c2-126">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="482c2-127">El valor predeterminado es 4096 para un módulo de 4096 bits.</span><span class="sxs-lookup"><span data-stu-id="482c2-127">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="482c2-128">Otros valores pueden ser 3072, 2048 o 1024 (no recomendado).</span><span class="sxs-lookup"><span data-stu-id="482c2-128">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="482c2-129">**NX_CRYPTO_FIPS**: si se define, esta opción habilita las características de seguridad adicionales necesarias para el uso conforme a FIPS.</span><span class="sxs-lookup"><span data-stu-id="482c2-129">**NX_CRYPTO_FIPS**: Defined, this option enables extra security features required for FIPS-Compliant usage.</span></span> <span data-ttu-id="482c2-130">Esta opción no está habilitada para compilaciones no conformes a FIPS.</span><span class="sxs-lookup"><span data-stu-id="482c2-130">This option is not enabled for non-FIPS build.</span></span>
- <span data-ttu-id="482c2-131">**NX_CRYPTO_STANDALONE_ENABLE**: si se define, permite usar NetX Crypto en modo independiente (sin Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="482c2-131">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="482c2-132">De forma predeterminada, este símbolo no está definido.</span><span class="sxs-lookup"><span data-stu-id="482c2-132">By default this symbol is not defined.</span></span>
