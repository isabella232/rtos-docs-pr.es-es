---
title: 'Capítulo 3: Descripción de los servicios de Protocolo punto a punto (PPP) de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios PPP de Azure RTOS NetX (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f24d7366d27a8223b069a54ef7b93f6b3e38bf3a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815154"
---
# <a name="chapter-3---description-of-azure-rtos-netx-point-to-point-protocol-ppp-services"></a><span data-ttu-id="1045a-103">Capítulo 3: Descripción de los servicios de Protocolo punto a punto (PPP) de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="1045a-103">Chapter 3 - Description of Azure RTOS NetX Point-to-Point Protocol (PPP) services</span></span>

<span data-ttu-id="1045a-104">Este capítulo contiene una descripción de todos los servicios PPP de Azure RTOS NetX (enumerados a continuación) en orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="1045a-104">This chapter contains a description of all Azure RTOS NetX PPP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="1045a-105">En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="1045a-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="1045a-106">**nx_ppp_byte_receive**: *Recibir un byte de ISR en serie*</span><span class="sxs-lookup"><span data-stu-id="1045a-106">**nx_ppp_byte_receive**: *Receive a byte from serial ISR*</span></span>
- <span data-ttu-id="1045a-107">**nx_ppp_chap_challenge**: *Generar un desafío CHAP*</span><span class="sxs-lookup"><span data-stu-id="1045a-107">**nx_ppp_chap_challenge**: *Generate a CHAP challenge*</span></span>
- <span data-ttu-id="1045a-108">**nx_ppp_chap_enable**: *Habilitar la autenticación CHAP*</span><span class="sxs-lookup"><span data-stu-id="1045a-108">**nx_ppp_chap_enable**: *Enable CHAP authentication*</span></span>
- <span data-ttu-id="1045a-109">**nx_ppp_create**: *Crear una instancia de PPP*</span><span class="sxs-lookup"><span data-stu-id="1045a-109">**nx_ppp_create**: *Create a PPP instance*</span></span>
- <span data-ttu-id="1045a-110">**nx_ppp_delete**: *Eliminar una instancia de PPP*</span><span class="sxs-lookup"><span data-stu-id="1045a-110">**nx_ppp_delete**: *Delete a PPP instance*</span></span>
- <span data-ttu-id="1045a-111">**nx_ppp_dns_address_get**: *Obtener la dirección IP del servidor DNS*</span><span class="sxs-lookup"><span data-stu-id="1045a-111">**nx_ppp_dns_address_get**: *Get DNS IP address*</span></span>
- <span data-ttu-id="1045a-112">**nx_ppp_dns_address_get**: *Establecer la dirección IP del servidor DNS*</span><span class="sxs-lookup"><span data-stu-id="1045a-112">**nx_ppp_dns_address_set**:*Set DNS Server IP address*</span></span>
- <span data-ttu-id="1045a-113">**nx_ppp_secondary_dns_address_get**: *Obtener la dirección IP del servidor DNS secundario*</span><span class="sxs-lookup"><span data-stu-id="1045a-113">**nx_ppp_secondary_dns_address_get**: *Get Secondary DNS Server IP address*</span></span>
- <span data-ttu-id="1045a-114">**nx_ppp_secondary_dns_address_set**: *Establecer la dirección IP del servidor DNS secundario*</span><span class="sxs-lookup"><span data-stu-id="1045a-114">**nx_ppp_secondary_dns_address_set**: *Set Secondary_DNS Server IP address*</span></span>
- <span data-ttu-id="1045a-115">**nx_ppp_interface_index_get**: *Obtener el índice de la interfaz IP*</span><span class="sxs-lookup"><span data-stu-id="1045a-115">**nx_ppp_interface_index_get**: *Get IP interface index*</span></span>
- <span data-ttu-id="1045a-116">**nx_ppp_ip_address_assign**: *Asignar direcciones IP para IPCP*</span><span class="sxs-lookup"><span data-stu-id="1045a-116">**nx_ppp_ip_address_assign**: *Assign IP addresses for IPCP*</span></span>
- <span data-ttu-id="1045a-117">**nx_ppp_link_down_notify**: *Notificar a la aplicación la inactividad del vínculo*</span><span class="sxs-lookup"><span data-stu-id="1045a-117">**nx_ppp_link_down_notify**: *Notify application on link down*</span></span>
- <span data-ttu-id="1045a-118">**nx_ppp_link_down_notify**: *Notificar a la aplicación la recuperación de la actividad del vínculo*</span><span class="sxs-lookup"><span data-stu-id="1045a-118">**nx_ppp_link_up_notify**: *Notify application on link up*</span></span>
- <span data-ttu-id="1045a-119">**nx_ppp_nak_authentication_notify**: *Notificar a la aplicación si se ha recibido un NAK de autenticación*</span><span class="sxs-lookup"><span data-stu-id="1045a-119">**nx_ppp_nak_authentication_notify**: *Notify application if authentication NAK is received*</span></span>
- <span data-ttu-id="1045a-120">**nx_ppp_pap_enable**: *Habilitar la autenticación PAP*</span><span class="sxs-lookup"><span data-stu-id="1045a-120">**nx_ppp_pap_enable**: *Enable PAP authentication*</span></span>
- <span data-ttu-id="1045a-121">**nx_ppp_ping_request**: *Enviar una solicitud de eco LCP*</span><span class="sxs-lookup"><span data-stu-id="1045a-121">**nx_ppp_ping_request**: *Send an LCP echo request*</span></span>
- <span data-ttu-id="1045a-122">**nx_ppp_raw_string_send**: *Enviar una cadena que no sea PPP*</span><span class="sxs-lookup"><span data-stu-id="1045a-122">**nx_ppp_raw_string_send**: *Send non PPP string*</span></span>
- <span data-ttu-id="1045a-123">**nx_ppp_restart**: *Reiniciar el procesamiento de PPP*</span><span class="sxs-lookup"><span data-stu-id="1045a-123">**nx_ppp_restart**: *Restart PPP processing*</span></span>
- <span data-ttu-id="1045a-124">**nx_ppp_start**: *Iniciar el procesamiento de PPP*</span><span class="sxs-lookup"><span data-stu-id="1045a-124">**nx_ppp_start**: *Start PPP processing*</span></span>
- <span data-ttu-id="1045a-125">**nx_ppp_status_get**: *Obtener el estado actual de PPP*</span><span class="sxs-lookup"><span data-stu-id="1045a-125">**nx_ppp_status_get**: *Get current PPP status*</span></span>
- <span data-ttu-id="1045a-126">**nx_ppp_stop**: *Detener el procesamiento de PPP*</span><span class="sxs-lookup"><span data-stu-id="1045a-126">**nx_ppp_stop**: *Stop PPP processing*</span></span>
- <span data-ttu-id="1045a-127">**nx_ppp_packet_receive**: *Recibir un paquete de PPP*</span><span class="sxs-lookup"><span data-stu-id="1045a-127">**nx_ppp_packet_receive**: *Receive PPP packet*</span></span>
- <span data-ttu-id="1045a-128">**nx_ppp_packet_send_set**: *establecer la función de envío de paquetes de PPP*</span><span class="sxs-lookup"><span data-stu-id="1045a-128">**nx_ppp_packet_send_set**: *Set PPP packet send function*</span></span>

## <a name="nx_ppp_byte_receive"></a><span data-ttu-id="1045a-129">nx_ppp_byte_receive</span><span class="sxs-lookup"><span data-stu-id="1045a-129">nx_ppp_byte_receive</span></span>

