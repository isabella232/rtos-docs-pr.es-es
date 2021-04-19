---
title: 'Capítulo 3: Descripción de los servicios del cliente MQTT de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del cliente MQTT de NetX Duo (se enumeran a continuación) por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814650"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a><span data-ttu-id="e6c59-103">Capítulo 3: Descripción de los servicios del cliente MQTT de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e6c59-103">Chapter 3 - Description of Azure RTOS NetX Duo MQTT client services</span></span>

<span data-ttu-id="e6c59-104">Este capítulo contiene una descripción de todos los servicios del cliente MQTT de Azure RTOS NetX Duo (se enumeran a continuación) por orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="e6c59-104">This chapter contains a description of all Azure RTOS NetX Duo MQTT client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="e6c59-105">En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="e6c59-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="e6c59-106">**nxd_mqtt_client_create** *Crear la instancia de cliente MQTT*</span><span class="sxs-lookup"><span data-stu-id="e6c59-106">**nxd_mqtt_client_create** *Create MQTT client instance*</span></span>
- <span data-ttu-id="e6c59-107">**nxd_mqtt_client_will_message_set** *Establecer el mensaje Will*</span><span class="sxs-lookup"><span data-stu-id="e6c59-107">**nxd_mqtt_client_will_message_set** *Set the will message*</span></span>
- <span data-ttu-id="e6c59-108">**nxd_mqtt_client_client_login_set** *Establecer el nombre de usuario y contraseña de inicio de sesión del cliente MQTT*</span><span class="sxs-lookup"><span data-stu-id="e6c59-108">**nxd_mqtt_client_client_login_set** *Set MQTT client login username and password*</span></span>
- <span data-ttu-id="e6c59-109">**nxd_mqtt_client_connect** *Conectar el cliente MQTT al agente*</span><span class="sxs-lookup"><span data-stu-id="e6c59-109">**nxd_mqtt_client_connect** *Connect MQTT Client to the broker*</span></span>
- <span data-ttu-id="e6c59-110">**nxd_mqtt_client_secure_connect** *Conectar el cliente MQTT al agente con seguridad TLS*</span><span class="sxs-lookup"><span data-stu-id="e6c59-110">**nxd_mqtt_client_secure_connect** *Connect MQTT client to the broker with TLS security*</span></span>
- <span data-ttu-id="e6c59-111">**nxd_mqtt_client_publish** *Publicar un mensaje a través del agente.*</span><span class="sxs-lookup"><span data-stu-id="e6c59-111">**nxd_mqtt_client_publish** *Publish a message through the broker.*</span></span>
- <span data-ttu-id="e6c59-112">**nxd_mqtt_client_subscribe** *Suscribirse a un tema*</span><span class="sxs-lookup"><span data-stu-id="e6c59-112">**nxd_mqtt_client_subscribe** *Subscribe to a topic*</span></span>
- <span data-ttu-id="e6c59-113">**nxd_mqtt_client_unsubscribe** *Cancelar la suscripción a un tema*</span><span class="sxs-lookup"><span data-stu-id="e6c59-113">**nxd_mqtt_client_unsubscribe** *Unsubscribe from a topic*</span></span>
- <span data-ttu-id="e6c59-114">**nxd_mqtt_client_receive_notify_set** *Establecer la función de devolución de llamada de la notificación que indica la recepción de un mensaje de MQTT*</span><span class="sxs-lookup"><span data-stu-id="e6c59-114">**nxd_mqtt_client_receive_notify_set** *Set MQTT message receive notify callback function*</span></span>
- <span data-ttu-id="e6c59-115">**nxd_mqtt_client_message_get** *Recuperar un mensaje del agente*</span><span class="sxs-lookup"><span data-stu-id="e6c59-115">**nxd_mqtt_client_message_get** *Retrieve a message from the broker*</span></span>
- <span data-ttu-id="e6c59-116">**nxd_mqtt_client_disconnect_notify_set** *Establecer la función de devolución de llamada de la notificación que indica la desconexión de MQTT*</span><span class="sxs-lookup"><span data-stu-id="e6c59-116">**nxd_mqtt_client_disconnect_notify_set** *Set MQTT message disconnect notify callback function*</span></span>
- <span data-ttu-id="e6c59-117">**nxd_mqtt_client_disconnect** *Desconectar el cliente MQTT del agente*</span><span class="sxs-lookup"><span data-stu-id="e6c59-117">**nxd_mqtt_client_disconnect** *Disconnect MQTT client from the broker*</span></span>
- <span data-ttu-id="e6c59-118">**nxd_mqtt_client_delete** *Eliminar la instancia de cliente MQTT*</span><span class="sxs-lookup"><span data-stu-id="e6c59-118">**nxd_mqtt_client_delete** *Delete the MQTT client instance*</span></span>

## <a name="nxd_mqtt_client_create"></a><span data-ttu-id="e6c59-119">nxd_mqtt_client_create</span><span class="sxs-lookup"><span data-stu-id="e6c59-119">nxd_mqtt_client_create</span></span>

<span data-ttu-id="e6c59-120">Crear instancia de cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="e6c59-120">Create MQTT Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-121">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-121">Prototype</span></span>

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="e6c59-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-122">Description</span></span>

<span data-ttu-id="e6c59-123">Este servicio crea una instancia de cliente MQTT en la instancia de IP especificada.</span><span class="sxs-lookup"><span data-stu-id="e6c59-123">This service creates an MQTT Client instance on the specified IP instance.</span></span> <span data-ttu-id="e6c59-124">La cadena *client_id* se pasa al servidor durante la fase de conexión de MQTT como *Identificador de cliente (ClientId)* .</span><span class="sxs-lookup"><span data-stu-id="e6c59-124">The *client_id* string is passed to the server during MQTT connection phase as the *Client Identifier (ClientId)*.</span></span> <span data-ttu-id="e6c59-125">También crea los recursos ThreadX necesarios (subproceso de la tarea cliente MQTT, exclusión mutua, grupo de marcas de evento y socket TCP).</span><span class="sxs-lookup"><span data-stu-id="e6c59-125">It also creates the necessary ThreadX resources (MQTT Client task thread, mutex, event flag group, and TCP socket).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-126">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-126">Input Parameters</span></span>

