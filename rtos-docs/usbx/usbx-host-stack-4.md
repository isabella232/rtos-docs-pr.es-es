---
title: 'Capítulo 4: Descripción de los servicios de host de USBX'
description: Obtenga información sobre los servicios de host de USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816357"
---
# <a name="chapter-4---description-of-usbx-host-services"></a><span data-ttu-id="3849c-103">Capítulo 4: Descripción de los servicios de host de USBX</span><span class="sxs-lookup"><span data-stu-id="3849c-103">Chapter 4 - Description of USBX Host Services</span></span>

## <a name="ux_host_stack_initialize"></a><span data-ttu-id="3849c-104">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="3849c-104">ux_host_stack_initialize</span></span>

<span data-ttu-id="3849c-105">Inicializa USBX para la operación del host.</span><span class="sxs-lookup"><span data-stu-id="3849c-105">Initialize USBX for host operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-106">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-106">Prototype</span></span>

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a><span data-ttu-id="3849c-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-107">Description</span></span>

<span data-ttu-id="3849c-108">Esta función inicializará la pila de host USB.</span><span class="sxs-lookup"><span data-stu-id="3849c-108">This function will initialize the USB host stack.</span></span> <span data-ttu-id="3849c-109">El área de memoria suministrada se configurará para su uso interno en USBX.</span><span class="sxs-lookup"><span data-stu-id="3849c-109">The supplied memory area will be setup for USBX internal use.</span></span> <span data-ttu-id="3849c-110">Si se devuelve UX_SUCCESS, USBX está listo para la controladora de host y el registro de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-110">If UX_SUCCESS is returned, USBX is ready for host controller and class registration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3849c-111">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="3849c-111">Input Parameter</span></span>

- <span data-ttu-id="3849c-112">**system_change_function** Puntero a la rutina de devolución de llamada opcional para notificar a la aplicación de los cambios en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3849c-112">**system_change_function** Pointer to optional callback routine for notifying application of device changes.</span></span>

### <a name="return-value"></a><span data-ttu-id="3849c-113">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3849c-113">Return Value</span></span>

- <span data-ttu-id="3849c-114">**UX_SUCCESS** (0x00) Inicialización correcta.</span><span class="sxs-lookup"><span data-stu-id="3849c-114">**UX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="3849c-115">**UX_MEMORY_INSUFFICIENT** (0x12) Error en una asignación de memoria.</span><span class="sxs-lookup"><span data-stu-id="3849c-115">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-116">Example</span></span>

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="3849c-117">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="3849c-117">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="3849c-118">Anula todas las transacciones vinculadas a una solicitud de transferencia para un punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="3849c-118">Abort all transactions attached to a transfer request for an endpoint.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-119">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-119">Prototype</span></span>

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="3849c-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-120">Description</span></span>

<span data-ttu-id="3849c-121">Esta función cancela todas las transacciones activas o pendientes para una solicitud de transferencia específica vinculada a un punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="3849c-121">This function will cancel all transactions active or pending for a specific transfer request attached to an endpoint.</span></span> <span data-ttu-id="3849c-122">La solicitud de transferencia tiene una función de devolución de llamada vinculada, a la que se llamará con el estado UX_TRANSACTION_ABORTED.</span><span class="sxs-lookup"><span data-stu-id="3849c-122">It the transfer request has a callback function attached, the callback function will be called with the UX_TRANSACTION_ABORTED status.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3849c-123">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="3849c-123">Input Parameter</span></span>

- <span data-ttu-id="3849c-124">**endpoint** Puntero a un punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="3849c-124">**endpoint** Pointer to an endpoint.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-125">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-125">Return Values</span></span>

- <span data-ttu-id="3849c-126">**UX_SUCCESS** (0X00) No hay errores.</span><span class="sxs-lookup"><span data-stu-id="3849c-126">**UX_SUCCESS** (0x00) No errors.</span></span>
- <span data-ttu-id="3849c-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) El identificador del punto de conexión no es válido.</span><span class="sxs-lookup"><span data-stu-id="3849c-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint handle is not valid.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-128">Example</span></span>

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a><span data-ttu-id="3849c-129">ux_host_stack_class_get</span><span class="sxs-lookup"><span data-stu-id="3849c-129">ux_host_stack_class_get</span></span>

<span data-ttu-id="3849c-130">Obtiene el puntero a un contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-130">Get the pointer to a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-131">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-131">Prototype</span></span>

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a><span data-ttu-id="3849c-132">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-132">Description</span></span>

