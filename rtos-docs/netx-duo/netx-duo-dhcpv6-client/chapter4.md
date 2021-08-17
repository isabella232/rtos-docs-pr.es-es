---
title: 'Capítulo 4: Servicios de cliente DHCPv6 de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del cliente Azure RTOS NetX Duo DHCPv6 incluidos a continuación por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6caf943f990f8fe5cbd2cd6139a1253fcaf47dc207141963e31a9e31864ef839
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791744"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a>Capítulo 4: Servicios de cliente DHCPv6 de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios del cliente Azure RTOS NetX Duo DHCPv6 incluidos a continuación por orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_dhcpv6_client_create:** *Creación de una instancia de cliente DHCPv6* 

- **nx_dhcpv6_client_delete:** *Eliminación de una instancia de cliente DHCPv6* 

- **nx_dhcpv6_create_ client_duid:** *Creación de un DUID de cliente DHCPv6* 

- **nx_dhcpv6 _add_client_ia:** *Agregar una dirección de identidad de cliente DHCPv6 (IA)* 

- **nx_dhcpv6 _create_client_ia:** (*Heredado agregar una dirección de identidad de cliente DHCPv6 (IA))* 

- **nx_dhcpv6_create_client_iana:** *Creación de una asociación de identidad de cliente Dhcpv6 para direcciones no temporales (IANA)* 

- **nx_dhcpv6_get_client_duid_time_id:** *Obtener el id. de hora del DUID del cliente DHCPv6* 

- **nx_dhcpv6_client_set_interface:** *Establecer la interfaz de red de cliente para las comunicaciones con el servidor DHCPv6* 

- **nx_dhcpv6_get_IP_address:** *Obtener la dirección IPv6 global asignada al cliente DHCPv6* 

- **nx_dhcpv6_get_lease_time_data:** *Obtener las duraciones T1 y T2 válidas y preferidas para la dirección IPv6 global del cliente*

- **nx_dhcpv6_get_valid_ip_address_lease_time:** *Obtener las duraciones T1 y T2 válidas y preferidas para la dirección IPv6 del cliente DHCPv6 por índice de dirección* 

- **nx_dhcpv6_get_iana_lease_time:** *Obtener T1 y T2 en la Asociación de identidad (IANA) concedida al cliente DHCPv6* 

- **nx_dhcpv6_get_other_option_data:** *Obtener los datos de opción especificados, por ejemplo, el nombre de dominio o el servidor de zona horaria* 

- **nx_dhcpv6_get_DNS_server_address:** *Obtener la dirección del servidor DNS en el índice especificado de la lista de servidores DNS de cliente DHCPv6* 

- **nx_dhcpv6_get_time_accrued:** *Obtener el tiempo acumulado que la concesión de la dirección IPv6 global se ha vinculado al cliente DHCPv6* 

- **nx_dhcpv6_get_time_server_address:** *Obtener la dirección del servidor de tiempo en el índice especificado de la lista de servidores de tiempo de cliente DHCPv6*

- **nx_dhcpv6_get_valid_ip_address_count:** *Obtener el número de direcciones IPv6 asignadas al cliente DHCPv6* 

- **nx_dhcpv6_reinitialize:** *Reinicialice DHCPv6 para reiniciar la máquina de Estados cliente DHCPv6 y reejecutar el protocolo DHCPv6* 

- **nx_dhcpv6_request_confirm:** *Enviar una solicitud de confirmación al Servidor* 

- **nx_dhcpv6_request_inform_request:** E *nviar un mensaje de SOLICITUD DE INFORME al servidor* 

- **nx_dhcpv6_request_release:** *Enviar una solicitud de VERSIÓN al servidor* 

- **nx_dhcpv6_request_option_DNS_server:** *Agregar la opción de servidor DNS a la opción de Cliente solicitar datos en mensajes de solicitud al servidor* 

- **nx_dhcpv6_request_option_FQDN:** *Agregar la opción FQDN a la opción de cliente solicitar datos en los mensajes de solicitud al servidor* 

- **nx_dhcpv6_request_option_domain_name:** *Agregar la opción de nombre de dominio a la opción de cliente solicitar datos en los mensajes de solicitud al servidor* 

