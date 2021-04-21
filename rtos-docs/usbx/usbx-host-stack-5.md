---
title: 'Capítulo 5: API de clases de host de USBX'
description: Obtenga información sobre la API de clases de host de USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bf5876042e08a59979adcd429917bfc3fbfdbc20
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816466"
---
# <a name="chapter-5---usbx-host-classes-api"></a><span data-ttu-id="0d837-103">Capítulo 5: API de clases de host de USBX</span><span class="sxs-lookup"><span data-stu-id="0d837-103">Chapter 5 - USBX Host Classes API</span></span>

<span data-ttu-id="0d837-104">En este capítulo se tratan todas las API expuestas de las clases de host de USBX.</span><span class="sxs-lookup"><span data-stu-id="0d837-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="0d837-105">Se describen en detalle las siguientes API de cada clase.</span><span class="sxs-lookup"><span data-stu-id="0d837-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="0d837-106">Clase HID</span><span class="sxs-lookup"><span data-stu-id="0d837-106">HID class</span></span>
- <span data-ttu-id="0d837-107">Clase CDC/ACM</span><span class="sxs-lookup"><span data-stu-id="0d837-107">CDC-ACM class</span></span>
- <span data-ttu-id="0d837-108">Clase CDC/ECM</span><span class="sxs-lookup"><span data-stu-id="0d837-108">CDC-ECM class</span></span>
- <span data-ttu-id="0d837-109">Clase de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="0d837-109">Storage class</span></span>

## <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="0d837-110">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="0d837-110">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="0d837-111">Registra un cliente HID en la clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-111">Register a HID client to the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-112">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-112">Prototype</span></span>

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="0d837-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-113">Description</span></span>

<span data-ttu-id="0d837-114">Esta función se usa para registrar un cliente HID en la clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-114">This function is used to register a HID client to the HID class.</span></span> <span data-ttu-id="0d837-115">La clase HID debe encontrar una coincidencia entre un dispositivo HID y el cliente HID antes de solicitar datos de este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0d837-115">The HID class needs to find a match between a HID device and HID client before requesting data from this device.</span></span>

> [!NOTE]
> <span data-ttu-id="0d837-116">La cadena de C de hid_client_name debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="0d837-116">The C string of hid_client_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-117">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-117">Parameters</span></span>

- <span data-ttu-id="0d837-118">**hid_client_name**: puntero al nombre del cliente HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-118">**hid_client_name** Pointer to the HID client name.</span></span>
- <span data-ttu-id="0d837-119">**hid_client_handler**: puntero al controlador del cliente HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-119">**hid_client_handler** Pointer to the HID client handler.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-120">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-120">Return Values</span></span>

- <span data-ttu-id="0d837-121">**UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.</span><span class="sxs-lookup"><span data-stu-id="0d837-121">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="0d837-122">**UX_MEMORY_INSUFFICIENT** (0X12): error de asignación de memoria para el cliente.</span><span class="sxs-lookup"><span data-stu-id="0d837-122">**UX_MEMORY_INSUFFICIENT** (0x12) Memory allocation for client failed.</span></span>
- <span data-ttu-id="0d837-123">**UX_MEMORY_ARRAY_FULL** (0X1a): ya se ha registrado el número máximo de clientes.</span><span class="sxs-lookup"><span data-stu-id="0d837-123">**UX_MEMORY_ARRAY_FULL** (0x1a) Max clients already registered.</span></span>
- <span data-ttu-id="0d837-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0X58): esta clase ya existe.</span><span class="sxs-lookup"><span data-stu-id="0d837-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) This class already exists</span></span>

### <a name="example"></a><span data-ttu-id="0d837-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-125">Example</span></span>

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a><span data-ttu-id="0d837-126">ux_host_class_hid_report_callback_register</span><span class="sxs-lookup"><span data-stu-id="0d837-126">ux_host_class_hid_report_callback_register</span></span>

<span data-ttu-id="0d837-127">Registra una devolución de llamada de la clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-127">Register a callback from the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-128">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-128">Prototype</span></span>

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a><span data-ttu-id="0d837-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-129">Description</span></span>

<span data-ttu-id="0d837-130">Esta función se usa para registrar una devolución de llamada de la clase HID al cliente HID cuando se recibe un informe.</span><span class="sxs-lookup"><span data-stu-id="0d837-130">This function is used to register a callback from the HID class to the HID client when a report is received.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-131">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-131">Parameters</span></span>

