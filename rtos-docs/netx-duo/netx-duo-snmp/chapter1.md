---
title: 'Capítulo 1: Introducción a SNMP de Azure RTOS NetX Duo'
description: La implementación de SNMP de NetX Duo es la de un agente de SNMP. Un agente es responsable de responder a los comandos del administrador de SNMP y enviar las capturas controladas por eventos.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814574"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a><span data-ttu-id="9ca59-104">Capítulo 1: Introducción a SNMP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-104">Chapter 1 - Introduction to Azure RTOS NetX Duo SNMP</span></span>

<span data-ttu-id="9ca59-105">El Protocolo simple de administración de redes (SNMP) es un protocolo diseñado para administrar dispositivos en Internet.</span><span class="sxs-lookup"><span data-stu-id="9ca59-105">The Simple Network Management Protocol (SNMP) is a protocol designed for managing devices on the internet.</span></span> <span data-ttu-id="9ca59-106">SNMP es un protocolo que emplea los servicios del Protocolo de datagramas de usuario (UDP) sin conexión para realizar su función de administración.</span><span class="sxs-lookup"><span data-stu-id="9ca59-106">SNMP is a protocol that utilizes the connectionless User Datagram Protocol (UDP) services to perform its management function.</span></span> <span data-ttu-id="9ca59-107">La implementación de SNMP de Azure RTOS NetX Duo es la de un agente de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-107">The Azure RTOS NetX Duo SNMP implementation is that of an SNMP Agent.</span></span> <span data-ttu-id="9ca59-108">Un agente es responsable de responder a los comandos del administrador de SNMP y enviar las capturas controladas por eventos.</span><span class="sxs-lookup"><span data-stu-id="9ca59-108">An agent is responsible for responding to SNMP Manager’s commands and sending event driven traps.</span></span> 

<span data-ttu-id="9ca59-109">SNMP de NetX Duo admite la comunicación IPv4 e IPv6 con los administradores de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-109">NetX Duo SNMP supports both IPv4 and IPv6 communication with SNMP Managers.</span></span> <span data-ttu-id="9ca59-110">Las aplicaciones SNMP de NetX deben compilarse y ejecutarse en el protocolo SNMP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9ca59-110">NetX SNMP applications should compile and run in NetX Duo SNMP.</span></span> <span data-ttu-id="9ca59-111">Sin embargo, se recomienda que el desarrollador porte las aplicaciones SNMP existentes para usar los servicios equivalentes "Duo".</span><span class="sxs-lookup"><span data-stu-id="9ca59-111">However, the developer is encouraged to port existing SNMP applications to using the equivalent “duo” services.</span></span> <span data-ttu-id="9ca59-112">Por ejemplo, al enviar mensajes de captura de SNMP, los siguientes servicios "Duo" deben reemplazar su equivalente de NetX:</span><span class="sxs-lookup"><span data-stu-id="9ca59-112">For example, when sending SNMP trap messages, the following ‘duo’ services should replace their NetX equivalent:</span></span>

<span data-ttu-id="9ca59-113">*nxd_snmp_object_trap_send*</span><span class="sxs-lookup"><span data-stu-id="9ca59-113">*nxd_snmp_object_trap_send*</span></span>

<span data-ttu-id="9ca59-114">*nxd_snmp_object_trapv2_send*</span><span class="sxs-lookup"><span data-stu-id="9ca59-114">*nxd_snmp_object_trapv2_send*</span></span>

<span data-ttu-id="9ca59-115">*nxd_snmp_object_trapv3_send*</span><span class="sxs-lookup"><span data-stu-id="9ca59-115">*nxd_snmp_object_trapv3_send*</span></span>

<span data-ttu-id="9ca59-116">Para obtener más información, consulte el capítulo **Descripción de los servicios del agente SNMP** de este manual del usuario.</span><span class="sxs-lookup"><span data-stu-id="9ca59-116">For more details, see **Description of SNMP Agent Services** elsewhere in this User Guide for more details.</span></span>

## <a name="netx-duo-snmp-agent-requirements"></a><span data-ttu-id="9ca59-117">Requisitos del agente de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-117">NetX Duo SNMP Agent Requirements</span></span>

<span data-ttu-id="9ca59-118">El paquete de SNMP de NetX Duo requiere que ya se haya creado una instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-118">The NetX Duo SNMP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="9ca59-119">Además, UDP debe estar habilitado en la misma instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-119">In addition, UDP must be enabled on that same IP instance.</span></span>

<span data-ttu-id="9ca59-120">El agente de SNMP de NetX Duo tiene varios requisitos adicionales.</span><span class="sxs-lookup"><span data-stu-id="9ca59-120">The NetX Duo SNMP Agent has several additional requirements.</span></span> <span data-ttu-id="9ca59-121">En primer lugar, requiere acceso al puerto 161 para controlar todas las solicitudes del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-121">First, it requires access to port 161 for handling all SNMP manager requests.</span></span> <span data-ttu-id="9ca59-122">También requiere acceso al puerto 162 para enviar mensajes de captura al administrador.</span><span class="sxs-lookup"><span data-stu-id="9ca59-122">It also requires access to port 162 for sending trap messages to the Manager.</span></span>

<span data-ttu-id="9ca59-123">Para usar el agente de SNMP de NetX Duo a través de IPv6 y obtener objetos IPv6, IPv6 debe estar habilitado en NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9ca59-123">To use NetX Duo SNMP Agent with over IPv6 and to obtain IPv6 objects, IPv6 must be enabled in NetX Duo.</span></span> <span data-ttu-id="9ca59-124">Consulte la ***guía del usuario de NetX Duo*** para obtener más detalles sobre cómo habilitar la instancia de IP para servicios IPv6.</span><span class="sxs-lookup"><span data-stu-id="9ca59-124">See the ***NetX Duo User Guide*** for details on enabling the IP instance for IPv6 services.</span></span>

## <a name="netx-duo-snmp-constraints"></a><span data-ttu-id="9ca59-125">Restricciones de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-125">NetX Duo SNMP Constraints</span></span>

