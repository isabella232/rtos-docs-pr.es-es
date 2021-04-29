---
title: 'Capítulo 3: Descripción de los servicios del cliente POP3'
description: Este capítulo contiene una descripción de todos los servicios del cliente POP3 de NetX Duo (que se enumeran a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f7681c8f3fe161db8a37a82574ab7d5e9bf348e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814614"
---
# <a name="chapter-3---description-of-pop3-client-services"></a><span data-ttu-id="3e050-103">Capítulo 3: Descripción de los servicios del cliente POP3</span><span class="sxs-lookup"><span data-stu-id="3e050-103">Chapter 3 - Description of POP3 Client Services</span></span>

<span data-ttu-id="3e050-104">Este capítulo contiene una descripción de todos los servicios del cliente POP3 de NetX Duo (que se enumeran a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="3e050-104">This chapter contains a description of all NetX Duo POP3 Client services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="3e050-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="3e050-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="3e050-106">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="3e050-106">nx_pop3_client_create</span></span>

<span data-ttu-id="3e050-107">Crear una instancia de cliente POP3 para IPv4</span><span class="sxs-lookup"><span data-stu-id="3e050-107">Create a POP3 Client instance for IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="3e050-108">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3e050-108">Prototype</span></span>

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="3e050-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e050-109">Description</span></span>

<span data-ttu-id="3e050-110">Este servicio crea una instancia del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-110">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="3e050-111">Solo admite direcciones IPv4 del servidor de POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-111">It supports only IPv4 POP3 server addresses.</span></span>

<span data-ttu-id="3e050-112">Tenga en cuenta que la aplicación del dispositivo debe crear primero una instancia de IP y un grupo de paquetes para que el cliente POP3 transmita paquetes.</span><span class="sxs-lookup"><span data-stu-id="3e050-112">Note that the device application must first create an IP instance and a packet pool for the POP3 Client to transmit packets.</span></span> <span data-ttu-id="3e050-113">Este grupo de paquetes creado para su uso exclusivo por la tarea del cliente POP3 o el mismo grupo de paquetes usado en la creación de la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="3e050-113">This packet pool created for use exclusively by the POP3 Client task or the same packet pool used in the IP instance creation.</span></span> <span data-ttu-id="3e050-114">El grupo de paquetes también puede compartirse con el grupo de paquetes de controladores de Ethernet, pero esto tiene la desventaja de usar grupos de paquetes de gran tamaño cuya carga está pensada para recibir cargas de paquetes potencialmente grandes para que el cliente POP3 envíe paquetes de mensajes POP3 relativamente pequeños al servidor.</span><span class="sxs-lookup"><span data-stu-id="3e050-114">The packet pool may also be shared with the Ethernet driver packet pool but this has the disadvantage of using large packet pools whose payload is intended for receiving potentially large packets payload for the POP3 Client to send relatively small POP3 message packets to the server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3e050-115">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="3e050-115">Input Parameters</span></span>

- <span data-ttu-id="3e050-116">**client_ptr** Puntero al cliente que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="3e050-116">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="3e050-117">**APOP_authentication** Habilitar la autenticación de APOP.</span><span class="sxs-lookup"><span data-stu-id="3e050-117">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="3e050-118">**ip_ptr** Puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="3e050-118">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="3e050-119">**packet_pool_ptr** Puntero al grupo de paquetes del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-119">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="3e050-120">**server_ip_address** Dirección IPv4 del servidor de POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-120">**server_ip_address** POP3 server IPv4 address</span></span>
- <span data-ttu-id="3e050-121">**server_port** Puerto del servidor de POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-121">**server_port** POP3 server port</span></span>
- <span data-ttu-id="3e050-122">**client_name** Puntero al nombre del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-122">**client_name** Pointer to Client name</span></span>
- <span data-ttu-id="3e050-123">**client_password** Puntero a la contraseña del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-123">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="3e050-124">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3e050-124">Return Values</span></span>

- <span data-ttu-id="3e050-125">**NX_SUCCESS** (0x00) El cliente se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="3e050-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="3e050-126">**status** Finalización del estado de las llamadas al servicio NetX Duo y ThreadX.</span><span class="sxs-lookup"><span data-stu-id="3e050-126">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="3e050-127">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e050-127">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="3e050-128">NX_POP3_PARAM_ERROR (0xB1) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="3e050-128">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3e050-129">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="3e050-129">Allowed From</span></span>

<span data-ttu-id="3e050-130">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="3e050-130">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3e050-131">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3e050-131">Example</span></span>

```C
/* Create the POP3 Client. Note that the Client uses its password for its APOP shared
    secret. */

/* Set up user defined callback services. */
/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_ADDRESS IP_ADDRESS(192,2,2,92)
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. */
status = nx_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    POP3_SERVER_ADDRESS, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nxd_pop3_client_create"></a><span data-ttu-id="3e050-132">nxd_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="3e050-132">nxd_pop3_client_create</span></span>

<span data-ttu-id="3e050-133">Crear una instancia del cliente POP3 para IPv4 o IPv6</span><span class="sxs-lookup"><span data-stu-id="3e050-133">Create a POP3 Client instance for IPv4 or IPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="3e050-134">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3e050-134">Prototype</span></span>

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="3e050-135">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e050-135">Description</span></span>

<span data-ttu-id="3e050-136">Este servicio crea una instancia del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-136">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="3e050-137">Es compatible con las direcciones de servidor de POP3 IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="3e050-137">It supports both IPv4 and IPv6 POP3 server addresses.</span></span> <span data-ttu-id="3e050-138">Consulte el servicio *nx_pop3_client_create* descrito anteriormente para obtener más detalles sobre el proceso de creación del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-138">See the previously described *nx_pop3_client_create* service for more details on POP3 Client create process.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3e050-139">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="3e050-139">Input Parameters</span></span>

- <span data-ttu-id="3e050-140">**client_ptr** Puntero al cliente que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="3e050-140">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="3e050-141">**APOP_authentication** Habilitar la autenticación de APOP.</span><span class="sxs-lookup"><span data-stu-id="3e050-141">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="3e050-142">**ip_ptr** Puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="3e050-142">**ip_ptr** Pointer to IP instance</span></span>
- <span data-ttu-id="3e050-143">**packet_pool_ptr** Puntero al grupo de paquetes del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-143">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="3e050-144">**server_ip_address** Dirección IPv6 o IPv4 del servidor de POP3</span><span class="sxs-lookup"><span data-stu-id="3e050-144">**server_ip_address** POP3 server IPv6 or IPv4 address</span></span>
- <span data-ttu-id="3e050-145">**server_port** Puerto del servidor de POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-145">**server_port** POP3 server port</span></span>
- <span data-ttu-id="3e050-146">**client_name** Puntero a nombre de cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-146">**client_name**  Pointer to Client name</span></span>
- <span data-ttu-id="3e050-147">**client_password** Puntero a la contraseña del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-147">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="3e050-148">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3e050-148">Return Values</span></span>

- <span data-ttu-id="3e050-149">**NX_SUCCESS** (0x00) El cliente se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="3e050-149">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="3e050-150">**status** Finalización del estado de las llamadas al servicio NetX Duo y ThreadX.</span><span class="sxs-lookup"><span data-stu-id="3e050-150">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="3e050-151">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e050-151">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="3e050-152">NX_POP3_PARAM_ERROR (0xB1) Entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="3e050-152">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3e050-153">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="3e050-153">Allowed From</span></span>

<span data-ttu-id="3e050-154">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="3e050-154">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3e050-155">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3e050-155">Example</span></span>

```C
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. Also note the details of IPv6 address validation
    and enabling IPv6 and ICMPv6 services on the IP task are not shown here. See the
    NetX Duo User Guide for more details on this process.
*/
NXD_ADDRESS server_ip_address;

/* Set client IP interface address. */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0xf101;
server_ip_address.nxd_ip_address.v6[2] = 0;
server_ip_address.nxd_ip_address.v6[3] = 0x101;
status = nxd_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    &server_ip_address, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="3e050-156">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="3e050-156">nx_pop3_client_delete</span></span>

<span data-ttu-id="3e050-157">Eliminar una instancia de cliente POP3</span><span class="sxs-lookup"><span data-stu-id="3e050-157">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="3e050-158">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3e050-158">Prototype</span></span>

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="3e050-159">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e050-159">Description</span></span>

<span data-ttu-id="3e050-160">Este servicio elimina un cliente POP3 creado previamente.</span><span class="sxs-lookup"><span data-stu-id="3e050-160">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="3e050-161">No es que este servicio no elimine el grupo de paquetes del cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-161">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="3e050-162">La aplicación de dispositivo debe eliminar este recurso por separado si ya no se usa para el grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="3e050-162">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3e050-163">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="3e050-163">Input Parameters</span></span>

- <span data-ttu-id="3e050-164">**client_ptr** Puntero al cliente que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="3e050-164">**client_ptr** Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="3e050-165">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3e050-165">Return Values</span></span>

- <span data-ttu-id="3e050-166">**NX_SUCCESS** (0x00) Cliente eliminado correctamente</span><span class="sxs-lookup"><span data-stu-id="3e050-166">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="3e050-167">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e050-167">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3e050-168">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="3e050-168">Allowed From</span></span>

<span data-ttu-id="3e050-169">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="3e050-169">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3e050-170">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3e050-170">Example</span></span>

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="3e050-171">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="3e050-171">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="3e050-172">Eliminar un elemento de correo especificado del maildrop del cliente</span><span class="sxs-lookup"><span data-stu-id="3e050-172">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="3e050-173">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3e050-173">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a><span data-ttu-id="3e050-174">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e050-174">Description</span></span>

<span data-ttu-id="3e050-175">Este servicio elimina el elemento de correo especificado de la maildrop del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-175">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="3e050-176">Está pensado para después de descargar el elemento de correo, aunque algunos servidores POP3 pueden eliminar elementos de correo automáticamente después de que el cliente los solicite.</span><span class="sxs-lookup"><span data-stu-id="3e050-176">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3e050-177">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="3e050-177">Input Parameters</span></span>

- <span data-ttu-id="3e050-178">**client_ptr** Puntero a la instancia de cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-178">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="3e050-179">**mail_index** Índice en maildrop del cliente</span><span class="sxs-lookup"><span data-stu-id="3e050-179">**mail_index** Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="3e050-180">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3e050-180">Return Values</span></span>

- <span data-ttu-id="3e050-181">**NX_SUCCESS** (0X00) Eliminar solicitud correcta</span><span class="sxs-lookup"><span data-stu-id="3e050-181">**NX_SUCCESS** (0x00) Delete request successful</span></span>
- <span data-ttu-id="3e050-182">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Índice de elemento de correo no válido</span><span class="sxs-lookup"><span data-stu-id="3e050-182">**NX_POP3_INVALID_MAIL_ITEM**(0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="3e050-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) La carga de paquete de cliente es demasiado pequeña para la solicitud de POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3e050-184">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) El servidor responde con el estado de error.</span><span class="sxs-lookup"><span data-stu-id="3e050-184">**NX_POP3_SERVER_ERROR_STATUS**(0xB4) Server replies with error status</span></span>
- <span data-ttu-id="3e050-185">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Entrada de índice de correo no válida</span><span class="sxs-lookup"><span data-stu-id="3e050-185">NX_POP3_CLIENT_INVALID_INDEX(0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="3e050-186">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e050-186">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3e050-187">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="3e050-187">Allowed From</span></span>

<span data-ttu-id="3e050-188">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="3e050-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3e050-189">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3e050-189">Example</span></span>

```C
ULONG item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status =
    NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="3e050-190">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="3e050-190">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="3e050-191">Recuperar un elemento de correo especificado</span><span class="sxs-lookup"><span data-stu-id="3e050-191">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="3e050-192">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3e050-192">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

### <a name="description"></a><span data-ttu-id="3e050-193">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e050-193">Description</span></span>

<span data-ttu-id="3e050-194">Este servicio realiza una solicitud RETR para recuperar un elemento de correo desde el maildrop del cliente especificado por el índice mail_item.</span><span class="sxs-lookup"><span data-stu-id="3e050-194">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="3e050-195">Después de hacer una solicitud RETR y recibir una respuesta positiva del servidor, el cliente puede comenzar a descargar el mensaje de correo mediante el servicio *nx_pop3_client_mail_item_message_get*.</span><span class="sxs-lookup"><span data-stu-id="3e050-195">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="3e050-196">Tenga en cuenta que el servicio también proporciona el tamaño del elemento de correo solicitado extraído de la respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="3e050-196">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3e050-197">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="3e050-197">Input Parameters</span></span>

- <span data-ttu-id="3e050-198">**client_ptr** Puntero a la instancia de cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-198">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="3e050-199">**mail_item** Índice en maildrop del cliente</span><span class="sxs-lookup"><span data-stu-id="3e050-199">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="3e050-200">**item_size** Puntero al tamaño del mensaje de correo.</span><span class="sxs-lookup"><span data-stu-id="3e050-200">**item_size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="3e050-201">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3e050-201">Return Values</span></span>

- <span data-ttu-id="3e050-202">**NX_SUCCESS** (0x00) Elemento de correo recuperado correctamente</span><span class="sxs-lookup"><span data-stu-id="3e050-202">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="3e050-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Índice de elemento de correo no válido</span><span class="sxs-lookup"><span data-stu-id="3e050-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="3e050-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) La carga de paquete de cliente es demasiado pequeña para la solicitud de POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3e050-205">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) El servidor responde con el estado de error.</span><span class="sxs-lookup"><span data-stu-id="3e050-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="3e050-206">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada de índice de correo no válida</span><span class="sxs-lookup"><span data-stu-id="3e050-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="3e050-207">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e050-207">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3e050-208">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="3e050-208">Allowed From</span></span>

<span data-ttu-id="3e050-209">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="3e050-209">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3e050-210">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3e050-210">Example</span></span>

```C
ULONG item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="3e050-211">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="3e050-211">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="3e050-212">Recuperar el número de elementos de correo en maildrop</span><span class="sxs-lookup"><span data-stu-id="3e050-212">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="3e050-213">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3e050-213">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items,
    ULONG *maildrop_total_size);
```

### <a name="description"></a><span data-ttu-id="3e050-214">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e050-214">Description</span></span>

<span data-ttu-id="3e050-215">Este servicio realiza una solicitud de STAT para recuperar el número de elementos de correo y el tamaño total de los datos de los mensajes de correo desde el maildrop del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-215">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3e050-216">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="3e050-216">Input Parameters</span></span>

- <span data-ttu-id="3e050-217">**client_ptr** Puntero a la instancia de cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-217">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="3e050-218">**number_mail_item** Número de correo en maildrop del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-218">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="3e050-219">**maildrop_total_size** Puntero al tamaño de todo el mensaje de correo.</span><span class="sxs-lookup"><span data-stu-id="3e050-219">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="3e050-220">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3e050-220">Return Values</span></span>

- <span data-ttu-id="3e050-221">**NX_SUCCESS** (0x00) Elemento de correo recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="3e050-221">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="3e050-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Índice de elemento de correo no válido.</span><span class="sxs-lookup"><span data-stu-id="3e050-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="3e050-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) La carga de paquete de cliente es demasiado pequeña para la solicitud de POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3e050-224">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) El servidor responde con el estado de error.</span><span class="sxs-lookup"><span data-stu-id="3e050-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="3e050-225">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e050-225">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3e050-226">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="3e050-226">Allowed From</span></span>

<span data-ttu-id="3e050-227">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="3e050-227">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3e050-228">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3e050-228">Example</span></span>

```C
UINT number_mail_items;

ULONG maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
    &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="3e050-229">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="3e050-229">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="3e050-230">Recuperar el mensaje de elemento de correo especificado</span><span class="sxs-lookup"><span data-stu-id="3e050-230">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="3e050-231">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3e050-231">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a><span data-ttu-id="3e050-232">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e050-232">Description</span></span>

<span data-ttu-id="3e050-233">Este servicio recupera el mensaje de elemento de correo, el tamaño del mensaje de correo y si es el último paquete del mensaje de correo.</span><span class="sxs-lookup"><span data-stu-id="3e050-233">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="3e050-234">Si final_packet es NX_TRUE, el paquete al que apunta recv_packet_ptr es el paquete final en el mensaje del elemento de correo.</span><span class="sxs-lookup"><span data-stu-id="3e050-234">If final_packet is NX_TRUE the packet pointed to by recv_packet_ptr is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3e050-235">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="3e050-235">Input Parameters</span></span>

- <span data-ttu-id="3e050-236">**client_ptr** Puntero a la instancia de cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-236">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="3e050-237">**recv_packet_ptr** Paquete recibido de datos de mensaje.</span><span class="sxs-lookup"><span data-stu-id="3e050-237">**recv_packet_ptr** Received packet of message data</span></span>
- <span data-ttu-id="3e050-238">**number_mail_item** Número de correo en maildrop del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-238">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="3e050-239">**maildrop_total_size** Puntero al tamaño de todo el mensaje de correo.</span><span class="sxs-lookup"><span data-stu-id="3e050-239">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="3e050-240">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3e050-240">Return Values</span></span>

- <span data-ttu-id="3e050-241">**NX_SUCCESS** (0x00) Elemento de correo recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="3e050-241">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="3e050-242">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) La carga de paquete de cliente es demasiado pequeña para la solicitud de POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3e050-243">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e050-243">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3e050-244">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="3e050-244">Allowed From</span></span>

<span data-ttu-id="3e050-245">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="3e050-245">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3e050-246">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3e050-246">Example</span></span>

```C
NX_PACKET *recv_packet_ptr;

ULONG bytes_retrieved;

UINT final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
    bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="3e050-247">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="3e050-247">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="3e050-248">Recupera el tamaño del elemento de correo especificado</span><span class="sxs-lookup"><span data-stu-id="3e050-248">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="3e050-249">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3e050-249">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_size_get(
    NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *size);
```

### <a name="description"></a><span data-ttu-id="3e050-250">Descripción</span><span class="sxs-lookup"><span data-stu-id="3e050-250">Description</span></span>

<span data-ttu-id="3e050-251">Este servicio realiza una solicitud de lista para obtener el tamaño del elemento de correo especificado.</span><span class="sxs-lookup"><span data-stu-id="3e050-251">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3e050-252">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="3e050-252">Input Parameters</span></span>

- <span data-ttu-id="3e050-253">**client_ptr** Puntero a la instancia de cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-253">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="3e050-254">**mail_item** Índice en maildrop del cliente.</span><span class="sxs-lookup"><span data-stu-id="3e050-254">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="3e050-255">**tamaño** Puntero al tamaño del mensaje de correo.</span><span class="sxs-lookup"><span data-stu-id="3e050-255">**size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="3e050-256">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3e050-256">Return Values</span></span>

- <span data-ttu-id="3e050-257">**NX_SUCCESS** (0x00) Elemento de correo recuperado correctamente.</span><span class="sxs-lookup"><span data-stu-id="3e050-257">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="3e050-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Índice de elemento de correo no válido.</span><span class="sxs-lookup"><span data-stu-id="3e050-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="3e050-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) La carga de paquete de cliente es demasiado pequeña para la solicitud de POP3.</span><span class="sxs-lookup"><span data-stu-id="3e050-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3e050-260">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) El servidor responde con el estado de error.</span><span class="sxs-lookup"><span data-stu-id="3e050-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="3e050-261">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada de índice de correo no válida</span><span class="sxs-lookup"><span data-stu-id="3e050-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="3e050-262">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e050-262">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3e050-263">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="3e050-263">Allowed From</span></span>

<span data-ttu-id="3e050-264">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="3e050-264">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3e050-265">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3e050-265">Example</span></span>

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
