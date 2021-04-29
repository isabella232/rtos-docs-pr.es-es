---
title: 'Capítulo 3: Descripción de los servicios de Telnet de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios de Telnet de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814529"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a><span data-ttu-id="d8f11-103">Capítulo 3: Descripción de los servicios de Telnet de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d8f11-103">Chapter 3 - Description of Azure RTOS NetX Duo Telnet services</span></span>

<span data-ttu-id="d8f11-104">Este capítulo contiene una descripción de todos los servicios de Telnet de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="d8f11-104">This chapter contains a description of all Azure RTOS NetX Duo Telnet Services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="d8f11-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están deshabilitados por completo.</span><span class="sxs-lookup"><span data-stu-id="d8f11-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="d8f11-106">**nx_telnet_client_connect**: *conecta un cliente Telnet con una dirección IPv4.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-106">**nx_telnet_client_connect**: *Connect a Telnet Client with IPv4 address*</span></span>
- <span data-ttu-id="d8f11-107">**nxd_telnet_client_connect**: *conecta un cliente Telnet IPv6 con una dirección IPv6.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-107">**nxd_telnet_client_connect**: *Connect an IPv6 Telnet Client with IPv6 address*</span></span>
- <span data-ttu-id="d8f11-108">**nx_telnet_client_create**: *crea un cliente Telnet.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-108">**nx_telnet_client_create**: *Create a Telnet Client*</span></span>
- <span data-ttu-id="d8f11-109">**nx_telnet_client_delete**: *elimina un cliente Telnet.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-109">**nx_telnet_client_delete**: *Delete a Telnet Client*</span></span>
- <span data-ttu-id="d8f11-110">**nx_telnet_client_disconnect**: *desconecta un cliente Telnet.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-110">**nx_telnet_client_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="d8f11-111">**nx_telnet_client_packet_receive**: *recibe un paquete mediante el cliente Telnet.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-111">**nx_telnet_client_packet_receive**: *Receive packet via Telnet Client*</span></span>
- <span data-ttu-id="d8f11-112">**nx_telnet_client_packet_send**: *envía un paquete mediante el cliente Telnet.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-112">**nx_telnet_client_packet_send**: *Send packet via Telnet Client*</span></span>
- <span data-ttu-id="d8f11-113">**nx_telnet_server_create**: *crea un servidor Telnet.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-113">**nx_telnet_server_create**: *Create a Telnet Server*</span></span>
- <span data-ttu-id="d8f11-114">**nx_telnet_server_delete**: *elimina un servidor Telnet.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-114">**nx_telnet_server_delete**: *Delete a Telnet Server*</span></span>
- <span data-ttu-id="d8f11-115">**nx_telnet_server_disconnect**: *desconecta un cliente Telnet.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-115">**nx_telnet_server_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="d8f11-116">**nx_telnet_server_get_open_connection_count**: *recupera el número de conexiones abiertas.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-116">**nx_telnet_server_get_open_connection_count**: *Retrieve the number of open connections*</span></span>
- <span data-ttu-id="d8f11-117">**nx_telnet_server_packet_send**: *envía un paquete a través de una conexión de cliente.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-117">**nx_telnet_server_packet_send**: *Send packet through Client connection*</span></span>
- <span data-ttu-id="d8f11-118">**nx_telnet_server_packet_pool_set**: *establece el grupo de paquetes como grupo de paquetes del servidor Telnet.*</span><span class="sxs-lookup"><span data-stu-id="d8f11-118">**nx_telnet_server_packet_pool_set**: *Set packet pool as Telnet Server packet pool*</span></span>
- <span data-ttu-id="d8f11-119">**nx_telnet_server_start**: *inicia un servidor Telnet*</span><span class="sxs-lookup"><span data-stu-id="d8f11-119">**nx_telnet_server_start**: *Start a Telnet Server*</span></span>
- <span data-ttu-id="d8f11-120">**nx_telnet_server_stop**: *detiene un servidor Telnet*</span><span class="sxs-lookup"><span data-stu-id="d8f11-120">**nx_telnet_server_stop**: *Stop a Telnet Server*</span></span>

## <a name="nx_telnet_client_connect"></a><span data-ttu-id="d8f11-121">nx_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="d8f11-121">nx_telnet_client_connect</span></span>

<span data-ttu-id="d8f11-122">Conecta un cliente Telnet con una dirección IPv4.</span><span class="sxs-lookup"><span data-stu-id="d8f11-122">Connect a Telnet Client with IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-123">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-123">Prototype</span></span>

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8f11-124">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-124">Description</span></span>

