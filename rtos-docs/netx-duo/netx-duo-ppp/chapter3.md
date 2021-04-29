---
title: 'Capítulo 3: Descripción de los servicios de Protocolo punto a punto (PPP) de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios de PPP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 90c24cad5e595087ba27178243f9dda0dab11029
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814602"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a>Capítulo 3: Descripción de los servicios de Protocolo punto a punto (PPP) de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios de PPP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_ppp_byte_receive**: *Recibir un byte de ISR en serie*
- **nx_ppp_chap_challenge**: *Generar un desafío CHAP*
- **nx_ppp_chap_enable**: *Habilitar la autenticación CHAP*
- **nx_ppp_create**: *Crear una instancia de PPP*
- **nx_ppp_delete**: *Eliminar una instancia de PPP*
- **nx_ppp_dns_address_get**: *Obtener la dirección IP del servidor DNS*
- **nx_ppp_dns_address_get**: *Establecer la dirección IP del servidor DNS*
- **nx_ppp_secondary_dns_address_get**: *Obtener la dirección IP del servidor DNS secundario*
- **nx_ppp_secondary_dns_address_set**: *Establecer la dirección IP del servidor DNS secundario*
- **nx_ppp_interface_index_get**: *Obtener el índice de la interfaz IP*
- **nx_ppp_ip_address_assign**: *Asignar direcciones IP para IPCP*
- **nx_ppp_link_down_notify**: *Notificar a la aplicación la inactividad del vínculo*
- **nx_ppp_link_down_notify**: *Notificar a la aplicación la recuperación de la actividad del vínculo*
- **nx_ppp_nak_authentication_notify**: *Notificar a la aplicación si se ha recibido un NAK de autenticación*
- **nx_ppp_pap_enable**: *Habilitar la autenticación PAP*
- **nx_ppp_ping_request**: *Enviar una solicitud de eco LCP*
- **nx_ppp_raw_string_send**: *Enviar una cadena que no sea de PPP*
- **nx_ppp_restart**: *Reiniciar el procesamiento de PPP*
- **nx_ppp_start**: *Iniciar el procesamiento de PPP*
- **nx_ppp_status_get**: *Obtener el estado actual de PPP*
- **nx_ppp_stop**: *Detener el procesamiento de PPP*
- **nx_ppp_packet_receive**: *Recibir un paquete de PPP*
- **nx_ppp_packet_send_set**: *Establecer la función de envío de paquetes DE PPP*

## <a name="nx_ppp_byte_receive"></a>nx_ppp_byte_receive

Recibir un byte de ISR en serie

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a>Descripción

Normalmente, se llama a este servicio desde la rutina de servicio de interrupción (ISR) del controlador serie de la aplicación para transferir un byte recibido a PPP. Cuando se le llama, esta rutina coloca el byte recibido en un búfer de bytes circular y emite una notificación al subproceso de PPP adecuado para su procesamiento.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **byte**: Byte recibido del dispositivo serie.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Recepción correcta de bytes de PPP.
- **NX_PPP_BUFFER_FULL**: (0xB1) El búfer de serie de PPP ya está lleno.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos, ISR

### <a name="example"></a>Ejemplo

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a>nx_ppp_chap_challenge

Generar un desafío CHAP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia un desafío CHAP después de que la conexión de PPP ya esté activa y en ejecución. Esto proporciona a la aplicación la posibilidad de comprobar la autenticidad de la conexión periódicamente. Si el desafío no se realiza correctamente, el vínculo de PPP se cierra.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Desafío de PPP iniciado correctamente.
- **NX_PPP_FAILURE**: (0xB0) Desafío de PPP no válido, CHAP se habilitó solo para la respuesta.
- **NX_NOT_IMPLEMENTED**: (0x80) La lógica de CHAP se deshabilitó a través de NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a>nx_ppp_chap_enable

Habilitar la autenticación CHAP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a>Descripción

