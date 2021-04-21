---
title: API de clases de host de USBX
description: En este capítulo se tratan todas las API expuestas de las clases de host de USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 39f3a71c28dd14e0093f72d1a3b1ff6837c6f1f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816129"
---
# <a name="chapter-2-usbx-host-classes-api"></a><span data-ttu-id="1cc86-103">Capítulo 2: API de clases de host de USBX</span><span class="sxs-lookup"><span data-stu-id="1cc86-103">Chapter 2: USBX Host Classes API</span></span>

<span data-ttu-id="1cc86-104">En este capítulo se tratan todas las API expuestas de las clases de host de USBX.</span><span class="sxs-lookup"><span data-stu-id="1cc86-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="1cc86-105">Se describen en detalle las siguientes API de cada clase.</span><span class="sxs-lookup"><span data-stu-id="1cc86-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="1cc86-106">Clase Printer</span><span class="sxs-lookup"><span data-stu-id="1cc86-106">Printer class</span></span>
- <span data-ttu-id="1cc86-107">Clase Audio</span><span class="sxs-lookup"><span data-stu-id="1cc86-107">Audio class</span></span>
- <span data-ttu-id="1cc86-108">Clase Asix</span><span class="sxs-lookup"><span data-stu-id="1cc86-108">Asix class</span></span>
- <span data-ttu-id="1cc86-109">Clase Pima/PTP</span><span class="sxs-lookup"><span data-stu-id="1cc86-109">Pima/PTP class</span></span>
- <span data-ttu-id="1cc86-110">Clase Prolific</span><span class="sxs-lookup"><span data-stu-id="1cc86-110">Prolific class</span></span>
- <span data-ttu-id="1cc86-111">Clase Generic Serial</span><span class="sxs-lookup"><span data-stu-id="1cc86-111">Generic Serial class</span></span>

## <a name="ux_host_class_printer_read"></a><span data-ttu-id="1cc86-112">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="1cc86-112">ux_host_class_printer_read</span></span>

<span data-ttu-id="1cc86-113">Lectura desde la interfaz de la impresora.</span><span class="sxs-lookup"><span data-stu-id="1cc86-113">Read from the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-114">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-114">Prototype</span></span>

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="1cc86-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-115">Description</span></span>

<span data-ttu-id="1cc86-116">Esta función lee desde la interfaz de la impresora.</span><span class="sxs-lookup"><span data-stu-id="1cc86-116">This function reads from the printer interface.</span></span> <span data-ttu-id="1cc86-117">La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia.</span><span class="sxs-lookup"><span data-stu-id="1cc86-117">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span> <span data-ttu-id="1cc86-118">Solo se permite la lectura en impresoras bidireccionales.</span><span class="sxs-lookup"><span data-stu-id="1cc86-118">A read is allowed only on bi-directional printers.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-119">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-119">Parameters</span></span>

- <span data-ttu-id="1cc86-120">**printer**: puntero que señala a la instancia de la clase printer.</span><span class="sxs-lookup"><span data-stu-id="1cc86-120">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="1cc86-121">**data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.</span><span class="sxs-lookup"><span data-stu-id="1cc86-121">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="1cc86-122">**requested_length**: longitud que se va a recibir.</span><span class="sxs-lookup"><span data-stu-id="1cc86-122">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="1cc86-123">**actual_length**: longitud recibida realmente.</span><span class="sxs-lookup"><span data-stu-id="1cc86-123">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-124">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-124">Return Value</span></span>

- <span data-ttu-id="1cc86-125">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-125">**UX_SUCCESS**:  (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54): no se admite la función porque la impresora no es bidireccional.</span><span class="sxs-lookup"><span data-stu-id="1cc86-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported because the printer is not bi-directional.</span></span>
- <span data-ttu-id="1cc86-127">**UX_TRANSFER_TIMEOUT**: (0x5c): se agotó el tiempo de espera de la transferencia, lectura incompleta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-127">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-128">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a><span data-ttu-id="1cc86-129">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="1cc86-129">ux_host_class_printer_write</span></span>

<span data-ttu-id="1cc86-130">Escritura en la interfaz de la impresora.</span><span class="sxs-lookup"><span data-stu-id="1cc86-130">Write to the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-131">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-131">Prototype</span></span>

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="1cc86-132">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-132">Description</span></span>

<span data-ttu-id="1cc86-133">Esta función escribe en la interfaz de la impresora.</span><span class="sxs-lookup"><span data-stu-id="1cc86-133">This function writes to the printer interface.</span></span> <span data-ttu-id="1cc86-134">La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia.</span><span class="sxs-lookup"><span data-stu-id="1cc86-134">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-135">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-135">Parameters</span></span>

- <span data-ttu-id="1cc86-136">**printer**: puntero que señala a la instancia de la clase printer.</span><span class="sxs-lookup"><span data-stu-id="1cc86-136">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="1cc86-137">**data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.</span><span class="sxs-lookup"><span data-stu-id="1cc86-137">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="1cc86-138">**requested_length**: longitud que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="1cc86-138">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="1cc86-139">**actual_length**: longitud enviada realmente.</span><span class="sxs-lookup"><span data-stu-id="1cc86-139">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-140">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-140">Return Value</span></span>

- <span data-ttu-id="1cc86-141">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-141">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-142">**UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, escritura incompleta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-142">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-143">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-143">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="1cc86-144">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="1cc86-144">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="1cc86-145">Realización de un restablecimiento parcial de la impresora.</span><span class="sxs-lookup"><span data-stu-id="1cc86-145">Perform a soft reset to the printer.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-146">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-146">Prototype</span></span>

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a><span data-ttu-id="1cc86-147">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-147">Description</span></span>

<span data-ttu-id="1cc86-148">Realiza un restablecimiento parcial de la impresora.</span><span class="sxs-lookup"><span data-stu-id="1cc86-148">This function performs a soft reset to the printer.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="1cc86-149">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="1cc86-149">Input Parameter</span></span>

- <span data-ttu-id="1cc86-150">**printer**: puntero que señala a la instancia de la clase printer.</span><span class="sxs-lookup"><span data-stu-id="1cc86-150">**printer**: Pointer to the printer class instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-151">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-151">Return Value</span></span>

- <span data-ttu-id="1cc86-152">**UX_SUCCESS**: (0x00): se ha completado el restablecimiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-152">**UX_SUCCESS**: (0x00)The reset was completed.</span></span>
- <span data-ttu-id="1cc86-153">**UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, restablecimiento incompleto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-153">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-154">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-154">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="1cc86-155">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-155">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="1cc86-156">Obtención del estado de la impresora.</span><span class="sxs-lookup"><span data-stu-id="1cc86-156">Get the printer status</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-157">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-157">Prototype</span></span>

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a><span data-ttu-id="1cc86-158">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-158">Description</span></span>

<span data-ttu-id="1cc86-159">Esta función obtiene el estado de la impresora.</span><span class="sxs-lookup"><span data-stu-id="1cc86-159">This function obtains the printer status.</span></span> <span data-ttu-id="1cc86-160">El estado de la impresora es similar al estado LPT (estándar 1284).</span><span class="sxs-lookup"><span data-stu-id="1cc86-160">The printer status is similar to the LPT status (1284 standard).</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-161">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-161">Parameters</span></span>

- <span data-ttu-id="1cc86-162">**printer**: puntero que señala a la instancia de la clase printer.</span><span class="sxs-lookup"><span data-stu-id="1cc86-162">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="1cc86-163">**printer_status**: dirección del estado que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="1cc86-163">**printer_status**: Address of the status to be returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-164">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-164">Return Value</span></span>

- <span data-ttu-id="1cc86-165">**UX_SUCCESS** (0x00): se ha completado el restablecimiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-165">**UX_SUCCESS** (0x00): The reset was completed.</span></span>
- <span data-ttu-id="1cc86-166">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para realizar la operación.</span><span class="sxs-lookup"><span data-stu-id="1cc86-166">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="1cc86-167">**UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, restablecimiento incompleto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-167">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-168">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-168">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a><span data-ttu-id="1cc86-169">ux_host_class_printer_device_id_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-169">ux_host_class_printer_device_id_get</span></span>

<span data-ttu-id="1cc86-170">Obtención del identificador de dispositivo de la impresora.</span><span class="sxs-lookup"><span data-stu-id="1cc86-170">Get the printer device id.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-171">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-171">Prototype</span></span>

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a><span data-ttu-id="1cc86-172">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-172">Description</span></span>

<span data-ttu-id="1cc86-173">Esta función obtiene la cadena de identidad del dispositivo IEEE 1284 de la impresora (incluida la longitud de los dos primeros bytes en formato big endian).</span><span class="sxs-lookup"><span data-stu-id="1cc86-173">This function obtains the printer IEEE 1284 device ID string (including length in the first two bytes in big endian format).</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-174">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-174">Parameters</span></span>

- <span data-ttu-id="1cc86-175">**printer**: puntero que señala a la instancia de la clase printer.</span><span class="sxs-lookup"><span data-stu-id="1cc86-175">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="1cc86-176">**descriptor_buffer**: puntero que señala a un búfer para llenar la cadena de identidad del dispositivo IEEE 1284 (incluida la longitud de los dos primeros bytes en formato BE).</span><span class="sxs-lookup"><span data-stu-id="1cc86-176">**descriptor_buffer**: Pointer to a buffer to fill IEEE 1284 device ID string (including length in the first two bytes in BE format)</span></span> 
- <span data-ttu-id="1cc86-177">**length**: longitud del búfer en bytes.</span><span class="sxs-lookup"><span data-stu-id="1cc86-177">**length**: Length of buffer in bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-178">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-178">Return Value</span></span>