<span data-ttu-id="d8f11-125">Este servicio intenta conectar la instancia de cliente Telnet creada anteriormente con el servidor de la dirección IP y el puerto especificados mediante una dirección IPv4 para el servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-125">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using an IPv4 address for the Telnet Server.</span></span> <span data-ttu-id="d8f11-126">En realidad, este servicio inserta la dirección IP del servidor ULONG en un bloque de control NXD_ADDRESS y establece la versión de IP en 4 antes de llamar al servicio *nxd_telnet_client_connect* que se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="d8f11-126">This service actually inserts the ULONG server IP address in an NXD_ADDRESS control block and sets the IP version to 4 before calling the *nxd_telnet_client_connect* service described below.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-127">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-127">Input Parameters</span></span>

- <span data-ttu-id="d8f11-128">**client_ptr**: puntero al bloque de control del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-128">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="d8f11-129">**server_ip**: dirección IPv4 del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-129">**server_ip**: IPv4 Address of the Telnet Server.</span></span>
- <span data-ttu-id="d8f11-130">**server_port**: puerto TCP del servidor (el servidor Telnet es el puerto 23).</span><span class="sxs-lookup"><span data-stu-id="d8f11-130">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="d8f11-131">**wait_option**: define cuánto tiempo va a esperar el servicio para la conexión del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-131">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="d8f11-132">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="d8f11-132">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="d8f11-133">**timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-133">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="d8f11-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="d8f11-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF)Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-135">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-135">Return Values</span></span>

- <span data-ttu-id="d8f11-136">**NX_SUCCESS**: (0x00) conexión correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-136">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="d8f11-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) el cliente ya está conectado.</span><span class="sxs-lookup"><span data-stu-id="d8f11-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="d8f11-138">NX_PTR_ERROR: (0x07) el puntero de cliente no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-138">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="d8f11-139">NX_IP_ADDRESS_ERROR (0x21): la dirección IP no es válida.</span><span class="sxs-lookup"><span data-stu-id="d8f11-139">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d8f11-140">NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-140">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-141">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-141">Allowed From</span></span>

<span data-ttu-id="d8f11-142">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-142">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-143">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-143">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a><span data-ttu-id="d8f11-144">nxd_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="d8f11-144">nxd_telnet_client_connect</span></span>

<span data-ttu-id="d8f11-145">Conecta un cliente Telnet con una dirección IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="d8f11-145">Connect a Telnet Client with IPv6 or IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-146">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-146">Prototype</span></span>

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8f11-147">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-147">Description</span></span>

<span data-ttu-id="d8f11-148">Este servicio intenta conectar la instancia de cliente Telnet creada anteriormente al servidor de la dirección IP y el puerto especificados mediante una dirección IPv6 del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-148">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using the Telnet Server’s IPv6 address.</span></span> <span data-ttu-id="d8f11-149">Este servicio puede tomar una dirección IPv4 o IPv6, pero debe incluirse en la variable *server_ip_address* de NXD_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="d8f11-149">This service can take an IPv4 or an IPv6 address but must be contained in the NXD_ADDRESS variable *server_ip_address.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-150">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-150">Input Parameters</span></span>

- <span data-ttu-id="d8f11-151">**client_ptr**: puntero al bloque de control del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-151">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="d8f11-152">**server_ip_address**: dirección IP del servidor.</span><span class="sxs-lookup"><span data-stu-id="d8f11-152">**server_ip_address**: IP Address of Server.</span></span>
- <span data-ttu-id="d8f11-153">**server_port**: puerto TCP del servidor (el servidor Telnet es el puerto 23).</span><span class="sxs-lookup"><span data-stu-id="d8f11-153">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="d8f11-154">**wait_option**: define cuánto tiempo va a esperar el servicio para la conexión del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-154">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="d8f11-155">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="d8f11-155">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="d8f11-156">**timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-156">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="d8f11-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="d8f11-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-158">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-158">Return Values</span></span>

- <span data-ttu-id="d8f11-159">**NX_SUCCESS**: (0x00) conexión correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-159">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="d8f11-160">**NX_TELNET_ERROR**: (0xF0) error de conexión del cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-160">**NX_TELNET_ERROR**: (0xF0) Client connect error.</span></span>
- <span data-ttu-id="d8f11-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) el cliente ya está conectado.</span><span class="sxs-lookup"><span data-stu-id="d8f11-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="d8f11-162">NX_PTR_ERROR: (0x07) el puntero de cliente no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-162">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="d8f11-163">NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-163">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="d8f11-164">NX_TELNET_INVALID_PARAMETER: (0xF5) entrada que no es de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="d8f11-164">NX_TELNET_INVALID_PARAMETER: (0xF5) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-165">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-165">Allowed From</span></span>