- <span data-ttu-id="e6c59-127">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-127">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-128">**client_name** Cadena de nombre de cliente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-128">**client_name** Client name string.</span></span>
- <span data-ttu-id="e6c59-129">**client_id** Cadena de identificador de cliente que se usa durante la fase de conexión.</span><span class="sxs-lookup"><span data-stu-id="e6c59-129">**client_id** Client ID string used during connection phase.</span></span> <span data-ttu-id="e6c59-130">El agente MQTT usa este client_id para identificar de forma única a un cliente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-130">MQTT broker uses this client_id to uniquely identify a client.</span></span>
- <span data-ttu-id="e6c59-131">**client_id_length** Longitud de la cadena de identificador de cliente, en bytes.</span><span class="sxs-lookup"><span data-stu-id="e6c59-131">**client_id_length** Length of the client ID string, in bytes.</span></span>
- <span data-ttu-id="e6c59-132">**ip_ptr** Puntero a la instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="e6c59-132">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="e6c59-133">**pool_ptr** Puntero al grupo de paquetes que el cliente MQTT usa para su funcionamiento.</span><span class="sxs-lookup"><span data-stu-id="e6c59-133">**pool_ptr** Pointer to a packet pool MQTT client uses for its operation.</span></span>
- <span data-ttu-id="e6c59-134">**stack_ptr** Área de pila para el subproceso del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-134">**stack_ptr** Stack area for the MQTT Client thread.</span></span>
- <span data-ttu-id="e6c59-135">**stack_size** Tamaño del área de la pila, en bytes.</span><span class="sxs-lookup"><span data-stu-id="e6c59-135">**stack_size** Size of the stack area, in bytes.</span></span>
- <span data-ttu-id="e6c59-136">**mqtt_thread_priority** Prioridad del subproceso MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-136">**mqtt_thread_priority** The priority of the MQTT Thread.</span></span>
- <span data-ttu-id="e6c59-137">**memory_ptr** En desuso.</span><span class="sxs-lookup"><span data-stu-id="e6c59-137">**memory_ptr** Deprecated.</span></span> <span data-ttu-id="e6c59-138">Ya no se usa.</span><span class="sxs-lookup"><span data-stu-id="e6c59-138">Not used anymore.</span></span>
- <span data-ttu-id="e6c59-139">**memory_size** En desuso.</span><span class="sxs-lookup"><span data-stu-id="e6c59-139">**memory_size** Deprecated.</span></span> <span data-ttu-id="e6c59-140">Ya no se usa.</span><span class="sxs-lookup"><span data-stu-id="e6c59-140">Not used anymore.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-141">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-141">Return Values</span></span>

- <span data-ttu-id="e6c59-142">**NXD_MQTT_SUCCESS** (0x00) El cliente MQTT se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-142">**NXD_MQTT_SUCCESS** (0x00) Successfully created MQTT client.</span></span>
- <span data-ttu-id="e6c59-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna</span><span class="sxs-lookup"><span data-stu-id="e6c59-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e6c59-144">NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-144">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer.</span></span>
- <span data-ttu-id="e6c59-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Cadena de tema Will, will_retrain_flag o will_QoS no válidos.</span><span class="sxs-lookup"><span data-stu-id="e6c59-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-146">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-146">Allowed From</span></span>

<span data-ttu-id="e6c59-147">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-148">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-148">Example</span></span>

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a><span data-ttu-id="e6c59-149">nxd_mqtt_client_will_message_set</span><span class="sxs-lookup"><span data-stu-id="e6c59-149">nxd_mqtt_client_will_message_set</span></span>

<span data-ttu-id="e6c59-150">Establece el mensaje Will.</span><span class="sxs-lookup"><span data-stu-id="e6c59-150">Sets the Will message</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-151">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-151">Prototype</span></span>

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a><span data-ttu-id="e6c59-152">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-152">Description</span></span>

<span data-ttu-id="e6c59-153">Este servicio establece el tema Will opcional y el mensaje Will antes de que el cliente se conecte al servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-153">This service sets the optional will topic and will message before the client connects to the server.</span></span> <span data-ttu-id="e6c59-154">El tema Will debe ser una cadena con codificación UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e6c59-154">Will topic must be UTF-8 encoded string.</span></span>

<span data-ttu-id="e6c59-155">Si se establece, el mensaje Will se transmite al agente como parte del mensaje CONNECT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-155">The will message, if set, is transmitted to the broker as part of the CONNECT message.</span></span> <span data-ttu-id="e6c59-156">Por lo tanto, las aplicaciones que quieran usar el mensaje Will deben usar este servicio antes de que se realice la conexión MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-156">Therefore application wishing to use will message must use this service before the MQTT connection is make.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-157">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-157">Input Parameters</span></span>

- <span data-ttu-id="e6c59-158">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-158">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-159">**will_topic** Cadena de tema Will con codificación UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e6c59-159">**will_topic** UTF-8 encoded will topic string.</span></span> <span data-ttu-id="e6c59-160">El tema Will debe estar presente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-160">Will topic must be present.</span></span> <span data-ttu-id="e6c59-161">El autor de la llamada debe hacer que la cadena will_topic siga siendo válida hasta que se realice la llamada a *nx_mqtt_client_connect*.</span><span class="sxs-lookup"><span data-stu-id="e6c59-161">Caller must keep the will_topic string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="e6c59-162">**will_topic_length** Número de bytes en la cadena de tema Will.</span><span class="sxs-lookup"><span data-stu-id="e6c59-162">**will_topic_length** Number of bytes in the will topic string</span></span>
- <span data-ttu-id="e6c59-163">**will_message** Mensaje Will definido por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e6c59-163">**will_message** Application defined will message.</span></span> <span data-ttu-id="e6c59-164">Si no se requiere el mensaje Will, la aplicación puede establecer este campo en *NX_NULL*.</span><span class="sxs-lookup"><span data-stu-id="e6c59-164">If will message is not required, application can set this field to *NX_NULL.*</span></span>
- <span data-ttu-id="e6c59-165">**will_message_length** Número de bytes en la cadena de mensaje Will.</span><span class="sxs-lookup"><span data-stu-id="e6c59-165">**will_message_length** Number of bytes in the will message string.</span></span> <span data-ttu-id="e6c59-166">Si will_message se establece en NULL, will_message_length debe establecerse en 0.</span><span class="sxs-lookup"><span data-stu-id="e6c59-166">If will_message is set to NULL, will_message_length must be set to 0.</span></span>
- <span data-ttu-id="e6c59-167">**will_retain_flag** Define si el servidor publicará el mensaje Will como un mensaje retenido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-167">**will_retain_flag** Whether the server publishes the will message as a retained message.</span></span> <span data-ttu-id="e6c59-168">Los valores válidos son *NX_TRUE* o *NX_FALSE*.</span><span class="sxs-lookup"><span data-stu-id="e6c59-168">Valid values are *NX_TRUE* or *NX_FALSE.*</span></span>
- <span data-ttu-id="e6c59-169">**will_QoS** Valor de QoS que usa el servidor cuando se envía el mensaje Will.</span><span class="sxs-lookup"><span data-stu-id="e6c59-169">**will_QoS** QoS value used by the server when sending will message.</span></span> <span data-ttu-id="e6c59-170">Los valores válidos son 0 ó 1.</span><span class="sxs-lookup"><span data-stu-id="e6c59-170">Valid values are 0 or 1.</span></span>  

### <a name="return-values"></a><span data-ttu-id="e6c59-171">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-171">Return Values</span></span>

- <span data-ttu-id="e6c59-172">**NXD_MQTT_SUCCESS** (0x00) (0x00) El mensaje Will se configuró correctamente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-172">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="e6c59-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) No se admiten los mensajes de QoS nivel 2.</span><span class="sxs-lookup"><span data-stu-id="e6c59-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="e6c59-174">NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-174">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="e6c59-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Cadena de tema Will, will_retrain_flag o will_QoS no válidos.</span><span class="sxs-lookup"><span data-stu-id="e6c59-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-176">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-176">Allowed From</span></span>

