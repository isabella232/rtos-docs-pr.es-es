---
title: 'Capítulo 4: Servicios de servidor DHCPv6 de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios de servidor DHCPv6 de NetX Duo
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814738"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a>Capítulo 4: Servicios de servidor DHCPv6 de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios de servidor DHCPv6 de NetX Duo (enumerados a continuación).

En la sección “Valores devueltos” de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- nx_dhcpv6_server_create *Crear una instancia de servidor DHCPv6*
- nx_dhcpv6_server_delete *Eliminar una instancia de servidor DHCPv6*
- nx_dhcpv6_server_start *Iniciar una tarea de servidor DHCPv6*
- nx_dhcpv6_server_suspend *Suspender la tarea de servidor DHCPv6*
- nx_dhcpv6_server_resume *Reanudar el procesamiento del cliente DHCPv6*
- nx_dhcpv6_server_suspend *Suspender el procesamiento del cliente DHCPv6*
- nx_dhcpv6_create_dns_address *Establecer el servidor DNS para las solicitudes de opción*
- nx_dhcpv6_create_ip_address_range *Crear el intervalo de direcciones IP que se va a conceder*
- nx_dhcpv6_reserve_ip_address_range *Reservar el intervalo de direcciones IP en la lista de servidores*
- nx_dhcpv6_set_server_duid *Establecer el DUID de servidor para paquetes DHCPv6*
- nx_dhcpv6_add_ip_address_lease *Agregar un registro de concesión a la tabla de servidor DHCPv6*
- Nx_dhcpv6_retrieve_ip_address_lease *Recuperar un registro de concesión de direcciones IP de la tabla de servidor*
- nx_dhcpv6_add_client_record *Agregar un registro de cliente DHCPv6 a la tabla de servidor*
- nx_dhcpv6_retrieve_client_record *Recuperar un registro de cliente de la tabla de servidor*
- nx_dhcpv6_server_interface_set *Establecer el índice de interfaz para los servicios DHCPv6 de servidor*
- nx_dhcpv6_server_option_request_handler_set *Establecer el controlador de solicitudes de opción*

## <a name="nx_dhcpv6_create_dns_address"></a>nx_dhcpv6_create_dns_address

### <a name="set-the-network-dns-server"></a>Establecimiento del servidor DNS de red

**Prototipo**

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

**Descripción**

Este servicio carga el servidor DHCPv6 con la dirección del servidor DNS para la interfaz de red DHCPv6 del servidor.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **dns_ipv6_address**: puntero al servidor DNS

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor DNS guardado en la instancia del servidor DHCPv6.
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Se proporciona una dirección no válida.
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a>nx_dhcpv6_create_ip_address_range

### <a name="create-the-server-ip-address-list"></a>Creación de la lista de direcciones IP del servidor

**Prototipo**

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

**Descripción**

Este servicio crea la lista de direcciones IP especificada por las direcciones de inicio y finalización del intervalo de direcciones asignables del servidor. Las direcciones de inicio y finalización deben coincidir con el prefijo de dirección de la interfaz del servidor (debe estar en el mismo vínculo que la interfaz DHCPv6 del servidor). Se devuelve el número de direcciones realmente agregadas.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **start_ipv6_address**: inicio de las direcciones que se van a agregar
- **end_ipv6_address**: fin de las direcciones que se van a agregar
- ***addresses_added**: salida de las direcciones agregadas

**Valores devueltos**

- **NX_SUCCESS** (0x00) Lista de direcciones IP creadas correctamente
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Se proporciona una dirección no válida.
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a>nx_dhcpv6_reserve_ip_address_range

### <a name="reserve-specified-range-of-ip-addresses"></a>Reservar el intervalo de direcciones IP especificado

**Prototipo**

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

**Descripción**

