---
title: 'Capítulo 3: Descripción de los servicios de cliente Azure RTOS NetX POP3'
description: Este capítulo contiene una descripción de todos los servicios de cliente Azure RTOS NetX POP3 (que se enumeran a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0ab96a454bea9f56ced0d7aa8de5d481b284e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815161"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a><span data-ttu-id="5d643-103">Capítulo 3: Descripción de los servicios de cliente Azure RTOS NetX POP3</span><span class="sxs-lookup"><span data-stu-id="5d643-103">Chapter 3 - Description of Azure RTOS NetX POP3 Client services</span></span>

<span data-ttu-id="5d643-104">Este capítulo contiene una descripción de todos los servicios de cliente Azure RTOS NetX POP3 (que se enumeran a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="5d643-104">This chapter contains a description of all Azure RTOS NetX POP3 Client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="5d643-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="5d643-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="5d643-106">nx_pop3_client_create: *Crear de una instancia de cliente POP3*</span><span class="sxs-lookup"><span data-stu-id="5d643-106">nx_pop3_client_create: *Create a POP3 Client Instance*</span></span>
- <span data-ttu-id="5d643-107">nx_pop3_client_delete: *Eliminar una instancia de cliente POP3*</span><span class="sxs-lookup"><span data-stu-id="5d643-107">nx_pop3_client_delete: *Delete a POP3 Client instance*</span></span>
- <span data-ttu-id="5d643-108">nx_pop3_client_ mail_item_get: *Eliminar un elemento de correo de cliente del servidor maildrop*</span><span class="sxs-lookup"><span data-stu-id="5d643-108">nx_pop3_client_ mail_item_get: *Delete a Client mail item from Server maildrop*</span></span>
- <span data-ttu-id="5d643-109">nx_pop3_client_mail_item_get: *Recuperar un tamaño de mensaje de correo específico*</span><span class="sxs-lookup"><span data-stu-id="5d643-109">nx_pop3_client_mail_item_get: *Retrieve a specific mail message size*</span></span>
- <span data-ttu-id="5d643-110">nx_pop3_client_mail_items_get: *Obtener el número de elementos de correo en maildrop*</span><span class="sxs-lookup"><span data-stu-id="5d643-110">nx_pop3_client_mail_items_get: *Obtain the number of mail items in maildrop*</span></span>
- <span data-ttu-id="5d643-111">nx_pop3_client_mail_item_message _get: *Descargar un mensaje de correo específico*</span><span class="sxs-lookup"><span data-stu-id="5d643-111">nx_pop3_client_mail_item_message _get: *Download a specific mail message*</span></span>
- <span data-ttu-id="5d643-112">nx_pop3_client_mail_item_size_get: *Obtener el tamaño de un elemento de correo específico*</span><span class="sxs-lookup"><span data-stu-id="5d643-112">nx_pop3_client_mail_item_size_get: *Obtain the size of a specific mail item*</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="5d643-113">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="5d643-113">nx_pop3_client_create</span></span>

<span data-ttu-id="5d643-114">Crear una instancia del cliente POP3</span><span class="sxs-lookup"><span data-stu-id="5d643-114">Create a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5d643-115">Prototipo</span><span class="sxs-lookup"><span data-stu-id="5d643-115">Prototype</span></span>

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="5d643-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="5d643-116">Description</span></span>

<span data-ttu-id="5d643-117">Este servicio crea una instancia del cliente POP3 y establece su configuración con los parámetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="5d643-117">This service creates an instance of the POP3 Client and sets up its configuration with the input parameters.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5d643-118">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-118">Input Parameters</span></span>

- <span data-ttu-id="5d643-119">**client_ptr**: Puntero al cliente que se va a crear</span><span class="sxs-lookup"><span data-stu-id="5d643-119">**client_ptr**: Pointer to Client to create</span></span>
- <span data-ttu-id="5d643-120">**APOP_authentication**: Habilitar la autenticación de APOP</span><span class="sxs-lookup"><span data-stu-id="5d643-120">**APOP_authentication**: Enable APOP authentication</span></span>
- <span data-ttu-id="5d643-121">**ip_ptr**: Puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="5d643-121">**ip_ptr**: Pointer to IP instance</span></span>
- <span data-ttu-id="5d643-122">**packet_pool_ptr**: Puntero al grupo de paquetes del cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-122">**packet_pool_ptr**: Pointer to Client packet pool</span></span>
- <span data-ttu-id="5d643-123">**server_ip_address**: Dirección del servidor POP3</span><span class="sxs-lookup"><span data-stu-id="5d643-123">**server_ip_address**: POP3 server address</span></span>
- <span data-ttu-id="5d643-124">**SERVER_PORT**: Puerto del servidor POP3</span><span class="sxs-lookup"><span data-stu-id="5d643-124">**server_port**: POP3 server port</span></span>
- <span data-ttu-id="5d643-125">**client_name**: Puntero a nombre de cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-125">**client_name**: Pointer to Client name</span></span>
- <span data-ttu-id="5d643-126">**client_password**: Puntero a la contraseña de cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-126">**client_password**: Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="5d643-127">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="5d643-127">Return Values</span></span>

- <span data-ttu-id="5d643-128">**NX_SUCCESS**: (0x00) Cliente creado correctamente</span><span class="sxs-lookup"><span data-stu-id="5d643-128">**NX_SUCCESS**: (0x00) Client successfully created</span></span>
- <span data-ttu-id="5d643-129">**estado**: Finalización del estado de las llamadas al servicio NetX y ThreadX</span><span class="sxs-lookup"><span data-stu-id="5d643-129">**status**: Status completion of NetX and ThreadX service calls</span></span>
- <span data-ttu-id="5d643-130">NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-130">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="5d643-131">NX_POP3_PARAM_ERROR: (0xB1) Entrada de puntero no válida</span><span class="sxs-lookup"><span data-stu-id="5d643-131">NX_POP3_PARAM_ERROR: (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5d643-132">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="5d643-132">Allowed From</span></span>

<span data-ttu-id="5d643-133">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="5d643-133">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5d643-134">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5d643-134">Example</span></span>

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="5d643-135">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="5d643-135">nx_pop3_client_delete</span></span>

<span data-ttu-id="5d643-136">Eliminar una instancia de cliente POP3</span><span class="sxs-lookup"><span data-stu-id="5d643-136">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5d643-137">Prototipo</span><span class="sxs-lookup"><span data-stu-id="5d643-137">Prototype</span></span>

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a><span data-ttu-id="5d643-138">Descripción</span><span class="sxs-lookup"><span data-stu-id="5d643-138">Description</span></span>

<span data-ttu-id="5d643-139">Este servicio elimina un cliente POP3 creado previamente.</span><span class="sxs-lookup"><span data-stu-id="5d643-139">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="5d643-140">No es que este servicio no elimine el grupo de paquetes del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="5d643-140">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="5d643-141">La aplicación de dispositivo debe eliminar este recurso por separado si ya no se usa para el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="5d643-141">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5d643-142">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-142">Input Parameters</span></span>

- <span data-ttu-id="5d643-143">**client_ptr**: Puntero al cliente que se va a eliminar</span><span class="sxs-lookup"><span data-stu-id="5d643-143">**client_ptr**: Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="5d643-144">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="5d643-144">Return Values</span></span>

- <span data-ttu-id="5d643-145">**NX_SUCCESS**: (0x00) Cliente eliminado correctamente</span><span class="sxs-lookup"><span data-stu-id="5d643-145">**NX_SUCCESS**: (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="5d643-146">NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-146">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5d643-147">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="5d643-147">Allowed From</span></span>

<span data-ttu-id="5d643-148">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="5d643-148">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5d643-149">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5d643-149">Example</span></span>

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="5d643-150">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="5d643-150">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="5d643-151">Eliminar un elemento de correo especificado del maildrop del cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-151">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="5d643-152">Prototipo</span><span class="sxs-lookup"><span data-stu-id="5d643-152">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a><span data-ttu-id="5d643-153">Descripción</span><span class="sxs-lookup"><span data-stu-id="5d643-153">Description</span></span>

<span data-ttu-id="5d643-154">Este servicio elimina el elemento de correo especificado de la maildrop del cliente.</span><span class="sxs-lookup"><span data-stu-id="5d643-154">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="5d643-155">Está pensada para después de descargar el elemento de correo, aunque algunos servidores POP3 pueden eliminar elementos de correo automáticamente después de que el cliente los solicite.</span><span class="sxs-lookup"><span data-stu-id="5d643-155">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5d643-156">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-156">Input Parameters</span></span>

- <span data-ttu-id="5d643-157">**client_ptr**: Puntero a la instancia de cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-157">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="5d643-158">**mail_index**: Índice en la maildrop del cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-158">**mail_index**: Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="5d643-159">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="5d643-159">Return Values</span></span>

- <span data-ttu-id="5d643-160">**NX_SUCCESS**: (0X00) Eliminar solicitud correcta</span><span class="sxs-lookup"><span data-stu-id="5d643-160">**NX_SUCCESS**: (0x00) Delete request successful</span></span>
- <span data-ttu-id="5d643-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de elemento de correo no válido</span><span class="sxs-lookup"><span data-stu-id="5d643-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="5d643-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) la carga de paquete de cliente es demasiado pequeña para la solicitud POP3.</span><span class="sxs-lookup"><span data-stu-id="5d643-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5d643-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) el servidor responde con el estado de error</span><span class="sxs-lookup"><span data-stu-id="5d643-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="5d643-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada de índice de correo no válida</span><span class="sxs-lookup"><span data-stu-id="5d643-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="5d643-165">NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-165">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5d643-166">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="5d643-166">Allowed From</span></span>

<span data-ttu-id="5d643-167">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="5d643-167">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5d643-168">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5d643-168">Example</span></span>

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="5d643-169">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="5d643-169">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="5d643-170">Recuperar un elemento de correo especificado</span><span class="sxs-lookup"><span data-stu-id="5d643-170">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="5d643-171">Prototipo</span><span class="sxs-lookup"><span data-stu-id="5d643-171">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a><span data-ttu-id="5d643-172">Descripción</span><span class="sxs-lookup"><span data-stu-id="5d643-172">Description</span></span>

<span data-ttu-id="5d643-173">Este servicio realiza una solicitud RETR para recuperar un elemento de correo desde el maildrop del cliente especificado por el índice mail_item.</span><span class="sxs-lookup"><span data-stu-id="5d643-173">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="5d643-174">Después de hacer una solicitud RETR y recibir una respuesta positiva del servidor, el cliente puede comenzar a descargar el mensaje de correo mediante el servicio *nx_pop3_client_mail_item_message_get*.</span><span class="sxs-lookup"><span data-stu-id="5d643-174">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="5d643-175">Tenga en cuenta que el servicio también proporciona el tamaño del elemento de correo solicitado extraído de la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="5d643-175">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5d643-176">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-176">Input Parameters</span></span>

- <span data-ttu-id="5d643-177">**client_ptr**: Puntero a la instancia de cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-177">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="5d643-178">**mail_item**: Índice en el maildrop del cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-178">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="5d643-179">**item_size**: Puntero al tamaño del mensaje de correo</span><span class="sxs-lookup"><span data-stu-id="5d643-179">**item_size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="5d643-180">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="5d643-180">Return Values</span></span>

- <span data-ttu-id="5d643-181">**NX_SUCCESS**: (0x00) Elemento de correo recuperado correctamente</span><span class="sxs-lookup"><span data-stu-id="5d643-181">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="5d643-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de elemento de correo no válido</span><span class="sxs-lookup"><span data-stu-id="5d643-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="5d643-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) la carga de paquete de cliente es demasiado pequeña para la solicitud POP3.</span><span class="sxs-lookup"><span data-stu-id="5d643-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5d643-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) el servidor responde con el estado de error</span><span class="sxs-lookup"><span data-stu-id="5d643-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="5d643-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada de índice de correo no válida</span><span class="sxs-lookup"><span data-stu-id="5d643-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="5d643-186">NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-186">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5d643-187">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="5d643-187">Allowed From</span></span>

<span data-ttu-id="5d643-188">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="5d643-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5d643-189">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5d643-189">Example</span></span>

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="5d643-190">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="5d643-190">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="5d643-191">Recuperar el número de elementos de correo en maildrop</span><span class="sxs-lookup"><span data-stu-id="5d643-191">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="5d643-192">Prototipo</span><span class="sxs-lookup"><span data-stu-id="5d643-192">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a><span data-ttu-id="5d643-193">Descripción</span><span class="sxs-lookup"><span data-stu-id="5d643-193">Description</span></span>

<span data-ttu-id="5d643-194">Este servicio realiza una solicitud de STAT para recuperar el número de elementos de correo y el tamaño total de los datos de los mensajes de correo desde el maildrop del cliente.</span><span class="sxs-lookup"><span data-stu-id="5d643-194">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5d643-195">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-195">Input Parameters</span></span>

- <span data-ttu-id="5d643-196">**client_ptr**: Puntero a la instancia de cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-196">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="5d643-197">**number_mail_item**: Número de correo en el maildrop del cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-197">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="5d643-198">**maildrop_total_size**: Puntero al tamaño de todo el mensaje de correo</span><span class="sxs-lookup"><span data-stu-id="5d643-198">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="5d643-199">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="5d643-199">Return Values</span></span>

- <span data-ttu-id="5d643-200">**NX_SUCCESS**: (0x00) Elemento de correo recuperado correctamente</span><span class="sxs-lookup"><span data-stu-id="5d643-200">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="5d643-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de elemento de correo no válido</span><span class="sxs-lookup"><span data-stu-id="5d643-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="5d643-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) la carga de paquete de cliente es demasiado pequeña para la solicitud POP3.</span><span class="sxs-lookup"><span data-stu-id="5d643-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5d643-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) el servidor responde con el estado de error</span><span class="sxs-lookup"><span data-stu-id="5d643-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span> 
- <span data-ttu-id="5d643-204">NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-204">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5d643-205">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="5d643-205">Allowed From</span></span>