<span data-ttu-id="e6c59-177">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-178">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-178">Example</span></span>

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a><span data-ttu-id="e6c59-179">nxd_mqtt_client_login_set</span><span class="sxs-lookup"><span data-stu-id="e6c59-179">nxd_mqtt_client_login_set</span></span>

<span data-ttu-id="e6c59-180">Establece el nombre de usuario y contraseña de inicio de sesión del cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="e6c59-180">Sets MQTT client login username and password</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-181">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-181">Prototype</span></span>

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a><span data-ttu-id="e6c59-182">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-182">Description</span></span>

<span data-ttu-id="e6c59-183">Este servicio establece el nombre de usuario y la contraseña, que se usan durante la fase de conexión de MQTT para el inicio de sesión en la autenticación.</span><span class="sxs-lookup"><span data-stu-id="e6c59-183">This service sets the username and password, which is used during MQTT connection phase for log in authentication purpose.</span></span>

<span data-ttu-id="e6c59-184">Iniciar sesión en el cliente MQTT con el nombre de usuario y la contraseña es opcional.</span><span class="sxs-lookup"><span data-stu-id="e6c59-184">The MQTT client login with username and password is optional.</span></span> <span data-ttu-id="e6c59-185">En situaciones en las que el servidor requiere un nombre de usuario y una contraseña, ambos valores se deben establecer antes de establecer la conexión.</span><span class="sxs-lookup"><span data-stu-id="e6c59-185">In situations where the server requires a user name and password, the user name and password must be set before the connection is established.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-186">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-186">Input Parameters</span></span>

- <span data-ttu-id="e6c59-187">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-187">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-188">**username** Cadena de nombre de usuario con codificación UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e6c59-188">**username** UTF-8 encoded user name string.</span></span> <span data-ttu-id="e6c59-189">El autor de la llamada debe hacer que la cadena username siga siendo válida hasta que se realice la llamada a *nx_mqtt_client_connect*.</span><span class="sxs-lookup"><span data-stu-id="e6c59-189">Caller must keep the username string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="e6c59-190">**username_length** Número de bytes en la cadena de nombre de usuario.</span><span class="sxs-lookup"><span data-stu-id="e6c59-190">**username_length** Number of bytes in the username string</span></span>
- <span data-ttu-id="e6c59-191">**password** Cadena de contraseña.</span><span class="sxs-lookup"><span data-stu-id="e6c59-191">**password** Password string.</span></span> <span data-ttu-id="e6c59-192">Si no se requiere una contraseña, este campo se puede establecer en NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="e6c59-192">If password is not required, this field may be set to NX_NULL.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-193">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-193">Return Values</span></span>

- <span data-ttu-id="e6c59-194">**NXD_MQTT_SUCCESS** (0x00) (0x00) El mensaje Will se configuró correctamente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-194">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="e6c59-195">NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-195">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="e6c59-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Cadena de nombre de usuario o contraseña no válidos.</span><span class="sxs-lookup"><span data-stu-id="e6c59-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid username string or the password string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-197">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-197">Allowed From</span></span>

<span data-ttu-id="e6c59-198">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-199">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-199">Example</span></span>

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a><span data-ttu-id="e6c59-200">nxd_mqtt_client_connect</span><span class="sxs-lookup"><span data-stu-id="e6c59-200">nxd_mqtt_client_connect</span></span>

<span data-ttu-id="e6c59-201">Conecta el cliente MQTT al agente</span><span class="sxs-lookup"><span data-stu-id="e6c59-201">Connect MQTT Client to the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-202">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-202">Prototype</span></span>

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="e6c59-203">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-203">Description</span></span>

<span data-ttu-id="e6c59-204">Este servicio inicia una conexión al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-204">This service initiates a connection to the broker.</span></span> <span data-ttu-id="e6c59-205">En primer lugar, se enlaza a un socket TCP y, a continuación, realiza una conexión TCP.</span><span class="sxs-lookup"><span data-stu-id="e6c59-205">First it binds a TCP socket, then makes a TCP connection.</span></span> <span data-ttu-id="e6c59-206">Suponiendo que se realiza correctamente, crea un temporizador si está habilitada la característica Mantener conexión de MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-206">Assuming that succeeds, it creates a timer if the MQTT keep alive feature is enabled.</span></span> <span data-ttu-id="e6c59-207">A continuación, se conecta con el servidor MQTT (agente).</span><span class="sxs-lookup"><span data-stu-id="e6c59-207">Then it connects with the MQTT server (broker).</span></span>

<span data-ttu-id="e6c59-208">Tenga en cuenta que este servicio crea una conexión MQTT sin protección TLS.</span><span class="sxs-lookup"><span data-stu-id="e6c59-208">Note that this service creates an MQTT connection with no TLS protection.</span></span> <span data-ttu-id="e6c59-209">Para crear una conexión MQTT segura, la aplicación debe usar el servicio ***nxd_mqtt_client_secure_connect().***</span><span class="sxs-lookup"><span data-stu-id="e6c59-209">To create a secure MQTT connection, the application shall use the service ***nxd_mqtt_client_secure_connect().***</span></span>

<span data-ttu-id="e6c59-210">Una vez establecida la conexión, si el cliente establece *clean_session* en NX_FALSE, el cliente volverá a transmitir los mensajes almacenados que todavía no se hayan confirmado.</span><span class="sxs-lookup"><span data-stu-id="e6c59-210">Upon the connection, if the client sets the *clean_session* to NX_FALSE, the client will retransmit any messages stored that have not been acknowledged yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-211">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-211">Input Parameters</span></span>

- <span data-ttu-id="e6c59-212">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-212">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-213">**server_IP** Dirección IP del agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-213">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="e6c59-214">**server_port** Número de puerto del agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-214">**server_port** Broker port number.</span></span> <span data-ttu-id="e6c59-215">El puerto predeterminado para MQTT está definido como **_NXD_MQTT_PORT_** (1883).</span><span class="sxs-lookup"><span data-stu-id="e6c59-215">The default port for MQTT is defined as **_NXD_MQTT_PORT_** (1883).</span></span>
- <span data-ttu-id="e6c59-216">**keep_alive** Valor de Mantener conexión, en segundos, que se va a usar durante la sesión.</span><span class="sxs-lookup"><span data-stu-id="e6c59-216">**keep_alive** The keep alive value, in seconds, to be used during the session.</span></span> <span data-ttu-id="e6c59-217">El valor indica el tiempo máximo entre dos mensajes de control de MQTT que se envían al agente antes de que este agote el tiempo de espera del cliente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-217">The value indicates the maximum time between two MQTT control messages being sent to the broker before the broker times out this client.</span></span> <span data-ttu-id="e6c59-218">El valor 0 desactiva la característica keep-alive.</span><span class="sxs-lookup"><span data-stu-id="e6c59-218">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="e6c59-219">**clean_session** Si el servidor debe iniciar la limpieza de esta sesión.</span><span class="sxs-lookup"><span data-stu-id="e6c59-219">**clean_session** Whether the server shall start this session clean.</span></span> <span data-ttu-id="e6c59-220">Las opciones válidas son **_NX_TRUE_ *_ o _* _NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="e6c59-220">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="e6c59-221">**wait_option** Tiempo de espera de la conexión.</span><span class="sxs-lookup"><span data-stu-id="e6c59-221">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-222">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-222">Return Values</span></span>

