---
title: 'Capítulo 5: Controladores de dispositivo para Azure RTOS ThreadX SMP'
description: Este capítulo contiene una descripción de los controladores de dispositivo de Azure RTOS ThreadX SMP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: acfb54a25cc8bc27b7d0aaeff48956529d90c9e1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816065"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a><span data-ttu-id="b40fb-103">Capítulo 5: Controladores de dispositivo para Azure RTOS ThreadX SMP</span><span class="sxs-lookup"><span data-stu-id="b40fb-103">Chapter 5 - Device Drivers for Azure RTOS ThreadX SMP</span></span>

<span data-ttu-id="b40fb-104">Este capítulo contiene una descripción de los controladores de dispositivo de Azure RTOS ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="b40fb-104">This chapter contains a description of device drivers for Azure RTOS ThreadX SMP.</span></span> <span data-ttu-id="b40fb-105">La información que se presenta en este capítulo está diseñada para ayudar a los desarrolladores a escribir controladores específicos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b40fb-105">The information presented in this chapter is designed to help developers write application specific drivers.</span></span> 

## <a name="device-driver-introduction"></a><span data-ttu-id="b40fb-106">Introducción al controlador de dispositivo</span><span class="sxs-lookup"><span data-stu-id="b40fb-106">Device Driver Introduction</span></span>

<span data-ttu-id="b40fb-107">La comunicación con el entorno externo es un componente importante de la mayoría de las aplicaciones insertadas.</span><span class="sxs-lookup"><span data-stu-id="b40fb-107">Communication with the external environment is an important component of most embedded applications.</span></span> <span data-ttu-id="b40fb-108">Esta comunicación se realiza a través de dispositivos de hardware que son accesibles para el software de la aplicación insertada.</span><span class="sxs-lookup"><span data-stu-id="b40fb-108">This communication is accomplished through hardware devices that are accessible to the embedded application software.</span></span> <span data-ttu-id="b40fb-109">Los componentes de software responsables de administrar dichos dispositivos se denominan normalmente *controladores de dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="b40fb-109">The software components responsible for managing such devices are commonly called *Device Drivers*.</span></span>

<span data-ttu-id="b40fb-110">Los controladores de dispositivo de los sistemas en tiempo real integrados dependen de las aplicaciones de forma inherente.</span><span class="sxs-lookup"><span data-stu-id="b40fb-110">Device drivers in embedded, real-time systems are inherently application dependent.</span></span> <span data-ttu-id="b40fb-111">Esto es así por dos motivos principales: la gran diversidad del hardware de destino y los requisitos de rendimiento igualmente amplios que afectan a las aplicaciones en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="b40fb-111">This is true for two principal reasons: the vast diversity of target hardware and the equally vast performance requirements imposed on real-time applications.</span></span> <span data-ttu-id="b40fb-112">Por esta razón, es prácticamente imposible proporcionar un conjunto común de controladores que cumplan los requisitos de cada aplicación.</span><span class="sxs-lookup"><span data-stu-id="b40fb-112">Because of this, it is virtually impossible to provide a common set of drivers that will meet the requirements of every application.</span></span> <span data-ttu-id="b40fb-113">La información de este capítulo, por tanto, se ha diseñado para ayudar a los usuarios a personalizar los controladores de dispositivo de ThreadX SMP *comerciales* y a escribir sus propios controladores específicos.</span><span class="sxs-lookup"><span data-stu-id="b40fb-113">For these reasons, the information in this chapter is designed to help users customize *off-the-shelf* ThreadX SMP device drivers and write their own specific drivers.</span></span>

## <a name="driver-functions"></a><span data-ttu-id="b40fb-114">Funciones de controlador</span><span class="sxs-lookup"><span data-stu-id="b40fb-114">Driver Functions</span></span>

<span data-ttu-id="b40fb-115">Los controladores de dispositivo de ThreadX SMP se componen de ocho áreas funcionales básicas, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="b40fb-115">ThreadX SMP device drivers are composed of eight basic functional areas, as follows:</span></span>

- <span data-ttu-id="b40fb-116">**Inicialización del controlador**</span><span class="sxs-lookup"><span data-stu-id="b40fb-116">**Driver Initialization**</span></span>
- <span data-ttu-id="b40fb-117">**Control del controlador**</span><span class="sxs-lookup"><span data-stu-id="b40fb-117">**Driver Control**</span></span>
- <span data-ttu-id="b40fb-118">**Acceso al controlador**</span><span class="sxs-lookup"><span data-stu-id="b40fb-118">**Driver Access**</span></span>
- <span data-ttu-id="b40fb-119">**Entrada al controlador**</span><span class="sxs-lookup"><span data-stu-id="b40fb-119">**Driver Input**</span></span>
- <span data-ttu-id="b40fb-120">**Salida del controlador**</span><span class="sxs-lookup"><span data-stu-id="b40fb-120">**Driver Output**</span></span>
- <span data-ttu-id="b40fb-121">**Interrupciones del controlador**</span><span class="sxs-lookup"><span data-stu-id="b40fb-121">**Driver Interrupts**</span></span>
- <span data-ttu-id="b40fb-122">**Estado del controlador**</span><span class="sxs-lookup"><span data-stu-id="b40fb-122">**Driver Status**</span></span>
- <span data-ttu-id="b40fb-123">**Finalización del controlador**</span><span class="sxs-lookup"><span data-stu-id="b40fb-123">**Driver Termination**</span></span>

<span data-ttu-id="b40fb-124">Con la excepción de la inicialización, las demás áreas funcionales del controlador son opcionales.</span><span class="sxs-lookup"><span data-stu-id="b40fb-124">With the exception of initialization, each driver functional area is optional.</span></span> <span data-ttu-id="b40fb-125">Además, el procesamiento exacto de cada área es específico del controlador de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-125">Furthermore, the exact processing in each area is specific to the device driver.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="b40fb-126">Inicialización del controlador</span><span class="sxs-lookup"><span data-stu-id="b40fb-126">Driver Initialization</span></span> 
<span data-ttu-id="b40fb-127">Esta área funcional es responsable de la inicialización del dispositivo real de hardware y de las estructuras de datos internas del controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-127">This functional area is responsible for initialization of the actual hardware device and the internal data structures of the driver.</span></span> <span data-ttu-id="b40fb-128">No se puede llamar a otros servicios del controlador mientras no se complete la inicialización.</span><span class="sxs-lookup"><span data-stu-id="b40fb-128">Calling other driver services is not allowed until initialization is complete.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b40fb-129">Normalmente, se llama al componente de la función de inicialización del controlador desde la función **tx_application_define** o desde un subproceso de inicialización.</span><span class="sxs-lookup"><span data-stu-id="b40fb-129">The driver’s initialization function component is typically called from the **tx_application_define** function or from an initialization thread.</span></span>

