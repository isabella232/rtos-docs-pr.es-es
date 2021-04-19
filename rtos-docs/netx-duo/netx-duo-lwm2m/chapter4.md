---
title: 'Capítulo 4: Descripción de los servicios del cliente LWM2M'
description: Este capítulo contiene una descripción de todos los servicios del cliente LWM2M en orden alfabético.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814673"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a><span data-ttu-id="7e9ce-103">Capítulo 4: Descripción de los servicios del cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="7e9ce-103">Chapter 4  Description of LWM2M CLIENT Services</span></span>

<span data-ttu-id="7e9ce-104">Este capítulo contiene una descripción de todos los servicios del cliente LWM2M siguientes en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-104">This chapter contains a description of all LWM2M Client services listed below in alphabetic order.</span></span>

<span data-ttu-id="7e9ce-105">En la sección "Valores devueltos" de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the  **NX_DISABLE_ERROR_CHECKING** define that is used to disable API  error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="7e9ce-106">**Administración de clientes de LWM2M:**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-106">**LWM2M Client Management:**</span></span>

- <span data-ttu-id="7e9ce-107">nx_lwm2m_client_create: *crear cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-107">nx_lwm2m_client_create: *Create LWM2M Client*</span></span>

- <span data-ttu-id="7e9ce-108">nx_lwm2m_client_delete: *eliminar cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-108">nx_lwm2m_client_delete: *Delete LWM2M Client*</span></span>

- <span data-ttu-id="7e9ce-109">nx_lwm2m_client_lock: *bloquear cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-109">nx_lwm2m_client_lock: *Lock LWM2M Client*</span></span>

- <span data-ttu-id="7e9ce-110">nx_lwm2m_client_unlock: *desbloquear cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-110">nx_lwm2m_client_unlock: *Unlock LWM2M Client*</span></span>

<span data-ttu-id="7e9ce-111">**Administración de sesiones de clientes LWM2M:**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-111">**LWM2M Client Session Management:**</span></span>

- <span data-ttu-id="7e9ce-112">nx_lwm2m_client_session_create: *crear sesión de cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-112">nx_lwm2m_client_session_create: *Create LWM2M Client Session*</span></span>

- <span data-ttu-id="7e9ce-113">nx_lwm2m_client_session_delete: *eliminar sesión de cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-113">nx_lwm2m_client_session_delete: *Delete LWM2M Client Session*</span></span>

- <span data-ttu-id="7e9ce-114">nx_lwm2m_client_session_bootstrap: *iniciar una sesión con un servidor de arranque*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-114">nx_lwm2m_client_session_bootstrap: *Start a session with a Bootstrap Server*</span></span>

- <span data-ttu-id="7e9ce-115">nx_lwm2m_client_session_bootstrap_dtls: *iniciar una sesión segura con un servidor de arranque*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-115">nx_lwm2m_client_session_bootstrap_dtls: *Start a secure session with a Bootstrap Server*</span></span>

- <span data-ttu-id="7e9ce-116">nx_lwm2m_client_session_register_info_get: *obtener información de registro del servidor de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-116">nx_lwm2m_client_session_register_info_get: *Get LWM2M Server register info*</span></span>

- <span data-ttu-id="7e9ce-117">nx_lwm2m_client_session_register: *iniciar una sesión con un servidor de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-117">nx_lwm2m_client_session_register: *Start a session with a LWM2M Server*</span></span>

- <span data-ttu-id="7e9ce-118">nx_lwm2m_client_session_register_dtls: *iniciar una sesión segura con un servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-118">nx_lwm2m_client_session_register_dtls: *Start a secure session with a LWM2M Server*</span></span>

- <span data-ttu-id="7e9ce-119">nx_lwm2m_client_session_update: *actualizar una sesión con un servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-119">nx_lwm2m_client_session_update: *Update a session with a LWM2M Server*</span></span>

- <span data-ttu-id="7e9ce-120">nx_lwm2m_client_session_deregister: *finalizar una sesión con un servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-120">nx_lwm2m_client_session_deregister: *Terminate a session with a LWM2M Server*</span></span>

- <span data-ttu-id="7e9ce-121">nx_lwm2m_client_session_error_get: *obtener el último error de una sesión*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-121">nx_lwm2m_client_session_error_get: *Get last error of a session*</span></span>

<span data-ttu-id="7e9ce-122">**Implementación de objetos de dispositivo:**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-122">**Device Object Implementation:**</span></span>

- <span data-ttu-id="7e9ce-123">nx_lwm2m_client_device_callbacks_set: *establecer devoluciones de llamada de aplicaciones de objetos de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-123">nx_lwm2m_client_device_callbacks_set: *Set Device Object application callbacks*</span></span>

- <span data-ttu-id="7e9ce-124">nx_lwm2m_client_device_error_push: *agregar un código de error a un objeto de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-124">nx_lwm2m_client_device_error_push: *Add error code to Device Object*</span></span>

- <span data-ttu-id="7e9ce-125">nx_lwm2m_client_device_error_reset: *restablecer códigos de error de un objeto de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-125">nx_lwm2m_client_device_error_reset: *Reset error codes of Device Object*</span></span>

- <span data-ttu-id="7e9ce-126">nx_lwm2m_client_device_resource_changed: *cambio de señal de un recurso de objeto de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-126">nx_lwm2m_client_device_resource_changed: *Signal change of Device Object resource*</span></span>

<span data-ttu-id="7e9ce-127">**Implementación de objetos de actualización de firmware:**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-127">**Firmware Update Object Implementation:**</span></span>

- <span data-ttu-id="7e9ce-128">nx_lwm2m_firmware_create: *crear un objeto de actualización de firmware*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-128">nx_lwm2m_firmware_create: *Create Firmware Update Object*</span></span>

- <span data-ttu-id="7e9ce-129">nx_lwm2m_firmware_package_info_set: *establecer la información de paquetes de actualización de firmware*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-129">nx_lwm2m_firmware_package_info_set: *Set Firmware Update Package Information*</span></span>

- <span data-ttu-id="7e9ce-130">nx_lwm2m_firmware_result_set: *establecer el resultado de la actualización de firmware*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-130">nx_lwm2m_firmware_result_set: *Set Firmware Update Result*</span></span>

- <span data-ttu-id="7e9ce-131">nx_lwm2m_firmware_state_set: *establecer el estado de la actualización de firmware*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-131">nx_lwm2m_firmware_state_set: *Set Firmware Update State*</span></span>

<span data-ttu-id="7e9ce-132">**Implementación de objetos personalizados:**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-132">**Custom Objects Implementation:**</span></span>

- <span data-ttu-id="7e9ce-133">nx_lwm2m_client_object_add: *agregar implementación de objeto al cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-133">nx_lwm2m_client_object_add: *Add Object implementation to LWM2M Client*</span></span>

- <span data-ttu-id="7e9ce-134">nx_lwm2m_client_object_remove: *quitar implementación de objeto del cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-134">nx_lwm2m_client_object_remove: *Remove Object implementation from LWM2M Client*</span></span>

- <span data-ttu-id="7e9ce-135">nx_lwm2m_client_object_instance_add: *agregar instancia de objeto al cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-135">nx_lwm2m_client_object_instance_add: *Add Object Instance to LWM2M Client*</span></span>

- <span data-ttu-id="7e9ce-136">nx_lwm2m_client_object_instance_remove: *quitar instancia de objeto del cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-136">nx_lwm2m_client_object_instance_remove: *Remove Object Instance from LWM2M Client*</span></span>

- <span data-ttu-id="7e9ce-137">nx_lwm2m_object_resource_changed: *cambio de señal del valor de un recurso de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-137">nx_lwm2m_object_resource_changed: *Signal change of a resource value of an Object Instance*</span></span>

<span data-ttu-id="7e9ce-138">**Administración de dispositivos locales:**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-138">**Local Device Management**</span></span>

- <span data-ttu-id="7e9ce-139">nx_lwm2m_client_object_create: *crear una nueva instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-139">nx_lwm2m_client_object_create: *Create a new Object Instance*</span></span>

- <span data-ttu-id="7e9ce-140">nx_lwm2m_client_object_delete: *eliminar una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-140">nx_lwm2m_client_object_delete: *Delete an Object Instance*</span></span>

- <span data-ttu-id="7e9ce-141">nx_lwm2m_client_object_discover: *detectar recursos de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-141">nx_lwm2m_client_object_discover: *Discover resources of an Object Instance*</span></span>

- <span data-ttu-id="7e9ce-142">nx_lwm2m_client_object_execute: *ejecutar el recurso de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-142">nx_lwm2m_client_object_execute: *Execute resource of an Object Instance*</span></span>

- <span data-ttu-id="7e9ce-143">nx_lwm2m_client_object_next_get: *obtener la lista de objetos implementados por el cliente LWM2M*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-143">nx_lwm2m_client_object_next_get: *Get the list of Objects implemented by the LWM2M Client*</span></span>

- <span data-ttu-id="7e9ce-144">nx_lwm2m_client_object_instance_next_get: *obtener la lista de instancias de un objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-144">nx_lwm2m_client_object_instance_next_get: *Get the list of Instances of an Object*</span></span>

- <span data-ttu-id="7e9ce-145">nx_lwm2m_client_object_read: *leer los valores de los recursos de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-145">nx_lwm2m_client_object_read: *Read resources values of an Object Instance*</span></span>

- <span data-ttu-id="7e9ce-146">nx_lwm2m_client_object_write: *cambiar los valores de los recursos de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-146">nx_lwm2m_client_object_write: *Change resources values of an Object instance*</span></span>

<span data-ttu-id="7e9ce-147">**Configuración de valores e información de recursos:**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-147">**Resources Info and Values Setting:**</span></span>

- <span data-ttu-id="7e9ce-148">nx_lwm2m_client_resource_info_set: *establecer la información de los recursos*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-148">nx_lwm2m_client_resource_info_set: *Set the resource info*</span></span>

- <span data-ttu-id="7e9ce-149">nx_lwm2m_client_resource_string_set: *establecer el valor del recurso como una cadena*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-149">nx_lwm2m_client_resource_string_set: *Set the resource value as string*</span></span>

- <span data-ttu-id="7e9ce-150">nx_lwm2m_client_resource_integer32_set: *establecer el valor del recurso como un entero de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-150">nx_lwm2m_client_resource_integer32_set: *Set the resource value as 32-Bit integer*</span></span>

- <span data-ttu-id="7e9ce-151">nx_lwm2m_client_resource_integer64_set: *establecer el valor del recurso como un entero de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-151">nx_lwm2m_client_resource_integer64_set: *Set the resource value as 64-Bit integer*</span></span>

- <span data-ttu-id="7e9ce-152">nx_lwm2m_client_resource_float32_set: *establecer el recurso en un valor flotante de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-152">nx_lwm2m_client_resource_float32_set: *Set the resource value as 32-Bit float*</span></span>

- <span data-ttu-id="7e9ce-153">nx_lwm2m_client_resource_float64_set: *establecer el recurso en un valor flotante de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-153">nx_lwm2m_client_resource_float64_set: *Set the resource value as 64-Bit float*</span></span>

- <span data-ttu-id="7e9ce-154">nx_lwm2m_client_resource_boolean_set: *establecer el recurso en un valor booleano*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-154">nx_lwm2m_client_resource_boolean_set: *Set the resource value as boolean*</span></span>

- <span data-ttu-id="7e9ce-155">nx_lwm2m_client_resource_objlnk_set: *establecer el valor del recurso como un vínculo de objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-155">nx_lwm2m_client_resource_objlnk_set: *Set the resource value as object link*</span></span>

- <span data-ttu-id="7e9ce-156">nx_lwm2m_client_resource_opaque_set: *establecer el valor del recurso como opaco*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-156">nx_lwm2m_client_resource_opaque_set: *Set the resource value as opaque*</span></span>