- <span data-ttu-id="0d837-132">**HID**: puntero a la instancia de la clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-132">**hid** Pointer to the HID class instance</span></span>
- <span data-ttu-id="0d837-133">**call_back**: puntero a la estructura de devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="0d837-133">**call_back** Pointer to the call_back structure</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-134">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-134">Return values</span></span>

- <span data-ttu-id="0d837-135">**UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.</span><span class="sxs-lookup"><span data-stu-id="0d837-135">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="0d837-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): instancia de HID no válida.</span><span class="sxs-lookup"><span data-stu-id="0d837-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Invalid HID instance.</span></span>
- <span data-ttu-id="0d837-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79): error en el registro de devolución de llamada del informe.</span><span class="sxs-lookup"><span data-stu-id="0d837-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Error in the report callback registration.</span></span>

### <a name="example"></a><span data-ttu-id="0d837-138">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-138">Example</span></span>

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a><span data-ttu-id="0d837-139">ux_host_class_hid_periodic_report_start</span><span class="sxs-lookup"><span data-stu-id="0d837-139">ux_host_class_hid_periodic_report_start</span></span>

<span data-ttu-id="0d837-140">Inicia el punto de conexión periódico para una instancia de clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-140">Start the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-141">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-141">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="0d837-142">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-142">Description</span></span>

<span data-ttu-id="0d837-143">Esta función se usa para iniciar el punto de conexión (interrupción) periódico de la instancia de la clase HID enlazada a este cliente HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-143">This function is used to start the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="0d837-144">La clase HID no puede iniciar el punto de conexión periódico hasta que se active el cliente HID y, por lo tanto, es el cliente HID quien tiene que iniciar este punto de conexión para recibir informes.</span><span class="sxs-lookup"><span data-stu-id="0d837-144">The HID class cannot start the periodic endpoint until the HID client is activated and therefore it is left to the HID client to start this endpoint to receive reports.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="0d837-145">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="0d837-145">Input Parameter</span></span>

- <span data-ttu-id="0d837-146">**HID** Puntero a la instancia de la clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-146">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-147">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-147">Return Values</span></span>

- <span data-ttu-id="0d837-148">**UX_SUCCESS** (0x00): los informes periódicos se han iniciado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0d837-148">**UX_SUCCESS** (0x00) Periodic reporting successfully started.</span></span>
- <span data-ttu-id="0d837-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A): error en el informe periódico.</span><span class="sxs-lookup"><span data-stu-id="0d837-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="0d837-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.</span><span class="sxs-lookup"><span data-stu-id="0d837-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="0d837-151">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-151">Example</span></span>

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a><span data-ttu-id="0d837-152">ux_host_class_hid_periodic_report_stop</span><span class="sxs-lookup"><span data-stu-id="0d837-152">ux_host_class_hid_periodic_report_stop</span></span>

<span data-ttu-id="0d837-153">Detiene el punto de conexión periódico para una instancia de clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-153">Stop the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-154">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-154">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="0d837-155">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-155">Description</span></span>

<span data-ttu-id="0d837-156">Esta función se usa para detener el punto de conexión (interrupción) periódico de la instancia de la clase HID enlazada a este cliente HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-156">This function is used to stop the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="0d837-157">La clase HID no puede detener el punto de conexión periódico hasta que se desactive el cliente HID y se liberen todos sus recursos, por lo tanto, es el cliente HID quien tiene que detener este punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="0d837-157">The HID class cannot stop the periodic endpoint until the HID client is deactivated, all its resources freed and therefore it is left to the HID client to stop this endpoint.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="0d837-158">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="0d837-158">Input Parameter</span></span>

- <span data-ttu-id="0d837-159">**HID** Puntero a la instancia de la clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-159">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-160">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-160">Return Values</span></span>

- <span data-ttu-id="0d837-161">**UX_SUCCESS** (0x00): los informes periódicos se detuvieron correctamente.</span><span class="sxs-lookup"><span data-stu-id="0d837-161">**UX_SUCCESS** (0x00) Periodic reporting successfully stopped.</span></span>
- <span data-ttu-id="0d837-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A): error en el informe periódico.</span><span class="sxs-lookup"><span data-stu-id="0d837-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="0d837-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.</span><span class="sxs-lookup"><span data-stu-id="0d837-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist</span></span>

