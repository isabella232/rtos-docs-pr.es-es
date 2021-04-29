---
title: 'Capítulo 5: Consideraciones acerca de la clase del dispositivo USBX'
description: Obtenga información sobre las consideraciones de la clase de dispositivo USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 84f215ad990a2fe185a08f3876276528787ef8bc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815081"
---
# <a name="chapter-5---usbx-device-class-considerations"></a><span data-ttu-id="edb5c-103">Capítulo 5: Consideraciones acerca de la clase del dispositivo USBX</span><span class="sxs-lookup"><span data-stu-id="edb5c-103">Chapter 5 - USBX Device Class Considerations</span></span>

## <a name="device-class-registration"></a><span data-ttu-id="edb5c-104">Registro de clase de dispositivo</span><span class="sxs-lookup"><span data-stu-id="edb5c-104">Device Class registration</span></span>

<span data-ttu-id="edb5c-105">Todas las clases de dispositivos siguen el mismo principio para el registro.</span><span class="sxs-lookup"><span data-stu-id="edb5c-105">Each device class follows the same principle for registration.</span></span> <span data-ttu-id="edb5c-106">Se pasa una estructura que contiene los parámetros específicos de clase a la función de inicialización de clase.</span><span class="sxs-lookup"><span data-stu-id="edb5c-106">A structure containing specific class parameters is passed to the class initialize function.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

<span data-ttu-id="edb5c-107">Cada clase puede registrar, opcionalmente, una función de devolución de llamada cuando se activa una instancia de la clase.</span><span class="sxs-lookup"><span data-stu-id="edb5c-107">Each class can register, optionally, a callback function when a instance of the class gets activated.</span></span> <span data-ttu-id="edb5c-108">La pila del dispositivo llama a la devolución de llamada para informar a la aplicación de que se ha creado una instancia.</span><span class="sxs-lookup"><span data-stu-id="edb5c-108">The callback is then called by the device stack to inform the application that an instance was created.</span></span>

<span data-ttu-id="edb5c-109">La aplicación tendrá en su cuerpo las dos funciones correspondientes a la activación y desactivación, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-109">The application would have in its body the 2 functions for activation and deactivation, as shown in the following example.</span></span>

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

<span data-ttu-id="edb5c-110">No se recomienda hacer nada en estas funciones, tan solo memorizar la instancia de la clase y sincronizar con el resto de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="edb5c-110">It is not recommended to do anything within these functions but to memorize the instance of the class and synchronize with the rest of the application.</span></span>

## <a name="usb-device-storage-class"></a><span data-ttu-id="edb5c-111">Clase de almacenamiento de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="edb5c-111">USB Device Storage Class</span></span>

<span data-ttu-id="edb5c-112">La clase de almacenamiento de dispositivo USB permite que un dispositivo de almacenamiento insertado en el sistema sea visible para un host USB.</span><span class="sxs-lookup"><span data-stu-id="edb5c-112">The USB device storage class allows for a storage device embedded in the system to be made visible to a USB host.</span></span>

<span data-ttu-id="edb5c-113">La clase de almacenamiento de dispositivo USB no proporciona por sí misma una solución de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="edb5c-113">The USB device storage class does not by itself provide a storage solution.</span></span> <span data-ttu-id="edb5c-114">Simplemente acepta e interpreta las solicitudes SCSI procedentes del host.</span><span class="sxs-lookup"><span data-stu-id="edb5c-114">It merely accepts and interprets SCSI requests coming from the host.</span></span> <span data-ttu-id="edb5c-115">Cuando una de estas solicitudes es un comando de lectura o escritura, invocará una devolución de llamada predefinida a un controlador de dispositivo de almacenamiento real, como un controlador de dispositivo ATA o un controlador de dispositivo Flash.</span><span class="sxs-lookup"><span data-stu-id="edb5c-115">When one of these requests is a read or a write command, it will invoke a pre-defined call back to a real storage device handler, such as an ATA device driver or a Flash device driver.</span></span>

<span data-ttu-id="edb5c-116">Al inicializar la clase de almacenamiento de dispositivo, se asigna una estructura de puntero a la clase que contiene toda la información necesaria.</span><span class="sxs-lookup"><span data-stu-id="edb5c-116">When initializing the device storage class, a pointer structure is given to the class that contains all the information necessary.</span></span> <span data-ttu-id="edb5c-117">A continuación encontrará un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-117">An example is given below.</span></span>

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

<span data-ttu-id="edb5c-118">En este ejemplo, las cadenas de almacenamiento del controlador se personalizan asignando punteros de cadena al parámetro correspondiente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-118">In this example, the driver storage strings are customized by assigning string pointers to corresponding parameter.</span></span> <span data-ttu-id="edb5c-119">Si uno de los punteros de cadena se deja en UX_NULL, se usa la cadena predeterminada de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="edb5c-119">If any one of the string pointer is left to UX_NULL, the default Azure RTOS string is used.</span></span>

<span data-ttu-id="edb5c-120">En este ejemplo, se proporciona la dirección del último bloque o LBA de la unidad, así como el tamaño del sector lógico.</span><span class="sxs-lookup"><span data-stu-id="edb5c-120">In this example, the drive's last block address or LBA is given as well as the logical sector size.</span></span> <span data-ttu-id="edb5c-121">La LBA es el número de sectores disponibles en el medio: 1.</span><span class="sxs-lookup"><span data-stu-id="edb5c-121">The LBA is the number of sectors available in the media –1.</span></span> <span data-ttu-id="edb5c-122">La longitud del bloque se establece en 512 en medios de almacenamiento normales.</span><span class="sxs-lookup"><span data-stu-id="edb5c-122">The block length is set to 512 in regular storage media.</span></span> <span data-ttu-id="edb5c-123">Se puede establecer en 2048 para las unidades ópticas.</span><span class="sxs-lookup"><span data-stu-id="edb5c-123">It can be set to 2048 for optical drives.</span></span>

<span data-ttu-id="edb5c-124">La aplicación debe pasar tres punteros de función de devolución de llamada para permitir que la clase de almacenamiento lea, escriba y obtenga el estado del medio.</span><span class="sxs-lookup"><span data-stu-id="edb5c-124">The application needs to pass three callback function pointers to allow the storage class to read, write and obtain status for the media.</span></span>

<span data-ttu-id="edb5c-125">En el ejemplo siguiente se muestran los prototipos de las funciones de lectura y escritura.</span><span class="sxs-lookup"><span data-stu-id="edb5c-125">The prototypes for the read and write functions are shown in the example below.</span></span>

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

<span data-ttu-id="edb5c-126">Donde:</span><span class="sxs-lookup"><span data-stu-id="edb5c-126">Where:</span></span>

- <span data-ttu-id="edb5c-127">*storage* es la instancia de la clase de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="edb5c-127">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="edb5c-128">*lun* es el LUN al que se dirige el comando.</span><span class="sxs-lookup"><span data-stu-id="edb5c-128">*lun* is the LUN the command is directed to.</span></span>
- <span data-ttu-id="edb5c-129">*data_pointer* es la dirección del búfer que se va a usar para la lectura o escritura.</span><span class="sxs-lookup"><span data-stu-id="edb5c-129">*data_pointer* is the address of the buffer to be used for reading or writing.</span></span>
- <span data-ttu-id="edb5c-130">*number_blocks* es el número de sectores para lectura y escritura.</span><span class="sxs-lookup"><span data-stu-id="edb5c-130">*number_blocks* is the number of sectors to read/write.</span></span>
- <span data-ttu-id="edb5c-131">*lba* es la dirección del sector que se va a leer.</span><span class="sxs-lookup"><span data-stu-id="edb5c-131">*lba* is the sector address to read.</span></span>
- <span data-ttu-id="edb5c-132">*media_status* se debe rellenar exactamente como el valor devuelto de la devolución de llamada del estado del medio.</span><span class="sxs-lookup"><span data-stu-id="edb5c-132">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="edb5c-133">El valor devuelto puede tener el valor UX_SUCCESS o UX_ERROR que indica una operación correcta o incorrecta.</span><span class="sxs-lookup"><span data-stu-id="edb5c-133">The return value can have either the value UX_SUCCESS or UX_ERROR indicating a successful or unsuccessful operation.</span></span> <span data-ttu-id="edb5c-134">Estas operaciones no necesitan devolver ningún otro código de error.</span><span class="sxs-lookup"><span data-stu-id="edb5c-134">These operations do not need to return any other error codes.</span></span> <span data-ttu-id="edb5c-135">Si hay un error en alguna operación, la clase de almacenamiento invocará la función de devolución de llamada de estado.</span><span class="sxs-lookup"><span data-stu-id="edb5c-135">If there is an error in any operation, the storage class will invoke the status call back function.</span></span>

<span data-ttu-id="edb5c-136">Esta función tiene el siguiente prototipo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-136">This function has the following prototype.</span></span>

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

<span data-ttu-id="edb5c-137">El parámetro de llamada media_id no se usa actualmente y siempre debe ser 0.</span><span class="sxs-lookup"><span data-stu-id="edb5c-137">The calling parameter media_id is not currently used and should always be 0.</span></span> <span data-ttu-id="edb5c-138">En el futuro, podrá usarse para distinguir varios dispositivos de almacenamiento o dispositivos de almacenamiento con varios LUN SCSI.</span><span class="sxs-lookup"><span data-stu-id="edb5c-138">In the future it may be used to distinguish multiple storage devices or storage devices with multiple SCSI LUNs.</span></span> <span data-ttu-id="edb5c-139">Esta versión de la clase de almacenamiento no admite varias instancias de la clase de almacenamiento o dispositivos de almacenamiento con varios LUN SCSI.</span><span class="sxs-lookup"><span data-stu-id="edb5c-139">This version of the storage class does not support multiple instances of the storage class or storage devices with multiple SCSI LUNs.</span></span>

<span data-ttu-id="edb5c-140">El valor devuelto es un código de error SCSI que puede tener el formato siguiente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-140">The return value is a SCSI error code that can have the following format.</span></span>

- <span data-ttu-id="edb5c-141">**Bits de 0 a 7** Clave de detección</span><span class="sxs-lookup"><span data-stu-id="edb5c-141">**Bits 0-7** Sense_key</span></span>
- <span data-ttu-id="edb5c-142">**Bits de 8 a 15** Código de detección adicional (ASC)</span><span class="sxs-lookup"><span data-stu-id="edb5c-142">**Bits 8-15** Additional Sense Code</span></span>
- <span data-ttu-id="edb5c-143">**Bits de 16 a 23** Código de detección adicional (ASCQ)</span><span class="sxs-lookup"><span data-stu-id="edb5c-143">**Bits 16-23** Additional Sense Code Qualifier</span></span>

