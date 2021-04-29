---
title: 'Capítulo 3: Descripción de los servicios FTP'
description: Este capítulo contiene una descripción de todos los servicios FTP de NetX (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814706"
---
# <a name="chapter-3---description-of-ftp-services"></a><span data-ttu-id="353d1-103">Capítulo 3: Descripción de los servicios FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-103">Chapter 3 - Description of FTP services</span></span>

<span data-ttu-id="353d1-104">Este capítulo contiene una descripción de todos los servicios FTP de NetX (enumerados a continuación) en orden alfabético (excepto donde los equivalentes de IPv4 e IPv6 del mismo servicio se emparejan juntos).</span><span class="sxs-lookup"><span data-stu-id="353d1-104">This chapter contains a description of all NetX FTP services (listed below) in alphabetic order (except where IPv4 and IPv6 equivalents of the same service are paired together).</span></span>

> [!NOTE]
> <span data-ttu-id="353d1-105">En la sección “Valores devueltos” de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="353d1-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="353d1-106">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="353d1-106">nx_ftp_client_connect</span></span>

<span data-ttu-id="353d1-107">Conexión con un servidor FTP a través de IPv4</span><span class="sxs-lookup"><span data-stu-id="353d1-107">Connect to an FTP Server over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-108">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-108">Prototype</span></span>

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-109">Description</span></span>

<span data-ttu-id="353d1-110">Este servicio conecta la instancia del cliente FTP de NetX creada anteriormente al servidor FTP en la dirección IP suministrada.</span><span class="sxs-lookup"><span data-stu-id="353d1-110">This service connects the previously created NetX FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-111">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-111">Input Parameters</span></span>

- <span data-ttu-id="353d1-112">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-112">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-113">**server_ip**: dirección IP del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-113">**server_ip** IP address of FTP Server.</span></span>
- <span data-ttu-id="353d1-114">**username**: nombre de usuario del cliente para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="353d1-114">**username** Client username for authentication.</span></span>
- <span data-ttu-id="353d1-115">**password**: contraseña del cliente para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="353d1-115">**password** Client password for authentication.</span></span>
- <span data-ttu-id="353d1-116">**wait_option**: define cuánto tiempo va a esperar el servicio para la conexión del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-116">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="353d1-117">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-117">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-118">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-118">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-120">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-120">Return Values</span></span>

- <span data-ttu-id="353d1-121">**NX_SUCCESS** (0x00) Conexión FTP correcta.</span><span class="sxs-lookup"><span data-stu-id="353d1-121">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="353d1-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) No recibió una respuesta 22X (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="353d1-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) No recibió una respuesta 23X (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="353d1-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) No recibió una respuesta 33X (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="353d1-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) El cliente ya está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="353d1-126">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="353d1-126">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="353d1-127">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-127">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="353d1-128">NX_IP_ADDRESS_ERROR (0x21) Dirección IP no válida.</span><span class="sxs-lookup"><span data-stu-id="353d1-128">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-129">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-129">Allowed From</span></span>

<span data-ttu-id="353d1-130">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-130">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-131">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-131">Example</span></span>

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="353d1-132">Consulte también</span><span class="sxs-lookup"><span data-stu-id="353d1-132">See Also</span></span>

<span data-ttu-id="353d1-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="353d1-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span></span>

## <a name="nxd_ftp_client_connect"></a><span data-ttu-id="353d1-134">nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="353d1-134">nxd_ftp_client_connect</span></span>

<span data-ttu-id="353d1-135">Conexión a un servidor FTP con compatibilidad con IPv6</span><span class="sxs-lookup"><span data-stu-id="353d1-135">Connect to an FTP Server with IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-136">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-136">Prototype</span></span>

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-137">Description</span></span>

<span data-ttu-id="353d1-138">Este servicio conecta la instancia del cliente FTP de NetX Duo creada anteriormente al servidor FTP en la dirección IP suministrada.</span><span class="sxs-lookup"><span data-stu-id="353d1-138">This service connects the previously created NetX Duo FTP Client instance to the FTP Server at the supplied IP address.</span></span> <span data-ttu-id="353d1-139">Se admiten tanto redes IPv4 como redes IPv6.</span><span class="sxs-lookup"><span data-stu-id="353d1-139">Both IPv4 and IPv6 networks are supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-140">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-140">Input Parameters</span></span>

- <span data-ttu-id="353d1-141">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-141">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-142">**server_ipduo**: dirección IP del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-142">**server_ipduo** IP address of the FTP Server.</span></span>
- <span data-ttu-id="353d1-143">**username**: nombre de usuario del cliente para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="353d1-143">**username** Client username for authentication.</span></span>
- <span data-ttu-id="353d1-144">**password**: contraseña del cliente para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="353d1-144">**password** Client password for authentication.</span></span>
- <span data-ttu-id="353d1-145">**wait_option**: define cuánto tiempo va a esperar el servicio para la conexión del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-145">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="353d1-146">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-146">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-147">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-147">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-149">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-149">Return Values</span></span>