<span data-ttu-id="3849c-133">Esta función devuelve un puntero al contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-133">This function returns a pointer to the class container.</span></span> <span data-ttu-id="3849c-134">Una clase debe obtener su contenedor de la pila USB para buscar instancias cuando una clase o una aplicación desea abrir un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3849c-134">A class needs to obtain its container from the USB stack to search for instances when a class or an application wants to open a device.</span></span>

> [!NOTE]
> <span data-ttu-id="3849c-135">La cadena C de class_name debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que UX_MAX_CLASS_NAME_LENGTH.</span><span class="sxs-lookup"><span data-stu-id="3849c-135">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than UX_MAX_CLASS_NAME_LENGTH.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-136">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-136">Parameters</span></span>

- <span data-ttu-id="3849c-137">**class_name** Puntero al nombre de la clase.</span><span class="sxs-lookup"><span data-stu-id="3849c-137">**class_name** Pointer to the class name.</span></span>
- <span data-ttu-id="3849c-138">**class** Un puntero actualizado por la llamada de función que incluye el contenedor de clases para el nombre de la clase.</span><span class="sxs-lookup"><span data-stu-id="3849c-138">**class** A pointer updated by the function call that contains the class container for the name of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-139">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-139">Return Values</span></span>

- <span data-ttu-id="3849c-140">**UX_SUCCESS** (0X00) No hay errores; en la devolución, el campo de clase se registra con el puntero al contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-140">**UX_SUCCESS** (0x00) No errors, on return the class field is filed with the pointer to the class container.</span></span>
- <span data-ttu-id="3849c-141">**UX_HOST_CLASS_UNKNOWN** (0x59) La pila no conoce la clase.</span><span class="sxs-lookup"><span data-stu-id="3849c-141">**UX_HOST_CLASS_UNKNOWN** (0x59) Class is unknown by the stack.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-142">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-142">Example</span></span>

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a><span data-ttu-id="3849c-143">ux_host_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="3849c-143">ux_host_stack_class_register</span></span>

<span data-ttu-id="3849c-144">Registra una clase USB en la pila USB.</span><span class="sxs-lookup"><span data-stu-id="3849c-144">Register a USB class to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-145">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-145">Prototype</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="3849c-146">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-146">Description</span></span>

<span data-ttu-id="3849c-147">Esta función registra una clase USB en la pila USB.</span><span class="sxs-lookup"><span data-stu-id="3849c-147">This function registers a USB class to the USB stack.</span></span> <span data-ttu-id="3849c-148">La clase debe especificar un punto de entrada para que la pila USB envíe comandos como el siguiente.</span><span class="sxs-lookup"><span data-stu-id="3849c-148">The class must specify an entry point for the USB stack to send commands such as the following.</span></span>

- <span data-ttu-id="3849c-149">**UX_HOST_CLASS_COMMAND_QUERY**</span><span class="sxs-lookup"><span data-stu-id="3849c-149">**UX_HOST_CLASS_COMMAND_QUERY**</span></span>
- <span data-ttu-id="3849c-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span><span class="sxs-lookup"><span data-stu-id="3849c-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span></span>
- <span data-ttu-id="3849c-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span><span class="sxs-lookup"><span data-stu-id="3849c-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span></span>

> [!NOTE]
> <span data-ttu-id="3849c-152">La cadena C de *class_name* debe terminar en NULL y la longitud (sin tener en cuenta el terminador NULL) no debe ser mayor que **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="3849c-152">The C string of *class_name* must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-153">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-153">Parameters</span></span>

- <span data-ttu-id="3849c-154">**class_name** Puntero al nombre de la clase; las entradas válidas se encuentran en el archivo ux_system_initialize.c en las clases USB de USBX.</span><span class="sxs-lookup"><span data-stu-id="3849c-154">**class_name** Pointer to the name of the class, valid entries are found in the file ux_system_initialize.c under the USB Classes of USBX.</span></span>
- <span data-ttu-id="3849c-155">**class_entry_address** Dirección de la función de entrada de la clase.</span><span class="sxs-lookup"><span data-stu-id="3849c-155">**class_entry_address** Address of the entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-156">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-156">Return Values</span></span>

- <span data-ttu-id="3849c-157">**UX_SUCCESS** (0x00) La clase se ha instalado correctamente.</span><span class="sxs-lookup"><span data-stu-id="3849c-157">**UX_SUCCESS** (0x00) Class installed successfully.</span></span>
- <span data-ttu-id="3849c-158">**UX_MEMORY_ARRAY_FULL** (0x1a) No hay más memoria para almacenar esta clase.</span><span class="sxs-lookup"><span data-stu-id="3849c-158">**UX_MEMORY_ARRAY_FULL** (0x1a) No more memory to store this class.</span></span>
- <span data-ttu-id="3849c-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) La clase de host ya está instalada.</span><span class="sxs-lookup"><span data-stu-id="3849c-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Host class already installed.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-160">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="3849c-160">Example:</span></span>

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a><span data-ttu-id="3849c-161">ux_host_stack_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="3849c-161">ux_host_stack_class_instance_create</span></span>

