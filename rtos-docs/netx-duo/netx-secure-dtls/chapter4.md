---
title: 'Capítulo 4: Descripción de los servicios Azure RTOS NetX Secure DTLS'
description: Este capítulo contiene una descripción de todos los servicios Azure RTOS NetX Secure DTLS en orden alfabético.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e795a5fa35a4590e508c7fe2eec53f5494809657
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814513"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a>Capítulo 4: Descripción de los servicios Azure RTOS NetX Secure DTLS

Este capítulo contiene una descripción de todos los servicios Azure RTOS NetX Secure DTLS (enumerados a continuación) en orden alfabético.

En la sección "Valores devueltos" de las siguientes descripciones de la API, los valores en **NEGRITA** no se ven afectados por el macro **NX_SECURE_DISABLE_ERROR_CHECKING** que se usan para deshabilitar la comprobación de errores de la API, mientras que los valores que no aparecen en negrita están totalmente deshabilitados.

- [nx_secure_dtls_client_session_start](#nx_secure_dtls_client_session_start)
- [nx_secure_dtls_packet_allocate](#nx_secure_dtls_packet_allocate)
- [nx_secure_dtls_psk_add](#nx_secure_dtls_psk_add)
- [nx_secure_dtls_server_create](#nx_secure_dtls_server_create)
- [nx_secure_dtls_server_delete](#nx_secure_dtls_server_delete)
- [nx_secure_dtls_server_local_certificate_add](#nx_secure_dtls_server_local_certificate_add)
- [nx_secure_dtls_server_local_certificate_remove](#nx_secure_dtls_server_local_certificate_remove)
- [nx_secure_dtls_server_notify_set](#nx_secure_dtls_server_notify_set)
- [nx_secure_dtls_server_psk_add](#nx_secure_dtls_server_psk_add)
- [nx_secure_dtls_server_session_send](#nx_secure_dtls_server_session_send)
- [nx_secure_dtls_server_session_start](#nx_secure_dtls_server_session_start)
- [nx_secure_dtls_server_start](#nx_secure_dtls_server_start)
- [nx_secure_dtls_server_stop](#nx_secure_dtls_server_stop)
- [nx_secure_dtls_server_trusted_certificate_add](#nx_secure_dtls_server_trusted_certificate_add)
- [nx_secure_dtls_server_trusted_certificate_remove](#nx_secure_dtls_server_trusted_certificate_remove)
- [nx_secure_dtls_server_x509_client_verify_configure](#nx_secure_dtls_server_x509_client_verify_configure)
- [nx_secure_dtls_server_x509_client_verify_disable](#nx_secure_dtls_server_x509_client_verify_disable)
- [nx_secure_dtls_session_client_info_get](#nx_secure_dtls_session_client_info_get)
- [nx_secure_dtls_session_create](#nx_secure_dtls_session_create)
- [nx_secure_dtls_session_delete](#nx_secure_dtls_session_delete)
- [nx_secure_dtls_session_end](#nx_secure_dtls_session_end)
- [nx_secure_dtls_session_local_certificate_add](#nx_secure_dtls_session_local_certificate_add)
- [nx_secure_dtls_session_local_certificate_remove](#nx_secure_dtls_session_local_certificate_remove)
- [nx_secure_dtls_session_receive](#nx_secure_dtls_session_receive)
- [nx_secure_dtls_session_reset](#nx_secure_dtls_session_reset)
- [nx_secure_dtls_session_send](#nx_secure_dtls_-session_send)
- [nx_secure_dtls_session_trusted_certificate_add](#nx_secure_dtls_session_trusted_certificate_add)
- [nx_secure_dtls_session_trusted_certificate_remove](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a>nx_secure_dtls_client_session_start

Iniciar una sesión de cliente de NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a>Descripción

Este servicio inicia una sesión de cliente DTLS, que se conecta al servidor en la dirección IP y el puerto UDP proporcionados mediante el socket UDP proporcionado para las comunicaciones de red.

El bloque de control de sesión DTLS debe inicializarse antes de llamar a este servicio mediante nx_secure_dtls_session_create. Además, el cliente DTLS necesita que se haya agregado al menos un certificado de entidad de certificación de confianza a la sesión mediante nx_secure_dtls_session_trusted_certificate_add o que las claves precompartidas estén habilitadas y configuradas.

### <a name="parameters"></a>Parámetros

- **dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.
- **udp_socket** Socket UDP inicializado que se usará para establecer comunicaciones de red con el servidor DTLS remoto.
- **ip_address** Puntero a la estructura de la dirección IP que contiene la dirección del servidor DTLS remoto.
- **port** Socket UDP inicializado que se usará para establecer comunicaciones de red con el servidor DTLS remoto.
- **wait_option** Opción de suspensión para el intento de conexión.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Asignación correcta del certificado a la sesión.
- **NX_NOT_CONNECTED** (0x38) No se puede tener acceso al servidor en la dirección y el puerto especificados.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) Un tipo de mensaje TLS/DTLS recibido es incorrecto.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) No se admite el cifrado proporcionado por el host remoto.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Procesamiento del mensaje durante el protocolo de enlace de TLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Un mensaje entrante no pudo realizar una comprobación de MAC hash.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Error al enviar un socket TCP subyacente.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Un mensaje entrante tenía un campo de longitud no válido.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0X10B) Un mensaje ChangeCipherSpec entrante era incorrecto.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) Un certificado TLS entrante no se puede usar para identificar el servidor DTLS remoto.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) No se admite el cifrado de clave pública proporcionado por el host remoto.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E) El host remoto ha indicado que no hay conjuntos de aplicaciones de cifrado admitidos por la pila de NetX Secure DTLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) Un mensaje DTLS recibido tenía una versión DTLS desconocida en el encabezado.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) Un mensaje DTLS recibido tenía una versión de DTLS conocida pero no admitida en su encabezado.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Error en una asignación interna de paquetes TLS.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) El host remoto proporcionó un certificado no válido.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) El host remoto envió una alerta que indica un error y finaliza la sesión de TLS.
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) Una entrada en la tabla de conjunto de aplicaciones de cifrado tenía un puntero de función NULL.
- **NX_PTR_ERROR** (0x07): La sesión, el socket o el puntero de dirección no son válidos.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_session_receive, nx_secure_dtls_session_send,
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_packet_allocate"></a>nx_secure_dtls_packet_allocate

Asignación de un paquete para una sesión de NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a>Descripción

Este servicio asigna un NX_PACKET para la sesión DTLS activa especificada desde el NX_PACKET_POOL especificado. La aplicación debe llamar a este servicio para asignar paquetes de datos que se enviarán a través de una conexión DTLS. La sesión DTLS debe inicializarse antes de llamar a este servicio.

El paquete asignado se ha inicializado correctamente para que se puedan agregar datos de encabezado y pie de página de DTLS una vez que se hayan rellenado los datos del paquete. De lo contrario, el comportamiento es idéntico al de *nx_packet_allocate*.

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia de sesión DTLS.
- **pool_ptr** Puntero a un NX_PACKET_POOL desde el que se va a asignar el paquete.
- **packet_ptr** Puntero de salida al paquete recién asignado.
- **wait_option** Opción de suspensión para la asignación de paquetes.


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Asignación correcta de paquetes.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Error al asignar el paquete subyacente.
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) No se inicializó la sesión DTLS proporcionada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a>Consulte también

- nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_dtls_session_send, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_end, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_psk_add"></a>nx_secure_dtls_psk_add

Incorporación de una clave precompartida a una sesión de NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>Descripción

Este servicio agrega una clave precompartida (PSK), su cadena de identidad y una sugerencia de identidad a un bloque de control de sesión DTLS. La PSK se usa en lugar de un certificado digital cuando se habilitan y se usan conjuntos de aplicaciones de cifrado.

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.
- **pre_shared_key** Valor de PSK real.
- **psk_length** Longitud del valor de PSK.
- **psk_identity** Cadena que se usa para identificar este valor de PSK.
- **identity_length** La longitud de la identidad de PSK.
- **hint** Cadena usada para indicar qué grupo de PSK elegir en un servidor TLS.
- **hint_length** Longitud de la cadena de sugerencia.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) PSK añadida correctamente.
- **NX_PTR_ERROR** (0x07) Puntero de sesión DTLS no válido.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) No se puede agregar otra PSK.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create

## <a name="nx_secure_dtls_server_create"></a>nx_secure_dtls_server_create

Creación de un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a>Descripción

Este servicio crea una instancia de un servidor DTLS para administrar las solicitudes DTLS entrantes en un puerto UDP determinado. Debido al hecho de que UDP no tiene estado, las solicitudes de DTLS de varios clientes pueden entrar en un único puerto mientras que otras sesiones DTLS están activas. Por lo tanto, se necesita el servidor para mantener las sesiones activas y enrutar correctamente los mensajes entrantes al controlador adecuado.

El parámetro ip_ptr apunta a una instancia NX_IP que se va a usar para el socket UDP interno asociado con el servidor DTLS (y se almacena en el bloque de control NX_SECURE_DTLS_SERVER). La instancia de IP y el puerto se usan para definir la interfaz de UDP en la que se crea una instancia del servidor con el servicio de nx_secure_dtls_server_start.

El parámetro de búfer de la sesión se usa para mantener los bloques de control para todas las sesiones DTLS simultáneas posibles para el servidor DTLS. Debe asignarse con un tamaño que sea un múltiplo par del tamaño de la estructura del bloque de control NX_SECURE_DTLS_SESSION.

Para calcular el tamaño de metadatos necesario, se puede usar la API nx_secure_tls_metadata_size_calculate.

DTLS usa el parámetro packet_reassembly_buffer para volver a ensamblar los datagramas UDP en un registro DTLS completo con el fin de descifrar y debe ser lo suficientemente grande como para acomodar el mayor registro DTLS esperado (16 KB es el tamaño máximo de registro de DTLS, pero muchas aplicaciones no envían esa cantidad de datos en un único registro).

La rutina de devolución de llamada connect_notify se invoca siempre que un nuevo cliente DTLS se conecta al servidor. Depende de la aplicación iniciar después la sesión DTLS mediante el servicio *nx_secure_dtls_server_session_start*. Aunque la sesión puede iniciarse en la devolución de llamada, se recomienda usar la devolución de llamada para notificar al subproceso de la aplicación (o al subproceso DTLS dedicado creado por la aplicación) de la conexión, ya que el subproceso IP invoca la devolución de llamada, que se usa para procesar todo el procesamiento de red de nivel inferior (por ejemplo, UDP). Esto puede ser tan sencillo como guardar el parámetro de sesión DTLS (proporcionado como parámetro para la devolución de llamada) e invocar nx_secure_dtls_server_session_start en el otro subproceso. Por lo general, la devolución de llamada de connect_notify debería devolver NX_SUCCESS.

La rutina de devolución de llamada de receive_notify se invoca cada vez que se recibe un registro DTLS que coincide con una sesión DTLS establecida existente (el puerto y la dirección IP del host remoto se usan para identificar una sesión existente). Representa los "datos de aplicación" que se cifran y se envían a través de DTLS. La aplicación debe llamar al servicio *nx_secure_dtls_session_receive* en la sesión DTLS proporcionada para recuperar los datos recibidos. Al igual que con la devolución de llamada de connect_receive, se recomienda pasar la sesión a otro subproceso para controlar el procesamiento de mensajes, ya que la devolución de llamada se invoca desde el subproceso IP. Por lo general, la devolución de llamada de connect_notify debería devolver NX_SUCCESS.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.
- **ip_ptr** Puntero a un bloque de control NX_IP inicializado para usarlo como interfaz de red para el servidor DTLS.
- **port** Puerto UDP local al que está enlazado el socket UDP del servidor DTLS.
- **timeout** Valor de tiempo de espera que se va a usar para las operaciones de red.
- **session_buffer** Espacio en búfer para contener los bloques de control de todas las instancias de NX_SECURE_DTLS_SESSION asignadas a esta instancia del servidor DTLS.
- **session_buffer_size** Tamaño del búfer de la sesión. Esto determina el número de sesiones DTLS asignadas al servidor DTLS.
- **crypto_table** Puntero a una estructura de tabla de cifrado TLS/DTLS usada para todas las operaciones criptográficas.
- **crypto_metadata_buffer** Espacio en búfer para cálculos de operaciones criptográficas e información de estado.
- **crypto_metadata_size** Tamaño del búfer de metadatos.
- **packet_reassembly_buffer** Búfer usado por DTLS para volver a ensamblar los datos de UDP en los registros de DTLS para el descifrado.
- **packet_reassembly_buffer_size** Tamaño del búfer de reensamblado. Por lo general, debe ser mayor que 16 KB, pero puede ser menor en función de la aplicación.
- **connect_notify** Rutina de devolución de llamada que se invoca cada vez que un cliente DTLS remoto trata de conectarse a este servidor DTLS.
- **receive_notify** Devolución de llamada invocada cuando se reciben datos de la aplicación a través de una sesión DTLS existente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Creación correcta del servidor DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_INVALID_PARAMETERS** (0X4D) No hay suficiente espacio de búfer para las sesiones, el reensamblado de paquetes o la criptografía.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_delete"></a>nx_secure_dtls_server_delete

Liberación de recursos usados por un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Descripción

Este servicio libera los recursos asignados a una instancia del servidor DTLS, incluido el socket UDP interno usado por el servidor.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta del servidor.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_STILL_BOUND** (0x42) El socket UDP sigue estando enlazado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_local_certificate_add"></a>nx_secure_dtls_server_local_certificate_add

Adición de un certificado de identidad de servidor local a un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a>Descripción

Este servicio agrega un certificado de identidad de servidor local a una instancia del servidor DTLS. Se necesita al menos un certificado de identidad para que los clientes se conecten a un servidor DTLS a menos que se use un mecanismo de autenticación alternativo (por ejemplo, claves precompartidas).

El parámetro cert_id es un identificador numérico distinto de cero para el certificado. Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presente en el almacén de servidores DTLS. Para obtener más información sobre los certificados de servidor X.509, consulte la guía de usuario de NetX Secure TLS.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.
- **certificate** Puntero a una estructura de certificados X.509 inicializada previamente.
- **cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Adición correcta del certificado al servidor DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_INVALID_PARAMETERS** (0x4D) Se ha enviado un id. de certificado con valor 0.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

\* Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_server_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_local_certificate_remove"></a>nx_secure_dtls_server_local_certificate_remove

Eliminación de un certificado de identidad de servidor local de un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a>Descripción

Este servicio quita un certificado de identidad de servidor local de una instancia del servidor DTLS. Se necesita al menos un certificado de identidad para que los clientes se conecten a un servidor DTLS a menos que se use un mecanismo de autenticación alternativo (por ejemplo, claves precompartidas).

El certificado que se va a quitar se puede identificar por su nombre común X.509 o por el cert_id numérico que se asignó en la llamada a *nx_secure_dtls_server_local_certificate_add*. El cert_id solo se usa para identificar el certificado y lo mantiene la aplicación. Si se usa el nombre común en lugar del identificador de certificado numérico, el parámetro cert_id debe establecerse en 0.

> [!NOTE]
> Si se quita un certificado mientras se está procesando un protocolo de enlace DTLS, se producirá un comportamiento inesperado. Antes de quitar los certificados, se debe llamar al parámetro *nx_secure_dtls_server_stop* de servicio.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.
- **common_name** CommonName X.509 del certificado que se va a quitar. Si se usa, envíe cert_id con valor cero.
- **common_name_length** Longitud de la cadena common_name en bytes.
- **cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS. Si se usa, envíe NX_NULL para el parámetro common_name.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta del certificado del servidor DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) No se encontró ningún certificado que coincida con el cert_id o common_name en el servidor DTLS especificado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_notify_set"></a>nx_secure_dtls_server_notify_set

Asignación de rutinas de devolución de llamada de notificación opcionales a un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a>Descripción

Este servicio se puede usar para agregar rutinas de devolución de llamada de notificación opcionales a un servidor DTLS. Cualquier parámetro de devolución de llamada se puede enviar como NX_NULL si solo se quiere una devolución de llamada.

La devolución de llamada de disconnect_notify se invoca cuando un cliente remoto finaliza una sesión DTLS. El parámetro dtls_session es la instancia de sesión que se cerró. Por lo general, la devolución de llamada debe devolver NX_SUCCESS.

La devolución de llamada de error_notify se invoca cada vez que se produce un error o un tiempo de espera de DTLS. El parámetro dtls_session es la instancia de sesión para la que se produjo el error y error_code es el código de estado numérico para el error que provocó el problema (consulte el Apéndice A).

Códigos de retorno/error de Net Secure de la lista de códigos de error que se puede devolver. Por lo general, la devolución de llamada debe devolver NX_SUCCESS.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.
- **disconnect_notify** Rutina de devolución de llamada que se invoca siempre que un host de cliente remoto cierra una sesión DTLS.
- **error_notify** Rutina de devolución de llamada que se invoca cuando DTLS encuentra un error o un tiempo de espera.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Asignación correcta de rutinas de devolución de llamada.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop

## <a name="nx_secure_dtls_server_psk_add"></a>nx_secure_dtls_server_psk_add

Incorporación de una clave precompartida a un servidor de NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a>Descripción

Este servicio agrega una clave precompartida (PSK), su cadena de identidad y una sugerencia de identidad a un bloque de control del servidor DTLS. La PSK se usa en lugar de un certificado digital cuando se habilitan y se usan conjuntos de aplicaciones de cifrado.

La PSK que se agrega se replica en todas las sesiones DTLS asignadas al servidor DTLS (a través del búfer de sesión proporcionado en la llamada a nx_secure_dtls_server_create).

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.
- **pre_shared_key** Valor de PSK real.
- **psk_length** Longitud del valor de PSK.
- **psk_identity** Cadena que se usa para identificar este valor de PSK.
- **identity_length** La longitud de la identidad de PSK.
- **hint** Cadena usada para indicar qué grupo de PSK elegir en un servidor TLS.
- **hint_length** Longitud de la cadena de sugerencia.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) PSK añadida correctamente.
- **NX_PTR_ERROR** (0x07) Puntero del servidor DTLS no válido.
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) No se puede agregar otra PSK.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_psk_add, nx_secure_dtls_server_create

## <a name="nx_secure_dtls_server_session_send"></a>nx_secure_dtls_server_session_send

Envío de datos a través de una sesión DTLS establecida con un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a>Descripción

Este servicio envía un paquete de datos a través de una sesión de servidor DTLS establecida a un host del cliente DTLS remoto. La sesión usada se obtiene en la rutina de devolución de llamada receive_notify proporcionada a nx_secure_dtls_session_create.

Los datos proporcionados en el paquete, que se deben asignar mediante *nx_secure_dtls_packet_allocate*, se cifran mediante los parámetros criptográficos y las rutinas de la sesión DTLS y, a continuación, se envían al host remoto a través del puerto UDP interno del servidor DTLS en la dirección IP y el puerto del cliente conectado (almacenados en la sesión DTLS).

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia de sesión DTLS obtenida a partir de la rutina de devolución de llamada receive_notify proporcionada por la aplicación.
- **packet_ptr** Puntero a una instancia NX_PACKET asignada previamente y rellenada con datos de la aplicación.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Creación correcta del servidor DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Se produjo un error en la operación de envío de UDP subyacente.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,
- nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_session_start"></a>nx_secure_dtls_server_session_start

Inicio de una sesión DTLS desde un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a>Descripción

Este servicio inicia una sesión del servidor DTLS mediante el protocolo de enlace DTLS del lado del servidor cuando un cliente DTLS remoto se ha conectado al servidor y ha pedido una conexión DTLS.

La sesión DTLS se obtiene en la rutina de devolución de llamada connect_notify proporcionada a nx_secure_dtls_server_create.

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia de sesión DTLS obtenida de una devolución de llamada connect_notify del servidor DTLS.
- **wait_option** Valor de espera de ThreadX que se va a usar para las operaciones de red.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Creación correcta del servidor DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) No se pudo asignar un paquete de protocolo de enlace de DTLS (grupo de paquetes vacío).
- **NX_SECURE_TLS_INVALID_PACKET** (0X104) Se han recibido datos que no eran un registro DTLS válido.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Un registro DTLS no se pudo codificar correctamente (error de cifrado).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Error al comprobar el relleno de cifrado.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) Se ha recibido una alerta del host remoto durante el protocolo de enlace DTLS.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) Se ha recibido un mensaje desconocido durante el protocolo de enlace DTLS.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) Se ha recibido un registro DTLS con una longitud no válida.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E) Se ha recibido un ClientHello sin conjuntos de aplicaciones de cifrado DTLS compatibles.
- **NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0X118) Se ha recibido un ClientHello con un método de compresión desconocido.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Error genérico (no especificado) de protocolo de enlace, normalmente debido a problemas con el procesamiento de la extensión.
- **NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0X130) Una función que todavía no se admite se invocó durante el protocolo de enlace DTLS.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Se ha encontrado un conjunto de aplicaciones de cifrado desconocido (error de criptografía interno indicado).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) Se ha recibido un registro DTLS con una versión DTLS no coincidente.
- **NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0X115) No se pudo validar el hash de protocolo de enlace de DTLS, la sesión no es válida.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Error de envío UDP interno.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_start"></a>nx_secure_dtls_server_start

Inicio de una instancia del servidor NetX Secure DTLS escuchando en el puerto UDP configurado

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a>Descripción

Este servicio inicia un servidor DTLS. Una vez que se devuelve la llamada, el servidor está activo y comenzará el procesamiento de las solicitudes entrantes de los clientes de DTLS. La instancia del servidor se debe haber configurado con el servicio *nx_secure_dtls_server_create*.

> [!NOTE]
> Este servicio enlaza el puerto UDP del servidor DTLS interno al puerto local configurado, por lo que la mayoría de los problemas encontrados tendrán que hacerse con las comunicaciones UDP y la configuración de red.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Inicio correcto del servidor.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_NOT_ENABLED** (0x14) UDP no habilitado.
- **NX_NO_FREE_PORTS** (0X45) No hay puertos UDP disponibles.
- **NX_INVALID_PORT** (0x46) Puerto UDP no válido.
- **NX_ALREADY_BOUND** (0x22) El puerto UDP ya está enlazado.
- **NX_PORT_UNAVAILABLE** (0x23) El puerto UDP no está disponible para su uso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_stop, nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_stop"></a>nx_secure_dtls_server_stop

Detención de una instancia activa del servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Descripción

Este servicio detiene la escucha de un servidor DTLS en el puerto UDP de configuración y restablece todas las sesiones DTLS asociadas, lo que detiene cualquier comunicación DTLS en curso.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia activa del servidor DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Detección correcta del servidor.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,
- nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a>nx_secure_dtls_server_trusted_certificate_add

Adición de un certificado de CA de confianza a un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Descripción

Este servicio agrega una CA de confianza o un certificado de CA intermedio a una instancia del servidor DTLS y se asigna a todas las sesiones internas del servidor DTLS. Esto solo es necesario si se habilita la autenticación de certificados X.509 de cliente mediante *nx_secure_dtls_server_x509_client_verify_configure*. El certificado agregado se usará para comprobar los certificados X.509 de cliente entrantes.

El parámetro cert_id es un identificador numérico distinto de cero para el certificado. Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presente en el almacén de servidores DTLS. Para obtener más información sobre los certificados de servidor X.509, consulte la guía de usuario de NetX Secure TLS.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.
- **certificate** Puntero a una estructura de certificados X.509 inicializada previamente.
- **cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Adición correcta del certificado al servidor DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_INVALID_PARAMETERS** (0x4D) Se ha enviado un id. de certificado con valor 0.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

\* Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_server_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_local_certificate_add,
- nx_secure_dtls_server_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a>nx_secure_dtls_server_trusted_certificate_remove

Eliminación de un certificado de CA de confianza de un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a>Descripción

Este servicio quita un certificado de CA de confianza de una instancia del servidor DTLS. Los certificados de CA de confianza solo son necesarios para un servidor DTLS para el que se haya habilitado la comprobación de certificados X.509 de cliente mediante una llamada a *nx_secure_dtls_server_x509_client_verify_configure*.

El certificado que se va a quitar se puede identificar por su nombre común X.509 o por el cert_id numérico que se asignó en la llamada a *nx_secure_dtls_server_trusted_certificate_add*. El cert_id solo se usa para identificar el certificado y lo mantiene la aplicación. Si se usa el nombre común en lugar del identificador de certificado numérico, el parámetro cert_id debe establecerse en 0.

> [!NOTE]
> Si se quita un certificado mientras se está procesando un protocolo de enlace DTLS, se puede producir un comportamiento inesperado. Antes de quitar los certificados, se debe llamar al parámetro *nx_secure_dtls_server_stop* de servicio.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.
- **common_name** CommonName X.509 del certificado que se va a quitar. Si se usa, envíe cert_id con valor cero.
- **common_name_length** Longitud de la cadena common_name en bytes.
- **cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS. Si se usa, envíe NX_NULL para el parámetro common_name.


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta del certificado del servidor DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) No se encontró ningún certificado que coincida con el cert_id o common_name en el servidor DTLS especificado.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a>nx_secure_dtls_server_x509_client_verify_configure

Configuración de un servidor NetX Secure DTLS para pedir y comprobar los certificados de cliente

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a>Descripción

Este servicio configura un servidor DTLS para pedir y comprobar los certificados de cliente DTLS. Esta función opcional se usa cuando se quiere usar certificados X.509 para la autenticación de clientes en lugar de otros mecanismos (por ejemplo, una clave precompartida).

> [!IMPORTANT]
> *Cuando se configura un servidor DTLS para comprobar los certificados de cliente que usan este servicio, debe agregarse al menos un certificado de CA de confianza al servidor mediante nx_secure_dtls_server_trusted_certificate_add o el servidor rechazará todas las conexiones de cliente entrantes porque no podrá comprobar los certificados de cliente en el almacén de confianza.*

Tras llamar a este servicio, la instancia del servidor DTLS pide (una vez iniciado) certificados de cliente como parte del protocolo de enlace DTLS. Suponiendo que el cliente está correctamente configurado con un certificado de identidad (y la cadena de certificados asociada cuando corresponda), el servidor DTLS necesita que se asigne memoria para procesar los datos del certificado de cliente. Esta memoria se envía como el parámetro *certs_buffer*.

Se debe ajustar el tamaño de certs_buffer para dar cabida a la cadena de certificados más grande esperada de un cliente DTLS, multiplicada por el *número de sesiones del servidor DTLS* El búfer se divide entre las sesiones disponibles mediante el parámetro *certs_per_session* que representa el número máximo esperado de certificados en una cadena de certificados de cliente. El búfer también debe proporcionar espacio para la estructura de datos NX_SECURE_X509_CERT que se usa para analizar los datos del certificado.

El cálculo del tamaño de búfer adecuado se puede realizar con la fórmula siguiente:

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- El número de sesiones DTLS viene determinado por el tamaño del búfer de sesión enviado en nx_secure_dtls_server_create.
- certs_per_session debe establecerse en el número máximo esperado de certificados en cualquier cadena de certificados de cliente.
- El tamaño máximo esperado del certificado depende de la aplicación, los tamaños de clave y otros factores, pero normalmente 2 KB es suficiente.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.
- **certs_per_session** Número de certificados que se van a asignar a cada sesión del servidor DTLS.
- **certs_buffer** Espacio en búfer para los datos de los certificados entrantes.
- **buffer_size** Tamaño del búfer de certificados.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Configuración correcta de la comprobación del cliente X.509.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_INVALID_PARAMETERS** (0x4D) Almacén de certificados no válido (¿instancia de DTLSserver no inicializada?).

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_x509_client_verify_disable,
- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a>nx_secure_dtls_server_x509_client_verify_disable

Deshabilita la comprobación de certificados X.509 del cliente para un servidor NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>Descripción

Este servicio deshabilita la comprobación de certificados X.509 de cliente en un servidor DTLS. El servicio no tiene ningún efecto si la comprobación de certificados de cliente X.509 no está habilitada.

> [!NOTE]
> Deshabilitar la autenticación de cliente en una instancia del servidor DTLS activa puede producir un comportamiento impredecible. Se debe llamar al servicio nx_secure_dtls_server_stop antes de cambiar el estado del servidor.

### <a name="parameters"></a>Parámetros

- **server_ptr** Puntero a una instancia del servidor DTLS creada anteriormente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Deshabilitación correcta de la autenticación del cliente X.509.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_x509_client_verify_configure,
- nx_secure_dtls_server_start, nx_secure_dtls_server_create,
- nx_secure_dtls_server_session_start,
- nx_secure_dtls_server_session_stop,
- nx_secure_dtls_server_trusted_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_client_info_get"></a>nx_secure_dtls_session_client_info_get

Obtención de información del cliente remoto desde una sesión del servidor DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a>Descripción

Este servicio devuelve la información de red sobre un cliente DTLS que está conectado a una sesión determinada del servidor DTLS. La información devuelta consta de la dirección IP y el puerto UDP del cliente remoto, así como del puerto del servidor local al que está conectado el cliente.

En general, la instancia de sesión DTLS será la obtenida en la invocación de una de las rutinas de devolución de llamada de notificación DTLS (por ejemplo, las devoluciones de llamada connect_notify o receive_notify enviadas en nx_secure_dtls_server_create).

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia activa de sesión del servidor DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta del servidor.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_INVALID_SOCKET** (0X13) El socket UDP asociado no es válido (¿sesión no inicializada?).
- **NX_NOT_CONNECTED** (0x38) El socket UDP no está conectado: la conexión de cliente ha caído o no se ha establecido todavía.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_server_start, nx_secure_dtls_server_stop,
- nx_secure_dtls_server_create, nx_secure_dtls_server_delete,
- nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_session_create"></a>nx_secure_dtls_session_create

Creación y configuración de una sesión de NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a>Descripción

Este servicio crea y configura una sesión DTLS. Por lo general, esto se usará para crear sesiones de cliente DTLS, ya que las sesiones del servidor DTLS se administran con el mecanismo de servidor DTLS (consulte *nx_secure_dtls_server_create*), pero puede haber instancias en las que una aplicación necesita crear una única instancia de sesión de servidor DTLS independiente, en cuyo caso se puede usar este servicio<sup>7</sup>.

Los parámetros configuran la información y la asignación de memoria necesaria para crear una instancia de una sesión DTLS. El parámetro crypto_table es una tabla de TLS que contiene todas las rutinas criptográficas necesarias para el cifrado y la autenticación de TLS/DTLS. El parámetro metadata_buffer se usa para cálculos de cifrado (consulte nx_secure_tls_metadata_size_calculate en la guía de usuario de NetX Secure TLS) y el parámetro packet_reassembly_buffer se usa para volver a ensamblar los datagramas UDP en un registro DTLS completo para el descifrado.

Los parámetros certs_number y remote_certificate_buffer son necesarios para los clientes DTLS que necesitan espacio para almacenar y procesar la cadena de certificados entrante del servidor DTLS. El búfer debe ser capaz de dar cabida al tamaño máximo previsto de la cadena de certificados para cualquier servidor al que se conectará. El búfer se divide por el número de certificados esperados (parámetro certs_number) y también debe ser lo suficientemente grande como para contener una estructura NX_SECURE_X509_CERT por certificado. El tamaño del búfer se puede determinar mediante la siguiente fórmula:

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- certs_number es el número máximo esperado de certificados en la cadena de certificados del servidor
- El tamaño máximo de los certificados depende del tamaño de las claves que se usan y de la información del certificado, pero 2 KB suele ser suficiente.

**7** La creación de sesiones del servidor DTLS con esta rutina no se recomienda y tiene algunas limitaciones. El principal problema es que la sesión no controlará conexiones de cliente adicionales correctamente; como el UDP no tiene conexión, un segundo cliente puede enviar datos legalmente al puerto UDP del servidor cuando una sesión DTLS anterior todavía está activa, lo que haría que la sesión del servidor finalizara con un error.

### <a name="parameters"></a>Parámetros

- **dtls_session** Puntero a una estructura de sesión DTLS sin inicializar.
- **crypto_table** Puntero a una estructura de tabla de cifrado TLS/DTLS usada para todas las operaciones criptográficas.
- **crypto_metadata_buffer** Espacio en búfer para cálculos de operaciones criptográficas e información de estado.
- **crypto_metadata_size** Tamaño del búfer de metadatos.
- **packet_reassembly_buffer** Búfer usado por DTLS para volver a ensamblar los datos de UDP en los registros de DTLS para el descifrado.
- **packet_reassembly_buffer_size** Tamaño del búfer de reensamblado. Por lo general, debe ser mayor que 16 KB, pero puede ser menor en función de la aplicación.
- **certs_number** Número máximo esperado de certificados en la cadena de certificados del servidor remoto.
- **remote_certificate_buffer** Espacio en búfer para los datos de los certificados entrantes.
- **remote_certificate_buffer_size** Tamaño del búfer de certificados.


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Creación correcta de la sesión.
- **NX_PTR_ERROR** (0x07) Puntero no válido de búfer o sesión.
- **NX_INVALID_PARAMETERS** (0X4D) No hay suficiente espacio de búfer para el reensamblado de paquetes, los certificados o la criptografía.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send

## <a name="nx_secure_dtls_session_delete"></a>nx_secure_dtls_session_delete

Liberación de recursos usados por una sesión NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a>Descripción

Este servicio elimina una sesión DTLS, lo que libera todos los recursos que se asignaron cuando se creó.

### <a name="parameters"></a>Parámetros

- **dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta de la sesión.
- **NX_PTR_ERROR** (0x07) Puntero no válido de búfer o sesión.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_end"></a>nx_secure_dtls_session_end

Apagado de una sesión NetX Secure DTLS activa

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a>Descripción

Este servicio finaliza una sesión DTLS activa mediante el envío de una alerta CloseNotify de TLS/DTLS al host remoto. La dirección IP y el puerto usados son los que se usan en la llamada anterior a nx_secure_dtls_session_send.

### <a name="parameters"></a>Parámetros

- **dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.
- **wait_option** Valor de espera de ThreadX que se va a usar para las operaciones de red.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta de la sesión.
- **NX_PTR_ERROR** (0x07) Puntero no válido de búfer o sesión.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) No se pudo asignar paquetes para la alerta CloseNotify.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Probable error interno: no se reconoce la rutina criptográfica.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Error de envío UDP subyacente.
- **NX_IP_ADDRESS_ERROR** (0x21) Error con la dirección IP del host remoto.
- **NX_NOT_BOUND** (0x24) Socket UDP subyacente no enlazado al puerto.
- **NX_INVALID_PORT** (0x46) Puerto UDP no válido.
- **NX_PORT_UNAVAILABLE** (0x23) El puerto UDP no está disponible para su uso.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_local_certificate_add"></a>nx_secure_dtls_session_local_certificate_add