- <span data-ttu-id="1cc86-179">**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="1cc86-179">**UX_SUCCESS** (0x00): The operation was successful.</span></span>
- <span data-ttu-id="1cc86-180">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para realizar la operación.</span><span class="sxs-lookup"><span data-stu-id="1cc86-180">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="1cc86-181">**UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, solicitud incompleta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-181">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, request not completed</span></span>
- <span data-ttu-id="1cc86-182">**UX_TRANSFER_NOT_READY**: (0x25): el dispositivo estaba en un estado no válido; debe estar en los estados ATTACHED, ADDRESSED o CONFIGURED.</span><span class="sxs-lookup"><span data-stu-id="1cc86-182">**UX_TRANSFER_NOT_READY**: (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>
- <span data-ttu-id="1cc86-183">**UX_TRANSFER_STALL**: (0x21): se ha detenido la transferencia.</span><span class="sxs-lookup"><span data-stu-id="1cc86-183">**UX_TRANSFER_STALL**: (0x21) Transfer stalled.</span></span>
- <span data-ttu-id="1cc86-184">**TX_WAIT_ABORTED** (0x1A): otro subproceso, temporizador o ISR anuló la suspensión.</span><span class="sxs-lookup"><span data-stu-id="1cc86-184">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="1cc86-185">**TX_SEMAPHORE_ERROR** (0x0C) puntero del semáforo de recuento no válido.</span><span class="sxs-lookup"><span data-stu-id="1cc86-185">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="1cc86-186">**TX_WAIT_ERROR** (0x04): se ha especificado una opción de espera distinta de TX_NO_WAIT en una llamada de un no subproceso.</span><span class="sxs-lookup"><span data-stu-id="1cc86-186">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-187">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-187">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a><span data-ttu-id="1cc86-188">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="1cc86-188">ux_host_class_audio_read</span></span>

<span data-ttu-id="1cc86-189">Lectura desde la interfaz de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-189">Read from the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-190">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-190">Prototype</span></span>

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="1cc86-191">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-191">Description</span></span>

<span data-ttu-id="1cc86-192">Esta función lee desde la interfaz de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-192">This function reads from the audio interface.</span></span> <span data-ttu-id="1cc86-193">La llamada no es de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="1cc86-193">The call is non-blocking.</span></span> <span data-ttu-id="1cc86-194">La aplicación debe asegurarse de que se ha seleccionado la configuración alternativa adecuada para la interfaz de transmisión de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-194">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-195">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-195">Parameters</span></span>

- <span data-ttu-id="1cc86-196">**audio**: puntero que señala a la instancia de clase de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-196">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="1cc86-197">**audio_transfer_request**: puntero que señala a la estructura de transferencia de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-197">**audio_transfer_request**: Pointer to the audio transfer structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-198">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-198">Return Value</span></span>

- <span data-ttu-id="1cc86-199">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-199">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="1cc86-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54): función no admitida.</span><span class="sxs-lookup"><span data-stu-id="1cc86-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54) Function not supported</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-201">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-201">Example</span></span>

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a><span data-ttu-id="1cc86-202">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="1cc86-202">ux_host_class_audio_write</span></span>

<span data-ttu-id="1cc86-203">Escritura en la interfaz de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-203">Write to the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-204">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-204">Prototype</span></span>

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="1cc86-205">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-205">Description</span></span>

<span data-ttu-id="1cc86-206">Esta función escribe en la interfaz de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-206">This function writes to the audio interface.</span></span> <span data-ttu-id="1cc86-207">La llamada no es de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="1cc86-207">The call is non-blocking.</span></span> <span data-ttu-id="1cc86-208">La aplicación debe asegurarse de que se ha seleccionado la configuración alternativa adecuada para la interfaz de transmisión de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-208">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-209">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-209">Parameters</span></span>

- <span data-ttu-id="1cc86-210">**audio**: puntero que señala a la instancia de clase de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-210">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="1cc86-211">**audio_transfer_request**: puntero que señala a la estructura de transferencia de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-211">**audio_transfer_request**: Pointer to the audio transfer structure</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-212">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-212">Return Value</span></span>

- <span data-ttu-id="1cc86-213">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-213">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.</span><span class="sxs-lookup"><span data-stu-id="1cc86-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported.</span></span>
- <span data-ttu-id="1cc86-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-216">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-216">Example</span></span>

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a><span data-ttu-id="1cc86-217">ux_host_class_audio_control_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-217">ux_host_class_audio_control_get</span></span>

<span data-ttu-id="1cc86-218">Obtención de un control específico de la interfaz de control de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-218">Get a specific control from the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-219">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-219">Prototype</span></span>

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a><span data-ttu-id="1cc86-220">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-220">Description</span></span>

<span data-ttu-id="1cc86-221">Esta función lee un control específico de la interfaz de control de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-221">This function reads a specific control from the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-222">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-222">Parameters</span></span>

- <span data-ttu-id="1cc86-223">**audio**: puntero que señala a la instancia de clase de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-223">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="1cc86-224">**audio_control**: puntero que señala a la estructura de control de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-224">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-225">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-225">Return Value</span></span>

- <span data-ttu-id="1cc86-226">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-226">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="1cc86-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.</span><span class="sxs-lookup"><span data-stu-id="1cc86-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="1cc86-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-229">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-229">Example</span></span>

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="1cc86-230">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="1cc86-230">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="1cc86-231">Establecimiento de un control específico en la interfaz de control de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-231">Set a specific control to the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-232">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-232">Prototype</span></span>

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

<span data-ttu-id="1cc86-233">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="1cc86-233">\*\*Description \*\*</span></span>

<span data-ttu-id="1cc86-234">Esta función establece un control específico en la interfaz de control de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-234">This function sets a specific control to the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-235">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-235">Parameters</span></span>

- <span data-ttu-id="1cc86-236">**audio**: puntero que señala a la instancia de clase de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-236">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="1cc86-237">**audio_control**: puntero que señala a la estructura de control de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-237">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-238">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-238">Return Value</span></span>

- <span data-ttu-id="1cc86-239">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-239">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="1cc86-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.</span><span class="sxs-lookup"><span data-stu-id="1cc86-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="1cc86-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-242">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-242">Example</span></span>

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="1cc86-243">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="1cc86-243">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="1cc86-244">Establecimiento de una interfaz de configuración alternativa de la interfaz de transmisión de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-244">Set an alternate setting interface of the audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-245">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-245">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="1cc86-246">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-246">Description</span></span>

<span data-ttu-id="1cc86-247">Esta función establece la interfaz de configuración alternativa adecuada de la interfaz de transmisión de audio según una estructura de muestreo específica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-247">This function sets the appropriate alternate setting interface of the audio streaming interface according to a specific sampling structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-248">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-248">Parameters</span></span>

- <span data-ttu-id="1cc86-249">**audio**: puntero que señala a la instancia de clase de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-249">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="1cc86-250">**audio_sampling**: puntero que señala a la estructura de muestreo de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-250">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-251">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-251">Return Value</span></span>

- <span data-ttu-id="1cc86-252">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-252">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="1cc86-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.</span><span class="sxs-lookup"><span data-stu-id="1cc86-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="1cc86-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="1cc86-255">**UX_NO_ALTERNATE_SETTING**: (0x5e): no hay valores alternativos para los valores de muestreo.</span><span class="sxs-lookup"><span data-stu-id="1cc86-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-256">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-256">Example</span></span>

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="1cc86-257">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-257">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="1cc86-258">Obtención de los ajustes de muestreo posibles de la interfaz de transmisión de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-258">Get possible sampling settings of audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-259">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-259">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="1cc86-260">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-260">Description</span></span>

<span data-ttu-id="1cc86-261">Esta función obtiene, de uno en uno, todos los ajustes de muestreo posibles disponibles en cada una de las configuraciones alternativas de la interfaz de transmisión de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-261">This function gets, one by one, all the possible sampling settings available in each of the alternate settings of the audio streaming interface.</span></span> <span data-ttu-id="1cc86-262">La primera vez que se usa la función, se deben restablecer todos los campos del puntero de la estructura de llamada.</span><span class="sxs-lookup"><span data-stu-id="1cc86-262">The first time the function is used, all the fields in the calling structure pointer must be reset.</span></span> <span data-ttu-id="1cc86-263">La función devolverá un conjunto específico de valores de transmisión por secuencias a menos que se haya alcanzado el final de la configuración alternativa.</span><span class="sxs-lookup"><span data-stu-id="1cc86-263">The function will return a specific set of streaming values upon return unless the end of the alternate settings has been reached.</span></span> <span data-ttu-id="1cc86-264">Cuando se vuelva a usar esta función, se usarán los valores de muestreo anteriores para buscar los siguientes valores de muestreo.</span><span class="sxs-lookup"><span data-stu-id="1cc86-264">When this function is reused, the previous sampling values will be used to find the next sampling values.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-265">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-265">Parameters</span></span>

- <span data-ttu-id="1cc86-266">**audio**: puntero que señala a la instancia de clase de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-266">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="1cc86-267">**audio_sampling**: puntero que señala a la estructura de muestreo de audio.</span><span class="sxs-lookup"><span data-stu-id="1cc86-267">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-268">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-268">Return Value</span></span>