### <a name="example"></a><span data-ttu-id="0d837-164">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-164">Example</span></span>

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="0d837-165">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="0d837-165">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="0d837-166">Obtiene un informe de una instancia de la clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-166">Get a report from a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-167">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-167">Prototype</span></span>

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="0d837-168">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-168">Description</span></span>

<span data-ttu-id="0d837-169">Esta función se usa para recibir un informe directamente del dispositivo sin depender del punto de conexión periódico.</span><span class="sxs-lookup"><span data-stu-id="0d837-169">This function is used to receive a report directly from the device without relying on the periodic endpoint.</span></span> <span data-ttu-id="0d837-170">Este informe procede del punto de conexión de control, pero su tratamiento es el mismo que si estuviera en el punto de conexión periódico.</span><span class="sxs-lookup"><span data-stu-id="0d837-170">This report is coming from the control endpoint but its treatment is the same as though it were coming on the periodic endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-171">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-171">Parameters</span></span>

- <span data-ttu-id="0d837-172">**HID** Puntero a la instancia de la clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-172">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="0d837-173">**client_report** Puntero al informe de cliente HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-173">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-174">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-174">Return Values</span></span>

- <span data-ttu-id="0d837-175">**UX_SUCCESS** (0X00): el informe se ha recibido correctamente.</span><span class="sxs-lookup"><span data-stu-id="0d837-175">**UX_SUCCESS** (0x00) The report was successfully received.</span></span>
- <span data-ttu-id="0d837-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0X70): el informe de cliente no era válido o se produjo un error durante la transferencia.</span><span class="sxs-lookup"><span data-stu-id="0d837-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="0d837-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.</span><span class="sxs-lookup"><span data-stu-id="0d837-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="0d837-178">**UX_BUFFER_OVERFLOW** (0X5d): el búfer proporcionado no es suficientemente grande para alojar el informe sin comprimir.</span><span class="sxs-lookup"><span data-stu-id="0d837-178">**UX_BUFFER_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="0d837-179">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-179">Example</span></span>

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="0d837-180">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="0d837-180">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="0d837-181">Envía un informe.</span><span class="sxs-lookup"><span data-stu-id="0d837-181">Send a report</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-182">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-182">Prototype</span></span>

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="0d837-183">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-183">Description</span></span>

<span data-ttu-id="0d837-184">Esta función se usa para enviar un informe directamente al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0d837-184">This function is used to send a report directly to the device.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-185">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-185">Parameters</span></span>

- <span data-ttu-id="0d837-186">**HID**: puntero a la instancia de la clase HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-186">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="0d837-187">**client_report**: puntero al informe de cliente HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-187">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-188">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-188">Return Values</span></span>

- <span data-ttu-id="0d837-189">**UX_SUCCESS** (0X00): el informe se ha enviado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0d837-189">**UX_SUCCESS** (0x00) The report was successfully sent.</span></span>
- <span data-ttu-id="0d837-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0X70): el informe de cliente no era válido o se produjo un error durante la transferencia.</span><span class="sxs-lookup"><span data-stu-id="0d837-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="0d837-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.</span><span class="sxs-lookup"><span data-stu-id="0d837-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="0d837-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0X5d): el búfer proporcionado no es suficientemente grande para alojar el informe sin comprimir.</span><span class="sxs-lookup"><span data-stu-id="0d837-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="0d837-193">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-193">Example</span></span>

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a><span data-ttu-id="0d837-194">ux_host_class_hid_mouse_buttons_get</span><span class="sxs-lookup"><span data-stu-id="0d837-194">ux_host_class_hid_mouse_buttons_get</span></span>

<span data-ttu-id="0d837-195">Obtiene los botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="0d837-195">Get mouse buttons.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-196">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-196">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a><span data-ttu-id="0d837-197">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-197">Description</span></span>

<span data-ttu-id="0d837-198">Esta función se usa para obtener los botones del mouse.</span><span class="sxs-lookup"><span data-stu-id="0d837-198">This function is used to get the mouse buttons</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-199">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-199">Parameters</span></span>

- <span data-ttu-id="0d837-200">**mouse_instance**: puntero a la instancia del mouse HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-200">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="0d837-201">**mouse_buttons**: puntero a los botones devueltos.</span><span class="sxs-lookup"><span data-stu-id="0d837-201">**mouse_buttons** Pointer to the return buttons.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-202">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-202">Return Values</span></span>

