---
title: 'Capítulo 1: Introducción a NetX HTTP'
description: En este documento se explica cómo el protocolo HTTP es un protocolo diseñado para transferir contenido en la web.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6137cc0d8deb753d784be844d5abc7778dd62295
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815198"
---
# <a name="chapter-1---introduction-to-netx-http"></a><span data-ttu-id="6cb73-103">Capítulo 1: Introducción a NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-103">Chapter 1 - Introduction to NetX HTTP</span></span>

<span data-ttu-id="6cb73-104">El protocolo de transferencia de hipertexto (HTTP) es un protocolo diseñado para transferir contenido en la web.</span><span class="sxs-lookup"><span data-stu-id="6cb73-104">The Hypertext Transfer Protocol (HTTP) is a protocol designed for transferring content on the Web.</span></span> <span data-ttu-id="6cb73-105">HTTP es un protocolo simple que emplea servicios de protocolo de control de transmisión (TCP) confiables para realizar su función de transferencia de contenido.</span><span class="sxs-lookup"><span data-stu-id="6cb73-105">HTTP is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its content transfer function.</span></span> <span data-ttu-id="6cb73-106">Por este motivo, HTTP es un protocolo de transferencia de contenido de gran confiabilidad.</span><span class="sxs-lookup"><span data-stu-id="6cb73-106">Because of this, HTTP is a highly reliable content transfer protocol.</span></span> <span data-ttu-id="6cb73-107">HTTP es uno de los protocolos de aplicación más usados.</span><span class="sxs-lookup"><span data-stu-id="6cb73-107">HTTP is one of the most used application protocols.</span></span> <span data-ttu-id="6cb73-108">Todas las operaciones en la web usan el protocolo HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-108">All operations on the Web utilize the HTTP protocol.</span></span>

## <a name="http-requirements"></a><span data-ttu-id="6cb73-109">Requisitos de HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-109">HTTP Requirements</span></span>

<span data-ttu-id="6cb73-110">Para que funcione correctamente, el paquete NetX HTTP requiere que esté instalado NetX (versión 5.2 o posterior).</span><span class="sxs-lookup"><span data-stu-id="6cb73-110">In order to function properly, the NetX HTTP package requires that a NetX (version 5.2 or later) is installed.</span></span> <span data-ttu-id="6cb73-111">Además, se debe crear una instancia de IP y TCP debe estar habilitado en la misma instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-111">In addition, an IP instance must already be created and TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="6cb73-112">El archivo de demostración de la sección "sistema de ejemplo pequeño" del **Capítulo 2** mostrará cómo se hace esto.</span><span class="sxs-lookup"><span data-stu-id="6cb73-112">The demo file in section “Small Example System” in **Chapter 2** will demonstrate how this is done.</span></span>

<span data-ttu-id="6cb73-113">La parte del cliente HTTP del paquete NetX HTTP no tiene ningún requisito adicional.</span><span class="sxs-lookup"><span data-stu-id="6cb73-113">The HTTP Client portion of the NetX HTTP package has no further requirements.</span></span>

<span data-ttu-id="6cb73-114">La parte del servidor HTTP del paquete NetX HTTP tiene varios requisitos adicionales.</span><span class="sxs-lookup"><span data-stu-id="6cb73-114">The HTTP Server portion of the NetX HTTP package has several additional requirements.</span></span> <span data-ttu-id="6cb73-115">En primer lugar, se necesita acceso completo al *puerto 80* de TCP conocido para controlar todas las solicitudes HTTP de cliente.</span><span class="sxs-lookup"><span data-stu-id="6cb73-115">First, it requires complete access to TCP *well-known port 80* for handling all Client HTTP requests.</span></span> <span data-ttu-id="6cb73-116">El servidor HTTP también está diseñado para su uso con el sistema de archivos incrustado FileX.</span><span class="sxs-lookup"><span data-stu-id="6cb73-116">The HTTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="6cb73-117">Si FileX no está disponible, el usuario puede migrar las partes de FileX usadas a su propio entorno.</span><span class="sxs-lookup"><span data-stu-id="6cb73-117">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="6cb73-118">Esto se describe en secciones posteriores de esta guía.</span><span class="sxs-lookup"><span data-stu-id="6cb73-118">This is discussed in later sections of this guide.</span></span>

## <a name="http-constraints"></a><span data-ttu-id="6cb73-119">Restricciones de HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-119">HTTP Constraints</span></span> 

<span data-ttu-id="6cb73-120">El protocolo de NetX HTTP implementa el estándar HTTP 1.0.</span><span class="sxs-lookup"><span data-stu-id="6cb73-120">The NetX HTTP protocol implements the HTTP 1.0 standard.</span></span> <span data-ttu-id="6cb73-121">Sin embargo, se aplican las restricciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="6cb73-121">However, there are following constraints:</span></span>

1.  <span data-ttu-id="6cb73-122">No se admiten conexiones persistentes</span><span class="sxs-lookup"><span data-stu-id="6cb73-122">Persistent connections are not supported</span></span>

