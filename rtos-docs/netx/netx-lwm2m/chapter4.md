---
title: 'Capítulo 4: Descripción de los servicios de Azure RTOS NetX LWM2M'
description: Este capítulo contiene una descripción de todos los servicios Azure RTOS NetX LWM2M (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815169"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a><span data-ttu-id="e4d69-103">Capítulo 4: Descripción de los servicios de Azure RTOS NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-103">Chapter 4 - Description of Azure RTOS NetX LWM2M services</span></span>

<span data-ttu-id="e4d69-104">Este capítulo contiene una descripción de todos los servicios Azure RTOS NetX LWM2M (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="e4d69-104">This chapter contains a description of all Azure RTOS NetX LWM2M services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="e4d69-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="e4d69-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

### <a name="lwm2m-client-management"></a><span data-ttu-id="e4d69-106">Administración de clientes de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-106">LWM2M Client Management</span></span>

- <span data-ttu-id="e4d69-107">**nx_lwm2m_client_create**: *Crear cliente de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-107">**nx_lwm2m_client_create**: *Create LWM2M Client*</span></span>
- <span data-ttu-id="e4d69-108">**nx_lwm2m_client_delete**: *Eliminar cliente de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-108">**nx_lwm2m_client_delete**: *Delete LWM2M Client*</span></span>
- <span data-ttu-id="e4d69-109">**nx_lwm2m_client_lock**: *Bloquear cliente de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-109">**nx_lwm2m_client_lock**: *Lock LWM2M Client*</span></span>
- <span data-ttu-id="e4d69-110">**nx_lwm2m_client_object_add**: *Agregar implementación de objeto al cliente de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-110">**nx_lwm2m_client_object_add**: *Add Object implementation to the LWM2M Client*</span></span>
- <span data-ttu-id="e4d69-111">**nx_lwm2m_client_unlock**: *Desbloquear cliente de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-111">**nx_lwm2m_client_unlock**: *Unlock LWM2M Client*</span></span>

### <a name="lwm2m-client-session-management"></a><span data-ttu-id="e4d69-112">Administración de sesiones de clientes de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-112">LWM2M Client Session Management</span></span>

- <span data-ttu-id="e4d69-113">**nx_lwm2m_client_session_bootstrap**: *Iniciar sesión con un servidor de arranque*</span><span class="sxs-lookup"><span data-stu-id="e4d69-113">**nx_lwm2m_client_session_bootstrap**: *Start a session with a Bootstrap Server*</span></span>
- <span data-ttu-id="e4d69-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Iniciar una sesión segura con un servidor de arranque*</span><span class="sxs-lookup"><span data-stu-id="e4d69-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Start a secure session with a Bootstrap Server*</span></span>
- <span data-ttu-id="e4d69-115">**nx_lwm2m_client_session_create**: *Crear sesión de cliente de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-115">**nx_lwm2m_client_session_create**: *Create LWM2M Client Session*</span></span>
- <span data-ttu-id="e4d69-116">**nx_lwm2m_client_session_delete**: *Eliminación de sesión de cliente de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-116">**nx_lwm2m_client_session_delete**: *Delete LWM2M Client Session*</span></span>
- <span data-ttu-id="e4d69-117">**nx_lwm2m_client_session_deregister**: *Finalizar una sesión con un servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-117">**nx_lwm2m_client_session_deregister**: *Terminate a session with a LWM2M Server*</span></span>
- <span data-ttu-id="e4d69-118">**nx_lwm2m_client_session_error_get**: *Obtener el último error de una sesión*</span><span class="sxs-lookup"><span data-stu-id="e4d69-118">**nx_lwm2m_client_session_error_get**: *Get last error of a session*</span></span>
- <span data-ttu-id="e4d69-119">**nx_lwm2m_client_session_register**: *Iniciar una sesión con un servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-119">**nx_lwm2m_client_session_register**: *Start a session with a LWM2M Server*</span></span>
- <span data-ttu-id="e4d69-120">**nx_lwm2m_client_session_register_dtls**: *Iniciar una sesión segura con un servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-120">**nx_lwm2m_client_session_register_dtls**: *Start a secure session with a LWM2M Server*</span></span>
- <span data-ttu-id="e4d69-121">**nx_lwm2m_client_session_update**: *Actualizar una sesión con un servidor LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-121">**nx_lwm2m_client_session_update**: *Update a session with a LWM2M Server*</span></span>

### <a name="security-object-implementation"></a><span data-ttu-id="e4d69-122">Implementación de objetos de seguridad</span><span class="sxs-lookup"><span data-stu-id="e4d69-122">Security Object Implementation</span></span>

- <span data-ttu-id="e4d69-123">**nx_lwm2m_client_security_key_callbacks_set**: *Establecer devoluciones de llamada de administración de claves de seguridad*</span><span class="sxs-lookup"><span data-stu-id="e4d69-123">**nx_lwm2m_client_security_key_callbacks_set**: *Set security key management callbacks*</span></span>

### <a name="device-object-implementation"></a><span data-ttu-id="e4d69-124">Implementación de objetos de dispositivo</span><span class="sxs-lookup"><span data-stu-id="e4d69-124">Device Object Implementation</span></span>

- <span data-ttu-id="e4d69-125">**nx_lwm2m_client_device_callbacks_set**: *Establecer devoluciones de llamada de aplicaciones de objetos de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="e4d69-125">**nx_lwm2m_client_device_callbacks_set**: *Set Device Object application callbacks*</span></span>
- <span data-ttu-id="e4d69-126">**nx_lwm2m_client_device_error_push**: *Agregar un código de error a un objeto de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="e4d69-126">**nx_lwm2m_client_device_error_push**: *Add error code to Device Object*</span></span>
- <span data-ttu-id="e4d69-127">**nx_lwm2m_client_device_error_reset**: *Restablecer códigos de error del objeto de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="e4d69-127">**nx_lwm2m_client_device_error_reset**: *Reset error codes of Device Object*</span></span>
- <span data-ttu-id="e4d69-128">**nx_lwm2m_client_device_resource_changed**: *Cambio de señal del recurso de objeto de dispositivo*</span><span class="sxs-lookup"><span data-stu-id="e4d69-128">**nx_lwm2m_client_device_resource_changed**: *Signal change of Device Object resource*</span></span>

### <a name="custom-objects-implementation"></a><span data-ttu-id="e4d69-129">Implementación de objetos personalizados</span><span class="sxs-lookup"><span data-stu-id="e4d69-129">Custom Objects Implementation</span></span>

- <span data-ttu-id="e4d69-130">**nx_lwm2m_object_resource_changed**: *Cambio de señal de un valor de recursos de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="e4d69-130">**nx_lwm2m_object_resource_changed**: *Signal change of a resource value of an Object Instance*</span></span>

### <a name="local-device-management"></a><span data-ttu-id="e4d69-131">Administración de dispositivos locales</span><span class="sxs-lookup"><span data-stu-id="e4d69-131">Local Device Management</span></span>

- <span data-ttu-id="e4d69-132">**nx_lwm2m_client_object_create**: *Crear una nueva instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="e4d69-132">**nx_lwm2m_client_object_create**: *Create a new Object Instance*</span></span>
- <span data-ttu-id="e4d69-133">**nx_lwm2m_client_object_delete**: *Eliminar una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="e4d69-133">**nx_lwm2m_client_object_delete**: *Delete an Object Instance*</span></span>
- <span data-ttu-id="e4d69-134">**nx_lwm2m_client_object_discover**: *Detectar recursos de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="e4d69-134">**nx_lwm2m_client_object_discover**: *Discover resources of an Object Instance*</span></span>
- <span data-ttu-id="e4d69-135">**nx_lwm2m_client_object_execute**: *Ejecutar el recurso de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="e4d69-135">**nx_lwm2m_client_object_execute**: *Execute resource of an Object Instance*</span></span>
- <span data-ttu-id="e4d69-136">**nx_lwm2m_client_object_get_next**: *Obtener la lista de objetos implementados por el cliente de LWM2M*</span><span class="sxs-lookup"><span data-stu-id="e4d69-136">**nx_lwm2m_client_object_get_next**: *Get the list of Objects implemented by the LWM2M Client*</span></span>
- <span data-ttu-id="e4d69-137">**nx_lwm2m_client_object_instance_get_next**: *Obtener la lista de instancias de un objeto*</span><span class="sxs-lookup"><span data-stu-id="e4d69-137">**nx_lwm2m_client_object_instance_get_next**: *Get the list of Instances of an Object*</span></span>
- <span data-ttu-id="e4d69-138">**nx_lwm2m_client_object_read**: *Leer los valores de los recursos de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="e4d69-138">**nx_lwm2m_client_object_read**: *Read resources values of an Object Instance*</span></span>
- <span data-ttu-id="e4d69-139">**nx_lwm2m_client_object_write**: *Cambiar los valores de los recursos de una instancia de objeto*</span><span class="sxs-lookup"><span data-stu-id="e4d69-139">**nx_lwm2m_client_object_write**: *Change resources values of an Object instance*</span></span>

### <a name="resources-values-decoding"></a><span data-ttu-id="e4d69-140">Descodificación de valores de recursos</span><span class="sxs-lookup"><span data-stu-id="e4d69-140">Resources Values Decoding</span></span>

- <span data-ttu-id="e4d69-141">**nx_lwm2m_resource_get_boolean**: *Obtener el valor de un recurso booleano*</span><span class="sxs-lookup"><span data-stu-id="e4d69-141">**nx_lwm2m_resource_get_boolean**: *Get the value of a Boolean Resource*</span></span>
- <span data-ttu-id="e4d69-142">**nx_lwm2m_resource_get_float32**: *Obtener el valor de un recurso de punto flotante de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="e4d69-142">**nx_lwm2m_resource_get_float32**: *Get the value of a 32-bit Floating Point Resource*</span></span>
- <span data-ttu-id="e4d69-143">**nx_lwm2m_resource_get_float64**: *Obtener el valor de un recurso de punto flotante de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="e4d69-143">**nx_lwm2m_resource_get_float64**: *Get the value of a 64-bit Floating Point Resource*</span></span>
- <span data-ttu-id="e4d69-144">**nx_lwm2m_resource_get_integer32**: *Obtener el valor de un recurso entero de 32 bits*</span><span class="sxs-lookup"><span data-stu-id="e4d69-144">**nx_lwm2m_resource_get_integer32**: *Get the value of a 32-Bit Integer Resource*</span></span>
- <span data-ttu-id="e4d69-145">**nx_lwm2m_resource_get_integer64**: *Obtener el valor de un recurso entero de 64 bits*</span><span class="sxs-lookup"><span data-stu-id="e4d69-145">**nx_lwm2m_resource_get_integer64**: *Get the value of a 64-Bit Integer Resource*</span></span>
- <span data-ttu-id="e4d69-146">**nx_lwm2m_resource_get_objlnk**: *Obtener el valor de un recurso de vínculo de objeto*</span><span class="sxs-lookup"><span data-stu-id="e4d69-146">**nx_lwm2m_resource_get_objlnk**: *Get the value of an Object Link Resource*</span></span>
- <span data-ttu-id="e4d69-147">**nx_lwm2m_resource_get_opaque**: *Obtener el valor de un recurso opaco*</span><span class="sxs-lookup"><span data-stu-id="e4d69-147">**nx_lwm2m_resource_get_opaque**: *Get the value of an Opaque Resource*</span></span>
- <span data-ttu-id="e4d69-148">**nx_lwm2m_resource_get_string**: *Obtener el valor de un recurso de cadena*</span><span class="sxs-lookup"><span data-stu-id="e4d69-148">**nx_lwm2m_resource_get_string**: *Get the value of a String Resource*</span></span>
- <span data-ttu-id="e4d69-149">**nx_lwm2m_resource_multiple_get_boolean**: *Obtener el valor de una instancia de recurso booleano en un recurso múltiple*</span><span class="sxs-lookup"><span data-stu-id="e4d69-149">**nx_lwm2m_resource_multiple_get_boolean**: *Get the value of a Boolean Resource Multiple Resource Instance*</span></span>
- <span data-ttu-id="e4d69-150">**nx_lwm2m_resource_multiple_get_float32**: *Obtener el valor de una instancia de recurso de punto flotante de 32 bits en un recurso múltiple*</span><span class="sxs-lookup"><span data-stu-id="e4d69-150">**nx_lwm2m_resource_multiple_get_float32**: *Get the value of a 32-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="e4d69-151">**nx_lwm2m_resource_multiple_get_float64**: *Obtener el valor de un punto flotante de 64 bits en una instancia de múltiples recursos*</span><span class="sxs-lookup"><span data-stu-id="e4d69-151">**nx_lwm2m_resource_multiple_get_float64**: *Get the value of a 64-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="e4d69-152">**nx_lwm2m_resource_multiple_get_integer32**: *Obtener el valor de una instancia de recurso entero de 32 bits de un recurso múltiple*</span><span class="sxs-lookup"><span data-stu-id="e4d69-152">**nx_lwm2m_resource_multiple_get_integer32**: *Get the value of a 32-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="e4d69-153">**nx_lwm2m_resource_multiple_get_integer64**: *Obtener el valor de una instancia de recurso entero de 64 bits de un recurso múltiple*</span><span class="sxs-lookup"><span data-stu-id="e4d69-153">**nx_lwm2m_resource_multiple_get_integer64**: *Get the value of a 64-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="e4d69-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Obtener el valor de una instancia de recurso de enlace de objeto de un recurso múltiple*</span><span class="sxs-lookup"><span data-stu-id="e4d69-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Get the value of an Object Link Multiple Resource Instance*</span></span>
- <span data-ttu-id="e4d69-155">**nx_lwm2m_resource_multiple_get_opaque**: *Obtener el valor de una instancia de recurso opaco de un recurso múltiple*</span><span class="sxs-lookup"><span data-stu-id="e4d69-155">**nx_lwm2m_resource_multiple_get_opaque**: *Get the value of an Opaque Multiple Resource Instance*</span></span>
- <span data-ttu-id="e4d69-156">**nx_lwm2m_resource_multiple_get_string**: *Obtener el valor de una instancia de cadena de un recurso múltiple*</span><span class="sxs-lookup"><span data-stu-id="e4d69-156">**nx_lwm2m_resource_multiple_get_string**: *Get the value of a String Multiple Resource Instance*</span></span>

### <a name="firmware-update-object"></a><span data-ttu-id="e4d69-157">objeto de actualización de firmware</span><span class="sxs-lookup"><span data-stu-id="e4d69-157">Firmware Update Object</span></span>

- <span data-ttu-id="e4d69-158">**nx_lwm2m_firmware_create**: *Crear el objeto de actualización de firmware*</span><span class="sxs-lookup"><span data-stu-id="e4d69-158">**nx_lwm2m_firmware_create**: *Create Firmware Update Object*</span></span>
- <span data-ttu-id="e4d69-159">**nx_lwm2m_firmware_package_info_set**: *Establecer la información de paquetes de actualización de firmware*</span><span class="sxs-lookup"><span data-stu-id="e4d69-159">**nx_lwm2m_firmware_package_info_set**: *Set Firmware Update Package Information*</span></span>
- <span data-ttu-id="e4d69-160">**nx_lwm2m_firmware_result_set**: *Establecer el resultado de la actualización de firmware*</span><span class="sxs-lookup"><span data-stu-id="e4d69-160">**nx_lwm2m_firmware_result_set**: *Set Firmware Update Result*</span></span>
- <span data-ttu-id="e4d69-161">**nx_lwm2m_firmware_state_set**: *Establecer el estado de la actualización de firmware*</span><span class="sxs-lookup"><span data-stu-id="e4d69-161">**nx_lwm2m_firmware_state_set**: *Set Firmware Update State*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="e4d69-162">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="e4d69-162">nx_lwm2m_client_create</span></span>

<span data-ttu-id="e4d69-163">Creación de cliente de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-163">Create LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-164">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-164">Prototype</span></span>

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="e4d69-165">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-165">Description</span></span>

<span data-ttu-id="e4d69-166">Este servicio crea una instancia de cliente de LWM2M que se ejecuta en el contexto de su propio subproceso ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e4d69-166">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="e4d69-167">El cliente de LWM2M implementa los siguientes objetos OMA LWM2M: Security (0), Server (1), Access Control (2) y Device (3).</span><span class="sxs-lookup"><span data-stu-id="e4d69-167">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="e4d69-168">La aplicación debe agregar las implementaciones de otros objetos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-168">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-169">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-169">Parameters</span></span>

- <span data-ttu-id="e4d69-170">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-170">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-171">**ip_ptr**: Puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-171">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="e4d69-172">**packet_pool_ptr**: Puntero al grupo de paquetes predeterminado para este cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-172">**packet_pool_ptr**: Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="e4d69-173">**local_port**: Puerto UDP local que se usa para la comunicación no segura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-173">**local_port**: The local UDP port used for non-secure communication.</span></span>
- <span data-ttu-id="e4d69-174">**name_ptr**: Puntero al nombre de punto de conexión del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-174">**name_ptr**: Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="e4d69-175">**msisdn_ptr**: Puntero a MSISDN, donde se puede acceder al cliente de LWM2M para su uso con el enlace SMS; puede ser NULL si no se admite el enlace SMS.</span><span class="sxs-lookup"><span data-stu-id="e4d69-175">**msisdn_ptr**: Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="e4d69-176">**binding_modes**: El enlace y los modos admitidos por el cliente de LWM2M, deben ser una combinación de las marcas NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S y NX_LWM2M_BINDING_SQ.</span><span class="sxs-lookup"><span data-stu-id="e4d69-176">**binding_modes**: The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="e4d69-177">**stack_ptr**: Puntero al área de la pila de subprocesos del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-177">**stack_ptr**: Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="e4d69-178">**stack_size**: Tamaño de la pila de subprocesos del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-178">**stack_size**: The LWM2M Client thread stack size.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-179">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-179">Return Values</span></span>

- <span data-ttu-id="e4d69-180">**NX_SUCCESS**: El cliente de LWM2M se ha creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-180">**NX_SUCCESS**: The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="e4d69-181">**NX_LWM2M_ERROR**: Error al crear el cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-181">**NX_LWM2M_ERROR**: LWM2M Client create error.</span></span>
- <span data-ttu-id="e4d69-182">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-182">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="e4d69-183">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="e4d69-183">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="e4d69-184">Eliminación de clientes de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-184">Delete LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-185">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-185">Prototype</span></span>

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-186">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-186">Description</span></span>

<span data-ttu-id="e4d69-187">Este servicio elimina una instancia de cliente de LWM2M creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-187">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="e4d69-188">Esta llamada también elimina todas las sesiones asociadas actualmente al cliente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-188">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-189">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-189">Parameters</span></span>

- <span data-ttu-id="e4d69-190">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-190">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-191">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-191">Return Values</span></span>

- <span data-ttu-id="e4d69-192">**NX_SUCCESS**: El cliente de LWM2M se ha eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-192">**NX_SUCCESS**: The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="e4d69-193">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-193">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_callbacks_set"></a><span data-ttu-id="e4d69-194">nx_lwm2m_client_device_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="e4d69-194">nx_lwm2m_client_device_callbacks_set</span></span>

<span data-ttu-id="e4d69-195">Definición de devoluciones de llamada de aplicaciones de objetos de dispositivo</span><span class="sxs-lookup"><span data-stu-id="e4d69-195">Set Device Object application callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-196">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-196">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a><span data-ttu-id="e4d69-197">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-197">Description</span></span>

<span data-ttu-id="e4d69-198">Este servicio instala las devoluciones de llamada de la aplicación para implementar operaciones en los recursos de objeto de dispositivo de LWM2M que no son controlados por el cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-198">This service installs the application callbacks for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="e4d69-199">El cliente de LWM2M implementa los siguientes recursos: Error Code (11), Reset Error Code (12) and Supported Binding y Modes (16); las operaciones con los demás recursos se redirigen a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e4d69-199">The LWM2M Client implements the following resources : Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-200">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-200">Parameters</span></span>

- <span data-ttu-id="e4d69-201">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-201">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-202">**read_callback**: Devolución de llamada del método de lectura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-202">**read_callback**: The 'Read' method callback.</span></span>
- <span data-ttu-id="e4d69-203">**discover_callback**: Devolución de llamada del método de descubrimiento.</span><span class="sxs-lookup"><span data-stu-id="e4d69-203">**discover_callback**: The 'Discover' method callback.</span></span>
- <span data-ttu-id="e4d69-204">**write_callback**: Devolución de llamada del método de escritura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-204">**write_callback**: The 'Write' method callback.</span></span>
- <span data-ttu-id="e4d69-205">**execute_callback**: Devolución de llamada del método de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e4d69-205">**execute_callback**: The 'Execute' method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-206">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-206">Return Values</span></span>

- <span data-ttu-id="e4d69-207">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-207">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-208">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-208">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="e4d69-209">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="e4d69-209">nx_lwm2m_client_device_error_push</span></span>

<span data-ttu-id="e4d69-210">Adición de un código de error a un objeto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="e4d69-210">Add error code to Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-211">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-211">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a><span data-ttu-id="e4d69-212">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-212">Description</span></span>

<span data-ttu-id="e4d69-213">Este servicio agrega una nueva instancia al recurso Error Code (11) del dispositivo de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-213">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-214">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-214">Parameters</span></span>

- <span data-ttu-id="e4d69-215">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-215">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-216">**code**: Nuevo código de error.</span><span class="sxs-lookup"><span data-stu-id="e4d69-216">**code**: The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-217">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-217">Return Values</span></span>

- <span data-ttu-id="e4d69-218">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-218">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-219">**NX_LWM2M_BUFFER_TOO_SMALL**: Se ha alcanzado el número máximo de códigos de error almacenados.</span><span class="sxs-lookup"><span data-stu-id="e4d69-219">**NX_LWM2M_BUFFER_TOO_SMALL**: The maximum number of stored error codes has been reached.</span></span>
- <span data-ttu-id="e4d69-220">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-220">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="e4d69-221">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="e4d69-221">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="e4d69-222">Restablecimiento de códigos de error del objeto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="e4d69-222">Reset error codes of Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-223">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-223">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-224">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-224">Description</span></span>

<span data-ttu-id="e4d69-225">Este servicio elimina todas las instancias de recursos de código de error del objeto de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e4d69-225">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="e4d69-226">Esto es equivalente a la ejecución del código del recurso Reset Error Code (12).</span><span class="sxs-lookup"><span data-stu-id="e4d69-226">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-227">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-227">Parameters</span></span>

- <span data-ttu-id="e4d69-228">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-228">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-229">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-229">Return Values</span></span>

- <span data-ttu-id="e4d69-230">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-230">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-231">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-231">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="e4d69-232">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="e4d69-232">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="e4d69-233">Cambio de señal del recurso de objeto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="e4d69-233">Signal change of Device Object resource</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-234">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-234">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="e4d69-235">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-235">Description</span></span>

<span data-ttu-id="e4d69-236">La aplicación usa el servicio para indicar al cliente de LWM2M que un recurso del objeto de dispositivo ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="e4d69-236">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="e4d69-237">El cliente de LWM2M enviará una notificación si un servidor LWM2M observa el recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-237">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-238">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-238">Parameters</span></span>

- <span data-ttu-id="e4d69-239">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-239">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-240">**resource**: Puntero a la estructura que describe el recurso que ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="e4d69-240">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-241">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-241">Return Values</span></span>

- <span data-ttu-id="e4d69-242">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-242">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-243">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-243">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="e4d69-244">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="e4d69-244">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="e4d69-245">Bloqueo del cliente de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-245">Lock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-246">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-246">Prototype</span></span>

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-247">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-247">Description</span></span>

<span data-ttu-id="e4d69-248">Este servicio bloquea al cliente de LWM2M para impedir el acceso simultáneo a los objetos LWM2M desde los servidores o desde otro subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="e4d69-248">This service locks the LWM2M Client to prevent concurent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="e4d69-249">Si el cliente de LWM2M está bloqueado actualmente por otro subproceso, la función se bloqueará hasta que se desbloquee el cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-249">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="e4d69-250">Las llamadas a pares nx_lwm2m_client_lock nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() se pueden anidar.</span><span class="sxs-lookup"><span data-stu-id="e4d69-250">Calls to nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-251">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-251">Parameters</span></span>

- <span data-ttu-id="e4d69-252">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-252">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-253">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-253">Return Values</span></span>

- <span data-ttu-id="e4d69-254">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-254">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-255">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-255">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="e4d69-256">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="e4d69-256">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="e4d69-257">Adición de implementación de objeto al cliente de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-257">Add Object implementation to the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-258">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-258">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-259">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-259">Description</span></span>

<span data-ttu-id="e4d69-260">Este servicio agrega una nueva implementación de objeto al cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-260">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-261">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-261">Parameters</span></span>

- <span data-ttu-id="e4d69-262">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-262">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-263">**object_ptr**: Puntero a la estructura que define la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-263">**object_ptr**: Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-264">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-264">Return Values</span></span>

- <span data-ttu-id="e4d69-265">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-265">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-266">**NX_LWM2M_ALREADY_EXIST**: El id. de objeto ya existe.</span><span class="sxs-lookup"><span data-stu-id="e4d69-266">**NX_LWM2M_ALREADY_EXIST**: The Object ID already exists.</span></span>
- <span data-ttu-id="e4d69-267">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-267">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="e4d69-268">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="e4d69-268">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="e4d69-269">Creación de una nueva instancia de objeto</span><span class="sxs-lookup"><span data-stu-id="e4d69-269">Create a new Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-270">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-270">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-271">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-271">Description</span></span>

<span data-ttu-id="e4d69-272">Este servicio realiza una operación de creación en un objeto del cliente de LWM2M para crear una nueva instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-272">This service performs a 'Create' operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-273">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-273">Parameters</span></span>

- <span data-ttu-id="e4d69-274">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-274">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-275">**object_id**: Id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-275">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="e4d69-276">**instance_id_ptr**: Puntero al id. de la nueva instancia, puede ser NULL si el cliente de LWM2M debe asignar un id. de instancia.</span><span class="sxs-lookup"><span data-stu-id="e4d69-276">**instance_id_ptr**: Pointer to the ID of the new instance, can be NULL if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="e4d69-277">Si el id. es el valor reservado 65535, el cliente de LWM2M asignará un id. de instancia.</span><span class="sxs-lookup"><span data-stu-id="e4d69-277">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="e4d69-278">Si no es NULL, el id. asignado se devuelve después de la llamada.</span><span class="sxs-lookup"><span data-stu-id="e4d69-278">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="e4d69-279">**num_values**: Número de valores que se van a definir.</span><span class="sxs-lookup"><span data-stu-id="e4d69-279">**num_values**: The number of values to set.</span></span>
- <span data-ttu-id="e4d69-280">**values_ptr**: Puntero a una matriz de valores de recursos para inicializar la nueva instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-280">**values_ptr**: Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-281">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-281">Return Values</span></span>

- <span data-ttu-id="e4d69-282">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-282">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-283">**NX_LWM2M_ALREADY_EXIST**: El id. de instancia de objeto ya existe.</span><span class="sxs-lookup"><span data-stu-id="e4d69-283">**NX_LWM2M_ALREADY_EXIST**: The Object Instance ID already exists.</span></span>
- <span data-ttu-id="e4d69-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: El objeto no admite la creación de instancias.</span><span class="sxs-lookup"><span data-stu-id="e4d69-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance creation.</span></span>
- <span data-ttu-id="e4d69-285">**NX_LWM2M_NO_MEMORY**: No se puede asignar memoria para almacenar la nueva instancia.</span><span class="sxs-lookup"><span data-stu-id="e4d69-285">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="e4d69-286">**NX_LWM2M_NOT_FOUND**: El id. de objeto no existe.</span><span class="sxs-lookup"><span data-stu-id="e4d69-286">**NX_LWM2M_NOT_FOUND**: The Object ID doesn't exist.</span></span>
- <span data-ttu-id="e4d69-287">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-287">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="e4d69-288">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="e4d69-288">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="e4d69-289">Eliminación de una instancia de objeto</span><span class="sxs-lookup"><span data-stu-id="e4d69-289">Delete an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-290">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-290">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="e4d69-291">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-291">Description</span></span>

<span data-ttu-id="e4d69-292">Este servicio realiza una operación de eliminación en una instancia de objeto del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-292">This service performs a 'Delete' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-293">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-293">Parameters</span></span>

- <span data-ttu-id="e4d69-294">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-294">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-295">**object_id**: Id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-295">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="e4d69-296">**instance_id**: Id. de instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-296">**instance_id**: The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-297">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-297">Return Values</span></span>

- <span data-ttu-id="e4d69-298">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-298">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: El objeto no admite la eliminación de instancias.</span><span class="sxs-lookup"><span data-stu-id="e4d69-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance deletion.</span></span>
- <span data-ttu-id="e4d69-300">**NX_LWM2M_NOT_FOUND**: El id. de objeto o el id. de instancia de objeto no existen.</span><span class="sxs-lookup"><span data-stu-id="e4d69-300">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="e4d69-301">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-301">NX_PTR_ERROR Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="e4d69-302">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="e4d69-302">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="e4d69-303">Detección de recursos de una instancia de objeto</span><span class="sxs-lookup"><span data-stu-id="e4d69-303">Discover resources of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-304">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-304">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-305">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-305">Description</span></span>

<span data-ttu-id="e4d69-306">Este servicio realiza una operación de descubrimiento en una instancia de objeto del cliente de LWM2M, lo que devuelve la lista de recursos implementados por el objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-306">This service performs a 'Discover' operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-307">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-307">Parameters</span></span>

- <span data-ttu-id="e4d69-308">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-308">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-309">**object_id**: Id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-309">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="e4d69-310">**instance_id**: Id. de instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-310">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="e4d69-311">**num_resources_ptr**: En la entrada, el tamaño del búfer de destino, en la salida, el número de elementos escritos en el búfer.</span><span class="sxs-lookup"><span data-stu-id="e4d69-311">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>
- <span data-ttu-id="e4d69-312">**resources_ptr**: Puntero al búfer de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-312">**resources_ptr**: Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-313">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-313">Return Values</span></span>

- <span data-ttu-id="e4d69-314">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-314">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="e4d69-315">**NX_LWM2M_BUFFER_TOO_SMALL**: El búfer de recursos es demasiado pequeño para almacenar la lista de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-315">**NX_LWM2M_BUFFER_TOO_SMALL**: The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="e4d69-316">**NX_LWM2M_NOT_FOUND**: El id. de objeto o el id. de instancia de objeto no existen.</span><span class="sxs-lookup"><span data-stu-id="e4d69-316">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="e4d69-317">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-317">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="e4d69-318">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="e4d69-318">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="e4d69-319">Ejecución del recurso de una instancia de objeto</span><span class="sxs-lookup"><span data-stu-id="e4d69-319">Execute resource of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-320">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-320">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="e4d69-321">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-321">Description</span></span>

<span data-ttu-id="e4d69-322">Este servicio realiza una operación de ejecución en una instancia de objeto del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-322">This service performs the 'Execute' operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-323">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-323">Parameters</span></span>

- <span data-ttu-id="e4d69-324">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-324">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-325">**object_id**: Id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-325">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="e4d69-326">**instance_id**: Id. de instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-326">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="e4d69-327">**resource_id**: Id. de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-327">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="e4d69-328">**arguments_ptr**: Puntero a los argumentos de la operación de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e4d69-328">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="e4d69-329">Puede ser NULL si arguments_length es cero.</span><span class="sxs-lookup"><span data-stu-id="e4d69-329">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="e4d69-330">**arguments_length**: Longitud de los argumentos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-330">**arguments_length**: The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-331">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-331">Return Values</span></span>

- <span data-ttu-id="e4d69-332">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-332">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: El recurso no admite la operación de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e4d69-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: The resource doesn't support the execute operation.</span></span>
- <span data-ttu-id="e4d69-334">**NX_LWM2M_NOT_FOUND**: El id. de objeto, el id. de instancia de objeto o el id. de recurso no existen.</span><span class="sxs-lookup"><span data-stu-id="e4d69-334">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or the resource ID doesn't exist.</span></span>
- <span data-ttu-id="e4d69-335">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-335">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_get_next"></a><span data-ttu-id="e4d69-336">nx_lwm2m_client_object_get_next</span><span class="sxs-lookup"><span data-stu-id="e4d69-336">nx_lwm2m_client_object_get_next</span></span>

<span data-ttu-id="e4d69-337">Obtención de la lista de objetos implementados por el cliente de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-337">Get the list of Objects implemented by the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-338">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-338">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-339">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-339">Description</span></span>

<span data-ttu-id="e4d69-340">Este servicio devuelve el id. del siguiente objeto implementado por el cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-340">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="e4d69-341">Si el id. de objeto actual se establece en NX_LWM2M_RESERVED_ID (65535), se devuelve el primer id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-341">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-342">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-342">Parameters</span></span>

- <span data-ttu-id="e4d69-343">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-343">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-344">**object_id_ptr**: Puntero al id. de objeto actual.</span><span class="sxs-lookup"><span data-stu-id="e4d69-344">**object_id_ptr**: Pointer to the current Object ID.</span></span> <span data-ttu-id="e4d69-345">En la devolución, contiene el siguiente id. de objeto implementado por el cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-345">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-346">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-346">Return Values</span></span>

- <span data-ttu-id="e4d69-347">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-347">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="e4d69-348">**NX_LWM2M_NOT_FOUND**: El id. de objeto especificado es el último de la base de datos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-348">**NX_LWM2M_NOT_FOUND**: The given Object ID is the last of the database.</span></span>
- <span data-ttu-id="e4d69-349">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-349">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_instance_get_next"></a><span data-ttu-id="e4d69-350">nx_lwm2m_client_object_instance_get_next</span><span class="sxs-lookup"><span data-stu-id="e4d69-350">nx_lwm2m_client_object_instance_get_next</span></span>

<span data-ttu-id="e4d69-351">Obtención de la lista de instancias de un objeto</span><span class="sxs-lookup"><span data-stu-id="e4d69-351">Get the list of Instances of an Object</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-352">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-352">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-353">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-353">Description</span></span>

<span data-ttu-id="e4d69-354">Este servicio devuelve el id. de la siguiente instancia de objeto del objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="e4d69-354">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="e4d69-355">Si el id. de instancia actual se establece en NX_LWM2M_RESERVED_ID (65535), se devuelve el id. de la primera instancia.</span><span class="sxs-lookup"><span data-stu-id="e4d69-355">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-356">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-356">Parameters</span></span>

- <span data-ttu-id="e4d69-357">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-357">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-358">**object_id**: Id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-358">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="e4d69-359">**instance_id_ptr**: Puntero al id. de instancia de objeto actual.</span><span class="sxs-lookup"><span data-stu-id="e4d69-359">**instance_id_ptr**: Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="e4d69-360">En la devolución, contiene el id. de instancia siguiente del objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-360">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-361">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-361">Return Values</span></span>

- <span data-ttu-id="e4d69-362">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-362">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="e4d69-363">**NX_LWM2M_NOT_FOUND**: El id. de instancia proporcionado es el último del objeto o el id. de objeto no está implementado.</span><span class="sxs-lookup"><span data-stu-id="e4d69-363">**NX_LWM2M_NOT_FOUND**: The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="e4d69-364">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-364">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="e4d69-365">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="e4d69-365">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="e4d69-366">Lectura de los valores de los recursos de una instancia de objeto</span><span class="sxs-lookup"><span data-stu-id="e4d69-366">Read resources values of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-367">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-367">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="e4d69-368">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-368">Description</span></span>

<span data-ttu-id="e4d69-369">Este servicio realiza una operación de lectura en una instancia de objeto del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-369">This service performs a 'Read' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-370">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-370">Parameters</span></span>

- <span data-ttu-id="e4d69-371">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-371">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-372">**object_id**: Id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-372">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="e4d69-373">**instance_id**: Id. de instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-373">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="e4d69-374">**num_values**: El número de recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="e4d69-374">**num_values**: The number of resources to read.</span></span>
- <span data-ttu-id="e4d69-375">**values_ptr**: Puntero a una matriz de NX_LWM2M_RESOURCE que contiene los id. de los recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="e4d69-375">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="e4d69-376">En la devolución, la matriz se rellena con los tipos y valores correspondientes.</span><span class="sxs-lookup"><span data-stu-id="e4d69-376">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-377">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-377">Return Values</span></span>

- <span data-ttu-id="e4d69-378">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-378">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: Un recurso no admite la operación de lectura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the read operation.</span></span>
- <span data-ttu-id="e4d69-380">**NX_LWM2M_NOT_FOUND**: El id. de objeto, el id. de instancia de objeto o un id. de recursos no existen.</span><span class="sxs-lookup"><span data-stu-id="e4d69-380">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="e4d69-381">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-381">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="e4d69-382">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="e4d69-382">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="e4d69-383">Modificación de los valores de los recursos de una instancia de objeto</span><span class="sxs-lookup"><span data-stu-id="e4d69-383">Change resources values of an Object instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-384">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-384">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a><span data-ttu-id="e4d69-385">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-385">Description</span></span>

<span data-ttu-id="e4d69-386">Este servicio realiza una operación de escritura en una instancia de objeto del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-386">This service performs a 'Write' operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="e4d69-387">Se pueden especificar las siguientes operaciones de escritura en el parámetro *write_op*:</span><span class="sxs-lookup"><span data-stu-id="e4d69-387">The following write operations can be specified to the *write_op* parameter:</span></span>

- <span data-ttu-id="e4d69-388">**0** &mdash; Partial Update: Agrega o actualiza los recursos proporcionados en el nuevo valor y deja sin modificar otros recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="e4d69-388">**0** &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="e4d69-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: Reemplaza la instancia de objeto con los nuevos valores de recursos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="e4d69-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="e4d69-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: Reemplaza los recursos con los nuevos valores de recursos proporcionados (usados para reemplazar recursos múltiples).</span><span class="sxs-lookup"><span data-stu-id="e4d69-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="e4d69-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: Indica una llamada desde una secuencia de arranque.</span><span class="sxs-lookup"><span data-stu-id="e4d69-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: indicates a call from a Bootstrap sequence.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-392">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-392">Parameters</span></span>

- <span data-ttu-id="e4d69-393">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-393">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-394">**object_id**: Id. de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-394">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="e4d69-395">**instance_id**: Id. de instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-395">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="e4d69-396">**num_values**: Número de recursos que se van a escribir.</span><span class="sxs-lookup"><span data-stu-id="e4d69-396">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="e4d69-397">**values_ptr**: Puntero a una matriz de NX_LWM2M_RESOURCE que contiene los id. de los recursos, los tipos y los valores que se van a escribir.</span><span class="sxs-lookup"><span data-stu-id="e4d69-397">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="e4d69-398">**write_op**: Tipo de operación de escritura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-398">**write_op**: The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-399">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-399">Return Values</span></span>

- <span data-ttu-id="e4d69-400">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-400">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-401">**NX_LWM2M_BAD_ENCODING**: El tipo de un recurso no es válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-401">**NX_LWM2M_BAD_ENCODING**: The type of a resource is not valid.</span></span>
- <span data-ttu-id="e4d69-402">**NX_LWM2M_BUFFER_TOO_SMALL**: La longitud de un valor es demasiado grande para almacenarse en la instancia.</span><span class="sxs-lookup"><span data-stu-id="e4d69-402">**NX_LWM2M_BUFFER_TOO_SMALL**: The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="e4d69-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: Un recurso no admite la operación de escritura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the write operation.</span></span>
- <span data-ttu-id="e4d69-404">**NX_LWM2M_NO_MEMORY**: No se puede asignar memoria para almacenar un valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-404">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="e4d69-405">**NX_LWM2M_NOT_ACCEPTABLE**: El valor de un recurso no es válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-405">**NX_LWM2M_NOT_ACCEPTABLE**: The value of a resource is not valid.</span></span>
- <span data-ttu-id="e4d69-406">**NX_LWM2M_NOT_FOUND**: El id. de objeto, el id. de instancia de objeto o un id. de recursos no existen.</span><span class="sxs-lookup"><span data-stu-id="e4d69-406">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="e4d69-407">NX_OPTION_ERROR: Tipo no válido de operación de escritura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-407">NX_OPTION_ERROR: Invalid type of write operation.</span></span>
- <span data-ttu-id="e4d69-408">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-408">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a><span data-ttu-id="e4d69-409">nx_lwm2m_client_security_key_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="e4d69-409">nx_lwm2m_client_security_key_callbacks_set</span></span>

<span data-ttu-id="e4d69-410">Definición de devoluciones de llamada de administración de claves de objetos de seguridad</span><span class="sxs-lookup"><span data-stu-id="e4d69-410">Set Security Object key management callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-411">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-411">Prototype</span></span>

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a><span data-ttu-id="e4d69-412">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-412">Description</span></span>

<span data-ttu-id="e4d69-413">Este servicio instala las devoluciones de llamada de la aplicación para implementar operaciones en los recursos del objeto de seguridad de LWM2M relacionados con las claves de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e4d69-413">This service installs the application callbacks for implementing operations on the LWM2M Security Object resources related to the security keys.</span></span>

<span data-ttu-id="e4d69-414">El cliente de LWM2M delega la administración de claves de seguridad en la aplicación durante las sesiones de arranque, se llamará a las devoluciones de llamada cuando el servidor de arranque escriba o elimine los siguientes recursos en una instancia de objeto de seguridad: Public Key o Identity (3), Server Public Key (4), Secret Key (5).</span><span class="sxs-lookup"><span data-stu-id="e4d69-414">The LWM2M Client delegates the security key management to the application during the Bootstrap sessions, the callbacks will be called when the Bootstrap Server writes or deletes the following resources on a Security Object Instance: Public Key or Identity (3), Server Public Key (4), Secret Key (5).</span></span>

<span data-ttu-id="e4d69-415">La aplicación es responsable del almacenamiento de los datos de claves y de la configuración de las sesiones DTLS usadas por el cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-415">The application is responsible for storing the keys data and for configuring the DTLS sessions used by the LWM2M client.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-416">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-416">Parameters</span></span>

- <span data-ttu-id="e4d69-417">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-417">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="e4d69-418">**write_callback**: Devolución de llamada del método de clave de escritura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-418">**write_callback**: The 'Write' key method callback.</span></span>
- <span data-ttu-id="e4d69-419">**delete_callback**: Devolución de llamada del método de clave de eliminación.</span><span class="sxs-lookup"><span data-stu-id="e4d69-419">**delete_callback**: The 'Delete' key method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-420">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-420">Return Values</span></span>

- <span data-ttu-id="e4d69-421">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-421">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-422">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-422">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="e4d69-423">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="e4d69-423">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="e4d69-424">Inicio de una sesión con un servidor de arranque</span><span class="sxs-lookup"><span data-stu-id="e4d69-424">Start a session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-425">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-425">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="e4d69-426">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-426">Description</span></span>

<span data-ttu-id="e4d69-427">Este servicio inicia una sesión con un servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="e4d69-427">This service start a session with a Bootstrap Server.</span></span> <span data-ttu-id="e4d69-428">El servidor debe tener una instancia de seguridad correspondiente en el objeto de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e4d69-428">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="e4d69-429">Si el recurso de espera es distinto de cero en la instancia de seguridad asociada a este servidor, la sesión esperará a un arranque iniciado por el servidor, si el servidor no inicia ningún arranque después de este período de tiempo, se llevará a cabo un arranque iniciado por el cliente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-429">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="e4d69-430">Esta llamada anula cualquier sesión activa actual y se reemplaza por la nueva sesión del servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="e4d69-430">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-431">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-431">Parameters</span></span>

- <span data-ttu-id="e4d69-432">**session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-432">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="e4d69-433">**security_id**: Id. de instancia de seguridad del servidor de arranque; debe establecerse en NX_LWM2M_RESERVED_ID (65535) si el servidor de arranque no tiene definida ninguna instancia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e4d69-433">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="e4d69-434">**ip_address**: Dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-434">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="e4d69-435">**port**: Puerto UDP del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-435">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-436">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-436">Return Values</span></span>

- <span data-ttu-id="e4d69-437">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-437">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-438">**NX_LWM2M_NOT_FOUND**: No hay ninguna instancia de objeto de seguridad correspondiente al id. de instancia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e4d69-438">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="e4d69-439">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-439">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="e4d69-440">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="e4d69-440">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="e4d69-441">Inicio de una sesión segura con un servidor de arranque</span><span class="sxs-lookup"><span data-stu-id="e4d69-441">Start a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-442">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-442">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="e4d69-443">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-443">Description</span></span>

<span data-ttu-id="e4d69-444">Este servicio inicia una sesión con un servidor de arranque mediante una conexión DTLS segura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-444">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="e4d69-445">El servidor debe tener una instancia de seguridad correspondiente en el objeto de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e4d69-445">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="e4d69-446">La sesión DTLS se debe haber configurado con los conjuntos de cifrado y el material de clave adecuados antes de llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="e4d69-446">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="e4d69-447">NX_SECURE_ENABLE_DTLS debe definirse.</span><span class="sxs-lookup"><span data-stu-id="e4d69-447">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="e4d69-448">Si el recurso de espera es distinto de cero en la instancia de seguridad asociada a este servidor, la sesión esperará a un arranque iniciado por el servidor, si el servidor no inicia ningún arranque después de este período de tiempo, se llevará a cabo un arranque iniciado por el cliente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-448">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="e4d69-449">Esta llamada anula cualquier sesión activa actual y se reemplaza por la nueva sesión del servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="e4d69-449">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-450">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-450">Parameters</span></span>

- <span data-ttu-id="e4d69-451">**session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-451">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="e4d69-452">**security_id**: Id. de instancia de seguridad del servidor de arranque; debe establecerse en NX_LWM2M_RESERVED_ID (65535) si el servidor de arranque no tiene definida ninguna instancia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e4d69-452">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="e4d69-453">**ip_address**: Dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-453">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="e4d69-454">**port**: Puerto UDP del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-454">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="e4d69-455">**dtls_session_ptr**: Sesión DTLS que se va a usar para la sesión de arranque.</span><span class="sxs-lookup"><span data-stu-id="e4d69-455">**dtls_session_ptr**: The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="e4d69-456">**dtls_local_port**: Puerto UDP local usado para la sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="e4d69-456">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-457">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-457">Return Values</span></span>

- <span data-ttu-id="e4d69-458">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-458">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-459">**NX_LWM2M_NOT_FOUND**: No hay ninguna instancia de objeto de seguridad correspondiente al id. de instancia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e4d69-459">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="e4d69-460">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-460">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="e4d69-461">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="e4d69-461">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="e4d69-462">Creación de una sesión de cliente de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-462">Create LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-463">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-463">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="e4d69-464">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-464">Description</span></span>

<span data-ttu-id="e4d69-465">Este servicio crea una nueva sesión de cliente de LWM2M asociada a un cliente de LWM2M existente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-465">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="e4d69-466">El cliente de LWM2M usa la sesión para comunicarse con un servidor de arranque o un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-466">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span>

<span data-ttu-id="e4d69-467">La aplicación debe proporcionar una función de devolución de llamada a la que se llamará cuando se actualice el estado de la sesión.</span><span class="sxs-lookup"><span data-stu-id="e4d69-467">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-468">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-468">Parameters</span></span>

- <span data-ttu-id="e4d69-469">**session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-469">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="e4d69-470">**client_ptr**: Puntero al cliente de LWM2M creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-470">**client_ptr**: Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="e4d69-471">**state_callback**: Devolución de llamada de la aplicación a la que se llama cuando el estado de la sesión ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="e4d69-471">**state_callback**: Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-472">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-472">Return Values</span></span>

- <span data-ttu-id="e4d69-473">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-473">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-474">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-474">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="e4d69-475">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="e4d69-475">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="e4d69-476">Eliminación de una sesión de cliente de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-476">Delete LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-477">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-477">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-478">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-478">Description</span></span>

<span data-ttu-id="e4d69-479">Este servicio elimina una sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-479">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="e4d69-480">Cuando se elimina un cliente de LWM2M mediante una llamada a nx_lwm2m_client_delete también se eliminan todas las sesiones asociadas al cliente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-480">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-481">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-481">Parameters</span></span>

- <span data-ttu-id="e4d69-482">**session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-482">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-483">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-483">Return Values</span></span>

- <span data-ttu-id="e4d69-484">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-484">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-485">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-485">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="e4d69-486">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="e4d69-486">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="e4d69-487">Finalización de una sesión con un servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-487">Terminate a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-488">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-489">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-489">Description</span></span>

<span data-ttu-id="e4d69-490">Este servicio realiza una operación de anulación de registro en un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-490">This service performs a 'De-Register' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-491">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-491">Parameters</span></span>

- <span data-ttu-id="e4d69-492">**session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-492">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-493">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-493">Return Values</span></span>

- <span data-ttu-id="e4d69-494">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-494">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-495">**NX_LWM2M_NOT_REGISTERED**: El cliente no está registrado en el servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-495">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="e4d69-496">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-496">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="e4d69-497">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="e4d69-497">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="e4d69-498">Obtención del último error de una sesión</span><span class="sxs-lookup"><span data-stu-id="e4d69-498">Get last error of a session</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-499">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-499">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-500">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-500">Description</span></span>

<span data-ttu-id="e4d69-501">Este servicio devuelve el código de error de la sesión cuando la sesión se encuentra en estado de error.</span><span class="sxs-lookup"><span data-stu-id="e4d69-501">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-502">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-502">Parameters</span></span>

- <span data-ttu-id="e4d69-503">**session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-503">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-504">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-504">Return Values</span></span>

- <span data-ttu-id="e4d69-505">**NX_SUCCESS**: La sesión no está en estado de error.</span><span class="sxs-lookup"><span data-stu-id="e4d69-505">**NX_SUCCESS**: The session is not in error state.</span></span>
- <span data-ttu-id="e4d69-506">**NX_LWM2M_ADDRESS_ERROR**: Dirección de servidor no válida.</span><span class="sxs-lookup"><span data-stu-id="e4d69-506">**NX_LWM2M_ADDRESS_ERROR**: Invalid server address.</span></span>
- <span data-ttu-id="e4d69-507">**NX_LWM2M_BUFFER_TOO_SMALL**: la carga de la solicitud no cabe en el búfer de red.</span><span class="sxs-lookup"><span data-stu-id="e4d69-507">**NX_LWM2M_BUFFER_TOO_SMALL**: Payload of request doesn't fit in network buffer.</span></span>
- <span data-ttu-id="e4d69-508">**NX_LWM2M_DTLS_ERROR**: No se pudo establecer una conexión segura con el servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-508">**NX_LWM2M_DTLS_ERROR**: Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="e4d69-509">**NX_LWM2M_ERROR**: Error no especificado.</span><span class="sxs-lookup"><span data-stu-id="e4d69-509">**NX_LWM2M_ERROR**: Unspecified error.</span></span>
- <span data-ttu-id="e4d69-510">**NX_LWM2M_FORBIDDEN**: Registro rechazado por el servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-510">**NX_LWM2M_FORBIDDEN**: Registration refused by server.</span></span>
- <span data-ttu-id="e4d69-511">**NX_LWM2M_NOT_FOUND**: El servidor no encontró al cliente al actualizar/eliminar el registro.</span><span class="sxs-lookup"><span data-stu-id="e4d69-511">**NX_LWM2M_NOT_FOUND**: Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="e4d69-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: Se ha eliminado la instancia de objeto de servidor correspondiente a la sesión.</span><span class="sxs-lookup"><span data-stu-id="e4d69-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="e4d69-513">**NX_LWM2M_TIMED_OUT**: No hay respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-513">**NX_LWM2M_TIMED_OUT**: No answer from server.</span></span>
- <span data-ttu-id="e4d69-514">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-514">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="e4d69-515">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="e4d69-515">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="e4d69-516">Inicio de una sesión con un servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-516">Start a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-517">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-517">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="e4d69-518">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-518">Description</span></span>

<span data-ttu-id="e4d69-519">Este servicio realiza una operación de registro en un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-519">This service performs a 'Register' operation to a LWM2M Server.</span></span> <span data-ttu-id="e4d69-520">El servidor debe tener una instancia de servidor correspondiente en el objeto de servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-520">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="e4d69-521">Si el registro se realiza correctamente, el cliente de LWM2M procesará más operaciones desde el servidor y enviará periódicamente mensajes de actualización hasta que se elimine el registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-521">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="e4d69-522">Esta llamada anula cualquier sesión activa actual y se reemplaza por la nueva sesión del servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-522">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-523">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-523">Parameters</span></span>

- <span data-ttu-id="e4d69-524">**session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-524">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="e4d69-525">**server_id**: Id. de servidor corto del servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-525">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="e4d69-526">**ip_address**: Dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-526">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="e4d69-527">**port**: Puerto UDP del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-527">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-528">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-528">Return Values</span></span>

- <span data-ttu-id="e4d69-529">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-529">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="e4d69-530">**NX_LWM2M_NOT_FOUND**: No hay ninguna instancia de objeto de servidor correspondiente al id. de servidor corto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-530">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="e4d69-531">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-531">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="e4d69-532">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="e4d69-532">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="e4d69-533">Inicio de una sesión segura con un servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-533">Start a secure session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-534">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-534">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="e4d69-535">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-535">Description</span></span>

<span data-ttu-id="e4d69-536">Este servicio realiza una operación de registro en un servidor LWM2M mediante una conexión DTLS segura.</span><span class="sxs-lookup"><span data-stu-id="e4d69-536">This service performs a 'Register' operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="e4d69-537">El servidor debe tener una instancia de servidor correspondiente en el objeto de servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-537">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="e4d69-538">La sesión DTLS se debe haber configurado con los conjuntos de cifrado y el material de clave adecuados antes de llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="e4d69-538">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="e4d69-539">NX_SECURE_ENABLE_DTLS debe definirse.</span><span class="sxs-lookup"><span data-stu-id="e4d69-539">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="e4d69-540">Cada sesión DTLS usa su propio socket UDP para la comunicación, por lo que el puerto local dtls_local_port debe ser diferente para cada sesión si la aplicación crea varias sesiones seguras.</span><span class="sxs-lookup"><span data-stu-id="e4d69-540">Each DTLS session uses its own UDP socket for communication, so the local port dtls_local_port must be different for each session if the application creates several secure sessions.</span></span>

<span data-ttu-id="e4d69-541">Si el registro se realiza correctamente, el cliente de LWM2M procesará más operaciones desde el servidor y enviará periódicamente mensajes de actualización hasta que se elimine el registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-541">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="e4d69-542">Esta llamada anula cualquier sesión activa actual y se reemplaza por la nueva sesión del servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-542">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-543">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-543">Parameters</span></span>

- <span data-ttu-id="e4d69-544">**session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-544">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="e4d69-545">**server_id**: Id. de servidor corto del servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-545">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="e4d69-546">**ip_address**: Dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-546">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="e4d69-547">**port**: Puerto UDP del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-547">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="e4d69-548">**dtls_session_ptr**: Sesión DTLS que se va a usar para la sesión de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-548">**dtls_session_ptr**: The DTLS session to use for the LWM2M session.</span></span>
- <span data-ttu-id="e4d69-549">**dtls_local_port**: Puerto UDP local usado para la sesión DTLS.</span><span class="sxs-lookup"><span data-stu-id="e4d69-549">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-550">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-550">Return Values</span></span>

- <span data-ttu-id="e4d69-551">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-551">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-552">**NX_LWM2M_NOT_FOUND**: No hay ninguna instancia de objeto de servidor correspondiente al id. de servidor corto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-552">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="e4d69-553">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-553">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="e4d69-554">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="e4d69-554">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="e4d69-555">Actualización de una sesión con un servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-555">Update a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-556">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-557">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-557">Description</span></span>

<span data-ttu-id="e4d69-558">Este servicio realiza una operación de actualización en un servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-558">This service performs an 'Update' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-559">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-559">Parameters</span></span>

- <span data-ttu-id="e4d69-560">**session_ptr**: Puntero al bloque de control de sesión de cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-560">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-561">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-561">Return Values</span></span>

- <span data-ttu-id="e4d69-562">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-562">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-563">**NX_LWM2M_NOT_REGISTERED**: El cliente no está registrado en el servidor.</span><span class="sxs-lookup"><span data-stu-id="e4d69-563">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="e4d69-564">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-564">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="e4d69-565">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="e4d69-565">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="e4d69-566">Desbloqueo del cliente de LWM2M</span><span class="sxs-lookup"><span data-stu-id="e4d69-566">Unlock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-567">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-567">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-568">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-568">Description</span></span>

<span data-ttu-id="e4d69-569">Este servicio desbloquea al cliente de LWM2M previamente bloqueado por una llamada a nx_lwm2m_client_unlock().</span><span class="sxs-lookup"><span data-stu-id="e4d69-569">This service unlocks the LWM2M Client previoulsy locked by a call to nx_lwm2m_client_unlock().</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-570">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-570">Parameters</span></span>

- <span data-ttu-id="e4d69-571">**client_ptr**: Puntero al bloque de control del cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="e4d69-571">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-572">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-572">Return Values</span></span>

- <span data-ttu-id="e4d69-573">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-573">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-574">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-574">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_create"></a><span data-ttu-id="e4d69-575">nx_lwm2m_firmware_create</span><span class="sxs-lookup"><span data-stu-id="e4d69-575">nx_lwm2m_firmware_create</span></span>

<span data-ttu-id="e4d69-576">Creación de un objeto de actualización de firmware</span><span class="sxs-lookup"><span data-stu-id="e4d69-576">Create Firmware Update Object</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-577">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-577">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="e4d69-578">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-578">Description</span></span>

<span data-ttu-id="e4d69-579">Este servicio inicializa un objeto de actualización de firmware y agrega el objeto a un cliente de LWM2M creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-579">This service initializes a Firmware Update Object and adds the Object to a previously created LWM2M Client.</span></span> <span data-ttu-id="e4d69-580">El objeto de actualización de firmware implementa los recursos para comunicarse con un servidor LWM2M, pero la aplicación debe proporcionar devoluciones de llamada para implementar las operaciones reales en el firmware (descarga, almacenamiento y actualización de firmware).</span><span class="sxs-lookup"><span data-stu-id="e4d69-580">The Firmware Update Object implements the resources for communicating with a LWM2M Server but the application must provide callbacks for implementing the actual operations on the firmware (dowloading, storing, and updating the firmware).</span></span>

<span data-ttu-id="e4d69-581">El parámetro protocols indica qué protocolos son compatibles con la aplicación para recuperar el firmware con el recurso "Package URI"; se definen las marcas siguientes:</span><span class="sxs-lookup"><span data-stu-id="e4d69-581">The protocols parameter indicates which protocols are supported by the application for retrieving the firmware with the 'Package URI' resource, the following flags are defined:</span></span>

<span data-ttu-id="e4d69-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span><span class="sxs-lookup"><span data-stu-id="e4d69-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-583">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-583">Parameters</span></span>

- <span data-ttu-id="e4d69-584">**firmware_ptr**: Puntero al bloque de control del objeto de firmware.</span><span class="sxs-lookup"><span data-stu-id="e4d69-584">**firmware_ptr**: Pointer to the Firmware Object control block.</span></span>
- <span data-ttu-id="e4d69-585">**client_ptr**: Puntero al cliente de LWM2M creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e4d69-585">**client_ptr**: Pointer to previsously created LWM2M Client.</span></span>
- <span data-ttu-id="e4d69-586">**protocolos**: Marcas que indican qué protocolos admite el recurso URI del paquete.</span><span class="sxs-lookup"><span data-stu-id="e4d69-586">**protocols**: Flags indicating which protocols are supported by the Package URI resource.</span></span>
- <span data-ttu-id="e4d69-587">**package_callback**: Debe ser NULL [por determinar].</span><span class="sxs-lookup"><span data-stu-id="e4d69-587">**package_callback**: Must be NULL [TBD].</span></span>
- <span data-ttu-id="e4d69-588">**package_uri_callback**: Devolución de llamada usada para implementar el recurso URI del paquete.</span><span class="sxs-lookup"><span data-stu-id="e4d69-588">**package_uri_callback**: Callback used to implement the Package URI resource.</span></span>
- <span data-ttu-id="e4d69-589">**update_callback**: Devolución de llamada usada para implementar el recurso de Actualización.</span><span class="sxs-lookup"><span data-stu-id="e4d69-589">**update_callback**: Callback used to implement the Update resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-590">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-590">Return Values</span></span>

- <span data-ttu-id="e4d69-591">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-591">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-592">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-592">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_package_info_set"></a><span data-ttu-id="e4d69-593">nx_lwm2m_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="e4d69-593">nx_lwm2m_firmware_package_info_set</span></span>

<span data-ttu-id="e4d69-594">Definición de información de paquete de actualización de firmware</span><span class="sxs-lookup"><span data-stu-id="e4d69-594">Set Firmware Update Package Information</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-595">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-595">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a><span data-ttu-id="e4d69-596">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-596">Description</span></span>

<span data-ttu-id="e4d69-597">Este servicio cambia los valores de los recursos "PkgName" (6) y "PkgVersion" (7) del objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="e4d69-597">This service changes the values of the 'PkgName' (6) and 'PkgVersion' (7) resources of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-598">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-598">Parameters</span></span>

- <span data-ttu-id="e4d69-599">**firmware_ptr**: Puntero al objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="e4d69-599">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="e4d69-600">**name**: Nuevo valor del Nombre del paquete.</span><span class="sxs-lookup"><span data-stu-id="e4d69-600">**name**: The new value of the Package Name.</span></span>
- <span data-ttu-id="e4d69-601">**versión**: Nuevo valor de la Versión del paquete.</span><span class="sxs-lookup"><span data-stu-id="e4d69-601">**version**: The new value of the Package Version.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-602">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-602">Return Values</span></span>

- <span data-ttu-id="e4d69-603">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-603">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-604">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-604">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_result_set"></a><span data-ttu-id="e4d69-605">nx_lwm2m_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="e4d69-605">nx_lwm2m_firmware_result_set</span></span>

<span data-ttu-id="e4d69-606">Definición del resultado de la actualización de firmware</span><span class="sxs-lookup"><span data-stu-id="e4d69-606">Set Firmware Update Result</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-607">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-607">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a><span data-ttu-id="e4d69-608">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-608">Description</span></span>

<span data-ttu-id="e4d69-609">Este servicio cambia el valor del recurso "Update result" (5) del objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="e4d69-609">This service changes the value of the 'Update Result' (5) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-610">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-610">Parameters</span></span>

- <span data-ttu-id="e4d69-611">**firmware_ptr**: Puntero al objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="e4d69-611">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="e4d69-612">**result**: El nuevo valor del recurso de Resultado de actualización.</span><span class="sxs-lookup"><span data-stu-id="e4d69-612">**result**: The new value of the Update Result resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-613">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-613">Return Values</span></span>

- <span data-ttu-id="e4d69-614">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-614">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-615">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-615">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_state_set"></a><span data-ttu-id="e4d69-616">nx_lwm2m_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="e4d69-616">nx_lwm2m_firmware_state_set</span></span>

<span data-ttu-id="e4d69-617">Definición del estado de actualización del firmware</span><span class="sxs-lookup"><span data-stu-id="e4d69-617">Set Firmware Update State</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-618">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-618">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a><span data-ttu-id="e4d69-619">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-619">Description</span></span>

<span data-ttu-id="e4d69-620">Este servicio cambia el valor del recurso "State" (3) del objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="e4d69-620">This service changes the value of the 'State' (3) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-621">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-621">Parameters</span></span>

- <span data-ttu-id="e4d69-622">**firmware_ptr**: Puntero al objeto de actualización de firmware.</span><span class="sxs-lookup"><span data-stu-id="e4d69-622">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="e4d69-623">**state**: Nuevo valor del recurso de Estado.</span><span class="sxs-lookup"><span data-stu-id="e4d69-623">**state**: The new value of the State resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-624">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-624">Return Values</span></span>

- <span data-ttu-id="e4d69-625">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-625">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-626">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-626">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_object_resource_changed"></a><span data-ttu-id="e4d69-627">nx_lwm2m_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="e4d69-627">nx_lwm2m_object_resource_changed</span></span>

<span data-ttu-id="e4d69-628">Modificación de señal de un valor de recurso de una instancia de objeto</span><span class="sxs-lookup"><span data-stu-id="e4d69-628">Signal change of a resource value of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-629">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-629">Prototype</span></span>

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="e4d69-630">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-630">Description</span></span>

<span data-ttu-id="e4d69-631">La implementación de un objeto usa este servicio para indicar al cliente de LWM2M que uno de sus valores de recurso ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="e4d69-631">This service is used by an Object implementation to signals the LWM2M Client that one of its resource value has changed.</span></span> <span data-ttu-id="e4d69-632">El cliente de LWM2M enviará una notificación si un servidor LWM2M observa el recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-632">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-633">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-633">Parameters</span></span>

- <span data-ttu-id="e4d69-634">**object_ptr**: Puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-634">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="e4d69-635">**instance_ptr**: Puntero a la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-635">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="e4d69-636">**resource**: Puntero a la estructura que describe el recurso que ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="e4d69-636">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-637">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-637">Return Values</span></span>

- <span data-ttu-id="e4d69-638">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-638">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-639">NX_PTR_ERROR: Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="e4d69-639">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_resource_get_boolean"></a><span data-ttu-id="e4d69-640">nx_lwm2m_resource_get_boolean</span><span class="sxs-lookup"><span data-stu-id="e4d69-640">nx_lwm2m_resource_get_boolean</span></span>

<span data-ttu-id="e4d69-641">Obtención del valor de un recurso booleano</span><span class="sxs-lookup"><span data-stu-id="e4d69-641">Get the value of a Boolean Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-642">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-642">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-643">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-643">Description</span></span>

<span data-ttu-id="e4d69-644">Este servicio recupera el valor de un recurso booleano.</span><span class="sxs-lookup"><span data-stu-id="e4d69-644">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-645">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-645">Parameters</span></span>

- <span data-ttu-id="e4d69-646">**value**: Puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-646">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="e4d69-647">**bool_ptr**: Puntero al valor booleano de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-647">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-648">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-648">Return Values</span></span>

- <span data-ttu-id="e4d69-649">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-649">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-650">**NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor booleano.</span><span class="sxs-lookup"><span data-stu-id="e4d69-650">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_get_float32"></a><span data-ttu-id="e4d69-651">nx_lwm2m_resource_get_float32</span><span class="sxs-lookup"><span data-stu-id="e4d69-651">nx_lwm2m_resource_get_float32</span></span>

<span data-ttu-id="e4d69-652">Obtención del valor de un recurso de punto flotante de 32 bits</span><span class="sxs-lookup"><span data-stu-id="e4d69-652">Get the value of a 32-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-653">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-653">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-654">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-654">Description</span></span>

<span data-ttu-id="e4d69-655">Este servicio recupera el valor de un recurso de punto flotante de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e4d69-655">The service retrieves the value of a 32-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-656">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-656">Parameters</span></span>

- <span data-ttu-id="e4d69-657">**value**: Puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-657">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="e4d69-658">**float32_ptr**: Puntero al valor de punto flotante de 32 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-658">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-659">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-659">Return Values</span></span>

- <span data-ttu-id="e4d69-660">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-660">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-661">**NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor de punto flotante.</span><span class="sxs-lookup"><span data-stu-id="e4d69-661">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_float64"></a><span data-ttu-id="e4d69-662">nx_lwm2m_resource_get_float64</span><span class="sxs-lookup"><span data-stu-id="e4d69-662">nx_lwm2m_resource_get_float64</span></span>

<span data-ttu-id="e4d69-663">Obtención del valor de un recurso de punto flotante de 64 bits</span><span class="sxs-lookup"><span data-stu-id="e4d69-663">Get the value of a 64-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-664">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-664">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-665">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-665">Description</span></span>

<span data-ttu-id="e4d69-666">Este servicio recupera el valor de un recurso de punto flotante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e4d69-666">The service retrieves the value of a 64-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-667">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-667">Parameters</span></span>

- <span data-ttu-id="e4d69-668">**value**: Puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-668">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="e4d69-669">**float64_ptr**: Puntero al valor de punto flotante de 64 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-669">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-670">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-670">Return Values</span></span>

- <span data-ttu-id="e4d69-671">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-671">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-672">**NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor de punto flotante.</span><span class="sxs-lookup"><span data-stu-id="e4d69-672">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_integer32"></a><span data-ttu-id="e4d69-673">nx_lwm2m_resource_get_integer32</span><span class="sxs-lookup"><span data-stu-id="e4d69-673">nx_lwm2m_resource_get_integer32</span></span>

<span data-ttu-id="e4d69-674">Obtención del valor de un recurso entero de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e4d69-674">Get the value of a 32-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-675">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-675">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-676">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-676">Description</span></span>

<span data-ttu-id="e4d69-677">Este servicio recupera el valor de un recurso entero de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e4d69-677">The service retrieves the value of a 32-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-678">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-678">Parameters</span></span>

- <span data-ttu-id="e4d69-679">**value**: Puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-679">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="e4d69-680">**int32_ptr**: Puntero al valor Entero de 32 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-680">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-681">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-681">Return Values</span></span>

- <span data-ttu-id="e4d69-682">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-682">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-683">**NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor Entero o el valor Entero no cabe en un número de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e4d69-683">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_get_integer64"></a><span data-ttu-id="e4d69-684">nx_lwm2m_resource_get_integer64</span><span class="sxs-lookup"><span data-stu-id="e4d69-684">nx_lwm2m_resource_get_integer64</span></span>

<span data-ttu-id="e4d69-685">Obtención del valor de un recurso entero de 64 bits</span><span class="sxs-lookup"><span data-stu-id="e4d69-685">Get the value of a 64-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-686">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-686">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-687">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-687">Description</span></span>

<span data-ttu-id="e4d69-688">Este servicio recupera el valor de un recurso entero de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e4d69-688">The service retrieves the value of a 64-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-689">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-689">Parameters</span></span>

- <span data-ttu-id="e4d69-690">**value**: Puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-690">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="e4d69-691">**int64_ptr**: Puntero al valor Entero de 64 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-691">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-692">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-692">Return Values</span></span>

- <span data-ttu-id="e4d69-693">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-693">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-694">**NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor Entero.</span><span class="sxs-lookup"><span data-stu-id="e4d69-694">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_get_objlnk"></a><span data-ttu-id="e4d69-695">nx_lwm2m_resource_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="e4d69-695">nx_lwm2m_resource_get_objlnk</span></span>

<span data-ttu-id="e4d69-696">Obtención del valor de un recurso de vínculo de objeto</span><span class="sxs-lookup"><span data-stu-id="e4d69-696">Get the value of an Object Link Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-697">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-697">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-698">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-698">Description</span></span>

<span data-ttu-id="e4d69-699">Este servicio recupera el valor de un recurso de vínculo de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-699">The service retrieves the value of an Object Link Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-700">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-700">Parameters</span></span>

- <span data-ttu-id="e4d69-701">**value**: Puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-701">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="e4d69-702">**objlnk_ptr**: Puntero al valor de Vínculo del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-702">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-703">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-703">Return Values</span></span>

- <span data-ttu-id="e4d69-704">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-704">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-705">**NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor de Vínculo de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-705">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_get_opaque"></a><span data-ttu-id="e4d69-706">nx_lwm2m_resource_get_opaque</span><span class="sxs-lookup"><span data-stu-id="e4d69-706">nx_lwm2m_resource_get_opaque</span></span>

<span data-ttu-id="e4d69-707">Obtención del valor de un recurso opaco</span><span class="sxs-lookup"><span data-stu-id="e4d69-707">Get the value of an Opaque Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-708">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-708">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-709">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-709">Description</span></span>

<span data-ttu-id="e4d69-710">Este servicio recupera el valor de un recurso opaco.</span><span class="sxs-lookup"><span data-stu-id="e4d69-710">The service retrieves the value of an Opaque Resource.</span></span>

<span data-ttu-id="e4d69-711">Un valor de recurso opaco está formado por un puntero a un búfer y una longitud.</span><span class="sxs-lookup"><span data-stu-id="e4d69-711">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-712">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-712">Parameters</span></span>

- <span data-ttu-id="e4d69-713">**value**: Puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-713">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="e4d69-714">**opaque_ptr_ptr**: Puntero al puntero de búfer opaco de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-714">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="e4d69-715">**opaque_length_ptr**: Puntero a la longitud de búfer opaco de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-715">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-716">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-716">Return Values</span></span>

- <span data-ttu-id="e4d69-717">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-717">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-718">**NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor Opaco.</span><span class="sxs-lookup"><span data-stu-id="e4d69-718">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_get_string"></a><span data-ttu-id="e4d69-719">nx_lwm2m_resource_get_string</span><span class="sxs-lookup"><span data-stu-id="e4d69-719">nx_lwm2m_resource_get_string</span></span>

<span data-ttu-id="e4d69-720">Obtención del valor de un recurso de cadena</span><span class="sxs-lookup"><span data-stu-id="e4d69-720">Get the value of a String Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-721">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-721">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-722">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-722">Description</span></span>

<span data-ttu-id="e4d69-723">Este servicio recupera el valor de un recurso de cadena.</span><span class="sxs-lookup"><span data-stu-id="e4d69-723">The service retrieves the value of a String Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-724">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-724">Parameters</span></span>

- <span data-ttu-id="e4d69-725">**value**: Puntero a la descripción del valor de recurso.</span><span class="sxs-lookup"><span data-stu-id="e4d69-725">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="e4d69-726">**string_ptr_ptr**: Puntero al puntero de la cadena de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-726">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="e4d69-727">**string_length_ptr**: Puntero a la longitud de la cadena de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-727">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="e4d69-728">Puede ser NULL si la cadena termina en cero.</span><span class="sxs-lookup"><span data-stu-id="e4d69-728">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-729">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-729">Return Values</span></span>

- <span data-ttu-id="e4d69-730">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-730">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-731">**NX_LWM2M_BAD_ENCODING**: El valor del recurso no es un valor de Cadena.</span><span class="sxs-lookup"><span data-stu-id="e4d69-731">**NX_LWM2M_BAD_ENCODING**: The resource value is not a String value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a><span data-ttu-id="e4d69-732">nx_lwm2m_resource_multiple_get_boolean</span><span class="sxs-lookup"><span data-stu-id="e4d69-732">nx_lwm2m_resource_multiple_get_boolean</span></span>

<span data-ttu-id="e4d69-733">Obtención del valor de una instancia de recurso booleano en un recurso múltiple</span><span class="sxs-lookup"><span data-stu-id="e4d69-733">Get the value of a Boolean Resource Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-734">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-734">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-735">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-735">Description</span></span>

<span data-ttu-id="e4d69-736">Este servicio recupera el valor de una instancia de recurso booleano de un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-736">The service retrieves the value of a Boolean Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-737">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-737">Parameters</span></span>

- <span data-ttu-id="e4d69-738">**value**: Puntero a la descripción del valor de recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-738">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="e4d69-739">**index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-739">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="e4d69-740">**instance_id_ptr**: Puntero al id. de instancia de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-740">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="e4d69-741">**bool_ptr**: Puntero al valor booleano de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-741">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-742">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-742">Return Values</span></span>

- <span data-ttu-id="e4d69-743">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-743">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-744">**NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.</span><span class="sxs-lookup"><span data-stu-id="e4d69-744">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="e4d69-745">**NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor booleano.</span><span class="sxs-lookup"><span data-stu-id="e4d69-745">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float32"></a><span data-ttu-id="e4d69-746">nx_lwm2m_resource_multiple_get_float32</span><span class="sxs-lookup"><span data-stu-id="e4d69-746">nx_lwm2m_resource_multiple_get_float32</span></span>

<span data-ttu-id="e4d69-747">Obtención del valor de una instancia de recurso de punto flotante de 32 bits en un recurso múltiple</span><span class="sxs-lookup"><span data-stu-id="e4d69-747">Get the value of a 32-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-748">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-748">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-749">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-749">Description</span></span>

<span data-ttu-id="e4d69-750">Este servicio recupera el valor de una instancia de recurso de punto flotante de 32 bits de un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-750">The service retrieves the value of a 32-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-751">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-751">Parameters</span></span>

- <span data-ttu-id="e4d69-752">**value**: Puntero a la descripción del valor de recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-752">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="e4d69-753">**index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-753">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="e4d69-754">**instance_id_ptr**: Puntero al id. de instancia de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-754">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="e4d69-755">**float32_ptr**: Puntero al valor de punto flotante de 32 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-755">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-756">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-756">Return Values</span></span>

- <span data-ttu-id="e4d69-757">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-757">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-758">**NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.</span><span class="sxs-lookup"><span data-stu-id="e4d69-758">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="e4d69-759">**NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor de punto flotante.</span><span class="sxs-lookup"><span data-stu-id="e4d69-759">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float64"></a><span data-ttu-id="e4d69-760">nx_lwm2m_resource_multiple_get_float64</span><span class="sxs-lookup"><span data-stu-id="e4d69-760">nx_lwm2m_resource_multiple_get_float64</span></span>

<span data-ttu-id="e4d69-761">Obtención del valor de una instancia de recurso de punto flotante de 64 bits de un recurso múltiple</span><span class="sxs-lookup"><span data-stu-id="e4d69-761">Get the value of a 64-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-762">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-762">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-763">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-763">Description</span></span>

<span data-ttu-id="e4d69-764">Este servicio recupera el valor de una instancia de recurso de punto flotante de 64 bits de un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-764">The service retrieves the value of a 64-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-765">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-765">Parameters</span></span>

- <span data-ttu-id="e4d69-766">**value**: Puntero a la descripción del valor de recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-766">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="e4d69-767">**index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-767">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="e4d69-768">**instance_id_ptr**: Puntero al id. de instancia de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-768">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="e4d69-769">**float64_ptr**: Puntero al valor de punto flotante de 64 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-769">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-770">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-770">Return Values</span></span>

- <span data-ttu-id="e4d69-771">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-771">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-772">**NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.</span><span class="sxs-lookup"><span data-stu-id="e4d69-772">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="e4d69-773">**NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor de punto flotante.</span><span class="sxs-lookup"><span data-stu-id="e4d69-773">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a><span data-ttu-id="e4d69-774">nx_lwm2m_resource_multiple_get_integer32</span><span class="sxs-lookup"><span data-stu-id="e4d69-774">nx_lwm2m_resource_multiple_get_integer32</span></span>

<span data-ttu-id="e4d69-775">Obtención del valor de una instancia de recurso entero de 32 bits de un recurso múltiple</span><span class="sxs-lookup"><span data-stu-id="e4d69-775">Get the value of a 32-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-776">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-776">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-777">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-777">Description</span></span>

<span data-ttu-id="e4d69-778">Este servicio recupera el valor de una instancia de recurso entero de 32 bits de un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-778">The service retrieves the value of a 32-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-779">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-779">Parameters</span></span>

- <span data-ttu-id="e4d69-780">**value**: Puntero a la descripción del valor de recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-780">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="e4d69-781">**index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-781">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="e4d69-782">**instance_id_ptr**: Puntero al id. de instancia de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-782">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="e4d69-783">**int32_ptr**: Puntero al valor Entero de 32 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-783">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-784">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-784">Return Values</span></span>

- <span data-ttu-id="e4d69-785">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-785">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-786">**NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.</span><span class="sxs-lookup"><span data-stu-id="e4d69-786">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="e4d69-787">**NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor entero o el valor entero no cabe en un número de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e4d69-787">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a><span data-ttu-id="e4d69-788">nx_lwm2m_resource_multiple_get_integer64</span><span class="sxs-lookup"><span data-stu-id="e4d69-788">nx_lwm2m_resource_multiple_get_integer64</span></span>

<span data-ttu-id="e4d69-789">Obtención del valor de una instancia de recurso entero de 64 bits de un recurso múltiple</span><span class="sxs-lookup"><span data-stu-id="e4d69-789">Get the value of a 64-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-790">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-790">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-791">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-791">Description</span></span>

<span data-ttu-id="e4d69-792">Este servicio recupera el valor de una instancia de recurso entero de 64 bits de un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-792">The service retrieves the value of a 64-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-793">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-793">Parameters</span></span>

- <span data-ttu-id="e4d69-794">**value**: Puntero a la descripción del valor de recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-794">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="e4d69-795">**index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-795">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="e4d69-796">**instance_id_ptr**: Puntero al id. de instancia de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-796">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="e4d69-797">**int64_ptr**: Puntero al valor Entero de 64 bits de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-797">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-798">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-798">Return Values</span></span>

- <span data-ttu-id="e4d69-799">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-799">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-800">**NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.</span><span class="sxs-lookup"><span data-stu-id="e4d69-800">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="e4d69-801">**NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor Entero.</span><span class="sxs-lookup"><span data-stu-id="e4d69-801">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a><span data-ttu-id="e4d69-802">nx_lwm2m_resource_multiple_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="e4d69-802">nx_lwm2m_resource_multiple_get_objlnk</span></span>

<span data-ttu-id="e4d69-803">Obtención del valor de una instancia de recurso de enlace de objeto de un recurso múltiple</span><span class="sxs-lookup"><span data-stu-id="e4d69-803">Get the value of an Object Link Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-804">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-804">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-805">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-805">Description</span></span>

<span data-ttu-id="e4d69-806">Este servicio recupera el valor de una instancia de recurso de enlace de objeto de un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-806">The service retrieves the value of an Object Link Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-807">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-807">Parameters</span></span>

- <span data-ttu-id="e4d69-808">**value**: Puntero a la descripción del valor de recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-808">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="e4d69-809">**index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-809">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="e4d69-810">**instance_id_ptr**: Puntero al id. de instancia de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-810">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="e4d69-811">**objlnk_ptr**: Puntero al valor de Vínculo del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-811">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-812">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-812">Return Values</span></span>

- <span data-ttu-id="e4d69-813">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-813">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-814">**NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.</span><span class="sxs-lookup"><span data-stu-id="e4d69-814">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="e4d69-815">**NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor de vínculo de objeto.</span><span class="sxs-lookup"><span data-stu-id="e4d69-815">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a><span data-ttu-id="e4d69-816">nx_lwm2m_resource_multiple_get_opaque</span><span class="sxs-lookup"><span data-stu-id="e4d69-816">nx_lwm2m_resource_multiple_get_opaque</span></span>

<span data-ttu-id="e4d69-817">Obtención del valor de una instancia de recurso opaco de un recurso múltiple</span><span class="sxs-lookup"><span data-stu-id="e4d69-817">Get the value of an Opaque Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-818">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-818">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-819">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-819">Description</span></span>

<span data-ttu-id="e4d69-820">Este servicio recupera el valor de una instancia de recurso opaco de un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-820">The service retrieves the value of an Opaque Resource Instance from a Multiple Resource.</span></span>

<span data-ttu-id="e4d69-821">Un valor de recurso opaco está formado por un puntero a un búfer y una longitud.</span><span class="sxs-lookup"><span data-stu-id="e4d69-821">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-822">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-822">Parameters</span></span>

- <span data-ttu-id="e4d69-823">**value**: Puntero a la descripción del valor de recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-823">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="e4d69-824">**index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-824">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="e4d69-825">**instance_id_ptr**: Puntero al id. de instancia de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-825">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="e4d69-826">**opaque_ptr_ptr**: Puntero al puntero de búfer opaco de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-826">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="e4d69-827">**opaque_length_ptr**: Puntero a la longitud de búfer opaco de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-827">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-828">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-828">Return Values</span></span>

- <span data-ttu-id="e4d69-829">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-829">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-830">**NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.</span><span class="sxs-lookup"><span data-stu-id="e4d69-830">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="e4d69-831">**NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor del recurso no es un valor Opaco.</span><span class="sxs-lookup"><span data-stu-id="e4d69-831">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_string"></a><span data-ttu-id="e4d69-832">nx_lwm2m_resource_multiple_get_string</span><span class="sxs-lookup"><span data-stu-id="e4d69-832">nx_lwm2m_resource_multiple_get_string</span></span>

<span data-ttu-id="e4d69-833">Obtención del valor de una instancia de cadena de un recurso múltiple</span><span class="sxs-lookup"><span data-stu-id="e4d69-833">Get the value of a String Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e4d69-834">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e4d69-834">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="e4d69-835">Descripción</span><span class="sxs-lookup"><span data-stu-id="e4d69-835">Description</span></span>

<span data-ttu-id="e4d69-836">Este servicio recupera el valor de una instancia de recurso de cadena de un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-836">The service retrieves the value of a String Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="e4d69-837">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e4d69-837">Parameters</span></span>

- <span data-ttu-id="e4d69-838">**value**: Puntero a la descripción del valor de recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="e4d69-838">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="e4d69-839">**index**: Índice de la instancia que se va a recuperar en la matriz de valores de recursos.</span><span class="sxs-lookup"><span data-stu-id="e4d69-839">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="e4d69-840">**instance_id_ptr**: Puntero al id. de instancia de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-840">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="e4d69-841">**string_ptr_ptr**: Puntero al puntero de la cadena de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-841">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="e4d69-842">**string_length_ptr**: Puntero a la longitud de la cadena de destino.</span><span class="sxs-lookup"><span data-stu-id="e4d69-842">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="e4d69-843">Puede ser NULL si la cadena termina en cero.</span><span class="sxs-lookup"><span data-stu-id="e4d69-843">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="e4d69-844">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e4d69-844">Return Values</span></span>

- <span data-ttu-id="e4d69-845">**NX_SUCCESS**: Operación correcta.</span><span class="sxs-lookup"><span data-stu-id="e4d69-845">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="e4d69-846">**NX_LWM2M_BAD_PARAMETER**: El índice está fuera de rango.</span><span class="sxs-lookup"><span data-stu-id="e4d69-846">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="e4d69-847">**NX_LWM2M_BAD_ENCODING**: El recurso no es un recurso múltiple o el valor de instancia no es un valor de cadena.</span><span class="sxs-lookup"><span data-stu-id="e4d69-847">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the instance value is not a String value.</span></span>
