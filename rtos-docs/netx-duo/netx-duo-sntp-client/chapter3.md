---
title: 'Capítulo 3: Descripción de los servicios del cliente SNTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del cliente SNTP de NetX Duo incluidos a continuación por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814550"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a><span data-ttu-id="a2f36-103">Capítulo 3: Descripción de los servicios del cliente SNTP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a2f36-103">Chapter 3 - Description of Azure RTOS NetX Duo SNTP Client Services</span></span>

<span data-ttu-id="a2f36-104">Este capítulo contiene una descripción de todos los servicios del cliente SNTP de Azure RTOS NetX Duo incluidos a continuación por orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="a2f36-104">This chapter contains a description of all Azure RTOS NetX Duo SNTP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="a2f36-105">En la sección “Valores devueltos” de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición de **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="a2f36-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="a2f36-106">**nx_sntp_client_create**: *crea el cliente SNTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-106">**nx_sntp_client_create**: *Create the SNTP Client*</span></span>
- <span data-ttu-id="a2f36-107">**nx_sntp_client_delete**: *elimina el cliente SNTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-107">**nx_sntp_client_delete**: *Delete the SNTP Client*</span></span>
- <span data-ttu-id="a2f36-108">**nx_sntp_client_get_local_time**: *obtiene la hora local del cliente SNTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-108">**nx_sntp_client_get_local_time**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="a2f36-109">**nx_sntp_client_get_local_time_extended**: *obtiene la hora local del cliente SNTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-109">**nx_sntp_client_get_local_time_extended**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="a2f36-110">**nx_sntp_client_initialize_broadcast**: *inicializa el cliente para la operación de difusión en IPv4.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-110">**nx_sntp_client_initialize_broadcast**: *Initialize Client for IPv4 broadcast operation*</span></span>
- <span data-ttu-id="a2f36-111">**nxd_sntp_client_initialize_broadcast**: *inicializa el cliente para la operación de difusión en IPv6 o IPv4.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-111">**nxd_sntp_client_initialize_broadcast**: *Initialize Client for IPv6 or IPv4 broadcast operation*</span></span>
- <span data-ttu-id="a2f36-112">**nx_sntp_client_initialize_unicast**: *inicializa el cliente para la operación de unidifusión en IPv4.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-112">**nx_sntp_client_initialize_unicast**: *Initialize Client for IPv4 unicast operation*</span></span>
- <span data-ttu-id="a2f36-113">**nxd_sntp_client_initialize_unicast**: *inicializa el cliente para la operación de unidifusión en IPv4 o IPv6.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-113">**nxd_sntp_client_initialize_unicast**: *Initialize Client for IPv4 or IPv6 unicast operation*</span></span>
- <span data-ttu-id="a2f36-114">**nx_sntp_client_receiving_udpates**: *el cliente está recibiendo actualmente actualizaciones válidas de SNTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-114">**nx_sntp_client_receiving_udpates**: *Client is currently receiving valid SNTP updates*</span></span>
- <span data-ttu-id="a2f36-115">**nx_sntp_client_request_unicast_time**: *envía una solicitud de unidifusión directamente al servidor NTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-115">**nx_sntp_client_request_unicast_time**: *Send a unicast request directly to the NTP Server*</span></span>
- <span data-ttu-id="a2f36-116">**nx_sntp_client_run_broadcast**: *ejecuta el cliente en modo de difusión.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-116">**nx_sntp_client_run_broadcast**: *Run the Client in broadcast mode*</span></span>
- <span data-ttu-id="a2f36-117">**nx_sntp_client_run_unicast**: *ejecuta el cliente en modo de unidifusión.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-117">**nx_sntp_client_run_unicast**: *Run the Client in unicast mode*</span></span>
- <span data-ttu-id="a2f36-118">**nx_sntp_client_set_local_time**: *establece la hora local inicial del cliente SNTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-118">**nx_sntp_client_set_local_time**: *Set SNTP Client initial local time*</span></span>
- <span data-ttu-id="a2f36-119">**nx_sntp_client_set_time_update_notify**: *establece la devolución de llamada de actualización de SNTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-119">**nx_sntp_client_set_time_update_notify**: *Set the SNTP update callback*</span></span>
- <span data-ttu-id="a2f36-120">**nx_sntp_client_stop**: *detiene el subproceso del cliente SNTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-120">**nx_sntp_client_stop**: *Stop the SNTP Client thread*</span></span>
- <span data-ttu-id="a2f36-121">**nx_sntp_client_utility_display_date_and_time**: *muestra la hora de NTP en segundos.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-121">**nx_sntp_client_utility_display_date_and_time**: *Display NTP time in seconds*</span></span>
- <span data-ttu-id="a2f36-122">**nx_sntp_client_utility_msecs_to_fraction**: *convierte milisegundos a un componente de fracción de NTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-122">**nx_sntp_client_utility_msecs_to_fraction**: *Convert milliseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="a2f36-123">**nx_sntp_client_utility_usecs_to_fraction**: *convierte microsegundos a un componente de fracción de NTP.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-123">**nx_sntp_client_utility_usecs_to_fraction**: *Convert microseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="a2f36-124">**nx_sntp_client_utility_fraction_to_usecs**: *convierte un componente de fracción de NTP a microsegundos.*</span><span class="sxs-lookup"><span data-stu-id="a2f36-124">**nx_sntp_client_utility_fraction_to_usecs**: *Convert an NTP fraction component to microseconds*</span></span>


## <a name="nx_sntp_client_create"></a><span data-ttu-id="a2f36-125">nx_sntp_client_create</span><span class="sxs-lookup"><span data-stu-id="a2f36-125">nx_sntp_client_create</span></span>

<span data-ttu-id="a2f36-126">Crea un cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-126">Create an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-127">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-127">Prototype</span></span>

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a><span data-ttu-id="a2f36-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-128">Description</span></span>

<span data-ttu-id="a2f36-129">Este servicio crea una instancia del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-129">This service creates an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-130">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-130">Input Parameters</span></span>

- <span data-ttu-id="a2f36-131">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-131">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="a2f36-132">**ip_ptr**: puntero a la instancia de IP del cliente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-132">**ip_ptr** Pointer to Client IP instance</span></span>

