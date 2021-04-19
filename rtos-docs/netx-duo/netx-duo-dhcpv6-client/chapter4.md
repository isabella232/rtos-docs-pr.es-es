---
title: 'Capítulo 4: Servicios de cliente DHCPv6 de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del cliente Azure RTOS NetX Duo DHCPv6 incluidos a continuación por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814769"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a><span data-ttu-id="d690d-103">Capítulo 4: Servicios de cliente DHCPv6 de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d690d-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 Client services</span></span>

<span data-ttu-id="d690d-104">Este capítulo contiene una descripción de todos los servicios del cliente Azure RTOS NetX Duo DHCPv6 incluidos a continuación por orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="d690d-104">This chapter contains a description of all Azure RTOS NetX Duo DHCPv6 Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="d690d-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="d690d-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="d690d-106">**nx_dhcpv6_client_create:** *Creación de una instancia de cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-106">**nx_dhcpv6_client_create:** *Create a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="d690d-107">**nx_dhcpv6_client_delete:** *Eliminación de una instancia de cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-107">**nx_dhcpv6_client_delete:** *Delete a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="d690d-108">**nx_dhcpv6_create_ client_duid:** *Creación de un DUID de cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-108">**nx_dhcpv6_create_ client_duid:** *Create a DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="d690d-109">**nx_dhcpv6 _add_client_ia:** *Agregar una dirección de identidad de cliente DHCPv6 (IA)*</span><span class="sxs-lookup"><span data-stu-id="d690d-109">**nx_dhcpv6 _add_client_ia:** *Add a DHCPv6 Client Identity Address (IA)*</span></span> 

- <span data-ttu-id="d690d-110">**nx_dhcpv6 _create_client_ia:** (*Heredado agregar una dirección de identidad de cliente DHCPv6 (IA))*</span><span class="sxs-lookup"><span data-stu-id="d690d-110">**nx_dhcpv6 _create_client_ia:** (*Legacy Add a DHCPv6 Client Identity Address (IA))*</span></span> 

- <span data-ttu-id="d690d-111">**nx_dhcpv6_create_client_iana:** *Creación de una asociación de identidad de cliente Dhcpv6 para direcciones no temporales (IANA)*</span><span class="sxs-lookup"><span data-stu-id="d690d-111">**nx_dhcpv6_create_client_iana:** *Create a DHCPv6 Client Identity Association for Non Temporary Addresses (IANA)*</span></span> 

- <span data-ttu-id="d690d-112">**nx_dhcpv6_get_client_duid_time_id:** *Obtener el id. de hora del DUID del cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-112">**nx_dhcpv6_get_client_duid_time_id:** *Get the time ID from DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="d690d-113">**nx_dhcpv6_client_set_interface:** *Establecer la interfaz de red de cliente para las comunicaciones con el servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-113">**nx_dhcpv6_client_set_interface:** *Set the Client network interface for communications with the DHCPv6 Server*</span></span> 

- <span data-ttu-id="d690d-114">**nx_dhcpv6_get_IP_address:** *Obtener la dirección IPv6 global asignada al cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-114">**nx_dhcpv6_get_IP_address:** *Get the global IPv6 address assigned to the DHCPv6 client*</span></span> 

- <span data-ttu-id="d690d-115">**nx_dhcpv6_get_lease_time_data:** *Obtener las duraciones T1 y T2 válidas y preferidas para la dirección IPv6 global del cliente*</span><span class="sxs-lookup"><span data-stu-id="d690d-115">**nx_dhcpv6_get_lease_time_data:** *Get T1, T2, valid and preferred lifetimes for the Client global IPv6 address*</span></span>

- <span data-ttu-id="d690d-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Obtener las duraciones T1 y T2 válidas y preferidas para la dirección IPv6 del cliente DHCPv6 por índice de dirección*</span><span class="sxs-lookup"><span data-stu-id="d690d-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Get T1, T2, valid and preferred lifetimes for the DHCPv6 Client IPv6 address by address index*</span></span> 

- <span data-ttu-id="d690d-117">**nx_dhcpv6_get_iana_lease_time:** *Obtener T1 y T2 en la Asociación de identidad (IANA) concedida al cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-117">**nx_dhcpv6_get_iana_lease_time:** *Get T1 and T2 in the Identity Association (IANA) leased to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="d690d-118">**nx_dhcpv6_get_other_option_data:** *Obtener los datos de opción especificados, por ejemplo, el nombre de dominio o el servidor de zona horaria*</span><span class="sxs-lookup"><span data-stu-id="d690d-118">**nx_dhcpv6_get_other_option_data:** *Get the specified option data e.g. domain name or time zone server*</span></span> 

- <span data-ttu-id="d690d-119">**nx_dhcpv6_get_DNS_server_address:** *Obtener la dirección del servidor DNS en el índice especificado de la lista de servidores DNS de cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-119">**nx_dhcpv6_get_DNS_server_address:** *Get DNS Server address at the specified index into the DHCPv6 Client DNS server list*</span></span> 

- <span data-ttu-id="d690d-120">**nx_dhcpv6_get_time_accrued:** *Obtener el tiempo acumulado que la concesión de la dirección IPv6 global se ha vinculado al cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-120">**nx_dhcpv6_get_time_accrued:** *Get the time accrued the global IPv6 address lease has been bound to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="d690d-121">**nx_dhcpv6_get_time_server_address:** *Obtener la dirección del servidor de tiempo en el índice especificado de la lista de servidores de tiempo de cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-121">**nx_dhcpv6_get_time_server_address:** *Get Time Server address at the specified index into the DHCPv6 Client Time server list*</span></span>

- <span data-ttu-id="d690d-122">**nx_dhcpv6_get_valid_ip_address_count:** *Obtener el número de direcciones IPv6 asignadas al cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-122">**nx_dhcpv6_get_valid_ip_address_count:** *Get the number of IPv6 addresses assigned to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="d690d-123">**nx_dhcpv6_reinitialize:** *Reinicialice DHCPv6 para reiniciar la máquina de Estados cliente DHCPv6 y reejecutar el protocolo DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-123">**nx_dhcpv6_reinitialize:** *Reinitialize the DHCPv6 for restarting the DHCPv6 Client state machine and rerunning the DHCPv6 protocol*</span></span> 

- <span data-ttu-id="d690d-124">**nx_dhcpv6_request_confirm:** *Enviar una solicitud de confirmación al Servidor*</span><span class="sxs-lookup"><span data-stu-id="d690d-124">**nx_dhcpv6_request_confirm:** *Send a CONFIRM request to the Server*</span></span> 

- <span data-ttu-id="d690d-125">**nx_dhcpv6_request_inform_request:** E *nviar un mensaje de SOLICITUD DE INFORME al servidor*</span><span class="sxs-lookup"><span data-stu-id="d690d-125">**nx_dhcpv6_request_inform_request:** S *end an INFORM REQUEST message to the Server*</span></span> 

- <span data-ttu-id="d690d-126">**nx_dhcpv6_request_release:** *Enviar una solicitud de VERSIÓN al servidor*</span><span class="sxs-lookup"><span data-stu-id="d690d-126">**nx_dhcpv6_request_release:** *Send a RELEASE request to the Server*</span></span> 

- <span data-ttu-id="d690d-127">**nx_dhcpv6_request_option_DNS_server:** *Agregar la opción de servidor DNS a la opción de Cliente solicitar datos en mensajes de solicitud al servidor*</span><span class="sxs-lookup"><span data-stu-id="d690d-127">**nx_dhcpv6_request_option_DNS_server:** *Add the DNS server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="d690d-128">**nx_dhcpv6_request_option_FQDN:** *Agregar la opción FQDN a la opción de cliente solicitar datos en los mensajes de solicitud al servidor*</span><span class="sxs-lookup"><span data-stu-id="d690d-128">**nx_dhcpv6_request_option_FQDN:** *Add the FQDN option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="d690d-129">**nx_dhcpv6_request_option_domain_name:** *Agregar la opción de nombre de dominio a la opción de cliente solicitar datos en los mensajes de solicitud al servidor*</span><span class="sxs-lookup"><span data-stu-id="d690d-129">**nx_dhcpv6_request_option_domain_name:** *Add the domain name option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="d690d-130">**nx_dhcpv6_request_option_time_server:** *Agregar la opción de servidor de tiempo a la opción de cliente solicitar datos en mensajes de solicitud al servidor*</span><span class="sxs-lookup"><span data-stu-id="d690d-130">**nx_dhcpv6_request_option_time_server:** *Add the time server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="d690d-131">**nx_dhcpv6_request_option_timezone:** *Agregar la opción de zona horaria a la opción de cliente solicitar datos en los mensajes de solicitud al servidor*</span><span class="sxs-lookup"><span data-stu-id="d690d-131">**nx_dhcpv6_request_option_timezone:** *Add the time zone option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="d690d-132">**nx_dhcpv6_request_solicit:** *Enviar una solicitud de PETICIÓN DHCPv6 a cualquier servidor de la red de cliente (difusión)*</span><span class="sxs-lookup"><span data-stu-id="d690d-132">**nx_dhcpv6_request_solicit:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast)*</span></span> 

- <span data-ttu-id="d690d-133">**nx_dhcpv6_request_solicit_rapid:** *Enviar una solicitud de PETICIÓN DHCPv6 a cualquier servidor de la red de cliente (difusión) con la opción de confirmación rápida establecida*</span><span class="sxs-lookup"><span data-stu-id="d690d-133">**nx_dhcpv6_request_solicit_rapid:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast) with the Rapid Commit option set*</span></span> 

- <span data-ttu-id="d690d-134">**nx_dhcpv6_resume:** *Reanudar el procesamiento del cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-134">**nx_dhcpv6_resume:** *Resume DHCPv6 Client processing*</span></span> 

- <span data-ttu-id="d690d-135">**nx_dhcpv6_start:** *Inicie la tarea de subproceso de cliente DHCPv6. Tenga en cuenta que esto no es equivalente a iniciar la máquina de estados DHCPv6 y no envía una solicitud de PETICIÓN*</span><span class="sxs-lookup"><span data-stu-id="d690d-135">**nx_dhcpv6_start:** *Start the DHCPv6 Client thread task. Note this is not equivalent to starting the DHCPv6 state machine and does not send a SOLICIT request*</span></span> 

- <span data-ttu-id="d690d-136">**nx_dhcpv6_stop:** *Detener la tarea de subproceso de cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-136">**nx_dhcpv6_stop:** *Stop the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="d690d-137">**nx_dhcpv6_suspend:** *Suspender la tarea de subproceso de cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="d690d-137">**nx_dhcpv6_suspend:** *Suspend the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="d690d-138">**nx_dhcpv6_set_time_accrued:** *Establezca el tiempo acumulado en la concesión de la dirección IPv6 del cliente global en el registro de cliente.*</span><span class="sxs-lookup"><span data-stu-id="d690d-138">**nx_dhcpv6_set_time_accrued:** *Set the time accrued on the global Client IPv6 address lease in the Client record.*</span></span>

## <a name="nx_dhcpv6_client_create"></a><span data-ttu-id="d690d-139">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="d690d-139">nx_dhcpv6_client_create</span></span>