<span data-ttu-id="d8f11-166">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-166">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-167">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-167">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a><span data-ttu-id="d8f11-168">nx_telnet_client_create</span><span class="sxs-lookup"><span data-stu-id="d8f11-168">nx_telnet_client_create</span></span>

<span data-ttu-id="d8f11-169">Crear un cliente Telnet</span><span class="sxs-lookup"><span data-stu-id="d8f11-169">Create a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-170">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-170">Prototype</span></span>

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="d8f11-171">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-171">Description</span></span>

<span data-ttu-id="d8f11-172">Este servicio crea una instancia del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-172">This service creates a Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-173">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-173">Input Parameters</span></span>

- <span data-ttu-id="d8f11-174">**client_ptr**: puntero al bloque de control del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-174">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="d8f11-175">**client_name**: nombre de la instancia del cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-175">**client_name**: Name of Client instance.</span></span>
- <span data-ttu-id="d8f11-176">**ip_ptr**: puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="d8f11-176">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="d8f11-177">**window_size**: tamaño de la ventana de recepción TCP para este cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-177">**window_size**: Size of TCP receive window for this Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-178">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-178">Return Values</span></span>

- <span data-ttu-id="d8f11-179">**NX_SUCCESS**: (0x00) creación correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-179">**NX_SUCCESS**: (0x00) Successful Client create.</span></span>
- <span data-ttu-id="d8f11-180">**NX_TELNET_ERROR**: (0xF0) error de creación del socket.</span><span class="sxs-lookup"><span data-stu-id="d8f11-180">**NX_TELNET_ERROR**: (0xF0) Socket create error.</span></span>
- <span data-ttu-id="d8f11-181">NX_PTR_ERROR: (0x07) el puntero de IP o el cliente no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-181">NX_PTR_ERROR: (0x07) Invalid Client or IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-182">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-182">Allowed From</span></span>

<span data-ttu-id="d8f11-183">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-183">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-184">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-184">Example</span></span>

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a><span data-ttu-id="d8f11-185">nx_telnet_client_delete</span><span class="sxs-lookup"><span data-stu-id="d8f11-185">nx_telnet_client_delete</span></span>

<span data-ttu-id="d8f11-186">Elimina un cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-186">Delete a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-187">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-187">Prototype</span></span>

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="d8f11-188">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-188">Description</span></span>

<span data-ttu-id="d8f11-189">Este servicio elimina una instancia de cliente Telnet creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-189">This service deletes a previously created Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-190">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-190">Input Parameters</span></span>

- <span data-ttu-id="d8f11-191">**client_ptr**: puntero al bloque de control del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-191">**client_ptr**: Pointer to Telnet Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-192">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-192">Return Values</span></span>

- <span data-ttu-id="d8f11-193">**NX_SUCCESS**: (0x00) eliminación correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-193">**NX_SUCCESS**: (0x00) Successful Client delete.</span></span>
- <span data-ttu-id="d8f11-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) el cliente aún está conectado.</span><span class="sxs-lookup"><span data-stu-id="d8f11-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client still connected.</span></span>
- <span data-ttu-id="d8f11-195">NX_PTR_ERROR: (0x07) el puntero de cliente no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-195">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="d8f11-196">NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-196">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-197">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-197">Allowed From</span></span>

<span data-ttu-id="d8f11-198">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-199">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-199">Example</span></span>

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a><span data-ttu-id="d8f11-200">nx_telnet_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="d8f11-200">nx_telnet_client_disconnect</span></span>

<span data-ttu-id="d8f11-201">Desconecta un cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-201">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-202">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-202">Prototype</span></span>

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8f11-203">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-203">Description</span></span>

<span data-ttu-id="d8f11-204">Este servicio desconecta una instancia de cliente Telnet conectada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-204">This service disconnects a previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-205">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-205">Input Parameters</span></span>

- <span data-ttu-id="d8f11-206">**client_ptr**: puntero al bloque de control del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-206">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="d8f11-207">**wait_option**: define cuánto tiempo va a esperar el servicio la desconexión del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-207">**wait_option**: Defines how long the service will wait for the Telnet Client disconnect.</span></span> <span data-ttu-id="d8f11-208">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="d8f11-208">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="d8f11-209">**timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-209">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="d8f11-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="d8f11-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-211">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-211">Return Values</span></span>

