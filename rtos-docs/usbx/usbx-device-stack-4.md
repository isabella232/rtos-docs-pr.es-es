---
title: 'Capítulo 4: Descripción de los servicios del dispositivo USBX'
description: Obtenga información sobre los servicios del dispositivo USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816145"
---
# <a name="description-of-usbx-device-services"></a><span data-ttu-id="a98e4-103">Descripción de los servicios del dispositivo USBX</span><span class="sxs-lookup"><span data-stu-id="a98e4-103">Description of USBX Device Services</span></span>

### <a name="ux_device_stack_alternate_setting_get"></a><span data-ttu-id="a98e4-104">ux_device_stack_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="a98e4-104">ux_device_stack_alternate_setting_get</span></span>

<span data-ttu-id="a98e4-105">Obtención del valor alternativo actual de un valor de interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-105">Get current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-106">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-106">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a><span data-ttu-id="a98e4-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-107">Description</span></span>

<span data-ttu-id="a98e4-108">El host USB usa esta función para obtener la configuración alternativa actual de un valor de interfaz específico.</span><span class="sxs-lookup"><span data-stu-id="a98e4-108">This function is used by the USB host to obtain the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="a98e4-109">El driver del controlador lo llama cuando se recibe una solicitud de **GET_INTERFACE**.</span><span class="sxs-lookup"><span data-stu-id="a98e4-109">It is called by the controller driver when a **GET_INTERFACE** request is received.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a98e4-110">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="a98e4-110">Input Parameter</span></span>

- <span data-ttu-id="a98e4-111">**Interface_value**: valor de interfaz para el que se consulta la configuración alternativa actual</span><span class="sxs-lookup"><span data-stu-id="a98e4-111">**Interface_value** Interface value for which the current alternate setting is queried</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-112">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-112">Return Values</span></span>

- <span data-ttu-id="a98e4-113">**UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="a98e4-113">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="a98e4-114">**UX_ERROR** (0xFF): valor de interfaz incorrecto.</span><span class="sxs-lookup"><span data-stu-id="a98e4-114">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-115">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-115">Example</span></span>

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a><span data-ttu-id="a98e4-116">ux_device_stack_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="a98e4-116">ux_device_stack_alternate_setting_set</span></span>

<span data-ttu-id="a98e4-117">Obtención del valor alternativo actual de un valor de interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-117">Set current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-118">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-118">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="a98e4-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-119">Description</span></span>

<span data-ttu-id="a98e4-120">El host USB usa esta función para establecer la configuración alternativa actual de un valor de interfaz específico.</span><span class="sxs-lookup"><span data-stu-id="a98e4-120">This function is used by the USB host to set the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="a98e4-121">El driver del controlador lo llama cuando se recibe una solicitud de **SET_INTERFACE**.</span><span class="sxs-lookup"><span data-stu-id="a98e4-121">It is called by the controller driver when a **SET_INTERFACE** request is received.</span></span> <span data-ttu-id="a98e4-122">Una vez finalizada **SET_INTERFACE**, los valores de la configuración alternativa se aplican a la clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-122">When the **SET_INTERFACE** is completed, the values of the alternate settings are applied to the class.</span></span>

<span data-ttu-id="a98e4-123">La pila de dispositivos emitirá **UX_SLAVE_CLASS_COMMAND_CHANGE** a la clase a la que pertenece esta interfaz para reflejar el cambio de la configuración alternativa.</span><span class="sxs-lookup"><span data-stu-id="a98e4-123">The device stack will issue a **UX_SLAVE_CLASS_COMMAND_CHANGE** to the class that owns this interface to reflect the change of alternate setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="a98e4-124">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a98e4-124">Parameters</span></span>

- <span data-ttu-id="a98e4-125">**interface_value**: valor de interfaz para el que se establece la configuración alternativa actual.</span><span class="sxs-lookup"><span data-stu-id="a98e4-125">**interface_value**: Interface value for which the current alternate setting is set.</span></span>
- <span data-ttu-id="a98e4-126">**alternate_setting_value**: nuevo valor de configuración alternativo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-126">**alternate_setting_value**: The new alternate setting value.</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-127">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-127">Return Values</span></span>

- <span data-ttu-id="a98e4-128">**UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="a98e4-128">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="a98e4-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52): no hay ninguna interfaz asociada.</span><span class="sxs-lookup"><span data-stu-id="a98e4-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) No interface attached.</span></span>
- <span data-ttu-id="a98e4-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54): el dispositivo no está configurado.</span><span class="sxs-lookup"><span data-stu-id="a98e4-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Device is not configured.</span></span>
- <span data-ttu-id="a98e4-131">**UX_ERROR** (0xFF): valor de interfaz incorrecto.</span><span class="sxs-lookup"><span data-stu-id="a98e4-131">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-132">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-132">Example</span></span>

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a><span data-ttu-id="a98e4-133">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="a98e4-133">ux_device_stack_class_register</span></span>

