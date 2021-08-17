---
title: 'Capítulo 3: Descripción de los servicios de Azure RTOS NetX FTP'
description: Este capítulo contiene una descripción de todos los servicios DNS de Azure RTOS NetX FTP (enumerados a continuación) en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1aec01088236dcae359c0273a0206c10ea09201eb486478ebd678529413badae
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799462"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a>Capítulo 3: Descripción de los servicios de Azure RTOS NetX FTP

Este capítulo contiene una descripción de todos los servicios DNS de Azure RTOS NetX FTP (enumerados a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de API, los valores en **NEGRITA** no se ven afectados por la definición **NX_DISABLE_ERROR_CHECKING** que se usa para deshabilitar la comprobación de errores de API, mientras que los valores que no están en negrita están completamente deshabilitados.

- **nx_ftp_client_connect**: *permite conectarse a un servidor FTP*.
- **nx_ftp_client_create**: *permite crear una instancia de cliente FTP*.
- **nx_ftp_client_delete**: *permite eliminar una instancia de cliente FTP*.
- **nx_ftp_client_directory_create**: *permite crear un directorio en el servidor*.
- **nx_ftp_client_directory_default_set**: *permite establecer un directorio predeterminado en el servidor*.
- **nx_ftp_client_directory_delete**: *permite eliminar un directorio en el servidor*.
- **nx_ftp_client_directory_listing_get**: *permite obtener la lista de directorios desde el servidor*.
- **nx_ftp_client_directory_listing_continue**: *permite continuar la lista de directorios desde el servidor*.
- **nx_ftp_client_disconnect**: *permite desconectarse del servidor FTP*.
- **nx_ftp_client_file_close**: *permite cerrar el archivo de cliente*.
- **nx_ftp_client_file_delete**: *permite eliminar el archivo en el servidor*.
- **nx_ftp_client_file_open**: *permite abrir el archivo de cliente*.
- **nx_ftp_client_file_read**: *permite leer del archivo*.
- **nx_ftp_client_file_rename**: *permite cambiar el nombre en el servidor*.
- **nx_ftp_client_file_write**: *permite escribir en el archivo*.
- **nx_ftp_server_create**: *permite crear el servidor FTP*.
- **nx_ftp_server_delete**: *permite eliminar el servidor FTP*.
- **nx_ftp_server_start**: *permite iniciar el servidor FTP*.
- **nx_ftp_server_stop**: *permite detener el servidor FTP*.

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

Conexión a un servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio conecta la instancia del cliente FTP creada anteriormente al servidor FTP en la dirección IP suministrada.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **server_ip**: Dirección IP del servidor FTP.
- **username**: Nombre de usuario del cliente para la autenticación.
- **password**: Contraseña del cliente para la autenticación.
- **wait_option**: define cuánto tiempo va a esperar el servicio para la conexión del cliente FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Conexión FTP correcta.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) No recibió una respuesta 22X (correcto).
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) No recibió una respuesta 23X (correcto).
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) No recibió una respuesta 33X (correcto).
- **NX_FTP_NOT_DISCONNECTED** (0xD4) El cliente ya está conectado.
- NX_PTR_ERROR (0x07) Entrada de puntero no válida.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.
- NX_IP_ADDRESS_ERROR (0x21) Dirección IP no válida.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a>nx_ftp_client_create

Creación de una instancia del cliente FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Descripción

Este servicio crea una instancia del cliente FTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **ftp_client_name**: Nombre del cliente FTP.
- **ip_ptr**: Puntero a la instancia de IP creada anteriormente.
- **window_size**: Tamaño de ventana anunciado para sockets TCP de este cliente FTP.
- **pool_ptr**: Puntero al grupo de paquetes predeterminado para este cliente FTP. Tenga en cuenta que la carga mínima de paquete debe ser lo suficientemente grande como para contener la ruta de acceso completa y el nombre de archivo o directorio.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Cliente FTP creado correctamente.
- NX_PTR_ERROR (0x16) Puntero FTP, de puntero IP o de grupo de paquetes no válido. puntero de contraseña.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

