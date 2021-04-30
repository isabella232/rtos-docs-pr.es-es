---
title: 'Capítulo 3: Descripción funcional de Azure RTOS NetX LWM2M'
description: Este capítulo contiene una descripción funcional de Azure RTOS NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f49a4f5f4c899dfa461a9d57a8b56e4503d6acd4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815173"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="8b316-103">Capítulo 3: Descripción funcional de Azure RTOS NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="8b316-103">Chapter 3 - Functional description of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="8b316-104">Este capítulo contiene una descripción funcional de Azure RTOS NetX LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-104">This chapter contains a functional description of Azure RTOS NetX LWM2M.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="8b316-105">Inicialización del cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="8b316-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="8b316-106">El cliente LWM2M se inicializa mediante una llamada al servicio ***nx_lwm2m_client_create***.</span><span class="sxs-lookup"><span data-stu-id="8b316-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="8b316-107">El cliente LWM2M se ejecuta en su propio subproceso y puede notificar algunos eventos a la aplicación mediante devoluciones de llamada o bien llamando a los métodos de los objetos personalizados implementados por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8b316-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="8b316-108">Además, las sesiones del cliente LWM2M deben crearse mediante una llamada a ***nx_lwm2m_client_session_create*** para habilitar la comunicación con uno o más servidores.</span><span class="sxs-lookup"><span data-stu-id="8b316-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="8b316-109">Una sesión puede comunicarse con dos tipos de servidores diferentes: un servidor de arranque o un servidor LWM2M (administración de dispositivos).</span><span class="sxs-lookup"><span data-stu-id="8b316-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="8b316-110">Sesión del servidor de arranque</span><span class="sxs-lookup"><span data-stu-id="8b316-110">Bootstrap Server Session</span></span>

<span data-ttu-id="8b316-111">Una sesión de comunicación con un servidor de arranque se usa para aprovisionar información esencial en el cliente LWM2M para permitir que este realice la operación "Registro" con uno o varios servidores LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation "Register" with one or more LWM2M Servers.</span></span> <span data-ttu-id="8b316-112">Este tipo de servidor se usa durante los modos de arranque iniciados por el cliente y por el servidor.</span><span class="sxs-lookup"><span data-stu-id="8b316-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="8b316-113">La aplicación puede iniciar una sesión de arranque mediante una llamada a ***nx_lwm2m_client_session_bootstrap** _ o _*_nx_lwm2m_client_session_bootstrap_dtls_\*_; debe proporcionar la dirección IP y el número de puerto del servidor, y un identificador de instancia de objeto de seguridad opcional.</span><span class="sxs-lookup"><span data-stu-id="8b316-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="8b316-114">La función _*_nx_lwm2m_client_session_bootstrap_*_ utiliza la comunicación no segura, mientras que _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establece una conexión DTLS segura con el servidor.</span><span class="sxs-lookup"><span data-stu-id="8b316-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="8b316-115">Si la operación de arranque se realiza correctamente, el servidor de arranque debe haber creado instancias de objeto de seguridad para los servidores de arranque y LWM2M, e instancias de objeto de servidor para los servidores LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="8b316-116">La aplicación debe utilizar esta información para establecer una sesión con los servidores LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-116">The application must use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="8b316-117">La aplicación debe guardar los datos de arranque en la memoria no volátil para configurar el cliente LWM2M en el siguiente reinicio del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8b316-117">The Bootstrap data should be saved to non-volatile memory by the application in order to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="8b316-118">Sesión del servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="8b316-118">LWM2M Server Session</span></span>

<span data-ttu-id="8b316-119">Una sesión de comunicación con un servidor LWM2M se usa para el registro, la administración de dispositivos y la habilitación del servicio.</span><span class="sxs-lookup"><span data-stu-id="8b316-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="8b316-120">La aplicación puede registrar el cliente LWM2M en un servidor mediante una llamada a ***nx_lwm2m_client_session_register** _ o _*_nx_lwm2m_client_session_register_dtls_\*_; debe proporcionar la dirección IP y el número de puerto del servidor, y el identificador de servidor corto que corresponde a una instancia de objeto de servidor existente.</span><span class="sxs-lookup"><span data-stu-id="8b316-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="8b316-121">La función _*_nx_lwm2m_client_session_register_*_ utiliza la comunicación no segura, mientras que _ *_nx_lwm2m_client_session_register_dtls_*\* establece una conexión DTLS segura con el servidor.</span><span class="sxs-lookup"><span data-stu-id="8b316-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="8b316-122">La aplicación puede anular el registro del cliente LWM2M mediante una llamada a ***nx_lwm2m_client_session_deregister** _ y pedir al cliente que envíe un mensaje de "actualización" mediante una llamada a _*_nx_lwm2m_client_session_update_\*\*.</span><span class="sxs-lookup"><span data-stu-id="8b316-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an 'Update' message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="8b316-123">Devolución de llamada de estado de sesión</span><span class="sxs-lookup"><span data-stu-id="8b316-123">Session State Callback</span></span>