Este servicio habilita el Protocolo de autenticación por desafío mutuo (CHAP) para la instancia de PPP especificada.

Si se especifican los punteros de función "***get_challenge_values** _" y "_ *_get_verification_values_**", esta instancia de PPP requiere CHAP. De lo contrario, CHAP solo responde a las solicitudes de desafío del homólogo.

Hay varios elementos de datos a los que se hace referencia a continuación en las funciones de devolución de llamada necesarias. Se espera que los elementos de datos *secret*, *name* y *system* sean cadenas terminadas en NULL con un tamaño máximo de NX_PPP_NAME_SIZE-1. Se espera que el elemento de datos *rand_value* sea una cadena terminada en NULL con un tamaño máximo de NX_PPP_VALUE_SIZE-1. El elemento de datos *id* es un tipo de carácter único sin signo.

>[!NOTE]
> Se debe llamar a esta función después de *nx_ppp_create* pero antes de nx_ip_create o *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **get_challenge_values**: Puntero a la función de aplicación para recuperar los valores usados para el desafío. Tenga en cuenta que los valores de *rand_value*, *id* y *secret* deben copiarse en los destinos proporcionados.
- **get_responder_values**: Puntero a la función de aplicación que recupera los valores utilizados para responder a un desafío. Tenga en cuenta que los valores de *system*, *name* y *secret* deben copiarse en los destinos proporcionados.
- **get_verification_values**: Puntero a la función de aplicación que recupera los valores utilizados para comprobar la respuesta del desafío. Tenga en cuenta que los valores de *system*,*name* y *secret* deben copiarse en los destinos proporcionados.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) CHAP de PPP habilitado correctamente.
- **NX_NOT_IMPLEMENTED**: (0x80) La lógica de CHAP se deshabilitó a través de NX_PPP_DISABLE_CHAP.
- NX_PTR_ERROR: (0x07) Puntero de PPP o puntero de función de devolución de llamada no válido. Tenga en cuenta que si se especifica *get_challenge_values*, también se debe proporcionar la función *get_verification_values*.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a>nx_ppp_create

Crear una instancia de PPP

### <a name="prototype"></a>Prototipo

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de PPP para la instancia de IP de NetX especificada. Se debe llamar a esta función antes de crear la instancia de IP de NetX.

>[!NOTE]
> Por lo general, es una buena idea crear el subproceso de IP de NetX con una prioridad más alta que la prioridad de los subprocesos de PPP. Consulte el servicio *nx_ip_create* para obtener más información sobre cómo especificar la prioridad del subproceso de IP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **nombre**: Nombre de esta instancia de PPP.
- **ip_ptr**: Puntero al bloque de control para la instancia de IP que todavía no se ha creado.
- **stack_memory_ptr**: Puntero al inicio del área de la pila del subproceso de PPP.
- **stack_size**: Tamaño en bytes de la pila del subproceso.
- **pool_ptr**: Puntero al grupo de paquetes predeterminado.
- **thread_priority**: Prioridad de los subprocesos de PPP internos (1-31).
- **ppp_invalid_packet_handler**: Puntero de función al controlador de la aplicación para todos los paquetes que no son de PPP. El PPP de NetX normalmente llama a esta rutina durante la inicialización. Aquí es donde la aplicación puede responder a los comandos del módem o, en el caso de Windows XP, la aplicación de PPP de NetX puede iniciar PPP respondiendo con "CLIENT SERVER” al "CLIENT" inicial enviado por Windows XP.
- **ppp_byte_send**: Puntero de función a la rutina de salida de bytes de serie de la aplicación.


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Instancia de PPP creada correctamente.
- NX_PTR_ERROR: (0x07) Puntero de función de salida de PPP, IP o bytes no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a>nx_ppp_delete

Eliminar una instancia de PPP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina la instancia de PPP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Instancia de PPP eliminada correctamente.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a>nx_ppp_dns_address_get