<span data-ttu-id="5d643-206">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="5d643-206">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5d643-207">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5d643-207">Example</span></span>

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="5d643-208">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="5d643-208">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="5d643-209">Recuperar el mensaje de elemento de correo especificado</span><span class="sxs-lookup"><span data-stu-id="5d643-209">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="5d643-210">Prototipo</span><span class="sxs-lookup"><span data-stu-id="5d643-210">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a><span data-ttu-id="5d643-211">Descripción</span><span class="sxs-lookup"><span data-stu-id="5d643-211">Description</span></span>

<span data-ttu-id="5d643-212">Este servicio recupera el mensaje de elemento de correo, el tamaño del mensaje de correo y si es el último paquete del mensaje de correo.</span><span class="sxs-lookup"><span data-stu-id="5d643-212">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="5d643-213">Si `final_packet` es NX_TRUE el paquete al que apunta `recv_packet_ptr` es el paquete final en el mensaje del elemento de correo.</span><span class="sxs-lookup"><span data-stu-id="5d643-213">If `final_packet` is NX_TRUE the packet pointed to by `recv_packet_ptr` is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5d643-214">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-214">Input Parameters</span></span>

- <span data-ttu-id="5d643-215">**client_ptr**: Puntero a la instancia de cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-215">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="5d643-216">**recv_packet_ptr**: Paquete recibido de datos de mensaje</span><span class="sxs-lookup"><span data-stu-id="5d643-216">**recv_packet_ptr**: Received packet of message data</span></span>
- <span data-ttu-id="5d643-217">**number_mail_item**: Número de correo en el maildrop del cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-217">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="5d643-218">**maildrop_total_size**: Puntero al tamaño de todo el mensaje de correo</span><span class="sxs-lookup"><span data-stu-id="5d643-218">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="5d643-219">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="5d643-219">Return Values</span></span>