<span data-ttu-id="9ca59-126">El protocolo SNMP de NetX Duo implementa las versiones 1, 2 y 3 de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-126">The NetX Duo SNMP protocol implements SNMP Version 1, 2, and 3.</span></span> <span data-ttu-id="9ca59-127">La implementación de SNMPv3 admite la autenticación MD5 y SHA y el cifrado DES.</span><span class="sxs-lookup"><span data-stu-id="9ca59-127">The SNMPv3 implementation supports MD5 and SHA authentication, and DES encryption.</span></span> <span data-ttu-id="9ca59-128">Esta versión del agente de SNMP de NetX Duo tiene las siguientes restricciones:</span><span class="sxs-lookup"><span data-stu-id="9ca59-128">This version of the NetX Duo SNMP Agent has the following constraints:</span></span>

1. <span data-ttu-id="9ca59-129">Debe haber un agente de SNMP por instancia de IP de NetX.</span><span class="sxs-lookup"><span data-stu-id="9ca59-129">One SNMP Agent per NetX IP Instance</span></span>
2. <span data-ttu-id="9ca59-130">No se admite RMON.</span><span class="sxs-lookup"><span data-stu-id="9ca59-130">No support for RMON</span></span>
3. <span data-ttu-id="9ca59-131">No se admiten los mensajes informativos de SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="9ca59-131">SNMP v3 Inform messages are not supported</span></span>
4. <span data-ttu-id="9ca59-132">No se admiten los tipos de datos OPAQUE y NSAP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-132">OPAQUE and NSAP data types are not supported</span></span>
5. <span data-ttu-id="9ca59-133">Las direcciones IPv6 se definen como cadenas de octetos, y la aplicación se encarga de la comprobación de formato.</span><span class="sxs-lookup"><span data-stu-id="9ca59-133">IPv6 addresses are defined as octet strings, and format checking is left to the application.</span></span>

## <a name="snmp-object-names"></a><span data-ttu-id="9ca59-134">Nombres de objeto de SNMP</span><span class="sxs-lookup"><span data-stu-id="9ca59-134">SNMP Object Names</span></span>

<span data-ttu-id="9ca59-135">El protocolo SNMP está diseñado para administrar dispositivos en Internet.</span><span class="sxs-lookup"><span data-stu-id="9ca59-135">The SNMP protocol is designed to manage devices on the internet.</span></span> <span data-ttu-id="9ca59-136">Para ello, cada dispositivo administrado de SNMP tiene un conjunto de objetos definidos por la estructura de información de administración (SMI), tal y como se especifica en el protocolo RFC 1155.</span><span class="sxs-lookup"><span data-stu-id="9ca59-136">To accomplish this, each SNMP managed device has a set of objects that are defined by the Structure of Management Information (SMI) as defined by RFC 1155.</span></span> <span data-ttu-id="9ca59-137">La estructura es un tipo de árbol jerárquico con una estructura similar a la siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ca59-137">The structure is a hierarchical tree type of structure that looks like the following:</span></span>

![Diagrama de la estructura de la información de administración.](media/image3.png)

<span data-ttu-id="9ca59-139">Cada nodo del árbol es un objeto.</span><span class="sxs-lookup"><span data-stu-id="9ca59-139">Each node in the tree is an object.</span></span> <span data-ttu-id="9ca59-140">El objeto "dod" del árbol se identifica mediante la notación 1.3.6, mientras que el objeto "Internet" del árbol se identifica mediante la notación 1.3.6.1.</span><span class="sxs-lookup"><span data-stu-id="9ca59-140">The “dod” object in the tree is identified by the notation 1.3.6, while the “internet” object in the tree is identified by the notation 1.3.6.1.</span></span> <span data-ttu-id="9ca59-141">Todos los nombres de objeto de SNMP comienzan con la notación 1.3.6.</span><span class="sxs-lookup"><span data-stu-id="9ca59-141">All SNMP object names begin with the notation 1.3.6.</span></span>

<span data-ttu-id="9ca59-142">Un administrador de SNMP usa esta notación de objeto para especificar qué objeto del dispositivo quiere obtener o establecer.</span><span class="sxs-lookup"><span data-stu-id="9ca59-142">An SNMP Manager uses this object notation to specify what object in the device it wishes to get or set.</span></span> <span data-ttu-id="9ca59-143">El agente de SNMP de NetX Duo interpreta dichas solicitudes del administrador y proporciona mecanismos para que la aplicación realice la operación solicitada.</span><span class="sxs-lookup"><span data-stu-id="9ca59-143">The NetX Duo SNMP Agent interprets such manager requests and provides mechanisms for the application to perform the requested operation.</span></span>

## <a name="snmp-manager-requests"></a><span data-ttu-id="9ca59-144">Solicitudes del administrador del SNMP</span><span class="sxs-lookup"><span data-stu-id="9ca59-144">SNMP Manager Requests</span></span>

<span data-ttu-id="9ca59-145">SNMP tiene un mecanismo sencillo para administrar dispositivos.</span><span class="sxs-lookup"><span data-stu-id="9ca59-145">The SNMP has a simple mechanism for managing devices.</span></span> <span data-ttu-id="9ca59-146">Existe un conjunto de comandos de SNMP estándar que emite el administrador de SNMP para el dispositivo de SNMP en el *puerto 161*.</span><span class="sxs-lookup"><span data-stu-id="9ca59-146">There is a set of standard SNMP commands that are issued by the SNMP Manager to the SNMP device on *port 161*.</span></span> <span data-ttu-id="9ca59-147">A continuación, se muestran algunos de los comandos básicos del administrador de SNMP:</span><span class="sxs-lookup"><span data-stu-id="9ca59-147">The following shows some of the basic SNMP Manager commands:</span></span>

| <span data-ttu-id="9ca59-148">Comando de SNMP</span><span class="sxs-lookup"><span data-stu-id="9ca59-148">SNMP Command</span></span> | <span data-ttu-id="9ca59-149">Significado</span><span class="sxs-lookup"><span data-stu-id="9ca59-149">Meaning</span></span>                                                        |
|--------------|----------------------------------------------------------------|
| <span data-ttu-id="9ca59-150">GET</span><span class="sxs-lookup"><span data-stu-id="9ca59-150">GET</span></span>          | <span data-ttu-id="9ca59-151">*Obtiene el objeto especificado.*</span><span class="sxs-lookup"><span data-stu-id="9ca59-151">*Get the specified object*</span></span>                                       |
| <span data-ttu-id="9ca59-152">GETNEXT</span><span class="sxs-lookup"><span data-stu-id="9ca59-152">GETNEXT</span></span>      | <span data-ttu-id="9ca59-153">*Obtiene el siguiente objeto lógico después del identificador de objeto especificado.*</span><span class="sxs-lookup"><span data-stu-id="9ca59-153">*Get the next logical object after the specified object ID*</span></span>      |
| <span data-ttu-id="9ca59-154">GETBULK</span><span class="sxs-lookup"><span data-stu-id="9ca59-154">GETBULK</span></span>      | <span data-ttu-id="9ca59-155">*Obtiene varios objetos lógicos después del identificador de objeto especificado.*</span><span class="sxs-lookup"><span data-stu-id="9ca59-155">*Get the multiple logical objects after the specified object ID*</span></span> |
| <span data-ttu-id="9ca59-156">SET</span><span class="sxs-lookup"><span data-stu-id="9ca59-156">SET</span></span>          | <span data-ttu-id="9ca59-157">*Establece el objeto especificado.*</span><span class="sxs-lookup"><span data-stu-id="9ca59-157">*Set the specified object*</span></span>                                       |