Adición de un certificado de identidad local a una sesión de NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a>Descripción

Este servicio agrega un certificado de identidad local a una instancia de sesión DTLS. En general, este servicio se usará cuando una sesión de cliente DTLS necesite proporcionar un certificado de identidad a un host de servidor remoto. Se trata de una configuración opcional para DTLS, por lo que no suele ser necesario un certificado para los clientes de DTLS. Un certificado de identidad necesita una clave privada asociada.

El parámetro cert_id es un identificador numérico distinto de cero para el certificado. Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presentes en el almacén de certificados de DTLS. Para obtener más información sobre los certificados X.509, consulte la guía de usuario de NetX Secure TLS.

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.
- **certificate** Puntero a una estructura de certificados X.509 inicializada previamente.
- **cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Adición correcta del certificado a la sesión DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_INVALID_PARAMETERS** (0x4D) Se ha enviado un id. de certificado con valor 0.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

*Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_session_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_local_certificate_remove"></a>nx_secure_dtls_session_local_certificate_remove

Eliminación de un certificado de identidad local de una sesión NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Descripción

Este servicio quita un certificado de identidad local de una instancia de sesión DTLS con un número de identificación de certificado (asignado cuando el certificado se agregó con nx_secure_dtls_session_local_certificate_add) o el campo CommonName X.509.

