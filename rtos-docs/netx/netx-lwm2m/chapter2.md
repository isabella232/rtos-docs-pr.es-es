---
title: 'Capítulo 2: Instalación y uso de LWM2M de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente LWM2M de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c13d3b092d3a5b59bd0369f6ffc162509d02590
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815186"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="fca07-103">Capítulo 2: Instalación y uso de LWM2M de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="fca07-103">Chapter 2 - Installation and use of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="fca07-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente LWM2M de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="fca07-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX LWM2M component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="fca07-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="fca07-105">Product Distribution</span></span>

<span data-ttu-id="fca07-106">LWM2M de NetX está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="fca07-106">NetX LWM2M is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="fca07-107">El paquete incluye tres archivos de código fuente, un archivo de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="fca07-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="fca07-108">**nx_lwm2m_client.h**: archivo de encabezado para el cliente NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="fca07-108">**nx_lwm2m_client.h**: Header file for the NetX LWM2M Client</span></span>

- <span data-ttu-id="fca07-109">**nx_lwm2m_\*.c/h**: archivos de código fuente de C/H para NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="fca07-109">**nx_lwm2m_\*.c/h**: C/H Source files for NetX LWM2M</span></span>

- <span data-ttu-id="fca07-110">**demo_netx_lwm2m_client.c**: archivo de código fuente C para la demostración de cliente NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="fca07-110">**demo_netx_lwm2m_client.c**: C Source file for NetX LWM2M Client Demo</span></span>

- <span data-ttu-id="fca07-111">**NetX_LWM2M_User_Guide.pdf**: descripción en PDF del producto NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="fca07-111">**NetX_LWM2M_User_Guide.pdf**: PDF description of NetX LWM2M product</span></span>

## <a name="netx-lwm2m-installation"></a><span data-ttu-id="fca07-112">Instalación de NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="fca07-112">NetX LWM2M Installation</span></span>

<span data-ttu-id="fca07-113">Para usar NetX LWM2M, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="fca07-113">In order to use NetX LWM2M, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="fca07-114">Por ejemplo, si NetX se ha instalado en el directorio " *\\threadx\\arm7\\green*", los archivos *nx_lwm2m&#42;.&#42;* deben copiarse en ese mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="fca07-114">For example, if NetX is installed in the directory "*\\threadx\\arm7\\green*" then the *nx_lwm2m&#42;.&#42;* files should be copied into this directory.</span></span>

## <a name="using-netx-lwm2m"></a><span data-ttu-id="fca07-115">Uso de NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="fca07-115">Using NetX LWM2M</span></span>

<span data-ttu-id="fca07-116">El uso de NetX LWM2M es fácil.</span><span class="sxs-lookup"><span data-stu-id="fca07-116">Using NetX LWM2M is easy.</span></span> <span data-ttu-id="fca07-117">Básicamente, el código de la aplicación debe incluir *nx_lwm2m_client.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX.</span><span class="sxs-lookup"><span data-stu-id="fca07-117">Basically, the application code must include *nx_lwm2m_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="fca07-118">Después de incluir *nx_lwm2m_client.h*, el código de la aplicación puede realizar las llamadas de función NetX LWM2M que se especifican más adelante en este manual.</span><span class="sxs-lookup"><span data-stu-id="fca07-118">Once *nx_lwm2m_client.h* is included, the application code is then able to make the NetX LWM2M function calls specified later in this guide.</span></span> <span data-ttu-id="fca07-119">La aplicación también debe importar los archivos *nx_lwm2m&#42;.&#42;* en la biblioteca de NetX.</span><span class="sxs-lookup"><span data-stu-id="fca07-119">The application must also import the *nx_lwm2m&#42;.&#42;* files into the NetX library.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="fca07-120">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="fca07-120">Configuration Options</span></span>

<span data-ttu-id="fca07-121">Hay varias opciones de configuración al compilar la biblioteca de cliente de LWM2M y la aplicación mediante el cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fca07-121">There are several configuration options when building the LWM2M Client library and the application using the LWM2M Client.</span></span> <span data-ttu-id="fca07-122">Las opciones de configuración pueden definirse en el origen de la aplicación, en la línea de comandos, a menos que se especifique lo contrario.</span><span class="sxs-lookup"><span data-stu-id="fca07-122">The configuration options can be defined in the application source, on the command line, unless otherwise specified.</span></span>

### <a name="nx_lwm2m_client_disable_error_checking"></a><span data-ttu-id="fca07-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span><span class="sxs-lookup"><span data-stu-id="fca07-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span></span>

