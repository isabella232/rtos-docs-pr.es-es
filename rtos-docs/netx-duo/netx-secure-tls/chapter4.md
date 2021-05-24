---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS NetX Secure'
description: Este capítulo contiene una descripción de todos los servicios de NetX Secure (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80ec22058ab64ed0c6258bb3d9364ec44f9a741b
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223399"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="17754-103">Capítulo 4: Descripción de los servicios de Azure RTOS NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="17754-104">Este capítulo contiene una descripción de todos los servicios de Azure RTOS NetX Secure (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="17754-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="17754-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la macro **NX_SECURE_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no aparecen en negrita están totalmente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="17754-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="17754-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="17754-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="17754-107">Realizar pruebas automáticas en los métodos criptográficos</span><span class="sxs-lookup"><span data-stu-id="17754-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="17754-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="17754-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="17754-109">Calcular el valor del código hash mediante una función hash proporcionada por el usuario</span><span class="sxs-lookup"><span data-stu-id="17754-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="17754-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="17754-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="17754-111">Establecer el certificado de identidad activo para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="17754-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="17754-113">Establecer una clave compartida previamente para una sesión de cliente TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="17754-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="17754-115">Inicializar el módulo de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="17754-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="17754-117">Agregar un certificado local a una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="17754-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="17754-119">Buscar un certificado local en una sesión de TLS de NetX Secure por nombre común</span><span class="sxs-lookup"><span data-stu-id="17754-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="17754-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="17754-121">Quitar certificado local de una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="17754-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="17754-123">Calcular el tamaño de los metadatos criptográficos para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="17754-125">Asignar un paquete para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="17754-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="17754-127">Agregar una clave compartida previamente a una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="17754-129">Asignar espacio para el certificado proporcionado por un host de TLS remoto</span><span class="sxs-lookup"><span data-stu-id="17754-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="17754-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="17754-131">Asignar espacio para todos los certificados proporcionados por un host de TLS remoto</span><span class="sxs-lookup"><span data-stu-id="17754-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="17754-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="17754-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="17754-133">Liberar el espacio asignado para los certificados entrantes</span><span class="sxs-lookup"><span data-stu-id="17754-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="17754-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="17754-135">Agregar un certificado específicamente para servidores TLS mediante un identificador numérico</span><span class="sxs-lookup"><span data-stu-id="17754-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="17754-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="17754-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="17754-137">Buscar un certificado mediante un identificador numérico</span><span class="sxs-lookup"><span data-stu-id="17754-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="17754-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="17754-139">Quitar un certificado de servidor local mediante un identificador numérico</span><span class="sxs-lookup"><span data-stu-id="17754-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="17754-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="17754-141">Configurar una devolución de llamada para que TLS la use para la validación de certificados adicional</span><span class="sxs-lookup"><span data-stu-id="17754-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="17754-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="17754-143">Configurar una devolución de llamada para que TLS la invoque al principio de un protocolo de enlace de cliente TLS</span><span class="sxs-lookup"><span data-stu-id="17754-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="17754-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="17754-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="17754-145">Habilitar la comprobación X.509 de cliente y asignar espacio para los certificados de cliente</span><span class="sxs-lookup"><span data-stu-id="17754-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="17754-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="17754-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="17754-147">Deshabilitar la autenticación de certificados de cliente para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="17754-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="17754-149">Habilitar la autenticación de certificados de cliente para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="17754-151">Crear una sesión de TLS de NetX Secure para comunicaciones seguras</span><span class="sxs-lookup"><span data-stu-id="17754-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="17754-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="17754-153">Eliminar una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="17754-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="17754-155">Finalizar una sesión activa de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="17754-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="17754-157">Establecer el búfer de reensamblado de paquetes para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="17754-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="17754-159">Invalidar la versión predeterminada del protocolo TLS para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="17754-161">Recibir datos de una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="17754-163">Asignar una devolución de llamada que se invocará al comienzo de una renegociación de sesión</span><span class="sxs-lookup"><span data-stu-id="17754-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="17754-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="17754-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="17754-165">Iniciar un protocolo de enlace de renegociación de sesión con el host remoto</span><span class="sxs-lookup"><span data-stu-id="17754-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="17754-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="17754-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="17754-167">Borrar y restablecer una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="17754-169">Enviar datos mediante una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="17754-171">Configurar una devolución de llamada para que TLS la invoque al comienzo de un protocolo de enlace del servidor TLS</span><span class="sxs-lookup"><span data-stu-id="17754-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="17754-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="17754-173">Analizar una extensión de Indicación de nombre de servidor (SNI) recibida desde un cliente TLS</span><span class="sxs-lookup"><span data-stu-id="17754-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="17754-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="17754-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="17754-175">Establecer un nombre DNS de extensión de Indicación de nombre de servidor (SNI) para enviar a un servidor remoto</span><span class="sxs-lookup"><span data-stu-id="17754-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="17754-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="17754-177">Iniciar una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="17754-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="17754-179">Asignar una función de marca de tiempo a una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="17754-181">Agregar un certificado de confianza a la sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="17754-183">Quitar un certificado de confianza de la sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="17754-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="17754-185">Inicializar un certificado X.509 para TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="17754-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="17754-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="17754-187">Comprobar el nombre DNS con el certificado X.509</span><span class="sxs-lookup"><span data-stu-id="17754-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="17754-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="17754-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="17754-189">Comprobar el certificado X.509 en una lista de revocación de certificados (CRL) proporcionada</span><span class="sxs-lookup"><span data-stu-id="17754-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="17754-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="17754-191">Inicializar una estructura de nombre DNS de X.509</span><span class="sxs-lookup"><span data-stu-id="17754-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="17754-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="17754-193">Buscar y analizar una extensión de uso extendido de clave X.509 en un certificado X.509</span><span class="sxs-lookup"><span data-stu-id="17754-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="17754-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="17754-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="17754-195">Buscar y devolver una extensión X.509 en un certificado X.509</span><span class="sxs-lookup"><span data-stu-id="17754-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="17754-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="17754-197">Buscar y analizar una extensión de uso de clave X.509 en un certificado X.509</span><span class="sxs-lookup"><span data-stu-id="17754-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="17754-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="17754-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="17754-199">Realizar pruebas automáticas en los métodos criptográficos</span><span class="sxs-lookup"><span data-stu-id="17754-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-200">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="17754-201">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-201">Description</span></span>

<span data-ttu-id="17754-202">Este servicio ejecuta las pruebas automáticas de los métodos criptográficos para realizar la validación.</span><span class="sxs-lookup"><span data-stu-id="17754-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="17754-203">La prueba automática solo está disponible si se ha compilado la biblioteca de NetX Secure con el símbolo NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK definido.</span><span class="sxs-lookup"><span data-stu-id="17754-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="17754-204">Para cada método criptográfico admitido, la prueba automática proporciona datos de entrada predefinidos y comprueba que la salida coincide con el valor esperado predefinido.</span><span class="sxs-lookup"><span data-stu-id="17754-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="17754-205">La prueba automática de criptografía de NetX Secure admite los siguientes algoritmos y tamaños de clave:</span><span class="sxs-lookup"><span data-stu-id="17754-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="17754-206">DES: cifrado y descifrado</span><span class="sxs-lookup"><span data-stu-id="17754-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="17754-207">Triple DES (3DES): cifrado y descifrado</span><span class="sxs-lookup"><span data-stu-id="17754-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="17754-208">AES: tamaño de clave de 128, 192 y 256 bits, cifrado y descifrado, en modo CBC y en modo de contador.</span><span class="sxs-lookup"><span data-stu-id="17754-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="17754-209">HMAC-MD5: autenticación y cálculo de hash</span><span class="sxs-lookup"><span data-stu-id="17754-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="17754-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, autenticación y cálculo de hash</span><span class="sxs-lookup"><span data-stu-id="17754-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="17754-211">MD5: autenticación</span><span class="sxs-lookup"><span data-stu-id="17754-211">MD5: authentication</span></span>
- <span data-ttu-id="17754-212">Función pseudoaleatoria (PRF): PRF_HMAC_SHA1 y PRF_HMAC_SHA2-256</span><span class="sxs-lookup"><span data-stu-id="17754-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="17754-213">RSA: operación de potencia-módulo de RSA de 1024, 2048 y 4096 bits</span><span class="sxs-lookup"><span data-stu-id="17754-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="17754-214">SHA: autenticación SHA1 (96 y 160 bits) y SHA2 (256 bits, 384 bits, 512 bits)</span><span class="sxs-lookup"><span data-stu-id="17754-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="17754-215">Esta función tiene los vectores integrados para los algoritmos criptográficos enumerados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="17754-216">Sin embargo, solo comprueba los que aparecen en el elemento *cipher_table* pasado a esta función.</span><span class="sxs-lookup"><span data-stu-id="17754-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="17754-217">Por ejemplo, para una sesión de TLS que solo usa el conjunto de cifrado TLS_RSA_WITH_AES_128_CBC_SHA, esta función realizará una prueba automática en RSA (1024, 2048 y 4096 bits), AES-CBC (128 bits) y SHA1.</span><span class="sxs-lookup"><span data-stu-id="17754-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-218">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-218">Parameters</span></span>

- <span data-ttu-id="17754-219">**crypto_table**: puntero a la tabla de cifrado que utiliza la sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="17754-220">Es el mismo elemento crypto_table que se pasa a la llamada **_nx_secure_tls_session_create()_**.</span><span class="sxs-lookup"><span data-stu-id="17754-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="17754-221">**metadata**: puntero al espacio para el área de metadatos de criptografía.</span><span class="sxs-lookup"><span data-stu-id="17754-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="17754-222">.</span><span class="sxs-lookup"><span data-stu-id="17754-222">.</span></span>
- <span data-ttu-id="17754-223">**metadata_size**: tamaño del búfer de metadatos.</span><span class="sxs-lookup"><span data-stu-id="17754-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-224">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-224">Return Values</span></span>

- <span data-ttu-id="17754-225">**NX_SECURE_TLS_SUCCESS**: (0x00) Se han probado correctamente los métodos criptográficos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="17754-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="17754-226">**NX_PTR_ERROR**: (0x07) Estructura de método criptográfico no válida.</span><span class="sxs-lookup"><span data-stu-id="17754-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="17754-227">**NX_NOT_SUCCESSFUL**: (0x43) Se ha producido un error en la prueba automática de criptografía.</span><span class="sxs-lookup"><span data-stu-id="17754-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-228">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-228">Allowed From</span></span>

<span data-ttu-id="17754-229">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-230">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-230">Example</span></span>

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a><span data-ttu-id="17754-231">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-231">See Also</span></span>

- <span data-ttu-id="17754-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="17754-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="17754-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="17754-234">Calcular el valor del código hash mediante una función hash proporcionada por el usuario</span><span class="sxs-lookup"><span data-stu-id="17754-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-235">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="17754-236">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-236">Description</span></span>

<span data-ttu-id="17754-237">Esta función calcula el valor del código hash del flujo de datos del área de memoria especificada, utilizando el método criptográfico HMAC y la cadena de clave proporcionados.</span><span class="sxs-lookup"><span data-stu-id="17754-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="17754-238">La función de cálculo del código hash del módulo solo está disponible si se ha compilado la biblioteca de NetX Secure con el siguiente símbolo definido: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span><span class="sxs-lookup"><span data-stu-id="17754-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-239">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-239">Parameters</span></span>

- <span data-ttu-id="17754-240">**hmac_ptr**: puntero al método criptográfico HMAC que se utiliza para calcular el valor del código hash.</span><span class="sxs-lookup"><span data-stu-id="17754-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="17754-241">**start_address**: dirección inicial del búfer de datos.</span><span class="sxs-lookup"><span data-stu-id="17754-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="17754-242">**end_address**: dirección final del búfer de datos.</span><span class="sxs-lookup"><span data-stu-id="17754-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="17754-243">Tenga en cuenta que el cálculo del código hash no incluye los datos de esta dirección final.</span><span class="sxs-lookup"><span data-stu-id="17754-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="17754-244">**key**: cadena de clave que se usa en el cálculo de HMAC.</span><span class="sxs-lookup"><span data-stu-id="17754-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="17754-245">**key_length**: tamaño de la cadena de clave en bytes.</span><span class="sxs-lookup"><span data-stu-id="17754-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="17754-246">**metadata**: puntero al espacio usado por el algoritmo HMAC.</span><span class="sxs-lookup"><span data-stu-id="17754-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="17754-247">**metadata_size**: tamaño del búfer de metadatos.</span><span class="sxs-lookup"><span data-stu-id="17754-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="17754-248">**output_buffer**: ubicación de memoria donde se va a almacenar la salida del código hash.</span><span class="sxs-lookup"><span data-stu-id="17754-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="17754-249">**output_buffer_size**: espacio disponible del búfer de salida en bytes.</span><span class="sxs-lookup"><span data-stu-id="17754-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="17754-250">**actual_size**: lo devuelve la función e indica el número real de bytes que se escriben en el búfer de salida.</span><span class="sxs-lookup"><span data-stu-id="17754-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-251">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-251">Return Values</span></span>

- <span data-ttu-id="17754-252">**0**: se ha calculado correctamente el valor del código hash.</span><span class="sxs-lookup"><span data-stu-id="17754-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="17754-253">**1**: error en el cálculo del código hash.</span><span class="sxs-lookup"><span data-stu-id="17754-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-254">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-254">Allowed From</span></span>

<span data-ttu-id="17754-255">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-256">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-256">Example</span></span>

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a><span data-ttu-id="17754-257">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-257">See Also</span></span>

- <span data-ttu-id="17754-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="17754-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="17754-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="17754-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="17754-260">Establecer el certificado de identidad activo para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-261">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="17754-262">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-262">Description</span></span>

<span data-ttu-id="17754-263">Este servicio está diseñado para ser llamado desde una devolución de llamada de sesión (consulte nx_secure_tls_session_client_callback_set y nx_secure_tls_session_server_callback_set).</span><span class="sxs-lookup"><span data-stu-id="17754-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="17754-264">Cuando se le llama con una estructura NX_SECURE_X509_CERT inicializada previamente, se usará ese certificado en lugar del certificado de identidad predeterminado.</span><span class="sxs-lookup"><span data-stu-id="17754-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="17754-265">En la mayoría de los casos, el certificado se debe haber agregado al almacén local (consulte nx_secure_tls_local_certificate_add) o el protocolo de enlace de TLS puede producir un error.</span><span class="sxs-lookup"><span data-stu-id="17754-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="17754-266">Este servicio está diseñado para permitir que TLS admita varios certificados de identidad.</span><span class="sxs-lookup"><span data-stu-id="17754-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="17754-267">Esto resulta útil para un servidor de TLS que proporciona servicio a varias direcciones de red para que el servidor pueda elegir un certificado adecuado para proporcionar al cliente remoto en función del punto de entrada del cliente.</span><span class="sxs-lookup"><span data-stu-id="17754-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="17754-268">Para un cliente TLS, esta rutina se puede usar para cambiar el certificado que se envía a un servidor remoto en tiempo de ejecución después de que el servidor se haya identificado en el protocolo de enlace de TLS (esto es menos frecuente que el caso de uso de servidor TLS).</span><span class="sxs-lookup"><span data-stu-id="17754-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="17754-269">En el caso de que varios certificados puedan compartir el mismo nombre distintivo X.509, los certificados deberán agregarse mediante nx_secure_tls_server_certificate_add, que introduce un identificador numérico independiente del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-270">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-270">Parameters</span></span>

- <span data-ttu-id="17754-271">**session_ptr**: puntero a una instancia de sesión de TLS que se pasa a la devolución de llamada de sesión.</span><span class="sxs-lookup"><span data-stu-id="17754-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="17754-272">**certificate**: puntero a un certificado X.509 inicializado que se va a utilizar para la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="17754-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-273">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-273">Return Values</span></span>

- <span data-ttu-id="17754-274">**NX_SUCCESS**: (0x00) Asignación correcta del certificado a la sesión.</span><span class="sxs-lookup"><span data-stu-id="17754-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="17754-275">**NX_PTR_ERROR**: (0x07) Puntero de certificado o sesión de TLS no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-276">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-276">Allowed From</span></span>

<span data-ttu-id="17754-277">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-278">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-278">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a><span data-ttu-id="17754-279">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-279">See Also</span></span>

- <span data-ttu-id="17754-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="17754-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="17754-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="17754-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="17754-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="17754-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="17754-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="17754-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="17754-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="17754-288">Establecer una clave compartida previamente para una sesión de cliente TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-289">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="17754-290">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-290">Description</span></span>

<span data-ttu-id="17754-291">Este servicio agrega una clave compartida previamente (PSK), su cadena de identidad y una sugerencia de identidad a un bloque de control de sesión de TLS, y establece esa PSK para que se use en las conexiones de cliente TLS subsiguientes.</span><span class="sxs-lookup"><span data-stu-id="17754-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="17754-292">La PSK se usa en lugar de un certificado digital cuando se habilitan y se usan conjuntos de cifrado de PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="17754-293">En este caso, la PSK está asociada a un servidor TLS remoto específico con el que el cliente TLS desea comunicarse.</span><span class="sxs-lookup"><span data-stu-id="17754-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="17754-294">La PSK establecida mediante esta API se proporcionará al host del servidor TLS remoto durante el siguiente protocolo de enlace de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-295">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-295">Parameters</span></span>

- <span data-ttu-id="17754-296">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-297">**pre_shared_key**: valor real de la PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="17754-298">**psk_length**: longitud del valor de la PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="17754-299">**psk_identity**: cadena que se usa para identificar este valor de PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="17754-300">**identity_length**: longitud de la identidad de la PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="17754-301">**hint**: cadena usada para indicar qué grupo de PSK elegir en un servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="17754-302">**hint_length**: longitud de la cadena de sugerencia.</span><span class="sxs-lookup"><span data-stu-id="17754-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-303">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-303">Return Values</span></span>

- <span data-ttu-id="17754-304">**NX_SUCCESS**: (0x00) PSK agregada correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="17754-305">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="17754-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE**: (0x125) No se puede agregar otra PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-307">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-307">Allowed From</span></span>

<span data-ttu-id="17754-308">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-309">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-310">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-310">See Also</span></span>

- <span data-ttu-id="17754-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="17754-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="17754-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="17754-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="17754-317">Inicializar el módulo de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-318">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="17754-319">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-319">Description</span></span>

<span data-ttu-id="17754-320">Este servicio inicializa el módulo de TLS de NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="17754-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="17754-321">Se le debe llamar antes de que se pueda acceder a otros servicios de NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="17754-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-322">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-322">Parameters</span></span>

<span data-ttu-id="17754-323">Ninguno</span><span class="sxs-lookup"><span data-stu-id="17754-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-324">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-324">Return Values</span></span>

<span data-ttu-id="17754-325">Ninguno</span><span class="sxs-lookup"><span data-stu-id="17754-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-326">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-326">Allowed From</span></span>

<span data-ttu-id="17754-327">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-328">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="17754-329">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-329">See Also</span></span>

- <span data-ttu-id="17754-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="17754-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="17754-332">Agregar un certificado local a una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-333">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="17754-334">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-334">Description</span></span>

<span data-ttu-id="17754-335">Este servicio agrega una instancia de la estructura NX_SECURE_X509_CERT inicializada al almacén local de una sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="17754-336">Este certificado puede ser utilizado por la pila de TLS para identificar el dispositivo durante el protocolo de enlace de TLS (si se marcó como certificado de identidad durante la inicialización de la estructura del certificado mediante nx_secure_x509_certificate_initialize) o como un emisor como parte de una cadena de certificados proporcionada al host remoto durante el protocolo de enlace de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="17754-337">Si se necesitan varios certificados locales con el mismo nombre común, se pueden agregar certificados mediante el servicio *nx_secure_tls_server_certificate_add* (consulte la advertencia siguiente).</span><span class="sxs-lookup"><span data-stu-id="17754-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="17754-338">Se **requiere** un certificado para el modo de servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="17754-339">El certificado es *opcional* para el modo de cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-340">*Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_server_certificate_add. La API de certificados de servidor utiliza un identificador numérico único para cada certificado y nx_secure_tls_local_certificate_add indexa en función del nombre común de X.509. Los servicios de certificados locales proporcionan una alternativa cómoda al identificador numérico para las aplicaciones que usan un solo certificado de identidad: mediante el uso del nombre común, la aplicación no necesita realizar un seguimiento de los identificadores numéricos.*</span><span class="sxs-lookup"><span data-stu-id="17754-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-341">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-341">Parameters</span></span>

- <span data-ttu-id="17754-342">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-343">**certificate_ptr**: puntero a una instancia de certificado TLS inicializada.</span><span class="sxs-lookup"><span data-stu-id="17754-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-344">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-344">Return Values</span></span>

- <span data-ttu-id="17754-345">**NX_SUCCESS**: (0x00) Certificado agregado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="17754-346">**NX_INVALID_PARAMETERS**: (0x4D) Se ha intentado agregar un certificado no válido o duplicado.</span><span class="sxs-lookup"><span data-stu-id="17754-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="17754-347">**NX_PTR_ERROR**: (0x07) Puntero de certificado o sesión de TLS no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-348">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-348">Allowed From</span></span>

<span data-ttu-id="17754-349">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-350">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-351">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-351">See Also</span></span>

- <span data-ttu-id="17754-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="17754-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="17754-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="17754-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="17754-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="17754-358">Buscar un certificado local en una sesión de TLS de NetX Secure por nombre común</span><span class="sxs-lookup"><span data-stu-id="17754-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-359">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="17754-360">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-360">Description</span></span>

<span data-ttu-id="17754-361">Este servicio encuentra un certificado en el almacén de certificados del dispositivo local de una sesión de TLS y devuelve un puntero a la estructura NX_SECURE_X509_CERT del almacén.</span><span class="sxs-lookup"><span data-stu-id="17754-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="17754-362">El parámetro common_name y su longitud (name_length) se usan para identificar el certificado en el almacén mediante la coincidencia del campo de nombre común del firmante X.509 del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="17754-363">Si hay más de un certificado con el mismo nombre común, solo se devolverá el primero: use *nx_secure_tls_server_certificate_find* en su lugar.</span><span class="sxs-lookup"><span data-stu-id="17754-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-364">*Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_server_certificate_add. La API de certificados de servidor utiliza un identificador numérico único para cada certificado y nx_secure_tls_local_certificate_add indexa en función del nombre común de X.509. Los servicios de certificados locales proporcionan una alternativa cómoda al identificador numérico para las aplicaciones que usan un solo certificado de identidad: mediante el uso del nombre común, la aplicación no necesita realizar un seguimiento de los identificadores numéricos.*</span><span class="sxs-lookup"><span data-stu-id="17754-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-365">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-365">Parameters</span></span>

- <span data-ttu-id="17754-366">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-367">**certificate**: puntero devuelto al certificado coincidente.</span><span class="sxs-lookup"><span data-stu-id="17754-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="17754-368">**common_name**: cadena de nombre común que debe coincidir (nombre DNS).</span><span class="sxs-lookup"><span data-stu-id="17754-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="17754-369">**name_length**: longitud de los datos de cadena common_name.</span><span class="sxs-lookup"><span data-stu-id="17754-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-370">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-370">Return Values</span></span>

- <span data-ttu-id="17754-371">**NX_SUCCESS**: (0x00) Se encontró el certificado y se devolvió el puntero en el parámetro "certificate".</span><span class="sxs-lookup"><span data-stu-id="17754-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="17754-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) No se encontró ningún certificado con el nombre común proporcionado.</span><span class="sxs-lookup"><span data-stu-id="17754-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="17754-373">**NX_PTR_ERROR**: (0x07) Sesión de TLS, puntero de certificado o cadena de nombre común no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-374">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-374">Allowed From</span></span>