- <span data-ttu-id="7e9ce-157">nx_lwm2m_client_resource_instance_set: *establecer el valor del recurso como una instancia para varios recursos*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-157">nx_lwm2m_client_resource_instance_set: *Set the resource value as instance for multiple resource*</span></span>
-
- <span data-ttu-id="7e9ce-158">nx_lwm2m_client_resource_dim_set: *establecer la dimensión del recurso para varios recursos.*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-158">nx_lwm2m_client_resource_dim_set: *Set the resource dimension for multiple resource.*</span></span>

<span data-ttu-id="7e9ce-159">**Obtención de valores e información de recursos:**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-159">**Resources Info and Values Getting:**</span></span>

- <span data-ttu-id="7e9ce-160">nx_lwm2m_client_resource_info_get: *obtener la información de los recursos*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-160">nx_lwm2m_client_resource_info_get: *Get the resource info*</span></span>

- <span data-ttu-id="7e9ce-161">nx_lwm2m_client_resource_string_get: *obtener el valor de un recurso string*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-161">nx_lwm2m_client_resource_string_get: *Get the value of a string resource*</span></span>

- <span data-ttu-id="7e9ce-162">nx_lwm2m_client_resource_integer32_get: *obtener el valor de un recurso integer de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-162">nx_lwm2m_client_resource_integer32_get: *Get the value of a 32-Bit integer resource*</span></span>

- <span data-ttu-id="7e9ce-163">nx_lwm2m_client_resource_integer64_get: *obtener el valor de un recurso integer de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-163">nx_lwm2m_client_resource_integer64_get: *Get the value of a 64-Bit integer resource*</span></span>

- <span data-ttu-id="7e9ce-164">nx_lwm2m_client_resource_float32_get: *obtener el valor de un recurso flotante de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-164">nx_lwm2m_client_resource_float32_get: *Get the value of a 32-Bit float resource*</span></span>

- <span data-ttu-id="7e9ce-165">nx_lwm2m_client_resource_float64_get: *obtener el valor de un recurso flotante de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-165">nx_lwm2m_client_resource_float64_get: *Get the value of a 64-Bit float resource*</span></span>

- <span data-ttu-id="7e9ce-166">nx_lwm2m_client_resource_boolean_get: *obtener el valor de un recurso boolean*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-166">nx_lwm2m_client_resource_boolean_get: *Get the value of a boolean resource*</span></span>

- <span data-ttu-id="7e9ce-167">nx_lwm2m_client_resource_objlnk_get: *obtener el valor de un recurso de vínculo de objeto*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-167">nx_lwm2m_client_resource_objlnk_get: *Get the value of an object link resource*</span></span>

- <span data-ttu-id="7e9ce-168">nx_lwm2m_client_resource_opaque_get: *obtener el valor de un recurso opaque*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-168">nx_lwm2m_client_resource_opaque_get: *Get the value of an opaque resource*</span></span>

- <span data-ttu-id="7e9ce-169">nx_lwm2m_client_resource_instance_get: *obtener la instancia de recurso para varios recursos*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-169">nx_lwm2m_client_resource_instance_get: *Get the resource instance for multiple resource*</span></span>

- <span data-ttu-id="7e9ce-170">nx_lwm2m_client_resource_dim_get: *obtener la dimensión de recurso para varios recursos.*</span><span class="sxs-lookup"><span data-stu-id="7e9ce-170">nx_lwm2m_client_resource_dim_get: *Get the resource dimension for multiple resource.*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="7e9ce-171">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="7e9ce-171">nx_lwm2m_client_create</span></span>

<span data-ttu-id="7e9ce-172">Crea un cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-172">Creates a LWM2M client.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-173">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-173">Prototype</span></span>

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="7e9ce-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-174">Description</span></span>

<span data-ttu-id="7e9ce-175">Este servicio crea una instancia de cliente LWM2M que se ejecuta en el contexto de su propio subproceso ThreadX.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-175">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="7e9ce-176">El cliente LWM2M implementa los siguientes objetos OMA LWM2M: Security (0), Server (1), Access Control (2) y Device (3).</span><span class="sxs-lookup"><span data-stu-id="7e9ce-176">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="7e9ce-177">La aplicación debe agregar las implementaciones de otros objetos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-177">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-178">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-178">Parameters</span></span>

- <span data-ttu-id="7e9ce-179">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-179">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-180">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-180">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7e9ce-181">**packet_pool_ptr**: puntero al grupo de paquetes predeterminado para este cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-181">**packet_pool_ptr** Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="7e9ce-182">**name_ptr**: puntero al nombre de punto de conexión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-182">**name_ptr** Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="7e9ce-183">**name_length**: longitud del nombre del punto de conexión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-183">**name_length** Length of LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="7e9ce-184">**msisdn_ptr**: puntero a MSISDN, donde se puede acceder al cliente LWM2M para su uso con el enlace SMS; puede ser NULL si no se admite el enlace SMS.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-184">**msisdn_ptr** Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="7e9ce-185">**msisdn_length**: longitud del número MSISDN.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-185">**msisdn_length** Length of MSISDN number.</span></span>
- <span data-ttu-id="7e9ce-186">**binding_modes**: el enlace y los modos admitidos que admite el cliente LWM2M, deben ser una combinación de las marcas NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S y NX_LWM2M_BINDING_SQ.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-186">**binding_modes** The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="7e9ce-187">**stack_ptr**: puntero al área de la pila de subprocesos del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-187">**stack_ptr** Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="7e9ce-188">**stack_size**: tamaño de la pila de subprocesos del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-188">**stack_size** The LWM2M Client thread stack size.</span></span>
- <span data-ttu-id="7e9ce-189">**priority**: prioridad del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-189">**priority** Priority of LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-190">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-190">Return Values</span></span>

- <span data-ttu-id="7e9ce-191">**NX_SUCCESS**: el cliente LWM2M se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-191">**NX_SUCCESS** The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="7e9ce-192">**NX_LWM2M_CLIENT_ERROR**: error al crear el cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-192">**NX_LWM2M_CLIENT_ERROR** LWM2M Client create error.</span></span>
- <span data-ttu-id="7e9ce-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="7e9ce-194">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-194">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="7e9ce-195">**NX_SIZE_ERROR**: tamaño de pila no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-195">**NX_SIZE_ERROR** Invalid stack size.</span></span>
- <span data-ttu-id="7e9ce-196">**NX_OPTION_ERROR**: prioridad no válida.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-196">**NX_OPTION_ERROR** Invalid priority.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-197">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-197">Allowed From</span></span>

<span data-ttu-id="7e9ce-198">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-198">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-199">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-199">Example</span></span>

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="7e9ce-200">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="7e9ce-200">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="7e9ce-201">Elimina un cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-201">Deletes a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-202">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-202">Prototype</span></span>

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-203">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-203">Description</span></span>

<span data-ttu-id="7e9ce-204">Este servicio elimina una instancia de cliente LWM2M creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-204">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="7e9ce-205">Esta llamada también elimina todas las sesiones asociadas actualmente al cliente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-205">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-206">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-206">Parameters</span></span>

- <span data-ttu-id="7e9ce-207">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-207">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-208">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-208">Return Values</span></span>

- <span data-ttu-id="7e9ce-209">**NX_SUCCESS**: el cliente LWM2M se eliminó correctamente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-209">**NX_SUCCESS** The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="7e9ce-210">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-210">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-211">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-211">Allowed From</span></span>

<span data-ttu-id="7e9ce-212">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-212">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-213">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-213">Example</span></span>

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a><span data-ttu-id="7e9ce-214">nx_lwm2m_client_device_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-214">nx_lwm2m_client_device_callback_set</span></span>

<span data-ttu-id="7e9ce-215">Establece la devolución de llamada de la aplicación de un objeto de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-215">Sets a device object's application callback.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-216">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-216">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a><span data-ttu-id="7e9ce-217">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-217">Description</span></span>

<span data-ttu-id="7e9ce-218">Este servicio instala la devolución de llamada de la aplicación para implementar operaciones en los recursos de objeto de dispositivo de LWM2M que no controla el cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-218">This service installs the application callback for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="7e9ce-219">El cliente LWM2M implementa los siguientes recursos: Error Code (11), Reset Error Code (12) y Supported Binding and Modes (16); las operaciones con los demás recursos se redirigen a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-219">The LWM2M Client implements the following resources: Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-220">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-220">Parameters</span></span>

- <span data-ttu-id="7e9ce-221">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-221">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-222">**operation_callback**: devolución de llamada de operación de lectura, detección, escritura y ejecución.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-222">**operation_callback** The operation callback for “Read”, “Discover”, “Write” and “Execute”.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-223">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-223">Return Values</span></span>

- <span data-ttu-id="7e9ce-224">**NX_SUCCESS**: la devolución de llamada de la operación se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-224">**NX_SUCCESS** The operation callback has been successfully set.</span></span>
- <span data-ttu-id="7e9ce-225">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-225">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-226">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-226">Allowed From</span></span>

<span data-ttu-id="7e9ce-227">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-227">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-228">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-228">Example</span></span>

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="7e9ce-229">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="7e9ce-229">nx_lwm2m_client_device_error_push</span></span>
<span data-ttu-id="7e9ce-230">Agrega un código de error a un objeto de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-230">Adds an error code to a device object.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-231">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-231">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a><span data-ttu-id="7e9ce-232">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-232">Description</span></span>

<span data-ttu-id="7e9ce-233">Este servicio agrega una nueva instancia al recurso Error Code (11) del dispositivo de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-233">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-234">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-234">Parameters</span></span>

- <span data-ttu-id="7e9ce-235">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-235">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-236">**code**: nuevo código de error.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-236">**code** The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-237">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-237">Return Values</span></span>

- <span data-ttu-id="7e9ce-238">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-238">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span></span>

<span data-ttu-id="7e9ce-240">Se alcanzó el número máximo de códigos de error</span><span class="sxs-lookup"><span data-stu-id="7e9ce-240">The maximum number of stored error codes has</span></span>

<span data-ttu-id="7e9ce-241">almacenados.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-241">been reached.</span></span>

<span data-ttu-id="7e9ce-242">NX_PTR_ERROR: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-242">NX_PTR_ERROR Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-243">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-243">Allowed From</span></span>

<span data-ttu-id="7e9ce-244">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-244">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-245">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-245">Example</span></span>

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="7e9ce-246">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="7e9ce-246">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="7e9ce-247">Restablece los códigos de error del objeto de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-247">Resets the error codes of Device Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-248">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-248">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-249">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-249">Description</span></span>

<span data-ttu-id="7e9ce-250">Este servicio elimina todas las instancias de recursos de código de error del objeto de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-250">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="7e9ce-251">Esto es equivalente a la ejecución del recurso Reset Error Code (12).</span><span class="sxs-lookup"><span data-stu-id="7e9ce-251">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-252">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-252">Parameters</span></span>

- <span data-ttu-id="7e9ce-253">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-253">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-254">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-254">Return Values</span></span>

- <span data-ttu-id="7e9ce-255">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-255">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-256">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-256">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-257">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-257">Allowed From</span></span>

<span data-ttu-id="7e9ce-258">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-258">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-259">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-259">Example</span></span>

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="7e9ce-260">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="7e9ce-260">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="7e9ce-261">Indica un cambio en un recurso de objeto de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-261">Signals a change to a Device Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-262">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-262">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a><span data-ttu-id="7e9ce-263">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-263">Description</span></span>

<span data-ttu-id="7e9ce-264">La aplicación usa el servicio para indicar al cliente LWM2M que un recurso del dispositivo de objeto ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-264">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="7e9ce-265">El cliente LWM2M enviará una notificación si un servidor LWM2M observa el recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-265">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-266">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-266">Parameters</span></span>

