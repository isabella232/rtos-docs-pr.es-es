---
title: 'Capítulo 3: Descripción de los servicios del cliente DHCP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del cliente DHCP de Azure RTOS NetX Duo incluidos a continuación por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f143a443221ae08848316a458a630a0790108198
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814798"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="0bc4c-103">Capítulo 3: Descripción de los servicios del cliente DHCP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="0bc4c-104">Este capítulo contiene una descripción de todos los servicios del cliente DHCP de Azure RTOS NetX Duo incluidos a continuación por orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-104">This chapter contains a description of all Azure RTOS NetX Duo DHCP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="0bc4c-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0bc4c-106">**nx_dhcp_create**: *crea una instancia de DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>
- <span data-ttu-id="0bc4c-107">**nx_dhcp_clear_broadcast_flag**: *borra la marca de difusión en mensajes de cliente*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-107">**nx_dhcp_clear_broadcast_flag**: *Clear broadcast flag on Client messages*</span></span>
- <span data-ttu-id="0bc4c-108">**nx_dhcp_delete**: *elimina una instancia de DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>
- <span data-ttu-id="0bc4c-109">**nx_dhcp_force_renew**: *envía un mensaje para forzar la renovación*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-109">**nx_dhcp_force_renew**: *Send a force renew message*</span></span>
- <span data-ttu-id="0bc4c-110">**nx_dhcp_packet_pool_set**: *establece el grupo de paquetes de cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-110">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>
- <span data-ttu-id="0bc4c-111">**nx_dhcp_decline**: envía un *mensaje DECLINE al servidor*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-111">**nx_dhcp_decline**: Send *Decline message to server*</span></span>
- <span data-ttu-id="0bc4c-112">**nx_dhcp_release**: envía un *mensaje de liberación al servidor*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-112">**nx_dhcp_release**: Send *Release message to server*</span></span>
- <span data-ttu-id="0bc4c-113">**nx_dhcp_reinitialize**: *borra los parámetros de red de cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>
- <span data-ttu-id="0bc4c-114">**nx_dhcp_request_client_ip**: *especifica una dirección IP concreta*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>
- <span data-ttu-id="0bc4c-115">**nx_dhcp_send_request**: *envía un mensaje DHCP al servidor*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>
- <span data-ttu-id="0bc4c-116">**nx_dhcp_start**: *inicia el procesamiento de cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-116">**nx_dhcp_start**: *Start the DHCP Client processing*</span></span>
- <span data-ttu-id="0bc4c-117">**nx_dhcp_stop**: *detiene el procesamiento de cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-117">**nx_dhcp_stop**: *Stop the DHCP Client processing*</span></span>
- <span data-ttu-id="0bc4c-118">**nx_dhcp_set_interface_index**: *establece la interfaz para ejecutar el cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-118">**nx_dhcp_set_interface_index**: *Set the interface to run DHCP Client*</span></span>
- <span data-ttu-id="0bc4c-119">**nx_dhcp_server_address_get**: *obtiene la dirección IP del servidor DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-119">**nx_dhcp_server_address_get**: *Get the DHCP server IP address*</span></span>
- <span data-ttu-id="0bc4c-120">**nx_dhcp_state_change_notify**: *establece la función de devolución de llamada cuando el estado de DHCP cambia*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-120">**nx_dhcp_state_change_notify**: *Set the callback function when DHCP state changes*</span></span>
- <span data-ttu-id="0bc4c-121">**nx_dhcp_user_option_retrieve**: *recupera la opción DHCP especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-121">**nx_dhcp_user_option_retrieve**: *Retrieve the specified DHCP option*</span></span>
- <span data-ttu-id="0bc4c-122">**nx_dhcp_user_option_convert**: *convierte cuatro bytes a ULONG*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="0bc4c-123">Servicios de cliente DHCP específicos de la interfaz:</span><span class="sxs-lookup"><span data-stu-id="0bc4c-123">Interface specific DHCP Client services:</span></span>
 
- <span data-ttu-id="0bc4c-124">**nx_dhcp_interface_clear_broadcast_flag**: *borra la marca de difusión en mensajes de cliente en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>
- <span data-ttu-id="0bc4c-125">**nx_dhcp_interface_enable**: *habilita la interfaz para ejecutar DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-126">**nx_dhcp_interface_disable**: *deshabilita la interfaz para ejecutar DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-127">**nx_dhcp_interface_decline**: *envía un mensaje DECLINE al servidor en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-128">**nx_dhcp_interface_force_renew**: *envía un mensaje para forzar la renovación en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-129">**nx_dhcp_interface_reinitialize**: *borra parámetros de red de cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-130">**nx_dhcp_interface_release**: *envía un mensaje de liberación al servidor en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-130">**nx_dhcp_interface_release**: *Send Release message to server on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-131">**nx_dhcp_interface_request_client_ip**: *especifica una dirección IP concreta en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-132">**nx_dhcp_interface_send_request**: *envía un mensaje DHCP al servidor en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-133">**nx_dhcp_interface_server_address_get**: *obtiene la dirección IP del servidor DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-134">**nx_dhcp_interface_start**: *inicia el procesamiento de cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-135">**nx_dhcp_interface_stop**: *detiene el procesamiento de cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-136">**nx_dhcp_interface_state_change_notify**: *establece la función de devolución de llamada cuando el estado de DHCP cambia en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-137">**nx_dhcp_interface_user_option_retrieve**: *recupera la opción DHCP especificada en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="0bc4c-138">Servicios de cliente DHCP si se define NX_DHCP_CLIENT_RESORE_STATE:</span><span class="sxs-lookup"><span data-stu-id="0bc4c-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="0bc4c-139">**nx_dhcp_resume**: *reanuda el estado del cliente DHCP previamente establecido*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>
- <span data-ttu-id="0bc4c-140">**nx_dhcp_suspend**: *suspende el procesamiento del estado del cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>
- <span data-ttu-id="0bc4c-141">**nx_dhcp_client_get_record**: *crea un registro del estado del cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>
- <span data-ttu-id="0bc4c-142">**nx_dhcp_client_restore_record**: *restaura un registro guardado previamente en el cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>
- <span data-ttu-id="0bc4c-143">**nx_dhcp_client_update_time_remaining**: *actualiza el tiempo restante en el estado actual de DHCP*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="0bc4c-144">Servicios de cliente DHCP específicos de interfaz si se define NX_DHCP_CLIENT_RESORE_STATE:</span><span class="sxs-lookup"><span data-stu-id="0bc4c-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="0bc4c-145">**nx_dhcp_client_interface_get_record**: *crea un registro del estado del cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-146">**nx_dhcp_client_interface_restore_record**: *crea un registro guardado previamente del estado del cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>
- <span data-ttu-id="0bc4c-147">**nx_dhcp_client_interface_update_time_remaining**: *actualiza el tiempo restante en el estado DHCP actual en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="0bc4c-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="0bc4c-148">nx_dhcp_create</span></span>

<span data-ttu-id="0bc4c-149">Crea una instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-150">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-150">Prototype</span></span>