<span data-ttu-id="a98e4-134">Registro de una nueva clase de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="a98e4-134">Register a new USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-135">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-135">Prototype</span></span>

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="a98e4-136">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-136">Description</span></span>

<span data-ttu-id="a98e4-137">La aplicación usa esta función para registrar una nueva clase de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="a98e4-137">This function is used by the application to register a new USB device class.</span></span> <span data-ttu-id="a98e4-138">Este registro inicia un contenedor de clases y no una instancia de la clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-138">This registration starts a class container and not an instance of the class.</span></span> <span data-ttu-id="a98e4-139">La clase debe tener un subproceso activo y asociarse a una interfaz específica.</span><span class="sxs-lookup"><span data-stu-id="a98e4-139">A class should have an active thread and be attached to a specific interface.</span></span>

<span data-ttu-id="a98e4-140">Algunas clases esperan un parámetro o una lista de parámetros.</span><span class="sxs-lookup"><span data-stu-id="a98e4-140">Some classes expect a parameter or parameter list.</span></span> <span data-ttu-id="a98e4-141">Por ejemplo, la clase de almacenamiento de dispositivo esperaría la geometría del dispositivo de almacenamiento que está intentando emular.</span><span class="sxs-lookup"><span data-stu-id="a98e4-141">For instance, the device storage class would expect the geometry of the storage device it is trying to emulate.</span></span> <span data-ttu-id="a98e4-142">Por lo tanto, el campo de parámetro depende del requisito de la clase y puede ser un valor o un puntero que señala a una estructura rellena con los valores de clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-142">The parameter field is therefore dependent on the class requirement and can be a value or a pointer to a structure filled with the class values.</span></span>

> [!NOTE]
> <span data-ttu-id="a98e4-143">La cadena C de class_name debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="a98e4-143">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="a98e4-144">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a98e4-144">Parameters</span></span>

- <span data-ttu-id="a98e4-145">**class_name**: nombre de clase</span><span class="sxs-lookup"><span data-stu-id="a98e4-145">**class_name** Class Name</span></span>
- <span data-ttu-id="a98e4-146">**class_entry_function**: función de entrada de la clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-146">**class_entry_function** The entry function of the class.</span></span>
- <span data-ttu-id="a98e4-147">**configuration_number**: número de configuración al que está asociada esta clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-147">**configuration_number** The configuration number this class is attached to.</span></span>
- <span data-ttu-id="a98e4-148">**interface_number**: número de la interfaz a la que está asociada esta clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-148">**interface_number** The interface number this class is attached to.</span></span>
- <span data-ttu-id="a98e4-149">**parameter**: puntero que señala a una lista de parámetros específica de la clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-149">**parameter** A pointer to a class specific parameter list.</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-150">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-150">Return Values</span></span>

- <span data-ttu-id="a98e4-151">**UX_SUCCESS** (0X00): se ha registrado la clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-151">**UX_SUCCESS** (0x00) The class was registered</span></span>
- <span data-ttu-id="a98e4-152">**UX_MEMORY_INSUFFICIENT** (0x12): no quedan entradas en la tabla de clases.</span><span class="sxs-lookup"><span data-stu-id="a98e4-152">**UX_MEMORY_INSUFFICIENT** (0x12) No entries left in class table.</span></span>
- <span data-ttu-id="a98e4-153">**UX_THREAD_ERROR** (0x16): no se puede crear un subproceso de clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-153">**UX_THREAD_ERROR** (0x16) Cannot create a class thread.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-154">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-154">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a><span data-ttu-id="a98e4-155">ux_device_stack_class_unregister</span><span class="sxs-lookup"><span data-stu-id="a98e4-155">ux_device_stack_class_unregister</span></span>

<span data-ttu-id="a98e4-156">Anulación del registro de una clase de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="a98e4-156">Unregister a USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-157">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-157">Prototype</span></span>

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a><span data-ttu-id="a98e4-158">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-158">Description</span></span>

<span data-ttu-id="a98e4-159">La aplicación usa esta función para anular el registro de una clase de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="a98e4-159">This function is used by the application to unregister a USB device class.</span></span>

> [!NOTE]
> <span data-ttu-id="a98e4-160">La cadena C de class_name debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="a98e4-160">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="a98e4-161">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a98e4-161">Parameters</span></span>

