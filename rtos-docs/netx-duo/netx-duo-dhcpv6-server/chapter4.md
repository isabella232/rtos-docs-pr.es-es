---
title: 'Capítulo 4: Servicios de servidor DHCPv6 de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios de servidor DHCPv6 de NetX Duo
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814738"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a><span data-ttu-id="ebe35-103">Capítulo 4: Servicios de servidor DHCPv6 de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ebe35-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 server services</span></span>

<span data-ttu-id="ebe35-104">Este capítulo contiene una descripción de todos los servicios de servidor DHCPv6 de NetX Duo (enumerados a continuación).</span><span class="sxs-lookup"><span data-stu-id="ebe35-104">This chapter contains a description of all NetX Duo DHCPv6Server services (listed below).</span></span>

<span data-ttu-id="ebe35-105">En la sección “Valores devueltos” de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="ebe35-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ebe35-106">nx_dhcpv6_server_create *Crear una instancia de servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ebe35-106">nx_dhcpv6_server_create *Create a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="ebe35-107">nx_dhcpv6_server_delete *Eliminar una instancia de servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ebe35-107">nx_dhcpv6_server_delete *Delete a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="ebe35-108">nx_dhcpv6_server_start *Iniciar una tarea de servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ebe35-108">nx_dhcpv6_server_start *Start the DHCPv6 server task*</span></span>
- <span data-ttu-id="ebe35-109">nx_dhcpv6_server_suspend *Suspender la tarea de servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ebe35-109">nx_dhcpv6_server_suspend *Suspend the DHCPv6 server task*</span></span>
- <span data-ttu-id="ebe35-110">nx_dhcpv6_server_resume *Reanudar el procesamiento del cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ebe35-110">nx_dhcpv6_server_resume *Resume DHCPv6 client processing*</span></span>
- <span data-ttu-id="ebe35-111">nx_dhcpv6_server_suspend *Suspender el procesamiento del cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ebe35-111">nx_dhcpv6_server_suspend *Suspend DHCPv6 client processing*</span></span>
- <span data-ttu-id="ebe35-112">nx_dhcpv6_create_dns_address *Establecer el servidor DNS para las solicitudes de opción*</span><span class="sxs-lookup"><span data-stu-id="ebe35-112">nx_dhcpv6_create_dns_address *Set the DNS server for option requests*</span></span>
- <span data-ttu-id="ebe35-113">nx_dhcpv6_create_ip_address_range *Crear el intervalo de direcciones IP que se va a conceder*</span><span class="sxs-lookup"><span data-stu-id="ebe35-113">nx_dhcpv6_create_ip_address_range *Create the range of IP addresses to lease*</span></span>
- <span data-ttu-id="ebe35-114">nx_dhcpv6_reserve_ip_address_range *Reservar el intervalo de direcciones IP en la lista de servidores*</span><span class="sxs-lookup"><span data-stu-id="ebe35-114">nx_dhcpv6_reserve_ip_address_range *Reserve range of IP addresses in server list*</span></span>
- <span data-ttu-id="ebe35-115">nx_dhcpv6_set_server_duid *Establecer el DUID de servidor para paquetes DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ebe35-115">nx_dhcpv6_set_server_duid *Set the Server DUID for DHCPv6 packets*</span></span>
- <span data-ttu-id="ebe35-116">nx_dhcpv6_add_ip_address_lease *Agregar un registro de concesión a la tabla de servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ebe35-116">nx_dhcpv6_add_ip_address_lease *Add a lease record to the DHCPv6 server table*</span></span>
- <span data-ttu-id="ebe35-117">Nx_dhcpv6_retrieve_ip_address_lease *Recuperar un registro de concesión de direcciones IP de la tabla de servidor*</span><span class="sxs-lookup"><span data-stu-id="ebe35-117">Nx_dhcpv6_retrieve_ip_address_lease *Retrieve an IP lease record from the Server table*</span></span>
- <span data-ttu-id="ebe35-118">nx_dhcpv6_add_client_record *Agregar un registro de cliente DHCPv6 a la tabla de servidor*</span><span class="sxs-lookup"><span data-stu-id="ebe35-118">nx_dhcpv6_add_client_record *Add a DHCPv6 Client record to the Server table*</span></span>
- <span data-ttu-id="ebe35-119">nx_dhcpv6_retrieve_client_record *Recuperar un registro de cliente de la tabla de servidor*</span><span class="sxs-lookup"><span data-stu-id="ebe35-119">nx_dhcpv6_retrieve_client_record *Retrieve a client record from the Server table*</span></span>
- <span data-ttu-id="ebe35-120">nx_dhcpv6_server_interface_set *Establecer el índice de interfaz para los servicios DHCPv6 de servidor*</span><span class="sxs-lookup"><span data-stu-id="ebe35-120">nx_dhcpv6_server_interface_set *Set the interface index for Server DHCPv6 services*</span></span>
- <span data-ttu-id="ebe35-121">nx_dhcpv6_server_option_request_handler_set *Establecer el controlador de solicitudes de opción*</span><span class="sxs-lookup"><span data-stu-id="ebe35-121">nx_dhcpv6_server_option_request_handler_set *Set the option request handler*</span></span>

## <a name="nx_dhcpv6_create_dns_address"></a><span data-ttu-id="ebe35-122">nx_dhcpv6_create_dns_address</span><span class="sxs-lookup"><span data-stu-id="ebe35-122">nx_dhcpv6_create_dns_address</span></span>

### <a name="set-the-network-dns-server"></a><span data-ttu-id="ebe35-123">Establecimiento del servidor DNS de red</span><span class="sxs-lookup"><span data-stu-id="ebe35-123">Set the network DNS server</span></span>

<span data-ttu-id="ebe35-124">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-124">**Prototype**</span></span>

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

<span data-ttu-id="ebe35-125">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-125">**Description**</span></span>

<span data-ttu-id="ebe35-126">Este servicio carga el servidor DHCPv6 con la dirección del servidor DNS para la interfaz de red DHCPv6 del servidor.</span><span class="sxs-lookup"><span data-stu-id="ebe35-126">This service loads the DHCPv6 Server with the DNS server address for the Server DHCPv6 network interface.</span></span>

<span data-ttu-id="ebe35-127">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-127">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-128">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-128">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-129">**dns_ipv6_address**: puntero al servidor DNS</span><span class="sxs-lookup"><span data-stu-id="ebe35-129">**dns_ipv6_address** Pointer to the DNS server</span></span>

<span data-ttu-id="ebe35-130">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-130">**Return Values**</span></span>

