---
title: 'Capítulo 2: Instalación y uso del agente de SNMP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente de agente de SNMP de NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f011b73217c7f413dd19c555e9c2d40dace305ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814562"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-snmp-agent"></a><span data-ttu-id="dc077-103">Capítulo 2: Instalación y uso del agente de SNMP de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dc077-103">Chapter 2 - Installation and use of the Azure RTOS NetX Duo SNMP agent</span></span>

<span data-ttu-id="dc077-104">Este capítulo contiene una descripción de varios problemas relacionados con la instalación, la configuración y el uso del componente de agente de SNMP de Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dc077-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo SNMP agent component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="dc077-105">Distribución del producto</span><span class="sxs-lookup"><span data-stu-id="dc077-105">Product Distribution</span></span>

<span data-ttu-id="dc077-106">El agente de SNMP para NetX Duo está disponible en [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="dc077-106">SNMP Agent for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="dc077-107">El paquete incluye cuatro archivos de código fuente, un archivo de inclusión y un archivo PDF que contiene este documento, como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="dc077-107">The package includes four source files, one include file, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="dc077-108">**nxd_snmp.h**: archivo de encabezado para SNMP para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dc077-108">**nxd_snmp.h** Header file for SNMP for NetX Duo</span></span>
- <span data-ttu-id="dc077-109">**demo_snmp_helper.h**: archivo de encabezado para datos MIB de SNMP</span><span class="sxs-lookup"><span data-stu-id="dc077-109">**demo_snmp_helper.h** Header file for SNMP MIB data</span></span>
- <span data-ttu-id="dc077-110">**nxd_snmp.c**: archivo de código fuente de C para el agente de SNMP para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dc077-110">**nxd_snmp.c** C Source file for SNMP Agent for NetX Duo</span></span>
- <span data-ttu-id="dc077-111">**nx_md5.c**: algoritmos hash MD5</span><span class="sxs-lookup"><span data-stu-id="dc077-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="dc077-112">**nx_sha.c**: algoritmos hash SHA</span><span class="sxs-lookup"><span data-stu-id="dc077-112">**nx_sha.c** SHA digest algorithms</span></span>
- <span data-ttu-id="dc077-113">**nx_des.c**: algoritmos hash DES</span><span class="sxs-lookup"><span data-stu-id="dc077-113">**nx_des.c** DES encryption algorithms</span></span>
- <span data-ttu-id="dc077-114">**nxd_snmp.pdf**: guía del usuario para el agente de SNMP para NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dc077-114">**nxd_snmp.pdf** User Guide for SNMP Agent for NetX Duo</span></span>
- <span data-ttu-id="dc077-115">**demo_netxduo_snmp.c**: demostración simple de SNMP</span><span class="sxs-lookup"><span data-stu-id="dc077-115">**demo_netxduo_snmp.c** Simple SNMP demonstration</span></span>
- <span data-ttu-id="dc077-116">**demo_netxduo_mib2.c**: demostración simple de MIB2 (MIB tiene elementos de dirección IPv6).</span><span class="sxs-lookup"><span data-stu-id="dc077-116">**demo_netxduo_mib2.c** Simple MIB2 demonstration (MIB has IPv6 address elements)</span></span>
- <span data-ttu-id="dc077-117">**demo_snmp_helper.h**: archivo de encabezado que define elementos MIB.</span><span class="sxs-lookup"><span data-stu-id="dc077-117">**demo_snmp_helper.h** Header file defining MIB elements</span></span>

## <a name="netx-duo-snmp-agent-installation"></a><span data-ttu-id="dc077-118">Instalación del agente de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dc077-118">NetX Duo SNMP Agent Installation</span></span>

<span data-ttu-id="dc077-119">Para usar el protocolo SNMP de NetX Duo, la distribución completa que se ha mencionado anteriormente debe copiarse en el mismo directorio en el que está instalado NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dc077-119">In order to use NetX Duo SNMP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="dc077-120">Por ejemplo, si NetX Duo está instalado en el directorio “ *\threadx\arm7\green*”, los archivos *nxd_snmp.h*, *nxd_snmp.c*, *nx_md5.c, nx_sha.c* y nx_ *des.c* deben copiarse en este directorio.</span><span class="sxs-lookup"><span data-stu-id="dc077-120">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_snmp.h*, *nxd_snmp.c*, *nx_md5.c, nx_sha.c* and nx_ *des.c* files should be copied into this directory.</span></span>

## <a name="using-the-netx-duo-snmp-agent"></a><span data-ttu-id="dc077-121">Uso del agente de SNMP de NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dc077-121">Using the NetX Duo SNMP Agent</span></span>

<span data-ttu-id="dc077-122">La aplicación debe tener *nxd_snmp.c*, *nx_md5.c, nx_sha.c* y *nx_des.c* en el proyecto de compilación.</span><span class="sxs-lookup"><span data-stu-id="dc077-122">The application must have *nxd_snmp.c*, *nx_md5.c, nx_sha.c*, and *nx_des.c* in the build project.</span></span> <span data-ttu-id="dc077-123">El código de aplicación también debe incluir *nxd_snmp.h* después de *nx_api.h* para poder invocar los servicios SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-123">The application code must also include *nxd_snmp.h* after it includes *nx_api.h to be* able to invoke SNMP services.</span></span> <span data-ttu-id="dc077-124">Estos archivos deben compilarse de la misma manera que otros archivos de aplicación y su forma de objeto debe vincularse a la biblioteca de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dc077-124">These files must be compiled in the same manner as other application files and its object form must be linked to the NetX Duo library.</span></span> <span data-ttu-id="dc077-125">Esto es todo lo que se necesita para usar SNMP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dc077-125">This is all that is required to use NetX Duo SNMP.</span></span>

> [!NOTE]
> <span data-ttu-id="dc077-126">*Si se especifica **NX_SNMP_NO_SECURITY** en el proceso de compilación, los archivos nx_md5.c, nx_sha.c y nx_des.c no son necesarios.*</span><span class="sxs-lookup"><span data-stu-id="dc077-126">*If **NX_SNMP_NO_SECURITY** is specified in the build process, the nx_md5.c, nx_sha.c, and nx_des.c files are not needed.*</span></span>

> [!NOTE]
> <span data-ttu-id="dc077-127">Dado que NetX Duo SNMP usa los servicios de UDP, UDP debe habilitarse con la llamada *nx_udp_enable* antes de utilizar SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-127">That since NetX Duo SNMP utilizes UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using SNMP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="dc077-128">Sistema de ejemplo pequeño</span><span class="sxs-lookup"><span data-stu-id="dc077-128">Small Example System</span></span>

<span data-ttu-id="dc077-129">En la figura 1.0 que aparece a continuación, se muestra un ejemplo de cómo usar el agente de SNMP de NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dc077-129">An example of how to use NetX Duo SNMP Agent is described in Figure 1.0 that appears below.</span></span> <span data-ttu-id="dc077-130">En este ejemplo, el archivo de inclusión SNMP *nxd_snmp.h* se incluye en la línea 6.</span><span class="sxs-lookup"><span data-stu-id="dc077-130">In this example, the SNMP include file *nxd_snmp.h* is brought in at line 6.</span></span> <span data-ttu-id="dc077-131">El archivo de encabezado que define los elementos de base de datos MIB, *demo_snmp_helper.h,* se introduce en la línea 8.</span><span class="sxs-lookup"><span data-stu-id="dc077-131">The header file that defines the MIB database elements, *demo_snmp_helper.h,* is brought in at line 8.</span></span> <span data-ttu-id="dc077-132">MIB se define a partir de la línea 32.</span><span class="sxs-lookup"><span data-stu-id="dc077-132">The MIB is defined starting on line 32.</span></span> <span data-ttu-id="dc077-133">A continuación, el agente SNMP se crea en “*tx_application_define*” en la línea 129.</span><span class="sxs-lookup"><span data-stu-id="dc077-133">Next, the SNMP Agent is created in “*tx_application_define*” at line 129.</span></span> <span data-ttu-id="dc077-134">Tenga en cuenta que el bloque de control del agente SNMP "*my_agent*" se definió anteriormente como una variable global en la línea 18.</span><span class="sxs-lookup"><span data-stu-id="dc077-134">Note that the SNMP Agent control block “*my_agent*” was defined as a global variable at line 18 previously.</span></span> <span data-ttu-id="dc077-135">Si IPv6 está habilitado, las direcciones IPv6 se registran con la instancia de IP en las líneas 166-223.</span><span class="sxs-lookup"><span data-stu-id="dc077-135">If IPv6 is enabled, the IPv6 addresses are registered with the IP instance in lines 166-223.</span></span> <span data-ttu-id="dc077-136">El agente de SNMP se inicia en la línea 229.</span><span class="sxs-lookup"><span data-stu-id="dc077-136">SNMP Agent is started at line 229.</span></span> <span data-ttu-id="dc077-137">Las definiciones de devoluciones de llamada de objetos de SNMP para las solicitudes GET, GETNEXT y SET del administrador de SNMP, así como las solicitudes de actualización de nombre de usuario y MIB, se procesan a partir de la línea 250.</span><span class="sxs-lookup"><span data-stu-id="dc077-137">SNMP object callback definitions for SNMP manager GET, GETNEXT and SET requests, as well as username and MIB update requests, are processed starting at line 250.</span></span> <span data-ttu-id="dc077-138">En este ejemplo no se realiza ninguna autenticación.</span><span class="sxs-lookup"><span data-stu-id="dc077-138">For this example, no authenticate is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="dc077-139">*La tabla MIB2 que se muestra a continuación es solo un ejemplo. La aplicación puede usar otro MIB e incluirlo en archivos independientes, así como definir el proceso GET, GETNEXT o SET en función de los requisitos de su aplicación.*</span><span class="sxs-lookup"><span data-stu-id="dc077-139">*The MIB2 table shown below is simply an example. The application may use a different MIB and include it in separate files, as well as define GET, GETNEXT, or SET processing as per their application requirements.*</span></span>

```c
/* This is a small demo of the NetX SNMP Agent on the high-performance NetX TCP/IP  
   stack. This demo relies on ThreadX and NetX to show simple SNMP the SNMP
   GET/GETNEXT/SET requests on MIB-2 objects.  */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_snmp.h"
#include  "demo_snmp_helper.h"

#define     DEMO_STACK_SIZE         4096
#define     AGENT_PRIMARY_ADDRESS   IP_ADDRESS(192, 2, 2, 66)

/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_SNMP_AGENT           my_agent;


/* Indicate if using IPv6 to communicate with SNMP servers. Note that
   IPv6 must be enabled in the NetX Duo library first. Further, IPv6
   and ICMPv6 services are enabled before starting the SNMP agent. */
#define USE_IPV6


/* Define authentication and privacy keys.  */

#ifdef AUTHENTICATION_REQUIRED
NX_SNMP_SECURITY_KEY    my_authentication_key;
#endif

#ifdef PRIVACY_REQUIRED
NX_SNMP_SECURITY_KEY    my_privacy_key;
#endif

/* Define an error counter variable. */
UINT error_counter = 0;

/* This binds a secondary interfaces to the primary IP network interface 
   if SNMP is required for required for that interface. */
/* #define  MULTI_HOMED_DEVICE */

/* Define function prototypes.  A generic ram driver is used in this demo.  However
   to properly run an SNMP agent demo, a real driver should be substituted. */

VOID    thread_agent_entry(ULONG thread_input);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username);
VOID    mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr);


UCHAR context_engine_id[] = {0x80, 0x00, 0x0d, 0xfe, 0x03, 0x00, 0x11, 0x23, 0x23, 
                             0x44, 0x55};
UINT  context_engine_size = 11;
UCHAR context_name[] = {0x69, 0x6e, 0x69, 0x74, 0x69, 0x61, 0x6c};
UINT  context_name_size = 7;

/* Define main entry point.  */

int main()
{

   /* Enter the ThreadX kernel.  */
   tx_kernel_enter();
}


/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UCHAR   *pointer;
UINT    status;


   /* Setup the working pointer.  */
   pointer =  (UCHAR *) first_unused_memory;

   status = tx_thread_create(&thread_0, "agent thread", thread_agent_entry, 0,  
            pointer, DEMO_STACK_SIZE, 
            4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
   if (status != NX_SUCCESS)
   {
      return;
   }

   pointer =  pointer + DEMO_STACK_SIZE;


   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create packet pool.  */
   status = nx_packet_pool_create(&pool_0, "NetX Packet Pool 0", 2048, 
                                   pointer, 20000);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer = pointer + 20000;
  
   /* Create an IP instance.  */
   status = nx_ip_create(&ip_0, "SNMP Agent IP Instance", AGENT_PRIMARY_ADDRESS, 
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
   nx_arp_enable(&ip_0, (void *) pointer, 1024);
   pointer = pointer + 1024;

   /* Enable UPD processing for IP instance.  */
   nx_udp_enable(&ip_0);
  
   /* Enable ICMP for ping.  */
   nx_icmp_enable(&ip_0);
  
   /* Create an SNMP agent instance.  */
   status = nx_snmp_agent_create(&my_agent, "SNMP Agent", &ip_0, pointer, 4096, 
                                 &pool_0, 
                                 mib2_username_processing, mib2_get_processing, 
                                 mib2_getnext_processing, 
                                 mib2_set_processing);


  
   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   status = nx_snmp_agent_context_engine_set(&my_agent, context_engine_id, 
                                             context_engine_size);
  
   if (status != NX_SUCCESS)
   {
      error_counter++;
   }
  
   return;
}
  
VOID thread_agent_entry(ULONG thread_input)
{
  
#ifdef USE_IPV6
UINT        iface_index, address_index;
UINT        status;
NXD_ADDRESS agent_ipv6_address;
#endif
  
  
      /* Allow NetX time to get initialized. */
      tx_thread_sleep(100);
  
      /* If using IPv6, enable IPv6 and ICMPv6 services and get IPv6 addresses 
         registered with NetX Dou. */
  
#ifdef USE_IPV6
  
      /* Enable IPv6 on the IP instance. */
      status = nxd_ipv6_enable(&ip_0);
   
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
      /* Enable ICMPv6 on the IP instance. */
      status = nxd_icmp_enable(&ip_0);
  
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
  
      agent_ipv6_address.nxd_ip_address.v6[3] = 0x101;
      agent_ipv6_address.nxd_ip_address.v6[2] = 0x0;
      agent_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
      agent_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
      agent_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
  
      /* Set the primary interface for our DNS IPv6 addresses. */
      iface_index = 0;
  
      /* This assumes we are using the primary network interface (index 0). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, NX_NULL, 10, &address_index);
  
      /* Check for link local address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }
  
      /* Set the host global IP address. We are assuming a 64 
         bit prefix here but this can be any value (< 128). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, &agent_ipv6_address, 64, 
                                    &address_index);
  
      /* Check for global address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }

      /* Wait while NetX Duo validates the link local and global address. */
      tx_thread_sleep(500);
#endif
  
#ifdef AUTHENTICATION_REQUIRED

      /* Create an authentication key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "authpassword", &my_authentication_key);
  
      /* Use the authentication key.  */
      nx_snmp_agent_authenticate_key_use(&my_agent, &my_authentication_key);
#endif
  
#ifdef PRIVACY_REQUIRED
  
      /* Create a privacy key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "privpassword", &my_privacy_key);
  
      /* Use the privacy key.  */
      nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);
#endif
  
      /* Start the SNMP instance.  */
      nx_snmp_agent_start(&my_agent);
  
}
  
/* Define the application's GET processing routine.  */
  
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
      printf("SNMP Manager GET Request For:  %s", object_requested);
  
      /* Loop through the sample MIB to see if we have information for the supplied 
         variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's GETNEXT processing routine.  */
  
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                                NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager GETNEXT Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied 
      variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the next entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Is the next entry the mib greater?  */
         if (status == NX_SNMP_NEXT_ENTRY)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SNMP_NEXT_ENTRY)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Copy the new name into the object.  */
      nx_snmp_object_copy(mib2_mib[i].object_name, object_requested);
  
      printf(" Next Name is: %s", object_requested);
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
  
         /* Determine if the object data indicates an end-of-mib condition.  */
         if (object_data -> nx_snmp_object_data_type == NX_SNMP_END_OF_MIB_VIEW)
         {
  
            /* Copy the name supplied in the mib table.  */
            nx_snmp_object_copy(mib2_mib[i].object_value_ptr, object_requested);
         }
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's SET processing routine.  */
  
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager SET Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Determine if the entry has a set function.  */
      if (mib2_mib[i].object_set_callback)
      {
  
         /* Yes, call the set function.  */
         status =  (mib2_mib[i].object_set_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO SET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's authentication routine.  */
  
UINT  mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username)
{
  
      printf("Username is:  %s\n", username);
  
      /* Update MIB-2 objects. In this example, it is only the SNMP objects.  */
      mib2_variable_update(&ip_0, &my_agent);
  
      /* No authentication is done, just return success!  */
      return(NX_SUCCESS);
}
  
  
/* Define the application's update routine.  */ 
  
VOID  mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr)
{
  
      /* Update the snmp parameters.  */
      snmpInPkts =                agent_ptr -> nx_snmp_agent_packets_received;
      snmpOutPkts =               agent_ptr -> nx_snmp_agent_packets_sent;
      snmpInBadVersions =         agent_ptr -> nx_snmp_agent_invalid_version;
      snmpInBadCommunityNames =   agent_ptr -> nx_snmp_agent_authentication_errors;
      snmpInBadCommunityUsers =   agent_ptr -> nx_snmp_agent_username_errors; 
      snmpInASNParseErrs =        agent_ptr -> nx_snmp_agent_internal_errors;
      snmpInTotalReqVars =        agent_ptr -> nx_snmp_agent_total_get_variables;
      snmpInTotalSetVars =        agent_ptr -> nx_snmp_agent_total_set_variables;
      snmpInGetRequests =         agent_ptr -> nx_snmp_agent_get_requests;
      snmpInGetNexts =            agent_ptr -> nx_snmp_agent_getnext_requests;
      snmpInSetRequests =         agent_ptr -> nx_snmp_agent_set_requests;
      snmpOutTooBigs =            agent_ptr -> nx_snmp_agent_too_big_errors;
      snmpOutNoSuchNames =        agent_ptr -> nx_snmp_agent_no_such_name_errors;
      snmpOutBadValues =          agent_ptr -> nx_snmp_agent_bad_value_errors;
      snmpOutGenErrs =            agent_ptr -> nx_snmp_agent_general_errors;
      snmpOutTraps =              agent_ptr -> nx_snmp_agent_traps_sent;
}   
```
<span data-ttu-id="dc077-140">Figura 1.0 Ejemplo de uso del agente de SNMP con NetX Duo</span><span class="sxs-lookup"><span data-stu-id="dc077-140">Figure 1.0 Example of SNMP Agent use with NetX Duo</span></span>

## <a name="configuration-options"></a><span data-ttu-id="dc077-141">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="dc077-141">Configuration Options</span></span>

<span data-ttu-id="dc077-142">Hay varias opciones de configuración para compilar SNMP para NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="dc077-142">There are several configuration options for building SNMP for NetX Duo.</span></span> <span data-ttu-id="dc077-143">A continuación, se muestra una lista de todas las opciones, donde se describe con detalle cada una de ellas:</span><span class="sxs-lookup"><span data-stu-id="dc077-143">Following is a list of all options, where each is described in detail:</span></span>  
  
| <span data-ttu-id="dc077-144">Definir</span><span class="sxs-lookup"><span data-stu-id="dc077-144">Define</span></span>                     | <span data-ttu-id="dc077-145">Significado</span><span class="sxs-lookup"><span data-stu-id="dc077-145">Meaning</span></span>                                                                                                                                                                                                                                                                        |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="dc077-146">**NX_SNMP_AGENT_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="dc077-146">**NX_SNMP_AGENT_PRIORITY**</span></span>     | <span data-ttu-id="dc077-147">Prioridad del subproceso del agente de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-147">The priority of the SNMP AGENT thread.</span></span> <span data-ttu-id="dc077-148">De forma predeterminada, este valor se define como 16 para especificar la prioridad 16.</span><span class="sxs-lookup"><span data-stu-id="dc077-148">By default, this value is defined as 16 to specify priority 16.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="dc077-149">**NX_SNMP_TYPE_OF_SERVICE**</span><span class="sxs-lookup"><span data-stu-id="dc077-149">**NX_SNMP_TYPE_OF_SERVICE**</span></span>    | <span data-ttu-id="dc077-150">Tipo de servicio necesario para las respuestas UDP de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-150">Type of service required for the SNMP UDP responses.</span></span> <span data-ttu-id="dc077-151">De forma predeterminada, este valor se define como NX_IP_NORMAL para indicar el servicio de paquetes de IP normal.</span><span class="sxs-lookup"><span data-stu-id="dc077-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span> <span data-ttu-id="dc077-152">La aplicación puede establecer esta definición antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-152">This define can be set by the application prior to inclusion of *nxd_snmp.h.*</span></span>                                                       |
| <span data-ttu-id="dc077-153">**NX_SNMP_FRAGMENT_OPTION**</span><span class="sxs-lookup"><span data-stu-id="dc077-153">**NX_SNMP_FRAGMENT_OPTION**</span></span>    | <span data-ttu-id="dc077-154">Habilitación del fragmento para solicitudes de UDP de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-154">Fragment enable for SNMP UDP requests.</span></span> <span data-ttu-id="dc077-155">De forma predeterminada, este valor es NX_DONT_FRAGMENT para deshabilitar la fragmentación de UDP de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-155">By default, this value is NX_DONT_FRAGMENT to disable SNMP UDP fragmenting.</span></span> <span data-ttu-id="dc077-156">La aplicación puede establecer esta definición antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-156">This define can be set by the application prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                 |
| <span data-ttu-id="dc077-157">**NX_SNMP_TIME_TO_LIVE**</span><span class="sxs-lookup"><span data-stu-id="dc077-157">**NX_SNMP_TIME_TO_LIVE**</span></span>       | <span data-ttu-id="dc077-158">Especifica el período de vida antes de que expire.</span><span class="sxs-lookup"><span data-stu-id="dc077-158">Specifies the time to live before it expires.</span></span> <span data-ttu-id="dc077-159">El valor predeterminado se establece en 0x80, pero se puede redefinir antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-159">The default value is set to 0x80, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                                         |
| <span data-ttu-id="dc077-160">**NX_SNMP_AGENT_TIMEOUT**</span><span class="sxs-lookup"><span data-stu-id="dc077-160">**NX_SNMP_AGENT_TIMEOUT**</span></span>      | <span data-ttu-id="dc077-161">Especifica el número de tics de ThreadX durante los que se suspenderán los servicios internos.</span><span class="sxs-lookup"><span data-stu-id="dc077-161">Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="dc077-162">El valor predeterminado se establece en 100, pero se puede redefinir antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-162">The default value is set to 100, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                         |
| <span data-ttu-id="dc077-163">**NX_SNMP_MAX_OCTET_STRING**</span><span class="sxs-lookup"><span data-stu-id="dc077-163">**NX_SNMP_MAX_OCTET_STRING**</span></span>   | <span data-ttu-id="dc077-164">Especifica el número máximo de bytes permitidos en una cadena de octetos en el agente de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-164">Specifies the maximum number of bytes allowed in an octet string in the SNMP Agent.</span></span> <span data-ttu-id="dc077-165">El valor predeterminado se establece en 255, pero se puede redefinir antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-165">The default value is set to 255, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                    |
| <span data-ttu-id="dc077-166">**NX_SNMP_MAX_CONTEXT_STRING**</span><span class="sxs-lookup"><span data-stu-id="dc077-166">**NX_SNMP_MAX_CONTEXT_STRING**</span></span> | <span data-ttu-id="dc077-167">Especifica el número máximo de bytes de una cadena de motor de contexto en el agente de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-167">Specifies the maximum number of bytes for a context engine string in the SNMP Agent.</span></span> <span data-ttu-id="dc077-168">El valor predeterminado se establece en 32, pero se puede redefinir antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-168">The default value is set to 32, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                    |
| <span data-ttu-id="dc077-169">**NX_SNMP_MAX_USER_NAME**</span><span class="sxs-lookup"><span data-stu-id="dc077-169">**NX_SNMP_MAX_USER_NAME**</span></span>      | <span data-ttu-id="dc077-170">Especifica el número máximo de bytes de un nombre de usuario (incluidas las cadenas de comunidad).</span><span class="sxs-lookup"><span data-stu-id="dc077-170">Specifies the maximum number of bytes in a username (including community strings).</span></span> <span data-ttu-id="dc077-171">El valor predeterminado se establece en 64, pero se puede redefinir antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-171">The default value is set to 64, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                      |
| <span data-ttu-id="dc077-172">**NX_SNMP_MAX_SECURITY_KEY**</span><span class="sxs-lookup"><span data-stu-id="dc077-172">**NX_SNMP_MAX_SECURITY_KEY**</span></span>   | <span data-ttu-id="dc077-173">Especifica el número de bytes permitidos en una cadena de clave de seguridad.</span><span class="sxs-lookup"><span data-stu-id="dc077-173">Specifies the number of bytes allowed in a security key string.</span></span> <span data-ttu-id="dc077-174">El valor predeterminado se establece en 64, pero se puede redefinir antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-174">The default value is set to 64, but can be redefined prior to nclusion of *nxd_snmp.h.*</span></span>                                                                                                                          |
| <span data-ttu-id="dc077-175">**NX_SNMP_PACKET_SIZE**</span><span class="sxs-lookup"><span data-stu-id="dc077-175">**NX_SNMP_PACKET_SIZE**</span></span>        | <span data-ttu-id="dc077-176">Especifica el tamaño mínimo de los paquetes del grupo especificado al crear el agente de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-176">Specifies the minimum size of the packets in the pool specified at SNMP Agent creation.</span></span> <span data-ttu-id="dc077-177">El tamaño mínimo es necesario para asegurarse de que la carga de SNMP completa puede estar incluida en un paquete.</span><span class="sxs-lookup"><span data-stu-id="dc077-177">The minimum size is needed to ensure the complete SNMP payload can be contained in one packet.</span></span> <span data-ttu-id="dc077-178">El valor predeterminado se establece en 560, pero se puede redefinir antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-178">The default value is set to 560, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span> |
| <span data-ttu-id="dc077-179">**NX_SNMP_AGENT_PORT**</span><span class="sxs-lookup"><span data-stu-id="dc077-179">**NX_SNMP_AGENT_PORT**</span></span>         | <span data-ttu-id="dc077-180">Especifica el puerto UDP en el que se atenderán las solicitudes de administrador de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-180">Specifies the UDP port to field SNMP Manager requests on.</span></span> <span data-ttu-id="dc077-181">El puerto predeterminado es el de UDP 161, pero se puede redefinir antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-181">The default port is UDP port 161, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                             |
| <span data-ttu-id="dc077-182">**NX_SNMP_MANAGER_TRAP_PORT**</span><span class="sxs-lookup"><span data-stu-id="dc077-182">**NX_SNMP_MANAGER_TRAP_PORT**</span></span>  | <span data-ttu-id="dc077-183">Especifica el puerto UDP al que se enviarán las solicitudes de captura del agente de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-183">Specifies the UDP port to send SNMP Agent trap requests to.</span></span> <span data-ttu-id="dc077-184">El puerto predeterminado es UDP 162, pero se puede redefinir antes de la inclusión de *nxd_snmp.h.*</span><span class="sxs-lookup"><span data-stu-id="dc077-184">The default port is UDP port 162, but can be redefined prior to inclusion of *nxd_snmp.h.*</span></span>                                                                                                                           |
| <span data-ttu-id="dc077-185">**NX_SNMP_MAX_TRAP_NAME**</span><span class="sxs-lookup"><span data-stu-id="dc077-185">**NX_SNMP_MAX_TRAP_NAME**</span></span>      | <span data-ttu-id="dc077-186">Especifica el tamaño de la matriz que contiene el nombre de usuario enviado con mensajes de captura.</span><span class="sxs-lookup"><span data-stu-id="dc077-186">Specifies the size of the array to hold the username sent with trap messages.</span></span> <span data-ttu-id="dc077-187">El valor predeterminado es 64.</span><span class="sxs-lookup"><span data-stu-id="dc077-187">The default value is 64.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="dc077-188">**NX_SNMP_MAX_TRAP_KEY**</span><span class="sxs-lookup"><span data-stu-id="dc077-188">**NX_SNMP_MAX_TRAP_KEY**</span></span>       | <span data-ttu-id="dc077-189">Especifica el tamaño de las claves de privacidad y autenticación de los mensajes de captura.</span><span class="sxs-lookup"><span data-stu-id="dc077-189">Specifies the size of the authentication and privacy keys for trap messages.</span></span> <span data-ttu-id="dc077-190">El valor predeterminado es 64.</span><span class="sxs-lookup"><span data-stu-id="dc077-190">The default value is 64.</span></span>                                                                                                                                                                          |
| <span data-ttu-id="dc077-191">**NX_SNMP_TIME_INTERVAL**</span><span class="sxs-lookup"><span data-stu-id="dc077-191">**NX_SNMP_TIME_INTERVAL**</span></span>      | <span data-ttu-id="dc077-192">Determina el intervalo de suspensión en tics del temporizador que realiza la tarea de subproceso de SNMP entre el procesamiento de paquetes de SNMP recibidos.</span><span class="sxs-lookup"><span data-stu-id="dc077-192">This determines the sleep interval in timer ticks taken by the SNMP thread task between processing received SNMP packets.</span></span> <span data-ttu-id="dc077-193">El valor predeterminado es 100.</span><span class="sxs-lookup"><span data-stu-id="dc077-193">The default value is 100.</span></span> <span data-ttu-id="dc077-194">Durante dicho intervalo, la aplicación host tiene acceso a los servicios de la API de SNMP.</span><span class="sxs-lookup"><span data-stu-id="dc077-194">During this sleep interval the host application has access to SNMP API services.</span></span>                                           |
| <span data-ttu-id="dc077-195">**NX_SNMP_DISABLE_V1**</span><span class="sxs-lookup"><span data-stu-id="dc077-195">**NX_SNMP_DISABLE_V1**</span></span>         | <span data-ttu-id="dc077-196">Si se define, elimina todo el procesamiento de la versión 1 de SNMP en *nxd_snmp.c.*</span><span class="sxs-lookup"><span data-stu-id="dc077-196">Defined, this removes all the SNMP Version 1 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="dc077-197">De manera predeterminada, no está definido.</span><span class="sxs-lookup"><span data-stu-id="dc077-197">By default this is not defined.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="dc077-198">**NX_SNMP_DISABLE_V2**</span><span class="sxs-lookup"><span data-stu-id="dc077-198">**NX_SNMP_DISABLE_V2**</span></span>         | <span data-ttu-id="dc077-199">Si se define, elimina todo el procesamiento de la versión 2 de SNMP en *nxd_snmp.c.*</span><span class="sxs-lookup"><span data-stu-id="dc077-199">Defined, this removes all the SNMP Version 2 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="dc077-200">De manera predeterminada, no está definido.</span><span class="sxs-lookup"><span data-stu-id="dc077-200">By default this is not defined.</span></span>                                                                                                                                                                         |
| <span data-ttu-id="dc077-201">**NX_SNMP_DISABLE_V3**</span><span class="sxs-lookup"><span data-stu-id="dc077-201">**NX_SNMP_DISABLE_V3**</span></span>         | <span data-ttu-id="dc077-202">Si está definido, elimina todo el procesamiento de SNMPv3 en *nxd_snmp.c.*</span><span class="sxs-lookup"><span data-stu-id="dc077-202">Defined, this removes all the SNMPv3 processing in *nxd_snmp.c.*</span></span> <span data-ttu-id="dc077-203">De manera predeterminada, no está definido.</span><span class="sxs-lookup"><span data-stu-id="dc077-203">By default this is not defined.</span></span>                                                                                                                                                                                 |