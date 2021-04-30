---
title: 'Capítulo 3: Descripción de los servicios de NetX HTTP'
description: Este capítulo contiene una descripción de todos los servicios de NetX HTTP (se enumeran a continuación) por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c58d0e3d7eca86816a9d656bf2b92a896ffb96fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815194"
---
# <a name="chapter-3---description-of-netx-http-services"></a><span data-ttu-id="8300b-103">Capítulo 3: Descripción de los servicios de NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="8300b-103">Chapter 3 - Description of NetX HTTP services</span></span>

<span data-ttu-id="8300b-104">Este capítulo contiene una descripción de todos los servicios de NetX HTTP (se enumeran a continuación) por orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="8300b-104">This chapter contains a description of all NetX HTTP services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="8300b-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="8300b-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="8300b-106">**Servicios de cliente HTTP:**</span><span class="sxs-lookup"><span data-stu-id="8300b-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="8300b-107">nx_http_client_create *Crear una instancia de cliente HTTP*</span><span class="sxs-lookup"><span data-stu-id="8300b-107">nx_http_client_create *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="8300b-108">nx_http_client_delete *Eliminar una instancia de cliente HTTP*</span><span class="sxs-lookup"><span data-stu-id="8300b-108">nx_http_client_delete *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="8300b-109">nx_http_client_get_start *Iniciar una solicitud HTTP GET*</span><span class="sxs-lookup"><span data-stu-id="8300b-109">nx_http_client_get_start *Start an HTTP GET request*</span></span>
- <span data-ttu-id="8300b-110">nx_http_client_get_start_extended *Iniciar una solicitud HTTP GET*</span><span class="sxs-lookup"><span data-stu-id="8300b-110">nx_http_client_get_start_extended *Start an HTTP GET request*</span></span>
- <span data-ttu-id="8300b-111">nx_http_client_get_packet *Obtener el siguiente paquete de datos de recursos*</span><span class="sxs-lookup"><span data-stu-id="8300b-111">nx_http_client_get_packet *Get next resource data packet*</span></span>
- <span data-ttu-id="8300b-112">nx_http_client_put_start *Iniciar una solicitud HTTP PUT*</span><span class="sxs-lookup"><span data-stu-id="8300b-112">nx_http_client_put_start *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="8300b-113">nx_http_client_put_start_extended *Iniciar una solicitud HTTP PUT*</span><span class="sxs-lookup"><span data-stu-id="8300b-113">nx_http_client_put_start_extended *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="8300b-114">nx_http_client_put_packet *Enviar el siguiente paquete de datos de recursos*</span><span class="sxs-lookup"><span data-stu-id="8300b-114">nx_http_client_put_packet *Send next resource data packet*</span></span>
- <span data-ttu-id="8300b-115">*nx_http_client_set_connect_port* *Cambiar el puerto para conectarse al servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="8300b-115">*nx_http_client_set_connect_port* *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="8300b-116">**Servicios de servidor HTTP:**</span><span class="sxs-lookup"><span data-stu-id="8300b-116">**HTTP Server services:**</span></span>

- <span data-ttu-id="8300b-117">nx_http_server_cache_info_callback_set *Establecer la devolución de llamada para recuperar la fecha de vencimiento y última modificación de la dirección URL especificada*</span><span class="sxs-lookup"><span data-stu-id="8300b-117">nx_http_server_cache_info_callback_set *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="8300b-118">nx_http_server_callback_data_send *Enviar datos HTTP desde la función de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="8300b-118">nx_http_server_callback_data_send *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="8300b-119">nx_http_server_callback_generate_response_header *Crear un encabezado de respuesta en funciones de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="8300b-119">nx_http_server_callback_generate_response_header *Create response header in callback functions*</span></span>
- <span data-ttu-id="8300b-120">nx_http_server_callback_generate_response_header_extended *Crear un encabezado de respuesta en funciones de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="8300b-120">nx_http_server_callback_generate_response_header_extended *Create response header in callback functions*</span></span>
- <span data-ttu-id="8300b-121">nx_http_server_callback_packet_send *Enviar un paquete HTTP desde una devolución de llamada HTTP*</span><span class="sxs-lookup"><span data-stu-id="8300b-121">nx_http_server_callback_packet_send *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="8300b-122">nx_http_server_callback_response_send *Enviar una respuesta desde la función de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="8300b-122">nx_http_server_callback_response_send *Send response from callback function*</span></span>
- <span data-ttu-id="8300b-123">nx_http_server_callback_response_send_extended *Enviar una respuesta desde la función de devolución de llamada*</span><span class="sxs-lookup"><span data-stu-id="8300b-123">nx_http_server_callback_response_send_extended *Send response from callback function*</span></span>
- <span data-ttu-id="8300b-124">nx_http_server_content_get *Obtener contenido de la solicitud*</span><span class="sxs-lookup"><span data-stu-id="8300b-124">nx_http_server_content_get *Get content from the request*</span></span>
- <span data-ttu-id="8300b-125">nx_http_server_content_get_extended *Obtener contenido de la solicitud; admite solicitudes vacías (longitud de contenido cero)*</span><span class="sxs-lookup"><span data-stu-id="8300b-125">nx_http_server_content_get_extended *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="8300b-126">nx_http_server_content_length_get *Obtener longitud de contenido de la solicitud*</span><span class="sxs-lookup"><span data-stu-id="8300b-126">nx_http_server_content_length_get *Get length of content in the request*</span></span>
- <span data-ttu-id="8300b-127">nx_http_server_content_length_get_extended *Obtener longitud de contenido de la solicitud; admite solicitudes vacías (longitud de contenido cero)*</span><span class="sxs-lookup"><span data-stu-id="8300b-127">nx_http_server_content_length_get_extended *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="8300b-128">nx_http_server_create *Crear una instancia de servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="8300b-128">nx_http_server_create *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="8300b-129">nx_http_server_delete *Eliminar una instancia de servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="8300b-129">nx_http_server_delete *Delete an HTTP Server instance*</span></span>
- <span data-ttu-id="8300b-130">nx_http_server_get_entity_content *Devolver tamaño y ubicación del contenido de la entidad en la dirección URL*</span><span class="sxs-lookup"><span data-stu-id="8300b-130">nx_http_server_get_entity_content *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="8300b-131">nx_http_server_get_entity_header *Extraer encabezado de entidad URL en el búfer especificado*</span><span class="sxs-lookup"><span data-stu-id="8300b-131">nx_http_server_get_entity_header *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="8300b-132">nx_http_server_gmt_callback_set *Establecer devolución de llamada para recuperar la fecha y hora GMT*</span><span class="sxs-lookup"><span data-stu-id="8300b-132">nx_http_server_gmt_callback_set *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="8300b-133">nx_http_server_invalid_userpassword_notify_set *Establecer devolución de llamada para cuando se recibe un nombre de usuario y una contraseña no válidos en una solicitud de cliente*</span><span class="sxs-lookup"><span data-stu-id="8300b-133">nx_http_server_invalid_userpassword_notify_set *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="8300b-134">nx_http_server_mime_maps_additional_set *Definir asignaciones MIME adicionales para HTML*</span><span class="sxs-lookup"><span data-stu-id="8300b-134">nx_http_server_mime_maps_additional_set *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="8300b-135">nx_http_server_packet_content_find *Extraer longitud de contenido en el encabezado HTTP y establecer puntero en el inicio de los datos de contenido*</span><span class="sxs-lookup"><span data-stu-id="8300b-135">nx_http_server_packet_content_find *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="8300b-136">nx_http_server_packet_get *Recibir paquete de cliente directamente*</span><span class="sxs-lookup"><span data-stu-id="8300b-136">nx_http_server_packet_get *Receive client packet directly*</span></span>
- <span data-ttu-id="8300b-137">nx_http_server_param_get *Obtener parámetro de la solicitud*</span><span class="sxs-lookup"><span data-stu-id="8300b-137">nx_http_server_param_get *Get parameter from the request*</span></span>
- <span data-ttu-id="8300b-138">nx_http_server_query_get *Obtener consulta de la solicitud*</span><span class="sxs-lookup"><span data-stu-id="8300b-138">nx_http_server_query_get *Get query from the request*</span></span>
- <span data-ttu-id="8300b-139">nx_http_server_start *Iniciar el servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="8300b-139">nx_http_server_start *Start the HTTP Server*</span></span>
- <span data-ttu-id="8300b-140">nx_http_server_stop *Detener el servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="8300b-140">nx_http_server_stop *Stop the HTTP Server*</span></span>
- <span data-ttu-id="8300b-141">nx_http_server_type_get_extended *Extraer tipo HTTP, por ejemplo, texto/sin formato*</span><span class="sxs-lookup"><span data-stu-id="8300b-141">nx_http_server_type_get *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="8300b-142">nx_http_server_type_get_extended *Extraer tipo HTTP, por ejemplo, texto/sin formato*</span><span class="sxs-lookup"><span data-stu-id="8300b-142">nx_http_server_type_get_extended *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="8300b-143">nx_http_server_digest_authenticate_notify_set *Establecer función de devolución de llamada de autenticación implícita*</span><span class="sxs-lookup"><span data-stu-id="8300b-143">nx_http_server_digest_authenticate_notify_set *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="8300b-144">nx_http_server_authentication_check_set *Establecer función de devolución de llamada de comprobación de autenticación*</span><span class="sxs-lookup"><span data-stu-id="8300b-144">nx_http_server_authentication_check_set *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="8300b-145">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="8300b-145">nx_http_client_create</span></span>

### <a name="create-an-http-client-instance"></a><span data-ttu-id="8300b-146">Creación de una instancia de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="8300b-146">Create an HTTP Client Instance</span></span>

<span data-ttu-id="8300b-147">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-147">**Prototype**</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

<span data-ttu-id="8300b-148">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-148">**Description**</span></span>

<span data-ttu-id="8300b-149">Este servicio crea una instancia de cliente HTTP en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="8300b-149">This service creates an HTTP Client instance on the specified IP instance.</span></span>

<span data-ttu-id="8300b-150">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-150">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-151">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-151">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8300b-152">**client_name** Nombre de la instancia de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-152">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="8300b-153">**ip_ptr** Puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="8300b-153">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="8300b-154">**pool_ptr** Puntero al grupo de paquetes predeterminado.</span><span class="sxs-lookup"><span data-stu-id="8300b-154">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="8300b-155">Tenga en cuenta que los paquetes de este grupo deben tener una carga útil lo suficientemente grande como para controlar el encabezado de respuesta completo.</span><span class="sxs-lookup"><span data-stu-id="8300b-155">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="8300b-156">Se define mediante NX_HTTP_CLIENT_MIN_PACKET_SIZE en *nx_http_client.h*.</span><span class="sxs-lookup"><span data-stu-id="8300b-156">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http_client.h*.</span></span>
- <span data-ttu-id="8300b-157">**window_size** Tamaño de la ventana de recepción del socket TCP del cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-157">**window_size** Size of the Client’s TCP socket receive window.</span></span>

<span data-ttu-id="8300b-158">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-158">**Return Values**</span></span>

- <span data-ttu-id="8300b-159">**NX_SUCCESS** (0x00) Cliente HTTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-159">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="8300b-160">NX_PTR_ERROR (0x16) Puntero HTTP, ip_ptr o de grupo de paquetes no válido.</span><span class="sxs-lookup"><span data-stu-id="8300b-160">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="8300b-161">NX_HTTP_POOL_ERROR (0xE9) Tamaño de carga no válido en el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="8300b-161">NX_HTTP_POOL_ERROR(0xE9) Invalid payload size in packet pool</span></span>

<span data-ttu-id="8300b-162">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-162">**Allowed From**</span></span>

<span data-ttu-id="8300b-163">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-163">Initialization, Threads</span></span>

<span data-ttu-id="8300b-164">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-164">**Example**</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="8300b-165">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="8300b-165">nx_http_client_delete</span></span>

### <a name="delete-an-http-client-instance"></a><span data-ttu-id="8300b-166">Eliminación de una instancia de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="8300b-166">Delete an HTTP Client Instance</span></span>