<span data-ttu-id="9ca59-158">Estos comandos se codifican en el formato de notación de sintaxis abstracta uno (ASN.1) y residen en la carga del paquete UDP enviado por el administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-158">These commands are encoded in the Abstract Syntax Notation One (ASN.1) format and reside in the payload of the UDP packet sent by the SNMP Manager.</span></span> <span data-ttu-id="9ca59-159">El agente de SNMP de NetX Duo procesa la solicitud y, a continuación, llama a la rutina de control correspondiente especificada en la llamada ***nx_snmp_agent_create***.</span><span class="sxs-lookup"><span data-stu-id="9ca59-159">The NetX Duo SNMP Agent processes the request and then calls the corresponding handling routine specified in the ***nx_snmp_agent_create*** call.</span></span>

## <a name="netx-duo-snmp-agent-traps"></a><span data-ttu-id="9ca59-160">Capturas del agente de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-160">NetX Duo SNMP Agent Traps</span></span>

<span data-ttu-id="9ca59-161">El agente de SNMP de NetX Duo proporciona la capacidad de alertar también a un administrador de SNMP de eventos de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="9ca59-161">The NetX Duo SNMP Agent provides the ability to also alert an SNMP Manager of events asynchronously.</span></span> <span data-ttu-id="9ca59-162">Esto se hace a través de un comando de captura de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-162">This is done via an SNMP trap command.</span></span> <span data-ttu-id="9ca59-163">Existe una API única para cada versión de SNMP para enviar capturas a un administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-163">There is a unique API for each version of SNMP for sending traps to an SNMP Manager.</span></span> <span data-ttu-id="9ca59-164">De forma predeterminada, las capturas se envían al administrador de SNMP en el puerto 162.</span><span class="sxs-lookup"><span data-stu-id="9ca59-164">By default, the traps are sent to the SNMP Manager on port 162.</span></span>

<span data-ttu-id="9ca59-165">El agente de SNMP de NetX Duo proporciona claves de seguridad independientes para los mensajes de captura de SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="9ca59-165">The NetX Duo SNMP Agent provides separate security keys for SNMPv3 trap messages.</span></span> <span data-ttu-id="9ca59-166">Para ello, la aplicación SNMP debe crear un conjunto de claves distinto de las que se aplican a las respuestas a las solicitudes del administrador.</span><span class="sxs-lookup"><span data-stu-id="9ca59-166">To do so, the SNMP application must create a separate set of keys from those applied to responses to Manager requests.</span></span> <span data-ttu-id="9ca59-167">La seguridad de captura permite al agente de SNMP utilizar contraseñas iguales o distintas para la autenticación y la privacidad.</span><span class="sxs-lookup"><span data-stu-id="9ca59-167">Trap security enables the SNMP Agent to use the same or different passwords for authentication and privacy.</span></span> <span data-ttu-id="9ca59-168">Para obtener más información acerca de la creación de claves de seguridad, consulte el apartado **Cifrado y autenticación de SNMP de NetX Duo** en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="9ca59-168">For more information on creating security keys, see **NetX Duo SNMP Authentication and Encryption** in the next section.</span></span>

<span data-ttu-id="9ca59-169">En la parte superior del archivo *nxd_snmp.h* se enumera una lista de variables de captura de SNMP estándar:</span><span class="sxs-lookup"><span data-stu-id="9ca59-169">A list of standard SNMP trap variables is enumerated at the top of *nxd_snmp.h:*</span></span>

| <span data-ttu-id="9ca59-170">Variables</span><span class="sxs-lookup"><span data-stu-id="9ca59-170">Variables</span></span>                                 | <span data-ttu-id="9ca59-171">Value</span><span class="sxs-lookup"><span data-stu-id="9ca59-171">Value</span></span>  |
|-------------------------------------------|---|
| <span data-ttu-id="9ca59-172">#define NX_SNMP_TRAP_COLDSTART</span><span class="sxs-lookup"><span data-stu-id="9ca59-172">#define NX_SNMP_TRAP_COLDSTART</span></span>            | <span data-ttu-id="9ca59-173">0</span><span class="sxs-lookup"><span data-stu-id="9ca59-173">0</span></span> |
| <span data-ttu-id="9ca59-174">#define NX_SNMP_TRAP_WARMSTART</span><span class="sxs-lookup"><span data-stu-id="9ca59-174">#define NX_SNMP_TRAP_WARMSTART</span></span>            | <span data-ttu-id="9ca59-175">1</span><span class="sxs-lookup"><span data-stu-id="9ca59-175">1</span></span> |
| <span data-ttu-id="9ca59-176">#define NX_SNMP_TRAP_LINKDOWN</span><span class="sxs-lookup"><span data-stu-id="9ca59-176">#define NX_SNMP_TRAP_LINKDOWN</span></span>             | <span data-ttu-id="9ca59-177">2</span><span class="sxs-lookup"><span data-stu-id="9ca59-177">2</span></span> |
| <span data-ttu-id="9ca59-178">#define NX_SNMP_TRAP_LINKUP</span><span class="sxs-lookup"><span data-stu-id="9ca59-178">#define NX_SNMP_TRAP_LINKUP</span></span>               | <span data-ttu-id="9ca59-179">3</span><span class="sxs-lookup"><span data-stu-id="9ca59-179">3</span></span> |
| <span data-ttu-id="9ca59-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span><span class="sxs-lookup"><span data-stu-id="9ca59-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span></span> | <span data-ttu-id="9ca59-181">4</span><span class="sxs-lookup"><span data-stu-id="9ca59-181">4</span></span> |
| <span data-ttu-id="9ca59-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span><span class="sxs-lookup"><span data-stu-id="9ca59-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span></span>      | <span data-ttu-id="9ca59-183">5</span><span class="sxs-lookup"><span data-stu-id="9ca59-183">5</span></span> |
| <span data-ttu-id="9ca59-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span><span class="sxs-lookup"><span data-stu-id="9ca59-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span></span>   | <span data-ttu-id="9ca59-185">6</span><span class="sxs-lookup"><span data-stu-id="9ca59-185">6</span></span> |

