---
title: 'Capítulo 3: Descripción de los servicios TFTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios TFTP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814525"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a><span data-ttu-id="0c59c-103">Capítulo 3: Descripción de los servicios TFTP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="0c59c-103">Chapter 3 - Description of Azure RTOS NetX Duo TFTP services</span></span>

<span data-ttu-id="0c59c-104">Este capítulo contiene una descripción de todos los servicios TFTP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="0c59c-104">This chapter contains a description of all NetX Duo TFTP services (listed below) in alphabetic order.</span></span> <span data-ttu-id="0c59c-105">A menos que se especifique lo contrario, todos los servicios admiten las comunicaciones IPv6 e IPv4.</span><span class="sxs-lookup"><span data-stu-id="0c59c-105">Unless otherwise specified, all services support IPv6 and IPv4 communications.</span></span>

<span data-ttu-id="0c59c-106">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="0c59c-106">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0c59c-107">**nxd_tftp_client_file_open**: *abre el archivo de cliente TFTP*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-107">**nxd_tftp_client_file_open**: *Open TFTP client file*</span></span>

- <span data-ttu-id="0c59c-108">**nxd_tftp_client_create**: *crea una instancia de cliente TFTP*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-108">**nxd_tftp_client_create**: *Create a TFTP client instance*</span></span>

- <span data-ttu-id="0c59c-109">**nxd_tftp_client_delete**: *elimina una instancia de cliente TFTP*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-109">**nxd_tftp_client_delete**: *Delete a TFTP client instance*</span></span>

- <span data-ttu-id="0c59c-110">**nxd_tftp_client_error_info_get**: *obtiene información de error de cliente*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-110">**nxd_tftp_client_error_info_get**: *Get client error information*</span></span>

- <span data-ttu-id="0c59c-111">**nxd_tftp_client_file_close**: *cierra el archivo de cliente*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-111">**nxd_tftp_client_file_close**: *Close client file*</span></span>

- <span data-ttu-id="0c59c-112">**nxd_tftp_client_file_open**: *abre el archivo de cliente*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-112">**nxd_tftp_client_file_open**: *Open client file*</span></span>

- <span data-ttu-id="0c59c-113">**nxd_tftp_client_file_read**: *lee un bloque del archivo de cliente*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-113">**nxd_tftp_client_file_read**: *Read a block from client file*</span></span>

- <span data-ttu-id="0c59c-114">**nxd_tftp_client_file_write**: *escribe un bloque en el archivo de cliente*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-114">**nxd_tftp_client_file_write**: *Write block to client file*</span></span>

- <span data-ttu-id="0c59c-115">**nxd_tftp_client_packet_allocate**: *asigna paquete para escritura de archivo de cliente*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-115">**nxd_tftp_client_packet_allocate**: *Allocate packet for client file write*</span></span>

- <span data-ttu-id="0c59c-116">**nxd_tftp_client_set_interface**: *establece la interfaz física de las solicitudes TFTP*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-116">**nxd_tftp_client_set_interface**: *Set the physical interface for TFTP requests*</span></span>

- <span data-ttu-id="0c59c-117">**nxd_tftp_server_create**: *crea servidor TFTP*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-117">**nxd_tftp_server_create**: *Create TFTP server*</span></span>

- <span data-ttu-id="0c59c-118">**nxd_tftp_server_delete**: *elimina servidor TFTP*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-118">**nxd_tftp_server_delete**: *Delete TFTP server*</span></span>

- <span data-ttu-id="0c59c-119">**nxd_tftp_server_start**: *inicia servidor TFTP*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-119">**nxd_tftp_server_start**: *Start TFTP server*</span></span>

- <span data-ttu-id="0c59c-120">**nxd_tftp_server_stop**: *detiene servidor TFTP*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-120">**nxd_tftp_server_stop**: *Stop TFTP server*</span></span>

> [!NOTE] 
> <span data-ttu-id="0c59c-121">Los equivalentes de IPv4 de todos los servicios enumerados anteriormente están disponibles en el cliente y el servidor TFTP de NetX Duo, por ejemplo, *nx_tftp_server_create* y *nx_tftp_client_file_open*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-121">The IPv4 equivalents of all the services listed above are available in NetX Duo TFTP Client and Server e.g. *nx_tftp_server_create* and *nx_tftp_client_file_open*.</span></span> <span data-ttu-id="0c59c-122">En las páginas siguientes solo se proporcionan las descripciones de API de "Duo", por ejemplo, los servicios que empiezan por *nxd_* .</span><span class="sxs-lookup"><span data-stu-id="0c59c-122">Only the ‘Duo’ API descriptions, e.g. services beginning with *nxd_*, are provided in the following pages.</span></span> <span data-ttu-id="0c59c-123">Donde se especifica una entrada NXD_ADDRESS \*, la API equivalente de IPv4 llama a una entrada ULONG.</span><span class="sxs-lookup"><span data-stu-id="0c59c-123">Where an NXD_ADDRESS \* input is specified, the IPv4 equivalent API calls for ULONG input.</span></span> <span data-ttu-id="0c59c-124">De lo contrario, no hay ninguna diferencia en el uso de la API.</span><span class="sxs-lookup"><span data-stu-id="0c59c-124">Otherwise there is no difference in using the API.</span></span>

