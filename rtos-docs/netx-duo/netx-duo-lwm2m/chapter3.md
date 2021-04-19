---
title: 'Capítulo 3: Descripción funcional del cliente LWM2M'
description: Este capítulo contiene una descripción funcional del cliente LWM2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814678"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a><span data-ttu-id="b1d4c-103">Capítulo 3: Descripción funcional del cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="b1d4c-103">Chapter 3  Functional Description of LWM2M Client</span></span>

> <span data-ttu-id="b1d4c-104">Este capítulo contiene una descripción funcional del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-104">This chapter contains a functional description of LWM2M Client.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="b1d4c-105">Inicialización del cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="b1d4c-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="b1d4c-106">El cliente LWM2M se inicializa mediante una llamada al servicio ***nx_lwm2m_client_create***.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="b1d4c-107">El cliente LWM2M se ejecuta en su propio subproceso y puede notificar algunos eventos a la aplicación mediante devoluciones de llamada o bien llamando a los métodos de los objetos personalizados implementados por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="b1d4c-108">Además, las sesiones del cliente LWM2M deben crearse mediante una llamada a ***nx_lwm2m_client_session_create*** para habilitar la comunicación con uno o más servidores.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="b1d4c-109">Una sesión puede comunicarse con dos tipos de servidores diferentes: un servidor de arranque o un servidor LWM2M (administración de dispositivos).</span><span class="sxs-lookup"><span data-stu-id="b1d4c-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="b1d4c-110">Sesión del servidor de arranque</span><span class="sxs-lookup"><span data-stu-id="b1d4c-110">Bootstrap Server Session</span></span>

<span data-ttu-id="b1d4c-111">Una sesión de comunicación con un servidor de arranque se usa para aprovisionar información esencial en el cliente LWM2M para permitir que dicho realice la operación de registro con uno o varios servidores LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation “Register” with one or more LWM2M Servers.</span></span> <span data-ttu-id="b1d4c-112">Este tipo de servidor se usa durante los modos de arranque iniciados por el cliente y por el servidor.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="b1d4c-113">La aplicación puede iniciar una sesión de arranque mediante una llamada a ***nx_lwm2m_client_session_bootstrap** _ o _*_nx_lwm2m_client_session_bootstrap_dtls_\*_; debe proporcionar la dirección IP y el número de puerto del servidor, y un identificador de instancia de objeto de seguridad opcional.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="b1d4c-114">La función _*_nx_lwm2m_client_session_bootstrap_*_ utiliza la comunicación no segura, mientras que _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establece una conexión DTLS segura con el servidor.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="b1d4c-115">Si la operación de arranque se realiza correctamente, el servidor de arranque debe haber creado instancias de objeto de seguridad para los servidores de arranque y LWM2M, e instancias de objeto de servidor para los servidores LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="b1d4c-116">La aplicación puede llamar a ***nx_lwm2m_client_session_register_info_get*** para obtener información de los servidores LWM2M y usar esta información para establecer una sesión con dichos servidores.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-116">The application can call ***nx_lwm2m_client_session_register_info_get*** to get LWM2M Server(s) information and use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="b1d4c-117">La aplicación debe guardar los datos de arranque en la memoria no volátil para configurar el cliente LWM2M en el siguiente reinicio del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-117">The Bootstrap data should be saved to non-volatile memory by the application to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="b1d4c-118">Sesión del servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="b1d4c-118">LWM2M Server Session</span></span>

<span data-ttu-id="b1d4c-119">Una sesión de comunicación con un servidor LWM2M se usa para el registro, la administración de dispositivos y la habilitación del servicio.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="b1d4c-120">La aplicación puede registrar el cliente LWM2M en un servidor mediante una llamada a ***nx_lwm2m_client_session_register** _ o _*_nx_lwm2m_client_session_register_dtls_\*_; debe proporcionar la dirección IP y el número de puerto del servidor, y el identificador de servidor corto que corresponde a una instancia de objeto de servidor existente.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="b1d4c-121">La función _*_nx_lwm2m_client_session_register_*_ utiliza la comunicación no segura, mientras que _ *_nx_lwm2m_client_session_register_dtls_*\* establece una conexión DTLS segura con el servidor.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas  _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="b1d4c-122">La aplicación puede anular el registro del cliente LWM2M mediante una llamada a ***nx_lwm2m_client_session_deregister** _ y pedir al cliente que envíe un mensaje de actualización mediante una llamada a _*_nx_lwm2m_client_session_update_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an ‘Update’ message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="b1d4c-123">Devolución de llamada de estado de sesión</span><span class="sxs-lookup"><span data-stu-id="b1d4c-123">Session State Callback</span></span>

<span data-ttu-id="b1d4c-124">La aplicación registra una devolución de llamada durante la creación de una sesión a la que se llama cuando se actualiza el estado de la sesión; la función de devolución de llamada **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** tiene el siguiente prototipo.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** has the following prototype.</span></span>