### <a name="driver-control"></a><span data-ttu-id="b40fb-130">Control del controlador</span><span class="sxs-lookup"><span data-stu-id="b40fb-130">Driver Control</span></span> 
<span data-ttu-id="b40fb-131">Una vez que el controlador se inicializa y está listo para su funcionamiento, esta área funcional es responsable del control en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="b40fb-131">After the driver is initialized and ready for operation, this functional area is responsible for run-time control.</span></span> <span data-ttu-id="b40fb-132">Normalmente, este control consiste en realizar cambios en el dispositivo de hardware subyacente.</span><span class="sxs-lookup"><span data-stu-id="b40fb-132">Typically, run-time control consists of making changes to the underlying hardware device.</span></span> <span data-ttu-id="b40fb-133">Entre los ejemplos se incluyen el cambio de la velocidad en baudios de un dispositivo serie o la búsqueda de un nuevo sector en un disco.</span><span class="sxs-lookup"><span data-stu-id="b40fb-133">Examples include changing the baud rate of a serial device or seeking a new sector on a disk.</span></span>

### <a name="driver-access"></a><span data-ttu-id="b40fb-134">Acceso al controlador</span><span class="sxs-lookup"><span data-stu-id="b40fb-134">Driver Access</span></span> 
<span data-ttu-id="b40fb-135">A algunos controladores de dispositivo solo se les llama desde un único subproceso de aplicación.</span><span class="sxs-lookup"><span data-stu-id="b40fb-135">Some device drivers are called only from a single application thread.</span></span> <span data-ttu-id="b40fb-136">En tales casos, no es necesaria esta área funcional.</span><span class="sxs-lookup"><span data-stu-id="b40fb-136">In such cases, this functional area is not needed.</span></span> <span data-ttu-id="b40fb-137">Sin embargo, en las aplicaciones en las que varios subprocesos necesitan acceso simultáneo al controlador, su interacción debe controlarse mediante la adición de recursos de asignación y liberación en el controlador de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-137">However, in applications where multiple threads need simultaneous driver access, their interaction must be controlled by adding assign/ release facilities in the device driver.</span></span> <span data-ttu-id="b40fb-138">Como alternativa, la aplicación puede usar un semáforo para administrar el acceso al controlador y evitar una sobrecarga y una complicación adicionales dentro del controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-138">Alternatively, the application may use a semaphore to control driver access and avoid extra overhead and complication inside the driver.</span></span> 

### <a name="driver-input"></a><span data-ttu-id="b40fb-139">Entrada al controlador</span><span class="sxs-lookup"><span data-stu-id="b40fb-139">Driver Input</span></span> 
<span data-ttu-id="b40fb-140">Esta área funcional es responsable de todas las entradas al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-140">This functional area is responsible for all device input.</span></span> <span data-ttu-id="b40fb-141">Los principales problemas asociados a la entrada al controlador suelen tener que ver con el modo en que la entrada se almacena en el búfer y cómo esperan los subprocesos esa entrada.</span><span class="sxs-lookup"><span data-stu-id="b40fb-141">The principal issues associated with driver input usually involve how the input is buffered and how threads wait for such input.</span></span> 

### <a name="driver-output"></a><span data-ttu-id="b40fb-142">Salida del controlador</span><span class="sxs-lookup"><span data-stu-id="b40fb-142">Driver Output</span></span> 
<span data-ttu-id="b40fb-143">Esta área funcional es responsable de todas las salidas del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-143">This functional area is responsible for all device output.</span></span> <span data-ttu-id="b40fb-144">Los principales problemas asociados con la salida del controlador suelen tener que ver con el modo en que la salida se almacena en el búfer y cómo esperan los subprocesos para realizar la salida.</span><span class="sxs-lookup"><span data-stu-id="b40fb-144">The principal issues associated with driver output usually involve how the output is buffered and how threads wait to perform output.</span></span> 

### <a name="driver-interrupts"></a><span data-ttu-id="b40fb-145">Interrupciones del controlador</span><span class="sxs-lookup"><span data-stu-id="b40fb-145">Driver Interrupts</span></span> 
<span data-ttu-id="b40fb-146">La mayoría de los sistemas en tiempo real se basan en interrupciones de hardware para notificar al controlador los eventos de entrada, salida, control y error del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-146">Most real-time systems rely on hardware interrupts to notify the driver of device input, output, control, and error events.</span></span> <span data-ttu-id="b40fb-147">Las interrupciones proporcionan un tiempo de respuesta garantizado para estos eventos externos.</span><span class="sxs-lookup"><span data-stu-id="b40fb-147">Interrupts provide a guaranteed response time to such external events.</span></span> <span data-ttu-id="b40fb-148">En lugar de las interrupciones, el software del controlador puede comprobar periódicamente el hardware externo para detectar esos eventos.</span><span class="sxs-lookup"><span data-stu-id="b40fb-148">Instead of interrupts, the driver software may periodically check the external hardware for such events.</span></span> <span data-ttu-id="b40fb-149">Esta técnica se conoce como *sondeo*.</span><span class="sxs-lookup"><span data-stu-id="b40fb-149">This technique is called *polling*.</span></span> <span data-ttu-id="b40fb-150">El sondeo no está tan próximo al tiempo real como las interrupciones, pero puede tener sentido en algunas aplicaciones que tampoco lo están.</span><span class="sxs-lookup"><span data-stu-id="b40fb-150">It is less real-time than interrupts, but polling may make sense for some less real-time applications.</span></span> 

### <a name="driver-status"></a><span data-ttu-id="b40fb-151">Estado del controlador</span><span class="sxs-lookup"><span data-stu-id="b40fb-151">Driver Status</span></span> 
<span data-ttu-id="b40fb-152">Esta área funcional es responsable de proporcionar el estado en tiempo de ejecución y las estadísticas asociadas al funcionamiento del controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-152">This function area is responsible for providing runtime status and statistics associated with the driver operation.</span></span> <span data-ttu-id="b40fb-153">Por lo general, la información administrada por esta área funcional incluye lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b40fb-153">Information managed by this function area typically includes the following:</span></span> 
- <span data-ttu-id="b40fb-154">Estado actual del dispositivo</span><span class="sxs-lookup"><span data-stu-id="b40fb-154">Current device status</span></span>
- <span data-ttu-id="b40fb-155">Bytes de entrada</span><span class="sxs-lookup"><span data-stu-id="b40fb-155">Input bytes</span></span>
- <span data-ttu-id="b40fb-156">Bytes de salida</span><span class="sxs-lookup"><span data-stu-id="b40fb-156">Output bytes</span></span>
- <span data-ttu-id="b40fb-157">Recuentos de errores de dispositivos</span><span class="sxs-lookup"><span data-stu-id="b40fb-157">Device error counts</span></span>