- <span data-ttu-id="e6c59-223">**NXD_MQTT_SUCCESS** (0x00) Conexión a MQTT correcta.</span><span class="sxs-lookup"><span data-stu-id="e6c59-223">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT connection</span></span>
- <span data-ttu-id="e6c59-224">**NXD_MQTT_ALREADY_CONNECTED** (0X10001) El cliente ya está conectado al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="e6c59-225">**NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="e6c59-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.</span><span class="sxs-lookup"><span data-stu-id="e6c59-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e6c59-227">**NXD_MQTT_CONNECT_FAILURE** (0X10005) No se pudo conectar al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="e6c59-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No pueden enviar mensajes al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="e6c59-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) El servidor respondió con un error.</span><span class="sxs-lookup"><span data-stu-id="e6c59-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error</span></span>
- <span data-ttu-id="e6c59-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="e6c59-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="e6c59-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="e6c59-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="e6c59-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="e6c59-235">NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-235">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-236">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-236">Allowed From</span></span>

<span data-ttu-id="e6c59-237">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-238">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-238">Example</span></span>

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a><span data-ttu-id="e6c59-239">nxd_mqtt_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="e6c59-239">nxd_mqtt_client_secure_connect</span></span>

<span data-ttu-id="e6c59-240">Conecta el cliente MQTT al agente con seguridad TLS</span><span class="sxs-lookup"><span data-stu-id="e6c59-240">Connect MQTT client to the broker with TLS security</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-241">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-241">Prototype</span></span>

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="e6c59-242">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-242">Description</span></span>

<span data-ttu-id="e6c59-243">Este servicio es idéntico a ***nxd_mqtt_client_connect***, salvo que la conexión pasa a través de la capa TLS en lugar de TCP.</span><span class="sxs-lookup"><span data-stu-id="e6c59-243">This service is identical to ***nxd_mqtt_client_connect*** except that the connection goes through TLS layer instead of TCP.</span></span> <span data-ttu-id="e6c59-244">Por lo tanto, se protege la comunicación entre el cliente y el agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-244">Therefore, communication between the client and the broker is secured.</span></span>

<span data-ttu-id="e6c59-245">El elemento *tls_setup* definido por el usuario es una función de devolución de llamada que usa el cliente MQTT antes de realizar una conexión de cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-245">The user-defined *tls_setup* is a callback function that the MQTT client uses prior to making a MQTT client connection.</span></span> <span data-ttu-id="e6c59-246">La aplicación inicializará NetX Secure TLS, configurará los parámetros de seguridad y cargará los certificados pertinentes que se usarán durante el protocolo de enlace TLS.</span><span class="sxs-lookup"><span data-stu-id="e6c59-246">The application shall initialize NetX Secure TLS, configure security parameters, and load relevant certificates to be used during TLS handshake.</span></span> <span data-ttu-id="e6c59-247">El protocolo de enlace TLS real se produce después de establecer una conexión TCP en el puerto TLS MQTT del agente (puerto TCP predeterminado 8883).</span><span class="sxs-lookup"><span data-stu-id="e6c59-247">The actual TLS handshake happens after a TCP connection is established on the broker's MQTT TLS port (default TCP port 8883).</span></span> <span data-ttu-id="e6c59-248">Una vez que el protocolo de enlace de TLS se ha realizado correctamente, el paquete de control CONNECT de MQTT se envía a través de TLS.</span><span class="sxs-lookup"><span data-stu-id="e6c59-248">Once the TLS handshake is successful, the MQTT CONNECT control packet is sent via TLS.</span></span>

<span data-ttu-id="e6c59-249">Para establecer conexiones seguras, la biblioteca de NetX Secure TLS debe estar disponible y el cliente MQTT de NetX Duo debe compilarse con el valor ***NX_SECURE_ENABLE*** definido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-249">To make secure connections, the NetX Secure TLS library must be available, and the NetX Duo MQTT client must be built with ***NX_SECURE_ENABLE*** defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-250">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-250">Input Parameters</span></span>

- <span data-ttu-id="e6c59-251">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-251">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-252">**server_IP** Dirección IP del agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-252">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="e6c59-253">**server_port** Número de puerto del agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-253">**server_port** Broker port number.</span></span> <span data-ttu-id="e6c59-254">El puerto predeterminado para MQTT está definido como **_NXD_MQTT_TLS_PORT_** (8883).</span><span class="sxs-lookup"><span data-stu-id="e6c59-254">The default port for MQTT isdefined as **_NXD_MQTT_TLS_PORT_** (8883).</span></span>
- <span data-ttu-id="e6c59-255">**tls_setup** Función de devolución de llamada de configuración de TLS proporcionada por el usuario.</span><span class="sxs-lookup"><span data-stu-id="e6c59-255">**tls_setup** User-provided TLS Setup callback function.</span></span> <span data-ttu-id="e6c59-256">Esta función de devolución de llamada se invoca para establecer los parámetros de conexión del cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="e6c59-256">This callback function is invoked to set up TLS client connection parameters.</span></span>
- <span data-ttu-id="e6c59-257">**keep_alive** Valor de Mantener conexión que se va a usar durante la sesión.</span><span class="sxs-lookup"><span data-stu-id="e6c59-257">**keep_alive** The keep-alive value to be used during the session.</span></span> <span data-ttu-id="e6c59-258">El valor 0 desactiva la característica keep-alive.</span><span class="sxs-lookup"><span data-stu-id="e6c59-258">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="e6c59-259">**clean_session** Si el servidor debe o no iniciar la limpieza de esta sesión.</span><span class="sxs-lookup"><span data-stu-id="e6c59-259">**clean_session** Whether or not the server shall start this session clean.</span></span> <span data-ttu-id="e6c59-260">Las opciones válidas son **_NX_TRUE_ *_ o _* _NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="e6c59-260">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="e6c59-261">**wait_option** Tiempo de espera de la conexión.</span><span class="sxs-lookup"><span data-stu-id="e6c59-261">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-262">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-262">Return Values</span></span>

