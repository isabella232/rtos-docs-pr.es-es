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
# <a name="chapter-1---introduction-to-azure-rtos-netx-crypto"></a><span data-ttu-id="61e41-103">Capítulo 1: Introducción a Azure RTOS NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="61e41-103">Chapter 1 - Introduction to Azure RTOS NetX Crypto</span></span>

<span data-ttu-id="61e41-104">Azure RTOS NetX Crypto es una implementación en tiempo real de alto rendimiento de algoritmos criptográficos diseñados para proporcionar cifrado de datos y servicios de autenticación.</span><span class="sxs-lookup"><span data-stu-id="61e41-104">Azure RTOS NetX Crypto is a high-performance real-time implementation of cryptographic algorithms designed to provide data encryption and authentication services.</span></span> <span data-ttu-id="61e41-105">NetX Crypto está diseñado para conectarse a los módulos de IPsec, DTLS y TLS seguros.</span><span class="sxs-lookup"><span data-stu-id="61e41-105">NetX Crypto is designed to plug in for NetX Secure TLS, DTLS, and IPsec modules.</span></span> <span data-ttu-id="61e41-106">Las aplicaciones también pueden usar NetX Crypto como módulo independiente fuera de la seguridad de la red.</span><span class="sxs-lookup"><span data-stu-id="61e41-106">Applications may also use NetX Crypto as a standalone module outside network security.</span></span>

## <a name="netx-crypto-unique-features"></a><span data-ttu-id="61e41-107">Características únicas de NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="61e41-107">NetX Crypto Unique Features</span></span>

<span data-ttu-id="61e41-108">NetX Crypto se implementa en el lenguaje C estándar (C99), compatible con casi todos los compiladores de C/C++.</span><span class="sxs-lookup"><span data-stu-id="61e41-108">NetX Crypto is implemented in the standard C language (C99), compatible with virtually all C/C++ compilers.</span></span> <span data-ttu-id="61e41-109">Su diseño modular permite que una aplicación solo vincule los algoritmos criptográficos que necesita utilizar, logrando así un tamaño de código mínimo.</span><span class="sxs-lookup"><span data-stu-id="61e41-109">Its modular design allows an application to only link in the crypto algorithms it needs to use, therefore achieving minimal code size.</span></span> <span data-ttu-id="61e41-110">La implementación está diseñada para funcionar con la mayoría de los microprocesadores de 32 bits y solo usa las operaciones matemáticas básicas (suma, resta, multiplicación, división, operador lógico AND, OR, NOR y desplazamiento de bits).</span><span class="sxs-lookup"><span data-stu-id="61e41-110">The implementation is designed to work with most 32-bit microprocessors and uses only the basic math operations (addition, subtraction, multiplication, division, logical AND, OR, NOR, and bit shift operations).</span></span> <span data-ttu-id="61e41-111">Todas estas operaciones se utilizan con cantidades de 32 bits, lo que permite que NetX Crypto sea portable en la mayoría de los microprocesadores de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="61e41-111">All these operations are used with 32-bit quantities, making NetX Crypto portable across most 32-bit microprocessors.</span></span> <span data-ttu-id="61e41-112">La implementación está optimizada específicamente para ejecutarse en microprocesadores con recursos limitados, orientados a aplicaciones profundamente integradas.</span><span class="sxs-lookup"><span data-stu-id="61e41-112">The implementation is specifically optimized to run on resource constrained microprocessors, targeting deeply embedded applications.</span></span>

## <a name="algorithms-supported-by-netx-crypto"></a><span data-ttu-id="61e41-113">Algoritmos admitidos por NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="61e41-113">Algorithms supported by NetX Crypto</span></span>

<span data-ttu-id="61e41-114">NetX Crypto es compatible con los siguientes algoritmos criptográficos.</span><span class="sxs-lookup"><span data-stu-id="61e41-114">NetX Crypto supports the following cryptographic algorithms.</span></span> <span data-ttu-id="61e41-115">NetX Crypto sigue todas las recomendaciones generales y los requisitos básicos dentro de las restricciones de un sistema operativo en tiempo real y las plataformas que requieren una superficie de memoria pequeña y una ejecución eficiente.</span><span class="sxs-lookup"><span data-stu-id="61e41-115">NetX Crypto follows all general recommendations and basic requirements within the constraints of a real-time operating system and platforms requiring a small memory footprint and efficient execution.</span></span>