- <span data-ttu-id="d8f11-212">**NX_SUCCESS**: (0x00) desconexión correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-212">**NX_SUCCESS**: (0x00) Successful Client disconnect.</span></span>
- <span data-ttu-id="d8f11-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) el cliente no está conectado.</span><span class="sxs-lookup"><span data-stu-id="d8f11-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) Client not connected.</span></span>
- <span data-ttu-id="d8f11-214">NX_PTR_ERROR: (0x07) el puntero de cliente no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-214">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="d8f11-215">NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="d8f11-216">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-216">Allowed From</span></span>

<span data-ttu-id="d8f11-217">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-218">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-218">Example</span></span>

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a><span data-ttu-id="d8f11-219">nx_telnet_client_packet_receive</span><span class="sxs-lookup"><span data-stu-id="d8f11-219">nx_telnet_client_packet_receive</span></span>

<span data-ttu-id="d8f11-220">Recibe un paquete mediante el cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-220">Receive packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-221">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-221">Prototype</span></span>

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8f11-222">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-222">Description</span></span>

<span data-ttu-id="d8f11-223">Este servicio recibe un paquete de la instancia de cliente Telnet conectada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-223">This service receives a packet from the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-224">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-224">Input Parameters</span></span>

- <span data-ttu-id="d8f11-225">**client_ptr**: puntero al bloque de control del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-225">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="d8f11-226">**packet_ptr**: puntero al destino del paquete recibido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-226">**packet_ptr**: Pointer to the destination for the received packet.</span></span>
- <span data-ttu-id="d8f11-227">**wait_option**: define cuánto tiempo va a esperar el servicio para recibir un paquete del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-227">**wait_option**: Defines how long the service will wait for the Telnet Client packet receive.</span></span> <span data-ttu-id="d8f11-228">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="d8f11-228">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="d8f11-229">**timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-229">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="d8f11-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="d8f11-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-231">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-231">Return Values</span></span>

- <span data-ttu-id="d8f11-232">**NX_SUCCESS**: (0x00) recepción correcta de paquetes del cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-232">**NX_SUCCESS**: (0x00) Successful Client packet receive.</span></span>
- <span data-ttu-id="d8f11-233">NX_PTR_ERROR: (0x07) la entrada del puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="d8f11-233">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="d8f11-234">NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-234">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-235">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-235">Allowed From</span></span>

<span data-ttu-id="d8f11-236">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-236">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-237">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-237">Example</span></span>

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a><span data-ttu-id="d8f11-238">nx_telnet_client_packet_send</span><span class="sxs-lookup"><span data-stu-id="d8f11-238">nx_telnet_client_packet_send</span></span>

<span data-ttu-id="d8f11-239">Envía un paquete mediante el cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-239">Send packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-240">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-240">Prototype</span></span>

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8f11-241">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-241">Description</span></span>

<span data-ttu-id="d8f11-242">Este servicio envía un paquete mediante la instancia de cliente Telnet conectada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-242">This service sends a packet through the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-243">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-243">Input Parameters</span></span>

- <span data-ttu-id="d8f11-244">**client_ptr**: puntero al bloque de control del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-244">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="d8f11-245">**packet_ptr**: puntero al paquete que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="d8f11-245">**packet_ptr**: Pointer to the packet to send.</span></span>
- <span data-ttu-id="d8f11-246">**wait_option**: define cuánto tiempo va a esperar el servicio para enviar un paquete del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-246">**wait_option**: Defines how long the service will wait for the Telnet Client packet send.</span></span> <span data-ttu-id="d8f11-247">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="d8f11-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="d8f11-248">**timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-248">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="d8f11-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="d8f11-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-250">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-250">Return Values</span></span>

- <span data-ttu-id="d8f11-251">**NX_SUCCESS**: (0x00) envío correcto de paquetes.</span><span class="sxs-lookup"><span data-stu-id="d8f11-251">**NX_SUCCESS**: (0x00) Successful Client packet send.</span></span>
- <span data-ttu-id="d8f11-252">**NX_TELNET_ERROR**: (0xF0) error de envío de paquete; el autor de la llamada es responsable de liberar el paquete.</span><span class="sxs-lookup"><span data-stu-id="d8f11-252">**NX_TELNET_ERROR**: (0xF0) Send packet failed – caller is responsible for releasing the packet.</span></span>
- <span data-ttu-id="d8f11-253">NX_PTR_ERROR: (0x07) la entrada del puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="d8f11-253">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="d8f11-254">NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-254">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-255">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-255">Allowed From</span></span>