- <span data-ttu-id="ebe35-131">**NX_SUCCESS** (0x00) Servidor DNS guardado en la instancia del servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-131">**NX_SUCCESS** (0x00) DNS Serversaved to DHCPv6 Server instance</span></span>
- <span data-ttu-id="ebe35-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Se proporciona una dirección no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="ebe35-133">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-133">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-134">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-134">**Allowed From**</span></span>

<span data-ttu-id="ebe35-135">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-135">Application Code</span></span>

<span data-ttu-id="ebe35-136">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-136">**Example**</span></span>

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a><span data-ttu-id="ebe35-137">nx_dhcpv6_create_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="ebe35-137">nx_dhcpv6_create_ip_address_range</span></span>

### <a name="create-the-server-ip-address-list"></a><span data-ttu-id="ebe35-138">Creación de la lista de direcciones IP del servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-138">Create the Server IP address list</span></span>

<span data-ttu-id="ebe35-139">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-139">**Prototype**</span></span>

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

<span data-ttu-id="ebe35-140">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-140">**Description**</span></span>

<span data-ttu-id="ebe35-141">Este servicio crea la lista de direcciones IP especificada por las direcciones de inicio y finalización del intervalo de direcciones asignables del servidor.</span><span class="sxs-lookup"><span data-stu-id="ebe35-141">This service creates the IP address list specified by the start and end addresses of the Server’s assignable address range.</span></span> <span data-ttu-id="ebe35-142">Las direcciones de inicio y finalización deben coincidir con el prefijo de dirección de la interfaz del servidor (debe estar en el mismo vínculo que la interfaz DHCPv6 del servidor).</span><span class="sxs-lookup"><span data-stu-id="ebe35-142">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 interface).</span></span> <span data-ttu-id="ebe35-143">Se devuelve el número de direcciones realmente agregadas.</span><span class="sxs-lookup"><span data-stu-id="ebe35-143">The number of addresses actually added is returned.</span></span>

<span data-ttu-id="ebe35-144">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-144">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-145">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-145">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-146">**start_ipv6_address**: inicio de las direcciones que se van a agregar</span><span class="sxs-lookup"><span data-stu-id="ebe35-146">**start_ipv6_address** Start of addresses to add</span></span>
- <span data-ttu-id="ebe35-147">**end_ipv6_address**: fin de las direcciones que se van a agregar</span><span class="sxs-lookup"><span data-stu-id="ebe35-147">**end_ipv6_address** End of addresses to add</span></span>
- <span data-ttu-id="ebe35-148">\***addresses_added**: salida de las direcciones agregadas</span><span class="sxs-lookup"><span data-stu-id="ebe35-148">\***addresses_added** Output of addresses added</span></span>

<span data-ttu-id="ebe35-149">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-149">**Return Values**</span></span>

- <span data-ttu-id="ebe35-150">**NX_SUCCESS** (0x00) Lista de direcciones IP creadas correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-150">**NX_SUCCESS** (0x00) IP address list successfully created</span></span>
- <span data-ttu-id="ebe35-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Se proporciona una dirección no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="ebe35-152">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-152">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-153">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-153">**Allowed From**</span></span>

<span data-ttu-id="ebe35-154">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-154">Application Code</span></span>

<span data-ttu-id="ebe35-155">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-155">**Example**</span></span>

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a><span data-ttu-id="ebe35-156">nx_dhcpv6_reserve_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="ebe35-156">nx_dhcpv6_reserve_ip_address_range</span></span>

### <a name="reserve-specified-range-of-ip-addresses"></a><span data-ttu-id="ebe35-157">Reservar el intervalo de direcciones IP especificado</span><span class="sxs-lookup"><span data-stu-id="ebe35-157">Reserve specified range of IP addresses</span></span>

<span data-ttu-id="ebe35-158">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-158">**Prototype**</span></span>

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

<span data-ttu-id="ebe35-159">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-159">**Description**</span></span>

<span data-ttu-id="ebe35-160">Este servicio reserva el intervalo de direcciones IP especificado por las direcciones de inicio y finalización.</span><span class="sxs-lookup"><span data-stu-id="ebe35-160">This service reserves the IP address range specified by the start and end addresses.</span></span> <span data-ttu-id="ebe35-161">Estas direcciones deben estar dentro del intervalo de direcciones IP del servidor creado previamente.</span><span class="sxs-lookup"><span data-stu-id="ebe35-161">These addresses must be within in the previously created server IP address range.</span></span> <span data-ttu-id="ebe35-162">Estas direcciones no se asignarán a ningún cliente por parte del servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-162">These addresses will not be assigned to any Clients by the DHCPv6 Server.</span></span> <span data-ttu-id="ebe35-163">Las direcciones de inicio y finalización deben coincidir con el prefijo de dirección de la interfaz del servidor (debe estar en el mismo vínculo que la interfaz de red DHCPv6 del servidor).</span><span class="sxs-lookup"><span data-stu-id="ebe35-163">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 network interface).</span></span> <span data-ttu-id="ebe35-164">Se devuelve el número de direcciones realmente reservadas.</span><span class="sxs-lookup"><span data-stu-id="ebe35-164">The number of addresses actually reserved is returned.</span></span>

<span data-ttu-id="ebe35-165">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-165">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-166">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-166">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-167">**start_ipv6_address**: inicio de las direcciones que se van a reservar</span><span class="sxs-lookup"><span data-stu-id="ebe35-167">**start_ipv6_address** Start of addresses to reserve</span></span>
- <span data-ttu-id="ebe35-168">**end_ipv6_address**: fin de las direcciones que se van a reservar</span><span class="sxs-lookup"><span data-stu-id="ebe35-168">**end_ipv6_address** End of addresses to reserve</span></span>
- <span data-ttu-id="ebe35-169">\***addresses_reserved** Número de direcciones reservadas</span><span class="sxs-lookup"><span data-stu-id="ebe35-169">\***addresses_reserved** Number of addresses reserved</span></span>

<span data-ttu-id="ebe35-170">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-170">**Return Values**</span></span>

- <span data-ttu-id="ebe35-171">**NX_SUCCESS** (0x00) Mensaje de LIBERACIÓN creado y procesado correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-171">**NX_SUCCESS** (0x00) RELEASE message successfully created and processed</span></span>
- <span data-ttu-id="ebe35-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Se proporciona una dirección no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="ebe35-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) No se encontró la dirección de inicio en la lista de direcciones del servidor.</span><span class="sxs-lookup"><span data-stu-id="ebe35-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Starting address not found in Server address list.</span></span>
- <span data-ttu-id="ebe35-174">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-174">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-175">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-175">**Allowed From**</span></span>

<span data-ttu-id="ebe35-176">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-176">Application Code</span></span>