<span data-ttu-id="1045a-130">Recibir un byte de ISR en serie</span><span class="sxs-lookup"><span data-stu-id="1045a-130">Receive a byte from serial ISR</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-131">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-131">Prototype</span></span>

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a><span data-ttu-id="1045a-132">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-132">Description</span></span>

<span data-ttu-id="1045a-133">Normalmente, se llama a este servicio desde la rutina de servicio de interrupción (ISR) del controlador serie de la aplicación para transferir un byte recibido a PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-133">This service is typically called from the application’s serial driver Interrupt Service Routine (ISR) to transfer a received byte to PPP.</span></span> <span data-ttu-id="1045a-134">Cuando se le llama, esta rutina coloca el byte recibido en un búfer de bytes circular y emite una notificación al subproceso de PPP adecuado para su procesamiento.</span><span class="sxs-lookup"><span data-stu-id="1045a-134">When called, this routine places the received byte into a circular byte buffer and notifies the appropriate PPP thread for processing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-135">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-135">Input Parameters</span></span>

- <span data-ttu-id="1045a-136">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-136">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-137">**byte**: byte recibido del dispositivo serie.</span><span class="sxs-lookup"><span data-stu-id="1045a-137">**byte**: Byte received from serial device</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-138">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-138">Return Values</span></span>

- <span data-ttu-id="1045a-139">**NX_SUCCESS**: (0x00) Recepción correcta de bytes de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-139">**NX_SUCCESS**: (0x00) Successful PPP byte receive.</span></span>
- <span data-ttu-id="1045a-140">**NX_PPP_BUFFER_FULL**: (0xB1) El búfer serie de PPP ya está lleno.</span><span class="sxs-lookup"><span data-stu-id="1045a-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP serial buffer is already full.</span></span>
- <span data-ttu-id="1045a-141">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-141">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-142">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-142">Allowed From</span></span>

<span data-ttu-id="1045a-143">Subprocesos, ISR</span><span class="sxs-lookup"><span data-stu-id="1045a-143">Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="1045a-144">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-144">Example</span></span>

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a><span data-ttu-id="1045a-145">nx_ppp_chap_challenge</span><span class="sxs-lookup"><span data-stu-id="1045a-145">nx_ppp_chap_challenge</span></span>

<span data-ttu-id="1045a-146">Generar un desafío CHAP</span><span class="sxs-lookup"><span data-stu-id="1045a-146">Generate a CHAP challenge</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-147">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-147">Prototype</span></span>

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="1045a-148">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-148">Description</span></span>

<span data-ttu-id="1045a-149">Este servicio inicia un desafío CHAP después de que la conexión de PPP ya esté activa y en ejecución.</span><span class="sxs-lookup"><span data-stu-id="1045a-149">This service initiates a CHAP challenge after the PPP connection is already up and running.</span></span> <span data-ttu-id="1045a-150">Esto proporciona a la aplicación la posibilidad de comprobar la autenticidad de la conexión periódicamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-150">This gives the application the ability to verify the authenticity of the connection on a periodic basis.</span></span> <span data-ttu-id="1045a-151">Si el desafío no se realiza correctamente, el vínculo de PPP se cierra.</span><span class="sxs-lookup"><span data-stu-id="1045a-151">If the challenge is unsuccessful, the PPP link is closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-152">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-152">Input Parameters</span></span>

- <span data-ttu-id="1045a-153">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-153">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-154">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-154">Return Values</span></span>

- <span data-ttu-id="1045a-155">**NX_SUCCESS**: (0x00) Desafío de PPP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-155">**NX_SUCCESS**: (0x00) Successful PPP challenge initiated.</span></span>
- <span data-ttu-id="1045a-156">**NX_PPP_FAILURE**: (0xB0) Desafío de PPP no válido, CHAP se habilitó solo para la respuesta.</span><span class="sxs-lookup"><span data-stu-id="1045a-156">**NX_PPP_FAILURE**: (0xB0) Invalid PPP challenge, CHAP was enabled only for response.</span></span>
- <span data-ttu-id="1045a-157">**NX_NOT_IMPLEMENTED**: (0x80) La lógica de CHAP se deshabilitó a través de NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="1045a-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="1045a-158">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-158">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="1045a-159">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-159">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-160">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-160">Allowed From</span></span>

<span data-ttu-id="1045a-161">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-161">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-162">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-162">Example</span></span>

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a><span data-ttu-id="1045a-163">nx_ppp_chap_enable</span><span class="sxs-lookup"><span data-stu-id="1045a-163">nx_ppp_chap_enable</span></span>

<span data-ttu-id="1045a-164">Habilitar la autenticación CHAP</span><span class="sxs-lookup"><span data-stu-id="1045a-164">Enable CHAP authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-165">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-165">Prototype</span></span>

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a><span data-ttu-id="1045a-166">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-166">Description</span></span>

<span data-ttu-id="1045a-167">Este servicio habilita el Protocolo de autenticación por desafío mutuo (CHAP) para la instancia de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="1045a-167">This service enables the Challenge-Handshake Authentication Protocol (CHAP) for the specified PPP instance.</span></span>

<span data-ttu-id="1045a-168">Si se especifican los punteros de función "\***get_challenge_values** _" y "_ \*_get_verification_values_\*\*", esta instancia de PPP requiere CHAP.</span><span class="sxs-lookup"><span data-stu-id="1045a-168">If the “\***get_challenge_values**_” and “_\*_get_verification_values_\*\*” function pointers are specified, CHAP is required by this PPP instance.</span></span> <span data-ttu-id="1045a-169">De lo contrario, CHAP solo responde a las solicitudes de desafío del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-169">Otherwise, CHAP only responds to the peer’s challenge requests.</span></span>

<span data-ttu-id="1045a-170">Hay varios elementos de datos a los que se hace referencia a continuación en las funciones de devolución de llamada necesarias.</span><span class="sxs-lookup"><span data-stu-id="1045a-170">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="1045a-171">Se espera que los elementos de datos *secret*, *name* y *system* sean cadenas terminadas en NULL con un tamaño máximo de NX_PPP_NAME_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="1045a-171">The data items *secret*, *name*, and *system* are expected to be NULL-terminated strings with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="1045a-172">Se espera que el elemento de datos *rand_value* sea una cadena terminada en NULL con un tamaño máximo de NX_PPP_VALUE_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="1045a-172">The data item *rand_value* is expected to be a NULL-terminated string with a maximum size of NX_PPP_VALUE_SIZE-1.</span></span> <span data-ttu-id="1045a-173">El elemento de datos *id* es un tipo de carácter único sin signo.</span><span class="sxs-lookup"><span data-stu-id="1045a-173">The data item *id* is a simple unsigned character type.</span></span>

>[!NOTE]
> <span data-ttu-id="1045a-174">Se debe llamar a esta función después de *nx_ppp_create*, pero antes de nx_ip_create o *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="1045a-174">This function must be called after *nx_ppp_create* but before nx_ip_create or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-175">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-175">Input Parameters</span></span>