- **nx_dhcpv6_request_option_time_server:** *Agregar la opción de servidor de tiempo a la opción de cliente solicitar datos en mensajes de solicitud al servidor* 

- **nx_dhcpv6_request_option_timezone:** *Agregar la opción de zona horaria a la opción de cliente solicitar datos en los mensajes de solicitud al servidor* 

- **nx_dhcpv6_request_solicit:** *Enviar una solicitud de PETICIÓN DHCPv6 a cualquier servidor de la red de cliente (difusión)* 

- **nx_dhcpv6_request_solicit_rapid:** *Enviar una solicitud de PETICIÓN DHCPv6 a cualquier servidor de la red de cliente (difusión) con la opción de confirmación rápida establecida* 

- **nx_dhcpv6_resume:** *Reanudar el procesamiento del cliente DHCPv6* 

- **nx_dhcpv6_start:** *Inicie la tarea de subproceso de cliente DHCPv6. Tenga en cuenta que esto no es equivalente a iniciar la máquina de estados DHCPv6 y no envía una solicitud de PETICIÓN* 

- **nx_dhcpv6_stop:** *Detener la tarea de subproceso de cliente DHCPv6* 

- **nx_dhcpv6_suspend:** *Suspender la tarea de subproceso de cliente DHCPv6* 

- **nx_dhcpv6_set_time_accrued:** *Establezca el tiempo acumulado en la concesión de la dirección IPv6 del cliente global en el registro de cliente.*

## <a name="nx_dhcpv6_client_create"></a>nx_dhcpv6_client_create

Crear una instancia de cliente DHCPv6

### <a name="prototype"></a>Prototipo

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente DHCPv6 que incluye funciones de devolución de llamada.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero al bloque de control DHCPv6  

- **ip_ptr** Puntero a la instancia de IP del cliente  

- **name_ptr** Puntero al nombre de la instancia de DHCPv6

- **packet_pool_ptr** Puntero al grupo de paquetes del cliente

- **stack_ptr** Puntero a la memoria de pila de cliente

- **stack_size** Tamaño de la memoria de pila de cliente

- **dhcpv6_state_change_notify** Puntero a la función de devolución de llamada que se invoca cuando el cliente inicia una nueva solicitud DHCPv6 al servidor

- **dhcpv6_server_error_handler** Puntero a la función de devolución de llamada que se invoca cuando el cliente recibe un estado de error del servidor

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Creación correcta del cliente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_client_delete

## <a name="nx_dhcpv6_client_delete"></a>nx_dhcpv6_client_delete

Eliminación de una instancia de cliente DHCPv6

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente DHCPv6 creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta de DHCPv6

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_client_create

## <a name="nx_dhcpv6_client_set_interface"></a>nx_dhcpv6_client_set_interface

Establece la interfaz de red del cliente para DHCPv6

### <a name="prototype"></a>Prototipo

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a>Descripción

Este servicio establece la interfaz de red del cliente para comunicarse con los servidores DHCPv6 en el índice de interfaz de entrada especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **interface_index** Índice que indica la interfaz de red

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se estableció correctamente la interfaz

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_INVALID_INTERFACE (0x4C) Entrada de índice de interfaz no válida

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_client_set_destination_address"></a>nx_dhcpv6_client_set_destination_address

Establece la dirección de destino a la que se debe enviar el mensaje DHCPv6

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección de destino a la que se debe enviar el mensaje DHCPv6. By default is ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **destination_address** Dirección de destino

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se estableció correctamente la interfaz

- NX_PTR_ERROR (0x07) Entrada de puntero no válida

- NX_DHCPV6_PARAM_ERROR (0xE93) Error de parámetro

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_client _create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_create_client_duid"></a>nx_dhcpv6_create_client_duid

Crear un objeto DUID de cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a>Descripción

Este servicio crea el DUID de cliente con los parámetros de entrada. Si no se proporciona la entrada de hora y el tipo de DUID indica el nivel de vínculo con el tiempo, esta función proporcionará una hora que incluye un factor aleatorio para la unicidad. No se admiten los tipos de DUID asignados por el proveedor (Enterprise).

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **duid_type** Tipo de DUID (hardware, empresa, etc.)