<span data-ttu-id="ebe35-177">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-177">**Example**</span></span>

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a><span data-ttu-id="ebe35-178">nx_dhcpv6_server_create</span><span class="sxs-lookup"><span data-stu-id="ebe35-178">nx_dhcpv6_server_create</span></span>

### <a name="create-the-dhcpv6-server-instance"></a><span data-ttu-id="ebe35-179">Creación de la instancia del servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-179">Create the DHCPv6 Server instance</span></span> 

<span data-ttu-id="ebe35-180">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-180">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

<span data-ttu-id="ebe35-181">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-181">**Description**</span></span>

<span data-ttu-id="ebe35-182">Este servicio crea la tarea de servidor DHCPv6 con la entrada especificada.</span><span class="sxs-lookup"><span data-stu-id="ebe35-182">This service creates the DHCPv6 Server task with the specified input.</span></span> <span data-ttu-id="ebe35-183">Los controladores de devolución de llamada son entradas opcionales.</span><span class="sxs-lookup"><span data-stu-id="ebe35-183">The callback handlers are optional input.</span></span> <span data-ttu-id="ebe35-184">Se requieren la entrada del puntero de pila, de la instancia de IP y del grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="ebe35-184">The stack pointer, IP instance and packet pool input are required.</span></span> <span data-ttu-id="ebe35-185">La instancia de IP y el grupo de paquetes ya deben estar creados.</span><span class="sxs-lookup"><span data-stu-id="ebe35-185">The IP instance and packet pool must already be created.</span></span>

<span data-ttu-id="ebe35-186">Se recomienda que el usuario llame a nx_dhcpv6_server_option_request_handler_set para establecer el controlador de solicitudes de opción.</span><span class="sxs-lookup"><span data-stu-id="ebe35-186">User is encouraged to call nx_dhcpv6_server_option_request_handler_set to set the option request handler.</span></span>

<span data-ttu-id="ebe35-187">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-187">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-188">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-188">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-189">**ip_ptr**: puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="ebe35-189">**ip_ptr** Pointer to the IP instance</span></span>
- <span data-ttu-id="ebe35-190">**name_str**: puntero al nombre del servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-190">**name_str** Pointer to Server name</span></span>
- <span data-ttu-id="ebe35-191">**packet_pool_ptr**: puntero al grupo de paquetes del servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-191">**packet_pool_ptr** Pointer to Server packet pool</span></span>
- <span data-ttu-id="ebe35-192">**stack_ptr**: puntero a la memoria de pila del cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-192">**stack_ptr** Pointer to Server stack memory</span></span>
- <span data-ttu-id="ebe35-193">**stack_size**: tamaño de la memoria de pila del servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-193">**stack_size** Size of Server stack memory</span></span>
- <span data-ttu-id="ebe35-194">**dhcpv6_address_declined_handler**: puntero al controlador de mensajes de rechazo o liberación del cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-194">**dhcpv6_address_declined_handler** Pointer to Client Decline or Release message handler</span></span>
- <span data-ttu-id="ebe35-195">**dhcpv6_option_request_handler**: puntero al controlador de opción de solicitud de opciones</span><span class="sxs-lookup"><span data-stu-id="ebe35-195">**dhcpv6_option_request_handler** Pointer to options request option handler</span></span>

<span data-ttu-id="ebe35-196">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-196">**Return Values**</span></span>

- <span data-ttu-id="ebe35-197">**NX_SUCCESS** (0x00) Servidor reanudado correctamente.</span><span class="sxs-lookup"><span data-stu-id="ebe35-197">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="ebe35-198">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-198">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="ebe35-199">NX_DHCPV6_PARAM_ERROR Entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-199">NX_DHCPV6_PARAM_ERROR Invalid non pointer input</span></span>

<span data-ttu-id="ebe35-200">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-200">**Allowed From**</span></span>

<span data-ttu-id="ebe35-201">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-201">Application Code</span></span>

<span data-ttu-id="ebe35-202">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-202">**Example**</span></span>

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a><span data-ttu-id="ebe35-203">nx_dhcpv6_server_delete</span><span class="sxs-lookup"><span data-stu-id="ebe35-203">nx_dhcpv6_server_delete</span></span>

### <a name="delete-the-dhcpv6-server"></a><span data-ttu-id="ebe35-204">Eliminación del servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-204">Delete the DHCPv6 Server</span></span>

<span data-ttu-id="ebe35-205">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-205">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="ebe35-206">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-206">**Description**</span></span>

<span data-ttu-id="ebe35-207">Este servicio elimina la tarea del servidor DHCPv6 y cualquier solicitud que el servidor estaba procesando.</span><span class="sxs-lookup"><span data-stu-id="ebe35-207">This service deletes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="ebe35-208">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-208">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-209">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-209">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="ebe35-210">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-210">**Return Values**</span></span>

- <span data-ttu-id="ebe35-211">**NX_SUCCESS** (0x00) Servidor eliminado correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-211">**NX_SUCCESS** (0x00) Server successfully deleted</span></span>
- <span data-ttu-id="ebe35-212">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-212">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-213">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-213">**Allowed From**</span></span>

<span data-ttu-id="ebe35-214">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ebe35-214">Threads</span></span>

<span data-ttu-id="ebe35-215">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-215">**Example**</span></span>

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a><span data-ttu-id="ebe35-216">nx_dhcpv6_server_resume</span><span class="sxs-lookup"><span data-stu-id="ebe35-216">nx_dhcpv6_server_resume</span></span>

### <a name="resume-dhcpv6-server-task"></a><span data-ttu-id="ebe35-217">Reanudación de la tarea del servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-217">Resume DHCPv6 Server task</span></span> 

<span data-ttu-id="ebe35-218">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-218">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="ebe35-219">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-219">**Description**</span></span>

<span data-ttu-id="ebe35-220">Este servicio reanuda la tarea del servidor DHCPv6 y cualquier solicitud que el servidor estaba procesando.</span><span class="sxs-lookup"><span data-stu-id="ebe35-220">This service resumes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="ebe35-221">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-221">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-222">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-222">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="ebe35-223">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-223">**Return Values**</span></span>

- <span data-ttu-id="ebe35-224">**NX_SUCCESS** (0x00) Servidor reanudado correctamente.</span><span class="sxs-lookup"><span data-stu-id="ebe35-224">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="ebe35-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) El servidor de ya se está ejecutando</span><span class="sxs-lookup"><span data-stu-id="ebe35-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="ebe35-226">**status** (variable) Estado de error de ThreadX y NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ebe35-226">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="ebe35-227">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-227">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-228">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-228">**Allowed From**</span></span>