Si el parámetro common_name se usa para coincidir con el certificado, el parámetro cert_id debe establecerse en 0. Si se usa cert_id, common_name debe enviarse un valor NX_NULL.

El parámetro cert_id es un identificador numérico distinto de cero para el certificado. Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presentes en el almacén de certificados de DTLS. Para obtener más información sobre los certificados X.509, consulte la guía de usuario de NetX Secure TLS.

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.
- **common_name** Puntero a la cadena CommonName que debe coincidir.
- **common_name_length** Longitud de la cadena common_name.
- **cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta del certificado de la sesión DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) No se encontró ningún certificado que coincida con el cert_id o common_name en la sesión DTLS especificada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

*Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_session_create*.

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_local_certificate_add,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_receive"></a>nx_secure_dtls_session_receive

Recepción de datos de la aplicación a través de una sesión NetX Secure DTLS establecida

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a>Descripción

Este servicio devuelve datos de aplicación recibidos por una sesión DTLS activa. La sesión DTLS puede ser una sesión de servidor DTLS (administrada por una instancia del servidor DTLS) o una sesión de cliente DTLS. El paquete devuelto se puede procesar con cualquiera de los servicios de NX_PACKET API (consulte la documentación de NetX para obtener más información).

### <a name="parameters"></a>Parámetros