- **hardware_type** Hardware de red, por ejemplo, IEEE 802

- **hora** de Valor usado en la creación de un identificador único

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Cliente exitoso DUID creado

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida

- NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) Tipo de DUID desconocido o no admitido 

- NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) Tipo de hardware de DUID desconocido o no admitido

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_create_client_ia
- nx_dhcpv6_create_client_iana
- nx_dhcpv6_create_server_duid

## <a name="nx_dhcpv6_create_client_ia"></a>nx_dhcpv6_create_client_ia

Agregar una Asociación de identidad al cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a>Descripción

Este servicio es idéntico al servicio *nx_dhcpv6_add_client_ia*. Agrega una Asociación de identidad de cliente rellenando el registro de cliente con los parámetros proporcionados. Para solicitar la vigencia máxima preferida y válida, establezca estos parámetros en Infinity. Para agregar más de un IA a un cliente DHCPv6, establezca el NX_DHCPV6_MAX_IA_ADDRESS en un valor mayor que el valor predeterminado de 1.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **ipv6_address** Puntero al bloque de direcciones IP de NetX Duo

- **preferred_lifetime** Período de tiempo antes de que la dirección IP esté en desuso

- **valid_lifetime** Período de tiempo antes de que la dirección IP expire

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) IA del cliente añadido correctamente

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Dirección IA duplicada 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA supera el número máximo de clientes de IA que puede almacenar

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) No válido (por ejemplo, NULL) dirección IA en IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida


### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_add_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_create_client_iana"></a>nx_dhcpv6_create_client_iana

Crear una Asociación de identidad (no temporal) para el cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a>Descripción

Este servicio crea una Asociación de identidad no temporal del cliente (IANA) a partir de los parámetros proporcionados. Para establecer las horas T1 y T2 en máximo (infinito) en las solicitudes de cliente DHCPv6, establezca estos parámetros en NX_DHCPV6_INFINITE_LEASE. 

> [!NOTE]
> Un cliente solo tiene una IANA.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **IA_ident** Identificador único de la Asociación de identidad

- **T1** Cuando el cliente debe iniciar la renovación de la dirección IPv6

- **T2** Cuando el cliente debe iniciar el reenlace de la dirección IPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Creó correctamente la IANA

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_add_client_ia

## <a name="nx_dhcpv6_add_client_ia"></a>nx_dhcpv6_add_client_ia 

Agregar una Asociación de identidad al cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a>Descripción

Este servicio agrega una Asociación de identidad de cliente rellenando el registro de cliente con los parámetros proporcionados. Para solicitar la vigencia máxima preferida y válida, establezca estos parámetros en Infinity. Para agregar más de un IA a un cliente DHCPv6, establezca el NX_DHCPV6_MAX_IA_ADDRESS en un valor mayor que el valor predeterminado de 1.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **ipv6_address** Puntero al bloque de direcciones IP de NetX Duo

- **preferred_lifetime** Período de tiempo antes de que la dirección IP esté en desuso

- **valid_lifetime** Período de tiempo antes de que la dirección IP expire 

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) IA del cliente añadido correctamente

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Dirección IA duplicada 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0XEAE) IA supera el número máximo de clientes de IA que puede almacenar

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) No válido (por ejemplo, NULL) dirección IA en IA

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida

 
### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_get_client_duid_time_id"></a>nx_dhcpv6_get_client_duid_time_id

Recupera el id. de hora del DUID del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a>Descripción

Este servicio recupera el campo de id. de hora del DUID de cliente. Si la aplicación debe llamar primero a *nx_dhcpv6_create_client_duid*, para rellenar el DUID de cliente en la instancia de cliente DHCPv6 o tendrá un valor NULL para este campo. La intención es que la aplicación guarde estos datos y presente el mismo DUID de cliente al servidor, incluido el campo de tiempo, entre reinicios.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **time_id** Puntero al campo de hora de DUID del cliente

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Datos de concesión de IP recuperados correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_time_lease_data
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_ip_address"></a>nx_dhcpv6_get_IP_address

Recupera la dirección IPv6 global del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a>Descripción

