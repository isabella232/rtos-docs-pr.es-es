---
title: 'Capítulo 2: Instalación y uso de Azure RTOS ThreadX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del kernel de alto rendimiento de Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e1bf85d363b07c81f226d494107eae9ba18114a7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814357"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a><span data-ttu-id="cd4e1-103">Capítulo 2: Instalación y uso de Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="cd4e1-103">Chapter 2 - Installation and Use of Azure RTOS ThreadX</span></span>

<span data-ttu-id="cd4e1-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del kernel de alto rendimiento de Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-104">This chapter contains a description of various issues related to installation, setup, and usage of the high-performance Azure RTOS ThreadX kernel.</span></span>

## <a name="host-considerations"></a><span data-ttu-id="cd4e1-105">Consideraciones sobre el host</span><span class="sxs-lookup"><span data-stu-id="cd4e1-105">Host Considerations</span></span>

<span data-ttu-id="cd4e1-106">El software insertado se suele desarrollar en equipos host con Windows o Linux (Unix).</span><span class="sxs-lookup"><span data-stu-id="cd4e1-106">Embedded software is usually developed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="cd4e1-107">Una vez que la aplicación está compilada, vinculada y ubicada en el host, se descarga en el hardware de destino para su ejecución.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="cd4e1-108">Normalmente, la descarga en el destino se realiza desde el depurador de la herramienta de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-108">Usually the target download is done from within the development tool debugger.</span></span> <span data-ttu-id="cd4e1-109">Después de finalizar la descarga, el depurador es responsable de proporcionar el control de ejecución de destino (ir, detener, punto de interrupción, etc.), así como el acceso a la memoria y a los registros del procesador.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-109">After the download has completed, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="cd4e1-110">La mayoría de los depuradores de las herramientas de desarrollo se comunican con el hardware de destino mediante conexiones de depuración en el chip (OCD), como JTAG (IEEE 1149.1) y el modo de depuración en segundo plano (BDM).</span><span class="sxs-lookup"><span data-stu-id="cd4e1-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="cd4e1-111">Los depuradores también se comunican con el hardware de destino mediante conexiones de emulación en el circuito (ICE).</span><span class="sxs-lookup"><span data-stu-id="cd4e1-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="cd4e1-112">Las conexiones OCD e ICE proporcionan soluciones sólidas con una intrusión mínima en el software residente de destino.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="cd4e1-113">En cuanto a los recursos utilizados en el host, el código fuente de ThreadX se entrega en formato ASCII y requiere aproximadamente 1 MByte de espacio en el disco duro del equipo host.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-113">As for resources used on the host, the source code for ThreadX is delivered in ASCII format and requires approximately 1 MByte of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="cd4e1-114">Consideraciones sobre el destino</span><span class="sxs-lookup"><span data-stu-id="cd4e1-114">Target Considerations</span></span>

<span data-ttu-id="cd4e1-115">ThreadX requiere entre 2 KBytes y 20 KBytes de memoria de solo lectura (ROM) en el destino.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-115">ThreadX requires between 2 KBytes and 20 KBytes of Read Only Memory (ROM) on the target.</span></span> <span data-ttu-id="cd4e1-116">También requiere de 1 a 2 KBytes adicionales de memoria de acceso aleatorio (RAM) del destino para la pila del sistema de ThreadX y otras estructuras de datos globales.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-116">It also requires another 1 to 2 KBytes of the target's Random Access Memory (RAM) for the ThreadX system stack and other global data structures.</span></span>

<span data-ttu-id="cd4e1-117">Para que las funciones relacionadas con el temporizador, como los tiempos de espera de las llamadas de servicio, la segmentación del tiempo y los temporizadores de la aplicación funcionen, el hardware de destino subyacente debe proporcionar un origen de interrupciones periódico.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-117">For timer-related functions like service call time-outs, time-slicing, and application timers to function, the underlying target hardware must provide a periodic interrupt source.</span></span> <span data-ttu-id="cd4e1-118">Si el procesador dispone de esta funcionalidad, ThreadX la usará.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-118">If the processor has this capability, it is utilized by ThreadX.</span></span> <span data-ttu-id="cd4e1-119">De lo contrario, si el procesador de destino no tiene la capacidad de generar una interrupción periódica, el hardware del usuario debe proporcionarla.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-119">Otherwise, if the target processor does not have the ability to generate a periodic interrupt, the user's hardware must provide it.</span></span> <span data-ttu-id="cd4e1-120">La instalación y configuración de la interrupción del temporizador se encuentra normalmente en el archivo de ensamblado ***tx_initialize_low_level*** de la distribución de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-120">Setup and configuration of the timer interrupt is typically located in the ***tx_initialize_low_level*** assembly file in the ThreadX distribution.</span></span>