Este servicio reserva el intervalo de direcciones IP especificado por las direcciones de inicio y finalización. Estas direcciones deben estar dentro del intervalo de direcciones IP del servidor creado previamente. Estas direcciones no se asignarán a ningún cliente por parte del servidor DHCPv6. Las direcciones de inicio y finalización deben coincidir con el prefijo de dirección de la interfaz del servidor (debe estar en el mismo vínculo que la interfaz de red DHCPv6 del servidor). Se devuelve el número de direcciones realmente reservadas.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **start_ipv6_address**: inicio de las direcciones que se van a reservar
- **end_ipv6_address**: fin de las direcciones que se van a reservar
- ***addresses_reserved** Número de direcciones reservadas

**Valores devueltos**

- **NX_SUCCESS** (0x00) Mensaje de LIBERACIÓN creado y procesado correctamente
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Se proporciona una dirección no válida.
- **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) No se encontró la dirección de inicio en la lista de direcciones del servidor.
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a>nx_dhcpv6_server_create

### <a name="create-the-dhcpv6-server-instance"></a>Creación de la instancia del servidor DHCPv6 

**Prototipo**

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

**Descripción**

Este servicio crea la tarea de servidor DHCPv6 con la entrada especificada. Los controladores de devolución de llamada son entradas opcionales. Se requieren la entrada del puntero de pila, de la instancia de IP y del grupo de paquetes. La instancia de IP y el grupo de paquetes ya deben estar creados.

Se recomienda que el usuario llame a nx_dhcpv6_server_option_request_handler_set para establecer el controlador de solicitudes de opción.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **ip_ptr**: puntero a la instancia de IP
- **name_str**: puntero al nombre del servidor
- **packet_pool_ptr**: puntero al grupo de paquetes del servidor
- **stack_ptr**: puntero a la memoria de pila del cliente
- **stack_size**: tamaño de la memoria de pila del servidor
- **dhcpv6_address_declined_handler**: puntero al controlador de mensajes de rechazo o liberación del cliente
- **dhcpv6_option_request_handler**: puntero al controlador de opción de solicitud de opciones

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor reanudado correctamente.
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.
- NX_DHCPV6_PARAM_ERROR Entrada que no es de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a>nx_dhcpv6_server_delete

### <a name="delete-the-dhcpv6-server"></a>Eliminación del servidor DHCPv6

**Prototipo**

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Descripción**

Este servicio elimina la tarea del servidor DHCPv6 y cualquier solicitud que el servidor estaba procesando.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor eliminado correctamente
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Subprocesos

**Ejemplo**

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a>nx_dhcpv6_server_resume

### <a name="resume-dhcpv6-server-task"></a>Reanudación de la tarea del servidor DHCPv6 

**Prototipo**

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Descripción**

Este servicio reanuda la tarea del servidor DHCPv6 y cualquier solicitud que el servidor estaba procesando.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor reanudado correctamente.
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) El servidor de ya se está ejecutando
- **status** (variable) Estado de error de ThreadX y NetX Duo
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Subprocesos

**Ejemplo**

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a>nx_dhcpv6_server_suspend

### <a name="suspend-dhcpv6-server-task"></a>Suspensión de la tarea del servidor DHCPv6 

**Prototipo**

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Descripción**

Este servicio suspende la tarea del servidor DHCPv6 y cualquier solicitud que el servidor estaba procesando.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor reanudado correctamente.
- **NX_DHCPV6_NOT_STARTED** (0xE92) El servidor no se ha iniciado 
- **Status** (variable) Estado de error de ThreadX y NetX Duo
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Subprocesos

**Ejemplo**

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a>nx_dhcpv6_server_start

### <a name="start-the-dhcpv6-server-task"></a>Inicio de la tarea del servidor DHCPv6 

**Prototipo**

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Descripción**

Este servicio inicia la tarea del servidor DHCPv6 y prepara al servidor para procesar las solicitudes de la aplicación para recibir mensajes del cliente DHCPv6. Comprueba que la instancia de servidor tiene suficiente información (DUID de servidor), crea y enlaza el socket UDP para enviar y recibir mensajes DHCPv6 y activa temporizadores para realizar un seguimiento del tiempo de sesión y de la expiración de la concesión de IP.