<span data-ttu-id="8b316-124">La aplicación registra una devolución de llamada durante la creación de una sesión a la que se llama cuando se actualiza el estado de la sesión; la función de devolución de llamada NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK tiene el siguiente prototipo:</span><span class="sxs-lookup"><span data-stu-id="8b316-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK has the following prototype:</span></span>

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

<span data-ttu-id="8b316-125">Los estados siguientes están definidos:</span><span class="sxs-lookup"><span data-stu-id="8b316-125">The following states are defined :</span></span>

- <span data-ttu-id="8b316-126">**NX_LWM2M_CLIENT_SESSION_INIT**: el estado inicial después de la creación de la sesión.</span><span class="sxs-lookup"><span data-stu-id="8b316-126">**NX_LWM2M_CLIENT_SESSION_INIT**: The initial state after session creation.</span></span>

- <span data-ttu-id="8b316-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: el cliente está esperando la expiración del temporizador "Hold Off" o el arranque iniciado por el servidor.</span><span class="sxs-lookup"><span data-stu-id="8b316-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: The client is waiting for the expiration of the 'Hold Off' timer or Server Initiated Bootstrap.</span></span>

- <span data-ttu-id="8b316-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: el cliente envió un mensaje de "solicitud" al servidor de arranque (arranque iniciado por el cliente).</span><span class="sxs-lookup"><span data-stu-id="8b316-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: The client has sent a 'Request' message to the Bootstrap Server (Client Initiated Bootstrap).</span></span>

- <span data-ttu-id="8b316-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: el cliente recibe datos del servidor de arranque.</span><span class="sxs-lookup"><span data-stu-id="8b316-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: The client is receiving data from the Bootstrap Server.</span></span>

- <span data-ttu-id="8b316-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: el servidor de arranque envió un mensaje de "finalizado".</span><span class="sxs-lookup"><span data-stu-id="8b316-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: The Bootstrap Server has sent a 'Finished' message.</span></span>

- <span data-ttu-id="8b316-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: error en la sesión de arranque.</span><span class="sxs-lookup"><span data-stu-id="8b316-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: The bootstrap session has failed.</span></span>

- <span data-ttu-id="8b316-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: el cliente envió un mensaje de "registro" al servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: The client has sent a 'Register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="8b316-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: el cliente está registrado en el servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: The client is registered to the LWM2M Server.</span></span>

- <span data-ttu-id="8b316-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: el cliente envió un mensaje de "actualización" al servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: The client has sent an 'Update' message to the LWM2M Server.</span></span>

- <span data-ttu-id="8b316-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: el cliente envió un mensaje de "anulación de registro" al servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: The client has sent an 'De-register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="8b316-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: se anuló el registro del cliente del servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: The client is de-registered from the LWM2M Server.</span></span>

- <span data-ttu-id="8b316-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: el servidor LWM2M está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="8b316-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: The LWM2M Server is disabled.</span></span> <span data-ttu-id="8b316-138">Se enviará un mensaje de registro después de la expiración del temporizador de deshabilitación.</span><span class="sxs-lookup"><span data-stu-id="8b316-138">A 'Register' will be sent after the expiration of the disable timer.</span></span>

- <span data-ttu-id="8b316-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: no se pudo realizar la operación de registro o actualización en el servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: The registration or update operation to the LWM2M Server has failed.</span></span>

- <span data-ttu-id="8b316-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: se eliminó la instancia de objeto de servidor correspondiente al servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> <span data-ttu-id="8b316-141">En caso de error, la aplicación puede recuperar la causa del error mediante una llamada a **_nx_lwm2m_client_session_error_get_**.</span><span class="sxs-lookup"><span data-stu-id="8b316-141">In case of error the application can retrieve the cause of the error by calling **_nx_lwm2m_client_session_error_get_**.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="8b316-142">Administración de dispositivos locales</span><span class="sxs-lookup"><span data-stu-id="8b316-142">Local Device Management</span></span>

<span data-ttu-id="8b316-143">La aplicación puede acceder a los objetos del cliente LWM2M mediante las funciones de administración de dispositivos locales.</span><span class="sxs-lookup"><span data-stu-id="8b316-143">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="8b316-144">Se proporcionan las funciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="8b316-144">The following functions are provided:</span></span>

- <span data-ttu-id="8b316-145">***nx_lwm2m_client_object_read***: permite leer los recursos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-145">***nx_lwm2m_client_object_read***: Read resources from an Object Instance.</span></span>