> [!NOTE]
> <span data-ttu-id="cd4e1-121">*ThreadX sigue siendo funcional incluso si no hay disponible ningún origen de interrupciones de temporizador periódico. Sin embargo, ninguno de los servicios relacionados con el temporizador son funcionales.*</span><span class="sxs-lookup"><span data-stu-id="cd4e1-121">*ThreadX is still functional even if no periodic timer interrupt source is available. However, none of the timer-related services are functional.*</span></span>

## <a name="product-distribution"></a><span data-ttu-id="cd4e1-122">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="cd4e1-122">Product Distribution</span></span>

<span data-ttu-id="cd4e1-123">Azure RTOS ThreadX se puede obtener desde el repositorio de código fuente público en <https://github.com/azure-rtos/threadx/>.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-123">Azure RTOS ThreadX can be obtained from our public source code repository at <https://github.com/azure-rtos/threadx/>.</span></span>

<span data-ttu-id="cd4e1-124">A continuación se muestra una lista de varios archivos importantes del repositorio.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-124">The following is a list of several important files in the repository.</span></span>

| <span data-ttu-id="cd4e1-125">Nombre de archivo</span><span class="sxs-lookup"><span data-stu-id="cd4e1-125">Filename</span></span> | <span data-ttu-id="cd4e1-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="cd4e1-126">Description</span></span> |
|------------------- | ----------- |
| <span data-ttu-id="cd4e1-127">**tx_api.h**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-127">**tx_api.h**</span></span>                      | <span data-ttu-id="cd4e1-128">Archivo de encabezado de C que contiene todas las equivalencias del sistema, las estructuras de datos y los prototipos del servicio.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-128">C header file containing all system equates, data structures, and service prototypes.</span></span>                                                             |
| <span data-ttu-id="cd4e1-129">**tx_port.h**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-129">**tx_port.h**</span></span>                     | <span data-ttu-id="cd4e1-130">Archivo de encabezado de C que contiene todas las definiciones y estructuras de datos específicos de la herramienta de desarrollo y del destino.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-130">C header file containing all development-tool and targetspecific data definitions and structures.</span></span>                                                 |
| <span data-ttu-id="cd4e1-131">**demo_threadx.c**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-131">**demo_threadx.c**</span></span>                | <span data-ttu-id="cd4e1-132">Archivo de C que contiene una pequeña aplicación de demostración.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-132">C file containing a small demo application.</span></span>                                                                                                       |
| <span data-ttu-id="cd4e1-133">**tx.a (o tx.lib)**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-133">**tx.a (or tx.lib)**</span></span>              | <span data-ttu-id="cd4e1-134">Versión binaria de la biblioteca de C de ThreadX que se distribuye con el paquete *estándar*.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-134">Binary version of the ThreadX C library that is distributed with the *standard* package.</span></span>                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
><span data-ttu-id="cd4e1-135">*Todos los nombres de archivo están en minúsculas. Esta convención de nomenclatura facilita la conversión de los comandos para plataformas de desarrollo Linux (Unix).*</span><span class="sxs-lookup"><span data-stu-id="cd4e1-135">*All file names are in lower-case. This naming convention makes it easier to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="threadx-installation"></a><span data-ttu-id="cd4e1-136">Instalación de ThreadX</span><span class="sxs-lookup"><span data-stu-id="cd4e1-136">ThreadX Installation</span></span>

<span data-ttu-id="cd4e1-137">ThreadX se instala mediante la clonación del repositorio de GitHub en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-137">ThreadX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="cd4e1-138">La siguiente es la sintaxis típica para la creación de un clon del repositorio de ThreadX en el equipo.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-138">The following is typical syntax for creating a clone of the ThreadX repository on your PC.</span></span>

```c
    git clone https://github.com/azure-rtos/threadx
```

<span data-ttu-id="cd4e1-139">También se puede descargar una copia del repositorio mediante el botón de descarga de la página principal de GitHub.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-139">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="cd4e1-140">Además, hay instrucciones para compilar la biblioteca de ThreadX en la página principal del repositorio en línea.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-140">You will also find instructions for building the ThreadX library on the front page of the online repository.</span></span>

> [!NOTE]
> <span data-ttu-id="cd4e1-141">*El software de la aplicación necesita acceso al archivo de biblioteca de ThreadX (normalmente **tx.a** o **tx.lib**) y los archivos de inclusión de C **_tx_api.h_* _ y _*_tx_port.h_*_.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-141">*Application software needs access to the ThreadX library file (usually **tx.a** or **tx.lib**) and the C include files **_tx_api.h_* _ and _*_tx_port.h_*_.</span></span> <span data-ttu-id="cd4e1-142">Esto se logra estableciendo la ruta de acceso adecuada para las herramientas de desarrollo o copiando estos archivos en el área de desarrollo de la aplicación._</span><span class="sxs-lookup"><span data-stu-id="cd4e1-142">This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area._</span></span>