```c
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-151">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-151">Description</span></span>

<span data-ttu-id="0bc4c-152">Este servicio crea una instancia de DHCP para la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="0bc4c-153">De forma predeterminada, la interfaz principal está habilitada para ejecutar DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="0bc4c-154">La entrada del nombre, aunque no se usa en la implementación de cliente DHCP de NetX Duo, debe seguir los criterios de la RFC 1035 para los nombres de hosts.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-154">The name input, while not used in the NetX Duo implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="0bc4c-155">La longitud total no debe superar los 255 caracteres, las etiquetas separadas por puntos deben comenzar con una letra y terminar con una letra o un número, y pueden contener guiones pero no otros caracteres no alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="0bc4c-156">Si la aplicación desea ejecutar otra interfaz de DHCP registrada con la instancia de IP (mediante *nx_ip_interface_attach*), puede llamar a *nx_dhcp_set_interface_index* para ejecutar DHCP solo en esa interfaz o *nx_dhcp_interface_enable* para ejecutar DHCP también en esa interfaz.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="0bc4c-157">Consulte la descripción de estos servicios para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-157">See description of these services for more details.</span></span>

>[!NOTE]
> <span data-ttu-id="0bc4c-158">La aplicación debe asegurarse de que la carga del grupo de paquetes del cliente DHCP pueda admitir el tamaño mínimo del mensaje DHCP especificado en la sección 2 de la RFC 2131 (548 bytes de datos de mensajes DHCP más UDP, IP y los encabezados de trama de la red física).</span><span class="sxs-lookup"><span data-stu-id="0bc4c-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-159">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-159">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-160">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-160">**dhcp_ptr**: Pointer to DHCP control block.</span></span> 
- <span data-ttu-id="0bc4c-161">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-161">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="0bc4c-162">**name_ptr**: puntero al nombre de host de la instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-162">**name_ptr**: Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-163">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-163">Return Values</span></span>

- <span data-ttu-id="0bc4c-164">**NX_SUCCESS**: (0x00) DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-164">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="0bc4c-165">**NX_DHCP_INVALID_NAME**: (0xA8) nombre de host no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-165">**NX_DHCP_INVALID_NAME**: (0xA8) Invalid host name</span></span>
- <span data-ttu-id="0bc4c-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) carga demasiado pequeña para el mensaje DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) Payload too small for DHCP message</span></span>
- <span data-ttu-id="0bc4c-167">NX_PTR_ERROR: (0x16) puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-167">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-168">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-168">Allowed From</span></span>

<span data-ttu-id="0bc4c-169">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="0bc4c-169">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-170">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-170">Example</span></span>

```c
/* Create a DHCP instance.  */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created.  */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="0bc4c-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="0bc4c-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="0bc4c-172">Habilita la interfaz especificada para ejecutar DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="0bc4c-173">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-173">Prototype</span></span>

```c
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0bc4c-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-174">Description</span></span>

<span data-ttu-id="0bc4c-175">Este servicio permite que la interfaz especificada ejecute DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="0bc4c-176">De forma predeterminada, la interfaz principal está habilitada para el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="0bc4c-177">En este punto, se puede iniciar DHCP en esta interfaz llamando a *nx_dhcp_interface_start* o hacerlo en todas las interfaces habilitadas con *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

>[!NOTE] 
> <span data-ttu-id="0bc4c-178">La aplicación debe registrar primero esta interfaz con la instancia de IP mediante *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-178">The application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="0bc4c-179">Además, debe haber un “registro” de interfaz de cliente DHCP disponible para agregar esta interfaz a la lista de interfaces habilitadas.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="0bc4c-180">De forma predeterminada, NX_DHCP_CLIENT_MAX_RECORDS se define como 1.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="0bc4c-181">Establezca esta opción en el número máximo de interfaces que se espera que ejecute el cliente DHCP simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="0bc4c-182">Normalmente NX_DHCP_CLIENT_MAX_RECORDS será igual a NX_MAX_PHYSICAL_INTERFACES; sin embargo, si un dispositivo tiene más interfaces físicas de las que espera ejecutar el cliente DHCP, puede ahorrar memoria si establece NX_DHCP_CLIENT_MAX_RECORDS en un valor inferior a ese número.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="0bc4c-183">No hay una asignación uno a uno de las interfaces físicas con los registros de la interfaz de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="0bc4c-184">La diferencia entre este servicio y *nx_dhcp_set_interface_index* es que el segundo establece una única interfaz para ejecutar DHCP, mientras que este servicio simplemente agrega la interfaz especificada a la lista de interfaces de cliente habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="0bc4c-185">Para deshabilitar una interfaz de DHCP, la aplicación puede llamar al servicio</span><span class="sxs-lookup"><span data-stu-id="0bc4c-185">To disable an interface for DHCP, the application can call the</span></span>

<span data-ttu-id="0bc4c-186">*nx_dhcp_interface_disable*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-186">*nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-187">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-187">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-188">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-188">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="0bc4c-189">**interface_index**: índice de interfaz para habilitar DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-189">**interface_index**: Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-190">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-190">Return Values</span></span>

- <span data-ttu-id="0bc4c-191">**NX_SUCCESS**: (0x00) DHCP habilitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-191">**NX_SUCCESS**: (0x00) Successful DHCP enable</span></span>
- <span data-ttu-id="0bc4c-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) no hay ningún registro disponible para poder habilitar otra interfaz para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another Interface to be enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) interfaz habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-194">NX_PTR_ERROR: (0x16) puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-194">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-195">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-195">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-196">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-196">Allowed From</span></span>

<span data-ttu-id="0bc4c-197">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="0bc4c-197">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-198">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-198">Example</span></span>

```c
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface.  NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled.  */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1.  */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="0bc4c-199">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="0bc4c-199">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="0bc4c-200">Deshabilita la interfaz especificada para ejecutar DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-200">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="0bc4c-201">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-201">Prototype</span></span>

```c

UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0bc4c-202">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-202">Description</span></span>

<span data-ttu-id="0bc4c-203">Este servicio impide que la interfaz especificada ejecute DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-203">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="0bc4c-204">Reinicializa el cliente DHCP en esta interfaz.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-204">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="0bc4c-205">Para reiniciar el cliente DHCP, la aplicación debe volver a habilitar la interfaz mediante *nx_dhcp_interface_enable* y reiniciar DHCP llamando a *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-205">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-206">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-206">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-207">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-207">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="0bc4c-208">**interface_index**: índice de interfaz para deshabilitar DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-208">**interface_index**: Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-209">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-209">Return Values</span></span>

- <span data-ttu-id="0bc4c-210">**NX_SUCCESS**: (0x00) DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-210">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="0bc4c-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-212">NX_PTR_ERROR: (0x16) puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-212">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-213">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-213">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0bc4c-214">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-214">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-215">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-215">Allowed From</span></span>

<span data-ttu-id="0bc4c-216">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-216">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-217">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-217">Example</span></span>

```c
/* Disable DHCP on a secondary interface. */

status =  nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled.  */
```
## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="0bc4c-218">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="0bc4c-218">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="0bc4c-219">Establece la marca de difusión de DHCP</span><span class="sxs-lookup"><span data-stu-id="0bc4c-219">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-220">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-220">Prototype</span></span>

```c
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="0bc4c-221">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-221">Description</span></span>

<span data-ttu-id="0bc4c-222">Este servicio establece o borra la marca de difusión del encabezado del mensaje DHCP de todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-222">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="0bc4c-223">En el caso de algunos mensajes DHCP (por ejemplo, DISCOVER), la marca de difusión se establece en “difundir” porque el cliente no tiene una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-223">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="0bc4c-224">Valores de clear_flag:</span><span class="sxs-lookup"><span data-stu-id="0bc4c-224">clear_flag values:</span></span> 

- <span data-ttu-id="0bc4c-225">**NX_TRUE**: la marca de difusión se borra (solicitud de respuesta de unidifusión).</span><span class="sxs-lookup"><span data-stu-id="0bc4c-225">**NX_TRUE**: broadcast flag is cleared (request unicast response)</span></span>
- <span data-ttu-id="0bc4c-226">**NX_FALSE**: la marca de difusión se establece (solicitud de respuesta de unidifusión).</span><span class="sxs-lookup"><span data-stu-id="0bc4c-226">**NX_FALSE**: broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="0bc4c-227">Este servicio está dirigido a los clientes DHCP que deben pasar por un enrutador para llegar al servidor DHCP, donde el enrutador rechaza el reenvío de mensajes de difusión.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-227">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-228">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-228">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-229">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-229">**dhcp_ptr**: Pointer to DHCP control block</span></span>  
- <span data-ttu-id="0bc4c-230">**clear_flag**: valor en el que se va a establecer la marca de difusión.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-230">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-231">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-231">Return Values</span></span>

- <span data-ttu-id="0bc4c-232">**NX_SUCCESS**: (0x00) marca establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-232">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="0bc4c-233">NX_PTR_ERROR: (0x16) puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-233">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-234">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-234">Allowed From</span></span>

