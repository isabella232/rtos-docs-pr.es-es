---
title: 'Capítulo 3: Descripción de los servicios de servidor DHCP de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios de servidor DHCP de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d24c69cf6b8c2bb84b7155e49a54e8296ee662f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815242"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a><span data-ttu-id="2dbaa-103">Capítulo 3: Descripción de los servicios de servidor DHCP de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="2dbaa-103">Chapter 3 - Description of Azure RTOS NetX DHCP Server services</span></span>

<span data-ttu-id="2dbaa-104">Este capítulo contiene una descripción de todos los servicios de servidor DHCP de Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-104">This chapter contains a description of all NetX DHCP Server services.</span></span>

<span data-ttu-id="2dbaa-105">En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2dbaa-106">**nx_dhcp_server_create**: *Crea una instancia de servidor DHCP*.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-106">**nx_dhcp_server_create**: *Create a DHCP Server instance*</span></span>
- <span data-ttu-id="2dbaa-107">**nx_dhcp_set_interface_network_parameters**: *Establece las opciones de servidor DHCP para los parámetros de red críticos de la interfaz especificada*.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-107">**nx_dhcp_set_interface_network_parameters**: *Set DHCP Server options for critical network parameters for specified interface*</span></span>
- <span data-ttu-id="2dbaa-108">**nx_dhcp_create_server_ip_address_list**: *Crea un grupo de direcciones IP disponibles para asignar a la interfaz de clientes DHCP*.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-108">**nx_dhcp_create_server_ip_address_list**: *Create pool of available IP addresses to assign to DHCP Clients interface*</span></span>
- <span data-ttu-id="2dbaa-109">**nx_dhcp_clear_client_record**: *Quita el registro del cliente de la base de datos del servidor*.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-109">**nx_dhcp_clear_client_record**: *Remove Client record in the Server database*</span></span>
- <span data-ttu-id="2dbaa-110">**nx_dhcp_server_delete**: *Elimina una instancia de servidor DHCP*.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-110">**nx_dhcp_server_delete**: *Delete a DHCPServer instance*</span></span>
- <span data-ttu-id="2dbaa-111">**nx_dhcp_server_start**: *Inicia o reanuda el procesamiento del servidor DHCP*.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-111">**nx_dhcp_server_start**: *Start or resume DHCP Server processing*</span></span>
- <span data-ttu-id="2dbaa-112">**nx_dhcp_server_stop**: *Detiene el procesamiento del servidor DHCP*.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-112">**nx_dhcp_server_stop**: *Stop DHCP server processing*</span></span>

## <a name="nx_dhcp_server_create"></a><span data-ttu-id="2dbaa-113">nx_dhcp_server_create</span><span class="sxs-lookup"><span data-stu-id="2dbaa-113">nx_dhcp_server_create</span></span>

<span data-ttu-id="2dbaa-114">Crea una instancia de servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2dbaa-114">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2dbaa-115">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-115">Prototype</span></span>

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="2dbaa-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="2dbaa-116">Description</span></span>

<span data-ttu-id="2dbaa-117">Este servicio crea una instancia de servidor DHCP con una instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-117">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2dbaa-118">La aplicación debe asegurarse de que el grupo de paquetes creado para el servicio de creación de IP tiene como mínimo una carga de 548 bytes, sin incluir los encabezados UDP, IP y Ethernet.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-118">The application must make sure the packet pool created for the IP create service has a minimum548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2dbaa-119">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2dbaa-119">Input Parameters</span></span>

- <span data-ttu-id="2dbaa-120">**dhcp_ptr**: puntero al bloque de control del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-120">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="2dbaa-121">**ip_ptr**: puntero a la instancia de IP del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-121">**ip_ptr**: Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="2dbaa-122">**stack_ptr**: puntero a la ubicación de la pila del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-122">**stack_ptr**: Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="2dbaa-123">**stack_size**: tamaño de la pila del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-123">**stack_size**: Size of DHCP Server stack</span></span>
- <span data-ttu-id="2dbaa-124">**input_address_list**: puntero a la lista de direcciones IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-124">**input_address_list**: Pointer to Server's list of IP addresses</span></span>
- <span data-ttu-id="2dbaa-125">**name_ptr**: puntero al nombre del servido DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-125">**name_ptr**: Pointer to DHCP Server name</span></span>
- <span data-ttu-id="2dbaa-126">**packet_pool_ptr**: puntero al grupo de paquetes del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-126">**packet_pool_ptr**: Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="2dbaa-127">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-127">Return Values</span></span>