<span data-ttu-id="17754-375">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-376">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-376">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a><span data-ttu-id="17754-377">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-377">See Also</span></span>

- <span data-ttu-id="17754-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="17754-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="17754-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="17754-384">Quitar certificado local de una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-385">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="17754-386">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-386">Description</span></span>

<span data-ttu-id="17754-387">Este servicio quita una instancia de certificado local de una sesión de TLS, con la clave en el campo de nombre común del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-388">*Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_server_certificate_add. La API de certificados de servidor utiliza un identificador numérico único para cada certificado y nx_secure_tls_local_certificate_add indexa en función del nombre común de X.509. Los servicios de certificados locales proporcionan una alternativa cómoda al identificador numérico para las aplicaciones que usan un solo certificado de identidad: mediante el uso del nombre común, la aplicación no necesita realizar un seguimiento de los identificadores numéricos.*</span><span class="sxs-lookup"><span data-stu-id="17754-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-389">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-389">Parameters</span></span>

- <span data-ttu-id="17754-390">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-391">**common_name**: valor del nombre común del certificado que se va a quitar.</span><span class="sxs-lookup"><span data-stu-id="17754-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="17754-392">**common_name_length**: longitud de la cadena del nombre común.</span><span class="sxs-lookup"><span data-stu-id="17754-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-393">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-393">Return Values</span></span>

- <span data-ttu-id="17754-394">**NX_SUCCESS**: (0x00) Certificado agregado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="17754-395">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="17754-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) No se encontró el certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-397">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-397">Allowed From</span></span>

<span data-ttu-id="17754-398">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-399">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-400">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-400">See Also</span></span>

- <span data-ttu-id="17754-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="17754-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="17754-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="17754-406">Calcular el tamaño de los metadatos criptográficos para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-407">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="17754-408">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-408">Description</span></span>

<span data-ttu-id="17754-409">Este servicio calcula y devuelve el tamaño de los metadatos criptográficos necesarios para una sesión de TLS determinada y la tabla de criptografía TLS (consulte la sección "Inicialización de TLS con métodos criptográficos" para más información sobre la tabla de cifrado criptográfico).</span><span class="sxs-lookup"><span data-stu-id="17754-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="17754-410">Se debe llamar a este servicio con la tabla criptográfica deseada para calcular el tamaño del búfer de metadatos que se pasa en nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="17754-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-411">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-411">Parameters</span></span>

- <span data-ttu-id="17754-412">**crypto_table**: puntero a una tabla de criptografía completa de TLS de NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="17754-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="17754-413">**metadata_size**: salida del cálculo de tamaño en bytes.</span><span class="sxs-lookup"><span data-stu-id="17754-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-414">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-414">Return Values</span></span>

- <span data-ttu-id="17754-415">**NX_SUCCESS**: (0x00) Cálculo correcto del tamaño de los metadatos.</span><span class="sxs-lookup"><span data-stu-id="17754-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="17754-416">**NX_PTR_ERROR**: (0x07) Tabla de cifrado o puntero al tamaño devuelto no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-417">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-417">Allowed From</span></span>

<span data-ttu-id="17754-418">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-419">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-419">Example</span></span>

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-420">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-420">See Also</span></span>

- <span data-ttu-id="17754-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="17754-422">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-422">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="17754-423">Asignar un paquete para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-423">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-424">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-424">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="17754-425">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-425">Description</span></span>

<span data-ttu-id="17754-426">Este servicio asigna un elemento NX_PACKET para la sesión de TLS activa especificada desde el elemento NX_PACKET_POOL especificado.</span><span class="sxs-lookup"><span data-stu-id="17754-426">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="17754-427">La aplicación debe llamar a este servicio para asignar los paquetes de datos que se enviarán mediante una conexión TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-427">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="17754-428">Se debe inicializar la sesión de TLS antes de llamar a este servicio.</span><span class="sxs-lookup"><span data-stu-id="17754-428">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="17754-429">El paquete asignado se ha inicializado correctamente para que se puedan agregar los datos de encabezado y pie de página de TLS una vez que se hayan rellenado los datos del paquete.</span><span class="sxs-lookup"><span data-stu-id="17754-429">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="17754-430">De lo contrario, el comportamiento es idéntico al de *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="17754-430">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-431">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-431">Parameters</span></span>

- <span data-ttu-id="17754-432">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-432">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-433">**pool_ptr**: puntero a un elemento NX_PACKET_POOL desde el que se va a asignar el paquete.</span><span class="sxs-lookup"><span data-stu-id="17754-433">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="17754-434">**packet_ptr**: puntero de salida al paquete recién asignado.</span><span class="sxs-lookup"><span data-stu-id="17754-434">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="17754-435">**wait_option**: opción de suspensión para la asignación de paquetes.</span><span class="sxs-lookup"><span data-stu-id="17754-435">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-436">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-436">Return Values</span></span>

- <span data-ttu-id="17754-437">**NX_SUCCESS**: (0x00) Asignación correcta del paquete.</span><span class="sxs-lookup"><span data-stu-id="17754-437">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="17754-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**: (0x111) Error al asignar el paquete subyacente.</span><span class="sxs-lookup"><span data-stu-id="17754-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="17754-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED**: (0x101) No se inicializó la sesión de TLS proporcionada.</span><span class="sxs-lookup"><span data-stu-id="17754-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-440">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-440">Allowed From</span></span>

<span data-ttu-id="17754-441">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-442">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-442">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-443">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-443">See Also</span></span>

- <span data-ttu-id="17754-444">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="17754-444">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="17754-445">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-445">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-446">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-446">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-447">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-447">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-448">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-448">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="17754-449">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-449">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-450">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-450">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-451">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="17754-451">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="17754-452">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-452">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="17754-453">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="17754-453">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="17754-454">Agregar una clave compartida previamente a una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-454">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-455">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-455">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="17754-456">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-456">Description</span></span>

<span data-ttu-id="17754-457">Este servicio agrega una clave compartida previamente (PSK), su cadena de identidad y una sugerencia de identidad a un bloque de control de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-457">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="17754-458">La PSK se usa en lugar de un certificado digital cuando se habilitan y se usan conjuntos de cifrado de PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-458">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-459">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-459">Parameters</span></span>

- <span data-ttu-id="17754-460">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-460">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-461">**pre_shared_key**: valor real de la PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-461">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="17754-462">**psk_length**: longitud del valor de la PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-462">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="17754-463">**psk_identity**: cadena que se usa para identificar este valor de PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-463">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="17754-464">**identity_length**: longitud de la identidad de la PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-464">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="17754-465">**hint**: cadena usada para indicar qué grupo de PSK elegir en un servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-465">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="17754-466">**hint_length**: longitud de la cadena de sugerencia.</span><span class="sxs-lookup"><span data-stu-id="17754-466">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-467">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-467">Return Values</span></span>

- <span data-ttu-id="17754-468">**NX_SUCCESS**: (0x00) PSK agregada correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-468">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="17754-469">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-469">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="17754-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE**: (0x125) No se puede agregar otra PSK.</span><span class="sxs-lookup"><span data-stu-id="17754-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-471">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-471">Allowed From</span></span>

<span data-ttu-id="17754-472">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-473">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-473">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-474">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-474">See Also</span></span>

- <span data-ttu-id="17754-475">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="17754-475">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="17754-476">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-476">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-477">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-477">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-478">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-478">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-479">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-479">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="17754-480">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-480">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="17754-481">Asignar espacio para el certificado proporcionado por un host de TLS remoto</span><span class="sxs-lookup"><span data-stu-id="17754-481">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-482">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-482">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="17754-483">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-483">Description</span></span>

<span data-ttu-id="17754-484">Este servicio agrega una instancia de la estructura NX_SECURE_X509_CERT sin inicializar a una sesión de TLS con el fin de asignar espacio para los certificados proporcionados por un host remoto durante una sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-484">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="17754-485">Los datos del certificado remoto se analizan mediante el uso de TLS de NetX Secure y esa información se usa para rellenar la instancia de la estructura de certificado proporcionada a esta función.</span><span class="sxs-lookup"><span data-stu-id="17754-485">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="17754-486">Los certificados agregados de esta manera se colocan en una lista vinculada.</span><span class="sxs-lookup"><span data-stu-id="17754-486">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="17754-487">Si se espera que el host remoto proporcione varios certificados, se debe llamar a esta función de forma repetida para asignar espacio para todos los certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-487">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="17754-488">Los certificados adicionales se agregan al final de la lista de certificados vinculados.</span><span class="sxs-lookup"><span data-stu-id="17754-488">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="17754-489">Si no se asigna un certificado remoto, se producirá un error en el modo de cliente TLS durante el protocolo de enlace de TLS, a menos que se utilice el conjunto de cifrado de una clave compartida previamente (PSK).</span><span class="sxs-lookup"><span data-stu-id="17754-489">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="17754-490">El parámetro *raw_certificate_buffer* apunta al espacio asignado para almacenar el certificado remoto entrante.</span><span class="sxs-lookup"><span data-stu-id="17754-490">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="17754-491">Los certificados típicos con claves RSA de 2048 bits y SHA-256 para las firmas están en el intervalo de 1000 a 2000 bytes.</span><span class="sxs-lookup"><span data-stu-id="17754-491">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="17754-492">El búfer debe ser lo suficientemente grande como para contener, como mínimo, ese tamaño, pero, en función de los certificados del host remoto, puede ser considerablemente menor o mayor.</span><span class="sxs-lookup"><span data-stu-id="17754-492">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="17754-493">Tenga en cuenta que si el búfer es demasiado pequeño para contener el certificado entrante, el protocolo de enlace de TLS finalizará con un error.</span><span class="sxs-lookup"><span data-stu-id="17754-493">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="17754-494">En el modo de servidor TLS, solo se necesita la asignación de certificados remotos si está habilitada la autenticación de certificados de cliente.</span><span class="sxs-lookup"><span data-stu-id="17754-494">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-495">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-495">Parameters</span></span>

- <span data-ttu-id="17754-496">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-496">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-497">**certificate_ptr**: puntero a una instancia de certificado X.509 no inicializada.</span><span class="sxs-lookup"><span data-stu-id="17754-497">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="17754-498">**raw_certificate_buffer**: puntero a un búfer para almacenar el certificado no analizado recibido del host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-498">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="17754-499">**raw_buffer_size**: tamaño del búfer de certificados sin procesar.</span><span class="sxs-lookup"><span data-stu-id="17754-499">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-500">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-500">Return Values</span></span>

- <span data-ttu-id="17754-501">**NX_SUCCESS**: (0x00) Certificado asignado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-501">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="17754-502">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-502">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="17754-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**: (0x12D) El búfer proporcionado era demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="17754-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="17754-504">**NX_INVALID_PARAMETERS**: (0x4D) Se ha intentado agregar un certificado no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-504">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-505">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-505">Allowed From</span></span>

<span data-ttu-id="17754-506">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-507">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-507">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-508">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-508">See Also</span></span>

- <span data-ttu-id="17754-509">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-509">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="17754-510">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-510">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="17754-511">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-511">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="17754-512">Asignar espacio para todos los certificados proporcionados por un host de TLS remoto</span><span class="sxs-lookup"><span data-stu-id="17754-512">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-513">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-513">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="17754-514">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-514">Description</span></span>

<span data-ttu-id="17754-515">Este servicio asigna espacio para procesar cadenas de certificados entrantes de los hosts de servidor remotos con el fin de realizar la autenticación X.509 y la comprobación en una instancia de cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-515">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="17754-516">En el modo de servidor TLS, la asignación de certificados remotos solo es necesaria si está habilitada la autenticación de certificados X.509 de cliente: en el caso de las instancias de servidor TLS, se debe usar en su lugar el servicio *nx_secure_tls_session_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="17754-516">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="17754-517">Si no se asignan certificados remotos, se producirá un error en el modo de cliente TLS durante el protocolo de enlace de TLS, a menos que se utilice el conjunto de cifrado de una clave compartida previamente (PSK).</span><span class="sxs-lookup"><span data-stu-id="17754-517">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="17754-518">El parámetro *certificate_buffer* apunta al espacio asignado para almacenar los certificados remotos entrantes y los bloques de control necesarios para dichos certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-518">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="17754-519">El búfer se dividirá por el número de certificados (*certs_number*) con una parte igual para cada certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-519">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="17754-520">El parámetro *buffer_size* indica el tamaño del búfer.</span><span class="sxs-lookup"><span data-stu-id="17754-520">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="17754-521">Se puede determinar el espacio necesario con la siguiente fórmula:</span><span class="sxs-lookup"><span data-stu-id="17754-521">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="17754-522">Los certificados típicos con claves RSA de 2048 bits y SHA-256 para las firmas están en el intervalo de 1000 a 2000 bytes.</span><span class="sxs-lookup"><span data-stu-id="17754-522">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="17754-523">El búfer debe ser lo suficientemente grande como para contener, como mínimo, ese tamaño para cada certificado, pero, en función de los certificados del host remoto, puede ser considerablemente menor o mayor.</span><span class="sxs-lookup"><span data-stu-id="17754-523">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="17754-524">Tenga en cuenta que si el búfer es demasiado pequeño para contener el certificado entrante, el protocolo de enlace de TLS finalizará con un error.</span><span class="sxs-lookup"><span data-stu-id="17754-524">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-525">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-525">Parameters</span></span>

- <span data-ttu-id="17754-526">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-526">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="17754-527">**certs_number**: número de certificados que se van a asignar desde el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="17754-527">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="17754-528">**certificate_buffer**: puntero a un búfer para contener los certificados recibidos de un host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-528">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="17754-529">**buffer_size**: tamaño del búfer de certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-529">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-530">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-530">Return Values</span></span>

- <span data-ttu-id="17754-531">**NX_SUCCESS**: (0x00) Certificado asignado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-531">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="17754-532">**NX_PTR_ERROR**: (0x07) Sesión de TLS o puntero de búfer no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-532">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="17754-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**: (0x12D) El búfer proporcionado era demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="17754-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="17754-534">**NX_INVALID_PARAMETERS**: (0x4D) El búfer era demasiado pequeño para contener el número deseado de certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-534">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-535">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-535">Allowed From</span></span>

<span data-ttu-id="17754-536">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-536">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-537">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-537">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-538">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-538">See Also</span></span>

- <span data-ttu-id="17754-539">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-539">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-540">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-540">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="17754-541">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="17754-541">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="17754-542">Liberar el espacio asignado para los certificados entrantes</span><span class="sxs-lookup"><span data-stu-id="17754-542">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-543">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-543">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="17754-544">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-544">Description</span></span>

<span data-ttu-id="17754-545">Este servicio se usa para liberar todos los búferes de certificado asignados a una sesión de TLS determinada con nx_secure_tls_remote_certificate_allocated mediante su devolución al espacio de certificados libre de esa sesión.</span><span class="sxs-lookup"><span data-stu-id="17754-545">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="17754-546">Esto puede ser necesario si una aplicación reutiliza un objeto de sesión de TLS sin eliminarlo y volver a crearlo con nx_secure_tls_session_delete y nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="17754-546">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="17754-547">Tenga en cuenta que el espacio de certificados remotos se recupera automáticamente cuando se restablece la sesión de TLS, como sucede en nx_secure_tls_session_end, por lo que la mayoría de las aplicaciones no tendrán que llamar a este servicio.</span><span class="sxs-lookup"><span data-stu-id="17754-547">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-548">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-548">Parameters</span></span>

- <span data-ttu-id="17754-549">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-549">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-550">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-550">Return Values</span></span>

- <span data-ttu-id="17754-551">**NX_SUCCESS**: (0x00) Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="17754-551">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="17754-552">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-552">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="17754-553">**NX_INVALID_PARAMETERS**: (0x4D) Error interno; el almacén de certificados probablemente esté dañado.</span><span class="sxs-lookup"><span data-stu-id="17754-553">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-554">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-554">Allowed From</span></span>

<span data-ttu-id="17754-555">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-555">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-556">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-556">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a><span data-ttu-id="17754-557">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-557">See Also</span></span>

- <span data-ttu-id="17754-558">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-558">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-559">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-559">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-560">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-560">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-561">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="17754-561">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="17754-562">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-562">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="17754-563">Agregar un certificado específicamente para servidores TLS mediante un identificador numérico</span><span class="sxs-lookup"><span data-stu-id="17754-563">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-564">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-564">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="17754-565">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-565">Description</span></span>

