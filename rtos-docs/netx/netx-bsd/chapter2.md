---
title: 'Capítulo 2: Instalación y uso de BSD de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente BSD de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7539565ccd4956c5354be45000efab8318dc606c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815282"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a><span data-ttu-id="9eaa3-103">Capítulo 2: Instalación y uso de BSD de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="9eaa3-103">Chapter 2 - Installation and Use of Azure RTOS NetX BSD</span></span>

<span data-ttu-id="9eaa3-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente BSD de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="9eaa3-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="9eaa3-105">Product Distribution</span></span>

<span data-ttu-id="9eaa3-106">El componente BSD de Azure RTOS NetX se puede obtener desde nuestro repositorio de código fuente público en [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span><span class="sxs-lookup"><span data-stu-id="9eaa3-106">Azure RTOS NetX BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="9eaa3-107">El paquete incluye dos archivos de código fuente y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="9eaa3-108">**nx_bsd.h**: archivo de encabezado para BSD de NetX</span><span class="sxs-lookup"><span data-stu-id="9eaa3-108">**nx_bsd.h**: Header file for NetX BSD</span></span>
- <span data-ttu-id="9eaa3-109">**nx_bsd.c**: archivo de código fuente C para BSD de NetX</span><span class="sxs-lookup"><span data-stu-id="9eaa3-109">**nx_bsd.c**: C Source file for NetX BSD</span></span>
- <span data-ttu-id="9eaa3-110">**nx_bsd.pdf**: guía de usuario para BSD de NetX</span><span class="sxs-lookup"><span data-stu-id="9eaa3-110">**nx_bsd.pdf**: User Guide for NetX BSD</span></span>

<span data-ttu-id="9eaa3-111">Archivos de demostración:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-111">Demo files:</span></span>
- <span data-ttu-id="9eaa3-112">**bsd_demo_tcp.c**</span><span class="sxs-lookup"><span data-stu-id="9eaa3-112">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="9eaa3-113">**bsd_demo_udp.c**</span><span class="sxs-lookup"><span data-stu-id="9eaa3-113">**bsd_demo_udp.c**</span></span>

## <a name="netx-bsd-installation"></a><span data-ttu-id="9eaa3-114">Instalación de BSD de NetX</span><span class="sxs-lookup"><span data-stu-id="9eaa3-114">NetX BSD Installation</span></span>

<span data-ttu-id="9eaa3-115">Para usar BSD de NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-115">In order to use NetX BSD the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="9eaa3-116">Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_bsd.h* y *nx_bsd.c* deben copiarse en ese mismo directorio.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-116">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_bsd.h* and *nx_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a><span data-ttu-id="9eaa3-117">Compilación de los componentes ThreadX y NetX de una aplicación BSD</span><span class="sxs-lookup"><span data-stu-id="9eaa3-117">Building the ThreadX and NetX components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="9eaa3-118">ThreadX</span><span class="sxs-lookup"><span data-stu-id="9eaa3-118">ThreadX</span></span>

<span data-ttu-id="9eaa3-119">La biblioteca de ThreadX debe definir *bsd_errno* en el almacenamiento local para el subproceso.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-119">The ThreadX library must define *bsd_errno* in the thread local storage.</span></span> <span data-ttu-id="9eaa3-120">Se recomienda el siguiente procedimiento:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-120">We recommend the following procedure:</span></span>

1. <span data-ttu-id="9eaa3-121">En *tx_port.h*, establezca una de las macros TX_THREAD_EXTENSION como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-121">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. <span data-ttu-id="9eaa3-122">Recompile la biblioteca de ThreadX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-122">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="9eaa3-123">Si TX_THREAD_EXTENSION_3 ya está en uso, el usuario puede utilizar una de las otras macros TX_THREAD_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-123">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx"></a><span data-ttu-id="9eaa3-124">NetX</span><span class="sxs-lookup"><span data-stu-id="9eaa3-124">NetX</span></span>

<span data-ttu-id="9eaa3-125">Antes de usar los servicios de BSD de NetX, la biblioteca de NetX debe compilarse con NX_ENABLE_EXTENDED_NOTIFY_SUPPORT definido (por ejemplo, en *nx_user.h*).</span><span class="sxs-lookup"><span data-stu-id="9eaa3-125">Before using NetX BSD Services, the NetX library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined (e.g. in *nx_user.h*).</span></span> <span data-ttu-id="9eaa3-126">De forma predeterminada, no está definido.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-126">By default it is not defined.</span></span>

## <a name="using-netx-bsd"></a><span data-ttu-id="9eaa3-127">Uso de BSD de NetX</span><span class="sxs-lookup"><span data-stu-id="9eaa3-127">Using NetX BSD</span></span>

<span data-ttu-id="9eaa3-128">El uso de BSD para NetX es sencillo.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-128">Using BSD for NetX is easy.</span></span> <span data-ttu-id="9eaa3-129">Básicamente, el código de la aplicación debe incluir *nx_bsd.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-129">Basically, the application code must include *nx_bsd.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="9eaa3-130">Una vez que se incluye *nx_bsd.h*, el código de aplicación puede usar los servicios BSD especificados más adelante en este manual.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-130">Once *nx_bsd.h* is included, the application code is then able to use the BSD services specified later in this guide.</span></span> <span data-ttu-id="9eaa3-131">La aplicación también debe incluir *nx_bsd.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-131">The application must also include *nx_bsd.c* in the build process.</span></span> <span data-ttu-id="9eaa3-132">Este archivo se debe compilar de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="9eaa3-133">Esto es todo lo que se necesita para usar BSD de NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-133">This is all that is required to use NetX BSD.</span></span>

<span data-ttu-id="9eaa3-134">Para utilizar los servicios BSD de NetX, la aplicación debe crear una instancia de IP, un grupo de paquetes e inicializar los servicios BSD mediante llamadas a *bsd_initialize.*</span><span class="sxs-lookup"><span data-stu-id="9eaa3-134">To utilize NetX BSD services, the application must create an IP instance, a packet pool, and initialize BSD services by calling *bsd_initialize.*</span></span> <span data-ttu-id="9eaa3-135">Esto se muestra en la sección "Ejemplo pequeño" más adelante en este manual.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-135">This is demonstrated in the "Small Example" section later in this guide.</span></span> <span data-ttu-id="9eaa3-136">El prototipo se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-136">The prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

<span data-ttu-id="9eaa3-137">Los tres últimos parámetros se usan para crear un subproceso para realizar tareas periódicas, como comprobar los eventos TCP y definir el espacio de pila del subproceso.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-137">The last three parameters are used for creating a thread for performing periodic tasks such as checking for TCP events and define the thread stack space.</span></span>

> [!NOTE]
> <span data-ttu-id="9eaa3-138">A diferencia de los sockets BSD, que funcionan en la red por orden, NetX funciona por orden de bytes del host del procesador del host.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-138">In contrast to BSD sockets, which work in network bye order, NetX works in the host byte order of the host processor.</span></span> <span data-ttu-id="9eaa3-139">Por motivos de compatibilidad de código fuente, se han definido las macros htons(), ntohs(), htonl() y ntohl(), pero no se modifica el argumento pasado.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-139">For source compatibility reasons, the macros htons(), ntohs(), htonl(), ntohl() have been defined, but do not modify the argument passed.</span></span>

## <a name="netx-bsd-limitations"></a><span data-ttu-id="9eaa3-140">Limitaciones de BSD de NetX</span><span class="sxs-lookup"><span data-stu-id="9eaa3-140">NetX BSD Limitations</span></span>

<span data-ttu-id="9eaa3-141">Debido a problemas de rendimiento y arquitectura, BSD de NetX no admite todas las características de sockets de BSD 4.3:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-141">Due to performance and architecture issues, NetX BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="9eaa3-142">Las marcas INT no se admiten para las llamadas a *send, recv, sendto* y *recvfrom*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-142">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="netx-bsd-with-dns-support"></a><span data-ttu-id="9eaa3-143">Compatibilidad de BSD de NetX con DNS</span><span class="sxs-lookup"><span data-stu-id="9eaa3-143">NetX BSD with DNS Support</span></span>

<span data-ttu-id="9eaa3-144">Si se define NX_BSD_ENABLE_DNS, NetX BDS puede enviar consultas de DNS para obtener la información de la IP del host o el nombre del host.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-144">If NX_BSD_ENABLE_DNS is defined, NetX BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="9eaa3-145">Esta característica requiere que se cree previamente un cliente NetX DNS con el servicio *nx_dns_create*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-145">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="9eaa3-146">Una o varias direcciones IP de servidor DNS conocidas deben registrarse con la instancia de DNS mediante *nx_dns_server_add* para agregar direcciones de servidor.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-146">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* for adding server addresses.</span></span>

<span data-ttu-id="9eaa3-147">Los servicios DNS y la asignación de memoria se usan en los servicios *getaddrinfo* y *getnameinfo*:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-147">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="9eaa3-148">Cuando la aplicación BSD llama a *getaddrinfo* con un nombre de host, BSD de NetX llamará a cualquiera de los servicios siguientes para obtener la dirección IP:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-148">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="9eaa3-149">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="9eaa3-149">nx_dns_ipv4_address_by_name_get</span></span>
- <span data-ttu-id="9eaa3-150">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="9eaa3-150">nx_dns_cname_get</span></span>

<span data-ttu-id="9eaa3-151">Para *nx_dns_ipv4_address_by_name_get*, BSD de NetX usa las áreas de memoria ipv4_addr_buffer.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-151">For *nx_dns_ipv4_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer memory areas.</span></span> <span data-ttu-id="9eaa3-152">El tamaño de estos búferes se define mediante (`NX_BSD_IPV4_ADDR_PER_HOST * 4`).</span><span class="sxs-lookup"><span data-stu-id="9eaa3-152">The size of these buffers are defined by (`NX_BSD_IPV4_ADDR_PER_HOST * 4`).</span></span>

<span data-ttu-id="9eaa3-153">Para devolver información de dirección de *getaddrinfo*, BSD de NetX usa la tabla de memoria de bloques de ThreadX *nx_bsd_addrinfo_pool_memory*, cuya área de memoria está definida por otro conjunto de opciones configurables, *NX_BSD_IPV4_ADDR_MAX_NUM*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-153">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table *nx_bsd_addrinfo_pool_memory*, whose memory area is defined by another set of configurable options, *NX_BSD_IPV4_ADDR_MAX_NUM*.</span></span>

<span data-ttu-id="9eaa3-154">Consulte las **Opciones de configuración** para obtener más detalles sobre las opciones de configuración anteriores.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-154">See **Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="9eaa3-155">Además, si se define NX_DNS_ENABLE_EXTENDED_RR_TYPES y la entrada del host es un nombre canónico, BSD de NetX asignará dinámicamente la memoria de un grupo de bloques *_nx_bsd_cname_block_pool* creado previamente.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-155">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX BSD will allocate memory dynamically from a previously created block pool *_nx_bsd_cname_block_pool*</span></span>

> [!NOTE]
> <span data-ttu-id="9eaa3-156">Después de llamar a *getaddrinfo*, la aplicación BSD es responsable de volver a liberar la memoria a la que apunta el argumento res de vuelta a la tabla de bloque mediante el servicio *freeaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-156">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="9eaa3-157">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="9eaa3-157">Configuration Options</span></span>

<span data-ttu-id="9eaa3-158">Las opciones configurables por el usuario en *nx_bsd.h* permiten a la aplicación ajustar los sockets de BSD de NetX para sus requisitos de la aplicación concretos.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-158">User configurable options in *nx_bsd.h* allow the application to fine tune NetX BSD sockets for its particular requirements.</span></span> <span data-ttu-id="9eaa3-159">A continuación, se muestra una lista de estos parámetros:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-159">The following is a list of these parameters:</span></span>

- <span data-ttu-id="9eaa3-160">**NX_BSD_TCP_WINDOW**: se usa en llamadas de creación de sockets TCP.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-160">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="9eaa3-161">65535 es un tamaño de ventana típico de Ethernet de 100 Mb.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-161">65535 is a typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="9eaa3-162">El valor predeterminado es 65535.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-162">The default value is 65535.</span></span>
- <span data-ttu-id="9eaa3-163">**NX_BSD_SOCKFD_START**: este es el índice lógico del valor de inicio del descriptor de archivo de socket BSD.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-163">**NX_BSD_SOCKFD_START** This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="9eaa3-164">De forma predeterminada, esta opción es 32.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-164">By default this option is 32.</span></span>
- <span data-ttu-id="9eaa3-165">**NX_BSD_MAX_SOCKETS**: especifica el número máximo de sockets totales disponibles en la capa BSD y debe ser un múltiplo de 32. El valor predeterminado es 32.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-165">**NX_BSD_MAX_SOCKETS** Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.The value is defaulted to 32.</span></span>
- <span data-ttu-id="9eaa3-166">**NX_BSD_SOCKET_QUEUE_MAX**: especifica el número máximo de paquetes UDP almacenados en la cola de sockets de recepción.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-166">**NX_BSD_SOCKET_QUEUE_MAX** Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="9eaa3-167">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-167">The value is defaulted to 5.</span></span>
- <span data-ttu-id="9eaa3-168">**NX_BSD_MAX_LISTEN_BACKLOG**: especifica el tamaño de la cola de escucha ("trabajo pendiente") para los sockets TCP de BSD.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-168">**NX_BSD_MAX_LISTEN_BACKLOG** This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="9eaa3-169">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-169">The default value is 5.</span></span>
- <span data-ttu-id="9eaa3-170">**NX_MICROSECOND_PER_CPU_TICK**: especifica el número de microsegundos por cada interrupción del temporizador.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-170">**NX_MICROSECOND_PER_CPU_TICK** Specifies the number of microseconds per timer interrupt</span></span>
- <span data-ttu-id="9eaa3-171">**NX_BSD_TIMEOUT**: especifica el tiempo de espera en tics de temporizador requerido por BSD en las llamadas internas de NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-171">**NX_BSD_TIMEOUT** Specifies the timeout in timer ticks on NetX internal calls required by BSD.</span></span> <span data-ttu-id="9eaa3-172">El valor predeterminado es 20\*NX_IP_PERIODIC_RATE.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-172">The default value is 20\*NX_IP_PERIODIC_RATE.</span></span>
- <span data-ttu-id="9eaa3-173">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: especifica el tiempo de espera en tics de temporizador en la llamada de desconexión de NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-173">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX disconnect call.</span></span> <span data-ttu-id="9eaa3-174">El valor predeterminado es 1.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-174">The default value is 1.</span></span>
- <span data-ttu-id="9eaa3-175">**NX_BSD_PRINT_ERRORS**: si se establece, el estado de error devuelto de una función BSD devuelve un número de línea y un tipo de error, por ejemplo NX_SOC_ERROR, donde se produce el error.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-175">**NX_BSD_PRINT_ERRORS** If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="9eaa3-176">Esto requiere que el desarrollador de la aplicación defina la salida de la depuración.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-176">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="9eaa3-177">La configuración predeterminada está deshabilitada y no se especifica ninguna salida en *nx_bsd.h*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-177">The default setting is disabled and no debug output is specified in *nx_bsd.h*</span></span>
- <span data-ttu-id="9eaa3-178">**NX_BSD_TIMER_RATE**: intervalo después del cual se ejecuta la tarea de temporizador periódica de BSD.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-178">**NX_BSD_TIMER_RATE** Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="9eaa3-179">El valor predeterminado es 1 segundo (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="9eaa3-179">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="9eaa3-180">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: si se establece, esta opción permite que el proceso de tiempo de espera de BSD se ejecute en el contexto del temporizador del sistema.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-180">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER** If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="9eaa3-181">De forma predeterminada está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-181">The default behavior is disabled.</span></span> <span data-ttu-id="9eaa3-182">Esta característica se describe con más detalle en el capítulo 2 "Instalación y uso de BSD de NetX".</span><span class="sxs-lookup"><span data-stu-id="9eaa3-182">This feature is described in more detail in Chapter 2 "Installation and Use of NetX BSD".</span></span>
- <span data-ttu-id="9eaa3-183">**NX_BSD_ENABLE_DNS**: si esta opción está habilitada, BSD de NetX enviará una consulta de DNS para un nombre de host o una dirección IP de host.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-183">**NX_BSD_ENABLE_DNS** If enabled, NetX BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="9eaa3-184">Requiere que se cree e inicie previamente una instancia de cliente DNS.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-184">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="9eaa3-185">De forma predeterminada, no está habilitada.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-185">By default it is not enabled.</span></span>
- <span data-ttu-id="9eaa3-186">**NX_BSD_IPV4_ADDR_MAX_NUM**: número máximo de direcciones IPv4 devueltas por *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-186">**NX_BSD_IPV4_ADDR_MAX_NUM** Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="9eaa3-187">Esto, junto con NX_BSD_IPV4_ADDR_MAX_NUM, define el tamaño del grupo de bloques BSD de NetX nx_bsd_addrinfo_block_pool para asignar memoria de forma dinámica para el almacenamiento de información de direcciones en *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-187">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="9eaa3-188">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-188">The default value is 5.</span></span>
- <span data-ttu-id="9eaa3-189">**NX_BSD_IPV4_ADDR_PER_HOST**: define el número máximo de direcciones IPv4 almacenadas por consulta de DNS.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-189">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="9eaa3-190">El valor predeterminado es 5.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-190">The default value is 5.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="9eaa3-191">Opciones de socket BSD</span><span class="sxs-lookup"><span data-stu-id="9eaa3-191">BSD Socket Options</span></span>

<span data-ttu-id="9eaa3-192">La siguiente lista de opciones de socket BSD de NetX se puede habilitar (o deshabilitar) en tiempo de ejecución por socket mediante el servicio *setsockopt*:</span><span class="sxs-lookup"><span data-stu-id="9eaa3-192">The following list of NetX BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

<span data-ttu-id="9eaa3-193">Hay dos configuraciones diferentes para *option_level*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-193">There are two different settings for *option_level*.</span></span>

<span data-ttu-id="9eaa3-194">El primer tipo de opciones de socket en tiempo de ejecución es SOL_SOCKET para las opciones de nivel de socket.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-194">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="9eaa3-195">Para habilitar una opción de nivel de socket es necesario llamar a *setsockopt* con option_level establecido en SOL_SOCKET y option_name establecido en la opción específica, por ejemplo, SO_BROADCAST.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-195">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST.</span></span> <span data-ttu-id="9eaa3-196">Para recuperar una configuración de opción, es necesario llamar a *getsockopt* para option_name con option_level de nuevo establecido en SOL_SOCKET.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-196">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="9eaa3-197">A continuación se muestra la lista de opciones de nivel de socket en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-197">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="9eaa3-198">**SO_BROADCAST**: si se establece, habilita el envío y la recepción de paquetes de difusión de sockets NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-198">**SO_BROADCAST**: If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="9eaa3-199">Este es el comportamiento predeterminado para NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-199">This is the default behavior for NetX.</span></span> <span data-ttu-id="9eaa3-200">Todos los sockets tienen esta capacidad.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-200">All sockets have this capability.</span></span>
- <span data-ttu-id="9eaa3-201">**SO_ERROR**: se usa para obtener el estado del socket en la operación de socket anterior del socket especificado, mediante el servicio *getsockopt*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-201">**SO_ERROR**: Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="9eaa3-202">Todos los sockets tienen esta capacidad.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-202">All sockets have this capability.</span></span>
- <span data-ttu-id="9eaa3-203">**SO_KEEPALIVE**: si se establece, habilita la característica de mantenimiento de conexión TCP.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-203">**SO_KEEPALIVE**: If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="9eaa3-204">Esto requiere que la biblioteca de NetX se compile con NX_TCP_ENABLE_KEEPALIVE definido en *nx_user.h*.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-204">This requires the NetX library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="9eaa3-205">Esta característica está deshabilitada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-205">By default this feature is disabled.</span></span>
- <span data-ttu-id="9eaa3-206">**SO_RCVTIMEO**: establece la opción de espera en segundos para recibir paquetes en sockets de BSD de NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-206">**SO_RCVTIMEO**: This sets the wait option in seconds for receiving packets on NetX BSD sockets.</span></span> <span data-ttu-id="9eaa3-207">El valor predeterminado es NX_WAIT_FOREVER (0xFFFFFFFF) o, si está habilitada la opción sin bloqueo, NX_NO_WAIT (0X0).</span><span class="sxs-lookup"><span data-stu-id="9eaa3-207">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>
- <span data-ttu-id="9eaa3-208">**SO_RCVBUF**: establece el tamaño de la ventana del socket TCP.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-208">**SO_RCVBUF**: This sets the window size of the TCP socket.</span></span> <span data-ttu-id="9eaa3-209">El valor predeterminado, NX_BSD_TCP_WINDOW, se establece en 64 k para sockets TCP de BSD.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-209">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="9eaa3-210">Para establecer un tamaño superior a 65535, es necesario que la biblioteca de NetX se compile con NX_TCP_ENABLE_WINDOW_SCALING definido.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-210">To set the size over 65535 requires the NetX library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>
- <span data-ttu-id="9eaa3-211">**SO_REUSEADDR**: si se establece, permite asignar varios sockets a un puerto.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-211">**SO_REUSEADDR**: If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="9eaa3-212">Por lo general se usa en el socket de servidor TCP.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-212">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="9eaa3-213">Este es el comportamiento predeterminado de los sockets de NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-213">This is the default behavior of NetX sockets.</span></span>

<span data-ttu-id="9eaa3-214">El segundo tipo de opciones de socket en tiempo de ejecución es el nivel de opción de IP.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-214">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="9eaa3-215">Para habilitar una opción de nivel de IP, es necesario llamar a *setsockopt* con option_level establecido en IP_PROTO y option_name establecido en la opción, por ejemplo, IP_MULTICAST_TTL.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-215">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL.</span></span> <span data-ttu-id="9eaa3-216">Para recuperar un valor de opción, es necesario llamar a *getsockopt* para option_name con option_level de nuevo establecido en IP_PROTO.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-216">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="9eaa3-217">A continuación se muestra la lista de opciones de nivel de IP en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-217">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="9eaa3-218">**IP_MULTICAST_TTL**: establece el período de vida de los sockets UDP.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-218">**IP_MULTICAST_TTL**: This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="9eaa3-219">El valor predeterminado es NX_IP_TIME_TO_LIVE (0x80) cuando se crea el socket.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-219">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="9eaa3-220">Este valor se puede reemplazar mediante una llamada a *setsockopt* con esta opción de socket.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-220">This value can be overridden by calling *setsockopt* with this socket option.</span></span>
- <span data-ttu-id="9eaa3-221">**IP_ADD_MEMBERSHIP**: si se establece, esta opción permite que el socket BSD (se aplica solo a los sockets UDP) se una al grupo IGMP especificado.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-221">**IP_ADD_MEMBERSHIP**: If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>
- <span data-ttu-id="9eaa3-222">**IP_ADD_MEMBERSHIP**: si se establece, esta opción permite que el socket BSD (se aplica solo a los sockets UDP) se una al grupo IGMP especificado.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-222">**IP_DROP_MEMBERSHIP**: If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="9eaa3-223">Sistema de ejemplo pequeño</span><span class="sxs-lookup"><span data-stu-id="9eaa3-223">Small Example System</span></span>

<span data-ttu-id="9eaa3-224">A continuación se muestra un ejemplo de cómo usar NetX en la figura 1.0.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-224">An example of how to use NetX BSD is shown in Figure 1.0 below.</span></span> <span data-ttu-id="9eaa3-225">En este ejemplo, el archivo de inclusión *nx_bsd.h* se agrega en la línea 7.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-225">In this example, the include file *nx_bsd.h* is brought in at line 7.</span></span> <span data-ttu-id="9eaa3-226">A continuación, la instancia de IP *bsd_ip* y el grupo de paquetes *bsd_pool* se crean como variables globales en las líneas 20 y 21.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-226">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="9eaa3-227">Observe que en esta demostración se usa un controlador de red (virtual) de RAM (línea 41).</span><span class="sxs-lookup"><span data-stu-id="9eaa3-227">Note that this demo uses a ram (virtual) network driver (line 41).</span></span> <span data-ttu-id="9eaa3-228">En este ejemplo, el cliente y el servidor compartirán la misma dirección IP en la instancia de IP única.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-228">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="9eaa3-229">Los subprocesos del cliente y servidor se crean en la línea 303 y 309 en *tx_application_define* que configura la aplicación y se define en las líneas 293-361.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-229">The client and server threads are created on line 303 and 309 in *tx_application_define* which sets up the application and is defined on lines 293-361.</span></span> <span data-ttu-id="9eaa3-230">Después de la creación correcta de la instancia de IP en la línea 327, la instancia de IP está habilitada para los servicios TCP en la línea 350.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-230">After IP instance successful creation on line 327, the IP instance is enabled for TCP services on line 350.</span></span> <span data-ttu-id="9eaa3-231">El último requisito antes de poder usar los servicios de BSD es llamar a *bsd_initialize* en la línea 360 para configurar todas las estructuras de datos y los recursos de NetX y ThreadX necesarios para BSD.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-231">The last requirement before BSD services can be used is to call *bsd_initialize* on line 360 to set up all data structures and NetX, and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="9eaa3-232">En la función de entrada de subproceso de servidor, *thread_1_entry,* que se define en las líneas 381-397, la aplicación espera a que el controlador inicialice NetX con parámetros de red.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-232">In the server thread entry function, *thread_1_entry,* which is defined on lines 381-397, the application waits for the driver to initialize NetX with network parameters.</span></span> <span data-ttu-id="9eaa3-233">Una vez hecho esto, llama a *tcpServer,* que se define en las líneas 146-253, para controlar los detalles de la configuración del socket de servidor TCP.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-233">Once this is done, it calls *tcpServer,* defined on lines 146-253, to handle the details of setting up the TCP server socket.</span></span>

<span data-ttu-id="9eaa3-234">*tcpServer* crea el socket maestro llamando al servicio de *socket* en la línea 159 y lo enlaza al socket de escucha mediante la llamada a *bind* en la línea 176.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-234">*tcpServer* creates the master socket by calling the *socket* service on line 159 and binds it to the listening socket using the *bind* call on line 176.</span></span> <span data-ttu-id="9eaa3-235">Después se configura para escuchar las solicitudes de conexión en la línea 191.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-235">It is then configured for listening for connection requests on line 191.</span></span> <span data-ttu-id="9eaa3-236">Observe que el socket maestro no acepta una solicitud de conexión.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-236">Note that the master socket does not accept a connection request.</span></span> <span data-ttu-id="9eaa3-237">Se ejecuta en un bucle continuo que llama a *select* cada vez para detectar solicitudes de conexión.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-237">It runs in a continuous loop which calls *select* each time to detect connection requests.</span></span> <span data-ttu-id="9eaa3-238">A un socket BSD secundario elegido de una matriz de sockets BSD se le asigna la solicitud de conexión después de llamar al servicio *accept* en la línea 218.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-238">A secondary BSD socket chosen from an array of BSD sockets is assigned the connection request after calling the *accept* service on line 218.</span></span>

<span data-ttu-id="9eaa3-239">En el lado del cliente, la función de entrada del subproceso del cliente, *thread_0_entry*, definida en las líneas 366-377, también debe esperar a que el controlador inicialice NetX.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-239">On the Client side, the client thread entry function, *thread_0_entry*, defined on lines 366-377, should also wait for NetX to be initialized by the driver.</span></span> <span data-ttu-id="9eaa3-240">Aquí solo se espera a que el lado del servidor lo haga.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-240">Here we just wait for the server side to do so.</span></span> <span data-ttu-id="9eaa3-241">A continuación, llama a *tcpClient* definido en la línea 54-142 para controlar los detalles de la configuración del socket de cliente TCP y la solicitud de una conexión TCP.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-241">It then calls *tcpClient* defined on line 54-142, to handle the details of setting up the TCP client socket and requesting a TCP connection.</span></span>

<span data-ttu-id="9eaa3-242">El socket de cliente TCP se crea en la línea 68.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-242">The TCP client socket is created on line 68.</span></span> <span data-ttu-id="9eaa3-243">El socket se enlaza a la dirección IP especificada e intenta conectarse al servidor TCP que usa una llamada a *connect* en la línea 84.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-243">The socket is bound to the specified IP address and attempts to connect to the TCP server by calling *connect* on line 84.</span></span> <span data-ttu-id="9eaa3-244">Ahora está listo para empezar a enviar y recibir paquetes.</span><span class="sxs-lookup"><span data-stu-id="9eaa3-244">It is now ready to begin sending and receiving packets.</span></span>

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
