---
title: 'Capítulo 3: Descripción de los servicios HTTP'
description: Este capítulo contiene una descripción de todos los servicios Web HTTP de NetX (se enumeran a continuación) por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30168ad5a564b0f4c0a8c999046c5103385f4f90
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815377"
---
# <a name="chapter-3---description-of-http-services"></a><span data-ttu-id="168cc-103">Capítulo 3: Descripción de los servicios HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-103">Chapter 3 - Description of HTTP services</span></span>

<span data-ttu-id="168cc-104">Este capítulo contiene una descripción de todos los servicios Web HTTP de NetX (se enumeran a continuación) por orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="168cc-104">This chapter contains a description of all NetX Web HTTP services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-105">En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="168cc-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="http-and-https-client-api"></a><span data-ttu-id="168cc-106">API de cliente HTTP y HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-106">HTTP and HTTPS Client API</span></span>

## <a name="nx_web_http_client_connect"></a><span data-ttu-id="168cc-107">nx_web_http_client_connect</span><span class="sxs-lookup"><span data-stu-id="168cc-107">nx_web_http_client_connect</span></span>

<span data-ttu-id="168cc-108">Abre un socket de texto simple en un servidor HTTP para las solicitudes personalizadas</span><span class="sxs-lookup"><span data-stu-id="168cc-108">Open a plaintext socket to an HTTP server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-109">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-109">Prototype</span></span>

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-110">Description</span></span>

<span data-ttu-id="168cc-111">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-111">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-112">Este servicio abre un socket TCP de texto no cifrado en un servidor HTTP, pero no envía ninguna solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-112">This service opens a plaintext TCP socket to an HTTP server but does not send any requests.</span></span> <span data-ttu-id="168cc-113">Las solicitudes se crean con n *x_web_http_client_request_initialize()* y se envían mediante *nx_web_http_client_request_send()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-113">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="168cc-114">Se pueden agregar encabezados HTTP personalizados a la solicitud mediante *nx_web_http_client_request_header_add()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-114">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="168cc-115">El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-115">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="168cc-116">**Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.**</span><span class="sxs-lookup"><span data-stu-id="168cc-116">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-117">Los métodos nx_web_http_client_\*_start se proporcionan por comodidad (por ejemplo, *nx_web_http_client_get_start*()) y controlan la generación de solicitudes y la conexión de socket.</span><span class="sxs-lookup"><span data-stu-id="168cc-117">The nx_web_http_client_\*_start methods are provided for convenience (e.g. *nx_web_http_client_get_start*()) and handle the request generation and socket connection.</span></span> <span data-ttu-id="168cc-118">Puede usar esos servicios en lugar de *nx_web_http_client_connect()* y las rutinas relacionadas si no necesita encabezados HTTP personalizados en sus solicitudes.</span><span class="sxs-lookup"><span data-stu-id="168cc-118">You can use those services instead of *nx_web_http_client_connect()* and the related routines if you do not need custom HTTP headers in your requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-119">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-119">Input Parameters</span></span>

- <span data-ttu-id="168cc-120">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-120">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-121">**server_ip** Dirección IP del servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-121">**server_ip** IP address of remote HTTP server.</span></span>
- <span data-ttu-id="168cc-122">**server_port** Puerto en el servidor HTTP remoto (por ejemplo, 80 para HTTP).</span><span class="sxs-lookup"><span data-stu-id="168cc-122">**server_port** Port on remote HTTP server (e.g. 80 for HTTP).</span></span>
- <span data-ttu-id="168cc-123">**wait_option** Define cuánto tiempo esperará el servicio para las operaciones de red subyacentes.</span><span class="sxs-lookup"><span data-stu-id="168cc-123">**wait_option** Defines how long the service will wait for underlying network operations.</span></span> <span data-ttu-id="168cc-124">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-124">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-125">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-125">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-127">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-127">Return Values</span></span>

- <span data-ttu-id="168cc-128">**NX_SUCCESS** (0x00) conexión correcta del socket TCP.</span><span class="sxs-lookup"><span data-stu-id="168cc-128">**NX_SUCCESS** (0x00) Successful connection of TCP socket.</span></span>
- <span data-ttu-id="168cc-129">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-129">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-130">NX_WEB_HTTP_NOT_READY (0x3000A) Ya hay otra solicitud en curso.</span><span class="sxs-lookup"><span data-stu-id="168cc-130">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-131">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-131">Allowed From</span></span>

<span data-ttu-id="168cc-132">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-133">Example</span></span>

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a><span data-ttu-id="168cc-134">nx_web_http_client_create</span><span class="sxs-lookup"><span data-stu-id="168cc-134">nx_web_http_client_create</span></span>

<span data-ttu-id="168cc-135">Crea una instancia de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-135">Create an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-136">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-136">Prototype</span></span>

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="168cc-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-137">Description</span></span>

<span data-ttu-id="168cc-138">Este servicio crea una instancia de cliente HTTP en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="168cc-138">This service creates an HTTP Client instance on the specified IP instance.</span></span> <span data-ttu-id="168cc-139">La instancia de cliente se puede usar para HTTP o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="168cc-139">The Client instance can be used for either HTTP or HTTPS.</span></span> <span data-ttu-id="168cc-140">Consulte los servicios *nx_web_http_client_connect()* y *nx_web_http_client_secure_connect()* para obtener más información sobre cómo iniciar una instancia HTTP o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="168cc-140">See the services *nx_web_http_client_connect()* and *nx_web_http_client_secure_connect()* for more information on starting an HTTP or HTTPS instance.</span></span> <span data-ttu-id="168cc-141">Consulte también la API de \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** para invocaciones simples de los métodos GET, PUT y POST.</span><span class="sxs-lookup"><span data-stu-id="168cc-141">Also refer to the API for \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** for simple invocations of GET, PUT, and POST methods.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-142">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-142">Input Parameters</span></span>

- <span data-ttu-id="168cc-143">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-143">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-144">**client_name** Nombre de la instancia de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-144">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="168cc-145">**ip_ptr** Puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="168cc-145">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="168cc-146">**pool_ptr** Puntero al grupo de paquetes predeterminado.</span><span class="sxs-lookup"><span data-stu-id="168cc-146">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="168cc-147">Tenga en cuenta que los paquetes de este grupo deben tener una carga útil lo suficientemente grande como para controlar el encabezado de respuesta completo.</span><span class="sxs-lookup"><span data-stu-id="168cc-147">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="168cc-148">Esto lo define *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* en *nx_web_http_client.h*.</span><span class="sxs-lookup"><span data-stu-id="168cc-148">This is defined by *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* in *nx_web_http_client.h*.</span></span>
- <span data-ttu-id="168cc-149">**window_size** Tamaño de la ventana de recepción del socket TCP del cliente.</span><span class="sxs-lookup"><span data-stu-id="168cc-149">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-150">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-150">Return Values</span></span>

- <span data-ttu-id="168cc-151">**NX_SUCCESS** (0x00) Cliente HTTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-151">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="168cc-152">NX_PTR_ERROR (0x16) Puntero HTTP, ip_ptr o de grupo de paquetes no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-152">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="168cc-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Tamaño de carga no válido en el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="168cc-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-154">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-154">Allowed From</span></span>

<span data-ttu-id="168cc-155">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-155">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-156">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-156">Example</span></span>

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a><span data-ttu-id="168cc-157">nx_web_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="168cc-157">nx_web_http_client_delete</span></span>

<span data-ttu-id="168cc-158">Elimina una instancia de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-158">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-159">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-159">Prototype</span></span>

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="168cc-160">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-160">Description</span></span>

<span data-ttu-id="168cc-161">Este servicio elimina una instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-161">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-162">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-162">Input Parameters</span></span>

- <span data-ttu-id="168cc-163">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-163">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-164">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-164">Return Values</span></span>

- <span data-ttu-id="168cc-165">**NX_SUCCESS** (0x00) Cliente HTTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-165">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="168cc-166">NX_PTR_ERROR (0x16) El puntero HTTP no es válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-166">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="168cc-167">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-168">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-168">Allowed From</span></span>

<span data-ttu-id="168cc-169">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-170">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-170">Example</span></span>

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a><span data-ttu-id="168cc-171">nx_web_http_client_delete_start</span><span class="sxs-lookup"><span data-stu-id="168cc-171">nx_web_http_client_delete_start</span></span>

<span data-ttu-id="168cc-172">Inicia una solicitud DELETE de HTTP de texto no cifrado</span><span class="sxs-lookup"><span data-stu-id="168cc-172">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-173">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-173">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-174">Description</span></span>

<span data-ttu-id="168cc-175">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-175">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-176">Este servicio intenta enviar una solicitud DELETE para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-176">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-177">Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-177">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="168cc-178">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-178">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-179">Esta API está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-179">This API is deprecated.</span></span> <span data-ttu-id="168cc-180">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_delete_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-180">Developers are encouraged to use *nx_web_http_client_delete_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-181">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-181">Input Parameters</span></span>

- <span data-ttu-id="168cc-182">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-182">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-183">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-183">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-184">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-184">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-185">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-185">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-186">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-186">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-187">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-187">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-188">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-188">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-189">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-189">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-190">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-190">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-191">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-191">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-192">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-192">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-193">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-193">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-195">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-195">Return Values</span></span>

- <span data-ttu-id="168cc-196">**NX_SUCCESS** (0x00) Mensaje de solicitud DELETE de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-196">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="168cc-197">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-197">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-199">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-201">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-201">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-202">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-202">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-203">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-203">Allowed From</span></span>

<span data-ttu-id="168cc-204">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-204">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-205">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-205">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a><span data-ttu-id="168cc-206">nx_web_http_client_delete_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-206">nx_web_http_client_delete_start_extended</span></span>

<span data-ttu-id="168cc-207">Inicia una solicitud DELETE de HTTP de texto no cifrado</span><span class="sxs-lookup"><span data-stu-id="168cc-207">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-208">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-208">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-209">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-209">Description</span></span>

<span data-ttu-id="168cc-210">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-210">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-211">Este servicio intenta enviar una solicitud DELETE para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-211">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-212">Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-212">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="168cc-213">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-213">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-214">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-214">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-215">Este servicio reemplaza a *nx_web_http_client_delete_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-215">This service replaces *nx_web_http_client_delete_start* ().</span></span> <span data-ttu-id="168cc-216">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-216">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-217">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-217">Input Parameters</span></span>

- <span data-ttu-id="168cc-218">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-218">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-219">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-219">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-220">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-220">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-221">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-221">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-222">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-222">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-223">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-223">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-224">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-224">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-225">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-225">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-226">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-226">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-227">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-227">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-228">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-228">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-229">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-229">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-230">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-230">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-231">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-231">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-232">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-232">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-233">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-233">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-235">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-235">Return Values</span></span>

- <span data-ttu-id="168cc-236">**NX_SUCCESS** (0x00) Mensaje de solicitud DELETE de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-236">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="168cc-237">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-237">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-239">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-241">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-241">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-242">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-242">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-243">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-243">Allowed From</span></span>

<span data-ttu-id="168cc-244">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-244">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-245">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-245">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a><span data-ttu-id="168cc-246">nx_web_http_client_delete_secure_start</span><span class="sxs-lookup"><span data-stu-id="168cc-246">nx_web_http_client_delete_secure_start</span></span>

<span data-ttu-id="168cc-247">Inicia una solicitud DELETE de HTTPS cifrada</span><span class="sxs-lookup"><span data-stu-id="168cc-247">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-248">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-248">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-249">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-249">Description</span></span>

<span data-ttu-id="168cc-250">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-250">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-251">Este servicio intenta enviar una solicitud DELETE para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-251">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-252">Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-252">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="168cc-253">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-253">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-254">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-254">This service is deprecated.</span></span> <span data-ttu-id="168cc-255">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_delete_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-255">Developers are encouraged to use *nx_web_http_client_delete_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-256">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-256">Input Parameters</span></span>

- <span data-ttu-id="168cc-257">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-257">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-258">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-258">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-259">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-259">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-260">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-260">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="168cc-261">El recurso debe terminar en NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-261">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="168cc-262">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-262">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-263">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-263">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-264">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-264">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-265">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-265">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-266">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-266">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-267">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-267">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-268">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-268">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-269">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-269">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-270">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-270">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-271">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-271">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-273">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-273">Return Values</span></span>

- <span data-ttu-id="168cc-274">**NX_SUCCESS** (0x00) Mensaje de solicitud DELETE de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-274">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="168cc-275">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-275">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-277">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-279">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-279">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-280">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-280">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-281">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-281">Allowed From</span></span>

<span data-ttu-id="168cc-282">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-283">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-283">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a><span data-ttu-id="168cc-284">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-284">nx_web_http_client_delete_secure_start_extended</span></span>

<span data-ttu-id="168cc-285">Inicia una solicitud DELETE de HTTPS cifrada</span><span class="sxs-lookup"><span data-stu-id="168cc-285">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-286">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-286">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-287">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-287">Description</span></span>

<span data-ttu-id="168cc-288">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-288">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-289">Este servicio intenta enviar una solicitud DELETE para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-289">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-290">Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-290">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="168cc-291">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-291">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-292">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-292">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-293">Este servicio reemplaza a *nx_web_http_client_delete_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-293">This service replaces *nx_web_http_client_delete_secure_start*().</span></span> <span data-ttu-id="168cc-294">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-294">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-295">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-295">Input Parameters</span></span>

- <span data-ttu-id="168cc-296">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-296">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-297">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-297">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-298">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-298">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-299">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-299">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="168cc-300">El recurso debe terminar en NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-300">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="168cc-301">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-301">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-302">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-302">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-303">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-303">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-304">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-304">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-305">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-305">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-306">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-306">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-307">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-307">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-308">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-308">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-309">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-309">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-310">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-310">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-311">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-311">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-312">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-312">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-313">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-313">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-314">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-314">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-316">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-316">Return Values</span></span>

- <span data-ttu-id="168cc-317">**NX_SUCCESS** (0x00) Mensaje de solicitud DELETE de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-317">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="168cc-318">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-318">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-320">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-322">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-322">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-323">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-323">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="168cc-324">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-324">Allowed From</span></span>

<span data-ttu-id="168cc-325">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-325">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-326">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-326">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a><span data-ttu-id="168cc-327">nx_web_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="168cc-327">nx_web_http_client_get_start</span></span>

<span data-ttu-id="168cc-328">Inicia una solicitud GET de HTTP de texto no cifrado</span><span class="sxs-lookup"><span data-stu-id="168cc-328">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-329">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-329">Prototype</span></span>

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-330">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-330">Description</span></span>

<span data-ttu-id="168cc-331">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-331">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-332">Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-332">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-333">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_web_http_client_response_body_get()* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-333">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="168cc-334">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-334">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-335">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-335">This service is deprecated.</span></span> <span data-ttu-id="168cc-336">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_delete_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-336">Developers are encouraged to use *nx_web_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-337">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-337">Input Parameters</span></span>

- <span data-ttu-id="168cc-338">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-338">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-339">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-339">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-340">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-340">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-341">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-341">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-342">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-342">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-343">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-343">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-344">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-344">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-345">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-345">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-346">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-346">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-347">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-347">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-348">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-348">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-349">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-349">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-351">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-351">Return Values</span></span>

- <span data-ttu-id="168cc-352">**NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-352">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="168cc-353">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-353">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-355">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-357">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-357">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-358">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-358">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-359">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-359">Allowed From</span></span>

<span data-ttu-id="168cc-360">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-361">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-361">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a><span data-ttu-id="168cc-362">nx_web_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-362">nx_web_http_client_get_start_extended</span></span>

<span data-ttu-id="168cc-363">Inicia una solicitud GET de HTTP de texto no cifrado</span><span class="sxs-lookup"><span data-stu-id="168cc-363">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-364">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-364">Prototype</span></span>

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-365">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-365">Description</span></span>

<span data-ttu-id="168cc-366">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-366">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-367">Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-367">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-368">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_web_http_client_response_body_get()* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-368">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="168cc-369">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-369">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-370">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-370">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-371">Este servicio reemplaza a *nx_web_http_client_delete_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-371">This service replaces *nx_web_http_client_get_start*().</span></span> <span data-ttu-id="168cc-372">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-372">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-373">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-373">Input Parameters</span></span>

- <span data-ttu-id="168cc-374">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-374">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-375">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-375">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-376">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-376">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-377">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-377">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-378">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-378">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-379">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-379">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-380">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-380">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-381">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-381">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-382">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-382">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-383">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-383">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-384">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-384">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-385">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-385">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-386">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-386">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-387">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-387">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-388">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-388">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-389">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-389">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-391">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-391">Return Values</span></span>

- <span data-ttu-id="168cc-392">**NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-392">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="168cc-393">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-393">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-395">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-397">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-397">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-398">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-398">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-399">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-399">Allowed From</span></span>

<span data-ttu-id="168cc-400">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-401">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-401">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a><span data-ttu-id="168cc-402">nx_web_http_client_get_secure_start</span><span class="sxs-lookup"><span data-stu-id="168cc-402">nx_web_http_client_get_secure_start</span></span>

<span data-ttu-id="168cc-403">Inicia una solicitud GET cifrada de HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-403">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-404">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-404">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-405">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-405">Description</span></span>

<span data-ttu-id="168cc-406">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-406">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-407">Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-407">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-408">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_web_http_client_response_body_get()* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-408">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="168cc-409">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-409">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-410">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-410">This service is deprecated.</span></span> <span data-ttu-id="168cc-411">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_get_secure_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-411">Developers are encouraged to use *nx_web_http_client_get_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-412">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-412">Input Parameters</span></span>

- <span data-ttu-id="168cc-413">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-413">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-414">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-414">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-415">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-415">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-416">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-416">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-417">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-417">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-418">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-418">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-419">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-419">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-420">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-420">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-421">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-421">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-422">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-422">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-423">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-423">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-424">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-424">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-425">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-425">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-426">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-426">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-428">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-428">Return Values</span></span>

- <span data-ttu-id="168cc-429">**NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-429">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="168cc-430">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-430">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-432">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-434">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-434">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-435">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-435">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-436">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-436">Allowed From</span></span>

<span data-ttu-id="168cc-437">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-438">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-438">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a><span data-ttu-id="168cc-439">nx_web_http_client_get_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-439">nx_web_http_client_get_secure_start_extended</span></span>

<span data-ttu-id="168cc-440">Inicia una solicitud GET cifrada de HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-440">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-441">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-441">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-442">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-442">Description</span></span>

<span data-ttu-id="168cc-443">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-443">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-444">Este servicio intenta enviar una solicitud GET para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-444">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-445">Si esta rutina devuelve NX_SUCCESS, la aplicación puede realizar varias llamadas a *nx_web_http_client_response_body_get()* para recuperar los paquetes de datos correspondientes al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-445">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="168cc-446">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-446">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-447">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-447">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-448">Este servicio reemplaza a *nx_web_http_client_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-448">This service replaces *nx_web_http_client_secure_start*().</span></span> <span data-ttu-id="168cc-449">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-449">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-450">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-450">Input Parameters</span></span>