- <span data-ttu-id="8b316-146">***nx_lwm2m_client_object_discover***: permite obtener la lista de recursos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-146">***nx_lwm2m_client_object_discover***: Get the list of the resources of an Object Instance.</span></span>

- <span data-ttu-id="8b316-147">***nx_lwm2m_client_object_write***: permite escribir recursos en una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-147">***nx_lwm2m_client_object_write***: Write resources to an Object Instance</span></span>

- <span data-ttu-id="8b316-148">***nx_lwm2m_client_object_execute***: permite realizar la operación de ejecución en un recurso de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-148">***nx_lwm2m_client_object_execute***: Perform the Execute operation on a resource of an Object Instance.</span></span>

- <span data-ttu-id="8b316-149">***nx_lwm2m_client_object_create***: permite crear una instancia de objeto nueva.</span><span class="sxs-lookup"><span data-stu-id="8b316-149">***nx_lwm2m_client_object_create***: Create a new Object Instance.</span></span>

- <span data-ttu-id="8b316-150">***nx_lwm2m_client_object_delete***: permite eliminar una instancia de objeto existente.</span><span class="sxs-lookup"><span data-stu-id="8b316-150">***nx_lwm2m_client_object_delete***: Delete an existing Object Instance.</span></span>

- <span data-ttu-id="8b316-151">***nx_lwm2m_client_object_get_next***: permite obtener el id. de objeto siguiente implementado por el cliente de LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8b316-151">***nx_lwm2m_client_object_get_next***: Get the next Object ID implemented by the LWM2M Client.</span></span>

- <span data-ttu-id="8b316-152">***nx_lwm2m_client_object_instance_get_next***: permite obtener la instancia siguiente de un objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-152">***nx_lwm2m_client_object_instance_get_next***: Get the next Instance of an Object.</span></span>

## <a name="resource-information"></a><span data-ttu-id="8b316-153">Información de recursos</span><span class="sxs-lookup"><span data-stu-id="8b316-153">Resource Information</span></span>

<span data-ttu-id="8b316-154">Al leer y escribir en objetos, un recurso se representa mediante la estructura de NX_LWM2M_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="8b316-154">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="8b316-155">Esta estructura contiene el identificador del recurso o la instancia y su valor.</span><span class="sxs-lookup"><span data-stu-id="8b316-155">This structure contains the ID of the Resource/Instance and its value.</span></span> <span data-ttu-id="8b316-156">La codificación del valor depende de su tipo y su origen (aplicación o red).</span><span class="sxs-lookup"><span data-stu-id="8b316-156">The encoding of the value depends on its type and its origin (application or network).</span></span>

<span data-ttu-id="8b316-157">La estructura de NX_LWM2M_RESOURCE tiene la definición siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-157">The NX_LWM2M_RESOURCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- <span data-ttu-id="8b316-158">**nx_lwm2m_resource_id**: el id. del recurso o de la instancia.</span><span class="sxs-lookup"><span data-stu-id="8b316-158">**nx_lwm2m_resource_id**: The ID of the Resource or the Instance.</span></span>
- <span data-ttu-id="8b316-159">**nx_lwm2m_resource_type**: el tipo del valor (ver a continuación).</span><span class="sxs-lookup"><span data-stu-id="8b316-159">**nx_lwm2m_resource_type**: The type of the value, see below.</span></span>
- <span data-ttu-id="8b316-160">**nx_lwm2m_resource_value**: el valor del recurso. Depende del tipo del valor.</span><span class="sxs-lookup"><span data-stu-id="8b316-160">**nx_lwm2m_resource_value**: The value of the Resource, depends on the type of the value.</span></span>

<span data-ttu-id="8b316-161">Se definen los siguientes tipos de valores:</span><span class="sxs-lookup"><span data-stu-id="8b316-161">The following type of values are defined :</span></span>

- <span data-ttu-id="8b316-162">**NX_LWM2M_RESOURCE_NONE**: recurso vacío.</span><span class="sxs-lookup"><span data-stu-id="8b316-162">**NX_LWM2M_RESOURCE_NONE**: Empty resource.</span></span>

- <span data-ttu-id="8b316-163">**NX_LWM2M_RESOURCE_STRING**: valor de cadena UTF-8 terminado en NULL almacenado en *nx_lwm2m_resource_stringdata*.</span><span class="sxs-lookup"><span data-stu-id="8b316-163">**NX_LWM2M_RESOURCE_STRING**: A null-terminated UTF-8 string value stored in *nx_lwm2m_resource_stringdata*.</span></span>

- <span data-ttu-id="8b316-164">**NX_LWM2M_RESOURCE_INTEGER32**: valor entero de 32 bits almacenado en *nx_lwm2m_resource_integer32data*.</span><span class="sxs-lookup"><span data-stu-id="8b316-164">**NX_LWM2M_RESOURCE_INTEGER32**: A 32-Bit Integer value stored in *nx_lwm2m_resource_integer32data*.</span></span>

