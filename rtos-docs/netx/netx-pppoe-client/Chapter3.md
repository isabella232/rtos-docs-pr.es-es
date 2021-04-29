---
title: 'Capítulo 3: Descripción de los servicios del cliente PPPoE de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios del cliente PPPoE de Azure RTOS NetX (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814446"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a><span data-ttu-id="c6c4c-103">Capítulo 3: Descripción de los servicios del cliente PPPoE de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="c6c4c-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Client Services</span></span>

<span data-ttu-id="c6c4c-104">Este capítulo contiene una descripción de todos los servicios del cliente PPPoE de Azure RTOS NetX (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-104">This chapter contains a description of all Azure RTOS NetX PPPoE Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="c6c4c-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="c6c4c-106">**nx_pppoe_client_create** *Crear una instancia de cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-106">**nx_pppoe_client_create** *Create a PPPoE Client instance*</span></span>
- <span data-ttu-id="c6c4c-107">**nx_pppoe_client_delete** *Eliminar una instancia de cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-107">**nx_pppoe_client_delete** *Delete a PPPoE Client instance*</span></span>
- <span data-ttu-id="c6c4c-108">**nx_pppoe_client_host_uniq_set** *Establecer el host único para el cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-108">**nx_pppoe_client_host_uniq_set** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="c6c4c-109">**nx_pppoe_client_host_uniq_set_extended** *Establecer el host único para el cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-109">**nx_pppoe_client_host_uniq_set_extended** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="c6c4c-110">**nx_pppoe_client_service_name_set** *Establecer el nombre del servicio para el cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-110">**nx_pppoe_client_service_name_set** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="c6c4c-111">**nx_pppoe_client_service_name_set_extended** *Establecer el nombre del servicio para el cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-111">**nx_pppoe_client_service_name_set_extended** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="c6c4c-112">**nx_pppoe_client_session_connect** *Conectar la sesión de cliente PPPoE al servidor de PPPoE*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-112">**nx_pppoe_client_session_connect** *Connect PPPoE Client session to PPPoE Server*</span></span>
- <span data-ttu-id="c6c4c-113">**nx_pppoe_client_session_packet_send** *Enviar paquete de sesión de PPPoE*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-113">**nx_pppoe_client_session_packet_send** *Send PPPoE session packet*</span></span>
- <span data-ttu-id="c6c4c-114">**nx_pppoe_client_session_terminate** *Finalizar la sesión de PPPoE*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-114">**nx_pppoe_client_session_terminate** *Terminate the PPPoE session*</span></span>
- <span data-ttu-id="c6c4c-115">**nx_pppoe_client_session_get** *Obtener el inf de sesión de PPPoE especificado*</span><span class="sxs-lookup"><span data-stu-id="c6c4c-115">**nx_pppoe_client_session_get** *Get the specified PPPoE session inf*</span></span>

## <a name="nx_pppoe_client_create"></a><span data-ttu-id="c6c4c-116">nx_pppoe_client_create</span><span class="sxs-lookup"><span data-stu-id="c6c4c-116">nx_pppoe_client_create</span></span>

<span data-ttu-id="c6c4c-117">Crear una instancia de cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="c6c4c-117">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-118">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-118">Prototype</span></span>

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="c6c4c-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-119">Description</span></span>

<span data-ttu-id="c6c4c-120">Este servicio crea una instancia del cliente PPPoE con el controlador de vínculo proporcionado por el usuario para la instancia de IP de NetX especificada.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-120">This service creates a PPPoE Client instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="c6c4c-121">Si el controlador de vínculo no se ha inicializado y está habilitado, el software del cliente PPPoE es responsable de inicializar el controlador de vínculo.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-121">If link driver has not been initialized, and enabled, PPPoE Client software is responsible initializing the link driver.</span></span>

<span data-ttu-id="c6c4c-122">Además, la aplicación debe proporcionar un grupo de paquetes creado previamente para la instancia de IP que se va a utilizar para la asignación interna de paquetes.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-122">In addition, the application must supply a previously created packet pool for the PPPoE Client instance to use for internal packet allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-123">Por lo general, es una buena idea crear el subproceso de IP de NetX con una prioridad más alta que la de los subprocesos del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-123">Generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Client thread priority.</span></span> <span data-ttu-id="c6c4c-124">Consulte el servicio *nx_ip_create* para obtener más información sobre cómo especificar la prioridad del subproceso de IP.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-124">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-125">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-125">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-126">**pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-126">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="c6c4c-127">**name** Nombre de esta instancia de cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-127">**name** Name of this PPPoE Client instance.</span></span>
 - <span data-ttu-id="c6c4c-128">**ip_ptr** Puntero al bloque de control de la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-128">**ip_ptr** Pointer to control block for IP instance.</span></span>
 - <span data-ttu-id="c6c4c-129">**interface_index** Índice de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-129">**interface_index** Interface index.</span></span>
 - <span data-ttu-id="c6c4c-130">**pool_ptr** Puntero al grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-130">**pool_ptr** Pointer to packet pool.</span></span>
 - <span data-ttu-id="c6c4c-131">**stack_ptr** Puntero al inicio del área de la pila del subproceso del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-131">**stack_ptr** Pointer to start of PPPoE Client thread’s stack area.</span></span>
 - <span data-ttu-id="c6c4c-132">**stack_size** Tamaño en bytes de la pila del subproceso.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-132">**stack_size** Size in bytes in the thread’s stack.</span></span>
 - <span data-ttu-id="c6c4c-133">**priority** Prioridad de los subprocesos de cliente PPPoE internos (1-31).</span><span class="sxs-lookup"><span data-stu-id="c6c4c-133">**priority** Priority of internal PPPoE Client threads (1-31).</span></span>
 - <span data-ttu-id="c6c4c-134">**pppoe_link_driver** Controlador del vínculo proporcionado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-134">**pppoe_link_driver** User supplied link driver.</span></span>
 - <span data-ttu-id="c6c4c-135">**pppoe_packet_receive** Función de recepción de paquetes proporcionada por el usuario.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-135">**pppoe_packet_receive** User supplied packet receive function.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-136">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-136">Return Values</span></span>

 - <span data-ttu-id="c6c4c-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Creación correcta del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client create.</span></span>
 - <span data-ttu-id="c6c4c-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de pila, grupo de paquetes, IP o cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client, IP, packet pool, or stack pointer.</span></span>
 - <span data-ttu-id="c6c4c-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Interfaz no válida.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Invalid interface.</span></span>
 - <span data-ttu-id="c6c4c-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Tamaño de carga no válido del grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid payload size of packet pool.</span></span>
 - <span data-ttu-id="c6c4c-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Tamaño de memoria no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Invalid memory size.</span></span>
 - <span data-ttu-id="c6c4c-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Prioridad no válida del subproceso del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Invalid priority of PPPoE Client thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-143">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-143">Allowed From</span></span>

<span data-ttu-id="c6c4c-144">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-145">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-145">Example</span></span>

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a><span data-ttu-id="c6c4c-146">nx_pppoe_client_delete</span><span class="sxs-lookup"><span data-stu-id="c6c4c-146">nx_pppoe_client_delete</span></span>

<span data-ttu-id="c6c4c-147">Eliminar una instancia de cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="c6c4c-147">Delete a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-148">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-148">Prototype</span></span>

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="c6c4c-149">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-149">Description</span></span>

<span data-ttu-id="c6c4c-150">Este servicio elimina la instancia del cliente PPPoE creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-150">This service deletes the previously created PPPoE Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-151">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-151">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-152">**pppoe_client_ptr** Puntero al bloque de control de cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-152">**pppoe_client_ptr** Pointer to PPPoE Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-153">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-153">Return Values</span></span>

 - <span data-ttu-id="c6c4c-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Eliminación correcta del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client delete.</span></span>
 - <span data-ttu-id="c6c4c-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-156">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-156">Allowed From</span></span>

<span data-ttu-id="c6c4c-157">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-158">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-158">Example</span></span>

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a><span data-ttu-id="c6c4c-159">nx_pppoe_client_host_uniq_set</span><span class="sxs-lookup"><span data-stu-id="c6c4c-159">nx_pppoe_client_host_uniq_set</span></span>

<span data-ttu-id="c6c4c-160">Establecer host único de cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="c6c4c-160">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-161">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-161">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a><span data-ttu-id="c6c4c-162">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-162">Description</span></span>

<span data-ttu-id="c6c4c-163">Este servicio establece un host de cliente PPPoE único.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-163">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="c6c4c-164">Un host usa Host-Uniq para asociar de forma única un concentrador de acceso a una solicitud de host determinada.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-164">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="c6c4c-165">Pueden ser datos binarios de cualquier valor y longitud que elija el host.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-165">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-166">El host único debe ser una cadena terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-166">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-167">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-167">This service is deprecated.</span></span> <span data-ttu-id="c6c4c-168">Se recomienda a los desarrolladores que migren a *nx_pppoe_client_host_uniq_set_extended()* .</span><span class="sxs-lookup"><span data-stu-id="c6c4c-168">Developers are encouraged to migrate to *nx_pppoe_client_host_uniq_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-169">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-169">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-170">**pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-170">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="c6c4c-171">**host_uniq** Puntero a un host único.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-171">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="c6c4c-172">El host único debe ser una cadena terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-172">Host unique must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-173">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-173">Return Values</span></span>

 - <span data-ttu-id="c6c4c-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Configuración correcta del host único del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="c6c4c-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-176">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-176">Allowed From</span></span>

<span data-ttu-id="c6c4c-177">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-178">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-178">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a><span data-ttu-id="c6c4c-179">nx_pppoe_client_host_uniq_set_extended</span><span class="sxs-lookup"><span data-stu-id="c6c4c-179">nx_pppoe_client_host_uniq_set_extended</span></span>

<span data-ttu-id="c6c4c-180">Establecer host único de cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="c6c4c-180">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-181">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-181">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a><span data-ttu-id="c6c4c-182">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-182">Description</span></span>

<span data-ttu-id="c6c4c-183">Este servicio establece un host de cliente PPPoE único.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-183">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="c6c4c-184">Un host usa Host-Uniq para asociar de forma única un concentrador de acceso a una solicitud de host determinada.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-184">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="c6c4c-185">Pueden ser datos binarios de cualquier valor y longitud que elija el host.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-185">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-186">El host único debe ser una cadena terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-186">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-187">Este servicio reemplaza a *nx_pppoe_client_host_uniq_set()* .</span><span class="sxs-lookup"><span data-stu-id="c6c4c-187">This service replaces *nx_pppoe_client_host_uniq_set()*.</span></span> <span data-ttu-id="c6c4c-188">Esta versión proporciona información de longitud adicional al servicio.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-188">This version supplies additional length information to the service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-189">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-189">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-190">**pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-190">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="c6c4c-191">**host_uniq** Puntero a un host único.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-191">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="c6c4c-192">El host único debe ser una cadena terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-192">Host unique must be Null-terminated string.</span></span>
 - <span data-ttu-id="c6c4c-193">**host_uniq_length** Longitud de host_uniq.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-193">**host_uniq_length** Length of host_uniq</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-194">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-194">Return Values</span></span>

 - <span data-ttu-id="c6c4c-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Configuración correcta del host único del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="c6c4c-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Puntero de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="c6c4c-197">**NX_SIZE_ERROR** (0x09) Error en la comprobación de host_uniq_length.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-197">**NX_SIZE_ERROR** (0x09) Check host_uniq_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-198">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-198">Allowed From</span></span>

<span data-ttu-id="c6c4c-199">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-199">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-200">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-200">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a><span data-ttu-id="c6c4c-201">nx_pppoe_client_service_name_set</span><span class="sxs-lookup"><span data-stu-id="c6c4c-201">nx_pppoe_client_service_name_set</span></span>

<span data-ttu-id="c6c4c-202">Establecer el nombre del servicio del cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="c6c4c-202">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-203">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-203">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a><span data-ttu-id="c6c4c-204">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-204">Description</span></span>

<span data-ttu-id="c6c4c-205">Este servicio establece el nombre del servicio del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-205">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="c6c4c-206">Service-Name que indica el servicio que el host está solicitando.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-206">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="c6c4c-207">Si no se establece Service-Name, indica que el host aceptará cualquier número de servicios.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-207">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-208">El nombre del servicio debe ser una cadena terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-208">service name must be Null-terminated string</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-209">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-209">This service is deprecated.</span></span> <span data-ttu-id="c6c4c-210">Se recomienda a los desarrolladores que migren a *nx_pppoe_client_service_name_set_extended()* .</span><span class="sxs-lookup"><span data-stu-id="c6c4c-210">Developers are encouraged to migrate to *nx_pppoe_client_service_name_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-211">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-211">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-212">**pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-212">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="c6c4c-213">**SERVICE_NAME** Puntero a un nombre de servicio.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-213">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="c6c4c-214">El nombre del servicio debe ser una cadena terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-214">Service name must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-215">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-215">Return Values</span></span>

 - <span data-ttu-id="c6c4c-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Configuración correcta del nombre del servicio del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="c6c4c-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Puntero de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-218">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-218">Allowed From</span></span>

<span data-ttu-id="c6c4c-219">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-219">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-220">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-220">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a><span data-ttu-id="c6c4c-221">nx_pppoe_client_service_name_set_extended</span><span class="sxs-lookup"><span data-stu-id="c6c4c-221">nx_pppoe_client_service_name_set_extended</span></span>

<span data-ttu-id="c6c4c-222">Establecer el nombre del servicio del cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="c6c4c-222">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-223">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-223">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a><span data-ttu-id="c6c4c-224">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-224">Description</span></span>

<span data-ttu-id="c6c4c-225">Este servicio establece el nombre del servicio del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-225">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="c6c4c-226">Service-Name que indica el servicio que el host está solicitando.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-226">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="c6c4c-227">Si no se establece Service-Name, indica que el host aceptará cualquier número de servicios.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-227">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-228">El nombre del servicio debe ser una cadena terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-228">service name must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-229">Este servicio reemplaza a *nx_pppoe_client_service_name_set()* .</span><span class="sxs-lookup"><span data-stu-id="c6c4c-229">This service replaces *nx_pppoe_client_service_name_set()*.</span></span> <span data-ttu-id="c6c4c-230">Esta versión proporciona a la función información adicional sobre la longitud del nombre del servicio.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-230">This version supplies additional service name length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-231">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-231">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-232">**pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-232">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="c6c4c-233">**SERVICE_NAME** Puntero a un nombre de servicio.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-233">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="c6c4c-234">El nombre del servicio debe ser una cadena terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-234">Service name must be Null-terminated string.</span></span>
 - <span data-ttu-id="c6c4c-235">**service_name_length** Longitud de service_name.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-235">**service_name_length** Length of service_name</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-236">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-236">Return Values</span></span>

 - <span data-ttu-id="c6c4c-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Configuración correcta del nombre del servicio del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="c6c4c-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Puntero de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="c6c4c-239">**NX_SIZE_ERROR** (0x09) Error de comprobación de service_name_length.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-239">**NX_SIZE_ERROR** (0x09) Check service_name_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-240">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-240">Allowed From</span></span>

<span data-ttu-id="c6c4c-241">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-241">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-242">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-242">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a><span data-ttu-id="c6c4c-243">nx_pppoe_client_session_connect</span><span class="sxs-lookup"><span data-stu-id="c6c4c-243">nx_pppoe_client_session_connect</span></span>

<span data-ttu-id="c6c4c-244">Conectar sesión de cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="c6c4c-244">Connect PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-245">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-245">Prototype</span></span>

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c6c4c-246">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-246">Description</span></span>

<span data-ttu-id="c6c4c-247">Este servicio realiza la conexión de la sesión de PPPoE utilizando un cliente PPPoE previamente creado al servidor de PPPoE especificado.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-247">This service makes PPPoE session connection using a previously created PPPoE Client to the specified PPPoE Server.</span></span>

> [!NOTE]
> <span data-ttu-id="c6c4c-248">Se debe llamar a esta función después de *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* y *nx_pppoe_client_service_name_set*.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-248">This function must be called after *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* and *nx_pppoe_client_service_name_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-249">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-249">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-250">**pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-250">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="c6c4c-251">**wait_option** Opción de espera mientras se establece la conexión.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-251">**wait_option** Wait option while the connection is being established.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-252">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-252">Return Values</span></span>

 - <span data-ttu-id="c6c4c-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Conexión correcta de la sesión del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session connect.</span></span>
 - <span data-ttu-id="c6c4c-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-255">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-255">Allowed From</span></span>

<span data-ttu-id="c6c4c-256">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-256">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-257">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-257">Example</span></span>

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a><span data-ttu-id="c6c4c-258">nx_pppoe_client_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="c6c4c-258">nx_pppoe_client_session_packet_send</span></span>

<span data-ttu-id="c6c4c-259">Enviar paquete de cliente PPPoE a la sesión especificada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-259">Send PPPoE Client packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-260">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-260">Prototype</span></span>

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="c6c4c-261">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-261">Description</span></span>

<span data-ttu-id="c6c4c-262">Este servicio envía un paquete de PPPoE mediante el identificador de sesión especificado.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-262">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-263">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-263">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-264">**pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-264">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="c6c4c-265">**packet_ptr** Puntero a paquete de PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-265">**packet_ptr** Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-266">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-266">Return Values</span></span>

 - <span data-ttu-id="c6c4c-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Envío correcto del paquete del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client packet send.</span></span>
 - <span data-ttu-id="c6c4c-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="c6c4c-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Paquete de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid PPPoE Client packet.</span></span>
 - <span data-ttu-id="c6c4c-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) Sesión de PPPoE no establecida.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-271">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-271">Allowed From</span></span>

<span data-ttu-id="c6c4c-272">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-272">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-273">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-273">Example</span></span>

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a><span data-ttu-id="c6c4c-274">nx_pppoe_client_session_terminate</span><span class="sxs-lookup"><span data-stu-id="c6c4c-274">nx_pppoe_client_session_terminate</span></span>

<span data-ttu-id="c6c4c-275">Finalizar sesión de cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="c6c4c-275">Terminate PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-276">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-276">Prototype</span></span>

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="c6c4c-277">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-277">Description</span></span>

<span data-ttu-id="c6c4c-278">Este servicio finaliza la sesión de PPPoE especificada.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-278">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-279">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-279">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-280">**pppoe_client_ptr** Puntero al bloque de control del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-280">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-281">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-281">Return Values</span></span>

 - <span data-ttu-id="c6c4c-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Finalización correcta de la sesión del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session terminate.</span></span>
 - <span data-ttu-id="c6c4c-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-284">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-284">Allowed From</span></span>

<span data-ttu-id="c6c4c-285">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-285">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-286">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-286">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a><span data-ttu-id="c6c4c-287">nx_pppoe_client_session_get</span><span class="sxs-lookup"><span data-stu-id="c6c4c-287">nx_pppoe_client_session_get</span></span>

<span data-ttu-id="c6c4c-288">Obtener la información de sesión de PPPoE especificada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-288">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="c6c4c-289">Prototipo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-289">Prototype</span></span>

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="c6c4c-290">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c4c-290">Description</span></span>

<span data-ttu-id="c6c4c-291">Este servicio obtiene la información de sesión de PPPoE especificada, la dirección física del servidor y el identificador de sesión.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-291">This service gets the specified PPPoE session information, server physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c6c4c-292">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="c6c4c-292">Input Parameters</span></span>

 - <span data-ttu-id="c6c4c-293">**pppoe_server_ptr** Puntero al bloque de control de cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-293">**pppoe_server_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="c6c4c-294">**server_mac_msw** Puntero MSW de dirección física del servidor.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-294">**server_mac_msw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="c6c4c-295">**server_mac_lsw** Puntero MSW de dirección física del servidor.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-295">**server_mac_lsw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="c6c4c-296">**session_id** Puntero de identificador de sesión.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-296">**session_id** Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="c6c4c-297">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-297">Return Values</span></span>

 - <span data-ttu-id="c6c4c-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Obtención correcta de la sesión del cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session get.</span></span>
 - <span data-ttu-id="c6c4c-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Puntero de cliente PPPoE no válido.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="c6c4c-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) Sesión de PPPoE no establecida.</span><span class="sxs-lookup"><span data-stu-id="c6c4c-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c6c4c-301">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="c6c4c-301">Allowed From</span></span>

<span data-ttu-id="c6c4c-302">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="c6c4c-302">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="c6c4c-303">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c4c-303">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