<span data-ttu-id="fca07-124">Si se define, quita la API de comprobación de errores de cliente de LWM2M básica y mejora el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="fca07-124">Defined, removes the basic LWM2M Client error checking API and improves performance.</span></span> <span data-ttu-id="fca07-125">Los códigos de retorno de API no afectados al deshabilitar la comprobación de errores se muestran en negrita en la definición de la API.</span><span class="sxs-lookup"><span data-stu-id="fca07-125">API return codes not affected by disabling error checking are listed in bold typeface in the API definition.</span></span>

### <a name="nx_lwm2m_client_disable_float"></a><span data-ttu-id="fca07-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span><span class="sxs-lookup"><span data-stu-id="fca07-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span></span>

<span data-ttu-id="fca07-127">Si se define, quita la compatibilidad de los valores de números de punto flotante.</span><span class="sxs-lookup"><span data-stu-id="fca07-127">Defined, removes the support of floating point numbers values.</span></span> <span data-ttu-id="fca07-128">Cuando está deshabilitado, el cliente de LWM2M no admite recursos con el tipo de datos float.</span><span class="sxs-lookup"><span data-stu-id="fca07-128">When disabled the LWM2M Client cannot support Resources with Float data type.</span></span>

### <a name="nx_lwm2m_client_disable_float64"></a><span data-ttu-id="fca07-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span><span class="sxs-lookup"><span data-stu-id="fca07-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span></span>

<span data-ttu-id="fca07-130">Si se define, quita la compatibilidad de los valores de números de punto flotante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="fca07-130">Defined, removes the support of 64-bit floating point numbers values.</span></span> <span data-ttu-id="fca07-131">El cliente de LWM2M todavía puede recibir mensajes TLV que contienen números flotantes de 64 bits, pero los valores se convierten en un número de punto flotante de 32 bits para su procesamiento.</span><span class="sxs-lookup"><span data-stu-id="fca07-131">The LWM2M Client can still receive TLV messages containing 64-bit floating numbers, but the values are converted to 32-bit floating point for processing.</span></span>

### <a name="nx_lwm2m_client_priority"></a><span data-ttu-id="fca07-132">NX_LWM2M_CLIENT_PRIORITY</span><span class="sxs-lookup"><span data-stu-id="fca07-132">NX_LWM2M_CLIENT_PRIORITY</span></span>

<span data-ttu-id="fca07-133">Especifica la prioridad del subproceso del cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="fca07-133">Specifies the priority of the LWM2M Client thread.</span></span> <span data-ttu-id="fca07-134">De forma predeterminada, este valor se define como 16 para especificar la prioridad 16.</span><span class="sxs-lookup"><span data-stu-id="fca07-134">By default, this value is defined as 16 to specify priority 16.</span></span>

### <a name="nx_lwm2m_client_max_device_errors"></a><span data-ttu-id="fca07-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span><span class="sxs-lookup"><span data-stu-id="fca07-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span></span>

<span data-ttu-id="fca07-136">Especifica el número máximo de códigos de error almacenados por el objeto de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fca07-136">Specifies the maximum number of error codes stored by the Device Object.</span></span> <span data-ttu-id="fca07-137">El valor predeterminado es 8.</span><span class="sxs-lookup"><span data-stu-id="fca07-137">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_security_instances"></a><span data-ttu-id="fca07-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="fca07-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span></span>

<span data-ttu-id="fca07-139">Especifica el número máximo de instancias de objeto de seguridad.</span><span class="sxs-lookup"><span data-stu-id="fca07-139">Specifies the maximum number of Security Object Instances.</span></span> <span data-ttu-id="fca07-140">El valor predeterminado es 2 para admitir un servidor de arranque y un servidor estándar.</span><span class="sxs-lookup"><span data-stu-id="fca07-140">The default value is 2 for supporting a Bootstrap Server and a standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_instances"></a><span data-ttu-id="fca07-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="fca07-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span></span>

<span data-ttu-id="fca07-142">Especifica el número máximo de instancias de objeto de servidor.</span><span class="sxs-lookup"><span data-stu-id="fca07-142">Specifies the maximum number of Server Object Instances.</span></span> <span data-ttu-id="fca07-143">El valor predeterminado es 1 para admitir un solo servidor estándar.</span><span class="sxs-lookup"><span data-stu-id="fca07-143">The default value is 1 for supporting a single standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_uri"></a><span data-ttu-id="fca07-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span><span class="sxs-lookup"><span data-stu-id="fca07-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span></span>

<span data-ttu-id="fca07-145">Especifica la longitud máxima de un URI de servidor, incluido el carácter nulo de terminación.</span><span class="sxs-lookup"><span data-stu-id="fca07-145">Specifies the maximum length of a server URI, including terminating nil character.</span></span> <span data-ttu-id="fca07-146">El valor predeterminado es 128.</span><span class="sxs-lookup"><span data-stu-id="fca07-146">The default value is 128.</span></span>

