---
title: 'Capítulo 3: Descripción de los servicios HTTP de NetX Duo para Azure RTOS'
description: Este capítulo contiene una descripción de todos los servicios HTTP de NetX Duo para Azure RTOS (enumerados a continuación) en orden alfabético, excepto el equivalente a "NetX" (solo IPv4) del mismo servicio, que se emparejan juntos.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 703071cd5a1d0677a3e995fccfe35d8b1dbbd9f3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814698"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a><span data-ttu-id="b132d-103">Capítulo 3: Descripción de los servicios HTTP de NetX Duo para Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="b132d-103">Chapter 3 - Description of Azure RTOS NetX Duo HTTP Services</span></span>

<span data-ttu-id="b132d-104">Este capítulo contiene una descripción de todos los servicios HTTP de NetX Duo para Azure RTOS (enumerados a continuación) en orden alfabético, excepto el equivalente a "NetX" (solo IPv4) del mismo servicio, que se emparejan juntos.</span><span class="sxs-lookup"><span data-stu-id="b132d-104">This chapter contains a description of all Azure RTOS NetX Duo HTTP services (listed below) in alphabetical order except for the ‘NetX’ (IPv4 only) equivalent of the same service are paired together).</span></span>

<span data-ttu-id="b132d-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en NEGRITA no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="b132d-105">In the “Return Values” section in the following API descriptions, values in BOLD are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="b132d-106">**Servicios de cliente HTTP:**</span><span class="sxs-lookup"><span data-stu-id="b132d-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="b132d-107">**nx_http_client_create** *Crear una instancia de cliente HTTP*</span><span class="sxs-lookup"><span data-stu-id="b132d-107">**nx_http_client_create** *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="b132d-108">**nx_http_client_delete** *Eliminar una instancia de cliente HTTP*</span><span class="sxs-lookup"><span data-stu-id="b132d-108">**nx_http_client_delete** *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="b132d-109">**nx_http_client_get_start** *Iniciar una solicitud HTTP GET (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="b132d-109">**nx_http_client_get_start** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="b132d-110">**nx_http_client_get_start_extended** *Iniciar una solicitud HTTP GET (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="b132d-110">**nx_http_client_get_start_extended** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="b132d-111">**nxd_http_client_get_start** *Iniciar una solicitud HTTP GET (IPv4 o IPv6)*</span><span class="sxs-lookup"><span data-stu-id="b132d-111">**nxd_http_client_get_start** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="b132d-112">**nxd_http_client_get_start_extended** *Iniciar una solicitud HTTP GET (IPv4 o IPv6)*</span><span class="sxs-lookup"><span data-stu-id="b132d-112">**nxd_http_client_get_start_extended** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="b132d-113">**nx_http_client_get_packet** *Obtener el siguiente paquete de datos de recursos*</span><span class="sxs-lookup"><span data-stu-id="b132d-113">**nx_http_client_get_packet** *Get next resource data packet*</span></span>
- <span data-ttu-id="b132d-114">**nx_http_client_put_start** *Iniciar una solicitud HTTP PUT (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="b132d-114">**nx_http_client_put_start** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="b132d-115">**nx_http_client_put_start_extended** *Iniciar una solicitud HTTP PUT (solo IPv4)*</span><span class="sxs-lookup"><span data-stu-id="b132d-115">**nx_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="b132d-116">**nxd_http_client_put_start** *Iniciar una solicitud HTTP PUT (IPv4 o IPv6)*</span><span class="sxs-lookup"><span data-stu-id="b132d-116">**nxd_http_client_put_start** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="b132d-117">**nxd_http_client_put_start_extended** *Iniciar una solicitud HTTP PUT (IPv4 o IPv6)*</span><span class="sxs-lookup"><span data-stu-id="b132d-117">**nxd_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="b132d-118">**nx_http_client_put_packet** *Enviar el siguiente paquete de datos de recursos*</span><span class="sxs-lookup"><span data-stu-id="b132d-118">**nx_http_client_put_packet** *Send next resource data packet*</span></span>
- <span data-ttu-id="b132d-119">**nx_http_client_set_connect_port** *Cambiar el puerto para conectarse al servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="b132d-119">**nx_http_client_set_connect_port** *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="b132d-120">**Servicios de servidor HTTP:**</span><span class="sxs-lookup"><span data-stu-id="b132d-120">**HTTP server services:**</span></span>

- <span data-ttu-id="b132d-121">**nx_http_server_cache_info_callback_set** *Establecer la devolución de llamada para recuperar la fecha de vencimiento y última modificación de la dirección URL especificada*</span><span class="sxs-lookup"><span data-stu-id="b132d-121">**nx_http_server_cache_info_callback_set** *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="b132d-122">**nx_http_server_callback_data_send** *Enviar datos HTTP desde la función de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="b132d-122">**nx_http_server_callback_data_send** *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="b132d-123">**nx_http_server_callback_generate_response_header** *Crear un encabezado de respuesta en funciones de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="b132d-123">**nx_http_server_callback_generate_response_header** *Create response header in callback functions*</span></span>
- <span data-ttu-id="b132d-124">**nx_http_server_callback_generate_response_header_extended** *Crear un encabezado de respuesta en funciones de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="b132d-124">**nx_http_server_callback_generate_response_header_extended** *Create response header in callback functions*</span></span>
- <span data-ttu-id="b132d-125">**nx_http_server_callback_packet_send** *Enviar un paquete HTTP desde una devolución de llamada HTTP*</span><span class="sxs-lookup"><span data-stu-id="b132d-125">**nx_http_server_callback_packet_send** *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="b132d-126">**nx_http_server_callback_response_send** *Enviar una respuesta desde la función de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="b132d-126">**nx_http_server_callback_response_send** *Send response from callback function*</span></span>
- <span data-ttu-id="b132d-127">**nx_http_server_callback_response_send_extended** *Enviar una respuesta desde la función de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="b132d-127">**nx_http_server_callback_response_send_extended** *Send response from callback function*</span></span>
- <span data-ttu-id="b132d-128">**nx_http_server_content_get** *Obtener contenido de la solicitud*</span><span class="sxs-lookup"><span data-stu-id="b132d-128">**nx_http_server_content_get** *Get content from the request*</span></span>
- <span data-ttu-id="b132d-129">**nx_http_server_content_get_extended** *Obtener contenido de la solicitud; admite solicitudes vacías (longitud de contenido cero)*</span><span class="sxs-lookup"><span data-stu-id="b132d-129">**nx_http_server_content_get_extended** *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="b132d-130">**nx_http_server_content_length_get** *Obtener longitud de contenido de la solicitud*</span><span class="sxs-lookup"><span data-stu-id="b132d-130">**nx_http_server_content_length_get** *Get length of content in the request*</span></span>
- <span data-ttu-id="b132d-131">**nx_http_server_content_length_get_extended** *Obtener longitud de contenido de la solicitud; admite solicitudes vacías (longitud de contenido cero)*</span><span class="sxs-lookup"><span data-stu-id="b132d-131">**nx_http_server_content_length_get_extended** *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="b132d-132">**nx_http_server_create** *Crear una instancia de servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="b132d-132">**nx_http_server_create** *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="b132d-133">**nx_http_server_delete** Eliminar una instancia de servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="b132d-133">**nx_http_server_delete** \* Delete an HTTP Server instance\*</span></span>
- <span data-ttu-id="b132d-134">**nx_http_server_get_entity_content** *Devolver tamaño y ubicación del contenido de la entidad en la dirección URL*</span><span class="sxs-lookup"><span data-stu-id="b132d-134">**nx_http_server_get_entity_content** *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="b132d-135">**nx_http_server_get_entity_header** *Extraer encabezado de entidad URL en el búfer especificado*</span><span class="sxs-lookup"><span data-stu-id="b132d-135">**nx_http_server_get_entity_header** *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="b132d-136">**nx_http_server_gmt_callback_set** *Establecer devolución de llamada para recuperar la fecha y hora GMT*</span><span class="sxs-lookup"><span data-stu-id="b132d-136">**nx_http_server_gmt_callback_set** *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="b132d-137">**nx_http_server_invalid_userpassword_notify_set** *Establecer devolución de llamada para cuando se recibe un nombre de usuario y una contraseña no válidos en una solicitud de cliente*</span><span class="sxs-lookup"><span data-stu-id="b132d-137">**nx_http_server_invalid_userpassword_notify_set** *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="b132d-138">**nx_http_server_mime_maps_additional_set** *Definir asignaciones MIME adicionales para HTML*</span><span class="sxs-lookup"><span data-stu-id="b132d-138">**nx_http_server_mime_maps_additional_set** *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="b132d-139">**nx_http_server_packet_content_find** *Extraer longitud de contenido en el encabezado HTTP y establecer puntero en el inicio de los datos de contenido*</span><span class="sxs-lookup"><span data-stu-id="b132d-139">**nx_http_server_packet_content_find** *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="b132d-140">**nx_http_server_packet_get** *Recibir paquete de cliente directamente*</span><span class="sxs-lookup"><span data-stu-id="b132d-140">**nx_http_server_packet_get** *Receive client packet directly*</span></span>
- <span data-ttu-id="b132d-141">**nx_http_server_param_get** *Obtener parámetro de la solicitud*</span><span class="sxs-lookup"><span data-stu-id="b132d-141">**nx_http_server_param_get** *Get parameter from the request*</span></span>
- <span data-ttu-id="b132d-142">**nx_http_server_query_get** *Obtener consulta de la solicitud*</span><span class="sxs-lookup"><span data-stu-id="b132d-142">**nx_http_server_query_get** *Get query from the request*</span></span>
- <span data-ttu-id="b132d-143">**nx_http_server_start** *Iniciar el servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="b132d-143">**nx_http_server_start** *Start the HTTP Server*</span></span>
- <span data-ttu-id="b132d-144">**nx_http_server_stop** *Detener el servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="b132d-144">**nx_http_server_stop** *Stop the HTTP Server*</span></span>
- <span data-ttu-id="b132d-145">**nx_http_server_type_get (en desuso)** *Extraer tipo HTTP, por ejemplo, texto/sin formato*</span><span class="sxs-lookup"><span data-stu-id="b132d-145">**nx_http_server_type_get (deprecated)** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="b132d-146">**nx_http_server_type_get_extended** *Extraer tipo HTTP, por ejemplo, texto/sin formato*</span><span class="sxs-lookup"><span data-stu-id="b132d-146">**nx_http_server_type_get_extended** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="b132d-147">**nx_http_server_digest_authenticate_notify_set** *Establecer función de devolución de llamada de autenticación implícita*</span><span class="sxs-lookup"><span data-stu-id="b132d-147">**nx_http_server_digest_authenticate_notify_set** *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="b132d-148">**nx_http_server_authentication_check_set** *Establecer función de devolución de llamada de comprobación de autenticación*</span><span class="sxs-lookup"><span data-stu-id="b132d-148">**nx_http_server_authentication_check_set** *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="b132d-149">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="b132d-149">nx_http_client_create</span></span>

<span data-ttu-id="b132d-150">Crear una instancia de cliente de PPPoE</span><span class="sxs-lookup"><span data-stu-id="b132d-150">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-151">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-151">Prototype</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="b132d-152">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-152">Description</span></span>

<span data-ttu-id="b132d-153">Este servicio crea una instancia de cliente HTTP en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="b132d-153">This service creates an HTTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-154">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-154">Input Parameters</span></span>

 - <span data-ttu-id="b132d-155">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-155">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-156">**client_name** Nombre de la instancia de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-156">**client_name** Name of HTTP Client instance.</span></span>
 - <span data-ttu-id="b132d-157">**ip_ptr** Puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="b132d-157">**ip_ptr** Pointer to IP instance.</span></span>
 - <span data-ttu-id="b132d-158">**pool_ptr** Puntero al grupo de paquetes predeterminado.</span><span class="sxs-lookup"><span data-stu-id="b132d-158">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="b132d-159">Tenga en cuenta que los paquetes de este grupo deben tener una carga útil lo suficientemente grande como para controlar el encabezado de respuesta completo.</span><span class="sxs-lookup"><span data-stu-id="b132d-159">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="b132d-160">Se define mediante NX_HTTP_CLIENT_MIN_PACKET_SIZE en *nx_http. h*.</span><span class="sxs-lookup"><span data-stu-id="b132d-160">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http.h*.</span></span>
 - <span data-ttu-id="b132d-161">**window_size** Tamaño de la ventana de recepción del socket TCP del cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-161">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-162">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-162">Return Values</span></span>

 - <span data-ttu-id="b132d-163">**NX_SUCCESS** (0x00) Se creó correctamente el cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-163">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
 - <span data-ttu-id="b132d-164">NX_PTR_ERROR (0x07) Puntero HTTP, ip_ptr o de grupo de paquetes no válido</span><span class="sxs-lookup"><span data-stu-id="b132d-164">NX_PTR_ERROR (0x07) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
 - <span data-ttu-id="b132d-165">NX_HTTP_POOL_ERROR (0xE9) Tamaño de carga no válido en el grupo de paquetes</span><span class="sxs-lookup"><span data-stu-id="b132d-165">NX_HTTP_POOL_ERROR (0xE9) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-166">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-166">Allowed From</span></span>

<span data-ttu-id="b132d-167">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-167">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-168">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-168">Example</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="b132d-169">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="b132d-169">nx_http_client_delete</span></span>

<span data-ttu-id="b132d-170">Eliminar una instancia de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="b132d-170">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-171">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-171">Prototype</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="b132d-172">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-172">Description</span></span>

<span data-ttu-id="b132d-173">Este servicio elimina una instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-173">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-174">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-174">Input Parameters</span></span>

 - <span data-ttu-id="b132d-175">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-175">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-176">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-176">Return Values</span></span>

 - <span data-ttu-id="b132d-177">**NX_SUCCESS** (0x00) Se eliminó correctamente el cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-177">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
 - <span data-ttu-id="b132d-178">NX_PTR_ERROR (0x07) Puntero HTTP no válido</span><span class="sxs-lookup"><span data-stu-id="b132d-178">NX_PTR_ERROR (0x07) Invalid HTTP pointer</span></span>
 - <span data-ttu-id="b132d-179">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-179">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-180">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-180">Allowed From</span></span>

<span data-ttu-id="b132d-181">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-181">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-182">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-182">Example</span></span>

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="b132d-183">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="b132d-183">nx_http_client_get_start</span></span>

<span data-ttu-id="b132d-184">Iniciar una solicitud HTTP GET mediante IPv4</span><span class="sxs-lookup"><span data-stu-id="b132d-184">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-185">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-185">Prototype</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-186">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-186">Description</span></span>

<span data-ttu-id="b132d-187">Este servicio intenta crear y enviar una solicitud GET con el recurso especificado por el puntero "resource" en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-187">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="b132d-188">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-188">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-189">La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="b132d-189">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="b132d-190">Este servicio solo funciona a través de la red IPv4.</span><span class="sxs-lookup"><span data-stu-id="b132d-190">This service works only over IPv4 network.</span></span> <span data-ttu-id="b132d-191">En el caso de las aplicaciones que necesitan conectarse a la red IPv6, se debe usar *nxd_http_client_get_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-191">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="b132d-192">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-192">This service is deprecated.</span></span> <span data-ttu-id="b132d-193">Se recomienda a los desarrolladores migrar a *nx_http_client_get_start_extended()* o *nxd_http_client_get_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-193">Developers are encouraged to migrate to *nx_http_client_get_start_extended()* or *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-194">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-194">Input Parameters</span></span>

 - <span data-ttu-id="b132d-195">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-195">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-196">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-196">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-197">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-197">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="b132d-198">**input_ptr** Puntero a datos adicionales para la solicitud GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-198">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="b132d-199">Esto es opcional.</span><span class="sxs-lookup"><span data-stu-id="b132d-199">This is optional.</span></span> <span data-ttu-id="b132d-200">Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-200">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="b132d-201">**input_size** Número de bytes en la entrada adicional opcional a la que apunta ```input_ptr```.</span><span class="sxs-lookup"><span data-stu-id="b132d-201">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="b132d-202">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-202">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-203">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-203">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-204">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio GET del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-204">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="b132d-205">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-205">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="b132d-206">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-206">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-208">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-208">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-209">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-209">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-210">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-210">Return Values</span></span>

 - <span data-ttu-id="b132d-211">**NX_SUCCESS** (0x00) Cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-211">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="b132d-212">Mensaje de inicio GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-212">GET start message.</span></span>
 - <span data-ttu-id="b132d-213">**NX_HTTP_ERROR** (0xE0) Error interno del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-213">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="b132d-214">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="b132d-214">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="b132d-215">**NX_HTTP_FAILED** (0xE2) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-215">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="b132d-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="b132d-217">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-217">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-218">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="b132d-218">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-219">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-219">Allowed From</span></span>

<span data-ttu-id="b132d-220">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-221">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-221">Example</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="b132d-222">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="b132d-222">nx_http_client_get_start_extended</span></span>

<span data-ttu-id="b132d-223">Iniciar una solicitud HTTP GET mediante IPv4</span><span class="sxs-lookup"><span data-stu-id="b132d-223">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-224">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-224">Prototype</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-225">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-225">Description</span></span>

<span data-ttu-id="b132d-226">Este servicio intenta crear y enviar una solicitud GET con el recurso especificado por el puntero "resource" en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-226">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="b132d-227">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-227">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-228">La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="b132d-228">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="b132d-229">Este servicio solo funciona a través de la red IPv4.</span><span class="sxs-lookup"><span data-stu-id="b132d-229">This service works only over IPv4 network.</span></span> <span data-ttu-id="b132d-230">En el caso de las aplicaciones que necesitan conectarse a la red IPv6, se debe usar *nxd_http_client_get_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-230">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="b132d-231">Este servicio reemplaza a *nx_http_client_get_start()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-231">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="b132d-232">Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="b132d-232">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-233">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-233">Input Parameters</span></span>

 - <span data-ttu-id="b132d-234">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-234">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-235">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-235">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-236">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-236">**resource Pointer** to URL string for requested resource.</span></span>
 - <span data-ttu-id="b132d-237">**resource_length** Longitud de la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-237">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="b132d-238">**input_ptr** Puntero a datos adicionales para la solicitud GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-238">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="b132d-239">Esto es opcional.</span><span class="sxs-lookup"><span data-stu-id="b132d-239">This is optional.</span></span> <span data-ttu-id="b132d-240">Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-240">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="b132d-241">**input_size** Número de bytes en la entrada adicional opcional a la que apunta ```input_ptr```.</span><span class="sxs-lookup"><span data-stu-id="b132d-241">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="b132d-242">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-242">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-243">**username_length** Longitud del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-243">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-244">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-244">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-245">**password_length** Longitud de la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-245">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-246">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio GET del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-246">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="b132d-247">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="b132d-248">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-248">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-250">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-250">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-251">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-251">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-252">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-252">Return Values</span></span>

 - <span data-ttu-id="b132d-253">**NX_SUCCESS** (0x00) Cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-253">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="b132d-254">Mensaje de inicio GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-254">GET start message</span></span>
 - <span data-ttu-id="b132d-255">**NX_HTTP_ERROR** (0xE0) Error interno del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-255">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="b132d-256">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="b132d-256">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="b132d-257">**NX_HTTP_FAILED** (0xE2) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-257">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="b132d-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="b132d-259">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-259">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-260">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="b132d-260">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-261">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-261">Allowed From</span></span>

<span data-ttu-id="b132d-262">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-262">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-263">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-263">Example</span></span>

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a><span data-ttu-id="b132d-264">nxd_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="b132d-264">nxd_http_client_get_start</span></span>

<span data-ttu-id="b132d-265">Enviar una solicitud HTTP GET (IPv4 o IPv6)</span><span class="sxs-lookup"><span data-stu-id="b132d-265">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-266">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-266">Prototype</span></span>

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-267">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-267">Description</span></span>

<span data-ttu-id="b132d-268">Este servicio intenta crear y enviar una solicitud GET con el recurso especificado por el puntero "resource" en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-268">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="b132d-269">Se puede usar para conectarse a una red IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="b132d-269">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="b132d-270">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-270">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
><span data-ttu-id="b132d-271">La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="b132d-271">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="b132d-272">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-272">This service is deprecated.</span></span> <span data-ttu-id="b132d-273">Se recomienda a los desarrolladores migrar a *nxd_http_client_get_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-273">Developers are encouraged to migrate to *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-274">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-274">Input Parameters</span></span>

 - <span data-ttu-id="b132d-275">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-275">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-276">**Server_ip** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-276">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-277">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-277">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="b132d-278">**input_ptr** Puntero a datos adicionales para la solicitud GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-278">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="b132d-279">Esto es opcional.</span><span class="sxs-lookup"><span data-stu-id="b132d-279">This is optional.</span></span> <span data-ttu-id="b132d-280">Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-280">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="b132d-281">**input_size** Número de bytes en la entrada adicional opcional a la que apunta ```input_ptr```.</span><span class="sxs-lookup"><span data-stu-id="b132d-281">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="b132d-282">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-282">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-283">**username_length** Longitud del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-283">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-284">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-284">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-285">**password_length** Longitud de la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-285">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-286">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio GET del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-286">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="b132d-287">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-287">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="b132d-288">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-288">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-290">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-290">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-291">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-291">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-292">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-292">Return Values</span></span>

 - <span data-ttu-id="b132d-293">**NX_SUCCESS** (0x00) Solicitud GET enviada correctamente</span><span class="sxs-lookup"><span data-stu-id="b132d-293">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="b132d-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) La contraseña supera el tamaño del búfer.</span><span class="sxs-lookup"><span data-stu-id="b132d-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="b132d-295">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="b132d-295">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="b132d-296">**NX_HTTP_FAILED** (0xE2) Parámetros de paquete no válidos.</span><span class="sxs-lookup"><span data-stu-id="b132d-296">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="b132d-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos</span><span class="sxs-lookup"><span data-stu-id="b132d-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="b132d-298">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-298">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-299">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-299">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-300">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-300">Allowed From</span></span>

<span data-ttu-id="b132d-301">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-302">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-302">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a><span data-ttu-id="b132d-303">nxd_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="b132d-303">nxd_http_client_get_start_extended</span></span>

<span data-ttu-id="b132d-304">Enviar una solicitud HTTP GET (IPv4 o IPv6)</span><span class="sxs-lookup"><span data-stu-id="b132d-304">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-305">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-305">Prototype</span></span>

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-306">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-306">Description</span></span>

<span data-ttu-id="b132d-307">Este servicio intenta crear y enviar una solicitud GET con el recurso especificado por el puntero "resource" en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-307">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="b132d-308">Se puede usar para conectarse a una red IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="b132d-308">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="b132d-309">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-309">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-310">La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="b132d-310">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="b132d-311">Este servicio reemplaza a *nxd_http_client_get_start()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-311">This service replaces *nxd_http_client_get_start()*.</span></span> <span data-ttu-id="b132d-312">Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="b132d-312">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-313">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-313">Input Parameters</span></span>

 - <span data-ttu-id="b132d-314">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-314">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-315">**Server_ip** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-315">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-316">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-316">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="b132d-317">**resource_length** Longitud de la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-317">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="b132d-318">**input_ptr** Puntero a datos adicionales para la solicitud GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-318">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="b132d-319">Esto es opcional.</span><span class="sxs-lookup"><span data-stu-id="b132d-319">This is optional.</span></span> <span data-ttu-id="b132d-320">Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.</span><span class="sxs-lookup"><span data-stu-id="b132d-320">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="b132d-321">**input_size** Número de bytes en la entrada adicional opcional a la que apunta ```input_ptr```.</span><span class="sxs-lookup"><span data-stu-id="b132d-321">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="b132d-322">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-322">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-323">**username_length** Longitud del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-323">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-324">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-324">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-325">**password_length** Longitud de la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-325">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-326">**wait_option** Define cuánto tiempo esperará el servicio internamente para procesar el inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-326">**wait_option** Defines how long the service will wait internally to process the HTTP Client get start.</span></span> <span data-ttu-id="b132d-327">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-327">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="b132d-328">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-328">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-330">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-330">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-331">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-331">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-332">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-332">Return Values</span></span>

 - <span data-ttu-id="b132d-333">**NX_SUCCESS** (0x00) Solicitud GET enviada correctamente</span><span class="sxs-lookup"><span data-stu-id="b132d-333">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="b132d-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) La contraseña supera el tamaño del búfer.</span><span class="sxs-lookup"><span data-stu-id="b132d-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="b132d-335">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="b132d-335">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="b132d-336">**NX_HTTP_FAILED** (0xE2) Parámetros de paquete no válidos.</span><span class="sxs-lookup"><span data-stu-id="b132d-336">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="b132d-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos</span><span class="sxs-lookup"><span data-stu-id="b132d-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="b132d-338">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-338">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-339">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-339">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-340">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-340">Allowed From</span></span>

<span data-ttu-id="b132d-341">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-342">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-342">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="b132d-343">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="b132d-343">nx_http_client_get_packet</span></span>

<span data-ttu-id="b132d-344">Obtener el siguiente paquete de datos de recursos</span><span class="sxs-lookup"><span data-stu-id="b132d-344">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-345">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-345">Prototype</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-346">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-346">Description</span></span>

<span data-ttu-id="b132d-347">Este servicio recupera el siguiente paquete de contenido del recurso solicitado por la llamada a *nx_http_client_get_start* anterior.</span><span class="sxs-lookup"><span data-stu-id="b132d-347">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="b132d-348">Deben realizarse llamadas sucesivas a esta rutina hasta que se reciba el estado de devolución de NX_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="b132d-348">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-349">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-349">Input Parameters</span></span>

 - <span data-ttu-id="b132d-350">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-350">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-351">**packet_ptr** Destino del puntero de paquete que contiene el contenido parcial del recurso.</span><span class="sxs-lookup"><span data-stu-id="b132d-351">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
 - <span data-ttu-id="b132d-352">**wait_option** Define cuánto tiempo esperará el servicio a que se obtenga el paquete del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-352">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="b132d-353">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-353">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="b132d-354">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-354">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-356">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-356">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-357">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-357">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-358">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-358">Return Values</span></span>

 - <span data-ttu-id="b132d-359">**NX_SUCCESS** (0x00) Se ha obtenido correctamente el paquete del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-359">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
 - <span data-ttu-id="b132d-360">**NX_HTTP_GET_DONE** (0xEC) Se ha realizado la obtención del paquete del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-360">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
 - <span data-ttu-id="b132d-361">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está en modo de obtención.</span><span class="sxs-lookup"><span data-stu-id="b132d-361">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
 - <span data-ttu-id="b132d-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Longitud de paquete no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="b132d-363">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-363">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-364">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-364">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-365">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-365">Allowed From</span></span>

<span data-ttu-id="b132d-366">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-366">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-367">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-367">Example</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="b132d-368">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="b132d-368">nx_http_client_put_start</span></span>

<span data-ttu-id="b132d-369">Iniciar una solicitud HTTP PUT a través de IPv4</span><span class="sxs-lookup"><span data-stu-id="b132d-369">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-370">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-370">Prototype</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-371">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-371">Description</span></span>

<span data-ttu-id="b132d-372">Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP proporcionada.</span><span class="sxs-lookup"><span data-stu-id="b132d-372">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="b132d-373">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet ()* para enviar realmente el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-373">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-374">La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o puede hacer referencia a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="b132d-374">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="b132d-375">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-375">This service is deprecated.</span></span> <span data-ttu-id="b132d-376">Se recomienda a los desarrolladores migrar a *nx_web_http_client_put_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-376">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-377">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-377">Input Parameters</span></span>

 - <span data-ttu-id="b132d-378">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-378">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-379">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-379">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-380">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-380">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="b132d-381">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-381">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-382">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-382">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-383">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="b132d-383">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="b132d-384">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="b132d-384">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="b132d-385">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-385">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="b132d-386">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-386">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="b132d-387">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-387">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-389">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-389">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-390">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-390">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-391">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-391">Return Values</span></span>

 - <span data-ttu-id="b132d-392">**NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-392">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="b132d-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) El nombre de usuario es demasiado largo para el búfer.</span><span class="sxs-lookup"><span data-stu-id="b132d-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="b132d-394">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="b132d-394">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="b132d-395">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-395">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-396">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-396">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="b132d-397">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-397">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-398">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-398">Allowed From</span></span>

<span data-ttu-id="b132d-399">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-400">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-400">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="b132d-401">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="b132d-401">nx_http_client_put_start_extended</span></span>

<span data-ttu-id="b132d-402">Iniciar una solicitud HTTP PUT a través de IPv4</span><span class="sxs-lookup"><span data-stu-id="b132d-402">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-403">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-403">Prototype</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-404">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-404">Description</span></span>

<span data-ttu-id="b132d-405">Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP proporcionada.</span><span class="sxs-lookup"><span data-stu-id="b132d-405">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="b132d-406">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet ()* para enviar realmente el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-406">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-407">La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o puede hacer referencia a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="b132d-407">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="b132d-408">Este servicio reemplaza a *nx_http_client_put_start()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-408">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="b132d-409">Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="b132d-409">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-410">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-410">Input Parameters</span></span>

 - <span data-ttu-id="b132d-411">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-411">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-412">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-412">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-413">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-413">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="b132d-414">**resource_length** Longitud de la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="b132d-414">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="b132d-415">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-415">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-416">**username_length** Longitud del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-416">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-417">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-417">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-418">**password_length** Longitud de la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-418">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-419">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="b132d-419">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="b132d-420">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="b132d-420">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="b132d-421">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-421">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="b132d-422">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-422">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="b132d-423">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-423">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-425">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-425">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-426">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-426">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-427">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-427">Return Values</span></span>

 - <span data-ttu-id="b132d-428">**NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-428">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="b132d-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) El nombre de usuario es demasiado largo para el búfer.</span><span class="sxs-lookup"><span data-stu-id="b132d-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="b132d-430">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="b132d-430">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="b132d-431">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-431">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-432">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-432">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="b132d-433">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-433">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-434">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-434">Allowed From</span></span>

<span data-ttu-id="b132d-435">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-436">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-436">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a><span data-ttu-id="b132d-437">nxd_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="b132d-437">nxd_http_client_put_start</span></span>

<span data-ttu-id="b132d-438">Iniciar una solicitud HTTP PUT (IPv4 o IPv6)</span><span class="sxs-lookup"><span data-stu-id="b132d-438">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-439">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-439">Prototype</span></span>

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-440">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-440">Description</span></span>

<span data-ttu-id="b132d-441">Este servicio intenta colocar (enviar) el recurso especificado en el servidor HTTP en la dirección IP proporcionada a través de IPv6.</span><span class="sxs-lookup"><span data-stu-id="b132d-441">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="b132d-442">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet ()* para enviar realmente el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-442">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-443">La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o puede hacer referencia a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="b132d-443">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="b132d-444">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-444">This service is deprecated.</span></span> <span data-ttu-id="b132d-445">Se recomienda a los desarrolladores migrar a *nx_web_http_client_put_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-445">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-446">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-446">Input Parameters</span></span>

 - <span data-ttu-id="b132d-447">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-447">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-448">**server_IP** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-448">**server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-449">**resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="b132d-449">**resource** Pointer to URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="b132d-450">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-450">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-451">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-451">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-452">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="b132d-452">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="b132d-453">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="b132d-453">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="b132d-454">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-454">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="b132d-455">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-455">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="b132d-456">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-456">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-458">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-458">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-459">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-459">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-460">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-460">Return Values</span></span>

 - <span data-ttu-id="b132d-461">**NX_SUCCESS** (0x00) Solicitud PUT del cliente HTTP enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-461">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="b132d-462">**NX_HTTP_ERROR** (0xE0) Error interno del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-462">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="b132d-463">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="b132d-463">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="b132d-464">**NX_HTTP_FAILED** (0xE2) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-464">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="b132d-465">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-465">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-466">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-466">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="b132d-467">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-468">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-468">Allowed From</span></span>

<span data-ttu-id="b132d-469">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-470">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-470">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a><span data-ttu-id="b132d-471">nxd_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="b132d-471">nxd_http_client_put_start_extended</span></span>

<span data-ttu-id="b132d-472">Iniciar una solicitud HTTP PUT (IPv4 o IPv6)</span><span class="sxs-lookup"><span data-stu-id="b132d-472">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-473">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-473">Prototype</span></span>

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-474">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-474">Description</span></span>

<span data-ttu-id="b132d-475">Este servicio intenta colocar (enviar) el recurso especificado en el servidor HTTP en la dirección IP proporcionada a través de IPv6.</span><span class="sxs-lookup"><span data-stu-id="b132d-475">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="b132d-476">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet ()* para enviar realmente el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-476">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-477">La cadena de recurso puede hacer referencia a un archivo local, por ejemplo, ``` “/index.htm” ```, o puede hacer referencia a otra dirección URL, por ejemplo, ```http://abc.website.com/index.htm``` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="b132d-477">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="b132d-478">Este servicio reemplaza a *nxd_http_client_put_start()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-478">This service replaces *nxd_http_client_put_start()*.</span></span> <span data-ttu-id="b132d-479">Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="b132d-479">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-480">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-480">Input Parameters</span></span>

 - <span data-ttu-id="b132d-481">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-481">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-482">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-482">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-483">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="b132d-483">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="b132d-484">**resource_length** Longitud de la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="b132d-484">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="b132d-485">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-485">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-486">**username_length** Longitud del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-486">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="b132d-487">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-487">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-488">**password_length** Longitud de la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-488">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="b132d-489">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="b132d-489">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="b132d-490">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="b132d-490">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="b132d-491">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-491">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="b132d-492">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-492">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="b132d-493">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-493">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-495">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-495">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-496">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-496">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-497">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-497">Return Values</span></span>

 - <span data-ttu-id="b132d-498">**NX_SUCCESS** (0x00) Solicitud PUT del cliente HTTP enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-498">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="b132d-499">**NX_HTTP_ERROR** (0xE0) Error interno del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-499">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="b132d-500">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="b132d-500">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="b132d-501">NX_HTTP_FAILED (0xE2) Error del cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-501">NX_HTTP_FAILED (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="b132d-502">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-502">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-503">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-503">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="b132d-504">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-504">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-505">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-505">Allowed From</span></span>

<span data-ttu-id="b132d-506">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-507">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-507">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="b132d-508">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="b132d-508">nx_http_client_put_packet</span></span>

<span data-ttu-id="b132d-509">Enviar el siguiente paquete de datos de recursos</span><span class="sxs-lookup"><span data-stu-id="b132d-509">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-510">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-510">Prototype</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="b132d-511">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-511">Description</span></span>

<span data-ttu-id="b132d-512">Este servicio intenta enviar el siguiente paquete de contenido de recursos al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-512">This service attempts to send the next packet of resource content to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-513">Se debe llamar a esta rutina repetidamente hasta que la longitud combinada de los paquetes enviados sea igual al valor de "total_bytes" especificado en la llamada a *nx_http_client_put_start* anterior.</span><span class="sxs-lookup"><span data-stu-id="b132d-513">This routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start* call.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-514">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-514">Input Parameters</span></span>

 - <span data-ttu-id="b132d-515">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-515">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-516">**packet_ptr** Puntero al siguiente contenido del recurso que se va a enviar al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-516">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
 - <span data-ttu-id="b132d-517">**WAIT_OPTION** Define cuánto tiempo esperará el servicio internamente para procesar el paquete PUT del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-517">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="b132d-518">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="b132d-518">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="b132d-519">**valor de tiempo de espera** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="b132d-519">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="b132d-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="b132d-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="b132d-521">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-521">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="b132d-522">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-522">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-523">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-523">Return Values</span></span>

 - <span data-ttu-id="b132d-524">**NX_SUCCESS** (0x00) Paquete de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-524">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
 - <span data-ttu-id="b132d-525">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="b132d-525">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="b132d-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Código de error del servidor recibido.</span><span class="sxs-lookup"><span data-stu-id="b132d-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code</span></span>
 - <span data-ttu-id="b132d-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Longitud de paquete no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="b132d-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="b132d-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
 - <span data-ttu-id="b132d-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) El servidor responde antes de que finalice PUT.</span><span class="sxs-lookup"><span data-stu-id="b132d-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
 - <span data-ttu-id="b132d-530">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-530">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-531">NX_INVALID_PACKET (0x12) El paquete es demasiado pequeño para el encabezado TCP.</span><span class="sxs-lookup"><span data-stu-id="b132d-531">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
 - <span data-ttu-id="b132d-532">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-532">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-533">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-533">Allowed From</span></span>

<span data-ttu-id="b132d-534">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-535">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-535">Example</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="b132d-536">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="b132d-536">nx_http_client_set_connect_port</span></span>

<span data-ttu-id="b132d-537">Establecer el puerto de conexión al servidor</span><span class="sxs-lookup"><span data-stu-id="b132d-537">Set the connection port to the Server</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-538">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-538">Prototype</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a><span data-ttu-id="b132d-539">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-539">Description</span></span>

<span data-ttu-id="b132d-540">Este servicio cambia el puerto de conexión al conectarse al servidor HTTP en el puerto especificado en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="b132d-540">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="b132d-541">De lo contrario, el puerto de conexión tiene como valor predeterminado 80.</span><span class="sxs-lookup"><span data-stu-id="b132d-541">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="b132d-542">Se debe llamar a este método antes de *nx_http_client_get_start()* y *nx_http_client_put_start()* , por ejemplo, cuando el cliente HTTP conecta con el servidor.</span><span class="sxs-lookup"><span data-stu-id="b132d-542">This must be called before *nx_http_client_get_start()* and *nx_http_client_put_start()* e.g. when the HTTP Client connects with the Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-543">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-543">Input Parameters</span></span>

 - <span data-ttu-id="b132d-544">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-544">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="b132d-545">**port** Puerto para la conexión al servidor.</span><span class="sxs-lookup"><span data-stu-id="b132d-545">**port** Port for connecting to the Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-546">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-546">Return Values</span></span>

 - <span data-ttu-id="b132d-547">**NX_SUCCESS** (0x00) Puerto cambiado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-547">**NX_SUCCESS** (0x00) Successfully change port</span></span>
 - <span data-ttu-id="b132d-548">NX_INVALID_PORT (0x46) El puerto supera el valor máximo (0xFFFF) o es cero.</span><span class="sxs-lookup"><span data-stu-id="b132d-548">NX_INVALID_PORT (0x46) Port exceeds the maximum (0xFFFF) or is zero</span></span>
 - <span data-ttu-id="b132d-549">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-549">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-550">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-550">Allowed From</span></span>

<span data-ttu-id="b132d-551">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="b132d-551">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="b132d-552">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-552">Example</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="b132d-553">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="b132d-553">nx_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="b132d-554">Establecer la devolución de llamada para recuperar la antigüedad máxima y la fecha de la dirección URL</span><span class="sxs-lookup"><span data-stu-id="b132d-554">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-555">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-555">Prototype</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a><span data-ttu-id="b132d-556">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-556">Description</span></span>

<span data-ttu-id="b132d-557">Este servicio establece el servicio de devolución de llamada invocado para obtener la antigüedad máxima y la fecha de última modificación del recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="b132d-557">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-558">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-558">Input Parameters</span></span>

 - <span data-ttu-id="b132d-559">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-559">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-560">**cache_info_get** Puntero a la devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="b132d-560">**cache_info_get** Pointer to the callback</span></span>
 - <span data-ttu-id="b132d-561">**max_age** Puntero a la antigüedad máxima de un recurso.</span><span class="sxs-lookup"><span data-stu-id="b132d-561">**max_age** Pointer to maximum age of a resource</span></span>
 - <span data-ttu-id="b132d-562">**data** Puntero a la fecha de última modificación devuelta.</span><span class="sxs-lookup"><span data-stu-id="b132d-562">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-563">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-563">Return Values</span></span>

 - <span data-ttu-id="b132d-564">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-564">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="b132d-565">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-565">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-566">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-566">Allowed From</span></span>

<span data-ttu-id="b132d-567">Inicialización</span><span class="sxs-lookup"><span data-stu-id="b132d-567">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="b132d-568">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-568">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="b132d-569">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="b132d-569">nx_http_server_callback_data_send</span></span>

<span data-ttu-id="b132d-570">Enviar datos desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="b132d-570">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-571">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-571">Prototype</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="b132d-572">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-572">Description</span></span>

<span data-ttu-id="b132d-573">Este servicio envía los datos del paquete proporcionado desde la rutina de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b132d-573">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="b132d-574">Normalmente se usa para enviar datos dinámicos asociados a solicitudes GET/POST.</span><span class="sxs-lookup"><span data-stu-id="b132d-574">This is typically used to send dynamic data associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-575">Si se usa esta función, la rutina de devolución de llamada es responsable de enviar la respuesta completa en el formato correcto.</span><span class="sxs-lookup"><span data-stu-id="b132d-575">If this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="b132d-576">Además, la rutina de devolución de llamada debe devolver el estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="b132d-576">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-577">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-577">Input Parameters</span></span>

 - <span data-ttu-id="b132d-578">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-578">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-579">**data_ptr** Puntero a los datos que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="b132d-579">**data_ptr** Pointer to the data to send.</span></span>
 - <span data-ttu-id="b132d-580">**data_length** Número de bytes que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="b132d-580">**data_length**  Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-581">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-581">Return Values</span></span>

 - <span data-ttu-id="b132d-582">**NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-582">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
 - <span data-ttu-id="b132d-583">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-583">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-584">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-584">Allowed From</span></span>

<span data-ttu-id="b132d-585">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-586">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-586">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="b132d-587">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="b132d-587">nx_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="b132d-588">Crear un encabezado de respuesta en una función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="b132d-588">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-589">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-589">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="b132d-590">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-590">Description</span></span>

<span data-ttu-id="b132d-591">Este servicio llama a la función interna *_nx_http_server_generate_response_header* cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE del cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-591">This service calls the internal function *_nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="b132d-592">Su uso está previsto en funciones de devolución de llamada de servidor HTTP cuando la aplicación de servidor HTTP está diseñando su respuesta al cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-592">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="b132d-593">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-593">This service is deprecated.</span></span> <span data-ttu-id="b132d-594">Se recomienda a los desarrolladores migrar a *nxd_http_server_callback_generate_response_header_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-594">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-595">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-595">Input Parameters</span></span>

 - <span data-ttu-id="b132d-596">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-596">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-597">**packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="b132d-597">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="b132d-598">**status_code** Indica el estado del recurso.</span><span class="sxs-lookup"><span data-stu-id="b132d-598">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="b132d-599">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="b132d-599">Examples:</span></span>
    - <span data-ttu-id="b132d-600">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="b132d-600">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="b132d-601">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="b132d-601">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="b132d-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="b132d-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="b132d-603">**content_length** Tamaño del contenido en bytes.</span><span class="sxs-lookup"><span data-stu-id="b132d-603">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="b132d-604">**content_type** Tipo de HTTP, por ejemplo, "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="b132d-604">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="b132d-605">**additional_header** Puntero a texto de encabezado adicional.</span><span class="sxs-lookup"><span data-stu-id="b132d-605">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-606">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-606">Return Values</span></span>

 - <span data-ttu-id="b132d-607">**NX_SUCCESS** (0x00) Encabezado creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-607">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="b132d-608">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-608">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-609">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-609">Allowed From</span></span>

<span data-ttu-id="b132d-610">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-610">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-611">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-611">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="b132d-612">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="b132d-612">nx_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="b132d-613">Crear un encabezado de respuesta en una función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="b132d-613">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-614">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-614">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header_extended(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT status_code_length,
                        UINT content_length,
                        CHAR *content_type, UINT content_type_length,
                        CHAR *additional_header,
                        UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="b132d-615">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-615">Description</span></span>

<span data-ttu-id="b132d-616">Este servicio llama a la función interna *_nx_http_server_generate_response_header* cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE del cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-616">This service calls the internal function *_nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="b132d-617">Su uso está previsto en funciones de devolución de llamada de servidor HTTP cuando la aplicación de servidor HTTP está diseñando su respuesta al cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-617">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="b132d-618">Este servicio reemplaza *nx_http_server_callback_generate_response_header()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-618">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="b132d-619">Esta versión proporciona información de longitud adicional a la función de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="b132d-619">This version supplies additional length information to the callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-620">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-620">Input Parameters</span></span>

 - <span data-ttu-id="b132d-621">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-621">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-622">**packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="b132d-622">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="b132d-623">**status_code** Indica el estado del recurso.</span><span class="sxs-lookup"><span data-stu-id="b132d-623">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="b132d-624">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="b132d-624">Examples:</span></span>
    - <span data-ttu-id="b132d-625">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="b132d-625">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="b132d-626">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="b132d-626">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="b132d-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="b132d-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="b132d-628">**status_code** Longitud del código de estado.</span><span class="sxs-lookup"><span data-stu-id="b132d-628">**status_code** Length of status code</span></span>
 - <span data-ttu-id="b132d-629">**content_length** Tamaño del contenido en bytes.</span><span class="sxs-lookup"><span data-stu-id="b132d-629">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="b132d-630">**content_type** Tipo de HTTP, por ejemplo, "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="b132d-630">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="b132d-631">**content_type_length** Longitud del tipo HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-631">**content_type_length** Length of HTTP type</span></span>
 - <span data-ttu-id="b132d-632">**additional_header** Puntero a texto de encabezado adicional.</span><span class="sxs-lookup"><span data-stu-id="b132d-632">**additional_header** Pointer to additional header text</span></span>
 - <span data-ttu-id="b132d-633">**additional_header_length** Longitud del texto de encabezado adicional.</span><span class="sxs-lookup"><span data-stu-id="b132d-633">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-634">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-634">Return Values</span></span>

 - <span data-ttu-id="b132d-635">**NX_SUCCESS** (0x00) Encabezado creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-635">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="b132d-636">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-636">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-637">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-637">Allowed From</span></span>

<span data-ttu-id="b132d-638">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-638">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-639">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-639">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header_extended(
                             http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
              sizeof(NX_HTTP_STATUS_OK) - 1, length,
              temp_string, string_length, NX_NULL, 0);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="b132d-640">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="b132d-640">nx_http_server_callback_packet_send</span></span>