- <span data-ttu-id="353d1-150">**NX_SUCCESS** (0x00) Conexión FTP correcta.</span><span class="sxs-lookup"><span data-stu-id="353d1-150">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="353d1-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) No recibió una respuesta 22X (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="353d1-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) No recibió una respuesta 23X (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="353d1-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) No recibió una respuesta 33X (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="353d1-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) El cliente ya está conectado</span><span class="sxs-lookup"><span data-stu-id="353d1-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected</span></span>
- <span data-ttu-id="353d1-155">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="353d1-155">NX_PTR_ERROR (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="353d1-156">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-156">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="353d1-157">NX_IP_ADDRESS_ERROR (0x21) Dirección IP no válida.</span><span class="sxs-lookup"><span data-stu-id="353d1-157">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-158">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-158">Allowed From</span></span>

<span data-ttu-id="353d1-159">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-159">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-160">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-160">Example</span></span>

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="353d1-161">Consulte también</span><span class="sxs-lookup"><span data-stu-id="353d1-161">See Also</span></span>

<span data-ttu-id="353d1-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="353d1-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span></span>

## <a name="nx_ftp_client_create"></a><span data-ttu-id="353d1-163">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="353d1-163">nx_ftp_client_create</span></span>

<span data-ttu-id="353d1-164">Creación de una instancia del cliente FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-164">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-165">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-165">Prototype</span></span>

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="353d1-166">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-166">Description</span></span>

<span data-ttu-id="353d1-167">Este servicio crea una instancia del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-167">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-168">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-168">Input Parameters</span></span>

- <span data-ttu-id="353d1-169">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-169">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-170">**ftp_client_name**: nombre del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-170">**ftp_client_name** Name of FTP Client.</span></span>
- <span data-ttu-id="353d1-171">**ip_ptr**: puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="353d1-171">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="353d1-172">**window_size**: tamaño de ventana anunciado para sockets TCP de este cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-172">**window_size** Advertised window size for TCP sockets of this FTP Client.</span></span>
- <span data-ttu-id="353d1-173">**pool_ptr**: puntero al grupo de paquetes predeterminado para este cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-173">**pool_ptr** Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="353d1-174">Tenga en cuenta que la carga mínima de paquete debe ser lo suficientemente grande como para contener la ruta de acceso completa y el nombre de archivo o directorio.</span><span class="sxs-lookup"><span data-stu-id="353d1-174">Note that the minimum packet payload must be large enough to hold  complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-175">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-175">Return Values</span></span>

- <span data-ttu-id="353d1-176">**NX_SUCCESS** (0x00) Cliente FTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-176">**NX_SUCCESS** (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="353d1-177">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="353d1-177">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-178">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-178">Allowed From</span></span>

<span data-ttu-id="353d1-179">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-179">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-180">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-180">Example</span></span>

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="353d1-181">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="353d1-181">nx_ftp_client_delete</span></span>

<span data-ttu-id="353d1-182">Eliminación de una instancia del cliente FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-182">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-183">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-183">Prototype</span></span>

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="353d1-184">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-184">Description</span></span>

<span data-ttu-id="353d1-185">Este servicio elimina una instancia del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-185">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-186">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-186">Input Parameters</span></span>

- <span data-ttu-id="353d1-187">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-187">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-188">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-188">Return Values</span></span>

- <span data-ttu-id="353d1-189">**NX_SUCCESS** (0x00) Cliente FTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-189">**NX_SUCCESS** (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="353d1-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) Cliente FTP no desconectado</span><span class="sxs-lookup"><span data-stu-id="353d1-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) FTP client not disconnected</span></span>
- <span data-ttu-id="353d1-191">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-191">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-192">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-192">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-193">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-193">Allowed From</span></span>

<span data-ttu-id="353d1-194">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-194">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-195">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-195">Example</span></span>

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="353d1-196">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="353d1-196">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="353d1-197">Creación de un directorio en el servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-197">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-198">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-198">Prototype</span></span>

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-199">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-199">Description</span></span>

<span data-ttu-id="353d1-200">Este servicio crea el directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="353d1-200">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-201">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-201">Input Parameters</span></span>

- <span data-ttu-id="353d1-202">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-202">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-203">**directory_name**: nombre del directorio que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="353d1-203">**directory_name** Name of directory to create.</span></span>
- <span data-ttu-id="353d1-204">**wait_option**: define cuánto tiempo va a esperar el servicio para la creación del directorio FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-204">**wait_option** Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="353d1-205">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-205">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-206">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-206">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-208">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-208">Return Values</span></span>

- <span data-ttu-id="353d1-209">**NX_SUCCESS** (0x00) Directorio FTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-209">**NX_SUCCESS** (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="353d1-210">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-210">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="353d1-212">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-212">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-213">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-213">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-214">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-214">Allowed From</span></span>

<span data-ttu-id="353d1-215">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-216">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-216">Example</span></span>

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="353d1-217">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="353d1-217">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="353d1-218">Establecer el directorio predeterminado en el servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-218">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-219">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-219">Prototype</span></span>

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-220">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-220">Description</span></span>