2.  <span data-ttu-id="6cb73-123">No se admite la canalización de solicitudes</span><span class="sxs-lookup"><span data-stu-id="6cb73-123">Request pipelining is not supported</span></span>

3.  <span data-ttu-id="6cb73-124">El servidor HTTP es compatible con la autenticación implícita básica y MD5, pero no con MD5-sess.</span><span class="sxs-lookup"><span data-stu-id="6cb73-124">The HTTP Server supports both basic and MD5 digest authentication, but not MD5-sess.</span></span> <span data-ttu-id="6cb73-125">En la actualidad, el cliente HTTP solo admite la autenticación básica.</span><span class="sxs-lookup"><span data-stu-id="6cb73-125">At present, the HTTP Client supports only basic authentication.</span></span>

4.  <span data-ttu-id="6cb73-126">No se admite la compresión de contenido.</span><span class="sxs-lookup"><span data-stu-id="6cb73-126">No content compression is supported.</span></span>

5.  <span data-ttu-id="6cb73-127">No se admiten las solicitudes TRACE, OPTIONS y CONNECT.</span><span class="sxs-lookup"><span data-stu-id="6cb73-127">TRACE, OPTIONS, and CONNECT requests are not supported.</span></span>

6.  <span data-ttu-id="6cb73-128">El grupo de paquetes asociado al servidor o cliente HTTP debe ser lo suficientemente grande como para contener el encabezado HTTP completo.</span><span class="sxs-lookup"><span data-stu-id="6cb73-128">The packet pool associated with the HTTP Server or Client must be large enough to hold the complete HTTP header.</span></span>

7.  <span data-ttu-id="6cb73-129">Los servicios de cliente HTTP son solo para la transferencia de contenido: no se proporciona ninguna utilidad de presentación en este paquete.</span><span class="sxs-lookup"><span data-stu-id="6cb73-129">HTTP Client services are for content transfer only—there are no display utilities provided in this package.</span></span>

## <a name="http-url-resource-names"></a><span data-ttu-id="6cb73-130">URL HTTP (nombres de recursos)</span><span class="sxs-lookup"><span data-stu-id="6cb73-130">HTTP URL (Resource Names)</span></span>

<span data-ttu-id="6cb73-131">El protocolo HTTP está diseñado para transferir contenido en la web.</span><span class="sxs-lookup"><span data-stu-id="6cb73-131">The HTTP protocol is designed to transfer content on Web.</span></span> <span data-ttu-id="6cb73-132">El contenido solicitado se especifica mediante el localizador universal de recursos (URL).</span><span class="sxs-lookup"><span data-stu-id="6cb73-132">The requested content is specified by the Universal Resource Locator (URL).</span></span> <span data-ttu-id="6cb73-133">Este es el componente principal de cada solicitud HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-133">This is the primary component of every HTTP request.</span></span> <span data-ttu-id="6cb73-134">Las direcciones URL siempre comienzan con un carácter "/" y suelen corresponderse con archivos del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-134">URLs always start with a “/” character and typically correspond to files on the HTTP Server.</span></span> <span data-ttu-id="6cb73-135">A continuación se muestran extensiones de archivo HTTP comunes:</span><span class="sxs-lookup"><span data-stu-id="6cb73-135">Common HTTP file extensions are shown below:</span></span>

- <span data-ttu-id="6cb73-136">**.htm (o .html)** Lenguaje de marcado de hipertexto (HTML)</span><span class="sxs-lookup"><span data-stu-id="6cb73-136">**.htm (or .html)** Hypertext Markup Language (HTML)</span></span>
- <span data-ttu-id="6cb73-137">**.txt** Texto ASCII sin formato</span><span class="sxs-lookup"><span data-stu-id="6cb73-137">**.txt** Plain ASCII text</span></span>
- <span data-ttu-id="6cb73-138">**.gif** Imagen GIF binaria</span><span class="sxs-lookup"><span data-stu-id="6cb73-138">**.gif** Binary GIF image</span></span>
- <span data-ttu-id="6cb73-139">**.xbm** Imagen Xbitmap binaria</span><span class="sxs-lookup"><span data-stu-id="6cb73-139">**.xbm** Binary Xbitmap image</span></span>

## <a name="http-client-requests"></a><span data-ttu-id="6cb73-140">Solicitudes de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-140">HTTP Client Requests</span></span>

<span data-ttu-id="6cb73-141">HTTP posee un mecanismo sencillo para solicitar contenido web.</span><span class="sxs-lookup"><span data-stu-id="6cb73-141">The HTTP has a simple mechanism for requesting Web content.</span></span> <span data-ttu-id="6cb73-142">Básicamente, hay un conjunto de comandos HTTP estándar que emite el cliente después de que una conexión se haya establecido correctamente en el *puerto conocido 80* de TCP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-142">There is basically a set of standard HTTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 80*.</span></span> <span data-ttu-id="6cb73-143">A continuación se muestran algunos de los comandos HTTP básicos:</span><span class="sxs-lookup"><span data-stu-id="6cb73-143">The following shows some of the basic HTTP commands:</span></span>