<span data-ttu-id="b132d-641">Enviar un paquete HTTP desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="b132d-641">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-642">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-642">Prototype</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="b132d-643">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-643">Description</span></span>

<span data-ttu-id="b132d-644">Este servicio envía una respuesta completa del servidor HTTP desde una devolución de llamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-644">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="b132d-645">El servidor HTTP enviará el paquete con NX_HTTP_SERVER_TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="b132d-645">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="b132d-646">El encabezado y los datos HTTP deben anexarse al paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-646">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="b132d-647">Si el estado devuelto indica un error, la aplicación HTTP debe liberar el paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-647">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="b132d-648">La devolución de llamada debe devolver NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="b132d-648">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="b132d-649">Consulte *nx_http_server_callback_generate_response_header()* para ver un ejemplo más detallado.</span><span class="sxs-lookup"><span data-stu-id="b132d-649">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-650">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-650">Input Parameters</span></span>

 - <span data-ttu-id="b132d-651">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-651">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-652">**packet_ptr** Puntero al paquete que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="b132d-652">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-653">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-653">Return Values</span></span>

 - <span data-ttu-id="b132d-654">**NX_SUCCESS** (0x00) Paquete del servidor enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-654">**NX_SUCCESS** (0x00) Successfully sent Server packet</span></span>
 - <span data-ttu-id="b132d-655">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-655">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-656">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-656">Allowed From</span></span>