<span data-ttu-id="d690d-140">Crear una instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-140">Create a DHCPv6 client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-141">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-141">Prototype</span></span>

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a><span data-ttu-id="d690d-142">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-142">Description</span></span>

<span data-ttu-id="d690d-143">Este servicio crea una instancia de cliente DHCPv6 que incluye funciones de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="d690d-143">This service creates a DHCPv6 client instance including callback functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-144">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-144">Input Parameters</span></span>

- <span data-ttu-id="d690d-145">**dhcpv6_ptr** Puntero al bloque de control DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-145">**dhcpv6_ptr** Pointer to DHCPv6 control block</span></span>  

- <span data-ttu-id="d690d-146">**ip_ptr** Puntero a la instancia de IP del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-146">**ip_ptr** Pointer to Client IP instance</span></span>  

- <span data-ttu-id="d690d-147">**name_ptr** Puntero al nombre de la instancia de DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-147">**name_ptr** Pointer to name for DHCPv6 instance</span></span>

- <span data-ttu-id="d690d-148">**packet_pool_ptr** Puntero al grupo de paquetes del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-148">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="d690d-149">**stack_ptr** Puntero a la memoria de pila de cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-149">**stack_ptr** Pointer to Client stack memory</span></span>

- <span data-ttu-id="d690d-150">**stack_size** Tamaño de la memoria de pila de cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-150">**stack_size** Size of Client stack memory</span></span>

- <span data-ttu-id="d690d-151">**dhcpv6_state_change_notify** Puntero a la función de devolución de llamada que se invoca cuando el cliente inicia una nueva solicitud DHCPv6 al servidor</span><span class="sxs-lookup"><span data-stu-id="d690d-151">**dhcpv6_state_change_notify** Pointer to callback function invoked when the Client initiates a new DHCPv6 request to the server</span></span>

- <span data-ttu-id="d690d-152">**dhcpv6_server_error_handler** Puntero a la función de devolución de llamada que se invoca cuando el cliente recibe un estado de error del servidor</span><span class="sxs-lookup"><span data-stu-id="d690d-152">**dhcpv6_server_error_handler** Pointer to callback function invoked when the Client receives an error status from the server</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-153">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-153">Return Values</span></span>

- <span data-ttu-id="d690d-154">**NX_SUCCESS** (0x00) Creación correcta del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-154">**NX_SUCCESS** (0x00) Successful Client create</span></span>

- <span data-ttu-id="d690d-155">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-155">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-156">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-156">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-157">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-157">Allowed From</span></span>

<span data-ttu-id="d690d-158">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-159">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-159">Example</span></span>

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-160">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-160">See Also</span></span>

- <span data-ttu-id="d690d-161">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="d690d-161">nx_dhcpv6_client_delete</span></span>

## <a name="nx_dhcpv6_client_delete"></a><span data-ttu-id="d690d-162">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="d690d-162">nx_dhcpv6_client_delete</span></span>

<span data-ttu-id="d690d-163">Eliminación de una instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-163">Delete a DHCPv6 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-164">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-164">Prototype</span></span>

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-165">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-165">Description</span></span>

<span data-ttu-id="d690d-166">Este servicio elimina una instancia de cliente DHCPv6 creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d690d-166">This service deletes a previously created DHCPv6 client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-167">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-167">Input Parameters</span></span>

- <span data-ttu-id="d690d-168">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-168">**dhcpv6_ptr** Pointer to DHCPv6 client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-169">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-169">Return Values</span></span>

- <span data-ttu-id="d690d-170">**NX_SUCCESS** (0x00) Eliminación correcta de DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-170">**NX_SUCCESS** (0x00) Successful DHCPv6 deletion</span></span>

- <span data-ttu-id="d690d-171">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-171">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-172">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-172">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-173">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-173">Allowed From</span></span>

<span data-ttu-id="d690d-174">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-175">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-175">Example</span></span>

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-176">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-176">See Also</span></span>

- <span data-ttu-id="d690d-177">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="d690d-177">nx_dhcpv6_client_create</span></span>

## <a name="nx_dhcpv6_client_set_interface"></a><span data-ttu-id="d690d-178">nx_dhcpv6_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="d690d-178">nx_dhcpv6_client_set_interface</span></span>

<span data-ttu-id="d690d-179">Establece la interfaz de red del cliente para DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-179">Sets Client’s Network Interface for DHCPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-180">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-180">Prototype</span></span>

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="d690d-181">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-181">Description</span></span>

<span data-ttu-id="d690d-182">Este servicio establece la interfaz de red del cliente para comunicarse con los servidores DHCPv6 en el índice de interfaz de entrada especificado.</span><span class="sxs-lookup"><span data-stu-id="d690d-182">This service sets the Client’s network interface for communicating with the DHCPv6 Server(s) to the specified input interface index.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-183">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-183">Input Parameters</span></span>

- <span data-ttu-id="d690d-184">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-184">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-185">**interface_index** Índice que indica la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="d690d-185">**interface_index** Index indicating network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-186">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-186">Return Values</span></span>

- <span data-ttu-id="d690d-187">**NX_SUCCESS** (0x00) Se estableció correctamente la interfaz</span><span class="sxs-lookup"><span data-stu-id="d690d-187">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="d690d-188">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-188">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-189">NX_INVALID_INTERFACE (0x4C) Entrada de índice de interfaz no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-189">NX_INVALID_INTERFACE (0x4C) Invalid interface index input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-190">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-190">Allowed From</span></span>

<span data-ttu-id="d690d-191">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-192">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-192">Example</span></span>

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-193">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-193">See Also</span></span>

- <span data-ttu-id="d690d-194">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="d690d-194">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="d690d-195">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="d690d-195">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_client_set_destination_address"></a><span data-ttu-id="d690d-196">nx_dhcpv6_client_set_destination_address</span><span class="sxs-lookup"><span data-stu-id="d690d-196">nx_dhcpv6_client_set_destination_address</span></span>

<span data-ttu-id="d690d-197">Establece la dirección de destino a la que se debe enviar el mensaje DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-197">Sets the destination address where DHCPv6 message should be sent to</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-198">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-198">Prototype</span></span>

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a><span data-ttu-id="d690d-199">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-199">Description</span></span>

<span data-ttu-id="d690d-200">Este servicio establece la dirección de destino a la que se debe enviar el mensaje DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-200">This service sets the destination address where DHCPv6 message should be sent to.</span></span> <span data-ttu-id="d690d-201">By default is ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).</span><span class="sxs-lookup"><span data-stu-id="d690d-201">By default is ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-202">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-202">Input Parameters</span></span>

- <span data-ttu-id="d690d-203">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-203">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-204">**destination_address** Dirección de destino</span><span class="sxs-lookup"><span data-stu-id="d690d-204">**destination_address** Destination address</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-205">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-205">Return Values</span></span>

- <span data-ttu-id="d690d-206">**NX_SUCCESS** (0x00) Se estableció correctamente la interfaz</span><span class="sxs-lookup"><span data-stu-id="d690d-206">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="d690d-207">NX_PTR_ERROR (0x07) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-207">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-208">NX_DHCPV6_PARAM_ERROR (0xE93) Error de parámetro</span><span class="sxs-lookup"><span data-stu-id="d690d-208">NX_DHCPV6_PARAM_ERROR (0xE93) Parament error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-209">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-209">Allowed From</span></span>

<span data-ttu-id="d690d-210">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-210">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-211">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-211">Example</span></span>

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-212">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-212">See Also</span></span>

- <span data-ttu-id="d690d-213">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="d690d-213">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="d690d-214">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="d690d-214">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_create_client_duid"></a><span data-ttu-id="d690d-215">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="d690d-215">nx_dhcpv6_create_client_duid</span></span>

<span data-ttu-id="d690d-216">Crear un objeto DUID de cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-216">Create Client DUID object</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-217">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-217">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a><span data-ttu-id="d690d-218">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-218">Description</span></span>

<span data-ttu-id="d690d-219">Este servicio crea el DUID de cliente con los parámetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="d690d-219">This service creates the Client DUID with the input parameters.</span></span> <span data-ttu-id="d690d-220">Si no se proporciona la entrada de hora y el tipo de DUID indica el nivel de vínculo con el tiempo, esta función proporcionará una hora que incluye un factor aleatorio para la unicidad.</span><span class="sxs-lookup"><span data-stu-id="d690d-220">If the time input is not supplied and the duid type indicates link layer with time, this function will supply a time which includes a randomizing factor for uniqueness.</span></span> <span data-ttu-id="d690d-221">No se admiten los tipos de DUID asignados por el proveedor (Enterprise).</span><span class="sxs-lookup"><span data-stu-id="d690d-221">Vendor assigned (enterprise) duid types are not supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-222">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-222">Input Parameters</span></span>

- <span data-ttu-id="d690d-223">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-223">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-224">**duid_type** Tipo de DUID (hardware, empresa, etc.)</span><span class="sxs-lookup"><span data-stu-id="d690d-224">**duid_type** Type of DUID (hardware, enterprise etc)</span></span>

- <span data-ttu-id="d690d-225">**hardware_type** Hardware de red, por ejemplo, IEEE 802</span><span class="sxs-lookup"><span data-stu-id="d690d-225">**hardware_type** Network hardware e.g. IEEE 802</span></span>

- <span data-ttu-id="d690d-226">**hora** de Valor usado en la creación de un identificador único</span><span class="sxs-lookup"><span data-stu-id="d690d-226">**time** Value used in creating unique identifier</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-227">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-227">Return Values</span></span>

- <span data-ttu-id="d690d-228">**NX_SUCCESS** (0x00) Cliente exitoso DUID creado</span><span class="sxs-lookup"><span data-stu-id="d690d-228">**NX_SUCCESS** (0x00) Successful Client DUID created</span></span>

- <span data-ttu-id="d690d-229">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-229">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-230">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-230">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="d690d-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) Tipo de DUID desconocido o no admitido</span><span class="sxs-lookup"><span data-stu-id="d690d-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID type unknown or not supported</span></span> 

- <span data-ttu-id="d690d-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) Tipo de hardware de DUID desconocido o no admitido</span><span class="sxs-lookup"><span data-stu-id="d690d-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID hardware type unknown or not supported</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-233">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-233">Allowed From</span></span>

<span data-ttu-id="d690d-234">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-234">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-235">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-235">Example</span></span>

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-236">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-236">See Also</span></span>

- <span data-ttu-id="d690d-237">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="d690d-237">nx_dhcpv6_create_client_ia</span></span>
- <span data-ttu-id="d690d-238">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="d690d-238">nx_dhcpv6_create_client_iana</span></span>
- <span data-ttu-id="d690d-239">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="d690d-239">nx_dhcpv6_create_server_duid</span></span>

## <a name="nx_dhcpv6_create_client_ia"></a><span data-ttu-id="d690d-240">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="d690d-240">nx_dhcpv6_create_client_ia</span></span>

<span data-ttu-id="d690d-241">Agregar una Asociación de identidad al cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-241">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-242">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-242">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="d690d-243">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-243">Description</span></span>