<span data-ttu-id="0bc4c-235">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="0bc4c-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-236">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-236">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response).  */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="0bc4c-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="0bc4c-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="0bc4c-238">Establece o borra la marca de difusión en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-239">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-239">Prototype</span></span>

```c
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr, 
                                            UINT interface_index, 
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="0bc4c-240">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-240">Description</span></span>

<span data-ttu-id="0bc4c-241">Este servicio permite que la aplicación host de cliente DHCP establezca o borre la marca de difusión en los mensajes de cliente DHCP en el servidor DHCP de la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="0bc4c-242">Para obtener más información, consulte **nx_dhcp_clear_broadcast_flag**.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-242">For more details see **nx_dhcp_clear_broadcast_flag**.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-243">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-243">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-244">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-244">**dhcp_ptr**: Pointer to DHCP control block</span></span>
- <span data-ttu-id="0bc4c-245">**interface_index**: índice de la interfaz para establecer la marca de difusión.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-245">**interface_index**: Index of interface to set the broadcast flag</span></span>
- <span data-ttu-id="0bc4c-246">**clear_flag**: valor en el que se va a establecer la marca de difusión.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-246">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-247">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-247">Return Values</span></span>

- <span data-ttu-id="0bc4c-248">**NX_SUCCESS**: (0x00) marca establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-248">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="0bc4c-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-250">NX_PTR_ERROR: (0x16) puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-250">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-251">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-251">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-252">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-252">Allowed From</span></span>

<span data-ttu-id="0bc4c-253">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="0bc4c-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-254">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-254">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface.  */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="0bc4c-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="0bc4c-255">nx_dhcp_delete</span></span>

<span data-ttu-id="0bc4c-256">Elimina una instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-257">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-257">Prototype</span></span>

```c
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-258">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-258">Description</span></span>

<span data-ttu-id="0bc4c-259">Este servicio elimina una instancia del cliente DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-260">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-260">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-261">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-261">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-262">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-262">Return Values</span></span>

- <span data-ttu-id="0bc4c-263">**NX_SUCCESS**: (0x00) DHCP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-263">**NX_SUCCESS**: (0x00) Successful DHCP delete.</span></span>
- <span data-ttu-id="0bc4c-264">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-264">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="0bc4c-265">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-265">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-266">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-266">Allowed From</span></span>

<span data-ttu-id="0bc4c-267">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-268">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-268">Example</span></span>

```c
/* Delete a DHCP instance.  */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted.  */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="0bc4c-269">nx_dhcp_force_renew</span><span class="sxs-lookup"><span data-stu-id="0bc4c-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="0bc4c-270">Envía un mensaje para forzar la renovación.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="0bc4c-271">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-271">Prototype</span></span>

```c
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-272">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-272">Description</span></span>

<span data-ttu-id="0bc4c-273">Este servicio permite que la aplicación host envíe un mensaje para forzar la renovación en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="0bc4c-274">El cliente DHCP debe estar en un estado BOUND.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="0bc4c-275">Esta función establece el estado en RENEW, de modo que el cliente DHCP intente renovar antes de que venza el tiempo de espera de T1.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="0bc4c-276">Si quiere enviar un mensaje para forzar la renovación en una interfaz específica cuando hay varias interfaces habilitadas para DHCP, use *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-277">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-277">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-278">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-278">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-279">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-279">Return Values</span></span>

- <span data-ttu-id="0bc4c-280">**NX_SUCCESS**: (0x00) mensaje para forzar la renovación enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-280">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>
- <span data-ttu-id="0bc4c-281">**NX_DHCP_NOT_BOUND**: (0x94) dirección IP del cliente no enlazada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-281">**NX_DHCP_NOT_BOUND**: (0x94) Client IP address not bound.</span></span>  
- <span data-ttu-id="0bc4c-282">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-282">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="0bc4c-283">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-283">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-284">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-284">Allowed From</span></span>

<span data-ttu-id="0bc4c-285">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-285">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-286">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-286">Example</span></span>

```c
/* Send a force renew message from the Client.  */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="0bc4c-287">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="0bc4c-287">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="0bc4c-288">Envía un mensaje para forzar la renovación en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-288">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-289">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-289">Prototype</span></span>

```c
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr, 
                                   UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0bc4c-290">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-290">Description</span></span>

