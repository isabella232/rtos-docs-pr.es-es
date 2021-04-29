---
title: 'Apéndice A: Descripción de la característica de restauración de estado para los servicios del cliente DHCPv6 de Azure RTOS NetX Duo'
description: Con la opción de configuración del cliente DHCPv6 de Azure RTOS NetX Duo, NX_DHCPV6_CLIENT_RESTORE_STATE, un sistema puede restaurar un cliente DHCP creado previamente con un estado Enlazado entre reinicios del sistema.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3e642af158202bb3b2a4e2a37397b47d707b566e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814786"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a><span data-ttu-id="087f1-103">Apéndice A: Descripción de la característica de restauración de estado para los servicios del cliente DHCPv6 de Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="087f1-103">Appendix A - Description of the Restore State Feature for Azure RTOS NetX Duo DHCPv6 Client</span></span>

<span data-ttu-id="087f1-104">Con la opción de configuración del cliente DHCPv6 de Azure RTOS NetX Duo, NX_DHCPV6_CLIENT_RESTORE_STATE, un sistema puede restaurar un cliente DHCP creado previamente con un estado Enlazado entre reinicios del sistema.</span><span class="sxs-lookup"><span data-stu-id="087f1-104">The Azure RTOS NetX Duo DHDPv6 Client configuration option, NX_DHCPV6_CLIENT_RESTORE_STATE, allows a system to restore a previously created DHCP Client in a Bound state between system reboots.</span></span>

<span data-ttu-id="087f1-105">Esta opción también permite que una aplicación suspenda el subproceso del cliente DHCPv6 y lo reanude, actualizado con el tiempo transcurrido entre la suspensión y la reanudación del subproceso sin necesidad de apagarse.</span><span class="sxs-lookup"><span data-stu-id="087f1-105">This option also allows an application to suspend the DHCPv6 Client thread and resume it, updated with the elapsed time between suspending and resuming the thread without powering down.</span></span>

## <a name="restoring-the-dhcpv6-client-between-reboots"></a><span data-ttu-id="087f1-106">Restauración del cliente DHCPv6 entre reinicios</span><span class="sxs-lookup"><span data-stu-id="087f1-106">Restoring the DHCPv6 Client between Reboots</span></span>

<span data-ttu-id="087f1-107">Para restaurar un cliente DHCPv6 entre reinicios, la aplicación DHCPv6 crea una instancia del cliente DHCPv6 y, a continuación, obtiene una concesión de dirección IP mediante el protocolo DHCPv6 normal y llama a *nx_dhcpv6_start*.</span><span class="sxs-lookup"><span data-stu-id="087f1-107">To restore a DHCPv6 Client between reboots, the DHCPv6 application creates an instance of the DHCPv6 Client, and then obtains an IP address lease using the normal DHCPv6 protocol and calling *nx_dhcpv6_start*.</span></span> <span data-ttu-id="087f1-108">A continuación, la aplicación DHCPv6 espera a que se complete el protocolo.</span><span class="sxs-lookup"><span data-stu-id="087f1-108">Then the DHCPv6 application waits for the protocol to complete.</span></span> <span data-ttu-id="087f1-109">Si todo va bien, el dispositivo consigue el estado BOUND con una dirección IP válida asignada desde su servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="087f1-109">If all goes well, the device achieves the BOUND state with an assigned valid IP address from its DHCPv6 Server.</span></span> <span data-ttu-id="087f1-110">Antes de que se apague, la aplicación cliente DHCPv6 guarda la instancia del cliente DHCPv6 actual en un registro de cliente DHCPv6 que luego se almacena en memoria no volátil.</span><span class="sxs-lookup"><span data-stu-id="087f1-110">Before it powers down, the DHCPv6 Client application saves the current DHCPv6 Client instance to a DHCPv6 Client record which is then stored in non-volatile memory.</span></span> <span data-ttu-id="087f1-111">Un "cronometrador" independiente en otro lugar del sistema realiza un seguimiento del tiempo transcurrido durante este estado de apagado.</span><span class="sxs-lookup"><span data-stu-id="087f1-111">An independent ‘time keeper’ elsewhere in the system keeps track of the time elapsed during this powered down state.</span></span> <span data-ttu-id="087f1-112">Al encenderse, la aplicación crea una instancia del cliente DHCPv6 y, a continuación, la actualiza con el registro del cliente DHCPv6 creado previamente.</span><span class="sxs-lookup"><span data-stu-id="087f1-112">On powering up, the application creates a new DHCPv6 Client instance, and then updates it with the previously created DHCPv6 Client record.</span></span> <span data-ttu-id="087f1-113">El tiempo transcurrido se obtiene del "tiempo de espera" y, a continuación, se aplica al tiempo restante en la concesión de Clientv6 DHCP.</span><span class="sxs-lookup"><span data-stu-id="087f1-113">The elapsed time is obtained from the “time keeper” and then applied to the time remaining on the DHCP Clientv6 lease.</span></span> <span data-ttu-id="087f1-114">En este momento, la aplicación puede reanudar el cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="087f1-114">At this point, the application can resume the DHCPv6 Client.</span></span>