Eliminación de una instancia del cliente FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia del cliente FTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS**: (0x00) Cliente FTP eliminado correctamente.
- **NX_FTP_NOT_DISCONNECTED**: (0xD4) Error de eliminación del cliente FTP.
- NX_PTR_ERROR (0x16) El puntero FTP no es válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

Creación de un directorio en el servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio crea el directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **directory_name**: Nombre del directorio que se va a crear.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para la creación del directorio FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Directorio FTP creado correctamente.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto). 
- NX_PTR_ERROR (0x07) Puntero FTP no válido. 
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

Establecimiento el directorio predeterminado en el servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio establece el directorio predeterminado en el servidor FTP que está conectado al cliente FTP especificado. Este directorio predeterminado solo se aplica a la conexión de este cliente.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **directory_path**: Nombre de la ruta de acceso al directorio que se va a establecer.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para el establecimiento del directorio predeterminado FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Establecimiento predeterminado FTP correcto.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto). 
- NX_PTR_ERROR (0x07) Puntero FTP no válido. 
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

Eliminación de un directorio en el servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio elimina el directorio especificado en el servidor FTP que está conectado al cliente FTP especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **directory_name**: Nombre del directorio que se va a eliminar.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para la eliminación del directorio FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Directorio FTP eliminado correctamente.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto). 
- NX_PTR_ERROR (0x07) Puntero FTP no válido. 
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

Obtención de la lista del directorio del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio obtiene el contenido del directorio especificado en el servidor FTP que está conectado al cliente FTP especificado. El puntero de paquete proporcionado contendrá una o más entradas de directorio. Cada entrada se separa mediante una combinación &lt;cr/lf\. Se debe llamar a ***nx_ftp_client_directory_listing_continue*** para completar la operación de obtención del directorio.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **directory_name**: Nombre del directorio del que se desea obtener el contenido.
- **packet_ptr**: Puntero al puntero de paquete de destino. Si la operación se realiza correctamente, la carga de paquete contendrá una o más entradas de directorio.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para el listado del directorio FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Directorio FTP enumerado correctamente.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_NOT_ENABLED** (0x14) El servicio (IPv6) no está habilitado.
- **NX_FTP_EXPECTED_1XX_CODE** (0xD9) No obtuvo una respuesta 1XX (correcto).
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).
- NX_PTR_ERROR (0x07) Puntero FTP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a>nx_ftp_client_directory_listing_continue

Continuación de la lista del directorio del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio continúa obteniendo el contenido del directorio especificado en el servidor FTP que está conectado al cliente FTP especificado. Debería haber estado inmediatamente precedido por una llamada a ***nx_ftp_client_directory_listing_get***. Si la operación se realiza correctamente, el puntero de paquete proporcionado contendrá una o más entradas de directorio. Se debe llamar a esta rutina hasta que se reciba un estado NX_FTP_END_OF_LISTING.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **packet_ptr**: Puntero al puntero de paquete de destino. Si la operación se realiza correctamente, la carga de paquete contendrá una o más entradas de directorio, separadas por &lt;cr/lf&gt;.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para el listado del directorio FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Directorio FTP enumerado correctamente.
- **NX_FTP_END_OF_LISTING** (0xD8) No hay más entradas en este directorio.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).
- NX_PTR_ERROR (0x07) Puntero FTP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a>nx_ftp_client_disconnect

Desconexión del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio desconecta una conexión de servidor FTP establecida previamente con el cliente FTP especificado.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para la desconexión del cliente FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Desconexión FTP correcta.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).
- NX_PTR_ERROR (0x07) Puntero FTP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

Cierre del archivo de cliente

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio cierra un archivo abierto previamente en el servidor FTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para que se cierre el archivo del cliente FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Archivo FTP cerrado correctamente.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_FTP_NOT_OPEN (0xD5)** Archivo no abierto; no se puede cerrar.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).
- NX_PTR_ERROR (0x07) Puntero FTP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