Este servicio recupera la dirección IPv6 global del cliente. Si el cliente no tiene una dirección válida, se devuelve un estado de error. Si un cliente tiene más de una dirección IPv6 global, se devuelve la dirección IPv6 principal.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **ip_address** Puntero a dirección IPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Dirección IPv6 asignada correctamente

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) La dirección IPv6 no es válida

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_lease_time_data"></a>nx_dhcpv6_get_lease_time_data

Recupera los datos de tiempo de concesión de dirección IA del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a>Descripción

Este servicio recupera los datos de hora de la dirección IA global del cliente. Si el estado de la dirección IA del cliente no es válido, los datos de hora se establecen en cero y se devuelve un estado de finalización correcto. Si un cliente tiene más de una dirección IPv6 global, se devuelven los datos de la dirección IA principal.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **T1** Hora de renovación del puntero a la dirección IA

- **T2** Puntero al tiempo de reenlace de la dirección IA

- **preferred_lifetime** Puntero a la hora en que la dirección IA está en desuso

- **valid_lifetime** Puntero a la hora de expiración de la dirección IA

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Datos de concesión de IP recuperados correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_iana_lease_time

## <a name="nx_dhcpv6_get_iana-lease_time"></a>nx_dhcpv6_get_iana lease_time

Recuperar los datos de tiempo de concesión de IANA del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a>Descripción

Este servicio recupera los datos globales de tiempo de concesión IA-NA del cliente (T1 y T2). Si ninguna de las direcciones IA-NA del cliente tiene un estado de dirección válido, los datos de hora se establecen en cero y se devuelve un estado de finalización correcto. Si un cliente tiene más de una dirección IPv6 global, se devuelven los datos de la dirección IA principal.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **T1** Puntero a hora de inicio de la renovación de la concesión

- **T2** Puntero a hora de inicio de la renovación de la concesión

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Datos de concesión de IANA recuperados correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a>nx_dhcpv6_get_valid_ip_address_count

Recuperación de un recuento de direcciones IA válidas del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a>Descripción

Este servicio recupera el recuento de las direcciones IPv6 válidas del cliente. Una dirección IPv6 válida está enlazada (asignada) al cliente y registrada con la instancia de IP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **address_count** Puntero al recuento de direcciones que se va a devolver

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Datos de concesión de IANA recuperados correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a>nx_dhcpv6_get_valid_ip_address_lease_time

Recuperación de los datos del IA del cliente por índice de dirección

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a>Descripción

Este servicio recupera la dirección IA del cliente y los datos de concesión por índice de dirección. Si se proporciona un índice no válido o la dirección IPv6 en dicho índice no es válida, el servicio devuelve un estado de error NX_DHCPV6_IA_ADDRESS_NOT_VALID.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **address_index** Índice en la tabla IA de DHCPv6

- **ip_address** Puntero a la dirección IPv6 para recuperar

- **preferred_lifetime** Puntero a la hora en que la dirección IA está en desuso

- **valid_lifetime** Puntero a la hora de expiración de la dirección IA

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Datos IANA recuperados correctamente

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0XEAD) Un índice no válido o una dirección IPv6 válida en el índice proporcionado 

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_iana_lease_time
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_dns_server_address"></a>nx_dhcpv6_get_DNS_server_address

Recupera la dirección del servidor DNS 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a>Descripción

Este servicio recupera los datos de la dirección IPv6 del servidor DNS en el índice especificado en la lista de clientes. Si la lista no contiene una dirección de servidor en el índice, se devuelve un error. Es posible que el índice no supere el tamaño de la lista de servidores DNS especificado por la opción configurable por el usuario NX_DHCPV6_NUM_DNS_SERVERS.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **Índice** El índice en la lista de servidores DNS

- **server_address** Puntero al búfer de direcciones del servidor

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) La dirección se recuperó correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_other_option_data"></a>nx_dhcpv6_get_other_option_data

Recupera datos de opciones DHCPv6 

### <a name="prototype"></a>Prototipo

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a>Descripción

Este servicio recupera datos de opciones DHCPv6 de un mensaje DHCPv6 para el código de opción especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- código de **opción** código de opción para el que se recuperarán los datos

- **búfer** Puntero al búfer en el que se van a copiar datos 

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Datos de opción recuperados correctamente