- <span data-ttu-id="7e9ce-267">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-267">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-268">**resource**: puntero a la estructura que describe el recurso que ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-268">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-269">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-269">Return Values</span></span>

- <span data-ttu-id="7e9ce-270">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-270">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-271">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-271">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-272">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-272">Allowed From</span></span>

<span data-ttu-id="7e9ce-273">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-273">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-274">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-274">Example</span></span>

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a><span data-ttu-id="7e9ce-275">nx_lwm2m_client_firmware_create</span><span class="sxs-lookup"><span data-stu-id="7e9ce-275">nx_lwm2m_client_firmware_create</span></span>

<span data-ttu-id="7e9ce-276">Cree un objeto de firmware de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-276">Create a LWM2M Client Firmware Object.</span></span> 

### <a name="prototype"></a><span data-ttu-id="7e9ce-277">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-277">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="7e9ce-278">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-278">Description</span></span>

<span data-ttu-id="7e9ce-279">La aplicación usa el servicio para crear el objeto de firmware.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-279">The service is used by the application to create firmware object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-280">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-280">Parameters</span></span>

- <span data-ttu-id="7e9ce-281">**firmware_ptr**: puntero al objeto de firmware de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-281">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="7e9ce-282">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-282">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-283">**protocols**: protocolos admitidos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-283">**protocols** The supported protocols.</span></span>
- <span data-ttu-id="7e9ce-284">**package_callback**: devolución de llamada del paquete.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-284">**package_callback** The package callback.</span></span>
- <span data-ttu-id="7e9ce-285">**package_uri_callback**: devolución de llamada del URI del paquete.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-285">**package_uri_callback** The package URI callback.</span></span>
- <span data-ttu-id="7e9ce-286">**update_callback**: devolución de llamada de actualización.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-286">**update_callback** The update callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-287">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-287">Return Values</span></span>

<span data-ttu-id="7e9ce-288">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-288">**NX_SUCCESS** Successful operation.</span></span>
<span data-ttu-id="7e9ce-289">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-289">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-290">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-290">Allowed From</span></span>

<span data-ttu-id="7e9ce-291">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-291">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-292">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-292">Example</span></span>

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a><span data-ttu-id="7e9ce-293">nx_lwm2m_client_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-293">nx_lwm2m_client_firmware_package_info_set</span></span>

<span data-ttu-id="7e9ce-294">Establece la información de paquetes de firmware del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-294">Sets the LWM2M Client Firmware package information.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-295">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-295">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a><span data-ttu-id="7e9ce-296">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-296">Description</span></span>

<span data-ttu-id="7e9ce-297">La aplicación usa el servicio para establecer los recursos de información de paquetes del objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-297">The service is used by the application to set the package information resources of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-298">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-298">Parameters</span></span>

- <span data-ttu-id="7e9ce-299">**firmware_ptr**: puntero al objeto de firmware de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-299">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="7e9ce-300">**name**: nombre del paquete de firmware.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-300">**name** The name of firmware package.</span></span>
- <span data-ttu-id="7e9ce-301">**name_length**: longitud del nombre.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-301">**name_length** The length of name.</span></span>
- <span data-ttu-id="7e9ce-302">**version**: versión del paquete de firmware.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-302">**version** The version of firmware package.</span></span>
- <span data-ttu-id="7e9ce-303">**version_length**: longitud de la versión.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-303">**version_length** The length of version.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-304">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-304">Return Values</span></span>

- <span data-ttu-id="7e9ce-305">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-305">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-306">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-306">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-307">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-307">Allowed From</span></span>

<span data-ttu-id="7e9ce-308">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-308">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-309">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-309">Example</span></span>

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a><span data-ttu-id="7e9ce-310">nx_lwm2m_client_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-310">nx_lwm2m_client_firmware_result_set</span></span>

<span data-ttu-id="7e9ce-311">Establece el recurso de resultado de la actualización del objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-311">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-312">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-312">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="7e9ce-313">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-313">Description</span></span>

<span data-ttu-id="7e9ce-314">La aplicación usa el servicio para establecer el recurso de resultado de la actualización del objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-314">The service is used by the application to set the update result resource of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-315">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-315">Parameters</span></span>

- <span data-ttu-id="7e9ce-316">**firmware_ptr**: puntero al objeto de firmware de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-316">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="7e9ce-317">**result**: resultado de la actualización.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-317">**result** The update result.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-318">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-318">Return Values</span></span>

- <span data-ttu-id="7e9ce-319">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-319">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-320">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-320">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-321">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-321">Allowed From</span></span>

<span data-ttu-id="7e9ce-322">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-322">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-323">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-323">Example</span></span>

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a><span data-ttu-id="7e9ce-324">nx_lwm2m_client_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-324">nx_lwm2m_client_firmware_state_set</span></span>

<span data-ttu-id="7e9ce-325">Establece el recurso de resultado de la actualización del objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-325">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-326">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-326">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="7e9ce-327">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-327">Description</span></span>

<span data-ttu-id="7e9ce-328">La aplicación usa el servicio para establecer el estado del objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-328">The service is used by the application to set the state of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-329">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-329">Parameters</span></span>

- <span data-ttu-id="7e9ce-330">**firmware_ptr**: puntero al objeto de firmware de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-330">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="7e9ce-331">**state**: estado del objeto de firmware.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-331">**state** The state of the firmware object.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-332">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-332">Return Values</span></span>

- <span data-ttu-id="7e9ce-333">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-333">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-334">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-334">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-335">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-335">Allowed From</span></span>

<span data-ttu-id="7e9ce-336">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-336">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-337">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-337">Example</span></span>

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="7e9ce-338">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="7e9ce-338">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="7e9ce-339">Bloquea el cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-339">Locks the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-340">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-340">Prototype</span></span>

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-341">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-341">Description</span></span>

<span data-ttu-id="7e9ce-342">Este servicio bloquea el cliente LWM2M para impedir el acceso simultáneo a los objetos LWM2M desde los servidores o desde otro subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-342">This service locks the LWM2M Client to prevent concurrent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="7e9ce-343">Si el cliente LWM2M está bloqueado actualmente por otro subproceso, la función se bloqueará hasta que dicho cliente se desbloquee.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-343">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="7e9ce-344">Las llamadas a pares ***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** se pueden anidar.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-344">Calls to \***nx_lwm2m_client_lock**_/_*_nx_lwm2m_client_unlock_*\* pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-345">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-345">Parameters</span></span>

- <span data-ttu-id="7e9ce-346">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-346">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-347">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-347">Return Values</span></span>

- <span data-ttu-id="7e9ce-348">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-348">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-349">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-349">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-350">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-350">Allowed From</span></span>

<span data-ttu-id="7e9ce-351">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-351">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-352">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-352">Example</span></span>

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="7e9ce-353">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="7e9ce-353">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="7e9ce-354">Agrega una implementación de objeto al cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-354">Adds an Object implementation to the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-355">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-355">Prototype</span></span>

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a><span data-ttu-id="7e9ce-356">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-356">Description</span></span>

<span data-ttu-id="7e9ce-357">Este servicio agrega una nueva implementación de objeto al cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-357">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-358">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-358">Parameters</span></span>

- <span data-ttu-id="7e9ce-359">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-359">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-360">**object_ptr**: puntero a la estructura que define la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-360">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="7e9ce-361">**object_id**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-361">**object_id** The object id.</span></span>
- <span data-ttu-id="7e9ce-362">**object_operation**: función de devolución de llamada de la operación de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-362">**object_operation** The object operation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-363">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-363">Return Values</span></span>

- <span data-ttu-id="7e9ce-364">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-364">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-365">**NX_LWM2M_ALREADY_EXIST**: el id. de objeto ya existe.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="7e9ce-366">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-366">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-367">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-367">Allowed From</span></span>

<span data-ttu-id="7e9ce-368">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-368">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-369">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-369">Example</span></span>

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="7e9ce-370">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="7e9ce-370">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="7e9ce-371">Crea una nueva instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-371">Creates a new Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-372">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-372">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-373">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-373">Description</span></span>

<span data-ttu-id="7e9ce-374">Este servicio realiza una operación de creación en un objeto del cliente LWM2M para crear una nueva instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-374">This service performs a ‘Create’ operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-375">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-375">Parameters</span></span>

- <span data-ttu-id="7e9ce-376">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-376">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-377">**object_id**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-377">**object_id** The Object ID.</span></span>
- <span data-ttu-id="7e9ce-378">**instance_id_ptr**: puntero al identificador de la nueva instancia, puede ser **NULL** si el cliente LWM2M debe asignar un id. de instancia.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-378">**instance_id_ptr** Pointer to the ID of the new instance, can be **NULL** if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="7e9ce-379">Si el identificador es el valor reservado 65535, el cliente LWM2M asignará un id. de instancia.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-379">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="7e9ce-380">Si no es NULL, el identificador asignado se devuelve después de la llamada.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-380">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="7e9ce-381">**num_values**: número de valores que se van a establecer.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-381">**num_values** The number of values to set.</span></span>
- <span data-ttu-id="7e9ce-382">**values_ptr**: puntero a una matriz de valores de recursos para inicializar la nueva instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-382">**values_ptr** Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-383">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-383">Return Values</span></span>

- <span data-ttu-id="7e9ce-384">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-384">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-385">**NX_LWM2M_ClIENT_ALREADY_EXIST**: el id. de instancia de objeto ya existe.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object Instance ID already exists.</span></span>
- <span data-ttu-id="7e9ce-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**: el objeto no admite la creación de instancias.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance creation.</span></span>
- <span data-ttu-id="7e9ce-387">**NX_LWM2M_CLIENT_NO_MEMORY**: no se puede asignar memoria para almacenar la nueva instancia.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-387">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="7e9ce-388">**NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto no existe.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-388">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID doesn’t exist.</span></span>
- <span data-ttu-id="7e9ce-389">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-389">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-390">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-390">Allowed From</span></span>

<span data-ttu-id="7e9ce-391">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-391">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-392">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-392">Example</span></span>

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="7e9ce-393">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="7e9ce-393">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="7e9ce-394">Elimina una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-394">Deletes an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-395">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-395">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="7e9ce-396">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-396">Description</span></span>

<span data-ttu-id="7e9ce-397">Este servicio realiza una operación de eliminación en una instancia de objeto del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-397">This service performs a ‘Delete’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-398">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-398">Parameters</span></span>

- <span data-ttu-id="7e9ce-399">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-399">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-400">**object_id**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-400">**object_id** The Object ID.</span></span>
- <span data-ttu-id="7e9ce-401">**instance_id**: identificador de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-401">**instance_id** The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-402">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-402">Return Values</span></span>

- <span data-ttu-id="7e9ce-403">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-403">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**: el objeto no admite la eliminación de instancias.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance deletion.</span></span>
- <span data-ttu-id="7e9ce-405">**NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto o el id. de instancia de objeto no existen.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-405">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="7e9ce-406">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-406">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-407">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-407">Allowed From</span></span>

<span data-ttu-id="7e9ce-408">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-408">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-409">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-409">Example</span></span>

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="7e9ce-410">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="7e9ce-410">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="7e9ce-411">Detecta recursos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-411">Discovers resources of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-412">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-412">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a><span data-ttu-id="7e9ce-413">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-413">Description</span></span>

<span data-ttu-id="7e9ce-414">Este servicio realiza una operación de detección en una instancia de objeto del cliente LWM2M, que devuelve la lista de recursos implementados por el objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-414">This service performs a ‘Discover’ operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-415">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-415">Parameters</span></span>