<span data-ttu-id="17754-566">Este servicio se usa para agregar un certificado al almacén local de una sesión de TLS (consulte nx_secure_tls_local_certificate_add) mediante un identificador numérico en lugar de indexar el almacén con el firmante de X.509 (nombre común) dentro del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-566">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="17754-567">El identificador numérico es independiente del certificado y permite agregar varios certificados como certificados de identidad a un servidor TLS, además de permitir que se agreguen varios certificados con el mismo nombre común al mismo almacén local de la sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-567">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="17754-568">Este mismo servicio se puede usar para los certificados de cliente, pero es raro que un cliente TLS tenga varios certificados de identidad.</span><span class="sxs-lookup"><span data-stu-id="17754-568">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="17754-569">El parámetro cert_id es un número entero positivo distinto de cero asignado por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="17754-569">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="17754-570">El valor real no importa (siempre que sea distinto de cero), pero debe ser único en el almacén de la sesión de TLS proporcionada.</span><span class="sxs-lookup"><span data-stu-id="17754-570">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="17754-571">El valor de cert_id se puede usar para buscar y quitar certificados del almacén local mediante nx_secure_tls_server_certificate_find y nx_secure_tls_server_certificate_remove, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="17754-571">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-572">*Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_local_certificate_add. La API nx_secure_tls_server_certificate_add usa un identificador numérico único para cada certificado y el índice de los servicios de certificados locales basado en el nombre común de X.509. Los servicios de certificados de servidor permiten que existan varios certificados con datos compartidos (especialmente el nombre común) en el mismo almacén local, lo que resulta útil para un servidor con varias identidades.*</span><span class="sxs-lookup"><span data-stu-id="17754-572">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-573">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-573">Parameters</span></span>

- <span data-ttu-id="17754-574">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-574">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-575">**certificate**: puntero a una instancia de certificado X.509 inicializada previamente.</span><span class="sxs-lookup"><span data-stu-id="17754-575">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="17754-576">**cert_id**: número identificador del certificado (positivo, distinto de cero y relativamente único).</span><span class="sxs-lookup"><span data-stu-id="17754-576">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-577">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-577">Return Values</span></span>

- <span data-ttu-id="17754-578">**NX_SUCCESS**: (0x00) Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="17754-578">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="17754-579">**NX_PTR_ERROR**: (0x07) Puntero de certificado o sesión de TLS no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-579">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="17754-580">**NX_SECURE_TLS_CERT_ID_INVALID**: (0x138) El identificador de certificado proporcionado tenía un valor no válido (probablemente 0).</span><span class="sxs-lookup"><span data-stu-id="17754-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="17754-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE**: (0x139) El identificador de certificado proporcionado ya está presente en el almacén local.</span><span class="sxs-lookup"><span data-stu-id="17754-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="17754-582">**NX_INVALID_PARAMETERS**: (0x4D) Error interno; el almacén de certificados probablemente esté dañado.</span><span class="sxs-lookup"><span data-stu-id="17754-582">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-583">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-583">Allowed From</span></span>

<span data-ttu-id="17754-584">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-585">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-585">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-586">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-586">See Also</span></span>

- <span data-ttu-id="17754-587">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-587">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-588">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-588">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="17754-589">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="17754-589">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="17754-590">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="17754-590">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="17754-591">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-591">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="17754-592">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="17754-592">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="17754-593">Buscar un certificado mediante un identificador numérico</span><span class="sxs-lookup"><span data-stu-id="17754-593">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-594">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-594">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="17754-595">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-595">Description</span></span>

<span data-ttu-id="17754-596">Este servicio se usa para buscar un certificado en el almacén local de una sesión de TLS (consulte nx_secure_tls_local_certificate_add) mediante un identificador numérico en lugar de indexar el almacén con el firmante de X.509 (nombre común) dentro del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-596">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="17754-597">El parámetro cert_id es un número entero positivo distinto de cero asignado por la aplicación cuando el certificado se agrega al almacén local de la sesión de TLS mediante nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="17754-597">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-598">*Esta API no se debe usar con la misma sesión de TLS cuando se usa nx_secure_tls_local_certificate_add. La API nx_secure_tls_server_certificate_add usa un identificador numérico único para cada certificado y el índice de los servicios de certificados locales basado en el nombre común de X.509. Los servicios de certificados de servidor permiten que existan varios certificados con datos compartidos (especialmente el nombre común) en el mismo almacén local, lo que resulta útil para un servidor con varias identidades.*</span><span class="sxs-lookup"><span data-stu-id="17754-598">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-599">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-599">Parameters</span></span>

- <span data-ttu-id="17754-600">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-600">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-601">**certificate**: puntero a un puntero de certificado X.509 para devolver una referencia al certificado encontrado.</span><span class="sxs-lookup"><span data-stu-id="17754-601">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="17754-602">**cert_id**: valor del identificador de certificado (positivo y distinto de cero).</span><span class="sxs-lookup"><span data-stu-id="17754-602">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-603">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-603">Return Values</span></span>

- <span data-ttu-id="17754-604">**NX_SUCCESS**: (0x00) Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="17754-604">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="17754-605">**NX_PTR_ERROR**: (0x07) Puntero de certificado o sesión de TLS no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-605">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="17754-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) El identificador de certificado proporcionado no coincidía con ninguno del almacén local de la sesión de TLS proporcionada.</span><span class="sxs-lookup"><span data-stu-id="17754-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-607">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-607">Allowed From</span></span>

<span data-ttu-id="17754-608">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-608">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-609">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-609">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-610">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-610">See Also</span></span>

- <span data-ttu-id="17754-611">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-611">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-612">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-612">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="17754-613">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="17754-613">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="17754-614">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-614">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="17754-615">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-615">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="17754-616">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-616">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="17754-617">Quitar un certificado de servidor local mediante un identificador numérico</span><span class="sxs-lookup"><span data-stu-id="17754-617">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-618">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-618">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="17754-619">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-619">Description</span></span>

<span data-ttu-id="17754-620">Este servicio se usa para quitar un certificado del almacén local de una sesión de TLS (consulte nx_secure_tls_local_certificate_add) mediante un identificador numérico en lugar de indexar el almacén con el firmante de X.509 (nombre común) dentro del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-620">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="17754-621">El parámetro cert_id es un número entero positivo distinto de cero asignado por la aplicación cuando el certificado se agrega al almacén local de la sesión de TLS mediante nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="17754-621">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-622">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-622">Parameters</span></span>

- <span data-ttu-id="17754-623">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-623">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-624">**cert_id**: valor del identificador de certificado (positivo y distinto de cero).</span><span class="sxs-lookup"><span data-stu-id="17754-624">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-625">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-625">Return Values</span></span>

- <span data-ttu-id="17754-626">**NX_SUCCESS**: (0x00) Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="17754-626">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="17754-627">**NX_PTR_ERROR**: (0x07) Sesión de TLS no válida.</span><span class="sxs-lookup"><span data-stu-id="17754-627">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="17754-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) El identificador de certificado proporcionado no coincidía con ninguno del almacén local de la sesión de TLS proporcionada.</span><span class="sxs-lookup"><span data-stu-id="17754-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-629">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-629">Allowed From</span></span>

<span data-ttu-id="17754-630">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-630">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-631">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-631">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-632">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-632">See Also</span></span>

- <span data-ttu-id="17754-633">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-633">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-634">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-634">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="17754-635">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="17754-635">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="17754-636">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-636">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="17754-637">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="17754-637">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="17754-638">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="17754-638">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="17754-639">Obtener el valor y el nivel de la alerta de TLS enviados por el host remoto</span><span class="sxs-lookup"><span data-stu-id="17754-639">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-640">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-640">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="17754-641">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-641">Description</span></span>

<span data-ttu-id="17754-642">Este servicio se usa para recuperar el valor y el nivel de la alerta de TLS cuando el host remoto envía una alerta en respuesta a algún problema o error.</span><span class="sxs-lookup"><span data-stu-id="17754-642">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="17754-643">Los valores de los parámetros alert_level y alert_value solo son válidos si se llama a esta función inmediatamente después de una llamada a la API de TLS que haya devuelto el estado NX_SECURE_TLS_ALERT_RECEIVED (0x114), que indica que se ha recibido una alerta del host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-643">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="17754-644">Tenga en cuenta que si el host local de TLS envía una alerta, los códigos de error devueltos son mucho más descriptivos del error real que la propia alerta de TLS, ya que los valores de la alerta de TLS se dejan ambiguos intencionadamente para evitar determinados tipos de ataque (por ejemplo, un ataque de tipo "padding oracle" o similar).</span><span class="sxs-lookup"><span data-stu-id="17754-644">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="17754-645">El nivel de alerta solo toma uno de estos dos valores: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) o NX_SECURE_TLS_ALERT_LEVEL_FATAL (0X2).</span><span class="sxs-lookup"><span data-stu-id="17754-645">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="17754-646">En general, solo se le asignará un nivel de "advertencia" a la alerta CloseNotify (que se usa para indicar una finalización correcta de una sesión de TLS), aunque algunas situaciones de configuración de extensiones también se pueden considerar advertencias.</span><span class="sxs-lookup"><span data-stu-id="17754-646">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="17754-647">La gran mayoría de las alertas serán "graves", lo que indica un posible error de seguridad y provocarán un cierre inmediato de la conexión TLS (protocolo de enlace o sesión).</span><span class="sxs-lookup"><span data-stu-id="17754-647">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="17754-648">Los valores de las alertas de TLS se definen en los documentos RFC de TLS; esta es la lista del documento RFC 5246 (TLS v1.2) como referencia:</span><span class="sxs-lookup"><span data-stu-id="17754-648">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="17754-649">Nombre de la alerta</span><span class="sxs-lookup"><span data-stu-id="17754-649">Alert Name</span></span>                     | <span data-ttu-id="17754-650">Value</span><span class="sxs-lookup"><span data-stu-id="17754-650">Value</span></span> | <span data-ttu-id="17754-651">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-651">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="17754-652">close_notify</span><span class="sxs-lookup"><span data-stu-id="17754-652">close_notify</span></span>                  | <span data-ttu-id="17754-653">0</span><span class="sxs-lookup"><span data-stu-id="17754-653">0</span></span>     | <span data-ttu-id="17754-654">Sin errores, indica que la finalización de la sesión se ha completado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-654">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="17754-655">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="17754-655">unexpected_message</span></span>            | <span data-ttu-id="17754-656">10</span><span class="sxs-lookup"><span data-stu-id="17754-656">10</span></span>    | <span data-ttu-id="17754-657">TLS ha recibido un mensaje inesperado o desordenado.</span><span class="sxs-lookup"><span data-stu-id="17754-657">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="17754-658">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="17754-658">bad_record_mac</span></span>               | <span data-ttu-id="17754-659">20</span><span class="sxs-lookup"><span data-stu-id="17754-659">20</span></span>    | <span data-ttu-id="17754-660">Error en el descifrado o la comprobación de MAC.</span><span class="sxs-lookup"><span data-stu-id="17754-660">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="17754-661">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="17754-661">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="17754-662">21</span><span class="sxs-lookup"><span data-stu-id="17754-662">21</span></span>    | <span data-ttu-id="17754-663">**EN DESUSO**: error de descifrado (en desuso debido a los ataques de tipo "padding oracle").</span><span class="sxs-lookup"><span data-stu-id="17754-663">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="17754-664">record_overflow</span><span class="sxs-lookup"><span data-stu-id="17754-664">record_overflow</span></span>               | <span data-ttu-id="17754-665">22</span><span class="sxs-lookup"><span data-stu-id="17754-665">22</span></span>    | <span data-ttu-id="17754-666">Se ha recibido un registro que es mayor que el tamaño máximo de registro de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-666">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="17754-667">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="17754-667">decompression_failure</span></span>         | <span data-ttu-id="17754-668">30</span><span class="sxs-lookup"><span data-stu-id="17754-668">30</span></span>    | <span data-ttu-id="17754-669">Se encontró un problema en la compresión y descompresión de un registro de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-669">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="17754-670">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="17754-670">handshake_failure</span></span>             | <span data-ttu-id="17754-671">40</span><span class="sxs-lookup"><span data-stu-id="17754-671">40</span></span>    | <span data-ttu-id="17754-672">Se produjo un error de protocolo de enlace no especificado que no está incluido en otras alertas.</span><span class="sxs-lookup"><span data-stu-id="17754-672">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="17754-673">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="17754-673">no_certificate_RESERVED</span></span>      | <span data-ttu-id="17754-674">41</span><span class="sxs-lookup"><span data-stu-id="17754-674">41</span></span>    | <span data-ttu-id="17754-675">**EN DESUSO** en TLS (solo SSL).</span><span class="sxs-lookup"><span data-stu-id="17754-675">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="17754-676">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="17754-676">bad_certificate</span></span>               | <span data-ttu-id="17754-677">42</span><span class="sxs-lookup"><span data-stu-id="17754-677">42</span></span>    | <span data-ttu-id="17754-678">Un certificado recibido contenía un formato o firmas no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-678">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="17754-679">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="17754-679">unsupported_certificate</span></span>       | <span data-ttu-id="17754-680">43</span><span class="sxs-lookup"><span data-stu-id="17754-680">43</span></span>    | <span data-ttu-id="17754-681">Se ha recibido un certificado que era de un tipo no válido (por ejemplo, un certificado solo de firma utilizado para la autenticación del servidor TLS).</span><span class="sxs-lookup"><span data-stu-id="17754-681">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="17754-682">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="17754-682">certificate_revoked</span></span>           | <span data-ttu-id="17754-683">44</span><span class="sxs-lookup"><span data-stu-id="17754-683">44</span></span>    | <span data-ttu-id="17754-684">El estado del certificado (proporcionado por una CRL u OCSP) se indicó como "revocado".</span><span class="sxs-lookup"><span data-stu-id="17754-684">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="17754-685">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="17754-685">certificate_expired</span></span>           | <span data-ttu-id="17754-686">45</span><span class="sxs-lookup"><span data-stu-id="17754-686">45</span></span>    | <span data-ttu-id="17754-687">El certificado recibido estaba fuera de su intervalo de fechas válido (aún no es válido o ha expirado).</span><span class="sxs-lookup"><span data-stu-id="17754-687">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="17754-688">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="17754-688">certificate_unknown</span></span>           | <span data-ttu-id="17754-689">46</span><span class="sxs-lookup"><span data-stu-id="17754-689">46</span></span>    | <span data-ttu-id="17754-690">Se encontró algún problema de certificado desconocido que no estaba incluido en otras alertas.</span><span class="sxs-lookup"><span data-stu-id="17754-690">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="17754-691">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="17754-691">illegal_parameter</span></span>             | <span data-ttu-id="17754-692">47</span><span class="sxs-lookup"><span data-stu-id="17754-692">47</span></span>    | <span data-ttu-id="17754-693">Algunos valores de configuración o negociados en el protocolo de enlace de TLS no eran válidos o están fuera del intervalo.</span><span class="sxs-lookup"><span data-stu-id="17754-693">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="17754-694">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="17754-694">unknown_ca</span></span>                    | <span data-ttu-id="17754-695">48</span><span class="sxs-lookup"><span data-stu-id="17754-695">48</span></span>    | <span data-ttu-id="17754-696">No se pudo realizar un seguimiento del certificado de identidad recibido mediante una cadena de certificados a un certificado de CA raíz de confianza.</span><span class="sxs-lookup"><span data-stu-id="17754-696">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="17754-697">access_denied</span><span class="sxs-lookup"><span data-stu-id="17754-697">access_denied</span></span>                 | <span data-ttu-id="17754-698">49</span><span class="sxs-lookup"><span data-stu-id="17754-698">49</span></span>    | <span data-ttu-id="17754-699">Indica que se recibió un certificado válido, pero el control de acceso de la aplicación indicó que el certificado no era válido para los recursos solicitados.</span><span class="sxs-lookup"><span data-stu-id="17754-699">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="17754-700">decode_error</span><span class="sxs-lookup"><span data-stu-id="17754-700">decode_error</span></span>                  | <span data-ttu-id="17754-701">50</span><span class="sxs-lookup"><span data-stu-id="17754-701">50</span></span>    | <span data-ttu-id="17754-702">Algunos campos o valores de un mensaje del protocolo de enlace o del encabezado TLS estaban fuera del intervalo o no eran válidos, lo que provoca un error en la descodificación de un registro de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-702">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="17754-703">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="17754-703">decrypt_error</span></span>                 | <span data-ttu-id="17754-704">51</span><span class="sxs-lookup"><span data-stu-id="17754-704">51</span></span>    | <span data-ttu-id="17754-705">No se pudo comprobar la firma o el código hash del mensaje de finalización durante el protocolo de enlace de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-705">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="17754-706">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="17754-706">export_restriction_RESERVED</span></span>  | <span data-ttu-id="17754-707">60</span><span class="sxs-lookup"><span data-stu-id="17754-707">60</span></span>    | <span data-ttu-id="17754-708">EN DESUSO en TLS v1.2.</span><span class="sxs-lookup"><span data-stu-id="17754-708">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="17754-709">protocol_version</span><span class="sxs-lookup"><span data-stu-id="17754-709">protocol_version</span></span>              | <span data-ttu-id="17754-710">70</span><span class="sxs-lookup"><span data-stu-id="17754-710">70</span></span>    | <span data-ttu-id="17754-711">Se reconoce la versión del protocolo TLS negociada durante el protocolo de enlace pero no se admite (por ejemplo, se presentó TLS v1.0 pero no se habilitó).</span><span class="sxs-lookup"><span data-stu-id="17754-711">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="17754-712">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="17754-712">insufficient_security</span></span>         | <span data-ttu-id="17754-713">71</span><span class="sxs-lookup"><span data-stu-id="17754-713">71</span></span>    | <span data-ttu-id="17754-714">Se envía cuando se produce un error en el protocolo de enlace debido a la falta de cifrados seguros (por ejemplo, el tamaño de la clave es demasiado pequeño para los requisitos de la aplicación).</span><span class="sxs-lookup"><span data-stu-id="17754-714">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="17754-715">internal_error</span><span class="sxs-lookup"><span data-stu-id="17754-715">internal_error</span></span>                | <span data-ttu-id="17754-716">80</span><span class="sxs-lookup"><span data-stu-id="17754-716">80</span></span>    | <span data-ttu-id="17754-717">Algunos errores que no son de TLS (por ejemplo, problemas de asignación de memoria o problemas de la aplicación) han interrumpido la sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-717">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="17754-718">user_canceled</span><span class="sxs-lookup"><span data-stu-id="17754-718">user_canceled</span></span>                 | <span data-ttu-id="17754-719">90</span><span class="sxs-lookup"><span data-stu-id="17754-719">90</span></span>    | <span data-ttu-id="17754-720">Se devuelve si un usuario o una aplicación cancelan la sesión de TLS antes de que se complete el protocolo de enlace (similar a CloseNotify).</span><span class="sxs-lookup"><span data-stu-id="17754-720">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="17754-721">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="17754-721">no_renegotiation</span></span>              | <span data-ttu-id="17754-722">100</span><span class="sxs-lookup"><span data-stu-id="17754-722">100</span></span>   | <span data-ttu-id="17754-723">Indica que el host remoto no está dispuesto a realizar protocolos de enlace de renegociación de TLS en respuesta a una solicitud de renegociación.</span><span class="sxs-lookup"><span data-stu-id="17754-723">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="17754-724">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="17754-724">unsupported_extension</span></span>         | <span data-ttu-id="17754-725">110</span><span class="sxs-lookup"><span data-stu-id="17754-725">110</span></span>   | <span data-ttu-id="17754-726">Se envía si un cliente TLS recibe un mensaje ServerHello que contiene extensiones no solicitadas explícitamente en el mensaje ClientHello inicial (lo que indica que el servidor tiene un problema).</span><span class="sxs-lookup"><span data-stu-id="17754-726">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="17754-727">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-727">Parameters</span></span>

- <span data-ttu-id="17754-728">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-728">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-729">**alert_level**: devuelve el nivel de la alerta recibida (advertencia o grave).</span><span class="sxs-lookup"><span data-stu-id="17754-729">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="17754-730">**alert_value**: devuelve el valor de la alerta recibida (consulte la tabla).</span><span class="sxs-lookup"><span data-stu-id="17754-730">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-731">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-731">Return Values</span></span>

