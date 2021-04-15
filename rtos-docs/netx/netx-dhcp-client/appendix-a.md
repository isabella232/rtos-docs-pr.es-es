---
title: 'Apéndice A: Descripción de la característica de restauración de estado'
description: Con la opción de configuración del cliente Azure RTOS NetX DHDP, NX_DHCP_CLIENT_RESTORE_STATE, un sistema puede restaurar un registro del cliente DHCP creado previamente con un estado Enlazado entre reinicios del sistema.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be8b5dc4885951bee3dba38af6fe5e21b81aa767
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815258"
---
# <a name="appendix-a---description-of-the-restore-state-feature"></a>Apéndice A: Descripción de la característica de restauración de estado

Con la opción de configuración del cliente Azure RTOS NetX DHDP, NX_DHCP_CLIENT_RESTORE_STATE, un sistema puede restaurar un registro del cliente DHCP creado previamente con un estado Enlazado entre reinicios del sistema.

Cuando esta opción está habilitada, la aplicación puede suspender y reanudar el subproceso del cliente DHCP. También hay un servicio para actualizar el cliente DHCP con el tiempo transcurrido entre la suspensión y la reanudación del subproceso.

## <a name="restoring-the-dhcp-client-between-reboots"></a>Restauración del cliente DHCP entre reinicios

Antes de restaurar un cliente DHCP después de un reinicio, un cliente DHCP creado previamente debe alcanzar el estado Enlazado y recibir una dirección IP del servidor DHCP. A continuación, antes del apagado, la aplicación DHCP debe guardar el registro del cliente DHCP actual en la memoria no volátil. También debe haber un "cronometrador" independiente en otro lugar del sistema para realizar un seguimiento del tiempo transcurrido mientras el cliente permanece apagado. Al encenderlo, la aplicación crea una instancia del cliente DHCP y, a continuación, la actualiza con el registro del cliente DHCP creado previamente. El tiempo transcurrido se obtiene del "cronometrador" y, a continuación, se aplica al tiempo restante de la concesión del cliente DHCP. Tenga en cuenta que esta acción puede provocar que el cliente DHCP cambie de estado, por ejemplo, de ENLAZADO a RENOVANDO. Llegados a este punto, la aplicación puede reanudar el cliente DHCP.

Si el tiempo transcurrido durante el apagado hace que el cliente DHCP pase a tener el estado RENOVAR o REENLAZAR, el cliente iniciará automáticamente mensajes DHCP en los que solicitará renovar o reenlazar la concesión de dirección IP. Si la dirección IP ha expirado, el cliente DHCP la borrará automáticamente de la instancia IP y comenzará el proceso DHCP desde el estado INICIALIZACIÓN, solicitando una nueva dirección IP.

De esta manera, el cliente DHCP puede operar entre reinicios como si no se hubiera interrumpido.

A continuación se muestra un ejemplo de esta característica. En él se asume que el cliente DHCP se ejecuta solo en la interfaz principal.

```C
/* On the power up, create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) for the DHCP Client/application
   in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

UINT        status;
UINT        time_elapsed = 0;
NX_DHCP_CLIENT_RECORD client_nv_record;


if (/* The application checks if there is a previously saved DHCP Client record. */)
{


  /* No previously saved Client record. Start the DHCP Client in the INIT state. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  do
  {
  
    /* Wait for DHCP to assign the IP address. */
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
     restore it to the current DHCP Client instance. */

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

## <a name="resuming-the-dhcp-client-thread-after-suspension"></a>Reanudación del subproceso del cliente DHCP tras una suspensión 

Para suspender un subproceso del cliente DHCP sin apagarlo, la aplicación llama a *nx_dhcp_suspend* en un cliente DHCP que ha alcanzado el estado ENLAZADO y tiene una dirección IP válida. Cuando está lista para reanudar el cliente DHCP, primero llama a *nx_dhcp_client_update_time_remaining* con el fin de actualizar el tiempo restante de la concesión de dirección DHCP (obteniendo el tiempo transcurrido de un cronometrador independiente). A continuación, llama a *nx_dhcp_resume* para reanudar el subproceso del cliente DHCP.

Si el tiempo transcurrido hace que el cliente DHCP pase a tener el estado RENOVAR o REENLAZAR, el cliente iniciará automáticamente mensajes DHCP en los que solicitará renovar o reenlazar la concesión de dirección IP. Si la dirección IP ha expirado, el cliente DHCP la borrará automáticamente y comenzará el proceso DHCP desde el estado INICIALIZACIÓN, solicitando una nueva dirección IP.

A continuación se muestra un ejemplo de uso de esta característica.

```C
/* Create an IP instance, DHCP Client, enable ICMP and UDP
   and other resources (not shown) typically in tx_application_define(). */
 