- <span data-ttu-id="168cc-451">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-451">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-452">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-452">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-453">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-453">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-454">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-454">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-455">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-455">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-456">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-456">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-457">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-457">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-458">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-458">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-459">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-459">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-460">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-460">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-461">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-461">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-462">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-462">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-463">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-463">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-464">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-464">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-465">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-465">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-466">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-466">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-467">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-467">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-468">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-468">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-470">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-470">Return Values</span></span>

- <span data-ttu-id="168cc-471">**NX_SUCCESS** (0x00) Mensaje de inicio de solicitud GET de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-471">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="168cc-472">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-472">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-474">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-476">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-477">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-477">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-478">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-478">Allowed From</span></span>

<span data-ttu-id="168cc-479">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-480">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-480">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a><span data-ttu-id="168cc-481">nx_web_http_client_head_start</span><span class="sxs-lookup"><span data-stu-id="168cc-481">nx_web_http_client_head_start</span></span>

<span data-ttu-id="168cc-482">Inicia una solicitud HEAD de HTTP de texto no cifrado</span><span class="sxs-lookup"><span data-stu-id="168cc-482">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-483">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-483">Prototype</span></span>

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-484">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-484">Description</span></span>

<span data-ttu-id="168cc-485">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-485">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-486">Este servicio intenta recuperar los metadatos HEAD para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-486">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-487">Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta.</span><span class="sxs-lookup"><span data-stu-id="168cc-487">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="168cc-488">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-488">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-489">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-489">This service is deprecated.</span></span> <span data-ttu-id="168cc-490">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_head_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-490">Developers are encouraged to use *nx_web_http_client_head_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-491">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-491">Input Parameters</span></span>

- <span data-ttu-id="168cc-492">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-492">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-493">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-493">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-494">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-494">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-495">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-495">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-496">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-496">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-497">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-497">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-498">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-498">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-499">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-499">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-500">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-500">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-501">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-501">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-502">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-502">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-503">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-503">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-505">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-505">Return Values</span></span>

- <span data-ttu-id="168cc-506">**NX_SUCCESS** (0x00) Mensaje de solicitud HEAD de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-506">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="168cc-507">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-507">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-509">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-511">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-511">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-512">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-513">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-513">Allowed From</span></span>

<span data-ttu-id="168cc-514">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-515">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-515">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a><span data-ttu-id="168cc-516">nx_web_http_client_head_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-516">nx_web_http_client_head_start_extended</span></span>

<span data-ttu-id="168cc-517">Inicia una solicitud HEAD de HTTP de texto no cifrado</span><span class="sxs-lookup"><span data-stu-id="168cc-517">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-518">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-518">Prototype</span></span>

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-519">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-519">Description</span></span>

<span data-ttu-id="168cc-520">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-520">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-521">Este servicio intenta recuperar los metadatos HEAD para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-521">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-522">Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta.</span><span class="sxs-lookup"><span data-stu-id="168cc-522">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="168cc-523">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-523">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-524">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-524">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-525">Este servicio reemplaza a *nx_web_http_client_head_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-525">This service replaces *nx_web_http_client_head_start*().</span></span> <span data-ttu-id="168cc-526">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-526">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-527">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-527">Input Parameters</span></span>

- <span data-ttu-id="168cc-528">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-528">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-529">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-529">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-530">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-530">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-531">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-531">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-532">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-532">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-533">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-533">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-534">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-534">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-535">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-535">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-536">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-536">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-537">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-537">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-538">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-538">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-539">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-539">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-540">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-540">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-541">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-541">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-542">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-542">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-543">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-543">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-545">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-545">Return Values</span></span>

- <span data-ttu-id="168cc-546">**NX_SUCCESS** (0x00) Mensaje de solicitud HEAD de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-546">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="168cc-547">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-547">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-549">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-551">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-551">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-552">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-552">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-553">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-553">Allowed From</span></span>

<span data-ttu-id="168cc-554">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-555">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-555">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a><span data-ttu-id="168cc-556">nx_web_http_client_head_secure_start</span><span class="sxs-lookup"><span data-stu-id="168cc-556">nx_web_http_client_head_secure_start</span></span>

<span data-ttu-id="168cc-557">Inicia una solicitud HEAD cifrada de HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-557">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-558">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-558">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-559">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-559">Description</span></span>

<span data-ttu-id="168cc-560">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-560">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-561">Este servicio intenta recuperar los metadatos HEAD para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-561">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-562">Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor correspondiente al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-562">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="168cc-563">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-563">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-564">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-564">This service is deprecated.</span></span> <span data-ttu-id="168cc-565">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_head_secure_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-565">Developers are encouraged to use *nx_web_http_client_head_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-566">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-566">Input Parameters</span></span>

- <span data-ttu-id="168cc-567">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-567">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-568">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-568">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-569">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-569">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-570">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-570">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-571">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-571">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-572">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-572">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-573">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-573">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-574">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-574">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-575">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-575">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-576">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-576">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-577">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-577">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-578">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-578">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-579">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-579">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-580">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-580">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-582">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-582">Return Values</span></span>

- <span data-ttu-id="168cc-583">**NX_SUCCESS** (0x00) Mensaje de solicitud HEAD de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-583">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="168cc-584">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-584">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-586">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-588">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-589">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-589">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-590">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-590">Allowed From</span></span>

<span data-ttu-id="168cc-591">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-591">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-592">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-592">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a><span data-ttu-id="168cc-593">nx_web_http_client_head_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-593">nx_web_http_client_head_secure_start_extended</span></span>

<span data-ttu-id="168cc-594">Inicia una solicitud HEAD cifrada de HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-594">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-595">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-595">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-596">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-596">Description</span></span>

<span data-ttu-id="168cc-597">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-597">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-598">Este servicio intenta recuperar los metadatos HEAD para el recurso especificado por el puntero “resource” en la instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-598">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="168cc-599">Si esta rutina devuelve NX_SUCCESS, la aplicación puede llamar a *nx_web_http_client_response_body_get()* para recuperar la respuesta del servidor correspondiente al contenido del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-599">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="168cc-600">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes GET de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-600">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="168cc-601">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-601">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-602">Este servicio reemplaza a *nx_web_http_client_head_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-602">This service replaces *nx_web_http_client_head_secure_start*().</span></span> <span data-ttu-id="168cc-603">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-603">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-604">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-604">Input Parameters</span></span>

- <span data-ttu-id="168cc-605">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-605">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-606">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-606">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-607">**server_port** Puerto en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-607">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-608">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-608">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-609">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-609">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-610">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-610">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-611">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-611">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-612">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-612">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-613">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-613">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-614">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-614">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-615">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-615">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-616">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-616">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-617">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-617">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-618">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-618">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-619">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-619">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-620">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-620">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-621">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-621">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-622">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-622">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-624">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-624">Return Values</span></span>

- <span data-ttu-id="168cc-625">**NX_SUCCESS** (0x00) Mensaje de solicitud HEAD de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-625">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="168cc-626">**NX_WEB_HTTP_ERROR** (0x30000) ERROR de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-626">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="168cc-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-628">**NX_WEB_HTTP_FAILED** (0x30002) Error de cliente HTTP al comunicarse con el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="168cc-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="168cc-630">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-630">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-631">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-631">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-632">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-632">Allowed From</span></span>

<span data-ttu-id="168cc-633">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-633">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-634">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-634">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a><span data-ttu-id="168cc-635">nx_web_http_client_request_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="168cc-635">nx_web_http_client_request_packet_allocate</span></span>

<span data-ttu-id="168cc-636">Asigna un paquete HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="168cc-636">Allocate a HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-637">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-637">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-638">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-638">Description</span></span>

<span data-ttu-id="168cc-639">Este servicio intenta asignar un paquete para HTTP(S) de cliente.</span><span class="sxs-lookup"><span data-stu-id="168cc-639">This service attempts to allocates a packet for Client HTTP(S).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-640">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-640">Input Parameters</span></span>