- <span data-ttu-id="17754-732">**NX_SUCCESS**: (0x00) Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="17754-732">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="17754-733">**NX_PTR_ERROR**: (0x07) Sesión de TLS no válida.</span><span class="sxs-lookup"><span data-stu-id="17754-733">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-734">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-734">Allowed From</span></span>

<span data-ttu-id="17754-735">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-736">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-736">Example</span></span>

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a><span data-ttu-id="17754-737">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-737">See Also</span></span>

- <span data-ttu-id="17754-738">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-738">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-739">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-739">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-740">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-740">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="17754-741">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-741">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="17754-742">Configurar una devolución de llamada para que TLS la use para la validación de certificados adicional</span><span class="sxs-lookup"><span data-stu-id="17754-742">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-743">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-743">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="17754-744">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-744">Description</span></span>

<span data-ttu-id="17754-745">Este servicio asigna un puntero de función a una sesión de TLS a la que TLS invocará cuando se reciba un certificado desde un host remoto, lo que permite que la aplicación realice comprobaciones de validación, como la validación de DNS, la revocación de certificados y la aplicación de directivas de certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-745">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="17754-746">TLS de NetX Secure realizará una validación básica de la ruta X.509 en el certificado antes de invocar a la devolución de llamada para garantizar que se pueda realizar un seguimiento del certificado en un certificado del almacén de certificados de confianza de TLS, pero el resto de la validación se controlará mediante esta devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="17754-746">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="17754-747">La devolución de llamada proporciona el puntero de la sesión de TLS y un puntero al certificado de identidad del host remoto (la hoja de la cadena de certificados).</span><span class="sxs-lookup"><span data-stu-id="17754-747">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="17754-748">La devolución de llamada debe devolver NX_SUCCESS si toda la validación es correcta; en caso contrario, debe devolver un código de error que indique el error de validación.</span><span class="sxs-lookup"><span data-stu-id="17754-748">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="17754-749">Cualquier valor distinto de NX_SUCCESS hará que el protocolo de enlace de TLS se anule inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="17754-749">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-750">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-750">Parameters</span></span>

- <span data-ttu-id="17754-751">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-751">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-752">**func_ptr**: puntero a la función de devolución de llamada de validación del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-752">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-753">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-753">Return Values</span></span>

- <span data-ttu-id="17754-754">**NX_SUCCESS**: (0x00) Asignación correcta del puntero de función.</span><span class="sxs-lookup"><span data-stu-id="17754-754">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="17754-755">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-755">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-756">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-756">Allowed From</span></span>

<span data-ttu-id="17754-757">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-757">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-758">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-758">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a><span data-ttu-id="17754-759">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-759">See Also</span></span>

- <span data-ttu-id="17754-760">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-760">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-761">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="17754-761">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="17754-762">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="17754-762">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="17754-763">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-763">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="17754-764">Configurar una devolución de llamada para que TLS la invoque al principio de un protocolo de enlace de cliente TLS</span><span class="sxs-lookup"><span data-stu-id="17754-764">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-765">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-765">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="17754-766">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-766">Description</span></span>

<span data-ttu-id="17754-767">Este servicio asigna un puntero de función a una sesión de TLS a la que TLS invocará cuando un protocolo de enlace del cliente TLS haya recibido un mensaje ServerHelloDone.</span><span class="sxs-lookup"><span data-stu-id="17754-767">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="17754-768">La función de devolución de llamada permite a una aplicación procesar las extensiones de TLS del mensaje ServerHello recibido que requieran la toma de decisiones o una entrada.</span><span class="sxs-lookup"><span data-stu-id="17754-768">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="17754-769">La devolución de llamada se ejecuta con el bloque de control de la sesión de TLS de invocación y una matriz de objetos NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="17754-769">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="17754-770">La matriz de objetos de extensión está pensada para pasarse a una función auxiliar que buscará y analizará una extensión específica.</span><span class="sxs-lookup"><span data-stu-id="17754-770">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="17754-771">Actualmente, no se admiten extensiones específicas en NetX Secure que requieran una entrada del cliente TLS, pero la devolución de llamada está disponible para que los diseñadores de aplicaciones puedan administrar extensiones personalizadas o nuevas que puedan estar disponibles.</span><span class="sxs-lookup"><span data-stu-id="17754-771">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="17754-772">Para obtener una función auxiliar de ejemplo que analice las extensiones de TLS proporcionadas en los mensajes de saludo, consulte *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="17754-772">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="17754-773">La devolución de llamada del cliente también se puede usar para seleccionar el certificado de identidad activo mediante *nx_secure_tls_active_certificate_set* para el cliente TLS en caso de que el servidor remoto haya solicitado un certificado y proporcione información para permitir que el cliente TLS seleccione un certificado específico.</span><span class="sxs-lookup"><span data-stu-id="17754-773">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="17754-774">Consulte la referencia de nx_secure_tls_active_certificate_set para más información.</span><span class="sxs-lookup"><span data-stu-id="17754-774">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-775">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-775">Parameters</span></span>

- <span data-ttu-id="17754-776">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-776">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-777">**func_ptr**: puntero a la función de devolución de llamada del cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-777">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-778">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-778">Return Values</span></span>

- <span data-ttu-id="17754-779">**NX_SUCCESS**: (0x00) Asignación correcta del puntero de función.</span><span class="sxs-lookup"><span data-stu-id="17754-779">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="17754-780">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-780">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-781">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-781">Allowed From</span></span>

<span data-ttu-id="17754-782">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-782">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-783">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-783">Example</span></span>

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="17754-784">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-784">See Also</span></span>

- <span data-ttu-id="17754-785">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-785">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-786">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-786">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="17754-787">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="17754-787">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="17754-788">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="17754-788">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="17754-789">Habilitar la comprobación X.509 de cliente y asignar espacio para los certificados de cliente</span><span class="sxs-lookup"><span data-stu-id="17754-789">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-790">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-790">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="17754-791">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-791">Description</span></span>

<span data-ttu-id="17754-792">Este servicio habilita la autenticación de cliente X.509 opcional para una instancia de servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-792">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="17754-793">También asigna el espacio necesario para procesar las cadenas de certificados entrantes del host del cliente remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-793">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="17754-794">Los certificados proporcionados por el cliente remoto se comprobarán con los certificados de confianza de la instancia de servidor TLS asignados con el servicio *nx_secure_tls_trusted_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="17754-794">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="17754-795">En el modo de cliente TLS se requiere la asignación de certificados remotos y en su lugar se debe usar el servicio *nx_secure_tls_remote_certificate_buffer_allocate*.</span><span class="sxs-lookup"><span data-stu-id="17754-795">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="17754-796">La habilitación de la autenticación de cliente X.509 en una instancia de cliente TLS no tendrá ningún efecto.</span><span class="sxs-lookup"><span data-stu-id="17754-796">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="17754-797">El parámetro *certificate_buffer* apunta al espacio asignado para almacenar los certificados remotos entrantes y los bloques de control necesarios para dichos certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-797">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="17754-798">El búfer se dividirá por el número de certificados (*certs_number*) con una parte igual para cada certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-798">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="17754-799">El parámetro *buffer_size* indica el tamaño del búfer.</span><span class="sxs-lookup"><span data-stu-id="17754-799">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="17754-800">Se puede determinar el espacio necesario con la siguiente fórmula:</span><span class="sxs-lookup"><span data-stu-id="17754-800">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="17754-801">Los certificados típicos con claves RSA de 2048 bits y SHA-256 para las firmas están en el intervalo de 1000 a 2000 bytes.</span><span class="sxs-lookup"><span data-stu-id="17754-801">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="17754-802">El búfer debe ser lo suficientemente grande como para contener, como mínimo, ese tamaño para cada certificado, pero, en función de los certificados del host remoto, puede ser considerablemente menor o mayor.</span><span class="sxs-lookup"><span data-stu-id="17754-802">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="17754-803">Tenga en cuenta que si el búfer es demasiado pequeño para contener el certificado entrante, el protocolo de enlace de TLS finalizará con un error.</span><span class="sxs-lookup"><span data-stu-id="17754-803">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-804">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-804">Parameters</span></span>

- <span data-ttu-id="17754-805">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-805">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-806">**certs_number**: número de certificados que se van a asignar desde el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="17754-806">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="17754-807">**certificate_buffer**: puntero a un búfer para contener los certificados recibidos de un host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-807">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="17754-808">**buffer_size**: tamaño del búfer de certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-808">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-809">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-809">Return Values</span></span>

- <span data-ttu-id="17754-810">**NX_SUCCESS**: (0x00) Certificado asignado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-810">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="17754-811">**NX_PTR_ERROR**: (0x07) Sesión de TLS o puntero de búfer no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-811">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="17754-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE**: (0x12D) El búfer proporcionado era demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="17754-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="17754-813">**NX_INVALID_PARAMETERS**: (0x4D) El búfer era demasiado pequeño para contener el número deseado de certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-813">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-814">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-814">Allowed From</span></span>

<span data-ttu-id="17754-815">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-815">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-816">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-816">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-817">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-817">See Also</span></span>

- <span data-ttu-id="17754-818">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-818">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-819">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-819">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-820">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-820">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="17754-821">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="17754-821">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="17754-822">Deshabilitar la autenticación de certificados de cliente para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-822">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-823">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-823">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="17754-824">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-824">Description</span></span>

<span data-ttu-id="17754-825">Este servicio deshabilita la autenticación de certificados de cliente para una sesión de TLS específica.</span><span class="sxs-lookup"><span data-stu-id="17754-825">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="17754-826">Consulte nx_secure_tls_session_client_verify_enable para más información.</span><span class="sxs-lookup"><span data-stu-id="17754-826">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-827">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-827">Parameters</span></span>

- <span data-ttu-id="17754-828">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-828">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-829">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-829">Return Values</span></span>

- <span data-ttu-id="17754-830">**NX_SUCCESS**: (0x00) Cambio de estado correcto.</span><span class="sxs-lookup"><span data-stu-id="17754-830">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="17754-831">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-831">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-832">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-832">Allowed From</span></span>

<span data-ttu-id="17754-833">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-834">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-834">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-835">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-835">See Also</span></span>

- <span data-ttu-id="17754-836">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="17754-836">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="17754-837">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-837">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-838">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-838">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="17754-839">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="17754-839">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="17754-840">Habilitar la autenticación de certificados de cliente para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-840">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-841">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-841">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="17754-842">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-842">Description</span></span>

<span data-ttu-id="17754-843">Este servicio habilita la autenticación de certificados de cliente para una sesión de TLS específica.</span><span class="sxs-lookup"><span data-stu-id="17754-843">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="17754-844">La habilitación de la autenticación de certificados de cliente para una instancia de servidor TLS hará que el servidor TLS solicite un certificado desde cualquier cliente TLS remoto durante el protocolo de enlace de TLS inicial.</span><span class="sxs-lookup"><span data-stu-id="17754-844">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="17754-845">El certificado recibido del cliente TLS remoto está acompañado de un mensaje CertificateVerify, que el servidor TLS utiliza para comprobar que el cliente es el propietario del certificado (tiene acceso a la clave privada asociada a ese certificado).</span><span class="sxs-lookup"><span data-stu-id="17754-845">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="17754-846">Si se puede comprobar el certificado proporcionado y realizar un seguimiento de él en un certificado del almacén de certificados de confianza del servidor TLS mediante una cadena de certificados X.509, el cliente TLS remoto se autentica y el protocolo de enlace continúa.</span><span class="sxs-lookup"><span data-stu-id="17754-846">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="17754-847">En caso de que se produzcan errores al procesar el certificado o el mensaje CertificateVerify, el protocolo de enlace de TLS finalizará con un error.</span><span class="sxs-lookup"><span data-stu-id="17754-847">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="17754-848">*El servidor TLS debe tener al menos un certificado en su almacén de confianza agregado con nx_secure_tls_trusted_certificate_add o siempre se producirá un error de autenticación.*</span><span class="sxs-lookup"><span data-stu-id="17754-848">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-849">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-849">Parameters</span></span>

- <span data-ttu-id="17754-850">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-850">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-851">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-851">Return Values</span></span>

- <span data-ttu-id="17754-852">**NX_SUCCESS**: (0x00) Cambio de estado correcto.</span><span class="sxs-lookup"><span data-stu-id="17754-852">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="17754-853">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-853">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-854">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-854">Allowed From</span></span>

<span data-ttu-id="17754-855">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-855">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-856">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-856">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-857">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-857">See Also</span></span>

- <span data-ttu-id="17754-858">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="17754-858">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="17754-859">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-859">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-860">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-860">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-861">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-861">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="17754-862">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-862">nx_secure_tls_session_create</span></span>

<span data-ttu-id="17754-863">Crear una sesión de TLS de NetX Secure para comunicaciones seguras</span><span class="sxs-lookup"><span data-stu-id="17754-863">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-864">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-864">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="17754-865">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-865">Description</span></span>

<span data-ttu-id="17754-866">Este servicio inicializa una instancia de la estructura NX_SECURE_TLS_SESSION para su uso en el establecimiento de comunicaciones TLS seguras mediante una conexión de red.</span><span class="sxs-lookup"><span data-stu-id="17754-866">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="17754-867">El método toma un objeto NX_SECURE_TLS_CRYPTO que se rellena con los métodos criptográficos disponibles que se van a usar para TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-867">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="17754-868">*encryption_metadata_area* apunta a un búfer asignado para su uso por TLS para los "metadatos" utilizados por los métodos criptográficos de la tabla NX_SECURE_TLS_CRYPTO para los cálculos.</span><span class="sxs-lookup"><span data-stu-id="17754-868">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="17754-869">El tamaño de la tabla se puede determinar mediante el servicio nx_secure_tls_metadata_size_calculate.</span><span class="sxs-lookup"><span data-stu-id="17754-869">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="17754-870">Consulte la sección "Criptografía en TLS de NetX Secure" en el Capítulo 3 para más detalles.</span><span class="sxs-lookup"><span data-stu-id="17754-870">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-871">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-871">Parameters</span></span>

- <span data-ttu-id="17754-872">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-872">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-873">**cipher_table**: puntero a los métodos criptográficos de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-873">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="17754-874">**encryption_metadata_area**: puntero al espacio para los metadatos de criptografía.</span><span class="sxs-lookup"><span data-stu-id="17754-874">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="17754-875">**encryption_metadata_size**: tamaño del búfer de metadatos.</span><span class="sxs-lookup"><span data-stu-id="17754-875">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-876">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-876">Return Values</span></span>

- <span data-ttu-id="17754-877">**NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-877">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="17754-878">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-878">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="17754-879">**NX_INVALID_PARAMETERS**: (0x4D) El búfer de metadatos era demasiado pequeño para los métodos especificados.</span><span class="sxs-lookup"><span data-stu-id="17754-879">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="17754-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER**: (0x106) No se proporcionó en la tabla de cifrado un método de cifrado necesario para la versión habilitada de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-881">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-881">Allowed From</span></span>

<span data-ttu-id="17754-882">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-882">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-883">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-883">Example</span></span>

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-884">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-884">See Also</span></span>

- <span data-ttu-id="17754-885">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-885">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-886">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="17754-886">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="17754-887">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-887">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-888">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-888">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-889">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="17754-889">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="17754-890">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-890">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-891">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-891">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-892">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-892">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="17754-893">Criptografía en TLS de NetX Secure en el Capítulo 3</span><span class="sxs-lookup"><span data-stu-id="17754-893">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="17754-894">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-894">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="17754-895">Eliminar una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-895">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-896">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-896">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="17754-897">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-897">Description</span></span>

<span data-ttu-id="17754-898">Este servicio elimina una sesión de TLS representada por una instancia de la estructura NX_SECURE_TLS_SESSION y libera todos los recursos del sistema que pertenecen a esa instancia de sesión.</span><span class="sxs-lookup"><span data-stu-id="17754-898">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-899">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-899">Parameters</span></span>

- <span data-ttu-id="17754-900">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-900">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-901">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-901">Return Values</span></span>

- <span data-ttu-id="17754-902">**NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-902">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="17754-903">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-903">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-904">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-904">Allowed From</span></span>

<span data-ttu-id="17754-905">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-906">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-906">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-907">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-907">See Also</span></span>

- <span data-ttu-id="17754-908">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-908">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-909">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-909">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-910">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-910">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-911">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="17754-911">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="17754-912">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-912">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-913">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-913">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-914">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-914">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="17754-915">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="17754-915">nx_secure_tls_session_end</span></span>

<span data-ttu-id="17754-916">Finalizar una sesión activa de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-916">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-917">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-917">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="17754-918">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-918">Description</span></span>

<span data-ttu-id="17754-919">Este servicio finaliza una sesión de TLS representada por una instancia de la estructura NX_SECURE_TLS_SESSION mediante el envío de un mensaje CloseNotify de TLS al host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-919">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="17754-920">Después, el servicio espera a que el host remoto responda con su propio mensaje CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="17754-920">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="17754-921">Si el host remoto no envía un mensaje CloseNotify, TLS lo considera un error y una posible infracción de seguridad, por lo que es importante comprobar el valor devuelto para una conexión segura.</span><span class="sxs-lookup"><span data-stu-id="17754-921">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="17754-922">El parámetro **wait_option** se puede utilizar para controlar cuánto tiempo debe esperar el servicio a la respuesta antes de devolver el control al subproceso que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="17754-922">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-923">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-923">Parameters</span></span>

- <span data-ttu-id="17754-924">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-924">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-925">**wait_option**: indica cuánto tiempo debe esperar el servicio la respuesta del host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-925">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-926">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-926">Return Values</span></span>

- <span data-ttu-id="17754-927">**NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-927">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="17754-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE**: (0x113) No se ha recibido una respuesta del host remoto antes de que se agotara el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="17754-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="17754-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**: (0x111) No se pudo asignar un paquete para enviar el mensaje CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="17754-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="17754-930">**NX_SECURE_TLS_TCP_SEND_FAILED**: (0x109) No se pudo enviar el mensaje CloseNotify mediante el socket TCP.</span><span class="sxs-lookup"><span data-stu-id="17754-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="17754-931">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-931">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-932">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-932">Allowed From</span></span>

<span data-ttu-id="17754-933">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-933">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-934">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-934">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-935">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-935">See Also</span></span>

- <span data-ttu-id="17754-936">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-936">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-937">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-937">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-938">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-938">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-939">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-939">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="17754-940">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-940">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-941">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-941">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-942">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-942">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="17754-943">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="17754-943">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="17754-944">Establecer el búfer de reensamblado de paquetes para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-944">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-945">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-945">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="17754-946">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-946">Description</span></span>

<span data-ttu-id="17754-947">Este servicio asocia un búfer de reensamblado de paquetes a una sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-947">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="17754-948">Para descifrar y analizar los registros de TLS entrantes, los datos de cada registro se deben ensamblar desde los paquetes TCP subyacentes.</span><span class="sxs-lookup"><span data-stu-id="17754-948">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="17754-949">Los registros de TLS pueden tener un tamaño máximo de 16 KB (aunque normalmente son mucho más pequeños), por lo que puede que no quepan en un único paquete TCP.</span><span class="sxs-lookup"><span data-stu-id="17754-949">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="17754-950">Si sabe que el tamaño del mensaje entrante será menor que el límite del registro de TLS de 16 KB, el tamaño del búfer puede ser menor, pero para controlar datos entrantes desconocidos, el búfer debe ser lo más grande posible.</span><span class="sxs-lookup"><span data-stu-id="17754-950">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="17754-951">Si un registro entrante es mayor que el búfer proporcionado, la sesión de TLS finalizará con un error.</span><span class="sxs-lookup"><span data-stu-id="17754-951">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-952">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-952">Parameters</span></span>

- <span data-ttu-id="17754-953">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-953">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-954">**buffer_ptr**: puntero al búfer que TLS utilizará para el reensamblado de paquetes.</span><span class="sxs-lookup"><span data-stu-id="17754-954">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="17754-955">**buffer_size**: tamaño del búfer proporcionado en bytes.</span><span class="sxs-lookup"><span data-stu-id="17754-955">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-956">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-956">Return Values</span></span>

- <span data-ttu-id="17754-957">**NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-957">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="17754-958">**NX_INVALID_PARAMETERS**: (0x4D) Búfer o puntero de sesión de TLS no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-958">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="17754-959">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-959">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-960">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-960">Allowed From</span></span>