<span data-ttu-id="353d1-221">Este servicio establece el directorio predeterminado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="353d1-221">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="353d1-222">Este directorio predeterminado solo se aplica a la conexión de este cliente.</span><span class="sxs-lookup"><span data-stu-id="353d1-222">This default directory applies only to this client’s connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-223">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-223">Input Parameters</span></span>

- <span data-ttu-id="353d1-224">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-224">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-225">**directory_path**: nombre de la ruta de acceso al directorio que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="353d1-225">**directory_path** Name of directory path to set.</span></span>
- <span data-ttu-id="353d1-226">**wait_option**: define cuánto tiempo va a esperar el servicio para el establecimiento del directorio predeterminado FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-226">**wait_option** Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="353d1-227">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-227">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-228">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-228">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-230">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-230">Return Values</span></span>

- <span data-ttu-id="353d1-231">**NX_SUCCESS** (0x00) Establecimiento predeterminado FTP correcto.</span><span class="sxs-lookup"><span data-stu-id="353d1-231">**NX_SUCCESS** (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="353d1-232">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-232">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="353d1-234">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-234">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-235">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-235">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-236">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-236">Allowed From</span></span>

<span data-ttu-id="353d1-237">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-238">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-238">Example</span></span>

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="353d1-239">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="353d1-239">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="353d1-240">Eliminación de un directorio en el servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-240">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-241">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-241">Prototype</span></span>

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-242">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-242">Description</span></span>

<span data-ttu-id="353d1-243">Este servicio elimina el directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="353d1-243">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-244">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-244">Input Parameters</span></span>

- <span data-ttu-id="353d1-245">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-245">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-246">**directory_name**: nombre del directorio que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="353d1-246">**directory_name** Name of directory to delete.</span></span>
- <span data-ttu-id="353d1-247">**wait_option**: define cuánto tiempo va a esperar el servicio para la eliminación del directorio FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-247">**wait_option** Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="353d1-248">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-248">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-249">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-249">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-251">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-251">Return Values</span></span>

- <span data-ttu-id="353d1-252">**NX_SUCCESS** (0x00) Directorio FTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-252">**NX_SUCCESS** (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="353d1-253">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-253">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="353d1-255">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-255">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-256">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-256">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-257">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-257">Allowed From</span></span>

<span data-ttu-id="353d1-258">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-258">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-259">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-259">Example</span></span>

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="353d1-260">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="353d1-260">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="353d1-261">Obtención de la lista del directorio del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-261">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-262">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-262">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-263">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-263">Description</span></span>

<span data-ttu-id="353d1-264">Este servicio obtiene el contenido del directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="353d1-264">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="353d1-265">El puntero de paquete proporcionado contendrá una o más entradas de directorio.</span><span class="sxs-lookup"><span data-stu-id="353d1-265">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="353d1-266">Cada entrada se separa mediante una combinación \<cr/lf\>.</span><span class="sxs-lookup"><span data-stu-id="353d1-266">Each entry is separated by a \<cr/lf\> combination.</span></span> <span data-ttu-id="353d1-267">Se debe llamar a ***nx_ftp_client_directory_listing_continue*** para completar la operación de obtención del directorio.</span><span class="sxs-lookup"><span data-stu-id="353d1-267">The ***nx_ftp_client_directory_listing_continue*** should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-268">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-268">Input Parameters</span></span>

- <span data-ttu-id="353d1-269">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-269">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-270">**directory_name**: nombre del directorio del que se desea obtener el contenido.</span><span class="sxs-lookup"><span data-stu-id="353d1-270">**directory_name** Name of directory to get contents of.</span></span>
- <span data-ttu-id="353d1-271">**packet_ptr**: puntero al puntero de paquete de destino.</span><span class="sxs-lookup"><span data-stu-id="353d1-271">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="353d1-272">Si la operación se realiza correctamente, la carga de paquete contendrá una o más entradas de directorio.</span><span class="sxs-lookup"><span data-stu-id="353d1-272">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="353d1-273">**wait_option**: define cuánto tiempo va a esperar el servicio para el listado del directorio FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-273">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="353d1-274">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-274">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-275">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-275">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-277">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-277">Return Values</span></span>

- <span data-ttu-id="353d1-278">**NX_SUCCESS** (0x00) Directorio FTP enumerado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-278">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="353d1-279">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-279">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-280">**NX_NOT_ENABLED** (0x14) El servicio (IPv6) no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="353d1-280">**NX_NOT_ENABLED** (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="353d1-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) No obtuvo una respuesta 1XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="353d1-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="353d1-283">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-283">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-284">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-284">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-285">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-285">Allowed From</span></span>

<span data-ttu-id="353d1-286">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-287">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-287">Example</span></span>

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="353d1-288">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="353d1-288">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="353d1-289">Continuación de la lista del directorio del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-289">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-290">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-290">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-291">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-291">Description</span></span>

<span data-ttu-id="353d1-292">Este servicio continúa obteniendo el contenido del directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="353d1-292">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="353d1-293">Debería haber estado inmediatamente precedido por una llamada a ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="353d1-293">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="353d1-294">Si la operación se realiza correctamente, el puntero de paquete proporcionado contendrá una o más entradas de directorio.</span><span class="sxs-lookup"><span data-stu-id="353d1-294">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="353d1-295">Se debe llamar a esta rutina hasta que se reciba un estado NX_FTP_END_OF_LISTING.</span><span class="sxs-lookup"><span data-stu-id="353d1-295">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-296">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-296">Input Parameters</span></span>