Obtener dirección IP del servidor DNS

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera la dirección IP de DNS proporcionada por el homólogo en el protocolo de enlace IPCP. Si el homólogo no proporcionó ninguna dirección IP, se devuelve una dirección IP de 0.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **dns_address_ptr**: Destino de la dirección del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) DNS obtenido correctamente.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) La instancia de PPP no ha completado la negociación con el homólogo.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a>nx_ppp_secondary_dns_address_get

Obtener la dirección IP del servidor DNS secundario

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera la dirección IP secundaria de DNS proporcionada por el homólogo en el protocolo de enlace IPCP. Si el homólogo no proporcionó ninguna dirección IP, se devuelve una dirección IP de 0.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **dns_address_ptr**: Destino de la dirección del servidor DNS secundario.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) DNS obtenido correctamente.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) La instancia de PPP no ha completado la negociación con el homólogo.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a>nx_ppp_dns_address_set

Establecer la dirección IP del servidor DNS principal

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección IP del servidor DNS. Si el homólogo envía una solicitud de opción de servidor DNS en el estado de IPCP, este host proporcionará la información.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **dns_address**: Dirección del servidor DNS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) DNS establecido correctamente.
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) La instancia de PPP no ha completado la negociación con el homólogo.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a>nx_ppp_secondary_dns_address_set

Establecer la dirección IP del servidor DNS secundario

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>Descripción

Este servicio establece la dirección IP del servidor DNS secundario. Si el homólogo envía una solicitud de opción de servidor DNS secundario en el estado de IPCP, este host proporcionará la información.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **dns_address**: dirección del servidor DNS secundario

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) DNS establecido correctamente. 
- **NX_PPP_NOT_ESTABLISHED**: (0XB5) La instancia de PPP no ha completado la negociación con el homólogo.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a>nx_ppp_interface_index_get

Obtener índice de la interfaz IP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a>Descripción

Este servicio recupera el índice de interfaz IP asociado a esta instancia de PPP. Esto solo resulta útil cuando la instancia de PPP no es la interfaz principal de una instancia de IP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **index_ptr**: Destino del índice de interfaz.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Índice de PPP obtenido correctamente.
- **NX_IN_PROGRESS**: (0X37) La instancia de PPP no ha completado la inicialización.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a>nx_ppp_ip_address_assign

Asignar direcciones IP para IPCP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a>Descripción

Este servicio configura las direcciones IP local y del homólogo para su uso en el Protocolo de control de protocolo de Internet (IPCP). Debe llamarse para la instancia de PPP que tiene direcciones IP válidas para sí misma y para el otro homólogo.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **local_ip_address**: Dirección IP local.
- **peer_ip_address**: Dirección IP del homólogo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Dirección de PPP asignada correctamente.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a>nx_ppp_link_down_notify

Notificar a la aplicación la inactividad del vínculo

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a>Descripción

Este servicio registra la devolución de llamada de notificación de inactividad del vínculo de la aplicación con la instancia de PPP especificada. Si no es NULL, se llama a la función de devolución de llamada de inactividad del vínculo de la aplicación cuando el vínculo deja de funcionar.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **link_down_callback**: Puntero de función de notificación de inactividad del vínculo de la aplicación. Si es NULL, se deshabilita la notificación de inactividad del vínculo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Devolución de llamada de notificación de vínculo inactivo registrada correctamente.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a>nx_ppp_link_up_notify

Notificar a la aplicación la actividad del vínculo

### <a name="prototype"></a>Prototipo

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a>Descripción

Este servicio registra la devolución de llamada de notificación de actividad del vínculo de la aplicación con la instancia de PPP especificada. Si no es NULL, se llama a la función de devolución de llamada de actividad del vínculo de la aplicación cuando el vínculo vuelve a funcionar.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **link_up_callback**: Puntero de función de notificación de actividad del vínculo de la aplicación. Si es NULL, se deshabilita la notificación de actividad del vínculo.**

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Devolución de llamada de notificación de vínculo activo registrada correctamente.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a>nx_ppp_nak_authentication_notify