<span data-ttu-id="0bc4c-291">Este servicio permite que la aplicación host envíe un mensaje para forzar la renovación en la interfaz de entrada, siempre y cuando esa interfaz se haya habilitado para DHCP (consulte *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="0bc4c-291">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="0bc4c-292">El cliente DHCP de la interfaz especificada debe estar en un estado BOUND.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-292">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="0bc4c-293">Esta función establece el estado en RENEW, de modo que el cliente DHCP intente renovar antes de que venza el tiempo de espera de T1.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-293">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-294">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-294">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-295">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-295">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-296">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-296">Return Values</span></span>

- <span data-ttu-id="0bc4c-297">**NX_SUCCESS**: (0x00) mensaje para forzar la renovación enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-297">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>  
- <span data-ttu-id="0bc4c-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-299">NX_PTR_ERROR: (0x16) puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-299">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-300">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-300">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-301">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-301">Allowed From</span></span>

<span data-ttu-id="0bc4c-302">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-303">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-303">Example</span></span>

```c
/* Send a force renew message to the server on interface 1.  */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);


/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="0bc4c-304">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="0bc4c-304">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="0bc4c-305">Establece el grupo de paquetes del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-305">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-306">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-306">Prototype</span></span>

```c
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-307">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-307">Description</span></span>

<span data-ttu-id="0bc4c-308">Este servicio permite que la aplicación cree el grupo de paquetes de cliente DHCP pasando un puntero a un grupo de paquetes creado previamente en esta llamada de servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-308">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="0bc4c-309">Para usar esta característica, la aplicación host debe definir NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-309">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="0bc4c-310">Una vez definido el parámetro, el servicio *nx_dhcp_create* no creará el grupo de paquetes de cliente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-310">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> 

>[!NOTE] 
> <span data-ttu-id="0bc4c-311">Se recomienda que la aplicación use los valores predeterminados para la carga del grupo de paquetes de cliente DHCP, definido como NX_DHCP_PACKET_PAYLOAD en *nxd_dhcp_client.h* al crear el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-311">The application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nxd_dhcp_client.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-312">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-312">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-313">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-313">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="0bc4c-314">**packet_pool_ptr**: puntero al grupo de paquetes creado previamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-314">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-315">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-315">Return Values</span></span>

- <span data-ttu-id="0bc4c-316">**NX_SUCCESS**: (0x00) grupo de paquetes del cliente DHCP establecido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-316">**NX_SUCCESS**: (0x00) DHCP Client packet pool is set</span></span>
- <span data-ttu-id="0bc4c-317">**NX_NOT_ENABLED**: (0x14) el servicio no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-317">**NX_NOT_ENABLED**: (0x14) Service is not enabled</span></span>
- <span data-ttu-id="0bc4c-318">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-318">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) la carga es demasiado pequeña.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-320">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-320">Allowed From</span></span>

<span data-ttu-id="0bc4c-321">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="0bc4c-321">Application code</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-322">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-322">Example</span></span>

```c
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
                                 NX_DHCP_PACKET_PAYLOAD, pointer, 
                                 (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool.  */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set.  */

```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="0bc4c-323">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="0bc4c-323">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="0bc4c-324">Establece la dirección IP solicitada para la instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-324">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-325">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-325">Prototype</span></span>

```c
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr, 
                               ULONG client_ip_address, 
                               UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="0bc4c-326">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-326">Description</span></span>

<span data-ttu-id="0bc4c-327">Este servicio establece la dirección IP que el cliente DHCP debe solicitar al servidor DHCP en la primera interfaz habilitada para DHCP en el registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-327">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="0bc4c-328">Si se establece la marca *skip_discover_message*, el cliente DHCP omite el mensaje de detección y envía un mensaje de solicitud.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-328">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="0bc4c-329">Para establecer la solicitud de una dirección IP específica para mensajes DHCP en una interfaz concreta, use el servicio *nx_dhcp_interface_request_client_ip*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-329">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-330">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-330">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-331">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-331">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="0bc4c-332">**client_ip_address**: dirección IP que se va a solicitar del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-332">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="0bc4c-333">**skip_discover_message**:</span><span class="sxs-lookup"><span data-stu-id="0bc4c-333">**skip_discover_message**:</span></span> 
    - <span data-ttu-id="0bc4c-334">si es el valor es true, el cliente DHCP envía un mensaje de solicitud.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-334">If true, DHCP Client sends Request message</span></span>
    - <span data-ttu-id="0bc4c-335">Si es false, envía el mensaje de detección.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-335">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-336">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-336">Return Values</span></span>

- <span data-ttu-id="0bc4c-337">**NX_SUCCESS**: (0x00) dirección IP solicitada establecida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-337">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="0bc4c-338">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-338">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) la dirección IP NULL solicitada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) NULL IP address requested</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-340">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-340">Allowed From</span></span>

<span data-ttu-id="0bc4c-341">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-342">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-342">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message.  */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */

```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="0bc4c-343">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="0bc4c-343">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="0bc4c-344">Establece la dirección IP solicitada para la instancia de DHCP en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-344">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-345">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-345">Prototype</span></span>

```c
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr, UINT  interface_index, 
                                         ULONG client_ip_address, UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="0bc4c-346">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-346">Description</span></span>

<span data-ttu-id="0bc4c-347">Este servicio establece la dirección IP que el cliente DHCP debe solicitar al servidor DHCP en la interfaz especificada, si dicha interfaz está habilitada para DHCP (consulte *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="0bc4c-347">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="0bc4c-348">Si se establece la marca *skip_discover_message*, el cliente DHCP omite el mensaje de detección y envía un mensaje de solicitud.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-348">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-349">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-349">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-350">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-350">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="0bc4c-351">**Interface_index**: índice de la interfaz en la que se va a solicitar la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-351">**Interface_index**: Index of interface to request IP address on</span></span>
- <span data-ttu-id="0bc4c-352">**client_ip_address**: dirección IP que se va a solicitar del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-352">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="0bc4c-353">**skip_discover_message** si es true, el cliente DHCP envía el mensaje de solicitud; de lo contrario, envía el mensaje de detección.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-353">**skip_discover_message**: If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-354">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-354">Return Values</span></span>

- <span data-ttu-id="0bc4c-355">**NX_SUCCESS**: (0x00) dirección IP solicitada establecida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-355">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="0bc4c-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-357">NX_PTR_ERROR: (0x16) puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-357">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-358">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-358">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-359">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-359">Allowed From</span></span>

<span data-ttu-id="0bc4c-360">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-361">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-361">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0.  */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="0bc4c-362">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="0bc4c-362">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="0bc4c-363">Borra los parámetros de red del cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="0bc4c-363">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="0bc4c-364">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-364">Prototype</span></span>

```c
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-365">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-365">Description</span></span>

<span data-ttu-id="0bc4c-366">Este servicio borra los parámetros de red de la aplicación host (dirección IP, dirección de red y máscara de red) y borra el estado del cliente DHCP en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-366">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="0bc4c-367">Se usa en combinación con *nx_dhcp_stop* y *nx_dhcp_start* para “reiniciar” la máquina de estados de DHCP:</span><span class="sxs-lookup"><span data-stu-id="0bc4c-367">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="0bc4c-368">Para reinicializar el cliente DHCP en una interfaz específica cuando hay varias interfaces habilitadas para DHCP, use el servicio *nx_dhcp_interface_reinitialize*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-368">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-369">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-369">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-370">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-370">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-371">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-371">Return Values</span></span>

- <span data-ttu-id="0bc4c-372">**NX_SUCCESS**: (0x00) DHCP reinicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-372">**NX_SUCCESS**: (0x00) DHCP successfully reinitialized</span></span> 
- <span data-ttu-id="0bc4c-373">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-373">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-374">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-374">Allowed From</span></span>

<span data-ttu-id="0bc4c-375">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-376">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-376">Example</span></span>

```c
/* Reinitialize the previously started DHCP client.  */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="0bc4c-377">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="0bc4c-377">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="0bc4c-378">Borra los parámetros de red del cliente DHCP en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-378">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="0bc4c-379">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-379">Prototype</span></span>

```c
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr, 
                                     UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0bc4c-380">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-380">Description</span></span>

<span data-ttu-id="0bc4c-381">Este servicio borra los parámetros de red (dirección IP, dirección de red y máscara de red) en la interfaz especificada si dicha interfaz está habilitada para DHCP (consulte *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="0bc4c-381">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="0bc4c-382">Consulte *nx_dhcp_reinitialize* para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-382">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-383">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-383">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-384">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-384">**dhcp_ptr**: Pointer to previously created DHCP instance</span></span>
- <span data-ttu-id="0bc4c-385">**interface_index**: índice de interfaz para reinicializar.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-385">**interface_index**: Index of interface to reinitialize</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-386">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-386">Return Values</span></span>

- <span data-ttu-id="0bc4c-387">**NX_SUCCESS**: (0x00) interfaz reinicializada correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-387">**NX_SUCCESS**: (0x00) Interface successfully reinitialized</span></span>
- <span data-ttu-id="0bc4c-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-389">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-389">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-390">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-390">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0bc4c-391">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-391">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-392">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-392">Allowed From</span></span>

<span data-ttu-id="0bc4c-393">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-393">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-394">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-394">Example</span></span>

```c
/* Reinitialize the previously started DHCP client on interface 1.  */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="0bc4c-395">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="0bc4c-395">nx_dhcp_release</span></span>

<span data-ttu-id="0bc4c-396">Libera la dirección IP concedida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-396">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-397">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-397">Prototype</span></span>

```c
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-398">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-398">Description</span></span>

<span data-ttu-id="0bc4c-399">Este servicio libera la dirección IP obtenida de un servidor DHCP mediante el envío del mensaje RELEASE a dicho servidor.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-399">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="0bc4c-400">Seguidamente, reinicializa el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-400">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="0bc4c-401">Este servicio se aplica a todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-401">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="0bc4c-402">La aplicación puede reiniciar el cliente DHCP llamando a *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-402">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="0bc4c-403">Para volver a liberar una dirección en el servidor DHCP en una interfaz específica, use el servicio *nx_dhcp_interface_release*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-403">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-404">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-404">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-405">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-405">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-406">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-406">Return Values</span></span>

- <span data-ttu-id="0bc4c-407">**NX_SUCCESS**: (0x00) DHCP liberado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-407">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>  
- <span data-ttu-id="0bc4c-408">**NX_DHCP_NOT_BOUND**: (0x94) no se ha concedido la dirección IP, por lo que no se puede liberar.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-408">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="0bc4c-409">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-409">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="0bc4c-410">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-410">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-411">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-411">Allowed From</span></span>

<span data-ttu-id="0bc4c-412">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-413">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-413">Example</span></span>

```c
/* Release the previously leased IP address.  */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="0bc4c-414">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="0bc4c-414">nx_dhcp_interface_release</span></span>

<span data-ttu-id="0bc4c-415">Libera la dirección IP en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-415">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-416">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-416">Prototype</span></span>

```c
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0bc4c-417">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-417">Description</span></span>

<span data-ttu-id="0bc4c-418">Este servicio libera la dirección IP obtenida de un servidor DHCP en la interfaz especificada y reinicializa el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-418">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="0bc4c-419">El cliente DHCP puede reiniciarse mediante una llamada a *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-419">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-420">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-420">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-421">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-421">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-422">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-422">Return Values</span></span>

- <span data-ttu-id="0bc4c-423">**NX_SUCCESS**: (0x00) DHCP liberado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-423">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>
- <span data-ttu-id="0bc4c-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-425">**NX_DHCP_NOT_BOUND**: (0x94) no se ha concedido la dirección IP, por lo que no se puede liberar.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-425">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="0bc4c-426">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-426">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-427">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-427">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0bc4c-428">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-428">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-429">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-429">Allowed From</span></span>

<span data-ttu-id="0bc4c-430">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-430">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-431">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-431">Example</span></span>

```c
/* Release the previously leased IP address on interface 1.  */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="0bc4c-432">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="0bc4c-432">nx_dhcp_decline</span></span>

<span data-ttu-id="0bc4c-433">Rechaza la dirección IP del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-433">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-434">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-434">Prototype</span></span>

```c
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-435">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-435">Description</span></span>

<span data-ttu-id="0bc4c-436">Este servicio rechaza una dirección IP concedida desde el servidor DHCP en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-436">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="0bc4c-437">Si se define NX_DHCP_CLIENT_ SEND_ ARP_PROBE, el cliente DHCP enviará un mensaje DECLINE si detecta que la dirección IP ya está en uso.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-437">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="0bc4c-438">Consulte **Sondeos ARP** en el capítulo 1 para obtener más información sobre la configuración de sondeo ARP en el cliente DHCP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-438">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX Duo DHCP Client.</span></span>

<span data-ttu-id="0bc4c-439">La aplicación puede usar este servicio para rechazar su dirección IP si detecta que la dirección se está usando por otros medios.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-439">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="0bc4c-440">Este servicio reinicializa el cliente DHCP para que se pueda reiniciar mediante una llamada a *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-440">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-441">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-441">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-442">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-442">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-443">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-443">Return Values</span></span>

- <span data-ttu-id="0bc4c-444">**NX_SUCCESS**: (0x00) rechazo enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-444">**NX_SUCCESS**: (0x00) Decline successfully sent</span></span>  
- <span data-ttu-id="0bc4c-445">**NX_DHCP_NOT_BOUND**: (0x94) cliente DHCP no enlazado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-445">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="0bc4c-446">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-446">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-447">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-447">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-448">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-448">Allowed From</span></span>

<span data-ttu-id="0bc4c-449">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-449">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-450">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-450">Example</span></span>

```c

/* Decline the IP address offered by the DHCP server.  */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="0bc4c-451">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="0bc4c-451">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="0bc4c-452">Rechaza la dirección IP del servidor DHCP en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-452">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-453">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-453">Prototype</span></span>

```c
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0bc4c-454">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-454">Description</span></span>

<span data-ttu-id="0bc4c-455">Este servicio envía el mensaje DECLINE al servidor para rechazar una dirección IP asignada por el servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-455">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="0bc4c-456">También reinicializa el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-456">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="0bc4c-457">Consulte *nx_dhcp_decline* para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-457">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-458">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-458">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-459">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-459">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="0bc4c-460">**Interface_index**: índice de la interfaz para rechazar la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-460">**Interface_index**: Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-461">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-461">Return Values</span></span>

- <span data-ttu-id="0bc4c-462">**NX_SUCCESS**: (0x00) mensaje DECLINE de DHCP enviado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-462">**NX_SUCCESS**: (0x00) DHCP decline message sent</span></span>  
- <span data-ttu-id="0bc4c-463">**NX_DHCP_NOT_BOUND**: (0x94) cliente DHCP no enlazado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-463">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="0bc4c-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-465">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-465">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-466">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-466">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0bc4c-467">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-467">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-468">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-468">Allowed From</span></span>

<span data-ttu-id="0bc4c-469">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-470">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-470">Example</span></span>

```c
/* Decline the IP address offered by the DHCP server on interface 2.  */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```
## <a name="nx_dhcp_send_request"></a><span data-ttu-id="0bc4c-471">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="0bc4c-471">nx_dhcp_send_request</span></span>

<span data-ttu-id="0bc4c-472">Envía un mensaje DHCP al servidor.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-472">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-473">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-473">Prototype</span></span>

```c
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);

```

### <a name="description"></a><span data-ttu-id="0bc4c-474">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-474">Description</span></span>

<span data-ttu-id="0bc4c-475">Este servicio envía el mensaje DHCP especificado al servidor DHCP en la primera interfaz habilitada para DHCP que se encuentra en el registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-475">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="0bc4c-476">Para enviar un mensaje RELEASE o DECLINE, la aplicación debe utilizar los servicios *nx_dhcp [_interface] _release*() o *nx_dhcp_interface_decline ()* , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-476">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="0bc4c-477">El cliente DHCP debe iniciarse para usar este servicio, salvo para enviar el tipo de mensaje INFORM_REQUEST.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-477">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

>[!NOTE]
> <span data-ttu-id="0bc4c-478">Este servicio no está destinado a que la aplicación host “impulse” la máquina de estados del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-478">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-479">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-479">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-480">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-480">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="0bc4c-481">**dhcp_message_type**: solicitud de mensaje (definida en *nxd_dhcp_client.h*).</span><span class="sxs-lookup"><span data-stu-id="0bc4c-481">**dhcp_message_type**: Message request (defined in *nxd_dhcp_client.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-482">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-482">Return Values</span></span>

- <span data-ttu-id="0bc4c-483">**NX_SUCCESS**: (0x00) mensaje DHCP enviado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-483">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="0bc4c-484">**NX_DHCP_NOT_STARTED**: (0x96) índice de interfaz no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-484">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="0bc4c-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) tipo de mensaje no válido para enviar.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="0bc4c-486">NX_PTR_ERROR: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-486">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-487">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-487">Allowed From</span></span>

<span data-ttu-id="0bc4c-488">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-488">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-489">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-489">Example</span></span>

```c
/* Send the DHCP INFORM REQUEST message to the server.  */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="0bc4c-490">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="0bc4c-490">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="0bc4c-491">Envía un mensaje DHCP al servidor en una interfaz específica.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-491">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-492">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-492">Prototype</span></span>

```c
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr, 
                                    UINT interface_index, 
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="0bc4c-493">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-493">Description</span></span>

<span data-ttu-id="0bc4c-494">Este servicio envía un mensaje al servidor DHCP en la interfaz especificada si esa interfaz está habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-494">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="0bc4c-495">Para enviar un mensaje RELEASE o DECLINE, la aplicación debe utilizar los servicios *nx_dhcp [_interface] _release*() o *nx_dhcp_interface_decline ()* , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-495">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="0bc4c-496">El cliente DHCP debe iniciarse para usar este servicio, salvo para enviar el tipo de mensaje DHCP INFORM REQUEST.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-496">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="0bc4c-497">Este servicio no está destinado a que la aplicación host “impulse” la máquina de estados del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-497">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-498">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-498">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-499">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-499">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="0bc4c-500">**Interface_index**: índice de la interfaz a la que se va a enviar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-500">**Interface_index**: Index of interface to send message on</span></span>
- <span data-ttu-id="0bc4c-501">**dhcp_message_type**: solicitud de mensaje (definida en nxd_dhcp_client.h).</span><span class="sxs-lookup"><span data-stu-id="0bc4c-501">**dhcp_message_type**: Message request (defined in nxd_dhcp_client.h)</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-502">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-502">Return Values</span></span>

- <span data-ttu-id="0bc4c-503">**NX_SUCCESS**: (0x00) mensaje DHCP enviado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-503">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="0bc4c-504">**NX_DHCP_NOT_STARTED**: (0x96) índice de interfaz no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-504">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="0bc4c-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) tipo de mensaje no válido para enviar.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="0bc4c-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-507">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-507">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-508">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-508">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0bc4c-509">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-509">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-510">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-510">Allowed From</span></span>

<span data-ttu-id="0bc4c-511">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-511">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-512">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-512">Example</span></span>

```c
/* Send the INFORM REQUEST message to the server on the primary interface.  */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="0bc4c-513">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="0bc4c-513">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="0bc4c-514">Obtiene la dirección IP del servidor DHCP del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-514">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-515">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-515">Prototype</span></span>

```c
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr, 
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="0bc4c-516">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-516">Description</span></span>

<span data-ttu-id="0bc4c-517">Este servicio recupera la dirección IP del servidor DHCP del cliente DHCP en la primera interfaz habilitada para DHCP que se encuentra en el registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-517">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="0bc4c-518">El autor de la llamada solo puede utilizar este servicio después de que el cliente DHCP se haya enlazado a una dirección IP asignada por el servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-518">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="0bc4c-519">La aplicación host puede usar el servicio *nx_ip_status_check* para comprobar que la dirección IP está establecida o usar *nx_dhcp_state_change_notify* y consultar si el estado del cliente DHCP es NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-519">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the nx *_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="0bc4c-520">Consulte *nx_dhcp_state_change_notify* para obtener más información sobre cómo establecer la función de devolución de llamada de cambio de estado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-520">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="0bc4c-521">Para buscar el servidor DHCP en una interfaz específica cuando hay varias interfaces habilitadas para el cliente DHCP, use el servicio *nx_dhcp_interface_server_address_get*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-521">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-522">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-522">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-523">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-523">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="0bc4c-524">**server_address**: puntero a la dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-524">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-525">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-525">Return Values</span></span>

- <span data-ttu-id="0bc4c-526">**NX_SUCCESS**: (0x00) dirección del servidor DHCP devuelta.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-526">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="0bc4c-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) no hay interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-528">NX_PTR_ERROR: (0x16) puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-528">NX_PTR_ERROR: (0x16) Invalid input pointer</span></span>
- <span data-ttu-id="0bc4c-529">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-529">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-530">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-530">Allowed From</span></span>

<span data-ttu-id="0bc4c-531">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-532">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-532">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the bound state and get its DHCP server IP address.*/

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{
ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
        }

}
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="0bc4c-533">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="0bc4c-533">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="0bc4c-534">Obtiene la dirección IP del servidor DHCP del cliente DHCP en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-534">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-535">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-535">Prototype</span></span>