- <span data-ttu-id="168cc-641">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-641">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-642">**packet_ptr** Puntero al paquete asignado.</span><span class="sxs-lookup"><span data-stu-id="168cc-642">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="168cc-643">**wait_option** Define el tiempo de espera en tics si no hay paquetes disponibles en el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="168cc-643">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="168cc-644">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-644">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-645">**NX_NO_WAIT** (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="168cc-645">**NX_NO_WAIT** (0x00000000)</span></span>
  - <span data-ttu-id="168cc-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="168cc-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="168cc-647">**TIMEOUT_IN_TICKS** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="168cc-647">**timeout in ticks** (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-648">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-648">Return Values</span></span>

- <span data-ttu-id="168cc-649">**NX_SUCCESS** (0x00) Asignación correcta de paquetes.</span><span class="sxs-lookup"><span data-stu-id="168cc-649">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="168cc-650">**NX_NO_PACKET** (0X01) No hay ningún paquete disponible.</span><span class="sxs-lookup"><span data-stu-id="168cc-650">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="168cc-651">**NX_WAIT_ABORTED** (0x1A) Una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="168cc-651">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="168cc-652">**NX_INVALID_PARAMETERS** (0x4D) El tamaño de paquete no admite el protocolo.</span><span class="sxs-lookup"><span data-stu-id="168cc-652">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="168cc-653">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-653">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-654">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-654">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-655">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-655">Allowed From</span></span>

<span data-ttu-id="168cc-656">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-657">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-657">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a><span data-ttu-id="168cc-658">nx_web_http_client_post_start</span><span class="sxs-lookup"><span data-stu-id="168cc-658">nx_web_http_client_post_start</span></span>

<span data-ttu-id="168cc-659">Envía una solicitud POST de HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-659">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-660">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-660">Prototype</span></span>

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-661">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-661">Description</span></span>

<span data-ttu-id="168cc-662">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-662">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-663">Este servicio intenta enviar una solicitud POST con el recurso especificado al servidor HTTP en la dirección IP y el puerto proporcionados.</span><span class="sxs-lookup"><span data-stu-id="168cc-663">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="168cc-664">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet* para enviar el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-664">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="168cc-665">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-665">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="168cc-666">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-666">This service is deprecated.</span></span> <span data-ttu-id="168cc-667">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_post_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-667">Developers are encouraged to use *nx_web_http_client_post_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-668">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-668">Input Parameters</span></span>

- <span data-ttu-id="168cc-669">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-669">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-670">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-670">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-671">**server_port** Puerto TCP en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-671">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-672">**resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-672">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="168cc-673">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-673">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-674">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-674">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-675">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-675">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-676">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-676">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-677">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-677">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-678">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="168cc-678">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="168cc-679">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="168cc-679">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="168cc-680">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-680">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-681">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-681">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-682">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-682">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-684">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-684">Return Values</span></span>

- <span data-ttu-id="168cc-685">**NX_SUCCESS** (0x00) Mensaje de solicitud POST enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-685">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="168cc-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.</span><span class="sxs-lookup"><span data-stu-id="168cc-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="168cc-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-688">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-688">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-689">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-689">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="168cc-690">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-690">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-691">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-691">Allowed From</span></span>

<span data-ttu-id="168cc-692">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-693">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-693">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a><span data-ttu-id="168cc-694">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-694">nx_web_http_client_post_start_extended</span></span>

<span data-ttu-id="168cc-695">Envía una solicitud POST de HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-695">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-696">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-696">Prototype</span></span>

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-697">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-697">Description</span></span>

<span data-ttu-id="168cc-698">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-698">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-699">Este servicio intenta enviar una solicitud POST con el recurso especificado al servidor HTTP en la dirección IP y el puerto proporcionados.</span><span class="sxs-lookup"><span data-stu-id="168cc-699">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="168cc-700">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet* para enviar el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-700">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="168cc-701">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-701">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="168cc-702">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-702">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-703">Este servicio reemplaza a *nx_web_http_client_post_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-703">This service replaces *nx_web_http_client_post_start* ().</span></span> <span data-ttu-id="168cc-704">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-704">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-705">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-705">Input Parameters</span></span>

- <span data-ttu-id="168cc-706">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-706">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-707">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-707">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-708">**server_port** Puerto TCP en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-708">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-709">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-709">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-710">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-710">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-711">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-711">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-712">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-712">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-713">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-713">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-714">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-714">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-715">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-715">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-716">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-716">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-717">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-717">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-718">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-718">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-719">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="168cc-719">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="168cc-720">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="168cc-720">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="168cc-721">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-721">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-722">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-722">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-723">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-723">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-725">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-725">Return Values</span></span>

- <span data-ttu-id="168cc-726">**NX_SUCCESS** (0x00) Mensaje de solicitud POST enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-726">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="168cc-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.</span><span class="sxs-lookup"><span data-stu-id="168cc-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="168cc-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-729">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-729">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-730">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-730">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="168cc-731">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-732">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-732">Allowed From</span></span>

<span data-ttu-id="168cc-733">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-734">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-734">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a><span data-ttu-id="168cc-735">nx_web_http_client_post_secure_start</span><span class="sxs-lookup"><span data-stu-id="168cc-735">nx_web_http_client_post_secure_start</span></span>

<span data-ttu-id="168cc-736">Inicia una solicitud POST cifrada de HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-736">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-737">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-737">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-738">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-738">Description</span></span>

<span data-ttu-id="168cc-739">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-739">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-740">Este servicio intenta enviar una solicitud POST con el recurso especificado al servidor HTTPS en la dirección IP y el puerto proporcionados.</span><span class="sxs-lookup"><span data-stu-id="168cc-740">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="168cc-741">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-741">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="168cc-742">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-742">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="168cc-743">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-743">This service is deprecated.</span></span> <span data-ttu-id="168cc-744">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_post_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-744">Developers are encouraged to use *nx_web_http_client_post_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-745">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-745">Input Parameters</span></span>

- <span data-ttu-id="168cc-746">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-746">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-747">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-747">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-748">**server_port** Puerto TCP en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-748">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-749">**resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-749">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="168cc-750">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-750">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-751">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-751">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-752">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-752">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-753">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-753">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-754">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-754">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-755">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="168cc-755">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="168cc-756">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="168cc-756">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="168cc-757">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-757">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-758">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-758">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-759">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-759">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-760">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-760">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-761">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-761">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-763">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-763">Return Values</span></span>

- <span data-ttu-id="168cc-764">**NX_SUCCESS** (0x00) Mensaje de solicitud POST enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-764">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="168cc-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.</span><span class="sxs-lookup"><span data-stu-id="168cc-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="168cc-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-767">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-767">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-768">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-768">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="168cc-769">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-769">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-770">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-770">Allowed From</span></span>

<span data-ttu-id="168cc-771">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-771">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-772">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-772">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a><span data-ttu-id="168cc-773">nx_web_http_client_post_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-773">nx_web_http_client_post_secure_start_extended</span></span>

<span data-ttu-id="168cc-774">Inicia una solicitud POST cifrada de HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-774">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-775">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-775">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-776">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-776">Description</span></span>

<span data-ttu-id="168cc-777">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-777">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-778">Este servicio intenta enviar una solicitud POST con el recurso especificado al servidor HTTPS en la dirección IP y el puerto proporcionados.</span><span class="sxs-lookup"><span data-stu-id="168cc-778">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="168cc-779">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-779">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="168cc-780">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-780">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="168cc-781">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-781">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-782">Este servicio reemplaza a *nx_web_http_client_post_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-782">This service replaces *nx_web_http_client_post_secure_start* ().</span></span> <span data-ttu-id="168cc-783">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-783">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-784">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-784">Input Parameters</span></span>

- <span data-ttu-id="168cc-785">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-785">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-786">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-786">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-787">**server_port** Puerto TCP en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-787">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-788">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-788">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-789">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-789">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-790">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-790">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-791">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-791">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-792">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-792">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-793">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-793">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-794">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-794">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-795">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-795">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-796">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-796">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-797">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-797">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-798">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="168cc-798">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="168cc-799">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="168cc-799">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="168cc-800">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-800">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-801">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-801">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-802">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-802">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-803">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-803">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-804">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-804">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-806">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-806">Return Values</span></span>

- <span data-ttu-id="168cc-807">**NX_SUCCESS** (0x00) Mensaje de solicitud POST enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-807">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="168cc-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.</span><span class="sxs-lookup"><span data-stu-id="168cc-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="168cc-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-810">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-810">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-811">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-811">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="168cc-812">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-812">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-813">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-813">Allowed From</span></span>

<span data-ttu-id="168cc-814">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-814">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-815">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-815">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a><span data-ttu-id="168cc-816">nx_web_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="168cc-816">nx_web_http_client_put_start</span></span>

<span data-ttu-id="168cc-817">Inicia una solicitud PUT de HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-817">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-818">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-818">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-819">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-819">Description</span></span>

<span data-ttu-id="168cc-820">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-820">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-821">Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP y el puerto proporcionados.</span><span class="sxs-lookup"><span data-stu-id="168cc-821">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="168cc-822">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-822">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="168cc-823">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-823">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="168cc-824">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-824">This service is deprecated.</span></span> <span data-ttu-id="168cc-825">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_put_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-825">Developers are encouraged to use *nx_web_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-826">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-826">Input Parameters</span></span>

- <span data-ttu-id="168cc-827">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-827">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-828">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-828">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-829">**server_port** Puerto TCP en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-829">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-830">**resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-830">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="168cc-831">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-831">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-832">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-832">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-833">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-833">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-834">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-834">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-835">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-835">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-836">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="168cc-836">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="168cc-837">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="168cc-837">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="168cc-838">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-838">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-839">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-839">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-840">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-840">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-842">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-842">Return Values</span></span>

- <span data-ttu-id="168cc-843">**NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-843">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="168cc-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.</span><span class="sxs-lookup"><span data-stu-id="168cc-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="168cc-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-846">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-846">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-847">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-847">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="168cc-848">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-848">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-849">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-849">Allowed From</span></span>

<span data-ttu-id="168cc-850">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-850">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-851">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-851">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a><span data-ttu-id="168cc-852">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-852">nx_web_http_client_put_start_extended</span></span>

<span data-ttu-id="168cc-853">Inicia una solicitud PUT de HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-853">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-854">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-854">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-855">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-855">Description</span></span>

<span data-ttu-id="168cc-856">Este método es para HTTP de **texto no cifrado**.</span><span class="sxs-lookup"><span data-stu-id="168cc-856">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="168cc-857">Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTP en la dirección IP y el puerto proporcionados.</span><span class="sxs-lookup"><span data-stu-id="168cc-857">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="168cc-858">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-858">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="168cc-859">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-859">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="168cc-860">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-860">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-861">Este servicio reemplaza a *nx_web_http_client_post_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-861">This service replaces *nx_web_http_client_put_start* ().</span></span> <span data-ttu-id="168cc-862">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-862">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-863">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-863">Input Parameters</span></span>

- <span data-ttu-id="168cc-864">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-864">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-865">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-865">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-866">**server_port** Puerto TCP en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-866">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-867">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-867">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-868">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-868">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-869">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-869">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-870">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-870">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-871">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-871">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-872">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-872">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-873">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-873">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-874">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-874">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-875">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-875">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-876">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-876">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-877">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="168cc-877">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="168cc-878">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="168cc-878">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="168cc-879">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-879">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-880">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-880">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-881">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-881">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-883">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-883">Return Values</span></span>

- <span data-ttu-id="168cc-884">**NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-884">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="168cc-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.</span><span class="sxs-lookup"><span data-stu-id="168cc-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="168cc-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-887">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-887">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-888">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-888">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="168cc-889">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-889">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-890">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-890">Allowed From</span></span>

<span data-ttu-id="168cc-891">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-892">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-892">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a><span data-ttu-id="168cc-893">nx_web_http_client_put_secure_start</span><span class="sxs-lookup"><span data-stu-id="168cc-893">nx_web_http_client_put_secure_start</span></span>

<span data-ttu-id="168cc-894">Inicia una solicitud PUT cifrada de HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-894">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-895">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-895">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-896">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-896">Description</span></span>

<span data-ttu-id="168cc-897">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-897">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-898">Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTPS en la dirección IP y el puerto proporcionados.</span><span class="sxs-lookup"><span data-stu-id="168cc-898">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="168cc-899">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-899">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="168cc-900">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-900">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="168cc-901">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-901">This service is deprecated.</span></span> <span data-ttu-id="168cc-902">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_put_secure_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-902">Developers are encouraged to use *nx_web_http_client_put_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-903">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-903">Input Parameters</span></span>

- <span data-ttu-id="168cc-904">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-904">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-905">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-905">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-906">**server_port** Puerto TCP en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-906">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-907">**resource** Puntero a la cadena de dirección URL para el recurso que se va a enviar al servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-907">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="168cc-908">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-908">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-909">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-909">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-910">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-910">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-911">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-911">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-912">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-912">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-913">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="168cc-913">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="168cc-914">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="168cc-914">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="168cc-915">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-915">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-916">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-916">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-917">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-917">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-918">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-919">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-919">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-921">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-921">Return Values</span></span>

- <span data-ttu-id="168cc-922">**NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-922">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="168cc-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.</span><span class="sxs-lookup"><span data-stu-id="168cc-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="168cc-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-925">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-925">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-926">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-926">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="168cc-927">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-927">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-928">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-928">Allowed From</span></span>

<span data-ttu-id="168cc-929">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-929">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-930">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-930">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a><span data-ttu-id="168cc-931">nx_web_http_client_put_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-931">nx_web_http_client_put_secure_start_extended</span></span>

<span data-ttu-id="168cc-932">Inicia una solicitud PUT cifrada de HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-932">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-933">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-933">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-934">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-934">Description</span></span>

<span data-ttu-id="168cc-935">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-935">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-936">Este servicio intenta enviar una solicitud PUT con el recurso especificado al servidor HTTPS en la dirección IP y el puerto proporcionados.</span><span class="sxs-lookup"><span data-stu-id="168cc-936">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="168cc-937">Si esta rutina se realiza correctamente, el código de aplicación debe realizar llamadas sucesivas a la rutina *nx_web_http_client_put_packet()* para enviar el contenido del recurso al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-937">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="168cc-938">Tenga en cuenta que la cadena de recurso puede hacer referencia a un archivo local, por ejemplo, “/index.htm”, o puede hacer referencia a otra dirección URL, por ejemplo, `http://abc.website.com/index.htm` si el servidor HTTP indica que admite solicitudes PUT de referencia.</span><span class="sxs-lookup"><span data-stu-id="168cc-938">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="168cc-939">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-939">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-940">Este servicio reemplaza a *nx_web_http_client_put_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="168cc-940">This service replaces *nx_web_http_client_put_secure_start*().</span></span> <span data-ttu-id="168cc-941">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-941">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-942">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-942">Input Parameters</span></span>

- <span data-ttu-id="168cc-943">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-943">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-944">**ip_address** Dirección IP del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-944">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="168cc-945">**server_port** Puerto TCP en el servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-945">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="168cc-946">**resource** Puntero a la cadena de dirección URL para el recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-946">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="168cc-947">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-947">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-948">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-948">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-949">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-949">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-950">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-950">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-951">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-951">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-952">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-952">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-953">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-953">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-954">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-954">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-955">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-955">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-956">**total_bytes** Bytes totales del recurso que se está enviando.</span><span class="sxs-lookup"><span data-stu-id="168cc-956">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="168cc-957">Tenga en cuenta que la longitud combinada de todos los paquetes enviados a través de las llamadas subsiguientes a *nx_web_http_client_put_packet()* debe ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="168cc-957">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="168cc-958">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-958">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-959">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-959">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-960">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-960">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-961">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-961">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-962">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-962">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-964">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-964">Return Values</span></span>

- <span data-ttu-id="168cc-965">**NX_SUCCESS** (0x00) Solicitud POST enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-965">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="168cc-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) El nombre de usuario es demasiado grande para el búfer.</span><span class="sxs-lookup"><span data-stu-id="168cc-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="168cc-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-968">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-968">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-969">NX_SIZE_ERROR (0x09) Tamaño total de recurso no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-969">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="168cc-970">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-970">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-971">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-971">Allowed From</span></span>

<span data-ttu-id="168cc-972">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-972">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-973">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-973">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a><span data-ttu-id="168cc-974">nx_web_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="168cc-974">nx_web_http_client_put_packet</span></span>

<span data-ttu-id="168cc-975">Envía el siguiente paquete de datos de recursos</span><span class="sxs-lookup"><span data-stu-id="168cc-975">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-976">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-976">Prototype</span></span>

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-977">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-977">Description</span></span>

<span data-ttu-id="168cc-978">Este servicio intenta enviar el siguiente paquete de contenido de recursos al servidor HTTP para las operaciones PUT y POST.</span><span class="sxs-lookup"><span data-stu-id="168cc-978">This service attempts to send the next packet of resource content to the HTTP Server for both PUT and POST operations.</span></span> <span data-ttu-id="168cc-979">Tenga en cuenta que se debe llamar a esta rutina repetidamente hasta que la longitud combinada de los paquetes enviados sea igual al objeto “total_bytes” especificado en la llamada anterior a *nx_web_http_client_put_start()* o *nx_web_http_client_post_start()* (o sus correspondientes versiones seguras).</span><span class="sxs-lookup"><span data-stu-id="168cc-979">Note that this routine should be called repetitively until the combined length of the packets sent equals the "total_bytes" specified in the previous *nx_web_http_client_put_start()* or *nx_web_http_client_post_start()* call (or their corresponding secure versions).</span></span>

<span data-ttu-id="168cc-980">Este servicio también busca una respuesta del servidor en caso de que se haya producido un problema al establecer la conexión HTTP (o HTTPS).</span><span class="sxs-lookup"><span data-stu-id="168cc-980">This service also checks for a response from the server in case there was a problem establishing the HTTP (or HTTPS) connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-981">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-981">Input Parameters</span></span>

- <span data-ttu-id="168cc-982">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-982">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-983">**packet_ptr** Puntero al siguiente contenido del recurso que se va a enviar al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-983">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="168cc-984">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-984">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-985">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-985">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-986">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-986">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-988">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-988">Return Values</span></span>

- <span data-ttu-id="168cc-989">**NX_SUCCESS** (0x00) Paquete de cliente HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-989">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="168cc-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está listo.</span><span class="sxs-lookup"><span data-stu-id="168cc-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="168cc-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Código de error del servidor recibido.\*\*</span><span class="sxs-lookup"><span data-stu-id="168cc-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Received Server error code\*\*</span></span>
- <span data-ttu-id="168cc-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Longitud de paquete no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="168cc-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nombre y/o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or Password</span></span>
- <span data-ttu-id="168cc-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) El servidor responde antes de que PUT finalice.</span><span class="sxs-lookup"><span data-stu-id="168cc-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Server responds before PUT is complete</span></span>
- <span data-ttu-id="168cc-995">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-995">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-996">NX_INVALID_PACKET (0x12) El paquete es demasiado pequeño para el encabezado TCP.</span><span class="sxs-lookup"><span data-stu-id="168cc-996">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="168cc-997">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-997">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-998">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-998">Allowed From</span></span>

<span data-ttu-id="168cc-999">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-999">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1000">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1000">Example</span></span>

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a><span data-ttu-id="168cc-1001">nx_web_http_client_request_chunked_set</span><span class="sxs-lookup"><span data-stu-id="168cc-1001">nx_web_http_client_request_chunked_set</span></span>

<span data-ttu-id="168cc-1002">Establece una transferencia fragmentada para la solicitud HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="168cc-1002">Set chunked transfer for HTTP(S) request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1003">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1003">Prototype</span></span>

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="168cc-1004">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1004">Description</span></span>

<span data-ttu-id="168cc-1005">Este servicio utiliza codificación de transferencia fragmentada para enviar una solicitud HTTP(S) personalizada al servidor especificado en la llamada *nx_web_http_client_connect()* o *nx_web_http_client_secure_connect()* que previamente ha establecido la conexión de socket al host remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1005">This service uses chunked transfer coding to send a custom HTTP(S) request to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* call which has previously established the socket connection to the remote host.</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-1006">Si la aplicación utiliza codificación de transferencia fragmentada para enviar un paquete de datos de solicitud, debe llamar a este servicio después de llamar a *nx_web_http_client_request_packet_allocate*() y antes de llamar a *nx_web_http_client_reqeust_packet_send*().</span><span class="sxs-lookup"><span data-stu-id="168cc-1006">If the application uses chunked transfer coding to send a request data packet, it must call this service after calling *nx_web_http_client_request_packet_allocate*(), and before call *nx_web_http_client_reqeust_packet_send* ().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1007">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1007">Input Parameters</span></span>

- <span data-ttu-id="168cc-1008">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1008">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-1009">**chunk_size** Tamaño de los datos de fragmentos en octetos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1009">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="168cc-1010">**packet_ptr** El puntero de paquete de datos de solicitud HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="168cc-1010">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1011">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1011">Return Values</span></span>

- <span data-ttu-id="168cc-1012">**NX_SUCCESS** (0x00) Fragmento establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1012">**NX_SUCCESS** (0x00) Successfully set chunked.</span></span>
- <span data-ttu-id="168cc-1013">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1013">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1014">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1014">Allowed From</span></span>

<span data-ttu-id="168cc-1015">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1015">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1016">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1016">Example</span></span>

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT, "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a><span data-ttu-id="168cc-1017">nx_web_http_client_request_header_add</span><span class="sxs-lookup"><span data-stu-id="168cc-1017">nx_web_http_client_request_header_add</span></span>

<span data-ttu-id="168cc-1018">Agrega un encabezado personalizado a una solicitud HTTP personalizada</span><span class="sxs-lookup"><span data-stu-id="168cc-1018">Add a custom header to a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1019">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1019">Prototype</span></span>

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-1020">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1020">Description</span></span>

<span data-ttu-id="168cc-1021">Este servicio agrega un encabezado personalizado (en forma de nombre y valor de campo) a una solicitud HTTP personalizada creada con n *x_web_http_client_request_initialize()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1021">This service adds a custom header (in the form of a field name and value) to a custom HTTP request created with n *x_web_http_client_request_initialize()*.</span></span>

<span data-ttu-id="168cc-1022">El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1022">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="168cc-1023">**Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.**</span><span class="sxs-lookup"><span data-stu-id="168cc-1023">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-1024">Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1024">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="168cc-1025">Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_initialize())* para crear y enviar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1025">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1026">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1026">Input Parameters</span></span>

- <span data-ttu-id="168cc-1027">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1027">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-1028">**field_name** Cadena de nombre de campo (por ejemplo, “Content-Type”).</span><span class="sxs-lookup"><span data-stu-id="168cc-1028">**field_name** Field name string (e.g. "Content-Type").</span></span>
- <span data-ttu-id="168cc-1029">**name_length** Longitud de la cadena de nombre de campo en bytes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1029">**name_length** Length of field name string in bytes.</span></span>
- <span data-ttu-id="168cc-1030">**field_value** Cadena de valor de campo (por ejemplo, “application/octet-stream”).</span><span class="sxs-lookup"><span data-stu-id="168cc-1030">**field_value** Field value string (e.g. "application/octet-stream").</span></span>
- <span data-ttu-id="168cc-1031">**value_length** Longitud de la cadena de valor en bytes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1031">**value_length** Length of value string in bytes.</span></span>
- <span data-ttu-id="168cc-1032">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1032">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-1033">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1033">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1034">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1034">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1036">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1036">Return Values</span></span>

- <span data-ttu-id="168cc-1037">**NX_SUCCESS** (0x00) Se ha agregado correctamente el encabezado a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1037">**NX_SUCCESS** (0x00) Successful addition of header to request.</span></span>
- <span data-ttu-id="168cc-1038">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1038">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1039">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1039">Allowed From</span></span>

<span data-ttu-id="168cc-1040">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1040">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1041">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1041">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a><span data-ttu-id="168cc-1042">nx_web_http_client_request_initialize</span><span class="sxs-lookup"><span data-stu-id="168cc-1042">nx_web_http_client_request_initialize</span></span>

<span data-ttu-id="168cc-1043">Inicializa una solicitud HTTP personalizada</span><span class="sxs-lookup"><span data-stu-id="168cc-1043">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1044">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1044">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-1045">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1045">Description</span></span>

<span data-ttu-id="168cc-1046">Este servicio crea una solicitud HTTP personalizada y la asocia a la instancia de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1046">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="168cc-1047">A diferencia del servicio más sencillo *nx_web_http_client_get_start()* (junto con los métodos para PUT, POST y las versiones seguras asociadas de esas API), la solicitud personalizada no se envía hasta que se llama al servicio *nx_web_http_client_request_send()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1047">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="168cc-1048">El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud mediante el servicio ***nx_web_http_client_request_header_add()***.</span><span class="sxs-lookup"><span data-stu-id="168cc-1048">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="168cc-1049">Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.</span><span class="sxs-lookup"><span data-stu-id="168cc-1049">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-1050">Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1050">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="168cc-1051">Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_send())* para crear y enviar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1051">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="168cc-1052">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1052">This service is deprecated.</span></span> <span data-ttu-id="168cc-1053">Se recomienda a los desarrolladores que utilicen *nx_web_http_client_request_initialize_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1053">Developers are encouraged to use *nx_web_http_client_request_initialize_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1054">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1054">Input Parameters</span></span>

- <span data-ttu-id="168cc-1055">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1055">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-1056">**method** Método de solicitud HTTP que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1056">**method** The HTTP request method to use.</span></span> <span data-ttu-id="168cc-1057">Las opciones se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1057">The options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="168cc-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="168cc-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="168cc-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="168cc-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="168cc-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="168cc-1064">**resource** Nombre del recurso que se va a transferir.</span><span class="sxs-lookup"><span data-stu-id="168cc-1064">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="168cc-1065">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-1065">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-1066">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1066">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-1067">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-1067">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-1068">**input_size** Tamaño de los datos de entrada para PUT y POST.</span><span class="sxs-lookup"><span data-stu-id="168cc-1068">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="168cc-1069">Pase 0 para otras operaciones.</span><span class="sxs-lookup"><span data-stu-id="168cc-1069">Pass 0 for other operations.</span></span>
- <span data-ttu-id="168cc-1070">**transfer_encoding_trunked** Parámetro reservado para la compatibilidad futura con transferencias troncales.</span><span class="sxs-lookup"><span data-stu-id="168cc-1070">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="168cc-1071">**username** Nombre de usuario para los recursos protegidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1071">**username** Username for protected resources.</span></span>
- <span data-ttu-id="168cc-1072">**password** Contraseña para los recursos protegidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1072">**password** Password for protected resources.</span></span>
- <span data-ttu-id="168cc-1073">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1073">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-1074">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1074">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1075">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1075">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1077">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1077">Return Values</span></span>

- <span data-ttu-id="168cc-1078">**NX_SUCCESS** (0x00) La solicitud se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1078">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="168cc-1079">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1079">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Faltaba información necesaria (por ejemplo, input_size para PUT o POST).</span><span class="sxs-lookup"><span data-stu-id="168cc-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1081">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1081">Allowed From</span></span>

<span data-ttu-id="168cc-1082">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1082">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1083">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1083">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a><span data-ttu-id="168cc-1084">nx_web_http_client_request_initialize_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-1084">nx_web_http_client_request_initialize_extended</span></span>

<span data-ttu-id="168cc-1085">Inicializa una solicitud HTTP personalizada</span><span class="sxs-lookup"><span data-stu-id="168cc-1085">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1086">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1086">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-1087">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1087">Description</span></span>

<span data-ttu-id="168cc-1088">Este servicio crea una solicitud HTTP personalizada y la asocia a la instancia de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1088">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="168cc-1089">A diferencia del servicio más sencillo *nx_web_http_client_get_start()* (junto con los métodos para PUT, POST y las versiones seguras asociadas de esas API), la solicitud personalizada no se envía hasta que se llama al servicio *nx_web_http_client_request_send()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1089">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="168cc-1090">El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud mediante el servicio ***nx_web_http_client_request_header_add()***.</span><span class="sxs-lookup"><span data-stu-id="168cc-1090">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="168cc-1091">Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.</span><span class="sxs-lookup"><span data-stu-id="168cc-1091">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-1092">Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1092">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="168cc-1093">Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_send())* para crear y enviar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1093">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="168cc-1094">Las cadenas de recurso, host, nombre de usuario y contraseña deben terminar en NULL y la longitud de cada cadena coincide con la especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1094">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-1095">Este servicio reemplaza a *nx_web_http_client_request_initialize*().</span><span class="sxs-lookup"><span data-stu-id="168cc-1095">This service replaces *nx_web_http_client_request_initialize*().</span></span> <span data-ttu-id="168cc-1096">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-1096">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1097">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1097">Input Parameters</span></span>