- <span data-ttu-id="e6c59-263">**NXD_MQTT_SUCCESS** (0x00) Se estableció correctamente una conexión de cliente MQTT a través de TLS.</span><span class="sxs-lookup"><span data-stu-id="e6c59-263">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT client connection established via TLS.</span></span>
- <span data-ttu-id="e6c59-264">**NXD_MQTT_ALREADY_CONNECTED** (0X10001) El cliente ya está conectado al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="e6c59-265">**NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="e6c59-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.</span><span class="sxs-lookup"><span data-stu-id="e6c59-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e6c59-267">**NXD_MQTT_CONNECT_FAILURE** (0X10005) No se pudo conectar al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="e6c59-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No pueden enviar mensajes al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="e6c59-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) El servidor respondió con un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="e6c59-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error message.</span></span>
- <span data-ttu-id="e6c59-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="e6c59-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="e6c59-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="e6c59-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="e6c59-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Código de respuesta del servidor.</span><span class="sxs-lookup"><span data-stu-id="e6c59-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="e6c59-275">NX_PTR_ERROR (0x07) Bloque de control o estructura de dirección de servidor MQTT no válidos.</span><span class="sxs-lookup"><span data-stu-id="e6c59-275">NX_PTR_ERROR (0x07) Invalid MQTT control block or sever address structure.</span></span>
- <span data-ttu-id="e6c59-276">NX_INVALID_PORT (0x46) El puerto del servidor no puede ser 0.</span><span class="sxs-lookup"><span data-stu-id="e6c59-276">NX_INVALID_PORT (0x46) Server port cannot be 0.</span></span>
- <span data-ttu-id="e6c59-277">NXD_MQTT_INVALID_PARAMETER (0x10009) Error de entrada del parámetro.</span><span class="sxs-lookup"><span data-stu-id="e6c59-277">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>
- <span data-ttu-id="e6c59-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) El subproceso MQTT aún no ha comenzado a ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="e6c59-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT Thread has not started running yet.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-279">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-279">Allowed From</span></span>

<span data-ttu-id="e6c59-280">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-281">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-281">Example</span></span>

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a><span data-ttu-id="e6c59-282">nxd_mqtt_client_publish</span><span class="sxs-lookup"><span data-stu-id="e6c59-282">nxd_mqtt_client_publish</span></span>

<span data-ttu-id="e6c59-283">Publica un mensaje a través del agente</span><span class="sxs-lookup"><span data-stu-id="e6c59-283">Publish a message through the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-284">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-284">Prototype</span></span>

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a><span data-ttu-id="e6c59-285">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-285">Description</span></span>

<span data-ttu-id="e6c59-286">Este servicio publica un mensaje a través del agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-286">This service publishes a message through the broker.</span></span> <span data-ttu-id="e6c59-287">Todavía no se admite la publicación de mensajes de QoS de nivel 2.</span><span class="sxs-lookup"><span data-stu-id="e6c59-287">Publishing QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-288">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-288">Input Parameters</span></span>

- <span data-ttu-id="e6c59-289">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-289">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-290">**topic_name** Tema en el que se va a publicar.</span><span class="sxs-lookup"><span data-stu-id="e6c59-290">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="e6c59-291">**topic_name_length** Longitud del tema, en bytes.</span><span class="sxs-lookup"><span data-stu-id="e6c59-291">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="e6c59-292">**message** Puntero al búfer de mensajes.</span><span class="sxs-lookup"><span data-stu-id="e6c59-292">**message** Pointer to the message buffer.</span></span>
- <span data-ttu-id="e6c59-293">**message_length** Tamaño del mensaje, en bytes</span><span class="sxs-lookup"><span data-stu-id="e6c59-293">**message_length** Size of the message, in bytes</span></span>
- <span data-ttu-id="e6c59-294">**retain** Determina si el agente debe conservar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="e6c59-294">**retain** Determines if the broker shall retain the message.</span></span>
- <span data-ttu-id="e6c59-295">**QoS** Valor de QoS deseado: 0 ó 1.</span><span class="sxs-lookup"><span data-stu-id="e6c59-295">**QoS** The desired QoS value: 0 or 1.</span></span>
- <span data-ttu-id="e6c59-296">**timeout** Valor de tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="e6c59-296">**timeout** Timeout value</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-297">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-297">Return Values</span></span>

- <span data-ttu-id="e6c59-298">**NXD_MQTT_SUCCESS** (0x00) Creación de cliente MQTT correcta.</span><span class="sxs-lookup"><span data-stu-id="e6c59-298">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT Client create</span></span>
- <span data-ttu-id="e6c59-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.</span><span class="sxs-lookup"><span data-stu-id="e6c59-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error.</span></span>
- <span data-ttu-id="e6c59-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0X10006) No se pudo obtener el paquete del grupo de paquetes.</span><span class="sxs-lookup"><span data-stu-id="e6c59-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Failed to obtain packet from the packet pool.</span></span>
- <span data-ttu-id="e6c59-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No se pudo comunicar con el agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Failed to communication with the broker.</span></span>
- <span data-ttu-id="e6c59-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) No se admiten los mensajes de QoS nivel 2.</span><span class="sxs-lookup"><span data-stu-id="e6c59-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="e6c59-303">NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-303">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="e6c59-304">NXD_MQTT_INVALID_PARAMETER (0x10009) Error de entrada del parámetro.</span><span class="sxs-lookup"><span data-stu-id="e6c59-304">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-305">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-305">Allowed From</span></span>

<span data-ttu-id="e6c59-306">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-307">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-307">Example</span></span>

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a><span data-ttu-id="e6c59-308">nxd_mqtt_client_subscribe</span><span class="sxs-lookup"><span data-stu-id="e6c59-308">nxd_mqtt_client_subscribe</span></span>

<span data-ttu-id="e6c59-309">Suscripción a un tema</span><span class="sxs-lookup"><span data-stu-id="e6c59-309">Subscribe to a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-310">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-310">Prototype</span></span>

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a><span data-ttu-id="e6c59-311">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-311">Description</span></span>

<span data-ttu-id="e6c59-312">Este servicio se suscribe a un tema específico.</span><span class="sxs-lookup"><span data-stu-id="e6c59-312">This service subscribes to a specific topic.</span></span> <span data-ttu-id="e6c59-313">Todavía no se admite la suscripción a mensajes de QoS de nivel 2.</span><span class="sxs-lookup"><span data-stu-id="e6c59-313">Subscribing to QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-314">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-314">Input Parameters</span></span>

- <span data-ttu-id="e6c59-315">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-315">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-316">**topic_name** Tema en el que se va a publicar.</span><span class="sxs-lookup"><span data-stu-id="e6c59-316">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="e6c59-317">**topic_name_length** Longitud del tema, en bytes.</span><span class="sxs-lookup"><span data-stu-id="e6c59-317">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="e6c59-318">**QoS Nivel de QoS deseado:** 0 ó 1.</span><span class="sxs-lookup"><span data-stu-id="e6c59-318">**QoS The desired QoS level:** 0 or 1.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-319">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-319">Return Values</span></span>

- <span data-ttu-id="e6c59-320">**NXD_MQTT_SUCCESS** (0x00) Se ha suscrito correctamente al tema.</span><span class="sxs-lookup"><span data-stu-id="e6c59-320">**NXD_MQTT_SUCCESS** (0x00) Successfully subscribed to the topic.</span></span>
- <span data-ttu-id="e6c59-321">**NXD_MQTT_NOT_CONNECTED** (0X10002) El cliente no está conectado al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="e6c59-322">**NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span>
- <span data-ttu-id="e6c59-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.</span><span class="sxs-lookup"><span data-stu-id="e6c59-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e6c59-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No pueden enviar mensajes al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="e6c59-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) No se admiten los mensajes de QoS nivel 2.</span><span class="sxs-lookup"><span data-stu-id="e6c59-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2messages are not supported.</span></span>
- <span data-ttu-id="e6c59-326">NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-326">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="e6c59-327">NXD_MQTT_INVALID_PARAMETER (0x10009) El valor de topic_name no está establecido, o topic_name_length es cero, o el valor de QoS no es válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero, or QoS is value is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-328">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-328">Allowed From</span></span>