<span data-ttu-id="edb5c-144">En la tabla siguiente se proporcionan las combinaciones posibles Sense/ASC/ASCQ.</span><span class="sxs-lookup"><span data-stu-id="edb5c-144">The following table provides the possible Sense/ASC/ASCQ combinations.</span></span>

| <span data-ttu-id="edb5c-145">Clave de detección</span><span class="sxs-lookup"><span data-stu-id="edb5c-145">Sense Key</span></span> | <span data-ttu-id="edb5c-146">ASC</span><span class="sxs-lookup"><span data-stu-id="edb5c-146">ASC</span></span> | <span data-ttu-id="edb5c-147">ASCQ</span><span class="sxs-lookup"><span data-stu-id="edb5c-147">ASCQ</span></span> | <span data-ttu-id="edb5c-148">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-148">Description</span></span>                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| <span data-ttu-id="edb5c-149">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-149">00</span></span>        | <span data-ttu-id="edb5c-150">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-150">00</span></span>  | <span data-ttu-id="edb5c-151">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-151">00</span></span>   | <span data-ttu-id="edb5c-152">SIN DETECCIÓN</span><span class="sxs-lookup"><span data-stu-id="edb5c-152">NO SENSE</span></span>                                          |
| <span data-ttu-id="edb5c-153">01</span><span class="sxs-lookup"><span data-stu-id="edb5c-153">01</span></span>        | <span data-ttu-id="edb5c-154">17</span><span class="sxs-lookup"><span data-stu-id="edb5c-154">17</span></span>  | <span data-ttu-id="edb5c-155">01</span><span class="sxs-lookup"><span data-stu-id="edb5c-155">01</span></span>   | <span data-ttu-id="edb5c-156">DATOS RECUPERADOS CON REINTENTOS</span><span class="sxs-lookup"><span data-stu-id="edb5c-156">RECOVERED DATA WITH RETRIES</span></span>                       |
| <span data-ttu-id="edb5c-157">01</span><span class="sxs-lookup"><span data-stu-id="edb5c-157">01</span></span>        | <span data-ttu-id="edb5c-158">18</span><span class="sxs-lookup"><span data-stu-id="edb5c-158">18</span></span>  | <span data-ttu-id="edb5c-159">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-159">00</span></span>   | <span data-ttu-id="edb5c-160">DATOS RECUPERADOS CON ECC</span><span class="sxs-lookup"><span data-stu-id="edb5c-160">RECOVERED DATA WITH ECC</span></span>                           |
| <span data-ttu-id="edb5c-161">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-161">02</span></span>        | <span data-ttu-id="edb5c-162">04</span><span class="sxs-lookup"><span data-stu-id="edb5c-162">04</span></span>  | <span data-ttu-id="edb5c-163">01</span><span class="sxs-lookup"><span data-stu-id="edb5c-163">01</span></span>   | <span data-ttu-id="edb5c-164">UNIDAD LÓGICA NO PREPARADA: PREPARÁNDOSE</span><span class="sxs-lookup"><span data-stu-id="edb5c-164">LOGICAL DRIVE NOT READY - BECOMING READY</span></span>          |
| <span data-ttu-id="edb5c-165">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-165">02</span></span>        | <span data-ttu-id="edb5c-166">04</span><span class="sxs-lookup"><span data-stu-id="edb5c-166">04</span></span>  | <span data-ttu-id="edb5c-167">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-167">02</span></span>   | <span data-ttu-id="edb5c-168">UNIDAD LÓGICA NO PREPARADA: SE REQUIERE INICIALIZACIÓN</span><span class="sxs-lookup"><span data-stu-id="edb5c-168">LOGICAL DRIVE NOT READY - INITIALIZATION REQUIRED</span></span> |
| <span data-ttu-id="edb5c-169">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-169">02</span></span>        | <span data-ttu-id="edb5c-170">04</span><span class="sxs-lookup"><span data-stu-id="edb5c-170">04</span></span>  | <span data-ttu-id="edb5c-171">04</span><span class="sxs-lookup"><span data-stu-id="edb5c-171">04</span></span>   | <span data-ttu-id="edb5c-172">UNIDAD LÓGICA NO PREPARADA: FORMATO EN CURSO</span><span class="sxs-lookup"><span data-stu-id="edb5c-172">LOGICAL UNIT NOT READY - FORMAT IN PROGRESS</span></span>       |
| <span data-ttu-id="edb5c-173">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-173">02</span></span>        | <span data-ttu-id="edb5c-174">04</span><span class="sxs-lookup"><span data-stu-id="edb5c-174">04</span></span>  | <span data-ttu-id="edb5c-175">FF</span><span class="sxs-lookup"><span data-stu-id="edb5c-175">FF</span></span>   | <span data-ttu-id="edb5c-176">UNIDAD LÓGICA NO PREPARADA: EL DISPOSITIVO ESTÁ OCUPADO</span><span class="sxs-lookup"><span data-stu-id="edb5c-176">LOGICAL DRIVE NOT READY - DEVICE IS BUSY</span></span>          |
| <span data-ttu-id="edb5c-177">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-177">02</span></span>        | <span data-ttu-id="edb5c-178">06</span><span class="sxs-lookup"><span data-stu-id="edb5c-178">06</span></span>  | <span data-ttu-id="edb5c-179">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-179">00</span></span>   | <span data-ttu-id="edb5c-180">NO SE ENCONTRÓ NINGUNA POSICIÓN DE REFERENCIA</span><span class="sxs-lookup"><span data-stu-id="edb5c-180">NO REFERENCE POSITION FOUND</span></span>                       |
| <span data-ttu-id="edb5c-181">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-181">02</span></span>        | <span data-ttu-id="edb5c-182">08</span><span class="sxs-lookup"><span data-stu-id="edb5c-182">08</span></span>  | <span data-ttu-id="edb5c-183">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-183">00</span></span>   | <span data-ttu-id="edb5c-184">ERROR DE COMUNICACIÓN DE UNIDAD LÓGICA</span><span class="sxs-lookup"><span data-stu-id="edb5c-184">LOGICAL UNIT COMMUNICATION FAILURE</span></span>                |
| <span data-ttu-id="edb5c-185">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-185">02</span></span>        | <span data-ttu-id="edb5c-186">08</span><span class="sxs-lookup"><span data-stu-id="edb5c-186">08</span></span>  | <span data-ttu-id="edb5c-187">01</span><span class="sxs-lookup"><span data-stu-id="edb5c-187">01</span></span>   | <span data-ttu-id="edb5c-188">TIEMPO DE ESPERA DE COMUNICACIÓN DE UNIDAD LÓGICA</span><span class="sxs-lookup"><span data-stu-id="edb5c-188">LOGICAL UNIT COMMUNICATION TIME-OUT</span></span>               |
| <span data-ttu-id="edb5c-189">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-189">02</span></span>        | <span data-ttu-id="edb5c-190">08</span><span class="sxs-lookup"><span data-stu-id="edb5c-190">08</span></span>  | <span data-ttu-id="edb5c-191">80</span><span class="sxs-lookup"><span data-stu-id="edb5c-191">80</span></span>   | <span data-ttu-id="edb5c-192">SATURACIÓN DE COMUNICACIÓN DE UNIDAD LÓGICA</span><span class="sxs-lookup"><span data-stu-id="edb5c-192">LOGICAL UNIT COMMUNICATION OVERRUN</span></span>                |
| <span data-ttu-id="edb5c-193">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-193">02</span></span>        | <span data-ttu-id="edb5c-194">3A</span><span class="sxs-lookup"><span data-stu-id="edb5c-194">3A</span></span>  | <span data-ttu-id="edb5c-195">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-195">00</span></span>   | <span data-ttu-id="edb5c-196">MEDIO NO PRESENTE</span><span class="sxs-lookup"><span data-stu-id="edb5c-196">MEDIUM NOT PRESENT</span></span>                                |
| <span data-ttu-id="edb5c-197">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-197">02</span></span>        | <span data-ttu-id="edb5c-198">54</span><span class="sxs-lookup"><span data-stu-id="edb5c-198">54</span></span>  | <span data-ttu-id="edb5c-199">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-199">00</span></span>   | <span data-ttu-id="edb5c-200">ERROR DE INTERFAZ DEL SISTEMA DE USB A HOST</span><span class="sxs-lookup"><span data-stu-id="edb5c-200">USB TO HOST SYSTEM INTERFACE FAILURE</span></span>              |
| <span data-ttu-id="edb5c-201">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-201">02</span></span>        | <span data-ttu-id="edb5c-202">80</span><span class="sxs-lookup"><span data-stu-id="edb5c-202">80</span></span>  | <span data-ttu-id="edb5c-203">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-203">00</span></span>   | <span data-ttu-id="edb5c-204">INSUFICIENTES RECURSOS</span><span class="sxs-lookup"><span data-stu-id="edb5c-204">INSUFFICIENT RESOURCES</span></span>                            |
| <span data-ttu-id="edb5c-205">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-205">02</span></span>        | <span data-ttu-id="edb5c-206">FF</span><span class="sxs-lookup"><span data-stu-id="edb5c-206">FF</span></span>  | <span data-ttu-id="edb5c-207">FF</span><span class="sxs-lookup"><span data-stu-id="edb5c-207">FF</span></span>   | <span data-ttu-id="edb5c-208">ERROR DESCONOCIDO</span><span class="sxs-lookup"><span data-stu-id="edb5c-208">UNKNOWN ERROR</span></span>                                     |
| <span data-ttu-id="edb5c-209">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-209">03</span></span>        | <span data-ttu-id="edb5c-210">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-210">02</span></span>  | <span data-ttu-id="edb5c-211">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-211">00</span></span>   | <span data-ttu-id="edb5c-212">NO SE COMPLETÓ LA BÚSQUEDA</span><span class="sxs-lookup"><span data-stu-id="edb5c-212">NO SEEK COMPLETE</span></span>                                  |
| <span data-ttu-id="edb5c-213">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-213">03</span></span>        | <span data-ttu-id="edb5c-214">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-214">03</span></span>  | <span data-ttu-id="edb5c-215">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-215">00</span></span>   | <span data-ttu-id="edb5c-216">ERROR DE ESCRITURA</span><span class="sxs-lookup"><span data-stu-id="edb5c-216">WRITE FAULT</span></span>                                       |
| <span data-ttu-id="edb5c-217">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-217">03</span></span>        | <span data-ttu-id="edb5c-218">10</span><span class="sxs-lookup"><span data-stu-id="edb5c-218">10</span></span>  | <span data-ttu-id="edb5c-219">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-219">00</span></span>   | <span data-ttu-id="edb5c-220">ERROR CRC DE ID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-220">ID CRC ERROR</span></span>                                      |
| <span data-ttu-id="edb5c-221">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-221">03</span></span>        | <span data-ttu-id="edb5c-222">11</span><span class="sxs-lookup"><span data-stu-id="edb5c-222">11</span></span>  | <span data-ttu-id="edb5c-223">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-223">00</span></span>   | <span data-ttu-id="edb5c-224">ERROR DE LECTURA NO RECUPERADO</span><span class="sxs-lookup"><span data-stu-id="edb5c-224">UNRECOVERED READ ERROR</span></span>                            |
| <span data-ttu-id="edb5c-225">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-225">03</span></span>        | <span data-ttu-id="edb5c-226">12</span><span class="sxs-lookup"><span data-stu-id="edb5c-226">12</span></span>  | <span data-ttu-id="edb5c-227">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-227">00</span></span>   | <span data-ttu-id="edb5c-228">NO SE ENCONTRÓ LA MARCA DE DIRECCIÓN PARA EL CAMPO DE ID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-228">ADDRESS MARK NOT FOUND FOR ID FIELD</span></span>               |
| <span data-ttu-id="edb5c-229">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-229">03</span></span>        | <span data-ttu-id="edb5c-230">13</span><span class="sxs-lookup"><span data-stu-id="edb5c-230">13</span></span>  | <span data-ttu-id="edb5c-231">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-231">00</span></span>   | <span data-ttu-id="edb5c-232">NO SE ENCONTRÓ LA MARCA DE DIRECCIÓN PARA EL CAMPO DE DATOS</span><span class="sxs-lookup"><span data-stu-id="edb5c-232">ADDRESS MARK NOT FOUND FOR DATA FIELD</span></span>             |
| <span data-ttu-id="edb5c-233">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-233">03</span></span>        | <span data-ttu-id="edb5c-234">14</span><span class="sxs-lookup"><span data-stu-id="edb5c-234">14</span></span>  | <span data-ttu-id="edb5c-235">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-235">00</span></span>   | <span data-ttu-id="edb5c-236">NO SE ENCONTRÓ LA ENTIDAD REGISTRADA</span><span class="sxs-lookup"><span data-stu-id="edb5c-236">RECORDED ENTITY NOT FOUND</span></span>                         |
| <span data-ttu-id="edb5c-237">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-237">03</span></span>        | <span data-ttu-id="edb5c-238">30</span><span class="sxs-lookup"><span data-stu-id="edb5c-238">30</span></span>  | <span data-ttu-id="edb5c-239">01</span><span class="sxs-lookup"><span data-stu-id="edb5c-239">01</span></span>   | <span data-ttu-id="edb5c-240">NO SE PUEDE LEER EL MEDIO: FORMATO DESCONOCIDO</span><span class="sxs-lookup"><span data-stu-id="edb5c-240">CANNOT READ MEDIUM - UNKNOWN FORMAT</span></span>               |
| <span data-ttu-id="edb5c-241">03</span><span class="sxs-lookup"><span data-stu-id="edb5c-241">03</span></span>        | <span data-ttu-id="edb5c-242">31</span><span class="sxs-lookup"><span data-stu-id="edb5c-242">31</span></span>  | <span data-ttu-id="edb5c-243">01</span><span class="sxs-lookup"><span data-stu-id="edb5c-243">01</span></span>   | <span data-ttu-id="edb5c-244">ERROR DEL COMANDO DE FORMATO</span><span class="sxs-lookup"><span data-stu-id="edb5c-244">FORMAT COMMAND FAILED</span></span>                             |
| <span data-ttu-id="edb5c-245">04</span><span class="sxs-lookup"><span data-stu-id="edb5c-245">04</span></span>        | <span data-ttu-id="edb5c-246">40</span><span class="sxs-lookup"><span data-stu-id="edb5c-246">40</span></span>  | <span data-ttu-id="edb5c-247">NN</span><span class="sxs-lookup"><span data-stu-id="edb5c-247">NN</span></span>   | <span data-ttu-id="edb5c-248">ERROR DE DIAGNÓSTICO EN EL COMPONENTE NN (80H-FFH)</span><span class="sxs-lookup"><span data-stu-id="edb5c-248">DIAGNOSTIC FAILURE ON COMPONENT NN (80H-FFH)</span></span>      |
| <span data-ttu-id="edb5c-249">05</span><span class="sxs-lookup"><span data-stu-id="edb5c-249">05</span></span>        | <span data-ttu-id="edb5c-250">1A</span><span class="sxs-lookup"><span data-stu-id="edb5c-250">1A</span></span>  | <span data-ttu-id="edb5c-251">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-251">00</span></span>   | <span data-ttu-id="edb5c-252">ERROR DE LONGITUD DE LA LISTA DE PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="edb5c-252">PARAMETER LIST LENGTH ERROR</span></span>                       |
| <span data-ttu-id="edb5c-253">05</span><span class="sxs-lookup"><span data-stu-id="edb5c-253">05</span></span>        | <span data-ttu-id="edb5c-254">20</span><span class="sxs-lookup"><span data-stu-id="edb5c-254">20</span></span>  | <span data-ttu-id="edb5c-255">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-255">00</span></span>   | <span data-ttu-id="edb5c-256">CÓDIGO DE OPERACIÓN DE COMANDO NO VÁLIDO</span><span class="sxs-lookup"><span data-stu-id="edb5c-256">INVALID COMMAND OPERATION CODE</span></span>                    |
| <span data-ttu-id="edb5c-257">05</span><span class="sxs-lookup"><span data-stu-id="edb5c-257">05</span></span>        | <span data-ttu-id="edb5c-258">21</span><span class="sxs-lookup"><span data-stu-id="edb5c-258">21</span></span>  | <span data-ttu-id="edb5c-259">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-259">00</span></span>   | <span data-ttu-id="edb5c-260">DIRECCIÓN DE BLOQUE LÓGICO FUERA DEL INTERVALO</span><span class="sxs-lookup"><span data-stu-id="edb5c-260">LOGICAL BLOCK ADDRESS OUT OF RANGE</span></span>                |
| <span data-ttu-id="edb5c-261">05</span><span class="sxs-lookup"><span data-stu-id="edb5c-261">05</span></span>        | <span data-ttu-id="edb5c-262">24</span><span class="sxs-lookup"><span data-stu-id="edb5c-262">24</span></span>  | <span data-ttu-id="edb5c-263">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-263">00</span></span>   | <span data-ttu-id="edb5c-264">CAMPO NO VÁLIDO EN EL PAQUETE DE COMANDOS</span><span class="sxs-lookup"><span data-stu-id="edb5c-264">INVALID FIELD IN COMMAND PACKET</span></span>                   |
| <span data-ttu-id="edb5c-265">05</span><span class="sxs-lookup"><span data-stu-id="edb5c-265">05</span></span>        | <span data-ttu-id="edb5c-266">25</span><span class="sxs-lookup"><span data-stu-id="edb5c-266">25</span></span>  | <span data-ttu-id="edb5c-267">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-267">00</span></span>   | <span data-ttu-id="edb5c-268">UNIDAD LÓGICA NO ADMITIDA</span><span class="sxs-lookup"><span data-stu-id="edb5c-268">LOGICAL UNIT NOT SUPPORTED</span></span>                        |
| <span data-ttu-id="edb5c-269">05</span><span class="sxs-lookup"><span data-stu-id="edb5c-269">05</span></span>        | <span data-ttu-id="edb5c-270">26</span><span class="sxs-lookup"><span data-stu-id="edb5c-270">26</span></span>  | <span data-ttu-id="edb5c-271">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-271">00</span></span>   | <span data-ttu-id="edb5c-272">CAMPO NO VÁLIDO EN LA LISTA DE PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="edb5c-272">INVALID FIELD IN PARAMETER LIST</span></span>                   |
| <span data-ttu-id="edb5c-273">05</span><span class="sxs-lookup"><span data-stu-id="edb5c-273">05</span></span>        | <span data-ttu-id="edb5c-274">26</span><span class="sxs-lookup"><span data-stu-id="edb5c-274">26</span></span>  | <span data-ttu-id="edb5c-275">01</span><span class="sxs-lookup"><span data-stu-id="edb5c-275">01</span></span>   | <span data-ttu-id="edb5c-276">PARÁMETRO NO ADMITIDO</span><span class="sxs-lookup"><span data-stu-id="edb5c-276">PARAMETER NOT SUPPORTED</span></span>                           |
| <span data-ttu-id="edb5c-277">05</span><span class="sxs-lookup"><span data-stu-id="edb5c-277">05</span></span>        | <span data-ttu-id="edb5c-278">26</span><span class="sxs-lookup"><span data-stu-id="edb5c-278">26</span></span>  | <span data-ttu-id="edb5c-279">02</span><span class="sxs-lookup"><span data-stu-id="edb5c-279">02</span></span>   | <span data-ttu-id="edb5c-280">VALOR DE PARÁMETRO NO VÁLIDO</span><span class="sxs-lookup"><span data-stu-id="edb5c-280">PARAMETER VALUE INVALID</span></span>                           |
| <span data-ttu-id="edb5c-281">05</span><span class="sxs-lookup"><span data-stu-id="edb5c-281">05</span></span>        | <span data-ttu-id="edb5c-282">39</span><span class="sxs-lookup"><span data-stu-id="edb5c-282">39</span></span>  | <span data-ttu-id="edb5c-283">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-283">00</span></span>   | <span data-ttu-id="edb5c-284">NO SE ADMITE GUARDAR PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="edb5c-284">SAVING PARAMETERS NOT SUPPORT</span></span>                     |
| <span data-ttu-id="edb5c-285">06</span><span class="sxs-lookup"><span data-stu-id="edb5c-285">06</span></span>        | <span data-ttu-id="edb5c-286">28</span><span class="sxs-lookup"><span data-stu-id="edb5c-286">28</span></span>  | <span data-ttu-id="edb5c-287">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-287">00</span></span>   | <span data-ttu-id="edb5c-288">TRANSICIÓN DE NO PREPARADO A PREPARADO: SE CAMBIÓ EL MEDIO</span><span class="sxs-lookup"><span data-stu-id="edb5c-288">NOT READY TO READY TRANSITION – MEDIA CHANGED</span></span>     |
| <span data-ttu-id="edb5c-289">06</span><span class="sxs-lookup"><span data-stu-id="edb5c-289">06</span></span>        | <span data-ttu-id="edb5c-290">29</span><span class="sxs-lookup"><span data-stu-id="edb5c-290">29</span></span>  | <span data-ttu-id="edb5c-291">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-291">00</span></span>   | <span data-ttu-id="edb5c-292">SE HA PRODUCIDO UN RESTABLECIMIENTO DE ENCENDIDO O DE DISPOSITIVO DE BUS</span><span class="sxs-lookup"><span data-stu-id="edb5c-292">POWER ON RESET OR BUS DEVICE RESET OCCURRED</span></span>       |
| <span data-ttu-id="edb5c-293">06</span><span class="sxs-lookup"><span data-stu-id="edb5c-293">06</span></span>        | <span data-ttu-id="edb5c-294">2F</span><span class="sxs-lookup"><span data-stu-id="edb5c-294">2F</span></span>  | <span data-ttu-id="edb5c-295">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-295">00</span></span>   | <span data-ttu-id="edb5c-296">COMANDOS DESACTIVADOS POR OTRO INICIADOR</span><span class="sxs-lookup"><span data-stu-id="edb5c-296">COMMANDS CLEARED BY ANOTHER INITIATOR</span></span>             |
| <span data-ttu-id="edb5c-297">07</span><span class="sxs-lookup"><span data-stu-id="edb5c-297">07</span></span>        | <span data-ttu-id="edb5c-298">27</span><span class="sxs-lookup"><span data-stu-id="edb5c-298">27</span></span>  | <span data-ttu-id="edb5c-299">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-299">00</span></span>   | <span data-ttu-id="edb5c-300">MEDIO PROTEGIDO CONTRA ESCRITURA</span><span class="sxs-lookup"><span data-stu-id="edb5c-300">WRITE PROTECTED MEDIA</span></span>                             |
| <span data-ttu-id="edb5c-301">0B</span><span class="sxs-lookup"><span data-stu-id="edb5c-301">0B</span></span>        | <span data-ttu-id="edb5c-302">4E</span><span class="sxs-lookup"><span data-stu-id="edb5c-302">4E</span></span>  | <span data-ttu-id="edb5c-303">00</span><span class="sxs-lookup"><span data-stu-id="edb5c-303">00</span></span>   | <span data-ttu-id="edb5c-304">SE INTENTÓ UN COMANDO SUPERPUESTO</span><span class="sxs-lookup"><span data-stu-id="edb5c-304">OVERLAPPED COMMAND ATTEMPTED</span></span>                      |