### <a name="nx_lwm2m_client_max_access_control_instances"></a><span data-ttu-id="fca07-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="fca07-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span></span>

<span data-ttu-id="fca07-148">Especifica el número máximo de instancias de Access Control.</span><span class="sxs-lookup"><span data-stu-id="fca07-148">Specifies the maximum number of Access Control Instances.</span></span> <span data-ttu-id="fca07-149">El valor predeterminado es 0, que deshabilita el control de acceso.</span><span class="sxs-lookup"><span data-stu-id="fca07-149">The default value is 0, which disables access control.</span></span> <span data-ttu-id="fca07-150">Si la aplicación admite más de un servidor LWM2M, el número máximo de instancias de Access Control debe establecerse en el número máximo de instancias de objeto que admitirá el cliente LWM2M, ya que se debe crear una instancia de Access Control para cada instancia de objeto (excepto las instancias de objeto de seguridad).</span><span class="sxs-lookup"><span data-stu-id="fca07-150">If the application supports more than one LWM2M Server, the maximum number of Access Control Instances must be set to the maximum number of Object Instances that the LWM2M Client will support, as one Access Control Instance must be created for each Object Instance (except for the Security Object Instances).</span></span>

### <a name="nx_lwm2m_client_max_access_control_acls"></a><span data-ttu-id="fca07-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span><span class="sxs-lookup"><span data-stu-id="fca07-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span></span>

<span data-ttu-id="fca07-152">Especifica el número máximo de recursos de ACL por instancia de Access Control.</span><span class="sxs-lookup"><span data-stu-id="fca07-152">Specifies the maximum number of ACL resources per Access Control Instance.</span></span> <span data-ttu-id="fca07-153">El valor predeterminado es 4.</span><span class="sxs-lookup"><span data-stu-id="fca07-153">The default value is 4.</span></span>

### <a name="nx_lwm2m_client_max_notifications"></a><span data-ttu-id="fca07-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="fca07-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span></span>

<span data-ttu-id="fca07-155">Especifica el número máximo de notificaciones que el cliente de LWM2M admitirá.</span><span class="sxs-lookup"><span data-stu-id="fca07-155">Specifies the maximum number of notifications that the LWM2M Client will support.</span></span> <span data-ttu-id="fca07-156">Un servidor LWM2M puede establecer notificaciones en objetos, instancias de objeto y recursos.</span><span class="sxs-lookup"><span data-stu-id="fca07-156">A LWM2M Server can set notifications on Objects, Object Instances, and Resources.</span></span> <span data-ttu-id="fca07-157">El valor predeterminado es 8.</span><span class="sxs-lookup"><span data-stu-id="fca07-157">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_resources"></a><span data-ttu-id="fca07-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="fca07-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span></span>

<span data-ttu-id="fca07-159">Especifica el número máximo de recursos por objeto.</span><span class="sxs-lookup"><span data-stu-id="fca07-159">Specifies the maximum number of Resources per Object.</span></span> <span data-ttu-id="fca07-160">El valor predeterminado es 32.</span><span class="sxs-lookup"><span data-stu-id="fca07-160">The default value is 32.</span></span>

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a><span data-ttu-id="fca07-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span><span class="sxs-lookup"><span data-stu-id="fca07-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span></span>

<span data-ttu-id="fca07-162">Especifica el tiempo máximo de espera para las solicitudes del servidor de arranque cuando se inicia la sesión de arranque antes de anular la sesión.</span><span class="sxs-lookup"><span data-stu-id="fca07-162">Specifies the maximum time to wait for bootstrap server requests when the bootstrap session is initiated before aborting the session.</span></span> <span data-ttu-id="fca07-163">El valor predeterminado es de 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="fca07-163">The default value is 60 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_start_timeout"></a><span data-ttu-id="fca07-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fca07-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span></span>

<span data-ttu-id="fca07-165">Especifica el tiempo máximo de espera para la finalización del protocolo de enlace de DTLS.</span><span class="sxs-lookup"><span data-stu-id="fca07-165">Specifies the maximum time to wait for DTLS handshake completion.</span></span> <span data-ttu-id="fca07-166">El valor predeterminado es 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="fca07-166">The default value is 30 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_end_timeout"></a><span data-ttu-id="fca07-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fca07-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span></span>

<span data-ttu-id="fca07-168">Especifica el tiempo máximo de espera para que se complete el apagado de DTLS.</span><span class="sxs-lookup"><span data-stu-id="fca07-168">Specifies the maximum time to wait for DTLS shutdown completion.</span></span> <span data-ttu-id="fca07-169">El valor predeterminado es de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="fca07-169">The default value is 5 seconds.</span></span>