- <span data-ttu-id="8b316-165">**NX_LWM2M_RESOURCE_INTEGER64**: valor entero de 64 bits almacenado en *nx_lwm2m_resource_integer64data*.</span><span class="sxs-lookup"><span data-stu-id="8b316-165">**NX_LWM2M_RESOURCE_INTEGER64**: A 64-Bit Integer value stored in *nx_lwm2m_resource_integer64data*.</span></span>

- <span data-ttu-id="8b316-166">**NX_LWM2M_RESOURCE_FLOAT32**: valor de número de punto flotante de 32 bits almacenado en *nx_lwm2m_resource_float32data*.</span><span class="sxs-lookup"><span data-stu-id="8b316-166">**NX_LWM2M_RESOURCE_FLOAT32**: A 32-Bit Floating Point value stored in *nx_lwm2m_resource_float32data*.</span></span>

- <span data-ttu-id="8b316-167">**NX_LWM2M_RESOURCE_FLOAT64**: valor de número de punto flotante de 64 bits almacenado en *nx_lwm2m_resource_float64data*.</span><span class="sxs-lookup"><span data-stu-id="8b316-167">**NX_LWM2M_RESOURCE_FLOAT64**: A 64-Bit Floating Point value stored in *nx_lwm2m_resource_float64data*.</span></span>

- <span data-ttu-id="8b316-168">**NX_LWM2M_RESOURCE_BOOLEAN**: valor booleano almacenado en *nx_lwm2m_resource_booleandata*.</span><span class="sxs-lookup"><span data-stu-id="8b316-168">**NX_LWM2M_RESOURCE_BOOLEAN**: A Boolean value stored in *nx_lwm2m_resource_booleandata*.</span></span>

- <span data-ttu-id="8b316-169">**NX_LWM2M_RESOURCE_OPAQUE**: valor opaco definido por *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="8b316-169">**NX_LWM2M_RESOURCE_OPAQUE**: An Opaque value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="8b316-170">**NX_LWM2M_RESOURCE_OBJLNK**: valor de vínculo de objeto almacenado en *nx_lwm2m_resource_objlnkdata*.</span><span class="sxs-lookup"><span data-stu-id="8b316-170">**NX_LWM2M_RESOURCE_OBJLNK**: An Object Link value stored in *nx_lwm2m_resource_objlnkdata*.</span></span>

- <span data-ttu-id="8b316-171">**NX_LWM2M_RESOURCE_TLV**: valor codificado TLV definido por *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="8b316-171">**NX_LWM2M_RESOURCE_TLV**: A TLV encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="8b316-172">**NX_LWM2M_RESOURCE_TEXT**: valor codificado de texto sin formato definido por *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="8b316-172">**NX_LWM2M_RESOURCE_TEXT**: A Plain-Text encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="8b316-173">**NX_LWM2M_RESOURCE_MULTIPLE**: recurso múltiple definido por *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="8b316-173">**NX_LWM2M_RESOURCE_MULTIPLE**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="8b316-174">*nx_lwm2m_resource_multiple_ptr* es un puntero a una matriz de estructuras **NX_LWM2M_RESOURCE** que contienen información sobre cada instancia de recurso.</span><span class="sxs-lookup"><span data-stu-id="8b316-174">*nx_lwm2m_resource_multiple_ptr* is a pointer to an array of **NX_LWM2M_RESOURCE** structures containing information about each Resource Instances.</span></span>

- <span data-ttu-id="8b316-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: recurso múltiple definido por *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="8b316-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="8b316-176">*nx_lwm2m_resource_multiple_ptr* es un puntero a un búfer codificado TLV.</span><span class="sxs-lookup"><span data-stu-id="8b316-176">*nx_lwm2m_resource_multiple_ptr* is a pointer to a TLV encoded buffer.</span></span>

<span data-ttu-id="8b316-177">Se proporcionan funciones útiles para recuperar el valor y comprobar su tipo. La aplicación nunca debe acceder directamente al campo *nx_lwm2m_resource_value* al obtener un valor de una estructura NX_LWM2M_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="8b316-177">Convenience functions are provided for retrieving the value and checking its type, the application should never directly access the *nx_lwm2m_resource_value* field when getting a value from a NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="8b316-178">Se definen las funciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="8b316-178">The following functions are defined :</span></span>

- <span data-ttu-id="8b316-179">***nx_lwm2m_resource_get_***: permite obtener un valor con el tipo determinado.</span><span class="sxs-lookup"><span data-stu-id="8b316-179">***nx_lwm2m_resource_get_***: Get a value with the given type.</span></span>
- <span data-ttu-id="8b316-180">***nx_lwm2m_resource_multiple_get_***: permite obtener un valor con el tipo determinado a partir de un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="8b316-180">***nx_lwm2m_resource_multiple_get_***: Get a value with the given type from a Multiple Resource.</span></span>

