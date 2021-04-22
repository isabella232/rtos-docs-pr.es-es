---
title: 'Capítulo 3: Descripción de los servicios de cliente SMTP'
description: Este capítulo contiene una descripción de todos los servicios de cliente SMTP de NetX Duo (que se enumeran a continuación) en orden de uso en una aplicación cliente SMTP típica.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814578"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a><span data-ttu-id="af358-103">Capítulo 3: Descripción de los servicios de cliente SMTP</span><span class="sxs-lookup"><span data-stu-id="af358-103">Chapter 3 - Client description of SMTP Client services</span></span>

<span data-ttu-id="af358-104">Este capítulo contiene una descripción de todos los servicios de cliente SMTP de NetX Duo (que se enumeran a continuación) en orden de uso en una aplicación cliente SMTP típica.</span><span class="sxs-lookup"><span data-stu-id="af358-104">This chapter contains a description of all NetX Duo SMTP Client services (listed below) in order of usage in a typical SMTP Client application.</span></span>

> [!NOTE]
> <span data-ttu-id="af358-105">En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **_NX_DISABLE_ERROR_CHECKING_** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="af358-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **_NX_DISABLE_ERROR_CHECKING_** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nxd_smtp_client_create"></a><span data-ttu-id="af358-106">nxd_smtp_client_create</span><span class="sxs-lookup"><span data-stu-id="af358-106">nxd_smtp_client_create</span></span>

<span data-ttu-id="af358-107">Crea una instancia de cliente SMTP</span><span class="sxs-lookup"><span data-stu-id="af358-107">Create an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="af358-108">Prototipo</span><span class="sxs-lookup"><span data-stu-id="af358-108">Prototype</span></span>

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="af358-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="af358-109">Description</span></span>

<span data-ttu-id="af358-110">Este servicio crea una instancia de cliente SMTP en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="af358-110">This service creates an SMTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af358-111">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="af358-111">Input Parameters</span></span>

- <span data-ttu-id="af358-112">**client_ptr** Puntero al bloque de control del cliente SMTP.</span><span class="sxs-lookup"><span data-stu-id="af358-112">**client_ptr** Pointer to SMTP Client control block;</span></span>
- <span data-ttu-id="af358-113">**ip_ptr** Puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="af358-113">**ip_ptr** Pointer to IP instance;</span></span>
- <span data-ttu-id="af358-114">**packet_pool_ptr** Puntero al grupo de paquetes de cliente.</span><span class="sxs-lookup"><span data-stu-id="af358-114">**packet_pool_ptr** Pointer to Client packet pool;</span></span>
- <span data-ttu-id="af358-115">**username** Nombre de usuario terminado en NULL\*\* para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="af358-115">**username** NULL-terminated\*\* Username for authentication</span></span>
- <span data-ttu-id="af358-116">**password** Contraseña terminada en NULL para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="af358-116">**password** NULL-terminated password for authentication</span></span>
- <span data-ttu-id="af358-117">**from_address** Dirección del remitente terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="af358-117">**from_address** NULL-terminated sender’s address</span></span>
- <span data-ttu-id="af358-118">**client_domain** Nombre de dominio terminado en NULL.</span><span class="sxs-lookup"><span data-stu-id="af358-118">**client_domain** NULL-terminated domain name</span></span>
- <span data-ttu-id="af358-119">**authentication_type** Tipo de autenticación de cliente.</span><span class="sxs-lookup"><span data-stu-id="af358-119">**authentication_type** Client authentication type.</span></span> <span data-ttu-id="af358-120">Estos son los tipos que se admiten:</span><span class="sxs-lookup"><span data-stu-id="af358-120">Supported types are:</span></span>
  - <span data-ttu-id="af358-121">NX_SMTP_CLIENT_AUTH_LOGIN</span><span class="sxs-lookup"><span data-stu-id="af358-121">NX_SMTP_CLIENT_AUTH_LOGIN</span></span>
  - <span data-ttu-id="af358-122">NX_SMTP_CLIENT_AUTH_PLAIN</span><span class="sxs-lookup"><span data-stu-id="af358-122">NX_SMTP_CLIENT_AUTH_PLAIN</span></span>
  - <span data-ttu-id="af358-123">NX_SMTP_CLIENT_AUTH_NONE</span><span class="sxs-lookup"><span data-stu-id="af358-123">NX_SMTP_CLIENT_AUTH_NONE</span></span>