- **dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.
- **packet_ptr_ptr** Puntero a un puntero NX_PACKET para el paquete devuelto.
- **wait_option** Valor de espera de ThreadX que se va a usar para las operaciones de red.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Recepción correcta del paquete de datos de la aplicación.
- **NX_PTR_ERROR** (0x07) Puntero no válido de paquete o sesión.
- **NX_NOT_ENABLED** (0x14) El UDP no está habilitado.
- **NX_NOT_BOUND** (0x24) Socket UDP no enlazado al puerto.
- **NX_SECURE_TLS_INVALID_PACKET** (0X104) Se han recibido datos que no eran un registro DTLS válido.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Un registro DTLS no se pudo codificar correctamente (error de cifrado).
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Error al comprobar el relleno de cifrado.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0X114) Se ha recibido una alerta del host remoto.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102) Se ha recibido un mensaje desconocido.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A) Se ha recibido un registro DTLS con una longitud no válida.
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Se ha encontrado un conjunto de aplicaciones de cifrado desconocido (indica un error interno de criptografía).
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E) Se ha recibido un registro DTLS con una versión DTLS no coincidente.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_reset"></a>nx_secure_dtls_session_reset

Eliminación de datos en una instancia de sesión NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a>Descripción

Este servicio restablece una sesión DTLS y borra todos los datos criptográficos efímeros, lo que permite que la estructura se vuelva a usar para una nueva sesión. Los datos persistentes (por ejemplo, los almacenes de certificados) se mantienen para que no sea necesario llamar a nx_secure_dtls_session_create de forma repetida.