<span data-ttu-id="17754-961">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-961">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-962">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-962">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-963">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-963">See Also</span></span>

- <span data-ttu-id="17754-964">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-964">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-965">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-965">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-966">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-966">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-967">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-967">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="17754-968">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-968">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-969">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-969">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-970">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-970">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="17754-971">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="17754-971">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="17754-972">Invalidar la versión predeterminada del protocolo TLS para una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-972">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-973">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-973">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="17754-974">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-974">Description</span></span>

<span data-ttu-id="17754-975">Este servicio invalida la versión predeterminada (más reciente) del protocolo TLS usada por una sesión determinada.</span><span class="sxs-lookup"><span data-stu-id="17754-975">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="17754-976">Esto permite a TLS de NetX Secure usar una versión anterior de TLS para una sesión de TLS específica sin deshabilitar las versiones más recientes de TLS en tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="17754-976">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="17754-977">Esto puede resultar útil en las aplicaciones que pueden necesitar comunicarse con un host más antiguo que no admita la versión más reciente de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-977">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-978">*A partir de la versión 5.11 SP3, TLS de NetX Secure es compatible con RFC 7507 (consulte la nota siguiente) y cualquier invalidación de una versión anterior con esta API producirá el envío de un SCSV de reserva en el mensaje ClientHello. Si el servidor admite una versión más reciente de TLS y el SCSV de reserva está incluido en el mensaje ClientHello, ese servidor anulará el protocolo de enlace de TLS con una alerta de "reserva inapropiada". El SCSV solo se envía cuando la invalidación de versión es una versión anterior de TLS que está habilitada (por ejemplo, si invalida la versión a TLS 1.2, no se enviará un SCSV).*</span><span class="sxs-lookup"><span data-stu-id="17754-978">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="17754-979">Los valores válidos para el parámetro protocol_version son las siguientes macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 y NX_SECURE_TLS_VERSION_TLS_1_2.</span><span class="sxs-lookup"><span data-stu-id="17754-979">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="17754-980">Las macros NX_SECURE_TLS_DISABLE_TLS_1_1 y NX_SECURE_TLS_ENABLE_TLS_1_0 se pueden usar para controlar las versiones de TLS que se han compilado en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="17754-980">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="17754-981">La versión 1.2 de TLS está siempre habilitada.</span><span class="sxs-lookup"><span data-stu-id="17754-981">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="17754-982">Tenga en cuenta que si el host remoto no admite la versión suministrada, se producirá un error en la conexión; TLS de NetX Secure solo negociará la versión de invalidación proporcionada.</span><span class="sxs-lookup"><span data-stu-id="17754-982">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-983">RFC 7507: SCSV de reserva de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-983">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="17754-984">Este documento RFC se introdujo para mitigar un problema de seguridad causado originalmente por servidores que no administraban correctamente la negociación de cambio a una versión anterior del protocolo y que, en su lugar, rechazaron mensajes ClientHello válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-984">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="17754-985">En un intento de seguir siendo compatible con estos servidores antiguos, algunas aplicaciones cliente de TLS empezaron a reintentar los protocolos de enlace con errores con una versión de TLS anterior (por ejemplo, TLS 1.2 produce un error y se intenta con TLS 1.1).</span><span class="sxs-lookup"><span data-stu-id="17754-985">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="17754-986">Sin embargo, esta solución ha creado un nuevo problema: un atacante podría forzar a un cliente a cambiar a una versión anterior mediante la introducción artificial de un error de red o de paquete que provoque un error en la conexión con el servidor, incluso cuando el servidor admita la versión más reciente de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-986">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="17754-987">Al cambiar a una versión anterior, el atacante podría aprovechar las vulnerabilidades de seguridad de esa versión (en especial, SSL v3<sup>21</sup> es vulnerable al ataque POODLE).</span><span class="sxs-lookup"><span data-stu-id="17754-987">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="17754-988">Para evitar esta situación, RFC 7507 introduce el "SCSV de reserva", un pseudo conjunto de cifrado<sup>22</sup> enviado en el mensaje ClientHello y que notifica a un servidor TLS cuando un cliente TLS usa una versión de TLS que no es la versión más reciente que admite.</span><span class="sxs-lookup"><span data-stu-id="17754-988">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="17754-989">De este modo, un servidor que admita una versión más reciente puede rechazar un mensaje ClientHello que contenga el SCSV de reserva y evitar que el ataque de cambio a una versión anterior tenga éxito.</span><span class="sxs-lookup"><span data-stu-id="17754-989">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="17754-990">NetX Secure no implementa SSLv3 debido a la existencia de vulnerabilidades de seguridad graves conocidas, como POODLE.</span><span class="sxs-lookup"><span data-stu-id="17754-990">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="17754-991">Un pseudo conjunto de cifrado o SCSV (valor de conjunto de cifrado de señalización) es un número de conjunto de cifrado reservado que se usa para indicar las implementaciones de TLS habilitadas sobre características que no estaban disponibles en versiones anteriores de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-991">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="17754-992">El SCSV de reserva y TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) son ejemplos.</span><span class="sxs-lookup"><span data-stu-id="17754-992">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-993">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-993">Parameters</span></span>

- <span data-ttu-id="17754-994">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-994">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-995">**protocol_version**: macro de la versión de TLS de la versión específica de TLS que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="17754-995">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-996">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-996">Return Values</span></span>

- <span data-ttu-id="17754-997">**NX_SUCCESS**: (0x00) Cambio de estado correcto.</span><span class="sxs-lookup"><span data-stu-id="17754-997">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="17754-998">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-998">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="17754-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION**: (0x110) Versión de TLS conocida pero no admitida.</span><span class="sxs-lookup"><span data-stu-id="17754-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="17754-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION**: (0x10F) Versión de protocolo no válida.</span><span class="sxs-lookup"><span data-stu-id="17754-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1001">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1001">Allowed From</span></span>

<span data-ttu-id="17754-1002">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1002">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1003">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1003">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="17754-1004">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1004">See Also</span></span>

- <span data-ttu-id="17754-1005">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-1005">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-1006">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1006">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="17754-1007">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1007">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="17754-1008">Recibir datos de una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1008">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1009">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1009">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="17754-1010">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1010">Description</span></span>

<span data-ttu-id="17754-1011">Este servicio recibe datos de la sesión de TLS activa especificada, controlando el descifrado de los datos antes de proporcionárselos al autor de llamada en el parámetro NX_PACKET.</span><span class="sxs-lookup"><span data-stu-id="17754-1011">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="17754-1012">Si no hay datos en cola en la sesión especificada, la llamada se suspende en función de la opción de espera proporcionada.</span><span class="sxs-lookup"><span data-stu-id="17754-1012">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-1013">*Si se devuelve NX_SUCCESS, la aplicación es responsable de liberar el paquete recibido después de que ya no se necesite.*</span><span class="sxs-lookup"><span data-stu-id="17754-1013">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1014">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1014">Parameters</span></span>

- <span data-ttu-id="17754-1015">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1015">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-1016">**packet_ptr**: puntero a un puntero de paquete TLS asignado.</span><span class="sxs-lookup"><span data-stu-id="17754-1016">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="17754-1017">**wait_option**: indica cuánto tiempo debe esperar el servicio a un paquete del host remoto antes de volver.</span><span class="sxs-lookup"><span data-stu-id="17754-1017">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1018">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1018">Return Values</span></span>

- <span data-ttu-id="17754-1019">**NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1019">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="17754-1020">**NX_NO_PACKET**: (0x01) No se ha recibido ningún dato.</span><span class="sxs-lookup"><span data-stu-id="17754-1020">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="17754-1021">**NX_NOT_CONNECTED**: (0x38) El socket TCP subyacente ya no está conectado.</span><span class="sxs-lookup"><span data-stu-id="17754-1021">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="17754-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**: (0x108) Un mensaje recibido produjo un error en una comprobación del código hash de autenticación.</span><span class="sxs-lookup"><span data-stu-id="17754-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="17754-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION**: (0x10F) Un mensaje recibido tenía una versión de protocolo desconocida en el encabezado.</span><span class="sxs-lookup"><span data-stu-id="17754-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="17754-1024">**NX_SECURE_TLS_ALERT_RECEIVED**: (0x114) Se ha recibido una alerta del host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="17754-1025">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1025">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="17754-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED**: (0x101) No se inicializó la sesión de TLS proporcionada.</span><span class="sxs-lookup"><span data-stu-id="17754-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1027">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1027">Allowed From</span></span>

<span data-ttu-id="17754-1028">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1028">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1029">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1029">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="17754-1030">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1030">See Also</span></span>

- <span data-ttu-id="17754-1031">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1031">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="17754-1032">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1032">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-1033">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1033">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-1034">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-1034">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-1035">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-1035">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="17754-1036">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-1036">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-1037">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="17754-1037">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="17754-1038">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1038">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="17754-1039">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1039">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="17754-1040">Asignar una devolución de llamada que se invocará al comienzo de una renegociación de sesión</span><span class="sxs-lookup"><span data-stu-id="17754-1040">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1041">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1041">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="17754-1042">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1042">Description</span></span>

<span data-ttu-id="17754-1043">Este servicio asigna una devolución de llamada a una sesión de TLS a la que se invocará siempre que se reciba el primer mensaje de un protocolo de enlace de renegociación de sesión desde el host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-1043">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="17754-1044">La función de devolución de llamada está pensada como una notificación a la aplicación de que se está iniciando un protocolo de enlace de renegociación: la aplicación puede elegir finalizar la sesión de TLS devolviendo cualquier valor distinto de cero de la devolución de llamada, lo que hará que TLS finalice la sesión de TLS con un error.</span><span class="sxs-lookup"><span data-stu-id="17754-1044">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="17754-1045">Si la aplicación desea continuar con la renegociación, la devolución de llamada debe devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="17754-1045">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="17754-1046">*Debido a la semántica de la renegociación de TLS, se invocará a la devolución de llamada para los clientes TLS de NetX Secure siempre que se reciba un mensaje HelloRequest desde el servidor remoto, pero no cuando el cliente inicie la renegociación. En los servidores TLS de NetX Secure, la devolución de llamada se invocará siempre que se reciba un mensaje ClientHello de renegociación (cualquier mensaje ClientHello recibido en el contexto de una sesión de TLS activa). Esto significa que la devolución de llamada se invocará si el host remoto o la aplicación local han iniciado la renegociación, porque el servidor TLS enviará un mensaje HelloRequest al que responderá el cliente remoto.*</span><span class="sxs-lookup"><span data-stu-id="17754-1046">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="17754-1047">TLS de NetX Secure implementa la extensión de indicación de renegociación segura de RFC 5746 para asegurarse de que los protocolos de enlace de renegociación no estén sujetos a ataques de tipo "Man in the Middle".</span><span class="sxs-lookup"><span data-stu-id="17754-1047">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1048">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1048">Parameters</span></span>

- <span data-ttu-id="17754-1049">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1049">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="17754-1050">**func_ptr**: puntero a la función de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="17754-1050">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1051">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1051">Return Values</span></span>

- <span data-ttu-id="17754-1052">**NX_SUCCESS**: (0x00) Asignación correcta de la devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="17754-1052">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="17754-1053">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido para la función de devolución de llamada o para la sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1053">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1054">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1054">Allowed From</span></span>

<span data-ttu-id="17754-1055">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1055">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1056">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1056">Example</span></span>

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a><span data-ttu-id="17754-1057">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1057">See Also</span></span>

- <span data-ttu-id="17754-1058">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1058">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1059">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-1059">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-1060">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1060">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-1061">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-1061">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-1062">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="17754-1062">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="17754-1063">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="17754-1063">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="17754-1064">Iniciar un protocolo de enlace de renegociación de sesión con el host remoto</span><span class="sxs-lookup"><span data-stu-id="17754-1064">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1065">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1065">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="17754-1066">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1066">Description</span></span>

<span data-ttu-id="17754-1067">Este servicio inicia un protocolo de enlace de *renegociación* de sesión con un host TLS remoto conectado.</span><span class="sxs-lookup"><span data-stu-id="17754-1067">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="17754-1068">Una renegociación consta de un segundo protocolo de enlace de TLS en el contexto de una sesión de TLS establecida previamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1068">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="17754-1069">Cada uno de los nuevos mensajes del protocolo de enlace se cifra con la sesión de TLS hasta que se generen nuevas claves de sesión y se intercambien los mensajes ChangeCipherSpec, momento en el que se usan las nuevas claves para cifrar todos los mensajes.</span><span class="sxs-lookup"><span data-stu-id="17754-1069">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="17754-1070">Se puede iniciar una renegociación en cualquier momento una vez establecida una sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1070">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="17754-1071">Si se intenta una renegociación durante un protocolo de enlace de TLS o antes de que se establezca una sesión de TLS, no se realizará ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="17754-1071">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="17754-1072">*Cuando se invoca este servicio, se realizará un protocolo de enlace de TLS completo, por lo que el tiempo de finalización y el estado devuelto variarán en función de los parámetros de sesión y la configuración de TLS actuales.*</span><span class="sxs-lookup"><span data-stu-id="17754-1072">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="17754-1073">TLS de NetX Secure implementa la extensión de indicación de renegociación segura de RFC 5746 para asegurarse de que los protocolos de enlace de renegociación no estén sujetos a ataques de tipo "Man in the Middle".</span><span class="sxs-lookup"><span data-stu-id="17754-1073">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1074">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1074">Parameters</span></span>

- <span data-ttu-id="17754-1075">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1075">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="17754-1076">**wait_option**: indica cuánto tiempo debe esperar el servicio a un paquete del host remoto antes de volver.</span><span class="sxs-lookup"><span data-stu-id="17754-1076">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="17754-1077">Esto se pasa a todos los servicios de NetX dentro de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1077">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1078">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1078">Return Values</span></span>

- <span data-ttu-id="17754-1079">**NX_SUCCESS**: (0x00) Renegociación correcta.</span><span class="sxs-lookup"><span data-stu-id="17754-1079">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="17754-1080">**NX_NO_PACKET**: (0x01) No se ha recibido ningún dato.</span><span class="sxs-lookup"><span data-stu-id="17754-1080">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="17754-1081">**NX_NOT_CONNECTED**: (0x38) El socket TCP subyacente ya no está conectado.</span><span class="sxs-lookup"><span data-stu-id="17754-1081">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="17754-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**: (0x108) Un mensaje recibido produjo un error en una comprobación del código hash de autenticación.</span><span class="sxs-lookup"><span data-stu-id="17754-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="17754-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION**: (0x10F) Un mensaje recibido tenía una versión de protocolo desconocida en el encabezado.</span><span class="sxs-lookup"><span data-stu-id="17754-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="17754-1084">**NX_SECURE_TLS_ALERT_RECEIVED**: (0x114) Se ha recibido una alerta del host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="17754-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE**: (0x134) La sesión de TLS local o remota está inactiva, lo que hace imposible la renegociación.</span><span class="sxs-lookup"><span data-stu-id="17754-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="17754-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE**: (0x13A) El host remoto no proporcionó la extensión de renegociación segura o el SCSV, por lo que no se puede realizar la renegociación.</span><span class="sxs-lookup"><span data-stu-id="17754-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="17754-1087">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1087">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="17754-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED**: (0x101) No se inicializó la sesión de TLS proporcionada.</span><span class="sxs-lookup"><span data-stu-id="17754-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="17754-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**: (0x111) Error al asignar el paquete subyacente.</span><span class="sxs-lookup"><span data-stu-id="17754-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1090">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1090">Allowed From</span></span>

<span data-ttu-id="17754-1091">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1091">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1092">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1092">Example</span></span>

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a><span data-ttu-id="17754-1093">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1093">See Also</span></span>

- <span data-ttu-id="17754-1094">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1094">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1095">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-1095">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-1096">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1096">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-1097">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-1097">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-1098">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1098">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="17754-1099">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="17754-1099">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="17754-1100">Borrar y restablecer una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1100">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1101">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1101">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="17754-1102">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1102">Description</span></span>

<span data-ttu-id="17754-1103">Este servicio borra una sesión de TLS y restablece el estado como si la sesión se hubiera creado ahora, por lo que se puede volver a usar un objeto de sesión de TLS existente para una nueva sesión.</span><span class="sxs-lookup"><span data-stu-id="17754-1103">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1104">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1104">Parameters</span></span>

- <span data-ttu-id="17754-1105">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1105">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1106">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1106">Return Values</span></span>

- <span data-ttu-id="17754-1107">**NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1107">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="17754-1108">**NX_INVALID_PARAMETERS**: (0x4D) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1108">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="17754-1109">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1109">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1110">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1110">Allowed From</span></span>

<span data-ttu-id="17754-1111">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1111">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1112">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1112">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="17754-1113">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1113">See Also</span></span>

- <span data-ttu-id="17754-1114">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1114">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-1115">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1115">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-1116">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-1116">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-1117">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-1117">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="17754-1118">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-1118">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-1119">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1119">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-1120">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1120">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="17754-1121">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-1121">nx_secure_tls_session_send</span></span>

<span data-ttu-id="17754-1122">Enviar datos mediante una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1122">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1123">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1123">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="17754-1124">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1124">Description</span></span>

<span data-ttu-id="17754-1125">Este servicio envía datos en el elemento NX_PACKET proporcionado, utilizando la sesión de TLS activa especificada y controlando el cifrado de los datos antes de enviarlos al host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-1125">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="17754-1126">Si el último tamaño de ventana anunciado del receptor es menor que esta solicitud, el servicio se suspende opcionalmente en función de las opciones de espera especificada.</span><span class="sxs-lookup"><span data-stu-id="17754-1126">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-1127">*A menos que se devuelva un error, la aplicación no debe liberar el paquete después de esta llamada. Si lo hace, se producirán resultados imprevisibles, ya que el controlador de red liberará el paquete después de la transmisión.*</span><span class="sxs-lookup"><span data-stu-id="17754-1127">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1128">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1128">Parameters</span></span>

- <span data-ttu-id="17754-1129">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1129">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-1130">**packet_ptr**: puntero a un paquete TLS que contiene los datos que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="17754-1130">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="17754-1131">**wait_option**: define cómo se comporta el servicio si la solicitud es mayor que el tamaño de la ventana del receptor.</span><span class="sxs-lookup"><span data-stu-id="17754-1131">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1132">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1132">Return Values</span></span>

- <span data-ttu-id="17754-1133">**NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1133">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="17754-1134">**NX_NO_PACKET**: (0x01) No se ha recibido ningún dato.</span><span class="sxs-lookup"><span data-stu-id="17754-1134">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="17754-1135">**NX_NOT_CONNECTED**: (0x38) El socket TCP subyacente ya no está conectado.</span><span class="sxs-lookup"><span data-stu-id="17754-1135">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="17754-1136">**NX_SECURE_TLS_TCP_SEND_FAILED**: (0x109) Error al enviar mediante un socket TCP subyacente.</span><span class="sxs-lookup"><span data-stu-id="17754-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="17754-1137">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1137">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="17754-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED**: (0x101) No se inicializó la sesión de TLS proporcionada.</span><span class="sxs-lookup"><span data-stu-id="17754-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1139">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1139">Allowed From</span></span>

<span data-ttu-id="17754-1140">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1140">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1141">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1141">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="17754-1142">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1142">See Also</span></span>

- <span data-ttu-id="17754-1143">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1143">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="17754-1144">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1144">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-1145">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1145">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-1146">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1146">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="17754-1147">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-1147">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-1148">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-1148">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="17754-1149">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1149">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-1150">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="17754-1150">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="17754-1151">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1151">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="17754-1152">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1152">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="17754-1153">Configurar una devolución de llamada para que TLS la invoque al comienzo de un protocolo de enlace del servidor TLS</span><span class="sxs-lookup"><span data-stu-id="17754-1153">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1154">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1154">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="17754-1155">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1155">Description</span></span>

