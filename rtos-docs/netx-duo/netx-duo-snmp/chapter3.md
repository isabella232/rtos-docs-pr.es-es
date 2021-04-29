---
title: 'Capítulo 3: Descripción de los servicios del agente SNMP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del agente SNMP de NetX Duo (se enumeran a continuación) por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814565"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a><span data-ttu-id="8b2f2-103">Capítulo 3: Descripción de los servicios del agente SNMP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-103">Chapter 3 - Description of Azure RTOS NetX Duo SNMP agent services</span></span>

<span data-ttu-id="8b2f2-104">Este capítulo contiene una descripción de todos los servicios del agente SNMP de Azure RTOS NetX Duo (se enumeran a continuación) por orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-104">This chapter contains a description of all Azure RTOS NetX Duo SNMP agent services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="8b2f2-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="8b2f2-106">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="8b2f2-106">nx_snmp_agent_auth_trap_key_use</span></span>](#nx_snmp_agent_auth_trap_key_use)
   - <span data-ttu-id="8b2f2-107">*Especificar la clave de autenticación (solo SNMP v3) para los mensajes de captura*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-107">*Specify authentication key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="8b2f2-108">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="8b2f2-108">nx_snmp_agent_authenticate_key_use</span></span>](#nx_snmp_agent_authenticate_key_use)
   - <span data-ttu-id="8b2f2-109">*Especificar la clave de autenticación (solo SNMP v3) para los mensajes de respuesta*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-109">*Specify authentication key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="8b2f2-110">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-110">nx_snmp_agent_community_get</span></span>](#nx_snmp_agent_community_get)
   - <span data-ttu-id="8b2f2-111">*Recuperar el nombre de la comunidad*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-111">*Retrieve community name*</span></span>
- [<span data-ttu-id="8b2f2-112">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-112">nx_snmp_agent_context_engine_set</span></span>](#nx_snmp_agent_context_engine_set)
   - <span data-ttu-id="8b2f2-113">*Establecer el motor de contexto (solo SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-113">*Set context engine (SNMP v3 only)*</span></span>
- [<span data-ttu-id="8b2f2-114">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-114">nx_snmp_agent_context_name_set</span></span>](#nx_snmp_agent_context_name_set)
   - <span data-ttu-id="8b2f2-115">*Establecer el nombre del contexto (solo SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-115">*Set context name (SNMP v3 only)*</span></span>
- [<span data-ttu-id="8b2f2-116">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="8b2f2-116">nx_snmp_agent_create</span></span>](#nx_snmp_agent_create)
   - <span data-ttu-id="8b2f2-117">*Crear agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-117">*Create SNMP agent*</span></span>
- [<span data-ttu-id="8b2f2-118">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-118">nx_snmp_agent_current_version_get</span></span>](#nx_snmp_agent_current_version_get)
   - <span data-ttu-id="8b2f2-119">*Obtener la versión de SNMP del paquete recibido*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-119">*Get the SNMP version of received packet*</span></span>
- [<span data-ttu-id="8b2f2-120">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="8b2f2-120">nx_snmp_agent_request_get_type_test</span></span>](#nx_snmp_agent_request_get_type_test)
   - <span data-ttu-id="8b2f2-121">*Indicar si la última solicitud SNMP es de tipo GET o SET*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-121">*Indicate if last SNMP request is GET or SET type*</span></span>
- [<span data-ttu-id="8b2f2-122">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="8b2f2-122">nx_snmp_agent_private_string_test</span></span>](#nx_snmp_agent_private_string_test)
   - <span data-ttu-id="8b2f2-123">*Determinar si la cadena coincide con la cadena privada del agente*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-123">*Determine if string matches agent private string*</span></span>
- [<span data-ttu-id="8b2f2-124">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="8b2f2-124">nx_snmp_agent_public_string_test</span></span>](#nx_snmp_agent_public_string_test)
   - <span data-ttu-id="8b2f2-125">*Determinar si la cadena coincide con la cadena pública del agente*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-125">*Determine if string matches agent public string*</span></span>
- [<span data-ttu-id="8b2f2-126">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="8b2f2-126">nx_snmp_agent_set_interface</span></span>](#nx_snmp_agent_set_interface)
   - <span data-ttu-id="8b2f2-127">*Establecer la interfaz de red para la mensajería SNMP*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-127">*Set network interface for SNMP messaging*</span></span>
- [<span data-ttu-id="8b2f2-128">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-128">nx_snmp_agent_private_string_set</span></span>](#nx_snmp_agent_private_string_set)
   - <span data-ttu-id="8b2f2-129">*Establecer la cadena de comunidad privada del agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-129">*Set the SNMP agent private community string*</span></span>
- [<span data-ttu-id="8b2f2-130">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-130">nx_snmp_agent_public_string_set</span></span>](#nx_snmp_agent_public_string_set)
   - <span data-ttu-id="8b2f2-131">*Establecer la cadena de comunidad pública del agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-131">*Set the SNMP agent public community string*</span></span>
- [<span data-ttu-id="8b2f2-132">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-132">nx_snmp_agent_version_set</span></span>](#nx_snmp_agent_version_set)
   - <span data-ttu-id="8b2f2-133">*Establecer el estado del agente SNMP para todas las versiones de SNMP*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-133">*Set the SNMP agent status for all SNMP versions*</span></span>
- [<span data-ttu-id="8b2f2-134">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="8b2f2-134">nx_snmp_agent_delete</span></span>](#nx_snmp_agent_delete)
   - <span data-ttu-id="8b2f2-135">*Eliminar el agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-135">*Delete SNMP agent*</span></span>
- [<span data-ttu-id="8b2f2-136">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="8b2f2-136">nx_snmp_agent_md5_key_create</span></span>](#nx_snmp_agent_md5_key_create)
   - <span data-ttu-id="8b2f2-137">*Crear clave MD5 (solo SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-137">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="8b2f2-138">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="8b2f2-138">nx_snmp_agent_md5_key_create_extended</span></span>](#nx_snmp_agent_md5_key_create_extended)
   - <span data-ttu-id="8b2f2-139">*Crear clave MD5 (solo SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-139">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="8b2f2-140">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="8b2f2-140">nx_snmp_agent_priv_trap_key_use</span></span>](#nx_snmp_agent_priv_trap_key_use)
   - <span data-ttu-id="8b2f2-141">*Especificar la clave de cifrado (solo SNMP v3) para los mensajes de captura*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-141">*Specify encryption key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="8b2f2-142">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="8b2f2-142">nx_snmp_agent_privacy_key_use</span></span>](#nx_snmp_agent_privacy_key_use)
   - <span data-ttu-id="8b2f2-143">*Especificar la clave de cifrado (solo SNMP v3) para los mensajes de respuesta*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-143">*Specify encryption key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="8b2f2-144">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="8b2f2-144">nx_snmp_agent_sha_key_create</span></span>](#nx_snmp_agent_sha_key_create)
   - <span data-ttu-id="8b2f2-145">*Crear clave SHA (solo SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-145">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="8b2f2-146">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="8b2f2-146">nx_snmp_agent_sha_key_create_extended</span></span>](#nx_snmp_agent_sha_key_create_extended)
   - <span data-ttu-id="8b2f2-147">*Crear clave SHA (solo SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-147">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="8b2f2-148">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="8b2f2-148">nx_snmp_agent_start</span></span>](#nx_snmp_agent_start)
   - <span data-ttu-id="8b2f2-149">*Iniciar el agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-149">*Start SNMP agent*</span></span>
- [<span data-ttu-id="8b2f2-150">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="8b2f2-150">nx_snmp_agent_stop</span></span>](#nx_snmp_agent_stop)
   - <span data-ttu-id="8b2f2-151">*Detener el agente SNMP*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-151">*Stop SNMP agent*</span></span>
- [<span data-ttu-id="8b2f2-152">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-152">nx_snmp_agent_trap_send</span></span>](#nx_snmp_agent_trap_send)
   - <span data-ttu-id="8b2f2-153">*Enviar captura de SNMP v1 (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-153">*Send SNMP v1 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="8b2f2-154">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-154">nx_snmp_agent_trapv2_send</span></span>](#nx_snmp_agent_trapv2_send)
   - <span data-ttu-id="8b2f2-155">*Enviar captura de SNMP v2 (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-155">*Send SNMP v2 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="8b2f2-156">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-156">nx_snmp_agent_trapv2_oid_send</span></span>](#nx_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="8b2f2-157">*Enviar captura de SNMP v2 (solo IPv4) especificando el OID*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-157">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="8b2f2-158">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-158">nx_snmp_agent_trapv3_send</span></span>](#nx_snmp_agent_trapv3_send)
   - <span data-ttu-id="8b2f2-159">*Enviar captura de SNMP v3 (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-159">*Send SNMP v3 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="8b2f2-160">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-160">nx_snmp_agent_trapv3_oid_send</span></span>](#nx_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="8b2f2-161">*Enviar captura de SNMP v2 (solo IPv4) especificando el OID*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-161">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="8b2f2-162">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-162">nxd_snmp_agent_trap_send</span></span>](#nxd_snmp_agent_trap_send)
   - <span data-ttu-id="8b2f2-163">*Enviar captura de SNMP v1 (IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-163">*Send SNMP v1 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="8b2f2-164">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-164">nxd_snmp_agent_trapv2_send</span></span>](#nxd_snmp_agent_trapv2_send)
   - <span data-ttu-id="8b2f2-165">*Enviar captura de SNMP v2 (IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-165">*Send SNMP v2 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="8b2f2-166">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-166">nxd_snmp_agent_trapv2_oid_send</span></span>](#nxd_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="8b2f2-167">*Enviar captura de SNMP v2 (IPv4 e IPv6) especificando el OID*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-167">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="8b2f2-168">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-168">nxd_snmp_agent_trapv3_send</span></span>](#nxd_snmp_agent_trapv3_send)
   - <span data-ttu-id="8b2f2-169">*Enviar captura de SNMP v3 (IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-169">*Send SNMP v3 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="8b2f2-170">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-170">nxd_snmp_agent_trapv3_oid_send</span></span>](#nxd_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="8b2f2-171">*Enviar captura de SNMP v2 (IPv4 e IPv6) especificando el OID*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-171">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="8b2f2-172">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-172">nx_snmp_agent_v3_context_boots_set</span></span>](#nx_snmp_agent_v3_context_boots_set)
   - <span data-ttu-id="8b2f2-173">*Establecer el número de reinicios*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-173">*Set the number of reboots*</span></span>
- [<span data-ttu-id="8b2f2-174">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="8b2f2-174">nx_snmp_object_compare</span></span>](#nx_snmp_object_compare)
   - <span data-ttu-id="8b2f2-175">*Comparar dos objetos*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-175">*Compare two objects*</span></span>
- [<span data-ttu-id="8b2f2-176">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="8b2f2-176">nx_snmp_object_compare_extended</span></span>](#nx_snmp_object_compare_extended)
   - <span data-ttu-id="8b2f2-177">*Comparar dos objetos*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-177">*Compare two objects*</span></span>
- [<span data-ttu-id="8b2f2-178">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="8b2f2-178">nx_snmp_object_copy</span></span>](#nx_snmp_object_copy)
   - <span data-ttu-id="8b2f2-179">*Copia de un objeto*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-179">*Copy an object*</span></span>
- [<span data-ttu-id="8b2f2-180">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="8b2f2-180">nx_snmp_object_copy_extended</span></span>](#nx_snmp_object_copy_extended)
   - <span data-ttu-id="8b2f2-181">*Copia de un objeto*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-181">*Copy an object*</span></span>
- [<span data-ttu-id="8b2f2-182">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-182">nx_snmp_object_counter_get</span></span>](#nx_snmp_object_counter_get)
   - <span data-ttu-id="8b2f2-183">*Obtener objeto de contador*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-183">*Get counter object*</span></span>
- [<span data-ttu-id="8b2f2-184">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-184">nx_snmp_object_counter_set</span></span>](#nx_snmp_object_counter_set)
   - <span data-ttu-id="8b2f2-185">*Establecer objeto de contador*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-185">*Set counter object*</span></span>
- [<span data-ttu-id="8b2f2-186">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-186">nx_snmp_object_counter64_get</span></span>](#nx_snmp_object_counter64_get)
   - <span data-ttu-id="8b2f2-187">*Obtener objeto de contador de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-187">*Get 64-bit counter object*</span></span>
- [<span data-ttu-id="8b2f2-188">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-188">nx_snmp_object_counter64_set</span></span>](#nx_snmp_object_counter64_set)
   - <span data-ttu-id="8b2f2-189">*Establecer objeto de contador de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-189">*Set 64-bit counter object*</span></span>
- [<span data-ttu-id="8b2f2-190">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="8b2f2-190">nx_snmp_object_end_of_mib</span></span>](#nx_snmp_object_end_of_mib)
   - <span data-ttu-id="8b2f2-191">*Establecer el valor de final de MIB*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-191">*Set end-of-mib value*</span></span>
- [<span data-ttu-id="8b2f2-192">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-192">nx_snmp_object_gauge_get</span></span>](#nx_snmp_object_gauge_get)
   - <span data-ttu-id="8b2f2-193">*Obtener objeto de medidor*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-193">*Get gauge object*</span></span>
- [<span data-ttu-id="8b2f2-194">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-194">nx_snmp_object_gauge_set</span></span>](#nx_snmp_object_gauge_set)
   - <span data-ttu-id="8b2f2-195">*Establecer objeto de medidor*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-195">*Set gauge object*</span></span>
- [<span data-ttu-id="8b2f2-196">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-196">nx_snmp_object_id_get</span></span>](#nx_snmp_object_id_get)
   - <span data-ttu-id="8b2f2-197">*Obtener el identificador de objeto*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-197">*Get object id*</span></span>
- [<span data-ttu-id="8b2f2-198">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-198">nx_snmp_object_id_set</span></span>](#nx_snmp_object_id_set)
   - <span data-ttu-id="8b2f2-199">*Establecer el identificador de objeto*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-199">*Set object id*</span></span>
- [<span data-ttu-id="8b2f2-200">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-200">nx_snmp_object_integer_get</span></span>](#nx_snmp_object_integer_get)
   - <span data-ttu-id="8b2f2-201">*Obtener objeto de número entero*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-201">*Get integer object*</span></span>
- [<span data-ttu-id="8b2f2-202">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-202">nx_snmp_object_integer_set</span></span>](#nx_snmp_object_integer_set)
   - <span data-ttu-id="8b2f2-203">*Establecer objeto de número entero*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-203">*Set integer object*</span></span>
- [<span data-ttu-id="8b2f2-204">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-204">nx_snmp_object_ip_address_get</span></span>](#nx_snmp_object_ip_address_get)
   - <span data-ttu-id="8b2f2-205">*Obtener objeto de dirección IP (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-205">*Get IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="8b2f2-206">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-206">nx_snmp_object_ip_address_set</span></span>](#nx_snmp_object_ip_address_set)
   - <span data-ttu-id="8b2f2-207">*Establecer objeto de dirección IP (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-207">*Set IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="8b2f2-208">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-208">nx_snmp_object_ipv6_address_get</span></span>](#nx_snmp_object_ipv6_address_get)
   - <span data-ttu-id="8b2f2-209">*Obtener objeto de dirección IP (solo IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-209">*Get IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="8b2f2-210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-210">nx_snmp_object_ipv6_address_set</span></span>](#nx_snmp_object_ipv6_address_set)
   - <span data-ttu-id="8b2f2-211">*Establecer objeto de dirección IP (solo IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-211">*Set IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="8b2f2-212">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="8b2f2-212">nx_snmp_object_no_instance</span></span>](#nx_snmp_object_no_instance)
   - <span data-ttu-id="8b2f2-213">*Establecer el valor "no hay instancia"*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-213">*Set no-instance value*</span></span>
- [<span data-ttu-id="8b2f2-214">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="8b2f2-214">nx_snmp_object_not_found</span></span>](#nx_snmp_object_not_found)
   - <span data-ttu-id="8b2f2-215">*Establecer el valor "no encontrado"*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-215">*Set not-found value*</span></span>
- [<span data-ttu-id="8b2f2-216">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-216">nx_snmp_object_octet_string_get</span></span>](#nx_snmp_object_octet_string_get)
   - <span data-ttu-id="8b2f2-217">*Obtener objeto de cadena de octetos*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-217">*Get octet string object*</span></span>
- [<span data-ttu-id="8b2f2-218">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-218">nx_snmp_object_octet_string_set</span></span>](#nx_snmp_object_octet_string_set)
   - <span data-ttu-id="8b2f2-219">*Establecer objeto de cadena de octetos*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-219">*Set octet string object*</span></span>
- [<span data-ttu-id="8b2f2-220">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-220">nx_snmp_object_string_get</span></span>](#nx_snmp_object_string_get)
   - <span data-ttu-id="8b2f2-221">*Obtener objeto de cadena ASCII*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-221">*Get ASCII string object*</span></span>
- [<span data-ttu-id="8b2f2-222">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-222">nx_snmp_object_string_set</span></span>](#nx_snmp_object_string_set)
   - <span data-ttu-id="8b2f2-223">*Establecer objeto de cadena ASCII*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-223">*Set ASCII string object*</span></span>
- [<span data-ttu-id="8b2f2-224">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-224">nx_snmp_object_timetics_get</span></span>](#nx_snmp_object_timetics_get)
   - <span data-ttu-id="8b2f2-225">*Obtener objeto timetics*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-225">*Get timetics object*</span></span>
- [<span data-ttu-id="8b2f2-226">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-226">nx_snmp_object_timetics_set</span></span>](#nx_snmp_object_timetics_set)
   - <span data-ttu-id="8b2f2-227">*Establecer objeto timetics*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-227">*Set timetics object*</span></span>

## <a name="nx_snmp_agent_auth_trap_key_use"></a><span data-ttu-id="8b2f2-228">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="8b2f2-228">nx_snmp_agent_auth_trap_key_use</span></span>
<span data-ttu-id="8b2f2-229">Especificar la clave de autenticación para los mensajes de captura</span><span class="sxs-lookup"><span data-stu-id="8b2f2-229">Specify authentication key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-230">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-230">Prototype</span></span>

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="8b2f2-231">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-231">Description</span></span>

<span data-ttu-id="8b2f2-232">Este servicio especifica la clave que se va a usar para establecer los parámetros de autenticación en el encabezado de seguridad SNMP v3 en los mensajes de captura.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-232">This service specifies the key to be used for setting authentication parameters in the SNMPv3 security header in trap messages.</span></span> <span data-ttu-id="8b2f2-233">Al proporcionar un valor NX_NULL para la clave, se deshabilita la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-233">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="8b2f2-234">La clave se debe crear previamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-234">The key must be previously created.</span></span> <span data-ttu-id="8b2f2-235">Consulte nx_snmp_agent_md5_key_create o nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-235">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-236">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-236">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-237">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-237">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-238">**key** Puntero a una clave MD5 o SHA creada previamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-238">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-239">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-239">Return Values</span></span>

- <span data-ttu-id="8b2f2-240">**NX_SUCCESS** (0x00) Conjunto de claves de autenticación correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-240">**NX_SUCCESS** (0x00) Successful authentication key set.</span></span>
- <span data-ttu-id="8b2f2-241">**NX_NOT_ENABLED** (0x14) La seguridad de SNMP está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-241">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span> 
- <span data-ttu-id="8b2f2-242">**NX_PTR_ERROR** (0x07) Puntero del agente SNMP no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-242">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-243">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-243">Allowed From</span></span>

<span data-ttu-id="8b2f2-244">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-244">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-245">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-245">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a><span data-ttu-id="8b2f2-246">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="8b2f2-246">nx_snmp_agent_authenticate_key_use</span></span>
<span data-ttu-id="8b2f2-247">Especificar la clave de autenticación para los mensajes de respuesta</span><span class="sxs-lookup"><span data-stu-id="8b2f2-247">Specify authentication key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-248">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-248">Prototype</span></span>

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="8b2f2-249">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-249">Description</span></span>

<span data-ttu-id="8b2f2-250">Este servicio especifica la clave que se va a usar para los parámetros de autenticación en el parámetro de seguridad de SNMP v3 para todas las solicitudes realizadas una vez establecido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-250">This service specifies the key to be used for authentication parameters in the SNMPv3 security parameter for all requests made after it is set.</span></span> <span data-ttu-id="8b2f2-251">Al proporcionar un valor NX_NULL para la clave, se deshabilita la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-251">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="8b2f2-252">La clave se debe crear previamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-252">The key must be previously created.</span></span> <span data-ttu-id="8b2f2-253">Consulte nx_snmp_agent_md5_key_create o nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-253">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-254">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-254">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-255">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-255">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-256">**key** Puntero a una clave MD5 o SHA creada previamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-256">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-257">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-257">Return Values</span></span>

- <span data-ttu-id="8b2f2-258">**NX_SUCCESS** (0x00) Conjunto de claves de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-258">**NX_SUCCESS** (0x00) Successful SNMP key set.</span></span>
- <span data-ttu-id="8b2f2-259">**NX_NOT_ENABLED** (0x14) La seguridad de SNMP está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-259">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span>
- <span data-ttu-id="8b2f2-260">**NX_PTR_ERROR** (0x07) Puntero del agente SNMP no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-260">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-261">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-261">Allowed From</span></span>

<span data-ttu-id="8b2f2-262">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-262">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-263">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-263">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a><span data-ttu-id="8b2f2-264">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-264">nx_snmp_agent_community_get</span></span>
<span data-ttu-id="8b2f2-265">Recuperar el nombre de la comunidad</span><span class="sxs-lookup"><span data-stu-id="8b2f2-265">Retrieve community name</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-266">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-266">Prototype</span></span>

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a><span data-ttu-id="8b2f2-267">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-267">Description</span></span>

<span data-ttu-id="8b2f2-268">Este servicio recupera el nombre de la comunidad de la solicitud SNMP más reciente recibida por el agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-268">This service retrieves the community name from the most recent SNMP request received by the SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-269">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-269">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-270">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-270">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-271">**community_string_ptr** Puntero a un puntero de cadena para devolver la cadena de la comunidad del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-271">**community_string_ptr** Pointer to a string pointer to return the SNMP Agent community string.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-272">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-272">Return Values</span></span>

- <span data-ttu-id="8b2f2-273">**NX_SUCCESS** (0x00) Obtención correcta de la comunidad de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-273">**NX_SUCCESS** (0x00) Successful SNMP community get.</span></span>
- <span data-ttu-id="8b2f2-274">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-274">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-275">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-275">Allowed From</span></span>

<span data-ttu-id="8b2f2-276">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-276">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-277">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-277">Example</span></span>

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a><span data-ttu-id="8b2f2-278">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="8b2f2-278">nx_snmp_agent_request_get_type_test</span></span>
<span data-ttu-id="8b2f2-279">Indicar si la última solicitud SNMP es de tipo GET o SET</span><span class="sxs-lookup"><span data-stu-id="8b2f2-279">Indicate if last SNMP request is GET or SET type</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-280">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-280">Prototype</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a><span data-ttu-id="8b2f2-281">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-281">Description</span></span>

<span data-ttu-id="8b2f2-282">Este servicio indica si la solicitud más reciente del administrador de SNMP es de tipo GET (GET, GETNEXT o GETBULK) o de tipo SET.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-282">This service indicates if the most recent request from the SNMP Manager is a GET (GET, GETNEXT, or GETBULK) or SET type.</span></span> <span data-ttu-id="8b2f2-283">Está pensada para su uso con la devolución de llamada de nombre de usuario, donde la aplicación SNMP v1 o SNMP v2 querrá comparar la cadena de la comunidad recibida con la cadena pública del agente SNMP si la solicitud es un tipo GET o con la cadena privada del agente SNMP si la solicitud es de tipo SET.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-283">It is intended for use with the username callback where the SNMPv1 or SNMPv2 application will want to compare the received community string to the SNMP Agent public string if the request is a GET type, or to the SNMP Agent private string if the request is a SET type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-284">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-284">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-285">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-285">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-286">**is_get_type** Puntero al estado del tipo de solicitud:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-286">**is_get_type** Pointer to request type status:</span></span>  
<span data-ttu-id="8b2f2-287">NX_TRUE si es de tipo GET</span><span class="sxs-lookup"><span data-stu-id="8b2f2-287">NX_TRUE if GET type</span></span>  
<span data-ttu-id="8b2f2-288">NX_FALSE si es de tipo SET</span><span class="sxs-lookup"><span data-stu-id="8b2f2-288">NX_FALSE if SET type</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-289">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-289">Return Values</span></span>

- <span data-ttu-id="8b2f2-290">**NX_SUCCESS** (0x00) Tipo devuelto correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-290">**NX_SUCCESS** (0x00) Successfully returned type</span></span>
- <span data-ttu-id="8b2f2-291">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-291">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-292">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-292">Allowed From</span></span>

<span data-ttu-id="8b2f2-293">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-293">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-294">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-294">Example</span></span>

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a><span data-ttu-id="8b2f2-295">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-295">nx_snmp_agent_context_engine_set</span></span>
<span data-ttu-id="8b2f2-296">Establecer el motor de contexto (solo SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-296">Set context engine (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-297">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-297">Prototype</span></span>

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a><span data-ttu-id="8b2f2-298">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-298">Description</span></span>

<span data-ttu-id="8b2f2-299">Este servicio establece el motor de contexto del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-299">This service sets the context engine of the SNMP Agent.</span></span> <span data-ttu-id="8b2f2-300">Solo es aplicable para el procesamiento de SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-300">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="8b2f2-301">Se debe llamar a este servicio antes de crear claves de seguridad si la aplicación usa autenticación y cifrado, ya que el identificador del motor de contexto se usa en el proceso de creación de claves.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-301">This should be called before creating security keys if the application is using authentication and encryption, since the context engine ID is used in the key creation process.</span></span> <span data-ttu-id="8b2f2-302">En caso contrario, SNMP de NetX Duo proporciona un identificador de motor de contexto predeterminado en la parte superior del archivo *nxd_snmp.c:*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-302">If not, NetX Duo SNMP provides a default context engine id at the top of *nxd_snmp.c:*</span></span>

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-303">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-303">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-304">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-304">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-305">**context_engine** Puntero a la cadena del motor de contexto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-305">**context_engine** Pointer to the context engine string.</span></span>
- <span data-ttu-id="8b2f2-306">**context_engine_size** Tamaño de la cadena del motor de contexto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-306">**context_engine_size** Size of context engine string.</span></span> <span data-ttu-id="8b2f2-307">Tenga en cuenta que el número máximo de bytes en un motor de contexto se define mediante NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-307">Note that the maximum number of bytes in a context engine is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-308">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-308">Return Values</span></span>

- <span data-ttu-id="8b2f2-309">**NX_SUCCESS** (0x00) Se ha establecido correctamente el motor de contexto de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-309">**NX_SUCCESS** (0x00) Successful SNMP context engine set.</span></span>
- <span data-ttu-id="8b2f2-310">**NX_NOT_ENABLED** (0x14) SNMP v3 no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-310">**NX_NOT_ENABLED** (0x14) SNMPv3 is not enabled</span></span>
- <span data-ttu-id="8b2f2-311">**NX_SNMP_ERROR** (0x100) Error de tamaño del motor de contexto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-311">**NX_SNMP_ERROR** (0x100) Context engine size error.</span></span>
- <span data-ttu-id="8b2f2-312">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-312">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-313">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-313">Allowed From</span></span>

<span data-ttu-id="8b2f2-314">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-314">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-315">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-315">Example</span></span>

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a><span data-ttu-id="8b2f2-316">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-316">nx_snmp_agent_context_name_set</span></span>
<span data-ttu-id="8b2f2-317">Establecer el nombre del contexto (solo SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-317">Set context name (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-318">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-318">Prototype</span></span>

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a><span data-ttu-id="8b2f2-319">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-319">Description</span></span>

<span data-ttu-id="8b2f2-320">Este servicio establece el nombre del contexto del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-320">This service sets the context name of the SNMP Agent.</span></span> <span data-ttu-id="8b2f2-321">Solo es aplicable para el procesamiento de SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-321">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="8b2f2-322">Si no se le llama, el agente SNMP de NetX Duo dejará el nombre de contexto en blanco.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-322">If not called, NetX Duo SNMP Agent will leave the context name blank.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-323">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-323">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-324">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-324">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-325">**context_name** Puntero a la cadena del nombre de contexto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-325">**context_name** Pointer to the context name string.</span></span>
- <span data-ttu-id="8b2f2-326">**context_name_size** Tamaño de la cadena del nombre de contexto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-326">**context_name_size** Size of context name string.</span></span> <span data-ttu-id="8b2f2-327">Tenga en cuenta que el número máximo de bytes en un nombre de contexto se define mediante NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-327">Note that the maximum number of bytes in a context name is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-328">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-328">Return Values</span></span>

- <span data-ttu-id="8b2f2-329">**NX_SUCCESS** (0x00) Se ha establecido correctamente el nombre de contexto de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-329">**NX_SUCCESS** (0x00) Successful SNMP context name set.</span></span>
- <span data-ttu-id="8b2f2-330">**NX_SNMP_ERROR** (0x100) Error de tamaño del nombre de contexto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-330">**NX_SNMP_ERROR** (0x100) Context name size error.</span></span>
- <span data-ttu-id="8b2f2-331">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-331">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-332">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-332">Allowed From</span></span>

<span data-ttu-id="8b2f2-333">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-333">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-334">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-334">Example</span></span>

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a><span data-ttu-id="8b2f2-335">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="8b2f2-335">nx_snmp_agent_create</span></span>
<span data-ttu-id="8b2f2-336">Crear agente SNMP</span><span class="sxs-lookup"><span data-stu-id="8b2f2-336">Create SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-337">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-337">Prototype</span></span>

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a><span data-ttu-id="8b2f2-338">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-338">Description</span></span>

<span data-ttu-id="8b2f2-339">Este servicio crea un agente SNMP en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-339">This service creates a SNMP Agent on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-340">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-340">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-341">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-341">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-342">**snmp_agent_name** Puntero a la cadena del nombre del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-342">**snmp_agent_name** Pointer to the SNMP Agent name string.</span></span>
- <span data-ttu-id="8b2f2-343">**ip_ptr** Puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-343">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="8b2f2-344">**stack_ptr** Puntero al puntero de la pila de subprocesos del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-344">**stack_ptr** Pointer to SNMP Agent thread stack pointer.</span></span>
- <span data-ttu-id="8b2f2-345">**stack_size** Tamaño de la pila en bytes.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-345">**stack_size** Stack size in bytes.</span></span>
- <span data-ttu-id="8b2f2-346">**pool_ptr** Puntero el grupo de paquetes predeterminado para este agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-346">**pool_ptr** Pointer the default packet pool for this SNMP Agent.</span></span>
- <span data-ttu-id="8b2f2-347">**snmp_agent_username_process** Puntero de función a la rutina de control de nombre de usuario de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-347">**snmp_agent_username_process** Function pointer to application’s username handling routine.</span></span>
- <span data-ttu-id="8b2f2-348">**snmp_agent_get_process** Puntero de función a la rutina de control de la solicitud GET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-348">**snmp_agent_get_process** Function pointer to application’s GET request handling routine.</span></span>
- <span data-ttu-id="8b2f2-349">**snmp_agent_getnext_process** Puntero de función a la rutina de control de la solicitud GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-349">**snmp_agent_getnext_process** Function pointer to application’s GETNEXT request handling routine.</span></span>
- <span data-ttu-id="8b2f2-350">**snmp_agent_set_process** Puntero de función a la rutina de control de la solicitud SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-350">**snmp_agent_set_process** Function pointer to application’s SET request handling routine.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-351">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-351">Return Values</span></span>

- <span data-ttu-id="8b2f2-352">**NX_SUCCESS** (0x00) Creación correcta del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-352">**NX_SUCCESS** (0x00) Successful SNMP Agent create.</span></span>
- <span data-ttu-id="8b2f2-353">**NX_SNMP_ERROR** (0x100) Error en la creación del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-353">**NX_SNMP_ERROR** (0x100) SNMP Agent create error.</span></span>
- <span data-ttu-id="8b2f2-354">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-354">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-355">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-355">Allowed From</span></span>

<span data-ttu-id="8b2f2-356">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-356">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-357">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-357">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a><span data-ttu-id="8b2f2-358">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-358">nx_snmp_agent_current_version_get</span></span>
<span data-ttu-id="8b2f2-359">Obtener la versión del paquete SNMP</span><span class="sxs-lookup"><span data-stu-id="8b2f2-359">Get the SNMP packet version</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-360">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-360">Prototype</span></span>

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a><span data-ttu-id="8b2f2-361">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-361">Description</span></span>

<span data-ttu-id="8b2f2-362">Este servicio recupera la versión de SNMP analizada a partir del paquete SNMP más reciente recibido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-362">This service retrieves the SNMP version parsed from the most recent SNMP packet received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-363">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-363">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-364">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-364">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-365">**version** Puntero a la versión de SNMP analizada desde el paquete SNMP recibido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-365">**version** Pointer to the SNMP version parsed from received SNMP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-366">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-366">Return Values</span></span>

- <span data-ttu-id="8b2f2-367">**NX_SUCCESS** (0x00) Obtención correcta de la versión de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-367">**NX_SUCCESS** (0x00) Successful SNMP version get</span></span>
- <span data-ttu-id="8b2f2-368">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-368">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-369">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-369">Allowed From</span></span>

<span data-ttu-id="8b2f2-370">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-370">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-371">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-371">Example</span></span>

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a><span data-ttu-id="8b2f2-372">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="8b2f2-372">nx_snmp_agent_private_string_test</span></span>
<span data-ttu-id="8b2f2-373">Comprobar si la cadena privada coincide con la cadena privada del agente</span><span class="sxs-lookup"><span data-stu-id="8b2f2-373">Verify private string matches Agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-374">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-374">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a><span data-ttu-id="8b2f2-375">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-375">Description</span></span>

<span data-ttu-id="8b2f2-376">Este servicio compara la cadena de la comunidad de entrada terminada en NULL con la cadena privada del agente SNMP e indica si coinciden.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-376">This service compares the null terminated input community string with the SNMP agent private string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-377">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-377">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-378">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-378">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-379">**community_string** Puntero a la cadena que se va a comparar.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-379">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="8b2f2-380">**is_private** Puntero al resultado de la comparación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-380">**is_private** Pointer to result of comparison</span></span>  
<span data-ttu-id="8b2f2-381">NX_TRUE: la cadena coincide</span><span class="sxs-lookup"><span data-stu-id="8b2f2-381">NX_TRUE - string matches</span></span>  
<span data-ttu-id="8b2f2-382">NX_FALSE: la cadena no coincide</span><span class="sxs-lookup"><span data-stu-id="8b2f2-382">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-383">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-383">Return Values</span></span>

- <span data-ttu-id="8b2f2-384">**NX_SUCCESS** (0x00) Comparación correcta.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-384">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="8b2f2-385">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-385">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-386">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-386">Allowed From</span></span>

<span data-ttu-id="8b2f2-387">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-388">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-388">Example</span></span>

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a><span data-ttu-id="8b2f2-389">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="8b2f2-389">nx_snmp_agent_public_string_test</span></span>
<span data-ttu-id="8b2f2-390">Comprobar que la cadena pública recibida coincida con la cadena pública del agente</span><span class="sxs-lookup"><span data-stu-id="8b2f2-390">Verify received public string matches Agent’s public string</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-391">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-391">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a><span data-ttu-id="8b2f2-392">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-392">Description</span></span>

<span data-ttu-id="8b2f2-393">Este servicio compara una cadena de la comunidad de entrada terminada en NULL con la cadena pública del agente SNMP e indica si coinciden.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-393">This service compares a null terminated input community string with the SNMP agent public string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-394">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-394">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-395">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-395">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-396">**community_string** Puntero a la cadena que se va a comparar.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-396">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="8b2f2-397">**is_public** Puntero al resultado de la comparación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-397">**is_public** Pointer to result of comparison</span></span>  
<span data-ttu-id="8b2f2-398">NX_TRUE: la cadena coincide</span><span class="sxs-lookup"><span data-stu-id="8b2f2-398">NX_TRUE - string matches</span></span>  
<span data-ttu-id="8b2f2-399">NX_FALSE: la cadena no coincide</span><span class="sxs-lookup"><span data-stu-id="8b2f2-399">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-400">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-400">Return Values</span></span>

- <span data-ttu-id="8b2f2-401">**NX_SUCCESS** (0x00) Comparación correcta.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-401">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="8b2f2-402">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-402">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-403">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-403">Allowed From</span></span>

<span data-ttu-id="8b2f2-404">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-405">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-405">Example</span></span>

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a><span data-ttu-id="8b2f2-406">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-406">nx_snmp_agent_version_set</span></span>
<span data-ttu-id="8b2f2-407">Establecer el estado del agente SNMP para todas las versiones de SNMP</span><span class="sxs-lookup"><span data-stu-id="8b2f2-407">Set the SNMP agent status for each SNMP version</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-408">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-408">Prototype</span></span>

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a><span data-ttu-id="8b2f2-409">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-409">Description</span></span>

<span data-ttu-id="8b2f2-410">Este servicio establece el estado (habilitado o deshabilitado) para cada una de las versiones de SNMP, V1, V2 y V3, en el agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-410">This service sets the status (enabled/disabled) for each of the SNMP versions, V1, V2 and V3 on the SNMP agent.</span></span> <span data-ttu-id="8b2f2-411">Tenga en cuenta que las opciones configurables por el usuario, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 y NX_SNMP_DISABLE_V3, invalidarán esta configuración en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-411">Note that the user configurable options, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2, and NX_SNMP_DISABLE_V3, will override these run time settings.</span></span> <span data-ttu-id="8b2f2-412">De manera predeterminada, el agente SNMP está habilitado para las tres versiones.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-412">By default, the SNMP agent is enabled for all three versions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-413">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-413">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-414">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-414">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-415">**enabled_v1** Establece el estado habilitado para SNMP V1 en on y off.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-415">**enabled_v1** Sets enabled status for SNMP V1 to on/off.</span></span>
- <span data-ttu-id="8b2f2-416">**enabled_v2** Establece el estado habilitado para SNMP V2 en on y off.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-416">**enabled_v2** Sets enabled status for SNMP V2 to on/off.</span></span>
- <span data-ttu-id="8b2f2-417">**enabled_v3** Establece el estado habilitado para SNMP V3 en on y off.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-417">**enabled_v3** Sets enabled status for SNMP V3 to on/off.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-418">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-418">Return Values</span></span>

- <span data-ttu-id="8b2f2-419">**NX_SUCCESS** (0x00) Establecimiento correcto de la versión de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-419">**NX_SUCCESS** (0x00) Successful SNMP version set</span></span>
- <span data-ttu-id="8b2f2-420">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-420">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-421">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-421">Allowed From</span></span>

<span data-ttu-id="8b2f2-422">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-422">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-423">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-423">Example</span></span>

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a><span data-ttu-id="8b2f2-424">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-424">nx_snmp_agent_private_string_set</span></span>
<span data-ttu-id="8b2f2-425">Establecer la cadena privada del agente SNMP</span><span class="sxs-lookup"><span data-stu-id="8b2f2-425">Set the SNMP agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-426">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-426">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="8b2f2-427">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-427">Description</span></span>

<span data-ttu-id="8b2f2-428">Este servicio establece la cadena de la comunidad privada del agente SNMP con la cadena de entrada terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-428">This service sets the SNMP agent private community string with the input null terminated string.</span></span> <span data-ttu-id="8b2f2-429">El valor predeterminado es NULL (no se establece una cadena privada), de modo que el agente SNMP no aceptará ningún paquete SNMP recibido con una cadena de la comunidad "privada" para el acceso de lectura y escritura.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-429">The default value is NULL (no private string set), such that any SNMP packet received with a “private” community string will not be accepted by the SNMP agent for read/write access.</span></span> <span data-ttu-id="8b2f2-430">La cadena de entrada debe ser menor o igual que el valor configurable por el usuario NX_SNMP_MAX_USER_NAME-1 (para dejar espacio para la terminación con NULL).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-430">The input string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-431">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-431">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-432">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-432">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-433">**community_string** Puntero a la cadena privada que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-433">**community_string** Pointer to the private string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-434">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-434">Return Values</span></span>

- <span data-ttu-id="8b2f2-435">**NX_SUCCESS** (0x00) Se ha establecido correctamente la cadena privada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-435">**NX_SUCCESS** (0x00) Successfully set private string</span></span>
- <span data-ttu-id="8b2f2-436">**NX_SNMP_ERROR_TOOBIG** (0x01) Tamaño de la cadena demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-436">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span> 
- <span data-ttu-id="8b2f2-437">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-437">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-438">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-438">Allowed From</span></span>

<span data-ttu-id="8b2f2-439">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-439">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-440">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-440">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a><span data-ttu-id="8b2f2-441">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-441">nx_snmp_agent_public_string_set</span></span>
<span data-ttu-id="8b2f2-442">Establecer la cadena pública del agente SNMP</span><span class="sxs-lookup"><span data-stu-id="8b2f2-442">Set the SNMP agent public string</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-443">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-443">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="8b2f2-444">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-444">Description</span></span>

<span data-ttu-id="8b2f2-445">Este servicio establece la cadena de la comunidad pública del agente SNMP con la cadena de entrada terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-445">This service sets the SNMP agent public community string with the input null terminated string.</span></span> <span data-ttu-id="8b2f2-446">La cadena de la comunidad debe ser menor o igual que el valor configurable por el usuario NX_SNMP_MAX_USER_NAME-1 (para dejar espacio para la terminación con NULL).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-446">The community string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-447">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-447">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-448">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-448">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-449">**community_string** Puntero a la cadena pública que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-449">**community_string** Pointer to the public string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-450">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-450">Return Values</span></span>

- <span data-ttu-id="8b2f2-451">**NX_SUCCESS** (0x00) Se ha establecido correctamente la cadena pública.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-451">**NX_SUCCESS** (0x00) Successfully set public string</span></span>
- <span data-ttu-id="8b2f2-452">**NX_SNMP_ERROR_TOOBIG** (0x01) Tamaño de la cadena demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-452">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span>
- <span data-ttu-id="8b2f2-453">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-453">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-454">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-454">Allowed From</span></span>

<span data-ttu-id="8b2f2-455">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-456">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-456">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a><span data-ttu-id="8b2f2-457">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="8b2f2-457">nx_snmp_agent_delete</span></span>
<span data-ttu-id="8b2f2-458">Eliminar el agente SNMP</span><span class="sxs-lookup"><span data-stu-id="8b2f2-458">Delete SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-459">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-459">Prototype</span></span>

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-460">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-460">Description</span></span>

<span data-ttu-id="8b2f2-461">Este servicio elimina un agente SNMP creado previamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-461">This service deletes a previously created SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-462">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-462">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-463">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-463">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-464">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-464">Return Values</span></span>

- <span data-ttu-id="8b2f2-465">**NX_SUCCESS** (0x00) Eliminación correcta del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-465">**NX_SUCCESS** (0x00) Successful SNMP Agent delete.</span></span>
- <span data-ttu-id="8b2f2-466">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-466">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-467">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-467">Allowed From</span></span>

<span data-ttu-id="8b2f2-468">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-468">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-469">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-469">Example</span></span>

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a><span data-ttu-id="8b2f2-470">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="8b2f2-470">nx_snmp_agent_set_interface</span></span>
<span data-ttu-id="8b2f2-471">Establecer la interfaz de red del agente SNMP</span><span class="sxs-lookup"><span data-stu-id="8b2f2-471">Set the SNMP agent network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-472">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-472">Prototype</span></span>

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a><span data-ttu-id="8b2f2-473">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-473">Description</span></span>

<span data-ttu-id="8b2f2-474">Este servicio establece la interfaz de red SNMP para el agente SNMP tal y como se especifica en el índice de la interfaz de entrada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-474">This service sets the SNMP network interface for the SNMP Agent as specified by the input interface index.</span></span> <span data-ttu-id="8b2f2-475">Esto solo es útil para las aplicaciones de host SNMP con NetX Duo 5.6 o superior que admiten varias interfaces de red.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-475">This is only useful for SNMP host applications with NetX Duo 5.6 or higher which support multiple network interfaces.</span></span> <span data-ttu-id="8b2f2-476">Si no se especifica en el host, el valor predeterminado es cero para la interfaz principal.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-476">The default value if not specified by the host is zero, for the primary interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-477">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-477">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-478">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-478">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-479">**If_index** Índice que especifica la interfaz SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-479">**If_index** Index specifying the SNMP interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-480">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-480">Return Values</span></span>

- <span data-ttu-id="8b2f2-481">**NX_SUCCESS**: (0x00) Se ha establecido correctamente la interfaz SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-481">**NX_SUCCESS** (0x00) Successful SNMP interface set.</span></span>
- <span data-ttu-id="8b2f2-482">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-482">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-483">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-483">Allowed From</span></span>

<span data-ttu-id="8b2f2-484">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-484">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-485">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-485">Example</span></span>

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a><span data-ttu-id="8b2f2-486">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="8b2f2-486">nx_snmp_agent_md5_key_create</span></span>
<span data-ttu-id="8b2f2-487">Crear clave MD5 (solo SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-487">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-488">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-488">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a><span data-ttu-id="8b2f2-489">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-489">Description</span></span>

<span data-ttu-id="8b2f2-490">Este servicio crea una clave MD5 que se puede usar para la autenticación y el cifrado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-490">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="8b2f2-491">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-491">This service is deprecated.</span></span> <span data-ttu-id="8b2f2-492">Se recomienda a los desarrolladores que migren a *nx_snmp_agent_md5_key_create_extended()* .</span><span class="sxs-lookup"><span data-stu-id="8b2f2-492">Developers are encouraged to migrate to *nx_snmp_agent_md5_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-493">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-493">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-494">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-494">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-495">**password** Puntero a la cadena de contraseña.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-495">**password** Pointer to password string.</span></span>
- <span data-ttu-id="8b2f2-496">**destination_key** Puntero a la estructura de datos de la clave SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-496">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-497">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-497">Return Values</span></span>

- <span data-ttu-id="8b2f2-498">**NX_SUCCESS** (0x00) Clave creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-498">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="8b2f2-499">**NX_NOT_ENABLED** (0x14) La seguridad no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-499">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="8b2f2-500">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-500">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-501">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-501">Allowed From</span></span>

<span data-ttu-id="8b2f2-502">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-502">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-503">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-503">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a><span data-ttu-id="8b2f2-504">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="8b2f2-504">nx_snmp_agent_md5_key_create_extended</span></span>
<span data-ttu-id="8b2f2-505">Crear clave MD5 (solo SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-505">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-506">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-506">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="8b2f2-507">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-507">Description</span></span>

<span data-ttu-id="8b2f2-508">Este servicio crea una clave MD5 que se puede usar para la autenticación y el cifrado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-508">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="8b2f2-509">Este servicio reemplaza a *nx_snmp_agent_md5_key_create().*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-509">This service replaces *nx_snmp_agent_md5_key_create().*</span></span> <span data-ttu-id="8b2f2-510">Esta versión requiere que el autor de la llamada proporcione la longitud de la contraseña.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-510">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-511">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-511">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-512">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-512">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-513">**password** Puntero a la cadena de contraseña.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-513">**password** Pointer to password string.</span></span>
- <span data-ttu-id="8b2f2-514">**password_length** Longitud de la cadena de contraseña.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-514">**password_length** Length of password string.</span></span>
- <span data-ttu-id="8b2f2-515">**destination_key** Puntero a la estructura de datos de la clave SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-515">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-516">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-516">Return Values</span></span>

- <span data-ttu-id="8b2f2-517">**NX_SUCCESS** (0x00) Clave creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-517">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="8b2f2-518">**NX_NOT_ENABLED** (0x14) La seguridad no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-518">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="8b2f2-519">**NX_SNMP_FAILED** (0x102) Error de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-519">**NX_SNMP_FAILED** (0x102) SNMP failed.</span></span>
- <span data-ttu-id="8b2f2-520">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-520">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-521">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-521">Allowed From</span></span>

<span data-ttu-id="8b2f2-522">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-522">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-523">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-523">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a><span data-ttu-id="8b2f2-524">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="8b2f2-524">nx_snmp_agent_priv_trap_key_use</span></span>
<span data-ttu-id="8b2f2-525">Especificar la clave de cifrado para los mensajes de captura</span><span class="sxs-lookup"><span data-stu-id="8b2f2-525">Specify encryption key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-526">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-526">Prototype</span></span>

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a><span data-ttu-id="8b2f2-527">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-527">Description</span></span>

<span data-ttu-id="8b2f2-528">Este servicio especifica que se utilizará una clave de privacidad creada previamente para el cifrado y descifrado de los mensajes de captura de SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-528">This service specifies that a previously created privacy key is to be used for encryption and decryption of SNMPv3 trap messages.</span></span>

> [!NOTE]
> <span data-ttu-id="8b2f2-529">*Se debe crear previamente una clave de autenticación. La privacidad de SNMP v3 (cifrado) requiere autenticación. Consulte nx_snmp_agent_auth_trap_key_use para más información.*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-529">*An authentictation key must be previously created. SNMP v3 privacy (encryption) requires authentication. See nx_snmp_agent_auth_trap_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-530">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-530">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-531">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-531">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-532">**key** Puntero a la clave creada previamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-532">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-533">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-533">Return Values</span></span>

- <span data-ttu-id="8b2f2-534">**NX_SUCCESS** (0x00) Se ha establecido correctamente la clave de privacidad.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-534">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="8b2f2-535">**NX_NOT_ENABLED** (0x14) La seguridad no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-535">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="8b2f2-536">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-536">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-537">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-537">Allowed From</span></span>

<span data-ttu-id="8b2f2-538">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-538">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-539">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-539">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a><span data-ttu-id="8b2f2-540">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="8b2f2-540">nx_snmp_agent_privacy_key_use</span></span>
<span data-ttu-id="8b2f2-541">Especificar la clave de cifrado para los mensajes de respuesta</span><span class="sxs-lookup"><span data-stu-id="8b2f2-541">Specify encryption key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-542">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-542">Prototype</span></span>

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="8b2f2-543">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-543">Description</span></span>

<span data-ttu-id="8b2f2-544">Este servicio especifica que se utilizará la clave creada previamente para el cifrado y descifrado de los mensajes de respuesta de SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-544">This service specifies that the previously created key is to be used for encryption and decryption of SNMPv3 response messages.</span></span>

> [!NOTE]
> <span data-ttu-id="8b2f2-545">*Se debe haber especificado previamente una clave de autenticación. El cifrado de SNMP v3 también requiere la creación de una clave de autenticación. Consulte nx_snmp_agent_authentiation_key_use para más información.*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-545">*An authentication key must have previously been specified. SNMP v3 encryption requires creation of an authentication key as well. See nx_snmp_agent_authentiation_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-546">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-546">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-547">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-547">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-548">**key** Puntero a la clave creada previamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-548">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-549">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-549">Return Values</span></span>

- <span data-ttu-id="8b2f2-550">**NX_SUCCESS** (0x00) Se ha establecido correctamente la clave de privacidad.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-550">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="8b2f2-551">**NX_NOT_ENABLED** (0x14) La seguridad no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-551">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="8b2f2-552">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-552">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-553">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-553">Allowed From</span></span>

<span data-ttu-id="8b2f2-554">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-554">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-555">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-555">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a><span data-ttu-id="8b2f2-556">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="8b2f2-556">nx_snmp_agent_sha_key_create</span></span>
<span data-ttu-id="8b2f2-557">Crear clave SHA (solo SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-557">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-558">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-558">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a><span data-ttu-id="8b2f2-559">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-559">Description</span></span>

<span data-ttu-id="8b2f2-560">Este servicio crea una clave SHA que se puede usar para la autenticación y el cifrado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-560">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="8b2f2-561">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-561">This service is deprecated.</span></span> <span data-ttu-id="8b2f2-562">Se recomienda a los desarrolladores que migren a *nx_snmp_agent_sha_key_create_extended()* .</span><span class="sxs-lookup"><span data-stu-id="8b2f2-562">Developers are encouraged to migrate to *nx_snmp_agent_sha_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-563">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-563">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-564">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-564">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-565">**password** Puntero a la cadena de contraseña.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-565">**password** Pointer to password string.</span></span>
- <span data-ttu-id="8b2f2-566">**destination_key** Puntero a la estructura de datos de la clave SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-566">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-567">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-567">Return Values</span></span>

- <span data-ttu-id="8b2f2-568">**NX_SUCCESS** (0x00) Clave creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-568">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="8b2f2-569">**NX_SNMP_ERROR** (0x100) Error en la creación de la clave.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-569">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="8b2f2-570">**NX_PTR_ERROR** (0x07) Puntero de clave o agente SNMP no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-570">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-571">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-571">Allowed From</span></span>

<span data-ttu-id="8b2f2-572">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-572">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-573">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-573">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a><span data-ttu-id="8b2f2-574">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="8b2f2-574">nx_snmp_agent_sha_key_create_extended</span></span>
<span data-ttu-id="8b2f2-575">Crear clave SHA (solo SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-575">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-576">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-576">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="8b2f2-577">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-577">Description</span></span>

<span data-ttu-id="8b2f2-578">Este servicio crea una clave SHA que se puede usar para la autenticación y el cifrado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-578">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="8b2f2-579">Este servicio reemplaza a *nx_snmp_agent_sha_key_create().*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-579">This service replaces *nx_snmp_agent_sha_key_create().*</span></span> <span data-ttu-id="8b2f2-580">Esta versión requiere que el autor de la llamada proporcione la longitud de la contraseña.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-580">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-581">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-581">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-582">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-582">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-583">**password** Puntero a la cadena de contraseña.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-583">**password** Pointer to password string.</span></span>
- <span data-ttu-id="8b2f2-584">**password_length** Longitud de la cadena de contraseña.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-584">**password_length** Length of password string.</span></span>
- <span data-ttu-id="8b2f2-585">**destination_key** Puntero a la estructura de datos de la clave SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-585">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-586">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-586">Return Values</span></span>

- <span data-ttu-id="8b2f2-587">**NX_SUCCESS** (0x00) Clave creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-587">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="8b2f2-588">**NX_SNMP_ERROR** (0x100) Error en la creación de la clave.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-588">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="8b2f2-589">**NX_SNMP_FAILED** (0x102) Error en la creación de la clave.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-589">**NX_SNMP_FAILED** (0x102) Key create failed.</span></span>
- <span data-ttu-id="8b2f2-590">**NX_PTR_ERROR** (0x07) Puntero de clave o agente SNMP no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-590">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-591">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-591">Allowed From</span></span>

<span data-ttu-id="8b2f2-592">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-592">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-593">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-593">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a><span data-ttu-id="8b2f2-594">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="8b2f2-594">nx_snmp_agent_start</span></span>
<span data-ttu-id="8b2f2-595">Iniciar el agente SNMP</span><span class="sxs-lookup"><span data-stu-id="8b2f2-595">Start SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-596">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-596">Prototype</span></span>

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-597">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-597">Description</span></span>

<span data-ttu-id="8b2f2-598">Este servicio enlaza el socket UDP al puerto 161 de SNMP e inicia la tarea del subproceso del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-598">This service binds the UDP socket to the SNMP port 161 and starts the SNMP Agent thread task.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-599">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-599">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-600">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-600">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-601">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-601">Return Values</span></span>

- <span data-ttu-id="8b2f2-602">**NX_SUCCESS** (0x00) Inicio correcto del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-602">**NX_SUCCESS** (0x00) Successful start of SNMP Agent.</span></span>
- <span data-ttu-id="8b2f2-603">**NX_SNMP_ERROR** (0x100) Error en el inicio del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-603">**NX_SNMP_ERROR** (0x100) SNMP Agent start error.</span></span>
- <span data-ttu-id="8b2f2-604">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-604">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-605">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-605">Allowed From</span></span>

<span data-ttu-id="8b2f2-606">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-606">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-607">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-607">Example</span></span>

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a><span data-ttu-id="8b2f2-608">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="8b2f2-608">nx_snmp_agent_stop</span></span>
<span data-ttu-id="8b2f2-609">Detener el agente SNMP</span><span class="sxs-lookup"><span data-stu-id="8b2f2-609">Stop SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-610">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-610">Prototype</span></span>

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-611">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-611">Description</span></span>

<span data-ttu-id="8b2f2-612">Este servicio detiene la tarea del subproceso del agente SNMP y anula el enlace del socket UDP al puerto de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-612">This service stops the SNMP Agent thread task and unbinds the UDP socket to the SNMP port.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-613">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-613">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-614">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-614">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-615">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-615">Return Values</span></span>

- <span data-ttu-id="8b2f2-616">**NX_SUCCESS** (0x00) Detención correcta del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-616">**NX_SUCCESS** (0x00) Successful stop of SNMP Agent.</span></span>
- <span data-ttu-id="8b2f2-617">**NX_PTR_ERROR** (0x07) Puntero del agente SNMP no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-617">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-618">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-618">Allowed From</span></span>

<span data-ttu-id="8b2f2-619">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-619">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-620">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-620">Example</span></span>

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a><span data-ttu-id="8b2f2-621">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-621">nx_snmp_agent_trap_send</span></span>
<span data-ttu-id="8b2f2-622">Enviar captura de SNMP v1 *(solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-622">Send SNMPv1 trap *(IPv4 only)*</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-623">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-623">Prototype</span></span>

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="8b2f2-624">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-624">Description</span></span>

<span data-ttu-id="8b2f2-625">Este servicio envía una captura de SNMP al administrador de SNMP en la dirección IPv4 especificada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-625">This service sends an SNMP trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="8b2f2-626">El método preferido para enviar una captura de SNMP en NetX Duo es usar el servicio *nxd_snmp_agent_trap_send*.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-626">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trap_send* service.</span></span> <span data-ttu-id="8b2f2-627">*nx_snmp_agent_trap_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-627">*nx_snmp_agent_trap_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-628">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-628">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-629">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-629">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-630">**ip_address** Dirección IPv4 del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-630">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="8b2f2-631">**enterprise** Cadena del identificador de objeto de empresa (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-631">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="8b2f2-632">**trap_type** Tipo de captura solicitada, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-632">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="8b2f2-633">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-633">NX_SNMP_TRAP_COLDSTART (0)</span></span>  
   - <span data-ttu-id="8b2f2-634">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-634">NX_SNMP_TRAP_WARMSTART (1)</span></span>  
   - <span data-ttu-id="8b2f2-635">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-635">NX_SNMP_TRAP_LINKDOWN (2)</span></span>  
   - <span data-ttu-id="8b2f2-636">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-636">NX_SNMP_TRAP_LINKUP (3)</span></span>  
   - <span data-ttu-id="8b2f2-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>  
   - <span data-ttu-id="8b2f2-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  

- <span data-ttu-id="8b2f2-639">**trap_code** Código de la captura específica.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-639">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="8b2f2-640">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-640">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-641">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-641">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-642">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-642">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-643">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-643">Return Values</span></span>

- <span data-ttu-id="8b2f2-644">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-644">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-645">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-645">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-646">**NX_NOT_ENABLED** (0x14) SNMP v1 no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-646">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="8b2f2-647">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-647">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-648">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-648">Allowed From</span></span>

<span data-ttu-id="8b2f2-649">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-650">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-650">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a><span data-ttu-id="8b2f2-651">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-651">nxd_snmp_agent_trap_send</span></span>
<span data-ttu-id="8b2f2-652">*Enviar captura de SNMP v1 (IPv4 e IPv6)*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-652">Send SNMPv1 trap *(IPv4 and IPv6)*</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-653">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-653">Prototype</span></span>

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-654">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-654">Description</span></span>

<span data-ttu-id="8b2f2-655">Este servicio envía una captura de SNMP al administrador de SNMP en la dirección IP especificada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-655">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="8b2f2-656">El método equivalente para enviar una captura de SNMP en NetX es el servicio *nxd_snmp_agent_trap_send*.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-656">The equivalent method for sending an SNMP trap in NetX is the *nxd_snmp_agent_trap_send* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-657">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-657">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-658">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-658">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-659">**ip_address** Dirección IPv4 o IPv6 del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-659">**ip_address** IPv4 or IPv6 address of the SNMP Manager.</span></span>
- <span data-ttu-id="8b2f2-660">**enterprise** Cadena del identificador de objeto de empresa (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-660">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="8b2f2-661">**trap_type** Tipo de captura solicitada, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-661">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="8b2f2-662">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-662">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="8b2f2-663">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-663">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="8b2f2-664">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-664">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="8b2f2-665">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-665">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="8b2f2-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="8b2f2-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

- <span data-ttu-id="8b2f2-668">**trap_code** Código de la captura específica.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-668">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="8b2f2-669">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-669">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-670">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-670">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-671">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-671">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-672">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-672">Return Values</span></span>

- <span data-ttu-id="8b2f2-673">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-673">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-674">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-674">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-675">**NX_NOT_ENABLED** (0x14) SNMP v1 no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-675">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="8b2f2-676">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-676">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-677">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-677">Allowed From</span></span>

<span data-ttu-id="8b2f2-678">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-678">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-679">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-679">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a><span data-ttu-id="8b2f2-680">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-680">nx_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="8b2f2-681">Enviar captura de SNMP v2 (solo IPv4)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-681">Send SNMPv2 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-682">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-682">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-683">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-683">Description</span></span>

<span data-ttu-id="8b2f2-684">Este servicio envía una captura de SNMP v2 al administrador de SNMP en la dirección IPv4 especificada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-684">This service sends an SNMPv2 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="8b2f2-685">El método preferido para enviar una captura de SNMP en NetX Duo es usar el servicio *nxd_snmp_agent_trapv2_send*.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-685">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv2_send* service.</span></span> <span data-ttu-id="8b2f2-686">*nx_snmp_agent_trapv2_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-686">*nx_snmp_agent_trapv2_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-687">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-687">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-688">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-688">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-689">**ip_address** Dirección IPv4 del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-689">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="8b2f2-690">**community** Nombre de comunidad (nombre de usuario).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-690">**community** Community name (username).</span></span>
- <span data-ttu-id="8b2f2-691">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="8b2f2-691">**trap_type**</span></span>  
   <span data-ttu-id="8b2f2-692">Tipo de captura solicitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-692">Type of trap requested.</span></span> <span data-ttu-id="8b2f2-693">Los eventos estándar son:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-693">The standard events are:</span></span>  
   - <span data-ttu-id="8b2f2-694">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-694">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="8b2f2-695">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-695">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="8b2f2-696">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-696">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="8b2f2-697">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-697">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="8b2f2-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="8b2f2-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="8b2f2-700">Para datos propietarios:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-700">For proprietary data:</span></span>  
   - <span data-ttu-id="8b2f2-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido en *nxd_snmp.h*)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>
   
- <span data-ttu-id="8b2f2-702">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-702">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-703">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-703">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-704">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-704">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-705">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-705">Return Values</span></span>

- <span data-ttu-id="8b2f2-706">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-706">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-707">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-707">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-708">**NX_NOT_ENABLED** (0x14) SNMP v2 no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-708">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="8b2f2-709">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-709">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-710">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-710">Allowed From</span></span>

<span data-ttu-id="8b2f2-711">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-711">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-712">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-712">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="8b2f2-713">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-713">nx_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="8b2f2-714">Enviar captura de SNMP v2 especificando directamente el OID</span><span class="sxs-lookup"><span data-stu-id="8b2f2-714">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-715">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-715">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-716">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-716">Description</span></span>

<span data-ttu-id="8b2f2-717">Este servicio envía una captura de SNMP v2 al administrador de SNMP en la dirección IP especificada (solo IPv4) y permite que el autor de la llamada especifique directamente el OID.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-717">This service sends an SNMPv2 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="8b2f2-718">El método preferido para enviar una captura de SNMP especificando el OID en NetX Duo es usar el servicio *nxd_snmp_agent_trapv2_oid_send*.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-718">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv2_oid_send* service.</span></span> <span data-ttu-id="8b2f2-719">*nx_snmp_agent_trapv2_oid_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-719">*nx_snmp_agent_trapv2_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-720">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-720">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-721">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-721">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-722">**ip_address** Dirección IP del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-722">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="8b2f2-723">**community** Nombre de comunidad (nombre de usuario).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-723">**community** Community name (username).</span></span>
- <span data-ttu-id="8b2f2-724">**OID** Puntero al búfer que contiene el OID.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-724">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="8b2f2-725">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-725">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-726">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-726">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-727">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-727">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-728">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-728">Return Values</span></span>

- <span data-ttu-id="8b2f2-729">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-729">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-730">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-730">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-731">**NX_PTR_ERROR** (0x16) Puntero de parámetro o agente SNMP no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-731">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="8b2f2-732">**NX_IP_ADDRESS_ERROR** (0x21) Dirección IP de destino no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-732">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="8b2f2-733">**NX_OPTION_ERROR** (0x0a) Parámetro no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-733">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-734">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-734">Allowed From</span></span>

<span data-ttu-id="8b2f2-735">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-736">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-736">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a><span data-ttu-id="8b2f2-737">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-737">nxd_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="8b2f2-738">Enviar captura de SNMP v2 (IPv4 e IPv6)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-738">Send SNMPv2 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-739">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-739">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-740">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-740">Description</span></span>

<span data-ttu-id="8b2f2-741">Este servicio envía una captura de SNMP V2 al administrador de SNMP en la dirección IP especificada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-741">This service sends an SNMP V2 trap to the SNMP Manager at the specified IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-742">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-742">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-743">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-743">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-744">**ip_address** Dirección IP (IPv4 o IPv6) del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-744">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="8b2f2-745">**community** Nombre de comunidad (nombre de usuario).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-745">**community** Community name (username).</span></span>
- <span data-ttu-id="8b2f2-746">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="8b2f2-746">**trap_type**</span></span>  
   <span data-ttu-id="8b2f2-747">Tipo de captura solicitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-747">Type of trap requested.</span></span> <span data-ttu-id="8b2f2-748">Los eventos estándar son:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-748">The standard events are:</span></span>  
   - <span data-ttu-id="8b2f2-749">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-749">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="8b2f2-750">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-750">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="8b2f2-751">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-751">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="8b2f2-752">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-752">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="8b2f2-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="8b2f2-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="8b2f2-755">Para datos propietarios:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-755">For proprietary data:</span></span>

   - <span data-ttu-id="8b2f2-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido en *nxd_snmp.h*)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="8b2f2-757">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-757">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-758">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-758">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-759">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-759">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-760">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-760">Return Values</span></span>

- <span data-ttu-id="8b2f2-761">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-761">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-762">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-762">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-763">**NX_NOT_ENABLED** (0x14) SNMP v2 no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-763">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="8b2f2-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Versión de IP no admitida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="8b2f2-765">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-765">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-766">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-766">Allowed From</span></span>

<span data-ttu-id="8b2f2-767">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-767">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-768">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-768">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="8b2f2-769">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-769">nxd_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="8b2f2-770">Enviar captura de SNMP v2 especificando directamente el OID</span><span class="sxs-lookup"><span data-stu-id="8b2f2-770">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-771">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-771">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-772">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-772">Description</span></span>

<span data-ttu-id="8b2f2-773">Este servicio envía una captura de SNMP v2 al administrador de SNMP en la dirección IP especificada (IPv4 e IPv6) y permite que el autor de la llamada especifique directamente el OID.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-773">This service sends an SNMP v2 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-774">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-774">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-775">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-775">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-776">**ip_address** Dirección IP del administrador de SNMP (IPv4 e IPv6).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-776">**ip_address** IP address of SNMP Manager (IPv4/IPv6).</span></span>
- <span data-ttu-id="8b2f2-777">**community** Nombre de comunidad (nombre de usuario).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-777">**community** Community name (username).</span></span>
- <span data-ttu-id="8b2f2-778">**OID** Puntero al búfer que contiene el OID.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-778">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="8b2f2-779">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-779">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-780">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-780">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-781">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-781">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-782">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-782">Return Values</span></span>

- <span data-ttu-id="8b2f2-783">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-783">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-784">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-784">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-785">**NX_PTR_ERROR** (0x16) Puntero de parámetro o agente SNMP no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-785">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="8b2f2-786">**NX_IP_ADDRESS_ERROR** (0x21) Dirección IP de destino no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-786">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="8b2f2-787">**NX_OPTION_ERROR** (0x0a) Parámetro no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-787">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-788">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-788">Allowed From</span></span>

<span data-ttu-id="8b2f2-789">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-790">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-790">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a><span data-ttu-id="8b2f2-791">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-791">nx_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="8b2f2-792">Enviar captura de SNMP v3 (solo IPv4)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-792">Send SNMPv3 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-793">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-793">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="8b2f2-794">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-794">Description</span></span>

<span data-ttu-id="8b2f2-795">Este servicio envía una captura de SNMP v3 al administrador de SNMP en la dirección IPv4 especificada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-795">This service sends an SNMPv3 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="8b2f2-796">El método preferido para enviar una captura de SNMP en NetX Duo es usar el servicio *nxd_snmp_agent_trapv3_send*.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-796">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv3_send* service.</span></span> <span data-ttu-id="8b2f2-797">*nx_snmp_agent_trapv3_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-797">*nx_snmp_agent_trapv3_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-798">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-798">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-799">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-799">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-800">**ip_address** Dirección IPv4 del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-800">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="8b2f2-801">**username** Nombre de comunidad (nombre de usuario).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-801">**username** Community name (username).</span></span>
- <span data-ttu-id="8b2f2-802">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="8b2f2-802">**trap_type**</span></span>  
   <span data-ttu-id="8b2f2-803">Tipo de captura solicitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-803">Type of trap requested.</span></span> <span data-ttu-id="8b2f2-804">Los eventos estándar son:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-804">The standard events are:</span></span>  
   - <span data-ttu-id="8b2f2-805">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-805">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="8b2f2-806">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-806">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="8b2f2-807">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-807">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="8b2f2-808">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-808">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="8b2f2-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="8b2f2-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="8b2f2-811">Para datos propietarios:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-811">For proprietary data:</span></span>
   - <span data-ttu-id="8b2f2-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido en *nxd_snmp.h*)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="8b2f2-813">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-813">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-814">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-814">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-815">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-815">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-816">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-816">Return Values</span></span>

- <span data-ttu-id="8b2f2-817">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-817">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-818">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-818">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-819">**NX_NOT_ENABLED** (0x14) SNMP v3 no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-819">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="8b2f2-820">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-820">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-821">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-821">Allowed From</span></span>

<span data-ttu-id="8b2f2-822">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-822">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-823">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-823">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="8b2f2-824">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-824">nx_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="8b2f2-825">Enviar captura de SNMP v3 especificando directamente el OID</span><span class="sxs-lookup"><span data-stu-id="8b2f2-825">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-826">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-826">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-827">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-827">Description</span></span>

<span data-ttu-id="8b2f2-828">Este servicio envía una captura de SNMP v3 al administrador de SNMP en la dirección IP especificada (solo IPv4) y permite que el autor de la llamada especifique directamente el OID.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-828">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="8b2f2-829">El método preferido para enviar una captura de SNMP especificando el OID en NetX Duo es usar el servicio *nxd_snmp_agent_trapv3_oid_send*.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-829">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv3_oid_send* service.</span></span> <span data-ttu-id="8b2f2-830">*nx_snmp_agent_trapv3_oid_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-830">*nx_snmp_agent_trapv3_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-831">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-831">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-832">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-832">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-833">**ip_address** Dirección IP del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-833">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="8b2f2-834">**username** Nombre de comunidad (nombre de usuario).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-834">**username** Community name (username).</span></span>
- <span data-ttu-id="8b2f2-835">**OID** Puntero al búfer que contiene el OID.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-835">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="8b2f2-836">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-836">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-837">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-837">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-838">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-838">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-839">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-839">Return Values</span></span>

- <span data-ttu-id="8b2f2-840">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-840">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-841">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-841">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-842">**NX_PTR_ERROR** (0x16) Puntero de parámetro o agente SNMP no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-842">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="8b2f2-843">**NX_IP_ADDRESS_ERROR** (0x21) Dirección IP de destino no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-843">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="8b2f2-844">**NX_OPTION_ERROR** (0x0a) Parámetro no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-844">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-845">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-845">Allowed From</span></span>

<span data-ttu-id="8b2f2-846">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-847">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-847">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a><span data-ttu-id="8b2f2-848">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-848">nxd_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="8b2f2-849">Enviar captura de SNMP v3 (IPv4 e IPv6)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-849">Send SNMPv3 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-850">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-850">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-851">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-851">Description</span></span>

<span data-ttu-id="8b2f2-852">Este servicio envía una captura de SNMP al administrador de SNMP en la dirección IP especificada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-852">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="8b2f2-853">Esta captura es básicamente la misma que la captura de SNMP v2, excepto que el formato del mensaje de captura está incluido en el PDU de SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-853">This trap is basically the same as the SNMP v2 trap, except the trap message format is contained in the SNMP v3 PDU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-854">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-854">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-855">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-855">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-856">**ip_address** Dirección IP (IPv4 o IPv6) del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-856">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="8b2f2-857">**username** Nombre de comunidad (nombre de usuario).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-857">**username** Community name (username).</span></span>
- <span data-ttu-id="8b2f2-858">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="8b2f2-858">**trap_type**</span></span>  
   <span data-ttu-id="8b2f2-859">Tipo de captura solicitada.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-859">Type of trap requested.</span></span> <span data-ttu-id="8b2f2-860">Los eventos estándar son:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-860">The standard events are:</span></span>
   - <span data-ttu-id="8b2f2-861">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-861">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="8b2f2-862">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-862">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="8b2f2-863">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-863">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="8b2f2-864">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-864">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="8b2f2-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="8b2f2-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  
   <span data-ttu-id="8b2f2-867">Para datos propietarios:</span><span class="sxs-lookup"><span data-stu-id="8b2f2-867">For proprietary data:</span></span>
   - <span data-ttu-id="8b2f2-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido en *nxd_snmp.h*)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="8b2f2-869">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-869">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-870">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-870">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-871">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-871">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-872">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-872">Return Values</span></span>

- <span data-ttu-id="8b2f2-873">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-873">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-874">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-874">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-875">**NX_NOT_ENABLED** (0x14) SNMP v3 no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-875">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="8b2f2-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Versión de IP no admitida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="8b2f2-877">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-877">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-878">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-878">Allowed From</span></span>

<span data-ttu-id="8b2f2-879">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-879">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-880">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-880">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="8b2f2-881">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="8b2f2-881">nxd_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="8b2f2-882">Enviar captura de SNMP v3 especificando directamente el OID</span><span class="sxs-lookup"><span data-stu-id="8b2f2-882">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-883">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-883">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="8b2f2-884">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-884">Description</span></span>

<span data-ttu-id="8b2f2-885">Este servicio envía una captura de SNMP v3 al administrador de SNMP en la dirección IP especificada (IPv4 e IPv6) y permite que el autor de la llamada especifique directamente el OID.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-885">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-886">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-886">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-887">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-887">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="8b2f2-888">**ip_address** Puntero a la dirección IP del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-888">**ip_address** Pointer to IP address of SNMP Manager.</span></span>
- <span data-ttu-id="8b2f2-889">**username** Nombre de usuario (nombre de comunidad).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-889">**username** Username (community name).</span></span>
- <span data-ttu-id="8b2f2-890">**OID** Puntero al búfer que contiene el OID.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-890">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="8b2f2-891">**elapsed_time** Tiempo de actividad del sistema (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="8b2f2-891">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="8b2f2-892">**object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-892">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="8b2f2-893">La lista termina con NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-893">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-894">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-894">Return Values</span></span>

- <span data-ttu-id="8b2f2-895">**NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-895">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="8b2f2-896">**NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-896">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="8b2f2-897">**NX_PTR_ERROR** (0x16) Puntero de parámetro o agente SNMP no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-897">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="8b2f2-898">**NX_IP_ADDRESS_ERROR** (0x21) Dirección IP de destino no válida.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-898">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-899">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-899">Allowed From</span></span>

<span data-ttu-id="8b2f2-900">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-900">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-901">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-901">Example</span></span>

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a><span data-ttu-id="8b2f2-902">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-902">nx_snmp_agent_v3_context_boots_set</span></span>
<span data-ttu-id="8b2f2-903">Establecer el número de reinicios (si está habilitado SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-903">Set the number of reboots (if SNMPv3 enabled)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-904">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-904">Prototype</span></span>

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a><span data-ttu-id="8b2f2-905">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-905">Description</span></span>

<span data-ttu-id="8b2f2-906">Este servicio establece el número de reinicios registrados por el agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-906">This service sets the number of reboots recorded by the SNMP agent.</span></span> <span data-ttu-id="8b2f2-907">Este servicio solo está disponible si está habilitado SNMP v3 para el agente SNMP, porque el número de reinicios solo se usa en el protocolo SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-907">This service is only available if SNMPv3 is enabled for the SNMP agent because boot count is only used in the SNMPv3 protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-908">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-908">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-909">**agent_ptr** Puntero al bloque de control del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-909">**agent_ptr** Pointer to SNMP Agent control block</span></span>
- <span data-ttu-id="8b2f2-910">**boots** Valor en el que se va a establecer el número de inicios del agente SNMP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-910">**boots** The value to set SNMP Agent boot count to</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-911">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-911">Return Values</span></span>

- <span data-ttu-id="8b2f2-912">**NX_SUCCESS** (0x00) Número de inicios establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-912">**NX_SUCCESS** (0x00) Successfully set boot count</span></span>
- <span data-ttu-id="8b2f2-913">**NX_SNMP_ERROR** (0x100) Error al establecer el número de inicios.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-913">**NX_SNMP_ERROR** (0x100) Error setting boot count</span></span>
- <span data-ttu-id="8b2f2-914">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-914">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-915">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-915">Allowed From</span></span>

<span data-ttu-id="8b2f2-916">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-916">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-917">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-917">Example</span></span>

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a><span data-ttu-id="8b2f2-918">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="8b2f2-918">nx_snmp_object_compare</span></span>
<span data-ttu-id="8b2f2-919">Comparar dos objetos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-919">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-920">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-920">Prototype</span></span>

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a><span data-ttu-id="8b2f2-921">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-921">Description</span></span>

<span data-ttu-id="8b2f2-922">Este servicio compara el identificador de objeto proporcionado con el identificador de objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-922">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="8b2f2-923">Ambos identificadores de objeto tendrán la notación SMI ASCII; por ejemplo, ambos objetos deben comenzar por la cadena ASCII "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="8b2f2-923">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="8b2f2-924">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-924">This service is deprecated.</span></span> <span data-ttu-id="8b2f2-925">Se recomienda a los desarrolladores que migren a *nx_snmp_object_compare_extended().*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-925">Developers are encouraged to migrate to *nx_snmp_object_compare_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-926">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-926">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-927">**object** Puntero al identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-927">**object** Pointer to object ID.</span></span>
- <span data-ttu-id="8b2f2-928">**reference_object** Puntero al identificador del objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-928">**reference_object** Pointer to the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-929">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-929">Return Values</span></span>

- <span data-ttu-id="8b2f2-930">**NX_SUCCESS** (0x00) El objeto coincide con el objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-930">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="8b2f2-931">**NX_SNMP_NEXT_ENTRY** (0x101) El objeto es menor que el objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-931">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="8b2f2-932">**NX_SNMP_ERROR** (0x100) El objeto es mayor que el objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-932">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="8b2f2-933">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-933">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-934">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-934">Allowed From</span></span>

<span data-ttu-id="8b2f2-935">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-935">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-936">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-936">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a><span data-ttu-id="8b2f2-937">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="8b2f2-937">nx_snmp_object_compare_extended</span></span>
<span data-ttu-id="8b2f2-938">Comparar dos objetos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-938">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-939">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-939">Prototype</span></span>

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a><span data-ttu-id="8b2f2-940">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-940">Description</span></span>

<span data-ttu-id="8b2f2-941">Este servicio compara el identificador de objeto proporcionado con el identificador de objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-941">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="8b2f2-942">Ambos identificadores de objeto tendrán la notación SMI ASCII; por ejemplo, ambos objetos deben comenzar por la cadena ASCII "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="8b2f2-942">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="8b2f2-943">Este servicio reemplaza a *nx_snmp_object_compare().*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-943">This service replaces *nx_snmp_object_compare().*</span></span> <span data-ttu-id="8b2f2-944">Esta versión requiere que los autores de llamada proporcionen la información de longitud.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-944">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-945">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-945">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-946">**request_object** Puntero al identificador del objeto de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-946">**request_object** Pointer to request object ID.</span></span>
- <span data-ttu-id="8b2f2-947">**request_object_length** Longitud del identificador del objeto de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-947">**request_object_length** Length of the request object ID.</span></span>
- <span data-ttu-id="8b2f2-948">**reference_object** Puntero al identificador del objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-948">**reference_object** Pointer to the reference object ID.</span></span>
- <span data-ttu-id="8b2f2-949">**reference_object_length** Longitud del identificador del objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-949">**reference_object_length** Length of the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-950">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-950">Return Values</span></span>

- <span data-ttu-id="8b2f2-951">**NX_SUCCESS** (0x00) El objeto coincide con el objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-951">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="8b2f2-952">**NX_SNMP_NEXT_ENTRY** (0x101) El objeto es menor que el objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-952">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="8b2f2-953">**NX_SNMP_ERROR** (0x100) El objeto es mayor que el objeto de referencia.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-953">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="8b2f2-954">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-954">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-955">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-955">Allowed From</span></span>

<span data-ttu-id="8b2f2-956">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-956">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-957">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-957">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a><span data-ttu-id="8b2f2-958">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="8b2f2-958">nx_snmp_object_copy</span></span>
<span data-ttu-id="8b2f2-959">Copia de un objeto</span><span class="sxs-lookup"><span data-stu-id="8b2f2-959">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-960">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-960">Prototype</span></span>

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a><span data-ttu-id="8b2f2-961">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-961">Description</span></span>

<span data-ttu-id="8b2f2-962">Este servicio copia el objeto de origen con la notación SIM ASCII en el objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-962">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="8b2f2-963">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-963">This service is deprecated.</span></span> <span data-ttu-id="8b2f2-964">Se recomienda a los desarrolladores que migren a *nx_snmp_object_copy_extended().*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-964">Developers are encouraged to migrate to *nx_snmp_object_copy_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-965">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-965">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-966">**source_object_name** Puntero al identificador del objeto de origen.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-966">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="8b2f2-967">**destination_object_name** Puntero al identificador de objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-967">**destination_object_name** Pointer to destination object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-968">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-968">Return Values</span></span>

- <span data-ttu-id="8b2f2-969">**size** Número de bytes copiados en el nombre de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-969">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="8b2f2-970">Si hay un error, se devuelve cero.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-970">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-971">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-971">Allowed From</span></span>

<span data-ttu-id="8b2f2-972">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-972">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-973">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-973">Example</span></span>

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a><span data-ttu-id="8b2f2-974">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="8b2f2-974">nx_snmp_object_copy_extended</span></span>
<span data-ttu-id="8b2f2-975">Copia de un objeto</span><span class="sxs-lookup"><span data-stu-id="8b2f2-975">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-976">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-976">Prototype</span></span>

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a><span data-ttu-id="8b2f2-977">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-977">Description</span></span>

<span data-ttu-id="8b2f2-978">Este servicio copia el objeto de origen con la notación SIM ASCII en el objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-978">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="8b2f2-979">Este servicio reemplaza a *nx_snmp_object_copy().*</span><span class="sxs-lookup"><span data-stu-id="8b2f2-979">This service replaces *nx_snmp_object_copy().*</span></span> <span data-ttu-id="8b2f2-980">Esta versión requiere que los autores de llamada proporcionen la información de longitud.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-980">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-981">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-981">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-982">**source_object_name** Puntero al identificador del objeto de origen.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-982">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="8b2f2-983">**source_object_name_length** Longitud del identificador del objeto de origen.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-983">**source_object_name_length** Length of source object ID.</span></span>
- <span data-ttu-id="8b2f2-984">**destination_object_name_buffer** Puntero al búfer del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-984">**destination_object_name_buffer** Pointer to destination object buffer.</span></span>
- <span data-ttu-id="8b2f2-985">**destination_object_name_buffer_size** Tamaño del búfer del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-985">**destination_object_name_buffer_size** Size of destination object buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-986">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-986">Return Values</span></span>

- <span data-ttu-id="8b2f2-987">**size** Número de bytes copiados en el nombre de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-987">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="8b2f2-988">Si hay un error, se devuelve cero.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-988">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-989">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-989">Allowed From</span></span>

<span data-ttu-id="8b2f2-990">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-990">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-991">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-991">Example</span></span>

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a><span data-ttu-id="8b2f2-992">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-992">nx_snmp_object_counter_get</span></span>
<span data-ttu-id="8b2f2-993">Obtener objeto de contador</span><span class="sxs-lookup"><span data-stu-id="8b2f2-993">Get counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-994">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-994">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="8b2f2-995">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-995">Description</span></span>

<span data-ttu-id="8b2f2-996">Este servicio recupera el objeto de contador en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-996">This service retrieves the counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-997">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-997">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-998">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-998">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-999">**source_ptr** Puntero al origen del contador.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-999">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="8b2f2-1000">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1000">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1001">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1001">Return Values</span></span>

- <span data-ttu-id="8b2f2-1002">**NX_SUCCESS** (0x00) El objeto de contador se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1002">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1003">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1003">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1004">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1004">Allowed From</span></span>

<span data-ttu-id="8b2f2-1005">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1005">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1006">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1006">Example</span></span>

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a><span data-ttu-id="8b2f2-1007">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1007">nx_snmp_object_counter_set</span></span>
<span data-ttu-id="8b2f2-1008">Establecer objeto de contador</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1008">Set counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1009">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1009">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1010">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1010">Description</span></span>

<span data-ttu-id="8b2f2-1011">Este servicio establece el contador en la dirección especificada por el puntero de destino con el valor del contador en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1011">This service sets the counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1012">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1012">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1013">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1013">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1014">**destination_ptr** Puntero al destino del contador.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1014">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="8b2f2-1015">**object_data** Puntero a la estructura del objeto de origen del contador.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1015">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1016">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1016">Return Values</span></span>

- <span data-ttu-id="8b2f2-1017">**NX_SUCCESS** (0x00) El objeto de contador se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1017">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="8b2f2-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1019">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1019">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1020">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1020">Allowed From</span></span>

<span data-ttu-id="8b2f2-1021">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1021">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1022">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1022">Example</span></span>

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a><span data-ttu-id="8b2f2-1023">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1023">nx_snmp_object_counter64_get</span></span>
<span data-ttu-id="8b2f2-1024">Obtener objeto de contador de 64 bits</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1024">Get 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1025">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1025">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1026">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1026">Description</span></span>

<span data-ttu-id="8b2f2-1027">Este servicio recupera el objeto de contador de 64 bits en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1027">This service retrieves the 64-bit counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1028">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1028">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1029">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1029">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1030">**source_ptr** Puntero al origen del contador.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1030">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="8b2f2-1031">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1031">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1032">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1032">Return Values</span></span>

- <span data-ttu-id="8b2f2-1033">**NX_SUCCESS** (0x00) El objeto de contador se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1033">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1034">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1034">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1035">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1035">Allowed From</span></span>

<span data-ttu-id="8b2f2-1036">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1036">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1037">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1037">Example</span></span>

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a><span data-ttu-id="8b2f2-1038">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1038">nx_snmp_object_counter64_set</span></span>
<span data-ttu-id="8b2f2-1039">Establecer objeto de contador de 64 bits</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1039">Set 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1040">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1040">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="8b2f2-1041">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1041">Description</span></span>

<span data-ttu-id="8b2f2-1042">Este servicio establece el contador de 64 bits en la dirección especificada por el puntero de destino con el valor del contador en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1042">This service sets the 64-bit counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1043">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1043">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1044">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1044">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1045">**destination_ptr** Puntero al destino del contador.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1045">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="8b2f2-1046">**object_data** Puntero a la estructura del objeto de origen del contador.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1046">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1047">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1047">Return Values</span></span>

- <span data-ttu-id="8b2f2-1048">**NX_SUCCESS** (0x00) El objeto de contador se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1048">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="8b2f2-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1050">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1050">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1051">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1051">Allowed From</span></span>

<span data-ttu-id="8b2f2-1052">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1052">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1053">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1053">Example</span></span>

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a><span data-ttu-id="8b2f2-1054">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1054">nx_snmp_object_end_of_mib</span></span>
<span data-ttu-id="8b2f2-1055">Establecer el valor de final de MIB</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1055">Set end-of-mib value</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1056">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1056">Prototype</span></span>

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1057">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1057">Description</span></span>

<span data-ttu-id="8b2f2-1058">Este servicio crea un objeto que señala el final de MIB y suele llamarse desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1058">This service creates an object signaling the end of the MIB and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1059">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1059">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1060">**not_used_ptr** Puntero no utilizado: debe ser NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1060">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="8b2f2-1061">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1061">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1062">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1062">Return Values</span></span>

- <span data-ttu-id="8b2f2-1063">**NX_SUCCESS** (0x00) El objeto de final de MIB se ha creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1063">**NX_SUCCESS** (0x00) The end-of-mib object has be successfully built.</span></span>
- <span data-ttu-id="8b2f2-1064">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1064">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1065">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1065">Allowed From</span></span>

<span data-ttu-id="8b2f2-1066">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1066">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1067">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1067">Example</span></span>

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a><span data-ttu-id="8b2f2-1068">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1068">nx_snmp_object_gauge_get</span></span>
<span data-ttu-id="8b2f2-1069">Obtener objeto de medidor</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1069">Get gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1070">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1070">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1071">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1071">Description</span></span>

<span data-ttu-id="8b2f2-1072">Este servicio recupera el objeto de medidor en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1072">This service retrieves the gauge object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1073">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1073">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1074">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1074">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1075">**source_ptr** Puntero al origen del medidor.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1075">**source_ptr** Pointer to gauge source.</span></span>
- <span data-ttu-id="8b2f2-1076">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1076">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1077">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1077">Return Values</span></span>

- <span data-ttu-id="8b2f2-1078">**NX_SUCCESS** (0x00) El objeto de medidor se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1078">**NX_SUCCESS** (0x00) The gauge object has be successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1079">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1079">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1080">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1080">Allowed From</span></span>

<span data-ttu-id="8b2f2-1081">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1081">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1082">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1082">Example</span></span>

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a><span data-ttu-id="8b2f2-1083">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1083">nx_snmp_object_gauge_set</span></span>
<span data-ttu-id="8b2f2-1084">Establecer objeto de medidor</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1084">Set gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1085">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1085">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1086">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1086">Description</span></span>

<span data-ttu-id="8b2f2-1087">Este servicio establece el medidor en la dirección especificada por el puntero de destino con el valor del medidor en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1087">This service sets the gauge at the address specified by the destination pointer with the gauge value in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1088">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1088">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1089">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1089">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1090">**destination_ptr** Puntero al destino del medidor.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1090">**destination_ptr** Pointer to gauge destination.</span></span>
- <span data-ttu-id="8b2f2-1091">**object_data** Puntero a la estructura del objeto de origen del medidor.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1091">**object_data** Pointer to gauge source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1092">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1092">Return Values</span></span>

- <span data-ttu-id="8b2f2-1093">**NX_SUCCESS** (0x00) El objeto de medidor se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1093">**NX_SUCCESS** (0x00) The gauge object has be successfully set.</span></span>
- <span data-ttu-id="8b2f2-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1095">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1095">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1096">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1096">Allowed From</span></span>

<span data-ttu-id="8b2f2-1097">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1097">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1098">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1098">Example</span></span>

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a><span data-ttu-id="8b2f2-1099">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1099">nx_snmp_object_id_get</span></span>
<span data-ttu-id="8b2f2-1100">Obtener el identificador de objeto</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1100">Get object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1101">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1101">Prototype</span></span>

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1102">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1102">Description</span></span>

<span data-ttu-id="8b2f2-1103">Este servicio recupera el identificador de objeto (en notación SIM ASCII) en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1103">This service retrieves the object ID (in ASCII SIM notation) at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1104">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1104">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1105">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1105">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1106">**source_ptr** Puntero al origen del identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1106">**source_ptr** Pointer to object ID source.</span></span>
- <span data-ttu-id="8b2f2-1107">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1107">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1108">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1108">Return Values</span></span>

- <span data-ttu-id="8b2f2-1109">**NX_SUCCESS** (0x00) El identificador de objeto se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1109">**NX_SUCCESS** (0x00) The object ID has be successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1110">**NX_SNMP_ERROR** (0x100) Longitud no válida del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1110">**NX_SNMP_ERROR** (0x100) Invalid length of object</span></span>
- <span data-ttu-id="8b2f2-1111">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1111">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1112">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1112">Allowed From</span></span>

<span data-ttu-id="8b2f2-1113">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1113">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1114">Example</span></span>

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a><span data-ttu-id="8b2f2-1115">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1115">nx_snmp_object_id_set</span></span>
<span data-ttu-id="8b2f2-1116">Establecer el identificador de objeto</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1116">Set object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1117">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1117">Prototype</span></span>

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1118">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1118">Description</span></span>

<span data-ttu-id="8b2f2-1119">Este servicio establece el identificador de objeto (en notación SIM ASCII) en la dirección especificada por el puntero de destino con el identificador de objeto en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1119">This service sets the object ID (in ASCII SIM notation) at the address specified by the destination pointer with the object ID in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1120">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1120">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1121">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1121">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1122">**destination_ptr** Puntero al destino del identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1122">**destination_ptr** Pointer to object ID destination.</span></span>
- <span data-ttu-id="8b2f2-1123">**object_data** Puntero a la estructura del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1123">**object_data** Pointer to object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1124">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1124">Return Values</span></span>

- <span data-ttu-id="8b2f2-1125">**NX_SUCCESS** (0x00) El identificador de objeto se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1125">**NX_SUCCESS** (0x00) The object ID has been successfully set.</span></span>
- <span data-ttu-id="8b2f2-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1127">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1127">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1128">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1128">Allowed From</span></span>

<span data-ttu-id="8b2f2-1129">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1129">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1130">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1130">Example</span></span>

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a><span data-ttu-id="8b2f2-1131">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1131">nx_snmp_object_integer_get</span></span>
<span data-ttu-id="8b2f2-1132">Obtener objeto de número entero</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1132">Get integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1133">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1133">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1134">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1134">Description</span></span>

<span data-ttu-id="8b2f2-1135">Este servicio recupera el objeto de número entero en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1135">This service retrieves the integer object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1136">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1136">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1137">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1137">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1138">**source_ptr** Puntero al origen del número entero.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1138">**source_ptr** Pointer to integer source.</span></span>
- <span data-ttu-id="8b2f2-1139">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1139">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1140">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1140">Return Values</span></span>

- <span data-ttu-id="8b2f2-1141">**NX_SUCCESS** (0x00) El objeto de número entero se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1141">**NX_SUCCESS** (0x00) The integer object has been successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1142">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1142">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1143">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1143">Allowed From</span></span>

<span data-ttu-id="8b2f2-1144">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1145">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1145">Example</span></span>

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a><span data-ttu-id="8b2f2-1146">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1146">nx_snmp_object_integer_set</span></span>
<span data-ttu-id="8b2f2-1147">Establecer objeto de número entero</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1147">Set integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1148">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1148">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1149">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1149">Description</span></span>

<span data-ttu-id="8b2f2-1150">Este servicio establece el número entero en la dirección especificada por el puntero de destino con el valor del número entero en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1150">This service sets the integer at the address specified by the destination pointer with the integer value in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1151">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1151">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1152">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1152">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1153">**destination_ptr** Puntero al destino del número entero.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1153">**destination_ptr** Pointer to integer destination.</span></span>
- <span data-ttu-id="8b2f2-1154">**object_data** Puntero a la estructura del objeto de origen del número entero.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1154">**object_data** Pointer to integer source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1155">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1155">Return Values</span></span>

- <span data-ttu-id="8b2f2-1156">**NX_SUCCESS** (0x00) El objeto de número entero se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1156">**NX_SUCCESS** (0x00) The integer object has been successfully set.</span></span>
- <span data-ttu-id="8b2f2-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1158">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1158">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1159">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1159">Allowed From</span></span>

<span data-ttu-id="8b2f2-1160">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1160">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1161">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1161">Example</span></span>

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a><span data-ttu-id="8b2f2-1162">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1162">nx_snmp_object_ip_address_get</span></span>
<span data-ttu-id="8b2f2-1163">Obtener objeto de dirección IP (solo IPv4)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1163">Get IP address object (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-1164">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1164">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1165">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1165">Description</span></span>

<span data-ttu-id="8b2f2-1166">Este servicio recupera el objeto de dirección IP en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1166">This service retrieves the IP address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1167">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1167">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1168">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1168">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1169">**source_ptr** Puntero al origen de la dirección IPv4.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1169">**source_ptr** Pointer to IPv4 address source.</span></span>
- <span data-ttu-id="8b2f2-1170">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1170">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1171">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1171">Return Values</span></span>

- <span data-ttu-id="8b2f2-1172">**NX_SUCCESS** (0x00) El objeto de dirección IP se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1172">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1173">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1173">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1174">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1174">Allowed From</span></span>

<span data-ttu-id="8b2f2-1175">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1175">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1176">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1176">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a><span data-ttu-id="8b2f2-1177">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1177">nx_snmp_object_ipv6_address_get</span></span>
<span data-ttu-id="8b2f2-1178">Obtener objeto de dirección IP (solo IPv6)</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1178">Get IP address object (IPv6 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="8b2f2-1179">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1179">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1180">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1180">Description</span></span>

<span data-ttu-id="8b2f2-1181">Este servicio recupera el objeto de dirección IPv6 en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1181">This service retrieves the IPv6 address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span>
<span data-ttu-id="8b2f2-1182">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1182">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1183">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1183">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1184">**source_ptr** Puntero al origen de la dirección IPv6.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1184">**source_ptr** Pointer to IPv6 address source.</span></span>
- <span data-ttu-id="8b2f2-1185">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1185">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1186">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1186">Return Values</span></span>

- <span data-ttu-id="8b2f2-1187">**NX_SUCCESS** (0x00) El objeto de dirección IP se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1187">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Código de objeto SNMP de entrada incorrecto.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Incorrect input SNMP object code</span></span>
- <span data-ttu-id="8b2f2-1189">**NX_NOT_ENABLED** (0x14) IPv6 no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1189">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="8b2f2-1190">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1190">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1191">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1191">Allowed From</span></span>

<span data-ttu-id="8b2f2-1192">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1192">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1193">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1193">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a><span data-ttu-id="8b2f2-1194">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1194">nx_snmp_object_ip_address_set</span></span>
<span data-ttu-id="8b2f2-1195">Establecer objeto de dirección IPv4</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1195">Set IPv4 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1196">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1196">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1197">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1197">Description</span></span>

<span data-ttu-id="8b2f2-1198">Este servicio establece la dirección IPv4 en la dirección especificada por el puntero de destino con el valor de la dirección IP en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1198">This service sets the IPv4 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1199">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1199">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1200">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1200">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1201">**destination_ptr** Puntero a la dirección IP que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1201">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="8b2f2-1202">**object_data** Puntero a la estructura del objeto de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1202">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1203">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1203">Return Values</span></span>

- <span data-ttu-id="8b2f2-1204">**NX_SUCCESS** (0x00) El objeto de dirección IP se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1204">**NX_SUCCESS** (0x00) The IP address object has been successfully set.</span></span>
- <span data-ttu-id="8b2f2-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1206">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1206">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1207">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1207">Allowed From</span></span>

<span data-ttu-id="8b2f2-1208">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1209">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1209">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a><span data-ttu-id="8b2f2-1210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1210">nx_snmp_object_ipv6_address_set</span></span>
<span data-ttu-id="8b2f2-1211">Establecer objeto de dirección IPv6</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1211">Set IPv6 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1212">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1212">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1213">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1213">Description</span></span>

<span data-ttu-id="8b2f2-1214">Este servicio establece la dirección IPv6 en la dirección especificada por el puntero de destino con el valor de la dirección IP en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1214">This service sets the IPv6 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1215">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1215">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1216">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1216">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1217">**destination_ptr** Puntero a la dirección IP que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1217">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="8b2f2-1218">**object_data** Puntero a la estructura del objeto de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1218">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1219">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1219">Return Values</span></span>

- <span data-ttu-id="8b2f2-1220">**NX_SUCCESS** (0x00) La dirección IPv6 se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1220">**NX_SUCCESS** (0x00) The IPv6 address has been successfully set.</span></span>
- <span data-ttu-id="8b2f2-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1222">**NX_NOT_ENABLED** (0x14) IPv6 no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1222">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="8b2f2-1223">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1223">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1224">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1224">Allowed From</span></span>

<span data-ttu-id="8b2f2-1225">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1225">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1226">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1226">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a><span data-ttu-id="8b2f2-1227">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1227">nx_snmp_object_no_instance</span></span>
<span data-ttu-id="8b2f2-1228">Establecer objeto "no hay instancia"</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1228">Set no-instance object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1229">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1229">Prototype</span></span>

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1230">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1230">Description</span></span>

<span data-ttu-id="8b2f2-1231">Este servicio crea un objeto que señala que no había ninguna instancia del objeto especificado y normalmente se le llama desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1231">This service creates an object signaling that there was no instance of the specified object and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1232">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1232">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1233">**not_used_ptr** Puntero no utilizado: debe ser NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1233">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="8b2f2-1234">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1234">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1235">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1235">Return Values</span></span>

- <span data-ttu-id="8b2f2-1236">**NX_SUCCESS** (0x00) El objeto "no hay instancia" se ha creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1236">**NX_SUCCESS** (0x00) The no-instance object has been successfully built.</span></span>
- <span data-ttu-id="8b2f2-1237">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1237">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1238">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1238">Allowed From</span></span>

<span data-ttu-id="8b2f2-1239">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1239">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1240">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1240">Example</span></span>

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a><span data-ttu-id="8b2f2-1241">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1241">nx_snmp_object_not_found</span></span>
<span data-ttu-id="8b2f2-1242">Establecer objeto "no encontrado"</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1242">Set not-found object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1243">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1243">Prototype</span></span>

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1244">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1244">Description</span></span>

<span data-ttu-id="8b2f2-1245">Este servicio crea un objeto que señala que no se ha encontrado el objeto y suele llamarse desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1245">This service creates an object signaling the object was not found and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1246">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1246">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1247">**not_used_ptr** Puntero no utilizado: debe ser NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1247">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="8b2f2-1248">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1248">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1249">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1249">Return Values</span></span>

- <span data-ttu-id="8b2f2-1250">**NX_SUCCESS** (0x00) El objeto "no encontrado" se ha creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1250">**NX_SUCCESS** (0x00) The not-found object has been successfully built.</span></span>
- <span data-ttu-id="8b2f2-1251">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1251">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1252">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1252">Allowed From</span></span>

<span data-ttu-id="8b2f2-1253">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1253">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1254">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1254">Example</span></span>

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a><span data-ttu-id="8b2f2-1255">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1255">nx_snmp_object_octet_string_get</span></span>
<span data-ttu-id="8b2f2-1256">Obtener objeto de cadena de octetos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1256">Get octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1257">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1257">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a><span data-ttu-id="8b2f2-1258">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1258">Description</span></span>

<span data-ttu-id="8b2f2-1259">Este servicio recupera la cadena de octetos en la dirección especificada por el puntero de origen y la coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1259">This service retrieves the octet string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1260">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1260">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1261">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1261">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1262">**source_ptr** Puntero al origen de la cadena de octetos.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1262">**source_ptr** Pointer to octet string source.</span></span>
- <span data-ttu-id="8b2f2-1263">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1263">**object_data** Pointer to destination object structure.</span></span>
- <span data-ttu-id="8b2f2-1264">**length** Número de bytes de la cadena de octetos.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1264">**length** Number of bytes in octet string.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1265">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1265">Return Values</span></span>

- <span data-ttu-id="8b2f2-1266">**NX_SUCCESS** (0x00) El objeto de cadena de octetos se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1266">**NX_SUCCESS** (0x00) The octet string object has been successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1267">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1267">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1268">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1268">Allowed From</span></span>

<span data-ttu-id="8b2f2-1269">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1269">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1270">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1270">Example</span></span>

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a><span data-ttu-id="8b2f2-1271">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1271">nx_snmp_object_octet_string_set</span></span>
<span data-ttu-id="8b2f2-1272">Establecer objeto de cadena de octetos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1272">Set octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1273">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1273">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1274">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1274">Description</span></span>

<span data-ttu-id="8b2f2-1275">Este servicio establece la cadena de octetos en la dirección especificada por el puntero de destino con el valor de la cadena de octetos en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1275">This service sets the octet string at the address specified by the destination pointer with the octet string in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1276">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1276">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1277">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1277">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1278">**destination_ptr** Puntero al destino de la cadena de octetos.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1278">**destination_ptr** Pointer to octet string destination.</span></span>
- <span data-ttu-id="8b2f2-1279">**object_data** Puntero a la estructura de objetos del origen de la cadena de octetos.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1279">**object_data** Pointer to octet string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1280">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1280">Return Values</span></span>

- <span data-ttu-id="8b2f2-1281">**NX_SUCCESS** (0x00) El objeto de cadena de octetos se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1281">**NX_SUCCESS** (0x00) The octet string object has been successfully set.</span></span>
- <span data-ttu-id="8b2f2-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1283">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1283">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1284">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1284">Allowed From</span></span>

<span data-ttu-id="8b2f2-1285">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1285">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1286">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1286">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a><span data-ttu-id="8b2f2-1287">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1287">nx_snmp_object_string_get</span></span>
<span data-ttu-id="8b2f2-1288">Obtener objeto de cadena ASCII</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1288">Get ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1289">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1289">Prototype</span></span>

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1290">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1290">Description</span></span>

<span data-ttu-id="8b2f2-1291">Este servicio recupera la cadena ASCII en la dirección especificada por el puntero de origen y la coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1291">This service retrieves the ASCII string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1292">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1292">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1293">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1293">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1294">**source_ptr** Puntero al origen de la cadena ASCII.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1294">**source_ptr** Pointer to ASCII string source.</span></span>
- <span data-ttu-id="8b2f2-1295">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1295">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1296">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1296">Return Values</span></span>

- <span data-ttu-id="8b2f2-1297">**NX_SUCCESS** (0x00) El objeto de cadena ASCII se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1297">**NX_SUCCESS** (0x00) The ASCII string object has been successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1298">**NX_SNMP_ERROR** (0x100) La cadena es demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1298">**NX_SNMP_ERROR** (0x100) String is too big</span></span>  
- <span data-ttu-id="8b2f2-1299">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1299">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1300">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1300">Allowed From</span></span>

<span data-ttu-id="8b2f2-1301">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1301">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1302">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1302">Example</span></span>

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a><span data-ttu-id="8b2f2-1303">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1303">nx_snmp_object_string_set</span></span>
<span data-ttu-id="8b2f2-1304">Establecer objeto de cadena ASCII</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1304">Set ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1305">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1305">Prototype</span></span>

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1306">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1306">Description</span></span>

<span data-ttu-id="8b2f2-1307">Este servicio establece la cadena ASCII en la dirección especificada por el puntero de destino con el valor de la cadena ASCII en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1307">This service sets the ASCII string at the address specified by the destination pointer with the ASCII string in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1308">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1308">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1309">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1309">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1310">**destination_ptr** Puntero al destino de la cadena ASCII.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1310">**destination_ptr** Pointer to ASCII string destination.</span></span>
- <span data-ttu-id="8b2f2-1311">**object_data** Puntero a la estructura de objetos del origen de la cadena ASCII.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1311">**object_data** Pointer to ASCII string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1312">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1312">Return Values</span></span>

- <span data-ttu-id="8b2f2-1313">**NX_SUCCESS** (0x00) El objeto de cadena ASCII se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1313">**NX_SUCCESS** (0x00) The ASCII string object has been successfully set.</span></span>
- <span data-ttu-id="8b2f2-1314">**NX_SNMP_ERROR** (0x100) La cadena es demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1314">**NX_SNMP_ERROR** (0x100) String too large.</span></span>
- <span data-ttu-id="8b2f2-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) Carácter no válido en la cadena.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) Invalid character in string</span></span>
- <span data-ttu-id="8b2f2-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1317">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1317">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1318">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1318">Allowed From</span></span>

<span data-ttu-id="8b2f2-1319">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1319">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1320">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1320">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a><span data-ttu-id="8b2f2-1321">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1321">nx_snmp_object_timetics_get</span></span>
<span data-ttu-id="8b2f2-1322">Obtener objeto timetics</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1322">Get timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1323">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1323">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1324">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1324">Description</span></span>

<span data-ttu-id="8b2f2-1325">Este servicio recupera el objeto timetics en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1325">This service retrieves the timetics at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="8b2f2-1326">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1326">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1327">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1327">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1328">**source_ptr** Puntero al origen del objeto timetics.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1328">**source_ptr** Pointer to timetics source.</span></span>
- <span data-ttu-id="8b2f2-1329">**object_data** Puntero a la estructura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1329">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1330">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1330">Return Values</span></span>

- <span data-ttu-id="8b2f2-1331">**NX_SUCCESS** (0x00) El objeto timetics se ha recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1331">**NX_SUCCESS** (0x00) The timetics object has been successfully retrieved.</span></span>
- <span data-ttu-id="8b2f2-1332">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1332">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1333">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1333">Allowed From</span></span>

<span data-ttu-id="8b2f2-1334">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1334">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1335">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1335">Example</span></span>

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a><span data-ttu-id="8b2f2-1336">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1336">nx_snmp_object_timetics_set</span></span>
<span data-ttu-id="8b2f2-1337">Establecer objeto timetics</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1337">Set timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="8b2f2-1338">Prototipo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1338">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="8b2f2-1339">Descripción</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1339">Description</span></span>

<span data-ttu-id="8b2f2-1340">Este servicio establece el objeto timetics en la dirección especificada por el puntero de destino con el valor del objeto timetics en la estructura de datos del objeto de NetX.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1340">This service sets the timetics variable at the address specified by the destination pointer with the timetics in the NetX object data structure.</span></span>
<span data-ttu-id="8b2f2-1341">Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1341">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8b2f2-1342">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1342">Input Parameters</span></span>

- <span data-ttu-id="8b2f2-1343">**destination_ptr** Puntero al destino del objeto timetics.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1343">**destination_ptr** Pointer to timetics destination.</span></span>
- <span data-ttu-id="8b2f2-1344">**object_data** Puntero a la estructura del objeto de origen del objeto timetics.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1344">**object_data** Pointer to timetics source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="8b2f2-1345">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1345">Return Values</span></span>

- <span data-ttu-id="8b2f2-1346">**NX_SUCCESS** (0x00) El objeto timetics se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1346">**NX_SUCCESS** (0x00) The timetics object has been successfully set.</span></span>
- <span data-ttu-id="8b2f2-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="8b2f2-1348">**NX_PTR_ERROR** (0x07) Puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1348">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8b2f2-1349">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1349">Allowed From</span></span>

<span data-ttu-id="8b2f2-1350">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1350">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="8b2f2-1351">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8b2f2-1351">Example</span></span>

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```