<span data-ttu-id="087f1-115">Si el tiempo transcurrido durante el apagado hace que el cliente DHCPv6 pase a tener el estado RENEW o REBIND, el cliente DHCPv6 iniciará automáticamente mensajes DHCPv6 en los que solicitará renovar o reenlazar la concesión de dirección IP.</span><span class="sxs-lookup"><span data-stu-id="087f1-115">If the time elapsed during power down puts the DHCPv6 Client state in either a RENEW or REBIND state, the DHCPv6 Client will automatically initiate DHCPv6 messages requesting to renew or rebind the IP address lease.</span></span> <span data-ttu-id="087f1-116">Si la dirección IP ha expirado, el cliente DHCPv6 la borrará automáticamente de la instancia IP y comenzará el proceso DHCPv6 desde el estado INIT, solicitando una nueva dirección IP.</span><span class="sxs-lookup"><span data-stu-id="087f1-116">If the IP address is expired, the DHCPv6 Client will automatically clear the IP address on the IP instance and begin the DHCPv6 process from the INIT state, requesting a new IP address.</span></span>

<span data-ttu-id="087f1-117">De esta manera, el cliente DHCPv6 puede operar entre reinicios como si no se interrumpa.</span><span class="sxs-lookup"><span data-stu-id="087f1-117">In this manner the DHCPv6 Client can operate between reboots as if uninterrupted.</span></span>

<span data-ttu-id="087f1-118">A continuación se muestra un ejemplo de esta característica.</span><span class="sxs-lookup"><span data-stu-id="087f1-118">Below is an illustration of this feature.</span></span>

```C
/* On the power up, create an IP instance, DHCPv6 Client, enable ICMPv6 and UDP
   and other resources (not shown) for the DHCPv6 Client/application
   in tx_application_define(). */
 
/* Define the DHCPv6 Client application thread. */     
void    thread_dhcpv6_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCPV6_CLIENT_RECORD client_my_record;


    /* No previously saved Client record. Start the DHCPv6 Client in the INIT state. */
    status =  nx_dhcpv6_start(&dhcp_0);

    if (status !=NX_SUCCESS)
        return;

    while(1)    
    {
    
        /* Wait for DHCPv6 Client to get the IP address. */
    }

    /* At some point decide we power down the system. */

    /* Save the Client state data which we will subsequently need to restore the DHCPv6    
       Client. */
    status = nx_dhcpv6_client_get_record(&dhcp_0, &client_my_record);               

    /* Copy this memory to non-volatile memory (not shown). */

    /* Delete the IP and DHCPv6 Client instances before powering down. */
    nx_dhcpv6_client_delete(&dhcp_0);

    nx_ip_delete(&ip_0);

    /* Ready to power down, having released other resources as necessary. */

    /* The application has determined there is a previously saved record. We will 
       restore it to the current DHCPv6 Client instance. */

/* Create the IP and DHCPv6 Client instances, enable ICMPv6 and UDP after powering up. */

/* Calculate the time elapsed during power down */

    /* Get the previous Client state data from non-volatile memory. */

    /* Apply the record to the current Client instance. This will also 
       update the IP instance with IP address, mask etc. */
    status = nx_dhcpv6_client_restore_record(&dhcp_0, &client_my_record, time_elapsed);   

     if (status != NX_SUCCESS)
          return;

     /* We are ready to resume the DHCPv6 Client thread and use the assigned IP address. */
     status = nx_dhcpv6_resume(&dhcp_0);

     if (status != NX_SUCCESS)
          return;

}
```