<span data-ttu-id="edb5c-305">Hay dos devoluciones de llamada adicionales opcionales que la aplicación puede implementar; una es para responder a un comando **GET_STATUS_NOTIFICATION** y la otra es para responder al comando **SYNCHRONIZE_CACHE**.</span><span class="sxs-lookup"><span data-stu-id="edb5c-305">There are two additional, optional callbacks the application may implement; one is for responding to a **GET_STATUS_NOTIFICATION** command and the other is for responding to the **SYNCHRONIZE_CACHE** command.</span></span>

<span data-ttu-id="edb5c-306">Si la aplicación desea controlar el comando GET_STATUS_NOTIFICATION desde el host, debe implementar una devolución de llamada con el siguiente prototipo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-306">If the application would like to handle the GET_STATUS_NOTIFICATION command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

<span data-ttu-id="edb5c-307">Donde:</span><span class="sxs-lookup"><span data-stu-id="edb5c-307">Where:</span></span>

- <span data-ttu-id="edb5c-308">*storage* es la instancia de la clase de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="edb5c-308">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="edb5c-309">*media_id* no se usa actualmente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-309">*media_id* is not currently used.</span></span> <span data-ttu-id="edb5c-310">notification_class especifica la clase de notificación.</span><span class="sxs-lookup"><span data-stu-id="edb5c-310">notification_class specifies the class of notification.</span></span>
- <span data-ttu-id="edb5c-311">La aplicación debe establecer *media_notification* en el búfer que contiene la respuesta de la notificación.</span><span class="sxs-lookup"><span data-stu-id="edb5c-311">*media_notification* should be set by the application to the buffer containing the response for the notification.</span></span>
- <span data-ttu-id="edb5c-312">La aplicación debe establecer *media_notification_length* para que contenga la longitud del búfer de respuesta.</span><span class="sxs-lookup"><span data-stu-id="edb5c-312">*media_notification_length* should be set by the application to contain the length of the response buffer.</span></span>