<span data-ttu-id="b132d-657">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-657">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-658">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-658">Example</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="b132d-659">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="b132d-659">nx_http_server_callback_response_send</span></span>

<span data-ttu-id="b132d-660">Enviar una respuesta desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="b132d-660">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-661">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-661">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="b132d-662">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-662">Description</span></span>

<span data-ttu-id="b132d-663">Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b132d-663">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="b132d-664">Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST.</span><span class="sxs-lookup"><span data-stu-id="b132d-664">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-665">Si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="b132d-665">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="b132d-666">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-666">This service is deprecated.</span></span> <span data-ttu-id="b132d-667">Se recomienda a los desarrolladores migrar a *nxd_http_server_callback_response_send_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-667">Developers are encouraged to migrate to *nxd_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-668">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-668">Input Parameters</span></span>

 - <span data-ttu-id="b132d-669">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-669">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-670">**header** Puntero a la cadena de encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="b132d-670">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="b132d-671">**information** Puntero a la cadena de información.</span><span class="sxs-lookup"><span data-stu-id="b132d-671">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="b132d-672">**additional_info** Puntero a la cadena de información adicional.</span><span class="sxs-lookup"><span data-stu-id="b132d-672">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-673">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-673">Return Values</span></span>

 - <span data-ttu-id="b132d-674">**NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-674">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-675">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-675">Allowed From</span></span>