- <span data-ttu-id="6cb73-144">GET resource HTTP/1.0 *Obtener el recurso especificado*</span><span class="sxs-lookup"><span data-stu-id="6cb73-144">GET resource HTTP/1.0 *Get the specified resource*</span></span>
- <span data-ttu-id="6cb73-145">POST resource HTTP/1.0 *Obtener el recurso especificado y pasar la entrada adjunta al servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="6cb73-145">POST resource HTTP/1.0 *Get the specified resource and pass attached input to the HTTP Server*</span></span>
- <span data-ttu-id="6cb73-146">HEAD resource HTTP/1.0 *Se trata como un GET pero el servidor HTTP no devuelve ningún contenido*</span><span class="sxs-lookup"><span data-stu-id="6cb73-146">HEAD resource HTTP/1.0 *Treated like a GET but not content is returned by the HTTP Server*</span></span>
- <span data-ttu-id="6cb73-147">PUT resource HTTP/1.0 *Colocar recurso en servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="6cb73-147">PUT resource HTTP/1.0 *Place resource on HTTP Server*</span></span>
- <span data-ttu-id="6cb73-148">DELETE resource HTTP/1.0 *Eliminar recursos en el servidor*</span><span class="sxs-lookup"><span data-stu-id="6cb73-148">DELETE resource HTTP/1.0 *Delete resource on the Server*</span></span>

<span data-ttu-id="6cb73-149">Estos comandos ASCII los generan internamente los exploradores web y los servicios de cliente NetX HTTP para realizar operaciones HTTP con un servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-149">These ASCII commands are generated internally by Web browsers and the NetX HTTP Client services to perform HTTP operations with an HTTP Server.</span></span>

>[!NOTE] 
> <span data-ttu-id="6cb73-150">La aplicación de cliente HTTP tiene como valor predeterminado el puerto de conexión 80.</span><span class="sxs-lookup"><span data-stu-id="6cb73-150">The HTTP Client application default to the connect port of 80.</span></span> <span data-ttu-id="6cb73-151">Sin embargo, puede cambiar el puerto de conexión al servidor HTTP en tiempo de ejecución mediante el servicio *nx_http_client_set_connect_port*.</span><span class="sxs-lookup"><span data-stu-id="6cb73-151">However, it can change the connect port to the HTTP Server at runtime using the *nx_http_client_set_connect_port* service.</span></span> <span data-ttu-id="6cb73-152">Consulte el capítulo 4 para obtener más detalles de este servicio.</span><span class="sxs-lookup"><span data-stu-id="6cb73-152">See Chapter 4 for more details of this service.</span></span> <span data-ttu-id="6cb73-153">Esto sirve para dar cabida a los servidores web que utilizan ocasionalmente puertos alternativos para las conexiones de cliente.</span><span class="sxs-lookup"><span data-stu-id="6cb73-153">This is to accommodate web servers that occasionally use alternate ports for Client connections.</span></span>

## <a name="http-server-responses"></a><span data-ttu-id="6cb73-154">Respuestas del servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-154">HTTP Server Responses</span></span>

<span data-ttu-id="6cb73-155">El servidor HTTP emplea el mismo *puerto 80 conocido de TCP* para enviar respuestas de comando de cliente.</span><span class="sxs-lookup"><span data-stu-id="6cb73-155">The HTTP Server utilizes the same *well-known TCP port 80* to send Client command responses.</span></span> <span data-ttu-id="6cb73-156">Una vez que el servidor HTTP procesa el comando de cliente, devuelve una cadena de respuesta ASCII que incluye un código de estado numérico de 3 dígitos.</span><span class="sxs-lookup"><span data-stu-id="6cb73-156">Once the HTTP Server processes the Client command, it returns an ASCII response string that includes a 3-digit numeric status code.</span></span> <span data-ttu-id="6cb73-157">El software cliente HTTP usa la respuesta numérica para determinar si la operación se ha realizado correctamente o no.</span><span class="sxs-lookup"><span data-stu-id="6cb73-157">The numeric response is used by the HTTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="6cb73-158">A continuación se muestra una lista de las distintas respuestas del servidor HTTP a los comandos de cliente:</span><span class="sxs-lookup"><span data-stu-id="6cb73-158">Following is a list of various HTTP Server responses to Client commands:</span></span>