<span data-ttu-id="edb5c-313">El valor devuelto indica si el comando se ha ejecutado correctamente o no; debe ser **UX_SUCCESS** o **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="edb5c-313">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

<span data-ttu-id="edb5c-314">Si la aplicación no implementa esta devolución de llamada, al recibir el comando **GET_STATUS_NOTIFICATION**, USBX notificará al host que el comando no está implementado.</span><span class="sxs-lookup"><span data-stu-id="edb5c-314">If the application does not implement this callback, then upon receiving the **GET_STATUS_NOTIFICATION** command, USBX will notify the host that the command is not implemented.</span></span>

<span data-ttu-id="edb5c-315">El comando **SYNCHRONIZE_CACHE** debe procesarse si la aplicación usa una caché para las escrituras desde el host.</span><span class="sxs-lookup"><span data-stu-id="edb5c-315">The **SYNCHRONIZE_CACHE** command should be handled if the application is utilizing a cache for writes from the host.</span></span> <span data-ttu-id="edb5c-316">Un host puede enviar este comando si sabe que el dispositivo de almacenamiento está a punto de desconectarse, por ejemplo, en Windows, si hace clic con el botón secundario en el icono de una unidad flash de la barra de herramientas y selecciona "Expulsar \[nombre del dispositivo de almacenamiento\]", Windows emitirá el comando **SYNCHRONIZE_CACHE** a ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-316">A host may send this command if it knows the storage device is about to be disconnected, for example, in Windows, if you right click a flash drive icon in the toolbar and select "Eject \[storage device name\]", Windows will issue the **SYNCHRONIZE_CACHE** command to that device.</span></span>

<span data-ttu-id="edb5c-317">Si la aplicación quiere procesar el comando **GET_STATUS_NOTIFICATION** desde el host, debe implementar una devolución de llamada con el siguiente prototipo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-317">If the application would like to handle the **GET_STATUS_NOTIFICATION** command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

<span data-ttu-id="edb5c-318">Donde:</span><span class="sxs-lookup"><span data-stu-id="edb5c-318">Where:</span></span>

- <span data-ttu-id="edb5c-319">*storage* es la instancia de la clase de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="edb5c-319">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="edb5c-320">*lun* es un parámetro que especifica a qué LUN se dirige el comando.</span><span class="sxs-lookup"><span data-stu-id="edb5c-320">*lun* parameter specifies which LUN the command is directed to.</span></span>
- <span data-ttu-id="edb5c-321">*number_blocks* especifica el número de bloques que se van a sincronizar.</span><span class="sxs-lookup"><span data-stu-id="edb5c-321">*number_blocks* specifies the number of blocks to synchronize.</span></span>
- <span data-ttu-id="edb5c-322">*lba* es la dirección del sector del primer bloque que se va a sincronizar.</span><span class="sxs-lookup"><span data-stu-id="edb5c-322">*lba* is the sector address of the first block to synchronize.</span></span>
- <span data-ttu-id="edb5c-323">*media_status* se debe rellenar exactamente como el valor devuelto de la devolución de llamada del estado del medio.</span><span class="sxs-lookup"><span data-stu-id="edb5c-323">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="edb5c-324">El valor devuelto indica si el comando se ha ejecutado correctamente o no; debe ser **UX_SUCCESS** o **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="edb5c-324">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

### <a name="multiple-scsi-lun"></a><span data-ttu-id="edb5c-325">LUN SCSI múltiple</span><span class="sxs-lookup"><span data-stu-id="edb5c-325">Multiple SCSI LUN</span></span>

<span data-ttu-id="edb5c-326">La clase de almacenamiento de dispositivo USBX admite varios LUN.</span><span class="sxs-lookup"><span data-stu-id="edb5c-326">The USBX device storage class supports multiple LUNs.</span></span> <span data-ttu-id="edb5c-327">Por lo tanto, es posible crear un dispositivo de almacenamiento que actúe como un CD-ROM y un disco Flash al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-327">It is therefore possible to create a storage device that acts as a CD-ROM and a Flash disk at the same time.</span></span> <span data-ttu-id="edb5c-328">En tal caso, la inicialización sería ligeramente diferente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-328">In such a case, the initialization would be slightly different.</span></span> <span data-ttu-id="edb5c-329">A continuación, se muestra un ejemplo de un disco Flash y un CD-ROM:</span><span class="sxs-lookup"><span data-stu-id="edb5c-329">Here is an example for a Flash Disk and CD-ROM:</span></span>

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a><span data-ttu-id="edb5c-330">Clase CDC-ACM de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="edb5c-330">USB Device CDC-ACM Class</span></span>

<span data-ttu-id="edb5c-331">La clase CDC-ACM de dispositivo host USB permite que un sistema host USB se comunique con el dispositivo como un dispositivo serie.</span><span class="sxs-lookup"><span data-stu-id="edb5c-331">The USB device CDC-ACM class allows for a USB host system to communicate with the device as a serial device.</span></span> <span data-ttu-id="edb5c-332">Esta clase se basa en el estándar USB y es un subconjunto del estándar CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-332">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="edb5c-333">Un marco de dispositivos compatible con CDC-ACM debe declararse en la pila de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="edb5c-333">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="edb5c-334">A continuación, se muestra un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-334">An example is found here below.</span></span>

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