- <span data-ttu-id="353d1-297">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-297">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-298">**packet_ptr**: puntero al puntero de paquete de destino.</span><span class="sxs-lookup"><span data-stu-id="353d1-298">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="353d1-299">Si la operación se realiza correctamente, la carga de paquete contendrá una o más entradas de directorio, separadas por <cr/lf>.</span><span class="sxs-lookup"><span data-stu-id="353d1-299">If successful, the packet payload will contain one or more directory entries, separated by a <cr/lf>.</span></span>
- <span data-ttu-id="353d1-300">**wait_option**: define cuánto tiempo va a esperar el servicio para el listado del directorio FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-300">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="353d1-301">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-301">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-302">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-302">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-304">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-304">Return Values</span></span>

- <span data-ttu-id="353d1-305">**NX_SUCCESS** (0x00) Directorio FTP enumerado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-305">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="353d1-306">**NX_FTP_END_OF_LISTING** (0xD8) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="353d1-306">**NX_FTP_END_OF_LISTING** (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="353d1-307">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-307">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="353d1-309">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-309">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-310">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-310">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-311">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-311">Allowed From</span></span>

<span data-ttu-id="353d1-312">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-313">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-313">Example</span></span>

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="353d1-314">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="353d1-314">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="353d1-315">Desconexión del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-315">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-316">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-316">Prototype</span></span>

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-317">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-317">Description</span></span>

<span data-ttu-id="353d1-318">Este servicio desconecta una conexión de servidor FTP establecida previamente con el cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="353d1-318">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-319">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-319">Input Parameters</span></span>

- <span data-ttu-id="353d1-320">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-320">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-321">**wait_option**: define cuánto tiempo va a esperar el servicio para la desconexión del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-321">**wait_option** Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="353d1-322">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-322">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-323">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-323">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-325">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-325">Return Values</span></span>