<span data-ttu-id="9ca59-186">Para incluir estas variables en el mensaje de captura, el argumento de entrada trap_type en *nx_snmp_agent_trapv2_send* (SNMPv2) o *nx_snmp_agent_trapv3_send* (SNMPv3) se establece en el valor enumerado de estas variables.</span><span class="sxs-lookup"><span data-stu-id="9ca59-186">To include these variables in the trap message, the trap_type input argument in *nx_snmp_agent_trapv2_send* (SNMPv2) or *nx_snmp_agent_trapv3_send* (SNMPv3) is set to the enumerated value of these variables.</span></span> <span data-ttu-id="9ca59-187">A continuación, se muestra un ejemplo para que SNMPv2 notifique al administrador de SNMP un evento de inicio en frío:</span><span class="sxs-lookup"><span data-stu-id="9ca59-187">An example is shown below for SNMPv2 to notify the SNMP Manager of a cold start event:</span></span>

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

<span data-ttu-id="9ca59-188">Para incluir variables de propiedad en el mensaje de captura, el argumento de entrada trap_type se establece en NX_SNMP_TRAP_CUSTOM y el argumento de entrada de la lista de capturas contiene los datos de propiedad.</span><span class="sxs-lookup"><span data-stu-id="9ca59-188">To include proprietary variables in the trap message, the trap_type input argument is set to NX_SNMP_TRAP_CUSTOM and the trap list input argument contains the proprietary data.</span></span> <span data-ttu-id="9ca59-189">Tenga en cuenta que el mensaje de captura contendrá el tiempo de actividad del sistema (1.3.6.1.6.3.1.1.4.1.0).</span><span class="sxs-lookup"><span data-stu-id="9ca59-189">Note that the trap message will contain as the system up time (1.3.6.1.6.3.1.1.4.1.0).</span></span> <span data-ttu-id="9ca59-190">A continuación se muestra un ejemplo para SNMPv2:</span><span class="sxs-lookup"><span data-stu-id="9ca59-190">An example is shown below for SNMPv2:</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a><span data-ttu-id="9ca59-191">Autenticación y cifrado de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-191">NetX Duo SNMP Authentication and Encryption</span></span>

<span data-ttu-id="9ca59-192">Existen dos tipos de autenticación: *básica* e *implícita*.</span><span class="sxs-lookup"><span data-stu-id="9ca59-192">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="9ca59-193">La autenticación básica equivale al *nombre de usuario* simple de texto sin formato que se encuentra en muchos protocolos.</span><span class="sxs-lookup"><span data-stu-id="9ca59-193">Basic authentication is equivalent to a simple plain text *username* authentication found in many protocols.</span></span> <span data-ttu-id="9ca59-194">En la autenticación SNMP básica, el usuario simplemente verifica que el nombre de usuario proporcionado es válido para realizar operaciones SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-194">In SNMP basic authentication, the user simply verifies that the supplied username is valid for performing SNMP operations.</span></span> <span data-ttu-id="9ca59-195">La autenticación básica es la única opción para las versiones 1 y 2 de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-195">Basic authentication is the only option for SNMP versions 1 and 2.</span></span>

<span data-ttu-id="9ca59-196">La principal desventaja de la autenticación básica es que el nombre de usuario se transmite en texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="9ca59-196">The main disadvantage of basic authentication is the username is transmitted in plain text.</span></span> <span data-ttu-id="9ca59-197">La autenticación implícita SNMPv3 soluciona este problema, ya que no transmite nunca el nombre de usuario en texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="9ca59-197">The SNMPv3 digest authentication addresses this problem by never transmitting the username in plain text.</span></span> <span data-ttu-id="9ca59-198">En su lugar, se utiliza un algoritmo para derivar un hash de 96 bits del nombre de usuario, el motor de contexto y otra información.</span><span class="sxs-lookup"><span data-stu-id="9ca59-198">Instead, an algorithm is used to derive a 96-bit ‘digest’ from the username, context engine, and other information.</span></span> <span data-ttu-id="9ca59-199">El agente de SNMP de NetX Duo admite los algoritmos hash MD5 y SHA.</span><span class="sxs-lookup"><span data-stu-id="9ca59-199">The NetX Duo SNMP Agent supports both MD5 and SHA digest algorithms.</span></span>

<span data-ttu-id="9ca59-200">Para habilitar la autenticación, el agente de SNMP debe establecer su identificador de motor de contexto mediante el servicio *nx_snmp_agent_context_engine_set*.</span><span class="sxs-lookup"><span data-stu-id="9ca59-200">To enable authentication, the SNMP Agent must set its Context Engine ID using the *nx_snmp_agent_context_engine_set* service.</span></span> <span data-ttu-id="9ca59-201">El identificador del motor de contexto se usa en la creación de la clave de autenticación.</span><span class="sxs-lookup"><span data-stu-id="9ca59-201">The Context Engine ID is used in the creation of the authentication key.</span></span>

<span data-ttu-id="9ca59-202">El cifrado de datos SNMPv3 está disponible mediante el algoritmo DES.</span><span class="sxs-lookup"><span data-stu-id="9ca59-202">Encryption of SNMPv3 data is available using the DES algorithm.</span></span> <span data-ttu-id="9ca59-203">El cifrado requiere que se habilite la autenticación (no se pueden cifrar los datos sin establecer los parámetros de autenticación).</span><span class="sxs-lookup"><span data-stu-id="9ca59-203">Encryption requires that authentication be enabled (one cannot encrypt data without setting the authentication parameters).</span></span>

<span data-ttu-id="9ca59-204">Para crear claves de privacidad y autenticación, se usa la siguiente API:</span><span class="sxs-lookup"><span data-stu-id="9ca59-204">To create authentication and privacy keys, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