<span data-ttu-id="edb5c-335">La clase CDC-ACM usa un marco de dispositivo compuesto para agrupar interfaces (control y datos).</span><span class="sxs-lookup"><span data-stu-id="edb5c-335">The CDC-ACM class uses a composite device framework to group interfaces (control and data).</span></span> <span data-ttu-id="edb5c-336">Como resultado, debe tener cuidado al definir el descriptor de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-336">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="edb5c-337">USBX se basa en el descriptor IAD para saber internamente cómo enlazar interfaces.</span><span class="sxs-lookup"><span data-stu-id="edb5c-337">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="edb5c-338">El descriptor IAD debe declararse antes de las interfaces y contener la primera interfaz de la clase CDC-ACM y el número de interfaces asociadas.</span><span class="sxs-lookup"><span data-stu-id="edb5c-338">The IAD descriptor should be declared before the interfaces and contain the first interface of the CDC-ACM class and how many interfaces are attached.</span></span>

<span data-ttu-id="edb5c-339">La clase CDC-ACM también usa un descriptor funcional de unión que realiza la misma función que el descriptor IAD más reciente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-339">The CDC-ACM class also uses a union functional descriptor which performs the same function as the newer IAD descriptor.</span></span> <span data-ttu-id="edb5c-340">Aunque debe declararse un descriptor funcional de unión por motivos históricos y por compatibilidad con el lado host, USBX no lo usa.</span><span class="sxs-lookup"><span data-stu-id="edb5c-340">Although a Union Functional descriptor must be declared for historical reasons and compatibility with the host side, it is not used by USBX.</span></span>

<span data-ttu-id="edb5c-341">La inicialización de la clase CDC-ACM espera los siguientes parámetros.</span><span class="sxs-lookup"><span data-stu-id="edb5c-341">The initialization of the CDC-ACM class expects the following parameters.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

<span data-ttu-id="edb5c-342">Los dos parámetros definidos son punteros de devolución de llamada a las aplicaciones de usuario a las que se llamará cuando la pila active o desactive esta clase.</span><span class="sxs-lookup"><span data-stu-id="edb5c-342">The 2 parameters defined are callback pointers into the user applications that will be called when the stack activates or deactivate this class.</span></span>

<span data-ttu-id="edb5c-343">El tercer parámetro definido es un puntero de devolución de llamada a la aplicación de usuario a la que se llamará cuando se produzca un cambio de parámetro de código de línea o de estado de línea.</span><span class="sxs-lookup"><span data-stu-id="edb5c-343">The third parameter defined is a callback pointer to the user application that will be called when there is line coding or line states parameter change.</span></span> <span data-ttu-id="edb5c-344">Por ejemplo, cuando hay una solicitud del host para cambiar el estado DTR a **TRUE**, se invoca la devolución de llamada, en ella la aplicación de usuario puede comprobar los estados de línea a través de la función IOCTL para saber si el host está preparado para la comunicación.</span><span class="sxs-lookup"><span data-stu-id="edb5c-344">E.g., when there is request from host to change DTR state to **TRUE**, the callback is invoked, in it user application can check line states through IOCTL function to kow host is ready for communication.</span></span>

<span data-ttu-id="edb5c-345">CDC-ACM se basa en un estándar USB-IF y se reconoce de forma automática por los sistemas operativos MAC y Linux.</span><span class="sxs-lookup"><span data-stu-id="edb5c-345">The CDC-ACM is based on a USB-IF standard and is automatically recognized by MACOs and Linux operating systems.</span></span> <span data-ttu-id="edb5c-346">En las plataformas de Windows, esta clase requiere un archivo. inf para la versión de Windows anterior a la versión 10.</span><span class="sxs-lookup"><span data-stu-id="edb5c-346">On Windows platforms, this class requires a .inf file for Windows version prior to 10.</span></span> <span data-ttu-id="edb5c-347">Windows 10 no requiere ningún archivo. inf.</span><span class="sxs-lookup"><span data-stu-id="edb5c-347">Windows 10 does not require any .inf files.</span></span> <span data-ttu-id="edb5c-348">Asimismo, proporcionamos una plantilla para la clase CDC-ACM que se puede encontrar en el directorio ***usbx_windows_host_files***.</span><span class="sxs-lookup"><span data-stu-id="edb5c-348">We supply a template for the CDC-ACM class and it can be found in the ***usbx_windows_host_files*** directory.</span></span> <span data-ttu-id="edb5c-349">Para obtener una versión más reciente de Windows, se debe usar el archivo CDC_ACM_Template_Win7_64bit.inf (excepto Win10).</span><span class="sxs-lookup"><span data-stu-id="edb5c-349">For more recent version of Windows the file CDC_ACM_Template_Win7_64bit.inf should be used (except Win10).</span></span> <span data-ttu-id="edb5c-350">Este archivo debe modificarse para reflejar el valor de PID/VID que usa el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-350">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="edb5c-351">El valor PID/VID será específico para el cliente final cuando la empresa y el producto se registren mediante el valor USB-IF.</span><span class="sxs-lookup"><span data-stu-id="edb5c-351">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="edb5c-352">En el archivo .inf, los campos que se van a modificar se encuentran aquí.</span><span class="sxs-lookup"><span data-stu-id="edb5c-352">In the inf file, the fields to modify are located here.</span></span>

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

<span data-ttu-id="edb5c-353">En el marco del dispositivo CDC-ACM, el valor PID/VID se almacena en el descriptor del dispositivo (consulte el descriptor de dispositivo que se declaró anteriormente).</span><span class="sxs-lookup"><span data-stu-id="edb5c-353">In the device framework of the CDC-ACM device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="edb5c-354">Cuando un sistema host USB detecta el dispositivo USB CDC-ACM, monta una clase serie y el dispositivo se puede usar con cualquier programa de terminal serie.</span><span class="sxs-lookup"><span data-stu-id="edb5c-354">When a USB host systems discovers the USB CDC-ACM device, it will mount a serial class and the device can be used with any serial terminal program.</span></span> <span data-ttu-id="edb5c-355">Consulte el sistema operativo host como referencia.</span><span class="sxs-lookup"><span data-stu-id="edb5c-355">See the host Operating System for reference.</span></span>

<span data-ttu-id="edb5c-356">A continuación, se definen las funciones de API de clase CDC-ACM.</span><span class="sxs-lookup"><span data-stu-id="edb5c-356">The CDC-ACM class API functions are defined below.</span></span>

### <a name="ux_device_class_cdc_acm_ioctl"></a><span data-ttu-id="edb5c-357">ux_device_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="edb5c-357">ux_device_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="edb5c-358">Ejecutar IOCTL en la interfaz CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="edb5c-358">Perform IOCTL on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-359">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-359">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="edb5c-360">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-360">Description</span></span>

<span data-ttu-id="edb5c-361">Se llama a esta función cuando una aplicación necesita realizar varias llamadas IOCTL a la interfaz CDC-ACM.</span><span class="sxs-lookup"><span data-stu-id="edb5c-361">This function is called when an application needs to perform various ioctl calls to the cdc acm interface</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-362">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-362">Parameters</span></span>

- <span data-ttu-id="edb5c-363">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-363">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-364">**ioctl_function**: función IOCTL que se va a realizar.</span><span class="sxs-lookup"><span data-stu-id="edb5c-364">**ioctl_function**: Ioctl function to be performed.</span></span>
- <span data-ttu-id="edb5c-365">**parameter**: puntero a un parámetro específico de la llamada IOCTL.</span><span class="sxs-lookup"><span data-stu-id="edb5c-365">**parameter**: Pointer to a parameter specific to the ioctl call.</span></span>

### <a name="return-value"></a><span data-ttu-id="edb5c-366">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-366">Return Value</span></span>