- <span data-ttu-id="a98e4-162">**class_name**: nombre de clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-162">**class_name**: Class Name</span></span>
- <span data-ttu-id="a98e4-163">**class_entry_function**: función de entrada de la clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-163">**class_entry_function**: The entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-164">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-164">Return Values</span></span>

- <span data-ttu-id="a98e4-165">**UX_SUCCESS** (0x00): se ha anulado el registro de la clase.</span><span class="sxs-lookup"><span data-stu-id="a98e4-165">**UX_SUCCESS** (0x00) The class was unregistered.</span></span>
- <span data-ttu-id="a98e4-166">**UX_NO_CLASS_MATCH** (0x57): la clase no está registrada.</span><span class="sxs-lookup"><span data-stu-id="a98e4-166">**UX_NO_CLASS_MATCH** (0x57) The class isn't registered.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-167">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-167">Example</span></span>

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a><span data-ttu-id="a98e4-168">ux_device_stack_configuration_get</span><span class="sxs-lookup"><span data-stu-id="a98e4-168">ux_device_stack_configuration_get</span></span>

<span data-ttu-id="a98e4-169">Obtención de la configuración actual.</span><span class="sxs-lookup"><span data-stu-id="a98e4-169">Get the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-170">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-170">Prototype</span></span>

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a><span data-ttu-id="a98e4-171">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-171">Description</span></span>

<span data-ttu-id="a98e4-172">El host usa esta función para obtener la configuración actual que se ejecuta en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-172">This function is used by the host to obtain the current configuration running in the device.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a98e4-173">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="a98e4-173">Input Parameter</span></span>

<span data-ttu-id="a98e4-174">Ninguno</span><span class="sxs-lookup"><span data-stu-id="a98e4-174">None</span></span>

### <a name="return-value"></a><span data-ttu-id="a98e4-175">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a98e4-175">Return Value</span></span>

- <span data-ttu-id="a98e4-176">**UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="a98e4-176">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-177">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-177">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="a98e4-178">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="a98e4-178">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="a98e4-179">Establecimiento de la configuración actual.</span><span class="sxs-lookup"><span data-stu-id="a98e4-179">Set the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-180">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-180">Prototype</span></span>

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a><span data-ttu-id="a98e4-181">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-181">Description</span></span>

<span data-ttu-id="a98e4-182">El host usa esta función para establecer la configuración actual que se ejecuta en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-182">This function is used by the host to set the current configuration running in the device.</span></span> <span data-ttu-id="a98e4-183">Tras recibir este comando, la pila de dispositivos USB activará la configuración alternativa 0 de cada interfaz conectada a esta configuración.</span><span class="sxs-lookup"><span data-stu-id="a98e4-183">Upon reception of this command, the USB device stack will activate the alternate setting 0 of each interface connected to this configuration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a98e4-184">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="a98e4-184">Input Parameter</span></span>

- <span data-ttu-id="a98e4-185">**configuration_value**: el valor de configuración seleccionado por el host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-185">**configuration_value** The configuration value selected by the host.</span></span>

### <a name="return-value"></a><span data-ttu-id="a98e4-186">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a98e4-186">Return Value</span></span>

- <span data-ttu-id="a98e4-187">**UX_SUCCESS** (0x00): la configuración se ha establecido correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-187">**UX_SUCCESS** (0x00) The configuration was successfully set.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-188">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-188">Example</span></span>

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="a98e4-189">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="a98e4-189">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="a98e4-190">Envío de un descriptor al host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-190">Send a descriptor to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-191">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-191">Prototype</span></span>

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="a98e4-192">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-192">Description</span></span>

<span data-ttu-id="a98e4-193">El lado del dispositivo usa esta función para devolver un descriptor al host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-193">This function is used by the device side to return a descriptor to the host.</span></span> <span data-ttu-id="a98e4-194">Este descriptor puede ser un descriptor de dispositivo, un descriptor de configuración o un descriptor de cadena.</span><span class="sxs-lookup"><span data-stu-id="a98e4-194">This descriptor can be a device descriptor, a configuration descriptor or a string descriptor.</span></span>

### <a name="parameters"></a><span data-ttu-id="a98e4-195">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a98e4-195">Parameters</span></span>

- <span data-ttu-id="a98e4-196">**descriptor_type**: tipo de descriptor.</span><span class="sxs-lookup"><span data-stu-id="a98e4-196">**descriptor_type**: The type of the descriptor.</span></span> <span data-ttu-id="a98e4-197">Debe ser uno de los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="a98e4-197">Must be one of the following values.</span></span>
  - <span data-ttu-id="a98e4-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a98e4-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="a98e4-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a98e4-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="a98e4-200">**UX_STRING_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a98e4-200">**UX_STRING_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="a98e4-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a98e4-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="a98e4-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="a98e4-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span></span>