- <span data-ttu-id="168cc-1098">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1098">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-1099">**method** Método de solicitud HTTP que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1099">**method** The HTTP request method to use.</span></span> <span data-ttu-id="168cc-1100">Las opciones se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1100">The options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="168cc-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="168cc-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="168cc-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="168cc-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="168cc-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="168cc-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="168cc-1107">**resource** Nombre del recurso que se va a transferir.</span><span class="sxs-lookup"><span data-stu-id="168cc-1107">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="168cc-1108">**resource_length** Longitud de cadena del recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1108">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="168cc-1109">**host** Cadena terminada en NULL del nombre de dominio del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-1109">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="168cc-1110">Esta cadena se transmite en el campo de encabezado del host HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1110">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="168cc-1111">La cadena de host no puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="168cc-1111">The host string cannot be NULL.</span></span>
- <span data-ttu-id="168cc-1112">**host_length** Longitud de cadena del host.</span><span class="sxs-lookup"><span data-stu-id="168cc-1112">**host_length** String length of host.</span></span>
- <span data-ttu-id="168cc-1113">**input_size** Tamaño de los datos de entrada para PUT y POST.</span><span class="sxs-lookup"><span data-stu-id="168cc-1113">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="168cc-1114">Pase 0 para otras operaciones.</span><span class="sxs-lookup"><span data-stu-id="168cc-1114">Pass 0 for other operations.</span></span>
- <span data-ttu-id="168cc-1115">**transfer_encoding_trunked** Parámetro reservado para la compatibilidad futura con transferencias troncales.</span><span class="sxs-lookup"><span data-stu-id="168cc-1115">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="168cc-1116">**username** Puntero al nombre de usuario opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1116">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="168cc-1117">**username_length** Longitud de cadena del nombre de usuario para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1117">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="168cc-1118">**password** Puntero a la contraseña opcional para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1118">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="168cc-1119">**password_length** Longitud de cadena de la contraseña para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1119">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="168cc-1120">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1120">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-1121">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1121">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1122">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1122">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1124">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1124">Return Values</span></span>

- <span data-ttu-id="168cc-1125">**NX_SUCCESS** (0x00) La solicitud se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1125">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="168cc-1126">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1126">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Faltaba información necesaria (por ejemplo, input_size para PUT o POST).</span><span class="sxs-lookup"><span data-stu-id="168cc-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1128">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1128">Allowed From</span></span>

<span data-ttu-id="168cc-1129">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1130">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1130">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a><span data-ttu-id="168cc-1131">nx_web_http_client_request_packet_send</span><span class="sxs-lookup"><span data-stu-id="168cc-1131">nx_web_http_client_request_packet_send</span></span>

<span data-ttu-id="168cc-1132">Envía un paquete de datos de solicitud HTTP(S) al servidor remoto</span><span class="sxs-lookup"><span data-stu-id="168cc-1132">Send HTTP(S) request data packet to remote server</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1133">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1133">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-1134">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1134">Description</span></span>

<span data-ttu-id="168cc-1135">Este servicio envía un paquete de datos de solicitud HTTP(S) personalizado creado con *nx_web_http_client_request_packet_allocate*() al servidor especificado en la llamada *nx_web_http_client_connect()* o *nx_web_http_client_secure_connect(* ) que previamente ha establecido la conexión de socket al host remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1135">This service sends a custom HTTP(S) request data packet created with *nx_web_http_client_request_packet_allocate* () to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect(*) call which has previously established the socket connection to the remote host.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1136">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1136">Input Parameters</span></span>

- <span data-ttu-id="168cc-1137">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1137">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-1138">**packet_ptr** El puntero de paquete de datos de solicitud HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="168cc-1138">**packet_ptr** HTTP(S) request data packet pointer.</span></span>
- <span data-ttu-id="168cc-1139">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1139">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-1140">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1140">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1141">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1141">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1143">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1143">Return Values</span></span>

- <span data-ttu-id="168cc-1144">**NX_SUCCESS** (0x00) Paquete de datos de la solicitud enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1144">**NX_SUCCESS** (0x00) Successful send of request data packet.</span></span>
- <span data-ttu-id="168cc-1145">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1145">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1146">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1146">Allowed From</span></span>

<span data-ttu-id="168cc-1147">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1148">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1148">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a><span data-ttu-id="168cc-1149">nx_web_http_client_request_send</span><span class="sxs-lookup"><span data-stu-id="168cc-1149">nx_web_http_client_request_send</span></span>

<span data-ttu-id="168cc-1150">Envía una solicitud HTTP personalizada</span><span class="sxs-lookup"><span data-stu-id="168cc-1150">Send a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1151">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1151">Prototype</span></span>

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-1152">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1152">Description</span></span>

<span data-ttu-id="168cc-1153">Este servicio envía una solicitud HTTP personalizada creada con *nx_web_http_client_request_initialize*() al servidor especificado en la llamada *nx_web_http_client_connect()* o *nx_web_http_client_secure_connect(* ) (ambos previamente han establecido la conexión de socket al host remoto).</span><span class="sxs-lookup"><span data-stu-id="168cc-1153">This service sends a custom HTTP request created with *nx_web_http_client_request_initialize()* to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* both of which have previously established the socket connection to the remote host.</span></span>

<span data-ttu-id="168cc-1154">El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud mediante el servicio ***nx_web_http_client_request_header_add()***.</span><span class="sxs-lookup"><span data-stu-id="168cc-1154">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="168cc-1155">Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.</span><span class="sxs-lookup"><span data-stu-id="168cc-1155">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-1156">Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1156">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="168cc-1157">Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_initialize())* para crear y enviar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1157">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1158">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1158">Input Parameters</span></span>

- <span data-ttu-id="168cc-1159">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1159">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-1160">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1160">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-1161">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1161">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1162">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1162">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1164">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1164">Return Values</span></span>

- <span data-ttu-id="168cc-1165">**NX_SUCCESS** (0x00) Solicitud enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1165">**NX_SUCCESS** (0x00) Successful send of request.</span></span>
- <span data-ttu-id="168cc-1166">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1166">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1167">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1167">Allowed From</span></span>

<span data-ttu-id="168cc-1168">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1169">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1169">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a><span data-ttu-id="168cc-1170">nx_web_http_client_response_body_get</span><span class="sxs-lookup"><span data-stu-id="168cc-1170">nx_web_http_client_response_body_get</span></span>

<span data-ttu-id="168cc-1171">Obtiene el siguiente paquete de datos de recursos</span><span class="sxs-lookup"><span data-stu-id="168cc-1171">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1172">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1172">Prototype</span></span>

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-1173">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1173">Description</span></span>

<span data-ttu-id="168cc-1174">Este servicio recupera el siguiente paquete de contenido del recurso solicitado por la llamada anterior a *nx_web_http_client_get_start()* o *nx_web_http_client_get_secure_start()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1174">This service retrieves the next packet of content of the resource requested by the previous *nx_web_http_client_get_start()* or *nx_web_http_client_get_secure_start()* call.</span></span> <span data-ttu-id="168cc-1175">Deben realizarse llamadas sucesivas a esta rutina hasta que se reciba el estado de devolución de NX_WEB_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="168cc-1175">Successive calls to this routine should be made until the return status of NX_WEB_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1176">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1176">Input Parameters</span></span>

- <span data-ttu-id="168cc-1177">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1177">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-1178">**packet_ptr** Destino del puntero de paquete que contiene el contenido parcial del recurso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1178">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="168cc-1179">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1179">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-1180">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1180">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1181">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1181">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1183">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1183">Return Values</span></span>

- <span data-ttu-id="168cc-1184">**NX_SUCCESS** (0x00) Paquete de cliente HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1184">**NX_SUCCESS** (0x00) Successful get of HTTP Client packet.</span></span>
- <span data-ttu-id="168cc-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) Obtención del paquete de cliente HTTP completada.</span><span class="sxs-lookup"><span data-stu-id="168cc-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client get packet is done</span></span>
- <span data-ttu-id="168cc-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) El cliente HTTP no está en modo GET.</span><span class="sxs-lookup"><span data-stu-id="168cc-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="168cc-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Longitud de paquete no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="168cc-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) Código de estado HTTP 100 - Continuar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP status code 100 Continue</span></span>
- <span data-ttu-id="168cc-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) Código de estado HTTP 101 - Cambiando protocolos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP status code 101 Switching Protocols</span></span>
- <span data-ttu-id="168cc-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) Código de estado HTTP 201 - Creado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP status code 201 Created</span></span>
- <span data-ttu-id="168cc-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) Código de estado HTTP 202 - Aceptado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP status code 202 Accepted</span></span>
- <span data-ttu-id="168cc-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) Código de estado HTTP 203 - Información no autoritativa.</span><span class="sxs-lookup"><span data-stu-id="168cc-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP status code 203 Non-Authoritative Information</span></span>
- <span data-ttu-id="168cc-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) Código de estado HTTP 204 - Sin contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP status code 204 No Content</span></span>
- <span data-ttu-id="168cc-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) Código de estado HTTP 205 - Restablecer contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP status code 205 Reset Content</span></span>
- <span data-ttu-id="168cc-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) Código de estado HTTP 206 - Contenido parcial.</span><span class="sxs-lookup"><span data-stu-id="168cc-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP status code 206 Partial Content</span></span>
- <span data-ttu-id="168cc-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) Código de estado HTTP 300 - Varias opciones.</span><span class="sxs-lookup"><span data-stu-id="168cc-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP status code 300 Multiple Choices</span></span>
- <span data-ttu-id="168cc-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) Código de estado HTTP 301 - Trasladado permanentemente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently</span></span>
- <span data-ttu-id="168cc-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) Código de estado HTTP 302 - Encontrado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP status code 302 Found</span></span>
- <span data-ttu-id="168cc-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) Código de estado HTTP 303 - Ver otro.</span><span class="sxs-lookup"><span data-stu-id="168cc-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP status code 303 See Other</span></span>
- <span data-ttu-id="168cc-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) Código de estado HTTP 304 - Sin modificar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP status code 304 Not Modified</span></span>
- <span data-ttu-id="168cc-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) Código de estado HTTP 305 - Usar proxy.</span><span class="sxs-lookup"><span data-stu-id="168cc-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP status code 305 Use Proxy</span></span>
- <span data-ttu-id="168cc-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) Código de estado HTTP 307 - Redirección temporal.</span><span class="sxs-lookup"><span data-stu-id="168cc-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP status code 307 Temporary Redirect</span></span>
- <span data-ttu-id="168cc-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) Código de estado HTTP 400 - Solicitud incorrecta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP status code 400 Bad Request</span></span>
- <span data-ttu-id="168cc-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) Código de estado HTTP 401 - No autorizado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span></span>
- <span data-ttu-id="168cc-1205">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x3002B) Código de estado HTTP 402 - Solicitud incorrecta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP status code 402 Payment Required</span></span>
- <span data-ttu-id="168cc-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) Código de estado HTTP 403 - Prohibido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span></span>
- <span data-ttu-id="168cc-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) Código de estado HTTP 404 - No encontrado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP status code 404 Not Found</span></span>
- <span data-ttu-id="168cc-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) Código de estado HTTP 405 - Método no permitido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP status code 405 Method Not Allowed</span></span>
- <span data-ttu-id="168cc-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) Código de estado HTTP 406 - No aceptable.</span><span class="sxs-lookup"><span data-stu-id="168cc-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP status code 406 Not Acceptable</span></span>
- <span data-ttu-id="168cc-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) Código de estado HTTP 407 - Autenticación de proxy necesaria.</span><span class="sxs-lookup"><span data-stu-id="168cc-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span></span>
- <span data-ttu-id="168cc-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) Código de estado HTTP 408 - Tiempo de espera de solicitud agotado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP status code 408 Request Time-out</span></span>
- <span data-ttu-id="168cc-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) Código de estado HTTP 409 - Conflicto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP status code 409 Conflict</span></span>
- <span data-ttu-id="168cc-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) Código de estado HTTP 410 - Desaparecido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP status code 410 Gone</span></span>
- <span data-ttu-id="168cc-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) Código de estado HTTP 411 - Longitud requerida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP status code 411 Length Required</span></span>
- <span data-ttu-id="168cc-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) Código de estado HTTP 412 - Error de condición previa.</span><span class="sxs-lookup"><span data-stu-id="168cc-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP status code 412 Precondition Failed</span></span>
- <span data-ttu-id="168cc-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) Código de estado HTTP 413 - Entidad de solicitud demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="168cc-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large</span></span>
- <span data-ttu-id="168cc-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) Código de estado HTTP 414 - Dirección URL de solicitud demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="168cc-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP status code 414 Request URL Too Large</span></span>
- <span data-ttu-id="168cc-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) Código de estado HTTP 415 - Tipo de medio no admitido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type</span></span>
- <span data-ttu-id="168cc-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) Código de estado HTTP 416 - No se puede satisfacer el rango solicitado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP status code 416 Requested range not satisfiable</span></span>
- <span data-ttu-id="168cc-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) Código de estado HTTP 417 - Error de expectativa.</span><span class="sxs-lookup"><span data-stu-id="168cc-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed</span></span>
- <span data-ttu-id="168cc-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) Código de estado HTTP 500 - Error interno del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP status code 500 Internal Server Error</span></span>
- <span data-ttu-id="168cc-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) Código de estado HTTP 501 - No implementado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP status code 501 Not Implemented</span></span>
- <span data-ttu-id="168cc-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) Código de estado HTTP 502 - Puerta de enlace incorrecta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP status code 502 Bad Gateway</span></span>
- <span data-ttu-id="168cc-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) Código de estado HTTP 503 - Servicio no disponible.</span><span class="sxs-lookup"><span data-stu-id="168cc-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP status code 503 Service Unavailable</span></span>
- <span data-ttu-id="168cc-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) Código de estado HTTP 504 - Tiempo de espera de puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="168cc-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP status code 504 Gateway Time-out</span></span>
- <span data-ttu-id="168cc-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) Código de estado HTTP 505 - Versión no admitida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP status code 505 HTTP Version not supported</span></span>
- <span data-ttu-id="168cc-1227">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1227">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1228">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1228">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1229">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1229">Allowed From</span></span>

<span data-ttu-id="168cc-1230">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1231">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1231">Example</span></span>

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a><span data-ttu-id="168cc-1232">nx_web_http_client_response_header_callback_set</span><span class="sxs-lookup"><span data-stu-id="168cc-1232">nx_web_http_client_response_header_callback_set</span></span>

<span data-ttu-id="168cc-1233">Establece la devolución de llamada para invocar al procesar encabezados HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-1233">Set callback to invoke when processing HTTP headers</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1234">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1234">Prototype</span></span>

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a><span data-ttu-id="168cc-1235">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1235">Description</span></span>

<span data-ttu-id="168cc-1236">Este servicio asigna una devolución de llamada que se invocará cuando el cliente Web HTTP de NetX procese un encabezado HTTP en una respuesta entrante desde un servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1236">This service assigns a callback that will be invoked whenever NetX Web HTTP Client processes an HTTP header in an incoming response from a remote HTTP server.</span></span> <span data-ttu-id="168cc-1237">La devolución de llamada se invoca una vez para cada encabezado de la respuesta cuando se procesa.</span><span class="sxs-lookup"><span data-stu-id="168cc-1237">The callback is invoked once for each header in the response as it is processed.</span></span> <span data-ttu-id="168cc-1238">La devolución de llamada permite a una aplicación cliente HTTP tener acceso a cada uno de los encabezados de la respuesta del servidor HTTP para realizar cualquier acción deseada más allá del procesamiento básico que el cliente Web HTTP de NetX.</span><span class="sxs-lookup"><span data-stu-id="168cc-1238">The callback allows an HTTP Client application to access each of the headers in the HTTP server response to take any desired actions beyond the basic processing that NetX Web HTTP Client does.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1239">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1239">Input Parameters</span></span>

<span data-ttu-id="168cc-1240">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1240">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="168cc-1241">**callback_function** Devolución de llamada invocada durante el procesamiento de encabezados de respuesta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1241">**callback_function** Callback invoked during response header processing.</span></span> <span data-ttu-id="168cc-1242">La devolución de llamada se invoca con el nombre y el valor del campo como cadenas (y sus longitudes).</span><span class="sxs-lookup"><span data-stu-id="168cc-1242">The callback is invoked with the field name and value as strings (and their lengths).</span></span> <span data-ttu-id="168cc-1243">Por ejemplo, el encabezado “Content-Length: 100” haría que la función se invocara con “Content-Length” para *field_name* y la cadena “100” para *field_value*.</span><span class="sxs-lookup"><span data-stu-id="168cc-1243">For example, the header "Content-Length: 100" would cause the function to be invoked with "Content-Length" for *field_name* and the string "100" for *field_value*.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1244">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1244">Return Values</span></span>

- <span data-ttu-id="168cc-1245">**NX_SUCCESS** (0x00) Asignación correcta de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="168cc-1245">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="168cc-1246">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1246">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1247">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1247">Allowed From</span></span>

<span data-ttu-id="168cc-1248">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1248">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1249">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1249">Example</span></span>

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a><span data-ttu-id="168cc-1250">nx_web_http_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="168cc-1250">nx_web_http_client_secure_connect</span></span>

<span data-ttu-id="168cc-1251">Abre una sesión de TLS en un servidor HTTPS para las solicitudes personalizadas</span><span class="sxs-lookup"><span data-stu-id="168cc-1251">Open a TLS session to an HTTPS server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1252">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1252">Prototype</span></span>

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-1253">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1253">Description</span></span>

<span data-ttu-id="168cc-1254">Este método es para HTTPS **protegido por TLS**.</span><span class="sxs-lookup"><span data-stu-id="168cc-1254">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="168cc-1255">Este servicio abre una sesión de TLS protegida en un servidor HTTPS, pero no envía ninguna solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1255">This service opens a secured TLS session to an HTTPS server but does not send any requests.</span></span> <span data-ttu-id="168cc-1256">Las solicitudes se crean con n *x_web_http_client_request_initialize()* y se envían mediante *nx_web_http_client_request_send()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1256">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="168cc-1257">Se pueden agregar encabezados HTTP personalizados a la solicitud mediante *nx_web_http_client_request_header_add()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1257">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="168cc-1258">El uso de este servicio permite que una aplicación agregue cualquier número de encabezados personalizados a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1258">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="168cc-1259">**Esto permite solicitudes HTTP personalizadas diseñadas para aplicaciones específicas.**</span><span class="sxs-lookup"><span data-stu-id="168cc-1259">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-1260">Se proporcionan los métodos nx_web_http_client_\*_start para mayor comodidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1260">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="168cc-1261">Todas estas funciones usan esta rutina internamente (junto con *nx_web_http_client_request_initialize())* para crear y enviar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1261">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1262">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1262">Input Parameters</span></span>