- <span data-ttu-id="6cb73-159">200 *La solicitud se ha realizado correctamente*</span><span class="sxs-lookup"><span data-stu-id="6cb73-159">200 *Request was successful*</span></span>
- <span data-ttu-id="6cb73-160">400 *La solicitud no tiene el formato correcto*</span><span class="sxs-lookup"><span data-stu-id="6cb73-160">400 *Request was not formed properly*</span></span>
- <span data-ttu-id="6cb73-161">401 *Solicitud no autorizada, el cliente debe enviar la autenticación*</span><span class="sxs-lookup"><span data-stu-id="6cb73-161">401 *Unauthorized request, client needs to send authentication*</span></span>
- <span data-ttu-id="6cb73-162">404 *No se ha encontrado el recurso especificado en la solicitud*</span><span class="sxs-lookup"><span data-stu-id="6cb73-162">404 *Specified resource in request was not found*</span></span>
- <span data-ttu-id="6cb73-163">500 *Error interno del servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="6cb73-163">500 *Internal HTTP Server error*</span></span>
- <span data-ttu-id="6cb73-164">501 *Solicitud no implementada por el servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="6cb73-164">501 *Request not implemented by HTTP Server*</span></span>
- <span data-ttu-id="6cb73-165">502 *El servicio no está disponible*</span><span class="sxs-lookup"><span data-stu-id="6cb73-165">502 *Service is not available*</span></span>

<span data-ttu-id="6cb73-166">Por ejemplo, a una solicitud de cliente PUT correcta para el archivo "test.htm" se responde con el mensaje "HTTP/1.0 200 OK".</span><span class="sxs-lookup"><span data-stu-id="6cb73-166">For example, a successful Client request to PUT the file “test.htm” is responded with the message “HTTP/1.0 200 OK.”</span></span>

## <a name="http-communication"></a><span data-ttu-id="6cb73-167">Comunicación HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-167">HTTP Communication</span></span>

<span data-ttu-id="6cb73-168">Como se ha mencionado anteriormente, el servidor HTTP emplea el *puerto 80 conocido de TCP* para las solicitudes de cliente de campo.</span><span class="sxs-lookup"><span data-stu-id="6cb73-168">As mentioned previously, the HTTP Server utilizes the *well-known TCP port 80* to field Client requests.</span></span> <span data-ttu-id="6cb73-169">Los clientes HTTP pueden utilizar cualquier puerto TCP disponible.</span><span class="sxs-lookup"><span data-stu-id="6cb73-169">HTTP Clients may use any available TCP port.</span></span> <span data-ttu-id="6cb73-170">La secuencia general de eventos HTTP es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="6cb73-170">The general sequence of HTTP events is as follows:</span></span>

<span data-ttu-id="6cb73-171">**Solicitud HTTP GET**:</span><span class="sxs-lookup"><span data-stu-id="6cb73-171">**HTTP GET Request**:</span></span>

1.  <span data-ttu-id="6cb73-172">El cliente emite una conexión TCP al puerto del servidor 80.</span><span class="sxs-lookup"><span data-stu-id="6cb73-172">Client issues TCP connect to Server port 80.</span></span>

2.  <span data-ttu-id="6cb73-173">El cliente envía la solicitud "**GET resource HTTP/1.0**" (junto con otra información de encabezado).</span><span class="sxs-lookup"><span data-stu-id="6cb73-173">Client sends “**GET resource HTTP/1.0**” request (along with other header information).</span></span>

3.  <span data-ttu-id="6cb73-174">El servidor genera un mensaje "**HTTP/1.0 200 OK**" con información adicional seguida inmediatamente del contenido del recurso (si existe).</span><span class="sxs-lookup"><span data-stu-id="6cb73-174">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content (if any).</span></span>

4.  <span data-ttu-id="6cb73-175">El servidor realiza una desconexión.</span><span class="sxs-lookup"><span data-stu-id="6cb73-175">Server performs a disconnection.</span></span>

5.  <span data-ttu-id="6cb73-176">El cliente realiza una desconexión.</span><span class="sxs-lookup"><span data-stu-id="6cb73-176">Client performs a disconnection.</span></span>

<span data-ttu-id="6cb73-177">**Solicitud HTTP PUT**:</span><span class="sxs-lookup"><span data-stu-id="6cb73-177">**HTTP PUT Request**:</span></span>

1. <span data-ttu-id="6cb73-178">El cliente emite una conexión TCP al puerto del servidor 80.</span><span class="sxs-lookup"><span data-stu-id="6cb73-178">Client issues TCP connect to Server port 80.</span></span>

2. <span data-ttu-id="6cb73-179">El cliente envía la solicitud "**PUT resource HTTP/1.0**", junto con otra información de encabezado, seguida del contenido del recurso.</span><span class="sxs-lookup"><span data-stu-id="6cb73-179">Client sends “**PUT resource HTTP/1.0**” request, along with other header information, and followed by the resource content.</span></span>

3. <span data-ttu-id="6cb73-180">El servidor genera un mensaje "**HTTP/1.0 200 OK**" con información adicional seguida inmediatamente del contenido del recurso.</span><span class="sxs-lookup"><span data-stu-id="6cb73-180">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content.</span></span>

4. <span data-ttu-id="6cb73-181">El servidor realiza una desconexión.</span><span class="sxs-lookup"><span data-stu-id="6cb73-181">Server performs a disconnection.</span></span>