- <span data-ttu-id="2dbaa-128">**NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-128">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="2dbaa-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Error de carga de paquete demasiado pequeña.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="2dbaa-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) La lista de opciones está vacía.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) Server option list is empty</span></span>
- <span data-ttu-id="2dbaa-131">NX_DHCP_PARAMETER_ERROR: (0x92) Entrada no válida que no es puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-131">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="2dbaa-132">NX_CALLER_ERROR: (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-132">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="2dbaa-133">NX_PTR_ERROR: (0x16) Entrada no válida de puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-133">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2dbaa-134">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2dbaa-134">Allowed From</span></span>

<span data-ttu-id="2dbaa-135">Application</span><span class="sxs-lookup"><span data-stu-id="2dbaa-135">Application</span></span>

### <a name="example"></a><span data-ttu-id="2dbaa-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-136">Example</span></span>

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="2dbaa-137">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="2dbaa-137">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="2dbaa-138">Crea un grupo de direcciones IP</span><span class="sxs-lookup"><span data-stu-id="2dbaa-138">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="2dbaa-139">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-139">Prototype</span></span>

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="2dbaa-140">Descripción</span><span class="sxs-lookup"><span data-stu-id="2dbaa-140">Description</span></span>

<span data-ttu-id="2dbaa-141">Este servicio crea un grupo específico de interfaces de red de direcciones IP disponibles para el servidor DHCP especificado que se va a asignar.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-141">This service creates a networkinterface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="2dbaa-142">Las direcciones IP inicial y final deben coincidir con la interfaz de red especificada.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-142">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="2dbaa-143">El número real de direcciones IP agregadas puede ser menor que el total de direcciones si la lista de direcciones IP no es suficientemente grande (esto se establece en el parámetro *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* configurable por el usuario).</span><span class="sxs-lookup"><span data-stu-id="2dbaa-143">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2dbaa-144">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2dbaa-144">Input Parameters</span></span>

- <span data-ttu-id="2dbaa-145">**dhcp_ptr**: puntero al bloque de control del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-145">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="2dbaa-146">**iface_index**: índice correspondiente a la interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-146">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="2dbaa-147">**start_ip_address**: primera dirección IP disponible.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-147">**start_ip_address**: First available IP address</span></span>
- <span data-ttu-id="2dbaa-148">**end_ip_address**: última dirección IP disponible.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-148">**end_ip_address**: Last of the available IP address</span></span>
- <span data-ttu-id="2dbaa-149">**addresses_added**: número de direcciones IP agregadas a la lista.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-149">**addresses_added**: Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="2dbaa-150">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-150">Return Values</span></span>

- <span data-ttu-id="2dbaa-151">**NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-151">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="2dbaa-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) El índice no coincide con las direcciones.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="2dbaa-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Entrada de dirección no válida.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Invalid address input</span></span>
- <span data-ttu-id="2dbaa-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Direcciones de inicio/fin ilógicas.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="2dbaa-155">NX_PTR_ERROR: (0x16) Entrada no válida de puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-155">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2dbaa-156">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2dbaa-156">Allowed From</span></span>

<span data-ttu-id="2dbaa-157">Application</span><span class="sxs-lookup"><span data-stu-id="2dbaa-157">Application</span></span>

### <a name="example"></a><span data-ttu-id="2dbaa-158">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-158">Example</span></span>

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="2dbaa-159">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="2dbaa-159">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="2dbaa-160">Quita el registro del cliente de la base de datos del servidor</span><span class="sxs-lookup"><span data-stu-id="2dbaa-160">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="2dbaa-161">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-161">Prototype</span></span>

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="2dbaa-162">Descripción</span><span class="sxs-lookup"><span data-stu-id="2dbaa-162">Description</span></span>