<span data-ttu-id="8b316-181">La macro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(tipo) se puede usar para comprobar si un tipo de recurso es un recurso múltiple.</span><span class="sxs-lookup"><span data-stu-id="8b316-181">The macro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(type) can be used to check if a resource type is a Multiple Resource.</span></span>

## <a name="object-implementation"></a><span data-ttu-id="8b316-182">Implementación de objetos</span><span class="sxs-lookup"><span data-stu-id="8b316-182">Object Implementation</span></span>

<span data-ttu-id="8b316-183">El cliente LWM2M implementa los siguientes objetos OMA LWM2M obligatorios: Seguridad (0), Servidor (1), Control de acceso (2) y Dispositivo (3).</span><span class="sxs-lookup"><span data-stu-id="8b316-183">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="8b316-184">La aplicación debe implementar otros objetos específicos del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8b316-184">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="8b316-185">Se usan dos estructuras de datos para definir un objeto: la estructura NX_LWM2M_OBJECT define la implementación del objeto (incluidos el id. de objeto y los métodos de objeto) y la estructura NX_LWM2M_OBJECT_INSTANCE contiene los datos de una instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-185">Two data structures are used to define an Object: the NX_LWM2M_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="8b316-186">La estructura de NX_LWM2M_OBJECT tiene la definición siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-186">The NX_LWM2M_OBJECT structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- <span data-ttu-id="8b316-187">**nx_lwm2m_object_next**: el objeto siguiente de la lista.</span><span class="sxs-lookup"><span data-stu-id="8b316-187">**nx_lwm2m_object_next**: The next object in the list.</span></span>
- <span data-ttu-id="8b316-188">**nx_lwm2m_object_id**: el id. del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-188">**nx_lwm2m_object_id**: The Object ID.</span></span>
- <span data-ttu-id="8b316-189">**nx_lwm2m_object_read**: el método "Read" (ver a continuación).</span><span class="sxs-lookup"><span data-stu-id="8b316-189">**nx_lwm2m_object_read**: The 'Read' method, see below.</span></span>
- <span data-ttu-id="8b316-190">**nx_lwm2m_object_discover**: el método "Discover" (ver a continuación).</span><span class="sxs-lookup"><span data-stu-id="8b316-190">**nx_lwm2m_object_discover**: The 'Discover' method, see below.</span></span>
- <span data-ttu-id="8b316-191">**nx_lwm2m_object_write**: el método "Write" (ver a continuación).</span><span class="sxs-lookup"><span data-stu-id="8b316-191">**nx_lwm2m_object_write**: The 'Write' method, see below.</span></span>
- <span data-ttu-id="8b316-192">**nx_lwm2m_object_execute**: el método "Execute" (ver a continuación).</span><span class="sxs-lookup"><span data-stu-id="8b316-192">**nx_lwm2m_object_execute**: The 'Execute' method, see below.</span></span>
- <span data-ttu-id="8b316-193">**nx_lwm2m_object_create**: el método "Create" (ver a continuación).</span><span class="sxs-lookup"><span data-stu-id="8b316-193">**nx_lwm2m_object_create**: The 'Create' method, see below.</span></span>
- <span data-ttu-id="8b316-194">**nx_lwm2m_object_delete**: el método "Delete" (ver a continuación).</span><span class="sxs-lookup"><span data-stu-id="8b316-194">**nx_lwm2m_object_delete**: The 'Delete' method, see below.</span></span>
- <span data-ttu-id="8b316-195">**nx_lwm2m_object_instances**: lista de instancias de objeto terminada en NULL.</span><span class="sxs-lookup"><span data-stu-id="8b316-195">**nx_lwm2m_object_instances**: The NULL-terminated list of object instances.</span></span>

<span data-ttu-id="8b316-196">La estructura NX_LWM2M_OBJECT_INSTANCE tiene la definición siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-196">The NX_LWM2M_OBJECT_INSTANCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- <span data-ttu-id="8b316-197">**nx_lwm2m_object_instance_next**: la instancia siguiente de la lista.</span><span class="sxs-lookup"><span data-stu-id="8b316-197">**nx_lwm2m_object_instance_next**: The next instance in the list.</span></span>
- <span data-ttu-id="8b316-198">**nx_lwm2m_object_instance_id**: el id. de la instancia de objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-198">**nx_lwm2m_object_instance_id**: The Object Instance ID.</span></span>