- <span data-ttu-id="edb5c-367">**UX_SUCCESS** (0X00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-367">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="edb5c-368">**UX_ERROR** (0xFF) Error de la función.</span><span class="sxs-lookup"><span data-stu-id="edb5c-368">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-369">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-369">Example</span></span>

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a><span data-ttu-id="edb5c-370">Funciones IOCTL:</span><span class="sxs-lookup"><span data-stu-id="edb5c-370">Ioctl functions:</span></span>

| <span data-ttu-id="edb5c-371">Función</span><span class="sxs-lookup"><span data-stu-id="edb5c-371">Function</span></span>                                        | <span data-ttu-id="edb5c-372">Value</span><span class="sxs-lookup"><span data-stu-id="edb5c-372">Value</span></span> |
| ----------------------------------------------- | - |
| <span data-ttu-id="edb5c-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="edb5c-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>    | <span data-ttu-id="edb5c-374">1</span><span class="sxs-lookup"><span data-stu-id="edb5c-374">1</span></span> |
| <span data-ttu-id="edb5c-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="edb5c-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>    | <span data-ttu-id="edb5c-376">2</span><span class="sxs-lookup"><span data-stu-id="edb5c-376">2</span></span> |
| <span data-ttu-id="edb5c-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="edb5c-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>     | <span data-ttu-id="edb5c-378">3</span><span class="sxs-lookup"><span data-stu-id="edb5c-378">3</span></span> |
| <span data-ttu-id="edb5c-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="edb5c-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>         | <span data-ttu-id="edb5c-380">4</span><span class="sxs-lookup"><span data-stu-id="edb5c-380">4</span></span> |
| <span data-ttu-id="edb5c-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="edb5c-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>     | <span data-ttu-id="edb5c-382">5</span><span class="sxs-lookup"><span data-stu-id="edb5c-382">5</span></span> |
| <span data-ttu-id="edb5c-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="edb5c-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span> | <span data-ttu-id="edb5c-384">6</span><span class="sxs-lookup"><span data-stu-id="edb5c-384">6</span></span> |
| <span data-ttu-id="edb5c-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="edb5c-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>  | <span data-ttu-id="edb5c-386">7</span><span class="sxs-lookup"><span data-stu-id="edb5c-386">7</span></span> |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="edb5c-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="edb5c-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>

<span data-ttu-id="edb5c-388">Ejecutar el establecimiento de codificación de línea de IOCTL en la interfaz CDC-AC M</span><span class="sxs-lookup"><span data-stu-id="edb5c-388">Perform IOCTL Set Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-389">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-389">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="edb5c-390">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-390">Description</span></span>

<span data-ttu-id="edb5c-391">Se llama a esta función cuando una aplicación necesita establecer los parámetros de codificación de línea.</span><span class="sxs-lookup"><span data-stu-id="edb5c-391">This function is called when an application needs to Set the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-392">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-392">Parameters</span></span>

- <span data-ttu-id="edb5c-393">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-393">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="edb5c-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="edb5c-395">**parámetro**: puntero a una estructura de parámetros de línea:</span><span class="sxs-lookup"><span data-stu-id="edb5c-395">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="edb5c-396">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-396">Return Value</span></span>

<span data-ttu-id="edb5c-397">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-397">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-398">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-398">Example</span></span>

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="edb5c-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="edb5c-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>

<span data-ttu-id="edb5c-400">Ejecutar la obtención de la codificación de línea de IOCTL en la interfaz CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="edb5c-400">Perform IOCTL Get Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-401">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-401">Prototype</span></span>

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="edb5c-402">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-402">Description</span></span>

<span data-ttu-id="edb5c-403">Se llama a esta función cuando una aplicación necesita obtener los parámetros de codificación de línea.</span><span class="sxs-lookup"><span data-stu-id="edb5c-403">This function is called when an application needs to Get the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-404">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-404">Parameters</span></span>

- <span data-ttu-id="edb5c-405">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-405">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="edb5c-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span></span>
- <span data-ttu-id="edb5c-407">**parámetro**: puntero a una estructura de parámetros de línea:</span><span class="sxs-lookup"><span data-stu-id="edb5c-407">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="edb5c-408">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-408">Return Value</span></span>

- <span data-ttu-id="edb5c-409">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-409">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-410">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-410">Example</span></span>

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a><span data-ttu-id="edb5c-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="edb5c-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>

<span data-ttu-id="edb5c-412">Ejecutar la obtención de estado de línea de IOCTL en la interfaz CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="edb5c-412">Perform IOCTL Get Line State on the CDC-ACM interface</span></span>

## <a name="prototype"></a><span data-ttu-id="edb5c-413">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-413">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="edb5c-414">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-414">Description</span></span>

<span data-ttu-id="edb5c-415">Se llama a esta función cuando una aplicación necesita obtener los parámetros de estado de línea.</span><span class="sxs-lookup"><span data-stu-id="edb5c-415">This function is called when an application needs to Get the Line State parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-416">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-416">Parameters</span></span>

- <span data-ttu-id="edb5c-417">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-417">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="edb5c-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>
- <span data-ttu-id="edb5c-419">**parámetro**: puntero a una estructura de parámetros de línea:</span><span class="sxs-lookup"><span data-stu-id="edb5c-419">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="edb5c-420">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-420">Return Value</span></span>

- <span data-ttu-id="edb5c-421">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-421">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-422">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-422">Example</span></span>

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="edb5c-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="edb5c-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>

<span data-ttu-id="edb5c-424">Ejecutar el establecimiento de estado de línea de IOCTL en la interfaz CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="edb5c-424">Perform IOCTL Set Line State on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-425">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-425">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="edb5c-426">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-426">Description</span></span>

<span data-ttu-id="edb5c-427">Se llama a esta función cuando una aplicación necesita obtener los parámetros de estado de línea.</span><span class="sxs-lookup"><span data-stu-id="edb5c-427">This function is called when an application needs to Get the Line State parameters</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-428">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-428">Parameters</span></span>

- <span data-ttu-id="edb5c-429">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-429">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="edb5c-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="edb5c-431">**parámetro**: puntero a una estructura de parámetros de línea:</span><span class="sxs-lookup"><span data-stu-id="edb5c-431">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="edb5c-432">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-432">Return Value</span></span>

- <span data-ttu-id="edb5c-433">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-433">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-434">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-434">Example</span></span>

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a><span data-ttu-id="edb5c-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="edb5c-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>

<span data-ttu-id="edb5c-436">Ejecutar ABORT PIPE de IOCTL en la interfaz CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="edb5c-436">Perform IOCTL ABORT PIPE on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-437">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-437">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="edb5c-438">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-438">Description</span></span>

<span data-ttu-id="edb5c-439">Se llama a esta función cuando una aplicación necesita anular una canalización.</span><span class="sxs-lookup"><span data-stu-id="edb5c-439">This function is called when an application needs to abort a pipe.</span></span> <span data-ttu-id="edb5c-440">Por ejemplo, para anular una escritura en curso, se debe pasar UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT como parámetro.</span><span class="sxs-lookup"><span data-stu-id="edb5c-440">For example, to abort an ongoing write, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT should be passed as the parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-441">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-441">Parameters</span></span>

- <span data-ttu-id="edb5c-442">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-442">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="edb5c-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>
- <span data-ttu-id="edb5c-444">**parámetro**: la dirección de la canalización:</span><span class="sxs-lookup"><span data-stu-id="edb5c-444">**parameter**: The pipe direction:</span></span>

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a><span data-ttu-id="edb5c-445">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-445">Return Value</span></span>

- <span data-ttu-id="edb5c-446">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-446">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="edb5c-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Dirección de canalización no válida.</span><span class="sxs-lookup"><span data-stu-id="edb5c-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Invalid pipe direction.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-448">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-448">Example</span></span>

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a><span data-ttu-id="edb5c-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="edb5c-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>

<span data-ttu-id="edb5c-450">Ejecutar el inicio de la transmisión de IOCTL en la interfaz CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="edb5c-450">Perform IOCTL Transmission Start on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-451">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-451">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="edb5c-452">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-452">Description</span></span>

<span data-ttu-id="edb5c-453">Se llama a esta función cuando una aplicación desea usar la transmisión con devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="edb5c-453">This function is called when an application wants to use transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-454">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-454">Parameters</span></span>

- <span data-ttu-id="edb5c-455">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-455">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="edb5c-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>
- <span data-ttu-id="edb5c-457">**parámetro**: puntero a la estructura del parámetro de inicio de transmisión:</span><span class="sxs-lookup"><span data-stu-id="edb5c-457">**parameter**: Pointer to the Start Transmission parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="edb5c-458">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-458">Return Value</span></span>

- <span data-ttu-id="edb5c-459">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-459">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="edb5c-460">**UX_ERROR** (0xFF) La transmisión ya se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="edb5c-460">**UX_ERROR** (0xFF) Transmission already started.</span></span>
- <span data-ttu-id="edb5c-461">**UX_MEMORY_INSUFFICIENT** (0x12) Error en una asignación de memoria.</span><span class="sxs-lookup"><span data-stu-id="edb5c-461">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-462">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-462">Example</span></span>

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a><span data-ttu-id="edb5c-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="edb5c-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>

<span data-ttu-id="edb5c-464">Ejecutar la detención de la transmisión de IOCTL en la interfaz CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="edb5c-464">Perform IOCTL Transmission Stop on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-465">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-465">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="edb5c-466">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-466">Description</span></span>

<span data-ttu-id="edb5c-467">Se llama a esta función cuando una aplicación desea dejar de usar la transmisión con devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="edb5c-467">This function is called when an application wants to stop using transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-468">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-468">Parameters</span></span>

- <span data-ttu-id="edb5c-469">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-469">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span><span class="sxs-lookup"><span data-stu-id="edb5c-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span></span>
- <span data-ttu-id="edb5c-471">**parameter**: no se usa.</span><span class="sxs-lookup"><span data-stu-id="edb5c-471">**parameter**: Not used</span></span>

### <a name="return-value"></a><span data-ttu-id="edb5c-472">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-472">Return Value</span></span>

- <span data-ttu-id="edb5c-473">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-473">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="edb5c-474">**UX_ERROR** (0xFF) no hay ninguna transmisión en curso.</span><span class="sxs-lookup"><span data-stu-id="edb5c-474">**UX_ERROR** (0xFF) No ongoing transmission.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-475">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-475">Example</span></span>

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a><span data-ttu-id="edb5c-476">ux_device_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="edb5c-476">ux_device_class_cdc_acm_read</span></span>

<span data-ttu-id="edb5c-477">Leer la canalización CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="edb5c-477">Read from CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-478">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-478">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="edb5c-479">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-479">Description</span></span>

<span data-ttu-id="edb5c-480">Se llama a esta función cuando una aplicación necesita leer la canalización de datos OUT (OUT desde el host, IN desde el dispositivo).</span><span class="sxs-lookup"><span data-stu-id="edb5c-480">This function is called when an application needs to read from the OUT data pipe (OUT from the host, IN from the device).</span></span> <span data-ttu-id="edb5c-481">Está bloqueando.</span><span class="sxs-lookup"><span data-stu-id="edb5c-481">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-482">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-482">Parameters</span></span>

- <span data-ttu-id="edb5c-483">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-483">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-484">**bufer**: dirección del búfer donde se almacenarán los datos.</span><span class="sxs-lookup"><span data-stu-id="edb5c-484">**buffer**: Buffer address where data will be stored.</span></span>
- <span data-ttu-id="edb5c-485">**requested_length**: la longitud máxima que se espera.</span><span class="sxs-lookup"><span data-stu-id="edb5c-485">**requested_length**: The maximum length we expect.</span></span>
- <span data-ttu-id="edb5c-486">**actual_length**: la longitud devuelta en el búfer.</span><span class="sxs-lookup"><span data-stu-id="edb5c-486">**actual_length**: The length returned into the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="edb5c-487">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-487">Return Value</span></span>

- <span data-ttu-id="edb5c-488">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-488">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="edb5c-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) El dispositivo ya no está en el estado configurado.</span><span class="sxs-lookup"><span data-stu-id="edb5c-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="edb5c-490">**UX_TRANSFER_NO_ANSWER** (0x22) No hay respuesta del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-490">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="edb5c-491">Es probable que el dispositivo se desconectase mientras estaba pendiente la transferencia.</span><span class="sxs-lookup"><span data-stu-id="edb5c-491">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-492">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-492">Example</span></span>

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a><span data-ttu-id="edb5c-493">ux_device_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="edb5c-493">ux_device_class_cdc_acm_write</span></span>

<span data-ttu-id="edb5c-494">Escribir en una canalización CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="edb5c-494">Write to a CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-495">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-495">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="edb5c-496">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-496">Description</span></span>

<span data-ttu-id="edb5c-497">Se llama a esta función cuando una aplicación necesita escribir en la canalización de datos IN (IN desde el host, OUT desde el dispositivo).</span><span class="sxs-lookup"><span data-stu-id="edb5c-497">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="edb5c-498">Está bloqueando.</span><span class="sxs-lookup"><span data-stu-id="edb5c-498">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-499">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-499">Parameters</span></span>

