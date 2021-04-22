---
title: 'Capítulo 3: Descripción de los servicios de cliente DHCP de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios DHCP de Azure RTOS NetX (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815250"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a><span data-ttu-id="26e20-103">Capítulo 3: Descripción de los servicios de cliente DHCP de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="26e20-103">Chapter 3 - Description of Azure RTOS NetX DHCP Client services</span></span>

<span data-ttu-id="26e20-104">Este capítulo contiene una descripción de todos los servicios DHCP de Azure RTOS NetX (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="26e20-104">This chapter contains a description of all Azure RTOS NetX DHCP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="26e20-105">En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="26e20-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="26e20-106">**nx_dhcp_create**: *crea una instancia de DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>

- <span data-ttu-id="26e20-107">**nx_dhcp_clear_broadcast_flag**: borra la marca de difusión en mensajes de cliente.</span><span class="sxs-lookup"><span data-stu-id="26e20-107">**nx_dhcp_clear_broadcast_flag**: Clear broadcast flag on Client messages</span></span>

- <span data-ttu-id="26e20-108">**nx_dhcp_delete**: *elimina una instancia de DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>

- <span data-ttu-id="26e20-109">**nx_dhcp_decline**: envía un *mensaje de rechazo al servidor*.</span><span class="sxs-lookup"><span data-stu-id="26e20-109">**nx_dhcp_decline**: Send *Decline message to server*</span></span>

- <span data-ttu-id="26e20-110">**nx_dhcp_force_renew**: *envía un mensaje para forzar la renovación*.</span><span class="sxs-lookup"><span data-stu-id="26e20-110">**nx_dhcp_force_renew**: *Send force renew message*</span></span>

- <span data-ttu-id="26e20-111">**nx_dhcp_packet_pool_set**: *establece el grupo de paquetes de cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-111">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>

- <span data-ttu-id="26e20-112">**nx_dhcp_release**: envía un *mensaje de liberación al servidor*.</span><span class="sxs-lookup"><span data-stu-id="26e20-112">**nx_dhcp_release**: Send *Release message to server*</span></span>

- <span data-ttu-id="26e20-113">**nx_dhcp_reinitialize**: *borra los parámetros de red de cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>

- <span data-ttu-id="26e20-114">**nx_dhcp_request_client_ip**: *especifica una dirección IP concreta*.</span><span class="sxs-lookup"><span data-stu-id="26e20-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>

- <span data-ttu-id="26e20-115">**nx_dhcp_send_request**: *envía un mensaje DHCP al servidor*.</span><span class="sxs-lookup"><span data-stu-id="26e20-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>

- <span data-ttu-id="26e20-116">**nx_dhcp_server_address_get**: *recupera la dirección del servidor DHCP del cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-116">**nx_dhcp_server_address_get**: *Retrieve DHCP Client’s DHCP server address*</span></span>

- <span data-ttu-id="26e20-117">**nx_dhcp_set_interface_index**: *especifica la interfaz de red de cliente*.</span><span class="sxs-lookup"><span data-stu-id="26e20-117">**nx_dhcp_set_interface_index**: *Specify the Client network interface*</span></span>

- <span data-ttu-id="26e20-118">**nx_dhcp_start**: *inicia el procesamiento de DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-118">**nx_dhcp_start**: *Start DHCP processing*</span></span>

- <span data-ttu-id="26e20-119">**nx_dhcp_state_change_notify**: *notifica a la aplicación el cambio de estado de DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-119">**nx_dhcp_state_change_notify**: *Notify application of DHCP state change*</span></span>

- <span data-ttu-id="26e20-120">**nx_dhcp_stop**: *detiene el procesamiento de DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-120">**nx_dhcp_stop**: *Stop DHCP processing*</span></span>

- <span data-ttu-id="26e20-121">**nx_dhcp_user_option_retrieve**: *recupera la opción DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-121">**nx_dhcp_user_option_retrieve**: *Retrieve DHCP option*</span></span>

- <span data-ttu-id="26e20-122">**nx_dhcp_user_option_convert**: *convierte cuatro bytes a ULONG*.</span><span class="sxs-lookup"><span data-stu-id="26e20-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="26e20-123">Servicios de cliente DHCP específicos de la interfaz:</span><span class="sxs-lookup"><span data-stu-id="26e20-123">Interface specific DHCP Client services:</span></span>

- <span data-ttu-id="26e20-124">**nx_dhcp_interface_clear_broadcast_flag**: *borra la marca de difusión en mensajes de cliente en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>

- <span data-ttu-id="26e20-125">**nx_dhcp_interface_enable**: *habilita la interfaz para ejecutar DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="26e20-126">**nx_dhcp_interface_disable**: *deshabilita la interfaz para ejecutar DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="26e20-127">**nx_dhcp_interface_decline**: *envía un mensaje de rechazo al servidor en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>

- <span data-ttu-id="26e20-128">**nx_dhcp_interface_force_renew**: *envía un mensaje para forzar la renovación en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>

- <span data-ttu-id="26e20-129">**nx_dhcp_interface_reinitialize**: *borra parámetros de red de cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>

- <span data-ttu-id="26e20-130">**nx_dhcp_interface_release**: *envía un mensaje de liberación al servidor en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-130">**nx_dhcp_interface_release**: *Send Release message to server  on the specified interface*</span></span>

- <span data-ttu-id="26e20-131">**nx_dhcp_interface_request_client_ip**: *especifica una dirección IP concreta en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>

- <span data-ttu-id="26e20-132">**nx_dhcp_interface_send_request**: *envía un mensaje DHCP al servidor en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>

- <span data-ttu-id="26e20-133">**nx_dhcp_interface_server_address_get**: *obtiene la dirección IP del servidor DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>

- <span data-ttu-id="26e20-134">**nx_dhcp_interface_start**: *inicia el procesamiento de cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="26e20-135">**nx_dhcp_interface_stop**: *detiene el procesamiento de cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="26e20-136">**nx_dhcp_interface_state_change_notify**: *establece la función de devolución de llamada cuando el estado de DHCP cambia en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>

- <span data-ttu-id="26e20-137">**nx_dhcp_interface_user_option_retrieve**: *recupera la opción DHCP especificada en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="26e20-138">Servicios de cliente DHCP si se define NX_DHCP_CLIENT_RESORE_STATE:</span><span class="sxs-lookup"><span data-stu-id="26e20-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="26e20-139">**nx_dhcp_resume**: *reanuda el estado del cliente DHCP previamente establecido*.</span><span class="sxs-lookup"><span data-stu-id="26e20-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>

- <span data-ttu-id="26e20-140">**nx_dhcp_suspend**: *suspende el procesamiento del estado del cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>

- <span data-ttu-id="26e20-141">**nx_dhcp_client_get_record**: *crea un registro del estado del cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>

- <span data-ttu-id="26e20-142">**nx_dhcp_client_restore_record**: *restaura un registro guardado previamente en el cliente DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>

- <span data-ttu-id="26e20-143">**nx_dhcp_client_update_time_remaining**: *actualiza el tiempo restante en el estado actual de DHCP*.</span><span class="sxs-lookup"><span data-stu-id="26e20-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="26e20-144">Servicios de cliente DHCP si se define NX_DHCP_CLIENT_RESORE_STATE:</span><span class="sxs-lookup"><span data-stu-id="26e20-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="26e20-145">**nx_dhcp_client_interface_get_record**: *crea un registro del estado del cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>

- <span data-ttu-id="26e20-146">**nx_dhcp_client_interface_restore_record**: *crea un registro guardado previamente del estado del cliente DHCP en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>

- <span data-ttu-id="26e20-147">**nx_dhcp_client_interface_update_time_remaining**: *actualiza el tiempo restante en el estado DHCP actual en la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="26e20-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="26e20-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="26e20-148">nx_dhcp_create</span></span>

<span data-ttu-id="26e20-149">Crea una instancia de DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-150">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-150">Prototype</span></span>

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-151">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-151">Description</span></span>

<span data-ttu-id="26e20-152">Este servicio crea una instancia de DHCP para la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="26e20-153">De forma predeterminada, la interfaz principal está habilitada para ejecutar DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="26e20-154">La entrada del nombre, aunque no se usa en la implementación de cliente DHCP de NetX, debe seguir los criterios de la RFC 1035 para los nombres de hosts.</span><span class="sxs-lookup"><span data-stu-id="26e20-154">The name input, while not used in the NetX implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="26e20-155">La longitud total no debe superar los 255 caracteres, las etiquetas separadas por puntos deben comenzar con una letra y terminar con una letra o un número, y pueden contener guiones pero no otros caracteres no alfanuméricos.</span><span class="sxs-lookup"><span data-stu-id="26e20-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="26e20-156">Si la aplicación desea ejecutar otra interfaz de DHCP registrada con la instancia de IP (mediante *nx_ip_interface_attach*), puede llamar a *nx_dhcp_set_interface_index* para ejecutar DHCP solo en esa interfaz o *nx_dhcp_interface_enable* para ejecutar DHCP también en esa interfaz.</span><span class="sxs-lookup"><span data-stu-id="26e20-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="26e20-157">Consulte la descripción de estos servicios para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="26e20-157">See description of these services for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="26e20-158">La aplicación debe asegurarse de que la carga del grupo de paquetes del cliente DHCP pueda admitir el tamaño mínimo del mensaje DHCP especificado en la sección 2 de la RFC 2131 (548 bytes de datos de mensajes DHCP más UDP, IP y los encabezados de trama de la red física).</span><span class="sxs-lookup"><span data-stu-id="26e20-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-159">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-159">Input Parameters</span></span>

- <span data-ttu-id="26e20-160">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-160">**dhcp_ptr** Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="26e20-161">**ip_ptr** Puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-161">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="26e20-162">**name_ptr** Puntero al nombre de host de la instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-162">**name_ptr** Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-163">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-163">Return Values</span></span>

- <span data-ttu-id="26e20-164">**NX_SUCCESS** (0x00) DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-164">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="26e20-165">**NX_DHCP_INVALID_NAME** (0xA8) Nombre de host no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-165">**NX_DHCP_INVALID_NAME** (0xA8) Invalid host name</span></span>

- <span data-ttu-id="26e20-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) Carga demasiado pequeña para el mensaje DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) Payload too small for DHCP message</span></span>

- <span data-ttu-id="26e20-167">NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-167">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-168">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-168">Allowed From</span></span>

<span data-ttu-id="26e20-169">**Subprocesos,** inicialización</span><span class="sxs-lookup"><span data-stu-id="26e20-169">**Threads,** Initialization</span></span>

### <a name="example"></a><span data-ttu-id="26e20-170">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-170">Example</span></span>

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="26e20-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="26e20-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="26e20-172">Habilita la interfaz especificada para ejecutar DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="26e20-173">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-173">Prototype</span></span>

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="26e20-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-174">Description</span></span>

<span data-ttu-id="26e20-175">Este servicio permite que la interfaz especificada ejecute DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="26e20-176">De forma predeterminada, la interfaz principal está habilitada para el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="26e20-177">En este punto, se puede iniciar DHCP en esta interfaz llamando a *nx_dhcp_interface_start* o hacerlo en todas las interfaces habilitadas con *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="26e20-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

<span data-ttu-id="26e20-178">Tenga en cuenta que la aplicación debe registrar primero esta interfaz con la instancia de IP mediante *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="26e20-178">Note the application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="26e20-179">Además, debe haber un “registro” de interfaz de cliente DHCP disponible para agregar esta interfaz a la lista de interfaces habilitadas.</span><span class="sxs-lookup"><span data-stu-id="26e20-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="26e20-180">De forma predeterminada NX_DHCP_CLIENT_MAX_RECORDS se define como 1.</span><span class="sxs-lookup"><span data-stu-id="26e20-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="26e20-181">Establezca esta opción en el número máximo de interfaces que se espera que ejecute el cliente DHCP simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="26e20-182">Normalmente NX_DHCP_CLIENT_MAX_RECORDS será igual a NX_MAX_PHYSICAL_INTERFACES; sin embargo, si un dispositivo tiene más interfaces físicas de las que espera ejecutar el cliente DHCP, puede ahorrar memoria si establece NX_DHCP_CLIENT_MAX_RECORDS en un valor inferior a ese número.</span><span class="sxs-lookup"><span data-stu-id="26e20-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="26e20-183">No hay una asignación uno a uno de las interfaces físicas con los registros de la interfaz de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="26e20-184">La diferencia entre este servicio y *nx_dhcp_set_interface_index* es que el segundo establece una única interfaz para ejecutar DHCP, mientras que este servicio simplemente agrega la interfaz especificada a la lista de interfaces de cliente habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="26e20-185">Para deshabilitar una interfaz de DHCP, la aplicación puede llamar al servicio *nx_dhcp_interface_disable*.</span><span class="sxs-lookup"><span data-stu-id="26e20-185">To disable an interface for DHCP, the application can call the *nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-186">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-186">Input Parameters</span></span>

- <span data-ttu-id="26e20-187">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-187">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="26e20-188">**interface_index** Índice de interfaz para habilitar DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-188">**interface_index** Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-189">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-189">Return Values</span></span>

- <span data-ttu-id="26e20-190">**NX_SUCCESS** (0x00) DHCP habilitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-190">**NX_SUCCESS** (0x00) Successful DHCP enable</span></span>

- <span data-ttu-id="26e20-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No hay ningún registro disponible para poder habilitar otra interfaz para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another Interface to be enabled for DHCP</span></span>

- <span data-ttu-id="26e20-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interfaz habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="26e20-193">NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-193">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="26e20-194">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-194">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-195">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-195">Allowed From</span></span>

<span data-ttu-id="26e20-196">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="26e20-196">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="26e20-197">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-197">Example</span></span>

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="26e20-198">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="26e20-198">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="26e20-199">Deshabilita la interfaz especificada para ejecutar DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-199">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="26e20-200">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-200">Prototype</span></span>

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="26e20-201">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-201">Description</span></span>

<span data-ttu-id="26e20-202">Este servicio impide que la interfaz especificada ejecute DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-202">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="26e20-203">Reinicializa el cliente DHCP en esta interfaz.</span><span class="sxs-lookup"><span data-stu-id="26e20-203">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="26e20-204">Para reiniciar el cliente DHCP, la aplicación debe volver a habilitar la interfaz mediante *nx_dhcp_interface_enable* y reiniciar DHCP llamando a *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="26e20-204">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-205">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-205">Input Parameters</span></span>

- <span data-ttu-id="26e20-206">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-206">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="26e20-207">**interface_index** Índice de interfaz para deshabilitar DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-207">**interface_index** Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-208">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-208">Return Values</span></span>

- <span data-ttu-id="26e20-209">**NX_SUCCESS** (0x00) DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-209">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="26e20-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="26e20-211">NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-211">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="26e20-212">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-212">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="26e20-213">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-213">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-214">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-214">Allowed From</span></span>

<span data-ttu-id="26e20-215">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-216">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-216">Example</span></span>

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="26e20-217">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="26e20-217">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="26e20-218">Establece la marca de difusión de DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-218">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-219">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-219">Prototype</span></span>

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="26e20-220">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-220">Description</span></span>

<span data-ttu-id="26e20-221">Este servicio establece o borra la marca de difusión del encabezado del mensaje DHCP de todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-221">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="26e20-222">En el caso de algunos mensajes DHCP (por ejemplo, DISCOVER), la marca de difusión se establece en “difundir” porque el cliente no tiene una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="26e20-222">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="26e20-223">__clear_flag__</span><span class="sxs-lookup"><span data-stu-id="26e20-223">__clear_flag__</span></span>


- <span data-ttu-id="26e20-224">**NX_TRUE** La marca de difusión se borra (solicitud de respuesta de unidifusión).</span><span class="sxs-lookup"><span data-stu-id="26e20-224">**NX_TRUE** broadcast flag is cleared (request unicast response)</span></span>

- <span data-ttu-id="26e20-225">**NX_TRUE** La marca de difusión se establece (solicitud de respuesta de unidifusión).</span><span class="sxs-lookup"><span data-stu-id="26e20-225">**NX_FALSE** broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="26e20-226">Este servicio está dirigido a los clientes DHCP que deben pasar por un enrutador para llegar al servidor DHCP, donde el enrutador rechaza el reenvío de mensajes de difusión.</span><span class="sxs-lookup"><span data-stu-id="26e20-226">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-227">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-227">Input Parameters</span></span>

- <span data-ttu-id="26e20-228">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-228">**dhcp_ptr** Pointer to DHCP control block</span></span>  

- <span data-ttu-id="26e20-229">**clear_flag** Valor en el que se va a establecer la marca de difusión.</span><span class="sxs-lookup"><span data-stu-id="26e20-229">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-230">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-230">Return Values</span></span>

- <span data-ttu-id="26e20-231">**NX_SUCCESS** (0x00) Marca de difusión actualizada correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-231">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="26e20-232">NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-232">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="26e20-233">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-233">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-234">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-234">Allowed From</span></span>

<span data-ttu-id="26e20-235">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="26e20-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="26e20-236">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-236">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="26e20-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="26e20-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="26e20-238">Establece o borra la marca de difusión en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-239">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-239">Prototype</span></span>

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="26e20-240">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-240">Description</span></span>

<span data-ttu-id="26e20-241">Este servicio permite que la aplicación host de cliente DHCP establezca o borre la marca de difusión en los mensajes de cliente DHCP en el servidor DHCP de la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="26e20-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="26e20-242">Para obtener más información, consulte **nx_dhcp_clear_broadcast_flag**.</span><span class="sxs-lookup"><span data-stu-id="26e20-242">For more details see **nx_dhcp_clear_broadcast_flag**</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-243">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-243">Input Parameters</span></span>

- <span data-ttu-id="26e20-244">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-244">**dhcp_ptr** Pointer to DHCP control block</span></span>

- <span data-ttu-id="26e20-245">**interface_index** Índice de la interfaz para establecer la marca de difusión.</span><span class="sxs-lookup"><span data-stu-id="26e20-245">**interface_index** Index of interface to set the broadcast flag</span></span>  

- <span data-ttu-id="26e20-246">**clear_flag** Valor en el que se va a establecer la marca de difusión.</span><span class="sxs-lookup"><span data-stu-id="26e20-246">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-247">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-247">Return Values</span></span>

- <span data-ttu-id="26e20-248">**NX_SUCCESS** (0x00) Marca de difusión actualizada correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-248">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="26e20-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="26e20-250">NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-250">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="26e20-251">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-251">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-252">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-252">Allowed From</span></span>

<span data-ttu-id="26e20-253">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="26e20-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="26e20-254">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-254">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="26e20-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="26e20-255">nx_dhcp_delete</span></span>

<span data-ttu-id="26e20-256">Elimina una instancia de DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-257">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-257">Prototype</span></span>

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-258">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-258">Description</span></span>

<span data-ttu-id="26e20-259">Este servicio elimina una instancia de cliente DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-260">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-260">Input Parameters</span></span>

- <span data-ttu-id="26e20-261">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-261">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-262">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-262">Return Values</span></span>

- <span data-ttu-id="26e20-263">**NX_SUCCESS** (0x00) DHCP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-263">**NX_SUCCESS** (0x00) Successful DHCP delete.</span></span>

- <span data-ttu-id="26e20-264">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-264">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="26e20-265">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-265">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-266">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-266">Allowed From</span></span>

<span data-ttu-id="26e20-267">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-268">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-268">Example</span></span>

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="26e20-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="26e20-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="26e20-270">Envía un mensaje para forzar la renovación</span><span class="sxs-lookup"><span data-stu-id="26e20-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="26e20-271">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-271">Prototype</span></span>

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-272">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-272">Description</span></span>

<span data-ttu-id="26e20-273">Este servicio permite que la aplicación host envíe un mensaje para forzar la renovación en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="26e20-274">El cliente DHCP debe estar en un estado ENLAZADO.</span><span class="sxs-lookup"><span data-stu-id="26e20-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="26e20-275">Esta función establece el estado en RENOVAR, de modo que el cliente DHCP intente renovar antes de que venza el tiempo de espera de T1.</span><span class="sxs-lookup"><span data-stu-id="26e20-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="26e20-276">Si quiere enviar un mensaje para forzar la renovación en una interfaz específica cuando hay varias interfaces habilitadas para DHCP, use *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="26e20-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-277">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-277">Input Parameters</span></span>

- <span data-ttu-id="26e20-278">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-278">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-279">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-279">Return Values</span></span>

- <span data-ttu-id="26e20-280">**NX_SUCCESS** (0x00) Mensaje para forzar la renovación enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-280">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="26e20-281">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-281">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="26e20-282">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-282">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-283">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-283">Allowed From</span></span>

<span data-ttu-id="26e20-284">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-285">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-285">Example</span></span>

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="26e20-286">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="26e20-286">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="26e20-287">Envía un mensaje para forzar la renovación en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-287">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-288">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-288">Prototype</span></span>

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="26e20-289">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-289">Description</span></span>

<span data-ttu-id="26e20-290">Este servicio permite que la aplicación host envíe un mensaje para forzar la renovación en la interfaz de entrada, siempre y cuando esa interfaz se haya habilitado para DHCP (consulte *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="26e20-290">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="26e20-291">El cliente DHCP de la interfaz especificada debe estar en un estado ENLAZADO.</span><span class="sxs-lookup"><span data-stu-id="26e20-291">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="26e20-292">Esta función establece el estado en RENOVAR, de modo que el cliente DHCP intente renovar antes de que venza el tiempo de espera de T1.</span><span class="sxs-lookup"><span data-stu-id="26e20-292">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-293">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-293">Input Parameters</span></span>

- <span data-ttu-id="26e20-294">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-294">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-295">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-295">Return Values</span></span>

- <span data-ttu-id="26e20-296">**NX_SUCCESS** (0x00) Mensaje para forzar la renovación enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-296">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="26e20-297">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-297">**NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="26e20-298">NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-298">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="26e20-299">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-299">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-300">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-300">Allowed From</span></span>

<span data-ttu-id="26e20-301">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-302">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-302">Example</span></span>

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="26e20-303">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="26e20-303">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="26e20-304">Establece el grupo de paquetes del cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-304">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-305">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-305">Prototype</span></span>

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-306">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-306">Description</span></span>

<span data-ttu-id="26e20-307">Este servicio permite que la aplicación cree el grupo de paquetes de cliente DHCP pasando un puntero a un grupo de paquetes creado previamente en esta llamada de servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-307">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="26e20-308">Para usar esta característica, la aplicación host debe definir NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="26e20-308">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="26e20-309">Una vez definido el parámetro, el servicio *nx_dhcp_create* no creará el grupo de paquetes de cliente.</span><span class="sxs-lookup"><span data-stu-id="26e20-309">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> <span data-ttu-id="26e20-310">Tenga en cuenta que se recomienda que la aplicación use los valores predeterminados para la carga del grupo de paquetes de cliente DHCP, definido como NX_DHCP_PACKET_PAYLOAD en *nx_dhcp.h* al crear el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="26e20-310">Note that the application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nx_dhcp.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-311">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-311">Input Parameters</span></span>

- <span data-ttu-id="26e20-312">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-312">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="26e20-313">**packet_pool_ptr** Puntero al grupo de paquetes creado previamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-313">**packet_pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-314">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-314">Return Values</span></span>

- <span data-ttu-id="26e20-315">**NX_SUCCESS** (0x00) Grupo de paquetes del cliente DHCP establecido.</span><span class="sxs-lookup"><span data-stu-id="26e20-315">**NX_SUCCESS** (0x00) DHCP Client packet pool is set</span></span>

- <span data-ttu-id="26e20-316">**NX_NOT_ENABLED** (0x14) El servicio no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="26e20-316">**NX_NOT_ENABLED** (0x14) Service is not enabled</span></span>

- <span data-ttu-id="26e20-317">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-317">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="26e20-318">NX_DHCP_INVALID_PAYLOAD (0x9C) La carga es demasiado pequeña.</span><span class="sxs-lookup"><span data-stu-id="26e20-318">NX_DHCP_INVALID_PAYLOAD (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-319">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-319">Allowed From</span></span>

<span data-ttu-id="26e20-320">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="26e20-320">Application code</span></span>

### <a name="example"></a><span data-ttu-id="26e20-321">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-321">Example</span></span>

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="26e20-322">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="26e20-322">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="26e20-323">Establece la dirección IP solicitada para la instancia de DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-323">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-324">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-324">Prototype</span></span>

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="26e20-325">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-325">Description</span></span>

<span data-ttu-id="26e20-326">Este servicio establece la dirección IP que el cliente DHCP debe solicitar al servidor DHCP en la primera interfaz habilitada para DHCP en el registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-326">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="26e20-327">Si se establece la marca *skip_discover_message*, el cliente DHCP omite el mensaje de detección y envía un mensaje de solicitud.</span><span class="sxs-lookup"><span data-stu-id="26e20-327">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="26e20-328">Para establecer la solicitud de una dirección IP específica para mensajes DHCP en una interfaz concreta, use el servicio *nx_dhcp_interface_request_client_ip*.</span><span class="sxs-lookup"><span data-stu-id="26e20-328">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-329">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-329">Input Parameters</span></span>

- <span data-ttu-id="26e20-330">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-330">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="26e20-331">**client_ip_address** Dirección IP que se va a solicitar del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-331">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="26e20-332">**skip_discover_message** Si es verdadero, el cliente DHCP envía un mensaje de solicitud.</span><span class="sxs-lookup"><span data-stu-id="26e20-332">**skip_discover_message** If true, DHCP Client sends Request message</span></span>  
<span data-ttu-id="26e20-333">Si es falso, envía el mensaje de detección.</span><span class="sxs-lookup"><span data-stu-id="26e20-333">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-334">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-334">Return Values</span></span>

- <span data-ttu-id="26e20-335">**NX_SUCCESS** (0x00) La dirección IP solicitada se ha establecido.</span><span class="sxs-lookup"><span data-stu-id="26e20-335">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="26e20-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="26e20-337">NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-337">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="26e20-338">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-338">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="26e20-339">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-339">Allowed From</span></span>

<span data-ttu-id="26e20-340">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-340">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-341">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-341">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="26e20-342">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="26e20-342">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="26e20-343">Establece la dirección IP solicitada para la instancia de DHCP en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-343">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-344">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-344">Prototype</span></span>

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="26e20-345">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-345">Description</span></span>

<span data-ttu-id="26e20-346">Este servicio establece la dirección IP que el cliente DHCP debe solicitar al servidor DHCP en la interfaz especificada, si dicha interfaz está habilitada para DHCP (consulte *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="26e20-346">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="26e20-347">Si se establece la marca *skip_discover_message*, el cliente DHCP omite el mensaje de detección y envía un mensaje de solicitud.</span><span class="sxs-lookup"><span data-stu-id="26e20-347">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-348">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-348">Input Parameters</span></span>

- <span data-ttu-id="26e20-349">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-349">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="26e20-350">**Interface_index** Índice de la interfaz en la que se va a solicitar la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="26e20-350">**Interface_index** Index of interface to request IP address on</span></span>

- <span data-ttu-id="26e20-351">**client_ip_address** Dirección IP que se va a solicitar del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-351">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="26e20-352">**skip_discover_message** Si es verdadero, el cliente DHCP envía el mensaje de solicitud; de lo contrario, envía el mensaje de detección.</span><span class="sxs-lookup"><span data-stu-id="26e20-352">**skip_discover_message** If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-353">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-353">Return Values</span></span>

- <span data-ttu-id="26e20-354">**NX_SUCCESS** (0x00) La dirección IP solicitada se ha establecido.</span><span class="sxs-lookup"><span data-stu-id="26e20-354">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="26e20-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="26e20-356">NX_PTR_ERROR (0x16) Puntero IP o DHCP no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-356">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="26e20-357">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-357">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>


### <a name="allowed-from"></a><span data-ttu-id="26e20-358">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-358">Allowed From</span></span>

<span data-ttu-id="26e20-359">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-360">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-360">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="26e20-361">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="26e20-361">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="26e20-362">Borra los parámetros de red del cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-362">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="26e20-363">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-363">Prototype</span></span>

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-364">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-364">Description</span></span>

<span data-ttu-id="26e20-365">Este servicio borra los parámetros de red de la aplicación host (dirección IP, dirección de red y máscara de red) y borra el estado del cliente DHCP en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-365">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="26e20-366">Se usa en combinación con *nx_dhcp_stop* y *nx_dhcp_start* para “reiniciar” la máquina de estados de DHCP:</span><span class="sxs-lookup"><span data-stu-id="26e20-366">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span> 

<span data-ttu-id="26e20-367">nx_dhcp_stop(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="26e20-367">nx_dhcp_stop(&my_dhcp);</span></span>  
<span data-ttu-id="26e20-368">nx_dhcp_reinitialize(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="26e20-368">nx_dhcp_reinitialize(&my_dhcp);</span></span>  
<span data-ttu-id="26e20-369">nx_dhcp_start(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="26e20-369">nx_dhcp_start(&my_dhcp);</span></span>


<span data-ttu-id="26e20-370">Para reinicializar el cliente DHCP en una interfaz específica cuando hay varias interfaces habilitadas para DHCP, use el servicio *nx_dhcp_interface_reinitialize*.</span><span class="sxs-lookup"><span data-stu-id="26e20-370">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-371">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-371">Input Parameters</span></span>

- <span data-ttu-id="26e20-372">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-372">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-373">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-373">Return Values</span></span>

- <span data-ttu-id="26e20-374">**NX_SUCCESS** (0X00) DHCP reinicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-374">**NX_SUCCESS** (0x00) DHCP successfully reinitialized</span></span> 

- <span data-ttu-id="26e20-375">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-375">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-376">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-376">Allowed From</span></span>

<span data-ttu-id="26e20-377">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-377">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-378">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-378">Example</span></span>

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="26e20-379">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="26e20-379">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="26e20-380">Borra los parámetros de red del cliente DHCP en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-380">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="26e20-381">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-381">Prototype</span></span>

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="26e20-382">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-382">Description</span></span>

<span data-ttu-id="26e20-383">Este servicio borra los parámetros de red (dirección IP, dirección de red y máscara de red) en la interfaz especificada si dicha interfaz está habilitada para DHCP (consulte *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="26e20-383">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="26e20-384">Consulte *nx_dhcp_reinitialize* para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="26e20-384">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-385">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-385">Input Parameters</span></span>

- <span data-ttu-id="26e20-386">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-386">**dhcp_ptr** Pointer to previously created DHCP instance</span></span>

- <span data-ttu-id="26e20-387">**interface_index** Índice de interfaz para reinicializar.</span><span class="sxs-lookup"><span data-stu-id="26e20-387">**interface_index** Index of interface to reinitialize.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-388">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-388">Return Values</span></span>

- <span data-ttu-id="26e20-389">**NX_SUCCESS** (0x00) Interfaz reinicializada correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-389">**NX_SUCCESS** (0x00) Interface successfully reinitialized</span></span>

- <span data-ttu-id="26e20-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="26e20-391">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-391">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="26e20-392">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-392">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="26e20-393">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-393">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-394">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-394">Allowed From</span></span>

<span data-ttu-id="26e20-395">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-395">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-396">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-396">Example</span></span>

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="26e20-397">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="26e20-397">nx_dhcp_release</span></span>

<span data-ttu-id="26e20-398">Libera la dirección IP concedida</span><span class="sxs-lookup"><span data-stu-id="26e20-398">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-399">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-399">Prototype</span></span>

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-400">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-400">Description</span></span>

<span data-ttu-id="26e20-401">Este servicio libera la dirección IP obtenida de un servidor DHCP mediante el envío del mensaje RELEASE a dicho servidor.</span><span class="sxs-lookup"><span data-stu-id="26e20-401">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="26e20-402">Seguidamente, reinicializa el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-402">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="26e20-403">Este servicio se aplica a todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-403">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="26e20-404">La aplicación puede reiniciar el cliente DHCP llamando a *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="26e20-404">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="26e20-405">Para volver a liberar una dirección en el servidor DHCP en una interfaz específica, use el servicio *nx_dhcp_interface_release*.</span><span class="sxs-lookup"><span data-stu-id="26e20-405">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-406">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-406">Input Parameters</span></span>

- <span data-ttu-id="26e20-407">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-407">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-408">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-408">Return Values</span></span>

- <span data-ttu-id="26e20-409">**NX_SUCCESS** (0x00) DHCP liberado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-409">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>  

- <span data-ttu-id="26e20-410">**NX_DHCP_NOT_BOUND** (0x94) No se ha concedido la dirección IP, por lo que no se puede liberar.</span><span class="sxs-lookup"><span data-stu-id="26e20-410">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="26e20-411">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-411">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="26e20-412">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-412">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-413">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-413">Allowed From</span></span>

<span data-ttu-id="26e20-414">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-414">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-415">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-415">Example</span></span>

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="26e20-416">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="26e20-416">nx_dhcp_interface_release</span></span>

<span data-ttu-id="26e20-417">Libera la dirección IP en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-417">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-418">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-418">Prototype</span></span>

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="26e20-419">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-419">Description</span></span>

<span data-ttu-id="26e20-420">Este servicio libera la dirección IP obtenida de un servidor DHCP en la interfaz especificada y reinicializa el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-420">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="26e20-421">El cliente DHCP puede reiniciarse mediante una llamada a *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="26e20-421">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-422">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-422">Input Parameters</span></span>

- <span data-ttu-id="26e20-423">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-423">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-424">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-424">Return Values</span></span>

- <span data-ttu-id="26e20-425">**NX_SUCCESS** (0x00) DHCP liberado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-425">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>

- <span data-ttu-id="26e20-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="26e20-427">**NX_DHCP_NOT_BOUND** (0x94) No se ha concedido la dirección IP, por lo que no se puede liberar.</span><span class="sxs-lookup"><span data-stu-id="26e20-427">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="26e20-428">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-428">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="26e20-429">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-429">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="26e20-430">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-430">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-431">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-431">Allowed From</span></span>

<span data-ttu-id="26e20-432">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-432">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-433">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-433">Example</span></span>

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="26e20-434">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="26e20-434">nx_dhcp_decline</span></span>

<span data-ttu-id="26e20-435">Rechaza la dirección IP del servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-435">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-436">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-436">Prototype</span></span>

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-437">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-437">Description</span></span>

<span data-ttu-id="26e20-438">Este servicio rechaza una dirección IP concedida desde el servidor DHCP en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-438">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="26e20-439">Si se define NX_DHCP_CLIENT_ SEND_ ARP_PROBE, el cliente DHCP enviará un mensaje de rechazo si detecta que la dirección IP ya está en uso.</span><span class="sxs-lookup"><span data-stu-id="26e20-439">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="26e20-440">Consulte **Sondeos ARP** en el capítulo 1 para obtener más información sobre la configuración de sondeo ARP en el cliente DHCP de NetX.</span><span class="sxs-lookup"><span data-stu-id="26e20-440">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX DHCP Client.</span></span>

<span data-ttu-id="26e20-441">La aplicación puede usar este servicio para rechazar su dirección IP si detecta que la dirección se está usando por otros medios.</span><span class="sxs-lookup"><span data-stu-id="26e20-441">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="26e20-442">Este servicio reinicializa el cliente DHCP para que se pueda reiniciar mediante una llamada a *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="26e20-442">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-443">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-443">Input Parameters</span></span>

- <span data-ttu-id="26e20-444">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-444">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-445">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-445">Return Values</span></span>

- <span data-ttu-id="26e20-446">**NX_SUCCESS** (0x00) Rechazo enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-446">**NX_SUCCESS** (0x00) Decline successfully sent</span></span>  

- <span data-ttu-id="26e20-447">**NX_DHCP_NOT_STARTED** (0x96) No se ha iniciado la instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-447">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started</span></span>

- <span data-ttu-id="26e20-448">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-448">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="26e20-449">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-449">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-450">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-450">Allowed From</span></span>

<span data-ttu-id="26e20-451">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-452">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-452">Example</span></span>

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="26e20-453">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="26e20-453">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="26e20-454">Rechaza la dirección IP del servidor DHCP en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-454">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-455">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-455">Prototype</span></span>

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="26e20-456">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-456">Description</span></span>

<span data-ttu-id="26e20-457">Este servicio envía el mensaje DECLINE al servidor para rechazar una dirección IP asignada por el servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-457">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="26e20-458">También reinicializa el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-458">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="26e20-459">Consulte *nx_dhcp_decline* para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="26e20-459">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-460">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-460">Input Parameters</span></span>

- <span data-ttu-id="26e20-461">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-461">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="26e20-462">**Interface_index** Índice de la interfaz para rechazar la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="26e20-462">**Interface_index** Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-463">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-463">Return Values</span></span>

- <span data-ttu-id="26e20-464">**NX_SUCCESS** (0x00) Mensaje de rechazo de DHCP enviado.</span><span class="sxs-lookup"><span data-stu-id="26e20-464">**NX_SUCCESS** (0x00) DHCP decline message sent</span></span>  

- <span data-ttu-id="26e20-465">**NX_DHCP_NOT_BOUND** (0x94) Cliente DHCP no enlazado.</span><span class="sxs-lookup"><span data-stu-id="26e20-465">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="26e20-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="26e20-467">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-467">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="26e20-468">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="26e20-469">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-469">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-470">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-470">Allowed From</span></span>

<span data-ttu-id="26e20-471">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-471">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-472">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-472">Example</span></span>
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a><span data-ttu-id="26e20-473">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="26e20-473">nx_dhcp_send_request</span></span>

<span data-ttu-id="26e20-474">Envía un mensaje DHCP al servidor</span><span class="sxs-lookup"><span data-stu-id="26e20-474">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-475">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-475">Prototype</span></span>

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="26e20-476">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-476">Description</span></span>

<span data-ttu-id="26e20-477">Este servicio envía el mensaje DHCP especificado al servidor DHCP en la primera interfaz habilitada para DHCP que se encuentra en el registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-477">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="26e20-478">Para enviar un mensaje RELEASE o DECLINE, la aplicación debe utilizar los servicios *nx_dhcp [_interface] _release*() o *nx_dhcp_interface_decline ()* , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-478">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="26e20-479">El cliente DHCP debe iniciarse para usar este servicio, salvo para enviar el tipo de mensaje INFORM_REQUEST.</span><span class="sxs-lookup"><span data-stu-id="26e20-479">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

> [!NOTE] 
> <span data-ttu-id="26e20-480">Este servicio no está destinado a que la aplicación host “impulse” la máquina de estados del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-480">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-481">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-481">Input Parameters</span></span>

- <span data-ttu-id="26e20-482">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-482">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="26e20-483">**dhcp_message_type** Solicitud de mensaje (definida en *nx_dhcp.h*)</span><span class="sxs-lookup"><span data-stu-id="26e20-483">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-484">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-484">Return Values</span></span>

- <span data-ttu-id="26e20-485">**NX_SUCCESS** (0x00) Mensaje DHCP enviado.</span><span class="sxs-lookup"><span data-stu-id="26e20-485">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="26e20-486">**NX_DHCP_NOT_STARTED** (0x96) Índice de interfaz no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-486">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="26e20-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) Tipo de mensaje no válido para enviar.</span><span class="sxs-lookup"><span data-stu-id="26e20-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="26e20-488">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-488">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-489">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-489">Allowed From</span></span>

<span data-ttu-id="26e20-490">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-491">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-491">Example</span></span>

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="26e20-492">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="26e20-492">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="26e20-493">Envía un mensaje DHCP al servidor en una interfaz específica</span><span class="sxs-lookup"><span data-stu-id="26e20-493">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-494">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-494">Prototype</span></span>

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="26e20-495">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-495">Description</span></span>

<span data-ttu-id="26e20-496">Este servicio envía un mensaje al servidor DHCP en la interfaz especificada si esa interfaz está habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-496">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="26e20-497">Para enviar un mensaje RELEASE o DECLINE, la aplicación debe utilizar los servicios *nx_dhcp [_interface] _release*() o *nx_dhcp_interface_decline ()* , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-497">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="26e20-498">El cliente DHCP debe iniciarse para usar este servicio, salvo para enviar el tipo de mensaje INFORM_REQUEST.</span><span class="sxs-lookup"><span data-stu-id="26e20-498">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="26e20-499">Este servicio no está destinado a que la aplicación host “impulse” la máquina de estados del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-499">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-500">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-500">Input Parameters</span></span>

- <span data-ttu-id="26e20-501">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-501">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="26e20-502">**Interface_index** Índice de la interfaz a la que se va a enviar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="26e20-502">**Interface_index** Index of interface to send message on</span></span>  

- <span data-ttu-id="26e20-503">**dhcp_message_type** Solicitud de mensaje (definida en *nx_dhcp.h*).</span><span class="sxs-lookup"><span data-stu-id="26e20-503">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-504">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-504">Return Values</span></span>

- <span data-ttu-id="26e20-505">**NX_SUCCESS** (0x00) Mensaje DHCP enviado.</span><span class="sxs-lookup"><span data-stu-id="26e20-505">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="26e20-506">**NX_DHCP_NOT_STARTED** (0x96) Índice de interfaz no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-506">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="26e20-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) Tipo de mensaje no válido para enviar.</span><span class="sxs-lookup"><span data-stu-id="26e20-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="26e20-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interfaz no habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="26e20-509">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-509">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="26e20-510">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-510">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="26e20-511">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-511">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-512">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-512">Allowed From</span></span>

<span data-ttu-id="26e20-513">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-513">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-514">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-514">Example</span></span>

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="26e20-515">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="26e20-515">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="26e20-516">Obtiene la dirección IP del servidor DHCP del cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-516">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-517">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-517">Prototype</span></span>

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="26e20-518">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-518">Description</span></span>

<span data-ttu-id="26e20-519">Este servicio recupera la dirección IP del servidor DHCP del cliente DHCP en la primera interfaz habilitada para DHCP que se encuentra en el registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-519">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="26e20-520">El autor de la llamada solo puede utilizar este servicio después de que el cliente DHCP se haya enlazado a una dirección IP asignada por el servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-520">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="26e20-521">La aplicación host puede usar el servicio *nx_ip_status_check* para comprobar que la dirección IP está establecida o usar *nx_dhcp_state_change_notify* y consultar si el estado del cliente DHCP es NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="26e20-521">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the *nx_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="26e20-522">Consulte *nx_dhcp_state_change_notify* para obtener información sobre cómo establecer la función de devolución de llamada de cambio de estado.</span><span class="sxs-lookup"><span data-stu-id="26e20-522">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="26e20-523">Para buscar el servidor DHCP en una interfaz específica cuando hay varias interfaces habilitadas para el cliente DHCP, use el servicio *nx_dhcp_interface_server_address_get*</span><span class="sxs-lookup"><span data-stu-id="26e20-523">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-524">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-524">Input Parameters</span></span>

- <span data-ttu-id="26e20-525">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-525">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="26e20-526">**server_address** Puntero a la dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="26e20-526">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-527">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-527">Return Values</span></span>

- <span data-ttu-id="26e20-528">**NX_SUCCESS** (0x00) Dirección del servidor DHCP devuelta.</span><span class="sxs-lookup"><span data-stu-id="26e20-528">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="26e20-529">NX_PTR_ERROR (0x16) El puntero de entrada no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-529">NX_PTR_ERROR (0x16) Invalid input pointer</span></span>

- <span data-ttu-id="26e20-530">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-530">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-531">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-531">Allowed From</span></span>

<span data-ttu-id="26e20-532">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-533">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-533">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="26e20-534">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="26e20-534">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="26e20-535">Obtiene la dirección IP del servidor DHCP del cliente DHCP en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-535">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-536">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-536">Prototype</span></span>

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="26e20-537">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-537">Description</span></span>

<span data-ttu-id="26e20-538">Este servicio recupera la dirección IP del servidor DHCP del cliente DHCP en la interfaz especificada si dicha interfaz está habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-538">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="26e20-539">El cliente DHCP debe estar en un estado ENLAZADO.</span><span class="sxs-lookup"><span data-stu-id="26e20-539">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="26e20-540">Después de iniciar el cliente DHCP en esa interfaz, la aplicación host puede usar el servicio *nx_ip_status_check* para comprobar que la dirección IP está establecida o bien usar la devolución de llamada de cambio de estado del cliente DHCP y consultar si el estado del cliente DHCP es NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="26e20-540">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="26e20-541">Consulte *nx_dhcp_state_change_notify* para obtener más información sobre cómo establecer la función de devolución de llamada de cambio de estado.</span><span class="sxs-lookup"><span data-stu-id="26e20-541">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-542">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-542">Input Parameters</span></span>

- <span data-ttu-id="26e20-543">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-543">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="26e20-544">**Interface_index** Índice de la interfaz para obtener la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="26e20-544">**Interface_index** Index of interface to obtain IP address</span></span>  

- <span data-ttu-id="26e20-545">**server_address** Puntero a la dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="26e20-545">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-546">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-546">Return Values</span></span>

- <span data-ttu-id="26e20-547">**NX_SUCCESS** (0x00) Dirección del servidor DHCP devuelta.</span><span class="sxs-lookup"><span data-stu-id="26e20-547">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="26e20-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No hay interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="26e20-549">**NX_DHCP_NOT_BOUND** (0x94) Cliente DHCP no enlazado.</span><span class="sxs-lookup"><span data-stu-id="26e20-549">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="26e20-550">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-550">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="26e20-551">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-551">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="26e20-552">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-552">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-553">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-553">Allowed From</span></span>

<span data-ttu-id="26e20-554">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-555">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-555">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="26e20-556">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="26e20-556">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="26e20-557">Establece la interfaz de red para la instancia de DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-557">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-558">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-558">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="26e20-559">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-559">Description</span></span>

<span data-ttu-id="26e20-560">Este servicio establece la interfaz de red para que la instancia de DHCP se conecte al servidor DHCP cuando se ejecuta el cliente DHCP configurado para una sola interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="26e20-560">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="26e20-561">De forma predeterminada, el cliente DHCP se ejecuta en la interfaz principal.</span><span class="sxs-lookup"><span data-stu-id="26e20-561">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="26e20-562">Para ejecutar DHCP en un servicio secundario, use este servicio para establecer la interfaz secundaria como la interfaz de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-562">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="26e20-563">La aplicación debe registrar previamente la interfaz especificada en la instancia de IP mediante el servicio de *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="26e20-563">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

<span data-ttu-id="26e20-564">Tenga en cuenta que este servicio está pensado para las aplicaciones que tienen previsto ejecutar el cliente DHCP en una sola interfaz.</span><span class="sxs-lookup"><span data-stu-id="26e20-564">Note that this service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="26e20-565">Para ejecutar DHCP en varias interfaces, consulte *nx_dhcp_interface_enable* para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="26e20-565">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-566">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-566">Input Parameters</span></span>

- <span data-ttu-id="26e20-567">**dhcp_ptr** Puntero al bloque de control de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-567">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="26e20-568">**index** Índice de la interfaz de red del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="26e20-568">**index** Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-569">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-569">Return Values</span></span>

- <span data-ttu-id="26e20-570">**NX_SUCCESS** (0x00) La interfaz se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-570">**NX_SUCCESS** (0x00) Interface is successfully set.</span></span>

- <span data-ttu-id="26e20-571">**NX_INVALID_INTERFACE** (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-571">**NX_INVALID_INTERFACE** (0x4C) Invalid network interface</span></span>

- <span data-ttu-id="26e20-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interfaz habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="26e20-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No hay ningún registro disponible para otro.</span><span class="sxs-lookup"><span data-stu-id="26e20-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another</span></span>

- <span data-ttu-id="26e20-574">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-574">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-575">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-575">Allowed From</span></span>

<span data-ttu-id="26e20-576">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-576">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-577">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-577">Example</span></span>

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="26e20-578">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="26e20-578">nx_dhcp_start</span></span>

<span data-ttu-id="26e20-579">Inicia el procesamiento de DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-579">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-580">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-580">Prototype</span></span>

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-581">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-581">Description</span></span>

<span data-ttu-id="26e20-582">Este servicio inicia el procesamiento de DHCP en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-582">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="26e20-583">De forma predeterminada, la interfaz principal se habilita para DHCP cuando la aplicación llama a *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="26e20-583">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="26e20-584">Para comprobar si la instancia de IP está enlazada a una dirección IP en la interfaz de cliente DHCP, use *nx_ip_status_check* para ver la confirmación de que la dirección IP es válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-584">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="26e20-585">Si hay otras interfaces que ya ejecutan DHCP, no se verán afectadas por este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-585">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="26e20-586">Para iniciar DHCP en una interfaz específica cuando hay varias interfaces habilitadas, utilice el servicio *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="26e20-586">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-587">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-587">Input Parameters</span></span>

- <span data-ttu-id="26e20-588">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-588">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-589">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-589">Return Values</span></span>

- <span data-ttu-id="26e20-590">**NX_SUCCESS** (0x00) DHCP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-590">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="26e20-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="26e20-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>

- <span data-ttu-id="26e20-592">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-592">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="26e20-593">NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-593">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-594">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-594">Allowed From</span></span>

<span data-ttu-id="26e20-595">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-595">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-596">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-596">Example</span></span>

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="26e20-597">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="26e20-597">nx_dhcp_interface_start</span></span>

<span data-ttu-id="26e20-598">Inicia el procesamiento de DHCP en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-598">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-599">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-599">Prototype</span></span>

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="26e20-600">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-600">Description</span></span>

<span data-ttu-id="26e20-601">Este servicio inicia el procesamiento de DHCP en la interfaz especificada si dicha interfaz está habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-601">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="26e20-602">Consulte *nx_dhcp_interface_enable*() para obtener más información sobre cómo habilitar una interfaz para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-602">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="26e20-603">De forma predeterminada, la interfaz principal se habilita para DHCP cuando la aplicación llama a *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="26e20-603">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="26e20-604">Si no hay otras interfaces que ejecuten el cliente DHCP, este servicio iniciará o reanudará el subproceso del cliente DHCP y (re)activará el temporizador del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-604">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="26e20-605">La aplicación debe usar *nx_ip_status_check* para comprobar si se obtiene una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="26e20-605">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-606">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-606">Input Parameters</span></span>

- <span data-ttu-id="26e20-607">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-607">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="26e20-608">**Interface_index** Índice en el que se va a iniciar el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-608">**Interface_index** Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-609">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-609">Return Values</span></span>

- <span data-ttu-id="26e20-610">**NX_SUCCESS** (0x00) DHCP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-610">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="26e20-611">**NX_DHCP_ALREADY_STARTED** (0x93) Ya se ha iniciado la instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-611">**NX_DHCP_ALREADY_STARTED** (0x93) The DHCP instance has already been started.</span></span>

- <span data-ttu-id="26e20-612">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-612">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="26e20-613">NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-613">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="26e20-614">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-614">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-615">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-615">Allowed From</span></span>

<span data-ttu-id="26e20-616">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-616">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-617">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-617">Example</span></span>

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="26e20-618">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="26e20-618">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="26e20-619">Establece la función de devolución de llamada de cambio de estado de DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-619">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-620">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-620">Prototype</span></span>

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="26e20-621">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-621">Description</span></span>

<span data-ttu-id="26e20-622">Este servicio registra la función de devolución de llamada especificada “dhcp_state_change_notify” para notificar a una aplicación los cambios de estado de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-622">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="26e20-623">La función de devolución de llamada proporciona el estado al que ha pasado el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-623">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="26e20-624">A continuación se indican los valores asociados a los distintos estados de DHCP:</span><span class="sxs-lookup"><span data-stu-id="26e20-624">Following are values associated with the various DHCP states:</span></span>

| <span data-ttu-id="26e20-625">Estado</span><span class="sxs-lookup"><span data-stu-id="26e20-625">State</span></span>                             | <span data-ttu-id="26e20-626">Value</span><span class="sxs-lookup"><span data-stu-id="26e20-626">Value</span></span> |
|-----------------------------------|-------|
| <span data-ttu-id="26e20-627">NX\_DHCP\_STATE\_BOOT</span><span class="sxs-lookup"><span data-stu-id="26e20-627">NX\_DHCP\_STATE\_BOOT</span></span>             | <span data-ttu-id="26e20-628">1</span><span class="sxs-lookup"><span data-stu-id="26e20-628">1</span></span>     |
| <span data-ttu-id="26e20-629">NX\_DHCP\_STATE\_INIT</span><span class="sxs-lookup"><span data-stu-id="26e20-629">NX\_DHCP\_STATE\_INIT</span></span>             | <span data-ttu-id="26e20-630">2</span><span class="sxs-lookup"><span data-stu-id="26e20-630">2</span></span>     |
| <span data-ttu-id="26e20-631">NX\_DHCP\_STATE\_SELECTING</span><span class="sxs-lookup"><span data-stu-id="26e20-631">NX\_DHCP\_STATE\_SELECTING</span></span>        | <span data-ttu-id="26e20-632">3</span><span class="sxs-lookup"><span data-stu-id="26e20-632">3</span></span>     |
| <span data-ttu-id="26e20-633">NX\_DHCP\_STATE\_REQUESTING</span><span class="sxs-lookup"><span data-stu-id="26e20-633">NX\_DHCP\_STATE\_REQUESTING</span></span>       | <span data-ttu-id="26e20-634">4</span><span class="sxs-lookup"><span data-stu-id="26e20-634">4</span></span>     |
| <span data-ttu-id="26e20-635">NX\_DHCP\_STATE\_BOUND</span><span class="sxs-lookup"><span data-stu-id="26e20-635">NX\_DHCP\_STATE\_BOUND</span></span>            | <span data-ttu-id="26e20-636">5</span><span class="sxs-lookup"><span data-stu-id="26e20-636">5</span></span>     |
| <span data-ttu-id="26e20-637">NX\_DHCP\_STATE\_RENEWING</span><span class="sxs-lookup"><span data-stu-id="26e20-637">NX\_DHCP\_STATE\_RENEWING</span></span>         | <span data-ttu-id="26e20-638">6</span><span class="sxs-lookup"><span data-stu-id="26e20-638">6</span></span>     |
| <span data-ttu-id="26e20-639">NX\_DHCP\_STATE\_REBINDING</span><span class="sxs-lookup"><span data-stu-id="26e20-639">NX\_DHCP\_STATE\_REBINDING</span></span>        | <span data-ttu-id="26e20-640">7</span><span class="sxs-lookup"><span data-stu-id="26e20-640">7</span></span>     |
| <span data-ttu-id="26e20-641">NX_DHCP_STATE_FORCERENEW</span><span class="sxs-lookup"><span data-stu-id="26e20-641">NX_DHCP_STATE_FORCERENEW</span></span>          | <span data-ttu-id="26e20-642">8</span><span class="sxs-lookup"><span data-stu-id="26e20-642">8</span></span>     |
| <span data-ttu-id="26e20-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span><span class="sxs-lookup"><span data-stu-id="26e20-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span></span> | <span data-ttu-id="26e20-644">9</span><span class="sxs-lookup"><span data-stu-id="26e20-644">9</span></span>     |


### <a name="input-parameters"></a><span data-ttu-id="26e20-645">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-645">Input Parameters</span></span>

- <span data-ttu-id="26e20-646">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-646">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="26e20-647">**dhcp_state_change_notify** Puntero de función de devolución de llamada de cambio de estado</span><span class="sxs-lookup"><span data-stu-id="26e20-647">**dhcp_state_change_notify** State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-648">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-648">Return Values</span></span>

- <span data-ttu-id="26e20-649">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-649">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="26e20-650">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-650">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="26e20-651">NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-651">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-652">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-652">Allowed From</span></span>

<span data-ttu-id="26e20-653">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="26e20-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="26e20-654">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-654">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="26e20-655">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="26e20-655">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="26e20-656">Establece la función de devolución de llamada de cambio de estado DHCP en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-656">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-657">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-657">Prototype</span></span>

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="26e20-658">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-658">Description</span></span>

<span data-ttu-id="26e20-659">Este servicio registra la función de devolución de llamada especificada para notificar a una aplicación los cambios de estado de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-659">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="26e20-660">Los argumentos de entrada de la función de devolución de llamada son el índice de interfaz y el estado al que el cliente DHCP ha pasado en esa interfaz.</span><span class="sxs-lookup"><span data-stu-id="26e20-660">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="26e20-661">Para obtener más información sobre las funciones de cambio de estado, consulte *nx_dhcp_state_change_notify*().</span><span class="sxs-lookup"><span data-stu-id="26e20-661">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-662">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-662">Input Parameters</span></span>

- <span data-ttu-id="26e20-663">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-663">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="26e20-664">**dhcp_interface_state_change_notify** Puntero de función de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="26e20-664">**dhcp_interface_state_change_notify** Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-665">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-665">Return Values</span></span>

- <span data-ttu-id="26e20-666">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-666">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="26e20-667">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-667">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-668">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-668">Allowed From</span></span>

<span data-ttu-id="26e20-669">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="26e20-669">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="26e20-670">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-670">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="26e20-671">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="26e20-671">nx_dhcp_stop</span></span>

<span data-ttu-id="26e20-672">Detiene el procesamiento de DHCP</span><span class="sxs-lookup"><span data-stu-id="26e20-672">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-673">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-673">Prototype</span></span>

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-674">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-674">Description</span></span>

<span data-ttu-id="26e20-675">Este servicio detiene el procesamiento de DHCP en todas las interfaces que han iniciado el procesamiento de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-675">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="26e20-676">Si no hay ninguna interfaz que procese DHCP, este servicio suspenderá el subproceso de cliente DHCP e inactivará el temporizador de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-676">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="26e20-677">Para detener DHCP en una interfaz específica si hay varias interfaces habilitadas para DHCP, use el servicio *nx_dhcp_interface_stop*.</span><span class="sxs-lookup"><span data-stu-id="26e20-677">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-678">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-678">Input Parameters</span></span>

- <span data-ttu-id="26e20-679">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-679">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-680">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-680">Return Values</span></span>

- <span data-ttu-id="26e20-681">**NX_SUCCESS** (0x00) DHCP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-681">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="26e20-682">**NX_DHCP_NOT_STARTED** (0x96) No se ha iniciado la instancia de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-682">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started.</span></span>

- <span data-ttu-id="26e20-683">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-683">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="26e20-684">NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-684">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-685">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-685">Allowed From</span></span>

<span data-ttu-id="26e20-686">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-686">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-687">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-687">Example</span></span>

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="26e20-688">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="26e20-688">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="26e20-689">Detiene el procesamiento de DHCP en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-689">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-690">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-690">Prototype</span></span>

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="26e20-691">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-691">Description</span></span>

<span data-ttu-id="26e20-692">Este servicio detiene el procesamiento de DHCP en la interfaz especificada si DHCP ya está iniciado.</span><span class="sxs-lookup"><span data-stu-id="26e20-692">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="26e20-693">Si no hay ninguna otra interfaz que ejecute DHCP, se suspenden el subproceso y el temporizador de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-693">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-694">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-694">Input Parameters</span></span>

- <span data-ttu-id="26e20-695">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-695">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="26e20-696">**Interface_index** Interfaz en la que se va a detener el procesamiento de DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-696">**Interface_index** Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-697">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-697">Return Values</span></span>

- <span data-ttu-id="26e20-698">**NX_SUCCESS** (0x00) DHCP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-698">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="26e20-699">**NX_DHCP_NOT_STARTED** (0x96) No se ha iniciado DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP not started.</span></span>

- <span data-ttu-id="26e20-700">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-700">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="26e20-701">NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-701">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="26e20-702">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-702">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-703">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-703">Allowed From</span></span>

<span data-ttu-id="26e20-704">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-704">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-705">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-705">Example</span></span>

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="26e20-706">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="26e20-706">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="26e20-707">Recupera una opción DHCP de la última respuesta del servidor</span><span class="sxs-lookup"><span data-stu-id="26e20-707">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-708">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-708">Prototype</span></span>

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="26e20-709">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-709">Description</span></span>

<span data-ttu-id="26e20-710">Este servicio recupera la opción DHCP especificada del búfer de opciones DHCP de la primera interfaz habilitada para DHCP encontrada en el registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-710">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="26e20-711">Si se realiza correctamente, los datos de la opción se copian en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="26e20-711">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-712">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-712">Input Parameters</span></span>

- <span data-ttu-id="26e20-713">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-713">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>  

- <span data-ttu-id="26e20-714">**request_option** Opción DHCP, tal y como se especifica en las RFC.</span><span class="sxs-lookup"><span data-stu-id="26e20-714">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="26e20-715">Consulte la opción NX_DHCP_OPTION en *nx_dhcp.h*.</span><span class="sxs-lookup"><span data-stu-id="26e20-715">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>

- <span data-ttu-id="26e20-716">**destination_ptr** Puntero al destino de la cadena de respuesta.</span><span class="sxs-lookup"><span data-stu-id="26e20-716">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="26e20-717">**destination_size** Puntero al tamaño del destino y, en la devolución, al destino para colocar el número de bytes devueltos.</span><span class="sxs-lookup"><span data-stu-id="26e20-717">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-718">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-718">Return Values</span></span>

- <span data-ttu-id="26e20-719">**NX_SUCCESS** (0x00) Opción recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-719">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="26e20-720">**NX_DHCP_NOT_BOUND** (0x94) Cliente DHCP no enlazado.</span><span class="sxs-lookup"><span data-stu-id="26e20-720">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound.</span></span>

- <span data-ttu-id="26e20-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No hay interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="26e20-722">**NX_DHCP_DEST_TO_SMALL** (0x95) El destino es demasiado pequeño para mantener la respuesta.</span><span class="sxs-lookup"><span data-stu-id="26e20-722">**NX_DHCP_DEST_TO_SMALL** (0x95) Destination is too small to hold response.</span></span>

- <span data-ttu-id="26e20-723">**NX_DHCP_PARSE_ERROR** (0x97) No se encontró la opción DHCP en la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="26e20-723">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="26e20-724">NX_PTR_ERROR (0x16) El puntero de entrada no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-724">NX_PTR_ERROR (0x16) Invalid input pointer.</span></span>

- <span data-ttu-id="26e20-725">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-725">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-726">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-726">Allowed From</span></span>

<span data-ttu-id="26e20-727">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-727">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-728">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-728">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="26e20-729">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="26e20-729">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="26e20-730">Recupera una opción de DHCP de la última respuesta del servidor en la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="26e20-730">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-731">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-731">Prototype</span></span>

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="26e20-732">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-732">Description</span></span>

<span data-ttu-id="26e20-733">Este servicio recupera la opción DHCP especificada del búfer de opciones DHCP en la interfaz especificada, si dicha interfaz está habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="26e20-733">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="26e20-734">Si se realiza correctamente, los datos de la opción se copian en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="26e20-734">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-735">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-735">Input Parameters</span></span>

- <span data-ttu-id="26e20-736">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-736">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="26e20-737">**Interface_index** Índice en el que se va a recuperar la opción especificada.</span><span class="sxs-lookup"><span data-stu-id="26e20-737">**Interface_index** Index on which to retrieve the specified option</span></span>  

- <span data-ttu-id="26e20-738">**request_option** Opción DHCP, tal y como se especifica en las RFC.</span><span class="sxs-lookup"><span data-stu-id="26e20-738">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="26e20-739">Consulte la opción NX_DHCP_OPTION en *nx_dhcp.h*.</span><span class="sxs-lookup"><span data-stu-id="26e20-739">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>  

- <span data-ttu-id="26e20-740">**destination_ptr** Puntero al destino de la cadena de respuesta.</span><span class="sxs-lookup"><span data-stu-id="26e20-740">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="26e20-741">**destination_size** Puntero al tamaño del destino y, en la devolución, al destino para colocar el número de bytes devueltos.</span><span class="sxs-lookup"><span data-stu-id="26e20-741">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-742">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-742">Return Values</span></span>

- <span data-ttu-id="26e20-743">**NX_SUCCESS** (0x00) Opción recuperada correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-743">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="26e20-744">**NX_DHCP_NOT_BOUND** (0x94) Dirección IP no asignada.</span><span class="sxs-lookup"><span data-stu-id="26e20-744">**NX_DHCP_NOT_BOUND** (0x94) IP address not assigned</span></span>

- <span data-ttu-id="26e20-745">**NX_DHCP_DEST_TO_SMALL** (0x95) El búfer es demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="26e20-745">**NX_DHCP_DEST_TO_SMALL** (0x95) Buffer is too small</span></span>

- <span data-ttu-id="26e20-746">**NX_DHCP_PARSE_ERROR** (0x97) No se encontró la opción DHCP en la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="26e20-746">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="26e20-747">NX_PTR_ERROR (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-747">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="26e20-748">NX_CALLER_ERROR (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="26e20-748">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="26e20-749">NX_INVALID_INTERFACE (0x4C) Interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="26e20-749">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-750">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-750">Allowed From</span></span>

<span data-ttu-id="26e20-751">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-752">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-752">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="26e20-753">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="26e20-753">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="26e20-754">Convierte cuatro bytes en ULONG</span><span class="sxs-lookup"><span data-stu-id="26e20-754">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-755">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-755">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="26e20-756">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-756">Description</span></span>

<span data-ttu-id="26e20-757">Este servicio convierte los cuatro caracteres a los que apunta “option_string_ptr” en un valor Long sin signo.</span><span class="sxs-lookup"><span data-stu-id="26e20-757">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="26e20-758">Es especialmente útil cuando hay presentes direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="26e20-758">It is especially useful when IP addresses are present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-759">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-759">Input Parameters</span></span>

- <span data-ttu-id="26e20-760">**option_string_ptr** Puntero a la cadena de opción recuperada previamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-760">**option_string_ptr** Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-761">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-761">Return Values</span></span>

- <span data-ttu-id="26e20-762">**Value** Valor de los primeros cuatro bytes.</span><span class="sxs-lookup"><span data-stu-id="26e20-762">**Value** Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-763">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-763">Allowed From</span></span>

<span data-ttu-id="26e20-764">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-765">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-765">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="26e20-766">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="26e20-766">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="26e20-767">Establece la función de devolución de llamada para agregar opciones proporcionadas por el usuario</span><span class="sxs-lookup"><span data-stu-id="26e20-767">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="26e20-768">Prototipo</span><span class="sxs-lookup"><span data-stu-id="26e20-768">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="26e20-769">Descripción</span><span class="sxs-lookup"><span data-stu-id="26e20-769">Description</span></span>

<span data-ttu-id="26e20-770">Este servicio registra la función de devolución de llamada especificada para agregar las opciones proporcionadas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="26e20-770">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="26e20-771">Si se especifica la función de devolución de llamada, las aplicaciones pueden agregar al paquete opciones proporcionadas por el usuario mediante iface_index y message_type.</span><span class="sxs-lookup"><span data-stu-id="26e20-771">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

> [!NOTE]
> <span data-ttu-id="26e20-772">En la rutina del usuario.</span><span class="sxs-lookup"><span data-stu-id="26e20-772">In user’s routine.</span></span> <span data-ttu-id="26e20-773">Las aplicaciones deben seguir el formato de las opciones de DHCP cuando se agregan opciones proporcionadas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="26e20-773">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="26e20-774">El tamaño total de las opciones de usuario debe ser menor o igual que user_option_length y actualizar user_option_length como la longitud de las opciones reales.</span><span class="sxs-lookup"><span data-stu-id="26e20-774">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="26e20-775">Devuelve NX_TRUE si se agregan opciones correctamente; de lo contrario, devuelve NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="26e20-775">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="26e20-776">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="26e20-776">Input Parameters</span></span>

- <span data-ttu-id="26e20-777">**dhcp_ptr** Puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="26e20-777">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="26e20-778">**dhcp_user_option_add** Puntero a la opción Agregar función de usuario.</span><span class="sxs-lookup"><span data-stu-id="26e20-778">**dhcp_user_option_add** Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="26e20-779">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="26e20-779">Return Values</span></span>

- <span data-ttu-id="26e20-780">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="26e20-780">**NX_SUCCESS** (0x00) Successful callback set.</span></span>

- <span data-ttu-id="26e20-781">NX_PTR_ERROR (0x16) Puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="26e20-781">NX_PTR_ERROR (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="26e20-782">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="26e20-782">Allowed From</span></span>

<span data-ttu-id="26e20-783">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="26e20-783">Threads</span></span>

### <a name="example"></a><span data-ttu-id="26e20-784">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="26e20-784">Example</span></span>

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