<span data-ttu-id="b1d4c-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span><span class="sxs-lookup"><span data-stu-id="b1d4c-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span></span>

<span data-ttu-id="b1d4c-126">Los estados siguientes están definidos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-126">The following states are defined.</span></span>

| <span data-ttu-id="b1d4c-127">Estado de&nbsp;la sesión</span><span class="sxs-lookup"><span data-stu-id="b1d4c-127">Session&nbsp;State</span></span> | <span data-ttu-id="b1d4c-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-128">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span></span> | <span data-ttu-id="b1d4c-130">Estado inicial después de la creación de la sesión.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-130">The initial state after session creation.</span></span> |
| <span data-ttu-id="b1d4c-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span></span> | <span data-ttu-id="b1d4c-132">El cliente está esperando la expiración del temporizador "Hold Off" o el arranque iniciado por el servidor.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-132">The client is waiting for the expiration of the ‘Hold Off’ timer or Server Initiated Bootstrap.</span></span> |
| <span data-ttu-id="b1d4c-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span></span> | <span data-ttu-id="b1d4c-134">El cliente ha enviado un mensaje de solicitud al servidor de arranque (arranque iniciado por el cliente).</span><span class="sxs-lookup"><span data-stu-id="b1d4c-134">The client has sent a ‘Request’ message to the Bootstrap Server (Client Initiated Bootstrap).</span></span> |
| <span data-ttu-id="b1d4c-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span></span> | <span data-ttu-id="b1d4c-136">El cliente recibe datos del servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-136">The client is receiving data from the Bootstrap Server.</span></span> |
| <span data-ttu-id="b1d4c-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span></span> | <span data-ttu-id="b1d4c-138">El servidor de arranque ha enviado un mensaje de finalización.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-138">The Bootstrap Server has sent a ‘Finished’ message.</span></span> |
| <span data-ttu-id="b1d4c-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span></span> | <span data-ttu-id="b1d4c-140">Error en la sesión de arranque.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-140">The bootstrap session has failed.</span></span> |
| <span data-ttu-id="b1d4c-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span></span> | <span data-ttu-id="b1d4c-142">El cliente ha enviado un mensaje de registro al servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-142">The client has sent a ‘Register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="b1d4c-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span></span> | <span data-ttu-id="b1d4c-144">El cliente está registrado en el servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-144">The client is registered to the LWM2M Server.</span></span> |
| <span data-ttu-id="b1d4c-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span></span> | <span data-ttu-id="b1d4c-146">El cliente ha enviado un mensaje de actualización al servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-146">The client has sent an ‘Update’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="b1d4c-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span></span> | <span data-ttu-id="b1d4c-148">El cliente ha enviado un mensaje de anulación de registro al servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-148">The client has sent an ‘De-register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="b1d4c-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span></span> | <span data-ttu-id="b1d4c-150">Se anuló el registro del cliente en el servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-150">The client is de-registered from the LWM2M Server.</span></span> |
| <span data-ttu-id="b1d4c-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span></span> | <span data-ttu-id="b1d4c-152">El servidor LWM2M está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-152">The LWM2M Server is disabled.</span></span> <span data-ttu-id="b1d4c-153">Se enviará un mensaje de registro después de la expiración del temporizador de deshabilitación.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-153">A ‘Register’ will be sent after the expiration of the disable timer.</span></span> |
| <span data-ttu-id="b1d4c-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span></span> | <span data-ttu-id="b1d4c-155">No se pudo realizar la operación de registro o actualización en el servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-155">The registration or update operation to the LWM2M Server has failed.</span></span> |
| <span data-ttu-id="b1d4c-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span></span> | <span data-ttu-id="b1d4c-157">Se eliminó la instancia de objeto de servidor correspondiente al servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-157">The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> |

<span data-ttu-id="b1d4c-158">En caso de error, la aplicación puede recuperar la causa del error mediante una llamada a ***nx_lwm2m_client_session_error_get***.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-158">In case of error the application can retrieve the cause of the error by calling ***nx_lwm2m_client_session_error_get***.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="b1d4c-159">Administración de dispositivos locales</span><span class="sxs-lookup"><span data-stu-id="b1d4c-159">Local Device Management</span></span>

<span data-ttu-id="b1d4c-160">La aplicación puede acceder a los objetos del cliente LWM2M mediante las funciones de administración de dispositivos locales.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-160">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="b1d4c-161">Se proporciona las siguientes funciones.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-161">The following functions are provided.</span></span>