<span data-ttu-id="9ca59-205">A continuación, el agente de SNMP se debe configurar para usar estas claves.</span><span class="sxs-lookup"><span data-stu-id="9ca59-205">Next, the SNMP agent must be configured to use these keys.</span></span> <span data-ttu-id="9ca59-206">Para registrar una clave con el agente de SNMP, se usa la siguiente API:</span><span class="sxs-lookup"><span data-stu-id="9ca59-206">To register a key with the SNMP agent, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="9ca59-207">Se pueden crear claves independientes para los mensajes de captura.</span><span class="sxs-lookup"><span data-stu-id="9ca59-207">Separate keys can be created for trap messages.</span></span> <span data-ttu-id="9ca59-208">Para aplicar claves para mensajes de captura, hay disponibles las siguientes API:</span><span class="sxs-lookup"><span data-stu-id="9ca59-208">To apply keys for trap messages the following API are available:</span></span>

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="9ca59-209">Para deshabilitar la autenticación o el cifrado de los mensajes de respuesta y enviar capturas, use estos servicios con la entrada de puntero de clave establecida en NULL.</span><span class="sxs-lookup"><span data-stu-id="9ca59-209">To disable authentication or encryption for response messages and sending traps, use these services with the key pointer input set to NULL.</span></span>

## <a name="netx-duo-snmp-community-strings"></a><span data-ttu-id="9ca59-210">Cadenas de comunidad de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-210">NetX Duo SNMP Community Strings</span></span>

<span data-ttu-id="9ca59-211">El agente de SNMP de NetX Duo admite cadenas de comunidad públicas y privadas.</span><span class="sxs-lookup"><span data-stu-id="9ca59-211">The NetX Duo SNMP Agent supports both public and private community strings.</span></span> <span data-ttu-id="9ca59-212">La cadena pública se establece con el servicio *nx_snmp_agent _public_string_set*.</span><span class="sxs-lookup"><span data-stu-id="9ca59-212">The public string is set with the *nx_snmp_agent _public_string_set* service.</span></span> <span data-ttu-id="9ca59-213">La cadena privada del agente de SNMP de NetX Duo se establece mediante el servicio *nx_snmp_agent_private_string_set*.</span><span class="sxs-lookup"><span data-stu-id="9ca59-213">The NetX Duo SNMP Agent private string is set using the *nx_snmp_agent_private_string_set* service.</span></span>

## <a name="netx-duo-snmp-username-callback"></a><span data-ttu-id="9ca59-214">Devolución de llamada de nombre de usuario SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-214">NetX Duo SNMP Username Callback</span></span>

<span data-ttu-id="9ca59-215">El paquete del agente de SNMP de NetX Duo permite que la aplicación especifique (a través de la llamada ***nx_snmp_agent_create***) una devolución de llamada de nombre de usuario a la que se llama cuando se empieza a administrar cada solicitud de cliente SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-215">The NetX Duo SNMP Agent package allows the application to specify (via the ***nx_snmp_agent_create*** call) a username callback  that is called at the beginning of handling each SNMP Client request.</span></span>

<span data-ttu-id="9ca59-216">La rutina de devolución de llamada proporciona el nombre de usuario al agente de SNMP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="9ca59-216">The callback routine provides the NetX Duo SNMP Agent with the username.</span></span> <span data-ttu-id="9ca59-217">Si el nombre de usuario proporcionado es válido o si no se necesita ninguna comprobación de nombre de usuario para responder a la solicitud, la devolución de llamada del nombre de usuario debe devolver el valor **NX_SUCCESS**.</span><span class="sxs-lookup"><span data-stu-id="9ca59-217">If the supplied username is valid or if no username check is necessary for the responding to the request, the username callback should return the value of **NX_SUCCESS**.</span></span> <span data-ttu-id="9ca59-218">De lo contrario, la rutina debe devolver **NX_SNMP_ERROR** para indicar que el nombre de usuario especificado no es válido.</span><span class="sxs-lookup"><span data-stu-id="9ca59-218">Otherwise, the routine should return **NX_SNMP_ERROR** to indicate the specified username is invalid.</span></span>

<span data-ttu-id="9ca59-219">El formato de la rutina de devolución de llamada del nombre de usuario de la aplicación se define a continuación:</span><span class="sxs-lookup"><span data-stu-id="9ca59-219">The format of the application username callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

<span data-ttu-id="9ca59-220">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ca59-220">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="9ca59-221">Parámetro</span><span class="sxs-lookup"><span data-stu-id="9ca59-221">Parameter</span></span> | <span data-ttu-id="9ca59-222">Significado</span><span class="sxs-lookup"><span data-stu-id="9ca59-222">Meaning</span></span>                                              |
|-----------|------------------------------------------------------|
| <span data-ttu-id="9ca59-223">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="9ca59-223">*agent_ptr*</span></span> | <span data-ttu-id="9ca59-224">Puntero al agente de SNMP que realiza la llamada</span><span class="sxs-lookup"><span data-stu-id="9ca59-224">Pointer to calling SNMP agent</span></span>                        |
| <span data-ttu-id="9ca59-225">username</span><span class="sxs-lookup"><span data-stu-id="9ca59-225">username</span></span>  | <span data-ttu-id="9ca59-226">Destino del puntero al nombre de usuario solicitado</span><span class="sxs-lookup"><span data-stu-id="9ca59-226">Destination for the pointer to the required username</span></span> |

<span data-ttu-id="9ca59-227">En el caso de las sesiones SNMPv1 y SNMPv2/v2C, la aplicación deberá examinar la cadena de comunidad en una solicitud de SNMP entrante para determinar si la solicitud de SNMP tiene una cadena de comunidad válida.</span><span class="sxs-lookup"><span data-stu-id="9ca59-227">For SNMPv1 and SNMPv2/v2C sessions, the application will want to examine the community string on an incoming SNMP request to determine if the SNMP request has a valid community string.</span></span> <span data-ttu-id="9ca59-228">Hay varios servicios que puede usar la aplicación SNMP para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="9ca59-228">There are several services for the SNMP application to do this.</span></span>

<span data-ttu-id="9ca59-229">La aplicación SNMP puede consultar si la solicitud actual del administrador de SNMP es de tipo GET (por ejemplo, GET, GETNEXT o GETBULK) o SET en la solicitud mediante este servicio:</span><span class="sxs-lookup"><span data-stu-id="9ca59-229">The SNMP application can inquire if the current SNMP Manager request is a GET (e.g. GET, GETNEXT, or GETBULK) or SET type of request using this service:</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