<span data-ttu-id="b132d-676">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-677">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-677">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send(server_ptr,
                      "HTTP/1.0 404 ",
                      "NetX HTTP Server unable to find  
                       file: ", resource);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="b132d-678">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="b132d-678">nx_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="b132d-679">Enviar una respuesta desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="b132d-679">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-680">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-680">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="b132d-681">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-681">Description</span></span>

<span data-ttu-id="b132d-682">Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b132d-682">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="b132d-683">Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST.</span><span class="sxs-lookup"><span data-stu-id="b132d-683">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-684">Si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="b132d-684">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="b132d-685">Este servicio reemplaza a *nx_http_server_callback_response_send()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-685">This service replaces *nx_http_server_callback_response_send()*.</span></span> <span data-ttu-id="b132d-686">Esta versión toma información de longitud adicional como argumentos.</span><span class="sxs-lookup"><span data-stu-id="b132d-686">This version takes additional length information as arguments.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-687">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-687">Input Parameters</span></span>

 - <span data-ttu-id="b132d-688">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-688">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-689">**header** Puntero a la cadena de encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="b132d-689">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="b132d-690">**header_length** Longitud de la cadena de encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="b132d-690">**header_length** Length of the response header string.</span></span>
 - <span data-ttu-id="b132d-691">**information** Puntero a la cadena de información.</span><span class="sxs-lookup"><span data-stu-id="b132d-691">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="b132d-692">**Information_length** Longitud de la cadena de información.</span><span class="sxs-lookup"><span data-stu-id="b132d-692">**information_length** Length of the information string.</span></span>
 - <span data-ttu-id="b132d-693">**additional_info** Puntero a la cadena de información adicional.</span><span class="sxs-lookup"><span data-stu-id="b132d-693">**additional_info** Pointer to the additional information string.</span></span>
 - <span data-ttu-id="b132d-694">**additional_info_length** Longitud de la cadena de información adicional.</span><span class="sxs-lookup"><span data-stu-id="b132d-694">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-695">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-695">Return Values</span></span>

 - <span data-ttu-id="b132d-696">**NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-696">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-697">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-697">Allowed From</span></span>

<span data-ttu-id="b132d-698">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-698">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-699">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-699">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="b132d-700">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="b132d-700">nx_http_server_content_get</span></span>

<span data-ttu-id="b132d-701">Obtener contenido de la solicitud</span><span class="sxs-lookup"><span data-stu-id="b132d-701">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-702">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-702">Prototype</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="b132d-703">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-703">Description</span></span>

<span data-ttu-id="b132d-704">Este servicio intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST o PUT.</span><span class="sxs-lookup"><span data-stu-id="b132d-704">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="b132d-705">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="b132d-705">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="b132d-706">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-706">This service is deprecated.</span></span> <span data-ttu-id="b132d-707">Se recomienda a los desarrolladores migrar a *nx_http_server_content_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-707">Developers are encouraged to migrate to *nx_http_server_content_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-708">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-708">Input Parameters</span></span>

 - <span data-ttu-id="b132d-709">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-709">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-710">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-710">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="b132d-711">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-711">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="b132d-712">**byte_offset** Número de bytes que se van a desplazar en el área de contenido.</span><span class="sxs-lookup"><span data-stu-id="b132d-712">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="b132d-713">**destination_ptr** Puntero al área de destino para el contenido.</span><span class="sxs-lookup"><span data-stu-id="b132d-713">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="b132d-714">**destination_size** Número máximo de bytes disponibles en el área de destino.</span><span class="sxs-lookup"><span data-stu-id="b132d-714">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="b132d-715">**actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.</span><span class="sxs-lookup"><span data-stu-id="b132d-715">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-716">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-716">Return Values</span></span>

 - <span data-ttu-id="b132d-717">**NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-717">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
 - <span data-ttu-id="b132d-718">**NX_HTTP_ERROR** (0xE0) Error interno del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-718">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="b132d-719">**NX_HTTP_DATA_END** (0xE7) Fin del contenido de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-719">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="b132d-720">**NX_WEB_HTTP_TIMEOUT** (0xE1) Tiempo de espera del servidor HTTP para obtener el siguiente paquete de contenido.</span><span class="sxs-lookup"><span data-stu-id="b132d-720">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
 - <span data-ttu-id="b132d-721">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-721">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-722">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-722">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-723">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-723">Allowed From</span></span>

<span data-ttu-id="b132d-724">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-724">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-725">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-725">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="b132d-726">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="b132d-726">nx_http_server_content_get_extended</span></span>

<span data-ttu-id="b132d-727">Obtener contenido de la solicitud (admite la longitud de contenido cero)</span><span class="sxs-lookup"><span data-stu-id="b132d-727">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-728">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-728">Prototype</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="b132d-729">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-729">Description</span></span>

<span data-ttu-id="b132d-730">Este servicio es casi idéntico a *nx_http_server_content_get();* intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST O PUT.</span><span class="sxs-lookup"><span data-stu-id="b132d-730">This service is almost identical to *nx_http_server_content_get();* it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="b132d-731">Sin embargo, administra las solicitudes con una longitud de contenido de valor cero ("solicitud vacía") como solicitud válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-731">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="b132d-732">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="b132d-732">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="b132d-733">Este servicio reemplaza a *nx_http_server_content_get()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-733">This service replaces *nx_http_server_content_get()*.</span></span> <span data-ttu-id="b132d-734">Esta versión requiere que el autor de la llamada proporcione información de longitud adicional.</span><span class="sxs-lookup"><span data-stu-id="b132d-734">This version requires caller to supply additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-735">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-735">Input Parameters</span></span>

 - <span data-ttu-id="b132d-736">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-736">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-737">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-737">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="b132d-738">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-738">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="b132d-739">**byte_offset** Número de bytes que se van a desplazar en el área de contenido.</span><span class="sxs-lookup"><span data-stu-id="b132d-739">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="b132d-740">**destination_ptr** Puntero al área de destino para el contenido.</span><span class="sxs-lookup"><span data-stu-id="b132d-740">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="b132d-741">**destination_size** Número máximo de bytes disponibles en el área de destino.</span><span class="sxs-lookup"><span data-stu-id="b132d-741">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="b132d-742">**actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.</span><span class="sxs-lookup"><span data-stu-id="b132d-742">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-743">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-743">Return Values</span></span>

 - <span data-ttu-id="b132d-744">**NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-744">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
 - <span data-ttu-id="b132d-745">**NX_HTTP_ERROR** (0xE0) Error interno del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-745">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="b132d-746">**NX_HTTP_DATA_END** (0xE7) Fin del contenido de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-746">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="b132d-747">**NX_WEB_HTTP_TIMEOUT** (0xE1) Tiempo de espera del servidor HTTP para obtener el siguiente paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-747">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
 - <span data-ttu-id="b132d-748">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-748">NX_PTR_ERROR (0x07) Invalid  pointer input</span></span>
 - <span data-ttu-id="b132d-749">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-749">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-750">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-750">Allowed From</span></span>

<span data-ttu-id="b132d-751">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-752">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-752">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="b132d-753">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="b132d-753">nx_http_server_content_length_get</span></span>

<span data-ttu-id="b132d-754">Obtener la longitud del contenido de la solicitud</span><span class="sxs-lookup"><span data-stu-id="b132d-754">Get length of content in the request</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-755">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-755">Prototype</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="b132d-756">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-756">Description</span></span>

<span data-ttu-id="b132d-757">Este servicio intenta recuperar la longitud del contenido HTTP en el paquete proporcionado.</span><span class="sxs-lookup"><span data-stu-id="b132d-757">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="b132d-758">Si no hay contenido HTTP, esta rutina devuelve un valor de cero.</span><span class="sxs-lookup"><span data-stu-id="b132d-758">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="b132d-759">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="b132d-759">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="b132d-760">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-760">This service is deprecated.</span></span> <span data-ttu-id="b132d-761">Se recomienda a los desarrolladores migrar a *nx_http_server_content_length_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-761">Developers are encouraged to migrate to *nx_http_server_content_length_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-762">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-762">Input Parameters</span></span>

 - <span data-ttu-id="b132d-763">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-763">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="b132d-764">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-764">Note that this packet must not be released by the request notify callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-765">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-765">Return Values</span></span>

 - <span data-ttu-id="b132d-766">**content length** Si hay error, se devuelve un valor de cero.</span><span class="sxs-lookup"><span data-stu-id="b132d-766">**content length** On error, a value of zero is returned</span></span>  

### <a name="allowed-from"></a><span data-ttu-id="b132d-767">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-767">Allowed From</span></span>

<span data-ttu-id="b132d-768">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-768">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-769">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-769">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="b132d-770">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="b132d-770">nx_http_server_content_length_get_extended</span></span>

<span data-ttu-id="b132d-771">Obtener la longitud del contenido de la solicitud (admite la longitud de contenido de valor cero)</span><span class="sxs-lookup"><span data-stu-id="b132d-771">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-772">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-772">Prototype</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="b132d-773">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-773">Description</span></span>

<span data-ttu-id="b132d-774">Este servicio es similar a *nx_http_server_content_length_get;* intenta recuperar la longitud del contenido HTTP en el paquete proporcionado.</span><span class="sxs-lookup"><span data-stu-id="b132d-774">This service is similar to *nx_http_server_content_length_get;* attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="b132d-775">Sin embargo, el valor devuelto indica el estado de finalización correcta y el valor de longitud real se devuelve en el puntero de ```content_length```.</span><span class="sxs-lookup"><span data-stu-id="b132d-775">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer ```content_length```.</span></span> <span data-ttu-id="b132d-776">Si no hay contenido HTTP/longitud de contenido = 0, esta rutina sigue devolviendo un estado de finalización correcta y el puntero de entrada content_length apunta a una longitud válida (cero).</span><span class="sxs-lookup"><span data-stu-id="b132d-776">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="b132d-777">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="b132d-777">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="b132d-778">Este servicio reemplaza a *nx_http_server_content_length_get()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-778">This service replaces *nx_http_server_content_length_get()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-779">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-779">Input Parameters</span></span>

 - <span data-ttu-id="b132d-780">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-780">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="b132d-781">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-781">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="b132d-782">**CONTENT_LENGTH** Puntero al valor recuperado del campo de longitud de contenido.</span><span class="sxs-lookup"><span data-stu-id="b132d-782">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-783">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-783">Return Values</span></span>

 - <span data-ttu-id="b132d-784">**NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-784">**NX_SUCCESS** (0x00) Successful Server content get</span></span>
 - <span data-ttu-id="b132d-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Formato de encabezado HTTP incorrecto</span><span class="sxs-lookup"><span data-stu-id="b132d-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
 - <span data-ttu-id="b132d-786">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-786">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-787">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-787">Allowed From</span></span>

<span data-ttu-id="b132d-788">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-789">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-789">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="b132d-790">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="b132d-790">nx_http_server_create</span></span>

<span data-ttu-id="b132d-791">Crear una instancia de servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="b132d-791">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-792">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-792">Prototype</span></span>

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
      CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
      VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, CHAR **name,
            CHAR **password, CHAR **realm),
      UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="b132d-793">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-793">Description</span></span>