Eliminación de un archivo del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio elimina el archivo especificado del servidor FTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **file_name**: Nombre del archivo que se va a eliminar.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para que se elimine el archivo del cliente FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Archivo FTP eliminado correctamente.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).
- NX_PTR_ERROR (0x07) Puntero FTP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a>nx_ftp_client_file_open

Apertura de un archivo del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio abre el archivo especificado (para lectura o escritura) del servidor FTP previamente conectado a la instancia de cliente especificada.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **file_name**: Nombre del archivo que se va a abrir.
- **open_type**: **NX_FTP_OPEN_FOR_READ** o **NX_FTP_OPEN_FOR_WRITE**.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para que se abra el archivo del cliente FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Archivo FTP abierto correctamente.
- **NX_OPTION_ERROR** (0x0A) Tipo abierto no válido.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_FTP_NOT_CLOSED** (0xD6) El cliente FTP ya está abierto.
- **NX_NO_FREE_PORTS** (0x45) No hay puertos TCP disponibles para asignar.
- NX_PTR_ERROR (0x07) Puntero FTP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a>nx_ftp_client_file_read

Lectura del archivo

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio lee un paquete de un archivo abierto previamente. Se debe llamar repetidamente hasta que se reciba un estado de NX_FTP_END_OF_FILE.

Tenga en cuenta que el autor de la llamada no asigna un paquete para este servicio.  Solo necesita proporcionar un puntero a un puntero de paquete. Este servicio actualizará ese puntero de paquete para que apunte a un paquete recuperado de la cola de recepción de socket.  Si se devuelve un estado correcto, significa que hay un paquete disponible y es responsabilidad del autor de la llamada liberarlo cuando haya terminado con él.

Si se devuelve un estado distinto de cero (ya sea un estado de error o NX_FTP_END_OF_FILE), el autor de la llamada no libera el paquete. De lo contrario, se genera un error cuando el puntero del paquete es NULL.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **packet_ptr**: Puntero al destino del puntero del paquete de datos recuperado de la cola. Si la operación se realiza correctamente, los datos del paquete contienen todo o parte del archivo.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para que se lea el archivo del cliente FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Archivo FTP leído correctamente.
- **NX_FTP_NOT_OPEN** (0xD5) El cliente FTP de no está abierto.
- **NX_FTP_END_OF_FILE** (0xD7) Fin de la condición del archivo.
- NX_PTR_ERROR (0x07) Puntero FTP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

        /* Check status.  */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }
        else
        {
            /* Release packet when done with it. */
            nx_packet_release(my_packet);
        }

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a>nx_ftp_client_file_rename

Cambio de nombre de un archivo del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio cambia el nombre de un archivo en el servidor FTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **filename**: Nombre actual del archivo.
- **new_filename**: Nuevo nombre del archivo.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para que se cambie el nombre al archivo del cliente FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Nombre del archivo FTP cambiado correctamente.
- **NX_FTP_NOT_CONNECTED** (0xD3) El cliente FTP no está conectado.
- **NX_FTP_EXPECTED_3XX_CODE** (0xDD) No recibió una respuesta 3XX (correcto).
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) No obtuvo una respuesta 2XX (correcto).
- NX_PTR_ERROR (0x07) Puntero FTP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

Escritura en un archivo

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Descripción

Este servicio escribe un paquete de datos en el archivo abierto previamente en el servidor FTP.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **packet_ptr**: Puntero de paquete que contiene los datos que se van a escribir.
- **wait_option**: Define cuánto tiempo va a esperar el servicio para que se escriba el archivo del cliente FTP. Las opciones de espera se definen de la siguiente forma:
  - **timeout value**: (de 0x00000001 a 0xFFFFFFFE)
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): si se selecciona TX_WAIT_FOREVER, el subproceso que realiza la llamada se suspende indefinidamente hasta que el servidor FTP responde a la solicitud. Si se selecciona un valor numérico (1-0xFFFFFFFE), se especifica el número máximo de tics del temporizador que permanece suspendido mientras se espera la respuesta del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Archivo FTP escrito correctamente.
- **NX_FTP_NOT_OPEN** (0xD5) El cliente FTP de no está abierto.
- NX_PTR_ERROR (0x07) Puntero FTP no válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