<span data-ttu-id="3849c-162">Crea una instancia de clase para un contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-162">Create a new class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-163">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-163">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="3849c-164">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-164">Description</span></span>

<span data-ttu-id="3849c-165">Esta función crea una instancia de clase para un contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-165">This function creates a new class instance for a class container.</span></span> <span data-ttu-id="3849c-166">La instancia de una clase no se incluye en el código de clase para reducir la complejidad de la clase.</span><span class="sxs-lookup"><span data-stu-id="3849c-166">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="3849c-167">En su lugar, cada instancia de clase se vincula al contenedor de clases ubicado en la pila principal.</span><span class="sxs-lookup"><span data-stu-id="3849c-167">Rather, each class instance is attached to the class container located in the main stack.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-168">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-168">Parameters</span></span>

- <span data-ttu-id="3849c-169">**class** Puntero al contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-169">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="3849c-170">**class_instance** Puntero a la instancia de clase que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="3849c-170">**class_instance** Pointer to the class instance to be created.</span></span>

### <a name="return-value"></a><span data-ttu-id="3849c-171">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="3849c-171">Return Value</span></span>

- <span data-ttu-id="3849c-172">**UX_SUCCESS** (0X00) La instancia de clase se ha vinculado al contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-172">**UX_SUCCESS** (0x00) The class instance was attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-173">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-173">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a><span data-ttu-id="3849c-174">ux_host_stack_class_instance_destroy</span><span class="sxs-lookup"><span data-stu-id="3849c-174">ux_host_stack_class_instance_destroy</span></span>

<span data-ttu-id="3849c-175">Destruye una instancia de clase para un contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-175">Destroy a class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-176">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-176">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="3849c-177">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-177">Description</span></span>

<span data-ttu-id="3849c-178">Esta función destruye una instancia de clase para un contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-178">This function destroys a class instance for a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-179">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-179">Parameters</span></span>

- <span data-ttu-id="3849c-180">**class** Puntero al contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-180">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="3849c-181">**class_instance** Puntero a la instancia que se va a destruir.</span><span class="sxs-lookup"><span data-stu-id="3849c-181">**class_instance** Pointer to the instance to destroy.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-182">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-182">Return Values</span></span>

- <span data-ttu-id="3849c-183">**UX_SUCCESS** (0x00) Se destruyó la instancia de clase.</span><span class="sxs-lookup"><span data-stu-id="3849c-183">**UX_SUCCESS** (0x00) The class instance was destroyed.</span></span>
- <span data-ttu-id="3849c-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) La instancia de clase no está vinculada al contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The class instance is not attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-185">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-185">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a><span data-ttu-id="3849c-186">ux_host_stack_class_instance_get</span><span class="sxs-lookup"><span data-stu-id="3849c-186">ux_host_stack_class_instance_get</span></span>

<span data-ttu-id="3849c-187">Obtiene un puntero de instancia de clase para una clase específica.</span><span class="sxs-lookup"><span data-stu-id="3849c-187">Get a class instance pointer for a specific class.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-188">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-188">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a><span data-ttu-id="3849c-189">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-189">Description</span></span>

<span data-ttu-id="3849c-190">Esta función devuelve un puntero de instancia de clase para una clase específica.</span><span class="sxs-lookup"><span data-stu-id="3849c-190">This function returns a class instance pointer for a specific class.</span></span> <span data-ttu-id="3849c-191">La instancia de una clase no se incluye en el código de clase para reducir la complejidad de la clase.</span><span class="sxs-lookup"><span data-stu-id="3849c-191">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="3849c-192">En su lugar, cada instancia de clase se vincula al contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-192">Rather, each class instance is attached to the class container.</span></span> <span data-ttu-id="3849c-193">Esta función se usa para buscar instancias de clase dentro de un contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-193">This function is used to search for class instances within a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-194">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-194">Parameters</span></span>

- <span data-ttu-id="3849c-195">**class** Puntero al contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-195">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="3849c-196">**class_index** Índice que la llamada de función usará en la lista de clases vinculadas al contenedor.</span><span class="sxs-lookup"><span data-stu-id="3849c-196">**class_index** An index to be used by the function call within the list of attached classes to the container.</span></span>
- <span data-ttu-id="3849c-197">**class_instance** Puntero a la instancia que la llamada de función devolverá.</span><span class="sxs-lookup"><span data-stu-id="3849c-197">**class_instance** Pointer to the instance to be returned by the function call.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-198">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-198">Return Values</span></span>

