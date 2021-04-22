---
title: 'Capítulo 3: Descripción de los servicios AutoIP de Azure RTOS NetX'
description: Este capítulo contiene una descripción de todos los servicios AutoIP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 22cc06c32cc9f1857b32d1d2b44a506ea1652cfd
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815285"
---
# <a name="chapter-3---description-of-azure-rtos-netx-autoip-services"></a>Capítulo 3: Descripción de los servicios AutoIP de Azure RTOS NetX

Este capítulo contiene una descripción de todos los servicios AutoIP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.

En la sección “Valores devueltos” de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de la API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_auto_ip_create**: *crea una instancia de AutoIP*.
- **nx_auto_ip_delete**: *elimina una instancia de AutoIP*.
- **nx_auto_ip_get_address**: *obtiene la dirección AutoIP actual*.
- **nx_auto_ip_set_interface**: *establece la interfaz IP que necesita una dirección AutoIP*.
- **nx_auto_ip_start**: *inicia el procesamiento de AutoIP*.
- **nx_auto_ip_stop**: *detiene el procesamiento de AutoIP*.

## <a name="nx_auto_ip_create"></a>nx_auto_ip_create

Crea una instancia de AutoIP

### <a name="prototype"></a>Prototipo

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
            NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
            UINT priority);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de AutoIP en la instancia de IP especificada.

- **auto_ip_ptr**: puntero al bloque de control de AutoIP.
- **name**: nombre de la instancia de AutoIP.
- **ip_ptr**: puntero a la instancia de IP.
- **stack_ptr**: puntero al área de la pila de subprocesos AutoIP.
- **stack_size**: tamaño del área de la pila de subprocesos AutoIP.
- **priority**: prioridad del subproceso AutoIP.

> [!NOTE]
> Si se utiliza DHCP, el subproceso DHCP debe tener una prioridad más alta que el subproceso de la instancia de IP y el subproceso AutoIP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Creación correcta de AutoIP.
- **NX_AUTO_IP_ERROR**: (0XA00) Error de creación de AutoIP.
- NX_PTR_ERROR: (0x16) AutoIP, ip_ptr o puntero de pila no válidos.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a>Consulte también

nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_delete"></a>nx_auto_ip_delete

Elimina una instancia de AutoIP

### <a name="prototype"></a>Prototipo

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de AutoIP creada anteriormente en la instancia de IP especificada.

### <a name="input-parameters"></a>Parámetros de entrada

- **auto_ip_ptr**: puntero al bloque de control de AutoIP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Eliminación correcta de AutoIP.
- **NX_AUTO_IP_ERROR**: (0XA00) Error de eliminación de AutoIP.
- NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a>Consulte también

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_get_address"></a>nx_auto_ip_get_address

Obtiene la dirección AutoIP actual

### <a name="prototype"></a>Prototipo

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a>Descripción

Este servicio recupera la dirección AutoIP configurada actualmente. Si no hay ninguna, se devuelve la dirección IP 0.0.0.0.

### <a name="input-parameters"></a>Parámetros de entrada

- **auto_ip_ptr**: puntero al bloque de control de AutoIP.
- **local_ip_address**: destino de la dirección IP devuelta.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha obtenido la dirección AutoIP correctamente.
- **NX_AUTO_IP_NO_LOCAL**: (0XA01) No hay ninguna dirección AutoIP válida.
- NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Inicialización, temporizadores, subprocesos, ISR

### <a name="example"></a>Ejemplo

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a>Consulte también

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_set_interface"></a>nx_auto_ip_set_interface

Establece la interfaz de red para AutoIP

### <a name="prototype"></a>Prototipo

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                                UINT interface_index);
```

### <a name="description"></a>Descripción

Este servicio establece el índice de la interfaz de red que AutoIP sondeará para buscar una dirección IP de red. El valor predeterminado es cero (la interfaz de red principal). Solo se aplica a los dispositivos de host múltiple.

### <a name="input-parameters"></a>Parámetros de entrada

- **auto_ip_ptr**: puntero al bloque de control de AutoIP.
- **interface_index**: interfaz para sondear si hay una dirección IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Interfaz de AutoIP configurada correctamente.
- **NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Interfaz de red no válida. 
- NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Inicialización, temporizadores, subprocesos, ISR

### <a name="example"></a>Ejemplo

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block auto_ip_0. */
```

### <a name="see-also"></a>Consulte también

nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop

## <a name="nx_auto_ip_start"></a>nx_auto_ip_start

Inicia el procesamiento de AutoIP

### <a name="prototype"></a>Prototipo

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a>Descripción

Este servicio inicia el protocolo AutoIP en una instancia de AutoIP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **auto_ip_ptr**: puntero al bloque de control de AutoIP.
- **starting_local_address**: dirección de inicio de AutoIP opcional. Un valor de IP_ADDRESS (0,0,0,0) especifica que se debe derivar una dirección AutoIP aleatoria. De lo contrario, si se especifica una dirección AutoIP válida, NetX AutoIP intenta asignar esa dirección.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Inicio correcto de AutoIP.
- **NX_AUTO_IP_ERROR**: (0XA00) Error de inicio de AutoIP.
- NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a>Consulte también

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop

## <a name="nx_auto_ip_stop"></a>nx_auto_ip_stop

Detiene el procesamiento de AutoIP

### <a name="prototype"></a>Prototipo

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene el protocolo AutoIP en una instancia de AutoIP creada e iniciada anteriormente. Este servicio se suele utilizar cuando se cambia la dirección IP mediante DHCP o manualmente por una dirección que no es AutoIP.

### <a name="input-parameters"></a>Parámetros de entrada

- **auto_ip_ptr**: puntero al bloque de control de AutoIP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Detención correcta de AutoIP.
- **NX_AUTO_IP_ERROR**: (0XA00) Error de detención de AutoIP.
- NX_PTR_ERROR: (0x16) Puntero de AutoIP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a>Consulte también

nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start