## <a name="nxd_tftp_client_create"></a><span data-ttu-id="0c59c-125">nxd_tftp_client_create</span><span class="sxs-lookup"><span data-stu-id="0c59c-125">nxd_tftp_client_create</span></span>

<span data-ttu-id="0c59c-126">Cree una instancia de cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="0c59c-126">Create a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-127">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-127">Prototype</span></span>

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0c59c-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-128">Description</span></span>

<span data-ttu-id="0c59c-129">Este servicio crea una instancia de cliente TFTP para la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-129">This service creates a TFTP Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c59c-130">La aplicación debe asegurarse de que la dirección IP y el grupo de paquetes proporcionados ya se hayan creado.</span><span class="sxs-lookup"><span data-stu-id="0c59c-130">The application must make certain the supplied IP and packet pool are already created.</span></span> <span data-ttu-id="0c59c-131">Además, UDP debe estar habilitado en la instancia de IP antes de llamar a este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-131">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-132">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-132">Input Parameters</span></span>

- <span data-ttu-id="0c59c-133">**tftp_client_ptr** Puntero al bloque de control del cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-133">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="0c59c-134">**tftp_client_name** Nombre de esta instancia de cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-134">**tftp_client_name** Name of this TFTP Client instance</span></span>

- <span data-ttu-id="0c59c-135">**ip_ptr** Puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-135">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="0c59c-136">**pool_ptr** Puntero a la instancia de cliente TFTP del grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="0c59c-136">**pool_ptr** Pointer to packet pool TFTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-137">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-137">Return Values</span></span>

- <span data-ttu-id="0c59c-138">**NX_SUCCESS** (0x00) TFTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-138">**NX_SUCCESS**(0x00) Successful TFTP create.</span></span>

- <span data-ttu-id="0c59c-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Versión de IP no válida o no compatible.</span><span class="sxs-lookup"><span data-stu-id="0c59c-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid or unsupported IP version</span></span>

- <span data-ttu-id="0c59c-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Dirección IP de servidor no válida recibida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP address received</span></span>

- <span data-ttu-id="0c59c-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) ACK de servidor no recibida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Server ACK not received</span></span>

- <span data-ttu-id="0c59c-142">NX_PTR_ERROR (0x16) Dirección IP, grupo o puntero TFTP no válidos.</span><span class="sxs-lookup"><span data-stu-id="0c59c-142">NX_PTR_ERROR (0x16) Invalid IP, pool, or TFTP pointer.</span></span>

- <span data-ttu-id="0c59c-143">NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.</span><span class="sxs-lookup"><span data-stu-id="0c59c-143">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="0c59c-144">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-144">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-145">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-145">Allowed From</span></span>

<span data-ttu-id="0c59c-146">Inicialización y subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-146">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-147">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-147">Example</span></span>

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a><span data-ttu-id="0c59c-148">nxd_tftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="0c59c-148">nxd_tftp_client_delete</span></span>

<span data-ttu-id="0c59c-149">Elimine una instancia de cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="0c59c-149">Delete a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-150">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-150">Prototype</span></span>

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="0c59c-151">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-151">Description</span></span>

<span data-ttu-id="0c59c-152">Este servicio elimina una instancia de cliente TFTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-152">This service deletes a previously created TFTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-153">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-153">Input Parameters</span></span>

- <span data-ttu-id="0c59c-154">**tftp_client_ptr** Puntero a una instancia de cliente TFTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-154">**tftp_client_ptr** Pointer to previously created TFTP client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-155">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-155">Return Values</span></span>

- <span data-ttu-id="0c59c-156">**NX_SUCCESS** (0x00) Cliente TFTP eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-156">**NX_SUCCESS** (0x00) Successful TFTP Client delete.</span></span>

- <span data-ttu-id="0c59c-157">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-157">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-158">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-158">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-159">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-159">Allowed From</span></span>

<span data-ttu-id="0c59c-160">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-160">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-161">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-161">Example</span></span>

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a><span data-ttu-id="0c59c-162">nxd_tftp_client_error_info_get</span><span class="sxs-lookup"><span data-stu-id="0c59c-162">nxd_tftp_client_error_info_get</span></span>

<span data-ttu-id="0c59c-163">Obtenga información de error de cliente</span><span class="sxs-lookup"><span data-stu-id="0c59c-163">Get client error information</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-164">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-164">Prototype</span></span>

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a><span data-ttu-id="0c59c-165">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-165">Description</span></span>

<span data-ttu-id="0c59c-166">Este servicio devuelve el último código de error recibido y establece el puntero en la cadena de error interna del cliente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-166">This service returns the last error code received and sets the pointer to the client’s internal error string.</span></span> <span data-ttu-id="0c59c-167">En caso de error, el usuario puede ver el último error enviado por el servidor.</span><span class="sxs-lookup"><span data-stu-id="0c59c-167">In error conditions, the user can view the last error sent by the server.</span></span> <span data-ttu-id="0c59c-168">Una cadena de error NULL indica que no hay ningún error.</span><span class="sxs-lookup"><span data-stu-id="0c59c-168">A null error string indicates no error is present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-169">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-169">Input Parameters</span></span>

- <span data-ttu-id="0c59c-170">**tftp_client_ptr** Puntero a una instancia de cliente TFTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-170">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="0c59c-171">**error_code** Puntero al área de destino del código de error.</span><span class="sxs-lookup"><span data-stu-id="0c59c-171">**error_code** Pointer to destination area for error code</span></span>