5. <span data-ttu-id="6cb73-182">El cliente realiza una desconexión.</span><span class="sxs-lookup"><span data-stu-id="6cb73-182">Client performs a disconnection.</span></span>

>[!NOTE] 
> <span data-ttu-id="6cb73-183">Como se ha mencionado anteriormente, el cliente HTTP puede cambiar el puerto de conexión predeterminado de 80 a otro puerto mediante *nx_http_client_set_connect_port* para servidores web que usan puertos alternativos para conectarse a los clientes.</span><span class="sxs-lookup"><span data-stu-id="6cb73-183">As mentioned previously, the HTTP Client can change the default connect port from 80 to another port using the *nx_http_client_set_connect_port* for web servers that use alternate ports to connect to clients.</span></span>

## <a name="http-authentication"></a><span data-ttu-id="6cb73-184">Autenticación HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-184">HTTP Authentication</span></span>

<span data-ttu-id="6cb73-185">La autenticación HTTP es opcional y no es necesaria para todas las solicitudes web.</span><span class="sxs-lookup"><span data-stu-id="6cb73-185">HTTP authentication is optional and isn’t required for all Web requests.</span></span> <span data-ttu-id="6cb73-186">Hay dos tipos de autenticación, a saber: *básica* e *implícita*.</span><span class="sxs-lookup"><span data-stu-id="6cb73-186">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="6cb73-187">La autenticación básica es equivalente a la autenticación de *nombre* y *contraseña* que se encuentra en muchos protocolos.</span><span class="sxs-lookup"><span data-stu-id="6cb73-187">Basic authentication is equivalent to the *name* and *password* authentication found in many protocols.</span></span> <span data-ttu-id="6cb73-188">En la autenticación HTTP básica, el nombre y las contraseñas se concatenan y se codifican en formato base64.</span><span class="sxs-lookup"><span data-stu-id="6cb73-188">In HTTP basic authentication, the name and passwords are concatenated and encoded in the base64 format.</span></span> <span data-ttu-id="6cb73-189">El principal inconveniente de la autenticación básica es que el nombre y la contraseña se transmiten abiertamente en la solicitud.</span><span class="sxs-lookup"><span data-stu-id="6cb73-189">The main disadvantage of basic authentication is the name and password are transmitted openly in the request.</span></span> <span data-ttu-id="6cb73-190">Esto hace que resulte muy fácil que el nombre y la contraseña se roben.</span><span class="sxs-lookup"><span data-stu-id="6cb73-190">This makes it somewhat easy for the name and password to be stolen.</span></span> <span data-ttu-id="6cb73-191">La autenticación implícita soluciona este problema, ya que nunca transmite el nombre y la contraseña en la solicitud.</span><span class="sxs-lookup"><span data-stu-id="6cb73-191">Digest authentication addresses this problem by never transmitting the name and password in the request.</span></span> <span data-ttu-id="6cb73-192">En su lugar, se utiliza un algoritmo para derivar una clave de 128 bits o una síntesis del nombre, la contraseña y otra información.</span><span class="sxs-lookup"><span data-stu-id="6cb73-192">Instead, an algorithm is used to derive a 128-bit key or digest from the name, password, and other information.</span></span> <span data-ttu-id="6cb73-193">El servidor NetX HTTP admite el algoritmo de síntesis estándar MD5.</span><span class="sxs-lookup"><span data-stu-id="6cb73-193">The NetX HTTP Server supports the standard MD5 digest algorithm.</span></span>

<span data-ttu-id="6cb73-194">¿Cuándo se requiere autenticación?</span><span class="sxs-lookup"><span data-stu-id="6cb73-194">When is authentication required?</span></span> <span data-ttu-id="6cb73-195">Básicamente, el servidor HTTP decide si un recurso solicitado requiere autenticación.</span><span class="sxs-lookup"><span data-stu-id="6cb73-195">Basically, the HTTP Server decides if a requested resource requires authentication.</span></span> <span data-ttu-id="6cb73-196">Si se requiere autenticación y la solicitud de cliente no incluía la autenticación correcta, se envía al cliente una respuesta "HTTP/1.0 401 No autorizado" con el tipo de autenticación necesario.</span><span class="sxs-lookup"><span data-stu-id="6cb73-196">If authentication is required and the Client request did not include the proper authentication, a “HTTP/1.0 401 Unauthorized” response with the type of authentication required is sent to the Client.</span></span> <span data-ttu-id="6cb73-197">A continuación, se espera que el cliente formule una nueva solicitud con la autenticación adecuada.</span><span class="sxs-lookup"><span data-stu-id="6cb73-197">The Client is then expected to form a new request with the proper authentication.</span></span>

## <a name="http-authentication-callback"></a><span data-ttu-id="6cb73-198">Devolución de llamada de autenticación HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-198">HTTP Authentication Callback</span></span>

