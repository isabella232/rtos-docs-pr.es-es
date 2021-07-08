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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a><span data-ttu-id="5ea86-103">Capítulo 2: Instalación y uso de Crypto de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="5ea86-103">Chapter 2 - Installation and use of Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="5ea86-104">En este capítulo se describen la instalación, la configuración y el uso del componente Crypto de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="5ea86-104">This chapter describes installation, setup, and usage of the Azure RTOS NetX Crypto component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="5ea86-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="5ea86-105">Product Distribution</span></span>

<span data-ttu-id="5ea86-106">Crypto, de Azure RTOS NetX, está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="5ea86-106">Azure RTOS NetX Crypto is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="5ea86-107">El paquete incluye archivos de código fuente, archivos de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="5ea86-107">The package includes source files, include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="5ea86-108">**nx_crypto.h**: archivo de encabezado de la API pública del módulo NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="5ea86-108">**nx_crypto.h**: Public API header file NetX Crypto module</span></span>
- <span data-ttu-id="5ea86-109">**nx_crypto_\*.c/h**: archivos de código fuente de C/H para NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="5ea86-109">**nx_crypto_\*.c/h**: C/H Source files for NetX Crypto</span></span>
- <span data-ttu-id="5ea86-110">**nx_crypto_port.h**: archivo de encabezado de C que contiene todas las definiciones y estructuras de datos específicos de la herramienta de desarrollo y de destino.</span><span class="sxs-lookup"><span data-stu-id="5ea86-110">**nx_crypto_port.h**: C header file containing all development-tool and target specific data definitions and structures.</span></span>
- <span data-ttu-id="5ea86-111">**NetX_Crypto_User_Guide.pdf**: descripción en PDF del módulo NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="5ea86-111">**NetX_Crypto_User_Guide.pdf**: PDF description of NetX Crypto Module.</span></span>

## <a name="netx-crypto-installation"></a><span data-ttu-id="5ea86-112">Instalación de NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="5ea86-112">NetX Crypto Installation</span></span>

<span data-ttu-id="5ea86-113">Toda la distribución mencionada anteriormente está disponible en el directorio **crypto_libraries**, presente en el nivel raíz del repositorio NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="5ea86-113">The entire distribution mentioned previously is available in **crypto_libraries** directory, present at root level of NetX Duo repository.</span></span>

<span data-ttu-id="5ea86-114">Para usar NetX Crypto, toda la distribución que se menciona anteriormente debe copiarse en el mismo directorio en el que se ha instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="5ea86-114">In order to use NetX Crypto, the entire distribution mentioned previously should be copied to the same directory level where NetX is installed.</span></span> <span data-ttu-id="5ea86-115">Por ejemplo, si NetX se ha instalado en el directorio "\threadx\arm7\NetX", los directorios nx_crypto *.*</span><span class="sxs-lookup"><span data-stu-id="5ea86-115">For example, if NetX is installed in the directory "\threadx\arm7\NetX" then the nx_crypto *.*</span></span> <span data-ttu-id="5ea86-116">deben copiarse en "\threadx\arm7\NetXCrypto".</span><span class="sxs-lookup"><span data-stu-id="5ea86-116">directories should be copied into "\threadx\arm7\NetXCrypto".</span></span>

<span data-ttu-id="5ea86-117">Para que la criptografía de NetX se use en modo independiente, la distribución completa que se ha mencionado anteriormente debe copiarse en el proyecto de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5ea86-117">For NetX Crypto to be used in standalone mode, the entire distribution mentioned previously should be copied to the application project.</span></span> <span data-ttu-id="5ea86-118">Por ejemplo, el directorio **crypto_libraries** debe copiarse en el proyecto de la aplicación o en un proyecto de biblioteca con directorio **crypto_libraries** que se debe crear y vincular al proyecto de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5ea86-118">For example **crypto_libraries** directory should be copied to the application project or a library project with **crypto_libraries** directory should be created and linked to the application project.</span></span> 

## <a name="using-netx-crypto"></a><span data-ttu-id="5ea86-119">Uso de NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="5ea86-119">Using NetX Crypto</span></span>

<span data-ttu-id="5ea86-120">El código de la aplicación debe incluir *nx_crypto.h*.</span><span class="sxs-lookup"><span data-stu-id="5ea86-120">The application code must include the *nx_crypto.h*.</span></span>  <span data-ttu-id="5ea86-121">Después de incluir *nx_crypto.h*, el código de la aplicación puede realizar las llamadas de función NetX Crypto especificadas más adelante en este manual.</span><span class="sxs-lookup"><span data-stu-id="5ea86-121">Once *nx_crypto.h* is included, the application code is then able to make the NetX Crypto function calls specified later in this guide.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="5ea86-122">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="5ea86-122">Configuration Options</span></span>

<span data-ttu-id="5ea86-123">Hay varias opciones de configuración para compilar NetX Crypto.</span><span class="sxs-lookup"><span data-stu-id="5ea86-123">There are several configuration options for building NetX Crypto.</span></span> <span data-ttu-id="5ea86-124">A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas:</span><span class="sxs-lookup"><span data-stu-id="5ea86-124">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="5ea86-125">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: si se define, esta opción proporciona el módulo de RSA máximo esperado, en bits.</span><span class="sxs-lookup"><span data-stu-id="5ea86-125">**NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: Defined, this option gives the maximum RSA modulus expected, in bits.</span></span> <span data-ttu-id="5ea86-126">El valor predeterminado es 4096 para un módulo de 4096 bits.</span><span class="sxs-lookup"><span data-stu-id="5ea86-126">The default value is 4096 for a 4096-bit modulus.</span></span> <span data-ttu-id="5ea86-127">Otros valores pueden ser 3072, 2048 o 1024 (no recomendado).</span><span class="sxs-lookup"><span data-stu-id="5ea86-127">Other values can be 3072, 2048, or 1024 (not recommended).</span></span>
- <span data-ttu-id="5ea86-128">**NX_CRYPTO_SELF_TEST**: si se define, habilita las pruebas automáticas del módulo Crypto de NetX.</span><span class="sxs-lookup"><span data-stu-id="5ea86-128">**NX_CRYPTO_SELF_TEST**: Defined, enables self tests for NetX Crypto module.</span></span> <span data-ttu-id="5ea86-129">El símbolo **NX_CRYPTO_FIPS** ahora está en desuso y se ha cambiado el nombre a **NX_CRYPTO_SELF_TEST**.</span><span class="sxs-lookup"><span data-stu-id="5ea86-129">**NX_CRYPTO_FIPS** symbol is now deprecated and renamed to **NX_CRYPTO_SELF_TEST**</span></span>
- <span data-ttu-id="5ea86-130">**NX_CRYPTO_STANDALONE_ENABLE**: si se define, permite usar NetX Crypto en modo independiente (sin Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="5ea86-130">**NX_CRYPTO_STANDALONE_ENABLE**: Defined enables NetX Crypto to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="5ea86-131">De forma predeterminada, este símbolo no está definido.</span><span class="sxs-lookup"><span data-stu-id="5ea86-131">By default this symbol is not defined.</span></span>