- <span data-ttu-id="0c59c-172">**error_string** Puntero al destino de la cadena de error.</span><span class="sxs-lookup"><span data-stu-id="0c59c-172">**error_string** Pointer to destination for error string</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-173">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-173">Return Values</span></span>

- <span data-ttu-id="0c59c-174">**NX_SUCCESS** (0x00) Información de error de TFTP obtenida correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-174">**NX_SUCCESS** (0x00) Successful TFTP error info get.</span></span>  

- <span data-ttu-id="0c59c-175">NX_PTR_ERROR (0x16) Puntero de cliente TFTP no válido.</span><span class="sxs-lookup"><span data-stu-id="0c59c-175">NX_PTR_ERROR (0x16) Invalid TFTP Client pointer.</span></span>

- <span data-ttu-id="0c59c-176">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-176">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-177">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-177">Allowed From</span></span>

<span data-ttu-id="0c59c-178">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-178">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-179">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-179">Example</span></span>

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a><span data-ttu-id="0c59c-180">nxd_tftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="0c59c-180">nxd_tftp_client_file_close</span></span>

<span data-ttu-id="0c59c-181">Cierre el archivo de cliente</span><span class="sxs-lookup"><span data-stu-id="0c59c-181">Close client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-182">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-182">Prototype</span></span>

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0c59c-183">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-183">Description</span></span>

<span data-ttu-id="0c59c-184">Este servicio cierra el archivo abierto previamente por esta instancia de cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-184">This service closes the previously opened file by this TFTP Client instance.</span></span> <span data-ttu-id="0c59c-185">Una instancia de cliente TFTP solo puede tener un archivo abierto a la vez.</span><span class="sxs-lookup"><span data-stu-id="0c59c-185">A TFTP Client instance is allowed to have only one file open at a time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-186">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-186">Input Parameters</span></span>

- <span data-ttu-id="0c59c-187">**tftp_client_ptr** Puntero a una instancia de cliente TFTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-187">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="0c59c-188">**ip_type** Indica el protocolo IP que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="0c59c-188">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0c59c-189">Las opciones válidas son IPv4 (4) o IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="0c59c-189">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-190">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-190">Return Values</span></span>

- <span data-ttu-id="0c59c-191">**NX_SUCCESS** (0x00) Archivo TFTP cerrado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-191">**NX_SUCCESS** (0x00) Successful TFTP file close.</span></span>

- <span data-ttu-id="0c59c-192">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-192">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-193">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-193">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="0c59c-194">NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.</span><span class="sxs-lookup"><span data-stu-id="0c59c-194">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-195">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-195">Allowed From</span></span>

<span data-ttu-id="0c59c-196">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-197">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-197">Example</span></span>

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a><span data-ttu-id="0c59c-198">nx_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="0c59c-198">nx_tftp_client_file_open</span></span>

<span data-ttu-id="0c59c-199">Abra el archivo de cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="0c59c-199">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-200">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-200">Prototype</span></span>

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0c59c-201">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-201">Description</span></span>

<span data-ttu-id="0c59c-202">Este servicio intenta abrir el archivo especificado en el servidor TFTP en la dirección IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0c59c-202">This service attempts to open the specified file on the TFTP Server at the specified IP address.</span></span> <span data-ttu-id="0c59c-203">El archivo se abre para lectura o escritura.</span><span class="sxs-lookup"><span data-stu-id="0c59c-203">The file will be opened for either reading or writing.</span></span> 

> [!NOTE] 
> <span data-ttu-id="0c59c-204">Esta limitación solo afecta a los paquetes IPv4 y está destinada a admitir aplicaciones TFTP de NetX.</span><span class="sxs-lookup"><span data-stu-id="0c59c-204">This is limited to IPv4 packets only, and is intended for supporting NetX TFTP applications.</span></span> <span data-ttu-id="0c59c-205">Se recomienda a los desarrolladores que porten sus aplicaciones para usar el servicio *nxd_tftp_client_file_open* equivalente de "Duo".</span><span class="sxs-lookup"><span data-stu-id="0c59c-205">Developers are encouraged to port their applications to using equivalent “duo” service *nxd_tftp_client_file_open.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-206">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-206">Input Parameters</span></span>

- <span data-ttu-id="0c59c-207">**tftp_client_ptr** Puntero al bloque de control de TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-207">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="0c59c-208">**file_name** Nombre de archivo ASCII, terminado en NULL y con la información de ruta de acceso adecuada.</span><span class="sxs-lookup"><span data-stu-id="0c59c-208">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="0c59c-209">**server_ip_address** Dirección TFTP del servidor.</span><span class="sxs-lookup"><span data-stu-id="0c59c-209">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="0c59c-210">**open_type** Tipo de solicitud abierta; puede ser:</span><span class="sxs-lookup"><span data-stu-id="0c59c-210">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="0c59c-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="0c59c-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="0c59c-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="0c59c-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="0c59c-213">**wait_option** Define cuánto tiempo va a esperar el servicio para que se abra el archivo de cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-213">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="0c59c-214">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0c59c-214">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0c59c-215">**timeout value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c59c-215">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0c59c-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0c59c-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span> 
  
  <span data-ttu-id="0c59c-217">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor TFTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0c59c-217">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span> 
  
  <span data-ttu-id="0c59c-218">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-218">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="0c59c-219">**ip_type** Indica el protocolo IP que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="0c59c-219">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0c59c-220">Las opciones válidas son IPv4 (4) o IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="0c59c-220">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-221">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-221">Return Values</span></span>