### <a name="driver-termination"></a><span data-ttu-id="b40fb-158">Finalización del controlador</span><span class="sxs-lookup"><span data-stu-id="b40fb-158">Driver Termination</span></span> 
<span data-ttu-id="b40fb-159">Esta área funcional es opcional.</span><span class="sxs-lookup"><span data-stu-id="b40fb-159">This functional area is optional.</span></span> <span data-ttu-id="b40fb-160">Solo se precisa si es necesario apagar el controlador o el dispositivo de hardware físico.</span><span class="sxs-lookup"><span data-stu-id="b40fb-160">It is only required if the driver and/or the physical hardware device need to be shut down.</span></span> <span data-ttu-id="b40fb-161">Una vez finalizado el controlador, no se debe volver a llamar hasta que se vuelva a inicializar.</span><span class="sxs-lookup"><span data-stu-id="b40fb-161">After being terminated, the driver must not be called again until it is re-initialized.</span></span> 

## <a name="simple-driver-example"></a><span data-ttu-id="b40fb-162">Ejemplo de un controlador simple</span><span class="sxs-lookup"><span data-stu-id="b40fb-162">Simple Driver Example</span></span>

<span data-ttu-id="b40fb-163">Un ejemplo es la mejor manera de describir un controlador de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-163">An example is the best way to describe a device driver.</span></span> <span data-ttu-id="b40fb-164">En este ejemplo, el controlador supone que existe un dispositivo de hardware serie simple con un registro de configuración, un registro de entrada y un registro de salida.</span><span class="sxs-lookup"><span data-stu-id="b40fb-164">In this example, the driver assumes a simple serial hardware device with a configuration register, an input register, and an output register.</span></span> <span data-ttu-id="b40fb-165">En este ejemplo de controlador simple se muestran las áreas funcionales de inicialización, entrada, salida e interrupción.</span><span class="sxs-lookup"><span data-stu-id="b40fb-165">This simple driver example illustrates the initialization, input, output, and interrupt functional areas.</span></span>

### <a name="simple-driver-initialization"></a><span data-ttu-id="b40fb-166">Inicialización del controlador simple</span><span class="sxs-lookup"><span data-stu-id="b40fb-166">Simple Driver Initialization</span></span> 
<span data-ttu-id="b40fb-167">La función ***tx_sdriver_initialize*** del controlador simple crea dos semáforos de recuento que se usan para administrar las operaciones de entrada y salida del controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-167">The ***tx_sdriver_initialize*** function of the simple driver creates two counting semaphores that are used to manage the driver’s input and output operation.</span></span> <span data-ttu-id="b40fb-168">La ISR de entrada establece el semáforo de entrada cuando el dispositivo de hardware serie recibe un carácter.</span><span class="sxs-lookup"><span data-stu-id="b40fb-168">The input semaphore is set by the input ISR when a character is received by the serial hardware device.</span></span> <span data-ttu-id="b40fb-169">Por este motivo, el semáforo de entrada se crea con un recuento inicial de cero.</span><span class="sxs-lookup"><span data-stu-id="b40fb-169">Because of this, the input semaphore is created with an initial count of zero.</span></span>

<span data-ttu-id="b40fb-170">A su vez, el semáforo de salida indica la disponibilidad del registro de transmisión del dispositivo de hardware serie.</span><span class="sxs-lookup"><span data-stu-id="b40fb-170">Conversely, the output semaphore indicates the availability of the serial hardware transmit register.</span></span> <span data-ttu-id="b40fb-171">Se crea con un valor de uno para indicar que el registro de transmisión está inicialmente disponible.</span><span class="sxs-lookup"><span data-stu-id="b40fb-171">It is created with a value of one to indicate the transmit register is initially available.</span></span>

<span data-ttu-id="b40fb-172">La función de inicialización también es responsable de instalar los controladores de vector de interrupción de bajo nivel para las notificaciones de entrada y salida.</span><span class="sxs-lookup"><span data-stu-id="b40fb-172">The initialization function is also responsible for installing the low-level interrupt vector handlers for input and output notifications.</span></span> <span data-ttu-id="b40fb-173">Al igual que otras rutinas de servicio de interrupción de ThreadX SMP, el controlador de bajo nivel debe llamar a \* **_tx_thread_context_save** _ antes de llamar a la ISR del controlador simple.</span><span class="sxs-lookup"><span data-stu-id="b40fb-173">Like other ThreadX SMP interrupt service routines, the low-level handler must call \***_tx_thread_context_save** _ before calling the simple driver ISR.</span></span> <span data-ttu-id="b40fb-174">Cuando vuelve la ISR del controlador, el controlador de bajo nivel debe llamar a _\*_ _tx_thread_context_restore_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b40fb-174">After the driver ISR returns, the low-level handler must call _\*_ _tx_thread_context_restore_\*\*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b40fb-175">Es importante que se llame a la inicialización antes que a cualquier otra función del controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-175">It is important that initialization is called before any of the other driver functions.</span></span> <span data-ttu-id="b40fb-176">Normalmente, se llama a la inicialización del controlador desde **tx_application_define**.</span><span class="sxs-lookup"><span data-stu-id="b40fb-176">Typically, driver initialization is called from **tx_application_define**.</span></span>

<span data-ttu-id="b40fb-177">Consulte la figura 9 para ver el código fuente de inicialización del controlador simple.</span><span class="sxs-lookup"><span data-stu-id="b40fb-177">See Figure 9 on page 306 for the initialization source code of the simple driver.</span></span>

```C
VOID     tx_sdriver_initialize(VOID)
{

    /* Initialize the two counting semaphores used to control
       the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                       "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                       "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
       The initial vector handling should call the ISRs
       defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
       generation, baud rate, stop bits, etc. */
}
```
<span data-ttu-id="b40fb-178">**FIGURA 9. Inicialización de un controlador simple**</span><span class="sxs-lookup"><span data-stu-id="b40fb-178">**FIGURE 9. Simple Driver Initialization**</span></span>