>[!NOTE] 
> Antes de que el servidor DHCPv6 pueda ejecutarse, la aplicación host es responsable de crear el intervalo de direcciones IP desde el que el servidor puede asignar direcciones IP. También es responsable de establecer el DUID del servidor y la interfaz DHCPv6 (consulte *nx_dhcpv6_server_duid_set* y *nx_dhcpv6_server_interface_set*, respectivamente).

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor iniciado correctamente
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) El servidor de ya se está ejecutando
- **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) El servidor de no tiene direcciones asignables para conceder
- **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Índice de direcciones global sin establecer
- **NX_DHCPV6_NO_SERVER_DUID** (0xE92) No se creó ningún DUID de servidor 
- **status** (variable) Estado de error de ThreadX y NetX Duo
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Subprocesos

**Ejemplo**

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a>nx_dhcpv6_retrieve_ip_address_lease

### <a name="get-an-ip-address-lease-from-the-server-table"></a>Obtención de una concesión de dirección IP de la tabla de servidor

**Prototipo**

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

**Descripción**

Este servicio recupera un registro de concesión de direcciones IP de la tabla de servidor en la ubicación de índice de tabla especificada. Esto se puede hacer antes o después de recuperar los datos de registro del cliente.

La capacidad de almacenar y recuperar datos entre el servidor DHCPv6 y la memoria no volátil es un requisito del protocolo DHCPv6. No importa en qué orden se guardan los datos de concesión de IP y los datos de registro del cliente en la memoria no volátil.

>[!NOTE] 
> No se recomienda copiar datos a las tablas de servidores o desde estas sin detener o suspender primero el servidor DHCPv6.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **table_index**: índice de tabla en el que almacenar la concesión
- **lease_IP_address**: puntero a la dirección IP concedida al cliente
- **T1**: tiempo de renovación solicitado por el cliente
- **T2**: tiempo de reenlace solicitado por el cliente
- **valid_lifetime**: la concesión del cliente queda en desuso
- **preferred_lifetime**: la concesión del cliente deja de ser válida

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor iniciado correctamente
- **NX_DHCPV6_PARAMETER_ERROR** (0xE93) Entrada de datos de concesión de IP no válida
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a>nx_dhcpv6_add_ip_address_lease

### <a name="add-an-ip-address-lease-to-the-server-table"></a>Incorporación de una concesión de dirección IP de la tabla de servidor

**Prototipo**

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

**Descripción**

Este servicio carga los datos de concesión de IP de una sesión de servidor DHCPv6 anterior desde memoria no volátil a la tabla de concesión del servidor. Esto no es necesario si el servidor se ejecuta por primera vez y no tiene datos de concesión anteriores. Si este es el caso, la aplicación host debe crear un intervalo de direcciones IP para asignar direcciones IP mediante el servicio *nx_dhcpv6_create_ip_address_range*. Los datos son suficientes para reconstruir un registro de concesiones DHCPv6. No es necesario especificar el índice de tabla. Si se establece en 0xFFFFFFFF (infinito), el servidor DHCPv6 encontrará la siguiente ranura disponible en la que copiar los datos.

>[!NOTE] 
> La carga de los datos de concesión de IP debe realizarse antes de cargar los registros de cliente; ambas acciones DEBEN realizarse antes de volver a iniciar el servidor DHCPv6.

La capacidad de almacenar y recuperar datos entre el servidor DHCPv6 y la memoria no volátil es un requisito del protocolo DHCPv6.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **table_index**: índice de tabla en el que almacenar la concesión
- **lease_IP_address**: puntero a la dirección IP concedida al cliente
- **T1**: tiempo de renovación solicitado por el cliente
- **T2**: tiempo de reenlace solicitado por el cliente
- **valid_lifetime**: la concesión del cliente queda en desuso
- **preferred_lifetime**: la concesión del cliente deja de ser válida

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor iniciado correctamente
- **NX_DHCPV6_TABLE_FULL** (0xEC4) No hay espacio para más datos de concesión**
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Los datos de concesión de no parecen estar en el vínculo con la interfaz DHCPv6 del servidor
- **NX_DHCPV6_PARAM_ERROR** (0xE93) Entrada de datos de concesión de IP no válida
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a>nx_dhcpv6_add_client_record