- <span data-ttu-id="0c59c-222">**NX_SUCCESS** (0x00) Archivo de cliente abierto correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-222">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="0c59c-223">**NX_TFTP_NOT_CLOSED** (0xC3) El cliente ya tiene un archivo abierto.</span><span class="sxs-lookup"><span data-stu-id="0c59c-223">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="0c59c-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0c59c-225">**NX_TFTP_NO_ACK_RECEIVED** (0X09) No se ha recibido ACK del servidor.</span><span class="sxs-lookup"><span data-stu-id="0c59c-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="0c59c-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) IP de servidor no válida recibida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="0c59c-227">**NX_TFTP_CODE_ERROR** (0x05) Código de error recibido.</span><span class="sxs-lookup"><span data-stu-id="0c59c-227">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="0c59c-228">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-228">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-229">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-229">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0c59c-230">NX_IP_ADDRESS_ERROR (0x21) Dirección IP del servidor no válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-230">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="0c59c-231">NX_OPTION_ERROR (0x0A) Tipo abierto no válido.</span><span class="sxs-lookup"><span data-stu-id="0c59c-231">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-232">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-232">Allowed From</span></span>

<span data-ttu-id="0c59c-233">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-234">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-234">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a><span data-ttu-id="0c59c-235">nxd_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="0c59c-235">nxd_tftp_client_file_open</span></span>

<span data-ttu-id="0c59c-236">Abra el archivo de cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="0c59c-236">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-237">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-237">Prototype</span></span>

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0c59c-238">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-238">Description</span></span>

<span data-ttu-id="0c59c-239">Este servicio intenta abrir el archivo especificado en el servidor TFTP en la dirección IPv6 especificada.</span><span class="sxs-lookup"><span data-stu-id="0c59c-239">This service attempts to open the specified file on the TFTP Server at the specified IPv6 address.</span></span> <span data-ttu-id="0c59c-240">El archivo se abre para lectura o escritura.</span><span class="sxs-lookup"><span data-stu-id="0c59c-240">The file will be opened for either reading or writing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-241">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-241">Input Parameters</span></span>

- <span data-ttu-id="0c59c-242">**tftp_client_ptr** Puntero al bloque de control de TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-242">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="0c59c-243">**file_name** Nombre de archivo ASCII, terminado en NULL y con la información de ruta de acceso adecuada.</span><span class="sxs-lookup"><span data-stu-id="0c59c-243">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="0c59c-244">**server_ip_address** Dirección TFTP del servidor.</span><span class="sxs-lookup"><span data-stu-id="0c59c-244">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="0c59c-245">**open_type** Tipo de solicitud abierta; puede ser:</span><span class="sxs-lookup"><span data-stu-id="0c59c-245">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="0c59c-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="0c59c-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="0c59c-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="0c59c-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="0c59c-248">**wait_option** Define cuánto tiempo va a esperar el servicio para que se abra el archivo de cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-248">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="0c59c-249">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0c59c-249">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0c59c-250">**timeout value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c59c-250">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0c59c-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0c59c-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0c59c-252">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor TFTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0c59c-252">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span>

  <span data-ttu-id="0c59c-253">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-253">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="0c59c-254">**ip_type** Indica el protocolo IP que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="0c59c-254">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0c59c-255">Las opciones válidas son IPv4 (4) o IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="0c59c-255">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-256">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-256">Return Values</span></span>

- <span data-ttu-id="0c59c-257">**NX_SUCCESS** (0x00) Archivo de cliente abierto correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-257">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="0c59c-258">**NX_TFTP_NOT_CLOSED** (0xC3) El cliente ya tiene un archivo abierto.</span><span class="sxs-lookup"><span data-stu-id="0c59c-258">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="0c59c-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0c59c-260">**NX_TFTP_NO_ACK_RECEIVED** (0X09) No se ha recibido ACK del servidor.</span><span class="sxs-lookup"><span data-stu-id="0c59c-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="0c59c-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Versión de IP no válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="0c59c-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) IP de servidor no válida recibida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="0c59c-263">**NX_TFTP_CODE_ERROR** (0x05) Código de error recibido.</span><span class="sxs-lookup"><span data-stu-id="0c59c-263">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="0c59c-264">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-264">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-265">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-265">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0c59c-266">NX_IP_ADDRESS_ERROR (0x21) Dirección IP del servidor no válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-266">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="0c59c-267">NX_OPTION_ERROR (0x0A) Tipo abierto no válido.</span><span class="sxs-lookup"><span data-stu-id="0c59c-267">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

- <span data-ttu-id="0c59c-268">NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.</span><span class="sxs-lookup"><span data-stu-id="0c59c-268">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-269">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-269">Allowed From</span></span>

<span data-ttu-id="0c59c-270">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-270">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-271">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-271">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a><span data-ttu-id="0c59c-272">nxd_tftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="0c59c-272">nxd_tftp_client_file_read</span></span>

<span data-ttu-id="0c59c-273">Lea un bloque del archivo de cliente</span><span class="sxs-lookup"><span data-stu-id="0c59c-273">Read a block from client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-274">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-274">Prototype</span></span>

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0c59c-275">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-275">Description</span></span>

