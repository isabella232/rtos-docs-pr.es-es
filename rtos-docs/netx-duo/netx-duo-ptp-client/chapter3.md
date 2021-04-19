---
title: 'Capítulo 3: Descripción de los servicios del cliente PTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del cliente PTP de NetX Duo por orden alfabético.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814589"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a><span data-ttu-id="ece05-103">Capítulo 3: Descripción de los servicios del cliente PTP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ece05-103">Chapter 3 - Description of Azure RTOS NetX Duo PTP Client Services</span></span>

<span data-ttu-id="ece05-104">Este capítulo contiene una descripción de todos los servicios del cliente PTP de NetX Duo (se enumeran a continuación) por orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="ece05-104">This chapter contains a description of all NetX Duo PTP client services (listed below) in alphabetical order.</span></span>

[!NOTE]
> <span data-ttu-id="ece05-105">*En la sección **Valores devueltos** de las siguientes descripciones de funciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.*</span><span class="sxs-lookup"><span data-stu-id="ece05-105">*In the **Return Values** section in the following API function descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.*</span></span>

## <a name="nx_ptp_client_create"></a><span data-ttu-id="ece05-106">nx_ptp_client_create</span><span class="sxs-lookup"><span data-stu-id="ece05-106">nx_ptp_client_create</span></span>

<span data-ttu-id="ece05-107">Cree una instancia de cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-107">Create a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-108">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-108">Prototype</span></span>

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a><span data-ttu-id="ece05-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-109">Description</span></span>

<span data-ttu-id="ece05-110">Este servicio crea una instancia de cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-110">This service creates an instance of the PTP client.</span></span>

<span data-ttu-id="ece05-111">Tenga en cuenta que la aplicación debe crear primero una instancia de IP y un grupo de paquetes para que el cliente PTP transmita paquetes.</span><span class="sxs-lookup"><span data-stu-id="ece05-111">Note that the  application must first create an IP instance and a packet pool for the PTP client to transmit packets.</span></span> <span data-ttu-id="ece05-112">En el caso del grupo de paquetes, la aplicación puede usar el mismo grupo de paquetes en la instancia de IP; o bien, puede crear un grupo de paquetes dedicado para el cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-112">For the packet pool, application may use the same packet pool in the IP instance; or it can create a dedicated packet pool for PTP client.</span></span>  <span data-ttu-id="ece05-113">La estrategia de usar un grupo de paquetes dedicado tiene la ventaja de usar paquetes pequeños (paquetes de 128 bytes si se usa IPv6, o 108 bytes para IPv4 solamente).</span><span class="sxs-lookup"><span data-stu-id="ece05-113">The dedicated packet pool approach has the advantage of using small packets (128 bytes packets if IPv6 is used, or 108 bytes for IPv4-only).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-114">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-114">Input Parameters</span></span>
* <span data-ttu-id="ece05-115">**client_ptr** Puntero al cliente PTP que se va a crear</span><span class="sxs-lookup"><span data-stu-id="ece05-115">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="ece05-116">**ip_ptr** Puntero a la instancia de IP</span><span class="sxs-lookup"><span data-stu-id="ece05-116">**ip_ptr** Pointer to IP instance</span></span>
* <span data-ttu-id="ece05-117">**interface_index** Índice de la interfaz de red PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-117">**interface_index** Index of PTP network interface</span></span>
* <span data-ttu-id="ece05-118">**packet_pool_ptr** Puntero al grupo de paquetes del cliente</span><span class="sxs-lookup"><span data-stu-id="ece05-118">**packet_pool_ptr** Pointer to client packet pool</span></span>
* <span data-ttu-id="ece05-119">**thread_priority** Prioridad del subproceso PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-119">**thread_priority**  Priority of PTP thread</span></span>
* <span data-ttu-id="ece05-120">**thread_stack** Puntero a la pila de subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-120">**thread_stack** Pointer to thread stack</span></span>
* <span data-ttu-id="ece05-121">**stack_size** Tamaño de la pila de subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-121">**stack_size** Size of thread stack</span></span>
* <span data-ttu-id="ece05-122">**clock_callback** Devolución de llamada del reloj PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-122">**clock_callback** PTP clock callback</span></span>
* <span data-ttu-id="ece05-123">**clock_callback_data** Datos de la devolución de llamada del reloj</span><span class="sxs-lookup"><span data-stu-id="ece05-123">**clock_callback_data** Data for the clock callback</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-124">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-124">Return Values</span></span>
* <span data-ttu-id="ece05-125">**NX_SUCCESS** (0x00) El cliente se creó correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="ece05-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) La carga útil del paquete es demasiado pequeña</span><span class="sxs-lookup"><span data-stu-id="ece05-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Packet payload too small</span></span>
* <span data-ttu-id="ece05-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Error de devolución de llamada del reloj</span><span class="sxs-lookup"><span data-stu-id="ece05-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Failure on clock callback</span></span>
* <span data-ttu-id="ece05-128">**status** Finalización del estado de las llamadas al servicio NetX Duo y ThreadX</span><span class="sxs-lookup"><span data-stu-id="ece05-128">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="ece05-129">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-129">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
* <span data-ttu-id="ece05-130">NX_INVALID_INTERFACE (0x4C) Interfaz no válida</span><span class="sxs-lookup"><span data-stu-id="ece05-130">NX_INVALID_INTERFACE (0x4C) Invalid interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-131">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-131">Allowed From</span></span>
<span data-ttu-id="ece05-132">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-133">Example</span></span>
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a><span data-ttu-id="ece05-134">nx_ptp_client_delete</span><span class="sxs-lookup"><span data-stu-id="ece05-134">nx_ptp_client_delete</span></span>

