---
title: 'Apéndice A: Descripción de la característica de restauración de estado para los servicios del cliente Azure RTOS NetX Duo DHCP'
description: Este capítulo contiene una descripción de la característica de restauración de estado para los servicios del cliente Azure RTOS NetX Duo DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 008ca6fb0052339e188e0240cc38a81d3a6b40e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814817"
---
# <a name="appendix-a--description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="6cae2-103">Apéndice A: Descripción de la característica de restauración de estado para los servicios del cliente Azure RTOS NetX Duo DHCP</span><span class="sxs-lookup"><span data-stu-id="6cae2-103">Appendix A : Description of the Restore state feature for Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="6cae2-104">Con la opción de configuración del cliente NetX Duo DHDP, NX_DHCP_CLIENT_RESTORE_STATE, un sistema puede restaurar un registro del cliente DHCP creado previamente con un estado Enlazado entre reinicios del sistema.</span><span class="sxs-lookup"><span data-stu-id="6cae2-104">The NetX Duo DHDP Client configuration option, NX_DHCP_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client Record in a Bound state between system reboots.</span></span>

<span data-ttu-id="6cae2-105">Cuando esta opción está habilitada, la aplicación puede suspender y reanudar el subproceso del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-105">When this option is enabled, the application can suspend and resume the DHCP Client thread.</span></span> <span data-ttu-id="6cae2-106">También hay un servicio para actualizar el cliente DHCP con el tiempo transcurrido entre la suspensión y la reanudación del subproceso.</span><span class="sxs-lookup"><span data-stu-id="6cae2-106">There is also a service to update the DHCP Client with the elapsed time between suspending and resuming the thread.</span></span>

## <a name="restoring-the-dhcp-client-between-reboots"></a><span data-ttu-id="6cae2-107">Restauración del cliente DHCP entre reinicios</span><span class="sxs-lookup"><span data-stu-id="6cae2-107">Restoring the DHCP Client between Reboots</span></span>

<span data-ttu-id="6cae2-108">Antes de restaurar un cliente DHCP después de un reinicio, un cliente DHCP creado previamente debe alcanzar el estado Enlazado y recibir una dirección IP del servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-108">Before restoring a DHCP Client after rebooting, a previously created DHCP Client that must reach the Bound state and be is assigned an IP address from the DHCP server.</span></span> <span data-ttu-id="6cae2-109">A continuación, antes del apagado, la aplicación DHCP debe guardar el registro del cliente DHCP actual en la memoria no volátil.</span><span class="sxs-lookup"><span data-stu-id="6cae2-109">Before it powers down, the DHCP application must then save the current DHCP Client record to non-volatile memory.</span></span> <span data-ttu-id="6cae2-110">También debe haber un "cronometrador" independiente en otro lugar del sistema para realizar un seguimiento del tiempo transcurrido mientras el cliente permanece apagado.</span><span class="sxs-lookup"><span data-stu-id="6cae2-110">There must also be an independent ‘time keeper’ elsewhere in the system to keep track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="6cae2-111">Al encenderlo, la aplicación crea una instancia del cliente DHCP y, a continuación, la actualiza con el registro del cliente DHCP creado previamente.</span><span class="sxs-lookup"><span data-stu-id="6cae2-111">On powering up, the application creates a new DHCP Client instance, and then updates it with the previously created DHCP Client record.</span></span> <span data-ttu-id="6cae2-112">El tiempo transcurrido se obtiene del "cronometrador" y, a continuación, se aplica al tiempo restante de la concesión del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-112">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Client lease.</span></span> <span data-ttu-id="6cae2-113">Tenga en cuenta que esta acción puede provocar que el cliente DHCP cambie de estado, por ejemplo, de ENLAZADO a RENOVANDO.</span><span class="sxs-lookup"><span data-stu-id="6cae2-113">Note that this may cause the DHCP Client to change states e.g. from BOUND to RENEWING.</span></span> <span data-ttu-id="6cae2-114">Llegados a este punto, la aplicación puede reanudar el cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-114">At this point, the application can resume the DHCP Client.</span></span>

