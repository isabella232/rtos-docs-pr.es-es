---
title: 'Apéndice A: Descripción de la característica de restauración de estado para los servicios del cliente DHCPv6 de Azure RTOS NetX Duo'
description: Con la opción de configuración del cliente DHCPv6 de Azure RTOS NetX Duo, NX_DHCPV6_CLIENT_RESTORE_STATE, un sistema puede restaurar un cliente DHCP creado previamente con un estado Enlazado entre reinicios del sistema.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6840f89e66d713b1839ac84427b73273b3f9601d4b6d9d39cd94908ac77a77ca
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791336"
---
# <a name="appendix-a---description-of-the-restore-state-feature-for-azure-rtos-netx-duo-dhcpv6-client"></a>Apéndice A: Descripción de la característica de restauración de estado para los servicios del cliente DHCPv6 de Azure RTOS NetX Duo

Con la opción de configuración del cliente DHCPv6 de Azure RTOS NetX Duo, NX_DHCPV6_CLIENT_RESTORE_STATE, un sistema puede restaurar un cliente DHCP creado previamente con un estado Enlazado entre reinicios del sistema.

Esta opción también permite que una aplicación suspenda el subproceso del cliente DHCPv6 y lo reanude, actualizado con el tiempo transcurrido entre la suspensión y la reanudación del subproceso sin necesidad de apagarse.

## <a name="restoring-the-dhcpv6-client-between-reboots"></a>Restauración del cliente DHCPv6 entre reinicios

Para restaurar un cliente DHCPv6 entre reinicios, la aplicación DHCPv6 crea una instancia del cliente DHCPv6 y, a continuación, obtiene una concesión de dirección IP mediante el protocolo DHCPv6 normal y llama a *nx_dhcpv6_start*. A continuación, la aplicación DHCPv6 espera a que se complete el protocolo. Si todo va bien, el dispositivo consigue el estado BOUND con una dirección IP válida asignada desde su servidor DHCPv6. Antes de que se apague, la aplicación cliente DHCPv6 guarda la instancia del cliente DHCPv6 actual en un registro de cliente DHCPv6 que luego se almacena en memoria no volátil. Un "cronometrador" independiente en otro lugar del sistema realiza un seguimiento del tiempo transcurrido durante este estado de apagado. Al encenderse, la aplicación crea una instancia del cliente DHCPv6 y, a continuación, la actualiza con el registro del cliente DHCPv6 creado previamente. El tiempo transcurrido se obtiene del "tiempo de espera" y, a continuación, se aplica al tiempo restante en la concesión de Clientv6 DHCP. En este momento, la aplicación puede reanudar el cliente DHCPv6.

Si el tiempo transcurrido durante el apagado hace que el cliente DHCPv6 pase a tener el estado RENEW o REBIND, el cliente DHCPv6 iniciará automáticamente mensajes DHCPv6 en los que solicitará renovar o reenlazar la concesión de dirección IP. Si la dirección IP ha expirado, el cliente DHCPv6 la borrará automáticamente de la instancia IP y comenzará el proceso DHCPv6 desde el estado INIT, solicitando una nueva dirección IP.

De esta manera, el cliente DHCPv6 puede operar entre reinicios como si no se interrumpa.

A continuación se muestra un ejemplo de esta característica.

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

## <a name="nx_dhcpv6_client_get_record"></a>nx_dhcpv6_client_get_record

Crear un registro del estado actual del cliente DHCPv6.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcpv6_client_get_record(NX_DHCPV6 *dhcpv6_ptr, 
                                  NX_DHCPV6_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Descripción

Este servicio guarda el cliente DHCPv6 en el registro al que apunta record_ptr. Esto permite que la aplicación cliente DHCPv6 restaure su estado de cliente DHCPv6 después de, por ejemplo, un apagado y un reinicio.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr**: puntero al cliente DHCPv6.

- **record_ptr**: puntero al registro del cliente DHCPv6.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS (0X0)** : se ha creado un registro del cliente válido.

- El cliente **NX_DHCPV6_NOT_BOUND** (0xE94) no tiene el estado BOUND, por lo que no tiene asignada una dirección IP válida.

- **NX_PTR_ERROR**: (0x16) entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;


/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_get_record(&dhcpv6_ptr, &dhcpv6_record);

/* If status is NX_SUCCESS dhcpv6_record contains the current DHCPv6 client record. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_client_restore_record

## <a name="nx_dhcpv6_client_restore_record"></a>nx_dhcpv6_client_restore_record

Restaura el estado del cliente DHCPv6 desde un registro guardado.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcpv6_client_restore_record(NX_DHCPV6 *dhcpv6_ptr, 
                                      NX_DHCPV6_CLIENT_RECORD       
                                      *record_ptr, ULONG time_elapsed);
```

### <a name="description"></a>Descripción

Este servicio permite a una aplicación DHCPv6 volver a crear su estado de cliente DHCPv6 desde una sesión anterior actualizando el cliente DHCPv6 con el registro del cliente DHCPv6 al que apunta record_ptr, y actualiza el tiempo restante en la concesión del cliente DHCPv6 con la entrada time_elapsed. Esto permite a la aplicación cliente DHCPv6 volver a crear su cliente DHCPv6, por ejemplo, después de apagarse. Para ello, es necesario que la aplicación cliente DHCPv6 haya creado un registro del cliente DHCPv6 antes de apagarlo y haya guardado dicho registro en la memoria no volátil.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr**: puntero al cliente DHCPv6.

- **record_ptr**: puntero al registro del cliente DHCPv6.

- **time_elapsed**: tiempo que se debe restar del tiempo de la concesión que queda en el registro del cliente de entrada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x0) se ha restaurado el registro del cliente.

- NX_PTR_ERROR: (0x16) entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_DHCPV6_CLIENT_RECORD dhcpv6_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 

/* Obtain a record of the current client state. */
status=  nx_dhcpv6_client_restore_record(&dhcpv6_ptr, &dhcpv6_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCPv6 Client pointed to by dhcpv6_ptr contains the current client record updated for time elapsed during power down. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_client_get_record