- <span data-ttu-id="edb5c-500">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-500">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-501">**bufer**: dirección del búfer donde se almacenan los datos.</span><span class="sxs-lookup"><span data-stu-id="edb5c-501">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="edb5c-502">**requested_length**: la longitud del búfer que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="edb5c-502">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="edb5c-503">**actual_length**: la longitud devuelta en el búfer después de realizar la escritura.</span><span class="sxs-lookup"><span data-stu-id="edb5c-503">**actual_length**: The length returned into the buffer after write is performed.</span></span>

### <a name="return-value"></a><span data-ttu-id="edb5c-504">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-504">Return Value</span></span>
- <span data-ttu-id="edb5c-505">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-505">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="edb5c-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) El dispositivo ya no está en el estado configurado.</span><span class="sxs-lookup"><span data-stu-id="edb5c-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="edb5c-507">**UX_TRANSFER_NO_ANSWER** (0x22) No hay respuesta del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-507">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="edb5c-508">Es probable que el dispositivo se desconectase mientras estaba pendiente la transferencia.</span><span class="sxs-lookup"><span data-stu-id="edb5c-508">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-509">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-509">Example</span></span>

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a><span data-ttu-id="edb5c-510">ux_device_class_cdc_acm_write_with_callback</span><span class="sxs-lookup"><span data-stu-id="edb5c-510">ux_device_class_cdc_acm_write_with_callback</span></span>

<span data-ttu-id="edb5c-511">Escribir en una canalización CDC-ACM con devolución de llamada</span><span class="sxs-lookup"><span data-stu-id="edb5c-511">Writing to a CDC-ACM pipe with callback</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-512">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-512">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a><span data-ttu-id="edb5c-513">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-513">Description</span></span>

<span data-ttu-id="edb5c-514">Se llama a esta función cuando una aplicación necesita escribir en la canalización de datos IN (IN desde el host, OUT desde el dispositivo).</span><span class="sxs-lookup"><span data-stu-id="edb5c-514">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="edb5c-515">Esta función no es de bloqueo y la finalización se realizará a través de una devolución de llamada establecida en UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span><span class="sxs-lookup"><span data-stu-id="edb5c-515">This function is non-blocking and the completion will be done through a callback set in UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-516">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-516">Parameters</span></span>

- <span data-ttu-id="edb5c-517">**cdc_acm**: puntero a la instancia de la clase CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-517">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="edb5c-518">**bufer**: dirección del búfer donde se almacenan los datos.</span><span class="sxs-lookup"><span data-stu-id="edb5c-518">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="edb5c-519">**requested_length**: la longitud del búfer que se va a escribir.</span><span class="sxs-lookup"><span data-stu-id="edb5c-519">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="edb5c-520">**actual_length**: la longitud devuelta en el búfer después de realizar la escritura.</span><span class="sxs-lookup"><span data-stu-id="edb5c-520">**actual_length**: The length returned into the buffer after write is performed</span></span>

### <a name="return-value"></a><span data-ttu-id="edb5c-521">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-521">Return Value</span></span>

- <span data-ttu-id="edb5c-522">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-522">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="edb5c-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) El dispositivo ya no está en el estado configurado.</span><span class="sxs-lookup"><span data-stu-id="edb5c-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="edb5c-524">**UX_TRANSFER_NO_ANSWER** (0x22) No hay respuesta del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-524">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="edb5c-525">Es probable que el dispositivo se desconectase mientras estaba pendiente la transferencia.</span><span class="sxs-lookup"><span data-stu-id="edb5c-525">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-526">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-526">Example</span></span>

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a><span data-ttu-id="edb5c-527">Clase CDC-ECM de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="edb5c-527">USB Device CDC-ECM Class</span></span>

<span data-ttu-id="edb5c-528">La clase CDC-ECM del dispositivo USB permite que un sistema host USB se comunique con el dispositivo como un dispositivo Ethernet.</span><span class="sxs-lookup"><span data-stu-id="edb5c-528">The USB device CDC-ECM class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="edb5c-529">Esta clase se basa en el estándar USB y es un subconjunto del estándar CDC.</span><span class="sxs-lookup"><span data-stu-id="edb5c-529">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="edb5c-530">Un marco de dispositivos compatible con CDC-ACM debe declararse en la pila de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="edb5c-530">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="edb5c-531">A continuación, se muestra un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-531">An example is found here below.</span></span>

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

<span data-ttu-id="edb5c-532">La clase CDC-ECM usa un enfoque de descriptor de dispositivos muy similar para CDC-ACM, y también requiere un descriptor IAD.</span><span class="sxs-lookup"><span data-stu-id="edb5c-532">The CDC-ECM class uses a very similar device descriptor approach to the CDC-ACM and also requires an IAD descriptor.</span></span> <span data-ttu-id="edb5c-533">Vea la clase CDC-ACM para la definición.</span><span class="sxs-lookup"><span data-stu-id="edb5c-533">See the CDC-ACM class for definition.</span></span>

<span data-ttu-id="edb5c-534">Además del marco normal del dispositivos, CDC-ECM requiere descriptores de cadena especiales.</span><span class="sxs-lookup"><span data-stu-id="edb5c-534">In addition to the regular device framework, the CDC-ECM requires special string descriptors.</span></span> <span data-ttu-id="edb5c-535">A continuación encontrará un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-535">An example is given below.</span></span>

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

<span data-ttu-id="edb5c-536">La clase CDC-ECM usa el descriptor de cadena de dirección MAC para responder a las consultas de host de en qué dirección MAC responde el dispositivo en el protocolo TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="edb5c-536">The MAC address string descriptor is used by the CDC-ECM class to reply to the host queries as to what MAC address the device is answering to at the TCP/IP protocol.</span></span> <span data-ttu-id="edb5c-537">Se puede establecer en la elección del dispositivo, pero debe definirse aquí.</span><span class="sxs-lookup"><span data-stu-id="edb5c-537">It can be set to the device choice but must be defined here.</span></span>

<span data-ttu-id="edb5c-538">La inicialización de la clase CDC-ECM es como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="edb5c-538">The initialization of the CDC-ECM class is as follows.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

<span data-ttu-id="edb5c-539">La inicialización de esta clase espera la misma devolución de llamada de función para la activación y la desactivación, aunque aquí se establece en NULL para que no se realice ninguna devolución de llamada.</span><span class="sxs-lookup"><span data-stu-id="edb5c-539">The initialization of this class expects the same function callback for activation and deactivation, although here as an exercise they are set to NULL so that no callback is performed.</span></span>

<span data-ttu-id="edb5c-540">Los parámetros siguientes son para la definición de los id. de nodo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-540">The next parameters are for the definition of the node IDs.</span></span> <span data-ttu-id="edb5c-541">Son necesarios dos nodos para CDC-ECM, un nodo local y un nodo remoto.</span><span class="sxs-lookup"><span data-stu-id="edb5c-541">2 Nodes are necessary for the CDC-ECM, a local node and a remote node.</span></span> <span data-ttu-id="edb5c-542">El nodo local especifica la dirección MAC del dispositivo, mientras que el nodo remoto especifica la dirección MAC del host.</span><span class="sxs-lookup"><span data-stu-id="edb5c-542">The local node specifies the MAC address of the device, while the remote node specifies the MAC address of the host.</span></span> <span data-ttu-id="edb5c-543">El nodo remoto debe ser el mismo que el declarado en el descriptor de cadena del marco de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-543">The remote node must be the same one as the one declared in the device framework string descriptor.</span></span>

<span data-ttu-id="edb5c-544">La clase CDC-ECM tiene API integradas para transferir datos de ambas maneras, pero están ocultas en la aplicación, ya que la aplicación de usuario se comunicará con el dispositivo USB Ethernet a través de NetX.</span><span class="sxs-lookup"><span data-stu-id="edb5c-544">The CDC-ECM class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="edb5c-545">La clase USBX CDC-ECM está estrechamente relacionada con la pila de red NetX de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="edb5c-545">The USBX CDC-ECM class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="edb5c-546">Una aplicación que use las clases NetX y USBX CDC-ECM activará la pila de red de NetX de la manera habitual, pero además necesitará activar la pila de red USB tal como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="edb5c-546">An application using both NetX and USBX CDC-ECM class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="edb5c-547">La pila de red USB debe activarse una sola vez y no es específica de CDCECM, pero es necesaria para cualquier clase USB que requiera los servicios de NetX.</span><span class="sxs-lookup"><span data-stu-id="edb5c-547">The USB network stack needs to be activated only once and is not specific to CDCECM but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="edb5c-548">Los hosts de MAC OS y Linux reconocerán la clase CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="edb5c-548">The CDC-ECM class will be recognized by MAC OS and Linux hosts.</span></span> <span data-ttu-id="edb5c-549">Pero no hay ningún controlador proporcionado por Microsoft Windows para reconocer CDC-ECM de forma nativa.</span><span class="sxs-lookup"><span data-stu-id="edb5c-549">But there is no driver supplied by Microsoft Windows to recognize CDC-ECM natively.</span></span> <span data-ttu-id="edb5c-550">Algunos productos comerciales existen para las plataformas de Windows y suministran su propio archivo .inf.</span><span class="sxs-lookup"><span data-stu-id="edb5c-550">Some commercial products do exist for Windows platforms and they supply their own .inf file.</span></span> <span data-ttu-id="edb5c-551">Este archivo deberá modificarse de la misma forma que la plantilla inf de CDC-ACM para que coincida con el PID/VID del dispositivo de red USB.</span><span class="sxs-lookup"><span data-stu-id="edb5c-551">This file will need to be modified the same way as the CDC-ACM inf template to match the PID/VID of the USB network device.</span></span>

## <a name="usb-device-hid-class"></a><span data-ttu-id="edb5c-552">Clase HID del dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="edb5c-552">USB Device HID Class</span></span>

<span data-ttu-id="edb5c-553">La clase HID del dispositivo USB permite que un sistema host USB se conecte a un dispositivo HID con capacidades específicas del cliente HID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-553">The USB device HID class allows for a USB host system to connect to a HID device with specific HID client capabilities.</span></span>

<span data-ttu-id="edb5c-554">La clase de dispositivo USBX HID es relativamente sencilla en comparación con el lado host.</span><span class="sxs-lookup"><span data-stu-id="edb5c-554">USBX HID device class is relatively simple compared to the host side.</span></span> <span data-ttu-id="edb5c-555">Está estrechamente vinculada al comportamiento del dispositivo y su descriptor HID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-555">It is closely tied to the behavior of the device and its HID descriptor.</span></span>