- <span data-ttu-id="0d837-203">**UX_SUCCESS** (0x00): se recuperó correctamente el botón del mouse.</span><span class="sxs-lookup"><span data-stu-id="0d837-203">**UX_SUCCESS** (0x00) Mouse button successfully retrieved.</span></span>
- <span data-ttu-id="0d837-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.</span><span class="sxs-lookup"><span data-stu-id="0d837-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="0d837-205">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-205">Example</span></span>

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a><span data-ttu-id="0d837-206">ux_host_class_hid_mouse_position_get</span><span class="sxs-lookup"><span data-stu-id="0d837-206">ux_host_class_hid_mouse_position_get</span></span>

<span data-ttu-id="0d837-207">Obtiene la posición del mouse.</span><span class="sxs-lookup"><span data-stu-id="0d837-207">Get mouse position.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-208">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-208">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a><span data-ttu-id="0d837-209">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-209">Description</span></span>

<span data-ttu-id="0d837-210">Esta función se usa para obtener la posición del mouse en coordenadas X e Y.</span><span class="sxs-lookup"><span data-stu-id="0d837-210">This function is used to get the mouse position in x & y coordinates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-211">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-211">Parameters</span></span>

- <span data-ttu-id="0d837-212">**mouse_instance**: puntero a la instancia del mouse HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-212">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="0d837-213">**mouse_x_position**: puntero a la coordenada X.</span><span class="sxs-lookup"><span data-stu-id="0d837-213">**mouse_x_position** Pointer to the x coordinate.</span></span>
- <span data-ttu-id="0d837-214">**mouse_y_position**: puntero a la coordenada Y.</span><span class="sxs-lookup"><span data-stu-id="0d837-214">**mouse_y_position** Pointer to the y coordinate.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-215">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-215">Return Values</span></span>

- <span data-ttu-id="0d837-216">**UX_SUCCESS** (0X00): se han recuperado correctamente las coordenadas X e Y.</span><span class="sxs-lookup"><span data-stu-id="0d837-216">**UX_SUCCESS** (0x00) X &amp; Y coordinates successfully retrieved.</span></span>
- <span data-ttu-id="0d837-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.</span><span class="sxs-lookup"><span data-stu-id="0d837-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="0d837-218">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-218">Example</span></span>

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a><span data-ttu-id="0d837-219">ux_host_class_hid_keyboard_key_get</span><span class="sxs-lookup"><span data-stu-id="0d837-219">ux_host_class_hid_keyboard_key_get</span></span>

<span data-ttu-id="0d837-220">Obtiene la tecla y el estado del teclado.</span><span class="sxs-lookup"><span data-stu-id="0d837-220">Get keyboard key and state.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-221">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-221">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a><span data-ttu-id="0d837-222">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-222">Description</span></span>

<span data-ttu-id="0d837-223">Esta función se usa para obtener la tecla y el estado del teclado.</span><span class="sxs-lookup"><span data-stu-id="0d837-223">This function is used to get the keyboard key and state.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-224">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-224">Parameters</span></span>

- <span data-ttu-id="0d837-225">**keyboard_instance**: puntero a la instancia del teclado HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-225">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="0d837-226">**keyboard_key**: puntero al contenedor de claves del teclado.</span><span class="sxs-lookup"><span data-stu-id="0d837-226">**keyboard_key** Pointer to keyboard key container.</span></span>
- <span data-ttu-id="0d837-227">**keyboard_state**: puntero al contenedor de estados del teclado.</span><span class="sxs-lookup"><span data-stu-id="0d837-227">**keyboard_state** Pointer to the keyboard state container.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-228">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-228">Return Values</span></span>

- <span data-ttu-id="0d837-229">**UX_SUCCESS** (0x00): se han recuperado correctamente la clave y el estado.</span><span class="sxs-lookup"><span data-stu-id="0d837-229">**UX_SUCCESS** (0x00) Key and state successfully retrieved.</span></span>
- <span data-ttu-id="0d837-230">**UX_ERROR** (0Xff): no hay nada que notificar.</span><span class="sxs-lookup"><span data-stu-id="0d837-230">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="0d837-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.</span><span class="sxs-lookup"><span data-stu-id="0d837-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="0d837-232">El estado del teclado puede tener los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="0d837-232">The keyboard state can have the following values.</span></span>