<span data-ttu-id="d690d-244">Este servicio es idéntico al servicio *nx_dhcpv6_add_client_ia*.</span><span class="sxs-lookup"><span data-stu-id="d690d-244">This service is identical to the *nx_dhcpv6_add_client_ia* service.</span></span> <span data-ttu-id="d690d-245">Agrega una Asociación de identidad de cliente rellenando el registro de cliente con los parámetros proporcionados.</span><span class="sxs-lookup"><span data-stu-id="d690d-245">It adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="d690d-246">Para solicitar la vigencia máxima preferida y válida, establezca estos parámetros en Infinity.</span><span class="sxs-lookup"><span data-stu-id="d690d-246">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="d690d-247">Para agregar más de un IA a un cliente DHCPv6, establezca el NX_DHCPV6_MAX_IA_ADDRESS en un valor mayor que el valor predeterminado de 1.</span><span class="sxs-lookup"><span data-stu-id="d690d-247">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-248">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-248">Input Parameters</span></span>

- <span data-ttu-id="d690d-249">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-249">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-250">**ipv6_address** Puntero al bloque de direcciones IP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d690d-250">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="d690d-251">**preferred_lifetime** Período de tiempo antes de que la dirección IP esté en desuso</span><span class="sxs-lookup"><span data-stu-id="d690d-251">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="d690d-252">**valid_lifetime** Período de tiempo antes de que la dirección IP expire</span><span class="sxs-lookup"><span data-stu-id="d690d-252">**valid_lifetime** Length of time before IP address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-253">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-253">Return Values</span></span>

- <span data-ttu-id="d690d-254">**NX_SUCCESS** (0x00) IA del cliente añadido correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-254">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="d690d-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Dirección IA duplicada</span><span class="sxs-lookup"><span data-stu-id="d690d-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="d690d-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA supera el número máximo de clientes de IA que puede almacenar</span><span class="sxs-lookup"><span data-stu-id="d690d-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="d690d-257">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-257">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) No válido (por ejemplo, NULL) dirección IA en IA</span><span class="sxs-lookup"><span data-stu-id="d690d-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="d690d-259">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-259">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>


### <a name="allowed-from"></a><span data-ttu-id="d690d-260">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-260">Allowed From</span></span>

<span data-ttu-id="d690d-261">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-261">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-262">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-262">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-263">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-263">See Also</span></span>

- <span data-ttu-id="d690d-264">nx_dhcpv6_add_client_duid</span><span class="sxs-lookup"><span data-stu-id="d690d-264">nx_dhcpv6_add_client_duid</span></span>
- <span data-ttu-id="d690d-265">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="d690d-265">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="d690d-266">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="d690d-266">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_create_client_iana"></a><span data-ttu-id="d690d-267">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="d690d-267">nx_dhcpv6_create_client_iana</span></span>

<span data-ttu-id="d690d-268">Crear una Asociación de identidad (no temporal) para el cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-268">Create an Identity Association (Non Temporary) for the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-269">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-269">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a><span data-ttu-id="d690d-270">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-270">Description</span></span>

<span data-ttu-id="d690d-271">Este servicio crea una Asociación de identidad no temporal del cliente (IANA) a partir de los parámetros proporcionados.</span><span class="sxs-lookup"><span data-stu-id="d690d-271">This service creates a Client Non Temporary Identity Association (IANA) from the supplied parameters.</span></span> <span data-ttu-id="d690d-272">Para establecer las horas T1 y T2 en máximo (infinito) en las solicitudes de cliente DHCPv6, establezca estos parámetros en NX_DHCPV6_INFINITE_LEASE.</span><span class="sxs-lookup"><span data-stu-id="d690d-272">To set the T1 and T2 times to maximum (infinity) in the DHCPv6 Client requests, set these parameters to NX_DHCPV6_INFINITE_LEASE.</span></span> 

> [!NOTE]
> <span data-ttu-id="d690d-273">Un cliente solo tiene una IANA.</span><span class="sxs-lookup"><span data-stu-id="d690d-273">A Client has only one IANA.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-274">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-274">Input Parameters</span></span>

- <span data-ttu-id="d690d-275">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-275">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-276">**IA_ident** Identificador único de la Asociación de identidad</span><span class="sxs-lookup"><span data-stu-id="d690d-276">**IA_ident** Identity Association unique identifier</span></span>

- <span data-ttu-id="d690d-277">**T1** Cuando el cliente debe iniciar la renovación de la dirección IPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-277">**T1** When the Client must start the IPv6 address renewal</span></span>

- <span data-ttu-id="d690d-278">**T2** Cuando el cliente debe iniciar el reenlace de la dirección IPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-278">**T2** When the Client must start theIPv6 address rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-279">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-279">Return Values</span></span>

- <span data-ttu-id="d690d-280">**NX_SUCCESS** (0x00) Creó correctamente la IANA</span><span class="sxs-lookup"><span data-stu-id="d690d-280">**NX_SUCCESS** (0x00) Successfully created the IANA</span></span>

- <span data-ttu-id="d690d-281">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-281">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-282">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-282">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-283">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-283">Allowed From</span></span>

<span data-ttu-id="d690d-284">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-285">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-285">Example</span></span>

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-286">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-286">See Also</span></span>

- <span data-ttu-id="d690d-287">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="d690d-287">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="d690d-288">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="d690d-288">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="d690d-289">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="d690d-289">nx_dhcpv6_add_client_ia</span></span>

## <a name="nx_dhcpv6_add_client_ia"></a><span data-ttu-id="d690d-290">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="d690d-290">nx_dhcpv6_add_client_ia</span></span> 

<span data-ttu-id="d690d-291">Agregar una Asociación de identidad al cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-291">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-292">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-292">Prototype</span></span>

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="d690d-293">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-293">Description</span></span>

<span data-ttu-id="d690d-294">Este servicio agrega una Asociación de identidad de cliente rellenando el registro de cliente con los parámetros proporcionados.</span><span class="sxs-lookup"><span data-stu-id="d690d-294">This service adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="d690d-295">Para solicitar la vigencia máxima preferida y válida, establezca estos parámetros en Infinity.</span><span class="sxs-lookup"><span data-stu-id="d690d-295">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="d690d-296">Para agregar más de un IA a un cliente DHCPv6, establezca el NX_DHCPV6_MAX_IA_ADDRESS en un valor mayor que el valor predeterminado de 1.</span><span class="sxs-lookup"><span data-stu-id="d690d-296">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-297">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-297">Input Parameters</span></span>

- <span data-ttu-id="d690d-298">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-298">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-299">**ipv6_address** Puntero al bloque de direcciones IP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d690d-299">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="d690d-300">**preferred_lifetime** Período de tiempo antes de que la dirección IP esté en desuso</span><span class="sxs-lookup"><span data-stu-id="d690d-300">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="d690d-301">**valid_lifetime** Período de tiempo antes de que la dirección IP expire</span><span class="sxs-lookup"><span data-stu-id="d690d-301">**valid_lifetime** Length of time before IP address is expired</span></span> 

### <a name="return-values"></a><span data-ttu-id="d690d-302">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-302">Return Values</span></span>

- <span data-ttu-id="d690d-303">**NX_SUCCESS** (0x00) IA del cliente añadido correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-303">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="d690d-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Dirección IA duplicada</span><span class="sxs-lookup"><span data-stu-id="d690d-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="d690d-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA supera el número máximo de clientes de IA que puede almacenar</span><span class="sxs-lookup"><span data-stu-id="d690d-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="d690d-306">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-306">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) No válido (por ejemplo, NULL) dirección IA en IA</span><span class="sxs-lookup"><span data-stu-id="d690d-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="d690d-308">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-308">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

 
### <a name="allowed-from"></a><span data-ttu-id="d690d-309">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-309">Allowed From</span></span>

<span data-ttu-id="d690d-310">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-311">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-311">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-312">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-312">See Also</span></span>

- <span data-ttu-id="d690d-313">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="d690d-313">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="d690d-314">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="d690d-314">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="d690d-315">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="d690d-315">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_get_client_duid_time_id"></a><span data-ttu-id="d690d-316">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="d690d-316">nx_dhcpv6_get_client_duid_time_id</span></span>

<span data-ttu-id="d690d-317">Recupera el id. de hora del DUID del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-317">Retrieves time ID from Client DUID</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-318">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-318">Prototype</span></span>

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a><span data-ttu-id="d690d-319">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-319">Description</span></span>

<span data-ttu-id="d690d-320">Este servicio recupera el campo de id. de hora del DUID de cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-320">This service retrieves the time ID field from the Client DUID.</span></span> <span data-ttu-id="d690d-321">Si la aplicación debe llamar primero a *nx_dhcpv6_create_client_duid*, para rellenar el DUID de cliente en la instancia de cliente DHCPv6 o tendrá un valor NULL para este campo.</span><span class="sxs-lookup"><span data-stu-id="d690d-321">If the application must first call *nx_dhcpv6_create_client_duid*, to fill in the Client DUID in the DHCPv6 Client instance or it will have a null value for this field.</span></span> <span data-ttu-id="d690d-322">La intención es que la aplicación guarde estos datos y presente el mismo DUID de cliente al servidor, incluido el campo de tiempo, entre reinicios.</span><span class="sxs-lookup"><span data-stu-id="d690d-322">The intent is for the application to save this data and present the same Client DUID to the server, including the time field, across reboots.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-323">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-323">Input Parameters</span></span>

- <span data-ttu-id="d690d-324">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-324">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-325">**time_id** Puntero al campo de hora de DUID del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-325">**time_id** Pointer to Client DUID time field</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-326">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-326">Return Values</span></span>

- <span data-ttu-id="d690d-327">**NX_SUCCESS** (0x00) Datos de concesión de IP recuperados correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-327">**NX_SUCCESS** (0x00) IP lease data successfully retrieved</span></span>

- <span data-ttu-id="d690d-328">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-328">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-329">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-329">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-330">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-330">Allowed From</span></span>

<span data-ttu-id="d690d-331">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-331">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-332">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-332">Example</span></span>

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-333">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-333">See Also</span></span>

- <span data-ttu-id="d690d-334">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-334">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="d690d-335">nx_dhcpv6_get_time_lease_data</span><span class="sxs-lookup"><span data-stu-id="d690d-335">nx_dhcpv6_get_time_lease_data</span></span>
- <span data-ttu-id="d690d-336">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="d690d-336">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="d690d-337">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-337">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_ip_address"></a><span data-ttu-id="d690d-338">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-338">nx_dhcpv6_get_IP_address</span></span>

<span data-ttu-id="d690d-339">Recupera la dirección IPv6 global del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-339">Retrieves Client’s global IPv6 address</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-340">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-340">Prototype</span></span>

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a><span data-ttu-id="d690d-341">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-341">Description</span></span>