- <span data-ttu-id="a2f36-133">**iface_index**: índice de la interfaz de red de SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-133">**iface_index** Index to SNTP network interface</span></span>

- <span data-ttu-id="a2f36-134">**packet_pool_ptr**: puntero al grupo de paquetes del cliente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-134">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="a2f36-135">**leap_second_handler**: devolución de llamada para la respuesta de la aplicación al segundo intercalar inminente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-135">**leap_second_handler** Callback for application response to impending leap second</span></span>

- <span data-ttu-id="a2f36-136">**kiss_of_death_handler**: devolución de llamada para la respuesta de la aplicación a la recepción de un paquete de beso de la muerte.</span><span class="sxs-lookup"><span data-stu-id="a2f36-136">**kiss_of_death_handler** Callback for application response to receiving Kiss of Death packet</span></span>

- <span data-ttu-id="a2f36-137">**random_number_generator**: devolución de llamada al servicio generador de números aleatorios.</span><span class="sxs-lookup"><span data-stu-id="a2f36-137">**random_number_generator** Callback to random number generator service</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-138">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-138">Return Values</span></span>

- <span data-ttu-id="a2f36-139">**NX_SUCCESS**: (0x00) creación correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-139">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="a2f36-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD**: (0xD2A) entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Invalid non pointer input</span></span>

- <span data-ttu-id="a2f36-141">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-141">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-142">NX_INVALID_INTERFACE: (0x4C) interfaz de red no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-142">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-143">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-143">Allowed From</span></span>

<span data-ttu-id="a2f36-144">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-145">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-145">Example</span></span>

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a><span data-ttu-id="a2f36-146">nx_sntp_client_delete</span><span class="sxs-lookup"><span data-stu-id="a2f36-146">nx_sntp_client_delete</span></span>

<span data-ttu-id="a2f36-147">Elimina un cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-147">Delete an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-148">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-148">Prototype</span></span>

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="a2f36-149">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-149">Description</span></span>

<span data-ttu-id="a2f36-150">Este servicio elimina una instancia del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-150">This service deletes an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-151">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-151">Input Parameters</span></span>

- <span data-ttu-id="a2f36-152">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-152">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-153">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-153">Return Values</span></span>

- <span data-ttu-id="a2f36-154">**NX_SUCCESS**: (0x00) creación correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-154">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="a2f36-155">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-155">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-156">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-156">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-157">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-157">Allowed From</span></span>

<span data-ttu-id="a2f36-158">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-159">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-159">Example</span></span>

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a><span data-ttu-id="a2f36-160">nx_sntp_client_get_local_time</span><span class="sxs-lookup"><span data-stu-id="a2f36-160">nx_sntp_client_get_local_time</span></span>

<span data-ttu-id="a2f36-161">Obtiene la hora local del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-161">Get the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-162">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-162">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a><span data-ttu-id="a2f36-163">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-163">Description</span></span>

<span data-ttu-id="a2f36-164">Este servicio obtiene la hora local del cliente SNTP con una entrada de puntero al búfer opcional para recibir los datos en formato de mensaje de cadena.</span><span class="sxs-lookup"><span data-stu-id="a2f36-164">This service gets the SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

<span data-ttu-id="a2f36-165">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="a2f36-165">This service is deprecated.</span></span> <span data-ttu-id="a2f36-166">Se recomienda a los desarrolladores que migren a *nx_sntp_client_get_local_time_extended*().</span><span class="sxs-lookup"><span data-stu-id="a2f36-166">Developers are encouraged to migrate to *nx_sntp_client_get_local_time_extended*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-167">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-167">Input Parameters</span></span>

- <span data-ttu-id="a2f36-168">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-168">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="a2f36-169">**seconds**: puntero a los segundos de la hora local.</span><span class="sxs-lookup"><span data-stu-id="a2f36-169">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="a2f36-170">**fraction**: componente de fracción de la hora local.</span><span class="sxs-lookup"><span data-stu-id="a2f36-170">**fraction** Local time fraction component</span></span>

- <span data-ttu-id="a2f36-171">**buffer**: puntero al búfer para escribir datos de hora.</span><span class="sxs-lookup"><span data-stu-id="a2f36-171">**buffer** Pointer to buffer to write time data</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-172">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-172">Return Values</span></span>

- <span data-ttu-id="a2f36-173">**NX_SUCCESS**: (0x00) creación correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-173">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="a2f36-174">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-174">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-175">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-175">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-176">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-176">Allowed From</span></span>

<span data-ttu-id="a2f36-177">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-178">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-178">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a><span data-ttu-id="a2f36-179">nx_sntp_client_get_local_time_extended</span><span class="sxs-lookup"><span data-stu-id="a2f36-179">nx_sntp_client_get_local_time_extended</span></span>

<span data-ttu-id="a2f36-180">Obtiene la hora local extendida del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-180">Get the extended SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-181">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-181">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a><span data-ttu-id="a2f36-182">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-182">Description</span></span>

<span data-ttu-id="a2f36-183">Este servicio obtiene la hora local extendida del cliente SNTP con una entrada de puntero al búfer opcional para recibir los datos en formato de mensaje de cadena.</span><span class="sxs-lookup"><span data-stu-id="a2f36-183">This service gets the extended SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-184">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-184">Input Parameters</span></span>

- <span data-ttu-id="a2f36-185">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-185">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="a2f36-186">**seconds**: puntero a los segundos de la hora local.</span><span class="sxs-lookup"><span data-stu-id="a2f36-186">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="a2f36-187">**fraction**: puntero al componente de fracción.</span><span class="sxs-lookup"><span data-stu-id="a2f36-187">**fraction** Pointer to fraction component</span></span>

- <span data-ttu-id="a2f36-188">**buffer**: puntero al búfer para escribir datos de hora.</span><span class="sxs-lookup"><span data-stu-id="a2f36-188">**buffer** Pointer to buffer to write time data</span></span>

- <span data-ttu-id="a2f36-189">**buffer_size**: longitud del búfer.</span><span class="sxs-lookup"><span data-stu-id="a2f36-189">**buffer_size** Length of buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-190">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-190">Return Values</span></span>