/* Define the DHCP application thread. */     
void    thread_dhcp_client_entry(ULONG thread_input)
{

  /* Start the DHCP Client. */
  status =  nx_dhcp_start(&dhcp_0);

  if (status !=NX_SUCCESS)
    return;

  while(1)
  {
   
    /* Wait for DHCP to obtain an IP address. */
  }

  /* Do tasks with the IP address e.g. send pings to another host on the 
     network... */
  status =  nx_icmp_ping(…);

  if (status !=NX_SUCCESS)
          printf("Failed %d byte Ping!\n", length);

  /* At some later time, suspend the DHCP Client e.g. the device is going to low 
   power mode (sleep) so we do not want any threads to wake it up. */

  nx_dhcp_suspend(&dhcp_0);  

  /* During this suspended state, an independent timer is keeping track of the
     elapsed time. */


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

A continuación figura una lista de servicios para restaurar el estado de un cliente DHCP desde la memoria y para suspenderlo y reanudarlo.

## <a name="nx_dhcp_client_get_record"></a>nx_dhcp_client_get_record

Cree un registro del estado actual del cliente DHCP.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_ client_get_record(NX_DHCP *dhcp_ptr, 
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```

### <a name="description"></a>Descripción

Este servicio guarda en el registro al que apunta record_ptr el cliente DHCP en ejecución en la primera interfaz habilitada para DHCP que se encuentre en la instancia del cliente DHCP. De este modo, la aplicación cliente DHCP puede restaurar el estado de su cliente DHCP después de, por ejemplo, un apagado y un reinicio.

Para guardar un registro del cliente DHCP en una interfaz específica si hay más de una habilitada para DHCP, use el servicio *nx_dhcp_interface_client_get_record*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al cliente DHCP.

- **record_ptr**: puntero al registro del cliente DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x0) Se ha creado un registro del cliente.

- **NX_DHCP_NOT_BOUND**: (0x94) El cliente no tiene el estado Enlazado.

- **NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No hay interfaces habilitadas para DHCP.

- **NX_PTR_ERROR**: (0x16) La entrada de puntero no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_get_record(dhcp_ptr, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_interface_client_get_record"></a>nx_dhcp_interface_client_get_record

Cree un registro del estado actual del cliente DHCP en la interfaz especificada.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_interface_client_get_record(NX_DHCP *dhcp_ptr, 
                                 UINT interface_index,
                                 NX_DHCP_CLIENT_RECORD *record_ptr);
```
### <a name="description"></a>Descripción

Este servicio guarda en el registro al que apunta record_ptr el cliente DHCP en ejecución en la interfaz especificada. De este modo, la aplicación cliente DHCP puede restaurar el estado de su cliente DHCP después de, por ejemplo, un apagado y un reinicio.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al cliente DHCP.

- **interface_index**: índice en el que se obtiene el registro.

- **record_ptr**: puntero al registro del cliente DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x0) Se ha creado un registro del cliente.

- **NX_DHCP_NOT_BOUND**: (0x94) El cliente no tiene el estado Enlazado.

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) El índice de interfaz no es válido.

- NX_PTR_ERROR: (0x16) El puntero DHCP no es válido.

- NX_INVALID_INTERFACE: (0x4C) La interfaz de red no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_DHCP_CLIENT_RECORD dhcp_record;


/* Obtain a record of the current client state on interface 1. */
status=  nx_dhcp_interface_client_get_record(dhcp_ptr, 1, &dhcp_record);