- <span data-ttu-id="3849c-199">**UX_SUCCESS** (0x00) Se encontró la instancia de clase.</span><span class="sxs-lookup"><span data-stu-id="3849c-199">**UX_SUCCESS** (0x00) The class instance was found.</span></span>

- <span data-ttu-id="3849c-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) No hay más instancias de clase vinculadas a este contenedor de clases.</span><span class="sxs-lookup"><span data-stu-id="3849c-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) There are no more class instances attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-201">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-201">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="3849c-202">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="3849c-202">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="3849c-203">Obtiene un puntero a un contenedor de configuración.</span><span class="sxs-lookup"><span data-stu-id="3849c-203">Get a pointer to a configuration container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-204">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-204">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="3849c-205">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-205">Description</span></span>

<span data-ttu-id="3849c-206">Esta función devuelve un contenedor de configuración basado en un identificador de dispositivo y en un índice de configuración.</span><span class="sxs-lookup"><span data-stu-id="3849c-206">This function returns a configuration container based on a device handle and a configuration index.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-207">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-207">Parameters</span></span>

- <span data-ttu-id="3849c-208">**device** Puntero al contenedor de dispositivos que posee la configuración solicitada.</span><span class="sxs-lookup"><span data-stu-id="3849c-208">**device** Pointer to the device container that owns the configuration requested.</span></span>
- <span data-ttu-id="3849c-209">**configuration_index** Índice de la configuración que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="3849c-209">**configuration_index** Index of the configuration to be searched.</span></span>
- <span data-ttu-id="3849c-210">**configuration** Dirección del puntero al contenedor de configuración que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="3849c-210">**configuration** Address of the pointer to the configuration container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-211">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-211">Return Values</span></span>

- <span data-ttu-id="3849c-212">**UX_SUCCESS** (0x00) Se encontró la configuración.</span><span class="sxs-lookup"><span data-stu-id="3849c-212">**UX_SUCCESS** (0x00) The configuration was found.</span></span>
- <span data-ttu-id="3849c-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) El contenedor de dispositivos no existe.</span><span class="sxs-lookup"><span data-stu-id="3849c-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) The device container does not exist.</span></span>
- <span data-ttu-id="3849c-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0X51) El identificador de configuración para el índice no existe.</span><span class="sxs-lookup"><span data-stu-id="3849c-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle for the index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-215">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-215">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="3849c-216">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="3849c-216">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="3849c-217">Selecciona una configuración específica para un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3849c-217">Select a specific configuration for a device.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-218">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-218">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="3849c-219">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-219">Description</span></span>

<span data-ttu-id="3849c-220">Esta función selecciona una configuración específica para un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3849c-220">This function selects a specific configuration for a device.</span></span> <span data-ttu-id="3849c-221">Cuando esta configuración se establece en el dispositivo, de forma predeterminada, cada interfaz del dispositivo y su valor alternativo asociado 0 se activan en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3849c-221">When this configuration is set to the device, by default, each device interface and its associated alternate setting 0 is activated on the device.</span></span> <span data-ttu-id="3849c-222">Si la clase device o interface desea cambiar la configuración de una interfaz determinada, debe emitir una llamada de servicio **ux_host_stack_interface_setting_select**.</span><span class="sxs-lookup"><span data-stu-id="3849c-222">If the device/interface class wishes to change the setting of a particular interface, it needs to issue a **ux_host_stack_interface_setting_select** service call.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-223">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-223">Parameters</span></span>

- <span data-ttu-id="3849c-224">**configuration** Puntero al contenedor de configuración que se va a habilitar para este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3849c-224">**configuration** Pointer to the configuration container that is to be enabled for this device.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-225">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-225">Return Values</span></span>

- <span data-ttu-id="3849c-226">**UX_SUCCESS** (0x00) La configuración se ha seleccionado correctamente.</span><span class="sxs-lookup"><span data-stu-id="3849c-226">**UX_SUCCESS** (0x00) The configuration selection was successful.</span></span>
- <span data-ttu-id="3849c-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) El identificador de configuración no existe.</span><span class="sxs-lookup"><span data-stu-id="3849c-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle does not exist.</span></span>
- <span data-ttu-id="3849c-228">**UX_OVER_CURRENT_CONDITION** (0X43) Existe una condición de exceso de corriente en el bus para esta configuración.</span><span class="sxs-lookup"><span data-stu-id="3849c-228">**UX_OVER_CURRENT_CONDITION** (0x43) An over current condition exists on the bus for this configuration.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-229">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-229">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a><span data-ttu-id="3849c-230">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="3849c-230">ux_host_stack_device_get</span></span>