<span data-ttu-id="8b316-199">El objeto debe implementar los métodos que corresponden a las operaciones definidas por la interfaz de administración de dispositivos LWM2M: "Read", "Discover", "Write", "Execute", "Create" y "Delete".</span><span class="sxs-lookup"><span data-stu-id="8b316-199">The Object must implement the methods corresponding to the operations defined by the LWM2M Device Management Interface: 'Read', 'Discover', 'Write', 'Execute', 'Create' and 'Delete'.</span></span> <span data-ttu-id="8b316-200">Los métodos "Create" y "Delete" se pueden establecer en NULL si el objeto no admite la creación dinámica de instancias.</span><span class="sxs-lookup"><span data-stu-id="8b316-200">The 'Create' and 'Delete' methods can be set to NULL if the object doesn't support dynamic creation of instances.</span></span>

### <a name="the-read-method"></a><span data-ttu-id="8b316-201">Método "Read"</span><span class="sxs-lookup"><span data-stu-id="8b316-201">The 'Read' Method</span></span>

<span data-ttu-id="8b316-202">El método "Read" se usa para leer los valores de recursos de una instancia de objeto; la función tiene la definición siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-202">The 'Read' method is used to read Resource values from an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

<span data-ttu-id="8b316-203">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-203">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8b316-204">**object_ptr**: puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-204">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="8b316-205">**instance_ptr**: puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-205">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="8b316-206">**num_values**: número de recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="8b316-206">**num_values**: The number of resources to read.</span></span>

- <span data-ttu-id="8b316-207">**values_ptr**: puntero a una matriz de NX_LWM2M_RESOURCE que contiene los identificadores de los recursos que se van a leer.</span><span class="sxs-lookup"><span data-stu-id="8b316-207">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="8b316-208">En la devolución, la matriz se rellena con los tipos y valores correspondientes.</span><span class="sxs-lookup"><span data-stu-id="8b316-208">On return the array is filled with the corresponding types and values.</span></span>

### <a name="the-discover-method"></a><span data-ttu-id="8b316-209">Método "Discover"</span><span class="sxs-lookup"><span data-stu-id="8b316-209">The 'Discover' Method</span></span>

<span data-ttu-id="8b316-210">El método '"Discover" se usa para recuperar la lista de todos los recursos que un objeto implementa; la función tiene la definición siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-210">The 'Discover' method is used to retrieve the list of all Resources implemented by an Object, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

<span data-ttu-id="8b316-211">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-211">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8b316-212">**object_ptr**: puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-212">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="8b316-213">**instance_ptr**: puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-213">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="8b316-214">**num_resources_ptr**: en la entrada, el tamaño del búfer de destino; en la salida, el número de elementos escritos en el búfer.</span><span class="sxs-lookup"><span data-stu-id="8b316-214">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>

- <span data-ttu-id="8b316-215">**resources_ptr**: puntero al búfer de destino.</span><span class="sxs-lookup"><span data-stu-id="8b316-215">**resources_ptr**: Pointer to the destination buffer.</span></span>

<span data-ttu-id="8b316-216">La información de los recursos se devuelve en una estructura NX_LWM2M_RESOURCE_INFO que se define como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="8b316-216">The resource information is returned in a NX_LWM2M_RESOURCE_INFO structure defined as follows:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- <span data-ttu-id="8b316-217">**nx_lwm2m_resource_info_id**: el id. del recurso.</span><span class="sxs-lookup"><span data-stu-id="8b316-217">**nx_lwm2m_resource_info_id**: The ID of the Resource.</span></span>

- <span data-ttu-id="8b316-218">**nx_lwm2m_resource_info_flags**: ver a continuación.</span><span class="sxs-lookup"><span data-stu-id="8b316-218">**nx_lwm2m_resource_info_flags**: See below.</span></span>

- <span data-ttu-id="8b316-219">**nx_lwm2m_resource_info_dim**: la dimensión de un recurso múltiple si está establecida la marca NX_LWM2M_RESOURCE_INFO_MULTIPLE.</span><span class="sxs-lookup"><span data-stu-id="8b316-219">**nx_lwm2m_resource_info_dim**: The dimension of Multiple Resource if the flag NX_LWM2M_RESOURCE_INFO_MULTIPLE is set.</span></span>

<span data-ttu-id="8b316-220">El campo *nx_lwm2m_resource_flags* puede tener los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="8b316-220">The field *nx_lwm2m_resource_flags* can have to the following values:</span></span>

- <span data-ttu-id="8b316-221">0: recurso legible único.</span><span class="sxs-lookup"><span data-stu-id="8b316-221">0: Single readable resource.</span></span>

- <span data-ttu-id="8b316-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: recurso múltiple; se debe definir *nx_lwm2m_resource_info_dim*.</span><span class="sxs-lookup"><span data-stu-id="8b316-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: Multiple Resource, *nx_lwm2m_resource_info_dim* must be defined.</span></span>