Habilitación o deshabilitación del modo de transferencia pasiva

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a>Descripción

Este servicio habilita el modo de transferencia pasivo si la entrada passive_mode_enabled está establecida en NX_TRUE en una instancia de cliente FTP creada anteriormente, de modo que las llamadas subsiguientes para leer o escribir archivos (RETR, STOR) o descargar un listado del directorio (NLST) se realizan en modo de transferencia. Para deshabilitar la transferencia del modo pasivo y volver al comportamiento predeterminado del modo de transferencia activa, llame a esta función con la entrada passive_mode_enabled establecida en NX_FALSE.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_client_ptr**: Puntero al bloque de control del cliente FTP.
- **passive_mode_enabled**:
  - Si se establece en NX_TRUE, se habilita el modo pasivo.
  - Si se establece en NX_FALSE, se deshabilita el modo pasivo.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Modo pasivo establecido correctamente.
- NX_PTR_ERROR (0x16) El puntero FTP no es válido.
- NX_INVALID_PARAMETERS (0x4D) Entrada no válida que no es de puntero.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

Creación del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a>Descripción

Este servicio crea una instancia del servidor FTP en la instancia de IP NetX especificada y creada anteriormente. Tenga en cuenta que el servidor FTP debe iniciarse con una llamada a ***nx_ftp_server_start*** para que inicie la operación.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_server_ptr**: Puntero al bloque de control del servidor FTP.
- **ftp_server_name**: Nombre del servidor FTP.
- **ip_ptr**: Puntero a la instancia de IP de NetX asociada. Tenga en cuenta que solo puede haber un servidor FTP para una instancia de IP.
- **media_ptr**: Puntero a la instancia multimedia de FileX.
- **stack_ptr**: Puntero a la memoria para el área de pila del subproceso del servidor FTP interno.
- **stack_size** Tamaño del área de pila especificado por *stack_ptr*.
- **pool_ptr**: Puntero al grupo de paquetes de NetX. Tenga en cuenta que el tamaño de carga de los paquetes del grupo debe ser lo suficientemente grande como para alojar el nombre de archivo o la ruta de acceso más grande.
- **ftp_login**: Puntero de función a la función de inicio de sesión de la aplicación. Esta función proporciona el nombre de usuario y la contraseña del cliente que solicita una conexión. Si resulta válido, la función de inicio de sesión de la aplicación debe devolver NX_SUCCESS.
- **ftp_logout**: Puntero de función a la función de cierre de sesión de la aplicación. Esta función proporciona el nombre de usuario y la contraseña del cliente que solicita una desconexión. Si resulta válido, la función de inicio de sesión de la aplicación debe devolver NX_SUCCESS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Servidor FTP creado correctamente.
- NX_PTR_ERROR (0x16) El puntero FTP no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a>nx_ftp_server_delete

Eliminación del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio elimina una instancia de servidor FTP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_server_ptr**: Puntero al bloque de control del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Servidor FTP eliminado correctamente.
- NX_PTR_ERROR (0x16) El puntero FTP no es válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

Inicio del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio inicia una instancia de servidor FTP creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_server_ptr**: Puntero al bloque de control del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Servidor FTP iniciado correctamente.
- NX_PTR_ERROR (0x16) El puntero FTP no es válido.

### <a name="allowed-from"></a>Permitido desde

Inicialización y subprocesos

### <a name="example"></a>Ejemplo

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

Detención del servidor FTP

### <a name="prototype"></a>Prototipo

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene una instancia de servidor FTP iniciada y creada anteriormente.

### <a name="input-parameters"></a>Parámetros de entrada

- **ftp_server_ptr**: Puntero al bloque de control del servidor FTP.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Servidor FTP detenido correctamente.
- NX_PTR_ERROR (0x16) El puntero FTP no es válido.
- NX_CALLER_ERROR: (0x11) Autor de llamada no válido de este servicio.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