- **NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Código de opción desconocido o no compatible

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_DHCPV6_PARAM_ERROR (0xE93) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_time_accrued"></a>nx_dhcpv6_get_time_accrued

Recupera el tiempo acumulado en la concesión de la dirección IP del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a>Descripción

Este servicio recupera el tiempo acumulado en la concesión de la dirección IPv6 del cliente. La función comprueba todas las direcciones IPv6 asignadas al cliente para la primera dirección válida. Si no se encuentran direcciones válidas, se devuelve un valor de cero para el tiempo acumulado.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **time_accrued** Puntero al tiempo acumulado en la concesión de IP

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Tiempo acumulado recuperado correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_set_time_accrued

## <a name="nx_dhcpv6_get_time_server_address"></a>nx_dhcpv6_get_time_server_address

Recupera la dirección del servidor de tiempo 

### <a name="prototype"></a>Prototipo

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a>Descripción

Este servicio recupera los datos de la dirección IPv6 del servidor de tiempo en el índice especificado en la lista de clientes. Si la lista no contiene una dirección de servidor en el índice, se devuelve un error. El índice no puede exceder el tamaño de la lista de servidores de tiempo especificado por la opción configurable por el usuario NX_DHCPV6_NUM_TIME_SERVERS.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **Índice** Índice en la lista de servidores de tiempo

- **server_address** Puntero al búfer de direcciones del servidor

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) La dirección se recuperó correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_DNS_server_address

## <a name="nx_dhcpv6_reinitialize"></a>nx_dhcpv6_reinitialize

Quitar la dirección IP del cliente de la tabla IP

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio reinicializa el cliente para reiniciar la máquina de estados DHCPv6 y volver a ejecutar el protocolo DHCPv6. Esto no es necesario si el cliente no ha iniciado previamente el equipo de estado DHPCv6 o si se le ha asignado cualquier dirección IPv6. Se desactivan las direcciones guardadas en el cliente DHCPv6 y registradas con la instancia de IP.

> [!NOTE]
> La aplicación todavía debe iniciar el cliente DHCPv6 mediante el *servicio de nx_dhcpv6_start* y comenzar la solicitud de asignación de direcciones IPv6 llamando a *nx_dhcpv6_request_solicit*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) La dirección se quitó correctamente

- **NX_DHCPV6_ALREADY_STARTED** (0xE91) El cliente DHCPv6 ya se está ejecutando

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_stop
- nx_dhcpv6_start

## <a name="nx_dhcpv6_request_confirm"></a>nx_dhcpv6_request_confirm

Procesar el estado de CONFIRMACIÓN del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía una solicitud de confirmación. Si se recibe una respuesta del servidor, el cliente DHCPv6 actualiza los parámetros de concesión con los datos recibidos.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de CONFIRMACIÓN enviado y procesado correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release
- nx_dhcpv6_request_solicit


## <a name="nx_dhcpv6_request_inform_request"></a>nx_dhcpv6_request_inform_request

Procesar el estado de SOLICITUD DE INFORME del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía un mensaje de SOLICITUD DE INFORME. Si se recibe una respuesta, cuando se recibe una, se procesa la respuesta para determinar si es válida y el servidor ha concedido la solicitud. La instancia del cliente se actualiza entonces con la información del servidor según sea necesario.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se creó y procesó correctamente el mensaje de SOLICITUD DE INFORME

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_request_confirm

## <a name="nx_dhcpv6_request_option_dns_server"></a>nx_dhcpv6_request_option_DNS_server

Agregar servidor DNS a solicitud de opción DHCPv6

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio agrega la opción para solicitar información del servidor DNS a la solicitud de la opción DHCPv6. Si la respuesta del servidor incluye datos del servidor DNS, el cliente almacenará el servidor DNS si tiene espacio para hacerlo. El número de servidores DNS que puede almacenar el cliente viene determinado por la opción configurable NX_DHCPV6_NUM_DNS_SERVERS cuyo valor predeterminado es 2.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se incluye la opción de servidor DNS

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_fqdn"></a>nx_dhcpv6_request_option_FQDN

Agregar la opción nombre de dominio completo a la lista de solicitudes de opción

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a>Descripción