<span data-ttu-id="0c59c-276">Este servicio lee un bloque de 512 bytes del archivo de cliente TFTP previamente abierto.</span><span class="sxs-lookup"><span data-stu-id="0c59c-276">This service reads a 512-byte block from the previously opened TFTP Client file.</span></span> <span data-ttu-id="0c59c-277">Un bloque que contiene menos de 512 bytes señala el final del archivo.</span><span class="sxs-lookup"><span data-stu-id="0c59c-277">A block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-278">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-278">Input Parameters</span></span>

- <span data-ttu-id="0c59c-279">**tftp_client_ptr** Puntero al bloque de control del cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-279">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="0c59c-280">**packet_ptr** Destino del paquete que contiene el bloque leído del archivo.</span><span class="sxs-lookup"><span data-stu-id="0c59c-280">**packet_ptr** Destination for packet containing the block read from the file.</span></span>

- <span data-ttu-id="0c59c-281">**wait_option** Define cuánto tiempo espera el servicio para que se complete la lectura.</span><span class="sxs-lookup"><span data-stu-id="0c59c-281">**wait_option** Defines how long the service will wait for the read to complete.</span></span> <span data-ttu-id="0c59c-282">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0c59c-282">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0c59c-283">**timeout value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c59c-283">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0c59c-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0c59c-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0c59c-285">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor TFTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0c59c-285">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>

  <span data-ttu-id="0c59c-286">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera a que el servidor TFTP envíe un bloque del archivo.</span><span class="sxs-lookup"><span data-stu-id="0c59c-286">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send a block of the file.</span></span>

- <span data-ttu-id="0c59c-287">**ip_type** Indica el protocolo IP que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="0c59c-287">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0c59c-288">Las opciones válidas son IPv4 (4) o IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="0c59c-288">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-289">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-289">Return Values</span></span>

- <span data-ttu-id="0c59c-290">**NX_SUCCESS** (0x00) Bloque de cliente leído correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-290">**NX_SUCCESS** (0x00) Successful Client block read</span></span>

- <span data-ttu-id="0c59c-291">**NX_TFTP_NOT_OPEN** (0xC3) El archivo de cliente especificado no está abierto para lectura.</span><span class="sxs-lookup"><span data-stu-id="0c59c-291">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for reading</span></span>

- <span data-ttu-id="0c59c-292">**NX_NO_PACKET** (0X01) No se ha recibido ningún paquete del servidor.</span><span class="sxs-lookup"><span data-stu-id="0c59c-292">**NX_NO_PACKET** (0x01) No Packet received from Server.</span></span>

- <span data-ttu-id="0c59c-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0c59c-294">**NX_TFTP_NO_ACK_RECEIVED** (0X09) No se ha recibido ACK del servidor.</span><span class="sxs-lookup"><span data-stu-id="0c59c-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from Server</span></span>

- <span data-ttu-id="0c59c-295">**NX_TFTP_END_OF_FILE** (0xC5) Final de archivo detectado (no es un error).</span><span class="sxs-lookup"><span data-stu-id="0c59c-295">**NX_TFTP_END_OF_FILE** (0xC5) End of file detected (not an error).</span></span>

- <span data-ttu-id="0c59c-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Versión de IP no válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="0c59c-297">**NX_TFTP_CODE_ERROR** (0x05) Código de error recibido.</span><span class="sxs-lookup"><span data-stu-id="0c59c-297">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="0c59c-298">**NX_TFTP_FAILED** (0xC2) Código TFTP desconocido recibido.</span><span class="sxs-lookup"><span data-stu-id="0c59c-298">**NX_TFTP_FAILED** (0xC2) Unknown TFTP code received</span></span>

- <span data-ttu-id="0c59c-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) El número de bloque recibido no es válido.</span><span class="sxs-lookup"><span data-stu-id="0c59c-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Invalid block number received</span></span>

- <span data-ttu-id="0c59c-300">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-300">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-301">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-301">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0c59c-302">NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.</span><span class="sxs-lookup"><span data-stu-id="0c59c-302">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-303">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-303">Allowed From</span></span>

<span data-ttu-id="0c59c-304">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-304">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-305">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-305">Example</span></span>

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a><span data-ttu-id="0c59c-306">nxd_tftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="0c59c-306">nxd_tftp_client_file_write</span></span>

<span data-ttu-id="0c59c-307">Escriba un bloque en el archivo de cliente</span><span class="sxs-lookup"><span data-stu-id="0c59c-307">Write a block to Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-308">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-308">Prototype</span></span>

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0c59c-309">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-309">Description</span></span>

<span data-ttu-id="0c59c-310">Este servicio escribe un bloque de 512 bytes en el archivo de cliente TFTP previamente abierto.</span><span class="sxs-lookup"><span data-stu-id="0c59c-310">This service writes a 512-byte block to the previously opened TFTP Client file.</span></span> <span data-ttu-id="0c59c-311">Si especifica un bloque que contiene menos de 512 bytes, se señala el final del archivo.</span><span class="sxs-lookup"><span data-stu-id="0c59c-311">Specifying a block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-312">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-312">Input Parameters</span></span>

- <span data-ttu-id="0c59c-313">**tftp_client_ptr** Puntero al bloque de control del cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-313">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="0c59c-314">**packet_ptr** Paquete que contiene el bloque que se va a escribir en el archivo.</span><span class="sxs-lookup"><span data-stu-id="0c59c-314">**packet_ptr** Packet containing the block to write to the file.</span></span>