- <span data-ttu-id="7e9ce-416">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-416">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-417">**object_id**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-417">**object_id** The Object ID.</span></span>
- <span data-ttu-id="7e9ce-418">**instance_id**: identificador de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-418">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="7e9ce-419">**num_resources**: en la entrada, el tamaño del búfer de destino; en la salida, el número de elementos escritos en el búfer.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-419">**num_resources** On input the size of the destination buffer, on output the number of elements written to the buffer.</span></span>
- <span data-ttu-id="7e9ce-420">**resources**: puntero al búfer de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-420">**resources** Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-421">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-421">Return Values</span></span>

- <span data-ttu-id="7e9ce-422">\*NX_SUCCESS\*\*: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-422">*NX_SUCCESS*\* Successful operation.</span></span>
- <span data-ttu-id="7e9ce-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**: el búfer de recursos es demasiado pequeño para almacenar la lista de recursos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="7e9ce-424">**NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto o el id. de instancia de objeto no existen.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-424">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="7e9ce-425">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-425">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-426">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-426">Allowed From</span></span>

<span data-ttu-id="7e9ce-427">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-427">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-428">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-428">Example</span></span>

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="7e9ce-429">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="7e9ce-429">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="7e9ce-430">Realiza una operación de ejecución en un recurso de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-430">Performs an 'Execute' operation on a resource of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-431">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-431">Prototype</span></span>

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="7e9ce-432">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-432">Description</span></span>

<span data-ttu-id="7e9ce-433">Este servicio realiza una operación de ejecución en un recurso de una instancia de objeto del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-433">This service performs the ‘Execute’ operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-434">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-434">Parameters</span></span>

- <span data-ttu-id="7e9ce-435">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-435">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-436">**object_id**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-436">**object_id** The Object ID.</span></span>
- <span data-ttu-id="7e9ce-437">**instance_id**: identificador de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-437">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="7e9ce-438">**resource_id**: identificador del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-438">**resource_id** The Resource ID.</span></span>
- <span data-ttu-id="7e9ce-439">**arguments_ptr**: puntero a los argumentos de la operación de ejecución.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-439">**arguments_ptr** Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="7e9ce-440">Puede ser NULL si arguments_length es cero.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-440">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="7e9ce-441">**arguments_length**: longitud de los argumentos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-441">**arguments_length** The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-442">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-442">Return Values</span></span>

- <span data-ttu-id="7e9ce-443">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-443">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**: el búfer de recursos es demasiado pequeño para almacenar la lista de recursos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="7e9ce-445">**NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto o el id. de instancia de objeto no existen.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-445">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="7e9ce-446">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-446">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-447">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-447">Allowed From</span></span>

<span data-ttu-id="7e9ce-448">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-448">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-449">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-449">Example</span></span>

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a><span data-ttu-id="7e9ce-450">nx_lwm2m_client_object_instance_add</span><span class="sxs-lookup"><span data-stu-id="7e9ce-450">nx_lwm2m_client_object_instance_add</span></span>

<span data-ttu-id="7e9ce-451">Agrega una implementación de instancia de objeto a un objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-451">Adds an Object instance implementation to an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-452">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-452">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-453">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-453">Description</span></span>

<span data-ttu-id="7e9ce-454">Este servicio agrega una nueva implementación de instancia de objeto al cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-454">This service adds a new Object instance implementation to the LWM2M Client.</span></span> <span data-ttu-id="7e9ce-455">Si el valor de instance_id_ptr es **NX_LWM2M_CLIENT_RESERVED_ID**, el cliente LWM2M asignará automáticamente un id. de instancia no utilizado; de lo contrario, el cliente LWM2M usará el valor de la aplicación establecido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-455">If the value of instance_id_ptr is **NX_LWM2M_CLIENT_RESERVED_ID**, LWM2M Client will automatically assign an unused instance id, otherwise, LWM2M Client will use the value application set.</span></span> <span data-ttu-id="7e9ce-456">Después de agregar la nueva instancia correctamente, el campo instance_id se rellenará en instance_id_ptr para volver a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-456">Once new instance was added successfully, the instance_id will be filled in instance_id_ptr to return to application.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-457">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-457">Parameters</span></span>

- <span data-ttu-id="7e9ce-458">**object_ptr**: puntero a la estructura que define la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-458">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="7e9ce-459">**instance_ptr**: puntero a la estructura que define la implementación de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-459">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="7e9ce-460">**instance_id_ptr**: puntero al id. de instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-460">**instance_id_ptr** Pointer to the object instance id.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-461">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-461">Return Values</span></span>

- <span data-ttu-id="7e9ce-462">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-462">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-463">**NX_CLIENT_LWM2M_ALREADY_EXIST**: el id. de objeto ya existe.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="7e9ce-464">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-464">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-465">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-465">Allowed From</span></span>

<span data-ttu-id="7e9ce-466">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-466">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-467">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-467">Example</span></span>

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a><span data-ttu-id="7e9ce-468">nx_lwm2m_client_object_instance_next_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-468">nx_lwm2m_client_object_instance_next_get</span></span>

<span data-ttu-id="7e9ce-469">Obtiene la siguiente instancia de un objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-469">Gets the next instance of an Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-470">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-470">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-471">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-471">Description</span></span>

<span data-ttu-id="7e9ce-472">Este servicio devuelve el identificador de la siguiente instancia de objeto del objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-472">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="7e9ce-473">Si el id. de instancia actual se establece en NX_LWM2M_RESERVED_ID (65535), se devuelve el identificador de la primera instancia.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-473">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-474">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-474">Parameters</span></span>

- <span data-ttu-id="7e9ce-475">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-475">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-476">**object_id**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-476">**object_id** The Object ID.</span></span>
- <span data-ttu-id="7e9ce-477">**instance_id_ptr**: puntero al id. de instancia de objeto actual.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-477">**instance_id_ptr** Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="7e9ce-478">En la devolución, contiene el id. de instancia siguiente del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-478">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-479">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-479">Return Values</span></span>

- <span data-ttu-id="7e9ce-480">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-480">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-481">**NX_CLIENT_LWM2M_NOT_FOUND**: el id. de instancia proporcionado es el último del objeto, o bien el id. de objeto no está implementado.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-481">**NX_CLIENT_LWM2M_NOT_FOUND** The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="7e9ce-482">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-482">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-483">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-483">Allowed From</span></span>

<span data-ttu-id="7e9ce-484">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-484">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-485">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-485">Example</span></span>

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a><span data-ttu-id="7e9ce-486">nx_lwm2m_client_object_instance_remove</span><span class="sxs-lookup"><span data-stu-id="7e9ce-486">nx_lwm2m_client_object_instance_remove</span></span>

<span data-ttu-id="7e9ce-487">Quita una implementación de instancia de objeto de un objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-487">Removes an  Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-488">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-489">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-489">Description</span></span>

<span data-ttu-id="7e9ce-490">Este servicio quita una instancia de objeto de un objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-490">This service removes an Object instance from an object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-491">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-491">Parameters</span></span>

- <span data-ttu-id="7e9ce-492">***object_ptr***: puntero a la estructura que define la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-492">***object_ptr*** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="7e9ce-493">**instance_ptr**: puntero a la estructura que define la implementación de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-493">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-494">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-494">Return Values</span></span>

- <span data-ttu-id="7e9ce-495">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-495">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-496">**NX_LWM2M_ALREADY_EXIST**: el id. de objeto ya existe.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="7e9ce-497">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-497">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-498">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-498">Allowed From</span></span>

<span data-ttu-id="7e9ce-499">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-499">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-500">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-500">Example</span></span>

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a><span data-ttu-id="7e9ce-501">nx_lwm2m_client_object_next_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-501">nx_lwm2m_client_object_next_get</span></span>

<span data-ttu-id="7e9ce-502">Obtiene el siguiente objeto del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-502">Gets the next object of the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-503">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-503">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-504">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-504">Description</span></span>

<span data-ttu-id="7e9ce-505">Este servicio devuelve el identificador del siguiente objeto implementado por el cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-505">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="7e9ce-506">Si el id. de objeto actual se establece en NX_LWM2M_RESERVED_ID (65535), se devuelve el primer id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-506">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-507">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-507">Parameters</span></span>

- <span data-ttu-id="7e9ce-508">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-508">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-509">**object_id_ptr**: puntero al id. de objeto actual.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-509">**object_id_ptr** Pointer to the current Object ID.</span></span> <span data-ttu-id="7e9ce-510">En la devolución, contiene el siguiente id. de objeto implementado por el cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-510">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-511">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-511">Return Values</span></span>

- <span data-ttu-id="7e9ce-512">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-512">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-513">**NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto especificado es el último de la base de datos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-513">**NX_LWM2M_CLIENT_NOT_FOUND** The given Object ID is the last of the database.</span></span>
<span data-ttu-id="7e9ce-514">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-514">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-515">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-515">Allowed From</span></span>

<span data-ttu-id="7e9ce-516">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-516">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-517">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-517">Example</span></span>

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="7e9ce-518">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="7e9ce-518">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="7e9ce-519">Lee los valores de los recursos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-519">Reads an Object Instance's resource's values.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-520">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-520">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="7e9ce-521">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-521">Description</span></span>

<span data-ttu-id="7e9ce-522">Este servicio realiza una operación de lectura en una instancia de objeto del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-522">This service performs a ‘Read’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-523">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-523">Parameters</span></span>

- <span data-ttu-id="7e9ce-524">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-524">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-525">**object_id**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-525">**object_id** The Object ID.</span></span>
- <span data-ttu-id="7e9ce-526">**instance_id**: identificador de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-526">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="7e9ce-527">**num_values**: número de recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-527">**num_values** The number of resources to read.</span></span>
- <span data-ttu-id="7e9ce-528">**values_ptr**: puntero a una matriz de NX_LWM2M_RESOURCE que contiene los identificadores de los recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-528">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="7e9ce-529">En la devolución, la matriz se rellena con los tipos y valores correspondientes.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-529">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-530">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-530">Return Values</span></span>

- <span data-ttu-id="7e9ce-531">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-531">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**: un recurso no admite la operación de lectura.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the read operation.</span></span>
- <span data-ttu-id="7e9ce-533">**NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto, el id. de instancia de objeto o un id. de recursos no existen.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-533">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="7e9ce-534">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-534">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-535">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-535">Allowed From</span></span>

<span data-ttu-id="7e9ce-536">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-536">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-537">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-537">Example</span></span>

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a><span data-ttu-id="7e9ce-538">nx_lwm2m_client_object_remove</span><span class="sxs-lookup"><span data-stu-id="7e9ce-538">nx_lwm2m_client_object_remove</span></span>

<span data-ttu-id="7e9ce-539">Quita una implementación de instancia de objeto de un objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-539">Removes an Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-540">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-540">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-541">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-541">Description</span></span>

<span data-ttu-id="7e9ce-542">Este servicio quita un objeto del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-542">This service removes an Object from the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-543">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-543">Parameters</span></span>

- <span data-ttu-id="7e9ce-544">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-544">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-545">**object_ptr**: puntero a la estructura que define la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-545">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-546">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-546">Return Values</span></span>

- <span data-ttu-id="7e9ce-547">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-547">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-548">**NX_LWM2M_ALREADY_EXIST**: el id. de objeto ya existe.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="7e9ce-549">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-549">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="7e9ce-550">**NX_LWM2M_CLIENT_FORBIDDEN**: se prohíbe eliminar un objeto interno.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-550">**NX_LWM2M_CLIENT_FORBIDDEN** Removing internal object is forbidden.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-551">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-551">Allowed From</span></span>

<span data-ttu-id="7e9ce-552">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-552">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-553">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-553">Example</span></span>

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a><span data-ttu-id="7e9ce-554">nx_lwm2m_client_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="7e9ce-554">nx_lwm2m_client_object_resource_changed</span></span>

<span data-ttu-id="7e9ce-555">Indica un cambio de un recurso de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-555">Signals a change of an Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-556">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="7e9ce-557">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-557">Description</span></span>

