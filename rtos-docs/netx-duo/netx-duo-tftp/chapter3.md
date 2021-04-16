---
title: 'Capítulo 3: Descripción de los servicios TFTP de Azure RTOS NetX Duo'
description: Este capítulo contiene una descripción de todos los servicios TFTP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814525"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a>Capítulo 3: Descripción de los servicios TFTP de Azure RTOS NetX Duo

Este capítulo contiene una descripción de todos los servicios TFTP de Azure RTOS NetX Duo (enumerados a continuación) en orden alfabético. A menos que se especifique lo contrario, todos los servicios admiten las comunicaciones IPv6 e IPv4.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nxd_tftp_client_file_open**: *abre el archivo de cliente TFTP*.

- **nxd_tftp_client_create**: *crea una instancia de cliente TFTP*.

- **nxd_tftp_client_delete**: *elimina una instancia de cliente TFTP*.

- **nxd_tftp_client_error_info_get**: *obtiene información de error de cliente*.

- **nxd_tftp_client_file_close**: *cierra el archivo de cliente*.

- **nxd_tftp_client_file_open**: *abre el archivo de cliente*.

- **nxd_tftp_client_file_read**: *lee un bloque del archivo de cliente*.

- **nxd_tftp_client_file_write**: *escribe un bloque en el archivo de cliente*.

- **nxd_tftp_client_packet_allocate**: *asigna paquete para escritura de archivo de cliente*.

- **nxd_tftp_client_set_interface**: *establece la interfaz física de las solicitudes TFTP*.

- **nxd_tftp_server_create**: *crea servidor TFTP*.

- **nxd_tftp_server_delete**: *elimina servidor TFTP*.

- **nxd_tftp_server_start**: *inicia servidor TFTP*.

- **nxd_tftp_server_stop**: *detiene servidor TFTP*.

> [!NOTE] 
> Los equivalentes de IPv4 de todos los servicios enumerados anteriormente están disponibles en el cliente y el servidor TFTP de NetX Duo, por ejemplo, *nx_tftp_server_create* y *nx_tftp_client_file_open*. En las páginas siguientes solo se proporcionan las descripciones de API de "Duo", por ejemplo, los servicios que empiezan por *nxd_* . Donde se especifica una entrada NXD_ADDRESS \*, la API equivalente de IPv4 llama a una entrada ULONG. De lo contrario, no hay ninguna diferencia en el uso de la API.

## <a name="nxd_tftp_client_create"></a>nxd_tftp_client_create

Cree una instancia de cliente TFTP

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia de cliente TFTP para la instancia de IP creada anteriormente.

> [!IMPORTANT]
> La aplicación debe asegurarse de que la dirección IP y el grupo de paquetes proporcionados ya se hayan creado. Además, UDP debe estar habilitado en la instancia de IP antes de llamar a este servicio.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_client_ptr** Puntero al bloque de control del cliente TFTP.

- **tftp_client_name** Nombre de esta instancia de cliente TFTP.

- **ip_ptr** Puntero a la instancia de IP creada anteriormente.

- **pool_ptr** Puntero a la instancia de cliente TFTP del grupo de paquetes.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) TFTP creado correctamente.

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Versión de IP no válida o no compatible.

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Dirección IP de servidor no válida recibida.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) ACK de servidor no recibida.

- NX_PTR_ERROR (0x16) Dirección IP, grupo o puntero TFTP no válidos.

- NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a>nxd_tftp_client_delete

Elimine una instancia de cliente TFTP

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de cliente TFTP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_client_ptr** Puntero a una instancia de cliente TFTP creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Cliente TFTP eliminado correctamente.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a>nxd_tftp_client_error_info_get

Obtenga información de error de cliente

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a>Descripción

Este servicio devuelve el último código de error recibido y establece el puntero en la cadena de error interna del cliente. En caso de error, el usuario puede ver el último error enviado por el servidor. Una cadena de error NULL indica que no hay ningún error.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_client_ptr** Puntero a una instancia de cliente TFTP creada anteriormente.

- **error_code** Puntero al área de destino del código de error.

- **error_string** Puntero al destino de la cadena de error.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Información de error de TFTP obtenida correctamente.  

- NX_PTR_ERROR (0x16) Puntero de cliente TFTP no válido.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a>nxd_tftp_client_file_close

Cierre el archivo de cliente

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a>Descripción

Este servicio cierra el archivo abierto previamente por esta instancia de cliente TFTP. Una instancia de cliente TFTP solo puede tener un archivo abierto a la vez.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_client_ptr** Puntero a una instancia de cliente TFTP creada anteriormente.

- **ip_type** Indica el protocolo IP que se va a usar. Las opciones válidas son IPv4 (4) o IPv6 (6).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Archivo TFTP cerrado correctamente.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a>nx_tftp_client_file_open

Abra el archivo de cliente TFTP

### <a name="prototype"></a>Prototipo

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio intenta abrir el archivo especificado en el servidor TFTP en la dirección IP especificada. El archivo se abre para lectura o escritura. 