- <span data-ttu-id="0d837-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span><span class="sxs-lookup"><span data-stu-id="0d837-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span></span>
- <span data-ttu-id="0d837-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span><span class="sxs-lookup"><span data-stu-id="0d837-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span></span>
- <span data-ttu-id="0d837-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="0d837-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span></span>
- <span data-ttu-id="0d837-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span><span class="sxs-lookup"><span data-stu-id="0d837-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span></span>
- <span data-ttu-id="0d837-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span><span class="sxs-lookup"><span data-stu-id="0d837-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span></span>
- <span data-ttu-id="0d837-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span><span class="sxs-lookup"><span data-stu-id="0d837-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span></span>
- <span data-ttu-id="0d837-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span><span class="sxs-lookup"><span data-stu-id="0d837-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span></span>
- <span data-ttu-id="0d837-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span><span class="sxs-lookup"><span data-stu-id="0d837-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span></span>
- <span data-ttu-id="0d837-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span><span class="sxs-lookup"><span data-stu-id="0d837-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span></span>
- <span data-ttu-id="0d837-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span><span class="sxs-lookup"><span data-stu-id="0d837-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span></span>
- <span data-ttu-id="0d837-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span><span class="sxs-lookup"><span data-stu-id="0d837-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span></span>
- <span data-ttu-id="0d837-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span><span class="sxs-lookup"><span data-stu-id="0d837-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span></span>
- <span data-ttu-id="0d837-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span><span class="sxs-lookup"><span data-stu-id="0d837-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span></span>
- <span data-ttu-id="0d837-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span><span class="sxs-lookup"><span data-stu-id="0d837-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span></span>
- <span data-ttu-id="0d837-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span><span class="sxs-lookup"><span data-stu-id="0d837-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span></span>
- <span data-ttu-id="0d837-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span><span class="sxs-lookup"><span data-stu-id="0d837-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span></span>
- <span data-ttu-id="0d837-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span><span class="sxs-lookup"><span data-stu-id="0d837-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span></span>

### <a name="example"></a><span data-ttu-id="0d837-250">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-250">Example</span></span>

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a><span data-ttu-id="0d837-251">ux_host_class_hid_keyboard_ioctl</span><span class="sxs-lookup"><span data-stu-id="0d837-251">ux_host_class_hid_keyboard_ioctl</span></span>

<span data-ttu-id="0d837-252">Realiza una función IOCTL en el teclado HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-252">Perform an IOCTL function to the HID keyboard.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-253">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-253">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0d837-254">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-254">Description</span></span>

<span data-ttu-id="0d837-255">Esta función realiza una función IOCTL específica en el teclado HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-255">This function performs a specific ioctl function to the HID keyboard.</span></span> <span data-ttu-id="0d837-256">La llamada produce un bloqueo, y solo devuelve un resultado cuando hay un error o cuando se completa el comando.</span><span class="sxs-lookup"><span data-stu-id="0d837-256">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-257">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-257">Parameters</span></span>

- <span data-ttu-id="0d837-258">**keyboard_instance**: puntero a la instancia del teclado HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-258">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="0d837-259">**ioctl_function**: función IOCTL que se va a realizar.</span><span class="sxs-lookup"><span data-stu-id="0d837-259">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="0d837-260">Vea la tabla siguiente para ver una de las funciones IOCTL permitidas.</span><span class="sxs-lookup"><span data-stu-id="0d837-260">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="0d837-261">**parameter**: puntero a un parámetro específico de IOCTL.</span><span class="sxs-lookup"><span data-stu-id="0d837-261">**parameter** Pointer to a parameter specific to the ioctl.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-262">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-262">Return Values</span></span>

- <span data-ttu-id="0d837-263">**UX_SUCCESS** (0X00): la función IOCTL se ha completado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0d837-263">**UX_SUCCESS** (0x00) The ioctl function completed successfully.</span></span>
- <span data-ttu-id="0d837-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54): función IOCTL desconocida.</span><span class="sxs-lookup"><span data-stu-id="0d837-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="0d837-265">Funciones IOCTL</span><span class="sxs-lookup"><span data-stu-id="0d837-265">IOCTL functions</span></span>

- <span data-ttu-id="0d837-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="0d837-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span></span>
- <span data-ttu-id="0d837-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span><span class="sxs-lookup"><span data-stu-id="0d837-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span></span>
- <span data-ttu-id="0d837-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span><span class="sxs-lookup"><span data-stu-id="0d837-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span></span>