/* If status is NX_SUCCESS dhcp_record contains the current DHCP client record. */
```

## <a name="nx_dhcp_-client_restore_record"></a>nx_dhcp_client_restore_record

Restaure el cliente DHCP a partir de un registro guardado previamente.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_client_restore_record(NX_DHCP *dhcp_ptr, 
                                    NX_DHCP_CLIENT_RECORD       
                                    *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a>Descripción

Con este servicio, una aplicación puede restaurar su cliente DHCP a partir de una sesión anterior con el registro del cliente DHCP al que apunta record_ptr. La entrada time_elapsed se aplica al tiempo restante de la concesión del cliente DHCP.

Para ello, es necesario que la aplicación cliente DHCP haya creado un registro del cliente DHCP antes de apagarlo y haya guardado dicho registro en la memoria no volátil.

Si hay más de una interfaz habilitada para el cliente DHCP, este servicio se aplica a la primera interfaz válida que se encuentre en la instancia de cliente DHCP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al cliente DHCP.

- **record_ptr**: puntero al registro del cliente DHCP.

- **time_elapsed**: tiempo que se debe restar del tiempo de la concesión que queda en el registro del cliente de entrada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x0) Se ha restaurado el registro del cliente.

- **NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No hay interfaces que ejecuten DHCP.

- **NX_PTR_ERROR**: (0x16) La entrada de puntero no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo
```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state. */
status=  nx_dhcp_client_restore_record(client_ptr, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_interace_client_restore_record"></a>nx_dhcp_interace_client_restore_record

Restaure el cliente DHCP en la interfaz especificada a partir de un registro guardado previamente.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_interface_client_restore_record(NX_DHCP *dhcp_ptr, 
                                              NX_DHCP_CLIENT_RECORD       
                                              *record_ptr, ULONG time_elapsed);
```
### <a name="description"></a>Descripción

Con este servicio, una aplicación puede restaurar su cliente DHCP en la interfaz especificada con el registro del cliente DHCP al que apunta record_ptr. La entrada time_elapsed se aplica al tiempo restante de la concesión del cliente DHCP.

Para ello, es necesario que la aplicación cliente DHCP haya creado un registro del cliente DHCP antes de apagarlo y haya guardado dicho registro en la memoria no volátil.

Si hay más de una interfaz habilitada para el cliente DHCP, este servicio se aplica a la primera interfaz válida que se encuentre en la instancia de cliente DHCP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al cliente DHCP.

- **record_ptr**: puntero al registro del cliente DHCP.

- **time_elapsed**: tiempo que se debe restar del tiempo de la concesión que queda en el registro del cliente de entrada.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x0) Se ha restaurado el registro del cliente.

- **NX_DHCP_NOT_BOUND**: (0x94) El cliente no está enlazado a una dirección IP.

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) El índice de interfaz no es válido.

- NX_PTR_ERROR: (0x16) El puntero DHCP no es válido.

- NX_INVALID_INTERFACE: (0x4C) La interfaz de red no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
NX_DHCP_CLIENT_RECORD dhcp_record;
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
Time_elapsed = /* to be determined by application */ 1000; 


/* Obtain a record of the current client state on the primary interface. */
status=  nx_dhcp_interface_client_restore_record(client_ptr, 0, &dhcp_record, time_elapsed);

/* If status is NX_SUCCESS the current DHCP Client pointed to by dhcp_ptr  
   contains the current client record updated for time elapsed during power down. */
```

## <a name="nx_dhcp_-client_update_time_remaining"></a>nx_dhcp_client_update_time_remaining

Actualice el tiempo restante de la concesión del cliente DHCP.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_client_update_time_remaining(NX_DHCP *dhcp_ptr
                                           ULONG time_elapsed);
```
### <a name="description"></a>Descripción

Este servicio actualiza el tiempo restante de la concesión de dirección IP del cliente DHCP con la entrada time_elapsed en la primera interfaz habilitada para DHCP que se encuentre en la instancia de cliente DHCP. La aplicación debe suspender el subproceso del cliente DHCP antes de usar este servicio mediante *nx_dhcp_suspend*. Después de llamar a este servicio, la aplicación puede reanudar el subproceso del cliente DHCP si llama a *nx_dhcp_resume*.

Este servicio está pensado para aplicaciones cliente DHCP que necesitan suspender el subproceso del cliente DHCP durante un período de tiempo y, a continuación, actualizar el tiempo restante de la concesión de dirección IP.

> [!NOTE]
> Este servicio no está diseñado para usarse con *nx_dhcp_client_get_record* ni *nx_dhcp_client_restore_record* (descritos previamente). Estos servicios se han descrito anteriormente en esta sección.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al cliente DHCP.

- **time_elapsed**: tiempo que se debe restar del que queda en la concesión de dirección IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x0) La concesión de dirección IP del cliente se ha actualizado.

- **NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No hay interfaces habilitadas para DHCP.

- **NX_PTR_ERROR**: (0x16) La entrada de puntero no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease. */
status=  nx_dhcp_client_update_time_remaining(client_ptr, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_interface_client_update_time_remaining"></a>nx_dhcp_interface_client_update_time_remaining

Actualice el tiempo restante de la concesión del cliente DHCP en la interfaz especificada.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_interface_client_update_time_remaining(NX_DHCP *dhcp_ptr,
                                                     UINT interface_index,
                                                     ULONG time_elapsed);
```
### <a name="description"></a>Descripción

Este servicio actualiza el tiempo restante de la concesión de dirección IP del cliente DHCP con la entrada time_elapsed en la interfaz especificada si dicha interfaz está habilitada para DHCP. La aplicación debe suspender el subproceso del cliente DHCP antes de usar este servicio mediante *nx_dhcp_suspend*. Después de llamar a este servicio, la aplicación puede reanudar el subproceso del cliente DHCP si llama a *nx_dhcp_resume*. Tenga en cuenta que la suspensión y la reanudación del subproceso del cliente DHCP se aplican a todas las interfaces habilitadas para DHCP.

Este servicio está pensado para aplicaciones cliente DHCP que necesitan suspender el subproceso del cliente DHCP durante un período de tiempo y, a continuación, actualizar el tiempo restante de la concesión de dirección IP.

> [!NOTE] 
> Este servicio no está diseñado para usarse con *nx_dhcp_client_get_record* ni *nx_dhcp_client_restore_record* (descritos previamente). Estos servicios se han descrito anteriormente en esta sección.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al cliente DHCP.

- **interface_index**: índice de interfaz al que se debe aplicar el tiempo transcurrido.

- **time_elapsed**: tiempo que se debe restar del que queda en la concesión de dirección IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x0) La concesión de dirección IP del cliente se ha actualizado.