<span data-ttu-id="9ca59-230">Si la solicitud es de tipo GET, la aplicación comparará la cadena de la comunidad de entrada con la cadena pública del agente de SNMP:</span><span class="sxs-lookup"><span data-stu-id="9ca59-230">If the request is a GET type, the application will want to compare the input community string to the SNMP Agent’s public string:</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

<span data-ttu-id="9ca59-231">De igual manera, si la solicitud es de tipo SET, la aplicación querrá comparar la cadena de comunidad de entrada con la cadena privada del agente de SNMP:</span><span class="sxs-lookup"><span data-stu-id="9ca59-231">Similarly if the request is a SET type, the application will want to compare the input community string to the SNMP Agent’s private string:</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

<span data-ttu-id="9ca59-232">Los valores devueltos is_public e is_private indican respectivamente si la cadena de comunidad de entrada es una cadena de comunidad privada o pública válida.</span><span class="sxs-lookup"><span data-stu-id="9ca59-232">The is_public and is_private return values indicate respectively if the input community string is a valid public or private community string.</span></span>

<span data-ttu-id="9ca59-233">El valor devuelto de la rutina de devolución de llamada de nombre de usuario indica si el nombre de usuario es válido.</span><span class="sxs-lookup"><span data-stu-id="9ca59-233">The return value of the username callback routine indicates if the username is valid.</span></span> <span data-ttu-id="9ca59-234">Se devuelve el valor **NX_SUCCESS** si el nombre de usuario es válido o **NX_SNMP_ERROR** si no lo es.</span><span class="sxs-lookup"><span data-stu-id="9ca59-234">The value **NX_SUCCESS** is returned if the username is valid, or **NX_SNMP_ERROR** if the username is invalid.</span></span>

## <a name="netx-duo-snmp-agent-get-callback"></a><span data-ttu-id="9ca59-235">Devolución de llamada GET del agente de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-235">NetX Duo SNMP Agent GET Callback</span></span>

<span data-ttu-id="9ca59-236">La aplicación debe establecer una rutina de devolución de llamada para controlar las solicitudes del objeto GET del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-236">The application must set a callback routine for handling GET object requests from the SNMP Manager.</span></span> <span data-ttu-id="9ca59-237">La devolución de llamada recupera el valor del objeto especificado en la solicitud.</span><span class="sxs-lookup"><span data-stu-id="9ca59-237">The callback retrieves the value of the object specified in the request.</span></span>

<span data-ttu-id="9ca59-238">La rutina de devolución de llamada de la solicitud GET de la aplicación se define a continuación:</span><span class="sxs-lookup"><span data-stu-id="9ca59-238">The application GET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="9ca59-239">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ca59-239">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="9ca59-240">Parámetro</span><span class="sxs-lookup"><span data-stu-id="9ca59-240">Parameter</span></span>        | <span data-ttu-id="9ca59-241">Significado</span><span class="sxs-lookup"><span data-stu-id="9ca59-241">Meaning</span></span> |
|------------------|----------------------------------|
| <span data-ttu-id="9ca59-242">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="9ca59-242">*agent_ptr*</span></span>        | <span data-ttu-id="9ca59-243">Puntero al agente de SNMP que realiza la llamada</span><span class="sxs-lookup"><span data-stu-id="9ca59-243">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="9ca59-244">object_requested</span><span class="sxs-lookup"><span data-stu-id="9ca59-244">object_requested</span></span> | <span data-ttu-id="9ca59-245">Cadena ASCII que representa el identificador de objeto para el que se realiza la operación GET.</span><span class="sxs-lookup"><span data-stu-id="9ca59-245">ASCII string representing the object ID the GET operation is for.</span></span> |
| <span data-ttu-id="9ca59-246">object_data</span><span class="sxs-lookup"><span data-stu-id="9ca59-246">object_data</span></span>      | <span data-ttu-id="9ca59-247">Estructura de datos que contiene el valor recuperado por la devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="9ca59-247">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="9ca59-248">Se puede establecer con una serie de API SNMP de NetX Duo que se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="9ca59-248">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

> [!NOTE]
> <span data-ttu-id="9ca59-249">*En el caso de las cadenas de octeto, el objeto debe tener asignada la longitud para que la función interna la conozca, ya que la devolución de llamada no tiene ningún argumento de longitud:*</span><span class="sxs-lookup"><span data-stu-id="9ca59-249">*For octet strings, the object must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:*</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="9ca59-250">Dado que la devolución de llamada GET no conoce el tipo de datos, no es necesario comprobarlo.</span><span class="sxs-lookup"><span data-stu-id="9ca59-250">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="9ca59-251">La longitud no tendrá ningún efecto en las cadenas o tipos numéricos que estén delimitados con valores NULL.</span><span class="sxs-lookup"><span data-stu-id="9ca59-251">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="9ca59-252">A continuación, llame a la función interna:</span><span class="sxs-lookup"><span data-stu-id="9ca59-252">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="9ca59-253">Si la función de devolución de llamada no encuentra el objeto solicitado, se debe devolver el código de error **NX_SNMP_ERROR_NOSUCHNAME**.</span><span class="sxs-lookup"><span data-stu-id="9ca59-253">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="9ca59-254">Si se detecta algún otro error, se debe devolver el código **NX_SNMP_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="9ca59-254">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-getnext-callback"></a><span data-ttu-id="9ca59-255">Devolución de llamada GETNEXT del agente de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-255">NetX Duo SNMP Agent GETNEXT Callback</span></span>

<span data-ttu-id="9ca59-256">La aplicación también debe establecer la rutina de devolución de llamada para las solicitudes del objeto GETNEXT desde el administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-256">The application must also set the callback routine for GETNEXT object requests from the SNMP Manager.</span></span> <span data-ttu-id="9ca59-257">La devolución de llamada GETNEXT recupera el valor del siguiente objeto especificado por la solicitud.</span><span class="sxs-lookup"><span data-stu-id="9ca59-257">The GETNEXT callback retrieves the value of the next object specified by the request.</span></span>