### <a name="example--change-keyboard-layout"></a><span data-ttu-id="0d837-269">Ejemplo: cambio de la distribución del teclado</span><span class="sxs-lookup"><span data-stu-id="0d837-269">Example – change keyboard layout</span></span>

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a><span data-ttu-id="0d837-270">Ejemplo: deshabilitación de la descodificación de teclas del teclado</span><span class="sxs-lookup"><span data-stu-id="0d837-270">Example – disable keyboard key decode</span></span>

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a><span data-ttu-id="0d837-271">ux_host_class_hid_remote_control_usage_get</span><span class="sxs-lookup"><span data-stu-id="0d837-271">ux_host_class_hid_remote_control_usage_get</span></span>

<span data-ttu-id="0d837-272">Obtención del uso del control remoto</span><span class="sxs-lookup"><span data-stu-id="0d837-272">Get remote control usage</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-273">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-273">Prototype</span></span>

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a><span data-ttu-id="0d837-274">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-274">Description</span></span>

<span data-ttu-id="0d837-275">Esta función se usa para obtener los usos del control remoto.</span><span class="sxs-lookup"><span data-stu-id="0d837-275">This function is used to get the remote control usages.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-276">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-276">Parameters</span></span>

- <span data-ttu-id="0d837-277">**remote_control_instance**: puntero a la instancia del control remoto HID.</span><span class="sxs-lookup"><span data-stu-id="0d837-277">**remote_control_instance** Pointer to the HID remote control instance.</span></span>
- <span data-ttu-id="0d837-278">**usage**: puntero al uso.</span><span class="sxs-lookup"><span data-stu-id="0d837-278">**usage** Pointer to the usage.</span></span>
- <span data-ttu-id="0d837-279">**value**: puntero al valor del uso.</span><span class="sxs-lookup"><span data-stu-id="0d837-279">**value** Pointer to the value for the usage.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-280">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-280">Return Values</span></span>

- <span data-ttu-id="0d837-281">**UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.</span><span class="sxs-lookup"><span data-stu-id="0d837-281">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="0d837-282">**UX_ERROR** (0Xff): no hay nada que notificar.</span><span class="sxs-lookup"><span data-stu-id="0d837-282">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="0d837-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): la instancia de la clase HID no existe.</span><span class="sxs-lookup"><span data-stu-id="0d837-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="0d837-284">La lista de todos los usos posibles es demasiado larga para caber en esta guía de usuario.</span><span class="sxs-lookup"><span data-stu-id="0d837-284">The list of all possible usages is too long to fit in this user guide.</span></span> <span data-ttu-id="0d837-285">Si quiere obtener una descripción completa, ux_host_class_hid.h tiene el conjunto completo de valores posibles.</span><span class="sxs-lookup"><span data-stu-id="0d837-285">For a full description, the ux_host_class_hid.h has the entire set of possible values.</span></span>

### <a name="example"></a><span data-ttu-id="0d837-286">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-286">Example</span></span>

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="0d837-287">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="0d837-287">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="0d837-288">Lee desde la interfaz cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-288">Read from the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-289">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-289">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="0d837-290">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-290">Description</span></span>

<span data-ttu-id="0d837-291">Esta función lee desde la interfaz cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-291">This function reads from the cdc_acm interface.</span></span> <span data-ttu-id="0d837-292">La llamada produce un bloqueo, y solo devuelve un resultado cuando hay un error o cuando se completa la transferencia.</span><span class="sxs-lookup"><span data-stu-id="0d837-292">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-293">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-293">Parameters</span></span>

- <span data-ttu-id="0d837-294">**cdc_acm**: puntero a la instancia de la clase cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-294">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="0d837-295">**data_pointer**: puntero a la dirección del búfer de la carga de datos.</span><span class="sxs-lookup"><span data-stu-id="0d837-295">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="0d837-296">**requested_length**: longitud que se va a recibir.</span><span class="sxs-lookup"><span data-stu-id="0d837-296">**requested_length** Length to be received.</span></span>
- <span data-ttu-id="0d837-297">**actual_length**: longitud recibida realmente.</span><span class="sxs-lookup"><span data-stu-id="0d837-297">**actual_length** Length actually received.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-298">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-298">Return Values</span></span>