<span data-ttu-id="6cae2-115">Si el tiempo transcurrido durante el apagado hace que el cliente DHCP pase a tener el estado RENOVAR o REENLAZAR, el cliente iniciará automáticamente mensajes DHCP en los que solicitará renovar o reenlazar la concesión de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-115">If the time elapsed during power down puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="6cae2-116">Si la dirección IP ha expirado, el cliente DHCP la borrará automáticamente de la instancia IP y comenzará el proceso DHCP desde el estado INICIALIZACIÓN, solicitando una nueva dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-116">If the IP address is expired, the DHCP Client will automatically clear the IP address on the IP instance and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="6cae2-117">De esta manera, el cliente DHCP puede operar entre reinicios como si no se hubiera interrumpido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-117">In this manner the DHCP Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="6cae2-118">A continuación se muestra un ejemplo de esta característica.</span><span class="sxs-lookup"><span data-stu-id="6cae2-118">Below is an illustration of this feature.</span></span> <span data-ttu-id="6cae2-119">En él se asume que el cliente DHCP se ejecuta solo en la interfaz principal.</span><span class="sxs-lookup"><span data-stu-id="6cae2-119">This assumes DHCP Client is running only on the primary interface.</span></span>

```c
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{
    /* No previously saved Client record. Start the DHCP Client in the INIT state.  */
    status =  nx_dhcp_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    do
    {
        /* Wait for DHCP to assign the IP address.  */
    } while (status != NX_SUCCESS);

    /* We have a valid IP address. */
    /* At some point decide we power down the system. */
    /* Save the Client state data which we will subsequently need to restore the DHCP    
       Client. */
    status = nx_dhcp_client_get_record(&dhcp_0, &client_nv_record);               

    /* Copy this memory to non-volatile memory (not shown). */
    /* Delete the IP and DHCP Client instances before powering down. */
    nx_dhcp_delete(&dhcp_0);

    nx_ip_delete(&ip_0);
    /* Ready to power down, having released other resources as necessary. */

}
else
{

    /* The application has determined there is a previously saved record. We will 
        restore it to the current DHCP Client instance.  */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
        update the IP instance with IP address, mask etc. */
    status = nx_dhcp_client_restore_record(&dhcp_0, &client_nv_record, time_elapsed);   

    if (status != NX_SUCCESS)
        return;

    /* We are ready to resume the DHCP Client thread and use the assigned IP address. */
    status = nx_dhcp_resume(&dhcp_0);

    if (status != NX_SUCCESS)
        return;

}
```
## <a name="resuming-the-dhcp-client-thread-after-suspension"></a><span data-ttu-id="6cae2-120">Reanudación del subproceso del cliente DHCP tras una suspensión</span><span class="sxs-lookup"><span data-stu-id="6cae2-120">Resuming the DHCP Client Thread after Suspension</span></span> 

<span data-ttu-id="6cae2-121">Para suspender un subproceso del cliente DHCP sin apagarlo, la aplicación llama a *nx_dhcp_suspend* en un cliente DHCP que ha alcanzado el estado ENLAZADO y tiene una dirección IP válida.</span><span class="sxs-lookup"><span data-stu-id="6cae2-121">To suspend a DHCP Client thread without powering down, the application calls *nx_dhcp_suspend* on a DHCP Client which has achieved the BOUND state and which has a valid IP address.</span></span> <span data-ttu-id="6cae2-122">Cuando está lista para reanudar el cliente DHCP, primero llama a *nx_dhcp_client_update_time_remaining* con el fin de actualizar el tiempo restante de la concesión de dirección DHCP (obteniendo el tiempo transcurrido de un cronometrador independiente).</span><span class="sxs-lookup"><span data-stu-id="6cae2-122">When it is ready to resume the DHCP Client it first calls *nx_dhcp_client_update_time_remaining* to update the time remaining on the DHCP address lease (obtaining the time elapsed from an independent time keeper).</span></span> <span data-ttu-id="6cae2-123">A continuación, llama a *nx_dhcp_resume* para reanudar el subproceso del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-123">Then it calls the *nx_dhcp_resume* to resume the DHCP Client thread.</span></span>

<span data-ttu-id="6cae2-124">Si el tiempo transcurrido hace que el cliente DHCP pase a tener el estado RENOVAR o REENLAZAR, el cliente iniciará automáticamente mensajes DHCP en los que solicitará renovar o reenlazar la concesión de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-124">If the time elapsed puts the DHCP Client state in either a RENEW or REBIND state, the DHCP Client will automatically initiate DHCP messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="6cae2-125">Si la dirección IP ha expirado, el cliente DHCP la borrará automáticamente y comenzará el proceso DHCP desde el estado INICIALIZACIÓN, solicitando una nueva dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-125">If the IP address is expired, the DHCP Client will automatically clear the IP address and begin the DHCP process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="6cae2-126">A continuación se muestra un ejemplo de uso de esta característica.</span><span class="sxs-lookup"><span data-stu-id="6cae2-126">Below is an illustration of using this feature.</span></span>