- <span data-ttu-id="1cc86-269">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-269">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="1cc86-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54): función no admitida.</span><span class="sxs-lookup"><span data-stu-id="1cc86-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="1cc86-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81): la interfaz es incorrecta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="1cc86-272">**UX_NO_ALTERNATE_SETTING**: (0x5e): no hay valores alternativos para los valores de muestreo.</span><span class="sxs-lookup"><span data-stu-id="1cc86-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-273">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-273">Example</span></span>

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a><span data-ttu-id="1cc86-274">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="1cc86-274">ux_host_class_asix_read</span></span>

<span data-ttu-id="1cc86-275">Lectura desde la interfaz ASIX.</span><span class="sxs-lookup"><span data-stu-id="1cc86-275">Read from the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-276">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-276">Prototype</span></span>

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="1cc86-277">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-277">Description</span></span>

<span data-ttu-id="1cc86-278">Esta función lee desde la interfaz ASIX.</span><span class="sxs-lookup"><span data-stu-id="1cc86-278">This function reads from the asix interface.</span></span> <span data-ttu-id="1cc86-279">La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia.</span><span class="sxs-lookup"><span data-stu-id="1cc86-279">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-280">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-280">Parameters</span></span>

- <span data-ttu-id="1cc86-281">**ASIX**: puntero que señala a la instancia de la clase ASIX.</span><span class="sxs-lookup"><span data-stu-id="1cc86-281">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="1cc86-282">**data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.</span><span class="sxs-lookup"><span data-stu-id="1cc86-282">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="1cc86-283">**requested_length**: longitud que se va a recibir.</span><span class="sxs-lookup"><span data-stu-id="1cc86-283">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="1cc86-284">**actual_length**: longitud recibida realmente.</span><span class="sxs-lookup"><span data-stu-id="1cc86-284">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-285">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-285">Return Value</span></span>

- <span data-ttu-id="1cc86-286">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-286">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-287">**UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, lectura incompleta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-287">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-288">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-288">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a><span data-ttu-id="1cc86-289">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="1cc86-289">ux_host_class_asix_write</span></span>

<span data-ttu-id="1cc86-290">Escritura en la interfaz ASIX.</span><span class="sxs-lookup"><span data-stu-id="1cc86-290">Write to the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-291">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-291">Prototype</span></span>

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a><span data-ttu-id="1cc86-292">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-292">Description</span></span>

<span data-ttu-id="1cc86-293">Esta función escribe en la interfaz ASIX.</span><span class="sxs-lookup"><span data-stu-id="1cc86-293">This function writes to the asix interface.</span></span> <span data-ttu-id="1cc86-294">La llamada no es de bloqueo.</span><span class="sxs-lookup"><span data-stu-id="1cc86-294">The call is non blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-295">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-295">Parameters</span></span>

- <span data-ttu-id="1cc86-296">**ASIX**: puntero que señala a la instancia de la clase ASIX.</span><span class="sxs-lookup"><span data-stu-id="1cc86-296">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="1cc86-297">**packet**: paquete de datos NetX</span><span class="sxs-lookup"><span data-stu-id="1cc86-297">**packet**: Netx data packet</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-298">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-298">Return Value</span></span>

- <span data-ttu-id="1cc86-299">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-299">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-300">**UX_ERROR**: (0xFF): no se pudo solicitar la transferencia.</span><span class="sxs-lookup"><span data-stu-id="1cc86-300">**UX_ERROR**: (0xFF) Transfer could not be requested.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-301">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-301">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="1cc86-302">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="1cc86-302">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="1cc86-303">Apertura de una sesión entre el iniciador y el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-303">Open a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-304">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-304">Prototype</span></span>

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="1cc86-305">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-305">Description</span></span>

<span data-ttu-id="1cc86-306">Esta función abre una sesión entre un iniciador PIMA y un respondedor PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-306">This function opens a session between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="1cc86-307">Una vez que se abre una sesión correctamente, la mayoría de los comandos PIMA se pueden ejecutar.</span><span class="sxs-lookup"><span data-stu-id="1cc86-307">Once a session is successfully opened, most PIMA commands can be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-308">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-308">Parameters</span></span>

- <span data-ttu-id="1cc86-309">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-309">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-310">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-310">**pima_sessio**: Pointer to PIMA session<</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-311">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-311">Return Value</span></span>

- <span data-ttu-id="1cc86-312">**UX_SUCCESS**: (0x00): la sesión se ha abierto correctamente.</span><span class="sxs-lookup"><span data-stu-id="1cc86-312">**UX_SUCCESS**: (0x00) Session successfully opened</span></span>
- <span data-ttu-id="1cc86-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E): la sesión ya está abierta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Session already opened</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-314">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-314">Example</span></span>

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="1cc86-315">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="1cc86-315">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="1cc86-316">Cierre de una sesión entre el iniciador y el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-316">Close a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-317">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-317">Prototype</span></span>

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="1cc86-318">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-318">Description</span></span>

<span data-ttu-id="1cc86-319">Esta función cierra una sesión que se abrió previamente entre un iniciador PIMA y un respondedor PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-319">This function closes a session that was previously opened between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="1cc86-320">Una vez que se cierra una sesión, la mayoría de los comandos PIMA ya no se pueden ejecutar.</span><span class="sxs-lookup"><span data-stu-id="1cc86-320">Once a session is closed, most PIMA commands can no longer be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-321">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-321">Parameters</span></span>

- <span data-ttu-id="1cc86-322">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-322">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-323">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-323">**pima_session**: Pointer to PIMA session.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-324">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-324">Return Value</span></span>

- <span data-ttu-id="1cc86-325">**UX_SUCCESS**: (0x00): la sesión se ha cerrado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-325">**UX_SUCCESS**: (0x00) The session was closed.</span></span>
- <span data-ttu-id="1cc86-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-327">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-327">Example</span></span>

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a><span data-ttu-id="1cc86-328">ux_host_class_pima_storage_ids_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-328">ux_host_class_pima_storage_ids_get</span></span>

<span data-ttu-id="1cc86-329">Obtención de la matriz del identificador de almacenamiento del respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-329">Obtain the storage ID array from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-330">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-330">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a><span data-ttu-id="1cc86-331">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-331">Description</span></span>

<span data-ttu-id="1cc86-332">Esta función obtiene la matriz de identificación de almacenamiento del respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-332">This function obtains the storage ID array from the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-333">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-333">Parameters</span></span>

- <span data-ttu-id="1cc86-334">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-334">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-335">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-335">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="1cc86-336">**storage_ids_array**: matriz en la que se devolverán los identificadores de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-336">**storage_ids_array**: Array where storage IDs will be returned</span></span>
- <span data-ttu-id="1cc86-337">**storage_id_length**: longitud de la matriz de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-337">**storage_id_length**: Length of the storage array</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-338">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-338">Return Value</span></span>

- <span data-ttu-id="1cc86-339">**UX_SUCCESS**: (0x00): se ha rellenado la matriz de identificación del almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-339">**UX_SUCCESS**: (0x00) The storage ID array has been populated</span></span>
- <span data-ttu-id="1cc86-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="1cc86-341">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-341">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-342">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-342">Example</span></span>

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="1cc86-343">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-343">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="1cc86-344">Obtención de la información de almacenamiento del respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-344">Obtain the storage information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-345">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-345">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a><span data-ttu-id="1cc86-346">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-346">Description</span></span>

<span data-ttu-id="1cc86-347">Esta función obtiene la información de almacenamiento de un contenedor de almacenamiento con el valor *storage_id*.</span><span class="sxs-lookup"><span data-stu-id="1cc86-347">This function obtains the storage information for a storage container of value *storage_id*.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-348">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-348">Parameters</span></span>

- <span data-ttu-id="1cc86-349">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-349">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-350">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-350">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="1cc86-351">**storage_id**: identificador del contenedor de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-351">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="1cc86-352">**storage**: puntero que señala a un contenedor de información de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-352">**storage**: Pointer to storage information container</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-353">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-353">Return Value</span></span>

- <span data-ttu-id="1cc86-354">**UX_SUCCESS**: (0x00): se ha recuperado la información de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-354">**UX_SUCCESS**: (0x00) The storage information was retrieved</span></span>
- <span data-ttu-id="1cc86-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="1cc86-356">**UX_MEMORY_INSUFFICIENT** (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-356">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-357">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-357">Example</span></span>

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a><span data-ttu-id="1cc86-358">ux_host_class_pima_num_objects_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-358">ux_host_class_pima_num_objects_get</span></span>

<span data-ttu-id="1cc86-359">Obtención del número de objetos de un contenedor de almacenamiento del respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-359">Obtain the number of objects on a storage container from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-360">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-360">Prototype</span></span>

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a><span data-ttu-id="1cc86-361">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-361">Description</span></span>

<span data-ttu-id="1cc86-362">Esta función obtiene el número de objetos almacenados en un contenedor de almacenamiento específico con el valor storage_id que coincide con un código de formato específico.</span><span class="sxs-lookup"><span data-stu-id="1cc86-362">This function obtains the number of objects stored on a specific storage container of value storage_id matching a specific format code.</span></span> <span data-ttu-id="1cc86-363">El número de objetos se devuelve en el campo ux_host_class_pima_session_nb_objects de la estructura pima_session.</span><span class="sxs-lookup"><span data-stu-id="1cc86-363">The number of objects is returned in the field: ux_host_class_pima_session_nb_objects of the pima_session structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-364">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-364">Parameters</span></span>