| <span data-ttu-id="b1d4c-162">Nombre de&nbsp;la función</span><span class="sxs-lookup"><span data-stu-id="b1d4c-162">Function&nbsp;Name</span></span> | <span data-ttu-id="b1d4c-163">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-163">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-164">***nx_lwm2m_client_object_read***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-164">***nx_lwm2m_client_object_read***</span></span> | <span data-ttu-id="b1d4c-165">Permite leer recursos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-165">Read resources from an Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-166">***nx_lwm2m_client_object_discover***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-166">***nx_lwm2m_client_object_discover***</span></span> | <span data-ttu-id="b1d4c-167">Permite obtener la lista de los recursos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-167">Get the list of the resources of an Object Instance.</span></span>
| <span data-ttu-id="b1d4c-168">***nx_lwm2m_client_object_write***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-168">***nx_lwm2m_client_object_write***</span></span> | <span data-ttu-id="b1d4c-169">Permite escribir recursos en una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-169">Write resources to an Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-170">***nx_lwm2m_client_object_execute***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-170">***nx_lwm2m_client_object_execute***</span></span> | <span data-ttu-id="b1d4c-171">Permite realizar una operación de ejecución en un recurso de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-171">Perform the Execute operation on a resource of an Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-172">***nx_lwm2m_client_object_create***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-172">***nx_lwm2m_client_object_create***</span></span> | <span data-ttu-id="b1d4c-173">Permite crear una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-173">Create a new Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-174">***nx_lwm2m_client_object_delete***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-174">***nx_lwm2m_client_object_delete***</span></span> | <span data-ttu-id="b1d4c-175">Permite eliminar una instancia de objeto existente.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-175">Delete an existing Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-176">***nx_lwm2m_client_object_next_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-176">***nx_lwm2m_client_object_next_get***</span></span> | <span data-ttu-id="b1d4c-177">Permite obtener el id. de objeto siguiente mediante el cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-177">Get the next Object ID by the LWM2M Client.</span></span> |
| <span data-ttu-id="b1d4c-178">***nx_lwm2m_client_object_instance_next_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-178">***nx_lwm2m_client_object_instance_next_get***</span></span> | <span data-ttu-id="b1d4c-179">Permite obtener la siguiente instancia de un objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-179">Get the next Instance of an Object.</span></span> |

## <a name="resource-information"></a><span data-ttu-id="b1d4c-180">Información de recursos</span><span class="sxs-lookup"><span data-stu-id="b1d4c-180">Resource Information</span></span>

<span data-ttu-id="b1d4c-181">Al leer y escribir en objetos, un recurso se representa mediante la estructura de NX_LWM2M_CLIENT_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-181">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_CLIENT_RESOURCE structure.</span></span> <span data-ttu-id="b1d4c-182">Esta estructura contiene el identificador del recurso o la instancia y su valor.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-182">This structure contains the ID of the Resource/Instance and its value.</span></span>

<span data-ttu-id="b1d4c-183">Se proporcionan las siguientes funciones para establecer la información y el valor de los recursos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-183">The following functions are provided for setting resource info and value.</span></span>

| <span data-ttu-id="b1d4c-184">Nombre de&nbsp;la función</span><span class="sxs-lookup"><span data-stu-id="b1d4c-184">Function&nbsp;Name</span></span> | <span data-ttu-id="b1d4c-185">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-185">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-186">***nx_lwm2m_client_resource_info_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-186">***nx_lwm2m_client_resource_info_set***</span></span> | <span data-ttu-id="b1d4c-187">Permite establecer la información de los recursos. Id. de recurso y operación: READ, WRITE, EXECUTABLE.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-187">Set resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="b1d4c-188">***nx_lwm2m_client_resource_string_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-188">***nx_lwm2m_client_resource_string_set***</span></span> | <span data-ttu-id="b1d4c-189">Permite establecer el valor del recurso como una cadena.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-189">Set the resource value as string.</span></span> |
| <span data-ttu-id="b1d4c-190">***nx_lwm2m_client_resource_integer32_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-190">***nx_lwm2m_client_resource_integer32_set***</span></span> | <span data-ttu-id="b1d4c-191">Permite establecer el valor del recurso como un entero de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-191">Set the resource value as 32-Bit integer.</span></span> |
| <span data-ttu-id="b1d4c-192">***nx_lwm2m_client_resource_integer64_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-192">***nx_lwm2m_client_resource_integer64_set***</span></span> | <span data-ttu-id="b1d4c-193">Permite establecer el valor del recurso como un entero de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-193">Set the resource value as 64-Bit integer.</span></span> |
| <span data-ttu-id="b1d4c-194">***nx_lwm2m_client_resource_float32_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-194">***nx_lwm2m_client_resource_float32_set***</span></span> | <span data-ttu-id="b1d4c-195">Permite establecer el recurso en un valor flotante de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-195">Set the resource value as 32-Bit float.</span></span> |
| <span data-ttu-id="b1d4c-196">***nx_lwm2m_client_resource_float64_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-196">***nx_lwm2m_client_resource_float64_set***</span></span> | <span data-ttu-id="b1d4c-197">Permite establecer el recurso en un valor flotante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-197">Set the resource value as 64-Bit float.</span></span> |
| <span data-ttu-id="b1d4c-198">***nx_lwm2m_client_resource_boolean_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-198">***nx_lwm2m_client_resource_boolean_set***</span></span> | <span data-ttu-id="b1d4c-199">Permite establecer el recurso en un valor booleano.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-199">Set the resource value as boolean.</span></span> |
| <span data-ttu-id="b1d4c-200">***nx_lwm2m_client_resource_objlnk_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-200">***nx_lwm2m_client_resource_objlnk_set***</span></span> | <span data-ttu-id="b1d4c-201">Permite establecer el valor del recurso como un vínculo de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-201">Set the resource value as object link.</span></span> |
| <span data-ttu-id="b1d4c-202">***nx_lwm2m_client_resource_opaque_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-202">***nx_lwm2m_client_resource_opaque_set***</span></span> | <span data-ttu-id="b1d4c-203">Permite establecer el recurso en un valor opaco.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-203">Set the resource value as opaque.</span></span> |
| <span data-ttu-id="b1d4c-204">***nx_lwm2m_client_resource_instance_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-204">***nx_lwm2m_client_resource_instance_set***</span></span> | <span data-ttu-id="b1d4c-205">Permite establecer el valor del recurso como una instancia para varios recursos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-205">Set the resource value as instance for multiple resource.</span></span> |
| <span data-ttu-id="b1d4c-206">***nx_lwm2m_client_resource_dim_set***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-206">***nx_lwm2m_client_resource_dim_set***</span></span> | <span data-ttu-id="b1d4c-207">Permite establecer la dimensión del recurso para varios recursos con fines de detección.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-207">Set the resource dimension for multiple resource for discover.</span></span> |