```c
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define().  */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client.  */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   /* Wait for DHCP to obtain an IP address.  */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the network...  */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the elapsed      
     time. */


  /* At some point, we are ready to resume the DHCP Client thread. */

  /* Update the DHCP Client lease time remaining with the time elapsed. */
  status = nx_dhcp_client_update_time_remaining(&dhcp_0, time_elapsed);   

  if (status != NX_SUCCESS)
       return;

  /* We now can resume the DHCP Client thread. */
  status = nx_dhcp_resume(&dhcp_0);

  if (status != NX_SUCCESS)
       return;

  /* Resume tasks e.g. ping another host. */
  status =  nx_icmp_ping(…);

}

```
<span data-ttu-id="6cae2-127">A continuación figura una lista de servicios para restaurar el estado de un cliente DHCP desde la memoria y para suspenderlo y reanudarlo.</span><span class="sxs-lookup"><span data-stu-id="6cae2-127">Below is a list of services for restoring a DHCP Client state from memory and for suspending and resuming the DHCP Client.</span></span>

## <a name="nx_dhcp_client_get_record"></a><span data-ttu-id="6cae2-128">nx_dhcp_client_get_record</span><span class="sxs-lookup"><span data-stu-id="6cae2-128">nx_dhcp_client_get_record</span></span>

<span data-ttu-id="6cae2-129">Cree un registro del estado actual del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-129">Create a record of the current DHCP Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="6cae2-130">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6cae2-130">Prototype</span></span>