> [!NOTE] 
> Esta limitación solo afecta a los paquetes IPv4 y está destinada a admitir aplicaciones TFTP de NetX. Se recomienda a los desarrolladores que porten sus aplicaciones para usar el servicio *nxd_tftp_client_file_open* equivalente de "Duo".

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_client_ptr** Puntero al bloque de control de TFTP.

- **file_name** Nombre de archivo ASCII, terminado en NULL y con la información de ruta de acceso adecuada.

- **server_ip_address** Dirección TFTP del servidor.

- **open_type** Tipo de solicitud abierta; puede ser:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** Define cuánto tiempo va a esperar el servicio para que se abra el archivo de cliente TFTP. Las opciones de espera se definen de la siguiente forma:

  **timeout value** (de 0x00000001 a 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF) 
  
  Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor TFTP responde a la solicitud. 
  
  Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor TFTP.

- **ip_type** Indica el protocolo IP que se va a usar. Las opciones válidas son IPv4 (4) o IPv6 (6).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Archivo de cliente abierto correctamente.

- **NX_TFTP_NOT_CLOSED** (0xC3) El cliente ya tiene un archivo abierto.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) No se ha recibido ACK del servidor.

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) IP de servidor no válida recibida.

- **NX_TFTP_CODE_ERROR** (0x05) Código de error recibido.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_IP_ADDRESS_ERROR (0x21) Dirección IP del servidor no válida.

- NX_OPTION_ERROR (0x0A) Tipo abierto no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a>nxd_tftp_client_file_open

Abra el archivo de cliente TFTP

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Descripción

Este servicio intenta abrir el archivo especificado en el servidor TFTP en la dirección IPv6 especificada. El archivo se abre para lectura o escritura.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_client_ptr** Puntero al bloque de control de TFTP.

- **file_name** Nombre de archivo ASCII, terminado en NULL y con la información de ruta de acceso adecuada.

- **server_ip_address** Dirección TFTP del servidor.

- **open_type** Tipo de solicitud abierta; puede ser:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** Define cuánto tiempo va a esperar el servicio para que se abra el archivo de cliente TFTP. Las opciones de espera se definen de la siguiente forma:

  **timeout value** (de 0x00000001 a 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que un servidor TFTP responde a la solicitud.

  Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor TFTP.

- **ip_type** Indica el protocolo IP que se va a usar. Las opciones válidas son IPv4 (4) o IPv6 (6).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Archivo de cliente abierto correctamente.

- **NX_TFTP_NOT_CLOSED** (0xC3) El cliente ya tiene un archivo abierto.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) No se ha recibido ACK del servidor.

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Versión de IP no válida.

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) IP de servidor no válida recibida.

- **NX_TFTP_CODE_ERROR** (0x05) Código de error recibido.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_IP_ADDRESS_ERROR (0x21) Dirección IP del servidor no válida.

- NX_OPTION_ERROR (0x0A) Tipo abierto no válido.

- NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a>nxd_tftp_client_file_read

Lea un bloque del archivo de cliente

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Descripción

Este servicio lee un bloque de 512 bytes del archivo de cliente TFTP previamente abierto. Un bloque que contiene menos de 512 bytes señala el final del archivo.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_client_ptr** Puntero al bloque de control del cliente TFTP.

- **packet_ptr** Destino del paquete que contiene el bloque leído del archivo.

- **wait_option** Define cuánto tiempo espera el servicio para que se complete la lectura. Las opciones de espera se definen de la siguiente forma:

  **timeout value** (de 0x00000001 a 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor TFTP responde a la solicitud.

  Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera a que el servidor TFTP envíe un bloque del archivo.

- **ip_type** Indica el protocolo IP que se va a usar. Las opciones válidas son IPv4 (4) o IPv6 (6).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Bloque de cliente leído correctamente.

- **NX_TFTP_NOT_OPEN** (0xC3) El archivo de cliente especificado no está abierto para lectura.

- **NX_NO_PACKET** (0X01) No se ha recibido ningún paquete del servidor.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) No se ha recibido ACK del servidor.

- **NX_TFTP_END_OF_FILE** (0xC5) Final de archivo detectado (no es un error).

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Versión de IP no válida.

- **NX_TFTP_CODE_ERROR** (0x05) Código de error recibido.

- **NX_TFTP_FAILED** (0xC2) Código TFTP desconocido recibido.

- **NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) El número de bloque recibido no es válido.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a>nxd_tftp_client_file_write

Escriba un bloque en el archivo de cliente

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Descripción

Este servicio escribe un bloque de 512 bytes en el archivo de cliente TFTP previamente abierto. Si especifica un bloque que contiene menos de 512 bytes, se señala el final del archivo.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_client_ptr** Puntero al bloque de control del cliente TFTP.

- **packet_ptr** Paquete que contiene el bloque que se va a escribir en el archivo.