<span data-ttu-id="b1d4c-208">Se proporcionan las siguientes funciones para obtener la información y el valor de los recursos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-208">The following functions are provided for getting resource info and value.</span></span>

| <span data-ttu-id="b1d4c-209">Nombre de&nbsp;la función</span><span class="sxs-lookup"><span data-stu-id="b1d4c-209">Function&nbsp;Name</span></span> | <span data-ttu-id="b1d4c-210">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-210">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-211">***nx_lwm2m_client_resource_info_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-211">***nx_lwm2m_client_resource_info_get***</span></span> | <span data-ttu-id="b1d4c-212">Permite obtener la información de los recursos. Id. de recurso y operación: READ, WRITE, EXECUTABLE.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-212">Get resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="b1d4c-213">***nx_lwm2m_client_resource_string_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-213">***nx_lwm2m_client_resource_string_get***</span></span> | <span data-ttu-id="b1d4c-214">Permite obtener el valor de un recurso string.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-214">Get the value of a string resource.</span></span> |
| <span data-ttu-id="b1d4c-215">***nx_lwm2m_client_resource_integer32_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-215">***nx_lwm2m_client_resource_integer32_get***</span></span> | <span data-ttu-id="b1d4c-216">Permite obtener el valor de un recurso integer de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-216">Get the value of a 32-Bit integer resource.</span></span> |
| <span data-ttu-id="b1d4c-217">***nx_lwm2m_client_resource_integer64_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-217">***nx_lwm2m_client_resource_integer64_get***</span></span> | <span data-ttu-id="b1d4c-218">Permite obtener el valor de un recurso integer de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-218">Get the value of a b4-Bit integer resource.</span></span> |
| <span data-ttu-id="b1d4c-219">***nx_lwm2m_client_resource_float32_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-219">***nx_lwm2m_client_resource_float32_get***</span></span> | <span data-ttu-id="b1d4c-220">Permite obtener el valor de un recurso float de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-220">Get the value of a 32-Bit float resource.</span></span> |
| <span data-ttu-id="b1d4c-221">***nx_lwm2m_client_resource_float64_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-221">***nx_lwm2m_client_resource_float64_get***</span></span> | <span data-ttu-id="b1d4c-222">Permite obtener el valor de un recurso float de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-222">Get the value of a 64-Bit float resource.</span></span> |
| <span data-ttu-id="b1d4c-223">***nx_lwm2m_client_resource_boolean_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-223">***nx_lwm2m_client_resource_boolean_get***</span></span> | <span data-ttu-id="b1d4c-224">Obtiene el valor de un recurso boolean.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-224">Get the value of a Boolean resource.</span></span> |
| <span data-ttu-id="b1d4c-225">***nx_lwm2m_client_resource_objlnk_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-225">***nx_lwm2m_client_resource_objlnk_get***</span></span> | <span data-ttu-id="b1d4c-226">Permite obtener el valor de un recurso de vínculo de objeto</span><span class="sxs-lookup"><span data-stu-id="b1d4c-226">Get the value of an object link resource.</span></span> |
| <span data-ttu-id="b1d4c-227">***nx_lwm2m_client_resource_opaque_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-227">***nx_lwm2m_client_resource_opaque_get***</span></span> | <span data-ttu-id="b1d4c-228">Permite obtener el valor de un recurso opaque.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-228">Get the value of an opaque resource.</span></span> |
| <span data-ttu-id="b1d4c-229">***nx_lwm2m_client_resource_instance_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-229">***nx_lwm2m_client_resource_instance_get***</span></span> | <span data-ttu-id="b1d4c-230">Permite obtener la instancia de recurso para varios recursos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-230">Get the resource instance for multiple resource.</span></span> |
| <span data-ttu-id="b1d4c-231">***nx_lwm2m_client_resource_dim_get***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-231">***nx_lwm2m_client_resource_dim_get***</span></span> | <span data-ttu-id="b1d4c-232">Permite obtener la dimensión de recurso para varios recursos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-232">Get the resource dimension for multiple resource.</span></span> |