<span data-ttu-id="b132d-794">Este servicio crea una instancia de servidor HTTP que se ejecuta en el contexto de su propio subproceso ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b132d-794">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="b132d-795">Las rutinas de devolución de llamada de aplicación opcionales *authentication_check* y request_notify proporcionan al software de aplicación control sobre las operaciones básicas del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-795">The optional *authentication_check* and request_notify application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-796">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-796">Input Parameters</span></span>

 - <span data-ttu-id="b132d-797">**http_server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-797">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="b132d-798">**http_server_name** Puntero al nombre del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-798">**http_server_name** Pointer to HTTP Server’s name.</span></span>
 - <span data-ttu-id="b132d-799">**ip_ptr** Puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-799">**ip_ptr** Pointer to previously created IP instance.</span></span>
 - <span data-ttu-id="b132d-800">**media_ptr** Puntero a la instancia de medios FileX creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-800">**media_ptr** Pointer to previously created FileX media instance.</span></span>
 - <span data-ttu-id="b132d-801">**stack_ptr** Puntero al área de la pila de subprocesos del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-801">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
 - <span data-ttu-id="b132d-802">**stack_size** Puntero al tamaño de la pila de subprocesos del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-802">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
 - <span data-ttu-id="b132d-803">**authentication_check** Puntero de función a la rutina de comprobación de autenticación de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b132d-803">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="b132d-804">Si se especifica, se llama a esta rutina para cada solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-804">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="b132d-805">Si este parámetro es NULL, no se realizará ninguna autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-805">If this parameter is NULL, no authentication will be performed.</span></span>
 - <span data-ttu-id="b132d-806">**request_notify** Puntero de función a la rutina de notificación de solicitud de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b132d-806">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="b132d-807">Si se especifica, se llama a esta rutina antes de que se procese el servidor HTTP de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="b132d-807">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="b132d-808">Esto permite que se redirija el nombre del recurso o que los campos de un recurso se actualicen antes de completar la solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-808">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-809">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-809">Return Values</span></span>

 - <span data-ttu-id="b132d-810">**NX_SUCCESS**: (0x00) Servidor HTTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-810">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
 - <span data-ttu-id="b132d-811">NX_PTR_ERROR (0x07) El puntero de servidor HTTP, dirección IP, medio, pila o grupo de paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-811">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
 - <span data-ttu-id="b132d-812">NX_HTTP_POOL_ERROR (0xE9) La carga de paquetes del grupo no es lo suficientemente grande como para contener una solicitud HTTP completa.</span><span class="sxs-lookup"><span data-stu-id="b132d-812">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-813">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-813">Allowed From</span></span>