- <span data-ttu-id="1cc86-365">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-365">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-366">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-366">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="1cc86-367">**storage_id**: identificador del contenedor de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-367">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="1cc86-368">**object_format_code**: filtro del código de formato de los objetos.</span><span class="sxs-lookup"><span data-stu-id="1cc86-368">**object_format_code**: Objects format code filter.</span></span>

<span data-ttu-id="1cc86-369">Los códigos de formato de los objetos pueden tener uno de estos valores.</span><span class="sxs-lookup"><span data-stu-id="1cc86-369">The Object Format Codes can have one of the following values.</span></span>

| <span data-ttu-id="1cc86-370">Código de formato de objeto</span><span class="sxs-lookup"><span data-stu-id="1cc86-370">Object Format Code</span></span>               | <span data-ttu-id="1cc86-371">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-371">Description</span></span>   |     <span data-ttu-id="1cc86-372">Código de USBX</span><span class="sxs-lookup"><span data-stu-id="1cc86-372">USBX code</span></span>                          |
|----------------------------------|---------------|------------------------------------------|
| <span data-ttu-id="1cc86-373">0x3000</span><span class="sxs-lookup"><span data-stu-id="1cc86-373">0x3000</span></span>                           | <span data-ttu-id="1cc86-374">Objeto no definido que no es una imagen</span><span class="sxs-lookup"><span data-stu-id="1cc86-374">Undefined Undefined non-image object</span></span> | <span data-ttu-id="1cc86-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span><span class="sxs-lookup"><span data-stu-id="1cc86-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span></span>   |
| <span data-ttu-id="1cc86-376">0x3001</span><span class="sxs-lookup"><span data-stu-id="1cc86-376">0x3001</span></span>                           | <span data-ttu-id="1cc86-377">Asociación (por ejemplo, carpeta)</span><span class="sxs-lookup"><span data-stu-id="1cc86-377">Association Association (e.g. folder)</span></span> | <span data-ttu-id="1cc86-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span><span class="sxs-lookup"><span data-stu-id="1cc86-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span></span> |
| <span data-ttu-id="1cc86-379">0x3002</span><span class="sxs-lookup"><span data-stu-id="1cc86-379">0x3002</span></span>                           | <span data-ttu-id="1cc86-380">Script específico del modelo de dispositivo</span><span class="sxs-lookup"><span data-stu-id="1cc86-380">Script Device-model specific script</span></span> | <span data-ttu-id="1cc86-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span><span class="sxs-lookup"><span data-stu-id="1cc86-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span></span>      |
| <span data-ttu-id="1cc86-382">0x3003</span><span class="sxs-lookup"><span data-stu-id="1cc86-382">0x3003</span></span>                           | <span data-ttu-id="1cc86-383">Archivo ejecutable binario específico del modelo de dispositivo</span><span class="sxs-lookup"><span data-stu-id="1cc86-383">Executable Device model-specific binary executable</span></span> | <span data-ttu-id="1cc86-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span><span class="sxs-lookup"><span data-stu-id="1cc86-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span></span>  |
| <span data-ttu-id="1cc86-385">0x3004</span><span class="sxs-lookup"><span data-stu-id="1cc86-385">0x3004</span></span>                           | <span data-ttu-id="1cc86-386">Archivo de texto</span><span class="sxs-lookup"><span data-stu-id="1cc86-386">Text Text file</span></span>  |   <span data-ttu-id="1cc86-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span><span class="sxs-lookup"><span data-stu-id="1cc86-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span></span>        |
| <span data-ttu-id="1cc86-388">0x3005</span><span class="sxs-lookup"><span data-stu-id="1cc86-388">0x3005</span></span>                           | <span data-ttu-id="1cc86-389">Archivo de lenguaje de marcado de hipertexto, HTML (texto)</span><span class="sxs-lookup"><span data-stu-id="1cc86-389">HTML HyperText Markup Language file (text)</span></span> | <span data-ttu-id="1cc86-390">UX_HOST_CLASS_PIMA_OFC_HTML</span><span class="sxs-lookup"><span data-stu-id="1cc86-390">UX_HOST_CLASS_PIMA_OFC_HTML</span></span>        |
| <span data-ttu-id="1cc86-391">0x3006</span><span class="sxs-lookup"><span data-stu-id="1cc86-391">0x3006</span></span>                           | <span data-ttu-id="1cc86-392">Archivo de formato de orden de impresión digital, DPOF (texto)</span><span class="sxs-lookup"><span data-stu-id="1cc86-392">DPOF Digital Print Order Format file (text)</span></span> | <span data-ttu-id="1cc86-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span><span class="sxs-lookup"><span data-stu-id="1cc86-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span></span>        |
| <span data-ttu-id="1cc86-394">0x3007</span><span class="sxs-lookup"><span data-stu-id="1cc86-394">0x3007</span></span>                           | <span data-ttu-id="1cc86-395">Clip de audio AIFF</span><span class="sxs-lookup"><span data-stu-id="1cc86-395">AIFF Audio clip</span></span>  |  <span data-ttu-id="1cc86-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span><span class="sxs-lookup"><span data-stu-id="1cc86-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span></span>        |
| <span data-ttu-id="1cc86-397">0x3008</span><span class="sxs-lookup"><span data-stu-id="1cc86-397">0x3008</span></span>                           | <span data-ttu-id="1cc86-398">Clip de audio WAV</span><span class="sxs-lookup"><span data-stu-id="1cc86-398">WAV Audio clip</span></span>   |  <span data-ttu-id="1cc86-399">UX_HOST_CLASS_PIMA_OFC_WAV</span><span class="sxs-lookup"><span data-stu-id="1cc86-399">UX_HOST_CLASS_PIMA_OFC_WAV</span></span>         |
| <span data-ttu-id="1cc86-400">0x3009</span><span class="sxs-lookup"><span data-stu-id="1cc86-400">0x3009</span></span>                           | <span data-ttu-id="1cc86-401">Clip de audio MP3</span><span class="sxs-lookup"><span data-stu-id="1cc86-401">MP3 Audio clip</span></span>   |  <span data-ttu-id="1cc86-402">UX_HOST_CLASS_PIMA_OFC_MP3</span><span class="sxs-lookup"><span data-stu-id="1cc86-402">UX_HOST_CLASS_PIMA_OFC_MP3</span></span>         |
| <span data-ttu-id="1cc86-403">0x300A</span><span class="sxs-lookup"><span data-stu-id="1cc86-403">0x300A</span></span>                           | <span data-ttu-id="1cc86-404">Clip de vídeo AVI</span><span class="sxs-lookup"><span data-stu-id="1cc86-404">AVI Video clip</span></span>   |  <span data-ttu-id="1cc86-405">UX_HOST_CLASS_PIMA_OFC_AVI</span><span class="sxs-lookup"><span data-stu-id="1cc86-405">UX_HOST_CLASS_PIMA_OFC_AVI</span></span>         |
| <span data-ttu-id="1cc86-406">0x300B</span><span class="sxs-lookup"><span data-stu-id="1cc86-406">0x300B</span></span>                           | <span data-ttu-id="1cc86-407">Clip de vídeo MPEG</span><span class="sxs-lookup"><span data-stu-id="1cc86-407">MPEG Video clip</span></span>  |  <span data-ttu-id="1cc86-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span><span class="sxs-lookup"><span data-stu-id="1cc86-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span></span>        |
| <span data-ttu-id="1cc86-409">0x300C</span><span class="sxs-lookup"><span data-stu-id="1cc86-409">0x300C</span></span>                           | <span data-ttu-id="1cc86-410">Advanced Streaming Format de Microsoft, ASF (vídeo)</span><span class="sxs-lookup"><span data-stu-id="1cc86-410">ASF Microsoft Advanced Streaming Format (video)</span></span> | <span data-ttu-id="1cc86-411">UX_HOST_CLASS_PIMA_OFC_ASF</span><span class="sxs-lookup"><span data-stu-id="1cc86-411">UX_HOST_CLASS_PIMA_OFC_ASF</span></span>         |
| <span data-ttu-id="1cc86-412">0x3800</span><span class="sxs-lookup"><span data-stu-id="1cc86-412">0x3800</span></span>                           | <span data-ttu-id="1cc86-413">Objeto de imagen desconocido sin definir</span><span class="sxs-lookup"><span data-stu-id="1cc86-413">Undefined Unknown image object</span></span> | <span data-ttu-id="1cc86-414">UX_HOST_CLASS_PIMA_OFC_QT</span><span class="sxs-lookup"><span data-stu-id="1cc86-414">UX_HOST_CLASS_PIMA_OFC_QT</span></span>          |
| <span data-ttu-id="1cc86-415">0x3801</span><span class="sxs-lookup"><span data-stu-id="1cc86-415">0x3801</span></span>                           | <span data-ttu-id="1cc86-416">Exchangeable Image File Format (EXIF/JPEG), estándar JEIDA</span><span class="sxs-lookup"><span data-stu-id="1cc86-416">EXIF/JPEG Exchangeable File Format, JEIDA standard</span></span> | <span data-ttu-id="1cc86-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="1cc86-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span></span>   |
| <span data-ttu-id="1cc86-418">0x3802</span><span class="sxs-lookup"><span data-stu-id="1cc86-418">0x3802</span></span>                           | <span data-ttu-id="1cc86-419">Tagged Image File Format para fotografía electrónica (TIFF/EP)</span><span class="sxs-lookup"><span data-stu-id="1cc86-419">TIFF/EP Tag Image File Format for Electronic Photography</span></span> | <span data-ttu-id="1cc86-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span><span class="sxs-lookup"><span data-stu-id="1cc86-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span></span>     |
| <span data-ttu-id="1cc86-421">0x3803</span><span class="sxs-lookup"><span data-stu-id="1cc86-421">0x3803</span></span>                           | <span data-ttu-id="1cc86-422">Formato de imagen de almacenamiento estructurado FlashPix</span><span class="sxs-lookup"><span data-stu-id="1cc86-422">FlashPix Structured Storage Image Format</span></span> | <span data-ttu-id="1cc86-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span><span class="sxs-lookup"><span data-stu-id="1cc86-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span></span>    |
| <span data-ttu-id="1cc86-424">0x3804</span><span class="sxs-lookup"><span data-stu-id="1cc86-424">0x3804</span></span>                           | <span data-ttu-id="1cc86-425">Archivo de mapa de bits de Microsoft Windows (BMP)</span><span class="sxs-lookup"><span data-stu-id="1cc86-425">BMP Microsoft Windows Bitmap file</span></span> | <span data-ttu-id="1cc86-426">UX_HOST_CLASS_PIMA_OFC_BMP</span><span class="sxs-lookup"><span data-stu-id="1cc86-426">UX_HOST_CLASS_PIMA_OFC_BMP</span></span>         |
| <span data-ttu-id="1cc86-427">0x3805</span><span class="sxs-lookup"><span data-stu-id="1cc86-427">0x3805</span></span>                           | <span data-ttu-id="1cc86-428">Formato de archivo de imagen de cámara Canon (CIFF)</span><span class="sxs-lookup"><span data-stu-id="1cc86-428">CIFF Canon Camera Image File Format</span></span> | <span data-ttu-id="1cc86-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span><span class="sxs-lookup"><span data-stu-id="1cc86-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span></span>        |
| <span data-ttu-id="1cc86-430">0x3806</span><span class="sxs-lookup"><span data-stu-id="1cc86-430">0x3806</span></span>                           | <span data-ttu-id="1cc86-431">Reservado sin definir</span><span class="sxs-lookup"><span data-stu-id="1cc86-431">Undefined Reserved</span></span> |  |
| <span data-ttu-id="1cc86-432">0x3807</span><span class="sxs-lookup"><span data-stu-id="1cc86-432">0x3807</span></span>                           | <span data-ttu-id="1cc86-433">Formato de intercambio de gráficos (GIF)</span><span class="sxs-lookup"><span data-stu-id="1cc86-433">GIF Graphics Interchange Format</span></span> | <span data-ttu-id="1cc86-434">UX_HOST_CLASS_PIMA_OFC_GIF</span><span class="sxs-lookup"><span data-stu-id="1cc86-434">UX_HOST_CLASS_PIMA_OFC_GIF</span></span>         |
| <span data-ttu-id="1cc86-435">0x3808</span><span class="sxs-lookup"><span data-stu-id="1cc86-435">0x3808</span></span>                           | <span data-ttu-id="1cc86-436">Formato de intercambio de archivos (JPEG/JFIF)</span><span class="sxs-lookup"><span data-stu-id="1cc86-436">JFIF JPEG File Interchange Format</span></span> | <span data-ttu-id="1cc86-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span><span class="sxs-lookup"><span data-stu-id="1cc86-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span></span>        |
| <span data-ttu-id="1cc86-438">0x3809</span><span class="sxs-lookup"><span data-stu-id="1cc86-438">0x3809</span></span>                           | <span data-ttu-id="1cc86-439">PhotoCD Image Pac (PCD)</span><span class="sxs-lookup"><span data-stu-id="1cc86-439">PCD PhotoCD Image Pac</span></span> | <span data-ttu-id="1cc86-440">UX_HOST_CLASS_PIMA_OFC_PCD</span><span class="sxs-lookup"><span data-stu-id="1cc86-440">UX_HOST_CLASS_PIMA_OFC_PCD</span></span>         |
| <span data-ttu-id="1cc86-441">0x380A</span><span class="sxs-lookup"><span data-stu-id="1cc86-441">0x380A</span></span>                           | <span data-ttu-id="1cc86-442">Formato de imagen de Quickdraw (PICT)</span><span class="sxs-lookup"><span data-stu-id="1cc86-442">PICT Quickdraw Image Format</span></span> | <span data-ttu-id="1cc86-443">UX_HOST_CLASS_PIMA_OFC_PICT</span><span class="sxs-lookup"><span data-stu-id="1cc86-443">UX_HOST_CLASS_PIMA_OFC_PICT</span></span>        |
| <span data-ttu-id="1cc86-444">0x380B</span><span class="sxs-lookup"><span data-stu-id="1cc86-444">0x380B</span></span>                           | <span data-ttu-id="1cc86-445">Portable Network Graphics (PNG)</span><span class="sxs-lookup"><span data-stu-id="1cc86-445">PNG Portable Network Graphics</span></span> | <span data-ttu-id="1cc86-446">UX_HOST_CLASS_PIMA_OFC_PNG</span><span class="sxs-lookup"><span data-stu-id="1cc86-446">UX_HOST_CLASS_PIMA_OFC_PNG</span></span>         |
| <span data-ttu-id="1cc86-447">0x380C</span><span class="sxs-lookup"><span data-stu-id="1cc86-447">0x380C</span></span>                           | <span data-ttu-id="1cc86-448">Reservado sin definir</span><span class="sxs-lookup"><span data-stu-id="1cc86-448">Undefined Reserved</span></span> |   |
| <span data-ttu-id="1cc86-449">0x380D</span><span class="sxs-lookup"><span data-stu-id="1cc86-449">0x380D</span></span>                           | <span data-ttu-id="1cc86-450">Tag Image File Format (TIFF)</span><span class="sxs-lookup"><span data-stu-id="1cc86-450">TIFF Tag Image File Format</span></span> | <span data-ttu-id="1cc86-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span><span class="sxs-lookup"><span data-stu-id="1cc86-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span></span>        |
| <span data-ttu-id="1cc86-452">0x380E</span><span class="sxs-lookup"><span data-stu-id="1cc86-452">0x380E</span></span>                           | <span data-ttu-id="1cc86-453">Tag Image File Format para tecnologías de la información, TIFF/IT (artes gráficas)</span><span class="sxs-lookup"><span data-stu-id="1cc86-453">TIFF/IT Tag Image File Format for Information Technology (graphic arts)</span></span> | <span data-ttu-id="1cc86-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span><span class="sxs-lookup"><span data-stu-id="1cc86-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span></span>     |
| <span data-ttu-id="1cc86-455">0x380F</span><span class="sxs-lookup"><span data-stu-id="1cc86-455">0x380F</span></span>                           | <span data-ttu-id="1cc86-456">Formato de archivo de base de referencia JPEG2000 (JP2)</span><span class="sxs-lookup"><span data-stu-id="1cc86-456">JP2 JPEG2000 Baseline File Format</span></span> | <span data-ttu-id="1cc86-457">UX_HOST_CLASS_PIMA_OFC_JP2</span><span class="sxs-lookup"><span data-stu-id="1cc86-457">UX_HOST_CLASS_PIMA_OFC_JP2</span></span>         |
| <span data-ttu-id="1cc86-458">0x3810</span><span class="sxs-lookup"><span data-stu-id="1cc86-458">0x3810</span></span>                           | <span data-ttu-id="1cc86-459">Formato de archivo extendido JPEG2000 (JPX)</span><span class="sxs-lookup"><span data-stu-id="1cc86-459">JPX JPEG2000 Extended File Format</span></span> | <span data-ttu-id="1cc86-460">UX_HOST_CLASS_PIMA_OFC_JPX</span><span class="sxs-lookup"><span data-stu-id="1cc86-460">UX_HOST_CLASS_PIMA_OFC_JPX</span></span>         |
| <span data-ttu-id="1cc86-461">Resto de códigos con un MSN de 0011</span><span class="sxs-lookup"><span data-stu-id="1cc86-461">All other codes with MSN of 0011</span></span> | <span data-ttu-id="1cc86-462">Cualquier reservado sin definir para uso futuro</span><span class="sxs-lookup"><span data-stu-id="1cc86-462">Any Undefined Reserved for future use</span></span> |                                    |
| <span data-ttu-id="1cc86-463">Resto de códigos con un MSN de 1011</span><span class="sxs-lookup"><span data-stu-id="1cc86-463">All other codes with MSN of 1011</span></span> | <span data-ttu-id="1cc86-464">Cualquier tipo definido por el fabricante: imagen</span><span class="sxs-lookup"><span data-stu-id="1cc86-464">Any Vendor-Defined Vendor-Defined type: Image</span></span> |                                    |