- <span data-ttu-id="a2f36-191">**NX_SUCCESS**: (0x00) creación correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-191">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="a2f36-192">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-192">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-193">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-193">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

- <span data-ttu-id="a2f36-194">NX_SIZE_ERROR: (0x09) error de comprobación de buffer_size.</span><span class="sxs-lookup"><span data-stu-id="a2f36-194">NX_SIZE_ERROR (0x09) Check buffer_size fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-195">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-195">Allowed From</span></span>

<span data-ttu-id="a2f36-196">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-197">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-197">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a><span data-ttu-id="a2f36-198">nx_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="a2f36-198">nx_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="a2f36-199">Inicializa el cliente para la operación de difusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-199">Initialize the Client for broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-200">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-200">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a><span data-ttu-id="a2f36-201">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-201">Description</span></span>

<span data-ttu-id="a2f36-202">Este servicio inicializa el cliente para la operación de difusión estableciendo la dirección IP del servidor SNTP e inicializando los parámetros de inicio y los tiempos de espera de SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-202">This service initializes the Client for broadcast operation by setting the the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="a2f36-203">Si ni la dirección de multidifusión ni la de difusión son NULL, se selecciona la dirección de multidifusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-203">If both multicast and broadcast addresses are non-null, the multicast address is selected.</span></span> <span data-ttu-id="a2f36-204">Si ambas direcciones son NULL, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="a2f36-204">If both addresses are null an error is returned.</span></span> <span data-ttu-id="a2f36-205">Tenga en cuenta que solo es compatible con las direcciones de servidor IPv4.</span><span class="sxs-lookup"><span data-stu-id="a2f36-205">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-206">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-206">Input Parameters</span></span>

- <span data-ttu-id="a2f36-207">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-207">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="a2f36-208">**multicast_server_address**: dirección de multidifusión de SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-208">**multicast_server_address** SNTP multicast address</span></span>

- <span data-ttu-id="a2f36-209">**broadcast_time_server**: dirección de difusión del servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-209">**broadcast_time_server** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-210">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-210">Return Values</span></span>

- <span data-ttu-id="a2f36-211">**NX_SUCCESS**: (0x00) creación correcta del cliente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-211">**NX_SUCCESS** (0x00) Successful Client Creation</span></span>

- <span data-ttu-id="a2f36-212">**NX_INVALID_PARAMETERS**: (0x4D) entrada que no es de puntero no válida:</span><span class="sxs-lookup"><span data-stu-id="a2f36-212">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="a2f36-213">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-213">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-214">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-214">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-215">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-215">Allowed From</span></span>

<span data-ttu-id="a2f36-216">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-216">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-217">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-217">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a><span data-ttu-id="a2f36-218">nxd_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="a2f36-218">nxd_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="a2f36-219">Inicializa el cliente para la operación de difusión en IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="a2f36-219">Initialize the Client for IPv4 or IPv6 broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-220">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-220">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a><span data-ttu-id="a2f36-221">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-221">Description</span></span>

<span data-ttu-id="a2f36-222">Este servicio inicializa el cliente para la operación de difusión configurando la dirección IP del servidor SNTP e inicializando los parámetros de inicio y los tiempos de espera de SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-222">This service initializes the Client for broadcast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="a2f36-223">Si ni el puntero a la dirección de multidifusión ni a la de difusión son NULL, se selecciona la dirección de multidifusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-223">If both broadcast and multicast address pointers are non null, the multicast address is selected.</span></span> <span data-ttu-id="a2f36-224">Si ambos punteros de dirección son NULL, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="a2f36-224">If both address pointers are null, an error is returned.</span></span> <span data-ttu-id="a2f36-225">Es compatible con los tipos de dirección IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="a2f36-225">This supports both IPv4 and IPv6 address types.</span></span> <span data-ttu-id="a2f36-226">Tenga en cuenta que IPv6 no admite la difusión, por lo que si el puntero de dirección de difusión se establece en IPv6, se devuelve un error.</span><span class="sxs-lookup"><span data-stu-id="a2f36-226">Note that IPv6 does not support broadcast, so the broadcast address pointer is set to IPv6, an error is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-227">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-227">Input Parameters</span></span>

- <span data-ttu-id="a2f36-228">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-228">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="a2f36-229">**multicast_server_address**: dirección de multidifusión del servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-229">**multicast_server_address** SNTP server multicast address</span></span>

- <span data-ttu-id="a2f36-230">**broadcast_server_address**: dirección de difusión del servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-230">**broadcast_server_address** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-231">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-231">Return Values</span></span>

- <span data-ttu-id="a2f36-232">**NX_SUCCESS**: (0x00) cliente inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-232">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="a2f36-233">NX_SNTP_PARAM_ERROR: (0xD0D) entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-233">NX_SNTP_PARAM_ERROR (0xD0D) Invalid non pointer input</span></span>

- <span data-ttu-id="a2f36-234">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-234">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-235">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-235">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="a2f36-236">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-236">Allowed From</span></span>

<span data-ttu-id="a2f36-237">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-237">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-238">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-238">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a><span data-ttu-id="a2f36-239">nx_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="a2f36-239">nx_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="a2f36-240">Configura el cliente SNTP para que se ejecute en unidifusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-240">Set up the SNTP Client to run in unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-241">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-241">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a><span data-ttu-id="a2f36-242">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-242">Description</span></span>

<span data-ttu-id="a2f36-243">Este servicio inicializa el cliente para la operación de unidifusión estableciendo la dirección IP del servidor SNTP e inicializando los parámetros de inicio y los tiempos de espera de SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-243">This service initializes the Client for unicast operation by setting the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="a2f36-244">Tenga en cuenta que solo es compatible con las direcciones de servidor IPv4.</span><span class="sxs-lookup"><span data-stu-id="a2f36-244">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-245">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-245">Input Parameters</span></span>

- <span data-ttu-id="a2f36-246">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-246">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="a2f36-247">**unicast_time_server**: dirección IP del servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-247">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-248">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-248">Return Values</span></span>