<span data-ttu-id="d690d-342">Este servicio recupera la dirección IPv6 global del cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-342">This service retrieves the Client’s global IPv6 address.</span></span> <span data-ttu-id="d690d-343">Si el cliente no tiene una dirección válida, se devuelve un estado de error.</span><span class="sxs-lookup"><span data-stu-id="d690d-343">If the Client does not have a valid address, an error status is returned.</span></span> <span data-ttu-id="d690d-344">Si un cliente tiene más de una dirección IPv6 global, se devuelve la dirección IPv6 principal.</span><span class="sxs-lookup"><span data-stu-id="d690d-344">If a Client has more than one global IPv6 address, the primary IPv6 address is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-345">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-345">Input Parameters</span></span>

- <span data-ttu-id="d690d-346">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-346">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-347">**ip_address** Puntero a dirección IPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-347">**ip_address** Pointer to IPv6 address</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-348">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-348">Return Values</span></span>

- <span data-ttu-id="d690d-349">**NX_SUCCESS** (0x00) Dirección IPv6 asignada correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-349">**NX_SUCCESS** (0x00) IPv6 address successfully assigned</span></span>

- <span data-ttu-id="d690d-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) La dirección IPv6 no es válida</span><span class="sxs-lookup"><span data-stu-id="d690d-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) IPv6 address is not valid</span></span>

- <span data-ttu-id="d690d-351">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-351">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-352">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-352">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-353">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-353">Allowed From</span></span>

<span data-ttu-id="d690d-354">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-354">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-355">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-355">Example</span></span>

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a><span data-ttu-id="d690d-356">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-356">See Also</span></span>

- <span data-ttu-id="d690d-357">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="d690d-357">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="d690d-358">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="d690d-358">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="d690d-359">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="d690d-359">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="d690d-360">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-360">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_lease_time_data"></a><span data-ttu-id="d690d-361">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="d690d-361">nx_dhcpv6_get_lease_time_data</span></span>

<span data-ttu-id="d690d-362">Recupera los datos de tiempo de concesión de dirección IA del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-362">Retrieves Client’s IA address lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-363">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-363">Prototype</span></span>

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="d690d-364">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-364">Description</span></span>

<span data-ttu-id="d690d-365">Este servicio recupera los datos de hora de la dirección IA global del cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-365">This service retrieves the Client’s global IA address time data.</span></span> <span data-ttu-id="d690d-366">Si el estado de la dirección IA del cliente no es válido, los datos de hora se establecen en cero y se devuelve un estado de finalización correcto.</span><span class="sxs-lookup"><span data-stu-id="d690d-366">If the Client IA address status is invalid, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="d690d-367">Si un cliente tiene más de una dirección IPv6 global, se devuelven los datos de la dirección IA principal.</span><span class="sxs-lookup"><span data-stu-id="d690d-367">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-368">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-368">Input Parameters</span></span>

- <span data-ttu-id="d690d-369">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-369">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-370">**T1** Hora de renovación del puntero a la dirección IA</span><span class="sxs-lookup"><span data-stu-id="d690d-370">**T1** Pointer to IA address renew time</span></span>

- <span data-ttu-id="d690d-371">**T2** Puntero al tiempo de reenlace de la dirección IA</span><span class="sxs-lookup"><span data-stu-id="d690d-371">**T2** Pointer to IA address rebind time</span></span>

- <span data-ttu-id="d690d-372">**preferred_lifetime** Puntero a la hora en que la dirección IA está en desuso</span><span class="sxs-lookup"><span data-stu-id="d690d-372">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="d690d-373">**valid_lifetime** Puntero a la hora de expiración de la dirección IA</span><span class="sxs-lookup"><span data-stu-id="d690d-373">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-374">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-374">Return Values</span></span>

- <span data-ttu-id="d690d-375">**NX_SUCCESS** (0x00) Datos de concesión de IP recuperados correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-375">**NX_SUCCESS** (0x00) IA lease data successfully retrieved</span></span>

- <span data-ttu-id="d690d-376">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-376">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-377">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-377">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-378">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-378">Allowed From</span></span>

<span data-ttu-id="d690d-379">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-380">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-380">Example</span></span>

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-381">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-381">See Also</span></span>

- <span data-ttu-id="d690d-382">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-382">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="d690d-383">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="d690d-383">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="d690d-384">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="d690d-384">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="d690d-385">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-385">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="d690d-386">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="d690d-386">nx_dhcpv6_get_iana_lease_time</span></span>

## <a name="nx_dhcpv6_get_iana-lease_time"></a><span data-ttu-id="d690d-387">nx_dhcpv6_get_iana lease_time</span><span class="sxs-lookup"><span data-stu-id="d690d-387">nx_dhcpv6_get_iana lease_time</span></span>

<span data-ttu-id="d690d-388">Recuperar los datos de tiempo de concesión de IANA del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-388">Retrieve the Client’s IANA lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-389">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-389">Prototype</span></span>

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a><span data-ttu-id="d690d-390">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-390">Description</span></span>

<span data-ttu-id="d690d-391">Este servicio recupera los datos globales de tiempo de concesión IA-NA del cliente (T1 y T2).</span><span class="sxs-lookup"><span data-stu-id="d690d-391">This service retrieves the Client’s global IA-NA lease time data (T1 and T2).</span></span> <span data-ttu-id="d690d-392">Si ninguna de las direcciones IA-NA del cliente tiene un estado de dirección válido, los datos de hora se establecen en cero y se devuelve un estado de finalización correcto.</span><span class="sxs-lookup"><span data-stu-id="d690d-392">If none of the Client IA-NA addresses have a valid address status, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="d690d-393">Si un cliente tiene más de una dirección IPv6 global, se devuelven los datos de la dirección IA principal.</span><span class="sxs-lookup"><span data-stu-id="d690d-393">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-394">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-394">Input Parameters</span></span>

- <span data-ttu-id="d690d-395">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-395">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-396">**T1** Puntero a hora de inicio de la renovación de la concesión</span><span class="sxs-lookup"><span data-stu-id="d690d-396">**T1** Pointer to time for starting lease renewal</span></span>

- <span data-ttu-id="d690d-397">**T2** Puntero a hora de inicio de la renovación de la concesión</span><span class="sxs-lookup"><span data-stu-id="d690d-397">**T2** Pointer to time for starting lease rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-398">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-398">Return Values</span></span>

- <span data-ttu-id="d690d-399">**NX_SUCCESS** (0x00) Datos de concesión de IANA recuperados correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-399">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="d690d-400">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-400">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-401">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-401">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-402">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-402">Allowed From</span></span>

<span data-ttu-id="d690d-403">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-403">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-404">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-404">Example</span></span>

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-405">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-405">See Also</span></span>

- <span data-ttu-id="d690d-406">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-406">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="d690d-407">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="d690d-407">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="d690d-408">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="d690d-408">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="d690d-409">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-409">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="d690d-410">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="d690d-410">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a><span data-ttu-id="d690d-411">nx_dhcpv6_get_valid_ip_address_count</span><span class="sxs-lookup"><span data-stu-id="d690d-411">nx_dhcpv6_get_valid_ip_address_count</span></span>

<span data-ttu-id="d690d-412">Recuperación de un recuento de direcciones IA válidas del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-412">Retrieve a count of Client’s valid IA addresses</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-413">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-413">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a><span data-ttu-id="d690d-414">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-414">Description</span></span>

<span data-ttu-id="d690d-415">Este servicio recupera el recuento de las direcciones IPv6 válidas del cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-415">This service retrieves the count of the Client’s valid IPv6 addresses.</span></span> <span data-ttu-id="d690d-416">Una dirección IPv6 válida está enlazada (asignada) al cliente y registrada con la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="d690d-416">A valid IPv6 address is bound (assigned) to the Client and registered with the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-417">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-417">Input Parameters</span></span>

- <span data-ttu-id="d690d-418">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-418">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-419">**address_count** Puntero al recuento de direcciones que se va a devolver</span><span class="sxs-lookup"><span data-stu-id="d690d-419">**address_count** Pointer to address count to return</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-420">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-420">Return Values</span></span>

- <span data-ttu-id="d690d-421">**NX_SUCCESS** (0x00) Datos de concesión de IANA recuperados correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-421">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="d690d-422">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-422">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-423">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-423">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-424">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-424">Allowed From</span></span>

<span data-ttu-id="d690d-425">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-425">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-426">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-426">Example</span></span>

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a><span data-ttu-id="d690d-427">nx_dhcpv6_get_valid_ip_address_lease_time</span><span class="sxs-lookup"><span data-stu-id="d690d-427">nx_dhcpv6_get_valid_ip_address_lease_time</span></span>

<span data-ttu-id="d690d-428">Recuperación de los datos del IA del cliente por índice de dirección</span><span class="sxs-lookup"><span data-stu-id="d690d-428">Retrieve the Client IA data by address index</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-429">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-429">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="d690d-430">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-430">Description</span></span>

<span data-ttu-id="d690d-431">Este servicio recupera la dirección IA del cliente y los datos de concesión por índice de dirección.</span><span class="sxs-lookup"><span data-stu-id="d690d-431">This service retrieves the Client’s IA address and lease data by address index.</span></span> <span data-ttu-id="d690d-432">Si se proporciona un índice no válido o la dirección IPv6 en dicho índice no es válida, el servicio devuelve un estado de error NX_DHCPV6_IA_ADDRESS_NOT_VALID.</span><span class="sxs-lookup"><span data-stu-id="d690d-432">If an invalid index is supplied, or the IPv6 address at that index is not valid, the service returns an NX_DHCPV6_IA_ADDRESS_NOT_VALID error status.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-433">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-433">Input Parameters</span></span>

- <span data-ttu-id="d690d-434">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-434">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-435">**address_index** Índice en la tabla IA de DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-435">**address_index** Index into DHCPv6 IA table</span></span>

- <span data-ttu-id="d690d-436">**ip_address** Puntero a la dirección IPv6 para recuperar</span><span class="sxs-lookup"><span data-stu-id="d690d-436">**ip_address** Pointer to IPv6 address to retrieve</span></span>

- <span data-ttu-id="d690d-437">**preferred_lifetime** Puntero a la hora en que la dirección IA está en desuso</span><span class="sxs-lookup"><span data-stu-id="d690d-437">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="d690d-438">**valid_lifetime** Puntero a la hora de expiración de la dirección IA</span><span class="sxs-lookup"><span data-stu-id="d690d-438">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-439">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-439">Return Values</span></span>

- <span data-ttu-id="d690d-440">**NX_SUCCESS** (0x00) Datos IANA recuperados correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-440">**NX_SUCCESS** (0x00) IANA data successfully retrieved</span></span>

- <span data-ttu-id="d690d-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0XEAD) Un índice no válido o una dirección IPv6 válida en el índice proporcionado</span><span class="sxs-lookup"><span data-stu-id="d690d-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) An invalid index or no valid IPv6 address at the supplied index</span></span> 

- <span data-ttu-id="d690d-442">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-442">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-443">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-443">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-444">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-444">Allowed From</span></span>

<span data-ttu-id="d690d-445">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-445">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-446">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-446">Example</span></span>

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="d690d-447">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-447">See Also</span></span>