### <a name="return-value"></a><span data-ttu-id="1cc86-465">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-465">Return Value</span></span>

- <span data-ttu-id="1cc86-466">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-466">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="1cc86-468">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-468">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-469">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-469">Example</span></span>

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a><span data-ttu-id="1cc86-470">ux_host_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-470">ux_host_class_pima_object_handles_get</span></span>

<span data-ttu-id="1cc86-471">Obtención de identificadores de objeto del respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-471">Obtain object handles from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-472">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-472">Prototype</span></span>

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a><span data-ttu-id="1cc86-473">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-473">Description</span></span>

<span data-ttu-id="1cc86-474">Devuelve una matriz de identificadores de objetos presentes en el contenedor de almacenamiento indicado por el parámetro storage_id.</span><span class="sxs-lookup"><span data-stu-id="1cc86-474">Returns an array of Object Handles present in the storage container indicated by the storage_id parameter.</span></span> <span data-ttu-id="1cc86-475">Si quiere una lista agregada en todos los almacenes, este valor se establecerá en 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="1cc86-475">If an aggregated list across all stores is desired, this value shall be set to 0xFFFFFFFF.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-476">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-476">Parameters</span></span>

- <span data-ttu-id="1cc86-477">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-477">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-478">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-478">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="1cc86-479">**object_handes_array**: matriz en la que se devuelven los identificadores.</span><span class="sxs-lookup"><span data-stu-id="1cc86-479">**object_handes_array**: Array where handles are returned</span></span>
- <span data-ttu-id="1cc86-480">**object_handles_length**: longitud de la matriz.</span><span class="sxs-lookup"><span data-stu-id="1cc86-480">**object_handles_length**: Length of the array</span></span>
- <span data-ttu-id="1cc86-481">**storage_id**: identificador del contenedor de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1cc86-481">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="1cc86-482">**object_format_code**: código de formato del objeto (consulte la tabla para la función ux_host_class_pima_num_objects_get).</span><span class="sxs-lookup"><span data-stu-id="1cc86-482">**object_format_code**: Format code for object (see table for function ux_host_class_pima_num_objects_get)</span></span>
- <span data-ttu-id="1cc86-483">**object_handle_association**: valor de asociación de objeto opcional.</span><span class="sxs-lookup"><span data-stu-id="1cc86-483">**object_handle_association**: Optional object association value</span></span>

