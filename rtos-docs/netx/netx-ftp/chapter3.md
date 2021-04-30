---
title: 'Capítulo 3: Descripción de los servicios de Azure RTOS NetX FTP'
description: Este capítulo contiene una descripción de todos los servicios DNS de Azure RTOS NetX FTP (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b05d03c45607c45acf32474cf8e40861532c5fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815201"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a><span data-ttu-id="0dd3b-103">Capítulo 3: Descripción de los servicios de Azure RTOS NetX FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-103">Chapter 3 - Description of Azure RTOS NetX FTP services</span></span>

<span data-ttu-id="0dd3b-104">Este capítulo contiene una descripción de todos los servicios DNS de Azure RTOS NetX FTP (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-104">This chapter contains a description of all Azure RTOS NetX FTP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="0dd3b-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0dd3b-106">**nx_ftp_client_connect**: *permite conectarse a un servidor FTP*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-106">**nx_ftp_client_connect**: *Connect to FTP Server*</span></span>
- <span data-ttu-id="0dd3b-107">**nx_ftp_client_create**: *permite crear una instancia de cliente FTP*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-107">**nx_ftp_client_create**: *Create an FTP Client instance*</span></span>
- <span data-ttu-id="0dd3b-108">**nx_ftp_client_delete**: *permite eliminar una instancia de cliente FTP*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-108">**nx_ftp_client_delete**: *Delete an FTP Client instance*</span></span>
- <span data-ttu-id="0dd3b-109">**nx_ftp_client_directory_create**: *permite crear un directorio en el servidor*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-109">**nx_ftp_client_directory_create**: *Create a directory on Server*</span></span>
- <span data-ttu-id="0dd3b-110">**nx_ftp_client_directory_default_set**: *permite establecer un directorio predeterminado en el servidor*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-110">**nx_ftp_client_directory_default_set**: *Set default directory on Server*</span></span>
- <span data-ttu-id="0dd3b-111">**nx_ftp_client_directory_delete**: *permite eliminar un directorio en el servidor*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-111">**nx_ftp_client_directory_delete**: *Delete a directory on Server*</span></span>
- <span data-ttu-id="0dd3b-112">**nx_ftp_client_directory_listing_get**: *permite obtener la lista de directorios desde el servidor*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-112">**nx_ftp_client_directory_listing_get**: *Get directory listing from Server*</span></span>
- <span data-ttu-id="0dd3b-113">**nx_ftp_client_directory_listing_continue**: *permite continuar la lista de directorios desde el servidor*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-113">**nx_ftp_client_directory_listing_continue**: *Continue directory listing from Server*</span></span>
- <span data-ttu-id="0dd3b-114">**nx_ftp_client_disconnect**: *permite desconectarse del servidor FTP*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-114">**nx_ftp_client_disconnect**: *Disconnect from FTP Server*</span></span>
- <span data-ttu-id="0dd3b-115">**nx_ftp_client_file_close**: *permite cerrar el archivo de cliente*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-115">**nx_ftp_client_file_close**: *Close Client file*</span></span>
- <span data-ttu-id="0dd3b-116">**nx_ftp_client_file_delete**: *permite eliminar el archivo en el servidor*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-116">**nx_ftp_client_file_delete**: *Delete file on Server*</span></span>
- <span data-ttu-id="0dd3b-117">**nx_ftp_client_file_open**: *permite abrir el archivo de cliente*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-117">**nx_ftp_client_file_open**: *Open Client file*</span></span>
- <span data-ttu-id="0dd3b-118">**nx_ftp_client_file_read**: *permite leer del archivo*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-118">**nx_ftp_client_file_read**: *Read from file*</span></span>
- <span data-ttu-id="0dd3b-119">**nx_ftp_client_file_rename**: *permite cambiar el nombre en el servidor*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-119">**nx_ftp_client_file_rename**: *Rename file on Server*</span></span>
- <span data-ttu-id="0dd3b-120">**nx_ftp_client_file_write**: *permite escribir en el archivo*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-120">**nx_ftp_client_file_write**: *Write to file*</span></span>
- <span data-ttu-id="0dd3b-121">**nx_ftp_server_create**: *permite crear el servidor FTP*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-121">**nx_ftp_server_create**: *Create FTP Server*</span></span>
- <span data-ttu-id="0dd3b-122">**nx_ftp_server_delete**: *permite eliminar el servidor FTP*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-122">**nx_ftp_server_delete**: *Delete FTP Server*</span></span>
- <span data-ttu-id="0dd3b-123">**nx_ftp_server_start**: *permite iniciar el servidor FTP*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-123">**nx_ftp_server_start**: *Start FTP Server*</span></span>
- <span data-ttu-id="0dd3b-124">**nx_ftp_server_stop**: *permite detener el servidor FTP*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-124">**nx_ftp_server_stop**: *Stop FTP Server*</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="0dd3b-125">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="0dd3b-125">nx_ftp_client_connect</span></span>

<span data-ttu-id="0dd3b-126">Conexión a un servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-126">Connect to an FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-127">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-127">Prototype</span></span>

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-128">Description</span></span>

<span data-ttu-id="0dd3b-129">Este servicio conecta la instancia del cliente FTP creada anteriormente al servidor FTP en la dirección IP suministrada.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-129">This service connects the previously created FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-130">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-130">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-131">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-131">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-132">**server_ip**: Dirección IP del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-132">**server_ip**: IP address of FTP Server.</span></span>
- <span data-ttu-id="0dd3b-133">**username**: Nombre de usuario del cliente para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-133">**username**: Client username for authentication.</span></span>
- <span data-ttu-id="0dd3b-134">**password**: Contraseña del cliente para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-134">**password**: Client password for authentication.</span></span>
- <span data-ttu-id="0dd3b-135">**wait_option**: define cuánto tiempo va a esperar el servicio para la conexión del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-135">**wait_option**: Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="0dd3b-136">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-136">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-137">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-137">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-138">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-139">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-139">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-140">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-140">Return Values</span></span>

- <span data-ttu-id="0dd3b-141">**NX_SUCCESS** (0x00) Conexión FTP correcta.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-141">**NX_SUCCESS**: (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="0dd3b-142">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) No recibió una respuesta 22X (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="0dd3b-143">**NX_FTP_EXPECTED_23X_CODE** (0xDC) No recibió una respuesta 23X (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="0dd3b-144">**NX_FTP_EXPECTED_33X_CODE** (0xDE) No recibió una respuesta 33X (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="0dd3b-145">**NX_FTP_NOT_DISCONNECTED** (0xD4) El cliente ya está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="0dd3b-146">NX_PTR_ERROR (0x07) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-146">NX_PTR_ERROR: (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="0dd3b-147">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-147">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0dd3b-148">NX_IP_ADDRESS_ERROR (0x21) Dirección IP no válida.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-148">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-149">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-149">Allowed From</span></span>

<span data-ttu-id="0dd3b-150">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-150">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-151">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-151">Example</span></span>

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a><span data-ttu-id="0dd3b-152">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="0dd3b-152">nx_ftp_client_create</span></span>

<span data-ttu-id="0dd3b-153">Creación de una instancia del cliente FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-153">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-154">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-154">Prototype</span></span>

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0dd3b-155">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-155">Description</span></span>

<span data-ttu-id="0dd3b-156">Este servicio crea una instancia del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-156">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-157">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-157">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-158">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-158">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-159">**ftp_client_name**: Nombre del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-159">**ftp_client_name**: Name of FTP Client.</span></span>
- <span data-ttu-id="0dd3b-160">**ip_ptr**: Puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-160">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0dd3b-161">**window_size**: Tamaño de ventana anunciado para sockets TCP de este cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-161">**window_size**: Advertised window size for TCP socket of this FTP Client.</span></span>
- <span data-ttu-id="0dd3b-162">**pool_ptr**: Puntero al grupo de paquetes predeterminado para este cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-162">**pool_ptr**: Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="0dd3b-163">Tenga en cuenta que la carga mínima de paquete debe ser lo suficientemente grande como para contener la ruta de acceso completa y el nombre de archivo o directorio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-163">Note that the minimum packet payload must be large enough to hold complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-164">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-164">Return Values</span></span>

- <span data-ttu-id="0dd3b-165">**NX_SUCCESS** (0x00) Cliente FTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-165">**NX_SUCCESS**: (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="0dd3b-166">NX_PTR_ERROR (0x16) Puntero FTP, de puntero IP o de grupo de paquetes no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-166">NX_PTR_ERROR: (0x16) Invalid FTP, IP pointer, or packet pool pointer.</span></span> <span data-ttu-id="0dd3b-167">puntero de contraseña.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-167">password pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-168">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-168">Allowed From</span></span>

<span data-ttu-id="0dd3b-169">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-169">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-170">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-170">Example</span></span>

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="0dd3b-171">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="0dd3b-171">nx_ftp_client_delete</span></span>

<span data-ttu-id="0dd3b-172">Eliminación de una instancia del cliente FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-172">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-173">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-173">Prototype</span></span>

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="0dd3b-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-174">Description</span></span>

<span data-ttu-id="0dd3b-175">Este servicio elimina una instancia del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-175">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-176">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-176">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-177">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-177">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-178">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-178">Return Values</span></span>

- <span data-ttu-id="0dd3b-179">**NX_SUCCESS**: (0x00) Cliente FTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-179">**NX_SUCCESS**: (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="0dd3b-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) Error de eliminación del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP Client delete error.</span></span>
- <span data-ttu-id="0dd3b-181">NX_PTR_ERROR (0x16) El puntero FTP no es válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-181">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-182">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-182">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-183">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-183">Allowed From</span></span>

<span data-ttu-id="0dd3b-184">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-185">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-185">Example</span></span>

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="0dd3b-186">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="0dd3b-186">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="0dd3b-187">Creación de un directorio en el servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-187">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-188">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-188">Prototype</span></span>

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-189">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-189">Description</span></span>

<span data-ttu-id="0dd3b-190">Este servicio crea el directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-190">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-191">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-191">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-192">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-192">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-193">**directory_name**: Nombre del directorio que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-193">**directory_name**: Name of directory to create.</span></span>
- <span data-ttu-id="0dd3b-194">**wait_option**: Define cuánto tiempo va a esperar el servicio para la creación del directorio FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-194">**wait_option**: Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="0dd3b-195">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-195">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-196">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-196">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-197">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-198">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-198">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-199">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-199">Return Values</span></span>

- <span data-ttu-id="0dd3b-200">**NX_SUCCESS** (0x00) Directorio FTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-200">**NX_SUCCESS**: (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="0dd3b-201">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-201">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-202">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="0dd3b-203">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-203">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="0dd3b-204">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-205">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-205">Allowed From</span></span>

<span data-ttu-id="0dd3b-206">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-206">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-207">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-207">Example</span></span>

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="0dd3b-208">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="0dd3b-208">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="0dd3b-209">Establecimiento el directorio predeterminado en el servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-209">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-210">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-210">Prototype</span></span>

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-211">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-211">Description</span></span>

<span data-ttu-id="0dd3b-212">Este servicio establece el directorio predeterminado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-212">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="0dd3b-213">Este directorio predeterminado solo se aplica a la conexión de este cliente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-213">This default directory applies only to this client's connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-214">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-214">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-215">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-215">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-216">**directory_path**: Nombre de la ruta de acceso al directorio que se va a establecer.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-216">**directory_path**: Name of directory path to set.</span></span>
- <span data-ttu-id="0dd3b-217">**wait_option**: Define cuánto tiempo va a esperar el servicio para el establecimiento del directorio predeterminado FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-217">**wait_option**: Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="0dd3b-218">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-218">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-219">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-219">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-220">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-221">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-221">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-222">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-222">Return Values</span></span>

- <span data-ttu-id="0dd3b-223">**NX_SUCCESS** (0x00) Establecimiento predeterminado FTP correcto.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-223">**NX_SUCCESS**: (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="0dd3b-224">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-224">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-225">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="0dd3b-226">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-226">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="0dd3b-227">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-227">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-228">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-228">Allowed From</span></span>

<span data-ttu-id="0dd3b-229">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-230">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-230">Example</span></span>

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="0dd3b-231">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="0dd3b-231">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="0dd3b-232">Eliminación de un directorio en el servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-232">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-233">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-233">Prototype</span></span>

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-234">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-234">Description</span></span>

<span data-ttu-id="0dd3b-235">Este servicio elimina el directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-235">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-236">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-236">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-237">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-237">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-238">**directory_name**: Nombre del directorio que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-238">**directory_name**: Name of directory to delete.</span></span>
- <span data-ttu-id="0dd3b-239">**wait_option**: Define cuánto tiempo va a esperar el servicio para la eliminación del directorio FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-239">**wait_option**: Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="0dd3b-240">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-240">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-241">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-241">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-242">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-243">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-243">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-244">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-244">Return Values</span></span>

- <span data-ttu-id="0dd3b-245">**NX_SUCCESS** (0x00) Directorio FTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-245">**NX_SUCCESS**: (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="0dd3b-246">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-246">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-247">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="0dd3b-248">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-248">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="0dd3b-249">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-249">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-250">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-250">Allowed From</span></span>

<span data-ttu-id="0dd3b-251">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-252">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-252">Example</span></span>

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="0dd3b-253">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="0dd3b-253">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="0dd3b-254">Obtención de la lista del directorio del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-254">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-255">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-255">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-256">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-256">Description</span></span>

<span data-ttu-id="0dd3b-257">Este servicio obtiene el contenido del directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-257">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="0dd3b-258">El puntero de paquete proporcionado contendrá una o más entradas de directorio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-258">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="0dd3b-259">Cada entrada se separa mediante una combinación &lt;cr/lf\.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-259">Each entry is separated by a &lt;cr/lf\combination.</span></span> <span data-ttu-id="0dd3b-260">Se debe llamar a ***nx_ftp_client_directory_listing_continue*** para completar la operación de obtención del directorio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-260">The ***nx_ftp_client_directory_listing_continue***: should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-261">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-261">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-262">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-262">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-263">**directory_name**: Nombre del directorio del que se desea obtener el contenido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-263">**directory_name**: Name of directory to get contents of.</span></span>
- <span data-ttu-id="0dd3b-264">**packet_ptr**: Puntero al puntero de paquete de destino.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-264">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="0dd3b-265">Si la operación se realiza correctamente, la carga de paquete contendrá una o más entradas de directorio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-265">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="0dd3b-266">**wait_option**: Define cuánto tiempo va a esperar el servicio para el listado del directorio FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-266">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="0dd3b-267">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-267">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-268">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-268">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-269">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-270">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-270">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-271">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-271">Return Values</span></span>

- <span data-ttu-id="0dd3b-272">**NX_SUCCESS** (0x00) Directorio FTP enumerado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-272">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="0dd3b-273">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-273">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-274">**NX_NOT_ENABLED** (0x14) El servicio (IPv6) no está habilitado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-274">**NX_NOT_ENABLED**: (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="0dd3b-275">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) No obtuvo una respuesta 1XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="0dd3b-276">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0dd3b-277">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-277">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-278">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-278">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-279">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-279">Allowed From</span></span>

<span data-ttu-id="0dd3b-280">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-281">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-281">Example</span></span>

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="0dd3b-282">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="0dd3b-282">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="0dd3b-283">Continuación de la lista del directorio del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-283">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-284">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-284">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-285">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-285">Description</span></span>

<span data-ttu-id="0dd3b-286">Este servicio continúa obteniendo el contenido del directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-286">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="0dd3b-287">Debería haber estado inmediatamente precedido por una llamada a ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-287">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="0dd3b-288">Si la operación se realiza correctamente, el puntero de paquete proporcionado contendrá una o más entradas de directorio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-288">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="0dd3b-289">Se debe llamar a esta rutina hasta que se reciba un estado NX_FTP_END_OF_LISTING.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-289">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-290">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-290">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-291">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-291">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-292">**packet_ptr**: Puntero al puntero de paquete de destino.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-292">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="0dd3b-293">Si la operación se realiza correctamente, la carga de paquete contendrá una o más entradas de directorio, separadas por &lt;cr/lf&gt;.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-293">If successful, the packet payload will contain one or more directory entries, separated by a &lt;cr/lf&gt;.</span></span>
- <span data-ttu-id="0dd3b-294">**wait_option**: Define cuánto tiempo va a esperar el servicio para el listado del directorio FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-294">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="0dd3b-295">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-295">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-296">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-296">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-297">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-298">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-298">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-299">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-299">Return Values</span></span>

- <span data-ttu-id="0dd3b-300">**NX_SUCCESS** (0x00) Directorio FTP enumerado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-300">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="0dd3b-301">**NX_FTP_END_OF_LISTING** (0xD8) No hay más entradas en este directorio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-301">**NX_FTP_END_OF_LISTING**: (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="0dd3b-302">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-302">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0dd3b-304">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-304">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-305">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-305">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-306">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-306">Allowed From</span></span>

<span data-ttu-id="0dd3b-307">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-308">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-308">Example</span></span>

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="0dd3b-309">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="0dd3b-309">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="0dd3b-310">Desconexión del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-310">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-311">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-311">Prototype</span></span>

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-312">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-312">Description</span></span>

<span data-ttu-id="0dd3b-313">Este servicio desconecta una conexión de servidor FTP establecida previamente con el cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-313">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-314">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-314">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-315">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-315">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-316">**wait_option**: Define cuánto tiempo va a esperar el servicio para la desconexión del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-316">**wait_option**: Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="0dd3b-317">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-317">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-318">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-318">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-319">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-320">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-321">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-321">Return Values</span></span>

- <span data-ttu-id="0dd3b-322">**NX_SUCCESS** (0x00) Desconexión FTP correcta.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-322">**NX_SUCCESS**: (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="0dd3b-323">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-323">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-324">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0dd3b-325">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-325">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-326">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-327">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-327">Allowed From</span></span>

<span data-ttu-id="0dd3b-328">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-329">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-329">Example</span></span>

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="0dd3b-330">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="0dd3b-330">nx_ftp_client_file_close</span></span>

<span data-ttu-id="0dd3b-331">Cierre del archivo de cliente</span><span class="sxs-lookup"><span data-stu-id="0dd3b-331">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-332">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-332">Prototype</span></span>

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-333">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-333">Description</span></span>

<span data-ttu-id="0dd3b-334">Este servicio cierra un archivo abierto previamente en el servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-334">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-335">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-335">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-336">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-336">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-337">**wait_option**: Define cuánto tiempo va a esperar el servicio para que se cierre el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-337">**wait_option**: Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="0dd3b-338">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-338">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-339">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-339">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-340">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-341">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-341">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-342">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-342">Return Values</span></span>

- <span data-ttu-id="0dd3b-343">**NX_SUCCESS** (0x00) Archivo FTP cerrado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-343">**NX_SUCCESS**: (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="0dd3b-344">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-344">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-345">**NX_FTP_NOT_OPEN (0xD5)** Archivo no abierto; no se puede cerrar.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-345">**NX_FTP_NOT_OPEN (0xD5)**: File not open; cannot close it</span></span>
- <span data-ttu-id="0dd3b-346">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0dd3b-347">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-347">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-348">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-348">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-349">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-349">Allowed From</span></span>

<span data-ttu-id="0dd3b-350">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-351">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-351">Example</span></span>

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="0dd3b-352">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="0dd3b-352">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="0dd3b-353">Eliminación de un archivo del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-353">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-354">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-354">Prototype</span></span>

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-355">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-355">Description</span></span>

<span data-ttu-id="0dd3b-356">Este servicio elimina el archivo especificado del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-356">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-357">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-357">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-358">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-358">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-359">**file_name**: Nombre del archivo que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-359">**file_name**: Name of file to delete.</span></span>
- <span data-ttu-id="0dd3b-360">**wait_option**: Define cuánto tiempo va a esperar el servicio para que se elimine el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-360">**wait_option**: Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="0dd3b-361">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-361">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-362">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-362">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-363">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-364">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-364">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-365">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-365">Return Values</span></span>

- <span data-ttu-id="0dd3b-366">**NX_SUCCESS** (0x00) Archivo FTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-366">**NX_SUCCESS**: (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="0dd3b-367">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-367">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-368">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0dd3b-369">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-369">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-370">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-371">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-371">Allowed From</span></span>

<span data-ttu-id="0dd3b-372">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-373">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-373">Example</span></span>

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="0dd3b-374">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="0dd3b-374">nx_ftp_client_file_open</span></span>

<span data-ttu-id="0dd3b-375">Apertura de un archivo del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-375">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-376">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-376">Prototype</span></span>

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-377">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-377">Description</span></span>

<span data-ttu-id="0dd3b-378">Este servicio abre el archivo especificado (para lectura o escritura) del servidor FTP previamente conectado a la instancia de cliente especificada.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-378">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-379">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-379">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-380">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-380">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-381">**file_name**: Nombre del archivo que se va a abrir.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-381">**file_name**: Name of file to open.</span></span>
- <span data-ttu-id="0dd3b-382">**open_type**: **NX_FTP_OPEN_FOR_READ** o **NX_FTP_OPEN_FOR_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-382">**open_type**: Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="0dd3b-383">**wait_option**: Define cuánto tiempo va a esperar el servicio para que se abra el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-383">**wait_option**: Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="0dd3b-384">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-384">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-385">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-385">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-386">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-387">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-387">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-388">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-388">Return Values</span></span>

- <span data-ttu-id="0dd3b-389">**NX_SUCCESS** (0x00) Archivo FTP abierto correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-389">**NX_SUCCESS**: (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="0dd3b-390">**NX_OPTION_ERROR** (0x0A) Tipo abierto no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-390">**NX_OPTION_ERROR**: (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="0dd3b-391">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-391">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-392">**NX_FTP_NOT_CLOSED** (0xD6) El cliente FTP ya está abierto.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-392">**NX_FTP_NOT_CLOSED**: (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="0dd3b-393">**NX_NO_FREE_PORTS** (0x45) No hay puertos TCP disponibles para asignar.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-393">**NX_NO_FREE_PORTS**: (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="0dd3b-394">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-394">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-395">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-395">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-396">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-396">Allowed From</span></span>

<span data-ttu-id="0dd3b-397">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-398">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-398">Example</span></span>

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="0dd3b-399">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="0dd3b-399">nx_ftp_client_file_read</span></span>

<span data-ttu-id="0dd3b-400">Lectura del archivo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-400">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-401">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-401">Prototype</span></span>

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-402">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-402">Description</span></span>

<span data-ttu-id="0dd3b-403">Este servicio lee un paquete de un archivo abierto previamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-403">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="0dd3b-404">Se debe llamar repetidamente hasta que se reciba un estado de NX_FTP_END_OF_FILE.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-404">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="0dd3b-405">Tenga en cuenta que el autor de la llamada no asigna un paquete para este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-405">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="0dd3b-406">Solo necesita proporcionar un puntero a un puntero de paquete.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-406">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="0dd3b-407">Este servicio actualizará ese puntero de paquete para que apunte a un paquete recuperado de la cola de recepción de socket.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-407">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="0dd3b-408">Si se devuelve un estado correcto, significa que hay un paquete disponible y es responsabilidad del autor de la llamada liberarlo cuando haya terminado con él.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-408">If a successful status is returned, that means there was a packet available, and it is the caller's responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="0dd3b-409">Si se devuelve un estado distinto de cero (ya sea un estado de error o NX_FTP_END_OF_FILE), el autor de la llamada no libera el paquete.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-409">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="0dd3b-410">De lo contrario, se genera un error cuando el puntero del paquete es NULL.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-410">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-411">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-411">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-412">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-412">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-413">**packet_ptr**: Puntero al destino del puntero del paquete de datos recuperado de la cola.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-413">**packet_ptr**: Pointer to destination for the data packet pointer retrieved from the queue.</span></span> <span data-ttu-id="0dd3b-414">Si la operación se realiza correctamente, los datos del paquete contienen todo o parte del archivo.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-414">If successful, the packet data contains some or all of the file.</span></span>
- <span data-ttu-id="0dd3b-415">**wait_option**: Define cuánto tiempo va a esperar el servicio para que se lea el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-415">**wait_option**: Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="0dd3b-416">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-416">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-417">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-417">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-418">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-419">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-419">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-420">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-420">Return Values</span></span>

- <span data-ttu-id="0dd3b-421">**NX_SUCCESS** (0x00) Archivo FTP leído correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-421">**NX_SUCCESS**: (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="0dd3b-422">**NX_FTP_NOT_OPEN** (0xD5) El cliente FTP de no está abierto.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-422">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="0dd3b-423">**NX_FTP_END_OF_FILE** (0xD7) Fin de la condición del archivo.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-423">**NX_FTP_END_OF_FILE**: (0xD7) End of file condition.</span></span>
- <span data-ttu-id="0dd3b-424">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-424">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-425">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-425">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-426">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-426">Allowed From</span></span>

<span data-ttu-id="0dd3b-427">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-428">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-428">Example</span></span>

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

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

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="0dd3b-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="0dd3b-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="0dd3b-430">Cambio de nombre de un archivo del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-431">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-431">Prototype</span></span>

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-432">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-432">Description</span></span>

<span data-ttu-id="0dd3b-433">Este servicio cambia el nombre de un archivo en el servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-434">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-434">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-435">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-435">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-436">**filename**: Nombre actual del archivo.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-436">**filename**: Current name of file.</span></span>
- <span data-ttu-id="0dd3b-437">**new_filename**: Nuevo nombre del archivo.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-437">**new_filename**: New name for file.</span></span>
- <span data-ttu-id="0dd3b-438">**wait_option**: Define cuánto tiempo va a esperar el servicio para que se cambie el nombre al archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-438">**wait_option**: Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="0dd3b-439">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-440">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-440">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-441">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-442">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-442">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-443">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-443">Return Values</span></span>

- <span data-ttu-id="0dd3b-444">**NX_SUCCESS** (0x00) Nombre del archivo FTP cambiado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-444">**NX_SUCCESS**: (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="0dd3b-445">**NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-445">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="0dd3b-446">**NX_FTP_EXPECTED_3XX_CODE** (0xDD) No recibió una respuesta 3XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="0dd3b-447">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).</span><span class="sxs-lookup"><span data-stu-id="0dd3b-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="0dd3b-448">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-448">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-449">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-449">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-450">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-450">Allowed From</span></span>

<span data-ttu-id="0dd3b-451">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-452">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-452">Example</span></span>

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="0dd3b-453">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="0dd3b-453">nx_ftp_client_file_write</span></span>

<span data-ttu-id="0dd3b-454">Escritura en un archivo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-454">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-455">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-455">Prototype</span></span>

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0dd3b-456">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-456">Description</span></span>

<span data-ttu-id="0dd3b-457">Este servicio escribe un paquete de datos en el archivo abierto previamente en el servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-457">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-458">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-458">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-459">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-459">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-460">**packet_ptr**: Puntero de paquete que contiene los datos que se van a escribir.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-460">**packet_ptr**: Packet pointer containing data to write.</span></span>
- <span data-ttu-id="0dd3b-461">**wait_option**: Define cuánto tiempo va a esperar el servicio para que se escriba el archivo del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-461">**wait_option**: Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="0dd3b-462">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-462">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="0dd3b-463">**timeout value**: (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0dd3b-463">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="0dd3b-464">**TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="0dd3b-465">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-465">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-466">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-466">Return Values</span></span>

- <span data-ttu-id="0dd3b-467">**NX_SUCCESS** (0x00) Archivo FTP escrito correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-467">**NX_SUCCESS**: (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="0dd3b-468">**NX_FTP_NOT_OPEN** (0xD5) El cliente FTP de no está abierto.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-468">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="0dd3b-469">NX_PTR_ERROR (0x07) Puntero FTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-469">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-470">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-470">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-471">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-471">Allowed From</span></span>

<span data-ttu-id="0dd3b-472">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-473">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-473">Example</span></span>

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="0dd3b-474">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="0dd3b-474">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="0dd3b-475">Habilitación o deshabilitación del modo de transferencia pasiva</span><span class="sxs-lookup"><span data-stu-id="0dd3b-475">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-476">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-476">Prototype</span></span>

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="0dd3b-477">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-477">Description</span></span>

<span data-ttu-id="0dd3b-478">Este servicio habilita el modo de transferencia pasivo si la entrada passive_mode_enabled está establecida en NX_TRUE en una instancia de cliente FTP creada anteriormente, de modo que las llamadas subsiguientes para leer o escribir archivos (RETR, STOR) o descargar un listado del directorio (NLST) se realizan en modo de transferencia.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-478">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="0dd3b-479">Para deshabilitar la transferencia del modo pasivo y volver al comportamiento predeterminado del modo de transferencia activa, llame a esta función con la entrada passive_mode_enabled establecida en NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-479">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-480">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-480">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-481">**ftp_client_ptr**: Puntero al bloque de control del cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-481">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="0dd3b-482">**passive_mode_enabled**:</span><span class="sxs-lookup"><span data-stu-id="0dd3b-482">**passive_mode_enabled**:</span></span>
  - <span data-ttu-id="0dd3b-483">Si se establece en NX_TRUE, se habilita el modo pasivo.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-483">If set to NX_TRUE, passive mode is enabled.</span></span>
  - <span data-ttu-id="0dd3b-484">Si se establece en NX_FALSE, se deshabilita el modo pasivo.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-484">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-485">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-485">Return Values</span></span>

- <span data-ttu-id="0dd3b-486">**NX_SUCCESS** (0x00) Modo pasivo establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-486">**NX_SUCCESS**: (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="0dd3b-487">NX_PTR_ERROR (0x16) El puntero FTP no es válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-487">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-488">NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-488">NX_INVALID_PARAMETERS: (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-489">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-489">Allowed From</span></span>

<span data-ttu-id="0dd3b-490">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-491">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-491">Example</span></span>

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="0dd3b-492">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="0dd3b-492">nx_ftp_server_create</span></span>

<span data-ttu-id="0dd3b-493">Creación del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-493">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-494">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-494">Prototype</span></span>

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="0dd3b-495">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-495">Description</span></span>

<span data-ttu-id="0dd3b-496">Este servicio crea una instancia del servidor FTP en la instancia de IP NetX especificada y creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-496">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="0dd3b-497">Tenga en cuenta que el servidor FTP debe iniciarse con una llamada a ***nx_ftp_server_start*** para que inicie la operación.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-497">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-498">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-498">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-499">**ftp_server_ptr**: Puntero al bloque de control del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-499">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="0dd3b-500">**ftp_server_name**: Nombre del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-500">**ftp_server_name**: Name of FTP Server.</span></span>
- <span data-ttu-id="0dd3b-501">**ip_ptr**: Puntero a la instancia de IP de NetX asociada.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-501">**ip_ptr**: Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="0dd3b-502">Tenga en cuenta que solo puede haber un servidor FTP para una instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-502">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="0dd3b-503">**media_ptr**: Puntero a la instancia multimedia de FileX.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-503">**media_ptr**: Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="0dd3b-504">**stack_ptr**: Puntero a la memoria para el área de pila del subproceso del servidor FTP interno.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-504">**stack_ptr**: Pointer to memory for the internal FTP Server thread's stack area.</span></span>
- <span data-ttu-id="0dd3b-505">**stack_size** Tamaño del área de pila especificado por *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-505">**stack_size**: Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="0dd3b-506">**pool_ptr**: Puntero al grupo de paquetes de NetX.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-506">**pool_ptr**: Pointer to default NetX packet pool.</span></span> <span data-ttu-id="0dd3b-507">Tenga en cuenta que el tamaño de carga de los paquetes del grupo debe ser lo suficientemente grande como para alojar el nombre de archivo o la ruta de acceso más grande.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-507">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="0dd3b-508">**ftp_login**: Puntero de función a la función de inicio de sesión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-508">**ftp_login**: Function pointer to application's login function.</span></span> <span data-ttu-id="0dd3b-509">Esta función proporciona el nombre de usuario y la contraseña del cliente que solicita una conexión.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-509">This function is supplied the username and password from the Client requesting a connection.</span></span> <span data-ttu-id="0dd3b-510">Si resulta válido, la función de inicio de sesión de la aplicación debe devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-510">If this is valid, the application's login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="0dd3b-511">**ftp_logout**: Puntero de función a la función de cierre de sesión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-511">**ftp_logout**: Function pointer to application's logout function.</span></span> <span data-ttu-id="0dd3b-512">Esta función proporciona el nombre de usuario y la contraseña del cliente que solicita una desconexión.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-512">This function is supplied the username and password from the Client requesting a disconnection.</span></span> <span data-ttu-id="0dd3b-513">Si resulta válido, la función de inicio de sesión de la aplicación debe devolver NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-513">If this is valid, the application's login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-514">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-514">Return Values</span></span>

- <span data-ttu-id="0dd3b-515">**NX_SUCCESS** (0x00) Servidor FTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-515">**NX_SUCCESS**: (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="0dd3b-516">NX_PTR_ERROR (0x16) El puntero FTP no es válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-516">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-517">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-517">Allowed From</span></span>

<span data-ttu-id="0dd3b-518">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-518">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-519">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-519">Example</span></span>

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="0dd3b-520">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="0dd3b-520">nx_ftp_server_delete</span></span>

<span data-ttu-id="0dd3b-521">Eliminación del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-521">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-522">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-522">Prototype</span></span>

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0dd3b-523">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-523">Description</span></span>

<span data-ttu-id="0dd3b-524">Este servicio elimina una instancia de servidor FTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-524">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-525">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-525">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-526">**ftp_server_ptr**: Puntero al bloque de control del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-526">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-527">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-527">Return Values</span></span>

- <span data-ttu-id="0dd3b-528">**NX_SUCCESS** (0x00) Servidor FTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-528">**NX_SUCCESS**: (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="0dd3b-529">NX_PTR_ERROR (0x16) El puntero FTP no es válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-529">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-530">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-530">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-531">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-531">Allowed From</span></span>

<span data-ttu-id="0dd3b-532">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-533">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-533">Example</span></span>

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="0dd3b-534">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="0dd3b-534">nx_ftp_server_start</span></span>

<span data-ttu-id="0dd3b-535">Inicio del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-535">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-536">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-536">Prototype</span></span>

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0dd3b-537">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-537">Description</span></span>

<span data-ttu-id="0dd3b-538">Este servicio inicia una instancia de servidor FTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-538">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-539">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-539">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-540">**ftp_server_ptr**: Puntero al bloque de control del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-540">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-541">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-541">Return Values</span></span>

- <span data-ttu-id="0dd3b-542">**NX_SUCCESS** (0x00) Servidor FTP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-542">**NX_SUCCESS**: (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="0dd3b-543">NX_PTR_ERROR (0x16) El puntero FTP no es válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-543">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-544">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-544">Allowed From</span></span>

<span data-ttu-id="0dd3b-545">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-545">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-546">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-546">Example</span></span>

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="0dd3b-547">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="0dd3b-547">nx_ftp_server_stop</span></span>

<span data-ttu-id="0dd3b-548">Detención del servidor FTP</span><span class="sxs-lookup"><span data-stu-id="0dd3b-548">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0dd3b-549">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-549">Prototype</span></span>

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0dd3b-550">Descripción</span><span class="sxs-lookup"><span data-stu-id="0dd3b-550">Description</span></span>

<span data-ttu-id="0dd3b-551">Este servicio detiene una instancia de servidor FTP iniciada y creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-551">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0dd3b-552">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0dd3b-552">Input Parameters</span></span>

- <span data-ttu-id="0dd3b-553">**ftp_server_ptr**: Puntero al bloque de control del servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-553">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0dd3b-554">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-554">Return Values</span></span>

- <span data-ttu-id="0dd3b-555">**NX_SUCCESS** (0x00) Servidor FTP detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-555">**NX_SUCCESS**: (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="0dd3b-556">NX_PTR_ERROR (0x16) El puntero FTP no es válido.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-556">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="0dd3b-557">NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0dd3b-557">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0dd3b-558">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0dd3b-558">Allowed From</span></span>

<span data-ttu-id="0dd3b-559">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0dd3b-559">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0dd3b-560">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0dd3b-560">Example</span></span>

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