<span data-ttu-id="e6c59-329">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-330">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-330">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a><span data-ttu-id="e6c59-331">nxd_mqtt_client_unsubscribe</span><span class="sxs-lookup"><span data-stu-id="e6c59-331">nxd_mqtt_client_unsubscribe</span></span>

<span data-ttu-id="e6c59-332">Cancela la suscripción a un tema</span><span class="sxs-lookup"><span data-stu-id="e6c59-332">Unsubscribe from a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-333">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-333">Prototype</span></span>

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a><span data-ttu-id="e6c59-334">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-334">Description</span></span>

<span data-ttu-id="e6c59-335">Este servicio cancela la suscripción de un tema.</span><span class="sxs-lookup"><span data-stu-id="e6c59-335">This service unsubscribes from a topic.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-336">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-336">Input Parameters</span></span>

- <span data-ttu-id="e6c59-337">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-337">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-338">**topic_name** Tema del que se cancelará la suscripción.</span><span class="sxs-lookup"><span data-stu-id="e6c59-338">**topic_name** Topic to unsubscribe from.</span></span>
- <span data-ttu-id="e6c59-339">**topic_name_length** Longitud del tema, en bytes.</span><span class="sxs-lookup"><span data-stu-id="e6c59-339">**topic_name_length** Length of the topic, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-340">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-340">Return Values</span></span>

- <span data-ttu-id="e6c59-341">**NXD_MQTT_SUCCESS** (0x00) Se ha cancelado correctamente la suscripción al tema.</span><span class="sxs-lookup"><span data-stu-id="e6c59-341">**NXD_MQTT_SUCCESS** (0x00) Successfully unsubscribed from the topic.</span></span>
- <span data-ttu-id="e6c59-342">**NXD_MQTT_NOT_CONNECTED** (0X10002) El cliente no está conectado al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="e6c59-343">**NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="e6c59-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.</span><span class="sxs-lookup"><span data-stu-id="e6c59-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e6c59-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) No pueden enviar mensajes al agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="e6c59-346">NX_PTR_ERROR (0x07) Puntero de bloque de control MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-346">NX_PTR_ERROR (0x07) Invalid MQTT control block pointer</span></span>
- <span data-ttu-id="e6c59-347">NXD_MQTT_INVALID_PARAMETER (0x10009) El valor de topic_name no está establecido, o topic_name_length es cero.</span><span class="sxs-lookup"><span data-stu-id="e6c59-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-348">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-348">Allowed From</span></span>

<span data-ttu-id="e6c59-349">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-350">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-350">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a><span data-ttu-id="e6c59-351">nxd_mqtt_client_receive_notify_set</span><span class="sxs-lookup"><span data-stu-id="e6c59-351">nxd_mqtt_client_receive_notify_set</span></span>

<span data-ttu-id="e6c59-352">Establece la función de devolución de llamada de la notificación de recepción de un mensaje MQTT</span><span class="sxs-lookup"><span data-stu-id="e6c59-352">Set MQTT message receive notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-353">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-353">Prototype</span></span>

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a><span data-ttu-id="e6c59-354">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-354">Description</span></span>

<span data-ttu-id="e6c59-355">Este servicio registra una función de devolución de llamada con el cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-355">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="e6c59-356">Al recibir un mensaje publicado por el agente, el cliente MQTT almacena el mensaje en la cola de recepción.</span><span class="sxs-lookup"><span data-stu-id="e6c59-356">Upon receiving a message published by the broker, MQTT client stores the message in the receive queue.</span></span> <span data-ttu-id="e6c59-357">Si está establecida la función de devolución de llamada, se invoca para notificar a la aplicación que un mensaje está listo para recuperarse.</span><span class="sxs-lookup"><span data-stu-id="e6c59-357">If the callback function is set, the callback function is invoked to notify the application that a message is ready to be retrieved.</span></span> <span data-ttu-id="e6c59-358">La función de notificación de recepción toma un puntero al bloque de control de cliente MQTT y un *message_count* que indica el número de mensajes disponibles en la cola de recepción.</span><span class="sxs-lookup"><span data-stu-id="e6c59-358">The receive notify function takes a pointer to the MQTT client control block, and a *message_count* indicating the number of messages available in the receive queue.</span></span> <span data-ttu-id="e6c59-359">Tenga en cuenta que el número puede cambiar entre la notificación de recepción y el momento en que la aplicación recupera estos mensajes, ya que es posible que los mensajes nuevos hayan llegado durante el intervalo.</span><span class="sxs-lookup"><span data-stu-id="e6c59-359">Note that the number may change between the receive notification and when the application retrieves these messages, as new messages may have arrived in the interval.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-360">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-360">Input Parameters</span></span>

- <span data-ttu-id="e6c59-361">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-361">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-362">**receive_notify** Función de devolución de llamada proporcionada por el usuario que se invocará cuando se reciba un mensaje.</span><span class="sxs-lookup"><span data-stu-id="e6c59-362">**receive_notify** User supplied callback function to be invoked on receiving a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-363">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-363">Return Values</span></span>

- <span data-ttu-id="e6c59-364">**NXD_MQTT_SUCCESS** (0x00) La función de notificación de recepción se configuró correctamente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-364">**NXD_MQTT_SUCCESS** (0x00) Successfully set the receive notify function.</span></span>
- <span data-ttu-id="e6c59-365">NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-365">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-366">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-366">Allowed From</span></span>

<span data-ttu-id="e6c59-367">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-368">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-368">Example</span></span>

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a><span data-ttu-id="e6c59-369">nxd_mqtt_client_message_get</span><span class="sxs-lookup"><span data-stu-id="e6c59-369">nxd_mqtt_client_message_get</span></span>

<span data-ttu-id="e6c59-370">Recupera de un mensaje del agente</span><span class="sxs-lookup"><span data-stu-id="e6c59-370">Retrieve a message from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-371">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-371">Prototype</span></span>

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a><span data-ttu-id="e6c59-372">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-372">Description</span></span>