- <span data-ttu-id="0c59c-315">**wait_option** Define cuánto tiempo espera el servicio para que se complete la escritura.</span><span class="sxs-lookup"><span data-stu-id="0c59c-315">**wait_option** Defines how long the service will wait for the write to complete.</span></span> <span data-ttu-id="0c59c-316">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0c59c-316">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0c59c-317">**timeout value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c59c-317">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0c59c-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0c59c-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0c59c-319">Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor TFTP responde a la solicitud.</span><span class="sxs-lookup"><span data-stu-id="0c59c-319">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>
 
  <span data-ttu-id="0c59c-320">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera a que el servidor TFTP envíe una ACK para la solicitud de escritura.</span><span class="sxs-lookup"><span data-stu-id="0c59c-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send an ACK for the write request.</span></span>

- <span data-ttu-id="0c59c-321">**ip_type** Indica el protocolo IP que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="0c59c-321">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0c59c-322">Las opciones válidas son IPv4 (4) o IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="0c59c-322">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-323">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-323">Return Values</span></span>

- <span data-ttu-id="0c59c-324">**NX_SUCCESS** (0x00) Bloque de cliente escrito correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-324">**NX_SUCCESS** (0x00) Successful Client block write</span></span>

- <span data-ttu-id="0c59c-325">**NX_TFTP_NOT_OPEN** (0xC3) El archivo de cliente especificado no está abierto para escritura.</span><span class="sxs-lookup"><span data-stu-id="0c59c-325">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for writing</span></span>

- <span data-ttu-id="0c59c-326">**NX_TFTP_TIMEOUT** (0xC1) Tiempo de espera agotado para la ACK del servidor.</span><span class="sxs-lookup"><span data-stu-id="0c59c-326">**NX_TFTP_TIMEOUT** (0xC1) Timeout waiting for Server ACK</span></span>

- <span data-ttu-id="0c59c-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0c59c-328">**NX_TFTP_NO_ACK_RECEIVED** (0X09) No se ha recibido ACK del servidor.</span><span class="sxs-lookup"><span data-stu-id="0c59c-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="0c59c-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Versión de IP no válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="0c59c-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="0c59c-331">**NX_TFTP_CODE_ERROR** (0x05) Código de error recibido.</span><span class="sxs-lookup"><span data-stu-id="0c59c-331">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="0c59c-332">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-332">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-333">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-333">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0c59c-334">NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.</span><span class="sxs-lookup"><span data-stu-id="0c59c-334">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-335">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-335">Allowed From</span></span>

<span data-ttu-id="0c59c-336">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-336">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-337">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-337">Example</span></span>

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a><span data-ttu-id="0c59c-338">nxd_tftp_client_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="0c59c-338">nxd_tftp_client_packet_allocate</span></span>

<span data-ttu-id="0c59c-339">Asigne paquete para escritura de archivo de cliente</span><span class="sxs-lookup"><span data-stu-id="0c59c-339">Allocate packet for Client file write</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-340">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-340">Prototype</span></span>

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="0c59c-341">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-341">Description</span></span>

<span data-ttu-id="0c59c-342">Este servicio asigna un paquete UDP desde el grupo de paquetes especificado y deja espacio para el encabezado TFTP de 4 bytes antes de que el paquete se devuelva al autor de la llamada.</span><span class="sxs-lookup"><span data-stu-id="0c59c-342">This service allocates a UDP packet from the specified packet pool and makes room for the 4-byte TFTP header before the packet is returned to the caller.</span></span> <span data-ttu-id="0c59c-343">Después, el autor de la llamada puede compilar un búfer para escribir en un archivo de cliente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-343">The caller can then build a buffer for writing to a client file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-344">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-344">Input Parameters</span></span>

- <span data-ttu-id="0c59c-345">**pool_ptr** Puntero al grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="0c59c-345">**pool_ptr** Pointer to packet pool.</span></span>

- <span data-ttu-id="0c59c-346">**packet_ptr** Destino del puntero al paquete asignado.</span><span class="sxs-lookup"><span data-stu-id="0c59c-346">**packet_ptr** Destination for pointer to allocated packet.</span></span>