### <a name="parameters"></a>Parámetros

- **dtls_session** Puntero a una estructura de sesión DTLS que se inicializó previamente.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Sesión restablecida correctamente.
- **NX_PTR_ERROR** (0x07) Puntero no válido de búfer o sesión.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_-session_send"></a>nx_secure_dtls_ session_send

Envío de datos a través de una sesión DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a>Descripción

Este servicio envía un paquete de datos a través de una sesión DTLS establecida a un host de DTLS remoto en la dirección IP y el puerto especificados. La sesión usada es una sesión de cliente DTLS activa. Tenga en cuenta que la dirección IP y el puerto se proporcionan debido a la naturaleza sin estado del UDP, pero por lo general deben coincidir con la dirección y el puerto usados para iniciar la sesión en nx_secure_dtls_session_start.

Los datos proporcionados en el paquete, que se deben asignar mediante *nx_secure_dtls_packet_allocate*, se cifran mediante los parámetros criptográficos y las rutinas de la sesión DTLS y, a continuación, se envían al host remoto a través del socket UDP de la sesión DTLS.

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia de sesión de cliente DTLS activa.
- **packet_ptr** Puntero a una instancia NX_PACKET asignada previamente y rellenada con datos de la aplicación.
- **ip_address** Puntero a una estructura NXD_ADDRESS que contiene la dirección IP del host remoto.
- **port** Puerto UDP en el host remoto.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Envío correcto del paquete.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Se produjo un error en la operación de envío de UDP subyacente.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a>nx_secure_dtls_session_trusted_certificate_add