- <span data-ttu-id="353d1-326">**NX_SUCCESS** (0x00) Desconexión FTP correcta.</span><span class="sxs-lookup"><span data-stu-id="353d1-326">**NX_SUCCESS** (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="353d1-327">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-327">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="353d1-329">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-329">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-330">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-330">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-331">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-331">Allowed From</span></span>

<span data-ttu-id="353d1-332">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-332">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-333">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-333">Example</span></span>

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="353d1-334">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="353d1-334">nx_ftp_client_file_close</span></span>

<span data-ttu-id="353d1-335">Cierre del archivo de cliente</span><span class="sxs-lookup"><span data-stu-id="353d1-335">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-336">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-336">Prototype</span></span>

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-337">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-337">Description</span></span>

<span data-ttu-id="353d1-338">Este servicio cierra un archivo abierto previamente en el servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-338">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-339">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-339">Input Parameters</span></span>

- <span data-ttu-id="353d1-340">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-340">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-341">**wait_option**: define cuánto tiempo va a esperar el servicio para que se cierre el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-341">**wait_option** Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="353d1-342">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-342">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-343">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-343">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-345">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-345">Return Values</span></span>

- <span data-ttu-id="353d1-346">**NX_SUCCESS** (0x00) Archivo FTP cerrado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-346">**NX_SUCCESS** (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="353d1-347">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-347">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-348">**NX_FTP_NOT_OPEN (0xD5)** Archivo no abierto; no se puede cerrar.</span><span class="sxs-lookup"><span data-stu-id="353d1-348">**NX_FTP_NOT_OPEN (0xD5)** File not open; cannot close it</span></span>
- <span data-ttu-id="353d1-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="353d1-350">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-350">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-351">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-351">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-352">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-352">Allowed From</span></span>

<span data-ttu-id="353d1-353">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-354">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-354">Example</span></span>

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="353d1-355">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="353d1-355">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="353d1-356">Eliminación de un archivo del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-356">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-357">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-357">Prototype</span></span>

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-358">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-358">Description</span></span>

<span data-ttu-id="353d1-359">Este servicio elimina el archivo especificado del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-359">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-360">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-360">Input Parameters</span></span>

- <span data-ttu-id="353d1-361">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-361">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-362">**file_name**: nombre del archivo que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="353d1-362">**file_name** Name of file to delete.</span></span>
- <span data-ttu-id="353d1-363">**wait_option**: define cuánto tiempo va a esperar el servicio para que se elimine el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-363">**wait_option** Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="353d1-364">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-364">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-365">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-365">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-367">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-367">Return Values</span></span>

- <span data-ttu-id="353d1-368">**NX_SUCCESS** (0x00) Archivo FTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-368">**NX_SUCCESS** (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="353d1-369">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-369">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="353d1-371">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-371">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-372">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-372">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-373">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-373">Allowed From</span></span>

<span data-ttu-id="353d1-374">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-374">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-375">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-375">Example</span></span>

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="353d1-376">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="353d1-376">nx_ftp_client_file_open</span></span>

<span data-ttu-id="353d1-377">Apertura de un archivo del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-377">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-378">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-378">Prototype</span></span>

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-379">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-379">Description</span></span>

<span data-ttu-id="353d1-380">Este servicio abre el archivo especificado (para lectura o escritura) del servidor FTP previamente conectado a la instancia de cliente especificada.</span><span class="sxs-lookup"><span data-stu-id="353d1-380">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-381">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-381">Input Parameters</span></span>

- <span data-ttu-id="353d1-382">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-382">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-383">**file_name**: nombre del archivo que se va a abrir.</span><span class="sxs-lookup"><span data-stu-id="353d1-383">**file_name** Name of file to open.</span></span>
- <span data-ttu-id="353d1-384">**open_type** **NX_FTP_OPEN_FOR_READ** o **NX_FTP_OPEN_FOR_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="353d1-384">**open_type** Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="353d1-385">**wait_option** Define cuánto tiempo va a esperar el servicio para que se abra el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-385">**wait_option** Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="353d1-386">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-386">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-387">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-387">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-389">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-389">Return Values</span></span>

- <span data-ttu-id="353d1-390">**NX_SUCCESS** (0x00) Archivo FTP abierto correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-390">**NX_SUCCESS** (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="353d1-391">**NX_OPTION_ERROR** (0x0A) Tipo abierto no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-391">**NX_OPTION_ERROR** (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="353d1-392">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-392">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-393">**NX_FTP_NOT_CLOSED** (0xD6) El cliente FTP ya está abierto.</span><span class="sxs-lookup"><span data-stu-id="353d1-393">**NX_FTP_NOT_CLOSED** (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="353d1-394">**NX_NO_FREE_PORTS** (0x45) No hay puertos TCP disponibles para asignar.</span><span class="sxs-lookup"><span data-stu-id="353d1-394">**NX_NO_FREE_PORTS** (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="353d1-395">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-395">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-396">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-396">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-397">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-397">Allowed From</span></span>

<span data-ttu-id="353d1-398">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-399">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-399">Example</span></span>

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="353d1-400">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="353d1-400">nx_ftp_client_file_read</span></span>

<span data-ttu-id="353d1-401">Lectura del archivo</span><span class="sxs-lookup"><span data-stu-id="353d1-401">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-402">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-402">Prototype</span></span>

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-403">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-403">Description</span></span>

<span data-ttu-id="353d1-404">Este servicio lee un paquete de un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-404">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="353d1-405">Se debe llamar repetidamente hasta que se reciba un estado de NX_FTP_END_OF_FILE.</span><span class="sxs-lookup"><span data-stu-id="353d1-405">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="353d1-406">Tenga en cuenta que el autor de la llamada no asigna un paquete para este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-406">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="353d1-407">Solo necesita proporcionar un puntero a un puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="353d1-407">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="353d1-408">Este servicio actualizará ese puntero de paquete para que apunte a un paquete recuperado de la cola de recepción de socket.</span><span class="sxs-lookup"><span data-stu-id="353d1-408">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="353d1-409">Si se devuelve un estado correcto, significa que hay un paquete disponible y es responsabilidad del autor de la llamada liberarlo cuando haya terminado con él.</span><span class="sxs-lookup"><span data-stu-id="353d1-409">If a successful status is returned, that means there was a packet available, and it is the caller’s responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="353d1-410">Si se devuelve un estado distinto de cero (ya sea un estado de error o NX_FTP_END_OF_FILE), el autor de la llamada no libera el paquete.</span><span class="sxs-lookup"><span data-stu-id="353d1-410">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="353d1-411">De lo contrario, se genera un error cuando el puntero del paquete es NULL.</span><span class="sxs-lookup"><span data-stu-id="353d1-411">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-412">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-412">Input Parameters</span></span>

- <span data-ttu-id="353d1-413">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-413">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-414">**packet_ptr**: puntero al destino del puntero de paquete de datos que se va a almacenar.</span><span class="sxs-lookup"><span data-stu-id="353d1-414">**packet_ptr** Pointer to destination for the data packet pointer to be stored.</span></span> <span data-ttu-id="353d1-415">Si es correcto, el paquete contiene parte o todo el archivo.</span><span class="sxs-lookup"><span data-stu-id="353d1-415">If successful, the packet some or all the contains of the file.</span></span>
- <span data-ttu-id="353d1-416">**wait_option**: define cuánto tiempo va a esperar el servicio para que se lea el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-416">**wait_option** Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="353d1-417">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-417">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-418">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-418">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-420">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-420">Return Values</span></span>

- <span data-ttu-id="353d1-421">**NX_SUCCESS** (0x00) Archivo FTP leído correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-421">**NX_SUCCESS** (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="353d1-422">**NX_FTP_NOT_OPEN** (0xD5) El cliente FTP de no está abierto.</span><span class="sxs-lookup"><span data-stu-id="353d1-422">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="353d1-423">**NX_FTP_END_OF_FILE** (0xD7) Fin de la condición del archivo.</span><span class="sxs-lookup"><span data-stu-id="353d1-423">**NX_FTP_END_OF_FILE** (0xD7) End of file condition.</span></span>
- <span data-ttu-id="353d1-424">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-424">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-425">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-425">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-426">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-426">Allowed From</span></span>

<span data-ttu-id="353d1-427">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-428">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-428">Example</span></span>

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

/* Check status.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else
{
    /* Release packet when done with it. */
    nx_packet_release(my_packet);
}

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="353d1-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="353d1-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="353d1-430">Cambio de nombre de un archivo del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-431">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-431">Prototype</span></span>

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-432">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-432">Description</span></span>

<span data-ttu-id="353d1-433">Este servicio cambia el nombre de un archivo en el servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-434">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-434">Input Parameters</span></span>

- <span data-ttu-id="353d1-435">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-435">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-436">**filename**: nombre actual del archivo.</span><span class="sxs-lookup"><span data-stu-id="353d1-436">**filename** Current name of file.</span></span>
- <span data-ttu-id="353d1-437">**new_filename**: nuevo nombre del archivo.</span><span class="sxs-lookup"><span data-stu-id="353d1-437">**new_filename** New name for file.</span></span>
- <span data-ttu-id="353d1-438">**wait_option**: define cuánto tiempo va a esperar el servicio para que se cambie el nombre al archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-438">**wait_option** Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="353d1-439">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-440">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-440">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-442">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-442">Return Values</span></span>

- <span data-ttu-id="353d1-443">**NX_SUCCESS** (0x00) Nombre del archivo FTP cambiado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-443">**NX_SUCCESS** (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="353d1-444">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="353d1-444">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="353d1-445">**NX_FTP_EXPECTED_3XX_CODE** (0xDD) No recibió una respuesta 3XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="353d1-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="353d1-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="353d1-447">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-447">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-448">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-448">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-449">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-449">Allowed From</span></span>

<span data-ttu-id="353d1-450">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-450">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-451">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-451">Example</span></span>

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="353d1-452">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="353d1-452">nx_ftp_client_file_write</span></span>

<span data-ttu-id="353d1-453">Escritura en un archivo</span><span class="sxs-lookup"><span data-stu-id="353d1-453">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-454">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-454">Prototype</span></span>

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="353d1-455">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-455">Description</span></span>

<span data-ttu-id="353d1-456">Este servicio escribe un paquete de datos en el archivo abierto previamente en el servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-456">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-457">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-457">Input Parameters</span></span>

- <span data-ttu-id="353d1-458">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-458">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-459">**packet_ptr**: puntero de paquete que contiene los datos que se van a escribir.</span><span class="sxs-lookup"><span data-stu-id="353d1-459">**packet_ptr** Packet pointer containing data to write.</span></span>
- <span data-ttu-id="353d1-460">**wait_option**: define cuánto tiempo va a esperar el servicio para que se escriba el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-460">**wait_option** Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="353d1-461">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="353d1-461">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="353d1-462">**timeout value** (de 0x00000001 a 0xFFFFFFFE) Al seleccionar un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics de temporizador que permanecerá suspendido esperando la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-462">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="353d1-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="353d1-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-464">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-464">Return Values</span></span>

- <span data-ttu-id="353d1-465">**NX_SUCCESS** (0x00) Archivo FTP escrito correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-465">**NX_SUCCESS** (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="353d1-466">**NX_FTP_NOT_OPEN** (0xD5) El cliente FTP de no está abierto.</span><span class="sxs-lookup"><span data-stu-id="353d1-466">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="353d1-467">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-467">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-468">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-469">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-469">Allowed From</span></span>

<span data-ttu-id="353d1-470">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-471">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-471">Example</span></span>

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="353d1-472">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="353d1-472">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="353d1-473">Habilitación o deshabilitación del modo de transferencia pasiva</span><span class="sxs-lookup"><span data-stu-id="353d1-473">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-474">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-474">Prototype</span></span>

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="353d1-475">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-475">Description</span></span>

<span data-ttu-id="353d1-476">Este servicio habilita el modo de transferencia pasivo si la entrada passive_mode_enabled está establecida en NX_TRUE en una instancia de cliente FTP creada anteriormente, de modo que las llamadas subsiguientes para leer o escribir archivos (RETR, STOR) o descargar un listado del directorio (NLST) se realizan en modo de transferencia.</span><span class="sxs-lookup"><span data-stu-id="353d1-476">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="353d1-477">Para deshabilitar la transferencia del modo pasivo y volver al comportamiento predeterminado del modo de transferencia activa, llame a esta función con la entrada passive_mode_enabled establecida en NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="353d1-477">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-478">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-478">Input Parameters</span></span>

- <span data-ttu-id="353d1-479">**ftp_client_ptr**: puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-479">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="353d1-480">**passive_mode_enabled** Si se establece en NX_TRUE, se habilita el modo pasivo.</span><span class="sxs-lookup"><span data-stu-id="353d1-480">**passive_mode_enabled** If set to NX_TRUE, passive mode is enabled.</span></span><br /><span data-ttu-id="353d1-481">Si se establece en NX_FALSE, el modo pasivo se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="353d1-481">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-482">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-482">Return Values</span></span>

- <span data-ttu-id="353d1-483">**NX_SUCCESS** (0x00) Modo pasivo establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-483">**NX_SUCCESS** (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="353d1-484">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-484">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-485">NX_INVALID_PARAMETERS (0x4D) Entrada que no es de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="353d1-485">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-486">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-486">Allowed From</span></span>

<span data-ttu-id="353d1-487">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-488">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-488">Example</span></span>

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="353d1-489">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="353d1-489">nx_ftp_server_create</span></span>

<span data-ttu-id="353d1-490">Creación del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-490">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-491">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-491">Prototype</span></span>

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="353d1-492">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-492">Description</span></span>

<span data-ttu-id="353d1-493">Este servicio crea una instancia del servidor FTP en la instancia de IP NetX especificada y creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="353d1-493">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="353d1-494">Tenga en cuenta que el servidor FTP debe iniciarse con una llamada a ***nx_ftp_server_start*** para que inicie la operación.</span><span class="sxs-lookup"><span data-stu-id="353d1-494">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-495">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-495">Input Parameters</span></span>

- <span data-ttu-id="353d1-496">**ftp_server_ptr**: puntero al bloque de control del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-496">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="353d1-497">**ftp_server_name**: nombre del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-497">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="353d1-498">**ip_ptr**: puntero a la instancia de IP de NetX asociada.</span><span class="sxs-lookup"><span data-stu-id="353d1-498">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="353d1-499">Tenga en cuenta que solo puede haber un servidor FTP para una instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="353d1-499">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="353d1-500">**media_ptr**: puntero a la instancia multimedia de FileX.</span><span class="sxs-lookup"><span data-stu-id="353d1-500">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="353d1-501">**stack_ptr**: puntero a la memoria para el área de pila del subproceso del servidor FTP interno.</span><span class="sxs-lookup"><span data-stu-id="353d1-501">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="353d1-502">**stack_size** Tamaño del área de pila especificado por *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="353d1-502">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="353d1-503">**pool_ptr**: puntero al grupo de paquetes de NetX.</span><span class="sxs-lookup"><span data-stu-id="353d1-503">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="353d1-504">Tenga en cuenta que el tamaño de carga de los paquetes del grupo debe ser lo suficientemente grande como para alojar el nombre de archivo o la ruta de acceso más grande.</span><span class="sxs-lookup"><span data-stu-id="353d1-504">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="353d1-505">**ftp_login**: puntero de función a la función de inicio de sesión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="353d1-505">**ftp_login** Function pointer to application’s login function.</span></span> <span data-ttu-id="353d1-506">A esta función se le proporcionan el nombre de usuario y la contraseña del cliente que solicita una conexión y la dirección del cliente en el tipo de datos ULONG.</span><span class="sxs-lookup"><span data-stu-id="353d1-506">This function is supplied the username and password from the Client requesting a connection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="353d1-507">Si resulta válido, la función de inicio de sesión de la aplicación debe devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="353d1-507">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="353d1-508">**ftp_logout**: puntero de función a la función de cierre de sesión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="353d1-508">**ftp_logout** Function pointer to application’s logout function.</span></span> <span data-ttu-id="353d1-509">A esta función se le proporcionan el nombre de usuario y la contraseña del cliente que solicita una desconexión y la dirección del cliente en el tipo de datos ULONG.</span><span class="sxs-lookup"><span data-stu-id="353d1-509">This function is supplied the username and password from the Client requesting a disconnection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="353d1-510">Si resulta válido, la función de inicio de sesión de la aplicación debe devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="353d1-510">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-511">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-511">Return Values</span></span>

- <span data-ttu-id="353d1-512">**NX_SUCCESS** (0x00) Servidor FTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-512">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="353d1-513">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-513">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-514">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-514">Allowed From</span></span>

<span data-ttu-id="353d1-515">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-515">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-516">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-516">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a><span data-ttu-id="353d1-517">nxd_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="353d1-517">nxd_ftp_server_create</span></span>

<span data-ttu-id="353d1-518">Creación del servidor FTP con compatibilidad con IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="353d1-518">Create FTP Server with IPv4 and IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-519">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-519">Prototype</span></span>

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="353d1-520">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-520">Description</span></span>

<span data-ttu-id="353d1-521">Este servicio crea una instancia del servidor FTP en la instancia de IP NetX especificada y creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="353d1-521">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="353d1-522">Tenga en cuenta que el servidor FTP todavía debe iniciarse con una llamada a ***nx_ftp_server_start*** para que inicie la operación después de que se cree el servidor.</span><span class="sxs-lookup"><span data-stu-id="353d1-522">Note the FTP Server still needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation after the Server is created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-523">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-523">Input Parameters</span></span>

- <span data-ttu-id="353d1-524">**ftp_server_ptr**: puntero al bloque de control del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-524">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="353d1-525">**ftp_server_name**: nombre del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-525">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="353d1-526">**ip_ptr**: puntero a la instancia de IP de NetX asociada.</span><span class="sxs-lookup"><span data-stu-id="353d1-526">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="353d1-527">Tenga en cuenta que solo puede haber un servidor FTP para una instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="353d1-527">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="353d1-528">**media_ptr**: puntero a la instancia multimedia de FileX.</span><span class="sxs-lookup"><span data-stu-id="353d1-528">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="353d1-529">**stack_ptr**: puntero a la memoria para el área de pila del subproceso del servidor FTP interno.</span><span class="sxs-lookup"><span data-stu-id="353d1-529">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="353d1-530">**stack_size** Tamaño del área de pila especificado por *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="353d1-530">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="353d1-531">**pool_ptr**: puntero al grupo de paquetes de NetX.</span><span class="sxs-lookup"><span data-stu-id="353d1-531">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="353d1-532">Tenga en cuenta que el tamaño de carga de los paquetes del grupo debe ser lo suficientemente grande como para alojar el nombre de archivo o la ruta de acceso más grande.</span><span class="sxs-lookup"><span data-stu-id="353d1-532">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="353d1-533">**ftp_login_duo**: puntero de función a la función de inicio de sesión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="353d1-533">**ftp_login_duo** Function pointer to application’s login function.</span></span> <span data-ttu-id="353d1-534">A esta función se le proporcionan el nombre de usuario y la contraseña del cliente que solicita una conexión y un puntero a la dirección del cliente en el tipo de datos NXD_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="353d1-534">This function is supplied the username and password from the Client requesting a connection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="353d1-535">Si resulta válido, la función de inicio de sesión de la aplicación debe devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="353d1-535">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="353d1-536">**ftp_logout_duo**: puntero de función a la función de cierre de sesión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="353d1-536">**ftp_logout_duo** Function pointer to application’s logout function.</span></span> <span data-ttu-id="353d1-537">A esta función se le proporcionan el nombre de usuario y la contraseña del cliente que solicita una desconexión y un puntero a la dirección del cliente en el tipo de datos NXD_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="353d1-537">This function is supplied the username and password from the Client requesting a disconnection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="353d1-538">Si resulta válido, la función de inicio de sesión de la aplicación debe devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="353d1-538">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-539">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-539">Return Values</span></span>

- <span data-ttu-id="353d1-540">**NX_SUCCESS** (0x00) Servidor FTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-540">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="353d1-541">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-541">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-542">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-542">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-543">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-543">Allowed From</span></span>

<span data-ttu-id="353d1-544">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-544">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-545">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-545">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="353d1-546">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="353d1-546">nx_ftp_server_delete</span></span>

<span data-ttu-id="353d1-547">Eliminación del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-547">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-548">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-548">Prototype</span></span>

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="353d1-549">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-549">Description</span></span>

<span data-ttu-id="353d1-550">Este servicio elimina una instancia de servidor FTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="353d1-550">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-551">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-551">Input Parameters</span></span>

- <span data-ttu-id="353d1-552">**ftp_server_ptr**: puntero al bloque de control del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-552">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-553">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-553">Return Values</span></span>

- <span data-ttu-id="353d1-554">**NX_SUCCESS** (0x00) Servidor FTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-554">**NX_SUCCESS** (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="353d1-555">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-555">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-556">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-556">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-557">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-557">Allowed From</span></span>

<span data-ttu-id="353d1-558">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-558">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-559">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-559">Example</span></span>

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="353d1-560">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="353d1-560">nx_ftp_server_start</span></span>

<span data-ttu-id="353d1-561">Inicio del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-561">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-562">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-562">Prototype</span></span>

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="353d1-563">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-563">Description</span></span>

<span data-ttu-id="353d1-564">Este servicio inicia una instancia de servidor FTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="353d1-564">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-565">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-565">Input Parameters</span></span>

- <span data-ttu-id="353d1-566">**ftp_server_ptr**: puntero al bloque de control del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-566">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-567">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-567">Return Values</span></span>

- <span data-ttu-id="353d1-568">**NX_SUCCESS** (0x00) Servidor FTP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-568">**NX_SUCCESS** (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="353d1-569">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-569">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-570">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-570">Allowed From</span></span>

<span data-ttu-id="353d1-571">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-571">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-572">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-572">Example</span></span>

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="353d1-573">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="353d1-573">nx_ftp_server_stop</span></span>

<span data-ttu-id="353d1-574">Detención del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="353d1-574">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="353d1-575">Prototipo</span><span class="sxs-lookup"><span data-stu-id="353d1-575">Prototype</span></span>

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="353d1-576">Descripción</span><span class="sxs-lookup"><span data-stu-id="353d1-576">Description</span></span>

<span data-ttu-id="353d1-577">Este servicio detiene una instancia de servidor FTP iniciada y creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="353d1-577">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="353d1-578">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="353d1-578">Input Parameters</span></span>

- <span data-ttu-id="353d1-579">**ftp_server_ptr**: puntero al bloque de control del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="353d1-579">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="353d1-580">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="353d1-580">Return Values</span></span>

- <span data-ttu-id="353d1-581">**NX_SUCCESS** (0x00) Servidor FTP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="353d1-581">**NX_SUCCESS** (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="353d1-582">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="353d1-582">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="353d1-583">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="353d1-583">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="353d1-584">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="353d1-584">Allowed From</span></span>

<span data-ttu-id="353d1-585">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="353d1-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="353d1-586">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="353d1-586">Example</span></span>

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