<span data-ttu-id="3849c-231">Obtiene un puntero a un contenedor de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3849c-231">Get a pointer to a device container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-232">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-232">Prototype</span></span>

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a><span data-ttu-id="3849c-233">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-233">Description</span></span>

<span data-ttu-id="3849c-234">Esta función devuelve un contenedor de dispositivos basado en su índice.</span><span class="sxs-lookup"><span data-stu-id="3849c-234">This function returns a device container based on its index.</span></span> <span data-ttu-id="3849c-235">El índice del dispositivo empieza por 0.</span><span class="sxs-lookup"><span data-stu-id="3849c-235">The device index starts with 0.</span></span> <span data-ttu-id="3849c-236">Tenga en cuenta que el índice es un tipo ULONG porque podríamos tener varios controladores, y un índice de bytes podría no ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="3849c-236">Note that the index is a ULONG because we could have several controllers and a byte index might not be enough.</span></span> <span data-ttu-id="3849c-237">El índice del dispositivo no se debe confundir con la dirección del dispositivo, ya que esta es específica del bus.</span><span class="sxs-lookup"><span data-stu-id="3849c-237">The device index should not be confused with the device address that is bus specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-238">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-238">Parameters</span></span>

- <span data-ttu-id="3849c-239">**device_index** Índice del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3849c-239">**device_index** Index of the device.</span></span>
- <span data-ttu-id="3849c-240">**device** Dirección del puntero para el contenedor de dispositivos que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="3849c-240">**device** Address of the pointer for the device container to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-241">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-241">Return Values</span></span>

- <span data-ttu-id="3849c-242">**UX_SUCCESS** (0X00) El contenedor de dispositivos existe y se devuelve.</span><span class="sxs-lookup"><span data-stu-id="3849c-242">**UX_SUCCESS** (0x00) The device container exists and is returned</span></span>
- <span data-ttu-id="3849c-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) Dispositivo desconocido.</span><span class="sxs-lookup"><span data-stu-id="3849c-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) Device unknown</span></span>

### <a name="example"></a><span data-ttu-id="3849c-244">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-244">Example</span></span>

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a><span data-ttu-id="3849c-245">ux_host_stack_interface_endpoint_get</span><span class="sxs-lookup"><span data-stu-id="3849c-245">ux_host_stack_interface_endpoint_get</span></span>

<span data-ttu-id="3849c-246">Obtiene un contenedor de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="3849c-246">Get an endpoint container.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-247">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-247">Prototype</span></span>

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="3849c-248">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-248">Description</span></span>

<span data-ttu-id="3849c-249">Esta función devuelve un contenedor de puntos de conexión basado en el identificador de la interfaz y un índice de punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="3849c-249">This function returns an endpoint container based on the interface handle and an endpoint index.</span></span> <span data-ttu-id="3849c-250">Se supone que se ha seleccionado la configuración alternativa de la interfaz o que se usa la configuración predeterminada antes de los puntos de conexión buscados.</span><span class="sxs-lookup"><span data-stu-id="3849c-250">It is assumed that the alternate setting for the interface has been selected or the default setting is being used prior to the endpoint(s) being searched.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-251">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-251">Parameters</span></span>

- <span data-ttu-id="3849c-252">**interface** Puntero al contenedor de la interfaz que contiene el punto de conexión solicitado.</span><span class="sxs-lookup"><span data-stu-id="3849c-252">**interface** Pointer to the interface container that contains the endpoint requested.</span></span>
- <span data-ttu-id="3849c-253">**endpoint_index** Índice del punto de conexión de esta interfaz.</span><span class="sxs-lookup"><span data-stu-id="3849c-253">**endpoint_index** Index of the endpoint in this interface.</span></span>
- <span data-ttu-id="3849c-254">**endpoint** Dirección del contenedor de puntos de conexión que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="3849c-254">**endpoint** Address of the endpoint container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-255">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-255">Return Values</span></span>

- <span data-ttu-id="3849c-256">**UX_SUCCESS** (0X00) El contenedor de puntos de conexión existe y se devuelve.</span><span class="sxs-lookup"><span data-stu-id="3849c-256">**UX_SUCCESS** (0x00) The endpoint container exists and is returned.</span></span>
- <span data-ttu-id="3849c-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) La interfaz especificada no existe.</span><span class="sxs-lookup"><span data-stu-id="3849c-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Interface specified does not exist.</span></span>
- <span data-ttu-id="3849c-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) El índice de punto de conexión no existe.</span><span class="sxs-lookup"><span data-stu-id="3849c-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-259">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-259">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="3849c-260">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="3849c-260">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="3849c-261">Registra una controladora USB en la pila USB.</span><span class="sxs-lookup"><span data-stu-id="3849c-261">Register a USB controller to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-262">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-262">Prototype</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a><span data-ttu-id="3849c-263">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-263">Description</span></span>