- <span data-ttu-id="8b316-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: recurso ejecutable o no legible.</span><span class="sxs-lookup"><span data-stu-id="8b316-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: Executable or Non-Readable Resource.</span></span>

### <a name="the-write-method"></a><span data-ttu-id="8b316-224">Método "Write"</span><span class="sxs-lookup"><span data-stu-id="8b316-224">The 'Write' Method</span></span>

<span data-ttu-id="8b316-225">El método "Write" se usa para actualizar o reemplazar los recursos de una instancia de objeto; la función tiene la definición siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-225">The 'Write' method is used to update or replace resources of an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

<span data-ttu-id="8b316-226">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-226">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8b316-227">**object_ptr**: puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-227">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="8b316-228">**instance_ptr**: puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-228">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="8b316-229">**num_values**: número de recursos que se van a escribir.</span><span class="sxs-lookup"><span data-stu-id="8b316-229">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="8b316-230">**values_ptr**:puntero a los valores de los recursos.</span><span class="sxs-lookup"><span data-stu-id="8b316-230">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="8b316-231">**write_op**: tipo de operaciones de escritura.</span><span class="sxs-lookup"><span data-stu-id="8b316-231">**write_op**: The type of write operations.</span></span>

<span data-ttu-id="8b316-232">Se pueden especificar las operaciones de escritura siguientes en el parámetro *write_op*:</span><span class="sxs-lookup"><span data-stu-id="8b316-232">The following write operations can be specified to the *write_op* parameter :</span></span>

- <span data-ttu-id="8b316-233">0 &mdash; Actualización parcial: agrega o actualiza los recursos proporcionados en el valor nuevo y deja sin modificar otros recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="8b316-233">0 &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="8b316-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Reemplazo de instancia: reemplaza la instancia de objeto por los valores de recursos proporcionados nuevos.</span><span class="sxs-lookup"><span data-stu-id="8b316-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="8b316-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Reemplazo de recurso: reemplaza los recursos por los valores de recursos proporcionados nuevos (se usa para reemplazar los recursos múltiples).</span><span class="sxs-lookup"><span data-stu-id="8b316-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="8b316-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Creación de instancia: inicializa la instancia de objeto que recién se creó por los valores de recursos proporcionados (se llama desde el método *nx_lwm2m_object_create*).</span><span class="sxs-lookup"><span data-stu-id="8b316-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Create Instance: initializes the newly created Object Instance with the provided resource values (called from the *nx_lwm2m_object_create* method).</span></span>

- <span data-ttu-id="8b316-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Escritura de arranque: se llama durante la secuencia de arranque.</span><span class="sxs-lookup"><span data-stu-id="8b316-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: called during Bootstrap sequence.</span></span>

### <a name="the-execute-method"></a><span data-ttu-id="8b316-238">Método "Execute"</span><span class="sxs-lookup"><span data-stu-id="8b316-238">The 'Execute' Method</span></span>

<span data-ttu-id="8b316-239">El método "Execute" implementa la ejecución de un recurso de objeto; la función tiene la definición siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-239">The 'Execute' method implements the execution of an Object Resource, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

<span data-ttu-id="8b316-240">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-240">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8b316-241">**object_ptr**: puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-241">**object_ptr**: Pointer to the Object implementation</span></span>
- <span data-ttu-id="8b316-242">**instance_ptr**: puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-242">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="8b316-243">**resource_id**: id. del recurso.</span><span class="sxs-lookup"><span data-stu-id="8b316-243">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="8b316-244">**arguments_ptr**: puntero a los argumentos de la operación de ejecución.</span><span class="sxs-lookup"><span data-stu-id="8b316-244">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="8b316-245">Puede ser NULL si *arguments_length* es cero.</span><span class="sxs-lookup"><span data-stu-id="8b316-245">Can be NULL if *arguments_length* is zero.</span></span>
- <span data-ttu-id="8b316-246">**arguments_length**: longitud de los argumentos.</span><span class="sxs-lookup"><span data-stu-id="8b316-246">**arguments_length**: The length of the arguments.</span></span>

<span data-ttu-id="8b316-247">La función debe devolver NX_LWM2M_NOT_FOUND si el id. de recurso no existe, o bien NX_LWM2M_METHOD_NOT_ALLOWED si no admite la ejecución.</span><span class="sxs-lookup"><span data-stu-id="8b316-247">The function must return NX_LWM2M_NOT_FOUND if the Resource ID doesn't exist, or NX_LWM2M_METHOD_NOT_ALLOWED if it doesn't support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="8b316-248">Método "Create"</span><span class="sxs-lookup"><span data-stu-id="8b316-248">The 'Create' Method</span></span>