<span data-ttu-id="8300b-167">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-167">**Prototype**</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

<span data-ttu-id="8300b-168">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-168">**Description**</span></span>

<span data-ttu-id="8300b-169">Este servicio elimina una instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8300b-169">This service deletes a previously created HTTP Client instance.</span></span>

<span data-ttu-id="8300b-170">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-170">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-171">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-171">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="8300b-172">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-172">**Return Values**</span></span>

- <span data-ttu-id="8300b-173">**NX_SUCCESS** (0x00) Cliente HTTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-173">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="8300b-174">NX_PTR_ERROR (0x16) El puntero HTTP no es válido.</span><span class="sxs-lookup"><span data-stu-id="8300b-174">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="8300b-175">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-175">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-176">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-176">**Allowed From**</span></span>

<span data-ttu-id="8300b-177">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-177">Threads</span></span>

<span data-ttu-id="8300b-178">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-178">**Example**</span></span>

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="8300b-179">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="8300b-179">nx_http_client_get_start</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="8300b-180">Inicio de una solicitud HTTP GET</span><span class="sxs-lookup"><span data-stu-id="8300b-180">Start an HTTP GET request</span></span>

<span data-ttu-id="8300b-181">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-181">**Prototype**</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

<span data-ttu-id="8300b-182">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-182">**Description**</span></span>

<span data-ttu-id="8300b-183">Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero "Recurso" en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8300b-183">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8300b-184">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="8300b-184">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="8300b-185">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, "/index.htm", o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="8300b-185">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8300b-186">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8300b-186">This service is deprecated.</span></span> <span data-ttu-id="8300b-187">Se recomienda a los desarrolladores migrar a *nx_http_client_get_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-187">Developers are encouraged to migrate to *nx_http_client_get_start_extended()*</span></span>

<span data-ttu-id="8300b-188">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-188">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-189">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-189">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8300b-190">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-190">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8300b-191">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="8300b-191">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8300b-192">**input_ptr** Puntero a datos adicionales para la solicitud GET.</span><span class="sxs-lookup"><span data-stu-id="8300b-192">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="8300b-193">Esto es opcional.</span><span class="sxs-lookup"><span data-stu-id="8300b-193">This is optional.</span></span> <span data-ttu-id="8300b-194">Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.</span><span class="sxs-lookup"><span data-stu-id="8300b-194">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="8300b-195">**input_size** Número de bytes en la entrada adicional opcional a la que apunta input_ptr.</span><span class="sxs-lookup"><span data-stu-id="8300b-195">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="8300b-196">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-196">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8300b-197">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-197">**password** Pointer to optional password for authentication.</span></span><span data-ttu-id="8300b-198">
-\*\*wait_option*\* Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-198">
-\*\*wait_option*\* Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8300b-199">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="8300b-199">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8300b-200">**time out value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8300b-200">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="8300b-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8300b-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="8300b-202">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-202">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="8300b-203">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-203">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="8300b-204">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-204">**Return Values**</span></span>

- <span data-ttu-id="8300b-205">**NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-205">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="8300b-206">**NX_HTTP_ERROR** (0xE0) Error de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="8300b-206">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="8300b-207">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="8300b-207">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="8300b-208">**NX_HTTP_FAILED** (0xE2) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-208">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8300b-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="8300b-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="8300b-210">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-210">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-211">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-211">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="8300b-212">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-212">**Allowed From**</span></span>

<span data-ttu-id="8300b-213">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-213">Threads</span></span>

<span data-ttu-id="8300b-214">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-214">**Example**</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  POST_MESSAGE, sizeof(POST_MESSAGE),
                                  “myname”, “mypassword”, 1000);
 
/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```


## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="8300b-215">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="8300b-215">nx_http_client_get_start_extended</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="8300b-216">Inicio de una solicitud HTTP GET</span><span class="sxs-lookup"><span data-stu-id="8300b-216">Start an HTTP GET request</span></span>

<span data-ttu-id="8300b-217">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-217">**Prototype**</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

<span data-ttu-id="8300b-218">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-218">**Description**</span></span>

<span data-ttu-id="8300b-219">Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero "Recurso" en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8300b-219">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="8300b-220">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_http_client_get_packet* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="8300b-220">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="8300b-221">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, "/index.htm", o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="8300b-221">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="8300b-222">Este servicio reemplaza a *nx_http_client_get_start()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-222">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="8300b-223">Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="8300b-223">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="8300b-224">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-224">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-225">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-225">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8300b-226">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-226">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8300b-227">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="8300b-227">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="8300b-228">**resource_length** Longitud de la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="8300b-228">**resource_length** Length of URL string for requested resource.</span></span>
- <span data-ttu-id="8300b-229">**input_ptr** Puntero a datos adicionales para la solicitud GET.</span><span class="sxs-lookup"><span data-stu-id="8300b-229">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="8300b-230">Esto es opcional.</span><span class="sxs-lookup"><span data-stu-id="8300b-230">This is optional.</span></span> <span data-ttu-id="8300b-231">Si es válido, la entrada especificada se coloca en el área de contenido del mensaje y se usa una solicitud POST en lugar de una operación GET.</span><span class="sxs-lookup"><span data-stu-id="8300b-231">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="8300b-232">**input_size** Número de bytes en la entrada adicional opcional a la que apunta input_ptr.</span><span class="sxs-lookup"><span data-stu-id="8300b-232">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="8300b-233">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-233">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8300b-234">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-234">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="8300b-235">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-235">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8300b-236">**password_length** Longitud de la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-236">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="8300b-237">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-237">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="8300b-238">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="8300b-238">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8300b-239">**time out value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8300b-239">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="8300b-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8300b-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="8300b-241">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-241">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="8300b-242">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-242">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="8300b-243">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-243">**Return Values**</span></span>

- <span data-ttu-id="8300b-244">**NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-244">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="8300b-245">**NX_HTTP_ERROR** (0xE0) Error de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="8300b-245">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="8300b-246">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="8300b-246">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="8300b-247">**NX_HTTP_FAILED** (0xE2) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-247">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="8300b-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="8300b-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="8300b-249">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-249">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-250">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-250">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="8300b-251">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-251">**Allowed From**</span></span>

<span data-ttu-id="8300b-252">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-252">Threads</span></span>

<span data-ttu-id="8300b-253">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-253">**Example**</span></span>
            
```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5),
                                           “/TEST.HTM”,
                                           9, NX_NULL, 0, “myname”, 6,
                                           “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), 
                                           “/TEST.HTM”,
                                           9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                           “myname”, 6, “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="8300b-254">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="8300b-254">nx_http_client_get_packet</span></span>

### <a name="get-next-resource-data-packet"></a><span data-ttu-id="8300b-255">Obtención del siguiente paquete de datos de recursos</span><span class="sxs-lookup"><span data-stu-id="8300b-255">Get next resource data packet</span></span>

<span data-ttu-id="8300b-256">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-256">**Prototype**</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="8300b-257">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-257">**Description**</span></span>

<span data-ttu-id="8300b-258">Este servicio recupera el siguiente paquete de contenido del recurso solicitado por la llamada a *nx_http_client_get_start* anterior.</span><span class="sxs-lookup"><span data-stu-id="8300b-258">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="8300b-259">Deben realizarse llamadas sucesivas a esta rutina hasta que se reciba el estado de devolución de NX_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="8300b-259">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

<span data-ttu-id="8300b-260">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-260">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-261">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-261">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8300b-262">**packet_ptr** Destino del puntero de paquete que contiene el contenido parcial del recurso.</span><span class="sxs-lookup"><span data-stu-id="8300b-262">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="8300b-263">**wait_option** Define cuánto tiempo esperará el servicio a que se obtenga el paquete del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-263">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="8300b-264">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="8300b-264">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8300b-265">**timeout value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8300b-265">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="8300b-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8300b-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="8300b-267">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-267">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="8300b-268">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-268">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="8300b-269">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-269">**Return Values**</span></span>

- <span data-ttu-id="8300b-270">**NX_SUCCESS** (0x00) Se ha obtenido correctamente el paquete del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-270">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
- <span data-ttu-id="8300b-271">**NX_HTTP_GET_DONE** (0xEC) Se ha realizado la obtención del paquete del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-271">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
- <span data-ttu-id="8300b-272">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está en modo de obtención.</span><span class="sxs-lookup"><span data-stu-id="8300b-272">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="8300b-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Longitud de paquete no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="8300b-274">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-275">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-275">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-276">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-276">**Allowed From**</span></span>

<span data-ttu-id="8300b-277">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-277">Threads</span></span>

<span data-ttu-id="8300b-278">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-278">**Example**</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
Note that the nx_http_client_get_start routine must have been called
previously. */
status = nx_http_client_get_packet(&my_client, &next_packet, 1000);
 