- <span data-ttu-id="d690d-448">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-448">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="d690d-449">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="d690d-449">nx_dhcpv6_get_iana_lease_time</span></span>
- <span data-ttu-id="d690d-450">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="d690d-450">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_dns_server_address"></a><span data-ttu-id="d690d-451">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="d690d-451">nx_dhcpv6_get_DNS_server_address</span></span>

<span data-ttu-id="d690d-452">Recupera la dirección del servidor DNS</span><span class="sxs-lookup"><span data-stu-id="d690d-452">Retrieves DNS Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="d690d-453">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-453">Prototype</span></span>

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="d690d-454">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-454">Description</span></span>

<span data-ttu-id="d690d-455">Este servicio recupera los datos de la dirección IPv6 del servidor DNS en el índice especificado en la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="d690d-455">This service retrieves the DNS server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="d690d-456">Si la lista no contiene una dirección de servidor en el índice, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="d690d-456">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="d690d-457">Es posible que el índice no supere el tamaño de la lista de servidores DNS especificado por la opción configurable por el usuario NX_DHCPV6_NUM_DNS_SERVERS.</span><span class="sxs-lookup"><span data-stu-id="d690d-457">The index may not exceed the size of the DNS Server list is specified by the user configurable option NX_DHCPV6_NUM_DNS_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-458">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-458">Input Parameters</span></span>

- <span data-ttu-id="d690d-459">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-459">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-460">**Índice** El índice en la lista de servidores DNS</span><span class="sxs-lookup"><span data-stu-id="d690d-460">**index** Index into the DNS Server list</span></span>

- <span data-ttu-id="d690d-461">**server_address** Puntero al búfer de direcciones del servidor</span><span class="sxs-lookup"><span data-stu-id="d690d-461">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-462">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-462">Return Values</span></span>

- <span data-ttu-id="d690d-463">**NX_SUCCESS** (0x00) La dirección se recuperó correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-463">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="d690d-464">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-464">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-465">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-465">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-466">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-466">Allowed From</span></span>

<span data-ttu-id="d690d-467">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-467">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-468">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-468">Example</span></span>

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-469">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-469">See Also</span></span>

- <span data-ttu-id="d690d-470">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-470">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="d690d-471">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="d690d-471">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="d690d-472">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-472">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_other_option_data"></a><span data-ttu-id="d690d-473">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="d690d-473">nx_dhcpv6_get_other_option_data</span></span>

<span data-ttu-id="d690d-474">Recupera datos de opciones DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-474">Retrieves DHCPv6 option data</span></span> 

### <a name="prototype"></a><span data-ttu-id="d690d-475">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-475">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="d690d-476">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-476">Description</span></span>

<span data-ttu-id="d690d-477">Este servicio recupera datos de opciones DHCPv6 de un mensaje DHCPv6 para el código de opción especificado.</span><span class="sxs-lookup"><span data-stu-id="d690d-477">This service retrieves DHCPv6 option data from a DHCPv6 message for the specified option code.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-478">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-478">Input Parameters</span></span>

- <span data-ttu-id="d690d-479">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-479">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-480">código de **opción** código de opción para el que se recuperarán los datos</span><span class="sxs-lookup"><span data-stu-id="d690d-480">**option** code Option code for which data to retrieve</span></span>

- <span data-ttu-id="d690d-481">**búfer** Puntero al búfer en el que se van a copiar datos</span><span class="sxs-lookup"><span data-stu-id="d690d-481">**buffer** Pointer to buffer to copy data to</span></span> 

### <a name="return-values"></a><span data-ttu-id="d690d-482">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-482">Return Values</span></span>

- <span data-ttu-id="d690d-483">**NX_SUCCESS** (0x00) Datos de opción recuperados correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-483">**NX_SUCCESS** (0x00) Option data successfully retrieved</span></span>

- <span data-ttu-id="d690d-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Código de opción desconocido o no compatible</span><span class="sxs-lookup"><span data-stu-id="d690d-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Unknown/unsupported option code</span></span>

- <span data-ttu-id="d690d-485">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-485">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-486">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-486">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="d690d-487">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-487">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-488">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-488">Allowed From</span></span>

<span data-ttu-id="d690d-489">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-489">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-490">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-490">Example</span></span>

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-491">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-491">See Also</span></span>

- <span data-ttu-id="d690d-492">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-492">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="d690d-493">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="d690d-493">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="d690d-494">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-494">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_accrued"></a><span data-ttu-id="d690d-495">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-495">nx_dhcpv6_get_time_accrued</span></span>

<span data-ttu-id="d690d-496">Recupera el tiempo acumulado en la concesión de la dirección IP del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-496">Retrieves time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-497">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-497">Prototype</span></span>

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a><span data-ttu-id="d690d-498">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-498">Description</span></span>

<span data-ttu-id="d690d-499">Este servicio recupera el tiempo acumulado en la concesión de la dirección IPv6 del cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-499">This service retrieves the time accrued on the Client’s IPv6 address lease.</span></span> <span data-ttu-id="d690d-500">La función comprueba todas las direcciones IPv6 asignadas al cliente para la primera dirección válida.</span><span class="sxs-lookup"><span data-stu-id="d690d-500">The function checks all the IPv6 addresses assigned to the Client for the first valid address.</span></span> <span data-ttu-id="d690d-501">Si no se encuentran direcciones válidas, se devuelve un valor de cero para el tiempo acumulado.</span><span class="sxs-lookup"><span data-stu-id="d690d-501">If no valid addresses are found, a zero value for time accrued is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-502">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-502">Input Parameters</span></span>

- <span data-ttu-id="d690d-503">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-503">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-504">**time_accrued** Puntero al tiempo acumulado en la concesión de IP</span><span class="sxs-lookup"><span data-stu-id="d690d-504">**time_accrued** Pointer to time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-505">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-505">Return Values</span></span>

- <span data-ttu-id="d690d-506">**NX_SUCCESS** (0x00) Tiempo acumulado recuperado correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-506">**NX_SUCCESS** (0x00) Accrued time successfully retrieved</span></span>

- <span data-ttu-id="d690d-507">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-507">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-508">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-508">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-509">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-509">Allowed From</span></span>

<span data-ttu-id="d690d-510">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-510">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-511">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-511">Example</span></span>

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-512">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-512">See Also</span></span>

- <span data-ttu-id="d690d-513">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-513">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="d690d-514">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="d690d-514">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="d690d-515">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="d690d-515">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="d690d-516">nx_dhcpv6_set_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-516">nx_dhcpv6_set_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_server_address"></a><span data-ttu-id="d690d-517">nx_dhcpv6_get_time_server_address</span><span class="sxs-lookup"><span data-stu-id="d690d-517">nx_dhcpv6_get_time_server_address</span></span>

<span data-ttu-id="d690d-518">Recupera la dirección del servidor de tiempo</span><span class="sxs-lookup"><span data-stu-id="d690d-518">Retrieves Time Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="d690d-519">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-519">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="d690d-520">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-520">Description</span></span>

<span data-ttu-id="d690d-521">Este servicio recupera los datos de la dirección IPv6 del servidor de tiempo en el índice especificado en la lista de clientes.</span><span class="sxs-lookup"><span data-stu-id="d690d-521">This service retrieves the Time server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="d690d-522">Si la lista no contiene una dirección de servidor en el índice, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="d690d-522">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="d690d-523">El índice no puede exceder el tamaño de la lista de servidores de tiempo especificado por la opción configurable por el usuario NX_DHCPV6_NUM_TIME_SERVERS.</span><span class="sxs-lookup"><span data-stu-id="d690d-523">The index may not exceed the size of the Time Server list is specified by the user configurable option NX_DHCPV6_NUM_TIME_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-524">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-524">Input Parameters</span></span>

- <span data-ttu-id="d690d-525">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-525">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-526">**Índice** Índice en la lista de servidores de tiempo</span><span class="sxs-lookup"><span data-stu-id="d690d-526">**index** Index into the Time Server list</span></span>

- <span data-ttu-id="d690d-527">**server_address** Puntero al búfer de direcciones del servidor</span><span class="sxs-lookup"><span data-stu-id="d690d-527">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-528">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-528">Return Values</span></span>

- <span data-ttu-id="d690d-529">**NX_SUCCESS** (0x00) La dirección se recuperó correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-529">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="d690d-530">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-530">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-531">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-531">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-532">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-532">Allowed From</span></span>

<span data-ttu-id="d690d-533">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-533">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-534">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-534">Example</span></span>

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-535">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-535">See Also</span></span>

- <span data-ttu-id="d690d-536">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-536">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="d690d-537">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="d690d-537">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="d690d-538">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-538">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="d690d-539">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="d690d-539">nx_dhcpv6_get_DNS_server_address</span></span>

## <a name="nx_dhcpv6_reinitialize"></a><span data-ttu-id="d690d-540">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="d690d-540">nx_dhcpv6_reinitialize</span></span>

<span data-ttu-id="d690d-541">Quitar la dirección IP del cliente de la tabla IP</span><span class="sxs-lookup"><span data-stu-id="d690d-541">Remove the Client IP address from the IP table</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-542">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-542">Prototype</span></span>

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-543">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-543">Description</span></span>

<span data-ttu-id="d690d-544">Este servicio reinicializa el cliente para reiniciar la máquina de estados DHCPv6 y volver a ejecutar el protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-544">This service reinitializes the Client for restarting the DHCPv6 state machine and re-running the DHCPv6 protocol.</span></span> <span data-ttu-id="d690d-545">Esto no es necesario si el cliente no ha iniciado previamente el equipo de estado DHPCv6 o si se le ha asignado cualquier dirección IPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-545">This is not necessary if the Client has not previously started the DHPCv6 state machine or been assigned any IPv6 addresses.</span></span> <span data-ttu-id="d690d-546">Se desactivan las direcciones guardadas en el cliente DHCPv6 y registradas con la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="d690d-546">The addresses saved to the DHCPv6 Client as well as registered with the IP instance are both cleared.</span></span>

> [!NOTE]
> <span data-ttu-id="d690d-547">La aplicación todavía debe iniciar el cliente DHCPv6 mediante el *servicio de nx_dhcpv6_start* y comenzar la solicitud de asignación de direcciones IPv6 llamando a *nx_dhcpv6_request_solicit*.</span><span class="sxs-lookup"><span data-stu-id="d690d-547">The application must still start the DHCPv6 Client using the *nx_dhcpv6_start service* and begin the request for IPv6 address assignment by calling *nx_dhcpv6_request_solicit*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-548">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-548">Input Parameters</span></span>

- <span data-ttu-id="d690d-549">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-549">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-550">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-550">Return Values</span></span>

- <span data-ttu-id="d690d-551">**NX_SUCCESS** (0x00) La dirección se quitó correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-551">**NX_SUCCESS** (0x00) Address successfully removed</span></span>

- <span data-ttu-id="d690d-552">**NX_DHCPV6_ALREADY_STARTED** (0xE91) El cliente DHCPv6 ya se está ejecutando</span><span class="sxs-lookup"><span data-stu-id="d690d-552">**NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 Client is already running</span></span>

- <span data-ttu-id="d690d-553">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-553">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-554">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-554">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-555">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-555">Allowed From</span></span>