```c
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="6cae2-131">Descripción</span><span class="sxs-lookup"><span data-stu-id="6cae2-131">Description</span></span>

<span data-ttu-id="6cae2-132">Este servicio guarda en el registro al que apunta record_ptr el cliente DHCP en ejecución en la primera interfaz habilitada para DHCP que se encuentre en la instancia del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-132">This service saves the DHCP Client running on the first interface enabled for DHCP found on the DHCP Client instance to the record pointed to by record_ptr.</span></span> <span data-ttu-id="6cae2-133">De este modo, la aplicación cliente DHCP puede restaurar el estado de su cliente DHCP después de, por ejemplo, un apagado y un reinicio.</span><span class="sxs-lookup"><span data-stu-id="6cae2-133">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

<span data-ttu-id="6cae2-134">Para guardar un registro del cliente DHCP en una interfaz específica si hay más de una habilitada para DHCP, use el servicio *nx_dhcp_interface_client_get_record*.</span><span class="sxs-lookup"><span data-stu-id="6cae2-134">To save a DHCP Client record on a specific interface if more than one interface is enabled for DHCP, use the *nx_dhcp_interface_client_get_record* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6cae2-135">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6cae2-135">Input Parameters</span></span>

- <span data-ttu-id="6cae2-136">**dhcp_ptr**: puntero al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-136">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="6cae2-137">**record_ptr**: puntero al registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-137">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="6cae2-138">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6cae2-138">Return Values</span></span>

- <span data-ttu-id="6cae2-139">**NX_SUCCESS**: (0x0) Se ha creado un registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="6cae2-139">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="6cae2-140">**NX_DHCP_NOT_BOUND**: (0x94) El cliente no tiene el estado Enlazado.</span><span class="sxs-lookup"><span data-stu-id="6cae2-140">**NX_DHCP_NOT_BOUND**: (0x94) Client not in Bound states</span></span>
- <span data-ttu-id="6cae2-141">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No hay interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-141">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="6cae2-142">NX_PTR_ERROR: (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="6cae2-142">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6cae2-143">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6cae2-143">Allowed From</span></span>

<span data-ttu-id="6cae2-144">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="6cae2-144">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6cae2-145">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6cae2-145">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a><span data-ttu-id="6cae2-146">nx_dhcp_interface_client_get_record</span><span class="sxs-lookup"><span data-stu-id="6cae2-146">nx_dhcp_interface_client_get_record</span></span>

<span data-ttu-id="6cae2-147">Cree un registro del estado actual del cliente DHCP en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="6cae2-147">Create a record of the current DHCP Client state on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6cae2-148">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6cae2-148">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, UINT interface_index,
                                          NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="6cae2-149">Descripción</span><span class="sxs-lookup"><span data-stu-id="6cae2-149">Description</span></span>

<span data-ttu-id="6cae2-150">Este servicio guarda en el registro al que apunta record_ptr el cliente DHCP en ejecución en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="6cae2-150">This service saves the DHCP Client running on the specified interface to the record pointed to by record_ptr.</span></span> <span data-ttu-id="6cae2-151">De este modo, la aplicación cliente DHCP puede restaurar el estado de su cliente DHCP después de, por ejemplo, un apagado y un reinicio.</span><span class="sxs-lookup"><span data-stu-id="6cae2-151">This allows the DHCP Client application restore its DHCP Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6cae2-152">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6cae2-152">Input Parameters</span></span>

- <span data-ttu-id="6cae2-153">**dhcp_ptr**: puntero al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-153">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="6cae2-154">**interface_index**: índice en el que se obtiene el registro.</span><span class="sxs-lookup"><span data-stu-id="6cae2-154">**interface_index**: Index on which to get record</span></span>
- <span data-ttu-id="6cae2-155">**record_ptr**: puntero al registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-155">**record_ptr**: Pointer to DHCP Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="6cae2-156">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6cae2-156">Return Values</span></span>

- <span data-ttu-id="6cae2-157">**NX_SUCCESS**: (0x0) Se ha creado un registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="6cae2-157">**NX_SUCCESS (0x0)**: Client record created</span></span>
- <span data-ttu-id="6cae2-158">**NX_DHCP_NOT_BOUND**: (0x94) **El cliente no tiene el estado Enlazado.**</span><span class="sxs-lookup"><span data-stu-id="6cae2-158">**NX_DHCP_NOT_BOUND**: (0x94) **Client not in Bound state**</span></span>
- <span data-ttu-id="6cae2-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) El índice de interfaz no es válido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-159">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="6cae2-160">NX_PTR_ERROR: (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-160">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6cae2-161">NX_INVALID_INTERFACE: (0x4C) La interfaz de red no es válida.</span><span class="sxs-lookup"><span data-stu-id="6cae2-161">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6cae2-162">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6cae2-162">Allowed From</span></span>

<span data-ttu-id="6cae2-163">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="6cae2-163">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6cae2-164">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6cae2-164">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a><span data-ttu-id="6cae2-165">nx_dhcp_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="6cae2-165">nx_dhcp_ client_restore_record</span></span>

<span data-ttu-id="6cae2-166">Restaure el cliente DHCP a partir de un registro guardado previamente.</span><span class="sxs-lookup"><span data-stu-id="6cae2-166">Restore DHCP Client from a previously saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="6cae2-167">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6cae2-167">Prototype</span></span>

```c
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD *record_ptr, 
                                    ULONG time_elapsed);