- <span data-ttu-id="a2f36-249">**NX_SUCCESS**: (0x00) cliente inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-249">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="a2f36-250">NX_INVALID_PARAMETERS: (0x4D) entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-250">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="a2f36-251">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-251">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-252">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-252">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-253">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-253">Allowed From</span></span>

<span data-ttu-id="a2f36-254">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-254">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-255">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-255">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a><span data-ttu-id="a2f36-256">nxd_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="a2f36-256">nxd_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="a2f36-257">Configura el cliente SNTP para que se ejecute en unidifusión en IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="a2f36-257">Set up the SNTP Client to run in IPv4 or IPv6 unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-258">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-258">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a><span data-ttu-id="a2f36-259">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-259">Description</span></span>

<span data-ttu-id="a2f36-260">Este servicio inicializa el cliente para la operación de unidifusión configurando la dirección IP del servidor SNTP e inicializando los parámetros de inicio y los tiempos de espera de SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-260">This service initializes the Client for unicast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="a2f36-261">Es compatible con los tipos de dirección IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="a2f36-261">This supports both IPv4 and IPv6 address types.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-262">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-262">Input Parameters</span></span>

- <span data-ttu-id="a2f36-263">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-263">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="a2f36-264">**unicast_time_server**: dirección IP del servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-264">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-265">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-265">Return Values</span></span>

- <span data-ttu-id="a2f36-266">**NX_SUCCESS**: (0x00) cliente inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-266">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="a2f36-267">NX_INVALID_PARAMETERS: (0x4D) entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-267">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="a2f36-268">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-268">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-269">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-269">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-270">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-270">Allowed From</span></span>

<span data-ttu-id="a2f36-271">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-271">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-272">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-272">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a><span data-ttu-id="a2f36-273">nx_sntp_client_receiving_updates</span><span class="sxs-lookup"><span data-stu-id="a2f36-273">nx_sntp_client_receiving_updates</span></span>

<span data-ttu-id="a2f36-274">Indica si el cliente está recibiendo actualizaciones válidas.</span><span class="sxs-lookup"><span data-stu-id="a2f36-274">Indicate if Client is receiving valid updates</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-275">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-275">Prototype</span></span>

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a><span data-ttu-id="a2f36-276">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-276">Description</span></span>

<span data-ttu-id="a2f36-277">Este servicio indica si el cliente está recibiendo actualizaciones SNTP válidas.</span><span class="sxs-lookup"><span data-stu-id="a2f36-277">This service indicates if the Client is receiving valid SNTP updates.</span></span> <span data-ttu-id="a2f36-278">Si se supera el intervalo máximo de tiempo sin una actualización o se supera el límite de actualizaciones no válidas consecutivas, el estado de recepción se devuelve como false.</span><span class="sxs-lookup"><span data-stu-id="a2f36-278">If the maximum time lapse without a valid update or limit on consecutive invalid updates is exceeded, the receive status is returned as false.</span></span> <span data-ttu-id="a2f36-279">Tenga en cuenta que el cliente SNTP se sigue ejecutando y, si la aplicación desea reiniciarlo con otro servidor de unidifusión o de difusión/multidifusión, debe detenerlo mediante el servicio *nx_sntp_client_stop* y después reinicializarlo mediante uno de los servicios de inicialización con otro servidor.</span><span class="sxs-lookup"><span data-stu-id="a2f36-279">Note that the SNTP Client is still running and if the application wishes to restart the SNTP Client with another unicast or broadcast/multicast server it must stop the SNTP Client using the *nx_sntp_client_stop* service, reinitialize the Client using one of the initialize services with another server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-280">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-280">Input Parameters</span></span>

- <span data-ttu-id="a2f36-281">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-281">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="a2f36-282">**receive_status**: puntero al indicador que señala si el cliente está recibiendo actualizaciones válidas.</span><span class="sxs-lookup"><span data-stu-id="a2f36-282">**receive_status** Pointer to indicator if Client is receiving valid updates.</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-283">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-283">Return Values</span></span>

- <span data-ttu-id="a2f36-284">**NX_SUCCESS**: (0x00) el cliente ha recibido correctamente el estado de actualización.</span><span class="sxs-lookup"><span data-stu-id="a2f36-284">**NX_SUCCESS** (0x00) Client successfully received update status</span></span>

- <span data-ttu-id="a2f36-285">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-285">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-286">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-286">Allowed From</span></span>

<span data-ttu-id="a2f36-287">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-287">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-288">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-288">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a><span data-ttu-id="a2f36-289">nx_sntp_client_request_unicast_time</span><span class="sxs-lookup"><span data-stu-id="a2f36-289">nx_sntp_client_request_unicast_time</span></span>

<span data-ttu-id="a2f36-290">Envía una solicitud de unidifusión directamente al servidor NTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-290">Send a unicast request directly to the NTP Server</span></span>


### <a name="prototype"></a><span data-ttu-id="a2f36-291">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-291">Prototype</span></span>

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="a2f36-292">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-292">Description</span></span>

<span data-ttu-id="a2f36-293">Este servicio permite que la aplicación envíe directamente una solicitud de unidifusión al servidor NTP de forma asincrónica desde la tarea de subproceso del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-293">This service allows the application to directly send a unicast request to the NTP server asynchronously from the SNTP Client thread task.</span></span> <span data-ttu-id="a2f36-294">La opción de espera especifica cuánto tiempo se debe esperar por una respuesta.</span><span class="sxs-lookup"><span data-stu-id="a2f36-294">The wait option specifies how long to wait for a response.</span></span> <span data-ttu-id="a2f36-295">Si finaliza correctamente, la aplicación puede usar otros servicios del cliente SNTP para obtener la hora más reciente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-295">If successful, the application can use other SNTP Client services to obtain the latest time.</span></span> <span data-ttu-id="a2f36-296">Consulte la sección **Solicitudes asincrónicas de unidifusión de SNTP** para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="a2f36-296">See section **SNTP Asynchronous Unicast Requests** for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-297">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-297">Input Parameters</span></span>