- <span data-ttu-id="168cc-1263">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1263">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-1264">**server_ip** Dirección IP del servidor HTTPS remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1264">**server_ip** IP address of remote HTTPS server.</span></span>
- <span data-ttu-id="168cc-1265">**server_port** Puerto en el servidor HTTPS remoto (por ejemplo, 443 para HTTPS).</span><span class="sxs-lookup"><span data-stu-id="168cc-1265">**server_port** Port on remote HTTPS server (e.g. 443 for HTTPS).</span></span>
- <span data-ttu-id="168cc-1266">**tls_setup** Devolución de llamada que se usa para la configuración de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1266">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="168cc-1267">La aplicación define esta devolución de llamada para inicializar las credenciales y la criptografía de TLS (por ejemplo, los certificados).</span><span class="sxs-lookup"><span data-stu-id="168cc-1267">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="168cc-1268">**wait_option** Define cuánto tiempo esperará el servicio a la solicitud de inicio del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1268">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="168cc-1269">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1269">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1270">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1270">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="168cc-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1272">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1272">Return Values</span></span>

- <span data-ttu-id="168cc-1273">**NX_SUCCESS** (0x00) Conexión correcta de la sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1273">**NX_SUCCESS** (0x00) Successful connection of TLS session.</span></span>
- <span data-ttu-id="168cc-1274">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Ya hay otra solicitud en curso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1276">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1276">Allowed From</span></span>

<span data-ttu-id="168cc-1277">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1278">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1278">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a><span data-ttu-id="168cc-1279">API de servidor HTTP y HTTPS</span><span class="sxs-lookup"><span data-stu-id="168cc-1279">HTTP and HTTPS Server API</span></span>

## <a name="nx_web_http_server_cache_info_callback_set"></a><span data-ttu-id="168cc-1280">nx_web_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="168cc-1280">nx_web_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="168cc-1281">Establece la devolución de llamada para recuperar la antigüedad máxima y la fecha de la dirección URL</span><span class="sxs-lookup"><span data-stu-id="168cc-1281">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1282">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1282">Prototype</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a><span data-ttu-id="168cc-1283">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1283">Description</span></span>

<span data-ttu-id="168cc-1284">Este servicio establece el servicio de devolución de llamada invocado para obtener la antigüedad máxima y la fecha de última modificación del recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1284">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1285">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1285">Input Parameters</span></span>

- <span data-ttu-id="168cc-1286">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1286">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1287">**cache_info_get** Puntero a la devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="168cc-1287">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="168cc-1288">**max_age** Puntero a la antigüedad máxima de un recurso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1288">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="168cc-1289">**data** Puntero a la fecha de última modificación devuelta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1289">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1290">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1290">Return Values</span></span>

- <span data-ttu-id="168cc-1291">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1291">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="168cc-1292">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1292">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1293">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1293">Allowed From</span></span>

<span data-ttu-id="168cc-1294">Inicialización</span><span class="sxs-lookup"><span data-stu-id="168cc-1294">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1295">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1295">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a><span data-ttu-id="168cc-1296">nx_web_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="168cc-1296">nx_web_http_server_callback_data_send</span></span>

<span data-ttu-id="168cc-1297">Envía datos desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="168cc-1297">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1298">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1298">Prototype</span></span>

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="168cc-1299">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1299">Description</span></span>

<span data-ttu-id="168cc-1300">Este servicio envía los datos del paquete proporcionado desde la rutina de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1300">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="168cc-1301">Normalmente se usa para enviar datos dinámicos asociados a solicitudes GET/POST.</span><span class="sxs-lookup"><span data-stu-id="168cc-1301">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="168cc-1302">Tenga en cuenta que si se usa esta función, la rutina de devolución de llamada es responsable de enviar la respuesta completa en el formato correcto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1302">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="168cc-1303">Además, la rutina de devolución de llamada debe devolver el estado de NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="168cc-1303">In addition, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1304">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1304">Input Parameters</span></span>

- <span data-ttu-id="168cc-1305">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1305">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1306">**data_ptr** Puntero a los datos que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1306">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="168cc-1307">**data_length** Número de bytes que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1307">**data_length** Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1308">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1308">Return Values</span></span>

- <span data-ttu-id="168cc-1309">**NX_SUCCESS** (0x00) Datos del servidor enviados correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1309">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="168cc-1310">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1310">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1311">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1311">Allowed From</span></span>

<span data-ttu-id="168cc-1312">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1313">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1313">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a><span data-ttu-id="168cc-1314">nx_web_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="168cc-1314">nx_web_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="168cc-1315">Crea un encabezado de respuesta en una función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="168cc-1315">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1316">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1316">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="168cc-1317">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1317">Description</span></span>

<span data-ttu-id="168cc-1318">Este servicio se usa en la rutina de devolución de llamada del servidor HTTP(S) (definida por la aplicación) para generar un encabezado de respuesta HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1318">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="168cc-1319">La rutina de devolución de llamada del servidor se invoca cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE de cliente que requieren una respuesta HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1319">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="168cc-1320">Esta función toma la información de la respuesta de la aplicación y genera el encabezado de respuesta adecuado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1320">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="168cc-1321">Consulte el servicio *nx_web_http_server_create()* para obtener más información sobre la rutina de devolución de llamada de solicitud del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-1321">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

<span data-ttu-id="168cc-1322">Esta API está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1322">This API is deprecated.</span></span> <span data-ttu-id="168cc-1323">Se recomienda a los desarrolladores que utilicen *nx_web_http_server_callback_generate_response_header_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1323">Developers are encouraged to use *nx_web_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1324">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1324">Input Parameters</span></span>

- <span data-ttu-id="168cc-1325">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1325">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1326">**packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="168cc-1326">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="168cc-1327">**status_code** Indica el estado del recurso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1327">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="168cc-1328">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="168cc-1328">Examples:</span></span>
  - <span data-ttu-id="168cc-1329">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="168cc-1329">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="168cc-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="168cc-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="168cc-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="168cc-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="168cc-1332">**content_length** Tamaño del contenido en bytes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1332">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="168cc-1333">**content_type** Tipo de HTTP, por ejemplo, “texto/sin formato”.</span><span class="sxs-lookup"><span data-stu-id="168cc-1333">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="168cc-1334">**additional_header** Puntero a texto de encabezado adicional.</span><span class="sxs-lookup"><span data-stu-id="168cc-1334">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1335">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1335">Return Values</span></span>

- <span data-ttu-id="168cc-1336">**NX_SUCCESS** (0x00) Encabezado HTML creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1336">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="168cc-1337">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1337">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1338">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1338">Allowed From</span></span>

<span data-ttu-id="168cc-1339">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1339">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1340">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1340">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="168cc-1341">nx_web_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-1341">nx_web_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="168cc-1342">Crea un encabezado de respuesta en una función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="168cc-1342">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1343">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1343">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="168cc-1344">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1344">Description</span></span>

<span data-ttu-id="168cc-1345">Este servicio se usa en la rutina de devolución de llamada del servidor HTTP(S) (definida por la aplicación) para generar un encabezado de respuesta HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1345">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="168cc-1346">La rutina de devolución de llamada del servidor se invoca cuando el servidor HTTP responde a las solicitudes GET, PUT y DELETE de cliente que requieren una respuesta HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1346">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="168cc-1347">Esta función toma la información de la respuesta de la aplicación y genera el encabezado de respuesta adecuado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1347">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="168cc-1348">Consulte el servicio *nx_web_http_server_create()* para obtener más información sobre la rutina de devolución de llamada de solicitud del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-1348">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1349">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1349">Input Parameters</span></span>

- <span data-ttu-id="168cc-1350">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1350">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1351">**packet_pptr** Puntero de un puntero de paquete asignado para el mensaje.</span><span class="sxs-lookup"><span data-stu-id="168cc-1351">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="168cc-1352">**status_code** Indica el estado del recurso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1352">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="168cc-1353">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="168cc-1353">Examples:</span></span>
  - <span data-ttu-id="168cc-1354">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="168cc-1354">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="168cc-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="168cc-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="168cc-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="168cc-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="168cc-1357">**status_code_length** Longitud de cadena del código de estado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1357">**status_code_length** String length of status code</span></span>
- <span data-ttu-id="168cc-1358">**content_length** Tamaño del contenido en bytes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1358">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="168cc-1359">**content_type** Tipo de HTTP, por ejemplo, “texto/sin formato”.</span><span class="sxs-lookup"><span data-stu-id="168cc-1359">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="168cc-1360">**content_type_length** Longitud de cadena del tipo de contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1360">**content_type_length** String length of content type</span></span>
- <span data-ttu-id="168cc-1361">**additional_header** Puntero a texto de encabezado adicional.</span><span class="sxs-lookup"><span data-stu-id="168cc-1361">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="168cc-1362">**additional_header_length** Longitud del texto de encabezado adicional.</span><span class="sxs-lookup"><span data-stu-id="168cc-1362">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1363">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1363">Return Values</span></span>

- <span data-ttu-id="168cc-1364">**NX_SUCCESS** (0x00) Encabezado HTML creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1364">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="168cc-1365">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1365">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1366">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1366">Allowed From</span></span>

<span data-ttu-id="168cc-1367">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1368">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1368">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a><span data-ttu-id="168cc-1369">nx_web_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="168cc-1369">nx_web_http_server_callback_packet_send</span></span>

<span data-ttu-id="168cc-1370">Envía un paquete HTTP desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="168cc-1370">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1371">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1371">Prototype</span></span>

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="168cc-1372">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1372">Description</span></span>

<span data-ttu-id="168cc-1373">Este servicio envía una respuesta completa del servidor HTTP desde una devolución de llamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1373">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="168cc-1374">El servidor HTTP enviará el paquete con NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="168cc-1374">HTTP server will send the packet with the NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="168cc-1375">El encabezado y los datos HTTP deben anexarse al paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1375">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="168cc-1376">Si el estado devuelto indica un error, la aplicación HTTP debe liberar el paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1376">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="168cc-1377">La devolución de llamada debe devolver NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="168cc-1377">The callback should return NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="168cc-1378">Consulte *nx_web_http_server_callback_generate_response_header()* para ver un ejemplo más detallado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1378">See *nx_web_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1379">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1379">Input Parameters</span></span>

- <span data-ttu-id="168cc-1380">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1380">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="168cc-1381">**packet_ptr** Puntero al paquete que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1381">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1382">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1382">Return Values</span></span>

- <span data-ttu-id="168cc-1383">**NX_SUCCESS** (0x00) Paquete de servidor HTTP enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1383">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="168cc-1384">**NX_PTR_ERROR** (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1384">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1385">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1385">Allowed From</span></span>

<span data-ttu-id="168cc-1386">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1386">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1387">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1387">Example</span></span>

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a><span data-ttu-id="168cc-1388">nx_web_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="168cc-1388">nx_web_http_server_callback_response_send</span></span>

<span data-ttu-id="168cc-1389">Envía una respuesta desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="168cc-1389">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1390">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1390">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="168cc-1391">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1391">Description</span></span>

<span data-ttu-id="168cc-1392">Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1392">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="168cc-1393">Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST.</span><span class="sxs-lookup"><span data-stu-id="168cc-1393">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="168cc-1394">Tenga en cuenta que si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="168cc-1394">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="168cc-1395">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1395">This service is deprecated.</span></span> <span data-ttu-id="168cc-1396">Se recomienda a los desarrolladores que utilicen *nx_web_http_server_callback_response_send_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1396">Developers are encouraged to use *nx_web_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1397">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1397">Input Parameters</span></span>

- <span data-ttu-id="168cc-1398">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1398">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1399">**header** Puntero a la cadena de encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1399">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="168cc-1400">**information** Puntero a la cadena de información.</span><span class="sxs-lookup"><span data-stu-id="168cc-1400">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="168cc-1401">**additional_info** Puntero a la cadena de información adicional.</span><span class="sxs-lookup"><span data-stu-id="168cc-1401">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1402">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1402">Return Values</span></span>

- <span data-ttu-id="168cc-1403">**NX_SUCCESS** (0x00) Respuesta de servidor HTTP enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1403">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1404">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1404">Allowed From</span></span>

<span data-ttu-id="168cc-1405">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1405">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1406">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1406">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a><span data-ttu-id="168cc-1407">nx_web_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-1407">nx_web_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="168cc-1408">Envía una respuesta desde la función de devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="168cc-1408">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1409">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1409">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="168cc-1410">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1410">Description</span></span>

<span data-ttu-id="168cc-1411">Este servicio envía la información de respuesta suministrada desde la rutina de devolución de llamada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1411">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="168cc-1412">Normalmente se usa para enviar respuestas personalizadas asociadas a solicitudes GET/POST.</span><span class="sxs-lookup"><span data-stu-id="168cc-1412">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="168cc-1413">Tenga en cuenta que si se usa esta función, la rutina de devolución de llamada debe devolver el estado de NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="168cc-1413">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="168cc-1414">Las cadenas “header”, “information” y “additional_info” deben terminar en NULL y la longitud de cada cadena coincide con la longitud especificada en la lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1414">The strings of header, information and additional_info must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="168cc-1415">Este servicio reemplaza a *nx_web_http_server_callback_response_send*().</span><span class="sxs-lookup"><span data-stu-id="168cc-1415">This service replaces *nx_web_http_server_callback_response_send*().</span></span> <span data-ttu-id="168cc-1416">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-1416">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1417">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1417">Input Parameters</span></span>

- <span data-ttu-id="168cc-1418">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1419">**header** Puntero a la cadena de encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1419">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="168cc-1420">**header_length** Longitud de la cadena de encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1420">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="168cc-1421">**information** Puntero a la cadena de información.</span><span class="sxs-lookup"><span data-stu-id="168cc-1421">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="168cc-1422">**Information_length** Longitud de la cadena de información.</span><span class="sxs-lookup"><span data-stu-id="168cc-1422">**Information_length** Length of the information string.</span></span>
- <span data-ttu-id="168cc-1423">**additional_info** Puntero a la cadena de información adicional.</span><span class="sxs-lookup"><span data-stu-id="168cc-1423">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="168cc-1424">**additional_info_length** Longitud de la cadena de información adicional.</span><span class="sxs-lookup"><span data-stu-id="168cc-1424">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1425">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1425">Return Values</span></span>

- <span data-ttu-id="168cc-1426">**NX_SUCCESS** (0x00) Respuesta de servidor HTTP enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1426">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1427">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1427">Allowed From</span></span>

<span data-ttu-id="168cc-1428">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1428">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1429">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1429">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a><span data-ttu-id="168cc-1430">nx_web_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="168cc-1430">nx_web_http_server_content_get</span></span>

<span data-ttu-id="168cc-1431">Obtiene contenido de la solicitud</span><span class="sxs-lookup"><span data-stu-id="168cc-1431">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1432">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1432">Prototype</span></span>

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="168cc-1433">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1433">Description</span></span>

<span data-ttu-id="168cc-1434">Este servicio intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST o PUT.</span><span class="sxs-lookup"><span data-stu-id="168cc-1434">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="168cc-1435">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="168cc-1435">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1436">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1436">Input Parameters</span></span>

- <span data-ttu-id="168cc-1437">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1437">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1438">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1438">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="168cc-1439">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1439">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="168cc-1440">**byte_offset** Número de bytes que se van a desplazar en el área de contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1440">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="168cc-1441">**destination_ptr** Puntero al área de destino para el contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1441">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="168cc-1442">**destination_size** Número máximo de bytes disponibles en el área de destino.</span><span class="sxs-lookup"><span data-stu-id="168cc-1442">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="168cc-1443">**actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1443">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1444">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1444">Return Values</span></span>

- <span data-ttu-id="168cc-1445">**NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1445">**NX_SUCCESS** (0x00) Successful HTTP Server content Get</span></span>
- <span data-ttu-id="168cc-1446">**NX_WEB_HTTP_ERROR** (0x30000) Error interno del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="168cc-1447">**NX_WEB_HTTP_DATA_END** (0x30007) Fin de la solicitud de contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1447">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="168cc-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo de espera del servidor HTTP para obtener el siguiente paquete de contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="168cc-1449">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1449">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1450">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1450">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1451">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1451">Allowed From</span></span>

<span data-ttu-id="168cc-1452">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1452">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1453">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1453">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a><span data-ttu-id="168cc-1454">nx_web_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-1454">nx_web_http_server_content_get_extended</span></span>

<span data-ttu-id="168cc-1455">Obtiene contenido de la solicitud/admite la longitud del contenido de longitud cero</span><span class="sxs-lookup"><span data-stu-id="168cc-1455">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1456">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1456">Prototype</span></span>

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="168cc-1457">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1457">Description</span></span>

<span data-ttu-id="168cc-1458">Este servicio es casi idéntico a *nx_web_http_server_content_get()* ; intenta recuperar la cantidad especificada de contenido de la solicitud de cliente HTTP POST o PUT.</span><span class="sxs-lookup"><span data-stu-id="168cc-1458">This service is almost identical to *nx_web_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="168cc-1459">Sin embargo, administra las solicitudes con longitud de contenido de valor cero (“solicitud vacía”) como solicitud válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1459">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="168cc-1460">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="168cc-1460">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

<span data-ttu-id="168cc-1461">Este servicio reemplaza a *nx_web_http_server_content_get*().</span><span class="sxs-lookup"><span data-stu-id="168cc-1461">This service replaces *nx_web_http_server_content_get*().</span></span> <span data-ttu-id="168cc-1462">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-1462">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1463">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1463">Input Parameters</span></span>

- <span data-ttu-id="168cc-1464">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1464">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1465">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1465">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="168cc-1466">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1466">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="168cc-1467">**byte_offset** Número de bytes que se van a desplazar en el área de contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1467">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="168cc-1468">**destination_ptr** Puntero al área de destino para el contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1468">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="168cc-1469">**destination_size** Número máximo de bytes disponibles en el área de destino.</span><span class="sxs-lookup"><span data-stu-id="168cc-1469">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="168cc-1470">**actual_size** Puntero a la variable de destino que se establecerá en el tamaño real del contenido copiado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1470">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1471">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1471">Return Values</span></span>

- <span data-ttu-id="168cc-1472">**NX_SUCCESS** (0X00) Contenido del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1472">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="168cc-1473">**NX_WEB_HTTP_ERROR** (0x30000) Error interno del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="168cc-1474">**NX_WEB_HTTP_DATA_END** (0x30007) Fin de la solicitud de contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1474">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="168cc-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo de espera del servidor HTTP para obtener el siguiente paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="168cc-1476">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1477">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1477">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1478">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1478">Allowed From</span></span>

<span data-ttu-id="168cc-1479">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1480">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1480">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a><span data-ttu-id="168cc-1481">nx_web_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="168cc-1481">nx_web_http_server_content_length_get</span></span>

<span data-ttu-id="168cc-1482">Obtiene la longitud del contenido de la solicitud/admite la longitud del contenido de cero.</span><span class="sxs-lookup"><span data-stu-id="168cc-1482">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1483">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1483">Prototype</span></span>

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="168cc-1484">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1484">Description</span></span>