<span data-ttu-id="17754-1156">Este servicio asigna un puntero de función a una sesión de TLS a la que TLS invocará cuando un protocolo de enlace del servidor TLS haya recibido un mensaje ClientHello.</span><span class="sxs-lookup"><span data-stu-id="17754-1156">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="17754-1157">La función de devolución de llamada permite a una aplicación procesar las extensiones de TLS del mensaje ClientHello recibido que requieran la toma de decisiones o una entrada.</span><span class="sxs-lookup"><span data-stu-id="17754-1157">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="17754-1158">La devolución de llamada se ejecuta con el bloque de control de la sesión de TLS de invocación y una matriz de objetos NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="17754-1158">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="17754-1159">La matriz de objetos de extensión está pensada para pasarse a una función auxiliar que buscará y analizará una extensión específica.</span><span class="sxs-lookup"><span data-stu-id="17754-1159">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="17754-1160">Para obtener una función auxiliar de ejemplo que analice las extensiones de TLS proporcionadas en los mensajes de saludo, consulte *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="17754-1160">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="17754-1161">La devolución de llamada del servidor también se puede usar para seleccionar el certificado de identidad activo mediante *nx_secure_tls_active_certificate_set* para el servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1161">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="17754-1162">Esto se suele producir en respuesta a una extensión de Indicación de nombre de servidor (SNI), que permite a un cliente TLS indicar el servidor con el que intenta ponerse en contacto.</span><span class="sxs-lookup"><span data-stu-id="17754-1162">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="17754-1163">Consulte las referencias de *nx_secure_tls_session_sni_extension_parse* y *nx_secure_tls_active_certificate_set* para más información.</span><span class="sxs-lookup"><span data-stu-id="17754-1163">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1164">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1164">Parameters</span></span>

- <span data-ttu-id="17754-1165">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-1165">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-1166">**func_ptr**: puntero a la función de devolución de llamada del servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1166">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1167">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1167">Return Values</span></span>

- <span data-ttu-id="17754-1168">**NX_SUCCESS**: (0x00) Asignación correcta del puntero de función.</span><span class="sxs-lookup"><span data-stu-id="17754-1168">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="17754-1169">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1169">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1170">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1170">Allowed From</span></span>

<span data-ttu-id="17754-1171">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1172">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1172">Example</span></span>

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="17754-1173">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1173">See Also</span></span>

- <span data-ttu-id="17754-1174">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1174">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1175">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1175">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="17754-1176">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="17754-1176">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="17754-1177">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-1177">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="17754-1178">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-1178">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="17754-1179">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="17754-1179">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="17754-1180">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-1180">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="17754-1181">Analizar una extensión de Indicación de nombre de servidor (SNI) recibida desde un cliente TLS</span><span class="sxs-lookup"><span data-stu-id="17754-1181">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1182">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1182">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="17754-1183">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1183">Description</span></span>

<span data-ttu-id="17754-1184">Este servicio está diseñado para que se le llame desde una devolución de llamada de la sesión del servidor TLS, que se agrega a una sesión de TLS mediante nx_secure_tls_session_server_callback_set.</span><span class="sxs-lookup"><span data-stu-id="17754-1184">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="17754-1185">Se invoca a la devolución de llamada después de la recepción de un mensaje ClientHello desde un cliente TLS remoto y se proporciona una matriz de extensiones disponibles (y el número de extensiones de la matriz).</span><span class="sxs-lookup"><span data-stu-id="17754-1185">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="17754-1186">Se pueden pasar esa matriz y su longitud directamente a esta rutina para determinar si hay una extensión SNI presente; si no la hay, se devuelve NX_SECURE_TLS_EXTENSION_NOT_FOUND, lo que indica simplemente que el cliente optó por no proporcionar la extensión SNI (esto no es un error).</span><span class="sxs-lookup"><span data-stu-id="17754-1186">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="17754-1187">Si se encuentra la extensión SNI, se devuelve el nombre DNS de X.509 proporcionado por el cliente TLS en la estructura dns_name.</span><span class="sxs-lookup"><span data-stu-id="17754-1187">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="17754-1188">Actualmente, la extensión SNI solo proporciona una única entrada de nombre DNS, que puede ser utilizada por el servidor TLS para determinar el certificado de identidad que se va a enviar al cliente remoto.\*\*</span><span class="sxs-lookup"><span data-stu-id="17754-1188">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="17754-1189">La estructura NX_SECURE_X509_DNS_NAME simplemente contiene el nombre DNS como una cadena UCHAR en el campo *nx_secure_x509_dns_name* y la longitud de la cadena de nombre en *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="17754-1189">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="17754-1190">La macro NX_SECURE_X509_DNS_NAME_MAX controla el tamaño del búfer de nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="17754-1190">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1191">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1191">Parameters</span></span>

- <span data-ttu-id="17754-1192">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1192">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-1193">**extensions**: puntero a una matriz de extensiones de saludo de TLS (desde la devolución de llamada de la sesión).</span><span class="sxs-lookup"><span data-stu-id="17754-1193">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="17754-1194">**num_extensions**: número de extensiones de la matriz (desde la devolución de llamada de la sesión).</span><span class="sxs-lookup"><span data-stu-id="17754-1194">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="17754-1195">**dns_name**: devuelve el nombre DNS proporcionado en la extensión SNI.</span><span class="sxs-lookup"><span data-stu-id="17754-1195">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1196">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1196">Return Values</span></span>

- <span data-ttu-id="17754-1197">**NX_SUCCESS**: (0x00) Análisis correcto de la extensión.</span><span class="sxs-lookup"><span data-stu-id="17754-1197">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="17754-1198">**NX_PTR_ERROR**: (0x07) Matriz de extensiones o puntero de sesión de TLS no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-1198">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="17754-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND**: (0x136) No se ha encontrado la extensión SNI.</span><span class="sxs-lookup"><span data-stu-id="17754-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="17754-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID**: (0x137) El formato de la extensión SNI no era válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1201">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1201">Allowed From</span></span>

<span data-ttu-id="17754-1202">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1203">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1203">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="17754-1204">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1204">See Also</span></span>

- <span data-ttu-id="17754-1205">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1205">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="17754-1206">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1206">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="17754-1207">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1207">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="17754-1208">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="17754-1208">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="17754-1209">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="17754-1209">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="17754-1210">Establecer un nombre DNS de extensión de Indicación de nombre de servidor (SNI) para enviar a un servidor remoto</span><span class="sxs-lookup"><span data-stu-id="17754-1210">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1211">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1211">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="17754-1212">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1212">Description</span></span>

<span data-ttu-id="17754-1213">Este servicio permite que una aplicación de cliente TLS proporcione un nombre DNS de servidor preferido a un servidor TLS remoto mediante la extensión Indicación de nombre de servidor (SNI) de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1213">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="17754-1214">La extensión SNI permite al servidor seleccionar el certificado de identidad y los parámetros adecuados en función de la preferencia de servidor indicada por el cliente.</span><span class="sxs-lookup"><span data-stu-id="17754-1214">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="17754-1215">La extensión SNI actualmente solo admite el envío de un único nombre DNS, de ahí el parámetro de nombre en singular.</span><span class="sxs-lookup"><span data-stu-id="17754-1215">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="17754-1216">El parámetro dns_name se debe inicializar con *nx_secure_x509_dns_name_initialize* y contendrá el servidor preferido del cliente.</span><span class="sxs-lookup"><span data-stu-id="17754-1216">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="17754-1217">Para anular el nombre de la extensión, basta con llamar a este servicio con un valor del parámetro "dns_name" establecido en NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="17754-1217">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="17754-1218">La estructura NX_SECURE_X509_DNS_NAME simplemente contiene el nombre DNS como una cadena UCHAR en el campo *nx_secure_x509_dns_name* y la longitud de la cadena de nombre en *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="17754-1218">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="17754-1219">La macro NX_SECURE_X509_DNS_NAME_MAX controla el tamaño del búfer de nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="17754-1219">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="17754-1220">*Se debe llamar a esta rutina antes de invocar a nx_secure_tls_session_start o el mensaje ClientHello no contendrá la extensión SNI.*</span><span class="sxs-lookup"><span data-stu-id="17754-1220">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1221">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1221">Parameters</span></span>

- <span data-ttu-id="17754-1222">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1222">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-1223">**dns_name**: nombre DNS proporcionado por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="17754-1223">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1224">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1224">Return Values</span></span>

- <span data-ttu-id="17754-1225">**NX_SUCCESS**: (0x00) Nombre de servidor DNS agregado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1225">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="17754-1226">**NX_PTR_ERROR**: (0x07) Nombre DNS o puntero de sesión de TLS no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-1226">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1227">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1227">Allowed From</span></span>

<span data-ttu-id="17754-1228">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1228">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1229">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1229">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a><span data-ttu-id="17754-1230">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1230">See Also</span></span>

- <span data-ttu-id="17754-1231">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-1231">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-1232">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1232">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="17754-1233">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-1233">nx_secure_tls_session_start</span></span>

<span data-ttu-id="17754-1234">Iniciar una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1234">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1235">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1235">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="17754-1236">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1236">Description</span></span>

<span data-ttu-id="17754-1237">Este servicio inicia una sesión de TLS con el bloque de control de la sesión de TLS proporcionado y un socket TCP conectado.</span><span class="sxs-lookup"><span data-stu-id="17754-1237">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="17754-1238">La conexión TCP ya debe estar completa después de una llamada correcta a nx_tcp_client_socket_connect o nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="17754-1238">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="17754-1239">Este servicio determinará el tipo de sesión de TLS (cliente o servidor) a partir del socket TCP.</span><span class="sxs-lookup"><span data-stu-id="17754-1239">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="17754-1240">La opción de espera define cómo se comporta el servicio mientras el protocolo de enlace de TLS está en curso.</span><span class="sxs-lookup"><span data-stu-id="17754-1240">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1241">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1241">Parameters</span></span>

- <span data-ttu-id="17754-1242">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1242">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-1243">**tcp_socket_ptr**: puntero a un socket TCP conectado.</span><span class="sxs-lookup"><span data-stu-id="17754-1243">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="17754-1244">**wait_option**: define cómo se comporta el servicio mientras el protocolo de enlace de TLS está en curso.</span><span class="sxs-lookup"><span data-stu-id="17754-1244">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1245">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1245">Return Values</span></span>

- <span data-ttu-id="17754-1246">**NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1246">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="17754-1247">**NX_NOT_CONNECTED**: (0x38) El socket TCP subyacente ya no está conectado.</span><span class="sxs-lookup"><span data-stu-id="17754-1247">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="17754-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**: (0x102) Un tipo de mensaje TLS recibido es incorrecto.</span><span class="sxs-lookup"><span data-stu-id="17754-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="17754-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER**: (0x106) No se admite el cifrado proporcionado por el host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="17754-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE**: (0x107) Error al procesar el mensaje durante el protocolo de enlace de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="17754-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE**: (0x108) Un mensaje entrante no pudo realizar una comprobación del hash de MAC.</span><span class="sxs-lookup"><span data-stu-id="17754-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="17754-1252">**NX_SECURE_TLS_TCP_SEND_FAILED**: (0x109) Error al enviar mediante un socket TCP subyacente.</span><span class="sxs-lookup"><span data-stu-id="17754-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="17754-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH**: (0x10A) Un mensaje entrante tenía un campo de longitud no válida.</span><span class="sxs-lookup"><span data-stu-id="17754-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="17754-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC**: (0x10B) Un mensaje ChangeCipherSpec entrante era incorrecto.</span><span class="sxs-lookup"><span data-stu-id="17754-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="17754-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT**: (0x10C) Un certificado TLS entrante no se puede usar para identificar el servidor TLS remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="17754-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER**: (0x10D) No se admite el cifrado de clave pública proporcionado por el host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="17754-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS**: (0x10E) El host remoto ha indicado que no hay conjuntos de cifrado admitidos por la pila de TLS de NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="17754-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="17754-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION**: (0x10F) Un mensaje TLS recibido tenía una versión de TLS desconocida en el encabezado.</span><span class="sxs-lookup"><span data-stu-id="17754-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="17754-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION**: (0x110) Un mensaje TLS recibido tenía una versión de TLS conocida pero no admitida en el encabezado.</span><span class="sxs-lookup"><span data-stu-id="17754-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="17754-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED**: (0x111) Error en la asignación interna del paquete TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="17754-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE**: (0x112) El host remoto proporcionó un certificado no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="17754-1262">**NX_SECURE_TLS_ALERT_RECEIVED**: (0x114) El host remoto envió una alerta que indica un error y finaliza la sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="17754-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE**: (0x13B) Una entrada de la tabla del conjunto de cifrado tenía un puntero de función NULL.</span><span class="sxs-lookup"><span data-stu-id="17754-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="17754-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK**: (0x146) Un mensaje ClientHello de TLS remoto incluía el SCSV de reserva y ha intentado un cambio a una versión de reserva.</span><span class="sxs-lookup"><span data-stu-id="17754-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="17754-1265">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1265">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1266">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1266">Allowed From</span></span>

<span data-ttu-id="17754-1267">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1268">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1268">Example</span></span>

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a><span data-ttu-id="17754-1269">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1269">See Also</span></span>

- <span data-ttu-id="17754-1270">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1270">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="17754-1271">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1271">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-1272">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1272">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-1273">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="17754-1273">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="17754-1274">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-1274">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="17754-1275">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1275">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-1276">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1276">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="17754-1277">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="17754-1277">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="17754-1278">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1278">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1279">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="17754-1279">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="17754-1280">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="17754-1280">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="17754-1281">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="17754-1281">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="17754-1282">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="17754-1282">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="17754-1283">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="17754-1283">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="17754-1284">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="17754-1284">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="17754-1285">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1285">nx_packet_allocate</span></span>
- <span data-ttu-id="17754-1286">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="17754-1286">nx_packet_data_append</span></span>
- <span data-ttu-id="17754-1287">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="17754-1287">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="17754-1288">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="17754-1288">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="17754-1289">Asignar una función de marca de tiempo a una sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1289">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1290">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1290">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="17754-1291">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1291">Description</span></span>

<span data-ttu-id="17754-1292">Esta función configura un puntero de función a la que TLS invocará cuando tenga que obtener la hora actual, que se usa en varios mensajes del protocolo de enlace de TLS y para la comprobación de certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-1292">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="17754-1293">Se espera que la función devuelva el valor de la hora GMT actual en formato de 32 bits de UNIX (segundos desde la medianoche a partir del 1 de enero de 1970, UTC, pasando por alto los segundos bisiestos), según los requisitos para mensajes ClientHello de RFC 5246 de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1293">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="17754-1294">Si no se asigna ninguna función de marca de tiempo, se usará un valor de 0 para la marca de tiempo en el protocolo de enlace de TLS y la comprobación de la expiración del certificado no funcionará.</span><span class="sxs-lookup"><span data-stu-id="17754-1294">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1295">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1295">Parameters</span></span>

- <span data-ttu-id="17754-1296">**session_ptr**: puntero a una instancia de sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1296">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="17754-1297">**time_func_ptr**: puntero a una función que devuelve la hora actual (GMT) en formato de 32 bits de UNIX.</span><span class="sxs-lookup"><span data-stu-id="17754-1297">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1298">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1298">Return Values</span></span>

- <span data-ttu-id="17754-1299">**NX_SUCCESS**: (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1299">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="17754-1300">**NX_INVALID_PARAMETERS**: (0x4D) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1300">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="17754-1301">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1301">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1302">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1302">Allowed From</span></span>

<span data-ttu-id="17754-1303">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1303">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1304">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1304">Example</span></span>

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a><span data-ttu-id="17754-1305">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1305">See Also</span></span>

- <span data-ttu-id="17754-1306">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1306">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-1307">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1307">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-1308">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="17754-1308">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="17754-1309">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="17754-1309">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="17754-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="17754-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="17754-1311">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1311">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="17754-1312">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-1312">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="17754-1313">Agregar un certificado de confianza a la sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1313">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1314">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1314">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="17754-1315">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1315">Description</span></span>

<span data-ttu-id="17754-1316">Este servicio agrega una instancia de la estructura NX_SECURE_X509_CERT inicializada a una sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1316">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="17754-1317">La pila de TLS usa este certificado para comprobar los certificados proporcionados por el host remoto durante el protocolo de enlace de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1317">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="17754-1318">Los certificados de confianza son necesarios para el modo de cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1318">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="17754-1319">Los certificados de confianza solo son necesarios para el modo de servidor TLS si está habilitada la autenticación de certificados de cliente.</span><span class="sxs-lookup"><span data-stu-id="17754-1319">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1320">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1320">Parameters</span></span>

- <span data-ttu-id="17754-1321">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-1321">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-1322">**certificate_ptr**: puntero a una instancia de certificado TLS inicializada.</span><span class="sxs-lookup"><span data-stu-id="17754-1322">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1323">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1323">Return Values</span></span>

- <span data-ttu-id="17754-1324">**NX_SUCCESS**: (0x00) Certificado agregado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1324">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="17754-1325">**NX_INVALID_PARAMETERS**: (0x4D) Se ha intentado agregar un certificado no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1325">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="17754-1326">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1326">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1327">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1327">Allowed From</span></span>

<span data-ttu-id="17754-1328">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1329">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1329">Example</span></span>

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-1330">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1330">See Also</span></span>

- <span data-ttu-id="17754-1331">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1331">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-1332">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1332">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1333">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1333">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-1334">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-1334">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="17754-1335">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="17754-1335">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="17754-1336">Quitar un certificado de confianza de la sesión de TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1336">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1337">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1337">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="17754-1338">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1338">Description</span></span>

<span data-ttu-id="17754-1339">Este servicio quita un certificado de confianza de una sesión de TLS, con la clave en el campo de nombre común del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1339">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1340">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1340">Parameters</span></span>

- <span data-ttu-id="17754-1341">**session_ptr**: puntero a una instancia de sesión de TLS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="17754-1341">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="17754-1342">**common_name**: valor del nombre común del certificado que se va a quitar.</span><span class="sxs-lookup"><span data-stu-id="17754-1342">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="17754-1343">**common_name_length**: longitud de la cadena del nombre común.</span><span class="sxs-lookup"><span data-stu-id="17754-1343">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1344">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1344">Return Values</span></span>

- <span data-ttu-id="17754-1345">**NX_SUCCESS**: (0x00) Certificado agregado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="17754-1346">**NX_PTR_ERROR**: (0x07) Puntero a la sesión de TLS no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1346">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="17754-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) No se encontró el certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1348">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1348">Allowed From</span></span>

<span data-ttu-id="17754-1349">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1350">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1350">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-1351">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1351">See Also</span></span>

- <span data-ttu-id="17754-1352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="17754-1353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-1355">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-1355">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="17754-1356">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1356">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="17754-1357">Inicializar un certificado X.509 para TLS de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1357">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1358">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1358">Prototype</span></span>

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a><span data-ttu-id="17754-1359">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1359">Description</span></span>