<span data-ttu-id="3849c-264">Esta función registra una controladora USB en la pila USB.</span><span class="sxs-lookup"><span data-stu-id="3849c-264">This function registers a USB controller to the USB stack.</span></span> <span data-ttu-id="3849c-265">Principalmente asigna la memoria usada por este controlador y pasa el comando de inicialización al controlador.</span><span class="sxs-lookup"><span data-stu-id="3849c-265">It mainly allocates the memory used by this controller and passes the initialization command to the controller.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-266">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-266">Parameters</span></span>

- <span data-ttu-id="3849c-267">**hcd_name** Nombre de la controladora de host.</span><span class="sxs-lookup"><span data-stu-id="3849c-267">**hcd_name** Name of the host controller</span></span>
- <span data-ttu-id="3849c-268">**hcd_function** Función de la controladora de host responsable de la inicialización.</span><span class="sxs-lookup"><span data-stu-id="3849c-268">**hcd_function** The function in the host controller responsible for the initialization.</span></span>
- <span data-ttu-id="3849c-269">**hcd_param1** El recurso de E/S o de memoria utilizado por HCD.</span><span class="sxs-lookup"><span data-stu-id="3849c-269">**hcd_param1** The IO or memory resource used by the hcd.</span></span>
- <span data-ttu-id="3849c-270">**hcd_param2** La IRQ utilizada por la controladora de host.</span><span class="sxs-lookup"><span data-stu-id="3849c-270">**hcd_param2** The IRQ used by the host controller.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-271">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-271">Return Values</span></span>

- <span data-ttu-id="3849c-272">**UX_SUCCESS** (0x00) La controladora se inicializó correctamente.</span><span class="sxs-lookup"><span data-stu-id="3849c-272">**UX_SUCCESS** (0x00) The controller was initialized properly.</span></span>
- <span data-ttu-id="3849c-273">**UX_MEMORY_INSUFFICIENT** (0X12) No hay suficiente memoria para esta controladora.</span><span class="sxs-lookup"><span data-stu-id="3849c-273">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory for this controller.</span></span>
- <span data-ttu-id="3849c-274">**UX_PORT_RESET_FAILED** (0x31) No se pudo restablecer la controladora.</span><span class="sxs-lookup"><span data-stu-id="3849c-274">**UX_PORT_RESET_FAILED** (0x31) The reset of the controller failed.</span></span>
- <span data-ttu-id="3849c-275">**UX_CONTROLLER_INIT_FAILED** (0x32) La controladora no se pudo inicializar correctamente.</span><span class="sxs-lookup"><span data-stu-id="3849c-275">**UX_CONTROLLER_INIT_FAILED** (0x32) The controller failed to initialize properly.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-276">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-276">Example</span></span>

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a><span data-ttu-id="3849c-277">ux_host_stack_configuration_interface_get</span><span class="sxs-lookup"><span data-stu-id="3849c-277">ux_host_stack_configuration_interface_get</span></span>

<span data-ttu-id="3849c-278">Obtiene un puntero de contenedor de interfaz.</span><span class="sxs-lookup"><span data-stu-id="3849c-278">Get an interface container pointer.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-279">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-279">Prototype</span></span>

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a><span data-ttu-id="3849c-280">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-280">Description</span></span>

<span data-ttu-id="3849c-281">Esta función devuelve un contenedor de interfaz basado en un identificador de configuración, un índice de interfaz y un índice de configuración alternativo.</span><span class="sxs-lookup"><span data-stu-id="3849c-281">This function returns an interface container based on a configuration handle, an interface index, and an alternate setting index.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-282">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-282">Parameters</span></span>

- <span data-ttu-id="3849c-283">**configuration** Puntero al contenedor de configuración que posee la interfaz.</span><span class="sxs-lookup"><span data-stu-id="3849c-283">**configuration** Pointer to the configuration container that owns the interface.</span></span>
- <span data-ttu-id="3849c-284">**interface_index** Índice de interfaz que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="3849c-284">**interface_index** Interface index to be searched.</span></span>
- <span data-ttu-id="3849c-285">**alternate_setting_index** Configuración alternativa dentro de la interfaz que se va a buscar.</span><span class="sxs-lookup"><span data-stu-id="3849c-285">**alternate_setting_index** Alternate setting within the interface to search.</span></span>
- <span data-ttu-id="3849c-286">**interface** Dirección del puntero de contenedor de la interfaz que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="3849c-286">**interface** Address of the interface container pointer to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-287">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-287">Return Values</span></span>