```

### <a name="description"></a><span data-ttu-id="6cae2-168">Descripción</span><span class="sxs-lookup"><span data-stu-id="6cae2-168">Description</span></span>

<span data-ttu-id="6cae2-169">Con este servicio, una aplicación puede restaurar su cliente DHCP a partir de una sesión anterior con el registro del cliente DHCP al que apunta record_ptr.</span><span class="sxs-lookup"><span data-stu-id="6cae2-169">This service enables an application to restore its DHCP Client from a previous session using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="6cae2-170">La entrada time_elapsed se aplica al tiempo restante de la concesión del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-170">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="6cae2-171">Para ello, es necesario que la aplicación cliente DHCP haya creado un registro del cliente DHCP antes de apagarlo y haya guardado dicho registro en la memoria no volátil.</span><span class="sxs-lookup"><span data-stu-id="6cae2-171">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="6cae2-172">Si hay más de una interfaz habilitada para el cliente DHCP, este servicio se aplica a la primera interfaz válida que se encuentre en la instancia de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-172">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6cae2-173">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6cae2-173">Input Parameters</span></span>

- <span data-ttu-id="6cae2-174">**dhcp_ptr**: puntero al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-174">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="6cae2-175">**record_ptr**: puntero al registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-175">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="6cae2-176">**time_elapsed**: tiempo que se debe restar del tiempo de concesión que queda en el registro del cliente de entrada.</span><span class="sxs-lookup"><span data-stu-id="6cae2-176">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="6cae2-177">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6cae2-177">Return Values</span></span>

- <span data-ttu-id="6cae2-178">**NX_SUCCESS**: (0x0) Se ha restaurado el registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="6cae2-178">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="6cae2-179">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No hay interfaces que ejecuten DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-179">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces running DHCP</span></span>
- <span data-ttu-id="6cae2-180">NX_PTR_ERROR: (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="6cae2-180">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6cae2-181">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6cae2-181">Allowed From</span></span>

<span data-ttu-id="6cae2-182">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="6cae2-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6cae2-183">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6cae2-183">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a><span data-ttu-id="6cae2-184">nx_dhcp_interace_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="6cae2-184">nx_dhcp_interace_client_restore_record</span></span>

<span data-ttu-id="6cae2-185">Restaure el cliente DHCP en la interfaz especificada a partir de un registro guardado previamente.</span><span class="sxs-lookup"><span data-stu-id="6cae2-185">Restore DHCP Client from a previously saved record on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6cae2-186">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6cae2-186">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD *record_ptr, 
                                              ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="6cae2-187">Descripción</span><span class="sxs-lookup"><span data-stu-id="6cae2-187">Description</span></span>

<span data-ttu-id="6cae2-188">Con este servicio, una aplicación puede restaurar su cliente DHCP en la interfaz especificada con el registro del cliente DHCP al que apunta record_ptr.</span><span class="sxs-lookup"><span data-stu-id="6cae2-188">This service enables an application to restore its DHCP Client on the specified interface using the DHCP Client record pointed to by record_ptr.</span></span> <span data-ttu-id="6cae2-189">La entrada time_elapsed se aplica al tiempo restante de la concesión del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-189">The time_elapsed input is applied to the time remaining on DHCP Client lease.</span></span>

<span data-ttu-id="6cae2-190">Para ello, es necesario que la aplicación cliente DHCP haya creado un registro del cliente DHCP antes de apagarlo y haya guardado dicho registro en la memoria no volátil.</span><span class="sxs-lookup"><span data-stu-id="6cae2-190">This requires that the DHCP Client application created a record of the DHCP Client before powering down, and saved that record to nonvolatile memory.</span></span>

<span data-ttu-id="6cae2-191">Si hay más de una interfaz habilitada para el cliente DHCP, este servicio se aplica a la primera interfaz válida que se encuentre en la instancia de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-191">If more than one interface is enabled for DHCP Client, this service is applied to the first valid interface found in the DHCP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6cae2-192">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6cae2-192">Input Parameters</span></span>

- <span data-ttu-id="6cae2-193">**dhcp_ptr**: puntero al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-193">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="6cae2-194">**record_ptr**: puntero al registro del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-194">**record_ptr**: Pointer to DHCP Client record</span></span> 
- <span data-ttu-id="6cae2-195">**time_elapsed**: tiempo que se debe restar del tiempo de concesión que queda en el registro del cliente de entrada.</span><span class="sxs-lookup"><span data-stu-id="6cae2-195">**time_elapsed**: Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="6cae2-196">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6cae2-196">Return Values</span></span>

- <span data-ttu-id="6cae2-197">**NX_SUCCESS**: (0x0) Se ha restaurado el registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="6cae2-197">**NX_SUCCESS**: (0x0) Client record restored</span></span>
- <span data-ttu-id="6cae2-198">**NX_DHCP_NOT_BOUND**: (0x94) El cliente no está enlazado a una dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-198">**NX_DHCP_NOT_BOUND**: (0x94) Client not bound to IP address</span></span>
- <span data-ttu-id="6cae2-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) El índice de interfaz no es válido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-199">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="6cae2-200">NX_PTR_ERROR: (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-200">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6cae2-201">NX_INVALID_INTERFACE: (0x4C) La interfaz de red no es válida.</span><span class="sxs-lookup"><span data-stu-id="6cae2-201">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6cae2-202">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6cae2-202">Allowed From</span></span>

<span data-ttu-id="6cae2-203">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="6cae2-203">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6cae2-204">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6cae2-204">Example</span></span>

```c
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a><span data-ttu-id="6cae2-205">nx_dhcp_client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="6cae2-205">nx_dhcp_ client_update_time_remaining</span></span>