<span data-ttu-id="1cc86-484">La asociación del identificador de objeto puede ser uno de los valores de la tabla siguiente:</span><span class="sxs-lookup"><span data-stu-id="1cc86-484">The object handle association can be one of the value from the table below:</span></span>

| <span data-ttu-id="1cc86-485">AssociationCode</span><span class="sxs-lookup"><span data-stu-id="1cc86-485">AssociationCode</span></span>                        | <span data-ttu-id="1cc86-486">AssociationType</span><span class="sxs-lookup"><span data-stu-id="1cc86-486">AssociationType</span></span>      | <span data-ttu-id="1cc86-487">Interpretación</span><span class="sxs-lookup"><span data-stu-id="1cc86-487">Interpretation</span></span>       |
|----------------------------------------|----------------------|----------------------|
| <span data-ttu-id="1cc86-488">0x0000</span><span class="sxs-lookup"><span data-stu-id="1cc86-488">0x0000</span></span>                                 | <span data-ttu-id="1cc86-489">No definido</span><span class="sxs-lookup"><span data-stu-id="1cc86-489">Undefined</span></span>            | <span data-ttu-id="1cc86-490">No definido</span><span class="sxs-lookup"><span data-stu-id="1cc86-490">Undefined</span></span>            |
| <span data-ttu-id="1cc86-491">0x0001</span><span class="sxs-lookup"><span data-stu-id="1cc86-491">0x0001</span></span>                                 | <span data-ttu-id="1cc86-492">GenericFolder</span><span class="sxs-lookup"><span data-stu-id="1cc86-492">GenericFolder</span></span>        | <span data-ttu-id="1cc86-493">No utilizado</span><span class="sxs-lookup"><span data-stu-id="1cc86-493">Unused</span></span>               |
| <span data-ttu-id="1cc86-494">0x0002</span><span class="sxs-lookup"><span data-stu-id="1cc86-494">0x0002</span></span>                                 | <span data-ttu-id="1cc86-495">Álbum</span><span class="sxs-lookup"><span data-stu-id="1cc86-495">Album</span></span>                | <span data-ttu-id="1cc86-496">Reservado</span><span class="sxs-lookup"><span data-stu-id="1cc86-496">Reserved</span></span>             |
| <span data-ttu-id="1cc86-497">0x0003</span><span class="sxs-lookup"><span data-stu-id="1cc86-497">0x0003</span></span>                                 | <span data-ttu-id="1cc86-498">TimeSequence</span><span class="sxs-lookup"><span data-stu-id="1cc86-498">TimeSequence</span></span>         | <span data-ttu-id="1cc86-499">DefaultPlaybackDelta</span><span class="sxs-lookup"><span data-stu-id="1cc86-499">DefaultPlaybackDelta</span></span> |
| <span data-ttu-id="1cc86-500">0x0004</span><span class="sxs-lookup"><span data-stu-id="1cc86-500">0x0004</span></span>                                 | <span data-ttu-id="1cc86-501">HorizontalPanoramic</span><span class="sxs-lookup"><span data-stu-id="1cc86-501">HorizontalPanoramic</span></span>  | <span data-ttu-id="1cc86-502">No utilizado</span><span class="sxs-lookup"><span data-stu-id="1cc86-502">Unused</span></span>               |
| <span data-ttu-id="1cc86-503">0x0005</span><span class="sxs-lookup"><span data-stu-id="1cc86-503">0x0005</span></span>                                 | <span data-ttu-id="1cc86-504">VerticalPanoramic</span><span class="sxs-lookup"><span data-stu-id="1cc86-504">VerticalPanoramic</span></span>    | <span data-ttu-id="1cc86-505">No utilizado</span><span class="sxs-lookup"><span data-stu-id="1cc86-505">Unused</span></span>               |
| <span data-ttu-id="1cc86-506">0x0006</span><span class="sxs-lookup"><span data-stu-id="1cc86-506">0x0006</span></span>                                 | <span data-ttu-id="1cc86-507">2DPanoramic</span><span class="sxs-lookup"><span data-stu-id="1cc86-507">2DPanoramic</span></span>          | <span data-ttu-id="1cc86-508">ImagesPerRow</span><span class="sxs-lookup"><span data-stu-id="1cc86-508">ImagesPerRow</span></span>         |
| <span data-ttu-id="1cc86-509">0x0007</span><span class="sxs-lookup"><span data-stu-id="1cc86-509">0x0007</span></span>                                 | <span data-ttu-id="1cc86-510">AncillaryData</span><span class="sxs-lookup"><span data-stu-id="1cc86-510">AncillaryData</span></span>        | <span data-ttu-id="1cc86-511">No definido</span><span class="sxs-lookup"><span data-stu-id="1cc86-511">Undefined</span></span>            |
| <span data-ttu-id="1cc86-512">Resto de valores con el bit 15 establecido en 0</span><span class="sxs-lookup"><span data-stu-id="1cc86-512">All other values with bit 15 set to 0</span></span>  | <span data-ttu-id="1cc86-513">Reservado</span><span class="sxs-lookup"><span data-stu-id="1cc86-513">Reserved</span></span>             | <span data-ttu-id="1cc86-514">No definido</span><span class="sxs-lookup"><span data-stu-id="1cc86-514">Undefined</span></span>            |
| <span data-ttu-id="1cc86-515">Resto de valores con el bit 15 establecido en 1</span><span class="sxs-lookup"><span data-stu-id="1cc86-515">All values with bit 15 set to 1</span></span>        | <span data-ttu-id="1cc86-516">Vendor-Defined</span><span class="sxs-lookup"><span data-stu-id="1cc86-516">Vendor-Defined</span></span>       | <span data-ttu-id="1cc86-517">Vendor-Defined</span><span class="sxs-lookup"><span data-stu-id="1cc86-517">Vendor-Defined</span></span>       |

### <a name="return-value"></a><span data-ttu-id="1cc86-518">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-518">Return Value</span></span>

- <span data-ttu-id="1cc86-519">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-519">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="1cc86-521">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-521">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-522">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-522">Example</span></span>

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="1cc86-523">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-523">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="1cc86-524">Obtención de la información del objeto del respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-524">Obtain the object information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-525">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-525">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="1cc86-526">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-526">Description</span></span>

<span data-ttu-id="1cc86-527">Esta función obtiene la información de objeto de un identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-527">This function obtains the object information for an object handle.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-528">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-528">Parameters</span></span>

- <span data-ttu-id="1cc86-529">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-529">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-530">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-530">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="1cc86-531">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-531">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="1cc86-532">**object**: puntero que señala al contenedor de información del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-532">**object**: Pointer to object information container</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-533">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-533">Return Value</span></span>

- <span data-ttu-id="1cc86-534">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-534">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="1cc86-536">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-536">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-537">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-537">Example</span></span>

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="1cc86-538">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="1cc86-538">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="1cc86-539">Envío de la información del objeto al respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-539">Send the object information to Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-540">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-540">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="1cc86-541">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-541">Description</span></span>

<span data-ttu-id="1cc86-542">Esta función envía la información de almacenamiento de un contenedor de almacenamiento con el valor storage_id.</span><span class="sxs-lookup"><span data-stu-id="1cc86-542">This function sends the storage information for a storage container of value storage_id.</span></span> <span data-ttu-id="1cc86-543">El iniciador debe usar este comando antes de enviar un objeto al respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-543">The Initiator should use this command before sending an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-544">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-544">Parameters</span></span>