- <span data-ttu-id="1045a-176">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-176">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-177">**get_challenge_values**: Puntero a la función de aplicación para recuperar los valores usados para el desafío.</span><span class="sxs-lookup"><span data-stu-id="1045a-177">**get_challenge_values**: Pointer to application function to retrieve values used for the challenge.</span></span> <span data-ttu-id="1045a-178">Tenga en cuenta que los valores de *rand_value*, *id* y *secret* deben copiarse en los destinos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="1045a-178">Note that the *rand_value*, *id*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="1045a-179">**get_responder_values**: Puntero a la función de aplicación que recupera los valores utilizados para responder a un desafío.</span><span class="sxs-lookup"><span data-stu-id="1045a-179">**get_responder_values**: Pointer to application function that retrieves values used to respond to a challenge.</span></span> <span data-ttu-id="1045a-180">Tenga en cuenta que los valores de *system*, *name* y *secret* deben copiarse en los destinos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="1045a-180">Note that the *system*, *name*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="1045a-181">**get_verification_values**: Puntero a la función de aplicación que recupera los valores utilizados para comprobar la respuesta del desafío.</span><span class="sxs-lookup"><span data-stu-id="1045a-181">**get_verification_values**: Pointer to application function that retrieves values used to verify the challenge response.</span></span> <span data-ttu-id="1045a-182">Tenga en cuenta que los valores de *system*,*name* y *secret* deben copiarse en los destinos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="1045a-182">Note that the *system*,*name*, and *secret* values must be copied into the supplied destinations.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-183">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-183">Return Values</span></span>

- <span data-ttu-id="1045a-184">**NX_SUCCESS** (0x00) CHAP de PPP habilitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-184">**NX_SUCCESS**: (0x00) Successful PPP CHAP enable</span></span>
- <span data-ttu-id="1045a-185">**NX_NOT_IMPLEMENTED**: (0x80) La lógica de CHAP se deshabilitó a través de NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="1045a-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="1045a-186">NX_PTR_ERROR: (0x07) Puntero de PPP o puntero de función de devolución de llamada no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-186">NX_PTR_ERROR: (0x07) Invalid PPP pointer or callback function pointer.</span></span> <span data-ttu-id="1045a-187">Tenga en cuenta que si se especifica *get_challenge_values*, también se debe proporcionar la función *get_verification_values*.</span><span class="sxs-lookup"><span data-stu-id="1045a-187">Note that if *get_challenge_values* is specified, then the *get_verification_values* function must also be supplied.</span></span>
- <span data-ttu-id="1045a-188">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-188">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-189">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-189">Allowed From</span></span>

<span data-ttu-id="1045a-190">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-190">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-191">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-191">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a><span data-ttu-id="1045a-192">nx_ppp_create</span><span class="sxs-lookup"><span data-stu-id="1045a-192">nx_ppp_create</span></span>

<span data-ttu-id="1045a-193">Crear una instancia de PPP</span><span class="sxs-lookup"><span data-stu-id="1045a-193">Create a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-194">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-194">Prototype</span></span>

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a><span data-ttu-id="1045a-195">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-195">Description</span></span>

<span data-ttu-id="1045a-196">Este servicio crea una instancia de PPP para la instancia de IP de NetX especificada.</span><span class="sxs-lookup"><span data-stu-id="1045a-196">This service creates a PPP instance for the specified NetX IP instance.</span></span>

>[!NOTE]
> <span data-ttu-id="1045a-197">Por lo general, es una buena idea crear el subproceso de IP de NetX con una prioridad más alta que la prioridad de los subprocesos de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-197">It is generally a good idea to create the NetX IP thread at a higher priority than the PPP thread priority.</span></span> <span data-ttu-id="1045a-198">Consulte el servicio *nx_ip_create* para obtener más información sobre cómo especificar la prioridad del subproceso de IP.</span><span class="sxs-lookup"><span data-stu-id="1045a-198">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-199">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-199">Input Parameters</span></span>

- <span data-ttu-id="1045a-200">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-200">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-201">**nombre**: Nombre de esta instancia de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-201">**name**: Name of this PPP instance.</span></span>
- <span data-ttu-id="1045a-202">**ip_ptr**: Puntero al bloque de control para la instancia de IP que todavía no se ha creado.</span><span class="sxs-lookup"><span data-stu-id="1045a-202">**ip_ptr**: Pointer to control block for not-yet-created IP instance.</span></span>
- <span data-ttu-id="1045a-203">**stack_memory_ptr**: Puntero al inicio del área de la pila del subproceso de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-203">**stack_memory_ptr**: Pointer to start of PPP thread’s stack area.</span></span>
- <span data-ttu-id="1045a-204">**stack_size**: Tamaño en bytes de la pila del subproceso.</span><span class="sxs-lookup"><span data-stu-id="1045a-204">**stack_size**: Size in bytes in the thread’s stack.</span></span>
- <span data-ttu-id="1045a-205">**pool_ptr**: Puntero al grupo de paquetes predeterminado.</span><span class="sxs-lookup"><span data-stu-id="1045a-205">**pool_ptr**: Pointer to default packet pool.</span></span>
- <span data-ttu-id="1045a-206">**thread_priority**: Prioridad de los subprocesos de PPP internos (1-31).</span><span class="sxs-lookup"><span data-stu-id="1045a-206">**thread_priority**: Priority of internal PPP threads (1-31).</span></span>
- <span data-ttu-id="1045a-207">**ppp_invalid_packet_handler**: Puntero de función al controlador de la aplicación para todos los paquetes que no son de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-207">**ppp_invalid_packet_handler**: Function pointer to application’s handler for all non-PPP packets.</span></span> <span data-ttu-id="1045a-208">El PPP de NetX normalmente llama a esta rutina durante la inicialización.</span><span class="sxs-lookup"><span data-stu-id="1045a-208">The NetX PPP typically calls this routine during initialization.</span></span> <span data-ttu-id="1045a-209">Aquí es donde la aplicación puede responder a los comandos del módem o, en el caso de Windows XP, la aplicación de PPP de NetX puede iniciar PPP respondiendo con "CLIENT SERVER" al "CLIENT" inicial enviado por Windows XP.</span><span class="sxs-lookup"><span data-stu-id="1045a-209">This is where the application can respond to modem commands or in the case of Windows XP, the NetX PPP application can initiate PPP by responding with“ CLIENT SERVER” to the initial “CLIENT” sent by Windows XP.</span></span>
- <span data-ttu-id="1045a-210">**ppp_byte_send**: Puntero de función a la rutina de salida de bytes de serie de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1045a-210">**ppp_byte_send**: Function pointer to application’s serial byte output routine.</span></span>


### <a name="return-values"></a><span data-ttu-id="1045a-211">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-211">Return Values</span></span>

- <span data-ttu-id="1045a-212">**NX_SUCCESS** (0x00) Instancia de PPP creada correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-212">**NX_SUCCESS**: (0x00) Successful PPP create.</span></span>
- <span data-ttu-id="1045a-213">NX_PTR_ERROR: (0x07) Puntero de función de salida de PPP, IP o bytes no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-213">NX_PTR_ERROR: (0x07) Invalid PPP, IP, or byte output function pointer.</span></span>
- <span data-ttu-id="1045a-214">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-214">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-215">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-215">Allowed From</span></span>

<span data-ttu-id="1045a-216">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-216">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-217">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-217">Example</span></span>

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a><span data-ttu-id="1045a-218">nx_ppp_delete</span><span class="sxs-lookup"><span data-stu-id="1045a-218">nx_ppp_delete</span></span>

<span data-ttu-id="1045a-219">Eliminar una instancia de PPP</span><span class="sxs-lookup"><span data-stu-id="1045a-219">Delete a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-220">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-220">Prototype</span></span>

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="1045a-221">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-221">Description</span></span>

<span data-ttu-id="1045a-222">Este servicio elimina la instancia de PPP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1045a-222">This service deletes the previously created PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-223">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-223">Input Parameters</span></span>

- <span data-ttu-id="1045a-224">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-224">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-225">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-225">Return Values</span></span>

- <span data-ttu-id="1045a-226">**NX_SUCCESS**: (0x00) Instancia de PPP eliminada correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-226">**NX_SUCCESS**: (0x00) Successful PPP deletion.</span></span>
- <span data-ttu-id="1045a-227">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-227">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="1045a-228">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-228">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-229">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-229">Allowed From</span></span>