<span data-ttu-id="b132d-814">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-814">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-815">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-815">Example</span></span>

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="b132d-816">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="b132d-816">nx_http_server_delete</span></span>

<span data-ttu-id="b132d-817">Eliminar una instancia de servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="b132d-817">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-818">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-818">Prototype</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="b132d-819">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-819">Description</span></span>

<span data-ttu-id="b132d-820">Este servicio elimina una instancia de servidor HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-820">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-821">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-821">Input Parameters</span></span>

 - <span data-ttu-id="b132d-822">**http_server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-822">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-823">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-823">Return Values</span></span>

 - <span data-ttu-id="b132d-824">**NX_SUCCESS**: (0x00) Servidor HTTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-824">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
 - <span data-ttu-id="b132d-825">NX_PTR_ERROR (0x07) Puntero de servidor HTTP no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-825">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
 - <span data-ttu-id="b132d-826">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-827">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-827">Allowed From</span></span>

<span data-ttu-id="b132d-828">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-828">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-829">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-829">Example</span></span>

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="b132d-830">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="b132d-830">nx_http_server_get_entity_content</span></span>

<span data-ttu-id="b132d-831">Recuperar la ubicación y la longitud de los datos de entidad</span><span class="sxs-lookup"><span data-stu-id="b132d-831">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-832">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-832">Prototype</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="b132d-833">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-833">Description</span></span>

<span data-ttu-id="b132d-834">Este servicio determina la ubicación del inicio de los datos dentro de la entidad actual de varias partes en los mensajes de cliente recibidos y la longitud de los datos que no incluyen la cadena de límite.</span><span class="sxs-lookup"><span data-stu-id="b132d-834">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="b132d-835">Internamente, el servidor HTTP actualiza sus propios desplazamientos para que se pueda volver a llamar a esta función en el mismo datagrama de cliente para mensajes con varias entidades.</span><span class="sxs-lookup"><span data-stu-id="b132d-835">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="b132d-836">El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.</span><span class="sxs-lookup"><span data-stu-id="b132d-836">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-837">NX_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio.</span><span class="sxs-lookup"><span data-stu-id="b132d-837">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="b132d-838">Para más información, consulte [*nx_web_http_server_get_entity_header*](#nx_http_server_get_entity_header).</span><span class="sxs-lookup"><span data-stu-id="b132d-838">See [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-839">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-839">Input Parameters</span></span>

 - <span data-ttu-id="b132d-840">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-840">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="b132d-841">**packet_pptr** Puntero a la ubicación del puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-841">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="b132d-842">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-842">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="b132d-843">**available_offset** Puntero para desplazar los datos de entidad desde el puntero de anteposición del paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-843">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
 - <span data-ttu-id="b132d-844">**available_length** Puntero a la longitud de los datos de entidad.</span><span class="sxs-lookup"><span data-stu-id="b132d-844">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-845">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-845">Return Values</span></span>

 - <span data-ttu-id="b132d-846">**NX_SUCCESS** (0x00) Tamaño y ubicación del contenido de la entidad recuperados correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-846">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
 - <span data-ttu-id="b132d-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Ya se encontró el contenido interno de los marcadores de varias partes del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server  internal multipart markers is already found</span></span>
 - <span data-ttu-id="b132d-848">NX_HTTP_ERROR (0xE0) Error de HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="b132d-848">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="b132d-849">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-849">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-850">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-850">Allowed From</span></span>

<span data-ttu-id="b132d-851">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-851">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-852">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-852">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="b132d-853">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="b132d-853">nx_http_server_get_entity_header</span></span>

<span data-ttu-id="b132d-854">Recuperar el contenido del encabezado de entidad</span><span class="sxs-lookup"><span data-stu-id="b132d-854">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-855">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-855">Prototype</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="b132d-856">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-856">Description</span></span>

<span data-ttu-id="b132d-857">Este servicio recupera el encabezado de entidad en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="b132d-857">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="b132d-858">Internamente, el servidor HTTP actualiza sus propios punteros para localizar la siguiente entidad de varias partes en un datagrama de cliente con varios encabezados de entidad.</span><span class="sxs-lookup"><span data-stu-id="b132d-858">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="b132d-859">El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.</span><span class="sxs-lookup"><span data-stu-id="b132d-859">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-860">NX_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio.</span><span class="sxs-lookup"><span data-stu-id="b132d-860">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-861">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-861">Input Parameters</span></span>

 - <span data-ttu-id="b132d-862">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-862">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="b132d-863">**packet_pptr** Puntero a la ubicación del puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-863">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="b132d-864">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-864">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="b132d-865">**entity_header_buffer** Puntero a la ubicación donde se va a almacenar el encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="b132d-865">**entity_header_buffer** Pointer to location to store entity header</span></span>
 - <span data-ttu-id="b132d-866">**buffer_size** Tamaño del búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="b132d-866">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-867">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-867">Return Values</span></span>

 - <span data-ttu-id="b132d-868">**NX_SUCCESS** (0x00) Encabezado de entidad recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-868">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
 - <span data-ttu-id="b132d-869">**NX_HTTP_NOT_FOUND** **(0xE6)** No se encontró el campo de encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="b132d-869">**NX_HTTP_NOT_FOUND** **(0xE6)** Entity header field not found</span></span>
 - <span data-ttu-id="b132d-870">**NX_HTTP_TIMEOUT** **(0xE1)** Se agotó el tiempo para recibir el siguiente paquete del mensaje de cliente de varios paquetes.</span><span class="sxs-lookup"><span data-stu-id="b132d-870">**NX_HTTP_TIMEOUT** **(0xE1)** Time expired to receive next packet for multipacket client message</span></span>
 - <span data-ttu-id="b132d-871">NX_HTTP_ERROR (0xE0) Error de HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="b132d-871">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="b132d-872">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-872">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-873">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-873">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-874">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-874">Allowed From</span></span>