<span data-ttu-id="d8f11-256">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-256">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-257">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-257">Example</span></span>

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a><span data-ttu-id="d8f11-258">nx_telnet_server_create</span><span class="sxs-lookup"><span data-stu-id="d8f11-258">nx_telnet_server_create</span></span>

<span data-ttu-id="d8f11-259">Crea un servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-259">Create a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-260">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-260">Prototype</span></span>

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a><span data-ttu-id="d8f11-261">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-261">Description</span></span>

<span data-ttu-id="d8f11-262">Este servicio crea una instancia de un servidor Telnet en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="d8f11-262">This service creates a Telnet Server instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-263">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-263">Input Parameters</span></span>

- <span data-ttu-id="d8f11-264">**server_ptr**: puntero al bloque de control del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-264">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="d8f11-265">**server_name**: nombre de la instancia del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-265">**server_name**: Name of Telnet Server instance.</span></span>
- <span data-ttu-id="d8f11-266">**ip_ptr**: puntero a la instancia de IP asociada.</span><span class="sxs-lookup"><span data-stu-id="d8f11-266">**ip_ptr**: Pointer to associated IP instance.</span></span>
- <span data-ttu-id="d8f11-267">**stack_ptr**: puntero a la pila del subproceso del servidor interno.</span><span class="sxs-lookup"><span data-stu-id="d8f11-267">**stack_ptr**: Pointer to stack for the internal Server thread.</span></span>
- <span data-ttu-id="d8f11-268">**stack_size**: tamaño de la pila, en bytes.</span><span class="sxs-lookup"><span data-stu-id="d8f11-268">**sack_size**: Size of the stack, in bytes.</span></span>
- <span data-ttu-id="d8f11-269">**new_connection**: puntero de función de rutina de la devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d8f11-269">**new_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="d8f11-270">Se llama a esta rutina siempre que el servidor detecta una nueva solicitud de conexión del cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-270">This routine is called whenever a new Telnet Client connection request is detected by the Server.</span></span>
- <span data-ttu-id="d8f11-271">**receive_data**: puntero de función de rutina de la devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d8f11-271">**receive_data**: Application callback routine function pointer.</span></span> <span data-ttu-id="d8f11-272">Se llama a esta rutina siempre que haya nuevos datos del cliente Telnet en la conexión.</span><span class="sxs-lookup"><span data-stu-id="d8f11-272">This routine is called whenever a new Telnet Client data is present on the connection.</span></span> <span data-ttu-id="d8f11-273">Esta rutina es responsable de liberar el paquete.</span><span class="sxs-lookup"><span data-stu-id="d8f11-273">This routine is responsible for releasing the packet.</span></span>
- <span data-ttu-id="d8f11-274">**end_connection**: puntero de función de rutina de la devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d8f11-274">**end_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="d8f11-275">Se llama a esta rutina cuando el cliente desconecta una conexión de cliente Telnet o se agota el tiempo de espera de la conexión de cliente ("tiempo de espera de la actividad").</span><span class="sxs-lookup"><span data-stu-id="d8f11-275">This routine is called whenever a Telnet Client connection is disconnected by the Client or the Client connection times out (“activity timeout” expires).</span></span> <span data-ttu-id="d8f11-276">El servidor también se puede desconectar mediante el servicio *nx_telnet_server_disconnect* que se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="d8f11-276">The Server can also disconnect via the *nx_telnet_server_disconnect* service described below.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-277">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-277">Return Values</span></span>

- <span data-ttu-id="d8f11-278">**NX_SUCCESS**: (0x00) el servidor se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-278">**NX_SUCCESS**: (0x00) Successful Server create.</span></span>
- <span data-ttu-id="d8f11-279">NX_PTR_ERROR: (0x07) el servidor, la dirección IP, la pila o los punteros de devolución de llamada de aplicación no son válidos.</span><span class="sxs-lookup"><span data-stu-id="d8f11-279">NX_PTR_ERROR: (0x07) Invalid Server, IP, stack, or application callback pointers.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-280">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-280">Allowed From</span></span>

<span data-ttu-id="d8f11-281">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-281">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-282">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-282">Example</span></span>

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a><span data-ttu-id="d8f11-283">nx_telnet_server_delete</span><span class="sxs-lookup"><span data-stu-id="d8f11-283">nx_telnet_server_delete</span></span>

<span data-ttu-id="d8f11-284">Elimina un servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-284">Delete a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-285">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-285">Prototype</span></span>

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="d8f11-286">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-286">Description</span></span>