<span data-ttu-id="ebe35-229">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ebe35-229">Threads</span></span>

<span data-ttu-id="ebe35-230">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-230">**Example**</span></span>

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a><span data-ttu-id="ebe35-231">nx_dhcpv6_server_suspend</span><span class="sxs-lookup"><span data-stu-id="ebe35-231">nx_dhcpv6_server_suspend</span></span>

### <a name="suspend-dhcpv6-server-task"></a><span data-ttu-id="ebe35-232">Suspensión de la tarea del servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-232">Suspend DHCPv6 Server task</span></span> 

<span data-ttu-id="ebe35-233">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-233">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="ebe35-234">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-234">**Description**</span></span>

<span data-ttu-id="ebe35-235">Este servicio suspende la tarea del servidor DHCPv6 y cualquier solicitud que el servidor estaba procesando.</span><span class="sxs-lookup"><span data-stu-id="ebe35-235">This service suspends the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="ebe35-236">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-236">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-237">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-237">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="ebe35-238">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-238">**Return Values**</span></span>

- <span data-ttu-id="ebe35-239">**NX_SUCCESS** (0x00) Servidor reanudado correctamente.</span><span class="sxs-lookup"><span data-stu-id="ebe35-239">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="ebe35-240">**NX_DHCPV6_NOT_STARTED** (0xE92) El servidor no se ha iniciado</span><span class="sxs-lookup"><span data-stu-id="ebe35-240">**NX_DHCPV6_NOT_STARTED** (0xE92) Server is not started</span></span> 
- <span data-ttu-id="ebe35-241">**Status** (variable) Estado de error de ThreadX y NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ebe35-241">**Status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="ebe35-242">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-242">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-243">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-243">**Allowed From**</span></span>

<span data-ttu-id="ebe35-244">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ebe35-244">Threads</span></span>

<span data-ttu-id="ebe35-245">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-245">**Example**</span></span>

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a><span data-ttu-id="ebe35-246">nx_dhcpv6_server_start</span><span class="sxs-lookup"><span data-stu-id="ebe35-246">nx_dhcpv6_server_start</span></span>

### <a name="start-the-dhcpv6-server-task"></a><span data-ttu-id="ebe35-247">Inicio de la tarea del servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-247">Start the DHCPv6 Server task</span></span> 

<span data-ttu-id="ebe35-248">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-248">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="ebe35-249">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-249">**Description**</span></span>

<span data-ttu-id="ebe35-250">Este servicio inicia la tarea del servidor DHCPv6 y prepara al servidor para procesar las solicitudes de la aplicación para recibir mensajes del cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-250">This service starts the DHCPv6 Server task and readies the Server to process application requests for receiving DHCPv6 Client messages.</span></span> <span data-ttu-id="ebe35-251">Comprueba que la instancia de servidor tiene suficiente información (DUID de servidor), crea y enlaza el socket UDP para enviar y recibir mensajes DHCPv6 y activa temporizadores para realizar un seguimiento del tiempo de sesión y de la expiración de la concesión de IP.</span><span class="sxs-lookup"><span data-stu-id="ebe35-251">It verifies the Server instance has sufficient information (Server DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages, and activates timers for keeping track of session time and IP lease expiration.</span></span>

>[!NOTE] 
> <span data-ttu-id="ebe35-252">Antes de que el servidor DHCPv6 pueda ejecutarse, la aplicación host es responsable de crear el intervalo de direcciones IP desde el que el servidor puede asignar direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="ebe35-252">Before the DHCPv6 Server can run, the host application is responsible for creating the IP address range from which the Server can assign IP addresses.</span></span> <span data-ttu-id="ebe35-253">También es responsable de establecer el DUID del servidor y la interfaz DHCPv6 (consulte *nx_dhcpv6_server_duid_set* y *nx_dhcpv6_server_interface_set*, respectivamente).</span><span class="sxs-lookup"><span data-stu-id="ebe35-253">It is also responsible for setting the Server DUID and DHCPv6 interface (see *nx_dhcpv6_server_duid_set* and *nx_dhcpv6_server_interface_set* respectively.</span></span>

<span data-ttu-id="ebe35-254">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-254">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-255">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-255">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="ebe35-256">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-256">**Return Values**</span></span>

- <span data-ttu-id="ebe35-257">**NX_SUCCESS** (0x00) Servidor iniciado correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-257">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="ebe35-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) El servidor de ya se está ejecutando</span><span class="sxs-lookup"><span data-stu-id="ebe35-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="ebe35-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) El servidor de no tiene direcciones asignables para conceder</span><span class="sxs-lookup"><span data-stu-id="ebe35-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Server has no assignable addresses to lease</span></span>
- <span data-ttu-id="ebe35-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Índice de direcciones global sin establecer</span><span class="sxs-lookup"><span data-stu-id="ebe35-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Global address index not set</span></span>
- <span data-ttu-id="ebe35-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) No se creó ningún DUID de servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) No Server DUID created</span></span> 
- <span data-ttu-id="ebe35-262">**status** (variable) Estado de error de ThreadX y NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ebe35-262">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="ebe35-263">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-263">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-264">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-264">**Allowed From**</span></span>

<span data-ttu-id="ebe35-265">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ebe35-265">Threads</span></span>

<span data-ttu-id="ebe35-266">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-266">**Example**</span></span>

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a><span data-ttu-id="ebe35-267">nx_dhcpv6_retrieve_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="ebe35-267">nx_dhcpv6_retrieve_ip_address_lease</span></span>

### <a name="get-an-ip-address-lease-from-the-server-table"></a><span data-ttu-id="ebe35-268">Obtención de una concesión de dirección IP de la tabla de servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-268">Get an IP address lease from the Server table</span></span>

<span data-ttu-id="ebe35-269">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-269">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

<span data-ttu-id="ebe35-270">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-270">**Description**</span></span>

<span data-ttu-id="ebe35-271">Este servicio recupera un registro de concesión de direcciones IP de la tabla de servidor en la ubicación de índice de tabla especificada.</span><span class="sxs-lookup"><span data-stu-id="ebe35-271">This service retrieves an IP address lease record from the Server table at the specified table index location.</span></span> <span data-ttu-id="ebe35-272">Esto se puede hacer antes o después de recuperar los datos de registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="ebe35-272">This can be done before or after retrieving Client record data.</span></span>