Notificar a la aplicación si se ha recibido un NAK de autenticación

### <a name="prototype"></a>Prototipo

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a>Descripción

Este servicio registra la devolución de llamada de notificación del NAK de autenticación de la aplicación con la instancia de PPP especificada. Si no es NULL, se llama a esta función de devolución de llamada siempre que la instancia de PPP recibe un NAK durante la autenticación.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **nak_authentication_notify**: Puntero a la función a la que se llama cuando la instancia de PPP recibe un NAK de autenticación. Si es NULL, la notificación se deshabilita.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Devolución de llamada de notificación registrada correctamente.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a>nx_ppp_pap_enable

Habilitar la autenticación PAP

### <a name="prototype"></a>Prototipo

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a>Descripción

Este servicio habilita el Protocolo de autenticación de contraseña (PAP) para la instancia de PPP especificada. Si se especifica el puntero de función "***verify_login***", esta instancia de PPP requiere PAP. De lo contrario, PAP solo responde a los requisitos de PAP del homólogo que se especifican durante la negociación de LCP.

Hay varios elementos de datos a los que se hace referencia a continuación en las funciones de devolución de llamada necesarias. Se espera que el elemento de datos *name* sea una cadena terminada en NULL con un tamaño máximo de NX_PPP_NAME_SIZE-1. Se espera que el elemento de datos *password* sea una cadena terminada en NULL con un tamaño máximo de NX_PPP_PASSWORD_SIZE-1.

>[!NOTE]
> Se debe llamar a esta función después de *nx_ppp_create* pero antes de *nx_ip_create* o *nx_ip_interface_attach*.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **generate_login**: Puntero a la función de aplicación que genera un elemento *name* y *password* para la autenticación por parte del homólogo. Tenga en cuenta que los valores de *name* y *password* deben copiarse en los destinos proporcionados.
- **generate_login**: Puntero a la función de aplicación que verifica los elementos *name* y *password* proporcionados por el homólogo. Esta rutina debe comparar los elementos *name* y *password* proporcionados. Si esta rutina devuelve NX_SUCCESS, los elementos name y password son correctos y PPP puede continuar con el paso siguiente. De lo contrario, esta rutina devuelve NX_PPP_ERROR y PPP simplemente espera otro nombre y contraseña.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) PAP de PPP habilitado correctamente.
- **NX_NOT_IMPLEMENTED**: (0x80) La lógica de PAP se deshabilitó a través de NX_PPP_DISABLE_PAP.
- NX_PTR_ERROR: (0x07) Puntero de PPP o puntero de función de aplicación no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a>nx_ppp_ping_request

Enviar una solicitud de ping de LCP

### <a name="prototype"></a>Prototipo

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a>Descripción

Este servicio envía una solicitud de LCP y establece una marca que indica que el dispositivo PPP está esperando una respuesta de eco. La opción wait es principalmente para la llamada *nx_packet_allocate*. El servicio vuelve en cuanto se envía la solicitud. No espera una respuesta. 

Cuando se recibe una respuesta de eco coincidente, la tarea de subprocesos de PPP borrará la marca. El dispositivo de PPP debe haber completado la parte de LCP de la negociación de PPP.

Este servicio es útil para las configuraciones PPP en las que no es posible sondear el hardware para conocer el estado del vínculo.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **data**: Puntero a los datos que se van a enviar en la solicitud de eco.
- **data_size**: Tamaño de los datos que se van a enviar wait_option. Tiempo de espera para enviar el mensaje de eco de LCP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Solicitud de eco enviada correctamente.
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) Conexión de PPP no establecida.
- NX_PTR_ERROR: (0x07) Puntero de PPP o puntero de función de aplicación no válido.
- NX_CALLER_ERROR (0x11): Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos de aplicación

### <a name="example"></a>Ejemplo

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  sizeof("username ") - 1;

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a>nx_ppp_raw_string_send