<span data-ttu-id="ece05-135">Elimina una instancia de cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-135">Deletes a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-136">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-136">Prototype</span></span>

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="ece05-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-137">Description</span></span>

<span data-ttu-id="ece05-138">Este servicio elimina una instancia de cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-138">This service deletes an instance of the PTP client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-139">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-139">Input Parameters</span></span>
* <span data-ttu-id="ece05-140">**client_ptr** Puntero al cliente PTP que se va a eliminar</span><span class="sxs-lookup"><span data-stu-id="ece05-140">**client_ptr** Pointer to PTP client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-141">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-141">Return Values</span></span>
* <span data-ttu-id="ece05-142">**NX_SUCCESS** (0x00) Cliente eliminado correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-142">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
* <span data-ttu-id="ece05-143">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-143">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-144">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-144">Allowed From</span></span>
<span data-ttu-id="ece05-145">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-145">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-146">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-146">Example</span></span>
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a><span data-ttu-id="ece05-147">nx_ptp_client_master_info_get</span><span class="sxs-lookup"><span data-stu-id="ece05-147">nx_ptp_client_master_info_get</span></span>

<span data-ttu-id="ece05-148">Obtenga la información del reloj principal.</span><span class="sxs-lookup"><span data-stu-id="ece05-148">Get master clock information.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-149">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-149">Prototype</span></span>

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a><span data-ttu-id="ece05-150">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-150">Description</span></span>
<span data-ttu-id="ece05-151">Este servicio obtiene información del reloj principal.</span><span class="sxs-lookup"><span data-stu-id="ece05-151">This service gets information of master clock.</span></span> <span data-ttu-id="ece05-152">El bloque de control principal se pasa a la aplicación de usuario a través de la función de devolución de llamada del evento.</span><span class="sxs-lookup"><span data-stu-id="ece05-152">The master control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-153">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-153">Input Parameters</span></span>
* <span data-ttu-id="ece05-154">**master_ptr** Puntero al reloj PTP principal</span><span class="sxs-lookup"><span data-stu-id="ece05-154">**master_ptr** Pointer to PTP master clock</span></span>
* <span data-ttu-id="ece05-155">**address** Dirección del reloj principal</span><span class="sxs-lookup"><span data-stu-id="ece05-155">**address** Address of master clock</span></span>
* <span data-ttu-id="ece05-156">**port_identity** Identidad y puerto principal PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-156">**port_identity** PTP master port and identity</span></span>
* <span data-ttu-id="ece05-157">**port_identity_length** Longitud de la identidad y el puerto principal PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-157">**port_identity_length** Length of PTP master port and identity</span></span>
* <span data-ttu-id="ece05-158">**priority1** Prioridad 1 del reloj PTP principal</span><span class="sxs-lookup"><span data-stu-id="ece05-158">**priority1** Priority1 of PTP master clock</span></span>
* <span data-ttu-id="ece05-159">**priority2** Prioridad 2 del reloj PTP principal</span><span class="sxs-lookup"><span data-stu-id="ece05-159">**priority2** Priority2 of PTP master clock</span></span>
* <span data-ttu-id="ece05-160">**clock_class** Clase del reloj PTP principal</span><span class="sxs-lookup"><span data-stu-id="ece05-160">**clock_class** Class of PTP master clock</span></span>
* <span data-ttu-id="ece05-161">**clock_accuracy** Precisión del reloj PTP principal</span><span class="sxs-lookup"><span data-stu-id="ece05-161">**clock_accuracy** Accuracy of PTP master clock</span></span>
* <span data-ttu-id="ece05-162">**clock_variance** Varianza del reloj PTP principal</span><span class="sxs-lookup"><span data-stu-id="ece05-162">**clock_variance** Variance of PTP master clock</span></span>
* <span data-ttu-id="ece05-163">**grandmaster_identity** Identidad del reloj Grandmaster</span><span class="sxs-lookup"><span data-stu-id="ece05-163">**grandmaster_identity** Identity of grandmaster clock</span></span>
* <span data-ttu-id="ece05-164">**grandmaster_identity_length** Longitud de la identidad de Grandmaster</span><span class="sxs-lookup"><span data-stu-id="ece05-164">**grandmaster_identity_length** Length of grandmaster Identity</span></span>
* <span data-ttu-id="ece05-165">**steps_removed** Etapas eliminadas del encabezado PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-165">**steps_removed** Steps removed from PTP header</span></span>
* <span data-ttu-id="ece05-166">**time_source** El origen del que usa el reloj Grandmaster</span><span class="sxs-lookup"><span data-stu-id="ece05-166">**time_source** The source of timer used by grandmaster clock</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-167">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-167">Return Values</span></span>
* <span data-ttu-id="ece05-168">**NX_SUCCESS** (0X00) Información del reloj principal obtenida correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-168">**NX_SUCCESS** (0x00) Get master clock information successfully</span></span>
* <span data-ttu-id="ece05-169">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-169">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-170">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-170">Allowed From</span></span>
<span data-ttu-id="ece05-171">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-172">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-172">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a><span data-ttu-id="ece05-173">nx_ptp_client_packet_timestamp_notify</span><span class="sxs-lookup"><span data-stu-id="ece05-173">nx_ptp_client_packet_timestamp_notify</span></span>