<span data-ttu-id="ebe35-273">La capacidad de almacenar y recuperar datos entre el servidor DHCPv6 y la memoria no volátil es un requisito del protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-273">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="ebe35-274">No importa en qué orden se guardan los datos de concesión de IP y los datos de registro del cliente en la memoria no volátil.</span><span class="sxs-lookup"><span data-stu-id="ebe35-274">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="ebe35-275">No se recomienda copiar datos a las tablas de servidores o desde estas sin detener o suspender primero el servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-275">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="ebe35-276">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-276">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-277">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-277">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-278">**table_index**: índice de tabla en el que almacenar la concesión</span><span class="sxs-lookup"><span data-stu-id="ebe35-278">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="ebe35-279">**lease_IP_address**: puntero a la dirección IP concedida al cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-279">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="ebe35-280">**T1**: tiempo de renovación solicitado por el cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-280">**T1** Client requested renew time</span></span>
- <span data-ttu-id="ebe35-281">**T2**: tiempo de reenlace solicitado por el cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-281">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="ebe35-282">**valid_lifetime**: la concesión del cliente queda en desuso</span><span class="sxs-lookup"><span data-stu-id="ebe35-282">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="ebe35-283">**preferred_lifetime**: la concesión del cliente deja de ser válida</span><span class="sxs-lookup"><span data-stu-id="ebe35-283">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="ebe35-284">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-284">**Return Values**</span></span>

- <span data-ttu-id="ebe35-285">**NX_SUCCESS** (0x00) Servidor iniciado correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-285">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="ebe35-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) Entrada de datos de concesión de IP no válida</span><span class="sxs-lookup"><span data-stu-id="ebe35-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="ebe35-287">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-287">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-288">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-288">**Allowed From**</span></span>

<span data-ttu-id="ebe35-289">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-289">Application code</span></span>

<span data-ttu-id="ebe35-290">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-290">**Example**</span></span>

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a><span data-ttu-id="ebe35-291">nx_dhcpv6_add_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="ebe35-291">nx_dhcpv6_add_ip_address_lease</span></span>

### <a name="add-an-ip-address-lease-to-the-server-table"></a><span data-ttu-id="ebe35-292">Incorporación de una concesión de dirección IP de la tabla de servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-292">Add an IP address lease to the Server table</span></span>

<span data-ttu-id="ebe35-293">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-293">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

<span data-ttu-id="ebe35-294">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-294">**Description**</span></span>

<span data-ttu-id="ebe35-295">Este servicio carga los datos de concesión de IP de una sesión de servidor DHCPv6 anterior desde memoria no volátil a la tabla de concesión del servidor.</span><span class="sxs-lookup"><span data-stu-id="ebe35-295">This service loads IP lease data from a previous DHCPv6 Server session from non volatile memory to the Server lease table.</span></span> <span data-ttu-id="ebe35-296">Esto no es necesario si el servidor se ejecuta por primera vez y no tiene datos de concesión anteriores.</span><span class="sxs-lookup"><span data-stu-id="ebe35-296">This is not necessary if the Server is running for the first time and has no previous lease data.</span></span> <span data-ttu-id="ebe35-297">Si este es el caso, la aplicación host debe crear un intervalo de direcciones IP para asignar direcciones IP mediante el servicio *nx_dhcpv6_create_ip_address_range*.</span><span class="sxs-lookup"><span data-stu-id="ebe35-297">If this is the case the host application must create an IP address range for assigning IP addresses, using the *nx_dhcpv6_create_ip_address_range* service.</span></span> <span data-ttu-id="ebe35-298">Los datos son suficientes para reconstruir un registro de concesiones DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-298">The data is sufficient to reconstruct a DHCPv6 lease record.</span></span> <span data-ttu-id="ebe35-299">No es necesario especificar el índice de tabla.</span><span class="sxs-lookup"><span data-stu-id="ebe35-299">The table index need not be specified.</span></span> <span data-ttu-id="ebe35-300">Si se establece en 0xFFFFFFFF (infinito), el servidor DHCPv6 encontrará la siguiente ranura disponible en la que copiar los datos.</span><span class="sxs-lookup"><span data-stu-id="ebe35-300">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will find the next available slot to copy the data to.</span></span>

>[!NOTE] 
> <span data-ttu-id="ebe35-301">La carga de los datos de concesión de IP debe realizarse antes de cargar los registros de cliente; ambas acciones DEBEN realizarse antes de volver a iniciar el servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-301">Uploading IP lease data MUST be done before uploading Client records; both MUST be done before (re)starting the DHCPv6 Server.</span></span>

<span data-ttu-id="ebe35-302">La capacidad de almacenar y recuperar datos entre el servidor DHCPv6 y la memoria no volátil es un requisito del protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-302">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="ebe35-303">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-303">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-304">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-304">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-305">**table_index**: índice de tabla en el que almacenar la concesión</span><span class="sxs-lookup"><span data-stu-id="ebe35-305">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="ebe35-306">**lease_IP_address**: puntero a la dirección IP concedida al cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-306">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="ebe35-307">**T1**: tiempo de renovación solicitado por el cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-307">**T1** Client requested renew time</span></span>
- <span data-ttu-id="ebe35-308">**T2**: tiempo de reenlace solicitado por el cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-308">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="ebe35-309">**valid_lifetime**: la concesión del cliente queda en desuso</span><span class="sxs-lookup"><span data-stu-id="ebe35-309">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="ebe35-310">**preferred_lifetime**: la concesión del cliente deja de ser válida</span><span class="sxs-lookup"><span data-stu-id="ebe35-310">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="ebe35-311">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-311">**Return Values**</span></span>

- <span data-ttu-id="ebe35-312">**NX_SUCCESS** (0x00) Servidor iniciado correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-312">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="ebe35-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) No hay espacio para más datos de concesión\*\*</span><span class="sxs-lookup"><span data-stu-id="ebe35-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) No room for more lease data\*\*</span></span>
- <span data-ttu-id="ebe35-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Los datos de concesión de no parecen estar en el vínculo con la interfaz DHCPv6 del servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Lease data does not appear to be on link with Server DHCPv6 interface</span></span>
- <span data-ttu-id="ebe35-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) Entrada de datos de concesión de IP no válida</span><span class="sxs-lookup"><span data-stu-id="ebe35-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="ebe35-316">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-316">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-317">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-317">**Allowed From**</span></span>

<span data-ttu-id="ebe35-318">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-318">Application code</span></span>

<span data-ttu-id="ebe35-319">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-319">**Example**</span></span>

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a><span data-ttu-id="ebe35-320">nx_dhcpv6_add_client_record</span><span class="sxs-lookup"><span data-stu-id="ebe35-320">nx_dhcpv6_add_client_record</span></span>

### <a name="add-a-client-record-to-the-server-table"></a><span data-ttu-id="ebe35-321">Incorporación de un registro de cliente a la tabla de servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-321">Add a Client record to the Server table</span></span>

