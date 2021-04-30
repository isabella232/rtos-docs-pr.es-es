---
title: 'Capítulo 2: Instalación y uso del servidor DHCP de Azure RTOS NetX DHCP'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente del servidor DHCP de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 034a4d74c566fbfe94981a42b7e06e7f2ee79d25
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815246"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-dhcp-server"></a><span data-ttu-id="9f28e-103">Capítulo 2: Instalación y uso del servidor DHCP de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="9f28e-103">Chapter 2 - Installation and use of the Azure RTOS NetX DHCP Server</span></span>

<span data-ttu-id="9f28e-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente DHCP de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="9f28e-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="9f28e-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="9f28e-105">Product Distribution</span></span>

<span data-ttu-id="9f28e-106">El servidor DHCP de Azure RTOS NetX se puede obtener desde nuestro repositorio de código fuente público en [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span><span class="sxs-lookup"><span data-stu-id="9f28e-106">Azure RTOS NetX DHCP Server can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="9f28e-107">El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="9f28e-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="9f28e-108">**nx_dhcp_server.h**: archivo de encabezado para el servidor DHCP de NetX</span><span class="sxs-lookup"><span data-stu-id="9f28e-108">**nx_dhcp_server.h**: Header file for NetX DHCP Server</span></span>
- <span data-ttu-id="9f28e-109">**nx_dhcp_server. c**: archivo de código fuente C para el servidor DHCP de NetX</span><span class="sxs-lookup"><span data-stu-id="9f28e-109">**nx_dhcp_server.c**: C Source file for NetX DHCP Server</span></span>
- <span data-ttu-id="9f28e-110">**nx_dhcp_server.pdf**: descripción en PDF del servidor DHCP de NetX</span><span class="sxs-lookup"><span data-stu-id="9f28e-110">**nx_dhcp_server.pdf**: PDF description of NetX DHCP Server</span></span>
- <span data-ttu-id="9f28e-111">**demo_netx_dhcp_server.c**: demostración del servidor DHCP de NetX</span><span class="sxs-lookup"><span data-stu-id="9f28e-111">**demo_netx_dhcp_server.c**: NetX DHCP Server demonstration</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="9f28e-112">Instalación de DHCP</span><span class="sxs-lookup"><span data-stu-id="9f28e-112">DHCP Installation</span></span>

<span data-ttu-id="9f28e-113">Para usar el servidor DHCP de NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="9f28e-113">In order to use NetX DHCP Server, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="9f28e-114">Por ejemplo, si NetX está instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_dhcp_server.h* y *nx_dhpc_server.c* deben copiarse en ese mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="9f28e-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_dhcp_server.h* and *nx_dhpc_server.c* files should be copied into this directory.</span></span>

## <a name="using-netx-dhcp-server"></a><span data-ttu-id="9f28e-115">Uso del servidor DHCP de NetX</span><span class="sxs-lookup"><span data-stu-id="9f28e-115">Using NetX DHCP Server</span></span>

<span data-ttu-id="9f28e-116">El uso del servidor DHCP de NetX es sencillo.</span><span class="sxs-lookup"><span data-stu-id="9f28e-116">Using NetX DHCP Server is easy.</span></span> <span data-ttu-id="9f28e-117">Básicamente, el código de la aplicación debe incluir *nx_dhcp_server.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-117">Basically, the application code must include *nx_dhcp_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="9f28e-118">Después de incluir *nx_dhcp_server.h*, el código de la aplicación puede realizar las llamadas de función DHCP especificadas más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="9f28e-118">Once *nx_dhcp_server.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="9f28e-119">La aplicación también debe incluir *nx_dhcp_server.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="9f28e-119">The application must also include *nx_dhcp_server.c* in the build process.</span></span> <span data-ttu-id="9f28e-120">Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9f28e-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="9f28e-121">Para obtener más información sobre el uso del servidor DHCP de NetX, consulte los siguientes apartados: [Requisitos del servidor DHCP de NetX](#requirements-of-the-netx-dhcp-server) y [Restricciones del servidor DHCP de NetX](#constraints-of-the-netx-dhcp-server).</span><span class="sxs-lookup"><span data-stu-id="9f28e-121">For more details on using NetX DHCP Server, see the following sections [Requirements of the NetX DHCPServer](#requirements-of-the-netx-dhcp-server) and [Constraints of the NetX DHCP Server](#constraints-of-the-netx-dhcp-server).</span></span>

> [!NOTE]
> <span data-ttu-id="9f28e-122">Observe que, como DHCP usa los servicios UDP de NetX, debe habilitarse UDP con la llamada a *nx_udp_enable* antes de utilizar DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-122">Since DHCP utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

## <a name="requirements-of-the-netx-dhcp-server"></a><span data-ttu-id="9f28e-123">Requisitos del servidor DHCP de NetX</span><span class="sxs-lookup"><span data-stu-id="9f28e-123">Requirements of the NetX DHCP Server</span></span>

<span data-ttu-id="9f28e-124">El servidor DHCP de NetX requiere un puerto de socket UDP asignado al puerto DHCP 67 conocido.</span><span class="sxs-lookup"><span data-stu-id="9f28e-124">The NetX DHCP Server requires a UDP socket port assigned to the well known DHCP port 67.</span></span> <span data-ttu-id="9f28e-125">Para crear el servidor DHCP, la aplicación debe crear un grupo de paquetes con una carga de paquetes de al menos 548 bytes más los encabezados IP, UDP y Ethernet (que tienen un total de 44 bytes con una alineación de 4 bytes).</span><span class="sxs-lookup"><span data-stu-id="9f28e-125">To create the DHCP Server, the application must create a packet pool with packet payload at least 548 bytes plus IP, UDP and Ethernet headers (which total 44 bytes with 4 byte alignment).</span></span>

<span data-ttu-id="9f28e-126">Se supone que el servidor y el cliente usan la configuración de la dirección de hardware Ethernet:</span><span class="sxs-lookup"><span data-stu-id="9f28e-126">It is assumed that the Server and Client are both using Ethernet hardware address settings:</span></span>

- <span data-ttu-id="9f28e-127">**Tipo de hardware**: 1</span><span class="sxs-lookup"><span data-stu-id="9f28e-127">**Hardware type**: 1</span></span>
- <span data-ttu-id="9f28e-128">**Longitud de hardware**: 6</span><span class="sxs-lookup"><span data-stu-id="9f28e-128">**Hardware length**: 6</span></span>
- <span data-ttu-id="9f28e-129">**Saltos**: 0</span><span class="sxs-lookup"><span data-stu-id="9f28e-129">**Hops**: 0</span></span>

### <a name="multiple-client-sessions"></a><span data-ttu-id="9f28e-130">Varias sesiones de cliente</span><span class="sxs-lookup"><span data-stu-id="9f28e-130">Multiple Client Sessions</span></span>

<span data-ttu-id="9f28e-131">El servidor DHCP de NetX puede controlar varias sesiones de cliente manteniendo una tabla de clientes DHCP activos y el "estado" en el que se encuentra el cliente, por ejemplo, los estados DHCP INIT, BOOT, SELECTING, REQUESTING, RENEWING, etc. Si el tiempo de espera de la sesión expira antes de recibir el siguiente mensaje de cliente, a menos que el cliente esté enlazado a una concesión de IP, el servidor borrará los datos de la sesión de cliente y devolverá la dirección IP asignada al grupo disponible.</span><span class="sxs-lookup"><span data-stu-id="9f28e-131">The NetX DHCP Server can handles multiple Client sessions by keeping a table of active DHCP clients and what 'state' the Client is in e.g. DHCP states INIT, BOOT, SELECTING, REQUESTING, RENEWING etc. If the session time out expires before receiving the next Client message, unless that Client is bound to an IP lease, the Server will clear the Client session data and return the assigned IP address back to the available pool.</span></span> <span data-ttu-id="9f28e-132">Si el servidor recibe varios mensajes DISCOVER del mismo cliente, el servidor restablece el tiempo de espera de la sesión y mantiene la dirección IP reservada para que el cliente acepte en un mensaje REQUEST posterior.</span><span class="sxs-lookup"><span data-stu-id="9f28e-132">If the Server receives multiple DISCOVER messages from the same Client the Server resets the session time out and keeps the IP address reserved for the Client to accept in a subsequent REQUEST message.</span></span>

<span data-ttu-id="9f28e-133">El servidor DHCP de NetX también acepta la solicitud DHCP de cliente de un solo estado; por ejemplo, el cliente solo envía un mensaje REQUEST.</span><span class="sxs-lookup"><span data-stu-id="9f28e-133">The NetX DHCP Server also accepts the single state Client DHCP request e.g. the Client only sends a REQUEST message.</span></span> <span data-ttu-id="9f28e-134">Se supone que al cliente se le ha asignado previamente una concesión de IP del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-134">This assumes the Client has been previously assigned an IP lease from the DHCP server.</span></span>

### <a name="setting-interface-specific-network-parameters-server-responses"></a><span data-ttu-id="9f28e-135">Configuración de las respuestas del servidor de parámetros de red específicos de la interfaz</span><span class="sxs-lookup"><span data-stu-id="9f28e-135">Setting Interface Specific Network Parameters Server Responses</span></span>

<span data-ttu-id="9f28e-136">La aplicación puede configurar el enrutador, la máscara de subred y los parámetros del servidor DNS para cada interfaz que administra las solicitudes de cliente DHCP mediante el servicio *nx_dhcp_set_interface_network_parameters*.</span><span class="sxs-lookup"><span data-stu-id="9f28e-136">The application can set the router, subnet mask and DNS server parameters for each interface it handles DHCP Client requests, using the *nx_dhcp_set_interface_network_parameters* service.</span></span> <span data-ttu-id="9f28e-137">De lo contrario, estos parámetros se configuran de forma predeterminada para la puerta de enlace IP en la interfaz principal del servidor, la subred de red DHCP y la dirección IP del servidor DHCP, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-137">Otherwise these parameters are defaulted to the IP gateway on the Server's primary interface, its DHCP network subnet, and DHCP Server IP address, respectively.</span></span>

<span data-ttu-id="9f28e-138">El servidor DHCP incluye estos parámetros en la opción datos de los mensajes DHCP que envía a los clientes DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-138">The DHCP Server includes these parameters in the option data of DHCP messages it sends to DHCP clients.</span></span>

### <a name="assigning-ip-addresses-to-the-client"></a><span data-ttu-id="9f28e-139">Asignación de direcciones IP al cliente</span><span class="sxs-lookup"><span data-stu-id="9f28e-139">Assigning IP addresses to the Client</span></span>

<span data-ttu-id="9f28e-140">Si el mensaje DISCOVER de cliente no especifica una dirección IP solicitada, el servidor DHCP puede usar una de su propio grupo.</span><span class="sxs-lookup"><span data-stu-id="9f28e-140">If the Client DISCOVER message does not specify a requested IP address, the DHCP Server can use one from its own pool.</span></span> <span data-ttu-id="9f28e-141">Si el servidor no tiene ninguna dirección IP disponible, enviará al cliente un mensaje NACK.</span><span class="sxs-lookup"><span data-stu-id="9f28e-141">If the Server has no available IP addresses it will send the Client a NACK message.</span></span>

<span data-ttu-id="9f28e-142">El servidor DHCP de NetX concederá la dirección IP solicitada en el mensaje REQUEST de cliente siempre que la dirección IP esté disponible y se encuentre en la base de datos de direcciones IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="9f28e-142">The NetX DHCP Server will grant the requested IP address in the Client REQUEST message as long as the IP address is available and can be found in the Server IP address database.</span></span> <span data-ttu-id="9f28e-143">La aplicación crea la lista de direcciones IP disponibles del servidor para asignar a los clientes DHCP mediante el servicio *nx_dhcp_create_server_ip_address_list*.</span><span class="sxs-lookup"><span data-stu-id="9f28e-143">The application creates the Server's list of available IP addresses for assigning to DHCP Clients using the *nx_dhcp_create_server_ip_address_list* service.</span></span> <span data-ttu-id="9f28e-144">Si el servidor no tiene las direcciones IP solicitadas o se asigna a otro host, enviará al cliente un mensaje NACK.</span><span class="sxs-lookup"><span data-stu-id="9f28e-144">If the Server does not have the requested IP addresses or it is assigned to another host it will send the Client a NACK message.</span></span>

<span data-ttu-id="9f28e-145">Cuando el servidor DHCP recibe una solicitud de cliente, identifica a ese cliente de forma exclusiva mediante la dirección MAC del cliente en el campo dirección MAC del cliente en el mensaje de DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-145">When the DHCP Server receives a Client request, it identifies that Client uniquely using the Client MAC address in the Client MAC address field in the DHCP message.</span></span> <span data-ttu-id="9f28e-146">Si el cliente cambia su dirección MAC o se mueve a otra subred, debe enviar un mensaje RELEASE al servidor para devolver la dirección IP al grupo disponible y solicitar una nueva dirección IP en el estado INIT.</span><span class="sxs-lookup"><span data-stu-id="9f28e-146">If the Client changes it's MAC address or is moved elsewhere onto another subnet it should send a RELEASE message to the Server to return the IP address back to the available pool, and request a new IP address in the INIT state.</span></span>

<span data-ttu-id="9f28e-147">Consulte la figura 1.1 de la sección **Sistema de ejemplo pequeño** para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="9f28e-147">See Figure 1.1 of the **Small Example System** section for details.</span></span> <span data-ttu-id="9f28e-148">El número de direcciones IP guardadas en la instancia del servidor DHCP se limita al tamaño de la matriz de direcciones del servidor en el bloque de control del servidor DHCP y se define mediante la opción configurable NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.</span><span class="sxs-lookup"><span data-stu-id="9f28e-148">The number of IP addresses saved to the DHCP Server instance is limited to the size of the server address array in the DHCP Server control block, and defined by the configurable option NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.</span></span>

### <a name="ip-address-lease-times"></a><span data-ttu-id="9f28e-149">Tiempos de concesión de dirección IP</span><span class="sxs-lookup"><span data-stu-id="9f28e-149">IP Address Lease Times</span></span>

<span data-ttu-id="9f28e-150">El servidor DHCP también aceptará el tiempo de concesión del cliente de la solicitud si dicho tiempo de concesión es menor que el tiempo de concesión predeterminado del servidor, que se define en la opción configurable NX_DHCP_DEFAULT_LEASE_TIME.</span><span class="sxs-lookup"><span data-stu-id="9f28e-150">The DHCP Server will also accept the request Client lease time if that lease time is less than the Server default lease time which is defined in configurable option NX_DHCP_DEFAULT_LEASE_TIME.</span></span> <span data-ttu-id="9f28e-151">Los tiempos de renovación y reenlace asignados al cliente son del 50 % y del 85 % del tiempo de concesión, respectivamente, a menos que el tiempo de concesión sea infinito (0xFFFFFFFF), en cuyo caso los tiempos de renovación y reenlace también se establecen en infinito.</span><span class="sxs-lookup"><span data-stu-id="9f28e-151">Renewal and rebind times assigned to the Client are 50% and 85% of the lease time, respectively, unless the lease time is infinity (0xFFFFFFFF), in which case renewal and rebind times are also set to infinity.</span></span>

### <a name="dhcp-server-timeouts"></a><span data-ttu-id="9f28e-152">Tiempos de expiración del servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="9f28e-152">DHCP Server Timeouts</span></span>

<span data-ttu-id="9f28e-153">El servidor DHCP tiene un tiempo de espera de sesión configurable de usuario, NX_DHCP_CLIENT_SESSION_TIMEOUT, para esperar al siguiente mensaje de cliente DHCP, a menos que se complete la sesión.</span><span class="sxs-lookup"><span data-stu-id="9f28e-153">The DHCP Server has a user configurable session timeout, NX_DHCP_CLIENT_SESSION_TIMEOUT, for waiting for the next DHCP Client message unless the session is completed.</span></span> <span data-ttu-id="9f28e-154">El tiempo de espera se restablece cuando el servidor recibe el mensaje siguiente del cliente, independientemente de si es el mismo mensaje enviado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-154">The time out is reset when the Server receives the next message from the Client regardless if is the same message previously sent.</span></span>

### <a name="internal-error-handling"></a><span data-ttu-id="9f28e-155">Control de errores interno</span><span class="sxs-lookup"><span data-stu-id="9f28e-155">Internal error handling</span></span>

<span data-ttu-id="9f28e-156">El servidor DHCP recibe y procesa los paquetes de cliente DHCP en la función *nx_dhcp_listen_for_messages*.</span><span class="sxs-lookup"><span data-stu-id="9f28e-156">The DHCP Server receives and processes DHCP Client packets in the *nx_dhcp_listen_for_messages* function.</span></span> <span data-ttu-id="9f28e-157">Esta función interrumpirá el procesamiento del paquete de cliente DHCP actual si el paquete no es válido o el servidor DHCP encuentra un error interno. n *x_dhcp_listen_for_messages* devuelve un estado de error.</span><span class="sxs-lookup"><span data-stu-id="9f28e-157">This function will discontinue processing the current DHCP Client packet if the packet is invalid, or the DHCP Server encounters an internal error.n *x_dhcp_listen_for_messages* returns an error status.</span></span> <span data-ttu-id="9f28e-158">El subproceso del servidor DHCP cede el control brevemente del programador de ThreadX antes de llamar a esta función para recibir el siguiente mensaje de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-158">The DHCP Server thread relinquishes control briefly of the ThreadX scheduler before calling this function to receive the next DHCP Client message.</span></span> <span data-ttu-id="9f28e-159">En la versión actual no hay compatibilidad de registro para el estado de error devuelto desde *nx_dhcp_listen_for_messages.*</span><span class="sxs-lookup"><span data-stu-id="9f28e-159">In the current release there is no logging support for error status returns from *nx_dhcp_listen_for_messages.*</span></span>

### <a name="option-55-parameter-request-list"></a><span data-ttu-id="9f28e-160">Opción 55: lista de solicitudes de parámetros</span><span class="sxs-lookup"><span data-stu-id="9f28e-160">Option 55: Parameter Request List</span></span>

<span data-ttu-id="9f28e-161">El servidor DHCP de NetX debe estar configurado con un conjunto de opciones para cargar en la lista de la opción de solicitud de parámetros (55) en los mensajes OFFER y DHCPACK que se transmiten de vuelta al cliente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-161">The NetX DHCP Server must be configured with a set of options to load to Parameter Request Option (55) list in the OFFER and DHCPACK messages it transmits back to the Client.</span></span> <span data-ttu-id="9f28e-162">Estas opciones deben incluir datos de configuración críticos de red para la red de cliente y, de forma predeterminada, se define como dirección IP del enrutador, máscara de subred y servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="9f28e-162">These options should include network critical configuration data for the Client network and by default is defined to be router IP address, subnet mask, and DNS server.</span></span> <span data-ttu-id="9f28e-163">La lista de opciones es una lista delimitada por espacios y se define en la NX_DHCP_DEFAULT_SERVER_OPTION_LIST configurable por el usuario.</span><span class="sxs-lookup"><span data-stu-id="9f28e-163">The option list is a space delimited list and defined in the user configurable NX_DHCP_DEFAULT_SERVER_OPTION_LIST.</span></span> <span data-ttu-id="9f28e-164">Observe que el número de opciones especificado en esta lista debe ser igual que NX_DHCP_DEFAULT_OPTION_LIST_SIZE, que también está definido por el usuario.</span><span class="sxs-lookup"><span data-stu-id="9f28e-164">Note the number of options specified in this list must equal NX_DHCP_DEFAULT_OPTION_LIST_SIZE which is also user defined.</span></span>

## <a name="constraints-of-the-netx-dhcp-server"></a><span data-ttu-id="9f28e-165">Restricciones del servidor DHCP de NetX</span><span class="sxs-lookup"><span data-stu-id="9f28e-165">Constraints of the NetX DHCP Server</span></span>

### <a name="dhcp-messages"></a><span data-ttu-id="9f28e-166">Mensajes DHCP</span><span class="sxs-lookup"><span data-stu-id="9f28e-166">DHCP Messages</span></span>

<span data-ttu-id="9f28e-167">El servidor DHCP de NetX no comprueba si no se ha asignado una dirección IP en otra parte de la red antes de conceder la dirección IP al cliente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-167">The NetX DHCP Server does not verify that an IP address has not been assigned elsewhere on the network before granting the IP address to the Client.</span></span> <span data-ttu-id="9f28e-168">Si hay varios servidores DHCP, este podría ser el caso.</span><span class="sxs-lookup"><span data-stu-id="9f28e-168">If there are multiple DHCP servers, this can indeed be the case.</span></span> <span data-ttu-id="9f28e-169">*Según RFC 2131, es responsabilidad del cliente comprobar que la dirección IP es única en su red* (por ejemplo, haciendo ping a la dirección).</span><span class="sxs-lookup"><span data-stu-id="9f28e-169">*As per RFC 2131, it is the Client's responsibility to verify the IP address is unique on its network* (e.g. pinging the address).</span></span> <span data-ttu-id="9f28e-170">Si no es así, el servidor debería recibir un mensaje DECLINE con la dirección IP para actualizar su base de datos desde el cliente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-170">If it is not, the Server should receive a DECLINE message with the IP address to update its database from the Client.</span></span>

<span data-ttu-id="9f28e-171">El servidor DHCP de NetX no emite mensajes de FORCE_RENEW.</span><span class="sxs-lookup"><span data-stu-id="9f28e-171">The NetX DHCP Server does not issue FORCE_RENEW messages.</span></span> <span data-ttu-id="9f28e-172">Es el cliente DHCP el que renueva su concesión de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-172">It is up to the DHCP Client to renew its IP address lease.</span></span> <span data-ttu-id="9f28e-173">Sin embargo, el servidor DHCP supervisa el tiempo restante en todas las direcciones IP asignadas en su base de datos.</span><span class="sxs-lookup"><span data-stu-id="9f28e-173">However, the DHCP Server monitors the time remaining on all the assigned IP addresses in its database.</span></span> <span data-ttu-id="9f28e-174">Cuando expira una concesión de dirección IP, se devuelve la dirección IP al grupo de direcciones IP disponibles.</span><span class="sxs-lookup"><span data-stu-id="9f28e-174">When an IP address lease expires, that IP address is returned to the pool of available IP addresses.</span></span> <span data-ttu-id="9f28e-175">Por lo tanto, es el cliente quien debe renovar o volver a enlazar activamente su concesión de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-175">Hence it is up to the Client to actively renew/rebind its IP address lease.</span></span>

<span data-ttu-id="9f28e-176">Los datos de la sesión se borran en cuanto el cliente se le concede ("se enlaza") a una concesión de IP (o se renueva una existente).</span><span class="sxs-lookup"><span data-stu-id="9f28e-176">Session data is cleared as soon as the Client either is granted ("bound") to an IP lease (or an existing one is renewed).</span></span> <span data-ttu-id="9f28e-177">Si un paquete de cliente demuestra ser ficticio o el cliente agota el tiempo de espera entre respuestas, se borran los datos de la sesión.</span><span class="sxs-lookup"><span data-stu-id="9f28e-177">If a Client packet proves bogus, or the Client times out between responses, session data is cleared.</span></span>

### <a name="saving-data-between-reboots"></a><span data-ttu-id="9f28e-178">Guardado de datos entre reinicios</span><span class="sxs-lookup"><span data-stu-id="9f28e-178">Saving Data Between Reboots</span></span>

<span data-ttu-id="9f28e-179">El servidor DHCP de NetX guarda los datos de cliente, incluidos los parámetros de solicitud DHCP, en una tabla de registros de cliente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-179">The NetX DHCP Server saves Client data including DHCP request parameters in a Client record table.</span></span> <span data-ttu-id="9f28e-180">Esta tabla no se almacena en memoria no volátil, por lo que, si el host del servidor DHCP debe reiniciar esa información, no se guarda entre reinicios.</span><span class="sxs-lookup"><span data-stu-id="9f28e-180">This table is not stored in non volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

<span data-ttu-id="9f28e-181">El servidor DHCP de NetX guarda los datos de concesión de direcciones IP en una tabla de direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-181">The NetX DHCP Server saves IP address lease data in a IP address table.</span></span> <span data-ttu-id="9f28e-182">Esta tabla no se almacena en memoria no volátil, por lo que, si el host del servidor DHCP debe reiniciar esa información, no se guarda entre reinicios.</span><span class="sxs-lookup"><span data-stu-id="9f28e-182">This table is not stored in non volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

### <a name="relay-agents"></a><span data-ttu-id="9f28e-183">Agentes de retransmisión</span><span class="sxs-lookup"><span data-stu-id="9f28e-183">Relay Agents</span></span>

<span data-ttu-id="9f28e-184">El servidor DHCP de NetX está configurado con una dirección IP cero para el campo 'agente de retransmisión' porque no es compatible con las solicitudes DHCP de la red.</span><span class="sxs-lookup"><span data-stu-id="9f28e-184">The NetX DHCP Server is configured with a zero IP address for the 'Relay agent' field because it does not support out of network DHCP requests.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="9f28e-185">Sistema de ejemplo pequeño</span><span class="sxs-lookup"><span data-stu-id="9f28e-185">Small Example System</span></span>

<span data-ttu-id="9f28e-186">Un ejemplo de lo fácil que es usar el servidor DHCP de NetX se describe en la figura 1.1 que aparece a continuación.</span><span class="sxs-lookup"><span data-stu-id="9f28e-186">An example of how easy it is to use the NetX DHCP Server is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="9f28e-187">En este ejemplo, el archivo de inclusión DHCP *nx_dhcp_server.h* se agrega en la línea 5.</span><span class="sxs-lookup"><span data-stu-id="9f28e-187">In this example, the DHCP include file *nx_dhcp_server.h* is brought in at line 5.</span></span> <span data-ttu-id="9f28e-188">El tamaño de la pila del subproceso del servidor DHCP, el tamaño de la pila del subproceso IP y el tamaño de la pila del subproceso de prueba se definen en las líneas 7-13.</span><span class="sxs-lookup"><span data-stu-id="9f28e-188">DHCP Server thread stack size, IP thread stack size and test thread stack size are all defined in lines 7-13.</span></span>

<span data-ttu-id="9f28e-189">En primer lugar, se crea una tarea de subproceso de prueba opcional para detener, reiniciar y eliminar el servidor DHCP con la función "*test_thread_entry*" en la línea 57.</span><span class="sxs-lookup"><span data-stu-id="9f28e-189">First, an optional test thread task for stopping, restarting and eventually deleting the DHCP server is created with the "*test_thread_entry*" function at line 57.</span></span> <span data-ttu-id="9f28e-190">Un bloque de control de servidor DHCP "*dhcp_server*" se define como una variable global en la línea 20.</span><span class="sxs-lookup"><span data-stu-id="9f28e-190">A DHCP Server control block "*dhcp_server*" is defined as a global variable at line 20.</span></span> <span data-ttu-id="9f28e-191">Observe que el grupo de paquetes de servidor se crea con paquetes que tienen una carga al menos tan grande como el mensaje DHCP estándar (548 bytes más bytes de encabezado UDP e IP).</span><span class="sxs-lookup"><span data-stu-id="9f28e-191">Note that the server packet pool is created with packets having a payload at least as large as the standard DHCP message (548 bytes plus IP and UDP header bytes).</span></span> <span data-ttu-id="9f28e-192">Después de crear correctamente una instancia de IP para el servidor DHCP, la aplicación crea el servidor DHCP en la línea 96.</span><span class="sxs-lookup"><span data-stu-id="9f28e-192">After successfully creating an IP instance for the DHCP Server, the application creates the DHCP Server in line 96.</span></span> <span data-ttu-id="9f28e-193">A continuación, la aplicación permite que la instancia de IP del servidor esté habilitada para UDP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-193">Next, the application enables the Server IP instance to be UDP enabled.</span></span> <span data-ttu-id="9f28e-194">Antes de iniciar el servidor DHCP, se crea la lista de direcciones IP disponibles en la línea 137 mediante el servicio *nx_dhcp_create_server_ip_address_list*.</span><span class="sxs-lookup"><span data-stu-id="9f28e-194">Before starting the DHCP Server, the available IP address list is created in line 137 using the *nx_dhcp_create_server_ip_address_list* service.</span></span> <span data-ttu-id="9f28e-195">Los parámetros de configuración de red se establecen en la siguiente línea 138 con el servicio *nx_dhcp_set_interface_network_parameters*, los servicios de servidor DHCP están disponibles cuando la aplicación llama a *nx_dhcp_server_start* en la línea 141.</span><span class="sxs-lookup"><span data-stu-id="9f28e-195">The network configuration parameters are set in the following line 138 using the *nx_dhcp_set_interface_network_parameters* service, DHCP Server services become available when the application calls the *nx_dhcp_server_start* at line 141.</span></span> <span data-ttu-id="9f28e-196">La tarea de subproceso de prueba muestra el uso de la detención y el reinicio del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-196">The test thread task demonstrates the use of stopping and restarting the DHCP server.</span></span>

```c
/* This is a small demo of NetX DHCP Server for the high-performance NetX TCP/IP stack. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE       2048
#define     DEMO_SERVER_STACK_SIZE     2048
#define     SERVER_IP_ADDRESS_LIST     "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD             1000
#define     PACKET_POOL_SIZE           (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK     2048

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD          test_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_DHCP_SERVER     dhcp_server;

/* Define the counters used in the demo application... */

ULONG             state_changes;

/* Define thread prototypes. */

void     test_thread_entry(ULONG thread_input);
void     nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the test thread. */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
                pointer, TEST_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the DHCP Server packet pool. */
    status = nx_packet_pool_create(&server_pool, "NetX Main Packet Pool",
                                PACKET_PAYLOAD, pointer, PACKET_POOL_SIZE);
                                pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance. */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
                        0xFFFFFF00UL, &server_pool, nx_etherDriver_mcf5485, pointer,
                        SERVER_IP_THREAD_STACK, 1);

    pointer = pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors. */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance. */
    status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic. */
    status = nx_udp_enable(&server_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility. */
    status = nx_icmp_enable(&server_ip);

    /* Check for errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

    status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);
    status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                        NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                        IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server. */
    status = nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread. */
void     test_thread_entry(ULONG thread_input)
{

UINT     status;
UINT     keep_spinning;

    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);

    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}
```

<span data-ttu-id="9f28e-197">Figura 1.1 Ejemplo de aplicación del servidor DHCP de NetX</span><span class="sxs-lookup"><span data-stu-id="9f28e-197">Figure 1.1 Example NetX DHCP Server application</span></span>

## <a name="configuration-options"></a><span data-ttu-id="9f28e-198">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="9f28e-198">Configuration Options</span></span>

<span data-ttu-id="9f28e-199">Hay varias opciones de configuración para compilar el servidor DHCP de NetX.</span><span class="sxs-lookup"><span data-stu-id="9f28e-199">There are several configuration options for building NetX DHCP Server.</span></span> <span data-ttu-id="9f28e-200">En la lista siguiente se describe cada una de forma detallada:</span><span class="sxs-lookup"><span data-stu-id="9f28e-200">The following list describes each in detail:</span></span>  
  
- <span data-ttu-id="9f28e-201">**NX_DISABLE_ERROR_CHECKING**: esta opción quita la comprobación de errores DHCP básica.</span><span class="sxs-lookup"><span data-stu-id="9f28e-201">**NX_DISABLE_ERROR_CHECKING**: This option removes the basic DHCP error checking.</span></span> <span data-ttu-id="9f28e-202">Normalmente se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9f28e-202">It is typically used after the application is debugged.</span></span>  
- <span data-ttu-id="9f28e-203">**NX_DHCP_SERVER_THREAD_PRIORITY**: esta opción especifica la prioridad del subproceso del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-203">**NX_DHCP_SERVER_THREAD_PRIORITY**: This option specifies the priority of the DHCP Server thread.</span></span> <span data-ttu-id="9f28e-204">De forma predeterminada, este valor especifica que el subproceso DHCP se ejecuta con la prioridad 2.</span><span class="sxs-lookup"><span data-stu-id="9f28e-204">By default, this value specifies that the DHCP thread runs at priority 2.</span></span>
- <span data-ttu-id="9f28e-205">**NX_DHCP_TYPE_OF_SERVICE**: esta opción especifica el tipo de servicio necesario para las solicitudes UDP de DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-205">**NX_DHCP_TYPE_OF_SERVICE**: This option specifies the type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="9f28e-206">De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes IP normal.</span><span class="sxs-lookup"><span data-stu-id="9f28e-206">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="9f28e-207">**NX_DHCP_FRAGMENT_OPTION**: habilita los fragmentos para solicitudes UDP de DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-207">**NX_DHCP_FRAGMENT_OPTION**: Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="9f28e-208">De forma predeterminada, este valor se establece en NX_DONT_FRAGMENT para deshabilitar la fragmentación de UDP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-208">By default, this value is set to NX_DONT_FRAGMENT to disable UDP fragmenting.</span></span>
- <span data-ttu-id="9f28e-209">**NX_DHCP_TIME_TO_LIVE**: especifica el número de enrutadores que un paquete puede pasar antes de que se descarte.</span><span class="sxs-lookup"><span data-stu-id="9f28e-209">**NX_DHCP_TIME_TO_LIVE**: Specifies the number of routers the packet can pass before it is discarded.</span></span> <span data-ttu-id="9f28e-210">El valor predeterminado es 0x80.</span><span class="sxs-lookup"><span data-stu-id="9f28e-210">The default value is 0x80.</span></span>
- <span data-ttu-id="9f28e-211">**NX_DHCP_QUEUE_DEPTH**: especifica el número de paquetes que el socket del servidor DHCP conserva antes de vaciar la cola.</span><span class="sxs-lookup"><span data-stu-id="9f28e-211">**NX_DHCP_QUEUE_DEPTH** Specifies the number of packets that the DHCP Server socket keeps before flushing the queue.</span></span> <span data-ttu-id="9f28e-212">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="9f28e-212">The default value is 5.</span></span>
- <span data-ttu-id="9f28e-213">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: especifica el tiempo de espera en tics del temporizador para que el servidor DHCP de NetX espere a que se asigne un paquete de su grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="9f28e-213">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: Specifies the timeout in timer ticks for the NetX DHCP Server to wait for allocate a packet from its packet pool.</span></span> <span data-ttu-id="9f28e-214">El valor predeterminado está establecido en NX_IP_PERIODIC_RATE.</span><span class="sxs-lookup"><span data-stu-id="9f28e-214">The default value is set to NX_IP_PERIODIC_RATE.</span></span>
- <span data-ttu-id="9f28e-215">**NX_DHCP_SUBNET_MASK**: se trata de la máscara de subred con la que se debe configurar el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-215">**NX_DHCP_SUBNET_MASK**: This is the subnet mask the DHCP Client should be configured with.</span></span> <span data-ttu-id="9f28e-216">El valor predeterminado se define en 0xFFFFFF00.</span><span class="sxs-lookup"><span data-stu-id="9f28e-216">The default value is set to 0xFFFFFF00.</span></span>
- <span data-ttu-id="9f28e-217">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: es el período de tiempo de espera en tics del temporizador para que el temporizador rápido del servidor DHCP compruebe el tiempo restante de la sesión y administre las sesiones que han agotado el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="9f28e-217">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server fast timer to check on session time remaining and handle sessions that have timed out.</span></span>
- <span data-ttu-id="9f28e-218">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: es el período de tiempo de espera en tics del temporizador para que el temporizador lento del servidor DHCP compruebe el tiempo restante de la concesión de dirección IP y administre las concesiones que han agotado el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="9f28e-218">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server slow timer to check on IP address lease time remaining and handle lease that have timed out.</span></span>
- <span data-ttu-id="9f28e-219">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: este es el período de tiempo de espera en tics del temporizador que el servidor DHCP esperará para recibir el siguiente mensaje de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-219">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: This is timeout period in timer ticks the DHCP Server will wait to receive the next DHCP Client message.</span></span>
- <span data-ttu-id="9f28e-220">**NX_DHCP_DEFAULT_LEASE_TIME**: este es el tiempo de concesión de la dirección IP en segundos asignado al cliente DHCP y la base para calcular los tiempos de renovación y reenlace también asignados al cliente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-220">**NX_DHCP_DEFAULT_LEASE_TIME**: This is IP Address lease time in seconds assigned to the DHCP Client, and the basis for computing the renewal and rebind times also assigned to the Client.</span></span> <span data-ttu-id="9f28e-221">El valor predeterminado se define en 0xFFFFFFFF (infinito).</span><span class="sxs-lookup"><span data-stu-id="9f28e-221">The default value is set to 0xFFFFFFFF (infinity).</span></span>
- <span data-ttu-id="9f28e-222">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: es el tamaño de la matriz de servidores DHCP que contiene las direcciones IP disponibles para asignar al cliente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-222">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: This is size of the DHCP Server array for holding available IP addresses for assigning to the Client.</span></span> <span data-ttu-id="9f28e-223">El valor predeterminado es 20.</span><span class="sxs-lookup"><span data-stu-id="9f28e-223">The default value is 20.</span></span>
- <span data-ttu-id="9f28e-224">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: es el tamaño de la matriz de servidor DHCP para contener los registros de cliente.</span><span class="sxs-lookup"><span data-stu-id="9f28e-224">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: This is size of the DHCP Server array for holding Client records.</span></span> <span data-ttu-id="9f28e-225">El valor predeterminado es 50.</span><span class="sxs-lookup"><span data-stu-id="9f28e-225">The default value is 50.</span></span>
- <span data-ttu-id="9f28e-226">**NX_DHCP_CLIENT_OPTIONS_MAX**: es el tamaño de la matriz en la instancia del cliente DHCP para contener todas las opciones solicitadas en la lista de solicitudes de parámetros en la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="9f28e-226">**NX_DHCP_CLIENT_OPTIONS_MAX**: This is size of the array in the DHCP Client instance for holding the all the requested options in the parameter request list in the current session.</span></span> <span data-ttu-id="9f28e-227">El valor predeterminado es 12.</span><span class="sxs-lookup"><span data-stu-id="9f28e-227">The default value is 12.</span></span>
- <span data-ttu-id="9f28e-228">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: este es el búfer que contiene la lista de opciones predeterminada del servidor DHCP que proporcionar al cliente DHCP actual en la lista de solicitudes de parámetros.</span><span class="sxs-lookup"><span data-stu-id="9f28e-228">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: This is the buffer holding the DHCP Server's default list of options to supply to the current DHCP Client in the parameter request list.</span></span> <span data-ttu-id="9f28e-229">El valor predeterminado es "1 3 6".</span><span class="sxs-lookup"><span data-stu-id="9f28e-229">The default is "1 3 6."</span></span>
- <span data-ttu-id="9f28e-230">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: es el tamaño de la matriz que contiene la lista de opciones predeterminada del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="9f28e-230">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: This is the size of the array to hold the DHCP Server's default list of options.</span></span> <span data-ttu-id="9f28e-231">El valor predeterminado es 3.</span><span class="sxs-lookup"><span data-stu-id="9f28e-231">The default value is 3.</span></span>
- <span data-ttu-id="9f28e-232">**NX_DHCP_SERVER_HOSTNAME_MAX**: tamaño del búfer para contener el nombre de host del servidor.</span><span class="sxs-lookup"><span data-stu-id="9f28e-232">**NX_DHCP_SERVER_HOSTNAME_MAX**: This is size of the buffer for holding the Server host name.</span></span> <span data-ttu-id="9f28e-233">El valor predeterminado es 32.</span><span class="sxs-lookup"><span data-stu-id="9f28e-233">The default value is 32.</span></span>
- <span data-ttu-id="9f28e-234">**NX_DHCP_CLIENT_HOSTNAME_MAX**: es el tamaño del búfer que contiene el nombre de host del cliente en la sesión de cliente del servidor DHCP actual.</span><span class="sxs-lookup"><span data-stu-id="9f28e-234">**NX_DHCP_CLIENT_HOSTNAME_MAX**: This is size of the buffer for holding the Client host name in the current DHCP Server Client session.</span></span> <span data-ttu-id="9f28e-235">El valor predeterminado es 32.</span><span class="sxs-lookup"><span data-stu-id="9f28e-235">The default value is 32.</span></span>