Adición de un certificado de CA de confianza a una sesión NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>Descripción

Este servicio agrega una CA de confianza o un certificado X.509 de CA intermedio a una instancia de sesión DTLS. Un cliente DTLS necesita al menos un certificado de confianza para validar los certificados de servidor remoto, a menos que se use un mecanismo de autenticación alternativo (por ejemplo, claves precompartidas). Un certificado de confianza no suele tener una clave privada.

El parámetro cert_id es un identificador numérico distinto de cero para el certificado. Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presentes en el almacén de certificados de DTLS. Para obtener más información sobre los certificados X.509, consulte la guía de usuario de NetX Secure TLS.

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.
- **certificate** Puntero a una estructura de certificados X.509 inicializada previamente.
- **cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.

### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Adición correcta del certificado a la sesión DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_INVALID_PARAMETERS** (0x4D) Se ha enviado un id. de certificado con valor 0.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

*Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_session_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_remove,
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a>nx_secure_dtls_session_trusted_certificate_remove

Eliminación de un certificado de CA de confianza de una sesión NetX Secure DTLS

### <a name="prototype"></a>Prototipo

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>Descripción

Este servicio quita un certificado de CA de confianza de una instancia de sesión DTLS con un número de id. de certificado (asignado cuando el certificado se agregó con nx_secure_dtls_session_trusted_certificate_add) o el campo CommonName X.509.