## <a name="using-threadx"></a><span data-ttu-id="cd4e1-143">Uso de ThreadX</span><span class="sxs-lookup"><span data-stu-id="cd4e1-143">Using ThreadX</span></span>

<span data-ttu-id="cd4e1-144">Para usar ThreadX, el código de la aplicación debe incluir el archivo ***tx_api.h** _ durante la compilación y vincular con la biblioteca en tiempo de ejecución de ThreadX _*_tx.a_*_ (o _*_tx.lib_\*\*).</span><span class="sxs-lookup"><span data-stu-id="cd4e1-144">To use ThreadX, the application code must include ***tx_api.h** _ during compilation and link with the ThreadX run-time library _*_tx.a_*_ (or _*_tx.lib_\*\*).</span></span>

<span data-ttu-id="cd4e1-145">Hay cuatro pasos necesarios para compilar una aplicación de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-145">There are four steps required to build a ThreadX application.</span></span>

1. <span data-ttu-id="cd4e1-146">Incluya el archivo ***tx_api.h*** en todos los archivos de la aplicación que usen servicios o estructuras de datos de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-146">Include the ***tx_api.h*** file in all application files that use ThreadX services or data structures.</span></span>

1. <span data-ttu-id="cd4e1-147">Cree la función estándar de C \***main** _.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-147">Create the standard C \***main** _ function.</span></span> <span data-ttu-id="cd4e1-148">Esta función debe llamar finalmente a _ *_tx_kernel_enter_*\* para iniciar ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-148">This function must eventually call _ *_tx_kernel_enter_*\* to start ThreadX.</span></span> <span data-ttu-id="cd4e1-149">La inicialización específica de la aplicación que no implique a ThreadX se puede agregar antes de entrar en el kernel.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-149">Application-specific initialization that does not involve ThreadX may be added prior to entering the kernel.</span></span>

      > [!IMPORTANT]
      > <span data-ttu-id="cd4e1-150">\*La función de entrada de ThreadX \***tx_kernel_enter** _ nunca vuelve.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-150">\*The ThreadX entry function \***tx_kernel_enter** _ does not return.</span></span> <span data-ttu-id="cd4e1-151">Por tanto, asegúrese de no colocar ninguna llamada de función o procesamiento después de ella._</span><span class="sxs-lookup"><span data-stu-id="cd4e1-151">So be sure not to place any processing or function calls after it._</span></span>

1. <span data-ttu-id="cd4e1-152">Cree la función ***tx_application_define***.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-152">Create the ***tx_application_define*** function.</span></span> <span data-ttu-id="cd4e1-153">Aquí es donde se crean los recursos iniciales del sistema.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-153">This is where the initial system resources are created.</span></span> <span data-ttu-id="cd4e1-154">Algunos ejemplos de recursos del sistema son los subprocesos, las colas, los bloques de memoria, los grupos de marcas de eventos, las exclusiones mutuas y los semáforos.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-154">Examples of system resources include threads, queues, memory pools, event flags groups, mutexes, and semaphores.</span></span>

1. <span data-ttu-id="cd4e1-155">Compile el código fuente de la aplicación y vincúlelo con la biblioteca en tiempo de ejecución de ThreadX ***tx.lib***.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-155">Compile application source and link with the ThreadX run-time library ***tx.lib***.</span></span> <span data-ttu-id="cd4e1-156">La imagen resultante se puede descargar en el destino y ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-156">The resulting image can be downloaded to the target and executed!</span></span>

## <a name="small-example-system"></a><span data-ttu-id="cd4e1-157">Sistema de ejemplo pequeño</span><span class="sxs-lookup"><span data-stu-id="cd4e1-157">Small Example System</span></span>