- <span data-ttu-id="a2f36-298">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-298">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="a2f36-299">**Wait_option**: opción de espera por la respuesta de NTP en tics de temporizador.</span><span class="sxs-lookup"><span data-stu-id="a2f36-299">**Wait_option** Wait option for NTP response in timer ticks.</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-300">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-300">Return Values</span></span>

- <span data-ttu-id="a2f36-301">**NX_SUCCESS**: (0x00) el cliente envía y recibe correctamente la actualización de unidifusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-301">**NX_SUCCESS** (0x00) Client successfully sends and receives unicast update</span></span>

- <span data-ttu-id="a2f36-302">**NX_SNTP_CLIENT_NOT_STARTED**: (0xD0B) no se ha iniciado el subproceso del cliente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Client thread not started</span></span>

- <span data-ttu-id="a2f36-303">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-303">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-304">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-304">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-305">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-305">Allowed From</span></span>

<span data-ttu-id="a2f36-306">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-307">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-307">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a><span data-ttu-id="a2f36-308">nx_sntp_client_run_broadcast</span><span class="sxs-lookup"><span data-stu-id="a2f36-308">nx_sntp_client_run_broadcast</span></span>

<span data-ttu-id="a2f36-309">Ejecuta el cliente en modo de difusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-309">Run the Client in broadcast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-310">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-310">Prototype</span></span>

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="a2f36-311">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-311">Description</span></span>

<span data-ttu-id="a2f36-312">Este servicio inicia el cliente en modo de difusión, en el que esperará para recibir las difusiones del servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-312">This service starts the Client in broadcast mode where it will wait to receive broadcasts from the SNTP server.</span></span> <span data-ttu-id="a2f36-313">Si se recibe un mensaje SNTP de difusión válido, se restablecen el tiempo de espera del cliente SNTP del intervalo máximo sin actualizaciones y el número de mensajes no válidos consecutivos recibidos.</span><span class="sxs-lookup"><span data-stu-id="a2f36-313">If a valid broadcast SNTP message is received, the SNTP client timeout for maximum lapse without an update and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="a2f36-314">Si se supera cualquiera de estos límites, el cliente SNTP establece el estado del servidor en no válido, aunque seguirá esperando recibir actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="a2f36-314">If the either of these limits are exceeded, the SNTP Client sets the server status to invalid although it will still wait to receive updates.</span></span> <span data-ttu-id="a2f36-315">La aplicación puede sondear la tarea de cliente SNTP para comprobar el estado del servidor y, si no es válido, detener el cliente SNTP y reinicializarlo con otra dirección de difusión SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-315">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP broadcast address.</span></span> <span data-ttu-id="a2f36-316">También puede cambiar a un servidor SNTP de unidifusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-316">It can also switch to a unicast SNTP server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-317">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-317">Input Parameters</span></span>

- <span data-ttu-id="a2f36-318">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-318">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-319">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-319">Return Values</span></span>

- <span data-ttu-id="a2f36-320">**status**: -------- estado de finalización real.</span><span class="sxs-lookup"><span data-stu-id="a2f36-320">**status** -------- Actual completion status</span></span>

- <span data-ttu-id="a2f36-321">**NX_SNTP_CLIENT_ALREADY_STARTED**: (0xD0C) el cliente ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="a2f36-321">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="a2f36-322">**NX_SNTP_CLIENT_NOT_INITIALIZED**: (0xD01) el cliente no se ha inicializado.</span><span class="sxs-lookup"><span data-stu-id="a2f36-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="a2f36-323">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-323">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-324">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-324">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-325">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-325">Allowed From</span></span>

<span data-ttu-id="a2f36-326">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-326">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-327">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-327">Example</span></span>

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a><span data-ttu-id="a2f36-328">nx_sntp_client_run_unicast</span><span class="sxs-lookup"><span data-stu-id="a2f36-328">nx_sntp_client_run_unicast</span></span>

<span data-ttu-id="a2f36-329">Ejecuta el cliente en modo de unidifusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-329">Run the Client in unicast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-330">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-330">Prototype</span></span>

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="a2f36-331">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-331">Description</span></span>

<span data-ttu-id="a2f36-332">Este servicio inicia el cliente en modo de unidifusión, desde el que envía periódicamente una solicitud de unidifusión a su servidor SNTP para una actualización de hora.</span><span class="sxs-lookup"><span data-stu-id="a2f36-332">This service starts the Client in unicast mode where it periodically sends a unicast request to its SNTP Server for a time update.</span></span> <span data-ttu-id="a2f36-333">Si se recibe un mensaje SNTP válido, se restablecen el tiempo de espera del cliente SNTP del intervalo máximo sin actualizaciones, el intervalo inicial de sondeo y el número de mensajes no válidos consecutivos recibidos.</span><span class="sxs-lookup"><span data-stu-id="a2f36-333">If a valid SNTP message is received, the SNTP client timeout for maximum lapse without an update, initial polling interval and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="a2f36-334">Si se supera cualquiera de estos límites, el cliente SNTP establece el estado del servidor en no válido, aunque seguirá sondeando y esperando recibir actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="a2f36-334">If the either of these limits are exceeded, the SNTP Client sets the Server status to invalid although it will still poll and wait to receive updates.</span></span> <span data-ttu-id="a2f36-335">La aplicación puede sondear la tarea de cliente SNTP para comprobar el estado del servidor y, si no es válido, detener el cliente SNTP y reinicializarlo con otra dirección de unidifusión SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-335">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP unicast address.</span></span> <span data-ttu-id="a2f36-336">También puede cambiar a un servidor SNTP de difusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-336">It can also switch to a broadcast SNTP server.</span></span>

<span data-ttu-id="a2f36-337">.</span><span class="sxs-lookup"><span data-stu-id="a2f36-337">.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-338">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-338">Input Parameters</span></span>

- <span data-ttu-id="a2f36-339">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-339">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-340">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-340">Return Values</span></span>

- <span data-ttu-id="a2f36-341">**NX_SUCCESS**: (0x00) el cliente se ha iniciado correctamente en modo de unidifusión.</span><span class="sxs-lookup"><span data-stu-id="a2f36-341">**NX_SUCCESS** (0x00) Successfully started Client in unicast mode</span></span>