- <span data-ttu-id="3849c-288">**UX_SUCCESS** (0X00) El contenedor de interfaz para el índice de interfaz y la configuración alternativa se encontraron y devolvieron.</span><span class="sxs-lookup"><span data-stu-id="3849c-288">**UX_SUCCESS** (0x00) The interface container for the interface index and the alternate setting was found and returned.</span></span>
- <span data-ttu-id="3849c-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) La configuración no existe.</span><span class="sxs-lookup"><span data-stu-id="3849c-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration does not exist.</span></span>
- <span data-ttu-id="3849c-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) La interfaz no existe.</span><span class="sxs-lookup"><span data-stu-id="3849c-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-291">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-291">Example</span></span>

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="3849c-292">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="3849c-292">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="3849c-293">Selecciona una configuración alternativa para una interfaz.</span><span class="sxs-lookup"><span data-stu-id="3849c-293">Select an alternate setting for an interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-294">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-294">Prototype</span></span>

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a><span data-ttu-id="3849c-295">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-295">Description</span></span>

<span data-ttu-id="3849c-296">Esta función selecciona una configuración alternativa específica para una interfaz determinada que pertenece a la configuración seleccionada.</span><span class="sxs-lookup"><span data-stu-id="3849c-296">This function selects a specific alternate setting for a given interface belonging to the selected configuration.</span></span> <span data-ttu-id="3849c-297">Esta función se usa para cambiar de la configuración alternativa predeterminada a una nueva configuración o para volver a la configuración alternativa predeterminada.</span><span class="sxs-lookup"><span data-stu-id="3849c-297">This function is used to change from the default alternate setting to a new setting or to go back to the default alternate setting.</span></span> <span data-ttu-id="3849c-298">Cuando se selecciona una nueva configuración alternativa, las características del punto de conexión anterior no son válidas y se deben volver a cargar.</span><span class="sxs-lookup"><span data-stu-id="3849c-298">When a new alternate setting is selected, the previous endpoint characteristics are invalid and should be reloaded.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3849c-299">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="3849c-299">Input Parameter</span></span>

- <span data-ttu-id="3849c-300">**interface** Puntero al contenedor de interfaz cuya configuración alternativa se va a seleccionar.</span><span class="sxs-lookup"><span data-stu-id="3849c-300">**interface** Pointer to the interface container whose alternate setting is to be selected.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-301">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-301">Return Values</span></span>

- <span data-ttu-id="3849c-302">**UX_SUCCESS** (0X00) La configuración alternativa de esta interfaz se ha seleccionado correctamente.</span><span class="sxs-lookup"><span data-stu-id="3849c-302">**UX_SUCCESS** (0x00) The alternate setting for this interface has been successfully selected.</span></span>
- <span data-ttu-id="3849c-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) La interfaz no existe.</span><span class="sxs-lookup"><span data-stu-id="3849c-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-304">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-304">Example</span></span>

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a><span data-ttu-id="3849c-305">ux_host_stack_transfer_request_abort</span><span class="sxs-lookup"><span data-stu-id="3849c-305">ux_host_stack_transfer_request_abort</span></span>

<span data-ttu-id="3849c-306">Anula una solicitud de transferencia pendiente.</span><span class="sxs-lookup"><span data-stu-id="3849c-306">Abort a pending transfer request.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-307">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-307">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="3849c-308">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-308">Description</span></span>

<span data-ttu-id="3849c-309">Esta función anula una solicitud de transferencia pendiente que se ha enviado previamente.</span><span class="sxs-lookup"><span data-stu-id="3849c-309">This function aborts a pending transfer request that has been previously submitted.</span></span> <span data-ttu-id="3849c-310">Esta función solo cancela una solicitud de transferencia concreta.</span><span class="sxs-lookup"><span data-stu-id="3849c-310">This function only cancels a specific transfer request.</span></span> <span data-ttu-id="3849c-311">La devolución de llamada a la función tendrá el estado UX_TRANSFER REQUEST_STATUS_ABORT.</span><span class="sxs-lookup"><span data-stu-id="3849c-311">The call back to the function will have the UX_TRANSFER REQUEST_STATUS_ABORT status.</span></span>

### <a name="parameters"></a><span data-ttu-id="3849c-312">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3849c-312">Parameters</span></span>

- <span data-ttu-id="3849c-313">**transfer request** Puntero a la solicitud de transferencia que se va a anular.</span><span class="sxs-lookup"><span data-stu-id="3849c-313">**transfer request** Pointer to the transfer request to be aborted.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-314">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-314">Return Values</span></span>