<span data-ttu-id="1045a-230">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-231">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-231">Example</span></span>

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a><span data-ttu-id="1045a-232">nx_ppp_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="1045a-232">nx_ppp_dns_address_get</span></span>

<span data-ttu-id="1045a-233">Dirección IP de DNS</span><span class="sxs-lookup"><span data-stu-id="1045a-233">Get DNS IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-234">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-234">Prototype</span></span>

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="1045a-235">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-235">Description</span></span>

<span data-ttu-id="1045a-236">Este servicio recupera la dirección IP de DNS proporcionada por el elemento del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-236">This service retrieves the DNS IP address supplied by the peer.</span></span> <span data-ttu-id="1045a-237">Si el elemento del mismo nivel no proporcionó ninguna dirección IP, se devuelve una dirección IP de 0.</span><span class="sxs-lookup"><span data-stu-id="1045a-237">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-238">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-238">Input Parameters</span></span>

- <span data-ttu-id="1045a-239">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-239">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-240">**dns_address_ptr**: destino de la dirección IP del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="1045a-240">**dns_address_ptr**: Destination for DNS IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-241">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-241">Return Values</span></span>

- <span data-ttu-id="1045a-242">**NX_SUCCESS**: (0x00) la dirección PPP se ha obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-242">**NX_SUCCESS**: (0x00) Successful PPP address get.</span></span>
- <span data-ttu-id="1045a-243">**NX_PPP_NOT_ESTABLISHED**: (0xB5) la instancia de PPP no ha completado la negociación con el elemento del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-243">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="1045a-244">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-244">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-245">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-245">Allowed From</span></span>

<span data-ttu-id="1045a-246">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="1045a-246">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="1045a-247">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-247">Example</span></span>