<span data-ttu-id="d690d-556">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-556">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-557">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-557">Example</span></span>

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-558">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-558">See Also</span></span>

- <span data-ttu-id="d690d-559">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="d690d-559">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="d690d-560">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="d690d-560">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_request_confirm"></a><span data-ttu-id="d690d-561">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="d690d-561">nx_dhcpv6_request_confirm</span></span>

<span data-ttu-id="d690d-562">Procesar el estado de CONFIRMACIÓN del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-562">Process the Client’s CONFIRM state</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-563">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-563">Prototype</span></span>

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-564">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-564">Description</span></span>

<span data-ttu-id="d690d-565">Este servicio envía una solicitud de confirmación.</span><span class="sxs-lookup"><span data-stu-id="d690d-565">This service sends a CONFIRM request.</span></span> <span data-ttu-id="d690d-566">Si se recibe una respuesta del servidor, el cliente DHCPv6 actualiza los parámetros de concesión con los datos recibidos.</span><span class="sxs-lookup"><span data-stu-id="d690d-566">If a reply is received from the Server, the DHCPv6 Client updates its lease parameters with the received data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-567">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-567">Input Parameters</span></span>

- <span data-ttu-id="d690d-568">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-568">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-569">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-569">Return Values</span></span>

- <span data-ttu-id="d690d-570">**NX_SUCCESS** (0x00) Mensaje de CONFIRMACIÓN enviado y procesado correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-570">**NX_SUCCESS** (0x00) CONFIRM message successfully sent and processed</span></span>

- <span data-ttu-id="d690d-571">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-571">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-572">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-572">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-573">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-573">Allowed From</span></span>

<span data-ttu-id="d690d-574">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-574">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-575">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-575">Example</span></span>

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-576">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-576">See Also</span></span>

- <span data-ttu-id="d690d-577">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="d690d-577">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="d690d-578">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="d690d-578">nx_dhcpv6_request_release</span></span>
- <span data-ttu-id="d690d-579">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="d690d-579">nx_dhcpv6_request_solicit</span></span>


## <a name="nx_dhcpv6_request_inform_request"></a><span data-ttu-id="d690d-580">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="d690d-580">nx_dhcpv6_request_inform_request</span></span>

<span data-ttu-id="d690d-581">Procesar el estado de SOLICITUD DE INFORME del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-581">Process the Client’s INFORM REQUEST state</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-582">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-582">Prototype</span></span>

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-583">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-583">Description</span></span>

<span data-ttu-id="d690d-584">Este servicio envía un mensaje de SOLICITUD DE INFORME.</span><span class="sxs-lookup"><span data-stu-id="d690d-584">This service sends an INFORM REQUEST message.</span></span> <span data-ttu-id="d690d-585">Si se recibe una respuesta, cuando se recibe una, se procesa la respuesta para determinar si es válida y el servidor ha concedido la solicitud.</span><span class="sxs-lookup"><span data-stu-id="d690d-585">If a reply is received, When one is received, the reply is processed to determine it is valid and the server granted the request.</span></span> <span data-ttu-id="d690d-586">La instancia del cliente se actualiza entonces con la información del servidor según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="d690d-586">The Client instance is then updated with the server information as needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-587">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-587">Input Parameters</span></span>

- <span data-ttu-id="d690d-588">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-588">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-589">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-589">Return Values</span></span>

- <span data-ttu-id="d690d-590">**NX_SUCCESS** (0x00) Se creó y procesó correctamente el mensaje de SOLICITUD DE INFORME</span><span class="sxs-lookup"><span data-stu-id="d690d-590">**NX_SUCCESS** (0x00) INFORM REQUEST message successfully created and processed</span></span>

- <span data-ttu-id="d690d-591">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-591">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-592">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-592">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-593">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-593">Allowed From</span></span>

<span data-ttu-id="d690d-594">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-595">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-595">Example</span></span>

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-596">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-596">See Also</span></span>

- <span data-ttu-id="d690d-597">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="d690d-597">nx_dhcpv6_request_confirm</span></span>

## <a name="nx_dhcpv6_request_option_dns_server"></a><span data-ttu-id="d690d-598">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="d690d-598">nx_dhcpv6_request_option_DNS_server</span></span>

<span data-ttu-id="d690d-599">Agregar servidor DNS a solicitud de opción DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-599">Add DNS Server to DHCPv6 Option request</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-600">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-600">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-601">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-601">Description</span></span>

<span data-ttu-id="d690d-602">Este servicio agrega la opción para solicitar información del servidor DNS a la solicitud de la opción DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-602">This service adds the option for requesting DNS server information to the DHCPv6 option request.</span></span> <span data-ttu-id="d690d-603">Si la respuesta del servidor incluye datos del servidor DNS, el cliente almacenará el servidor DNS si tiene espacio para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="d690d-603">If the Server reply includes DNS server data, the Client will store the DNS server if it has room to do so.</span></span> <span data-ttu-id="d690d-604">El número de servidores DNS que puede almacenar el cliente viene determinado por la opción configurable NX_DHCPV6_NUM_DNS_SERVERS cuyo valor predeterminado es 2.</span><span class="sxs-lookup"><span data-stu-id="d690d-604">The number of DNS servers the Client can store is determined by the configurable option NX_DHCPV6_NUM_DNS_SERVERS whose default value is 2.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-605">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-605">Input Parameters</span></span>

- <span data-ttu-id="d690d-606">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-606">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-607">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-607">Return Values</span></span>

- <span data-ttu-id="d690d-608">**NX_SUCCESS** (0x00) Se incluye la opción de servidor DNS</span><span class="sxs-lookup"><span data-stu-id="d690d-608">**NX_SUCCESS** (0x00) DNS server option is included</span></span>

- <span data-ttu-id="d690d-609">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-609">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-610">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-610">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-611">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-611">Allowed From</span></span>

<span data-ttu-id="d690d-612">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-613">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-613">Example</span></span>

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="d690d-614">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-614">See Also</span></span>

- <span data-ttu-id="d690d-615">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="d690d-615">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="d690d-616">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="d690d-616">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="d690d-617">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="d690d-617">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_fqdn"></a><span data-ttu-id="d690d-618">nx_dhcpv6_request_option_FQDN</span><span class="sxs-lookup"><span data-stu-id="d690d-618">nx_dhcpv6_request_option_FQDN</span></span>

<span data-ttu-id="d690d-619">Agregar la opción nombre de dominio completo a la lista de solicitudes de opción</span><span class="sxs-lookup"><span data-stu-id="d690d-619">Add Fully Qualified Domain Name option to Option request list</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-620">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-620">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a><span data-ttu-id="d690d-621">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-621">Description</span></span>

<span data-ttu-id="d690d-622">Este servicio agrega la opción para agregar el nombre de dominio completo del cliente a la solicitud de la opción DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-622">This service adds the option for adding the Client Fully Qualified Domain Name to the DHCPv6 option request.</span></span> <span data-ttu-id="d690d-623">Hay tres opciones para la opción FQDN:</span><span class="sxs-lookup"><span data-stu-id="d690d-623">There are three options for the FQDN option:</span></span>

- <span data-ttu-id="d690d-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Actualice la asignación de direcciones FQDN a IPv6 para FQDN y direcciones utilizadas por el cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client.</span></span>

- <span data-ttu-id="d690d-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Actualice la asignación de direcciones FQDN a IPv6 para FQDN y direcciones que usa el cliente al servidor.</span><span class="sxs-lookup"><span data-stu-id="d690d-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client to the server.</span></span>

- <span data-ttu-id="d690d-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Solicite al servidor que no realice actualizaciones de DNS en nombre del Cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Request the server perform no DNS updates on the Client’s behalf.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-627">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-627">Input Parameters</span></span>

- <span data-ttu-id="d690d-628">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-628">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-629">**domain_name** Cadena que contiene el nombre de dominio</span><span class="sxs-lookup"><span data-stu-id="d690d-629">**domain_name** String holding the domain name</span></span>

- <span data-ttu-id="d690d-630">**operación** Tipo de opción de FQDN que se va a aplicar (vea la lista anterior)</span><span class="sxs-lookup"><span data-stu-id="d690d-630">**op** Type of FQDN option to apply (see list above)</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-631">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-631">Return Values</span></span>

- <span data-ttu-id="d690d-632">**NX_SUCCESS** (0x00) Se incluye la opción de FQDN</span><span class="sxs-lookup"><span data-stu-id="d690d-632">**NX_SUCCESS** (0x00) FQDN option is included</span></span>

- <span data-ttu-id="d690d-633">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-633">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-634">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-634">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-635">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-635">Allowed From</span></span>

<span data-ttu-id="d690d-636">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-637">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-637">Example</span></span>

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a><span data-ttu-id="d690d-638">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-638">See Also</span></span>

- <span data-ttu-id="d690d-639">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="d690d-639">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="d690d-640">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="d690d-640">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="d690d-641">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="d690d-641">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_domain_name"></a><span data-ttu-id="d690d-642">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="d690d-642">nx_dhcpv6_request_option_domain_name</span></span>

<span data-ttu-id="d690d-643">Agregar opción de nombre de dominio a solicitud de opción DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-643">Add domain name option to DHCPv6 option request</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-644">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-644">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-645">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-645">Description</span></span>

<span data-ttu-id="d690d-646">Este servicio agrega la opción de nombre de dominio a la opción solicitud en los mensajes de solicitud de cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-646">This service adds the domain name option to the option request in Client request messages.</span></span> <span data-ttu-id="d690d-647">Si la respuesta del servidor incluye datos de nombre de dominio, el cliente almacenará la información del nombre de dominio si el tamaño del nombre de dominio se encuentra dentro del tamaño del búfer para contener el nombre de dominio.</span><span class="sxs-lookup"><span data-stu-id="d690d-647">If the Server reply includes domain name data, the Client will store the domain name information if the size of the domain name is within the buffer size for holding the domain name.</span></span> <span data-ttu-id="d690d-648">Este tamaño de búfer es una opción configurable (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) con un valor predeterminado de 30 bytes.</span><span class="sxs-lookup"><span data-stu-id="d690d-648">This buffer size is a configurable option (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) with a default value of 30 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-649">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-649">Input Parameters</span></span>

- <span data-ttu-id="d690d-650">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-650">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-651">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-651">Return Values</span></span>

- <span data-ttu-id="d690d-652">**NX_SUCCESS** (0x00) Conjunto de opciones de nombre de dominio</span><span class="sxs-lookup"><span data-stu-id="d690d-652">**NX_SUCCESS** (0x00) Domain name option set</span></span>

- <span data-ttu-id="d690d-653">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-653">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-654">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-654">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-655">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-655">Allowed From</span></span>

<span data-ttu-id="d690d-656">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-657">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-657">Example</span></span>

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="d690d-658">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-658">See Also</span></span>

- <span data-ttu-id="d690d-659">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="d690d-659">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="d690d-660">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="d690d-660">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="d690d-661">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="d690d-661">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_time_server"></a><span data-ttu-id="d690d-662">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="d690d-662">nx_dhcpv6_request_option_time_server</span></span>