<span data-ttu-id="d8f11-287">Este servicio elimina una instancia de servidor Telnet creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-287">This service deletes a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-288">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-288">Input Parameters</span></span>

- <span data-ttu-id="d8f11-289">**server_ptr**: puntero al bloque de control del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-289">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-290">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-290">Return Values</span></span>

- <span data-ttu-id="d8f11-291">**NX_SUCCESS**: (0x00) el servidor se eliminó correctamente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-291">**NX_SUCCESS**: (0x00) Successful Server delete.</span></span>
- <span data-ttu-id="d8f11-292">NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-292">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="d8f11-293">NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-293">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-294">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-294">Allowed From</span></span>

<span data-ttu-id="d8f11-295">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-295">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-296">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-296">Example</span></span>

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a><span data-ttu-id="d8f11-297">nx_telnet_server_disconnect</span><span class="sxs-lookup"><span data-stu-id="d8f11-297">nx_telnet_server_disconnect</span></span>

<span data-ttu-id="d8f11-298">Desconecta un cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-298">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-299">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-299">Prototype</span></span>

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a><span data-ttu-id="d8f11-300">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-300">Description</span></span>

<span data-ttu-id="d8f11-301">Este servicio desconecta un cliente conectado previamente en esta instancia del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-301">This service disconnects a previously connected Client on this Telnet Server instance.</span></span> <span data-ttu-id="d8f11-302">Normalmente, se llama a esta rutina desde la función de devolución de llamada de recepción de datos de la aplicación en respuesta a una condición detectada en los datos recibidos.</span><span class="sxs-lookup"><span data-stu-id="d8f11-302">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-303">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-303">Input Parameters</span></span>

- <span data-ttu-id="d8f11-304">**server_ptr**: puntero al bloque de control del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-304">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="d8f11-305">**logical_connection**: conexión lógica correspondiente a la conexión de cliente en este servidor.</span><span class="sxs-lookup"><span data-stu-id="d8f11-305">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="d8f11-306">El intervalo de valores válidos es de 0 a NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="d8f11-306">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-307">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-307">Return Values</span></span>

- <span data-ttu-id="d8f11-308">**NX_SUCCESS**: (0x00) el servidor se desconectó correctamente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-308">**NX_SUCCESS**: (0x00) Successful Server disconnect.</span></span>
- <span data-ttu-id="d8f11-309">**NX_TELNET_ERROR**: (0xF0) error al desconectar el servidor.</span><span class="sxs-lookup"><span data-stu-id="d8f11-309">**NX_TELNET_ERROR**: (0xF0) Server disconnect failed.</span></span>
- <span data-ttu-id="d8f11-310">NX_OPTION_ERROR: (0x0A) la conexión lógica no es válida.</span><span class="sxs-lookup"><span data-stu-id="d8f11-310">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="d8f11-311">NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-311">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="d8f11-312">NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-312">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-313">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-313">Allowed From</span></span>

<span data-ttu-id="d8f11-314">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-314">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-315">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-315">Example</span></span>

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a><span data-ttu-id="d8f11-316">nx_telnet_server_get_open_connection_count</span><span class="sxs-lookup"><span data-stu-id="d8f11-316">nx_telnet_server_get_open_connection_count</span></span>

<span data-ttu-id="d8f11-317">Devuelve el número de conexiones abiertas actualmente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-317">Return number of currently open connections</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-318">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-318">Prototype</span></span>

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a><span data-ttu-id="d8f11-319">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-319">Description</span></span>

<span data-ttu-id="d8f11-320">Este servicio devuelve el número de clientes de Telnet conectados actualmente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-320">This service returns the number of currently connected Telnet Clients.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-321">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-321">Input Parameters</span></span>

- <span data-ttu-id="d8f11-322">**server_ptr**: puntero al bloque de control del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-322">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="d8f11-323">**Connection_count**: puntero a la memoria para almacenar el número de conexiones</span><span class="sxs-lookup"><span data-stu-id="d8f11-323">**Connection_count**: Pointer to memory to store connection count</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-324">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-324">Return Values</span></span>

- <span data-ttu-id="d8f11-325">**NX_SUCCESS**: (0x00) la operación finalizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-325">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="d8f11-326">NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-326">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="d8f11-327">NX_CALLER_ERROR: (0x11) el autor de llamada de este servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-327">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-328">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-328">Allowed From</span></span>

<span data-ttu-id="d8f11-329">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-330">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-330">Example</span></span>

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a><span data-ttu-id="d8f11-331">nx_telnet_server_packet_send</span><span class="sxs-lookup"><span data-stu-id="d8f11-331">nx_telnet_server_packet_send</span></span>