## <a name="object-implementation"></a><span data-ttu-id="b1d4c-233">Implementación de objetos</span><span class="sxs-lookup"><span data-stu-id="b1d4c-233">Object Implementation</span></span>

<span data-ttu-id="b1d4c-234">El cliente LWM2M implementa los siguientes objetos OMA LWM2M obligatorios: Security (0), Server (1), Access Control (2) y Device (3).</span><span class="sxs-lookup"><span data-stu-id="b1d4c-234">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="b1d4c-235">La aplicación debe implementar otros objetos específicos del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-235">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="b1d4c-236">Se usan dos estructuras de datos para definir un objeto: la estructura NX_LWM2M_CLIENT_OBJECT define la implementación del objeto (incluidos el id. de objeto y los métodos de objeto) y la estructura NX_LWM2M_CLIENT_OBJECT_INSTANCE contiene los datos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-236">Two data structures are used to define an Object: the NX_LWM2M_CLIENT_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_CLIENT_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="b1d4c-237">Se proporciona las siguientes funciones.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-237">The following functions are provided.</span></span>

| <span data-ttu-id="b1d4c-238">Nombre de&nbsp;la función</span><span class="sxs-lookup"><span data-stu-id="b1d4c-238">Function&nbsp;Name</span></span> | <span data-ttu-id="b1d4c-239">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-239">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-240">***nx_lwm2m_client_object_add***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-240">***nx_lwm2m_client_object_add***</span></span> | <span data-ttu-id="b1d4c-241">Permite agregar la implementación de objeto al cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-241">Add object implementation to the LwM2M Client.</span></span> |
| <span data-ttu-id="b1d4c-242">***nx_lwm2m_client_object_remove***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-242">***nx_lwm2m_client_object_remove***</span></span> | <span data-ttu-id="b1d4c-243">Permite quitar la implementación de objeto del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-243">Remove object implementation from the LwM2M Client.</span></span> |
| <span data-ttu-id="b1d4c-244">***nx_lwm2m_client_object_instance_add***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-244">***nx_lwm2m_client_object_instance_add***</span></span> | <span data-ttu-id="b1d4c-245">Permite agregar una instancia de objeto al objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-245">Add object instance to the Object.</span></span> |
| <span data-ttu-id="b1d4c-246">***nx_lwm2m_client_object_instance_remove***</span><span class="sxs-lookup"><span data-stu-id="b1d4c-246">***nx_lwm2m_client_object_instance_remove***</span></span> | <span data-ttu-id="b1d4c-247">Permite quitar la instancia de objeto del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-247">Remove object instance from the Object.</span></span> |

<span data-ttu-id="b1d4c-248">La función de devolución de llamada del método de objeto tiene la firma que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-248">The object method callback function has signature shown below.</span></span>

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a><span data-ttu-id="b1d4c-249">Método "Read"</span><span class="sxs-lookup"><span data-stu-id="b1d4c-249">The ‘Read’ Method</span></span>

<span data-ttu-id="b1d4c-250">El método "Read" se usa para leer los valores de recursos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-250">The ‘Read’ method is used to read Resource values from an Object Instance.</span></span> <span data-ttu-id="b1d4c-251">Los parámetros se definen como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-251">The parameters are defined as follows.</span></span>

| <span data-ttu-id="b1d4c-252">Parámetro</span><span class="sxs-lookup"><span data-stu-id="b1d4c-252">Parameter</span></span> | <span data-ttu-id="b1d4c-253">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-253">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-254">**operation**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-254">**operation**</span></span> | <span data-ttu-id="b1d4c-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span></span> |
| <span data-ttu-id="b1d4c-256">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-256">**object_ptr**</span></span> | <span data-ttu-id="b1d4c-257">Puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-257">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="b1d4c-258">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-258">**instance_ptr**</span></span> | <span data-ttu-id="b1d4c-259">Puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-259">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-260">**resource**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-260">**resource**</span></span> | <span data-ttu-id="b1d4c-261">Puntero a una matriz de **NX_LWM2M_CLIENT_RESOURCE** que contiene los identificadores de los recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-261">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="b1d4c-262">En la devolución, la matriz se rellena con los tipos y valores correspondientes.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-262">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="b1d4c-263">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-263">**resource_count**</span></span> | <span data-ttu-id="b1d4c-264">Puntero al número de recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-264">Pointer to the number of resources to read.</span></span> |
| <span data-ttu-id="b1d4c-265">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-265">**args_ptr**</span></span> | <span data-ttu-id="b1d4c-266">Parámetro sin usar para la lectura.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-266">Unused parameter for read.</span></span> |
| <span data-ttu-id="b1d4c-267">**args_length**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-267">**args_length**</span></span> | <span data-ttu-id="b1d4c-268">Parámetro sin usar para la lectura.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-268">Unused parameter for read.</span></span> |