- <span data-ttu-id="a98e4-203">**request_index**: índice del descriptor.</span><span class="sxs-lookup"><span data-stu-id="a98e4-203">**request_index**: The index of the descriptor.</span></span>
- <span data-ttu-id="a98e4-204">**host_length**: longitud requerida por el host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-204">**host_length**: The length required by the host.</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-205">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-205">Return Values</span></span>

- <span data-ttu-id="a98e4-206">**UX_SUCCESS** (0x00): la transferencia de datos ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="a98e4-206">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="a98e4-207">**UX_ERROR** (0xFF): no se ha completado la transferencia.</span><span class="sxs-lookup"><span data-stu-id="a98e4-207">**UX_ERROR** (0xFF) The transfer was not completed.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-208">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-208">Example</span></span>

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="a98e4-209">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="a98e4-209">ux_device_stack_disconnect</span></span>

<span data-ttu-id="a98e4-210">Desconexión de la pila de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a98e4-210">Disconnect device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-211">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-211">Prototype</span></span>

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a><span data-ttu-id="a98e4-212">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-212">Description</span></span>

<span data-ttu-id="a98e4-213">El administrador de VBUS llama a esta función cuando se produce una desconexión del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-213">The VBUS manager calls this function when there is a device disconnection.</span></span> <span data-ttu-id="a98e4-214">La pila de dispositivos informará a todas las clases registradas en este dispositivo y, a partir de ese momento, liberará todos los recursos del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-214">The device stack will inform all classes registered to this device and will thereafter release all the device resources.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a98e4-215">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="a98e4-215">Input Parameter</span></span>

<span data-ttu-id="a98e4-216">Ninguno</span><span class="sxs-lookup"><span data-stu-id="a98e4-216">None</span></span>

### <a name="return-value"></a><span data-ttu-id="a98e4-217">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a98e4-217">Return Value</span></span>

- <span data-ttu-id="a98e4-218">**UX_SUCCESS** (0x00): se ha desconectado el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-218">**UX_SUCCESS** (0x00) The device was disconnected.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-219">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-219">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="a98e4-220">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="a98e4-220">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="a98e4-221">Solicitud de la condición Stall del punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="a98e4-221">Request endpoint Stall condition</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-222">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-222">Prototype</span></span>

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a><span data-ttu-id="a98e4-223">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-223">Description</span></span>

<span data-ttu-id="a98e4-224">La clase de dispositivo USB llama a esta función cuando un punto de conexión debe devolver una condición Stall al host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-224">This function is called by the USB device class when an endpoint should return a Stall condition to the host.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a98e4-225">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="a98e4-225">Input Parameter</span></span>

- <span data-ttu-id="a98e4-226">**endpoint**: punto de conexión donde se solicita la condición Stall.</span><span class="sxs-lookup"><span data-stu-id="a98e4-226">**endpoint** The endpoint on which the Stall condition is requested.</span></span>

### <a name="return-value"></a><span data-ttu-id="a98e4-227">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a98e4-227">Return Value</span></span>

- <span data-ttu-id="a98e4-228">**UX_SUCCESS** (0x00): la operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-228">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a98e4-229">**UX_ERROR** (0xFF): el dispositivo está en un estado no válido.</span><span class="sxs-lookup"><span data-stu-id="a98e4-229">**UX_ERROR** (0xFF) The device is in an invalid state.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-230">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-230">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="a98e4-231">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="a98e4-231">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="a98e4-232">Reactivación del host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-232">Wake up the host</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-233">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-233">Prototype</span></span>

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a><span data-ttu-id="a98e4-234">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-234">Description</span></span>

<span data-ttu-id="a98e4-235">Se llama a esta función cuando el dispositivo quiere reactivar el host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-235">This function is called when the device wants to wake up the host.</span></span> <span data-ttu-id="a98e4-236">Este comando solo es válido cuando el dispositivo está en modo de suspensión.</span><span class="sxs-lookup"><span data-stu-id="a98e4-236">This command is only valid when the device is in suspend mode.</span></span> <span data-ttu-id="a98e4-237">Depende de la aplicación del dispositivo decidir si quiere reactivar el host USB.</span><span class="sxs-lookup"><span data-stu-id="a98e4-237">It is up to the device application to decide when it wants to wake up the USB host.</span></span> <span data-ttu-id="a98e4-238">Por ejemplo, un módem USB puede reactivar un host cuando detecta una señal de timbre en la línea telefónica.</span><span class="sxs-lookup"><span data-stu-id="a98e4-238">For instance, a USB modem can wake up a host when it detects a RING signal on the telephone line.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a98e4-239">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="a98e4-239">Input Parameter</span></span>