<span data-ttu-id="d690d-663">Establecer datos del servidor de tiempo como solicitud opcional</span><span class="sxs-lookup"><span data-stu-id="d690d-663">Set time server data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-664">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-664">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-665">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-665">Description</span></span>

<span data-ttu-id="d690d-666">Este servicio agrega la opción de información de servidor de tiempo a la opción solicitud de mensajes de solicitud de cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-666">This service adds the option for time server information to the option request of Client request messages.</span></span> <span data-ttu-id="d690d-667">Si la respuesta del servidor incluye datos del servidor Tim, el cliente almacenará el servidor de tiempo si tiene espacio para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="d690d-667">If the Server reply includes tim server data, the Client will store the time server if it has room to do so.</span></span> <span data-ttu-id="d690d-668">El número de servidores de tiempo que el cliente puede almacenar viene determinado por la opción configurable</span><span class="sxs-lookup"><span data-stu-id="d690d-668">The number of time servers the Client can store is determined by the configurable option</span></span>

<span data-ttu-id="d690d-669">NX_DHCPV6_NUM_TIME _SERVERS cuyo valor predeterminado es 1.</span><span class="sxs-lookup"><span data-stu-id="d690d-669">NX_DHCPV6_NUM_TIME _SERVERS whose default value is 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-670">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-670">Input Parameters</span></span>

- <span data-ttu-id="d690d-671">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-671">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-672">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-672">Return Values</span></span>

- <span data-ttu-id="d690d-673">**NX_SUCCESS** (0x00) Opción de servidor de tiempo agregada</span><span class="sxs-lookup"><span data-stu-id="d690d-673">**NX_SUCCESS** (0x00) Time server option added</span></span>

- <span data-ttu-id="d690d-674">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-674">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-675">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-675">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-676">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-676">Allowed From</span></span>

<span data-ttu-id="d690d-677">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-677">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-678">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-678">Example</span></span>

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="d690d-679">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-679">See Also</span></span>

- <span data-ttu-id="d690d-680">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="d690d-680">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="d690d-681">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="d690d-681">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="d690d-682">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="d690d-682">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_timezone"></a><span data-ttu-id="d690d-683">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="d690d-683">nx_dhcpv6_request_option_timezone</span></span>

<span data-ttu-id="d690d-684">Establecer datos de la zona horaria como solicitud opcional</span><span class="sxs-lookup"><span data-stu-id="d690d-684">Set time zone data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-685">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-685">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-686">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-686">Description</span></span>

<span data-ttu-id="d690d-687">Este servicio agrega la opción para solicitar información de zona horaria a la solicitud de opción de cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-687">This service adds the option for requesting time zone information to the Client option request.</span></span> <span data-ttu-id="d690d-688">Si la respuesta del servidor incluye datos de zona horaria, el cliente almacenará la información de zona horaria si el tamaño de la zona horaria está dentro del tamaño del búfer para contener la zona horaria.</span><span class="sxs-lookup"><span data-stu-id="d690d-688">If the Server reply includes time zone data, the Client will store the time zone information if the size of the time zone is within the buffer size for holding the time zone.</span></span> <span data-ttu-id="d690d-689">Este tamaño de búfer es una opción configurable (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) con un valor predeterminado de 10 bytes.</span><span class="sxs-lookup"><span data-stu-id="d690d-689">This buffer size is a configurable option (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) with a default value of 10 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-690">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-690">Input Parameters</span></span>

- <span data-ttu-id="d690d-691">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-691">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-692">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-692">Return Values</span></span>

- <span data-ttu-id="d690d-693">**NX_SUCCESS** (0x00) Opción de zona horaria agregada</span><span class="sxs-lookup"><span data-stu-id="d690d-693">**NX_SUCCESS** (0x00) Time zone option added</span></span>

- <span data-ttu-id="d690d-694">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-694">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-695">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-695">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-696">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-696">Allowed From</span></span>

<span data-ttu-id="d690d-697">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-698">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-698">Example</span></span>

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="d690d-699">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-699">See Also</span></span>

- <span data-ttu-id="d690d-700">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="d690d-700">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="d690d-701">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="d690d-701">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="d690d-702">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="d690d-702">nx_dhcpv6_request_option_time_server</span></span>

## <a name="nx_dhcpv6_request_release"></a><span data-ttu-id="d690d-703">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="d690d-703">nx_dhcpv6_request_release</span></span>

<span data-ttu-id="d690d-704">Enviar un mensaje de VERSIÓN DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-704">Send a DHCPv6 RELEASE message</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-705">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-705">Prototype</span></span>

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-706">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-706">Description</span></span>

<span data-ttu-id="d690d-707">Este servicio envía un mensaje de VERSIÓN en la red del cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-707">This service sends a RELEASE message on the Client network.</span></span> <span data-ttu-id="d690d-708">Si el mensaje se envía correctamente, se devuelve un estado correcto.</span><span class="sxs-lookup"><span data-stu-id="d690d-708">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="d690d-709">Una finalización correcta no significa que el cliente reciba una respuesta o que se le haya concedido todavía una dirección IPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-709">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="d690d-710">La tarea de subproceso de cliente DHCPv6 espera una respuesta de un servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-710">The DHCPv6 Client thread task waits for a reply from a DHCPv6 Server.</span></span> <span data-ttu-id="d690d-711">Si se recibe uno, comprueba que la respuesta es válida y almacena los datos en el registro de cliente.</span><span class="sxs-lookup"><span data-stu-id="d690d-711">If one is received, it checks the reply is valid and stores the data to the Client record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-712">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-712">Input Parameters</span></span>

- <span data-ttu-id="d690d-713">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-713">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-714">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-714">Return Values</span></span>

- <span data-ttu-id="d690d-715">**NX_SUCCESS** (0x00) Mensaje de VERSIÓN enviado correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-715">**NX_SUCCESS** (0x00) RELEASE message successfully sent</span></span>

- <span data-ttu-id="d690d-716">**NX_DHCPV6_NOT_STARTED** (0xE92) Tarea de cliente DHCPv6 no iniciada</span><span class="sxs-lookup"><span data-stu-id="d690d-716">**NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Client task not started</span></span>

- <span data-ttu-id="d690d-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Dirección no enlazada al cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Address not bound to Client</span></span>

- <span data-ttu-id="d690d-718">**NX_INVALID_INTERFACE** (0x4C) No se encontró en la tabla de direcciones IP</span><span class="sxs-lookup"><span data-stu-id="d690d-718">**NX_INVALID_INTERFACE** (0x4C) Not found in IP address table</span></span>

- <span data-ttu-id="d690d-719">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-719">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-720">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-720">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-721">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-721">Allowed From</span></span>

<span data-ttu-id="d690d-722">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-722">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-723">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-723">Example</span></span>

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-724">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-724">See Also</span></span>

- <span data-ttu-id="d690d-725">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="d690d-725">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="d690d-726">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="d690d-726">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="d690d-727">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="d690d-727">nx_dhcpv6_request_solicit</span></span>

## <a name="nx_dhcpv6_request_solicit"></a><span data-ttu-id="d690d-728">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="d690d-728">nx_dhcpv6_request_solicit</span></span>

<span data-ttu-id="d690d-729">Enviar un mensaje de PETICIÓN</span><span class="sxs-lookup"><span data-stu-id="d690d-729">Send a SOLICIT message</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-730">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-730">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-731">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-731">Description</span></span>

<span data-ttu-id="d690d-732">Este servicio envía un mensaje de PETICIÓN a la red.</span><span class="sxs-lookup"><span data-stu-id="d690d-732">This service sends a SOLICIT message out on the network.</span></span> <span data-ttu-id="d690d-733">Si el mensaje se envía correctamente, se devuelve un estado correcto.</span><span class="sxs-lookup"><span data-stu-id="d690d-733">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="d690d-734">Una finalización correcta no significa que el cliente reciba una respuesta o que se le haya concedido todavía una dirección IPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-734">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="d690d-735">La tarea de subproceso de cliente DHCPv6 espera una respuesta (un mensaje de ANUNCIO) de un servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-735">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="d690d-736">Si se recibe uno, comprueba que la respuesta es válida, almacena los datos en el registro de cliente y promueve el cliente al estado de la SOLICITUD.</span><span class="sxs-lookup"><span data-stu-id="d690d-736">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the REQUEST state.</span></span>

> [!NOTE] 
> <span data-ttu-id="d690d-737">Si se establece la opción de confirmación rápida, el cliente DHCPv6 irá directamente al estado enlazado si recibe un mensaje de ANUNCIO de servidor válido.</span><span class="sxs-lookup"><span data-stu-id="d690d-737">If the Rapid Commit option is set, the DHCPv6 Client will go directly to the Bound state if it receives a valid Server ADVERTISE message.</span></span> <span data-ttu-id="d690d-738">Para obtener más información, consulte la descripción del servicio para obtener *nx_dhcpv6_request_solicit_rapid*.</span><span class="sxs-lookup"><span data-stu-id="d690d-738">See the service description for *nx_dhcpv6_request_solicit_rapid* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-739">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-739">Input Parameters</span></span>

- <span data-ttu-id="d690d-740">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-740">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-741">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-741">Return Values</span></span>

- <span data-ttu-id="d690d-742">**NX_SUCCESS** (0x00) Mensaje de PETICIÓN enviado correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-742">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="d690d-743">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-743">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-744">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-744">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-745">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-745">Allowed From</span></span>

<span data-ttu-id="d690d-746">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-746">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-747">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-747">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a><span data-ttu-id="d690d-748">nx_dhcpv6_request_solicit_rapid</span><span class="sxs-lookup"><span data-stu-id="d690d-748">nx_dhcpv6_request_solicit_rapid</span></span>

<span data-ttu-id="d690d-749">Enviar un mensaje de PETICIÓN con la opción de confirmación rápida</span><span class="sxs-lookup"><span data-stu-id="d690d-749">Send a SOLICIT message with the Rapid Commit option</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-750">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-750">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-751">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-751">Description</span></span>

<span data-ttu-id="d690d-752">Este servicio envía un mensaje de PETICIÓN en la red con la opción de confirmación rápida establecida.</span><span class="sxs-lookup"><span data-stu-id="d690d-752">This service sends a SOLICIT message out on the network with the Rapid Commit option set.</span></span> <span data-ttu-id="d690d-753">Si el mensaje se envía correctamente, se devuelve un estado correcto.</span><span class="sxs-lookup"><span data-stu-id="d690d-753">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="d690d-754">Una finalización correcta no significa que el cliente reciba una respuesta o que se le haya concedido todavía una dirección IPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-754">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="d690d-755">La tarea de subproceso de cliente DHCPv6 espera una respuesta (un mensaje de ANUNCIO) de un servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-755">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="d690d-756">Si se recibe uno, comprueba que la respuesta es válida, almacena los datos en el registro de cliente y promueve el cliente al estado ENLAZADO.</span><span class="sxs-lookup"><span data-stu-id="d690d-756">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the BOUND state.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-757">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-757">Input Parameters</span></span>

- <span data-ttu-id="d690d-758">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-758">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-759">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-759">Return Values</span></span>