<span data-ttu-id="6cb73-199">Como se ha mencionado anteriormente, la autenticación HTTP es opcional y no es necesaria en todas las transferencias web.</span><span class="sxs-lookup"><span data-stu-id="6cb73-199">As mentioned before, HTTP authentication is optional and isn’t required on all Web transfers.</span></span> <span data-ttu-id="6cb73-200">Además, la autenticación suele depender del recurso.</span><span class="sxs-lookup"><span data-stu-id="6cb73-200">In addition, authentication is typically resource dependent.</span></span> <span data-ttu-id="6cb73-201">El acceso a algunos recursos del servidor requiere autenticación, mientras que otros, no.</span><span class="sxs-lookup"><span data-stu-id="6cb73-201">Access of some resources on the Server require authentication, while others do not.</span></span> <span data-ttu-id="6cb73-202">El paquete de servidor NetX HTTP permite que la aplicación especifique (a través de la llamada a ***nx_http_server_create***) una rutina de devolución de llamada de autenticación a la que se llama al comenzar a administrar cada solicitud de cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-202">The NetX HTTP Server package allows the application to specify (via the ***nx_http_server_create*** call) an authentication callback routine that is called at the beginning of handling each HTTP Client request.</span></span>

<span data-ttu-id="6cb73-203">La rutina de devolución de llamada proporciona el servidor NetX HTTP con las cadenas de nombre de usuario, contraseña y dominio kerberos asociadas al recurso y devuelven el tipo de autenticación necesaria.</span><span class="sxs-lookup"><span data-stu-id="6cb73-203">The callback routine provides the NetX HTTP Server with the username, password, and realm strings associated with the resource and return the type of authentication necessary.</span></span> <span data-ttu-id="6cb73-204">Si no es necesaria ninguna autenticación para el recurso, la devolución de llamada de autenticación debe devolver el valor de **NX_HTTP_DONT_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="6cb73-204">If no authentication is necessary for the resource, the authentication callback should return the value of **NX_HTTP_DONT_AUTHENTICATE**.</span></span> <span data-ttu-id="6cb73-205">De lo contrario, si se requiere la autenticación básica para el recurso especificado, la rutina debe devolver **NX_HTTP_BASIC_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="6cb73-205">Otherwise, if basic authentication is required for the specified resource, the routine should return **NX_HTTP_BASIC_AUTHENTICATE**.</span></span> <span data-ttu-id="6cb73-206">Y, por último, si se requiere autenticación implícita MD5, la rutina de devolución de llamada debe devolver **NX_HTTP_DIGEST_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="6cb73-206">And finally, if MD5 digest authentication is required, the callback routine should return **NX_HTTP_DIGEST_AUTHENTICATE**.</span></span> <span data-ttu-id="6cb73-207">Si no se requiere autenticación para ningún recurso proporcionado por el servidor HTTP, la devolución de llamada no es necesaria y se puede proporcionar un puntero NULL a la llamada de creación del servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-207">If no authentication is required for any resource provided by the HTTP Server, the callback is not needed and a NULL pointer can be provided to the HTTP Server create call.</span></span>

<span data-ttu-id="6cb73-208">El formato de la rutina de devolución de llamada de autenticación de la aplicación es muy simple y se define a continuación:</span><span class="sxs-lookup"><span data-stu-id="6cb73-208">The format of the application authenticate callback routine is very simple and is defined below:</span></span>

```c
UINT nx_http_server_authentication_check (NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, CHAR **password,
                                         CHAR **realm);
```

<span data-ttu-id="6cb73-209">Los parámetros de entrada se definen a continuación:</span><span class="sxs-lookup"><span data-stu-id="6cb73-209">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="6cb73-210">*request_type*: especifica la solicitud de cliente HTTP; las solicitudes válidas se definen como:</span><span class="sxs-lookup"><span data-stu-id="6cb73-210">*request_type* Specifies the HTTP Client request, valid requests are defined as:</span></span>
  - <span data-ttu-id="6cb73-211">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-211">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
  - <span data-ttu-id="6cb73-212">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-212">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
  - <span data-ttu-id="6cb73-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
  - <span data-ttu-id="6cb73-214">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-214">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
  - <span data-ttu-id="6cb73-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>
- <span data-ttu-id="6cb73-216">*resource* Recurso específico solicitado.</span><span class="sxs-lookup"><span data-stu-id="6cb73-216">*resource* Specific resource requested.</span></span>
- <span data-ttu-id="6cb73-217">*name* Destino del puntero al nombre de usuario solicitado.</span><span class="sxs-lookup"><span data-stu-id="6cb73-217">*name* Destination for the pointer to the required username.</span></span>
- <span data-ttu-id="6cb73-218">*password* Destino del puntero a la contraseña solicitada.</span><span class="sxs-lookup"><span data-stu-id="6cb73-218">*password* Destination for the pointer to the required password.</span></span>
- <span data-ttu-id="6cb73-219">*realm* Destino del puntero al dominio kerberos para esta autenticación.</span><span class="sxs-lookup"><span data-stu-id="6cb73-219">*realm* Destination for the pointer to the realm for this authentication.</span></span>