<span data-ttu-id="d8f11-332">Envía un paquete a través de la conexión de cliente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-332">Send packet through Client connection</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-333">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-333">Prototype</span></span>

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8f11-334">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-334">Description</span></span>

<span data-ttu-id="d8f11-335">Este servicio envía un paquete a la conexión de cliente en esta instancia del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-335">This service sends a packet to the Client connection on this Telnet Server instance.</span></span> <span data-ttu-id="d8f11-336">Normalmente, se llama a esta rutina desde la función de devolución de llamada de recepción de datos de la aplicación en respuesta a una condición detectada en los datos recibidos.</span><span class="sxs-lookup"><span data-stu-id="d8f11-336">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-337">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-337">Input Parameters</span></span>

- <span data-ttu-id="d8f11-338">**server_ptr**: puntero al bloque de control del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-338">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="d8f11-339">**logical_connection**: conexión lógica correspondiente a la conexión de cliente en este servidor.</span><span class="sxs-lookup"><span data-stu-id="d8f11-339">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="d8f11-340">El intervalo de valores válidos es de 0 a NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="d8f11-340">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>
- <span data-ttu-id="d8f11-341">**packet_ptr**: puntero al paquete recibido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-341">**packet_ptr**: Pointer to the received packet.</span></span>
- <span data-ttu-id="d8f11-342">**wait_option**: define cuánto tiempo va a esperar el servicio para enviar un paquete del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-342">**wait_option**: Defines how long the service will wait for the Telnet Server packet send.</span></span> <span data-ttu-id="d8f11-343">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="d8f11-343">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="d8f11-344">**timeout value**: (de 0x00000001 a 0xFFFFFFFE) al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que debe permanecer suspendido a la espera de respuesta por parte del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-344">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="d8f11-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor Telnet responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="d8f11-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span> 

### <a name="return-values"></a><span data-ttu-id="d8f11-346">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-346">Return Values</span></span>

- <span data-ttu-id="d8f11-347">**NX_SUCCESS**: (0x00) el paquete se envió correctamente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-347">**NX_SUCCESS**: (0x00) Successful packet send.</span></span>
- <span data-ttu-id="d8f11-348">**NX_TELNET_FAILED**: (0xF2) error al enviar el socket TCP.</span><span class="sxs-lookup"><span data-stu-id="d8f11-348">**NX_TELNET_FAILED**: (0xF2) TCP socket send failed.</span></span>
- <span data-ttu-id="d8f11-349">NX_OPTION_ERROR: (0x0A) la conexión lógica no es válida.</span><span class="sxs-lookup"><span data-stu-id="d8f11-349">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="d8f11-350">NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-350">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="d8f11-351">NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-351">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-352">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-352">Allowed From</span></span>

<span data-ttu-id="d8f11-353">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-354">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-354">Example</span></span>

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a><span data-ttu-id="d8f11-355">nx_telnet_server_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="d8f11-355">nx_telnet_server_packet_pool_set</span></span>

<span data-ttu-id="d8f11-356">Establece el grupo de paquetes creado anteriormente como grupo de servidores Telnet</span><span class="sxs-lookup"><span data-stu-id="d8f11-356">Set previously created packet pool as Telnet Server pool</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-357">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-357">Prototype</span></span>

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a><span data-ttu-id="d8f11-358">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-358">Description</span></span>

<span data-ttu-id="d8f11-359">Este servicio establece un grupo de paquetes creado anteriormente como el grupo de paquetes del servidor Telnet si se define NX_TELNET_SERVER_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="d8f11-359">This service sets a previously created packet pool as the Telnet Server packet pool if NX_TELNET_SERVER_USER_CREATE_PACKET_POOL is defined.</span></span> <span data-ttu-id="d8f11-360">También requiere que NX_TELNET_SERVER_OPTION_DISABLE no se defina de modo que el servidor Telnet necesite un grupo de paquetes para transmitir opciones de Telnet a los clientes Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-360">It also requires that NX_TELNET_SERVER_OPTION_DISABLE not be defined such that the Telnet Server needs a packet pool to transmit Telnet options to Telnet clients.</span></span>

