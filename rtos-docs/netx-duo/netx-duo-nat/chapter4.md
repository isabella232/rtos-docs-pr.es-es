---
title: 'Capítulo 4: Descripción de los servicios NAT'
description: Este capítulo contiene una descripción de todos los servicios de la API NAT de NetX Duo en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dbe2cb25607162b62b048251927bdc7671c5884d2a3b45b6b24bae539e08d24a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797302"
---
# <a name="chapter-4---description-of-nat-services"></a>Capítulo 4: Descripción de los servicios NAT

Este capítulo contiene una descripción de todos los servicios de la API NAT de NetX Duo (enumerados a continuación) en orden alfabético.

> [!NOTE]
> En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

## <a name="nx_nat_create"></a>nx_nat_create

Crear un servidor de NAT

### <a name="prototype"></a>Prototipo

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia del servidor de NAT.

### <a name="input-parameters"></a>Parámetros de entrada

- **nat_ptr** Puntero a la instancia de NAT que se va a crear.
- **ip_ptr** Puntero a la instancia de IP.
- **global_interface_index** Índice de la interfaz de red global.
- **dynamic_cache_memory** Área de memoria de puntero a la tabla NAT.
- **dynamic_cache_size** Tamaño del área de memoria para la tabla NAT.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Servidor NAT creado correctamente.
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.
- NX_NAT_PARAM_ERROR (0xD01) Entrada no de puntero no válida.
- NX_NAT_CACHE_ERROR (0xD02) Entrada de puntero de caché no válida.

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a>nx_nat_delete

Eliminar un servidor NAT

### <a name="prototype"></a>Prototipo

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina un servidor NAT creado previamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **nat_ptr** Puntero a la instancia de NAT que se va a eliminar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Servicio NAT eliminado correctamente
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a>nx_nat_enable

Habilitar la instancia de IP para NAT

### <a name="prototype"></a>Prototipo

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Descripción

Este servicio habilita la instancia de IP para NAT (por ejemplo, reenviar los paquetes recibidos al servidor NAT).

### <a name="input-parameters"></a>Parámetros de entrada

- **nat_ptr** Puntero a la instancia de NAT.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Servicio NAT habilitado correctamente.
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a>nx_nat_disable

Deshabilitar la instancia de IP para NAT

### <a name="prototype"></a>Prototipo

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita NAT en la instancia de IP.

### <a name="input-parameters"></a>Parámetros de entrada

- **nat_ptr** Puntero a la instancia de NAT.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Servicio NAT deshabilitado correctamente.
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a>nx_nat_cache_notify_set

Establecer una función de devolución de llamada de notificación completa de caché

### <a name="prototype"></a>Prototipo

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a>Descripción

Este servicio registra la devolución de llamada completa de la memoria caché con el puntero de función de entrada cache_full_notify_cb que apunta a una función de notificación completa de caché definida por el usuario.

### <a name="input-parameters"></a>Parámetros de entrada

- **nat_ptr** Puntero a la instancia de NAT.
- **cache_full_notify_cb** Puntero a la función de notificación completa de caché.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0X00) Establecimiento correcto de la función de notificación completa de caché.
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.
- NX_NAT_PARAM_ERROR (0xD01) Entrada no de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a>nx_nat_inbound_entry_create

Crear una entrada en la tabla de traducción de NAT

### <a name="prototype"></a>Prototipo

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a>Descripción

Este servicio crea una entrada como estática (entrada permanente, nunca expira) y la agrega a la tabla de traducciones de NAT. Estas entradas se crean normalmente para los servidores de host locales en los que se inicia una conexión desde un host de la red externa. El servidor de NAT comprueba que el puerto externo no se esté usando en la tabla de traducciones o que esté enlazado con un socket de NetX Duo anterior del mismo protocolo.

### <a name="input-parameters"></a>Parámetros de entrada

- **nat_ptr** Puntero a la instancia de NAT.
- **entry_ptr** Puntero a la entrada de traducción.
- **local_ip_address** Dirección IP del host local.
- **external_port** Puerto de destino en la red externa.
- **local_port** Puerto de origen (host local).
- **protocol** Protocolo de paquetes (por ejemplo, TCP).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Entrada creada correctamente.
- **NX_NAT_PORT_UNAVAILABLE** (0xD0D) Puerto externo no válido.
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.
- NX_NAT_PARAM_ERROR (0xD01) Entrada no de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a>nx_nat_inbound_entry_delete

Eliminar una entrada en la tabla de traducciones de NAT

### <a name="prototype"></a>Prototipo

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a>Descripción

Este servicio elimina la entrada especificada de la tabla de traducción.

### <a name="input-parameters"></a>Parámetros de entrada

- **nat_ptr** Puntero a la instancia de NAT.
- **delete_entry_ptr** Puntero a la entrada de traducciones de NAT.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Entrada eliminada correctamente.
- **NX_NAT_ENTRY_NOT_FOUND** (0xD04) Entrada no encontrada.
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada.
- NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Tipo de traducción no válido.

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
