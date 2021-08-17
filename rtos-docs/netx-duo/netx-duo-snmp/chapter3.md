---
title: 'Capítulo 3: Descripción de los servicios del agente SNMP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios del agente SNMP de NetX Duo (se enumeran a continuación) por orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b24776c2eb25a53195ea4eb452497b23b933e4ab3f9f0a379ea64d8469c1c971
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790129"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a>Capítulo 3: Descripción de los servicios del agente SNMP de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios del agente SNMP de Azure RTOS NetX Duo (se enumeran a continuación) por orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- [nx_snmp_agent_auth_trap_key_use](#nx_snmp_agent_auth_trap_key_use)
   - *Especificar la clave de autenticación (solo SNMP v3) para los mensajes de captura*
- [nx_snmp_agent_authenticate_key_use](#nx_snmp_agent_authenticate_key_use)
   - *Especificar la clave de autenticación (solo SNMP v3) para los mensajes de respuesta*
- [nx_snmp_agent_community_get](#nx_snmp_agent_community_get)
   - *Recuperar el nombre de la comunidad*
- [nx_snmp_agent_context_engine_set](#nx_snmp_agent_context_engine_set)
   - *Establecer el motor de contexto (solo SNMP v3)*
- [nx_snmp_agent_context_name_set](#nx_snmp_agent_context_name_set)
   - *Establecer el nombre del contexto (solo SNMP v3)*
- [nx_snmp_agent_create](#nx_snmp_agent_create)
   - *Crear agente SNMP*
- [nx_snmp_agent_current_version_get](#nx_snmp_agent_current_version_get)
   - *Obtener la versión de SNMP del paquete recibido*
- [nx_snmp_agent_request_get_type_test](#nx_snmp_agent_request_get_type_test)
   - *Indicar si la última solicitud SNMP es de tipo GET o SET*
- [nx_snmp_agent_private_string_test](#nx_snmp_agent_private_string_test)
   - *Determinar si la cadena coincide con la cadena privada del agente*
- [nx_snmp_agent_public_string_test](#nx_snmp_agent_public_string_test)
   - *Determinar si la cadena coincide con la cadena pública del agente*
- [nx_snmp_agent_set_interface](#nx_snmp_agent_set_interface)
   - *Establecer la interfaz de red para la mensajería SNMP*
- [nx_snmp_agent_private_string_set](#nx_snmp_agent_private_string_set)
   - *Establecer la cadena de comunidad privada del agente SNMP*
- [nx_snmp_agent_public_string_set](#nx_snmp_agent_public_string_set)
   - *Establecer la cadena de comunidad pública del agente SNMP*
- [nx_snmp_agent_version_set](#nx_snmp_agent_version_set)
   - *Establecer el estado del agente SNMP para todas las versiones de SNMP*
- [nx_snmp_agent_delete](#nx_snmp_agent_delete)
   - *Eliminar el agente SNMP*
- [nx_snmp_agent_md5_key_create](#nx_snmp_agent_md5_key_create)
   - *Crear clave MD5 (solo SNMP v3)*
- [nx_snmp_agent_md5_key_create_extended](#nx_snmp_agent_md5_key_create_extended)
   - *Crear clave MD5 (solo SNMP v3)*
- [nx_snmp_agent_priv_trap_key_use](#nx_snmp_agent_priv_trap_key_use)
   - *Especificar la clave de cifrado (solo SNMP v3) para los mensajes de captura*
- [nx_snmp_agent_privacy_key_use](#nx_snmp_agent_privacy_key_use)
   - *Especificar la clave de cifrado (solo SNMP v3) para los mensajes de respuesta*
- [nx_snmp_agent_sha_key_create](#nx_snmp_agent_sha_key_create)
   - *Crear clave SHA (solo SNMP v3)*
- [nx_snmp_agent_sha_key_create_extended](#nx_snmp_agent_sha_key_create_extended)
   - *Crear clave SHA (solo SNMP v3)*
- [nx_snmp_agent_start](#nx_snmp_agent_start)
   - *Iniciar el agente SNMP*
- [nx_snmp_agent_stop](#nx_snmp_agent_stop)
   - *Detener el agente SNMP*
- [nx_snmp_agent_trap_send](#nx_snmp_agent_trap_send)
   - *Enviar captura de SNMP v1 (solo IPv4)*
- [nx_snmp_agent_trapv2_send](#nx_snmp_agent_trapv2_send)
   - *Enviar captura de SNMP v2 (solo IPv4)*
- [nx_snmp_agent_trapv2_oid_send](#nx_snmp_agent_trapv2_oid_send)
   - *Enviar captura de SNMP v2 (solo IPv4) especificando el OID*
- [nx_snmp_agent_trapv3_send](#nx_snmp_agent_trapv3_send)
   - *Enviar captura de SNMP v3 (solo IPv4)*
- [nx_snmp_agent_trapv3_oid_send](#nx_snmp_agent_trapv3_oid_send)
   - *Enviar captura de SNMP v2 (solo IPv4) especificando el OID*
- [nxd_snmp_agent_trap_send](#nxd_snmp_agent_trap_send)
   - *Enviar captura de SNMP v1 (IPv4 e IPv6)*
- [nxd_snmp_agent_trapv2_send](#nxd_snmp_agent_trapv2_send)
   - *Enviar captura de SNMP v2 (IPv4 e IPv6)*
- [nxd_snmp_agent_trapv2_oid_send](#nxd_snmp_agent_trapv2_oid_send)
   - *Enviar captura de SNMP v2 (IPv4 e IPv6) especificando el OID*
- [nxd_snmp_agent_trapv3_send](#nxd_snmp_agent_trapv3_send)
   - *Enviar captura de SNMP v3 (IPv4 e IPv6)*
- [nxd_snmp_agent_trapv3_oid_send](#nxd_snmp_agent_trapv3_oid_send)
   - *Enviar captura de SNMP v2 (IPv4 e IPv6) especificando el OID*
- [nx_snmp_agent_v3_context_boots_set](#nx_snmp_agent_v3_context_boots_set)
   - *Establecer el número de reinicios*
- [nx_snmp_object_compare](#nx_snmp_object_compare)
   - *Comparar dos objetos*
- [nx_snmp_object_compare_extended](#nx_snmp_object_compare_extended)
   - *Comparar dos objetos*
- [nx_snmp_object_copy](#nx_snmp_object_copy)
   - *Copia de un objeto*
- [nx_snmp_object_copy_extended](#nx_snmp_object_copy_extended)
   - *Copia de un objeto*
- [nx_snmp_object_counter_get](#nx_snmp_object_counter_get)
   - *Obtener objeto de contador*
- [nx_snmp_object_counter_set](#nx_snmp_object_counter_set)
   - *Establecer objeto de contador*
- [nx_snmp_object_counter64_get](#nx_snmp_object_counter64_get)
   - *Obtener objeto de contador de 64 bits*
- [nx_snmp_object_counter64_set](#nx_snmp_object_counter64_set)
   - *Establecer objeto de contador de 64 bits*
- [nx_snmp_object_end_of_mib](#nx_snmp_object_end_of_mib)
   - *Establecer el valor de final de MIB*
- [nx_snmp_object_gauge_get](#nx_snmp_object_gauge_get)
   - *Obtener objeto de medidor*
- [nx_snmp_object_gauge_set](#nx_snmp_object_gauge_set)
   - *Establecer objeto de medidor*
- [nx_snmp_object_id_get](#nx_snmp_object_id_get)
   - *Obtener el identificador de objeto*
- [nx_snmp_object_id_set](#nx_snmp_object_id_set)
   - *Establecer el identificador de objeto*
- [nx_snmp_object_integer_get](#nx_snmp_object_integer_get)
   - *Obtener objeto de número entero*
- [nx_snmp_object_integer_set](#nx_snmp_object_integer_set)
   - *Establecer objeto de número entero*
- [nx_snmp_object_ip_address_get](#nx_snmp_object_ip_address_get)
   - *Obtener objeto de dirección IP (solo IPv4)*
- [nx_snmp_object_ip_address_set](#nx_snmp_object_ip_address_set)
   - *Establecer objeto de dirección IP (solo IPv4)*
- [nx_snmp_object_ipv6_address_get](#nx_snmp_object_ipv6_address_get)
   - *Obtener objeto de dirección IP (solo IPv6)*
- [nx_snmp_object_ipv6_address_set](#nx_snmp_object_ipv6_address_set)
   - *Establecer objeto de dirección IP (solo IPv6)*
- [nx_snmp_object_no_instance](#nx_snmp_object_no_instance)
   - *Establecer el valor "no hay instancia"*
- [nx_snmp_object_not_found](#nx_snmp_object_not_found)
   - *Establecer el valor "no encontrado"*
- [nx_snmp_object_octet_string_get](#nx_snmp_object_octet_string_get)
   - *Obtener objeto de cadena de octetos*
- [nx_snmp_object_octet_string_set](#nx_snmp_object_octet_string_set)
   - *Establecer objeto de cadena de octetos*
- [nx_snmp_object_string_get](#nx_snmp_object_string_get)
   - *Obtener objeto de cadena ASCII*
- [nx_snmp_object_string_set](#nx_snmp_object_string_set)
   - *Establecer objeto de cadena ASCII*
- [nx_snmp_object_timetics_get](#nx_snmp_object_timetics_get)
   - *Obtener objeto timetics*
- [nx_snmp_object_timetics_set](#nx_snmp_object_timetics_set)
   - *Establecer objeto timetics*

## <a name="nx_snmp_agent_auth_trap_key_use"></a>nx_snmp_agent_auth_trap_key_use
Especificar la clave de autenticación para los mensajes de captura

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Descripción

Este servicio especifica la clave que se va a usar para establecer los parámetros de autenticación en el encabezado de seguridad SNMP v3 en los mensajes de captura. Al proporcionar un valor NX_NULL para la clave, se deshabilita la autenticación.

> [!NOTE]
> La clave se debe crear previamente. Consulte nx_snmp_agent_md5_key_create o nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **key** Puntero a una clave MD5 o SHA creada previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Conjunto de claves de autenticación correcto.
- **NX_NOT_ENABLED** (0x14) La seguridad de SNMP está deshabilitada. 
- **NX_PTR_ERROR** (0x07) Puntero del agente SNMP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a>nx_snmp_agent_authenticate_key_use
Especificar la clave de autenticación para los mensajes de respuesta

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Descripción

Este servicio especifica la clave que se va a usar para los parámetros de autenticación en el parámetro de seguridad de SNMP v3 para todas las solicitudes realizadas una vez establecido. Al proporcionar un valor NX_NULL para la clave, se deshabilita la autenticación.

> [!NOTE]
> La clave se debe crear previamente. Consulte nx_snmp_agent_md5_key_create o nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **key** Puntero a una clave MD5 o SHA creada previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Conjunto de claves de SNMP correcto.
- **NX_NOT_ENABLED** (0x14) La seguridad de SNMP está deshabilitada.
- **NX_PTR_ERROR** (0x07) Puntero del agente SNMP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a>nx_snmp_agent_community_get
Recuperar el nombre de la comunidad

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el nombre de la comunidad de la solicitud SNMP más reciente recibida por el agente SNMP.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **community_string_ptr** Puntero a un puntero de cadena para devolver la cadena de la comunidad del agente SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Obtención correcta de la comunidad de SNMP.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a>nx_snmp_agent_request_get_type_test
Indicar si la última solicitud SNMP es de tipo GET o SET

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a>Descripción

Este servicio indica si la solicitud más reciente del administrador de SNMP es de tipo GET (GET, GETNEXT o GETBULK) o de tipo SET. Está pensada para su uso con la devolución de llamada de nombre de usuario, donde la aplicación SNMP v1 o SNMP v2 querrá comparar la cadena de la comunidad recibida con la cadena pública del agente SNMP si la solicitud es un tipo GET o con la cadena privada del agente SNMP si la solicitud es de tipo SET.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **is_get_type** Puntero al estado del tipo de solicitud:  
NX_TRUE si es de tipo GET  
NX_FALSE si es de tipo SET

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Tipo devuelto correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a>nx_snmp_agent_context_engine_set
Establecer el motor de contexto (solo SNMP v3)

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a>Descripción

Este servicio establece el motor de contexto del agente SNMP. Solo es aplicable para el procesamiento de SNMP v3. Se debe llamar a este servicio antes de crear claves de seguridad si la aplicación usa autenticación y cifrado, ya que el identificador del motor de contexto se usa en el proceso de creación de claves. En caso contrario, SNMP de NetX Duo proporciona un identificador de motor de contexto predeterminado en la parte superior del archivo *nxd_snmp.c:*

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **context_engine** Puntero a la cadena del motor de contexto.
- **context_engine_size** Tamaño de la cadena del motor de contexto. Tenga en cuenta que el número máximo de bytes en un motor de contexto se define mediante NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se ha establecido correctamente el motor de contexto de SNMP.
- **NX_NOT_ENABLED** (0x14) SNMP v3 no está habilitado.
- **NX_SNMP_ERROR** (0x100) Error de tamaño del motor de contexto.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a>nx_snmp_agent_context_name_set
Establecer el nombre del contexto (solo SNMP v3)

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a>Descripción

Este servicio establece el nombre del contexto del agente SNMP. Solo es aplicable para el procesamiento de SNMP v3. Si no se le llama, el agente SNMP de NetX Duo dejará el nombre de contexto en blanco.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **context_name** Puntero a la cadena del nombre de contexto.
- **context_name_size** Tamaño de la cadena del nombre de contexto. Tenga en cuenta que el número máximo de bytes en un nombre de contexto se define mediante NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se ha establecido correctamente el nombre de contexto de SNMP.
- **NX_SNMP_ERROR** (0x100) Error de tamaño del nombre de contexto.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a>nx_snmp_agent_create
Crear agente SNMP

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a>Descripción

Este servicio crea un agente SNMP en la instancia de IP especificada.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **snmp_agent_name** Puntero a la cadena del nombre del agente SNMP.
- **ip_ptr** Puntero a la instancia de IP.
- **stack_ptr** Puntero al puntero de la pila de subprocesos del agente SNMP.
- **stack_size** Tamaño de la pila en bytes.
- **pool_ptr** Puntero el grupo de paquetes predeterminado para este agente SNMP.
- **snmp_agent_username_process** Puntero de función a la rutina de control de nombre de usuario de la aplicación.
- **snmp_agent_get_process** Puntero de función a la rutina de control de la solicitud GET de la aplicación.
- **snmp_agent_getnext_process** Puntero de función a la rutina de control de la solicitud GETNEXT de la aplicación.
- **snmp_agent_set_process** Puntero de función a la rutina de control de la solicitud SET de la aplicación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Creación correcta del agente SNMP.
- **NX_SNMP_ERROR** (0x100) Error en la creación del agente SNMP.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a>nx_snmp_agent_current_version_get
Obtener la versión del paquete SNMP

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a>Descripción

Este servicio recupera la versión de SNMP analizada a partir del paquete SNMP más reciente recibido.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **version** Puntero a la versión de SNMP analizada desde el paquete SNMP recibido.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Obtención correcta de la versión de SNMP.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a>nx_snmp_agent_private_string_test
Comprobar si la cadena privada coincide con la cadena privada del agente

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a>Descripción

Este servicio compara la cadena de la comunidad de entrada terminada en NULL con la cadena privada del agente SNMP e indica si coinciden.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **community_string** Puntero a la cadena que se va a comparar.
- **is_private** Puntero al resultado de la comparación.  
NX_TRUE: la cadena coincide  
NX_FALSE: la cadena no coincide

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Comparación correcta.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a>nx_snmp_agent_public_string_test
Comprobar que la cadena pública recibida coincida con la cadena pública del agente

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a>Descripción

Este servicio compara una cadena de la comunidad de entrada terminada en NULL con la cadena pública del agente SNMP e indica si coinciden.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **community_string** Puntero a la cadena que se va a comparar.
- **is_public** Puntero al resultado de la comparación.  
NX_TRUE: la cadena coincide  
NX_FALSE: la cadena no coincide

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Comparación correcta.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a>nx_snmp_agent_version_set
Establecer el estado del agente SNMP para todas las versiones de SNMP

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a>Descripción

Este servicio establece el estado (habilitado o deshabilitado) para cada una de las versiones de SNMP, V1, V2 y V3, en el agente SNMP. Tenga en cuenta que las opciones configurables por el usuario, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 y NX_SNMP_DISABLE_V3, invalidarán esta configuración en tiempo de ejecución. De manera predeterminada, el agente SNMP está habilitado para las tres versiones.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **enabled_v1** Establece el estado habilitado para SNMP V1 en on y off.
- **enabled_v2** Establece el estado habilitado para SNMP V2 en on y off.
- **enabled_v3** Establece el estado habilitado para SNMP V3 en on y off.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Establecimiento correcto de la versión de SNMP.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a>nx_snmp_agent_private_string_set
Establecer la cadena privada del agente SNMP

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a>Descripción

Este servicio establece la cadena de la comunidad privada del agente SNMP con la cadena de entrada terminada en NULL. El valor predeterminado es NULL (no se establece una cadena privada), de modo que el agente SNMP no aceptará ningún paquete SNMP recibido con una cadena de la comunidad "privada" para el acceso de lectura y escritura. La cadena de entrada debe ser menor o igual que el valor configurable por el usuario NX_SNMP_MAX_USER_NAME-1 (para dejar espacio para la terminación con NULL).

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **community_string** Puntero a la cadena privada que se va a asignar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se ha establecido correctamente la cadena privada.
- **NX_SNMP_ERROR_TOOBIG** (0x01) Tamaño de la cadena demasiado grande. 
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a>nx_snmp_agent_public_string_set
Establecer la cadena pública del agente SNMP

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a>Descripción

Este servicio establece la cadena de la comunidad pública del agente SNMP con la cadena de entrada terminada en NULL. La cadena de la comunidad debe ser menor o igual que el valor configurable por el usuario NX_SNMP_MAX_USER_NAME-1 (para dejar espacio para la terminación con NULL).

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **community_string** Puntero a la cadena pública que se va a asignar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se ha establecido correctamente la cadena pública.
- **NX_SNMP_ERROR_TOOBIG** (0x01) Tamaño de la cadena demasiado grande.
- **NX_PTR_ERROR** (0x07) Entrada de puntero no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a>nx_snmp_agent_delete
Eliminar el agente SNMP

### <a name="prototype"></a>Prototipo

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Descripción

Este servicio elimina un agente SNMP creado previamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta del agente SNMP.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a>nx_snmp_agent_set_interface
Establecer la interfaz de red del agente SNMP

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a>Descripción

Este servicio establece la interfaz de red SNMP para el agente SNMP tal y como se especifica en el índice de la interfaz de entrada. Esto solo es útil para las aplicaciones de host SNMP con NetX Duo 5.6 o superior que admiten varias interfaces de red. Si no se especifica en el host, el valor predeterminado es cero para la interfaz principal.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **If_index** Índice que especifica la interfaz SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Se ha establecido correctamente la interfaz SNMP.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a>nx_snmp_agent_md5_key_create
Crear clave MD5 (solo SNMP v3)

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a>Descripción

Este servicio crea una clave MD5 que se puede usar para la autenticación y el cifrado.

Este servicio está en desuso. Se recomienda a los desarrolladores que migren a *nx_snmp_agent_md5_key_create_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **password** Puntero a la cadena de contraseña.
- **destination_key** Puntero a la estructura de datos de la clave SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Clave creada correctamente.
- **NX_NOT_ENABLED** (0x14) La seguridad no está habilitada.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a>nx_snmp_agent_md5_key_create_extended
Crear clave MD5 (solo SNMP v3)

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a>Descripción

Este servicio crea una clave MD5 que se puede usar para la autenticación y el cifrado.

Este servicio reemplaza a *nx_snmp_agent_md5_key_create().* Esta versión requiere que el autor de la llamada proporcione la longitud de la contraseña.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **password** Puntero a la cadena de contraseña.
- **password_length** Longitud de la cadena de contraseña.
- **destination_key** Puntero a la estructura de datos de la clave SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Clave creada correctamente.
- **NX_NOT_ENABLED** (0x14) La seguridad no está habilitada.
- **NX_SNMP_FAILED** (0x102) Error de SNMP.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a>nx_snmp_agent_priv_trap_key_use
Especificar la clave de cifrado para los mensajes de captura

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a>Descripción

Este servicio especifica que se utilizará una clave de privacidad creada previamente para el cifrado y descifrado de los mensajes de captura de SNMP v3.

> [!NOTE]
> *Se debe crear previamente una clave de autenticación. La privacidad de SNMP v3 (cifrado) requiere autenticación. Consulte nx_snmp_agent_auth_trap_key_use para más información.*

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **key** Puntero a la clave creada previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se ha establecido correctamente la clave de privacidad.
- **NX_NOT_ENABLED** (0x14) La seguridad no está habilitada.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a>nx_snmp_agent_privacy_key_use
Especificar la clave de cifrado para los mensajes de respuesta

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Descripción

Este servicio especifica que se utilizará la clave creada previamente para el cifrado y descifrado de los mensajes de respuesta de SNMP v3.

> [!NOTE]
> *Se debe haber especificado previamente una clave de autenticación. El cifrado de SNMP v3 también requiere la creación de una clave de autenticación. Consulte nx_snmp_agent_authentiation_key_use para más información.*

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **key** Puntero a la clave creada previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Se ha establecido correctamente la clave de privacidad.
- **NX_NOT_ENABLED** (0x14) La seguridad no está habilitada.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a>nx_snmp_agent_sha_key_create
Crear clave SHA (solo SNMP v3)

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a>Descripción

Este servicio crea una clave SHA que se puede usar para la autenticación y el cifrado.

Este servicio está en desuso. Se recomienda a los desarrolladores que migren a *nx_snmp_agent_sha_key_create_extended()* .

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **password** Puntero a la cadena de contraseña.
- **destination_key** Puntero a la estructura de datos de la clave SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Clave creada correctamente.
- **NX_SNMP_ERROR** (0x100) Error en la creación de la clave.
- **NX_PTR_ERROR** (0x07) Puntero de clave o agente SNMP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a>nx_snmp_agent_sha_key_create_extended
Crear clave SHA (solo SNMP v3)

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a>Descripción

Este servicio crea una clave SHA que se puede usar para la autenticación y el cifrado.

Este servicio reemplaza a *nx_snmp_agent_sha_key_create().* Esta versión requiere que el autor de la llamada proporcione la longitud de la contraseña.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **password** Puntero a la cadena de contraseña.
- **password_length** Longitud de la cadena de contraseña.
- **destination_key** Puntero a la estructura de datos de la clave SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Clave creada correctamente.
- **NX_SNMP_ERROR** (0x100) Error en la creación de la clave.
- **NX_SNMP_FAILED** (0x102) Error en la creación de la clave.
- **NX_PTR_ERROR** (0x07) Puntero de clave o agente SNMP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a>nx_snmp_agent_start
Iniciar el agente SNMP 

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Descripción

Este servicio enlaza el socket UDP al puerto 161 de SNMP e inicia la tarea del subproceso del agente SNMP.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Inicio correcto del agente SNMP.
- **NX_SNMP_ERROR** (0x100) Error en el inicio del agente SNMP.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a>nx_snmp_agent_stop
Detener el agente SNMP 

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Descripción

Este servicio detiene la tarea del subproceso del agente SNMP y anula el enlace del socket UDP al puerto de SNMP.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Detención correcta del agente SNMP.
- **NX_PTR_ERROR** (0x07) Puntero del agente SNMP no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a>nx_snmp_agent_trap_send
Enviar captura de SNMP v1 *(solo IPv4)*

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP al administrador de SNMP en la dirección IPv4 especificada. El método preferido para enviar una captura de SNMP en NetX Duo es usar el servicio *nxd_snmp_agent_trap_send*. *nx_snmp_agent_trap_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Dirección IPv4 del administrador de SNMP.
- **enterprise** Cadena del identificador de objeto de empresa (sysObectID).
- **trap_type** Tipo de captura solicitada, como se indica a continuación:  
   - NX_SNMP_TRAP_COLDSTART (0)  
   - NX_SNMP_TRAP_WARMSTART (1)  
   - NX_SNMP_TRAP_LINKDOWN (2)  
   - NX_SNMP_TRAP_LINKUP (3)  
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)  
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  

- **trap_code** Código de la captura específica.
- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_NOT_ENABLED** (0x14) SNMP v1 no está habilitado.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a>nxd_snmp_agent_trap_send
*Enviar captura de SNMP v1 (IPv4 e IPv6)*

### <a name="prototype"></a>Prototipo

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP al administrador de SNMP en la dirección IP especificada. El método equivalente para enviar una captura de SNMP en NetX es el servicio *nxd_snmp_agent_trap_send*.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Dirección IPv4 o IPv6 del administrador de SNMP.
- **enterprise** Cadena del identificador de objeto de empresa (sysObectID).
- **trap_type** Tipo de captura solicitada, como se indica a continuación:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

- **trap_code** Código de la captura específica.
- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_NOT_ENABLED** (0x14) SNMP v1 no está habilitado.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a>nx_snmp_agent_trapv2_send
Enviar captura de SNMP v2 (solo IPv4)

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP v2 al administrador de SNMP en la dirección IPv4 especificada. El método preferido para enviar una captura de SNMP en NetX Duo es usar el servicio *nxd_snmp_agent_trapv2_send*. *nx_snmp_agent_trapv2_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Dirección IPv4 del administrador de SNMP.
- **community** Nombre de comunidad (nombre de usuario).
- **trap_type**  
   Tipo de captura solicitada. Los eventos estándar son:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   Para datos propietarios:  
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido en *nxd_snmp.h*)
   
- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_NOT_ENABLED** (0x14) SNMP v2 no está habilitado.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a>nx_snmp_agent_trapv2_oid_send
Enviar captura de SNMP v2 especificando directamente el OID 

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP v2 al administrador de SNMP en la dirección IP especificada (solo IPv4) y permite que el autor de la llamada especifique directamente el OID. El método preferido para enviar una captura de SNMP especificando el OID en NetX Duo es usar el servicio *nxd_snmp_agent_trapv2_oid_send*. *nx_snmp_agent_trapv2_oid_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Dirección IP del administrador de SNMP.
- **community** Nombre de comunidad (nombre de usuario).
- **OID** Puntero al búfer que contiene el OID.
- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_PTR_ERROR** (0x16) Puntero de parámetro o agente SNMP no válido.
- **NX_IP_ADDRESS_ERROR** (0x21) Dirección IP de destino no válida.
- **NX_OPTION_ERROR** (0x0a) Parámetro no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a>nxd_snmp_agent_trapv2_send
Enviar captura de SNMP v2 (IPv4 e IPv6)

### <a name="prototype"></a>Prototipo

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP V2 al administrador de SNMP en la dirección IP especificada.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Dirección IP (IPv4 o IPv6) del administrador de SNMP.
- **community** Nombre de comunidad (nombre de usuario).
- **trap_type**  
   Tipo de captura solicitada. Los eventos estándar son:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   Para datos propietarios:

   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido en *nxd_snmp.h*)

- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_NOT_ENABLED** (0x14) SNMP v2 no está habilitado.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Versión de IP no admitida.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a>nxd_snmp_agent_trapv2_oid_send
Enviar captura de SNMP v2 especificando directamente el OID 

### <a name="prototype"></a>Prototipo

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP v2 al administrador de SNMP en la dirección IP especificada (IPv4 e IPv6) y permite que el autor de la llamada especifique directamente el OID.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Dirección IP del administrador de SNMP (IPv4 e IPv6).
- **community** Nombre de comunidad (nombre de usuario).
- **OID** Puntero al búfer que contiene el OID.
- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_PTR_ERROR** (0x16) Puntero de parámetro o agente SNMP no válido.
- **NX_IP_ADDRESS_ERROR** (0x21) Dirección IP de destino no válida.
- **NX_OPTION_ERROR** (0x0a) Parámetro no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a>nx_snmp_agent_trapv3_send
Enviar captura de SNMP v3 (solo IPv4)

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP v3 al administrador de SNMP en la dirección IPv4 especificada. El método preferido para enviar una captura de SNMP en NetX Duo es usar el servicio *nxd_snmp_agent_trapv3_send*. *nx_snmp_agent_trapv3_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Dirección IPv4 del administrador de SNMP.
- **username** Nombre de comunidad (nombre de usuario).
- **trap_type**  
   Tipo de captura solicitada. Los eventos estándar son:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   Para datos propietarios:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido en *nxd_snmp.h*)

- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_NOT_ENABLED** (0x14) SNMP v3 no está habilitado.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a>nx_snmp_agent_trapv3_oid_send
Enviar captura de SNMP v3 especificando directamente el OID 

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP v3 al administrador de SNMP en la dirección IP especificada (solo IPv4) y permite que el autor de la llamada especifique directamente el OID. El método preferido para enviar una captura de SNMP especificando el OID en NetX Duo es usar el servicio *nxd_snmp_agent_trapv3_oid_send*. *nx_snmp_agent_trapv3_oid_send* está incluido en NetX Duo para admitir aplicaciones de agente SNMP de NetX existentes.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Dirección IP del administrador de SNMP.
- **username** Nombre de comunidad (nombre de usuario).
- **OID** Puntero al búfer que contiene el OID.
- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_PTR_ERROR** (0x16) Puntero de parámetro o agente SNMP no válido.
- **NX_IP_ADDRESS_ERROR** (0x21) Dirección IP de destino no válida.
- **NX_OPTION_ERROR** (0x0a) Parámetro no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a>nxd_snmp_agent_trapv3_send
Enviar captura de SNMP v3 (IPv4 e IPv6)

### <a name="prototype"></a>Prototipo

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP al administrador de SNMP en la dirección IP especificada. Esta captura es básicamente la misma que la captura de SNMP v2, excepto que el formato del mensaje de captura está incluido en el PDU de SNMP v3.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Dirección IP (IPv4 o IPv6) del administrador de SNMP.
- **username** Nombre de comunidad (nombre de usuario).
- **trap_type**  
   Tipo de captura solicitada. Los eventos estándar son:
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  
   Para datos propietarios:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (definido en *nxd_snmp.h*)

- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_NOT_ENABLED** (0x14) SNMP v3 no está habilitado.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Versión de IP no admitida.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a>nxd_snmp_agent_trapv3_oid_send
Enviar captura de SNMP v3 especificando directamente el OID 

### <a name="prototype"></a>Prototipo

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Descripción

Este servicio envía una captura de SNMP v3 al administrador de SNMP en la dirección IP especificada (IPv4 e IPv6) y permite que el autor de la llamada especifique directamente el OID.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **ip_address** Puntero a la dirección IP del administrador de SNMP.
- **username** Nombre de usuario (nombre de comunidad).
- **OID** Puntero al búfer que contiene el OID.
- **elapsed_time** Tiempo de actividad del sistema (sysUpTime).
- **object_list_ptr** Matriz de objetos y sus valores asociados que se incluirán en la captura de SNMP. La lista termina con NX_NULL.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío de captura de SNMP correcto.
- **NX_SNMP_ERROR** (0x100) Error al enviar la captura de SNMP.
- **NX_PTR_ERROR** (0x16) Puntero de parámetro o agente SNMP no válido.
- **NX_IP_ADDRESS_ERROR** (0x21) Dirección IP de destino no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a>nx_snmp_agent_v3_context_boots_set
Establecer el número de reinicios (si está habilitado SNMP v3)

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a>Descripción

Este servicio establece el número de reinicios registrados por el agente SNMP. Este servicio solo está disponible si está habilitado SNMP v3 para el agente SNMP, porque el número de reinicios solo se usa en el protocolo SNMP v3.

### <a name="input-parameters"></a>Parámetros de entrada

- **agent_ptr** Puntero al bloque de control del agente SNMP.
- **boots** Valor en el que se va a establecer el número de inicios del agente SNMP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Número de inicios establecido correctamente.
- **NX_SNMP_ERROR** (0x100) Error al establecer el número de inicios.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a>nx_snmp_object_compare
Comparar dos objetos 

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a>Descripción

Este servicio compara el identificador de objeto proporcionado con el identificador de objeto de referencia. Ambos identificadores de objeto tendrán la notación SMI ASCII; por ejemplo, ambos objetos deben comenzar por la cadena ASCII "1.3.6".

Este servicio está en desuso. Se recomienda a los desarrolladores que migren a *nx_snmp_object_compare_extended().*

### <a name="input-parameters"></a>Parámetros de entrada

- **object** Puntero al identificador de objeto.
- **reference_object** Puntero al identificador del objeto de referencia.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto coincide con el objeto de referencia.
- **NX_SNMP_NEXT_ENTRY** (0x101) El objeto es menor que el objeto de referencia.
- **NX_SNMP_ERROR** (0x100) El objeto es mayor que el objeto de referencia.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a>nx_snmp_object_compare_extended
Comparar dos objetos 

### <a name="prototype"></a>Prototipo

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a>Descripción

Este servicio compara el identificador de objeto proporcionado con el identificador de objeto de referencia. Ambos identificadores de objeto tendrán la notación SMI ASCII; por ejemplo, ambos objetos deben comenzar por la cadena ASCII "1.3.6".

Este servicio reemplaza a *nx_snmp_object_compare().* Esta versión requiere que los autores de llamada proporcionen la información de longitud.

### <a name="input-parameters"></a>Parámetros de entrada

- **request_object** Puntero al identificador del objeto de la solicitud.
- **request_object_length** Longitud del identificador del objeto de la solicitud.
- **reference_object** Puntero al identificador del objeto de referencia.
- **reference_object_length** Longitud del identificador del objeto de referencia.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto coincide con el objeto de referencia.
- **NX_SNMP_NEXT_ENTRY** (0x101) El objeto es menor que el objeto de referencia.
- **NX_SNMP_ERROR** (0x100) El objeto es mayor que el objeto de referencia.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a>nx_snmp_object_copy
Copia de un objeto 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a>Descripción

Este servicio copia el objeto de origen con la notación SIM ASCII en el objeto de destino.

Este servicio está en desuso. Se recomienda a los desarrolladores que migren a *nx_snmp_object_copy_extended().*

### <a name="input-parameters"></a>Parámetros de entrada

- **source_object_name** Puntero al identificador del objeto de origen.
- **destination_object_name** Puntero al identificador de objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **size** Número de bytes copiados en el nombre de destino. Si hay un error, se devuelve cero.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a>nx_snmp_object_copy_extended
Copia de un objeto 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a>Descripción

Este servicio copia el objeto de origen con la notación SIM ASCII en el objeto de destino.

Este servicio reemplaza a *nx_snmp_object_copy().* Esta versión requiere que los autores de llamada proporcionen la información de longitud.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_object_name** Puntero al identificador del objeto de origen.
- **source_object_name_length** Longitud del identificador del objeto de origen.
- **destination_object_name_buffer** Puntero al búfer del objeto de destino.
- **destination_object_name_buffer_size** Tamaño del búfer del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **size** Número de bytes copiados en el nombre de destino. Si hay un error, se devuelve cero.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a>nx_snmp_object_counter_get
Obtener objeto de contador 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Descripción

Este servicio recupera el objeto de contador en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen del contador.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de contador se ha recuperado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a>nx_snmp_object_counter_set
Establecer objeto de contador 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio establece el contador en la dirección especificada por el puntero de destino con el valor del contador en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero al destino del contador.
- **object_data** Puntero a la estructura del objeto de origen del contador.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de contador se ha establecido correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a>nx_snmp_object_counter64_get
Obtener objeto de contador de 64 bits 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio recupera el objeto de contador de 64 bits en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen del contador.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de contador se ha recuperado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a>nx_snmp_object_counter64_set
Establecer objeto de contador de 64 bits 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Descripción

Este servicio establece el contador de 64 bits en la dirección especificada por el puntero de destino con el valor del contador en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero al destino del contador.
- **object_data** Puntero a la estructura del objeto de origen del contador.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de contador se ha establecido correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a>nx_snmp_object_end_of_mib
Establecer el valor de final de MIB 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio crea un objeto que señala el final de MIB y suele llamarse desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **not_used_ptr** Puntero no utilizado: debe ser NX_NULL.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de final de MIB se ha creado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a>nx_snmp_object_gauge_get
Obtener objeto de medidor 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio recupera el objeto de medidor en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen del medidor.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de medidor se ha recuperado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a>nx_snmp_object_gauge_set
Establecer objeto de medidor 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio establece el medidor en la dirección especificada por el puntero de destino con el valor del medidor en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero al destino del medidor.
- **object_data** Puntero a la estructura del objeto de origen del medidor.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de medidor se ha establecido correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a>nx_snmp_object_id_get
Obtener el identificador de objeto 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio recupera el identificador de objeto (en notación SIM ASCII) en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen del identificador de objeto.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El identificador de objeto se ha recuperado correctamente.
- **NX_SNMP_ERROR** (0x100) Longitud no válida del objeto.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a>nx_snmp_object_id_set
Establecer el identificador de objeto 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio establece el identificador de objeto (en notación SIM ASCII) en la dirección especificada por el puntero de destino con el identificador de objeto en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero al destino del identificador de objeto.
- **object_data** Puntero a la estructura del objeto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El identificador de objeto se ha establecido correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a>nx_snmp_object_integer_get
Obtener objeto de número entero 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio recupera el objeto de número entero en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen del número entero.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de número entero se ha recuperado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a>nx_snmp_object_integer_set
Establecer objeto de número entero 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio establece el número entero en la dirección especificada por el puntero de destino con el valor del número entero en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero al destino del número entero.
- **object_data** Puntero a la estructura del objeto de origen del número entero.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de número entero se ha establecido correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a>nx_snmp_object_ip_address_get
Obtener objeto de dirección IP (solo IPv4)

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio recupera el objeto de dirección IP en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen de la dirección IPv4.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de dirección IP se ha recuperado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a>nx_snmp_object_ipv6_address_get
Obtener objeto de dirección IP (solo IPv6)

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a>Descripción

Este servicio recupera el objeto de dirección IPv6 en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX.
Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen de la dirección IPv6.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de dirección IP se ha recuperado correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Código de objeto SNMP de entrada incorrecto.
- **NX_NOT_ENABLED** (0x14) IPv6 no está habilitado.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a>nx_snmp_object_ip_address_set
Establecer objeto de dirección IPv4 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección IPv4 en la dirección especificada por el puntero de destino con el valor de la dirección IP en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero a la dirección IP que se va a establecer.
- **object_data** Puntero a la estructura del objeto de dirección IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de dirección IP se ha establecido correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a>nx_snmp_object_ipv6_address_set
Establecer objeto de dirección IPv6 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección IPv6 en la dirección especificada por el puntero de destino con el valor de la dirección IP en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero a la dirección IP que se va a establecer.
- **object_data** Puntero a la estructura del objeto de dirección IP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) La dirección IPv6 se ha establecido correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_NOT_ENABLED** (0x14) IPv6 no está habilitado.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a>nx_snmp_object_no_instance
Establecer objeto "no hay instancia" 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio crea un objeto que señala que no había ninguna instancia del objeto especificado y normalmente se le llama desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **not_used_ptr** Puntero no utilizado: debe ser NX_NULL.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto "no hay instancia" se ha creado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a>nx_snmp_object_not_found
Establecer objeto "no encontrado" 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio crea un objeto que señala que no se ha encontrado el objeto y suele llamarse desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **not_used_ptr** Puntero no utilizado: debe ser NX_NULL.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto "no encontrado" se ha creado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a>nx_snmp_object_octet_string_get
Obtener objeto de cadena de octetos 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a>Descripción

Este servicio recupera la cadena de octetos en la dirección especificada por el puntero de origen y la coloca en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen de la cadena de octetos.
- **object_data** Puntero a la estructura del objeto de destino.
- **length** Número de bytes de la cadena de octetos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de cadena de octetos se ha recuperado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a>nx_snmp_object_octet_string_set
Establecer objeto de cadena de octetos 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio establece la cadena de octetos en la dirección especificada por el puntero de destino con el valor de la cadena de octetos en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero al destino de la cadena de octetos.
- **object_data** Puntero a la estructura de objetos del origen de la cadena de octetos.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de cadena de octetos se ha establecido correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a>nx_snmp_object_string_get
Obtener objeto de cadena ASCII 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio recupera la cadena ASCII en la dirección especificada por el puntero de origen y la coloca en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen de la cadena ASCII.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de cadena ASCII se ha recuperado correctamente.
- **NX_SNMP_ERROR** (0x100) La cadena es demasiado grande.  
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a>nx_snmp_object_string_set
Establecer objeto de cadena ASCII 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio establece la cadena ASCII en la dirección especificada por el puntero de destino con el valor de la cadena ASCII en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero al destino de la cadena ASCII.
- **object_data** Puntero a la estructura de objetos del origen de la cadena ASCII.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto de cadena ASCII se ha establecido correctamente.
- **NX_SNMP_ERROR** (0x100) La cadena es demasiado grande.
- **NX_SNMP_ERROR_BADVALUE** (0x03) Carácter no válido en la cadena.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a>nx_snmp_object_timetics_get
Obtener objeto timetics 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio recupera el objeto timetics en la dirección especificada por el puntero de origen y lo coloca en la estructura de datos del objeto de NetX. Normalmente, se llama a esta rutina desde la rutina de devolución de llamada GET o GETNEXT de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **source_ptr** Puntero al origen del objeto timetics.
- **object_data** Puntero a la estructura del objeto de destino.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto timetics se ha recuperado correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a>nx_snmp_object_timetics_set
Establecer objeto timetics 

### <a name="prototype"></a>Prototipo

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Descripción

Este servicio establece el objeto timetics en la dirección especificada por el puntero de destino con el valor del objeto timetics en la estructura de datos del objeto de NetX.
Normalmente, se llama a esta rutina desde la rutina de devolución de llamada SET de la aplicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **destination_ptr** Puntero al destino del objeto timetics.
- **object_data** Puntero a la estructura del objeto de origen del objeto timetics.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) El objeto timetics se ha establecido correctamente.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) Tipo de objeto no válido.
- **NX_PTR_ERROR** (0x07) Puntero de entrada no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```