### <a name="simple-driver-input"></a><span data-ttu-id="b40fb-179">Entrada al controlador simple</span><span class="sxs-lookup"><span data-stu-id="b40fb-179">Simple Driver Input</span></span> 
<span data-ttu-id="b40fb-180">La entrada al controlador simple se centra en el semáforo de entrada.</span><span class="sxs-lookup"><span data-stu-id="b40fb-180">Input for the simple driver centers around the input semaphore.</span></span> <span data-ttu-id="b40fb-181">Cuando se recibe una interrupción de entrada del dispositivo serie, se establece el semáforo de entrada.</span><span class="sxs-lookup"><span data-stu-id="b40fb-181">When a serial device input interrupt is received, the input semaphore is set.</span></span> <span data-ttu-id="b40fb-182">Si hay varios subprocesos esperando un carácter del controlador, se reanuda el subproceso que lleva esperando más tiempo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-182">If one or more threads are waiting for a character from the driver, the thread waiting the longest is resumed.</span></span> <span data-ttu-id="b40fb-183">Si no hay ningún subproceso en espera, el semáforo simplemente permanece establecido hasta que un subproceso llama a la función de entrada al controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-183">If no threads are waiting, the semaphore simply remains set until a thread calls the drive input function.</span></span>

<span data-ttu-id="b40fb-184">Existen varias limitaciones en el control de entradas al controlador simple.</span><span class="sxs-lookup"><span data-stu-id="b40fb-184">There are several limitations to the simple driver input handling.</span></span> <span data-ttu-id="b40fb-185">La más importante es la posibilidad de que se quiten caracteres de la entrada.</span><span class="sxs-lookup"><span data-stu-id="b40fb-185">The most significant is the potential for dropping input characters.</span></span> <span data-ttu-id="b40fb-186">Esto se debe a que no hay ninguna opción para almacenar en búfer los caracteres de entrada que llegan antes de que se haya procesado el carácter anterior.</span><span class="sxs-lookup"><span data-stu-id="b40fb-186">This is possible because there is no ability to buffer input characters that arrive before the previous character is processed.</span></span> <span data-ttu-id="b40fb-187">Se puede solucionar fácilmente agregando un búfer de caracteres de entrada.</span><span class="sxs-lookup"><span data-stu-id="b40fb-187">This is easily handled by adding an input character buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b40fb-188">Solo los subprocesos pueden llamar a la función **tx_sdriver_input**.</span><span class="sxs-lookup"><span data-stu-id="b40fb-188">Only threads are allowed to call the **tx_sdriver_input** function.</span></span>

<span data-ttu-id="b40fb-189">En la figura 10 se muestra el código fuente asociado a la entrada al controlador simple.</span><span class="sxs-lookup"><span data-stu-id="b40fb-189">Figure 10 shows the source code associated with simple driver input.</span></span>

```C
UCHAR     tx_sdriver_input(VOID)
{

    /* Determine if there is a character waiting. If not,
        suspend. */
    tx_semaphore_get(&tx_sdriver_input_semaphore,
                                             TX_WAIT_FOREVER;
    /* Return character from serial RX hardware register. */
    return(*serial_hardware_input_ptr);
}

VOID     tx_sdriver_input_ISR(VOID)
{
    /* See if an input character notification is pending. */
    if (!tx_sdriver_input_semaphore.tx_semaphore_count)
    {
        /* If not, notify thread of an input character. */
        tx_semaphore_put(&tx_sdriver_input_semaphore);
    }
}
```
<span data-ttu-id="b40fb-190">**FIGURA 10. Entrada al controlador simple**</span><span class="sxs-lookup"><span data-stu-id="b40fb-190">**FIGURE 10. Simple Driver Input**</span></span>

### <a name="simple-driver-output"></a><span data-ttu-id="b40fb-191">Salida del controlador simple</span><span class="sxs-lookup"><span data-stu-id="b40fb-191">Simple Driver Output</span></span> 
<span data-ttu-id="b40fb-192">El procesamiento de la salida emplea el semáforo de salida para indicar si el registro de transmisión del dispositivo serie está libre.</span><span class="sxs-lookup"><span data-stu-id="b40fb-192">Output processing utilizes the output semaphore to signal when the serial device’s transmit register is free.</span></span> <span data-ttu-id="b40fb-193">Antes de que un carácter de salida se escriba realmente en el dispositivo, se obtiene el semáforo de salida.</span><span class="sxs-lookup"><span data-stu-id="b40fb-193">Before an output character is actually written to the device, the output semaphore is obtained.</span></span> <span data-ttu-id="b40fb-194">Si no está disponible, significa que la transmisión anterior no ha finalizado todavía.</span><span class="sxs-lookup"><span data-stu-id="b40fb-194">If it is not available, the previous transmit is not yet complete.</span></span>

<span data-ttu-id="b40fb-195">La ISR de salida es responsable de controlar la interrupción de transmisión completa.</span><span class="sxs-lookup"><span data-stu-id="b40fb-195">The output ISR is responsible for handling the transmit complete interrupt.</span></span> <span data-ttu-id="b40fb-196">El procesamiento de la ISR de salida equivale a establecer el semáforo de salida, lo que permite la salida de otro carácter.</span><span class="sxs-lookup"><span data-stu-id="b40fb-196">Processing of the output ISR amounts to setting the output semaphore, thereby allowing output of another character.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b40fb-197">Solo los subprocesos pueden llamar a la función **tx_sdriver_output**.</span><span class="sxs-lookup"><span data-stu-id="b40fb-197">Only threads are allowed to call the **tx_sdriver_output** function.</span></span>

<span data-ttu-id="b40fb-198">En la figura 11 se muestra el código fuente asociado con la salida del controlador simple.</span><span class="sxs-lookup"><span data-stu-id="b40fb-198">Figure 11 shows the source code associated with simple driver output.</span></span>