- <span data-ttu-id="a2f36-342">**NX_SNTP_CLIENT_ALREADY_STARTED**: (0xD0C) el cliente ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="a2f36-342">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="a2f36-343">**NX_SNTP_CLIENT_NOT_INITIALIZED**: (0xD01) el cliente no se ha inicializado.</span><span class="sxs-lookup"><span data-stu-id="a2f36-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="a2f36-344">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-344">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="a2f36-345">NX_CALLER_ERROR: (0x11) autor de llamada del servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-345">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="a2f36-346">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-346">Allowed From</span></span>

<span data-ttu-id="a2f36-347">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-348">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-348">Example</span></span>

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a><span data-ttu-id="a2f36-349">nx_sntp_client_set_local_time</span><span class="sxs-lookup"><span data-stu-id="a2f36-349">nx_sntp_client_set_local_time</span></span>

<span data-ttu-id="a2f36-350">Establece la hora local del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-350">Set the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-351">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-351">Prototype</span></span>

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a><span data-ttu-id="a2f36-352">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-352">Description</span></span>

<span data-ttu-id="a2f36-353">Este servicio establece la hora local del cliente SNTP a partir de la hora de entrada, en formato SNTP; es decir, con segundos y una fracción, que es la forma de incluir fracciones de segundo en formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="a2f36-353">This service sets the SNTP Client local time with the input time, in SNTP format e.g. seconds and ‘fraction’ which is the format for putting fractions of a second in hexadecimal format.</span></span> <span data-ttu-id="a2f36-354">Está diseñado para actualizar la hora local del cliente SNTP a partir de un cronometrador independiente; por ejemplo, un reloj en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="a2f36-354">It is intended for updating the SNTP Client local time from an independent time keeper, e.g. a real time clock.</span></span> <span data-ttu-id="a2f36-355">El protocolo SNTP está diseñado de modo que las actualizaciones de hora de SNTP impidan el desfase de la hora del reloj local.</span><span class="sxs-lookup"><span data-stu-id="a2f36-355">The SNTP protocol is intended for SNTP time updates to keep local clock time from ‘drifting’.</span></span> <span data-ttu-id="a2f36-356">Las actualizaciones de hora del servidor SNTP pueden ser, aunque no está previsto que lo sean, la única entrada para la hora local del cliente SNTP si no hay ningún cronometrador independiente en el dispositivo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a2f36-356">SNTP server time updates can be, but are not intended to be the sole input to the SNTP Client local time if there is no independent time keeper on the application device.</span></span>

<span data-ttu-id="a2f36-357">Esta API también se puede usar para proporcionar al cliente SNTP una hora base antes de iniciar el subproceso del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-357">This API can also be used to give the SNTP Client a base time before starting the SNTP Client thread.</span></span> <span data-ttu-id="a2f36-358">La hora local del cliente SNTP se compara con las actualizaciones recibidas para obtener datos de hora válidos.</span><span class="sxs-lookup"><span data-stu-id="a2f36-358">The SNTP Client local time is compared to received updates for valid time data.</span></span> <span data-ttu-id="a2f36-359">La primera vez que se recibe una actualización puede haber una discrepancia muy grande.</span><span class="sxs-lookup"><span data-stu-id="a2f36-359">For the first time update received, there might be a very large discrepancy.</span></span> <span data-ttu-id="a2f36-360">Por lo tanto, existe una opción para que el cliente SNTP pase por alto la discrepancia de la primera actualización.</span><span class="sxs-lookup"><span data-stu-id="a2f36-360">Therefore there is an option for the SNTP Client to ignore the discrepancy on the first update.</span></span> <span data-ttu-id="a2f36-361">Así, el cliente SNTP puede iniciarse sin una hora base.</span><span class="sxs-lookup"><span data-stu-id="a2f36-361">In this manner, the SNTP Client can start without a base time.</span></span> <span data-ttu-id="a2f36-362">La hora de entrada puede obtenerse a partir de horas de época conocidas (normalmente disponibles en Internet) y se calcula como el número de segundos transcurridos desde el 1 de enero de 1900 (hasta 2036, año en que empezará una nueva "época").</span><span class="sxs-lookup"><span data-stu-id="a2f36-362">Input time can be obtained from known epoch times (usually available on the Internet) and are computed as the number of seconds since January 1, 1900 (until 2036 when a new ‘epoch’ will be started.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-363">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-363">Input Parameters</span></span>

- <span data-ttu-id="a2f36-364">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-364">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="a2f36-365">**seconds**: componente de segundos de la entrada de hora.</span><span class="sxs-lookup"><span data-stu-id="a2f36-365">**seconds** Seconds component of the time input</span></span>

- <span data-ttu-id="a2f36-366">**fraction**: componente de subsegundos en el formato de fracción de SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-366">**fraction** Subseconds component in the SNTP fraction format</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-367">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-367">Return Values</span></span>

- <span data-ttu-id="a2f36-368">**NX_SUCCESS**: (0x00) hora local establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-368">**NX_SUCCESS** (0x00) Successfully set local time</span></span>

- <span data-ttu-id="a2f36-369">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-369">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-370">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-370">Allowed From</span></span>

<span data-ttu-id="a2f36-371">Inicialización</span><span class="sxs-lookup"><span data-stu-id="a2f36-371">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-372">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-372">Example</span></span>

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a><span data-ttu-id="a2f36-373">nx_sntp_client_set_time_update_notify</span><span class="sxs-lookup"><span data-stu-id="a2f36-373">nx_sntp_client_set_time_update_notify</span></span>

<span data-ttu-id="a2f36-374">Establece la devolución de llamada de la actualización de SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-374">Set the SNTP update callback</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-375">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-375">Prototype</span></span>

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a><span data-ttu-id="a2f36-376">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-376">Description</span></span>