- <span data-ttu-id="1cc86-545">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-545">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-546">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-546">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="1cc86-547">**storage_id**: identificador del almacenamiento de destino.</span><span class="sxs-lookup"><span data-stu-id="1cc86-547">**storage_id**: Destination storage ID.</span></span>
- <span data-ttu-id="1cc86-548">**parent_object_id**: ObjectHandle primario en el respondedor donde debe colocarse el objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-548">**parent_object_id**: Parent ObjectHandle on Responder where object should be placed.</span></span>
- <span data-ttu-id="1cc86-549">**object**: puntero que señala al contenedor de información del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-549">**object**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-550">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-550">Return Value</span></span>

- <span data-ttu-id="1cc86-551">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-551">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="1cc86-553">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-553">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-554">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-554">Example</span></span>

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a><span data-ttu-id="1cc86-555">ux_host_class_pima_object_open</span><span class="sxs-lookup"><span data-stu-id="1cc86-555">ux_host_class_pima_object_open</span></span>

<span data-ttu-id="1cc86-556">Apertura de un objeto almacenado en el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-556">Open an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-557">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-557">Prototype</span></span>

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="1cc86-558">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-558">Description</span></span>

<span data-ttu-id="1cc86-559">Esta función abre un objeto en el respondedor antes de la lectura o escritura.</span><span class="sxs-lookup"><span data-stu-id="1cc86-559">This function opens an object on the responder before reading or writing.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-560">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-560">Parameters</span></span>

- <span data-ttu-id="1cc86-561">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-561">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-562">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-562">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="1cc86-563">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-563">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="1cc86-564">**object**: puntero que señala al contenedor de información del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-564">**objec**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-565">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-565">Return Value</span></span>

- <span data-ttu-id="1cc86-566">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-566">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="1cc86-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) El objeto ya se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Object already opened.</span></span>
- <span data-ttu-id="1cc86-569">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-569">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-570">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-570">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="1cc86-571">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-571">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="1cc86-572">Obtención de un objeto almacenado en el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-572">Get an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-573">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-573">Prototype</span></span>

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a><span data-ttu-id="1cc86-574">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-574">Description</span></span>

<span data-ttu-id="1cc86-575">Esta función obtiene un objeto del respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-575">This function gets an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-576">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-576">Parameters</span></span>

- <span data-ttu-id="1cc86-577">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-577">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-578">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-578">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="1cc86-579">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-579">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="1cc86-580">**object**: puntero que señala al contenedor de información del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-580">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="1cc86-581">**object_buffer**: dirección de los datos del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-581">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="1cc86-582">**object_buffer_length**: longitud solicitada del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-582">**object_buffer_length**: Requested length of object</span></span>
- <span data-ttu-id="1cc86-583">**object_actual_length**: longitud del objeto devuelto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-583">**object_actual_length**: Length of object returned</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-584">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-584">Return Value</span></span>

- <span data-ttu-id="1cc86-585">**UX_SUCCESS**: (0x00): se ha transferido el objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-585">**UX_SUCCESS**: (0x00) The object was transfered</span></span>
- <span data-ttu-id="1cc86-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="1cc86-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023): el objeto no está abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="1cc86-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f): acceso al objeto denegado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="1cc86-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007): la transferencia no está completa.</span><span class="sxs-lookup"><span data-stu-id="1cc86-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="1cc86-590">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-590">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="1cc86-591">**UX_TRANSFER_ERROR**: (0x23): error de transferencia al leer el objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-591">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-592">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-592">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a><span data-ttu-id="1cc86-593">ux_host_class_pima_object_send</span><span class="sxs-lookup"><span data-stu-id="1cc86-593">ux_host_class_pima_object_send</span></span>

<span data-ttu-id="1cc86-594">Envío de un objeto almacenado en el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-594">Send an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-595">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-595">Prototype</span></span>

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a><span data-ttu-id="1cc86-596">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-596">Description</span></span>

<span data-ttu-id="1cc86-597">Esta función envía un objeto al respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-597">This function sends an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-598">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-598">Parameters</span></span>

- <span data-ttu-id="1cc86-599">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-599">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-600">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-600">**pima_sessio**: Pointer to PIMA session</span></span>
- <span data-ttu-id="1cc86-601">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-601">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="1cc86-602">**object**: puntero que señala al contenedor de información del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-602">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="1cc86-603">**object_buffer**: dirección de los datos del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-603">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="1cc86-604">**object_buffer_length**: longitud solicitada del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-604">**object_buffer_length**: Requested length of object</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-605">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-605">Return Value</span></span>

- <span data-ttu-id="1cc86-606">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-606">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="1cc86-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023): el objeto no está abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="1cc86-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f): acceso al objeto denegado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="1cc86-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007): la transferencia no está completa.</span><span class="sxs-lookup"><span data-stu-id="1cc86-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="1cc86-611">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-611">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="1cc86-612">**UX_TRANSFER_ERROR**: (0x23): error de transferencia durante la escritura del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-612">**UX_TRANSFER_ERROR**: (0x23) Transfer error while writing object</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-613">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-613">Example</span></span>

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="1cc86-614">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="1cc86-614">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="1cc86-615">Obtención de un objeto thumb almacenado en el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-615">Get a thumb object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-616">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-616">Prototype</span></span>

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a><span data-ttu-id="1cc86-617">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-617">Description</span></span>

<span data-ttu-id="1cc86-618">Esta función obtiene un objeto thumb del respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-618">This function gets a thumb object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-619">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-619">Parameters</span></span>

- <span data-ttu-id="1cc86-620">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-620">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-621">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-621">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="1cc86-622">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-622">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="1cc86-623">**object**: puntero que señala al contenedor de información del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-623">**object**: Pointer to object information container.</span></span>
- <span data-ttu-id="1cc86-624">**thumb_buffer**: dirección de los datos del objeto thumb.</span><span class="sxs-lookup"><span data-stu-id="1cc86-624">**thumb_buffer**: Address of thumb object data.</span></span>
- <span data-ttu-id="1cc86-625">**thumb_buffer_length**: longitud solicitada del objeto thumb.</span><span class="sxs-lookup"><span data-stu-id="1cc86-625">**thumb_buffer_length**: Requested length of thumb object.</span></span>
- <span data-ttu-id="1cc86-626">**thumb_actual_length**: longitud del objeto thumb devuelto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-626">**thumb_actual_length**: Length of thumb object returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-627">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-627">Return Value</span></span>

- <span data-ttu-id="1cc86-628">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-628">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="1cc86-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023): el objeto no está abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="1cc86-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Acceso al objeto denegado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied.</span></span>
- <span data-ttu-id="1cc86-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) La transferencia no está completa.</span><span class="sxs-lookup"><span data-stu-id="1cc86-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete.</span></span>
- <span data-ttu-id="1cc86-633">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-633">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="1cc86-634">**UX_TRANSFER_ERROR**: (0x23): error de transferencia al leer el objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-634">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-635">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-635">Example</span></span>

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="1cc86-636">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="1cc86-636">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="1cc86-637">Eliminación de un objeto almacenado en el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-637">Delete an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-638">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-638">Prototype</span></span>

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a><span data-ttu-id="1cc86-639">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-639">Description</span></span>

<span data-ttu-id="1cc86-640">Esta función elimina un objeto en el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-640">This function deletes an object on the responder</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-641">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-641">Parameters</span></span>

- <span data-ttu-id="1cc86-642">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-642">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-643">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-643">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="1cc86-644">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-644">**object_handle**: handle of the object</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-645">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-645">Return Value</span></span>

- <span data-ttu-id="1cc86-646">**UX_SUCCESS**: (0x00): se ha eliminado el objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-646">**UX_SUCCESS**: (0x00) The object was deleted.</span></span>
- <span data-ttu-id="1cc86-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="1cc86-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f): no se puede eliminar el objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Cannot delete object.</span></span>
- <span data-ttu-id="1cc86-649">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-649">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-650">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-650">Example</span></span>

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="1cc86-651">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="1cc86-651">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="1cc86-652">Cierre de un objeto almacenado en el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-652">Close an object stored in the Responder</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-653">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-653">Prototype</span></span>

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="1cc86-654">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-654">Description</span></span>

<span data-ttu-id="1cc86-655">Esta función cierra un objeto en el respondedor.</span><span class="sxs-lookup"><span data-stu-id="1cc86-655">This function closes an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-656">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-656">Parameters</span></span>

- <span data-ttu-id="1cc86-657">**pima**: puntero que señala a la instancia de clase PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-657">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1cc86-658">**pima_session**: puntero que señala a la sesión PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-658">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="1cc86-659">**object_handle**: identificador del objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-659">**object_handle**: Handle of the object.</span></span>
- <span data-ttu-id="1cc86-660">**object**: puntero que señala al objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-660">**object**: Pointer to object.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-661">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-661">Return Value</span></span>

- <span data-ttu-id="1cc86-662">**UX_SUCCESS**: (0x00) Se cerró el objeto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-662">**UX_SUCCESS**: (0x00) The object was closed.</span></span>
- <span data-ttu-id="1cc86-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003): la sesión no se ha abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="1cc86-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023): el objeto no está abierto.</span><span class="sxs-lookup"><span data-stu-id="1cc86-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="1cc86-665">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria para crear el comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="1cc86-665">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-666">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-666">Example</span></span>

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a><span data-ttu-id="1cc86-667">ux_host_class_gser_read</span><span class="sxs-lookup"><span data-stu-id="1cc86-667">ux_host_class_gser_read</span></span>