/* If status is NX_SUCCESS, the next packet of content is pointed to by 
“next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="8300b-279">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="8300b-279">nx_http_client_put_start</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="8300b-280">Inicio de una solicitud HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="8300b-280">Start an HTTP PUT request</span></span> 

<span data-ttu-id="8300b-281">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-281">**Prototype**</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="8300b-282">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-282">**Description**</span></span>

<span data-ttu-id="8300b-283">Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP proporcionada.</span><span class="sxs-lookup"><span data-stu-id="8300b-283">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="8300b-284">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet* para enviar realmente el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-284">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8300b-285">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, "/index.htm", o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="8300b-285">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8300b-286">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8300b-286">This service is deprecated.</span></span> <span data-ttu-id="8300b-287">Se recomienda a los desarrolladores migrar a *nx_http_client_put_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-287">Developers are encouraged to migrate to *nx_http_client_put_start_extended()*.</span></span>

<span data-ttu-id="8300b-288">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-288">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-289">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-289">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8300b-290">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-290">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8300b-291">**resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="8300b-291">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="8300b-292">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-292">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8300b-293">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-293">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8300b-294">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="8300b-294">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8300b-295">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="8300b-295">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="8300b-296">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-296">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="8300b-297">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="8300b-297">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8300b-298">**timeout value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8300b-298">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="8300b-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8300b-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="8300b-300">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-300">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="8300b-301">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-301">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="8300b-302">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-302">**Return Values**</span></span>

- <span data-ttu-id="8300b-303">**NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-303">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="8300b-304">**NX_HTTP_USERNAME_TOO_LONG**</span><span class="sxs-lookup"><span data-stu-id="8300b-304">**NX_HTTP_USERNAME_TOO_LONG**</span></span>
- <span data-ttu-id="8300b-305">**(0xF1) El nombre de usuario es demasiado grande para el búfer**</span><span class="sxs-lookup"><span data-stu-id="8300b-305">**(0xF1) Username too large for buffer**</span></span>
- <span data-ttu-id="8300b-306">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="8300b-306">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="8300b-307">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-307">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-308">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="8300b-308">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8300b-309">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-309">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-310">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-310">**Allowed From**</span></span>

<span data-ttu-id="8300b-311">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-311">Threads</span></span>

<span data-ttu-id="8300b-312">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-312">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                 “/TEST.HTM”, “myname”, “mypassword”, 20, 
                                 NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="8300b-313">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="8300b-313">nx_http_client_put_start_extended</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="8300b-314">Inicio de una solicitud HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="8300b-314">Start an HTTP PUT request</span></span>

<span data-ttu-id="8300b-315">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-315">**Prototype**</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="8300b-316">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-316">**Description**</span></span>

<span data-ttu-id="8300b-317">Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP proporcionada.</span><span class="sxs-lookup"><span data-stu-id="8300b-317">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="8300b-318">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_http_client_put_packet* para enviar realmente el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-318">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="8300b-319">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, "/index.htm", o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="8300b-319">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="8300b-320">Este servicio reemplaza a *nx_http_client_put_start()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-320">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="8300b-321">Requiere que el autor de llamada especifique la longitud del recurso, el nombre de usuario y la contraseña.</span><span class="sxs-lookup"><span data-stu-id="8300b-321">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="8300b-322">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-322">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-323">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-323">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8300b-324">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-324">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="8300b-325">**resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="8300b-325">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="8300b-326">**resource_length** Longitud de la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="8300b-326">**resource_length** Length of URL string for resource to send to Server.</span></span>
- <span data-ttu-id="8300b-327">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-327">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="8300b-328">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-328">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="8300b-329">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-329">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="8300b-330">**password_length** Longitud de la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-330">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="8300b-331">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="8300b-331">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="8300b-332">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_http_client_put_packet* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="8300b-332">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="8300b-333">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud PUT del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-333">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="8300b-334">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="8300b-334">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8300b-335">**timeout value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8300b-335">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="8300b-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8300b-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="8300b-337">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-337">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="8300b-338">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-338">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="8300b-339">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-339">**Return Values**</span></span>

- <span data-ttu-id="8300b-340">**NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-340">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="8300b-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) El nombre de usuario es demasiado grande para el búfer.</span><span class="sxs-lookup"><span data-stu-id="8300b-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
- <span data-ttu-id="8300b-342">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="8300b-342">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="8300b-343">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-343">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-344">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="8300b-344">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="8300b-345">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-345">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-346">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-346">**Allowed From**</span></span>

<span data-ttu-id="8300b-347">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-347">Threads</span></span>

<span data-ttu-id="8300b-348">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-348">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                          “/TEST.HTM”, 9, “myname”, 6, 
                                          “mypassword”, 
                                          10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="8300b-349">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="8300b-349">nx_http_client_put_packet</span></span>

### <a name="send-next-resource-data-packet"></a><span data-ttu-id="8300b-350">Envío del siguiente paquete de datos de recursos</span><span class="sxs-lookup"><span data-stu-id="8300b-350">Send next resource data packet</span></span>

<span data-ttu-id="8300b-351">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-351">**Prototype**</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="8300b-352">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-352">**Description**</span></span>

<span data-ttu-id="8300b-353">Este servicio intenta enviar el siguiente paquete de contenido de recursos al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-353">This service attempts to send the next packet of resource content to the HTTP Server.</span></span> <span data-ttu-id="8300b-354">Observe que se debe llamar a esta rutina repetidamente hasta que la longitud combinada de los paquetes enviados sea igual al valor de "total_bytes" especificado en la llamada a *nx_http_client_put_start()* anterior.</span><span class="sxs-lookup"><span data-stu-id="8300b-354">Note that this routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start()* call.</span></span>

<span data-ttu-id="8300b-355">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-355">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-356">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-356">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8300b-357">**packet_ptr** Puntero al siguiente contenido del recurso que se va a enviar al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-357">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="8300b-358">**WAIT_OPTION** Define cuánto tiempo esperará el servicio internamente para procesar el paquete PUT del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-358">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="8300b-359">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="8300b-359">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8300b-360">**timeout value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8300b-360">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="8300b-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="8300b-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="8300b-362">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-362">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /> <span data-ttu-id="8300b-363">Si se selecciona un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanecen suspendidos mientras se espera la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-363">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="8300b-364">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-364">**Return Values**</span></span>

- <span data-ttu-id="8300b-365">**NX_SUCCESS** (0x00) Paquete de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-365">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="8300b-366">**NX_HTTP_NOT_READY** (0xEA) El cliente HTTP no está preparado.</span><span class="sxs-lookup"><span data-stu-id="8300b-366">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="8300b-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Código de error del servidor recibido.\*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Longitud de paquete no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code\*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="8300b-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nombre o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="8300b-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
- <span data-ttu-id="8300b-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) El servidor responde antes de que finalice PUT.</span><span class="sxs-lookup"><span data-stu-id="8300b-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
- <span data-ttu-id="8300b-370">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-370">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-371">NX_INVALID_PACKET (0x12) El paquete es demasiado pequeño para el encabezado TCP.</span><span class="sxs-lookup"><span data-stu-id="8300b-371">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="8300b-372">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-372">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-373">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-373">**Allowed From**</span></span>

<span data-ttu-id="8300b-374">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-374">Threads</span></span>

<span data-ttu-id="8300b-375">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-375">**Example**</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
“/TEST.HTM” to the HTTP Server. */
status = nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                                  NX_PACKET *packet_ptr,
                                  ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM
has successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="8300b-376">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="8300b-376">nx_http_client_set_connect_port</span></span>

### <a name="set-the-connection-port-to-the-server"></a><span data-ttu-id="8300b-377">Establecimiento del puerto de conexión al servidor</span><span class="sxs-lookup"><span data-stu-id="8300b-377">Set the connection port to the Server</span></span>

<span data-ttu-id="8300b-378">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-378">**Prototype**</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

<span data-ttu-id="8300b-379">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-379">**Description**</span></span>

<span data-ttu-id="8300b-380">Este servicio cambia el puerto de conexión al conectarse al servidor HTTP en el puerto especificado en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="8300b-380">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="8300b-381">De lo contrario, el puerto de conexión tiene como valor predeterminado 80.</span><span class="sxs-lookup"><span data-stu-id="8300b-381">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="8300b-382">Se debe llamar a este método antes de *nx_http_client_get_start*() y *nx_http_client_put_start*(), por ejemplo, cuando el cliente HTTP conecta con el servidor.</span><span class="sxs-lookup"><span data-stu-id="8300b-382">This must be called before *nx_http_client_get_start*() and *nx_http_client_put_start*() e.g. when the HTTP Client connects with the Server.</span></span>

<span data-ttu-id="8300b-383">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-383">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-384">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-384">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="8300b-385">**port** Puerto para la conexión al servidor.</span><span class="sxs-lookup"><span data-stu-id="8300b-385">**port** Port for connecting to the Server.</span></span>

<span data-ttu-id="8300b-386">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-386">**Return Values**</span></span>

- <span data-ttu-id="8300b-387">**NX_SUCCESS** (0x00) Puerto cambiado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-387">**NX_SUCCESS** (0x00) Successfully changed the connect port</span></span>
- <span data-ttu-id="8300b-388">**NX_INVALID_PORT** (0x46) El puerto supera el máximo (0xFFFF) o es cero.</span><span class="sxs-lookup"><span data-stu-id="8300b-388">**NX_INVALID_PORT** (0x46) Port exceeds the maximum (0xFFFF) or is zero.</span></span>
- <span data-ttu-id="8300b-389">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-389">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-390">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-390">**Allowed From**</span></span>

<span data-ttu-id="8300b-391">Subprocesos, inicialización</span><span class="sxs-lookup"><span data-stu-id="8300b-391">Threads, Initialization</span></span>

<span data-ttu-id="8300b-392">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-392">**Example**</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="8300b-393">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="8300b-393">nx_http_server_cache_info_callback_set</span></span>

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a><span data-ttu-id="8300b-394">Establece la devolución de llamada para recuperar la antigüedad máxima y la fecha de la dirección URL</span><span class="sxs-lookup"><span data-stu-id="8300b-394">Set the callback to retrieve URL max age and date</span></span>

<span data-ttu-id="8300b-395">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-395">**Prototype**</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

<span data-ttu-id="8300b-396">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-396">**Description**</span></span>

<span data-ttu-id="8300b-397">Este servicio establece el servicio de devolución de llamada invocado para obtener la antigüedad máxima y la fecha de última modificación del recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="8300b-397">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

<span data-ttu-id="8300b-398">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-398">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-399">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-399">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8300b-400">**cache_info_get** Puntero a la devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="8300b-400">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="8300b-401">**max_age** Puntero a la antigüedad máxima de un recurso.</span><span class="sxs-lookup"><span data-stu-id="8300b-401">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="8300b-402">**data** Puntero a la fecha de última modificación devuelta.</span><span class="sxs-lookup"><span data-stu-id="8300b-402">**data** Pointer to last modified date returned.</span></span>

<span data-ttu-id="8300b-403">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-403">**Return Values**</span></span>

- <span data-ttu-id="8300b-404">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-404">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8300b-405">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-405">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-406">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-406">**Allowed From**</span></span>

<span data-ttu-id="8300b-407">Inicialización</span><span class="sxs-lookup"><span data-stu-id="8300b-407">Initialization</span></span>