<span data-ttu-id="17754-1360">Este servicio inicializa una estructura NX_SECURE_X509_CERT a partir de un certificado digital X.509 codificado en binario para su uso en una sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1360">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="17754-1361">Los datos del certificado **deben** ser un certificado digital X.509 válido en formato binario con codificación DER.</span><span class="sxs-lookup"><span data-stu-id="17754-1361">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="17754-1362">Los datos pueden proceder de cualquier origen (por ejemplo, el sistema de archivos, el búfer de constantes compilado, etc.), siempre que se proporcione un puntero UCHAR a los datos.</span><span class="sxs-lookup"><span data-stu-id="17754-1362">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="17754-1363">El parámetro *raw_data_buffer* y su tamaño son parámetros opcionales que especifican un búfer dedicado en el que se copian los datos del certificado antes del análisis.</span><span class="sxs-lookup"><span data-stu-id="17754-1363">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="17754-1364">Si raw_data_buffer se pasa como NX_NULL, la estructura NX_SECURE_X509_CERT apuntará directamente a la matriz certificate_data (en este caso, se omitirá buffer_size).</span><span class="sxs-lookup"><span data-stu-id="17754-1364">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="17754-1365">Si se pasa raw_data_buffer como NX_NULL, ***no*** modifique los datos a los que apunta el puntero certificate_data o se producirá un error en el procesamiento del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1365">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="17754-1366">El parámetro de clave privada es para los certificados de identidad local: los servidores usan la clave privada para descifrar los datos de clave entrante de un cliente (cifrados con la clave pública del servidor) y los clientes para comprobar su identidad en un servidor cuando el servidor solicita un certificado de cliente.</span><span class="sxs-lookup"><span data-stu-id="17754-1366">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="17754-1367">Al agregar una clave privada con esta API, se marcará automáticamente el certificado asociado como certificado de identidad para una aplicación TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1367">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="17754-1368">Al inicializar los certificados para otros propósitos (por ejemplo, el almacén de confianza), el parámetro *private_key_data* se debe pasar como NULL, *private_key_data_length* como 0 y *private_key_type* se debe pasar como NX_SECURE_X509_KEY_TYPE_NONE.</span><span class="sxs-lookup"><span data-stu-id="17754-1368">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="17754-1369">El parámetro *private_key_type* indica el formato de la clave privada.</span><span class="sxs-lookup"><span data-stu-id="17754-1369">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="17754-1370">Por ejemplo, si la clave privada es una clave privada RSA con formato PKCS#1 y codificación DER, el parámetro private_key_type se debe pasar como NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, un tipo conocido para NetX Secure que se analizará inmediatamente y se guardará para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="17754-1370">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="17754-1371">El parámetro private_key_type también admite tipos de clave definidos por el usuario<sup>23</sup> para plataformas y aplicaciones que tengan formatos de clave específicos u otras necesidades.</span><span class="sxs-lookup"><span data-stu-id="17754-1371">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="17754-1372">Por ejemplo, un motor de cifrado basado en hardware puede usar un formato específico no reconocido por el software de NetX Secure, o se puede cifrar o representar una clave privada mediante un token criptográfico, como podría ser el caso de un Módulo de plataforma segura (TPM) o de hardware criptográfico PKCS#11.</span><span class="sxs-lookup"><span data-stu-id="17754-1372">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="17754-1373">Cuando se usa un tipo de clave definido por el usuario, los datos de la clave se pasan literalmente a la rutina criptográfica adecuada; por ejemplo, se pasaría una clave privada RSA, sin análisis ni procesamiento, directamente a la rutina criptográfica de RSA proporcionada a TLS en la tabla de conjuntos de cifrado.</span><span class="sxs-lookup"><span data-stu-id="17754-1373">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="17754-1374">El tipo de clave definido por el usuario también se pasa a la rutina criptográfica (en el caso de RSA, es el parámetro "op").</span><span class="sxs-lookup"><span data-stu-id="17754-1374">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="17754-1375">El intervalo de claves definidas por el usuario abarca la mitad superior de un número entero sin signo de 32 bits, de 0x0001 0000 a 0xFFFF FFFF.</span><span class="sxs-lookup"><span data-stu-id="17754-1375">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="17754-1376">Los valores menores que 0x0001 0000 se reservan para el uso de NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="17754-1376">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="17754-1377">Los tipos de clave definidos por el usuario son una característica avanzada que requiere rutinas criptográficas personalizadas para controlar los datos de clave privada sin procesar.</span><span class="sxs-lookup"><span data-stu-id="17754-1377">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="17754-1378">Si necesita esta característica, póngase en contacto con su representante de Logic Express.</span><span class="sxs-lookup"><span data-stu-id="17754-1378">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1379">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1379">Parameters</span></span>

- <span data-ttu-id="17754-1380">**certificate_ptr**: puntero a una instancia de certificado X.509 no inicializada.</span><span class="sxs-lookup"><span data-stu-id="17754-1380">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="17754-1381">**certificate_data**: puntero a los datos binarios X.509 con codificación DER.</span><span class="sxs-lookup"><span data-stu-id="17754-1381">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="17754-1382">**raw_data_buffer**: puntero al búfer de datos de certificados dedicado opcional.</span><span class="sxs-lookup"><span data-stu-id="17754-1382">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="17754-1383">**buffer_size**: tamaño del búfer de datos de certificados dedicado opcional.</span><span class="sxs-lookup"><span data-stu-id="17754-1383">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="17754-1384">**certificate_data_length**: longitud de los datos binarios del certificado en bytes.</span><span class="sxs-lookup"><span data-stu-id="17754-1384">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="17754-1385">**private_key_data**: puntero a los datos de la clave privada opcional.</span><span class="sxs-lookup"><span data-stu-id="17754-1385">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="17754-1386">**private_key_data_length**: longitud de los datos de la clave privada.</span><span class="sxs-lookup"><span data-stu-id="17754-1386">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="17754-1387">**private_key_type**: identificador del tipo de clave.</span><span class="sxs-lookup"><span data-stu-id="17754-1387">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1388">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1388">Return Values</span></span>

- <span data-ttu-id="17754-1389">**NX_SUCCESS**: (0x00) Certificado agregado correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1389">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="17754-1390">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1390">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="17754-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE**: (0x112) Los datos del certificado no contenían un certificado X.509 con codificación DER.</span><span class="sxs-lookup"><span data-stu-id="17754-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="17754-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER**: (0x10D) El certificado no tenía un cifrado de clave pública admitido por NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="17754-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="17754-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE**: (0x186) La clave privada o el certificado no contenían una secuencia ASN.1 válida.</span><span class="sxs-lookup"><span data-stu-id="17754-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="17754-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY**: (0x18A) La clave privada proporcionada no era una clave RSA PKCS#1 válida.</span><span class="sxs-lookup"><span data-stu-id="17754-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="17754-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE**: (0x19D) El tipo de clave privada proporcionado no estaba definido por el usuario y no coincidía con ningún tipo conocido.</span><span class="sxs-lookup"><span data-stu-id="17754-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1396">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1396">Allowed From</span></span>

<span data-ttu-id="17754-1397">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1398">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1398">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="17754-1399">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1399">See Also</span></span>

- <span data-ttu-id="17754-1400">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="17754-1400">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="17754-1401">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1401">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1402">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="17754-1402">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="17754-1403">Importación de certificados X.509 en NetX Secure en el Capítulo 3.</span><span class="sxs-lookup"><span data-stu-id="17754-1403">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="17754-1404">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="17754-1404">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="17754-1405">Comprobar el nombre DNS con el certificado X.509</span><span class="sxs-lookup"><span data-stu-id="17754-1405">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1406">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1406">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="17754-1407">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1407">Description</span></span>

<span data-ttu-id="17754-1408">Este servicio comprueba el nombre común de un certificado con un nombre de dominio de nivel superior (TLD) proporcionado por el autor de llamada para la validación DNS de un host remoto.</span><span class="sxs-lookup"><span data-stu-id="17754-1408">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="17754-1409">Esta función auxiliar está pensada para ser llamada desde una rutina de devolución de llamada de validación de certificados proporcionada por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="17754-1409">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="17754-1410">El nombre del TLD debe ser la parte superior de la dirección URL usada para acceder al host remoto (la cadena separada por "." antes de la primera barra diagonal).</span><span class="sxs-lookup"><span data-stu-id="17754-1410">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="17754-1411">Si el nombre común contiene un carácter comodín (por ejemplo, *.example.com), el carácter comodín coincidirá con cualquiera que tenga el mismo sufijo. Tenga en cuenta que solo se tendrá en cuenta el primer carácter comodín ("* ") encontrado (lectura de derecha a izquierda) para la coincidencia de caracteres comodín: por ejemplo, abc.\*. example. com coincidirá con *cualquier* nombre que termine en ".example.com".</span><span class="sxs-lookup"><span data-stu-id="17754-1411">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="17754-1412">Si el nombre común no coincide con la cadena proporcionada, se analiza la extensión "subjectAltName" (si existe en el certificado) y también se comparan las entradas de nombres DNS.</span><span class="sxs-lookup"><span data-stu-id="17754-1412">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="17754-1413">Si ninguna de esas entradas coincide, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="17754-1413">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="17754-1414">Es importante comprender el formato del nombre común (y las entradas subjectAltName) en los certificados esperados.</span><span class="sxs-lookup"><span data-stu-id="17754-1414">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="17754-1415">Por ejemplo, algunos certificados pueden usar una dirección IP sin formato o un carácter comodín.</span><span class="sxs-lookup"><span data-stu-id="17754-1415">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="17754-1416">Se debe dar formato a la cadena del TLD de DNS para que coincida con los valores esperados en los certificados recibidos.</span><span class="sxs-lookup"><span data-stu-id="17754-1416">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1417">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1417">Parameters</span></span>

- <span data-ttu-id="17754-1418">**certificate_ptr**: puntero a una instancia de certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="17754-1418">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="17754-1419">**dns_tld**: nombre del dominio de nivel superior con el que se va a comparar.</span><span class="sxs-lookup"><span data-stu-id="17754-1419">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="17754-1420">**dns_tld_length**: longitud de la cadena del TLD.</span><span class="sxs-lookup"><span data-stu-id="17754-1420">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1421">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1421">Return Values</span></span>

- <span data-ttu-id="17754-1422">**NX_SUCCESS**: (0x00) Comparación correcta con el nombre común o con subjectAltName.</span><span class="sxs-lookup"><span data-stu-id="17754-1422">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="17754-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH**: (0x195) No se encontró ningún nombre coincidente.</span><span class="sxs-lookup"><span data-stu-id="17754-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="17754-1424">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1424">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1425">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1425">Allowed From</span></span>

<span data-ttu-id="17754-1426">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1426">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1427">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1427">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="17754-1428">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1428">See Also</span></span>

- <span data-ttu-id="17754-1429">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1429">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1430">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1430">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="17754-1431">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="17754-1431">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="17754-1432">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="17754-1432">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="17754-1433">Comprobar el certificado X.509 en una lista de revocación de certificados (CRL) proporcionada</span><span class="sxs-lookup"><span data-stu-id="17754-1433">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1434">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1434">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="17754-1435">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1435">Description</span></span>

<span data-ttu-id="17754-1436">Este servicio toma una lista de revocación de certificados con codificación DER y busca un certificado específico en esa lista.</span><span class="sxs-lookup"><span data-stu-id="17754-1436">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="17754-1437">El emisor de la CRL se valida con un almacén de certificados proporcionado, el emisor de la CRL se valida para que sea el mismo que en el certificado que se está comprobando y el número de serie del certificado en cuestión se usa para buscar en la lista de certificados revocados.</span><span class="sxs-lookup"><span data-stu-id="17754-1437">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="17754-1438">Si los emisores coinciden, se comprueba correctamente la firma y el certificado **no** está presente en la lista, la llamada se realiza correctamente.</span><span class="sxs-lookup"><span data-stu-id="17754-1438">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="17754-1439">Todos los demás casos provocan que se devuelva un error.</span><span class="sxs-lookup"><span data-stu-id="17754-1439">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1440">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1440">Parameters</span></span>

- <span data-ttu-id="17754-1441">**crl_data**: puntero a una CRL con codificación DER.</span><span class="sxs-lookup"><span data-stu-id="17754-1441">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="17754-1442">**crl_length**: longitud en bytes de los datos de la CRL.</span><span class="sxs-lookup"><span data-stu-id="17754-1442">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="17754-1443">**store**: puntero a un almacén de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="17754-1443">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="17754-1444">**certificate_ptr**: puntero a una instancia de certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="17754-1444">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1445">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1445">Return Values</span></span>

- <span data-ttu-id="17754-1446">**NX_SUCCESS**: (0x00) Validación correcta de que no se ha revocado el certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1446">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="17754-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND**: (0x119) No se encontró el certificado del emisor de la CRL.</span><span class="sxs-lookup"><span data-stu-id="17754-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="17754-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND**: (0x11B) No se encontró el certificado del emisor del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="17754-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**: (0x182) El elemento ASN.1 de la CRL contenía un campo de longitud no válida.</span><span class="sxs-lookup"><span data-stu-id="17754-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="17754-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG**: (0x189) La CRL contenía un elemento ASN.1 no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="17754-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE**: (0x18C) Error de comprobación de la cadena de certificados.</span><span class="sxs-lookup"><span data-stu-id="17754-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="17754-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH**: (0x197) La CRL y los emisores del certificado no coincidían.</span><span class="sxs-lookup"><span data-stu-id="17754-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="17754-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED**: (0x198) La firma de la CRL no era válida.</span><span class="sxs-lookup"><span data-stu-id="17754-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="17754-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED**: (0x199) Se encontró el certificado que se está comprobando en la CRL y, por lo tanto, se ha revocado.</span><span class="sxs-lookup"><span data-stu-id="17754-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="17754-1455">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1455">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1456">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1456">Allowed From</span></span>

<span data-ttu-id="17754-1457">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1458">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1458">Example</span></span>

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="17754-1459">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1459">See Also</span></span>

- <span data-ttu-id="17754-1460">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1460">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1461">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1461">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="17754-1462">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="17754-1462">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="17754-1463">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="17754-1463">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="17754-1464">Inicializar una estructura de nombre DNS de X.509</span><span class="sxs-lookup"><span data-stu-id="17754-1464">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1465">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1465">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="17754-1466">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1466">Description</span></span>

<span data-ttu-id="17754-1467">Este servicio inicializa un nombre DNS de X.509 para su uso con determinados servicios de API que requieren un formato de nombre específico.</span><span class="sxs-lookup"><span data-stu-id="17754-1467">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="17754-1468">Por ejemplo, el servicio *nx_secure_tls_sni_extension_parse* espera un objeto NX_SECURE_X509_DNS_NAME para que coincida con el nombre proporcionado por un host remoto en la extensión de indicación de nombre de servidor durante el protocolo de enlace de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1468">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="17754-1469">Un nombre DNS es simplemente una cadena de caracteres con una longitud: la longitud máxima permitida de un nombre DNS (y el tamaño del búfer interno en NX_SECURE_X509_DNS_NAME) se controla mediante la macro NX_SECURE_X509_DNS_NAME_MAX (el valor predeterminado es de 100 bytes).</span><span class="sxs-lookup"><span data-stu-id="17754-1469">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1470">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1470">Parameters</span></span>

- <span data-ttu-id="17754-1471">**dns_name**: estructura de nombre DNS que se va a inicializar.</span><span class="sxs-lookup"><span data-stu-id="17754-1471">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="17754-1472">**name_string**: datos de la cadena del nombre DNS.</span><span class="sxs-lookup"><span data-stu-id="17754-1472">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="17754-1473">**length**: longitud de la cadena del nombre.</span><span class="sxs-lookup"><span data-stu-id="17754-1473">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1474">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1474">Return Values</span></span>