<span data-ttu-id="ece05-174">Notifique al cliente PTP la marca de tiempo del paquete.</span><span class="sxs-lookup"><span data-stu-id="ece05-174">Notify PTP client the timestamp of the packet.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-175">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-175">Prototype</span></span>

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a><span data-ttu-id="ece05-176">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-176">Description</span></span>
<span data-ttu-id="ece05-177">Este servicio notifica al cliente PTP que el paquete se transmitió con una marca de tiempo.</span><span class="sxs-lookup"><span data-stu-id="ece05-177">This service notifies the PTP client that packet is transmitted with timestamp.</span></span> <span data-ttu-id="ece05-178">Este servicio está diseñado para el controlador de red y se invoca cuando se transmite el paquete.</span><span class="sxs-lookup"><span data-stu-id="ece05-178">This service is designed for network driver and invoked when the packet is transmitted.</span></span> <span data-ttu-id="ece05-179">Normalmente, la marca de tiempo se genera mediante hardware.</span><span class="sxs-lookup"><span data-stu-id="ece05-179">The timestamp is usually generated by hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-180">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-180">Input Parameters</span></span>
* <span data-ttu-id="ece05-181">**client_ptr** Puntero al cliente PTP que se va a crear</span><span class="sxs-lookup"><span data-stu-id="ece05-181">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="ece05-182">**packet_ptr** Puntero al paquete PTP que se transmitirá</span><span class="sxs-lookup"><span data-stu-id="ece05-182">**packet_ptr** Pointer to PTP packet that is transmitted</span></span>
* <span data-ttu-id="ece05-183">**timestamp_ptr** Puntero a la marca de tiempo del paquete PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-183">**timestamp_ptr** Pointer to timestamp of PTP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-184">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-184">Return Values</span></span>
<span data-ttu-id="ece05-185">Ninguno</span><span class="sxs-lookup"><span data-stu-id="ece05-185">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-186">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-186">Allowed From</span></span>
<span data-ttu-id="ece05-187">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-187">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-188">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-188">Example</span></span>
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a><span data-ttu-id="ece05-189">nx_ptp_client_soft_clock_callback</span><span class="sxs-lookup"><span data-stu-id="ece05-189">nx_ptp_client_soft_clock_callback</span></span>