```C
VOID     tx_sdriver_output(UCHAR alpha)
{

    /* Determine if the hardware is ready to transmit a
       character. If not, suspend until the previous output
        completes. */
    tx_semaphore_get(&tx_sdriver_output_semaphore,
                                            TX_WAIT_FOREVER);
    /* Send the character through the hardware. */
    *serial_hardware_output_ptr = alpha;
}

VOID     tx_sdriver_output_ISR(VOID)
{
    /* Notify thread last character transmit is
        complete. */
    tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
<span data-ttu-id="b40fb-199">**FIGURA 11. Salida del controlador simple**</span><span class="sxs-lookup"><span data-stu-id="b40fb-199">**FIGURE 11. Simple Driver Output**</span></span>

### <a name="simple-driver-shortcomings"></a><span data-ttu-id="b40fb-200">Limitaciones del controlador simple</span><span class="sxs-lookup"><span data-stu-id="b40fb-200">Simple Driver Shortcomings</span></span> 
<span data-ttu-id="b40fb-201">Este ejemplo de un controlador de dispositivo simple refleja la idea básica de un controlador de dispositivo de ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="b40fb-201">This simple device driver example illustrates the basic idea of a ThreadX SMP device driver.</span></span> <span data-ttu-id="b40fb-202">Sin embargo, dado que el controlador de dispositivo simple no se ocupa del almacenamiento en búfer de datos ni de ningún problema de sobrecarga, no acaba de representar los controladores de ThreadX SMP del mundo real.</span><span class="sxs-lookup"><span data-stu-id="b40fb-202">However, because the simple device driver does not address data buffering or any overhead issues, it does not fully represent real-world ThreadX SMP drivers.</span></span> <span data-ttu-id="b40fb-203">En la sección siguiente se describen algunas de las cuestiones más avanzadas asociadas a los controladores de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-203">The following section describes some of the more advanced issues associated with device drivers.</span></span>

## <a name="advanced-driver-issues"></a><span data-ttu-id="b40fb-204">Cuestiones de controladores avanzados</span><span class="sxs-lookup"><span data-stu-id="b40fb-204">Advanced Driver Issues</span></span>

<span data-ttu-id="b40fb-205">Como se mencionó anteriormente, los controladores de dispositivo tienen requisitos tan únicos como sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b40fb-205">As mentioned previously, device drivers have requirements as unique as their applications.</span></span> <span data-ttu-id="b40fb-206">Es posible que algunas aplicaciones requieran una cantidad enorme de almacenamiento en el búfer de datos, mientras que otra aplicación puede requerir una ISR de controlador optimizada debido a una gran frecuencia de las interrupciones de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-206">Some applications may require an enormous amount of data buffering while another application may require optimized driver ISRs because of high-frequency device interrupts.</span></span>

### <a name="io-buffering"></a><span data-ttu-id="b40fb-207">Almacenamiento en búfer de E/S</span><span class="sxs-lookup"><span data-stu-id="b40fb-207">I/O Buffering</span></span> 
<span data-ttu-id="b40fb-208">El almacenamiento en el búfer de datos de las aplicaciones insertadas en tiempo real requiere un planeamiento considerable.</span><span class="sxs-lookup"><span data-stu-id="b40fb-208">Data buffering in real-time embedded applications requires considerable planning.</span></span> <span data-ttu-id="b40fb-209">Parte del diseño viene determinado por el dispositivo de hardware subyacente.</span><span class="sxs-lookup"><span data-stu-id="b40fb-209">Some of the design is dictated by the underlying hardware device.</span></span> <span data-ttu-id="b40fb-210">Si el dispositivo proporciona E/S de bytes básica, es probable que resulte adecuado un búfer circular simple.</span><span class="sxs-lookup"><span data-stu-id="b40fb-210">If the device provides basic byte I/O, a simple circular buffer is probably in order.</span></span> <span data-ttu-id="b40fb-211">Sin embargo, si el dispositivo proporciona E/S en bloque, de DMA o de paquetes, es probable que esté justificado un esquema de administración de búferes.</span><span class="sxs-lookup"><span data-stu-id="b40fb-211">However, if the device provides block, DMA, or packet I/O, a buffer management scheme is probably warranted.</span></span> 

### <a name="circular-byte-buffers"></a><span data-ttu-id="b40fb-212">Búferes de bytes circulares</span><span class="sxs-lookup"><span data-stu-id="b40fb-212">Circular Byte Buffers</span></span> 
<span data-ttu-id="b40fb-213">Los búferes de bytes circulares se usan normalmente en controladores que administran un dispositivo de hardware serie simple como un UART.</span><span class="sxs-lookup"><span data-stu-id="b40fb-213">Circular byte buffers are typically used in drivers that manage a simple serial hardware device like a UART.</span></span> <span data-ttu-id="b40fb-214">En estas situaciones, se suelen usan dos búferes circulares: uno para la entrada y otro para la salida.</span><span class="sxs-lookup"><span data-stu-id="b40fb-214">Two circular buffers are most often used in such situations—one for input and one for output.</span></span>

<span data-ttu-id="b40fb-215">Cada búfer de bytes circular está formado por un área de memoria de bytes (normalmente una matriz de UCHAR), un puntero de lectura y un puntero de escritura.</span><span class="sxs-lookup"><span data-stu-id="b40fb-215">Each circular byte buffer is comprised of a byte memory area (typically an array of UCHARs), a read pointer, and a write pointer.</span></span> <span data-ttu-id="b40fb-216">Un búfer se considera vacío cuando el puntero de lectura y el puntero de escritura hacen referencia a la misma ubicación de memoria en el búfer.</span><span class="sxs-lookup"><span data-stu-id="b40fb-216">A buffer is considered empty when the read pointer and the write pointers reference the same memory location in the buffer.</span></span> <span data-ttu-id="b40fb-217">La inicialización del controlador establece los punteros de lectura y escritura del búfer en la dirección inicial del búfer.</span><span class="sxs-lookup"><span data-stu-id="b40fb-217">Driver initialization sets both the read and write buffer pointers to the beginning address of the buffer.</span></span>

### <a name="circular-buffer-input"></a><span data-ttu-id="b40fb-218">Entrada de búfer circular</span><span class="sxs-lookup"><span data-stu-id="b40fb-218">Circular Buffer Input</span></span> 
<span data-ttu-id="b40fb-219">El búfer de entrada se usa para contener los caracteres que llegan antes de que la aplicación esté lista para recibirlos.</span><span class="sxs-lookup"><span data-stu-id="b40fb-219">The input buffer is used to hold characters that arrive before the application is ready for them.</span></span> <span data-ttu-id="b40fb-220">Cuando se recibe un carácter de entrada (normalmente en una rutina de servicio de interrupción), el nuevo carácter se recupera del dispositivo de hardware y se coloca en el búfer de entrada en la ubicación a la que señala el puntero de escritura.</span><span class="sxs-lookup"><span data-stu-id="b40fb-220">When an input character is received (usually in an interrupt service routine), the new character is retrieved from the hardware device and placed into the input buffer at the location pointed to by the write pointer.</span></span> <span data-ttu-id="b40fb-221">A continuación, el puntero de escritura avanza a la siguiente posición en el búfer.</span><span class="sxs-lookup"><span data-stu-id="b40fb-221">The write pointer is then advanced to the next position in the buffer.</span></span> <span data-ttu-id="b40fb-222">Si la siguiente posición está más allá del final del búfer, el puntero de escritura se establece en el principio del búfer.</span><span class="sxs-lookup"><span data-stu-id="b40fb-222">If the next position is past the end of the buffer, the write pointer is set to the beginning of the buffer.</span></span> <span data-ttu-id="b40fb-223">La condición de cola llena se controla cancelando el avance del puntero de escritura si el nuevo puntero de escritura es el mismo que el puntero de lectura.</span><span class="sxs-lookup"><span data-stu-id="b40fb-223">The queue full condition is handled by canceling the write pointer advancement if the new write pointer is the same as the read pointer.</span></span>

<span data-ttu-id="b40fb-224">Las solicitudes de bytes de entrada de la aplicación al controlador examinan primero los punteros de lectura y escritura del búfer de entrada.</span><span class="sxs-lookup"><span data-stu-id="b40fb-224">Application input byte requests to the driver first examine the read and write pointers of the input buffer.</span></span> <span data-ttu-id="b40fb-225">Si ambos punteros son idénticos, significa que el búfer está vacío.</span><span class="sxs-lookup"><span data-stu-id="b40fb-225">If the read and write pointers are identical, the buffer is empty.</span></span> <span data-ttu-id="b40fb-226">De lo contrario, si el puntero de lectura no es el mismo, el byte al que apunta el puntero de lectura se copia desde el búfer de entrada y el puntero de lectura avanza a la siguiente ubicación de búfer.</span><span class="sxs-lookup"><span data-stu-id="b40fb-226">Otherwise, if the read pointer is not the same, the byte pointed to by the read pointer is copied from the input buffer and the read pointer is advanced to the next buffer location.</span></span> <span data-ttu-id="b40fb-227">Si el nuevo puntero de lectura está más allá del final del búfer, se restablece al principio.</span><span class="sxs-lookup"><span data-stu-id="b40fb-227">If the new read pointer is past the end of the buffer, it is reset to the beginning.</span></span> <span data-ttu-id="b40fb-228">En la figura 12 se muestra la lógica del búfer de entrada circular.</span><span class="sxs-lookup"><span data-stu-id="b40fb-228">Figure 12 shows the logic for the circular input buffer.</span></span>

```C
UCHAR     tx_input_buffer[MAX_SIZE];
UCHAR     tx_input_write_ptr;
UCHAR     tx_input_read_ptr;