```c
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr, 
                                          UINT interface_index,
                                          ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="0bc4c-536">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-536">Description</span></span>

<span data-ttu-id="0bc4c-537">Este servicio recupera la dirección IP del servidor DHCP del cliente DHCP en la interfaz especificada si dicha interfaz está habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-537">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="0bc4c-538">El cliente DHCP debe estar en un estado BOUND.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-538">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="0bc4c-539">Después de iniciar el cliente DHCP en esa interfaz, la aplicación host puede usar el servicio *nx_ip_status_check* para comprobar que la dirección IP está establecida o bien usar la devolución de llamada de cambio de estado del cliente DHCP y consultar si el estado del cliente DHCP es NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-539">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="0bc4c-540">Consulte *nx_dhcp_state_change_notify* para obtener más información sobre cómo establecer la función de devolución de llamada de cambio de estado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-540">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-541">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-541">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-542">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-542">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="0bc4c-543">**Interface_index**: índice de la interfaz para obtener la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-543">**Interface_index**: Index of interface to obtain IP address</span></span>
- <span data-ttu-id="0bc4c-544">**server_address**: puntero a la dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-544">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-545">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-545">Return Values</span></span>

- <span data-ttu-id="0bc4c-546">**NX_SUCCESS**: (0x00) dirección del servidor DHCP devuelta.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-546">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="0bc4c-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) no hay interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-548">**NX_DHCP_NOT_BOUND**: (0x94) cliente DHCP no enlazado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-548">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="0bc4c-549">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-549">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="0bc4c-550">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-550">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0bc4c-551">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-551">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-552">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-552">Allowed From</span></span>

<span data-ttu-id="0bc4c-553">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-553">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-554">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-554">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. */

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

/* Get the DHCP server IP address on interface 1 */
if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
         status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                       &server_address);
        }
}
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="0bc4c-555">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="0bc4c-555">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="0bc4c-556">Establece la interfaz de red para la instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-556">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-557">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-557">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="0bc4c-558">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-558">Description</span></span>

<span data-ttu-id="0bc4c-559">Este servicio establece la interfaz de red para que la instancia de DHCP se conecte al servidor DHCP cuando se ejecuta el cliente DHCP configurado para una sola interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-559">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="0bc4c-560">De forma predeterminada, el cliente DHCP se ejecuta en la interfaz principal.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-560">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="0bc4c-561">Para ejecutar DHCP en un servicio secundario, use este servicio para establecer la interfaz secundaria como la interfaz de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-561">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="0bc4c-562">La aplicación debe registrar previamente la interfaz especificada en la instancia de IP mediante el servicio de *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-562">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

>[!NOTE]
> <span data-ttu-id="0bc4c-563">Este servicio está pensado para las aplicaciones que tienen previsto ejecutar el cliente DHCP en una sola interfaz.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-563">This service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="0bc4c-564">Para ejecutar DHCP en varias interfaces, consulte *nx_dhcp_interface_enable* para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-564">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-565">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-565">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-566">**dhcp_ptr**: puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-566">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="0bc4c-567">**index**: índice de la interfaz de red del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-567">**index**: Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-568">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-568">Return Values</span></span>

- <span data-ttu-id="0bc4c-569">**NX_SUCCESS**: (0x00) interfaz establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-569">**NX_SUCCESS**: (0x00) Interface is successfully set.</span></span>
- <span data-ttu-id="0bc4c-570">**NX_INVALID_INTERFACE**: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-570">**NX_INVALID_INTERFACE**: (0x4C) Invalid network interface</span></span>
- <span data-ttu-id="0bc4c-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) interfaz habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) no hay ningún registro disponible para otro.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another</span></span> 
- <span data-ttu-id="0bc4c-573">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-573">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-574">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-574">Allowed From</span></span>

<span data-ttu-id="0bc4c-575">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-575">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-576">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-576">Example</span></span>

```c
/* Set the DHCP Client interface to the secondary interface (index 1).  */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set.  */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="0bc4c-577">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="0bc4c-577">nx_dhcp_start</span></span>