<span data-ttu-id="168cc-1485">Este servicio intenta recuperar la longitud del contenido HTTP en el paquete proporcionado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1485">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="168cc-1486">El valor devuelto indica el estado de finalización correcta y el valor de longitud real se devuelve en el puntero de entrada content_length.</span><span class="sxs-lookup"><span data-stu-id="168cc-1486">The return value indicates successful completion status and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="168cc-1487">Si no hay contenido HTTP/longitud de contenido = 0, esta rutina sigue devolviendo un estado de finalización correcta y el puntero de entrada content_length apunta a una longitud válida (cero).</span><span class="sxs-lookup"><span data-stu-id="168cc-1487">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="168cc-1488">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="168cc-1488">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1489">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1489">Input Parameters</span></span>

- <span data-ttu-id="168cc-1490">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1490">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="168cc-1491">Tenga en cuenta que este paquete no debe ser liberado por la devolución de llamada de notificación de solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1491">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="168cc-1492">**CONTENT_LENGTH** Puntero al valor recuperado del campo de longitud de contenido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1492">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1493">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1493">Return Values</span></span>

- <span data-ttu-id="168cc-1494">**NX_SUCCESS** (0X00) Longitud del contenido del servidor HTTP obtenida correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1494">**NX_SUCCESS** (0x00) Successful HTTP Server Content Length Get</span></span>
- <span data-ttu-id="168cc-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Formato de encabezado HTTP incorrecto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Improper HTTP header format</span></span>
- <span data-ttu-id="168cc-1496">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1496">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1497">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1497">Allowed From</span></span>

<span data-ttu-id="168cc-1498">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1498">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1499">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1499">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a><span data-ttu-id="168cc-1500">nx_web_http_server_create</span><span class="sxs-lookup"><span data-stu-id="168cc-1500">nx_web_http_server_create</span></span>

<span data-ttu-id="168cc-1501">Crea una instancia de servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-1501">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1502">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1502">Prototype</span></span>

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="168cc-1503">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1503">Description</span></span>

<span data-ttu-id="168cc-1504">Este servicio crea una instancia de servidor HTTP que se ejecuta en el contexto de su propio subproceso ThreadX.</span><span class="sxs-lookup"><span data-stu-id="168cc-1504">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="168cc-1505">Las rutinas de devolución de llamada de aplicación *authentication_check* y *request_notify* opcionales proporcionan al software de aplicación control sobre las operaciones básicas del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1505">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="168cc-1506">Este servicio se utiliza para crear servidores HTTP de texto no cifrado y servidores HTTPS protegidos por TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1506">This service is used to create both plaintext HTTP servers and TLS-secured HTTPS servers.</span></span> <span data-ttu-id="168cc-1507">Para habilitar HTTPS mediante TLS, consulte el servicio *nx_web_http_server_secure_configure()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1507">To enable HTTPS using TLS, see the service *nx_web_http_server_secure_configure()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1508">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1508">Input Parameters</span></span>

- <span data-ttu-id="168cc-1509">**http_server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1509">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1510">**http_server_name** Puntero al nombre del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1510">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="168cc-1511">**ip_ptr** Puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1511">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="168cc-1512">**server_port** Puerto de escucha de TCP para la instancia de servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-1512">**server_port** TCP listening port for server instance.</span></span>
- <span data-ttu-id="168cc-1513">**media_ptr** Puntero a la instancia de medios FileX creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1513">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="168cc-1514">**stack_ptr** Puntero al área de la pila de subprocesos del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1514">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="168cc-1515">**stack_size** Puntero al tamaño de la pila de subprocesos del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1515">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="168cc-1516">**authentication_check** Puntero de función a la rutina de comprobación de autenticación de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1516">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="168cc-1517">Si se especifica, se llama a esta rutina para cada solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1517">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="168cc-1518">Si este parámetro es NULL, no se realizará ninguna autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1518">If this parameter is NULL, no authentication will be performed.</span></span> <span data-ttu-id="168cc-1519">Este parámetro está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1519">This parameter is deprecated.</span></span> <span data-ttu-id="168cc-1520">Llame a *nx_web_http_server_authenticate_check_set*() en su lugar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1520">Call *nx_web_http_server_authenticate_check_set*() instead.</span></span>
- <span data-ttu-id="168cc-1521">**request_notify** Puntero de función a la rutina de notificación de solicitud de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1521">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="168cc-1522">Si se especifica, se llama a esta rutina antes de que se procese el servidor HTTP de la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1522">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="168cc-1523">Esto permite que se redirija el nombre del recurso o que los campos de un recurso se actualicen antes de completar la solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1523">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1524">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1524">Return Values</span></span>

- <span data-ttu-id="168cc-1525">**NX_SUCCESS**: (0x00) Servidor HTTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1525">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="168cc-1526">NX_PTR_ERROR (0x07) El puntero de servidor HTTP, dirección IP, medio, pila o grupo de paquetes no es válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1526">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="168cc-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) La carga de paquetes del grupo no es lo suficientemente grande como para contener una solicitud HTTP completa.</span><span class="sxs-lookup"><span data-stu-id="168cc-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1528">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1528">Allowed From</span></span>

<span data-ttu-id="168cc-1529">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1529">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1530">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1530">Example</span></span>

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a><span data-ttu-id="168cc-1531">nx_web_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="168cc-1531">nx_web_http_server_delete</span></span>

<span data-ttu-id="168cc-1532">Elimina una instancia de servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-1532">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1533">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1533">Prototype</span></span>

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="168cc-1534">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1534">Description</span></span>

<span data-ttu-id="168cc-1535">Este servicio elimina una instancia de cliente HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1535">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1536">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1536">Input Parameters</span></span>

- <span data-ttu-id="168cc-1537">**http_server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1537">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1538">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1538">Return Values</span></span>

- <span data-ttu-id="168cc-1539">**NX_SUCCESS**: (0x00) Servidor HTTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1539">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="168cc-1540">NX_PTR_ERROR (0x07) Puntero de servidor HTTP no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1540">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="168cc-1541">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1541">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1542">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1542">Allowed From</span></span>

<span data-ttu-id="168cc-1543">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1543">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1544">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1544">Example</span></span>

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a><span data-ttu-id="168cc-1545">nx_web_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="168cc-1545">nx_web_http_server_get_entity_content</span></span>

<span data-ttu-id="168cc-1546">Recupera la ubicación y la longitud de los datos de entidad</span><span class="sxs-lookup"><span data-stu-id="168cc-1546">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1547">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1547">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="168cc-1548">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1548">Description</span></span>

<span data-ttu-id="168cc-1549">Este servicio determina la ubicación del inicio de los datos dentro de la entidad actual de varias partes en los mensajes de cliente recibidos y la longitud de los datos que no incluyen la cadena de límite.</span><span class="sxs-lookup"><span data-stu-id="168cc-1549">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="168cc-1550">Internamente, el servidor HTTP actualiza sus propios desplazamientos para que se pueda volver a llamar a esta función en el mismo datagrama de cliente para mensajes con varias entidades.</span><span class="sxs-lookup"><span data-stu-id="168cc-1550">Internally, the HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="168cc-1551">El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1551">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="168cc-1552">Tenga en cuenta que NX_WEB_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1552">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="168cc-1553">Tenga en cuenta también que la aplicación no debe liberar el paquete al que apunta packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="168cc-1553">Also note that the application should not release the packet pointed to by packet_pptr.</span></span> <span data-ttu-id="168cc-1554">Esto lo realiza internamente el servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1554">This is done internally by the HTTP server.</span></span>

<span data-ttu-id="168cc-1555">Consulte *nx_web_http_server_get_entity_header()* para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="168cc-1555">See *nx_web_http_server_get_entity_header()* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1556">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1556">Input Parameters</span></span>

- <span data-ttu-id="168cc-1557">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1557">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="168cc-1558">**packet_pptr** Puntero a la ubicación del puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1558">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="168cc-1559">Tenga en cuenta que la aplicación no debe liberar este paquete</span><span class="sxs-lookup"><span data-stu-id="168cc-1559">Note that the application should not release this packet</span></span>
- <span data-ttu-id="168cc-1560">**available_offset** Puntero para desplazar los datos de entidad desde el puntero antepuesto de paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1560">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="168cc-1561">**available_length** Puntero a la longitud de los datos de entidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1561">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1562">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1562">Return Values</span></span>

- <span data-ttu-id="168cc-1563">**NX_SUCCESS** (0x00) Tamaño y ubicación del contenido de la entidad recuperados correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1563">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="168cc-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Contenido para los marcadores de varias partes internos del servidor HTTP ya encontrado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="168cc-1565">NX_WEB_HTTP_ERROR (0x30000) Error interno del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="168cc-1566">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1566">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1567">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1567">Allowed From</span></span>

<span data-ttu-id="168cc-1568">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1568">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1569">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1569">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a><span data-ttu-id="168cc-1570">nx_web_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="168cc-1570">nx_web_http_server_get_entity_header</span></span>

<span data-ttu-id="168cc-1571">Recupera el contenido del encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1571">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1572">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1572">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="168cc-1573">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1573">Description</span></span>

<span data-ttu-id="168cc-1574">Este servicio recupera el encabezado de entidad en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1574">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="168cc-1575">Internamente, el servidor HTTP actualiza sus propios punteros para localizar la siguiente entidad de varias partes en un datagrama de cliente con varios encabezados de entidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1575">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="168cc-1576">El puntero de paquete se actualiza al siguiente paquete en el que el mensaje de cliente es un datagrama de varios paquetes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1576">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="168cc-1577">Tenga en cuenta que NX_WEB_HTTP_MULTIPART_ENABLE debe estar habilitado para usar este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1577">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="168cc-1578">Tenga en cuenta también que la aplicación no debe liberar el paquete al que apunta packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="168cc-1578">Note also that the application should not release the packet pointed to by packet_pptr.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1579">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1579">Input Parameters</span></span>

- <span data-ttu-id="168cc-1580">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1580">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="168cc-1581">**packet_pptr** Puntero a la ubicación del puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1581">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="168cc-1582">Tenga en cuenta que la aplicación no debe liberar este paquete</span><span class="sxs-lookup"><span data-stu-id="168cc-1582">Note that the application should not release this packet</span></span>
- <span data-ttu-id="168cc-1583">**entity_header_buffer** Puntero a la ubicación donde se va a almacenar el encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1583">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="168cc-1584">**buffer_size** Tamaño del búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="168cc-1584">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1585">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1585">Return Values</span></span>

- <span data-ttu-id="168cc-1586">**NX_SUCCESS** (0x00) Encabezado de entidad recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1586">**NX_SUCCESS** (0x00) Successfully retrieved entity Header</span></span>
- <span data-ttu-id="168cc-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Campo de encabezado de identidad no encontrado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Entity header field not found</span></span>
- <span data-ttu-id="168cc-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo agotado para recibir el siguiente paquete para el mensaje de cliente con varios paquetes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired to receive next packet for multipacket client message</span></span>
- <span data-ttu-id="168cc-1589">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1589">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1590">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1590">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="168cc-1591">NX_WEB_HTTP_ERROR (0x30000) Error de cliente HTTP interno.</span><span class="sxs-lookup"><span data-stu-id="168cc-1591">NX_WEB_HTTP_ERROR (0x30000) Internal HTTP error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1592">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1592">Allowed From</span></span>

<span data-ttu-id="168cc-1593">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1593">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1594">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1594">Example</span></span>

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a><span data-ttu-id="168cc-1595">nx_web_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="168cc-1595">nx_web_http_server_gmt_callback_set</span></span>

<span data-ttu-id="168cc-1596">Establece la devolución de llamada para obtener la fecha y hora GMT.</span><span class="sxs-lookup"><span data-stu-id="168cc-1596">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1597">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1597">Prototype</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="168cc-1598">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1598">Description</span></span>

<span data-ttu-id="168cc-1599">Este servicio establece la devolución de llamada para obtener la fecha y hora GMT con un servidor HTTP creado previamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1599">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="168cc-1600">Este servicio se invoca con el servidor HTTP y crea un encabezado en las respuestas del servidor HTTP al cliente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1600">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1601">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1601">Input Parameters</span></span>

- <span data-ttu-id="168cc-1602">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1602">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="168cc-1603">**gmt_get** Puntero a la devolución de llamada GMT.</span><span class="sxs-lookup"><span data-stu-id="168cc-1603">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="168cc-1604">**date** Puntero a la fecha de recuperación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1604">**date** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1605">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1605">Return Values</span></span>

- <span data-ttu-id="168cc-1606">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1606">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="168cc-1607">NX_PTR_ERROR (0x07) Puntero de paquete o parámetro no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1607">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1608">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1608">Allowed From</span></span>

<span data-ttu-id="168cc-1609">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1609">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1610">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1610">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="168cc-1611">nx_web_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="168cc-1611">nx_web_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="168cc-1612">Establece la devolución de llamada para controlar la contraseña o el usuario no válidos</span><span class="sxs-lookup"><span data-stu-id="168cc-1612">Set the callback to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1613">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1613">Prototype</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="168cc-1614">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1614">Description</span></span>

<span data-ttu-id="168cc-1615">Este servicio establece la devolución de llamada invocada cuando se recibe un nombre de usuario y una contraseña no válidos en una solicitud GET, PUT o DELETE de cliente, ya sea mediante autenticación implícita o básica.</span><span class="sxs-lookup"><span data-stu-id="168cc-1615">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="168cc-1616">El servidor HTTP se debe crear previamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1616">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1617">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1617">Input Parameters</span></span>

- <span data-ttu-id="168cc-1618">**server_ptr** Puntero al servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1618">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="168cc-1619">**invalid_username_password_callback** Puntero a una devolución de llamada de aprobado/usuario no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1619">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="168cc-1620">**resource** Puntero al recurso especificado por el cliente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1620">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="168cc-1621">**client_address** Dirección de cliente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1621">**client_address** Client address</span></span>
- <span data-ttu-id="168cc-1622">**request_type** Indica el tipo de solicitud de cliente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1622">**request_type** Indicates client request type.</span></span> <span data-ttu-id="168cc-1623">Puede ser:</span><span class="sxs-lookup"><span data-stu-id="168cc-1623">May be:</span></span>
  - <span data-ttu-id="168cc-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="168cc-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span></span>
  - <span data-ttu-id="168cc-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="168cc-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span></span>
  - <span data-ttu-id="168cc-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="168cc-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1627">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1627">Return Values</span></span>

- <span data-ttu-id="168cc-1628">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1628">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="168cc-1629">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1629">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1630">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1630">Allowed From</span></span>

<span data-ttu-id="168cc-1631">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1631">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1632">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1632">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a><span data-ttu-id="168cc-1633">nx_web_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="168cc-1633">nx_web_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="168cc-1634">Establece asignaciones MIME adicionales para HTML</span><span class="sxs-lookup"><span data-stu-id="168cc-1634">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1635">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1635">Prototype</span></span>

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="168cc-1636">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1636">Description</span></span>

<span data-ttu-id="168cc-1637">Este servicio permite al desarrollador de aplicaciones HTTP agregar tipos MIME adicionales a partir de los tipos MIME predeterminados proporcionados por el servidor Web HTTP de NetX.</span><span class="sxs-lookup"><span data-stu-id="168cc-1637">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by the NetX Web HTTP Server.</span></span> <span data-ttu-id="168cc-1638">Consulte *nx_web_http_server_get_type()* para obtener una lista de tipos definidos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1638">See *nx_web_http_server_get_type()* for list of defined types.</span></span>

<span data-ttu-id="168cc-1639">Cuando se recibe una solicitud de cliente, por ejemplo, una solicitud GET, el servidor HTTP analiza el tipo de archivo solicitado del encabezado HTTP mediante el conjunto de asignaciones MIME adicional y, si no se encuentra ninguna coincidencia, busca una coincidencia en la asignación MIME predeterminada del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1639">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="168cc-1640">Si no se encuentra ninguna coincidencia, el tipo MIME tiene como valor predeterminado “texto/sin formato”.</span><span class="sxs-lookup"><span data-stu-id="168cc-1640">If no match is found, the MIME type defaults to "text/plain".</span></span>

<span data-ttu-id="168cc-1641">Si la función de notificación de solicitud se registra con el servidor HTTP, la devolución de llamada de solicitud de notificación puede llamar a *nx_web_http_server_type_get_extended()* para analizar el tipo de archivo.</span><span class="sxs-lookup"><span data-stu-id="168cc-1641">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_web_http_server_type_get_extended()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1642">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1642">Input Parameters</span></span>

- <span data-ttu-id="168cc-1643">**server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1643">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="168cc-1644">**mime_maps** Puntero a una matriz de asignaciones MIME.</span><span class="sxs-lookup"><span data-stu-id="168cc-1644">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="168cc-1645">**mime_map_num** Número de asignaciones MIME en la matriz.</span><span class="sxs-lookup"><span data-stu-id="168cc-1645">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1646">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1646">Return Values</span></span>

- <span data-ttu-id="168cc-1647">**NX_SUCCESS**: (0x00) Asignación MIME del servidor HTTP establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="168cc-1648">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1648">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1649">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1649">Allowed From</span></span>

<span data-ttu-id="168cc-1650">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1650">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1651">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1651">Example</span></span>

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a><span data-ttu-id="168cc-1652">nx_web_http_server_response_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="168cc-1652">nx_web_http_server_response_packet_allocate</span></span>

<span data-ttu-id="168cc-1653">Asigna un paquete HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="168cc-1653">Allocate an HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1654">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1654">Prototype</span></span>

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="168cc-1655">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1655">Description</span></span>

<span data-ttu-id="168cc-1656">Este servicio intenta asignar un paquete para el servidor HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="168cc-1656">This service attempts to allocates a packet for the HTTP(S) server.</span></span>

<span data-ttu-id="168cc-1657">Tenga en cuenta que si **se produce un error en** una API de servidor NetX o HTTP posterior que usa este paquete como entrada, como nx_packet_data_append o \*\*nx_web_http_server_callback_packet_send, la aplicación es responsable de liberar el paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1657">Note that if a subsequent NetX or HTTP Server API using this packet as input **fails**, such as nx_packet_data_append or \*\*nx_web_http_server_callback_packet_send, the application is responsible for releasing the packet.</span></span> **

### <a name="input-parameters"></a><span data-ttu-id="168cc-1658">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1658">Input Parameters</span></span>