<span data-ttu-id="1cc86-668">Lectura desde la interfaz serie genérica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-668">Read from the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-669">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-669">Prototype</span></span>

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="1cc86-670">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-670">Description</span></span>

<span data-ttu-id="1cc86-671">Esta función lee desde la interfaz serie genérica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-671">This function reads from the generic serial interface.</span></span> <span data-ttu-id="1cc86-672">La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia.</span><span class="sxs-lookup"><span data-stu-id="1cc86-672">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-673">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-673">Parameters</span></span>

- <span data-ttu-id="1cc86-674">**gser**: puntero que señala a la instancia de la clase gser.</span><span class="sxs-lookup"><span data-stu-id="1cc86-674">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="1cc86-675">**interface_index**: índice de interfaz desde el que se va a leer.</span><span class="sxs-lookup"><span data-stu-id="1cc86-675">**interface_index**: Interface index to read from.</span></span>
- <span data-ttu-id="1cc86-676">**data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.</span><span class="sxs-lookup"><span data-stu-id="1cc86-676">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="1cc86-677">**requested_length**: longitud que se va a recibir.</span><span class="sxs-lookup"><span data-stu-id="1cc86-677">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="1cc86-678">**actual_length**: longitud recibida realmente.</span><span class="sxs-lookup"><span data-stu-id="1cc86-678">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-679">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-679">Return Value</span></span>

- <span data-ttu-id="1cc86-680">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-680">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-681">**UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, lectura incompleta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-681">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-682">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-682">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a><span data-ttu-id="1cc86-683">ux_host_class_gser_write</span><span class="sxs-lookup"><span data-stu-id="1cc86-683">ux_host_class_gser_write</span></span>

<span data-ttu-id="1cc86-684">Escritura desde la interfaz serie genérica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-684">Write to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-685">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-685">Prototype</span></span>

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="1cc86-686">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-686">Description</span></span>

<span data-ttu-id="1cc86-687">Esta función escribe desde la interfaz serie genérica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-687">This function writes to the generic serial interface.</span></span> <span data-ttu-id="1cc86-688">La llamada produce un bloqueo, y solo vuelve cuando hay un error o cuando se completa la transferencia.</span><span class="sxs-lookup"><span data-stu-id="1cc86-688">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-689">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-689">Parameters</span></span>

- <span data-ttu-id="1cc86-690">**gser**: puntero que señala a la instancia de la clase gser.</span><span class="sxs-lookup"><span data-stu-id="1cc86-690">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="1cc86-691">**interface_index**: interfaz en la que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="1cc86-691">**interface_index**: Interface to which to write.</span></span>
- <span data-ttu-id="1cc86-692">**data_pointer**: puntero que señala a la dirección del búfer de la carga de datos.</span><span class="sxs-lookup"><span data-stu-id="1cc86-692">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="1cc86-693">**requested_length**: longitud que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="1cc86-693">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="1cc86-694">**actual_length**: longitud enviada realmente.</span><span class="sxs-lookup"><span data-stu-id="1cc86-694">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-695">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-695">Return Value</span></span>

- <span data-ttu-id="1cc86-696">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-696">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-697">**UX_TRANSFER_TIMEOUT**: (0x5c): se ha agotado el tiempo de espera de la transferencia, escritura incompleta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-697">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-698">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-698">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a><span data-ttu-id="1cc86-699">ux_host_class_gser_ioctl</span><span class="sxs-lookup"><span data-stu-id="1cc86-699">ux_host_class_gser_ioctl</span></span>

<span data-ttu-id="1cc86-700">Realización de una función IOCTL en la interfaz serie genérica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-700">Perform an IOCTL function to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-701">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-701">Prototype</span></span>

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a><span data-ttu-id="1cc86-702">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-702">Description</span></span>

<span data-ttu-id="1cc86-703">Esta función realiza una función IOCTL específica en la interfaz gser.</span><span class="sxs-lookup"><span data-stu-id="1cc86-703">This function performs a specific ioctl function to the gser interface.</span></span> <span data-ttu-id="1cc86-704">La llamada produce un bloqueo, y solo devuelve cuando hay un error o cuando se completa el comando.</span><span class="sxs-lookup"><span data-stu-id="1cc86-704">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-705">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-705">Parameters</span></span>

- <span data-ttu-id="1cc86-706">**gser**: puntero que señala a la instancia de la clase gser.</span><span class="sxs-lookup"><span data-stu-id="1cc86-706">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="1cc86-707">**ioctl_function**: función IOCTL que se va a realizar.</span><span class="sxs-lookup"><span data-stu-id="1cc86-707">**ioctl_function**: ioctl function to be performed.</span></span> <span data-ttu-id="1cc86-708">Vea la tabla siguiente para ver las funciones IOCTL permitidas.</span><span class="sxs-lookup"><span data-stu-id="1cc86-708">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="1cc86-709">**parameter**: puntero que señala a un parámetro específico de IOCTL.</span><span class="sxs-lookup"><span data-stu-id="1cc86-709">**parameter**: Pointerto a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-710">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-710">Return Value</span></span>

- <span data-ttu-id="1cc86-711">**UX_SUCCESS**: (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-711">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-712">**UX_MEMORY_INSUFFICIENT**: (0x12): no hay suficiente memoria.</span><span class="sxs-lookup"><span data-stu-id="1cc86-712">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory.</span></span>
- <span data-ttu-id="1cc86-713">**UX_HOST_CLASS_UNKNOWN**: (0x59): la instancia de clase es incorrecta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) Wrong class instance</span></span>
- <span data-ttu-id="1cc86-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54): la función de IOCTL es desconocida.</span><span class="sxs-lookup"><span data-stu-id="1cc86-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="1cc86-715">Funciones IOCTL</span><span class="sxs-lookup"><span data-stu-id="1cc86-715">IOCTL functions</span></span>

- <span data-ttu-id="1cc86-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="1cc86-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="1cc86-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="1cc86-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="1cc86-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="1cc86-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="1cc86-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="1cc86-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="1cc86-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="1cc86-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="1cc86-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="1cc86-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="1cc86-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="1cc86-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="1cc86-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="1cc86-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-724">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-724">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a><span data-ttu-id="1cc86-725">ux_host_class_gser_reception_start</span><span class="sxs-lookup"><span data-stu-id="1cc86-725">ux_host_class_gser_reception_start</span></span>

<span data-ttu-id="1cc86-726">Inicio de la recepción en la interfaz serie genérica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-726">Start reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-727">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-727">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="1cc86-728">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-728">Description</span></span>

<span data-ttu-id="1cc86-729">Esta función inicia la recepción en la interfaz de clase serie genérica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-729">This function starts the reception on the generic serial class interface.</span></span> <span data-ttu-id="1cc86-730">Esta función permite la recepción sin bloqueo.</span><span class="sxs-lookup"><span data-stu-id="1cc86-730">This function allows for non-blocking reception.</span></span> <span data-ttu-id="1cc86-731">Cuando se recibe un búfer, se invoca una devolución de llamada en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1cc86-731">When a buffer is received, a callback in invoked into the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-732">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-732">Parameters</span></span>

- <span data-ttu-id="1cc86-733">**gser**: puntero que señala a la instancia de la clase gser.</span><span class="sxs-lookup"><span data-stu-id="1cc86-733">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="1cc86-734">**gser_reception**: estructura que contiene los parámetros de recepción.</span><span class="sxs-lookup"><span data-stu-id="1cc86-734">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-735">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-735">Return Value</span></span>

- <span data-ttu-id="1cc86-736">**UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-736">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-737">**UX_HOST_CLASS_UNKNOWN** (0x59): la instancia de clase es incorrecta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-737">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="1cc86-738">**UX_ERROR** (0x01): error</span><span class="sxs-lookup"><span data-stu-id="1cc86-738">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-739">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-739">Example</span></span>

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a><span data-ttu-id="1cc86-740">ux_host_class_gser_reception_stop</span><span class="sxs-lookup"><span data-stu-id="1cc86-740">ux_host_class_gser_reception_stop</span></span>

<span data-ttu-id="1cc86-741">Detención de recepción en la interfaz serie genérica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-741">Stop reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="1cc86-742">Prototipo</span><span class="sxs-lookup"><span data-stu-id="1cc86-742">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="1cc86-743">Descripción</span><span class="sxs-lookup"><span data-stu-id="1cc86-743">Description</span></span>

<span data-ttu-id="1cc86-744">Esta función detiene la recepción en la interfaz de clase serie genérica.</span><span class="sxs-lookup"><span data-stu-id="1cc86-744">This function stops the reception on the generic serial class interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="1cc86-745">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1cc86-745">Parameters</span></span>

- <span data-ttu-id="1cc86-746">**gser**: puntero que señala a la instancia de la clase gser.</span><span class="sxs-lookup"><span data-stu-id="1cc86-746">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="1cc86-747">**gser_reception**: estructura que contiene los parámetros de recepción.</span><span class="sxs-lookup"><span data-stu-id="1cc86-747">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="1cc86-748">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1cc86-748">Return Value</span></span>

- <span data-ttu-id="1cc86-749">**UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="1cc86-749">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="1cc86-750">**UX_HOST_CLASS_UNKNOWN** (0x59): la instancia de clase es incorrecta.</span><span class="sxs-lookup"><span data-stu-id="1cc86-750">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="1cc86-751">**UX_ERROR** (0x01): error</span><span class="sxs-lookup"><span data-stu-id="1cc86-751">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="1cc86-752">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1cc86-752">Example</span></span>

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