### <a name="add-a-client-record-to-the-server-table"></a>Incorporación de un registro de cliente a la tabla de servidor

**Prototipo**

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

**Descripción**

Este servicio copia los datos de cliente desde la memoria no volátil a la tabla de servidor de un registro a la vez. Esto solo es necesario si el servidor se está reiniciando y tiene datos de cliente de una sesión anterior para restaurar desde la memoria. Si un servidor no tiene datos anteriores, el servidor DHCPv6 inicializará la tabla de cliente para poder agregar registros de cliente.

No es necesario especificar el índice de la tabla. Si se establece en 0xFFFFFFFF (infinito), el servidor DHCPv6 buscará la siguiente ranura disponible. El servidor DHCPv6 puede reconstruir un registro de cliente a partir de estos datos.

>[!NOTE] 
> La aplicación host DEBE cargar los datos de concesión de IP ANTES de los datos de registro del cliente. Esto es para que, internamente, el servidor DHCPv6 pueda vincular las tablas de modo que cada registro de cliente se una con su correspondiente registro de concesión de IP en sus tablas correspondientes. Consulte *nx_dhcpv6_add_ip_address_lease* para obtener más información sobre cómo cargar los datos de concesión de IP desde la memoria.

>[!NOTE] 
> En función del tipo de DUID, no se deben proporcionar todos los datos. Por ejemplo, si un cliente tiene un tipo de DUID asignado por el proveedor, puede enviar cero para los parámetros del nivel de vínculo de DUID (dirección MAC, tipo de hardware, hora de DUID).

La capacidad de almacenar y recuperar datos entre el servidor DHCPv6 y la memoria no volátil es un requisito del protocolo DHCPv6.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor iniciado correctamente
- **NX_INVALID_PARAMETERS** (0x4D) Entrada que no es de puntero no válida.**
- **NX_DHCPV6_TABLE_FULL** (0xEC4) No quedan ranuras vacías para agregar otro registro de cliente
- **NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) No se encontró la dirección asignada del cliente en la tabla de concesión del servidor.
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a>nx_dhcpv6_retrieve_client_record

### <a name="retrieve-a-client-record-from-the-server-table"></a>Recuperación de un registro de cliente de la tabla de servidor

**Prototipo**

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

**Descripción**

Este servicio copia los datos esenciales de la tabla de registros de cliente del servidor para el almacenamiento en memoria no volátil. El servidor puede reconstruir un registro de cliente adecuado a partir de estos datos en el proceso inverso (carga de datos en la tabla de servidor). Independientemente del tipo de DUID, ninguno de los punteros puede ser NULL; los datos se inicializan en cero para todos los parámetros. Por ejemplo, si el tipo de DUID de cliente es el nivel de vínculo más el tiempo, el número de proveedor se devuelve como cero y el identificador privado es una cadena vacía.

La capacidad de almacenar y recuperar datos entre el servidor DHCPv6 y la memoria no volátil es un requisito del protocolo DHCPv6. No importa en qué orden se guardan los datos de concesión de IP y los datos de registro del cliente en la memoria no volátil.

>[!NOTE] 
> No se recomienda copiar datos a las tablas de servidores o desde estas sin detener o suspender primero el servidor DHCPv6.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **table_index**: índice en la tabla de cliente del servidor
- **message_xid**: identificador de la transacción cliente/servidor
- **client_address**: dirección IPv6 concedida al cliente
- **client_state**: estado de DHCPv6 del cliente (por ejemplo, enlazado)
- **IP_lease_time_accrued**: el tiempo expiró en el puntero **dhcpv6_server_ptr** al servidor DHCPv6
- **dhcpv6_server_ptr**: puntero al servidor DHCPv6

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor iniciado correctamente
- **NX_DHCPV6_INVALID_DUID** (0xECC) Datos de DUID no válidos o incoherentes
- **NX_PTR_ERROR**(0x16) Entrada de puntero no válida.
- NX_INVALID_PARAMETERS (0x4D) Entrada que no es de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a>nx_dhcpv6_server_interface_set

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a>Establecimiento del índice de interfaz para la interfaz DHCPv6 del servidor