<span data-ttu-id="e6c59-373">Este servicio recupera un mensaje publicado por el agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-373">This service retrieves a message published by the broker.</span></span> <span data-ttu-id="e6c59-374">Todos los mensajes entrantes se almacenan en la cola de recepción.</span><span class="sxs-lookup"><span data-stu-id="e6c59-374">All incoming messages are stored in the receive queue.</span></span> <span data-ttu-id="e6c59-375">La aplicación usa este servicio para recuperar estos mensajes.</span><span class="sxs-lookup"><span data-stu-id="e6c59-375">The application uses this service to retrieve these messages.</span></span> <span data-ttu-id="e6c59-376">Esta llamada no es de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="e6c59-376">This call is non-blocking.</span></span> <span data-ttu-id="e6c59-377">Si la cola de recepción está vacía, este servicio devuelve \***NXD_MQTT_NO_MESSAGE** _.</span><span class="sxs-lookup"><span data-stu-id="e6c59-377">If the receive queue is empty, this service returns \***NXD_MQTT_NO_MESSAGE** _.</span></span> <span data-ttu-id="e6c59-378">Una aplicación que quiera recibir notificaciones acerca del mensaje entrante puede llamar al servicio _ *_nxd_mqtt_client_receive_notify_set_*\* para registrar una función de devolución de llamada de recepción.</span><span class="sxs-lookup"><span data-stu-id="e6c59-378">An application wishing to be notified of incoming message can call the service _ *_nxd_mqtt_client_receive_notify_set_*\* to register a receive callback function.</span></span>

<span data-ttu-id="e6c59-379">El autor de la llamada debe proporcionar espacio de memoria para la cadena de tema y para el cuerpo del mensaje.</span><span class="sxs-lookup"><span data-stu-id="e6c59-379">The caller needs to provide memory space for the topic string and the message body.</span></span> <span data-ttu-id="e6c59-380">Los tamaños de estos dos búferes se pasan mediante los parámetros *topic_buffer_size* y *message_buffer_size*.</span><span class="sxs-lookup"><span data-stu-id="e6c59-380">The sizes of these two buffers are passed in using *topic_buffer_size* and *message_buffer_size*.</span></span> <span data-ttu-id="e6c59-381">El número real de bytes de la cadena de tema y el cuerpo del mensaje se devuelven en los parámetros *actual_topic_length* y *actual_message_length*.</span><span class="sxs-lookup"><span data-stu-id="e6c59-381">The actual number of bytes in the topic string and the message body are returned in *actual_topic_length* and *actual_message_length*.</span></span> <span data-ttu-id="e6c59-382">Si la longitud del tema o del mensaje es mayor que el espacio en búfer proporcionado, este servicio devuelve el código de error *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span><span class="sxs-lookup"><span data-stu-id="e6c59-382">If topic length or massage length is greater than the buffer space provided, this service returns error code *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span></span>

<span data-ttu-id="e6c59-383">La aplicación asignará un búfer de mayor tamaño y volverá a intentarlo.</span><span class="sxs-lookup"><span data-stu-id="e6c59-383">The application shall allocate a bigger buffer and try again.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-384">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-384">Input Parameters</span></span>

- <span data-ttu-id="e6c59-385">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-385">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-386">**topic_buffer** Puntero a la ubicación de memoria en la que se copia la cadena de tema.</span><span class="sxs-lookup"><span data-stu-id="e6c59-386">**topic_buffer** Pointer to the memory location where the topic string is copied into.</span></span>
- <span data-ttu-id="e6c59-387">**topic_buffer_size** Tamaño del búfer de tema.</span><span class="sxs-lookup"><span data-stu-id="e6c59-387">**topic_buffer_size** Size of the topic buffer.</span></span>
- <span data-ttu-id="e6c59-388">**actual_topic_length** Puntero a la ubicación de memoria en la que se devuelve la longitud real del tema.</span><span class="sxs-lookup"><span data-stu-id="e6c59-388">**actual_topic_length** Pointer to the memory location where the actual topic length is returned.</span></span>
- <span data-ttu-id="e6c59-389">**message_buffer** Puntero a la ubicación de memoria en la que se copia la cadena de mensaje.</span><span class="sxs-lookup"><span data-stu-id="e6c59-389">**message_buffer** Pointer to the memory location where the message string is copied into.</span></span>
- <span data-ttu-id="e6c59-390">**message_buffer_size** Tamaño del búfer de mensajes.</span><span class="sxs-lookup"><span data-stu-id="e6c59-390">**message_buffer_size** Size of the message buffer.</span></span>
- <span data-ttu-id="e6c59-391">**actual_message_length** Puntero a la ubicación de memoria en la que se devuelve la longitud del mensaje.</span><span class="sxs-lookup"><span data-stu-id="e6c59-391">**actual_message_length** Pointer to the memory location where the message length is returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-392">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-392">Return Values</span></span>

- <span data-ttu-id="e6c59-393">**NXD_MQTT_SUCCESS** (0x00) Se recuperó correctamente el mensaje.</span><span class="sxs-lookup"><span data-stu-id="e6c59-393">**NXD_MQTT_SUCCESS** (0x00) Successfully retrieved message.</span></span>
- <span data-ttu-id="e6c59-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Error de lógica interna.</span><span class="sxs-lookup"><span data-stu-id="e6c59-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e6c59-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) La cola de recepción está vacía.</span><span class="sxs-lookup"><span data-stu-id="e6c59-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) The receive queue is empty.</span></span>
- <span data-ttu-id="e6c59-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) El búfer de tema o mensaje es demasiado pequeño para el tema o mensaje.</span><span class="sxs-lookup"><span data-stu-id="e6c59-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Topic buffer or message buffer is too small for the topic or the message.</span></span>
- <span data-ttu-id="e6c59-397">NX_PTR_ERROR (0x07) Bloque de control, ip_ptr o puntero de grupo de paquetes MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-397">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="e6c59-398">NXD_MQTT_INVALID_PARAMETER (0x10009) El puntero de message_buffer o topic_buffer es NULL.</span><span class="sxs-lookup"><span data-stu-id="e6c59-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer or topic_buffer pointer is NULL</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-399">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-399">Allowed From</span></span>

<span data-ttu-id="e6c59-400">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-401">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-401">Example</span></span>

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a><span data-ttu-id="e6c59-402">nxd_mqtt_client_disconnect_notify_set</span><span class="sxs-lookup"><span data-stu-id="e6c59-402">nxd_mqtt_client_disconnect_notify_set</span></span>

<span data-ttu-id="e6c59-403">Establece la función de devolución de llamada de notificación de desconexión del mensaje de MQTT</span><span class="sxs-lookup"><span data-stu-id="e6c59-403">Set MQTT message disconnect notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-404">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-404">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a><span data-ttu-id="e6c59-405">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-405">Description</span></span>

<span data-ttu-id="e6c59-406">Este servicio registra una función de devolución de llamada con el cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-406">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="e6c59-407">Cuando MQTT detecta que se pierde la conexión con el agente, llama a esta función de notificación para avisar a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e6c59-407">When MQTT detects the connection to the broker is lost, it calls this notify function to alert the application.</span></span> <span data-ttu-id="e6c59-408">Por lo tanto, la aplicación puede usar esta función de devolución de llamada para detectar una conexión perdida y restablecer la conexión con el agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-408">Therefore, the application can use this callback function to detect a lost connection, and to be able to re-establish connection to the broker.</span></span>

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a><span data-ttu-id="e6c59-409">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-409">Input Parameters</span></span>

- <span data-ttu-id="e6c59-410">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-410">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e6c59-411">**disconnect_notify** Función de devolución de llamada proporcionada por el usuario que se va a invocar cuando MQTT detecte que se ha perdido la conexión con el agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-411">**disconnect_notify** User supplied callback function to be invoked when MQTT detects the connection to the broker is lost.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-412">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-412">Return Values</span></span>