<span data-ttu-id="9ca59-258">La rutina de devolución de llamada de la solicitud GETNEXT de la aplicación se define a continuación:</span><span class="sxs-lookup"><span data-stu-id="9ca59-258">The application GETNEXT request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="9ca59-259">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ca59-259">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="9ca59-260">Parámetro</span><span class="sxs-lookup"><span data-stu-id="9ca59-260">Parameter</span></span>        | <span data-ttu-id="9ca59-261">Significado</span><span class="sxs-lookup"><span data-stu-id="9ca59-261">Meaning</span></span> |
|------------------|-------------------------------------------|
| <span data-ttu-id="9ca59-262">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="9ca59-262">*agent_ptr*</span></span>        | <span data-ttu-id="9ca59-263">Puntero al agente de SNMP que realiza la llamada</span><span class="sxs-lookup"><span data-stu-id="9ca59-263">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="9ca59-264">object_requested</span><span class="sxs-lookup"><span data-stu-id="9ca59-264">object_requested</span></span> | <span data-ttu-id="9ca59-265">Cadena ASCII que representa el identificador de objeto para el que es la operación GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="9ca59-265">ASCII string representing the object ID the GETNEXT operation is for.</span></span> |
| <span data-ttu-id="9ca59-266">object_data</span><span class="sxs-lookup"><span data-stu-id="9ca59-266">object_data</span></span>      | <span data-ttu-id="9ca59-267">Estructura de datos que contiene el valor recuperado por la devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="9ca59-267">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="9ca59-268">Se puede establecer con una serie de API SNMP de NetX Duo que se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="9ca59-268">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="9ca59-269">Al igual que sucede con las devoluciones de llamada GET, los objetos con datos de cadenas de octeto deben tener asignada la longitud para que la función interna la conozca, ya que la devolución de llamada no tiene ningún argumento de longitud:</span><span class="sxs-lookup"><span data-stu-id="9ca59-269">Same as is true for GET callbacks, objects with octet string data must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="9ca59-270">Dado que la devolución de llamada GET no conoce el tipo de datos, no es necesario comprobarlo.</span><span class="sxs-lookup"><span data-stu-id="9ca59-270">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="9ca59-271">La longitud no tendrá ningún efecto en las cadenas o tipos numéricos que estén delimitados con valores NULL.</span><span class="sxs-lookup"><span data-stu-id="9ca59-271">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="9ca59-272">A continuación, llame a la función interna:</span><span class="sxs-lookup"><span data-stu-id="9ca59-272">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="9ca59-273">Si la función de devolución de llamada no encuentra el objeto solicitado, se debe devolver el código de error **NX_SNMP_ERROR_NOSUCHNAME**.</span><span class="sxs-lookup"><span data-stu-id="9ca59-273">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="9ca59-274">Si se detecta algún otro error, se debe devolver el código **NX_SNMP_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="9ca59-274">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-set-callback"></a><span data-ttu-id="9ca59-275">Devolución de llamada SET del agente de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-275">NetX Duo SNMP Agent SET Callback</span></span>

<span data-ttu-id="9ca59-276">La aplicación debe establecer la rutina de devolución de llamada para controlar las solicitudes del objeto SET del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-276">The application should set the callback routine for handling SET object requests from the SNMP Manager.</span></span> <span data-ttu-id="9ca59-277">La devolución de llamada SET establece el valor del objeto especificado por la solicitud.</span><span class="sxs-lookup"><span data-stu-id="9ca59-277">The SET callback sets the value of the object specified by the request.</span></span>

<span data-ttu-id="9ca59-278">La rutina de devolución de llamada de la solicitud SET de la aplicación se define a continuación:</span><span class="sxs-lookup"><span data-stu-id="9ca59-278">The application SET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="9ca59-279">Los parámetros de entrada se definen de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ca59-279">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="9ca59-280">Parámetro</span><span class="sxs-lookup"><span data-stu-id="9ca59-280">Parameter</span></span>        | <span data-ttu-id="9ca59-281">Significado</span><span class="sxs-lookup"><span data-stu-id="9ca59-281">Meaning</span></span> |
|------------------|-------- |
| <span data-ttu-id="9ca59-282">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="9ca59-282">*agent_ptr*</span></span>      | <span data-ttu-id="9ca59-283">Puntero al agente de SNMP que realiza la llamada</span><span class="sxs-lookup"><span data-stu-id="9ca59-283">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="9ca59-284">object_requested</span><span class="sxs-lookup"><span data-stu-id="9ca59-284">object_requested</span></span> | <span data-ttu-id="9ca59-285">Cadena ASCII que representa el identificador de objeto para el que es la operación SET.</span><span class="sxs-lookup"><span data-stu-id="9ca59-285">ASCII string representing the object ID the SET operation is for.</span></span> |
| <span data-ttu-id="9ca59-286">object_data</span><span class="sxs-lookup"><span data-stu-id="9ca59-286">object_data</span></span>      | <span data-ttu-id="9ca59-287">Estructura de datos que contiene el nuevo valor para el objeto especificado.</span><span class="sxs-lookup"><span data-stu-id="9ca59-287">Data structure that contains the new value for the specified object.</span></span> <span data-ttu-id="9ca59-288">La operación real se puede realizar con la API de SNMP de NetX Duo que se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="9ca59-288">The actual operation can be done using the NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="9ca59-289">Tenga en cuenta que, para las cadenas de octetos, la devolución de llamada SET debe actualizar la tabla MIB con la longitud de los datos, ya que el agente de SNMP ha analizado los datos y conoce el tipo y la longitud:</span><span class="sxs-lookup"><span data-stu-id="9ca59-289">Note that for octet strings, the SET callback should update the MIB table with the length of the data since the SNMP Agent has parsed the data and knows the type and length:</span></span>

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

<span data-ttu-id="9ca59-290">Si la función de devolución de llamada no encuentra el objeto solicitado, se debe devolver el código de error **NX_SNMP_ERROR_NOSUCHNAME**.</span><span class="sxs-lookup"><span data-stu-id="9ca59-290">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span>

<span data-ttu-id="9ca59-291">Si el host de SNMP de NetX Duo ha creado cadenas de comunidad privadas y el emisor de SNMP de la solicitud SET no tiene la cadena privada coincidente, es posible que se devuelva el error **NX_SNMP_ERROR_NOACCESS**.</span><span class="sxs-lookup"><span data-stu-id="9ca59-291">If the NetX Duo SNMP host has created private community strings, and the SNMP sender of the SET request does not have the matching private string, it may return an **NX_SNMP_ERROR_NOACCESS** error.</span></span> <span data-ttu-id="9ca59-292">Si se detecta algún otro error, se devolverá el código **NX_SNMP_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="9ca59-292">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