<span data-ttu-id="a98e4-240">Ninguno</span><span class="sxs-lookup"><span data-stu-id="a98e4-240">None</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-241">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-241">Return values</span></span>

- <span data-ttu-id="a98e4-242">**UX_SUCCESS** (0x00): la llamada se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-242">**UX_SUCCESS** (0x00) The call was successful.</span></span>
- <span data-ttu-id="a98e4-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54): error en la llamada (es probable que el dispositivo no estuviera en el modo de suspensión).</span><span class="sxs-lookup"><span data-stu-id="a98e4-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) The call failed (the device was probably not in the suspended mode).</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-244">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-244">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a><span data-ttu-id="a98e4-245">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="a98e4-245">ux_device_stack_initialize</span></span>

<span data-ttu-id="a98e4-246">Inicialización de la pila de dispositivos USB.</span><span class="sxs-lookup"><span data-stu-id="a98e4-246">Initialize USB device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-247">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-247">Prototype</span></span>

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a><span data-ttu-id="a98e4-248">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-248">Description</span></span>

<span data-ttu-id="a98e4-249">La aplicación llama a esta función para inicializar la pila del dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="a98e4-249">This function is called by the application to initialize the USB device stack.</span></span> <span data-ttu-id="a98e4-250">No inicializa ninguna clase ni controlador.</span><span class="sxs-lookup"><span data-stu-id="a98e4-250">It does not initialize any classes or any controllers.</span></span> <span data-ttu-id="a98e4-251">Esto se debe hacer con llamadas de función independientes.</span><span class="sxs-lookup"><span data-stu-id="a98e4-251">This should be done with separate function calls.</span></span> <span data-ttu-id="a98e4-252">Esta llamada proporciona principalmente la pila con el marco de dispositivo para la función USB.</span><span class="sxs-lookup"><span data-stu-id="a98e4-252">This call mainly provides the stack with the device framework for the USB function.</span></span> <span data-ttu-id="a98e4-253">Admite velocidades altas y completas con la posibilidad de tener un marco de dispositivo totalmente independiente para cada velocidad.</span><span class="sxs-lookup"><span data-stu-id="a98e4-253">It supports both high and full speeds with the possibility to have completely separate device framework for each speed.</span></span> <span data-ttu-id="a98e4-254">Se admiten el marco de cadena y varios lenguajes.</span><span class="sxs-lookup"><span data-stu-id="a98e4-254">String framework and multiple languages are supported.</span></span>

### <a name="parameters"></a><span data-ttu-id="a98e4-255">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a98e4-255">Parameters</span></span>

- <span data-ttu-id="a98e4-256">**device_framework_high_speed**: puntero que señala al marco de alta velocidad.</span><span class="sxs-lookup"><span data-stu-id="a98e4-256">**device_framework_high_speed**: Pointer to the high speed framework.</span></span>
- <span data-ttu-id="a98e4-257">**device_framework_length_high_speed**: longitud del marco de alta velocidad.</span><span class="sxs-lookup"><span data-stu-id="a98e4-257">**device_framework_length_high_speed**: Length of the high speed framework.</span></span>
- <span data-ttu-id="a98e4-258">**device_framework_full_speed**: puntero que señala al marco de velocidad máxima.</span><span class="sxs-lookup"><span data-stu-id="a98e4-258">**device_framework_full_speed**: Pointer to the full speed framework.</span></span>
- <span data-ttu-id="a98e4-259">**device_framework_length_full_speed**: longitud del marco de velocidad máxima.</span><span class="sxs-lookup"><span data-stu-id="a98e4-259">**device_framework_length_full_speed**: Length of the full speed framework.</span></span>
- <span data-ttu-id="a98e4-260">**string_framework**: puntero que señala al marco de cadena.</span><span class="sxs-lookup"><span data-stu-id="a98e4-260">**string_framework**: Pointer to string framework.</span></span>
- <span data-ttu-id="a98e4-261">**string_framework_length**: longitud del marco de cadena.</span><span class="sxs-lookup"><span data-stu-id="a98e4-261">**string_framework_length**: Length of string framework.</span></span>
- <span data-ttu-id="a98e4-262">**language_id_framework**: puntero que señala al marco de lenguaje de cadena.</span><span class="sxs-lookup"><span data-stu-id="a98e4-262">**language_id_framework**: Pointer to string language framework.</span></span>
- <span data-ttu-id="a98e4-263">**language_id_framework_length**: longitud del marco de lenguaje de cadena.</span><span class="sxs-lookup"><span data-stu-id="a98e4-263">**language_id_framework_length**: Length of the string language framework.</span></span>
- <span data-ttu-id="a98e4-264">**ux_system_slave_change_function**: función a la que se llamará cuando cambie el estado del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-264">**ux_system_slave_change_function**: Function to be called when the device state changes.</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-265">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-265">Return Values</span></span>

