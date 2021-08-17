---
title: 'Capítulo 3: Descripción de los servicios de cliente Azure RTOS NetX POP3'
description: Este capítulo contiene una descripción de todos los servicios de cliente Azure RTOS NetX POP3 (que se enumeran a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f68d6ac942c829dbf6eb9be334328b1b58a47ea370a73d37f471ec32cd46a360
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782394"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a>Capítulo 3: Descripción de los servicios de cliente Azure RTOS NetX POP3

Este capítulo contiene una descripción de todos los servicios de cliente Azure RTOS NetX POP3 (que se enumeran a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- nx_pop3_client_create: *Crear de una instancia de cliente POP3*
- nx_pop3_client_delete: *Eliminar una instancia de cliente POP3*
- nx_pop3_client_ mail_item_get: *Eliminar un elemento de correo de cliente del servidor maildrop*
- nx_pop3_client_mail_item_get: *Recuperar un tamaño de mensaje de correo específico*
- nx_pop3_client_mail_items_get: *Obtener el número de elementos de correo en maildrop*
- nx_pop3_client_mail_item_message _get: *Descargar un mensaje de correo específico*
- nx_pop3_client_mail_item_size_get: *Obtener el tamaño de un elemento de correo específico*

## <a name="nx_pop3_client_create"></a>nx_pop3_client_create

Crear una instancia del cliente POP3

### <a name="prototype"></a>Prototipo

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia del cliente POP3 y establece su configuración con los parámetros de entrada.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: Puntero al cliente que se va a crear
- **APOP_authentication**: Habilitar la autenticación de APOP
- **ip_ptr**: Puntero a la instancia de IP
- **packet_pool_ptr**: Puntero al grupo de paquetes del cliente
- **server_ip_address**: Dirección del servidor POP3
- **SERVER_PORT**: Puerto del servidor POP3
- **client_name**: Puntero a nombre de cliente
- **client_password**: Puntero a la contraseña de cliente

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Cliente creado correctamente
- **estado**: Finalización del estado de las llamadas al servicio NetX y ThreadX
- NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada
- NX_POP3_PARAM_ERROR: (0xB1) Entrada de puntero no válida

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a>nx_pop3_client_delete

Eliminar una instancia de cliente POP3

### <a name="prototype"></a>Prototipo

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a>Descripción

Este servicio elimina un cliente POP3 creado previamente. No es que este servicio no elimine el grupo de paquetes del cliente POP3. La aplicación de dispositivo debe eliminar este recurso por separado si ya no se usa para el grupo de paquetes.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: Puntero al cliente que se va a eliminar

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Cliente eliminado correctamente
- NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a>nx_pop3_client_mail_item_delete

Eliminar un elemento de correo especificado del maildrop del cliente

### <a name="prototype"></a>Prototipo

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a>Descripción

Este servicio elimina el elemento de correo especificado de la maildrop del cliente. Está pensado para después de descargar el elemento de correo, aunque algunos servidores POP3 pueden eliminar elementos de correo automáticamente después de que el cliente los solicite.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: Puntero a la instancia de cliente
- **mail_index**: Índice en la maildrop del cliente

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0X00) Eliminar solicitud correcta
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de elemento de correo no válido
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) la carga de paquete de cliente es demasiado pequeña para la solicitud POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) el servidor responde con el estado de error
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada de índice de correo no válida
- NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a>nx_pop3_client_mail_item_get

Recuperar un elemento de correo especificado

### <a name="prototype"></a>Prototipo

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a>Descripción

Este servicio realiza una solicitud RETR para recuperar un elemento de correo desde el maildrop del cliente especificado por el índice mail_item. Después de hacer una solicitud RETR y recibir una respuesta positiva del servidor, el cliente puede comenzar a descargar el mensaje de correo mediante el servicio *nx_pop3_client_mail_item_message_get*. Tenga en cuenta que el servicio también proporciona el tamaño del elemento de correo solicitado extraído de la respuesta del servidor.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: Puntero a la instancia de cliente
- **mail_item**: Índice en el maildrop del cliente
- **item_size**: Puntero al tamaño del mensaje de correo

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Elemento de correo recuperado correctamente
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de elemento de correo no válido
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) la carga de paquete de cliente es demasiado pequeña para la solicitud POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) el servidor responde con el estado de error
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada de índice de correo no válida
- NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a>nx_pop3_client_mail_items_get

Recuperar el número de elementos de correo en maildrop

### <a name="prototype"></a>Prototipo

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a>Descripción

Este servicio realiza una solicitud de STAT para recuperar el número de elementos de correo y el tamaño total de los datos de los mensajes de correo desde el maildrop del cliente.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: Puntero a la instancia de cliente
- **number_mail_item**: Número de correo en el maildrop del cliente
- **maildrop_total_size**: Puntero al tamaño de todo el mensaje de correo

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Elemento de correo recuperado correctamente
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de elemento de correo no válido
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) la carga de paquete de cliente es demasiado pequeña para la solicitud POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) el servidor responde con el estado de error 
- NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a>nx_pop3_client_mail_item_message_get

Recuperar el mensaje de elemento de correo especificado

### <a name="prototype"></a>Prototipo

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a>Descripción

Este servicio recupera el mensaje de elemento de correo, el tamaño del mensaje de correo y si es el último paquete del mensaje de correo. Si `final_packet` es NX_TRUE el paquete al que apunta `recv_packet_ptr` es el paquete final en el mensaje del elemento de correo.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: Puntero a la instancia de cliente
- **recv_packet_ptr**: Paquete recibido de datos de mensaje
- **number_mail_item**: Número de correo en el maildrop del cliente
- **maildrop_total_size**: Puntero al tamaño de todo el mensaje de correo

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Elemento de correo recuperado correctamente
- **NX_POP3_CLIENT_INVALID_STATE**: (0xB7) La carga de paquete de cliente es demasiado pequeña para la solicitud POP3.
- NX_PTR_ERROR (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a>nx_pop3_client_mail_item_size_get

Recupera el tamaño del elemento de correo especificado

### <a name="prototype"></a>Prototipo

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a>Descripción

Este servicio realiza una solicitud de lista para obtener el tamaño del elemento de correo especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **client_ptr**: Puntero a la instancia de cliente
- **mail_item**: Índice en el maildrop del cliente
- **tamaño**: Puntero al tamaño del mensaje de correo

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Elemento de correo recuperado correctamente
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de elemento de correo no válido
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) la carga de paquete de cliente es demasiado pequeña para la solicitud POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) el servidor responde con el estado de error
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada de índice de correo no válida
- NX_PTR_ERROR: (0x07) Parámetro no válido de puntero de entrada

### <a name="allowed-from"></a>Permitido desde

Código de aplicación

### <a name="example"></a>Ejemplo

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