<span data-ttu-id="2dbaa-163">Este servicio borra el registro del cliente de la base de datos del servidor.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-163">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2dbaa-164">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2dbaa-164">Input Parameters</span></span>

- <span data-ttu-id="2dbaa-165">**dhcp_ptr**: puntero al bloque de control del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-165">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="2dbaa-166">**dhcp_client_ptr**: puntero al cliente DHCP que se va a quitar.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-166">**dhcp_client_ptr**: Pointer to DHCP Client to remove</span></span>

### <a name="return-values"></a><span data-ttu-id="2dbaa-167">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-167">Return Values</span></span>

- <span data-ttu-id="2dbaa-168">**NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-168">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="2dbaa-169">NX_PTR_ERROR: (0x16) Entrada no válida de puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-169">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="2dbaa-170">NX_CALLER_ERROR: (0x11) Autor de llamada del servicio sin subproceso.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-170">NX_CALLER_ERROR: (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2dbaa-171">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2dbaa-171">Allowed From</span></span>

<span data-ttu-id="2dbaa-172">Application</span><span class="sxs-lookup"><span data-stu-id="2dbaa-172">Application</span></span>

### <a name="example"></a><span data-ttu-id="2dbaa-173">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-173">Example</span></span>

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="2dbaa-174">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="2dbaa-174">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="2dbaa-175">Establece parámetros de red para opciones de DHCP</span><span class="sxs-lookup"><span data-stu-id="2dbaa-175">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="2dbaa-176">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-176">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="2dbaa-177">Descripción</span><span class="sxs-lookup"><span data-stu-id="2dbaa-177">Description</span></span>

<span data-ttu-id="2dbaa-178">Este servicio establece los valores predeterminados para los parámetros críticos de red de la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-178">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="2dbaa-179">El servidor DHCP incluirá estas opciones en sus respuestas OFFER y ACK al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-179">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="2dbaa-180">Si los parámetros de interfaz del conjunto de hosts se ejecutan en un servidor DHCP, los parámetros se establecerán de forma predeterminada de la siguiente manera: el enrutador establecido en la puerta de enlace de la interfaz principal para el propio servidor DHCP, la dirección del servidor DNS para el propio servidor DHCP y la máscara de subred en la que se configura la interfaz del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-180">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2dbaa-181">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2dbaa-181">Input Parameters</span></span>

- <span data-ttu-id="2dbaa-182">**dhcp_ptr**: puntero al bloque de control del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-182">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="2dbaa-183">**iface_index**: índice correspondiente a la interfaz de red.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-183">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="2dbaa-184">**subnet_mask**: máscara de subred para la red del cliente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-184">**subnet_mask**: Subnet mask for Client network</span></span>
- <span data-ttu-id="2dbaa-185">**default_gateway_address**: dirección IP del enrutador del cliente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-185">**default_gateway_address**: Client's router IP address</span></span>
- <span data-ttu-id="2dbaa-186">**dns_server_address**: servidor DNS para la red del cliente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-186">**dns_server_address**: DNS server for Client's network</span></span>

### <a name="return-values"></a><span data-ttu-id="2dbaa-187">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-187">Return Values</span></span>

- <span data-ttu-id="2dbaa-188">**NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-188">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="2dbaa-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) El índice no coincide con las direcciones.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="2dbaa-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Parámetros de red no válidos.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="2dbaa-191">NX_PTR_ERROR: (0x16) Entrada no válida de puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-191">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2dbaa-192">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2dbaa-192">Allowed From</span></span>

<span data-ttu-id="2dbaa-193">Application</span><span class="sxs-lookup"><span data-stu-id="2dbaa-193">Application</span></span>

### <a name="example"></a><span data-ttu-id="2dbaa-194">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-194">Example</span></span>

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="2dbaa-195">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="2dbaa-195">nx_dhcp_server_delete</span></span>

<span data-ttu-id="2dbaa-196">Elimina una instancia de servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2dbaa-196">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2dbaa-197">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-197">Prototype</span></span>

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2dbaa-198">Descripción</span><span class="sxs-lookup"><span data-stu-id="2dbaa-198">Description</span></span>

<span data-ttu-id="2dbaa-199">Este servicio elimina una instancia de cliente DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-199">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2dbaa-200">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2dbaa-200">Input Parameters</span></span>