- <span data-ttu-id="3849c-315">**UX_SUCCESS** (0x00) Se canceló la transferencia USB para esta solicitud de transferencia.</span><span class="sxs-lookup"><span data-stu-id="3849c-315">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was canceled.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-316">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3849c-316">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="3849c-317">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="3849c-317">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="3849c-318">Solicita una transferencia USB.</span><span class="sxs-lookup"><span data-stu-id="3849c-318">Request a USB transfer.</span></span>

### <a name="prototype"></a><span data-ttu-id="3849c-319">Prototipo</span><span class="sxs-lookup"><span data-stu-id="3849c-319">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="3849c-320">Descripción</span><span class="sxs-lookup"><span data-stu-id="3849c-320">Description</span></span>

<span data-ttu-id="3849c-321">Esta función realiza una transacción USB.</span><span class="sxs-lookup"><span data-stu-id="3849c-321">This function performs a USB transaction.</span></span> <span data-ttu-id="3849c-322">En la entrada, la solicitud de transferencia proporciona la canalización del punto de conexión seleccionada para esta transacción y los parámetros asociados a la transferencia (carga de datos y longitud de la transacción).</span><span class="sxs-lookup"><span data-stu-id="3849c-322">On entry the transfer request gives the endpoint pipe selected for this transaction and the parameters associated with the transfer (data payload, length of transaction).</span></span> <span data-ttu-id="3849c-323">En el caso de la canalización de control, la transacción se bloquea y solo se devolverá cuando se hayan completado las tres fases de la transferencia de control o si se ha producido un error anterior.</span><span class="sxs-lookup"><span data-stu-id="3849c-323">For Control pipe, the transaction is blocking and will only return when the three phases of the control transfer have been completed or if there is a previous error.</span></span> <span data-ttu-id="3849c-324">En el caso de otras canalizaciones, la pila USB programará la transacción en la unidad USB, pero no esperará a que se complete.</span><span class="sxs-lookup"><span data-stu-id="3849c-324">For other pipes, the USB stack will schedule the transaction on the USB but will not wait for its completion.</span></span> <span data-ttu-id="3849c-325">Cada solicitud de transferencia para canalizaciones sin bloqueo tiene que especificar un controlador de rutina de finalización.</span><span class="sxs-lookup"><span data-stu-id="3849c-325">Each transfer request for non-blocking pipes has to specify a completion routine handler.</span></span>

<span data-ttu-id="3849c-326">Cuando se devuelve la llamada de función, se debe examinar el estado de la solicitud de transferencia, ya que contiene el resultado de la transacción.</span><span class="sxs-lookup"><span data-stu-id="3849c-326">When the function call returns, the status of the transfer request should be examined as it contains the result of the transaction.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="3849c-327">Parámetro de entrada</span><span class="sxs-lookup"><span data-stu-id="3849c-327">Input Parameter</span></span>

- <span data-ttu-id="3849c-328">**transfer_request** Puntero a la solicitud de transferencia.</span><span class="sxs-lookup"><span data-stu-id="3849c-328">**transfer_request** Pointer to the transfer request.</span></span> <span data-ttu-id="3849c-329">La solicitud de transferencia contiene toda la información necesaria para la transferencia.</span><span class="sxs-lookup"><span data-stu-id="3849c-329">The transfer request contains all the necessary information required for the transfer.</span></span>

### <a name="return-values"></a><span data-ttu-id="3849c-330">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="3849c-330">Return Values</span></span>

- <span data-ttu-id="3849c-331">**UX_SUCCESS** (0x00) Se canceló la transferencia USB para esta solicitud de transferencia.</span><span class="sxs-lookup"><span data-stu-id="3849c-331">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was scheduled properly.</span></span> <span data-ttu-id="3849c-332">El código de estado de la solicitud de transferencia debe examinarse cuando se complete la solicitud de transferencia.</span><span class="sxs-lookup"><span data-stu-id="3849c-332">The status code of the transfer request should be examined when the transfer request completes.</span></span>
- <span data-ttu-id="3849c-333">**UX_MEMORY_INSUFFICIENT** (0X12) No hay suficiente memoria para asignar los recursos de controlador necesarios.</span><span class="sxs-lookup"><span data-stu-id="3849c-333">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to allocate the necessary controller resources.</span></span>
- <span data-ttu-id="3849c-334">**UX_TRANSFER_NOT_READY** (0x25) El dispositivo estaba en un estado no válido; debe estar en los estados ATTACHED, ADDRESSED o CONFIGURED.</span><span class="sxs-lookup"><span data-stu-id="3849c-334">**UX_TRANSFER_NOT_READY** (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>

### <a name="example"></a><span data-ttu-id="3849c-335">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="3849c-335">Example:</span></span>

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