- **wait_option** Define cuánto tiempo espera el servicio para que se complete la escritura. Las opciones de espera se definen de la siguiente forma:

  **timeout value** (de 0x00000001 a 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor TFTP responde a la solicitud.
 
  Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera a que el servidor TFTP envíe una ACK para la solicitud de escritura.

- **ip_type** Indica el protocolo IP que se va a usar. Las opciones válidas son IPv4 (4) o IPv6 (6).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Bloque de cliente escrito correctamente.

- **NX_TFTP_NOT_OPEN** (0xC3) El archivo de cliente especificado no está abierto para escritura.

- **NX_TFTP_TIMEOUT** (0xC1) Tiempo de espera agotado para la ACK del servidor.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.

- **NX_TFTP_NO_ACK_RECEIVED** (0X09) No se ha recibido ACK del servidor.

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) Versión de IP no válida.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Dirección de servidor no válida recibida.

- **NX_TFTP_CODE_ERROR** (0x05) Código de error recibido.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a>nxd_tftp_client_packet_allocate

Asigne paquete para escritura de archivo de cliente

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Descripción

Este servicio asigna un paquete UDP desde el grupo de paquetes especificado y deja espacio para el encabezado TFTP de 4 bytes antes de que el paquete se devuelva al autor de la llamada. Después, el autor de la llamada puede compilar un búfer para escribir en un archivo de cliente.

### <a name="input-parameters"></a>Parámetros de entrada

- **pool_ptr** Puntero al grupo de paquetes.

- **packet_ptr** Destino del puntero al paquete asignado.

- **wait_option** Define cuánto tiempo espera el servicio para que se complete la asignación de paquete. Las opciones de espera se definen de la siguiente forma:

  **timeout value** (de 0x00000001 a 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  Al seleccionar TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que se completa la asignación.

  Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la asignación del paquete.

- **ip_type** Indica el protocolo IP que se va a usar. Las opciones válidas son IPv4 (4) o IPv6 (6).

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Asignación correcta de paquete.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a>nxd_tftp_client_set_interface

Establezca la interfaz física para solicitudes TFTP

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a>Descripción

Este servicio usa el índice de la interfaz de entrada para establecer la interfaz física para que el cliente TFTP envíe y reciba paquetes TFTP. El valor predeterminado es cero para la interfaz principal.

> [!NOTE]
> NetX Duo debe admitir el direccionamiento de host múltiple (v5.6 o posterior) para usar este servicio.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_client_ptr** Puntero a la instancia de cliente TFTP.

- **if_index** Índice de la interfaz física que se va a usar.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Interfaz establecida correctamente. (0X0B) Entrada de interfaz no válida.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

- NX_TFTP_INVALID_INTERFACE (0x0B) Entrada de interfaz no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a>nxd_tftp_server_create

Cree un servidor TFTP

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Descripción

Este servicio crea un servidor TFTP que responde a las solicitudes de cliente TFTP en el puerto 69. El servidor debe iniciarse mediante una llamada subsiguiente a *nxd_tftp_server_start*.

> [!IMPORTANT]
> La aplicación debe asegurarse de que ya se hayan creado la instancia de IP, el grupo de paquetes y la instancia de medios FileX suministrados. Además, UDP debe estar habilitado en la instancia de IP antes de llamar a este servicio.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_server_ptr** Puntero al bloque de control del servidor TFTP.

- **tftp_server_name** Nombre de esta instancia del servidor TFTP.

- **ip_ptr** Puntero a la instancia de IP creada anteriormente.

- **media_ptr** Puntero a la instancia de medios FileX.

- **stack_ptr** Puntero al área de pila del servidor TFTP.

- **stack_size** Número de bytes en la pila del servidor TFTP.

- **pool_ptr** Puntero al grupo de paquetes TFTP. 

> [!NOTE]
> El grupo proporcionado debe tener cargas de paquetes de al menos 580 bytes.<sup>1</sup>

<sup>1</sup> La parte de datos de un paquete tiene exactamente 512 bytes, pero el tamaño de la carga de paquete debe ser de al menos 572 bytes. Los bytes restantes se utilizan para los encabezados UDP, IPv6 o Ethernet y los bytes finales posibles que necesita el controlador para la alineación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Servidor creado correctamente.

- **NX_TFTP_POOL_ERROR** (0xC6) El grupo de paquetes tiene un tamaño de paquete de menos de 560 bytes.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a>nxd_tftp_server_delete

Elimine un servidor TFTP

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina un servidor TFTP creado anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_server_ptr** Puntero al bloque de control del servidor TFTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Servidor eliminado correctamente.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a>nxd_tftp_server_start

Inicie el servidor TFTP

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia el servidor TFTP creado previamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_server_ptr** Puntero al bloque de control del servidor TFTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Servidor iniciado correctamente.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.
 
### <a name="allowed-from"></a>Permitido desde

Inicialización, subprocesos

### <a name="example"></a>Ejemplo

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a>nxd_tftp_server_stop

Detenga el servidor TFTP

### <a name="prototype"></a>Prototipo

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene el servidor TFTP creado previamente.

### <a name="input-parameters"></a>Parámetros de entrada

- **tftp_server_ptr** Puntero al bloque de control del servidor TFTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Servidor detenido correctamente.

- NX_PTR_ERROR (0x16) La entrada de puntero no es válida.

- NX_CALLER_ERROR (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```