<span data-ttu-id="ece05-190">Implementación de software de un reloj PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-190">Software implementation of a PTP clock.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-191">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-191">Prototype</span></span>

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a><span data-ttu-id="ece05-192">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-192">Description</span></span>
<span data-ttu-id="ece05-193">Esta función de devolución de llamada sirve como un origen de reloj simulado de baja resolución para PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-193">This callback function serves as a simulated low resolution clock source for PTP.</span></span> <span data-ttu-id="ece05-194">Esta rutina se proporciona como referencia y no se puede usar para producción.</span><span class="sxs-lookup"><span data-stu-id="ece05-194">This routine is provided as a reference and cannot be used for production.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-195">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-195">Input Parameters</span></span>
* <span data-ttu-id="ece05-196">**client_ptr** Puntero al cliente PTP que se va a crear</span><span class="sxs-lookup"><span data-stu-id="ece05-196">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="ece05-197">**operation** Operación de devolución de llamada, los valores válidos se definen como:</span><span class="sxs-lookup"><span data-stu-id="ece05-197">**operation** Callback operation, valid values are defined as:</span></span>
  * <span data-ttu-id="ece05-198">**NX_PTP_CLIENT_CLOCK_INIT** Inicializa el reloj.</span><span class="sxs-lookup"><span data-stu-id="ece05-198">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="ece05-199">**NX_PTP_CLIENT_CLOCK_SET** Establece la marca de tiempo actual especificada por `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="ece05-199">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="ece05-200">**NX_PTP_CLIENT_CLOCK_GET** Devuelve la marca de tiempo actual a `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="ece05-200">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="ece05-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extrae la marca de tiempo de `packet_ptr` en `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="ece05-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="ece05-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Ajusta la marca de tiempo actual menos de *1* segundo.</span><span class="sxs-lookup"><span data-stu-id="ece05-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="ece05-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Marque el `packet_ptr` que necesita para notificar al cliente PTP la marca de tiempo cuando se transmita.</span><span class="sxs-lookup"><span data-stu-id="ece05-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="ece05-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Actualiza el temporizador de software.</span><span class="sxs-lookup"><span data-stu-id="ece05-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="ece05-205">El reloj de hardware puede pasarlo por alto.</span><span class="sxs-lookup"><span data-stu-id="ece05-205">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="ece05-206">**time_ptr** Puntero a la marca de tiempo.</span><span class="sxs-lookup"><span data-stu-id="ece05-206">**time_ptr** Pointer to timestamp.</span></span>
* <span data-ttu-id="ece05-207">**packet_ptr** Puntero al paquete.</span><span class="sxs-lookup"><span data-stu-id="ece05-207">**packet_ptr** Pointer to packet.</span></span>
* <span data-ttu-id="ece05-208">**callback_data** Puntero a los datos de devolución de llamada opacos.</span><span class="sxs-lookup"><span data-stu-id="ece05-208">**callback_data** Pointer to opaque callback data.</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-209">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-209">Return Values</span></span>
* <span data-ttu-id="ece05-210">**NX_SUCCESS** (0x00) Operación correcta</span><span class="sxs-lookup"><span data-stu-id="ece05-210">**NX_SUCCESS** (0x00) Operation successfully</span></span>
* <span data-ttu-id="ece05-211">**NX_PTP_PARAM_ERROR** (0xD03) Parámetro no válido</span><span class="sxs-lookup"><span data-stu-id="ece05-211">**NX_PTP_PARAM_ERROR** (0xD03) Invalid parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-212">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-212">Allowed From</span></span>
<span data-ttu-id="ece05-213">PTP interno</span><span class="sxs-lookup"><span data-stu-id="ece05-213">PTP internal</span></span>

### <a name="example"></a><span data-ttu-id="ece05-214">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-214">Example</span></span>
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a><span data-ttu-id="ece05-215">nx_ptp_client_start</span><span class="sxs-lookup"><span data-stu-id="ece05-215">nx_ptp_client_start</span></span>