| <span data-ttu-id="61e41-116">Algoritmo</span><span class="sxs-lookup"><span data-stu-id="61e41-116">Algorithm</span></span>       | <span data-ttu-id="61e41-117">Longitud de clave (bits)</span><span class="sxs-lookup"><span data-stu-id="61e41-117">Key Length (bits)</span></span>      |
| --------------- | ---------------------- |
| <span data-ttu-id="61e41-118">AES(CBC, CTR)</span><span class="sxs-lookup"><span data-stu-id="61e41-118">AES(CBC, CTR)</span></span>   | <span data-ttu-id="61e41-119">128, 192, 256</span><span class="sxs-lookup"><span data-stu-id="61e41-119">128, 192, 256</span></span>          |
| <span data-ttu-id="61e41-120">AES(XCBC)</span><span class="sxs-lookup"><span data-stu-id="61e41-120">AES(XCBC)</span></span>       | <span data-ttu-id="61e41-121">128</span><span class="sxs-lookup"><span data-stu-id="61e41-121">128</span></span>                    |
| <span data-ttu-id="61e41-122">AES-CCM 8</span><span class="sxs-lookup"><span data-stu-id="61e41-122">AES-CCM 8</span></span>       | <span data-ttu-id="61e41-123">128</span><span class="sxs-lookup"><span data-stu-id="61e41-123">128</span></span>                    |
| <span data-ttu-id="61e41-124">3DES(CBC)</span><span class="sxs-lookup"><span data-stu-id="61e41-124">3DES(CBC)</span></span>       | <span data-ttu-id="61e41-125">192</span><span class="sxs-lookup"><span data-stu-id="61e41-125">192</span></span>                    |
| <span data-ttu-id="61e41-126">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="61e41-126">HMAC-SHA1</span></span>       | <span data-ttu-id="61e41-127">Cualquier longitud</span><span class="sxs-lookup"><span data-stu-id="61e41-127">Any length</span></span>             |
| <span data-ttu-id="61e41-128">HMAC-SHA224</span><span class="sxs-lookup"><span data-stu-id="61e41-128">HMAC-SHA224</span></span>     | <span data-ttu-id="61e41-129">Cualquier longitud</span><span class="sxs-lookup"><span data-stu-id="61e41-129">Any length</span></span>             |
| <span data-ttu-id="61e41-130">HMAC-SHA256</span><span class="sxs-lookup"><span data-stu-id="61e41-130">HMAC-SHA256</span></span>     | <span data-ttu-id="61e41-131">Cualquier longitud</span><span class="sxs-lookup"><span data-stu-id="61e41-131">Any length</span></span>             |
| <span data-ttu-id="61e41-132">HMAC-SHA384</span><span class="sxs-lookup"><span data-stu-id="61e41-132">HMAC-SHA384</span></span>     | <span data-ttu-id="61e41-133">Cualquier longitud</span><span class="sxs-lookup"><span data-stu-id="61e41-133">Any length</span></span>             |
| <span data-ttu-id="61e41-134">HMAC-SHA512</span><span class="sxs-lookup"><span data-stu-id="61e41-134">HMAC-SHA512</span></span>     | <span data-ttu-id="61e41-135">Cualquier longitud</span><span class="sxs-lookup"><span data-stu-id="61e41-135">Any length</span></span>             |
| <span data-ttu-id="61e41-136">HMAC-SHA512/224</span><span class="sxs-lookup"><span data-stu-id="61e41-136">HMAC-SHA512/224</span></span> | <span data-ttu-id="61e41-137">Cualquier longitud</span><span class="sxs-lookup"><span data-stu-id="61e41-137">Any length</span></span>             |
| <span data-ttu-id="61e41-138">HMAC-SHA512/256</span><span class="sxs-lookup"><span data-stu-id="61e41-138">HMAC-SHA512/256</span></span> | <span data-ttu-id="61e41-139">Cualquier longitud</span><span class="sxs-lookup"><span data-stu-id="61e41-139">Any length</span></span>             |
| <span data-ttu-id="61e41-140">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="61e41-140">HMAC-MD5</span></span>        | <span data-ttu-id="61e41-141">Cualquier longitud</span><span class="sxs-lookup"><span data-stu-id="61e41-141">Any length</span></span>             |
| <span data-ttu-id="61e41-142">RSA</span><span class="sxs-lookup"><span data-stu-id="61e41-142">RSA</span></span>             | <span data-ttu-id="61e41-143">1024, 2048, 3072, 4096</span><span class="sxs-lookup"><span data-stu-id="61e41-143">1024, 2048, 3072, 4096</span></span> |