> [!NOTE]
> <span data-ttu-id="9ca59-293">*Aunque el agente de SNMP de NetX Duo proporciona una base de datos MIB de SNMP con la distribución, esta es principalmente para fines de prueba y desarrollo. Probablemente, el desarrollador necesitará una base de datos MIB de propiedad para una aplicación SNMP profesional.*</span><span class="sxs-lookup"><span data-stu-id="9ca59-293">*Although NetX Duo SNMP Agent supplies an SNMP MIB database with the distribution, it is primarily for testing and development purposes. The developer will likely require a proprietary MIB database for a professional SNMP application.*</span></span>

## <a name="changing-snmp-version-at-run-time"></a><span data-ttu-id="9ca59-294">Cambio de la versión de SNMP en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="9ca59-294">Changing SNMP Version at Run Time</span></span>

<span data-ttu-id="9ca59-295">El host de agente de SNMP puede cambiar la versión de SNMP para cada una de las tres versiones en tiempo de ejecución mediante el servicio *nx_snmp_agent_set_version*.</span><span class="sxs-lookup"><span data-stu-id="9ca59-295">The SNMP Agent host can change SNMP version for each of the three versions at run time using the *nx_snmp_agent_set_version* service.</span></span> <span data-ttu-id="9ca59-296">El agente de SNMP se habilita de forma predeterminada para las tres versiones cuando se crea el agente de SNMP en *nx_snmp_agent_create*.</span><span class="sxs-lookup"><span data-stu-id="9ca59-296">The SNMP Agent is by default enabled for all three versions when the SNMP Agent is created in *nx_snmp_agent_create*.</span></span> <span data-ttu-id="9ca59-297">Sin embargo, la aplicación puede limitarlo a un subconjunto de todas las versiones.</span><span class="sxs-lookup"><span data-stu-id="9ca59-297">However, the application can limit that to a subset of all versions.</span></span>

> [!NOTE]
> <span data-ttu-id="9ca59-298">*Si las opciones de configuración NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 o NX_SNMP_DISABLE_V3 están definidas, esta función no tendrá ningún efecto cuando se habiliten las versiones afectadas.*</span><span class="sxs-lookup"><span data-stu-id="9ca59-298">*If the configuration options NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 and/or NX_SNMP_DISABLE_V3 are defined, this function will have no effect enabling the effected versions.*</span></span>

<span data-ttu-id="9ca59-299">El agente de SNMP puede recuperar la versión de SNMP del paquete de SNMP más reciente recibido mediante el servicio *nx_snmp_agent_get_current_version*.</span><span class="sxs-lookup"><span data-stu-id="9ca59-299">The SNMP Agent can retrieve the SNMP version of the latest SNMP packet received using the *nx_snmp_agent_get_current_version* service.</span></span>

## <a name="snmpv3-discovery"></a><span data-ttu-id="9ca59-300">Detección de SNMPv3</span><span class="sxs-lookup"><span data-stu-id="9ca59-300">SNMPv3 Discovery</span></span>

<span data-ttu-id="9ca59-301">Si el agente de SNMP está habilitado para SNMPv3, este responderá a las solicitudes de detección del administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="9ca59-301">The SNMP Agent, if enabled for SNMPv3, will respond to discovery requests from the SNMP Manager.</span></span> <span data-ttu-id="9ca59-302">Esta solicitud contiene datos de parámetros de seguridad con valores NULL para el identificador del motor autoritativo, el nombre de usuario, el recuento de arranques y el tiempo de arranque.</span><span class="sxs-lookup"><span data-stu-id="9ca59-302">Such a request contains security parameter data with null values for Authoritative Engine ID, user name, boot count and boot time.</span></span> <span data-ttu-id="9ca59-303">Los parámetros de autenticación no se aplican al mensaje DISCOVERY.</span><span class="sxs-lookup"><span data-stu-id="9ca59-303">Authentication parameters are not applied to the DISCOVERY message.</span></span> <span data-ttu-id="9ca59-304">La lista de enlaces de variables de la solicitud está vacía (no contiene ningún elemento).</span><span class="sxs-lookup"><span data-stu-id="9ca59-304">The variable binding list in the request is empty (contains zero items).</span></span> <span data-ttu-id="9ca59-305">El agente de SNMP responde con un recuento y un tiempo de arranque de cero y la lista de enlaces de variables que contiene un elemento, *usmStatsUnknownEngineIDs*, que es el recuento de solicitudes recibidas con un identificador de motor desconocido (NULL).</span><span class="sxs-lookup"><span data-stu-id="9ca59-305">The SNMP agent responds with a zero boot time and count, and the variable binding list containing 1 item, *usmStatsUnknownEngineIDs*, which is the count of requests received with an unknown (null) engine ID.</span></span> <span data-ttu-id="9ca59-306">En la solicitud GETNEXT subsiguiente del explorador/administrador, los datos de arranque y los parámetros de seguridad se rellenan solo si está habilitada la seguridad.</span><span class="sxs-lookup"><span data-stu-id="9ca59-306">On the subsequent GETNEXT request from the Browser/Manager, the boot data and security parameters are filled in only if security is enabled.</span></span> <span data-ttu-id="9ca59-307">Si es así, también se enviará una actualización de datos NotInTime en la PDU.</span><span class="sxs-lookup"><span data-stu-id="9ca59-307">If so it will also send a NotInTime data update in the PDU.</span></span> <span data-ttu-id="9ca59-308">Los parámetros de seguridad, como la autenticación, demuestran la identidad del agente para el administrador.</span><span class="sxs-lookup"><span data-stu-id="9ca59-308">The security parameters, e.g. authentication prove the identity of the Agent to the Manager.</span></span>

<span data-ttu-id="9ca59-309">Puede encontrar información más detallada sobre la autenticación SNMPv3 en el protocolo RFC 3414 "Modelo de seguridad basado en el usuario (USM) para la versión 3 del Protocolo simple de administración de redes (SNMPv3)".</span><span class="sxs-lookup"><span data-stu-id="9ca59-309">More detailed information on SNMPv3 authentication is available in RFC 3414 “User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)”.</span></span>

## <a name="netx-duo-snmp-rfcs"></a><span data-ttu-id="9ca59-310">RFC de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="9ca59-310">NetX Duo SNMP RFCs</span></span>

<span data-ttu-id="9ca59-311">SNMP de NetX Duo es compatible con RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 y otros protocolos RFC relacionados.</span><span class="sxs-lookup"><span data-stu-id="9ca59-311">NetX Duo SNMP is compliant with RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 and related RFCs.</span></span>