## <a name="nx_dhcpv6_client_get_record"></a><span data-ttu-id="087f1-119">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="087f1-119">nx_dhcpv6_client_get_record</span></span>

<span data-ttu-id="087f1-120">Crear un registro del estado actual del cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="087f1-120">Create a record of the current DHCPv6 Client state</span></span>

### <a name="prototype"></a><span data-ttu-id="087f1-121">Prototipo</span><span class="sxs-lookup"><span data-stu-id="087f1-121">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a><span data-ttu-id="087f1-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="087f1-122">Description</span></span>

<span data-ttu-id="087f1-123">Este servicio guarda el cliente DHCPv6 en el registro al que apunta record_ptr.</span><span class="sxs-lookup"><span data-stu-id="087f1-123">This service saves the DHCPv6 Client to the record pointed to by record_ptr.</span></span> <span data-ttu-id="087f1-124">Esto permite que la aplicación cliente DHCPv6 restaure su estado de cliente DHCPv6 después de, por ejemplo, un apagado y un reinicio.</span><span class="sxs-lookup"><span data-stu-id="087f1-124">This allows the DHCPv6 Client application restore its DHCPv6 Client state after, for example, a power down and reboot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="087f1-125">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="087f1-125">Input Parameters</span></span>

- <span data-ttu-id="087f1-126">**dhcpv6_ptr**: puntero al cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="087f1-126">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="087f1-127">**record_ptr**: puntero al registro del cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="087f1-127">**record_ptr** Pointer to DHCPv6 Client record</span></span>

### <a name="return-values"></a><span data-ttu-id="087f1-128">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="087f1-128">Return Values</span></span>

- <span data-ttu-id="087f1-129">**NX_SUCCESS (0X0)** : se ha creado un registro del cliente válido.</span><span class="sxs-lookup"><span data-stu-id="087f1-129">**NX_SUCCESS (0x0)** Valid Client record created</span></span>

- <span data-ttu-id="087f1-130">El cliente **NX_DHCPV6_NOT_BOUND** (0xE94) no tiene el estado BOUND, por lo que no tiene asignada una dirección IP válida.</span><span class="sxs-lookup"><span data-stu-id="087f1-130">**NX_DHCPV6_NOT_BOUND** (0xE94) Client not in bound state, therefore not assigned valid IP address</span></span>

- <span data-ttu-id="087f1-131">**NX_PTR_ERROR**: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="087f1-131">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="087f1-132">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="087f1-132">Allowed From</span></span>

<span data-ttu-id="087f1-133">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="087f1-133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="087f1-134">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="087f1-134">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a><span data-ttu-id="087f1-135">Consulte también</span><span class="sxs-lookup"><span data-stu-id="087f1-135">See Also</span></span>

- <span data-ttu-id="087f1-136">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="087f1-136">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="087f1-137">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="087f1-137">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="087f1-138">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="087f1-138">nx_dhcpv6_client_restore_record</span></span>

## <a name="nx_dhcpv6_client_restore_record"></a><span data-ttu-id="087f1-139">nx_dhcpv6_client_restore_record</span><span class="sxs-lookup"><span data-stu-id="087f1-139">nx_dhcpv6_client_restore_record</span></span>

<span data-ttu-id="087f1-140">Restaura el estado del cliente DHCPv6 desde un registro guardado.</span><span class="sxs-lookup"><span data-stu-id="087f1-140">Restore DHCPv6 Client state from saved record</span></span>