- <span data-ttu-id="af358-124">**server_address** Puntero a la dirección IP del servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="af358-124">**server_address** Pointer to SMTP Server IP address</span></span>
- <span data-ttu-id="af358-125">**server_port** Puerto TCP del servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="af358-125">**server_port** SMTP Server TCP port</span></span>

### <a name="return-values"></a><span data-ttu-id="af358-126">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="af358-126">Return Values</span></span>

- <span data-ttu-id="af358-127">**NX_SUCCESS** (0x00) Cliente SMTP creado correctamente.</span><span class="sxs-lookup"><span data-stu-id="af358-127">**NX_SUCCESS** (0x00) SMTP Client successfully created.</span></span> <span data-ttu-id="af358-128">Estado de creación de sockets TCP</span><span class="sxs-lookup"><span data-stu-id="af358-128">TCP socket creation status</span></span>
- <span data-ttu-id="af358-129">NX_SMTP_INVALID_PARAM (0xA5) Entrada no válida que no es de puntero.</span><span class="sxs-lookup"><span data-stu-id="af358-129">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="af358-130">NX_IP_ADDRESS_ERROR (0x21) Tipo de dirección IP no válida.</span><span class="sxs-lookup"><span data-stu-id="af358-130">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address type</span></span>
- <span data-ttu-id="af358-131">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="af358-131">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af358-132">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="af358-132">Allowed From</span></span>

<span data-ttu-id="af358-133">Código de aplicación</span><span class="sxs-lookup"><span data-stu-id="af358-133">Application Code</span></span>

### <a name="example"></a><span data-ttu-id="af358-134">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="af358-134">Example</span></span>

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a><span data-ttu-id="af358-135">nx_smtp_client_delete</span><span class="sxs-lookup"><span data-stu-id="af358-135">nx_smtp_client_delete</span></span>

<span data-ttu-id="af358-136">Elimina una instancia de cliente SMTP</span><span class="sxs-lookup"><span data-stu-id="af358-136">Delete an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="af358-137">Prototipo</span><span class="sxs-lookup"><span data-stu-id="af358-137">Prototype</span></span>

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="af358-138">Descripción</span><span class="sxs-lookup"><span data-stu-id="af358-138">Description</span></span>

<span data-ttu-id="af358-139">Este servicio elimina una instancia de cliente SMTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="af358-139">This service deletes a previously created SMTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af358-140">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="af358-140">Input Parameters</span></span>

- <span data-ttu-id="af358-141">**client_ptr** Puntero a la instancia de cliente SMTP.</span><span class="sxs-lookup"><span data-stu-id="af358-141">**client_ptr** Pointer to SMTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="af358-142">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="af358-142">Return Values</span></span>

- <span data-ttu-id="af358-143">**NX_SUCCESS** (0x00) Cliente eliminado correctamente.</span><span class="sxs-lookup"><span data-stu-id="af358-143">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="af358-144">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="af358-144">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af358-145">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="af358-145">Allowed From</span></span>

<span data-ttu-id="af358-146">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="af358-146">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af358-147">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="af358-147">Example</span></span>

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a><span data-ttu-id="af358-148">nx_smtp_mail_send</span><span class="sxs-lookup"><span data-stu-id="af358-148">nx_smtp_mail_send</span></span>

<span data-ttu-id="af358-149">Crea y envía un elemento de correo SMTP</span><span class="sxs-lookup"><span data-stu-id="af358-149">Create and send an SMTP mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="af358-150">Prototipo</span><span class="sxs-lookup"><span data-stu-id="af358-150">Prototype</span></span>

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a><span data-ttu-id="af358-151">Descripción</span><span class="sxs-lookup"><span data-stu-id="af358-151">Description</span></span>