- <span data-ttu-id="5d643-220">**NX_SUCCESS**: (0x00) Elemento de correo recuperado correctamente</span><span class="sxs-lookup"><span data-stu-id="5d643-220">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="5d643-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) La carga de paquete de cliente es demasiado pequeña para la solicitud POP3.</span><span class="sxs-lookup"><span data-stu-id="5d643-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5d643-222">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-222">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5d643-223">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="5d643-223">Allowed From</span></span>

<span data-ttu-id="5d643-224">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="5d643-224">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5d643-225">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5d643-225">Example</span></span>

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="5d643-226">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="5d643-226">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="5d643-227">Recupera el tamaño del elemento de correo especificado</span><span class="sxs-lookup"><span data-stu-id="5d643-227">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="5d643-228">Prototipo</span><span class="sxs-lookup"><span data-stu-id="5d643-228">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a><span data-ttu-id="5d643-229">Descripción</span><span class="sxs-lookup"><span data-stu-id="5d643-229">Description</span></span>

<span data-ttu-id="5d643-230">Este servicio realiza una solicitud de lista para obtener el tamaño del elemento de correo especificado.</span><span class="sxs-lookup"><span data-stu-id="5d643-230">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5d643-231">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-231">Input Parameters</span></span>

- <span data-ttu-id="5d643-232">**client_ptr**: Puntero a la instancia de cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-232">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="5d643-233">**mail_item**: Índice en el maildrop del cliente</span><span class="sxs-lookup"><span data-stu-id="5d643-233">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="5d643-234">**tamaño**: Puntero al tamaño del mensaje de correo</span><span class="sxs-lookup"><span data-stu-id="5d643-234">**size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="5d643-235">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="5d643-235">Return Values</span></span>

- <span data-ttu-id="5d643-236">**NX_SUCCESS**: (0x00) Elemento de correo recuperado correctamente</span><span class="sxs-lookup"><span data-stu-id="5d643-236">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="5d643-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de elemento de correo no válido</span><span class="sxs-lookup"><span data-stu-id="5d643-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="5d643-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) la carga de paquete de cliente es demasiado pequeña para la solicitud POP3.</span><span class="sxs-lookup"><span data-stu-id="5d643-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="5d643-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) el servidor responde con el estado de error</span><span class="sxs-lookup"><span data-stu-id="5d643-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="5d643-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada de índice de correo no válida</span><span class="sxs-lookup"><span data-stu-id="5d643-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="5d643-241">NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="5d643-241">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5d643-242">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="5d643-242">Allowed From</span></span>

<span data-ttu-id="5d643-243">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="5d643-243">Application code</span></span>

### <a name="example"></a><span data-ttu-id="5d643-244">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="5d643-244">Example</span></span>

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