/* Initialization.  */
tx_input_write_ptr =  &tx_input_buffer[0];
tx_input_read_ptr =    &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr =  tx_input_write_ptr;
*tx_input_write_ptr++ =  alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr =  &tx_input_buffer[0];  /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr =  save_ptr;  /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
    alpha =  *tx_input_read_ptr++;
    if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
        tx_input_read_ptr =  &tx_input_buffer[0];
}
```
<span data-ttu-id="b40fb-229">**FIGURA 12. Lógica del búfer de entrada circular**</span><span class="sxs-lookup"><span data-stu-id="b40fb-229">**FIGURE 12. Logic for Circular Input Buffer**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b40fb-230">Para conseguir un funcionamiento confiable, puede ser necesario bloquear las interrupciones cuando se manipulan los punteros de lectura y escritura de los búferes circulares de entrada y salida.</span><span class="sxs-lookup"><span data-stu-id="b40fb-230">For reliable operation, it may be necessary to lockout interrupts when manipulating the read and write pointers of both the input and output circular buffers.</span></span>

### <a name="circular-output-buffer"></a><span data-ttu-id="b40fb-231">Búfer de salida circular</span><span class="sxs-lookup"><span data-stu-id="b40fb-231">Circular Output Buffer</span></span> 
<span data-ttu-id="b40fb-232">El búfer de salida se usa para contener los caracteres que han llegado para su salida antes de que el dispositivo de hardware haya terminado de enviar el byte anterior.</span><span class="sxs-lookup"><span data-stu-id="b40fb-232">The output buffer is used to hold characters that have arrived for output before the hardware device finished sending the previous byte.</span></span> <span data-ttu-id="b40fb-233">El procesamiento del búfer de salida es similar al procesamiento del búfer de entrada, excepto en que el procesamiento de la interrupción de transmisión completa manipula el puntero de lectura de salida, en tanto que la solicitud de salida de la aplicación emplea el puntero de escritura de salida.</span><span class="sxs-lookup"><span data-stu-id="b40fb-233">Output buffer processing is similar to input buffer processing, except the transmit complete interrupt processing manipulates the output read pointer, while the application output request utilizes the output write pointer.</span></span> <span data-ttu-id="b40fb-234">Por lo demás, el procesamiento del búfer de salida es el mismo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-234">Otherwise, the output buffer processing is the same.</span></span> <span data-ttu-id="b40fb-235">En la figura 13 se muestra la lógica del búfer de salida circular.</span><span class="sxs-lookup"><span data-stu-id="b40fb-235">Figure 13shows the logic for the circular output buffer.</span></span>

```C
UCHAR     tx_output_buffer[MAX_SIZE];
UCHAR     tx_output_write_ptr;
UCHAR     tx_output_read_ptr;

/* Initialization.  */
tx_output_write_ptr =  &tx_output_buffer[0];
tx_output_read_ptr =   &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
    *device_reg =  *tx_output_read_ptr++;
    if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
    tx_output_read_ptr =  &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr =  tx_output_write_ptr;