<span data-ttu-id="ebe35-322">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-322">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

<span data-ttu-id="ebe35-323">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-323">**Description**</span></span>

<span data-ttu-id="ebe35-324">Este servicio copia los datos de cliente desde la memoria no volátil a la tabla de servidor de un registro a la vez.</span><span class="sxs-lookup"><span data-stu-id="ebe35-324">This service copies Client data from non volatile memory to the Server table one record at a time.</span></span> <span data-ttu-id="ebe35-325">Esto solo es necesario si el servidor se está reiniciando y tiene datos de cliente de una sesión anterior para restaurar desde la memoria.</span><span class="sxs-lookup"><span data-stu-id="ebe35-325">This is only necessary if the Server is being rebooted and has Client data from a previous session to restore from memory.</span></span> <span data-ttu-id="ebe35-326">Si un servidor no tiene datos anteriores, el servidor DHCPv6 inicializará la tabla de cliente para poder agregar registros de cliente.</span><span class="sxs-lookup"><span data-stu-id="ebe35-326">If a Server has no previous data, the DHCPv6 Server will initialize the Client table to be able for adding Client records.</span></span>

<span data-ttu-id="ebe35-327">No es necesario especificar el índice de la tabla.</span><span class="sxs-lookup"><span data-stu-id="ebe35-327">It is not necessary to specify the table index.</span></span> <span data-ttu-id="ebe35-328">Si se establece en 0xFFFFFFFF (infinito), el servidor DHCPv6 buscará la siguiente ranura disponible.</span><span class="sxs-lookup"><span data-stu-id="ebe35-328">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will locate the next available slot.</span></span> <span data-ttu-id="ebe35-329">El servidor DHCPv6 puede reconstruir un registro de cliente a partir de estos datos.</span><span class="sxs-lookup"><span data-stu-id="ebe35-329">The DHCPv6 Server can reconstruct a Client record from this data.</span></span>

>[!NOTE] 
> <span data-ttu-id="ebe35-330">La aplicación host DEBE cargar los datos de concesión de IP ANTES de los datos de registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="ebe35-330">The host application MUST upload the IP lease data BEFORE the Client record data.</span></span> <span data-ttu-id="ebe35-331">Esto es para que, internamente, el servidor DHCPv6 pueda vincular las tablas de modo que cada registro de cliente se una con su correspondiente registro de concesión de IP en sus tablas correspondientes.</span><span class="sxs-lookup"><span data-stu-id="ebe35-331">This is so that internally the DHCPv6 Server can cross link the tables so that each Client record is joined with its corresponding IP lease record in their respective tables.</span></span> <span data-ttu-id="ebe35-332">Consulte *nx_dhcpv6_add_ip_address_lease* para obtener más información sobre cómo cargar los datos de concesión de IP desde la memoria.</span><span class="sxs-lookup"><span data-stu-id="ebe35-332">See *nx_dhcpv6_add_ip_address_lease* for details on uploading IP lease data from memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="ebe35-333">En función del tipo de DUID, no se deben proporcionar todos los datos.</span><span class="sxs-lookup"><span data-stu-id="ebe35-333">Depending on DUID type, not all data must be supplied.</span></span> <span data-ttu-id="ebe35-334">Por ejemplo, si un cliente tiene un tipo de DUID asignado por el proveedor, puede enviar cero para los parámetros del nivel de vínculo de DUID (dirección MAC, tipo de hardware, hora de DUID).</span><span class="sxs-lookup"><span data-stu-id="ebe35-334">For example if a Client has a vendor assigned DUID type, it can send in zero for DUID Link Layer parameters (MAC address, hardware type, DUID time).</span></span>

<span data-ttu-id="ebe35-335">La capacidad de almacenar y recuperar datos entre el servidor DHCPv6 y la memoria no volátil es un requisito del protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-335">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="ebe35-336">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-336">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-337">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-337">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="ebe35-338">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-338">**Return Values**</span></span>

- <span data-ttu-id="ebe35-339">**NX_SUCCESS** (0x00) Servidor iniciado correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-339">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="ebe35-340">**NX_INVALID_PARAMETERS** (0x4D) Entrada que no es de puntero no válida.\*\*</span><span class="sxs-lookup"><span data-stu-id="ebe35-340">**NX_ INVALID_PARAMETERS** (0x4D) Invalid non pointer input\*\*</span></span>
- <span data-ttu-id="ebe35-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) No quedan ranuras vacías para agregar otro registro de cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) No empty slots left for adding another Client record</span></span>
- <span data-ttu-id="ebe35-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) No se encontró la dirección asignada del cliente en la tabla de concesión del servidor.</span><span class="sxs-lookup"><span data-stu-id="ebe35-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Client assigned address not found in Server lease table.</span></span>
- <span data-ttu-id="ebe35-343">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-343">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-344">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-344">**Allowed From**</span></span>

<span data-ttu-id="ebe35-345">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-345">Application code</span></span>

<span data-ttu-id="ebe35-346">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-346">**Example**</span></span>

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a><span data-ttu-id="ebe35-347">nx_dhcpv6_retrieve_client_record</span><span class="sxs-lookup"><span data-stu-id="ebe35-347">nx_dhcpv6_retrieve_client_record</span></span>

### <a name="retrieve-a-client-record-from-the-server-table"></a><span data-ttu-id="ebe35-348">Recuperación de un registro de cliente de la tabla de servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-348">Retrieve a Client record from the Server table</span></span>

<span data-ttu-id="ebe35-349">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-349">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

<span data-ttu-id="ebe35-350">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-350">**Description**</span></span>

<span data-ttu-id="ebe35-351">Este servicio copia los datos esenciales de la tabla de registros de cliente del servidor para el almacenamiento en memoria no volátil.</span><span class="sxs-lookup"><span data-stu-id="ebe35-351">This service copies the essential data from the Server’s Client record table for storage to non-volatile memory.</span></span> <span data-ttu-id="ebe35-352">El servidor puede reconstruir un registro de cliente adecuado a partir de estos datos en el proceso inverso (carga de datos en la tabla de servidor).</span><span class="sxs-lookup"><span data-stu-id="ebe35-352">The Server can reconstruct an adequate Client record from such data in the reverse process (uploading data to the Server table).</span></span> <span data-ttu-id="ebe35-353">Independientemente del tipo de DUID, ninguno de los punteros puede ser NULL; los datos se inicializan en cero para todos los parámetros.</span><span class="sxs-lookup"><span data-stu-id="ebe35-353">Regardless of the DUID type, none of the pointers can be NULL pointers; data is initialized to zero for all parameters.</span></span> <span data-ttu-id="ebe35-354">Por ejemplo, si el tipo de DUID de cliente es el nivel de vínculo más el tiempo, el número de proveedor se devuelve como cero y el identificador privado es una cadena vacía.</span><span class="sxs-lookup"><span data-stu-id="ebe35-354">For example, if the Client DUID type is Link Layer Plus Time, the vendor number is returned as zero and the private ID is an empty string.</span></span>