- <span data-ttu-id="e6c59-413">**NXD_MQTT_SUCCESS** (0x00) La función de notificación de desconexión se configuró correctamente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-413">**NXD_MQTT_SUCCESS** (0x00) Successfully set the disconnect notify function.</span></span>
- <span data-ttu-id="e6c59-414">NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-414">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-415">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-415">Allowed From</span></span>

<span data-ttu-id="e6c59-416">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-417">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-417">Example</span></span>

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a><span data-ttu-id="e6c59-418">nxd_mqtt_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="e6c59-418">nxd_mqtt_client_disconnect</span></span>

<span data-ttu-id="e6c59-419">Desconecta el cliente MQTT del agente</span><span class="sxs-lookup"><span data-stu-id="e6c59-419">Disconnect MQTT client from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-420">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-420">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="e6c59-421">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-421">Description</span></span>

<span data-ttu-id="e6c59-422">Este servicio desconecta el cliente del agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-422">This service disconnects the client from the broker.</span></span> <span data-ttu-id="e6c59-423">Tenga en cuenta que se liberan los mensajes en la cola de recepción.</span><span class="sxs-lookup"><span data-stu-id="e6c59-423">Note that messages on the receive queue are released.</span></span> <span data-ttu-id="e6c59-424">No se liberan los mensajes con QoS 1 en la cola de transmisión.</span><span class="sxs-lookup"><span data-stu-id="e6c59-424">Messages with QoS 1 in the transmit queue are not released.</span></span> <span data-ttu-id="e6c59-425">Una vez que el cliente se vuelve a conectar al servidor, se pueden procesar los mensajes con QoS 1, a menos que el cliente vuelva a conectarse al servidor con la marca *clean_session* establecida en ***NX_TRUE***.</span><span class="sxs-lookup"><span data-stu-id="e6c59-425">After the client reconnects to the server, QoS 1 messages can be processed, unless the client reconnects to the server with *clean_session* flag set to ***NX_TRUE***.</span></span>

<span data-ttu-id="e6c59-426">Si la conexión se realizó con protección de seguridad de TLS, este servicio cerrará la sesión de TLS antes de desconectar la conexión TCP.</span><span class="sxs-lookup"><span data-stu-id="e6c59-426">If the connection was made with TLS security protection, this service will close the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="e6c59-427">La llamada de desconexión del socket TCP real tiene una opción de espera que define el parámetro NXD_MQTT_SOCKET_TIMEOUT (tics del temporizador).</span><span class="sxs-lookup"><span data-stu-id="e6c59-427">The actual TCP socket disconnect call has a wait option defined by NXD_MQTT_SOCKET_TIMEOUT (timer ticks).</span></span> <span data-ttu-id="e6c59-428">El valor predeterminado es NX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="e6c59-428">The default value is NX_WAIT_FOREVER.</span></span> <span data-ttu-id="e6c59-429">Para evitar la suspensión indefinida en caso de que se pierda la conexión de red o de que el servidor no responda, establezca esta opción en un valor finito.</span><span class="sxs-lookup"><span data-stu-id="e6c59-429">To avoid indefinite suspension in the event that the network connection is lost or the server is not responding, set this option to a finite value.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-430">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-430">Input Parameters</span></span>

- <span data-ttu-id="e6c59-431">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-431">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-432">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-432">Return Values</span></span>

- <span data-ttu-id="e6c59-433">**NXD_MQTT_SUCCESS** (0x00) Se desconectó correctamente del agente.</span><span class="sxs-lookup"><span data-stu-id="e6c59-433">**NXD_MQTT_SUCCESS** (0x00) Successfully disconnected from broker</span></span>
- <span data-ttu-id="e6c59-434">**NXD_MQTT_MUTEX_FAILURE** (0X10003) No se pudo obtener la exclusión mutua de MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="e6c59-435">NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-435">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-436">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-436">Allowed From</span></span>

<span data-ttu-id="e6c59-437">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-438">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-438">Example</span></span>

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a><span data-ttu-id="e6c59-439">nxd_mqtt_client_delete</span><span class="sxs-lookup"><span data-stu-id="e6c59-439">nxd_mqtt_client_delete</span></span>

<span data-ttu-id="e6c59-440">Elimine la instancia de cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="e6c59-440">Delete the MQTT client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e6c59-441">Prototipo</span><span class="sxs-lookup"><span data-stu-id="e6c59-441">Prototype</span></span>

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="e6c59-442">Descripción</span><span class="sxs-lookup"><span data-stu-id="e6c59-442">Description</span></span>

<span data-ttu-id="e6c59-443">Este servicio elimina la instancia de cliente MQTT y libera los recursos internos.</span><span class="sxs-lookup"><span data-stu-id="e6c59-443">This service deletes the MQTT client instance and releases internal resources.</span></span> <span data-ttu-id="e6c59-444">Este servicio desconecta automáticamente el cliente del agente si aún está conectado.</span><span class="sxs-lookup"><span data-stu-id="e6c59-444">This service automatically disconnects the client from the broker if it is still connected.</span></span> <span data-ttu-id="e6c59-445">Se liberan los mensajes que todavía no se han transmitido o no se han confirmado.</span><span class="sxs-lookup"><span data-stu-id="e6c59-445">Messages not yet transmitted or not been acknowledged are released.</span></span> <span data-ttu-id="e6c59-446">También se liberan los mensajes que se han recibido pero que la aplicación no ha recuperado.</span><span class="sxs-lookup"><span data-stu-id="e6c59-446">Messages received but not retrieved by the application are also released.</span></span>

<span data-ttu-id="e6c59-447">Si la conexión se realizó con protección de seguridad de TLS, este servicio cierra la sesión de TLS antes de desconectar la conexión TCP.</span><span class="sxs-lookup"><span data-stu-id="e6c59-447">If the connection was made with TLS security protection, this service closes the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="e6c59-448">Una vez eliminado el cliente, una aplicación que quiera usar el servicio MQTT deberá crear una nueva instancia.</span><span class="sxs-lookup"><span data-stu-id="e6c59-448">After the client is deleted, an application wishing to use MQTT service needs to create a new instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e6c59-449">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="e6c59-449">Input Parameters</span></span>

- <span data-ttu-id="e6c59-450">**client_ptr** Puntero al bloque de control del cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-450">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e6c59-451">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="e6c59-451">Return Values</span></span>

- <span data-ttu-id="e6c59-452">**NXD_MQTT_SUCCESS** (0x00) Se eliminó correctamente el cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="e6c59-452">**NXD_MQTT_SUCCESS** (0x00) Successfully deleted MQTT client.</span></span>
- <span data-ttu-id="e6c59-453">NX_PTR_ERROR (0x07) Bloque de control MQTT no válido.</span><span class="sxs-lookup"><span data-stu-id="e6c59-453">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e6c59-454">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="e6c59-454">Allowed From</span></span>

<span data-ttu-id="e6c59-455">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="e6c59-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e6c59-456">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="e6c59-456">Example</span></span>

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