### <a name="the-discover-method"></a><span data-ttu-id="b1d4c-269">Método "Discover"</span><span class="sxs-lookup"><span data-stu-id="b1d4c-269">The ‘Discover’ Method</span></span>

<span data-ttu-id="b1d4c-270">El método "Discover" se usa para recuperar la lista de todos los recursos implementados por un objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-270">The ‘Discover’ method is used to retrieve the list of all Resources implemented by an Object.</span></span> <span data-ttu-id="b1d4c-271">Los parámetros se definen como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-271">The parameters are defined as follows.</span></span>

| <span data-ttu-id="b1d4c-272">Parámetro</span><span class="sxs-lookup"><span data-stu-id="b1d4c-272">Parameter</span></span> | <span data-ttu-id="b1d4c-273">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-273">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-274">**operation**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-274">**operation**</span></span> | <span data-ttu-id="b1d4c-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span></span> |
| <span data-ttu-id="b1d4c-276">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-276">**object_ptr**</span></span> | <span data-ttu-id="b1d4c-277">Puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-277">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="b1d4c-278">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-278">**instance_ptr**</span></span> | <span data-ttu-id="b1d4c-279">Puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-279">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-280">**resource**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-280">**resource**</span></span> | <span data-ttu-id="b1d4c-281">Puntero a una matriz de NX_LWM2M_CLIENT_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-281">Pointer to an array of NX_LWM2M_CLIENT_RESOURCE.</span></span> <span data-ttu-id="b1d4c-282">En la devolución, la matriz se rellena con la información de recursos correspondiente.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-282">On return the array is filled with corresponding resource info.</span></span> |
| <span data-ttu-id="b1d4c-283">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-283">**resource_count**</span></span> | <span data-ttu-id="b1d4c-284">Puntero al número de recursos que se van a detectar.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-284">Pointer to the number of resources to discover.</span></span> <span data-ttu-id="b1d4c-285">En la devolución, este parámetro debe actualizarse como el valor true.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-285">On return this parameter must be updated as the true value.</span></span> |
| <span data-ttu-id="b1d4c-286">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-286">**args_ptr**</span></span> | <span data-ttu-id="b1d4c-287">Parámetro sin usar para la detección.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-287">Unused parameter for discover.</span></span> |
| <span data-ttu-id="b1d4c-288">**args_length**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-288">**args_length**</span></span> | <span data-ttu-id="b1d4c-289">Parámetro sin usar para la detección.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-289">Unused parameter for discover.</span></span> |

### <a name="the-write-method"></a><span data-ttu-id="b1d4c-290">Método "Write"</span><span class="sxs-lookup"><span data-stu-id="b1d4c-290">The ‘Write’ Method</span></span>

<span data-ttu-id="b1d4c-291">El método "Write" se usa para actualizar o reemplazar los recursos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-291">The ‘Write’ method is used to update or replace resources of an Object Instance.</span></span> <span data-ttu-id="b1d4c-292">Los parámetros se definen como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-292">The parameters are defined as follows.</span></span>

| <span data-ttu-id="b1d4c-293">Parámetro</span><span class="sxs-lookup"><span data-stu-id="b1d4c-293">Parameter</span></span>  | <span data-ttu-id="b1d4c-294">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-294">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-295">**operation**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-295">**operation**</span></span> | <span data-ttu-id="b1d4c-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span></span> |
| <span data-ttu-id="b1d4c-297">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-297">**object_ptr**</span></span> | <span data-ttu-id="b1d4c-298">Puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-298">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="b1d4c-299">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-299">**instance_ptr**</span></span> | <span data-ttu-id="b1d4c-300">Puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-300">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-301">**resource**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-301">**resource**</span></span> | <span data-ttu-id="b1d4c-302">Puntero a una matriz de **NX_LWM2M_CLIENT_RESOURCE** que contiene los identificadores de los recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-302">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="b1d4c-303">En la devolución, la matriz se rellena con los tipos y valores correspondientes.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-303">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="b1d4c-304">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-304">**resource_count**</span></span> | <span data-ttu-id="b1d4c-305">Puntero al número de recursos que se van a detectar.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-305">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="b1d4c-306">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-306">**args_ptr**</span></span> | <span data-ttu-id="b1d4c-307">Marcas de escritura.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-307">Write flags.</span></span> |
| <span data-ttu-id="b1d4c-308">**args_length**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-308">**args_length**</span></span> | <span data-ttu-id="b1d4c-309">Longitud de los argumentos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-309">The length of the arguments.</span></span> |