- **NX_DHCP_BAD_INTERFACE_INDEX_ERROR**: (0x9A) El índice de interfaz no es válido.

- NX_PTR_ERROR: (0x16) El puntero DHCP no es válido.

- NX_INVALID_INTERFACE: (0x4C) La interfaz de red no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
ULONG       time_elapsed;

/* Obtain time (timer ticks) elapsed from independent time keeper. */
time_elapsed = /* to be determined by application */ 1000; 


/* Apply the elapsed time to the DHCP Client address lease on interface 1. */
status=  nx_dhcp_interface_client_update_time_remaining(client_ptr, 1, time_elapsed);

/* If status is NX_SUCCESS the DHCP Client is updated for time elapsed. */
```


## <a name="nx_dhcp_suspend"></a>nx_dhcp_suspend

Suspenda el subproceso del cliente DHCP.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_suspend(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a>Descripción

Este servicio suspende el subproceso del cliente DHCP en curso. Tenga en cuenta que, a diferencia de *nx_dhcp_stop*, el estado del cliente DHCP no sufre ningún cambio cuando se llama a este servicio.

Este servicio suspende el cliente DHCP en ejecución en todas las interfaces habilitadas para DHCP.

Para actualizar el estado del cliente DHCP con el tiempo transcurrido mientras el cliente permanece suspendido, vea la descripción anterior de *nx_dhcp_client_update_time_remaining*. Para reanudar un subproceso del cliente DHCP suspendido, la aplicación debe llamar a *nx_dhcp_resume*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al cliente DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x0) Se ha suspendido el subproceso del cliente.

- **NX_PTR_ERROR**: (0x16) La entrada de puntero no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Pause the DHCP client thread. */
status=  nx_dhcp_suspend(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is paused. */
```


## <a name="nx_dhcp_resume"></a>nx_dhcp_resume

Reanude un subproceso del cliente DHCP suspendido.

### <a name="prototype"></a>Prototipo

```C
ULONG nx_dhcp_resume(NX_DHCP *dhcp_ptr);
```
### <a name="description"></a>Descripción

Este servicio reanuda un subproceso del cliente DHCP suspendido. Tenga en cuenta que el estado del cliente DHCP no sufre ningún cambio al reanudarse el subproceso. Para actualizar el tiempo restante de la concesión de dirección IP del cliente DHCP con el tiempo transcurrido antes de llamar a *nx_dhcp_resume*, vea la descripción anterior de *nx_dhcp_client_update_time_remaining*.

Este servicio reanuda el cliente DHCP en ejecución en todas las interfaces habilitadas para DHCP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al cliente DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x0) Se ha reanudado el subproceso del cliente.

- NX_PTR_ERROR: (0x16) La entrada de puntero no es válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Resume the DHCP client thread. */
status=  nx_dhcp_resume(client_ptr);

/* If status is NX_SUCCESS the current DHCP Client thread is resumed. */
```