<span data-ttu-id="ece05-216">Inicie el cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-216">Start PTP client.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-217">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-217">Prototype</span></span>

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a><span data-ttu-id="ece05-218">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-218">Description</span></span>
<span data-ttu-id="ece05-219">Este servicio inicia una instancia de cliente PTP creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ece05-219">This service starts a previously created PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-220">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-220">Input Parameters</span></span>
* <span data-ttu-id="ece05-221">**client_ptr** Puntero al cliente PTP que se va a crear</span><span class="sxs-lookup"><span data-stu-id="ece05-221">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="ece05-222">**client_port_identity_ptr** Puntero a la identidad y al puerto de cliente; puede ser NULL.</span><span class="sxs-lookup"><span data-stu-id="ece05-222">**client_port_identity_ptr** Pointer to client port and identity, it can be NULL</span></span>
* <span data-ttu-id="ece05-223">**client_port_identity_length** Longitud del puerto y la identidad del cliente.</span><span class="sxs-lookup"><span data-stu-id="ece05-223">**client_port_identity_length** Length of client port and identity.</span></span> <span data-ttu-id="ece05-224">Debe ser 0 si client_port_identity_ptr es NULL o NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span><span class="sxs-lookup"><span data-stu-id="ece05-224">It must be 0 if client_port_identity_ptr is NULL or NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span></span>
* <span data-ttu-id="ece05-225">**domain** Dominio del reloj PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-225">**domain** PTP clock domain</span></span>
* <span data-ttu-id="ece05-226">**transport_specific** 4 bits de la dirección de transporte específico</span><span class="sxs-lookup"><span data-stu-id="ece05-226">**transport_specific** 4 bits of transport specific</span></span>
* <span data-ttu-id="ece05-227">**event_callback** Función de devolución de llamada invocada en el evento</span><span class="sxs-lookup"><span data-stu-id="ece05-227">**event_callback** Callback function invoked on event</span></span>
* <span data-ttu-id="ece05-228">**event_callback_data** Datos para la devolución de llamada del evento</span><span class="sxs-lookup"><span data-stu-id="ece05-228">**event_callback_data** Data for the event callback</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-229">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-229">Return Values</span></span>
* <span data-ttu-id="ece05-230">**NX_SUCCESS** (0x00) El cliente se inició correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-230">**NX_SUCCESS** (0x00) Client successfully started</span></span>
* <span data-ttu-id="ece05-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) El cliente PTP ya se ha iniciado</span><span class="sxs-lookup"><span data-stu-id="ece05-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="ece05-232">**status** Finalización del estado de las llamadas al servicio NetX Duo y ThreadX</span><span class="sxs-lookup"><span data-stu-id="ece05-232">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="ece05-233">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-233">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-234">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-234">Allowed From</span></span>
<span data-ttu-id="ece05-235">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-235">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-236">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-236">Example</span></span>
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a><span data-ttu-id="ece05-237">nx_ptp_client_stop</span><span class="sxs-lookup"><span data-stu-id="ece05-237">nx_ptp_client_stop</span></span>

<span data-ttu-id="ece05-238">Detenga el cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-238">Stop PTP client.</span></span>  <span data-ttu-id="ece05-239">Una vez detenido el cliente PTP, no procesará los paquetes PTP ni transmitirá los paquetes PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-239">After the PTP client is stopped, it does not process PTP packets, nor does it transmit PTP packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-240">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-240">Prototype</span></span>

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="ece05-241">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-241">Description</span></span>
<span data-ttu-id="ece05-242">Este servicio detiene una instancia de cliente PTP iniciada y creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ece05-242">This service stops a previously created and started PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-243">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-243">Input Parameters</span></span>
* <span data-ttu-id="ece05-244">**client_ptr** Puntero al cliente PTP que se va a detener</span><span class="sxs-lookup"><span data-stu-id="ece05-244">**client_ptr** Pointer to PTP client to stop</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-245">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-245">Return Values</span></span>
* <span data-ttu-id="ece05-246">**NX_SUCCESS** (0x00) El cliente se detuvo correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-246">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>
* <span data-ttu-id="ece05-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) El cliente no se inició</span><span class="sxs-lookup"><span data-stu-id="ece05-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) Client not started</span></span>
* <span data-ttu-id="ece05-248">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-248">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-249">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-249">Allowed From</span></span>
<span data-ttu-id="ece05-250">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-250">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-251">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-251">Example</span></span>
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a><span data-ttu-id="ece05-252">nx_ptp_client_sync_info_get</span><span class="sxs-lookup"><span data-stu-id="ece05-252">nx_ptp_client_sync_info_get</span></span>