<span data-ttu-id="7e9ce-558">La aplicación usa el servicio para indicar al cliente LWM2M que un recurso del objeto ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-558">The service is used by the application to signal to the LWM2M Client that a resource of the Object has changed.</span></span> <span data-ttu-id="7e9ce-559">El cliente LWM2M enviará una notificación si un servidor LWM2M observa el recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-559">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-560">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-560">Parameters</span></span>

- <span data-ttu-id="7e9ce-561">**object_ptr**: puntero a la estructura que define la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-561">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="7e9ce-562">***instance_ptr***: puntero a la estructura que define la implementación de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-562">***instance_ptr*** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="7e9ce-563">**resource**: puntero a la estructura que describe el recurso que ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-563">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-564">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-564">Return Values</span></span>

- <span data-ttu-id="7e9ce-565">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-565">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-566">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-566">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-567">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-567">Allowed From</span></span>

<span data-ttu-id="7e9ce-568">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-568">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-569">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-569">Example</span></span>

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="7e9ce-570">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="7e9ce-570">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="7e9ce-571">Cambia los valores de los recursos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-571">Changes resource's values of an Object instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-572">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-572">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a><span data-ttu-id="7e9ce-573">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-573">Description</span></span>

<span data-ttu-id="7e9ce-574">Este servicio realiza una operación de escritura en una instancia de objeto del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-574">This service performs a ‘Write’ operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="7e9ce-575">Se pueden especificar las siguientes operaciones de escritura en el parámetro *write_op*.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-575">The following write operations can be specified to the *write_op* parameter.</span></span>

| <span data-ttu-id="7e9ce-576">Value</span><span class="sxs-lookup"><span data-stu-id="7e9ce-576">Value</span></span> | <span data-ttu-id="7e9ce-577">Operación&nbsp;de escritura</span><span class="sxs-lookup"><span data-stu-id="7e9ce-577">Write&nbsp;Operation</span></span> | <span data-ttu-id="7e9ce-578">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-578">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="7e9ce-579">0</span><span class="sxs-lookup"><span data-stu-id="7e9ce-579">0</span></span> | <span data-ttu-id="7e9ce-580">Actualización parcial</span><span class="sxs-lookup"><span data-stu-id="7e9ce-580">Partial Update</span></span> | <span data-ttu-id="7e9ce-581">Agrega o actualiza los recursos proporcionados en el nuevo valor y deja sin modificar otros recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-581">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span> |
| <span data-ttu-id="7e9ce-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="7e9ce-583">Reemplazo de instancia</span><span class="sxs-lookup"><span data-stu-id="7e9ce-583">Replace Instance</span></span> | <span data-ttu-id="7e9ce-584">Reemplaza la instancia de objeto por los nuevos valores de recursos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-584">Replaces the Object Instance with the new provided resource values.</span></span> |
| <span data-ttu-id="7e9ce-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> | <span data-ttu-id="7e9ce-586">Reemplazo de recurso</span><span class="sxs-lookup"><span data-stu-id="7e9ce-586">Replace Resource</span></span> | <span data-ttu-id="7e9ce-587">Reemplaza los recursos por los nuevos valores de recursos proporcionados (usados para reemplazar varios recursos).</span><span class="sxs-lookup"><span data-stu-id="7e9ce-587">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="7e9ce-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="7e9ce-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="7e9ce-589">Escritura de arranque</span><span class="sxs-lookup"><span data-stu-id="7e9ce-589">Bootstrap Write</span></span> | <span data-ttu-id="7e9ce-590">Indica una llamada desde una secuencia de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-590">Indicates a call from a Bootstrap sequence.</span></span> |

### <a name="parameters"></a><span data-ttu-id="7e9ce-591">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-591">Parameters</span></span>

- <span data-ttu-id="7e9ce-592">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-592">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7e9ce-593">**object_id**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-593">**object_id** The Object ID.</span></span>
- <span data-ttu-id="7e9ce-594">**instance_id**: identificador de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-594">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="7e9ce-595">**num_values**: número de recursos que se van a escribir.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-595">**num_values** The number of resources to write.</span></span>
- <span data-ttu-id="7e9ce-596">**values_ptr**: puntero a una matriz de NX_LWM2M_RESOURCE que contiene los identificadores de los recursos, los tipos y los valores que se van a escribir.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-596">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="7e9ce-597">**write_op**: tipo de operación de escritura.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-597">**write_op** The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-598">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-598">Return Values</span></span>

- <span data-ttu-id="7e9ce-599">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-599">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-600">**NX_LWM2M_CLIENT_BAD_ENCODING**: El tipo de un recurso no es válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-600">**NX_LWM2M_CLIENT_BAD_ENCODING** The type of a resource is not valid.</span></span>
- <span data-ttu-id="7e9ce-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**: la longitud de un valor es demasiado grande para almacenarse en la instancia.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="7e9ce-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**: un recurso no admite la operación de escritura.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the write operation.</span></span>
- <span data-ttu-id="7e9ce-603">**NX_LWM2M_CLIENT_NO_MEMORY**: no se puede asignar memoria para almacenar un valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-603">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="7e9ce-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE**: el valor de un recurso no es válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** The value of a resource is not valid.</span></span>
- <span data-ttu-id="7e9ce-605">**NX_LWM2M_CLIENT_NOT_FOUND**: el id. de objeto, el id. de instancia de objeto o un id. de recursos no existen.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-605">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="7e9ce-606">**NX_OPTION_ERROR**: tipo de operación de escritura no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-606">**NX_OPTION_ERROR** Invalid type of write operation.</span></span> 
- <span data-ttu-id="7e9ce-607">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-607">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-608">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-608">Allowed From</span></span>

<span data-ttu-id="7e9ce-609">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-609">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-610">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-610">Example</span></span>

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a><span data-ttu-id="7e9ce-611">nx_lwm2m_client_resource_boolean_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-611">nx_lwm2m_client_resource_boolean_get</span></span>

<span data-ttu-id="7e9ce-612">Obtiene el valor de un recurso boolean.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-612">Gets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-613">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-613">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-614">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-614">Description</span></span>

<span data-ttu-id="7e9ce-615">El servicio recupera el valor de un recurso boolean.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-615">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-616">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-616">Parameters</span></span>

- <span data-ttu-id="7e9ce-617">**resource**: puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-617">**resource** Pointer to Resource value description.</span></span>
- <span data-ttu-id="7e9ce-618">**bool_ptr**: puntero al valor booleano de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-618">**bool_ptr** Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-619">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-619">Return Values</span></span>

- <span data-ttu-id="7e9ce-620">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-620">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-621">**NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es booleano.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-621">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="7e9ce-622">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-622">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-623">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-623">Allowed From</span></span>

<span data-ttu-id="7e9ce-624">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-624">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-625">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-625">Example</span></span>

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a><span data-ttu-id="7e9ce-626">nx_lwm2m_client_resource_boolean_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-626">nx_lwm2m_client_resource_boolean_set</span></span>

<span data-ttu-id="7e9ce-627">Establece el valor de un recurso boolean.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-627">Sets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-628">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-628">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a><span data-ttu-id="7e9ce-629">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-629">Description</span></span>

<span data-ttu-id="7e9ce-630">El servicio establece el valor de un recurso boolean.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-630">The service sets the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-631">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-631">Parameters</span></span>

- <span data-ttu-id="7e9ce-632">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-632">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-633">**bool_data**: datos booleanos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-633">**bool_data** Boolean data.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-634">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-634">Return Values</span></span>

- <span data-ttu-id="7e9ce-635">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-635">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-636">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-636">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-637">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-637">Allowed From</span></span>

<span data-ttu-id="7e9ce-638">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-638">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-639">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-639">Example</span></span>

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a><span data-ttu-id="7e9ce-640">nx_lwm2m_client_resource_dim_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-640">nx_lwm2m_client_resource_dim_get</span></span>

<span data-ttu-id="7e9ce-641">Obtiene la dimensión de recurso para varios recursos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-641">Gets the resource dimension for multiple Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-642">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-642">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a><span data-ttu-id="7e9ce-643">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-643">Description</span></span>

<span data-ttu-id="7e9ce-644">El servicio recupera la dimensión de recurso para varios recursos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-644">The service retrieves the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-645">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-645">Parameters</span></span>

- <span data-ttu-id="7e9ce-646">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-646">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-647">**dim**: puntero a la dimensión de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-647">**dim** Pointer to the destination dimension.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-648">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-648">Return Values</span></span>

- <span data-ttu-id="7e9ce-649">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-649">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-650">**NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es booleano.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-650">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="7e9ce-651">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-651">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-652">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-652">Allowed From</span></span>

<span data-ttu-id="7e9ce-653">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-654">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-654">Example</span></span>

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a><span data-ttu-id="7e9ce-655">nx_lwm2m_client_resource_dim_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-655">nx_lwm2m_client_resource_dim_set</span></span>

<span data-ttu-id="7e9ce-656">Establece la dimensión de recurso para varios recursos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-656">Sets the resource dimension for multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-657">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-657">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a><span data-ttu-id="7e9ce-658">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-658">Description</span></span>

<span data-ttu-id="7e9ce-659">El servicio establece la dimensión de recurso para varios recursos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-659">The service sets the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-660">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-660">Parameters</span></span>

- <span data-ttu-id="7e9ce-661">**value**: puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-661">**value** Pointer to Resource value description.</span></span>
- <span data-ttu-id="7e9ce-662">**dim**: valor de dimensión.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-662">**dim** Dimension value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-663">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-663">Return Values</span></span>

- <span data-ttu-id="7e9ce-664">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-664">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-665">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-665">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-666">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-666">Allowed From</span></span>

<span data-ttu-id="7e9ce-667">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-667">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-668">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-668">Example</span></span>

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a><span data-ttu-id="7e9ce-669">nx_lwm2m_client_resource_float32_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-669">nx_lwm2m_client_resource_float32_get</span></span>

<span data-ttu-id="7e9ce-670">Establece el valor de un recurso **float** de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-670">Gets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-671">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-671">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-672">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-672">Description</span></span>

<span data-ttu-id="7e9ce-673">El servicio recupera el valor de un recurso **float** de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-673">The service retrieves the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-674">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-674">Parameters</span></span>

- <span data-ttu-id="7e9ce-675">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-675">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-676">**float32_ptr**: puntero al valor **float** de 32 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-676">**float32_ptr** Pointer to the destination 32-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-677">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-677">Return Values</span></span>

- <span data-ttu-id="7e9ce-678">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-678">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-679">**NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es booleano.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-679">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="7e9ce-680">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-680">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-681">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-681">Allowed From</span></span>

<span data-ttu-id="7e9ce-682">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-682">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-683">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-683">Example</span></span>

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a><span data-ttu-id="7e9ce-684">nx_lwm2m_client_resource_float32_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-684">nx_lwm2m_client_resource_float32_set</span></span>

<span data-ttu-id="7e9ce-685">Establece el valor de un recurso **float** de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-685">Sets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-686">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-686">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a><span data-ttu-id="7e9ce-687">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-687">Description</span></span>

<span data-ttu-id="7e9ce-688">El servicio establece el valor de un recurso **float** de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-688">The service sets the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-689">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-689">Parameters</span></span>

- <span data-ttu-id="7e9ce-690">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-690">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-691">**float32_data**: datos de valor **float** de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-691">**float32_data** 32-Bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-692">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-692">Return Values</span></span>

- <span data-ttu-id="7e9ce-693">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-693">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-694">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-694">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-695">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-695">Allowed From</span></span>

<span data-ttu-id="7e9ce-696">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-696">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-697">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-697">Example</span></span>

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a><span data-ttu-id="7e9ce-698">nx_lwm2m_client_resource_float64_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-698">nx_lwm2m_client_resource_float64_get</span></span>