### <a name="prototype"></a><span data-ttu-id="087f1-141">Prototipo</span><span class="sxs-lookup"><span data-stu-id="087f1-141">Prototype</span></span>

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a><span data-ttu-id="087f1-142">Descripción</span><span class="sxs-lookup"><span data-stu-id="087f1-142">Description</span></span>

<span data-ttu-id="087f1-143">Este servicio permite a una aplicación DHCPv6 volver a crear su estado de cliente DHCPv6 desde una sesión anterior actualizando el cliente DHCPv6 con el registro del cliente DHCPv6 al que apunta record_ptr, y actualiza el tiempo restante en la concesión del cliente DHCPv6 con la entrada time_elapsed.</span><span class="sxs-lookup"><span data-stu-id="087f1-143">This service enables a DHCPv6 application to recreate its DHCPv6 Client state from a previous session by updating the DHCPv6 Client with the DHCPv6 Client record pointed to by record_ptr, and updates the time remaining on DHCPv6 Client lease with the time_elapsed input.</span></span> <span data-ttu-id="087f1-144">Esto permite a la aplicación cliente DHCPv6 volver a crear su cliente DHCPv6, por ejemplo, después de apagarse.</span><span class="sxs-lookup"><span data-stu-id="087f1-144">This allows the DHCPv6 Client application to recreate its DHCPv6 Client, for example, after powering down.</span></span> <span data-ttu-id="087f1-145">Para ello, es necesario que la aplicación cliente DHCPv6 haya creado un registro del cliente DHCPv6 antes de apagarlo y haya guardado dicho registro en la memoria no volátil.</span><span class="sxs-lookup"><span data-stu-id="087f1-145">This requires that the DHCPv6 Client application created a record of the DHCPv6 Client before powering down, and saved that record to non-volatile memory.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="087f1-146">Parámetros de entrada</span><span class="sxs-lookup"><span data-stu-id="087f1-146">Input Parameters</span></span>

- <span data-ttu-id="087f1-147">**dhcpv6_ptr**: puntero al cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="087f1-147">**dhcpv6_ptr** Pointer to DHCPv6 Client</span></span>

- <span data-ttu-id="087f1-148">**record_ptr**: puntero al registro del cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="087f1-148">**record_ptr** Pointer to DHCPv6 Client record</span></span>

- <span data-ttu-id="087f1-149">**time_elapsed**: tiempo que se debe restar del tiempo de la concesión que queda en el registro del cliente de entrada.</span><span class="sxs-lookup"><span data-stu-id="087f1-149">**time_elapsed** Time to subtract from the lease time remaining in the input client record</span></span>

### <a name="return-values"></a><span data-ttu-id="087f1-150">Valores devueltos</span><span class="sxs-lookup"><span data-stu-id="087f1-150">Return Values</span></span>

- <span data-ttu-id="087f1-151">**NX_SUCCESS**: (0x0) se ha restaurado el registro del cliente.</span><span class="sxs-lookup"><span data-stu-id="087f1-151">**NX_SUCCESS (0x0)** Client record restored</span></span>

- <span data-ttu-id="087f1-152">NX_PTR_ERROR: (0x16) entrada de puntero no válida.</span><span class="sxs-lookup"><span data-stu-id="087f1-152">NX_PTR_ERROR (0x16) Invalid Pointer Input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="087f1-153">Permitido desde</span><span class="sxs-lookup"><span data-stu-id="087f1-153">Allowed From</span></span>

<span data-ttu-id="087f1-154">Subprocesos</span><span class="sxs-lookup"><span data-stu-id="087f1-154">Threads</span></span>

### <a name="example"></a><span data-ttu-id="087f1-155">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="087f1-155">Example</span></span>

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a><span data-ttu-id="087f1-156">Consulte también</span><span class="sxs-lookup"><span data-stu-id="087f1-156">See Also</span></span>

- <span data-ttu-id="087f1-157">nx_dhcpv6_client_get_record</span><span class="sxs-lookup"><span data-stu-id="087f1-157">nx_dhcpv6_client_get_record</span></span>