| <span data-ttu-id="61e41-144">Algoritmo</span><span class="sxs-lookup"><span data-stu-id="61e41-144">Algorithm</span></span>       | <span data-ttu-id="61e41-145">Longitud de síntesis (bits)</span><span class="sxs-lookup"><span data-stu-id="61e41-145">Digest Length (bits)</span></span> | <span data-ttu-id="61e41-146">Tamaño de bloque (bits)</span><span class="sxs-lookup"><span data-stu-id="61e41-146">Block Size (bits)</span></span> |
| --------------- | -------------------- | ----------------- |
| <span data-ttu-id="61e41-147">SHA1</span><span class="sxs-lookup"><span data-stu-id="61e41-147">SHA1</span></span>            | <span data-ttu-id="61e41-148">160</span><span class="sxs-lookup"><span data-stu-id="61e41-148">160</span></span>                  | <span data-ttu-id="61e41-149">512</span><span class="sxs-lookup"><span data-stu-id="61e41-149">512</span></span>               |
| <span data-ttu-id="61e41-150">SHA224</span><span class="sxs-lookup"><span data-stu-id="61e41-150">SHA224</span></span>          | <span data-ttu-id="61e41-151">224</span><span class="sxs-lookup"><span data-stu-id="61e41-151">224</span></span>                  | <span data-ttu-id="61e41-152">512</span><span class="sxs-lookup"><span data-stu-id="61e41-152">512</span></span>               |
| <span data-ttu-id="61e41-153">SHA256</span><span class="sxs-lookup"><span data-stu-id="61e41-153">SHA256</span></span>          | <span data-ttu-id="61e41-154">256</span><span class="sxs-lookup"><span data-stu-id="61e41-154">256</span></span>                  | <span data-ttu-id="61e41-155">512</span><span class="sxs-lookup"><span data-stu-id="61e41-155">512</span></span>               |
| <span data-ttu-id="61e41-156">SHA384</span><span class="sxs-lookup"><span data-stu-id="61e41-156">SHA384</span></span>          | <span data-ttu-id="61e41-157">384</span><span class="sxs-lookup"><span data-stu-id="61e41-157">384</span></span>                  | <span data-ttu-id="61e41-158">1024</span><span class="sxs-lookup"><span data-stu-id="61e41-158">1024</span></span>              |
| <span data-ttu-id="61e41-159">SHA512</span><span class="sxs-lookup"><span data-stu-id="61e41-159">SHA512</span></span>          | <span data-ttu-id="61e41-160">512</span><span class="sxs-lookup"><span data-stu-id="61e41-160">512</span></span>                  | <span data-ttu-id="61e41-161">1024</span><span class="sxs-lookup"><span data-stu-id="61e41-161">1024</span></span>              |
| <span data-ttu-id="61e41-162">MD5</span><span class="sxs-lookup"><span data-stu-id="61e41-162">MD5</span></span>             | <span data-ttu-id="61e41-163">128</span><span class="sxs-lookup"><span data-stu-id="61e41-163">128</span></span>                  | <span data-ttu-id="61e41-164">512</span><span class="sxs-lookup"><span data-stu-id="61e41-164">512</span></span>               |
| <span data-ttu-id="61e41-165">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="61e41-165">HMAC-SHA1</span></span>       | <span data-ttu-id="61e41-166">160</span><span class="sxs-lookup"><span data-stu-id="61e41-166">160</span></span>                  | <span data-ttu-id="61e41-167">512</span><span class="sxs-lookup"><span data-stu-id="61e41-167">512</span></span>               |
| <span data-ttu-id="61e41-168">HMAC-SHA224</span><span class="sxs-lookup"><span data-stu-id="61e41-168">HMAC-SHA224</span></span>     | <span data-ttu-id="61e41-169">224</span><span class="sxs-lookup"><span data-stu-id="61e41-169">224</span></span>                  | <span data-ttu-id="61e41-170">512</span><span class="sxs-lookup"><span data-stu-id="61e41-170">512</span></span>               |
| <span data-ttu-id="61e41-171">HMAC-SHA256</span><span class="sxs-lookup"><span data-stu-id="61e41-171">HMAC-SHA256</span></span>     | <span data-ttu-id="61e41-172">256</span><span class="sxs-lookup"><span data-stu-id="61e41-172">256</span></span>                  | <span data-ttu-id="61e41-173">512</span><span class="sxs-lookup"><span data-stu-id="61e41-173">512</span></span>               |
| <span data-ttu-id="61e41-174">HMAC-SHA384</span><span class="sxs-lookup"><span data-stu-id="61e41-174">HMAC-SHA384</span></span>     | <span data-ttu-id="61e41-175">384</span><span class="sxs-lookup"><span data-stu-id="61e41-175">384</span></span>                  | <span data-ttu-id="61e41-176">1024</span><span class="sxs-lookup"><span data-stu-id="61e41-176">1024</span></span>              |
| <span data-ttu-id="61e41-177">HMAC-SHA512</span><span class="sxs-lookup"><span data-stu-id="61e41-177">HMAC-SHA512</span></span>     | <span data-ttu-id="61e41-178">512</span><span class="sxs-lookup"><span data-stu-id="61e41-178">512</span></span>                  | <span data-ttu-id="61e41-179">1024</span><span class="sxs-lookup"><span data-stu-id="61e41-179">1024</span></span>              |
| <span data-ttu-id="61e41-180">HMAC-SHA512/224</span><span class="sxs-lookup"><span data-stu-id="61e41-180">HMAC-SHA512/224</span></span> | <span data-ttu-id="61e41-181">224</span><span class="sxs-lookup"><span data-stu-id="61e41-181">224</span></span>                  | <span data-ttu-id="61e41-182">1024</span><span class="sxs-lookup"><span data-stu-id="61e41-182">1024</span></span>              |
| <span data-ttu-id="61e41-183">HMAC-SHA512/256</span><span class="sxs-lookup"><span data-stu-id="61e41-183">HMAC-SHA512/256</span></span> | <span data-ttu-id="61e41-184">256</span><span class="sxs-lookup"><span data-stu-id="61e41-184">256</span></span>                  | <span data-ttu-id="61e41-185">1024</span><span class="sxs-lookup"><span data-stu-id="61e41-185">1024</span></span>              |
| <span data-ttu-id="61e41-186">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="61e41-186">HMAC-MD5</span></span>        | <span data-ttu-id="61e41-187">128</span><span class="sxs-lookup"><span data-stu-id="61e41-187">128</span></span>                  | <span data-ttu-id="61e41-188">512</span><span class="sxs-lookup"><span data-stu-id="61e41-188">512</span></span>               |
| <span data-ttu-id="61e41-189">Curva elíptica</span><span class="sxs-lookup"><span data-stu-id="61e41-189">Elliptic Curve</span></span>  | <span data-ttu-id="61e41-190">P192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="61e41-190">P192/224/256/384/521</span></span> |                   |

## <a name="netx-crypto-requirements"></a><span data-ttu-id="61e41-191">Requisitos de NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="61e41-191">NetX Crypto Requirements</span></span>

<span data-ttu-id="61e41-192">TBD: Requisito de memoria...</span><span class="sxs-lookup"><span data-stu-id="61e41-192">TBD: Memory Requirement..</span></span> <span data-ttu-id="61e41-193">¿Seguridad de interrupción/reentrada?</span><span class="sxs-lookup"><span data-stu-id="61e41-193">Interrupt/re-entrant safe?</span></span> <span data-ttu-id="61e41-194">Necesita debate</span><span class="sxs-lookup"><span data-stu-id="61e41-194">Needs discussion</span></span>

## <a name="netx-crypto-constraints"></a><span data-ttu-id="61e41-195">Restricciones de NetX Crypto</span><span class="sxs-lookup"><span data-stu-id="61e41-195">NetX Crypto Constraints</span></span>

<span data-ttu-id="61e41-196">Ninguno.</span><span class="sxs-lookup"><span data-stu-id="61e41-196">None.</span></span>