- <span data-ttu-id="0c59c-347">**wait_option** Define cuánto tiempo espera el servicio para que se complete la asignación de paquete.</span><span class="sxs-lookup"><span data-stu-id="0c59c-347">**wait_option** Defines how long the service will wait for the packet allocate to complete.</span></span> <span data-ttu-id="0c59c-348">Las opciones de espera se definen de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="0c59c-348">The wait options are defined as follows:</span></span>

  <span data-ttu-id="0c59c-349">**timeout value** (de 0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0c59c-349">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="0c59c-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0c59c-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="0c59c-351">Al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que se completa la asignación.</span><span class="sxs-lookup"><span data-stu-id="0c59c-351">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the allocation completes.</span></span>

  <span data-ttu-id="0c59c-352">Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la asignación del paquete.</span><span class="sxs-lookup"><span data-stu-id="0c59c-352">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the packet allocation.</span></span>

- <span data-ttu-id="0c59c-353">**ip_type** Indica el protocolo IP que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="0c59c-353">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="0c59c-354">Las opciones válidas son IPv4 (4) o IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="0c59c-354">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-355">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-355">Return Values</span></span>

- <span data-ttu-id="0c59c-356">**NX_SUCCESS** (0x00) Asignación correcta de paquete.</span><span class="sxs-lookup"><span data-stu-id="0c59c-356">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>

- <span data-ttu-id="0c59c-357">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-357">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-358">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-358">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0c59c-359">NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.</span><span class="sxs-lookup"><span data-stu-id="0c59c-359">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-360">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-360">Allowed From</span></span>

<span data-ttu-id="0c59c-361">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-361">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-362">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-362">Example</span></span>

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a><span data-ttu-id="0c59c-363">nxd_tftp_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="0c59c-363">nxd_tftp_client_set_interface</span></span>

<span data-ttu-id="0c59c-364">Establezca la interfaz física para solicitudes TFTP</span><span class="sxs-lookup"><span data-stu-id="0c59c-364">Set physical interface for TFTP requests</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-365">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-365">Prototype</span></span>

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a><span data-ttu-id="0c59c-366">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-366">Description</span></span>

<span data-ttu-id="0c59c-367">Este servicio usa el índice de la interfaz de entrada para establecer la interfaz física para que el cliente TFTP envíe y reciba paquetes TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-367">This service uses the input interface index to set the physical interface for the TFTP Client to send and receive TFTP packets.</span></span> <span data-ttu-id="0c59c-368">El valor predeterminado es cero para la interfaz principal.</span><span class="sxs-lookup"><span data-stu-id="0c59c-368">The default value is zero, for the primary interface.</span></span>

> [!NOTE]
> <span data-ttu-id="0c59c-369">NetX Duo debe admitir el direccionamiento de host múltiple (v5.6 o posterior) para usar este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-369">NetX Duo must support multihome addressing (v5.6 or later) to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-370">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-370">Input Parameters</span></span>

- <span data-ttu-id="0c59c-371">**tftp_client_ptr** Puntero a la instancia de cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-371">**tftp_client_ptr** Pointer to TFTP Client instance</span></span>

- <span data-ttu-id="0c59c-372">**if_index** Índice de la interfaz física que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="0c59c-372">**if_index** Index of physical interface to use</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-373">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-373">Return Values</span></span>

- <span data-ttu-id="0c59c-374">**NX_SUCCESS** (0x00) Interfaz establecida correctamente. (0X0B) Entrada de interfaz no válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-374">**NX_SUCCESS** (0x00) Successfully set interface (0x0B) Invalid interface input</span></span>

- <span data-ttu-id="0c59c-375">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-375">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-376">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-376">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="0c59c-377">NX_TFTP_INVALID_INTERFACE (0x0B) Entrada de interfaz no válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-377">NX_TFTP_INVALID_INTERFACE (0x0B) Invalid interface input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-378">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-378">Allowed From</span></span>

<span data-ttu-id="0c59c-379">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-380">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-380">Example</span></span>

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a><span data-ttu-id="0c59c-381">nxd_tftp_server_create</span><span class="sxs-lookup"><span data-stu-id="0c59c-381">nxd_tftp_server_create</span></span>

<span data-ttu-id="0c59c-382">Cree un servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="0c59c-382">Create TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-383">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-383">Prototype</span></span>

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0c59c-384">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-384">Description</span></span>

<span data-ttu-id="0c59c-385">Este servicio crea un servidor TFTP que responde a las solicitudes de cliente TFTP en el puerto 69.</span><span class="sxs-lookup"><span data-stu-id="0c59c-385">This service creates a TFTP Server that responds to TFTP Client requests on port 69.</span></span> <span data-ttu-id="0c59c-386">El servidor debe iniciarse mediante una llamada subsiguiente a *nxd_tftp_server_start*.</span><span class="sxs-lookup"><span data-stu-id="0c59c-386">The Server must be started by a subsequent call to *nxd_tftp_server_start*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c59c-387">La aplicación debe asegurarse de que ya se hayan creado la instancia de IP, el grupo de paquetes y la instancia de medios FileX suministrados.</span><span class="sxs-lookup"><span data-stu-id="0c59c-387">The application must make certain the supplied IP instance, packet pool, and FileX media instance are already created.</span></span> <span data-ttu-id="0c59c-388">Además, UDP debe estar habilitado en la instancia de IP antes de llamar a este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-388">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-389">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-389">Input Parameters</span></span>

- <span data-ttu-id="0c59c-390">**tftp_server_ptr** Puntero al bloque de control del servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-390">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

- <span data-ttu-id="0c59c-391">**tftp_server_name** Nombre de esta instancia del servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-391">**tftp_server_name** Name of this TFTP Server instance</span></span>

- <span data-ttu-id="0c59c-392">**ip_ptr** Puntero a la instancia de IP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-392">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="0c59c-393">**media_ptr** Puntero a la instancia de medios FileX.</span><span class="sxs-lookup"><span data-stu-id="0c59c-393">**media_ptr** Pointer to FileX media instance.</span></span>

- <span data-ttu-id="0c59c-394">**stack_ptr** Puntero al área de pila del servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-394">**stack_ptr** Pointer to TFTP Server stack area.</span></span>

- <span data-ttu-id="0c59c-395">**stack_size** Número de bytes en la pila del servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-395">**stack_size** Number of bytes in the TFTP Server stack.</span></span>

- <span data-ttu-id="0c59c-396">**pool_ptr** Puntero al grupo de paquetes TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-396">**pool_ptr** Pointer to TFTP packet pool.</span></span> 

> [!NOTE]
> <span data-ttu-id="0c59c-397">El grupo proporcionado debe tener cargas de paquetes de al menos 580 bytes.<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0c59c-397">The supplied pool must have packet payloads at least 580 bytes in size.<sup>1</sup></span></span>

<span data-ttu-id="0c59c-398"><sup>1</sup> La parte de datos de un paquete tiene exactamente 512 bytes, pero el tamaño de la carga de paquete debe ser de al menos 572 bytes.</span><span class="sxs-lookup"><span data-stu-id="0c59c-398"><sup>1</sup> The data portion of a packet is exactly 512 bytes, but the packet payload size must be at least 572 bytes.</span></span> <span data-ttu-id="0c59c-399">Los bytes restantes se utilizan para los encabezados UDP, IPv6 o Ethernet y los bytes finales posibles que necesita el controlador para la alineación.</span><span class="sxs-lookup"><span data-stu-id="0c59c-399">The remaining bytes are used for the UDP, IPv6, and Ethernet headers and potential trailing bytes required by the driver for alignment.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-400">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-400">Return Values</span></span>

- <span data-ttu-id="0c59c-401">**NX_SUCCESS** (0x00) Servidor creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-401">**NX_SUCCESS** (0x00) Successful Server create</span></span>

- <span data-ttu-id="0c59c-402">**NX_TFTP_POOL_ERROR** (0xC6) El grupo de paquetes tiene un tamaño de paquete de menos de 560 bytes.</span><span class="sxs-lookup"><span data-stu-id="0c59c-402">**NX_TFTP_POOL_ERROR** (0xC6) Packet pool has packet size of less than 560 bytes</span></span>

- <span data-ttu-id="0c59c-403">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-403">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-404">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-404">Allowed From</span></span>

<span data-ttu-id="0c59c-405">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-405">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-406">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-406">Example</span></span>

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a><span data-ttu-id="0c59c-407">nxd_tftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="0c59c-407">nxd_tftp_server_delete</span></span>

<span data-ttu-id="0c59c-408">Elimine un servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="0c59c-408">Delete TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-409">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-409">Prototype</span></span>

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0c59c-410">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-410">Description</span></span>

<span data-ttu-id="0c59c-411">Este servicio elimina un servidor TFTP creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-411">This service deletes a previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-412">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-412">Input Parameters</span></span>

- <span data-ttu-id="0c59c-413">**tftp_server_ptr** Puntero al bloque de control del servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-413">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-414">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-414">Return Values</span></span>

- <span data-ttu-id="0c59c-415">**NX_SUCCESS** (0x00) Servidor eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-415">**NX_SUCCESS** (0x00) Successful Server delete</span></span>

- <span data-ttu-id="0c59c-416">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-416">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-417">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-417">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-418">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-418">Allowed From</span></span>

<span data-ttu-id="0c59c-419">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-419">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-420">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-420">Example</span></span>

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a><span data-ttu-id="0c59c-421">nxd_tftp_server_start</span><span class="sxs-lookup"><span data-stu-id="0c59c-421">nxd_tftp_server_start</span></span>

<span data-ttu-id="0c59c-422">Inicie el servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="0c59c-422">Start TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-423">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-423">Prototype</span></span>

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0c59c-424">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-424">Description</span></span>

<span data-ttu-id="0c59c-425">Este servicio inicia el servidor TFTP creado previamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-425">This service starts the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-426">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-426">Input Parameters</span></span>

- <span data-ttu-id="0c59c-427">**tftp_server_ptr** Puntero al bloque de control del servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-427">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-428">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-428">Return Values</span></span>

- <span data-ttu-id="0c59c-429">**NX_SUCCESS** (0x00) Servidor iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-429">**NX_SUCCESS** (0x00) Successful Server start</span></span>

- <span data-ttu-id="0c59c-430">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-430">NX_PTR_ERROR (0x16) Invalid pointer input .</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="0c59c-431">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-431">Allowed From</span></span>

<span data-ttu-id="0c59c-432">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-432">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-433">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-433">Example</span></span>

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a><span data-ttu-id="0c59c-434">nxd_tftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="0c59c-434">nxd_tftp_server_stop</span></span>

<span data-ttu-id="0c59c-435">Detenga el servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="0c59c-435">Stop TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="0c59c-436">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0c59c-436">Prototype</span></span>

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="0c59c-437">Descripción</span><span class="sxs-lookup"><span data-stu-id="0c59c-437">Description</span></span>

<span data-ttu-id="0c59c-438">Este servicio detiene el servidor TFTP creado previamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-438">This service stops the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c59c-439">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c59c-439">Input Parameters</span></span>

- <span data-ttu-id="0c59c-440">**tftp_server_ptr** Puntero al bloque de control del servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="0c59c-440">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c59c-441">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0c59c-441">Return Values</span></span>

- <span data-ttu-id="0c59c-442">**NX_SUCCESS** (0x00) Servidor detenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="0c59c-442">**NX_SUCCESS** (0x00) Successful Server stop</span></span>

- <span data-ttu-id="0c59c-443">NX_PTR_ERROR (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="0c59c-443">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="0c59c-444">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="0c59c-444">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c59c-445">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="0c59c-445">Allowed From</span></span>

<span data-ttu-id="0c59c-446">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="0c59c-446">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0c59c-447">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0c59c-447">Example</span></span>

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```