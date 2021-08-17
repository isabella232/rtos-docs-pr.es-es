---
title: 'Capítulo 3: Descripción de los servicios de servidor DHCP de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios de servidor DHCP de Azure RTOS NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 702499184b12484fa5862ba83ff3fadb8fccea31089b6bf8b71daf267e8c84a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799530"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a>Capítulo 3: Descripción de los servicios de servidor DHCP de Azure RTOS NetX

Este capítulo contiene una descripción de todos los servicios de servidor DHCP de Azure RTO NetX.

En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_dhcp_server_create**: *Crea una instancia de servidor DHCP*.
- **nx_dhcp_set_interface_network_parameters**: *Establece las opciones de servidor DHCP para los parámetros de red críticos de la interfaz especificada*.
- **nx_dhcp_create_server_ip_address_list**: *Crea un grupo de direcciones IP disponibles para asignar a la interfaz de clientes DHCP*.
- **nx_dhcp_clear_client_record**: *Quita el registro del cliente de la base de datos del servidor*.
- **nx_dhcp_server_delete**: *Elimina una instancia de servidor DHCP*.
- **nx_dhcp_server_start**: *Inicia o reanuda el procesamiento del servidor DHCP*.
- **nx_dhcp_server_stop**: *Detiene el procesamiento del servidor DHCP*.

## <a name="nx_dhcp_server_create"></a>nx_dhcp_server_create

Crea una instancia de servidor DHCP

### <a name="prototype"></a>Prototipo

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de servidor DHCP con una instancia de IP creada anteriormente.

> [!IMPORTANT]
> La aplicación debe asegurarse de que el grupo de paquetes creado para el servicio de creación de IP tiene como mínimo una carga de 548 bytes, sin incluir los encabezados UDP, IP y Ethernet.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al bloque de control del servidor DHCP.  
- **ip_ptr**: puntero a la instancia de IP del servidor DHCP.
- **stack_ptr**: puntero a la ubicación de la pila del servidor DHCP.
- **stack_size**: tamaño de la pila del servidor DHCP.
- **input_address_list**: puntero a la lista de direcciones IP del servidor.
- **name_ptr**: puntero al nombre del servido DHCP.
- **packet_pool_ptr**: puntero al grupo de paquetes del servidor DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Error de carga de paquete demasiado pequeña.
- **NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) La lista de opciones está vacía.
- NX_DHCP_PARAMETER_ERROR: (0x92) Entrada no válida que no es puntero.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido del servicio.
- NX_PTR_ERROR: (0x16) Entrada no válida de puntero.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a>nx_dhcp_create_server_ip_address_list

Crea un grupo de direcciones IP.

### <a name="prototype"></a>Prototipo

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a>Descripción

Este servicio crea un grupo específico de interfaces de red de direcciones IP disponibles para el servidor DHCP especificado que se va a asignar. Las direcciones IP inicial y final deben coincidir con la interfaz de red especificada. El número real de direcciones IP agregadas puede ser menor que el total de direcciones si la lista de direcciones IP no es suficientemente grande (esto se establece en el parámetro *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* configurable por el usuario).

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al bloque de control del servidor DHCP.  
- **iface_index**: índice correspondiente a la interfaz de red.
- **start_ip_address**: primera dirección IP disponible.
- **end_ip_address**: última dirección IP disponible.
- **addresses_added**: número de direcciones IP agregadas a la lista.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) El índice no coincide con las direcciones.
- **NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Entrada de dirección no válida.
- NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Direcciones de inicio/fin ilógicas.
- NX_PTR_ERROR: (0x16) Entrada no válida de puntero.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a>nx_dhcp_clear_client_record

Quita el registro del cliente de la base de datos del servidor.

### <a name="prototype"></a>Prototipo

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Descripción

Este servicio borra el registro del cliente de la base de datos del servidor.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al bloque de control del servidor DHCP.  
- **dhcp_client_ptr**: puntero al cliente DHCP que se va a quitar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.
- NX_PTR_ERROR: (0x16) Entrada no válida de puntero.
- NX_CALLER_ERROR: (0x11) Autor de llamada del servicio sin subproceso.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

Establece parámetros de red para opciones de DHCP.

### <a name="prototype"></a>Prototipo

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a>Descripción

Este servicio establece los valores predeterminados para los parámetros críticos de red de la interfaz especificada. El servidor DHCP incluirá estas opciones en sus respuestas OFFER y ACK al cliente DHCP. Si los parámetros de interfaz del conjunto de hosts se ejecutan en un servidor DHCP, los parámetros se establecerán de forma predeterminada de la siguiente manera: el enrutador establecido en la puerta de enlace de la interfaz principal para el propio servidor DHCP, la dirección del servidor DNS para el propio servidor DHCP y la máscara de subred en la que se configura la interfaz del servidor DHCP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero al bloque de control del servidor DHCP.  
- **iface_index**: índice correspondiente a la interfaz de red.
- **subnet_mask**: máscara de subred para la red del cliente.
- **default_gateway_address**: dirección IP del enrutador del cliente.
- **dns_server_address**: servidor DNS para la red del cliente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor DHCP creado correctamente.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) El índice no coincide con las direcciones.
- **NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Parámetros de red no válidos.
- NX_PTR_ERROR: (0x16) Entrada no válida de puntero.

### <a name="allowed-from"></a>Permitido desde

Application

### <a name="example"></a>Ejemplo

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a>nx_dhcp_server_delete

Elimina una instancia de servidor DHCP.

### <a name="prototype"></a>Prototipo

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia del servidor DHCP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero a una instancia de servidor DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor DHCP eliminado correctamente.
- NX_PTR_ERROR: (0x16) Entrada no válida de puntero.
- NX_DHCP_PARAMETER_ERROR: (0x92) Entrada no válida que no es puntero.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido del servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

Inicia el procesamiento del servidor DHCP.

### <a name="prototype"></a>Prototipo

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia el procesamiento del servidor DHCP, que incluye la creación de un socket UDP del servidor, el enlace del puerto DHCP y la espera para recibir las solicitudes DHCP del cliente.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero a la instancia de DHCP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Servidor iniciado correctamente.  
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP ya se ha iniciado.
- NX_PTR_ERROR: (0x16) Entrada no válida de puntero.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido del servicio.
- NX_DHCP_PARAMETER_ERROR: (0x92) Entrada no válida que no es puntero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a>Consulte también

nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

Detiene el procesamiento del servidor DHCP.

### <a name="prototype"></a>Prototipo

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene el procesamiento del servidor DHCP, que incluye la recepción de solicitudes de cliente DHCP.

### <a name="input-parameters"></a>Parámetros de entrada

- **dhcp_ptr**: puntero a una instancia de servidor DHCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) DHCP detenido correctamente.
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP ya se ha iniciado.
- NX_PTR_ERROR: (0x16) Entrada no válida de puntero.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido del servicio.
- NX_DHCP_PARAMETER_ERROR: (0x92) Entrada no válida que no es puntero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