- <span data-ttu-id="a98e4-266">**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-266">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a98e4-267">**UX_MEMORY_INSUFFICIENT** (0x12): no hay suficiente memoria para inicializar la pila.</span><span class="sxs-lookup"><span data-stu-id="a98e4-267">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to initialize the stack.</span></span>
- <span data-ttu-id="a98e4-268">**UX_DESCRIPTOR_CORRUPTED** (0x42): el descriptor no es válido.</span><span class="sxs-lookup"><span data-stu-id="a98e4-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) The descriptor is invalid.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-269">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-269">Example</span></span>

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="a98e4-270">La aplicación puede solicitar una devolución de llamada cuando el controlador cambia su estado.</span><span class="sxs-lookup"><span data-stu-id="a98e4-270">The application can request a call back when the controller changes its state.</span></span> <span data-ttu-id="a98e4-271">Los dos estados principales del controlador son:</span><span class="sxs-lookup"><span data-stu-id="a98e4-271">The two main states for the controller are:</span></span>

- <span data-ttu-id="a98e4-272">**UX_DEVICE_SUSPENDED**</span><span class="sxs-lookup"><span data-stu-id="a98e4-272">**UX_DEVICE_SUSPENDED**</span></span>
- <span data-ttu-id="a98e4-273">**UX_DEVICE_RESUMED**</span><span class="sxs-lookup"><span data-stu-id="a98e4-273">**UX_DEVICE_RESUMED**</span></span>

<span data-ttu-id="a98e4-274">Si la aplicación no necesita señales de suspensión/reanudación, proporciona una función UX_NULL.</span><span class="sxs-lookup"><span data-stu-id="a98e4-274">If the application does not need Suspend/Resume signals, it would supply a UX_NULL function.</span></span>

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="a98e4-275">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="a98e4-275">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="a98e4-276">Eliminación de una interfaz de pila.</span><span class="sxs-lookup"><span data-stu-id="a98e4-276">Delete a stack interface</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-277">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-277">Prototype</span></span>

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="a98e4-278">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-278">Description</span></span>

<span data-ttu-id="a98e4-279">Se llama a esta función cuando se debe quitar una interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-279">This function is called when an interface should be removed.</span></span> <span data-ttu-id="a98e4-280">Una interfaz se quita cuando se extrae un dispositivo o después de un restablecimiento de bus, o cuando hay un nuevo valor alternativo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-280">An interface is either removed when a device is extracted, or following a bus reset, or when there is a new alternate setting.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a98e4-281">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="a98e4-281">Input Parameter</span></span>

- <span data-ttu-id="a98e4-282">**interface**: puntero que señala a la interfaz que se va a quitar.</span><span class="sxs-lookup"><span data-stu-id="a98e4-282">**interface**: Pointer to the interface to remove.</span></span>

### <a name="return-value"></a><span data-ttu-id="a98e4-283">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a98e4-283">Return Value</span></span>

- <span data-ttu-id="a98e4-284">**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-284">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-285">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-285">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="a98e4-286">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="a98e4-286">ux_device_stack_interface_get</span></span>

<span data-ttu-id="a98e4-287">Obtención del valor de la interfaz actual.</span><span class="sxs-lookup"><span data-stu-id="a98e4-287">Get the current interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-288">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-288">Prototype</span></span>

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a><span data-ttu-id="a98e4-289">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-289">Description</span></span>

<span data-ttu-id="a98e4-290">Se llama a esta función cuando el host consulta la interfaz actual.</span><span class="sxs-lookup"><span data-stu-id="a98e4-290">This function is called when the host queries the current interface.</span></span> <span data-ttu-id="a98e4-291">El dispositivo devuelve el valor de la interfaz actual.</span><span class="sxs-lookup"><span data-stu-id="a98e4-291">The device returns the current interface value.</span></span>