- <span data-ttu-id="17754-1475">**NX_SUCCESS**: (0x00) Inicialización correcta.</span><span class="sxs-lookup"><span data-stu-id="17754-1475">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="17754-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG**: (0x19E) La cadena de nombre especificada supera el valor de NX_SECURE_X509_DNS_NAME_MAX.</span><span class="sxs-lookup"><span data-stu-id="17754-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="17754-1477">**NX_PTR_ERROR**: (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1477">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1478">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1478">Allowed From</span></span>

<span data-ttu-id="17754-1479">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1480">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1480">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="17754-1481">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1481">See Also</span></span>

- <span data-ttu-id="17754-1482">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="17754-1482">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="17754-1483">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-1483">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="17754-1484">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="17754-1484">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="17754-1485">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-1485">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="17754-1486">Buscar y analizar una extensión de uso extendido de clave X.509 en un certificado X.509</span><span class="sxs-lookup"><span data-stu-id="17754-1486">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1487">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1487">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="17754-1488">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1488">Description</span></span>

<span data-ttu-id="17754-1489">Este servicio está diseñado para ser llamado desde una devolución de llamada de comprobación de certificado (consulte *nx_secure_tls_session_certificate_callback_set*).</span><span class="sxs-lookup"><span data-stu-id="17754-1489">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="17754-1490">Buscará un OID de uso extendido de clave específico dentro de un certificado X.509 y devolverá si el OID está presente.</span><span class="sxs-lookup"><span data-stu-id="17754-1490">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="17754-1491">El parámetro key_usage es una asignación de números enteros de los OID que X.509 y TLS de NetX Secure usan internamente para evitar pasar las cadenas de OID de longitud variable como parámetros.</span><span class="sxs-lookup"><span data-stu-id="17754-1491">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="17754-1492">Los OID correspondientes a la extensión de uso extendido de clave se proporcionan en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="17754-1492">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="17754-1493">Una implementación de cliente TLS típica que desee comprobar el uso extendido de clave en un certificado de servidor TLS recibido comprobará la existencia del OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH: si la extensión está presente pero ese OID no lo está, el certificado se considerará no válido para identificar el host como un servidor TLS y la devolución de llamada de comprobación del certificado debe devolver un error.</span><span class="sxs-lookup"><span data-stu-id="17754-1493">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="17754-1494">Si falta la propia extensión, depende de la aplicación si desea continuar con el protocolo de enlace de TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1494">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="17754-1495">En la devolución de llamada de comprobación del certificado, el código de retorno de error NX_SECURE_X509_KEY_USAGE_ERROR está reservado para el uso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="17754-1495">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="17754-1496">Si se produce un error al comprobar el uso de la clave, se puede devolver este valor desde la devolución de llamada para indicar el motivo del error.</span><span class="sxs-lookup"><span data-stu-id="17754-1496">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="17754-1497">Identificador de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1497">NetX Secure Identifier</span></span>                                | <span data-ttu-id="17754-1498">Valor de OID</span><span class="sxs-lookup"><span data-stu-id="17754-1498">OID Value</span></span>         | <span data-ttu-id="17754-1499">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1499">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="17754-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="17754-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="17754-1501">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="17754-1501">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="17754-1502">El certificado se puede usar para identificar un servidor TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1502">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="17754-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="17754-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="17754-1504">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="17754-1504">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="17754-1505">El certificado se puede usar para identificar un cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="17754-1505">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="17754-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="17754-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="17754-1507">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="17754-1507">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="17754-1508">El certificado se puede usar para firmar código.</span><span class="sxs-lookup"><span data-stu-id="17754-1508">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="17754-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="17754-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="17754-1510">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="17754-1510">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="17754-1511">El certificado se puede usar para firmar los mensajes de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="17754-1511">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="17754-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="17754-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="17754-1513">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="17754-1513">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="17754-1514">El certificado se puede usar para firmar las marcas de tiempo.</span><span class="sxs-lookup"><span data-stu-id="17754-1514">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="17754-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="17754-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="17754-1516">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="17754-1516">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="17754-1517">El certificado se puede usar para firmar las respuestas de OCSP.</span><span class="sxs-lookup"><span data-stu-id="17754-1517">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="17754-1518">OID y asignaciones para la extensión de uso extendido de clave X.509</span><span class="sxs-lookup"><span data-stu-id="17754-1518">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1519">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1519">Parameters</span></span>

- <span data-ttu-id="17754-1520">**certificate**: puntero al certificado que se está comprobando.</span><span class="sxs-lookup"><span data-stu-id="17754-1520">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="17754-1521">**key_usage**: asignación de números enteros de OID de la tabla anterior.</span><span class="sxs-lookup"><span data-stu-id="17754-1521">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1522">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1522">Return Values</span></span>

- <span data-ttu-id="17754-1523">**NX_SUCCESS**: (0x00) Se encontró el OID de uso de clave especificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1523">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="17754-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**: (0x181) Etiqueta ASN.1 de varios bytes detectada (certificado no admitido).</span><span class="sxs-lookup"><span data-stu-id="17754-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="17754-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**: (0x182) Se encontró el campo ASN.1 (certificado no válido).</span><span class="sxs-lookup"><span data-stu-id="17754-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="17754-1526">**NX_SECURE_X509_INVALID_TAG_CLASS**: (0x190) Se encontró una clase de etiqueta ASN.1 no válida (certificado no válido).</span><span class="sxs-lookup"><span data-stu-id="17754-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="17754-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**: (0x192) Se encontró una extensión no válida (certificado no válido).</span><span class="sxs-lookup"><span data-stu-id="17754-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="17754-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND**: (0x19B) No se encontró la extensión de uso de clave extendida en el certificado proporcionado.</span><span class="sxs-lookup"><span data-stu-id="17754-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="17754-1529">**NX_PTR_ERROR**: (0x07) Puntero de certificado no válido.</span><span class="sxs-lookup"><span data-stu-id="17754-1529">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1530">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1530">Allowed From</span></span>

<span data-ttu-id="17754-1531">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1532">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1532">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="17754-1533">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1533">See Also</span></span>

- <span data-ttu-id="17754-1534">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1534">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="17754-1535">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-1535">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="17754-1536">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="17754-1536">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="17754-1537">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="17754-1537">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="17754-1538">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="17754-1538">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="17754-1539">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="17754-1539">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="17754-1540">Buscar y devolver una extensión X.509 en un certificado X.509</span><span class="sxs-lookup"><span data-stu-id="17754-1540">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1541">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1541">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="17754-1542">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1542">Description</span></span>

<span data-ttu-id="17754-1543">Este servicio está diseñado para ser llamado desde una devolución de llamada de comprobación de certificado (consulte *nx_secure_tls_session_certificate_callback_set*) y es un servicio X.509 avanzado.</span><span class="sxs-lookup"><span data-stu-id="17754-1543">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="17754-1544">La función buscará una extensión específica dentro de un certificado X.509 en función de un OID y devolverá si el OID está presente, junto con una estructura que contiene referencias a los datos de la extensión sin procesar correspondientes.</span><span class="sxs-lookup"><span data-stu-id="17754-1544">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="17754-1545">El parámetro extension_id es una asignación de números enteros de los OID que X.509 y TLS de NetX Secure usan internamente para evitar pasar las cadenas de OID de longitud variable como parámetros.</span><span class="sxs-lookup"><span data-stu-id="17754-1545">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="17754-1546">Las funciones auxiliares proporcionadas para extensiones específicas (como *nx_secure_x509_key_usage_extension_parse*) llaman a nx_secure_x509_extension_find internamente para obtener los datos de la extensión.</span><span class="sxs-lookup"><span data-stu-id="17754-1546">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="17754-1547">Los OID correspondientes a las extensiones X.509 conocidas se proporcionan en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="17754-1547">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="17754-1548">La estructura NX_SECURE_X509_EXTENSION contiene punteros al certificado X.509 que permiten que funciones auxiliares, como *nx_secure_x509_key_usage_extension_parse*, descodifiquen rápidamente los datos sin procesar ASN.1 con codificación DER de la extensión.</span><span class="sxs-lookup"><span data-stu-id="17754-1548">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="17754-1549">Para obtener información sobre extensiones específicas, consulte el documento RFC 5280 (especificación X.509) o la referencia de las funciones auxiliares adecuadas, si está disponible.</span><span class="sxs-lookup"><span data-stu-id="17754-1549">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="17754-1550">La versión actual de X.509 de NetX Secure tiene compatibilidad limitada con las extensiones X.509.</span><span class="sxs-lookup"><span data-stu-id="17754-1550">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="17754-1551">En el futuro se agregarán más funciones auxiliares.</span><span class="sxs-lookup"><span data-stu-id="17754-1551">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="17754-1552">*Este servicio es una característica avanzada para los usuarios familiarizados con las extensiones X.509 y ASN.1 con codificación DER. Se proporciona para permitir que los usuarios accedan a las extensiones para las que X.509 de NetX Secure no proporciona funciones auxiliares en la actualidad. En el caso de las extensiones sin funciones auxiliares, tendrá que analizar los elementos ASN.1 sin procesar con codificación DER.*</span><span class="sxs-lookup"><span data-stu-id="17754-1552">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="17754-1553">Identificador de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1553">NetX Secure Identifier</span></span>                              | <span data-ttu-id="17754-1554">Valor de OID</span><span class="sxs-lookup"><span data-stu-id="17754-1554">OID Value</span></span> | <span data-ttu-id="17754-1555">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1555">Description</span></span>                                                                    | <span data-ttu-id="17754-1556">¿Función auxiliar?</span><span class="sxs-lookup"><span data-stu-id="17754-1556">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="17754-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="17754-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="17754-1558">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="17754-1558">2.5.29.9</span></span>  | <span data-ttu-id="17754-1559">Atributos de directorio: atributos de información básica acerca del firmante del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1559">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="17754-1560">No</span><span class="sxs-lookup"><span data-stu-id="17754-1560">No</span></span>               |
| <span data-ttu-id="17754-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="17754-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="17754-1562">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="17754-1562">2.5.29.14</span></span> | <span data-ttu-id="17754-1563">Se usa para identificar una clave pública específica.</span><span class="sxs-lookup"><span data-stu-id="17754-1563">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="17754-1564">No</span><span class="sxs-lookup"><span data-stu-id="17754-1564">No</span></span>               |
| <span data-ttu-id="17754-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="17754-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="17754-1566">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="17754-1566">2.5.29.15</span></span> | <span data-ttu-id="17754-1567">Proporciona información sobre los usos válidos de la clave pública del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1567">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="17754-1568">Sí</span><span class="sxs-lookup"><span data-stu-id="17754-1568">Yes</span></span>              |
| <span data-ttu-id="17754-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="17754-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="17754-1570">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="17754-1570">2.5.29.17</span></span> | <span data-ttu-id="17754-1571">Proporciona nombres DNS alternativos para identificar el certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1571">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="17754-1572">Sí<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="17754-1572">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="17754-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="17754-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="17754-1574">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="17754-1574">2.5.29.18</span></span> | <span data-ttu-id="17754-1575">Proporciona nombres DNS alternativos para identificar el emisor del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1575">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="17754-1576">No</span><span class="sxs-lookup"><span data-stu-id="17754-1576">No</span></span>               |
| <span data-ttu-id="17754-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="17754-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="17754-1578">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="17754-1578">2.5.29.19</span></span> | <span data-ttu-id="17754-1579">Proporciona información básica sobre las restricciones de uso del certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1579">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="17754-1580">No</span><span class="sxs-lookup"><span data-stu-id="17754-1580">No</span></span>               |
| <span data-ttu-id="17754-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="17754-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="17754-1582">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="17754-1582">2.5.29.30</span></span> | <span data-ttu-id="17754-1583">Se usa para restringir los nombres de certificado a dominios específicos.</span><span class="sxs-lookup"><span data-stu-id="17754-1583">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="17754-1584">No</span><span class="sxs-lookup"><span data-stu-id="17754-1584">No</span></span>               |
| <span data-ttu-id="17754-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="17754-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="17754-1586">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="17754-1586">2.5.29.31</span></span> | <span data-ttu-id="17754-1587">Proporciona los identificadores URI para la distribución de la CRL.</span><span class="sxs-lookup"><span data-stu-id="17754-1587">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="17754-1588">No</span><span class="sxs-lookup"><span data-stu-id="17754-1588">No</span></span>               |
| <span data-ttu-id="17754-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="17754-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="17754-1590">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="17754-1590">2.5.29.32</span></span> | <span data-ttu-id="17754-1591">Lista de directivas de certificados para sistemas PKI de gran tamaño.</span><span class="sxs-lookup"><span data-stu-id="17754-1591">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="17754-1592">No</span><span class="sxs-lookup"><span data-stu-id="17754-1592">No</span></span>               |
| <span data-ttu-id="17754-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="17754-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="17754-1594">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="17754-1594">2.5.29.33</span></span> | <span data-ttu-id="17754-1595">Lista de directivas de certificados de la entidad de certificación</span><span class="sxs-lookup"><span data-stu-id="17754-1595">List of CA certificate policies</span></span>                                                | <span data-ttu-id="17754-1596">No</span><span class="sxs-lookup"><span data-stu-id="17754-1596">No</span></span>               |
| <span data-ttu-id="17754-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="17754-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="17754-1598">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="17754-1598">2.5.29.35</span></span> | <span data-ttu-id="17754-1599">Se usa para identificar una clave pública específica asociada a una firma de certificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1599">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="17754-1600">No</span><span class="sxs-lookup"><span data-stu-id="17754-1600">No</span></span>               |
| <span data-ttu-id="17754-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="17754-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="17754-1602">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="17754-1602">2.5.29.36</span></span> | <span data-ttu-id="17754-1603">Restricciones de directivas de la CA</span><span class="sxs-lookup"><span data-stu-id="17754-1603">CA policy constraints</span></span>                                                          | <span data-ttu-id="17754-1604">No</span><span class="sxs-lookup"><span data-stu-id="17754-1604">No</span></span>               |
| <span data-ttu-id="17754-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="17754-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="17754-1606">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="17754-1606">2.5.29.37</span></span> | <span data-ttu-id="17754-1607">Información adicional sobre el uso de claves basado en OID.</span><span class="sxs-lookup"><span data-stu-id="17754-1607">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="17754-1608">Sí</span><span class="sxs-lookup"><span data-stu-id="17754-1608">Yes</span></span>              |
| <span data-ttu-id="17754-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="17754-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="17754-1610">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="17754-1610">2.5.29.46</span></span> | <span data-ttu-id="17754-1611">Proporciona información para obtener listas de revocación de certificados incrementales.</span><span class="sxs-lookup"><span data-stu-id="17754-1611">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="17754-1612">No</span><span class="sxs-lookup"><span data-stu-id="17754-1612">No</span></span>               |
| <span data-ttu-id="17754-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="17754-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="17754-1614">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="17754-1614">2.5.29.54</span></span> | <span data-ttu-id="17754-1615">Campo del certificado de la CA que indica que no se puede usar el elemento AnyPolicy.</span><span class="sxs-lookup"><span data-stu-id="17754-1615">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="17754-1616">No</span><span class="sxs-lookup"><span data-stu-id="17754-1616">No</span></span>               |

<span data-ttu-id="17754-1617">OID y asignaciones de las extensiones X.509</span><span class="sxs-lookup"><span data-stu-id="17754-1617">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="17754-1618">La extensión SubjectAltName se analiza como parte de la comprobación del nombre DNS en el servicio nx_secure_x509_common_name_dns_check.</span><span class="sxs-lookup"><span data-stu-id="17754-1618">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1619">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1619">Parameters</span></span>

- <span data-ttu-id="17754-1620">**certificate**: puntero al certificado que se está comprobando.</span><span class="sxs-lookup"><span data-stu-id="17754-1620">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="17754-1621">**extension**: estructura devuelta que contiene el puntero de datos de la extensión y la longitud.</span><span class="sxs-lookup"><span data-stu-id="17754-1621">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="17754-1622">**extension_id**: asignación de números enteros de OID de la tabla anterior.</span><span class="sxs-lookup"><span data-stu-id="17754-1622">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1623">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1623">Return Values</span></span>

- <span data-ttu-id="17754-1624">**NX_SUCCESS**: (0x00) Se encontró el OID de extensión especificado y se devuelven los datos.</span><span class="sxs-lookup"><span data-stu-id="17754-1624">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="17754-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**: (0x181) Etiqueta ASN.1 de varios bytes detectada (certificado no admitido).</span><span class="sxs-lookup"><span data-stu-id="17754-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="17754-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**: (0x182) Se encontró el campo ASN.1 (certificado no válido).</span><span class="sxs-lookup"><span data-stu-id="17754-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="17754-1627">**NX_SECURE_X509_INVALID_TAG_CLASS**: (0x190) Se encontró una clase de etiqueta ASN.1 no válida (certificado no válido).</span><span class="sxs-lookup"><span data-stu-id="17754-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="17754-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**: (0x192) Se encontró una extensión no válida.</span><span class="sxs-lookup"><span data-stu-id="17754-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="17754-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND**: (0x19B) No se encontró el OID de extensión especificado en el certificado proporcionado.</span><span class="sxs-lookup"><span data-stu-id="17754-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="17754-1630">**NX_PTR_ERROR**: (0x07) Puntero de extensión o certificado no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-1630">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1631">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1631">Allowed From</span></span>

<span data-ttu-id="17754-1632">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1632">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1633">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1633">Example</span></span>

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="17754-1634">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1634">See Also</span></span>

- <span data-ttu-id="17754-1635">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1635">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="17754-1636">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-1636">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="17754-1637">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="17754-1637">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="17754-1638">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="17754-1638">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="17754-1639">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-1639">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="17754-1640">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-1640">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="17754-1641">Buscar y analizar una extensión de uso de clave X.509 en un certificado X.509</span><span class="sxs-lookup"><span data-stu-id="17754-1641">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="17754-1642">Prototipo</span><span class="sxs-lookup"><span data-stu-id="17754-1642">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="17754-1643">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1643">Description</span></span>

<span data-ttu-id="17754-1644">Este servicio está diseñado para ser llamado desde una devolución de llamada de comprobación de certificado (consulte *nx_secure_tls_session_certificate_callback_set*).</span><span class="sxs-lookup"><span data-stu-id="17754-1644">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="17754-1645">Buscará la extensión de uso de clave y, si la encuentra, devolverá el campo de bits de uso de la clave en el parámetro "bitfield".</span><span class="sxs-lookup"><span data-stu-id="17754-1645">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="17754-1646">Los bits, tal y como se define en la especificación X.509 (RFC 5280), se indican en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="17754-1646">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="17754-1647">Una operación AND bit a bit con la máscara de bits adecuada (y comprobando que sea distinto de cero) proporcionará el valor de cada bit.</span><span class="sxs-lookup"><span data-stu-id="17754-1647">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="17754-1648">Tenga en cuenta que la codificación DER del campo de bits elimina los ceros adicionales, por lo que la posición real de los bits en los datos del certificado sin procesar probablemente será diferente de sus posiciones en el campo de bits descodificado.</span><span class="sxs-lookup"><span data-stu-id="17754-1648">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="17754-1649">Las máscaras de bits proporcionadas solo están pensadas para usarse en el campo de bits descodificado devuelto por *nx_secure_x509_key_usage_extension_parse* y no con los datos del certificado con codificación DER sin procesar.</span><span class="sxs-lookup"><span data-stu-id="17754-1649">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="17754-1650">En la devolución de llamada de comprobación del certificado, el código de retorno de error NX_SECURE_X509_KEY_USAGE_ERROR está reservado para el uso de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="17754-1650">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="17754-1651">Si se produce un error al comprobar el uso de la clave, se puede devolver este valor desde la devolución de llamada para indicar el motivo del error.</span><span class="sxs-lookup"><span data-stu-id="17754-1651">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="17754-1652">Identificador de NetX Secure</span><span class="sxs-lookup"><span data-stu-id="17754-1652">NetX Secure Identifier</span></span>                            | <span data-ttu-id="17754-1653">Posición de bit</span><span class="sxs-lookup"><span data-stu-id="17754-1653">Bit position</span></span> | <span data-ttu-id="17754-1654">Descripción</span><span class="sxs-lookup"><span data-stu-id="17754-1654">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="17754-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="17754-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="17754-1656">0</span><span class="sxs-lookup"><span data-stu-id="17754-1656">0</span></span>            | <span data-ttu-id="17754-1657">El certificado se puede utilizar para firmas digitales.</span><span class="sxs-lookup"><span data-stu-id="17754-1657">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="17754-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="17754-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="17754-1659">1</span><span class="sxs-lookup"><span data-stu-id="17754-1659">1</span></span>            | <span data-ttu-id="17754-1660">El certificado se puede usar para comprobar firmas digitales distintas de las de certificados y CRL.</span><span class="sxs-lookup"><span data-stu-id="17754-1660">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="17754-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="17754-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="17754-1662">2</span><span class="sxs-lookup"><span data-stu-id="17754-1662">2</span></span>            | <span data-ttu-id="17754-1663">El certificado se puede usar para cifrar claves simétricas (transporte de claves).</span><span class="sxs-lookup"><span data-stu-id="17754-1663">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="17754-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="17754-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="17754-1665">3</span><span class="sxs-lookup"><span data-stu-id="17754-1665">3</span></span>            | <span data-ttu-id="17754-1666">El certificado se puede usar para cifrar directamente los datos de usuario sin procesar (poco frecuente).</span><span class="sxs-lookup"><span data-stu-id="17754-1666">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="17754-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="17754-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="17754-1668">4</span><span class="sxs-lookup"><span data-stu-id="17754-1668">4</span></span>            | <span data-ttu-id="17754-1669">El certificado se puede usar para el contrato de claves (como con Diffie-Hellman).</span><span class="sxs-lookup"><span data-stu-id="17754-1669">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="17754-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="17754-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="17754-1671">5</span><span class="sxs-lookup"><span data-stu-id="17754-1671">5</span></span>            | <span data-ttu-id="17754-1672">El certificado se puede usar para firmar y comprobar otros certificados (el certificado es un certificado CA o ICA).</span><span class="sxs-lookup"><span data-stu-id="17754-1672">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="17754-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="17754-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="17754-1674">6</span><span class="sxs-lookup"><span data-stu-id="17754-1674">6</span></span>            | <span data-ttu-id="17754-1675">La clave pública del certificado se usa para comprobar las firmas en las CRL.</span><span class="sxs-lookup"><span data-stu-id="17754-1675">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="17754-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="17754-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="17754-1677">7</span><span class="sxs-lookup"><span data-stu-id="17754-1677">7</span></span>            | <span data-ttu-id="17754-1678">Se utiliza con el bit de contrato de claves (bit 4): cuando se establece, la clave de certificado solo se puede usar para cifrar durante el acuerdo de claves.</span><span class="sxs-lookup"><span data-stu-id="17754-1678">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="17754-1679">Indefinido si no se establece el bit de contrato de claves.</span><span class="sxs-lookup"><span data-stu-id="17754-1679">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="17754-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="17754-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="17754-1681">8</span><span class="sxs-lookup"><span data-stu-id="17754-1681">8</span></span>            | <span data-ttu-id="17754-1682">Se utiliza con el bit de contrato de claves (bit 4): cuando se establece, la clave de certificado solo se puede usar para descifrar durante el acuerdo de claves.</span><span class="sxs-lookup"><span data-stu-id="17754-1682">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="17754-1683">Indefinido si no se establece el bit de contrato de claves.</span><span class="sxs-lookup"><span data-stu-id="17754-1683">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="17754-1684">Máscaras de bits y valores de la extensión de uso de clave X.509</span><span class="sxs-lookup"><span data-stu-id="17754-1684">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="17754-1685">Parámetros</span><span class="sxs-lookup"><span data-stu-id="17754-1685">Parameters</span></span>

- <span data-ttu-id="17754-1686">**certificate**: puntero al certificado que se está comprobando.</span><span class="sxs-lookup"><span data-stu-id="17754-1686">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="17754-1687">**bitfield**: devuelve el campo de bits completo de la extensión.</span><span class="sxs-lookup"><span data-stu-id="17754-1687">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="17754-1688">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="17754-1688">Return Values</span></span>

- <span data-ttu-id="17754-1689">**NX_SUCCESS**: (0x00) Se encontró la extensión de uso de clave y se devuelve el campo de bits.</span><span class="sxs-lookup"><span data-stu-id="17754-1689">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="17754-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED**: (0x181) Etiqueta ASN.1 de varios bytes detectada (certificado no admitido).</span><span class="sxs-lookup"><span data-stu-id="17754-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="17754-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG**: (0x182) Se encontró el campo ASN.1 (certificado no válido).</span><span class="sxs-lookup"><span data-stu-id="17754-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="17754-1692">**NX_SECURE_X509_INVALID_TAG_CLASS**: (0x190) Se encontró una clase de etiqueta ASN.1 no válida (certificado no válido).</span><span class="sxs-lookup"><span data-stu-id="17754-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="17754-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE**: (0x192) Se encontró una extensión no válida (certificado no válido).</span><span class="sxs-lookup"><span data-stu-id="17754-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="17754-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND**: (0x19B) No se encontró la extensión de uso de clave en el certificado proporcionado.</span><span class="sxs-lookup"><span data-stu-id="17754-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="17754-1695">**NX_PTR_ERROR**: (0x07) Puntero de campo de bits o certificado no válidos.</span><span class="sxs-lookup"><span data-stu-id="17754-1695">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17754-1696">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="17754-1696">Allowed From</span></span>

<span data-ttu-id="17754-1697">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="17754-1697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17754-1698">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="17754-1698">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="17754-1699">Consulte también</span><span class="sxs-lookup"><span data-stu-id="17754-1699">See Also</span></span>

- <span data-ttu-id="17754-1700">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="17754-1700">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="17754-1701">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="17754-1701">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="17754-1702">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="17754-1702">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="17754-1703">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="17754-1703">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="17754-1704">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="17754-1704">nx_secure_x509_extension_find</span></span>