- <span data-ttu-id="0d837-299">**UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.</span><span class="sxs-lookup"><span data-stu-id="0d837-299">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="0d837-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b): la instancia de cdc_acm no es válida.</span><span class="sxs-lookup"><span data-stu-id="0d837-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="0d837-301">**UX_TRANSFER_TIMEOUT** (0x5c): se ha agotado el tiempo de espera de la transferencia, lectura incompleta.</span><span class="sxs-lookup"><span data-stu-id="0d837-301">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="0d837-302">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-302">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a><span data-ttu-id="0d837-303">ux_host_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="0d837-303">ux_host_class_cdc_acm_write</span></span>

<span data-ttu-id="0d837-304">Escribe en la interfaz cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-304">Write to the cdc_acm interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-305">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-305">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="0d837-306">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-306">Description</span></span>

<span data-ttu-id="0d837-307">Esta función escribe en la interfaz cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-307">This function writes to the cdc_acm interface.</span></span> <span data-ttu-id="0d837-308">La llamada produce un bloqueo, y solo devuelve un resultado cuando hay un error o cuando se completa la transferencia.</span><span class="sxs-lookup"><span data-stu-id="0d837-308">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-309">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-309">Parameters</span></span>

- <span data-ttu-id="0d837-310">**cdc_acm**: puntero a la instancia de la clase cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-310">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="0d837-311">**data_pointer**: puntero a la dirección del búfer de la carga de datos.</span><span class="sxs-lookup"><span data-stu-id="0d837-311">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="0d837-312">**requested_length**: longitud que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="0d837-312">**requested_length** Length to be sent.</span></span>
- <span data-ttu-id="0d837-313">**actual_length**: longitud enviada realmente.</span><span class="sxs-lookup"><span data-stu-id="0d837-313">**actual_length** Length actually sent.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d837-314">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="0d837-314">Return Values</span></span>

- <span data-ttu-id="0d837-315">**UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.</span><span class="sxs-lookup"><span data-stu-id="0d837-315">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="0d837-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b): la instancia de cdc_acm no es válida.</span><span class="sxs-lookup"><span data-stu-id="0d837-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="0d837-317">**UX_TRANSFER_TIMEOUT** (0x5c): se ha agotado el tiempo de espera de la transferencia, escritura incompleta.</span><span class="sxs-lookup"><span data-stu-id="0d837-317">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="0d837-318">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0d837-318">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a><span data-ttu-id="0d837-319">ux_host_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="0d837-319">ux_host_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="0d837-320">Realiza una función IOCTL en la interfaz cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-320">Perform an IOCTL function to the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-321">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-321">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="0d837-322">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-322">Description</span></span>

<span data-ttu-id="0d837-323">Esta función realiza una función IOCTL específica en la interfaz cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-323">This function performs a specific ioctl function to the cdc_acm interface.</span></span> <span data-ttu-id="0d837-324">La llamada produce un bloqueo, y solo devuelve un resultado cuando hay un error o cuando se completa el comando.</span><span class="sxs-lookup"><span data-stu-id="0d837-324">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-325">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-325">Parameters</span></span>

- <span data-ttu-id="0d837-326">**cdc_acm**: puntero a la instancia de la clase cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-326">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="0d837-327">**ioctl_function**: función IOCTL que se va a realizar.</span><span class="sxs-lookup"><span data-stu-id="0d837-327">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="0d837-328">Vea la tabla siguiente para ver una de las funciones IOCTL permitidas.</span><span class="sxs-lookup"><span data-stu-id="0d837-328">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="0d837-329">**parameter**: puntero a un parámetro específico de IOCTL.</span><span class="sxs-lookup"><span data-stu-id="0d837-329">**parameter** Pointer to a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="0d837-330">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0d837-330">Return Value</span></span>

- <span data-ttu-id="0d837-331">**UX_SUCCESS** (0X00): ha finalizado la transferencia de datos.</span><span class="sxs-lookup"><span data-stu-id="0d837-331">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="0d837-332">**UX_MEMORY_INSUFFICIENT** (0X12): no tiene suficiente memoria.</span><span class="sxs-lookup"><span data-stu-id="0d837-332">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory.</span></span>
- <span data-ttu-id="0d837-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0X5b): la instancia de CDC_ACM no tiene un estado válido.</span><span class="sxs-lookup"><span data-stu-id="0d837-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) CDC-ACM instance is in an invalid state.</span></span>
- <span data-ttu-id="0d837-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54): función IOCTL desconocida.</span><span class="sxs-lookup"><span data-stu-id="0d837-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="0d837-335">Funciones IOCTL:</span><span class="sxs-lookup"><span data-stu-id="0d837-335">IOCTL functions:</span></span>