<span data-ttu-id="a2f36-377">Este servicio establece una devolución de llamada para notificar a la aplicación cuando el cliente SNTP reciba una actualización de hora válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-377">This service sets callback to notify the application when the SNTP Client receives a valid time update.</span></span> <span data-ttu-id="a2f36-378">Proporciona la hora local del mensaje SNTP y del cliente SNTP (normalmente la misma) en formato NTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-378">It supplies the actual SNTP message and the SNTP Client’s local time (usually the same) in NTP format.</span></span> <span data-ttu-id="a2f36-379">La aplicación puede usar los datos NTP directamente o llamar al *servicio nx_sntp_client_utility_display_date_time* para convertir la hora a un formato en lenguaje natural.</span><span class="sxs-lookup"><span data-stu-id="a2f36-379">The application can use the NTP data directly or call the *nx_sntp_client_utility_display_date_time service* to convert the time to human readable format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-380">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-380">Input Parameters</span></span>

- <span data-ttu-id="a2f36-381">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-381">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="a2f36-382">**time_update_cb**: puntero a la función de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="a2f36-382">**time_update_cb** Pointer to callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-383">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-383">Return Values</span></span>

- <span data-ttu-id="a2f36-384">**NX_SUCCESS**: (0x00) devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-384">**NX_SUCCESS** (0x00) Successfully set callback</span></span>

- <span data-ttu-id="a2f36-385">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-385">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-386">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-386">Allowed From</span></span>

<span data-ttu-id="a2f36-387">Inicialización</span><span class="sxs-lookup"><span data-stu-id="a2f36-387">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-388">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-388">Example</span></span>

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a><span data-ttu-id="a2f36-389">nx_sntp_client_stop</span><span class="sxs-lookup"><span data-stu-id="a2f36-389">nx_sntp_client_stop</span></span>

<span data-ttu-id="a2f36-390">Detiene el subproceso del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-390">Stop the SNTP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-391">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-391">Prototype</span></span>

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="a2f36-392">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-392">Description</span></span>

<span data-ttu-id="a2f36-393">Este servicio detiene el subproceso del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-393">This service stops the SNTP Client thread.</span></span> <span data-ttu-id="a2f36-394">Las tareas de subproceso del cliente SNTP, que se ejecutan en un bucle infinito, se pausan en cada iteración para liberar el control del estado del cliente SNTP y permitir que las aplicaciones realicen llamadas API al cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-394">The SNTP Client thread tasks, which runs in an infinite loop, pauses on every iteration to release control of the SNTP Client state and allow applications to make API calls on the SNTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-395">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-395">Input Parameters</span></span>

- <span data-ttu-id="a2f36-396">**client_ptr**: puntero al bloque de control del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-396">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-397">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-397">Return Values</span></span>

- <span data-ttu-id="a2f36-398">**NX_SUCCESS**: (0x00) subproceso de cliente correctamente detenido.</span><span class="sxs-lookup"><span data-stu-id="a2f36-398">**NX_SUCCESS** (0x00) Successful stopped Client thread</span></span>

- <span data-ttu-id="a2f36-399">**NX_SNTP_CLIENT_NOT_STARTED**: (0xDB) no se ha iniciado el subproceso del cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP Client thread not started</span></span>

- <span data-ttu-id="a2f36-400">NX_PTR_ERROR: (0x07) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-400">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-401">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-401">Allowed From</span></span>

<span data-ttu-id="a2f36-402">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-402">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-403">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-403">Example</span></span>

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a><span data-ttu-id="a2f36-404">nx_sntp_client_utility_display_date_time</span><span class="sxs-lookup"><span data-stu-id="a2f36-404">nx_sntp_client_utility_display_date_time</span></span>

<span data-ttu-id="a2f36-405">Convierte una hora NTP en una cadena de fecha y hora.</span><span class="sxs-lookup"><span data-stu-id="a2f36-405">Convert an NTP Time to Date and Time string</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-406">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-406">Prototype</span></span>

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a><span data-ttu-id="a2f36-407">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-407">Description</span></span>

<span data-ttu-id="a2f36-408">Este servicio convierte la hora local del cliente SNTP al formato de año, mes y día, y devuelve la fecha en el búfer proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a2f36-408">This service converts the SNTP Client local time to a year month date format and returns the date in the supplied buffer.</span></span> <span data-ttu-id="a2f36-409">No es necesario que el valor de NX_SNTP_CURRENT_YEAR sea el mismo año que el de la hora actual del cliente, pero debe definirse.</span><span class="sxs-lookup"><span data-stu-id="a2f36-409">The NX_SNTP_CURRENT_YEAR need not be the same year as the current Client time but it must be defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-410">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-410">Input Parameters</span></span>

- <span data-ttu-id="a2f36-411">**client_ptr**: puntero al cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-411">**client_ptr Pointer to SNTP Client**</span></span>

- <span data-ttu-id="a2f36-412">**buffer**: puntero al búfer para almacenar la fecha.</span><span class="sxs-lookup"><span data-stu-id="a2f36-412">**buffer** Pointer to buffer to store date</span></span>

- <span data-ttu-id="a2f36-413">**length**: tamaño del búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="a2f36-413">**length** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-414">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-414">Return Values</span></span>

- <span data-ttu-id="a2f36-415">**NX_SUCCESS**: (0x00) conversión correcta.</span><span class="sxs-lookup"><span data-stu-id="a2f36-415">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="a2f36-416">**NX_SNTP_ERROR_CONVERTING_DATETIME**: (0xD08) no se ha definido NX_SNTP_CURRENT_YEAR o no se ha establecido la hora del cliente local.</span><span class="sxs-lookup"><span data-stu-id="a2f36-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR not defined or no local client time established</span></span>

- <span data-ttu-id="a2f36-417">**NX_SNTP_INVALID_DATETIME_BUFFER**: (0xD07) tamaño de búfer insuficiente.</span><span class="sxs-lookup"><span data-stu-id="a2f36-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Insufficient buffer length</span></span>


### <a name="allowed-from"></a><span data-ttu-id="a2f36-418">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-418">Allowed From</span></span>

<span data-ttu-id="a2f36-419">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-419">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-420">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-420">Example</span></span>

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a><span data-ttu-id="a2f36-421">nx_sntp_client_utility_msecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="a2f36-421">nx_sntp_client_utility_msecs_to_fraction</span></span>

<span data-ttu-id="a2f36-422">Convierte milisegundos a un componente de fracción de NTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-422">Convert milliseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-423">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-423">Prototype</span></span>

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a><span data-ttu-id="a2f36-424">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-424">Description</span></span>