<span data-ttu-id="7e9ce-699">Obtiene el valor de un recurso float de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-699">Gets the value of a 64-Bit float Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-700">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-700">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-701">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-701">Description</span></span>

<span data-ttu-id="7e9ce-702">El servicio recupera el valor de un recurso **float** de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-702">The service retrieves the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-703">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-703">Parameters</span></span>

- <span data-ttu-id="7e9ce-704">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-704">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-705">**float64_ptr**: puntero al valor **float** de 64 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-705">**float64_ptr** Pointer to the destination 64-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-706">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-706">Return Values</span></span>

- <span data-ttu-id="7e9ce-707">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-707">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-708">**NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es flotante.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-708">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a float value.</span></span>
- <span data-ttu-id="7e9ce-709">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-709">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-710">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-710">Allowed From</span></span>

<span data-ttu-id="7e9ce-711">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-711">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-712">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-712">Example</span></span>

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a><span data-ttu-id="7e9ce-713">nx_lwm2m_client_resource_float64_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-713">nx_lwm2m_client_resource_float64_set</span></span>

<span data-ttu-id="7e9ce-714">Establece el valor de un recurso **float** de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-714">Sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-715">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-715">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="7e9ce-716">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-716">Description</span></span>

<span data-ttu-id="7e9ce-717">El servicio establece el valor de un recurso **float** de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-717">The service sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-718">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-718">Parameters</span></span>

- <span data-ttu-id="7e9ce-719">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-719">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-720">**float64_data**: datos de valor **float** de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-720">**float64_data** 64-bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-721">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-721">Return Values</span></span>

- <span data-ttu-id="7e9ce-722">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-722">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-723">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-723">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-724">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-724">Allowed From</span></span>

<span data-ttu-id="7e9ce-725">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-725">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-726">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-726">Example</span></span>

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a><span data-ttu-id="7e9ce-727">nx_lwm2m_client_resource_info_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-727">nx_lwm2m_client_resource_info_get</span></span>

<span data-ttu-id="7e9ce-728">Obtiene la información del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-728">Gets the resource info.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-729">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-729">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a><span data-ttu-id="7e9ce-730">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-730">Description</span></span>

<span data-ttu-id="7e9ce-731">El servicio recupera la información del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-731">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-732">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-732">Parameters</span></span>

- <span data-ttu-id="7e9ce-733">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-733">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-734">**resource_id**: puntero al identificador del recurso de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-734">**resource_id** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="7e9ce-735">**operation**: puntero a la operación de recurso de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-735">**operation** Pointer to the destination resource operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-736">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-736">Return Values</span></span>

- <span data-ttu-id="7e9ce-737">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-737">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-738">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-738">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-739">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-739">Allowed From</span></span>

<span data-ttu-id="7e9ce-740">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-740">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-741">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-741">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a><span data-ttu-id="7e9ce-742">nx_lwm2m_client_resource_info_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-742">nx_lwm2m_client_resource_info_set</span></span>

<span data-ttu-id="7e9ce-743">Establece la información del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-743">Sets the resource information.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-744">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-744">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="7e9ce-745">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-745">Description</span></span>

<span data-ttu-id="7e9ce-746">El servicio establece la información del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-746">The service sets the resource information.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-747">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-747">Parameters</span></span>

- <span data-ttu-id="7e9ce-748">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-748">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-749">**resource_id**: identificador del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-749">**resource_id** ID of the resource.</span></span>
- <span data-ttu-id="7e9ce-750">**operation**: operación del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-750">**operation** Operation of the resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-751">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-751">Return Values</span></span>

- <span data-ttu-id="7e9ce-752">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-752">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-753">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-753">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-754">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-754">Allowed From</span></span>

<span data-ttu-id="7e9ce-755">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-755">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-756">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-756">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a><span data-ttu-id="7e9ce-757">nx_lwm2m_client_resource_instances_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-757">nx_lwm2m_client_resource_instances_get</span></span>

<span data-ttu-id="7e9ce-758">Obtiene la instancia de varios recursos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-758">Gets the instance of multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-759">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-759">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a><span data-ttu-id="7e9ce-760">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-760">Description</span></span>

<span data-ttu-id="7e9ce-761">El servicio recupera la información del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-761">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-762">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-762">Parameters</span></span>

- <span data-ttu-id="7e9ce-763">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-763">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-764">**resource_instances**: puntero al identificador del recurso de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-764">**resource_instances** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="7e9ce-765">**count**: puntero al recuento.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-765">**count** Pointer to the count.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-766">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-766">Return Values</span></span>

- <span data-ttu-id="7e9ce-767">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-767">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-768">**NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es booleano.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-768">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="7e9ce-769">**NX_LWM2M_CLIENT_NO_MEMORY**: sin memoria para rellenar las instancias.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-769">**NX_LWM2M_CLIENT_NO_MEMORY** No memory to fill out instances.</span></span>
- <span data-ttu-id="7e9ce-770">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-770">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-771">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-771">Allowed From</span></span>

<span data-ttu-id="7e9ce-772">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-772">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-773">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-773">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a><span data-ttu-id="7e9ce-774">nx_lwm2m_client_resource_instances_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-774">nx_lwm2m_client_resource_instances_set</span></span>

<span data-ttu-id="7e9ce-775">Establece las instancias del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-775">Sets the resource instances.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-776">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-776">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a><span data-ttu-id="7e9ce-777">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-777">Description</span></span>

<span data-ttu-id="7e9ce-778">El servicio establece las instancias de recurso para varios recursos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-778">The service sets the resource instances for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-779">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-779">Parameters</span></span>

- <span data-ttu-id="7e9ce-780">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-780">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-781">**resource_instance**: puntero a las instancias de recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-781">**resource_instance** Pointer to resource instances.</span></span>
- <span data-ttu-id="7e9ce-782">**count**: recuento de instancias de recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-782">**count** Count of resource instances.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-783">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-783">Return Values</span></span>

- <span data-ttu-id="7e9ce-784">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-784">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-785">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-785">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-786">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-786">Allowed From</span></span>

<span data-ttu-id="7e9ce-787">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-787">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-788">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-788">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a><span data-ttu-id="7e9ce-789">nx_lwm2m_client_resource_integer32_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-789">nx_lwm2m_client_resource_integer32_get</span></span>

<span data-ttu-id="7e9ce-790">Obtiene el valor de un recurso integer de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-790">Gets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-791">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-791">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-792">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-792">Description</span></span>

<span data-ttu-id="7e9ce-793">El servicio recupera el valor de un recurso integer de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-793">The service retrieves the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-794">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-794">Parameters</span></span>

- <span data-ttu-id="7e9ce-795">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-795">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-796">**integer32_ptr**: puntero al valor entero de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-796">**integer32_ptr** Pointer to the 32-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-797">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-797">Return Values</span></span>

- <span data-ttu-id="7e9ce-798">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-798">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-799">**NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es entero.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-799">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not integer value.</span></span>
- <span data-ttu-id="7e9ce-800">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-800">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-801">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-801">Allowed From</span></span>

<span data-ttu-id="7e9ce-802">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-802">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-803">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-803">Example</span></span>

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a><span data-ttu-id="7e9ce-804">nx_lwm2m_client_resource_integer32_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-804">nx_lwm2m_client_resource_integer32_set</span></span>

<span data-ttu-id="7e9ce-805">Establece el valor de un recurso integer de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-805">Sets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-806">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-806">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a><span data-ttu-id="7e9ce-807">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-807">Description</span></span>

<span data-ttu-id="7e9ce-808">El servicio establece el valor de un recurso integer de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-808">The service sets the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-809">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-809">Parameters</span></span>

- <span data-ttu-id="7e9ce-810">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-810">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-811">**integer32_data**: datos de entero de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-811">**integer32_data** 32-Bit integer data.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-812">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-812">Return Values</span></span>

- <span data-ttu-id="7e9ce-813">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-813">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-814">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-814">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-815">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-815">Allowed From</span></span>

<span data-ttu-id="7e9ce-816">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-816">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-817">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-817">Example</span></span>

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a><span data-ttu-id="7e9ce-818">nx_lwm2m_client_resource_integer64_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-818">nx_lwm2m_client_resource_integer64_get</span></span>

<span data-ttu-id="7e9ce-819">Obtiene el valor de un recurso integer de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-819">Gets the value of a 64-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-820">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-820">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-821">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-821">Description</span></span>

<span data-ttu-id="7e9ce-822">El servicio recupera el valor de un recurso integer de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-822">The service retrieves the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-823">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-823">Parameters</span></span>

- <span data-ttu-id="7e9ce-824">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-824">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-825">**integer64_ptr**: puntero al valor entero de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-825">**integer64_ptr** Pointer to the 64-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-826">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-826">Return Values</span></span>

- <span data-ttu-id="7e9ce-827">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-827">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-828">**NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es un entero de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-828">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not 64-Bit integer value.</span></span>
- <span data-ttu-id="7e9ce-829">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-829">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-830">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-830">Allowed From</span></span>

<span data-ttu-id="7e9ce-831">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-831">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-832">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-832">Example</span></span>

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a><span data-ttu-id="7e9ce-833">nx_lwm2m_client_resource_integer64_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-833">nx_lwm2m_client_resource_integer64_set</span></span>

## <a name="set-the-value-of-a-64-bit-integer-resource"></a><span data-ttu-id="7e9ce-834">Establece el valor de un recurso integer de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-834">Set the value of a 64-Bit integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-835">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-835">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a><span data-ttu-id="7e9ce-836">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-836">Description</span></span>

<span data-ttu-id="7e9ce-837">El servicio establece el valor de un recurso integer de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-837">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-838">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-838">Parameters</span></span>

- <span data-ttu-id="7e9ce-839">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-839">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-840">**integer64_data**: entero 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-840">**integer64_data** 64-bit integer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-841">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-841">Return Values</span></span>

- <span data-ttu-id="7e9ce-842">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-842">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-843">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-843">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-844">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-844">Allowed From</span></span>

<span data-ttu-id="7e9ce-845">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-845">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-846">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-846">Example</span></span>

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a><span data-ttu-id="7e9ce-847">nx_lwm2m_client_resource_objlnk_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-847">nx_lwm2m_client_resource_objlnk_get</span></span>

<span data-ttu-id="7e9ce-848">Obtiene el valor de un recurso de vínculo de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-848">Gets the value of an object link resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-849">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-849">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a><span data-ttu-id="7e9ce-850">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-850">Description</span></span>

<span data-ttu-id="7e9ce-851">El servicio recupera el valor de un vínculo de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-851">The service retrieves the value of object link.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-852">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-852">Parameters</span></span>

- <span data-ttu-id="7e9ce-853">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-853">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-854">**object_id**: puntero al id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-854">**object_id** Pointer to the object ID.</span></span>
- <span data-ttu-id="7e9ce-855">**instance_id**: puntero al id. de instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-855">**instance_id** Pointer to the object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-856">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-856">Return Values</span></span>

- <span data-ttu-id="7e9ce-857">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-857">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-858">**NX_LWM2M_CLIENT_BAD_ENCODING**: El valor del recurso no es un valor de vínculo de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-858">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an object link value.</span></span>
- <span data-ttu-id="7e9ce-859">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-859">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-860">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-860">Allowed From</span></span>

<span data-ttu-id="7e9ce-861">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-861">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-862">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-862">Example</span></span>

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a><span data-ttu-id="7e9ce-863">nx_lwm2m_client_resource_objlnk_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-863">nx_lwm2m_client_resource_objlnk_set</span></span>

<span data-ttu-id="7e9ce-864">Establece las instancias del recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-864">Sets the resource instances</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-865">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-865">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="7e9ce-866">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-866">Description</span></span>