<span data-ttu-id="b1d4c-310">Se pueden especificar las siguientes operaciones de escritura en el parámetro *flag*.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-310">The following write operations can be specified to the *flag* parameter.</span></span>

| <span data-ttu-id="b1d4c-311">Operación</span><span class="sxs-lookup"><span data-stu-id="b1d4c-311">Operation</span></span> | <span data-ttu-id="b1d4c-312">Acción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-312">Action</span></span> | <span data-ttu-id="b1d4c-313">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-313">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="b1d4c-314">0</span><span class="sxs-lookup"><span data-stu-id="b1d4c-314">0</span></span> | <span data-ttu-id="b1d4c-315">Actualización parcial</span><span class="sxs-lookup"><span data-stu-id="b1d4c-315">Partial Update</span></span> | <span data-ttu-id="b1d4c-316">Agrega o actualiza los recursos proporcionados en el nuevo valor y deja sin modificar otros recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-316">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span>
| <span data-ttu-id="b1d4c-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="b1d4c-318">Reemplazo de instancia</span><span class="sxs-lookup"><span data-stu-id="b1d4c-318">Replace Instance</span></span> | <span data-ttu-id="b1d4c-319">Reemplaza la instancia de objeto por los nuevos valores de recursos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-319">Replaces the Object Instance with the new provided resource values.</span></span>
| <span data-ttu-id="b1d4c-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> |  <span data-ttu-id="b1d4c-321">Reemplazo de recurso</span><span class="sxs-lookup"><span data-stu-id="b1d4c-321">Replace Resource</span></span> | <span data-ttu-id="b1d4c-322">Reemplaza los recursos por los nuevos valores de recursos proporcionados (usados para reemplazar varios recursos).</span><span class="sxs-lookup"><span data-stu-id="b1d4c-322">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="b1d4c-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span></span> | <span data-ttu-id="b1d4c-324">Create Instance</span><span class="sxs-lookup"><span data-stu-id="b1d4c-324">Create Instance</span></span> | <span data-ttu-id="b1d4c-325">Inicializa la instancia del objeto recién creada con los valores de recursos proporcionados (llamados desde el método **_nx_lwm2m_object_create_**).</span><span class="sxs-lookup"><span data-stu-id="b1d4c-325">Initializes the newly created Object Instance with the provided resource values (called from the **_nx_lwm2m_object_create_** method).</span></span> |
| <span data-ttu-id="b1d4c-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="b1d4c-327">Escritura de arranque</span><span class="sxs-lookup"><span data-stu-id="b1d4c-327">Bootstrap Write</span></span> | <span data-ttu-id="b1d4c-328">Se llama durante la secuencia de arranque.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-328">Called during Bootstrap sequence.</span></span> |

### <a name="the-execute-method"></a><span data-ttu-id="b1d4c-329">Método "Execute"</span><span class="sxs-lookup"><span data-stu-id="b1d4c-329">The ‘Execute’ Method</span></span>

<span data-ttu-id="b1d4c-330">El método "Execute" implementa la ejecución de un recurso de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-330">The ‘Execute’ method implements the execution of an Object Resource.</span></span>

<span data-ttu-id="b1d4c-331">Los parámetros de entrada se definen de la manera siguiente.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-331">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="b1d4c-332">Parámetro</span><span class="sxs-lookup"><span data-stu-id="b1d4c-332">Parameter</span></span>  | <span data-ttu-id="b1d4c-333">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-333">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-334">**operation**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-334">**operation**</span></span> | <span data-ttu-id="b1d4c-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="b1d4c-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span></span> |
| <span data-ttu-id="b1d4c-336">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-336">**object_ptr**</span></span> | <span data-ttu-id="b1d4c-337">Puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-337">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="b1d4c-338">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-338">**instance_ptr**</span></span> | <span data-ttu-id="b1d4c-339">Puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-339">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-340">**resource**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-340">**resource**</span></span> | <span data-ttu-id="b1d4c-341">Puntero a una matriz de **NX_LWM2M_CLIENT_RESOURCE** que contiene los identificadores de los recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-341">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="b1d4c-342">En la devolución, la matriz se rellena con los tipos y valores correspondientes.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-342">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="b1d4c-343">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-343">**resource_count**</span></span> | <span data-ttu-id="b1d4c-344">Puntero al número de recursos que se van a detectar.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-344">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="b1d4c-345">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-345">**args_ptr**</span></span> | <span data-ttu-id="b1d4c-346">Puntero a los argumentos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-346">Pointer to the arguments.</span></span> |
| <span data-ttu-id="b1d4c-347">**args_length**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-347">**args_length**</span></span> | <span data-ttu-id="b1d4c-348">Longitud de los argumentos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-348">The length of the arguments.</span></span>  |