<span data-ttu-id="ece05-253">Obtenga la información de sincronización.</span><span class="sxs-lookup"><span data-stu-id="ece05-253">Get Sync information.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-254">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-254">Prototype</span></span>

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a><span data-ttu-id="ece05-255">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-255">Description</span></span>
<span data-ttu-id="ece05-256">Este servicio obtiene información del mensaje de sincronización.</span><span class="sxs-lookup"><span data-stu-id="ece05-256">This service gets information of Sync message.</span></span> <span data-ttu-id="ece05-257">El bloque de control de sincronización se pasa a la aplicación de usuario a través de la función de devolución de llamada del evento.</span><span class="sxs-lookup"><span data-stu-id="ece05-257">The Sync control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-258">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-258">Input Parameters</span></span>
* <span data-ttu-id="ece05-259">**client_ptr** Puntero al cliente PTP que se va a crear</span><span class="sxs-lookup"><span data-stu-id="ece05-259">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="ece05-260">**flags** Marcas en el mensaje de sincronización</span><span class="sxs-lookup"><span data-stu-id="ece05-260">**flags** Flags in Sync message</span></span>
* <span data-ttu-id="ece05-261">**utc_offset** Desplazamiento entre TAI y UTC</span><span class="sxs-lookup"><span data-stu-id="ece05-261">**utc_offset** Offset between TAI and UTC</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-262">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-262">Return Values</span></span>
* <span data-ttu-id="ece05-263">**NX_SUCCESS** (0X00) La información de sincronización se obtuvo correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-263">**NX_SUCCESS** (0x00) Get Sync information successfully</span></span>
* <span data-ttu-id="ece05-264">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-264">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-265">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-265">Allowed From</span></span>
<span data-ttu-id="ece05-266">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-267">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-267">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a><span data-ttu-id="ece05-268">nx_ptp_client_time_get</span><span class="sxs-lookup"><span data-stu-id="ece05-268">nx_ptp_client_time_get</span></span>

<span data-ttu-id="ece05-269">Obtenga la hora actual.</span><span class="sxs-lookup"><span data-stu-id="ece05-269">Get current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-270">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-270">Prototype</span></span>

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="ece05-271">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-271">Description</span></span>
<span data-ttu-id="ece05-272">Este servicio obtiene el valor actual del reloj PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-272">This service gets the current value of the PTP clock.</span></span> <span data-ttu-id="ece05-273">Está disponible, independientemente de si el cliente PTP está sincronizado con el reloj principal o no.</span><span class="sxs-lookup"><span data-stu-id="ece05-273">It is available no matter PTP client is synchronized with master clock or not.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-274">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-274">Input Parameters</span></span>
* <span data-ttu-id="ece05-275">**client_ptr** Puntero al cliente PTP que se va a crear</span><span class="sxs-lookup"><span data-stu-id="ece05-275">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="ece05-276">**time_ptr** Puntero a la hora PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-276">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-277">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-277">Return Values</span></span>
* <span data-ttu-id="ece05-278">**NX_SUCCESS** (0x00) El cliente se creó correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-278">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="ece05-279">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-279">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-280">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-280">Allowed From</span></span>
<span data-ttu-id="ece05-281">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-282">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-282">Example</span></span>
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a><span data-ttu-id="ece05-283">nx_ptp_client_time_set</span><span class="sxs-lookup"><span data-stu-id="ece05-283">nx_ptp_client_time_set</span></span>

<span data-ttu-id="ece05-284">Establezca la hora actual.</span><span class="sxs-lookup"><span data-stu-id="ece05-284">Set current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-285">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-285">Prototype</span></span>

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="ece05-286">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-286">Description</span></span>
<span data-ttu-id="ece05-287">Este servicio establece el valor actual del reloj PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-287">This service sets the current value of the PTP clock.</span></span> <span data-ttu-id="ece05-288">Se debe invocar antes de que se inicie el cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-288">It must be invoked before PTP client starts.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-289">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-289">Input Parameters</span></span>
* <span data-ttu-id="ece05-290">**client_ptr** Puntero al cliente PTP que se va a crear</span><span class="sxs-lookup"><span data-stu-id="ece05-290">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="ece05-291">**time_ptr** Puntero a la hora PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-291">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-292">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-292">Return Values</span></span>
* <span data-ttu-id="ece05-293">**NX_SUCCESS** (0x00) El cliente se creó correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-293">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="ece05-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) El cliente PTP ya se ha iniciado</span><span class="sxs-lookup"><span data-stu-id="ece05-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="ece05-295">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-295">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-296">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-296">Allowed From</span></span>
<span data-ttu-id="ece05-297">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-297">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-298">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-298">Example</span></span>
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a><span data-ttu-id="ece05-299">nx_ptp_client_utility_convert_time_to_date</span><span class="sxs-lookup"><span data-stu-id="ece05-299">nx_ptp_client_utility_convert_time_to_date</span></span>