<span data-ttu-id="6cae2-206">Actualice el tiempo restante de la concesión del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-206">Update the time remaining on DHCP Client lease</span></span>

### <a name="prototype"></a><span data-ttu-id="6cae2-207">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6cae2-207">Prototype</span></span>

```c
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="6cae2-208">Descripción</span><span class="sxs-lookup"><span data-stu-id="6cae2-208">Description</span></span>

<span data-ttu-id="6cae2-209">Este servicio actualiza el tiempo restante de la concesión de dirección IP del cliente DHCP con la entrada time_elapsed en la primera interfaz habilitada para DHCP que se encuentre en la instancia de cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-209">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the first interface enabled for DHCP found on the DHCP Client instance.</span></span> <span data-ttu-id="6cae2-210">La aplicación debe suspender el subproceso del cliente DHCP antes de usar este servicio mediante *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="6cae2-210">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="6cae2-211">Después de llamar a este servicio, la aplicación puede reanudar el subproceso del cliente DHCP si llama a *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="6cae2-211">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span>

<span data-ttu-id="6cae2-212">Este servicio está pensado para aplicaciones cliente DHCP que necesitan suspender el subproceso del cliente DHCP durante un período de tiempo y, a continuación, actualizar el tiempo restante de la concesión de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-212">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="6cae2-213">Nota: Este servicio no está diseñado para usarse con *nx_dhcp_client_get_record* ni *nx_dhcp_client_restore_record* (descritos anteriormente).</span><span class="sxs-lookup"><span data-stu-id="6cae2-213">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="6cae2-214">Estos servicios se han descrito anteriormente en esta sección.</span><span class="sxs-lookup"><span data-stu-id="6cae2-214">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6cae2-215">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6cae2-215">Input Parameters</span></span>

- <span data-ttu-id="6cae2-216">**dhcp_ptr**: puntero al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-216">**dhcp_ptr**: Pointer to DHCP Client</span></span> 
- <span data-ttu-id="6cae2-217">**time_elapsed**: tiempo que se debe restar del que queda en la concesión de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-217">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="6cae2-218">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6cae2-218">Return Values</span></span>

- <span data-ttu-id="6cae2-219">**NX_SUCCESS**: (0x0) La concesión de dirección IP del cliente se ha actualizado.</span><span class="sxs-lookup"><span data-stu-id="6cae2-219">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="6cae2-220">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No hay interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-220">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="6cae2-221">NX_PTR_ERROR: (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="6cae2-221">NX_PTR_ERROR: (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6cae2-222">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6cae2-222">Allowed From</span></span>

<span data-ttu-id="6cae2-223">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="6cae2-223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6cae2-224">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6cae2-224">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```

## <a name="nx_dhcp_interface_client_update_time_remaining"></a><span data-ttu-id="6cae2-225">nx_dhcp_interface_client_update_time_remaining</span><span class="sxs-lookup"><span data-stu-id="6cae2-225">nx_dhcp_interface_client_update_time_remaining</span></span>

<span data-ttu-id="6cae2-226">Actualice el tiempo restante de la concesión del cliente DHCP en la interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="6cae2-226">Update the time remaining on DHCP Client lease on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6cae2-227">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6cae2-227">Prototype</span></span>

