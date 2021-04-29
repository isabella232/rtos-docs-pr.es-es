---
title: 'Capítulo 3: Descripción de los servicios del servidor DHCP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del servidor DHCP de NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 33eb0b4bd98f808124b9a6a1f01950639243d612
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814790"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a><span data-ttu-id="0cd0c-103">Capítulo 3: Descripción de los servicios del servidor DHCP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Server Services</span></span>

<span data-ttu-id="0cd0c-104">Este capítulo contiene una descripción de todos los servicios del servidor DHCP de NetX Duo (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-104">This chapter contains a description of all NetX Duo DHCP Server services (listed below) in alphabetic order.</span></span>

> [!NOTE]
> <span data-ttu-id="0cd0c-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_dhcp_server-create"></a><span data-ttu-id="0cd0c-106">nx_dhcp_server create</span><span class="sxs-lookup"><span data-stu-id="0cd0c-106">nx_dhcp_server create</span></span>

<span data-ttu-id="0cd0c-107">Crea una instancia de servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="0cd0c-107">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0cd0c-108">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-108">Prototype</span></span>

```C
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
    VOID *stack_ptr, ULONG stack_size,
    CHAR *input_address_list, CHAR *name_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0cd0c-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="0cd0c-109">Description</span></span>

<span data-ttu-id="0cd0c-110">Este servicio crea una instancia de servidor DHCP con una instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-110">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0cd0c-111">La aplicación debe asegurarse de que el grupo de paquetes creado para el servicio de creación de IP tiene como mínimo una carga de 548 bytes, sin incluir los encabezados UDP, IP y Ethernet.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-111">The application must make sure the packet pool created for the IP create service has a minimum 548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0cd0c-112">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0cd0c-112">Input Parameters</span></span>

- <span data-ttu-id="0cd0c-113">**dhcp_ptr**: puntero al bloque de control del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-113">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="0cd0c-114">**ip_ptr**: puntero a la instancia de IP del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-114">**ip_ptr** Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="0cd0c-115">**stack_ptr**: puntero a la ubicación de la pila del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-115">**stack_ptr** Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="0cd0c-116">**stack_size: tamaño de la pila del servidor DHCP.** input_address_list: puntero a la lista de direcciones IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-116">**stack_size Size of DHCP Server stack** input_address_list Pointer to Server’s list of IP addresses</span></span>
- <span data-ttu-id="0cd0c-117">**name_ptr: puntero al nombre del servidor DHCP.** packet_pool_ptr: puntero al grupo de paquetes del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-117">**name_ptr Pointer to DHCP Server name** packet_pool_ptr Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="0cd0c-118">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-118">Return Values</span></span>

- <span data-ttu-id="0cd0c-119">**NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-119">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="0cd0c-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) error de carga de paquete demasiado pequeña.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="0cd0c-121">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) lista de opciones vacía.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) Server option list is empty</span></span>
- <span data-ttu-id="0cd0c-122">NX_DHCP_PARAMETER_ERROR: (0x92) entrada no válida que no es puntero.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-122">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="0cd0c-123">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-123">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0cd0c-124">NX_PTR_ERROR: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-124">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0cd0c-125">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0cd0c-125">Allowed From</span></span>

<span data-ttu-id="0cd0c-126">Application</span><span class="sxs-lookup"><span data-stu-id="0cd0c-126">Application</span></span>

### <a name="example"></a><span data-ttu-id="0cd0c-127">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-127">Example</span></span>

```C
/* Create a DHCP Server instance. */

status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST, "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="0cd0c-128">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="0cd0c-128">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="0cd0c-129">Crea un grupo de direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-129">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="0cd0c-130">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-130">Prototype</span></span>

```C
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG start_ip_address,
    ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="0cd0c-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="0cd0c-131">Description</span></span>

<span data-ttu-id="0cd0c-132">Este servicio crea un grupo específico de interfaces de red de direcciones IP disponibles para el servidor DHCP especificado que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-132">This service creates a network interface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="0cd0c-133">Las direcciones IP inicial y final deben coincidir con la interfaz de red especificada.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-133">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="0cd0c-134">El número real de direcciones IP agregadas puede ser menor que el total de direcciones si la lista de direcciones IP no es suficientemente grande (esto se establece en el parámetro *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* configurable por el usuario).</span><span class="sxs-lookup"><span data-stu-id="0cd0c-134">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0cd0c-135">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0cd0c-135">Input Parameters</span></span>

- <span data-ttu-id="0cd0c-136">**dhcp_ptr**: puntero al bloque de control del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-136">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="0cd0c-137">**iface_index**: índice correspondiente a la interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-137">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="0cd0c-138">**start_ip_address**: primera dirección IP disponible.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-138">**start_ip_address** First available IP address</span></span>
- <span data-ttu-id="0cd0c-139">**end_ip_address**: última dirección IP disponible.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-139">**end_ip_address** Last of the available IP address</span></span>
- <span data-ttu-id="0cd0c-140">**addresses_added**: número de direcciones IP agregadas a la lista.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-140">**addresses_added** Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="0cd0c-141">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-141">Return Values</span></span>

- <span data-ttu-id="0cd0c-142">**NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-142">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="0cd0c-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) el índice no coincide con las direcciones.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="0cd0c-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) entrada de dirección no válida.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99) Invalid address input</span></span>
- <span data-ttu-id="0cd0c-145">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) direcciones de inicio/fin ilógicas.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="0cd0c-146">NX_PTR_ERROR: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-146">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0cd0c-147">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0cd0c-147">Allowed From</span></span>

<span data-ttu-id="0cd0c-148">Application</span><span class="sxs-lookup"><span data-stu-id="0cd0c-148">Application</span></span>

### <a name="example"></a><span data-ttu-id="0cd0c-149">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-149">Example</span></span>

```C
/* Create a pool of available IP addresses to assign. */

status = nx_dhcp_create_server_ip_list(&dhcp_server, iface_index,
    START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS a IP address list was successfully created.
    addresses_added indicates how many IP addresses were actually added to the
    list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="0cd0c-150">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="0cd0c-150">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="0cd0c-151">Quita el registro del cliente de la base de datos del servidor.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-151">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="0cd0c-152">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-152">Prototype</span></span>

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="0cd0c-153">Descripción</span><span class="sxs-lookup"><span data-stu-id="0cd0c-153">Description</span></span>

<span data-ttu-id="0cd0c-154">Este servicio borra el registro del cliente de la base de datos del servidor.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-154">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0cd0c-155">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0cd0c-155">Input Parameters</span></span>

- <span data-ttu-id="0cd0c-156">**dhcp_ptr**: puntero al bloque de control del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-156">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="0cd0c-157">**dhcp_client_ptr: puntero al cliente DHCP que se va a quitar.**</span><span class="sxs-lookup"><span data-stu-id="0cd0c-157">**dhcp_client_ptr Pointer to DHCP Client to remove**</span></span>

### <a name="return-values"></a><span data-ttu-id="0cd0c-158">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-158">Return Values</span></span>

- <span data-ttu-id="0cd0c-159">**NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-159">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="0cd0c-160">NX_PTR_ERROR: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-160">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="0cd0c-161">NX_CALLER_ERROR: (0x11) autor de llamada del servicio sin subproceso.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-161">NX_CALLER_ERROR (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0cd0c-162">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0cd0c-162">Allowed From</span></span>

<span data-ttu-id="0cd0c-163">Application</span><span class="sxs-lookup"><span data-stu-id="0cd0c-163">Application</span></span>

### <a name="example"></a><span data-ttu-id="0cd0c-164">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-164">Example</span></span>

```C
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record(&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="0cd0c-165">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="0cd0c-165">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="0cd0c-166">Establece parámetros de red para opciones de DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-166">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="0cd0c-167">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-167">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG subnet_mask,
    ULONG default_gateway_address,
    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="0cd0c-168">Descripción</span><span class="sxs-lookup"><span data-stu-id="0cd0c-168">Description</span></span>

<span data-ttu-id="0cd0c-169">Este servicio establece los valores predeterminados para los parámetros críticos de red de la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-169">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="0cd0c-170">El servidor DHCP incluirá estas opciones en sus respuestas OFFER y ACK al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-170">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="0cd0c-171">Si los parámetros de interfaz del conjunto de hosts se ejecutan en un servidor DHCP, los parámetros se establecerán de forma predeterminada de la siguiente manera: el enrutador establecido en la puerta de enlace de la interfaz principal para el propio servidor DHCP, la dirección del servidor DNS para el propio servidor DHCP y la máscara de subred en la que se configura la interfaz del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-171">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0cd0c-172">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0cd0c-172">Input Parameters</span></span>

- <span data-ttu-id="0cd0c-173">**dhcp_ptr**: puntero al bloque de control del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-173">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="0cd0c-174">**iface_index**: índice correspondiente a la interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-174">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="0cd0c-175">**subnet_mask**: máscara de subred para la red del cliente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-175">**subnet_mask** Subnet mask for Client network</span></span>
- <span data-ttu-id="0cd0c-176">**default_gateway_address**: dirección IP del enrutador del cliente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-176">**default_gateway_address** Client’s router IP address</span></span>
- <span data-ttu-id="0cd0c-177">**dns_server_address**: servidor DNS para la red del cliente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-177">**dns_server_address** DNS server for Client’s network</span></span>

### <a name="return-values"></a><span data-ttu-id="0cd0c-178">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-178">Return Values</span></span>

- <span data-ttu-id="0cd0c-179">**NX_SUCCESS**: (0x00) servidor DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-179">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="0cd0c-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) el índice no coincide con las direcciones.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="0cd0c-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) parámetros de red no válidos.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="0cd0c-182">NX_PTR_ERROR: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-182">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0cd0c-183">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0cd0c-183">Allowed From</span></span>

<span data-ttu-id="0cd0c-184">Application</span><span class="sxs-lookup"><span data-stu-id="0cd0c-184">Application</span></span>

### <a name="example"></a><span data-ttu-id="0cd0c-185">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-185">Example</span></span>

```C
/* Set network parameters for a specific interface. */

status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
    NX_DHCP_SUBNET_MASK, NX_DHCP_DEFAULT_GATEWAY,
    NX_DHCP_DNS_SERVER);

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="0cd0c-186">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="0cd0c-186">nx_dhcp_server_delete</span></span>

<span data-ttu-id="0cd0c-187">Elimina una instancia de servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-187">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0cd0c-188">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-188">Prototype</span></span>

```C
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0cd0c-189">Descripción</span><span class="sxs-lookup"><span data-stu-id="0cd0c-189">Description</span></span>

<span data-ttu-id="0cd0c-190">Este servicio elimina una instancia del servidor DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-190">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0cd0c-191">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0cd0c-191">Input Parameters</span></span>

- <span data-ttu-id="0cd0c-192">**dhcp_ptr**: puntero a una instancia de servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-192">**dhcp_ptr** Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0cd0c-193">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-193">Return Values</span></span>

- <span data-ttu-id="0cd0c-194">**NX_SUCCESS**: (0x00) servidor DHCP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-194">**NX_SUCCESS** (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="0cd0c-195">NX_PTR_ERROR: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-195">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="0cd0c-196">NX_DHCP_PARAMETER_ERROR: (0x92) entrada no válida que no es puntero.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-196">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="0cd0c-197">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-197">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0cd0c-198">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0cd0c-198">Allowed From</span></span>

<span data-ttu-id="0cd0c-199">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-199">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0cd0c-200">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-200">Example</span></span>

```C
/* Delete a DHCP Server instance. */

status = nx_dhcp_server_delete(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="0cd0c-201">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="0cd0c-201">nx_dhcp_server_start</span></span>

<span data-ttu-id="0cd0c-202">Inicia el procesamiento del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-202">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="0cd0c-203">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-203">Prototype</span></span>

```C
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0cd0c-204">Descripción</span><span class="sxs-lookup"><span data-stu-id="0cd0c-204">Description</span></span>

<span data-ttu-id="0cd0c-205">Este servicio inicia el procesamiento del servidor DHCP, que incluye la creación de un socket UDP del servidor, el enlace del puerto DHCP y la espera para recibir las solicitudes DHCP del cliente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-205">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0cd0c-206">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0cd0c-206">Input Parameters</span></span>

- <span data-ttu-id="0cd0c-207">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-207">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0cd0c-208">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-208">Return Values</span></span>

- <span data-ttu-id="0cd0c-209">**NX_SUCCESS**: (0x00) servidor iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-209">**NX_SUCCESS** (0x00) Successful Server start.</span></span>
- <span data-ttu-id="0cd0c-210">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-210">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="0cd0c-211">NX_PTR_ERROR: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-211">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="0cd0c-212">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-212">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0cd0c-213">NX_DHCP_PARAMETER_ERROR: (0x92) entrada no válida que no es puntero.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-213">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0cd0c-214">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0cd0c-214">Allowed From</span></span>

<span data-ttu-id="0cd0c-215">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0cd0c-216">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-216">Example</span></span>

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="0cd0c-217">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="0cd0c-217">nx_dhcp_server_stop</span></span>

<span data-ttu-id="0cd0c-218">Detiene el procesamiento del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-218">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="0cd0c-219">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-219">Prototype</span></span>

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0cd0c-220">Descripción</span><span class="sxs-lookup"><span data-stu-id="0cd0c-220">Description</span></span>

<span data-ttu-id="0cd0c-221">Este servicio detiene el procesamiento del servidor DHCP, que incluye la recepción de solicitudes de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-221">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0cd0c-222">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0cd0c-222">Input Parameters</span></span>

- <span data-ttu-id="0cd0c-223">**dhcp_ptr**: puntero a una instancia de servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-223">**dhcp_ptr** Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0cd0c-224">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-224">Return Values</span></span>

- <span data-ttu-id="0cd0c-225">**NX_SUCCESS**: (0x00) DHCP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-225">**NX_SUCCESS** (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="0cd0c-226">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-226">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="0cd0c-227">NX_PTR_ERROR: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-227">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="0cd0c-228">NX_CALLER_ERROR: (0x11) autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-228">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0cd0c-229">NX_DHCP_PARAMETER_ERROR: (0x92) entrada no válida que no es puntero.</span><span class="sxs-lookup"><span data-stu-id="0cd0c-229">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0cd0c-230">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0cd0c-230">Allowed From</span></span>

<span data-ttu-id="0cd0c-231">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0cd0c-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0cd0c-232">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0cd0c-232">Example</span></span>

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