- <span data-ttu-id="0d837-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="0d837-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="0d837-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="0d837-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="0d837-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="0d837-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="0d837-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="0d837-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="0d837-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="0d837-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="0d837-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="0d837-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="0d837-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="0d837-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="0d837-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="0d837-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="0d837-344">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="0d837-344">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="0d837-345">Comienza la recepción en segundo plano de los datos del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0d837-345">Begins background reception of data from the device.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-346">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-346">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="0d837-347">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-347">Description</span></span>

<span data-ttu-id="0d837-348">Esta función hace que USBX lea continuamente los datos del dispositivo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0d837-348">This function causes USBX to continuously read data from the device in the background.</span></span> <span data-ttu-id="0d837-349">Tras la finalización de cada transacción, se invoca la devolución de llamada especificada en **cdc_acm_reception** para que la aplicación pueda realizar un procesamiento posterior de los datos de la transacción.</span><span class="sxs-lookup"><span data-stu-id="0d837-349">Upon completion of each transaction, the callback specified in **cdc_acm_reception** is invoked so the application may perform further processing of the transaction's data.</span></span>

> [!NOTE]
> <span data-ttu-id="0d837-350">No se debe usar **ux_host_class_cdc_acm_read** mientras la recepción en segundo plano esté en uso.</span><span class="sxs-lookup"><span data-stu-id="0d837-350">**ux_host_class_cdc_acm_read** must not be used while background reception is in use.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-351">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-351">Parameters</span></span>

- <span data-ttu-id="0d837-352">**cdc_acm**: puntero a la instancia de la clase cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-352">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="0d837-353">**cdc_acm_reception**: puntero al parámetro que contiene valores que definen el comportamiento de la recepción en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0d837-353">**cdc_acm_reception** Pointer to parameter that contains values defining behavior of background reception.</span></span> <span data-ttu-id="0d837-354">El diseño de este parámetro es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="0d837-354">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="0d837-355">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0d837-355">Return Value</span></span>

- <span data-ttu-id="0d837-356">**UX_SUCCESS** (0x00): se ha iniciado correctamente la recepción en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0d837-356">**UX_SUCCESS** (0x00) Background reception successfully started.</span></span>
- <span data-ttu-id="0d837-357">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): instancia de clase no válida.</span><span class="sxs-lookup"><span data-stu-id="0d837-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="0d837-358">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="0d837-358">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="0d837-359">Detiene la recepción en segundo plano de los paquetes.</span><span class="sxs-lookup"><span data-stu-id="0d837-359">Stops background reception of packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="0d837-360">Prototipo</span><span class="sxs-lookup"><span data-stu-id="0d837-360">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="0d837-361">Descripción</span><span class="sxs-lookup"><span data-stu-id="0d837-361">Description</span></span>

<span data-ttu-id="0d837-362">Esta función hace que USBX detenga la recepción en segundo plano iniciada previamente por **ux_host_class_cdc_acm_reception_start**.</span><span class="sxs-lookup"><span data-stu-id="0d837-362">This function causes USBX to stop background reception previously started by **ux_host_class_cdc_acm_reception_start**.</span></span>

### <a name="parameters"></a><span data-ttu-id="0d837-363">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0d837-363">Parameters</span></span>

- <span data-ttu-id="0d837-364">**cdc_acm**: puntero a la instancia de la clase cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="0d837-364">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="0d837-365">**cdc_acm_reception**: puntero al mismo parámetro que se usó para iniciar la recepción en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0d837-365">**cdc_acm_reception** Pointer to the same parameter that was used to start background reception.</span></span> <span data-ttu-id="0d837-366">El diseño de este parámetro es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="0d837-366">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="0d837-367">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0d837-367">Return Value</span></span>

- <span data-ttu-id="0d837-368">**UX_SUCCESS** (0x00): se ha detenido correctamente la recepción en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="0d837-368">**UX_SUCCESS** (0x00) Background reception successfully stopped.</span></span>
- <span data-ttu-id="0d837-369">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b): instancia de clase no válida.</span><span class="sxs-lookup"><span data-stu-id="0d837-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