- <span data-ttu-id="168cc-1659">**server_ptr** Puntero al bloque de control del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1659">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="168cc-1660">**packet_ptr** Puntero al paquete asignado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1660">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="168cc-1661">**wait_option** Define el tiempo de espera en tics si no hay paquetes disponibles en el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1661">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="168cc-1662">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="168cc-1662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="168cc-1663">**NX_NO_WAIT** (0X00000000) Si se selecciona NX_NO_WAIT, el subproceso que realiza la llamada se devuelve inmediatamente si no se puede cumplir la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1663">**NX_NO_WAIT** (0x00000000) Selecting NX_NO_WAIT causes the calling thread to return immediately if the request cannot be fulfilled.</span></span>
  - <span data-ttu-id="168cc-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor HTTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="168cc-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>
  - <span data-ttu-id="168cc-1665">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (0x1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1665">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1666">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1666">Return Values</span></span>

- <span data-ttu-id="168cc-1667">**NX_SUCCESS** (0x00) Asignación correcta de paquetes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1667">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="168cc-1668">**NX_NO_PACKET** (0X01) No hay ningún paquete disponible.</span><span class="sxs-lookup"><span data-stu-id="168cc-1668">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="168cc-1669">**NX_WAIT_ABORTED** (0x1A) Una llamada a *tx_thread_wait_abort* ha anulado la suspensión solicitada.</span><span class="sxs-lookup"><span data-stu-id="168cc-1669">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="168cc-1670">**NX_INVALID_PARAMETERS** (0x4D) El tamaño de paquete no admite el protocolo.</span><span class="sxs-lookup"><span data-stu-id="168cc-1670">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="168cc-1671">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1671">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1672">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1672">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1673">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1673">Allowed From</span></span>

<span data-ttu-id="168cc-1674">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1675">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1675">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a><span data-ttu-id="168cc-1676">nx_web_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="168cc-1676">nx_web_http_server_packet_content_find</span></span>

<span data-ttu-id="168cc-1677">Extrae la longitud del contenido y establece el puntero en el inicio de los datos</span><span class="sxs-lookup"><span data-stu-id="168cc-1677">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1678">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1678">Prototype</span></span>

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="168cc-1679">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1679">Description</span></span>

<span data-ttu-id="168cc-1680">Este servicio extrae la longitud del contenido del encabezado HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1680">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="168cc-1681">También actualiza el paquete proporcionado de la siguiente manera: el puntero antepuesto de paquete (inicio de la ubicación del búfer de paquetes en el que se va a escribir) se establece en el contenido HTTP (datos) que se acaba de pasar al encabezado HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1681">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="168cc-1682">Si no se encuentra el principio del contenido en el paquete actual, la función espera a que se reciba el siguiente paquete mediante la opción de espera NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="168cc-1682">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="168cc-1683">Tenga en cuenta que no se debe llamar a este método antes de llamar a *nx_web_http_server_get_entity_header()* porque modifica el puntero antepuesto de paquete más allá del encabezado de entidad.</span><span class="sxs-lookup"><span data-stu-id="168cc-1683">Note this should not be called before calling *nx_web_http_server_get_entity_header()* because it modifies the packet prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1684">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1684">Input Parameters</span></span>

- <span data-ttu-id="168cc-1685">**server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1685">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="168cc-1686">**packet_ptr** Puntero al puntero de paquete para devolver el paquete con el puntero antepuesto actualizado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1686">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="168cc-1687">**CONTENT_LENGTH** Puntero al valor content_length extraído.</span><span class="sxs-lookup"><span data-stu-id="168cc-1687">**content_length** Pointer to extracted content_length</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1688">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1688">Return Values</span></span>

- <span data-ttu-id="168cc-1689">**NX_SUCCESS** (0x00) Se encontró la longitud del contenido HTTP y el paquete se actualizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1689">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="168cc-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo agotado esperando al siguiente paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="168cc-1691">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1691">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1692">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1692">Allowed From</span></span>

<span data-ttu-id="168cc-1693">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1693">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1694">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1694">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a><span data-ttu-id="168cc-1695">nx_web_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="168cc-1695">nx_web_http_server_packet_get</span></span>

<span data-ttu-id="168cc-1696">Recibe el siguiente paquete HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-1696">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1697">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1697">Prototype</span></span>

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="168cc-1698">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1698">Description</span></span>

<span data-ttu-id="168cc-1699">Este servicio devuelve el siguiente paquete recibido en el socket de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1699">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="168cc-1700">La opción de espera para recibir un paquete es NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="168cc-1700">The wait option to receive a packet is NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="168cc-1701">Tenga en cuenta que si se ejecuta correctamente, la aplicación es responsable de liberar el paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1701">Note that if successful the application is responsible for releasing the packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1702">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1702">Input Parameters</span></span>

- <span data-ttu-id="168cc-1703">**server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1703">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="168cc-1704">**packet_ptr** Puntero al paquete recibido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1704">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1705">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1705">Return Values</span></span>

- <span data-ttu-id="168cc-1706">**NX_SUCCESS** (0x00) Siguiente paquete HTTP recibido correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1706">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="168cc-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Tiempo agotado esperando al siguiente paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="168cc-1708">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1708">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1709">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1709">Allowed From</span></span>

<span data-ttu-id="168cc-1710">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1710">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1711">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1711">Example</span></span>

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a><span data-ttu-id="168cc-1712">nx_web_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="168cc-1712">nx_web_http_server_param_get</span></span>

<span data-ttu-id="168cc-1713">Obtiene el parámetro de la solicitud</span><span class="sxs-lookup"><span data-stu-id="168cc-1713">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1714">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1714">Prototype</span></span>

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="168cc-1715">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1715">Description</span></span>

<span data-ttu-id="168cc-1716">Este servicio intenta recuperar el parámetro de dirección URL HTTP especificado en el paquete de solicitud proporcionado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1716">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="168cc-1717">Si el parámetro HTTP solicitado no está presente, esta rutina devuelve un estado de NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="168cc-1717">If the requested HTTP parameter is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="168cc-1718">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="168cc-1718">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1719">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1719">Input Parameters</span></span>

- <span data-ttu-id="168cc-1720">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1720">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="168cc-1721">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1721">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="168cc-1722">**param_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de parámetros.</span><span class="sxs-lookup"><span data-stu-id="168cc-1722">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="168cc-1723">**param_ptr** Área de destino para copiar el parámetro.</span><span class="sxs-lookup"><span data-stu-id="168cc-1723">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="168cc-1724">**param_size** Devuelve la longitud total de los datos del parámetro (en bytes).</span><span class="sxs-lookup"><span data-stu-id="168cc-1724">**param_size** Return the total parameter data length (in bytes).</span></span>
- <span data-ttu-id="168cc-1725">**max_param_size** Tamaño máximo del área de destino del parámetro.</span><span class="sxs-lookup"><span data-stu-id="168cc-1725">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1726">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1726">Return Values</span></span>

- <span data-ttu-id="168cc-1727">**NX_SUCCESS** (0X00) Parámetro del servidor HTTP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1727">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="168cc-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) No se encontró el parámetro especificado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified parameter not found</span></span>
- <span data-ttu-id="168cc-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Parámetro de solicitud no terminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated</span></span>
- <span data-ttu-id="168cc-1730">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1730">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1731">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1732">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1732">Allowed From</span></span>

<span data-ttu-id="168cc-1733">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1734">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1734">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a><span data-ttu-id="168cc-1735">nx_web_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="168cc-1735">nx_web_http_server_query_get</span></span>

<span data-ttu-id="168cc-1736">Obtiene la consulta de la solicitud</span><span class="sxs-lookup"><span data-stu-id="168cc-1736">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1737">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1737">Prototype</span></span>

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="168cc-1738">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1738">Description</span></span>

<span data-ttu-id="168cc-1739">Este servicio intenta recuperar la consulta de dirección URL HTTP especificada en el paquete de solicitud proporcionado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1739">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="168cc-1740">Si la consulta HTTP solicitada no está presente, esta rutina devuelve un estado de NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="168cc-1740">If the requested HTTP query is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="168cc-1741">Debe llamarse desde la devolución de llamada de notificación de solicitud de la aplicación especificada durante la creación del servidor HTTP (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="168cc-1741">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1742">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1742">Input Parameters</span></span>

- <span data-ttu-id="168cc-1743">**packet_ptr** Puntero al paquete de solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1743">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="168cc-1744">Tenga en cuenta que la aplicación no debe liberar este paquete.</span><span class="sxs-lookup"><span data-stu-id="168cc-1744">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="168cc-1745">**query_number** Número lógico del parámetro que comienza en cero, de izquierda a derecha en la lista de consultas.</span><span class="sxs-lookup"><span data-stu-id="168cc-1745">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="168cc-1746">**query_ptr** Área de destino en la que se va a copiar la consulta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1746">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="168cc-1747">**query_size** Devuelve el tamaño de los datos de consulta (en bytes).</span><span class="sxs-lookup"><span data-stu-id="168cc-1747">**query_size** Return query data size (in bytes).</span></span>
- <span data-ttu-id="168cc-1748">**max_query_size** Tamaño máximo del destino de la consulta.</span><span class="sxs-lookup"><span data-stu-id="168cc-1748">**max_query_size** Maximum size of the query destination</span></span>

<span data-ttu-id="168cc-1749">zona.</span><span class="sxs-lookup"><span data-stu-id="168cc-1749">area.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1750">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1750">Return Values</span></span>

- <span data-ttu-id="168cc-1751">**NX_SUCCESS**: (0x00) Consulta del servidor HTTP obtenida correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1751">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="168cc-1752">**NX_WEB_HTTP_FAILED** (0x30002) Tamaño de consulta demasiado pequeño.</span><span class="sxs-lookup"><span data-stu-id="168cc-1752">**NX_WEB_HTTP_FAILED** (0x30002) Query size too small.</span></span>
- <span data-ttu-id="168cc-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) No se encontró la consulta especificada.</span><span class="sxs-lookup"><span data-stu-id="168cc-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified query not found</span></span>
- <span data-ttu-id="168cc-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0X30013) No hay ninguna consulta en la solicitud de cliente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) No query in Client request</span></span>
- <span data-ttu-id="168cc-1755">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1755">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1756">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1756">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1757">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1757">Allowed From</span></span>

<span data-ttu-id="168cc-1758">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1758">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1759">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1759">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a><span data-ttu-id="168cc-1760">nx_web_http_server_response_chunked_set</span><span class="sxs-lookup"><span data-stu-id="168cc-1760">nx_web_http_server_response_chunked_set</span></span>

<span data-ttu-id="168cc-1761">Establece una transferencia fragmentada para la respuesta HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="168cc-1761">Set chunked transfer for HTTP(S) response</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1762">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1762">Prototype</span></span>

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="168cc-1763">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1763">Description</span></span>

<span data-ttu-id="168cc-1764">Este servicio utiliza codificación de transferencia fragmentada para enviar un paquete de datos de respuesta HTTP(S) personalizado creado con *nx_web_http_server_response_packet_allocate*() al cliente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1764">This service uses chunked transfer coding to send a custom HTTP(S) response data packet created with *nx_web_http_server_response_packet_allocate*() to the client.</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-1765">Si la aplicación utiliza codificación de transferencia fragmentada para enviar un paquete de datos de respuesta, debe llamar a este servicio después de llamar a *nx_web_http_client_response_packet_allocate*() y antes de llamar a *nx_web_http_server_callback_packet_send*().</span><span class="sxs-lookup"><span data-stu-id="168cc-1765">If the application uses chunked transfer coding to send a response data packet, it must call this service after calling *nx_web_http_server_response_packet_allocate*(), and before calling *nx_web_http_server_callback_packet_send*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1766">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1766">Input Parameters</span></span>

- <span data-ttu-id="168cc-1767">**client_ptr** Puntero al bloque de control del cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1767">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="168cc-1768">**chunk_size** Tamaño de los datos de fragmentos en octetos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1768">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="168cc-1769">**packet_ptr** El puntero de paquete de datos de solicitud HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="168cc-1769">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1770">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1770">Return Values</span></span>

- <span data-ttu-id="168cc-1771">**NX_SUCCESS** (0x00) Fragmento establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1771">**NX_SUCCESS** (0x00) Successful set chunked.</span></span>
- <span data-ttu-id="168cc-1772">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1772">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1773">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1773">Allowed From</span></span>

<span data-ttu-id="168cc-1774">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1774">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1775">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1775">Example</span></span>

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a><span data-ttu-id="168cc-1776">nx_web_http_server_secure_configure</span><span class="sxs-lookup"><span data-stu-id="168cc-1776">nx_web_http_server_secure_configure</span></span>

<span data-ttu-id="168cc-1777">Configura un servidor HTTP para usar TLS para HTTPS seguro</span><span class="sxs-lookup"><span data-stu-id="168cc-1777">Configure an HTTP Server to use TLS for secure HTTPS</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1778">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1778">Prototype</span></span>

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a><span data-ttu-id="168cc-1779">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1779">Description</span></span>

<span data-ttu-id="168cc-1780">Este servicio configura una instancia de servidor Web HTTP de NetX creada previamente para usar TLS en las comunicaciones HTTPS seguras.</span><span class="sxs-lookup"><span data-stu-id="168cc-1780">This service configures a previously created NetX Web HTTP server instance to use TLS for secure HTTPS communications.</span></span> <span data-ttu-id="168cc-1781">Los parámetros se usan para configurar todas las sesiones TLS posibles con un estado idéntico, de modo que cada cliente HTTPS entrante experimente un comportamiento coherente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1781">The parameters are used to configure all the possible TLS sessions with identical state so that each incoming HTTPS Client experiences consistent behavior.</span></span> <span data-ttu-id="168cc-1782">El número de sesiones TLS se controla mediante la macro NX_WEB_HTTP_SESSION_MAX.</span><span class="sxs-lookup"><span data-stu-id="168cc-1782">The number of TLS sessions is controlled using the macro NX_WEB_HTTP_SESSION_MAX.</span></span>

<span data-ttu-id="168cc-1783">La tabla de rutinas criptográficas (tabla de conjuntos de cifrado) se comparte entre todas las sesiones TLS, ya que solo contiene punteros de función.</span><span class="sxs-lookup"><span data-stu-id="168cc-1783">The cryptographic routine table (ciphersuite table) is shared between all TLS sessions as it just contains function pointers.</span></span>

<span data-ttu-id="168cc-1784">Los metadatos y los búferes de reensamblado de paquetes se dividen equitativamente entre todas las sesiones TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1784">The metadata and packet reassembly buffers are each divided equally between all TLS sessions.</span></span> <span data-ttu-id="168cc-1785">Si el tamaño del búfer no es divisible por el número de sesiones, el resto no se usará.</span><span class="sxs-lookup"><span data-stu-id="168cc-1785">If the buffer size is not evenly divisible by the number of sessions the remainder will be unused.</span></span>

<span data-ttu-id="168cc-1786">Todas las sesiones usan el certificado de identidad que se ha pasado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1786">The passed-in identity certificate is used by all sessions.</span></span> <span data-ttu-id="168cc-1787">Durante la operación TLS, el certificado de identidad de servidor solo se lee para que no se necesiten copias para cada sesión.</span><span class="sxs-lookup"><span data-stu-id="168cc-1787">During TLS operation the server identity certificate is only read from so copies are not needed for each session.</span></span>

<span data-ttu-id="168cc-1788">Los certificados de confianza se agregan a cada sesión de TLS en el servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1788">The trusted certificates are added to each TLS session in the HTTPS Server.</span></span> <span data-ttu-id="168cc-1789">Se usan para la autenticación de certificados de cliente que se habilita automáticamente cuando se proporciona un espacio de certificados remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1789">These are used for Client certificate authentication which is automatically enabled when remote certificate space is provided.</span></span>

<span data-ttu-id="168cc-1790">La matriz de certificados y el búfer remotos se comparten de forma predeterminada entre todas las sesiones de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1790">The remote certificate array and buffer is shared by default between all TLS sessions.</span></span> <span data-ttu-id="168cc-1791">Los certificados remotos se utilizan para la autenticación de certificados de cliente que se habilita automáticamente cuando el número de certificados remotos es distinto de cero.</span><span class="sxs-lookup"><span data-stu-id="168cc-1791">The remote certificates are used for Client certificate authentication which is automatically enabled when the remote certificate count is nonzero.</span></span> <span data-ttu-id="168cc-1792">Debido al uso compartido del búfer, algunas sesiones pueden bloquearse durante la validación del certificado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1792">Due to the buffer being shared some sessions may block during certificate validation.</span></span>

<span data-ttu-id="168cc-1793">Para deshabilitar la autenticación de certificados de cliente, pase NX_NULL al parámetro remote_certificates y un valor de 0 para el parámetro remote_certs_num.</span><span class="sxs-lookup"><span data-stu-id="168cc-1793">To disable client certificate authentication, pass NX_NULL for the remote_certificates parameter and a value of 0 for the remote_certs_num parameter.</span></span>

<span data-ttu-id="168cc-1794">Los valores devueltos incluirán cualquier código de error de TLS que resulte de problemas en la configuración de las sesiones de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1794">Return values will include any TLS error codes resulting from issues in the configuration of the TLS sessions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1795">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1795">Input Parameters</span></span>