> [!NOTE]
> <span data-ttu-id="a98e4-292">Esta función es desusada.</span><span class="sxs-lookup"><span data-stu-id="a98e4-292">This function is deprecated.</span></span> <span data-ttu-id="a98e4-293">Está disponible para software heredado, pero el nuevo software debe usar la función ***ux_device_stack_alternate_setting_get*** en su lugar.</span><span class="sxs-lookup"><span data-stu-id="a98e4-293">It is available for legacy software, but new software should use the ***ux_device_stack_alternate_setting_get*** function instead.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a98e4-294">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="a98e4-294">Input Parameter</span></span>

- <span data-ttu-id="a98e4-295">**interface_value** Valor de interfaz que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="a98e4-295">**interface_value** Interface value to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-296">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-296">Return Values</span></span>

- <span data-ttu-id="a98e4-297">**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-297">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a98e4-298">**UX_ERROR** (0xFF): no existe ninguna interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-298">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-299">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-299">Example</span></span>

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="a98e4-300">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="a98e4-300">ux_device_stack_interface_set</span></span>

<span data-ttu-id="a98e4-301">Cambio de la configuración alternativa de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-301">Change the alternate setting of the interface</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-302">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-302">Prototype</span></span>

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="a98e4-303">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-303">Description</span></span>

<span data-ttu-id="a98e4-304">Se llama a esta función cuando el host solicita un cambio de la configuración alternativa de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-304">This function is called when the host requests a change of the alternate setting for the interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="a98e4-305">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a98e4-305">Parameters</span></span>

- <span data-ttu-id="a98e4-306">**device_framework**: dirección del marco de dispositivo para esta interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-306">**device_framework**: Address of the device framework for this interface.</span></span>
- <span data-ttu-id="a98e4-307">**device_framework_length**: longitud de la plataforma del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-307">**device_framework_length**: Length of the device framework.</span></span>
- <span data-ttu-id="a98e4-308">**alternate_setting_value**: valor de configuración alternativo que va a usar esta interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-308">**alternate_setting_value**: Alternate setting value to be used by this interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-309">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-309">Return Values</span></span>

- <span data-ttu-id="a98e4-310">**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-310">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a98e4-311">**UX_ERROR** (0xFF): no existe ninguna interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-311">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-312">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-312">Example</span></span>

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a><span data-ttu-id="a98e4-313">ux_device_stack_interface_start</span><span class="sxs-lookup"><span data-stu-id="a98e4-313">ux_device_stack_interface_start</span></span>

<span data-ttu-id="a98e4-314">Inicio de la búsqueda de una clase para que sea propietaria de una instancia de interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-314">Start search for a class to own an interface instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-315">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-315">Prototype</span></span>

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="a98e4-316">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-316">Description</span></span>

<span data-ttu-id="a98e4-317">Se llama a esta función cuando el host selecciona una interfaz y la pila de dispositivos necesita buscar una clase de dispositivo para que sea propietaria de esta instancia de la interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-317">This function is called when an interface has been selected by the host and the device stack needs to search for a device class to own this interface instance.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="a98e4-318">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="a98e4-318">Input Parameter</span></span>

- <span data-ttu-id="a98e4-319">**interface**: puntero que señala a la interfaz que se ha creado.</span><span class="sxs-lookup"><span data-stu-id="a98e4-319">**interface**: Pointer to the interface created.</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-320">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-320">Return Values</span></span>

- <span data-ttu-id="a98e4-321">**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-321">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a98e4-322">**UX_NO_CLASS_MATCH** (0x57): no existe ninguna clase para esta interfaz.</span><span class="sxs-lookup"><span data-stu-id="a98e4-322">**UX_NO_CLASS_MATCH** (0x57) No class exists for this interface.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-323">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-323">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="a98e4-324">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="a98e4-324">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="a98e4-325">Solicitud de la transferencia de datos al host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-325">Request to transfer data to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-326">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-326">Prototype</span></span>

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="a98e4-327">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-327">Description</span></span>

<span data-ttu-id="a98e4-328">Se llama a esta función cuando una clase o la pila quiere transferir datos al host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-328">This function is called when a class or the stack wants to transfer data to the host.</span></span> <span data-ttu-id="a98e4-329">El host siempre sondea el dispositivo, pero el dispositivo puede preparar los datos de antemano.</span><span class="sxs-lookup"><span data-stu-id="a98e4-329">The host always polls the device but the device can prepare data in advance.</span></span>

### <a name="parameters"></a><span data-ttu-id="a98e4-330">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a98e4-330">Parameters</span></span>