Si el parámetro common_name se usa para coincidir con el certificado, el parámetro cert_id debe establecerse en 0. Si se usa cert_id, common_name debe enviarse un valor NX_NULL.

El parámetro cert_id es un identificador numérico distinto de cero para el certificado. Permite que el certificado se quite fácilmente o se encuentre en caso de que haya varios certificados de identidad con el mismo nombre común de X.509 presentes en el almacén de certificados de DTLS. Para obtener más información sobre los certificados X.509, consulte la guía de usuario de NetX Secure TLS.

### <a name="parameters"></a>Parámetros

- **session_ptr** Puntero a una instancia de sesión DTLS creada anteriormente.
- **common_name** Puntero a la cadena CommonName que debe coincidir.
- **common_name_length** Longitud de la cadena common_name.
- **cert_id** Identificador único numérico distinto de cero para este certificado en este servidor DTLS.


### <a name="return-values"></a>Valores devueltos

- **NX_SUCCESS** (0x00) Eliminación correcta del certificado de la sesión DTLS.
- **NX_PTR_ERROR** (0x07) Se ha enviado un puntero no válido.
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) No se encontró ningún certificado que coincida con el cert_id o common_name en la sesión DTLS especificada.

### <a name="allowed-from"></a>Permitido desde

Subprocesos

### <a name="example"></a>Ejemplo

*Para ver un ejemplo más completo, consulte la referencia de *nx_secure_dtls_session_create*.

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>Consulte también

- nx_secure_dtls_session_create, nx_secure_dtls_session_receive,
- nx_secure_dtls_session_send, nx_secure_dtls_session_start,
- nx_secure_dtls_session_trusted_certificate_add,
- nx_secure_x509_certificate_initialize