<span data-ttu-id="8b316-249">El método "Create" implementa la creación de una instancia de objeto nueva; la función tiene la definición siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-249">The 'Create' method implements the creation of a new Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

<span data-ttu-id="8b316-250">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-250">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8b316-251">**object_ptr**: puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-251">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="8b316-252">**instance_id**: id. de la instancia nueva.</span><span class="sxs-lookup"><span data-stu-id="8b316-252">**instance_id**: The ID of the new Instance.</span></span>
- <span data-ttu-id="8b316-253">**num_values**: número de recursos que se van a inicializar.</span><span class="sxs-lookup"><span data-stu-id="8b316-253">**num_values**: The number of resources to initialize.</span></span>
- <span data-ttu-id="8b316-254">**values_ptr**:puntero a los valores de los recursos.</span><span class="sxs-lookup"><span data-stu-id="8b316-254">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="8b316-255">**instance_ptr**: puntero al puntero de destino de la instancia creada.</span><span class="sxs-lookup"><span data-stu-id="8b316-255">**instance_ptr**: Pointer to the destination pointer of the created instance.</span></span>
- <span data-ttu-id="8b316-256">**bootstrap**: True si se llamada desde la secuencia de arranque.</span><span class="sxs-lookup"><span data-stu-id="8b316-256">**bootstrap**: True if called from bootstrap sequence.</span></span>

<span data-ttu-id="8b316-257">El objeto debe asignar e inicializar una instancia de objeto nueva con la lista de valores de recursos proporcionada.</span><span class="sxs-lookup"><span data-stu-id="8b316-257">The Object must allocate and initialiaze a new Object instance, using the provided list of resource values.</span></span>

### <a name="the-delete-method"></a><span data-ttu-id="8b316-258">Método "Delete"</span><span class="sxs-lookup"><span data-stu-id="8b316-258">The 'Delete' Method</span></span>

<span data-ttu-id="8b316-259">El método "Delete" implementa la eliminación de una instancia de objeto; la función tiene la definición siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-259">The 'Delete' method implements the deletion of an object instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

<span data-ttu-id="8b316-260">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="8b316-260">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8b316-261">**object_ptr**: puntero a la implementación del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-261">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="8b316-262">**instance_ptr**: puntero a la instancia del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-262">**instance_ptr**: Pointer to the Object Instance.</span></span>

<span data-ttu-id="8b316-263">Si se ejecuta correctamente, el objeto debe liberar los datos de la instancia de objeto y cualquier otro recurso asignado por la instancia.</span><span class="sxs-lookup"><span data-stu-id="8b316-263">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a><span data-ttu-id="8b316-264">Incorporación de implementaciones e instancias de objeto al cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="8b316-264">Adding Object Implementations and Instances to the LWM2M Client</span></span>

<span data-ttu-id="8b316-265">La aplicación puede agregar una implementación de objeto nueva al cliente LWM2M mediante una llamada al servicio ***nx_lwm2m_client_object_add***.</span><span class="sxs-lookup"><span data-stu-id="8b316-265">The application can add new object implementation to the LWM2M Client by calling the ***nx_lwm2m_client_object_add*** service.</span></span>

<span data-ttu-id="8b316-266">Si el objeto no admite la creación dinámica de instancias (por ejemplo, si se trata de un objeto solo de instancia única), el campo *nx_lwm2m_object_instances* de la estructura del objeto debería apuntar a la lista de las estructuras de instancias estáticas.</span><span class="sxs-lookup"><span data-stu-id="8b316-266">If the Object doesn't support dynamic creation of Instances, for example if it's a single instance only Object, the *nx_lwm2m_object_instances* field of the object structure should point to the list of the static instances structures.</span></span>

<span data-ttu-id="8b316-267">Si el objeto admite la creación dinámica de instancias, *nx_lwm2m_object_instances* se debe establecer en NULL y, en su lugar, se debe usar el servicio ***nx_lwm2m_client_object_create*** para llamar al método "Create" del objeto.</span><span class="sxs-lookup"><span data-stu-id="8b316-267">If the Object supports dynamic instance creation, *nx_lwm2m_object_instances* should be set to NULL and the ***nx_lwm2m_client_object_create*** service should be used instead in order to call the 'Create' method of the object.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="8b316-268">Ejemplo de aplicación cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="8b316-268">Example of LWM2M Client Application</span></span>

<span data-ttu-id="8b316-269">El código siguiente es un ejemplo de una aplicación cliente LWM2M simple que implementa un dispositivo personalizado que consta de un sensor de temperatura y un interruptor de luz.</span><span class="sxs-lookup"><span data-stu-id="8b316-269">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="8b316-270">El dispositivo permite que un servidor lea el valor del sensor de temperatura y el estado booleano del interruptor de luz, así como encender y apagar dicho dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8b316-270">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