- <span data-ttu-id="a98e4-331">**transfer_request**: puntero que señala a la solicitud de transferencia.</span><span class="sxs-lookup"><span data-stu-id="a98e4-331">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="a98e4-332">**slave_length**: longitud que el dispositivo quiere devolver.</span><span class="sxs-lookup"><span data-stu-id="a98e4-332">**slave_length**: Length the device wants to return.</span></span>
- <span data-ttu-id="a98e4-333">**host_length**: longitud solicitada por el host.</span><span class="sxs-lookup"><span data-stu-id="a98e4-333">**host_length**: Length the host has requested.</span></span>

### <a name="return-values"></a><span data-ttu-id="a98e4-334">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="a98e4-334">Return Values</span></span>

- <span data-ttu-id="a98e4-335">**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-335">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="a98e4-336">**UX_TRANSFER_NOT_READY** (0x25): el dispositivo está en un estado no válido; debe estar en los estados **ATTACHED** (adjunto), **CONFIGURED** (configurado) o **ADDRESSED** (solucionado).</span><span class="sxs-lookup"><span data-stu-id="a98e4-336">**UX_TRANSFER_NOT_READY** (0x25) The device is in an invalid state; it must be **ATTACHED**, **CONFIGURED**, or **ADDRESSED**.</span></span>
- <span data-ttu-id="a98e4-337">**UX_ERROR** (0xFF): error de transporte.</span><span class="sxs-lookup"><span data-stu-id="a98e4-337">**UX_ERROR** (0xFF) Transport error.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-338">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-338">Example</span></span>

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="a98e4-339">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="a98e4-339">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="a98e4-340">Cancelación de una solicitud de transferencia</span><span class="sxs-lookup"><span data-stu-id="a98e4-340">Cancel a transfer request</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-341">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-341">Prototype</span></span>

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a><span data-ttu-id="a98e4-342">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-342">Description</span></span>

<span data-ttu-id="a98e4-343">Se llama a esta función cuando una aplicación necesita cancelar una solicitud de transferencia o cuando la pila necesita anular una solicitud de transferencia asociada a un punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="a98e4-343">This function is called when an application needs to cancel a transfer request or when the stack needs to abort a transfer request associated with an endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="a98e4-344">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a98e4-344">Parameters</span></span>

- <span data-ttu-id="a98e4-345">**transfer_request**: puntero que señala a la solicitud de transferencia.</span><span class="sxs-lookup"><span data-stu-id="a98e4-345">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="a98e4-346">**completion_code**: código de error que se devolverá a la clase en espera de que se complete la solicitud de transferencia.</span><span class="sxs-lookup"><span data-stu-id="a98e4-346">**completion_code**: Error code to be returned to the class waiting for this transfer request to complete.</span></span>

### <a name="return-value"></a><span data-ttu-id="a98e4-347">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a98e4-347">Return Value</span></span>

- <span data-ttu-id="a98e4-348">**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-348">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="a98e4-349">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="a98e4-349">Example</span></span>

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a><span data-ttu-id="a98e4-350">ux_device_stack_uninitialize</span><span class="sxs-lookup"><span data-stu-id="a98e4-350">ux_device_stack_uninitialize</span></span>

<span data-ttu-id="a98e4-351">Detención de la inicialización de la pila.</span><span class="sxs-lookup"><span data-stu-id="a98e4-351">Unitialize stack</span></span>

### <a name="prototype"></a><span data-ttu-id="a98e4-352">Prototipo</span><span class="sxs-lookup"><span data-stu-id="a98e4-352">Prototype</span></span>

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a><span data-ttu-id="a98e4-353">Descripción</span><span class="sxs-lookup"><span data-stu-id="a98e4-353">Description</span></span>

<span data-ttu-id="a98e4-354">Se llama a esta función cuando una aplicación necesita detener la inicialización de la pila de dispositivos USBX y se liberan todos los recursos de la pila del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a98e4-354">This function is called when an application needs to unitialize the USBX device stack – all device stack resources are freed.</span></span> <span data-ttu-id="a98e4-355">Se debe llamar a este método una vez que se ha anulado el registro de todas las clases mediante ux_device_stack_class_unregister.</span><span class="sxs-lookup"><span data-stu-id="a98e4-355">This should be called after all classes have been unregistered via ux_device_stack_class_unregister.</span></span>

### <a name="parameters"></a><span data-ttu-id="a98e4-356">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a98e4-356">Parameters</span></span>

<span data-ttu-id="a98e4-357">Ninguno</span><span class="sxs-lookup"><span data-stu-id="a98e4-357">None</span></span>

### <a name="return-value"></a><span data-ttu-id="a98e4-358">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="a98e4-358">Return Value</span></span>

<span data-ttu-id="a98e4-359">**UX_SUCCESS** (0x00): la operación se ha realizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="a98e4-359">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