<span data-ttu-id="7e9ce-867">El servicio establece el valor del recurso de vínculo de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-867">The service sets the value of the object link resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-868">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-868">Parameters</span></span>

- <span data-ttu-id="7e9ce-869">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-869">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-870">**object_id**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-870">**object_id** Object ID.</span></span>
- <span data-ttu-id="7e9ce-871">**instance_id**: identificador de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-871">**instance_id** Object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-872">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-872">Return Values</span></span>

- <span data-ttu-id="7e9ce-873">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-873">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-874">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-874">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-875">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-875">Allowed From</span></span>

<span data-ttu-id="7e9ce-876">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-876">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-877">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-877">Example</span></span>

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a><span data-ttu-id="7e9ce-878">nx_lwm2m_client_resource_opaque_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-878">nx_lwm2m_client_resource_opaque_get</span></span>

<span data-ttu-id="7e9ce-879">Obtiene el valor de un recurso opaque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-879">Gets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-880">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-880">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a><span data-ttu-id="7e9ce-881">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-881">Description</span></span>

<span data-ttu-id="7e9ce-882">El servicio recupera el valor de un recurso opaque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-882">The service retrieves the value of an opaque Resource.</span></span> <span data-ttu-id="7e9ce-883">Un valor de recurso opaque está formado por un puntero a un búfer y una longitud.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-883">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-884">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-884">Parameters</span></span>

- <span data-ttu-id="7e9ce-885">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-885">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-886">**opaque_ptr**: puntero a los datos opacos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-886">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="7e9ce-887">**opaque_length**: puntero a la longitud de los datos opacos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-887">**opaque_length** Pointer to the opaque data length.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-888">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-888">Return Values</span></span>

- <span data-ttu-id="7e9ce-889">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-889">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-890">**NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es un recurso opaque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-890">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an opaque resource.</span></span>
- <span data-ttu-id="7e9ce-891">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-891">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-892">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-892">Allowed From</span></span>

<span data-ttu-id="7e9ce-893">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-893">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-894">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-894">Example</span></span>

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a><span data-ttu-id="7e9ce-895">nx_lwm2m_client_resource_opaque_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-895">nx_lwm2m_client_resource_opaque_set</span></span>

<span data-ttu-id="7e9ce-896">Establece el valor de un recurso opaque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-896">Sets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-897">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-897">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a><span data-ttu-id="7e9ce-898">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-898">Description</span></span>

<span data-ttu-id="7e9ce-899">El servicio establece el valor de un recurso opaque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-899">The service sets the value of an opaque Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-900">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-900">Parameters</span></span>

- <span data-ttu-id="7e9ce-901">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-901">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-902">**opaque_ptr**: puntero a los datos opacos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-902">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="7e9ce-903">**opaque_length**: longitud de los datos opacos.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-903">**opaque_length** Length of the opaque data.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-904">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-904">Return Values</span></span>

- <span data-ttu-id="7e9ce-905">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-905">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-906">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-906">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-907">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-907">Allowed From</span></span>

<span data-ttu-id="7e9ce-908">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-908">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-909">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-909">Example</span></span>

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a><span data-ttu-id="7e9ce-910">nx_lwm2m_client_resource_string_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-910">nx_lwm2m_client_resource_string_get</span></span>

<span data-ttu-id="7e9ce-911">Obtiene el valor de un recurso string.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-911">Gets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-912">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-912">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a><span data-ttu-id="7e9ce-913">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-913">Description</span></span>

<span data-ttu-id="7e9ce-914">El servicio recupera el valor de un recurso string.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-914">The service retrieves the value of a string Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-915">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-915">Parameters</span></span>

- <span data-ttu-id="7e9ce-916">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-916">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-917">**string_ptr**: puntero al puntero de la cadena de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-917">**string_ptr** Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="7e9ce-918">**string_length**: puntero a la longitud de la cadena de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-918">**string_length** Pointer to the destination string length.</span></span> <span data-ttu-id="7e9ce-919">Puede ser **NULL** si la cadena termina en NULL.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-919">Can be **NULL** if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-920">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-920">Return Values</span></span>

- <span data-ttu-id="7e9ce-921">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-921">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-922">**NX_LWM2M_CLIENT_BAD_ENCODING**: el valor del recurso no es de cadena.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-922">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a string value.</span></span>
- <span data-ttu-id="7e9ce-923">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-923">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-924">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-924">Allowed From</span></span>

<span data-ttu-id="7e9ce-925">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-925">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-926">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-926">Example</span></span>

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a><span data-ttu-id="7e9ce-927">nx_lwm2m_client_resource_string_set</span><span class="sxs-lookup"><span data-stu-id="7e9ce-927">nx_lwm2m_client_resource_string_set</span></span>

<span data-ttu-id="7e9ce-928">Establece el valor de un recurso string.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-928">Sets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-929">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-929">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a><span data-ttu-id="7e9ce-930">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-930">Description</span></span>

<span data-ttu-id="7e9ce-931">El servicio establece el valor de un recurso integer de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-931">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-932">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-932">Parameters</span></span>

- <span data-ttu-id="7e9ce-933">**resource**: puntero al recurso.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-933">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="7e9ce-934">**string_ptr**: puntero a la cadena.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-934">**string_ptr** Pointer to the string.</span></span>
- <span data-ttu-id="7e9ce-935">**string_length**: longitud de la cadena.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-935">**string_length** Length of the string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-936">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-936">Return Values</span></span>

- <span data-ttu-id="7e9ce-937">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-937">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-938">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-938">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-939">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-939">Allowed From</span></span>

<span data-ttu-id="7e9ce-940">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-940">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-941">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-941">Example</span></span>

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="7e9ce-942">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="7e9ce-942">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="7e9ce-943">Inicia una sesión con un servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-943">Starts a session with a Bootstrap Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-944">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-944">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a><span data-ttu-id="7e9ce-945">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-945">Description</span></span>

<span data-ttu-id="7e9ce-946">Este servicio inicia una sesión con un servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-946">This service starts a session with a Bootstrap Server.</span></span> <span data-ttu-id="7e9ce-947">El servidor debe tener una instancia de seguridad correspondiente en el objeto de seguridad.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-947">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="7e9ce-948">Si el recurso "Hold Off" es distinto de cero en la instancia de seguridad asociada a este servidor, la sesión esperará a un arranque iniciado por el servidor; si el servidor no inicia ningún arranque después de este período de tiempo, se llevará a cabo un arranque iniciado por el cliente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-948">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, If no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="7e9ce-949">Esta llamada anula cualquier sesión activa actual, que se reemplaza por la nueva sesión del servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-949">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-950">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-950">Parameters</span></span>

- <span data-ttu-id="7e9ce-951">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-951">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7e9ce-952">**security_id**: id. de instancia de seguridad del servidor de arranque; debe establecerse en NX_LWM2M_RESERVED_ID (65535) si el servidor de arranque no tiene definida ninguna instancia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-952">**security_id** The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="7e9ce-953">**ip_address**: dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-953">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="7e9ce-954">**port**: puerto UDP del servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-954">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-955">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-955">Return Values</span></span>

- <span data-ttu-id="7e9ce-956">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-956">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-957">**NX_LWM2M_CLIENT_ERROR**: error de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-957">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="7e9ce-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="7e9ce-959">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-959">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-960">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-960">Allowed From</span></span>

<span data-ttu-id="7e9ce-961">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-961">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-962">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-962">Example</span></span>

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="7e9ce-963">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="7e9ce-963">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="7e9ce-964">Inicia una sesión segura con un servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-964">Starts a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-965">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-965">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-966">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-966">Description</span></span>

<span data-ttu-id="7e9ce-967">Este servicio inicia una sesión con un servidor de arranque mediante una conexión DTLS segura.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-967">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="7e9ce-968">El servidor debe tener una instancia de seguridad correspondiente en el objeto de seguridad.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-968">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="7e9ce-969">La sesión DTLS se debe haber configurado con los conjuntos de cifrado y el material de clave adecuados antes de llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-969">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="7e9ce-970">**NX_SECURE_ENABLE_DTLS** debe definirse.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-970">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="7e9ce-971">Si el recurso "Hold Off" es distinto de cero en la instancia de seguridad asociada a este servidor, la sesión esperará a un arranque iniciado por el servidor; si el servidor no inicia ningún arranque después de este período de tiempo, se llevará a cabo un arranque iniciado por el cliente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-971">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span> 

<span data-ttu-id="7e9ce-972">Esta llamada anula cualquier sesión activa actual, que se reemplaza por la nueva sesión del servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-972">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-973">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-973">Parameters</span></span>

- <span data-ttu-id="7e9ce-974">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-974">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7e9ce-975">**security_id**: id. de instancia de seguridad del servidor de arranque; debe establecerse en **NX_LWM2M_RESERVED_ID** (65535) si el servidor de arranque no tiene definida ninguna instancia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-975">**security_id** The Security Instance ID of the Bootstrap Server, must be set to **NX_LWM2M_RESERVED_ID** (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="7e9ce-976">**ip_address**: dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-976">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="7e9ce-977">**port**: puerto UDP del servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-977">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="7e9ce-978">**dtls_session_ptr**: sesión DTLS que se va a usar para la sesión de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-978">**dtls_session_ptr** The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="7e9ce-979">**dtls_local_port**: puerto UDP local usado para la sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-979">**dtls_local_port** The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-980">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-980">Return Values</span></span>

- <span data-ttu-id="7e9ce-981">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-981">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-982">**NX_LWM2M_CLIENT_ERROR**: error de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-982">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="7e9ce-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="7e9ce-984">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-984">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-985">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-985">Allowed From</span></span>

<span data-ttu-id="7e9ce-986">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-986">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-987">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-987">Example</span></span>

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="7e9ce-988">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="7e9ce-988">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="7e9ce-989">Crea una sesión de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-989">Creates a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-990">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-990">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="7e9ce-991">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-991">Description</span></span>

<span data-ttu-id="7e9ce-992">Este servicio crea una nueva sesión de cliente LWM2M asociada a un cliente LWM2M existente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-992">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="7e9ce-993">El cliente LWM2M usa la sesión para comunicarse con un servidor de arranque o un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-993">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span> 

<span data-ttu-id="7e9ce-994">La aplicación debe proporcionar una función de devolución de llamada a la que se llamará cuando se actualice el estado de la sesión.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-994">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-995">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-995">Parameters</span></span>

- <span data-ttu-id="7e9ce-996">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-996">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7e9ce-997">**client_ptr**: puntero al cliente LWM2M creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-997">**client_ptr** Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="7e9ce-998">**state_callback**: devolución de llamada de la aplicación a la que se llama cuando el estado de la sesión ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-998">**state_callback** Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-999">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-999">Return Values</span></span>

- <span data-ttu-id="7e9ce-1000">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1000">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-1001">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1001">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-1002">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1002">Allowed From</span></span>

<span data-ttu-id="7e9ce-1003">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1003">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-1004">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1004">Example</span></span>

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="7e9ce-1005">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1005">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="7e9ce-1006">Elimina una sesión de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1006">Deletes a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-1007">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1007">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-1008">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1008">Description</span></span>

<span data-ttu-id="7e9ce-1009">Este servicio elimina una sesión de cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1009">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="7e9ce-1010">Cuando se elimina un cliente LWM2M mediante una llamada a nx_lwm2m_client_delete también se eliminan todas las sesiones asociadas al cliente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1010">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-1011">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1011">Parameters</span></span>

- <span data-ttu-id="7e9ce-1012">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1012">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-1013">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1013">Return Values</span></span>

- <span data-ttu-id="7e9ce-1014">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1014">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-1015">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1015">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-1016">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1016">Allowed From</span></span>