<span data-ttu-id="b132d-875">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-875">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-876">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-876">Example</span></span>

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

        /* Process multipart data. */
        if(request_type == NX_HTTP_SERVER_POST_REQUEST)
        {

       /* Get the content header. */
       while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                         sizeof(buffer)) == NX_SUCCESS)
   {

      /* Header obtained successfully. Get the content data location. */
      while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                              &length) == NX_SUCCESS)
      {
           /* Write content data to buffer. */
           nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
           buffer[length] = 0;
      }

    }

    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
                         &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
  NX_SUCCESS)
 {
                nx_packet_release(response_pkt);
     }
    }


}
else
{
    /* Indicate we have not processed the response to client yet.*/
    return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="b132d-877">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="b132d-877">nx_http_server_gmt_callback_set</span></span>

<span data-ttu-id="b132d-878">Establecer la devolución de llamada para obtener la fecha y hora GMT.</span><span class="sxs-lookup"><span data-stu-id="b132d-878">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-879">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-879">Prototype</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="b132d-880">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-880">Description</span></span>

<span data-ttu-id="b132d-881">Este servicio establece la devolución de llamada para obtener la fecha y hora GMT con un servidor HTTP creado previamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-881">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="b132d-882">Este servicio se invoca con el servidor HTTP y crea un encabezado en las respuestas del servidor HTTP al cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-882">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-883">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-883">Input Parameters</span></span>

 - <span data-ttu-id="b132d-884">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-884">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="b132d-885">**gmt_get** Puntero a la devolución de llamada GMT.</span><span class="sxs-lookup"><span data-stu-id="b132d-885">**gmt_getv** Pointer to GMT callback</span></span>
 - <span data-ttu-id="b132d-886">**date** Puntero a la fecha de recuperación.</span><span class="sxs-lookup"><span data-stu-id="b132d-886">**datev** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-887">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-887">Return Values</span></span>

 - <span data-ttu-id="b132d-888">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-888">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="b132d-889">NX_PTR_ERROR (0x07) Puntero de paquete o parámetro no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-889">NX_PTR_ERROR (0x07)  Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-890">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-890">Allowed From</span></span>

<span data-ttu-id="b132d-891">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-892">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-892">Example</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="b132d-893">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="b132d-893">nx_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="b132d-894">Establecer la devolución de llamada para controlar la contraseña o el usuario no válidos</span><span class="sxs-lookup"><span data-stu-id="b132d-894">Set the callback to to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-895">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-895">Prototype</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="b132d-896">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-896">Description</span></span>

<span data-ttu-id="b132d-897">Este servicio establece la devolución de llamada invocada cuando se recibe un nombre de usuario y una contraseña no válidos en una solicitud de cliente GET, PUT o DELETE, ya sea mediante autenticación implícita o básica.</span><span class="sxs-lookup"><span data-stu-id="b132d-897">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="b132d-898">El servidor HTTP se debe crear previamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-898">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-899">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-899">Input Parameters</span></span>

 - <span data-ttu-id="b132d-900">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-900">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="b132d-901">**invalid_username_password_callback** Puntero a una devolución de llamada de aprobación/usuario no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-901">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
 - <span data-ttu-id="b132d-902">**resource** Puntero al recurso especificado por el cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-902">**resource** Pointer to the resource specified by the client</span></span>
 - <span data-ttu-id="b132d-903">**client_address** Puntero a la dirección del cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-903">**client_address** Pointer to client address.</span></span> <span data-ttu-id="b132d-904">Puede ser IPv4 o IPv6.</span><span class="sxs-lookup"><span data-stu-id="b132d-904">Can be IPv4 or IPv6</span></span>
 - <span data-ttu-id="b132d-905">**request_type** Indica el tipo de solicitud de cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-905">**request_type** Indicates client request type.</span></span> <span data-ttu-id="b132d-906">Puede ser:</span><span class="sxs-lookup"><span data-stu-id="b132d-906">May be:</span></span>
    - <span data-ttu-id="b132d-907">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="b132d-907">NX_HTTP_SERVER_GET_REQUEST</span></span>
    - <span data-ttu-id="b132d-908">NX_HTTP_SERVER_POST_REQUEST</span><span class="sxs-lookup"><span data-stu-id="b132d-908">NX_HTTP_SERVER_POST_REQUEST</span></span>
    - <span data-ttu-id="b132d-909">NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="b132d-909">NX_HTTP_SERVER_HEAD_REQUEST</span></span>
    - <span data-ttu-id="b132d-910">NX_HTTP_SERVER_PUT_REQUEST</span><span class="sxs-lookup"><span data-stu-id="b132d-910">NX_HTTP_SERVER_PUT_REQUEST</span></span>
    - <span data-ttu-id="b132d-911">NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="b132d-911">NX_HTTP_SERVER_DELETE_REQUEST</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-912">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-912">Return Values</span></span>

 - <span data-ttu-id="b132d-913">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-913">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="b132d-914">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-914">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-915">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-915">Allowed From</span></span>

<span data-ttu-id="b132d-916">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-916">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-917">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-917">Example</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="b132d-918">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="b132d-918">nx_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="b132d-919">Establecer asignaciones MIME adicionales para HTML</span><span class="sxs-lookup"><span data-stu-id="b132d-919">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-920">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-920">Prototype</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="b132d-921">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-921">Description</span></span>

<span data-ttu-id="b132d-922">Este servicio permite al desarrollador de aplicaciones HTTP agregar tipos MIME adicionales de los tipos MIME predeterminados proporcionados por el servidor NetX Duo HTTP (consulte *nx_http_server_get_type* para ver una lista de tipos definidos).</span><span class="sxs-lookup"><span data-stu-id="b132d-922">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX Duo HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="b132d-923">Cuando se recibe una solicitud de cliente, por ejemplo, una solicitud GET, el servidor HTTP analiza el tipo de archivo solicitado del encabezado HTTP mediante el conjunto de asignaciones MIME adicional y, si no se encuentra ninguna coincidencia, busca una coincidencia en la asignación MIME predeterminada del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-923">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="b132d-924">Si no se encuentra ninguna coincidencia, el tipo MIME tiene como valor predeterminado "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="b132d-924">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="b132d-925">Si la función de notificación de solicitud se registra con el servidor HTTP, la devolución de llamada de solicitud de notificación puede llamar a *nx_http_server_type_retrieve()* para analizar el tipo de archivo.</span><span class="sxs-lookup"><span data-stu-id="b132d-925">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_retrieve()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-926">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-926">Input Parameters</span></span>

 - <span data-ttu-id="b132d-927">**server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-927">**server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="b132d-928">**mime_maps** Puntero a una matriz de asignaciones MIME.</span><span class="sxs-lookup"><span data-stu-id="b132d-928">**mime_maps** Pointer to a MIME map array</span></span>
 - <span data-ttu-id="b132d-929">**mime_map_num** Número de asignaciones MIME en la matriz.</span><span class="sxs-lookup"><span data-stu-id="b132d-929">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-930">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-930">Return Values</span></span>

 - <span data-ttu-id="b132d-931">**NX_SUCCESS**: (0x00) Asignación MIME de servidor HTTP establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-931">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
 - <span data-ttu-id="b132d-932">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-932">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-933">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-933">Allowed From</span></span>

<span data-ttu-id="b132d-934">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-934">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-935">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-935">Example</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="b132d-936">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="b132d-936">nx_http_server_packet_content_find</span></span>

<span data-ttu-id="b132d-937">Extraer la longitud del contenido y establecer el puntero en el inicio de los datos</span><span class="sxs-lookup"><span data-stu-id="b132d-937">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-938">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-938">Prototype</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="b132d-939">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-939">Description</span></span>

<span data-ttu-id="b132d-940">Este servicio extrae la longitud del contenido del encabezado HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-940">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="b132d-941">También actualiza el paquete proporcionado de la siguiente manera: el puntero de anteposición del paquete (inicio de la ubicación del búfer de paquetes en el que se va a escribir) se establece en el contenido HTTP (datos) que se acaba de pasar al encabezado HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-941">It also  updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="b132d-942">Si no se encuentra el principio del contenido en el paquete actual, la función espera a que se reciba el siguiente paquete mediante la opción de espera NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="b132d-942">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-943">No se debe llamar a esta función antes que a *nx_web_http_server_get_entity_header()* , ya que modifica el puntero de anteposición más allá del encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="b132d-943">This should not be called before calling *nx_http_server_get_entity_header* because it modifies the prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-944">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-944">Input Parameters</span></span>

 - <span data-ttu-id="b132d-945">**server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-945">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="b132d-946">**packet_ptr** Puntero al puntero de paquete para devolver el paquete con el puntero de anteposición actualizado.</span><span class="sxs-lookup"><span data-stu-id="b132d-946">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
 - <span data-ttu-id="b132d-947">**CONTENT_LENGTH** Puntero al valor de ```content_length``` extraído.</span><span class="sxs-lookup"><span data-stu-id="b132d-947">**content_length** Pointer to extracted ```content_length```</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-948">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-948">Return Values</span></span>

 - <span data-ttu-id="b132d-949">**NX_SUCCESS** (0x00) Se encontró la longitud del contenido HTTP y el paquete se actualizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-949">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
 - <span data-ttu-id="b132d-950">**NX_HTTP_TIMEOUT** (0xE1) Tiempo agotado esperando al siguiente paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-950">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="b132d-951">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-951">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-952">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-952">Allowed From</span></span>

<span data-ttu-id="b132d-953">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-953">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-954">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-954">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="b132d-955">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="b132d-955">nx_http_server_packet_get</span></span>

<span data-ttu-id="b132d-956">Recibir el siguiente paquete HTTP</span><span class="sxs-lookup"><span data-stu-id="b132d-956">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-957">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-957">Prototype</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="b132d-958">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-958">Description</span></span>

<span data-ttu-id="b132d-959">Este servicio devuelve el siguiente paquete recibido en el socket de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-959">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="b132d-960">La opción de espera para recibir un paquete es NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="b132d-960">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-961">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-961">Input Parameters</span></span>

 - <span data-ttu-id="b132d-962">**server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-962">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="b132d-963">**packet_ptr** Puntero al paquete recibido.</span><span class="sxs-lookup"><span data-stu-id="b132d-963">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-964">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-964">Return Values</span></span>

 - <span data-ttu-id="b132d-965">**NX_SUCCESS** (0x00) Siguiente paquete recibido correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-965">**NX_SUCCESS** (0x00) Successfully received next packet</span></span>
 - <span data-ttu-id="b132d-966">**NX_HTTP_TIMEOUT** (0xE1) Tiempo agotado esperando al siguiente paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-966">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="b132d-967">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-967">NX_PTR_ERROR (0x07)  Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-968">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-968">Allowed From</span></span>

<span data-ttu-id="b132d-969">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-969">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-970">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-970">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="b132d-971">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="b132d-971">nx_http_server_param_get</span></span>

<span data-ttu-id="b132d-972">Obtener el parámetro de la solicitud</span><span class="sxs-lookup"><span data-stu-id="b132d-972">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-973">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-973">Prototype</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="b132d-974">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-974">Description</span></span>

<span data-ttu-id="b132d-975">Este servicio intenta recuperar el parámetro de dirección URL HTTP especificado en el paquete de solicitud proporcionado.</span><span class="sxs-lookup"><span data-stu-id="b132d-975">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="b132d-976">Si el parámetro HTTP solicitado no está presente, esta rutina devuelve un estado de NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="b132d-976">If the requested HTTP parameter is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="b132d-977">Se debe llamar a esta rutina desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="b132d-977">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-978">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-978">Input Parameters</span></span>

 - <span data-ttu-id="b132d-979">**packet_ptr** Puntero al paquete de solicitud del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-979">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="b132d-980">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-980">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="b132d-981">**param_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de parámetros.</span><span class="sxs-lookup"><span data-stu-id="b132d-981">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
 - <span data-ttu-id="b132d-982">**param_ptr** Área de destino para copiar el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b132d-982">**param_ptr** Destination area to copy the parameter.</span></span>
 - <span data-ttu-id="b132d-983">**max_param_size** Tamaño máximo del área de destino del parámetro.</span><span class="sxs-lookup"><span data-stu-id="b132d-983">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-984">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-984">Return Values</span></span>

 - <span data-ttu-id="b132d-985">**NX_SUCCESS** (0X00) Parámetro del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-985">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
 - <span data-ttu-id="b132d-986">**NX_WEB_HTTP_NOT_FOUND** (0xE6) Parámetro especificado no encontrado.</span><span class="sxs-lookup"><span data-stu-id="b132d-986">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
 - <span data-ttu-id="b132d-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Parámetro de solicitud no terminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
 - <span data-ttu-id="b132d-988">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-988">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-989">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-989">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-990">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-990">Allowed From</span></span>

<span data-ttu-id="b132d-991">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-991">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-992">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-992">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="b132d-993">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="b132d-993">nx_http_server_query_get</span></span>

<span data-ttu-id="b132d-994">Obtener consulta de la solicitud</span><span class="sxs-lookup"><span data-stu-id="b132d-994">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-995">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-995">Prototype</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="b132d-996">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-996">Description</span></span>

<span data-ttu-id="b132d-997">Este servicio intenta recuperar la consulta de dirección URL HTTP especificada en el paquete de solicitud proporcionado.</span><span class="sxs-lookup"><span data-stu-id="b132d-997">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="b132d-998">Si la consulta HTTP solicitada no está presente, esta rutina devuelve un estado de NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="b132d-998">If the requested HTTP query is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="b132d-999">Se debe llamar a esta rutina desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="b132d-999">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-1000">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-1000">Input Parameters</span></span>

 - <span data-ttu-id="b132d-1001">**packet_ptr** Puntero al paquete de solicitud del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-1001">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="b132d-1002">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="b132d-1002">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="b132d-1003">**query_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de consultas.</span><span class="sxs-lookup"><span data-stu-id="b132d-1003">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
 - <span data-ttu-id="b132d-1004">**query_ptr** Área de destino en la que se va a copiar la consulta.</span><span class="sxs-lookup"><span data-stu-id="b132d-1004">**query_ptr** Destination area to copy the query.</span></span>
 - <span data-ttu-id="b132d-1005">**max_query_size** Tamaño máximo del área de destino de la consulta.</span><span class="sxs-lookup"><span data-stu-id="b132d-1005">**max_query_size** Maximum size of the query destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-1006">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-1006">Return Values</span></span>

 - <span data-ttu-id="b132d-1007">**NX_SUCCESS**: (0x00) Consulta del servidor HTTP obtenida correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-1007">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
 - <span data-ttu-id="b132d-1008">**NX_HTTP_FAILED** (0xE2) Tamaño de consulta demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="b132d-1008">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
 - <span data-ttu-id="b132d-1009">**NX_HTTP_NOT_FOUND** (0xE6) No se encontró la consulta especificada.</span><span class="sxs-lookup"><span data-stu-id="b132d-1009">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
 - <span data-ttu-id="b132d-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No hay ninguna consulta en la solicitud de cliente.</span><span class="sxs-lookup"><span data-stu-id="b132d-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
 - <span data-ttu-id="b132d-1011">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-1011">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-1012">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-1012">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-1013">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-1013">Allowed From</span></span>

<span data-ttu-id="b132d-1014">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-1014">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-1015">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-1015">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a><span data-ttu-id="b132d-1016">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="b132d-1016">nx_http_server_start</span></span>

<span data-ttu-id="b132d-1017">Iniciar el servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="b132d-1017">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-1018">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-1018">Prototype</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="b132d-1019">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-1019">Description</span></span>

<span data-ttu-id="b132d-1020">Este servicio inicia la instancia de servidor HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-1020">This service starts the previously create HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-1021">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-1021">Input Parameters</span></span>

 - <span data-ttu-id="b132d-1022">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-1022">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-1023">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-1023">Return Values</span></span>

 - <span data-ttu-id="b132d-1024">**NX_SUCCESS** (0x00) Servidor iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-1024">**NX_SUCCESS** (0x00) Successful Server start</span></span>
 - <span data-ttu-id="b132d-1025">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-1025">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-1026">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-1026">Allowed From</span></span>

<span data-ttu-id="b132d-1027">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-1027">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-1028">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-1028">Example</span></span>

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="b132d-1029">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="b132d-1029">nx_http_server_stop</span></span>

<span data-ttu-id="b132d-1030">Detener el servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="b132d-1030">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-1031">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-1031">Prototype</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="b132d-1032">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-1032">Description</span></span>

<span data-ttu-id="b132d-1033">Este servicio detiene la instancia de servidor HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b132d-1033">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="b132d-1034">Se debe llamar a esta rutina antes de eliminar una instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-1034">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-1035">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-1035">Input Parameters</span></span>

 - <span data-ttu-id="b132d-1036">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-1036">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-1037">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-1037">Return Values</span></span>

 - <span data-ttu-id="b132d-1038">**NX_SUCCESS** (0x00) Servidor detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-1038">**NX_SUCCESS** (0x00) Successful Server stop</span></span>
 - <span data-ttu-id="b132d-1039">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-1039">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-1040">NX_CALLER_ERROR (0x11) Autor de llamada de este servicio no válido.</span><span class="sxs-lookup"><span data-stu-id="b132d-1040">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-1041">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-1041">Allowed From</span></span>

<span data-ttu-id="b132d-1042">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="b132d-1042">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b132d-1043">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-1043">Example</span></span>

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="b132d-1044">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="b132d-1044">nx_http_server_type_get</span></span>

<span data-ttu-id="b132d-1045">Extraer el tipo de archivo de la solicitud HTTP del cliente</span><span class="sxs-lookup"><span data-stu-id="b132d-1045">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-1046">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-1046">Prototype</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a><span data-ttu-id="b132d-1047">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-1047">Description</span></span>

> [!NOTE]
> <span data-ttu-id="b132d-1048">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-1048">This service is deprecated.</span></span> <span data-ttu-id="b132d-1049">Se recomienda a los usuarios que usen el servicio *nx_http_server_type_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-1049">Users are encouraged to use the service *nx_http_server_type_retrieve()*.</span></span>

<span data-ttu-id="b132d-1050">Este servicio extrae el tipo de solicitud HTTP en el búfer http_type_string y su longitud en el valor devuelto del nombre del búfer de entrada, normalmente la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="b132d-1050">This service extracts the HTTP request type in the buffer http_type_string and its length in the return value from the input buffer name, usually the URL.</span></span> <span data-ttu-id="b132d-1051">Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="b132d-1051">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="b132d-1052">En caso contrario, se compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias.</span><span class="sxs-lookup"><span data-stu-id="b132d-1052">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="b132d-1053">Los mapas MIME predeterminados del servidor HTTP de NetX Duo son:</span><span class="sxs-lookup"><span data-stu-id="b132d-1053">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="b132d-1054">**html** texto/html</span><span class="sxs-lookup"><span data-stu-id="b132d-1054">**html** text/html</span></span>
 - <span data-ttu-id="b132d-1055">**htm** texto/html</span><span class="sxs-lookup"><span data-stu-id="b132d-1055">**htm** text/html</span></span>
 - <span data-ttu-id="b132d-1056">**txt** texto/sin formato</span><span class="sxs-lookup"><span data-stu-id="b132d-1056">**txt** text/plain</span></span>
 - <span data-ttu-id="b132d-1057">**gif** imagen/gif</span><span class="sxs-lookup"><span data-stu-id="b132d-1057">**gif** image/gif</span></span>
 - <span data-ttu-id="b132d-1058">**jpg** imagen/jpeg</span><span class="sxs-lookup"><span data-stu-id="b132d-1058">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="b132d-1059">**ico** imagen/x-icon</span><span class="sxs-lookup"><span data-stu-id="b132d-1059">**ico** image/x-icon</span></span>

<span data-ttu-id="b132d-1060">Si se proporciona, también se buscará un conjunto definido por el usuario de asignaciones MIME adicionales.</span><span class="sxs-lookup"><span data-stu-id="b132d-1060">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="b132d-1061">Consulte *nx_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="b132d-1061">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="b132d-1062">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b132d-1062">This service is deprecated.</span></span> <span data-ttu-id="b132d-1063">Se recomienda a los desarrolladores migrar a *nx_http_server_type_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-1063">Developers are encouraged to migrate to *nx_http_server_type_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-1064">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-1064">Input Parameters</span></span>

 - <span data-ttu-id="b132d-1065">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-1065">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="b132d-1066">**name** Puntero al búfer que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="b132d-1066">**name Pointer** to buffer to search</span></span>
 - <span data-ttu-id="b132d-1067">**http_type_string** Puntero a la cadena de tipo HTML extraída.</span><span class="sxs-lookup"><span data-stu-id="b132d-1067">**http_type_string** (Pointer to extracted HTML type)</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-1068">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-1068">Return Values</span></span>

 - <span data-ttu-id="b132d-1069">**Longitud de la cadena en bytes** Un valor distinto de cero es correcto.</span><span class="sxs-lookup"><span data-stu-id="b132d-1069">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="b132d-1070">Cero indica un error.</span><span class="sxs-lookup"><span data-stu-id="b132d-1070">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-1071">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-1071">Allowed From</span></span>

<span data-ttu-id="b132d-1072">Application</span><span class="sxs-lookup"><span data-stu-id="b132d-1072">Application</span></span>

### <a name="example"></a><span data-ttu-id="b132d-1073">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-1073">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="b132d-1074">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="b132d-1074">nx_http_server_type_get_extended</span></span>

<span data-ttu-id="b132d-1075">Extraer el tipo de archivo de la solicitud HTTP del cliente</span><span class="sxs-lookup"><span data-stu-id="b132d-1075">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-1076">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-1076">Prototype</span></span>

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a><span data-ttu-id="b132d-1077">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-1077">Description</span></span>

<span data-ttu-id="b132d-1078">Este servicio extrae el tipo de solicitud HTTP en el búfer *http_type_string* y su longitud en el valor devuelto por el *nombre* de búfer de entrada, normalmente la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="b132d-1078">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="b132d-1079">Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="b132d-1079">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="b132d-1080">En caso contrario, se compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias.</span><span class="sxs-lookup"><span data-stu-id="b132d-1080">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="b132d-1081">Los mapas MIME predeterminados del servidor HTTP de NetX Duo son:</span><span class="sxs-lookup"><span data-stu-id="b132d-1081">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="b132d-1082">**html** texto/html</span><span class="sxs-lookup"><span data-stu-id="b132d-1082">**html** text/html</span></span>
 - <span data-ttu-id="b132d-1083">**htm** texto/html</span><span class="sxs-lookup"><span data-stu-id="b132d-1083">**htm** text/html</span></span>
 - <span data-ttu-id="b132d-1084">**txt** texto/sin formato</span><span class="sxs-lookup"><span data-stu-id="b132d-1084">**txt** text/plain</span></span>
 - <span data-ttu-id="b132d-1085">**gif** imagen/gif</span><span class="sxs-lookup"><span data-stu-id="b132d-1085">**gif** image/gif</span></span>
 - <span data-ttu-id="b132d-1086">**jpg** imagen/jpeg</span><span class="sxs-lookup"><span data-stu-id="b132d-1086">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="b132d-1087">**ico** imagen/x-icon</span><span class="sxs-lookup"><span data-stu-id="b132d-1087">**ico** image/x-icon</span></span>

<span data-ttu-id="b132d-1088">Si se proporciona, también se buscará un conjunto definido por el usuario de asignaciones MIME adicionales.</span><span class="sxs-lookup"><span data-stu-id="b132d-1088">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="b132d-1089">Consulte *nx_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="b132d-1089">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="b132d-1090">Este servicio reemplaza a *nx_http_server_type_get()* .</span><span class="sxs-lookup"><span data-stu-id="b132d-1090">This service replaces *nx_http_server_type_get()*.</span></span> <span data-ttu-id="b132d-1091">Esta versión proporciona información de longitud adicional.</span><span class="sxs-lookup"><span data-stu-id="b132d-1091">This version supplies additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-1092">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-1092">Input Parameters</span></span>

 - <span data-ttu-id="b132d-1093">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-1093">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="b132d-1094">**name** Puntero al búfer que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="b132d-1094">**name** Pointer to buffer to search</span></span>
 - <span data-ttu-id="b132d-1095">**name_length** Longitud del búfer que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="b132d-1095">**name_length** Length of buffer to search</span></span>
 - <span data-ttu-id="b132d-1096">**http_type_string** Puntero a la cadena de tipo HTML extraída.</span><span class="sxs-lookup"><span data-stu-id="b132d-1096">**http_type_string** (Pointer to extracted HTML type)</span></span>
 - <span data-ttu-id="b132d-1097">**http_type_string_max_size** Tamaño del búfer de http_type_string.</span><span class="sxs-lookup"><span data-stu-id="b132d-1097">**http_type_string_max_size** Size of the http_type_string buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-1098">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-1098">Return Values</span></span>

 - <span data-ttu-id="b132d-1099">**Longitud de la cadena en bytes** Un valor distinto de cero es correcto.</span><span class="sxs-lookup"><span data-stu-id="b132d-1099">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="b132d-1100">Cero indica un error.</span><span class="sxs-lookup"><span data-stu-id="b132d-1100">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-1101">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-1101">Allowed From</span></span>

<span data-ttu-id="b132d-1102">Application</span><span class="sxs-lookup"><span data-stu-id="b132d-1102">Application</span></span>

### <a name="example"></a><span data-ttu-id="b132d-1103">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-1103">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
                    my_server.nx_http_server_request_resource, &resource_length,
                    sizeof(my_server.nx_http_server_request_resource) - 1))
           {
               return;
           }

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="b132d-1104">Para ver un ejemplo más detallado, consulte la descripción de [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span><span class="sxs-lookup"><span data-stu-id="b132d-1104">For a more detailed example, see the description for [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="b132d-1105">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="b132d-1105">nx_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="b132d-1106">Establecer la función de devolución de llamada de autenticación implícita</span><span class="sxs-lookup"><span data-stu-id="b132d-1106">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-1107">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-1107">Prototype</span></span>

```c
UINT nx_http_server_digest_authenticate_notify_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                            CHAR *name_ptr,
                                            CHAR *realm_ptr,
                                            CHAR *password_ptr,
                                            CHAR *method,
                                            CHAR *authorization_uri,
                                            CHAR *authorization_nc,
                                            CHAR *authorization_cnonce
                                           ));
```

### <a name="description"></a><span data-ttu-id="b132d-1108">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-1108">Description</span></span>

<span data-ttu-id="b132d-1109">Este servicio establece la devolución de llamada invocada cuando se realiza la autenticación implícita.</span><span class="sxs-lookup"><span data-stu-id="b132d-1109">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-1110">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-1110">Input Parameters</span></span>

 - <span data-ttu-id="b132d-1111">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-1111">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="b132d-1112">**digest_authenticate_callback** Puntero a la devolución de llamada de autenticación implícita.</span><span class="sxs-lookup"><span data-stu-id="b132d-1112">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-1113">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-1113">Return Values</span></span>

 - <span data-ttu-id="b132d-1114">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-1114">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="b132d-1115">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-1115">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="b132d-1116">NX_NOT_SUPPORTED (0x4B) Autenticación implícita no habilitada.</span><span class="sxs-lookup"><span data-stu-id="b132d-1116">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-1117">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-1117">Allowed From</span></span>

<span data-ttu-id="b132d-1118">Application</span><span class="sxs-lookup"><span data-stu-id="b132d-1118">Application</span></span>

### <a name="example"></a><span data-ttu-id="b132d-1119">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-1119">Example</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="b132d-1120">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="b132d-1120">nx_http_server_authentication_check_set</span></span>

<span data-ttu-id="b132d-1121">Establecer la función de devolución de llamada de comprobación de autenticación</span><span class="sxs-lookup"><span data-stu-id="b132d-1121">Set authentication checking callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="b132d-1122">Prototipo</span><span class="sxs-lookup"><span data-stu-id="b132d-1122">Prototype</span></span>

```c
UINT nx_http_server_authentication_check_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*authentication_check_extended)(
                                            NX_HTTP_SERVER *server_ptr,
                                            UINT request_type,
                                            CHAR *resource,
                                            CHAR **name,
                                            UINT *name_length,
                                            CHAR **password,
                                            UINT *password_length,
                                            CHAR **realm,
                                            UINT *realm_length
                                            ));
```

### <a name="description"></a><span data-ttu-id="b132d-1123">Descripción</span><span class="sxs-lookup"><span data-stu-id="b132d-1123">Description</span></span>

<span data-ttu-id="b132d-1124">Este servicio establece la función de devolución de llamada de comprobación de autenticación.</span><span class="sxs-lookup"><span data-stu-id="b132d-1124">This service sets the callback function of authentication checking.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b132d-1125">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="b132d-1125">Input Parameters</span></span>

 - <span data-ttu-id="b132d-1126">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="b132d-1126">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="b132d-1127">**authentication_check** Puntero a la comprobación de autenticación de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b132d-1127">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

### <a name="return-values"></a><span data-ttu-id="b132d-1128">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="b132d-1128">Return Values</span></span>

 - <span data-ttu-id="b132d-1129">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="b132d-1129">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="b132d-1130">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="b132d-1130">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b132d-1131">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="b132d-1131">Allowed From</span></span>

<span data-ttu-id="b132d-1132">Application</span><span class="sxs-lookup"><span data-stu-id="b132d-1132">Application</span></span>

### <a name="example"></a><span data-ttu-id="b132d-1133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b132d-1133">Example</span></span>

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