```c
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="6cae2-228">Descripción</span><span class="sxs-lookup"><span data-stu-id="6cae2-228">Description</span></span>

<span data-ttu-id="6cae2-229">Este servicio actualiza el tiempo restante de la concesión de dirección IP del cliente DHCP con la entrada time_elapsed en la interfaz especificada si dicha interfaz está habilitada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-229">This service updates the time remaining on the DHCP Client IP address lease with the time_elapsed input on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="6cae2-230">La aplicación debe suspender el subproceso del cliente DHCP antes de usar este servicio mediante *nx_dhcp_suspend*.</span><span class="sxs-lookup"><span data-stu-id="6cae2-230">The application must suspend the DHCP Client thread before using this service using *nx_dhcp_suspend*.</span></span> <span data-ttu-id="6cae2-231">Después de llamar a este servicio, la aplicación puede reanudar el subproceso del cliente DHCP si llama a *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="6cae2-231">After calling this service, the application can resume the DHCP Client thread by calling *nx_dhcp_resume*.</span></span> <span data-ttu-id="6cae2-232">Tenga en cuenta que la suspensión y la reanudación del subproceso del cliente DHCP se aplican a todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-232">Note suspending and resuming the DHCP Client thread applies to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="6cae2-233">Este servicio está pensado para aplicaciones cliente DHCP que necesitan suspender el subproceso del cliente DHCP durante un período de tiempo y, a continuación, actualizar el tiempo restante de la concesión de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-233">This is intended for DHCP Client applications that need to suspend the DHCP Client thread for a period of time, and then update the IP address lease time remaining.</span></span>

<span data-ttu-id="6cae2-234">Nota: Este servicio no está diseñado para usarse con *nx_dhcp_client_get_record* ni *nx_dhcp_client_restore_record* (descritos anteriormente).</span><span class="sxs-lookup"><span data-stu-id="6cae2-234">Note: This service is not intended to be used with *nx_dhcp_client_get_record* and *nx_dhcp_client_restore_record* described previously).</span></span> <span data-ttu-id="6cae2-235">Estos servicios se han descrito anteriormente en esta sección.</span><span class="sxs-lookup"><span data-stu-id="6cae2-235">These services are previously described in this section.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6cae2-236">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6cae2-236">Input Parameters</span></span>

- <span data-ttu-id="6cae2-237">**dhcp_ptr**: puntero al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-237">**dhcp_ptr**: Pointer to DHCP Client</span></span>
- <span data-ttu-id="6cae2-238">**interface_index**: índice de interfaz al que se debe aplicar el tiempo transcurrido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-238">**interface_index**: Index to interface to apply elapsed time to</span></span>
- <span data-ttu-id="6cae2-239">**time_elapsed**: tiempo que se debe restar del que queda en la concesión de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-239">**time_elapsed**: Time to subtract from the time remaining on the IP address lease</span></span>

### <a name="return-values"></a><span data-ttu-id="6cae2-240">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6cae2-240">Return Values</span></span>

- <span data-ttu-id="6cae2-241">**NX_SUCCESS**: (0x0) La concesión de dirección IP del cliente se ha actualizado.</span><span class="sxs-lookup"><span data-stu-id="6cae2-241">**NX_SUCCESS**: (0x0) Client IP lease updated</span></span>
- <span data-ttu-id="6cae2-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) El índice de interfaz no es válido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-242">**NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) Invalid interface index</span></span>
- <span data-ttu-id="6cae2-243">NX_PTR_ERROR: (0x16) El puntero DHCP no es válido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-243">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="6cae2-244">NX_INVALID_INTERFACE: (0x4C) La interfaz de red no es válida.</span><span class="sxs-lookup"><span data-stu-id="6cae2-244">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6cae2-245">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6cae2-245">Allowed From</span></span>

<span data-ttu-id="6cae2-246">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="6cae2-246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6cae2-247">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6cae2-247">Example</span></span>

```c
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */

```

## <a name="nx_dhcp_suspend"></a><span data-ttu-id="6cae2-248">nx_dhcp_suspend</span><span class="sxs-lookup"><span data-stu-id="6cae2-248">nx_dhcp_suspend</span></span>

<span data-ttu-id="6cae2-249">Suspenda el subproceso del cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-249">Suspend the DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="6cae2-250">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6cae2-250">Prototype</span></span>

```c
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6cae2-251">Descripción</span><span class="sxs-lookup"><span data-stu-id="6cae2-251">Description</span></span>

<span data-ttu-id="6cae2-252">Este servicio suspende el subproceso del cliente DHCP en curso.</span><span class="sxs-lookup"><span data-stu-id="6cae2-252">This service suspends the current DHCP Client thread.</span></span> <span data-ttu-id="6cae2-253">Tenga en cuenta que, a diferencia de *nx_dhcp_stop*, el estado del cliente DHCP no sufre ningún cambio cuando se llama a este servicio.</span><span class="sxs-lookup"><span data-stu-id="6cae2-253">Note that unlike *nx_dhcp_stop*, there is no change to the DHCP Client state when this service is called.</span></span>