<span data-ttu-id="ebe35-355">La capacidad de almacenar y recuperar datos entre el servidor DHCPv6 y la memoria no volátil es un requisito del protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-355">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="ebe35-356">No importa en qué orden se guardan los datos de concesión de IP y los datos de registro del cliente en la memoria no volátil.</span><span class="sxs-lookup"><span data-stu-id="ebe35-356">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="ebe35-357">No se recomienda copiar datos a las tablas de servidores o desde estas sin detener o suspender primero el servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-357">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="ebe35-358">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-358">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-359">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-359">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-360">**table_index**: índice en la tabla de cliente del servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-360">**table_index** Index into Server’s client table</span></span>
- <span data-ttu-id="ebe35-361">**message_xid**: identificador de la transacción cliente/servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-361">**message_xid** Client Server Transaction ID</span></span>
- <span data-ttu-id="ebe35-362">**client_address**: dirección IPv6 concedida al cliente</span><span class="sxs-lookup"><span data-stu-id="ebe35-362">**client_address** IPv6 address leased to Client</span></span>
- <span data-ttu-id="ebe35-363">**client_state**: estado de DHCPv6 del cliente (por ejemplo, enlazado)</span><span class="sxs-lookup"><span data-stu-id="ebe35-363">**client_state** Client DHCPv6 state (e.g. bound)</span></span>
- <span data-ttu-id="ebe35-364">**IP_lease_time_accrued**: el tiempo expiró en el puntero **dhcpv6_server_ptr** al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-364">**IP_lease_time_accrued** Time expired on lease already **dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-365">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-365">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="ebe35-366">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-366">**Return Values**</span></span>