<span data-ttu-id="6cb73-220">El valor devuelto de la rutina de autenticación especifica si se requiere autenticación.</span><span class="sxs-lookup"><span data-stu-id="6cb73-220">The return value of the authentication routine specifies if authentication is required.</span></span> <span data-ttu-id="6cb73-221">Los punteros name, password y realm no se usan si la rutina de devolución de llamada de autenticación devuelve **NX_HTTP_DONT_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="6cb73-221">name, password, and realm pointers are not used if **NX_HTTP_DONT_AUTHENTICATE** is returned by the authentication callback routine.</span></span> <span data-ttu-id="6cb73-222">De lo contrario, el programador del servidor HTTP debe asegurarse de que **NX_HTTP_MAX_USERNAME** y **NX_HTTP_MAX_PASSWORD** definidos en *nx_http_server.h* sean lo suficientemente grandes para el nombre de usuario y la contraseña especificados en la devolución de llamada de autenticación.</span><span class="sxs-lookup"><span data-stu-id="6cb73-222">Otherwise the HTTP server developer must ensure that **NX_HTTP_MAX_USERNAME** and **NX_HTTP_MAX_PASSWORD** defined in *nx_http_server.h* are large enough for the username and password specified in the authentication callback.</span></span> <span data-ttu-id="6cb73-223">Ambos tienen como valor de tamaño predeterminado 20 caracteres.</span><span class="sxs-lookup"><span data-stu-id="6cb73-223">These are both defaulted to size 20 chars.</span></span>

## <a name="http-invalid-usernamepassword-callback"></a><span data-ttu-id="6cb73-224">Devolución de llamada de nombre de usuario/contraseña no válida HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-224">HTTP Invalid Username/Password Callback</span></span>

<span data-ttu-id="6cb73-225">La devolución de llamada de nombre de usuario/contraseña no válida en el servidor NetX HTTP se invoca si el servidor HTTP recibe una combinación de nombre de usuario y contraseña no válida en una solicitud de cliente.</span><span class="sxs-lookup"><span data-stu-id="6cb73-225">The optional invalid username/password callback in NetX HTTP Server is invoked if HTTP server receives an invalid username and password combination in a Client request.</span></span> <span data-ttu-id="6cb73-226">Si la aplicación de servidor HTTP registra una devolución de llamada con el servidor HTTP, se invocará si se produce un error en la autenticación básica o implícita *en nx_http_server_get_process*, en *nx_http_server_put_process* o *en nx_http_server_delete_process.*</span><span class="sxs-lookup"><span data-stu-id="6cb73-226">If the HTTP server application registers a callback with HTTP server it will be invoked if either basic or digest authentication fails *in nx_http_server_get_process*, in *nx_http_server_put_process,* or *in nx_http_server_delete_process.*</span></span>

<span data-ttu-id="6cb73-227">Para registrar una devolución de llamada con el servidor HTTP, el siguiente servicio se define en el servidor NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-227">To register a callback with the HTTP server, the following service is defined in NetX HTTP Server.</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set (NX_HTTP_SERVER *http_server_ptr,
                                                    UINT *invalid_username_password_callback)
                                                    (CHAR *resource,
                                                    ULONG *client_nx_address,
                                                    UINT request_type));