- <span data-ttu-id="d690d-760">**NX_SUCCESS** (0x00) Mensaje de PETICIÓN enviado correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-760">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="d690d-761">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-761">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-762">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-762">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-763">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-763">Allowed From</span></span>

<span data-ttu-id="d690d-764">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-765">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-765">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-766">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-766">See Also</span></span>

- <span data-ttu-id="d690d-767">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="d690d-767">nx_dhcpv6_request_solicit</span></span>
- <span data-ttu-id="d690d-768">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="d690d-768">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="d690d-769">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="d690d-769">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="d690d-770">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="d690d-770">nx_dhcpv6_request_release</span></span>

## <a name="nx_dhcpv6_resume"></a><span data-ttu-id="d690d-771">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="d690d-771">nx_dhcpv6_resume</span></span>

<span data-ttu-id="d690d-772">Reanudar tarea de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-772">Resume DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="d690d-773">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-773">Prototype</span></span>

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-774">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-774">Description</span></span>

<span data-ttu-id="d690d-775">Este servicio reanuda la tarea de subproceso de cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-775">This service resumes the DHCPv6 Client thread task.</span></span> <span data-ttu-id="d690d-776">Se procesará el estado del cliente DHCPv6 actual (por ejemplo, enlazado, petición)</span><span class="sxs-lookup"><span data-stu-id="d690d-776">The current DHCPv6 Client state will be processed (e.g. Bound, Solicit)</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-777">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-777">Input Parameters</span></span>

- <span data-ttu-id="d690d-778">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-778">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-779">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-779">Return Values</span></span>

- <span data-ttu-id="d690d-780">**NX_SUCCESS** (0x00) El cliente se reanudó correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-780">**NX_SUCCESS** (0x00) Client successfully resumed</span></span>

- <span data-ttu-id="d690d-781">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-781">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-782">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-782">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-783">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-783">Allowed From</span></span>

<span data-ttu-id="d690d-784">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-784">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-785">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-785">Example</span></span>

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-786">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-786">See Also</span></span>

- <span data-ttu-id="d690d-787">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="d690d-787">nx_dhcpv6_start</span></span>
- <span data-ttu-id="d690d-788">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="d690d-788">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="d690d-789">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="d690d-789">nx_dhcpv6_suspend</span></span>

## <a name="nx_dhcpv6_set_-time_accrued"></a><span data-ttu-id="d690d-790">nx_dhcpv6_set_ time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-790">nx_dhcpv6_set_ time_accrued</span></span>

<span data-ttu-id="d690d-791">Establece el tiempo acumulado en la concesión de la dirección IP del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-791">Sets time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="d690d-792">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-792">Prototype</span></span>

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a><span data-ttu-id="d690d-793">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-793">Description</span></span>

<span data-ttu-id="d690d-794">Este servicio establece el tiempo acumulado en la dirección IP global del cliente desde que fue asignada por el servidor.</span><span class="sxs-lookup"><span data-stu-id="d690d-794">This service sets the time accrued on the Client’s global IP address since it was assigned by the server.</span></span> <span data-ttu-id="d690d-795">Solo debe usarse si un cliente está enlazado actualmente a una dirección IPv6 asignada.</span><span class="sxs-lookup"><span data-stu-id="d690d-795">This should only be used if a Client is currently bound to an assigned IPv6 address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-796">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-796">Input Parameters</span></span>

- <span data-ttu-id="d690d-797">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-797">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="d690d-798">**time_accrued** Tiempo acumulado en la concesión de IP</span><span class="sxs-lookup"><span data-stu-id="d690d-798">**time_accrued** Time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-799">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-799">Return Values</span></span>

- <span data-ttu-id="d690d-800">**NX_SUCCESS** (0x00) Tiempo acumulado correctamente establecido</span><span class="sxs-lookup"><span data-stu-id="d690d-800">**NX_SUCCESS** (0x00) Time accrued successfully set</span></span>

- <span data-ttu-id="d690d-801">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-801">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-802">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-802">Allowed From</span></span>

<span data-ttu-id="d690d-803">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-804">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-804">Example</span></span>

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-805">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-805">See Also</span></span>

- <span data-ttu-id="d690d-806">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="d690d-806">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="d690d-807">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="d690d-807">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="d690d-808">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="d690d-808">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="d690d-809">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="d690d-809">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_start"></a><span data-ttu-id="d690d-810">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="d690d-810">nx_dhcpv6_start</span></span>

<span data-ttu-id="d690d-811">Iniciar la tarea de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-811">Start the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="d690d-812">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-812">Prototype</span></span>

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-813">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-813">Description</span></span>

<span data-ttu-id="d690d-814">Este servicio inicia la tarea de cliente DHCPv6 y prepara el cliente para ejecutar el protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-814">This service starts the DHCPv6 Client task and prepares the Client for running the DHCPv6 protocol.</span></span> <span data-ttu-id="d690d-815">Comprueba que la instancia de cliente tiene suficiente información (por ejemplo, un DUID de cliente), crea y enlaza el socket UDP para enviar y recibir mensajes DHCPv6 y activa temporizadores para realizar un seguimiento del tiempo de sesión y cuando expira la concesión de IPv6 actual.</span><span class="sxs-lookup"><span data-stu-id="d690d-815">It verifies the Client instance has sufficient information (such as a Client DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages and activates timers for keeping track of session time and when the current IPv6 lease expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-816">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-816">Input Parameters</span></span>

- <span data-ttu-id="d690d-817">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-817">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-818">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-818">Return Values</span></span>

- <span data-ttu-id="d690d-819">**NX_SUCCESS** (0x00) Se inició correctamente el cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-819">**NX_SUCCESS** (0x00) Client successfully started</span></span>

- <span data-ttu-id="d690d-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Faltan las opciones necesarias del cliente</span><span class="sxs-lookup"><span data-stu-id="d690d-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Client missing required options</span></span>

- <span data-ttu-id="d690d-821">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-821">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-822">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-822">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-823">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-823">Allowed From</span></span>

<span data-ttu-id="d690d-824">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-824">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-825">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-825">Example</span></span>

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-826">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-826">See Also</span></span>

- <span data-ttu-id="d690d-827">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="d690d-827">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="d690d-828">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="d690d-828">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="d690d-829">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="d690d-829">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="d690d-830">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="d690d-830">nx_dhcpv6_reinitialize</span></span>

## <a name="nx_dhcpv6_stop"></a><span data-ttu-id="d690d-831">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="d690d-831">nx_dhcpv6_stop</span></span>

<span data-ttu-id="d690d-832">Detener la tarea de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-832">Stop the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="d690d-833">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-833">Prototype</span></span>

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-834">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-834">Description</span></span>

<span data-ttu-id="d690d-835">Este servicio detiene la tarea de cliente DHCPv6 y borra los recuentos de retransmisión, el intervalo máximo de retransmisión, desactiva los temporizadores de expiración de la sesión y la concesión y desenlaza el puerto de socket de cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-835">This service stops the DHCPv6 Client task, and clears retransmission counts, maximum retransmission intervals, deactivates the session and lease expiration timers, and unbinds the DHCPv6 Client socket port.</span></span> <span data-ttu-id="d690d-836">Para reiniciar el cliente, primero debe detenerse y, opcionalmente, reinicializar el cliente antes de iniciar otra sesión con cualquier servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="d690d-836">To restart the Client, one must first stop and optionally reinitialize the Client before starting another session with any DHCPv6 server.</span></span> <span data-ttu-id="d690d-837">Para más detalles, consulte la sección Ejemplo pequeño.</span><span class="sxs-lookup"><span data-stu-id="d690d-837">See the Small Example section for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-838">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-838">Input Parameters</span></span>

- <span data-ttu-id="d690d-839">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-839">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-840">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-840">Return Values</span></span>

- <span data-ttu-id="d690d-841">**NX_SUCCESS** (0x00) El cliente se detuvo correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-841">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>

- <span data-ttu-id="d690d-842">**NX_DHCPV6_NOT_STARTED** (0xE92) Subproceso de cliente no iniciado</span><span class="sxs-lookup"><span data-stu-id="d690d-842">**NX_DHCPV6_NOT_STARTED** (0xE92) Client thread not started</span></span>

- <span data-ttu-id="d690d-843">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-843">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-844">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-844">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>


### <a name="allowed-from"></a><span data-ttu-id="d690d-845">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-845">Allowed From</span></span>

<span data-ttu-id="d690d-846">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-847">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-847">Example</span></span>

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-848">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-848">See Also</span></span>

- <span data-ttu-id="d690d-849">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="d690d-849">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="d690d-850">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="d690d-850">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="d690d-851">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="d690d-851">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="d690d-852">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="d690d-852">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_suspend"></a><span data-ttu-id="d690d-853">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="d690d-853">nx_dhcpv6_suspend</span></span>

<span data-ttu-id="d690d-854">Suspender la tarea de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-854">Suspend the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="d690d-855">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d690d-855">Prototype</span></span>

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="d690d-856">Descripción</span><span class="sxs-lookup"><span data-stu-id="d690d-856">Description</span></span>

<span data-ttu-id="d690d-857">Este servicio suspende la tarea de cliente DHCPv6 y cualquier solicitud que se encontraba en medio del procesamiento.</span><span class="sxs-lookup"><span data-stu-id="d690d-857">This service suspends the DHCPv6 client task and any request it was in the middle of processing.</span></span> <span data-ttu-id="d690d-858">Los temporizadores se desactivan y el estado del cliente se establece en no en ejecución.</span><span class="sxs-lookup"><span data-stu-id="d690d-858">Timers are deactivated and the Client state is set to non-running.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d690d-859">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d690d-859">Input Parameters</span></span>

- <span data-ttu-id="d690d-860">**dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="d690d-860">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="d690d-861">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d690d-861">Return Values</span></span>

- <span data-ttu-id="d690d-862">**NX_SUCCESS** (0x00) El cliente se suspendió correctamente</span><span class="sxs-lookup"><span data-stu-id="d690d-862">**NX_SUCCESS** (0x00) Client successfully suspended</span></span>

- <span data-ttu-id="d690d-863">**NX_DHCPV6_NOT_STARTED** (0XE92) El cliente no se está ejecutando, por lo que no se puede suspender</span><span class="sxs-lookup"><span data-stu-id="d690d-863">**NX_DHCPV6_NOT_STARTED** (0XE92) Client not running so cannot be suspended</span></span>

- <span data-ttu-id="d690d-864">NX_PTR_ERROR: (0x16) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d690d-864">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="d690d-865">NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso</span><span class="sxs-lookup"><span data-stu-id="d690d-865">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d690d-866">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d690d-866">Allowed From</span></span>

<span data-ttu-id="d690d-867">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d690d-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d690d-868">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d690d-868">Example</span></span>

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a><span data-ttu-id="d690d-869">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d690d-869">See Also</span></span>

- <span data-ttu-id="d690d-870">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="d690d-870">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="d690d-871">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="d690d-871">nx_dhcpv6_start</span></span>
- <span data-ttu-id="d690d-872">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="d690d-872">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="d690d-873">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="d690d-873">nx_dhcpv6_stop</span></span>