Enviar una cadena de ASCII sin formato

### <a name="prototype"></a>Prototipo

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a>Descripción

Este servicio envía una cadena de ASCII que no es de PPP directamente a la interfaz de PPP. Normalmente se utiliza después de que PPP reciba un paquete que no es de PPP y que contenga información de control de módem.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **string_ptr**: Puntero a la cadena que se va a enviar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Cadena sin formato de PPP enviada correctamente.
- NX_PTR_ERROR: (0x07) Puntero PPP o puntero de cadena no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a>nx_ppp_restart

Reiniciar el procesamiento de PPP

### <a name="prototype"></a>Prototipo

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Descripción

Este servicio reinicia el procesamiento de PPP. Normalmente se le llama cuando es necesario restablecer el vínculo, ya sea desde una devolución de llamada de inactividad del vínculo o por un mensaje de módem que no es de PPP que indica que se perdió la comunicación.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Reinicio de PPP iniciado correctamente.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a>nx_ppp_start

Iniciar el procesamiento de PPP

### <a name="prototype"></a>Prototipo

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia el procesamiento de PPP. Normalmente se le llama después de llamar a nx_ppp_stop ().

>[!NOTE]
> PPP inicia automáticamente el procesamiento de PPP cuando el vínculo está habilitado.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Inicio de PPP iniciado correctamente. 
- **NX_PPP_ALREADY_STARTED**: (0XB9) PPP ya iniciado.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a>nx_ppp_status_get

Obtener el estado actual de PPP

### <a name="prototype"></a>Prototipo

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a>Descripción

Este servicio obtiene el estado actual de la instancia de PPP especificada.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **status_ptr**: Destino del estado de PPP, los valores de estado posibles son los siguientes:
    - **NX_PPP_STATUS_ESTABLISHED**
    - **NX_PPP_STATUS_LCP_IN_PROGRESS**
    - **NX_PPP_STATUS_LCP_FAILED**
    - **NX_PPP_STATUS_PAP_IN_PROGRESS**
    - **NX_PPP_STATUS_PAP_FAILED**
    - **NX_PPP_STATUS_CHAP_IN_PROGRESS**
    - **NX_PPP_STATUS_CHAP_FAILED**
    - **NX_PPP_STATUS_IPCP_IN_PROGRESS**
    - **NX_PPP_STATUS_IPCP_FAILED**

>[!NOTE]
> El estado solo es válido si la API devuelve NX_SUCCESS. Además, si se devuelve cualquiera de los valores de estado *_FAILED, el procesamiento de PPP se detiene efectivamente hasta que la aplicación vuelva a iniciarlo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Estado de PPP solicitado correctamente.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos, temporizadores e ISR

### <a name="example"></a>Ejemplo

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a>nx_ppp_stop

Iniciar el procesamiento de PPP

### <a name="prototype"></a>Prototipo

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene el procesamiento de PPP. El usuario también puede llamar a nx_ppp_start () para iniciar el procesamiento de PPP, si es necesario.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Inicio de PPP iniciado correctamente. 
- **NX_PPP_ALREADY_STOPPED**: (0XB8) PPP ya está detenido.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.
- NX_CALLER_ERROR (0x11): Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a>nx_ppp_packet_receive

Recibir paquete de PPP

### <a name="prototype"></a>Prototipo

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a>Descripción

Este servicio recibe el paquete de PPP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **packet_ptr**: Puntero al paquete de PPP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Estado de PPP solicitado correctamente.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a>nx_ppp_packet_send_set

Establecer la función de envío de paquetes de PPP

### <a name="prototype"></a>Prototipo

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a>Descripción

Este servicio establece la función de envío de paquetes de PPP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ppp_ptr**: Puntero al bloque de control de PPP.
- **nx_ppp_packet_send**: Rutina para enviar el paquete de PPP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Estado de PPP solicitado correctamente.
- NX_PTR_ERROR: (0x07) Puntero de PPP no válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```