<span data-ttu-id="7e9ce-1017">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1017">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-1018">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1018">Example</span></span>

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="7e9ce-1019">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1019">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="7e9ce-1020">Finaliza una sesión con un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1020">Terminates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-1021">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1021">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-1022">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1022">Description</span></span>

<span data-ttu-id="7e9ce-1023">Este servicio realiza una operación de anulación de registro en un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1023">This service performs a ‘De-Register’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-1024">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1024">Parameters</span></span>

- <span data-ttu-id="7e9ce-1025">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1025">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-1026">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1026">Return Values</span></span>

- <span data-ttu-id="7e9ce-1027">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1027">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED**: el cliente no está registrado en el servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="7e9ce-1029">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1029">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-1030">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1030">Allowed From</span></span>

<span data-ttu-id="7e9ce-1031">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1031">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-1032">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1032">Example</span></span>

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="7e9ce-1033">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1033">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="7e9ce-1034">Obtiene el último error de una sesión.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1034">Gets the last error of a session.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-1035">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1035">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-1036">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1036">Description</span></span>

<span data-ttu-id="7e9ce-1037">Este servicio devuelve el código de error de la sesión cuando la sesión se encuentra en estado de error.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1037">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-1038">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1038">Parameters</span></span>

- <span data-ttu-id="7e9ce-1039">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1039">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-1040">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1040">Return Values</span></span>

- <span data-ttu-id="7e9ce-1041">**NX_SUCCESS**: la sesión no está en estado de error.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1041">**NX_SUCCESS** The session is not in error state.</span></span>
- <span data-ttu-id="7e9ce-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR**: dirección del servidor no válida.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Invalid server address.</span></span>
- <span data-ttu-id="7e9ce-1043">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**: la carga de la solicitud no cabe en el búfer de red.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Payload of request doesn’t fit in network buffer.</span></span>
- <span data-ttu-id="7e9ce-1044">**NX_LWM2M_CLIENT_DTLS_ERROR**: no se pudo establecer una conexión segura con el servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="7e9ce-1045">**NX_LWM2M_CLIENT_ERROR**: error no especificado.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1045">**NX_LWM2M_ CLIENT_ERROR** Unspecified error.</span></span>
- <span data-ttu-id="7e9ce-1046">**NX_LWM2M_CLIENT_FORBIDDEN**: el servidor rechazó el registro.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Registration refused by server.</span></span>
- <span data-ttu-id="7e9ce-1047">**NX_LWM2M_CLIENT_NOT_FOUND**: el servidor no encontró el cliente al actualizar o eliminar el registro.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="7e9ce-1048">**NX_LWM2M_CLIENT_SERVER_INSTANCE_DELETED**: se eliminó la instancia de objeto de servidor correspondiente a la sesión.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="7e9ce-1049">**NX_LWM2M_CLIENT_TIMED_OUT**: el servidor no devolvió ninguna respuesta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** No answer from server.</span></span>
- <span data-ttu-id="7e9ce-1050">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1050">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-1051">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1051">Allowed From</span></span>

<span data-ttu-id="7e9ce-1052">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1052">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-1053">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1053">Example</span></span>

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="7e9ce-1054">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1054">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="7e9ce-1055">Inicia una sesión con un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1055">Starts a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-1056">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1056">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a><span data-ttu-id="7e9ce-1057">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1057">Description</span></span>

<span data-ttu-id="7e9ce-1058">Este servicio realiza una operación de registro en un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1058">This service performs a ‘Register’ operation to a LWM2M Server.</span></span> <span data-ttu-id="7e9ce-1059">El servidor debe tener una instancia de servidor correspondiente en el objeto de servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1059">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="7e9ce-1060">Si el registro se realiza correctamente, el cliente LWM2M procesará más operaciones desde el servidor y enviará periódicamente mensajes de actualización hasta que se elimine el registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1060">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="7e9ce-1061">Esta llamada anula cualquier sesión activa actual, que se reemplaza por la nueva sesión del servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1061">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-1062">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1062">Parameters</span></span>

- <span data-ttu-id="7e9ce-1063">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1063">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7e9ce-1064">**server_id**: id. de servidor corto del servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1064">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="7e9ce-1065">**ip_address**: dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1065">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="7e9ce-1066">**port**: puerto UDP del servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1066">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-1067">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1067">Return Values</span></span>

- <span data-ttu-id="7e9ce-1068">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1068">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-1069">**NX_LWM2M_CLIENT_ERROR**: error de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1069">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="7e9ce-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="7e9ce-1071">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1071">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-1072">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1072">Allowed From</span></span>

<span data-ttu-id="7e9ce-1073">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1073">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-1074">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1074">Example</span></span>

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="7e9ce-1075">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1075">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="7e9ce-1076">Inicia una sesión segura con un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1076">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-1077">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1077">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-1078">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1078">Description</span></span>

<span data-ttu-id="7e9ce-1079">Este servicio realiza una operación de registro en un servidor LWM2M mediante una conexión DTLS segura.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1079">This service performs a ‘Register’ operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="7e9ce-1080">El servidor debe tener una instancia de servidor correspondiente en el objeto de servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1080">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="7e9ce-1081">La sesión DTLS se debe haber configurado con los conjuntos de cifrado y el material de clave adecuados antes de llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1081">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="7e9ce-1082">**NX_SECURE_ENABLE_DTLS** debe definirse.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1082">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="7e9ce-1083">Si el registro se realiza correctamente, el cliente LWM2M procesará más operaciones desde el servidor y enviará periódicamente mensajes de actualización hasta que se elimine el registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1083">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="7e9ce-1084">Esta llamada anula cualquier sesión activa actual, que se reemplaza por la nueva sesión del servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1084">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-1085">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1085">Parameters</span></span>

- <span data-ttu-id="7e9ce-1086">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1086">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7e9ce-1087">**server_id**: id. de servidor corto del servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1087">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="7e9ce-1088">**ip_address**: dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1088">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="7e9ce-1089">**port**: puerto UDP del servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1089">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="7e9ce-1090">**dtls_session_ptr**: sesión DTLS que se va a usar para la sesión de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1090">**dtls_session_ptr** The DTLS session to use for the LWM2M session.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-1091">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1091">Return Values</span></span>

- <span data-ttu-id="7e9ce-1092">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1092">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-1093">**NX_LWM2M_CLIENT_ERROR**: error de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1093">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="7e9ce-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE**: el puerto no está disponible.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="7e9ce-1095">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1095">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-1096">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1096">Allowed From</span></span>

<span data-ttu-id="7e9ce-1097">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1097">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-1098">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1098">Example</span></span>

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a><span data-ttu-id="7e9ce-1099">nx_lwm2m_client_session_register_info_get</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1099">nx_lwm2m_client_session_register_info_get</span></span>

<span data-ttu-id="7e9ce-1100">Inicia una sesión segura con un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1100">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-1101">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1101">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a><span data-ttu-id="7e9ce-1102">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1102">Description</span></span>

<span data-ttu-id="7e9ce-1103">Una vez establecida una sesión de comunicación con un servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1103">Once a communication session with a Bootstrap server was established.</span></span> <span data-ttu-id="7e9ce-1104">La aplicación puede llamar a esta API para obtener el servidor y la información de seguridad para el siguiente paso de registro.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1104">Application can call this api to get the server and security information for the next registration step.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-1105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1105">Parameters</span></span>

- <span data-ttu-id="7e9ce-1106">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1106">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7e9ce-1107">**security_instance_id**: identificador de la instancia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1107">**security_instance_id** Security instance ID.</span></span>
- <span data-ttu-id="7e9ce-1108">**server_id**: puntero al identificador del servidor de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1108">**server_id** Pointer to destination server ID.</span></span>
- <span data-ttu-id="7e9ce-1109">**server_uri**: puntero al URI del servidor de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1109">**server_uri** Pointer to destination server uri.</span></span>
- <span data-ttu-id="7e9ce-1110">**server_uri_len**: puntero a la longitud del URI del servidor de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1110">**server_uri_len** Pointer to destination server uri length.</span></span>
- <span data-ttu-id="7e9ce-1111">**security_mode**: puntero al modo de seguridad de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1111">**security_mode** Pointer to destination security mode.</span></span>
- <span data-ttu-id="7e9ce-1112">**pub_key_or_id**: puntero a la identidad o la clave pública de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1112">**pub_key_or_id** Pointer to destination public key or identity.</span></span>
- <span data-ttu-id="7e9ce-1113">**pub_key_or_id_len**: puntero a la longitud de la identidad o la clave pública de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1113">**pub_key_or_id_len** Pointer to destination public key or identity length.</span></span>
- <span data-ttu-id="7e9ce-1114">**server_pub_key**: puntero a la clave pública del servidor de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1114">**server_pub_key** Pointer to destination server public key.</span></span>
- <span data-ttu-id="7e9ce-1115">**server_pub_key_len**: puntero a la longitud de la clave pública del servidor de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1115">**server_pub_key_len** Pointer to destination server public key length.</span></span>
- <span data-ttu-id="7e9ce-1116">**secret_key**: puntero a la clave secreta de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1116">**secret_key** Pointer to destination secret key.</span></span>
- <span data-ttu-id="7e9ce-1117">**secret_key_len**: puntero a la longitud de la clave secreta de destino.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1117">**secret_key_len** Pointer to destination secret key length.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-1118">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1118">Return Values</span></span>

- <span data-ttu-id="7e9ce-1119">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1119">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-1120">**NX_LWM2M_CLIENT_NOT_FOUND**: no hay ninguna instancia de objeto de seguridad.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1120">**NX_LWM2M_CLIENT_NOT_FOUND** There is no security Object instance.</span></span>
- <span data-ttu-id="7e9ce-1121">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1121">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-1122">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1122">Allowed From</span></span>

<span data-ttu-id="7e9ce-1123">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1123">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-1124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1124">Example</span></span>

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="7e9ce-1125">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1125">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="7e9ce-1126">Actualiza una sesión con un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1126">Updates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-1127">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1127">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-1128">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1128">Description</span></span>

<span data-ttu-id="7e9ce-1129">Este servicio realiza una operación de actualización en un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1129">This service performs an ‘Update’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-1130">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1130">Parameters</span></span>

- <span data-ttu-id="7e9ce-1131">**session_ptr**: puntero al bloque de control de sesión del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1131">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-1132">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1132">Return Values</span></span>

- <span data-ttu-id="7e9ce-1133">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1133">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED**: el cliente no está registrado en el servidor.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="7e9ce-1135">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1135">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-1136">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1136">Allowed From</span></span>

<span data-ttu-id="7e9ce-1137">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1137">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-1138">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1138">Example</span></span>

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="7e9ce-1139">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1139">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="7e9ce-1140">Desbloquea un cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1140">Unlocks a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="7e9ce-1141">Prototipo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1141">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="7e9ce-1142">Descripción</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1142">Description</span></span>

<span data-ttu-id="7e9ce-1143">Este servicio desbloquea el cliente LWM2M previamente bloqueado mediante una llamada a ***nx_lwm2m_client_unlock***.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1143">This service unlocks the LWM2M Client previously locked by a call to ***nx_lwm2m_client_unlock***.</span></span>

### <a name="parameters"></a><span data-ttu-id="7e9ce-1144">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1144">Parameters</span></span>

- <span data-ttu-id="7e9ce-1145">**client_ptr**: puntero al bloque de control del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1145">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7e9ce-1146">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1146">Return Values</span></span>

- <span data-ttu-id="7e9ce-1147">**NX_SUCCESS**: operación correcta.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1147">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="7e9ce-1148">**NX_PTR_ERROR**: puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1148">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7e9ce-1149">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1149">Allowed From</span></span>

<span data-ttu-id="7e9ce-1150">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1150">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="7e9ce-1151">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7e9ce-1151">Example</span></span>

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```