*tx_output_write_ptr++ =  alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr =  &tx_output_buffer[0];  /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr =  save_ptr;  /* Buffer full!  */
```
<span data-ttu-id="b40fb-236">**FIGURA 13. Lógica del búfer de salida circular**</span><span class="sxs-lookup"><span data-stu-id="b40fb-236">**FIGURE 13. Logic for Circular Output Buffer**</span></span>

### <a name="buffer-io-management"></a><span data-ttu-id="b40fb-237">Administración de búferes de E/S</span><span class="sxs-lookup"><span data-stu-id="b40fb-237">Buffer I/O Management</span></span> 
<span data-ttu-id="b40fb-238">Para mejorar el rendimiento de los microprocesadores insertados, muchos dispositivos periféricos transmiten y reciben datos con búferes suministrados por el software.</span><span class="sxs-lookup"><span data-stu-id="b40fb-238">To improve the performance of embedded microprocessors, many peripheral device devices transmit and receive data with buffers supplied by software.</span></span> <span data-ttu-id="b40fb-239">En algunas implementaciones, se pueden usar varios búferes para transmitir o recibir paquetes de datos individuales.</span><span class="sxs-lookup"><span data-stu-id="b40fb-239">In some implementations, multiple buffers may be used to transmit or receive individual packets of data.</span></span> 

<span data-ttu-id="b40fb-240">El tamaño y la ubicación de los búferes de E/S viene determinado por la aplicación o el software del controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-240">The size and location of I/O buffers is determined by the application and/or driver software.</span></span> <span data-ttu-id="b40fb-241">Normalmente, los búferes tienen un tamaño fijo y se administran dentro de un grupo de bloques de memoria de ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="b40fb-241">Typically, buffers are fixed in size and managed within a ThreadX SMP block memory pool.</span></span> <span data-ttu-id="b40fb-242">En la figura 14 se describe un búfer de E/S típico y un grupo de bloques de memoria de ThreadX SMP que administra su asignación.</span><span class="sxs-lookup"><span data-stu-id="b40fb-242">Figure 14describes a typical I/O buffer and a ThreadX SMP block memory pool that manages their allocation.</span></span>

```C
typedef struct TX_IO_BUFFER_STRUCT
{

      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
    struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR  tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
   "free_memory_ptr"points to an available memory area that
   is 64 KBytes in size. */

tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```
<span data-ttu-id="b40fb-243">**FIGURA 14. Búfer de E/S**</span><span class="sxs-lookup"><span data-stu-id="b40fb-243">**FIGURE 14. I/O Buffer**</span></span>

### <a name="tx_io_buffer"></a><span data-ttu-id="b40fb-244">TX_IO_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b40fb-244">TX_IO_BUFFER</span></span> 
<span data-ttu-id="b40fb-245">La definición de tipo TX_IO_BUFFER consta de dos punteros.</span><span class="sxs-lookup"><span data-stu-id="b40fb-245">The typedef TX_IO_BUFFER consists of two pointers.</span></span> <span data-ttu-id="b40fb-246">El puntero \***tx_next_packet** _ se usa para vincular varios paquetes de la lista de entrada o de salida.</span><span class="sxs-lookup"><span data-stu-id="b40fb-246">The \***tx_next_packet** _ pointer is used to link multiple packets on either the input or output list.</span></span> <span data-ttu-id="b40fb-247">El puntero _ *_tx_next_buffer_*\* se usa para vincular los búferes que componen un paquete individual de datos del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-247">The _ *_tx_next_buffer_*\* pointer is used to link together buffers that make up an individual packet of data from the device.</span></span> <span data-ttu-id="b40fb-248">Ambos punteros se establecen en NULL cuando el búfer se asigna desde el grupo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-248">Both of these pointers are set to NULL when the buffer is allocated from the pool.</span></span> <span data-ttu-id="b40fb-249">Además, algunos dispositivos pueden requerir otro campo para indicar cuánta proporción del área de búfer contiene realmente datos.</span><span class="sxs-lookup"><span data-stu-id="b40fb-249">In addition, some devices may require another field to indicate how much of the buffer area actually contains data.</span></span>

### <a name="buffered-io-advantage"></a><span data-ttu-id="b40fb-250">Ventaja de la entrada/salida almacenada en búfer</span><span class="sxs-lookup"><span data-stu-id="b40fb-250">Buffered I/O Advantage</span></span> 
<span data-ttu-id="b40fb-251">¿Cuáles son las ventajas de un esquema de E/S en búfer?</span><span class="sxs-lookup"><span data-stu-id="b40fb-251">What are the advantages of a buffer I/O scheme?</span></span> <span data-ttu-id="b40fb-252">La mayor ventaja es que los datos no se copian entre los registros del dispositivo y la memoria de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b40fb-252">The biggest advantage is that data is not copied between the device registers and the application’s memory.</span></span> <span data-ttu-id="b40fb-253">En vez de esto, el controlador proporciona al dispositivo una serie de punteros de búfer.</span><span class="sxs-lookup"><span data-stu-id="b40fb-253">Instead, the driver provides the device with a series of buffer pointers.</span></span> <span data-ttu-id="b40fb-254">La E/S del dispositivo físico emplea directamente la memoria de búfer suministrada.</span><span class="sxs-lookup"><span data-stu-id="b40fb-254">Physical device I/O utilizes the supplied buffer memory directly.</span></span>

<span data-ttu-id="b40fb-255">El uso del procesador para copiar paquetes de entrada o salida de información es extremadamente costoso y debe evitarse en cualquier situación de E/S con una capacidad de proceso elevada.</span><span class="sxs-lookup"><span data-stu-id="b40fb-255">Using the processor to copy input or output packets of information is extremely costly and should be avoided in any high throughput I/O situation.</span></span>

<span data-ttu-id="b40fb-256">Otra ventaja del enfoque de E/S almacenada en búfer es que las listas de entrada y salida no tienen condiciones de elemento completo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-256">Another advantage to the buffered I/O approach is that the input and output lists do not have full conditions.</span></span> <span data-ttu-id="b40fb-257">Todos los búferes disponibles pueden estar en cualquiera de las dos listas en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="b40fb-257">All of the available buffers can be on either list at any one time.</span></span> <span data-ttu-id="b40fb-258">Esto lo distingue de los búferes circulares de bytes simples presentados antes en el capítulo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-258">This contrasts with the simple byte circular buffers presented earlier in the chapter.</span></span> <span data-ttu-id="b40fb-259">Cada uno tenía un tamaño fijo que se determinaba en la compilación.</span><span class="sxs-lookup"><span data-stu-id="b40fb-259">Each had a fixed size determined at compilation.</span></span>

### <a name="buffered-driver-responsibilities"></a><span data-ttu-id="b40fb-260">Responsabilidades del controlador con almacenamiento en búfer</span><span class="sxs-lookup"><span data-stu-id="b40fb-260">Buffered Driver Responsibilities</span></span> 
<span data-ttu-id="b40fb-261">Los controladores de dispositivo con almacenamiento en búfer solo se ocupan de administrar listas vinculadas de búferes de E/S.</span><span class="sxs-lookup"><span data-stu-id="b40fb-261">Buffered device drivers are only concerned with managing linked lists of I/O buffers.</span></span> <span data-ttu-id="b40fb-262">Se mantiene una lista de búferes de entrada para los paquetes que se reciben antes de que el software de la aplicación esté listo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-262">An input buffer list is maintained for packets that are received before the application software is ready.</span></span> <span data-ttu-id="b40fb-263">También se mantiene una lista de búferes de salida para los paquetes que se envían más rápido de lo que el dispositivo de hardware puede gestionar.</span><span class="sxs-lookup"><span data-stu-id="b40fb-263">Conversely, an output buffer list is maintained for packets being sent faster than the hardware device can handle them.</span></span> <span data-ttu-id="b40fb-264">En la figura 15 se muestran listas vinculadas de entrada y salida simples de paquetes de datos y los búferes que componen cada paquete.</span><span class="sxs-lookup"><span data-stu-id="b40fb-264">Figure 15 on page 314 shows simple input and output linked lists of data packets and the buffer(s) that make up each packet.</span></span>

![Responsabilidades del controlador con almacenamiento en búfer](media/image11.png)

<span data-ttu-id="b40fb-266">**FIGURA 15. Listas de entrada y salida**</span><span class="sxs-lookup"><span data-stu-id="b40fb-266">**FIGURE 15. Input-Output Lists**</span></span>

<span data-ttu-id="b40fb-267">Las aplicaciones interactúan con controladores con almacenamiento en búfer que tienen los mismos búferes de E/S.</span><span class="sxs-lookup"><span data-stu-id="b40fb-267">Applications interface with buffered drivers with the same I/O buffers.</span></span> <span data-ttu-id="b40fb-268">En la transmisión, el software de la aplicación proporciona al controlador uno o más búferes para transmitir.</span><span class="sxs-lookup"><span data-stu-id="b40fb-268">On transmit, application software provides the driver with one or more buffers to transmit.</span></span> <span data-ttu-id="b40fb-269">Cuando el software de la aplicación solicita una entrada, el controlador devuelve los datos de entrada en búferes de E/S.</span><span class="sxs-lookup"><span data-stu-id="b40fb-269">When the application software requests input, the driver returns the input data in I/O buffers.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b40fb-270">En algunas aplicaciones, puede ser útil crear una interfaz de entrada al controlador que requiera que la aplicación intercambie un búfer libre por un búfer de entrada del controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-270">In some applications, it may be useful to build a driver input interface that requires the application to exchange a free buffer for an input buffer from the driver.</span></span> <span data-ttu-id="b40fb-271">Esto podría aliviar parte del procesamiento de la asignación de búferes dentro del controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-271">This might alleviate some buffer allocation processing inside of the driver.</span></span>

### <a name="interrupt-management"></a><span data-ttu-id="b40fb-272">Administración de interrupciones</span><span class="sxs-lookup"><span data-stu-id="b40fb-272">Interrupt Management</span></span> 
<span data-ttu-id="b40fb-273">En algunas aplicaciones, la frecuencia de interrupción del dispositivo puede prohibir escribir la ISR en C o interactuar con ThreadX SMP en cada interrupción.</span><span class="sxs-lookup"><span data-stu-id="b40fb-273">In some applications, the device interrupt frequency may prohibit writing the ISR in C or to interact with ThreadX SMP on each interrupt.</span></span> <span data-ttu-id="b40fb-274">Por ejemplo, si se tardan 25 μs en guardar y restaurar el contexto interrumpido, no sería aconsejable realizar un guardado de contexto completo con una frecuencia de interrupción de 50 μs.</span><span class="sxs-lookup"><span data-stu-id="b40fb-274">For example, if it takes 25us to save and restore the interrupted context, it would not be advisable to perform a full context save if the interrupt frequency was 50us.</span></span> <span data-ttu-id="b40fb-275">En tales casos, se usa una ISR de lenguaje de ensamblado pequeña para controlar la mayoría de las interrupciones del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b40fb-275">In such cases, a small assembly language ISR is used to handle most of the device interrupts.</span></span> <span data-ttu-id="b40fb-276">Esta ISR de carga baja solo interactuará con ThreadX SMP cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="b40fb-276">This lowoverhead ISR would only interact with ThreadX SMP when necessary.</span></span>

<span data-ttu-id="b40fb-277">Se trata una cuestión similar en la explicación sobre la administración de interrupciones al final del capítulo 3.</span><span class="sxs-lookup"><span data-stu-id="b40fb-277">A similar discussion can be found in the interrupt management discussion at the end of Chapter 3.</span></span>

> [!NOTE]
> <span data-ttu-id="b40fb-278">Si se va a usar el bloqueo de interrupciones para proteger secciones críticas del código de controlador ante el código de la ISR del controlador, el código del controlador en el nivel de subproceso debe ejecutarse siempre en el mismo núcleo en el que se procesa la ISR.</span><span class="sxs-lookup"><span data-stu-id="b40fb-278">If interrupt lockout is to be used to protect critical sections of driver code from driver ISR code, the thread level driver code must always execute on the same core that the ISR is processed on.</span></span> <span data-ttu-id="b40fb-279">Si no, se deben usar primitivas internas de ThreadX SMP como TX_DISABLE y TX_RESTORE, que también tienen integrada la protección entre núcleos.</span><span class="sxs-lookup"><span data-stu-id="b40fb-279">Otherwise, internal ThreadX SMP primitives like TX_DISABLE and TX_RESTORE should be used that also have inter-core protection built-in.</span></span>

### <a name="thread-suspension"></a><span data-ttu-id="b40fb-280">Suspensión de subprocesos</span><span class="sxs-lookup"><span data-stu-id="b40fb-280">Thread Suspension</span></span> 
<span data-ttu-id="b40fb-281">En el ejemplo de controlador simple presentado anteriormente en este capítulo, se suspende el autor de la llamada del servicio de entrada si un carácter no está disponible.</span><span class="sxs-lookup"><span data-stu-id="b40fb-281">In the simple driver example presented earlier in this chapter, the caller of the input service suspends if a character is not available.</span></span> <span data-ttu-id="b40fb-282">En algunas aplicaciones, puede que esto no resulte viable.</span><span class="sxs-lookup"><span data-stu-id="b40fb-282">In some applications, this might not be acceptable.</span></span>

<span data-ttu-id="b40fb-283">Por ejemplo, si el subproceso responsable de procesar la entrada de un controlador también tiene otras tareas, probablemente no se podrá suspender solo la entrada del controlador.</span><span class="sxs-lookup"><span data-stu-id="b40fb-283">For example, if the thread responsible for processing input from a driver also has other duties, suspending on just the driver input is probably not going to work.</span></span> <span data-ttu-id="b40fb-284">En su lugar, debe personalizarse el controlador para solicitar el procesamiento de forma similar a la manera en que se realizan otras solicitudes de procesamiento al subproceso.</span><span class="sxs-lookup"><span data-stu-id="b40fb-284">Instead, the driver needs to be customized to request processing similar to the way other processing requests are made to the thread.</span></span>

<span data-ttu-id="b40fb-285">En la mayoría de los casos, se coloca el búfer de entrada en una lista vinculada y se envía un mensaje de evento de entrada a la cola de entrada del subproceso.</span><span class="sxs-lookup"><span data-stu-id="b40fb-285">In most cases, the input buffer is placed on a linked list and an input event message is sent to the thread’s input queue.</span></span>