Este servicio agrega la opción para agregar el nombre de dominio completo del cliente a la solicitud de la opción DHCPv6. Hay tres opciones para la opción FQDN:

- NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Actualice la asignación de direcciones FQDN a IPv6 para FQDN y direcciones utilizadas por el cliente.

- NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Actualice la asignación de direcciones FQDN a IPv6 para FQDN y direcciones que usa el cliente al servidor.

- NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Solicite al servidor que no realice actualizaciones de DNS en nombre del Cliente.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **domain_name** Cadena que contiene el nombre de dominio

- **operación** Tipo de opción de FQDN que se va a aplicar (vea la lista anterior)

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se incluye la opción de FQDN

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_domain_name"></a>nx_dhcpv6_request_option_domain_name

Agregar opción de nombre de dominio a solicitud de opción DHCPv6

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio agrega la opción de nombre de dominio a la opción solicitud en los mensajes de solicitud de cliente. Si la respuesta del servidor incluye datos de nombre de dominio, el cliente almacenará la información del nombre de dominio si el tamaño del nombre de dominio se encuentra dentro del tamaño del búfer para contener el nombre de dominio. Este tamaño de búfer es una opción configurable (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) con un valor predeterminado de 30 bytes.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Conjunto de opciones de nombre de dominio

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_time_server"></a>nx_dhcpv6_request_option_time_server

Establecer datos del servidor de tiempo como solicitud opcional

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio agrega la opción de información de servidor de tiempo a la opción solicitud de mensajes de solicitud de cliente. Si la respuesta del servidor incluye datos del servidor Tim, el cliente almacenará el servidor de tiempo si tiene espacio para hacerlo. El número de servidores de tiempo que el cliente puede almacenar viene determinado por la opción configurable

NX_DHCPV6_NUM_TIME _SERVERS cuyo valor predeterminado es 1.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Opción de servidor de tiempo agregada

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_timezone"></a>nx_dhcpv6_request_option_timezone

Establecer datos de la zona horaria como solicitud opcional

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio agrega la opción para solicitar información de zona horaria a la solicitud de opción de cliente. Si la respuesta del servidor incluye datos de zona horaria, el cliente almacenará la información de zona horaria si el tamaño de la zona horaria está dentro del tamaño del búfer para contener la zona horaria. Este tamaño de búfer es una opción configurable (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) con un valor predeterminado de 10 bytes.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Opción de zona horaria agregada

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server

## <a name="nx_dhcpv6_request_release"></a>nx_dhcpv6_request_release

Enviar un mensaje de VERSIÓN DHCPv6

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía un mensaje de VERSIÓN en la red del cliente. Si el mensaje se envía correctamente, se devuelve un estado correcto. Una finalización correcta no significa que el cliente reciba una respuesta o que se le haya concedido todavía una dirección IPv6. La tarea de subproceso de cliente DHCPv6 espera una respuesta de un servidor DHCPv6. Si se recibe uno, comprueba que la respuesta es válida y almacena los datos en el registro de cliente.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de VERSIÓN enviado correctamente

- **NX_DHCPV6_NOT_STARTED** (0xE92) Tarea de cliente DHCPv6 no iniciada

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Dirección no enlazada al cliente

- **NX_INVALID_INTERFACE** (0x4C) No se encontró en la tabla de direcciones IP

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_solicit

## <a name="nx_dhcpv6_request_solicit"></a>nx_dhcpv6_request_solicit

Enviar un mensaje de PETICIÓN

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía un mensaje de PETICIÓN a la red. Si el mensaje se envía correctamente, se devuelve un estado correcto. Una finalización correcta no significa que el cliente reciba una respuesta o que se le haya concedido todavía una dirección IPv6. La tarea de subproceso de cliente DHCPv6 espera una respuesta (un mensaje de ANUNCIO) de un servidor DHCPv6. Si se recibe uno, comprueba que la respuesta es válida, almacena los datos en el registro de cliente y promueve el cliente al estado de la SOLICITUD.

> [!NOTE] 
> Si se establece la opción de confirmación rápida, el cliente DHCPv6 irá directamente al estado enlazado si recibe un mensaje de ANUNCIO de servidor válido. Para obtener más información, consulte la descripción del servicio para obtener *nx_dhcpv6_request_solicit_rapid*.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de PETICIÓN enviado correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a>nx_dhcpv6_request_solicit_rapid