<span data-ttu-id="edb5c-556">Cualquier cliente HID requiere en primer lugar definir un marco de dispositivo HID como en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-556">Any HID client requires first to define a HID device framework as the example below.</span></span>

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

<span data-ttu-id="edb5c-557">El marco HID contiene un descriptor de interfaz que describe la clase HID y la subclase de dispositivo HID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-557">The HID framework contains an interface descriptor that describes the HID class and the HID device subclass.</span></span> <span data-ttu-id="edb5c-558">La interfaz HID puede ser una clase independiente o parte de un dispositivo compuesto.</span><span class="sxs-lookup"><span data-stu-id="edb5c-558">The HID interface can be a standalone class or part of a composite device.</span></span>

<span data-ttu-id="edb5c-559">Actualmente, la clase USBX HID no admite varios id. de informe, ya que la mayoría de las aplicaciones solo requieren un id. (id. cero).</span><span class="sxs-lookup"><span data-stu-id="edb5c-559">Currently, the USBX HID class does not support multiple report IDs, as most applications only require one ID (ID zero).</span></span> <span data-ttu-id="edb5c-560">Si le interesa la característica de varios id. de informe, póngase en contacto con nosotros.</span><span class="sxs-lookup"><span data-stu-id="edb5c-560">If multiple report IDs is a feature you are interested in, please contact us.</span></span>

<span data-ttu-id="edb5c-561">La inicialización de la clase HID es como sigue, empleando un teclado USB como ejemplo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-561">The initialization of the HID class is as follow, using a USB keyboard as an example.</span></span>

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

<span data-ttu-id="edb5c-562">La aplicación debe pasar a la clase HID un descriptor de informe HID y su longitud.</span><span class="sxs-lookup"><span data-stu-id="edb5c-562">The application needs to pass to the HID class a HID report descriptor and its length.</span></span> <span data-ttu-id="edb5c-563">El descriptor de informe es una colección de elementos que describen el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-563">The report descriptor is a collection of items that describe the device.</span></span> <span data-ttu-id="edb5c-564">Para más información sobre la gramática de HID, consulte la especificación de la clase HID USB.</span><span class="sxs-lookup"><span data-stu-id="edb5c-564">For more information on the HID grammar refer to the HID USB class specification.</span></span>

<span data-ttu-id="edb5c-565">Además del descriptor de informe, la aplicación pasa una devolución de llamada cuando se produce un evento de HID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-565">In addition to the report descriptor, the application passes a call back when a HID event happens.</span></span>

<span data-ttu-id="edb5c-566">La clase USBX HID admite los siguientes comandos HID estándar desde el host.</span><span class="sxs-lookup"><span data-stu-id="edb5c-566">The USBX HID class supports the following standard HID commands from the host.</span></span>

| <span data-ttu-id="edb5c-567">Nombre de comando</span><span class="sxs-lookup"><span data-stu-id="edb5c-567">Command name</span></span>                             | <span data-ttu-id="edb5c-568">Value</span><span class="sxs-lookup"><span data-stu-id="edb5c-568">Value</span></span> | <span data-ttu-id="edb5c-569">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-569">Description</span></span>                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| <span data-ttu-id="edb5c-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span><span class="sxs-lookup"><span data-stu-id="edb5c-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span></span>   | <span data-ttu-id="edb5c-571">0x01</span><span class="sxs-lookup"><span data-stu-id="edb5c-571">0x01</span></span>  | <span data-ttu-id="edb5c-572">Obtención de un informe del dispositivo</span><span class="sxs-lookup"><span data-stu-id="edb5c-572">Get a report from the device</span></span>                     |
| <span data-ttu-id="edb5c-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span><span class="sxs-lookup"><span data-stu-id="edb5c-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span></span>     | <span data-ttu-id="edb5c-574">0x02</span><span class="sxs-lookup"><span data-stu-id="edb5c-574">0x02</span></span>  | <span data-ttu-id="edb5c-575">Obtención de la frecuencia de inactividad del punto de conexión de interrupción</span><span class="sxs-lookup"><span data-stu-id="edb5c-575">Get the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="edb5c-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="edb5c-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span></span> | <span data-ttu-id="edb5c-577">0x03</span><span class="sxs-lookup"><span data-stu-id="edb5c-577">0x03</span></span>  | <span data-ttu-id="edb5c-578">Obtención del protocolo que se ejecuta en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="edb5c-578">Get the protocol running on the device</span></span>           |
| <span data-ttu-id="edb5c-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span><span class="sxs-lookup"><span data-stu-id="edb5c-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span></span>   | <span data-ttu-id="edb5c-580">0x09</span><span class="sxs-lookup"><span data-stu-id="edb5c-580">0x09</span></span>  | <span data-ttu-id="edb5c-581">Establecimiento de un informe en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="edb5c-581">Set a report to the device</span></span>                       |
| <span data-ttu-id="edb5c-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span><span class="sxs-lookup"><span data-stu-id="edb5c-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span></span>     | <span data-ttu-id="edb5c-583">0x0a</span><span class="sxs-lookup"><span data-stu-id="edb5c-583">0x0a</span></span>  | <span data-ttu-id="edb5c-584">Establecimiento de la frecuencia de inactividad del punto de conexión de interrupción</span><span class="sxs-lookup"><span data-stu-id="edb5c-584">Set the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="edb5c-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="edb5c-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span></span> | <span data-ttu-id="edb5c-586">0x0b</span><span class="sxs-lookup"><span data-stu-id="edb5c-586">0x0b</span></span>  | <span data-ttu-id="edb5c-587">Obtención del protocolo que se ejecuta en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="edb5c-587">Get the protocol running on the device</span></span>           |

<span data-ttu-id="edb5c-588">Los comandos de obtención y establecimiento de informes son los que HID usa más para transferir datos entre el host y el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="edb5c-588">The Get and Set report are the most commonly used commands by HID to transfer data back and forth between the host and the device.</span></span> <span data-ttu-id="edb5c-589">Normalmente, el host envía datos en el punto de conexión de control, pero puede recibir datos en el punto de conexión de interrupción o mediante la emisión de un comando GET_REPORT para capturar los datos del punto de conexión de control.</span><span class="sxs-lookup"><span data-stu-id="edb5c-589">Most commonly the host sends data on the control endpoint but can receive data either on the interrupt endpoint or by issuing a GET_REPORT command to fetch the data on the control endpoint.</span></span>

<span data-ttu-id="edb5c-590">La clase HID puede devolver datos al host en el punto de conexión de interrupción mediante el uso de la función ux_device_class_hid_event_set.</span><span class="sxs-lookup"><span data-stu-id="edb5c-590">The HID class can send data back to the host on the interrupt endpoint by using the ux_device_class_hid_event_set function.</span></span>

### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="edb5c-591">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="edb5c-591">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="edb5c-592">Establecimiento de un evento en la clase HID</span><span class="sxs-lookup"><span data-stu-id="edb5c-592">Setting an event to the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-593">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-593">Prototype</span></span>

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="edb5c-594">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-594">Description</span></span>

<span data-ttu-id="edb5c-595">Se llama a esta función cuando una aplicación necesita enviar un evento de HID de nuevo al host.</span><span class="sxs-lookup"><span data-stu-id="edb5c-595">This function is called when an application needs to send a HID event back to the host.</span></span> <span data-ttu-id="edb5c-596">La función no es de bloqueo, simplemente coloca el informe en una cola circular y vuelve a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="edb5c-596">The function is not blocking, it merely puts the report into a circular queue and returns to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-597">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-597">Parameters</span></span>

- <span data-ttu-id="edb5c-598">**hid** puntero a la instancia de la clase HID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-598">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="edb5c-599">**hid_event**: puntero a la estructura del evento de HID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-599">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="return-value"></a><span data-ttu-id="edb5c-600">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="edb5c-600">Return Value</span></span>

- <span data-ttu-id="edb5c-601">**UX_SUCCESS** (0x00) Esta operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="edb5c-601">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="edb5c-602">**UX_ERROR** (0xFF) Error de no hay espacio disponible en la cola circular.</span><span class="sxs-lookup"><span data-stu-id="edb5c-602">**UX_ERROR** (0xFF) Error no space available in circular queue.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-603">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-603">Example</span></span>

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

<span data-ttu-id="edb5c-604">La devolución de llamada definida en la inicialización de la clase HID realiza lo opuesto al envío de un evento.</span><span class="sxs-lookup"><span data-stu-id="edb5c-604">The callback defined at the initialization of the HID class performs the opposite of sending an event.</span></span> <span data-ttu-id="edb5c-605">Obtiene como entrada el evento enviado por el host.</span><span class="sxs-lookup"><span data-stu-id="edb5c-605">It gets as input the event sent by the host.</span></span> <span data-ttu-id="edb5c-606">El prototipo de la devolución de llamada es como sigue.</span><span class="sxs-lookup"><span data-stu-id="edb5c-606">The prototype of the callback is as follows.</span></span>

### <a name="hid_callback"></a><span data-ttu-id="edb5c-607">hid_callback</span><span class="sxs-lookup"><span data-stu-id="edb5c-607">hid_callback</span></span>

<span data-ttu-id="edb5c-608">Obtener un evento de la clase HID</span><span class="sxs-lookup"><span data-stu-id="edb5c-608">Getting an event from the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="edb5c-609">Prototipo</span><span class="sxs-lookup"><span data-stu-id="edb5c-609">Prototype</span></span>

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="edb5c-610">Descripción</span><span class="sxs-lookup"><span data-stu-id="edb5c-610">Description</span></span>

<span data-ttu-id="edb5c-611">Se llama a esta función cuando el host envía un informe HID a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="edb5c-611">This function is called when the host sends a HID report to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="edb5c-612">Parámetros</span><span class="sxs-lookup"><span data-stu-id="edb5c-612">Parameters</span></span>

- <span data-ttu-id="edb5c-613">**hid** puntero a la instancia de la clase HID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-613">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="edb5c-614">**hid_event**: puntero a la estructura del evento de HID.</span><span class="sxs-lookup"><span data-stu-id="edb5c-614">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="example"></a><span data-ttu-id="edb5c-615">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="edb5c-615">Example</span></span>

<span data-ttu-id="edb5c-616">En el ejemplo siguiente se muestra cómo interpretar un evento para un teclado HID:</span><span class="sxs-lookup"><span data-stu-id="edb5c-616">The following example shows how to interpret an event for a HID keyboard:</span></span>

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