<span data-ttu-id="ece05-300">Convierta la hora PTP en una fecha y hora UTC.</span><span class="sxs-lookup"><span data-stu-id="ece05-300">Convert PTP time to a UTC date and time.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-301">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-301">Prototype</span></span>

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a><span data-ttu-id="ece05-302">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-302">Description</span></span>
<span data-ttu-id="ece05-303">Este servicio convierte la hora PTP en una fecha y hora UTC.</span><span class="sxs-lookup"><span data-stu-id="ece05-303">This service converts PTP time to a UTC date and time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-304">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-304">Input Parameters</span></span>
* <span data-ttu-id="ece05-305">**time_ptr** Puntero a la hora PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-305">**time_ptr** Pointer to PTP time</span></span>
* <span data-ttu-id="ece05-306">**offset** Desplazamiento en segundos con signo para agregar a la hora PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-306">**offset** Signed second offset to add the PTP time</span></span>
* <span data-ttu-id="ece05-307">**date_time_ptr** Puntero a la fecha resultante</span><span class="sxs-lookup"><span data-stu-id="ece05-307">**date_time_ptr** Pointer to resulting date</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-308">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-308">Return Values</span></span>
* <span data-ttu-id="ece05-309">**NX_SUCCESS** (0x00) El cliente se creó correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-309">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="ece05-310">**Puntero a la fecha resultante** (0xD03) Parámetro de entrada no válido</span><span class="sxs-lookup"><span data-stu-id="ece05-310">**Pointer to resulting date** (0xD03) Invalid input parameter</span></span>
* <span data-ttu-id="ece05-311">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-311">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-312">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-312">Allowed From</span></span>
<span data-ttu-id="ece05-313">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-313">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-314">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-314">Example</span></span>
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a><span data-ttu-id="ece05-315">nx_ptp_client_utility_time_diff</span><span class="sxs-lookup"><span data-stu-id="ece05-315">nx_ptp_client_utility_time_diff</span></span>

<span data-ttu-id="ece05-316">Diferencia entre dos horas PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-316">Diff two PTP times.</span></span>

### <a name="prototype"></a><span data-ttu-id="ece05-317">Prototipo</span><span class="sxs-lookup"><span data-stu-id="ece05-317">Prototype</span></span>

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a><span data-ttu-id="ece05-318">Descripción</span><span class="sxs-lookup"><span data-stu-id="ece05-318">Description</span></span>
<span data-ttu-id="ece05-319">Este servicio calcula la diferencia entre dos horas PTP.</span><span class="sxs-lookup"><span data-stu-id="ece05-319">This service computes the difference between two PTP times.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ece05-320">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-320">Input Parameters</span></span>
* <span data-ttu-id="ece05-321">**time1_ptr** Puntero a la primera hora PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-321">**time1_ptr** Pointer to first PTP time</span></span>
* <span data-ttu-id="ece05-322">**time2_ptr** Puntero a la segunda hora PTP</span><span class="sxs-lookup"><span data-stu-id="ece05-322">**time2_ptr** Pointer to second PTP time</span></span>
* <span data-ttu-id="ece05-323">**result_ptr** Puntero al resultado de la operación time1-time2</span><span class="sxs-lookup"><span data-stu-id="ece05-323">**result_ptr** Pointer to result time1-time2</span></span>

### <a name="return-values"></a><span data-ttu-id="ece05-324">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="ece05-324">Return Values</span></span>
* <span data-ttu-id="ece05-325">**NX_SUCCESS** (0x00) El cliente se creó correctamente</span><span class="sxs-lookup"><span data-stu-id="ece05-325">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="ece05-326">NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada</span><span class="sxs-lookup"><span data-stu-id="ece05-326">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ece05-327">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="ece05-327">Allowed From</span></span>
<span data-ttu-id="ece05-328">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="ece05-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ece05-329">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ece05-329">Example</span></span>
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```