Enviar un mensaje de PETICIÓN con la opción de confirmación rápida

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía un mensaje de PETICIÓN en la red con la opción de confirmación rápida establecida. Si el mensaje se envía correctamente, se devuelve un estado correcto. Una finalización correcta no significa que el cliente reciba una respuesta o que se le haya concedido todavía una dirección IPv6. La tarea de subproceso de cliente DHCPv6 espera una respuesta (un mensaje de ANUNCIO) de un servidor DHCPv6. Si se recibe uno, comprueba que la respuesta es válida, almacena los datos en el registro de cliente y promueve el cliente al estado ENLAZADO.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Mensaje de PETICIÓN enviado correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_request_solicit
- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release

## <a name="nx_dhcpv6_resume"></a>nx_dhcpv6_resume

Reanudar tarea de cliente DHCPv6 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio reanuda la tarea de subproceso de cliente DHCPv6. Se procesará el estado del cliente DHCPv6 actual (por ejemplo, enlazado, petición)

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El cliente se reanudó correctamente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_start
- nx_dhcpv6_stop
- nx_dhcpv6_suspend

## <a name="nx_dhcpv6_set_-time_accrued"></a>nx_dhcpv6_set_ time_accrued

Establece el tiempo acumulado en la concesión de la dirección IP del cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a>Descripción

Este servicio establece el tiempo acumulado en la dirección IP global del cliente desde que fue asignada por el servidor. Solo debe usarse si un cliente está enlazado actualmente a una dirección IPv6 asignada.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

- **time_accrued** Tiempo acumulado en la concesión de IP

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Tiempo acumulado correctamente establecido

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_start"></a>nx_dhcpv6_start

Iniciar la tarea de cliente DHCPv6 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia la tarea de cliente DHCPv6 y prepara el cliente para ejecutar el protocolo DHCPv6. Comprueba que la instancia de cliente tiene suficiente información (por ejemplo, un DUID de cliente), crea y enlaza el socket UDP para enviar y recibir mensajes DHCPv6 y activa temporizadores para realizar un seguimiento del tiempo de sesión y cuando expira la concesión de IPv6 actual.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se inició correctamente el cliente

- **NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Faltan las opciones necesarias del cliente

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_stop
- nx_dhcpv6_reinitialize

## <a name="nx_dhcpv6_stop"></a>nx_dhcpv6_stop

Detener la tarea de cliente DHCPv6 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene la tarea de cliente DHCPv6 y borra los recuentos de retransmisión, el intervalo máximo de retransmisión, desactiva los temporizadores de expiración de la sesión y la concesión y desenlaza el puerto de socket de cliente DHCPv6. Para reiniciar el cliente, primero debe detenerse y, opcionalmente, reinicializar el cliente antes de iniciar otra sesión con cualquier servidor DHCPv6. Para más detalles, consulte la sección Ejemplo pequeño.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El cliente se detuvo correctamente

- **NX_DHCPV6_NOT_STARTED** (0xE92) Subproceso de cliente no iniciado

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso


### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_reinitialize
- nx_dhcpv6_start

## <a name="nx_dhcpv6_suspend"></a>nx_dhcpv6_suspend

Suspender la tarea de cliente DHCPv6 

### <a name="prototype"></a>Prototipo

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Descripción

Este servicio suspende la tarea de cliente DHCPv6 y cualquier solicitud que se encontraba en medio del procesamiento. Los temporizadores se desactivan y el estado del cliente se establece en no en ejecución.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcpv6_ptr** Puntero a la instancia de cliente DHCPv6

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El cliente se suspendió correctamente

- **NX_DHCPV6_NOT_STARTED** (0XE92) El cliente no se está ejecutando, por lo que no se puede suspender

- NX_PTR_ERROR: (0x16) Entrada de puntero no válida

- NX_CALLER_ERROR (0x11) Debe llamarse desde el subproceso

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a>Consulte también

- nx_dhcpv6_resume
- nx_dhcpv6_start
- nx_dhcpv6_reinitialize
- nx_dhcpv6_stop