<span data-ttu-id="b1d4c-349">La función debe devolver **NX_LWM2M_CLIENT_NOT_FOUND** si el identificador de recurso no existe, o bien **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** si no admite la ejecución.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-349">The function must return **NX_LWM2M_CLIENT_NOT_FOUND** if the Resource ID doesn’t exist, or **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** if it doesn’t support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="b1d4c-350">Método "Create"</span><span class="sxs-lookup"><span data-stu-id="b1d4c-350">The ‘Create’ Method</span></span>

<span data-ttu-id="b1d4c-351">El método "Create" implementa la creación de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-351">The ‘Create’ method implements the creation of a new Object Instance.</span></span>

<span data-ttu-id="b1d4c-352">Los parámetros de entrada se definen de la manera siguiente.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-352">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="b1d4c-353">Parámetro</span><span class="sxs-lookup"><span data-stu-id="b1d4c-353">Parameter</span></span>  | <span data-ttu-id="b1d4c-354">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-354">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-355">**operation**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-355">**operation**</span></span> | <span data-ttu-id="b1d4c-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span></span> |
| <span data-ttu-id="b1d4c-357">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-357">**object_ptr**</span></span> | <span data-ttu-id="b1d4c-358">Puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-358">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="b1d4c-359">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-359">**instance_ptr**</span></span> | <span data-ttu-id="b1d4c-360">Parámetro sin usar.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-360">Unused parameter.</span></span> |
| <span data-ttu-id="b1d4c-361">**resource**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-361">**resource**</span></span> | <span data-ttu-id="b1d4c-362">Puntero a una matriz de **NX_LWM2M_CLIENT_RESOURCE** que contiene los identificadores de los recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-362">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="b1d4c-363">En la devolución, la matriz se rellena con los tipos y valores correspondientes.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-363">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="b1d4c-364">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-364">**resource_count**</span></span> | <span data-ttu-id="b1d4c-365">Puntero al número de recursos que se van a detectar.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-365">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="b1d4c-366">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-366">**args_ptr**</span></span> | <span data-ttu-id="b1d4c-367">Id. de instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-367">Object instance id.</span></span> |
| <span data-ttu-id="b1d4c-368">**args_length**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-368">**args_length**</span></span> | <span data-ttu-id="b1d4c-369">Longitud de los argumentos.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-369">The length of the arguments.</span></span> |

### <a name="the-delete-method"></a><span data-ttu-id="b1d4c-370">Método "Delete"</span><span class="sxs-lookup"><span data-stu-id="b1d4c-370">The ‘Delete’ Method</span></span>

<span data-ttu-id="b1d4c-371">El método "Delete" implementa la eliminación de una instancia de objeto. Los parámetros de entrada se definen como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-371">The ‘Delete’ method implements the deletion of an object instance, the input parameters are defined as follows.</span></span>

| <span data-ttu-id="b1d4c-372">Parámetro</span><span class="sxs-lookup"><span data-stu-id="b1d4c-372">Parameter</span></span>  | <span data-ttu-id="b1d4c-373">Descripción</span><span class="sxs-lookup"><span data-stu-id="b1d4c-373">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b1d4c-374">**operation**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-374">**operation**</span></span> | <span data-ttu-id="b1d4c-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span><span class="sxs-lookup"><span data-stu-id="b1d4c-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span></span> |
| <span data-ttu-id="b1d4c-376">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-376">**object_ptr**</span></span> | <span data-ttu-id="b1d4c-377">Puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-377">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="b1d4c-378">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-378">**instance_ptr**</span></span> | <span data-ttu-id="b1d4c-379">Puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-379">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="b1d4c-380">**resource**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-380">**resource**</span></span> | <span data-ttu-id="b1d4c-381">Parámetro sin usar.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-381">Unused parameter.</span></span> |
| <span data-ttu-id="b1d4c-382">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-382">**resource_count**</span></span> | <span data-ttu-id="b1d4c-383">Parámetro sin usar.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-383">Unused parameter.</span></span> |
| <span data-ttu-id="b1d4c-384">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-384">**args_ptr**</span></span> | <span data-ttu-id="b1d4c-385">Parámetro sin usar.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-385">Unused parameter.</span></span> |
| <span data-ttu-id="b1d4c-386">**args_length**</span><span class="sxs-lookup"><span data-stu-id="b1d4c-386">**args_length**</span></span> | <span data-ttu-id="b1d4c-387">Parámetro sin usar.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-387">Unused parameter.</span></span> |

<span data-ttu-id="b1d4c-388">Si se ejecuta correctamente, el objeto debe liberar los datos de la instancia de objeto y cualquier otro recurso asignado por la instancia.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-388">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="b1d4c-389">Ejemplo de aplicación cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="b1d4c-389">Example of LWM2M Client Application</span></span>

<span data-ttu-id="b1d4c-390">El código siguiente es un ejemplo de una aplicación cliente LWM2M simple que implementa un dispositivo personalizado que consta de un sensor de temperatura y un interruptor de luz.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-390">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="b1d4c-391">El dispositivo permite que un servidor lea el valor del sensor de temperatura y el estado booleano del interruptor de luz, así como encender y apagar dicho dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-391">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```