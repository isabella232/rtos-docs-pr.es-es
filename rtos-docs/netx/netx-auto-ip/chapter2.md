---
title: 'Capítulo 2: Instalación y uso de la AutoIP de Azure RTOS NetX'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente AutoIP de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 269a3b4e9754fdc19e2cf1482d483fad2b841de9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814461"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-autoip"></a><span data-ttu-id="fc674-103">Capítulo 2: Instalación y uso de la AutoIP de Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="fc674-103">Chapter 2 - Installation and use of Azure RTOS NetX AutoIP</span></span>

<span data-ttu-id="fc674-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente AutoIP de Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="fc674-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="fc674-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="fc674-105">Product Distribution</span></span>

<span data-ttu-id="fc674-106">AutoIP para NetX está disponible en [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="fc674-106">AutoIP for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="fc674-107">El paquete incluye tres archivos de código fuente, un archivo de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="fc674-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="fc674-108">**nx_auto_ip.h**: archivo de encabezado para AutoIP de NetX</span><span class="sxs-lookup"><span data-stu-id="fc674-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="fc674-109">**nx_auto_ip.c**: archivo de código fuente de C para AutoIP de NetX</span><span class="sxs-lookup"><span data-stu-id="fc674-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="fc674-110">**demo_netx_auto_ip.c**: demo de archivo de código fuente de C para AutoIP de NetX</span><span class="sxs-lookup"><span data-stu-id="fc674-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="fc674-111">**nx_auto_ip.pdf**: descripción en PDF de AutoIP de NetX</span><span class="sxs-lookup"><span data-stu-id="fc674-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="fc674-112">Instalación de AutoIP</span><span class="sxs-lookup"><span data-stu-id="fc674-112">AutoIP Installation</span></span>

<span data-ttu-id="fc674-113">Para usar AutoIP de NetX, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX.</span><span class="sxs-lookup"><span data-stu-id="fc674-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="fc674-114">Por ejemplo, si NetX se ha instalado en el directorio " *\threadx\arm7\green*", los archivos *nx_auto_ip.h*, *nx_auto_ip.c* y *demo_netx_auto_ip.c* deben copiarse en este directorio.</span><span class="sxs-lookup"><span data-stu-id="fc674-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="fc674-115">Uso de AutoIP</span><span class="sxs-lookup"><span data-stu-id="fc674-115">Using AutoIP</span></span>

<span data-ttu-id="fc674-116">El uso de AutoIP de NetX es sencillo.</span><span class="sxs-lookup"><span data-stu-id="fc674-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="fc674-117">Básicamente, el código de la aplicación debe incluir *nx_auto_ip.h* después de incluir *tx_api.h* y *nx_api.h*, con el fin de usar ThreadX y NetX.</span><span class="sxs-lookup"><span data-stu-id="fc674-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="fc674-118">Después de incluir *nx_auto_ip.h*, el código de la aplicación puede realizar las llamadas de función AutoIP que se especifican más adelante en esta guía.</span><span class="sxs-lookup"><span data-stu-id="fc674-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="fc674-119">La aplicación también debe incluir *nx_auto_ip.c* en el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="fc674-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="fc674-120">Estos archivos se deben compilar de la misma manera que otros archivos de aplicación y su formulario de objetos se debe vincular junto con los archivos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fc674-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="fc674-121">Esto es todo lo que se necesita para usar AutoIP de NetX.</span><span class="sxs-lookup"><span data-stu-id="fc674-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="fc674-122">Dado que AutoIP usa servicios ARP de NetX, ARP debe estar habilitado con la llamada *nx_arp_enable* antes de usar AutoIP.</span><span class="sxs-lookup"><span data-stu-id="fc674-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="fc674-123">Pequeño sistema de ejemplo</span><span class="sxs-lookup"><span data-stu-id="fc674-123">Small Example System</span></span>

<span data-ttu-id="fc674-124">Un ejemplo de lo fácil que es usar AutoIP de NetX se describe en la figura 1.1 que aparece a continuación.</span><span class="sxs-lookup"><span data-stu-id="fc674-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="fc674-125">En este ejemplo, el archivo de inclusión de AutoIP *nx_auto_ip.h* se incluye en la línea 002.</span><span class="sxs-lookup"><span data-stu-id="fc674-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="fc674-126">A continuación, se crea la instancia de AutoIP de NetX en "*tx_application_define*" en la línea 090.</span><span class="sxs-lookup"><span data-stu-id="fc674-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="fc674-127">Tenga en cuenta que el bloque de control de AutoIP de NetX "auto_ip_0" se definió anteriormente como una variable global en la línea 015.</span><span class="sxs-lookup"><span data-stu-id="fc674-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="fc674-128">Después de la creación correcta, se inicia una AutoIP de NetX en la línea 098.</span><span class="sxs-lookup"><span data-stu-id="fc674-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="fc674-129">El procesamiento de la función de devolución de llamada de cambio de dirección IP comienza en la línea 105, que se usa para controlar los conflictos subsiguientes o la posible resolución de direcciones DHCP.</span><span class="sxs-lookup"><span data-stu-id="fc674-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="fc674-130">En el siguiente ejemplo se supone que el dispositivo host es un dispositivo de host único.</span><span class="sxs-lookup"><span data-stu-id="fc674-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="fc674-131">En el caso de un dispositivo de host múltiple, la aplicación host puede usar el servicio AutoIP de NetX *nx_auto_ip_interface_* establecido para especificar una interfaz de red secundaria para sondear una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="fc674-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="fc674-132">Consulte la **Guía de usuario de NetX** para obtener más detalles sobre la configuración de aplicaciones de host múltiple.</span><span class="sxs-lookup"><span data-stu-id="fc674-132">See the **NetX User Guide** for more details on setting up multihomed applications.</span></span> <span data-ttu-id="fc674-133">Tenga en cuenta que la aplicación host debe usar la API de NetX *nx_status_ip_interface_check* para comprobar que AutoIP haya obtenido una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="fc674-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

## <a name="example-of-autoip-use-with-netx"></a><span data-ttu-id="fc674-134">Ejemplo de uso de AutoIP con NetX</span><span class="sxs-lookup"><span data-stu-id="fc674-134">Example of AutoIP use with NetX</span></span>

```c
000 #include "tx_api.h"
001 #include "nx_api.h"
002 #include "nx_auto_ip.h"
003
004 #define         DEMO_STACK_SIZE         4096
005
006 /* Define the ThreadX and NetX object control blocks... */
007
008 TX_THREAD         thread_0;
009 NX_PACKET_POOL    pool_0;
010 NX_IP             ip_0;
011
012
013 /* Define the AUTO IP structures for the IP instance. */
014
015 NX_AUTO_IP         auto_ip_0;
016
017
018 /* Define the counters used in the demo application... */
019
020 ULONG             thread_0_counter;
021 ULONG             address_changes;
022 ULONG             error_counter;
023
024
025 /* Define thread prototypes. */
026
027 void     thread_0_entry(ULONG thread_input);
028 void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
029 void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
030
031
032 /* Define main entry point. */
033
034 int main()
035 {
036
037     /* Enter the ThreadX kernel. */
038     tx_kernel_enter();
039 }
040
041
042 /* Define what the initial system looks like. */
043
044 void     tx_application_define(void *first_unused_memory)
045 {
046
047 CHAR     *pointer;
048 UINT     status;
049
050
051     /* Setup the working pointer. */
052     pointer = (CHAR *) first_unused_memory;
053
054     /* Create the main thread. */
055     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
056                     pointer, DEMO_STACK_SIZE,
057                     16, 16, 1, TX_AUTO_START);
058
059     pointer = pointer + DEMO_STACK_SIZE;
060
061     /* Initialize the NetX system. */
062     nx_system_initialize();
063
064     /* Create a packet pool. */
065     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
066                                     pointer, 4096);
067                                     pointer = pointer + 4096;
068
069     if (status)
070         error_counter++;
071
072     /* Create an IP instance. */
073     status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
074                             0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
075                             pointer, 4096, 1);
076                             pointer = pointer + 4096;
077
078     if (status)
079         error_counter++;
080
081     /* Enable ARP and supply ARP cache memory for IP Instance 0. */
082     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
083     pointer = pointer + 1024;
084
085     /* Check ARP enable status. */
086     if (status)
087         error_counter++;
088
089     /* Create the AutoIP instance for IP Instance 0. */
090     status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
091     pointer = pointer + 4096;
092
093     /* Check AutoIP create status. */
094     if (status)
095         error_counter++;
096
097     /* Start AutoIP instances. */
098     status = nx_auto_ip_start(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);
099
100     /* Check AutoIP start status. */
101     if (status)
102         error_counter++;
103
104     /* Register an IP address change function for IP Instance 0. */
105     status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
106                                         (void *) &auto_ip_0);
107
108     /* Check IP address change notify status. */
109     if (status)
110         error_counter++;
111     }
112
113
114     /* Define the test thread. */
115
116     void thread_0_entry(ULONG thread_input)
117     {
118
119     UINT      status;
120     ULONG     actual_status;
121
122
123          /* Wait for IP address to be resolved. */
124         do
125         {
126
127             /* Call IP status check routine. */
128             status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
129                                         &actual_status, 10000);
130
131         } while (status != NX_SUCCESS);
132
133         /* Since the IP address is resolved at this point, the application
134         can now fully utilize NetX! */
135
136         while(1)
137         {
138
139
140
141             /* Increment thread 0's counter. */
142             thread_0_counter++;
143
144             /* Sleep... */
145             tx_thread_sleep(10);
146         }
147     }
148
149
150     void ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
151     {
152
153     ULONG         ip_address;
154     ULONG         network_mask;
155     NX_AUTO_IP    *auto_ip_ptr;
156
157
158     /* Setup pointer to auto IP instance. */
159     auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;
160
161     /* Pickup the current IP address. */
162     nx_ip_address_get(ip_ptr, &ip_address, &network_mask);
163
164     /* Determine if the IP address has changed back to zero. If so,
165     make sure the AutoIP instance is started. */
166     if (ip_address == 0)
167     {
168
169         /* Get the last AutoIP address for this node. */
170         nx_auto_ip_get_address(auto_ip_ptr, &ip_address);
171
172         /* Start this AutoIP instance. */
173         nx_auto_ip_start(auto_ip_ptr, ip_address);
174     }
175
176     /* Determine if IP address has transitioned to a non local IP address. */
177     else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
178     {
179
180         /* Stop the AutoIP processing. */
181         nx_auto_ip_stop(auto_ip_ptr);
182     }
183
184     /* Increment a counter. */
185     address_changes++;
186 }
```

## <a name="configuration-options"></a><span data-ttu-id="fc674-135">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="fc674-135">Configuration Options</span></span>

<span data-ttu-id="fc674-136">Hay varias opciones de configuración para compilar AutoIP para NetX.</span><span class="sxs-lookup"><span data-stu-id="fc674-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="fc674-137">A continuación se muestra una lista de todas las opciones, donde cada una de ellas se describe en detalle:</span><span class="sxs-lookup"><span data-stu-id="fc674-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="fc674-138">**NX_DISABLE_ERROR_CHECKING**: si está definida, esta opción quita la comprobación de errores básica de AutoIP.</span><span class="sxs-lookup"><span data-stu-id="fc674-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="fc674-139">Normalmente se utiliza después de depurar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fc674-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="fc674-140">**NX_AUTO_IP_PROBE_WAIT**: el número de segundos que hay que esperar antes de enviar el primer sondeo.</span><span class="sxs-lookup"><span data-stu-id="fc674-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="fc674-141">De forma predeterminada, este valor es 1.</span><span class="sxs-lookup"><span data-stu-id="fc674-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="fc674-142">**NX_AUTO_IP_PROBE_NUM**: el número de sondeos ARP que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="fc674-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="fc674-143">De forma predeterminada, este valor es 3.</span><span class="sxs-lookup"><span data-stu-id="fc674-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="fc674-144">**NX_AUTO_IP_PROBE_MIN**: el número mínimo de segundos que hay que esperar entre el envío de sondeos.</span><span class="sxs-lookup"><span data-stu-id="fc674-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="fc674-145">De forma predeterminada, este valor es 1.</span><span class="sxs-lookup"><span data-stu-id="fc674-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="fc674-146">**NX_AUTO_IP_PROBE_MAX**: el número máximo de segundos que hay que esperar entre el envío de sondeos.</span><span class="sxs-lookup"><span data-stu-id="fc674-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="fc674-147">De forma predeterminada, este valor es 2.</span><span class="sxs-lookup"><span data-stu-id="fc674-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="fc674-148">**NX_AUTO_IP_MAX_CONFLICTS**: el número de conflictos de AutoIP antes de aumentar los retrasos de procesamiento.</span><span class="sxs-lookup"><span data-stu-id="fc674-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="fc674-149">De forma predeterminada, este valor es 10.</span><span class="sxs-lookup"><span data-stu-id="fc674-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="fc674-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: el número de segundos que se debe extender el período de espera cuando se supera el número total de conflictos.</span><span class="sxs-lookup"><span data-stu-id="fc674-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="fc674-151">De forma predeterminada, este valor es 60.</span><span class="sxs-lookup"><span data-stu-id="fc674-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="fc674-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: el número de segundos que hay que esperar antes de enviar el anuncio.</span><span class="sxs-lookup"><span data-stu-id="fc674-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="fc674-153">De forma predeterminada, este valor es 2.</span><span class="sxs-lookup"><span data-stu-id="fc674-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="fc674-154">**NX_AUTO_IP_ANNOUNCE_NUM**: el número de anuncios de ARP que se van a enviar.</span><span class="sxs-lookup"><span data-stu-id="fc674-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="fc674-155">De forma predeterminada, este valor es 2.</span><span class="sxs-lookup"><span data-stu-id="fc674-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="fc674-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: el número de segundos de espera entre el envío de anuncios.</span><span class="sxs-lookup"><span data-stu-id="fc674-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="fc674-157">De forma predeterminada, este valor es 2.</span><span class="sxs-lookup"><span data-stu-id="fc674-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="fc674-158">**NX_AUTO_IP_DEFEND_INTERVAL**: el número de segundos de espera entre anuncios de defensa.</span><span class="sxs-lookup"><span data-stu-id="fc674-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="fc674-159">De forma predeterminada, este valor es 10.</span><span class="sxs-lookup"><span data-stu-id="fc674-159">By default, this value is defined as 10.</span></span>