<span data-ttu-id="d8f11-361">Esto permite que las aplicaciones creen el grupo de paquetes en una memoria distinta (por ejemplo, sin memoria caché) a la pila del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-361">This permits applications to create the packet pool in different memory e.g. no cache memory, than the Telnet Server stack.</span></span> <span data-ttu-id="d8f11-362">Tenga en cuenta que esta función no comprueba si el grupo de paquetes del servidor Telnet ya está establecido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-362">Note that if this function does not check if the Telnet Server packet pool is already set.</span></span> <span data-ttu-id="d8f11-363">Si se llama en un puntero del grupo de paquetes del servidor Telnet que no tenga un valor null, lo sobrescribirá y reemplazará el grupo de paquetes existente al que señala el puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="d8f11-363">If it is called on a non null Telnet Server packet pool pointer, it will overwrite it and replace the existing packet pool with packet pool pointed to by the input pointer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-364">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-364">Input Parameters</span></span>

- <span data-ttu-id="d8f11-365">**server_ptr**: puntero al bloque de control del servidor Telnet</span><span class="sxs-lookup"><span data-stu-id="d8f11-365">**server_ptr**: Pointer to Telnet Server control block</span></span>
- <span data-ttu-id="d8f11-366">**packet_pool_ptr**: puntero al grupo de paquetes creado previamente</span><span class="sxs-lookup"><span data-stu-id="d8f11-366">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-367">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-367">Return Values</span></span>

- <span data-ttu-id="d8f11-368">**NX_SUCCESS**: (0x00) el grupo se estableció correctamente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-368">**NX_SUCCESS**: (0x00) Successfully set pool.</span></span>
- <span data-ttu-id="d8f11-369">NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-369">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-370">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-370">Allowed From</span></span>

<span data-ttu-id="d8f11-371">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-371">Init, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-372">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-372">Example</span></span>

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a><span data-ttu-id="d8f11-373">nx_telnet_server_start</span><span class="sxs-lookup"><span data-stu-id="d8f11-373">nx_telnet_server_start</span></span>

<span data-ttu-id="d8f11-374">Inicia un servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-374">Start a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-375">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-375">Prototype</span></span>

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="d8f11-376">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-376">Description</span></span>

<span data-ttu-id="d8f11-377">Este servicio inicia una instancia de servidor Telnet creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-377">This service starts a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-378">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-378">Input Parameters</span></span>

- <span data-ttu-id="d8f11-379">**server_ptr**: puntero al bloque de control del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-379">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-380">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-380">Return Values</span></span>

- <span data-ttu-id="d8f11-381">**NX_SUCCESS**: (0x00) iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-381">**NX_SUCCESS**: (0x00) Successfully started.</span></span>
- <span data-ttu-id="d8f11-382">**NX_TELNET_NO_PACKET_POOL**: (0XF6) no hay ningún grupo de paquetes establecido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) No packet pool set</span></span>
- <span data-ttu-id="d8f11-383">NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-383">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-384">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-384">Allowed From</span></span>

<span data-ttu-id="d8f11-385">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-385">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-386">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-386">Example</span></span>

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a><span data-ttu-id="d8f11-387">nx_telnet_server_stop</span><span class="sxs-lookup"><span data-stu-id="d8f11-387">nx_telnet_server_stop</span></span>

<span data-ttu-id="d8f11-388">Detiene un servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-388">Stop a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d8f11-389">Prototipo</span><span class="sxs-lookup"><span data-stu-id="d8f11-389">Prototype</span></span>

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="d8f11-390">Descripción</span><span class="sxs-lookup"><span data-stu-id="d8f11-390">Description</span></span>

<span data-ttu-id="d8f11-391">Este servicio detiene una instancia de servidor Telnet iniciada y creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-391">This service stops a previously created and started Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d8f11-392">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="d8f11-392">Input Parameters</span></span>

- <span data-ttu-id="d8f11-393">**server_ptr**: puntero al bloque de control del servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="d8f11-393">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8f11-394">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="d8f11-394">Return Values</span></span>

- <span data-ttu-id="d8f11-395">**NX_SUCCESS**: (0x00) se detuvo correctamente.</span><span class="sxs-lookup"><span data-stu-id="d8f11-395">**NX_SUCCESS**: (0x00) Successfully stopped</span></span>
- <span data-ttu-id="d8f11-396">NX_PTR_ERROR: (0x07) el puntero de servidor no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-396">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="d8f11-397">NX_CALLER_ERROR: (0x11) el autor de llamada del servicio no es válido.</span><span class="sxs-lookup"><span data-stu-id="d8f11-397">NX_CALLER_ERROR: (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8f11-398">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="d8f11-398">Allowed From</span></span>

<span data-ttu-id="d8f11-399">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="d8f11-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8f11-400">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d8f11-400">Example</span></span>

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```