**Prototipo**

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

**Descripción**

Este servicio establece la interfaz de red en la que el servidor DHCPv6 controla las solicitudes del cliente DHCPv6. No en el caso de las versiones de NetX Duo que no admiten varios host, el valor predeterminado de la interfaz es cero. El índice de direcciones globales es necesario para obtener la dirección global del servidor en su interfaz DHCPv6. La lógica DHCPv6 usa esto para asegurarse de que las direcciones de concesión y otros datos de DHCPv6 están vinculados al servidor DHCPv6.

Se debe llamar antes de que se inicie el servidor DHCPv6, incluso en el caso de las aplicaciones en dispositivos de host único o no compatibles con varios host.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **iface_index**: interfaz de servidor del servidor DHCPv6
- **ga_address_index**: índice de la dirección global del servidor en la tabla de direcciones de la instancia de IP del servidor

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor iniciado correctamente
- **NX_INVALID_INTERFACE** (0x4C) La interfaz no existe
- NX_NO_INTERFACE_ADDRESS (0x50) El índice global supera el número máximo de direcciones IPv6 de la instancia IP (NX_MAX_IPV6_ADDRESSES)
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a>nx_dhcpv6_set_server_duid

### <a name="set-the-server-duid-for-dhcpv6-packets"></a>Establecimiento del DUID de servidor para paquetes DHCPv6

**Prototipo**

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

**Descripción**

Este servicio establece el DUID del servidor y se debe llamar antes de que la aplicación host inicie el servidor. En cuanto a la capa de vínculo y los tipos de DUID de tiempo de capa de vínculo, la aplicación host debe proporcionar el tipo de hardware y los datos de dirección MAC. Para DUID de tiempo de nivel de vínculo, el puntero de tiempo debe apuntar a una hora válida. El número de segundos transcurridos desde el 1 de enero de 2000 es un valor de inicialización típico. Si el tipo de DUID del servidor es empresarial, tipo asignado por el proveedor, el DUID se creará a partir de las opciones configurables por el usuario NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID y NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, y los valores de la tiempo y dirección MAC pueden establecerse en NULL.

>[!NOTE] 
> Es responsabilidad de la aplicación host guardar los parámetros de DUID del servidor en memoria no volátil, de modo que use el mismo DUID en los mensajes para los clientes entre reinicios. Se trata de un requisito del protocolo DHCPv6 (RFC 3315).

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **duid_type**: tipo de DUID de servidor DHCPv6
- **hardware_type**: tipo de hardware (por ejemplo, Ethernet)
- **mac_address_msw**: puntero al servidor DHCPv6
- **mac_address_lsw**: puntero al servidor DHCPv6
- **time**: valor de tiempo para DUID

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor suspendido correctamente
- **NX_DHCPV6_INVALID_SERVER_DUID** (0xE98) Tipo de DUID desconocido o no admitido
- **NX_INVALID_PARAMETERS** (0x4D) Entrada que no es de puntero no válida.
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a>nx_dhcpv6_server_option_request_handler_set

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a>Establecimiento del controlador de solicitud de opción para la instancia del servidor DHCPv6 

**Prototipo**

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

**Descripción**

Este servicio establece el controlador de solicitud de opciones extendidas del servidor DHCPv6.

**Parámetros de entrada**

- **dhcpv6_server_ptr**: puntero al servidor DHCPv6
- **dhcpv6_option_request_handler_extended**: puntero al controlador de solicitud de opciones extendidas

**Valores devueltos**

- **NX_SUCCESS** (0x00) Servidor reanudado correctamente.
- NX_PTR_ERROR (0x16) Entrada de puntero no válida.

**Permitido desde**

Código de aplicación

**Ejemplo**

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```