```
<span data-ttu-id="6cb73-228">Los tipos de solicitud se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="6cb73-228">The request types are defined as follows:</span></span>

- <span data-ttu-id="6cb73-229">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-229">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
- <span data-ttu-id="6cb73-230">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-230">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
- <span data-ttu-id="6cb73-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
- <span data-ttu-id="6cb73-232">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-232">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
- <span data-ttu-id="6cb73-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="6cb73-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>

## <a name="http-insert-gmt-date-header-callback"></a><span data-ttu-id="6cb73-234">Devolución de llamada de encabezado de fecha GMT de inserción HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-234">HTTP Insert GMT Date Header Callback</span></span>

<span data-ttu-id="6cb73-235">Hay una devolución de llamada opcional en el servidor NetX HTTP para insertar un encabezado de fecha en sus mensajes de respuesta.</span><span class="sxs-lookup"><span data-stu-id="6cb73-235">There is an optional callback in NetX HTTP Server to insert a date header in its response messages.</span></span> <span data-ttu-id="6cb73-236">Esta devolución de llamada se invoca cuando el servidor HTTP responde a una solicitud put o get</span><span class="sxs-lookup"><span data-stu-id="6cb73-236">This callback is invoked when the HTTP Server is responding to a put or get request</span></span>

<span data-ttu-id="6cb73-237">Para registrar una devolución de llamada de fecha GMT con el servidor HTTP, el siguiente servicio se define en el servidor NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-237">To register a GMT date callback with the HTTP server, the following service is defined in the NetX HTTP Server.</span></span>

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="6cb73-238">El tipo de datos NX_HTTP_SERVER_DATE se define de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="6cb73-238">The NX_HTTP_SERVER_DATE data type is defined as follows:</span></span>

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT     nx_http_server_year;         /* Year        */
    UCHAR      nx_http_server_month;        /* Month       */
    UCHAR      nx_http_server_day;          /* Day         */
    UCHAR      nx_http_server_hour;         /* Hour        */
    UCHAR      nx_http_server_minute;       /* Minute      */
    UCHAR      nx_http_server_second;       /* Second      */
    UCHAR      nx_http_server_weekday;      /* Weekday     */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a><span data-ttu-id="6cb73-239">Devolución de llamada GET de información de caché HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-239">HTTP Cache Info Get Callback</span></span>

<span data-ttu-id="6cb73-240">El servidor HTTP tiene una devolución de llamada para solicitar la antigüedad y la fecha máximas de la aplicación HTTP para un recurso específico.</span><span class="sxs-lookup"><span data-stu-id="6cb73-240">The HTTP Server has a callback to request the max age and date from the HTTP application for a specific resource.</span></span> <span data-ttu-id="6cb73-241">Esta información se usa para determinar si el servidor HTTP envía toda la página como respuesta a una solicitud GET de cliente.</span><span class="sxs-lookup"><span data-stu-id="6cb73-241">This information is used to determine if the HTTP server sends the entire page in response to a Client Get request.</span></span> <span data-ttu-id="6cb73-242">Si no se encuentra "If modified since" en la solicitud de cliente o no coincide con la fecha de "Last modified" devuelta por la devolución de llamada de caché GET, se envía toda la página.</span><span class="sxs-lookup"><span data-stu-id="6cb73-242">If the “if modified since” in the Client request is not found or does not match the “last modified” date returned by the get cache callback, the entire page is sent.</span></span>

<span data-ttu-id="6cb73-243">Para registrar una devolución de llamada con el servidor HTTP, se define el siguiente servicio:</span><span class="sxs-lookup"><span data-stu-id="6cb73-243">To register the callback with the HTTP server the following service is defined:</span></span>

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a><span data-ttu-id="6cb73-244">Compatibilidad con varias partes HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-244">HTTP Multipart Support</span></span>

<span data-ttu-id="6cb73-245">Las extensiones multipropósito de correo Internet (MIME) estaban pensadas originalmente para el protocolo SMTP, pero su uso se ha distribuido a HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cb73-245">Multipurpose Internet Mail Extensions (MIME) was originally intended for the SMTP protocol, but its use has spread to HTTP.</span></span> <span data-ttu-id="6cb73-246">MIME permite que los mensajes contengan tipos de mensajes mixtos (por ejemplo, imagen/jpg y texto/sin formato) dentro del mismo mensaje.</span><span class="sxs-lookup"><span data-stu-id="6cb73-246">MIME allows messages to contain mixed message types (e.g. image/jpg and text/plain) within the same message.</span></span> <span data-ttu-id="6cb73-247">El servidor NetX HTTP ha agregado servicios para determinar el tipo de contenido en los mensajes HTTP que contienen MIME del cliente.</span><span class="sxs-lookup"><span data-stu-id="6cb73-247">NetX HTTP Server has added services to determine content type in HTTP messages containing MIME from the Client.</span></span> <span data-ttu-id="6cb73-248">Para habilitar la compatibilidad con varias partes HTTP y usar estos servicios, debe definirse la opción de configuración **NX_HTTP_MULTIPART_ENABLE**.</span><span class="sxs-lookup"><span data-stu-id="6cb73-248">To enable HTTP multipart support and use these services, the configuration option **NX_HTTP_MULTIPART_ENABLE** must be defined.</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);

UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="6cb73-249">Para obtener más detalles sobre el uso de estos servicios, consulte su descripción en el capítulo 3 "Descripción de los servicios HTTP".</span><span class="sxs-lookup"><span data-stu-id="6cb73-249">For more details on the use of these services, see their description in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multi-thread-support"></a><span data-ttu-id="6cb73-250">Compatibilidad con varios subprocesos HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-250">HTTP Multi-Thread Support</span></span>

<span data-ttu-id="6cb73-251">Se puede llamar a los servicios de cliente NetX HTTP desde varios subprocesos simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="6cb73-251">The NetX HTTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="6cb73-252">Sin embargo, las solicitudes de lectura o escritura de una determinada instancia de cliente HTTP deben realizarse en secuencia desde el mismo subproceso.</span><span class="sxs-lookup"><span data-stu-id="6cb73-252">However, read or write requests for a particular HTTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="http-rfcs"></a><span data-ttu-id="6cb73-253">RFC de HTTP</span><span class="sxs-lookup"><span data-stu-id="6cb73-253">HTTP RFCs</span></span>

<span data-ttu-id="6cb73-254">NetX HTTP es compatible con la RFC1945 "Protocolo de transferencia de hipertexto/1.0", RFC 2581 "Control de congestión de TCP", RFC 1122 "Requisitos para hosts de Internet" y RFC relacionadas.</span><span class="sxs-lookup"><span data-stu-id="6cb73-254">NetX HTTP is compliant with RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts”, and related RFCs.</span></span>