<span data-ttu-id="cd4e1-158">En el sistema de ejemplo pequeño de la figura 1 se muestra la creación de un único subproceso con prioridad 3.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-158">The small example system in Figure 1 shows the creation of a single thread with a priority of 3.</span></span> <span data-ttu-id="cd4e1-159">El subproceso se ejecuta, incrementa un contador y, a continuación, entra en suspensión durante un tic del reloj.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-159">The thread executes, increments a counter, then sleeps for one clock tick.</span></span>
<span data-ttu-id="cd4e1-160">Este proceso continúa indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-160">This process continues forever.</span></span>

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter( );
}
void tx_application_define(void *first_unused_memory)
{
    /* Create my_thread! */
    tx_thread_create(&my_thread, "My Thread",
    my_thread_entry, 0x1234, first_unused_memory, 1024,
    3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}
void my_thread_entry(ULONG thread_input)
{
    /* Enter into a forever loop. */
    while(1)
    {
        /* Increment thread counter. */
        my_thread_counter++;
        /* Sleep for 1 tick. */
        tx_thread_sleep(1);
    }
}
```

<span data-ttu-id="cd4e1-161">**FIGURA 1. Plantilla para el desarrollo de aplicaciones**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-161">**FIGURE 1. Template for Application Development**</span></span>

<span data-ttu-id="cd4e1-162">Aunque este es un ejemplo sencillo, proporciona una buena plantilla para el desarrollo de aplicaciones reales.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-162">Although this is a simple example, it provides a good template for real application development.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="cd4e1-163">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="cd4e1-163">Troubleshooting</span></span>

<span data-ttu-id="cd4e1-164">Cada distribución de ThreadX se entrega con una aplicación de demostración.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-164">Each ThreadX port is delivered with a demonstration application.</span></span> <span data-ttu-id="cd4e1-165">Siempre es una buena idea poner en primer lugar el sistema de demostración en ejecución, ya sea en el hardware de destino real o en un entorno simulado.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-165">It is always a good idea to first get the demonstration system running—either on actual target hardware or simulated environment.</span></span>

<span data-ttu-id="cd4e1-166">Si el sistema de demostración no se ejecuta correctamente, estas son algunas sugerencias para la solución de problemas.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-166">If the demonstration system does not execute properly, the following are some troubleshooting tips.</span></span>

1. <span data-ttu-id="cd4e1-167">Determine qué parte de la demostración se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-167">Determine how much of the demonstration is running.</span></span>
1. <span data-ttu-id="cd4e1-168">Aumente los tamaños de la pila (esto es más importante en el código real de la aplicación que en la demostración).</span><span class="sxs-lookup"><span data-stu-id="cd4e1-168">Increase stack sizes (this is more important in actual application code than it is for the demonstration).</span></span>
1. <span data-ttu-id="cd4e1-169">Vuelva a compilar la biblioteca de ThreadX con TX_ENABLE_STACK_CHECKING definido.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-169">Rebuild the ThreadX library with TX_ENABLE_STACK_CHECKING defined.</span></span> <span data-ttu-id="cd4e1-170">Esto habilita la comprobación de la pila de ThreadX integrada.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-170">This enables the built-in ThreadX stack checking.</span></span>
1. <span data-ttu-id="cd4e1-171">Omita temporalmente los cambios recientes para ver si el problema desaparece o cambia.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-171">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="cd4e1-172">Esta información debería resultar útil para los ingenieros de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-172">Such information should prove useful to support engineers.</span></span>

<span data-ttu-id="cd4e1-173">Siga los procedimientos descritos en "[Centro de atención al cliente](about-this-guide.md#customer-support-center)" para enviar la información recopilada en los pasos de solución de problemas.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-173">Follow the procedures outlined in "[Customer Support Center](about-this-guide.md#customer-support-center)" to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="cd4e1-174">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="cd4e1-174">Configuration Options</span></span>

<span data-ttu-id="cd4e1-175">Hay varias opciones de configuración al compilar la biblioteca de ThreadX y la aplicación con ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-175">There are several configuration options when building the ThreadX library and the application using ThreadX.</span></span> <span data-ttu-id="cd4e1-176">Las opciones siguientes se pueden definir en el código fuente de la aplicación, en la línea de comandos o en el archivo de inclusión ***tx_user.h***.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-176">The options below can be defined in the application source, on the command line, or within the ***tx_user.h*** include file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd4e1-177">*Las opciones definidas en ***tx_user.h** _ solo se aplican si la aplicación y la biblioteca de ThreadX se compilan con el elemento _ *TX_INCLUDE_USER_DEFINE_FILE** definido.*</span><span class="sxs-lookup"><span data-stu-id="cd4e1-177">*Options defined in ***tx_user.h** _ are applied only if the application and ThreadX library are built with _ *TX_INCLUDE_USER_DEFINE_FILE** defined.*</span></span>

### <a name="smallest-configuration"></a><span data-ttu-id="cd4e1-178">Configuración más pequeña</span><span class="sxs-lookup"><span data-stu-id="cd4e1-178">Smallest Configuration</span></span>

<span data-ttu-id="cd4e1-179">Para obtener el tamaño de código más pequeño, se deben tener en cuenta las siguientes opciones de configuración de ThreadX (en ausencia de todas las demás opciones).</span><span class="sxs-lookup"><span data-stu-id="cd4e1-179">For the smallest code size, the following ThreadX configuration options should be considered (in absence of all other options).</span></span>

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a><span data-ttu-id="cd4e1-180">Configuración más rápida</span><span class="sxs-lookup"><span data-stu-id="cd4e1-180">Fastest Configuration</span></span>

<span data-ttu-id="cd4e1-181">Para lograr la ejecución más rápida, se han utilizado las mismas opciones de configuración que para la configuración más pequeña anterior, pero también se han tenido en cuenta estas opciones.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-181">For the fastest execution, the same configuration options used for the Smallest Configuration previously, but with these options also considered.</span></span>

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

<span data-ttu-id="cd4e1-182">Más adelante se describen las [opciones de configuración detalladas](#detailed-configuration-options).</span><span class="sxs-lookup"><span data-stu-id="cd4e1-182">[Detailed configuration options](#detailed-configuration-options) are described.</span></span>

### <a name="global-time-source"></a><span data-ttu-id="cd4e1-183">Origen de hora global</span><span class="sxs-lookup"><span data-stu-id="cd4e1-183">Global Time Source</span></span>

<span data-ttu-id="cd4e1-184">Para otros productos de Microsoft Azure RTOS (FileX, NetX, GUIX, USBX, etc.), ThreadX define el número de tics del temporizador de ThreadX que representa un segundo.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-184">For other Microsoft Azure RTOS products (FileX, NetX, GUIX, USBX, etc.), ThreadX defines the number of ThreadX timer ticks that represents one second.</span></span> <span data-ttu-id="cd4e1-185">El resto deriva sus requisitos de hora en función de esta constante.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-185">Others derive their time requirements based on this constant.</span></span> <span data-ttu-id="cd4e1-186">De manera predeterminada, el valor es 100, suponiendo una interrupción periódica de 10 ms.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-186">By default, the value is 100, assuming a 10ms periodic interrupt.</span></span> <span data-ttu-id="cd4e1-187">El usuario puede invalidar este valor mediante la definición de TX_TIMER_TICKS_PER_SECOND con el valor deseado en ***tx_port.h*** o en el IDE o en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-187">The user may override this value by defining TX_TIMER_TICKS_PER_SECOND with the desired value in ***tx_port.h*** or within the IDE or command line.</span></span>

### <a name="detailed-configuration-options"></a><span data-ttu-id="cd4e1-188">Opciones de configuración detalladas</span><span class="sxs-lookup"><span data-stu-id="cd4e1-188">Detailed Configuration Options</span></span>

<span data-ttu-id="cd4e1-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="cd4e1-190">Cuando se define, esta opción habilita la recopilación de información de rendimiento sobre los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-190">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="cd4e1-191">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-191">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="cd4e1-193">Cuando se define, esta opción habilita la recopilación de información de rendimiento sobre los grupos de bytes.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-193">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="cd4e1-194">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-194">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-195">**TX_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-195">**TX_DISABLE_ERROR_CHECKING**</span></span>

<span data-ttu-id="cd4e1-196">Omite la comprobación de errores de llamada de servicio básica.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-196">Bypasses basic service call error checking.</span></span> <span data-ttu-id="cd4e1-197">Cuando se define en el código fuente de la aplicación, todas las comprobaciones de errores de parámetros básicas están deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-197">When defined in the application source, all basic parameter error checking is disabled.</span></span> <span data-ttu-id="cd4e1-198">Esto puede mejorar el rendimiento hasta un 30 % y también puede reducir el tamaño de la imagen.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-198">This may improve performance by as much as 30% and may also reduce the image size.</span></span>

> [!NOTE]
> <span data-ttu-id="cd4e1-199">*Solo es seguro deshabilitar la comprobación de errores si la aplicación puede garantizar absolutamente que todos los parámetros de entrada siempre son válidos en todas las circunstancias, incluidos los parámetros de entrada derivados de la entrada externa. Si se proporciona una entrada no válida a la API con la comprobación de errores deshabilitada, el comportamiento resultante es indefinido y podría provocar datos dañados en la memoria o el bloqueo del sistema.*</span><span class="sxs-lookup"><span data-stu-id="cd4e1-199">*It is only safe to disable error checking if the application can absolutely guarantee all input parameters are always valid under all circumstances, including input parameters derived from external input. If invalid input is supplied to the API with error checking disabled, the resulting behavior is undefined and could result in memory corruption or system crash.*</span></span>

> [!NOTE]
> <span data-ttu-id="cd4e1-200">*Los valores devueltos por la API de ThreadX que no se ven afectados por la deshabilitación de la comprobación de errores se muestran en negrita en la sección "Valores devueltos" de cada descripción de API en el capítulo 4. Los valores devueltos que no están en negrita son nulos si la comprobación de errores está deshabilitada mediante la opción TX_DISABLE_ERROR_CHECKING.*</span><span class="sxs-lookup"><span data-stu-id="cd4e1-200">*ThreadX API return values not affected by disabling error checking are listed in bold in the “Return Values” section of each API description in Chapter 4. The nonbold return values are void if error checking is disabled by using the TX_DISABLE_ERROR_CHECKING option.*</span></span>

<span data-ttu-id="cd4e1-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span></span>

<span data-ttu-id="cd4e1-202">Cuando se define, deshabilita las devoluciones de llamada de notificación para varios objetos de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-202">When defined, disables the notify callbacks for various ThreadX objects.</span></span> <span data-ttu-id="cd4e1-203">El uso de esta opción reduce ligeramente el tamaño del código y mejora el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-203">Using this option slightly reduces code size and improves performance.</span></span> <span data-ttu-id="cd4e1-204">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-204">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span></span>

<span data-ttu-id="cd4e1-206">Cuando se define, deshabilita la característica de umbral de adelantamiento y reduce ligeramente el tamaño del código y mejora el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-206">When defined, disables the preemption-threshold feature and slightly reduces code size and improves performance.</span></span> <span data-ttu-id="cd4e1-207">Por supuesto, las funcionalidades de umbral de adelantamiento ya no están disponibles.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-207">Of course, the preemption-threshold capabilities are no longer available.</span></span> <span data-ttu-id="cd4e1-208">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-208">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-209">**TX_DISABLE_REDUNDANT_CLEARING**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-209">**TX_DISABLE_REDUNDANT_CLEARING**</span></span>

<span data-ttu-id="cd4e1-210">Cuando se define, quita la lógica para inicializar con ceros las estructuras de datos globales de C de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-210">When defined, removes the logic for initializing ThreadX global C data structures to zero.</span></span> <span data-ttu-id="cd4e1-211">Solo se debe usar si el código de inicialización del compilador establece todos los datos globales de C no inicializados en cero.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-211">This should only be used if the compiler's initialization code sets all un-initialized C global data to zero.</span></span> <span data-ttu-id="cd4e1-212">El uso de esta opción reduce ligeramente el tamaño del código y mejora el rendimiento durante la inicialización.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-212">Using this option slightly reduces code size and improves performance during initialization.</span></span> <span data-ttu-id="cd4e1-213">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-213">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-214">**TX_DISABLE_STACK_FILLING**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-214">**TX_DISABLE_STACK_FILLING**</span></span>

<span data-ttu-id="cd4e1-215">Cuando se define, deshabilita el establecimiento del valor 0xEF en cada byte de la pila de cada subproceso cuando se crea.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-215">When defined, disables placing the 0xEF value in each byte of each thread's stack when created.</span></span> <span data-ttu-id="cd4e1-216">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-216">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-217">**TX_ENABLE_EVENT_TRACE**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-217">**TX_ENABLE_EVENT_TRACE**</span></span>

<span data-ttu-id="cd4e1-218">Cuando se define, ThreadX habilita el código de recopilación de eventos para crear un búfer de seguimiento de TraceX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-218">When defined, ThreadX enables the event gathering code for creating a TraceX trace buffer.</span></span>

<span data-ttu-id="cd4e1-219">**TX_ENABLE_STACK_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-219">**TX_ENABLE_STACK_CHECKING**</span></span>

<span data-ttu-id="cd4e1-220">Cuando se define, habilita la comprobación de la pila en tiempo de ejecución de ThreadX, que incluye el análisis de la parte de la pila que se ha usado y el examen de las "barreras" del patrón de datos antes y después del área de pila.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-220">When defined, enables ThreadX run-time stack checking, which includes analysis of how much stack has been used and examination of data pattern "fences" before and after the stack area.</span></span> <span data-ttu-id="cd4e1-221">Si se detecta un error en la pila, se llama al controlador de errores de la pila de la aplicación registrado.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-221">If a stack error is detected, the registered application stack error handler is called.</span></span> <span data-ttu-id="cd4e1-222">Esta opción da como resultado una sobrecarga y un tamaño de código ligeramente mayores.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-222">This option does result in slightly increased overhead and code size.</span></span> <span data-ttu-id="cd4e1-223">Consulte la función de la API ***tx_thread_stack_error_notify*** para más información.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-223">Review the ***tx_thread_stack_error_notify*** API function for more information.</span></span> <span data-ttu-id="cd4e1-224">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-224">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="cd4e1-226">Cuando se define, habilita la recopilación de información de rendimiento sobre los grupos de marcas de eventos.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-226">When defined, enables the gathering of performance information on event flags groups.</span></span> <span data-ttu-id="cd4e1-227">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-227">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span></span>

<span data-ttu-id="cd4e1-229">Cuando se define, ThreadX mejora las llamadas a las API ***tx_thread_resume** _ y _ *_tx_thread_suspend_** mediante código en línea.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-229">When defined, ThreadX improves the ***tx_thread_resume** _ and _ *_tx_thread_suspend_** API calls via in-line code.</span></span> <span data-ttu-id="cd4e1-230">Esto aumenta el tamaño del código, pero mejora el rendimiento de estas dos llamadas de API.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-230">This increases code size but enhances performance of these two API calls.</span></span>

<span data-ttu-id="cd4e1-231">**TX_MAX_PRIORITIES**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-231">**TX_MAX_PRIORITIES**</span></span>

<span data-ttu-id="cd4e1-232">Define los niveles de prioridad de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-232">Defines the priority levels for ThreadX.</span></span> <span data-ttu-id="cd4e1-233">Los valores válidos van de 32 a 1024 (ambos incluidos) y *deben* ser divisibles por 32.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-233">Legal values range from 32 through 1024 (inclusive) and *must* be evenly divisible by 32.</span></span> <span data-ttu-id="cd4e1-234">El incremento del número de niveles de prioridad admitidos aumenta el uso de RAM en 128 bytes por cada grupo de 32 prioridades.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-234">Increasing the number of priority levels supported increases the RAM usage by 128 bytes for every group of 32 priorities.</span></span> <span data-ttu-id="cd4e1-235">Sin embargo, solo tiene un efecto insignificante en el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-235">However, there is only a negligible effect on performance.</span></span> <span data-ttu-id="cd4e1-236">De manera predeterminada, este valor se establece en 32 niveles de prioridad.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-236">By default, this value is set to 32 priority levels.</span></span>

<span data-ttu-id="cd4e1-237">**TX_MINIMUM_STACK**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-237">**TX_MINIMUM_STACK**</span></span>

<span data-ttu-id="cd4e1-238">Define el tamaño mínimo de la pila (en bytes).</span><span class="sxs-lookup"><span data-stu-id="cd4e1-238">Defines the minimum stack size (in bytes).</span></span> <span data-ttu-id="cd4e1-239">Se utiliza para la comprobación de errores cuando se crean subprocesos.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-239">It is used for error checking when threads are created.</span></span> <span data-ttu-id="cd4e1-240">El valor predeterminado es específico de la distribución y se encuentra en ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-240">The default value is port-specific and is found in ***tx_port.h***.</span></span>

<span data-ttu-id="cd4e1-241">**TX_MISRA_ENABLE**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-241">**TX_MISRA_ENABLE**</span></span>

<span data-ttu-id="cd4e1-242">Cuando se define, ThreadX emplea convenciones compatibles con MISRA C.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-242">When defined, ThreadX utilizes MISRA C compliant conventions.</span></span> <span data-ttu-id="cd4e1-243">Consulte ***ThreadX_MISRA_Compliance.pdf*** para más información.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-243">Refer to  ***ThreadX_MISRA_Compliance.pdf*** for details.</span></span>

<span data-ttu-id="cd4e1-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="cd4e1-245">Cuando se define, habilita la recopilación de información de rendimiento sobre las exclusiones mutuas.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-245">When defined, enables the gathering of performance information on mutexes.</span></span> <span data-ttu-id="cd4e1-246">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-246">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-247">**TX_NO_TIMER**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-247">**TX_NO_TIMER**</span></span>

<span data-ttu-id="cd4e1-248">Cuando se define, la lógica del temporizador de ThreadX está completamente deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-248">When defined, the ThreadX timer logic is completely disabled.</span></span> <span data-ttu-id="cd4e1-249">Esto resulta útil en los casos en los que no se usan las características de temporizador de ThreadX (suspensión de un subproceso, tiempos de espera de API, segmentación de tiempo y temporizadores de aplicación).</span><span class="sxs-lookup"><span data-stu-id="cd4e1-249">This is useful in cases where the ThreadX timer features (thread sleep, API timeouts, time-slicing, and application timers) are not utilized.</span></span> <span data-ttu-id="cd4e1-250">Si se especifica **TX_NO_TIMER**, también se debe definir la opción **TX_TIMER_PROCESS_IN_ISR**.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-250">If **TX_NO_TIMER** is specified, the option **TX_TIMER_PROCESS_IN_ISR** must also be defined.</span></span>

<span data-ttu-id="cd4e1-251">**TX_NOT_INTERRUPTABLE**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-251">**TX_NOT_INTERRUPTABLE**</span></span>

<span data-ttu-id="cd4e1-252">Cuando se define, ThreadX no intenta minimizar el tiempo de bloqueo de una interrupción.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-252">When defined, ThreadX does not attempt to minimize interrupt lockout time.</span></span> <span data-ttu-id="cd4e1-253">Esto da como resultado una ejecución más rápida, pero aumenta ligeramente el tiempo de bloqueo de las interrupciones.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-253">This results in faster execution but does slightly increase interrupt lockout time.</span></span>

<span data-ttu-id="cd4e1-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="cd4e1-255">Cuando se define, habilita la recopilación de información de rendimiento sobre las colas.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-255">When defined, enables the gathering of performance information on queues.</span></span> <span data-ttu-id="cd4e1-256">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-256">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-257">**TX_REACTIVATE_INLINE**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-257">**TX_REACTIVATE_INLINE**</span></span>

<span data-ttu-id="cd4e1-258">Cuando se define, realiza la reactivación de los temporizadores de ThreadX insertados en lugar de usar una llamada de función.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-258">When defined, performs reactivation of ThreadX timers inline instead of using a function call.</span></span> <span data-ttu-id="cd4e1-259">Esto mejora el rendimiento, pero aumenta ligeramente el tamaño del código.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-259">This improves performance but slightly increases code size.</span></span> <span data-ttu-id="cd4e1-260">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-260">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="cd4e1-262">Cuando se define, habilita la recopilación de información de rendimiento sobre los semáforos.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-262">When defined, enables the gathering of performance information on semaphores.</span></span> <span data-ttu-id="cd4e1-263">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-263">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="cd4e1-265">Cuando se define, habilita la recopilación de información de rendimiento sobre los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-265">When defined, enables the gathering of performance information on threads.</span></span> <span data-ttu-id="cd4e1-266">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-266">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="cd4e1-268">Cuando se define, habilita la recopilación de información de rendimiento sobre los temporizadores.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-268">When defined, enables the gathering of performance information on timers.</span></span> <span data-ttu-id="cd4e1-269">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-269">By default, this option is not defined.</span></span>

<span data-ttu-id="cd4e1-270">**TX_TIMER_PROCESS_IN_ISR**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-270">**TX_TIMER_PROCESS_IN_ISR**</span></span>

<span data-ttu-id="cd4e1-271">Cuando se define, elimina el subproceso interno del temporizador del sistema para ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-271">When defined, eliminates the internal system timer thread for ThreadX.</span></span> <span data-ttu-id="cd4e1-272">Esto da como resultado un rendimiento mejorado en los eventos del temporizador y requisitos de RAM más pequeños porque ya no se necesitan la pila del temporizador y el bloque de control.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-272">This results in improved performance on timer events and smaller RAM requirements because the timer stack and control block are no longer needed.</span></span> <span data-ttu-id="cd4e1-273">Sin embargo, el uso de esta opción mueve todo el procesamiento de la expiración del temporizador al nivel de ISR del temporizador.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-273">However, using this option moves all the timer expiration processing to the timer ISR level.</span></span> <span data-ttu-id="cd4e1-274">De manera predeterminada, esta opción no está definida.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-274">By default, this option is not defined.</span></span>

> [!NOTE]
> <span data-ttu-id="cd4e1-275">*Es posible que los servicios permitidos desde los temporizadores no se permitan desde ISR y, por lo tanto, no se permitan al usar esta opción.*</span><span class="sxs-lookup"><span data-stu-id="cd4e1-275">*Services allowed from timers may not be allowed from ISRs and thus might not be allowed when using this option.*</span></span>

<span data-ttu-id="cd4e1-276">**TX_TIMER_THREAD_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-276">**TX_TIMER_THREAD_PRIORITY**</span></span>

<span data-ttu-id="cd4e1-277">Define la prioridad del subproceso interno del temporizador del sistema de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-277">Defines the priority of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="cd4e1-278">El valor predeterminado es prioridad 0, la prioridad más alta en ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-278">The default value is priority 0—the highest priority in ThreadX.</span></span> <span data-ttu-id="cd4e1-279">El valor predeterminado se define en ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-279">The default value is defined in ***tx_port.h***.</span></span>

<span data-ttu-id="cd4e1-280">**TX_TIMER_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="cd4e1-280">**TX_TIMER_THREAD_STACK_SIZE**</span></span>

<span data-ttu-id="cd4e1-281">Define el tamaño de la pila (en bytes) del subproceso interno del temporizador del sistema de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-281">Defines the stack size (in bytes) of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="cd4e1-282">Este subproceso procesa todas las solicitudes de suspensión de subprocesos, así como todos los tiempos de espera de las llamadas de servicio.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-282">This thread processes all thread sleep requests as well as all service call timeouts.</span></span> <span data-ttu-id="cd4e1-283">Además, todas las rutinas de devolución de llamada del temporizador de la aplicación se invocan desde este contexto.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-283">In addition, all application timer callback routines are invoked from this context.</span></span> <span data-ttu-id="cd4e1-284">El valor predeterminado es específico de la distribución y se encuentra en ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-284">The default value is port-specific and is found in ***tx_port.h***.</span></span>

## <a name="threadx-version-id"></a><span data-ttu-id="cd4e1-285">Identificador de versión de ThreadX</span><span class="sxs-lookup"><span data-stu-id="cd4e1-285">ThreadX Version ID</span></span>

<span data-ttu-id="cd4e1-286">El programador puede obtener la versión de ThreadX mediante el examen del archivo \***tx_port.h** _.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-286">The programmer can obtain the ThreadX version from examination of the \***tx_port.h** _ file.</span></span> <span data-ttu-id="cd4e1-287">Además, este archivo también contiene un historial de versiones de la distribución correspondiente.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-287">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="cd4e1-288">El software de la aplicación puede obtener la versión de ThreadX mediante el examen de la cadena global _\*_tx_version_id\*\*.</span><span class="sxs-lookup"><span data-stu-id="cd4e1-288">Application software can obtain the ThreadX version by examining the global string _\*_tx_version_id\*\*.</span></span>