- <span data-ttu-id="2dbaa-201">**dhcp_ptr**: puntero a una instancia de servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-201">**dhcp_ptr**: Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2dbaa-202">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-202">Return Values</span></span>

- <span data-ttu-id="2dbaa-203">**NX_SUCCESS**: (0x00) Servidor DHCP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-203">**NX_SUCCESS**: (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="2dbaa-204">NX_PTR_ERROR: (0x16) Entrada no válida de puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-204">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="2dbaa-205">NX_DHCP_PARAMETER_ERROR: (0x92) Entrada no válida que no es puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-205">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="2dbaa-206">NX_CALLER_ERROR: (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-206">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2dbaa-207">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2dbaa-207">Allowed From</span></span>

<span data-ttu-id="2dbaa-208">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-208">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2dbaa-209">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-209">Example</span></span>

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="2dbaa-210">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="2dbaa-210">nx_dhcp_server_start</span></span>

<span data-ttu-id="2dbaa-211">Inicia el procesamiento del servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2dbaa-211">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2dbaa-212">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-212">Prototype</span></span>

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2dbaa-213">Descripción</span><span class="sxs-lookup"><span data-stu-id="2dbaa-213">Description</span></span>

<span data-ttu-id="2dbaa-214">Este servicio inicia el procesamiento del servidor DHCP, que incluye la creación de un socket UDP del servidor, el enlace del puerto DHCP y la espera para recibir las solicitudes DHCP del cliente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-214">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2dbaa-215">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2dbaa-215">Input Parameters</span></span>

- <span data-ttu-id="2dbaa-216">**dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-216">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2dbaa-217">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-217">Return Values</span></span>

- <span data-ttu-id="2dbaa-218">**NX_SUCCESS**: (0x00) Servidor iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-218">**NX_SUCCESS**: (0x00) Successful Server start.</span></span>  
- <span data-ttu-id="2dbaa-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="2dbaa-220">NX_PTR_ERROR: (0x16) Entrada no válida de puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-220">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="2dbaa-221">NX_CALLER_ERROR: (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-221">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="2dbaa-222">NX_DHCP_PARAMETER_ERROR: (0x92) Entrada no válida que no es puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-222">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2dbaa-223">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2dbaa-223">Allowed From</span></span>

<span data-ttu-id="2dbaa-224">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2dbaa-225">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-225">Example</span></span>

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="2dbaa-226">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2dbaa-226">See Also</span></span>

<span data-ttu-id="2dbaa-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="2dbaa-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span></span>

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="2dbaa-228">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="2dbaa-228">nx_dhcp_server_stop</span></span>

<span data-ttu-id="2dbaa-229">Detiene el procesamiento del servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2dbaa-229">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2dbaa-230">Prototipo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-230">Prototype</span></span>

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2dbaa-231">Descripción</span><span class="sxs-lookup"><span data-stu-id="2dbaa-231">Description</span></span>

<span data-ttu-id="2dbaa-232">Este servicio detiene el procesamiento del servidor DHCP, que incluye la recepción de solicitudes de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-232">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2dbaa-233">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="2dbaa-233">Input Parameters</span></span>

- <span data-ttu-id="2dbaa-234">**dhcp_ptr**: puntero a una instancia de servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-234">**dhcp_ptr**: Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2dbaa-235">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-235">Return Values</span></span>

- <span data-ttu-id="2dbaa-236">**NX_SUCCESS**: (0x00) DHCP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-236">**NX_SUCCESS**: (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="2dbaa-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="2dbaa-238">NX_PTR_ERROR: (0x16) Entrada no válida de puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-238">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="2dbaa-239">NX_CALLER_ERROR: (0x11) Autor de llamada no válido del servicio.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-239">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="2dbaa-240">NX_DHCP_PARAMETER_ERROR: (0x92) Entrada no válida que no es puntero.</span><span class="sxs-lookup"><span data-stu-id="2dbaa-240">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2dbaa-241">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="2dbaa-241">Allowed From</span></span>

<span data-ttu-id="2dbaa-242">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="2dbaa-242">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2dbaa-243">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="2dbaa-243">Example</span></span>

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