<span data-ttu-id="8300b-408">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-408">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
UINT cache_info_get(CHAR *resource, UINT *max_age,
                   NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP
server is set by nx_http_server_start(), set the cache info callback: */
status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="8300b-409">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="8300b-409">nx_http_server_callback_data_send</span></span>

### <a name="send-data-from-callback-function"></a><span data-ttu-id="8300b-410">Envío de datos desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="8300b-410">Send data from callback function</span></span>

<span data-ttu-id="8300b-411">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-411">**Prototype**</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

<span data-ttu-id="8300b-412">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-412">**Description**</span></span>

<span data-ttu-id="8300b-413">Este servicio envía los datos del paquete proporcionado desde la rutina de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8300b-413">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="8300b-414">Normalmente se usa para enviar datos dinámicos asociados a solicitudes GET/POST.</span><span class="sxs-lookup"><span data-stu-id="8300b-414">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="8300b-415">Tenga en cuenta que si se usa esta función, la rutina de devolución de llamada es responsable de enviar la respuesta completa en el formato correcto.</span><span class="sxs-lookup"><span data-stu-id="8300b-415">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="8300b-416">Además, la rutina de devolución de llamada debe devolver el estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="8300b-416">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8300b-417">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-417">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-418">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8300b-419">**data_ptr** Puntero a los datos que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="8300b-419">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="8300b-420">**data_length** Número de bytes que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="8300b-420">**data_length** Number of bytes to send.</span></span>

<span data-ttu-id="8300b-421">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-421">**Return Values**</span></span>

- <span data-ttu-id="8300b-422">**NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-422">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="8300b-423">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-423">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-424">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-424">**Allowed From**</span></span>

<span data-ttu-id="8300b-425">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-425">Threads</span></span>

<span data-ttu-id="8300b-426">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-426">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
       (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
        contents directly. */

        nx_http_server_callback_data_send(server_ptr,
                                         "HTTP/1.0 200 \r\nContent-Length:
                                         103\r\nContent-Type: text/html\r\n\r\n",
                                         63);
        nx_http_server_callback_data_send(server_ptr, "<HTML>> r\n<HEAD><TITLE>NetX
                                         HTTP Test </TITLE></HEAD>\r\n
                                         <BODY>\r\n<H1>NetX Test Page
                                         </H1>\r\n</BODY>> r\n</HTML>\r\n", 103);
        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="8300b-427">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="8300b-427">nx_http_server_callback_generate_response_header</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="8300b-428">Creación de un encabezado de respuesta en una función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="8300b-428">Create a response header in a callback function</span></span>

<span data-ttu-id="8300b-429">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-429">**Prototype**</span></span>

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

<span data-ttu-id="8300b-430">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-430">**Description**</span></span>

<span data-ttu-id="8300b-431">Este servicio llama a la función interna _ *nx_http_server_generate_response_header* cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE del cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-431">This service calls the internal function _ *nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="8300b-432">Su uso está previsto en funciones de devolución de llamada de servidor HTTP cuando la aplicación de servidor HTTP está diseñando su respuesta al cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-432">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="8300b-433">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8300b-433">This service is deprecated.</span></span> <span data-ttu-id="8300b-434">Se recomienda a los desarrolladores migrar a *nxd_http_server_callback_generate_response_header_extended()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-434">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

<span data-ttu-id="8300b-435">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-435">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-436">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-436">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8300b-437">**packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="8300b-437">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="8300b-438">**status_code** Indica el estado del recurso.</span><span class="sxs-lookup"><span data-stu-id="8300b-438">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="8300b-439">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="8300b-439">Examples:</span></span>
- <span data-ttu-id="8300b-440">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="8300b-440">**NX_HTTP_STATUS_OK**</span></span>
- <span data-ttu-id="8300b-441">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="8300b-441">**NX_HTTP_STATUS_MODIFIED**</span></span>
- <span data-ttu-id="8300b-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8300b-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="8300b-443">**content_length** Tamaño del contenido en bytes.</span><span class="sxs-lookup"><span data-stu-id="8300b-443">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="8300b-444">**content_type** Tipo de HTTP, por ejemplo, "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="8300b-444">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="8300b-445">**additional_header** Puntero a texto de encabezado adicional.</span><span class="sxs-lookup"><span data-stu-id="8300b-445">**additional_header** Pointer to additional header text</span></span>

<span data-ttu-id="8300b-446">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-446">**Return Values**</span></span>

- <span data-ttu-id="8300b-447">**NX_SUCCESS** (0x00) Encabezado HTML creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-447">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="8300b-448">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-448">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-449">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-449">**Allowed From**</span></span>

<span data-ttu-id="8300b-450">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-450">Threads</span></span>

<span data-ttu-id="8300b-451">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-451">**Example**</span></span>

```c
CHAR demotestbuffer[] = “<html>\r\n\r\n<head> r\n\r\n<title>Main                 \
                        Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n  \ 
                        </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
the HTTP server in nx_http_server_create, creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET     *sresp_packet_ptr;
    ULONG         string_length;
    CHAR          temp_string[30];
    ULONG         length = 0;

        length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length = (ULONG) nx_http_server_type_get(server_ptr, server_ptr ->
                   nx_http_server_request_resource, temp_string);

/* Null terminate the string. */
   temp_string[temp] = 0;

/* Now build a response header with server status is OK and no additional header info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
            &resp_packet_ptr, NX_HTTP_STATUS_OK,
            length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
            length, server_ptr >>
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

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="8300b-452">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="8300b-452">nx_http_server_callback_generate_response_header_extended</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="8300b-453">Creación de un encabezado de respuesta en una función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="8300b-453">Create a response header in a callback function</span></span>

<span data-ttu-id="8300b-454">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-454">**Prototype**</span></span>

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

<span data-ttu-id="8300b-455">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-455">**Description**</span></span>

<span data-ttu-id="8300b-456">Este servicio llama a la función interna _ *nx_http_server_generate_response_header()* cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE del cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-456">This service calls the internal function _ *nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="8300b-457">Su uso está previsto en funciones de devolución de llamada de servidor HTTP cuando la aplicación de servidor HTTP está diseñando su respuesta al cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-457">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="8300b-458">Este servicio reemplaza a *nx_http_server_callback_generate_response_header()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-458">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="8300b-459">Esta versión proporciona información de longitud adicional a la función de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="8300b-459">This version supplies additional length information to the callback function.</span></span>

<span data-ttu-id="8300b-460">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-460">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-461">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-461">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8300b-462">**packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="8300b-462">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="8300b-463">**status_code** Indica el estado del recurso.</span><span class="sxs-lookup"><span data-stu-id="8300b-463">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="8300b-464">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="8300b-464">Examples:</span></span>
  - <span data-ttu-id="8300b-465">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="8300b-465">**NX_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="8300b-466">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="8300b-466">**NX_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="8300b-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="8300b-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="8300b-468">**status_code** Longitud del código de estado.</span><span class="sxs-lookup"><span data-stu-id="8300b-468">**status_code** Length of status code</span></span>
- <span data-ttu-id="8300b-469">**content_length** Tamaño del contenido en bytes.</span><span class="sxs-lookup"><span data-stu-id="8300b-469">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="8300b-470">**content_type** Tipo de HTTP, por ejemplo, "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="8300b-470">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="8300b-471">**content_type_length** Longitud del tipo HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-471">**content_type_length** Length of HTTP type</span></span>
- <span data-ttu-id="8300b-472">**additional_header** Puntero a texto de encabezado adicional.</span><span class="sxs-lookup"><span data-stu-id="8300b-472">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="8300b-473">**additional_header_length** Longitud del texto de encabezado adicional.</span><span class="sxs-lookup"><span data-stu-id="8300b-473">**additional_header_length** Length of additional header text</span></span>

<span data-ttu-id="8300b-474">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-474">**Return Values**</span></span>

- <span data-ttu-id="8300b-475">**NX_SUCCESS** (0x00) Encabezado creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-475">**NX_SUCCESS** (0x00) Successfully created header</span></span>
- <span data-ttu-id="8300b-476">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-476">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-477">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-477">**Allowed From**</span></span>

<span data-ttu-id="8300b-478">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-478">Threads</span></span>

<span data-ttu-id="8300b-479">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-479">**Example**</span></span>

```c
  CHAR demotestbuffer[] = “<html>\r\n\r\n<head>\r\n\r\n<title>Main                    \
                          Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n     \
                          </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
   the HTTP server in nx_http_server_create, creates a response to the received
   Client request. */

   UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, NX_PACKET *recv_packet_ptr)
   {
     NX_PACKET *sresp_packet_ptr;
     ULONG string_length;
     CHAR temp_string[30];
     ULONG length = 0;

     length = sizeof(demotestbuffer) - 1;

    /* Derive the client request type from the client request. */
       string_length = (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr >>
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
                length, server_ptr ->
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

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="8300b-480">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="8300b-480">nx_http_server_callback_packet_send</span></span>

### <a name="send-an-http-packet-from-callback-function"></a><span data-ttu-id="8300b-481">Envío un paquete HTTP desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="8300b-481">Send an HTTP packet from callback function</span></span>

<span data-ttu-id="8300b-482">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-482">**Prototype**</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

<span data-ttu-id="8300b-483">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-483">**Description**</span></span>

<span data-ttu-id="8300b-484">Este servicio envía una respuesta completa del servidor HTTP desde una devolución de llamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-484">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="8300b-485">El servidor HTTP enviará el paquete con NX_HTTP_SERVER_TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="8300b-485">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="8300b-486">El encabezado y los datos HTTP deben anexarse al paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-486">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="8300b-487">Si el estado devuelto indica un error, la aplicación HTTP debe liberar el paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-487">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="8300b-488">La devolución de llamada debe devolver NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="8300b-488">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8300b-489">Consulte *nx_http_server_callback_generate_response_header()* para ver un ejemplo más detallado.</span><span class="sxs-lookup"><span data-stu-id="8300b-489">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

<span data-ttu-id="8300b-490">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-490">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-491">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-491">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="8300b-492">**packet_ptr** Puntero al paquete que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="8300b-492">**packet_ptr** Pointer to the packet to send</span></span>

<span data-ttu-id="8300b-493">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-493">**Return Values**</span></span>

- <span data-ttu-id="8300b-494">**NX_SUCCESS** (0x00) Paquete de servidor HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-494">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="8300b-495">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-495">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-496">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-496">**Allowed From**</span></span>

<span data-ttu-id="8300b-497">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-497">Threads</span></span>

<span data-ttu-id="8300b-498">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-498">**Example**</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
Client directly. */

   status = nx_http_server_callback_response_send**(server_ptr, packet_ptr);
   
   if (status != NX_SUCCESS)
   {
        nx_packet_release(packet_ptr);
   }
    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="8300b-499">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="8300b-499">nx_http_server_callback_response_send</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="8300b-500">Envío de una respuesta desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="8300b-500">Send response from callback function</span></span>

<span data-ttu-id="8300b-501">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-501">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

<span data-ttu-id="8300b-502">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-502">**Description**</span></span>

<span data-ttu-id="8300b-503">Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8300b-503">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="8300b-504">Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST.</span><span class="sxs-lookup"><span data-stu-id="8300b-504">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="8300b-505">Tenga en cuenta que si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="8300b-505">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8300b-506">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8300b-506">This service is deprecated.</span></span> <span data-ttu-id="8300b-507">Se recomienda a los desarrolladores migrar a *nx_http_server_callback_response_send_extended()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-507">Developers are encouraged to migrate to *nx_http_server_callback_response_send_extended().*</span></span>

<span data-ttu-id="8300b-508">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-508">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-509">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-509">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8300b-510">**header** Puntero a la cadena de encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="8300b-510">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="8300b-511">**information** Puntero a la cadena de información.</span><span class="sxs-lookup"><span data-stu-id="8300b-511">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="8300b-512">**additional_info** Puntero a la cadena de información adicional.</span><span class="sxs-lookup"><span data-stu-id="8300b-512">**additional_info** Pointer to the additional information string.</span></span>

<span data-ttu-id="8300b-513">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-513">**Return Values**</span></span>

- <span data-ttu-id="8300b-514">**NX_SUCCESS** (0x00) Respuesta de servidor HTTP enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-514">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

<span data-ttu-id="8300b-515">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-515">**Allowed From**</span></span>

<span data-ttu-id="8300b-516">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-516">Threads</span></span>

<span data-ttu-id="8300b-517">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-517">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
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

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="8300b-518">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="8300b-518">nx_http_server_callback_response_send_extended</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="8300b-519">Envío de una respuesta desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="8300b-519">Send response from callback function</span></span>

<span data-ttu-id="8300b-520">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-520">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

<span data-ttu-id="8300b-521">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-521">**Description**</span></span>

<span data-ttu-id="8300b-522">Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8300b-522">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="8300b-523">Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST.</span><span class="sxs-lookup"><span data-stu-id="8300b-523">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="8300b-524">Tenga en cuenta que si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="8300b-524">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="8300b-525">Este servicio reemplaza a *nx_http_server_callback_response_send()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-525">This service replaces *nx_http_server_callback_response_send().*</span></span> <span data-ttu-id="8300b-526">Esta versión toma la información de longitud como argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="8300b-526">This version takes length information as input argument.</span></span>

<span data-ttu-id="8300b-527">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-527">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-528">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-528">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8300b-529">**header** Puntero a la cadena de encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="8300b-529">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="8300b-530">**header_length** Longitud de la cadena de encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="8300b-530">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="8300b-531">**information** Puntero a la cadena de información.</span><span class="sxs-lookup"><span data-stu-id="8300b-531">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="8300b-532">**information_length** Longitud de la cadena de información.</span><span class="sxs-lookup"><span data-stu-id="8300b-532">**information_length** Length of the information string.</span></span>
- <span data-ttu-id="8300b-533">**additional_info** Puntero a la cadena de información adicional.</span><span class="sxs-lookup"><span data-stu-id="8300b-533">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="8300b-534">**additional_info_length** Longitud de la cadena de información adicional.</span><span class="sxs-lookup"><span data-stu-id="8300b-534">**additional_info_length** Length of the additional information string.</span></span>

<span data-ttu-id="8300b-535">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-535">**Return Values**</span></span>

- <span data-ttu-id="8300b-536">**NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-536">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

<span data-ttu-id="8300b-537">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-537">**Allowed From**</span></span>

<span data-ttu-id="8300b-538">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-538">Threads</span></span>

<span data-ttu-id="8300b-539">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-539">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
           a resource not found response. */
           nx_http_server_callback_response_send_extended(server_ptr,
                                                         "HTTP/1.0 404 ", 12,
                                                         "NetX HTTP Server unable to find
                                                         file: ", 38, resource, 9);
        /* Return completion status. */
           return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="8300b-540">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="8300b-540">nx_http_server_content_get</span></span>

### <a name="get-content-from-the-request"></a><span data-ttu-id="8300b-541">Obtención de contenido de la solicitud</span><span class="sxs-lookup"><span data-stu-id="8300b-541">Get content from the request</span></span>

<span data-ttu-id="8300b-542">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-542">**Prototype**</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

<span data-ttu-id="8300b-543">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-543">**Description**</span></span>

<span data-ttu-id="8300b-544">Este servicio intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST o PUT.</span><span class="sxs-lookup"><span data-stu-id="8300b-544">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="8300b-545">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="8300b-545">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="8300b-546">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8300b-546">This service is deprecated.</span></span> <span data-ttu-id="8300b-547">Se recomienda a los desarrolladores migrar a nx_http_server_content_get_extended().</span><span class="sxs-lookup"><span data-stu-id="8300b-547">Developers are encouraged to migrate to nx_http_server_content_get_extended().</span></span>

<span data-ttu-id="8300b-548">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-548">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-549">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-549">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8300b-550">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-550">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8300b-551">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-551">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="8300b-552">**byte_offset** Número de bytes que se van a desplazar en el área de contenido.</span><span class="sxs-lookup"><span data-stu-id="8300b-552">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="8300b-553">**destination_ptr** Puntero al área de destino para el contenido.</span><span class="sxs-lookup"><span data-stu-id="8300b-553">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="8300b-554">**destination_size** Número máximo de bytes disponibles en el área de destino.</span><span class="sxs-lookup"><span data-stu-id="8300b-554">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="8300b-555">**actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.</span><span class="sxs-lookup"><span data-stu-id="8300b-555">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="8300b-556">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-556">**Return Values**</span></span>

- <span data-ttu-id="8300b-557">**NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-557">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="8300b-558">**NX_HTTP_ERROR** (0xE0) Error interno del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-558">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="8300b-559">**NX_HTTP_DATA_END** (0xE7) Fin del contenido de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-559">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="8300b-560">**NX_WEB_HTTP_TIMEOUT** (0xE1) Tiempo de espera del servidor HTTP para obtener el siguiente paquete de contenido.</span><span class="sxs-lookup"><span data-stu-id="8300b-560">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="8300b-561">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-561">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-562">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-562">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-563">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-563">**Allowed From**</span></span>

<span data-ttu-id="8300b-564">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-564">Threads</span></span>

<span data-ttu-id="8300b-565">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-565">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get(&my_server, packet_ptr,
                                   0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="8300b-566">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="8300b-566">nx_http_server_content_get_extended</span></span>

### <a name="get-content-from-the-requestsupports-zero-length-content-length"></a><span data-ttu-id="8300b-567">Obtención de contenido de la solicitud/admite la longitud del contenido de longitud cero</span><span class="sxs-lookup"><span data-stu-id="8300b-567">Get content from the request/supports zero length Content Length</span></span>

<span data-ttu-id="8300b-568">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-568">**Prototype**</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

<span data-ttu-id="8300b-569">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-569">**Description**</span></span>

<span data-ttu-id="8300b-570">Este servicio es casi idéntico a *nx_http_server_content_get();* intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST O PUT.</span><span class="sxs-lookup"><span data-stu-id="8300b-570">This service is almost identical to *nx_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="8300b-571">Sin embargo, administra las solicitudes con longitud de contenido de valor cero ("solicitud vacía") como solicitud válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-571">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="8300b-572">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="8300b-572">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="8300b-573">Este servicio reemplaza a *nx_http_server_content_get()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-573">This service replaces *nx_http_server_content_get().*</span></span> <span data-ttu-id="8300b-574">Esta versión requiere que el autor de la llamada proporcione información de longitud adicional.</span><span class="sxs-lookup"><span data-stu-id="8300b-574">This version requires caller to supply additional length information.</span></span>

<span data-ttu-id="8300b-575">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-575">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-576">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-576">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8300b-577">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-577">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8300b-578">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-578">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="8300b-579">**byte_offset** Número de bytes que se van a desplazar en el área de contenido.</span><span class="sxs-lookup"><span data-stu-id="8300b-579">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="8300b-580">**destination_ptr** Puntero al área de destino para el contenido.</span><span class="sxs-lookup"><span data-stu-id="8300b-580">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="8300b-581">**destination_size** Número máximo de bytes disponibles en el área de destino.</span><span class="sxs-lookup"><span data-stu-id="8300b-581">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="8300b-582">**actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.</span><span class="sxs-lookup"><span data-stu-id="8300b-582">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="8300b-583">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-583">**Return Values**</span></span>

- <span data-ttu-id="8300b-584">**NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-584">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="8300b-585">**NX_HTTP_ERROR** (0xE0) Error interno del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-585">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="8300b-586">**NX_HTTP_DATA_END** (0xE7) Fin del contenido de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-586">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="8300b-587">**NX_WEB_HTTP_TIMEOUT** (0xE1) Tiempo de espera del servidor HTTP para obtener el siguiente paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-587">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="8300b-588">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-589">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-589">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-590">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-590">**Allowed From**</span></span>

<span data-ttu-id="8300b-591">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-591">Threads</span></span>

<span data-ttu-id="8300b-592">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-592">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get_extended(&my_server, packet_ptr,
                                            0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="8300b-593">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="8300b-593">nx_http_server_content_length_get</span></span>

### <a name="get-length-of-content-in-the-request"></a><span data-ttu-id="8300b-594">Obtención de la longitud del contenido de la solicitud</span><span class="sxs-lookup"><span data-stu-id="8300b-594">Get length of content in the request</span></span>

<span data-ttu-id="8300b-595">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-595">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
<span data-ttu-id="8300b-596">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-596">**Description**</span></span>

<span data-ttu-id="8300b-597">Este servicio intenta recuperar la longitud del contenido HTTP en el paquete proporcionado.</span><span class="sxs-lookup"><span data-stu-id="8300b-597">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="8300b-598">Si no hay contenido HTTP, esta rutina devuelve un valor de cero.</span><span class="sxs-lookup"><span data-stu-id="8300b-598">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="8300b-599">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="8300b-599">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="8300b-600">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8300b-600">This service is deprecated.</span></span> <span data-ttu-id="8300b-601">Se recomienda a los desarrolladores migrar a nx_http_server_content_length_get_extended().</span><span class="sxs-lookup"><span data-stu-id="8300b-601">Developers are encouraged to migrate to nx_http_server_content_length_get_extended().</span></span>

<span data-ttu-id="8300b-602">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-602">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-603">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-603">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8300b-604">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-604">Note that this packet must not be released by the request notify callback.</span></span>

<span data-ttu-id="8300b-605">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-605">**Return Values**</span></span>

- <span data-ttu-id="8300b-606">**content length** Si hay error, se devuelve un valor de cero.</span><span class="sxs-lookup"><span data-stu-id="8300b-606">**content length** On error, a value of zero is returned</span></span>

<span data-ttu-id="8300b-607">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-607">**Allowed From**</span></span>

<span data-ttu-id="8300b-608">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-608">Threads</span></span>

<span data-ttu-id="8300b-609">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-609">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
length = nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="8300b-610">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="8300b-610">nx_http_server_content_length_get_extended</span></span>

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a><span data-ttu-id="8300b-611">Obtención de la longitud del contenido de la solicitud/admite la longitud del contenido de cero</span><span class="sxs-lookup"><span data-stu-id="8300b-611">Get length of content in the request/supports Content Length of zero value</span></span>

<span data-ttu-id="8300b-612">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-612">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

<span data-ttu-id="8300b-613">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-613">**Description**</span></span>

<span data-ttu-id="8300b-614">Este servicio es similar a *nx_http_server_content_length_get()* ; intenta recuperar la longitud del contenido HTTP en el paquete proporcionado.</span><span class="sxs-lookup"><span data-stu-id="8300b-614">This service is similar to *nx_http_server_content_length_get()*; attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="8300b-615">Sin embargo, el valor devuelto indica el estado de finalización correcta y el valor de longitud real se devuelve en el puntero de entrada content_length.</span><span class="sxs-lookup"><span data-stu-id="8300b-615">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="8300b-616">Si no hay contenido HTTP/longitud de contenido = 0, esta rutina sigue devolviendo un estado de finalización correcta y el puntero de entrada content_length apunta a una longitud válida (cero).</span><span class="sxs-lookup"><span data-stu-id="8300b-616">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="8300b-617">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="8300b-617">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="8300b-618">Este servicio reemplaza a *nx_http_server_content_length_get()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-618">This service replaces *nx_http_server_content_length_get*().</span></span>

<span data-ttu-id="8300b-619">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-619">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-620">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-620">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="8300b-621">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-621">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="8300b-622">**CONTENT_LENGTH** Puntero al valor recuperado del campo de longitud de contenido.</span><span class="sxs-lookup"><span data-stu-id="8300b-622">**content_length** Pointer to value retrieved from Content Length field</span></span>

<span data-ttu-id="8300b-623">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-623">**Return Values**</span></span>

- <span data-ttu-id="8300b-624">**NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-624">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="8300b-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Formato de encabezado HTTP incorrecto</span><span class="sxs-lookup"><span data-stu-id="8300b-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
- <span data-ttu-id="8300b-626">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-626">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-627">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-627">**Allowed From**</span></span>

<span data-ttu-id="8300b-628">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-628">Threads</span></span>

<span data-ttu-id="8300b-629">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-629">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
ULONG content_length;

status = nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="8300b-630">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="8300b-630">nx_http_server_create</span></span>

### <a name="create-an-http-server-instance"></a><span data-ttu-id="8300b-631">Creación de una instancia de servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="8300b-631">Create an HTTP Server instance</span></span>

<span data-ttu-id="8300b-632">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-632">**Prototype**</span></span>

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

<span data-ttu-id="8300b-633">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-633">**Description**</span></span>

<span data-ttu-id="8300b-634">Este servicio crea una instancia de servidor HTTP que se ejecuta en el contexto de su propio subproceso ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8300b-634">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="8300b-635">Las rutinas de devolución de llamada de aplicación *authentication_check* y *request_notify* opcionales proporcionan al software de aplicación control sobre las operaciones básicas del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-635">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="8300b-636">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-636">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-637">**http_server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-637">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="8300b-638">**http_server_name** Puntero al nombre del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-638">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="8300b-639">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8300b-639">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="8300b-640">**media_ptr** Puntero a la instancia de medios FileX creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8300b-640">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="8300b-641">**stack_ptr** Puntero al área de la pila de subprocesos del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-641">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="8300b-642">**stack_size** Puntero al tamaño de la pila de subprocesos del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-642">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="8300b-643">**authentication_check** Puntero de función a la rutina de comprobación de autenticación de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8300b-643">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="8300b-644">Si se especifica, se llama a esta rutina para cada solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-644">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="8300b-645">Si este parámetro es NULL, no se realizará ninguna autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-645">If this parameter is NULL no authentication will be performed.</span></span>
- <span data-ttu-id="8300b-646">**request_notify** Puntero de función a la rutina de notificación de solicitud de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8300b-646">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="8300b-647">Si se especifica, se llama a esta rutina antes de que se procese el servidor HTTP de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="8300b-647">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="8300b-648">Esto permite que se redirija el nombre del recurso o que los campos de un recurso se actualicen antes de completar la solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-648">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

<span data-ttu-id="8300b-649">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-649">**Return Values**</span></span>

- <span data-ttu-id="8300b-650">**NX_SUCCESS**: (0x00) Servidor HTTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-650">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="8300b-651">NX_PTR_ERROR (0x07) El puntero de servidor HTTP, dirección IP, medio, pila o grupo de paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="8300b-651">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="8300b-652">NX_HTTP_POOL_ERROR (0xE9) La carga de paquetes del grupo no es lo suficientemente grande como para contener una solicitud HTTP completa.</span><span class="sxs-lookup"><span data-stu-id="8300b-652">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

<span data-ttu-id="8300b-653">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-653">**Allowed From**</span></span>

<span data-ttu-id="8300b-654">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-654">Initialization, Threads</span></span>

<span data-ttu-id="8300b-655">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-655">**Example**</span></span>

```c
/* Create an HTTP Server instance called “my_server.” */
status = nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
                              stack_ptr, stack_size, &pool_0,
                              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="8300b-656">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="8300b-656">nx_http_server_delete</span></span>

### <a name="delete-an-http-server-instance"></a><span data-ttu-id="8300b-657">Eliminación de una instancia de servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="8300b-657">Delete an HTTP Server instance</span></span>

<span data-ttu-id="8300b-658">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-658">**Prototype**</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="8300b-659">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-659">**Description**</span></span>

<span data-ttu-id="8300b-660">Este servicio elimina una instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8300b-660">This service deletes a previously created HTTP Server instance.</span></span>

<span data-ttu-id="8300b-661">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-661">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-662">**http_server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-662">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

<span data-ttu-id="8300b-663">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-663">**Return Values**</span></span>

- <span data-ttu-id="8300b-664">**NX_SUCCESS** (0x00) Servidor HTTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-664">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="8300b-665">NX_PTR_ERROR (0x07) Puntero de servidor HTTP no válido.</span><span class="sxs-lookup"><span data-stu-id="8300b-665">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="8300b-666">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-666">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-667">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-667">**Allowed From**</span></span>

<span data-ttu-id="8300b-668">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-668">Threads</span></span>

<span data-ttu-id="8300b-669">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-669">**Example**</span></span>

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="8300b-670">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="8300b-670">nx_http_server_get_entity_content</span></span>

### <a name="retrieve-the-location-and-length-of-entity-data"></a><span data-ttu-id="8300b-671">Recuperación de la ubicación y la longitud de los datos de entidad</span><span class="sxs-lookup"><span data-stu-id="8300b-671">Retrieve the location and length of entity data</span></span>

<span data-ttu-id="8300b-672">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-672">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="8300b-673">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-673">**Description**</span></span>

<span data-ttu-id="8300b-674">Este servicio determina la ubicación del inicio de los datos dentro de la entidad actual de varias partes en los mensajes de cliente recibidos y la longitud de los datos que no incluyen la cadena de límite.</span><span class="sxs-lookup"><span data-stu-id="8300b-674">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="8300b-675">Internamente, el servidor HTTP actualiza sus propios desplazamientos para que se pueda volver a llamar a esta función en el mismo datagrama de cliente para mensajes con varias entidades.</span><span class="sxs-lookup"><span data-stu-id="8300b-675">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="8300b-676">El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.</span><span class="sxs-lookup"><span data-stu-id="8300b-676">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="8300b-677">Tenga en cuenta que NX_WEB_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-677">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="8300b-678">Para más información, consulte *nx_web_http_server_get_entity_header*.</span><span class="sxs-lookup"><span data-stu-id="8300b-678">See *nx_http_server_get_entity_header* for more details.</span></span>

<span data-ttu-id="8300b-679">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-679">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-680">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-680">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="8300b-681">**packet_pptr** Puntero a la ubicación del puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-681">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="8300b-682">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-682">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="8300b-683">**available_offset** Puntero para desplazar los datos de entidad desde el puntero antepuesto de paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-683">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="8300b-684">**available_length** Puntero a la longitud de los datos de entidad.</span><span class="sxs-lookup"><span data-stu-id="8300b-684">**available_length** Pointer to length of entity data</span></span>

<span data-ttu-id="8300b-685">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-685">**Return Values**</span></span>

- <span data-ttu-id="8300b-686">**NX_SUCCESS** (0x00) Tamaño y ubicación del contenido de la entidad recuperados correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-686">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="8300b-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Ya se encontró el contenido interno de los marcadores de varias partes del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="8300b-688">NX_HTTP_ERROR (0xE0) Error interno del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-688">NX_HTTP_ERROR (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="8300b-689">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-689">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-690">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-690">**Allowed From**</span></span>

<span data-ttu-id="8300b-691">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-691">Threads</span></span>

<span data-ttu-id="8300b-692">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-692">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

UINT         offset, length;
NX_PACKET    *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
the entity header to determine details about the multipart data. If
successful, it then calls this service to get the location of entity data: */
status = nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
                                          &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="8300b-693">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="8300b-693">nx_http_server_get_entity_header</span></span>

### <a name="retrieve-the-contents-of-entity-header"></a><span data-ttu-id="8300b-694">Recuperación del contenido del encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="8300b-694">Retrieve the contents of entity header</span></span>

<span data-ttu-id="8300b-695">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-695">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

<span data-ttu-id="8300b-696">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-696">**Description**</span></span>

<span data-ttu-id="8300b-697">Este servicio recupera el encabezado de entidad en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="8300b-697">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="8300b-698">Internamente, el servidor HTTP actualiza sus propios punteros para localizar la siguiente entidad de varias partes en un datagrama de cliente con varios encabezados de entidad.</span><span class="sxs-lookup"><span data-stu-id="8300b-698">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="8300b-699">El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.</span><span class="sxs-lookup"><span data-stu-id="8300b-699">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="8300b-700">Tenga en cuenta que NX_WEB_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-700">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="8300b-701">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-701">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-702">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-702">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="8300b-703">**packet_pptr** Puntero a la ubicación del puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-703">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="8300b-704">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-704">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="8300b-705">**entity_header_buffer** Puntero a la ubicación donde se va a almacenar el encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="8300b-705">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="8300b-706">**buffer_size** Tamaño del búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="8300b-706">**buffer_size** Size of input buffer</span></span>

<span data-ttu-id="8300b-707">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-707">**Return Values**</span></span>

- <span data-ttu-id="8300b-708">**NX_SUCCESS** (0x00) Encabezado de entidad recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-708">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
- <span data-ttu-id="8300b-709">**NX_HTTP_NOT_FOUND (0xE6)** No se encontró el campo de encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="8300b-709">**NX_HTTP_NOT_FOUND (0xE6)** Entity header field not found</span></span>
- <span data-ttu-id="8300b-710">**NX_HTTP_TIMEOUT (0xE1)** Se agotó el tiempo para recibir el siguiente paquete del mensaje de cliente de varios paquetes.</span><span class="sxs-lookup"><span data-stu-id="8300b-710">**NX_HTTP_TIMEOUT (0xE1)** Time expired to receive next packet for multipacket client message</span></span> 
- <span data-ttu-id="8300b-711">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-711">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-712">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-712">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="8300b-713">NX_HTTP_ERROR (0xE0) Error de HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="8300b-713">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>

<span data-ttu-id="8300b-714">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-714">**Allowed From**</span></span>

<span data-ttu-id="8300b-715">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-715">Threads</span></span>

<span data-ttu-id="8300b-716">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-716">**Example**</span></span>

```c
/* my_request_notify* is the application request notify callback registered with
the HTTP server in *nx_http_server_create,* creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

NX_PACKET     *sresp_packet_ptr;
UINT          offset, length;**
NX_PACKET     *response_pkt;
UCHAR         buffer[1440];

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
             "Server: NetX HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
                                              NX_SUCCESS)
        {
            nx_packet_release(response_pkt);
        }
    }
}
Else
{

        /* Indicate we have not processed the response to client yet.*/        
        return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="8300b-717">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="8300b-717">nx_http_server_gmt_callback_set</span></span>

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a><span data-ttu-id="8300b-718">Establecimiento de la devolución de llamada para obtener la fecha y hora GMT</span><span class="sxs-lookup"><span data-stu-id="8300b-718">Set the callback to obtain GMT date and time</span></span>

<span data-ttu-id="8300b-719">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-719">**Prototype**</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="8300b-720">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-720">**Description**</span></span>

<span data-ttu-id="8300b-721">Este servicio establece la devolución de llamada para obtener la fecha y hora GMT con un servidor HTTP creado previamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-721">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="8300b-722">Este servicio se invoca con el servidor HTTP y crea un encabezado en las respuestas del servidor HTTP al cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-722">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

<span data-ttu-id="8300b-723">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-723">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-724">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-724">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="8300b-725">**gmt_get** Puntero a la devolución de llamada GMT.</span><span class="sxs-lookup"><span data-stu-id="8300b-725">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="8300b-726">**date** Puntero a la fecha de recuperación.</span><span class="sxs-lookup"><span data-stu-id="8300b-726">**date** Pointer to the date retrieved</span></span>

<span data-ttu-id="8300b-727">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-727">**Return Values**</span></span>

- <span data-ttu-id="8300b-728">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-728">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8300b-729">NX_PTR_ERROR (0x07) Puntero de paquete o parámetro no válido.</span><span class="sxs-lookup"><span data-stu-id="8300b-729">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

<span data-ttu-id="8300b-730">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-730">**Allowed From**</span></span>

<span data-ttu-id="8300b-731">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-731">Threads</span></span>

<span data-ttu-id="8300b-732">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-732">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the GMT
retrieve callback: */

status = nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="8300b-733">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="8300b-733">nx_http_server_invalid_userpassword_notify_set</span></span>

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a><span data-ttu-id="8300b-734">Establecimiento de la devolución de llamada para controlar la contraseña o el usuario no válidos</span><span class="sxs-lookup"><span data-stu-id="8300b-734">Set the callback to to handle invalid user/password</span></span>

<span data-ttu-id="8300b-735">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-735">**Prototype**</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

<span data-ttu-id="8300b-736">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-736">**Description**</span></span>

<span data-ttu-id="8300b-737">Este servicio establece la devolución de llamada invocada cuando se recibe un nombre de usuario y una contraseña no válidos en una solicitud GET, PUT o DELETE de cliente, ya sea mediante autenticación implícita o básica.</span><span class="sxs-lookup"><span data-stu-id="8300b-737">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="8300b-738">El servidor HTTP se debe crear previamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-738">The HTTP server must be previously created.</span></span>

<span data-ttu-id="8300b-739">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-739">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-740">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-740">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="8300b-741">**invalid_username_password_callback** Puntero a una devolución de llamada de aprobado/usuario no válido.</span><span class="sxs-lookup"><span data-stu-id="8300b-741">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="8300b-742">**resource** Puntero al recurso especificado por el cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-742">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="8300b-743">**client_address** Dirección de cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-743">**client_address** Client address</span></span>
- <span data-ttu-id="8300b-744">**request_type** Indica el tipo de solicitud de cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-744">**request_type** Indicates client request type.</span></span> <span data-ttu-id="8300b-745">Puede ser:</span><span class="sxs-lookup"><span data-stu-id="8300b-745">May be:</span></span>
  - <span data-ttu-id="8300b-746">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="8300b-746">NX_HTTP_SERVER_GET_REQUEST</span></span>
  - <span data-ttu-id="8300b-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="8300b-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span></span>
  - <span data-ttu-id="8300b-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="8300b-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span></span>

<span data-ttu-id="8300b-749">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-749">**Return Values**</span></span>

- <span data-ttu-id="8300b-750">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-750">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8300b-751">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-751">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-752">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-752">**Allowed From**</span></span>

<span data-ttu-id="8300b-753">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-753">Threads</span></span>

<span data-ttu-id="8300b-754">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-754">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                        ULONG client_address,
                                        UINT request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the invalid
username password callback: */

status = nx_http_server_gmt_callback_set(&my_server,
                                        invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="8300b-755">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="8300b-755">nx_http_server_mime_maps_additional_set</span></span>

### <a name="set-additional-mime-maps-for-html"></a><span data-ttu-id="8300b-756">Establecimiento de asignaciones MIME adicionales para HTML</span><span class="sxs-lookup"><span data-stu-id="8300b-756">Set additional MIME maps for HTML</span></span> 

<span data-ttu-id="8300b-757">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-757">**Prototype**</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

<span data-ttu-id="8300b-758">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-758">**Description**</span></span>

<span data-ttu-id="8300b-759">Este servicio permite al desarrollador de aplicaciones HTTP agregar tipos MIME adicionales de los tipos MIME predeterminados proporcionados por el servidor NetX HTTP (consulte *nx_http_server_get_type* para ver una lista de tipos definidos).</span><span class="sxs-lookup"><span data-stu-id="8300b-759">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="8300b-760">Cuando se recibe una solicitud de cliente, por ejemplo, una solicitud GET, el servidor HTTP analiza el tipo de archivo solicitado del encabezado HTTP mediante el conjunto de asignaciones MIME adicional y, si no se encuentra ninguna coincidencia, busca una coincidencia en la asignación MIME predeterminada del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-760">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="8300b-761">Si no se encuentra ninguna coincidencia, el tipo MIME tiene como valor predeterminado "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="8300b-761">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="8300b-762">Si la función de notificación de solicitud se registra con el servidor HTTP, la devolución de llamada de solicitud de notificación puede llamar a *nx_http_server_type_retrieve()* para analizar el tipo de archivo.</span><span class="sxs-lookup"><span data-stu-id="8300b-762">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_get* to parse the file type.</span></span>

<span data-ttu-id="8300b-763">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-763">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-764">**server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-764">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8300b-765">**mime_maps** Puntero a una matriz de asignaciones MIME.</span><span class="sxs-lookup"><span data-stu-id="8300b-765">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="8300b-766">**mime_map_num** Número de asignaciones MIME en la matriz.</span><span class="sxs-lookup"><span data-stu-id="8300b-766">**mime_map_num** Number of MIME maps in array</span></span>

<span data-ttu-id="8300b-767">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-767">**Return Values**</span></span>

- <span data-ttu-id="8300b-768">**NX_SUCCESS**: (0x00) Asignación MIME del servidor HTTP establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-768">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="8300b-769">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-769">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-770">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-770">**Allowed From**</span></span>

<span data-ttu-id="8300b-771">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-771">Initialization, Threads</span></span>

<span data-ttu-id="8300b-772">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-772">**Example**</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_http_server_mime_maps_additional_set(&my_server,
                                                &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="8300b-773">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="8300b-773">nx_http_server_packet_content_find</span></span>

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a><span data-ttu-id="8300b-774">Extracción de la longitud del contenido y establece el puntero en el inicio de los datos</span><span class="sxs-lookup"><span data-stu-id="8300b-774">Extract content length and set pointer to start of data</span></span>

<span data-ttu-id="8300b-775">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-775">**Prototype**</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

<span data-ttu-id="8300b-776">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-776">**Description**</span></span>

<span data-ttu-id="8300b-777">Este servicio extrae la longitud del contenido del encabezado HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-777">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="8300b-778">También actualiza el paquete proporcionado de la siguiente manera: el puntero antepuesto de paquete (inicio de la ubicación del búfer de paquetes en el que se va a escribir) se establece en el contenido HTTP (datos) que se acaba de pasar al encabezado HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-778">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="8300b-779">Si no se encuentra el principio del contenido en el paquete actual, la función espera a que se reciba el siguiente paquete mediante la opción de espera NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="8300b-779">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="8300b-780">Tenga en cuenta que no se debe llamar a esta función antes que a *nx_web_http_server_get_entity_header()* , ya que modifica el puntero de anteposición más allá del encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="8300b-780">Note this should not be called before calling *nx_http_server_get_entity_header()* because it modifies the prepend pointer past the entity header.</span></span>

<span data-ttu-id="8300b-781">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-781">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-782">**server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-782">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="8300b-783">**packet_ptr** Puntero al puntero de paquete para devolver el paquete con el puntero antepuesto actualizado.</span><span class="sxs-lookup"><span data-stu-id="8300b-783">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="8300b-784">**CONTENT_LENGTH** Puntero al valor content_length extraído.</span><span class="sxs-lookup"><span data-stu-id="8300b-784">**content_length** Pointer to extracted content_length</span></span>

<span data-ttu-id="8300b-785">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-785">**Return Values**</span></span>

- <span data-ttu-id="8300b-786">**NX_SUCCESS** (0x00) Se encontró la longitud del contenido HTTP y el paquete se actualizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-786">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="8300b-787">**NX_HTTP_TIMEOUT** (0xE1) Tiempo agotado esperando al siguiente paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-787">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="8300b-788">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-788">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-789">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-789">**Allowed From**</span></span>

<span data-ttu-id="8300b-790">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-790">Threads</span></span>

<span data-ttu-id="8300b-791">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-791">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function 
registere with the HTTP server. */

UINT content_length;

status = nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                           &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="8300b-792">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="8300b-792">nx_http_server_packet_get</span></span>

### <a name="receive-the-next-http-packet"></a><span data-ttu-id="8300b-793">Recepción del siguiente paquete HTTP</span><span class="sxs-lookup"><span data-stu-id="8300b-793">Receive the next HTTP packet</span></span>

<span data-ttu-id="8300b-794">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-794">**Prototype**</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

<span data-ttu-id="8300b-795">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-795">**Description**</span></span>

<span data-ttu-id="8300b-796">Este servicio devuelve el siguiente paquete recibido en el socket de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-796">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="8300b-797">La opción de espera para recibir un paquete es NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="8300b-797">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="8300b-798">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-798">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-799">**server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-799">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="8300b-800">**packet_ptr** Puntero al paquete recibido.</span><span class="sxs-lookup"><span data-stu-id="8300b-800">**packet_ptr** Pointer to received packet</span></span>

<span data-ttu-id="8300b-801">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-801">**Return Values**</span></span>

- <span data-ttu-id="8300b-802">**NX_SUCCESS** (0x00) Siguiente paquete HTTP recibido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-802">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="8300b-803">**NX_HTTP_TIMEOUT** (0xE1) Tiempo agotado esperando al siguiente paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-803">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="8300b-804">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-804">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-805">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-805">**Allowed From**</span></span>

<span data-ttu-id="8300b-806">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-806">Threads</span></span>

<span data-ttu-id="8300b-807">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-807">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="8300b-808">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="8300b-808">nx_http_server_param_get</span></span>

### <a name="get-parameter-from-the-request"></a><span data-ttu-id="8300b-809">Obtención del parámetro de la solicitud</span><span class="sxs-lookup"><span data-stu-id="8300b-809">Get parameter from the request</span></span>

<span data-ttu-id="8300b-810">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-810">**Prototype**</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

<span data-ttu-id="8300b-811">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-811">**Description**</span></span>

<span data-ttu-id="8300b-812">Este servicio intenta recuperar el parámetro de dirección URL HTTP especificado en el paquete de solicitud proporcionado.</span><span class="sxs-lookup"><span data-stu-id="8300b-812">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="8300b-813">Si el parámetro HTTP solicitado no está presente, esta rutina devuelve un estado de NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="8300b-813">If the requested HTTP parameter is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="8300b-814">Se debe llamar a esta rutina desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="8300b-814">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="8300b-815">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-815">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-816">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-816">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="8300b-817">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-817">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="8300b-818">**param_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de parámetros.</span><span class="sxs-lookup"><span data-stu-id="8300b-818">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="8300b-819">**param_ptr** Área de destino para copiar el parámetro.</span><span class="sxs-lookup"><span data-stu-id="8300b-819">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="8300b-820">**max_param_size** Tamaño máximo del área de destino del parámetro.</span><span class="sxs-lookup"><span data-stu-id="8300b-820">**max_param_size** Maximum size of the parameter destination area.</span></span>

<span data-ttu-id="8300b-821">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-821">**Return Values**</span></span>

- <span data-ttu-id="8300b-822">**NX_SUCCESS** (0X00) Parámetro del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-822">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="8300b-823">**NX_WEB_HTTP_NOT_FOUND** (0xE6) Parámetro especificado no encontrado.</span><span class="sxs-lookup"><span data-stu-id="8300b-823">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
- <span data-ttu-id="8300b-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Parámetro de solicitud no terminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
- <span data-ttu-id="8300b-825">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-825">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-826">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-827">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-827">**Allowed From**</span></span>

<span data-ttu-id="8300b-828">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-828">Threads</span></span>

<span data-ttu-id="8300b-829">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-829">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first parameter of the HTTP Client request. */

status = nx_http_server_param_get(request_packet_ptr, 0, param_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="8300b-830">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="8300b-830">nx_http_server_query_get</span></span>

### <a name="get-query-from-the-request"></a><span data-ttu-id="8300b-831">Obtiene la consulta de la solicitud</span><span class="sxs-lookup"><span data-stu-id="8300b-831">Get query from the request</span></span>

<span data-ttu-id="8300b-832">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-832">**Prototype**</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

<span data-ttu-id="8300b-833">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-833">**Description**</span></span>

<span data-ttu-id="8300b-834">Este servicio intenta recuperar la consulta de dirección URL HTTP especificada en el paquete de solicitud proporcionado.</span><span class="sxs-lookup"><span data-stu-id="8300b-834">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="8300b-835">Si la consulta HTTP solicitada no está presente, esta rutina devuelve un estado de NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="8300b-835">If the requested HTTP query is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="8300b-836">Se debe llamar a esta rutina desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="8300b-836">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="8300b-837">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-837">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-838">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-838">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="8300b-839">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="8300b-839">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="8300b-840">**query_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de consultas.</span><span class="sxs-lookup"><span data-stu-id="8300b-840">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="8300b-841">**query_ptr** Área de destino en la que se va a copiar la consulta.</span><span class="sxs-lookup"><span data-stu-id="8300b-841">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="8300b-842">**max_query_size** Tamaño máximo del área de destino de la consulta.</span><span class="sxs-lookup"><span data-stu-id="8300b-842">**max_query_size** Maximum size of the query destination area.</span></span>

<span data-ttu-id="8300b-843">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-843">**Return Values**</span></span>

- <span data-ttu-id="8300b-844">**NX_SUCCESS**: (0x00) Consulta del servidor HTTP obtenida correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-844">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="8300b-845">**NX_HTTP_FAILED** (0xE2) Tamaño de consulta demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="8300b-845">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
- <span data-ttu-id="8300b-846">**NX_HTTP_NOT_FOUND** (0xE6) No se encontró la consulta especificada.</span><span class="sxs-lookup"><span data-stu-id="8300b-846">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
- <span data-ttu-id="8300b-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No hay ninguna consulta en la solicitud de cliente.</span><span class="sxs-lookup"><span data-stu-id="8300b-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
- <span data-ttu-id="8300b-848">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-848">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-849">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-849">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-850">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-850">**Allowed From**</span></span>

<span data-ttu-id="8300b-851">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-851">Threads</span></span>

<span data-ttu-id="8300b-852">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-852">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first query of the HTTP Client request. */
status = nx_http_server_query_get(request_packet_ptr, 0, query_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
in “query_destination.” */
```

##   
<span data-ttu-id="8300b-853">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="8300b-853">nx_http_server_start</span></span>

### <a name="start-the-http-server"></a><span data-ttu-id="8300b-854">Inicio del servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="8300b-854">Start the HTTP Server</span></span>

<span data-ttu-id="8300b-855">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-855">**Prototype**</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="8300b-856">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-856">**Description**</span></span>

<span data-ttu-id="8300b-857">Este servicio inicia la instancia de servidor HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8300b-857">This service starts the previously create HTTP Server instance.</span></span>

<span data-ttu-id="8300b-858">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-858">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-859">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-859">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="8300b-860">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-860">**Return Values**</span></span>

- <span data-ttu-id="8300b-861">**NX_SUCCESS** (0x00) Servidor HTTP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-861">**NX_SUCCESS** (0x00) Successful HTTP Server start</span></span>
- <span data-ttu-id="8300b-862">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-862">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-863">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-863">**Allowed From**</span></span>

<span data-ttu-id="8300b-864">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-864">Initialization, Threads</span></span>

<span data-ttu-id="8300b-865">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-865">**Example**</span></span>

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="8300b-866">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="8300b-866">nx_http_server_stop</span></span>

### <a name="stop-the-http-server"></a><span data-ttu-id="8300b-867">Detención del servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="8300b-867">Stop the HTTP Server</span></span>

<span data-ttu-id="8300b-868">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-868">**Prototype**</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="8300b-869">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-869">**Description**</span></span>

<span data-ttu-id="8300b-870">Este servicio detiene la instancia de servidor HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8300b-870">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="8300b-871">Se debe llamar a esta rutina antes de eliminar una instancia del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-871">This routine should be called prior to deleting an HTTP Server instance.</span></span>

<span data-ttu-id="8300b-872">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-872">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-873">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-873">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="8300b-874">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-874">**Return Values**</span></span>

- <span data-ttu-id="8300b-875">**NX_SUCCESS** (0x00) Servidor HTTP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-875">**NX_SUCCESS** (0x00) Successful HTTP Server stop</span></span>
- <span data-ttu-id="8300b-876">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-876">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-877">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="8300b-877">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="8300b-878">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-878">**Allowed From**</span></span>

<span data-ttu-id="8300b-879">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="8300b-879">Threads</span></span>

<span data-ttu-id="8300b-880">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-880">**Example**</span></span>

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="8300b-881">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="8300b-881">nx_http_server_type_get</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="8300b-882">Extracción del tipo de archivo de la solicitud HTTP del cliente</span><span class="sxs-lookup"><span data-stu-id="8300b-882">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="8300b-883">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-883">**Prototype**</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

<span data-ttu-id="8300b-884">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-884">**Description**</span></span>

<span data-ttu-id="8300b-885">Este servicio extrae el tipo de solicitud HTTP en el búfer *http_type_string* y su longitud en el valor devuelto por el *nombre* de búfer de entrada, normalmente la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="8300b-885">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="8300b-886">Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="8300b-886">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="8300b-887">En caso contrario, compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias.</span><span class="sxs-lookup"><span data-stu-id="8300b-887">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="8300b-888">Los mapas MIME predeterminados del servidor HTTP de NetX son:</span><span class="sxs-lookup"><span data-stu-id="8300b-888">The default MIME maps in NetX HTTP Server are:</span></span>

- <span data-ttu-id="8300b-889">texto html/html</span><span class="sxs-lookup"><span data-stu-id="8300b-889">html text/html</span></span>
- <span data-ttu-id="8300b-890">texto htm/html</span><span class="sxs-lookup"><span data-stu-id="8300b-890">htm text/html</span></span>
- <span data-ttu-id="8300b-891">texto txt/plain</span><span class="sxs-lookup"><span data-stu-id="8300b-891">txt text/plain</span></span>
- <span data-ttu-id="8300b-892">imagen gif/gif</span><span class="sxs-lookup"><span data-stu-id="8300b-892">gif image/gif</span></span>
- <span data-ttu-id="8300b-893">imagen jpg/jpeg</span><span class="sxs-lookup"><span data-stu-id="8300b-893">jpg image/jpeg</span></span>
- <span data-ttu-id="8300b-894">imagen ico/x-icon</span><span class="sxs-lookup"><span data-stu-id="8300b-894">ico image/x-icon</span></span>

<span data-ttu-id="8300b-895">Si se proporciona, también buscará un conjunto definido por el usuario de asignaciones MIME adicionales.</span><span class="sxs-lookup"><span data-stu-id="8300b-895">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="8300b-896">Consulte *nx_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="8300b-896">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="8300b-897">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="8300b-897">This service is deprecated.</span></span> <span data-ttu-id="8300b-898">Se recomienda a los desarrolladores migrar a *nx_http_server_type_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-898">Developers are encouraged to migrate to *nx_http_server_type_get_extended().*</span></span>

<span data-ttu-id="8300b-899">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-899">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-900">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-900">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8300b-901">**name** Puntero al búfer para buscar.</span><span class="sxs-lookup"><span data-stu-id="8300b-901">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="8300b-902">**http_type_string** (Puntero a la cadena de tipo HTML extraída).</span><span class="sxs-lookup"><span data-stu-id="8300b-902">**http_type_string** (Pointer to extracted HTML type)</span></span>

<span data-ttu-id="8300b-903">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-903">**Return Values**</span></span>

- <span data-ttu-id="8300b-904">**Longitud de la cadena en bytes** Un valor distinto de cero es correcto.</span><span class="sxs-lookup"><span data-stu-id="8300b-904">**Length of string in bytes** Non zero value is success</span></span>
- <span data-ttu-id="8300b-905">**Cero indica un error**</span><span class="sxs-lookup"><span data-stu-id="8300b-905">**Zero indicates error**</span></span>

<span data-ttu-id="8300b-906">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-906">**Allowed From**</span></span>

<span data-ttu-id="8300b-907">Application</span><span class="sxs-lookup"><span data-stu-id="8300b-907">Application</span></span>

<span data-ttu-id="8300b-908">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-908">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="8300b-909">Para un ejemplo más detallado, consulte la descripción de</span><span class="sxs-lookup"><span data-stu-id="8300b-909">For a more detailed example, see the description for</span></span>

<span data-ttu-id="8300b-910">*nx_http_server_callback_generate_response_header.*</span><span class="sxs-lookup"><span data-stu-id="8300b-910">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="8300b-911">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="8300b-911">nx_http_server_type_get_extended</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="8300b-912">Extracción del tipo de archivo de la solicitud HTTP del cliente</span><span class="sxs-lookup"><span data-stu-id="8300b-912">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="8300b-913">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-913">**Prototype**</span></span>

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

<span data-ttu-id="8300b-914">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-914">**Description**</span></span>

<span data-ttu-id="8300b-915">Este servicio extrae el tipo de solicitud HTTP en el búfer *http_type_string* y su longitud en el valor devuelto por el *nombre* de búfer de entrada, normalmente la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="8300b-915">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="8300b-916">Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo "texto/sin formato".</span><span class="sxs-lookup"><span data-stu-id="8300b-916">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="8300b-917">En caso contrario, compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias.</span><span class="sxs-lookup"><span data-stu-id="8300b-917">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="8300b-918">Los mapas MIME predeterminados del servidor HTTP de NetX Duo son:</span><span class="sxs-lookup"><span data-stu-id="8300b-918">The default MIME maps in NetX Duo HTTP Server are:</span></span>

- <span data-ttu-id="8300b-919">texto html/html</span><span class="sxs-lookup"><span data-stu-id="8300b-919">html text/html</span></span>
- <span data-ttu-id="8300b-920">texto htm/html</span><span class="sxs-lookup"><span data-stu-id="8300b-920">htm text/html</span></span>
- <span data-ttu-id="8300b-921">texto txt/plain</span><span class="sxs-lookup"><span data-stu-id="8300b-921">txt text/plain</span></span>
- <span data-ttu-id="8300b-922">imagen gif/gif</span><span class="sxs-lookup"><span data-stu-id="8300b-922">gif image/gif</span></span>
- <span data-ttu-id="8300b-923">imagen jpg/jpeg</span><span class="sxs-lookup"><span data-stu-id="8300b-923">jpg image/jpeg</span></span>
- <span data-ttu-id="8300b-924">imagen ico/x-icon</span><span class="sxs-lookup"><span data-stu-id="8300b-924">ico image/x-icon</span></span>

<span data-ttu-id="8300b-925">Si se proporciona, también buscará un conjunto definido por el usuario de asignaciones MIME adicionales.</span><span class="sxs-lookup"><span data-stu-id="8300b-925">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="8300b-926">Consulte *nx_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="8300b-926">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="8300b-927">Este servicio reemplaza a *nx_http_server_type_get()* .</span><span class="sxs-lookup"><span data-stu-id="8300b-927">This service replaces *nx_http_server_type_get().*</span></span> <span data-ttu-id="8300b-928">Esta versión proporciona información de longitud adicional.</span><span class="sxs-lookup"><span data-stu-id="8300b-928">This version supplies additional length information.</span></span>

<span data-ttu-id="8300b-929">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-929">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-930">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-930">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8300b-931">**name** Puntero al búfer para buscar.</span><span class="sxs-lookup"><span data-stu-id="8300b-931">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="8300b-932">**name_length** Longitud del búfer que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="8300b-932">**name_length** Length of buffer to search</span></span>
- <span data-ttu-id="8300b-933">**http_type_string** (Puntero a la cadena de tipo HTML extraída).</span><span class="sxs-lookup"><span data-stu-id="8300b-933">**http_type_string** (Pointer to extracted HTML type)</span></span>
- <span data-ttu-id="8300b-934">**http_type_string_max_size**</span><span class="sxs-lookup"><span data-stu-id="8300b-934">**http_type_string_max_size**</span></span>

<span data-ttu-id="8300b-935">Tamaño del búfer de *http_type_string*.</span><span class="sxs-lookup"><span data-stu-id="8300b-935">Size of the *http_type_string* buffer</span></span>

<span data-ttu-id="8300b-936">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-936">**Return Values**</span></span>

- <span data-ttu-id="8300b-937">**Longitud de la cadena en bytes** Un valor distinto de cero es correcto.</span><span class="sxs-lookup"><span data-stu-id="8300b-937">**Length of string in bytes** Non zero value is success</span></span><br /><span data-ttu-id="8300b-938">Cero indica un error.</span><span class="sxs-lookup"><span data-stu-id="8300b-938">Zero indicates error</span></span>

<span data-ttu-id="8300b-939">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-939">**Allowed From**</span></span>

<span data-ttu-id="8300b-940">Application</span><span class="sxs-lookup"><span data-stu-id="8300b-940">Application</span></span>

<span data-ttu-id="8300b-941">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-941">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

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
string_length = nx_http_server_type_get_extended(&my_server,
                my_server.nx_http_server_request_resource, resource_length,
                temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="8300b-942">Para un ejemplo más detallado, consulte la descripción de</span><span class="sxs-lookup"><span data-stu-id="8300b-942">For a more detailed example, see the description for</span></span>

<span data-ttu-id="8300b-943">*nx_http_server_callback_generate_response_header.*</span><span class="sxs-lookup"><span data-stu-id="8300b-943">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="8300b-944">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="8300b-944">nx_http_server_digest_authenticate_notify_set</span></span>

### <a name="set-digest-authenticate-callback-function"></a><span data-ttu-id="8300b-945">Establecimiento de la función de devolución de llamada de autenticación implícita</span><span class="sxs-lookup"><span data-stu-id="8300b-945">Set digest authenticate callback function</span></span>

<span data-ttu-id="8300b-946">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-946">**Prototype**</span></span>

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

<span data-ttu-id="8300b-947">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-947">**Description**</span></span>

<span data-ttu-id="8300b-948">Este servicio establece la devolución de llamada invocada cuando se realiza la autenticación implícita.</span><span class="sxs-lookup"><span data-stu-id="8300b-948">This service sets the callback invoked when digest authenticate is performed.</span></span>

<span data-ttu-id="8300b-949">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-949">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-950">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-950">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8300b-951">**digest_authenticate_callback** Puntero a la devolución de llamada de autenticación implícita.</span><span class="sxs-lookup"><span data-stu-id="8300b-951">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

<span data-ttu-id="8300b-952">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-952">**Return Values**</span></span>

- <span data-ttu-id="8300b-953">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-953">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8300b-954">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-954">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="8300b-955">NX_NOT_SUPPORTED (0x4B) Autenticación implícita no habilitada.</span><span class="sxs-lookup"><span data-stu-id="8300b-955">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

<span data-ttu-id="8300b-956">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-956">**Allowed From**</span></span>

<span data-ttu-id="8300b-957">Application</span><span class="sxs-lookup"><span data-stu-id="8300b-957">Application</span></span>

<span data-ttu-id="8300b-958">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-958">**Example**</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                 CHAR *realm_ptr, CHAR *password_ptr,
                                 CHAR *method,CHAR *authorization_uri,
                                 CHAR *authorization_nc,
                                 CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set the
digest authenticate callback: */

status = nx_http_server_digest_authenticate_notify_set (&my_server,
                                                       digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="8300b-959">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="8300b-959">nx_http_server_authentication_check_set</span></span>

### <a name="set-authentication-checking-callback-function"></a><span data-ttu-id="8300b-960">Establecimiento de la función de devolución de llamada de comprobación de autenticación</span><span class="sxs-lookup"><span data-stu-id="8300b-960">Set authentication checking callback function</span></span>

<span data-ttu-id="8300b-961">**Prototipo**</span><span class="sxs-lookup"><span data-stu-id="8300b-961">**Prototype**</span></span>

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

<span data-ttu-id="8300b-962">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="8300b-962">**Description**</span></span>

<span data-ttu-id="8300b-963">Este servicio establece la función de devolución de llamada de comprobación de autenticación.</span><span class="sxs-lookup"><span data-stu-id="8300b-963">This service sets the callback function of authentication checking.</span></span>

<span data-ttu-id="8300b-964">**Parámetros de entrada**</span><span class="sxs-lookup"><span data-stu-id="8300b-964">**Input Parameters**</span></span>

- <span data-ttu-id="8300b-965">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="8300b-965">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="8300b-966">**authentication_check_extended** Puntero a la comprobación de autenticación de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8300b-966">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

<span data-ttu-id="8300b-967">**Valores devueltos**</span><span class="sxs-lookup"><span data-stu-id="8300b-967">**Return Values**</span></span>

- <span data-ttu-id="8300b-968">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="8300b-968">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="8300b-969">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="8300b-969">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="8300b-970">**Permitido desde**</span><span class="sxs-lookup"><span data-stu-id="8300b-970">**Allowed From**</span></span>

<span data-ttu-id="8300b-971">Application</span><span class="sxs-lookup"><span data-stu-id="8300b-971">Application</span></span>

<span data-ttu-id="8300b-972">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8300b-972">**Example**</span></span>

```c
static UINT authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, UINT *name_length,
                                         CHAR **password, 
                                         UINT *password_length,
                                         CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */

    *name = "name";
    *password = "password";
    *realm = "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set 
the authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                        authentication_check_extended);
```