<span data-ttu-id="0bc4c-578">Inicia el procesamiento de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-578">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-579">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-579">Prototype</span></span>

```c
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-580">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-580">Description</span></span>

<span data-ttu-id="0bc4c-581">Este servicio inicia el procesamiento de DHCP en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-581">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="0bc4c-582">De forma predeterminada, la interfaz principal se habilita para DHCP cuando la aplicación llama a *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="0bc4c-582">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="0bc4c-583">Para comprobar si la instancia de IP está enlazada a una dirección IP en la interfaz de cliente DHCP, use *nx_ip_status_check* para ver la confirmación de que la dirección IP es válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-583">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="0bc4c-584">Si hay otras interfaces que ya ejecutan DHCP, no se verán afectadas por este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-584">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="0bc4c-585">Para iniciar DHCP en una interfaz específica cuando hay varias interfaces habilitadas, utilice el servicio *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-585">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-586">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-586">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-587">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-587">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-588">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-588">Return Values</span></span>

- <span data-ttu-id="0bc4c-589">**NX_SUCCESS**: (0x00) DHCP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-589">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span>  
- <span data-ttu-id="0bc4c-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="0bc4c-591">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-591">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="0bc4c-592">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-592">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-593">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-593">Allowed From</span></span>

<span data-ttu-id="0bc4c-594">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-595">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-595">Example</span></span>

```c
/* Start the DHCP processing for this IP instance.  */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="0bc4c-596">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="0bc4c-596">nx_dhcp_interface_start</span></span>

<span data-ttu-id="0bc4c-597">Inicia el procesamiento de DHCP en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-597">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-598">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-598">Prototype</span></span>