- <span data-ttu-id="168cc-1796">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1796">**http_server_ptr** Pointer to HTTP Server instance.</span></span>
- <span data-ttu-id="168cc-1797">**crypto_table** Puntero a la tabla de conjuntos de cifrado de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1797">**crypto_table** Pointer to TLS ciphersuite table.</span></span>
- <span data-ttu-id="168cc-1798">**metadata_buffer** Puntero al búfer de metadatos criptográficos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1798">**metadata_buffer** Pointer to cryptographic metadata buffer.</span></span>
- <span data-ttu-id="168cc-1799">**metadata_size** Tamaño del búfer de metadatos criptográficos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1799">**metadata_size** Size of cryptographic metadata buffer.</span></span>
- <span data-ttu-id="168cc-1800">**packet_buffer** Búfer del reensamblado de paquetes TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1800">**packet_buffer** TLS packet reassembly buffer.</span></span>
- <span data-ttu-id="168cc-1801">**packet_buffer** Tamaño del búfer de paquetes TLS: debe ser igual a (<tamaño de búfer de TLS deseado\* NX_WEB_HTTP_SESSION_MAX).</span><span class="sxs-lookup"><span data-stu-id="168cc-1801">**packet_buffer** Size of TLS packet buffer – should be equal to (<desired TLS buffer size\* NX_WEB_HTTP_SESSION_MAX).</span></span>
- <span data-ttu-id="168cc-1802">**identity_certificate** Certificado de identidad del servidor TLS: se usará para todas las sesiones HTTPS del servidor.</span><span class="sxs-lookup"><span data-stu-id="168cc-1802">**identity_certificate** TLS server identity certificate – will be used for all HTTPS server sessions.</span></span>
- <span data-ttu-id="168cc-1803">**trusted_certificates** Puntero a la matriz de objetos NX_SECURE_X509_CERT, que se usa para validar los certificados de cliente entrantes si se habilita la autenticación de certificados de cliente pasando un valor distinto de cero para el parámetro *remote_certs_num*.</span><span class="sxs-lookup"><span data-stu-id="168cc-1803">**trusted_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used to validate incoming client certificates if client certificate authentication is enabled by passing a non-zero value for the *remote_certs_num* parameter.</span></span>
- <span data-ttu-id="168cc-1804">**trusted_certs_num** Número de certificados de confianza en la matriz de *trusted_certificates*.</span><span class="sxs-lookup"><span data-stu-id="168cc-1804">**trusted_certs_num** Number of trusted certificates in the *trusted_certificates* array.</span></span>
- <span data-ttu-id="168cc-1805">**remote_certificates** Puntero a la matriz de objetos NX_SECURE_X509_CERT, que se usa para los certificados de cliente entrantes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1805">**remote_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used for incoming client certificates.</span></span>
- <span data-ttu-id="168cc-1806">**remote_certs_num** Número de certificados remotos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1806">**remote_certs_num** Number of remote certificates.</span></span> <span data-ttu-id="168cc-1807">Debe ser el número máximo de certificados esperados de los clientes.</span><span class="sxs-lookup"><span data-stu-id="168cc-1807">Should be the maximum number of expected certificates from clients.</span></span> <span data-ttu-id="168cc-1808">La autenticación de certificados de cliente se habilita automáticamente cuando no es cero.</span><span class="sxs-lookup"><span data-stu-id="168cc-1808">Client certificate authentication is enabled automatically when this is non-zero.</span></span>
- <span data-ttu-id="168cc-1809">**remote_certificate_buffer** Búfer que contiene los certificados remotos entrantes de los clientes si está habilitada la autenticación de certificados de cliente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1809">**remote_certificate_buffer** Buffer to contain incoming remote certificates from clients if client certificate authentication is enabled.</span></span> <span data-ttu-id="168cc-1810">remote_cert_buffer_size Tamaño del búfer de certificados remotos.</span><span class="sxs-lookup"><span data-stu-id="168cc-1810">remote_cert_buffer_size Size of remote certificates buffer.</span></span> <span data-ttu-id="168cc-1811">Debe ser igual a (<tamaño máximo de certificado esperado \* remote_certs_num).</span><span class="sxs-lookup"><span data-stu-id="168cc-1811">Should be equal to (<maximum expected certificate size \* remote_certs_num).</span></span>


### <a name="return-values"></a><span data-ttu-id="168cc-1812">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1812">Return Values</span></span>

- <span data-ttu-id="168cc-1813">**NX_SUCCESS** (0x00) La sesión de TLS se ha inicializado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1813">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="168cc-1814">**NX_NOT_CONNECTED** (0X38) El socket TCP subyacente ya no está conectado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1814">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="168cc-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) Un tipo de mensaje TLS/DTLS recibido es incorrecto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="168cc-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) No se admite el cifrado proporcionado por el host remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="168cc-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Error al procesar el mensaje durante el protocolo de enlace de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="168cc-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Un mensaje entrante no pudo realizar una comprobación hash de MAC.</span><span class="sxs-lookup"><span data-stu-id="168cc-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a  hash MAC check.</span></span>
- <span data-ttu-id="168cc-1819">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Error al enviar un socket TCP subyacente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="168cc-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Un mensaje entrante tenía un campo de longitud no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="168cc-1821">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0X10B) Un mensaje ChangeCipherSpec entrante era incorrecto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="168cc-1822">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Un certificado TLS entrante no se puede usar para identificar el servidor DTLS remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="168cc-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) No se admite el cifrado de clave pública proporcionado por el host remoto.</span><span class="sxs-lookup"><span data-stu-id="168cc-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="168cc-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E) El host remoto ha indicado que no hay conjuntos de aplicaciones de cifrado admitidos por la pila del servicio DTLS de NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="168cc-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="168cc-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) Un mensaje DTLS recibido tenía una versión DTLS desconocida en el encabezado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="168cc-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) Un mensaje DTLS recibido tenía una versión de DTLS conocida pero no admitida en su encabezado.</span><span class="sxs-lookup"><span data-stu-id="168cc-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="168cc-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Error en una asignación interna de paquetes TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="168cc-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) El host remoto proporcionó un certificado no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="168cc-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) El host remoto envió una alerta que indica un error y finaliza la sesión de TLS.</span><span class="sxs-lookup"><span data-stu-id="168cc-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="168cc-1830">**NX_PTR_ERROR** (0x07) Se ha intentado usar un puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="168cc-1830">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1831">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1831">Allowed From</span></span>

<span data-ttu-id="168cc-1832">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1832">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1833">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1833">Example</span></span>

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a><span data-ttu-id="168cc-1834">nx_web_http_server_start</span><span class="sxs-lookup"><span data-stu-id="168cc-1834">nx_web_http_server_start</span></span>

<span data-ttu-id="168cc-1835">Inicia el servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-1835">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1836">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1836">Prototype</span></span>

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="168cc-1837">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1837">Description</span></span>

<span data-ttu-id="168cc-1838">Este servicio inicia una instancia de servidor HTTP o HTTPS creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1838">This service starts a previously created HTTP or HTTPS Server instance.</span></span>

<span data-ttu-id="168cc-1839">Los servidores HTTPS comparten la misma API que los HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1839">HTTPS servers share the same API as HTTP.</span></span> <span data-ttu-id="168cc-1840">Para habilitar HTTPS mediante TLS, consulte el servicio *nx_web_http_server_secure_configure()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1840">To enable HTTPS using TLS on an HTTP server, see the service *nx_web_http_server_secure_configure().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1841">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1841">Input Parameters</span></span>

- <span data-ttu-id="168cc-1842">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1842">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1843">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1843">Return Values</span></span>

- <span data-ttu-id="168cc-1844">**NX_SUCCESS**: (0x00) Servidor HTTP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1844">**NX_SUCCESS** (0x00) Successful HTTP Server Start</span></span>
- <span data-ttu-id="168cc-1845">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1845">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1846">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1846">Allowed From</span></span>

<span data-ttu-id="168cc-1847">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1847">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1848">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1848">Example</span></span>

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a><span data-ttu-id="168cc-1849">nx_web_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="168cc-1849">nx_web_http_server_stop</span></span>

<span data-ttu-id="168cc-1850">Detiene el servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="168cc-1850">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1851">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1851">Prototype</span></span>

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="168cc-1852">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1852">Description</span></span>

<span data-ttu-id="168cc-1853">Este servicio detiene la instancia de servidor HTTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1853">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="168cc-1854">Se debe llamar a esta rutina antes de eliminar una instancia del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1854">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1855">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1855">Input Parameters</span></span>

- <span data-ttu-id="168cc-1856">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1856">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1857">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1857">Return Values</span></span>

- <span data-ttu-id="168cc-1858">**NX_SUCCESS**: (0x00) Servidor HTTP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1858">**NX_SUCCESS** (0x00) Successful HTTP Server Stop</span></span>
- <span data-ttu-id="168cc-1859">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1859">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1860">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="168cc-1860">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1861">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1861">Allowed From</span></span>

<span data-ttu-id="168cc-1862">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="168cc-1862">Threads</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1863">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1863">Example</span></span>

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a><span data-ttu-id="168cc-1864">nx_web_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="168cc-1864">nx_web_http_server_type_get</span></span>

<span data-ttu-id="168cc-1865">Extrae el tipo de archivo de la solicitud HTTP del cliente</span><span class="sxs-lookup"><span data-stu-id="168cc-1865">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1866">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1866">Prototype</span></span>

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="168cc-1867">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1867">Description</span></span>

> [!NOTE]
> <span data-ttu-id="168cc-1868">Este servicio está en desuso.</span><span class="sxs-lookup"><span data-stu-id="168cc-1868">This service is deprecated.</span></span> <span data-ttu-id="168cc-1869">Se recomienda a los usuarios que usen el servicio *nx_web_http_server_type_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="168cc-1869">Users are encouraged to use the service *nx_web_http_server_type_get_extended()*.</span></span>

<span data-ttu-id="168cc-1870">Este servicio extrae el tipo de solicitud HTTP en el búfer *http_type_string* y su longitud en *string_size* desde el *nombre* del búfer de entrada, normalmente la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="168cc-1870">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="168cc-1871">Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo “texto/sin formato”.</span><span class="sxs-lookup"><span data-stu-id="168cc-1871">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="168cc-1872">En caso contrario, compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias.</span><span class="sxs-lookup"><span data-stu-id="168cc-1872">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="168cc-1873">Los mapas MIME predeterminados del servidor Web HTTP de NetX son:</span><span class="sxs-lookup"><span data-stu-id="168cc-1873">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="168cc-1874">texto html/html</span><span class="sxs-lookup"><span data-stu-id="168cc-1874">html text/html</span></span>
- <span data-ttu-id="168cc-1875">texto htm/html</span><span class="sxs-lookup"><span data-stu-id="168cc-1875">htm text/html</span></span>
- <span data-ttu-id="168cc-1876">texto txt/plain</span><span class="sxs-lookup"><span data-stu-id="168cc-1876">txt text/plain</span></span>
- <span data-ttu-id="168cc-1877">imagen gif/gif</span><span class="sxs-lookup"><span data-stu-id="168cc-1877">gif image/gif</span></span>
- <span data-ttu-id="168cc-1878">imagen jpg/jpeg</span><span class="sxs-lookup"><span data-stu-id="168cc-1878">jpg image/jpeg</span></span>
- <span data-ttu-id="168cc-1879">imagen ico/x-icon</span><span class="sxs-lookup"><span data-stu-id="168cc-1879">ico image/x-icon</span></span>

<span data-ttu-id="168cc-1880">Si se proporciona, también buscará un conjunto definido por el usuario de asignaciones MIME adicionales.</span><span class="sxs-lookup"><span data-stu-id="168cc-1880">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="168cc-1881">Consulte *nx_web_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="168cc-1881">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1882">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1882">Input Parameters</span></span>

- <span data-ttu-id="168cc-1883">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1883">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="168cc-1884">**name** Puntero al búfer para buscar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1884">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="168cc-1885">**http_type_string** Puntero a la cadena de tipo HTML extraída.</span><span class="sxs-lookup"><span data-stu-id="168cc-1885">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="168cc-1886">**string_size** Puntero para devolver la longitud de cadena de tipo HTML extraída.</span><span class="sxs-lookup"><span data-stu-id="168cc-1886">**string_size** Pointer to return extracted HTML type string length.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1887">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1887">Return Values</span></span>

- <span data-ttu-id="168cc-1888">**NX_SUCCESS** (0x00) Tipo extraído correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1888">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="168cc-1889">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1889">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Se devuelve el valor predeterminado “texto/sin formato”.</span><span class="sxs-lookup"><span data-stu-id="168cc-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1891">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1891">Allowed From</span></span>

<span data-ttu-id="168cc-1892">Application</span><span class="sxs-lookup"><span data-stu-id="168cc-1892">Application</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1893">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1893">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a><span data-ttu-id="168cc-1894">nx_web_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="168cc-1894">nx_web_http_server_type_get_extended</span></span>

<span data-ttu-id="168cc-1895">Extrae el tipo de archivo de la solicitud HTTP del cliente</span><span class="sxs-lookup"><span data-stu-id="168cc-1895">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1896">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1896">Prototype</span></span>

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="168cc-1897">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1897">Description</span></span>

<span data-ttu-id="168cc-1898">Este servicio extrae el tipo de solicitud HTTP en el búfer *http_type_string* y su longitud en *string_size* desde el *nombre* del búfer de entrada, normalmente la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="168cc-1898">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="168cc-1899">Si no se encuentra ninguna asignación MIME, se toma como valor predeterminado el tipo “texto/sin formato”.</span><span class="sxs-lookup"><span data-stu-id="168cc-1899">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="168cc-1900">En caso contrario, compara el tipo extraído con las asignaciones MIME predeterminadas del servidor HTTP para buscar coincidencias.</span><span class="sxs-lookup"><span data-stu-id="168cc-1900">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="168cc-1901">Los mapas MIME predeterminados del servidor Web HTTP de NetX son:</span><span class="sxs-lookup"><span data-stu-id="168cc-1901">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="168cc-1902">texto html/html</span><span class="sxs-lookup"><span data-stu-id="168cc-1902">html text/html</span></span>
- <span data-ttu-id="168cc-1903">texto htm/html</span><span class="sxs-lookup"><span data-stu-id="168cc-1903">htm text/html</span></span>
- <span data-ttu-id="168cc-1904">texto txt/plain</span><span class="sxs-lookup"><span data-stu-id="168cc-1904">txt text/plain</span></span>
- <span data-ttu-id="168cc-1905">imagen gif/gif</span><span class="sxs-lookup"><span data-stu-id="168cc-1905">gif image/gif</span></span>
- <span data-ttu-id="168cc-1906">imagen jpg/jpeg</span><span class="sxs-lookup"><span data-stu-id="168cc-1906">jpg image/jpeg</span></span>
- <span data-ttu-id="168cc-1907">imagen ico/x-icon</span><span class="sxs-lookup"><span data-stu-id="168cc-1907">ico image/x-icon</span></span>

<span data-ttu-id="168cc-1908">Si se proporciona, también buscará un conjunto definido por el usuario de asignaciones MIME adicionales.</span><span class="sxs-lookup"><span data-stu-id="168cc-1908">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="168cc-1909">Consulte *nx_web_http_server_mime_maps_addtional_set()* para obtener más detalles sobre las asignaciones definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="168cc-1909">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="168cc-1910">Este servicio reemplaza a *nx_web_http_server_type_get*().</span><span class="sxs-lookup"><span data-stu-id="168cc-1910">This service replaces *nx_web_http_server_type_get*().</span></span> <span data-ttu-id="168cc-1911">Esta versión requiere que los autores de llamada proporcionen información de longitud a la función.</span><span class="sxs-lookup"><span data-stu-id="168cc-1911">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1912">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1912">Input Parameters</span></span>

- <span data-ttu-id="168cc-1913">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1913">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="168cc-1914">**name** Puntero al búfer para buscar.</span><span class="sxs-lookup"><span data-stu-id="168cc-1914">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="168cc-1915">**name_length** Longitud del nombre.</span><span class="sxs-lookup"><span data-stu-id="168cc-1915">**name_length** Length of name</span></span>
- <span data-ttu-id="168cc-1916">**http_type_string** Puntero a la cadena de tipo HTML extraída.</span><span class="sxs-lookup"><span data-stu-id="168cc-1916">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="168cc-1917">**http_type_string_max_size** Tamaño del búfer de http_type_string.</span><span class="sxs-lookup"><span data-stu-id="168cc-1917">**http_type_string_max_size** Size of the http_type_string buffer size</span></span>
- <span data-ttu-id="168cc-1918">**string_size** Puntero para devolver la longitud de cadena de tipo HTML</span><span class="sxs-lookup"><span data-stu-id="168cc-1918">**string_size** Pointer to return extracted HTML type string</span></span>

<span data-ttu-id="168cc-1919">extraída.</span><span class="sxs-lookup"><span data-stu-id="168cc-1919">length.</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1920">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1920">Return Values</span></span>

- <span data-ttu-id="168cc-1921">**NX_SUCCESS** (0x00) Tipo extraído correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1921">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="168cc-1922">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1922">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Se devuelve el valor predeterminado “texto/sin formato”.</span><span class="sxs-lookup"><span data-stu-id="168cc-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1924">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1924">Allowed From</span></span>

<span data-ttu-id="168cc-1925">Application</span><span class="sxs-lookup"><span data-stu-id="168cc-1925">Application</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1926">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1926">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="168cc-1927">nx_web_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="168cc-1927">nx_web_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="168cc-1928">Establece la función de devolución de llamada de autenticación implícita</span><span class="sxs-lookup"><span data-stu-id="168cc-1928">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1929">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1929">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a><span data-ttu-id="168cc-1930">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1930">Description</span></span>

<span data-ttu-id="168cc-1931">Este servicio establece la devolución de llamada invocada cuando se realiza la autenticación implícita.</span><span class="sxs-lookup"><span data-stu-id="168cc-1931">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1932">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1932">Input Parameters</span></span>

- <span data-ttu-id="168cc-1933">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1933">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="168cc-1934">**digest_authenticate_callback** Puntero a la devolución de llamada de autenticación implícita.</span><span class="sxs-lookup"><span data-stu-id="168cc-1934">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1935">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1935">Return Values</span></span>

- <span data-ttu-id="168cc-1936">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1936">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="168cc-1937">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1937">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="168cc-1938">NX_NOT_SUPPORTED (0x4B) Autenticación implícita no habilitada.</span><span class="sxs-lookup"><span data-stu-id="168cc-1938">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1939">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1939">Allowed From</span></span>

<span data-ttu-id="168cc-1940">Application</span><span class="sxs-lookup"><span data-stu-id="168cc-1940">Application</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1941">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1941">Example</span></span>

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a><span data-ttu-id="168cc-1942">nx_web_http_server_authenticate_check_set</span><span class="sxs-lookup"><span data-stu-id="168cc-1942">nx_web_http_server_authenticate_check_set</span></span>

<span data-ttu-id="168cc-1943">Establece la función de devolución de llamada de autenticación implícita</span><span class="sxs-lookup"><span data-stu-id="168cc-1943">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="168cc-1944">Prototipo</span><span class="sxs-lookup"><span data-stu-id="168cc-1944">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a><span data-ttu-id="168cc-1945">Descripción</span><span class="sxs-lookup"><span data-stu-id="168cc-1945">Description</span></span>

<span data-ttu-id="168cc-1946">Este servicio establece la devolución de llamada invocada cuando se realiza la comprobación de autenticación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1946">This service sets the callback invoked when authenticate check is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="168cc-1947">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="168cc-1947">Input Parameters</span></span>

- <span data-ttu-id="168cc-1948">**http_server_ptr** Puntero a la instancia de servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="168cc-1948">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="168cc-1949">**authenticate_check_externded** Puntero para autenticar la devolución de llamada de comprobación.</span><span class="sxs-lookup"><span data-stu-id="168cc-1949">**authenticate_check_externded** Pointer to authenticate check callback</span></span>

### <a name="return-values"></a><span data-ttu-id="168cc-1950">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="168cc-1950">Return Values</span></span>

- <span data-ttu-id="168cc-1951">**NX_SUCCESS** (0x00) Devolución de llamada establecida correctamente.</span><span class="sxs-lookup"><span data-stu-id="168cc-1951">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="168cc-1952">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="168cc-1952">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="168cc-1953">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="168cc-1953">Allowed From</span></span>

<span data-ttu-id="168cc-1954">Application</span><span class="sxs-lookup"><span data-stu-id="168cc-1954">Application</span></span>

### <a name="example"></a><span data-ttu-id="168cc-1955">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="168cc-1955">Example</span></span>

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