<span data-ttu-id="6cae2-254">Este servicio suspende el cliente DHCP en ejecución en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-254">This service suspends DHCP running on all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="6cae2-255">Para actualizar el estado del cliente DHCP con el tiempo transcurrido mientras el cliente permanece suspendido, vea la descripción anterior de *nx_dhcp_client_update_time_remaining*.</span><span class="sxs-lookup"><span data-stu-id="6cae2-255">To update the DHCP Client state with elapsed time while the DHCP Client is suspended, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span> <span data-ttu-id="6cae2-256">Para reanudar un subproceso del cliente DHCP suspendido, la aplicación debe llamar a *nx_dhcp_resume*.</span><span class="sxs-lookup"><span data-stu-id="6cae2-256">To resume a suspended DHCP Client thread, the application should call *nx_dhcp_resume*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6cae2-257">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6cae2-257">Input Parameters</span></span>

- <span data-ttu-id="6cae2-258">**dhcp_ptr**: puntero al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-258">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="6cae2-259">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6cae2-259">Return Values</span></span>

- <span data-ttu-id="6cae2-260">**NX_SUCCESS**: (0x0) Se ha suspendido el subproceso del cliente.</span><span class="sxs-lookup"><span data-stu-id="6cae2-260">**NX_SUCCESS**: (0x0) Client thread is suspended</span></span>
- <span data-ttu-id="6cae2-261">NX_PTR_ERROR: (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="6cae2-261">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6cae2-262">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6cae2-262">Allowed From</span></span>

<span data-ttu-id="6cae2-263">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="6cae2-263">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6cae2-264">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6cae2-264">Example</span></span>

```c
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```

## <a name="nx_dhcp_resume"></a><span data-ttu-id="6cae2-265">nx_dhcp_resume</span><span class="sxs-lookup"><span data-stu-id="6cae2-265">nx_dhcp_resume</span></span>

<span data-ttu-id="6cae2-266">Reanude un subproceso del cliente DHCP suspendido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-266">Resume a suspended DHCP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="6cae2-267">Prototipo</span><span class="sxs-lookup"><span data-stu-id="6cae2-267">Prototype</span></span>

```c
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6cae2-268">Descripción</span><span class="sxs-lookup"><span data-stu-id="6cae2-268">Description</span></span>

<span data-ttu-id="6cae2-269">Este servicio reanuda un subproceso del cliente DHCP suspendido.</span><span class="sxs-lookup"><span data-stu-id="6cae2-269">This service resumes a suspended DHCP Client thread.</span></span> <span data-ttu-id="6cae2-270">Tenga en cuenta que el estado del cliente DHCP no sufre ningún cambio al reanudarse el subproceso.</span><span class="sxs-lookup"><span data-stu-id="6cae2-270">Note that there is no change to the actual DHCP Client state after resuming the Client thread.</span></span> <span data-ttu-id="6cae2-271">Para actualizar el tiempo restante de la concesión de dirección IP del cliente DHCP con el tiempo transcurrido antes de llamar a *nx_dhcp_resume*, vea la descripción anterior de *nx_dhcp_client_update_time_remaining*.</span><span class="sxs-lookup"><span data-stu-id="6cae2-271">To update the time remaining on the DHCP Client IP address lease with elapsed time before calling *nx_dhcp_resume*, see the *nx_dhcp_client_update_time_remaining* described previously.</span></span>

<span data-ttu-id="6cae2-272">Este servicio reanuda el cliente DHCP en ejecución en todas las interfaces habilitadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-272">This service resumes DHCP running on all interfaces enabled for DHCP.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6cae2-273">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="6cae2-273">Input Parameters</span></span>

- <span data-ttu-id="6cae2-274">**dhcp_ptr**: puntero al cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6cae2-274">**dhcp_ptr**: Pointer to DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="6cae2-275">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="6cae2-275">Return Values</span></span>

- <span data-ttu-id="6cae2-276">**NX_SUCCESS**: (0x0) Se ha reanudado el subproceso del cliente.</span><span class="sxs-lookup"><span data-stu-id="6cae2-276">**NX_SUCCESS**: (0x0) Client thread is resumed</span></span>
- <span data-ttu-id="6cae2-277">NX_PTR_ERROR: (0x16) La entrada de puntero no es válida.</span><span class="sxs-lookup"><span data-stu-id="6cae2-277">NX_PTR_ERROR: (0x16) Invalid pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6cae2-278">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="6cae2-278">Allowed From</span></span>

<span data-ttu-id="6cae2-279">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="6cae2-279">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6cae2-280">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="6cae2-280">Example</span></span>

```c
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```