```c
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0bc4c-599">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-599">Description</span></span>

<span data-ttu-id="0bc4c-600">Este servicio inicia el procesamiento de DHCP en la interfaz especificada si dicha interfaz está habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-600">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="0bc4c-601">Consulte *nx_dhcp_interface_enable*() para obtener más información sobre cómo habilitar una interfaz para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-601">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="0bc4c-602">De forma predeterminada, la interfaz principal se habilita para DHCP cuando la aplicación llama a *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="0bc4c-602">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="0bc4c-603">Si no hay otras interfaces que ejecuten el cliente DHCP, este servicio iniciará o reanudará el subproceso del cliente DHCP y (re)activará el temporizador del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-603">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="0bc4c-604">La aplicación debe usar *nx_ip_status_check* para comprobar si se obtiene una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-604">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-605">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-605">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-606">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-606">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="0bc4c-607">**Interface_index**: índice en el que se va a iniciar el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-607">**Interface_index**: Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-608">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-608">Return Values</span></span>

- <span data-ttu-id="0bc4c-609">**NX_SUCCESS**: (0x00) DHCP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-609">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span> 
- <span data-ttu-id="0bc4c-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="0bc4c-611">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-611">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="0bc4c-612">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-612">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0bc4c-613">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-613">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-614">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-614">Allowed From</span></span>

<span data-ttu-id="0bc4c-615">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-615">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-616">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-616">Example</span></span>

```c
/* Start the DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="0bc4c-617">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="0bc4c-617">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="0bc4c-618">Establece la función de devolución de llamada de cambio de estado de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-618">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-619">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-619">Prototype</span></span>

```c
UINT nx_dhcp_state_change_notify(NX_DHCP *dhcp_ptr, 
                                 VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="0bc4c-620">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-620">Description</span></span>

<span data-ttu-id="0bc4c-621">Este servicio registra la función de devolución de llamada especificada “dhcp_state_change_notify” para notificar a una aplicación los cambios de estado de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-621">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="0bc4c-622">La función de devolución de llamada proporciona el estado al que ha pasado el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-622">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="0bc4c-623">A continuación se indican los valores asociados a los distintos estados de DHCP:</span><span class="sxs-lookup"><span data-stu-id="0bc4c-623">Following are values associated with the various DHCP states:</span></span>

- <span data-ttu-id="0bc4c-624">NX_DHCP_STATE_BOOT: 1</span><span class="sxs-lookup"><span data-stu-id="0bc4c-624">NX_DHCP_STATE_BOOT: 1</span></span>
- <span data-ttu-id="0bc4c-625">NX_DHCP_STATE_INIT: 2</span><span class="sxs-lookup"><span data-stu-id="0bc4c-625">NX_DHCP_STATE_INIT: 2</span></span>
- <span data-ttu-id="0bc4c-626">NX_DHCP_STATE_SELECTING: 3</span><span class="sxs-lookup"><span data-stu-id="0bc4c-626">NX_DHCP_STATE_SELECTING: 3</span></span>
- <span data-ttu-id="0bc4c-627">NX_DHCP_STATE_REQUESTING: 4</span><span class="sxs-lookup"><span data-stu-id="0bc4c-627">NX_DHCP_STATE_REQUESTING: 4</span></span>
- <span data-ttu-id="0bc4c-628">NX_DHCP_STATE_BOUND: 5</span><span class="sxs-lookup"><span data-stu-id="0bc4c-628">NX_DHCP_STATE_BOUND: 5</span></span>
- <span data-ttu-id="0bc4c-629">NX_DHCP_STATE_RENEWING: 6</span><span class="sxs-lookup"><span data-stu-id="0bc4c-629">NX_DHCP_STATE_RENEWING: 6</span></span>
- <span data-ttu-id="0bc4c-630">NX_DHCP_STATE_REBINDING: 7</span><span class="sxs-lookup"><span data-stu-id="0bc4c-630">NX_DHCP_STATE_REBINDING: 7</span></span>
- <span data-ttu-id="0bc4c-631">NX_DHCP_STATE_FORCERENEW: 8</span><span class="sxs-lookup"><span data-stu-id="0bc4c-631">NX_DHCP_STATE_FORCERENEW: 8</span></span>
- <span data-ttu-id="0bc4c-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span><span class="sxs-lookup"><span data-stu-id="0bc4c-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-633">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-633">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-634">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-634">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="0bc4c-635">**dhcp_state_change_notify**: puntero de función de devolución de llamada de cambio de estado</span><span class="sxs-lookup"><span data-stu-id="0bc4c-635">**dhcp_state_change_notify**: State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-636">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-636">Return Values</span></span>

- <span data-ttu-id="0bc4c-637">**NX_SUCCESS**: (0x00) devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-637">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="0bc4c-638">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-638">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="0bc4c-639">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-639">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-640">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-640">Allowed From</span></span>

<span data-ttu-id="0bc4c-641">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="0bc4c-641">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-642">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-642">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change, assuming DHCP has alreadybeen created.  */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="0bc4c-643">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="0bc4c-643">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="0bc4c-644">Establece la función de devolución de llamada de cambio de estado DHCP en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-644">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-645">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-645">Prototype</span></span>

```c
UINT nx_dhcp_interface_state_change_notify(NX_DHCP *dhcp_ptr, UINT interface_index,
                                           VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                                                            UINT interface_index,
                                                                            UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="0bc4c-646">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-646">Description</span></span>

<span data-ttu-id="0bc4c-647">Este servicio registra la función de devolución de llamada especificada para notificar a una aplicación los cambios de estado de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-647">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="0bc4c-648">Los argumentos de entrada de la función de devolución de llamada son el índice de interfaz y el estado al que el cliente DHCP ha pasado en esa interfaz.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-648">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="0bc4c-649">Para obtener más información sobre las funciones de cambio de estado, consulte *nx_dhcp_state_change_notify*().</span><span class="sxs-lookup"><span data-stu-id="0bc4c-649">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-650">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-650">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-651">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-651">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="0bc4c-652">**dhcp_interface_state_change_notify**: puntero de función de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-652">**dhcp_interface_state_change_notify**: Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-653">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-653">Return Values</span></span>

- <span data-ttu-id="0bc4c-654">**NX_SUCCESS**: (0x00) devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-654">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="0bc4c-655">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-655">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-656">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-656">Allowed From</span></span>

<span data-ttu-id="0bc4c-657">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="0bc4c-657">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-658">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-658">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change,   
   assuming DHCP has alreadybeen created.  */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                  UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="0bc4c-659">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="0bc4c-659">nx_dhcp_stop</span></span>

<span data-ttu-id="0bc4c-660">Detiene el procesamiento de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-660">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-661">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-661">Prototype</span></span>

```c
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-662">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-662">Description</span></span>

<span data-ttu-id="0bc4c-663">Este servicio detiene el procesamiento de DHCP en todas las interfaces que han iniciado el procesamiento de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-663">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="0bc4c-664">Si no hay ninguna interfaz que procese DHCP, este servicio suspenderá el subproceso de cliente DHCP e inactivará el temporizador de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-664">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="0bc4c-665">Para detener DHCP en una interfaz específica si hay varias interfaces habilitadas para DHCP, use el servicio *nx_dhcp_interface_stop*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-665">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-666">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-666">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-667">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-667">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-668">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-668">Return Values</span></span>

- <span data-ttu-id="0bc4c-669">**NX_SUCCESS**: (0x00) DHCP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-669">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="0bc4c-670">**NX_DHCP_NOT_STARTED**: (0x96) no se ha iniciado la instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-670">**NX_DHCP_NOT_STARTED**: (0x96) The DHCP instance not started.</span></span>
- <span data-ttu-id="0bc4c-671">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-671">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="0bc4c-672">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-672">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-673">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-673">Allowed From</span></span>

<span data-ttu-id="0bc4c-674">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-675">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-675">Example</span></span>

```c
/* Stop the DHCP processing for this IP instance.  */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="0bc4c-676">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="0bc4c-676">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="0bc4c-677">Detiene el procesamiento de DHCP en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-677">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-678">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-678">Prototype</span></span>

```c
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0bc4c-679">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-679">Description</span></span>

<span data-ttu-id="0bc4c-680">Este servicio detiene el procesamiento de DHCP en la interfaz especificada si DHCP ya está iniciado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-680">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="0bc4c-681">Si no hay ninguna otra interfaz que ejecute DHCP, se suspenden el subproceso y el temporizador de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-681">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-682">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-682">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-683">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-683">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="0bc4c-684">**Interface_index**: interfaz en la que se va a detener el procesamiento de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-684">**Interface_index**: Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-685">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-685">Return Values</span></span>

- <span data-ttu-id="0bc4c-686">**NX_SUCCESS**: (0x00) DHCP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-686">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="0bc4c-687">**NX_DHCP_NOT_STARTED**: (0x96) no se ha iniciado DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-687">**NX_DHCP_NOT_STARTED**: (0x96) DHCP not started.</span></span>
- <span data-ttu-id="0bc4c-688">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-688">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="0bc4c-689">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-689">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0bc4c-690">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-690">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-691">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-691">Allowed From</span></span>