<span data-ttu-id="a2f36-425">Este servicio convierte los milisegundos de la entrada al componente de fracción de NTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-425">This service converts the input milliseconds to the NTP fraction component.</span></span> <span data-ttu-id="a2f36-426">Está diseñado para usarse con aplicaciones que tienen una hora base de inicio para el cliente SNTP pero no en formato de segundos/fracción de NTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-426">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="a2f36-427">El número de milisegundos debe ser inferior a 1000 para crear una fracción válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-427">The number of milliseconds must be less than 1000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-428">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-428">Input Parameters</span></span>

- <span data-ttu-id="a2f36-429">**milliseconds**: milisegundos que se van a convertir.</span><span class="sxs-lookup"><span data-stu-id="a2f36-429">**milliseconds Milliseconds to convert**</span></span>

- <span data-ttu-id="a2f36-430">**fraction**: puntero a los milisegundos convertidos a fracción.</span><span class="sxs-lookup"><span data-stu-id="a2f36-430">**fraction** Pointer to milliseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-431">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-431">Return Values</span></span>

- <span data-ttu-id="a2f36-432">**NX_SUCCESS**: (0x00) conversión correcta.</span><span class="sxs-lookup"><span data-stu-id="a2f36-432">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="a2f36-433">**NX_SNTP_OVERFLOW_ERROR**: (0xD32) error al convertir la hora a una fecha.</span><span class="sxs-lookup"><span data-stu-id="a2f36-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="a2f36-434">NX_SNTP_INVALID_TIME: (0xD30) entrada de datos de SNTP no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-434">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-435">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-435">Allowed From</span></span>

<span data-ttu-id="a2f36-436">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-436">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-437">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-437">Example</span></span>

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a><span data-ttu-id="a2f36-438">nx_sntp_client_utility_usecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="a2f36-438">nx_sntp_client_utility_usecs_to_fraction</span></span>

<span data-ttu-id="a2f36-439">Convierte microsegundos a un componente de fracción de NTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-439">Convert microseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-440">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-440">Prototype</span></span>

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a><span data-ttu-id="a2f36-441">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-441">Description</span></span>

<span data-ttu-id="a2f36-442">Este servicio convierte los microsegundos de la entrada al componente de fracción de NTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-442">This service converts the input microseconds to the NTP fraction component.</span></span> <span data-ttu-id="a2f36-443">Está diseñado para usarse con aplicaciones que tienen una hora base de inicio para el cliente SNTP pero no en formato de segundos/fracción de NTP.</span><span class="sxs-lookup"><span data-stu-id="a2f36-443">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="a2f36-444">El número de microsegundos debe ser inferior a 1 000 000 para crear una fracción válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-444">The number of microseconds must be less than 1000000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-445">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-445">Input Parameters</span></span>

- <span data-ttu-id="a2f36-446">**microseconds**: microsegundos que se van a convertir.</span><span class="sxs-lookup"><span data-stu-id="a2f36-446">**microseconds** Microseconds to convert</span></span>

- <span data-ttu-id="a2f36-447">**fraction**: puntero a los microsegundos convertidos a fracción.</span><span class="sxs-lookup"><span data-stu-id="a2f36-447">**fraction** Pointer to microseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-448">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-448">Return Values</span></span>

- <span data-ttu-id="a2f36-449">**NX_SUCCESS**: (0x00) conversión correcta.</span><span class="sxs-lookup"><span data-stu-id="a2f36-449">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="a2f36-450">**NX_SNTP_OVERFLOW_ERROR**: (0xD32) error al convertir la hora a una fecha.</span><span class="sxs-lookup"><span data-stu-id="a2f36-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="a2f36-451">NX_SNTP_INVALID_TIME: (0xD30) entrada de datos de SNTP no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-451">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-452">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-452">Allowed From</span></span>

<span data-ttu-id="a2f36-453">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-453">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-454">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-454">Example</span></span>

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a><span data-ttu-id="a2f36-455">nx_sntp_client_utility_fraction_to_usecs</span><span class="sxs-lookup"><span data-stu-id="a2f36-455">nx_sntp_client_utility_fraction_to_usecs</span></span>

<span data-ttu-id="a2f36-456">Convierte un componente de fracción de NTP a microsegundos.</span><span class="sxs-lookup"><span data-stu-id="a2f36-456">Convert an NTP fraction component to microseconds</span></span>

### <a name="prototype"></a><span data-ttu-id="a2f36-457">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a2f36-457">Prototype</span></span>

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a><span data-ttu-id="a2f36-458">Descripción</span><span class="sxs-lookup"><span data-stu-id="a2f36-458">Description</span></span>

<span data-ttu-id="a2f36-459">Este servicio convierte el componente de fracción de NTP de la entrada a microsegundos.</span><span class="sxs-lookup"><span data-stu-id="a2f36-459">This service converts the input NTP fraction component to microseconds.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a2f36-460">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="a2f36-460">Input Parameters</span></span>

- <span data-ttu-id="a2f36-461">**fraction**: fracción que se va a convertir.</span><span class="sxs-lookup"><span data-stu-id="a2f36-461">**fraction Fraction to convert**</span></span>

- <span data-ttu-id="a2f36-462">**microseconds**: puntero a la fracción convertida en microsegundos.</span><span class="sxs-lookup"><span data-stu-id="a2f36-462">**microseconds** Pointer to fraction converted to microseconds</span></span>

### <a name="return-values"></a><span data-ttu-id="a2f36-463">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a2f36-463">Return Values</span></span>

- <span data-ttu-id="a2f36-464">**NX_SUCCESS**: (0x00) conversión correcta.</span><span class="sxs-lookup"><span data-stu-id="a2f36-464">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="a2f36-465">NX_SNTP_INVALID_TIME: (0xD30) entrada de datos de SNTP no válida.</span><span class="sxs-lookup"><span data-stu-id="a2f36-465">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a2f36-466">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="a2f36-466">Allowed From</span></span>

<span data-ttu-id="a2f36-467">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="a2f36-467">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a2f36-468">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a2f36-468">Example</span></span>

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```