- <span data-ttu-id="ebe35-367">**NX_SUCCESS** (0x00) Servidor iniciado correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-367">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="ebe35-368">**NX_DHCPV6_INVALID_DUID** (0xECC) Datos de DUID no válidos o incoherentes</span><span class="sxs-lookup"><span data-stu-id="ebe35-368">**NX_DHCPV6_INVALID_DUID** (0xECC) Invalid or inconsistent DUID data</span></span>
- <span data-ttu-id="ebe35-369">**NX_PTR_ERROR**(0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-369">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="ebe35-370">NX_INVALID_PARAMETERS (0x4D) Entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-370">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

<span data-ttu-id="ebe35-371">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-371">**Allowed From**</span></span>

<span data-ttu-id="ebe35-372">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-372">Application code</span></span>

<span data-ttu-id="ebe35-373">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-373">**Example**</span></span>

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a><span data-ttu-id="ebe35-374">nx_dhcpv6_server_interface_set</span><span class="sxs-lookup"><span data-stu-id="ebe35-374">nx_dhcpv6_server_interface_set</span></span>

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a><span data-ttu-id="ebe35-375">Establecimiento del índice de interfaz para la interfaz DHCPv6 del servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-375">Setthe interface index for Server DHCPv6 interface</span></span>

<span data-ttu-id="ebe35-376">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-376">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

<span data-ttu-id="ebe35-377">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-377">**Description**</span></span>

<span data-ttu-id="ebe35-378">Este servicio establece la interfaz de red en la que el servidor DHCPv6 controla las solicitudes del cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-378">This service sets the network interface on which the DHCPv6 Server handles DHCPv6 Client requests.</span></span> <span data-ttu-id="ebe35-379">No en el caso de las versiones de NetX Duo que no admiten varios host, el valor predeterminado de la interfaz es cero.</span><span class="sxs-lookup"><span data-stu-id="ebe35-379">Not that for versions of NetX Duo that do not support multihome, the interface value is defaulted to zero.</span></span> <span data-ttu-id="ebe35-380">El índice de direcciones globales es necesario para obtener la dirección global del servidor en su interfaz DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-380">The global address index is necessary to obtain the Server global address on its DHCPv6 interface.</span></span> <span data-ttu-id="ebe35-381">La lógica DHCPv6 usa esto para asegurarse de que las direcciones de concesión y otros datos de DHCPv6 están vinculados al servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-381">This is used by the DHCPv6 logic to ensure that lease addresses and other DHCPv6 data is on link with the DHCPv6 Server.</span></span>

<span data-ttu-id="ebe35-382">Se debe llamar antes de que se inicie el servidor DHCPv6, incluso en el caso de las aplicaciones en dispositivos de host único o no compatibles con varios host.</span><span class="sxs-lookup"><span data-stu-id="ebe35-382">This must be called before the DHCPv6 server is started, even for applications on single homed devices or without multihome support.</span></span>

<span data-ttu-id="ebe35-383">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-383">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-384">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-384">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-385">**iface_index**: interfaz de servidor del servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-385">**iface_index** Server DHCPv6 Server interface</span></span>
- <span data-ttu-id="ebe35-386">**ga_address_index**: índice de la dirección global del servidor en la tabla de direcciones de la instancia de IP del servidor</span><span class="sxs-lookup"><span data-stu-id="ebe35-386">**ga_address_index** Index of Server global address in the Server IP instance address table</span></span>

<span data-ttu-id="ebe35-387">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-387">**Return Values**</span></span>

- <span data-ttu-id="ebe35-388">**NX_SUCCESS** (0x00) Servidor iniciado correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-388">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="ebe35-389">**NX_INVALID_INTERFACE** (0x4C) La interfaz no existe</span><span class="sxs-lookup"><span data-stu-id="ebe35-389">**NX_INVALID_INTERFACE** (0x4C) Interface does not exist</span></span>
- <span data-ttu-id="ebe35-390">NX_NO_INTERFACE_ADDRESS (0x50) El índice global supera el número máximo de direcciones IPv6 de la instancia IP (NX_MAX_IPV6_ADDRESSES)</span><span class="sxs-lookup"><span data-stu-id="ebe35-390">NX_NO_INTERFACE_ADDRESS (0x50) Global index exceeds the IP instance maximum IPv6 addresses (NX_MAX_IPV6_ADDRESSES)</span></span>
- <span data-ttu-id="ebe35-391">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-391">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-392">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-392">**Allowed From**</span></span>

<span data-ttu-id="ebe35-393">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-393">Application code</span></span>

<span data-ttu-id="ebe35-394">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-394">**Example**</span></span>

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a><span data-ttu-id="ebe35-395">nx_dhcpv6_set_server_duid</span><span class="sxs-lookup"><span data-stu-id="ebe35-395">nx_dhcpv6_set_server_duid</span></span>

### <a name="set-the-server-duid-for-dhcpv6-packets"></a><span data-ttu-id="ebe35-396">Establecimiento del DUID de servidor para paquetes DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-396">Set the Server DUID for DHCPv6 packets</span></span>

<span data-ttu-id="ebe35-397">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-397">**Prototype**</span></span>

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

<span data-ttu-id="ebe35-398">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-398">**Description**</span></span>

<span data-ttu-id="ebe35-399">Este servicio establece el DUID del servidor y se debe llamar antes de que la aplicación host inicie el servidor.</span><span class="sxs-lookup"><span data-stu-id="ebe35-399">This service sets the Server DUID and must be called before the host application starts the Server.</span></span> <span data-ttu-id="ebe35-400">En cuanto a la capa de vínculo y los tipos de DUID de tiempo de capa de vínculo, la aplicación host debe proporcionar el tipo de hardware y los datos de dirección MAC.</span><span class="sxs-lookup"><span data-stu-id="ebe35-400">For link layer and link layer time DUID types, the host application must supply the hardware type and MAC address data.</span></span> <span data-ttu-id="ebe35-401">Para DUID de tiempo de nivel de vínculo, el puntero de tiempo debe apuntar a una hora válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-401">For link layer time DUIDs, the time pointer must point to a valid time.</span></span> <span data-ttu-id="ebe35-402">El número de segundos transcurridos desde el 1 de enero de 2000 es un valor de inicialización típico.</span><span class="sxs-lookup"><span data-stu-id="ebe35-402">The number of seconds since Jan 1, 2000 is a typical seed value.</span></span> <span data-ttu-id="ebe35-403">Si el tipo de DUID del servidor es empresarial, tipo asignado por el proveedor, el DUID se creará a partir de las opciones configurables por el usuario NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID y NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, y los valores de la tiempo y dirección MAC pueden establecerse en NULL.</span><span class="sxs-lookup"><span data-stu-id="ebe35-403">If the Server DUID type is the enterprise, vendor assigned type, the DUID will be created from the user configurable options NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID and NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, and the time and MAC address values can be set to NULL.</span></span>

>[!NOTE] 
> <span data-ttu-id="ebe35-404">Es responsabilidad de la aplicación host guardar los parámetros de DUID del servidor en memoria no volátil, de modo que use el mismo DUID en los mensajes para los clientes entre reinicios.</span><span class="sxs-lookup"><span data-stu-id="ebe35-404">It is the host application’s responsibility to save the Server DUID parameters to nonvolatile memory such that it uses the same DUID in messages to Clients between reboots.</span></span> <span data-ttu-id="ebe35-405">Se trata de un requisito del protocolo DHCPv6 (RFC 3315).</span><span class="sxs-lookup"><span data-stu-id="ebe35-405">This is a requirement of the DHCPv6 protocol (RFC 3315).</span></span>

<span data-ttu-id="ebe35-406">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-406">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-407">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-407">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-408">**duid_type**: tipo de DUID de servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-408">**duid_type** DHCPv6 Server DUID type</span></span>
- <span data-ttu-id="ebe35-409">**hardware_type**: tipo de hardware (por ejemplo, Ethernet)</span><span class="sxs-lookup"><span data-stu-id="ebe35-409">**hardware_type** Hardware type (e.g. Ethernet)</span></span>
- <span data-ttu-id="ebe35-410">**mac_address_msw**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-410">**mac_address_msw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-411">**mac_address_lsw**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-411">**mac_address_lsw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-412">**time**: valor de tiempo para DUID</span><span class="sxs-lookup"><span data-stu-id="ebe35-412">**time** Time value for DUID</span></span>

<span data-ttu-id="ebe35-413">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-413">**Return Values**</span></span>

- <span data-ttu-id="ebe35-414">**NX_SUCCESS** (0x00) Servidor suspendido correctamente</span><span class="sxs-lookup"><span data-stu-id="ebe35-414">**NX_SUCCESS** (0x00) Server successfully suspended</span></span>
- <span data-ttu-id="ebe35-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0xE98) Tipo de DUID desconocido o no admitido</span><span class="sxs-lookup"><span data-stu-id="ebe35-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Unknown or unsupported DUID type</span></span>
- <span data-ttu-id="ebe35-416">**NX_INVALID_PARAMETERS** (0x4D) Entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-416">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>
- <span data-ttu-id="ebe35-417">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-417">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-418">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-418">**Allowed From**</span></span>

<span data-ttu-id="ebe35-419">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-419">Application code</span></span>

<span data-ttu-id="ebe35-420">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-420">**Example**</span></span>

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a><span data-ttu-id="ebe35-421">nx_dhcpv6_server_option_request_handler_set</span><span class="sxs-lookup"><span data-stu-id="ebe35-421">nx_dhcpv6_server_option_request_handler_set</span></span>

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a><span data-ttu-id="ebe35-422">Establecimiento del controlador de solicitud de opción para la instancia del servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-422">Set the option request handler for DHCPv6 Server instance</span></span> 

<span data-ttu-id="ebe35-423">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-423">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

<span data-ttu-id="ebe35-424">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="ebe35-424">**Description**</span></span>

<span data-ttu-id="ebe35-425">Este servicio establece el controlador de solicitud de opciones extendidas del servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ebe35-425">This service sets the DHCPv6 Server extended option request handler.</span></span>

<span data-ttu-id="ebe35-426">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="ebe35-426">**Input Parameters**</span></span>

- <span data-ttu-id="ebe35-427">**dhcpv6_server_ptr**: puntero al servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ebe35-427">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="ebe35-428">**dhcpv6_option_request_handler_extended**: puntero al controlador de solicitud de opciones extendidas</span><span class="sxs-lookup"><span data-stu-id="ebe35-428">**dhcpv6_option_request_handler_extended** Pointer to extended options request handler</span></span>

<span data-ttu-id="ebe35-429">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="ebe35-429">**Return Values**</span></span>

- <span data-ttu-id="ebe35-430">**NX_SUCCESS** (0x00) Servidor reanudado correctamente.</span><span class="sxs-lookup"><span data-stu-id="ebe35-430">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="ebe35-431">NX_PTR_ERROR (0x16) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="ebe35-431">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="ebe35-432">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="ebe35-432">**Allowed From**</span></span>

<span data-ttu-id="ebe35-433">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="ebe35-433">Application Code</span></span>

<span data-ttu-id="ebe35-434">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="ebe35-434">**Example**</span></span>

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```