```c

ULONG  my_dns_address;

/* Get IP Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a><span data-ttu-id="1045a-248">nx_ppp_secondary_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="1045a-248">nx_ppp_secondary_dns_address_get</span></span>

<span data-ttu-id="1045a-249">Obtener la dirección IP del servidor DNS secundario</span><span class="sxs-lookup"><span data-stu-id="1045a-249">Get Secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-250">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-250">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="1045a-251">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-251">Description</span></span>

<span data-ttu-id="1045a-252">Este servicio recupera la dirección IP secundaria de DNS proporcionada por el elemento del mismo nivel en el protocolo de enlace IPCP.</span><span class="sxs-lookup"><span data-stu-id="1045a-252">This service retrieves the secondary DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="1045a-253">Si el elemento del mismo nivel no proporcionó ninguna dirección IP, se devuelve una dirección IP de 0.</span><span class="sxs-lookup"><span data-stu-id="1045a-253">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-254">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-254">Input Parameters</span></span>

- <span data-ttu-id="1045a-255">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-255">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-256">**dns_address_ptr**: destino de la dirección del servidor DNS secundario.</span><span class="sxs-lookup"><span data-stu-id="1045a-256">**dns_address_ptr**: Destination for Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-257">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-257">Return Values</span></span>

- <span data-ttu-id="1045a-258">**NX_SUCCESS**: (0x00) DNS obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-258">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="1045a-259">**NX_PPP_NOT_ESTABLISHED**: (0xB5) la instancia de PPP no ha completado la negociación con el elemento del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-259">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="1045a-260">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-260">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-261">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-261">Allowed From</span></span>

<span data-ttu-id="1045a-262">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="1045a-262">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="1045a-263">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-263">Example</span></span>

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a><span data-ttu-id="1045a-264">nx_ppp_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="1045a-264">nx_ppp_dns_address_set</span></span>

<span data-ttu-id="1045a-265">Establecer la dirección IP del servidor DNS principal</span><span class="sxs-lookup"><span data-stu-id="1045a-265">Set primary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-266">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-266">Prototype</span></span>

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="1045a-267">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-267">Description</span></span>

<span data-ttu-id="1045a-268">Este servicio establece la dirección IP del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="1045a-268">This service sets the DNS Server IP address.</span></span> <span data-ttu-id="1045a-269">Si el elemento del mismo nivel envía una solicitud de opción de servidor DNS en el estado de IPCP, este host proporcionará la información.</span><span class="sxs-lookup"><span data-stu-id="1045a-269">If the peer sends a DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-270">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-270">Input Parameters</span></span>

- <span data-ttu-id="1045a-271">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-271">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-272">**dns_address**: dirección del servidor DNS.</span><span class="sxs-lookup"><span data-stu-id="1045a-272">**dns_address**: DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-273">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-273">Return Values</span></span>

- <span data-ttu-id="1045a-274">**NX_SUCCESS**: (0x00) DNS establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-274">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span>
- <span data-ttu-id="1045a-275">**NX_PPP_NOT_ESTABLISHED**: (0xB5) la instancia de PPP no ha completado la negociación con el elemento del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-275">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="1045a-276">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-276">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-277">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-277">Allowed From</span></span>

<span data-ttu-id="1045a-278">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-279">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-279">Example</span></span>

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a><span data-ttu-id="1045a-280">nx_ppp_secondary_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="1045a-280">nx_ppp_secondary_dns_address_set</span></span>

<span data-ttu-id="1045a-281">Establecer la dirección IP del servidor DNS secundario</span><span class="sxs-lookup"><span data-stu-id="1045a-281">Set secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-282">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-282">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="1045a-283">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-283">Description</span></span>

<span data-ttu-id="1045a-284">Este servicio establece la dirección IP del servidor DNS secundario.</span><span class="sxs-lookup"><span data-stu-id="1045a-284">This service sets the secondary DNS Server IP address.</span></span> <span data-ttu-id="1045a-285">Si el elemento del mismo nivel envía una solicitud de opción de servidor DNS secundario en el estado de IPCP, este host proporcionará la información.</span><span class="sxs-lookup"><span data-stu-id="1045a-285">If the peer sends a secondary DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-286">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-286">Input Parameters</span></span>

- <span data-ttu-id="1045a-287">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-287">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-288">**dns_address**: dirección del servidor DNS secundario.</span><span class="sxs-lookup"><span data-stu-id="1045a-288">**dns_address**: Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-289">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-289">Return Values</span></span>

- <span data-ttu-id="1045a-290">**NX_SUCCESS**: (0x00) DNS establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-290">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span> 
- <span data-ttu-id="1045a-291">**NX_PPP_NOT_ESTABLISHED**: (0xB5) la instancia de PPP no ha completado la negociación con el elemento del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-291">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="1045a-292">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-292">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-293">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-293">Allowed From</span></span>

<span data-ttu-id="1045a-294">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-294">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-295">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-295">Example</span></span>

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a><span data-ttu-id="1045a-296">nx_ppp_interface_index_get</span><span class="sxs-lookup"><span data-stu-id="1045a-296">nx_ppp_interface_index_get</span></span>

<span data-ttu-id="1045a-297">Obtener índice de la interfaz IP</span><span class="sxs-lookup"><span data-stu-id="1045a-297">Get IP interface index</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-298">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-298">Prototype</span></span>

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a><span data-ttu-id="1045a-299">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-299">Description</span></span>

<span data-ttu-id="1045a-300">Este servicio recupera el índice de interfaz IP asociado a esta instancia de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-300">This service retrieves the IP interface index associated with this PPP instance.</span></span> <span data-ttu-id="1045a-301">Esto solo resulta útil cuando la instancia de PPP no es la interfaz principal de una instancia de IP.</span><span class="sxs-lookup"><span data-stu-id="1045a-301">This is only useful when the PPP instance is not the primary interface of an IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-302">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-302">Input Parameters</span></span>

- <span data-ttu-id="1045a-303">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-303">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-304">**index_ptr**: destino del índice de interfaz.</span><span class="sxs-lookup"><span data-stu-id="1045a-304">**index_ptr**: Destination for interface index</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-305">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-305">Return Values</span></span>

- <span data-ttu-id="1045a-306">**NX_SUCCESS**: (0x00) índice de PPP obtenido correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-306">**NX_SUCCESS**: (0x00) Successful PPP index get.</span></span>
- <span data-ttu-id="1045a-307">**NX_IN_PROGRESS**: (0X37) la instancia de PPP no ha completado la inicialización.</span><span class="sxs-lookup"><span data-stu-id="1045a-307">**NX_IN_PROGRESS**: (0x37) PPP has not completed initialization.</span></span>
- <span data-ttu-id="1045a-308">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-308">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-309">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-309">Allowed From</span></span>

<span data-ttu-id="1045a-310">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="1045a-310">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="1045a-311">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-311">Example</span></span>

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a><span data-ttu-id="1045a-312">nx_ppp_ip_address_assign</span><span class="sxs-lookup"><span data-stu-id="1045a-312">nx_ppp_ip_address_assign</span></span>

<span data-ttu-id="1045a-313">Asignar direcciones IP para IPCP</span><span class="sxs-lookup"><span data-stu-id="1045a-313">Assign IP addresses for IPCP</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-314">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-314">Prototype</span></span>

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a><span data-ttu-id="1045a-315">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-315">Description</span></span>

<span data-ttu-id="1045a-316">Este servicio configura las direcciones IP local y del mismo nivel para su uso en el Protocolo de control de protocolo de Internet (IPCP).</span><span class="sxs-lookup"><span data-stu-id="1045a-316">This service sets up the local and peer IP addresses for use in the Internet Protocol Control Protocol (IPCP).</span></span> <span data-ttu-id="1045a-317">La aplicación PPP debe invocar este servicio en una instancia de PPP con direcciones IP válidas para sí mismo y para el otro nodo del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-317">The PPP application should invoke this service on a PPP instance with valid IP addresses for itself and the other peer.</span></span>  <span data-ttu-id="1045a-318">Si no se registran direcciones válidas con una instancia de PPP, debe basarse en el homólogo PPP para definir su dirección IP.</span><span class="sxs-lookup"><span data-stu-id="1045a-318">If no valid addresses are registered with a PPP instance, it must rely on the PPP peer to define its IP address.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="1045a-319">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-319">Input Parameters</span></span>

- <span data-ttu-id="1045a-320">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-320">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-321">**local_ip_address**: dirección IP local.</span><span class="sxs-lookup"><span data-stu-id="1045a-321">**local_ip_address**: Local IP address.</span></span>
- <span data-ttu-id="1045a-322">**peer_ip_address**: dirección IP del elemento del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-322">**peer_ip_address**: Peer’s IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-323">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-323">Return Values</span></span>

- <span data-ttu-id="1045a-324">**NX_SUCCESS**: (0x00) dirección de PPP asignada correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-324">**NX_SUCCESS**: (0x00) Successful PPP address assignment.</span></span>
- <span data-ttu-id="1045a-325">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-325">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="1045a-326">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-327">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-327">Allowed From</span></span>

<span data-ttu-id="1045a-328">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-329">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-329">Example</span></span>

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a><span data-ttu-id="1045a-330">nx_ppp_link_down_notify</span><span class="sxs-lookup"><span data-stu-id="1045a-330">nx_ppp_link_down_notify</span></span>

<span data-ttu-id="1045a-331">Notificar a la aplicación la inactividad del vínculo</span><span class="sxs-lookup"><span data-stu-id="1045a-331">Notify application on link down</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-332">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-332">Prototype</span></span>

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a><span data-ttu-id="1045a-333">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-333">Description</span></span>

<span data-ttu-id="1045a-334">Este servicio registra la devolución de llamada de notificación de inactividad del vínculo de la aplicación con la instancia de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="1045a-334">This service registers the application’s link down notification callback with the specified PPP instance.</span></span> <span data-ttu-id="1045a-335">Si no es NULL, se llama a la función de devolución de llamada de inactividad del vínculo de la aplicación cuando el vínculo deja de funcionar.</span><span class="sxs-lookup"><span data-stu-id="1045a-335">If non-NULL, the application’s link down callback function is called whenever the link goes down.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-336">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-336">Input Parameters</span></span>

- <span data-ttu-id="1045a-337">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-337">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-338">**link_down_callback**: puntero de función de notificación de inactividad del vínculo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1045a-338">**link_down_callback**: Application’s link down notification function pointer.</span></span> <span data-ttu-id="1045a-339">Si es NULL, se deshabilita la notificación de inactividad del vínculo.</span><span class="sxs-lookup"><span data-stu-id="1045a-339">If NULL, link down notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-340">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-340">Return Values</span></span>

- <span data-ttu-id="1045a-341">**NX_SUCCESS**: (0x00) devolución de llamada de notificación de vínculo inactivo registrada correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-341">**NX_SUCCESS**: (0x00) Successful link down notification callback registration.</span></span>
- <span data-ttu-id="1045a-342">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-342">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-343">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-343">Allowed From</span></span>

<span data-ttu-id="1045a-344">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="1045a-344">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="1045a-345">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-345">Example</span></span>

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a><span data-ttu-id="1045a-346">nx_ppp_link_up_notify</span><span class="sxs-lookup"><span data-stu-id="1045a-346">nx_ppp_link_up_notify</span></span>

<span data-ttu-id="1045a-347">Notificar a la aplicación la actividad del vínculo</span><span class="sxs-lookup"><span data-stu-id="1045a-347">Notify application on link up</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-348">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-348">Prototype</span></span>

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a><span data-ttu-id="1045a-349">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-349">Description</span></span>

<span data-ttu-id="1045a-350">Este servicio registra la devolución de llamada de notificación de actividad del vínculo de la aplicación con la instancia de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="1045a-350">This service registers the application’s link up notification callback with the specified PPP instance.</span></span> <span data-ttu-id="1045a-351">Si no es NULL, se llama a la función de devolución de llamada de actividad del vínculo de la aplicación cuando el vínculo vuelve a funcionar.</span><span class="sxs-lookup"><span data-stu-id="1045a-351">If non-NULL, the application’s link up callback function is called whenever the link comes up.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-352">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-352">Input Parameters</span></span>

- <span data-ttu-id="1045a-353">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-353">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-354">**link_up_callback**: puntero de función de notificación de actividad del vínculo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1045a-354">**link_up_callback**: Application’s link up notification function pointer.</span></span> <span data-ttu-id="1045a-355">Si es NULL, se deshabilita la notificación de actividad del vínculo.\*\*</span><span class="sxs-lookup"><span data-stu-id="1045a-355">If NULL, link up notification is disabled.\*\*</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-356">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-356">Return Values</span></span>

- <span data-ttu-id="1045a-357">**NX_SUCCESS**: (0x00) devolución de llamada de notificación de vínculo activo registrada correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-357">**NX_SUCCESS**: (0x00) Successful link up notification callback registration.</span></span>
- <span data-ttu-id="1045a-358">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-358">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-359">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-359">Allowed From</span></span>

<span data-ttu-id="1045a-360">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="1045a-360">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="1045a-361">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-361">Example</span></span>

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a><span data-ttu-id="1045a-362">nx_ppp_nak_authentication_notify</span><span class="sxs-lookup"><span data-stu-id="1045a-362">nx_ppp_nak_authentication_notify</span></span>

<span data-ttu-id="1045a-363">Notificar a la aplicación si se ha recibido un NAK de autenticación</span><span class="sxs-lookup"><span data-stu-id="1045a-363">Notify application if authentication NAK received</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-364">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-364">Prototype</span></span>

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a><span data-ttu-id="1045a-365">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-365">Description</span></span>

<span data-ttu-id="1045a-366">Este servicio registra la devolución de llamada de notificación del NAK de autenticación de la aplicación con la instancia de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="1045a-366">This service registers the application’s authentication nak notification callback with the specified PPP instance.</span></span> <span data-ttu-id="1045a-367">Si no es NULL, se llama a esta función de devolución de llamada siempre que la instancia de PPP recibe un NAK durante la autenticación.</span><span class="sxs-lookup"><span data-stu-id="1045a-367">If non-NULL, this callback function is called whenever the PPP instance receives a NAK during authentiaction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-368">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-368">Input Parameters</span></span>

- <span data-ttu-id="1045a-369">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-369">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-370">**nak_authentication_notify**: Puntero a la función a la que se llama cuando la instancia de PPP recibe un NAK de autenticación.</span><span class="sxs-lookup"><span data-stu-id="1045a-370">**nak_authentication_notify**: Pointer to function called when the PPP instance receives an authentication NAK.</span></span> <span data-ttu-id="1045a-371">Si es NULL, la notificación se deshabilita.</span><span class="sxs-lookup"><span data-stu-id="1045a-371">If NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-372">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-372">Return Values</span></span>

- <span data-ttu-id="1045a-373">**NX_SUCCESS**: (0x00) devolución de llamada de notificación registrada correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-373">**NX_SUCCESS**: (0x00) Successful notification callback registration.</span></span>
- <span data-ttu-id="1045a-374">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-374">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-375">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-375">Allowed From</span></span>

<span data-ttu-id="1045a-376">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="1045a-376">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="1045a-377">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-377">Example</span></span>

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a><span data-ttu-id="1045a-378">nx_ppp_pap_enable</span><span class="sxs-lookup"><span data-stu-id="1045a-378">nx_ppp_pap_enable</span></span>

<span data-ttu-id="1045a-379">Habilitar la autenticación PAP</span><span class="sxs-lookup"><span data-stu-id="1045a-379">Enable PAP Authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-380">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-380">Prototype</span></span>

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a><span data-ttu-id="1045a-381">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-381">Description</span></span>

<span data-ttu-id="1045a-382">Este servicio habilita el Protocolo de autenticación de contraseña (PAP) para la instancia de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="1045a-382">This service enables the Password Authentication Protocol (PAP) for the specified PPP instance.</span></span> <span data-ttu-id="1045a-383">Si se especifica el puntero de función "***verify_login***", esta instancia de PPP requiere PAP.</span><span class="sxs-lookup"><span data-stu-id="1045a-383">If the “***verify_login***” function pointer is specified, PAP is required by this PPP instance.</span></span> <span data-ttu-id="1045a-384">De lo contrario, PAP solo responde a los requisitos de PAP del elemento del mismo nivel que se especifican durante la negociación de LCP.</span><span class="sxs-lookup"><span data-stu-id="1045a-384">Otherwise, PAP only responds to the peer’s PAP requirements as specified during LCP negotiation.</span></span>

<span data-ttu-id="1045a-385">Hay varios elementos de datos a los que se hace referencia a continuación en las funciones de devolución de llamada necesarias.</span><span class="sxs-lookup"><span data-stu-id="1045a-385">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="1045a-386">Se espera que el elemento de datos *name* sea una cadena terminada en NULL con un tamaño máximo de NX_PPP_NAME_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="1045a-386">The data item *name* is expected to be NULL-terminated string with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="1045a-387">Se espera que el elemento de datos *password* sea una cadena terminada en NULL con un tamaño máximo de NX_PPP_PASSWORD_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="1045a-387">The data item *password* is also expected to be a NULL-terminated string with a maximum size of NX_PPP_PASSWORD_SIZE-1.</span></span>

>[!NOTE]
> <span data-ttu-id="1045a-388">Se debe llamar a esta función después de *nx_ppp_create*, pero antes de *nx_ip_create* o *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="1045a-388">This function must be called after *nx_ppp_create* but before *nx_ip_create* or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-389">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-389">Input Parameters</span></span>

- <span data-ttu-id="1045a-390">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-390">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-391">**generate_login**: puntero a la función de aplicación que genera un elemento *name* y *password* para la autenticación por parte del elemento del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-391">**generate_login**: Pointer to application function that produces a *name* and *password* for authentication by the peer.</span></span> <span data-ttu-id="1045a-392">Tenga en cuenta que los valores de *name* y *password* deben copiarse en los destinos proporcionados.</span><span class="sxs-lookup"><span data-stu-id="1045a-392">Note that the *name* and *password* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="1045a-393">**generate_login**: Puntero a la función de aplicación que verifica los elementos *name* y *password* proporcionados por el elemento del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="1045a-393">**verify_login**: Pointer to application function that verifies the *name* and *password* supplied by the peer.</span></span> <span data-ttu-id="1045a-394">Esta rutina debe comparar los elementos *name* y *password* proporcionados.</span><span class="sxs-lookup"><span data-stu-id="1045a-394">This routine must compare the supplied *name* and *password*.</span></span> <span data-ttu-id="1045a-395">Si esta rutina devuelve NX_SUCCESS, los elementos name y password son correctos y PPP puede continuar con el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="1045a-395">If this routine returns NX_SUCCESS, the name and password are correct and PPP can proceed to the next step.</span></span> <span data-ttu-id="1045a-396">De lo contrario, esta rutina devuelve NX_PPP_ERROR y PPP simplemente espera otro nombre y contraseña.</span><span class="sxs-lookup"><span data-stu-id="1045a-396">Otherwise, this routine returns NX_PPP_ERROR and PPP simply waits for another name and password.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-397">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-397">Return Values</span></span>

- <span data-ttu-id="1045a-398">**NX_SUCCESS** (0x00) PAP de PPP habilitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-398">**NX_SUCCESS**: (0x00) Successful PPP PAP enable.</span></span>
- <span data-ttu-id="1045a-399">**NX_NOT_IMPLEMENTED**: (0x80) La lógica de PAP se deshabilitó a través de NX_PPP_DISABLE_PAP.</span><span class="sxs-lookup"><span data-stu-id="1045a-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP logic was disabled via NX_PPP_DISABLE_PAP.</span></span>
- <span data-ttu-id="1045a-400">NX_PTR_ERROR: (0x07) puntero de PPP o puntero de función de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-400">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="1045a-401">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-401">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-402">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-402">Allowed From</span></span>

<span data-ttu-id="1045a-403">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-403">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-404">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-404">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a><span data-ttu-id="1045a-405">nx_ppp_ping_request</span><span class="sxs-lookup"><span data-stu-id="1045a-405">nx_ppp_ping_request</span></span>

<span data-ttu-id="1045a-406">Enviar una solicitud de ping de LCP</span><span class="sxs-lookup"><span data-stu-id="1045a-406">Send an LCP ping request</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-407">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-407">Prototype</span></span>

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a><span data-ttu-id="1045a-408">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-408">Description</span></span>

<span data-ttu-id="1045a-409">Este servicio envía una solicitud de ping de LCP y establece una marca que indica que el dispositivo PPP está esperando una respuesta de eco.</span><span class="sxs-lookup"><span data-stu-id="1045a-409">This service sends an LCP ping request and sets a flag that the PPP device is waiting for an echo response.</span></span> <span data-ttu-id="1045a-410">El servicio vuelve en cuanto se envía la solicitud.</span><span class="sxs-lookup"><span data-stu-id="1045a-410">The service returns as soon as the request is sent.</span></span> <span data-ttu-id="1045a-411">No espera una respuesta.</span><span class="sxs-lookup"><span data-stu-id="1045a-411">It does not wait for a response.</span></span> 

<span data-ttu-id="1045a-412">Cuando se recibe una respuesta de eco coincidente, la tarea de subprocesos de PPP borrará la marca.</span><span class="sxs-lookup"><span data-stu-id="1045a-412">When a matching echo response is received, the PPP thread task will clear the flag.</span></span> <span data-ttu-id="1045a-413">El dispositivo de PPP debe haber completado la parte de LCP de la negociación de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-413">The PPP device must have completed the LCP part of the PPP negotiation.</span></span>

<span data-ttu-id="1045a-414">Este servicio es útil para las configuraciones PPP en las que no es posible sondear el hardware para conocer el estado del vínculo.</span><span class="sxs-lookup"><span data-stu-id="1045a-414">This service is useful for PPP set ups where polling the hardware for link status may not be readily possible.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-415">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-415">Input Parameters</span></span>

- <span data-ttu-id="1045a-416">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-416">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-417">**data**: puntero a los datos que se van a enviar en la solicitud de eco.</span><span class="sxs-lookup"><span data-stu-id="1045a-417">**data**: Pointer to data to send in echo request.</span></span>
- <span data-ttu-id="1045a-418">**data_size**: tamaño de los datos que se van a enviar wait_option Tiempo de espera para enviar el mensaje de eco de LCP.</span><span class="sxs-lookup"><span data-stu-id="1045a-418">**data_size**: Size of data to send wait_option Time to wait to send the LCP echo message.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-419">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-419">Return Values</span></span>

- <span data-ttu-id="1045a-420">**NX_SUCCESS**: (0x00) solicitud de eco enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-420">**NX_SUCCESS**: (0x00) Successful sent echo request.</span></span>
- <span data-ttu-id="1045a-421">**NX_PPP_NOT_ESTABLISHED**: (0xB5) conexión de PPP no establecida.</span><span class="sxs-lookup"><span data-stu-id="1045a-421">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP connection not established.</span></span>
- <span data-ttu-id="1045a-422">NX_PTR_ERROR: (0x07) puntero de PPP o puntero de función de aplicación no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-422">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="1045a-423">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-423">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-424">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-424">Allowed From</span></span>

<span data-ttu-id="1045a-425">Subprocesos de aplicación</span><span class="sxs-lookup"><span data-stu-id="1045a-425">Application threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-426">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-426">Example</span></span>

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  strlen("username ");

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a><span data-ttu-id="1045a-427">nx_ppp_raw_string_send</span><span class="sxs-lookup"><span data-stu-id="1045a-427">nx_ppp_raw_string_send</span></span>

<span data-ttu-id="1045a-428">Enviar una cadena de ASCII sin formato</span><span class="sxs-lookup"><span data-stu-id="1045a-428">Send a raw ASCII string</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-429">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-429">Prototype</span></span>

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a><span data-ttu-id="1045a-430">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-430">Description</span></span>

<span data-ttu-id="1045a-431">Este servicio envía una cadena de ASCII que no es de PPP directamente a la interfaz de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-431">This service sends a non-PPP ASCII string directly out the PPP interface.</span></span> <span data-ttu-id="1045a-432">Normalmente se utiliza después de que PPP reciba un paquete que no es de PPP y que contenga información de control de módem.</span><span class="sxs-lookup"><span data-stu-id="1045a-432">It is typically used after PPP receives a non-PPP packet that contains modem control information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-433">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-433">Input Parameters</span></span>

- <span data-ttu-id="1045a-434">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-434">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-435">**string_ptr**: puntero a la cadena que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="1045a-435">**string_ptr**: Pointer to string to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-436">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-436">Return Values</span></span>

- <span data-ttu-id="1045a-437">**NX_SUCCESS**: (0x00) cadena sin formato de PPP enviada correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-437">**NX_SUCCESS**: (0x00) Successful PPP raw string send.</span></span>
- <span data-ttu-id="1045a-438">NX_PTR_ERROR: (0x07) puntero PPP o puntero de cadena no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-438">NX_PTR_ERROR: (0x07) Invalid PPP pointer or string pointer.</span></span>
- <span data-ttu-id="1045a-439">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-439">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-440">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-440">Allowed From</span></span>

<span data-ttu-id="1045a-441">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-442">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-442">Example</span></span>

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a><span data-ttu-id="1045a-443">nx_ppp_restart</span><span class="sxs-lookup"><span data-stu-id="1045a-443">nx_ppp_restart</span></span>

<span data-ttu-id="1045a-444">Reiniciar el procesamiento de PPP</span><span class="sxs-lookup"><span data-stu-id="1045a-444">Restart PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-445">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-445">Prototype</span></span>

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="1045a-446">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-446">Description</span></span>

<span data-ttu-id="1045a-447">Este servicio reinicia el procesamiento de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-447">This service restarts the PPP processing.</span></span> <span data-ttu-id="1045a-448">Normalmente se le llama cuando es necesario restablecer el vínculo, ya sea desde una devolución de llamada de inactividad del vínculo o por un mensaje de módem que no es de PPP que indica que se perdió la comunicación.</span><span class="sxs-lookup"><span data-stu-id="1045a-448">It is typically called when the link needs to be re-established either from a link down callback or by a non-PPP modem message indicating communication was lost.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-449">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-449">Input Parameters</span></span>

- <span data-ttu-id="1045a-450">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-450">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-451">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-451">Return Values</span></span>

- <span data-ttu-id="1045a-452">**NX_SUCCESS**: (0x00) reinicio de PPP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-452">**NX_SUCCESS**: (0x00) Successful PPP restart initiated.</span></span>
- <span data-ttu-id="1045a-453">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-453">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="1045a-454">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-454">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-455">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-455">Allowed From</span></span>

<span data-ttu-id="1045a-456">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-456">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-457">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-457">Example</span></span>

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a><span data-ttu-id="1045a-458">nx_ppp_start</span><span class="sxs-lookup"><span data-stu-id="1045a-458">nx_ppp_start</span></span>

<span data-ttu-id="1045a-459">Iniciar el procesamiento de PPP</span><span class="sxs-lookup"><span data-stu-id="1045a-459">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-460">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-460">Prototype</span></span>

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="1045a-461">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-461">Description</span></span>

<span data-ttu-id="1045a-462">Este servicio inicia el procesamiento de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-462">This service starts the PPP processing.</span></span> <span data-ttu-id="1045a-463">Normalmente se le llama después de llamar a nx_ppp_stop ().</span><span class="sxs-lookup"><span data-stu-id="1045a-463">It is typically called after nx_ppp_stop() called.</span></span>

>[!NOTE]
> <span data-ttu-id="1045a-464">PPP inicia automáticamente el procesamiento de PPP cuando el vínculo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="1045a-464">PPP automatically starts the PPP processing when the link is enabled.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-465">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-465">Input Parameters</span></span>

- <span data-ttu-id="1045a-466">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-466">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-467">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-467">Return Values</span></span>

- <span data-ttu-id="1045a-468">**NX_SUCCESS**: (0x00) inicio de PPP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-468">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="1045a-469">**NX_PPP_ALREADY_STARTED**: (0XB9) PPP ya iniciado.</span><span class="sxs-lookup"><span data-stu-id="1045a-469">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP already started.</span></span>
- <span data-ttu-id="1045a-470">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-470">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="1045a-471">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-471">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-472">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-472">Allowed From</span></span>

<span data-ttu-id="1045a-473">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-473">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-474">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-474">Example</span></span>

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a><span data-ttu-id="1045a-475">nx_ppp_status_get</span><span class="sxs-lookup"><span data-stu-id="1045a-475">nx_ppp_status_get</span></span>

<span data-ttu-id="1045a-476">Obtener el estado actual de PPP</span><span class="sxs-lookup"><span data-stu-id="1045a-476">Get current PPP status</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-477">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-477">Prototype</span></span>

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a><span data-ttu-id="1045a-478">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-478">Description</span></span>

<span data-ttu-id="1045a-479">Este servicio obtiene el estado actual de la instancia de PPP especificada.</span><span class="sxs-lookup"><span data-stu-id="1045a-479">This service gets the current status of the specified PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-480">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-480">Input Parameters</span></span>

- <span data-ttu-id="1045a-481">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-481">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-482">**status_ptr**: destino del estado de PPP, los valores de estado posibles son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="1045a-482">**status_ptr**: Destination for the PPP status, the following are possible status values:</span></span>
    - <span data-ttu-id="1045a-483">**NX_PPP_STATUS_ESTABLISHED**</span><span class="sxs-lookup"><span data-stu-id="1045a-483">**NX_PPP_STATUS_ESTABLISHED**</span></span>
    - <span data-ttu-id="1045a-484">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="1045a-484">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="1045a-485">**NX_PPP_STATUS_LCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="1045a-485">**NX_PPP_STATUS_LCP_FAILED**</span></span>
    - <span data-ttu-id="1045a-486">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="1045a-486">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="1045a-487">**NX_PPP_STATUS_PAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="1045a-487">**NX_PPP_STATUS_PAP_FAILED**</span></span>
    - <span data-ttu-id="1045a-488">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="1045a-488">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="1045a-489">**NX_PPP_STATUS_CHAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="1045a-489">**NX_PPP_STATUS_CHAP_FAILED**</span></span>
    - <span data-ttu-id="1045a-490">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="1045a-490">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="1045a-491">**NX_PPP_STATUS_IPCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="1045a-491">**NX_PPP_STATUS_IPCP_FAILED**</span></span>

>[!NOTE]
> <span data-ttu-id="1045a-492">El estado solo es válido si la API devuelve NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="1045a-492">The status is only valid if the API returns NX_SUCCESS.</span></span> <span data-ttu-id="1045a-493">Además, si se devuelve cualquiera de los valores de estado \*_FAILED, el procesamiento de PPP se detiene eficazmente hasta que la aplicación vuelva a iniciarlo.</span><span class="sxs-lookup"><span data-stu-id="1045a-493">In addition, if any of the \*_FAILED status values are returned, PPP processing is effectively stopped until it is restarted again by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-494">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-494">Return Values</span></span>

- <span data-ttu-id="1045a-495">**NX_SUCCESS**: (0x00) estado de PPP solicitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-495">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="1045a-496">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-496">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-497">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-497">Allowed From</span></span>

<span data-ttu-id="1045a-498">Inicialización, subprocesos, temporizadores e ISR</span><span class="sxs-lookup"><span data-stu-id="1045a-498">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="1045a-499">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-499">Example</span></span>

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a><span data-ttu-id="1045a-500">nx_ppp_stop</span><span class="sxs-lookup"><span data-stu-id="1045a-500">nx_ppp_stop</span></span>

<span data-ttu-id="1045a-501">Iniciar el procesamiento de PPP</span><span class="sxs-lookup"><span data-stu-id="1045a-501">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-502">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-502">Prototype</span></span>

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="1045a-503">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-503">Description</span></span>

<span data-ttu-id="1045a-504">Este servicio detiene el procesamiento de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-504">This service stops the PPP processing.</span></span> <span data-ttu-id="1045a-505">El usuario también puede llamar a nx_ppp_start () para iniciar el procesamiento de PPP, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="1045a-505">User also can calls nx_ppp_start() to start the PPP processing if needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-506">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-506">Input Parameters</span></span>

- <span data-ttu-id="1045a-507">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-507">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-508">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-508">Return Values</span></span>

- <span data-ttu-id="1045a-509">**NX_SUCCESS**: (0x00) inicio de PPP iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-509">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="1045a-510">**NX_PPP_ALREADY_STOPPED**: (0XB8) PPP ya está detenido.</span><span class="sxs-lookup"><span data-stu-id="1045a-510">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP already stopped.</span></span>
- <span data-ttu-id="1045a-511">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-511">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="1045a-512">NX_CALLER_ERROR: (0x11) autor de llamada no válido de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1045a-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-513">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-513">Allowed From</span></span>

<span data-ttu-id="1045a-514">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-515">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-515">Example</span></span>

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a><span data-ttu-id="1045a-516">nx_ppp_packet_receive</span><span class="sxs-lookup"><span data-stu-id="1045a-516">nx_ppp_packet_receive</span></span>

<span data-ttu-id="1045a-517">Recibir paquete de PPP</span><span class="sxs-lookup"><span data-stu-id="1045a-517">Receive PPP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-518">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-518">Prototype</span></span>

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="1045a-519">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-519">Description</span></span>

<span data-ttu-id="1045a-520">Este servicio recibe el paquete de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-520">This service receives PPP packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-521">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-521">Input Parameters</span></span>

- <span data-ttu-id="1045a-522">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-522">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-523">**packet_ptr**: puntero al paquete de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-523">**packet_ptr**: Pointer to PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-524">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-524">Return Values</span></span>

- <span data-ttu-id="1045a-525">**NX_SUCCESS**: (0x00) estado de PPP solicitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-525">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="1045a-526">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-526">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-527">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-527">Allowed From</span></span>

<span data-ttu-id="1045a-528">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-528">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-529">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-529">Example</span></span>

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a><span data-ttu-id="1045a-530">nx_ppp_packet_send_set</span><span class="sxs-lookup"><span data-stu-id="1045a-530">nx_ppp_packet_send_set</span></span>

<span data-ttu-id="1045a-531">Establecer la función de envío de paquetes de PPP</span><span class="sxs-lookup"><span data-stu-id="1045a-531">Set the PPP packet send function</span></span>

### <a name="prototype"></a><span data-ttu-id="1045a-532">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1045a-532">Prototype</span></span>

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a><span data-ttu-id="1045a-533">Descripción</span><span class="sxs-lookup"><span data-stu-id="1045a-533">Description</span></span>

<span data-ttu-id="1045a-534">Este servicio establece la función de envío de paquetes de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-534">This service sets the PPP packet send funciton.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1045a-535">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="1045a-535">Input Parameters</span></span>

- <span data-ttu-id="1045a-536">**ppp_ptr**: puntero al bloque de control de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-536">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="1045a-537">**nx_ppp_packet_send**: rutina para enviar el paquete de PPP.</span><span class="sxs-lookup"><span data-stu-id="1045a-537">**nx_ppp_packet_send**: Routine to send PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="1045a-538">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="1045a-538">Return Values</span></span>

- <span data-ttu-id="1045a-539">**NX_SUCCESS**: (0x00) estado de PPP solicitado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1045a-539">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="1045a-540">NX_PTR_ERROR: (0x07) puntero de PPP no válido.</span><span class="sxs-lookup"><span data-stu-id="1045a-540">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1045a-541">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="1045a-541">Allowed From</span></span>

<span data-ttu-id="1045a-542">Inicialización, subprocesos</span><span class="sxs-lookup"><span data-stu-id="1045a-542">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="1045a-543">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1045a-543">Example</span></span>

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```