<span data-ttu-id="af358-152">Este servicio crea y envía un elemento de correo SMTP.</span><span class="sxs-lookup"><span data-stu-id="af358-152">This service creates and sends an SMTP mail item.</span></span> <span data-ttu-id="af358-153">El cliente SMTP establece una conexión TCP con el servidor SMTP y envía una serie de comandos SMTP.</span><span class="sxs-lookup"><span data-stu-id="af358-153">The SMTP Client establishes a TCP connection with the SMTP Server and sends a series of SMTP commands.</span></span> <span data-ttu-id="af358-154">Si no se encuentra ningún error, transmitirá el mensaje de correo al servidor.</span><span class="sxs-lookup"><span data-stu-id="af358-154">If no errors are encountered, it will transmit the mail message to the Server.</span></span> <span data-ttu-id="af358-155">Independientemente de si el correo se envía correctamente, finalizará la conexión TCP y devolverá un estado que indica el resultado de la transmisión del correo.</span><span class="sxs-lookup"><span data-stu-id="af358-155">Regardless if the mail is sent successfully it will terminate the TCP connection and return a status indicating outcome of the mail transmission.</span></span> <span data-ttu-id="af358-156">La aplicación puede llamar a este servicio para tantos mensajes de correo como necesite enviar (sin límite).</span><span class="sxs-lookup"><span data-stu-id="af358-156">The application may call this service for as many mail messages as it needs to send without limit.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="af358-157">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="af358-157">Input Parameters</span></span>

- <span data-ttu-id="af358-158">**client_ptr** Puntero al cliente SMTP.</span><span class="sxs-lookup"><span data-stu-id="af358-158">**client_ptr** Pointer to SMTP Client</span></span>
- <span data-ttu-id="af358-159">**recipient_address** Dirección de destinatario terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="af358-159">**recipient_address** NULL-terminated recipient address.</span></span>
- <span data-ttu-id="af358-160">**subject** Texto de la línea de asunto terminado en NULL.</span><span class="sxs-lookup"><span data-stu-id="af358-160">**subject** NULL-terminated subject line text;.</span></span>
- <span data-ttu-id="af358-161">**priority** Nivel de prioridad con el que se entrega el correo.</span><span class="sxs-lookup"><span data-stu-id="af358-161">**priority** Priority level at which mail is delivered</span></span>
- <span data-ttu-id="af358-162">**mail_body** Puntero al mensaje de correo.</span><span class="sxs-lookup"><span data-stu-id="af358-162">**mail_body** Pointer to mail message</span></span>
- <span data-ttu-id="af358-163">**mail_body_length** Tamaño del mensaje de correo.</span><span class="sxs-lookup"><span data-stu-id="af358-163">**mail_body_length** Size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="af358-164">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="af358-164">Return Values</span></span>

- <span data-ttu-id="af358-165">**NX_SUCCESS** (0x00) Correo enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="af358-165">**NX_SUCCESS** (0x00) Mail successfully sent</span></span>
- <span data-ttu-id="af358-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) Instancia de cliente SMTP no inicializada para el resultado de la sesión SMTP.</span><span class="sxs-lookup"><span data-stu-id="af358-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP Client instance not initialized for SMTP session status Outcome of SMTP session</span></span>
- <span data-ttu-id="af358-167">NX_PTR_ERROR (0x07) Parámetro de puntero no válido.</span><span class="sxs-lookup"><span data-stu-id="af358-167">NX_PTR_ERROR (0x07) Invalid pointer parameter</span></span>
- <span data-ttu-id="af358-168">NX_SMTP_INVALID_PARAM (0xA5) Entrada no válida que no es de puntero.</span><span class="sxs-lookup"><span data-stu-id="af358-168">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="af358-169">NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="af358-169">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="af358-170">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="af358-170">Allowed From</span></span>

<span data-ttu-id="af358-171">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="af358-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="af358-172">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="af358-172">Example</span></span>

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