<span data-ttu-id="0bc4c-692">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-693">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-693">Example</span></span>

```c
/* Stop DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="0bc4c-694">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="0bc4c-694">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="0bc4c-695">Recupera una opción DHCP de la última respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-695">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-696">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-696">Prototype</span></span>

```c
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, UINT request_option, 
                                  UCHAR *destination_ptr, UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="0bc4c-697">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-697">Description</span></span>

<span data-ttu-id="0bc4c-698">Este servicio recupera la opción DHCP especificada del búfer de opciones DHCP de la primera interfaz habilitada para DHCP encontrada en el registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-698">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="0bc4c-699">Si se realiza correctamente, los datos de la opción se copian en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-699">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-700">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-700">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-701">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-701">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>  
- <span data-ttu-id="0bc4c-702">**request_option**: opción DHCP, tal y como se especifica en las RFC.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-702">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="0bc4c-703">Consulte la opción NX_DHCP_OPTION en *nxd_dhcp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-703">See the NX_DHCP_OPTION option in *nxd_dhcp_client.h*.</span></span>
- <span data-ttu-id="0bc4c-704">**destination_ptr**: puntero al destino de la cadena de respuesta.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-704">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="0bc4c-705">**destination_size**: puntero al tamaño del destino y, en la devolución, al destino para colocar el número de bytes devueltos.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-705">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-706">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-706">Return Values</span></span>

- <span data-ttu-id="0bc4c-707">**NX_SUCCESS**: (0x00) opción recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-707">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="0bc4c-708">**NX_DHCP_NOT_BOUND**: (0x94) cliente DHCP no enlazado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-708">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound.</span></span>
- <span data-ttu-id="0bc4c-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) no hay interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="0bc4c-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) destino demasiado pequeño para mantener la respuesta.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) Destination is too small to hold response.</span></span>
- <span data-ttu-id="0bc4c-711">**NX_DHCP_PARSE_ERROR**: (0x97) no se encontró la opción en la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-711">**NX_DHCP_PARSE_ERROR**: (0x97) Option not found in Server response.</span></span>
- <span data-ttu-id="0bc4c-712">NX_PTR_ERROR: (0x16) puntero de entrada no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-712">NX_PTR_ERROR: (0x16) Invalid input pointer.</span></span>
- <span data-ttu-id="0bc4c-713">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-713">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-714">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-714">Allowed From</span></span>

<span data-ttu-id="0bc4c-715">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-715">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-716">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-716">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
                                        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="0bc4c-717">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="0bc4c-717">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="0bc4c-718">Recupera una opción de DHCP de la última respuesta del servidor en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-718">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-719">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-719">Prototype</span></span>

```c
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT request_option, UCHAR *destination_ptr,
                                            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="0bc4c-720">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-720">Description</span></span>

<span data-ttu-id="0bc4c-721">Este servicio recupera la opción DHCP especificada del búfer de opciones DHCP en la interfaz especificada, si dicha interfaz está habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-721">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="0bc4c-722">Si se realiza correctamente, los datos de la opción se copian en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-722">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-723">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-723">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-724">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-724">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="0bc4c-725">**Interface_index**: índice en el que se va a recuperar la opción especificada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-725">**Interface_index**: Index on which to retrieve the specified option</span></span>
- <span data-ttu-id="0bc4c-726">**request_option**: opción DHCP, tal y como se especifica en las RFC.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-726">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="0bc4c-727">Consulte la opción NX_DHCP_OPTION en *nxd_dhcp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-727">See the NX_DHCP_OPTION option: in *nxd_dhcp_client.h*.</span></span>  
- <span data-ttu-id="0bc4c-728">**destination_ptr**: puntero al destino de la cadena de respuesta.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-728">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="0bc4c-729">**destination_size**: puntero al tamaño del destino y, en la devolución, al destino para colocar el número de bytes devueltos.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-729">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-730">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-730">Return Values</span></span>

- <span data-ttu-id="0bc4c-731">**NX_SUCCESS**: (0x00) opción recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-731">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="0bc4c-732">**NX_DHCP_NOT_BOUND**: (0x94) dirección IP no asignada.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-732">**NX_DHCP_NOT_BOUND**: (0x94) IP address not assigned</span></span>
- <span data-ttu-id="0bc4c-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) búfer demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) Buffer is too small</span></span>
- <span data-ttu-id="0bc4c-734">**NX_DHCP_PARSE_ERROR**: (0x97) no se encontró la opción DHCP en la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-734">**NX_DHCP_PARSE_ERROR**: (0x97) DHCP Option not found in Server response.</span></span>
- <span data-ttu-id="0bc4c-735">NX_PTR_ERROR: (0x16) puntero DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-735">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="0bc4c-736">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-736">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0bc4c-737">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-737">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-738">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-738">Allowed From</span></span>

<span data-ttu-id="0bc4c-739">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-740">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-740">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
                                                  dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="0bc4c-741">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="0bc4c-741">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="0bc4c-742">Convierte cuatro bytes en ULONG.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-742">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-743">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-743">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="0bc4c-744">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-744">Description</span></span>

<span data-ttu-id="0bc4c-745">Este servicio convierte los cuatro caracteres a los que apunta “option_string_ptr” en un valor Long sin signo.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-745">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="0bc4c-746">Es especialmente útil cuando hay</span><span class="sxs-lookup"><span data-stu-id="0bc4c-746">It is especially useful when IP addresses are</span></span>  
<span data-ttu-id="0bc4c-747">presentes direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-747">present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-748">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-748">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-749">**option_string_ptr**: puntero a la cadena de opción recuperada previamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-749">**option_string_ptr**: Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-750">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-750">Return Values</span></span>

- <span data-ttu-id="0bc4c-751">**Value**: valor de los primeros cuatro bytes.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-751">**Value**: Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-752">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-752">Allowed From</span></span>

<span data-ttu-id="0bc4c-753">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-753">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-754">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-754">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="0bc4c-755">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="0bc4c-755">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="0bc4c-756">Establece la función de devolución de llamada para agregar opciones proporcionadas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-756">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="0bc4c-757">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-757">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
                                           UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                                                        UINT iface_index, 
                                                                        UINT message_type, 
                                                                        UCHAR *user_option_ptr, 
                                                                        UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="0bc4c-758">Descripción</span><span class="sxs-lookup"><span data-stu-id="0bc4c-758">Description</span></span>

<span data-ttu-id="0bc4c-759">Este servicio registra la función de devolución de llamada especificada para agregar las opciones proporcionadas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-759">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="0bc4c-760">Si se especifica la función de devolución de llamada, las aplicaciones pueden agregar al paquete opciones proporcionadas por el usuario mediante iface_index y message_type.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-760">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

>[!NOTE] 
> <span data-ttu-id="0bc4c-761">En la rutina del usuario.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-761">In user’s routine.</span></span> <span data-ttu-id="0bc4c-762">Las aplicaciones deben seguir el formato de las opciones de DHCP cuando se agregan opciones proporcionadas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-762">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="0bc4c-763">El tamaño total de las opciones de usuario debe ser menor o igual que user_option_length y actualizar user_option_length como la longitud de las opciones reales.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-763">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="0bc4c-764">Devuelve NX_TRUE si se agregan opciones correctamente; de lo contrario, devuelve NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-764">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0bc4c-765">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0bc4c-765">Input Parameters</span></span>

- <span data-ttu-id="0bc4c-766">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-766">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="0bc4c-767">**dhcp_user_option_add**: puntero a la opción Agregar función de usuario.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-767">**dhcp_user_option_add**: Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="0bc4c-768">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-768">Return Values</span></span>

- <span data-ttu-id="0bc4c-769">**NX_SUCCESS**: (0x00) devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-769">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>
- <span data-ttu-id="0bc4c-770">NX_PTR_ERROR (0x16): puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="0bc4c-770">NX_PTR_ERROR: (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0bc4c-771">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0bc4c-771">Allowed From</span></span>

<span data-ttu-id="0bc4c-772">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0bc4c-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0bc4c-773">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0bc4c-773">Example</span></span>

```c
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created.  */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered.  */

```

